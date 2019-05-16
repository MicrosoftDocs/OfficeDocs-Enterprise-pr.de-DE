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
description: Enthält ein Beispiel und beschreibt die Benennungskonvention und die Standardprotokoll Ebene des Office 365-IdFix-Transaktionsprotokolls.
ms.openlocfilehash: 0c6f2dd64cb406681c0a98099b2a42887ee79c25
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "34067261"
---
# <a name="office-365-idfix-transaction-log"></a><span data-ttu-id="439ed-103">Office 365 IdFix-Transaktionsprotokoll</span><span class="sxs-lookup"><span data-stu-id="439ed-103">Office 365 IdFix transaction log</span></span>

<span data-ttu-id="439ed-104">Enthält ein Beispiel und beschreibt die Benennungskonvention und die Standardprotokoll Ebene des Office 365-IdFix-Transaktionsprotokolls.</span><span class="sxs-lookup"><span data-stu-id="439ed-104">Provides an example and describes the naming convention and default log level of the Office 365 IdFix transaction log.</span></span>
  
## <a name="idfix-transaction-log-location"></a><span data-ttu-id="439ed-105">Speicherort des IdFix-Transaktionsprotokolls</span><span class="sxs-lookup"><span data-stu-id="439ed-105">IdFix transaction log location</span></span>

<span data-ttu-id="439ed-106">Das Office 365-IdFix-Tool erstellt jedes Mal, wenn Sie auf IdFix **anwenden** klicken und Änderungen an der Active Directory-Gesamtstruktur anwenden, ein neues Transaktionsprotokoll.</span><span class="sxs-lookup"><span data-stu-id="439ed-106">The Office 365 IdFix tool creates a new transaction log each time you click **Apply** in IdFix and apply changes to the Active Directory forest.</span></span> <span data-ttu-id="439ed-107">Das Transaktionsprotokoll wird im gleichen Ordner gespeichert, in dem Sie IdFix installiert haben.</span><span class="sxs-lookup"><span data-stu-id="439ed-107">The transaction log is saved in the same folder where you installed IdFix.</span></span> <span data-ttu-id="439ed-108">Standardmäßig ist dieser Ordner C:\Deployment Tools\IDFix.</span><span class="sxs-lookup"><span data-stu-id="439ed-108">By default, this folder is C:\Deployment Tools\IDFix.</span></span> <span data-ttu-id="439ed-109">Der Name der Transaktionsprotokolldatei verwendet ein Datums-und Zeitstempelformat, beispielsweise Verbose 6-1-2018 6-17-22 pm gibt eine Datei an, die am 1. Juni 2018 bei 6:17:22 pm generiert wurde.</span><span class="sxs-lookup"><span data-stu-id="439ed-109">The transaction log file name uses a date and time stamp format, for example, Verbose 6-1-2018 6-17-22 PM indicates a file that was generated at June 1, 2018 at 6:17:22 PM.</span></span> <span data-ttu-id="439ed-110">Verbose gibt den Protokolliergrad an.</span><span class="sxs-lookup"><span data-stu-id="439ed-110">Verbose indicates the logging level.</span></span> 
  
## <a name="idfix-transaction-log-logging-level"></a><span data-ttu-id="439ed-111">IdFix-Transaktionsprotokoll-Protokolliergrad</span><span class="sxs-lookup"><span data-stu-id="439ed-111">IdFix transaction log logging level</span></span>

<span data-ttu-id="439ed-112">Das Wort Verbose im Namen der Transaktionsprotokolldatei gibt die Protokollierungsebene in der Datei an.</span><span class="sxs-lookup"><span data-stu-id="439ed-112">The word verbose in the transaction log file name indicates the level of logging in the file.</span></span> <span data-ttu-id="439ed-113">Verbose bedeutet, dass die maximale Menge an Informationen im Protokoll erfasst wird.</span><span class="sxs-lookup"><span data-stu-id="439ed-113">Verbose means that the maximum amount of information is captured in the log.</span></span> <span data-ttu-id="439ed-114">Dies ist die Standard Protokollierungsstufe.</span><span class="sxs-lookup"><span data-stu-id="439ed-114">This is the default logging level.</span></span> <span data-ttu-id="439ed-115">Derzeit ist es nicht möglich, den Protokolliergrad zu ändern.</span><span class="sxs-lookup"><span data-stu-id="439ed-115">At this time, you cannot change the logging level.</span></span>
  
## <a name="idfix-transaction-log-format"></a><span data-ttu-id="439ed-116">IdFix-Transaktionsprotokollformat</span><span class="sxs-lookup"><span data-stu-id="439ed-116">IdFix transaction log format</span></span>

<span data-ttu-id="439ed-117">IdFix schreibt die Ergebnisse der einzelnen **Update** -Aktionen in ein Transaktionsprotokoll, wie im folgenden Beispiel gezeigt:</span><span class="sxs-lookup"><span data-stu-id="439ed-117">IdFix writes the results of each **UPDATE** action to a transaction log as shown in the following example:</span></span>
  
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