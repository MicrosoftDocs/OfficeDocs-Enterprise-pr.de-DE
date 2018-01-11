---
title: "Hohe Verfügbarkeit Verbundauthentifizierung Phase 1 Konfigurieren von Azure"
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
ms.assetid: 91266aac-4d00-4b5f-b424-86a1a837792c
description: "Zusammenfassung: Konfigurieren Sie die Microsoft Azure-Infrastruktur Host hohe Verfügbarkeit Verbundauthentifizierung für Office 365."
ms.openlocfilehash: f74e91930f5aef8f10986dcf51db6066c953014d
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/11/2018
---
# <a name="high-availability-federated-authentication-phase-1-configure-azure"></a>Hochverfügbarkeit der Verbundauthentifizierung, Phase 1: Konfigurieren von Azure

 **Zusammenfassung:** Konfigurieren Sie die Microsoft Azure-Infrastruktur Host hohe Verfügbarkeit federated-Authentifizierung für Office 365.
  
In dieser Phase erstellen Sie die Ressourcengruppen, Speicherkonten, virtuelle Netzwerk (VNet) und Verfügbarkeit Mengen in Azure, die die virtuellen Computer in Phasen 2, 3 und 4 hostet. Müssen Sie vor dem Verschieben auf in dieser Phase [hoher Verfügbarkeit federated Authentifizierung Phase 2: Konfigurieren von Domänencontrollern](high-availability-federated-authentication-phase-2-configure-domain-controllers.md). Finden Sie unter [Deploy hohe Verfügbarkeit Verbundauthentifizierung für Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) für alle Phasen.
  
Azure muss diese grundlegenden Komponenten bereitgestellt werden:
  
- Ressourcengruppen
    
- Ein standortübergreifendes virtuelles Azure-Netzwerk (VNet) mit Subnetzen für das Hosting der virtuellen Computer in Azure
    
- Netzwerksicherheitsgruppen zur Isolierung der Subnetze
    
- Verfügbarkeitsgruppen
    
## <a name="configure-azure-components"></a>Konfigurieren der Azure-Komponenten

Vor dem Konfigurieren der Azure-Komponenten, füllen Sie in den folgenden Tabellen. Hilft Ihnen bei der die Verfahren zum Konfigurieren von Azure, in diesem Abschnitt Drucken und notieren Sie die benötigten Informationen oder Kopieren in diesem Abschnitt in ein Dokument und füllen Sie es aus. Füllen Sie für den Einstellungen der VNet Tabelle V aus.
  
|**Element**|**Einstellung für die Konfiguration**|**Beschreibung**|**Wert**|
|:-----|:-----|:-----|:-----|
|1.  <br/> |VNet-Name  <br/> |Ein Name, der dem VNet zugewiesen wird (z. B. FedAuthNet).  <br/> |_______________________________  <br/> |
|2.  <br/> |VNet Speicherort  <br/> |Das regionale Azure-Rechenzentrum, in dem sich das virtuelle Netzwerk befinden soll  <br/> |_______________________________  <br/> |
|3.  <br/> |IP-Adresse des VPN-Geräts  <br/> |Die öffentliche IPv4-Adresse der Schnittstelle des VPN-Geräts im Internet  <br/> |_______________________________  <br/> |
|4.  <br/> |VNet-Adressraum  <br/> |Der Adressraum für das virtuelle Netzwerk (Fragen Sie Ihre IT-Abteilung nach diesem Adressraum.)  <br/> |_______________________________  <br/> |
|5.  <br/> |Gemeinsam verwendeter IPsec-Schlüssel  <br/> |Eine 32 Zeichen zufällige, alphanumerische Zeichenfolge, die verwendet wird, um beide Seiten der Website-zu-Standort-VPN-Verbindung zu authentifizieren. Arbeiten mit Ihrer IT- oder jede Abteilung Sicherheit dieser Schlüsselwert bestimmen. Alternativ finden Sie unter [Erstellen einer zufälligen Zeichenfolge für einen vorinstallierten IPsec-Schlüssel](http://social.technet.microsoft.com/wiki/contents/articles/32330.create-a-random-string-for-an-ipsec-preshared-key.aspx).<br/> |_______________________________  <br/> |
   
 **Tabelle V: Konfiguration eines standortübergreifenden virtuellen Netzwerks**
  
Füllen Sie nun Tabelle S für die Subnetze dieser Lösung aus. Alle Adressräume sollten im CIDR (Classless Inter-Domain Routing)-Format angegeben werden, auch Netzwerkpräfixformat genannt. Beispiel: 10.24.64.0/20.
  
Geben Sie für die ersten drei Subnetze einen Namen und einen einzigen IP-Adressraum aus dem Adressraum des virtuellen Netzwerks an. Gehen Sie wie folgt vor, um den 27-Bit-Adressraum (mit Präfixlänge „/27“) für das Azure-Gatewaysubnetz zu ermitteln:
  
1. Setzen Sie die variablen Bits im Adressraum des VNet auf 1, bis zu den für das Gatewaysubnetz verwendeten Bits. Setzen Sie die verbleibenden Bits auf 0.
    
2. Übertragen Sie den resultierenden Bitblock ins Dezimalsystem, und drücken Sie ihn als Adressraum aus, wobei Sie als Präfixlänge die Größe des Gatewaysubnetzes festlegen.
    
Finden Sie unter [Adresse Speicherplatz Rechner für Azure Gateway Subnetze](https://gallery.technet.microsoft.com/scriptcenter/Address-prefix-calculator-a94b6eed) ein PowerShell-Befehl blockieren und c# oder Python Konsolenanwendung, die für Sie diese Berechnung ausgeführt hat.
  
Fragen Sie Ihre IT-Abteilung nach diesen Adressräumen aus dem Adressraum des virtuellen Netzwerks.
  
|**Element**|**Subnetzname**|**Subnetzadressraum**|**Zweck**|
|:-----|:-----|:-----|:-----|
|1.  <br/> |_______________________________  <br/> |_______________________________  <br/> |Das Subnetz, das vom Windows Server Active Directory-Domänencontroller und den virtuellen Computer des DirSync-Servers verwendet wird.  <br/> |
|2.  <br/> |_______________________________  <br/> |_______________________________  <br/> |Das von den virtuellen Computern von AD FS verwendete Subnetz.  <br/> |
|3.  <br/> |_______________________________  <br/> |_______________________________  <br/> |Das von den virtuellen Computern des Webanwendungsproxys verwendete Subnetz.  <br/> |
|4.  <br/> |GatewaySubnet  <br/> |_______________________________  <br/> |Das von den virtuellen Computern des Azure-Gateways verwendete Subnetz.  <br/> |
   
 **Tabelle S: Subnetze im virtuellen Netzwerk**
  
Tragen Sie in Tabelle I nun die statischen IP-Adressen ein, die den virtuellen Computern und den Load Balancer-Instanzen zugewiesen werden.
  
|**Element**|**Zweck**|**IP-Adresse im Subnetz**|**Wert**|
|:-----|:-----|:-----|:-----|
|1.  <br/> |Statische IP-Adresse des ersten Domänencontrollers  <br/> |Die vierte mögliche IP-Adresse für den Adressraum des in Tabelle S, Element 1 definierten Subnetzes  <br/> |_______________________________  <br/> |
|2.  <br/> |Statische IP-Adresse des zweiten Domänencontrollers  <br/> |Die fünfte mögliche IP-Adresse für den Adressraum des in Tabelle S, Element 1 definierten Subnetzes  <br/> |_______________________________  <br/> |
|3.  <br/> |Statische IP-Adresse des DirSync-Servers  <br/> |Die sechste mögliche IP-Adresse für den Adressraum des in Tabelle S, Element 1 definierten Subnetzes  <br/> |_______________________________  <br/> |
|4.  <br/> |Statische IP-Adresse des internen Lastenausgleichs für die AD FS-Server  <br/> |Die vierte mögliche IP-Adresse für den Adressraum des in Tabelle S, Element 2 definierten Subnetzes  <br/> |_______________________________  <br/> |
|5.  <br/> |Statische IP-Adresse des ersten AD FS-Servers  <br/> |Die fünfte mögliche IP-Adresse für den Adressraum des in Tabelle S, Element 2 definierten Subnetzes  <br/> |_______________________________  <br/> |
|6.  <br/> |Statische IP-Adresse des zweiten AD FS-Servers  <br/> |Die sechste mögliche IP-Adresse für den Adressraum des in Tabelle S, Element 2 definierten Subnetzes  <br/> |_______________________________  <br/> |
|7.  <br/> |Statische IP-Adresse des ersten Webanwendungsproxy-Servers
  <br/> |Die vierte mögliche IP-Adresse für den Adressraum des in Tabelle S, Element 3 definierten Subnetzes  <br/> |_______________________________  <br/> |
|8.  <br/> |Statische IP-Adresse des zweiten Webanwendungsproxy-Servers
  <br/> |Die fünfte mögliche IP-Adresse für den Adressraum des in Tabelle S, Element 3 definierten Subnetzes  <br/> |_______________________________  <br/> |
   
 **Tabelle I: statische IP-Adressen in das virtuelle Netzwerk**
  
Füllen Sie Tabelle D für die beiden DNS-Server in Ihrem lokalen Netzwerk aus, die Sie bei der Ersteinrichtung der Domänencontroller in Ihrem virtuellen Netzwerk verwenden möchten. Stellen Sie diese Liste gemeinsam mit Ihrer IT-Abteilung zusammen.
  
|**Element**|**Anzeigename des DNS-Servers**|**IP-Adresse des DNS-Servers**|
|:-----|:-----|:-----|
|1.  <br/> |_______________________________  <br/> |_______________________________  <br/> |
|2.  <br/> |_______________________________  <br/> |_______________________________  <br/> |
   
 **Tabelle D: Lokale DNS-Server**
  
Um Pakete über die Standort-zu-Standort-VPN-Verbindung aus dem standortübergreifenden Netzwerk an das Organisationsnetzwerk weiterleiten zu können, müssen Sie das virtuelle Netzwerk mit einem lokalen Netzwerk konfigurieren. Dieses lokale Netzwerk muss eine Liste der Adressräume (im CIDR-Format) für alle erreichbaren Standorte in Ihrem lokalen Organisationsnetzwerk enthalten. Die Liste der Adressräume, die Ihr lokales Netzwerk definieren, muss eindeutig sein und darf nicht mit den für andere virtuelle oder lokale Netzwerke verwendeten Adressräumen überlappen.
  
Für die Teilmenge der Adressräume für das lokale Netzwerk füllen Sie Tabelle L aus. Auch wenn hierfür nur drei Einträge vorgesehen sind, können Sie noch weitere hinzufügen. Erarbeiten Sie diese Liste der Adressräume gemeinsam mit Ihrer IT-Abteilung.
  
|**Element**|**Adressraum des lokalen Netzwerks**|
|:-----|:-----|
|1.  <br/> |_______________________________  <br/> |
|2.  <br/> |_______________________________  <br/> |
|3.  <br/> |_______________________________  <br/> |
   
 **Tabelle L: Adresspräfixe für das lokale Netzwerk**
  
Jetzt können Sie mit dem Erstellen der Azure-Infrastruktur beginnen, die die Verbundauthentifizierung für Office 365 hosten soll.
  
> [!NOTE]
> Verwenden Sie den folgenden Befehl wird die neueste Version von Azure PowerShell. Finden Sie unter [Erste Schritte mit Azure PowerShell-Cmdlets](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/). 
  
Starten Sie zunächst eine Azure PowerShell-Eingabeaufforderung, und melden Sie sich bei Ihrem Konto an.
  
```
Login-AzureRMAccount
```

> [!TIP]
> Eine Textdatei, die alle von PowerShell-Befehlen in diesem Artikel und Konfiguration Microsoft Excel-Arbeitsmappen, die generiert Ready-und-Los-PowerShell-Befehl Blöcke basierend auf Ihrer benutzerdefinierten Einstellungen enthält, finden Sie unter der [Federated-Authentifizierung für Office 365 in Azure Deployment Kit](https://gallery.technet.microsoft.com/Federated-Authentication-8a9f1664). 
  
Rufen Sie den Namen Ihres Abonnements mithilfe des folgenden Befehls ab.
  
```
Get-AzureRMSubscription | Sort Name | Select Name
```

Verwenden Sie diesen Befehl für ältere Versionen von Azure PowerShell stattdessen.
  
```
Get-AzureRMSubscription | Sort Name | Select SubscriptionName
```

Legen Sie Ihre Azure-Abonnement. Ersetzen Sie alles innerhalb der Anführungszeichen, einschließlich der \< und > Zeichen, mit dem korrekten Namen.
  
```
$subscr="<subscription name>"
Get-AzureRmSubscription -SubscriptionName $subscr | Select-AzureRmSubscription
```

Erstellen Sie im nächsten Schritt die neuen Ressourcengruppen. Listen Sie mit dem folgenden Befehl alle bereits vorhandenen Ressourcengruppen auf, um eine eindeutige Gruppe von Ressourcengruppennamen zu ermitteln.
  
```
Get-AzureRMResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

Tragen Sie die eindeutigen Ressourcengruppennamen in die folgende Tabelle ein.
  
|**Element**|**Gruppe Ressourcenname**|**Zweck**|
|:-----|:-----|:-----|
|1.  <br/> |_______________________________  <br/> |Domänencontroller  <br/> |
|2.  <br/> |_______________________________  <br/> |AD FS-Server  <br/> |
|3.  <br/> |_______________________________  <br/> |Webanwendungsproxy-Server  <br/> |
|4.  <br/> |_______________________________  <br/> |Infrastrukturelemente  <br/> |
   
 **Tabelle R: Ressourcengruppen**
  
Erstellen Sie die neuen Ressourcengruppen mit den folgenden Befehlen.
  
```
$locName="<an Azure location, such as West US>"
$rgName="<Table R - Item 1 - Name column>"
New-AzureRMResourceGroup -Name $rgName -Location $locName
$rgName="<Table R - Item 2 - Name column>"
New-AzureRMResourceGroup -Name $rgName -Location $locName
$rgName="<Table R - Item 3 - Name column>"
New-AzureRMResourceGroup -Name $rgName -Location $locName
$rgName="<Table R - Item 4 - Name column>"
New-AzureRMResourceGroup -Name $rgName -Location $locName
```

Erstellen Sie als Nächstes das virtuelle Azure-Netzwerk und seine Subnetze.
  
```
$rgName="<Table R - Item 4 - Resource group name column>"
$locName="<your Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$vnetAddrPrefix="<Table V - Item 4 - Value column>"
$dnsServers=@( "<Table D - Item 1 - DNS server IP address column>", "<Table D - Item 2 - DNS server IP address column>" )
# Get the shortened version of the location
$locShortName=(Get-AzureRmResourceGroup -Name $rgName).Location

# Create the subnets
$subnet1Name="<Table S - Item 1 - Subnet name column>"
$subnet1Prefix="<Table S - Item 1 - Subnet address space column>"
$subnet1=New-AzureRMVirtualNetworkSubnetConfig -Name $subnet1Name -AddressPrefix $subnet1Prefix
$subnet2Name="<Table S - Item 2 - Subnet name column>"
$subnet2Prefix="<Table S - Item 2 - Subnet address space column>"
$subnet2=New-AzureRMVirtualNetworkSubnetConfig -Name $subnet2Name -AddressPrefix $subnet2Prefix
$subnet3Name="<Table S - Item 3 - Subnet name column>"
$subnet3Prefix="<Table S - Item 3 - Subnet address space column>"
$subnet3=New-AzureRMVirtualNetworkSubnetConfig -Name $subnet3Name -AddressPrefix $subnet3Prefix
$gwSubnet4Prefix="<Table S - Item 4 - Subnet address space column>"
$gwSubnet=New-AzureRMVirtualNetworkSubnetConfig -Name "GatewaySubnet" -AddressPrefix $gwSubnet4Prefix

# Create the virtual network
New-AzureRMVirtualNetwork -Name $vnetName -ResourceGroupName $rgName -Location $locName -AddressPrefix $vnetAddrPrefix -Subnet $gwSubnet,$subnet1,$subnet2,$subnet3 -DNSServer $dnsServers

```

Im nächsten Schritt erstellen Sie Sicherheitsgruppen für jedes Subnetz, das virtuelle Netzwerk. Informationen zum Subnetz Isolation ausführen, können Sie Regeln für bestimmten Arten von Datenverkehr erteilt oder verweigert eines Subnetzes Netzwerk-Sicherheitsgruppe hinzufügen.
  
```
# Create network security groups
$vnet=Get-AzureRMVirtualNetwork -ResourceGroupName $rgName -Name $vnetName

New-AzureRMNetworkSecurityGroup -Name $subnet1Name -ResourceGroupName $rgName -Location $locShortName
$nsg=Get-AzureRMNetworkSecurityGroup -Name $subnet1Name -ResourceGroupName $rgName
Set-AzureRMVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnet1Name -AddressPrefix $subnet1Prefix -NetworkSecurityGroup $nsg

New-AzureRMNetworkSecurityGroup -Name $subnet2Name -ResourceGroupName $rgName -Location $locShortName
$nsg=Get-AzureRMNetworkSecurityGroup -Name $subnet2Name -ResourceGroupName $rgName
Set-AzureRMVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnet2Name -AddressPrefix $subnet2Prefix -NetworkSecurityGroup $nsg

New-AzureRMNetworkSecurityGroup -Name $subnet3Name -ResourceGroupName $rgName -Location $locShortName
$nsg=Get-AzureRMNetworkSecurityGroup -Name $subnet3Name -ResourceGroupName $rgName
Set-AzureRMVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnet3Name -AddressPrefix $subnet3Prefix -NetworkSecurityGroup $nsg
```

Verwenden Sie anschließend diese Befehle zum Erstellen der Gateways für die Standort-zu-Standort-VPN-Verbindung.
  
```
$rgName="<Table R - Item 4 - Resource group name column>"
$locName="<Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$vnet=Get-AzureRMVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
$subnet=Get-AzureRmVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name "GatewaySubnet"

# Attach a virtual network gateway to a public IP address and the gateway subnet
$publicGatewayVipName="PublicIPAddress"
$vnetGatewayIpConfigName="PublicIPConfig"
New-AzureRMPublicIpAddress -Name $vnetGatewayIpConfigName -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$publicGatewayVip=Get-AzureRMPublicIpAddress -Name $vnetGatewayIpConfigName -ResourceGroupName $rgName
$vnetGatewayIpConfig=New-AzureRMVirtualNetworkGatewayIpConfig -Name $vnetGatewayIpConfigName -PublicIpAddressId $publicGatewayVip.Id -Subnet $subnet

# Create the Azure gateway
$vnetGatewayName="AzureGateway"
$vnetGateway=New-AzureRMVirtualNetworkGateway -Name $vnetGatewayName -ResourceGroupName $rgName -Location $locName -GatewayType Vpn -VpnType RouteBased -IpConfigurations $vnetGatewayIpConfig

# Create the gateway for the local network
$localGatewayName="LocalNetGateway"
$localGatewayIP="<Table V - Item 3 - Value column>"
$localNetworkPrefix=@( <comma-separated, double-quote enclosed list of the local network address prefixes from Table L, example: "10.1.0.0/24", "10.2.0.0/24"> )
$localGateway=New-AzureRMLocalNetworkGateway -Name $localGatewayName -ResourceGroupName $rgName -Location $locName -GatewayIpAddress $localGatewayIP -AddressPrefix $localNetworkPrefix

# Define the Azure virtual network VPN connection
$vnetConnectionName="S2SConnection"
$vnetConnectionKey="<Table V - Item 5 - Value column>"
$vnetConnection=New-AzureRMVirtualNetworkGatewayConnection -Name $vnetConnectionName -ResourceGroupName $rgName -Location $locName -ConnectionType IPsec -SharedKey $vnetConnectionKey -VirtualNetworkGateway1 $vnetGateway -LocalNetworkGateway2 $localGateway

```

> [!NOTE]
> Verbundauthentifizierung einzelner Benutzer nicht auf alle lokalen Ressourcen verlassen. Wenn dieser Standort-zu-Standort-VPN-Verbindung nicht mehr verfügbar ist, erhalten Domänencontroller in der VNet nicht Updates für Benutzerkonten und Gruppen in der lokalen Windows Server Active Directory vorgenommen jedoch. Um sicherzustellen, dass dies nicht der Fall ist, können Sie hohen Verfügbarkeit für die Standort-zu-Standort-VPN-Verbindung konfigurieren. Weitere Informationen finden Sie unter [hoch verfügbaren standortübergreifenden und VNet-VNet - Konnektivität](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-highlyavailable)
  
Notieren Sie sich jetzt die öffentliche IPv4-Adresse des Azure-VPN-Gateways für Ihr virtuelles Netzwerk aus der Ausgabe des folgenden Befehls:
  
```
Get-AzureRMPublicIpAddress -Name $publicGatewayVipName -ResourceGroupName $rgName
```

Konfigurieren Sie anschließend Ihre lokale VPN-Gerät an das Gateway Azure VPN-Verbindung. Weitere Informationen finden Sie unter [Configure VPN-Gerät](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpn-devices).
  
Sie benötigen folgende Informationen zum Konfigurieren Ihres lokalen VPN-Geräts:
  
- Die öffentliche IPv4-Adresse des Azure-VPN-Gateways
    
- Der IPSec-vorinstallierten Schlüssel für die Standort-zu-Standort-VPN-Verbindung (Tabelle V - Element 5 - Wert-Spalte).
    
Vergewissern Sie sich im nächsten Schritt, dass der Adressraum des virtuellen Netzwerks aus Ihrem lokalen Netzwerk erreichbar ist. In der Regel fügen Sie dazu Ihrem VPN-Gerät eine dem Adressraum des virtuellen Netzwerks entsprechende Route hinzu und senden diese Route anschließend an die restliche Weiterleitungsinfrastruktur Ihres Organisationsnetzwerks. Erkundigen Sie sich bei Ihrer IT-Abteilung, wie Sie vorgehen sollen.
  
Definieren Sie nun die Namen von drei Verfügbarkeitsgruppen. Füllen Sie Tabelle A aus.  
  
|**Element**|**Zweck**|**Verfügbarkeit des Namens**|
|:-----|:-----|:-----|
|1.  <br/> |Domänencontroller  <br/> |_______________________________  <br/> |
|2.  <br/> |AD FS-Server  <br/> |_______________________________  <br/> |
|3.  <br/> |Webanwendungsproxy-Server  <br/> |_______________________________  <br/> |
   
 **Tabelle A: verfügbarkeitssätze**
  
Sie benötigen diese Namen bei der Erstellung der virtuellen Computer in den Phasen 2, 3 und 4.
  
Erstellen Sie die neuen Verfügbarkeitsgruppen mithilfe der folgenden Azure PowerShell-Befehle.
  
```
$locName="<the Azure location for your new resource group>"
$rgName="<Table R - Item 1 - Resource group name column>"
$avName="<Table A - Item 1 - Availability set name column>"
New-AzureRMAvailabilitySet -Name $avName -ResourceGroupName $rgName -Location $locName
$rgName="<Table R - Item 2 - Resource group name column>"
$avName="<Table A - Item 2 - Availability set name column>"
New-AzureRMAvailabilitySet -Name $avName -ResourceGroupName $rgName -Location $locName
$rgName="<Table R - Item 3 - Resource group name column>"
$avName="<Table A - Item 3 - Availability set name column>"
New-AzureRMAvailabilitySet -Name $avName -ResourceGroupName $rgName -Location $locName
```

Haben Sie diese Phase erfolgreich abgeschlossen, sieht Ihre Konfiguration wie folgt aus.
  
**Phase 1: Der Azure-Infrastruktur für hohe Verfügbarkeit Verbundauthentifizierung für Office 365**

![Phase 1 der hochverfügbaren Office 365-Verbundauthentifizierung in Azure mit der Azure-Infrastruktur](images/4e7ba678-07df-40ce-b372-021bf7fc91fa.png)
  
## <a name="next-step"></a>Nächster Schritt

Verwendung [hoher Verfügbarkeit federated Authentifizierung Phase 2: Konfigurieren von Domänencontrollern](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) um die Konfiguration der Arbeitslast fortzusetzen.
  
## <a name="see-also"></a>Weitere Artikel

[Bereitstellen der Verbundauthentifizierung mit Hochverfügbarkeit für Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)
  
[Verbundidentität für Ihre Office 365-Entwicklungs-/Testumgebung](federated-identity-for-your-office-365-dev-test-environment.md)
  
[Cloudakzeptanz und Hybridlösungen](cloud-adoption-and-hybrid-solutions.md)

[Verbundidentität für Office 365](https://support.office.com/article/Understanding-Office-365-identity-and-Azure-Active-Directory-06a189e7-5ec6-4af2-94bf-a22ea225a7a9#bk_federated)


