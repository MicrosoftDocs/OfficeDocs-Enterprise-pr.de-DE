---
title: Mandanten Isolierung in Office 365
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
description: Eine Zusammenfassung darüber, wie Microsoft die Mandanten Isolierung für Office 365 erzwingt.
ms.openlocfilehash: 4859fd5feec50159e71ca2ca8968388c5ab82d64
ms.sourcegitcommit: 55a046bdf49bf7c62ab74da73be1fd1cf6f0ad86
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/20/2019
ms.locfileid: "37067458"
---
# <a name="tenant-isolation-in-office-365"></a>Mandanten Isolierung in Office 365

Einer der Hauptvorteile von Cloud Computing ist das Konzept einer gemeinsam genutzten gemeinsamen Infrastruktur für zahlreiche Kunden gleichzeitig, die zu Größenvorteilen führt. Dieses Konzept wird als *mehr Mandanten*Fähigkeit bezeichnet. Microsoft arbeitet kontinuierlich daran, sicherzustellen, dass die mehrmandantenfähigen Architekturen unserer Cloud-Dienste auf Unternehmensebene Sicherheits-, Vertraulichkeits-, Datenschutz-, Integritäts-und Verfügbarkeitsstandards unterstützen.

Basierend auf den bedeutenden Investitionen und Erfahrungen, die von [Trustworthy Computing](https://www.microsoft.com/en-us/twc/default.aspx) und dem [Sicherheits Entwicklungslebenszyklus](http://www.microsoft.com/security/sdl/default.aspx)gesammelt wurden, wurden Microsoft Cloud-Dienste mit der Annahme entworfen, dass alle Mandanten potenziell feindlich für alle sind. andere Mandanten und wir haben Sicherheitsmaßnahmen implementiert, um zu verhindern, dass die Aktionen eines Mandanten die Sicherheit oder den Dienst eines anderen Mandanten beeinträchtigen oder auf den Inhalt eines anderen Mandanten zugreifen.

Die zwei Hauptziele der Verwaltung der mandantenisolation in einer Umgebung mit mehreren Mandanten sind:
1.  Verhindern von Auslaufen oder nicht autorisiertem Zugriff auf Kunden Inhalte über Mandanten hinweg; und
2.  Verhindern, dass die Aktionen eines Mandanten sich negativ auf den Dienst für einen anderen Mandanten auswirken

Mehrere Arten von Schutz wurden in Office 365 implementiert, um zu verhindern, dass Kunden Office 365 Dienste oder Anwendungen kompromittieren oder nicht autorisierten Zugriff auf die Informationen anderer Mandanten oder des Office 365 Systems erhalten, einschließlich:
- Die logische Isolierung von Kundeninhalten innerhalb der einzelnen Mandanten für Office 365 Dienste wird durch Azure Active Directory Autorisierung und rollenbasierte Zugriffssteuerung erreicht.
- SharePoint Online bietet Daten Isolationsmechanismen auf Speicherebene.
- Microsoft verwendet strenge physische Sicherheit, Hintergrundprüfung und eine mehrstufige Verschlüsselungsstrategie, um die Vertraulichkeit und Integrität von Kundeninhalten zu schützen. Alle Office 365 Rechenzentren verfügen über biometrische Zugriffssteuerungen, wobei die meisten Palm Prints benötigen, um physischen Zugriff zu erhalten. Darüber hinaus müssen alle in den USA ansässigen Microsoft-Mitarbeiter eine standardmäßige Hintergrundüberprüfung im Rahmen des Einstellungsprozesses erfolgreich abschließen. Weitere Informationen zu den Steuerelementen, die für den administrativen Zugriff in Office 365 verwendet werden, finden Sie unter [Office 365 administrative Zugriffssteuerung](office-365-administrative-access-controls-overview.md).
- Office 365 verwendet dienstseitige Technologien zum Verschlüsseln von Kundeninhalten im Rest und in der Übertragung, einschließlich BitLocker, Verschlüsselung per Datei, Transport Layer Security (TLS) und IPSec (Internet Protocol Security). Spezifische Details zur Verschlüsselung in Office 365 finden Sie unter [Datenverschlüsselungstechnologien in Office 365](/microsoft-365/compliance/office-365-encryption-in-the-microsoft-cloud-overview.md).

Zusammen bieten die oben aufgeführten Schutzmechanismen zuverlässige logische Isolierungs Steuerelemente, die den Schutz und die Minderung von Bedrohungen ermöglichen, gleichbedeutend mit der von der physischen Isolierung allein bereitgestellten.

## <a name="related-links"></a>Links zu verwandten Themen
- [Isolierung und Zugriffssteuerung in Azure Active Directory](office-365-isolation-in-azure-active-directory.md)
- [Mandantenisolation in Office Graph und Delve](office-365-isolation-in-graph-and-delve.md)
- [Mandantenisolation in der Office 365-Suche](office-365-isolation-in-office-365-search.md)
- [Mandantenisolation in Office 365 Video](office-365-isolation-in-office-365-video.md)
- [Ressourcenbeschränkungen](office-365-resource-limits.md)
- [Überwachen und Testen von Mandantengrenzen](office-365-monitoring-and-testing.md)
- [Isolierung und Zugriffskontrolle in Office 365](office-365-isolation-in-office-365.md)