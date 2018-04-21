---
title: Testumgebungsanleitung Konfigurieren einer integrierten Exchange-, Lync- und SharePoint-Testumgebung
ms.author: jhendr
author: JoanneHendrickson
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 48e16935-3429-456a-8fe6-50afa257924c
description: 'Zusammenfassung: Erfahren Sie, wie Sie eine integrierte Testumgebung erstellen, in der ein Server mit Exchange Server 2013, ein Server mit Lync Server 2013 und ein Server mit SharePoint Server 2013 ausgeführt werden.'
ms.openlocfilehash: a15bdefe1749bca98933a8b9a4c4874130732eda
ms.sourcegitcommit: 8ff1cd7733dba438697b68f90189d4da72bbbefd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/20/2018
---
# <a name="test-lab-guide-configure-an-integrated-exchange-lync-and-sharepoint-test-lab"></a><span data-ttu-id="87ae0-103">Testumgebungsanleitung: Konfigurieren einer integrierten Exchange-, Lync- und SharePoint-Testumgebung</span><span class="sxs-lookup"><span data-stu-id="87ae0-103">Test Lab Guide: Configure an integrated Exchange, Lync, and SharePoint test lab</span></span>

 <span data-ttu-id="87ae0-104">**Zusammenfassung:** Erfahren Sie, wie Sie eine integrierte Testumgebung erstellen, in der ein Server mit Exchange Server 2013, ein Server mit Lync Server 2013 und ein Server mit SharePoint Server 2013 ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="87ae0-104">**Summary:** Learn how to create an integrated test lab that contains a server that runs Exchange Server 2013, a server that runs Lync Server 2013, and a server that runs SharePoint Server 2013.</span></span>
 
<span data-ttu-id="87ae0-105">**Ansehen des Videos zur Testumgebungsanleitung für Exchange, Lync und SharePoint**</span><span class="sxs-lookup"><span data-stu-id="87ae0-105">**Watch the integrated Exchange, Lync, and SharePoint test lab guide overview video**</span></span>

> [!VIDEO https://videoplayercdn.osi.office.net/hub/?csid=ux-cms-en-us-msoffice&uuid=8d1f00cc-b8b1-4394-9367-0cc9765e380a&AutoPlayVideo=false]
 
<span data-ttu-id="87ae0-106">Die Testumgebung, die aus dieser Konfiguration resultiert und die Server-zu-Server-Authentifizierung zwischen allen drei Servertypen vorsieht, kann verwendet werden, um Szenarien und Lösungen mit mehreren Produkten zu erstellen und zu veranschaulichen, in denen ein Server mit Exchange Server 2013, ein Server mit Lync Server 2013 und ein Server mit SharePoint Server 2013 ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="87ae0-106">The test lab that results from this configuration, which includes server-to-server authentication between all three types of servers, can be used to build out and demonstrate multi-product scenarios and solutions that use a server that runs Exchange Server 2013, a server that runs Lync Server 2013, and a server that runs SharePoint Server 2013.</span></span>
  
<span data-ttu-id="87ae0-107">Dieses Dokument enthält Anleitungen zu den folgenden Punkten:</span><span class="sxs-lookup"><span data-stu-id="87ae0-107">This document contains instructions for the following:</span></span>
  
1. <span data-ttu-id="87ae0-108">Konfigurieren der Testumgebung "Windows Server 2012-Basiskonfiguration"</span><span class="sxs-lookup"><span data-stu-id="87ae0-108">Configuring the Windows Server 2012 Base Configuration test lab.</span></span>
    
2. <span data-ttu-id="87ae0-109">Installieren und Konfigurieren des neuen Servers SQL1</span><span class="sxs-lookup"><span data-stu-id="87ae0-109">Installing and configuring a new server named SQL1.</span></span>
    
3. <span data-ttu-id="87ae0-110">Installieren von SQL Server 2012 auf dem Server SQL1</span><span class="sxs-lookup"><span data-stu-id="87ae0-110">Installing SQL Server 2012 on the SQL1 server.</span></span>
    
4. <span data-ttu-id="87ae0-111">Installieren und Konfigurieren eines neuen Clientcomputers mit dem Namen CLIENT2</span><span class="sxs-lookup"><span data-stu-id="87ae0-111">Installing and configuring a new client computer named CLIENT2.</span></span>
    
5. <span data-ttu-id="87ae0-112">Installieren und Konfigurieren von Exchange Server 2013 auf EX1</span><span class="sxs-lookup"><span data-stu-id="87ae0-112">Installing and configuring Exchange Server 2013 on EX1.</span></span>
    
6. <span data-ttu-id="87ae0-113">Installieren und Konfigurieren eines neuen Servers mit dem Namen LYNC1</span><span class="sxs-lookup"><span data-stu-id="87ae0-113">Installing and configuring a new server named LYNC1.</span></span>
    
7. <span data-ttu-id="87ae0-114">Installieren von Lync Server 2013 Standard Edition auf LYNC1</span><span class="sxs-lookup"><span data-stu-id="87ae0-114">Installing Lync Server 2013 Standard Edition on LYNC1.</span></span>
    
8. <span data-ttu-id="87ae0-115">Installieren von SharePoint Server 2013 auf SP1</span><span class="sxs-lookup"><span data-stu-id="87ae0-115">Installing SharePoint Server 2013 on SP1.</span></span>
    
9. <span data-ttu-id="87ae0-116">Konfigurieren der Integration zwischen EX1, LYNC1 und SP1</span><span class="sxs-lookup"><span data-stu-id="87ae0-116">Configuring integration between EX1, LYNC1, and SP1.</span></span>
    
<span data-ttu-id="87ae0-117">Weitere Informationen zum Konfigurieren dieser Testumgebung in Hyper-V finden Sie unter [Hosten der integrierten Exchange-, Lync- und SharePoint-Testumgebung mit Windows Server 2012 Hyper-V](https://social.technet.microsoft.com/wiki/contents/articles/18483.hosting-the-integrated-exchange-lync-and-sharepoint-test-lab-with-windows-server-2012-hyper-v.aspx).</span><span class="sxs-lookup"><span data-stu-id="87ae0-117">For information about how to configure this test lab in Hyper-V, see [Hosting the integrated Exchange, Lync, and SharePoint test lab with Windows Server 2012 Hyper-V](https://social.technet.microsoft.com/wiki/contents/articles/18483.hosting-the-integrated-exchange-lync-and-sharepoint-test-lab-with-windows-server-2012-hyper-v.aspx).</span></span>
  
## <a name="download-the-test-lab-guide"></a><span data-ttu-id="87ae0-118">Die Testumgebungsanleitung herunterladen</span><span class="sxs-lookup"><span data-stu-id="87ae0-118">Download the test lab guide</span></span>

<span data-ttu-id="87ae0-119">[Test Lab Guide: Konfigurieren einer integrierten Exchange, Lync und SharePoint-Testlabor](https://go.microsoft.com/fwlink/p/?LinkId=313670) (https://go.microsoft.com/fwlink/p/?LinkId=313670)</span><span class="sxs-lookup"><span data-stu-id="87ae0-119">[Test Lab Guide: Configure an Integrated Exchange, Lync, and SharePoint Test Lab](https://go.microsoft.com/fwlink/p/?LinkId=313670) (https://go.microsoft.com/fwlink/p/?LinkId=313670)</span></span>
  
## <a name="see-also"></a><span data-ttu-id="87ae0-120">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="87ae0-120">See Also</span></span>

[<span data-ttu-id="87ae0-121">Testumgebungsanleitungen</span><span class="sxs-lookup"><span data-stu-id="87ae0-121">Test Lab Guides</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=202817)




