---
title: Basiskonfiguration der Entwicklungs-/Testumgebung
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 03/15/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
ms.assetid: 6fcbb50c-ac68-4be7-9fc5-dd0f275c1e3d
description: 'Zusammenfassung: Erstellen Sie ein vereinfachtes Intranet als Entwicklungs-/Testumgebung in Microsoft Azure.'
ms.openlocfilehash: 3f6851ba9ed1220fc7a55fb440b687528c81c938
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2019
ms.locfileid: "38030479"
---
# <a name="base-configuration-devtest-environment"></a><span data-ttu-id="a9079-103">Basiskonfiguration der Entwicklungs-/Testumgebung</span><span class="sxs-lookup"><span data-stu-id="a9079-103">Base Configuration dev/test environment</span></span>

 <span data-ttu-id="a9079-104">**Zusammenfassung:** Erstellen Sie ein vereinfachtes Intranet als Entwicklungs-/Testumgebung in Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="a9079-104">**Summary:** Create a simplified intranet as a dev/test environment in Microsoft Azure.</span></span>
  
<span data-ttu-id="a9079-105">Dieser Artikel enthält eine Anleitung zum Erstellen der folgenden Basiskonfiguration der Entwicklungs-/Testumgebung in Azure:</span><span class="sxs-lookup"><span data-stu-id="a9079-105">This article provides you with instructions to create the following Base Configuration dev/test environment in Azure:</span></span>
  
![Die Basiskonfiguration in Azure](media/25a010a6-c870-4690-b8f3-84421f8bc5c7.png)
  
<span data-ttu-id="a9079-107">**Abbildung 1: Die Basiskonfiguration der Entwicklungs-/Testumgebung**</span><span class="sxs-lookup"><span data-stu-id="a9079-107">**Figure 1: The Base Configuration dev/test environment**</span></span>

<span data-ttu-id="a9079-p101">Die Basiskonfiguration der Entwicklungs-/Testumgebung in Abbildung 1 besteht aus dem Unternehmensnetzwerk-Subnetz in einem auf die Cloud beschränkten virtuellen Azure-Netzwerk namens TestLab, das ein vereinfachtes privates Intranet simuliert, das mit dem Internet verbunden ist. Es enthält drei virtuelle Azure-Computer unter Windows Server 2016:</span><span class="sxs-lookup"><span data-stu-id="a9079-p101">The Base Configuration dev/test environment in Figure 1 consists of the Corpnet subnet in a cloud-only Azure virtual network named TestLab that simulates a simplified, private intranet connected to the Internet. It has three Azure virtual machines running Windows Server 2016:</span></span>
  
- <span data-ttu-id="a9079-110">DC1 ist als Intranet-Domänencontroller und DNS-Server (Domain Name System) konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="a9079-110">DC1 is configured as an intranet domain controller and Domain Name System (DNS) server</span></span>
    
- <span data-ttu-id="a9079-111">App1 ist als allgemeiner Anwendungs- und Webserver konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="a9079-111">APP1 is configured as a general application and web server</span></span>
    
- <span data-ttu-id="a9079-112">CLIENT1 fungiert als Intranetclient.</span><span class="sxs-lookup"><span data-stu-id="a9079-112">CLIENT1 acts as an intranet client</span></span>
    
<span data-ttu-id="a9079-113">Diese Konfiguration ermöglicht DC1, APP1, CLIENT1 und weiteren Computern im Unternehmensnetzwerk-Subnetz Folgendes:</span><span class="sxs-lookup"><span data-stu-id="a9079-113">This configuration lets DC1, APP1, CLIENT1, and additional Corpnet subnet computers to be:</span></span> 
  
- <span data-ttu-id="a9079-114">Verbindung mit dem Internet zum Installieren von Updates, Zugriff auf Internetressourcen in Echtzeit und Teilnahme an öffentlichen Cloud-Technologien wie z. B. Microsoft Office 365 und anderen Azure-Diensten.</span><span class="sxs-lookup"><span data-stu-id="a9079-114">Connected to the Internet to install updates, access Internet resources in real time, and participate in public cloud technologies such as Microsoft Office 365 and other Azure services.</span></span>
    
- <span data-ttu-id="a9079-115">Remoteverwaltung über Remotedesktopverbindungen von Ihrem Computer, der mit dem Internet oder dem Netzwerk Ihrer Organisation verbunden ist.</span><span class="sxs-lookup"><span data-stu-id="a9079-115">Remotely managed using Remote Desktop connections from your computer that is connected to the Internet or your organization network.</span></span>
    
<span data-ttu-id="a9079-116">Sie können die resultierende Testumgebung zu folgenden Zwecken verwenden:</span><span class="sxs-lookup"><span data-stu-id="a9079-116">You can use the resulting test environment:</span></span>
  
- <span data-ttu-id="a9079-117">Zur Anwendungsentwicklung und zum Testen.</span><span class="sxs-lookup"><span data-stu-id="a9079-117">For application development and testing.</span></span>
    
- <span data-ttu-id="a9079-118">Als anfängliche Konfiguration einer erweiterten Testumgebung mit Ihrem eigenen Design, die zusätzliche virtuelle Computer, Azure-Dienste oder andere Cloud-Angebote von Microsoft enthält, z. B. Office 365 and Enterprise Mobility + Security (EMS).</span><span class="sxs-lookup"><span data-stu-id="a9079-118">As the initial configuration of an extended test environment of your own design that includes additional virtual machines, Azure services, or other Microsoft cloud offerings such as Office 365 and Enterprise Mobility + Security (EMS).</span></span>
    
<span data-ttu-id="a9079-119">Es gibt zwei Methoden zum Erstellen dieser Umgebung:</span><span class="sxs-lookup"><span data-stu-id="a9079-119">There are two methods to creating this environment:</span></span>

1. <span data-ttu-id="a9079-120">Eine Azure Resource Manager-Vorlage</span><span class="sxs-lookup"><span data-stu-id="a9079-120">An Azure Resource Manager template</span></span>
2. <span data-ttu-id="a9079-121">Azure Powershell</span><span class="sxs-lookup"><span data-stu-id="a9079-121">Azure Powershell</span></span>

## <a name="method-1-build-your-simulated-intranet-with-an-azure-resource-manager-template"></a><span data-ttu-id="a9079-122">Methode 1: Erstellen eines simulierten Intranets mit einer Azure Resource Manager-Vorlage</span><span class="sxs-lookup"><span data-stu-id="a9079-122">Method 1: Build your simulated intranet with an Azure Resource Manager template</span></span>

<span data-ttu-id="a9079-p102">Bei dieser Methode verwenden Sie eine Azure Resource Manager-Vorlage (ARM), um das simulierte Intranet auszubauen. ARM-Vorlagen enthalten alle Anweisungen zum Erstellen und Konfigurieren der Azure-Netzwerkinfrastruktur und der virtuellen Maschinen.</span><span class="sxs-lookup"><span data-stu-id="a9079-p102">In this method, you use an Azure Resource Manager (ARM) template to build out the simulated intranet. ARM templates contain all of the instructions to create and configure the Azure networking infrastructure and the virtual machines.</span></span>

<span data-ttu-id="a9079-125">Lesen Sie vor der Bereitstellung der Vorlage die [Infodatei auf der Vorlagenseite](https://github.com/maxskunkworks/TLG/tree/master/tlg-base-config_3-vm) und halten Sie folgende Informationen bereit:</span><span class="sxs-lookup"><span data-stu-id="a9079-125">Prior to deploying the template, read through the [template README page](https://github.com/maxskunkworks/TLG/tree/master/tlg-base-config_3-vm) and have the following information ready:</span></span>

- <span data-ttu-id="a9079-p103">Den Namen des Azure-Abonnements. Sie müssen diese Bezeichnung in das Feld **Abonnement** auf der Seite **Benutzerdefinierte Bereitstellung** eingeben.</span><span class="sxs-lookup"><span data-stu-id="a9079-p103">The Azure subscription name. You’ll need to enter this label in the **Subscription** field of the **Custom deployment** page.</span></span>
- <span data-ttu-id="a9079-p104">Den Namen der Ressourcengruppe. Sie müssen diese Bezeichnung in das Feld **Ressourcengruppe** auf der Seite **Benutzerdefinierte Bereitstellung** eingeben.</span><span class="sxs-lookup"><span data-stu-id="a9079-p104">The Azure resource group name. You’ll need to enter this label in the **Resource group** field of the **Custom deployment** page.</span></span>
- <span data-ttu-id="a9079-p105">Ein DNS-Präfix für die URLs der öffentlichen IP-Adressen Ihrer virtueller Computer. Sie müssen diese Bezeichnung in das Feld **DNS-Präfix** der Seite **Benutzerdefinierte Bereitstellung** eingeben.</span><span class="sxs-lookup"><span data-stu-id="a9079-p105">A DNS label prefix for the URLs of the public IP addresses of your virtual machines. You’ll need to enter this label in the **Dns Label Prefix** field of the **Custom deployment** page.</span></span>

<span data-ttu-id="a9079-132">Klicken Sie nach dem Lesen der Anweisungen auf **In Azure bereitstellen** in der [Infodatei auf der Vorlagenseite](https://github.com/maxskunkworks/TLG/tree/master/tlg-base-config_3-vm), um loszulegen.</span><span class="sxs-lookup"><span data-stu-id="a9079-132">After reading through the instructions, click **Deploy to Azure** on the [template README page](https://github.com/maxskunkworks/TLG/tree/master/tlg-base-config_3-vm) to get started.</span></span>

>[!Note]
><span data-ttu-id="a9079-133">Das anhand der ARM-Vorlage erstellte simulierte Intranet erfordert ein kostenpflichtiges Azure-Abonnement.</span><span class="sxs-lookup"><span data-stu-id="a9079-133">The simulated intranet built by the ARM template requires a paid Azure subscription.</span></span>
>

<span data-ttu-id="a9079-134">Hier finden Sie Ihre Konfiguration nach Abschluss der Vorlage.</span><span class="sxs-lookup"><span data-stu-id="a9079-134">Here is your configuration after the template is complete.</span></span>

![Die Basiskonfiguration in Azure](media/25a010a6-c870-4690-b8f3-84421f8bc5c7.png)


## <a name="method-2-build-your-simulated-intranet-with-azure-powershell"></a><span data-ttu-id="a9079-136">Methode 2: Erstellen Ihres simulierten Intranets mit Azure PowerShell</span><span class="sxs-lookup"><span data-stu-id="a9079-136">Method 2: Build your simulated intranet with Azure PowerShell</span></span>

<span data-ttu-id="a9079-137">Bei dieser Methode verwenden Sie Windows PowerShell und das Azure PowerShell-Modul zum Erstellen der Netzwerkinfrastruktur, der virtuellen Computer und ihrer Konfiguration.</span><span class="sxs-lookup"><span data-stu-id="a9079-137">In this method, you use Windows PowerShell and the Azure PowerShell module to build out the networking infrastructure, the virtual machines, and their configuration.</span></span>

<span data-ttu-id="a9079-p106">Verwenden Sie diese Methode, wenn Sie Erfahrungen mit dem Erstellen von Elementen der Azure-Infrastruktur für jeden einzelnen Befehlsblock mit PowerShell sammeln möchten. Sie können dann die PowerShell-Befehlsblöcke für eine eigene Bereitstellung von anderen virtuellen Computern in Azure anpassen.</span><span class="sxs-lookup"><span data-stu-id="a9079-p106">Use this method if you want to get experience creating elements of Azure infrastructure one command block at a time with PowerShell. You can then customize the PowerShell command blocks for your own deployment of other virtual machines in Azure.</span></span>

<span data-ttu-id="a9079-140">Es gibt vier Schritte bei der Einrichtung der Basiskonfiguration für die Testumgebung mithilfe von Azure PowerShell:</span><span class="sxs-lookup"><span data-stu-id="a9079-140">There are four steps to setting up the Base Configuration test environment using Azure PowerShell:</span></span>
  
1. <span data-ttu-id="a9079-141">Erstellen des virtuellen Netzwerks</span><span class="sxs-lookup"><span data-stu-id="a9079-141">Create the virtual network.</span></span>
    
2. <span data-ttu-id="a9079-142">Konfigurieren von DC1</span><span class="sxs-lookup"><span data-stu-id="a9079-142">Configure DC1.</span></span>
    
3. <span data-ttu-id="a9079-143">Konfigurieren von APP1</span><span class="sxs-lookup"><span data-stu-id="a9079-143">Configure APP1.</span></span>
    
4. <span data-ttu-id="a9079-144">Konfigurieren von CLIENT1</span><span class="sxs-lookup"><span data-stu-id="a9079-144">Configure CLIENT1.</span></span>
    
<span data-ttu-id="a9079-p107">Wenn Sie noch kein Azure-Abonnement haben, können Sie sich für eine kostenlose Testversion unter [Testen von Azure](https://azure.microsoft.com/pricing/free-trial/) registrieren. Wenn Sie über ein MSDN- oder Visual Studio-Abonnement verfügen, lesen Sie die Informationen unter [Monatliche Azure-Gutschrift für Visual Studio-Abonnenten](https://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/).</span><span class="sxs-lookup"><span data-stu-id="a9079-p107">If you do not already have an Azure subscription, you can sign up for a free trial at [Try Azure](https://azure.microsoft.com/pricing/free-trial/). If you have an MSDN or Visual Studio subscription, see [Monthly Azure credit for Visual Studio subscribers](https://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/).</span></span>
  
> [!NOTE]
> <span data-ttu-id="a9079-p108">Für virtuelle Computer in Azure entstehen laufende finanzielle Kosten, wenn sie ausgeführt werden. Diese Kosten werden gegen Ihre kostenlose Testversion, Ihr MSDN-Abonnement oder Ihr kostenpflichtiges Abonnement berechnet. Weitere Informationen zu den Kosten der Ausführung virtueller Azure-Computer finden Sie unter [Preisdetails für virtuelle Computer](https://azure.microsoft.com/pricing/details/virtual-machines/) und [Azure-Preisrechner](https://azure.microsoft.com/pricing/calculator/). Informationen dazu, wie Sie die Kosten niedrig halten, finden Sie unter [Minimierung der Kosten für virtuelle Computer der Testumgebung in Azure](base-configuration-dev-test-environment.md#mincost).</span><span class="sxs-lookup"><span data-stu-id="a9079-p108">Virtual machines in Azure incur an ongoing monetary cost when they are running. This cost is billed against your free trial, MSDN subscription, or paid subscription. For more information about the costs of running Azure virtual machines, see [Virtual Machines Pricing Details](https://azure.microsoft.com/pricing/details/virtual-machines/) and [Azure Pricing Calculator](https://azure.microsoft.com/pricing/calculator/). To keep costs down, see [Minimizing the costs of test environment virtual machines in Azure](base-configuration-dev-test-environment.md#mincost).</span></span> 
  
![Testumgebungsanleitungen in der Microsoft Cloud](media/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
> [!TIP]
> <span data-ttu-id="a9079-152">Klicken Sie [hier](https://aka.ms/catlgstack), um eine visuelle Darstellung aller Artikel im Stapel der Testumgebungsanleitungen in Office 365 zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="a9079-152">Click [here](https://aka.ms/catlgstack) for a visual map to all the articles in the Office 365 Test Lab Guide stack.</span></span>
  
### <a name="step-1-create-the-virtual-network"></a><span data-ttu-id="a9079-153">Schritt 1: Erstellen des virtuellen Netzwerks</span><span class="sxs-lookup"><span data-stu-id="a9079-153">Step 1: Create the virtual network</span></span>

<span data-ttu-id="a9079-154">In diesem Schritt, erstellen Sie das virtuelle Netzwerk „TestLab“ in Azure.</span><span class="sxs-lookup"><span data-stu-id="a9079-154">In this step, you the TestLab virtual network in Azure.</span></span>

<span data-ttu-id="a9079-155">Starten Sie zunächst eine Azure PowerShell-Eingabeaufforderung.</span><span class="sxs-lookup"><span data-stu-id="a9079-155">First, start an Azure PowerShell prompt.</span></span>
  
> [!NOTE]
> <span data-ttu-id="a9079-p109">In den folgenden Befehlssätzen wird die aktuelle Version von Azure PowerShell verwendet. Informationen dazu finden Sie unter [Erste Schritte mit Azure PowerShell-Cmdlets](https://docs.microsoft.com/powershell/azureps-cmdlets-docs/).</span><span class="sxs-lookup"><span data-stu-id="a9079-p109">The following command sets use the latest version of Azure PowerShell. See [Get started with Azure PowerShell cmdlets](https://docs.microsoft.com/powershell/azureps-cmdlets-docs/).</span></span> 
  
<span data-ttu-id="a9079-158">Melden Sie sich mit dem folgenden Befehl bei Ihrem Azure-Konto an.</span><span class="sxs-lookup"><span data-stu-id="a9079-158">Sign in to your Azure account with the following command.</span></span>
  
```
Connect-AzAccount
```

> [!TIP]
> <span data-ttu-id="a9079-159">Klicken Sie [hier](https://gallery.technet.microsoft.com/PowerShell-commands-for-ba957d3d), um eine Textdatei zu erhalten, die alle PowerShell-Befehle in diesem Artikel enthält.</span><span class="sxs-lookup"><span data-stu-id="a9079-159">Click [here](https://gallery.technet.microsoft.com/PowerShell-commands-for-ba957d3d) to get a text file that has all the PowerShell commands in this article.</span></span>

<span data-ttu-id="a9079-160">Rufen Sie den Namen Ihres Abonnements mithilfe des folgenden Befehls ab.</span><span class="sxs-lookup"><span data-stu-id="a9079-160">Get your subscription name using the following command.</span></span>
  
```
Get-AzSubscription | Sort Name | Select Name
```

<span data-ttu-id="a9079-p110">Tragen Sie Ihr Azure-Abonnement ein. Ersetzen Sie alles innerhalb der Anführungszeichen, einschließlich der Zeichen „<“ und „>“, durch den entsprechenden Namen.</span><span class="sxs-lookup"><span data-stu-id="a9079-p110">Set your Azure subscription. Replace everything within the quotes, including the < and > characters, with the correct name.</span></span>
  
```
$subscrName="<subscription name>"
Select-AzSubscription -SubscriptionName $subscrName
```

<span data-ttu-id="a9079-p111">Im nächsten Schritt wird eine neue Ressourcengruppe für Ihre Basiskonfiguration des Testlabors erstellt. Verwenden Sie zum Ermitteln eines eindeutigen Ressourcengruppennamens diesen Befehl, mit dem die vorhandenen Ressourcengruppen aufgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="a9079-p111">Next, create a new resource group for your Base Configuration test lab. To determine a unique resource group name, use this command to list your existing resource groups.</span></span>
  
```
Get-AzResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

<span data-ttu-id="a9079-p112">Erstellen Sie die neue Ressourcengruppe mit diesen Befehlen. Ersetzen Sie alles innerhalb der Anführungszeichen, einschließlich der Zeichen „<“ und „>“, durch die entsprechenden Namen.</span><span class="sxs-lookup"><span data-stu-id="a9079-p112">Create your new resource group with these commands. Replace everything within the quotes, including the < and > characters, with the correct names.</span></span>
  
```
$rgName="<resource group name>"
$locName="<location name, such as West US>"
New-AzResourceGroup -Name $rgName -Location $locName
```

<span data-ttu-id="a9079-167">Im nächsten Schritt erstellen Sie das virtuelle Netzwerk „TestLab“, das das Unternehmensnetzwerk-Subnetz der Basiskonfiguration hostet, und schützen es mit einer Netzwerksicherheitsgruppe.</span><span class="sxs-lookup"><span data-stu-id="a9079-167">Next, you create the TestLab virtual network that will host the Corpnet subnet of the base configuration and protect it with a network security group.</span></span>
  
```
$rgName="<name of your new resource group>"
$locName=(Get-AzResourceGroup -Name $rgName).Location
$corpnetSubnet=New-AzVirtualNetworkSubnetConfig -Name Corpnet -AddressPrefix 10.0.0.0/24
New-AzVirtualNetwork -Name TestLab -ResourceGroupName $rgName -Location $locName -AddressPrefix 10.0.0.0/8 -Subnet $corpnetSubnet -DNSServer 10.0.0.4
$rule1=New-AzNetworkSecurityRuleConfig -Name "RDPTraffic" -Description "Allow RDP to all VMs on the subnet" -Access Allow -Protocol Tcp -Direction Inbound -Priority 100 -SourceAddressPrefix Internet -SourcePortRange * -DestinationAddressPrefix * -DestinationPortRange 3389
New-AzNetworkSecurityGroup -Name Corpnet -ResourceGroupName $rgName -Location $locName -SecurityRules $rule1
$vnet=Get-AzVirtualNetwork -ResourceGroupName $rgName -Name TestLab
$nsg=Get-AzNetworkSecurityGroup -Name Corpnet -ResourceGroupName $rgName
Set-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name Corpnet -AddressPrefix "10.0.0.0/24" -NetworkSecurityGroup $nsg
$vnet | Set-AzVirtualNetwork
```

<span data-ttu-id="a9079-168">Dies ist Ihre aktuelle Konfiguration.</span><span class="sxs-lookup"><span data-stu-id="a9079-168">This is your current configuration.</span></span>
  
![Schritt 1 der Basiskonfiguration in Azure mit dem virtuellen Netzwerk und Subnetz](media/0b5634fc-4e1c-469d-873d-97ed7e587411.png)
  
### <a name="step-2-configure-dc1"></a><span data-ttu-id="a9079-170">Schritt 2: Konfigurieren von DC1</span><span class="sxs-lookup"><span data-stu-id="a9079-170">Step 2: Configure DC1</span></span>

<span data-ttu-id="a9079-171">In diesem Schritt erstellen Sie den virtuellen Computer DC1 und konfigurieren diesen als Domänencontroller für die AD DS-Domäne (Active Directory Domain Services) „corp.contoso.com“ sowie einen DNS-Server für die virtuellen Computer des virtuellen Netzwerks TestLab.</span><span class="sxs-lookup"><span data-stu-id="a9079-171">In this step, we create the DC1 virtual machine and configure it as a domain controller for the corp.contoso.com Active Directory Domain Services (AD DS) domain and a DNS server for the virtual machines of the TestLab virtual network.</span></span>

> [!NOTE]
> <span data-ttu-id="a9079-p113">Stellen Sie vor dem Ausführen des folgenden Befehlsblocks sicher, dass die Azure-Region (Standort), die Sie ausgewählt haben, die Größe der Azure-VM unterstützt, die standardmäßig auf Standard_A1 festgelegt ist. Klicken Sie [hier](https://azure.microsoft.com/global-infrastructure/services/?products=virtual-machines), um die neuesten Informationen zu den Größen und Standorten von Azure-VMs anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="a9079-p113">Before executing the following command block, ensure that the Azure region (location) that you have chosen supports the Azure virtual machine size, which by default is set to Standard_A1. Click [here](https://azure.microsoft.com/global-infrastructure/services/?products=virtual-machines) to see the latest information on Azure virtual machine sizes and locations.</span></span>
  
<span data-ttu-id="a9079-174">Geben Sie zum Erstellen eines virtuellen Azure-Computers für DC1 den Namen Ihrer Ressourcengruppe ein, und führen Sie über die Azure PowerShell-Eingabeaufforderung auf Ihrem lokalen Computer die nachfolgenden Befehle aus.</span><span class="sxs-lookup"><span data-stu-id="a9079-174">To create an Azure virtual machine for DC1, fill in the name of your resource group and run these commands at the Azure PowerShell command prompt on your local computer.</span></span>
  
```
$rgName="<resource group name>"
$locName=(Get-AzResourceGroup -Name $rgName).Location
$vnet=Get-AzVirtualNetwork -Name TestLab -ResourceGroupName $rgName
$pip=New-AzPublicIpAddress -Name DC1-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic=New-AzNetworkInterface -Name DC1-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id -PrivateIpAddress 10.0.0.4
$vm=New-AzVMConfig -VMName DC1 -VMSize Standard_A1
$cred=Get-Credential -Message "Type the name and password of the local administrator account for DC1."
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName DC1 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name "DC1-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "Standard_LRS"
$diskConfig=New-AzDiskConfig -AccountType "Standard_LRS" -Location $locName -CreateOption Empty -DiskSizeGB 20
$dataDisk1=New-AzDisk -DiskName "DC1-DataDisk1" -Disk $diskConfig -ResourceGroupName $rgName
$vm=Add-AzVMDataDisk -VM $vm -Name "DC1-DataDisk1" -CreateOption Attach -ManagedDiskId $dataDisk1.Id -Lun 1
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

<span data-ttu-id="a9079-p114">Sie werden nach einem Benutzernamen und Kennwort für das lokale Administratorkonto auf DC1 gefragt. Verwenden Sie ein sicheres Kennwort, und notieren Sie den Namen und das Kennwort an einem sicheren Ort.</span><span class="sxs-lookup"><span data-stu-id="a9079-p114">You will be prompted for a user name and password for the local administrator account on DC1. Use a strong password and record both the name and password in a secure location.</span></span>
  
<span data-ttu-id="a9079-177">Stellen Sie dann eine Verbindung mit dem virtuellen Computer DC1 her.</span><span class="sxs-lookup"><span data-stu-id="a9079-177">Next, connect to the DC1 virtual machine.</span></span>
  
1. <span data-ttu-id="a9079-178">Klicken Sie im [Azure-Portal](https://portal.azure.com) auf **Ressourcengruppen >** [Name der neuen Ressourcengruppe] **> DC1 > Verbinden**.</span><span class="sxs-lookup"><span data-stu-id="a9079-178">In the [Azure portal](https://portal.azure.com), click **Resource Groups >** [the name of your new resource group] **> DC1 > Connect**.</span></span>
    
2. <span data-ttu-id="a9079-p115">Klicken Sie im Bereich „Öffnen“ auf  **RDP-Datei herunterladen**. Öffnen Sie die Datei „DC1.rdp“, die heruntergeladen wird, und klicken Sie dann auf **Verbinden**.</span><span class="sxs-lookup"><span data-stu-id="a9079-p115">In the open pane, click **Download RDP file**. Open the DC1.rdp file that is downloaded, and then click **Connect**.</span></span>
    
3. <span data-ttu-id="a9079-181">Geben Sie den Namen des lokalen DC1-Administratorkontos an:</span><span class="sxs-lookup"><span data-stu-id="a9079-181">Specify the DC1 local administrator account name:</span></span>
    
  - <span data-ttu-id="a9079-182">Für Windows 7:</span><span class="sxs-lookup"><span data-stu-id="a9079-182">For Windows 7:</span></span>
    
    <span data-ttu-id="a9079-p116">Klicken Sie im Dialogfeld **Windows-Sicherheit** auf **Anderes Konto verwenden**. Geben Sie unter **Benutzername** den Namen **DC1\\**[Kontoname des lokalen Administrators] ein.</span><span class="sxs-lookup"><span data-stu-id="a9079-p116">In the **Windows Security** dialog box, click **Use another account**. In **User name**, type **DC1\\**[Local administrator account name].</span></span>
    
  - <span data-ttu-id="a9079-185">Für Windows 8 oder Windows 10:</span><span class="sxs-lookup"><span data-stu-id="a9079-185">For Windows 8 or Windows 10:</span></span>
    
    <span data-ttu-id="a9079-p117">Klicken Sie im Dialogfeld **Windows-Sicherheit** auf **Weitere Optionen**, und klicken Sie dann auf **Anderes Konto verwenden**. Geben Sie unter **Benutzername** den Namen **DC1\\**[Kontoname des lokalen Administrators] ein.</span><span class="sxs-lookup"><span data-stu-id="a9079-p117">In the **Windows Security** dialog box, click **More choices**, and then click **Use a different account**. In **User name**, type **DC1\\**[Local administrator account name].</span></span>
    
4. <span data-ttu-id="a9079-188">Geben Sie unter **Kennwort** das Kennwort des lokalen Administratorkontos ein, und klicken Sie dann auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="a9079-188">In **Password**, type the password of the local administrator account, and then click **OK**.</span></span>
    
5. <span data-ttu-id="a9079-189">Klicken Sie auf **Ja**, wenn Sie dazu aufgefordert werden.</span><span class="sxs-lookup"><span data-stu-id="a9079-189">When prompted, click **Yes**.</span></span>
    
<span data-ttu-id="a9079-190">Im nächsten Schritt führen Sie diesen Befehl über eine Windows PowerShell-Eingabeaufforderung mit Administratorrechten auf DC1 aus, um ein zusätzliches Datenlaufwerk als neues Volume mit dem Laufwerkbuchstaben „F:" hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="a9079-190">Next, add an extra data disk as a new volume with the drive letter F: with this command at an administrator-level Windows PowerShell command prompt on DC1.</span></span>
  
```
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

<span data-ttu-id="a9079-p118">Konfigurieren Sie als Nächstes DC1 als Domänencontroller und DNS-Server für die Domäne „corp.contoso.com“. Führen Sie diese Befehle an einer Windows PowerShell-Eingabeaufforderung auf Administratorebene aus.</span><span class="sxs-lookup"><span data-stu-id="a9079-p118">Next, configure DC1 as a domain controller and DNS server for the corp.contoso.com domain. Run these commands at an administrator-level Windows PowerShell command prompt.</span></span>
  
```
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSForest -DomainName corp.contoso.com -DatabasePath "F:\NTDS" -SysvolPath "F:\SYSVOL" -LogPath "F:\Logs"
```
<span data-ttu-id="a9079-p119">Sie müssen ein Administratorkennwort für den abgesicherten Modus angeben. Bewahren Sie das Kennwort an einem sicheren Ort auf.</span><span class="sxs-lookup"><span data-stu-id="a9079-p119">You will need to specify a safe mode administrator password. Store this password in a secure location.</span></span>
  
<span data-ttu-id="a9079-195">Beachten Sie, dass der Abschluss dieser Befehle ein paar Minuten in Anspruch nehmen kann.</span><span class="sxs-lookup"><span data-stu-id="a9079-195">Note that these commands can take a few minutes to complete.</span></span>
  
<span data-ttu-id="a9079-196">Stellen Sie nach dem Neustart von DC1 mithilfe von Domänenanmeldeinformationen wieder eine Verbindung zum virtuellen DC1-Computer her.</span><span class="sxs-lookup"><span data-stu-id="a9079-196">After DC1 restarts, reconnect to the DC1 virtual machine using domain credentials.</span></span>
  
1. <span data-ttu-id="a9079-197">Klicken Sie im [Azure-Portal](https://portal.azure.com) auf **Ressourcengruppen >** [Ihre Ressourcengruppe] **> DC1 > Verbinden**.</span><span class="sxs-lookup"><span data-stu-id="a9079-197">In the [Azure portal](https://portal.azure.com), click **Resource Groups >** [your resource group name] **> DC1 > Connect**.</span></span>
    
2. <span data-ttu-id="a9079-198">Führen Sie die Datei „DC1.rdp“ aus, die heruntergeladen wurde, und klicken Sie dann auf **Verbinden**.</span><span class="sxs-lookup"><span data-stu-id="a9079-198">Run the DC1.rdp file that is downloaded, and then click **Connect**.</span></span>
    
3. <span data-ttu-id="a9079-p120">Klicken Sie unter **Windows-Sicherheit** auf **Anderes Konto verwenden**. Geben Sie unter **Benutzername** den Namen **CORP\\**[Kontoname des lokalen Administrators] ein.</span><span class="sxs-lookup"><span data-stu-id="a9079-p120">In **Windows Security**, click **Use another account**. In **User name**, type **CORP\\**[Local administrator account name].</span></span>
    
4. <span data-ttu-id="a9079-201">Geben Sie unter **Kennwort** das Kennwort des lokalen Administratorkontos ein, und klicken Sie dann auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="a9079-201">In **Password**, type the password of the local administrator account, and then click **OK**.</span></span>
    
5. <span data-ttu-id="a9079-202">Klicken Sie auf **Ja**, wenn Sie dazu aufgefordert werden.</span><span class="sxs-lookup"><span data-stu-id="a9079-202">When prompted, click **Yes**.</span></span>
    
<span data-ttu-id="a9079-p121">Im nächsten Schritt erstellen Sie ein Benutzerkonto in Active Directory, das bei der Anmeldung an Mitgliedscomputern der Domäne CORP verwendet wird. Führen Sie diesen Befehl an einer Windows PowerShell-Eingabeaufforderung auf Administratorebene aus.</span><span class="sxs-lookup"><span data-stu-id="a9079-p121">Next, create a user account in Active Directory that will be used when logging in to CORP domain member computers. Run this command at an administrator-level Windows PowerShell command prompt.</span></span>
  
```
New-ADUser -SamAccountName User1 -AccountPassword (read-host "Set user password" -assecurestring) -name "User1" -enabled $true -PasswordNeverExpires $true -ChangePasswordAtLogon $false
```

<span data-ttu-id="a9079-p122">Beachten Sie, dass Sie von dem Befehl aufgefordert werden, das Kennwort des Kontos „User1“ anzugeben. Da dieses Konto für Remotedesktopverbindungen für alle Mitgliedscomputer der Domäne CORP verwendet wird, sollten Sie ein sicheres Kennwort wählen. Notieren Sie das Kennwort des Kontos „User1“, und bewahren Sie es an einem sicheren Ort auf.</span><span class="sxs-lookup"><span data-stu-id="a9079-p122">Note that this command prompts you to supply the User1 account password. Because this account will be used for remote desktop connections for all CORP domain member computers, choose a strong password. Record the User1 account password and store it in a secured location.</span></span>
  
<span data-ttu-id="a9079-p123">Konfigurieren Sie als Nächstes das neue Konto „User1“ als Unternehmensadministrator. Führen Sie diesen Befehl an der Windows PowerShell-Eingabeaufforderung auf Administratorebene aus.</span><span class="sxs-lookup"><span data-stu-id="a9079-p123">Next, configure the new User1 account as an Enterprise Administrator. Run this command at the administrator-level Windows PowerShell command prompt.</span></span>
  
```
Add-ADPrincipalGroupMembership -Identity "CN=User1,CN=Users,DC=corp,DC=contoso,DC=com" -MemberOf "CN=Enterprise Admins,CN=Users,DC=corp,DC=contoso,DC=com","CN=Domain Admins,CN=Users,DC=corp,DC=contoso,DC=com","CN=Schema Admins,CN=Users,DC=corp,DC=contoso,DC=com"
```

<span data-ttu-id="a9079-210">Schließen Sie die Remotedesktopsitzung mit DC1, und stellen Sie dann mit dem Konto „CORP\\User1“ wieder eine Verbindung her.</span><span class="sxs-lookup"><span data-stu-id="a9079-210">Close the Remote Desktop session with DC1 and then reconnect using the CORP\\User1 account.</span></span>
  
<span data-ttu-id="a9079-211">Führen Sie als Nächstes den folgenden Befehl an einer Windows PowerShell-Eingabeaufforderung auf Administratorebene aus, um Datenverkehr für das Tool Ping zuzulassen.</span><span class="sxs-lookup"><span data-stu-id="a9079-211">Next, to allow traffic for the Ping tool, run this command at an administrator-level Windows PowerShell command prompt.</span></span>
  
```
Set-NetFirewallRule -DisplayName "File and Printer Sharing (Echo Request - ICMPv4-In)" -enabled True
```

<span data-ttu-id="a9079-212">Dies ist Ihre aktuelle Konfiguration.</span><span class="sxs-lookup"><span data-stu-id="a9079-212">This is your current configuration.</span></span>
  
![Schritt 2 der Basiskonfiguration in Azure mit dem virtuellen Computer DC1](media/49069908-29c3-4d73-87f7-debbea067261.png)
  
### <a name="step-3-configure-app1"></a><span data-ttu-id="a9079-214">Schritt 3: Konfigurieren von APP1</span><span class="sxs-lookup"><span data-stu-id="a9079-214">Step 3: Configure APP1</span></span>

<span data-ttu-id="a9079-215">In diesem Schritt erstellen und konfigurieren Sie APP1, der Web- und Dateifreigabedienste bereitstellt.</span><span class="sxs-lookup"><span data-stu-id="a9079-215">In this step, you create and configure APP1, which provides web and file sharing services.</span></span>

> [!NOTE]
> <span data-ttu-id="a9079-p124">Stellen Sie vor dem Ausführen des folgenden Befehlsblocks sicher, dass die Azure-Region (Standort), die Sie ausgewählt haben, die Größe der Azure-VM unterstützt, die standardmäßig auf Standard_A1 festgelegt ist. Klicken Sie [hier](https://azure.microsoft.com/global-infrastructure/services/?products=virtual-machines), um die neuesten Informationen zu den Größen und Standorten von Azure-VMs anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="a9079-p124">Before executing the following command block, ensure that the Azure region (location) that you have chosen supports the Azure virtual machine size, which by default is set to Standard_A1. Click [here](https://azure.microsoft.com/global-infrastructure/services/?products=virtual-machines) to see the latest information on Azure virtual machine sizes and locations.</span></span>
  
<span data-ttu-id="a9079-218">Geben Sie zum Erstellen eines virtuellen Azure-Computers für APP1 den Namen Ihrer Ressourcengruppe ein, und führen Sie über die Azure PowerShell-Eingabeaufforderung auf Ihrem lokalen Computer die nachfolgenden Befehle aus.</span><span class="sxs-lookup"><span data-stu-id="a9079-218">To create an Azure Virtual Machine for APP1, fill in the name of your resource group and run these commands at the Azure PowerShell command prompt on your local computer.</span></span>
  
```
$rgName="<resource group name>"
$locName=(Get-AzResourceGroup -Name $rgName).Location
$vnet=Get-AzVirtualNetwork -Name TestLab -ResourceGroupName $rgName
$pip=New-AzPublicIpAddress -Name APP1-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic=New-AzNetworkInterface -Name APP1-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id
$vm=New-AzVMConfig -VMName APP1 -VMSize Standard_A1
$cred=Get-Credential -Message "Type the name and password of the local administrator account for APP1."
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName APP1 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name "APP1-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "Standard_LRS"
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

<span data-ttu-id="a9079-219">Im nächsten Schritt stellen Sie eine Verbindung mit dem virtuellen Computer APP1 mit dem Kontonamen und Kennwort des lokalen Administratorkontos von APP1 her und öffnen dann eine Windows PowerShell-Eingabeaufforderung.</span><span class="sxs-lookup"><span data-stu-id="a9079-219">Next, connect to the APP1 virtual machine using the APP1 local administrator account name and password, and then open a Windows PowerShell command prompt.</span></span>
  
<span data-ttu-id="a9079-220">Führen Sie zum Überprüfen der Namensauflösung und der Netzwerkkommunikation zwischen APP1 und DC1 den Befehl **ping dc1.corp.contoso.com** aus, und vergewissern Sie sich, dass vier Antworten vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="a9079-220">To check name resolution and network communication between APP1 and DC1, run the **ping dc1.corp.contoso.com** command and check that there are four replies.</span></span>
  
<span data-ttu-id="a9079-221">Verknüpfen Sie als Nächstes unter Verwendung der folgenden Befehle an der Windows PowerShell-Eingabeaufforderung den virtuellen Computer APP1 mit der Domäne CORP.</span><span class="sxs-lookup"><span data-stu-id="a9079-221">Next, join the APP1 virtual machine to the CORP domain with these commands at the Windows PowerShell prompt.</span></span>
  
```
Add-Computer -DomainName corp.contoso.com
Restart-Computer
```

<span data-ttu-id="a9079-222">Beachten Sie, dass Sie nach der Ausführung des Befehls **Add-Computer** die Anmeldeinformationen für das Domänenkonto „CORP\\User1“ eingeben müssen.</span><span class="sxs-lookup"><span data-stu-id="a9079-222">Note that you must supply the CORP\\User1 domain account credentials after running the **Add-Computer** command.</span></span>
  
<span data-ttu-id="a9079-223">Stellen Sie nach dem Neustart von APP1 eine Verbindung über das Konto „CORP\\User1“ damit her, und öffnen Sie dann eine Windows PowerShell-Eingabeaufforderung auf Administratorebene.</span><span class="sxs-lookup"><span data-stu-id="a9079-223">After APP1 restarts, connect to it using the CORP\\User1 account, and then open an administrator-level Windows PowerShell command prompt.</span></span>
  
<span data-ttu-id="a9079-224">Im nächsten Schritt richten Sie APP1 mit dem folgenden Befehl in der Windows PowerShell-Eingabeaufforderung auf APP1 als Webserver ein.</span><span class="sxs-lookup"><span data-stu-id="a9079-224">Next, make APP1 a web server with this command at the Windows PowerShell command prompt on APP1.</span></span>
  
```
Install-WindowsFeature Web-WebServer -IncludeManagementTools
```

<span data-ttu-id="a9079-225">Erstellen Sie als Nächstes einen freigegebenen Ordner und eine Textdatei innerhalb des Ordners auf APP1 mit diesen PowerShell-Befehlen.</span><span class="sxs-lookup"><span data-stu-id="a9079-225">Next, create a shared folder and a text file within the folder on APP1 with these PowerShell commands.</span></span>
  
```
New-Item -path c:\files -type directory
Write-Output "This is a shared file." | out-file c:\files\example.txt
New-SmbShare -name files -path c:\files -changeaccess CORP\User1
```

<span data-ttu-id="a9079-226">Dies ist Ihre aktuelle Konfiguration.</span><span class="sxs-lookup"><span data-stu-id="a9079-226">This is your current configuration.</span></span>
  
![Schritt 3 der Basiskonfiguration in Azure mit dem virtuellen Computer APP1](media/92cfabb0-7f9d-4291-964d-ac32d52748d7.png)
  
### <a name="step-4-configure-client1"></a><span data-ttu-id="a9079-228">Schritt 4: Konfigurieren von CLIENT1</span><span class="sxs-lookup"><span data-stu-id="a9079-228">Step 4: Configure CLIENT1</span></span>

<span data-ttu-id="a9079-229">In diesem Schritt wird CLIENT1 erstellt und konfiguriert, der als typischer Laptop, als Tablet oder als Desktopcomputer im Contoso-Intranet fungiert.</span><span class="sxs-lookup"><span data-stu-id="a9079-229">In this step, you create and configure CLIENT1, which acts as a typical laptop, tablet, or desktop computer on the Contoso intranet.</span></span>

> [!NOTE]  
> <span data-ttu-id="a9079-p125">Der folgende Befehlssatz erstellt CLIENT1 unter Windows Server 2016 Datacenter. Er gilt für alle Arten von Azure-Abonnements. Wenn Sie über ein Visual Studio-basiertes Azure-Abonnement verfügen, können Sie CLIENT1 unter Windows 10 mit dem [Azure-Portal](https://portal.azure.com) erstellen.</span><span class="sxs-lookup"><span data-stu-id="a9079-p125">The following command set creates CLIENT1 running Windows Server 2016 Datacenter, which can be done for all types of Azure subscriptions. If you have an Visual Studio-based Azure subscription, you can create CLIENT1 running Windows 10 with the [Azure portal](https://portal.azure.com).</span></span> 
  

> [!NOTE]
> <span data-ttu-id="a9079-p126">Stellen Sie vor dem Ausführen des folgenden Befehlsblocks sicher, dass die Azure-Region (Standort), die Sie ausgewählt haben, die Größe der Azure-VM unterstützt, die standardmäßig auf Standard_A1 festgelegt ist. Klicken Sie [hier](https://azure.microsoft.com/global-infrastructure/services/?products=virtual-machines), um die neuesten Informationen zu den Größen und Standorten von Azure-VMs anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="a9079-p126">Before executing the following command block, ensure that the Azure region (location) that you have chosen supports the Azure virtual machine size, which by default is set to Standard_A1. Click [here](https://azure.microsoft.com/global-infrastructure/services/?products=virtual-machines) to see the latest information on Azure virtual machine sizes and locations.</span></span>
  
<span data-ttu-id="a9079-234">Geben Sie zum Erstellen eines virtuellen Azure-Computers für CLIENT1 den Namen Ihrer Ressourcengruppe ein, und führen Sie über die Azure PowerShell-Eingabeaufforderung auf Ihrem lokalen Computer die nachfolgenden Befehle aus.</span><span class="sxs-lookup"><span data-stu-id="a9079-234">To create an Azure Virtual Machine for CLIENT1, fill in the name of your resource group and run these commands at the Azure PowerShell command prompt on your local computer.</span></span>
  
```
$rgName="<resource group name>"
$locName=(Get-AzResourceGroup -Name $rgName).Location
$vnet=Get-AzVirtualNetwork -Name TestLab -ResourceGroupName $rgName
$pip=New-AzPublicIpAddress -Name CLIENT1-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic=New-AzNetworkInterface -Name CLIENT1-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id
$vm=New-AzVMConfig -VMName CLIENT1 -VMSize Standard_A1
$cred=Get-Credential -Message "Type the name and password of the local administrator account for CLIENT1."
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName CLIENT1 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name "CLIENT1-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "Standard_LRS"
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

<span data-ttu-id="a9079-235">Im nächsten Schritt stellen Sie eine Verbindung mit dem virtuellen Computer CLIENT1 mit dem Kontonamen und Kennwort des lokalen Administratorkontos von CLIENT1 her und öffnen dann eine Windows PowerShell-Eingabeaufforderung auf Administratorebene.</span><span class="sxs-lookup"><span data-stu-id="a9079-235">Next, connect to the CLIENT1 virtual machine using the CLIENT1 local administrator account name and password, and then open an administrator-level Windows PowerShell command prompt.</span></span>
  
<span data-ttu-id="a9079-236">Führen Sie zum Überprüfen der Namensauflösung und der Netzwerkkommunikation zwischen CLIENT1 und DC1 den Befehl **ping dc1.corp.contoso.com** an einer Windows PowerShell-Eingabeaufforderung aus, und vergewissern Sie sich, dass vier Antworten vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="a9079-236">To check name resolution and network communication between CLIENT1 and DC1, run the **ping dc1.corp.contoso.com** command at a Windows PowerShell command prompt and check that there are four replies.</span></span>
  
<span data-ttu-id="a9079-237">Verknüpfen Sie als Nächstes unter Verwendung der folgenden Befehle an der Windows PowerShell-Eingabeaufforderung den virtuellen Computer CLIENT1 mit der Domäne CORP.</span><span class="sxs-lookup"><span data-stu-id="a9079-237">Next, join the CLIENT1 virtual machine to the CORP domain with these commands at the Windows PowerShell prompt.</span></span>
  
```
Add-Computer -DomainName corp.contoso.com
Restart-Computer
```

<span data-ttu-id="a9079-238">Beachten Sie, dass Sie nach der Ausführung des Befehls **Add-Computer** Ihre Anmeldeinformationen für das Domänenkonto „CORP\\User1“ eingeben müssen.</span><span class="sxs-lookup"><span data-stu-id="a9079-238">Note that you must supply your CORP\\User1 domain account credentials after running the **Add-Computer** command.</span></span>
  
<span data-ttu-id="a9079-239">Stellen Sie nach dem Neustart von CLIENT1 eine Verbindung über den Kontonamen und das Kennwort von „CORP\\User1“ damit her, und öffnen Sie dann eine Windows PowerShell-Eingabeaufforderung auf Administratorebene.</span><span class="sxs-lookup"><span data-stu-id="a9079-239">After CLIENT1 restarts, connect to it using the CORP\\User1 account name and password, and then open an administrator-level Windows PowerShell command prompt.</span></span>
  
<span data-ttu-id="a9079-240">Überprüfen Sie im nächsten Schritt, ob Sie von CLIENT1 aus auf Web- und Dateifreigaberessourcen auf APP1 zugreifen können.</span><span class="sxs-lookup"><span data-stu-id="a9079-240">Next, check that you can access web and file share resources on APP1 from CLIENT1.</span></span>
  
1. <span data-ttu-id="a9079-241">Klicken Sie im Server-Manager im Strukturbereich auf **Lokaler Server**.</span><span class="sxs-lookup"><span data-stu-id="a9079-241">In Server Manager, in the tree pane, click **Local Server**.</span></span>
    
2. <span data-ttu-id="a9079-242">Klicken Sie in **Eigenschaften für CLIENT1** neben **Verstärkte Sicherheitskonfiguration für IE** auf **Ein**.</span><span class="sxs-lookup"><span data-stu-id="a9079-242">In **Properties for CLIENT1**, click **On** next to **IE Enhanced Security Configuration**.</span></span>
    
3. <span data-ttu-id="a9079-243">Klicken Sie unter **Verstärkte Sicherheitskonfiguration für Internet Explorer** für **Administratoren** und für **Benutzer** auf **Aus**, und klicken Sie dann auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="a9079-243">In **Internet Explorer Enhanced Security Configuration**, click **Off** for **Administrators** and **Users**, and then click **OK**.</span></span>
    
4. <span data-ttu-id="a9079-244">Klicken Sie auf dem Startbildschirm auf **Internet Explorer** und dann auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="a9079-244">From the Start screen, click **Internet Explorer**, and then click **OK**.</span></span>
    
5. <span data-ttu-id="a9079-p127">Geben Sie in der Adressleiste **http:\///app1.corp.contoso.com/** ein, und drücken Sie dann die EINGABETASTE. Nun sollte die standardmäßige Internetinformationsdienste-Webseite für APP1 angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="a9079-p127">In the Address bar, type **http:\//app1.corp.contoso.com/**, and then press ENTER. You should see the default Internet Information Services web page for APP1.</span></span>
    
6. <span data-ttu-id="a9079-247">Klicken Sie auf der Desktop-Taskleiste auf das Symbol für den Datei-Explorer.</span><span class="sxs-lookup"><span data-stu-id="a9079-247">From the desktop taskbar, click the File Explorer icon.</span></span>
    
7. <span data-ttu-id="a9079-p128">Geben Sie in der Adressleiste **\\\\app1\\Files** ein, und drücken Sie dann die EINGABETASTE. Nun sollte ein Ordnerfenster mit dem Inhalt des freigegebenen Ordners „Files“ angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="a9079-p128">In the address bar, type **\\\\app1\\Files**, and then press ENTER. You should see a folder window with the contents of the Files shared folder.</span></span>
    
8. <span data-ttu-id="a9079-p129">Doppelklicken Sie im Fenster des freigegebenen Ordners **Files** auf die Datei **Example.txt**. Nun sollte der Inhalt der Datei „Example.txt“ angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="a9079-p129">In the **Files** shared folder window, double-click the **Example.txt** file. You should see the contents of the Example.txt file.</span></span>
    
9. <span data-ttu-id="a9079-252">Schließen Sie das Fenster **example.txt - Editor** und das Fenster des freigegebenen Ordners **Files**.</span><span class="sxs-lookup"><span data-stu-id="a9079-252">Close the **example.txt - Notepad** and the **Files** shared folder windows.</span></span>
    
<span data-ttu-id="a9079-253">Dies ist Ihre endgültige Konfiguration.</span><span class="sxs-lookup"><span data-stu-id="a9079-253">This is your final configuration.</span></span>
  
![Schritt 4 der Basiskonfiguration in Azure mit dem virtuellen Computer CLIENT1](media/25a010a6-c870-4690-b8f3-84421f8bc5c7.png)
  
<span data-ttu-id="a9079-255">Die Basiskonfiguration in Azure kann nun für die Anwendungsentwicklung und zum Testen oder für die Erstellung zusätzlicher Testumgebungen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="a9079-255">Your Base Configuration in Azure is now ready for application development and testing or for building additional test environments.</span></span> 
  
> [!TIP]
> <span data-ttu-id="a9079-256">Klicken Sie [hier](https://aka.ms/catlgstack), um eine visuelle Darstellung aller Artikel im Stapel der Testumgebungsanleitungen in Office 365 zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="a9079-256">Click [here](https://aka.ms/catlgstack) for a visual map to all of the articles in the Office 365 Test Lab Guide stack.</span></span>
  
<span data-ttu-id="a9079-257"><a name="mincost"> </a></span><span class="sxs-lookup"><span data-stu-id="a9079-257"><a name="mincost"> </a></span></span>
## <a name="minimizing-the-costs-of-test-environment-virtual-machines-in-azure"></a><span data-ttu-id="a9079-258">Minimierung der Kosten für virtuelle Computer der Testumgebung in Azure</span><span class="sxs-lookup"><span data-stu-id="a9079-258">Minimizing the costs of test environment virtual machines in Azure</span></span>

<span data-ttu-id="a9079-259">Um die Kosten für die Ausführung der virtuellen Computer der Testumgebung zu minimieren, können Sie eine der folgenden Aktionen ausführen:</span><span class="sxs-lookup"><span data-stu-id="a9079-259">To minimize the cost of running the test environment virtual machines, you can do one of the following:</span></span>
  
- <span data-ttu-id="a9079-p130">Erstellen Sie die Testumgebung, und führen Sie Ihre benötigten Tests und Demonstrationen so schnell wie möglich aus. Nach Abschluss des Vorgangs löschen Sie die Ressourcengruppe für die Testumgebung.</span><span class="sxs-lookup"><span data-stu-id="a9079-p130">Create the test environment and perform your needed testing and demonstration as quickly as possible. When complete, delete the resource group for the test environment.</span></span>
    
- <span data-ttu-id="a9079-262">Fahren Sie die virtuellen Computer der Testumgebung in den Zustand der aufgehobenen Zuordnung herunter.</span><span class="sxs-lookup"><span data-stu-id="a9079-262">Shut down your test environment virtual machines into a deallocated state.</span></span>
    
<span data-ttu-id="a9079-263">Um die virtuellen Computer mit Azure PowerShell herunterzufahren, geben Sie den Ressourcengruppennamen ein und führen die folgenden Befehle aus.</span><span class="sxs-lookup"><span data-stu-id="a9079-263">To shut down the virtual machines with Azure PowerShell, fill in the resource group name and run these commands.</span></span>
  
```
$rgName="<your resource group name>"
Stop-AzVM -ResourceGroupName $rgName -Name "CLIENT1" -Force
Stop-AzVM -ResourceGroupName $rgName -Name "APP1" -Force
Stop-AzVM -ResourceGroupName $rgName -Name "DC1" -Force
```

<span data-ttu-id="a9079-264">Damit Ihre virtuellen Computer einwandfrei funktionieren, wenn alle aus dem beendeten Zustand (Zuordnung aufgehoben) gestartet werden, sollten Sie sie in der folgenden Reihenfolge starten:</span><span class="sxs-lookup"><span data-stu-id="a9079-264">To ensure that your virtual machines work properly when starting all of them from the Stopped (Deallocated) state, you should start them in the following order:</span></span>
  
1. <span data-ttu-id="a9079-265">DC1</span><span class="sxs-lookup"><span data-stu-id="a9079-265">DC1</span></span>
2. <span data-ttu-id="a9079-266">APP1</span><span class="sxs-lookup"><span data-stu-id="a9079-266">APP1</span></span>
3. <span data-ttu-id="a9079-267">CLIENT1</span><span class="sxs-lookup"><span data-stu-id="a9079-267">CLIENT1</span></span>
    
<span data-ttu-id="a9079-268">Um die virtuellen Computer in der richtigen Reihenfolge mit Azure PowerShell zu starten, geben Sie den Ressourcengruppennamen ein und führen die folgenden Befehle aus.</span><span class="sxs-lookup"><span data-stu-id="a9079-268">To start the virtual machines in order with Azure PowerShell, fill in the resource group name and run these commands.</span></span>
  
```
$rgName="<your resource group name>"
Start-AzVM -ResourceGroupName $rgName -Name "DC1"
Start-AzVM -ResourceGroupName $rgName -Name "APP1"
Start-AzVM -ResourceGroupName $rgName -Name "CLIENT1"
```

## <a name="see-also"></a><span data-ttu-id="a9079-269">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="a9079-269">See Also</span></span>

- [<span data-ttu-id="a9079-270">Office 365-Entwicklungs-/Testumgebung</span><span class="sxs-lookup"><span data-stu-id="a9079-270">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
- [<span data-ttu-id="a9079-271">DirSync für die Office 365-Entwicklungs-/Testumgebung</span><span class="sxs-lookup"><span data-stu-id="a9079-271">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)
- [<span data-ttu-id="a9079-272">Advanced Threat Protection für die Office 365-Entwicklungs-/Testumgebung</span><span class="sxs-lookup"><span data-stu-id="a9079-272">Advanced Threat Protection for your Office 365 dev/test environment</span></span>](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
- [<span data-ttu-id="a9079-273">Cloudakzeptanz und Hybridlösungen</span><span class="sxs-lookup"><span data-stu-id="a9079-273">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)
