---
title: Verwalten einer Umgebung mit mehreren geografisch
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: Strat_SP_gtc
localization_priority: Normal
description: Informationen Sie zum Verwalten von SharePoint und OneDrive-Dienste in einer Umgebung mit mehreren geografisch.
ms.openlocfilehash: 5d423fedc25b6e58ee84a51b01eb3858e6f198bb
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="administering-a-multi-geo-environment"></a>Verwalten einer Umgebung mit mehreren geografisch

Es folgt eine Aufstellung der Funktionsweise von OneDrive und SharePoint-Dienste in einer Umgebung mit mehreren geografisch.

#### <a name="onedrive-administrator-experience"></a>OneDrive Administratorbenutzeroberfläche

Der [OneDrive-Verwaltungskonsole](https://admin.onedrive.com) hat eine Registerkarte **Geo Speicherorte** im linken Navigationsbereich, welche Features, in dem Sie anzeigen und Verwalten von Speicherorten für Ihre Geo können ein Geo-Standorte zuordnen. Verwenden Sie diese Seite zum Hinzufügen oder Löschen von Geo Speicherorte für Ihre Mandanten.

#### <a name="taxonomy"></a>Taxonomie

Wir unterstützen eine einheitliche [Taxonomie](https://support.office.com/article/A180FA28-6405-4679-9EC3-81D2028C4EFC) für verwaltete Metadaten von Unternehmen über Geo-Standorte mit das Master-Shape in der zentralen Speicherort für Ihr Unternehmen gehostet wird. Es wird empfohlen, dass Sie der globalen Taxonomie vom zentralen Speicherort verwalten und nur Satelliten Geo Speicherort Taxonomie standortspezifische Begriffe hinzugefügt. Globale Taxonomie Begriffe werden an den Satelliten Geo Orten synchronisiert.

#### <a name="sharing"></a>Freigabe

Administratoren können festlegen und Verwalten von Freigaberichtlinien für jede ihrer Standorte. Die Websites OneDrive an jedem Standort Geo berücksichtigt nur die entsprechenden Geo bestimmte sharing Einstellungen. Beispielsweise können Sie [externe Freigabe](https://support.office.com/article/C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85) für den zentralen Standort, jedoch nicht für Ihre Satelliten Speicherort umgekehrt gestatten. OneDrive Multi-Geo müssen Sie Ihre Freigabe Einstellungen an jedem Standort Geo verwalten, wie diese über den Mandanten nicht synchronisiert sind.

Verwalten von sharing Besuch der Seite [freigabeeinstellungen OneDrive-Verwaltungskonsole](https://admin.onedrive.com/?v=SharingSettings) . Externe Freigabe wird mit jeder an jedem Satellitenstandort standardmäßig aktiviert.

#### <a name="user-profile-application"></a>Benutzer Benutzerprofildienst-Anwendung

An jedem Standort Geo ist ein [Benutzer Benutzerprofildienst-Anwendung](https://support.office.com/article/494bec9c-6654-41f0-920f-f7f937ea9723) . Profilinformationen des Benutzers gehostet wird in ihrem Standort Geo und an den Administrator für diesen Speicherort Geo verfügbar.

Wenn Sie benutzerdefinierte Eigenschaften, und es wird empfohlen, die Sie verwenden das gleiche Profilschema verschiedenen Standorten und füllen Sie Ihre benutzerdefinierte Profileigenschaften entweder an allen Speicherorten von Geo oder bei Bedarf.

#### <a name="bcs-secure-store-apps"></a>BCS, Secure Store-Apps

BCS, einmaliges Anmelden und Apps verfügen über separate Geo-Instanzen, daher der SharePoint Online-Administrator verwalten und konfigurieren Sie diese Dienste von jeder Geo-Instanz, in dem sie vorhanden sein sollen, sollten.

#### <a name="security-and-compliance-admin-center"></a>Sicherheit und Compliance-Verwaltungskonsole

Es ist eine zentrale Compliance Center für den Mandanten mit mehreren geografisch: [Office 365-Sicherheit und Compliance Center](https://protection.office.com/?rfr=AdminCenter\#/homepage).

#### <a name="information-protection-ip-data-loss-prevention-dlp-policy"></a>Schutz (IP) Data Loss Prevention (DLP) Informationsrichtlinien

Sie können Ihre IP DLP Richtlinien für OneDrive for Business in der Mitte Sicherheit und Richtlinientreue festlegen Bereichsdefinierung Richtlinien Bedarf für den gesamten Mandanten oder für Benutzer. Beispiel: Wenn Sie eine Richtlinie für einen Benutzer OneDrive an einem Speicherort Satelliten auswählen möchten, wenden Sie die Richtlinie zu einem bestimmten OneDrive und geben den Benutzer auswählen der OneDrive-Url. Allgemeine Richtlinien bei der Erstellung von DLP-Richtlinien finden Sie unter [Übersicht über Richtlinien zur Verhinderung von Datenverlust](https://support.office.com/article/1966b2a7-d1e2-4d92-ab61-42efbb137f5e) .

Die DLP-Richtlinien werden automatisch basierend auf ihren Anwendungsbereich an jedem Standort Geo synchronisiert.

Implementieren von Information Protection and Data Loss Prevention-Richtlinien für alle Benutzer an einem Speicherort Geo ist keine Option in der Benutzeroberfläche verfügbar, stattdessen müssen Sie wählen Sie die entsprechenden OneDrive-Konten für die Richtlinie oder gelten die Richtlinie global für alle OneDrive-Konten.

#### <a name="ediscovery"></a>eDiscovery 

Standardmäßig wird eine eDiscovery-Manager oder Administrator der einen Mandanten Multi-Geo eDiscovery nur in der zentralen Speicherort, Mandanten durchführen können. Um die Möglichkeit zum Durchführen von eDiscovery für Satelliten Speicherorte zu unterstützen, ist ein neuer Sicherheitsfilter Compliance-Parameter "Region" aufgerufen über PowerShell verfügbar.

Office 365 globale Administrator muss eDiscovery-Manager-Berechtigungen zu anderen Benutzern gestatten, Ausführen von eDiscovery, und weisen Sie einen Parameter "Region" in ihren entsprechenden Compliance Sicherheitsfilter an die Region für die Durchführung von eDiscovery als Satelliten zuweisen Speicherort, andernfalls keine eDiscovery für den Speicherort der Satelliten durchgeführt werden soll.

Wenn die eDiscovery-Manager oder Administrator-Rolle für einen bestimmten Geo-Speicherort festgelegt ist, wird die eDiscovery-Manager oder Administrator nur eDiscovery-Suche Aktionen für die SharePoint-Websites und OneDrive Standorte in diesen Geo-Speicherort ausführen können. Wenn ein eDiscovery-Manager oder Administrator versucht, SharePoint oder OneDrive Websites außerhalb des angegebenen Bereichs suchen, werden keine Ergebnisse zurückgegeben. Wenn nach Exportieren von eDiscovery-Manager oder Administrator für einen Bereich ausgelöst wird, werden Daten an die Azure Instanz dieser Region exportiert. Dadurch Organisationen in Compliance bleiben, indem nicht zulassen Inhalte über gesteuerte Grenzen hinweg exportiert werden sollen.

> [!NOTE]
> Wenn es für ein eDiscovery-Suche über mehrere SharePoint-Regionen Manager erforderlich ist, müssen eines anderen Benutzerkontos für die eDiscovery-Manager erstellt werden, der die alternative Region angibt, wo sich die OneDrive oder SharePoint-Websites befinden.

<table>
<thead>
<tr class="header">
<th align="left"><strong>Multi-Geo unterstützt Geo Speicherorte</strong></th>
<th align="left"><strong>eDiscovery für SharePoint exportiert Daten werden in diesem Speicherort der Azure Blob-Daten...</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><strong>NAME</strong></td>
<td align="left">US-Rechenzentren</td>
</tr>
<tr class="even">
<td align="left"><strong>EUR</strong></td>
<td align="left">Europa Rechenzentren</td>
</tr>
<tr class="odd">
<td align="left"><strong>APC</strong></td>
<td align="left">Südost oder East Asien-Rechenzentren</td>
</tr>
<tr class="even">
<td align="left"><strong>KÖNNEN</strong></td>
<td align="left">US-Rechenzentren</td>
</tr>
<tr class="odd">
<td align="left"><strong>AUS</strong></td>
<td align="left">Südost oder East Asien-Rechenzentren</td>
</tr>
<tr class="even">
<td align="left"><strong>KOREANISCHE</strong></td>
<td align="left">Mandanten Standardspeicherort Daten</td>
</tr>
<tr class="odd">
<td align="left"><strong>GBR</strong></td>
<td align="left">Europa Rechenzentren</td>
</tr>
<tr class="even">
<td align="left"><strong>JAPANISCHE</strong></td>
<td align="left">Südost oder East Asien-Rechenzentren</td>
</tr>
</tbody>
</table>

Die Einhaltung von Bestimmungen Sicherheitsfilter für einen Bereich festlegen:

1.  Öffnen von Windows PowerShell

2.  die EINGABETASTE  
    $s = New-PSSession - ConfigurationName Microsoft.Exchange - ConnectionUri <https://ps.compliance.protection.outlook.com/powershell-liveid> -Anmeldeinformationen $cred-Authentifizierung grundlegende - AllowRedirection - SessionOption (New-PSSessionOption - SkipCACheck - SkipCNCheck - SkipRevocationCheck)

    $eine = $s Import-PSSession - AllowClobber  

3.  **Neue ComplianceSecurityFilter** **-Aktion** ALLE **FilterName -** EnterTheNameYouWantToAssign **-Region** EnterTheRegionParameter **-Benutzer** EnterTheUserPrincipalName

    Beispiel: **neue ComplianceSecurityFilter-Aktion** alle **FilterName -** NAMEDISCOVERYMANAGERS **-Region** Name **-Benutzer** adwood@contosodemosx.onmicrosoft.com

Finden Sie im Artikel [Neu ComplianceSecurityFilter](https://technet.microsoft.com/library/mt210915(v=exchg.160).aspx) für zusätzliche Parameter und syntax

#### <a name="audit-log-search"></a>Überwachungsprotokollsuche

Eine einheitliche [Überwachungsprotokoll](https://support.office.com/article/0d4d0f35-390b-4518-800e-0c7ec95e946c) für alle Standorte Ihrer Geo ist über die Office 365 Audit Log Suchseite verfügbar. Sehen Sie alle Überwachungsprotokolleinträge aus über Geos, beispielsweise Name & EUR Geo Benutzeraktivitäten in einer einzigen Org-Ansicht angezeigt werden, und klicken Sie dann können Sie vorhandene Filter an, um bestimmte Benutzer Aktivitäten finden Sie unter anwenden.
