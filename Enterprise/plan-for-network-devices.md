---
title: Planen von Netzwerkgeräten, die eine Verbindung zu Office 365-Diensten herstellen
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/29/2016
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 073433ca-3511-4db9-b173-7a2edca57691
description: 'Zusammenfassung: Beschreibung von Überlegungen zu Netzwerkkapazität, WAN-Beschleunigern und Lastenausgleichsgeräten, die für die Herstellung einer Verbindung zu Office 365 verwendet werden.'
ms.openlocfilehash: 023eb3f5ed4d81d1d49d18c69ef8c81032fd5851
ms.sourcegitcommit: 317c2753be2aedb60698e94606ba59b63c962328
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/02/2018
ms.locfileid: "25933122"
---
# <a name="plan-for-network-devices-that-connect-to-office-365-services"></a>Planen von Netzwerkgeräten, die eine Verbindung zu Office 365-Diensten herstellen

 **Zusammenfassung**: Beschreibung von Überlegungen zu Netzwerkkapazität, WAN-Beschleunigern und Lastenausgleichsgeräten, die für die Herstellung einer Verbindung zu Office 365 verwendet werden.
  
Einige Netzwerkhardware möglicherweise Einschränkungen für die Anzahl der gleichzeitigen Sitzungen, die unterstützt werden. Für Organisationen mit mehr als 2.000 Benutzern wird empfohlen, dass sie Netzwerkgeräte überwachen, um sicherzustellen, dass diese den zusätzlichen Office 365-Dienst-Datenverkehr verarbeiten kann. SNMP Simple Network Management Protocol () Software für die Überwachung können Ihnen dabei helfen.

||
|:-----|
| Dieser Artikel ist Teil der [Planung von Netzwerk und zur leistungsoptimierung für Office 365](https://aka.ms/tune).|

In der lokalen ausgehende Internet-Proxyeinstellungen auch Konnektivität mit Office 365-Dienste für den-Clientanwendungen auswirken. Sie müssen auch der Proxy Netzwerkgeräte zum Zulassen von Verbindungen für Microsoft Cloud Services-URLs und Anwendungen konfigurieren. Jedes Unternehmen ist anders. Wenn Sie eine Vorstellung vom Zweck für wie Microsoft dieser Prozess und Bandbreite verwaltet erhalten möchten bereitstellen wir möchten, [Lesen Sie die Fallstudie](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365).
  
Die folgenden Skype für Artikel zu Business-Hilfe wurden weitere Informationen zu Skype für Unternehmen:
  
- [Problembehandlung bei Skype für Business Online Anmeldefehlern für Administratoren](https://docs.microsoft.com/skypeforbusiness/set-up-skype-for-business-online/troubleshooting-sign-in-errors-for-admins)

- [Sie können keine Verbindung mit Skype für Unternehmen oder bestimmte Features funktionieren nicht, da eine lokale Firewall die Verbindung blockiert](https://go.microsoft.com/fwlink/p/?LinkID=243625)

> [!NOTE]
> Obwohl viele dieser Einstellungen Skype für Business-spezifischen sind, ist die allgemeine Anleitung zur Netzwerkkonfiguration für alle Office 365-Dienste hilfreich.
  
## <a name="determining-network-capacity"></a>Ermitteln der Netzwerkkapazität

Jedes Netzwerkgerät, das in einer Verbindung vorhanden ist, hat eine Kapazitätsgrenze. Dies schließt die Client- und Servernetzwerkadapter, Router, Switches und Hubs ein, die sie verbinden. Ausreichende Netzwerkkapazität bedeutet, dass keines dieser Netzwerkgeräte vollständig ausgelastet ist. Die Überwachung der Netzwerkaktivität ist notwendig, um sicherzustellen, dass die tatsächlichen Lasten an allen Netzwerkgeräten unter der maximalen Kapazität liegen. Die Netzwerkkapazität wirkt sich auf die Leistung des Proxygeräts aus.
  
In den meisten Fällen wird die Verbindung Internetbandbreite die Obergrenze für den Datenverkehr. Schwache Leistung während der Spitzenzeiten Datenverkehr wird wahrscheinlich übermäßig viele mithilfe des Internetlinks verursacht. Dies gilt auch für eine Branch Office Szenario, in dem Branch Office Proxy-Server-Computern über eine langsame Netzwerk WAN (Wide Area) mit dem Proxygerät Unternehmenszentrale die Verzweigung verbunden sind.
  
Zum Testen der Netzwerkkapazität Überwachen der Netzwerk-Aktivitätsfeeds auf die Netzwerkschnittstelle Proxy. Wenn es sich mehr als 75 % der maximalen Bandbreite einer Netzwerkschnittstelle handelt, erhöhen Sie die Bandbreite der Netzwerkinfrastruktur, die dies nicht der Fall ist. Oder erweiterte Funktionen, wie etwa HTTP-Komprimierung in Betracht.
  
## <a name="wan-accelerators"></a>WAN-Beschleuniger

Wenn Ihre Organisation wide Area Network (WAN) Acceleration-Proxy-Einheiten verwendet, können Probleme auftreten, wenn Sie die Office 365-Dienste zugreifen. Möglicherweise müssen zur Optimierung Ihrer Netzwerkgeräte oder Geräte, um sicherzustellen, dass Ihre Benutzer beim Zugriff auf Office 365 eine einheitliche Erfahrung haben. Verschlüsseln beispielsweise Office 365-Diensten bestimmter Inhalte für Office 365 und TCP-Header. Das Gerät kann möglicherweise nicht dieser Art von Datenverkehr zu verarbeiten.
  
Lesen Sie unsere Support-Anweisung zum [Verwenden von WAN-Optimierung Controller oder/Überprüfung des Datenverkehrs Geräte mit Office 365](https://support.microsoft.com/kb/2690045).
  
## <a name="hardware-and-software-load-balancing-devices"></a>Hardware- und Softwaregeräte für den Lastenausgleich

Für Ihr Unternehmen empfiehlt sich die Verwendung eines Hardware-Lastenausgleichsmoduls (HLB) oder einer Netzwerk-Lastenausgleich-Lösung (NLB) um Anforderungen an die Server der Active Directory-Verbunddienste (AD FS) und/oder Ihres Hybridservers verteilen zu können. Geräte für den Lastenausgleich steuern den Netzwerkdatenverkehr zu den lokalen Servern. Diese Server sind für die Verfügbarkeit von einmaligen Anmeldungen sowie für die Exchange-Hybridbereitstellung unerlässlich.
  
Wir stellen eine softwarebasierte NLB-Lösung in Windows Server integriert. Office 365 unterstützt diese Lösung zum Lastenausgleich zu erzielen.
  
## <a name="firewalls-and-proxies"></a>Firewalls und Proxys

Weitere Informationen zum Konfigurieren von Firewalls und Proxys für die Verbindung zu Office 365, erfahren Sie mehr über die Geräte und Netzfrequenz Auswahl [Verwalten von Office 365-Endpunkten](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a), [Netzwerkkonnektivität zu Office 365](network-connectivity.md)und [häufig gestellte Fragen zu Office 365-Endpunkten](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d) lesen.
  
## <a name="see-also"></a>Siehe auch

[Bereitstellungsratgeber für Office 365-Dienste](deployment-advisors-for-office-365.md)
