---
title: Bereitstellen der Verbundauthentifizierung mit Hochverfügbarkeit für Office 365 in Azure
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/06/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150s
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_Solutions
ms.assetid: 34b1ab9c-814c-434d-8fd0-e5a82cd9bff6
description: 'Zusammenfassung: Konfigurieren der Verbundauthentifizierung mit hoher Verfügbarkeit für Ihr Office 365-Abonnement in Microsoft Azure.'
ms.openlocfilehash: c72090638bcdcb580353baa7a733051971598e66
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/21/2018
ms.locfileid: "22914900"
---
# <a name="deploy-high-availability-federated-authentication-for-office-365-in-azure"></a><span data-ttu-id="12a38-103">Bereitstellen der Verbundauthentifizierung mit Hochverfügbarkeit für Office 365 in Azure</span><span class="sxs-lookup"><span data-stu-id="12a38-103">Deploy high availability federated authentication for Office 365 in Azure</span></span>

 <span data-ttu-id="12a38-104">**Zusammenfassung:** Konfigurieren der Verbundauthentifizierung mit hoher Verfügbarkeit für Ihr Office 365-Abonnement in Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="12a38-104">**Summary:** Configure high availability federated authentication for your Office 365 subscription in Microsoft Azure.</span></span>
  
<span data-ttu-id="12a38-105">Dieser Artikel enthält Links zu den schrittweisen Anleitungen für die Bereitstellung der Verbundauthentifizierung mit hoher Verfügbarkeit für Microsoft Office 365 in Azure-Infrastrukturdiensten mit den folgenden virtuellen Computern:</span><span class="sxs-lookup"><span data-stu-id="12a38-105">This article contains links to the step-by-step instructions for deploying high availability federated authentication for Microsoft Office 365 in Azure infrastructure services with these virtual machines:</span></span>
  
- <span data-ttu-id="12a38-106">Zwei Webanwendungsproxy-Server</span><span class="sxs-lookup"><span data-stu-id="12a38-106">Two web application proxy servers</span></span>
    
- <span data-ttu-id="12a38-107">Zwei Active Directory-Verbunddienste (AD FS)</span><span class="sxs-lookup"><span data-stu-id="12a38-107">Two Active Directory Federation Services (AD FS) servers</span></span>
    
- <span data-ttu-id="12a38-108">Zwei replizierte Domänencontroller</span><span class="sxs-lookup"><span data-stu-id="12a38-108">Two replica domain controllers</span></span>
    
- <span data-ttu-id="12a38-109">Ein Verzeichnissynchronisierungsserver (DirSync), auf dem Azure AD Connect ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="12a38-109">One directory synchronization (DirSync) server running Azure AD Connect</span></span>
    
<span data-ttu-id="12a38-110">Nachfolgend sehen Sie die Konfiguration mit Platzhalternamen für jeden Server.</span><span class="sxs-lookup"><span data-stu-id="12a38-110">Here is the configuration, with placeholder names for each server.</span></span>
  
<span data-ttu-id="12a38-111">**Eine Verbundauthentifizierung mit Hochverfügbarkeit für die Office 365-Infrastruktur in Azure**</span><span class="sxs-lookup"><span data-stu-id="12a38-111">**A high availability federated authentication for Office 365 infrastructure in Azure**</span></span>

![Die Endkonfiguration für die hochverfügbare Office 365-Verbundauthentifizierungsinfrastruktur in Azure](media/c5da470a-f2aa-489a-a050-df09b4d641df.png)
  
<span data-ttu-id="12a38-113">Alle virtuellen Computer befinden sich in einem einzigen standortübergreifenden virtuellen Azure-Netzwerk (VNet).</span><span class="sxs-lookup"><span data-stu-id="12a38-113">All of the virtual machines are in a single cross-premises Azure virtual network (VNet).</span></span> 
  
> [!NOTE]
> <span data-ttu-id="12a38-p101">Für die Verbundauthentifizierung einzelner Benutzer ist kein Rückgriff auf lokale Ressourcen erforderlich. Sollte die standortübergreifende Verbindung jedoch ausfallen, empfangen die Domänencontroller im VNet keine im lokalen Windows Server AD vorgenommenen Updates an Benutzerkonten und Gruppen. Zur Vermeidung eines solchen Szenarios können Sie Hochverfügbarkeit für die standortübergreifende Verbindung konfigurieren. Weitere Informationen finden Sie unter [Standortübergreifende Verbindungen und VNet-zu-VNet-Verbindungen mit hoher Verfügbarkeit](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-highlyavailable).</span><span class="sxs-lookup"><span data-stu-id="12a38-p101">Federated authentication of individual users does not rely on any on-premises resources. However, if the cross-premises connection becomes unavailable, the domain controllers in the VNet will not receive updates to user accounts and groups made in the on-premises Windows Server AD. To ensure this does not happen, you can configure high availability for your cross-premises connection. For more information, see [Highly Available Cross-Premises and VNet-to-VNet Connectivity](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-highlyavailable)</span></span>
  
<span data-ttu-id="12a38-118">Jedes Paar virtuelle Computer für eine bestimmte Rolle befindet sich in einem eigenen Subnetz und einer eigenen Verfügbarkeitsgruppe.</span><span class="sxs-lookup"><span data-stu-id="12a38-118">Each pair of virtual machines for a specific role is in its own subnet and availability set.</span></span>
  
> [!NOTE]
> <span data-ttu-id="12a38-p102">Da dieses VNet mit dem lokalen Netzwerk verbunden ist, umfasst diese Konfiguration keinen virtuellen Jumpbox- oder Überwachungscomputer in einem Verwaltungssubnetz. Weitere Informationen finden Sie unter [Ausführen von virtuellen Windows-Computern für eine Architektur mit N-Ebenen](https://docs.microsoft.com/azure/guidance/guidance-compute-n-tier-vm).</span><span class="sxs-lookup"><span data-stu-id="12a38-p102">Because this VNet is connected to the on-premises network, this configuration does not include jumpbox or monitoring virtual machines on a management subnet. For more information, see [Running Windows VMs for an N-tier architecture](https://docs.microsoft.com/azure/guidance/guidance-compute-n-tier-vm).</span></span> 
  
<span data-ttu-id="12a38-p103">Das Ergebnis dieser Konfiguration ist eine Verbundauthentifizierung für alle Ihre Office 365-Benutzer. Diese können sich dann also mit ihren Windows Server Active Directory-Anmeldeinformationen statt mit ihrem Office 365-Konto anmelden. Die Verbundauthentifizierungsinfrastruktur nutzt einen redundanten Satz von Servern, die in den Azure-Infrastrukturdiensten bereitgestellt sind, nicht in Ihrem lokalen Umkreisnetzwerk. Das ist eine deutlich einfacher zu implementierende Konstellation.</span><span class="sxs-lookup"><span data-stu-id="12a38-p103">The result of this configuration is that you will have federated authentication for all of your Office 365 users, in which they can use their Windows Server Active Directory credentials to sign in rather than their Office 365 account. The federated authentication infrastructure uses a redundant set of servers that are more easily deployed in Azure infrastructure services, rather than in your on-premises edge network.</span></span>
  
## <a name="bill-of-materials"></a><span data-ttu-id="12a38-123">Erforderliche Komponenten</span><span class="sxs-lookup"><span data-stu-id="12a38-123">Bill of materials</span></span>

<span data-ttu-id="12a38-124">Diese geplante Konfiguration erfordert den folgenden Satz von Azure-Diensten und Komponenten:</span><span class="sxs-lookup"><span data-stu-id="12a38-124">This baseline configuration requires the following set of Azure services and components:</span></span>
  
- <span data-ttu-id="12a38-125">Sieben virtuelle Computer</span><span class="sxs-lookup"><span data-stu-id="12a38-125">Seven virtual machines</span></span>
    
- <span data-ttu-id="12a38-126">Ein standortübergreifendes virtuelles Netzwerk mit vier Subnetzen</span><span class="sxs-lookup"><span data-stu-id="12a38-126">One cross-premises virtual network with four subnets</span></span>
    
- <span data-ttu-id="12a38-127">Vier Ressourcengruppen</span><span class="sxs-lookup"><span data-stu-id="12a38-127">Four resource groups</span></span>
    
- <span data-ttu-id="12a38-128">Drei Verfügbarkeitsgruppen.</span><span class="sxs-lookup"><span data-stu-id="12a38-128">Three availability sets</span></span>
    
- <span data-ttu-id="12a38-129">Ein Azure-Abonnement</span><span class="sxs-lookup"><span data-stu-id="12a38-129">One Azure subscription</span></span>
    
<span data-ttu-id="12a38-130">Nachfolgend sehen Sie die virtuellen Computer und ihre Standardgrößen für diese Konfiguration.</span><span class="sxs-lookup"><span data-stu-id="12a38-130">Here are the virtual machines and their default sizes for this configuration.</span></span>
  
|<span data-ttu-id="12a38-131">**Element**</span><span class="sxs-lookup"><span data-stu-id="12a38-131">**Item**</span></span>|<span data-ttu-id="12a38-132">**Beschreibung des virtuellen Computers**</span><span class="sxs-lookup"><span data-stu-id="12a38-132">**Virtual machine description**</span></span>|<span data-ttu-id="12a38-133">**Azure-Katalogbild**</span><span class="sxs-lookup"><span data-stu-id="12a38-133">**Azure gallery image**</span></span>|<span data-ttu-id="12a38-134">**Standardgröße**</span><span class="sxs-lookup"><span data-stu-id="12a38-134">**Default size**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="12a38-135">1.</span><span class="sxs-lookup"><span data-stu-id="12a38-135">1.</span></span>  <br/> |<span data-ttu-id="12a38-136">Erster Domänencontroller</span><span class="sxs-lookup"><span data-stu-id="12a38-136">First domain controller</span></span>  <br/> |<span data-ttu-id="12a38-137">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="12a38-137">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="12a38-138">D2</span><span class="sxs-lookup"><span data-stu-id="12a38-138">D2</span></span>  <br/> |
|<span data-ttu-id="12a38-139">2.</span><span class="sxs-lookup"><span data-stu-id="12a38-139">2.</span></span>  <br/> |<span data-ttu-id="12a38-140">Zweiter Domänencontroller</span><span class="sxs-lookup"><span data-stu-id="12a38-140">Second domain controller</span></span>  <br/> |<span data-ttu-id="12a38-141">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="12a38-141">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="12a38-142">D2</span><span class="sxs-lookup"><span data-stu-id="12a38-142">D2</span></span>  <br/> |
|<span data-ttu-id="12a38-143">3.</span><span class="sxs-lookup"><span data-stu-id="12a38-143">3.</span></span>  <br/> |<span data-ttu-id="12a38-144">Azure AD Connect-Server</span><span class="sxs-lookup"><span data-stu-id="12a38-144">Azure AD Connect server</span></span>  <br/> |<span data-ttu-id="12a38-145">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="12a38-145">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="12a38-146">D2</span><span class="sxs-lookup"><span data-stu-id="12a38-146">D2</span></span>  <br/> |
|<span data-ttu-id="12a38-147">4.</span><span class="sxs-lookup"><span data-stu-id="12a38-147">4.</span></span>  <br/> |<span data-ttu-id="12a38-148">Erster AD FS-Server
</span><span class="sxs-lookup"><span data-stu-id="12a38-148">First AD FS server</span></span>  <br/> |<span data-ttu-id="12a38-149">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="12a38-149">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="12a38-150">D2</span><span class="sxs-lookup"><span data-stu-id="12a38-150">D2</span></span>  <br/> |
|<span data-ttu-id="12a38-151">5.</span><span class="sxs-lookup"><span data-stu-id="12a38-151">5.</span></span>  <br/> |<span data-ttu-id="12a38-152">Zweiter AD FS-Server
</span><span class="sxs-lookup"><span data-stu-id="12a38-152">Second AD FS server</span></span>  <br/> |<span data-ttu-id="12a38-153">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="12a38-153">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="12a38-154">D2</span><span class="sxs-lookup"><span data-stu-id="12a38-154">D2</span></span>  <br/> |
|<span data-ttu-id="12a38-155">6.</span><span class="sxs-lookup"><span data-stu-id="12a38-155">6.</span></span>  <br/> |<span data-ttu-id="12a38-156">Erster Webanwendungsproxy-Server
</span><span class="sxs-lookup"><span data-stu-id="12a38-156">First web application proxy server</span></span>  <br/> |<span data-ttu-id="12a38-157">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="12a38-157">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="12a38-158">D2</span><span class="sxs-lookup"><span data-stu-id="12a38-158">D2</span></span>  <br/> |
|<span data-ttu-id="12a38-159">7.</span><span class="sxs-lookup"><span data-stu-id="12a38-159">7.</span></span>  <br/> |<span data-ttu-id="12a38-160">Zweiter Webanwendungsproxy-Server
</span><span class="sxs-lookup"><span data-stu-id="12a38-160">Second web application proxy server</span></span>  <br/> |<span data-ttu-id="12a38-161">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="12a38-161">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="12a38-162">D2</span><span class="sxs-lookup"><span data-stu-id="12a38-162">D2</span></span>  <br/> |
   
<span data-ttu-id="12a38-163">Um die geschätzten Kosten für diese Konfiguration zu berechnen, finden Sie unter [Azure-Preisrechner](https://azure.microsoft.com/pricing/calculator/) weitere Informationen.</span><span class="sxs-lookup"><span data-stu-id="12a38-163">To compute the estimated costs for this configuration, see the [Azure pricing calculator](https://azure.microsoft.com/pricing/calculator/)</span></span>
  
## <a name="phases-of-deployment"></a><span data-ttu-id="12a38-164">Phasen der Bereitstellung</span><span class="sxs-lookup"><span data-stu-id="12a38-164">Phases of deployment</span></span>

<span data-ttu-id="12a38-165">Sie stellen diese Arbeitslast in den folgenden Phasen bereit:</span><span class="sxs-lookup"><span data-stu-id="12a38-165">You deploy this workload in the following phases:</span></span>
  
- <span data-ttu-id="12a38-p104">[Hochverfügbarkeit der Verbundauthentifizierung, Phase 1: Konfigurieren von Azure](high-availability-federated-authentication-phase-1-configure-azure.md). Erstellen von Ressourcengruppen, Speicherkonten, Verfügbarkeitsgruppen und einem standortübergreifenden virtuellen Netzwerk.</span><span class="sxs-lookup"><span data-stu-id="12a38-p104">[High availability federated authentication Phase 1: Configure Azure](high-availability-federated-authentication-phase-1-configure-azure.md). Create resource groups, storage accounts, availability sets, and a cross-premises virtual network.</span></span>
    
- <span data-ttu-id="12a38-p105">[High availability federated authentication Phase 2: Configure domain controllers](high-availability-federated-authentication-phase-2-configure-domain-controllers.md). Erstellen und Konfigurieren von replizierten Windows Server Active Directory (AD)-Domänencontrollern und des DirSync-Servers.</span><span class="sxs-lookup"><span data-stu-id="12a38-p105">[High availability federated authentication Phase 2: Configure domain controllers](high-availability-federated-authentication-phase-2-configure-domain-controllers.md). Create and configure replica Windows Server Active Directory (AD) domain controllers and the DirSync server.</span></span>
    
- <span data-ttu-id="12a38-p106">[Hochverfügbarkeit der Verbundauthentifizierung, Phase 3: Konfigurieren von AD FS-Servern](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md). Erstellen und Konfigurieren der beiden AD FS-Server.</span><span class="sxs-lookup"><span data-stu-id="12a38-p106">[High availability federated authentication Phase 3: Configure AD FS servers](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md). Create and configure the two AD FS servers.</span></span>
    
- <span data-ttu-id="12a38-p107">[Hochverfügbarkeit der Verbundauthentifizierung, Phase 4: Konfigurieren von Webanwendungsproxys](high-availability-federated-authentication-phase-4-configure-web-application-pro.md). Erstellen und Konfigurieren der beiden Webanwendungsproxy-Server</span><span class="sxs-lookup"><span data-stu-id="12a38-p107">[High availability federated authentication Phase 4: Configure web application proxies](high-availability-federated-authentication-phase-4-configure-web-application-pro.md). Create and configure the two web application proxy servers.</span></span>
    
- <span data-ttu-id="12a38-p108">[Hochverfügbarkeit der Verbundauthentifizierung, Phase 5: Konfigurieren der Verbundauthentifizierung für Office 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md). Konfigurieren der Verbundauthentifizierung für Ihr Office 365-Abonnement.</span><span class="sxs-lookup"><span data-stu-id="12a38-p108">[High availability federated authentication Phase 5: Configure federated authentication for Office 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md). Configure federated authentication for your Office 365 subscription.</span></span>
    
<span data-ttu-id="12a38-p109">Dieser Artikel enthält eine phasenweise Anleitung für eine vordefinierte Architektur, um eine funktionale Verbundauthentifizierung mit hoher Verfügbarkeit für Office 365 in Azure-Infrastrukturdiensten zu erstellen. Denken Sie dabei an Folgendes:</span><span class="sxs-lookup"><span data-stu-id="12a38-p109">These articles provide a prescriptive, phase-by-phase guide for a predefined architecture to create a functional, high availability federated authentication for Office 365 in Azure infrastructure services. Keep the following in mind:</span></span>
  
- <span data-ttu-id="12a38-178">Wenn Sie ein erfahrener AD FS-Implementierer sind, können Sie die Anweisungen in den Phasen 3 und 4 entsprechend anpassen und eine Gruppe von Servern erstellen, die Ihren Anforderungen am besten entspricht. </span><span class="sxs-lookup"><span data-stu-id="12a38-178">If you are an experienced AD FS implementer, feel free to adapt the instructions in phases 3 and 4 and build the set of servers that best suits your needs.</span></span>
    
- <span data-ttu-id="12a38-179">Wenn Sie bereits über eine vorhandene Azure-Hybridcloudbereitstellung mit einem vorhandenen standortübergreifenden virtuellen Netzwerk verfügen, können Sie die Anweisungen in den Phasen 1 und 2 entsprechend anpassen oder überspringen und die AD FS-Server und die Webanwendungsproxy-Server in den entsprechenden Subnetzen platzieren.</span><span class="sxs-lookup"><span data-stu-id="12a38-179">If you already have an existing Azure hybrid cloud deployment with an existing cross-premises virtual network, feel free to adapt or skip the instructions in phases 1 and 2 and place the AD FS and web application proxy servers on the appropriate subnets.</span></span>
    
<span data-ttu-id="12a38-180">Informationen zum Erstellen einer Entwicklungs-/Testumgebung oder einer Machbarkeitsstudie dieser Konfiguration finden Sie unter [Verbundidentität für Ihre Office 365-Entwicklungs-/Testumgebung](federated-identity-for-your-office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="12a38-180">To build a dev/test environment or a proof-of-concept of this configuration, see [Federated identity for your Office 365 dev/test environment](federated-identity-for-your-office-365-dev-test-environment.md).</span></span>
  
## <a name="next-step"></a><span data-ttu-id="12a38-181">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="12a38-181">Next step</span></span>

<span data-ttu-id="12a38-182">Starten Sie die Konfiguration dieser Arbeitslast mit [Hochverfügbarkeit der Verbundauthentifizierung, Phase 1: Konfigurieren von Azure](high-availability-federated-authentication-phase-1-configure-azure.md).</span><span class="sxs-lookup"><span data-stu-id="12a38-182">Start the configuration of this workload with [High availability federated authentication Phase 1: Configure Azure](high-availability-federated-authentication-phase-1-configure-azure.md).</span></span> 
  
> [!TIP]
> <span data-ttu-id="12a38-183">Weitere Informationen zu einem Satz von Dateien, mit dem Sie die Hochverfügbarkeit bei der Verbundauthentifizierung für Office 365 in Azure schneller bereitstellen können, finden Sie unter [Deployment Kit zur Verbundauthentifizierung für Office 365 in Azure](https://gallery.technet.microsoft.com/Federated-Authentication-8a9f1664).</span><span class="sxs-lookup"><span data-stu-id="12a38-183">For a set of files to more quickly deploy your high availability federated authentication for Office 365 in Azure, see the [Federated Authentication for Office 365 in Azure Deployment Kit](https://gallery.technet.microsoft.com/Federated-Authentication-8a9f1664).</span></span> 
 

