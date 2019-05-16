---
title: Entwerfen von Netzwerken für Microsoft Azure-IaaS
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/28/2018
audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 9cb70c9d-9ed9-47cc-af5a-6403d87d3372
description: 'Zusammenfassung: Hier erfahren Sie, wie Sie das optimierte Netzwerk für Arbeitsauslastungen in Microsoft Azure IaaS entwerfen.'
ms.openlocfilehash: b06564c8a86c59dac4ac9a5380cd88cf9d045974
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068131"
---
# <a name="designing-networking-for-microsoft-azure-iaas"></a><span data-ttu-id="e0c8f-103">Entwerfen von Netzwerken für Microsoft Azure-IaaS</span><span class="sxs-lookup"><span data-stu-id="e0c8f-103">Designing networking for Microsoft Azure IaaS</span></span>

 <span data-ttu-id="e0c8f-104">**Zusammenfassung:** Hier erfahren Sie, wie Sie das optimierte Netzwerk für Arbeitsauslastungen in Microsoft Azure IaaS entwerfen.</span><span class="sxs-lookup"><span data-stu-id="e0c8f-104">**Summary:** Understand how to design optimized networking for workloads in Microsoft Azure IaaS.</span></span>
  
<span data-ttu-id="e0c8f-105">Um Netzwerke für IT-Workloads, die in Azure IaaS gehostet werden, optimieren zu können, benötigen Sie als Voraussetzung grundlegende Kenntnisse über Azure Virtual Networks (VNets), Adressräume, Routing, DNS und Lastenausgleich.</span><span class="sxs-lookup"><span data-stu-id="e0c8f-105">Optimizing networking for IT workloads hosted in Azure IaaS requires an understanding of Azure virtual networks (VNets), address spaces, routing, DNS, and load balancing.</span></span>
  
## <a name="planning-steps-for-any-vnet"></a><span data-ttu-id="e0c8f-106">VNet-Planungsschritte</span><span class="sxs-lookup"><span data-stu-id="e0c8f-106">Planning steps for any VNet</span></span>

<span data-ttu-id="e0c8f-107">Führen Sie die folgenden Schritte für jede Art von VNet aus.</span><span class="sxs-lookup"><span data-stu-id="e0c8f-107">Follow these steps for any type of VNet.</span></span>
  
### <a name="step-1-prepare-your-intranet-for-microsoft-cloud-services"></a><span data-ttu-id="e0c8f-108">Schritt 1: Bereiten Sie das Intranet für Microsoft Cloud Services vor.</span><span class="sxs-lookup"><span data-stu-id="e0c8f-108">Step 1: Prepare your intranet for Microsoft cloud services.</span></span>

<span data-ttu-id="e0c8f-109">Durchlaufen Sie die **Schritte zum Vorbereiten Ihres Netzwerks für Microsoft Cloud Services** in [Gemeinsame Elemente der Microsoft-Cloudkonnektivität](common-elements-of-microsoft-cloud-connectivity.md).</span><span class="sxs-lookup"><span data-stu-id="e0c8f-109">Go through the **Steps to prepare your network for Microsoft cloud services** section in [Common elements of Microsoft cloud connectivity](common-elements-of-microsoft-cloud-connectivity.md).</span></span>
  
### <a name="step-2-optimize-your-internet-bandwidth"></a><span data-ttu-id="e0c8f-110">Schritt 2: Optimieren Sie die Internetbandbreite.</span><span class="sxs-lookup"><span data-stu-id="e0c8f-110">Step 2: Optimize your Internet bandwidth.</span></span>

<span data-ttu-id="e0c8f-111">Optimieren Sie die Internetbandbreite mithilfe der Schritte 2 bis 4 der **Schritte zum Vorbereiten Ihres Netzwerks für Microsoft SaaS-Dienste** in [Designing networking for Microsoft SaaS](designing-networking-for-microsoft-saas.md).</span><span class="sxs-lookup"><span data-stu-id="e0c8f-111">Optimize your Internet bandwidth using steps 2 - 4 of the **Steps to prepare your network for Microsoft SaaS services** section in [Designing networking for Microsoft SaaS](designing-networking-for-microsoft-saas.md).</span></span>
  
### <a name="step-3-determine-the-type-of-vnet-cloud-only-or-cross-premises"></a><span data-ttu-id="e0c8f-112">Schritt 3: Bestimmen Sie den VNet-Typ (reine Cloudbereitstellung oder standortübergreifend).</span><span class="sxs-lookup"><span data-stu-id="e0c8f-112">Step 3: Determine the type of VNet (cloud-only or cross-premises).</span></span>

<span data-ttu-id="e0c8f-p101">Eine reines Cloud-VNet hat keine Verbindung mit einem lokalen Netzwerk. Hier ein Beispiel:</span><span class="sxs-lookup"><span data-stu-id="e0c8f-p101">A cloud-only VNet has no connection to an on-premises network. Here is an example.</span></span>
  
<span data-ttu-id="e0c8f-115">**Abbildung 1: Reines Cloud-VNet**</span><span class="sxs-lookup"><span data-stu-id="e0c8f-115">**Figure 1: A cloud-only VNet**</span></span>

![Abbildung 1: ein virtuelles Cloud-Netzwerk in Azure](media/8be19104-02b3-4a7f-b0a0-30d6fcf8890b.png)
  
<span data-ttu-id="e0c8f-117">Abbildung 1 zeigt eine Reihe von virtuellen Computern in einem reinen Cloud-VNet.</span><span class="sxs-lookup"><span data-stu-id="e0c8f-117">Figure 1 shows a set of virtual machines in a cloud-only VNet.</span></span>
  
<span data-ttu-id="e0c8f-p102">Ein standortübergreifendes VNet verfügt über ein Azure-Gateway über eine S2S-VPN-Verbindung (Standort-zu-Standort) oder eine ExpressRoute-Verbindung zu einem lokalen Netzwerk. Hier ein Beispiel:</span><span class="sxs-lookup"><span data-stu-id="e0c8f-p102">A cross-premises VNet has a site-to-site (S2S) VPN or ExpressRoute connection to an on-premises network through an Azure gateway. Here is an example.</span></span>
  
<span data-ttu-id="e0c8f-120">**Abbildung 2: Ein standortübergreifendes VNet**</span><span class="sxs-lookup"><span data-stu-id="e0c8f-120">**Figure 2: A cross-premises VNet**</span></span>

![Abbildung 2: ein standortübergreifendes virtuelles Netzwerk in Azure](media/caacf007-e0dc-45d3-9531-441109776d25.png)
  
<span data-ttu-id="e0c8f-122">Abbildung 2 zeigt eine Reihe von virtuellen Computern in einem standortübergreifenden VNet, das mit einem lokalen Netzwerk verbunden ist.</span><span class="sxs-lookup"><span data-stu-id="e0c8f-122">Figure 2 shows a set of virtual machines in a cross-premises VNet, which is connected to an on-premises network.</span></span>
  
<span data-ttu-id="e0c8f-123">Weitere [Planungsschritte für ein standortübergreifendes VNet](designing-networking-for-microsoft-azure-iaas.md#cross_prem) finden Sie im entsprechenden Abschnitt in diesem Artikel.</span><span class="sxs-lookup"><span data-stu-id="e0c8f-123">See the additional [Planning steps for a cross-premises VNet](designing-networking-for-microsoft-azure-iaas.md#cross_prem) section in this article.</span></span>
  
### <a name="step-4-determine-the-address-space-of-the-vnet"></a><span data-ttu-id="e0c8f-124">Schritt 4: Ermitteln Sie den VNet-Adressraum.</span><span class="sxs-lookup"><span data-stu-id="e0c8f-124">Step 4: Determine the address space of the VNet.</span></span>

<span data-ttu-id="e0c8f-125">In Tabelle 1 sind die Adressräume für die verschiedenen VNet-Typen aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="e0c8f-125">Table 1 shows the address spaces for the different types of VNets.</span></span>
  
|<span data-ttu-id="e0c8f-126">**Typ des VNet**</span><span class="sxs-lookup"><span data-stu-id="e0c8f-126">**Type of VNet**</span></span>|<span data-ttu-id="e0c8f-127">**Adressraum des virtuellen Netzwerks**</span><span class="sxs-lookup"><span data-stu-id="e0c8f-127">**Virtual network address space**</span></span>|
|:-----|:-----|
|<span data-ttu-id="e0c8f-128">Rein cloudbasiert</span><span class="sxs-lookup"><span data-stu-id="e0c8f-128">Cloud-only</span></span>  <br/> |<span data-ttu-id="e0c8f-129">Beliebiger privater Adressraum</span><span class="sxs-lookup"><span data-stu-id="e0c8f-129">Arbitrary private address space</span></span>  <br/> |
|<span data-ttu-id="e0c8f-130">Miteinander verbunden, reine Cloudbereitstellung</span><span class="sxs-lookup"><span data-stu-id="e0c8f-130">Interconnected cloud-only</span></span>  <br/> |<span data-ttu-id="e0c8f-131">Beliebiges privates, jedoch nicht überlappend mit anderen verbundenen VNets</span><span class="sxs-lookup"><span data-stu-id="e0c8f-131">Arbitrary private, but not overlapping with other connected VNets</span></span>  <br/> |
|<span data-ttu-id="e0c8f-132">Standortübergreifend</span><span class="sxs-lookup"><span data-stu-id="e0c8f-132">Cross-premises</span></span>  <br/> |<span data-ttu-id="e0c8f-133">Privater Adressraum, der jedoch nicht mit lokalen VNets überlappt</span><span class="sxs-lookup"><span data-stu-id="e0c8f-133">Private, but not overlapping with on-premises</span></span>  <br/> |
|<span data-ttu-id="e0c8f-134">Miteinander verbunden, standortübergreifend</span><span class="sxs-lookup"><span data-stu-id="e0c8f-134">Interconnected cross-premises</span></span>  <br/> |<span data-ttu-id="e0c8f-135">Privater Adressraum, der jedoch nicht mit lokalen und anderen verbundenen VNets überlappt</span><span class="sxs-lookup"><span data-stu-id="e0c8f-135">Private, but not overlapping with on-premises and other connected VNets</span></span>  <br/> |
   
 <span data-ttu-id="e0c8f-136">**Tabelle 1: VNet-Typen und ihr entsprechender Adressraum**</span><span class="sxs-lookup"><span data-stu-id="e0c8f-136">**Table 1: Types of VNets and their corresponding address space**</span></span>
  
<span data-ttu-id="e0c8f-137">Virtuellen Computern wird vom Adressraum des Subnetzes durch DHCP ein Adresskonfiguriation zugewiesen:</span><span class="sxs-lookup"><span data-stu-id="e0c8f-137">Virtual machines are assigned an address configuration from the address space of the subnet by DHCP:</span></span>
  
- <span data-ttu-id="e0c8f-138">Adresse/Subnetzmaske</span><span class="sxs-lookup"><span data-stu-id="e0c8f-138">Address/subnet mask</span></span>
    
- <span data-ttu-id="e0c8f-139">Standardgateway</span><span class="sxs-lookup"><span data-stu-id="e0c8f-139">Default gateway</span></span>
    
- <span data-ttu-id="e0c8f-140">IP-Adressen des DNS-Servers</span><span class="sxs-lookup"><span data-stu-id="e0c8f-140">DNS server IP addresses</span></span>
    
<span data-ttu-id="e0c8f-141">Sie können auch eine statische IP-Adresse reservieren.</span><span class="sxs-lookup"><span data-stu-id="e0c8f-141">You can also reserve a static IP address.</span></span>
  
<span data-ttu-id="e0c8f-142">Virtuellen Computern kann auch eine öffentliche IP-Adresse zugewiesen werden, entweder einzeln oder über den enthaltenden Clouddienst (nur für herkömmliche Bereitstellungscomputer).</span><span class="sxs-lookup"><span data-stu-id="e0c8f-142">Virtual machines can also be assigned a public IP address, either individually or from the containing cloud service (for classic deployment machines only).</span></span>
  
### <a name="step-5-determine-the-subnets-within-the-vnet-and-the-address-spaces-assigned-to-each"></a><span data-ttu-id="e0c8f-143">Schritt 5: Bestimmen Sie die Subnetze im VNet und die ihnen zugewiesenen Adressräume.</span><span class="sxs-lookup"><span data-stu-id="e0c8f-143">Step 5: Determine the subnets within the VNet and the address spaces assigned to each.</span></span>

<span data-ttu-id="e0c8f-144">Es gibt zwei Arten von Subnetzen in einem VNet: ein Gatewaysubnetz und ein Hostingsubnetz für virtuelle Computer.</span><span class="sxs-lookup"><span data-stu-id="e0c8f-144">There are two types of subnets in a VNet, a gateway subnet and a virtual machine-hosting subnet.</span></span>
  
<span data-ttu-id="e0c8f-145">**Abbildung 3: Die zwei Arten von Subnetzen in Azure**</span><span class="sxs-lookup"><span data-stu-id="e0c8f-145">**Figure 3: The two types of subnets in Azure**</span></span>

![Abbildung 3: Die zwei Arten von Subnetzen in Azure](media/2eaa512d-1293-4e9b-b927-6bfe0fc0acb4.png)
  
<span data-ttu-id="e0c8f-147">Abbildung 3 zeigt eine VNet mit einem Gateway-Subnetz, das über ein Azure-Gateway und einen Satz virtueller Computer gehosteter Subnetze mit virtuellen Computern verfügt.</span><span class="sxs-lookup"><span data-stu-id="e0c8f-147">Figure 3 shows a VNet containing a gateway subnet that has an Azure gateway and a set of virtual machine-hosting subnets containing virtual machines.</span></span>
  
<span data-ttu-id="e0c8f-148">Azure benötigt das Azure-Gatewaysubnetz zum Hosten der beiden virtuellen Computer Ihres Azure-Gateways.</span><span class="sxs-lookup"><span data-stu-id="e0c8f-148">The Azure gateway subnet is needed by Azure to host the two virtual machines of your Azure gateway.</span></span> <span data-ttu-id="e0c8f-149">Angeben eines Adressraums mit einer Präfixlänge von mindestens 29 Bit (Beispiel: 192.168.15.248/29).</span><span class="sxs-lookup"><span data-stu-id="e0c8f-149">Specify an address space with at least a 29-bit prefix length (example: 192.168.15.248/29).</span></span> <span data-ttu-id="e0c8f-150">Eine 27-Bit-oder eine kleinere Präfixlänge wird empfohlen, insbesondere, wenn Sie Express Route verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="e0c8f-150">A 27-bit or smaller prefix length is recommended, especially if you are planning to use ExpressRoute.</span></span>
  
<span data-ttu-id="e0c8f-151">Eine bewährte Methode zum Bestimmen des Adressraums des Azure-Gateway-Subnetzes ist:</span><span class="sxs-lookup"><span data-stu-id="e0c8f-151">A best practice for determining the address space of the Azure gateway subnet is:</span></span>
  
1. <span data-ttu-id="e0c8f-152">Legen Sie die Größe des Gatewaysubnetzes fest.</span><span class="sxs-lookup"><span data-stu-id="e0c8f-152">Decide on the size of the gateway subnet.</span></span>
    
2. <span data-ttu-id="e0c8f-153">Legen Sie für die variablen Bits im Adressraum des VNet die Bits für das Gatewaysubnetz auf 0 und für die anderen Bits auf 1 fest.</span><span class="sxs-lookup"><span data-stu-id="e0c8f-153">In the variable bits in the address space of the VNet, set the bits used for the gateway subnet to 0 and set the remaining bits to 1.</span></span>
    
3. <span data-ttu-id="e0c8f-154">Konvertieren Sie dies in eine Dezimalzahl, und drücken Sie diese als Adressraum aus, wobei Sie als Präfixlänge die Größe des Gatewaysubnetzes festlegen.</span><span class="sxs-lookup"><span data-stu-id="e0c8f-154">Convert to decimal and express as an address space with the prefix length set to the size of the gateway subnet.</span></span>
    
<span data-ttu-id="e0c8f-155">Wenn Sie diese Methode verwenden, befindet sich der Adressraum für das Gatewaysubnetz immer am äußersten Ende des VNet-Adressbereichs.</span><span class="sxs-lookup"><span data-stu-id="e0c8f-155">With this method, the address space for the gateway subnet is always at the farthest end of the VNet address space.</span></span>
  
<span data-ttu-id="e0c8f-p104">Es folgt ein Beispiel für die Definition des Adresspräfixes für das Gatewaysubnetz: Der Adressraum des VNet ist 10.119.0.0/16. Die Organisation verwendet anfänglich eine Standort-zu-Standort-VPN-Verbindung, später jedoch ExpressRoute. In Tabelle 2 sind die Schritte sowie die Ergebnisse der Ermittlung des Adresspräfixes in der Netzwerkpräfixnotation für das Gatewaysubnetz aufgeführt (auch als CIDR bezeichnet).</span><span class="sxs-lookup"><span data-stu-id="e0c8f-p104">Here is an example of defining the address prefix for the gateway subnet: The address space of the VNet is 10.119.0.0/16. The organization will initially use a site-to-site VPN connection, but will eventually get ExpressRoute. Table 2 shows the steps and results of determining the gateway subnet address prefix in network prefix notation (also known as CIDR).</span></span>

<span data-ttu-id="e0c8f-159">Nachfolgend finden Sie die Schritte und Beispiele zum Bestimmen des Gateway-Subnetz-Adress Präfixes:</span><span class="sxs-lookup"><span data-stu-id="e0c8f-159">Here are the steps and example of determining the gateway subnet address prefix:</span></span>

1. <span data-ttu-id="e0c8f-160">Legen Sie die Größe des Gatewaysubnetzes fest.</span><span class="sxs-lookup"><span data-stu-id="e0c8f-160">Decide on the size of the gateway subnet.</span></span> <span data-ttu-id="e0c8f-161">Für unser Beispiel haben wir uns für/28 entschieden.</span><span class="sxs-lookup"><span data-stu-id="e0c8f-161">For our example, we chose /28.</span></span>
2. <span data-ttu-id="e0c8f-162">Legen Sie die Bits im Variablen Teil des VNet-Adressraums (b) auf 0 für die Gateway-Subnetz-Bits (G) fest, andernfalls 1 (V).</span><span class="sxs-lookup"><span data-stu-id="e0c8f-162">Set the bits in the variable portion of the VNet address space (b) to 0 for the gateway subnet bits (G), otherwise 1 (V).</span></span> <span data-ttu-id="e0c8f-163">Für unser Beispiel verwenden wir den 10.119.0.0/16-Adressraum für die VNet.</span><span class="sxs-lookup"><span data-stu-id="e0c8f-163">For our example, we are using the 10.119.0.0/16 address space for the VNet.</span></span>
<br/>
<br/><span data-ttu-id="e0c8f-164">10,119.</span><span class="sxs-lookup"><span data-stu-id="e0c8f-164">10.119.</span></span> <span data-ttu-id="e0c8f-165">bbbbbbbb.</span><span class="sxs-lookup"><span data-stu-id="e0c8f-165">bbbbbbbb .</span></span> <span data-ttu-id="e0c8f-166">bbbbbbbb</span><span class="sxs-lookup"><span data-stu-id="e0c8f-166">bbbbbbbb</span></span>
<br/><span data-ttu-id="e0c8f-167">10,119.</span><span class="sxs-lookup"><span data-stu-id="e0c8f-167">10.119.</span></span> <span data-ttu-id="e0c8f-168">VVVVVVVV .</span><span class="sxs-lookup"><span data-stu-id="e0c8f-168">VVVVVVVV .</span></span> <span data-ttu-id="e0c8f-169">VVVVGGGG</span><span class="sxs-lookup"><span data-stu-id="e0c8f-169">VVVVGGGG</span></span>
<br/><span data-ttu-id="e0c8f-170">10,119.</span><span class="sxs-lookup"><span data-stu-id="e0c8f-170">10.119.</span></span> <span data-ttu-id="e0c8f-171">11111111.</span><span class="sxs-lookup"><span data-stu-id="e0c8f-171">11111111 .</span></span> <span data-ttu-id="e0c8f-172">11110000</span><span class="sxs-lookup"><span data-stu-id="e0c8f-172">11110000</span></span>
<br/><br/>
3. <span data-ttu-id="e0c8f-173">Konvertieren Sie das Ergebnis aus Schritt 2 in Dezimal und Express als Adressraum.</span><span class="sxs-lookup"><span data-stu-id="e0c8f-173">Convert the result from step 2 to decimal and express as an address space.</span></span> <span data-ttu-id="e0c8f-174">Für unser Beispiel 10,119.</span><span class="sxs-lookup"><span data-stu-id="e0c8f-174">For our example, 10.119.</span></span> <span data-ttu-id="e0c8f-175">11111111.</span><span class="sxs-lookup"><span data-stu-id="e0c8f-175">11111111 .</span></span> <span data-ttu-id="e0c8f-176">11110000 ist 10.119.255.240, und mit der Präfixlänge aus Schritt 1 (28 in unserem Beispiel) lautet das resultierende Gateway-Subnetz-Adresspräfix 10.119.255.240/28.</span><span class="sxs-lookup"><span data-stu-id="e0c8f-176">11110000 is 10.119.255.240, and with the prefix length from step 1, (28 in our example), the resulting gateway subnet address prefix is 10.119.255.240/28.</span></span>
  
<span data-ttu-id="e0c8f-177">Weitere Informationen finden Sie unter [Adressraum Rechner für Azure-Gateway](https://gallery.technet.microsoft.com/scriptcenter/Address-prefix-calculator-a94b6eed) -Subnetze.</span><span class="sxs-lookup"><span data-stu-id="e0c8f-177">See [Address space calculator for Azure gateway subnets](https://gallery.technet.microsoft.com/scriptcenter/Address-prefix-calculator-a94b6eed) for more information.</span></span>
  
<span data-ttu-id="e0c8f-178">Sie platzieren virtuelle Azure-Computer in Hostingsubnetzen für virtuelle Computer, wobei Sie hier gemäß den typisch lokalen Richtlinien folgen können, wie z. B. einer allgemeinen Rolle oder Ebene einer Anwendung oder für die Subnetzisolierung.</span><span class="sxs-lookup"><span data-stu-id="e0c8f-178">Virtual machine-hosting subnets are where you place Azure virtual machines, which you can do according to typical on-premises guidelines, such as a common role or tier of an application or for subnet isolation.</span></span>
  
<span data-ttu-id="e0c8f-179">Azure verwendet die ersten drei Adressen in jedem Subnetz.</span><span class="sxs-lookup"><span data-stu-id="e0c8f-179">Azure uses the first 3 addresses on each subnet.</span></span> <span data-ttu-id="e0c8f-180">Daher ist die Anzahl der möglichen Adressen in einem Azure-Subnetz 2<sup>n</sup> -5, wobei n die Anzahl der Host-Bits ist.</span><span class="sxs-lookup"><span data-stu-id="e0c8f-180">Therefore, the number of possible addresses on an Azure subnet is 2<sup>n</sup> - 5, where n is the number of host bits.</span></span> <span data-ttu-id="e0c8f-181">In Tabelle 3 sind der Bereich der erforderlichen virtuellen Computer, die Anzahl der erforderlichen Hostbits und die entsprechende Subnetzgröße aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="e0c8f-181">Table 3 shows the range of virtual machines required, the number of hosts bits needed, and the corresponding subnet size.</span></span>
  
|<span data-ttu-id="e0c8f-182">**Erforderliche virtuelle Computer**</span><span class="sxs-lookup"><span data-stu-id="e0c8f-182">**Virtual machines required**</span></span>|<span data-ttu-id="e0c8f-183">**Hostbits**</span><span class="sxs-lookup"><span data-stu-id="e0c8f-183">**Host bits**</span></span>|<span data-ttu-id="e0c8f-184">**Subnetzgröße**</span><span class="sxs-lookup"><span data-stu-id="e0c8f-184">**Subnet size**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="e0c8f-185">1-3</span><span class="sxs-lookup"><span data-stu-id="e0c8f-185">1-3</span></span>  <br/> |<span data-ttu-id="e0c8f-186">3</span><span class="sxs-lookup"><span data-stu-id="e0c8f-186">3</span></span>  <br/> |<span data-ttu-id="e0c8f-187">/29</span><span class="sxs-lookup"><span data-stu-id="e0c8f-187">/29</span></span>  <br/> |
|<span data-ttu-id="e0c8f-188">4-11</span><span class="sxs-lookup"><span data-stu-id="e0c8f-188">4-11</span></span>  <br/> |<span data-ttu-id="e0c8f-189">4</span><span class="sxs-lookup"><span data-stu-id="e0c8f-189">4</span></span>  <br/> |<span data-ttu-id="e0c8f-190">/28</span><span class="sxs-lookup"><span data-stu-id="e0c8f-190">/28</span></span>  <br/> |
|<span data-ttu-id="e0c8f-191">12-27</span><span class="sxs-lookup"><span data-stu-id="e0c8f-191">12-27</span></span>  <br/> |<span data-ttu-id="e0c8f-192">5</span><span class="sxs-lookup"><span data-stu-id="e0c8f-192">5</span></span>  <br/> |<span data-ttu-id="e0c8f-193">/27</span><span class="sxs-lookup"><span data-stu-id="e0c8f-193">/27</span></span>  <br/> |
|<span data-ttu-id="e0c8f-194">28-59</span><span class="sxs-lookup"><span data-stu-id="e0c8f-194">28-59</span></span>  <br/> |<span data-ttu-id="e0c8f-195">6</span><span class="sxs-lookup"><span data-stu-id="e0c8f-195">6</span></span>  <br/> |<span data-ttu-id="e0c8f-196">/26</span><span class="sxs-lookup"><span data-stu-id="e0c8f-196">/26</span></span>  <br/> |
|<span data-ttu-id="e0c8f-197">60-123</span><span class="sxs-lookup"><span data-stu-id="e0c8f-197">60-123</span></span>  <br/> |<span data-ttu-id="e0c8f-198">7</span><span class="sxs-lookup"><span data-stu-id="e0c8f-198">7</span></span>  <br/> |<span data-ttu-id="e0c8f-199">/25</span><span class="sxs-lookup"><span data-stu-id="e0c8f-199">/25</span></span>  <br/> |
   
 <span data-ttu-id="e0c8f-200">**Tabelle 3: Anforderungen der virtuellen Computer und ihre Subnetzgrößen**</span><span class="sxs-lookup"><span data-stu-id="e0c8f-200">**Table 3: Virtual machine requirements and their subnet sizes**</span></span>
  
<span data-ttu-id="e0c8f-201">Weitere Informationen zur maximalen Anzahl von virtuellen Computern in einem Subnetz oder VNet finden Sie unter [Networking Limits](https://docs.microsoft.com/azure/azure-subscription-service-limits#networking-limits).</span><span class="sxs-lookup"><span data-stu-id="e0c8f-201">For more information about the maximum amount of virtual machines on a subnet or VNet, see [Networking Limits](https://docs.microsoft.com/azure/azure-subscription-service-limits#networking-limits).</span></span>
  
<span data-ttu-id="e0c8f-202">Weitere Informationen finden Sie unter [Planen und Entwerfen von virtuellen Azure-Netzwerken](https://azure.microsoft.com/documentation/articles/virtual-network-vnet-plan-design-arm/).</span><span class="sxs-lookup"><span data-stu-id="e0c8f-202">For more information, see [Plan and design Azure Virtual Networks](https://azure.microsoft.com/documentation/articles/virtual-network-vnet-plan-design-arm/).</span></span>
  
### <a name="step-6-determine-the-dns-server-configuration-and-the-addresses-of-the-dns-servers-to-assign-to-vms-in-the-vnet"></a><span data-ttu-id="e0c8f-203">Schritt 6: Ermitteln Sie die DNS-Serverkonfiguration und die Adressen der DNS-Server, die den VMs im VNet zugewiesen werden sollen.</span><span class="sxs-lookup"><span data-stu-id="e0c8f-203">Step 6: Determine the DNS server configuration and the addresses of the DNS servers to assign to VMs in the VNet.</span></span>

<span data-ttu-id="e0c8f-p112">Azure weist virtuellen Computern die Adressen der DNS-Server über DHCP zu. DNS-Server können:</span><span class="sxs-lookup"><span data-stu-id="e0c8f-p112">Azure assigns virtual machines the addresses of DNS servers by DHCP. DNS servers can be:</span></span>
  
- <span data-ttu-id="e0c8f-206">durch Azure bereitgestellt werden: Bietet lokale Namensregistrierung sowie lokale und über das Internet durchgeführte Namensauflösung</span><span class="sxs-lookup"><span data-stu-id="e0c8f-206">Supplied by Azure: Provides local name registration and local and Internet name resolution</span></span>
    
- <span data-ttu-id="e0c8f-207">von Ihnen bereitgestellt werden: Bietet lokale oder über das Internet durchgeführte Namensregistrierung und Namensauflösung entweder über das Intranet oder über das Internet</span><span class="sxs-lookup"><span data-stu-id="e0c8f-207">Provided by you: Provides local or intranet name registration and either intranet or Internet name resolution</span></span>
    
<span data-ttu-id="e0c8f-208">In Tabelle 4 sind die verschiedenen DNS-Serverkonfigurationen für jeden VNet-Typ aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="e0c8f-208">Table 4 shows the different configurations of DNS servers for each type of VNet.</span></span>
    
|<span data-ttu-id="e0c8f-209">**Typ des VNet**</span><span class="sxs-lookup"><span data-stu-id="e0c8f-209">**Type of VNet**</span></span>|<span data-ttu-id="e0c8f-210">**DNS-Server**</span><span class="sxs-lookup"><span data-stu-id="e0c8f-210">**DNS server**</span></span>|
|:-----|:-----|
|<span data-ttu-id="e0c8f-211">Rein cloudbasiert</span><span class="sxs-lookup"><span data-stu-id="e0c8f-211">Cloud-only</span></span>  <br/> |<span data-ttu-id="e0c8f-212">von Azure für die lokale und über das Internet durchgeführte Namensauflösung bereitgestellt</span><span class="sxs-lookup"><span data-stu-id="e0c8f-212">Azure-supplied for local and Internet name resolution</span></span>  <br/> <span data-ttu-id="e0c8f-213">virtueller Azure-Computer für die lokale und über das Internet durchgeführte Namensauflösung (DNS-Weiterleitung)</span><span class="sxs-lookup"><span data-stu-id="e0c8f-213">Azure virtual machine for local and Internet name resolution (DNS forwarding)</span></span>  <br/> |
|<span data-ttu-id="e0c8f-214">Standortübergreifend</span><span class="sxs-lookup"><span data-stu-id="e0c8f-214">Cross-premises</span></span>  <br/> |<span data-ttu-id="e0c8f-215">lokal für die lokale und über das Intranet durchgeführte Namensauflösung</span><span class="sxs-lookup"><span data-stu-id="e0c8f-215">On-premises for local and intranet name resolution</span></span>  <br/> <span data-ttu-id="e0c8f-216">virtueller Azure-Computer für die lokale und über das Intranet durchgeführte Namensauflösung (DNS-Replikation und -Weiterleitung)</span><span class="sxs-lookup"><span data-stu-id="e0c8f-216">Azure virtual machine for local and intranet name resolution (DNS replication and forwarding)</span></span>  <br/> |
   
 <span data-ttu-id="e0c8f-217">**Tabelle 4: DNS-Serveroptionen für die beiden verschiedenen VNet-Typen**</span><span class="sxs-lookup"><span data-stu-id="e0c8f-217">**Table 4: DNS server options for the two different types of VNets**</span></span>
  
<span data-ttu-id="e0c8f-218">Weitere Informationen finden Sie unter [Namensauflösung für VMS und Rolleninstanzen](https://docs.microsoft.com/azure/virtual-network/virtual-networks-name-resolution-for-vms-and-role-instances).</span><span class="sxs-lookup"><span data-stu-id="e0c8f-218">For more information, see [Name Resolution for VMs and Role Instances](https://docs.microsoft.com/azure/virtual-network/virtual-networks-name-resolution-for-vms-and-role-instances).</span></span>
  
### <a name="step-7-determine-the-load-balancing-configuration-internet-facing-or-internal"></a><span data-ttu-id="e0c8f-219">Schritt 7: Ermitteln Sie die Lastenausgleichskonfiguration (Internet-bezogen oder intern).</span><span class="sxs-lookup"><span data-stu-id="e0c8f-219">Step 7: Determine the load balancing configuration (Internet-facing or internal).</span></span>

<span data-ttu-id="e0c8f-p113">In einigen Fällen möchten Sie eingehenden Datenverkehr auf eine Gruppe von Servern verteilen, die über die gleiche Rolle verfügen. Azure IaaS verfügt über eine integrierte Funktion, mit der dies für dem Internet zugewandten und internen Datenverkehr vorgenommen werden kann.</span><span class="sxs-lookup"><span data-stu-id="e0c8f-p113">In some cases, you want to distribute incoming traffic to a set of servers that have the same role. Azure IaaS has a built-in facility to do this for Internet-facing and internal traffic loads.</span></span>
  
<span data-ttu-id="e0c8f-222">Der dem Internet zugewandte Lastenausgleich von Azure verteilt den unangefordert aus dem Internet kommenden Datenverkehr zufällig auf die Mitglieder einer Lastenausgleichsgruppe. </span><span class="sxs-lookup"><span data-stu-id="e0c8f-222">Azure Internet-facing load balancing randomly distributes unsolicited incoming traffic from the Internet to the members of a load-balanced set.</span></span>
  
<span data-ttu-id="e0c8f-223">**Abbildung 4: Ein externer Lastenausgleich in Azure**</span><span class="sxs-lookup"><span data-stu-id="e0c8f-223">**Figure 4: An external load balancer in Azure**</span></span>

![Abbildung 4: Ein externer Lastenausgleich in Azure](media/eb5945e5-0c2b-40f1-b9ed-54bb2b0f9e59.png)
  
<span data-ttu-id="e0c8f-225">Abbildung 4 zeigt einen externen Lastenausgleich in Azure, der eingehenden Datenverkehr über eine eingehende NAT-Regel oder einen Endpunkt an eine Gruppe virtueller Computer in einem Satz mit Lastenausgleich verteilt.</span><span class="sxs-lookup"><span data-stu-id="e0c8f-225">Figure 4 shows an external load balancer in Azure that distributes incoming traffic on an inbound NAT rule or endpoint to a set of virtual machines in a load-balanced set.</span></span>
  
<span data-ttu-id="e0c8f-226">Der Azure-interne Lastenausgleich verteilt unangeforderten eingehenden Datenverkehr von andere Azure-VMs oder Intranetcomputern an die Mitglieder einer Lastenausgleichsgruppe. </span><span class="sxs-lookup"><span data-stu-id="e0c8f-226">Azure internal load balancing randomly distributes unsolicited incoming traffic from other Azure VMs or from intranet computers to the members of a load-balanced set.</span></span> 
  
<span data-ttu-id="e0c8f-227">**Abbildung 5: Ein interner Lastenausgleich in Azure**</span><span class="sxs-lookup"><span data-stu-id="e0c8f-227">**Figure 5: An internal load balancer in Azure**</span></span>

![Abbildung 5: Ein interner Lastenausgleich in Azure](media/d1451b73-6465-449d-b3e6-22160ce51f35.png)
  
<span data-ttu-id="e0c8f-229">Abbildung 5 zeigt einen internen Lastenausgleich in Azure, der eingehenden Datenverkehr für eine eingehende NAT-Regel oder einen Endpunkt an eine Gruppe virtueller Computer in einem Satz mit Lastenausgleich verteilt.</span><span class="sxs-lookup"><span data-stu-id="e0c8f-229">Figure 5 shows an internal load balancer in Azure that distributes incoming traffic on an inbound NAT rule or endpoint to a set of virtual machines in a load-balanced set.</span></span>
  
<span data-ttu-id="e0c8f-230">Weitere Informationen finden Sie unter [Azure-Lastenausgleichsmodul](https://docs.microsoft.com/azure/load-balancer/load-balancer-overview).</span><span class="sxs-lookup"><span data-stu-id="e0c8f-230">For more information, see [Azure Load Balancer](https://docs.microsoft.com/azure/load-balancer/load-balancer-overview).</span></span>
  
### <a name="step-8-determine-the-use-of-virtual-appliances-and-user-defined-routes"></a><span data-ttu-id="e0c8f-231">Schritt 8: Ermitteln Sie die Verwendung von virtuellen Geräten und benutzerdefinierten Routen.</span><span class="sxs-lookup"><span data-stu-id="e0c8f-231">Step 8: Determine the use of virtual appliances and user-defined routes.</span></span>

<span data-ttu-id="e0c8f-232">Wenn Sie Datenverkehrs an virtuelle Geräte im VNet weiterleiten müssen, müssen Sie einem Subnetz möglicherweise eine oder mehrere benutzerdefinierte Routen hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="e0c8f-232">If you need to forward traffic to virtual appliances in your VNet, you may need to add one or more user-defined routes to a subnet.</span></span>
  
<span data-ttu-id="e0c8f-233">**Abbildung 6: Virtuelle Geräte und benutzerdefinierte Routen in Azure**</span><span class="sxs-lookup"><span data-stu-id="e0c8f-233">**Figure 6: Virtual appliances and user-defined routes in Azure**</span></span>

![Abbildung 6: Virtuelle Geräte und benutzerdefinierte Routen in Azure](media/f181d0f4-ebf9-439e-9c98-dec17428c32b.png)
  
<span data-ttu-id="e0c8f-235">Abbildung 6 zeigt ein standortübergreifendes VNet und eine benutzerdefinierte Route, die einem Hostingsubnetz für virtuelle Computer zugewiesen ist, das auf ein virtuelles Gerät verweist.</span><span class="sxs-lookup"><span data-stu-id="e0c8f-235">Figure 6 shows a cross-premises VNet and a user-defined route assigned to a virtual machine-hosting subnet that points to a virtual appliance.</span></span>
  
<span data-ttu-id="e0c8f-236">Weitere Informationen finden Sie unter [benutzerdefinierte Routen und IP-Weiterleitung](https://docs.microsoft.com/azure/virtual-network/virtual-networks-udr-overview).</span><span class="sxs-lookup"><span data-stu-id="e0c8f-236">For more information, see [User Defined Routes and IP Forwarding](https://docs.microsoft.com/azure/virtual-network/virtual-networks-udr-overview).</span></span>
  
### <a name="step-9-determine-how-computers-from-the-internet-will-connect-to-virtual-machines"></a><span data-ttu-id="e0c8f-237">Schritt 9 Ermitteln Sie, wie Computer aus dem Internet Verbindungen mit virtuellen Computern herstellen.</span><span class="sxs-lookup"><span data-stu-id="e0c8f-237">Step 9: Determine how computers from the Internet will connect to virtual machines.</span></span>

<span data-ttu-id="e0c8f-238">Es gibt mehrere Möglichkeiten, den virtuellen Computern in einem VNet Zugang zum Internet bereitzustellen. Dazu zählt der Zugriff vom Netzwerk Ihrer Organisation über einen Proxyserver oder ein anderes Edgegerät.</span><span class="sxs-lookup"><span data-stu-id="e0c8f-238">There are multiple ways to provide Internet access to the virtual machines on a VNet, which includes access from your organization network through your proxy server or other edge device.</span></span>
  
<span data-ttu-id="e0c8f-239">In Tabelle 5 sind die Methoden zum Filtern oder Prüfen von unangefordert eingehendem Datenverkehr aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="e0c8f-239">Table 5 lists the methods for filtering or inspecting unsolicited incoming traffic.</span></span>
  
|<span data-ttu-id="e0c8f-240">**Methode**</span><span class="sxs-lookup"><span data-stu-id="e0c8f-240">**Method**</span></span>|<span data-ttu-id="e0c8f-241">**Bereitstellungsmodell**</span><span class="sxs-lookup"><span data-stu-id="e0c8f-241">**Deployment model**</span></span>|
|:-----|:-----|
|<span data-ttu-id="e0c8f-242">1. Endpunkte und ACLs, für Clouddienste konfiguriert</span><span class="sxs-lookup"><span data-stu-id="e0c8f-242">1. Endpoints and ACLs configured on cloud services</span></span>  <br/> |<span data-ttu-id="e0c8f-243">Classic</span><span class="sxs-lookup"><span data-stu-id="e0c8f-243">Classic</span></span>  <br/> |
|<span data-ttu-id="e0c8f-244">2. Netzwerksicherheitsgruppen</span><span class="sxs-lookup"><span data-stu-id="e0c8f-244">2. Network security groups</span></span>  <br/> |<span data-ttu-id="e0c8f-245">Ressourcenmanager und klassisch</span><span class="sxs-lookup"><span data-stu-id="e0c8f-245">Resource Manager and classic</span></span>  <br/> |
|<span data-ttu-id="e0c8f-246">3. Dem Internet zugewandter Lastenausgleich mit NAT-Eingangsregeln</span><span class="sxs-lookup"><span data-stu-id="e0c8f-246">3. Internet-facing load balancer with inbound NAT rules</span></span>  <br/> |<span data-ttu-id="e0c8f-247">Ressourcenmanager</span><span class="sxs-lookup"><span data-stu-id="e0c8f-247">Resource Manager</span></span>  <br/> |
|<span data-ttu-id="e0c8f-248">4. Netzwerksicherheits-Appliances im Azure Marketplace (nicht dargestellt)</span><span class="sxs-lookup"><span data-stu-id="e0c8f-248">4. Network security appliances in the Azure Marketplace (not shown)</span></span>  <br/> |<span data-ttu-id="e0c8f-249">Ressourcenmanager und klassisch</span><span class="sxs-lookup"><span data-stu-id="e0c8f-249">Resource Manager and classic</span></span>  <br/> |
   
 <span data-ttu-id="e0c8f-250">**Tabelle 5: Methoden zum Herstellen einer Verbindung mit virtuellen Computern und ihre entsprechenden Azure-Bereitstellungsmodelle**</span><span class="sxs-lookup"><span data-stu-id="e0c8f-250">**Table 5: Methods of connecting to virtual machines and their corresponding Azure deployment models**</span></span>
  
<span data-ttu-id="e0c8f-251">**Abbildung 7: Herstellen einer Verbindung mit virtuellen Azure-Computern über das Internet**</span><span class="sxs-lookup"><span data-stu-id="e0c8f-251">**Figure 7: Connecting to Azure virtual machines over the Internet**</span></span>

![Abbildung 7: Herstellen einer Verbindung mit virtuellen Azure-Computern über das Internet](media/c5e3531b-170a-4482-a6ff-fb8fbbe81b35.png)
  
<span data-ttu-id="e0c8f-253">Abbildung 7 zeigt einen mit dem Internet verbundenen Computer, der mit einem virtuellen Computer in einem Clouddienst anhand eines Endpunkts verbunden ist, einen virtuellen Computer in einem Subnetz mit einer Netzwerksicherheitsgruppe und einen virtuellen Computer in einem Subnetz mit einem externen Lastenausgleich und NAT-Eingangsregeln.</span><span class="sxs-lookup"><span data-stu-id="e0c8f-253">Figure 7 shows an Internet-connected computer connecting to a virtual machine in a cloud service using an endpoint, a virtual machine on a subnet using a network security group, and a virtual machine on a subnet using an external load balancer and inbound NAT rules.</span></span>
  
<span data-ttu-id="e0c8f-254">Zusätzlicher Sicherheit bereitgestellt durch:</span><span class="sxs-lookup"><span data-stu-id="e0c8f-254">Additional security is provided by:</span></span>
  
- <span data-ttu-id="e0c8f-255">Remotedesktop- und SSH-Verbindungen, die verschlüsselt und authentifiziert werden</span><span class="sxs-lookup"><span data-stu-id="e0c8f-255">Remote Desktop and SSH connections, which are authenticated and encrypted.</span></span>
    
- <span data-ttu-id="e0c8f-256">Remote PowerShell-Sitzungen, die verschlüsselt und authentifiziert werden</span><span class="sxs-lookup"><span data-stu-id="e0c8f-256">Remote PowerShell sessions, which are authenticated and encrypted.</span></span>
    
- <span data-ttu-id="e0c8f-257">IPsec-Transportmodus, den Sie für die End-to-End-Verschlüsselung verwenden können</span><span class="sxs-lookup"><span data-stu-id="e0c8f-257">IPsec transport mode, which you can use for end-to-end encryption.</span></span>
    
- <span data-ttu-id="e0c8f-258">Azure DDOS-Schutz, der vor externe und interne Angriffen schützt</span><span class="sxs-lookup"><span data-stu-id="e0c8f-258">Azure DDOS protection, which helps prevent external and internal attacks</span></span>
    
<span data-ttu-id="e0c8f-259">Weitere Informationen finden Sie unter [Microsoft Cloud Security for Enterprise Architects](https://aka.ms/cloudarchsecurity) und [Azure Network Security](https://azure.microsoft.com/blog/azure-network-security/).</span><span class="sxs-lookup"><span data-stu-id="e0c8f-259">For more information, see [Microsoft Cloud Security for Enterprise Architects](https://aka.ms/cloudarchsecurity) and [Azure Network Security](https://azure.microsoft.com/blog/azure-network-security/).</span></span>
  
### <a name="step-10-for-multiple-vnets-determine-the-vnet-to-vnet-connection-topology"></a><span data-ttu-id="e0c8f-260">Schritt 10 Bestimmen Sie für mehrere VNets die Verbinungstopologie von VNet zu VNet.</span><span class="sxs-lookup"><span data-stu-id="e0c8f-260">Step 10: For multiple VNets, determine the VNet-to-VNet connection topology.</span></span>

<span data-ttu-id="e0c8f-261">VNets können mit ähnlichen Topologien verbunden werden, die auch zum Verbinden von Standorten einer Organisation verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="e0c8f-261">VNets can be connected to each other using topologies similar to those used for connecting the sites of an organization.</span></span>
  
<span data-ttu-id="e0c8f-262">Durch eine Verkettungskonfiguration (Daisychain) werden die VNets in einer Reihe verbunden.</span><span class="sxs-lookup"><span data-stu-id="e0c8f-262">A daisy chain configuration connects the VNets in a series.</span></span>
  
<span data-ttu-id="e0c8f-263">**Abbildung 8: Eine Verkettungskonfiguration für VNets**</span><span class="sxs-lookup"><span data-stu-id="e0c8f-263">**Figure 8: A daisy-chained configuration for VNets**</span></span>

![Abbildung 8: eine kaskadierte Konfiguration für virtuelle Azure-Netzwerke](media/264d5dd4-06c5-483f-9428-a18cc1f68ac1.png)
  
<span data-ttu-id="e0c8f-265">Abbildung 8 zeigt fünf VNets, die in einer Reihe mit einer kaskadierten Konfiguration verbunden sind.</span><span class="sxs-lookup"><span data-stu-id="e0c8f-265">Figure 8 shows five VNets connected in series using a daisy-chained configuration.</span></span>
  
<span data-ttu-id="e0c8f-266">Bei einer Hub-Spoke-Konfiguration werden mehrere VNets mit eine Reihe von zentralen VNets verbunden, die ihrerseits miteinander verbunden sind.</span><span class="sxs-lookup"><span data-stu-id="e0c8f-266">A spoke and hub configuration connects multiple VNets to a set of central VNets, which are themselves connected to each other.</span></span>
  
<span data-ttu-id="e0c8f-267">**Abbildung 9: Eine Hub-Spoke-Konfiguration für VNets**</span><span class="sxs-lookup"><span data-stu-id="e0c8f-267">**Figure 9: A spoke and hub configuration for VNets**</span></span>

![Abbildung 9: eine Spoke-und Hub-Konfiguration für virtuelle Azure-Netzwerke](media/dd442a38-5b76-4ac5-b743-8fc7711a91ba.png)
  
<span data-ttu-id="e0c8f-269">Abbildung 9 zeigt sechs VNets, wobei zwei VNets „Hubs“ sind, die miteinander sowie mit anderen „Spoke“-VNets verbunden sind.</span><span class="sxs-lookup"><span data-stu-id="e0c8f-269">Figure 9 shows six VNets, two VNets are hubs that are connected to each other and also two other spoke VNets.</span></span>
  
<span data-ttu-id="e0c8f-270">Bei einer Full-Mesh-Konfiguration ist jedes VNet mit jedem anderen verbunden.</span><span class="sxs-lookup"><span data-stu-id="e0c8f-270">A full mesh configuration connects every VNet to each other.</span></span>
  
<span data-ttu-id="e0c8f-271">**Abbildung 10: Eine Full-Mesh-Konfiguration für VNets**</span><span class="sxs-lookup"><span data-stu-id="e0c8f-271">**Figure 10: A full mesh configuration for VNets**</span></span>

![Abbildung 10: eine Netzkonfiguration für virtuelle Azure-Netzwerke](media/9dda0738-10db-4a63-95b3-79851a399b71.png)
  
<span data-ttu-id="e0c8f-273">Abbildung 10 zeigt vier VNets, die alle miteinander verbunden sind, wobei insgesamt sechs VNet-zu-VNet-Verbindungen vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="e0c8f-273">Figure 10 shows four VNets that are all connected to each other, using a total of six VNet-to-VNet connections.</span></span>
  
## <a name="planning-steps-for-a-cross-premises-vnet"></a><span data-ttu-id="e0c8f-274">Planungsschritte für ein standortübergreifendes VNet</span><span class="sxs-lookup"><span data-stu-id="e0c8f-274">Planning steps for a cross-premises VNet</span></span>
<span data-ttu-id="e0c8f-275"><a name="cross_prem"> </a></span><span class="sxs-lookup"><span data-stu-id="e0c8f-275"></span></span>

<span data-ttu-id="e0c8f-276">Führen Sie die folgende Schritte durch, um ein stadortübergreifendes VNet zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="e0c8f-276">Follow these steps for a cross-premises VNet.</span></span>
  
> [!TIP]
> <span data-ttu-id="e0c8f-277">Wie Sie eine simulierte standortübergreifende Entwicklungs-/Testumgebung einrichten, können Sie unter [Simulated cross-premises virtual network in Azure](simulated-cross-premises-virtual-network-in-azure.md) nachlesen.</span><span class="sxs-lookup"><span data-stu-id="e0c8f-277">To create a simulated cross-premises dev/test environment, see [Simulated cross-premises virtual network in Azure](simulated-cross-premises-virtual-network-in-azure.md).</span></span> 
  
### <a name="step-1-determine-the-cross-premises-connection-to-the-vnet-s2s-vpn-or-expressroute"></a><span data-ttu-id="e0c8f-278">Schritt 1: Ermitteln Sie die standortübergreifende Verbindung zum VNet (S2S-VPN oder ExpressRoute).</span><span class="sxs-lookup"><span data-stu-id="e0c8f-278">Step 1: Determine the cross-premises connection to the VNet (S2S VPN or ExpressRoute).</span></span>

<span data-ttu-id="e0c8f-279">In Tabelle 6 sind die verschiedenen Verbindungstypen aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="e0c8f-279">Table 6 lists the different types of connections.</span></span>
  
|<span data-ttu-id="e0c8f-280">**Verbindungstyp**</span><span class="sxs-lookup"><span data-stu-id="e0c8f-280">**Type of connection**</span></span>|<span data-ttu-id="e0c8f-281">**Zweck**</span><span class="sxs-lookup"><span data-stu-id="e0c8f-281">**Purpose**</span></span>|
|:-----|:-----|
|<span data-ttu-id="e0c8f-282">Standort-zu-Standort-VPN (S2S)</span><span class="sxs-lookup"><span data-stu-id="e0c8f-282">Site-to-Site (S2S) VPN</span></span>  <br/> |<span data-ttu-id="e0c8f-283">Verbinden Sie 1-10-Websites (einschließlich anderer VNets) mit einem einzelnen VNet.</span><span class="sxs-lookup"><span data-stu-id="e0c8f-283">Connect 1-10 sites (including other VNets) to a single VNet.</span></span>  <br/> |
|<span data-ttu-id="e0c8f-284">ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="e0c8f-284">ExpressRoute</span></span>  <br/> |<span data-ttu-id="e0c8f-285">Eine private, sichere Verbindung mit Azure über einen Internet-Exchange-Anbieter (IXP) oder ein Netzwerkdienstanbieter (NSP).</span><span class="sxs-lookup"><span data-stu-id="e0c8f-285">A private, secure link to Azure via an Internet Exchange Provider (IXP) or a Network Service Provider (NSP).</span></span>  <br/> |
|<span data-ttu-id="e0c8f-286">Punkt-zu-Standort-VPN (P2S)</span><span class="sxs-lookup"><span data-stu-id="e0c8f-286">Point-to-Site (P2S) VPN</span></span>  <br/> |<span data-ttu-id="e0c8f-287">Verbindet einen einzelnen Computer mit einem VNet</span><span class="sxs-lookup"><span data-stu-id="e0c8f-287">Connects a single computer to a VNet.</span></span>  <br/> |
|<span data-ttu-id="e0c8f-288">VNet-Peering oder VNet-zu-VNet-VPN (V2V) </span><span class="sxs-lookup"><span data-stu-id="e0c8f-288">VNet peering or VNet-to-VNet (V2V) VPN</span></span>  <br/> |<span data-ttu-id="e0c8f-289">Verbindet ein VNet mit einem anderen VNet</span><span class="sxs-lookup"><span data-stu-id="e0c8f-289">Connects a VNet to another VNet.</span></span>  <br/> |
   
 <span data-ttu-id="e0c8f-290">**Tabelle 6: Die Verbindungstypen für standortübergreifende VNets**</span><span class="sxs-lookup"><span data-stu-id="e0c8f-290">**Table 6: The types of connections for cross-premises VNets**</span></span>
  
<span data-ttu-id="e0c8f-291">Weitere Informationen zur maximalen Anzahl von Verbindungen finden Sie unter [Networking Limits](https://docs.microsoft.com/azure/azure-subscription-service-limits#networking-limits).</span><span class="sxs-lookup"><span data-stu-id="e0c8f-291">For more information on the maximum number of connections, see [Networking Limits](https://docs.microsoft.com/azure/azure-subscription-service-limits#networking-limits).</span></span>
  
<span data-ttu-id="e0c8f-292">Weitere Informationen zu VPN-Geräten finden Sie unter [VPN Devices for Site-to-Site Virtual Network Connections](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpn-devices).</span><span class="sxs-lookup"><span data-stu-id="e0c8f-292">For more information about VPN devices, see [VPN devices for site-to-site virtual network connections](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpn-devices).</span></span>
  
<span data-ttu-id="e0c8f-293">Weitere Informationen zu VNet-Peering finden Sie unter [VNet Peering](https://docs.microsoft.com/azure/virtual-network/virtual-network-peering-overview).</span><span class="sxs-lookup"><span data-stu-id="e0c8f-293">For more information about VNet peering, see [VNet peering](https://docs.microsoft.com/azure/virtual-network/virtual-network-peering-overview).</span></span>
  
<span data-ttu-id="e0c8f-294">**Abbildung 11: Die vier Verbindungsarten mit einem standortübergreifenden VNet**</span><span class="sxs-lookup"><span data-stu-id="e0c8f-294">**Figure 11: The four ways to connect to a cross-premises VNet**</span></span>

![Abbildung 11: die drei Möglichkeiten zum Herstellen einer Verbindung mit einem standortübergreifenden virtuellen Azure-Netzwerk](media/d5d4a625-cfbd-4a77-9159-eaca69d07e93.png)
  
<span data-ttu-id="e0c8f-296">Abbildung 11 zeigt eine VNet mit den vier Verbindungstypen: eine P2S-Verbindung von einem Computer, eine S2S-VPN-Verbindung von einem lokalen Netzwerk, eine Express Route-Verbindung von einem lokalen Netzwerk und eine VNet-zu-VNet-Verbindung von einem anderen VNet.</span><span class="sxs-lookup"><span data-stu-id="e0c8f-296">Figure 11 shows a VNet with the four types of connections: a P2S connection from a computer, an S2S VPN connection from an on-premises network, an ExpressRoute connection from an on-premises network, and a VNet-to-VNet connection from another VNet.</span></span> 
  
<span data-ttu-id="e0c8f-297">Sie können eine Verbindung mit VMs in einem VNet wie folgt herstellen:</span><span class="sxs-lookup"><span data-stu-id="e0c8f-297">You can connect to VMs in a VNet in the following ways:</span></span>
  
- <span data-ttu-id="e0c8f-298">Verwaltung von VNet-VMs über das lokale Netzwerk oder das Internet</span><span class="sxs-lookup"><span data-stu-id="e0c8f-298">Administration of VNet VMs from your on-premises network or the Internet</span></span>
    
- <span data-ttu-id="e0c8f-299">IT-Workloadzugriff vom lokalen Netzwerk</span><span class="sxs-lookup"><span data-stu-id="e0c8f-299">IT workload access from your on-premises network</span></span>
    
- <span data-ttu-id="e0c8f-300">Erweiterung des Netzwerks durch zusätzliche VNets</span><span class="sxs-lookup"><span data-stu-id="e0c8f-300">Extension of your network through additional VNets</span></span>
    
<span data-ttu-id="e0c8f-301">Die Sicherheit der Verbindungen wird durch Folgendes sichergestellt:</span><span class="sxs-lookup"><span data-stu-id="e0c8f-301">Security for connections is provided by the following:</span></span>
  
- <span data-ttu-id="e0c8f-302">P2S verwendet SSTP (Secure Socket Tunnel Protocol). </span><span class="sxs-lookup"><span data-stu-id="e0c8f-302">P2S uses the Secure Socket Tunneling Protocol (SSTP)</span></span> 
    
- <span data-ttu-id="e0c8f-303">S2S und VNet-zu-VNet-VPN-Verbindungen verwenden den IPsec-Tunnelmodus mit AES256.</span><span class="sxs-lookup"><span data-stu-id="e0c8f-303">S2S and VNet-to-VNet VPN connections use IPsec tunnel mode with AES256</span></span>
    
- <span data-ttu-id="e0c8f-304">ExpressRoute ist eine private WAN-Verbindung.</span><span class="sxs-lookup"><span data-stu-id="e0c8f-304">ExpressRoute is a private WAN connection</span></span>
    
<span data-ttu-id="e0c8f-305">Weitere Informationen finden Sie unter [Microsoft Cloud Security for Enterprise Architects](https://aka.ms/cloudarchsecurity) und [Azure Network Security](https://azure.microsoft.com/blog/azure-network-security/).</span><span class="sxs-lookup"><span data-stu-id="e0c8f-305">For more information, see [Microsoft Cloud Security for Enterprise Architects](https://aka.ms/cloudarchsecurity) and [Azure Network Security](https://azure.microsoft.com/blog/azure-network-security/).</span></span>
  
### <a name="step-2-determine-the-on-premises-vpn-device-or-router"></a><span data-ttu-id="e0c8f-306">Schritt 2: Ermitteln Sie das lokale VPN-Gerät oder den Router.</span><span class="sxs-lookup"><span data-stu-id="e0c8f-306">Step 2: Determine the on-premises VPN device or router.</span></span>

<span data-ttu-id="e0c8f-307">Ihr lokales VPN-Gerät oder der Router fungiert als:</span><span class="sxs-lookup"><span data-stu-id="e0c8f-307">Your on-premises VPN device or router acts as:</span></span>
  
- <span data-ttu-id="e0c8f-308">ein IPSec-Peer, der die S2S-VPN-Verbindung von einem Azure-Gateway trennt.</span><span class="sxs-lookup"><span data-stu-id="e0c8f-308">An IPsec peer, terminating the S2S VPN connection from the Azure gateway.</span></span>
    
- <span data-ttu-id="e0c8f-309">der BPG-Peer und Abschlusspunkt für die private ExpressRoute-Peeringverbindung.</span><span class="sxs-lookup"><span data-stu-id="e0c8f-309">The BPG peer and termination point for the private peering ExpressRoute connection.</span></span>
    
<span data-ttu-id="e0c8f-310">**Abbildung 12: Lokaler VPN-Router oder lokales Gerät**</span><span class="sxs-lookup"><span data-stu-id="e0c8f-310">**Figure 12: The on-premises VPN router or device**</span></span>

![Abbildung 12: Lokaler VPN-Router oder lokales Gerät](media/bd221468-a660-4730-aa55-0426986480b9.png)
  
<span data-ttu-id="e0c8f-312">Abbildung 12 zeigt eine standortübergreifendes VNet, das mit einem lokalen VPN-Router oder einem Gerät verbunden ist.</span><span class="sxs-lookup"><span data-stu-id="e0c8f-312">Figure 12 shows a cross-premises VNet connected to an on-premises VPN router or device.</span></span>
  
<span data-ttu-id="e0c8f-313">Weitere Informationen finden Sie unter [Informationen zum VPN-Gateway](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpngateways).</span><span class="sxs-lookup"><span data-stu-id="e0c8f-313">For more information, see [About VPN gateway](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpngateways).</span></span>
  
### <a name="step-3-add-routes-to-your-intranet-to-make-the-address-space-of-the-vnet-reachable"></a><span data-ttu-id="e0c8f-314">Schritt 3: Hinzufügen von Routen zu Ihrem Intranet, um den Adressraum des VNet erreichbar zu machen.</span><span class="sxs-lookup"><span data-stu-id="e0c8f-314">Step 3: Add routes to your intranet to make the address space of the VNet reachable.</span></span>

<span data-ttu-id="e0c8f-315">Die Weiterleitung an VNets von lokal umfasst Folgendes:</span><span class="sxs-lookup"><span data-stu-id="e0c8f-315">Routing to VNets from on-premises consists of the following:</span></span>
  
1. <span data-ttu-id="e0c8f-316">Eine Route für den VNet-Adressraum, die auf Ihr VPN-Gerät verweist.</span><span class="sxs-lookup"><span data-stu-id="e0c8f-316">A route for the VNet address space that points toward your VPN device.</span></span>
    
2. <span data-ttu-id="e0c8f-317">Eine Route für den VNet-Adressraum auf Ihrem VPN-Gerät, die über die S2S-VPN- oder ExpressRoute-Verbindung hinweg verweist.</span><span class="sxs-lookup"><span data-stu-id="e0c8f-317">A route for the VNet address space on your VPN device that points across the S2S VPN or ExpressRoute connection</span></span>
    
<span data-ttu-id="e0c8f-318">**Abbildung 13: Ein VNet muss durch lokale Routen erreichbar gemacht werden**</span><span class="sxs-lookup"><span data-stu-id="e0c8f-318">**Figure 13: The on-premises routes needed to make a VNet reachable**</span></span>

![Abbildung 13: die lokalen Routen, die erforderlich sind, um eine Azure-VNet erreichbar zu machen](media/7a1e20c1-fbc4-4cb9-9961-735da4e23307.png)
  
<span data-ttu-id="e0c8f-320">Abbildung 13 zeigt die Routinginformationen, die von den lokalen Routern benötigt werden, sowie den VPN-Router oder das Gerät, das den Adressraum das VNets darstellt.</span><span class="sxs-lookup"><span data-stu-id="e0c8f-320">Figure 13 shows the routing information needed by the on-premises routers and the VPN router or device that represents the address space of the VNet.</span></span>
  
### <a name="step-4-for-expressroute-plan-for-the-new-connection-with-your-provider"></a><span data-ttu-id="e0c8f-321">Schritt 4: Planen Sie bei Verwendung von ExpressRoute die neue Verbindung mit Ihrem Anbieter.</span><span class="sxs-lookup"><span data-stu-id="e0c8f-321">Step 4: For ExpressRoute, plan for the new connection with your provider.</span></span>

<span data-ttu-id="e0c8f-322">Sie haben drei verschiedene Möglichkeiten, um eine ExpressRoute-Verbindung mit privatem Peering zwischen Ihrem lokalen Netzwerk und der Microsoft-Cloud herzustellen:</span><span class="sxs-lookup"><span data-stu-id="e0c8f-322">You can create an ExpressRoute connection with private peering between your on-premises network and the Microsoft cloud in three different ways:</span></span>
  
- <span data-ttu-id="e0c8f-323">Co-Location bei einem Cloud Exchange</span><span class="sxs-lookup"><span data-stu-id="e0c8f-323">Co-located at a cloud exchange</span></span>
    
- <span data-ttu-id="e0c8f-324">Punkt-zu-Punkt-Ethernet-Verbindungen</span><span class="sxs-lookup"><span data-stu-id="e0c8f-324">Point-to-point Ethernet connections</span></span>
    
- <span data-ttu-id="e0c8f-325">Viele-zu-viele-Netzwerke (IP-VPN)</span><span class="sxs-lookup"><span data-stu-id="e0c8f-325">Any-to-any (IP VPN) networks</span></span>
    
<span data-ttu-id="e0c8f-326">**Abbildung 14: Verwenden von ExpressRoute für Verbindungen zu einem standortübergreifenden VNet**</span><span class="sxs-lookup"><span data-stu-id="e0c8f-326">**Figure 14: Using ExpressRoute to connect to a cross-premises VNet**</span></span>

![Abbildung 14: Verwenden von Express Route zum Herstellen einer Verbindung mit einem standortübergreifenden virtuellen Azure-Netzwerk](media/7030bd39-69a6-4283-8567-3434e1ab6ba6.png)
  
<span data-ttu-id="e0c8f-328">Abbildung 14 zeigt ein standortübergreifendes VNet und eine ExpressRoute-Verbindung von einem lokalen Router zu Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="e0c8f-328">Figure 14 shows a cross-premises VNet and an ExpressRoute connection from an on-premises router to Microsoft Azure.</span></span>
  
<span data-ttu-id="e0c8f-329">Weitere Informationen finden Sie unter [ExpressRoute für Microsoft-Cloudkonnektivität](expressroute-for-microsoft-cloud-connectivity.md).</span><span class="sxs-lookup"><span data-stu-id="e0c8f-329">For more information, see [ExpressRoute for Microsoft cloud connectivity](expressroute-for-microsoft-cloud-connectivity.md).</span></span>
  
### <a name="step-5-determine-the-local-network-address-space-for-the-azure-gateway"></a><span data-ttu-id="e0c8f-330">Schritt 5: Bestimmen Sie den lokalen Netzwerkadressraum für das Azure-Gateway.</span><span class="sxs-lookup"><span data-stu-id="e0c8f-330">Step 5: Determine the Local Network address space for the Azure gateway.</span></span>

<span data-ttu-id="e0c8f-331">Beim Routing zu lokalen oder anderen VNets von einem VNet leitet Azure den Datenverkehr über einen Azure-Gateway, der mit dem lokalen Netzwerkadressraum übereinstimmt, der dem Gateway zugeordnet ist.</span><span class="sxs-lookup"><span data-stu-id="e0c8f-331">For the routing to on-premises or other VNets from a VNet, Azure forwards traffic across an Azure gateway that matches the Local Network address space assigned to the gateway.</span></span>
  
<span data-ttu-id="e0c8f-332">**Abbildung 15: Adressraum des lokalen Netzwerks für ein standortübergreifendes VNet**</span><span class="sxs-lookup"><span data-stu-id="e0c8f-332">**Figure 15: The Local Network address space for a cross-premises VNet**</span></span>

![Abbildung 15: der lokale Netzwerk Adressraum für ein standortübergreifendes virtuelles Azure-Netzwerk](media/e3af2652-8b8e-4551-9a0b-b550e6e7e3c0.png)
  
<span data-ttu-id="e0c8f-334">Abbildung 15 zeigt eine standortübergreifendes VNet und den Adressraum des lokalen Netzwerks auf dem Azure-Gateway, der den erreichbaren Adressraum im lokalen Netzwerk darstellt. </span><span class="sxs-lookup"><span data-stu-id="e0c8f-334">Figure 15 shows a cross-premises VNet and the Local Network address space on the Azure gateway, which represents the reachable address space on the on-premises network.</span></span> 
  
<span data-ttu-id="e0c8f-335">Sie können den Adressraum des lokalen Netzwerks auf folgende Weise definieren:</span><span class="sxs-lookup"><span data-stu-id="e0c8f-335">You can define the Local Network address space in these ways:</span></span>
  
- <span data-ttu-id="e0c8f-336">Option 1: Die Liste der Präfixe für den gerade benötigten oder verwendeten Adressraum (Aktualisierungen können erforderlich sein, wenn Sie neue Subnetzen hinzufügen).</span><span class="sxs-lookup"><span data-stu-id="e0c8f-336">Option 1: The list of prefixes for the address space currently needed or in use (updates might be needed when you add new subnets).</span></span>
    
- <span data-ttu-id="e0c8f-337">Option 2: Der gesamte lokale Adressraum (Aktualisierungen sind nur nötig, wenn Sie einen neuen Adressraum hinzufügen).</span><span class="sxs-lookup"><span data-stu-id="e0c8f-337">Option 2: Your entire on-premises address space (updates only needed when you add new address space).</span></span>
    
<span data-ttu-id="e0c8f-338">Da das Azure-Gateway keine zusammengefassten Routen zulässt, müssen Sie den Adressraum des lokalen Netzwerk bei der Option 2 so definieren, dass er nicht den VNet-Adressraum enthält.</span><span class="sxs-lookup"><span data-stu-id="e0c8f-338">Because the Azure gateway does not allow summarized routes, you must define the Local Network address space for option 2 so that it does not include the VNet address space.</span></span>
  
<span data-ttu-id="e0c8f-339">**Abbildung 16: Die durch den VNet-Adressraum erzeugte Lücke im Adressraum**</span><span class="sxs-lookup"><span data-stu-id="e0c8f-339">**Figure 16: The address space hole created by the VNet address space**</span></span>

![Abbildung 16: die vom Adressraum des virtuellen Netzwerks erstellte Adressraum Bohrung](media/e79c4840-f9e3-4741-9b72-59db6043aefa.png)
  
<span data-ttu-id="e0c8f-341">Abbildung 16 zeigt eine Darstellung eines Adressraums mit dem Stammraum und dem VNet-Adressraum.</span><span class="sxs-lookup"><span data-stu-id="e0c8f-341">Figure 16 shows a representation of an address space, with the root space and the VNet address space.</span></span>
  
<span data-ttu-id="e0c8f-342">Nachfolgend finden Sie ein Beispiel für das Definieren der Präfixe für den Adressraum des lokalen Netzwerks um den Adressraum "Hole", der vom VNet erstellt wurde:</span><span class="sxs-lookup"><span data-stu-id="e0c8f-342">Here is an example of defining the prefixes for the Local Network address space around the address space "hole" created by the VNet:</span></span>
  
- <span data-ttu-id="e0c8f-p114">Eine Organisation verwendet Teile des privaten Adressraums (10.0.0.0/8, 172.16.0.0/12 und 192.168.0.0/16) in ihrem lokalen Netzwerk. Die Organisation verwendet Option 2 und 10.100.100.0/24 als ihren VNet-Adressraum.</span><span class="sxs-lookup"><span data-stu-id="e0c8f-p114">An organization uses portions of the private address space (10.0.0.0/8, 172.16.0.0/12, and 192.168.0.0/16) across their on-premises network. They chose option 2 and 10.100.100.0/24 as their VNet address space.</span></span>
    
<span data-ttu-id="e0c8f-345">In Tabelle 7 sind die Schritte und die resultierenden Präfixe aufgeführt, die den Adressraum des lokalen Netzwerks in diesem Beispiel definieren.</span><span class="sxs-lookup"><span data-stu-id="e0c8f-345">Table 7 shows the steps and resulting prefixes that define the Local Network address space for this example.</span></span>
  
|<span data-ttu-id="e0c8f-346">**Schritt**</span><span class="sxs-lookup"><span data-stu-id="e0c8f-346">**Step**</span></span>|<span data-ttu-id="e0c8f-347">**Ergebnisse**</span><span class="sxs-lookup"><span data-stu-id="e0c8f-347">**Results**</span></span>|
|:-----|:-----|
|<span data-ttu-id="e0c8f-348">1. Auflisten der Präfixe, die nicht der Stammraum für den VNet-Adressraum sind.</span><span class="sxs-lookup"><span data-stu-id="e0c8f-348">1. List the prefixes that are not the root space for the VNet address space.</span></span>  <br/> |<span data-ttu-id="e0c8f-349">172.16.0.0/12 und 192.168.0.0/16</span><span class="sxs-lookup"><span data-stu-id="e0c8f-349">172.16.0.0/12 and 192.168.0.0/16</span></span>  <br/> |
|<span data-ttu-id="e0c8f-350">2. Auflisten der nicht überlappenden Präfixe für Variable Oktette bis einschließlich des zuletzt verwendeten Oktetts im VNet-Adressraum.</span><span class="sxs-lookup"><span data-stu-id="e0c8f-350">2. List the non-overlapping prefixes for variable octets up to but not including the last used octet in the VNet address space.</span></span>  <br/> |<span data-ttu-id="e0c8f-351">10.0.0.0/16, 10.1.0.0/16... 10.99.0.0/16, 10.101.0.0/16... 10.254.0.0/16, 10.255.0.0/16 (255 Präfixe, Überspringen von 10.100.0.0/16)</span><span class="sxs-lookup"><span data-stu-id="e0c8f-351">10.0.0.0/16, 10.1.0.0/16…10.99.0.0/16, 10.101.0.0/16…10.254.0.0/16, 10.255.0.0/16 (255 prefixes, skipping 10.100.0.0/16)</span></span>  <br/> |
|<span data-ttu-id="e0c8f-352">3. Listen Sie die nicht überlappenden Präfixe innerhalb des zuletzt verwendeten Oktetts des VNet-Adressraums auf.</span><span class="sxs-lookup"><span data-stu-id="e0c8f-352">3. List the non-overlapping prefixes within the last used octet of the VNet address space.</span></span>  <br/> |<span data-ttu-id="e0c8f-353">10.100.0.0/24, 10.100.1.0/24... 10.100.99.0/24, 10.100.101.0/24... 10.100.254.0/24, 10.100.0.255.0/24 (255 Präfixe, Überspringen von 10.100.100.0/24)</span><span class="sxs-lookup"><span data-stu-id="e0c8f-353">10.100.0.0/24, 10.100.1.0/24…10.100.99.0/24, 10.100.101.0/24…10.100.254.0/24, 10.100.0.255.0/24 (255 prefixes, skipping 10.100.100.0/24)</span></span>  <br/> |
   
 <span data-ttu-id="e0c8f-354">**Tabelle 7: Beispiel für den Adressraum des lokalen Netzwerks**</span><span class="sxs-lookup"><span data-stu-id="e0c8f-354">**Table 7: Example Local Address network space**</span></span>
  
### <a name="step-6-configure-on-premises-dns-servers-for-dns-replication-with-dns-servers-hosted-in-azure"></a><span data-ttu-id="e0c8f-355">Schritt 6: Konfigurieren Sie lokale DNS-Server für die DNS-Replikation mit DNS-Servern, die in Azure gehostet werden.</span><span class="sxs-lookup"><span data-stu-id="e0c8f-355">Step 6: Configure on-premises DNS servers for DNS replication with DNS servers hosted in Azure.</span></span>

<span data-ttu-id="e0c8f-356">Um sicherzustellen, dass lokale Computer die Namen von Servern in Azure und die Server in Azure die Namen von lokalen Computern auflösen können, müssen Sie Folgendes konfigurieren:</span><span class="sxs-lookup"><span data-stu-id="e0c8f-356">To ensure that on-premises computers can resolve the names of Azure-based servers and Azure-based servers can resolve the names of on-premises computers, configure:</span></span>
  
- <span data-ttu-id="e0c8f-357">Die DNS-Server in Ihrem VNet leiten an lokale DNS-Server weiter</span><span class="sxs-lookup"><span data-stu-id="e0c8f-357">The DNS servers in your VNet to forward to on-premises DNS servers</span></span>
    
- <span data-ttu-id="e0c8f-358">DNS-Replikation der entsprechenden Zonen zwischen lokalen DNS-Servern und im VNet</span><span class="sxs-lookup"><span data-stu-id="e0c8f-358">DNS replication of the appropriate zones between DNS servers on-premises and in the VNet</span></span>
    
<span data-ttu-id="e0c8f-359">**Abbildung 17: DNS-Replikation und -Weiterleitung für einen DNS-Server in einem standortübergreifenden VNet**</span><span class="sxs-lookup"><span data-stu-id="e0c8f-359">**Figure 17: DNS replication and forwarding for a DNS server in a cross-premises VNet**</span></span>

![Abbildung 17: DNS-Replikation und-Weiterleitung für einen DNS-Server in einem standortübergreifenden virtuellen Azure-Netzwerk](media/ab55e5ce-ccb0-49d4-a301-657a727f97b2.png)
  
<span data-ttu-id="e0c8f-p115">Abbildung 17 zeigt ein standortübergreifendes VNet mit DNS-Server im lokalen Netzwerk und in einem Subnetz im. DNS-Replikation und -Weiterleitung wurde zwischen den beiden DNS-Servern konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="e0c8f-p115">Figure 17 shows a cross-premises VNet with DNS servers in the on-premises network and on a subnet in the VNet. DNS replication and forwarding has been configured between the two DNS servers.</span></span>
  
### <a name="step-7-determine-the-use-of-forced-tunneling"></a><span data-ttu-id="e0c8f-363">Schritt 7: Ermitteln Sie die Nutzung von erzwungenem Tunneln.</span><span class="sxs-lookup"><span data-stu-id="e0c8f-363">Step 7: Determine the use of forced tunneling.</span></span>

<span data-ttu-id="e0c8f-364">Die standardmäßige System Route für Azure-Subnetze weist auf das Internet hin.</span><span class="sxs-lookup"><span data-stu-id="e0c8f-364">The default system route for Azure subnets points to the Internet.</span></span> <span data-ttu-id="e0c8f-365">Um sicherzustellen, dass der gesamte Datenverkehr von virtuellen Computern über die standortübergreifende Verbindung übertragen wird, erstellen Sie eine Routingtabelle mit der Standardroute, die das Azure-Gateway als Adresse des nächsten Hops verwendet.</span><span class="sxs-lookup"><span data-stu-id="e0c8f-365">To ensure that all traffic from virtual machines travels across the cross-premises connection, create a routing table with the default route that uses the Azure gateway as its next-hop address.</span></span> <span data-ttu-id="e0c8f-366">Anschließend ordnen Sie die Routentabelle dem Subnetz zu.</span><span class="sxs-lookup"><span data-stu-id="e0c8f-366">You then associate the route table with the subnet.</span></span> <span data-ttu-id="e0c8f-367">Dies wird auch als Tunnelerzwingung bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="e0c8f-367">This is known as forced tunneling.</span></span> <span data-ttu-id="e0c8f-368">Weitere Informationen finden Sie unter [configure Forced Tunneling](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-forced-tunneling-rm).</span><span class="sxs-lookup"><span data-stu-id="e0c8f-368">For more information, see [Configure forced tunneling](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-forced-tunneling-rm).</span></span>
  
<span data-ttu-id="e0c8f-369">**Abbildung 18: Benutzerdefinierte Routen und erzwungenes Tunneln für ein standortübergreifendes VNet**</span><span class="sxs-lookup"><span data-stu-id="e0c8f-369">**Figure 18: User-defined routes and forced tunneling for a cross-premises VNet**</span></span>

![Abbildung 18: benutzerdefinierte Routen und erzwungenes Tunneln für ein standortübergreifendes virtuelles Azure-Netzwerk](media/1e545ec6-c2d9-48d2-bb5e-e0a581fee004.png)
  
<span data-ttu-id="e0c8f-371">Abbildung 18 zeigt einen standortübergreifenden VNet mit einer benutzerdefinierten Route für ein Subnetz, das auf das Azure-Gateway verweist.</span><span class="sxs-lookup"><span data-stu-id="e0c8f-371">Figure 18 shows a cross-premises VNet with a user-defined route for a subnet pointing to the Azure gateway.</span></span>
  
## <a name="sharepoint-server-2016-farm-in-azure"></a><span data-ttu-id="e0c8f-372">SharePoint Server 2016-Farm in Azure</span><span class="sxs-lookup"><span data-stu-id="e0c8f-372">SharePoint Server 2016 farm in Azure</span></span>
<span data-ttu-id="e0c8f-373"><a name="cross_prem"> </a></span><span class="sxs-lookup"><span data-stu-id="e0c8f-373"></span></span>

<span data-ttu-id="e0c8f-374">Ein Beispiel für eine Intranet-IT-Arbeitslast, die in Azure IaaS gehostet wird, ist eine hoch verfügbare, mehrstufige SharePoint Server-2016-Farm.</span><span class="sxs-lookup"><span data-stu-id="e0c8f-374">An example of an intranet IT workload hosted in Azure IaaS is a highly-available, multi-tier SharePoint Server 2016 farm.</span></span>
  
<span data-ttu-id="e0c8f-375">**Abbildung 19: Hoch verfügbare SharePoint Server 2016-Intranetfarm in Azure IaaS**</span><span class="sxs-lookup"><span data-stu-id="e0c8f-375">**Figure 19: A highly-available intranet SharePoint Server 2016 farm in Azure IaaS**</span></span>

![Eine SharePoint Server 2016-Farm mit hoher Verfügbarkeit in Azure IaaS](media/3a922e21-df91-455f-ba90-78abdd48d98d.png)
  
<span data-ttu-id="e0c8f-377">Abbildung 19 zeigt die neun Server einer SharePoint Server 2016-Farm, die in einem standortübergreifenden VNet bereitgestellt wird und interne Lastenausgleichsmodule für die Front-End-und Datenebenen verwendet.</span><span class="sxs-lookup"><span data-stu-id="e0c8f-377">Figure 19 shows the nine servers of a SharePoint Server 2016 farm deployed in a cross-premises VNet that uses internal load balancers for the front-end and data tiers.</span></span> <span data-ttu-id="e0c8f-378">Weitere Informationen, einschließlich Schritt-für-Schritt-Anleitungen zum Entwerfen und bereitstellen, finden Sie unter [SharePoint Server 2016 in Microsoft Azure](https://docs.microsoft.com/SharePoint/administration/sharepoint-server-2016-in-microsoft-azure).</span><span class="sxs-lookup"><span data-stu-id="e0c8f-378">For more information, including step-by-step design and deployment instructions, see [SharePoint Server 2016 in Microsoft Azure](https://docs.microsoft.com/SharePoint/administration/sharepoint-server-2016-in-microsoft-azure).</span></span>
  
> [!TIP]
> <span data-ttu-id="e0c8f-379">Informationen zum Erstellen einer SharePoint Server 2016-Farm mit einem Server in einer simulierten standortübergreifenden VNet finden Sie unter [Intranet SharePoint Server 2016 in Azure dev/Test Environment](https://docs.microsoft.com/SharePoint/administration/intranet-sharepoint-server-2016-in-azure-dev-test-environment).</span><span class="sxs-lookup"><span data-stu-id="e0c8f-379">To create a single-server SharePoint Server 2016 farm in a simulated cross-premises VNet, see [Intranet SharePoint Server 2016 in Azure dev/test environment](https://docs.microsoft.com/SharePoint/administration/intranet-sharepoint-server-2016-in-azure-dev-test-environment).</span></span> 
  
<span data-ttu-id="e0c8f-380">Weitere Beispiele für IT-Arbeitslasten, die auf virtuellen Computern in einem standortübergreifenden virtuellen Azure-Netzwerk bereitgestellt werden, finden Sie unter [Hybrid Cloud Scenarios for Azure IaaS](https://docs.microsoft.com/office365/enterprise/hybrid-cloud-scenarios-for-azure-iaas).</span><span class="sxs-lookup"><span data-stu-id="e0c8f-380">For additional examples of IT workloads deployed on virtual machines in a cross-premises Azure virtual network, see [Hybrid cloud scenarios for Azure IaaS](https://docs.microsoft.com/office365/enterprise/hybrid-cloud-scenarios-for-azure-iaas).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="e0c8f-381">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="e0c8f-381">See also</span></span>

[<span data-ttu-id="e0c8f-382">Microsoft-Cloudnetzwerke für Enterprise-Architekten</span><span class="sxs-lookup"><span data-stu-id="e0c8f-382">Microsoft Cloud Networking for Enterprise Architects</span></span>](microsoft-cloud-networking-for-enterprise-architects.md)
  
[<span data-ttu-id="e0c8f-383">Ressourcen zur Cloud-IT-Architektur von Microsoft</span><span class="sxs-lookup"><span data-stu-id="e0c8f-383">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)


