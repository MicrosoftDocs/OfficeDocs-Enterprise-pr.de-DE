---
title: Überwachen der Office 365-Konnektivität
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 7/6/2017
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Priority
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 53cdb60c-a6b2-4848-b3ff-e7b75dc3fd1f
description: Nachdem Sie Office 365 bereitgestellt haben, können Sie die Office 365-Konnektivität mithilfe einiger der unten dargestellten Tools und Techniken warten. Sie sollten die offiziellen Richtlinien für die Dienstintegrität und -kontinuität sowie unsere bewährten Methoden für die Verwendung von Office 365 in langsamen Netzwerken verstanden haben. Darüber hinaus ist es sinnvoll, sich die Office 365-Administrator-App zu beschaffen und eine Textmarke für die Office 365 for Business – Administratorhilfe zu setzen.
ms.openlocfilehash: 5a0a6e217d0f74f6266bffa1bd6037427f14e7bd
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/07/2020
ms.locfileid: "41843706"
---
# <a name="monitor-office-365-connectivity"></a>Überwachen der Office 365-Konnektivität

Nachdem Sie Office 365 bereitgestellt haben, können Sie die Office 365-Konnektivität mithilfe einiger der unten dargestellten Tools und Techniken warten. Sie sollten die offiziellen Richtlinien für die [Dienstintegrität und -kontinuität](https://docs.microsoft.com/office365/servicedescriptions/office-365-platform-service-description/service-health-and-continuity) sowie unsere [bewährten Methoden für die Verwendung von Office 365 in langsamen Netzwerken](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166) verstanden haben. Darüber hinaus ist es sinnvoll, sich die [Office 365-Administrator-App](https://blogs.office.com/2015/03/13/administer-on-the-go-with-the-updated-office-365-admin-app/) zu beschaffen und eine Textmarke für die [Office 365 for Business – Administratorhilfe](https://support.office.com/article/17d3ff3f-3601-466e-b5a1-482b31cfb791) zu setzen.
  
## <a name="monitoring-office-365-connectivity"></a>Überwachen der Office 365-Konnektivität

|||
|:-----|:-----|
|**Erhalten von Benachrichtigungen zu neuen Office 365-Endpunkten** <br/> |Wenn Sie beim [Verwalten von Office 365-Endpunkten](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a) Benachrichtigungen erhalten möchten, wenn wir neue Endpunkte veröffentlichen, können Sie unseren RSS-Feed mithilfe Ihres bevorzugten RSS-Readers abonnieren. Hier erfahren Sie, wie Sie [per Outlook abonnieren](https://go.microsoft.com/fwlink/p/?LinkId=532416) oder [Updates vom RSS-Feed per E-Mail an Sie senden lassen](https://go.microsoft.com/fwlink/p/?LinkId=532417) können. <br/> |
|**Verwenden von System Center zum Überwachen von Office 365** <br/> |Wenn Sie Microsoft System Center verwenden, können Sie das [System Center Management Pack für Office 365](https://www.microsoft.com/download/details.aspx?id=43708) herunterladen, um noch heute mit der Überwachung von Office 365 zu beginnen. Detailliertere Anweisungen finden Sie im Management Pack-Betriebshandbuch oder in diesem Blogbeitrag [Office365 Monitoring using System Centre Operations Manager](https://blogs.msdn.com/b/mvpawardprogram/archive/2015/07/08/office365-monitoring-using-system-centre-operations-manager.aspx) (Überwachen von Office 365 mit dem System Center Operations Manager) <br/> |
|**Überwachen des Zustands von Azure ExpressRoute** <br/> |Wenn Sie die Verbindung mit Office 365 mithilfe von Azure ExpressRoute für Office 365 herstellen, sollten Sie sicherstellen, dass Sie sowohl das Office 365 Service Health Dashboard als auch den Azure-Blog [Reducing troubleshooting time with Azure Resource health](https://azure.microsoft.com/blog/reduce-troubleshooting-time-with-azure-resource-health/) (Verringern des Zeitaufwands für die Problembehandlung mit Azure Resource Health) nutzen <br/> |
|**Verwenden von Azure AD Connect Health mit AD FS** <br/> |Wenn Sie AD FS für einmaliges Anmelden mit Office 365 verwenden, sollten Sie mit dem [Verwenden von Azure AD Connect Health zum Überwachen Ihrer AD FS-Infrastruktur](https://azure.microsoft.com/documentation/articles/active-directory-aadconnect-health-adfs/) beginnen.  <br/> |
|**Programmgesteuerte Überwachung von Office 365** <br/> |Richten Sie sich nach unserem Leitfaden zur [Office 365-Verwaltungs-API](https://docs.microsoft.com/office/office-365-management-api/office-365-management-apis-overview).  <br/> |

Mit diesem kurzen Link gelangen Sie wieder hierher zurück: [https://aka.ms/monitorconnectivity365](https://aka.ms/monitorconnectivity365)
  
## <a name="see-also"></a>Weitere Artikel

[Konfigurieren von Diensten und Anwendungen in Office 365 Enterprise](configure-services-and-applications.md)
  
[Vorbereiten Ihrer Organisation für Office 365 Enterprise](get-your-organization-ready-for-office-365.md)
  
[Netzwerkplanung und Leistungsoptimierung für Office 365](network-planning-and-performance.md)
  
[Office 365-Integration in lokale Umgebungen](office-365-integration.md)
  
[Verwalten von Office 365-Endpunkten](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
