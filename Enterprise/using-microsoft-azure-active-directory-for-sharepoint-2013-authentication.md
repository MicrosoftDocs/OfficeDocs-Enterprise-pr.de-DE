---
title: "Verwenden von Microsoft Azure Active Directory für die SharePoint 2013-Authentifizierung"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Top
ms.custom:
- DecEntMigration
- Ent_Solutions
ms.assetid: bef810a4-53f6-4962-878e-e20b5019baeb
description: 'Zusammenfassung: Erfahren Sie, wie den Azure Access Control Service verwenden, um SharePoint Server 2013-Benutzer mit Azure Active Directory zu authentifizieren.'
ms.openlocfilehash: 85db8376aeb06ef6f291b563410c991ea24351d5
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2017
---
# <a name="using-microsoft-azure-active-directory-for-sharepoint-2013-authentication"></a>Verwenden von Microsoft Azure Active Directory für die SharePoint 2013-Authentifizierung

 **Zusammenfassung:** Erfahren Sie, wie den Azure Access Control Service verwenden, um SharePoint Server 2013-Benutzer mit Azure Active Directory zu authentifizieren.
  
Die Verwaltung der Benutzer kann einfacher sein, wenn Sie sie mithilfe unterschiedlicher Identitätsanbieter authentifizieren. Berücksichtigen Sie, wie bequem es sein kann, einen Identitätsanbieter zu nutzen, den Sie als vertrauenswürdig einstufen, den aber eine andere Person verwaltet. Sie können beispielsweise über einen Authentifizierungstyp für Benutzer verfügen, die auf SharePoint Server 2013 in der Cloud zugreifen, und über einen weiteren für SharePoint 2013-Benutzer in Ihrer lokalen Umgebung. Der Azure Access Control Service ermöglicht diese Optionen. 
  
In diesem Artikel wird erläutert, wie Sie den Azure Access Control Service zum Authentifizieren der SharePoint 2013-Benutzer mit Azure AD anstatt mit Ihrem lokalen Active Directory verwenden können. Bei dieser Konfiguration wird Azure AD zu einem vertrauenswürdigen Identitätsanbieter für SharePoint 2013. Diese Konfiguration fügt eine Authentifizierungsmethode für Benutzer hinzu, die getrennt von der Active Directory-Authentifizierung ist, die von der SharePoint 2013-Installation selbst verwendet wird. Um von diesem Artikel zu profitieren, sollten Sie mit WS-Federation vertraut sein. Weitere Informationen finden Sie unter [Grundlegendes zu WS-Federation](https://go.microsoft.com/fwlink/p/?linkid=188052).
  
Die folgende Abbildung veranschaulicht die Funktionsweise der Authentifizierung für SharePoint 2013-Benutzer bei dieser Konfiguration.
  
![Mit Azure Active Directory authentifizierte Benutzer](images/SP_AzureAD.png)
  
Das in diesem Artikel verwendete Beispiel stammt von Kirk Evans, Microsoft Architect für das Azure Center of Excellence. 
  
Informationen zur SharePoint 2013-Barrierefreiheit finden Sie unter [Barrierefreiheit für SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=393123).
  
## <a name="configuration-overview"></a>Übersicht über die Konfiguration

Führen Sie die folgenden allgemeinen Schritte zum Einrichten der Umgebung für das Verwenden von Azure AD als SharePoint 2013-Identitätsanbieter aus.
  
1. Erstellen Sie einen neuen Azure AD-Mandanten und -Namespace.
    
2. Fügen Sie einen WS-Federation-Identitätsanbieter hinzu.
    
3. Fügen SharePoint als eine Anwendung der vertrauenden Seite hinzu.
    
4. Erstellen Sie ein selbstsigniertes für SSL zu verwendendes Zertifikat.
    
5. Erstellen Sie eine Regelgruppe für die anspruchsbasierte Authentifizierung.
    
6. Konfigurieren Sie das X.509-Zertifikat.
    
7. Erstellen Sie eine Anspruchszuordnung.
    
8. Konfigurieren Sie SharePoint für den neuen Identitätsanbieter.
    
9. Legen Sie die Berechtigungen fest.
    
10. Überprüfen Sie den neuen Anbieter.
    
## <a name="create-azure-ad-tenant-and-namespace"></a>Erstellen eines neuen Azure AD-Mandanten und -Namespace

Führen Sie die folgenden Schritte zum Erstellen eines neuen Azure AD-Mandanten und eines zugehörigen Namespace aus. In diesem Beispiel verwenden wir den Namespace "Blueskyabove". 
  
1. Klicken Sie im Azure-Verwaltungsportal auf **Active Directory**, und erstellen Sie einen neuen Azure AD-Mandanten.
    
2. Klicken Sie auf **Access Control-Namespaces**, und erstellen Sie einen neuen Namespace. 
    
3. Klicken Sie auf der unteren Leiste auf **Verwalten**. Dadurch wird dieser Speicherort geöffnet: https://blueskyabove.accesscontrol.windows.net/v2/mgmt/web.
    
4. Öffnen Sie Windows PowerShell. Verwenden Sie das Microsoft Online Services-Modul für Windows PowerShell, das eine Voraussetzung für die Installation von Azure für Windows PowerShell-Cmdlets ist.
    
5. Geben Sie an der Windows PowerShell-Eingabeaufforderung den Befehl  `Connect-Msolservice` und dann Ihre Anmeldeinformationen ein.
    
    > [!NOTE]
    > Weitere Informationen zur Verwendung von Azure für Windows PowerShell-Cmdlets finden Sie unter [Verwalten von Azure AD mit Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=393124). 
  
6. Geben Sie über eine Windows PowerShell-Eingabeaufforderung die folgenden Befehle ein:
    
  ```
  Import-Module MSOnlineExtended -Force
  ```

  ```
  $replyUrl = New-MsolServicePrincipalAddresses -Address "https://blueskyabove.accesscontrol.windows.net/"
  ```

  ```
  New-MsolServicePrincipal -ServicePrincipalNames @("https://blueskyabove.accesscontrol.windows.net/") -DisplayName "BlueSkyAbove ACS Namespace" -Addresses $replyUrl
  ```

    Die folgende Abbildung veranschaulicht das Ergebnis der Ausgabe.
    
     ![Erstellen von Dienstprinzipalnamen](images/ServicePrincipalNames.jpg)
  
## <a name="add-a-ws-federation-identity-provider-to-the-namespace"></a>Hinzufügen eines WS-Federation-Identitätsanbieters zum Namespace

Führen Sie die folgenden Schritte aus, um einen neuen WS-Federation-Identitätsanbieter zum Namespace "Blueskyabove" hinzuzufügen.
  
1. Wechseln Sie im Azure-Verwaltungsportal zu **Active Directory** > **Access Control-Namespaces**, klicken Sie auf **Neue Instanz erstellen** und dann auf **Verwalten**.
    
2. Klicken Sie im Azure Access Control-Portal auf **Identitätsanbieter** > **Hinzufügen**, wie in der folgenden Abbildung dargestellt.
    
     ![Dialogfeld "Identitätsanbieter" in Azure](images/Identity.jpg)
  
3. Klicken Sie auf **WS-Federation-Identitätsanbieter**, wie in der folgenden Abbildung dargestellt, und dann auf **Weiter**.
    
     ![Einstellungen zum Hinzufügen von Identitätsanbietern](images/AddIdentity.jpg)
  
4. Füllen Sie den Anzeigenamen und Anmeldelinktext aus, und klicken Sie auf **Speichern**. Geben Sie für die WS-Federation-Metadaten-URL https://accounts.accesscontrol.windows.net/blueskyabove.onmicrosoft.com/FederationMetadata/2007-06/FederationMetadata.xml ein. Die folgende Abbildung zeigt die Einstellung.
    
     ![Verbundidentitätsanbieter](images/FederationIdentity.jpg)
  
## <a name="add-sharepoint-as-a-relying-party-application"></a>Hinzufügen von SharePoint als eine Anwendung der vertrauenden Seite

Führen Sie die folgenden Schritte aus, um SharePoint als Anwendung der vertrauenden Seite hinzuzufügen.
  
Weitere Informationen zu den Einstellungen der Anwendung der vertrauenden Seite finden Sie unter [Anwendungen der vertrauenden Seite](https://go.microsoft.com/fwlink/p/?LinkId=393125).
  
1. Klicken Sie im Azure Access Control-Portal auf **Anwendungen der vertrauenden Seite** > **Hinzufügen**, wie in der folgenden Abbildung dargestellt.
    
     ![Anwendungseinstellungen der vertrauenden Seite](images/RelyingPartyApplications.jpg)
  
## <a name="create-a-self-signed-certificate-to-use-for-ssl"></a>Erstellen eines selbstsignierten für SSL zu verwendenden Zertifikats.

Führen Sie die folgenden Schritte zum Erstellen einer neuen, selbstsignierten Zertifikats aus, das für die sichere Kommunikation über SSL verwendet werden soll.
  
1. Erweitern Sie die Webanwendung für die Verwendung derselben URL wie "PublishingSite", wählen Sie aber SSL mit Port 443, wie in der folgenden Abbildung dargestellt.
    
     ![Einstellungen zur Anwendungserweiterung](images/ExtendWebApp.jpg)
  
2. Doppelklicken Sie in IIS-Manager auf **Serverzertifikate**.
    
3. Klicken Sie im Bereich **Aktionen** auf **Selbstsigniertes Zertifikat erstellen**. Geben Sie in das Feld **Anzeigename für das Zertifikat** einen Anzeigenamen ein, und klicken Sie auf **OK**.
    
4. Vergewissern Sie sich im Dialogfeld **Sitebindung bearbeiten**, dass der Hostname dem Anzeigenamen entspricht, wie in den folgenden Abbildungen dargestellt.
    
     ![Assistent "Selbstsigniertes Zertifikat erstellen"](images/SelfSignedCert.jpg)
  
     ![Hostname im Dialogfeld "Bindungen bearbeiten"](images/SelfSignedCert1.jpg)
  
5. Klicken Sie im Azure-Verwaltungsportal auf den virtuellen Computer, den Sie konfigurieren möchten, und klicken Sie dann auf **Endpunkte**.
    
6. Klicken Sie auf **Hinzufügen** und dann auf **-->** (für "Weiter").
    
7. Geben Sie in das Feld **Name** einen Namen für den Endpunkt ein.
    
8. Geben Sie in **Öffentlicher Port** und **Privater Port** die Portnummern ein, die Sie verwenden möchten, und klicken Sie dann zum Fertigstellen auf das Häkchen. Diese Nummern können unterschiedlich sein. In diesem Artikel verwenden wir 443, wie in der folgenden Abbildung dargestellt.
    
     ![Endpunkteinstellungen in Azure](images/AddEndpoint.jpg)
  
    > [!NOTE]
    > Weitere Informationen dazu, wie Sie einem virtuellen Computer einen Endpunkt in Azure hinzufügen, finden Sie unter [Einrichten von Endpunkten für einen virtuellen Computer](https://go.microsoft.com/fwlink/p/?LinkId=393126). 
  
9. Fügen Sie im Access Control Services-Portal eine vertrauende Seite hinzu, wie in der folgenden Abbildung dargestellt.
    
     ![Einstellungen zum Hinzufügen der vertrauenden Seite](images/AddRelyingParty.jpg)
  
## <a name="create-a-rule-group-for-claims-based-authentication"></a>Erstellen einer Regelgruppe für die anspruchsbasierte Authentifizierung

Führen Sie die folgenden Schritte aus, um eine neue Regelgruppe zur Steuerung der anspruchsbasierten Authentifizierung zu erstellen.
  
1. Klicken Sie im linken Bereich auf **Regelgruppen** und dann auf **Hinzufügen**.
    
2. Geben Sie einen Namen für die Regelgruppe ein, klicken Sie auf **Speichern** und dann auf **Generieren**. In diesem Artikel verwenden wir **Default Rule Group for. spvms.cloudapp.net**, wie in der folgenden Abbildung dargestellt.
    
     ![Regelgruppeneinstellungen in Azure](images/RuleGroup.jpg)
  
     ![Regeln nach Auswahl von "Generieen"](images/GenerateRules.jpg)
  
    > [!NOTE]
    > Weitere Informationen zum Erstellen von Regelgruppen finden Sie unter [Regelgruppen und Regeln](https://go.microsoft.com/fwlink/p/?LinkId=393128). 
  
3. Klicken Sie auf die Regelgruppe, die Sie ändern möchten, und dann auf die Anspruchsregel, die Sie ändern möchten. In diesem Artikel fügen wir der Gruppe eine Anspruchsregel zum Übergeben von **name** als **upn** hinzu, wie in der folgenden Abbildung dargestellt.
    
     ![Anspruchsregeleinstellungen in der Azure-Zugriffssteuerung](images/ClaimRules.jpg)
  
4. Löschen Sie die vorhandene Anspruchsregel **upn**, und belassen Sie die Regel **Name Claim to UPN** unverändert, wie in der folgenden Abbildung dargestellt.
    
     ![Regeleinstellungen in der Azure-Zugriffssteuerung](images/ClaimToUPN.jpg)
  
## <a name="configure-the-x509-certificate"></a>Konfigurieren des X.509-Zertifikats

Führen Sie die folgenden Schritte zum Konfigurieren des X.509-Zertifikats aus, das zum Signieren von Token verwendet wird.
  
1. Klicken Sie im Bereich Access Control Service unter **Entwicklung** auf **Anwendungsintegration**.
    
2. Wechseln Sie in **Endpunktverweis** zur Datei **Federation.xml**, die Ihrem Azure-Mandanten zugeordnet ist, und kopieren Sie den Speicherort in die Adressleiste des Browsers.
    
3. Wechseln Sie in der Datei **Federation.xml** zum Abschnitt **RoleDescriptor**, und kopieren Sie die Informationen aus dem Element  _<X509Certificate>_, wie in der folgenden Abbildung dargestellt.
    
     ![X509-Zertifikatelement in der Datei "Federation.xml"](images/X509Cert.jpg)
  
4. Erstellen Sie im Stammverzeichnis von Laufwerk C:\\ einen Ordner namens **Certificates**.
    
5. Speichern Sie die X.509-Zertifikatinformationen im Ordner C:\\Zertifikate mit dem Dateinamen **AcsTokenSigning.cer**.
    
    > [!NOTE]
    > Der Dateiname muss mit der Erweiterung .cer gespeichert werden. 
  
     ![Speichern von X509-Zertifikatelementinformation als Datei](images/X509Cert_Save.jpg)
  
## <a name="create-a-claim-mapping-by-using-windows-powershell"></a>Erstellen einer Anspruchszuordnung mithilfe von Windows PowerShell

Gehen Sie folgendermaßen vor, um eine Anspruchszuordnung mithilfe von Windows PowerShell zu erstellen.
  
Vergewissern Sie sich, dass Sie über die folgenden Mitgliedschaften verfügen:
  
1. Feste Serverrolle **securityadmin** auf der SQL Server-Instanz.
    
2. Feste Datenbankrolle **db_owner** für alle Datenbanken, die aktualisiert werden sollen.
    
3. Gruppe Administratoren auf dem Server, auf dem die Windows PowerShell-Cmdlets ausgeführt werden.
    
Ein Administrator kann mithilfe des **Add-SPShellAdmin** -Cmdlets Berechtigungen zur Verwendung des SharePoint 2013-Cmdlets gewähren.
  
> [!NOTE]
> Wenn Sie über keine Berechtigungen verfügen, kontaktieren Sie Ihren Setup-Administrator oder SQL Server-Administrator, um die Berechtigungen anzufordern. Weitere Informationen zu Windows PowerShell-Berechtigungen finden Sie unter [Add-SPShellAdmin]((http://technet.microsoft.com/library/2ddfad84-7ca8-409e-878b-d09cb35ed4aa.aspx)). 
  
1. Klicken Sie im **Startmenü** auf **Alle Programme**.
    
2. Klicken Sie auf **Microsoft SharePoint 2013-Produkte**.
    
3. Klicken Sie auf **SharePoint 2013-Verwaltungsshell**.
    
4. Geben Sie an der Windows PowerShell-Eingabeaufforderung den folgenden Befehl ein, um eine neue Anspruchszuordnung zu erstellen:
    
  ```
  $cert = New-Object System.Security.Cryptography.X509Certificates.X509Certificate2("c:\\certificates\\AcsTokenSigning.cer")
  ```

  ```
  New-SPTrustedRootAuthority -Name "ACS BlueSkyAbove Token Signing" -Certificate $cert
  ```

  ```
  $map = New-SPClaimTypeMapping -IncomingClaimType "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/upn" -IncomingClaimTypeDisplayName "UPN" -SameAsIncoming
  ```

  ```
  $map2 = New-SPClaimTypeMapping -IncomingClaimType "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/givenname" -IncomingClaimTypeDisplayName "GivenName" -SameAsIncoming
  ```

  ```
  $map3 = New-SPClaimTypeMapping -IncomingClaimType "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/surname" -IncomingClaimTypeDisplayName "SurName" -SameAsIncoming
  ```

  ```
  $realm = "urn:sharepoint:spvms"
  ```

  ```
  $ap = New-SPTrustedIdentityTokenIssuer -Name "ACS Provider" -Description "SharePoint secured by SAML in ACS" -realm $realm -ImportTrustCertificate $cert -ClaimsMappings $map,$map2,$map3 -SignInUrl "https://blueskyabove.accesscontrol.windows.net/v2/wsfederation" -IdentifierClaim "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/upn"
  ```

## <a name="configure-sharepoint-for-the-new-identity-provider"></a>Konfigurieren von SharePoint für den neuen Identitätsanbieter

Gehen Sie zum Konfigurieren der SharePoint-Installation für den neuen Identitätsanbieter für Azure AD wie folgt vor.
  
1. Vergewissern Sie sich, dass das Benutzerkonto, mit dem dieses Verfahren ausgeführt wird, Mitglied der SharePoint-Gruppe Farmadministratoren ist.
    
2. Klicken Sie in Zentraladministration auf der Startseite auf **Anwendungsverwaltung**.
    
3. Klicken Sie auf der Seite **Anwendungsverwaltung** im Abschnitt **Webanwendungen** auf **Webanwendungen verwalten**.
    
4. Klicken Sie auf die entsprechende Webanwendung.
    
5. Klicken Sie auf dem Menüband auf **Authentifizierungsanbieter**.
    
6. Klicken Sie unter **Zone** auf den Namen der Zone (z. B. **Standard**).
    
7. Wählen Sie auf der Seite **Authentifizierung bearbeiten** im Abschnitt **Forderungsauthentifizierungstypen** die Option **Vertrauenswürdiger Identitätsanbieter**, und klicken Sie dann auf den Namen Ihres Anbieters, der in diesem Artikel **ACS Provider** hießt. Klicken Sie auf **OK**.
    
8. Die folgende Abbildung veranschaulicht die Einstellung **Trusted Provider**.
    
![Einstellung "Vertrauenswürdiger Anbieter" in einer Webanwendung](images/AddProvider_Azure.jpg)
  
## <a name="set-the-permissions"></a>Festlegen der Berechtigungen

Gehen Sie folgendermaßen vor, um die Zugriffsberechtigungen für die Webanwendung festzulegen.
  
1. Klicken Sie in Zentraladministration auf der Startseite auf **Anwendungsverwaltung**.
    
2. Klicken Sie auf der Seite **Anwendungsverwaltung** im Abschnitt **Webanwendungen** auf **Webanwendungen verwalten**.
    
3. Klicken Sie auf die entsprechende Webanwendung und anschließend auf **Benutzerrichtlinie**.
    
4. Klicken Sie unter **Richtlinie für Webanwendung** auf **Benutzer hinzufügen**.
    
5. Klicken Sie im Dialogfeld **Benutzer hinzufügen** in **Zonen** auf die entsprechende Zone, und klicken Sie dann auf **Weiter**.
    
6. Geben Sie in das Dialogfeld **Benutzer hinzufügen** Folgendes ein:user2@blueskyabove.onmicrosoft.com (ACS-Anbieter).
    
7. Klicken Sie in **Berechtigungen** auf **Vollzugriff**.
    
8. Klicken Sie auf **Fertig stellen**, und klicken Sie dann auf **OK**.
    
Die folgende Abbildung zeigt den Abschnitt **Benutzer hinzufügen** einer vorhandenen Webanwendung.
  
![Hinzufügen von Benutzern zu einer vorhandenen Webanwendung](images/AddUsers_Azure.jpg)
  
## <a name="verify-the-new-provider"></a>Überprüfen des neuen Anbieters

Führen Sie die folgenden Schritte aus, um zu prüfen, ob der neuen Identitätsanbieter funktioniert, indem Sie sicherstellen, dass der neue Authentifizierungsanbieter bei der Anmeldeaufforderung angezeigt wird.
  
1. Melden Sie sich mithilfe des neuen Anbieters **Blue Sky Above** an, wie in der folgenden Abbildung dargestellt.
    
     ![Anmeldedialogfeld mit neuem vertrauenswürdigen Anbieter](images/BlueSkyAbove.jpg)
  
## <a name="additional-resources"></a>Zusätzliche Ressourcen

[Grundlegendes zu WS-Federation](https://go.microsoft.com/fwlink/p/?linkid=188052)
  
[Cloudakzeptanz und Hybridlösungen](cloud-adoption-and-hybrid-solutions.md)
  
## <a name="join-the-discussion"></a>An der Diskussion teilnehmen

|**Kontakt**|**Beschreibung**|
|:-----|:-----|
|**Welche Lösungen benötigen Sie?** <br/> |Wir entwickeln Inhalte für Lösungen auf Grundlage mehrerer Microsoft-Produkte und -Dienste. Lassen Sie uns wissen, was Sie von unseren serverübergreifenden Lösungen halten, oder fordern Sie spezifische Lösungen an, indem Sie eine E-Mail an [MODAcontent@microsoft.com](mailto:cloudadopt@microsoft.com?Subject=[Cloud%20Adoption%20Content%20Feedback]:%20) senden.<br/> |
|**An der Diskussion über Lösungen teilnehmen** <br/> |Wenn Sie sich für Cloud-basierte Lösungen interessieren, werden Sie Teil des Cloud Adoption Advisory Board (CAAB), um Zugriff auf eine größere, dynamische Community aus Microsoft-Inhaltsentwicklern, Branchenexperten und Kunden aus aller Welt zu haben. Um beizutreten, fügen Sie sich selbst als Mitglied des [CAAB (Cloud Adoption Advisory Board)-Bereichs]((https://aka.ms/caab)) der Microsoft Tech Community hinzu, und senden Sie uns eine E-Mail an [CAAB@microsoft.com](mailto:caab@microsoft.com?Subject=I%20just%20joined%20the%20Cloud%20Adoption%20Advisory%20Board!). Communityinhalte stehen allen Personen im [CAAB-Blog]((https://blogs.technet.com/b/solutions_advisory_board/)) zur Verfügung. CAAB-Mitglieder erhalten jedoch Einladungen zu privaten Webinaren, die neue Ressourcen und Lösungen für den Cloud-Einsatz beschreiben.<br/> |
|**Die hier gezeigte Grafik abrufen** <br/> |Wenn Sie eine bearbeitbare Kopie der Grafik wünschen, die Sie in disem Artikel sehen, senden wir Sie Ihnen gerne zu. Senden Sie eine E-Mail mit der Anforderung einschließlich der URL und dem Titel der Grafik an [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?subject=[Art%20Request]:%20).  <br/> |
   

