---
title: Ressourcengrenzwerte für Office 365
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
description: 'Zusammenfassung: Informationen zu den Ressourcen Grenzwerten für die verschiedenen Anwendungen in Office 365.'
ms.openlocfilehash: 7ccbf2bdfe359dd44a0b03dcf6e2aed8d5daedbe
ms.sourcegitcommit: 9eb68633728cc78e9906dab222edbf9977b17e21
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2019
ms.locfileid: "38035485"
---
# <a name="resource-limits"></a>Ressourcenbeschränkungen

Ressourcengrenzwerte werden mithilfe von Kontingenten (Limits) und Drosselung erzwungen. Azure Active Directory und die einzelnen Office 365 Dienste verwenden beides. Grenzen sind Dienst spezifisch und ändern sich im Laufe der Zeit, wenn neue Funktionen hinzugefügt werden. Ausführliche Informationen zu den aktuellen Grenzwerten für die verschiedenen Dienste finden Sie in den folgenden Themen:

- [Grenzwerte und Einschränkungen für Azure Active Directory Service](https://msdn.microsoft.com/library/azure/dn764971.aspx)
- [Exchange Online-Begrenzungen](https://technet.microsoft.com/library/exchange-online-limits.aspx)
- [Beschränkungen von Exchange Online Protection](https://technet.microsoft.com/library/exchange-online-protection-limits.aspx)
- [Grenzen und Grenzwerte für SharePoint Online Software](https://support.office.com/article/SharePoint-Online-software-boundaries-and-limits-8F34FF47-B749-408B-ABC0-B605E1F6D498)
- [Skype for Business Grenzen](https://technet.microsoft.com/library/skype-for-business-online-limits.aspx)
- [Jammern der Rest-API und Raten Begrenzungen](https://developer.yammer.com/docs/rest-api-rate-limits)
- [Dateigrößenbeschränkungen in Sway](https://support.office.com/article/File-size-limits-in-Sway-4db21bc6-b42b-499f-9272-66e089db109f)

Zusätzlich zu diesen Grenzwerten werden verschiedene Einschränkungs Mechanismen in Azure Active Directory und Office 365 verwendet. Die Drosselung innerhalb des Diensts ist besonders wichtig, da Netzwerkressourcen in Microsoft-Rechenzentren für die breite Palette von Kunden optimiert sind, die die Dienste nutzen. Zu den Einschränkungs Mechanismen gehören:

- Azure Active Directory und Office 365 verfügen über Einschränkungen auf Benutzerebene, die die Anzahl der Transaktionen oder gleichzeitigen Aufrufe (durch Skript oder Code) begrenzen, die von einem einzelnen Benutzer ausgeführt werden können.
- Jedem Mandanten wird bei der Mandanten Erstellung eine standardmäßige PowerShell-Einschränkungsrichtlinie zugewiesen. Diese Einstellungen wirken sich auf andere Elemente aus, beispielsweise die maximale Anzahl gleichzeitiger PowerShell-Sitzungen, die von einem einzelnen Administrator geöffnet werden können.
- Jeder Exchange Online-Kunde verfügt über eine standardmäßige Exchange-Webdienste-Richtlinie, die für EWS-Client Vorgänge optimiert ist, sowie für Einschränkungen, die für alle Outlook-Clients gelten.
