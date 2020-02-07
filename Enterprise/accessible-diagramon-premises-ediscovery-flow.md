---
title: Zugängliches Diagramm – Lokaler eDiscovery-Datenfluss
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: b9dcd692-0485-4eec-870d-87ab6b89d97b
f1.keywords:
- NOCSH
description: Dieser Artikel ist eine barrierefreie Textversion des Diagramms „Lokaler eDiscovery-Datenfluss“.
ms.openlocfilehash: ec9ecf7d3663503f2da412364d919a6c70032e23
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/07/2020
ms.locfileid: "41843856"
---
# <a name="accessible-diagram---on-premises-ediscovery-flow"></a><span data-ttu-id="b812a-103">Zugängliches Diagramm – Lokaler eDiscovery-Datenfluss</span><span class="sxs-lookup"><span data-stu-id="b812a-103">Accessible diagram - On-premises eDiscovery Flow</span></span>

<span data-ttu-id="b812a-104">**Zusammenfassung:** Dieser Artikel ist eine barrierefreie Textversion des Diagramms mit dem Namen "lokaler eDiscovery-Fluss".</span><span class="sxs-lookup"><span data-stu-id="b812a-104">**Summary:** This article is an accessible text version of the diagram named On-premises eDiscovery Flow.</span></span>
  
<span data-ttu-id="b812a-105">Dieses Poster bietet Details zu Architektur und Datenfluss bei Serverprodukten.</span><span class="sxs-lookup"><span data-stu-id="b812a-105">This poster provides details about the architecture and flow of data across server products.</span></span> 
  
## <a name="across-sharepoint-exchange-lync-and-file-shares"></a><span data-ttu-id="b812a-106">SharePoint, Exchange, Lync und Dateifreigaben</span><span class="sxs-lookup"><span data-stu-id="b812a-106">Across SharePoint, Exchange, Lync, and file shares</span></span>

<span data-ttu-id="b812a-107">Das Diagramm zeigt einen Benutzer, der eine Abfrage sendet, die auf zwei Serverfarmen, eine SharePoint 2013 Enterprise-App-Farm und eine SharePoint 2013-Dienstfarm zugreift.</span><span class="sxs-lookup"><span data-stu-id="b812a-107">The diagram shows a user sending a query that accesses two server farms, a SharePoint 2013 Enterprise App Farm, and a SharePoint 2013 Services Farm.</span></span> <span data-ttu-id="b812a-108">Die Farm mit SharePoint 2013 Diensten kommuniziert mit einer SharePoint 2013-Inhaltsfarm, Exchange Server 2013 (die mit lync 2013 kommuniziert) und Windows-Dateifreigaben.</span><span class="sxs-lookup"><span data-stu-id="b812a-108">The SharePoint 2013 Services Farm communicates with a SharePoint 2013 Content Farm, Exchange Server 2013 (which communicates with Lync 2013), and Windows File Shares.</span></span> 
  
<span data-ttu-id="b812a-109">In der eDiscovery-Ablaufliste werden der Datenfluss und die Reihenfolge beschrieben, in der Abfrageaktionen von eDiscovery in SharePoint, Exchange, Lync und Dateifreigaben erfolgen. </span><span class="sxs-lookup"><span data-stu-id="b812a-109">The eDiscovery Flow List describes the flow of data and the order in which eDisovery query actions occur across SharePoint, Exchange, Lync, and file shares.</span></span> 
  
<span data-ttu-id="b812a-110">Die eDiscovery-Ablaufliste wird zuerst detailliert beschrieben. Danach folgt eine detaillierte Beschreibung der im Diagramm abgebildeten Features. </span><span class="sxs-lookup"><span data-stu-id="b812a-110">The eDiscovery flow list is described in detail first, followed by a detailed description of the features depicted in the diagram.</span></span> 
  
### <a name="ediscovery-flow-list"></a><span data-ttu-id="b812a-111">eDiscovery-Ablaufliste</span><span class="sxs-lookup"><span data-stu-id="b812a-111">eDiscovery Flow List</span></span>

<span data-ttu-id="b812a-p102">Die Zahlen für die einzelnen in der Liste beschriebenen Schritte gehören zu einem im Diagramm abgebildeten Schritt. Das Diagramm wird weiter unten in diesem Dokument ausführlich beschrieben. </span><span class="sxs-lookup"><span data-stu-id="b812a-p102">The numbers for each of the steps described in this list pertain to a step depicted in the diagram. The diagram is described in detail later in this document.</span></span> 
  
1. <span data-ttu-id="b812a-114">eDiscovery-Fälle werden im eDiscovery Center (EDC) erstellt, verwaltet und verwendet.</span><span class="sxs-lookup"><span data-stu-id="b812a-114">eDiscovery cases are created, managed, and used in the eDiscovery center (EDC).</span></span> <span data-ttu-id="b812a-115">EDC ist eine SharePoint 2013 Websitesammlung.</span><span class="sxs-lookup"><span data-stu-id="b812a-115">The EDC is a SharePoint 2013 site collection.</span></span> <span data-ttu-id="b812a-116">Hier werden Fälle definiert, nachzuverfolgende Quellen bestimmt, Abfragen gestartet, Abfrageergebnisse geprüft und Sperren für Inhalte aktiviert oder aufgehoben.</span><span class="sxs-lookup"><span data-stu-id="b812a-116">This is where cases are defined, sources to be tracked are identified, queries are issued, query results are reviewed, and holds on content are placed or removed.</span></span> 
    
2. <span data-ttu-id="b812a-117">Die eDiscovery-Abfrage oder -Aktion, wie „Im Archiv platzieren“, „ReleaseHold“ oder „GetStatus“, wird vom EDC an den Proxy der Suchdienstanwendung (Search Service Application, SSA) in der App-Farm des Unternehmens weitergeleitet.</span><span class="sxs-lookup"><span data-stu-id="b812a-117">The eDiscovery query or action, such as place a Hold, ReleaseHold, or GetStatus, is relayed from the EDC to the Search Service Application (SSA) proxy in the Enterprise App Farm.</span></span> <span data-ttu-id="b812a-118">Der Proxy der Suchdienstanwendung leitet anschließend den Datenverkehr an die SSA in der Dienst-App-Farm weiter.</span><span class="sxs-lookup"><span data-stu-id="b812a-118">The SSA proxy then relays the traffic to the SSA in the Services App Farm.</span></span> <span data-ttu-id="b812a-119">In diesem Beispiel wird die Anforderung in der SharePoint-Inhalts Farm mit "Contoso" im Dateinamen in der Warteschleife platziert.</span><span class="sxs-lookup"><span data-stu-id="b812a-119">In this example, the request is to place anything in the SharePoint Content Farm with "CONTOSO" in the file name on hold.</span></span> 
    
3. <span data-ttu-id="b812a-p105">Wenn die Anforderung vorsieht, einen Fall abzufragen, konsultiert die Suchdienstanwendung den Suchindex. Dann wird das Resultset der eDiscovery-Abfrage über das EDC an den Benutzer zurückgegeben. </span><span class="sxs-lookup"><span data-stu-id="b812a-p105">If the request is to query a case, the SSA consults the search index. Then, the eDiscovery query result set returns to the user through the EDC.</span></span> 
    
4. <span data-ttu-id="b812a-122">Wenn die Anforderung eine Aktion ist, z. B. „Im Archiv platzieren“ oder „ReleaseHold“, wird diese Aktion in die Tabelle „Actions“ in der Verwaltungsdatenbank der Suchdienstanwendung geschrieben.</span><span class="sxs-lookup"><span data-stu-id="b812a-122">If the request is an action, such as place a Hold or ReleaseHold, that action is written to the Actions_Table in the SSA Administrative database.</span></span> <span data-ttu-id="b812a-123">In diesem Beispiel wird eine halte Anforderung für irgendetwas in der SharePoint-Inhalts Farm mit "Contoso" in die Actions_Table geschrieben.</span><span class="sxs-lookup"><span data-stu-id="b812a-123">In this example, a hold request for anything in the SharePoint Content Farm with "CONTOSO" is written to the Actions_Table.</span></span> 
    
5. <span data-ttu-id="b812a-124">In regelmäßigen Abständen wird der Zeitgeberauftrag für den eDiscovery-In-Situ-Speicher der Inhaltsfarm aktiviert, der eine Anforderung ausstehender Aktionen generiert und Statusaktualisierungen über den SSA-Proxy an die SSA sendet.</span><span class="sxs-lookup"><span data-stu-id="b812a-124">At regular intervals the Content Farm eDiscovery in-place hold timer job wakes up and generates a request for pending actions and sends status updates through the SSA proxy to the SSA.</span></span> 
    
6. <span data-ttu-id="b812a-125">Die Abfrage ausstehender Aktionen wird an die zentrale Suchdienstanwendung weitergeleitet, die die Tabelle „Actions“ auf ausstehende Aktionen für die Inhaltsfarm konsultiert.</span><span class="sxs-lookup"><span data-stu-id="b812a-125">The query for pending actions is relayed to the central SSA, which consults the Action_Table for any pending actions for the Content Farm.</span></span> <span data-ttu-id="b812a-126">Der Zeitgeberauftrag für den In-Situ-Speicher der Inhaltsfarm sendet außerdem Statusaktualisierungen für empfangene Objekte und Aktionen, die in die Tabelle „Actions“ geschrieben werden.</span><span class="sxs-lookup"><span data-stu-id="b812a-126">The Content Farm in-place hold timer job also sends status updates for objects and actions it has received, which are written to the ActionsTable.</span></span> 
    
7. <span data-ttu-id="b812a-127">Die halte Anforderung für alle Inhalte mit "Contoso" im Namen in der SharePoint 2013 Inhaltsfarm wird von der SSA an den Zeitgeberauftrag eDiscovery in der Inhaltsfarm gesendet.</span><span class="sxs-lookup"><span data-stu-id="b812a-127">The hold request for any content with "CONTOSO" in the name in the SharePoint 2013 Content Farm is sent by the SSA to the eDiscovery in-place hold timer job in the Content Farm.</span></span> 
    
8. <span data-ttu-id="b812a-128">Der Zeitgeberauftrag eDiscovery in-situ-Speicher platziert den "Contoso-Standort" und "Contoso-Inhalt" in der Warteschleife.</span><span class="sxs-lookup"><span data-stu-id="b812a-128">The eDiscovery in-place hold timer job places the "CONTOSO Site" and "CONTOSO content" on hold.</span></span> 
    
9. <span data-ttu-id="b812a-129">Der Zeitgeberauftrag für den eDiscovery-In-Situ-Speicher wird in der Unternehmens-App-Farm regelmäßig ausgeführt, um den Status von Ermittlungsaktionen zu prüfen und zu aktualisieren. </span><span class="sxs-lookup"><span data-stu-id="b812a-129">The eDiscovery in-place hold timer job periodically runs in the Enterprise App Farm to check the status of discovery actions and to update the status.</span></span> 
    
10. <span data-ttu-id="b812a-130">Die Statusabfrage wird über den Proxy der Suchdienstanwendung der Unternehmens-App-Farm an die Suchdienstanwendung der SharePoint Services-Farm weitergeleitet. </span><span class="sxs-lookup"><span data-stu-id="b812a-130">The status query is relayed through the Enterprise App Farm SSA proxy to the SharePoint Services Farm SSA.</span></span> 
    
11. <span data-ttu-id="b812a-131">Die Suchdienstanwendung ruft den Status der Tabelle „Actions“ ab und gibt ihn an den Zeitgeberauftrag in der Unternehmens-App-Farm zurück, die die Statusaktualisierungen per Push-Verfahren in das EDC überträgt.</span><span class="sxs-lookup"><span data-stu-id="b812a-131">The SSA retrieves the status from the Actions table and returns it to the timer job in the Enterprise App Farm, which pushes the status updates to the EDC.</span></span> 
    
12. <span data-ttu-id="b812a-132">Wenn der eDiscovery-Benutzer Exchange-Quellen durchsucht, z. B. ein Postfach oder archivierte Lync-Inhalte (oder eine Aktion darauf anwendet), verwendet die zentrale Suchdienstanwendung den Exchange-Webdienste-Proxy (Exchange Web Services, EWS) zum Abfragen von Exchange-Webdiensten.</span><span class="sxs-lookup"><span data-stu-id="b812a-132">When the eDiscovery user is searching (or performing an action) for Exchange sources, such as a mailbox or archived Lync content, the central SSA uses Exchange Web Services (EWS) proxy to query Exchange Web Services.</span></span> <span data-ttu-id="b812a-133">Exchange hat eine eigene Suchfunktion und eDiscovery-Infrastruktur und verwaltet alle eDiscovery-Aufrufe intern.</span><span class="sxs-lookup"><span data-stu-id="b812a-133">Exchange has its own search and eDiscovery infrastructure and manages all eDiscovery calls internally.</span></span> 
    
13. <span data-ttu-id="b812a-134">Exchange-Webdienste antwortet der Suchdienstanwendung mit eDiscovery-Suchergebnissen oder einer Antwort auf eine Statusanforderung eines abfragebasierten Archivs, das wiederum an das EDC weitergeleitet wird. </span><span class="sxs-lookup"><span data-stu-id="b812a-134">Exchange Web Services responds to SSA with eDiscovery search results or a response to a status request for a query-based hold, which, in turn, gets relayed to the EDC.</span></span> 
    
#### <a name="prerequisites"></a><span data-ttu-id="b812a-135">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="b812a-135">Prerequisites</span></span>

- <span data-ttu-id="b812a-136">Die SharePoint-Unternehmenssuche muss konfiguriert sein, Inhaltsquellen (SharePoint- und Windows-Dateifreigaben) müssen erfolgreich durchforstetet werden, und alle Inhaltsquellen müssen sich im Index befinden. </span><span class="sxs-lookup"><span data-stu-id="b812a-136">SharePoint Enterprise Search must be configured, search crawls on content sources (SharePoint and Windows file shares) are successfully occurring, and all content sources are in the index.</span></span> 
    
- <span data-ttu-id="b812a-137">Die Server-zu-Server-Vertrauensstellung und -Authentifizierung muss zwischen der SharePoint Services-Farm und Exchange sowie zwischen Exchange und Lync konfiguriert sein. </span><span class="sxs-lookup"><span data-stu-id="b812a-137">Server-to-server trust and authentication must be configured between the SharePoint Services Farm and Exchange and also between Exchange and Lync.</span></span> 
    
### <a name="description-of-components-in-the-diagram"></a><span data-ttu-id="b812a-138">Beschreibung der im Diagramm dargestellten Komponenten</span><span class="sxs-lookup"><span data-stu-id="b812a-138">Description of components in the diagram</span></span>

<span data-ttu-id="b812a-139">Das Diagramm zeigt einen Benutzer, der eine Abfrage sendet, die auf zwei Serverfarmen, eine SharePoint 2013 Enterprise-App-Farm und eine SharePoint 2013-Dienstfarm zugreift.</span><span class="sxs-lookup"><span data-stu-id="b812a-139">The diagram shows a user sending a query, which accesses two server farms, a SharePoint 2013 Enterprise App Farm and a SharePoint 2013 Services Farm.</span></span> <span data-ttu-id="b812a-140">Die SharePoint Services-Farm Schnittstellen mit einer SharePoint 2013-Inhaltsfarm, Exchange Server 2013 (die Schnittstellen mit lync 2013) und Windows-Dateifreigaben.</span><span class="sxs-lookup"><span data-stu-id="b812a-140">The SharePoint Services Farm interfaces with a SharePoint 2013 Content Farm, Exchange Server 2013 (which interfaces with Lync 2013), and Windows File Shares.</span></span> 
  
#### <a name="sharepoint-2013-enterprise-app-farm"></a><span data-ttu-id="b812a-141">SharePoint 2013 Enterprise-App-Farm</span><span class="sxs-lookup"><span data-stu-id="b812a-141">SharePoint 2013 Enterprise App Farm</span></span>

<span data-ttu-id="b812a-142">Die SharePoint 2013 Enterprise-App-Farm enthält die folgenden Komponenten:</span><span class="sxs-lookup"><span data-stu-id="b812a-142">The SharePoint 2013 Enterprise App Farm contains the following components:</span></span> 
  
- <span data-ttu-id="b812a-143">EDC</span><span class="sxs-lookup"><span data-stu-id="b812a-143">EDC</span></span>
    
- <span data-ttu-id="b812a-144">SSA-Proxy </span><span class="sxs-lookup"><span data-stu-id="b812a-144">SSA proxy</span></span> 
    
- <span data-ttu-id="b812a-145">Zeitgeberauftrag</span><span class="sxs-lookup"><span data-stu-id="b812a-145">Timer job</span></span> 
    
<span data-ttu-id="b812a-p110">Eine Abfrage oder eine Aktion, die vom Benutzer gesendet wird, wird an das EDC in der Unternehmens-App-Farm gesendet. Es geschieht Folgendes: </span><span class="sxs-lookup"><span data-stu-id="b812a-p110">A query or action sent by the user is sent to the EDC in the Enterprise App Farm. The following actions occur:</span></span> 
  
- <span data-ttu-id="b812a-148">Die Abfrage oder die Aktion wird an den SSA-Proxy übermittelt. </span><span class="sxs-lookup"><span data-stu-id="b812a-148">The query or action goes to the SSA proxy.</span></span> 
    
- <span data-ttu-id="b812a-p111">Der SSA-Proxy sendet eine Statusabfrage oder -antwort an den Zeitgeberauftrag in der Unternehmens-App-Farm. Zudem sendet er eine Statusabfrage oder -antwort an den SSA-Dienst in der SharePoint Services-Farm. Die Aktionen, die sich hieraus ergeben, werden im Abschnitt über die SharePoint Services-Farm beschrieben. </span><span class="sxs-lookup"><span data-stu-id="b812a-p111">The SSA proxy sends a status query or response to the Timer job in the Enterprise App Farm, and it also sends a status query or response to the SSA service in the SharePoint Services Farm. The actions that result from this are described in the section about the SharePoint Services Farm.</span></span> 
    
- <span data-ttu-id="b812a-151">Wenn der Zeitgeberauftrag eine Antwort erhält, sendet er diese an den SSA-Proxy und das EDC. </span><span class="sxs-lookup"><span data-stu-id="b812a-151">When it receives a response, the Timer job sends the response to the SSA proxy and to the EDC.</span></span> 
    
- <span data-ttu-id="b812a-152">Ergebnisse der Abfrage oder Aktion werden aus dem EDC an den Benutzer gesendet. </span><span class="sxs-lookup"><span data-stu-id="b812a-152">Any results from the query or action are sent to the user from the EDC.</span></span> 
    
#### <a name="sharepoint-2013-services-farm"></a><span data-ttu-id="b812a-153">SharePoint 2013-Dienst Farm</span><span class="sxs-lookup"><span data-stu-id="b812a-153">SharePoint 2013 Services Farm</span></span>

<span data-ttu-id="b812a-154">Die SharePoint 2013-Dienste-Farm enthält die folgenden Komponenten:</span><span class="sxs-lookup"><span data-stu-id="b812a-154">The SharePoint 2013 Services Farm contains the following components:</span></span> 
  
- <span data-ttu-id="b812a-155">SSA-Dienst </span><span class="sxs-lookup"><span data-stu-id="b812a-155">SSA Service</span></span> 
    
- <span data-ttu-id="b812a-156">Suchindexdatenbank</span><span class="sxs-lookup"><span data-stu-id="b812a-156">Search index database</span></span> 
    
- <span data-ttu-id="b812a-157">Verwaltungsdatenbank der Suchdienstanwendung.</span><span class="sxs-lookup"><span data-stu-id="b812a-157">SSA admin_db database.</span></span> <span data-ttu-id="b812a-158">Die Tabelle „Actions“ in dieser Datenbank enthält: Archiv, ReleaseHold, GetStatus</span><span class="sxs-lookup"><span data-stu-id="b812a-158">The Actions Table in this database contains: Hold Release Hold GetStatus</span></span> 
    
- <span data-ttu-id="b812a-159">EWS-Proxy </span><span class="sxs-lookup"><span data-stu-id="b812a-159">EWS proxy</span></span> 
    
<span data-ttu-id="b812a-160">Wenn der SSA-Proxy in der SharePoint-Unternehmens-App-Farm eine Statusabfrage an die SSA in der SharePoint Services-Farm sendet, geschieht Folgendes: </span><span class="sxs-lookup"><span data-stu-id="b812a-160">When the SSA proxy in the SharePoint Enterprise App Farm sends a status query to the SSA in the SharePoint Services Farm, the following actions occur:</span></span> 
  
- <span data-ttu-id="b812a-p113">Wenn die Anforderung eine Abfrage ist, konsultiert die Suchdienstanwendung den Suchindex. Die Antwort der Ermittlung wird an die SSA und dann über das EDC an den Benutzer zurückgegeben. </span><span class="sxs-lookup"><span data-stu-id="b812a-p113">If the request is a query, the SSA consults the search index. The discovery response is returned to the SSA and then to the user through the EDC.</span></span> 
    
- <span data-ttu-id="b812a-163">Wenn die Anforderung eine Schreibaktion ist, sendet der SSA-Dienst die Schreibaktion an die Verwaltungsdatenbank der Suchdienstanwendung. </span><span class="sxs-lookup"><span data-stu-id="b812a-163">If the request is a write action, the SSA service sends the write action to the SSA admin_db.</span></span> 
    
- <span data-ttu-id="b812a-164">Eine Durchforstungs-und Antwortergebnis Anforderung wird von der SSA an die SharePoint 2013-Inhalts Farm gesendet, und eine Antwort wird an die SSA zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="b812a-164">A crawl and responding results request is sent from the SSA to the SharePoint 2013 Content Farm and a response is returned to the SSA.</span></span> 
    
- <span data-ttu-id="b812a-165">Eine Anforderung für Durchforstung und Antwortergebnisse wird von der SSA an die Windows-Dateifreigaben gesendet, und eine Antwort wird an die SSA zurückgegeben. </span><span class="sxs-lookup"><span data-stu-id="b812a-165">A crawl and responding results request is sent from the SSA to the Windows File Shares, and a response is returned to the SSA.</span></span> 
    
- <span data-ttu-id="b812a-166">Eine Abfrage für ausstehenden Aktion(en), Antworten oder Statusaktualisierungen wird von der SSA an den SSA-Proxy in der SharePoint-Inhaltsfarm gesendet, und eine Antwort wird an die SSA zurückgegeben. </span><span class="sxs-lookup"><span data-stu-id="b812a-166">A query for pending action(s), responses, or status updates is sent from the SSA to the SSA proxy in the SharePoint Content Farm, and a response is returned to the SSA.</span></span> 
    
- <span data-ttu-id="b812a-167">Eine Aktions-/Statusanforderung von Exchange wird von der SSA an den EWS-Proxy gesendet, der eine Aktions-/Statusanforderung für eine Exchange-Abfrage an den Exchange-Webdienst auf dem Exchange 2013-Server sendet.  </span><span class="sxs-lookup"><span data-stu-id="b812a-167">An Exchange action/status request is sent from the SSA to the EWS proxy, which sends an Exchange Query action/status request to the Exchange Web Service on the Exchange 2013 server.</span></span> 
    
- <span data-ttu-id="b812a-168">Eine Statusabfrage/-antwort wird von der SSA an die Verwaltungsdatenbank der Suchdienstanwendung gesendet und an die SSA zurückgegeben. </span><span class="sxs-lookup"><span data-stu-id="b812a-168">A status query/response is sent from the SSA to the SSA admin_db and is returned to the SSA.</span></span> 
    
- <span data-ttu-id="b812a-169">Eine Abfrage/Antwort für eine ausstehende Aktion wird von der SSA an die Verwaltungsdatenbank der Suchdienstanwendung gesendet und an die SSA zurückgegeben. </span><span class="sxs-lookup"><span data-stu-id="b812a-169">A pending action query/response is sent from the SSA to the SSA admin_db and is returned to the SSA.</span></span> 
    
#### <a name="sharepoint-2013-content-farm"></a><span data-ttu-id="b812a-170">SharePoint 2013 Inhalts Farm</span><span class="sxs-lookup"><span data-stu-id="b812a-170">SharePoint 2013 Content Farm</span></span>

<span data-ttu-id="b812a-171">Die SharePoint 2013 Inhalts Farm enthält die folgenden Komponenten:</span><span class="sxs-lookup"><span data-stu-id="b812a-171">The SharePoint 2013 Content Farm contains the following components:</span></span> 
  
- <span data-ttu-id="b812a-172">SSA-Proxy </span><span class="sxs-lookup"><span data-stu-id="b812a-172">SSA proxy</span></span> 
    
- <span data-ttu-id="b812a-173">Zeitgeberauftrag</span><span class="sxs-lookup"><span data-stu-id="b812a-173">Timer job</span></span> 
    
- <span data-ttu-id="b812a-174">Contoso SharePoint-Website </span><span class="sxs-lookup"><span data-stu-id="b812a-174">Contoso SharePoint site</span></span> 
    
- <span data-ttu-id="b812a-175">Contoso SharePoint-Inhalte </span><span class="sxs-lookup"><span data-stu-id="b812a-175">Contoso SharePoint content</span></span> 
    
<span data-ttu-id="b812a-176">Wenn die SSA in der SharePoint Services-Farm eine Statusabfrage an den SSA-Proxy in der SharePoint-Inhaltsfarm sendet, geschieht Folgendes: </span><span class="sxs-lookup"><span data-stu-id="b812a-176">When the SSA in the SharePoint Services Farm sends a status query to the SSA Proxy in the SharePoint Content Farm, the following actions occur:</span></span> 
  
- <span data-ttu-id="b812a-177">Der SSA-Proxy in der SharePoint-Inhaltsfarm sendet eine Abfrage für ausstehende Aktionen/Statusantwort an den Zeitgeberauftrag. </span><span class="sxs-lookup"><span data-stu-id="b812a-177">The SSA proxy in the SharePoint Content Farm sends a query for pending actions/status response to the Timer job.</span></span> 
    
- <span data-ttu-id="b812a-178">Der Zeitgeberauftrag sendet eine Anforderung an die Contoso SharePoint-Website, die die Contoso SharePoint-Inhalte überprüft. </span><span class="sxs-lookup"><span data-stu-id="b812a-178">The Timer job sends a request to the Contoso SharePoint site, which reviews the Contoso SharePoint content.</span></span> 
    
- <span data-ttu-id="b812a-179">Die Antwort auf die Abfrage der ausstehenden Aktionen/Statusabfrage wird von dem Zeitgeberauftrag an den SSA-Proxy in der SharePoint-Inhaltsfarm gesendet. Anschließend wird sie an den SSA-Dienst in der SharePoint Services-Farm gesendet. </span><span class="sxs-lookup"><span data-stu-id="b812a-179">The response to the pending actions/status query is sent from the Timer job to the SSA proxy in the SharePoint Content Farm, and then it is sent to the SSA service in the SharePoint Services Farm</span></span> 
    
#### <a name="exchange-2013"></a><span data-ttu-id="b812a-180">Exchange 2013</span><span class="sxs-lookup"><span data-stu-id="b812a-180">Exchange 2013</span></span>

<span data-ttu-id="b812a-181">Die Exchange 2013-Serverkomponente enthält den Exchange-Webdienst und bietet Folgendes: </span><span class="sxs-lookup"><span data-stu-id="b812a-181">The Exchange 2013 server component contains the Exchange Web Service and provides the following:</span></span> 
  
- <span data-ttu-id="b812a-182">Die Server-zu-Server-Vertrauensstellung/OAuth wird zwischen der SharePoint 2013-Inhalts Farm und Exchange 2013 behandelt.</span><span class="sxs-lookup"><span data-stu-id="b812a-182">Server-to-server Trust/OAuth is handled between the SharePoint 2013 Content Farm and Exchange 2013.</span></span> 
    
- <span data-ttu-id="b812a-183">Server-zu-Server-Vertrauensstellung/OAuth erfolgt zwischen Exchange 2013 und Lync 2013. </span><span class="sxs-lookup"><span data-stu-id="b812a-183">Server-to-server Trust/OAuth is handled between Exchange 2013 and Lync 2013.</span></span> 
    
#### <a name="lync-2013"></a><span data-ttu-id="b812a-184">Lync 2013</span><span class="sxs-lookup"><span data-stu-id="b812a-184">Lync 2013</span></span>

<span data-ttu-id="b812a-185">Die Lync 2013-Komponente archiviert Lync-Inhalte in Exchange 2013. </span><span class="sxs-lookup"><span data-stu-id="b812a-185">The Lync 2013 component archives Lync content in Exchange 2013.</span></span> 
  
#### <a name="windows-file-shares"></a><span data-ttu-id="b812a-186">Windows-Dateifreigaben</span><span class="sxs-lookup"><span data-stu-id="b812a-186">Windows File Shares</span></span>

<span data-ttu-id="b812a-187">Die Windows-Dateifreigaben-Komponente stellt Durchforstungsergebnisse für die SSA in der SharePoint Services-Farm bereit. </span><span class="sxs-lookup"><span data-stu-id="b812a-187">The Windows File Shares component provides crawl results to the SSA in the SharePoint Services Farm.</span></span> 
  
### <a name="legend"></a><span data-ttu-id="b812a-188">Legende</span><span class="sxs-lookup"><span data-stu-id="b812a-188">Legend</span></span>

<span data-ttu-id="b812a-189">Die Legende für dieses Diagramm enthält eine grafische Darstellung der verschiedenen zwischen den Komponenten gezeigten Datenverkehrstypen in Form verschiedenfarbiger Linien, wie nachfolgend beschrieben: </span><span class="sxs-lookup"><span data-stu-id="b812a-189">The legend for this diagram graphically shows the different types of traffic depicted among the components in different colored lines as follows:</span></span> 
  
- <span data-ttu-id="b812a-190">Hellblaue Verbindung: Abfrage/Aktion – eDiscovery-Abfrage oder Aktionsdaten</span><span class="sxs-lookup"><span data-stu-id="b812a-190">Light blue line: Query/action - eDiscovery query or action data</span></span> 
    
- <span data-ttu-id="b812a-191">Orangefarbener Anschluss: eDiscovery-Antwort – Daten zur eDiscovery-Abfrageantwort</span><span class="sxs-lookup"><span data-stu-id="b812a-191">Orange line: eDisovery response - eDiscovery query response data</span></span> 
    
- <span data-ttu-id="b812a-192">Grüne Reihe: Statusabfrage/-Antwort – eDiscovery-Statusabfrage/Antwortdaten</span><span class="sxs-lookup"><span data-stu-id="b812a-192">Green line: Status query/response - eDiscovery status query/response data</span></span> 
    
- <span data-ttu-id="b812a-193">Purple-Reihe: Exchange-Aktion/Statusanforderung – eDiscovery-Anforderung für den Aktionsstatus für Exchange-Datenverkehr.</span><span class="sxs-lookup"><span data-stu-id="b812a-193">Purple line: Exchange action/status request - eDiscovery request for action status for Exchange traffic.</span></span> 
    
- <span data-ttu-id="b812a-194">Rote Schnur: Exchange-Daten/Statusantwort – eDiscovery-Abfrage oder Statusantwort von Exchange.</span><span class="sxs-lookup"><span data-stu-id="b812a-194">Red line: Exchange data/status response - eDiscovery query or status response from Exchange.</span></span> 
    
- <span data-ttu-id="b812a-195">Gepunktete schwarze Linie: Server-zu-Server-Vertrauensstellung/OAuth </span><span class="sxs-lookup"><span data-stu-id="b812a-195">Dotted black line: Server-to-Server Trust/Oauth</span></span> 
    
- <span data-ttu-id="b812a-196">Durchgezogene schwarze Linie: Durchforstung/Ergebnisse </span><span class="sxs-lookup"><span data-stu-id="b812a-196">Solid black line: Crawl/results</span></span> 
    

