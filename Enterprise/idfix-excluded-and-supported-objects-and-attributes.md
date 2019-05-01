---
title: Ausgeschlossene und unterstützte Objekte und Attribute für IdFix
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2016
ms.audience: Admin
ms.topic: reference
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
ms.assetid: cc453ae5-fa9b-4836-b0ce-c7e824b1e36d
description: Listet die Attribute auf, die vom IdFix-Tool ausgeschlossen und unterstützt werden.
ms.openlocfilehash: d6b7aac023e9fe96b8308483322e718937ab1355
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/30/2019
ms.locfileid: "33487181"
---
# <a name="idfix-excluded-and-supported-objects-and-attributes"></a><span data-ttu-id="58c5d-103">Ausgeschlossene und unterstützte Objekte und Attribute für IdFix</span><span class="sxs-lookup"><span data-stu-id="58c5d-103">IdFix excluded and supported objects and attributes</span></span>
<span data-ttu-id="58c5d-104">Es gibt zwei Regelsätze, die von IdFix verwaltet werden. Multi-Tenant und Dedicated/ITAR.</span><span class="sxs-lookup"><span data-stu-id="58c5d-104">There are two sets of rules maintained by IdFix; Multi-tenant and Dedicated/ITAR.</span></span> <span data-ttu-id="58c5d-105">Zu diesem Zeitpunkt schließen die beiden Regelsätze dieselben Objekte, Attribute und Attributwerte aus der Suche aus.</span><span class="sxs-lookup"><span data-stu-id="58c5d-105">At this time, the two rule sets exclude the same objects, attributes, and attribute values from its search.</span></span> <span data-ttu-id="58c5d-106">Dies kann sich in zukünftigen Versionen ändern.</span><span class="sxs-lookup"><span data-stu-id="58c5d-106">This may change in future releases.</span></span>
  
## <a name="multi-tenant-and-dedicated-error-exclusions-used-by-idfix"></a><span data-ttu-id="58c5d-107">Mit mehreren Mandanten und dedizierten Fehler Ausschlüssen, die von IdFix verwendet werden</span><span class="sxs-lookup"><span data-stu-id="58c5d-107">Multi-tenant and Dedicated error exclusions used by IdFix</span></span>
<span data-ttu-id="58c5d-108">In diesem Abschnitt werden die Objekte, Attribute und Werte aufgelistet, die von der Suche des Verzeichnisses IdFix ausgeschlossen werden.</span><span class="sxs-lookup"><span data-stu-id="58c5d-108">This section lists the objects, attributes, and values that IdFix excludes from its search of the directory.</span></span> <span data-ttu-id="58c5d-109">Das Sternchen (\*) ist ein Platzhalter, der andere Zeichen ersetzen kann.</span><span class="sxs-lookup"><span data-stu-id="58c5d-109">The asterisk (\*) is a wildcard that can be substituted for other characters.</span></span>
  
### <a name="objects-attributes-and-values-excluded-during-an-idfix-search"></a><span data-ttu-id="58c5d-110">Objekte, Attribute und Werte, die während einer IdFix-Suche ausgeschlossen sind</span><span class="sxs-lookup"><span data-stu-id="58c5d-110">Objects, attributes, and values excluded during an IdFix search</span></span>

|<span data-ttu-id="58c5d-111">**Ausschluss**</span><span class="sxs-lookup"><span data-stu-id="58c5d-111">**Exclusion**</span></span>|<span data-ttu-id="58c5d-112">**Beispiel**</span><span class="sxs-lookup"><span data-stu-id="58c5d-112">**Example**</span></span>|
|:-----|:-----|
|<span data-ttu-id="58c5d-113">Administrator\*</span><span class="sxs-lookup"><span data-stu-id="58c5d-113">Admini\*</span></span> |<span data-ttu-id="58c5d-114">Administrator</span><span class="sxs-lookup"><span data-stu-id="58c5d-114">Administrator</span></span> |
|<span data-ttu-id="58c5d-115">CAS_ {\*</span><span class="sxs-lookup"><span data-stu-id="58c5d-115">CAS_{\*</span></span>  |<span data-ttu-id="58c5d-116">CAS_ {fe35fc98e69e4d08}</span><span class="sxs-lookup"><span data-stu-id="58c5d-116">CAS_{fe35fc98e69e4d08}</span></span> |
|<span data-ttu-id="58c5d-117">DiscoverySearchMailbox\*</span><span class="sxs-lookup"><span data-stu-id="58c5d-117">DiscoverySearchMailbox\*</span></span>  |<span data-ttu-id="58c5d-118">DiscoverySearchMailbox</span><span class="sxs-lookup"><span data-stu-id="58c5d-118">DiscoverySearchMailbox</span></span>  |
|<span data-ttu-id="58c5d-119">FederatedEmail\*</span><span class="sxs-lookup"><span data-stu-id="58c5d-119">FederatedEmail\*</span></span> |<span data-ttu-id="58c5d-120">FederatedEmail.</span><span class="sxs-lookup"><span data-stu-id="58c5d-120">FederatedEmail.</span></span> <span data-ttu-id="58c5d-121">*GUID*</span><span class="sxs-lookup"><span data-stu-id="58c5d-121">*GUID*</span></span> |
|<span data-ttu-id="58c5d-122">Gast\*</span><span class="sxs-lookup"><span data-stu-id="58c5d-122">Guest\*</span></span> ||
|<span data-ttu-id="58c5d-123">HTTPConnector\*</span><span class="sxs-lookup"><span data-stu-id="58c5d-123">HTTPConnector\*</span></span>  |<span data-ttu-id="58c5d-124">HTTPConnector</span><span class="sxs-lookup"><span data-stu-id="58c5d-124">HTTPConnector</span></span> |
|<span data-ttu-id="58c5d-125">krbtgt\*</span><span class="sxs-lookup"><span data-stu-id="58c5d-125">krbtgt\*</span></span> |<span data-ttu-id="58c5d-126">ms-DS-KrbTgt-Link</span><span class="sxs-lookup"><span data-stu-id="58c5d-126">ms-DS-KrbTgt-Link</span></span> |
|<span data-ttu-id="58c5d-127">IUSR\*</span><span class="sxs-lookup"><span data-stu-id="58c5d-127">iusr_\*</span></span> |<span data-ttu-id="58c5d-128">IUSR_- *MachineName*</span><span class="sxs-lookup"><span data-stu-id="58c5d-128">iusr_ *machinename*</span></span> |
|<span data-ttu-id="58c5d-129">IWAM\*</span><span class="sxs-lookup"><span data-stu-id="58c5d-129">iwam\*</span></span>  |<span data-ttu-id="58c5d-130">IWAM_- *MachineName*</span><span class="sxs-lookup"><span data-stu-id="58c5d-130">IWAM_ *machinename*</span></span> |
|<span data-ttu-id="58c5d-131">MSOL\*</span><span class="sxs-lookup"><span data-stu-id="58c5d-131">msol\*</span></span> |<span data-ttu-id="58c5d-132">MSOL_AD_SYNC</span><span class="sxs-lookup"><span data-stu-id="58c5d-132">MSOL_AD_SYNC</span></span> |
|<span data-ttu-id="58c5d-133">Support\*</span><span class="sxs-lookup"><span data-stu-id="58c5d-133">support_\*</span></span> ||
|<span data-ttu-id="58c5d-134">System\*</span><span class="sxs-lookup"><span data-stu-id="58c5d-134">SystemMailbox\*</span></span> |<span data-ttu-id="58c5d-135">System { *GUID* }</span><span class="sxs-lookup"><span data-stu-id="58c5d-135">Systemmailbox{ *GUID*  }</span></span>|
|<span data-ttu-id="58c5d-136">WWIOadmini\*</span><span class="sxs-lookup"><span data-stu-id="58c5d-136">WWIOadmini\*</span></span>  ||
|\*$ ||
|<span data-ttu-id="58c5d-137">distinguishedName enthält "\0ACNF:"</span><span class="sxs-lookup"><span data-stu-id="58c5d-137">distinguishedName contains "\0ACNF:"</span></span>|<span data-ttu-id="58c5d-138">"\0ACNF: *GUID* "</span><span class="sxs-lookup"><span data-stu-id="58c5d-138">"\0ACNF: *GUID*  "</span></span> |
|<span data-ttu-id="58c5d-139">Objekt enthält das IsCriticalSystemObject-Attribut</span><span class="sxs-lookup"><span data-stu-id="58c5d-139">Object contains the IsCriticalSystemObject attribute</span></span> |<span data-ttu-id="58c5d-140">Weitere Informationen finden Sie unter [Attribut isCriticalSystemObject](https://go.microsoft.com/fwlink/p/?LinkId=401169).</span><span class="sxs-lookup"><span data-stu-id="58c5d-140">See [Attribute isCriticalSystemObject](https://go.microsoft.com/fwlink/p/?LinkId=401169).</span></span> |
   
## <a name="multi-tenant-and-dedicated-objects-and-attributes-checked-by-idfix"></a><span data-ttu-id="58c5d-141">Mehrinstanzenfähige und dedizierte Objekte und Attribute, die von IdFix überprüft wurden</span><span class="sxs-lookup"><span data-stu-id="58c5d-141">Multi-Tenant and Dedicated objects and attributes checked by IdFix</span></span>
<span data-ttu-id="58c5d-142">Die Attribute, die von IdFix auf Fehler überprüft werden, werden im Abschnitt "Verzeichnisobjekt-und Attribut Vorbereitung" unter [Vorbereiten von Verzeichnisattributen für die Synchronisierung mit Office 365 mithilfe des IdFix-Tools](prepare-directory-attributes-for-synch-with-idfix.md)beschrieben.</span><span class="sxs-lookup"><span data-stu-id="58c5d-142">The attributes that are checked for errors by IdFix are described in the section "Directory object and attribute preparation" in [Prepare directory attributes for synchronization with Office 365 by using the IdFix tool](prepare-directory-attributes-for-synch-with-idfix.md).</span></span>
  

