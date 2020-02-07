---
title: Ausgeschlossene und unterstützte Objekte und Attribute für IdFix
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: reference
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
- MOE150
f1.keywords:
- CSH
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
ms.assetid: cc453ae5-fa9b-4836-b0ce-c7e824b1e36d
description: Listet die Attribute auf, die vom IdFix-Tool ausgeschlossen und unterstützt werden.
ms.openlocfilehash: 0203f47864dc4222cd2f95a4e67b2f10bec44f71
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/07/2020
ms.locfileid: "41840142"
---
# <a name="idfix-excluded-and-supported-objects-and-attributes"></a><span data-ttu-id="ed9ca-103">Ausgeschlossene und unterstützte Objekte und Attribute für IdFix</span><span class="sxs-lookup"><span data-stu-id="ed9ca-103">IdFix excluded and supported objects and attributes</span></span>

<span data-ttu-id="ed9ca-104">*Dieser Artikel gilt sowohl für Office 365 Enterprise als auch Microsoft 365 Enterprise*.</span><span class="sxs-lookup"><span data-stu-id="ed9ca-104">*This article applies to both Office 365 Enterprise and Microsoft 365 Enterprise.*</span></span>

<span data-ttu-id="ed9ca-105">Es gibt zwei Regelsätze, die von IdFix verwaltet werden; Multi-Mandanten-und dedizierte/ITAR.</span><span class="sxs-lookup"><span data-stu-id="ed9ca-105">There are two sets of rules maintained by IdFix; Multi-tenant and Dedicated/ITAR.</span></span> <span data-ttu-id="ed9ca-106">Zu diesem Zeitpunkt schließen die beiden Regelsätze dieselben Objekte, Attribute und Attributwerte aus der Suche aus.</span><span class="sxs-lookup"><span data-stu-id="ed9ca-106">At this time, the two rule sets exclude the same objects, attributes, and attribute values from its search.</span></span> <span data-ttu-id="ed9ca-107">Dies kann sich in zukünftigen Versionen ändern.</span><span class="sxs-lookup"><span data-stu-id="ed9ca-107">This may change in future releases.</span></span>
  
## <a name="multi-tenant-and-dedicated-error-exclusions-used-by-idfix"></a><span data-ttu-id="ed9ca-108">Von IdFix verwendete mehrmandantenfähige und dedizierte fehlerausschlüsse</span><span class="sxs-lookup"><span data-stu-id="ed9ca-108">Multi-tenant and Dedicated error exclusions used by IdFix</span></span>
<span data-ttu-id="ed9ca-109">In diesem Abschnitt werden die Objekte, Attribute und Werte aufgelistet, die von IdFix aus der Suche im Verzeichnis ausgeschlossen werden.</span><span class="sxs-lookup"><span data-stu-id="ed9ca-109">This section lists the objects, attributes, and values that IdFix excludes from its search of the directory.</span></span> <span data-ttu-id="ed9ca-110">Das Sternchen (\*) ist ein Platzhalter, der für andere Zeichen ersetzt werden kann.</span><span class="sxs-lookup"><span data-stu-id="ed9ca-110">The asterisk (\*) is a wildcard that can be substituted for other characters.</span></span>
  
### <a name="objects-attributes-and-values-excluded-during-an-idfix-search"></a><span data-ttu-id="ed9ca-111">Während einer IdFix-Suche ausgeschlossene Objekte, Attribute und Werte</span><span class="sxs-lookup"><span data-stu-id="ed9ca-111">Objects, attributes, and values excluded during an IdFix search</span></span>

|<span data-ttu-id="ed9ca-112">**Ausschluss**</span><span class="sxs-lookup"><span data-stu-id="ed9ca-112">**Exclusion**</span></span>|<span data-ttu-id="ed9ca-113">**Beispiel**</span><span class="sxs-lookup"><span data-stu-id="ed9ca-113">**Example**</span></span>|
|:-----|:-----|
|<span data-ttu-id="ed9ca-114">Administrator\*</span><span class="sxs-lookup"><span data-stu-id="ed9ca-114">Admini\*</span></span> |<span data-ttu-id="ed9ca-115">Administrator</span><span class="sxs-lookup"><span data-stu-id="ed9ca-115">Administrator</span></span> |
|<span data-ttu-id="ed9ca-116">CAS_ {\*</span><span class="sxs-lookup"><span data-stu-id="ed9ca-116">CAS_{\*</span></span>  |<span data-ttu-id="ed9ca-117">CAS_ {fe35fc98e69e4d08}</span><span class="sxs-lookup"><span data-stu-id="ed9ca-117">CAS_{fe35fc98e69e4d08}</span></span> |
|<span data-ttu-id="ed9ca-118">DiscoverySearchMailbox\*</span><span class="sxs-lookup"><span data-stu-id="ed9ca-118">DiscoverySearchMailbox\*</span></span>  |<span data-ttu-id="ed9ca-119">DiscoverySearchMailbox</span><span class="sxs-lookup"><span data-stu-id="ed9ca-119">DiscoverySearchMailbox</span></span>  |
|<span data-ttu-id="ed9ca-120">FederatedEmail\*</span><span class="sxs-lookup"><span data-stu-id="ed9ca-120">FederatedEmail\*</span></span> |<span data-ttu-id="ed9ca-121">FederatedEmail.</span><span class="sxs-lookup"><span data-stu-id="ed9ca-121">FederatedEmail.</span></span> <span data-ttu-id="ed9ca-122">*GUID*</span><span class="sxs-lookup"><span data-stu-id="ed9ca-122">*GUID*</span></span> |
|<span data-ttu-id="ed9ca-123">Gast\*</span><span class="sxs-lookup"><span data-stu-id="ed9ca-123">Guest\*</span></span> ||
|<span data-ttu-id="ed9ca-124">HttpConnector\*</span><span class="sxs-lookup"><span data-stu-id="ed9ca-124">HTTPConnector\*</span></span>  |<span data-ttu-id="ed9ca-125">HttpConnector</span><span class="sxs-lookup"><span data-stu-id="ed9ca-125">HTTPConnector</span></span> |
|<span data-ttu-id="ed9ca-126">krbtgt\*</span><span class="sxs-lookup"><span data-stu-id="ed9ca-126">krbtgt\*</span></span> |<span data-ttu-id="ed9ca-127">ms-DS-KrbTgt-Link</span><span class="sxs-lookup"><span data-stu-id="ed9ca-127">ms-DS-KrbTgt-Link</span></span> |
|<span data-ttu-id="ed9ca-128">iusr_\*</span><span class="sxs-lookup"><span data-stu-id="ed9ca-128">iusr_\*</span></span> |<span data-ttu-id="ed9ca-129">IUSR_ *MachineName*</span><span class="sxs-lookup"><span data-stu-id="ed9ca-129">iusr_ *machinename*</span></span> |
|<span data-ttu-id="ed9ca-130">IWAM\*</span><span class="sxs-lookup"><span data-stu-id="ed9ca-130">iwam\*</span></span>  |<span data-ttu-id="ed9ca-131">IWAM_ *MachineName*</span><span class="sxs-lookup"><span data-stu-id="ed9ca-131">IWAM_ *machinename*</span></span> |
|<span data-ttu-id="ed9ca-132">MSOL\*</span><span class="sxs-lookup"><span data-stu-id="ed9ca-132">msol\*</span></span> |<span data-ttu-id="ed9ca-133">MSOL_AD_SYNC</span><span class="sxs-lookup"><span data-stu-id="ed9ca-133">MSOL_AD_SYNC</span></span> |
|<span data-ttu-id="ed9ca-134">support_\*</span><span class="sxs-lookup"><span data-stu-id="ed9ca-134">support_\*</span></span> ||
|<span data-ttu-id="ed9ca-135">System\*</span><span class="sxs-lookup"><span data-stu-id="ed9ca-135">SystemMailbox\*</span></span> |<span data-ttu-id="ed9ca-136">System { *GUID* }</span><span class="sxs-lookup"><span data-stu-id="ed9ca-136">Systemmailbox{ *GUID*  }</span></span>|
|<span data-ttu-id="ed9ca-137">WWIOadmini\*</span><span class="sxs-lookup"><span data-stu-id="ed9ca-137">WWIOadmini\*</span></span>  ||
|\*$ ||
|<span data-ttu-id="ed9ca-138">distinguishedName enthält "\0ACNF:"</span><span class="sxs-lookup"><span data-stu-id="ed9ca-138">distinguishedName contains "\0ACNF:"</span></span>|<span data-ttu-id="ed9ca-139">"\0ACNF: *GUID* "</span><span class="sxs-lookup"><span data-stu-id="ed9ca-139">"\0ACNF: *GUID*  "</span></span> |
|<span data-ttu-id="ed9ca-140">Objekt enthält das IsCriticalSystemObject-Attribut</span><span class="sxs-lookup"><span data-stu-id="ed9ca-140">Object contains the IsCriticalSystemObject attribute</span></span> |<span data-ttu-id="ed9ca-141">Siehe [Attribute isCriticalSystemObject](https://go.microsoft.com/fwlink/p/?LinkId=401169).</span><span class="sxs-lookup"><span data-stu-id="ed9ca-141">See [Attribute isCriticalSystemObject](https://go.microsoft.com/fwlink/p/?LinkId=401169).</span></span> |
   
## <a name="multi-tenant-and-dedicated-objects-and-attributes-checked-by-idfix"></a><span data-ttu-id="ed9ca-142">Mehrinstanzenfähige und dedizierte Objekte und Attribute, die von IdFix überprüft wurden</span><span class="sxs-lookup"><span data-stu-id="ed9ca-142">Multi-Tenant and Dedicated objects and attributes checked by IdFix</span></span>
<span data-ttu-id="ed9ca-143">Die Attribute, die von IdFix auf Fehler überprüft werden, werden im Abschnitt "Verzeichnisobjekt-und Attribut Vorbereitung" unter [Prepare Directory attributes for Synchronization with Office 365 mithilfe des IdFix-Tools](prepare-directory-attributes-for-synch-with-idfix.md)beschrieben.</span><span class="sxs-lookup"><span data-stu-id="ed9ca-143">The attributes that are checked for errors by IdFix are described in the section "Directory object and attribute preparation" in [Prepare directory attributes for synchronization with Office 365 by using the IdFix tool](prepare-directory-attributes-for-synch-with-idfix.md).</span></span>
  

