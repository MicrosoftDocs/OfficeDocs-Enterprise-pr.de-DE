---
title: Personalsteuerungen in Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
description: 'Zusammenfassung: eine Übersicht über die Microsoft-Personal Prüfungsverfahren für Office 365.'
ms.openlocfilehash: 82a8578ef5b5812dc3dfcfa69ccff604d2254286
ms.sourcegitcommit: 55a046bdf49bf7c62ab74da73be1fd1cf6f0ad86
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/20/2019
ms.locfileid: "37067422"
---
# <a name="office-365-personnel-controls"></a>Personalsteuerungen in Office 365 

Das Personal Screening, der Prozess der Überprüfung und Validierung des bisherigen Verhaltens und Status eines Bewerbers, ist eine wichtige Minderungs Kontrolle, um Office 365 Dienst Kompromiss zu verhindern. Während das vergangene Verhalten keine perfekte Voraussage für zukünftiges Verhalten ist, hilft es, mögliche fehlerhafte Akteure zu identifizieren. Der Microsoft-Personal Prüfungs Standard gilt für alle Microsoft-Mitarbeiter, Praktikanten und Kontingent Mitarbeiter, die an der Entwicklung, dem Betrieb oder der Bereitstellung von Onlinediensten für Behörden oder kommerzielle Cloud-Kunden beteiligt sind. Screening-Standards für nationale Cloud-Umgebungen, die nicht von Microsoft betrieben werden, werden von den Mitarbeitern des Betriebs Partners für die jeweilige Umgebung definiert.

## <a name="the-microsoft-personnel-screening-standard"></a>Der Microsoft-Personal Prüfungs Standard

Die Vorgehensweisen für das Personal Screening für Office 365 stimmen mit den Microsoft-Richtlinien für Unternehmensstandards und nationale Institute of Standards and Technology (NIST) für das Personal Screening überein. Microsoft-Mitarbeiter, die folgenden Zugriff benötigen, unterliegen dem Microsoft-Personal Prüfungs Standard:

- Physischer Zugriff auf Rechenzentren, Nebenstellenanlagen, gesicherte Räume, Käfige, Server Racks oder Edge-Websites, die die Infrastruktur zur Unterstützung von Onlinediensten für öffentliche oder kommerzielle Cloud-Kunden bereitstellen.
- Logischer Zugriff auf Kundendaten von Government oder Commercial Cloud, die über bestimmte verwaltete Umgebungen bereitgestellt werden.
- Netzwerkverwaltung Zugriff auf Geräte und Dienste, die die Kundendaten von Government oder Commercial Cloud transportieren oder speichern.

Zu den spezifischen personalbezogenen Ereignissen, die Screening-Anforderungen auslösen, gehören:

- Neue Microsoft-Mitarbeiter in Rollen, bei denen das Screening eine definierte Anforderung ist.
- Interne Microsoft-Mitarbeiter, die übertragen oder auf eine vorhandene Rolle verschoben wurden, die derzeit das Screening als definierte Anforderung umfasst.
- Vorhandene Rollen, die den Bereich ändern, um das Screening als definierte Anforderung einzubeziehen.

## <a name="screening-enforcement-criteria"></a>Screening-Durchsetzungs Kriterien

Um sicherzustellen, dass nur genehmigte Mitarbeiter Zugriff auf Kundendaten oder Umgebungen haben, für die eine Überprüfung erforderlich ist, gelten die folgenden Durchsetzungs Kriterien.

**Nur in den Vereinigten Staaten nur Cloud-Umgebungen**:

- Der Zugriff auf Kundendaten oder-Umgebungen, für die eine Überprüfung erforderlich ist, ist erst nach Abschluss der Entscheidung und Screening-Anforderungen zulässig.
- Microsoft-Mitarbeiter, die keinen Zugriff mehr auf Kundendaten oder Verwandte Umgebungen benötigen, haben beim Verlassen von Microsoft oder beim Wechsel zu einer neuen Rolle Zugriff auf die Datenbank.
- Microsoft-Mitarbeiter verlassen die Smart Cards mit geschirmten Umgebungen vor dem Verlassen der USA mit der Verwaltung.

**Nationale Cloud-Umgebungen**:

- Mitarbeiter von Drittanbieter-oder Daten Treuhändern sind für die Verwaltung und Erzwingung des Zugriffs für nationale Cloud-Umgebungen verantwortlich.

In den Microsoft Cloud Services-Umgebungen wird der Zugriff aufgrund der Rolle eines Benutzers und des betreffenden Daten Typs eingeschränkt, wie in der folgenden Tabelle beschrieben. Qualifiziertes oder nicht qualifiziertes Personal, das sich physisch außerhalb der USA befindet, darf keinen Zugriff auf Kundendaten innerhalb einer US-amerikanischen Cloud haben. Der Zugriff auf nationale Cloud-Umgebungen ist so eingeschränkt, dass Microsoft-Mitarbeiter ohne Genehmigung durch den Drittanbieter oder den Daten Treuhänder keinen technischen Zugriff auf Kundendaten oder Systeme haben, die Kundendaten enthalten.

| Rolle | Zugriff auf Kundendaten | Zugriff auf System Daten |
|---------------------------------------------------------------------------|------------------------------|---------------------------------|
| Qualifiziertes Personal, das sich physisch in den Vereinigten Staaten befindet | Erlaubt | Erlaubt |
| Qualifiziertes Personal, das sich physisch außerhalb der USA befindet | Nicht zulässig | Erlaubt |
| Internationaler Ausnahme Zugriff für Microsoft-Mitarbeiter: ermöglicht den logischen Zugriff für Microsoft-Mitarbeiter, die sich nicht in dem Land befinden, in dem sich die Daten der Regierung oder des Geschäftskunden in Ruhe befinden. | Nicht zulässig | Erlaubt |
| Nicht qualifiziertes Personal (nicht geschirmte Mitarbeiter, die eine Eskorte von qualifiziertem Personal benötigen) | Zulässig mit Autorisierung | Zulässig mit Begleit Aufsicht |

## <a name="microsoft-pre-employment-screening"></a>Microsoft Pre-Employment Screening

Wenn es das lokale Recht zulässt, führt die globale Sicherheitsabteilung von Microsoft eine vorarbeits Prüfung durch. Dies ist eine formelle Hintergrund Untersuchung, die die folgenden Kriterien umfasst:

- Überprüfung des Lebenslaufs des Antragstellers auf Vollständigkeit und Genauigkeit
- Bestätigung von akademischen und beruflichen Qualifikationen
- Untersuchung eines Verlusts an beruflichen Anmeldeinformationen
- Überprüfung der letzten drei Arbeitgeber
- Ein Check of Police Records für Verbrechen Verurteilungen
- Bestätigung der Identität von einer von einem Staat ausgestellten Identifikation
- Bonitätsprüfungen, falls zutreffend

Eine regelmäßige erneute Überprüfung und/oder zusätzliche Hintergrundprüfungen sind möglicherweise für bestimmte Verwaltungs-, Sicherheits-oder andere Rollen erforderlich, einschließlich, aber nicht ausschließlich für US-basierte Mitarbeiter in Rollen, die Zugriff auf Kundendaten benötigen.
Für Kontingent Mitarbeiter gibt der Vertrag mit dem Drittanbieter die Anforderungen von Microsoft für die Überprüfung an, die vom Drittanbieter ausgeführt werden müssen. Bei Hintergrundüberprüfungen ist das drittanbieterunternehmen dafür verantwortlich, dass Microsoft überprüft, ob eine Hintergrundüberprüfung durchgeführt wurde. Die Ergebnisse der Hintergrundüberprüfung werden in der Regel per e-Mail von der Personalabteilung des Drittanbieters empfangen. Internationale Mitarbeiter von Vertrags Mitarbeitern können aufgrund von Gesetzen in Ländern, die Hintergrundprüfungen verbieten, vom Hintergrund Prüfungsprozess ausgenommen werden.

## <a name="microsoft-employment-screening"></a>Microsoft Employment Screening

Seit 2004 in den USA erfordert Microsoft Mitarbeitern und Praktikanten, einen siebenjährigen Strafregister Bildschirm als Teil der vorarbeits Überprüfung zu übergeben. Das Screening auf Verbrechen, Vergehen und die Überprüfung der Bildungs-und Beschäftigungs Geschichte ist enthalten.

Vor dem Zuweisen von Microsoft-Mitarbeitern oder einem von uns von Microsoft zugewiesenen Subunternehmer zur Bereitstellung von Office 365 bezogenen Diensten führt Microsoft die Unterauftragnehmer für die Durchführung einer Hintergrundüberprüfung aus, die aus einer Ablaufverfolgung für Sozialversicherungsnummern besteht und Überprüfung des Strafregisters. Die Daten aus dieser Hintergrundüberprüfung sind ein Faktor in der Einstellungsentscheidung. Die Strafregister Prüfung umfasst ein siebenjähriges Verbrechen und Vergehens Delikte zur Überprüfung von Bundes-, Bundesland-und Landkreis Einträgen (sofern zutreffend).

Als Bedingung für die Beschäftigung und zum Zeitpunkt der Einstellung müssen alle Microsoft-Mitarbeiter Vertraulichkeits-und Geheimhaltungsvereinbarungen unterzeichnen und überprüfen, ob Sie das Microsoft-Mitarbeiterhandbuch überprüft haben.

## <a name="microsoft-cloud-background-check"></a>Microsoft-Cloud-Hintergrundüberprüfung

Eine Microsoft-Cloud-Hintergrundüberprüfung ist für Bewerber erforderlich, die als Mitarbeiter für Office 365 bezogene Dienste in den Vereinigten Staaten eingestellt sind. Microsoft-Mitarbeiter in den Vereinigten Staaten mit Zugriff auf Kundendaten müssen dem von allen Office 365 Diensten benötigten Microsoft Cloud Background Check Prozess entsprechen. Außerhalb der Vereinigten Staaten variiert der Prozess. Beispielsweise verwendet die Microsoft-Cloud für Deutschland ein Daten Vertrauensnehmer-Genehmigungsmodell, mit dem sichergestellt werden soll, dass der Daten Treuhänder (ein deutsches Unternehmen) und nicht Microsoft die Kontrolle über den Zugriff auf Kundendaten hat. Die Microsoft-Cloud in Deutschland wird von Rechenzentren in Deutschland zugestellt, und die Operations Center (OC), die das technische Personal des Daten Treuhänders enthalten, sind ebenfalls in Deutschland. Sowohl das Rechenzentrum als auch die OC-Einrichtungen werden vom Daten Treuhänder betrieben, verwaltet und gesteuert.

In der folgenden Tabelle sind die Prüfungen aufgeführt, die im Rahmen der Microsoft-Cloud-Hintergrundüberprüfung durchgeführt werden.

| Prüfung | Beschreibung |
|--------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------|
| Suche nach Sozialversicherungsnummern | Überprüft, ob die vorgesehene Sozialversicherungsnummer gültig ist. |
| Überprüfen des Vorstrafenregisters | Siebenjährige Strafregister überprüfen auf Verbrechen und Vergehens Delikte auf bundesstaatlicher, Landkreis-und lokaler Ebene und je nach Bedarf auf Bundesebene. |
| Steuerungsliste "Office of Foreign Assets" | Department of Treasury Liste von Personen und Organisationen, mit denen US-Bürger und dauerhafte Residenten keine Geschäfte tätigen dürfen. |
| Bureau of Industry and Security List | Department of Commerce Liste der Personen und Entitäten, die von der Beteiligung an Exportaktivitäten ausgeschlossen sind. |
| Office of Defense Trade Controls Debarred Persons List (*hinzugefügt am 1. Juli 2010*) | Abteilung für Statusliste von Personen und Entitäten, die von der Beteiligung an Exportaktivitäten im Zusammenhang mit der Rüstungsindustrie ausgeschlossen sind. |

Die Ergebnisse der Microsoft-Cloud-Hintergrundüberprüfung werden in unserer Mitarbeiterdatenbank gespeichert und mit unseren Datencenter-Zugriffs Steuerungssystemen verbunden. Wenn die Microsoft-Cloud-Hintergrundüberprüfung abläuft und der Mitarbeiter Sie nicht erneuert, wird der Zugriff auf Office 365 Dienste widerrufen und ist nicht mehr verfügbar, bis die Microsoft-Cloud-Hintergrundüberprüfung abgeschlossen ist. Wenn das Arbeitsverhältnis mit Microsoft endet, wird der Zugriff auf alle Datencenter sofort aufgehoben.

Die Staatsbürgerschaft der Vereinigten Staaten wird für alle Mitarbeiter mit physischem oder logischem Zugriff auf die Office 365 US-Regierungsdienste überprüft. Um die Staatsbürgerschaft zu überprüfen, treffen sich Mitarbeiter und/oder neue Kandidaten mit einem US-Staats Bürgerschafts Delegierten, der zur Überprüfung der US-Staatsbürgerschaft für die Dokumentation ausgebildet wurde. Mitarbeiter oder neue Bewerber müssen die erforderlichen Unterlagen mitbringen und bei einer Besprechung mit dem Delegierten der Staatsbürgerschaft für Ihre Region ein Bestätigungsformular unterzeichnen. Die Besprechung muss persönlich erfolgen. Sobald die Person mit dem Delegierten für die Staatsbürgerschaft zusammengetroffen und die erforderlichen Dokumentationen und Signaturen bereitgestellt hat, leitet die Staatsbürgerschaft eine Kopie der Dokumente an Microsoft-Mitarbeiter Vorgänge weiter, die die Kopie an die Datensatzaufbewahrung übermitteln.

Mitarbeiter mit logischem Zugriff auf die Office 365 u.s. Government Community Cloud oder logischer oder physischer Zugriff auf die Azure u.s. Government-Angebote sind erforderlich, um die Anforderungen des FBI an die Strafjustiz einzuhalten. [ Services](https://www.fbi.gov/services/cjis) (CJIS), einschließlich Personal Screening. Das CJIS-Screening zur Unterstützung des Office 365 U.S. Government Services umfasst eine Fingerabdruck basierte Überprüfung des strafrechtlichen Hintergrunds, die von der CJIS-System Agentur für Juror in Staaten, die sich im Microsoft Online Services-CJIS [registriert haben, fest](https://blogs.office.com/2013/10/23/california-and-microsoft-sign-cjis-security-policy-agreement/) gelegt wurde. Support Programm.
