---
title: Verwenden von Azure AD für die SharePoint Server-Authentifizierung
ms.author: tracyp
author: MSFTTracyP
ms.reviewer: kirke, josephd, kirks
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Ent_O365_Hybrid
ms.custom: Ent_Solutions
ms.assetid: ''
description: 'Zusammenfassung: erfahren Sie, wie Sie den Azure-zugriffssteuerungsdienst umgehen und SAML 1,1 verwenden, um Ihre SharePoint Server-Benutzer mit Azure Active Directory zu authentifizieren.'
ms.openlocfilehash: c2c9f33aa5e095a8b7fdde08e80cb1a61e88f3eb
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "34070791"
---
# <a name="using-azure-ad-for-sharepoint-server-authentication"></a>Verwenden von Azure AD für die SharePoint Server-Authentifizierung

 **Zusammenfassung:** Erfahren Sie, wie Sie Ihre SharePoint Server 2016-Benutzer mit Azure Active Directory authentifizieren. 

<blockquote>
<p>Dieser Artikel bezieht sich auf Codebeispiele für die Interaktion mit Azure Active Directory Graph. Sie können die Codebeispiele [hier](https://github.com/kaevans/spsaml11/tree/master/scripts)herunterladen.</p>
</blockquote>

SharePoint Server 2016 bietet die Möglichkeit, Benutzer mithilfe der anspruchsbasierten Authentifizierung zu authentifizieren, sodass Sie Ihre Benutzer einfach verwalten können, indem Sie Sie mit verschiedenen Identitätsanbietern authentifizieren, denen Sie Vertrauen, aber von einer anderen Person verwaltet werden. Anstatt die Benutzerauthentifizierung über Active Directory-Domänendienste (AD DS) zu verwalten, können Sie beispielsweise Benutzern die Authentifizierung mithilfe von Azure Active Directory (Azure AD) ermöglichen. Dies ermöglicht die Authentifizierung für Cloud-only-Benutzer mit dem onmicrosoft.com-Suffix in Ihrem Benutzernamen, mit einem lokalen Verzeichnis synchronisierte Benutzer und Gastbenutzer aus anderen Verzeichnissen. Außerdem können Sie Azure AD-Features wie mehrstufige Authentifizierung und erweiterte Berichterstellungsfunktionen nutzen.

> [!IMPORTANT]
> Die in diesem Artikel beschriebene Lösung kann auch mit SharePoint Server 2013 verwendet werden. Bedenken Sie jedoch, dass sich SharePoint Server 2013 dem Ende des Mainstream-Supports nähert. Weitere Informationen finden Sie unter [Microsoft Lifecycle Policy](https://support.microsoft.com/en-us/lifecycle/search?alpha=SharePoint%20Server%202013) und [aktualisierte Produktwartungsrichtlinie für SharePoint 2013](https://technet.microsoft.com/library/684173bb-e90a-4eb7-b268-b8d7458bc802(v=office.16).aspx).

In diesem Artikel wird erläutert, wie Sie Azure AD anstelle ihrer lokalen AD DS verwenden können, um Ihre Benutzer zu authentifizieren. In dieser Konfiguration wird Azure AD zu einem vertrauenswürdigen Identitätsanbieter für SharePoint Server 2016. Bei dieser Konfiguration wird eine Benutzerauthentifizierungsmethode hinzugefügt, die von der von der SharePoint Server 2016-Installation selbst verwendeten AD DS-Authentifizierung getrennt ist. Um von diesem Artikel zu profitieren, sollten Sie mit WS-Federation vertraut sein. Weitere Informationen finden Sie unter [Grundlegendes zu WS-Federation](https://go.microsoft.com/fwlink/p/?linkid=188052). Ausführliche Informationen zur Integration von SharePoint lokal mit Azure Active Directory finden Sie im dedizierten [Lernprogramm](https://docs.microsoft.com/azure/active-directory/saas-apps/sharepoint-on-premises-tutorial).

![Verwenden von Azure AD für die SharePoint-Authentifizierung](media/SAML11/fig1-architecture.png)

Zuvor hätte diese Konfiguration einen Verbunddienst wie Azure Access Control Service (ACS) in der Cloud oder eine Umgebung benötigt, die Active Directory-Verbunddienste (AD FS) zum Transformieren von Token von SAML 2,0 zu SAML 1,1 hostet. Diese Transformation ist nicht mehr erforderlich, da Azure AD jetzt das Ausgeben von SAML 1,1-Token ermöglicht. Das obige Diagramm zeigt die Funktionsweise der Authentifizierung für SharePoint 2016-Benutzer in dieser Konfiguration, was darauf hingewiesen wird, dass es für einen Vermittler nicht mehr erforderlich ist, diese Transformation durchzuführen.

> [!NOTE]
> Diese Konfiguration funktioniert, ob die SharePoint-Farm auf virtuellen Azure-Computern oder lokal gehostet wird. Es ist nicht erforderlich, zusätzliche Firewall-Ports zu öffnen, außer sicherzustellen, dass Benutzer über Ihren Browser auf Azure Active Directory zugreifen können.

Informationen zur Barrierefreiheit von SharePoint 2016 finden Sie unter [Accessibility Guidelines in SharePoint Server 2016](https://go.microsoft.com/fwlink/p/?LinkId=393123).

## <a name="configuration-overview"></a>Übersicht über die Konfiguration

Führen Sie die folgenden allgemeinen Schritte aus, um Ihre Umgebung für die Verwendung von Azure AD als SharePoint Server 2016 Identity Provider einzurichten.

1. Erstellen Sie ein neues Azure AD-Verzeichnis, oder verwenden Sie Ihr vorhandenes Verzeichnis.
2. Stellen Sie sicher, dass die Zone für die Webanwendung, die Sie mit Azure AD sichern möchten, für die Verwendung von SSL konfiguriert ist.
3. Erstellen Sie eine neue Enterprise-Anwendung in Azure AD.
4. Konfigurieren Sie einen neuen vertrauenswürdigen Identitätsanbieter in SharePoint Server 2016.
5. Legen Sie die Berechtigungen für die Webanwendung fest.
6. Hinzufügen einer SAML 1,1-Token-Veröffentlichungsrichtlinie in Azure AD.
7. Überprüfen Sie den neuen Anbieter.

In den folgenden Abschnitten wird beschrieben, wie Sie diese Aufgaben ausführen.

## <a name="step-1-create-a-new-azure-ad-directory-or-use-your-existing-directory"></a>Schritt 1: Erstellen eines neuen Azure AD-Verzeichnisses oder Verwenden des vorhandenen Verzeichnisses

Erstellen Sie im Azure-[https://portal.azure.com](https://portal.azure.com)Portal () ein neues Verzeichnis. Geben Sie den Namen der Organisation, den anfänglichen Domänennamen und das Land oder die Region an.

![Erstellen eines Verzeichnisses](media/SAML11/fig2-createdirectory.png) 

 Wenn Sie bereits über ein Verzeichnis wie das für Microsoft Office 365 oder Ihr Microsoft Azure-Abonnement verfügen, können Sie dieses Verzeichnis verwenden. Sie benötigen Berechtigungen zum Registrieren von Anwendungen im Verzeichnis.

## <a name="step-2-ensure-the-zone-for-the-web-application-that-you-want-to-secure-with-azure-ad-is-configured-to-use-ssl"></a>Schritt 2: Stellen Sie sicher, dass die Zone für die Webanwendung, die Sie mit Azure AD sichern möchten, für die Verwendung von SSL konfiguriert ist.

Dieser Artikel wurde mit der Referenzarchitektur in [Ausführen einer hoch verfügbaren SharePoint Server 2016-Farm in Azure](https://docs.microsoft.com/en-us/azure/architecture/reference-architectures/sharepoint)geschrieben. Mit den Begleit Skripts des Artikels, die zum Bereitstellen der in [diesem Artikel](https://docs.microsoft.com/en-us/azure/architecture/reference-architectures/sharepoint) beschriebenen Lösung verwendet werden, wird eine Website erstellt, die nicht SSL verwendet.  

Für die Verwendung von SAML muss die Anwendung so konfiguriert sein, dass SSL verwendet werden kann. Wenn Ihre SharePoint-Webanwendung nicht für die Verwendung von SSL konfiguriert ist, führen Sie die folgenden Schritte aus, um ein neues selbstsigniertes Zertifikat zu erstellen, um die Webanwendung für SSL zu konfigurieren. Diese Konfiguration ist nur für eine Lab-Umgebung gedacht und ist nicht für die Produktion vorgesehen. In Produktionsumgebungen sollte ein signiertes Zertifikat verwendet werden.

1. Wechseln Sie zur **zentral Administration** > **Anwendungsverwaltung** > **Verwalten**von Webanwendungen, und wählen Sie die Webanwendung aus, die für die Verwendung von SSL erweitert werden muss. Wählen Sie die Webanwendung aus, und klicken Sie auf die Menüband-Schaltfläche **erweitern** . Erweitern Sie die Webanwendung so, dass Sie dieselbe URL verwendet, aber SSL mit dem Anschluß 443 verwendet.<br/>![Erweitern der Web-App auf eine andere IIS-Website](media/SAML11/fig3-extendwebapptoiis.png)<br/>
2. Doppelklicken Sie in IIS-Manager auf **Serverzertifikate**.
3. Klicken Sie im Bereich **Aktionen** auf **Selbstsigniertes Zertifikat erstellen**. Geben Sie in das Feld Anzeigename für das Zertifikat einen Anzeigenamen ein, und klicken Sie auf **OK**.
4. Stellen Sie im Dialogfeld **Websitebindung bearbeiten** sicher, dass der Hostname dem Anzeigenamen entspricht, wie in der folgenden Abbildung dargestellt.<br/>![Bearbeiten der Websitebindung in IIS](media/SAML11/fig4-editsitebinding.png)<br/>

Jeder der Web-Front-End-Server in der SharePoint-Farm erfordert die Konfiguration des Zertifikats für die Websitebindung in IIS.


## <a name="step-3-create-a-new-enterprise-application-in-azure-ad"></a>Schritt 3: Erstellen einer neuen Enterprise-Anwendung in Azure AD

1. Öffnen Sie im Azure-[https://portal.azure.com](https://portal.azure.com)Portal () Ihr Azure AD-Verzeichnis. Klicken Sie auf **Enterprise-Anwendungen**und dann auf **neue Anwendung**. Wählen Sie **nicht-Kataloganwendung**aus. Geben Sie einen Namen wie die *SharePoint SAML-Integration* an, und klicken Sie auf **Hinzufügen**.<br/>![Hinzufügen einer neuen nicht-Kataloganwendung](media/SAML11/fig5-addnongalleryapp.png)<br/>
2. Klicken Sie im Navigationsbereich auf den Link einmaliges Anmelden, um die Anwendung zu konfigurieren. Ändern Sie den Dropdown **Modus für einmaliges Anmelden** in **SAML-basiertes anmelden** , um die SAML-Konfigurationseigenschaften für die Anwendung anzuzeigen. Konfigurieren Sie mit den folgenden Eigenschaften:<br/>
    - Bezeichner`urn:sharepoint:portal.contoso.local`
    - Antwort-URL:`https://portal.contoso.local/_trust/default.aspx`
    - Anmelde-URL:`https://portal.contoso.local/_trust/default.aspx`
    - Benutzer-ID:`user.userprincipalname`<br/>
    - Hinweis: Denken Sie daran, die URLs zu ändern, indem Sie *Portal. contoso. local* durch die URL der zu sichernden SharePoint-Website ersetzen.<br/>
3. Richten Sie eine Tabelle ein (ähnlich wie in Tabelle 1 unten), die die folgenden Zeilen enthält:<br/> 
    - Realm
    - Vollständiger Pfad zur SAML-Signaturzertifikats Datei
    - SAML-URL für einmaliges Anmelden (Ersetzen von */saml2* durch */wsfed*)
    - Anwendungsobjekt-ID. <br/>
Kopieren Sie den *Identifier* -Wert in die *Realm* -Eigenschaft in eine Tabelle (siehe Tabelle 1 unten.)
4. Speichern Sie Ihre Änderungen.
5. Klicken Sie auf den Link **Configure (App Name)** , um auf die Seite "Anmelden konfigurieren" zuzugreifen.<br/>![Konfigurieren einer Single-Sign-On-Seite](media/SAML11/fig7-configssopage.png)<br/> 
    -  Klicken Sie auf den Link **SAML Signing Certificate-RAW** , um das SAML-Signaturzertifikat als Datei mit der Erweiterung. CER herunterzuladen. Kopieren Sie den vollständigen Pfad der heruntergeladenen Datei in Ihre Tabelle, und fügen Sie ihn ein.
    - Kopieren Sie den SAML-URL-Link für einmaliges Anmelden und fügen Sie ihn in Ihre ein, und ersetzen Sie dabei den */saml2* -Teil der URL durch */wsfed*.<br/>
6.  Navigieren Sie zum Bereich **Eigenschaften** für die Anwendung. Kopieren Sie den Wert der Objekt-ID in die Tabelle, die Sie in Schritt 3 eingerichtet haben, und fügen Sie ihn ein.<br/>![Eigenschaftenbereich für die Anwendung](media/SAML11/fig8-propertiespane.png)<br/>
7. Stellen Sie mithilfe der erfassten Werte sicher, dass die Tabelle, die Sie in Schritt 3 eingerichtet haben, der Tabelle 1 ähnelt.


| Tabelle 1: erfasste Werte  |  |
|---------|---------|
|Realm | `urn:sharepoint:portal.contoso.local` |
|Vollständiger Pfad zur SAML-Signaturzertifikats Datei | `C:/temp/SharePoint SAML Integration.cer`  |
|SAML-URL für einmaliges Anmelden (ersetzen Sie/saml2 durch/wsfed) | `https://login.microsoftonline.com/b1726649-b616-460d-8d20-defab80d476c/wsfed` |
|Anwendungsobjekt-ID | `a812f48b-d1e4-4c8e-93be-e4808c8ca3ac` |

> [!IMPORTANT]
> Ersetzen Sie den */saml2* -Wert in der URL durch */wsfed*. Der */saml2* -Endpunkt verarbeitet SAML 2,0-Token. Der */wsfed* -Endpunkt ermöglicht die Verarbeitung von SAML 1,1-Token und ist für SharePoint 2016 SAML Federation erforderlich.

## <a name="step-4-configure-a-new-trusted-identity-provider-in-sharepoint-server-2016"></a>Schritt 4: Konfigurieren eines neuen vertrauenswürdigen Identitätsanbieters in SharePoint Server 2016

Melden Sie sich beim SharePoint Server 2016-Server an, und öffnen Sie die SharePoint 2016-Verwaltungsshell. Geben Sie die Werte $Realm, $wsfedurl und $filePath aus Tabelle 1 ein, und führen Sie die folgenden Befehle aus, um einen neuen vertrauenswürdigen Identitätsanbieter zu konfigurieren.

> [!TIP]
> Wenn Sie mit PowerShell noch nicht vertraut sind oder mehr über die Funktionsweise von PowerShell erfahren möchten, finden Sie weitere Informationen unter [SharePoint PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/overview?view=sharepoint-ps). 

```
$realm = "<Realm from Table 1>"
$wsfedurl="<SAML single sign-on service URL from Table 1>"
$filepath="<Full path to SAML signing certificate file from Table 1>"
$cert = New-Object System.Security.Cryptography.X509Certificates.X509Certificate2($filepath)
New-SPTrustedRootAuthority -Name "AzureAD" -Certificate $cert
$map = New-SPClaimTypeMapping -IncomingClaimType "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name" -IncomingClaimTypeDisplayName "name" -LocalClaimType "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/upn"
$map2 = New-SPClaimTypeMapping -IncomingClaimType "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/givenname" -IncomingClaimTypeDisplayName "GivenName" -SameAsIncoming
$map3 = New-SPClaimTypeMapping -IncomingClaimType "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/surname" -IncomingClaimTypeDisplayName "SurName" -SameAsIncoming
$ap = New-SPTrustedIdentityTokenIssuer -Name "AzureAD" -Description "SharePoint secured by Azure AD" -realm $realm -ImportTrustCertificate $cert -ClaimsMappings $map,$map2,$map3 -SignInUrl $wsfedurl -IdentifierClaim "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name"
```

Führen Sie als nächstes die folgenden Schritte aus, um den vertrauenswürdigen Identitätsanbieter für Ihre Anwendung zu aktivieren:
1. Navigieren Sie in der zentral Administration zu **Webanwendung verwalten** , und wählen Sie die Webanwendung aus, die Sie mit Azure AD sichern möchten. 
2. Klicken Sie im Menüband auf **Authentifizierungsanbieter** , und wählen Sie die Zone aus, die Sie verwenden möchten.
3. Wählen Sie **vertrauenswürdiger Identitätsanbieter** aus, und wählen Sie den identifizierten Anbieter, den Sie soeben mit dem Namen *AzureAD*.  
4. Wählen Sie auf der Anmeldeseiten-URL-Einstellung **benutzerdefinierte Anmeldeseite** aus, und geben Sie den Wert "/_trust/" an. 
5. Klicken Sie auf **OK**.

![Konfigurieren des Authentifizierungsanbieters](media/SAML11/fig10-configauthprovider.png)

> [!IMPORTANT]
> Es ist wichtig, alle Schritte zu befolgen, einschließlich der Einstellung der benutzerdefinierten Anmeldeseite auf "/_trust/" wie gezeigt. Die Konfiguration funktioniert nur, wenn alle Schritte befolgt werden.

## <a name="step-5-set-the-permissions"></a>Schritt 5: Festlegen der Berechtigungen

Die Benutzer, die sich bei Azure AD anmelden und auf SharePoint zugreifen, müssen Zugriff auf die Anwendung erhalten. 

1. Öffnen Sie im Azure-Portal das Azure AD-Verzeichnis. Klicken Sie auf **Enterprise-Anwendungen**und dann auf **alle Anwendungen**. Klicken Sie auf die Anwendung, die Sie zuvor erstellt haben (SharePoint SAML-Integration).
2. Klicken Sie auf **Benutzer und Gruppen**. 
3. Klicken Sie auf **Benutzer hinzufügen** , um einen Benutzer oder eine Gruppe hinzuzufügen, der über die Berechtigung zum Anmelden an SharePoint mit Azure AD verfügt.
4. Wählen Sie den Benutzer oder die Gruppe aus, und klicken Sie auf **zuweisen**.
 
Dem Benutzer wurde die Berechtigung in Azure AD erteilt, es muss aber auch eine Berechtigung in SharePoint erteilt werden. Gehen Sie folgendermaßen vor, um die Zugriffsberechtigungen für die Webanwendung festzulegen.

1. Klicken Sie in der Zentraladministration auf **Anwendungsverwaltung**.
2. Klicken Sie auf der Seite **Anwendungsverwaltung** im Abschnitt **Webanwendungen** auf **Webanwendungen verwalten**.
3. Klicken Sie auf die entsprechende Webanwendung und anschließend auf **Benutzerrichtlinie**.
4. Klicken Sie unter Richtlinie für Webanwendung auf **Benutzer hinzufügen**.<br/>![Suchen nach einem Benutzer anhand des Namens](media/SAML11/fig11-searchbynameclaim.png)<br/>
5. Klicken Sie im Dialogfeld **Benutzer hinzufügen** in **Zonen** auf die entsprechende Zone, und klicken Sie dann auf **Weiter**.
6. Klicken Sie im Dialogfeld **Richtlinie für Webanwendung** im Abschnitt **Benutzer auswählen** auf das Symbol **Durchsuchen** .
7. Geben Sie im Textfeld **Suchen** den Anmeldenamen für einen Benutzer in Ihrem Verzeichnis ein, und klicken Sie auf **Suchen**. <br/>Beispiel: *demouser@blueskyabove.onmicrosoft.com*.
8. Wählen Sie in der Listenansicht unter der Überschrift AzureAD aus, und klicken Sie dann auf **Hinzufügen** und dann auf **OK** , um das Dialogfeld zu schließen.
9. Klicken Sie unter Berechtigungen auf **Vollzugriff**.<br/>![Erteilen von Vollzugriff für einen Forderungs Benutzer](media/SAML11/fig12-grantfullcontrol.png)<br/>
10. Klicken Sie auf **Fertig stellen**, und klicken Sie dann auf **OK**.

## <a name="step-6-add-a-saml-11-token-issuance-policy-in-azure-ad"></a>Schritt 6: Hinzufügen einer SAML 1,1-Token-Veröffentlichungsrichtlinie in Azure AD

Wenn die Azure AD-Anwendung im Portal erstellt wird, wird standardmäßig SAML 2,0 verwendet. SharePoint Server 2016 erfordert das SAML 1,1-Tokenformat. Das folgende Skript entfernt die Standardrichtlinie für SAML 2,0 und fügt eine neue Richtlinie zum Ausgeben von SAML 1,1-Tokens hinzu. 

> Dieser Code erfordert das Herunterladen der begleitenden Beispiele, die die [Interaktion mit Azure Active Directory-Diagramm demonstrieren](https://github.com/kaevans/spsaml11/tree/master/scripts). Wenn Sie die Skripts als ZIP-Datei von GitHub auf einen Windows-Desktop herunterladen, müssen Sie die `MSGraphTokenLifetimePolicy.psm1` Blockierung der Skriptmodul Datei `Initialize.ps1` und der Skriptdatei aufheben (Klicken Sie mit der rechten Maustaste auf Eigenschaften, klicken Sie auf Entsperren und dann auf OK). 
![Aufheben der Blockierung von heruntergeladenen Dateien](media/SAML11/fig17-unblock.png)

Nachdem das Beispielskript heruntergeladen wurde, erstellen Sie ein neues PowerShell-Skript mithilfe des folgenden Codes, und ersetzen Sie dabei den Platzhalter `Initialize.ps1` durch den Dateipfad des heruntergeladenen auf dem lokalen Computer. Ersetzen Sie den Platzhalter für die Anwendungsobjekt-ID durch die Anwendungsobjekt-ID, die Sie in Tabelle 1 eingegeben haben. Führen Sie nach der Erstellung das PowerShell-Skript aus. 

```
function AssignSaml11PolicyToAppPrincipal
{
    Param(
        [Parameter(Mandatory=$true)]
        [string]$pathToInitializeScriptFile, 
        [Parameter(Mandatory=$true)]
        [string]$appObjectid
    )

    $folder = Split-Path $pathToInitializeScriptFile
    Push-Location $folder

    #Loads the dependent ADAL module used to acquire tokens
    Import-Module $pathToInitializeScriptFile 

    #Gets the existing token issuance policy
    $existingTokenIssuancePolicy = Get-PoliciesAssignedToServicePrincipal -servicePrincipalId $appObjectid | ?{$_.type -EQ "TokenIssuancePolicy"} 
    Write-Host "The following TokenIssuancePolicy policies are assigned to the service principal." -ForegroundColor Green
    Write-Host $existingTokenIssuancePolicy -ForegroundColor White
    $policyId = $existingTokenIssuancePolicy.objectId

    #Removes existing token issuance policy
    Write-Host "Only a single policy can be assigned to the service principal. Removing the existing policy with ID $policyId" -ForegroundColor Green
    Remove-PolicyFromServicePrincipal -policyId $policyId -servicePrincipalId $appObjectid

    #Creates a new token issuance policy and assigns to the service principal
    Write-Host "Adding the new SAML 1.1 TokenIssuancePolicy" -ForegroundColor Green
    $policy = Add-TokenIssuancePolicy -DisplayName SPSAML11 -SigningAlgorithm "http://www.w3.org/2001/04/xmldsig-more#rsa-sha256" -TokenResponseSigningPolicy TokenOnly -SamlTokenVersion "1.1"
    Write-Host "Assigning the new SAML 1.1 TokenIssuancePolicy $policy.objectId to the service principal $appObjectid" -ForegroundColor Green
    Set-PolicyToServicePrincipal -policyId $policy.objectId -servicePrincipalId $appObjectid
    Pop-Location
}

#Only edit the following two variables
$pathToInitializeScriptFile = "<file path of Initialize.ps1>"
$appObjectid = "<Application Object ID from Table 1>"

AssignSaml11PolicyToAppPrincipal $pathToInitializeScriptFile $appObjectid
```
> [!IMPORTANT]
> Die PowerShell-Skripts sind nicht signiert, und Sie werden möglicherweise aufgefordert, die Ausführungsrichtlinie festzulegen. Weitere Informationen zu Ausführungsrichtlinien finden Sie unter [Informationen zu Ausführungsrichtlinien](http://go.microsoft.com/fwlink/?LinkID=135170). Darüber hinaus müssen Sie möglicherweise eine Eingabeaufforderungen mit erhöhten Rechten öffnen, um die in den Beispielskripts enthaltenen Befehle erfolgreich auszuführen.

Diese Beispiel-PowerShell-Befehle sind Beispiele für das Ausführen von Abfragen für die Graph-API. Weitere Informationen zu Token-Ausstellungsrichtlinien mit Azure AD finden Sie in der [Graph-API-Referenz für Vorgänge in der Richtlinie](https://msdn.microsoft.com/en-us/library/azure/ad/graph/api/policy-operations#create-a-policy).

## <a name="step-7-verify-the-new-provider"></a>Schritt 7: Überprüfen des neuen Anbieters

Öffnen Sie einen Browser für die URL der Webanwendung, die Sie in den vorherigen Schritten konfiguriert haben. Sie werden umgeleitet, um sich bei Azure AD anzumelden.

![Anmelden bei Azure AD, konfiguriert für den Verbund](media/SAML11/fig13-examplesignin.png)

Sie werden gefragt, ob Sie angemeldet bleiben möchten.

![Bleiben Sie angemeldet?](media/SAML11/fig14-staysignedin.png)

Schließlich können Sie auf die Website zugreifen, die als Benutzer aus Ihrem Azure Active Directory-Mandanten angemeldet ist.

![In SharePoint signierter Benutzer](media/SAML11/fig15-signedinsharepoint.png)

## <a name="managing-certificates"></a>Verwalten von Zertifikaten
Beachten Sie, dass das Signaturzertifikat, das für den vertrauenswürdigen Identitätsanbieter in Schritt 4 oben konfiguriert wurde, ein Ablaufdatum aufweist und erneuert werden muss. Weitere Informationen zur Zertifikaterneuerung finden Sie im Artikel [manage certificates for Federated Single Sign-on in Azure Active Directory](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-sso-certs) . Nachdem das Zertifikat in Azure AD erneuert wurde, laden Sie es in eine lokale Datei herunter, und verwenden Sie das folgende Skript, um den vertrauenswürdigen Identitätsanbieter mit dem erneuten Signier Zertifikat zu konfigurieren. 

```
$filepath="<Full path to renewed SAML signing certificate file>"
$cert= New-Object System.Security.Cryptography.X509Certificates.X509Certificate2($filePath)
New-SPTrustedRootAuthority -Name "AzureAD" -Certificate $cert
Get-SPTrustedIdentityTokenIssuer "AzureAD" | Set-SPTrustedIdentityTokenIssuer -ImportTrustCertificate $cert
```
## <a name="configuring-one-trusted-identity-provider-for-multiple-web-applications"></a>Konfigurieren eines vertrauenswürdigen Identitätsanbieters für mehrere Webanwendungen
Die Konfiguration funktioniert für eine einzelne Webanwendung, erfordert jedoch eine zusätzliche Konfiguration, wenn Sie denselben vertrauenswürdigen Identitätsanbieter für mehrere Webanwendungen verwenden möchten. Nehmen wir beispielsweise an, dass eine Webanwendung so erweitert wurde, `https://portal.contoso.local` dass Sie die URL verwendet und die Benutzer `https://sales.contoso.local` nun auch authentifizieren soll. Zu diesem Zweck müssen wir den Identitätsanbieter aktualisieren, um den WReply-Parameter zu berücksichtigen und die Anwendungsregistrierung in Azure AD zu aktualisieren, um eine Antwort-URL hinzuzufügen.

1. Öffnen Sie im Azure-Portal das Azure AD-Verzeichnis. Klicken Sie auf **App**-Registrierungen, und klicken Sie dann auf **alle Anwendungen anzeigen**. Klicken Sie auf die Anwendung, die Sie zuvor erstellt haben (SharePoint SAML-Integration).
2. Klicken Sie auf **Einstellungen**.
3. Klicken Sie auf dem Blatt Einstellungen auf **Reply URLs**. 
4. Fügen Sie die URL für die zusätzliche Webanwendung `/_trust/default.aspx` hinzu, die der URL angefügt wird ( `https://sales.contoso.local/_trust/default.aspx`beispielsweise), und klicken Sie auf **Speichern**. 
5. Öffnen Sie auf dem SharePoint-Server die **SharePoint 2016-Verwaltungsshell** , und führen Sie die folgenden Befehle unter Verwendung des Namens des Ausstellers für vertrauenswürdige Identitätstoken aus, den Sie zuvor verwendet haben.

```
$t = Get-SPTrustedIdentityTokenIssuer "AzureAD"
$t.UseWReplyParameter=$true
$t.Update()
```
6. Wechseln Sie in der zentral Administration zur Webanwendung, und aktivieren Sie den vorhandenen vertrauenswürdigen Identitätsanbieter. Denken Sie daran, die Anmeldeseiten-URL auch als benutzerdefinierte Anmeldeseite `/_trust/`zu konfigurieren.
7. Klicken Sie in der zentral Administration auf die Webanwendung, und wählen Sie **Benutzerrichtlinie**aus. Fügen Sie einen Benutzer mit den entsprechenden Berechtigungen hinzu, wie zuvor in diesem Artikel veranschaulicht.

## <a name="fixing-people-picker"></a>Fixieren der Personenauswahl
Benutzer können sich jetzt in SharePoint 2016 mit Identitäten von Azure AD anmelden, aber es gibt noch Möglichkeiten zur Verbesserung der Benutzerfreundlichkeit. Wenn Sie beispielsweise nach einem Benutzer suchen, werden in der Personenauswahl mehrere Suchergebnisse angezeigt. Für jeden der drei Anspruchstypen, die in der Anspruchszuordnung erstellt wurden, gibt es ein Suchergebnis. Wenn Sie einen Benutzer mithilfe der Personenauswahl auswählen möchten, müssen Sie den Benutzernamen genau eingeben und den **Namen** Claim result auswählen.

![Ergebnisse der Forderungs Suche](media/SAML11/fig16-claimssearchresults.png)

Es gibt keine Validierung der Werte, die Sie suchen, was zu Rechtschreibfehlern führen kann, oder Benutzer, die versehentlich den falschen Anspruchstyp auswählen, um Sie wie den **Familiennamen** zu beanspruchen. Dadurch kann verhindert werden, dass Benutzer auf Ressourcen zugreifen.

Zur Unterstützung dieses Szenarios gibt es eine Open Source-Lösung mit dem Namen [AzureCP](https://yvand.github.io/AzureCP/) , die einen benutzerdefinierten anspruchsanbieter für SharePoint 2016 bereitstellt. Das Azure AD-Diagramm wird verwendet, um zu beheben, welche Benutzer eine Validierung durchführen. Weitere Informationen finden Sie unter [AzureCP](https://yvand.github.io/AzureCP/). 

## <a name="additional-resources"></a>Zusätzliche Ressourcen

[Grundlegendes zu WS-Federation](https://go.microsoft.com/fwlink/p/?linkid=188052)
  
[Cloudakzeptanz und Hybridlösungen](cloud-adoption-and-hybrid-solutions.md)
  
## <a name="join-the-discussion"></a>An der Diskussion teilnehmen

|**Kontakt**|**Beschreibung**|
|:-----|:-----|
|**Welche Lösungen benötigen Sie?** <br/> |Wir entwickeln Inhalte für Lösungen auf Grundlage mehrerer Microsoft-Produkte und -Dienste. Lassen Sie uns wissen, was Sie von unseren serverübergreifenden Lösungen halten, oder fordern Sie spezifische Lösungen an, indem Sie eine E-Mail an [MODAcontent@microsoft.com](mailto:cloudadopt@microsoft.com?Subject=[Cloud%20Adoption%20Content%20Feedback]:%20) senden.<br/> |
|**An der Diskussion über Lösungen teilnehmen** <br/> |Wenn Sie sich für Cloud-basierte Lösungen interessieren, werden Sie Teil des Cloud Adoption Advisory Board (CAAB), um Zugriff auf eine größere, dynamische Community aus Microsoft-Inhaltsentwicklern, Branchenexperten und Kunden aus aller Welt zu haben. Um beizutreten, fügen Sie sich selbst als Mitglied des [CAAB (Cloud Adoption Advisory Board)-Bereichs](https://aka.ms/caab) der Microsoft Tech Community hinzu, und senden Sie uns eine E-Mail an [CAAB@microsoft.com](mailto:caab@microsoft.com?Subject=I%20just%20joined%20the%20Cloud%20Adoption%20Advisory%20Board!). Communityinhalte stehen allen Personen im [CAAB-Blog](https://blogs.technet.com/b/solutions_advisory_board/) zur Verfügung. CAAB-Mitglieder erhalten jedoch Einladungen zu privaten Webinaren, die neue Ressourcen und Lösungen für den Cloud-Einsatz beschreiben.<br/> |
|**Die hier gezeigte Grafik abrufen** <br/> |Wenn Sie eine bearbeitbare Kopie der Grafik wünschen, die Sie in disem Artikel sehen, senden wir Sie Ihnen gerne zu. Senden Sie eine E-Mail mit der Anforderung einschließlich der URL und dem Titel der Grafik an [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?subject=[Art%20Request]:%20).  <br/> |
   

