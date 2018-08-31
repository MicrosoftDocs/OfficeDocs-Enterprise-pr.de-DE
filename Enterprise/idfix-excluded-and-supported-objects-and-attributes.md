---
title: IdFix ausgeschlossene und unterstützte Objekte und Attribute
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
ms.assetid: cc453ae5-fa9b-4836-b0ce-c7e824b1e36d
description: Werden die Attribute aufgeführt, die ausgeschlossen und von IdFix-Tools unterstützt werden.
ms.openlocfilehash: de8d57bb8ad9a3097ec9da3ff2a485095a140a42
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540870"
---
# <a name="idfix-excluded-and-supported-objects-and-attributes"></a><span data-ttu-id="55b99-103">IdFix ausgeschlossene und unterstützte Objekte und Attribute</span><span class="sxs-lookup"><span data-stu-id="55b99-103">IdFix excluded and supported objects and attributes</span></span>
<span data-ttu-id="55b99-p101">Es gibt zwei durch IdFix gewartete Regelsätze: mehrinstanzenfähig und dediziert/ITAR. Derzeit schließen die zwei Regelsätze dieselben Objekte, Attribute und Attributwerte aus der Suche aus. Dies kann sich in zukünftigen Versionen ändern.</span><span class="sxs-lookup"><span data-stu-id="55b99-p101">There are two sets of rules maintained by IdFix; Multi-tenant and Dedicated/ITAR. At this time, the two rule sets exclude the same objects, attributes, and attribute values from its search. This may change in future releases.</span></span>
  
## <a name="multi-tenant-and-dedicated-error-exclusions-used-by-idfix"></a><span data-ttu-id="55b99-107">Durch IdFix verwendete mehrinstanzenfähige und dedizierte Fehlerausschlüsse</span><span class="sxs-lookup"><span data-stu-id="55b99-107">Multi-tenant and Dedicated error exclusions used by IdFix</span></span>
<span data-ttu-id="55b99-p102">Dieser Abschnitt enthält die Objekte, Attribute und Werte, die von der Suche des Verzeichnisses IdFix ausschließt. Das Sternchen (\*) ist ein Platzhalter, der für andere Zeichen ersetzt werden kann.</span><span class="sxs-lookup"><span data-stu-id="55b99-p102">This section lists the objects, attributes, and values that IdFix excludes from its search of the directory. The asterisk (\*) is a wildcard that can be substituted for other characters.</span></span>
  
### <a name="objects-attributes-and-values-excluded-during-an-idfix-search"></a><span data-ttu-id="55b99-110">Während einer IdFix-Suche ausgeschlossene Objekte, Attribute und Werte</span><span class="sxs-lookup"><span data-stu-id="55b99-110">Objects, attributes, and values excluded during an IdFix search</span></span>

|<span data-ttu-id="55b99-111">**Ausschluss**</span><span class="sxs-lookup"><span data-stu-id="55b99-111">**Exclusion**</span></span>|<span data-ttu-id="55b99-112">**Beispiel**</span><span class="sxs-lookup"><span data-stu-id="55b99-112">**Example**</span></span>|
|:-----|:-----|
|<span data-ttu-id="55b99-113">Gefährdeten\*</span><span class="sxs-lookup"><span data-stu-id="55b99-113">Admini\*</span></span> |<span data-ttu-id="55b99-114">Administrator</span><span class="sxs-lookup"><span data-stu-id="55b99-114">Administrator</span></span> |
|<span data-ttu-id="55b99-115">{CAS_\*</span><span class="sxs-lookup"><span data-stu-id="55b99-115">CAS_{\*</span></span>  |<span data-ttu-id="55b99-116">CAS_{fe35fc98e69e4d08}</span><span class="sxs-lookup"><span data-stu-id="55b99-116">CAS_{fe35fc98e69e4d08}</span></span> |
|<span data-ttu-id="55b99-117">DiscoverySearchMailbox\*</span><span class="sxs-lookup"><span data-stu-id="55b99-117">DiscoverySearchMailbox\*</span></span>  |<span data-ttu-id="55b99-118">DiscoverySearchMailbox</span><span class="sxs-lookup"><span data-stu-id="55b99-118">DiscoverySearchMailbox</span></span>  |
|<span data-ttu-id="55b99-119">FederatedEmail\*</span><span class="sxs-lookup"><span data-stu-id="55b99-119">FederatedEmail\*</span></span> |<span data-ttu-id="55b99-p103">FederatedEmail. *GUID*</span><span class="sxs-lookup"><span data-stu-id="55b99-p103">FederatedEmail. *GUID*</span></span> |
|<span data-ttu-id="55b99-122">Gast\*</span><span class="sxs-lookup"><span data-stu-id="55b99-122">Guest\*</span></span> ||
|<span data-ttu-id="55b99-123">HTTPConnector\*</span><span class="sxs-lookup"><span data-stu-id="55b99-123">HTTPConnector\*</span></span>  |<span data-ttu-id="55b99-124">HTTPConnector</span><span class="sxs-lookup"><span data-stu-id="55b99-124">HTTPConnector</span></span> |
|<span data-ttu-id="55b99-125">KRBTGT\*</span><span class="sxs-lookup"><span data-stu-id="55b99-125">krbtgt\*</span></span> |<span data-ttu-id="55b99-126">ms-DS-KrbTgt-Link</span><span class="sxs-lookup"><span data-stu-id="55b99-126">ms-DS-KrbTgt-Link</span></span> |
|<span data-ttu-id="55b99-127">IUSR_\*</span><span class="sxs-lookup"><span data-stu-id="55b99-127">iusr_\*</span></span> |<span data-ttu-id="55b99-128">IUSR_ *Computername*</span><span class="sxs-lookup"><span data-stu-id="55b99-128">iusr_ *machinename*</span></span> |
|<span data-ttu-id="55b99-129">IWAM\*</span><span class="sxs-lookup"><span data-stu-id="55b99-129">iwam\*</span></span>  |<span data-ttu-id="55b99-130">IWAM_ *Computername*</span><span class="sxs-lookup"><span data-stu-id="55b99-130">IWAM_ *machinename*</span></span> |
|<span data-ttu-id="55b99-131">msol\*</span><span class="sxs-lookup"><span data-stu-id="55b99-131">msol\*</span></span> |<span data-ttu-id="55b99-132">MSOL_AD_SYNC</span><span class="sxs-lookup"><span data-stu-id="55b99-132">MSOL_AD_SYNC</span></span> |
|<span data-ttu-id="55b99-133">Support_\*</span><span class="sxs-lookup"><span data-stu-id="55b99-133">support_\*</span></span> ||
|<span data-ttu-id="55b99-134">SystemMailbox\*</span><span class="sxs-lookup"><span data-stu-id="55b99-134">SystemMailbox\*</span></span> |<span data-ttu-id="55b99-135">SystemMailbox { *GUID* }</span><span class="sxs-lookup"><span data-stu-id="55b99-135">Systemmailbox{ *GUID*  }</span></span>|
|<span data-ttu-id="55b99-136">WWIOadmini\*</span><span class="sxs-lookup"><span data-stu-id="55b99-136">WWIOadmini\*</span></span>  ||
|\*$ ||
|<span data-ttu-id="55b99-137">DistinguishedName enthält "\0ACNF:"</span><span class="sxs-lookup"><span data-stu-id="55b99-137">distinguishedName contains "\0ACNF:"</span></span>|<span data-ttu-id="55b99-138">"\0ACNF: *GUID* "</span><span class="sxs-lookup"><span data-stu-id="55b99-138">"\0ACNF: *GUID*  "</span></span> |
|<span data-ttu-id="55b99-139">Objekt enthält das "IsCriticalSystemObject"-Attribut</span><span class="sxs-lookup"><span data-stu-id="55b99-139">Object contains the IsCriticalSystemObject attribute</span></span> |<span data-ttu-id="55b99-140">Siehe [Attribut "isCriticalSystemObject"](https://go.microsoft.com/fwlink/p/?LinkId=401169).</span><span class="sxs-lookup"><span data-stu-id="55b99-140">See [Attribute isCriticalSystemObject](https://go.microsoft.com/fwlink/p/?LinkId=401169).</span></span> |
   
## <a name="multi-tenant-and-dedicated-objects-and-attributes-checked-by-idfix"></a><span data-ttu-id="55b99-141">Durch IdFix überprüfte mehrinstanzenfähige und dedizierte Objekte und Attribute</span><span class="sxs-lookup"><span data-stu-id="55b99-141">Multi-Tenant and Dedicated objects and attributes checked by IdFix</span></span>
<span data-ttu-id="55b99-142">Die Attribute, die durch IdFix auf Fehler überprüft werden, werden im Abschnitt "Directory-Objekt und die attributvorbereitung" in [die Freigabe Vorbereiten von Verzeichnisattributen für die Synchronisierung mit Office 365 mithilfe des IdFix-Tools](prepare-directory-attributes-for-synch-with-idfix.md)beschrieben.</span><span class="sxs-lookup"><span data-stu-id="55b99-142">The attributes that are checked for errors by IdFix are described in the section "Directory object and attribute preparation" in [Prepare directory attributes for synchronization with Office 365 by using the IdFix tool](prepare-directory-attributes-for-synch-with-idfix.md).</span></span>
  

