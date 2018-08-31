---
title: Client-Konnektivität
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 7/6/2017
ms.audience: ITPro
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
description: 'Zusammenfassung: Erläutert, wie Clientcomputer je nach Standort des Clientcomputers und des Office 365-Mandantenrechenzentrums eine Verbindung zu Office 365-Mandaten herstellen.'
ms.openlocfilehash: 9455147e70a391619e1602f2e36d9162ff2c0928
ms.sourcegitcommit: ad5bdc53ca67ee6a663c27648511c1ad768a76d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/28/2018
ms.locfileid: "23223037"
---
# <a name="client-connectivity"></a>Client-Konnektivität

 **Zusammenfassung:** Erläutert, wie Clientcomputer je nach Standort des Clientcomputers und des Office 365-Mandantenrechenzentrums eine Verbindung zu Office 365-Mandaten herstellen.
  
Office 365 befindet sich in Microsoft-Rechenzentren auf der ganzen Welt, das hilfreich, halten Sie den Dienst einrichten und betreiben, auch wenn es in einer Region, wie ein Erdbeben oder eines Stromausfalls ein ernstes Problem auftritt ist. Beim Herstellen der Verbindung zu Ihrem Office 365-Mandanten werden die Clientverbindung in die entsprechenden Rechenzentrum geleitet, wo Ihre Mandanten gehostet wird. Die Regeln, die bestimmen, wo Ihre Mandanten gehostet werden können, werden von Ihrer Vereinbarung mit Microsoft definiert. Die Regeln, die bestimmen, wie der Client die Daten aus diesem Speicherort Datacenter erwirbt hängen die Architektur des Diensts, den Sie verwenden.
  
Wenn Sie Office 365-Portal anmelden, sind Sie beispielsweise normalerweise mit dem nächsten Rechenzentrum an den Client verbunden und dann je nach dem Dienst weitergeleitet, mit denen Sie weiter. Wenn Sie e-Mail starten, die erste Verbindung zum Anzeigen der Benutzeroberfläche kann weiterhin stammen aus der nächsten Rechenzentrum, aber möglicherweise eine zweite Verbindung zwischen den nächsten Rechenzentrum und dem Rechenzentrum, wo sich Ihrem Mandanten befindet, um anzuzeigen, dass Sie, was in der e-Mails Sie lesen, geöffnet werden. Microsoft arbeitet mit einem der oberen zehn Netzwerke in der ganzen Welt resultierendes in fast unglaublich schnell Datacenter-an-Datacenter-Verbindungen.
  
Nachdem Sie den Artikel gelesen haben, Sie wahrscheinlich kennen Warum bieten wir [Office 365-URLs und IP-Adressbereiche](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2) nicht pro Rechenzentrum, sie sind einfach zu miteinander verknüpft und miteinander zu stellen, die Sie machbare abhängig.
  
Wenn Sie Azure ExpressRoute für Office 365 verwenden, in den meisten Fällen die Verbindung über eine private Verbindung zu Office 365 statt der hier beschriebenen öffentliche Verbindung gelangen. Die Prinzipien zur wie Clients eine Verbindung herstellen sind korrekt. Weitere Informationen zu [Azure ExpressRoute für Office 365](azure-expressroute.md).
  
Lesen Sie für weitere Tiefe auf Skype für Business Netzwerk Anforderungen Artikel [Medienqualität und Leistung des Netzwerks Connectivity in Skype für Business Online](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917).

||
|:-----|
| Dieser Artikel ist Teil der [Planung von Netzwerk und zur leistungsoptimierung für Office 365](https://aka.ms/tune).|

> [!NOTE]
> Wir müssen Sie Kundendaten also sichere und private in unseren Rechenzentren verwalten. Einzelheiten über die Schritte, die zum Verwalten von Privacy nehmen wir sind im [Trust Center](https://go.microsoft.com/fwlink/?LinkID=397383)enthalten.
  
## <a name="connecting-to-the-nearest-datacenter"></a>Herstellen einer Verbindung mit dem nächsten Rechenzentrum

Dies ist die am häufigsten verwendeten Typ der Verbindung, und es wird von den Office 365-Portal und Exchange Online verwendet. In dieser Situation Wenn Clients versuchen, eine Verbindung zu Office 365 herzustellen, DNS-Abfrage des Computers bestimmt die Region der Welt, die, der Ihren Computer stammt, und Office 365 leitet die Anforderung an den nächsten Rechenzentrum.
  
Verbindungen zum Portal bei der nächsten Rechenzentrum beendet, und der Clientcomputer erhält Informationen zu dem Mandanten des Clients von diesem Standort.
  
Exchange Online geht einen Schritt weiter. Nach der Clientcomputer mit der nächsten Rechenzentrum verbunden ist, ein Exchange-Server in Datencenter stellt eine Verbindung mit dem Rechenzentrum der Mandanten tatsächlich gespeichert, wie in dargestellt ist die *wie funktioniert dies funktioniert im Abschnitt* unten. Exchange Online-Server in der nächsten Rechenzentrum und den Proxy der Anforderungen vom Clientcomputer an den Postfachserver. Dies beschleunigt die Erfahrung für den Clientcomputer durch Verschieben den schwierigsten zum Abrufen von e-Mail-Nachrichten und Kalenderelemente mit dem Microsoft-Netzwerk ein.
  
## <a name="how-does-this-work-for-standard-cloud-offerings"></a>Wie funktioniert dies für standard-Cloud-angeboten?

Dieser Verbindungsprozess ist standard für starken Datenverkehr hochwertiger Webanwendungen wie Office 365. In diesem Abschnitt werden die notwendigen und auch die Schritte im Prozess. Wenn der Client-Computer nicht im selben Bereich als den Mandanten ist, sieht die Verbindung viel anders je nach den Dienst, den, dem der Client eine Verbindung herstellt.
  
 Dieses Diagramm zeigt einen Kunden in Nordamerika einen Mandanten ein standard Office 365-Angebot mit. In diesem Szenario die anfordernden Person hat in Europa getunnelt und Office 365 aus diesem Speicherort verwendet.
  
1. Der Clientcomputer fordert die lokalen DNS-Server für die Office 365 zugeordnete IP-Adresse.

2. Lokalen DNS-Server des Clientcomputers bitten Sie die Microsoft-DNS-Servern für die Office 365 zugeordnete IP-Adresse.

3. Microsoft DNS-Server zurückgeben der regionalen Servername (basierend auf den Speicherort der Client-DNS-Server) und der Clientcomputer wiederholen Sie die Schritte 1 und 2, um die IP-Adresse des regionalen Rechenzentrums Office 365 zu erhalten.

4. Der Clientcomputer stellt eine Verbindung zu der IP-Adresse des regionalen Rechenzentrums her.

5. Exchange Online-Servern herstellen eine Verbindung mit dem aktiven Rechenzentrum her, auf dem der Mandant des Kunden befindet.

![Nächstes regionales Rechenzentrum](media/4ea108e9-a299-4e3d-b0d3-469b434ff899.png)
  
## <a name="how-does-this-work-for-sovereign-cloud-offerings"></a>Cloud diese Arbeit für souveräne wie angeboten?

Diese Verbindung ist für unabhängigen Cloud-Angeboten wie etwa Office 365 vom Dienst 21 Vianet etwas unterschiedlich. Mit dem in einer unabhängigen Instanz von Office 365-Mandanten sind die nächsten Office 365-Servern, die Portal-Verbindungen akzeptieren die Server innerhalb der unabhängigen Region, in dem der Mandant befindet. In ähnlicher Weise werden Kunden, die Zugriff auf SharePoint Online in unseren unabhängigen Cloud oder standard Dienstangebote auf Front-End-Server weitergeleitet, in dem der Mandant befindet. Finden Sie unter Herstellen einer Verbindung mit dem aktiven Rechenzentrum unten.
  
1. Der Clientcomputer fordert die lokalen DNS-Server für die Office 365 zugeordnete IP-Adresse.

2. Lokalen DNS-Server des Clientcomputers bitten Sie die Microsoft-DNS-Servern für die Office 365 zugeordnete IP-Adresse.

3. Microsoft DNS-Server zurückgeben der regionalen Servername (basierend auf den Speicherort der Client-DNS-Server) und der Clientcomputer wiederholen Sie die Schritte 1 und 2, um die IP-Adresse des regionalen Rechenzentrums Office 365 zu erhalten.

4. Der Clientcomputer stellt eine Verbindung zu der IP-Adresse des regionalen Rechenzentrums her.

5. Exchange Online-Servern herstellen eine Verbindung mit dem aktiven Rechenzentrum her, auf dem der Mandant des Kunden befindet.

![Nächstes regionales US-Rechenzentrum](media/c0628c54-0059-48c5-8a0f-41bf392ee182.png)
  
## <a name="connecting-to-the-active-datacenter"></a>Herstellen einer Verbindung mit dem aktiven Rechenzentrum

Herstellen einer Verbindung mit dem aktiven Rechenzentrum ist für das schwerer Daten übertragen Arbeitslasten und wird derzeit von SharePoint Online verwendet. Wenn Clients die Verbindung zu Office 365, versuchen, wird ihrem Browser in dieser Situation auf dem aktiven Rechenzentrum für ihre SharePoint Online-Mandanten umgeleitet.
  
## <a name="how-does-this-work"></a>Wie funktioniert das?

Wenn der Client-Computer mit SharePoint Online von einer anderen Region herstellt, wird die Verbindung in das aktive SharePoint Online-Rechenzentrum umgeleitet. In diesem Szenario wird der Kunde einen Standard anbietet, was die verbleibenden lokalen Portal Verbindungen und die SharePoint Online Verbindungen weitergeleitet werden dem aktiven Rechenzentrum verwendet.
  
1. Der Clientcomputer fordert die lokalen DNS-Server für die Office 365 zugeordnete IP-Adresse.

2. Lokalen DNS-Server des Clientcomputers bitten Sie die Microsoft-DNS-Servern für die Office 365 zugeordnete IP-Adresse.

3. Microsoft DNS-Server zurückgeben des Servernamens das aktive SharePoint Online-Rechenzentrum (basierend auf den Speicherort der Office 365-Mandanten des Clients), und der Clientcomputer wiederholen Sie die Schritte 1 und 2, um die IP-Adresse des aktiven Office 365 Datencenters abzurufen.

4. Der Clientcomputer stellt eine Verbindung zu der IP-Adresse des aktiven Rechenzentrums her.

![Aktives US-Rechenzentrum](media/c6d2933f-49cb-4536-bea7-c868707755ae.png)
  
## <a name="connecting-over-virtual-private-networks-vpns"></a>Herstellen einer Verbindung über virtuelle private Netzwerke (VPNs)

Diese Art von Verbindung gilt nur, wenn ein virtuelles privates Netzwerk (VPN) von den Clientcomputern verwendet wird. In der Praxis Verhalten von Office 365 wird nicht geändert, einfach, da ein VPN verwendet wird, aber VPNs im Allgemeinen steuern zum werden, wie Clientcomputer Verbindungen zu Office 365 und in der Regel die Ergebnisse einer beeinträchtigter Oberfläche einrichten, sodass es ist wichtig, behandelt.
  
## <a name="how-does-this-work"></a>Wie funktioniert das?

Wenn der Clientcomputer eine VPN-Verbindung mit einer Unternehmenszentrale in einer anderen Region herstellt, werden die DNS-Server an, die von Office anstelle der DNS-Server am Standort des Clientcomputers verwendet. In den meisten Fällen wird diese zusätzliche Verbindung über VPN die Office 365-Erfahrung beeinträchtigt. Office 365-Dienste sind auf ungefähr in der Endbenutzer möglichst Kunden Verbindungen als optimiert. Viele Dienste nutzen die Azure edgenetzwerk, Content Delivery Networks und zuverlässige Netzwerkkapazität im Microsoft-Netzwerk zum Übermitteln von möglichen benutzerumgebung bei Netzwerk-Anforderungen für Office 365-Dienste wie ungefähr in der Client-Computer vorgenommen werden wie möglich.
  
1. Der Clientcomputer fordert den VPN-DNS Servern für die Office 365 zugeordnete IP-Adresse.

2. VPN-DNS-Server des Clientcomputers bitten Sie die Microsoft-DNS-Servern für die Office 365 zugeordnete IP-Adresse.

3. Microsoft DNS-Server zurückgeben der regionalen Servername (basierend auf den Speicherort der VPN-DNS-Server) und der Client-Computer wiederholen Sie die Schritte 1 und 2, um die IP-Adressinformationen des regionalen Rechenzentrums Office 365 zu erhalten.

4. Der Clientcomputer stellt eine Verbindung her in das Rechenzentrum IP-Adresse, die an der Niederlassung am nächsten ist, wenn sie eine VPN-Verbindung hergestellt.

![VPN-Datencenterkonnektivität](media/b5f4c06c-65a3-462d-aae8-9a4602dd8d9e.png)
  
Nachfolgend finden Sie ein kurzer Link, zurückkehren verwendet werden können:[https://aka.ms/o365clientconnectivity](https://aka.ms/o365clientconnectivity)
  
## <a name="see-also"></a>Siehe auch

[Verwalten von Office 365-Endpunkten](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[Netzwerkkonnektivität zu Office 365](network-connectivity.md)
