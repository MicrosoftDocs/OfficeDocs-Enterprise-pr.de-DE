---
title: "Entwerfen von Netzwerken für Microsoft Azure-IaaS"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: concetpual
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- DecEntMigration
- Ent_Architecture
ms.assetid: 9cb70c9d-9ed9-47cc-af5a-6403d87d3372
description: "Zusammenfassung: Informationen Sie zum Entwerfen optimierte Netzwerke für Arbeitslasten in Microsoft Azure IaaS."
ms.openlocfilehash: e4861de51f386af6e142debdafc64f655f010880
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2017
---
# <a name="designing-networking-for-microsoft-azure-iaas"></a><span data-ttu-id="bd705-103">Entwerfen von Netzwerken für Microsoft Azure-IaaS</span><span class="sxs-lookup"><span data-stu-id="bd705-103">Designing networking for Microsoft Azure IaaS</span></span>

 <span data-ttu-id="bd705-104">**Zusammenfassung:** Weitere Informationen Sie zum Entwerfen optimierte Netzwerke für Arbeitslasten in Microsoft Azure IaaS.</span><span class="sxs-lookup"><span data-stu-id="bd705-104">**Summary:** Understand how to design optimized networking for workloads in Microsoft Azure IaaS.</span></span>
  
<span data-ttu-id="bd705-105">Um Netzwerke für IT-Workloads, die in Azure IaaS gehostet werden, optimieren zu können, benötigen Sie als Voraussetzung grundlegende Kenntnisse über Azure Virtual Networks (VNets), Adressräume, Routing, DNS und Lastenausgleich.</span><span class="sxs-lookup"><span data-stu-id="bd705-105">Optimizing networking for IT workloads hosted in Azure IaaS requires an understanding of Azure virtual networks (VNets), address spaces, routing, DNS, and load balancing.</span></span>
  
## <a name="planning-steps-for-any-vnet"></a><span data-ttu-id="bd705-106">VNet-Planungsschritte</span><span class="sxs-lookup"><span data-stu-id="bd705-106">Planning steps for any VNet</span></span>

<span data-ttu-id="bd705-107">Führen Sie die folgenden Schritte für jede Art von VNet aus.</span><span class="sxs-lookup"><span data-stu-id="bd705-107">Follow these steps for any type of VNet.</span></span>
  
### <a name="step-1-prepare-your-intranet-for-microsoft-cloud-services"></a><span data-ttu-id="bd705-108">Schritt 1: Bereiten Sie das Intranet für Microsoft Cloud Services vor.</span><span class="sxs-lookup"><span data-stu-id="bd705-108">Step 1: Prepare your intranet for Microsoft cloud services.</span></span>

<span data-ttu-id="bd705-109">Durchlaufen Sie die **Schritte zum Vorbereiten von Ihr Netzwerks für Microsoft Cloud Services** -Abschnitt in [Allgemeine Elemente von Microsoft-Cloud-Diensten](common-elements-of-microsoft-cloud-connectivity.md).</span><span class="sxs-lookup"><span data-stu-id="bd705-109">Go through the **Steps to prepare your network for Microsoft cloud services** section in [Common elements of Microsoft cloud connectivity](common-elements-of-microsoft-cloud-connectivity.md).</span></span>
  
### <a name="step-2-optimize-your-internet-bandwidth"></a><span data-ttu-id="bd705-110">Schritt 2: Optimieren Sie die Internetbandbreite.</span><span class="sxs-lookup"><span data-stu-id="bd705-110">Step 2: Optimize your Internet bandwidth.</span></span>

<span data-ttu-id="bd705-111">Optimieren Sie die Schritte 2 bis 4 des Abschnitts **Schritte zum Vorbereiten von Ihr Netzwerks für Microsoft SaaS Services** [Netzwerkfunktionen für Microsoft SaaS](designing-networking-for-microsoft-saas.md)Entwerfen von Internetbandbreite.</span><span class="sxs-lookup"><span data-stu-id="bd705-111">Optimize your Internet bandwidth using steps 2 - 4 of the **Steps to prepare your network for Microsoft SaaS services** section in [Designing networking for Microsoft SaaS](designing-networking-for-microsoft-saas.md).</span></span>
  
### <a name="step-3-determine-the-type-of-vnet-cloud-only-or-cross-premises"></a><span data-ttu-id="bd705-112">Schritt 3: Bestimmen Sie den VNet-Typ (reine Cloudbereitstellung oder standortübergreifend).</span><span class="sxs-lookup"><span data-stu-id="bd705-112">Step 3: Determine the type of VNet (cloud-only or cross-premises).</span></span>

<span data-ttu-id="bd705-p101">Eine reines Cloud-VNet hat keine Verbindung mit einem lokalen Netzwerk. Hier ein Beispiel:</span><span class="sxs-lookup"><span data-stu-id="bd705-p101">A cloud-only VNet has no connection to an on-premises network. Here is an example.</span></span>
  
<span data-ttu-id="bd705-115">**Abbildung 1: Eine reine VNet**</span><span class="sxs-lookup"><span data-stu-id="bd705-115">**Figure 1: A cloud-only VNet**</span></span>

![Abbildung 1: Ein virtuelles Netzwerk in Microsoft Azure mit reiner Cloudbereitstellung. ](images/8be19104-02b3-4a7f-b0a0-30d6fcf8890b.png)
  
<span data-ttu-id="bd705-117">Abbildung 1 zeigt eine Reihe von virtuellen Computern in einem reinen Cloud-VNet.</span><span class="sxs-lookup"><span data-stu-id="bd705-117">Figure 1 shows a set of virtual machines in a cloud-only VNet.</span></span>
  
<span data-ttu-id="bd705-p102">Ein standortübergreifendes VNet verfügt über ein Azure-Gateway über eine S2S-VPN-Verbindung (Standort-zu-Standort) oder eine ExpressRoute-Verbindung zu einem lokalen Netzwerk. Hier ein Beispiel:</span><span class="sxs-lookup"><span data-stu-id="bd705-p102">A cross-premises VNet has a site-to-site (S2S) VPN or ExpressRoute connection to an on-premises network through an Azure gateway. Here is an example.</span></span>
  
<span data-ttu-id="bd705-120">**Abbildung 2: Eine standortübergreifende VNet**</span><span class="sxs-lookup"><span data-stu-id="bd705-120">**Figure 2: A cross-premises VNet**</span></span>

![Abbildung 2: Standortübergreifendes virtuelles Netzwerk in Azure](images/caacf007-e0dc-45d3-9531-441109776d25.png)
  
<span data-ttu-id="bd705-122">Abbildung 2 zeigt eine Reihe von virtuellen Computern in einem standortübergreifenden VNet, das mit einem lokalen Netzwerk verbunden ist.</span><span class="sxs-lookup"><span data-stu-id="bd705-122">Figure 2 shows a set of virtual machines in a cross-premises VNet, which is connected to an on-premises network.</span></span>
  
<span data-ttu-id="bd705-123">Finden Sie die zusätzlichen [Schritte für eine standortübergreifende VNet Planung](designing-networking-for-microsoft-azure-iaas.md#cross_prem) Abschnitt in diesem Artikel.</span><span class="sxs-lookup"><span data-stu-id="bd705-123">See the additional [Planning steps for a cross-premises VNet](designing-networking-for-microsoft-azure-iaas.md#cross_prem) section in this article.</span></span>
  
### <a name="step-4-determine-the-address-space-of-the-vnet"></a><span data-ttu-id="bd705-124">Schritt 4: Ermitteln Sie den VNet-Adressraum.</span><span class="sxs-lookup"><span data-stu-id="bd705-124">Step 4: Determine the address space of the VNet.</span></span>

<span data-ttu-id="bd705-125">In Tabelle 1 sind die Adressräume für die verschiedenen VNet-Typen aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="bd705-125">Table 1 shows the address spaces for the different types of VNets.</span></span>
  
|<span data-ttu-id="bd705-126">**Typ des VNet**</span><span class="sxs-lookup"><span data-stu-id="bd705-126">**Type of VNet**</span></span>|<span data-ttu-id="bd705-127">**Virtuelles Netzwerk-Adressraum**</span><span class="sxs-lookup"><span data-stu-id="bd705-127">**Virtual network address space**</span></span>|
|:-----|:-----|
|<span data-ttu-id="bd705-128">Reine Cloudbereitstellung</span><span class="sxs-lookup"><span data-stu-id="bd705-128">Cloud-only</span></span>  <br/> |<span data-ttu-id="bd705-129">Beliebiger privater Adressraum</span><span class="sxs-lookup"><span data-stu-id="bd705-129">Arbitrary private address space</span></span>  <br/> |
|<span data-ttu-id="bd705-130">Miteinander verbunden, reine Cloudbereitstellung</span><span class="sxs-lookup"><span data-stu-id="bd705-130">Interconnected cloud-only</span></span>  <br/> |<span data-ttu-id="bd705-131">Beliebige Private, aber nicht mit anderen überlappende verbunden VNets</span><span class="sxs-lookup"><span data-stu-id="bd705-131">Arbitrary private, but not overlapping with other connected VNets</span></span>  <br/> |
|<span data-ttu-id="bd705-132">Standortübergreifend</span><span class="sxs-lookup"><span data-stu-id="bd705-132">Cross-premises</span></span>  <br/> |<span data-ttu-id="bd705-133">Privater Adressraum, der jedoch nicht mit lokalen VNets überlappt</span><span class="sxs-lookup"><span data-stu-id="bd705-133">Private, but not overlapping with on-premises</span></span>  <br/> |
|<span data-ttu-id="bd705-134">Miteinander verbunden, standortübergreifend</span><span class="sxs-lookup"><span data-stu-id="bd705-134">Interconnected cross-premises</span></span>  <br/> |<span data-ttu-id="bd705-135">Privater Adressraum, der jedoch nicht mit lokalen und anderen verbundenen VNets überlappt</span><span class="sxs-lookup"><span data-stu-id="bd705-135">Private, but not overlapping with on-premises and other connected VNets</span></span>  <br/> |
   
 <span data-ttu-id="bd705-136">**Tabelle 1: Arten von VNets und ihre entsprechenden Adressraum**</span><span class="sxs-lookup"><span data-stu-id="bd705-136">**Table 1: Types of VNets and their corresponding address space**</span></span>
  
<span data-ttu-id="bd705-137">Virtuellen Computern wird vom Adressraum des Subnetzes durch DHCP ein Adresskonfiguriation zugewiesen:</span><span class="sxs-lookup"><span data-stu-id="bd705-137">Virtual machines are assigned an address configuration from the address space of the subnet by DHCP:</span></span>
  
- <span data-ttu-id="bd705-138">Adresse/Subnetzmaske</span><span class="sxs-lookup"><span data-stu-id="bd705-138">Address/subnet mask</span></span>
    
- <span data-ttu-id="bd705-139">Standardgateway</span><span class="sxs-lookup"><span data-stu-id="bd705-139">Default gateway</span></span>
    
- <span data-ttu-id="bd705-140">IP-Adressen des DNS-Servers</span><span class="sxs-lookup"><span data-stu-id="bd705-140">DNS server IP addresses</span></span>
    
<span data-ttu-id="bd705-141">Sie können auch eine statische IP-Adresse reservieren.</span><span class="sxs-lookup"><span data-stu-id="bd705-141">You can also reserve a static IP address.</span></span>
  
<span data-ttu-id="bd705-142">Virtuellen Computern kann auch eine öffentliche IP-Adresse zugewiesen werden, entweder einzeln oder über den enthaltenden Clouddienst (nur für herkömmliche Bereitstellungscomputer).</span><span class="sxs-lookup"><span data-stu-id="bd705-142">Virtual machines can also be assigned a public IP address, either individually or from the containing cloud service (for classic deployment machines only).</span></span>
  
### <a name="step-5-determine-the-subnets-within-the-vnet-and-the-address-spaces-assigned-to-each"></a><span data-ttu-id="bd705-143">Schritt 5: Bestimmen Sie die Subnetze im VNet und die ihnen zugewiesenen Adressräume.</span><span class="sxs-lookup"><span data-stu-id="bd705-143">Step 5: Determine the subnets within the VNet and the address spaces assigned to each.</span></span>

<span data-ttu-id="bd705-144">Es gibt zwei Arten von Subnetzen in einem VNet: ein Gatewaysubnetz und ein Hostingsubnetz für virtuelle Computer.</span><span class="sxs-lookup"><span data-stu-id="bd705-144">There are two types of subnets in a VNet, a gateway subnet and a virtual machine-hosting subnet.</span></span>
  
<span data-ttu-id="bd705-145">**Abbildung 3: Die zwei Arten von Subnetze in Azure**</span><span class="sxs-lookup"><span data-stu-id="bd705-145">**Figure 3: The two types of subnets in Azure**</span></span>

![Abbildung 3: Die zwei Arten von Subnetzen in Azure](images/2eaa512d-1293-4e9b-b927-6bfe0fc0acb4.png)
  
<span data-ttu-id="bd705-147">Abbildung 3 zeigt ein VNet mit einem Gatewaysubnetz, das ein Azure-Gateway und eine Reihe von Hostingsubnetzen mit virtuellen Computern enthält.</span><span class="sxs-lookup"><span data-stu-id="bd705-147">Figure 3 shows a VNet containing a gateway subnet that contains an Azure gateway and a set of virtual machine-hosting subnets containing virtual machines.</span></span>
  
<span data-ttu-id="bd705-p103">Azure benötigt das Azure-Gatewaysubnetz zum Hosten der beiden virtuellen Computer Ihres Azure-Gateways. Angeben eines Adressraums mit einer Präfixlänge von mindestens 29 Bit (Beispiel: 192.168.15.248/29). Es wird ein Präfixlänge von 28 Bit oder weniger empfohlen, insbesondere dann, wenn Sie beabsichtigen, ExpressRoute zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="bd705-p103">The Azure gateway subnet is needed by Azure to host the two virtual machines of your Azure gateway. Specify an address space with at least a 29-bit prefix length (example: 192.168.15.248/29). A 28-bit or smaller prefix length is recommended, especially if you are planning to use ExpressRoute.</span></span>
  
<span data-ttu-id="bd705-151">Nachfolgend ist eine bewährte Methode zum Ermitteln des Adressraums eines Azure-Gatewaysubnetzes aufgeführt:</span><span class="sxs-lookup"><span data-stu-id="bd705-151">A best practice for determining the address space of the Azure gateway subnet is the following:</span></span>
  
1. <span data-ttu-id="bd705-152">Legen Sie die Größe des Gatewaysubnetzes fest.</span><span class="sxs-lookup"><span data-stu-id="bd705-152">Decide on the size of the gateway subnet.</span></span>
    
2. <span data-ttu-id="bd705-153">Legen Sie für die variablen Bits im Adressraum des VNet die Bits für das Gatewaysubnetz auf 0 und für die anderen Bits auf 1 fest.</span><span class="sxs-lookup"><span data-stu-id="bd705-153">In the variable bits in the address space of the VNet, set the bits used for the gateway subnet to 0 and set the remaining bits to 1.</span></span>
    
3. <span data-ttu-id="bd705-154">Konvertieren Sie dies in eine Dezimalzahl, und drücken Sie diese als Adressraum aus, wobei Sie als Präfixlänge die Größe des Gatewaysubnetzes festlegen.</span><span class="sxs-lookup"><span data-stu-id="bd705-154">Convert to decimal and express as an address space with the prefix length set to the size of the gateway subnet.</span></span>
    
<span data-ttu-id="bd705-155">Wenn Sie diese Methode verwenden, befindet sich der Adressraum für das Gatewaysubnetz immer am äußersten Ende des VNet-Adressbereichs.</span><span class="sxs-lookup"><span data-stu-id="bd705-155">With this method, the address space for the gateway subnet is always at the farthest end of the VNet address space.</span></span>
  
<span data-ttu-id="bd705-p104">Es folgt ein Beispiel für die Definition des Adresspräfixes für das Gatewaysubnetz: Der Adressraum des VNet ist 10.119.0.0/16. Die Organisation verwendet anfänglich eine Standort-zu-Standort-VPN-Verbindung, später jedoch ExpressRoute. In Tabelle 2 sind die Schritte sowie die Ergebnisse der Ermittlung des Adresspräfixes in der Netzwerkpräfixnotation für das Gatewaysubnetz aufgeführt (auch als CIDR bezeichnet).</span><span class="sxs-lookup"><span data-stu-id="bd705-p104">Here is an example of defining the address prefix for the gateway subnet: The address space of the VNet is 10.119.0.0/16. The organization will initially use a site-to-site VPN connection, but will eventually get ExpressRoute. Table 2 shows the steps and results of determining the gateway subnet address prefix in network prefix notation (also known as CIDR).</span></span>

<span data-ttu-id="bd705-159">Es folgen die Schritte und Beispiel für das Gateway Subnetz Adresspräfix bestimmen:</span><span class="sxs-lookup"><span data-stu-id="bd705-159">Here are the steps and example of determining the gateway subnet address prefix:</span></span>

1. <span data-ttu-id="bd705-p105">Legen Sie die Größe des Subnetzes Gateway. In unserem Beispiel haben wir uns /28 entschieden.</span><span class="sxs-lookup"><span data-stu-id="bd705-p105">Decide on the size of the gateway subnet. For our example, we chose /28.</span></span>
2. <span data-ttu-id="bd705-p106">Legen Sie die Bits in den Variablen Teil der VNet-Adressraum (b) auf 0 für das Gateway Subnetz Bits (G), andernfalls 1 (V). In unserem Beispiel verwenden wir den 10.119.0.0/16-Adressraum für die VNet.</span><span class="sxs-lookup"><span data-stu-id="bd705-p106">Set the bits in the variable portion of the VNet address space (b) to 0 for the gateway subnet bits (G), otherwise 1 (V). For our example, we are using the 10.119.0.0/16 address space for the VNet. </span></span><br/>
<br/><span data-ttu-id="bd705-p107">10.119. Bbbbbbbb. bbbbbbbb</span><span class="sxs-lookup"><span data-stu-id="bd705-p107">10.119. bbbbbbbb . bbbbbbbb </span></span><br/><span data-ttu-id="bd705-p108">10.119. VVVVVVVV. VVVVGGGG</span><span class="sxs-lookup"><span data-stu-id="bd705-p108">10.119. VVVVVVVV . VVVVGGGG </span></span><br/><span data-ttu-id="bd705-p109">10.119. 11111111. 11110000</span><span class="sxs-lookup"><span data-stu-id="bd705-p109">10.119. 11111111 . 11110000 </span></span><br/><br/>
3. <span data-ttu-id="bd705-p110">Das Ergebnis aus Schritt 2 zu decimal und als Adressraum express zu konvertieren. In unserem Beispiel 10.119. 11111111. 11110000 ist 10.119.255.240, und mit dem Präfixlänge aus Schritt 1, (28 in unserem Beispiel), ist das resultierende Gateway Subnetz Adresspräfix 10.119.255.240/28.</span><span class="sxs-lookup"><span data-stu-id="bd705-p110">Convert the result from step 2 to decimal and express as an address space. For our example, 10.119. 11111111 . 11110000 is 10.119.255.240, and with the prefix length from step 1, (28 in our example), the resulting gateway subnet address prefix is 10.119.255.240/28.</span></span>
  
<span data-ttu-id="bd705-177">Weitere Informationen finden Sie unter [Adresse Speicherplatz Rechner für Azure Gateway Subnetze](https://gallery.technet.microsoft.com/scriptcenter/Address-prefix-calculator-a94b6eed) .</span><span class="sxs-lookup"><span data-stu-id="bd705-177">See [Address space calculator for Azure gateway subnets](https://gallery.technet.microsoft.com/scriptcenter/Address-prefix-calculator-a94b6eed) for more information.</span></span>
  
<span data-ttu-id="bd705-178">Sie platzieren virtuelle Azure-Computer in Hostingsubnetzen für virtuelle Computer, wobei Sie hier gemäß den typisch lokalen Richtlinien folgen können, wie z. B. einer allgemeinen Rolle oder Ebene einer Anwendung oder für die Subnetzisolierung.</span><span class="sxs-lookup"><span data-stu-id="bd705-178">Virtual machine-hosting subnets are where you place Azure virtual machines, which you can do according to typical on-premises guidelines, such as a common role or tier of an application or for subnet isolation.</span></span>
  
<span data-ttu-id="bd705-p111">Azure verwendet die ersten 3 Adressen in jedem Subnetz. Aus diesem Grund ist die Anzahl der möglichen Adressen in einem Subnetz Azure 2<sup>n</sup> -5, wobei n die Anzahl der Hostbits ist. Tabelle 3 zeigt der Bereich der virtuellen Computer erforderlich, die Anzahl der benötigten Bits gehostet wird, und die entsprechenden Subnetz-Größe.</span><span class="sxs-lookup"><span data-stu-id="bd705-p111">Azure uses the first 3 addresses on each subnet. Therefore, the number of possible addresses on an Azure subnet is 2<sup>n</sup> - 5, where n is the number of host bits. Table 3 shows the range of virtual machines required, the number of hosts bits needed, and the corresponding subnet size.</span></span>
  
|<span data-ttu-id="bd705-182">**Virtuelle Computer erforderlich**</span><span class="sxs-lookup"><span data-stu-id="bd705-182">**Virtual machines required**</span></span>|<span data-ttu-id="bd705-183">**Hostbits**</span><span class="sxs-lookup"><span data-stu-id="bd705-183">**Host bits**</span></span>|<span data-ttu-id="bd705-184">**Subnetz-Größe**</span><span class="sxs-lookup"><span data-stu-id="bd705-184">**Subnet size**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="bd705-185">1-3</span><span class="sxs-lookup"><span data-stu-id="bd705-185">1-3</span></span>  <br/> |<span data-ttu-id="bd705-186">3</span><span class="sxs-lookup"><span data-stu-id="bd705-186">3</span></span>  <br/> |<span data-ttu-id="bd705-187">/29</span><span class="sxs-lookup"><span data-stu-id="bd705-187">/29</span></span>  <br/> |
|<span data-ttu-id="bd705-188">4-11</span><span class="sxs-lookup"><span data-stu-id="bd705-188">4-11</span></span>  <br/> |<span data-ttu-id="bd705-189">4</span><span class="sxs-lookup"><span data-stu-id="bd705-189">4</span></span>  <br/> |<span data-ttu-id="bd705-190">/28</span><span class="sxs-lookup"><span data-stu-id="bd705-190">/28</span></span>  <br/> |
|<span data-ttu-id="bd705-191">12-27</span><span class="sxs-lookup"><span data-stu-id="bd705-191">12-27</span></span>  <br/> |<span data-ttu-id="bd705-192">5</span><span class="sxs-lookup"><span data-stu-id="bd705-192">5</span></span>  <br/> |<span data-ttu-id="bd705-193">/27</span><span class="sxs-lookup"><span data-stu-id="bd705-193">/27</span></span>  <br/> |
|<span data-ttu-id="bd705-194">28-59</span><span class="sxs-lookup"><span data-stu-id="bd705-194">28-59</span></span>  <br/> |<span data-ttu-id="bd705-195">6</span><span class="sxs-lookup"><span data-stu-id="bd705-195">6</span></span>  <br/> |<span data-ttu-id="bd705-196">/26</span><span class="sxs-lookup"><span data-stu-id="bd705-196">/26</span></span>  <br/> |
|<span data-ttu-id="bd705-197">60-123</span><span class="sxs-lookup"><span data-stu-id="bd705-197">60-123</span></span>  <br/> |<span data-ttu-id="bd705-198">7</span><span class="sxs-lookup"><span data-stu-id="bd705-198">7</span></span>  <br/> |<span data-ttu-id="bd705-199">/25</span><span class="sxs-lookup"><span data-stu-id="bd705-199">/25</span></span>  <br/> |
   
 <span data-ttu-id="bd705-200">**Tabelle 3: Anforderungen für die virtuellen Computer und ihre Größe Subnetz**</span><span class="sxs-lookup"><span data-stu-id="bd705-200">**Table 3: Virtual machine requirements and their subnet sizes**</span></span>
  
<span data-ttu-id="bd705-201">Weitere Informationen zu den maximalen Zeitraum der virtuellen Computer auf einem Subnetz oder VNet finden Sie unter [Networking Grenzwerte](https://docs.microsoft.com/azure/azure-subscription-service-limits#networking-limits).</span><span class="sxs-lookup"><span data-stu-id="bd705-201">For more information about the maximum amount of virtual machines on a subnet or VNet, see [Networking Limits](https://docs.microsoft.com/azure/azure-subscription-service-limits#networking-limits).</span></span>
  
<span data-ttu-id="bd705-202">Weitere Informationen finden Sie unter [Planen und Entwerfen Azure-virtuelle Netzwerke](https://azure.microsoft.com/documentation/articles/virtual-network-vnet-plan-design-arm/).</span><span class="sxs-lookup"><span data-stu-id="bd705-202">For more information, see [Plan and design Azure Virtual Networks](https://azure.microsoft.com/documentation/articles/virtual-network-vnet-plan-design-arm/).</span></span>
  
### <a name="step-6-determine-the-dns-server-configuration-and-the-addresses-of-the-dns-servers-to-assign-to-vms-in-the-vnet"></a><span data-ttu-id="bd705-203">Schritt 6: Ermitteln Sie die DNS-Serverkonfiguration und die Adressen der DNS-Server, die den VMs im VNet zugewiesen werden sollen.</span><span class="sxs-lookup"><span data-stu-id="bd705-203">Step 6: Determine the DNS server configuration and the addresses of the DNS servers to assign to VMs in the VNet.</span></span>

<span data-ttu-id="bd705-p112">Azure weist virtuellen Computern die Adressen der DNS-Server über DHCP zu. DNS-Server können:</span><span class="sxs-lookup"><span data-stu-id="bd705-p112">Azure assigns virtual machines the addresses of DNS servers by DHCP. DNS servers can be:</span></span>
  
- <span data-ttu-id="bd705-206">durch Azure bereitgestellt werden: Bietet lokale Namensregistrierung sowie lokale und über das Internet durchgeführte Namensauflösung</span><span class="sxs-lookup"><span data-stu-id="bd705-206">Supplied by Azure: Provides local name registration and local and Internet name resolution</span></span>
    
- <span data-ttu-id="bd705-207">von Ihnen bereitgestellt werden: Bietet lokale oder über das Internet durchgeführte Namensregistrierung und Namensauflösung entweder über das Intranet oder über das Internet</span><span class="sxs-lookup"><span data-stu-id="bd705-207">Provided by you: Provides local or intranet name registration and either intranet or Internet name resolution</span></span>
    
<span data-ttu-id="bd705-208">In Tabelle 4 sind die verschiedenen DNS-Serverkonfigurationen für jeden VNet-Typ aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="bd705-208">Table 4 shows the different configurations of DNS servers for each type of VNet.</span></span>
    
|<span data-ttu-id="bd705-209">**Typ des VNet**</span><span class="sxs-lookup"><span data-stu-id="bd705-209">**Type of VNet**</span></span>|<span data-ttu-id="bd705-210">**DNS-server**</span><span class="sxs-lookup"><span data-stu-id="bd705-210">**DNS server**</span></span>|
|:-----|:-----|
|<span data-ttu-id="bd705-211">Reine Cloudbereitstellung</span><span class="sxs-lookup"><span data-stu-id="bd705-211">Cloud-only</span></span>  <br/> |<span data-ttu-id="bd705-212">von Azure für die lokale und über das Internet durchgeführte Namensauflösung bereitgestellt</span><span class="sxs-lookup"><span data-stu-id="bd705-212">Azure-supplied for local and Internet name resolution</span></span>  <br/> <span data-ttu-id="bd705-213">virtueller Azure-Computer für die lokale und über das Internet durchgeführte Namensauflösung (DNS-Weiterleitung)</span><span class="sxs-lookup"><span data-stu-id="bd705-213">Azure virtual machine for local and Internet name resolution (DNS forwarding)</span></span>  <br/> |
|<span data-ttu-id="bd705-214">Standortübergreifend</span><span class="sxs-lookup"><span data-stu-id="bd705-214">Cross-premises</span></span>  <br/> |<span data-ttu-id="bd705-215">lokal für die lokale und über das Intranet durchgeführte Namensauflösung</span><span class="sxs-lookup"><span data-stu-id="bd705-215">On-premises for local and intranet name resolution</span></span>  <br/> <span data-ttu-id="bd705-216">virtueller Azure-Computer für die lokale und über das Intranet durchgeführte Namensauflösung (DNS-Replikation und -Weiterleitung)</span><span class="sxs-lookup"><span data-stu-id="bd705-216">Azure virtual machine for local and intranet name resolution (DNS replication and forwarding)</span></span>  <br/> |
   
 <span data-ttu-id="bd705-217">**Tabelle 4: DNS-Server-Optionen für die zwei verschiedenen Arten von VNets**</span><span class="sxs-lookup"><span data-stu-id="bd705-217">**Table 4: DNS server options for the two different types of VNets**</span></span>
  
<span data-ttu-id="bd705-218">Weitere Informationen finden Sie unter [Name Resolution für virtuelle Computer und Instanzen](https://docs.microsoft.com/azure/virtual-network/virtual-networks-name-resolution-for-vms-and-role-instances).</span><span class="sxs-lookup"><span data-stu-id="bd705-218">For more information, see [Name Resolution for VMs and Role Instances](https://docs.microsoft.com/azure/virtual-network/virtual-networks-name-resolution-for-vms-and-role-instances).</span></span>
  
### <a name="step-7-determine-the-load-balancing-configuration-internet-facing-or-internal"></a><span data-ttu-id="bd705-219">Schritt 7: Ermitteln Sie die Lastenausgleichskonfiguration (Internet-bezogen oder intern).</span><span class="sxs-lookup"><span data-stu-id="bd705-219">Step 7: Determine the load balancing configuration (Internet-facing or internal).</span></span>

<span data-ttu-id="bd705-p113">In einigen Fällen möchten Sie eingehenden Datenverkehr auf eine Gruppe von Servern verteilen, die über die gleiche Rolle verfügen. Azure IaaS verfügt über eine integrierte Funktion, mit der dies für dem Internet zugewandten und internen Datenverkehr vorgenommen werden kann.</span><span class="sxs-lookup"><span data-stu-id="bd705-p113">In some cases, you want to distribute incoming traffic to a set of servers that have the same role. Azure IaaS has a built-in facility to do this for Internet-facing and internal traffic loads.</span></span>
  
<span data-ttu-id="bd705-222">Der dem Internet zugewandte Lastenausgleich von Azure verteilt den unangefordert aus dem Internet kommenden Datenverkehr zufällig auf die Mitglieder einer Lastenausgleichsgruppe. </span><span class="sxs-lookup"><span data-stu-id="bd705-222">Azure Internet-facing load balancing randomly distributes unsolicited incoming traffic from the Internet to the members of a load-balanced set.</span></span>
  
<span data-ttu-id="bd705-223">**Abbildung 4: Eine externe System zum Lastenausgleich in Azure**</span><span class="sxs-lookup"><span data-stu-id="bd705-223">**Figure 4: An external load balancer in Azure**</span></span>

![Abbildung 4: Ein externer Lastenausgleich in Azure](images/eb5945e5-0c2b-40f1-b9ed-54bb2b0f9e59.png)
  
<span data-ttu-id="bd705-225">Abbildung 4 zeigt einen externes System zum Lastenausgleich in Azure, die eingehenden Datenverkehr auf eine eingehende NAT-Regel oder einen Endpunkt einen Satz von virtuellen Computern in einem Satz mit Lastenausgleich verteilt.</span><span class="sxs-lookup"><span data-stu-id="bd705-225">Figure 4 shows an external load balancer in Azure that distributes incoming traffic on an inbound NAT rule or endpoint to a set of virtual machines in a load-balanced set.</span></span>
  
<span data-ttu-id="bd705-226">Der Azure-interne Lastenausgleich verteilt unangeforderten eingehenden Datenverkehr von andere Azure-VMs oder Intranetcomputern an die Mitglieder einer Lastenausgleichsgruppe. </span><span class="sxs-lookup"><span data-stu-id="bd705-226">Azure internal load balancing randomly distributes unsolicited incoming traffic from other Azure VMs or from intranet computers to the members of a load-balanced set.</span></span> 
  
<span data-ttu-id="bd705-227">**Abbildung 5: Eine interne System zum Lastenausgleich in Azure**</span><span class="sxs-lookup"><span data-stu-id="bd705-227">**Figure 5: An internal load balancer in Azure**</span></span>

![Abbildung 5: Ein interner Lastenausgleich in Azure](images/d1451b73-6465-449d-b3e6-22160ce51f35.png)
  
<span data-ttu-id="bd705-229">Abbildung 5 zeigt eine interne System zum Lastenausgleich in Azure, die eingehenden Datenverkehr auf eine eingehende NAT-Regel oder einen Endpunkt einen Satz von virtuellen Computern in einem Satz mit Lastenausgleich verteilt.</span><span class="sxs-lookup"><span data-stu-id="bd705-229">Figure 5 shows an internal load balancer in Azure that distributes incoming traffic on an inbound NAT rule or endpoint to a set of virtual machines in a load-balanced set.</span></span>
  
<span data-ttu-id="bd705-230">Weitere Informationen finden Sie unter [Azure System zum Lastenausgleich](https://docs.microsoft.com/azure/load-balancer/load-balancer-overview).</span><span class="sxs-lookup"><span data-stu-id="bd705-230">For more information, see [Azure Load Balancer](https://docs.microsoft.com/azure/load-balancer/load-balancer-overview).</span></span>
  
### <a name="step-8-determine-the-use-of-virtual-appliances-and-user-defined-routes"></a><span data-ttu-id="bd705-231">Schritt 8: Ermitteln Sie die Verwendung von virtuellen Geräten und benutzerdefinierten Routen.</span><span class="sxs-lookup"><span data-stu-id="bd705-231">Step 8: Determine the use of virtual appliances and user-defined routes.</span></span>

<span data-ttu-id="bd705-232">Wenn Sie Datenverkehrs an virtuelle Geräte im VNet weiterleiten müssen, müssen Sie einem Subnetz möglicherweise eine oder mehrere benutzerdefinierte Routen hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="bd705-232">If you need to forward traffic to virtual appliances in your VNet, you may need to add one or more user-defined routes to a subnet.</span></span>
  
<span data-ttu-id="bd705-233">**Abbildung 6: Virtuelle Appliances und benutzerdefinierte Routen in Azure**</span><span class="sxs-lookup"><span data-stu-id="bd705-233">**Figure 6: Virtual appliances and user-defined routes in Azure**</span></span>

![Abbildung 6: Virtuelle Geräte und benutzerdefinierte Routen in Azure](images/f181d0f4-ebf9-439e-9c98-dec17428c32b.png)
  
<span data-ttu-id="bd705-235">Abbildung 6 zeigt ein standortübergreifendes VNet und eine benutzerdefinierte Route, die einem Hostingsubnetz für virtuelle Computer zugewiesen ist, das auf ein virtuelles Gerät verweist.</span><span class="sxs-lookup"><span data-stu-id="bd705-235">Figure 6 shows a cross-premises VNet and a user-defined route assigned to a virtual machine-hosting subnet that points to a virtual appliance.</span></span>
  
<span data-ttu-id="bd705-236">Weitere Informationen finden Sie unter [benutzerdefinierte Routen und IP-Weiterleitung](https://docs.microsoft.com/azure/virtual-network/virtual-networks-udr-overview).</span><span class="sxs-lookup"><span data-stu-id="bd705-236">For more information, see [User Defined Routes and IP Forwarding](https://docs.microsoft.com/azure/virtual-network/virtual-networks-udr-overview).</span></span>
  
### <a name="step-9-determine-how-computers-from-the-internet-will-connect-to-virtual-machines"></a><span data-ttu-id="bd705-237">Schritt 9 Ermitteln Sie, wie Computer aus dem Internet Verbindungen mit virtuellen Computern herstellen.</span><span class="sxs-lookup"><span data-stu-id="bd705-237">Step 9: Determine how computers from the Internet will connect to virtual machines.</span></span>

<span data-ttu-id="bd705-238">Es gibt mehrere Möglichkeiten, den virtuellen Computern in einem VNet Zugang zum Internet bereitzustellen. Dazu zählt der Zugriff vom Netzwerk Ihrer Organisation über einen Proxyserver oder ein anderes Edgegerät.</span><span class="sxs-lookup"><span data-stu-id="bd705-238">There are multiple ways to provide Internet access to the virtual machines on a VNet, which includes access from your organization network through your proxy server or other edge device.</span></span>
  
<span data-ttu-id="bd705-239">In Tabelle 5 sind die Methoden zum Filtern oder Prüfen von unangefordert eingehendem Datenverkehr aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="bd705-239">Table 5 lists the methods for filtering or inspecting unsolicited incoming traffic.</span></span>
  
|<span data-ttu-id="bd705-240">**Methode**</span><span class="sxs-lookup"><span data-stu-id="bd705-240">**Method**</span></span>|<span data-ttu-id="bd705-241">**Bereitstellungsmodell**</span><span class="sxs-lookup"><span data-stu-id="bd705-241">**Deployment model**</span></span>|
|:-----|:-----|
|<span data-ttu-id="bd705-242">1. Endpunkte und ACLs, für Clouddienste konfiguriert</span><span class="sxs-lookup"><span data-stu-id="bd705-242">1. Endpoints and ACLs configured on cloud services</span></span>  <br/> |<span data-ttu-id="bd705-243">Klassisch</span><span class="sxs-lookup"><span data-stu-id="bd705-243">Classic</span></span>  <br/> |
|<span data-ttu-id="bd705-244">2. Netzwerksicherheitsgruppen</span><span class="sxs-lookup"><span data-stu-id="bd705-244">2. Network security groups</span></span>  <br/> |<span data-ttu-id="bd705-245">Ressourcenmanager und klassisch</span><span class="sxs-lookup"><span data-stu-id="bd705-245">Resource Manager and classic</span></span>  <br/> |
|<span data-ttu-id="bd705-246">3. Dem Internet zugewandter Lastenausgleich mit NAT-Eingangsregeln</span><span class="sxs-lookup"><span data-stu-id="bd705-246">3. Internet-facing load balancer with inbound NAT rules</span></span>  <br/> |<span data-ttu-id="bd705-247">Ressourcenmanager</span><span class="sxs-lookup"><span data-stu-id="bd705-247">Resource Manager</span></span>  <br/> |
|<span data-ttu-id="bd705-248">4. Sicherheit Netzwerkgeräte in der Azure</span><span class="sxs-lookup"><span data-stu-id="bd705-248">4. Network security appliances in the Azure</span></span> 
 <span data-ttu-id="bd705-249">Marketplace (nicht dargestellt)</span><span class="sxs-lookup"><span data-stu-id="bd705-249">Marketplace (not shown)</span></span>  <br/> |<span data-ttu-id="bd705-250">Ressourcenmanager und klassisch</span><span class="sxs-lookup"><span data-stu-id="bd705-250">Resource Manager and classic</span></span>  <br/> |
   
 <span data-ttu-id="bd705-251">**Tabelle 5: Herstellen einer Verbindung mit virtuellen Computern und ihre entsprechenden Azure Bereitstellungsmodelle Methoden**</span><span class="sxs-lookup"><span data-stu-id="bd705-251">**Table 5: Methods of connecting to virtual machines and their corresponding Azure deployment models**</span></span>
  
<span data-ttu-id="bd705-252">**Abbildung 7: Herstellen einer Verbindung mit virtuellen Azure-Computern über das Internet**</span><span class="sxs-lookup"><span data-stu-id="bd705-252">**Figure 7: Connecting to Azure virtual machines over the Internet**</span></span>

![Abbildung 7: Herstellen einer Verbindung mit virtuellen Azure-Computern über das Internet](images/c5e3531b-170a-4482-a6ff-fb8fbbe81b35.png)
  
<span data-ttu-id="bd705-254">Abbildung 7 zeigt einen mit dem Internet verbundenen Computer, der mit einem virtuellen Computer in einem Clouddienst anhand eines Endpunkts verbunden ist, einen virtuellen Computer in einem Subnetz mit einer Netzwerksicherheitsgruppe und einen virtuellen Computer in einem Subnetz mit einem externen Lastenausgleich und NAT-Eingangsregeln.</span><span class="sxs-lookup"><span data-stu-id="bd705-254">Figure 7 shows an Internet-connected computer connecting to a virtual machine in a cloud service using an endpoint, a virtual machine on a subnet using a network security group, and a virtual machine on a subnet using an external load balancer and inbound NAT rules.</span></span>
  
<span data-ttu-id="bd705-255">Zusätzlicher Sicherheit bereitgestellt durch:</span><span class="sxs-lookup"><span data-stu-id="bd705-255">Additional security is provided by:</span></span>
  
- <span data-ttu-id="bd705-256">Remotedesktop- und SSH-Verbindungen, die verschlüsselt und authentifiziert werden</span><span class="sxs-lookup"><span data-stu-id="bd705-256">Remote Desktop and SSH connections, which are authenticated and encrypted.</span></span>
    
- <span data-ttu-id="bd705-257">Remote PowerShell-Sitzungen, die verschlüsselt und authentifiziert werden</span><span class="sxs-lookup"><span data-stu-id="bd705-257">Remote PowerShell sessions, which are authenticated and encrypted.</span></span>
    
- <span data-ttu-id="bd705-258">IPsec-Transportmodus, den Sie für die End-to-End-Verschlüsselung verwenden können</span><span class="sxs-lookup"><span data-stu-id="bd705-258">IPsec transport mode, which you can use for end-to-end encryption.</span></span>
    
- <span data-ttu-id="bd705-259">Azure DDOS-Schutz, der vor externe und interne Angriffen schützt</span><span class="sxs-lookup"><span data-stu-id="bd705-259">Azure DDOS protection, which helps prevent external and internal attacks</span></span>
    
<span data-ttu-id="bd705-260">Weitere Informationen finden Sie unter [Microsoft Cloud Sicherheitsupdates für Enterprise-konstruiert](https://aka.ms/cloudarchsecurity) und [Azure Netzwerk](https://azure.microsoft.com/blog/azure-network-security/).</span><span class="sxs-lookup"><span data-stu-id="bd705-260">For more information, see [Microsoft Cloud Security for Enterprise Architects](https://aka.ms/cloudarchsecurity) and [Azure Network Security](https://azure.microsoft.com/blog/azure-network-security/).</span></span>
  
### <a name="step-10-for-multiple-vnets-determine-the-vnet-to-vnet-connection-topology"></a><span data-ttu-id="bd705-261">Schritt 10 Bestimmen Sie für mehrere VNets die Verbinungstopologie von VNet zu VNet.</span><span class="sxs-lookup"><span data-stu-id="bd705-261">Step 10: For multiple VNets, determine the VNet-to-VNet connection topology.</span></span>

<span data-ttu-id="bd705-262">VNets können mit ähnlichen Topologien verbunden werden, die auch zum Verbinden von Standorten einer Organisation verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="bd705-262">VNets can be connected to each other using topologies similar to those used for connecting the sites of an organization.</span></span>
  
<span data-ttu-id="bd705-263">Durch eine Verkettungskonfiguration (Daisychain) werden die VNets in einer Reihe verbunden.</span><span class="sxs-lookup"><span data-stu-id="bd705-263">A daisy chain configuration connects the VNets in a series.</span></span>
  
<span data-ttu-id="bd705-264">**Abbildung 8: Eine Reihe geschalteten Konfiguration für VNets**</span><span class="sxs-lookup"><span data-stu-id="bd705-264">**Figure 8: A daisy-chained configuration for VNets**</span></span>

![Abbildung 8: Verkettete Konfiguration für virtuelle Azure-Netzwerke](images/264d5dd4-06c5-483f-9428-a18cc1f68ac1.png)
  
<span data-ttu-id="bd705-266">Abbildung 8 zeigt fünf VNets in Datenreihe mit einer Konfiguration verkettete verbunden.</span><span class="sxs-lookup"><span data-stu-id="bd705-266">Figure 8 shows five VNets connected in series using a daisy-chained configuration.</span></span>
  
<span data-ttu-id="bd705-267">Bei einer Hub-Spoke-Konfiguration werden mehrere VNets mit eine Reihe von zentralen VNets verbunden, die ihrerseits miteinander verbunden sind.</span><span class="sxs-lookup"><span data-stu-id="bd705-267">A spoke and hub configuration connects multiple VNets to a set of central VNets, which are themselves connected to each other.</span></span>
  
<span data-ttu-id="bd705-268">**Abbildung 9: Eine sternförmigen Konfiguration für VNets**</span><span class="sxs-lookup"><span data-stu-id="bd705-268">**Figure 9: A spoke and hub configuration for VNets**</span></span>

![Abbildung 9: Spoke-and-Hub-Konfiguration für virtuelle Azure-Netzwerke](images/dd442a38-5b76-4ac5-b743-8fc7711a91ba.png)
  
<span data-ttu-id="bd705-270">Abbildung 9 zeigt sechs VNets, wobei zwei VNets „Hubs“ sind, die miteinander sowie mit anderen „Spoke“-VNets verbunden sind.</span><span class="sxs-lookup"><span data-stu-id="bd705-270">Figure 9 shows six VNets, two VNets are hubs that are connected to each other and also two other spoke VNets.</span></span>
  
<span data-ttu-id="bd705-271">Bei einer Full-Mesh-Konfiguration ist jedes VNet mit jedem anderen verbunden.</span><span class="sxs-lookup"><span data-stu-id="bd705-271">A full mesh configuration connects every VNet to each other.</span></span>
  
<span data-ttu-id="bd705-272">**Abbildung 10: Eine vollständige mesh-Konfiguration für VNets**</span><span class="sxs-lookup"><span data-stu-id="bd705-272">**Figure 10: A full mesh configuration for VNets**</span></span>

![Abbildung 10: Maschenkonfiguration für virtuelle Azure-Netzwerke](images/9dda0738-10db-4a63-95b3-79851a399b71.png)
  
<span data-ttu-id="bd705-274">Abbildung 10 zeigt vier VNets, die alle miteinander verbunden sind, wobei insgesamt sechs VNet-zu-VNet-Verbindungen vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="bd705-274">Figure 10 shows four VNets that are all connected to each other, using a total of six VNet-to-VNet connections.</span></span>
  
## <a name="planning-steps-for-a-cross-premises-vnet"></a><span data-ttu-id="bd705-275">Planungsschritte für ein standortübergreifendes VNet</span><span class="sxs-lookup"><span data-stu-id="bd705-275">Planning steps for a cross-premises VNet</span></span>
<span data-ttu-id="bd705-276"><a name="cross_prem"> </a></span><span class="sxs-lookup"><span data-stu-id="bd705-276"></span></span>

<span data-ttu-id="bd705-277">Führen Sie die folgende Schritte durch, um ein stadortübergreifendes VNet zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="bd705-277">Follow these steps for a cross-premises VNet.</span></span>
  
> [!TIP]
> <span data-ttu-id="bd705-278">Zum Erstellen einer simulierten standortübergreifenden Test-/Umgebung finden Sie unter [simulierten standortübergreifenden virtuelles Netzwerk in Azure](simulated-cross-premises-virtual-network-in-azure.md).</span><span class="sxs-lookup"><span data-stu-id="bd705-278">To create a simulated cross-premises dev/test environment, see [Simulated cross-premises virtual network in Azure](simulated-cross-premises-virtual-network-in-azure.md).</span></span> 
  
### <a name="step-1-determine-the-cross-premises-connection-to-the-vnet-s2s-vpn-or-expressroute"></a><span data-ttu-id="bd705-279">Schritt 1: Ermitteln Sie die standortübergreifende Verbindung zum VNet (S2S-VPN oder ExpressRoute).</span><span class="sxs-lookup"><span data-stu-id="bd705-279">Step 1: Determine the cross-premises connection to the VNet (S2S VPN or ExpressRoute).</span></span>

<span data-ttu-id="bd705-280">In Tabelle 6 sind die verschiedenen Verbindungstypen aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="bd705-280">Table 6 lists the different types of connections.</span></span>
  
|<span data-ttu-id="bd705-281">**Verbindungstyp**</span><span class="sxs-lookup"><span data-stu-id="bd705-281">**Type of connection**</span></span>|<span data-ttu-id="bd705-282">**Zweck**</span><span class="sxs-lookup"><span data-stu-id="bd705-282">**Purpose**</span></span>|
|:-----|:-----|
|<span data-ttu-id="bd705-283">Standort-zu-Standort-VPN (S2S)</span><span class="sxs-lookup"><span data-stu-id="bd705-283">Site-to-Site (S2S) VPN</span></span>  <br/> |<span data-ttu-id="bd705-284">Verbinden Sie 1-10-Websites (einschließlich andere VNets) mit einer einzelnen VNet.</span><span class="sxs-lookup"><span data-stu-id="bd705-284">Connect 1-10 sites (including other VNets) to a single VNet.</span></span>  <br/> |
|<span data-ttu-id="bd705-285">ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="bd705-285">ExpressRoute</span></span>  <br/> |<span data-ttu-id="bd705-286">Eine private, sichere Verbindung mit Azure über einen Internet-Exchange-Anbieter (IXP) oder ein Netzwerkdienstanbieter (NSP).</span><span class="sxs-lookup"><span data-stu-id="bd705-286">A private, secure link to Azure via an Internet Exchange Provider (IXP) or a Network Service Provider (NSP).</span></span>  <br/> |
|<span data-ttu-id="bd705-287">Punkt-zu-Standort-VPN (P2S)</span><span class="sxs-lookup"><span data-stu-id="bd705-287">Point-to-Site (P2S) VPN</span></span>  <br/> |<span data-ttu-id="bd705-288">Verbindet einen einzelnen Computer mit einem VNet</span><span class="sxs-lookup"><span data-stu-id="bd705-288">Connects a single computer to a VNet.</span></span>  <br/> |
|<span data-ttu-id="bd705-289">VNet-Peering oder VNet-zu-VNet-VPN (V2V) </span><span class="sxs-lookup"><span data-stu-id="bd705-289">VNet peering or VNet-to-VNet (V2V) VPN</span></span>  <br/> |<span data-ttu-id="bd705-290">Verbindet ein VNet mit einem anderen VNet</span><span class="sxs-lookup"><span data-stu-id="bd705-290">Connects a VNet to another VNet.</span></span>  <br/> |
   
 <span data-ttu-id="bd705-291">**Tabelle 6: Die Typen der Verbindungen für standortübergreifende VNets**</span><span class="sxs-lookup"><span data-stu-id="bd705-291">**Table 6: The types of connections for cross-premises VNets**</span></span>
  
<span data-ttu-id="bd705-292">Weitere Informationen über die maximale Anzahl der Verbindungen finden Sie unter [Networking Grenzwerte](https://docs.microsoft.com/azure/azure-subscription-service-limits#networking-limits).</span><span class="sxs-lookup"><span data-stu-id="bd705-292">For more information on the maximum number of connections, see [Networking Limits](https://docs.microsoft.com/azure/azure-subscription-service-limits#networking-limits).</span></span>
  
<span data-ttu-id="bd705-293">Weitere Informationen zu VPN-Geräten finden Sie unter [VPN-Geräten für Verbindungen zwischen Standorten virtuelles Netzwerk](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpn-devices).</span><span class="sxs-lookup"><span data-stu-id="bd705-293">For more information about VPN devices, see [VPN devices for site-to-site virtual network connections](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpn-devices).</span></span>
  
<span data-ttu-id="bd705-294">Weitere Informationen zu VNet peering finden Sie unter [VNet peering](https://docs.microsoft.com/azure/virtual-network/virtual-network-peering-overview).</span><span class="sxs-lookup"><span data-stu-id="bd705-294">For more information about VNet peering, see [VNet peering](https://docs.microsoft.com/azure/virtual-network/virtual-network-peering-overview).</span></span>
  
<span data-ttu-id="bd705-295">**Abbildung 11: Die vier Methoden zum Herstellen einer Verbindung einer standortübergreifenden VNet**</span><span class="sxs-lookup"><span data-stu-id="bd705-295">**Figure 11: The four ways to connect to a cross-premises VNet**</span></span>

![Abbildung 11: Die drei Methoden zum Herstellen einer Verbindung zu einem standortübergreifenden virtuellen Azure-Netzwerk](images/d5d4a625-cfbd-4a77-9159-eaca69d07e93.png)
  
<span data-ttu-id="bd705-297">Abbildung 11 zeigt eine VNet mit vier Arten von Verbindungen: Verbindung mit einem P2S von einem Computer, eine S2S VPN-Verbindung von einem lokalen Netzwerk, einer ExpressRoute Verbindung über einen lokalen Netzwerk und Verbindung mit einem VNet-VNet-von einer anderen VNet.</span><span class="sxs-lookup"><span data-stu-id="bd705-297">Figure 11 shows a VNet with the four types of connections: a P2S connection from a computer, an S2S VPN connection from an on-premises network, an ExpressRoute connection from an on-premises network, and a VNet-to-VNet connection from another VNet.</span></span> 
  
<span data-ttu-id="bd705-298">Sie können eine Verbindung mit VMs in einem VNet wie folgt herstellen:</span><span class="sxs-lookup"><span data-stu-id="bd705-298">You can connect to VMs in a VNet in the following ways:</span></span>
  
- <span data-ttu-id="bd705-299">Verwaltung von VNet-VMs über das lokale Netzwerk oder das Internet</span><span class="sxs-lookup"><span data-stu-id="bd705-299">Administration of VNet VMs from your on-premises network or the Internet</span></span>
    
- <span data-ttu-id="bd705-300">IT-Workloadzugriff vom lokalen Netzwerk</span><span class="sxs-lookup"><span data-stu-id="bd705-300">IT workload access from your on-premises network</span></span>
    
- <span data-ttu-id="bd705-301">Erweiterung des Netzwerks durch zusätzliche VNets</span><span class="sxs-lookup"><span data-stu-id="bd705-301">Extension of your network through additional VNets</span></span>
    
<span data-ttu-id="bd705-302">Die Sicherheit der Verbindungen wird durch Folgendes sichergestellt:</span><span class="sxs-lookup"><span data-stu-id="bd705-302">Security for connections is provided by the following:</span></span>
  
- <span data-ttu-id="bd705-303">P2S verwendet SSTP (Secure Socket Tunnel Protocol). </span><span class="sxs-lookup"><span data-stu-id="bd705-303">P2S uses the Secure Socket Tunneling Protocol (SSTP)</span></span> 
    
- <span data-ttu-id="bd705-304">S2S und VNet-zu-VNet-VPN-Verbindungen verwenden den IPsec-Tunnelmodus mit AES256.</span><span class="sxs-lookup"><span data-stu-id="bd705-304">S2S and VNet-to-VNet VPN connections use IPsec tunnel mode with AES256</span></span>
    
- <span data-ttu-id="bd705-305">ExpressRoute ist eine private WAN-Verbindung.</span><span class="sxs-lookup"><span data-stu-id="bd705-305">ExpressRoute is a private WAN connection</span></span>
    
<span data-ttu-id="bd705-306">Weitere Informationen finden Sie unter [Microsoft Cloud Sicherheitsupdates für Enterprise-konstruiert](https://aka.ms/cloudarchsecurity) und [Azure Netzwerk](https://azure.microsoft.com/blog/azure-network-security/).</span><span class="sxs-lookup"><span data-stu-id="bd705-306">For more information, see [Microsoft Cloud Security for Enterprise Architects](https://aka.ms/cloudarchsecurity) and [Azure Network Security](https://azure.microsoft.com/blog/azure-network-security/).</span></span>
  
### <a name="step-2-determine-the-on-premises-vpn-device-or-router"></a><span data-ttu-id="bd705-307">Schritt 2: Ermitteln Sie das lokale VPN-Gerät oder den Router.</span><span class="sxs-lookup"><span data-stu-id="bd705-307">Step 2: Determine the on-premises VPN device or router.</span></span>

<span data-ttu-id="bd705-308">Ihr lokales VPN-Gerät oder der Router fungiert als:</span><span class="sxs-lookup"><span data-stu-id="bd705-308">Your on-premises VPN device or router acts as:</span></span>
  
- <span data-ttu-id="bd705-309">ein IPSec-Peer, der die S2S-VPN-Verbindung von einem Azure-Gateway trennt.</span><span class="sxs-lookup"><span data-stu-id="bd705-309">An IPsec peer, terminating the S2S VPN connection from the Azure gateway.</span></span>
    
- <span data-ttu-id="bd705-310">der BPG-Peer und Abschlusspunkt für die private ExpressRoute-Peeringverbindung.</span><span class="sxs-lookup"><span data-stu-id="bd705-310">The BPG peer and termination point for the private peering ExpressRoute connection.</span></span>
    
<span data-ttu-id="bd705-311">**Abbildung 12: Das lokale VPN-Router oder ein Gerät**</span><span class="sxs-lookup"><span data-stu-id="bd705-311">**Figure 12: The on-premises VPN router or device**</span></span>

![Abbildung 12: Lokaler VPN-Router oder lokales Gerät](images/bd221468-a660-4730-aa55-0426986480b9.png)
  
<span data-ttu-id="bd705-313">Abbildung 12 zeigt eine standortübergreifendes VNet, das mit einem lokalen VPN-Router oder einem Gerät verbunden ist.</span><span class="sxs-lookup"><span data-stu-id="bd705-313">Figure 12 shows a cross-premises VNet connected to an on-premises VPN router or device.</span></span>
  
<span data-ttu-id="bd705-314">Weitere Informationen finden Sie unter [Informationen zu VPN-Gateway](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpngateways).</span><span class="sxs-lookup"><span data-stu-id="bd705-314">For more information, see [About VPN gateway](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpngateways).</span></span>
  
### <a name="step-3-add-routes-to-your-intranet-to-make-the-address-space-of-the-vnet-reachable"></a><span data-ttu-id="bd705-315">Schritt 3: Fügen Sie Routen zu Ihrem Intranet zu den Adressraum der VNet erreichbar sind hinzu.</span><span class="sxs-lookup"><span data-stu-id="bd705-315">Step 3: Add routes to your intranet to make the address space of the VNet reachable.</span></span>

<span data-ttu-id="bd705-316">Die Weiterleitung an VNets von lokal umfasst Folgendes:</span><span class="sxs-lookup"><span data-stu-id="bd705-316">Routing to VNets from on-premises consists of the following:</span></span>
  
1. <span data-ttu-id="bd705-317">Eine Route für den VNet-Adressraum, die auf Ihr VPN-Gerät verweist.</span><span class="sxs-lookup"><span data-stu-id="bd705-317">A route for the VNet address space that points toward your VPN device.</span></span>
    
2. <span data-ttu-id="bd705-318">Eine Route für den VNet-Adressraum auf Ihrem VPN-Gerät, die über die S2S-VPN- oder ExpressRoute-Verbindung hinweg verweist.</span><span class="sxs-lookup"><span data-stu-id="bd705-318">A route for the VNet address space on your VPN device that points across the S2S VPN or ExpressRoute connection</span></span>
    
<span data-ttu-id="bd705-319">**Abbildung 13: Die lokalen Routen erforderlich, um eine VNet erreichbar sind.**</span><span class="sxs-lookup"><span data-stu-id="bd705-319">**Figure 13: The on-premises routes needed to make a VNet reachable**</span></span>

![Abbildung 13: Die lokalen Routen, die erforderlich sind, damit ein Azure VNet erreichbar ist](images/7a1e20c1-fbc4-4cb9-9961-735da4e23307.png)
  
<span data-ttu-id="bd705-321">Abbildung 13 zeigt die Routinginformationen, die von den lokalen Routern benötigt werden, sowie den VPN-Router oder das Gerät, das den Adressraum das VNets darstellt.</span><span class="sxs-lookup"><span data-stu-id="bd705-321">Figure 13 shows the routing information needed by the on-premises routers and the VPN router or device that represents the address space of the VNet.</span></span>
  
### <a name="step-4-for-expressroute-plan-for-the-new-connection-with-your-provider"></a><span data-ttu-id="bd705-322">Schritt 4: Planen Sie bei Verwendung von ExpressRoute die neue Verbindung mit Ihrem Anbieter.</span><span class="sxs-lookup"><span data-stu-id="bd705-322">Step 4: For ExpressRoute, plan for the new connection with your provider.</span></span>

<span data-ttu-id="bd705-323">Sie haben drei verschiedene Möglichkeiten, um eine ExpressRoute-Verbindung mit privatem Peering zwischen Ihrem lokalen Netzwerk und der Microsoft-Cloud herzustellen:</span><span class="sxs-lookup"><span data-stu-id="bd705-323">You can create an ExpressRoute connection with private peering between your on-premises network and the Microsoft cloud in three different ways:</span></span>
  
- <span data-ttu-id="bd705-324">Co-Location bei einem Cloud Exchange</span><span class="sxs-lookup"><span data-stu-id="bd705-324">Co-located at a cloud exchange</span></span>
    
- <span data-ttu-id="bd705-325">Punkt-zu-Punkt-Ethernet-Verbindungen</span><span class="sxs-lookup"><span data-stu-id="bd705-325">Point-to-point Ethernet connections</span></span>
    
- <span data-ttu-id="bd705-326">Viele-zu-viele-Netzwerke (IP-VPN)</span><span class="sxs-lookup"><span data-stu-id="bd705-326">Any-to-any (IP VPN) networks</span></span>
    
<span data-ttu-id="bd705-327">**Abbildung 14: ExpressRoute Verbindung mit einer standortübergreifenden VNet verwenden**</span><span class="sxs-lookup"><span data-stu-id="bd705-327">**Figure 14: Using ExpressRoute to connect to a cross-premises VNet**</span></span>

![Abbildung 14: Verwenden von ExpressRoute zum Herstellen einer Verbindung mit einem lokalen virtuellen Azure-Netzwerk](images/7030bd39-69a6-4283-8567-3434e1ab6ba6.png)
  
<span data-ttu-id="bd705-329">Abbildung 14 zeigt ein standortübergreifendes VNet und eine ExpressRoute-Verbindung von einem lokalen Router zu Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="bd705-329">Figure 14 shows a cross-premises VNet and an ExpressRoute connection from an on-premises router to Microsoft Azure.</span></span>
  
<span data-ttu-id="bd705-330">Weitere Informationen finden Sie unter [ExpressRoute für Microsoft-Cloudkonnektivität](expressroute-for-microsoft-cloud-connectivity.md).</span><span class="sxs-lookup"><span data-stu-id="bd705-330">For more information, see [ExpressRoute for Microsoft cloud connectivity](expressroute-for-microsoft-cloud-connectivity.md).</span></span>
  
### <a name="step-5-determine-the-local-network-address-space-for-the-azure-gateway"></a><span data-ttu-id="bd705-331">Schritt 5: Bestimmen Sie den lokalen Netzwerkadressraum für das Azure-Gateway.</span><span class="sxs-lookup"><span data-stu-id="bd705-331">Step 5: Determine the Local Network address space for the Azure gateway.</span></span>

<span data-ttu-id="bd705-332">Beim Routing zu lokalen oder anderen VNets von einem VNet leitet Azure den Datenverkehr über einen Azure-Gateway, der mit dem lokalen Netzwerkadressraum übereinstimmt, der dem Gateway zugeordnet ist.</span><span class="sxs-lookup"><span data-stu-id="bd705-332">For the routing to on-premises or other VNets from a VNet, Azure forwards traffic across an Azure gateway that matches the Local Network address space assigned to the gateway.</span></span>
  
<span data-ttu-id="bd705-333">**Abbildung 15: Den lokalen Netzwerk-Adressraum für eine standortübergreifende VNet**</span><span class="sxs-lookup"><span data-stu-id="bd705-333">**Figure 15: The Local Network address space for a cross-premises VNet**</span></span>

![Abbildung 15: Adressraum des lokalen Netzwerks für ein standortübergreifendes virtuelles Azure-Netzwerk](images/e3af2652-8b8e-4551-9a0b-b550e6e7e3c0.png)
  
<span data-ttu-id="bd705-335">Abbildung 15 zeigt eine standortübergreifendes VNet und den Adressraum des lokalen Netzwerks auf dem Azure-Gateway, der den erreichbaren Adressraum im lokalen Netzwerk darstellt. </span><span class="sxs-lookup"><span data-stu-id="bd705-335">Figure 15 shows a cross-premises VNet and the Local Network address space on the Azure gateway, which represents the reachable address space on the on-premises network.</span></span> 
  
<span data-ttu-id="bd705-336">Sie können den Adressraum des lokalen Netzwerks wie folgt definieren:</span><span class="sxs-lookup"><span data-stu-id="bd705-336">You can define the Local Network address space in the following ways:</span></span>
  
- <span data-ttu-id="bd705-337">Option 1: Die Liste der Präfixe für den gerade benötigten oder verwendeten Adressraum (Aktualisierungen können erforderlich sein, wenn Sie neue Subnetzen hinzufügen).</span><span class="sxs-lookup"><span data-stu-id="bd705-337">Option 1: The list of prefixes for the address space currently needed or in use (updates might be needed when you add new subnets).</span></span>
    
- <span data-ttu-id="bd705-338">Option 2: Der gesamte lokale Adressraum (Aktualisierungen sind nur nötig, wenn Sie einen neuen Adressraum hinzufügen).</span><span class="sxs-lookup"><span data-stu-id="bd705-338">Option 2: Your entire on-premises address space (updates only needed when you add new address space).</span></span>
    
<span data-ttu-id="bd705-339">Da das Azure-Gateway keine zusammengefassten Routen zulässt, müssen Sie den Adressraum des lokalen Netzwerk bei der Option 2 so definieren, dass er nicht den VNet-Adressraum enthält.</span><span class="sxs-lookup"><span data-stu-id="bd705-339">Because the Azure gateway does not allow summarized routes, you must define the Local Network address space for option 2 so that it does not include the VNet address space.</span></span>
  
<span data-ttu-id="bd705-340">**Abbildung 16: Die Adresse Speicherplatz Hole durch den VNet-Adressraum erstellt**</span><span class="sxs-lookup"><span data-stu-id="bd705-340">**Figure 16: The address space hole created by the VNet address space**</span></span>

![Abbildung 16: Das vom Adressraum des virtuellen Netzwerks erstellte Adressraumloch](images/e79c4840-f9e3-4741-9b72-59db6043aefa.png)
  
<span data-ttu-id="bd705-342">Abbildung 16 zeigt eine Darstellung eines Adressraums mit dem Stammraum und dem VNet-Adressraum.</span><span class="sxs-lookup"><span data-stu-id="bd705-342">Figure 16 shows a representation of an address space, with the root space and the VNet address space.</span></span>
  
<span data-ttu-id="bd705-343">Es folgt ein Beispiel der Präfixe für den lokalen Netzwerk-Adressraum, um den Adressraum "Hole" erstellt, durch die VNet definieren:</span><span class="sxs-lookup"><span data-stu-id="bd705-343">Here is an example of defining the prefixes for the Local Network address space around the address space "hole" created by the VNet:</span></span>
  
- <span data-ttu-id="bd705-p114">Eine Organisation verwendet Teile des privaten Adressraums (10.0.0.0/8, 172.16.0.0/12 und 192.168.0.0/16) in ihrem lokalen Netzwerk. Die Organisation verwendet Option 2 und 10.100.100.0/24 als ihren VNet-Adressraum.</span><span class="sxs-lookup"><span data-stu-id="bd705-p114">An organization uses portions of the private address space (10.0.0.0/8, 172.16.0.0/12, and 192.168.0.0/16) across their on-premises network. They chose option 2 and 10.100.100.0/24 as their VNet address space.</span></span>
    
<span data-ttu-id="bd705-346">In Tabelle 7 sind die Schritte und die resultierenden Präfixe aufgeführt, die den Adressraum des lokalen Netzwerks in diesem Beispiel definieren.</span><span class="sxs-lookup"><span data-stu-id="bd705-346">Table 7 shows the steps and resulting prefixes that define the Local Network address space for this example.</span></span>
  
|<span data-ttu-id="bd705-347">**Schritt**</span><span class="sxs-lookup"><span data-stu-id="bd705-347">**Step**</span></span>|<span data-ttu-id="bd705-348">**Ergebnisse**</span><span class="sxs-lookup"><span data-stu-id="bd705-348">**Results**</span></span>|
|:-----|:-----|
|<span data-ttu-id="bd705-349">1. Auflisten der Präfixe, die nicht der Stammraum für den VNet-Adressraum sind.</span><span class="sxs-lookup"><span data-stu-id="bd705-349">1. List the prefixes that are not the root space for the VNet address space.</span></span>  <br/> |<span data-ttu-id="bd705-350">172.16.0.0/12 und 192.168.0.0/16</span><span class="sxs-lookup"><span data-stu-id="bd705-350">172.16.0.0/12 and 192.168.0.0/16</span></span>  <br/> |
|<span data-ttu-id="bd705-351">2. die übereinander Präfixe für Variablen Bytes bis zu aufgelistet, aber nicht einschließlich des letzten verwendet</span><span class="sxs-lookup"><span data-stu-id="bd705-351">2. List the non-overlapping prefixes for variable octets up to but not including the last used</span></span> 
 <span data-ttu-id="bd705-352">Oktett im VNet-Adressraum.</span><span class="sxs-lookup"><span data-stu-id="bd705-352">octet in the VNet address space.</span></span>  <br/> |<span data-ttu-id="bd705-353">10.0.0.0/16, 10.1.0.0/16... 10.99.0.0/16, 10.101.0.0/16... 10.254.0.0/16 10.255.0.0/16 (255 Präfixe 10.100.0.0/16 überspringen)</span><span class="sxs-lookup"><span data-stu-id="bd705-353">10.0.0.0/16, 10.1.0.0/16…10.99.0.0/16, 10.101.0.0/16…10.254.0.0/16, 10.255.0.0/16 (255 prefixes, skipping 10.100.0.0/16)</span></span>  <br/> |
|<span data-ttu-id="bd705-354">3. Liste der übereinander innerhalb Präfixen der</span><span class="sxs-lookup"><span data-stu-id="bd705-354">3. List the non-overlapping prefixes within the</span></span> 
 <span data-ttu-id="bd705-355">zuletzt verwendete Oktett des Adressraums VNet.</span><span class="sxs-lookup"><span data-stu-id="bd705-355">last used octet of the VNet address space.</span></span>  <br/> <span data-ttu-id="bd705-356">| 10.100.0.0/24, 10.100.1.0/24... 10.100.99.0/24, 10.100.101.0/24... 10.100.254.0/24 10.100.0.255.0/24 (255 Präfixe 10.100.100.0/24 überspringen)</span><span class="sxs-lookup"><span data-stu-id="bd705-356">|10.100.0.0/24, 10.100.1.0/24…10.100.99.0/24, 10.100.101.0/24…10.100.254.0/24, 10.100.0.255.0/24 (255 prefixes, skipping 10.100.100.0/24)</span></span>  <br/> |
   
 <span data-ttu-id="bd705-357">**Tabelle 7: Beispiel lokalen Netzwerk Adressraum**</span><span class="sxs-lookup"><span data-stu-id="bd705-357">**Table 7: Example Local Address network space**</span></span>
  
### <a name="step-6-configure-on-premises-dns-servers-for-dns-replication-with-dns-servers-hosted-in-azure"></a><span data-ttu-id="bd705-358">Schritt 6: Konfigurieren Sie lokale DNS-Server für die DNS-Replikation mit DNS-Servern, die in Azure gehostet werden.</span><span class="sxs-lookup"><span data-stu-id="bd705-358">Step 6: Configure on-premises DNS servers for DNS replication with DNS servers hosted in Azure.</span></span>

<span data-ttu-id="bd705-359">Um sicherzustellen, dass lokale Computer die Namen von Servern in Azure und die Server in Azure die Namen von lokalen Computern auflösen können, müssen Sie Folgendes konfigurieren:</span><span class="sxs-lookup"><span data-stu-id="bd705-359">To ensure that on-premises computers can resolve the names of Azure-based servers and Azure-based servers can resolve the names of on-premises computers, configure:</span></span>
  
- <span data-ttu-id="bd705-360">Die DNS-Server in Ihrem VNet leiten an lokale DNS-Server weiter</span><span class="sxs-lookup"><span data-stu-id="bd705-360">The DNS servers in your VNet to forward to on-premises DNS servers</span></span>
    
- <span data-ttu-id="bd705-361">DNS-Replikation der entsprechenden Zonen zwischen lokalen DNS-Servern und im VNet</span><span class="sxs-lookup"><span data-stu-id="bd705-361">DNS replication of the appropriate zones between DNS servers on-premises and in the VNet</span></span>
    
<span data-ttu-id="bd705-362">**Abbildung 17: DNS-Replikation und Weiterleitung für einen DNS-Server in einer standortübergreifenden VNet**</span><span class="sxs-lookup"><span data-stu-id="bd705-362">**Figure 17: DNS replication and forwarding for a DNS server in a cross-premises VNet**</span></span>

![Abbildung 17: DNS-Replikation und Weiterleitung für einen DNS-Server in einem standortübergreifenden virtuellen Azure-Netzwerk](images/ab55e5ce-ccb0-49d4-a301-657a727f97b2.png)
  
<span data-ttu-id="bd705-p115">Abbildung 17 zeigt ein standortübergreifendes VNet mit DNS-Server im lokalen Netzwerk und in einem Subnetz im. DNS-Replikation und -Weiterleitung wurde zwischen den beiden DNS-Servern konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="bd705-p115">Figure 17 shows a cross-premises VNet with DNS servers in the on-premises network and on a subnet in the VNet. DNS replication and forwarding has been configured between the two DNS servers.</span></span>
  
### <a name="step-7-determine-the-use-of-forced-tunneling"></a><span data-ttu-id="bd705-366">Schritt 7: Ermitteln Sie die Nutzung von erzwungenem Tunneln.</span><span class="sxs-lookup"><span data-stu-id="bd705-366">Step 7: Determine the use of forced tunneling.</span></span>

<span data-ttu-id="bd705-p116">Die Standardroute System für Azure Subnetze verweist auf das Internet. Um sicherzustellen, dass der gesamte Datenverkehr von virtuellen Computern in der standortübergreifenden Verbindung übermittelt wird, erstellen Sie eine routing-Tabelle mit der Standardroute, die als die Adresse des nächsten Hop das Azure-Gateway verwendet wird. Ordnen Sie dann die Routentabelle das Subnetz. Dies wird als tunneling gezwungen bezeichnet. Weitere Informationen finden Sie unter [Configure gezwungen tunneling](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-forced-tunneling-rm).</span><span class="sxs-lookup"><span data-stu-id="bd705-p116">The default system route for Azure subnets points to the Internet. To ensure that all traffic from virtual machines travels across the cross-premises connection, create a routing table with the default route that uses the Azure gateway as its next-hop address. You then associate the route table with the subnet. This is known as forced tunneling. For more information, see [Configure forced tunneling](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-forced-tunneling-rm).</span></span>
  
<span data-ttu-id="bd705-372">**Abbildung 18: User-defined Routen und erzwungener Tunnel für eine standortübergreifende VNet**</span><span class="sxs-lookup"><span data-stu-id="bd705-372">**Figure 18: User-defined routes and forced tunneling for a cross-premises VNet**</span></span>

![Abbildung 18: Benutzerdefinierte Routen und erzwungenes Tunneln für ein standortübergreifendes virtuelles Azure-Netzwerk ](images/1e545ec6-c2d9-48d2-bb5e-e0a581fee004.png)
  
<span data-ttu-id="bd705-374">Abbildung 18 zeigt eine standortübergreifende VNet mit einer benutzerdefinierten Route für ein Subnetz, dem Azure-Gateway verweisen.</span><span class="sxs-lookup"><span data-stu-id="bd705-374">Figure 18 shows a cross-premises VNet with a user-defined route for a subnet pointing to the Azure gateway.</span></span>
  
## <a name="sharepoint-server-2016-farm-in-azure"></a><span data-ttu-id="bd705-375">SharePoint Server 2016-Farm in Azure</span><span class="sxs-lookup"><span data-stu-id="bd705-375">SharePoint Server 2016 farm in Azure</span></span>
<span data-ttu-id="bd705-376"><a name="cross_prem"> </a></span><span class="sxs-lookup"><span data-stu-id="bd705-376"></span></span>

<span data-ttu-id="bd705-377">Ein Beispiel für eine in Azure IaaS gehostete intranetbasierte IT-Workload ist eine hoch verfügbare SharePoint Server 2016-Farm mit mehreren Stufen, wie sie in Abbildung 19 dargestellt ist.</span><span class="sxs-lookup"><span data-stu-id="bd705-377">An example of an intranet IT workload hosted in Azure IaaS is a highly-available, multi-tier SharePoint Server 2016 farm, as shown in Figure 19.</span></span>
  
<span data-ttu-id="bd705-378">**Abbildung 19: Eine hochverfügbar 2016 für SharePoint Server-intranetfarm in Azure IaaS**</span><span class="sxs-lookup"><span data-stu-id="bd705-378">**Figure 19: A highly-available intranet SharePoint Server 2016 farm in Azure IaaS**</span></span>

![Hoch verfügbare SharePoint Server 2016-Farm in Azure IaaS](images/3a922e21-df91-455f-ba90-78abdd48d98d.png)
  
<span data-ttu-id="bd705-p117">Abbildung 19 zeigt die neun Server einer 2016 für SharePoint Server-Farm bereitgestellt, die in einer standortübergreifenden VNet, die die internen Systeme zum Lastenausgleich für die Front-End- und Daten Ebenen verwendet. Weitere Informationen, einschließlich schrittweise Entwurf und Bereitstellung-Anweisungen finden Sie unter [SharePoint Server 2016 in Microsoft Azure](https://technet.microsoft.com/library/mt779107%28v=office.16%29.aspx).</span><span class="sxs-lookup"><span data-stu-id="bd705-p117">Figure 19 shows the nine servers of a SharePoint Server 2016 farm deployed in a cross-premises VNet that uses internal load balancers for the front-end and data tiers. For more information, including step-by-step design and deployment instructions, see [SharePoint Server 2016 in Microsoft Azure](https://technet.microsoft.com/library/mt779107%28v=office.16%29.aspx).</span></span>
  
> [!TIP]
> <span data-ttu-id="bd705-382">Zum Erstellen einer 2016 für SharePoint Server-Farm in einer standortübergreifenden simulierten VNet finden Sie unter [Intranet SharePoint Server 2016 in Azure Test-/-Umgebung](https://technet.microsoft.com/library/mt806351%28v=office.16%29.aspx).</span><span class="sxs-lookup"><span data-stu-id="bd705-382">To create a single-server SharePoint Server 2016 farm in a simulated cross-premises VNet, see [Intranet SharePoint Server 2016 in Azure dev/test environment](https://technet.microsoft.com/library/mt806351%28v=office.16%29.aspx).</span></span> 
  
<span data-ttu-id="bd705-383">Weitere Beispiele für IT-Arbeitslasten auf virtuellen Computern in einer standortübergreifenden Azure virtual bereitgestellten Netzwerk, finden Sie unter [Hybrid-Cloud-Szenarien für Azure IaaS](https://technet.microsoft.com/library/mt750502.aspx).</span><span class="sxs-lookup"><span data-stu-id="bd705-383">For additional examples of IT workloads deployed on virtual machines in a cross-premises Azure virtual network, see [Hybrid cloud scenarios for Azure IaaS](https://technet.microsoft.com/library/mt750502.aspx).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="bd705-384">See Also</span><span class="sxs-lookup"><span data-stu-id="bd705-384">See Also</span></span>

<span data-ttu-id="bd705-385"><a name="cross_prem"> </a></span><span class="sxs-lookup"><span data-stu-id="bd705-385"></span></span>

[<span data-ttu-id="bd705-386">Microsoft-Cloudnetzwerke für Enterprise-Architekten</span><span class="sxs-lookup"><span data-stu-id="bd705-386">Microsoft Cloud Networking for Enterprise Architects</span></span>](microsoft-cloud-networking-for-enterprise-architects.md)
  
[<span data-ttu-id="bd705-387">Ressourcen zur Cloud-IT-Architektur von Microsoft</span><span class="sxs-lookup"><span data-stu-id="bd705-387">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="bd705-388">Enterprise-Cloud-Roadmap von Microsoft: Ressourcen für IT-Entscheidungsträger</span><span class="sxs-lookup"><span data-stu-id="bd705-388">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)



