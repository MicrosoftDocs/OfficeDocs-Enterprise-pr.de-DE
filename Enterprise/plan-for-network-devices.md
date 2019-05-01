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
description: 'Zusammenfassung: Beschreibung der Überlegungen für Netzwerkkapazität, WAN-Beschleuniger und Lastenausgleichsgeräte, die zum Herstellen einer Verbindung mit Office 365 verwendet werden.'
ms.openlocfilehash: 023eb3f5ed4d81d1d49d18c69ef8c81032fd5851
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/30/2019
ms.locfileid: "33492068"
---
# <a name="plan-for-network-devices-that-connect-to-office-365-services"></a>Planen von Netzwerkgeräten, die eine Verbindung zu Office 365-Diensten herstellen

 **Zusammenfassung**: Beschreibung der Überlegungen für Netzwerkkapazität, WAN-Beschleuniger und Lastenausgleichsgeräte, die zum Herstellen einer Verbindung mit Office 365 verwendet werden.
  
Einige Netzwerkhardware haben möglicherweise Einschränkungen hinsichtlich der Anzahl gleichzeitiger Sitzungen, die unterstützt werden. Für Organisationen mit mehr als 2.000 Benutzern empfiehlt es sich, ihre Netzwerkgeräte zu überwachen, um sicherzustellen, dass Sie den zusätzlichen Office 365-Dienst Datenverkehr verarbeiten können. Die SNMP-Überwachungssoftware (Simple Network Management Protocol) kann Ihnen dabei helfen.

||
|:-----|
| Dieser Artikel ist Teil der [Netzwerkplanung und Leistungsoptimierung für Office 365](https://aka.ms/tune).|

Lokale ausgehende Internet Proxyeinstellungen wirken sich auch auf die Konnektivität mit Office 365-Diensten für Ihre Clientanwendungen aus. Außerdem müssen Sie die Netzwerkproxy Geräte so konfigurieren, dass Verbindungen für Microsoft Cloud Services-URLs und-Anwendungen zugelassen werden. Jede Organisation ist unterschiedlich. Wenn Sie eine Vorstellung davon erhalten möchten, wie Microsoft diesen Prozess und die von uns bereitgestellten Bandbreite verwaltet, [Lesen Sie die Fallstudie](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365).
  
In den folgenden Skype for Business-Hilfeartikeln finden Sie weitere Informationen zu Skype for Business-Einstellungen:
  
- [Problembehandlung bei Skype for Business Online-Anmeldefehlern für Administratoren](https://docs.microsoft.com/skypeforbusiness/set-up-skype-for-business-online/troubleshooting-sign-in-errors-for-admins)

- [Sie können keine Verbindung zu Skype for Business herstellen, oder bestimmte Features funktionieren nicht, da eine lokale Firewall die Verbindung blockiert.](https://go.microsoft.com/fwlink/p/?LinkID=243625)

> [!NOTE]
> Während viele dieser Einstellungen Skype for Business-spezifisch sind, sind die allgemeinen Anweisungen zur Netzwerkkonfiguration für alle Office 365-Dienste hilfreich.
  
## <a name="determining-network-capacity"></a>Bestimmen der Netzwerkkapazität

Jedes Netzwerkgerät, das auf einer Verbindung vorhanden ist, hat seine Kapazitätsgrenze. Zu diesen Geräten gehört der Client-und Server Netzwerkadapter, Router, Switches und Hubs, die diese miteinander verbinden. Eine ausreichende Netzwerkkapazität führt dazu, dass keines der Benutzer gesättigt ist. Die Überwachung der Netzwerkaktivität ist wichtig, um sicherzustellen, dass die tatsächlichen Lasten auf allen Netzwerkgeräten kleiner als die maximale Kapazität sind. Die Netzwerkkapazität wirkt sich auf die Leistung des Proxy Geräts aus.
  
In den meisten Fällen wird durch die Bandbreite der Internet Verbindung die Grenze für den Datenverkehr festgelegt. Die schwache Leistung während der Hauptverkehrszeiten wird wahrscheinlich durch eine übermäßige Nutzung der Internet Verbindung verursacht. Diese Situation gilt auch für ein Zweigstellenszenario, bei dem die Computer der Zweigstelle Proxy Server über eine langsame WAN-Verbindung mit dem Proxygerät in der Zweigniederlassung verbunden sind.
  
Um die Netzwerkkapazität zu testen, überwachen Sie die Netzwerkaktivität auf der Proxy Netzwerkschnittstelle. Wenn es mehr als 75 Prozent der maximalen Bandbreite einer Netzwerkschnittstelle ist, sollten Sie die Bandbreite der unzureichenden Netzwerkinfrastruktur erhöhen. Sie sollten auch erweiterte Funktionen wie HTTP-Komprimierung verwenden.
  
## <a name="wan-accelerators"></a>WAN-Beschleuniger

Wenn Ihre Organisation WAN-Beschleunigungs Proxy-Appliances verwendet, können Probleme auftreten, wenn Sie auf die Office 365-Dienste zugreifen. Möglicherweise müssen Sie Ihr Netzwerkgerät oder Ihre Geräte optimieren, um sicherzustellen, dass Ihre Benutzer beim Zugriff auf Office 365 über eine konsistente Umgebung verfügen. Office 365-Dienste verschlüsseln beispielsweise einige Office 365-Inhalte und den TCP-Header. Möglicherweise ist Ihr Gerät nicht in der Lage, diese Art von Datenverkehr zu verarbeiten.
  
Lesen Sie unsere Support-Erklärung zur [Verwendung der WAN-Optimierung Controller oder Traffic/Inspection-Geräte mit Office 365](https://support.microsoft.com/kb/2690045).
  
## <a name="hardware-and-software-load-balancing-devices"></a>Hardware- und softwarebasierter Lastenausgleich

Ihre Organisation muss einen Hardwarelastenausgleich oder eine NLB-Lösung (Network Lastenausgleich) verwenden, um Anforderungen an Ihre Active Directory-Verbunddienste-Server (AD FS) und/oder an Ihre Exchange-hybridserver zu verteilen. Lastenausgleichsgeräte steuern den Netzwerkdatenverkehr zu den lokalen Servern. Diese Server sind entscheidend, um die Verfügbarkeit von einmaligem Anmelden und Exchange-hybridbereitstellung sicherzustellen.
  
Wir stellen eine softwarebasierte NLB-Lösung bereit, die in Windows Server integriert ist. Diese Lösung wird von Office 365 zur Implementierung des Lastenausgleichs unterstützt.
  
## <a name="firewalls-and-proxies"></a>Firewalls und Proxys

Weitere Informationen zum Konfigurieren von Firewalls und Proxys für die Verbindung mit Office 365 finden Sie unter [Managing Office 365 Endpoint](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a), [Network connectivity to Office 365](network-connectivity.md)und [Office 365 Endpoints FAQ](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d) , um mehr über die Geräte und die Leitungsauswahl zu erfahren.
  
## <a name="see-also"></a>Siehe auch

[Bereitstellungsratgeber für Office 365-Dienste](deployment-advisors-for-office-365.md)
