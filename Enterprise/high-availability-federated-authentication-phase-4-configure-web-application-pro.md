---
title: Hoher Verfügbarkeit federated Authentifizierung Phase 4 Konfigurieren Web-Anwendungsproxys
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Solutions
ms.assetid: 1c903173-67cd-47da-86d9-d333972dda80
description: 'Zusammenfassung: Konfigurieren der Web Application Proxy-Server für die hohe Verfügbarkeit Verbundauthentifizierung für Office 365 in Microsoft Azure.'
ms.openlocfilehash: 0f0299fe8fecdea608330eebc12aea01098f8cec
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915810"
---
# <a name="high-availability-federated-authentication-phase-4-configure-web-application-proxies"></a><span data-ttu-id="1285a-103">Hochverfügbarkeit der Verbundauthentifizierung, Phase 4: Konfigurieren von Webanwendungsproxys</span><span class="sxs-lookup"><span data-stu-id="1285a-103">High availability federated authentication Phase 4: Configure web application proxies</span></span>

 <span data-ttu-id="1285a-104">**Zusammenfassung:** Konfigurieren Sie die Web Application Proxy-Server für die hohe Verfügbarkeit Verbundauthentifizierung für Office 365 in Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="1285a-104">**Summary:** Configure the web application proxy servers for your high availability federated authentication for Office 365 in Microsoft Azure.</span></span>
  
<span data-ttu-id="1285a-105">In dieser Phase der Bereitstellung der hohen Verfügbarkeit für Verbundauthentifzierung für Office 365 in Azure-Infrastrukturdiensten erstellen Sie einen internen Lastenausgleich und zwei AD FS-Server.</span><span class="sxs-lookup"><span data-stu-id="1285a-105">In this phase of deploying high availability for Office 365 federated authentication in Azure infrastructure services, you create an internal load balancer and two AD FS servers.</span></span>
  
<span data-ttu-id="1285a-p101">Müssen Sie vor dem Verschieben auf in dieser Phase [hoher Verfügbarkeit federated Authentifizierung Phase 5: Konfigurieren von Verbundauthentifizierung für Office 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md). Finden Sie unter [Deploy hohe Verfügbarkeit Verbundauthentifizierung für Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) für alle Phasen.</span><span class="sxs-lookup"><span data-stu-id="1285a-p101">You must complete this phase before moving on to [High availability federated authentication Phase 5: Configure federated authentication for Office 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md). See [Deploy high availability federated authentication for Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) for all of the phases.</span></span>
  
## <a name="create-the-internet-facing-load-balancer-in-azure"></a><span data-ttu-id="1285a-108">Erstellen des Lastenausgleichs mit Internetzugriff in Azure</span><span class="sxs-lookup"><span data-stu-id="1285a-108">Create the Internet-facing load balancer in Azure</span></span>

<span data-ttu-id="1285a-109">Sie müssen einen Lastenausgleich mit Internetzugriff erstellen, damit Azure den eingehenden Clientauthentifizierungsverkehr aus dem Internet gleichmäßig unter den beiden Webanwendungsproxy-Servern verteilt.</span><span class="sxs-lookup"><span data-stu-id="1285a-109">You must create an Internet-facing load balancer so that Azure distributes the incoming client authentication traffic from the Internet evenly among the two web application proxy servers.</span></span>
  
> [!NOTE]
> <span data-ttu-id="1285a-p102">In den folgenden Befehlssätzen wird die aktuelle Version von Azure PowerShell verwendet. Informationen dazu finden Sie unter [Erste Schritte mit Azure PowerShell-Cmdlets](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/).</span><span class="sxs-lookup"><span data-stu-id="1285a-p102">The following command sets use the latest version of Azure PowerShell. See [Get started with Azure PowerShell cmdlets](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/).</span></span> 
  
<span data-ttu-id="1285a-112">Sobald Sie die Werte für Speicherort und Ressourcengruppe korrekt festgelegt haben, führen Sie den resultierenden Block über die Azure PowerShell-Eingabeaufforderung oder in PowerShell ISE aus.</span><span class="sxs-lookup"><span data-stu-id="1285a-112">When you have supplied location and resource group values, run the resulting block at the Azure PowerShell command prompt or in the PowerShell ISE.</span></span>
  
> [!TIP]
> <span data-ttu-id="1285a-113">Eine Textdatei, die alle von PowerShell-Befehlen in diesem Artikel und Konfiguration Microsoft Excel-Arbeitsmappen, die generiert Ready-und-Los-PowerShell-Befehl Blöcke basierend auf Ihrer benutzerdefinierten Einstellungen enthält, finden Sie unter der [Federated-Authentifizierung für Office 365 in Azure Deployment Kit](https://gallery.technet.microsoft.com/Federated-Authentication-8a9f1664).</span><span class="sxs-lookup"><span data-stu-id="1285a-113">For a text file that contains all of the PowerShell commands in this article and a Microsoft Excel configuration workbook that generates ready-to-run PowerShell command blocks based on your custom settings, see the [Federated Authentication for Office 365 in Azure Deployment Kit](https://gallery.technet.microsoft.com/Federated-Authentication-8a9f1664).</span></span> 
  
```
# Set up key variables
$locName="<your Azure location>"
$rgName="<Table R - Item 4 - Resource group name column>"

$publicIP=New-AzureRmPublicIpAddress -ResourceGroupName $rgName -Name "WebProxyPublicIP" -Location $LocName -AllocationMethod "Static"
$frontendIP=New-AzureRmLoadBalancerFrontendIpConfig -Name "WebAppProxyServers-LBFE" -PublicIpAddress $publicIP
$beAddressPool=New-AzureRMLoadBalancerBackendAddressPoolConfig -Name "WebAppProxyServers-LBBE"
$healthProbe=New-AzureRMLoadBalancerProbeConfig -Name "WebServersProbe" -Protocol "TCP" -Port 443 -IntervalInSeconds 15 -ProbeCount 2
$lbrule=New-AzureRMLoadBalancerRuleConfig -Name "WebTraffic" -FrontendIpConfiguration $frontendIP -BackendAddressPool $beAddressPool -Probe $healthProbe -Protocol "TCP" -FrontendPort 443 -BackendPort 443
New-AzureRMLoadBalancer -ResourceGroupName $rgName -Name "WebAppProxyServers" -Location $locName -LoadBalancingRule $lbrule -BackendAddressPool $beAddressPool -Probe $healthProbe -FrontendIpConfiguration $frontendIP
```

<span data-ttu-id="1285a-114">Um die dem Lastenausgleich mit Internetzugriff zugewiesene öffentliche IP-Adresse anzuzeigen, führen Sie die folgenden Azure PowerShell-Eingabeaufforderung auf dem lokalen Computer aus:</span><span class="sxs-lookup"><span data-stu-id="1285a-114">To display the public IP address assigned to your Internet-facing load balancer, run these commands at the Azure PowerShell command prompt on your local computer:</span></span>
  
```
Write-Host (Get-AzureRMPublicIpaddress -Name "WebProxyPublicIP" -ResourceGroup $rgName).IPAddress
```

## <a name="determine-your-federation-service-fqdn-and-create-dns-records"></a><span data-ttu-id="1285a-115">Ermitteln des FQDN des Verbunddiensts und Erstellen von DNS-Einträgen</span><span class="sxs-lookup"><span data-stu-id="1285a-115">Determine your federation service FQDN and create DNS records</span></span>

<span data-ttu-id="1285a-p103">Sie müssen den DNS-Namen ermitteln, um den Namen des Verbunddiensts im Internet zu identifizieren. Azure AD Connect konfiguriert Office 365 in Phase 5 mit diesem Namen, der Teil der URL wird, die Office 365 an Clients sendet, die eine Verbindung herstellen, um ein Sicherheitstoken abzurufen. Ein Beispiel ist „fs.contoso.com“ („fs“ steht für den Verbunddienst).</span><span class="sxs-lookup"><span data-stu-id="1285a-p103">You need to determine the DNS name to identify your federation service name on the Internet. Azure AD Connect will configure Office 365 with this name in Phase 5, which will become part of the URL that Office 365 sends to connecting clients to get a security token. An example is fs.contoso.com (fs stands for federation service).</span></span>
  
<span data-ttu-id="1285a-119">Nachdem Sie den FQDN des Verbunddiensts ermittelt haben, erstellen Sie einen öffentlichen DNS-Eintrag für Domäne A für den FQDN des Verbunddiensts, der die öffentliche IP-Adresse des Azure-Lastenausgleichs mit Internetzugriff auflöst.</span><span class="sxs-lookup"><span data-stu-id="1285a-119">Once you have your federation service FDQN, create a public DNS domain A record for the federation service FDQN that resolves to the public IP address of the Azure Internet-facing load balancer.</span></span>
  
|<span data-ttu-id="1285a-120">**Name**</span><span class="sxs-lookup"><span data-stu-id="1285a-120">**Name**</span></span>|<span data-ttu-id="1285a-121">**Typ**</span><span class="sxs-lookup"><span data-stu-id="1285a-121">**Type**</span></span>|<span data-ttu-id="1285a-122">**TTL**</span><span class="sxs-lookup"><span data-stu-id="1285a-122">**TTL**</span></span>|<span data-ttu-id="1285a-123">**Wert**</span><span class="sxs-lookup"><span data-stu-id="1285a-123">**Value**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="1285a-124">FQDN des Verbunddiensts</span><span class="sxs-lookup"><span data-stu-id="1285a-124">federation service FDQN</span></span>  <br/> |<span data-ttu-id="1285a-125">A</span><span class="sxs-lookup"><span data-stu-id="1285a-125">A</span></span>  <br/> |<span data-ttu-id="1285a-126">3600</span><span class="sxs-lookup"><span data-stu-id="1285a-126">3600</span></span>  <br/> |<span data-ttu-id="1285a-127">Öffentliche IP-Adresse des Azure-Lastenausgleich mit Internetzugriff (angezeigt durch den **Write-Host**-Befehl im vorherigen Abschnitt)</span><span class="sxs-lookup"><span data-stu-id="1285a-127">public IP address of the Azure Internet-facing load balancer (displayed by the **Write-Host** command in the previous section)</span></span> <br/> |
   
<span data-ttu-id="1285a-128">Hier ein Beispiel:</span><span class="sxs-lookup"><span data-stu-id="1285a-128">Here is an example:</span></span>
  
|<span data-ttu-id="1285a-129">**Name**</span><span class="sxs-lookup"><span data-stu-id="1285a-129">**Name**</span></span>|<span data-ttu-id="1285a-130">**Typ**</span><span class="sxs-lookup"><span data-stu-id="1285a-130">**Type**</span></span>|<span data-ttu-id="1285a-131">**TTL**</span><span class="sxs-lookup"><span data-stu-id="1285a-131">**TTL**</span></span>|<span data-ttu-id="1285a-132">**Wert**</span><span class="sxs-lookup"><span data-stu-id="1285a-132">**Value**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="1285a-133">FS.contoso.com</span><span class="sxs-lookup"><span data-stu-id="1285a-133">fs.contoso.com</span></span>  <br/> |<span data-ttu-id="1285a-134">A</span><span class="sxs-lookup"><span data-stu-id="1285a-134">A</span></span>  <br/> |<span data-ttu-id="1285a-135">3600</span><span class="sxs-lookup"><span data-stu-id="1285a-135">3600</span></span>  <br/> |<span data-ttu-id="1285a-136">131.107.249.117</span><span class="sxs-lookup"><span data-stu-id="1285a-136">131.107.249.117</span></span>  <br/> |
   
<span data-ttu-id="1285a-137">Als Nächstes fügen Sie ein DNS-Adresseintrag zu dem privaten DNS-Namespace Ihrer Organisation hinzu, der den FQDN des Verbunddiensts in die private IP-Adresse auflöst, die dem internen Lastenausgleich für die AD FS-Server (Tabelle I, Element 4, Spalte „Wert“) zugewiesen ist.</span><span class="sxs-lookup"><span data-stu-id="1285a-137">Next, add a DNS address record to your organization's private DNS namespace that resolves your federation service FQDN to the private IP address assigned to the internal load balancer for the AD FS servers (Table I, item 4, Value column).</span></span>
  
## <a name="create-the-web-application-proxy-server-virtual-machines-in-azure"></a><span data-ttu-id="1285a-138">Erstellen der virtuellen Computer des Webanwendungsproxy-Servers in Azure</span><span class="sxs-lookup"><span data-stu-id="1285a-138">Create the web application proxy server virtual machines in Azure</span></span>

<span data-ttu-id="1285a-139">Verwenden Sie die folgenden Azure PowerShell-Befehle, um die virtuellen Computer für die beiden Webanwendungsproxy-Server zu erstellen. </span><span class="sxs-lookup"><span data-stu-id="1285a-139">Use the following block of Azure PowerShell commands to create the virtual machines for the two web application proxy servers.</span></span> 
  
<span data-ttu-id="1285a-140">Beachten Sie, dass die folgenden Azure PowerShell-Befehlssätze Werte aus den folgenden Tabellen verwenden:</span><span class="sxs-lookup"><span data-stu-id="1285a-140">Note that the following Azure PowerShell command sets use values from the following tables:</span></span>
  
- <span data-ttu-id="1285a-141">Tabelle M (für die virtuellen Computer)</span><span class="sxs-lookup"><span data-stu-id="1285a-141">Table M, for your virtual machines</span></span>
    
- <span data-ttu-id="1285a-142">Tabelle R (für die Ressourcengruppen)</span><span class="sxs-lookup"><span data-stu-id="1285a-142">Table R, for your resource groups</span></span>
    
- <span data-ttu-id="1285a-143">Tabelle V (für die Einstellungen des virtuellen Netzwerks)</span><span class="sxs-lookup"><span data-stu-id="1285a-143">Table V, for your virtual network settings</span></span>
    
- <span data-ttu-id="1285a-144">Tabelle S (für das Subnetz)</span><span class="sxs-lookup"><span data-stu-id="1285a-144">Table S, for your subnets</span></span>
    
- <span data-ttu-id="1285a-145">Tabelle I (für die statischen IP-Adressen)</span><span class="sxs-lookup"><span data-stu-id="1285a-145">Table I, for your static IP addresses</span></span>
    
- <span data-ttu-id="1285a-146">Tabelle A (für die Verfügbarkeitsgruppen)</span><span class="sxs-lookup"><span data-stu-id="1285a-146">Table A, for your availability sets</span></span>
    
<span data-ttu-id="1285a-147">Denken Sie daran, dass Sie die Tabelle M in definiert [hoher Verfügbarkeit federated Authentifizierung Phase 2: Konfigurieren von Domänencontrollern](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) und Tabellen R, V, S, ich und eine in [hoher Verfügbarkeit federated Authentifizierung Phase 1: Konfigurieren von Azure](high-availability-federated-authentication-phase-1-configure-azure.md).</span><span class="sxs-lookup"><span data-stu-id="1285a-147">Recall that you defined Table M in [High availability federated authentication Phase 2: Configure domain controllers](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) and Tables R, V, S, I, and A in [High availability federated authentication Phase 1: Configure Azure](high-availability-federated-authentication-phase-1-configure-azure.md).</span></span>
  
<span data-ttu-id="1285a-148">Sobald Sie alle Werte korrekt festgelegt haben, führen Sie den resultierenden Block über die Azure PowerShell-Eingabeaufforderung oder in PowerShell ISE aus.</span><span class="sxs-lookup"><span data-stu-id="1285a-148">When you have supplied all the proper values, run the resulting block at the Azure PowerShell command prompt or in the PowerShell ISE.</span></span>
  
```
# Set up variables common to both virtual machines
$locName="<your Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$subnetName="<Table R - Item 3 - Subnet name column>"
$avName="<Table A - Item 3 - Availability set name column>"
$rgNameTier="<Table R - Item 3 - Resource group name column>"
$rgNameInfra="<Table R - Item 4 - Resource group name column>"

$rgName=$rgNameInfra
$vnet=Get-AzureRMVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
$subnet=Get-AzureRmVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnetName
$backendSubnet=Get-AzureRMVirtualNetworkSubnetConfig -Name $subnetName -VirtualNetwork $vnet
$webLB=Get-AzureRMLoadBalancer -ResourceGroupName $rgName -Name "WebAppProxyServers"

$rgName=$rgNameTier
$avSet=Get-AzureRMAvailabilitySet -Name $avName -ResourceGroupName $rgName

# Create the first web application proxy server virtual machine
$vmName="<Table M - Item 6 - Virtual machine name column>"
$vmSize="<Table M - Item 6 - Minimum size column>"
$staticIP="<Table I - Item 7 - Value column>"
$diskStorageType="<Table M - Item 6 - Storage type column>"

$nic=New-AzureRMNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName -Subnet $backendSubnet -LoadBalancerBackendAddressPool $webLB.BackendAddressPools[0] -PrivateIpAddress $staticIP
$vm=New-AzureRMVMConfig -VMName $vmName -VMSize $vmSize -AvailabilitySetId $avset.Id

$cred=Get-Credential -Message "Type the name and password of the local administrator account for the first web application proxy server." 
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm

# Create the second web application proxy virtual machine
$vmName="<Table M - Item 7 - Virtual machine name column>"
$vmSize="<Table M - Item 7 - Minimum size column>"
$staticIP="<Table I - Item 8 - Value column>"
$diskStorageType="<Table M - Item 7 - Storage type column>"

$nic=New-AzureRMNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName  -Subnet $backendSubnet -LoadBalancerBackendAddressPool $webLB.BackendAddressPools[0] -PrivateIpAddress $staticIP
$vm=New-AzureRMVMConfig -VMName $vmName -VMSize $vmSize -AvailabilitySetId $avset.Id

$cred=Get-Credential -Message "Type the name and password of the local administrator account for the second web application proxy server." 
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

> [!NOTE]
> <span data-ttu-id="1285a-p104">Da diese virtuellen Computer für eine Intranetanwendung gedacht sind, wird ihnen weder eine öffentliche IP-Adresse noch eine DNS-Domänennamenbezeichnung zugewiesen. Sie sind also nicht über das Internet erreichbar. Das bedeutet allerdings, dass Sie auch nicht über das Azure-Portal auf sie zugreifen können. Wenn Sie die Eigenschaften eines der virtuellen Computer aufrufen, ist die Option **Verbinden** nicht verfügbar. Verwenden Sie eine Remotedesktopverbindung oder ein anderes Remotedesktoptool, um eine Verbindung über die private IP-Adresse des betreffenden virtuellen Computers oder seinen Intranet-DNS-Namen und die Anmeldedaten des lokalen Administratorkontos herzustellen.</span><span class="sxs-lookup"><span data-stu-id="1285a-p104">Because these virtual machines are for an intranet application, they are not assigned a public IP address or a DNS domain name label and exposed to the Internet. However, this also means that you cannot connect to them from the Azure portal. The **Connect** option is unavailable when you view the properties of the virtual machine. Use the Remote Desktop Connection accessory or another Remote Desktop tool to connect to the virtual machine using its private IP address or intranet DNS name and the credentials of the local administrator account.</span></span>
  
<span data-ttu-id="1285a-153">Wenn Sie diese Phase erfolgreich abgeschlossen haben, sieht Ihre Konfiguration wie folgt aus. Für die Computernamen werden hier Platzhalter verwendet.</span><span class="sxs-lookup"><span data-stu-id="1285a-153">Here is the configuration resulting from the successful completion of this phase, with placeholder computer names.</span></span>
  
<span data-ttu-id="1285a-154">**Phase 4: Der Lastenausgleich mit Internetzugriff und die Webanwendungsproxy-Server für Verbundauthentifizierungsinfrastruktur mit hoher Verfügbarkeit in Azure**</span><span class="sxs-lookup"><span data-stu-id="1285a-154">**Phase 4: The Internet-facing load balancer and web application proxy servers for your high availability federated authentication infrastructure in Azure**</span></span>

![Phase 4 der hochverfügbaren Office 365-Verbundauthentifizierungsinfrastruktur in Azure mit Proxyservern der Webanwendung](media/7e03183f-3b3b-4cbe-9028-89cc3f195a63.png)
  
## <a name="next-step"></a><span data-ttu-id="1285a-156">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="1285a-156">Next step</span></span>

<span data-ttu-id="1285a-157">Gehen Sie weiter zu [High availability federated authentication Phase 5: Configure federated authentication for Office 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md), um mit der Konfiguration dieser Arbeitslast fortzufahren.</span><span class="sxs-lookup"><span data-stu-id="1285a-157">Use [High availability federated authentication Phase 5: Configure federated authentication for Office 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md) to continue configuring this workload.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="1285a-158">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="1285a-158">See Also</span></span>

[<span data-ttu-id="1285a-159">Bereitstellen der Verbundauthentifizierung mit Hochverfügbarkeit für Office 365 in Azure</span><span class="sxs-lookup"><span data-stu-id="1285a-159">Deploy high availability federated authentication for Office 365 in Azure</span></span>](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)
  
[<span data-ttu-id="1285a-160">Verbundidentität für Ihre Office 365-Entwicklungs-/Testumgebung</span><span class="sxs-lookup"><span data-stu-id="1285a-160">Federated identity for your Office 365 dev/test environment</span></span>](federated-identity-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="1285a-161">Cloudakzeptanz und Hybridlösungen</span><span class="sxs-lookup"><span data-stu-id="1285a-161">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)

[<span data-ttu-id="1285a-162">Optionen für Verbundauthentifizierung</span><span class="sxs-lookup"><span data-stu-id="1285a-162">Federated authentication options</span></span>](about-office-365-identity.md#federated-authentication-options)


