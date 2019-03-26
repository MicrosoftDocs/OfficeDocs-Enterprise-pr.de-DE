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
description: Enthält Links zu Informationen zur Netzwerkplanung und-Tests sowie zur Migration zu Office 365.
ms.openlocfilehash: 02576933a1be615e65b695a7dd72c19eed311c91
ms.sourcegitcommit: 4ef8e113fa20b539de1087422455fc26ff123d55
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "30574039"
---
# <a name="network-and-migration-planning-for-office-365"></a>Netzwerk- und Migrationsplanung für Office 365

Dieser Artikel enthält Links zu Informationen zur Netzwerkplanung und-Tests sowie zur Migration zu Office 365.
  
Bevor Sie das erste Mal bereitstellen oder zu Office 365 migrieren, können Sie anhand der Informationen in diesen Themen die benötigte Bandbreite schätzen und dann testen und sicherstellen, dass genügend Bandbreite für die Bereitstellung oder Migration zu Office 365 zur Verfügung steht.

||
|:-----|
| Dieser Artikel ist Teil der [Netzwerkplanung und Leistungsoptimierung für Office 365](https://aka.ms/tune).|

|||
|:-----|:-----|
|![Weitere Informationen finden Sie unter Microsoft Cloud Networking for Enterprise Architects Poster](media/3094be9f-2407-4fa5-896d-aa66ef7b9bb9.png)|Die Schritte zur Optimierung Ihres Netzwerks für Office 365 und andere Microsoft Cloud-Plattformen und-Dienste finden Sie unter [Microsoft Cloud Networking for Enterprise Architects](https://aka.ms/cloudarchnetworking) Poster. |
   
## <a name="estimate-network-bandwidth-requirements"></a>Schätzen der Anforderungen an die Netzwerkbandbreite
<a name="EstimateBandwidthRequirements"> </a>

Durch die Verwendung von Office 365 kann die Nutzung der Internetverbindung Ihrer Organisation erhöht werden. Es ist wichtig zu ermitteln, ob der Umfang der derzeit verfügbaren Bandbreite ausreicht, um die geschätzte Aufstockung zu bewältigen, nachdem Office 365 vollständig bereitgestellt wurde, und gleichzeitig mindestens 20% der Kapazität für die Verarbeitung der am stärksten verbliebenen Tage.
  
Gehen Sie folgendermaßen vor, um die Bandbreite zu schätzen:
  
1. Bewerten Sie die Anzahl der Clients, die die einzelnen Internet Ausgänge verwenden werden. Lassen Sie unser Multi-Terabit-Netzwerk so viele Verbindungen wie möglich verarbeiten. 
    
2. Legen Sie fest, welche Office 365-Dienste und-Features für Clients verfügbar sein sollen. Wahrscheinlich haben Sie Gruppen von Personen mit unterschiedlichen Diensten oder Nutzungsprofilen.
    
3. Messen Sie die Netzwerkverwendung für eine Pilotgruppe von Clients. Stellen Sie sicher, dass die Pilot Clients repräsentativ für die verschiedenen Profile von Personen in der Organisation und die verschiedenen geografischen Standorte sind. Sie können Ihre Ergebnisse gegen unsere alten Rechner für [Exchange ](https://go.microsoft.com/fwlink/p/?LinkId=321550)und [Skype for Business](https://go.microsoft.com/fwlink/p/?LinkId=321551) oder die [Fallstudie](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365) , die wir in unserem eigenen Netzwerk durchgeführt haben, überprüfen. 
    
4. Verwenden Sie die Messungen aus der Pilotgruppe, um die Anforderungen der gesamten Organisation hochzurechnen und erneut zu testen, um die Schätzungen zu überprüfen, bevor Sie Änderungen am Netzwerk vornehmen.
    
## <a name="test-your-existing-network"></a>Testen des vorhandenen Netzwerks
<a name="calculators"> </a>

 **Netzwerktools.** Testen und überprüfen Sie Ihre Internet Bandbreite, um Download-, Upload-und Latenz Einschränkungen zu bestimmen. Diese Tools helfen Ihnen dabei, die Möglichkeiten Ihres Netzwerks für die Migration sowie nach der vollständigen Bereitstellung zu bestimmen. 
  
- [Microsoft Message Analyzer](https://technet.microsoft.com/library/jj649776.aspx): Message Analyzer ist ein effektives Tool zur Problembehandlung von Netzwerkproblemen. Der Nachrichten Analysator erfasst, zeigt und analysiert protokollbasierten Messaging Datenverkehr und Systemnachrichten. Mit der Nachrichten Analyse können Sie auch Daten aus Protokoll-und Ablaufverfolgungsdateien importieren, Aggregieren und analysieren.
    
- [Microsoft Remote Connectivity Analyzer](https://go.microsoft.com/fwlink/p/?LinkId=517243): testet die Konnektivität in Ihrer Exchange Online-Umgebung.
    
- Verwenden Sie den [Microsoft-Support-und Wiederherstellungs-Assistenten für office 365](https://diagnostics.office.com/#/Download?env=SOC) , um Outlook-und Office 365-Probleme zu beheben. 
    
## <a name="best-practices-for-network-planning-and-improving-migration-performance-for-office-365"></a>Bewährte Methoden für die Netzwerkplanung und die Verbesserung der Migrationsleistung für Office 365
<a name="BestPractices"> </a>

In diesen bewährten Methoden erhalten Sie weitere Informationen zum Verbessern der Office 365-Umgebung.
  
1. Sie möchten Ihren Benutzern sofort helfen? Tipps zur Verwendung von Office 365, einschließlich SharePoint Online, Exchange Online und lync Online, wenn Ihr Netzwerk einfach nicht kooperiert, finden Sie unter [bewährte Methoden für die Verwendung von office 365 in einem langsamen Netzwerk](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166) . Dieser Artikel enthält Links zu vielen Inhalten auf TechNet und Support.office.com zur Optimierung Ihrer Office 365-Benutzeroberfläche sowie Informationen zu einfachen Methoden zum Anpassen Ihrer Webseiten und zum Festlegen der Internet Explorer-Einstellungen für die beste Office 365-Umgebung. 
    
2. Lesen Sie die [Grundprinzipien der office 365-Netzwerkkonnektivität](https://aka.ms/o365networkingprinciples) , um die Verbindungs Prinzipien für die sichere Verwaltung von Office 365-Datenverkehr und die bestmögliche Leistung zu verstehen. Dieser Artikel hilft Ihnen, die neuesten Richtlinien für die sichere Optimierung der Office 365-Netzwerkkonnektivität zu verstehen. 
    
3. Verbessern der e-Mail-Migrationsleistung durch sorgfältiges Verwalten des Zeitplans für Windows-Updates Sie können Ihre Clientcomputer in Batches aktualisieren und sicherstellen, dass alle Clientcomputer vor der Migration zu Office 365 aktualisiert werden, um die Verwendung der Netzwerkbandbreite zu regulieren. Weitere Informationen finden Sie unter [Manuelles Aktualisieren und Konfigurieren von Desktops für Office 365 für die neuesten Updates](https://support.microsoft.com/gp/office-2013-365-update).
    
4. Der Netzwerkdatenverkehr von Office 365 ist am besten geeignet, wenn er als vertrauenswürdiger Internetdienst behandelt wird und die herkömmliche Filterung und Überprüfung, die einige Organisationen für den Netzwerkdatenverkehr an nicht vertrauenswürdige Internetdienste durchführen, möglicherweise umgehen kann. Hierzu gehört in der Regel das Entfernen der ausgehenden Verarbeitung wie Proxybenutzer Authentifizierung und Paketprüfung sowie das Sicherstellen des lokalen Ausstiegs auf das Internet mit der richtigen Netzwerkadressübersetzung (Network Address Translation, NAT) und ausreichender Bandbreitenkapazität zur Verarbeitung der erhöhten Netzwerkanforderungen. Weitere Hinweise zum Konfigurieren Ihres Netzwerks zur Behandlung von Office 365 als vertrauenswürdigen Internet Dienst in Ihrem Netzwerk finden Sie unter [Managing office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)Endpoints.
    
1. Sicherstellen der [Verwaltung von Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)-Endpunkten Der zusätzliche Datenverkehr zu Office 365 führt zu einer Verbesserung der ausgehenden Proxyverbindungen sowie zu einer erhöhten Sicherheit des Datenverkehrs über TLS/SSL.
    
2. Wenn für Ihre ausgehenden Proxys eine Benutzerauthentifizierung erforderlich ist, kann es zu einer langsamen Verbindung oder Funktionalitätsverlusten führen. Wenn Sie die Authentifizierungsanforderung für die Office 365-Domänen umgehen, können Sie diesen Aufwand reduzieren.
    
3. Wenn Sie eine hohe Anzahl von freigegebenen Kalendern und Postfächern haben, wird möglicherweise eine Vergrößerung der Anzahl von Verbindungen zwischen Outlook und Exchange angezeigt. Beispielsweise kann der Outlook-Client bis zu zwei zusätzliche Verbindungen für jeden freigegebenen Kalender öffnen, der verwendet wird. Stellen Sie in dieser Situation sicher, dass der Ausstiegs Proxy die Verbindungen verarbeiten kann, oder umgehen Sie den Proxy für Verbindungen mit Office 365 für Outlook.
    
4. Bestimmen Sie die maximale Anzahl unterstützter Geräte für eine öffentliche IP-Adresse und wie Sie einen Lastenausgleich über mehrere IP-Adressen hinweg durchgehen. Weitere Informationen finden Sie unter [NAT-Unterstützung für Office 365](nat-support-with-office-365.md).
    
5. Wenn Sie ausgehende Verbindungen von Computern in Ihrem Netzwerk überprüfen, werden durch Umgehung dieser Filterung auf die Office 365-Domänen Konnektivität und Leistung verbessert. Darüber hinaus wird bei der Umgehung der ausgehenden Überprüfung häufig die Notwendigkeit eines einzelnen Internet Ausstiegs beseitigt und das lokale Internet-Ausstiegs für Office 365 für bestimmte Netzwerkanforderungen aktiviert.
    
6. Einige Kunden finden, dass interne Netzwerkeinstellungen die Leistung beeinträchtigen können. Einstellungen wie maximale Übertragungseinheit (MTU)-Größe, automatische Netzwerk Aushandlung oder automatische Erkennung sowie suboptimale Routen zum Internet sind häufig verwendete Orte.
    
## <a name="network-planning-reference-for-office-365"></a>Referenz zur Netzwerkplanung für Office 365
<a name="NetReference"> </a>

Diese Themen enthalten detaillierte Office 365-Netzwerk Referenzinformationen.
  
- [Verwalten von Office 365-Endpunkten](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
    
- [Clientkonnektivität](client-connectivity.md)
    
- [Netzwerke für die Inhaltsübermittlung](content-delivery-networks.md)
    
- [Externe DNS-Einträge für Office 365](external-domain-name-system-records.md)
    
- [IPv6-Unterstützung in Office 365-Diensten](ipv6-support.md)
    
- [Prinzipien von Office 365-Netzwerkverbindungen](https://aka.ms/o365networkingprinciples)
    
- [Office 365 Video Networking-häufig gestellte Fragen (FAQ)](office-365-video-networking-faq.md)
    
- [Planen von Netzwerkgeräten, die eine Verbindung mit Office 365-Diensten herstellen](plan-for-network-devices.md)
    
- [Bereitstellungs Ratgeber für Office 365-Dienste](deployment-advisors-for-office-365.md)
    

