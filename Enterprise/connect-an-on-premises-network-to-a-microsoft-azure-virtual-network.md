---
title: "Verbinden eines lokalen Netzwerks mit einem virtuellen Microsoft Azure-Netzwerk"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 1/13/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Hybrid
- Ent_O365_Hybrid_Top
- Ent_O365_Top
ms.custom:
- DecEntMigration
- Strat_O365_Enterprise
- Ent_Solutions
ms.assetid: 81190961-5454-4a5c-8b0e-6ae75b9fb035
description: "Zusammenfassung: Informationen zum Konfigurieren eines standortübergreifenden virtuellen Azure-Netzwerks für Office-Serverarbeitslasten."
---

# Verbinden eines lokalen Netzwerks mit einem virtuellen Microsoft Azure-Netzwerk

 **Zusammenfassung:** Informationen zum Konfigurieren eines standortübergreifenden virtuellen Azure-Netzwerks für Office-Serverarbeitslasten.
  
Ein standortübergreifendes virtuelles Azure-Netzwerk ist mit Ihrem lokalen Netzwerk verbunden, sodass Ihr Netzwerk durch Subnetze und virtuelle Computer, die in Azure-Infrastrukturdiensten gehostet werden, erweitert wird. Durch diese Verbindung können Computer in Ihrem lokalen Netzwerk direkt auf virtuelle Computer in Azure zugreifen und umgekehrt. Ein DirSync-Server beispielsweise, der auf einem virtuellen Azure-Computer ausgeführt wird, muss Kontenänderungen von lokalen Domänencontrollern abfragen und diese Änderungen mit dem Office 365-Abonnement synchronisieren. In diesem Artikel wird gezeigt, wie Sie ein standortübergreifendes virtuelles Azure-Netzwerk einrichten, das virtuelle Azure-Computer hosten kann.
  
Inhalt dieses Artikels:
  
- [Übersicht](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#Overview)
    
- [Planen des virtuellen Azure-Netzwerks](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#PlanningVirtual)
    
- [Fahrplan für die Bereitstellung](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#DeploymentRoadmap)
    
## Übersicht
<a name="Overview"> </a>

Die virtuellen Computer in Azure müssen nicht von Ihrer lokalen Umgebung isoliert sein. Um virtuelle Azure-Computer mit Ihren lokalen Netzwerkressourcen zu verbinden, müssen Sie ein standortübergreifendes virtuelles Azure-Netzwerk konfigurieren. Das folgende Diagramm zeigt die erforderlichen Komponenten zum Bereitstellen eines standortübergreifenden virtuellen Azure-Netzwerks mit einem virtuellen Computer in Azure.
  
![Lokales Netzwerk, das über eine Standort-zu-Standort-VPN-Verbindung mit Microsoft Azure verbunden ist](images/CP_ConnectOnPremisesNetworkToAzureVPN.png)
  
In diesem Diagramm sind zwei Netzwerke über ein Standort-zu-Standort-VPN (virtuelles privates Netzwerk) verbunden: das lokale Netzwerk und das virtuelle Azure-Netzwerk. Die Standort-zu-Standort-VPN-Verbindung wird von einem VPN-Gerät im lokalen Netzwerk und einem Azure-VPN-Gateway im virtuellen Azure-Netzwerk beendet. Das virtuelle Azure-Netzwerk weist virtuelle Computer auf. Von den virtuellen Computern im virtuellen Azure-Netzwerk ausgehender Netzwerkdatenverkehr wird an das VPN-Gateway weitergeleitet, das dann den Datenverkehr über die Standort-zu-Standort-VPN-Verbindung zum VPN-Gerät im lokalen Netzwerk weiterleitet. Anschließend leitet die Routinginfrastruktur des lokalen Netzwerks den Datenverkehr an sein Ziel.
  
Um die VPN-Verbindung zwischen dem virtuellen Azure-Netzwerk und Ihrem lokalen Netzwerk einzurichten, führen Sie die folgenden Schritte aus: 
  
1. **Lokal:** Definieren und erstellen Sie eine lokale Netzwerkroute für den Adressraum des virtuellen Azure-Netzwerks, die auf das lokale VPN-Gerät verweist.
    
2. **Microsoft Azure:** Richten Sie ein virtuelles Azure-Netzwerk mit einer Standort-zu-Standort-VPN-Verbindung ein. Dieser Artikel beschreibt nicht die Verwendung von[ExpressRoute](https://azure.microsoft.com/services/expressroute/).
    
3. **Lokal:** Konfigurieren Sie Ihr lokales VPN-Gerät auf Hardware- oder Softwarebasis zum Beenden der VPN-Verbindung, die IPsec (Internet Protocol Security) verwendet.
    
Nachdem Sie die Standort-zu-Standort VPN-Verbindung hergestellt haben, fügen Sie den Subnetzen des virtuellen Netzwerks virtuelle Azure-Computer hinzu.
  
## Planen des virtuellen Azure-Netzwerks
<a name="PlanningVirtual"> </a>

### Voraussetzungen
<a name="Prerequisites"> </a>

- Ein Azure-Abonnement. Informationen zu Azure-Abonnements finden Sie auf der [Seite zu Microsoft Azure-Abonnements](https://azure.microsoft.com/pricing/purchase-options/).
    
- Ein verfügbarer privater IPv4-Adressraum, der dem virtuellen Netzwerk und den Subnetzen zugewiesen wird, der über ausreichende Wachstumskapazität zur Unterstützung der jetzt und künftig benötigten virtuellen Computer verfügt.
    
- Ein verfügbares VPN-Gerät in Ihrem lokalen Netzwerk zum Beenden der Standort-zu-Standort-VPN-Verbindung, das die Anforderungen von IPsec erfüllt. Weitere Informationen finden Sie unter [Informationen zu VPN-Geräten für VPN-Gatewayverbindungen zwischen Standorten](https://go.microsoft.com/fwlink/p/?LinkId=393093).
    
- Änderungen an Ihrer Routinginfrastruktur, damit der an den Adressraum des virtuellen Azure-Netzwerks geleitete Datenverkehr an das VPN-Gerät weitergeleitet wird, das die Standort-zu-Standort-VPN-Verbindung hostet.
    
- Ein Webproxy, der Computern, die mit dem lokalen Netzwerk verbunden sind, und dem virtuellen Azure-Netzwerk Zugriff auf das Internet bietet.
    
### Entwurfsannahmen für die Lösungsarchitektur
<a name="DesignAssumptions"> </a>

Die folgende Liste enthält die Design-Entscheidungen, die für diese Lösungsarchitektur getroffen wurden.
  
- Diese Lösung verwendet ein einzelnes virtuelles Azure-Netzwerk mit einer einzelnen Standort-zu-Standort-VPN-Verbindung. Das virtuelle Azure-Netzwerk hostet ein einzelnes Subnetz, das mehrere virtuelle Computer enthalten kann.
    
- Sie können RRAS (Routing- und RAS-Dienst) in Windows Server 2016 oder Windows Server 2012 verwenden, um eine IPsec-Standort-zu-Standort-VPN-Verbindung zwischen dem lokalen Netzwerk und dem virtuellen Azure-Netzwerk herzustellen. Sie können auch andere Optionen wie Cisco- und Juniper Networks-VPN-Geräte wählen.
    
- Das lokale Netzwerk kann weiterhin Netzwerkdienste wie Windows Server Active Directory (AD), Domain Name System (DNS) und Proxy-Server enthalten. Je nach Ihren Anforderungen kann es von Vorteil sein, einige der Netzwerkressourcen in dem virtuellen Azure-Netzwerk zu betreiben.
    
Bestimmen Sie bei einem vorhandenen virtuellen Azure-Netzwerk mit einem oder mehreren Subnetzen, ob es genügend Adressraum für ein weiteres Subnetz zum Hosten Ihrer erforderlichen virtuellen Computer den Anforderungen entsprechend gibt. Wenn Sie keinen verbleibenden Adressraum für ein weiteres Subnetz haben, erstellen Sie ein zusätzliches virtuelles Netzwerk, das über eine eigene Standort-zu-Standort-zu-Standort-VPN-Verbindung verfügt.
  
### Planen der Änderungen der Routinginfrastruktur für das virtuelle Azure-Netzwerk
<a name="routing"> </a>

Sie müssen Ihre lokale Routinginfrastruktur für das Weiterleiten von Datenverkehr, der für den Adressraum des virtuellen Azure-Netzwerk bestimmt ist, an das lokale VPN-Gerät konfigurieren, auf dem die Standort-zu-Standort-zu-Standort-VPN-Verbindung gehostet wird.
  
Die genaue Methode zum Aktualisieren Ihrer Routinginfrastruktur hängt von der Verwaltung der Routinginformationen ab. Die sind die Möglichkeiten:
  
- Die Routingtabelle wird abhängig von manueller Konfiguration aktualisiert.
    
- Aktualisierungen der Routingtabelle basieren auf Routingprotokollen, wie z. B. Routing Information Protocol (RIP) oder Open Shortest Path First (OSPF).
    
Wenden Sie sich an Ihre Routingspezialisten, um sicherzustellen, dass der Datenverkehr an das virtuelle Azure-Netzwerk an das lokale VPN-Gerät weitergeleitet wird.
  
### Planen von Firewallregeln für ein- und ausgehenden Datenverkehr des lokalen VPN-Geräts
<a name="firewall"> </a>

Wenn sich Ihr VPN-Gerät in einem Umkreisnetzwerk mit einer Firewall zwischen dem Umkreisnetzwerk und dem Internet befindet, müssen Sie möglicherweise die Firewall mit den folgenden Regeln konfigurieren, um die Standort-zu-Standort-VPN-Verbindung zuzulassen.
  
- Datenverkehr an das VPN-Gerät (eingehend aus dem Internet):
    
  - Ziel-IP-Adresse des VPN-Geräts und IP-Protokoll 50
    
  - Ziel-IP-Adresse des VPN-Geräts und UDP-Zielport 500
    
  - Ziel-IP-Adresse des VPN-Geräts und UDP-Zielport 4500
    
- Datenverkehr von dem VPN-Gerät (ausgehend an das Internet):
    
  - Quell-IP-Adresse des VPN-Geräts und IP-Protokoll 50
    
  - Quell-IP-Adresse des VPN-Geräts und UDP-Quellport 500
    
  - Quell-IP-Adresse des VPN-Geräts und UDP-Quellport 4500
    
### Planen des privaten IP-Adressbereichs des virtuellen Azure-Netzwerks
<a name="IPAddresses"> </a>

Der private IP-Adressbereich des virtuellen Azure-Netzwerks muss in der Lage sein, von Azure verwendete Adressen aufzunehmen, um das virtuelle Netzwerk mit mindestens einem Subnetz zu hosten, das genügend Adressen für Ihre virtuellen Azure-Computer bietet.
  
Um die Anzahl der Adressen zu bestimmen, die für das Subnetz erforderlich sind, zählen Sie die Anzahl der virtuellen Computer, die Sie aktuell benötigen, schätzen Sie künftiges Wachstum ab, und verwenden Sie dann die folgende Tabelle, um die Größe des Subnetzes zu ermitteln.
  
|**Anzahl der benötigten virtuellen Computer**|**Anzahl der erforderlichen Hostbits**|**Größe des Subnetzes**|
|:-----|:-----|:-----|
|1-3  <br/> |3  <br/> |/29  <br/> |
|4-11  <br/> |4  <br/> |/28  <br/> |
|12-27  <br/> |5  <br/> |/27  <br/> |
|28-59  <br/> |6  <br/> |/26  <br/> |
|60-123  <br/> |7  <br/> |/25  <br/> |
   
### Arbeitsblatt für die Planung der Konfiguration des virtuellen Azure-Netzwerks
<a name="worksheet"> </a>

Vor dem Erstellen eines virtuellen Azure-Netzwerks zum Hosten von virtuellen Computern müssen Sie die erforderlichen Einstellungen in den folgenden Tabellen festlegen.
  
Füllen Sie für die Einstellungen des virtuellen Netzwerks Tabelle V aus.
  
 **Tabelle V: Konfiguration eines standortübergreifenden virtuellen Netzwerks**
  
|**Element**|**Configuration-Element**|**Beschreibung**|**Wert**|
|:-----|:-----|:-----|:-----|
|1.  <br/> |Name des virtuellen Netzwerks  <br/> |Ein Name, der dem virtuellen Azure-Netzwerk zugewiesen wird (z. B. DirSyncNet)  <br/> |__________________  <br/> |
|2.  <br/> |Adresse des virtuellen Netzwerks  <br/> |Das Azure-Rechenzentrum, das das virtuelle Netzwerk enthalten soll (z. B. USA (Westen)).  <br/> |__________________  <br/> |
|3.  <br/> |IP-Adresse des VPN-Geräts  <br/> |Die öffentliche IPv4-Adresse der Schnittstelle des VPN-Geräts im Internet. Fragen Sie Ihre IT-Abteilung nach dieser Adresse.  <br/> |__________________  <br/> |
|4.  <br/> |Adressraum des virtuellen Netzwerks  <br/> |Der Adressraum (in einem einzigen privaten Adresspräfix definiert) für das virtuelle Netzwerk. Fragen Sie Ihre IT-Abteilung nach diesem Adressraum. Der Adressraum sollte im CIDR-Format (Classless Interdomain Routing, klassenloses domänenübergreifendes Routing) angegeben werden, auch Netzwerkpräfixformat genannt. Beispiel: 10.24.64.0/20.  <br/> |__________________  <br/> |
|5.  <br/> |Gemeinsam verwendeter IPsec-Schlüssel  <br/> |Eine aus 32 zufällig ausgewählten alphanumerischen Zeichen bestehende Zeichenfolge, die zur Authentifizierung beider Seiten der Standort-zu-Standort-VPN-Verbindung verwendet wird. Fragen Sie Ihre IT- oder Sicherheitsabteilung nach diesem Schlüsselwert, und bewahren Sie diesen an einem sicheren Ort auf. Alternativ finden Sie weitere Informationen dazu unter [Create a random string for an IPsec preshared key](https://social.technet.microsoft.com/wiki/contents/articles/32330.create-a-random-string-for-an-ipsec-preshared-key.aspx).  <br/> |__________________  <br/> |
   
Füllen Sie für das Subnetz dieser Lösung Tabelle S aus.
  
- Legen Sie für das erste Subnetz einen 28-Bit-Adressraum (mit einer /28-Präfixlänge) für das Azure-Gatewaysubnetz fest. Informationen zum Bestimmen dieses Adressraums finden Sie unter [Calculating the gateway subnet address space for Azure virtual networks](https://blogs.technet.microsoft.com/solutions_advisory_board/2016/12/01/calculating-the-gateway-subnet-address-space-for-azure-virtual-networks/).
    
- Geben Sie für das zweite Subnetz einen Anzeigenamen, einen auf dem Adressraum des virtuellen Netzwerks basierenden einzelnen IP-Adressraum und einen beschreibenden Zweck an.
    
Fragen Sie Ihre IT-Abteilung nach diesen Adressräumen, die aus dem Adressraum des virtuellen Netzwerks bestimmt werden. Beide Adressräume muss im CIDR-Format eingegeben werden.
  
 **Tabelle S: Subnetze im virtuellen Netzwerk**
  
|**Element**|**Subnetzname**|**Subnetzadressraum**|**Zweck**|
|:-----|:-----|:-----|:-----|
|1.  <br/> |GatewaySubnet  <br/> |_____________________________  <br/> |Das von dem Azure-Gateway verwendete Subnetz.  <br/> |
|2.  <br/> |_____________________________  <br/> |_____________________________  <br/> |_____________________________  <br/> |
   
Füllen Sie für die lokalen DNS-Server, die von den virtuellen Computern im virtuellen Netzwerk verwendet werden sollen, Tabelle D aus. Geben Sie jedem DNS-Server einen Anzeigenamen und eine einzelne IP-Adresse. Der Anzeigename muss nicht mit dem Hostnamen oder dem Computernamen des DNS-Servers übereinstimmen. Auch wenn hierfür nur zwei Einträge vorgesehen sind, können Sie noch weitere hinzufügen. Erarbeiten Sie diese Liste gemeinsam mit Ihrer IT-Abteilung.
  
 **Tabelle D: Lokale DNS-Server**
  
|**Element**|**Anzeigename des DNS-Servers**|**IP-Adresse des DNS-Servers**|
|:-----|:-----|:-----|
|1.  <br/> |_____________________________  <br/> |_____________________________  <br/> |
|2.  <br/> |_____________________________  <br/> |_____________________________  <br/> |
   
Um Pakete aus dem virtuellen Azure-Netzwerk an das Organisationsnetzwerk über die Standort-zu-Standort-VPN-Verbindung weiterzuleiten, müssen Sie das virtuelle Netzwerk mit einem lokalen Netzwerk konfigurieren. Dieses lokale Netzwerk enthält eine Liste der Adressräume (im CIDR-Format) für alle Standorte in Ihrem lokalen Organisationsnetzwerk, die die virtuellen Computer im virtuellen Netzwerk erreichen müssen. Dies können alle Standorte im lokalen Netzwerk oder nur eine Teilmenge sein. Die Liste der Adressräume, die Ihr lokales Netzwerk definiert, muss eindeutig sein und darf nicht mit den für andere virtuelle Netzwerke verwendeten Adressräumen überlappen.
  
Für die Teilmenge der Adressräume für das lokale Netzwerk füllen Sie Tabelle L aus. Auch wenn hierfür nur drei Einträge vorgesehen sind, können Sie noch weitere hinzufügen. Erarbeiten Sie diese Liste gemeinsam mit Ihrer IT-Abteilung.
  
 **Tabelle L: Adresspräfixe für das lokale Netzwerk**
  
|**Element**|**Adressraum des lokalen Netzwerks**|
|:-----|:-----|
|1.  <br/> |_____________________________  <br/> |
|2.  <br/> |_____________________________  <br/> |
|3.  <br/> |_____________________________  <br/> |
   
## Fahrplan für die Bereitstellung
<a name="DeploymentRoadmap"> </a>

Das Erstellen des standortübergreifenden virtuellen Netzwerks und das Hinzufügen virtueller Computer in Azure umfasst drei Phasen:
  
- Phase 1: Vorbereiten Ihres lokalen Netzwerks.
    
- Phase 2: Erstellen des standortübergreifenden virtuellen Netzwerks in Azure.
    
- Phase 3 (optional): Hinzufügen virtueller Computer.
    
### Phase 1: Vorbereiten Ihres lokalen Netzwerks
<a name="Phase1"> </a>

Sie müssen Ihr lokales Netzwerk mit einer Route konfigurieren, die auf den Router am Rand des lokalen Netzwerks verweist und letztendlich für den Adressraum des virtuellen Netzwerks bestimmten Datenverkehr an diesen Router leitet. Wenden Sie sich an Ihren Netzwerkadministrator, um zu erfahren, wie die Route der Routing-Infrastruktur Ihres lokalen Netzwerks hinzugefügt wird.
  
Nachfolgend sehen Sie die daraus resultierende Konfiguration.
  
![Das lokale Netzwerk muss über eine Route für den Adressraum des virtuellen Netzwerks verfügen, der auf das VPN-Gerät zeigt.](images/90bab36b-cb60-4ea5-81d5-4737b696d41c.png)
  
### Phase 2: Erstellen des standortübergreifenden virtuellen Netzwerks in Azure
<a name="Phase2"> </a>

Öffnen Sie zunächst eine Azure PowerShell-Eingabeaufforderung. Informationen zum Vorgehen, wenn Sie Azure PowerShell nicht installiert haben, finden Sie unter [Get started with Azure PowerShell cmdlets](https://docs.microsoft.com/powershell/azureps-cmdlets-docs/).
  
> [!NOTE]
> Diese Befehle gelten für Azure PowerShell 1.0 und höher. Um eine Textdatei zu erhalten, die alle PowerShell-Befehle in diesem Artikel enthält, klicken Sie [hier](https://gallery.technet.microsoft.com/scriptcenter/PowerShell-commands-for-5c5a7c19). 
  
Melden Sie sich dann bei Ihrem Azure-Konto mit diesem Befehl an.
  
```
Login-AzureRMAccount
```

Rufen Sie den Namen Ihres Abonnements mithilfe des folgenden Befehls ab.
  
```
Get-AzureRMSubscription | Sort SubscriptionName | Select SubscriptionName
```

Legen Sie Ihr Azure-Abonnement mit diesen Befehlen fest. Ersetzen Sie alles innerhalb der Anführungszeichen, einschließlich der Zeichen „<" und „>", durch den entsprechenden Abonnementnamen.
  
```
$subscrName="<subscription name>"
Select-AzureRMSubscription -SubscriptionName $subscrName -Current
```

Im nächsten Schritt wird eine neue Ressourcengruppe für das virtuelle Netzwerk erstellt. Verwenden Sie zum Ermitteln eines eindeutigen Ressourcengruppennamens diesen Befehl, mit dem die vorhandenen Ressourcengruppen aufgeführt werden.
  
```
Get-AzureRMResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

Erstellen Sie die neue Ressourcengruppe mit diesen Befehlen.
  
```
$rgName="<resource group name>"
$locName="<Table V - Item 2 - Value column>"
New-AzureRMResourceGroup -Name $rgName -Location $locName

```

Für Ressourcen-Manager-basierte virtuelle Computer ist ein Ressourcen-Manager-basiertes Speicherkonto erforderlich. Sie müssen einen global eindeutigen Namen für Ihr Speicherkonto auswählen, der nur Kleinbuchstaben und Ziffern enthält. Sie können diesen Befehl zum Auflisten vorhandener Speicherkonten verwenden.
  
```
Get-AzureRMStorageAccount | Sort Name | Select Name
```

Verwenden Sie diesen Befehl, um zu testen, ob ein vorgeschlagener Speicherkontoname eindeutig ist.
  
```
Get-AzureRmStorageAccountNameAvailability "<proposed name>"
```

Führen Sie zum Erstellen eines neuen Speicherkontos diese Befehle aus.
  
```
$rgName="<your new resource group name>"
$locName="<the location of your new resource group>"
$saName="<unique storage account name>"
New-AzureRMStorageAccount -Name $saName -ResourceGroupName $rgName -Type Standard_LRS -Location $locName
```

Erstellen Sie als Nächstes das virtuelle Azure-Netzwerk.
  
```
# Fill in the variables from previous values and from Tables V, S, and D
$rgName="<name of your new resource group>"
$locName="<Azure location of your new resource group>"
$vnetName="<Table V - Item 1 - Value column>"
$vnetAddrPrefix="<Table V - Item 4 - Value column>"
$gwSubnetPrefix="<Table S - Item 1 - Subnet address space column>"
$SubnetName="<Table S - Item 2 - Subnet name column>"
$SubnetPrefix="<Table S - Item 2 - Subnet address space column>"
$dnsServers=@( "<Table D - Item 1 - DNS server IP address column>", "<Table D - Item 2 - DNS server IP address column>" )

# Get the shortened version of the location
$rg=Get-AzureRmResourceGroup -Name $rgName
$locShortName=$rg.Location

# Create the Azure virtual network and a network security group that allows incoming remote desktop connections to the subnet that is hosting virtual machines
$gatewaySubnet=New-AzureRmVirtualNetworkSubnetConfig -Name "GatewaySubnet" -AddressPrefix $gwSubnetPrefix
$vmSubnet=New-AzureRMVirtualNetworkSubnetConfig -Name $SubnetName -AddressPrefix $SubnetPrefix
New-AzureRMVirtualNetwork -Name $vnetName -ResourceGroupName $rgName -Location $locName -AddressPrefix $vnetAddrPrefix -Subnet $gatewaySubnet,$vmSubnet -DNSServer $dnsServers
$rule1=New-AzureRMNetworkSecurityRuleConfig -Name "RDPTraffic" -Description "Allow RDP to all VMs on the subnet" -Access Allow -Protocol Tcp -Direction Inbound -Priority 100 -SourceAddressPrefix Internet -SourcePortRange * -DestinationAddressPrefix * -DestinationPortRange 3389
New-AzureRMNetworkSecurityGroup -Name $SubnetName -ResourceGroupName $rgName -Location $locShortName -SecurityRules $rule1
$vnet=Get-AzureRMVirtualNetwork -ResourceGroupName $rgName -Name $vnetName
$nsg=Get-AzureRMNetworkSecurityGroup -Name $SubnetName -ResourceGroupName $rgName
Set-AzureRMVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $SubnetName -AddressPrefix $SubnetPrefix -NetworkSecurityGroup $nsg
```

Nachfolgend sehen Sie die daraus resultierende Konfiguration.
  
![Das virtuelle Netzwerk ist noch nicht mit dem lokalen Netzwerk verbunden.](images/54a37782-a6cc-4d48-b38d-73e128b44a82.png)
  
Verwenden Sie anschließend diese Befehle zum Erstellen der Gateways für die Standort-zu-Standort-VPN-Verbindung.
  
```
# Fill in the variables from previous values and from Tables V and L
$vnetName="<Table V - Item 1 - Value column>"
$localGatewayIP="<Table V - Item 3 - Value column>"
$localNetworkPrefix=@( <comma-separated, double-quote enclosed list of the local network address prefixes from Table L, example: "10.1.0.0/24", "10.2.0.0/24"> )
$vnetConnectionKey="<Table V - Item 5 - Value column>"
$vnet=Get-AzureRMVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
# Attach a virtual network gateway to a public IP address and the gateway subnet
$publicGatewayVipName="PublicIPAddress"
$vnetGatewayIpConfigName="PublicIPConfig"
New-AzureRMPublicIpAddress -Name $vnetGatewayIpConfigName -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$publicGatewayVip=Get-AzureRMPublicIpAddress -Name $vnetGatewayIpConfigName -ResourceGroupName $rgName
$vnetGatewayIpConfig=New-AzureRMVirtualNetworkGatewayIpConfig -Name $vnetGatewayIpConfigName -PublicIpAddressId $publicGatewayVip.Id -SubnetId $vnet.Subnets[0].Id
# Create the Azure gateway
$vnetGatewayName="AzureGateway"
$vnetGateway=New-AzureRMVirtualNetworkGateway -Name $vnetGatewayName -ResourceGroupName $rgName -Location $locName -GatewayType Vpn -VpnType RouteBased -IpConfigurations $vnetGatewayIpConfig
# Create the gateway for the local network
$localGatewayName="LocalNetGateway"
$localGateway=New-AzureRMLocalNetworkGateway -Name $localGatewayName -ResourceGroupName $rgName -Location $locName -GatewayIpAddress $localGatewayIP -AddressPrefix $localNetworkPrefix
# Create the Azure virtual network VPN connection
$vnetConnectionName="S2SConnection"
$vnetConnection=New-AzureRMVirtualNetworkGatewayConnection -Name $vnetConnectionName -ResourceGroupName $rgName -Location $locName -ConnectionType IPsec -SharedKey $vnetConnectionKey -VirtualNetworkGateway1 $vnetGateway -LocalNetworkGateway2 $localGateway
```

Nachfolgend sehen Sie die daraus resultierende Konfiguration.
  
![Das virtuelle Netzwerk verfügt jetzt über ein Gateway.](images/82dd66b2-a4b7-48f6-a89b-cfdd94630980.png)
  
Konfigurieren Sie im nächsten Schritt das lokale VPN-Gerät zum Herstellen einer Verbindung mit dem Azure-VPN-Gateway. Weitere Informationen finden Sie unter [Informationen zu VPN-Geräten für Standort-zu-Standort-Verbindungen im virtuellen Azure-Netzwerk](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpn-devices).
  
Zum Konfigurieren Ihres VPN-Geräts benötigen Sie Folgendes:
  
- Die öffentliche IPv4-Adresse des Azure-VPN-Gateways für das virtuelle Netzwerk. Verwenden Sie den Befehl **Get-AzureRMPublicIpAddress -Name $vnetGatewayIpConfigName -ResourceGroupName $rgName** zum Anzeigen dieser Adresse.
    
- Der vorinstallierte IPsec-Schlüssel für die Standort-zu-Standort-VPN-Verbindung (Tabelle V - Element 5 - Spalte „Wert").
    
Nachfolgend sehen Sie die daraus resultierende Konfiguration.
  
![Das virtuelle Netzwerk ist nun mit dem lokalen Netzwerk verbunden.](images/6379c423-4f22-4453-941b-7ff32484a0a5.png)
  
### Phase 3 (optional): Hinzufügen virtueller Computer.
<a name="Phase2"> </a>

Erstellen Sie die virtuellen Computer, die Sie in Azure benötigen. Weitere Informationen finden Sie unter [Erstellen Ihres ersten virtuellen Windows-Computers im Azure-Portal](https://go.microsoft.com/fwlink/p/?LinkId=393098).
  
Verwenden Sie die folgenden Einstellungen:
  
- Wählen Sie im Bereich **Grundlagen** das gleiche Abonnement und die Ressourcengruppe als virtuelles Netzwerk aus. Bewahren Sie den Benutzernamen und das Kennwort an einem sicheren Ort auf. Sie benötigen diese Informationen später für die Anmeldung auf dem virtuellen Computer.
    
- Wählen Sie im Bereich **Größe** die gewünschte Größe aus.
    
- Wählen Sie im Bereich **Einstellungen** im Abschnitt **Speicher** den Speichertyp **Standard** und das mit Ihrem virtuellen Netzwerk eingerichtete Speicherkonto aus. Wählen Sie im Abschnitt **Netzwerk** den Namen des virtuellen Netzwerks und das Subnetz zum Hosten virtueller Computer (nicht das Gateway-Subnetz). Alle anderen Einstellungen bleiben bei ihren Standardwerten.
    
Überprüfen Sie, ob der virtuelle Computer das DNS korrekt verwendet, indem Sie Ihr internes DNS prüfen, um sicherzustellen, dass die Adresse (A)-Einträge für Ihren neuen virtuellen Computer hinzugefügt wurden. Für den Zugriff auf das Internet müssen Ihre virtuellen Azure-Computer für die Verwendung des Proxyservers Ihres lokalen Netzwerks konfiguriert werden. Fragen Sie den Netzwerkadministrator nach zusätzlichen Konfigurationsschritten, die auf dem Server erfolgen müssen.
  
Nachfolgend sehen Sie die daraus resultierende Konfiguration.
  
![Das virtuelle Netzwerk hostet jetzt virtuelle Computer, auf die vom lokalen Netzwerk zugegriffen werden kann.](images/86ab63a6-bfae-4f75-8470-bd40dff123ac.png)
  
## See Also
<a name="DeploymentRoadmap"> </a>

#### 

[Cloudakzeptanz und Hybridlösungen](cloud-adoption-and-hybrid-solutions.md)
  
[Bereitstellen der Office 365-Verzeichnissynchronisierung (DirSync) in Microsoft Azure](deploy-office-365-directory-synchronization-dirsync-in-microsoft-azure.md)
#### 

[Erstellen von virtuellen Computern](https://go.microsoft.com/fwlink/p/?LinkId=393098)
  
[Informationen zu VPN-Geräten für Standort-zu-Standort-Verbindungen im virtuellen Azure-Netzwerk](https://azure.microsoft.com/documentation/articles/vpn-gateway-about-vpn-devices/)
  
[Installieren und Konfigurieren von Azure PowerShell](https://azure.microsoft.com/documentation/articles/powershell-install-configure/#how-to-install-azure-powershell)

