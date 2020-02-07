---
title: Office 365 IdFix-Transaktionsprotokoll
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: reference
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
ms.assetid: d58b7d45-7947-4193-9456-82ba76f42d89
description: Enthält ein Beispiel und beschreibt die Benennungskonvention und die Standardprotokoll Ebene des Office 365 IdFix-Transaktionsprotokolls.
ms.openlocfilehash: fb294095dc5b163965660546f5033a845d6cb0b4
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/07/2020
ms.locfileid: "41840112"
---
# <a name="office-365-idfix-transaction-log"></a><span data-ttu-id="fff92-103">Office 365 IdFix-Transaktionsprotokoll</span><span class="sxs-lookup"><span data-stu-id="fff92-103">Office 365 IdFix transaction log</span></span>

<span data-ttu-id="fff92-104">*Dieser Artikel gilt sowohl für Office 365 Enterprise als auch Microsoft 365 Enterprise*.</span><span class="sxs-lookup"><span data-stu-id="fff92-104">*This article applies to both Office 365 Enterprise and Microsoft 365 Enterprise.*</span></span>

<span data-ttu-id="fff92-105">Enthält ein Beispiel und beschreibt die Benennungskonvention und die Standardprotokoll Ebene des Office 365 IdFix-Transaktionsprotokolls.</span><span class="sxs-lookup"><span data-stu-id="fff92-105">Provides an example and describes the naming convention and default log level of the Office 365 IdFix transaction log.</span></span>
  
## <a name="idfix-transaction-log-location"></a><span data-ttu-id="fff92-106">Speicherort des IdFix-Transaktionsprotokolls</span><span class="sxs-lookup"><span data-stu-id="fff92-106">IdFix transaction log location</span></span>

<span data-ttu-id="fff92-107">Das Office 365 IdFix-Tool erstellt jedes Mal ein neues Transaktionsprotokoll, wenn Sie auf in IdFix **anwenden** klicken und Änderungen auf die Active Directory Gesamtstruktur anwenden.</span><span class="sxs-lookup"><span data-stu-id="fff92-107">The Office 365 IdFix tool creates a new transaction log each time you click **Apply** in IdFix and apply changes to the Active Directory forest.</span></span> <span data-ttu-id="fff92-108">Das Transaktionsprotokoll wird in demselben Ordner gespeichert, in dem Sie IdFix installiert haben.</span><span class="sxs-lookup"><span data-stu-id="fff92-108">The transaction log is saved in the same folder where you installed IdFix.</span></span> <span data-ttu-id="fff92-109">Standardmäßig lautet dieser Ordner C:\Deployment Tools\IDFix.</span><span class="sxs-lookup"><span data-stu-id="fff92-109">By default, this folder is C:\Deployment Tools\IDFix.</span></span> <span data-ttu-id="fff92-110">Der Name der Transaktionsprotokolldatei verwendet ein Datums-und Zeitstempelformat, beispielsweise Verbose 6-1-2018 6-17-22 Uhr gibt eine Datei an, die am 1. Juni 2018 um 6:17:22 Uhr generiert wurde.</span><span class="sxs-lookup"><span data-stu-id="fff92-110">The transaction log file name uses a date and time stamp format, for example, Verbose 6-1-2018 6-17-22 PM indicates a file that was generated at June 1, 2018 at 6:17:22 PM.</span></span> <span data-ttu-id="fff92-111">Verbose gibt die Protokollierungsstufe an.</span><span class="sxs-lookup"><span data-stu-id="fff92-111">Verbose indicates the logging level.</span></span> 
  
## <a name="idfix-transaction-log-logging-level"></a><span data-ttu-id="fff92-112">IdFix-Transaktionsprotokoll Protokollierungsstufe</span><span class="sxs-lookup"><span data-stu-id="fff92-112">IdFix transaction log logging level</span></span>

<span data-ttu-id="fff92-113">Das Wort Verbose im Namen der Transaktionsprotokolldatei gibt die Protokollierungsebene in der Datei an.</span><span class="sxs-lookup"><span data-stu-id="fff92-113">The word verbose in the transaction log file name indicates the level of logging in the file.</span></span> <span data-ttu-id="fff92-114">Verbose bedeutet, dass die maximale Menge an Informationen im Protokoll erfasst wird.</span><span class="sxs-lookup"><span data-stu-id="fff92-114">Verbose means that the maximum amount of information is captured in the log.</span></span> <span data-ttu-id="fff92-115">Dies ist die Standard Protokollierungsstufe.</span><span class="sxs-lookup"><span data-stu-id="fff92-115">This is the default logging level.</span></span> <span data-ttu-id="fff92-116">Zu diesem Zeitpunkt können Sie die Protokollierungsstufe nicht ändern.</span><span class="sxs-lookup"><span data-stu-id="fff92-116">At this time, you cannot change the logging level.</span></span>
  
## <a name="idfix-transaction-log-format"></a><span data-ttu-id="fff92-117">IdFix-Transaktionsprotokollformat</span><span class="sxs-lookup"><span data-stu-id="fff92-117">IdFix transaction log format</span></span>

<span data-ttu-id="fff92-118">IdFix schreibt die Ergebnisse der einzelnen **Update** Aktionen wie im folgenden Beispiel gezeigt in ein Transaktionsprotokoll:</span><span class="sxs-lookup"><span data-stu-id="fff92-118">IdFix writes the results of each **UPDATE** action to a transaction log as shown in the following example:</span></span>
  
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