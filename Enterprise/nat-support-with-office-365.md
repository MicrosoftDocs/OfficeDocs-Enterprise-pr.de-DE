---
title: NAT-Unterstützung in Office 365
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 1/24/2017
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- BCS160
ms.assetid: 170e96ea-d65d-4e51-acac-1de56abe39b9
description: 'Zusammenfassung: Hier erhalten Sie ausführliche Informationen dazu, wie Sie die richtige Anzahl Clients einschätzen, die Sie pro IP-Adresse mit der Netzwerkadressübersetzung (Network Address Translation, NAT) in Ihrem Unternehmen verwenden können.'
ms.openlocfilehash: 733d591bded599cfaece988a624baa7a3c0d4b06
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540704"
---
# <a name="nat-support-with-office-365"></a>NAT-Unterstützung in Office 365

 **Zusammenfassung:** Hier erhalten Sie ausführliche Informationen dazu, wie Sie die richtige Anzahl Clients einschätzen, die Sie pro IP-Adresse mit der Netzwerkadressübersetzung (Network Address Translation, NAT) in Ihrem Unternehmen verwenden können. 
  
Bisher vorgeschlagene Hinweise, dass die maximale Anzahl von Exchange-Clients, die Sie pro IP-Adresse verwenden sollten, Verbindung mit Office 365 etwa 2.000 Clients pro Netzwerkports war.
  
## <a name="why-use-nat"></a>Gründe für die Verwendung von NAT

Mithilfe von NAT können Tausende Benutzer in einem Unternehmensnetzwerk "wenige öffentlich routingfähige IP-Adressen gemeinsam nutzen".
  
Die meisten Unternehmensnetzwerke verwenden einen privaten (RFC1918) IP-Adressraum. Private Adressräume werden durch die IANA (Internet Assigned Numbers Authority) zugewiesen und sind ausschließlich für Netzwerke bestimmt, die nicht direkt vom und zum Internet routen.
  
Um Internetzugriff auf Geräte auf einem privaten IP-Adressraum zu ermöglichen, verwenden Sie Organisationen Gateway-Technologien wie Firewalls und Proxys, die Netzwerkadressübersetzung (NAT) oder Port Address Translation (PAT) Services bereitstellen. Diese Gateways stellen Datenverkehr von interne Geräte mit dem Internet (einschließlich Office 365) angezeigt werden, von einer oder mehreren öffentlich routingfähige IP-Adressen kommen. Jede ausgehende Verbindung von einem internen Gerät wird in einer anderen Quelle TCP-Port auf die öffentliche IP-Adresse übersetzt. 
  
## <a name="why-do-you-need-to-have-so-many-connections-open-to-office-365-at-the-same-time"></a>Warum müssen Sie so viele Verbindungen zu Office 365 gleichzeitig geöffnet haben?

Outlook kann acht oder mehr Verbindungen öffnen (in Situationen, in denen Add-Ins, freigegebene Kalender, Postfächer etc. vorhanden sind). Auf einem Windows-basierten NAT-Gerät sind höchstens 64.000 Ports verfügbar. Daher beträgt die Höchstzahl 8.000 Benutzer pro IP-Adresse. Bitte beachten Sie, dass die Anzahl der verfügbaren Ports bei Kunden, die kein Windows-basiertes Betriebssystem für NAT verwenden, abhängig von NAT-Gerät oder -Software ist. In einem solchen Szenario liegt die Höchstzahl der Ports ggf. unter 64.000. Die Verfügbarkeit der Ports ist außerdem abhängig von weiteren Faktoren: So beansprucht Windows 4.000 Ports für sich, wodurch die Anzahl der verfügbaren Ports auf 60.000 reduziert wird. Zudem besteht die Möglichkeit, dass weitere Anwendungen, die zur gleichen Zeit eine Verbindung aufbauen – z. B. Internet Explorer – ebenfalls Ports in Anspruch nehmen.
  
## <a name="calculating-maximum-supported-devices-behind-a-single-public-ip-address-with-office-365"></a>Berechnung der Höchstzahl an unterstützten Geräten für eine einzelne öffentliche IP-Adresse mit Office 365

Um die maximale Anzahl der Geräte hinter einer einzelnen öffentlichen IP-Adresse zu ermitteln, sollten Sie den Netzwerkverkehr zum Bestimmen der Spitzenlast Port-Auslastung pro Client überwachen. Darüber hinaus sollte Spitzenlast-Faktor beträgt die Verwendung von Port (mindestens 4) verwendet werden. 
  
 **Anhand der folgenden Formel berechnet die Anzahl der unterstützten Geräte pro IP-Adresse:**
  
Höchstanzahl unterstützter Geräte hinter einer einzelnen öffentlichen IP-Adresse = (64.000 – eingeschränkte Ports) / (Spitzenlast Port-Nutzung + Spitzenlast-Faktor)
  
 **Wenn beispielsweise die folgenden true haben:**
  
- **Eingeschränkte Ports:** 4.000 für das Betriebssystem 
    
- **Spitzenlast Port-Nutzung:** 6 pro Gerät 
    
- **Spitzenfaktor:** 4 
    
Klicken Sie dann die Höchstzahl an unterstützten Geräten für eine einzelne öffentliche IP-Adresse = (64.000-4.000) / (6 + 4) = 6.000
  
Mit der Veröffentlichung von Office 365-hosting enthalten in den Updates von September 2011 für Microsoft Office Outlook 2007 oder vom November 2011 für Microsoft Outlook 2010 oder einem neueren Update, die Anzahl der Verbindungen von Outlook (sowohl Office Outlook 2007 mit Service pack 2 und Outlook 2010-Paket) zu Exchange kann so wenige als 2 sein. Sie müssen Faktor in den verschiedenen Betriebssystemen Benutzerverhaltensweisen, und so weiter, um die minimale und maximale Anzahl von Ports zu ermitteln, die Ihr Netzwerk bei Spitzenbelastungen erforderlich ist.
  
Wenn Sie mehrere Geräte hinter einer einzelnen öffentlichen IP-Adresse unterstützen möchten, führen Sie die folgenden Schritte durch, um die maximale Anzahl von Geräten bewerten, die unterstützt werden können:
  
Überwachen des Netzwerkverkehrs Spitzenlast Port-Auslastung pro Client bestimmen. Sie sollten diese Daten zu erfassen:
  
- Von mehreren geografischen Orten aus
    
- Für mehrere Geräte
    
- Zu mehreren Zeitpunkten
    
Verwenden Sie die oben angegebene Formel, um die Höchstzahl der Nutzer pro IP-Adresse in deren jeweiligen Umgebung zu errechnen.
  
Es gibt verschiedene Methoden zum Verteilen der Clientlast auf Weitere öffentliche IP-Adressen. Strategien zur Verfügung, abhängig von der Funktionen des Unternehmens-Gateway-Lösung. Die einfachste Lösung ist Ihre Benutzeradressraum segmentieren und "zuweisen" statisch eine Anzahl von IP-Adressen an jedes Gateway. Eine andere Möglichkeit, die viele Gateway-Geräte bieten ist die Möglichkeit, einen Pool von IP-Adressen verwenden. Die Vorteile der Adresspool ist, es ist sehr viel dynamischen und mit weitaus geringerer Wahrscheinlichkeit Anpassung erforderlich ist, wenn Ihre Benutzerbasis wächst.
  
## <a name="see-also"></a>Siehe auch

[Verwalten von Office 365-Endpunkten](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[Häufig gestellte Fragen zu Office 365-Endpunkten](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)

