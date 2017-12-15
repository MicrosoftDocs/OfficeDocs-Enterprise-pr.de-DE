---
title: Testumgebungsanleitung Konfigurieren einer integrierten Exchange-, Lync- und SharePoint-Testumgebung
ms.author: jhendr
author: JoanneHendrickson
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 48e16935-3429-456a-8fe6-50afa257924c
description: "Zusammenfassung: Erfahren Sie, wie Sie eine integrierte Testumgebung erstellen, in der ein Server mit Exchange Server 2013, ein Server mit Lync Server 2013 und ein Server mit SharePoint Server 2013 ausgeführt werden."
ms.openlocfilehash: 6fc3bc05db0d28bc4de2be77671ccf5e8fc55926
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2017
---
# <a name="test-lab-guide-configure-an-integrated-exchange-lync-and-sharepoint-test-lab"></a><span data-ttu-id="5b08e-103">Testumgebungsanleitung: Konfigurieren einer integrierten Exchange-, Lync- und SharePoint-Testumgebung</span><span class="sxs-lookup"><span data-stu-id="5b08e-103">Test Lab Guide: Configure an integrated Exchange, Lync, and SharePoint test lab</span></span>

 <span data-ttu-id="5b08e-104">**Zusammenfassung:** Erfahren Sie, wie eine integrierte Testlabor erstellen, enthält einen Server, der Exchange Server 2013 ausgeführt wird, einem Server mit Lync Server 2013 und einem Server mit SharePoint Server 2013.</span><span class="sxs-lookup"><span data-stu-id="5b08e-104">**Summary:** Learn how to create an integrated test lab that contains a server that runs Exchange Server 2013, a server that runs Lync Server 2013, and a server that runs SharePoint Server 2013.</span></span>
  
<span data-ttu-id="5b08e-105">Die Testumgebung, die aus dieser Konfiguration resultiert und die Server-zu-Server-Authentifizierung zwischen allen drei Servertypen vorsieht, kann verwendet werden, um Szenarien und Lösungen mit mehreren Produkten zu erstellen und zu veranschaulichen, in denen ein Server mit Exchange Server 2013, ein Server mit Lync Server 2013 und ein Server mit SharePoint Server 2013 ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="5b08e-105">The test lab that results from this configuration, which includes server-to-server authentication between all three types of servers, can be used to build out and demonstrate multi-product scenarios and solutions that use a server that runs Exchange Server 2013, a server that runs Lync Server 2013, and a server that runs SharePoint Server 2013.</span></span>
  
<span data-ttu-id="5b08e-106">Dieses Dokument enthält Anleitungen zu den folgenden Punkten:</span><span class="sxs-lookup"><span data-stu-id="5b08e-106">This document contains instructions for the following:</span></span>
  
1. <span data-ttu-id="5b08e-107">Konfigurieren der Testumgebung "Windows Server 2012-Basiskonfiguration"</span><span class="sxs-lookup"><span data-stu-id="5b08e-107">Configuring the Windows Server 2012 Base Configuration test lab.</span></span>
    
2. <span data-ttu-id="5b08e-108">Installieren und Konfigurieren eines neuen Servers mit dem Namen SQL1</span><span class="sxs-lookup"><span data-stu-id="5b08e-108">Installing and configuring a new server named SQL1.</span></span>
    
3. <span data-ttu-id="5b08e-109">Installieren von SQL Server 2012 auf dem Server SQL1</span><span class="sxs-lookup"><span data-stu-id="5b08e-109">Installing SQL Server 2012 on the SQL1 server.</span></span>
    
4. <span data-ttu-id="5b08e-110">Installieren und Konfigurieren eines neuen Clientcomputers mit dem Namen CLIENT2</span><span class="sxs-lookup"><span data-stu-id="5b08e-110">Installing and configuring a new client computer named CLIENT2.</span></span>
    
5. <span data-ttu-id="5b08e-111">Installieren und Konfigurieren von Exchange Server 2013 auf EX1</span><span class="sxs-lookup"><span data-stu-id="5b08e-111">Installing and configuring Exchange Server 2013 on EX1.</span></span>
    
6. <span data-ttu-id="5b08e-112">Installieren und Konfigurieren eines neuen Servers mit dem Namen LYNC1</span><span class="sxs-lookup"><span data-stu-id="5b08e-112">Installing and configuring a new server named LYNC1.</span></span>
    
7. <span data-ttu-id="5b08e-113">Installieren von Lync Server 2013 Standard Edition auf LYNC1</span><span class="sxs-lookup"><span data-stu-id="5b08e-113">Installing Lync Server 2013 Standard Edition on LYNC1.</span></span>
    
8. <span data-ttu-id="5b08e-114">Installieren von SharePoint Server 2013 auf SP1</span><span class="sxs-lookup"><span data-stu-id="5b08e-114">Installing SharePoint Server 2013 on SP1.</span></span>
    
9. <span data-ttu-id="5b08e-115">Konfigurieren der Integration zwischen EX1, LYNC1 und SP1</span><span class="sxs-lookup"><span data-stu-id="5b08e-115">Configuring integration between EX1, LYNC1, and SP1.</span></span>
    
<span data-ttu-id="5b08e-116">**Ansehen des Videos zur Testumgebungsanleitung für Exchange, Lync und SharePoint**</span><span class="sxs-lookup"><span data-stu-id="5b08e-116">**Watch the integrated Exchange, Lync, and SharePoint test lab guide overview video**</span></span>

![Videosymbol (Wiedergabetaste)](images/mod_icon_video_M.png)
  
<span data-ttu-id="5b08e-118">Weitere Informationen zum Konfigurieren dieser Testumgebung in Hyper-V finden Sie unter [Hosten der integrierten Exchange-, Lync- und SharePoint-Testumgebung mit Windows Server 2012 Hyper-V](https://social.technet.microsoft.com/wiki/contents/articles/18483.hosting-the-integrated-exchange-lync-and-sharepoint-test-lab-with-windows-server-2012-hyper-v.aspx).</span><span class="sxs-lookup"><span data-stu-id="5b08e-118">For information about how to configure this test lab in Hyper-V, see [Hosting the integrated Exchange, Lync, and SharePoint test lab with Windows Server 2012 Hyper-V](https://social.technet.microsoft.com/wiki/contents/articles/18483.hosting-the-integrated-exchange-lync-and-sharepoint-test-lab-with-windows-server-2012-hyper-v.aspx).</span></span>
  
## <a name="download-the-test-lab-guide"></a><span data-ttu-id="5b08e-119">Die Testumgebungsanleitung herunterladen</span><span class="sxs-lookup"><span data-stu-id="5b08e-119">Download the test lab guide</span></span>

<span data-ttu-id="5b08e-120">[Testumgebungsanleitung: Konfigurieren einer integrierten Exchange-, Lync- und SharePoint-Testumgebung ](https://go.microsoft.com/fwlink/p/?LinkId=313670) (https://go.microsoft.com/fwlink/p/?LinkId=313670)</span><span class="sxs-lookup"><span data-stu-id="5b08e-120">[Test Lab Guide: Configure an Integrated Exchange, Lync, and SharePoint Test Lab](https://go.microsoft.com/fwlink/p/?LinkId=313670) (https://go.microsoft.com/fwlink/p/?LinkId=313670)</span></span>
  
## <a name="see-also"></a><span data-ttu-id="5b08e-121">See Also</span><span class="sxs-lookup"><span data-stu-id="5b08e-121">See Also</span></span>

[<span data-ttu-id="5b08e-122">Testumgebungsanleitungen</span><span class="sxs-lookup"><span data-stu-id="5b08e-122">Test Lab Guides</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=202817)




