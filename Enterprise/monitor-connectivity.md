---
title: Überwachen der Microsoft 365-Konnektivität
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 8/4/2020
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 53cdb60c-a6b2-4848-b3ff-e7b75dc3fd1f
description: Nachdem Sie Microsoft 365 bereitgestellt haben, können Sie die Microsoft 365-Konnektivität mit einigen der unten aufgeführten Tools und Techniken aufrecht erhalten. Sie sollten die offiziellen Richtlinien für den Service Health and Continuity sowie unsere bewährten Methoden für die Verwendung von Microsoft 365 in einem langsamen Netzwerk verstehen.
ms.openlocfilehash: aa47ff76f70e48285c6ca5f21ffdf30f1db52521
ms.sourcegitcommit: a9021ba0800ffc0da21cf2c4da67ab1da2d97099
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2020
ms.locfileid: "46571008"
---
# <a name="monitor-microsoft-365-connectivity"></a><span data-ttu-id="06f4a-104">Überwachen der Microsoft 365-Konnektivität</span><span class="sxs-lookup"><span data-stu-id="06f4a-104">Monitor Microsoft 365 connectivity</span></span>

<span data-ttu-id="06f4a-105">Nachdem Sie Microsoft 365 bereitgestellt haben, können Sie die Microsoft 365-Konnektivität mit einigen der unten aufgeführten Tools und Techniken aufrecht erhalten.</span><span class="sxs-lookup"><span data-stu-id="06f4a-105">Once you've deployed Microsoft 365, you can maintain Microsoft 365 connectivity using some of the tools and techniques below.</span></span> <span data-ttu-id="06f4a-106">Sie sollten die offiziellen Richtlinien für den [Service Health and Continuity](https://docs.microsoft.com/office365/servicedescriptions/office-365-platform-service-description/service-health-and-continuity) sowie unsere [bewährten Methoden für die Verwendung von Microsoft 365 in einem langsamen Netzwerk](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166)verstehen.</span><span class="sxs-lookup"><span data-stu-id="06f4a-106">You'll want to understand the official [Service Health and Continuity](https://docs.microsoft.com/office365/servicedescriptions/office-365-platform-service-description/service-health-and-continuity) guidelines as well as our [Best practices for using Microsoft 365 on a slow network](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166).</span></span> <span data-ttu-id="06f4a-107">Sie möchten auch die [Microsoft 365 admin-App](https://blogs.office.com/2015/03/13/administer-on-the-go-with-the-updated-office-365-admin-app/) nutzen und unsere [Microsoft 365 for Business-Admin-Hilfe](https://support.office.com/article/17d3ff3f-3601-466e-b5a1-482b31cfb791)mit einem Lesezeichen versehen.</span><span class="sxs-lookup"><span data-stu-id="06f4a-107">You'll also want to grab the [Microsoft 365 admin app](https://blogs.office.com/2015/03/13/administer-on-the-go-with-the-updated-office-365-admin-app/) and bookmark our [Microsoft 365 for business - Admin Help](https://support.office.com/article/17d3ff3f-3601-466e-b5a1-482b31cfb791).</span></span>
  
## <a name="monitoring-microsoft-365-connectivity"></a><span data-ttu-id="06f4a-108">Überwachen der Microsoft 365-Konnektivität</span><span class="sxs-lookup"><span data-stu-id="06f4a-108">Monitoring Microsoft 365 Connectivity</span></span>

|||
|:-----|:-----|
|<span data-ttu-id="06f4a-109">**Erhalten einer Benachrichtigung über neue Microsoft 365-Endpunkte**</span><span class="sxs-lookup"><span data-stu-id="06f4a-109">**Getting notified of new Microsoft 365 endpoints**</span></span> <br/> |<span data-ttu-id="06f4a-110">Wenn Sie [Microsoft 365-Endpunkte verwalten](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a), sollten Sie Benachrichtigungen erhalten, wenn wir neue Endpunkte veröffentlichen, können Sie unseren RSS-Feed mit Ihrem bevorzugten RSS-Reader abonnieren.</span><span class="sxs-lookup"><span data-stu-id="06f4a-110">If you're [Managing Microsoft 365 endpoints](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a), you'll want to receive notifications when we publish new endpoints, you can subscribe to our RSS feed using your favorite RSS reader.</span></span> <span data-ttu-id="06f4a-111">Hier erfahren Sie, wie Sie [über Outlook abonnieren](https://go.microsoft.com/fwlink/p/?LinkId=532416) , oder Sie können [die RSS-Feed-Updates per e-Mail](https://go.microsoft.com/fwlink/p/?LinkId=532417)erhalten.</span><span class="sxs-lookup"><span data-stu-id="06f4a-111">Here is how to [subscribe via Outlook](https://go.microsoft.com/fwlink/p/?LinkId=532416) or you can [have the RSS feed updates emailed to you](https://go.microsoft.com/fwlink/p/?LinkId=532417).</span></span>  <br/> |
|<span data-ttu-id="06f4a-112">**Verwenden von System Center zum Überwachen von Microsoft 365**</span><span class="sxs-lookup"><span data-stu-id="06f4a-112">**Use System Center to Monitor Microsoft 365**</span></span> <br/> |<span data-ttu-id="06f4a-113">Wenn Sie Microsoft System Center verwenden, können Sie das [System Center Management Pack für Office 365](https://www.microsoft.com/download/details.aspx?id=43708) zum Starten der Überwachung von Microsoft 365 heute herunterladen.</span><span class="sxs-lookup"><span data-stu-id="06f4a-113">If you're using Microsoft System Center, you can download the [System Center Management Pack for Office 365](https://www.microsoft.com/download/details.aspx?id=43708) to begin monitoring Microsoft 365 today.</span></span> <span data-ttu-id="06f4a-114">Ausführlichere Anleitungen finden Sie im Management Pack-Betriebshandbuch oder in dieser Blogbeitrag- [Office365-Überwachung mithilfe von System Center Operations Manager](https://blogs.msdn.com/b/mvpawardprogram/archive/2015/07/08/office365-monitoring-using-system-centre-operations-manager.aspx) .</span><span class="sxs-lookup"><span data-stu-id="06f4a-114">For more detailed guidance, please see the management pack operations guide or this blog post [Office365 Monitoring using System Centre Operations Manager](https://blogs.msdn.com/b/mvpawardprogram/archive/2015/07/08/office365-monitoring-using-system-centre-operations-manager.aspx)</span></span> <br/> |
|<span data-ttu-id="06f4a-115">**Überwachen des Zustands von Azure ExpressRoute**</span><span class="sxs-lookup"><span data-stu-id="06f4a-115">**Monitoring the health of Azure ExpressRoute**</span></span> <br/> |<span data-ttu-id="06f4a-116">Wenn Sie eine Verbindung mit Microsoft 365 mithilfe von Azure Express Route für Microsoft 365 herstellen, sollten Sie sicherstellen, dass Sie sowohl das Microsoft 365 Service Health Dashboard als auch das Azure [reduzieren der Problem Behandlungszeit mit Azure-Ressourcen Integrität](https://azure.microsoft.com/blog/reduce-troubleshooting-time-with-azure-resource-health/) verwenden.</span><span class="sxs-lookup"><span data-stu-id="06f4a-116">If you are connecting to Microsoft 365 using Azure ExpressRoute for Microsoft 365, you'll want to ensure that you're using both the Microsoft 365 Service Health Dashboard as well as the Azure [Reducing troubleshooting time with Azure Resource health](https://azure.microsoft.com/blog/reduce-troubleshooting-time-with-azure-resource-health/)</span></span> <br/> |
|<span data-ttu-id="06f4a-117">**Verwenden von Azure AD Connect Health mit AD FS**</span><span class="sxs-lookup"><span data-stu-id="06f4a-117">**Using Azure AD Connect Health with AD FS**</span></span> <br/> |<span data-ttu-id="06f4a-118">Wenn Sie AD FS für einmaliges Anmelden mit Microsoft 365 verwenden, sollten Sie zunächst [Azure AD Connect-Integrität zum Überwachen Ihrer AD FS-Infrastruktur verwenden](https://azure.microsoft.com/documentation/articles/active-directory-aadconnect-health-adfs/).</span><span class="sxs-lookup"><span data-stu-id="06f4a-118">If you're using AD FS for Single Sign-On with Microsoft 365, you'll want to begin [using Azure AD Connect Health to monitor your AD FS infrastructure](https://azure.microsoft.com/documentation/articles/active-directory-aadconnect-health-adfs/).</span></span>  <br/> |
|<span data-ttu-id="06f4a-119">**Programmgesteuertes Überwachen von Microsoft 365**</span><span class="sxs-lookup"><span data-stu-id="06f4a-119">**Programmatically monitor Microsoft 365**</span></span> <br/> |<span data-ttu-id="06f4a-120">Lesen Sie unsere Anleitung zur [Microsoft 365-Verwaltungs-API](https://docs.microsoft.com/office/office-365-management-api/office-365-management-apis-overview).</span><span class="sxs-lookup"><span data-stu-id="06f4a-120">Refer to our guidance on the [Microsoft 365 Management API](https://docs.microsoft.com/office/office-365-management-api/office-365-management-apis-overview).</span></span>  <br/> |

<span data-ttu-id="06f4a-121">Mit diesem kurzen Link gelangen Sie wieder hierher zurück: [https://aka.ms/monitorconnectivity365](https://aka.ms/monitorconnectivity365)</span><span class="sxs-lookup"><span data-stu-id="06f4a-121">Here's a short link you can use to come back: [https://aka.ms/monitorconnectivity365](https://aka.ms/monitorconnectivity365)</span></span>
  
## <a name="see-also"></a><span data-ttu-id="06f4a-122">Weitere Artikel</span><span class="sxs-lookup"><span data-stu-id="06f4a-122">See also</span></span>

[<span data-ttu-id="06f4a-123">Konfigurieren von Microsoft 365 Enterprise-Diensten und-Anwendungen</span><span class="sxs-lookup"><span data-stu-id="06f4a-123">Configure Microsoft 365 Enterprise services and applications</span></span>](configure-services-and-applications.md)
  
[<span data-ttu-id="06f4a-124">Vorbereiten Ihrer Organisation für Microsoft 365 Enterprise</span><span class="sxs-lookup"><span data-stu-id="06f4a-124">Get your organization ready for Microsoft 365 Enterprise</span></span>](get-your-organization-ready-for-office-365.md)
  
[<span data-ttu-id="06f4a-125">Netzwerkplanung und Leistungsoptimierung für Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="06f4a-125">Network planning and performance tuning for Microsoft 365</span></span>](network-planning-and-performance.md)
  
[<span data-ttu-id="06f4a-126">Microsoft 365-Integration in lokale Umgebungen</span><span class="sxs-lookup"><span data-stu-id="06f4a-126">Microsoft 365 integration with on-premises environments</span></span>](office-365-integration.md)
  
[<span data-ttu-id="06f4a-127">Verwalten von Microsoft 365-Endpunkten</span><span class="sxs-lookup"><span data-stu-id="06f4a-127">Managing Microsoft 365 endpoints</span></span>](managing-office-365-endpoints.md)
