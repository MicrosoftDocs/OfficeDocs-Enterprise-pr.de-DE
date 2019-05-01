---
title: Hybrid Cloud-Szenarien für Azure-PaaS
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/30/2018
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 5f4f5d0d-4638-48e8-a517-bd804856b617
description: 'Zusammenfassung: Grundlegende Informationen zur Hybrid-Architektur und -szenarien für PaaS-basierte Cloudangebote von Microsoft in Azure.'
ms.openlocfilehash: f4d90d51a7627063fae6fd168681bdf96cb4d6bc
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/30/2019
ms.locfileid: "33491196"
---
# <a name="hybrid-cloud-scenarios-for-azure-paas"></a><span data-ttu-id="f5b30-103">Hybrid Cloud-Szenarien für Azure PaaS</span><span class="sxs-lookup"><span data-stu-id="f5b30-103">Hybrid cloud scenarios for Azure PaaS</span></span>

 <span data-ttu-id="f5b30-104">**Zusammenfassung:** Grundlegende Informationen zur Hybrid-Architektur und -szenarien für PaaS-basierte Cloudangebote von Microsoft in Azure.</span><span class="sxs-lookup"><span data-stu-id="f5b30-104">**Summary:** Understand the hybrid architecture and scenarios for Microsoft's Platform as a Service (PaaS)-based cloud offerings in Azure.</span></span>
  
<span data-ttu-id="f5b30-105">Kombinieren Sie lokale Daten oder Computingressourcen mit neuen oder konvertierten Anwendungen, die in Azure PaaS ausgeführt werden und Cloudleistung, -zuverlässigkeit und -skalierung nutzen sowie bessere Unterstützung für mobile Benutzer bieten können.</span><span class="sxs-lookup"><span data-stu-id="f5b30-105">Combine on-premises data or computing resources with new or converted applications running in Azure PaaS, which can take advantage of cloud performance, reliability, and scale and provide better support for mobile users.</span></span> 
  
## <a name="azure-paas-hybrid-scenario-architecture"></a><span data-ttu-id="f5b30-106">Architektur für Azure PaaS-Hybridszenario</span><span class="sxs-lookup"><span data-stu-id="f5b30-106">Azure PaaS hybrid scenario architecture</span></span>

<span data-ttu-id="f5b30-107">Abbildung 1 zeigt die Architektur der PaaS-basierten Hybridszenarien von Microsoft in Azure.</span><span class="sxs-lookup"><span data-stu-id="f5b30-107">Figure 1 shows the architecture of Microsoft PaaS-based hybrid scenarios in Azure.</span></span>
  
<span data-ttu-id="f5b30-108">**Abbildung 1: Microsoft PaaS-basierte Hybridszenarien in Azure**</span><span class="sxs-lookup"><span data-stu-id="f5b30-108">**Figure 1: Microsoft PaaS-based hybrid scenarios in Azure**</span></span>

![Microsoft PaaS-basierte Hybridszenarien in Azure](media/Hybrid-Poster/Hybrid-Cloud-Stack-PaaS.png)
  
<span data-ttu-id="f5b30-110">Für jede Schicht der Architektur:</span><span class="sxs-lookup"><span data-stu-id="f5b30-110">For each layer of the architecture:</span></span>
  
- <span data-ttu-id="f5b30-111">Apps und Szenarien</span><span class="sxs-lookup"><span data-stu-id="f5b30-111">Apps and scenarios</span></span>
    
    <span data-ttu-id="f5b30-112">Eine hybride PaaS-Anwendung wird in Azure ausgeführt und nutzt lokale Compute- oder Speicherressourcen.</span><span class="sxs-lookup"><span data-stu-id="f5b30-112">A hybrid PaaS application runs in Azure and uses on-premises compute or storage resources.</span></span>
    
- <span data-ttu-id="f5b30-113">Identität</span><span class="sxs-lookup"><span data-stu-id="f5b30-113">Identity</span></span>
    
    <span data-ttu-id="f5b30-114">Besteht entweder aus einer Verzeichnissynchronisierung oder aus einem Partnerverbund mit einem Drittanbieter-Identitätsanbieter.</span><span class="sxs-lookup"><span data-stu-id="f5b30-114">Consists of either directory synchronization or federation with a third-party identity provider.</span></span>
    
- <span data-ttu-id="f5b30-115">Netzwerk</span><span class="sxs-lookup"><span data-stu-id="f5b30-115">Network</span></span>
    
    <span data-ttu-id="f5b30-p101">Besteht aus Ihrem vorhandenen Internetzugang oder einer ExpressRoute-Verbindung mit öffentlichem Peering zu Azure PaaS. Sie müssen eine Möglichkeit für die Azure PaaS-Anwendung für den Zugriff auf die lokale Compute- oder Speicherressource hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="f5b30-p101">Consists of either your existing Internet pipe or an ExpressRoute connection with public peering to Azure PaaS. You must include a way for the Azure PaaS application to access the on-premises compute or storage resource.</span></span>
    
- <span data-ttu-id="f5b30-118">Lokal</span><span class="sxs-lookup"><span data-stu-id="f5b30-118">On-premises</span></span>
    
    <span data-ttu-id="f5b30-119">Besteht aus der Identitäts- und Sicherheitsinfrastruktur sowie vorhandenen branchenspezifischen Anwendungen oder Datenbankserver, auf die eine Azure PaaS-Anwendung sicher zugreifen kann.</span><span class="sxs-lookup"><span data-stu-id="f5b30-119">Consists of identity and security infrastructure and existing line of business (LOB) applications or database servers, which an Azure PaaS application can securely access.</span></span>
    
## <a name="azure-paas-hybrid-application"></a><span data-ttu-id="f5b30-120">Azure PaaS-Hybridanwendung</span><span class="sxs-lookup"><span data-stu-id="f5b30-120">Azure PaaS hybrid application</span></span>

<span data-ttu-id="f5b30-121">Abbildung 2 zeigt die Konfiguration einer Hybridanwendung, die in Azure ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="f5b30-121">Figure 2 shows the configuration of a hybrid application running in Azure.</span></span>
  
<span data-ttu-id="f5b30-122">**Abbildung 2: Azure PaaS-basierte Hybridanwendung**</span><span class="sxs-lookup"><span data-stu-id="f5b30-122">**Figure 2: Azure PaaS-based hybrid application**</span></span>

![Azure PaaS-basierte Hybridanwendung](media/Hybrid-Poster/Hybrid-Cloud-Stack-PaaS-Apps.png)
  
<span data-ttu-id="f5b30-p102">In Abbildung 2 werden Speicher oder Apps auf Servern und in einer DMZ mit einem Proxyserver in einem lokalen Netzwerk gehostet. Das Netzwerk ist über das Internet oder eine ExpressRoute-Verbindung mit PaaS Azure-Diensten verbunden.</span><span class="sxs-lookup"><span data-stu-id="f5b30-p102">In Figure 2, an on-premises network hosts storage or apps on servers and a DMZ containing a proxy server. It is connected to Azure PaaS services either over the Internet or with an ExpressRoute connection.</span></span>
  
<span data-ttu-id="f5b30-126">Eine Organisation kann seine Compute- oder Speicherressourcen wie folgt für die Azure PaaS-Hybridanwendung zugänglich machen:</span><span class="sxs-lookup"><span data-stu-id="f5b30-126">An organization can make its compute or storage resources available to the Azure PaaS hybrid application by:</span></span>
  
- <span data-ttu-id="f5b30-127">Durch Hosten der Ressource auf Servern in der DMZ</span><span class="sxs-lookup"><span data-stu-id="f5b30-127">Hosting the resource on servers in the DMZ.</span></span>
    
- <span data-ttu-id="f5b30-128">Durch Hosten eines Reverseproxyservers in der DMZ, der authentifizierte, eingehende, HTTPS-basierte Anforderungen an die Ressource zulässt, die sich im lokalen System befindet</span><span class="sxs-lookup"><span data-stu-id="f5b30-128">Hosting a reverse proxy server in the DMZ, which allows authenticated, inbound, HTTPS-based requests to the resource that is located on-premises.</span></span>
    
<span data-ttu-id="f5b30-129">Die Azure-App kann Anmeldeinformationen verwenden von:</span><span class="sxs-lookup"><span data-stu-id="f5b30-129">The Azure app can use credentials from:</span></span>
  
- <span data-ttu-id="f5b30-130">Azure AD, die mit Ihrem lokalen Identitätsanbieter synchronisiert werden kann, beispielsweise Active Directory-Domänendienste (AD DS).</span><span class="sxs-lookup"><span data-stu-id="f5b30-130">Azure AD, which can be synchronized with your on-premises identity provider, such as Active Directory Domain Services (AD DS).</span></span>
    
- <span data-ttu-id="f5b30-131">Einem Drittanbieter-Identitätsanbieter</span><span class="sxs-lookup"><span data-stu-id="f5b30-131">A third-party identity provider.</span></span>
    
### <a name="example-azure-paas-hybrid-application"></a><span data-ttu-id="f5b30-132">Azure PaaS-Hybridanwendung als Beispiel</span><span class="sxs-lookup"><span data-stu-id="f5b30-132">Example Azure PaaS hybrid application</span></span>

<span data-ttu-id="f5b30-133">Abbildung 3 zeigt ein Beispiel für eine Hybridanwendung, die in Azure ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="f5b30-133">Figure 3 shows an example hybrid application running in Azure.</span></span>
  
<span data-ttu-id="f5b30-134">**Abbildung 3: Ein Beispiel für eine Azure PaaS-basierte Hybridanwendung**</span><span class="sxs-lookup"><span data-stu-id="f5b30-134">**Figure 3: An example Azure PaaS-based hybrid application**</span></span>

![Ein Beispiel für eine Azure PaaS-basierte Hybridanwendung](media/Hybrid-Poster/Hybrid-Cloud-Stack-PaaS-Apps-Ex.png)
  
<span data-ttu-id="f5b30-p103">In Abbildung 3 wird eine Branchenanwendung in einem lokalen Netzwerk gehostet. Azure PaaS hostet eine benutzerdefinierte mobile App. Ein Smartphone im Internet greift auf die benutzerdefinierte mobile App in Azure zu, von wo wiederum Datenanforderungen an die lokale Branchenanwendung gesendet werden.</span><span class="sxs-lookup"><span data-stu-id="f5b30-p103">In Figure 3, an on-premises network hosts an LOB app. Azure PaaS hosts a custom mobile app. A smartphone on the Internet accesses the custom mobile app in Azure, which sends data requests to the on-premises LOB app.</span></span>
  
<span data-ttu-id="f5b30-p104">Diese Azure PaaS-Beispielhybridanwendung ist eine benutzerdefinierte mobile App, die aktuelle Kontaktinformationen zu Mitarbeitern bereitstellt. Das End-to-End-Hybridszenario besteht aus:</span><span class="sxs-lookup"><span data-stu-id="f5b30-p104">This example Azure PaaS hybrid application is a custom mobile app that provides up-to-date contact information on employees. The end-to-end hybrid scenario consists of:</span></span>
  
- <span data-ttu-id="f5b30-141">Einer Smartphone-App, die überprüfte lokale Anmeldeinformationen erfordert, damit sie ausgeführt werden kann</span><span class="sxs-lookup"><span data-stu-id="f5b30-141">A smartphone app that requires validated, on-premises credentials to run.</span></span>
    
- <span data-ttu-id="f5b30-142">Einer benutzerdefinierten mobilen App, die in Azure PaaS ausgeführt wird und Informationen zu bestimmten Mitarbeitern anhand von Abfragen anfordert, die von der Smartphone-App eines Benutzers stammen</span><span class="sxs-lookup"><span data-stu-id="f5b30-142">A custom mobile app running in Azure PaaS, which requests information about specific employees based on queries from a user's smartphone app.</span></span>
    
- <span data-ttu-id="f5b30-143">Einem Reverseproxyserver in der DMZ, der die benutzerdefinierte mobile App überprüft und die Anforderung weiterleitet</span><span class="sxs-lookup"><span data-stu-id="f5b30-143">A reverse proxy server in the DMZ that validates the custom mobile app and forwards the request.</span></span>
    
- <span data-ttu-id="f5b30-144">Einer Branchenanwendungs-Serverfarm, die die Kontaktanforderung entsprechend den Berechtigungen verarbeitet, die das Konto des Benutzers hat</span><span class="sxs-lookup"><span data-stu-id="f5b30-144">An LOB application server farm that services the contact request, subject to the permissions of the user's account.</span></span>
    
<span data-ttu-id="f5b30-145">Da der lokale Identitätsanbieter mit Azure Active Directory synchronisiert wurde, können sowohl die benutzerdefinierte mobile App als auch die Branchen-App den Kontonamen des anfordernden Benutzers überprüfen.</span><span class="sxs-lookup"><span data-stu-id="f5b30-145">Because the on-premises identity provider has been synchronized with Azure AD, both the custom mobile app and the LOB app can validate the requesting user's account name.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="f5b30-146">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="f5b30-146">See Also</span></span>

[<span data-ttu-id="f5b30-147">Microsoft Hybrid Cloud für Enterprise-Architekten</span><span class="sxs-lookup"><span data-stu-id="f5b30-147">Microsoft Hybrid Cloud for Enterprise Architects</span></span>](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[<span data-ttu-id="f5b30-148">Ressourcen zur Cloud-IT-Architektur von Microsoft</span><span class="sxs-lookup"><span data-stu-id="f5b30-148">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

