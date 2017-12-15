---
title: "Zugängliches Diagramm – Lokaler eDiscovery-Datenfluss"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: b9dcd692-0485-4eec-870d-87ab6b89d97b
description: "Dieser Artikel ist eine barrierefreie Textversion des Diagramms „Lokaler eDiscovery-Datenfluss“."
ms.openlocfilehash: de94fc2af94df47a83f4a7847a84cd18131f637e
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2017
---
# <a name="accessible-diagram---on-premises-ediscovery-flow"></a><span data-ttu-id="80148-103">Zugängliches Diagramm – Lokaler eDiscovery-Datenfluss</span><span class="sxs-lookup"><span data-stu-id="80148-103">Accessible diagram - On-premises eDiscovery Flow</span></span>

<span data-ttu-id="80148-104">**Zusammenfassung:** Dieser Artikel ist eine Version verfügbaren Text des Diagramms mit dem Namen der lokale eDiscovery Flow.</span><span class="sxs-lookup"><span data-stu-id="80148-104">**Summary:** This article is an accessible text version of the diagram named On-premises eDiscovery Flow.</span></span>
  
<span data-ttu-id="80148-105">Dieses Poster bietet Details zu Architektur und Datenfluss bei Serverprodukten.</span><span class="sxs-lookup"><span data-stu-id="80148-105">This poster provides details about the architecture and flow of data across server products.</span></span> 
  
## <a name="across-sharepoint-exchange-lync-and-file-shares"></a><span data-ttu-id="80148-106">SharePoint, Exchange, Lync und Dateifreigaben</span><span class="sxs-lookup"><span data-stu-id="80148-106">Across SharePoint, Exchange, Lync, and file shares</span></span>

<span data-ttu-id="80148-p101">Das Diagramm zeigt die einen Benutzer sendet eine Abfrage, die auf zwei Serverfarmen, einer SharePoint 2013 Enterprise-App-Farm und einer SharePoint 2013-Dienstfarm zugreift. SharePoint 2013-Services-Farm kommuniziert mit einer SharePoint 2013-Inhalt Farm, Exchange Server 2013 (die mit Lync 2013 kommuniziert), und Windows-Dateifreigaben.</span><span class="sxs-lookup"><span data-stu-id="80148-p101">The diagram shows a user sending a query that accesses two server farms, a SharePoint 2013 Enterprise App Farm, and a SharePoint 2013 Services Farm. The SharePoint 2013 Services Farm communicates with a SharePoint 2013 Content Farm, Exchange Server 2013 (which communicates with Lync 2013), and Windows File Shares.</span></span> 
  
<span data-ttu-id="80148-109">In der eDiscovery-Ablaufliste werden der Datenfluss und die Reihenfolge beschrieben, in der Abfrageaktionen von eDiscovery in SharePoint, Exchange, Lync und Dateifreigaben erfolgen. </span><span class="sxs-lookup"><span data-stu-id="80148-109">The eDiscovery Flow List describes the flow of data and the order in which eDisovery query actions occur across SharePoint, Exchange, Lync, and file shares.</span></span> 
  
<span data-ttu-id="80148-110">Die eDiscovery-Ablaufliste wird zuerst detailliert beschrieben. Danach folgt eine detaillierte Beschreibung der im Diagramm abgebildeten Features. </span><span class="sxs-lookup"><span data-stu-id="80148-110">The eDiscovery flow list is described in detail first, followed by a detailed description of the features depicted in the diagram.</span></span> 
  
### <a name="ediscovery-flow-list"></a><span data-ttu-id="80148-111">eDiscovery-Ablaufliste</span><span class="sxs-lookup"><span data-stu-id="80148-111">eDiscovery Flow List</span></span>

<span data-ttu-id="80148-p102">Die Zahlen für die einzelnen in der Liste beschriebenen Schritte gehören zu einem im Diagramm abgebildeten Schritt. Das Diagramm wird weiter unten in diesem Dokument ausführlich beschrieben. </span><span class="sxs-lookup"><span data-stu-id="80148-p102">The numbers for each of the steps described in this list pertain to a step depicted in the diagram. The diagram is described in detail later in this document.</span></span> 
  
1. <span data-ttu-id="80148-p103">eDiscovery-Fälle werden erstellt, verwaltet und in das eDiscovery Center (EDC) verwendet. Das EDC ist eine SharePoint 2013-Websitesammlung. Dies ist, in dem Fällen definiert sind, Quellen nachverfolgt werden erkannt werden, Abfragen werden ausgegeben, Abfrageergebnisse werden überprüft und Haltebereiche auf Inhalt platziert oder entfernt werden.</span><span class="sxs-lookup"><span data-stu-id="80148-p103">eDiscovery cases are created, managed, and used in the eDiscovery center (EDC). The EDC is a SharePoint 2013 site collection. This is where cases are defined, sources to be tracked are identified, queries are issued, query results are reviewed, and holds on content are placed or removed.</span></span> 
    
2. <span data-ttu-id="80148-p104">Die eDiscovery-Abfrage oder eine Aktion wie etwa Ort einer Warteschleife, ReleaseHold oder GetStatus, wird an den Proxy (Search Service Application, SSA) in der Enterprise-App-Farm aus der EDC weitergeleitet. Der SSA Proxy leitet dann den Datenverkehr, der die SSA in der App-Services-Farm weiter. In diesem Beispiel wird in den Dateinamen in der Warteschleife Anforderung alles in der SharePoint-Inhaltsfarm mit "CONTOSO" platziert ist.</span><span class="sxs-lookup"><span data-stu-id="80148-p104">The eDiscovery query or action, such as place a Hold, ReleaseHold, or GetStatus, is relayed from the EDC to the Search Service Application (SSA) proxy in the Enterprise App Farm. The SSA proxy then relays the traffic to the SSA in the Services App Farm. In this example, the request is to place anything in the SharePoint Content Farm with "CONTOSO" in the file name on hold.</span></span> 
    
3. <span data-ttu-id="80148-p105">Wenn die Anforderung vorsieht, einen Fall abzufragen, konsultiert die Suchdienstanwendung den Suchindex. Dann wird das Resultset der eDiscovery-Abfrage über das EDC an den Benutzer zurückgegeben. </span><span class="sxs-lookup"><span data-stu-id="80148-p105">If the request is to query a case, the SSA consults the search index. Then, the eDiscovery query result set returns to the user through the EDC.</span></span> 
    
4. <span data-ttu-id="80148-p106">Wenn die Anforderung einer Aktion wie etwa eine Warteschleife oder ReleaseHold, Ort ist wird diese Aktion in der Actions_Table in der administrativen SSA Datenbank geschrieben. In diesem Beispiel wird eine Anforderung Haltestatus für alle in der SharePoint-Inhaltsfarm mit "CONTOSO" in die Actions_Table geschrieben.</span><span class="sxs-lookup"><span data-stu-id="80148-p106">If the request is an action, such as place a Hold or ReleaseHold, that action is written to the Actions_Table in the SSA Administrative database. In this example, a hold request for anything in the SharePoint Content Farm with "CONTOSO" is written to the Actions_Table.</span></span> 
    
5. <span data-ttu-id="80148-124">In regelmäßigen Abständen wird der Zeitgeberauftrag für den eDiscovery-In-Situ-Speicher der Inhaltsfarm aktiviert, der eine Anforderung ausstehender Aktionen generiert und Statusaktualisierungen über den SSA-Proxy an die SSA sendet. </span><span class="sxs-lookup"><span data-stu-id="80148-124">At regular intervals the Content Farm eDiscovery in-place hold timer job wakes up and generates a request for pending actions and sends status updates through the SSA proxy to the SSA.</span></span> 
    
6. <span data-ttu-id="80148-p107">Die Abfrage für Ausstehende Aktionen ist an der zentralen SSA weitergeleitet, die die Action_Table für alle ausstehenden Aktionen für die Inhaltsfarm konsultiert. Der Inhaltsfarm Compliance-Archiv-Zeitgeberauftrag sendet auch statusaktualisierungen für Objekte und Aktionen, die sie erhalten hat, die in die ActionsTable geschrieben werden.</span><span class="sxs-lookup"><span data-stu-id="80148-p107">The query for pending actions is relayed to the central SSA, which consults the Action_Table for any pending actions for the Content Farm. The Content Farm in-place hold timer job also sends status updates for objects and actions it has received, which are written to the ActionsTable.</span></span> 
    
7. <span data-ttu-id="80148-127">Die Anforderung Haltestatus für alle Inhalte mit "CONTOSO" in den Namen in der SharePoint 2013 Inhalte Farm wird durch die SSA an den eDiscovery-Compliance-Archiv-Zeitgeberauftrag in der Farm Inhalte gesendet.</span><span class="sxs-lookup"><span data-stu-id="80148-127">The hold request for any content with "CONTOSO" in the name in the SharePoint 2013 Content Farm is sent by the SSA to the eDiscovery in-place hold timer job in the Content Farm.</span></span> 
    
8. <span data-ttu-id="80148-128">Die eDiscovery-Compliance-Archiv Timer Job-Orte, halten Sie die "CONTOSO-Website" und "CONTOSO Content" auf.</span><span class="sxs-lookup"><span data-stu-id="80148-128">The eDiscovery in-place hold timer job places the "CONTOSO Site" and "CONTOSO content" on hold.</span></span> 
    
9. <span data-ttu-id="80148-129">Der Zeitgeberauftrag für den eDiscovery-In-Situ-Speicher wird in der Unternehmens-App-Farm regelmäßig ausgeführt, um den Status von Ermittlungsaktionen zu prüfen und zu aktualisieren. </span><span class="sxs-lookup"><span data-stu-id="80148-129">The eDiscovery in-place hold timer job periodically runs in the Enterprise App Farm to check the status of discovery actions and to update the status.</span></span> 
    
10. <span data-ttu-id="80148-130">Die Statusabfrage wird über den Proxy der Suchdienstanwendung der Unternehmens-App-Farm an die Suchdienstanwendung der SharePoint Services-Farm weitergeleitet. </span><span class="sxs-lookup"><span data-stu-id="80148-130">The status query is relayed through the Enterprise App Farm SSA proxy to the SharePoint Services Farm SSA.</span></span> 
    
11. <span data-ttu-id="80148-131">Die Suchdienstanwendung ruft den Status der Tabelle „Actions“ ab und gibt ihn an den Zeitgeberauftrag in der Unternehmens-App-Farm zurück, die die Statusaktualisierungen per Push-Verfahren in das EDC überträgt. </span><span class="sxs-lookup"><span data-stu-id="80148-131">The SSA retrieves the status from the Actions table and returns it to the timer job in the Enterprise App Farm, which pushes the status updates to the EDC.</span></span> 
    
12. <span data-ttu-id="80148-p108">Wenn ist der Benutzer eDiscovery-Suche (oder Ausführen einer Aktion) für Exchange-Quellen, wie ein Postfach oder archivierten Lync-Inhalten, die Zentraladministration SSA Proxy Abfrage Exchange-Webdienste (Exchange Web Services, EWS) verwendet. Exchange verfügt über eine eigene Such- und eDiscovery-Infrastruktur und alle eDiscovery Anrufe intern verwaltet.</span><span class="sxs-lookup"><span data-stu-id="80148-p108">When the eDiscovery user is searching (or performing an action) for Exchange sources, such as a mailbox or archived Lync content, the central SSA uses Exchange Web Services (EWS) proxy to query Exchange Web Services. Exchange has its own search and eDiscovery infrastructure and manages all eDiscovery calls internally.</span></span> 
    
13. <span data-ttu-id="80148-134">Exchange-Webdienste antwortet der Suchdienstanwendung mit eDiscovery-Suchergebnissen oder einer Antwort auf eine Statusanforderung eines abfragebasierten Archivs, das wiederum an das EDC weitergeleitet wird. </span><span class="sxs-lookup"><span data-stu-id="80148-134">Exchange Web Services responds to SSA with eDiscovery search results or a response to a status request for a query-based hold, which, in turn, gets relayed to the EDC.</span></span> 
    
#### <a name="prerequisites"></a><span data-ttu-id="80148-135">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="80148-135">Prerequisites</span></span>

- <span data-ttu-id="80148-136">Die SharePoint-Unternehmenssuche muss konfiguriert sein, Inhaltsquellen (SharePoint- und Windows-Dateifreigaben) müssen erfolgreich durchforstetet werden, und alle Inhaltsquellen müssen sich im Index befinden. </span><span class="sxs-lookup"><span data-stu-id="80148-136">SharePoint Enterprise Search must be configured, search crawls on content sources (SharePoint and Windows file shares) are successfully occurring, and all content sources are in the index.</span></span> 
    
- <span data-ttu-id="80148-137">Die Server-zu-Server-Vertrauensstellung und -Authentifizierung muss zwischen der SharePoint Services-Farm und Exchange sowie zwischen Exchange und Lync konfiguriert sein. </span><span class="sxs-lookup"><span data-stu-id="80148-137">Server-to-server trust and authentication must be configured between the SharePoint Services Farm and Exchange and also between Exchange and Lync.</span></span> 
    
### <a name="description-of-components-in-the-diagram"></a><span data-ttu-id="80148-138">Beschreibung der im Diagramm dargestellten Komponenten</span><span class="sxs-lookup"><span data-stu-id="80148-138">Description of components in the diagram</span></span>

<span data-ttu-id="80148-p109">Das Diagramm zeigt einen Benutzer eine Abfrage, wodurch greift auf zwei Serverfarmen einer SharePoint 2013 Enterprise-App-Farm und einer SharePoint 2013-Dienstfarm senden. Der SharePoint Services-Farm mit einer SharePoint 2013 Inhalte Farm Exchange Server 2013 (welche mit Lync 2013 Schnittstellen), Schnittstellen und Windows-Dateifreigaben.</span><span class="sxs-lookup"><span data-stu-id="80148-p109">The diagram shows a user sending a query, which accesses two server farms, a SharePoint 2013 Enterprise App Farm and a SharePoint 2013 Services Farm. The SharePoint Services Farm interfaces with a SharePoint 2013 Content Farm, Exchange Server 2013 (which interfaces with Lync 2013), and Windows File Shares.</span></span> 
  
#### <a name="sharepoint-2013-enterprise-app-farm"></a><span data-ttu-id="80148-141">SharePoint 2013 Enterprise-App-Farm</span><span class="sxs-lookup"><span data-stu-id="80148-141">SharePoint 2013 Enterprise App Farm</span></span>

<span data-ttu-id="80148-142">SharePoint 2013 Enterprise-App-Farm enthält die folgenden Komponenten:</span><span class="sxs-lookup"><span data-stu-id="80148-142">The SharePoint 2013 Enterprise App Farm contains the following components:</span></span> 
  
- <span data-ttu-id="80148-143">EDC</span><span class="sxs-lookup"><span data-stu-id="80148-143">EDC</span></span>
    
- <span data-ttu-id="80148-144">SSA-Proxy </span><span class="sxs-lookup"><span data-stu-id="80148-144">SSA proxy</span></span> 
    
- <span data-ttu-id="80148-145">Zeitgeberauftrag</span><span class="sxs-lookup"><span data-stu-id="80148-145">Timer job</span></span> 
    
<span data-ttu-id="80148-p110">Eine Abfrage oder eine Aktion, die vom Benutzer gesendet wird, wird an das EDC in der Unternehmens-App-Farm gesendet. Es geschieht Folgendes: </span><span class="sxs-lookup"><span data-stu-id="80148-p110">A query or action sent by the user is sent to the EDC in the Enterprise App Farm. The following actions occur:</span></span> 
  
- <span data-ttu-id="80148-148">Die Abfrage oder die Aktion wird an den SSA-Proxy übermittelt. </span><span class="sxs-lookup"><span data-stu-id="80148-148">The query or action goes to the SSA proxy.</span></span> 
    
- <span data-ttu-id="80148-p111">Der SSA-Proxy sendet eine Statusabfrage oder -antwort an den Zeitgeberauftrag in der Unternehmens-App-Farm. Zudem sendet er eine Statusabfrage oder -antwort an den SSA-Dienst in der SharePoint Services-Farm. Die Aktionen, die sich hieraus ergeben, werden im Abschnitt über die SharePoint Services-Farm beschrieben. </span><span class="sxs-lookup"><span data-stu-id="80148-p111">The SSA proxy sends a status query or response to the Timer job in the Enterprise App Farm, and it also sends a status query or response to the SSA service in the SharePoint Services Farm. The actions that result from this are described in the section about the SharePoint Services Farm.</span></span> 
    
- <span data-ttu-id="80148-151">Wenn der Zeitgeberauftrag eine Antwort erhält, sendet er diese an den SSA-Proxy und das EDC. </span><span class="sxs-lookup"><span data-stu-id="80148-151">When it receives a response, the Timer job sends the response to the SSA proxy and to the EDC.</span></span> 
    
- <span data-ttu-id="80148-152">Ergebnisse der Abfrage oder Aktion werden aus dem EDC an den Benutzer gesendet. </span><span class="sxs-lookup"><span data-stu-id="80148-152">Any results from the query or action are sent to the user from the EDC.</span></span> 
    
#### <a name="sharepoint-2013-services-farm"></a><span data-ttu-id="80148-153">SharePoint 2013-Dienstefarm</span><span class="sxs-lookup"><span data-stu-id="80148-153">SharePoint 2013 Services Farm</span></span>

<span data-ttu-id="80148-154">SharePoint 2013-Services-Farm enthält die folgenden Komponenten:</span><span class="sxs-lookup"><span data-stu-id="80148-154">The SharePoint 2013 Services Farm contains the following components:</span></span> 
  
- <span data-ttu-id="80148-155">SSA-Dienst </span><span class="sxs-lookup"><span data-stu-id="80148-155">SSA Service</span></span> 
    
- <span data-ttu-id="80148-156">Suchindexdatenbank </span><span class="sxs-lookup"><span data-stu-id="80148-156">Search index database</span></span> 
    
- <span data-ttu-id="80148-p112">SSA Admin_db-Datenbank. Die Tabelle Aktionen in dieser Datenbank enthält: Halten Version halten GetStatus</span><span class="sxs-lookup"><span data-stu-id="80148-p112">SSA admin_db database. The Actions Table in this database contains: Hold Release Hold GetStatus</span></span> 
    
- <span data-ttu-id="80148-159">EWS-Proxy </span><span class="sxs-lookup"><span data-stu-id="80148-159">EWS proxy</span></span> 
    
<span data-ttu-id="80148-160">Wenn der SSA-Proxy in der SharePoint-Unternehmens-App-Farm eine Statusabfrage an die SSA in der SharePoint Services-Farm sendet, geschieht Folgendes: </span><span class="sxs-lookup"><span data-stu-id="80148-160">When the SSA proxy in the SharePoint Enterprise App Farm sends a status query to the SSA in the SharePoint Services Farm, the following actions occur:</span></span> 
  
- <span data-ttu-id="80148-p113">Wenn die Anforderung eine Abfrage ist, konsultiert die Suchdienstanwendung den Suchindex. Die Antwort der Ermittlung wird an die SSA und dann über das EDC an den Benutzer zurückgegeben. </span><span class="sxs-lookup"><span data-stu-id="80148-p113">If the request is a query, the SSA consults the search index. The discovery response is returned to the SSA and then to the user through the EDC.</span></span> 
    
- <span data-ttu-id="80148-163">Wenn die Anforderung eine Schreibaktion ist, sendet der SSA-Dienst die Schreibaktion an die Verwaltungsdatenbank der Suchdienstanwendung. </span><span class="sxs-lookup"><span data-stu-id="80148-163">If the request is a write action, the SSA service sends the write action to the SSA admin_db.</span></span> 
    
- <span data-ttu-id="80148-164">Eine Durchforstung und reagiert Ergebnisse Anforderung wird an der SharePoint 2013 Inhalte Farm aus der SSA gesendet und eine Antwort wird an die SSA zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="80148-164">A crawl and responding results request is sent from the SSA to the SharePoint 2013 Content Farm and a response is returned to the SSA.</span></span> 
    
- <span data-ttu-id="80148-165">Eine Anforderung für Durchforstung und Antwortergebnisse wird von der SSA an die Windows-Dateifreigaben gesendet, und eine Antwort wird an die SSA zurückgegeben. </span><span class="sxs-lookup"><span data-stu-id="80148-165">A crawl and responding results request is sent from the SSA to the Windows File Shares, and a response is returned to the SSA.</span></span> 
    
- <span data-ttu-id="80148-166">Eine Abfrage für ausstehenden Aktion(en), Antworten oder Statusaktualisierungen wird von der SSA an den SSA-Proxy in der SharePoint-Inhaltsfarm gesendet, und eine Antwort wird an die SSA zurückgegeben. </span><span class="sxs-lookup"><span data-stu-id="80148-166">A query for pending action(s), responses, or status updates is sent from the SSA to the SSA proxy in the SharePoint Content Farm, and a response is returned to the SSA.</span></span> 
    
- <span data-ttu-id="80148-167">Eine Aktions-/Statusanforderung von Exchange wird von der SSA an den EWS-Proxy gesendet, der eine Aktions-/Statusanforderung für eine Exchange-Abfrage an den Exchange-Webdienst auf dem Exchange 2013-Server sendet.  </span><span class="sxs-lookup"><span data-stu-id="80148-167">An Exchange action/status request is sent from the SSA to the EWS proxy, which sends an Exchange Query action/status request to the Exchange Web Service on the Exchange 2013 server.</span></span> 
    
- <span data-ttu-id="80148-168">Eine Statusabfrage/-antwort wird von der SSA an die Verwaltungsdatenbank der Suchdienstanwendung gesendet und an die SSA zurückgegeben. </span><span class="sxs-lookup"><span data-stu-id="80148-168">A status query/response is sent from the SSA to the SSA admin_db and is returned to the SSA.</span></span> 
    
- <span data-ttu-id="80148-169">Eine Abfrage/Antwort für eine ausstehende Aktion wird von der SSA an die Verwaltungsdatenbank der Suchdienstanwendung gesendet und an die SSA zurückgegeben. </span><span class="sxs-lookup"><span data-stu-id="80148-169">A pending action query/response is sent from the SSA to the SSA admin_db and is returned to the SSA.</span></span> 
    
#### <a name="sharepoint-2013-content-farm"></a><span data-ttu-id="80148-170">SharePoint 2013 Inhalte Farm</span><span class="sxs-lookup"><span data-stu-id="80148-170">SharePoint 2013 Content Farm</span></span>

<span data-ttu-id="80148-171">Der SharePoint 2013 Inhalte Farm enthält die folgenden Komponenten:</span><span class="sxs-lookup"><span data-stu-id="80148-171">The SharePoint 2013 Content Farm contains the following components:</span></span> 
  
- <span data-ttu-id="80148-172">SSA-Proxy </span><span class="sxs-lookup"><span data-stu-id="80148-172">SSA proxy</span></span> 
    
- <span data-ttu-id="80148-173">Zeitgeberauftrag</span><span class="sxs-lookup"><span data-stu-id="80148-173">Timer job</span></span> 
    
- <span data-ttu-id="80148-174">Contoso SharePoint-Website </span><span class="sxs-lookup"><span data-stu-id="80148-174">Contoso SharePoint site</span></span> 
    
- <span data-ttu-id="80148-175">Contoso SharePoint-Inhalte </span><span class="sxs-lookup"><span data-stu-id="80148-175">Contoso SharePoint content</span></span> 
    
<span data-ttu-id="80148-176">Wenn die SSA in der SharePoint Services-Farm eine Statusabfrage an den SSA-Proxy in der SharePoint-Inhaltsfarm sendet, geschieht Folgendes: </span><span class="sxs-lookup"><span data-stu-id="80148-176">When the SSA in the SharePoint Services Farm sends a status query to the SSA Proxy in the SharePoint Content Farm, the following actions occur:</span></span> 
  
- <span data-ttu-id="80148-177">Der SSA-Proxy in der SharePoint-Inhaltsfarm sendet eine Abfrage für ausstehende Aktionen/Statusantwort an den Zeitgeberauftrag. </span><span class="sxs-lookup"><span data-stu-id="80148-177">The SSA proxy in the SharePoint Content Farm sends a query for pending actions/status response to the Timer job.</span></span> 
    
- <span data-ttu-id="80148-178">Der Zeitgeberauftrag sendet eine Anforderung an die Contoso SharePoint-Website, die die Contoso SharePoint-Inhalte überprüft. </span><span class="sxs-lookup"><span data-stu-id="80148-178">The Timer job sends a request to the Contoso SharePoint site, which reviews the Contoso SharePoint content.</span></span> 
    
- <span data-ttu-id="80148-179">Die Antwort auf die Abfrage der ausstehenden Aktionen/Statusabfrage wird von dem Zeitgeberauftrag an den SSA-Proxy in der SharePoint-Inhaltsfarm gesendet. Anschließend wird sie an den SSA-Dienst in der SharePoint Services-Farm gesendet. </span><span class="sxs-lookup"><span data-stu-id="80148-179">The response to the pending actions/status query is sent from the Timer job to the SSA proxy in the SharePoint Content Farm, and then it is sent to the SSA service in the SharePoint Services Farm</span></span> 
    
#### <a name="exchange-2013"></a><span data-ttu-id="80148-180">Exchange 2013</span><span class="sxs-lookup"><span data-stu-id="80148-180">Exchange 2013</span></span>

<span data-ttu-id="80148-181">Die Exchange 2013-Serverkomponente enthält den Exchange-Webdienst und bietet Folgendes: </span><span class="sxs-lookup"><span data-stu-id="80148-181">The Exchange 2013 server component contains the Exchange Web Service and provides the following:</span></span> 
  
- <span data-ttu-id="80148-182">Server-zu-Server-Vertrauensstellung/OAuth wird zwischen der SharePoint 2013 Inhalte Farm und Exchange 2013 behandelt.</span><span class="sxs-lookup"><span data-stu-id="80148-182">Server-to-server Trust/OAuth is handled between the SharePoint 2013 Content Farm and Exchange 2013.</span></span> 
    
- <span data-ttu-id="80148-183">Server-zu-Server-Vertrauensstellung/OAuth erfolgt zwischen Exchange 2013 und Lync 2013. </span><span class="sxs-lookup"><span data-stu-id="80148-183">Server-to-server Trust/OAuth is handled between Exchange 2013 and Lync 2013.</span></span> 
    
#### <a name="lync-2013"></a><span data-ttu-id="80148-184">Lync 2013</span><span class="sxs-lookup"><span data-stu-id="80148-184">Lync 2013</span></span>

<span data-ttu-id="80148-185">Die Lync 2013-Komponente archiviert Lync-Inhalte in Exchange 2013. </span><span class="sxs-lookup"><span data-stu-id="80148-185">The Lync 2013 component archives Lync content in Exchange 2013.</span></span> 
  
#### <a name="windows-file-shares"></a><span data-ttu-id="80148-186">Windows-Dateifreigaben</span><span class="sxs-lookup"><span data-stu-id="80148-186">Windows File Shares</span></span>

<span data-ttu-id="80148-187">Die Windows-Dateifreigaben-Komponente stellt Durchforstungsergebnisse für die SSA in der SharePoint Services-Farm bereit. </span><span class="sxs-lookup"><span data-stu-id="80148-187">The Windows File Shares component provides crawl results to the SSA in the SharePoint Services Farm.</span></span> 
  
### <a name="legend"></a><span data-ttu-id="80148-188">Legende</span><span class="sxs-lookup"><span data-stu-id="80148-188">Legend</span></span>

<span data-ttu-id="80148-189">Die Legende für dieses Diagramm enthält eine grafische Darstellung der verschiedenen zwischen den Komponenten gezeigten Datenverkehrstypen in Form verschiedenfarbiger Linien, wie nachfolgend beschrieben: </span><span class="sxs-lookup"><span data-stu-id="80148-189">The legend for this diagram graphically shows the different types of traffic depicted among the components in different colored lines as follows:</span></span> 
  
- <span data-ttu-id="80148-190">Hell blauen Linie: Abfragevorgang - eDiscovery-Abfrage oder eine Aktion Daten</span><span class="sxs-lookup"><span data-stu-id="80148-190">Light blue line: Query/action - eDiscovery query or action data</span></span> 
    
- <span data-ttu-id="80148-191">Orangefarbene Linie: eDisovery Antwort - Antwort eDiscovery-Abfragen von Daten</span><span class="sxs-lookup"><span data-stu-id="80148-191">Orange line: eDisovery response - eDiscovery query response data</span></span> 
    
- <span data-ttu-id="80148-192">Grüne Linie: Status-Abfrage/Antwort - eDiscovery-Abfrage/Antwort-Statusdaten</span><span class="sxs-lookup"><span data-stu-id="80148-192">Green line: Status query/response - eDiscovery status query/response data</span></span> 
    
- <span data-ttu-id="80148-193">Violett Linie: Exchange-Aktion/Status Anforderung - eDiscovery-Anforderung für den Status der Aktion für den Exchange-Datenverkehr.</span><span class="sxs-lookup"><span data-stu-id="80148-193">Purple line: Exchange action/status request - eDiscovery request for action status for Exchange traffic.</span></span> 
    
- <span data-ttu-id="80148-194">Rote Linie: Exchange Datenstatus/Antwort - eDiscovery-Abfrage oder Status Antwort vom Exchange.</span><span class="sxs-lookup"><span data-stu-id="80148-194">Red line: Exchange data/status response - eDiscovery query or status response from Exchange.</span></span> 
    
- <span data-ttu-id="80148-195">Gepunktete schwarze Linie: Server-zu-Server-Vertrauensstellung/OAuth </span><span class="sxs-lookup"><span data-stu-id="80148-195">Dotted black line: Server-to-Server Trust/Oauth</span></span> 
    
- <span data-ttu-id="80148-196">Durchgezogene schwarze Linie: Durchforstung/Ergebnisse </span><span class="sxs-lookup"><span data-stu-id="80148-196">Solid black line: Crawl/results</span></span> 
    

