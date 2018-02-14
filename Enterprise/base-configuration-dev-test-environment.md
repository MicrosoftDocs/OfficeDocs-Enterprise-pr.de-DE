---
title: Basiskonfiguration der Entwicklungs-/Testumgebung
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
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
ms.openlocfilehash: 04da1037dbebed9f9a5d2aa2fb37b03b88218839
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2018
---
# <a name="base-configuration-devtest-environment"></a>Basiskonfiguration der Entwicklungs-/Testumgebung

 **Zusammenfassung:** Erstellen Sie eine vereinfachte Intranet als einer Test-/-Umgebung in Microsoft Azure.
  
Dieser Artikel enthält eine schrittweise Anleitung zum Erstellen der folgenden Basiskonfiguration der Entwicklungs-/Testumgebung in Azure:
  
**Abbildung 1: Basiskonfiguration Test-/Umgebung**

![Phase 4 der Basiskonfiguration in Azure mit dem virtuellen Computer CLIENT1](images/25a010a6-c870-4690-b8f3-84421f8bc5c7.png)
  
Die Basiskonfiguration der Entwicklungs-/Testumgebung in Abbildung 1 besteht aus dem Unternehmensnetzwerk-Subnetz in einem auf die Cloud beschränkten virtuellen Azure-Netzwerk namens TestLab, das ein vereinfachtes privates Intranet simuliert, das mit dem Internet verbunden ist. Es enthält drei virtuelle Azure-Computer unter Windows Server 2016:
  
- DC1 ist als Intranet-Domänencontroller und DNS-Server (Domain Name System) konfiguriert.
    
- App1 ist als allgemeiner Anwendungs- und Webserver konfiguriert.
    
- 	CLIENT1 fungiert als Intranetclient.
    
Diese Konfiguration ermöglicht DC1, APP1, CLIENT1 und weiteren Computern im Unternehmensnetzwerk-Subnetz Folgendes:  
  
- Verbunden mit dem Internet Updates installiert, Zugriff auf Ressourcen im Internet in Echtzeit und öffentliche Cloud-Technologien wie Microsoft Office 365 und Azure-Diensten teilnehmen.
    
- 	Remoteverwaltung über Remotedesktopverbindungen von Ihrem Computer, der mit dem Internet oder dem Netzwerk Ihrer Organisation verbunden ist.
    
Sie können die resultierende Testumgebung zu folgenden Zwecken verwenden:
  
- Zur Anwendungsentwicklung und zum Testen.
    
- Die Erstkonfiguration eigener Entwurf einer erweiterten Test-Umgebung umfasst, die zusätzlicher virtueller Computer, Azure-Diensten oder andere Microsoft-Cloud-Angeboten wie etwa Office 365 und Sicherheit in Unternehmen + Mobilität.
    
Es gibt vier Phasen bei der Einrichtung der Basiskonfiguration für die Testumgebung in Azure:
  
1. 	Erstellen des virtuellen Netzwerks
    
2. 	Konfigurieren von DC1
    
3. 	Konfigurieren von APP1
    
4. 	Konfigurieren von CLIENT1
    
Wenn Sie nicht bereits über ein Azure-Abonnement verfügen, können Sie sich für eine kostenlose Testversion auf [Azure testen](https://azure.microsoft.com/pricing/free-trial/)signieren. Wenn Sie ein MSDN oder Visual Studio-Abonnement haben, finden Sie unter [monatliche Azure Credit für Abonnenten von Visual Studio](https://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/).
  
> [!NOTE]
> Virtuelle Computer in Azure ein einer laufenden Kosten entstehen, wenn sie ausgeführt werden. Diese Kosten für kostenlose Testversion, MSDN-Abonnement abgerechnet oder kostenpflichtiges Abonnement. Weitere Informationen zu den Kosten der Ausführung von Azure-virtuelle Computer finden Sie unter [Virtuelle Computer Preise Details](https://azure.microsoft.com/pricing/details/virtual-machines/) und [Azure Preise Rechner](https://azure.microsoft.com/pricing/calculator/). Um Kosten zu minimieren, finden Sie unter [Minimierung der Kosten für die Test Environment virtuellen Computern in Azure](base-configuration-dev-test-environment.md#mincost). 
  
![Testumgebungsanleitungen in der Microsoft Cloud](images/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
> [!TIP]
> Klicken Sie [hier](http://aka.ms/catlgstack), um eine visuelle Darstellung aller Artikel im Stapel der Testumgebungsanleitungen in der Microsoft Cloud zu erhalten.
  
## <a name="phase-1-create-the-virtual-network"></a>Phase 1: Erstellen des virtuellen Netzwerks

Starten Sie zunächst eine Azure PowerShell-Eingabeaufforderung.
  
> [!NOTE]
> Verwenden Sie den folgenden Befehl wird die neueste Version von Azure PowerShell. Finden Sie unter [Erste Schritte mit Azure PowerShell-Cmdlets](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/). 
  
Melden Sie sich mit dem folgenden Befehl bei Ihrem Azure-Konto an.
  
```
Login-AzureRMAccount
```

> [!TIP]
> Klicken Sie auf [hier](https://gallery.technet.microsoft.com/PowerShell-commands-for-ba957d3d) eine Textdatei ab, die PowerShell-Befehle in diesem Artikel enthält.
  
Rufen Sie den Namen Ihres Abonnements mithilfe des folgenden Befehls ab.
  
```
Get-AzureRMSubscription | Sort Name | Select Name
```

Tragen Sie Ihr Azure-Abonnement ein. Ersetzen Sie alles innerhalb der Anführungszeichen, einschließlich der Zeichen „<“ und „>“, durch den entsprechenden Namen.
  
```
$subscr="<subscription name>"
Get-AzureRmSubscription -SubscriptionName $subscr | Select-AzureRmSubscription
```

Im nächsten Schritt wird eine neue Ressourcengruppe für Ihre Basiskonfiguration des Testlabors erstellt. Verwenden Sie zum Ermitteln eines eindeutigen Ressourcengruppennamens diesen Befehl, mit dem die vorhandenen Ressourcengruppen aufgeführt werden.
  
```
Get-AzureRMResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

Erstellen Sie die neue Ressourcengruppe mit diesen Befehlen. Ersetzen Sie alles innerhalb der Anführungszeichen, einschließlich der Zeichen „<“ und „>“, durch die entsprechenden Namen.
  
```
$rgName="<resource group name>"
$locName="<location name, such as West US>"
New-AzureRMResourceGroup -Name $rgName -Location $locName
```

Im nächsten Schritt erstellen Sie das virtuelle Netzwerk „TestLab“, das das Unternehmensnetzwerk-Subnetz der Basiskonfiguration hostet, und schützen es mit einer Netzwerksicherheitsgruppe.
  
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

Dies ist Ihre aktuelle Konfiguration.
  
![Phase 1 der Basiskonfiguration in Azure mit dem virtuellen Netzwerk und Subnetz](images/0b5634fc-4e1c-469d-873d-97ed7e587411.png)
  
## <a name="phase-2-configure-dc1"></a>Phase 2: Konfigurieren von DC1

In dieser Phase erstellen Sie den virtuellen Computer DC1 und konfigurieren diesen als Domänencontroller für die Windows Server Active Directory-Domäne „corp.contoso.com“ sowie einen DNS-Server für die virtuellen Computer des virtuellen Netzwerks TestLab.
  
Zum Erstellen eines Azure-virtueller Computers für DC1 Geben Sie den Namen der Ressourcengruppe, und führen Sie diese Befehle an der Azure PowerShell-Eingabeaufforderung auf dem lokalen Computer.
  
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

Sie werden nach einem Benutzernamen und Kennwort für das lokale Administratorkonto auf DC1 gefragt. Verwenden Sie ein sicheres Kennwort, und notieren Sie den Namen und das Kennwort an einem sicheren Ort.
  
Stellen Sie dann eine Verbindung mit dem virtuellen Computer DC1 her.
  
### <a name="connect-to-dc1-using-local-administrator-account-credentials"></a>Herstellen einer Verbindung mit DC1 mithilfe von Anmeldeinformationen für das lokale Administratorkonto

1. Klicken Sie in der [Azure-Portal](https://portal.azure.com)auf **Ressourcengruppen >** <the name of your new resource group> **> DC1 > Connect**.
    
2. Öffnen Sie die DC1.rdp-Datei, die heruntergeladen wird, und klicken Sie auf **Verbinden**.
    
3. Geben Sie den Namen des DC1 lokalen Administratorkontos:
    
  - Für Windows 7:
    
    Klicken Sie auf **ein anderes Konto verwenden**, klicken Sie im Dialogfeld **Windows-Sicherheit** . Geben Sie im Feld **Benutzername** **DC1\\**[lokaler Administratorkontonamen].
    
  - Für Windows 8 oder Windows 10:
    
    Klicken Sie auf **Weitere Optionen**, und klicken Sie dann auf **ein anderes Konto verwenden**, klicken Sie im Dialogfeld **Windows-Sicherheit** . Geben Sie im Feld **Benutzername** **DC1\\**[lokaler Administratorkontonamen].
    
4. Geben Sie im Feld **Kennwort**das Kennwort für das lokale Administratorkonto ein, und klicken Sie dann auf **OK**.
    
5. Wenn Sie aufgefordert werden, klicken Sie auf **Ja**.
    
Im nächsten Schritt fügen Sie eine zusätzliche Datenträger als ein neues Volume mit dem Laufwerkbuchstaben F: mit diesem Befehl an einer Administratorebene Windows PowerShell-Eingabeaufforderung auf DC1 hinzu.
  
```
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

Konfigurieren Sie als Nächstes DC1 als Domänencontroller und DNS-Server für die Domäne „corp.contoso.com“. Führen Sie diese Befehle an einer Windows PowerShell-Eingabeaufforderung auf Administratorebene aus.
  
```
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSForest -DomainName corp.contoso.com -DatabasePath "F:\\NTDS" -SysvolPath "F:\\SYSVOL" -LogPath "F:\\Logs"
```

Sie müssen ein Administratorkennwort für den abgesicherten Modus angeben. Bewahren Sie das Kennwort an einem sicheren Ort auf.
  
Beachten Sie, dass der Abschluss dieser Befehle ein paar Minuten in Anspruch nehmen kann.
  
Stellen Sie nach dem Neustart von DC1 wieder eine Verbindung zum virtuellen DC1-Computer her.
  
### <a name="connect-to-dc1-using-domain-credentials"></a>Herstellen einer Verbindung mit DC1 mithilfe von Domänenanmeldeinformationen

1. Klicken Sie in der [Azure-Portal](https://portal.azure.com)auf **Ressourcengruppen >** <your resource group name> **> DC1 > Connect**.
    
2. Führen Sie die DC1.rdp-Datei, die heruntergeladen wird, und klicken Sie auf **Verbinden**.
    
3. Klicken Sie in der **Windows-Sicherheit**auf **ein anderes Konto verwenden**. Geben Sie im Feld **Benutzername** **CORP\\**[lokaler Administratorkontonamen].
    
4. Geben Sie im Feld **Kennwort**das Kennwort für das lokale Administratorkonto ein, und klicken Sie dann auf **OK**.
    
5. Wenn Sie aufgefordert werden, klicken Sie auf **Ja**.
    
Im nächsten Schritt erstellen Sie ein Benutzerkonto in Active Directory, das bei der Anmeldung an Mitgliedscomputern der Domäne CORP verwendet wird. Führen Sie diesen Befehl an einer Windows PowerShell-Eingabeaufforderung auf Administratorebene aus.
  
```
New-ADUser -SamAccountName User1 -AccountPassword (read-host "Set user password" -assecurestring) -name "User1" -enabled $true -PasswordNeverExpires $true -ChangePasswordAtLogon $false
```

Beachten Sie, dass Sie von dem Befehl aufgefordert werden, das Kennwort des Kontos „User1“ anzugeben. Da dieses Konto für Remotedesktopverbindungen für alle Mitgliedscomputer der Domäne CORP verwendet wird, sollten Sie ein sicheres Kennwort wählen. Notieren Sie das Kennwort des Kontos „User1“, und bewahren Sie es an einem sicheren Ort auf.
  
Konfigurieren Sie als Nächstes das neue Konto „User1“ als Unternehmensadministrator. Führen Sie diesen Befehl an der Windows PowerShell-Eingabeaufforderung auf Administratorebene aus.
  
```
Add-ADPrincipalGroupMembership -Identity "CN=User1,CN=Users,DC=corp,DC=contoso,DC=com" -MemberOf "CN=Enterprise Admins,CN=Users,DC=corp,DC=contoso,DC=com","CN=Domain Admins,CN=Users,DC=corp,DC=contoso,DC=com","CN=Schema Admins,CN=Users,DC=corp,DC=contoso,DC=com"
```

Schließen Sie die Remotedesktopsitzung mit DC1 und dann erneut eine Verbindung mit der CORP\\Konto User1 an.
  
Führen Sie als Nächstes den folgenden Befehl an einer Windows PowerShell-Eingabeaufforderung auf Administratorebene aus, um Datenverkehr für das Tool Ping zuzulassen.
  
```
Set-NetFirewallRule -DisplayName "File and Printer Sharing (Echo Request - ICMPv4-In)" -enabled True
```

Dies ist Ihre aktuelle Konfiguration.
  
![Phase 2 der Basiskonfiguration in Azure mit dem virtuellen Computer DC1](images/49069908-29c3-4d73-87f7-debbea067261.png)
  
## <a name="phase-3-configure-app1"></a>Phase 3: Konfigurieren von APP1

APP1 bietet Web- und Dateifreigabedienste.
  
Um einen virtuellen Azure-Computer für APP1 zu erstellen, geben Sie den Namen Ihrer Ressourcengruppe, den Azure-Speicherort und den Speicherkontonamen ein und führen diese Befehle in der Azure PowerShell-Befehlszeile auf Ihrem lokalen Computer aus.
  
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

Im nächsten Schritt stellen Sie eine Verbindung mit dem virtuellen Computer APP1 mit dem Kontonamen und Kennwort des lokalen Administratorkontos von APP1 her und öffnen dann eine Windows PowerShell-Eingabeaufforderung.
  
Zum Überprüfen der Namen Auflösung und Netzwerk-Kommunikation zwischen APP1 und DC1 führen Sie den Befehl **Ping dc1.corp.contoso.com** , und stellen Sie sicher, dass es vier Antworten gibt.
  
Verknüpfen Sie als Nächstes unter Verwendung der folgenden Befehle an der Windows PowerShell-Eingabeaufforderung den virtuellen Computer APP1 mit der Domäne CORP.
  
```
Add-Computer -DomainName corp.contoso.com
Restart-Computer
```

Beachten Sie, dass Sie die CORP angeben müssen\\User1 Domänenanmeldeinformationen Konto nach dem Ausführen des Befehls **Computer hinzufügen** .
  
Nach dem Neustart APP1 Herstellen einer Verbindung mit der CORP mit\\Konto User1 an, und öffnen Sie dann eine Administratorebene Windows PowerShell command Prompt.
  
Im nächsten Schritt richten Sie APP1 mit dem folgenden Befehl in der Windows PowerShell-Eingabeaufforderung auf APP1 als Webserver ein.
  
```
Install-WindowsFeature Web-WebServer -IncludeManagementTools
```

Erstellen Sie als Nächstes einen freigegebenen Ordner und eine Textdatei innerhalb des Ordners auf APP1 mit diesen PowerShell-Befehlen.
  
```
New-Item -path c:\\files -type directory
Write-Output "This is a shared file." | out-file c:\\files\\example.txt
New-SmbShare -name files -path c:\\files -changeaccess CORP\\User1
```

Dies ist Ihre aktuelle Konfiguration.
  
![Phase 3 der Basiskonfiguration in Azure mit dem virtuellen Computer APP1](images/92cfabb0-7f9d-4291-964d-ac32d52748d7.png)
  
## <a name="phase-4-configure-client1"></a>Phase 4: Konfigurieren von CLIENT1

CLIENT1 fungiert als normaler Laptop-, Tablet- oder Desktopcomputer im Intranet von Contoso.
  
> [!NOTE]
> Der folgende Befehl Set erstellt CLIENT1 mit Windows Server 2016 Datacenter, für alle Arten von Azure-Abonnements durchgeführt werden kann. Wenn Sie ein Visual Studio-basierte Azure-Abonnement verfügen, können Sie CLIENT1 ausgeführten Windows 10, Windows 8 oder Windows 7 mit dem [Azure-Portal](https://portal.azure.com)erstellen. 
  
Um einen virtuellen Azure-Computer für CLIENT1 zu erstellen, geben Sie den Namen Ihrer Ressourcengruppe, den Azure-Speicherort und den Speicherkontonamen ein und führen diese Befehle in der Azure PowerShell-Befehlszeile auf Ihrem lokalen Computer aus.
  
```
$rgName="<resource group name>"
$locName=(Get-AzureRmResourceGroup -Name $rgName).Location
$vnet=Get-AzureRMVirtualNetwork -Name TestLab -ResourceGroupName $rgName
$pip=New-AzureRMPublicIpAddress -Name CLIENT1-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic=New-AzureRMNetworkInterface -Name CLIENT1-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id
$vm=New-AzureRMVMConfig -VMName CLIENT1 -VMSize Standard_A1
$cred=Get-Credential -Message "Type the name and password of the local administrator account for CLIENT1."
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName CLIENT1 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name "CLIENT1-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "StandardLRS"
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

Im nächsten Schritt stellen Sie eine Verbindung mit dem virtuellen Computer CLIENT1 mit dem Kontonamen und Kennwort des lokalen Administratorkontos von CLIENT1 her und öffnen dann eine Windows PowerShell-Eingabeaufforderung auf Administratorebene.
  
Zum Überprüfen der Namen Auflösung und Netzwerk-Kommunikation zwischen CLIENT1 und DC1 führen Sie den Befehl **Ping dc1.corp.contoso.com** an einer Windows PowerShell-Eingabeaufforderung, und stellen Sie sicher, dass es vier Antworten gibt.
  
Verknüpfen Sie als Nächstes unter Verwendung der folgenden Befehle an der Windows PowerShell-Eingabeaufforderung den virtuellen Computer CLIENT1 mit der Domäne CORP.
  
```
Add-Computer -DomainName corp.contoso.com
Restart-Computer
```

Beachten Sie, dass Sie Ihre CORP angeben müssen\\User1 Domänenanmeldeinformationen Konto nach dem Ausführen des Befehls **Computer hinzufügen** .
  
Nach dem Neustart CLIENT1 Herstellen einer Verbindung mit der CORP mit\\User1 Kontoname und Kennwort, und öffnen Sie eine Windows PowerShell-Eingabeaufforderung auf Administratorebene.
  
Überprüfen Sie im nächsten Schritt, ob Sie von CLIENT1 aus auf Web- und Dateifreigaberessourcen auf APP1 zugreifen können.
  
### <a name="verify-client-access-to-app1"></a>Überprüfen des Clientzugriffs auf APP1

1. Klicken Sie im Server-Manager im Strukturbereich auf **Lokalen Server**.
    
2. Klicken Sie in den **Eigenschaften für CLIENT1** **auf** neben **Verstärkte Sicherheitskonfiguration für Internet Explorer**.
    
3. Klicken Sie in **Verstärkte Sicherheitskonfiguration für Internet Explorer**auf **aus** für **Administratoren** und **Benutzern**, und klicken Sie dann auf **OK**.
    
4. Klicken Sie auf der Startseite auf **Internet Explorer**, und klicken Sie dann auf **OK**.
    
5. Klicken Sie in der Adressleiste Geben Sie **http://app1.corp.contoso.com/**, und drücken Sie die EINGABETASTE. Sie sollten die standardmäßige Internet-Informationsdienste Webseite APP1 finden Sie unter.
    
6. Klicken Sie auf der Desktop-Taskleiste auf das Symbol für den Datei-Explorer.
    
7. Geben Sie in der Adressleiste ** \\ \\app1\\Dateien**, und drücken Sie dann die EINGABETASTE. Eine Ordneransicht mit dem Inhalt des freigegebenen Ordners sollte angezeigt werden.
    
8. Klicken Sie im freigegebenen Ordner **Dateien** Doppelklicken Sie auf die Datei **Example.txt** . Der Inhalt der Datei Example.txt sollte angezeigt werden.
    
9. Schließen Sie die **example.txt - Editor** und die **Dateien** freigegebene Ordner Windows.
    
Dies ist Ihre endgültige Konfiguration.
  
![Phase 4 der Basiskonfiguration in Azure mit dem virtuellen Computer CLIENT1](images/25a010a6-c870-4690-b8f3-84421f8bc5c7.png)
  
Die Basiskonfiguration in Azure kann nun für die Anwendungsentwicklung und zum Testen oder für die Erstellung zusätzlicher Testumgebungen verwendet werden. 
  
> [!TIP]
> Klicken Sie [hier](http://aka.ms/catlgstack), um eine visuelle Darstellung aller Artikel im Stapel der Testumgebungsanleitungen in der Microsoft Cloud zu erhalten.
  
## <a name="minimizing-the-costs-of-test-environment-virtual-machines-in-azure"></a>Minimierung der Kosten für virtuelle Computer der Testumgebung in Azure
<a name="mincost"> </a>

Um die Kosten für die Ausführung der virtuellen Computer der Testumgebung zu minimieren, können Sie eine der folgenden Aktionen ausführen:
  
- Erstellen Sie die Testumgebung, und führen Sie Ihre benötigten Tests und Demonstrationen so schnell wie möglich aus. Nach Abschluss des Vorgangs löschen Sie die Ressourcengruppe für die Testumgebung.
    
- 	Fahren Sie die virtuellen Computer der Testumgebung in den Zustand der aufgehobenen Zuordnung herunter.
    
Um die virtuellen Computer mit Azure PowerShell herunterzufahren, geben Sie den Ressourcengruppennamen ein und führen die folgenden Befehle aus.
  
```
$rgName="<your resource group name>"
Stop-AzureRMVM -ResourceGroupName $rgName -Name "CLIENT1" -Force
Stop-AzureRMVM -ResourceGroupName $rgName -Name "APP1" -Force
Stop-AzureRMVM -ResourceGroupName $rgName -Name "DC1" -Force
```

Damit Ihre virtuellen Computer einwandfrei funktionieren, wenn alle aus dem beendeten Zustand (Zuordnung aufgehoben) gestartet werden, sollten Sie sie in der folgenden Reihenfolge starten:
  
1. DC1
    
2. APP1
    
3. CLIENT1
    
Um die virtuellen Computer in der richtigen Reihenfolge mit Azure PowerShell zu starten, geben Sie den Ressourcengruppennamen ein und führen die folgenden Befehle aus.
  
```
$rgName="<your resource group name>"
Start-AzureRMVM -ResourceGroupName $rgName -Name "DC1"
Start-AzureRMVM -ResourceGroupName $rgName -Name "APP1"
Start-AzureRMVM -ResourceGroupName $rgName -Name "CLIENT1"
```

## <a name="see-also"></a>Weitere Artikel

<a name="mincost"> </a>

[Office 365-Entwicklungs-/Testumgebung](office-365-dev-test-environment.md)
  
[DirSync für die Office 365-Entwicklungs-/Testumgebung](dirsync-for-your-office-365-dev-test-environment.md)
  
[Cloud App Security für Ihre Office 365-Entwicklungs-/Testumgebung](cloud-app-security-for-your-office-365-dev-test-environment.md)
  
[Advanced Threat Protection für die Office 365-Entwicklungs-/Testumgebung](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
  
[Cloudakzeptanz und Hybridlösungen](cloud-adoption-and-hybrid-solutions.md)


