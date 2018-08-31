---
title: Anwenden von Bezeichnungen auf personenbezogene Daten in Office 365
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 2/7/2018
ms.audience: ITPro
ms.topic: overview
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- GDPR
ms.service: o365-solutions
localization_priority: Priority
ms.custom: ''
ms.assetid: ''
search.appverid:
- MET150
description: Erfahren Sie, wie Sie Office-Bezeichnungen im Rahmen Ihres DSGVO-Schutzplans verwenden können.
ms.openlocfilehash: c0058a023b807b81df42274d5e8b9408e37d505d
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/21/2018
ms.locfileid: "22914930"
---
# <a name="apply-labels-to-personal-data-in-office-365"></a>Anwenden von Bezeichnungen auf personenbezogene Daten in Office 365

 Lesen Sie diese Thema, wenn Sie Office-Bezeichnungen im Rahmen Ihres DSGVO-Schutzplans verwenden. Bezeichnungen können derzeit im Office 365 Security & Compliance Center und in Azure Information Protection erstellt werden. Mit der Zeit werden diese Technologien in einer einheitlichen Bezeichnungs- und Klassifikationserfahrung zusammengeführt, damit Sie noch mehr erreichen können.

Wenn Sie Bezeichnungen zum Schutz personenbezogener Daten in Office 365 verwenden, wird empfohlen, mit Office-Bezeichnungen zu beginnen. Sie können erweiterte Datenkontrolle verwenden, um Bezeichnungen auf Grundlage von vertraulichen Informationstypen und anderen Kriterien automatisch anzuwenden. Office-Bezeichnungen können mit Verhinderung von Datenverlust (DLP) verwendet werden, um Schutz anzuwenden. Sie können in Kürze sowohl Bezeichnungen als auch vertrauliche Informationstypen mit Cloud App Security verwenden, um personenbezogene Daten zu überwachen, die in anderen SaaS-Apps gespeichert sind.

Azure Information Protection-Bezeichnungen werden derzeit für das Anwenden von Bezeichnungen auf lokale Dateien und Dateien in anderen Clouddiensten und Anbietern empfohlen. Diese werden auch für Dateien in Office 365 empfohlen, für die die Azure RMS-Verschlüsselung (Azure Rights Management) für Schutz von Daten wie z. B. Dateien mit Betriebsgeheimnissen erforderlich ist.

Zu diesem Zeitpunkt wird die Verwendung von Azure Information Protection zum Anwenden der Azure RMS-Verschlüsselung nicht für Dateien mit Daten in Office 365 empfohlen, die der DSGVO unterliegen. Office 365-Dienste können derzeit RMS-verschlüsselte Dateien nicht lesen. Aus diesem Grund kann der Dienst die vertraulichen Daten in diesen Dateien nicht finden.

Azure Information Protection-Bezeichnungen können auf E-Mails in Exchange Online angewendet werden und können mit DLP von Office 365 verwendet werden. Mit den in Kürze verfügbaren einheitlichen Klassifikations- und Bezeichnungsmodul können Sie die gleichen Bezeichnungen für E-Mails und Dateien verwenden, darunter automatisches Anwenden von Bezeichnungen auf E-Mails und Schutz von E-Mails während der Übertragung.

![Bezeichnungen in Office 365 und Azure Information Protection](Media/Apply-labels-to-personal-data-in-Office-365-image1.png)

In der Abbildung sehen Sie Folgendes:

-   Verwenden von Office 365-Bezeichnungen für personenbezogene Daten und streng geregelte Dateien sowie Dateien mit Betriebsgeheimnissen in SharePoint Online und OneDrive for Business

-   Verwenden von Azure Information Protection (AIP)-Bezeichnungen für streng geregelte Dateien sowie Dateien mit Betriebsgeheimnissen, Exchange Online-E-Mails, Dateien in anderen SaaS-Diensten, Dateien in lokalen Rechenzentren und Dateien in anderen Cloudanbietern

-   In Kürze verfügbar: beide Arten von Bezeichnungen werden in einer einheitlichen Klassifikations- und Bezeichnungserfahrung zusammengeführt.

## <a name="use-office-labels-and-sensitive-information-types-across-microsoft-365-for-information-protection"></a>Verwenden von Office-Bezeichnungen und vertraulichen Informationstypen in Microsoft 365 zum Schutz von Informationen

Die folgende Abbildung zeigt, wie Office-Bezeichnungen und vertrauliche Informationstypen in Bezeichnungsrichtlinien, DLP-Richtlinien und mit Cloud App Security-Richtlinien verwendet werden können.

![Office-Bezeichnungen und vertrauliche Informationstypen](Media/Apply-labels-to-personal-data-in-Office-365-image2.png)

Für Zwecke der Barrierefreiheit enthält die folgende Tabelle die gleichen Beispiele wie die Abbildung.

<table>
<thead>
<tr class="header">
<th align="left"><strong>Klassifikationselemente</strong></th>
<th align="left"><strong>Bezeichnungsrichtlinien – 2 Beispiele</strong></th>
<th align="left"><strong>DLP-Richtlinien – 2 Beispiele</strong></th>
<th align="left"><strong>Cloud App Security-Richtlinien für alle SaaS-Apps – 1 Beispiel</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">Office-Bezeichnungen. Beispiele: „Privat“, „Öffentlich“, „Kundendaten“, „Personaldaten“, „Vertraulich“, „Streng vertraulich“</td>
<td align="left"><p>Diese Bezeichnung automatisch anwenden...</p>
<p>Kundendaten</p>
<p>... auf Dokumente, die folgenden vertraulichen Informationstypen entsprechen...</p>
<p>&lt;Liste der Beispiele für vertrauliche Informationstypen&gt;</p></td>
<td align="left"><p>Diesen Schutz anwenden...</p>
<p>&lt;Schutz definieren&gt;</p>
<p>... auf Dokumente mit dieser Bezeichnung...</p>
<p>Kundendaten</p></td>
<td align="left"><p>Warnung, wenn Dateien mit diesen Attributen...</p>
<p>&lt;vordefiniertes PII-Attribut – oder – benutzerdefinierter Ausdruck&gt;</p>
<p>... in einer beliebigen genehmigten SaaS-App außerhalb der Organisation freigegeben werden</p></td>
</tr>
<tr class="even">
<td align="left">Vertrauliche Informationstypen. Beispiele: Nationale belgische Nummer, Kreditkartennummer, Kroatische ID-Kartennummer, nationale finnische ID-Nummer</td>
<td align="left"><p>Diese Bezeichnungen für Benutzer zum manuellen Anwenden veröffentlichen...</p>
<p>&lt;Bezeichnungen wählen&gt;</p>
<p>... für diese Speicherorte...</p>
<p>&lt;alle Speicherorte oder bestimmte Speicherorte wählen&gt;</p></td>
<td align="left"><p>Diesen Schutz anwenden...</p>
<p>&lt;Schutz definieren&gt;</p>
<p>... auf Dokumente, die folgenden vertraulichen Informationstypen entsprechen&gt;</p></td>
<td align="left">Hinweis: In Kürze in Cloud App Security verfügbare Attribute beinhalten vertrauliche Informationstypen in Office 365 und einheitliche Bezeichnungen für Office 365 und Azure Information Protection.</td>
</tr>
</tbody>
</table>

## <a name="prioritize-auto-apply-label-policies"></a>Priorisieren automatisch angewendeter Bezeichnungsrichtlinien

Für personenbezogene Daten, die der DSGVO unterliegen, wird empfohlen, Bezeichnungen automatisch anzuwenden, indem vertrauliche Informationstypen verwendet werden, die Sie für Ihre Umgebung bereitgestellt haben. Es ist wichtig, dass Richtlinien für das automatische Anwenden von Bezeichnungen gut konzipiert und getestet wurden, damit ein beabsichtigtes Verhalten auftritt.

Die Reihenfolge, in der automatisch anzuwendende Richtlinien erstellt werden, sowie, ob Benutzer diese Bezeichnungen auch anwenden, wirkt sich auf das Ergebnis aus. Es ist als wichtig, die Einführung sorgfältig zu planen. Folgendes müssen Sie dazu wissen.

### <a name="one-label-at-a-time"></a>Jeweils nur eine Bezeichnung

Sie können einem Dokument jeweils nur eine Bezeichnung zuweisen.

### <a name="older-auto-apply-policies-win"></a>Ältere automatisch anzuwendende Richtlinien gelten zuerst

Wenn es mehrere Regeln gibt, die eine automatisch anzuwendende Bezeichnung zuweisen, und der Inhalt die Bedingungen für mehrere Regeln erfüllt, wird die Bezeichnung für die älteste Regel zugewiesen. Aus diesem Grund ist es wichtig, die Richtlinien für Bezeichnungen sorgfältig zu planen, bevor Sie diese konfigurieren. Wenn für eine Organisation eine Änderung der Priorität der Richtlinien für Bezeichnungen erforderlich ist, müssen die Richtlinien gelöscht und erneut erstellt werden.

### <a name="manual-user-applied-labels-trump-auto-applied-labels"></a>Manuell von Benutzern angewendete Bezeichnungen sind wichtiger als automatisch angewendete Bezeichnungen

Manuell von Benutzern angewendete Bezeichnungen sind wichtiger als automatisch angewendete Bezeichnungen. Richtlinien für automatisches Anwenden können keine Bezeichnung ersetzen, die bereits von einem Benutzer angewendet wurde. Benutzer können Bezeichnungen ersetzen, die automatisch angewendet wurden.

### <a name="auto-assigned-labels-can-be-updated"></a>Automatisch zugewiesene Bezeichnungen können aktualisiert werden

Automatisch zugewiesene Bezeichnungen können entweder durch neuere Bezeichnungsrichtlinien oder durch Aktualisierungen vorhandener Richtlinien aktualisiert werden.

Achten Sie darauf, dass Ihr Plan für die Implementierung von Bezeichnungen Folgendes umfasst:

-   Priorisieren der Reihenfolge, in der automatisch angewendete Richtlinien erstellt werden.

-   Ausreichend Zeit für das automatische Anwenden von Bezeichnungen, bevor diese für das manuelle Anwenden für Benutzer bereitgestellt werden. Es kann bis zu sieben Tage dauern, bis die Bezeichnungen auf alle Inhalte angewendet werden, die die Bedingungen erfüllen.

### <a name="example-priority-for-creating-the-auto-apply-policies"></a>Beispiel für Priorität für das Erstellen von automatisch angewendeten Richtlinien

<table>
<thead>
<tr class="header">
<th align="left"><strong>Bezeichnungen</strong></th>
<th align="left"><strong>Prioritätsreihenfolge beim Erstellen von automatisch angewendeten Richtlinien</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">Personaldaten – Mitarbeiterdaten</td>
<td align="left">1</td>
</tr>
<tr class="even">
<td align="left">Kundendaten</td>
<td align="left">2</td>
</tr>
<tr class="odd">
<td align="left">Streng vertraulich</td>
<td align="left">3</td>
</tr>
<tr class="even">
<td align="left">Personaldaten – Gehaltsdaten</td>
<td align="left">4</td>
</tr>
<tr class="odd">
<td align="left">Vertraulich</td>
<td align="left">5</td>
</tr>
<tr class="even">
<td align="left">Öffentlich</td>
<td align="left">6</td>
</tr>
<tr class="odd">
<td align="left">Privat</td>
<td align="left">Keine automatisch angewendete Richtlinie</td>
</tr>
</tbody>
</table>

## <a name="create-labels-and-auto-apply-label-policies"></a>Erstellen von Bezeichnungen und automatisch angewendeten Bezeichnungsrichtlinien

Erstellen Sie Bezeichnungen und Richtlinien im Office 365 Security & Compliance Center.

<table>
<thead>
<tr class="header">
<th align="left"><strong>Schritt</strong></th>
<th align="left"><strong>Beschreibung</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>Gewähren von Berechtigungen für Mitglieder Ihres Complianceteams</p></td>
<td align="left"><p>Mitglieder Ihres Complianceteams, die Bezeichnungen erstellen möchten, benötigen Berechtigungen für die Verwendung des Security &amp; Compliance Centers. Wechseln Sie im Security & Compliance Center zu „Berechtigungen“. und ändern Sie die Mitglieder der Gruppe „Complianceadministrator“.</p>
<p>Weitere Informationen finden Sie unter <a href="https://support.office.com/en-ie/article/Give-users-access-to-the-Office-365-Security-Compliance-Center-2cfce2c8-20c5-47f9-afc4-24b059c1bd76">Freigeben des Benutzerzugriffs auf das Office 365 Security &amp; Compliance Center</a></p></td>
</tr>
<tr class="even">
<td align="left"><p>Erstellen von Office-Bezeichnungen</p></td>
<td align="left">Wechseln Sie im Security & Compliance Center zu „Klassifizierungen“, wählen Sie „Bezeichnungen“, und erstellen Sie die Bezeichnungen für Ihre Umgebung.</td>
</tr>
<tr class="odd">
<td align="left"><p>Erstellen automatisch angewendeter Richtlinien für Bezeichnungen</p></td>
<td align="left">Wechseln Sie im Security & Compliance Center zu „Klassifizierung“, wählen Sie „Bezeichnungsrichtlinien“, und erstellen Sie Richtlinien für automatisch angewendete Bezeichnungen. Vergewissern Sie sich, dass Sie diese Richtlinien in der entsprechenden Reihenfolge erstellen.</td>
</tr>
</tbody>
</table>

Die folgende Abbildung zeigt, wie Sie eine automatisch angewendete Bezeichnung für die Bezeichnung „Kundendaten“ erstellen können.

![Erstellen und Anwenden einer Bezeichnung für Kundendaten](Media/Apply-labels-to-personal-data-in-Office-365-image3.png)

In der Abbildung sehen Sie Folgendes:

-   Die Bezeichnung „Kundendaten“ wird erstellt.

-   Die gewünschten vertraulichen Informationstypen für die DSGVO werden aufgeführt: Nationale belgische Nummer, Kreditkartennummer, Kroatische ID-Kartennummer, nationale finnische ID-Nummer.

-   Erstellen einer automatisch angewendeten Richtlinie, die die Bezeichnung „Kundendaten“ jeder Datei zuweist, die einen der vertraulichen Informationstypen enthält, die der Richtlinie hinzugefügt wurde.
