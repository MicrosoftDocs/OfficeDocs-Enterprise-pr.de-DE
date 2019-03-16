---
title: Hochverfügbarkeit der Verbundauthentifizierung, Phase 1 Konfigurieren von Azure
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 03/15/2019
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Solutions
ms.assetid: 91266aac-4d00-4b5f-b424-86a1a837792c
description: 'Zusammenfassung: Konfigurieren der Microsoft Azure-Infrastruktur zum Hosten der Verbundauthentifizierung mit hoher Verfügbarkeit für Ihr Office 365.'
ms.openlocfilehash: a57085ef066aeaf14235b8901c045911ef97ceed
ms.sourcegitcommit: b85d3db24385d7e0bdbfb0d4499174ccd7f573bd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/15/2019
ms.locfileid: "30650158"
---
# <a name="high-availability-federated-authentication-phase-1-configure-azure"></a>Hochverfügbarkeit der Verbundauthentifizierung, Phase 1: Konfigurieren von Azure

 **Zusammenfassung:** Konfigurieren der Microsoft Azure-Infrastruktur zum Hosten der Verbundauthentifizierung mit hoher Verfügbarkeit für Ihr Office 365.
  
In dieser Phase erstellen Sie die Ressourcengruppen, das virtuelle Netzwerk (VNet) und Verfügbarkeits Sätze in Azure, die die virtuellen Computer in den Phasen 2, 3 und 4 hosten werden. Sie müssen diese Phase abschließen, bevor Sie mit der [hoch Verfügbarkeits Verbundauthentifizierung, Phase 2: Konfigurieren von Domänencontrollern](high-availability-federated-authentication-phase-2-configure-domain-controllers.md), fortfahren. Eine Übersicht über alle Phasen finden Sie unter [Bereitstellen der Verbundauthentifizierung mit Hochverfügbarkeit für Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md).
  
Azure muss mit den folgenden grundlegenden Komponenten eingerichtet werden:
  
- Ressourcengruppen
    
- Ein standortübergreifendes virtuelles Azure-Netzwerk (VNet) mit Subnetzen für das Hosting der virtuellen Computer in Azure
    
- Netzwerksicherheitsgruppen zur Isolierung der Subnetze
    
- Verfügbarkeitsgruppen
    
## <a name="configure-azure-components"></a>Konfigurieren der Azure-Komponenten

Bevor Sie mit dem Konfigurieren von Azure-Komponenten beginnen, füllen Sie die folgenden Tabellen aus. Um Sie bei den Verfahren zum Konfigurieren von Azure zu unterstützen, Drucken Sie diesen Abschnitt, und notieren Sie sich die benötigten Informationen, oder kopieren Sie diesen Abschnitt in ein Dokument, und füllen Sie es aus. Füllen Sie für die Einstellungen des VNet die Tabelle V aus.
  
|**Item**|**Konfigurationseinstellung**|**Beschreibung**|**Wert**|
|:-----|:-----|:-----|:-----|
|1.  <br/> |VNet-Name  <br/> |Ein Name, der dem VNet zugewiesen wird (z. B. FedAuthNet).  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|2.  <br/> |VNet-Standort  <br/> |Das regionale Azure-Rechenzentrum, in dem sich das virtuelle Netzwerk befinden soll  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|3.  <br/> |IP-Adresse des VPN-Geräts  <br/> |Die öffentliche IPv4-Adresse der Schnittstelle des VPN-Geräts im Internet  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|4.  <br/> |VNet-Adressraum  <br/> |Der Adressraum für das virtuelle Netzwerk (Fragen Sie Ihre IT-Abteilung nach diesem Adressraum.)  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|5.  <br/> |Gemeinsam verwendeter IPsec-Schlüssel  <br/> |Eine aus 32 zufällig ausgewählten alphanumerischen Zeichen bestehende Zeichenfolge, die zur Authentifizierung beider Seiten der Standort-zu-Standort-VPN-Verbindung verwendet wird (Fragen Sie Ihre IT- oder Sicherheitsabteilung nach diesem Schlüsselwert. Alternativ finden Sie weitere Informationen unter [Create a random string for an IPsec preshared key](http://social.technet.microsoft.com/wiki/contents/articles/32330.create-a-random-string-for-an-ipsec-preshared-key.aspx).)  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
   
 **Tabelle V: Konfiguration eines standortübergreifenden virtuellen Netzwerks**
  
Füllen Sie nun Tabelle S für die Subnetze dieser Lösung aus. Alle Adressräume sollten im CIDR (Classless Inter-Domain Routing)-Format angegeben werden, auch Netzwerkpräfixformat genannt. Beispiel: 10.24.64.0/20.
  
Geben Sie für die ersten drei Subnetze einen Namen und einen einzigen IP-Adressraum aus dem Adressraum des virtuellen Netzwerks an. Gehen Sie wie folgt vor, um den 27-Bit-Adressraum (mit Präfixlänge „/27“) für das Azure-Gatewaysubnetz zu ermitteln:
  
1. Setzen Sie die variablen Bits im Adressraum des VNet auf 1, bis zu den für das Gatewaysubnetz verwendeten Bits. Setzen Sie die verbleibenden Bits auf 0.
    
2. Übertragen Sie den resultierenden Bitblock ins Dezimalsystem, und drücken Sie ihn als Adressraum aus, wobei Sie als Präfixlänge die Größe des Gatewaysubnetzes festlegen.
    
Siehe [Adressraum Rechner für Azure-Gateway](https://gallery.technet.microsoft.com/scriptcenter/Address-prefix-calculator-a94b6eed) -Subnetze für einen PowerShell-Befehlsblock und eine C#-oder python-Konsolenanwendung, die diese Berechnung für Sie durchführt.
  
Fragen Sie Ihre IT-Abteilung nach diesen Adressräumen aus dem Adressraum des virtuellen Netzwerks.
  
|**Item**|**Subnetzname**|**Subnetzadressraum**|**Zweck**|
|:-----|:-----|:-----|:-----|
|1.  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |Das Subnetz, das vom Windows Server Active Directory-Domänencontroller und den virtuellen Computer des DirSync-Servers verwendet wird.  <br/> |
|2.  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |Das von den virtuellen Computern von AD FS verwendete Subnetz.  <br/> |
|3.  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |Das von den virtuellen Computern des Webanwendungsproxys verwendete Subnetz.  <br/> |
|4.  <br/> |GatewaySubnet  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |Das von den virtuellen Computern des Azure-Gateways verwendete Subnetz.  <br/> |
   
 **Tabelle S: Subnetze im virtuellen Netzwerk**
  
Tragen Sie in Tabelle I nun die statischen IP-Adressen ein, die den virtuellen Computern und den Load Balancer-Instanzen zugewiesen werden.
  
|**Element**|**Zweck**|**IP-Adresse im Subnetz**|**Wert**|
|:-----|:-----|:-----|:-----|
|1.  <br/> |Statische IP-Adresse des ersten Domänencontrollers  <br/> |Die vierte mögliche IP-Adresse für den Adressraum des in Tabelle S, Element 1 definierten Subnetzes  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|2.  <br/> |Statische IP-Adresse des zweiten Domänencontrollers  <br/> |Die fünfte mögliche IP-Adresse für den Adressraum des in Tabelle S, Element 1 definierten Subnetzes  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|3.  <br/> |Statische IP-Adresse des DirSync-Servers  <br/> |Die sechste mögliche IP-Adresse für den Adressraum des in Tabelle S, Element 1 definierten Subnetzes  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|4.  <br/> |Statische IP-Adresse des internen Lastenausgleichs für die AD FS-Server  <br/> |Die vierte mögliche IP-Adresse für den Adressraum des in Tabelle S, Element 2 definierten Subnetzes  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|5.  <br/> |Statische IP-Adresse des ersten AD FS-Servers  <br/> |Die fünfte mögliche IP-Adresse für den Adressraum des in Tabelle S, Element 2 definierten Subnetzes  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|6.  <br/> |Statische IP-Adresse des zweiten AD FS-Servers  <br/> |Die sechste mögliche IP-Adresse für den Adressraum des in Tabelle S, Element 2 definierten Subnetzes  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|7.  <br/> |Statische IP-Adresse des ersten Webanwendungsproxy-Servers
  <br/> |Die vierte mögliche IP-Adresse für den Adressraum des in Tabelle S, Element 3 definierten Subnetzes  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|8.  <br/> |Statische IP-Adresse des zweiten Webanwendungsproxy-Servers
  <br/> |Die fünfte mögliche IP-Adresse für den Adressraum des in Tabelle S, Element 3 definierten Subnetzes  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
   
 **Tabelle I: Statische IP-Adressen im virtuellen Netzwerk**
  
Füllen Sie Tabelle D für die beiden DNS-Server in Ihrem lokalen Netzwerk aus, die Sie bei der Ersteinrichtung der Domänencontroller in Ihrem virtuellen Netzwerk verwenden möchten. Stellen Sie diese Liste gemeinsam mit Ihrer IT-Abteilung zusammen.
  
|**Item**|**Anzeigename des DNS-Servers**|**IP-Adresse des DNS-Servers**|
|:-----|:-----|:-----|
|1.  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|2.  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
   
 **Tabelle D: Lokale DNS-Server**
  
Zum Weiterleiten von Paketen aus dem standortübergreifenden Netzwerk zu Ihrem Organisationsnetzwerk über die Website-zu-Standort-VPN-Verbindung müssen Sie das virtuelle Netzwerk mit einem lokalen Netzwerk konfigurieren, das über eine Liste der Adressräume (in CIDR-Notation) für alle erreichbaren Standorte im lokalen Netzwerk Ihrer Organisation. Die Liste der Adressräume, die Ihr lokales Netzwerk definieren, muss eindeutig sein und darf sich nicht mit dem Adressraum überschneiden, der für andere virtuelle Netzwerke oder andere lokale Netzwerke verwendet wird.
  
Für die Teilmenge der Adressräume für das lokale Netzwerk füllen Sie Tabelle L aus. Auch wenn hierfür nur drei Einträge vorgesehen sind, können Sie noch weitere hinzufügen. Erarbeiten Sie diese Liste der Adressräume gemeinsam mit Ihrer IT-Abteilung.
  
|**Element**|**Adressraum des lokalen Netzwerks**|
|:-----|:-----|
|1.  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|2.  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|3.  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
   
 **Tabelle L: Adresspräfixe für das lokale Netzwerk**
  
Jetzt können Sie mit dem Erstellen der Azure-Infrastruktur beginnen, die die Verbundauthentifizierung für Office 365 hosten soll.
  
> [!NOTE]
> [!HINWEIS] In den folgenden Befehlssätzen wird die aktuelle Version von Azure PowerShell verwendet. Informationen dazu finden Sie unter [Get started with Azure PowerShell cmdlets](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/). 
  
Starten Sie zunächst eine Azure PowerShell-Eingabeaufforderung, und melden Sie sich bei Ihrem Konto an.
  
```
Connect-AzAccount
```

<!--
> [!TIP]
> For a text file that has all of the PowerShell commands in this article and a Microsoft Excel configuration workbook that generates ready-to-run PowerShell command blocks based on your custom settings, see the [Federated Authentication for Office 365 in Azure Deployment Kit](https://gallery.technet.microsoft.com/Federated-Authentication-8a9f1664). 
-->
  
Rufen Sie den Namen Ihres Abonnements mithilfe des folgenden Befehls ab.
  
```
Get-AzSubscription | Sort Name | Select Name
```

Verwenden Sie für ältere Versionen von Azure PowerShell stattdessen diesen Befehl.
  
```
Get-AzSubscription | Sort Name | Select SubscriptionName
```

Tragen Sie Ihr Azure-Abonnement ein. Ersetzen Sie alle Elemente innerhalb der Anführungszeichen, einschließlich der \< und >, mit dem richtigen Namen.
  
```
$subscr="<subscription name>"
Select-AzSubscription -SubscriptionName $subscrName -Current
```

Erstellen Sie im nächsten Schritt die neuen Ressourcengruppen. Listen Sie mit dem folgenden Befehl alle bereits vorhandenen Ressourcengruppen auf, um eine eindeutige Gruppe von Ressourcengruppennamen zu ermitteln.
  
```
Get-AzResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

Tragen Sie die eindeutigen Ressourcengruppennamen in die folgende Tabelle ein.
  
|**Element**|**Ressourcengruppenname**|**Zweck**|
|:-----|:-----|:-----|
|1.  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |Domänencontroller  <br/> |
|2.  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |AD FS-Server  <br/> |
|3.  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |Webanwendungsproxy-Server  <br/> |
|4.  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |Infrastrukturelemente  <br/> |
   
 **Tabelle R: Ressourcengruppen**
  
Erstellen Sie die neuen Ressourcengruppen mit den folgenden Befehlen.
  
```
$locName="<an Azure location, such as West US>"
$rgName="<Table R - Item 1 - Name column>"
New-AzResourceGroup -Name $rgName -Location $locName
$rgName="<Table R - Item 2 - Name column>"
New-AzResourceGroup -Name $rgName -Location $locName
$rgName="<Table R - Item 3 - Name column>"
New-AzResourceGroup -Name $rgName -Location $locName
$rgName="<Table R - Item 4 - Name column>"
New-AzResourceGroup -Name $rgName -Location $locName
```

Erstellen Sie als Nächstes das virtuelle Azure-Netzwerk und seine Subnetze.
  
```
$rgName="<Table R - Item 4 - Resource group name column>"
$locName="<your Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$vnetAddrPrefix="<Table V - Item 4 - Value column>"
$dnsServers=@( "<Table D - Item 1 - DNS server IP address column>", "<Table D - Item 2 - DNS server IP address column>" )
# Get the shortened version of the location
$locShortName=(Get-AzResourceGroup -Name $rgName).Location

# Create the subnets
$subnet1Name="<Table S - Item 1 - Subnet name column>"
$subnet1Prefix="<Table S - Item 1 - Subnet address space column>"
$subnet1=New-AzVirtualNetworkSubnetConfig -Name $subnet1Name -AddressPrefix $subnet1Prefix
$subnet2Name="<Table S - Item 2 - Subnet name column>"
$subnet2Prefix="<Table S - Item 2 - Subnet address space column>"
$subnet2=New-AzVirtualNetworkSubnetConfig -Name $subnet2Name -AddressPrefix $subnet2Prefix
$subnet3Name="<Table S - Item 3 - Subnet name column>"
$subnet3Prefix="<Table S - Item 3 - Subnet address space column>"
$subnet3=New-AzVirtualNetworkSubnetConfig -Name $subnet3Name -AddressPrefix $subnet3Prefix
$gwSubnet4Prefix="<Table S - Item 4 - Subnet address space column>"
$gwSubnet=New-AzVirtualNetworkSubnetConfig -Name "GatewaySubnet" -AddressPrefix $gwSubnet4Prefix

# Create the virtual network
New-AzVirtualNetwork -Name $vnetName -ResourceGroupName $rgName -Location $locName -AddressPrefix $vnetAddrPrefix -Subnet $gwSubnet,$subnet1,$subnet2,$subnet3 -DNSServer $dnsServers

```

Als Nächstes erstellen Sie Netzwerk Sicherheitsgruppen für jedes Subnetz mit virtuellen Computern. Um die Isolierung der Subnetze durchzuführen, können Sie Regeln für den jeweiligen Typ von Datenverkehr hinzufügen, der für die Netzwerksicherheitsgruppe eines Subnetzes erlaubt oder zurückgewiesen werden soll.
  
```
# Create network security groups
$vnet=Get-AzVirtualNetwork -ResourceGroupName $rgName -Name $vnetName

New-AzNetworkSecurityGroup -Name $subnet1Name -ResourceGroupName $rgName -Location $locShortName
$nsg=Get-AzNetworkSecurityGroup -Name $subnet1Name -ResourceGroupName $rgName
Set-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnet1Name -AddressPrefix $subnet1Prefix -NetworkSecurityGroup $nsg

New-AzNetworkSecurityGroup -Name $subnet2Name -ResourceGroupName $rgName -Location $locShortName
$nsg=Get-AzNetworkSecurityGroup -Name $subnet2Name -ResourceGroupName $rgName
Set-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnet2Name -AddressPrefix $subnet2Prefix -NetworkSecurityGroup $nsg

New-AzNetworkSecurityGroup -Name $subnet3Name -ResourceGroupName $rgName -Location $locShortName
$nsg=Get-AzNetworkSecurityGroup -Name $subnet3Name -ResourceGroupName $rgName
Set-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnet3Name -AddressPrefix $subnet3Prefix -NetworkSecurityGroup $nsg
```

Verwenden Sie anschließend diese Befehle zum Erstellen der Gateways für die Standort-zu-Standort-VPN-Verbindung.
  
```
$rgName="<Table R - Item 4 - Resource group name column>"
$locName="<Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$vnet=Get-AzVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
$subnet=Get-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name "GatewaySubnet"

# Attach a virtual network gateway to a public IP address and the gateway subnet
$publicGatewayVipName="PublicIPAddress"
$vnetGatewayIpConfigName="PublicIPConfig"
New-AzPublicIpAddress -Name $vnetGatewayIpConfigName -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$publicGatewayVip=Get-AzPublicIpAddress -Name $vnetGatewayIpConfigName -ResourceGroupName $rgName
$vnetGatewayIpConfig=New-AzVirtualNetworkGatewayIpConfig -Name $vnetGatewayIpConfigName -PublicIpAddressId $publicGatewayVip.Id -Subnet $subnet

# Create the Azure gateway
$vnetGatewayName="AzureGateway"
$vnetGateway=New-AzVirtualNetworkGateway -Name $vnetGatewayName -ResourceGroupName $rgName -Location $locName -GatewayType Vpn -VpnType RouteBased -IpConfigurations $vnetGatewayIpConfig

# Create the gateway for the local network
$localGatewayName="LocalNetGateway"
$localGatewayIP="<Table V - Item 3 - Value column>"
$localNetworkPrefix=@( <comma-separated, double-quote enclosed list of the local network address prefixes from Table L, example: "10.1.0.0/24", "10.2.0.0/24"> )
$localGateway=New-AzLocalNetworkGateway -Name $localGatewayName -ResourceGroupName $rgName -Location $locName -GatewayIpAddress $localGatewayIP -AddressPrefix $localNetworkPrefix

# Define the Azure virtual network VPN connection
$vnetConnectionName="S2SConnection"
$vnetConnectionKey="<Table V - Item 5 - Value column>"
$vnetConnection=New-AzVirtualNetworkGatewayConnection -Name $vnetConnectionName -ResourceGroupName $rgName -Location $locName -ConnectionType IPsec -SharedKey $vnetConnectionKey -VirtualNetworkGateway1 $vnetGateway -LocalNetworkGateway2 $localGateway

```

> [!NOTE]
> Für die Verbundauthentifizierung einzelner Benutzer ist kein Rückgriff auf lokale Ressourcen erforderlich. Wenn diese Standort-zu-Standort-VPN-Verbindung jedoch nicht mehr verfügbar ist, erhalten die Domänencontroller in der VNet keine Aktualisierungen an Benutzerkonten und Gruppen, die in der lokalen Windows Server AD-Anzeige vorgenommen wurden. Um sicherzustellen, dass dies nicht der Fall ist, können Sie hohe Verfügbarkeit für die Standort-zu-Standort-VPN-Verbindung konfigurieren. Weitere Informationen finden Sie unter [hoch verfügbare standortübergreifende und VNet-zu-VNet-Konnektivität](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-highlyavailable)
  
Notieren Sie sich jetzt die öffentliche IPv4-Adresse des Azure-VPN-Gateways für Ihr virtuelles Netzwerk aus der Ausgabe des folgenden Befehls:
  
```
Get-AzPublicIpAddress -Name $publicGatewayVipName -ResourceGroupName $rgName
```

Konfigurieren Sie im nächsten Schritt die Verbindung zwischen dem lokalen VPN-Gerät und dem Azure-VPN-Gateway. Weitere Informationen finden Sie im Artikel zum Thema [Konfigurieren von VPN-Geräten](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpn-devices).
  
Sie benötigen folgende Informationen zum Konfigurieren Ihres lokalen VPN-Geräts:
  
- Die öffentliche IPv4-Adresse des Azure-VPN-Gateways
    
- Den vorinstallierten IPsec-Schlüssel für die Standort-zu-Standort-VPN-Verbindung (Tabelle V, Element 5, Spalte „Wert")
    
Vergewissern Sie sich im nächsten Schritt, dass der Adressraum des virtuellen Netzwerks aus Ihrem lokalen Netzwerk erreichbar ist. In der Regel fügen Sie dazu Ihrem VPN-Gerät eine dem Adressraum des virtuellen Netzwerks entsprechende Route hinzu und senden diese Route anschließend an die restliche Weiterleitungsinfrastruktur Ihres Organisationsnetzwerks. Erkundigen Sie sich bei Ihrer IT-Abteilung, wie Sie vorgehen sollen.
  
Definieren Sie nun die Namen von drei Verfügbarkeitsgruppen. Füllen Sie Tabelle A aus.  
  
|**Item**|**Zweck**|**Name der Verfügbarkeitsgruppe**|
|:-----|:-----|:-----|
|1.  <br/> |Domänencontroller  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|2.  <br/> |AD FS-Server  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|3.  <br/> |Webanwendungsproxy-Server  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
   
 **Tabelle A: Verfügbarkeitsgruppen**
  
Sie benötigen diese Namen bei der Erstellung der virtuellen Computer in den Phasen 2, 3 und 4.
  
Erstellen Sie die neuen Verfügbarkeitsgruppen mithilfe der folgenden Azure PowerShell-Befehle.
  
```
$locName="<the Azure location for your new resource group>"
$rgName="<Table R - Item 1 - Resource group name column>"
$avName="<Table A - Item 1 - Availability set name column>"
New-AzAvailabilitySet -ResourceGroupName $rgName -Name $avName -Location $locName -Sku Aligned  -PlatformUpdateDomainCount 5 -PlatformFaultDomainCount 2
$rgName="<Table R - Item 2 - Resource group name column>"
$avName="<Table A - Item 2 - Availability set name column>"
New-AzAvailabilitySet -ResourceGroupName $rgName -Name $avName -Location $locName -Sku Aligned  -PlatformUpdateDomainCount 5 -PlatformFaultDomainCount 2
$rgName="<Table R - Item 3 - Resource group name column>"
$avName="<Table A - Item 3 - Availability set name column>"
New-AzAvailabilitySet -ResourceGroupName $rgName -Name $avName -Location $locName -Sku Aligned  -PlatformUpdateDomainCount 5 -PlatformFaultDomainCount 2
```

Haben Sie diese Phase erfolgreich abgeschlossen, sieht Ihre Konfiguration wie folgt aus.
  
**Phase 1: Die Azure-Infrastruktur für die Verbundauthentifizierung mit hoher Verfügbarkeit für Office 365**

![Phase 1 der hoch Verfügbarkeits-Office 365-Verbundauthentifizierung in Azure mit der Azure-Infrastruktur](media/4e7ba678-07df-40ce-b372-021bf7fc91fa.png)
  
## <a name="next-step"></a>Nächster Schritt

Gehen Sie zu [High availability federated authentication Phase 2: Configure domain controllers](high-availability-federated-authentication-phase-2-configure-domain-controllers.md), um mit der Konfiguration dieser Workload fortzufahren.
  
## <a name="see-also"></a>Siehe auch

[Bereitstellen der Verbundauthentifizierung mit Hochverfügbarkeit für Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)
  
[Verbundidentität für Ihre Office 365-Entwicklungs-/Testumgebung](federated-identity-for-your-office-365-dev-test-environment.md)
  
[Cloudakzeptanz und Hybridlösungen](cloud-adoption-and-hybrid-solutions.md)

[Grundlegendes zu Office 365-Identitäten und Azure Active Directory](about-office-365-identity.md)


