---
title: Client-Konnektivität
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 7/6/2017
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 4232abcf-4ae5-43aa-bfa1-9a078a99c78b
description: 'Zusammenfassung: erläutert, wie Clientcomputer eine Verbindung zu Office 365-Mandanten herstellen, je nach Standort des Clientcomputers und des Office 365-Mandantendaten Centers.'
ms.openlocfilehash: d101af5a0fdd4e29e366b34ad1ab682489f6b3ca
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068201"
---
# <a name="client-connectivity"></a>Client-Konnektivität

 **Zusammenfassung:** Erläutert, wie Clientcomputer eine Verbindung zu Office 365-Mandanten herstellen, je nach Standort des Clientcomputers und des Office 365-Mandantendaten Centers.
  
Office 365 befindet sich in Microsoft-Rechenzentren auf der ganzen Welt, die den Dienst auch dann in Betrieb halten, wenn ein großes Problem in einer Region auftritt, beispielsweise ein Erdbeben oder ein Stromausfall. Wenn Sie eine Verbindung mit Ihrem Office 365-Mandanten herstellen, wird die Clientverbindung an das entsprechende Datencenter weitergeleitet, in dem Ihr Mandant gehostet wird. Die Regeln, die bestimmen, wo Ihr Mandant gehostet werden kann, werden in ihrer Vereinbarung mit Microsoft definiert. Die Regeln, mit denen bestimmt wird, wie der Client die Daten von diesem Datacenter-Speicherort erwirbt, hängt von der Architektur des Diensts ab, den Sie verwenden.
  
Wenn Sie sich beispielsweise beim Office 365-Portal anmelden, sind Sie normalerweise mit dem nächstgelegenen Datencenter mit dem Client verbunden und dann abhängig von dem Dienst, den Sie als nächstes verwenden. Wenn Sie eine e-Mail-Nachricht starten, kann die anfängliche Verbindung zum Anzeigen der Benutzeroberfläche weiterhin vom nächsten Datencenter stammen, aber möglicherweise wird eine zweite Verbindung zwischen dem nächsten Datencenter und dem Datencenter geöffnet, in dem sich Ihr Mandant befindet, um zu zeigen, welche e-Mails Sie lesen. Microsoft betreibt eines der zehn führenden Netzwerke der Welt, was zu unglaublich schnellen Datencenter-zu-Datacenter-Verbindungen führt.
  
Nachdem Sie den Artikel gelesen haben, werden Sie wahrscheinlich verstehen, warum wir keine [Office 365-URLs und IP-Adressbereiche](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2) pro Datencenter bereitstellen, Sie sind einfach zu miteinander verbunden und voneinander abhängig, um dies zu ermöglichen.
  
Wenn Sie Azure Express Route für Office 365 verwenden, wird Ihre Konnektivität in den meisten Fällen über eine private Verbindung zu Office 365 anstelle der hier beschriebenen öffentlichen Verbindung übertragen. Die Grundsätze zur Verbindung von Clients sind weiterhin genau. Erfahren Sie mehr über [Azure Express Route für Office 365](azure-expressroute.md).
  
Weitere Informationen zu Skype for Business-Netzwerkanforderungen finden Sie im Artikel [Medienqualität und Leistung der Netzwerkkonnektivität in Skype for Business Online](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917).

||
|:-----|
| Dieser Artikel ist Teil der [Netzwerkplanung und Leistungsoptimierung für Office 365](https://aka.ms/tune).|

> [!NOTE]
> Wir legen großen Wert darauf, Kundendaten so zu verwalten, dass Sie in unseren Rechenzentren sicher und privat sind. Details zu den Schritten, die wir zum Verwalten des Datenschutzes ergreifen, sind im [Trust Center](https://go.microsoft.com/fwlink/?LinkID=397383)enthalten.
  
## <a name="connecting-to-the-nearest-datacenter"></a>Herstellen einer Verbindung mit dem nächsten Datencenter

Dies ist der häufigste Verbindungstyp, der sowohl vom Office 365-Portal als auch von Exchange Online verwendet wird. Wenn Clients versuchen, eine Verbindung mit Office 365 herzustellen, bestimmt die DNS-Abfrage Ihres Computers in dieser Situation die Region der Welt, von der Ihr Computer stammt, und Office 365 leitet die Anforderung an das nächste Datencenter um.
  
Verbindungen mit dem Portal werden am nächstgelegenen Datencenter beendet, und auf dem Clientcomputer werden Informationen zum Mandanten des Clients von diesem Standort angezeigt.
  
Exchange Online geht einen Schritt weiter. Sobald der Clientcomputer mit dem nächstgelegenen Datencenter verbunden ist, stellt ein Exchange-Server in diesem Datencenter eine Verbindung mit dem Datencenter her, in dem sich der Mandant befindet, wie im folgenden *Abschnitt wie funktioniert diese Arbeit* dargestellt. Die Exchange Online-Server im nächstgelegenen Datencenter stellen dann die Proxyanforderungen vom Clientcomputer an den Postfachserver weiter. Dadurch wird die Erfahrung für den Clientcomputer beschleunigt, da das Abrufen von e-Mails und Kalenderelementen in das Microsoft-Netzwerk stark aufgehoben wird.
  
## <a name="how-does-this-work-for-standard-cloud-offerings"></a>Wie funktioniert das für Standard-Cloud-Angebote?

Dieser Verbindungsprozess ist Standard für hohe Datenverkehr, hochwertige Webanwendungen wie Office 365. In diesem Abschnitt werden die Schritte im Prozess erläutert und veranschaulicht. Wenn sich der Clientcomputer nicht in der gleichen Region wie der Mandant befindet, sieht die Verbindung abhängig vom Dienst, mit dem der Client eine Verbindung herstellt, viel anders aus.
  
 Dieses Diagramm zeigt einen Kunden mit einem standardmäßigen Office 365-Angebot mit einem Mandanten in Nordamerika. In diesem Szenario ist der Antragsteller nach Europa gereist und verwendet Office 365 von diesem Standort aus.
  
1. Der Clientcomputer fordert die lokalen DNS-Server für die IP-Adresse an, die Office 365 zugeordnet ist.

2. Die lokalen DNS-Server des Clientcomputers Fragen die Microsoft-DNS-Server nach der IP-Adresse, die Office 365 zugeordnet ist.

3. Microsoft-DNS-Server geben den Namen des regionalen Servers (basierend auf dem Speicherort der DNS-Server des Clients) zurück, und der Clientcomputer wiederholt die Schritte 1 und 2, um die IP-Adresse des regionalen Office 365-Datencenters abzurufen.

4. Der Clientcomputer stellt eine Verbindung mit der IP-Adresse des regionalen Datencenters her.

5. Die Exchange Online-Server stellen eine Verbindung mit dem aktiven Datencenter her, in dem sich der Mandant des Kunden befindet.

![Nächstes Regionales Rechenzentrum](media/4ea108e9-a299-4e3d-b0d3-469b434ff899.png)
  
## <a name="how-does-this-work-for-sovereign-cloud-offerings"></a>Wie funktioniert das für Sovereign Cloud-Angebote?

Diese Verbindung unterscheidet sich geringfügig für Sovereign Cloud-Angebote wie Office 365, betrieben von 21 vianet. Mit dem Mandanten in einer souveränen Instanz von Office 365 sind die nächsten Office 365-Server, die Portal Verbindungen akzeptieren, die Server innerhalb der Sovereign-Region, in der sich der Mandant befindet. Entsprechend werden Kunden, die auf SharePoint Online in unseren Sovereign Cloud-oder Standard angeboten zugreifen, an Front-End-Server weitergeleitet, auf denen sich der Mandant befindet. Weitere Informationen finden Sie unter Herstellen einer Verbindung mit dem aktiven Rechenzentrum.
  
1. Der Clientcomputer fordert die lokalen DNS-Server für die IP-Adresse an, die Office 365 zugeordnet ist.

2. Die lokalen DNS-Server des Clientcomputers Fragen die Microsoft-DNS-Server nach der IP-Adresse, die Office 365 zugeordnet ist.

3. Microsoft-DNS-Server geben den Namen des regionalen Servers (basierend auf dem Speicherort der DNS-Server des Clients) zurück, und der Clientcomputer wiederholt die Schritte 1 und 2, um die IP-Adresse des regionalen Office 365-Datencenters abzurufen.

4. Der Clientcomputer stellt eine Verbindung mit der IP-Adresse des regionalen Datencenters her.

5. Die Exchange Online-Server stellen eine Verbindung mit dem aktiven Datencenter her, in dem sich der Mandant des Kunden befindet.

![Nächstes regionales US-Rechenzentrum](media/c0628c54-0059-48c5-8a0f-41bf392ee182.png)
  
## <a name="connecting-to-the-active-datacenter"></a>Herstellen einer Verbindung mit dem aktiven Datencenter

Das Herstellen einer Verbindung mit dem aktiven Datencenter ist für schwerere Datenübertragungs Lasten vorgesehen und wird derzeit von SharePoint Online verwendet. Wenn Clients versuchen, eine Verbindung mit Office 365 herzustellen, wird der Browser in dieser Situation für den SharePoint Online-Mandanten zum aktiven Datencenter umgeleitet.
  
## <a name="how-does-this-work"></a>Wie funktioniert das?

Wenn der Clientcomputer eine Verbindung zu SharePoint Online von einer anderen Region herstellt, wird die Verbindung zum aktiven SharePoint Online-Datencenter umgeleitet. In diesem Szenario verwendet der Kunde ein Standardangebot, was dazu führt, dass die Portal Verbindungen noch lokal bleiben und die SharePoint Online-Verbindungen an das aktive Datencenter weitergeleitet werden.
  
1. Der Clientcomputer fordert die lokalen DNS-Server für die IP-Adresse an, die Office 365 zugeordnet ist.

2. Die lokalen DNS-Server des Clientcomputers Fragen die Microsoft-DNS-Server nach der IP-Adresse, die Office 365 zugeordnet ist.

3. Microsoft-DNS-Server geben den Servernamen des aktiven SharePoint Online-Datencenters (basierend auf dem Standort des Office 365-Mandanten des Clients) zurück, und der Clientcomputer wiederholt die Schritte 1 und 2, um die IP-Adresse des aktiven Office 365-Datencenters abzurufen.

4. Der Clientcomputer stellt eine Verbindung mit der IP-Adresse des aktiven Datencenters her.

![Aktives US-Rechenzentrum](media/c6d2933f-49cb-4536-bea7-c868707755ae.png)
  
## <a name="connecting-over-virtual-private-networks-vpns"></a>Verbinden über VPN (Virtual Private Networks)

Dieser Verbindungstyp gilt nur, wenn ein VPN (virtuelles privates Netzwerk) von Clientcomputern verwendet wird. In Wirklichkeit ändert sich das Verhalten von Office 365 nicht nur, weil ein VPN verwendet wird, aber VPNs werden häufig verwendet, um zu steuern, wie Clientcomputerverbindungen mit Office 365 herstellen und in der Regel zu einer Beeinträchtigung der Umgebung führen, daher ist es wichtig, diese zu behandeln.
  
## <a name="how-does-this-work"></a>Wie funktioniert das?

Wenn der Clientcomputer eine VPN-Verbindung mit einer unternehmensniederlassung in einer anderen Region herstellt, werden die DNS-Server in diesem Office anstelle der DNS-Server am Standort des Clientcomputers verwendet. In den meisten Fällen verschlechtert diese zusätzliche Verbindung über das VPN die Office 365-Umgebung. Die Office 365-Dienste sind optimiert, um Kundenverbindungen möglichst in der Endbenutzerumgebung zu bedienen. Viele Dienste nutzen das Azure Edge-Netzwerk, Content-Zustellungs Netzwerke und die zuverlässige Netzwerkkapazität des Microsoft-Netzwerks, um die bestmögliche Benutzerfreundlichkeit zu erreichen, wenn Netzwerkanforderungen für Office 365-Dienste in der Nähe des Clientcomputers ausgeführt werden. wie möglich.
  
1. Der Clientcomputer fordert die VPN-DNS-Server für die IP-Adresse an, die Office 365 zugeordnet ist.

2. Die VPN-DNS-Server des Clientcomputers Fragen die Microsoft-DNS-Server nach der IP-Adresse, die Office 365 zugeordnet ist.

3. Microsoft-DNS-Server geben den Namen des regionalen Servers zurück (basierend auf dem Speicherort der VPN-DNS-Server), und der Clientcomputer wiederholt die Schritte 1 und 2, um die IP-Adressinformationen des regionalen Office 365-Datencenters abzurufen.

4. Der Clientcomputer stellt eine Verbindung mit der IP-Adresse des Rechenzentrums her, die der unternehmensniederlassung am nächsten ist, mit der Sie eine VPN-Verbindung hergestellt haben.

![VPN-Datencenter-Konnektivität](media/b5f4c06c-65a3-462d-aae8-9a4602dd8d9e.png)
  
Mit diesem kurzen Link gelangen Sie wieder hierher zurück: [https://aka.ms/o365clientconnectivity](https://aka.ms/o365clientconnectivity)
  
## <a name="see-also"></a>Siehe auch

[Verwalten von Office 365-Endpunkten](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[Netzwerkkonnektivität mit Office 365](network-connectivity.md)
