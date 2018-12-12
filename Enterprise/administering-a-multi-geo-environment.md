---
title: Verwalten einer Multi-Geo-Umgebung
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: Dieser Artikel enthält Informationen über die Verwaltung von SharePoint- und OneDrive-Diensten in einer Multi-Geo-Umgebung.
ms.openlocfilehash: 823b3a4c1d063a4d398b7f734c2171e856ee1244
ms.sourcegitcommit: 4a1d6c43da44b559136f2bf422a531bea5f48dbb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/09/2018
ms.locfileid: "27210123"
---
# <a name="administering-a-multi-geo-environment"></a>Verwalten einer Multi-Geo-Umgebung

In diesem Artikel wird die Funktionsweise von OneDrive- und SharePoint-Diensten in einer Multi-Geo-Umgebung erläutert.

#### <a name="onedrive-administrator-experience"></a>OneDrive-Administratorumgebung

Das [OneDrive Admin Center](https://admin.onedrive.com) verfügt im linken Navigationsbereich über die Registerkarte **Geografische Standorte**, die eine Karte mit geografischen Standorten enthält, auf der Sie Ihre geografischen Standorte anzeigen und verwalten können. Verwenden Sie diese Seite zum Hinzufügen oder Löschen von geografischen Standorten für Ihren Mandanten.

#### <a name="taxonomy"></a>Taxonomie

Wir unterstützen eine einheitliche [Taxonomie](https://support.office.com/article/A180FA28-6405-4679-9EC3-81D2028C4EFC) für verwaltete Unternehmensdaten für alle geografischen Standorte. Die Gestaltungsvorlage wird an einem zentralen Ort für das Unternehmen gehostet. Es wird empfohlen, die globale Taxonomie von einem zentralen Ort aus zu verwalten und nur der Taxonomie der Satellitenstandorte standortspezifische Ausdrücke hinzuzufügen. Globale Taxonomieausdrücke werden mit den Satellitenstandorten synchronisiert.

#### <a name="sharing"></a>Freigabe

Administratoren können die Freigabe von Richtlinien für jeden Standort einrichten und verwalten. OneDrive-Websites an den einzelnen geografischen Standorten berücksichtigen nur die entsprechenden Freigabeeinstellungen des geografischen Standorts. (Sie können z. B. [externe Freigabe](https://support.office.com/article/C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85) für Ihren zentralen Standort und nicht für den Satellitenstandort zulassen, und umgekehrt.) Beachten Sie, dass die Freigabeeinstellungen keine Konfiguration von Freigabeeinschränkungen zwischen den geografischen Standorten zulassen.

Für Multi-Geo in OneDrive müssen Sie Ihre Freigabeeinstellungen für jeden geografischen Standort verwalten, da diese nicht innerhalb des Mandanten synchronisiert werden. Die Einstellungen für die Freigabe können auf der Seite für die [Freigabeeinstellungen im OneDrive Admin Center](https://admin.onedrive.com/?v=SharingSettings) verwalten. Externe Freigabe ist standardmäßig für alle Benutzer an den einzelnen Satellitenstandorten aktiviert.

#### <a name="user-profile-application"></a>Benutzerprofilanwendung

Es gibt eine [Benutzerprofilanwendung](https://support.office.com/article/494bec9c-6654-41f0-920f-f7f937ea9723) an jedem geografischen Standort. Profilinformationen der Benutzer werden an dem jeweiligen geografischen Standort gehostet und stehen dem Administrator für diesen geografischen Standort zur Verfügung.

Wenn Sie über benutzerdefinierte Profileigenschaften verfügen, wird empfohlen, dasselbe Profilschema für alle geografischen Standorte zu verwenden und die benutzerdefinierten Profileigenschaften entweder für alle oder bestimmte geografischen Standorte aufzufüllen. Eine Anleitung dazu, wie Sie Benutzerprofildaten programmgesteuert auffüllen, finden Sie unter [API für die Massenaktualisierung von Benutzerprofilen](https://docs.microsoft.com/de-DE/sharepoint/dev/solution-guidance/bulk-user-profile-update-api-for-sharepoint-online).

#### <a name="bcs-secure-store-apps"></a>BCS, Secure Store, Apps

BCS, Secure Store und Apps verfügen über separate Instanzen. Daher sollte der SharePoint Online-Administrator diese Dienste von dem jeweiligen Satellitenstandort aus separat verwalten und konfigurieren.

#### <a name="security-and-compliance-admin-center"></a>Security & Compliance Center

Es gibt ein zentrales Compliance Center für den Multi-Geo-Mandanten: [Office 365 Security & Compliance Center](https://protection.office.com/?rfr=AdminCenter\#/homepage).

#### <a name="information-protection-ip-data-loss-prevention-dlp-policy"></a>DLP-Richtlinie in Information Protection

Sie können Ihre DLP-Richtlinien in Information Protection für OneDrive for Business im Security & Compliance Center festlegen und den Geltungsbereich je nach Bedarf auf den gesamten Mandanten oder einzelne Benutzer festlegen. Beispiel: Wenn Sie eine Richtlinie für einen OneDrive-Benutzer an einem Satellitenstandort auswählen möchten, wenden Sie die Richtlinie für eine bestimmte OneDrive-Umgebung an, und geben Sie die URL der OneDrive-Benutzerumgebung ein. Eine allgemeine Anleitung für das Erstellen von DLP-Richtlinien finden Sie unter [Übersicht über die Richtlinien zur Verhinderung von Datenverlust](https://support.office.com/article/1966b2a7-d1e2-4d92-ab61-42efbb137f5e).

Die DLP-Richtlinien werden automatisch basierend auf ihrer Anwendbarkeit auf den jeweiligen geografischen Standort synchronisiert.

Die Implementierung von IP- (Information Protection) und DLP-Richtlinien für alle Benutzer an einem geografischen Standort steht nicht als Option auf der Benutzeroberfläche zur Verfügung. Sie müssen stattdessen die entsprechenden OneDrive-Konten für die Richtlinie auswählen oder die Richtlinie global auf alle OneDrive-Konten anwenden.

#### <a name="ediscovery"></a>eDiscovery 

Standardmäßig kann ein eDiscovery-Manager oder Administrator eines Multi-Geo-Mandaten eDiscovery nur an der zentralen Stelle dieses Mandanten durchführen. Um eDiscovery für Satellitenstandorte durchführen zu können, steht ein neuer Parameter des Compliancesicherheitsfilters namens „Region“ über PowerShell zur Verfügung.

Der globale Office 365-Administrator muss eDiscovery-Managerberechtigungen zuweisen, damit andere Personen eDiscovery durchführen können, und einen „Region“-Parameter im entsprechenden Compliancesicherheitsfilter zuweisen, um die Region zum Durchführen von eDiscovery als Satellitenstandort festzulegen. Andernfalls wird eDiscovery nicht für den Satellitenstandort durchgeführt werden.

Wenn die eDiscovery-Manager- oder Administratorrolle für einen bestimmten Satellitenstandort festgelegt ist, kann der eDiscovery-Manager oder Administrator nur eDiscovery-Suchaktionen für die SharePoint-Websites und OneDrive-Websites an diesem Satellitenstandort durchführen. Wenn ein eDiscovery-Manager oder Administrator versucht, SharePoint- oder OneDrive-Websites außerhalb des angegebenen Satellitenstandorts zu durchsuchen, werden keine Ergebnisse zurückgegeben. Wenn der eDiscovery-Manager oder Administrator für einen Satellitenstandort einen Export auslöst, werden Daten in der Azure-Instanz dieses Bereichs exportiert. So können Organisationen Compliance gewährleisten, indem nicht zugelassen wird, dass Inhalte über den kontrollierten Rahmen hinaus exportiert werden.

> [!NOTE]
> Wenn ein eDiscovery-Manager mehrere SharePoint-Satellitenstandorte durchsuchen möchte, muss ein anderes Benutzerkonto für den eDiscovery-Manager erstellt werden, das den alternativen Satellitenstandort angibt, in dem sich OneDrive- oder SharePoint-Websites befinden.

<table>
<thead>
<tr class="header">
<th align="left"><strong>Von Multi-Geo unterstützte geografischen Standorte</strong></th>
<th align="left"><strong>eDiscovery für exportierte SharePoint-Daten erfolgt an diesem Azure Blob-Datenspeicherort...</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><strong>APC</strong></td>
<td align="left">Rechenzentren in Südost- oder Ostasien</td>
</tr>
<tr class="odd">
<td align="left"><strong>AUS</strong></td>
<td align="left">Rechenzentren in Südost- oder Ostasien</td>
</tr>
<tr class="even">
<td align="left"><strong>CAN</strong></td>
<td align="left">Rechenzentren in den USA</td>
</tr>
<tr class="even">
<td align="left"><strong>EUR</strong></td>
<td align="left">Rechenzentren in Europa</td>
</tr>
<tr class="odd">
<td align="left"><strong>FRA</strong></td>
<td align="left">Rechenzentren in Europa</td>
</tr>
<tr class="odd">
<td align="left"><strong>GBR</strong></td>
<td align="left">Rechenzentren in Europa</td>
</tr>
<tr class="even">
<td align="left"><strong>IND</strong></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><strong>KOR</strong></td>
<td align="left">Rechenzentren in Südost- oder Ostasien</td>
</tr>
<tr class="even">
<td align="left"><strong>JPN </strong></td>
<td align="left">Rechenzentren in Südost- oder Ostasien</td>
</tr>
<tr class="odd">
<td align="left"><strong>NAM</strong></td>
<td align="left">Rechenzentren in den USA</td>
</tr>
</tbody>
</table>

So legen Sie den Compliancesicherheitsfilter für eine Region fest

1.  Öffnen Sie Windows PowerShell.

2.  Geben Sie Folgendes ein:  
    $s = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri <https://ps.compliance.protection.outlook.com/powershell-liveid> -Credential $cred -Authentication Basic -AllowRedirection -SessionOption (New-PSSessionOption -SkipCACheck -SkipCNCheck -SkipRevocationCheck)

    $a = Import-PSSession $s -AllowClobber  

3.  **New-ComplianceSecurityFilter** **-Action** ALL **-FilterName** EnterTheNameYouWantToAssign **-Region** EnterTheRegionParameter **-Users** EnterTheUserPrincipalName

    Beispiel: **New-ComplianceSecurityFilter -Action** ALL **-FilterName** NAMEDISCOVERYMANAGERS **-Region** NAM **-Users** adwood@contosodemosx.onmicrosoft.com

Informationen zu weiteren Parametern und zur Syntax finden Sie im Artikel [New-ComplianceSecurityFilter](https://technet.microsoft.com/library/mt210915(v=exchg.160).aspx).

#### <a name="audit-log-search"></a>Überwachungsprotokollsuche

Ein einheitliches [Überwachungsprotokoll](https://support.office.com/article/0d4d0f35-390b-4518-800e-0c7ec95e946c) für alle Ihre Satellitenstandorte ist auf der Seite für die Office 365-Überwachungsprotokollsuche verfügbar. Sie können alle Überwachungsprotokolleinträge für alle geografischen Standorte anzeigen. Beispiel: Sie können Benutzeraktivitäten für die geografischen Standorte NAM und EUR in einer Organisationsansicht anzeigen und dann vorhandene Filter anwenden, um bestimmte Benutzeraktivitäten anzuzeigen.
