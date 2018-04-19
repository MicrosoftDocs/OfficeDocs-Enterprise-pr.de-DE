---
title: Die Microsoft 365 Enterprise-Entwicklungs-/Testumgebung
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/18/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
ms.assetid: 6f916a77-301c-4be2-b407-6cec4d80df76
description: 'Zusammenfassung: Mit diesem Test Lab Guide können eine Test-/Umgebung erstellen, die Office 365 E5, Enterprise Mobilität + Sicherheit (zur Abstimmung) E5 und einem Computer mit Windows 10 Enterprise enthält.'
ms.openlocfilehash: 9ef1c13d7ae194ff4ba31abaf379529220ffa14f
ms.sourcegitcommit: 62c0630cc0d2611710e73e0592bddfe093e00783
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/19/2018
---
# <a name="the-microsoft-365-enterprise-devtest-environment"></a><span data-ttu-id="b7098-103">Die Microsoft 365 Enterprise-Entwicklungs-/Testumgebung</span><span class="sxs-lookup"><span data-stu-id="b7098-103">The Microsoft 365 Enterprise dev/test environment</span></span>

 <span data-ttu-id="b7098-104">**Zusammenfassung:** Verwenden Sie in diesem Test Lab Guide eine Test-/Umgebung erstellen, die Office 365 E5, Enterprise Mobilität + Sicherheit (zur Abstimmung) E5 und einem Computer mit Windows 10 Enterprise enthält.</span><span class="sxs-lookup"><span data-stu-id="b7098-104">**Summary:** Use this Test Lab Guide to create a dev/test environment that includes Office 365 E5, Enterprise Mobility + Security (EMS) E5, and a computer running Windows 10 Enterprise.</span></span>
  
<span data-ttu-id="b7098-105">Dieser Artikel enthält eine schrittweise Anleitung zum Erstellen einer vereinfachten-Umgebung um die Features und Funktionen von [Microsoft 365 Enterprise](https://www.microsoft.com/microsoft-365/enterprise)zu testen.</span><span class="sxs-lookup"><span data-stu-id="b7098-105">This article provides you with step-by-step instructions to create a simplified environment to test the features and functionality of [Microsoft 365 Enterprise](https://www.microsoft.com/microsoft-365/enterprise).</span></span>
  
## <a name="phase-1-create-your-office-365-e5-subscription"></a><span data-ttu-id="b7098-106">Phase 1: Erstellen des Office 365 E5-Abonnements</span><span class="sxs-lookup"><span data-stu-id="b7098-106">Phase 1: Create your Office 365 E5 subscription</span></span>

<span data-ttu-id="b7098-107">Führen Sie die Schritte in Phase 2 und Phase 3 der [Office 365 Dev/Test-Umgebung](office-365-dev-test-environment.md) zu eine Test-/Lightweight Office 365-Umgebung erstellen, wie in Abbildung 1 dargestellt.</span><span class="sxs-lookup"><span data-stu-id="b7098-107">Follow the steps in Phase 2 and Phase 3 of the [Office 365 dev/test environment](office-365-dev-test-environment.md) to create a lightweight Office 365 dev/test environment, as shown in Figure 1.</span></span>
  
<span data-ttu-id="b7098-108">**Abbildung 1: Ihr Office 365 E5-Abonnement mit der Mandanten und Benutzerkonten von Azure Active Directory (AD)**</span><span class="sxs-lookup"><span data-stu-id="b7098-108">**Figure 1: Your Office 365 E5 subscription with its Azure Active Directory (AD) tenant and user accounts**</span></span>

![Phase 1 der Microsoft 3656 Enterprise-Entwicklungs-/Testumgebung](images/65bb027b-fb59-46eb-aec2-38c0af425168.png)

> [!NOTE]
> <span data-ttu-id="b7098-p101">Das Test-Abonnement von Office 365 E5 ist 30 Tage bis 60 Tage auf einfache Weise erweitert werden kann. Erstellen Sie für eine permanente Test-/-Umgebung ein neues kostenpflichtiges Abonnement mit einer kleinen Anzahl von Lizenzen.</span><span class="sxs-lookup"><span data-stu-id="b7098-p101">The Office 365 E5 trial subscription is 30 days, which can be easily extended to 60 days. For a permanent dev/test environment, create a new paid subscription with a small number of licenses.</span></span> 
  
## <a name="phase-2-add-ems"></a><span data-ttu-id="b7098-112">Phase 2: Hinzufügen von EMS</span><span class="sxs-lookup"><span data-stu-id="b7098-112">Phase 2: Add EMS</span></span>

<span data-ttu-id="b7098-113">In dieser Phase registrieren Sie sich für das EMS E5-Testabonnement und fügen es derselben Organisation wie Ihr Office 365 E5-Testabonnement hinzu.</span><span class="sxs-lookup"><span data-stu-id="b7098-113">In this phase, you sign up for the EMS E5 trial subscription and add it to the same organization as your Office 365 E5 trial subscription.</span></span>
  
<span data-ttu-id="b7098-114">Zunächst fügen Sie Test zur Abstimmung E5-Abonnement hinzu, und weisen Sie eine Lizenz zur Abstimmung Ihrer globale Administratorkonto ein.</span><span class="sxs-lookup"><span data-stu-id="b7098-114">First, add the EMS E5 trial subscription and assign an EMS license to your global administrator account.</span></span>
  
1. <span data-ttu-id="b7098-p102">Mit einer privaten Instanz eines Internetbrowsers melden Sie sich bei Office 365-Portal mit den Anmeldeinformationen Ihres globaler Administrator an. Hilfe finden Sie unter [Where zur Anmeldung bei Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="b7098-p102">With a private instance of an Internet browser, sign in to the Office 365 portal with your global administrator account credentials. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="b7098-117">Klicken Sie auf die Kachel **Admin**.</span><span class="sxs-lookup"><span data-stu-id="b7098-117">Click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="b7098-118">Klicken Sie auf der Registerkarte **Office Admin Center** in Ihrem Browser im linken Navigationsbereich auf **Abrechnung > Dienste kaufen**.</span><span class="sxs-lookup"><span data-stu-id="b7098-118">On the **Office Admin center** tab in your browser, in the left navigation, click **Billing > Purchase services**.</span></span>
    
4. <span data-ttu-id="b7098-p103">Suchen Sie auf der Seite **Dienste kaufen** den Artikel **Enterprise Mobility + Security E5**. Platzieren Sie den Mauszeiger auf dem Artikelnamen, und klicken Sie auf **Start free trial**.</span><span class="sxs-lookup"><span data-stu-id="b7098-p103">On the **Purchase services** page, find the **Enterprise Mobility + Security E5** item. Hover your mouse pointer over it and click **Start free trial**.</span></span>
    
5. <span data-ttu-id="b7098-121">Klicken Sie auf der Seite für die **Bestätigung Ihrer Bestellung** auf **Jetzt versuchen**.</span><span class="sxs-lookup"><span data-stu-id="b7098-121">On the **Confirm your order** page, click **Try now**.</span></span>
    
6. <span data-ttu-id="b7098-122">Klicken Sie auf der Seite **Bestellbestätigung** auf **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="b7098-122">On the **Order receipt** page, click **Continue**.</span></span>
    
7. <span data-ttu-id="b7098-123">Klicken Sie auf der Registerkarte **Office 365 Admin Center** in Ihrem Browser im linken Navigationsbereich auf **Benutzer > Aktive Benutzer**.</span><span class="sxs-lookup"><span data-stu-id="b7098-123">On the **Office 365 Admin center** tab in your browser, in the left navigation, click **Users > Active users**.</span></span>
    
8. <span data-ttu-id="b7098-124">Klicken Sie auf Ihr globales Administratorkonto und dann auf **Bearbeiten**, um die **Produktlizenzen** anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="b7098-124">Click your global administrator account, and then click **Edit** for **Product licenses**.</span></span>
    
9. <span data-ttu-id="b7098-125">Setzen Sie im Bereich **Product licenses** die Produktlizenz für **Enterprise Mobility + Security E5** auf **On**. Klicken Sie auf **Speichern** und dann auf **Schließen**.</span><span class="sxs-lookup"><span data-stu-id="b7098-125">On the **Product licenses** pane, turn the product license for **Enterprise Mobility + Security E5** to **On**, click **Save,** and then click **Close** twice.</span></span>
    
> [!NOTE]
> <span data-ttu-id="b7098-p104">Das Testabonnement für Enterprise Mobility + Security E5 ist 90 Tage gültig. Für eine dauerhafte Entwicklungs-/Testumgebung erstellen Sie ein neues bezahltes Abonnement mit einer kleinen Anzahl von Lizenzen.</span><span class="sxs-lookup"><span data-stu-id="b7098-p104">The Enterprise Mobility + Security E5 trial subscription is 90 days. For a permanent dev/test environment, create a new paid subscription with a small number of licenses.</span></span> 
  
 <span data-ttu-id="b7098-128">***Wenn Sie die Phase 3 des abgeschlossen die*** [Office 365 Dev/Test-Umgebung](office-365-dev-test-environment.md), wiederholen Sie die Schritte 8 und 9 des vorherigen Verfahrens für alle anderen Konten (Benutzer 2, 3 für Benutzer, Benutzer 4 und 5 Benutzer).</span><span class="sxs-lookup"><span data-stu-id="b7098-128">***If you completed Phase 3 of the*** [Office 365 dev/test environment](office-365-dev-test-environment.md), repeat steps 8 and 9 of the previous procedure for all of your other accounts (User 2, User 3, User 4, and User 5).</span></span>
  
<span data-ttu-id="b7098-129">Ihre Entwicklungs-/Testumgebung verfügt nun über Folgendes:</span><span class="sxs-lookup"><span data-stu-id="b7098-129">Your dev/test environment now has:</span></span>
  
- <span data-ttu-id="b7098-130">Office 365 E5 Unternehmen und zur Abstimmung E5 Testabonnements Freigabe den gleichen Azure AD-Mandanten mit der Liste der Benutzerkonten.</span><span class="sxs-lookup"><span data-stu-id="b7098-130">Office 365 E5 Enterprise and EMS E5 trial subscriptions sharing the same Azure AD tenant with your list of user accounts.</span></span>
- <span data-ttu-id="b7098-131">Alle Ihre entsprechenden Benutzerkonten (globaler Administrator oder alle fünf Benutzerkonten) werden von Office 365 E5 und zur Abstimmung E5 aktiviert.</span><span class="sxs-lookup"><span data-stu-id="b7098-131">All your appropriate user accounts (either just the global administrator or all five user accounts) are enabled to use Office 365 E5 and EMS E5.</span></span>
    
<span data-ttu-id="b7098-132">Abbildung 2 zeigt die Konfiguration nach dem Hinzufügen von EMS.</span><span class="sxs-lookup"><span data-stu-id="b7098-132">Figure 2 shows your resulting configuration, which adds EMS.</span></span>
  
<span data-ttu-id="b7098-133">**Abbildung 2: Hinzufügen des Test zur Abstimmung-Abonnements**</span><span class="sxs-lookup"><span data-stu-id="b7098-133">**Figure 2: Adding the EMS trial subscription**</span></span>

![Phase 2 der Microsoft 3656 Enterprise-Entwicklungs-/Testumgebung](images/8a01a483-3de2-41f3-a845-141c7edd0cb0.png)
  
## <a name="phase-3-create-a-windows-10-enterprise-computer"></a><span data-ttu-id="b7098-135">Phase 3: Erstellen eines Computers mit Windows 10 Enterprise</span><span class="sxs-lookup"><span data-stu-id="b7098-135">Phase 3: Create a Windows 10 Enterprise computer</span></span>

<span data-ttu-id="b7098-136">In dieser Phase erstellen Sie einen eigenständigen Computer, auf dem Windows 10 Enterprise ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="b7098-136">In this phase, you create a standalone computer running Windows 10 Enterprise.</span></span>
  
### <a name="physical-computer"></a><span data-ttu-id="b7098-137">Physischer Computer</span><span class="sxs-lookup"><span data-stu-id="b7098-137">Physical computer</span></span>

<span data-ttu-id="b7098-p105">Beziehen Sie einen privaten Computer und installieren Sie Windows 10 Enterprise darauf. Sie können das Windows 10 Enterprise Testversion [hier](https://www.microsoft.com/evalcenter/evaluate-windows-10-enterprise)herunterladen.</span><span class="sxs-lookup"><span data-stu-id="b7098-p105">Obtain a personal computer and install Windows 10 Enterprise on it. You can download the Windows 10 Enterprise trial [here](https://www.microsoft.com/evalcenter/evaluate-windows-10-enterprise).</span></span>
  
### <a name="virtual-machine"></a><span data-ttu-id="b7098-140">Virtueller Computer</span><span class="sxs-lookup"><span data-stu-id="b7098-140">Virtual machine</span></span>

<span data-ttu-id="b7098-p106">Erstellen Sie einen virtuellen Computer mit dem Hypervisor Ihrer Wahl, und installieren Sie Windows 10 Enterprise auf ihn. Sie können das Windows 10 Enterprise Testversion [hier](https://www.microsoft.com/evalcenter/evaluate-windows-10-enterprise)herunterladen.</span><span class="sxs-lookup"><span data-stu-id="b7098-p106">Create a virtual machine using the hypervisor of your choice and install Windows 10 Enterprise on it. You can download the Windows 10 Enterprise trial [here](https://www.microsoft.com/evalcenter/evaluate-windows-10-enterprise).</span></span>
  
### <a name="virtual-machine-in-azure"></a><span data-ttu-id="b7098-143">Virtueller Computer in Azure</span><span class="sxs-lookup"><span data-stu-id="b7098-143">Virtual machine in Azure</span></span>

<span data-ttu-id="b7098-p107">Zum Erstellen eines virtuellen Computers von Windows 10 in Microsoft Azure, ***benötigen Sie ein Visual Studio-basierte Abonnement***, die Zugriff auf das Bild für Windows 10 Enterprise hat. Andere Arten von Azure-Abonnements, wie etwa Testversionen und kostenpflichtigen Abonnements keinen Zugriff auf dieses Bild.</span><span class="sxs-lookup"><span data-stu-id="b7098-p107">To create a Windows 10 virtual machine in Microsoft Azure, ***you must have a Visual Studio-based subscription***, which has access to the image for Windows 10 Enterprise. Other types of Azure subscriptions, such as trial and paid subscriptions, do not have access to this image.</span></span>
  
> [!NOTE]
> <span data-ttu-id="b7098-p108">Verwenden Sie den folgenden Befehl wird die neueste Version von Azure PowerShell. Finden Sie unter [Erste Schritte mit Azure PowerShell-Cmdlets](https://docs.microsoft.com/powershell/azureps-cmdlets-docs/). Dieser Befehl legt Build einen Windows 10 Enterprise virtuellen Computer mit dem Namen WIN10 und alle seine notwendige Infrastruktur, einschließlich einer Ressourcengruppe, Speicher-Konto und ein virtuelles Netzwerk. Wenn Sie bereits mit Azure Infrastructure Services vertraut sind, wenden Sie sich passen Sie diese Anweisungen der aktuell bereitgestellten Infrastruktur entsprechend an.</span><span class="sxs-lookup"><span data-stu-id="b7098-p108">The following command sets use the latest version of Azure PowerShell. See [Get started with Azure PowerShell cmdlets](https://docs.microsoft.com/powershell/azureps-cmdlets-docs/). These command sets build a Windows 10 Enterprise virtual machine named WIN10 and all of its required infrastructure, including a resource group, a storage account, and a virtual network. If you are already familiar with Azure infrastructure services, please adapt these instructions to suit your currently deployed infrastructure.</span></span> 
  
<span data-ttu-id="b7098-150">Starten Sie zuerst eine Microsoft PowerShell-Eingabeaufforderung.</span><span class="sxs-lookup"><span data-stu-id="b7098-150">First, start a Microsoft PowerShell prompt.</span></span>
  
<span data-ttu-id="b7098-151">Melden Sie sich mit dem folgenden Befehl bei Ihrem Azure-Konto an.</span><span class="sxs-lookup"><span data-stu-id="b7098-151">Sign in to your Azure account with the following command.</span></span>
  
```
Login-AzureRMAccount
```

<span data-ttu-id="b7098-152">Rufen Sie den Namen Ihres Abonnements mithilfe des folgenden Befehls ab.</span><span class="sxs-lookup"><span data-stu-id="b7098-152">Get your subscription name using the following command.</span></span>
  
```
Get-AzureRMSubscription | Sort Name | Select Name
```

<span data-ttu-id="b7098-p109">Legen Sie Ihre Azure-Abonnement. Ersetzen Sie alles innerhalb der Anführungszeichen, einschließlich der \< und > Zeichen, mit dem korrekten Namen.</span><span class="sxs-lookup"><span data-stu-id="b7098-p109">Set your Azure subscription. Replace everything within the quotes, including the \< and > characters, with the correct name.</span></span>
  
```
$subscr="<subscription name>"
Get-AzureRmSubscription -SubscriptionName $subscr | Select-AzureRmSubscription
```

<span data-ttu-id="b7098-p110">Im nächsten Schritt wird eine neue Ressourcengruppe erstellt. Verwenden Sie zum Ermitteln eines eindeutigen Ressourcengruppennamens diesen Befehl, mit dem die vorhandenen Ressourcengruppen aufgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="b7098-p110">Next, create a new resource group. To determine a unique resource group name, use this command to list your existing resource groups.</span></span>
  
```
Get-AzureRMResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

<span data-ttu-id="b7098-p111">Erstellen Sie Ihre neue Ressourcengruppe mit diesen Befehlen. Ersetzen Sie alles innerhalb der Anführungszeichen, einschließlich der \< und > Zeichen, mit den richtigen Namen.</span><span class="sxs-lookup"><span data-stu-id="b7098-p111">Create your new resource group with these commands. Replace everything within the quotes, including the \< and > characters, with the correct names.</span></span>
  
```
$rgName="<resource group name>"
$locName="<location name, such as West US>"
New-AzureRMResourceGroup -Name $rgName -Location $locName
```

<span data-ttu-id="b7098-p112">Im nächsten Schritt erstellen Sie ein neues virtuelles Netzwerk und den virtuellen WIN10-Computer mit den folgenden Befehlen. Wenn Sie dazu aufgefordert werden, geben Sie den Namen und das Kennwort des lokalen Administratorkontos für WIN10 an, und bewahren Sie dieses an einem sicheren Ort auf.</span><span class="sxs-lookup"><span data-stu-id="b7098-p112">Next, you create a new virtual network and the WIN10 virtual machine with these commands. When prompted, provide the name and password of the local administrator account for WIN10 and store these in a secure location.</span></span>
  
```
$corpnetSubnet=New-AzureRMVirtualNetworkSubnetConfig -Name Corpnet -AddressPrefix 10.0.0.0/24
New-AzureRMVirtualNetwork -Name "M365Ent-TestLab" -ResourceGroupName $rgName -Location $locName -AddressPrefix 10.0.0.0/8 -Subnet $corpnetSubnet
$rule1=New-AzureRMNetworkSecurityRuleConfig -Name "RDPTraffic" -Description "Allow RDP to all VMs on the subnet" -Access Allow -Protocol Tcp -Direction Inbound -Priority 100 -SourceAddressPrefix Internet -SourcePortRange * -DestinationAddressPrefix * -DestinationPortRange 3389
New-AzureRMNetworkSecurityGroup -Name Corpnet -ResourceGroupName $rgName -Location $locName -SecurityRules $rule1
$vnet=Get-AzureRMVirtualNetwork -ResourceGroupName $rgName -Name "M365Ent-TestLab"
$nsg=Get-AzureRMNetworkSecurityGroup -Name Corpnet -ResourceGroupName $rgName
Set-AzureRMVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name Corpnet -AddressPrefix "10.0.0.0/24" -NetworkSecurityGroup $nsg
$pip=New-AzureRMPublicIpAddress -Name WIN10-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic=New-AzureRMNetworkInterface -Name WIN10-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id
$vm=New-AzureRMVMConfig -VMName WIN10 -VMSize Standard_D1_V2
$cred=Get-Credential -Message "Type the name and password of the local administrator account for WIN10."
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName WIN10 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsDesktop -Offer Windows-10 -Skus RS3-Pro -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name WIN10-TestLab-OSDisk -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "StandardLRS"
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

## <a name="phase-4-join-your-windows-10-computer-to-azure-ad"></a><span data-ttu-id="b7098-161">Phase 4: Einbinden des Windows 10-Computers in Azure AD</span><span class="sxs-lookup"><span data-stu-id="b7098-161">Phase 4: Join your Windows 10 computer to Azure AD</span></span>

<span data-ttu-id="b7098-162">Nach dem Erstellen der physischen oder virtuellen Computer mit Windows 10 Enterprise melden Sie sich über ein lokales Administratorkonto.</span><span class="sxs-lookup"><span data-stu-id="b7098-162">After the physical or virtual machine with Windows 10 Enterprise is created, sign in with a local administrator account.</span></span>
  
> [!NOTE]
> <span data-ttu-id="b7098-p113">Für einen virtuellen Computer in Azure eine Verbindung damit herzustellen Sie anhand der [folgenden Schritte](https://docs.microsoft.com/azure/virtual-machines/windows/connect-logon). Melden Sie sich mit den Anmeldeinformationen des lokalen Administratorkontos.</span><span class="sxs-lookup"><span data-stu-id="b7098-p113">For a virtual machine in Azure, connect to it using [these instructions](https://docs.microsoft.com/azure/virtual-machines/windows/connect-logon). Sign in with the credentials of the local administrator account.</span></span> 
  
<span data-ttu-id="b7098-165">Als Nächstes fügen Sie den WIN10-Computer dem Azure AD-Mandanten Ihrer Office 365- und EMS-Abonnements hinzu.</span><span class="sxs-lookup"><span data-stu-id="b7098-165">Next, join the WIN10 computer to the Azure AD tenant of your Office 365 and EMS subscriptions.</span></span>
  
1. <span data-ttu-id="b7098-166">Klicken Sie auf dem Desktop des Computers WIN10 **starten > Einstellungen > Konten > Access Arbeit "oder" Schule > Connect**.</span><span class="sxs-lookup"><span data-stu-id="b7098-166">At the desktop of the WIN10 computer, click **Start > Settings > Accounts > Access work or school > Connect**.</span></span>
    
2. <span data-ttu-id="b7098-167">Klicken Sie auf **dieses Gerät zu Azure Active Directory teilnehmen**, klicken Sie im Dialogfeld **Einrichten eines Kontos arbeiten oder Schule** .</span><span class="sxs-lookup"><span data-stu-id="b7098-167">In the **Set up a work or school account** dialog box, click **Join this device to Azure Active Directory**.</span></span>
    
3. <span data-ttu-id="b7098-168">In **Arbeit oder Schule Konto**, geben Sie den Kontonamen globaler Administrator Ihres Office 365-Abonnements, und klicken Sie dann auf **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="b7098-168">In **Work or school account**, type the global administrator account name of your Office 365 subscription, and then click **Next**.</span></span>
    
4. <span data-ttu-id="b7098-169">Geben Sie im Feld **Kennwort eingeben**das Kennwort für das globale Administratorkonto ein, und klicken Sie dann auf **Anmelden**.</span><span class="sxs-lookup"><span data-stu-id="b7098-169">In **Enter password**, type the password for your global administrator account, and then click **Sign in**.</span></span>
    
5. <span data-ttu-id="b7098-170">Wenn Sie aufgefordert werden, um sicherzustellen, dass dies Ihrer Organisation ist, klicken Sie auf **teilnehmen**, und klicken Sie dann auf **Fertig**.</span><span class="sxs-lookup"><span data-stu-id="b7098-170">When prompted to make sure this is your organization, click **Join**, and then click **Done**.</span></span>
    
6. <span data-ttu-id="b7098-171">Schließen Sie das Fenster mit den Einstellungen.</span><span class="sxs-lookup"><span data-stu-id="b7098-171">Close the settings window.</span></span>
    
<span data-ttu-id="b7098-172">Installieren Sie anschließend Office 2016 auf dem Computer WIN10.</span><span class="sxs-lookup"><span data-stu-id="b7098-172">Next, install Office 2016 on the WIN10 computer.</span></span>
  
1. <span data-ttu-id="b7098-p114">Öffnen Sie den Microsoft-Edge-Browser, und melden Sie sich mit den Anmeldeinformationen Ihres globaler Administrator Office 365-Portal. Hilfe finden Sie unter [Where zur Anmeldung bei Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="b7098-p114">Open the Microsoft Edge browser and sign in to the Office 365 portal with your global administrator account credentials. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="b7098-175">Klicken Sie auf der Registerkarte **Start von Microsoft Office** auf **Office 2016 installieren**.</span><span class="sxs-lookup"><span data-stu-id="b7098-175">On the **Microsoft Office Home** tab, click **Install Office 2016**.</span></span>
    
3. <span data-ttu-id="b7098-176">Klicken Sie mit dem, was tun Sie bei entsprechender Aufforderung auf **Ausführen**, und klicken Sie dann für die **Benutzerkontensteuerung**auf **Ja** .</span><span class="sxs-lookup"><span data-stu-id="b7098-176">When prompted with what to do, click **Run**, and then click **Yes** for **User Account Control**.</span></span>
    
4. <span data-ttu-id="b7098-p115">Warten Sie Office, um die Installation abzuschließen. Wenn Sie finden Sie unter **Sie alle festgelegt sind!**, klicken Sie zweimal auf **Schließen** .</span><span class="sxs-lookup"><span data-stu-id="b7098-p115">Wait for Office to complete its installation. When you see **You're all set!**, click **Close** twice.</span></span>
    
<span data-ttu-id="b7098-179">Abbildung 3 zeigt die erstellte Umgebung mit dem WIN10-Computer, der dem Azure AD-Mandanten Ihrer Office 365- und EMS-Abonnements beigetreten ist.</span><span class="sxs-lookup"><span data-stu-id="b7098-179">Figure 3 shows your resulting environment, which includes the WIN10 computer that has joined the Azure AD tenant of your Office 365 and EMS subscriptions.</span></span>
  
<span data-ttu-id="b7098-180">**Abbildung 3: Das Computerkonto WIN10, die dem Azure AD-Mandanten hinzufügen**</span><span class="sxs-lookup"><span data-stu-id="b7098-180">**Figure 3: Adding the WIN10 computer account to the Azure AD tenant**</span></span>

![Phase 4 der Microsoft 3656 Enterprise-Entwicklungs-/Testumgebung](images/20680f6a-f77e-4333-aaa9-f7cf5e4b0d03.png)
  
<span data-ttu-id="b7098-182">Sie sind jetzt bereit, Experimentieren mit zusätzlichen Features von [Microsoft 365 Enterprise](https://www.microsoft.com/microsoft-365/enterprise).</span><span class="sxs-lookup"><span data-stu-id="b7098-182">You are now ready to experiment with additional features of [Microsoft 365 Enterprise](https://www.microsoft.com/microsoft-365/enterprise).</span></span>
  
## <a name="next-steps"></a><span data-ttu-id="b7098-183">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="b7098-183">Next steps</span></span>

<span data-ttu-id="b7098-184">Anhand der folgenden weiteren Artikel erfahren Sie mehr über die Funktionen von Microsoft 365 Enterprise:</span><span class="sxs-lookup"><span data-stu-id="b7098-184">Use these additional articles to explore features of Microsoft 365 Enterprise:</span></span>
  
- [<span data-ttu-id="b7098-185">Hinzufügen von Informationsverwaltungsrichtlinien (MAM) für die mobile Anwendung</span><span class="sxs-lookup"><span data-stu-id="b7098-185">Add mobile application management (MAM) policies</span></span>](https://technet.microsoft.com/library/mt764059.aspx)
    
- [<span data-ttu-id="b7098-186">Registrieren Sie iOS und Android-Geräte</span><span class="sxs-lookup"><span data-stu-id="b7098-186">Enroll iOS and Android devices</span></span>](https://technet.microsoft.com/library/mt743077.aspx)
    
- [<span data-ttu-id="b7098-187">Konfigurieren und Testen von Advanced Security Management</span><span class="sxs-lookup"><span data-stu-id="b7098-187">Configure and test Advanced Security Management</span></span>](https://technet.microsoft.com/library/mt757250.aspx)
    
- [<span data-ttu-id="b7098-188">Konfigurieren und Testen der erweiterte Schutz</span><span class="sxs-lookup"><span data-stu-id="b7098-188">Configure and test Advanced Threat Protection</span></span>](https://technet.microsoft.com/library/mt490479.aspx)
    
## <a name="see-also"></a><span data-ttu-id="b7098-189">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="b7098-189">See Also</span></span>

- [<span data-ttu-id="b7098-190">Dokumentation zu Microsoft 365 Enterprise</span><span class="sxs-lookup"><span data-stu-id="b7098-190">Microsoft 365 Enterprise documentation</span></span>](https://docs.microsoft.com/microsoft-365-enterprise/)
- [<span data-ttu-id="b7098-191">Bereitstellen von Microsoft 365 Enterprise</span><span class="sxs-lookup"><span data-stu-id="b7098-191">Deploy Microsoft 365 Enterprise</span></span>](https://docs.microsoft.com/microsoft-365/enterprise/deploy-microsoft-365-enterprise)
- [<span data-ttu-id="b7098-192">Eine Microsoft-Cloud Dev/testumgebung</span><span class="sxs-lookup"><span data-stu-id="b7098-192">The One Microsoft Cloud dev/test environment</span></span>](the-one-microsoft-cloud-dev-test-environment.md)
- [<span data-ttu-id="b7098-193">Testumgebungsanleitungen (TLGs) zur Cloudakzeptanz</span><span class="sxs-lookup"><span data-stu-id="b7098-193">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
