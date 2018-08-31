---
title: Office 365 IdFix-Transaktionsprotokoll
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: reference
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
ms.assetid: d58b7d45-7947-4193-9456-82ba76f42d89
description: Enthält ein Beispiel, und beschreibt die Namenskonvention und den standardmäßigen Protokolliergrad des Office 365-IdFix-Transaktionsprotokolls.
ms.openlocfilehash: 016318c7e771ec6c5f90336e11c5dd011144d12e
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540872"
---
# <a name="office-365-idfix-transaction-log"></a>Office 365 IdFix-Transaktionsprotokoll

Enthält ein Beispiel, und beschreibt die Namenskonvention und den standardmäßigen Protokolliergrad des Office 365-IdFix-Transaktionsprotokolls.
  
## <a name="idfix-transaction-log-location"></a>IdFix-Transaktionsprotokoll-Speicherort

Das Office 365 IdFix-Tool erstellt ein neues Transaktionsprotokoll bei jedem Klicken Sie auf **Übernehmen** in IdFix und Anwenden von Änderungen an der Active Directory-Gesamtstruktur. Das Transaktionsprotokoll wird im selben Ordner gespeichert, in dem Sie IdFix installiert haben. Standardmäßig ist dieser Ordner C:\Deployment Tools\IDFix. Der Name der Protokolldatei Transaktion verwendet ein Datums- und Zeitstempel Format z. B. Verbose 6-1-2018 6-17-22 Uhr gibt eine Datei, die mit 1 Juni 2018 auf 6:17:22 PM erzeugt wurde Verbose gibt die Protokollierungsstufe an. 
  
## <a name="idfix-transaction-log-logging-level"></a>Protokollierungsstufe für das IdFix-Transaktionsprotokoll

Das Wort "verbose" (ausführlich) im Namen der Transaktionsprotokolldatei gibt die Stufe der Protokollierung in der Datei an. "Verbose" bedeutet, dass die maximale Anzahl an Informationen im Protokoll erfasst wird. Dies ist der Standardprotokolliergrad. Derzeit kann die Protokollierungsstufe nicht geändert werden.
  
## <a name="idfix-transaction-log-format"></a>IdFix-Transaktionsprotokoll-Format

IdFix schreibt die Ergebnisse jeder **UPDATE** -Aktion in ein Transaktionsprotokoll wie im folgenden Beispiel dargestellt:
  
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