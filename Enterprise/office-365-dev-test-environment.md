---
title: Office 365-Entwicklungs-/Testumgebung
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/02/2019
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
ms.assetid: 4f6035b8-2da3-4cf9-9657-5284d6364f7a
description: 'Zusammenfassung: Verwenden Sie diese Testumgebungsanleitung, um ein Office 365-Testabonnement für Analysen oder Entwicklungs-/Testumgebungen zu erstellen.'
ms.openlocfilehash: a49ba10ab9ddded36f21ca9cc92f0482cbe7a4fb
ms.sourcegitcommit: 201d3338d8bbc6da9389e62e2add8a17384fab4d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/02/2019
ms.locfileid: "31038030"
---
# <a name="office-365-devtest-environment"></a>Office 365-Entwicklungs-/Testumgebung

 **Zusammenfassung:** Verwenden Sie diese Testumgebungsanleitung, um ein Office 365-Testabonnement für Analysen oder Entwicklungs-/Testumgebungen zu erstellen.
  
Sie können ein Office 365-Testabonnement verwenden und eine Office 365-Entwicklungs-/Testumgebung für Anwendungen erstellen oder Features und Funktionen von Office 365 demonstrieren. Es gibt zwei Versionen:
  
- Die einfache Office 365-Entwicklungs-/Testumgebung besteht aus einem Office 365-Testabonnement, auf das Sie von Ihrem Hauptcomputer aus zugreifen.
    
    Verwenden Sie diese Umgebung, wenn Sie schnell ein Feature demonstrieren möchten. Führen Sie für die einfache Office 365-Entwicklungs-/Testumgebungen nur die Schritte in Phase 2 und 3 dieses Artikels durch.
    
- Die simulierte Office 365-Entwicklungs-/Testunternehmensumgebung besteht aus einem Office 365-Testabonnement und einem vereinfachtem Organisationsintranet mit Internetverbindung, das in Microsoft Azure-Infrastrukturdiensten gehostet wird. Sie können diese Konfiguration vollständig in der Microsoft-Cloud erstellen.
    
    Verwenden Sie diese Umgebung, wenn Sie ein Feature oder eine App in einer Umgebung demonstrieren möchten,die einem gewöhnlichen Organisationsnetzwerk mit Internetverbindung ähnelt, oder für Features, für die diese Art von Umgebung erforderlich ist. Führen Sie für die simulierte Office 365-Entwicklungs-/Testunternehmensumgebung die Schritte in Phasen 1, 2 und 3 dieses Artikels durch.
    
> [!NOTE]
> Sie können diesen Artikel auch ausdrucken, um die bestimmten Werte zu notieren, die Sie für diese Umgebung in den kommenden 30 Tage des Office 365-Testabonnements benötigen. Sie können das Testabonnement einfach um weitere 30 Tage verlängern. Für eine dauerhafte Entwicklungs-/Testumgebung erstellen Sie ein neues bezahltes Abonnement mit einer kleinen Anzahl von Lizenzen. 
  
![Testumgebungsanleitungen in der Microsoft Cloud](media/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
> [!TIP]
> Klicken Sie [hier](http://aka.ms/catlgstack), um eine visuelle Darstellung aller Artikel im Stapel der Testumgebungsanleitungen in der Microsoft Cloud zu erhalten.
  
## <a name="phase-1-create-the-base-configuration-in-azure"></a>Phase 1: Erstellen der Basiskonfiguration in Azure

Befolgen Sie die Anweisungen unter [Basiskonfiguration der Entwicklungs-/Testumgebung](base-configuration-dev-test-environment.md)
  
Sie benötigen ein Azure-Abonnement. Sie können die [kostenlose Testversion von Azure](https://azure.microsoft.com/pricing/free-trial/) für diese Konfiguration verwenden. Wenn Sie über ein MSDN- oder Visual Studio-Abonnement verfügen, lesen Sie die Informationen unter [Monatliche Azure-Gutschrift für Visual Studio-Abonnenten](https://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/).
  
Nachfolgend sehen Sie die daraus resultierende Konfiguration.
  
![Die Basiskonfiguration der Entwicklungs-/ Testumgebung in Azure](media/25a010a6-c870-4690-b8f3-84421f8bc5c7.png)


  
Diese Konfiguration besteht aus virtuellen DC1-, APP1- und CLIENT1-Computern in einem Subnetz eines virtuellen Azure-Netzwerks.
  
## <a name="phase-2-create-an-office-365-trial-subscription"></a>Phase 2: Erstellen eines Office 365-Testabonnements

Für das Office 365 E5-Testabonnement benötigen Sie zunächst einen fiktiven Unternehmensnamen und ein neues Microsoft-Konto.
  
1. Es wird empfohlen, eine Variante von „Contoso“ als Unternehmensnamen zu verwenden. Dies ist ein fiktives Unternehmen, das von Microsoft in Beispielen verwendet wird. Notieren Sie hier Ihren fiktiven Unternehmensnamen: ![](./media/Common-Images/TableLine.png).
    
2. Wenn Sie sich für ein neues Microsoft-Konto registrieren möchten, wechseln Sie zu [https://outlook.com](https://outlook.com), und erstellen Sie ein Konto mit neuem E-Mail-Konto und neuer E-Mail-Adresse. Dieses Konto wird für die Registrierung für Office 365 verwendet.
    
  - Notieren Sie hier den Vor- und Nachnamen des Kontos: ![](./media/Common-Images/TableLine.png)
    
  - Notieren Sie hier die neue E-Mail-Kontoadresse: ![](./media/Common-Images/TableLine.png)@outlook.com
    
### <a name="sign-up-for-an-office-365-e5-trial-subscription"></a>Registrieren für ein Office 365 E5-Testabonnement

1. Öffnen Sie für die einfache Office 365-Entwicklungs-/Testumgebung den Internetbrowser auf Ihrem Computer, und gehen Sie zu [https://aka.ms/e5trial](https://aka.ms/e5trial).  
    
    Stellen Sie für die simulierte Office 365-Entwicklungs-/Testumgebung über das Azure-Portal eine Verbindung mit CLIENT1 mit dem CORP\User1-Konto her.

    Führen Sie vom Startbildschirm Microsoft Edge aus, und wechseln Sie zu [https://aka.ms/e5trial](https://aka.ms/e5trial).
    
2. Geben Sie auf der Seite **Willkommen, Grundlegendes zu Ihrer Person** die folgenden Informationen an:
    
  - Tatsächlicher Standort
    
  - Vor- und Nachname des neuen Microsoft-Kontos
    
  - Die neue E-Mail-Kontoadresse
    
  - Telefonnummer geschäftlich
    
  - Fiktiver Unternehmensname
    
  - Unternehmensgröße zwischen 250-999 Mitarbeitern
    
3. Klicken Sie auf **Nur noch ein Schritt**.
    
4. Geben Sie auf der Seite **Benutzer-ID erstellen** einen Benutzernamen auf Grundlage der neuen E-Mail-Adresse, den fiktiven Unternehmensnamen nach dem @-Zeichen (entfernen Sie alle Leerzeichen im Namen) und dann (zweimal) ein Kennwort für dieses neue Office 365-Konto ein. 
    
    Notieren Sie das verwendete Kennwort, und bewahren Sie es an einem sicheren Ort auf.
    
    Notieren Sie hier den fiktiven Unternehmensnamen, der im Folgenden **Organisationsname** genannt wird: ![](./media/Common-Images/TableLine.png)
    
5. Klicken Sie auf **Mein Konto erstellen**.
    
6. Geben Sie auf der Seite **Ich bin kein Roboter** die Rufnummer eines SMS-fähigen Mobiltelefons, und klicken Sie dann auf **SMS an mich**.
    
7. Geben Sie den Verifizierungscode ein, den Sie per SMS erhalten haben, und klicken Sie dann auf **Weiter**.
    
8. Notieren Sie hier die URL der Anmeldeseite (auswählen und kopieren): ![](./media/Common-Images/TableLine.png)
    
9. Notieren Sie hier die Benutzer-ID (auswählen und kopieren): ![](./media/Common-Images/TableLine.png).onmicrosoft.com
    
    Dieser Wert wird **Name des globalen Office 365-Administrators** genannt.
    
10. Wenn **Alle Schritte wurden abgeschlossen.** angezeigt wird, klicken Sie darauf.
    
11. Warten Sie auf der nächsten Seite, bis die Einrichtung von Office 365 abgeschlossen ist und alle Kacheln verfügbar sind.
    
Nun sollte die Hauptseite des Office 365-Portals angezeigt werden, über die Sie auf Office Online-Dienste und das Microsoft 365 Admin Center zugreifen können.
  
So sieht die resultierende Konfiguration für die simulierte Office 365-Entwicklungs-/Testunternehmensumgebung aus.
  
![Die Office 365-Entwicklungs-/Testumgebung](media/48fb91aa-09b0-4020-a496-a8253920c45d.png)
  
Diese Konfiguration besteht aus:  
  
- Den virtuellen DC1-, APP1- und CLIENT1-Computern in einem Subnetz eines virtuellen Azure-Netzwerks
    
- Einem Office 365 E5-Testabonnement
    
## <a name="phase-3-configure-your-office-365-trial-subscription"></a>Phase 3: Konfigurieren des Office 365-Testabonnements

In dieser Phase konfigurieren Sie Ihr Office 365-Abonnement mit weiteren Benutzern und weisen diesen Office 365 E5-Lizenzen zu.
  
Befolgen Sie die Anweisungen unter [Verbinden mit Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell#connect-with-the-azure-active-directory-powershell-for-graph-module), um Ihr Office 365-Abonnement von folgenden Quellen aus mit dem Azure Active Directory PowerShell-Modul für Graph zu verbinden:
  
- Ihrem Computer aus (für die einfache Office 365-Entwicklungs-/Testunternehmensumgebung).
    
- Dem virtuellen Computer CLIENT1 aus (für die simulierte Office 365-Entwicklungs-/Testumgebung).
    
 Geben Sie in das Dialogfeld „Windows PowerShell Credential Request“ den Namen des globalen Office 365-Administrators (z. B. „jdoe@contosotoycompany.onmicrosoft.com“) und sein Kennwort ein.
  
Geben Sie den Namen Ihrer Organisation (z. B. „contosotoycompany“), den zweistelligen Ländercode für Ihren Standort und ein gemeinsames Kontokennwort ein, und führen Sie dann die folgenden Befehle von der PowerShell-Eingabeaufforderung aus:

```
$orgName="<organization name>"
$loc="<two-character country code, such as US>"
$commonPW="<common user account password>"
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password=$commonPW

$userUPN= "user2@" + $orgName + ".onmicrosoft.com"
New-AzureADUser -DisplayName "User 2" -GivenName User -SurName 2 -UserPrincipalName $userUPN -UsageLocation $loc -AccountEnabled $true -PasswordProfile $PasswordProfile -MailNickName "user2"
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value "ENTERPRISEPREMIUM" -EQ).SkuID
$LicensesToAssign = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$LicensesToAssign.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $LicensesToAssign

$userUPN= "user3@" + $orgName + ".onmicrosoft.com"
New-AzureADUser -DisplayName "User 3" -GivenName User -SurName 3 -UserPrincipalName $userUPN -UsageLocation $loc -AccountEnabled $true -PasswordProfile $PasswordProfile -MailNickName "user3"
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value "ENTERPRISEPREMIUM" -EQ).SkuID
$LicensesToAssign = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$LicensesToAssign.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $LicensesToAssign

$userUPN= "user4@" + $orgName + ".onmicrosoft.com"
New-AzureADUser -DisplayName "User 4" -GivenName User -SurName 4 -UserPrincipalName $userUPN -UsageLocation $loc -AccountEnabled $true -PasswordProfile $PasswordProfile -MailNickName "user4"
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value "ENTERPRISEPREMIUM" -EQ).SkuID
$LicensesToAssign = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$LicensesToAssign.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $LicensesToAssign
```

<!--
> [!TIP]
> Click [here](https://gallery.technet.microsoft.com/PowerShell-commands-for-fe3d7a34) to get a text file that has all the PowerShell commands in this article.
-->

  
## <a name="phase-4-create-three-new-sharepoint-online-team-sites-optional"></a>Phase 4: Erstellen von drei neuen SharePoint Online-Teamwebsites (optional)

In dieser Phase konfigurieren Sie eine Reihe von SharePoint Online-Teamwebsites.
  
1. Installieren Sie die [SharePoint Online-Verwaltungsshell](https://go.microsoft.com/fwlink/p/?LinkId=255251) (die x64-Version).
    
2. Klicken Sie auf **Start**, geben Sie **sharepoint** ein, und klicken Sie dann auf **SharePoint Online-Verwaltungsshell**.
    
3. Geben Sie den Namen Ihrer Organisation ein (Beispiel: contosotoycompany), und führen Sie dann über die Eingabeaufforderung der SharePoint Online-Verwaltungsshell die folgenden Befehle aus, um eine Verbindung mit dem SharePoint Online-Dienst herzustellen.
```
$orgName="<organization name>"
$spURL="https://" + $orgName + "-admin.sharepoint.com"
Connect-SPOService -Url $spURL
```

4. Geben Sie in das Dialogfeld **Microsoft SharePoint Online Management Shell** den Namen des globalen Office 365-Administrators (z. B. „jdoe@contosotoycompany.onmicrosoft.com“) und sein Kennwort ein, und klicken Sie auf **Anmelden**.
    
5. Geben Sie zum Erstellen von drei neuen Teamwebsites (Sales, Produktion und Support) den Namen des globalen Office 365-Administrators ein, und führen dann über die Eingabeaufforderung der SharePoint Online-Verwaltungsshell die folgenden Befehle aus:
    
  ```
  $owner = "<global administrator account name>"
$siteURL = "https://" + $orgName + ".sharepoint.com/sites/sales"
New-SPOSite -Url $siteURL -Owner $owner -StorageQuota 1000 -Title "Sales site collection" -Template "STS#0"
$siteURL = "https://" + $orgName + ".sharepoint.com/sites/production"
New-SPOSite -Url $siteURL -Owner $owner -StorageQuota 1000 -Title "Production site collection" -Template "STS#0"
$siteURL = "https://" + $orgName + ".sharepoint.com/sites/support"
New-SPOSite -Url $siteURL -Owner $owner -StorageQuota 1000 -Title "Support site collection" -Template "STS#0"
  ```

6. Führen Sie diesen Befehl aus, um die URLs der neuen Websites abzurufen:
    
  ```
  Get-SPOSite | Where URL -like "*/sites/*" | Sort URL | Select URL
  ```

7. Geben Sie im Internet Explorer die URL der Website „Produktion“ ein, um die standardmäßige SharePoint Online-Teamwebsite für die Abteilung „Produktion“ anzuzeigen.
    
## <a name="record-values-for-future-reference"></a>Notieren von Werten für zukünftige Verwendung

Notieren Sie die folgenden Werte für die Arbeit mit oder Bereitstellen von zusätzlichen Leitfäden für Test Lab in dieser Testumgebung:
  
- Name des globalen Office 365-Administrators: ![](./media/Common-Images/TableLine.png).onmicrosoft.com (aus Schritt 9 von Phase 2)
    
    Notieren Sie auch das Kennwort für dieses Konto, und bewahren Sie es an einem sicheren Ort auf.
    
- Organisationsname für das Testabonnement: ![](./media/Common-Images/TableLine.png) (aus Schritt 4 von Phase 2)
    
- Führen Sie über die „Windows Azure Active Directory-Modul für Windows PowerShell“-Eingabeaufforderung den folgenden Befehl aus, um die Konten für Benutzer 2, Benutzer 3, Benutzer 4 und Benutzer 5 anzuzeigen:
    
  ```
  Get-AzureADUser | Sort UserPrincipalName | Select UserPrincipalName
  ```

    Notieren Sie hier die Kontonamen:
    
  - Kontoname für Benutzer 2: benutzer2@![](./media/Common-Images/TableLine.png).onmicrosoft.com
    
  - Kontoname für Benutzer 3: benutzer3@![](./media/Common-Images/TableLine.png).onmicrosoft.com
    
  - Kontoname für Benutzer 4: benutzer4@![](./media/Common-Images/TableLine.png).onmicrosoft.com
    
  - Kontoname für Benutzer 5: benutzer5@![](./media/Common-Images/TableLine.png).onmicrosoft.com
    
    Notieren Sie auch die Kennwörter für diese Konten, und bewahren Sie sie an einem sicheren Ort auf.
    
- (Optional) Führen Sie über die Eingabeaufforderung der SharePoint Online-Verwaltungsshell den folgenden Befehl aus, um die URLs für die Teamwebsites „Sales“, „Produktion“ und „Support“ anzuzeigen:
    
  ```
  Get-SPOSite | Where URL -like "*/sites/*" | Sort URL | Select URL
  ```

  - URL der Website „Produktion“: https://![](./media/Common-Images/TableLine.png).sharepoint.com/sites/produktion
    
  - URL der Website „Sales“: https://![](./media/Common-Images/TableLine.png).sharepoint.com/sites/sales
    
  - URL der Website „Support“: https://![](./media/Common-Images/TableLine.png).sharepoint.com/sites/support
    
## <a name="next-steps"></a>Nächste Schritte

Verwenden Sie die folgenden zusätzlichen Artikel in Ihrer Office 365-Entwicklungs-/Testumgebung:
  
- [Verzeichnissynchronisierung für die Office 365-Entwicklungs-/Testumgebung](dirsync-for-your-office-365-dev-test-environment.md)
    
- [Multi-Factor Authentication für die Office 365-Entwicklungs-/Testumgebung](multi-factor-authentication-for-your-office-365-dev-test-environment.md)
    
- [Verbundidentität für Ihre Office 365-Entwicklungs-/Testumgebung](federated-identity-for-your-office-365-dev-test-environment.md)
    
- [Cloud App Security für Ihre Office 365-Entwicklungs-/Testumgebung](cloud-app-security-for-your-office-365-dev-test-environment.md)
    
- [Advanced Threat Protection für die Office 365-Entwicklungs-/Testumgebung](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
    
- [Advanced eDiscovery für die Office 365-Entwicklungs-/Testumgebung](advanced-ediscovery-for-your-office-365-dev-test-environment.md)
    
- [Schutz vertraulicher Dateien in Office 365-Entwicklungs-/-Testumgebungen](sensitive-file-protection-in-the-office-365-dev-test-environment.md)
    
- [Isolierte SharePoint Online-Teamwebsite in Ihrer Office 365-Entwicklungs-/Testumgebung](isolated-sharepoint-online-team-site-dev-test-environment.md)
    
- [Datenklassifizierung und -kennzeichnung in Office 365-Entwicklungs-/-Testumgebungen](data-classification-and-labeling-in-the-office-365-dev-test-environment.md)
    
Erweitern Sie Ihre Office 365-Entwicklungs-/Testumgebung um zusätzliche Microsoft-Cloudangebote:
  
- [Die Microsoft 365 Enterprise-Entwicklungs-/Testumgebung](the-microsoft-365-enterprise-dev-test-environment.md)
    
- [Office 365- und Dynamics 365-Entwicklungs-/Testumgebung](office-365-and-dynamics-365-dev-test-environment.md)
    
## <a name="see-also"></a>Siehe auch

- [Testumgebungsanleitungen (TLGs) zur Cloudakzeptanz](cloud-adoption-test-lab-guides-tlgs.md)
  
- [Office 365- und Dynamics 365-Entwicklungs-/Testumgebung](office-365-and-dynamics-365-dev-test-environment.md)
  
- [Cloudakzeptanz und Hybridlösungen](cloud-adoption-and-hybrid-solutions.md)


