---
title: Office 365-eDiscovery-und Such Features (Übersicht)
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
- SPO_Content
f1.keywords:
- NOCSH
description: Eine Übersicht über das eDiscovery-Feature und andere Suchfeatures in Office 365 für die Verwendung und Transparenz der Überwachung.
ms.openlocfilehash: 16cb8ac4703142b73d4f56bce9390743495d3fc2
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/07/2020
ms.locfileid: "41843647"
---
# <a name="ediscovery-and-search-features"></a>eDiscovery und Suchfunktionen 

## <a name="ediscovery"></a>eDiscovery

Die eDiscovery-Funktion stellt Administratoren, Compliance-Verantwortlichen und anderen autorisierten Benutzern eine zentrale Stelle zur Verfügung, um eine umfassende Untersuchung Office 365 Benutzeraktivitäten durchzuführen. Sicherheitsbeauftragte mit den entsprechenden Berechtigungen führen Suchvorgänge durch und platzieren Inhalte in der Aufbewahrungsstelle. Bei den Suchergebnissen handelt es sich um dieselben Ergebnisse wie bei einer Inhaltssuche, es werden jedoch keine eDiscovery-Fälle für alle angewendeten Haltestatus erstellt. Die Ergebnisse von eDiscovery-suchen werden aus Sicherheitsgründen verschlüsselt, und Sie können exportierte Daten mit [Advanced eDiscovery](https://support.office.com/article/office-365-advanced-ediscovery-fd53438a-a760-45f6-9df4-861b50161ae4)analysieren.

## <a name="content-search"></a>Inhaltssuche

Bei der [Inhaltssuche](https://support.office.com/article/Run-a-Content-Search-in-the-Office-365-Security-Compliance-Center-61852fd9-fe8a-4880-a339-cb19ed3bff4a) handelt es sich um ein eDiscovery-Such Tool, das verbesserte Skalierungs-und Leistungsfunktionen gegenüber früheren eDiscovery-Such Tools bereitstellt. Sie verwenden die Inhaltssuche zum Durchsuchen von Postfächern, öffentlichen Ordnern, SharePoint Online Websites und OneDrive für Unternehmen Speicherorten. Die Inhaltssuche unterstützt große Suchvorgänge. Es gibt keine Beschränkungen für die Anzahl der Postfächer und Websites, die Sie durchsuchen können. Außerdem gibt es keine Beschränkungen für die Anzahl der gleichzeitig ausgeführten Suchvorgänge. Nachdem Sie eine Suche ausgeführt haben, wird die Anzahl der Inhaltsquellen und eine geschätzte Anzahl von Suchergebnissen im Detailbereich auf der Suchseite angezeigt. Sie können eine Vorschau der Ergebnisse anzeigen oder Sie auf einen lokalen Computer exportieren. Wenn Ihre Organisation über ein Office 365 Enterprise E5-Abonnement verfügt, können Sie [die Ergebnisse](https://support.office.com/article/Run-a-Content-Search-in-the-Office-365-Security-Compliance-Center-61852fd9-fe8a-4880-a339-cb19ed3bff4a#prepare) zur Analyse mithilfe der leistungsstarken Analysefunktionen von [Office 365 Advanced eDiscovery](https://go.microsoft.com/fwlink/p/?LinkID=620116)vorbereiten.

## <a name="audit-log-search"></a>Überwachungsprotokollsuche

Neben dem Nachverfolgen von Änderungen in Ihrer Office 365 Organisation können Sie Überwachungsberichte anzeigen und Überwachungsprotokolle exportieren. Nachdem die Überwachung für einen Office 365 Mandanten aktiviert wurde, werden Benutzer-und Verwaltungsaktivitäten in Ereignisprotokollen aufgezeichnet und durchsuchbar gemacht. Beispielsweise können Sie die postfachüberwachungsprotokollierung zum Nachverfolgen von Aktionen verwenden, die für ein Postfach von anderen Benutzern als dem Postfachbesitzer ausgeführt werden. Compliance Officer können die Such-und Filterfunktionen für bestimmte Benutzeraktivitäten verwenden. Beispielsweise zum Identifizieren von Benutzern, die ein bestimmtes Dokument angezeigt oder heruntergeladen haben, wenn Administratoren Benutzer Verwaltungsaktivitäten ausgeführt haben, oder um Änderungen in der Mandanten Konfiguration in den letzten 90 Tagen anzuzeigen. Suchergebnisse enthalten wertvolle forensische Informationen zu bestimmten Aktivitäten, die von einem Benutzer oder Administrator durchgeführt werden. Eine Beschreibung der in Office 365 angemeldeten Benutzer-und Verwaltungsaktivitäten finden Sie unter über [wachte Aktivitäten in Office 365](https://support.office.com/article/Search-the-audit-log-in-the-Office-365-Security-Compliance-Center-0d4d0f35-390b-4518-800e-0c7ec95e946c#auditlogevents) .

Ereignisse aus SharePoint Online und OneDrive für Unternehmen werden innerhalb von 30 Minuten nach dem Auftreten im Protokoll angezeigt. Ereignisse aus Exchange Online werden innerhalb von 24 Stunden nach dem Auftreten in den Überwachungsprotokollen angezeigt. Anmeldeereignisse aus Azure AD sind innerhalb von Minuten nach dem Auftreten verfügbar, und andere Verzeichnis Ereignisse aus Azure AD sind innerhalb von 24 Stunden nach dem Auftreten verfügbar. Sie können Abzüge in Überwachungsprotokoll-Suchergebnissen zur weiteren Analyse exportieren. Es werden maximal 50.000 Einträge aus der einzelnen Überwachungsprotokoll Suche exportiert. Um weitere Einträge zu exportieren, die diesen Grenzwert haben, reduzieren Sie den Datumsbereich, oder führen Sie mehrere Überwachungsprotokoll Suchvorgänge aus.

In der folgenden Tabelle werden einige der Informationen aufgeführt, die in Aktivitätsberichten angezeigt werden. Weitere Informationen zu den Eigenschaften, die von den einzelnen Office 365 Arbeitslasten erfasst werden, finden Sie [in den detaillierten Eigenschaften im Office 365 Überwachungsprotokoll](https://support.office.com/article/detailed-properties-in-the-office-365-audit-log-ce004100-9e7f-443e-942b-9b04098fcfc3) .

| Eigenschaft | Beschreibung |
|----------------|----------------------------------------------------------------------------------------------------------------------|
| Datum | Datum und Uhrzeit des Ereignisses |
| Benutzer | Benutzer, der die Aktion ausgeführt hat |
| ClientIP | IPv4-oder IPv6-Adresse des Geräts, das verwendet wurde, als die Aktivität protokolliert wurde. |
| CreationTime | Datum und Uhrzeit in koordinierter Weltzeit (Coordinated Universal Time, UTC), wenn der Benutzer die Aktivität ausgeführt hat. |
| EventSource | Gibt an, dass ein Ereignis aufgetreten ist. Mögliche Werte sind SharePoint und ObjectModel. |
| ID | ID des Berichts Eintrags. Die ID identifiziert den Berichtseintrag eindeutig. |
| Vorgang | Name des Benutzers oder der Aktivität, der dem in der Anzeigeergebnisse für diese Benutzeraktivität ausgewählten Wert entspricht. |
| OrganizationId | GUID für den Office 365 Dienst des Unternehmens, in dem das Ereignis aufgetreten ist. |
| UserAgent | Informationen über den Browser des Benutzers, der vom Browser bereitgestellt wird. |
| UserId | Benutzer, der die Aktion (in der Eigenschaft "Operation" angegeben) ausgeführt hat, die dazu geführt hat, dass der Datensatz protokolliert wurde. |
| UserType | Der Typ des Benutzers, der den Vorgang ausgeführt hat. Die folgenden Werte geben den Benutzertyp an. |
|  | 0 gibt einen regulären Benutzer an. |
|  | 2 gibt einen Administrator in Ihrer Office 365 Organisation an. |
|  | 3 gibt ein Microsoft Datacenter-Administrator-oder Datacenter-Systemkonto an. |
| Arbeitslast | Office 365 Dienst, auf dem die Aktivität aufgetreten ist. Mögliche Werte für diese Eigenschaft sind: |
|  | Exchange Online |
|  | SharePoint Online |
|  | OneDrive for Business |
|  | Azure Active Directory-Berichte |

Ausführliche Anweisungen zum Durchsuchen Office 365 Überwachungsprotokolle finden Sie unter [Suchen von Überwachungsprotokollen im Office 365](https://support.office.com/article/Search-the-audit-log-in-the-Office-365-Security-Compliance-Center-0d4d0f35-390b-4518-800e-0c7ec95e946c).

## <a name="search-unified-audit-log"></a>Durchsuchen des einheitlichen Überwachungsprotokolls

Verwenden Sie die Überwachungsprotokoll-Suchfunktion, um das einheitliche Überwachungsprotokoll zu durchsuchen. Office 365 bietet auch die Möglichkeit zum Durchsuchen dieses Protokolls mithilfe von Remote-PowerShell. Das [Cmdlet Search-UnifiedAuditLog](https://docs.microsoft.com/powershell/module/exchange/policy-and-compliance-audit/Search-UnifiedAuditLog?view=exchange-ps) in Exchange Online PowerShell wird verwendet, um das vereinheitlichte Überwachungsprotokoll von Ereignissen in Bezug auf Benutzervorgänge aus Exchange Online, SharePoint Online, OneDrive für Unternehmen und Azure AD zu durchsuchen. 

Sie können nach allen Ereignissen in einem bestimmten Datumsbereich suchen oder die Ergebnisse auf der Grundlage bestimmter Kriterien filtern, beispielsweise einer bestimmten Aktion, des Benutzers, der die Aktion ausgeführt hat, oder des Zielobjekts. Administratoren können bis zu drei gleichzeitig ausgeführte Exchange Online PowerShell-Sitzungen verwenden, um große Datumsbereichs suchen aufzuteilen.