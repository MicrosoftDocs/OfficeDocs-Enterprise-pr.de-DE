---
title: Vorbereiten Ihrer Organisation für Office 365 Enterprise
ms.author: robmazz
author: robmazz
manager: laurawi
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- M365-subscription-management
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 712fced7-f9d0-4fde-8b79-286262a5d0bc
description: Wenn Sie sich für die Bereitstellung entschieden haben und nicht das finden, was Sie in unseren grundlegenden Bereitstellungsschritten benötigen, ist dies der richtige Ausgangspunkt.
ms.openlocfilehash: a15bd73efe2fd2e2dfd13b3a444f77b9d0bfc764
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085374"
---
# <a name="get-your-organization-ready-for-office-365-enterprise"></a>Vorbereiten Ihrer Organisation für Office 365 Enterprise

## <a name="what-do-you-need-to-do-to-get-ready-for-office-365"></a>Was müssen Sie tun, um sich für Office 365 vorzubereiten?

Die meisten Organisationen müssen nichts zur Vorbereitung auf Office 365 tun. Es handelt sich um eine Anwendung im Web, und die Benutzer können Sie verwenden, sobald Sie über ein Konto verfügen. Andere Organisationen verfügen über mehr Standorte, Sicherheitsmethoden oder andere Anforderungen, die mehr Planung erfordern. Befolgen Sie für Organisationen auf Unternehmensebene die folgenden Checklisten Elemente, um mit Office 365 zu beginnen.
  
Wenn Sie Hilfe bei der Installation von Office 365 wünschen, stellt [FastTrack](https://fasttrack.microsoft.com/office) die einfachste Möglichkeit zum Bereitstellen von Office 365 dar. Alternativ können Sie sich anmelden und die [Bereitstellungsratgeber für Office 365-Dienste](deployment-advisors-for-office-365.md) verwenden.
  
|**Wählen Sie einen oder mehrere der folgenden Schritte aus:**||
|:-----|:-----|
| [System Anforderungen für Office](https://products.office.com/office-system-requirements) |-Microsoft Office Professional, Office 365, Office 365 proPlus und jede Office-Anwendung für Windows, Mac, iOS und Android verfügen über spezifische Systemanforderungen. Stellen Sie sicher, dass Ihre Hardware und Software die Mindestsystemanforderungen erfüllen.|
|**Die meisten** Kunden verbinden Ihr lokales Verzeichnis mit Office 365. Holen Sie sich einen Vorsprung bei der Verzeichnis Vorbereitung, indem Sie [IdFix in Ihrem Netzwerk installieren und](https://www.microsoft.com/download/details.aspx?id=36832)starten.<br> Verwenden Sie den [Aad Connect Advisor](https://aka.ms/aadconnectpwsync) und das [Azure AD Premium-Set up-Handbuch](https://aka.ms/aadpguidance) , um angepasste Anleitungen für die Einrichtung zu erhalten. <br> |-Automatisierte Prüfungen für Ihr Verzeichnis, um die [Konten der Benutzer zu validieren, werden ordnungsgemäß synchronisiert](https://support.office.com/article/Prepare-to-provision-users-through-directory-synchronization-to-Office-365-01920974-9e6f-4331-a370-13aea4e82b3e). <br> -Empfiehlt Änderungen an Verzeichnisobjekten und angeboten, um die Änderungen für Sie zu automatisieren. <br> - [Weitere Informationen zur Verwendung des IdFix-Tools](prepare-directory-attributes-for-synch-with-idfix.md). |
|**Lesen** Sie unsere [Network Performance Guidance](https://aka.ms/tune) und verwenden Sie unsere Tools, um sicherzustellen, dass Sie über die Konnektivität und Leistungskonfiguration verfügen, die für die optimale Benutzerfreundlichkeit erforderlich ist.  <br> | -Stellen Sie sicher, dass Sie eine Verbindung mit Office 365 herstellen können, wenn Sie ausgehenden Datenverkehr filtern oder überprüfen, sollten Sie verstehen, was die [Verwaltung von office 365](https://support.office.com/article/Managing-Office-365-endpoints-99cab9d4-ef59-4207-9f2b-3728eb46bf9a) -Endpunkten für Ihre Organisation bedeuten.  <br>  - [Modellieren und testen Sie Ihre Netzwerkkapazität](https://support.office.com/article/Network-and-migration-planning-for-Office-365-f5ee6c33-bcd7-4b0b-b0f8-dc1d9fb8d132) , oder wechseln Sie zu einer [Azure express route für Office 365](https://support.office.com/article/Azure-ExpressRoute-for-Office-365-6d2534a2-c19c-4a99-be5e-33a0cee5d3bd) -Schaltung, um eine vorhersehbarere Umgebung zu erreichen.   |
|**Verwenden** Sie unsere [Planungsprüfliste](https://support.office.com/article/Deployment-planning-checklist-for-Office-365-5fa4f6ef-35ad-4840-91c1-4834df3df5a0) als Ausgangspunkt für die Erstellung Ihres eigenen Bereitstellungsplans.  <br> | -Ausführliche Übersicht über die möglichen Bereiche, die Sie benötigen, mit Links zu verweisen oder Vorgehensweise Informationen, die Ihnen bei der Planung helfen. |
|**Verwenden** Sie das [Exchange Server-Skript für größere Elemente](https://gallery.technet.microsoft.com/Exchange-Server-Large-Item-b9546cc6) , um nach e-Mail-Elementen zu suchen, die möglicherweise zu umfangreich sind.  <br> | -Verwendet Exchange-webDienste zum imitieren, zugreifen, Überprüfen des Postfachs für Dateigrößen, die Sie angeben, und Dumps die Ergebnisse in einer CSV-Datei. Lesen Sie die [detaillierten Anweisungen zur Verwendung des Skripts](https://blogs.technet.com/b/mikehall/archive/2013/06/27/large-mail-item-script.aspx). |
|**** Nutzen Sie die [Microsoft-Bereitstellungsexperten](https://go.microsoft.com/fwlink/?LinkId=517115) , die Ihnen bei der Planung helfen, die neuen Dienste und Anwendungen zu verwenden.  <br> Verwenden Sie die Bereitstellungs- [Assistenten für Office 365-Dienste](https://support.office.com/article/Deployment-wizards-for-Office-365-services-165f46e8-3533-4d76-be57-97f81ebd40f2) , um angepasste Anweisungen zur Einrichtung zu erhalten.  <br> | -Das Onboarding-Center arbeitet direkt mit Kunden und Partnerorganisationen. Rufen Sie Sie an. |
|**Verwenden** Sie die [Vorlagen und ressourcen im Office 365-Erfolgs Center](https://www.microsoft.com/fasttrack/resources) , um Ihre Bereitstellung und Onboarding-Pläne für die Personen in Ihrer Organisation freizugeben.  <br> | -Die Kommunikation mit allen Benutzern vor, während und nach dem Übergang zu Office 365 ist kritisch.  <br> -Verwenden Sie unsere Vorlagen, Leitfäden und Handzettel, um Ihre Kommunikation zu verbessern. |
|**Lesen Sie** den artikel [Office 365 Network Connectivity Principles](https://aka.ms/o365networkingprinciples) , um die Verbindungs Prinzipien für die sichere Verwaltung von Office 365-Datenverkehr und die bestmögliche Leistung zu verstehen.  <br> | -Dieser Artikel hilft Ihnen, die neuesten Richtlinien für die sichere Optimierung der Office 365-Netzwerkkonnektivität zu verstehen. |
   
Sie benötigen weitere Ressourcen, die Ihnen bei der Integration von Office 365 mit ihrer umfassenderen Cloud-Strategie helfen? Hier sind die [Ressourcen der Microsoft Cloud-IT-Architektur](https://docs.microsoft.com/en-us/office365/enterprise/microsoft-cloud-it-architecture-resources).
  
## <a name="want-to-talk-with-support"></a>Möchten Sie mit Support sprechen?

Wir helfen Ihnen gerne, [kontaktieren den Support](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) für Business-Produkte.
