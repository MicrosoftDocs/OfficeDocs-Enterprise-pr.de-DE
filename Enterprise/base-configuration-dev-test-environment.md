---
title: Basiskonfiguration der Entwicklungs-/Testumgebung
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/05/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Strat_O365_Enterprise
- Ent_TLGs
ms.assetid: 6fcbb50c-ac68-4be7-9fc5-dd0f275c1e3d
description: 'Zusammenfassung: Erstellen einer vereinfachten Intranet als Test-/Umgebung in Microsoft Azure.'
ms.openlocfilehash: b2bd1c7bb2b0cd100326867fc3603b6afb6cd8db
ms.sourcegitcommit: 1db536d09343bdf6b4eb695ab07890164c047bd3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2018
---
# <a name="base-configuration-devtest-environment"></a><span data-ttu-id="c95c8-103">Basiskonfiguration der Entwicklungs-/Testumgebung</span><span class="sxs-lookup"><span data-stu-id="c95c8-103">Base Configuration dev/test environment</span></span>

 <span data-ttu-id="c95c8-104">**Zusammenfassung:** Erstellen Sie eine vereinfachte Intranet als einer Test-/-Umgebung in Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="c95c8-104">**Summary:** Create a simplified intranet as a dev/test environment in Microsoft Azure.</span></span>
  
<span data-ttu-id="c95c8-105">Dieser Artikel enthält eine schrittweise Anleitung zum Erstellen der folgenden Basiskonfiguration der Entwicklungs-/Testumgebung in Azure:</span><span class="sxs-lookup"><span data-stu-id="c95c8-105">This article provides you with step-by-step instructions to create the following Base Configuration dev/test environment in Azure:</span></span>
  
<span data-ttu-id="c95c8-106">**Abbildung 1: Basiskonfiguration Test-/Umgebung**</span><span class="sxs-lookup"><span data-stu-id="c95c8-106">**Figure 1: The Base Configuration dev/test environment**</span></span>

![Phase 4 der Basiskonfiguration in Azure mit dem virtuellen Computer CLIENT1](images/25a010a6-c870-4690-b8f3-84421f8bc5c7.png)
  
<span data-ttu-id="c95c8-p101">Die Basiskonfiguration Test-/Umgebung in Abbildung 1 besteht aus dem Subnetz Corpnet in einer Cloud-only Azure-virtuelles Netzwerk mit dem Namen Testlabor, die simuliert eine vereinfachte, privaten Intranet mit dem Internet verbunden. Dieser Abschnitt enthält drei Azure-virtuelle Computer:</span><span class="sxs-lookup"><span data-stu-id="c95c8-p101">The Base Configuration dev/test environment in Figure 1 consists of the Corpnet subnet in a cloud-only Azure virtual network named TestLab that simulates a simplified, private intranet connected to the Internet. It contains three Azure virtual machines:</span></span>
  
- <span data-ttu-id="c95c8-110">DC1 ist als Intranet-Domänencontroller und DNS-Server (Domain Name System) konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="c95c8-110">DC1 is configured as an intranet domain controller and Domain Name System (DNS) server</span></span>
    
- <span data-ttu-id="c95c8-111">App1 ist als allgemeiner Anwendungs- und Webserver konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="c95c8-111">APP1 is configured as a general application and web server</span></span>
    
- <span data-ttu-id="c95c8-112">	CLIENT1 fungiert als Intranetclient.</span><span class="sxs-lookup"><span data-stu-id="c95c8-112">CLIENT1 acts as an intranet client</span></span>
    
<span data-ttu-id="c95c8-113">Diese Konfiguration ermöglicht DC1, APP1, CLIENT1 und weiteren Computern im Unternehmensnetzwerk-Subnetz Folgendes: </span><span class="sxs-lookup"><span data-stu-id="c95c8-113">This configuration allows DC1, APP1, CLIENT1, and additional Corpnet subnet computers to be:</span></span> 
  
- <span data-ttu-id="c95c8-114">Verbunden mit dem Internet Updates installiert, Zugriff auf Ressourcen im Internet in Echtzeit und öffentliche Cloud-Technologien wie Microsoft Office 365 und Azure-Diensten teilnehmen.</span><span class="sxs-lookup"><span data-stu-id="c95c8-114">Connected to the Internet to install updates, access Internet resources in real time, and participate in public cloud technologies such as Microsoft Office 365 and other Azure services.</span></span>
    
- <span data-ttu-id="c95c8-115">	Remoteverwaltung über Remotedesktopverbindungen von Ihrem Computer, der mit dem Internet oder dem Netzwerk Ihrer Organisation verbunden ist.</span><span class="sxs-lookup"><span data-stu-id="c95c8-115">Remotely managed using Remote Desktop connections from your computer that is connected to the Internet or your organization network.</span></span>
    
<span data-ttu-id="c95c8-116">Sie können die resultierende Testumgebung zu folgenden Zwecken verwenden:</span><span class="sxs-lookup"><span data-stu-id="c95c8-116">You can use the resulting test environment:</span></span>
  
- <span data-ttu-id="c95c8-117">Zur Anwendungsentwicklung und zum Testen.</span><span class="sxs-lookup"><span data-stu-id="c95c8-117">For application development and testing.</span></span>
    
- <span data-ttu-id="c95c8-118">Die Erstkonfiguration eigener Entwurf einer erweiterten Test-Umgebung umfasst, die zusätzlicher virtueller Computer, Azure-Diensten oder andere Microsoft-Cloud-Angeboten wie etwa Office 365 und Sicherheit in Unternehmen + Mobilität (zur Abstimmung).</span><span class="sxs-lookup"><span data-stu-id="c95c8-118">As the initial configuration of an extended test environment of your own design that includes additional virtual machines, Azure services, or other Microsoft cloud offerings such as Office 365 and Enterprise Security + Mobility (EMS).</span></span>
    
<span data-ttu-id="c95c8-119">Es gibt vier Phasen bei der Einrichtung der Basiskonfiguration für die Testumgebung in Azure:</span><span class="sxs-lookup"><span data-stu-id="c95c8-119">There are four phases to setting up the Base Configuration test environment in Azure:</span></span>
  
1. <span data-ttu-id="c95c8-120">	Erstellen des virtuellen Netzwerks</span><span class="sxs-lookup"><span data-stu-id="c95c8-120">Create the virtual network.</span></span>
    
2. <span data-ttu-id="c95c8-121">	Konfigurieren von DC1</span><span class="sxs-lookup"><span data-stu-id="c95c8-121">Configure DC1.</span></span>
    
3. <span data-ttu-id="c95c8-122">	Konfigurieren von APP1</span><span class="sxs-lookup"><span data-stu-id="c95c8-122">Configure APP1.</span></span>
    
4. <span data-ttu-id="c95c8-123">	Konfigurieren von CLIENT1</span><span class="sxs-lookup"><span data-stu-id="c95c8-123">Configure CLIENT1.</span></span>
    
<span data-ttu-id="c95c8-p102">Wenn Sie nicht bereits über ein Azure-Abonnement verfügen, können Sie sich für eine kostenlose Testversion auf [Azure testen](https://azure.microsoft.com/pricing/free-trial/)signieren. Wenn Sie ein MSDN oder Visual Studio-Abonnement haben, finden Sie unter [monatliche Azure Credit für Abonnenten von Visual Studio](https://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/).</span><span class="sxs-lookup"><span data-stu-id="c95c8-p102">If you do not already have an Azure subscription, you can sign up for a free trial at [Try Azure](https://azure.microsoft.com/pricing/free-trial/). If you have an MSDN or Visual Studio subscription, see [Monthly Azure credit for Visual Studio subscribers](https://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/).</span></span>
  
> [!NOTE]
> <span data-ttu-id="c95c8-p103">Virtuelle Computer in Azure ein einer laufenden Kosten entstehen, wenn sie ausgeführt werden. Diese Kosten für kostenlose Testversion, MSDN-Abonnement abgerechnet oder kostenpflichtiges Abonnement. Weitere Informationen zu den Kosten der Ausführung von Azure-virtuelle Computer finden Sie unter [Virtuelle Computer Preise Details](https://azure.microsoft.com/pricing/details/virtual-machines/) und [Azure Preise Rechner](https://azure.microsoft.com/pricing/calculator/). Um Kosten zu minimieren, finden Sie unter [Minimierung der Kosten für die Test Environment virtuellen Computern in Azure](base-configuration-dev-test-environment.md#mincost).</span><span class="sxs-lookup"><span data-stu-id="c95c8-p103">Virtual machines in Azure incur an ongoing monetary cost when they are running. This cost is billed against your free trial, MSDN subscription, or paid subscription. For more information about the costs of running Azure virtual machines, see [Virtual Machines Pricing Details](https://azure.microsoft.com/pricing/details/virtual-machines/) and [Azure Pricing Calculator](https://azure.microsoft.com/pricing/calculator/). To keep costs down, see [Minimizing the costs of test environment virtual machines in Azure](base-configuration-dev-test-environment.md#mincost).</span></span> 
  
![Testumgebungsanleitungen in der Microsoft Cloud](images/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
> [!TIP]
> <span data-ttu-id="c95c8-131">Klicken Sie [hier](http://aka.ms/catlgstack), um eine visuelle Darstellung aller Artikel im Stapel der Testumgebungsanleitungen in der Microsoft Cloud zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="c95c8-131">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-create-the-virtual-network"></a><span data-ttu-id="c95c8-132">Phase 1: Erstellen des virtuellen Netzwerks</span><span class="sxs-lookup"><span data-stu-id="c95c8-132">Phase 1: Create the virtual network</span></span>

<span data-ttu-id="c95c8-133">Starten Sie zunächst eine Azure PowerShell-Eingabeaufforderung.</span><span class="sxs-lookup"><span data-stu-id="c95c8-133">First, start an Azure PowerShell prompt.</span></span>
  
> [!NOTE]
> <span data-ttu-id="c95c8-p104">Verwenden Sie den folgenden Befehl wird die neueste Version von Azure PowerShell. Finden Sie unter [Erste Schritte mit Azure PowerShell-Cmdlets](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/).</span><span class="sxs-lookup"><span data-stu-id="c95c8-p104">The following command sets use the latest version of Azure PowerShell. See [Get started with Azure PowerShell cmdlets](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/).</span></span> 
  
<span data-ttu-id="c95c8-136">Melden Sie sich mit dem folgenden Befehl bei Ihrem Azure-Konto an.</span><span class="sxs-lookup"><span data-stu-id="c95c8-136">Sign in to your Azure account with the following command.</span></span>
  
```
Login-AzureRMAccount
```

> [!TIP]
> <span data-ttu-id="c95c8-137">Klicken Sie auf [hier](https://gallery.technet.microsoft.com/PowerShell-commands-for-ba957d3d) eine Textdatei ab, die PowerShell-Befehle in diesem Artikel enthält.</span><span class="sxs-lookup"><span data-stu-id="c95c8-137">Click [here](https://gallery.technet.microsoft.com/PowerShell-commands-for-ba957d3d) to get a text file that contains all the PowerShell commands in this article.</span></span>
  
<span data-ttu-id="c95c8-138">Rufen Sie den Namen Ihres Abonnements mithilfe des folgenden Befehls ab.</span><span class="sxs-lookup"><span data-stu-id="c95c8-138">Get your subscription name using the following command.</span></span>
  
```
Get-AzureRMSubscription | Sort Name | Select Name
```

<span data-ttu-id="c95c8-p105">Tragen Sie Ihr Azure-Abonnement ein. Ersetzen Sie alles innerhalb der Anführungszeichen, einschließlich der Zeichen „<“ und „>“, durch den entsprechenden Namen.</span><span class="sxs-lookup"><span data-stu-id="c95c8-p105">Set your Azure subscription. Replace everything within the quotes, including the < and > characters, with the correct name.</span></span>
  
```
$subscr="<subscription name>"
Get-AzureRmSubscription -SubscriptionName $subscr | Select-AzureRmSubscription
```

<span data-ttu-id="c95c8-p106">Im nächsten Schritt wird eine neue Ressourcengruppe für Ihre Basiskonfiguration des Testlabors erstellt. Verwenden Sie zum Ermitteln eines eindeutigen Ressourcengruppennamens diesen Befehl, mit dem die vorhandenen Ressourcengruppen aufgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="c95c8-p106">Next, create a new resource group for your Base Configuration test lab. To determine a unique resource group name, use this command to list your existing resource groups.</span></span>
  
```
Get-AzureRMResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

<span data-ttu-id="c95c8-p107">Erstellen Sie die neue Ressourcengruppe mit diesen Befehlen. Ersetzen Sie alles innerhalb der Anführungszeichen, einschließlich der Zeichen „<“ und „>“, durch die entsprechenden Namen.</span><span class="sxs-lookup"><span data-stu-id="c95c8-p107">Create your new resource group with these commands. Replace everything within the quotes, including the < and > characters, with the correct names.</span></span>
  
```
$rgName="<resource group name>"
$locName="<location name, such as West US>"
New-AzureRMResourceGroup -Name $rgName -Location $locName
```

<span data-ttu-id="c95c8-145">Im nächsten Schritt erstellen Sie das virtuelle Netzwerk „TestLab“, das das Unternehmensnetzwerk-Subnetz der Basiskonfiguration hostet, und schützen es mit einer Netzwerksicherheitsgruppe.</span><span class="sxs-lookup"><span data-stu-id="c95c8-145">Next, you create the TestLab virtual network that will host the Corpnet subnet of the base configuration and protect it with a network security group.</span></span>
  
```
$rgName="<name of your new resource group>"
$locName=(Get-AzureRmResourceGroup -Name $rgName).Location
$corpnetSubnet=New-AzureRMVirtualNetworkSubnetConfig -Name Corpnet -AddressPrefix 10.0.0.0/24
New-AzureRMVirtualNetwork -Name TestLab -ResourceGroupName $rgName -Location $locName -AddressPrefix 10.0.0.0/8 -Subnet $corpnetSubnet -DNSServer 10.0.0.4
$rule1=New-AzureRMNetworkSecurityRuleConfig -Name "RDPTraffic" -Description "Allow RDP to all VMs on the subnet" -Access Allow -Protocol Tcp -Direction Inbound -Priority 100 -SourceAddressPrefix Internet -SourcePortRange * -DestinationAddressPrefix * -DestinationPortRange 3389
New-AzureRMNetworkSecurityGroup -Name Corpnet -ResourceGroupName $rgName -Location $locName -SecurityRules $rule1
$vnet=Get-AzureRMVirtualNetwork -ResourceGroupName $rgName -Name TestLab
$nsg=Get-AzureRMNetworkSecurityGroup -Name Corpnet -ResourceGroupName $rgName
Set-AzureRMVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name Corpnet -AddressPrefix "10.0.0.0/24" -NetworkSecurityGroup $nsg
```

<span data-ttu-id="c95c8-146">Dies ist Ihre aktuelle Konfiguration.</span><span class="sxs-lookup"><span data-stu-id="c95c8-146">This is your current configuration.</span></span>
  
![Phase 1 der Basiskonfiguration in Azure mit dem virtuellen Netzwerk und Subnetz](images/0b5634fc-4e1c-469d-873d-97ed7e587411.png)
  
## <a name="phase-2-configure-dc1"></a><span data-ttu-id="c95c8-148">Phase 2: Konfigurieren von DC1</span><span class="sxs-lookup"><span data-stu-id="c95c8-148">Phase 2: Configure DC1</span></span>

<span data-ttu-id="c95c8-149">In dieser Phase erstellen Sie den virtuellen Computer DC1 und konfigurieren diesen als Domänencontroller für die Windows Server Active Directory-Domäne „corp.contoso.com“ sowie einen DNS-Server für die virtuellen Computer des virtuellen Netzwerks TestLab.</span><span class="sxs-lookup"><span data-stu-id="c95c8-149">In this phase, we create the DC1 virtual machine and configure it as a domain controller for the corp.contoso.com Windows Server Active Directory (AD) domain and a DNS server for the virtual machines of the TestLab virtual network.</span></span>
  
<span data-ttu-id="c95c8-150">Zum Erstellen eines Azure-virtueller Computers für DC1 Geben Sie den Namen der Ressourcengruppe, und führen Sie diese Befehle an der Azure PowerShell-Eingabeaufforderung auf dem lokalen Computer.</span><span class="sxs-lookup"><span data-stu-id="c95c8-150">To create an Azure virtual machine for DC1, fill in the name of your resource group and run these commands at the Azure PowerShell command prompt on your local computer.</span></span>
  
```
$rgName="<resource group name>"
$locName=(Get-AzureRmResourceGroup -Name $rgName).Location
$vnet=Get-AzureRMVirtualNetwork -Name TestLab -ResourceGroupName $rgName
$pip=New-AzureRMPublicIpAddress -Name DC1-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic=New-AzureRMNetworkInterface -Name DC1-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id -PrivateIpAddress 10.0.0.4
$vm=New-AzureRMVMConfig -VMName DC1 -VMSize Standard_A1
$cred=Get-Credential -Message "Type the name and password of the local administrator account for DC1."
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName DC1 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name "DC1-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "StandardLRS"
$diskConfig=New-AzureRmDiskConfig -AccountType "StandardLRS" -Location $locName -CreateOption Empty -DiskSizeGB 20
$dataDisk1=New-AzureRmDisk -DiskName "DC1-DataDisk1" -Disk $diskConfig -ResourceGroupName $rgName
$vm=Add-AzureRmVMDataDisk -VM $vm -Name "DC1-DataDisk1" -CreateOption Attach -ManagedDiskId $dataDisk1.Id -Lun 1
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

<span data-ttu-id="c95c8-p108">Sie werden nach einem Benutzernamen und Kennwort für das lokale Administratorkonto auf DC1 gefragt. Verwenden Sie ein sicheres Kennwort, und notieren Sie den Namen und das Kennwort an einem sicheren Ort.</span><span class="sxs-lookup"><span data-stu-id="c95c8-p108">You will be prompted for a user name and password for the local administrator account on DC1. Use a strong password and record both the name and password in a secure location.</span></span>
  
<span data-ttu-id="c95c8-153">Stellen Sie dann eine Verbindung mit dem virtuellen Computer DC1 her.</span><span class="sxs-lookup"><span data-stu-id="c95c8-153">Next, connect to the DC1 virtual machine.</span></span>
  
### <a name="connect-to-dc1-using-local-administrator-account-credentials"></a><span data-ttu-id="c95c8-154">Herstellen einer Verbindung mit DC1 mithilfe von Anmeldeinformationen für das lokale Administratorkonto</span><span class="sxs-lookup"><span data-stu-id="c95c8-154">Connect to DC1 using local administrator account credentials</span></span>

1. <span data-ttu-id="c95c8-155">Klicken Sie in der [Azure-Portal](https://portal.azure.com)auf **Ressourcengruppen >** [den Namen der neuen Ressourcengruppe] **> DC1 > Connect**.</span><span class="sxs-lookup"><span data-stu-id="c95c8-155">In the [Azure portal](https://portal.azure.com), click **Resource Groups >** [the name of your new resource group] **> DC1 > Connect**.</span></span>
    
2. <span data-ttu-id="c95c8-156">Öffnen Sie die DC1.rdp-Datei, die heruntergeladen wird, und klicken Sie auf **Verbinden**.</span><span class="sxs-lookup"><span data-stu-id="c95c8-156">Open the DC1.rdp file that is downloaded, and then click **Connect**.</span></span>
    
3. <span data-ttu-id="c95c8-157">Geben Sie den Namen des DC1 lokalen Administratorkontos:</span><span class="sxs-lookup"><span data-stu-id="c95c8-157">Specify the DC1 local administrator account name:</span></span>
    
  - <span data-ttu-id="c95c8-158">Für Windows 7:</span><span class="sxs-lookup"><span data-stu-id="c95c8-158">For Windows 7:</span></span>
    
    <span data-ttu-id="c95c8-p109">Klicken Sie auf **ein anderes Konto verwenden**, klicken Sie im Dialogfeld **Windows-Sicherheit** . Geben Sie im Feld **Benutzername** **DC1\\**[lokaler Administratorkontonamen].</span><span class="sxs-lookup"><span data-stu-id="c95c8-p109">In the **Windows Security** dialog box, click **Use another account**. In **User name**, type **DC1\\**[Local administrator account name].</span></span>
    
  - <span data-ttu-id="c95c8-161">Für Windows 8 oder Windows 10:</span><span class="sxs-lookup"><span data-stu-id="c95c8-161">For Windows 8 or Windows 10:</span></span>
    
    <span data-ttu-id="c95c8-p110">Klicken Sie auf **Weitere Optionen**, und klicken Sie dann auf **ein anderes Konto verwenden**, klicken Sie im Dialogfeld **Windows-Sicherheit** . Geben Sie im Feld **Benutzername** **DC1\\**[lokaler Administratorkontonamen].</span><span class="sxs-lookup"><span data-stu-id="c95c8-p110">In the **Windows Security** dialog box, click **More choices**, and then click **Use a different account**. In **User name**, type **DC1\\**[Local administrator account name].</span></span>
    
4. <span data-ttu-id="c95c8-164">Geben Sie im Feld **Kennwort**das Kennwort für das lokale Administratorkonto ein, und klicken Sie dann auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="c95c8-164">In **Password**, type the password of the local administrator account, and then click **OK**.</span></span>
    
5. <span data-ttu-id="c95c8-165">Wenn Sie aufgefordert werden, klicken Sie auf **Ja**.</span><span class="sxs-lookup"><span data-stu-id="c95c8-165">When prompted, click **Yes**.</span></span>
    
<span data-ttu-id="c95c8-166">Im nächsten Schritt fügen Sie eine zusätzliche Datenträger als ein neues Volume mit dem Laufwerkbuchstaben F: mit diesem Befehl an einer Administratorebene Windows PowerShell-Eingabeaufforderung auf DC1 hinzu.</span><span class="sxs-lookup"><span data-stu-id="c95c8-166">Next, add an extra data disk as a new volume with the drive letter F: with this command at an administrator-level Windows PowerShell command prompt on DC1.</span></span>
  
```
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

<span data-ttu-id="c95c8-p111">Konfigurieren Sie als Nächstes DC1 als Domänencontroller und DNS-Server für die Domäne „corp.contoso.com“. Führen Sie diese Befehle an einer Windows PowerShell-Eingabeaufforderung auf Administratorebene aus.</span><span class="sxs-lookup"><span data-stu-id="c95c8-p111">Next, configure DC1 as a domain controller and DNS server for the corp.contoso.com domain. Run these commands at an administrator-level Windows PowerShell command prompt.</span></span>
  
```
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSForest -DomainName corp.contoso.com -DatabasePath "F:\NTDS" -SysvolPath "F:\SYSVOL" -LogPath "F:\Logs"
```

<span data-ttu-id="c95c8-p112">Sie müssen ein Administratorkennwort für den abgesicherten Modus angeben. Bewahren Sie das Kennwort an einem sicheren Ort auf.</span><span class="sxs-lookup"><span data-stu-id="c95c8-p112">You will need to specify a safe mode administrator password. Store this password in a secure location.</span></span>
  
<span data-ttu-id="c95c8-171">Beachten Sie, dass der Abschluss dieser Befehle ein paar Minuten in Anspruch nehmen kann.</span><span class="sxs-lookup"><span data-stu-id="c95c8-171">Note that these commands can take a few minutes to complete.</span></span>
  
<span data-ttu-id="c95c8-172">Stellen Sie nach dem Neustart von DC1 wieder eine Verbindung zum virtuellen DC1-Computer her.</span><span class="sxs-lookup"><span data-stu-id="c95c8-172">After DC1 restarts, reconnect to the DC1 virtual machine.</span></span>
  
### <a name="connect-to-dc1-using-domain-credentials"></a><span data-ttu-id="c95c8-173">Herstellen einer Verbindung mit DC1 mithilfe von Domänenanmeldeinformationen</span><span class="sxs-lookup"><span data-stu-id="c95c8-173">Connect to DC1 using domain credentials</span></span>

1. <span data-ttu-id="c95c8-174">Klicken Sie in der [Azure-Portal](https://portal.azure.com)auf **Ressourcengruppen >** [Ihre Gruppe Ressourcenname] **> DC1 > Connect**.</span><span class="sxs-lookup"><span data-stu-id="c95c8-174">In the [Azure portal](https://portal.azure.com), click **Resource Groups >** [your resource group name] **> DC1 > Connect**.</span></span>
    
2. <span data-ttu-id="c95c8-175">Führen Sie die DC1.rdp-Datei, die heruntergeladen wird, und klicken Sie auf **Verbinden**.</span><span class="sxs-lookup"><span data-stu-id="c95c8-175">Run the DC1.rdp file that is downloaded, and then click **Connect**.</span></span>
    
3. <span data-ttu-id="c95c8-p113">Klicken Sie in der **Windows-Sicherheit**auf **ein anderes Konto verwenden**. Geben Sie im Feld **Benutzername** **CORP\\**[lokaler Administratorkontonamen].</span><span class="sxs-lookup"><span data-stu-id="c95c8-p113">In **Windows Security**, click **Use another account**. In **User name**, type **CORP\\**[Local administrator account name].</span></span>
    
4. <span data-ttu-id="c95c8-178">Geben Sie im Feld **Kennwort**das Kennwort für das lokale Administratorkonto ein, und klicken Sie dann auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="c95c8-178">In **Password**, type the password of the local administrator account, and then click **OK**.</span></span>
    
5. <span data-ttu-id="c95c8-179">Wenn Sie aufgefordert werden, klicken Sie auf **Ja**.</span><span class="sxs-lookup"><span data-stu-id="c95c8-179">When prompted, click **Yes**.</span></span>
    
<span data-ttu-id="c95c8-p114">Im nächsten Schritt erstellen Sie ein Benutzerkonto in Active Directory, das bei der Anmeldung an Mitgliedscomputern der Domäne CORP verwendet wird. Führen Sie diesen Befehl an einer Windows PowerShell-Eingabeaufforderung auf Administratorebene aus.</span><span class="sxs-lookup"><span data-stu-id="c95c8-p114">Next, create a user account in Active Directory that will be used when logging in to CORP domain member computers. Run this command at an administrator-level Windows PowerShell command prompt.</span></span>
  
```
New-ADUser -SamAccountName User1 -AccountPassword (read-host "Set user password" -assecurestring) -name "User1" -enabled $true -PasswordNeverExpires $true -ChangePasswordAtLogon $false
```

<span data-ttu-id="c95c8-p115">Beachten Sie, dass Sie von dem Befehl aufgefordert werden, das Kennwort des Kontos „User1“ anzugeben. Da dieses Konto für Remotedesktopverbindungen für alle Mitgliedscomputer der Domäne CORP verwendet wird, sollten Sie ein sicheres Kennwort wählen. Notieren Sie das Kennwort des Kontos „User1“, und bewahren Sie es an einem sicheren Ort auf.</span><span class="sxs-lookup"><span data-stu-id="c95c8-p115">Note that this command prompts you to supply the User1 account password. Because this account will be used for remote desktop connections for all CORP domain member computers, choose a strong password. Record the User1 account password and store it in a secured location.</span></span>
  
<span data-ttu-id="c95c8-p116">Konfigurieren Sie als Nächstes das neue Konto „User1“ als Unternehmensadministrator. Führen Sie diesen Befehl an der Windows PowerShell-Eingabeaufforderung auf Administratorebene aus.</span><span class="sxs-lookup"><span data-stu-id="c95c8-p116">Next, configure the new User1 account as an Enterprise Administrator. Run this command at the administrator-level Windows PowerShell command prompt.</span></span>
  
```
Add-ADPrincipalGroupMembership -Identity "CN=User1,CN=Users,DC=corp,DC=contoso,DC=com" -MemberOf "CN=Enterprise Admins,CN=Users,DC=corp,DC=contoso,DC=com","CN=Domain Admins,CN=Users,DC=corp,DC=contoso,DC=com","CN=Schema Admins,CN=Users,DC=corp,DC=contoso,DC=com"
```

<span data-ttu-id="c95c8-187">Schließen Sie die Remotedesktopsitzung mit DC1 und dann erneut eine Verbindung mit der CORP\\Konto User1 an.</span><span class="sxs-lookup"><span data-stu-id="c95c8-187">Close the Remote Desktop session with DC1 and then reconnect using the CORP\\User1 account.</span></span>
  
<span data-ttu-id="c95c8-188">Führen Sie als Nächstes den folgenden Befehl an einer Windows PowerShell-Eingabeaufforderung auf Administratorebene aus, um Datenverkehr für das Tool Ping zuzulassen.</span><span class="sxs-lookup"><span data-stu-id="c95c8-188">Next, to allow traffic for the Ping tool, run this command at an administrator-level Windows PowerShell command prompt.</span></span>
  
```
Set-NetFirewallRule -DisplayName "File and Printer Sharing (Echo Request - ICMPv4-In)" -enabled True
```

<span data-ttu-id="c95c8-189">Dies ist Ihre aktuelle Konfiguration.</span><span class="sxs-lookup"><span data-stu-id="c95c8-189">This is your current configuration.</span></span>
  
![Phase 2 der Basiskonfiguration in Azure mit dem virtuellen Computer DC1](images/49069908-29c3-4d73-87f7-debbea067261.png)
  
## <a name="phase-3-configure-app1"></a><span data-ttu-id="c95c8-191">Phase 3: Konfigurieren von APP1</span><span class="sxs-lookup"><span data-stu-id="c95c8-191">Phase 3: Configure APP1</span></span>

<span data-ttu-id="c95c8-192">APP1 bietet Web- und Dateifreigabedienste.</span><span class="sxs-lookup"><span data-stu-id="c95c8-192">APP1 provides web and file sharing services.</span></span>
  
<span data-ttu-id="c95c8-193">Zum Erstellen einer Azure Virtual Machine für APP1 Geben Sie den Namen der Ressourcengruppe, und führen Sie diese Befehle an der Azure PowerShell-Eingabeaufforderung auf dem lokalen Computer.</span><span class="sxs-lookup"><span data-stu-id="c95c8-193">To create an Azure Virtual Machine for APP1, fill in the name of your resource group and run these commands at the Azure PowerShell command prompt on your local computer.</span></span>
  
```
$rgName="<resource group name>"
$locName=(Get-AzureRmResourceGroup -Name $rgName).Location
$vnet=Get-AzureRMVirtualNetwork -Name TestLab -ResourceGroupName $rgName
$pip=New-AzureRMPublicIpAddress -Name APP1-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic=New-AzureRMNetworkInterface -Name APP1-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id
$vm=New-AzureRMVMConfig -VMName APP1 -VMSize Standard_A1
$cred=Get-Credential -Message "Type the name and password of the local administrator account for APP1."
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName APP1 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name "APP1-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "StandardLRS"
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

<span data-ttu-id="c95c8-194">Im nächsten Schritt stellen Sie eine Verbindung mit dem virtuellen Computer APP1 mit dem Kontonamen und Kennwort des lokalen Administratorkontos von APP1 her und öffnen dann eine Windows PowerShell-Eingabeaufforderung.</span><span class="sxs-lookup"><span data-stu-id="c95c8-194">Next, connect to the APP1 virtual machine using the APP1 local administrator account name and password, and then open a Windows PowerShell command prompt.</span></span>
  
<span data-ttu-id="c95c8-195">Zum Überprüfen der Namen Auflösung und Netzwerk-Kommunikation zwischen APP1 und DC1 führen Sie den Befehl **Ping dc1.corp.contoso.com** , und stellen Sie sicher, dass es vier Antworten gibt.</span><span class="sxs-lookup"><span data-stu-id="c95c8-195">To check name resolution and network communication between APP1 and DC1, run the **ping dc1.corp.contoso.com** command and verify that there are four replies.</span></span>
  
<span data-ttu-id="c95c8-196">Verknüpfen Sie als Nächstes unter Verwendung der folgenden Befehle an der Windows PowerShell-Eingabeaufforderung den virtuellen Computer APP1 mit der Domäne CORP.</span><span class="sxs-lookup"><span data-stu-id="c95c8-196">Next, join the APP1 virtual machine to the CORP domain with these commands at the Windows PowerShell prompt.</span></span>
  
```
Add-Computer -DomainName corp.contoso.com
Restart-Computer
```

<span data-ttu-id="c95c8-197">Beachten Sie, dass Sie die CORP angeben müssen\\User1 Domänenanmeldeinformationen Konto nach dem Ausführen des Befehls **Computer hinzufügen** .</span><span class="sxs-lookup"><span data-stu-id="c95c8-197">Note that you must supply the CORP\\User1 domain account credentials after running the **Add-Computer** command.</span></span>
  
<span data-ttu-id="c95c8-198">Nach dem Neustart APP1 Herstellen einer Verbindung mit der CORP mit\\Konto User1 an, und öffnen Sie dann eine Administratorebene Windows PowerShell command Prompt.</span><span class="sxs-lookup"><span data-stu-id="c95c8-198">After APP1 restarts, connect to it using the CORP\\User1 account, and then open an administrator-level Windows PowerShell command prompt.</span></span>
  
<span data-ttu-id="c95c8-199">Im nächsten Schritt richten Sie APP1 mit dem folgenden Befehl in der Windows PowerShell-Eingabeaufforderung auf APP1 als Webserver ein.</span><span class="sxs-lookup"><span data-stu-id="c95c8-199">Next, make APP1 a web server with this command at the Windows PowerShell command prompt on APP1.</span></span>
  
```
Install-WindowsFeature Web-WebServer -IncludeManagementTools
```

<span data-ttu-id="c95c8-200">Erstellen Sie als Nächstes einen freigegebenen Ordner und eine Textdatei innerhalb des Ordners auf APP1 mit diesen PowerShell-Befehlen.</span><span class="sxs-lookup"><span data-stu-id="c95c8-200">Next, create a shared folder and a text file within the folder on APP1 with these PowerShell commands.</span></span>
  
```
New-Item -path c:\files -type directory
Write-Output "This is a shared file." | out-file c:\files\example.txt
New-SmbShare -name files -path c:\files -changeaccess CORP\User1
```

<span data-ttu-id="c95c8-201">Dies ist Ihre aktuelle Konfiguration.</span><span class="sxs-lookup"><span data-stu-id="c95c8-201">This is your current configuration.</span></span>
  
![Phase 3 der Basiskonfiguration in Azure mit dem virtuellen Computer APP1](images/92cfabb0-7f9d-4291-964d-ac32d52748d7.png)
  
## <a name="phase-4-configure-client1"></a><span data-ttu-id="c95c8-203">Phase 4: Konfigurieren von CLIENT1</span><span class="sxs-lookup"><span data-stu-id="c95c8-203">Phase 4: Configure CLIENT1</span></span>

<span data-ttu-id="c95c8-204">CLIENT1 fungiert als normaler Laptop-, Tablet- oder Desktopcomputer im Intranet von Contoso.</span><span class="sxs-lookup"><span data-stu-id="c95c8-204">CLIENT1 acts as a typical laptop, tablet, or desktop computer on the Contoso intranet.</span></span>
  
<span data-ttu-id="c95c8-205">Um eine Azure Virtual Machine für CLIENT1 zu erstellen, geben Sie den Namen der Ressourcengruppe und führen Sie diese Befehle an der Azure PowerShell-Eingabeaufforderung auf dem lokalen Computer.</span><span class="sxs-lookup"><span data-stu-id="c95c8-205">To create an Azure Virtual Machine for CLIENT1, fill in the name of your resource group and run these commands at the Azure PowerShell command prompt on your local computer.</span></span>
  
```
$rgName="<resource group name>"
$locName=(Get-AzureRmResourceGroup -Name $rgName).Location
$vnet=Get-AzureRMVirtualNetwork -Name TestLab -ResourceGroupName $rgName
$pip=New-AzureRMPublicIpAddress -Name CLIENT1-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic=New-AzureRMNetworkInterface -Name CLIENT1-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id
$vm=New-AzureRMVMConfig -VMName CLIENT1 -VMSize Standard_A1
$cred=Get-Credential -Message "Type the name and password of the local administrator account for CLIENT1."
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName CLIENT1 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsDesktop -Offer Windows-10 -Skus RS3-Pro -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name "CLIENT1-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "StandardLRS"
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

<span data-ttu-id="c95c8-206">Im nächsten Schritt stellen Sie eine Verbindung mit dem virtuellen Computer CLIENT1 mit dem Kontonamen und Kennwort des lokalen Administratorkontos von CLIENT1 her und öffnen dann eine Windows PowerShell-Eingabeaufforderung auf Administratorebene.</span><span class="sxs-lookup"><span data-stu-id="c95c8-206">Next, connect to the CLIENT1 virtual machine using the CLIENT1 local administrator account name and password, and then open an administrator-level Windows PowerShell command prompt.</span></span>
  
<span data-ttu-id="c95c8-207">Zum Überprüfen der Namen Auflösung und Netzwerk-Kommunikation zwischen CLIENT1 und DC1 führen Sie den Befehl **Ping dc1.corp.contoso.com** an einer Windows PowerShell-Eingabeaufforderung, und stellen Sie sicher, dass es vier Antworten gibt.</span><span class="sxs-lookup"><span data-stu-id="c95c8-207">To check name resolution and network communication between CLIENT1 and DC1, run the **ping dc1.corp.contoso.com** command at a Windows PowerShell command prompt and verify that there are four replies.</span></span>
  
<span data-ttu-id="c95c8-208">Verknüpfen Sie als Nächstes unter Verwendung der folgenden Befehle an der Windows PowerShell-Eingabeaufforderung den virtuellen Computer CLIENT1 mit der Domäne CORP.</span><span class="sxs-lookup"><span data-stu-id="c95c8-208">Next, join the CLIENT1 virtual machine to the CORP domain with these commands at the Windows PowerShell prompt.</span></span>
  
```
Add-Computer -DomainName corp.contoso.com
Restart-Computer
```

<span data-ttu-id="c95c8-209">Beachten Sie, dass Sie Ihre CORP angeben müssen\\User1 Domänenanmeldeinformationen Konto nach dem Ausführen des Befehls **Computer hinzufügen** .</span><span class="sxs-lookup"><span data-stu-id="c95c8-209">Note that you must supply your CORP\\User1 domain account credentials after running the **Add-Computer** command.</span></span>
  
<span data-ttu-id="c95c8-210">Nach dem Neustart CLIENT1 Herstellen einer Verbindung mit der CORP mit\\User1 Kontoname und Kennwort, und öffnen Sie eine Windows PowerShell-Eingabeaufforderung auf Administratorebene.</span><span class="sxs-lookup"><span data-stu-id="c95c8-210">After CLIENT1 restarts, connect to it using the CORP\\User1 account name and password, and then open an administrator-level Windows PowerShell command prompt.</span></span>
  
<span data-ttu-id="c95c8-211">Überprüfen Sie im nächsten Schritt, ob Sie von CLIENT1 aus auf Web- und Dateifreigaberessourcen auf APP1 zugreifen können.</span><span class="sxs-lookup"><span data-stu-id="c95c8-211">Next, verify that you can access web and file share resources on APP1 from CLIENT1.</span></span>
  
### <a name="verify-client-access-to-app1"></a><span data-ttu-id="c95c8-212">Überprüfen des Clientzugriffs auf APP1</span><span class="sxs-lookup"><span data-stu-id="c95c8-212">Verify CLIENT access to APP1</span></span>

1. <span data-ttu-id="c95c8-213">Klicken Sie im Server-Manager im Strukturbereich auf **Lokalen Server**.</span><span class="sxs-lookup"><span data-stu-id="c95c8-213">In Server Manager, in the tree pane, click **Local Server**.</span></span>
    
2. <span data-ttu-id="c95c8-214">Klicken Sie in den **Eigenschaften für CLIENT1** **auf** neben **Verstärkte Sicherheitskonfiguration für Internet Explorer**.</span><span class="sxs-lookup"><span data-stu-id="c95c8-214">In **Properties for CLIENT1**, click **On** next to **IE Enhanced Security Configuration**.</span></span>
    
3. <span data-ttu-id="c95c8-215">Klicken Sie in **Verstärkte Sicherheitskonfiguration für Internet Explorer**auf **aus** für **Administratoren** und **Benutzern**, und klicken Sie dann auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="c95c8-215">In **Internet Explorer Enhanced Security Configuration**, click **Off** for **Administrators** and **Users**, and then click **OK**.</span></span>
    
4. <span data-ttu-id="c95c8-216">Klicken Sie auf der Startseite auf **Internet Explorer**, und klicken Sie dann auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="c95c8-216">From the Start screen, click **Internet Explorer**, and then click **OK**.</span></span>
    
5. <span data-ttu-id="c95c8-p117">Geben Sie in der Adressleiste **http://app1.corp.contoso.com/**, und drücken Sie dann die EINGABETASTE. Sie sollten die standardmäßige Internet-Informationsdienste Webseite APP1 finden Sie unter.</span><span class="sxs-lookup"><span data-stu-id="c95c8-p117">In the Address bar, type **http://app1.corp.contoso.com/**, and then press ENTER. You should see the default Internet Information Services web page for APP1.</span></span>
    
6. <span data-ttu-id="c95c8-219">Klicken Sie auf der Desktop-Taskleiste auf das Symbol für den Datei-Explorer.</span><span class="sxs-lookup"><span data-stu-id="c95c8-219">From the desktop taskbar, click the File Explorer icon.</span></span>
    
7. <span data-ttu-id="c95c8-p118">Geben Sie in der Adressleiste ** \\ \\app1\\Dateien**, und drücken Sie dann die EINGABETASTE. Eine Ordneransicht mit dem Inhalt des freigegebenen Ordners sollte angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="c95c8-p118">In the address bar, type **\\\\app1\\Files**, and then press ENTER. You should see a folder window with the contents of the Files shared folder.</span></span>
    
8. <span data-ttu-id="c95c8-p119">Klicken Sie im freigegebenen Ordner **Dateien** Doppelklicken Sie auf die Datei **Example.txt** . Der Inhalt der Datei Example.txt sollte angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="c95c8-p119">In the **Files** shared folder window, double-click the **Example.txt** file. You should see the contents of the Example.txt file.</span></span>
    
9. <span data-ttu-id="c95c8-224">Schließen Sie die **example.txt - Editor** und die **Dateien** freigegebene Ordner Windows.</span><span class="sxs-lookup"><span data-stu-id="c95c8-224">Close the **example.txt - Notepad** and the **Files** shared folder windows.</span></span>
    
<span data-ttu-id="c95c8-225">Dies ist Ihre endgültige Konfiguration.</span><span class="sxs-lookup"><span data-stu-id="c95c8-225">This is your final configuration.</span></span>
  
![Phase 4 der Basiskonfiguration in Azure mit dem virtuellen Computer CLIENT1](images/25a010a6-c870-4690-b8f3-84421f8bc5c7.png)
  
<span data-ttu-id="c95c8-227">Die Basiskonfiguration in Azure kann nun für die Anwendungsentwicklung und zum Testen oder für die Erstellung zusätzlicher Testumgebungen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="c95c8-227">Your Base Configuration in Azure is now ready for application development and testing or for building additional test environments.</span></span> 
  
> [!TIP]
> <span data-ttu-id="c95c8-228">Klicken Sie [hier](http://aka.ms/catlgstack), um eine visuelle Darstellung aller Artikel im Stapel der Testumgebungsanleitungen in der Microsoft Cloud zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="c95c8-228">Click [here](http://aka.ms/catlgstack) for a visual map to all of the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
<span data-ttu-id="c95c8-229"><a name="mincost"> </a></span><span class="sxs-lookup"><span data-stu-id="c95c8-229"></span></span>
## <a name="minimizing-the-costs-of-test-environment-virtual-machines-in-azure"></a><span data-ttu-id="c95c8-230">Minimierung der Kosten für virtuelle Computer der Testumgebung in Azure</span><span class="sxs-lookup"><span data-stu-id="c95c8-230">Minimizing the costs of test environment virtual machines in Azure</span></span>

<span data-ttu-id="c95c8-231">Um die Kosten für die Ausführung der virtuellen Computer der Testumgebung zu minimieren, können Sie eine der folgenden Aktionen ausführen:</span><span class="sxs-lookup"><span data-stu-id="c95c8-231">To minimize the cost of running the test environment virtual machines, you can do one of the following:</span></span>
  
- <span data-ttu-id="c95c8-p120">Erstellen Sie die Testumgebung, und führen Sie Ihre benötigten Tests und Demonstrationen so schnell wie möglich aus. Nach Abschluss des Vorgangs löschen Sie die Ressourcengruppe für die Testumgebung.</span><span class="sxs-lookup"><span data-stu-id="c95c8-p120">Create the test environment and perform your needed testing and demonstration as quickly as possible. When complete, delete the resource group for the test environment.</span></span>
    
- <span data-ttu-id="c95c8-234">	Fahren Sie die virtuellen Computer der Testumgebung in den Zustand der aufgehobenen Zuordnung herunter.</span><span class="sxs-lookup"><span data-stu-id="c95c8-234">Shut down your test environment virtual machines into a deallocated state.</span></span>
    
<span data-ttu-id="c95c8-235">Um die virtuellen Computer mit Azure PowerShell herunterzufahren, geben Sie den Ressourcengruppennamen ein und führen die folgenden Befehle aus.</span><span class="sxs-lookup"><span data-stu-id="c95c8-235">To shut down the virtual machines with Azure PowerShell, fill in the resource group name and run these commands.</span></span>
  
```
$rgName="<your resource group name>"
Stop-AzureRMVM -ResourceGroupName $rgName -Name "CLIENT1" -Force
Stop-AzureRMVM -ResourceGroupName $rgName -Name "APP1" -Force
Stop-AzureRMVM -ResourceGroupName $rgName -Name "DC1" -Force
```

<span data-ttu-id="c95c8-236">Damit Ihre virtuellen Computer einwandfrei funktionieren, wenn alle aus dem beendeten Zustand (Zuordnung aufgehoben) gestartet werden, sollten Sie sie in der folgenden Reihenfolge starten:</span><span class="sxs-lookup"><span data-stu-id="c95c8-236">To ensure that your virtual machines work properly when starting all of them from the Stopped (Deallocated) state, you should start them in the following order:</span></span>
  
1. <span data-ttu-id="c95c8-237">DC1</span><span class="sxs-lookup"><span data-stu-id="c95c8-237">DC1</span></span>
2. <span data-ttu-id="c95c8-238">APP1</span><span class="sxs-lookup"><span data-stu-id="c95c8-238">APP1</span></span>
3. <span data-ttu-id="c95c8-239">CLIENT1</span><span class="sxs-lookup"><span data-stu-id="c95c8-239">CLIENT1</span></span>
    
<span data-ttu-id="c95c8-240">Um die virtuellen Computer in der richtigen Reihenfolge mit Azure PowerShell zu starten, geben Sie den Ressourcengruppennamen ein und führen die folgenden Befehle aus.</span><span class="sxs-lookup"><span data-stu-id="c95c8-240">To start the virtual machines in order with Azure PowerShell, fill in the resource group name and run these commands.</span></span>
  
```
$rgName="<your resource group name>"
Start-AzureRMVM -ResourceGroupName $rgName -Name "DC1"
Start-AzureRMVM -ResourceGroupName $rgName -Name "APP1"
Start-AzureRMVM -ResourceGroupName $rgName -Name "CLIENT1"
```

## <a name="see-also"></a><span data-ttu-id="c95c8-241">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="c95c8-241">See Also</span></span>

- [<span data-ttu-id="c95c8-242">Office 365-Entwicklungs-/Testumgebung</span><span class="sxs-lookup"><span data-stu-id="c95c8-242">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
- [<span data-ttu-id="c95c8-243">DirSync für die Office 365-Entwicklungs-/Testumgebung</span><span class="sxs-lookup"><span data-stu-id="c95c8-243">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)
- [<span data-ttu-id="c95c8-244">Cloud App Security für Ihre Office 365-Entwicklungs-/Testumgebung</span><span class="sxs-lookup"><span data-stu-id="c95c8-244">Cloud App Security for your Office 365 dev/test environment</span></span>](cloud-app-security-for-your-office-365-dev-test-environment.md)
- [<span data-ttu-id="c95c8-245">Advanced Threat Protection für die Office 365-Entwicklungs-/Testumgebung</span><span class="sxs-lookup"><span data-stu-id="c95c8-245">Advanced Threat Protection for your Office 365 dev/test environment</span></span>](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
- [<span data-ttu-id="c95c8-246">Cloudakzeptanz und Hybridlösungen</span><span class="sxs-lookup"><span data-stu-id="c95c8-246">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)
