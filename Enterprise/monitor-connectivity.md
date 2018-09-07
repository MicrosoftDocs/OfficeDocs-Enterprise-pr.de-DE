---
title: Überwachen der Office 365-Konnektivität
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 7/6/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Priority
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 53cdb60c-a6b2-4848-b3ff-e7b75dc3fd1f
description: Nachdem Sie Office 365 bereitgestellt haben, können Sie die Office 365-Konnektivität mithilfe einiger der unten dargestellten Tools und Techniken warten. Sie sollten die offiziellen Richtlinien für die Dienstintegrität und -kontinuität sowie unsere bewährten Methoden für die Verwendung von Office 365 in langsamen Netzwerken verstanden haben. Darüber hinaus ist es sinnvoll, sich die Office 365-Administrator-App zu beschaffen und eine Textmarke für die Office 365 for Business – Administratorhilfe zu setzen.
ms.openlocfilehash: 80e1f56ed3ef7ae2e013239ac286e2a804bd9696
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540708"
---
# <a name="monitor-office-365-connectivity"></a><span data-ttu-id="47df8-105">Überwachen der Office 365-Konnektivität</span><span class="sxs-lookup"><span data-stu-id="47df8-105">Monitor Office 365 connectivity</span></span>

<span data-ttu-id="47df8-p102">Nachdem Sie Office 365 bereitgestellt haben, können Sie die Office 365-Konnektivität mithilfe einiger der unten dargestellten Tools und Techniken warten. Sie sollten die offiziellen Richtlinien für die [Dienstintegrität und -kontinuität](https://technet.microsoft.com/library/office-365-service-health.aspx) sowie unsere [bewährten Methoden für die Verwendung von Office 365 in langsamen Netzwerken](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166) verstanden haben. Darüber hinaus ist es sinnvoll, sich die [Office 365-Administrator-App](https://blogs.office.com/2015/03/13/administer-on-the-go-with-the-updated-office-365-admin-app/) zu beschaffen und eine Textmarke für die [Office 365 for Business – Administratorhilfe](https://support.office.com/article/17d3ff3f-3601-466e-b5a1-482b31cfb791) zu setzen.</span><span class="sxs-lookup"><span data-stu-id="47df8-p102">Once you've deployed Office 365, you can maintain Office 365 connectivity using some of the tools and techniques below. You'll want to understand the official [Service Health and Continuity](https://technet.microsoft.com/library/office-365-service-health.aspx) guidelines as well as our [Best practices for using Office 365 on a slow network](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166). You'll also want to grab the [Office 365 admin app](https://blogs.office.com/2015/03/13/administer-on-the-go-with-the-updated-office-365-admin-app/) and bookmark our [Office 365 for business - Admin Help](https://support.office.com/article/17d3ff3f-3601-466e-b5a1-482b31cfb791).</span></span>
  
## <a name="monitoring-office-365-connectivity"></a><span data-ttu-id="47df8-109">Überwachen der Office 365-Konnektivität</span><span class="sxs-lookup"><span data-stu-id="47df8-109">Monitoring Office 365 Connectivity</span></span>

|||
|:-----|:-----|
|<span data-ttu-id="47df8-110">**Erhalten von Benachrichtigungen zu neuen Office 365-Endpunkten**</span><span class="sxs-lookup"><span data-stu-id="47df8-110">**Getting notified of new Office 365 endpoints**</span></span> <br/> |<span data-ttu-id="47df8-p103">Wenn Sie beim [Verwalten von Office 365-Endpunkten](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a) Benachrichtigungen erhalten möchten, wenn wir neue Endpunkte veröffentlichen, können Sie unseren RSS-Feed mithilfe Ihres bevorzugten RSS-Readers abonnieren. Hier erfahren Sie, wie Sie [per Outlook abonnieren](https://go.microsoft.com/fwlink/p/?LinkId=532416) oder [Updates vom RSS-Feed per E-Mail an Sie senden lassen](https://go.microsoft.com/fwlink/p/?LinkId=532417) können. </span><span class="sxs-lookup"><span data-stu-id="47df8-p103">If you're [Managing Office 365 endpoints](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a), you'll want to receive notifications when we publish new endpoints, you can subscribe to our RSS feed using your favorite RSS reader. Here is how to [subscribe via Outlook](https://go.microsoft.com/fwlink/p/?LinkId=532416) or you can [have the RSS feed updates emailed to you](https://go.microsoft.com/fwlink/p/?LinkId=532417).  </span></span><br/> |
|<span data-ttu-id="47df8-113">**Verwenden von System Center zum Überwachen von Office 365**</span><span class="sxs-lookup"><span data-stu-id="47df8-113">**Use System Center to Monitor Office 365**</span></span> <br/> |<span data-ttu-id="47df8-p104">Wenn Sie Microsoft System Center verwenden, können Sie das [System Center Management Pack für Office 365](https://www.microsoft.com/download/details.aspx?id=43708) herunterladen, um noch heute mit der Überwachung von Office 365 zu beginnen. Detailliertere Anweisungen finden Sie im Management Pack-Betriebshandbuch oder in diesem Blogbeitrag [Office365 Monitoring using System Centre Operations Manager](https://blogs.msdn.com/b/mvpawardprogram/archive/2015/07/08/office365-monitoring-using-system-centre-operations-manager.aspx) (Überwachen von Office 365 mit dem System Center Operations Manager)</span><span class="sxs-lookup"><span data-stu-id="47df8-p104">If you're using Microsoft System Center, you can download the [System Center Management Pack for Office 365](https://www.microsoft.com/download/details.aspx?id=43708) to begin monitoring Office 365 today. For more detailed guidance, please see the management pack operations guide or this blog post [Office365 Monitoring using System Centre Operations Manager](https://blogs.msdn.com/b/mvpawardprogram/archive/2015/07/08/office365-monitoring-using-system-centre-operations-manager.aspx)</span></span> <br/> |
|<span data-ttu-id="47df8-116">**Überwachen des Zustands von Azure ExpressRoute**</span><span class="sxs-lookup"><span data-stu-id="47df8-116">**Monitoring the health of Azure ExpressRoute**</span></span> <br/> |<span data-ttu-id="47df8-117">Wenn Sie die Verbindung mit Office 365 mithilfe von Azure ExpressRoute für Office 365 herstellen, sollten Sie sicherstellen, dass Sie sowohl das Office 365 Service Health Dashboard als auch den Azure-Blog [Reducing troubleshooting time with Azure Resource health](https://azure.microsoft.com/blog/reduce-troubleshooting-time-with-azure-resource-health/) (Verringern des Zeitaufwands für die Problembehandlung mit Azure Resource Health) nutzen</span><span class="sxs-lookup"><span data-stu-id="47df8-117">If you are connecting to Office 365 using Azure ExpressRoute for Office 365, you'll want to ensure that you're using both the Office 365 Service Health Dashboard as well as the Azure [Reducing troubleshooting time with Azure Resource health](https://azure.microsoft.com/blog/reduce-troubleshooting-time-with-azure-resource-health/)</span></span> <br/> |
|<span data-ttu-id="47df8-118">**Verwenden von Azure AD Connect Health mit AD FS**</span><span class="sxs-lookup"><span data-stu-id="47df8-118">**Using Azure AD Connect Health with AD FS**</span></span> <br/> |<span data-ttu-id="47df8-119">Wenn Sie AD FS für einmaliges Anmelden mit Office 365 verwenden, sollten Sie mit dem [Verwenden von Azure AD Connect Health zum Überwachen Ihrer AD FS-Infrastruktur](https://azure.microsoft.com/documentation/articles/active-directory-aadconnect-health-adfs/) beginnen.</span><span class="sxs-lookup"><span data-stu-id="47df8-119">If you're using AD FS for Single Sign-On with Office 365, you'll want to begin [using Azure AD Connect Health to monitor your AD FS infrastructure](https://azure.microsoft.com/documentation/articles/active-directory-aadconnect-health-adfs/).</span></span>  <br/> |
|<span data-ttu-id="47df8-120">**Programmgesteuerte Überwachung von Office 365**</span><span class="sxs-lookup"><span data-stu-id="47df8-120">**Programmatically monitor Office 365**</span></span> <br/> |<span data-ttu-id="47df8-121">Richten Sie sich nach unserem Leitfaden zur [Office 365-Verwaltungs-API](https://msdn.microsoft.com/library/jj984343%28v=office.15%29.aspx).</span><span class="sxs-lookup"><span data-stu-id="47df8-121">Refer to our guidance on the [Office 365 Management API](https://msdn.microsoft.com/library/jj984343%28v=office.15%29.aspx).</span></span>  <br/> |

<span data-ttu-id="47df8-122">Mit diesem kurzen Link gelangen Sie wieder hierher zurück: [hhttps://aka.ms/monitorconnectivity365](https://aka.ms/monitorconnectivity365)</span><span class="sxs-lookup"><span data-stu-id="47df8-122">Here's a short link you can use to come back: [hhttps://aka.ms/monitorconnectivity365](https://aka.ms/monitorconnectivity365)</span></span>
  
## <a name="see-also"></a><span data-ttu-id="47df8-123">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="47df8-123">See also</span></span>

[<span data-ttu-id="47df8-124">Konfigurieren von Diensten und Anwendungen in Office 365 Enterprise</span><span class="sxs-lookup"><span data-stu-id="47df8-124">Configure Office 365 Enterprise services and applications</span></span>](configure-services-and-applications.md)
  
[<span data-ttu-id="47df8-125">Vorbereiten Ihrer Organisation für Office 365 Enterprise</span><span class="sxs-lookup"><span data-stu-id="47df8-125">Get your organization ready for Office 365 Enterprise</span></span>](get-your-organization-ready-for-office-365.md)
  
[<span data-ttu-id="47df8-126">Netzwerkplanung und Leistungsoptimierung für Office 365</span><span class="sxs-lookup"><span data-stu-id="47df8-126">Network planning and performance tuning for Office 365</span></span>](network-planning-and-performance.md)
  
<span data-ttu-id="47df8-127">[Office 365-Integration in lokale Umgebungen](office-365-integration.md)</span><span class="sxs-lookup"><span data-stu-id="47df8-127">Your existing active directory [Office 365 integration with on-premises environments](office-365-integration.md) or</span></span>
  
[<span data-ttu-id="47df8-128">Verwalten von Office 365-Endpunkten</span><span class="sxs-lookup"><span data-stu-id="47df8-128">Managing Office 365 endpoints</span></span>](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
