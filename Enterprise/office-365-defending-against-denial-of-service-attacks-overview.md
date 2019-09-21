---
title: Abwehr von Denial-of-Service-Angriffen in Office 365
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
description: Eine Übersicht über DOS-Angriffe (Denial of Service).
ms.openlocfilehash: 55fffccfc59f13d32cdd19930320c1df1cf58461
ms.sourcegitcommit: 55a046bdf49bf7c62ab74da73be1fd1cf6f0ad86
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/20/2019
ms.locfileid: "37067463"
---
# <a name="defend-against-denial-of-service-attacks-in-office-365"></a><span data-ttu-id="8ab7c-103">Abwehr von Denial-of-Service-Angriffen in Office 365</span><span class="sxs-lookup"><span data-stu-id="8ab7c-103">Defend Against Denial-of-Service Attacks in Office 365</span></span>

## <a name="introduction"></a><span data-ttu-id="8ab7c-104">Einführung</span><span class="sxs-lookup"><span data-stu-id="8ab7c-104">Introduction</span></span>

<span data-ttu-id="8ab7c-105">Microsoft bietet eine vertrauenswürdige Infrastruktur für mehr als 200 Cloud-Dienste, die in einer globalen Cloud-Infrastruktur mit mehr als 100 Rechenzentren gehostet werden.</span><span class="sxs-lookup"><span data-stu-id="8ab7c-105">Microsoft delivers a trustworthy infrastructure for more than 200 cloud services hosted in a global cloud infrastructure of more than 100 datacenters.</span></span> <span data-ttu-id="8ab7c-106">Zu diesen zählen:</span><span class="sxs-lookup"><span data-stu-id="8ab7c-106">These include:</span></span>

- <span data-ttu-id="8ab7c-107">Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="8ab7c-107">Microsoft Azure</span></span>
- <span data-ttu-id="8ab7c-108">Microsoft Bing</span><span class="sxs-lookup"><span data-stu-id="8ab7c-108">Microsoft Bing</span></span>
- <span data-ttu-id="8ab7c-109">Microsoft Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="8ab7c-109">Microsoft Dynamics 365</span></span>
- <span data-ttu-id="8ab7c-110">Microsoft Office 365</span><span class="sxs-lookup"><span data-stu-id="8ab7c-110">Microsoft Office 365</span></span>
- <span data-ttu-id="8ab7c-111">Microsoft OneDrive</span><span class="sxs-lookup"><span data-stu-id="8ab7c-111">Microsoft OneDrive</span></span>
- <span data-ttu-id="8ab7c-112">Skype</span><span class="sxs-lookup"><span data-stu-id="8ab7c-112">Skype</span></span>
- <span data-ttu-id="8ab7c-113">Xbox Live</span><span class="sxs-lookup"><span data-stu-id="8ab7c-113">Xbox Live</span></span>

<span data-ttu-id="8ab7c-114">Als globale Organisation mit einer bedeutenden Internetpräsenz und vielen prominenten Interneteigenschaften, die Cloud-Dienste bereitstellen, ist Microsoft ein großes, gemeinsames Ziel für Hacker und andere böswillige Personen.</span><span class="sxs-lookup"><span data-stu-id="8ab7c-114">As a global organization with a significant Internet presence and many prominent Internet properties that provide cloud services, Microsoft is a large, common target for hackers and other malicious individuals.</span></span> <span data-ttu-id="8ab7c-115">Die Netzwerk Kommunikationsschicht zwischen Clients und der Microsoft-Cloud gehört zu den größten Zielen böswilliger Angriffe.</span><span class="sxs-lookup"><span data-stu-id="8ab7c-115">The network communication layer between clients and the Microsoft Cloud is one of the biggest targets of malicious attacks.</span></span> <span data-ttu-id="8ab7c-116">Tatsächlich ist Microsoft ständig und dauerhaft unter irgendeiner Form von netzwerkbasierter Cyberangriff.</span><span class="sxs-lookup"><span data-stu-id="8ab7c-116">In fact, Microsoft is continuously and persistently under some form of network-based cyberattack.</span></span> <span data-ttu-id="8ab7c-117">In diesem Sinne verwendet Microsoft umfassende Sicherheitsprinzipien zum Schutz seiner Cloud-Dienste und-Netzwerke.</span><span class="sxs-lookup"><span data-stu-id="8ab7c-117">In line with this, Microsoft uses defense-in-depth security principles to protect its cloud services and networks.</span></span> <span data-ttu-id="8ab7c-118">Ohne zuverlässige und beständige mildernde Systeme, die sich gegen diese Angriffe wehren, wären die Cloud-Dienste von Microsoft Offline und für Kunden nicht verfügbar.</span><span class="sxs-lookup"><span data-stu-id="8ab7c-118">Without reliable and persistent mitigation systems that defend against these attacks, Microsoft's cloud services would be offline and unavailable to customers.</span></span>

## <a name="definition-and-symptoms-of-denial-of-service-attacks"></a><span data-ttu-id="8ab7c-119">Definition und Symptome von Denial-of-Service-Angriffen</span><span class="sxs-lookup"><span data-stu-id="8ab7c-119">Definition and Symptoms of Denial-of-Service Attacks</span></span>

<span data-ttu-id="8ab7c-120">Eine Möglichkeit zum angreifen von Netzwerkdiensten besteht darin, viele Anforderungen an Diensthosts zu erstellen, um das Netzwerk und die Server zu überlasten, um legitimen Benutzern den Dienst zu verweigern.</span><span class="sxs-lookup"><span data-stu-id="8ab7c-120">One way to attack network services is to create many requests against service hosts to overwhelm the network and servers to deny service to legitimate users.</span></span> <span data-ttu-id="8ab7c-121">Dies wird als DOS-Angriff (Denial of Service) bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="8ab7c-121">This is referred to as a denial-of-service (DoS) attack.</span></span> <span data-ttu-id="8ab7c-122">Wenn der Angriff von mehreren Akteuren, Endpunkten und/oder Vektoren ausgeführt wird, wird er als Distributed Denial-of-Service (DDoS)-Angriff bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="8ab7c-122">When the attack is performed by multiple actors, endpoints, and/or vectors, it is referred to as a distributed denial-of-service (DDoS) attack.</span></span> <span data-ttu-id="8ab7c-123">Obwohl die Mittel, Motive und Ziele unterschiedlich sind, bestehen DOS-und DDoS-Angriffe im Allgemeinen aus Anstrengungen, um zu verhindern, dass eine Internet-Website oder ein Dienst ordnungsgemäß oder überhaupt vorübergehend oder unbegrenzt funktioniert.</span><span class="sxs-lookup"><span data-stu-id="8ab7c-123">Although the means, motives, and targets vary, DoS and DDoS attacks generally consist of efforts to prevent an Internet site or service from functioning correctly or at all, either temporarily or indefinitely.</span></span>

<span data-ttu-id="8ab7c-124">Das US-amerikanische [Computer Notfall Bereitschafts Team](https://www.us-cert.gov/) (US-CERT) definiert die Symptome von DOS-Angriffen, die Folgendes umfassen:</span><span class="sxs-lookup"><span data-stu-id="8ab7c-124">The [United States Computer Emergency Readiness Team](https://www.us-cert.gov/) (US-CERT) defines symptoms of DoS attacks to include:</span></span>

- <span data-ttu-id="8ab7c-125">Ungewöhnlich langsame Netzwerkleistung (beim Öffnen von Dateien oder Zugriff auf Internet Websites)</span><span class="sxs-lookup"><span data-stu-id="8ab7c-125">Unusually slow network performance (when opening files or accessing Internet sites)</span></span>
- <span data-ttu-id="8ab7c-126">Nichtverfügbarkeit einer Website</span><span class="sxs-lookup"><span data-stu-id="8ab7c-126">Unavailability of a Web site</span></span>
- <span data-ttu-id="8ab7c-127">Unfähigkeit, auf eine Website zuzugreifen</span><span class="sxs-lookup"><span data-stu-id="8ab7c-127">Inability to access a Web site</span></span>
- <span data-ttu-id="8ab7c-128">Drastische Verstärkung des empfangenen Spam</span><span class="sxs-lookup"><span data-stu-id="8ab7c-128">Dramatic increase in received spam</span></span>
- <span data-ttu-id="8ab7c-129">Trennen einer drahtlosen oder verkabelten Internet Verbindung</span><span class="sxs-lookup"><span data-stu-id="8ab7c-129">Disconnection of a wireless or wired Internet connection</span></span>
- <span data-ttu-id="8ab7c-130">Langfristiger Verlust des Zugriffs auf das Web oder Internetdienste</span><span class="sxs-lookup"><span data-stu-id="8ab7c-130">Long-term loss of access to the Web or any Internet services</span></span>

## <a name="related-topics"></a><span data-ttu-id="8ab7c-131">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="8ab7c-131">Related Topics</span></span>

- [<span data-ttu-id="8ab7c-132">Wichtige Grundsätze zum Schutz vor Denial-of-Service-Angriffen</span><span class="sxs-lookup"><span data-stu-id="8ab7c-132">Core Principles of Defense Against Denial-of-Service Attacks</span></span>](office-365-core-principles-of-defense-against-dos-attacks.md)
- [<span data-ttu-id="8ab7c-133">Denial-of-Service-Verteidigungsstrategie von Microsoft</span><span class="sxs-lookup"><span data-stu-id="8ab7c-133">Microsoft's Denial-of-Service Defense Strategy</span></span>](office-365-microsoft-dos-defense-strategy.md)
- [<span data-ttu-id="8ab7c-134">Schützen von Microsoft Cloud Services vor Denial-of-Service-Angriffen</span><span class="sxs-lookup"><span data-stu-id="8ab7c-134">Defending Microsoft Cloud Services Against Denial-of-Service Attacks</span></span>](office-365-defending-cloud-services-against-dos-attacks.md)
