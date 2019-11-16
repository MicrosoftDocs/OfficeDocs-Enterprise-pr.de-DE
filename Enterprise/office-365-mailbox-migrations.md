---
title: Office 365-Postfachmigrationen
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
description: Eine kurze Zusammenfassung der Cmdlets, die für Office 365 Postfachmigrationen verwendet werden.
ms.openlocfilehash: 03075fdab50ed5dd315d4f9b988032e40f4cbc85
ms.sourcegitcommit: 8027254ab4b9ed44a5b0c336f714049859f93f3d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2019
ms.locfileid: "38035545"
---
# <a name="office-365-mailbox-migrations"></a>Office 365-Postfachmigrationen

Bei einer Exchange-basierten hybridbereitstellung können Kunden wahlweise lokale Exchange-Postfächer in eine [Exchange Online](https://docs.microsoft.com/Exchange/exchange-online) Organisation verschieben oder Exchange Online Postfächer in eine [lokale Exchange-](https://docs.microsoft.com/Exchange/exchange-server) Organisation verschieben. Migrationsbatches werden beim Verschieben von Postfächern zwischen lokalen und Exchange Online Organisationen verwendet.

Kunden können Statistiken und andere Informationen zu Postfachmigrationen mit den folgenden Cmdlets überprüfen:

- [Get-MoveRequestStatistics](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/Get-MoveRequestStatistics?view=exchange-ps): stellt Standardstatistiken für ein Benutzerpostfach bereit, das den Status, die Postfachgröße, die Archiv Postfachgröße und den abgeschlossenen Prozentsatz enthält.
- [Get-Mailbox](https://docs.microsoft.com/powershell/module/exchange/mailboxes/Get-Mailbox?view=exchange-ps
): enthält eine Zusammenfassungsliste der Postfachobjekte und-Attribute in der Organisation.
- [Get-Recipient](https://docs.microsoft.com/powershell/module/exchange/users-and-groups/Get-Recipient?view=exchange-ps): enthält eine Liste vorhandener e-Mail-aktivierter Objekte wie Postfächer, e-Mail-Benutzer, Kontakte und Verteilergruppen.
- [Get-MoveRequest](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/Get-MoveRequest?view=exchange-ps): bietet einen detaillierten Status einer laufenden Postfachmigration.
- [Get-MigrationUser](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/Get-MigrationUser?view=exchange-ps): enthält Informationen über die Benutzer der Post Fach Verlagerung und-Migration.
- [Get-MigrationBatch](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/Get-MigrationBatch?view=exchange-ps): enthält Informationen zum Status des aktuellen Migrationsbatches.
- [Get-MigrationUserStatistics](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/Get-MigrationUserStatistics?view=exchange-ps): enthält detaillierte Informationen zum Migrationsstatus für einen bestimmten Benutzer.
- [Get-MailboxStatistics](https://docs.microsoft.com/powershell/module/exchange/mailboxes/Get-MailboxStatistics?view=exchange-ps): stellt Informationen zu Postfächern bereit, beispielsweise die Größe, die Anzahl der Nachrichten und die Uhrzeit des letzten Zugriffs.

Weitere Informationen zu Cmdlets finden Sie unter [Umzugs-und Migrations-Cmdlets in Exchange Online](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell?view=exchange-ps).
