---
title: "Hoher Verfügbarkeit federated Authentifizierung Phase 4 Konfigurieren Web-Anwendungsproxys"
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
- Ent_O365_Hybrid
- Ent_O365_Hybrid_Top
ms.custom:
- DecEntMigration
- Ent_Solutions
ms.assetid: 1c903173-67cd-47da-86d9-d333972dda80
description: "Zusammenfassung: Konfigurieren der Web Application Proxy-Server für die hohe Verfügbarkeit Verbundauthentifizierung für Office 365 in Microsoft Azure."
ms.openlocfilehash: 02aeac727815a82c15cd602094e945a14ed551af
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2017
---
# <a name="high-availability-federated-authentication-phase-4-configure-web-application-proxies"></a>Hochverfügbarkeit der Verbundauthentifizierung, Phase 4: Konfigurieren von Webanwendungsproxys

 **Zusammenfassung:** Konfigurieren Sie die Web Application Proxy-Server für die hohe Verfügbarkeit Verbundauthentifizierung für Office 365 in Microsoft Azure.
  
In dieser Phase der Bereitstellung der hohen Verfügbarkeit für Verbundauthentifzierung für Office 365 in Azure-Infrastrukturdiensten erstellen Sie einen internen Lastenausgleich und zwei AD FS-Server.
  
Müssen Sie vor dem Verschieben auf in dieser Phase [hoher Verfügbarkeit federated Authentifizierung Phase 5: Konfigurieren von Verbundauthentifizierung für Office 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md). Finden Sie unter [Deploy hohe Verfügbarkeit Verbundauthentifizierung für Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) für alle Phasen.
  
## <a name="create-the-internet-facing-load-balancer-in-azure"></a>Erstellen des Lastenausgleichs mit Internetzugriff in Azure

Sie müssen einen Lastenausgleich mit Internetzugriff erstellen, damit Azure den eingehenden Clientauthentifizierungsverkehr aus dem Internet gleichmäßig unter den beiden Webanwendungsproxy-Servern verteilt.
  
> [!NOTE]
> Verwenden Sie den folgenden Befehl wird die neueste Version von Azure PowerShell. Finden Sie unter [Erste Schritte mit Azure PowerShell-Cmdlets](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/). 
  
Sobald Sie die Werte für Speicherort und Ressourcengruppe korrekt festgelegt haben, führen Sie den resultierenden Block über die Azure PowerShell-Eingabeaufforderung oder in PowerShell ISE aus.
  
> [!TIP]
> Eine Textdatei, die alle von PowerShell-Befehlen in diesem Artikel und Konfiguration Microsoft Excel-Arbeitsmappen, die generiert Ready-und-Los-PowerShell-Befehl Blöcke basierend auf Ihrer benutzerdefinierten Einstellungen enthält, finden Sie unter der [Federated-Authentifizierung für Office 365 in Azure Deployment Kit](https://gallery.technet.microsoft.com/Federated-Authentication-8a9f1664). 
  
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

Um die dem Lastenausgleich mit Internetzugriff zugewiesene öffentliche IP-Adresse anzuzeigen, führen Sie die folgenden Azure PowerShell-Eingabeaufforderung auf dem lokalen Computer aus:
  
```
Write-Host (Get-AzureRMPublicIpaddress -Name "WebProxyPublicIP" -ResourceGroup $rgName).IPAddress
```

## <a name="determine-your-federation-service-fqdn-and-create-dns-records"></a>Ermitteln des FQDN des Verbunddiensts und Erstellen von DNS-Einträgen

Sie müssen den DNS-Namen ermitteln, um den Namen des Verbunddiensts im Internet zu identifizieren. Azure AD Connect konfiguriert Office 365 in Phase 5 mit diesem Namen, der Teil der URL wird, die Office 365 an Clients sendet, die eine Verbindung herstellen, um ein Sicherheitstoken abzurufen. Ein Beispiel ist „fs.contoso.com“ („fs“ steht für den Verbunddienst).
  
Nachdem Sie den FQDN des Verbunddiensts ermittelt haben, erstellen Sie einen öffentlichen DNS-Eintrag für Domäne A für den FQDN des Verbunddiensts, der die öffentliche IP-Adresse des Azure-Lastenausgleichs mit Internetzugriff auflöst.
  
|**Name**|**Typ**|**TTL**|**Wert**|
|:-----|:-----|:-----|:-----|
|FQDN des Verbunddiensts  <br/> |A  <br/> |3600  <br/> |öffentliche IP-Adresse des Lastenausgleichssystems Azure Internetzugriff (mit dem Befehl **Write-Host** im vorherigen Abschnitt angezeigt) <br/> |
   
Hier ein Beispiel:
  
|**Name**|**Typ**|**TTL**|**Wert**|
|:-----|:-----|:-----|:-----|
|FS.contoso.com  <br/> |A  <br/> |3600  <br/> |131.107.249.117  <br/> |
   
Als Nächstes fügen Sie ein DNS-Adresseintrag zu dem privaten DNS-Namespace Ihrer Organisation hinzu, der den FQDN des Verbunddiensts in die private IP-Adresse auflöst, die dem internen Lastenausgleich für die AD FS-Server (Tabelle I, Element 4, Spalte „Wert“) zugewiesen ist.
  
## <a name="create-the-web-application-proxy-server-virtual-machines-in-azure"></a>Erstellen der virtuellen Computer des Webanwendungsproxy-Servers in Azure

Verwenden Sie die folgenden Azure PowerShell-Befehle, um die virtuellen Computer für die beiden Webanwendungsproxy-Server zu erstellen.  
  
Beachten Sie, dass die folgenden Azure PowerShell-Befehlssätze Werte aus den folgenden Tabellen verwenden:
  
- Tabelle M (für die virtuellen Computer)
    
- Tabelle R (für die Ressourcengruppen)
    
- Tabelle V (für die Einstellungen des virtuellen Netzwerks)
    
- Tabelle S (für das Subnetz)
    
- Tabelle I (für die statischen IP-Adressen)
    
- Tabelle A (für die Verfügbarkeitsgruppen)
    
Denken Sie daran, dass Sie die Tabelle M in definiert [hoher Verfügbarkeit federated Authentifizierung Phase 2: Konfigurieren von Domänencontrollern](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) und Tabellen R, V, S, ich und eine in [hoher Verfügbarkeit federated Authentifizierung Phase 1: Konfigurieren von Azure](high-availability-federated-authentication-phase-1-configure-azure.md).
  
Sobald Sie alle Werte korrekt festgelegt haben, führen Sie den resultierenden Block über die Azure PowerShell-Eingabeaufforderung oder in PowerShell ISE aus.
  
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
> Da diese virtuellen Maschinen für eine Intranetanwendung sind, sind keine öffentliche IP-Adresse oder eine Bezeichnung für DNS-Domäne zugewiesen und im Internet verfügbar gemacht. Dies bedeutet jedoch auch, dass Sie über das Portal Azure eine Verbindung ist nicht möglich. Die Option **Verbinden** ist nicht verfügbar, wenn Sie die Eigenschaften des virtuellen Computers anzeigen. Verwenden Sie die Remotedesktopverbindung Zubehör oder ein anderes Remotedesktop-Tool für die Verbindung mit ihrem privaten IP-Adresse oder Intranet DNS-Namen und die Anmeldeinformationen des lokalen Administratorkontos am virtuellen Computer.
  
Wenn Sie diese Phase erfolgreich abgeschlossen haben, sieht Ihre Konfiguration wie folgt aus. Für die Computernamen werden hier Platzhalter verwendet.
  
**Phase 4: Internet verbundenen laden zum Lastenausgleich und Web Application Proxy-Server für eine hohe Verfügbarkeit Verbundauthentifizierung-Infrastruktur in Azure**

![Phase 4 der hochverfügbaren Office 365-Verbundauthentifizierungsinfrastruktur in Azure mit Proxyservern der Webanwendung](images/7e03183f-3b3b-4cbe-9028-89cc3f195a63.png)
  
## <a name="next-step"></a>Nächster Schritt

Verwendung [hoher Verfügbarkeit federated Authentifizierung Phase 5: Konfigurieren von Verbundauthentifizierung für Office 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md) um den Vorgang fortzusetzen, konfigurieren diese Arbeitslast.
  
## <a name="see-also"></a>See Also

[Bereitstellen der Verbundauthentifizierung mit Hochverfügbarkeit für Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)
  
[Verbundidentität für Ihre Office 365-Entwicklungs-/Testumgebung](federated-identity-for-your-office-365-dev-test-environment.md)
  
[Cloudakzeptanz und Hybridlösungen](cloud-adoption-and-hybrid-solutions.md)

[Verbundidentität für Office 365](https://support.office.com/article/Understanding-Office-365-identity-and-Azure-Active-Directory-06a189e7-5ec6-4af2-94bf-a22ea225a7a9#bk_federated)


