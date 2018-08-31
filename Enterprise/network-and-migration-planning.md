---
title: Netzwerk- und Migrationsplanung für Office 365
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 6/29/2018
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Adm_O365
search.appverid:
- MET150
- BCS160
ms.assetid: f5ee6c33-bcd7-4b0b-b0f8-dc1d9fb8d132
description: Enthält Links zu Informationen über das Netzwerk planen und testen und Migration zu Office 365.
ms.openlocfilehash: e2434a65b48c12f38d7371a569ba8e0bc282ae06
ms.sourcegitcommit: ad5bdc53ca67ee6a663c27648511c1ad768a76d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/28/2018
ms.locfileid: "23223057"
---
# <a name="network-and-migration-planning-for-office-365"></a>Netzwerk- und Migrationsplanung für Office 365

Dieser Artikel enthält Links zu Informationen über das Netzwerk planen und testen und Migration zu Office 365.
  
Bevor Sie Office 365 zum ersten Mal bereitstellen oder zu Office 365 migrieren, können Sie anhand der Informationen in diesen Themen die benötigte Bandbreite einschätzen und dann testen bzw. prüfen, ob Sie über ausreichend Bandbreite für die Bereitstellung von oder Migration zu Office 365 verfügen.

||
|:-----|
| Dieser Artikel ist Teil der [Planung von Netzwerk und zur leistungsoptimierung für Office 365](https://aka.ms/tune).|

|||
|:-----|:-----|
|![Finden Sie unter Microsoft Cloud Netzwerk konstruiert Enterprise-Poster](media/3094be9f-2407-4fa5-896d-aa66ef7b9bb9.png)|Die Schritte zur Optimierung Ihres Netzwerks für Office 365 und anderen Microsoft-Cloud-Plattformen und Dienste finden Sie unter Details des Posters [Microsoft Cloud Networking für Enterprise-konstruiert](https://aka.ms/cloudarchnetworking) . |
   
## <a name="estimate-network-bandwidth-requirements"></a>Schätzen der Anforderungen an die Netzwerkbandbreite
<a name="EstimateBandwidthRequirements"> </a>

Verwendung von Office 365, kann die Nutzung in Ihrer Organisation Internet Netzfrequenz erhöhen. Es ist wichtig, um festzustellen, ob die aktuell verfügbare Bandbreite genügt, um die geschätzte Erhöhung behandeln nach Office 365 vollständig bereitgestellt wird, während Sie verlassen mindestens 20 % Kapazität zum Verarbeiten von der höchsten Auslastung von Tagen.
  
Um die Bandbreite zu schätzen, verwenden Sie die folgenden Schritte aus:
  
1. Bewerten Sie die Anzahl von Clients, die jeder Ausgang Internet verwendet wird. Können Sie unser Multi-TBit Netzwerk möglichst die Verbindung wie möglich verarbeiten. 
    
2. Bestimmen Sie, welche Office 365-Dienste und Features für die Verwendung von Clients zur Verfügung stehen. Sie müssen wahrscheinlich Personengruppen mit anderen Diensten oder Verwendungsprofile.
    
3. Messen Sie die Netzwerkverwendung für eine Pilotgruppe von Clients. Stellen Sie sicher, dass die pilot-Clients für die verschiedenen Profile von Personen in der Organisation als auch verschiedene geografische Standorte repräsentativ sind. Sie können Cross-Kontrollkästchen Ihre Ergebnisse für unsere alten Rechner für [Exchange ](https://go.microsoft.com/fwlink/p/?LinkId=321550)und [Skype für Unternehmen](https://go.microsoft.com/fwlink/p/?LinkId=321551) oder der [Fallstudie](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365) , die wir in unseren eigenen Netzwerk ausgeführt. 
    
4. Verwenden Sie die Maße von der Pilotgruppe, um die gesamte Organisation Anforderungen Schlussfolgerungen ziehen, und Testen Sie erneut um Einschätzung vor dem Durchführen von Änderungen an Ihrem Netzwerk überprüfen.
    
## <a name="test-your-existing-network"></a>Testen des vorhandenen Netzwerks
<a name="calculators"> </a>

 **Netzwerk-Tools.** Testen Sie und überprüfen Sie die Internetbandbreite zum Download, hochladen und Wartezeit Integritätsregeln bestimmen. Diese Tools helfen Ihnen beim bestimmen die Funktionen des Netzwerks für die Migration sowie Sie vollständig bereitgestellt werden. 
  
- [Microsoft Message Analyzer](https://technet.microsoft.com/library/jj649776.aspx): Nachricht Analyzer ist ein effizientes Tool für die Problembehandlung bei Netzwerkprobleme. Nachricht Analyzer erfasst, anzeigt und analysiert IP-basierten messaging-Datenverkehr und Systemnachrichten. Nachricht Analyzer können Sie auch importieren, aggregieren und Analysieren von Daten aus Protokoll- und Ablaufverfolgungsprotokoll-Dateien.
    
- [Microsoft Remote Connectivity Analyzer](https://go.microsoft.com/fwlink/p/?LinkId=517243): testet die Konnektivität in Ihrer Exchange Online-Umgebung.
    
- Verwenden Sie die [Microsoft-Support und Recovery-Assistenten für Office 365](https://diagnostics.office.com/#/Download?env=SOC) , um Outlook und Office 365 Probleme zu beheben. 
    
## <a name="best-practices-for-network-planning-and-improving-migration-performance-for-office-365"></a>Best practices for network planning and improving migration performance for Office 365
<a name="BestPractices"> </a>

Architekturprinzipien Sie etwas genauer diesen bewährten Methoden für Weitere Informationen zum Verbessern der Ihre Office 365-Erfahrung.
  
1. Helfen Ihren Benutzern sofort beginnen möchten? Tipps zur Verwendung von Office 365, einschließlich SharePoint Online, Exchange Online und Lync Online, wenn Ihr Netzwerk ist nicht einfach zusammenarbeiten, finden Sie unter [bewährte Methoden für die Verwendung von Office 365 bei langsamen Netzwerken](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166) . In diesem Artikel links out zu Lasten von Inhalten auf TechNet und Support.office.com für Ihre Office 365-Erfahrung optimieren und enthält Informationen über die einfache Verfahren zum Anpassen von Webseiten und wie Sie Ihre Einstellungen für Internet Explorer für die beste Office 365-Erfahrung festlegen. 
    
2. Lesen Sie [Office 365 Network Connectivity Prinzipien](https://aka.ms/o365networkingprinciples) , um die Konnektivität Prinzipien für die sichere Verwaltung von Office 365-Datenverkehr und erste die bestmögliche Leistung zu verstehen. In diesem Artikel helfen Ihnen das Verständnis der neuesten Anleitung zur Optimierung von Office 365-Netzwerkkonnektivität sicher. 
    
3. Verbessern der e-Mail-migrationsleistung durch sorgfältige Planung und Verwaltung des Zeitplans für die Windows-Updates. Sie können Ihren Clientcomputern in Batches aktualisieren und stellen Sie sicher, dass alle Clientcomputer vor der Migration zu Office 365 ein, um die Verwendung der Netzwerkbandbreite Weise aktualisiert werden. Weitere Informationen finden Sie unter [Manuelles Aktualisieren und Konfigurieren von Desktopcomputern für Office 365 für die neuesten Updates](https://support.microsoft.com/gp/office-2013-365-update).
    
4. Office 365 Netzwerkdatenverkehr führt am besten, wenn es als vertrauenswürdigen Internetdienst behandelt und einen Großteil der traditionellen Filter- und Überprüfung, die auf den Netzwerkverkehr zu nicht vertrauenswürdigen Internetdienste einige Organisationen setzen umgehen zulässig. Dies umfasst in der Regel ausgehende Verarbeitung wie Proxy Benutzerauthentifizierung und Paketinspektion als auch lokale Ausgang an das Internet mit den richtigen Network Address Translation (NAT) und ausreichende Bandbreitenkapazität, die erhöhte behandeln sicherstellen entfernen Netzwerk-Anfragen. Weitere Anleitungen zum Konfigurieren des Netzwerks zur Verarbeitung von Office 365 als vertrauenswürdigen Internetdienst in Ihrem Netzwerk finden Sie unter [Verwalten von Office 365-Endpunkten](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a).
    
1. Sicherzustellen Sie [Verwalten von Office 365-Endpunkten](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a). Der zusätzliche Datenverkehr zu Office 365 erzeugt einen Anstieg der ausgehenden Proxyverbindungen als auch einen Anstieg beim sicheren Datenverkehr über TLS/SSL.
    
2. Wenn Ihre ausgehenden Proxys Benutzerauthentifizierung langsame Verbindung oder ein Funktionalitätsverlust auftreten können erfordern. Die Authentifizierungsanforderung für die Office 365-Domänen umgehen kann diesen Aufwand reduziert werden.
    
3. Wenn Sie eine große Anzahl an freigegebenen Kalendern und Postfächern besitzen, stellen Sie möglicherweise einen Anstieg der Anzahl an Verbindungen von Outlook zu Exchange fest. So kann der Outlook-Client z. B. für jeden freigegebenen Kalender in Verwendung bis zu zwei zusätzliche Verbindungen öffnen. Stellen Sie in diesem Fall sicher, dass der Zugangsproxy die Verbindungen verarbeiten kann, oder umgehen Sie den Proxy für Verbindungen zu Office 365 für Outlook.
    
4. Bestimmen Sie die maximale Anzahl von unterstützten Geräten für eine öffentliche IP-Adresse und zum Lastenausgleich über mehrere IP-Adressen. Weitere Informationen finden Sie unter [NAT-Unterstützung mit Office 365](nat-support-with-office-365.md).
    
5. Wenn beim Überprüfen von ausgehender Verbindungen von Computern in Ihrem Netzwerk die Umgehung dieser Filter auf die Office 365-Domänen und die Leistung verbessert wird. Darüber hinaus umgehen häufig ausgehende Prüfung entfällt die Notwendigkeit einer einzelnen Internet Ausgang und ermöglicht lokalen Internet Ausgang für Office 365 bestimmt Netzwerk Anforderungen.
    
6. Einige Kunden Hier finden Sie internen Netzwerkeinstellungen Leistung auswirken können. Netzwerk-Einstellungen wie die maximale Größe der Übertragungseinheit, Auto-Verhandlung oder automatische Erkennung und suboptimalen Routen mit dem Internet sind allgemeine Orte zum Suchen.
    
## <a name="network-planning-reference-for-office-365"></a>Netzwerkplanung für Office 365 – Referenz
<a name="NetReference"> </a>

Diese Themen enthalten ausführliche Referenzinformationen für Office 365-Netzwerk.
  
- [Verwalten von Office 365-Endpunkten](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
    
- [Client-Konnektivität](client-connectivity.md)
    
- [Die Inhaltsübermittlung](content-delivery-networks.md)
    
- [Externe Domain Name System-Einträge für Office 365](external-domain-name-system-records.md)
    
- [IPv6-Unterstützung in Office 365-Diensten](ipv6-support.md)
    
- [Office 365 Network Connectivity Prinzipien](https://aka.ms/o365networkingprinciples)
    
- [Microsoft Virtual Academy: Die Verwaltung Office 365 Leistung](https://mva.microsoft.com/en-us/training-courses/office-365-performance-management-8416)
    
- [Office 365-video-Netzwerke häufig gestellte Fragen (FAQS)](office-365-video-networking-faq.md)
    
- [Planen von Netzwerkgeräten, die eine Verbindung zu Office 365-Diensten herstellen](plan-for-network-devices.md)
    
- [Bereitstellung Berater für Office 365-Dienste](deployment-advisors-for-office-365.md)
    

