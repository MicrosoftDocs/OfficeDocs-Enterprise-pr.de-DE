---
title: Office 365 IdFix-Transaktionsprotokoll
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: reference
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
ms.assetid: d58b7d45-7947-4193-9456-82ba76f42d89
description: Enthält ein Beispiel und beschreibt die Benennungskonvention und die Standardprotokoll Ebene des Office 365 IdFix-Transaktionsprotokolls.
ms.openlocfilehash: 22ea5af87b1bbcaa96f88e3746a50f1411a01b9a
ms.sourcegitcommit: a9804062071939b7b7e60da5b69f484ce1d34ff8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/04/2019
ms.locfileid: "39813423"
---
# <a name="office-365-idfix-transaction-log"></a>Office 365 IdFix-Transaktionsprotokoll

*Dieser Artikel gilt sowohl für Office 365 Enterprise als auch Microsoft 365 Enterprise*.

Enthält ein Beispiel und beschreibt die Benennungskonvention und die Standardprotokoll Ebene des Office 365 IdFix-Transaktionsprotokolls.
  
## <a name="idfix-transaction-log-location"></a>Speicherort des IdFix-Transaktionsprotokolls

Das Office 365 IdFix-Tool erstellt jedes Mal ein neues Transaktionsprotokoll, wenn Sie auf in IdFix **anwenden** klicken und Änderungen auf die Active Directory Gesamtstruktur anwenden. Das Transaktionsprotokoll wird in demselben Ordner gespeichert, in dem Sie IdFix installiert haben. Standardmäßig lautet dieser Ordner C:\Deployment Tools\IDFix. Der Name der Transaktionsprotokolldatei verwendet ein Datums-und Zeitstempelformat, beispielsweise Verbose 6-1-2018 6-17-22 Uhr gibt eine Datei an, die am 1. Juni 2018 um 6:17:22 Uhr generiert wurde. Verbose gibt die Protokollierungsstufe an. 
  
## <a name="idfix-transaction-log-logging-level"></a>IdFix-Transaktionsprotokoll Protokollierungsstufe

Das Wort Verbose im Namen der Transaktionsprotokolldatei gibt die Protokollierungsebene in der Datei an. Verbose bedeutet, dass die maximale Menge an Informationen im Protokoll erfasst wird. Dies ist die Standard Protokollierungsstufe. Zu diesem Zeitpunkt können Sie die Protokollierungsstufe nicht ändern.
  
## <a name="idfix-transaction-log-format"></a>IdFix-Transaktionsprotokollformat

IdFix schreibt die Ergebnisse der einzelnen **Update** Aktionen wie im folgenden Beispiel gezeigt in ein Transaktionsprotokoll:
  
```
5/22/2018 6:36:44 AM Initialized - IdFix version 1.07 - Multi-Tenant
5/22/2018 6:36:47 AM Query AD
5/22/2018 6:36:47 AM FOREST:e2k10.com SERVER:dc1.e2k10.com FILTER:(|(objectCategory=Person)(objectCategory=Group))
5/22/2018 6:36:47 AM Please wait while the LDAP Connection is established.
5/22/2018 6:36:49 AM Query Count: 140  Error Count: 29  Duplicate Check Count: 191
5/22/2018 6:36:49 AM Elapsed Time: AD Query - 00:00:02.3890432
5/22/2018 6:36:49 AM Write split files
5/22/2018 6:36:49 AM Merge split files
5/22/2018 6:36:49 AM Count duplicates
5/22/2018 6:36:49 AM Write filtered duplicate objects
5/22/2018 6:36:49 AM Read filtered duplicate objects
5/22/2018 6:36:49 AM Read error file
5/22/2018 6:36:49 AM Elapsed Time: Duplicate Checks - 00:00:00.0780785
5/22/2018 6:36:49 AM Populating DataGrid
5/22/2018 6:36:50 AM Elapsed Time: Populate DataGridView - 00:00:00.0780785
5/22/2018 6:36:50 AM Query Count: 140  Error Count: 53
5/22/2018 6:37:34 AM Apply Pending
5/22/2018 6:37:34 AM Update: [CN=user000001,OU=e2k10OU1,DC=e2k10,DC=com][user][mailnickname][character][user?^|000001][user000001][EDIT]
5/22/2018 6:37:34 AM Update: [CN=user000008,OU=e2k10OU1,DC=e2k10,DC=com][user][targetAddress][duplicate][smtp:user000008@customer.com][][REMOVE]
5/22/2018 6:37:34 AM COMPLETE
5/22/2018 6:37:40 AM Loading Updates
5/22/2018 6:37:40 AM Action Selection
5/22/2018 6:37:57 AM Apply Pending
5/22/2018 6:37:57 AM Update: [CN=user000001,OU=e2k10OU1,DC=e2k10,DC=com][user][mailnickname][character][user?^|000001][user000001][UNDO]
5/22/2018 6:37:57 AM Update: [CN=user000008,OU=e2k10OU1,DC=e2k10,DC=com][user][targetAddress][duplicate][smtp:user000008@customer.com][][UNDO]
5/22/2018 6:37:57 AM COMPLETE

```