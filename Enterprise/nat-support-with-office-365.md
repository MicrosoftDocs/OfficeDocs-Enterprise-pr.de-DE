---
title: NAT-Unterstützung mit Office 365
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 1/24/2017
audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- BCS160
ms.assetid: 170e96ea-d65d-4e51-acac-1de56abe39b9
description: 'Zusammenfassung: enthält Informationen dazu, wie Sie die korrekte Anzahl von Clients, die Sie pro IP-Adresse in Ihrer Organisation verwenden können, mithilfe von Netzwerkadressübersetzung (Network Address Translation, NAT) annähern.'
ms.openlocfilehash: bdbf108163c7b22fd6d7583436af5f0ed655784c
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "34069881"
---
# <a name="nat-support-with-office-365"></a>NAT-Unterstützung mit Office 365

 **Zusammenfassung:** Enthält ausführliche Informationen dazu, wie Sie die richtige Anzahl von Clients, die Sie pro IP-Adresse in Ihrer Organisation verwenden können, mithilfe von Netzwerkadressübersetzung (Network Address Translation, NAT) annähern. 
  
Bisher wurde empfohlen, dass die maximale Anzahl von Exchange-Clients, die Sie pro IP-Adresse zum Herstellen einer Verbindung mit Office 365 verwenden sollten, ungefähr 2.000 Clients pro Netzwerkport war.
  
## <a name="why-use-nat"></a>Gründe für die Verwendung von NAT

Durch die Verwendung von NAT können Tausende von Personen in einem Unternehmensnetzwerk einige öffentlich routingfähige IP-Adressen freigeben.
  
Die meisten Unternehmensnetzwerke verwenden einen privaten (RFC1918) IP-Adressraum. Privater Adressraum wird von der Internet Assigned Numbers Authority (IANA) zugewiesen und soll ausschließlich für Netzwerke bestimmt werden, die nicht direkt an das und aus dem globalen Internet weitergeleitet werden.
  
Um Internet Zugriff auf Geräte in einem privaten IP-Adressraum bereitzustellen, verwenden Organisationen Gateway-Technologien wie Firewalls und Proxys, die die Netzwerkadressübersetzung (NAT) oder Pat-Dienste (Port Address Translation) bereitstellen. Diese Gateways stellen den Datenverkehr von internen Geräten zum Internet (einschließlich Office 365) scheinbar aus einer oder mehreren öffentlich routingfähigen IP-Adressen her. Jede ausgehende Verbindung von einem internen Gerät wird in einen anderen TCP-Quellanschluss der öffentlichen IP-Adresse übersetzt. 
  
## <a name="why-do-you-need-to-have-so-many-connections-open-to-office-365-at-the-same-time"></a>Warum müssen Sie so viele Verbindungen zu Office 365 gleichzeitig öffnen?

Outlook kann acht oder mehr Verbindungen öffnen (in Situationen, in denen Add-Ins, freigegebene Kalender, Postfächer usw. vorhanden sind). Da für ein Windows-basiertes NAT-Gerät maximal 64.000 Ports verfügbar sind, können maximal 8.000 Benutzer hinter einer IP-Adresse liegen, bevor die Ports erschöpft sind. Beachten Sie, dass die insgesamt verfügbaren Ports davon abhängen, welche NAT-Geräte oder-Software verwendet werden, wenn Kunden nicht-Windows-Betriebssystembasierte Geräte für NAT verwenden. In diesem Szenario kann die maximale Anzahl von Ports kleiner als 64.000 sein. Die Verfügbarkeit von Ports wird auch von anderen Faktoren beeinflusst, wie beispielsweise der Windows-Beschränkung von 4.000-Ports für die eigene Verwendung, wodurch die Gesamtzahl der verfügbaren Ports auf 60.000 reduziert wird. möglicherweise gibt es andere Anwendungen wie Internet Explorer, die gleichzeitig eine Verbindung herstellen können. , die zusätzliche Ports erfordern.
  
## <a name="calculating-maximum-supported-devices-behind-a-single-public-ip-address-with-office-365"></a>Berechnen der maximal unterstützten Geräte hinter einer einzelnen öffentlichen IP-Adresse mit Office 365

Wenn Sie die maximale Anzahl von Geräten hinter einer einzelnen öffentlichen IP-Adresse ermitteln möchten, sollten Sie den Netzwerkdatenverkehr überwachen, um den maximalen Port Verbrauch pro Client zu bestimmen. Außerdem sollte ein Peak-Faktor für die Verwendung der Portierung verwendet werden (mindestens 4). 
  
 **Verwenden Sie die folgende Formel, um die Anzahl unterstützter Geräte pro IP-Adresse zu berechnen:**
  
Maximal unterstützte Geräte hinter einer einzelnen öffentlichen IP-Adresse = (64.000-restricted Ports)/(Peak Port Verbrauch + Spitzen Faktor)
  
 **Wenn beispielsweise Folgendes zutrifft:**
  
- **Eingeschränkte Ports:** 4.000 für das Betriebssystem 
    
- **Maximaler Stromverbrauch:** 6 pro Gerät 
    
- **Höchstwert:** 4 
    
Dann werden die maximal unterstützten Geräte hinter einer einzelnen öffentlichen IP-Adresse = (64.000-4000)/(6 + 4) = 6.000
  
Mit der Version von Office 365 Hosting Pack, die in den Updates vom September 2011 für Microsoft Office Outlook 2007 oder November 2011 für Microsoft Outlook 2010 oder einem späteren Update enthalten ist, ist die Anzahl der Verbindungen von Outlook (sowohl Office Outlook 2007 mit Dienst Pack 2 und Outlook 2010) an Exchange kann nur 2 sein. Sie müssen die unterschiedlichen Betriebssysteme, Benutzerverhalten usw. berücksichtigen, um die Mindest-und Höchstzahl der Ports zu ermitteln, die Ihr Netzwerk am höchsten ist.
  
Wenn Sie mehr Geräte hinter einer einzelnen öffentlichen IP-Adresse unterstützen möchten, führen Sie die folgenden Schritte aus, um die maximale Anzahl von Geräten zu bewerten, die unterstützt werden können:
  
Überwachen des Netzwerkdatenverkehrs zur Bestimmung des Spitzen Port Verbrauchs pro Client Sie sollten diese Daten erfassen:
  
- Von mehreren Standorten
    
- Von mehreren Geräten
    
- Mehrmals
    
Verwenden Sie die vorhergehende Formel, um die maximalen Benutzer pro IP-Adresse zu berechnen, die in Ihrer Umgebung unterstützt werden können.
  
Es gibt verschiedene Methoden zum Verteilen der Clientauslastung über zusätzliche öffentliche IP-Adressen. Verfügbare Strategien hängen von den Funktionen der Unternehmens Gateway-Lösung ab. Die einfachste Lösung besteht darin, ihren Benutzeradressraum zu segmentieren und jedem Gateway statisch eine Reihe von IP-Adressen zuzuweisen. Eine weitere Alternative, die viele Gateway-Geräte bieten, ist die Möglichkeit, einen Pool von IP-Adressen zu verwenden. Der Vorteil des Adresspools besteht darin, dass er viel dynamischer ist und weniger wahrscheinlich ist, dass eine Anpassung erforderlich ist, wenn die Benutzerbasis wächst.
  
## <a name="see-also"></a>Siehe auch

[Verwalten von Office 365-Endpunkten](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[Häufig gestellte Fragen zu Office 365-Endpunkten](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)

