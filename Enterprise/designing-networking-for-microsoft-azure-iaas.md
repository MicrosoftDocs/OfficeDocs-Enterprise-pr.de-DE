---
title: Entwerfen von Netzwerken für Microsoft Azure-IaaS
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/28/2018
audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 9cb70c9d-9ed9-47cc-af5a-6403d87d3372
description: 'Zusammenfassung: Hier erfahren Sie, wie Sie das optimierte Netzwerk für Arbeitsauslastungen in Microsoft Azure IaaS entwerfen.'
ms.openlocfilehash: b06564c8a86c59dac4ac9a5380cd88cf9d045974
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068131"
---
# <a name="designing-networking-for-microsoft-azure-iaas"></a>Entwerfen von Netzwerken für Microsoft Azure-IaaS

 **Zusammenfassung:** Hier erfahren Sie, wie Sie das optimierte Netzwerk für Arbeitsauslastungen in Microsoft Azure IaaS entwerfen.
  
Um Netzwerke für IT-Workloads, die in Azure IaaS gehostet werden, optimieren zu können, benötigen Sie als Voraussetzung grundlegende Kenntnisse über Azure Virtual Networks (VNets), Adressräume, Routing, DNS und Lastenausgleich.
  
## <a name="planning-steps-for-any-vnet"></a>VNet-Planungsschritte

Führen Sie die folgenden Schritte für jede Art von VNet aus.
  
### <a name="step-1-prepare-your-intranet-for-microsoft-cloud-services"></a>Schritt 1: Bereiten Sie das Intranet für Microsoft Cloud Services vor.

Durchlaufen Sie die **Schritte zum Vorbereiten Ihres Netzwerks für Microsoft Cloud Services** in [Gemeinsame Elemente der Microsoft-Cloudkonnektivität](common-elements-of-microsoft-cloud-connectivity.md).
  
### <a name="step-2-optimize-your-internet-bandwidth"></a>Schritt 2: Optimieren Sie die Internetbandbreite.

Optimieren Sie die Internetbandbreite mithilfe der Schritte 2 bis 4 der **Schritte zum Vorbereiten Ihres Netzwerks für Microsoft SaaS-Dienste** in [Designing networking for Microsoft SaaS](designing-networking-for-microsoft-saas.md).
  
### <a name="step-3-determine-the-type-of-vnet-cloud-only-or-cross-premises"></a>Schritt 3: Bestimmen Sie den VNet-Typ (reine Cloudbereitstellung oder standortübergreifend).

Eine reines Cloud-VNet hat keine Verbindung mit einem lokalen Netzwerk. Hier ein Beispiel:
  
**Abbildung 1: Reines Cloud-VNet**

![Abbildung 1: ein virtuelles Cloud-Netzwerk in Azure](media/8be19104-02b3-4a7f-b0a0-30d6fcf8890b.png)
  
Abbildung 1 zeigt eine Reihe von virtuellen Computern in einem reinen Cloud-VNet.
  
Ein standortübergreifendes VNet verfügt über ein Azure-Gateway über eine S2S-VPN-Verbindung (Standort-zu-Standort) oder eine ExpressRoute-Verbindung zu einem lokalen Netzwerk. Hier ein Beispiel:
  
**Abbildung 2: Ein standortübergreifendes VNet**

![Abbildung 2: ein standortübergreifendes virtuelles Netzwerk in Azure](media/caacf007-e0dc-45d3-9531-441109776d25.png)
  
Abbildung 2 zeigt eine Reihe von virtuellen Computern in einem standortübergreifenden VNet, das mit einem lokalen Netzwerk verbunden ist.
  
Weitere [Planungsschritte für ein standortübergreifendes VNet](designing-networking-for-microsoft-azure-iaas.md#cross_prem) finden Sie im entsprechenden Abschnitt in diesem Artikel.
  
### <a name="step-4-determine-the-address-space-of-the-vnet"></a>Schritt 4: Ermitteln Sie den VNet-Adressraum.

In Tabelle 1 sind die Adressräume für die verschiedenen VNet-Typen aufgeführt.
  
|**Typ des VNet**|**Adressraum des virtuellen Netzwerks**|
|:-----|:-----|
|Rein cloudbasiert  <br/> |Beliebiger privater Adressraum  <br/> |
|Miteinander verbunden, reine Cloudbereitstellung  <br/> |Beliebiges privates, jedoch nicht überlappend mit anderen verbundenen VNets  <br/> |
|Standortübergreifend  <br/> |Privater Adressraum, der jedoch nicht mit lokalen VNets überlappt  <br/> |
|Miteinander verbunden, standortübergreifend  <br/> |Privater Adressraum, der jedoch nicht mit lokalen und anderen verbundenen VNets überlappt  <br/> |
   
 **Tabelle 1: VNet-Typen und ihr entsprechender Adressraum**
  
Virtuellen Computern wird vom Adressraum des Subnetzes durch DHCP ein Adresskonfiguriation zugewiesen:
  
- Adresse/Subnetzmaske
    
- Standardgateway
    
- IP-Adressen des DNS-Servers
    
Sie können auch eine statische IP-Adresse reservieren.
  
Virtuellen Computern kann auch eine öffentliche IP-Adresse zugewiesen werden, entweder einzeln oder über den enthaltenden Clouddienst (nur für herkömmliche Bereitstellungscomputer).
  
### <a name="step-5-determine-the-subnets-within-the-vnet-and-the-address-spaces-assigned-to-each"></a>Schritt 5: Bestimmen Sie die Subnetze im VNet und die ihnen zugewiesenen Adressräume.

Es gibt zwei Arten von Subnetzen in einem VNet: ein Gatewaysubnetz und ein Hostingsubnetz für virtuelle Computer.
  
**Abbildung 3: Die zwei Arten von Subnetzen in Azure**

![Abbildung 3: Die zwei Arten von Subnetzen in Azure](media/2eaa512d-1293-4e9b-b927-6bfe0fc0acb4.png)
  
Abbildung 3 zeigt eine VNet mit einem Gateway-Subnetz, das über ein Azure-Gateway und einen Satz virtueller Computer gehosteter Subnetze mit virtuellen Computern verfügt.
  
Azure benötigt das Azure-Gatewaysubnetz zum Hosten der beiden virtuellen Computer Ihres Azure-Gateways. Angeben eines Adressraums mit einer Präfixlänge von mindestens 29 Bit (Beispiel: 192.168.15.248/29). Eine 27-Bit-oder eine kleinere Präfixlänge wird empfohlen, insbesondere, wenn Sie Express Route verwenden möchten.
  
Eine bewährte Methode zum Bestimmen des Adressraums des Azure-Gateway-Subnetzes ist:
  
1. Legen Sie die Größe des Gatewaysubnetzes fest.
    
2. Legen Sie für die variablen Bits im Adressraum des VNet die Bits für das Gatewaysubnetz auf 0 und für die anderen Bits auf 1 fest.
    
3. Konvertieren Sie dies in eine Dezimalzahl, und drücken Sie diese als Adressraum aus, wobei Sie als Präfixlänge die Größe des Gatewaysubnetzes festlegen.
    
Wenn Sie diese Methode verwenden, befindet sich der Adressraum für das Gatewaysubnetz immer am äußersten Ende des VNet-Adressbereichs.
  
Es folgt ein Beispiel für die Definition des Adresspräfixes für das Gatewaysubnetz: Der Adressraum des VNet ist 10.119.0.0/16. Die Organisation verwendet anfänglich eine Standort-zu-Standort-VPN-Verbindung, später jedoch ExpressRoute. In Tabelle 2 sind die Schritte sowie die Ergebnisse der Ermittlung des Adresspräfixes in der Netzwerkpräfixnotation für das Gatewaysubnetz aufgeführt (auch als CIDR bezeichnet).

Nachfolgend finden Sie die Schritte und Beispiele zum Bestimmen des Gateway-Subnetz-Adress Präfixes:

1. Legen Sie die Größe des Gatewaysubnetzes fest. Für unser Beispiel haben wir uns für/28 entschieden.
2. Legen Sie die Bits im Variablen Teil des VNet-Adressraums (b) auf 0 für die Gateway-Subnetz-Bits (G) fest, andernfalls 1 (V). Für unser Beispiel verwenden wir den 10.119.0.0/16-Adressraum für die VNet.
<br/>
<br/>10,119. bbbbbbbb. bbbbbbbb
<br/>10,119. VVVVVVVV . VVVVGGGG
<br/>10,119. 11111111. 11110000
<br/><br/>
3. Konvertieren Sie das Ergebnis aus Schritt 2 in Dezimal und Express als Adressraum. Für unser Beispiel 10,119. 11111111. 11110000 ist 10.119.255.240, und mit der Präfixlänge aus Schritt 1 (28 in unserem Beispiel) lautet das resultierende Gateway-Subnetz-Adresspräfix 10.119.255.240/28.
  
Weitere Informationen finden Sie unter [Adressraum Rechner für Azure-Gateway](https://gallery.technet.microsoft.com/scriptcenter/Address-prefix-calculator-a94b6eed) -Subnetze.
  
Sie platzieren virtuelle Azure-Computer in Hostingsubnetzen für virtuelle Computer, wobei Sie hier gemäß den typisch lokalen Richtlinien folgen können, wie z. B. einer allgemeinen Rolle oder Ebene einer Anwendung oder für die Subnetzisolierung.
  
Azure verwendet die ersten drei Adressen in jedem Subnetz. Daher ist die Anzahl der möglichen Adressen in einem Azure-Subnetz 2<sup>n</sup> -5, wobei n die Anzahl der Host-Bits ist. In Tabelle 3 sind der Bereich der erforderlichen virtuellen Computer, die Anzahl der erforderlichen Hostbits und die entsprechende Subnetzgröße aufgeführt.
  
|**Erforderliche virtuelle Computer**|**Hostbits**|**Subnetzgröße**|
|:-----|:-----|:-----|
|1-3  <br/> |3  <br/> |/29  <br/> |
|4-11  <br/> |4  <br/> |/28  <br/> |
|12-27  <br/> |5  <br/> |/27  <br/> |
|28-59  <br/> |6  <br/> |/26  <br/> |
|60-123  <br/> |7  <br/> |/25  <br/> |
   
 **Tabelle 3: Anforderungen der virtuellen Computer und ihre Subnetzgrößen**
  
Weitere Informationen zur maximalen Anzahl von virtuellen Computern in einem Subnetz oder VNet finden Sie unter [Networking Limits](https://docs.microsoft.com/azure/azure-subscription-service-limits#networking-limits).
  
Weitere Informationen finden Sie unter [Planen und Entwerfen von virtuellen Azure-Netzwerken](https://azure.microsoft.com/documentation/articles/virtual-network-vnet-plan-design-arm/).
  
### <a name="step-6-determine-the-dns-server-configuration-and-the-addresses-of-the-dns-servers-to-assign-to-vms-in-the-vnet"></a>Schritt 6: Ermitteln Sie die DNS-Serverkonfiguration und die Adressen der DNS-Server, die den VMs im VNet zugewiesen werden sollen.

Azure weist virtuellen Computern die Adressen der DNS-Server über DHCP zu. DNS-Server können:
  
- durch Azure bereitgestellt werden: Bietet lokale Namensregistrierung sowie lokale und über das Internet durchgeführte Namensauflösung
    
- von Ihnen bereitgestellt werden: Bietet lokale oder über das Internet durchgeführte Namensregistrierung und Namensauflösung entweder über das Intranet oder über das Internet
    
In Tabelle 4 sind die verschiedenen DNS-Serverkonfigurationen für jeden VNet-Typ aufgeführt.
    
|**Typ des VNet**|**DNS-Server**|
|:-----|:-----|
|Rein cloudbasiert  <br/> |von Azure für die lokale und über das Internet durchgeführte Namensauflösung bereitgestellt  <br/> virtueller Azure-Computer für die lokale und über das Internet durchgeführte Namensauflösung (DNS-Weiterleitung)  <br/> |
|Standortübergreifend  <br/> |lokal für die lokale und über das Intranet durchgeführte Namensauflösung  <br/> virtueller Azure-Computer für die lokale und über das Intranet durchgeführte Namensauflösung (DNS-Replikation und -Weiterleitung)  <br/> |
   
 **Tabelle 4: DNS-Serveroptionen für die beiden verschiedenen VNet-Typen**
  
Weitere Informationen finden Sie unter [Namensauflösung für VMS und Rolleninstanzen](https://docs.microsoft.com/azure/virtual-network/virtual-networks-name-resolution-for-vms-and-role-instances).
  
### <a name="step-7-determine-the-load-balancing-configuration-internet-facing-or-internal"></a>Schritt 7: Ermitteln Sie die Lastenausgleichskonfiguration (Internet-bezogen oder intern).

In einigen Fällen möchten Sie eingehenden Datenverkehr auf eine Gruppe von Servern verteilen, die über die gleiche Rolle verfügen. Azure IaaS verfügt über eine integrierte Funktion, mit der dies für dem Internet zugewandten und internen Datenverkehr vorgenommen werden kann.
  
Der dem Internet zugewandte Lastenausgleich von Azure verteilt den unangefordert aus dem Internet kommenden Datenverkehr zufällig auf die Mitglieder einer Lastenausgleichsgruppe. 
  
**Abbildung 4: Ein externer Lastenausgleich in Azure**

![Abbildung 4: Ein externer Lastenausgleich in Azure](media/eb5945e5-0c2b-40f1-b9ed-54bb2b0f9e59.png)
  
Abbildung 4 zeigt einen externen Lastenausgleich in Azure, der eingehenden Datenverkehr über eine eingehende NAT-Regel oder einen Endpunkt an eine Gruppe virtueller Computer in einem Satz mit Lastenausgleich verteilt.
  
Der Azure-interne Lastenausgleich verteilt unangeforderten eingehenden Datenverkehr von andere Azure-VMs oder Intranetcomputern an die Mitglieder einer Lastenausgleichsgruppe.  
  
**Abbildung 5: Ein interner Lastenausgleich in Azure**

![Abbildung 5: Ein interner Lastenausgleich in Azure](media/d1451b73-6465-449d-b3e6-22160ce51f35.png)
  
Abbildung 5 zeigt einen internen Lastenausgleich in Azure, der eingehenden Datenverkehr für eine eingehende NAT-Regel oder einen Endpunkt an eine Gruppe virtueller Computer in einem Satz mit Lastenausgleich verteilt.
  
Weitere Informationen finden Sie unter [Azure-Lastenausgleichsmodul](https://docs.microsoft.com/azure/load-balancer/load-balancer-overview).
  
### <a name="step-8-determine-the-use-of-virtual-appliances-and-user-defined-routes"></a>Schritt 8: Ermitteln Sie die Verwendung von virtuellen Geräten und benutzerdefinierten Routen.

Wenn Sie Datenverkehrs an virtuelle Geräte im VNet weiterleiten müssen, müssen Sie einem Subnetz möglicherweise eine oder mehrere benutzerdefinierte Routen hinzufügen.
  
**Abbildung 6: Virtuelle Geräte und benutzerdefinierte Routen in Azure**

![Abbildung 6: Virtuelle Geräte und benutzerdefinierte Routen in Azure](media/f181d0f4-ebf9-439e-9c98-dec17428c32b.png)
  
Abbildung 6 zeigt ein standortübergreifendes VNet und eine benutzerdefinierte Route, die einem Hostingsubnetz für virtuelle Computer zugewiesen ist, das auf ein virtuelles Gerät verweist.
  
Weitere Informationen finden Sie unter [benutzerdefinierte Routen und IP-Weiterleitung](https://docs.microsoft.com/azure/virtual-network/virtual-networks-udr-overview).
  
### <a name="step-9-determine-how-computers-from-the-internet-will-connect-to-virtual-machines"></a>Schritt 9 Ermitteln Sie, wie Computer aus dem Internet Verbindungen mit virtuellen Computern herstellen.

Es gibt mehrere Möglichkeiten, den virtuellen Computern in einem VNet Zugang zum Internet bereitzustellen. Dazu zählt der Zugriff vom Netzwerk Ihrer Organisation über einen Proxyserver oder ein anderes Edgegerät.
  
In Tabelle 5 sind die Methoden zum Filtern oder Prüfen von unangefordert eingehendem Datenverkehr aufgeführt.
  
|**Methode**|**Bereitstellungsmodell**|
|:-----|:-----|
|1. Endpunkte und ACLs, für Clouddienste konfiguriert  <br/> |Classic  <br/> |
|2. Netzwerksicherheitsgruppen  <br/> |Ressourcenmanager und klassisch  <br/> |
|3. Dem Internet zugewandter Lastenausgleich mit NAT-Eingangsregeln  <br/> |Ressourcenmanager  <br/> |
|4. Netzwerksicherheits-Appliances im Azure Marketplace (nicht dargestellt)  <br/> |Ressourcenmanager und klassisch  <br/> |
   
 **Tabelle 5: Methoden zum Herstellen einer Verbindung mit virtuellen Computern und ihre entsprechenden Azure-Bereitstellungsmodelle**
  
**Abbildung 7: Herstellen einer Verbindung mit virtuellen Azure-Computern über das Internet**

![Abbildung 7: Herstellen einer Verbindung mit virtuellen Azure-Computern über das Internet](media/c5e3531b-170a-4482-a6ff-fb8fbbe81b35.png)
  
Abbildung 7 zeigt einen mit dem Internet verbundenen Computer, der mit einem virtuellen Computer in einem Clouddienst anhand eines Endpunkts verbunden ist, einen virtuellen Computer in einem Subnetz mit einer Netzwerksicherheitsgruppe und einen virtuellen Computer in einem Subnetz mit einem externen Lastenausgleich und NAT-Eingangsregeln.
  
Zusätzlicher Sicherheit bereitgestellt durch:
  
- Remotedesktop- und SSH-Verbindungen, die verschlüsselt und authentifiziert werden
    
- Remote PowerShell-Sitzungen, die verschlüsselt und authentifiziert werden
    
- IPsec-Transportmodus, den Sie für die End-to-End-Verschlüsselung verwenden können
    
- Azure DDOS-Schutz, der vor externe und interne Angriffen schützt
    
Weitere Informationen finden Sie unter [Microsoft Cloud Security for Enterprise Architects](https://aka.ms/cloudarchsecurity) und [Azure Network Security](https://azure.microsoft.com/blog/azure-network-security/).
  
### <a name="step-10-for-multiple-vnets-determine-the-vnet-to-vnet-connection-topology"></a>Schritt 10 Bestimmen Sie für mehrere VNets die Verbinungstopologie von VNet zu VNet.

VNets können mit ähnlichen Topologien verbunden werden, die auch zum Verbinden von Standorten einer Organisation verwendet werden.
  
Durch eine Verkettungskonfiguration (Daisychain) werden die VNets in einer Reihe verbunden.
  
**Abbildung 8: Eine Verkettungskonfiguration für VNets**

![Abbildung 8: eine kaskadierte Konfiguration für virtuelle Azure-Netzwerke](media/264d5dd4-06c5-483f-9428-a18cc1f68ac1.png)
  
Abbildung 8 zeigt fünf VNets, die in einer Reihe mit einer kaskadierten Konfiguration verbunden sind.
  
Bei einer Hub-Spoke-Konfiguration werden mehrere VNets mit eine Reihe von zentralen VNets verbunden, die ihrerseits miteinander verbunden sind.
  
**Abbildung 9: Eine Hub-Spoke-Konfiguration für VNets**

![Abbildung 9: eine Spoke-und Hub-Konfiguration für virtuelle Azure-Netzwerke](media/dd442a38-5b76-4ac5-b743-8fc7711a91ba.png)
  
Abbildung 9 zeigt sechs VNets, wobei zwei VNets „Hubs“ sind, die miteinander sowie mit anderen „Spoke“-VNets verbunden sind.
  
Bei einer Full-Mesh-Konfiguration ist jedes VNet mit jedem anderen verbunden.
  
**Abbildung 10: Eine Full-Mesh-Konfiguration für VNets**

![Abbildung 10: eine Netzkonfiguration für virtuelle Azure-Netzwerke](media/9dda0738-10db-4a63-95b3-79851a399b71.png)
  
Abbildung 10 zeigt vier VNets, die alle miteinander verbunden sind, wobei insgesamt sechs VNet-zu-VNet-Verbindungen vorhanden sind.
  
## <a name="planning-steps-for-a-cross-premises-vnet"></a>Planungsschritte für ein standortübergreifendes VNet
<a name="cross_prem"> </a>

Führen Sie die folgende Schritte durch, um ein stadortübergreifendes VNet zu erstellen.
  
> [!TIP]
> Wie Sie eine simulierte standortübergreifende Entwicklungs-/Testumgebung einrichten, können Sie unter [Simulated cross-premises virtual network in Azure](simulated-cross-premises-virtual-network-in-azure.md) nachlesen. 
  
### <a name="step-1-determine-the-cross-premises-connection-to-the-vnet-s2s-vpn-or-expressroute"></a>Schritt 1: Ermitteln Sie die standortübergreifende Verbindung zum VNet (S2S-VPN oder ExpressRoute).

In Tabelle 6 sind die verschiedenen Verbindungstypen aufgeführt.
  
|**Verbindungstyp**|**Zweck**|
|:-----|:-----|
|Standort-zu-Standort-VPN (S2S)  <br/> |Verbinden Sie 1-10-Websites (einschließlich anderer VNets) mit einem einzelnen VNet.  <br/> |
|ExpressRoute  <br/> |Eine private, sichere Verbindung mit Azure über einen Internet-Exchange-Anbieter (IXP) oder ein Netzwerkdienstanbieter (NSP).  <br/> |
|Punkt-zu-Standort-VPN (P2S)  <br/> |Verbindet einen einzelnen Computer mit einem VNet  <br/> |
|VNet-Peering oder VNet-zu-VNet-VPN (V2V)   <br/> |Verbindet ein VNet mit einem anderen VNet  <br/> |
   
 **Tabelle 6: Die Verbindungstypen für standortübergreifende VNets**
  
Weitere Informationen zur maximalen Anzahl von Verbindungen finden Sie unter [Networking Limits](https://docs.microsoft.com/azure/azure-subscription-service-limits#networking-limits).
  
Weitere Informationen zu VPN-Geräten finden Sie unter [VPN Devices for Site-to-Site Virtual Network Connections](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpn-devices).
  
Weitere Informationen zu VNet-Peering finden Sie unter [VNet Peering](https://docs.microsoft.com/azure/virtual-network/virtual-network-peering-overview).
  
**Abbildung 11: Die vier Verbindungsarten mit einem standortübergreifenden VNet**

![Abbildung 11: die drei Möglichkeiten zum Herstellen einer Verbindung mit einem standortübergreifenden virtuellen Azure-Netzwerk](media/d5d4a625-cfbd-4a77-9159-eaca69d07e93.png)
  
Abbildung 11 zeigt eine VNet mit den vier Verbindungstypen: eine P2S-Verbindung von einem Computer, eine S2S-VPN-Verbindung von einem lokalen Netzwerk, eine Express Route-Verbindung von einem lokalen Netzwerk und eine VNet-zu-VNet-Verbindung von einem anderen VNet. 
  
Sie können eine Verbindung mit VMs in einem VNet wie folgt herstellen:
  
- Verwaltung von VNet-VMs über das lokale Netzwerk oder das Internet
    
- IT-Workloadzugriff vom lokalen Netzwerk
    
- Erweiterung des Netzwerks durch zusätzliche VNets
    
Die Sicherheit der Verbindungen wird durch Folgendes sichergestellt:
  
- P2S verwendet SSTP (Secure Socket Tunnel Protocol).  
    
- S2S und VNet-zu-VNet-VPN-Verbindungen verwenden den IPsec-Tunnelmodus mit AES256.
    
- ExpressRoute ist eine private WAN-Verbindung.
    
Weitere Informationen finden Sie unter [Microsoft Cloud Security for Enterprise Architects](https://aka.ms/cloudarchsecurity) und [Azure Network Security](https://azure.microsoft.com/blog/azure-network-security/).
  
### <a name="step-2-determine-the-on-premises-vpn-device-or-router"></a>Schritt 2: Ermitteln Sie das lokale VPN-Gerät oder den Router.

Ihr lokales VPN-Gerät oder der Router fungiert als:
  
- ein IPSec-Peer, der die S2S-VPN-Verbindung von einem Azure-Gateway trennt.
    
- der BPG-Peer und Abschlusspunkt für die private ExpressRoute-Peeringverbindung.
    
**Abbildung 12: Lokaler VPN-Router oder lokales Gerät**

![Abbildung 12: Lokaler VPN-Router oder lokales Gerät](media/bd221468-a660-4730-aa55-0426986480b9.png)
  
Abbildung 12 zeigt eine standortübergreifendes VNet, das mit einem lokalen VPN-Router oder einem Gerät verbunden ist.
  
Weitere Informationen finden Sie unter [Informationen zum VPN-Gateway](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpngateways).
  
### <a name="step-3-add-routes-to-your-intranet-to-make-the-address-space-of-the-vnet-reachable"></a>Schritt 3: Hinzufügen von Routen zu Ihrem Intranet, um den Adressraum des VNet erreichbar zu machen.

Die Weiterleitung an VNets von lokal umfasst Folgendes:
  
1. Eine Route für den VNet-Adressraum, die auf Ihr VPN-Gerät verweist.
    
2. Eine Route für den VNet-Adressraum auf Ihrem VPN-Gerät, die über die S2S-VPN- oder ExpressRoute-Verbindung hinweg verweist.
    
**Abbildung 13: Ein VNet muss durch lokale Routen erreichbar gemacht werden**

![Abbildung 13: die lokalen Routen, die erforderlich sind, um eine Azure-VNet erreichbar zu machen](media/7a1e20c1-fbc4-4cb9-9961-735da4e23307.png)
  
Abbildung 13 zeigt die Routinginformationen, die von den lokalen Routern benötigt werden, sowie den VPN-Router oder das Gerät, das den Adressraum das VNets darstellt.
  
### <a name="step-4-for-expressroute-plan-for-the-new-connection-with-your-provider"></a>Schritt 4: Planen Sie bei Verwendung von ExpressRoute die neue Verbindung mit Ihrem Anbieter.

Sie haben drei verschiedene Möglichkeiten, um eine ExpressRoute-Verbindung mit privatem Peering zwischen Ihrem lokalen Netzwerk und der Microsoft-Cloud herzustellen:
  
- Co-Location bei einem Cloud Exchange
    
- Punkt-zu-Punkt-Ethernet-Verbindungen
    
- Viele-zu-viele-Netzwerke (IP-VPN)
    
**Abbildung 14: Verwenden von ExpressRoute für Verbindungen zu einem standortübergreifenden VNet**

![Abbildung 14: Verwenden von Express Route zum Herstellen einer Verbindung mit einem standortübergreifenden virtuellen Azure-Netzwerk](media/7030bd39-69a6-4283-8567-3434e1ab6ba6.png)
  
Abbildung 14 zeigt ein standortübergreifendes VNet und eine ExpressRoute-Verbindung von einem lokalen Router zu Microsoft Azure.
  
Weitere Informationen finden Sie unter [ExpressRoute für Microsoft-Cloudkonnektivität](expressroute-for-microsoft-cloud-connectivity.md).
  
### <a name="step-5-determine-the-local-network-address-space-for-the-azure-gateway"></a>Schritt 5: Bestimmen Sie den lokalen Netzwerkadressraum für das Azure-Gateway.

Beim Routing zu lokalen oder anderen VNets von einem VNet leitet Azure den Datenverkehr über einen Azure-Gateway, der mit dem lokalen Netzwerkadressraum übereinstimmt, der dem Gateway zugeordnet ist.
  
**Abbildung 15: Adressraum des lokalen Netzwerks für ein standortübergreifendes VNet**

![Abbildung 15: der lokale Netzwerk Adressraum für ein standortübergreifendes virtuelles Azure-Netzwerk](media/e3af2652-8b8e-4551-9a0b-b550e6e7e3c0.png)
  
Abbildung 15 zeigt eine standortübergreifendes VNet und den Adressraum des lokalen Netzwerks auf dem Azure-Gateway, der den erreichbaren Adressraum im lokalen Netzwerk darstellt.  
  
Sie können den Adressraum des lokalen Netzwerks auf folgende Weise definieren:
  
- Option 1: Die Liste der Präfixe für den gerade benötigten oder verwendeten Adressraum (Aktualisierungen können erforderlich sein, wenn Sie neue Subnetzen hinzufügen).
    
- Option 2: Der gesamte lokale Adressraum (Aktualisierungen sind nur nötig, wenn Sie einen neuen Adressraum hinzufügen).
    
Da das Azure-Gateway keine zusammengefassten Routen zulässt, müssen Sie den Adressraum des lokalen Netzwerk bei der Option 2 so definieren, dass er nicht den VNet-Adressraum enthält.
  
**Abbildung 16: Die durch den VNet-Adressraum erzeugte Lücke im Adressraum**

![Abbildung 16: die vom Adressraum des virtuellen Netzwerks erstellte Adressraum Bohrung](media/e79c4840-f9e3-4741-9b72-59db6043aefa.png)
  
Abbildung 16 zeigt eine Darstellung eines Adressraums mit dem Stammraum und dem VNet-Adressraum.
  
Nachfolgend finden Sie ein Beispiel für das Definieren der Präfixe für den Adressraum des lokalen Netzwerks um den Adressraum "Hole", der vom VNet erstellt wurde:
  
- Eine Organisation verwendet Teile des privaten Adressraums (10.0.0.0/8, 172.16.0.0/12 und 192.168.0.0/16) in ihrem lokalen Netzwerk. Die Organisation verwendet Option 2 und 10.100.100.0/24 als ihren VNet-Adressraum.
    
In Tabelle 7 sind die Schritte und die resultierenden Präfixe aufgeführt, die den Adressraum des lokalen Netzwerks in diesem Beispiel definieren.
  
|**Schritt**|**Ergebnisse**|
|:-----|:-----|
|1. Auflisten der Präfixe, die nicht der Stammraum für den VNet-Adressraum sind.  <br/> |172.16.0.0/12 und 192.168.0.0/16  <br/> |
|2. Auflisten der nicht überlappenden Präfixe für Variable Oktette bis einschließlich des zuletzt verwendeten Oktetts im VNet-Adressraum.  <br/> |10.0.0.0/16, 10.1.0.0/16... 10.99.0.0/16, 10.101.0.0/16... 10.254.0.0/16, 10.255.0.0/16 (255 Präfixe, Überspringen von 10.100.0.0/16)  <br/> |
|3. Listen Sie die nicht überlappenden Präfixe innerhalb des zuletzt verwendeten Oktetts des VNet-Adressraums auf.  <br/> |10.100.0.0/24, 10.100.1.0/24... 10.100.99.0/24, 10.100.101.0/24... 10.100.254.0/24, 10.100.0.255.0/24 (255 Präfixe, Überspringen von 10.100.100.0/24)  <br/> |
   
 **Tabelle 7: Beispiel für den Adressraum des lokalen Netzwerks**
  
### <a name="step-6-configure-on-premises-dns-servers-for-dns-replication-with-dns-servers-hosted-in-azure"></a>Schritt 6: Konfigurieren Sie lokale DNS-Server für die DNS-Replikation mit DNS-Servern, die in Azure gehostet werden.

Um sicherzustellen, dass lokale Computer die Namen von Servern in Azure und die Server in Azure die Namen von lokalen Computern auflösen können, müssen Sie Folgendes konfigurieren:
  
- Die DNS-Server in Ihrem VNet leiten an lokale DNS-Server weiter
    
- DNS-Replikation der entsprechenden Zonen zwischen lokalen DNS-Servern und im VNet
    
**Abbildung 17: DNS-Replikation und -Weiterleitung für einen DNS-Server in einem standortübergreifenden VNet**

![Abbildung 17: DNS-Replikation und-Weiterleitung für einen DNS-Server in einem standortübergreifenden virtuellen Azure-Netzwerk](media/ab55e5ce-ccb0-49d4-a301-657a727f97b2.png)
  
Abbildung 17 zeigt ein standortübergreifendes VNet mit DNS-Server im lokalen Netzwerk und in einem Subnetz im. DNS-Replikation und -Weiterleitung wurde zwischen den beiden DNS-Servern konfiguriert.
  
### <a name="step-7-determine-the-use-of-forced-tunneling"></a>Schritt 7: Ermitteln Sie die Nutzung von erzwungenem Tunneln.

Die standardmäßige System Route für Azure-Subnetze weist auf das Internet hin. Um sicherzustellen, dass der gesamte Datenverkehr von virtuellen Computern über die standortübergreifende Verbindung übertragen wird, erstellen Sie eine Routingtabelle mit der Standardroute, die das Azure-Gateway als Adresse des nächsten Hops verwendet. Anschließend ordnen Sie die Routentabelle dem Subnetz zu. Dies wird auch als Tunnelerzwingung bezeichnet. Weitere Informationen finden Sie unter [configure Forced Tunneling](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-forced-tunneling-rm).
  
**Abbildung 18: Benutzerdefinierte Routen und erzwungenes Tunneln für ein standortübergreifendes VNet**

![Abbildung 18: benutzerdefinierte Routen und erzwungenes Tunneln für ein standortübergreifendes virtuelles Azure-Netzwerk](media/1e545ec6-c2d9-48d2-bb5e-e0a581fee004.png)
  
Abbildung 18 zeigt einen standortübergreifenden VNet mit einer benutzerdefinierten Route für ein Subnetz, das auf das Azure-Gateway verweist.
  
## <a name="sharepoint-server-2016-farm-in-azure"></a>SharePoint Server 2016-Farm in Azure
<a name="cross_prem"> </a>

Ein Beispiel für eine Intranet-IT-Arbeitslast, die in Azure IaaS gehostet wird, ist eine hoch verfügbare, mehrstufige SharePoint Server-2016-Farm.
  
**Abbildung 19: Hoch verfügbare SharePoint Server 2016-Intranetfarm in Azure IaaS**

![Eine SharePoint Server 2016-Farm mit hoher Verfügbarkeit in Azure IaaS](media/3a922e21-df91-455f-ba90-78abdd48d98d.png)
  
Abbildung 19 zeigt die neun Server einer SharePoint Server 2016-Farm, die in einem standortübergreifenden VNet bereitgestellt wird und interne Lastenausgleichsmodule für die Front-End-und Datenebenen verwendet. Weitere Informationen, einschließlich Schritt-für-Schritt-Anleitungen zum Entwerfen und bereitstellen, finden Sie unter [SharePoint Server 2016 in Microsoft Azure](https://docs.microsoft.com/SharePoint/administration/sharepoint-server-2016-in-microsoft-azure).
  
> [!TIP]
> Informationen zum Erstellen einer SharePoint Server 2016-Farm mit einem Server in einer simulierten standortübergreifenden VNet finden Sie unter [Intranet SharePoint Server 2016 in Azure dev/Test Environment](https://docs.microsoft.com/SharePoint/administration/intranet-sharepoint-server-2016-in-azure-dev-test-environment). 
  
Weitere Beispiele für IT-Arbeitslasten, die auf virtuellen Computern in einem standortübergreifenden virtuellen Azure-Netzwerk bereitgestellt werden, finden Sie unter [Hybrid Cloud Scenarios for Azure IaaS](https://docs.microsoft.com/office365/enterprise/hybrid-cloud-scenarios-for-azure-iaas).
  
## <a name="see-also"></a>Siehe auch

[Microsoft-Cloudnetzwerke für Enterprise-Architekten](microsoft-cloud-networking-for-enterprise-architects.md)
  
[Ressourcen zur Cloud-IT-Architektur von Microsoft](microsoft-cloud-it-architecture-resources.md)


