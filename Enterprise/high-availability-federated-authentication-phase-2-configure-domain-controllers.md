---
title: "Hoher Verfügbarkeit federated Authentifizierung Phase 2 Konfigurieren von Domänencontrollern"
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
ms.assetid: 6b0eff4c-2c5e-4581-8393-a36f7b36a72f
description: "Zusammenfassung: Konfigurieren der Domänencontroller und Dirsync-Server für die hohe Verfügbarkeit Verbundauthentifizierung für Office 365 in Microsoft Azure."
ms.openlocfilehash: 609d282321296be79c20c451cca12ccf46fe036d
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/11/2018
---
# <a name="high-availability-federated-authentication-phase-2-configure-domain-controllers"></a><span data-ttu-id="185b6-103">Hochverfügbarkeit der Verbundauthentifizierung, Phase 2: Konfigurieren von Domänencontrollern</span><span class="sxs-lookup"><span data-stu-id="185b6-103">High availability federated authentication Phase 2: Configure domain controllers</span></span>

 <span data-ttu-id="185b6-104">**Zusammenfassung:** Konfigurieren Sie die Domänencontroller und Dirsync-Server für die hohe Verfügbarkeit Verbundauthentifizierung für Office 365 in Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="185b6-104">**Summary:** Configure the domain controllers and DirSync server for your high availability federated authentication for Office 365 in Microsoft Azure.</span></span>
  
<span data-ttu-id="185b6-p101">In dieser Phase der Bereitstellung einer hohen Verfügbarkeit für die Office 365-Verbundauthentifizierung in den Azure-Infrastrukturdiensten konfigurieren Sie die beiden Domänencontroller und den DirSync-Server im virtuellen Azure-Netzwerk. Clientwebanforderungen für die Authentifizierung können dann im virtuellen Azure-Netzwerk authentifiziert werden, anstatt diesen Authentifizierungsverkehr über das VPN zwischen Standorten an Ihr lokales Netzwerk zu senden.</span><span class="sxs-lookup"><span data-stu-id="185b6-p101">In this phase of deploying high availability for Office 365 federated authentication in Azure infrastructure services, you configure two domain controllers and the DirSync server in the Azure virtual network. Client web requests for authentication can then be authenticated in the Azure virtual network, rather than sending that authentication traffic across the site-to-site VPN connection to your on-premises network.</span></span>
  
> [!NOTE]
> <span data-ttu-id="185b6-107">Active Directory Federation Services (AD FS) kann Azure Active Directory-Domänendienste nicht als Ersatz für Windows Server Active Directory-Domänencontroller verwenden.</span><span class="sxs-lookup"><span data-stu-id="185b6-107">Active Directory Federation Services (AD FS) cannot use Azure Active Directory Domain Services as a substitute for Windows Server AD domain controllers.</span></span> 
  
<span data-ttu-id="185b6-p102">Sie müssen vor dem Verschieben auf in dieser Phase ausführen [hoher Verfügbarkeit federated Authentifizierung Phase 3: Konfigurieren von AD FS-Servern](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md). Finden Sie unter [Deploy hohe Verfügbarkeit Verbundauthentifizierung für Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) für alle Phasen.</span><span class="sxs-lookup"><span data-stu-id="185b6-p102">You must complete this phase before moving on to [High availability federated authentication Phase 3: Configure AD FS servers](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md). See [Deploy high availability federated authentication for Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) for all of the phases.</span></span>
  
## <a name="create-the-domain-controller-virtual-machines-in-azure"></a><span data-ttu-id="185b6-110">Erstellen der Domänencontroller der virtuellen Computer in Azure</span><span class="sxs-lookup"><span data-stu-id="185b6-110">Create the domain controller virtual machines in Azure</span></span>

<span data-ttu-id="185b6-111">Zunächst müssen Sie der **Name des virtuellen Computers** -Spalte der Tabelle M ausfüllen und Größen virtueller Computer in der Spalte **Mindestgröße** Bedarf zu ändern.</span><span class="sxs-lookup"><span data-stu-id="185b6-111">First, you need to fill out the **Virtual machine name** column of Table M and modify virtual machine sizes as needed in the **Minimum size** column.</span></span>
  
|<span data-ttu-id="185b6-112">**Element**</span><span class="sxs-lookup"><span data-stu-id="185b6-112">**Item**</span></span>|<span data-ttu-id="185b6-113">**Name des virtuellen Computers**</span><span class="sxs-lookup"><span data-stu-id="185b6-113">**Virtual machine name**</span></span>|<span data-ttu-id="185b6-114">**Bild aus der Galerie**</span><span class="sxs-lookup"><span data-stu-id="185b6-114">**Gallery image**</span></span>|<span data-ttu-id="185b6-115">**Speichertyp**</span><span class="sxs-lookup"><span data-stu-id="185b6-115">**Storage type**</span></span>|<span data-ttu-id="185b6-116">**Mindestgröße**</span><span class="sxs-lookup"><span data-stu-id="185b6-116">**Minimum size**</span></span>|
|:-----|:-----|:-----|:-----|:-----|
|<span data-ttu-id="185b6-117">1.</span><span class="sxs-lookup"><span data-stu-id="185b6-117">1.</span></span>  <br/> |<span data-ttu-id="185b6-118">______________ (erster Domänencontroller, Beispiel DC1)</span><span class="sxs-lookup"><span data-stu-id="185b6-118">______________ (first domain controller, example DC1)</span></span>  <br/> |<span data-ttu-id="185b6-119">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="185b6-119">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="185b6-120">StandardLRS</span><span class="sxs-lookup"><span data-stu-id="185b6-120">StandardLRS</span></span>  <br/> |<span data-ttu-id="185b6-121">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="185b6-121">Standard_D2</span></span>  <br/> |
|<span data-ttu-id="185b6-122">2.</span><span class="sxs-lookup"><span data-stu-id="185b6-122">2.</span></span>  <br/> |<span data-ttu-id="185b6-123">______________ (zweiter Domänencontroller, Beispiel DC2)</span><span class="sxs-lookup"><span data-stu-id="185b6-123">______________ (second domain controller, example DC2)</span></span>  <br/> |<span data-ttu-id="185b6-124">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="185b6-124">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="185b6-125">StandardLRS</span><span class="sxs-lookup"><span data-stu-id="185b6-125">StandardLRS</span></span>  <br/> |<span data-ttu-id="185b6-126">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="185b6-126">Standard_D2</span></span>  <br/> |
|<span data-ttu-id="185b6-127">3.</span><span class="sxs-lookup"><span data-stu-id="185b6-127">3.</span></span>  <br/> |<span data-ttu-id="185b6-128">___ (DirSync-Server, Beispiel DS1)</span><span class="sxs-lookup"><span data-stu-id="185b6-128">______________ (DirSync server, example DS1)</span></span>  <br/> |<span data-ttu-id="185b6-129">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="185b6-129">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="185b6-130">StandardLRS</span><span class="sxs-lookup"><span data-stu-id="185b6-130">StandardLRS</span></span>  <br/> |<span data-ttu-id="185b6-131">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="185b6-131">Standard_D2</span></span>  <br/> |
|<span data-ttu-id="185b6-132">4.</span><span class="sxs-lookup"><span data-stu-id="185b6-132">4.</span></span>  <br/> |<span data-ttu-id="185b6-133">___ (erster AD FS-Server, Beispiel ADFS1)</span><span class="sxs-lookup"><span data-stu-id="185b6-133">______________ (first AD FS server, example ADFS1)</span></span>  <br/> |<span data-ttu-id="185b6-134">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="185b6-134">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="185b6-135">StandardLRS</span><span class="sxs-lookup"><span data-stu-id="185b6-135">StandardLRS</span></span>  <br/> |<span data-ttu-id="185b6-136">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="185b6-136">Standard_D2</span></span>  <br/> |
|<span data-ttu-id="185b6-137">5.</span><span class="sxs-lookup"><span data-stu-id="185b6-137">5.</span></span>  <br/> |<span data-ttu-id="185b6-138">___ (zweiter AD FS-Server, Beispiel ADFS2)</span><span class="sxs-lookup"><span data-stu-id="185b6-138">______________ (second AD FS server, example ADFS2)</span></span>  <br/> |<span data-ttu-id="185b6-139">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="185b6-139">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="185b6-140">StandardLRS</span><span class="sxs-lookup"><span data-stu-id="185b6-140">StandardLRS</span></span>  <br/> |<span data-ttu-id="185b6-141">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="185b6-141">Standard_D2</span></span>  <br/> |
|<span data-ttu-id="185b6-142">6.</span><span class="sxs-lookup"><span data-stu-id="185b6-142">6.</span></span>  <br/> |<span data-ttu-id="185b6-143">______________ (erster Webanwendungsproxy-Server, Beispiel WEB1)</span><span class="sxs-lookup"><span data-stu-id="185b6-143">______________ (first web application proxy server, example WEB1)</span></span>  <br/> |<span data-ttu-id="185b6-144">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="185b6-144">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="185b6-145">StandardLRS</span><span class="sxs-lookup"><span data-stu-id="185b6-145">StandardLRS</span></span>  <br/> |<span data-ttu-id="185b6-146">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="185b6-146">Standard_D2</span></span>  <br/> |
|<span data-ttu-id="185b6-147">7.</span><span class="sxs-lookup"><span data-stu-id="185b6-147">7.</span></span>  <br/> |<span data-ttu-id="185b6-148">______________ (zweiter Webanwendungsproxy-Server, Beispiel WEB2)</span><span class="sxs-lookup"><span data-stu-id="185b6-148">______________ (second web application proxy server, example WEB2)</span></span>  <br/> |<span data-ttu-id="185b6-149">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="185b6-149">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="185b6-150">StandardLRS</span><span class="sxs-lookup"><span data-stu-id="185b6-150">StandardLRS</span></span>  <br/> |<span data-ttu-id="185b6-151">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="185b6-151">Standard_D2</span></span>  <br/> |
   
 <span data-ttu-id="185b6-152">**Tabelle M - virtueller Computer für die hohe Verfügbarkeit Verbundauthentifizierung für Office 365 in Azure**</span><span class="sxs-lookup"><span data-stu-id="185b6-152">**Table M - Virtual machines for the high availability federated authentication for Office 365 in Azure**</span></span>
  
<span data-ttu-id="185b6-153">Die vollständige Liste der Größen virtueller Computer finden Sie unter [Größen für virtuelle Computer](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-sizes).</span><span class="sxs-lookup"><span data-stu-id="185b6-153">For the complete list of virtual machine sizes, see [Sizes for virtual machines](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-sizes).</span></span>
  
<span data-ttu-id="185b6-p103">Der folgende Azure PowerShell-Befehlsblock erstellt die virtuellen Computer für die beiden Domänencontroller. Geben Sie die Werte für die Variablen, entfernen die \< und > Zeichen. Beachten Sie, dass dieser Befehl-Block von Azure PowerShell Werte aus den folgenden Tabellen verwendet wird:</span><span class="sxs-lookup"><span data-stu-id="185b6-p103">The following Azure PowerShell command block creates the virtual machines for the two domain controllers. Specify the values for the variables, removing the \< and > characters. Note that this Azure PowerShell command block uses values from the following tables:</span></span>
  
- <span data-ttu-id="185b6-157">Tabelle M (für die virtuellen Computer)</span><span class="sxs-lookup"><span data-stu-id="185b6-157">Table M, for your virtual machines</span></span>
    
- <span data-ttu-id="185b6-158">Tabelle R (für die Ressourcengruppen)</span><span class="sxs-lookup"><span data-stu-id="185b6-158">Table R, for your resource groups</span></span>
    
- <span data-ttu-id="185b6-159">Tabelle V (für die Einstellungen des virtuellen Netzwerks)</span><span class="sxs-lookup"><span data-stu-id="185b6-159">Table V, for your virtual network settings</span></span>
    
- <span data-ttu-id="185b6-160">Tabelle S (für das Subnetz)</span><span class="sxs-lookup"><span data-stu-id="185b6-160">Table S, for your subnets</span></span>
    
- <span data-ttu-id="185b6-161">Tabelle I (für die statischen IP-Adressen)</span><span class="sxs-lookup"><span data-stu-id="185b6-161">Table I, for your static IP addresses</span></span>
    
- <span data-ttu-id="185b6-162">Tabelle A (für die Verfügbarkeitsgruppen)</span><span class="sxs-lookup"><span data-stu-id="185b6-162">Table A, for your availability sets</span></span>
    
<span data-ttu-id="185b6-163">Denken Sie daran, dass Sie definierten Tabellen R, V, S, ich und in eine [hoher Verfügbarkeit federated Authentifizierung Phase 1: Konfigurieren von Azure](high-availability-federated-authentication-phase-1-configure-azure.md).</span><span class="sxs-lookup"><span data-stu-id="185b6-163">Recall that you defined Tables R, V, S, I, and A in [High availability federated authentication Phase 1: Configure Azure](high-availability-federated-authentication-phase-1-configure-azure.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="185b6-p104">Verwenden Sie den folgenden Befehl wird die neueste Version von Azure PowerShell. Finden Sie unter [Erste Schritte mit Azure PowerShell-Cmdlets](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/).</span><span class="sxs-lookup"><span data-stu-id="185b6-p104">The following command sets use the latest version of Azure PowerShell. See [Get started with Azure PowerShell cmdlets](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/).</span></span> 
  
<span data-ttu-id="185b6-166">Sobald Sie alle Werte korrekt festgelegt haben, führen Sie den resultierenden Block über die Azure PowerShell-Eingabeaufforderung oder in PowerShell ISE (Integrated Script Environment) auf Ihrem lokalen Computer aus.</span><span class="sxs-lookup"><span data-stu-id="185b6-166">When you have supplied all the correct values, run the resulting block at the Azure PowerShell prompt or in the PowerShell Integrated Script Environment (ISE) on your local computer.</span></span>
  
> [!TIP]
> <span data-ttu-id="185b6-167">Eine Textdatei, die alle von PowerShell-Befehlen in diesem Artikel und Konfiguration Microsoft Excel-Arbeitsmappen, die generiert Ready-und-Los-PowerShell-Befehl Blöcke basierend auf Ihrer benutzerdefinierten Einstellungen enthält, finden Sie unter der [Federated-Authentifizierung für Office 365 in Azure Deployment Kit](https://gallery.technet.microsoft.com/Federated-Authentication-8a9f1664).</span><span class="sxs-lookup"><span data-stu-id="185b6-167">For a text file that contains all of the PowerShell commands in this article and a Microsoft Excel configuration workbook that generates ready-to-run PowerShell command blocks based on your custom settings, see the [Federated Authentication for Office 365 in Azure Deployment Kit](https://gallery.technet.microsoft.com/Federated-Authentication-8a9f1664).</span></span> 
  
```
# Set up variables common to both virtual machines
$locName="<your Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$subnetName="<Table S - Item 1 - Value column>"
$avName="<Table A - Item 1 - Availability set name column>"
$rgNameTier="<Table R - Item 1 - Resource group name column>"
$rgNameInfra="<Table R - Item 4 - Resource group name column>"

$rgName=$rgNameInfra
$vnet=Get-AzureRMVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
$subnet=Get-AzureRmVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnetName

$rgName=$rgNameTier
$avSet=Get-AzureRMAvailabilitySet -Name $avName -ResourceGroupName $rgName 

# Create the first domain controller
$vmName="<Table M - Item 1 - Virtual machine name column>"
$vmSize="<Table M - Item 1 - Minimum size column>"
$staticIP="<Table I - Item 1 - Value column>"
$diskStorageType="<Table M - Item 1 - Storage type column>"
$diskSize=<size of the extra disk for Windows Server AD data in GB>

$nic=New-AzureRMNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName -Subnet $subnet -PrivateIpAddress $staticIP
$vm=New-AzureRMVMConfig -VMName $vmName -VMSize $vmSize -AvailabilitySetId $avset.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
$diskConfig=New-AzureRmDiskConfig -AccountType $diskStorageType -Location $locName -CreateOption Empty -DiskSizeGB $diskSize
$dataDisk1=New-AzureRmDisk -DiskName ($vmName + "-DataDisk1") -Disk $diskConfig -ResourceGroupName $rgName
$vm=Add-AzureRmVMDataDisk -VM $vm -Name ($vmName + "-DataDisk1") -CreateOption Attach -ManagedDiskId $dataDisk1.Id -Lun 1
$cred=Get-Credential -Message "Type the name and password of the local administrator account for the first domain controller." 
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm

# Create the second domain controller
$vmName="<Table M - Item 2 - Virtual machine name column>"
$vmSize="<Table M - Item 2 - Minimum size column>"
$staticIP="<Table I - Item 2 - Value column>"
$diskStorageType="<Table M - Item 2 - Storage type column>"
$diskSize=<size of the extra disk for Windows Server AD data in GB>

$nic=New-AzureRMNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName -Subnet $subnet -PrivateIpAddress $staticIP
$vm=New-AzureRMVMConfig -VMName $vmName -VMSize $vmSize -AvailabilitySetId $avset.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
$diskConfig=New-AzureRmDiskConfig -AccountType $diskStorageType -Location $locName -CreateOption Empty -DiskSizeGB $diskSize
$dataDisk1=New-AzureRmDisk -DiskName ($vmName + "-DataDisk1") -Disk $diskConfig -ResourceGroupName $rgName
$vm=Add-AzureRmVMDataDisk -VM $vm -Name ($vmName + "-DataDisk1") -CreateOption Attach -ManagedDiskId $dataDisk1.Id -Lun 1
$cred=Get-Credential -Message "Type the name and password of the local administrator account for the second domain controller." 
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm

# Create the DirSync server
$vmName="<Table M - Item 3 - Virtual machine name column>"
$vmSize="<Table M - Item 3 - Minimum size column>"
$staticIP="<Table I - Item 3 - Value column>"
$diskStorageType="<Table M - Item 3 - Storage type column>"

$nic=New-AzureRMNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName -Subnet $subnet -PrivateIpAddress $staticIP
$vm=New-AzureRMVMConfig -VMName $vmName -VMSize $vmSize

$cred=Get-Credential -Message "Type the name and password of the local administrator account for the DirSync server." 
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

> [!NOTE]
> <span data-ttu-id="185b6-p105">Da diese virtuellen Maschinen für eine Intranetanwendung sind, sind keine öffentliche IP-Adresse oder eine Bezeichnung für DNS-Domäne zugewiesen und im Internet verfügbar gemacht. Dies bedeutet jedoch auch, dass Sie über das Portal Azure eine Verbindung ist nicht möglich. Die Option **Verbinden** ist nicht verfügbar, wenn Sie die Eigenschaften des virtuellen Computers anzeigen. Verwenden Sie die Remotedesktopverbindung Zubehör oder ein anderes Remotedesktop-Tool Verbindung mit dem virtuellen Computer mit privaten IP-Adresse oder Intranet DNS-Namen ein.</span><span class="sxs-lookup"><span data-stu-id="185b6-p105">Because these virtual machines are for an intranet application, they are not assigned a public IP address or a DNS domain name label and exposed to the Internet. However, this also means that you cannot connect to them from the Azure portal. The **Connect** option is unavailable when you view the properties of the virtual machine. Use the Remote Desktop Connection accessory or another Remote Desktop tool to connect to the virtual machine using its private IP address or intranet DNS name.</span></span>
  
## <a name="configure-the-first-domain-controller"></a><span data-ttu-id="185b6-172">Konfigurieren des ersten Domänencontrollers</span><span class="sxs-lookup"><span data-stu-id="185b6-172">Configure the first domain controller</span></span>

<span data-ttu-id="185b6-p106">Erstellen Sie mithilfe eines Remotedesktopclients Ihrer Wahl eine Remotedesktopverbindung zum virtuellen Computer mit dem ersten Domänencontroller. Verwenden Sie den Intranet-DNS-Namen oder den Computernamen des Servers und die Anmeldeinformationen des lokalen Administratorkontos.</span><span class="sxs-lookup"><span data-stu-id="185b6-p106">Use the remote desktop client of your choice and create a remote desktop connection to the first domain controller virtual machine. Use its intranet DNS or computer name and the credentials of the local administrator account.</span></span>
  
<span data-ttu-id="185b6-175">Fügen Sie als Nächstes den zusätzlichen Datenträger mit dem ersten Domänencontroller mit diesem Befehl von einer Windows PowerShell-Eingabeaufforderung **auf dem ersten Domain Controller virtuellen Computer**:</span><span class="sxs-lookup"><span data-stu-id="185b6-175">Next, add the extra data disk to the first domain controller with this command from a Windows PowerShell command prompt **on the first domain controller virtual machine**:</span></span>
  
```
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

<span data-ttu-id="185b6-176">Im nächsten Schritt Testen der ersten Domänencontroller Konnektivität zu Speicherorten im Netzwerk Ihrer Organisation mithilfe des **Ping** -Befehls ping und IP-Adressen von Ressourcen im Netzwerk Ihrer Organisation.</span><span class="sxs-lookup"><span data-stu-id="185b6-176">Next, test the first domain controller's connectivity to locations on your organization network by using the **ping** command to ping names and IP addresses of resources on your organization network.</span></span>
  
<span data-ttu-id="185b6-p107">Gleichzeitig stellen Sie damit sicher, dass die DNS-Namensauflösung korrekt funktioniert (d. h., dass der virtuelle Computer korrekt mit denlokalen DNS-Servern konfiguriert ist) und dass Pakete sowohl an das standortübergreifende Netzwerk als auch aus ihm gesendet werden können. Wenn bei diesem grundlegenden Test ein Fehler auftritt, wenden Sie sich an Ihre IT-Abteilung, um die Probleme mit der DNS-Namensauflösung und der Paketzustellung zu lösen.</span><span class="sxs-lookup"><span data-stu-id="185b6-p107">This procedure ensures that DNS name resolution is working correctly (that the virtual machine is correctly configured with on-premises DNS servers) and that packets can be sent to and from the cross-premises virtual network. If this basic test fails, contact your IT department to troubleshoot the DNS name resolution and packet delivery issues.</span></span>
  
<span data-ttu-id="185b6-179">Führen Sie im nächsten Schritt an der Windows PowerShell-Eingabeaufforderung auf dem ersten Domänencontroller die folgenden Befehle aus:</span><span class="sxs-lookup"><span data-stu-id="185b6-179">Next, from the Windows PowerShell command prompt on the first domain controller, run the following commands:</span></span>
  
```
$domname="<DNS domain name of the domain for which this computer will be a domain controller, such as corp.contoso.com>"
$cred = Get-Credential -Message "Enter credentials of an account with permission to join a new domain controller to the domain"
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSDomainController -InstallDns -DomainName $domname  -DatabasePath "F:\\NTDS" -SysvolPath "F:\\SYSVOL" -LogPath "F:\\Logs" -Credential $cred
```

<span data-ttu-id="185b6-p108">Sie werden aufgefordert, die Anmeldeinformationen für ein Domänenadministratorkonto einzugeben. Der Computer wird neu gestartet.</span><span class="sxs-lookup"><span data-stu-id="185b6-p108">You will be prompted to supply the credentials of a domain administrator account. The computer will restart.</span></span>
  
## <a name="configure-the-second-domain-controller"></a><span data-ttu-id="185b6-182">Konfigurieren des zweiten Domänencontrollers</span><span class="sxs-lookup"><span data-stu-id="185b6-182">Configure the second domain controller</span></span>

<span data-ttu-id="185b6-p109">Erstellen Sie mithilfe eines Remotedesktopclients Ihrer Wahl eine Remotedesktopverbindung zum virtuellen Computer mit dem zweiten Domänencontroller. Verwenden Sie den Intranet-DNS-Namen oder den Computernamen des Servers und die Anmeldeinformationen des lokalen Administratorkontos.</span><span class="sxs-lookup"><span data-stu-id="185b6-p109">Use the remote desktop client of your choice and create a remote desktop connection to the second domain controller virtual machine. Use its intranet DNS or computer name and the credentials of the local administrator account.</span></span>
  
<span data-ttu-id="185b6-185">Als Nächstes müssen Sie den zusätzlichen Daten Datenträger auf den zweiten Domänencontroller mit diesem Befehl von einer Windows PowerShell-Eingabeaufforderung **auf dem zweiten Domain Controller virtuellen Computer**hinzufügen:</span><span class="sxs-lookup"><span data-stu-id="185b6-185">Next, you need to add the extra data disk to the second domain controller with this command from a Windows PowerShell command prompt **on the second domain controller virtual machine**:</span></span>
  
```
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

<span data-ttu-id="185b6-186">Führen Sie als nächsten Schritt die folgenden Befehle aus:</span><span class="sxs-lookup"><span data-stu-id="185b6-186">Next, run the following commands:</span></span>
  
```
$domname="<DNS domain name of the domain for which this computer will be a domain controller, such as corp.contoso.com>"
$cred = Get-Credential -Message "Enter credentials of an account with permission to join a new domain controller to the domain"
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSDomainController -InstallDns -DomainName $domname  -DatabasePath "F:\\NTDS" -SysvolPath "F:\\SYSVOL" -LogPath "F:\\Logs" -Credential $cred

```

<span data-ttu-id="185b6-p110">Sie werden aufgefordert, die Anmeldeinformationen für ein Domänenadministratorkonto einzugeben. Der Computer wird neu gestartet.</span><span class="sxs-lookup"><span data-stu-id="185b6-p110">You will be prompted to supply the credentials of a domain administrator account. The computer will restart.</span></span>
  
<span data-ttu-id="185b6-p111">Im nächsten Schritt müssen Sie die DNS-Server für das virtuelle Netzwerk aktualisieren, damit dieser Azure virtuelle Computer zwei neue Domänencontroller als DNS-Server verwenden die IP-Adressen zugewiesen. Füllen Sie die Variablen, und führen Sie diese Befehle von einer Windows PowerShell-Eingabeaufforderung auf dem lokalen Computer:</span><span class="sxs-lookup"><span data-stu-id="185b6-p111">Next, you need to update the DNS servers for your virtual network so that Azure assigns virtual machines the IP addresses of the two new domain controllers to use as their DNS servers. Fill in the variables and then run these commands from a Windows PowerShell command prompt on your local computer:</span></span>
  
```
$rgName="<Table R - Item 4 - Resource group name column>"
$adrgName="<Table R - Item 1 - Resource group name column>"
$locName="<your Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$onpremDNSIP1="<Table D - Item 1 - DNS server IP address column>"
$onpremDNSIP2="<Table D - Item 2 - DNS server IP address column>"
$staticIP1="<Table I - Item 1 - Value column>"
$staticIP2="<Table I - Item 2 - Value column>"
$firstDCName="<Table M - Item 1 - Virtual machine name column>"
$secondDCName="<Table M - Item 2 - Virtual machine name column>"

$vnet=Get-AzureRMVirtualNetwork -ResourceGroupName $rgName -Name $vnetName
$vnet.DhcpOptions.DnsServers.Add($staticIP1)
$vnet.DhcpOptions.DnsServers.Add($staticIP2) 
$vnet.DhcpOptions.DnsServers.Remove($onpremDNSIP1)
$vnet.DhcpOptions.DnsServers.Remove($onpremDNSIP2) 
Set-AzureRMVirtualNetwork -VirtualNetwork $vnet
Restart-AzureRMVM -ResourceGroupName $adrgName -Name $firstDCName
Restart-AzureRMVM -ResourceGroupName $adrgName -Name $secondDCName
```

<span data-ttu-id="185b6-p112">Beachten Sie, dass die beiden Domänencontroller neu gestartet werden, damit sie nicht mit den lokalen DNS-Server als DNS-Server konfiguriert werden. Da beide selbst DNS-Server sind, wurden sie bei der Höherstufung zu Domänencontrollern automatisch mit den lokalen DNS-Servern als DNS-Weiterleitungen konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="185b6-p112">Note that we restart the two domain controllers so that they are not configured with the on-premises DNS servers as DNS servers. Because they are both DNS servers themselves, they were automatically configured with the on-premises DNS servers as DNS forwarders when they were promoted to domain controllers.</span></span>
  
<span data-ttu-id="185b6-p113">Als Nächstes müssen wir eine Active Directory-Replikationswebsite erstellen, um sicherzustellen, dass Server im virtuellen Azure-Netzwerk die lokalen Domänencontroller verwenden. Stellen Sie mit einem Domänenadministratorkonto eine Verbindung zu einem der Domänencontroller her, und führen Sie folgende Befehle an einer Windows PowerShell-Eingabeaufforderung auf Administratorebene aus:</span><span class="sxs-lookup"><span data-stu-id="185b6-p113">Next, we need to create an Active Directory replication site to ensure that servers in the Azure virtual network use the local domain controllers. Connect to either domain controller with a domain administrator account and run the following commands from an administrator-level Windows PowerShell prompt:</span></span>
  
```
$vnet="<Table V - Item 1 - Value column>"
$vnetSpace="<Table V - Item 4 - Value column>"
New-ADReplicationSite -Name $vnet 
New-ADReplicationSubnet -Name $vnetSpace -Site $vnet
```

## <a name="configure-the-dirsync-server"></a><span data-ttu-id="185b6-195">Konfigurieren des DirSync-Servers</span><span class="sxs-lookup"><span data-stu-id="185b6-195">Configure the DirSync server</span></span>

<span data-ttu-id="185b6-p114">Verwenden Sie den remote desktop Client Ihrer Wahl, und erstellen Sie eine Remotedesktopverbindung Dirsync-Server am virtuellen Computer. Verwenden Sie dem Intranet Computer oder DNS-Namen und die Anmeldeinformationen für das lokale Administratorkonto.</span><span class="sxs-lookup"><span data-stu-id="185b6-p114">Use the remote desktop client of your choice and create a remote desktop connection to the DirSync server virtual machine. Use its intranet DNS or computer name and the credentials of the local administrator account.</span></span>
  
<span data-ttu-id="185b6-198">Verknüpfen Sie als nächstes unter Verwendung der folgenden Befehle an einer Windows PowerShell-Eingabeaufforderung diesen mit der entsprechenden Windows Server AD-Domäne.</span><span class="sxs-lookup"><span data-stu-id="185b6-198">Next, join it to the appropriate Windows Server AD domain with these commands at the Windows PowerShell prompt.</span></span>
  
```
$domName="<Windows Server AD domain name to join, such as corp.contoso.com>"
$cred=Get-Credential -Message "Type the name and password of a domain acccount."
Add-Computer -DomainName $domName -Credential $cred
Restart-Computer
```

<span data-ttu-id="185b6-199">Wenn Sie diese Phase erfolgreich abgeschlossen haben, sieht Ihre Konfiguration wie folgt aus. Für die Computernamen werden hier Platzhalter verwendet.</span><span class="sxs-lookup"><span data-stu-id="185b6-199">Here is the configuration resulting from the successful completion of this phase, with placeholder computer names.</span></span>
  
<span data-ttu-id="185b6-200">**Phase 2: Die Domänencontroller und Dirsync-Server für eine hohe Verfügbarkeit Verbundauthentifizierung-Infrastruktur in Azure**</span><span class="sxs-lookup"><span data-stu-id="185b6-200">**Phase 2: The domain controllers and DirSync server for your high availability federated authentication infrastructure in Azure**</span></span>

![Phase 2 der hochverfügbaren Office 365-Verbundauthentifizierungsinfrastruktur in Azure mit Domänencontrollern](images/b0c1013b-3fb4-499e-93c1-bf310d8f4c32.png)
  
## <a name="next-step"></a><span data-ttu-id="185b6-202">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="185b6-202">Next step</span></span>

<span data-ttu-id="185b6-203">Verwendung [hoher Verfügbarkeit federated Authentifizierung Phase 3: Konfigurieren von AD FS-Servern](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md) Konfiguration von Arbeitslast fortzufahren.</span><span class="sxs-lookup"><span data-stu-id="185b6-203">Use [High availability federated authentication Phase 3: Configure AD FS servers](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md) to continue configuring this workload.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="185b6-204">Weitere Artikel</span><span class="sxs-lookup"><span data-stu-id="185b6-204">See Also</span></span>

[<span data-ttu-id="185b6-205">Bereitstellen der Verbundauthentifizierung mit Hochverfügbarkeit für Office 365 in Azure</span><span class="sxs-lookup"><span data-stu-id="185b6-205">Deploy high availability federated authentication for Office 365 in Azure</span></span>](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)
  
[<span data-ttu-id="185b6-206">Verbundidentität für Ihre Office 365-Entwicklungs-/Testumgebung</span><span class="sxs-lookup"><span data-stu-id="185b6-206">Federated identity for your Office 365 dev/test environment</span></span>](federated-identity-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="185b6-207">Cloudakzeptanz und Hybridlösungen</span><span class="sxs-lookup"><span data-stu-id="185b6-207">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)

[<span data-ttu-id="185b6-208">Verbundidentität für Office 365</span><span class="sxs-lookup"><span data-stu-id="185b6-208">Federated identity for Office 365</span></span>](https://support.office.com/article/Understanding-Office-365-identity-and-Azure-Active-Directory-06a189e7-5ec6-4af2-94bf-a22ea225a7a9#bk_federated)


