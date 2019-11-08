---
title: Office 365 Überwachung und Überwachung von Zugriffssteuerungen
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
description: 'Zusammenfassung: eine Zusammenfassung der verschiedenen Überwachungs-und Überwachungs Zugriffssteuerungen, die in Office 365 verfügbar sind.'
ms.openlocfilehash: f42fd642985d64a3e50daa401f438327a0cbae3a
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2019
ms.locfileid: "38031970"
---
# <a name="monitoring-and-auditing-access-controls-in-office-365"></a>Überwachen und Überwachen von Zugriffssteuerungen in Office 365

Microsoft führt eine umfassende Überwachung und Überwachung aller Delegierungen, Berechtigungen und Vorgänge durch, die in Office 365 auftreten. Office 365 Zugriffssteuerung ist ein automatisierter Prozess, der auf dem Prinzip der geringsten Rechte basiert und Datenzugriffs Steuerelemente und-Überprüfungen einbindet:

- Alle zulässigen Zugriffe können auf einen eindeutigen Benutzer zurückgeführt werden. Administratoren sind für die Verarbeitung von Kundeninhalten verantwortlich.
- Zugriffssteuerungsanforderungen, Genehmigungen und Administrative Operations Protokolle werden zur Analyse von Sicherheit und böswilligen Ereignissen erfasst.
- Zugriffsebenen werden basierend auf der Sicherheitsgruppenmitgliedschaft nahezu in Echtzeit überprüft, um sicherzustellen, dass nur Benutzer mit autorisierten geschäftlichen Begründungen und den Berechtigungsanforderungen Zugriff auf die Systeme haben.
- Office 365, die Zugriffssteuerung und die unterstützenden Dienste, einschließlich Azure Active Directory und physische Rechenzentren, werden regelmäßig von unabhängigen Drittanbietern für die Einhaltung von [ISO/IEC 27001](https://www.microsoft.com/TrustCenter/Compliance/iso-iec-27001), [ISO/IEC 27018](https://www.microsoft.com/TrustCenter/Compliance/iso-iec-27018), [SOC](https://www.microsoft.com/TrustCenter/Compliance/SOC), [FedRAMP](https://www.microsoft.com/TrustCenter/Compliance/FedRAMP)und anderen [Standards](https://www.microsoft.com/TrustCenter/Compliance?service=Office#Icons)überwacht.
- Office 365 Ingenieure müssen jährlich Sicherheitsschulungen durchführen, die bewährten Methoden für den erhöhten Zugriff überprüfen und die Sicherheits-und Datenschutzrichtlinien von Microsoft anerkennen, um die Berechtigungen für den Dienst beizubehalten.

Automatische Warnungen werden ausgelöst, wenn verdächtige Aktivitäten erkannt werden, beispielsweise mehrere fehlgeschlagene Anmeldungen innerhalb eines kurzen Zeitraums. Das Office 365-Sicherheitsantwort Team verwendet Maschinelles Lernen und eine große Datenanalyse, um Aktivitäten zu überprüfen und zu analysieren, nach unregelmäßigen Zugriffsmustern zu suchen und proaktiv auf anomale und unerlaubte Aktivitäten zu reagieren. Microsoft beschäftigt außerdem ein dediziertes Team von Penetrations Testern und engagiert sich in regelmäßigen roten Team-und blauen Teamübungen, um Sicherheits-und Zugriffssteuerungsprobleme im Dienst zu finden. Kunden können die Effektivität von Zugriffs Steuerungssystemen mithilfe von Überwachungsberichten und der von Office 365 bereitgestellten Verwaltungs Aktivitäts-API überprüfen.

Weitere Informationen finden Sie unter [Office 365 Management Activity API Reference](https://msdn.microsoft.com/library/office/mt227394.aspx) and [Auditing and Reporting in Office 365](office-365-auditing-and-reporting-overview.md).
