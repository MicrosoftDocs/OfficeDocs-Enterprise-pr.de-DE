---
title: Allgemeine häufig gestellte Fragen zum Verschieben von Daten
ms.author: deniseb
author: denisebmsft
manager: laurawi
ms.date: 9/14/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 1f01bc6f-5d37-4d14-bdd3-9d94a1e23e14
description: Hier erhalten Sie Antworten zu allgemeinen Fragen zum Verschieben von Hauptdaten zu einer neuen Datacenter Geo.
ms.openlocfilehash: 40f83ee94aaa7c919f08d91d888ff131da02df67
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540888"
---
# <a name="data-move-general-faq"></a><span data-ttu-id="00c98-103">Allgemeine häufig gestellte Fragen zum Verschieben von Daten</span><span class="sxs-lookup"><span data-stu-id="00c98-103">Data move general FAQ</span></span>

<span data-ttu-id="00c98-104">Hier erhalten Sie Antworten zu allgemeinen Fragen zum Verschieben von Hauptdaten zu einer neuen Datacenter Geo.</span><span class="sxs-lookup"><span data-stu-id="00c98-104">Here are answers to general questions about moving core data to a new datacenter geo.</span></span>
  
 <span data-ttu-id="00c98-105">**F: wie sicherstellen Sie, dass meine Kundendaten Safe beim Verschieben und dass ich Ausfallzeiten werden nicht?**</span><span class="sxs-lookup"><span data-stu-id="00c98-105">**Q. How do you make sure my customer data is safe during the move and that I won't experience downtime?**</span></span>
  
<span data-ttu-id="00c98-p101">A. Daten Verschiebungen sind mit minimaler Beeinträchtigung für Endbenutzer an einen Back-End-Dienst-Vorgang. Features, die Faktoren beeinträchtigt werden können, sind in [während und nach der Daten verschoben](during-and-after-your-data-move.md)aufgeführt. Wir entsprechen die [Microsoft Online Services Service Level Agreement (SLA)](https://go.microsoft.com/fwlink/p/?LinkId=523897) für Verfügbarkeit, es werden, die Kunden So bereiten Sie vor oder während des Verschiebens überwachen müssen.</span><span class="sxs-lookup"><span data-stu-id="00c98-p101">A. Data moves are a back-end service operation with minimal impact to end-users. Features that can be impacted are listed in [During and after your data move](during-and-after-your-data-move.md). We adhere to the [Microsoft Online Services Service Level Agreement (SLA)](https://go.microsoft.com/fwlink/p/?LinkId=523897) for availability so there is nothing that customers need to prepare for or to monitor during the move.</span></span> 
  
<span data-ttu-id="00c98-p102">Alle Office 365-Dienste führen die gleichen Version in den Datencentern, damit Sie konsistente Funktionalität sicher sein können. Der Dienst wird über den gesamten Prozess vollständig unterstützt.</span><span class="sxs-lookup"><span data-stu-id="00c98-p102">All Office 365 services run the same versions in the datacenters, so you can be assured of consistent functionality. Your service is fully supported throughout the process.</span></span>
  
 <span data-ttu-id="00c98-112">**F: Was ist die Auswirkungen der müssen verschiedene Dienste befindet sich in unterschiedlichen Geos?**</span><span class="sxs-lookup"><span data-stu-id="00c98-112">**Q. What is the impact of having different services located in different geos?**</span></span>
  
<span data-ttu-id="00c98-p103">A. für einige Kunden und Kunden in der Mitte des Verschiebens kann einige der Office 365-Dienste in verschiedenen Geos befinden. Unsere Dienste unabhängig voneinander ausgeführt und keine Beeinträchtigung für die Benutzer vorhanden ist, wenn dies der Fall ist.</span><span class="sxs-lookup"><span data-stu-id="00c98-p103">A. For some existing customers and customers in the middle of the move process, some of the Office 365 services may be located in different geos. Our services run independently of each other and there is no user impact if this is the case.</span></span>
  
 <span data-ttu-id="00c98-116">**F: werden werden neue Office 365-Kunden automatisch in die neue Datacenter Geos bereitgestellt?**</span><span class="sxs-lookup"><span data-stu-id="00c98-116">**Q. Will new Office 365 customers be automatically provisioned in the new datacenter geos?**</span></span>
  
<span data-ttu-id="00c98-p104">A: Ja. Sobald eine neue Datacenter Geo verfügbar ist, müssen neue Office 365 für Unternehmenskunden, die ein Land für die neue Geo als ihres Landes während des Anmeldevorgangs auswählen ihren wichtige Daten in die neue Geo Datacenter gehostet.</span><span class="sxs-lookup"><span data-stu-id="00c98-p104">A. Yes. Once a new datacenter geo is available, new Office 365 for business customers who select a country eligible for the new geo as their country during sign-up will have their core data hosted in the new datacenter geo.</span></span>
  
 <span data-ttu-id="00c98-120">**F: Wo wird meine Daten befindet?**</span><span class="sxs-lookup"><span data-stu-id="00c98-120">**Q. Where is my data is located?**</span></span>
  
<span data-ttu-id="00c98-p105">Wir veröffentlichen Sie den Speicherort der Datacenter Geos Rechenzentren und Speicherort der Kundendaten auf der [Office 365 interaktive Datacenter zugeordnet ist ](https://o365datacentermap.azurewebsites.net). Am 1. August können Sie feststellen, ob den Speicherort der Ihre Kundendaten im Ruhezustand über den Abschnitt Datenspeicherort unter Ihrer Organisationsprofil in Office 365 Admin Center.</span><span class="sxs-lookup"><span data-stu-id="00c98-p105">We publish the location of datacenter geos, datacenters, and location of customer data on the [ Office 365 interactive datacenter maps ](https://o365datacentermap.azurewebsites.net). As of August 1, you will be able to verify the location of your customer data at rest via the Data Location section under your Organization Profile in the Office 365 Admin Center.</span></span>
  
 <span data-ttu-id="00c98-123">**F: werden werden vorhandene Office 365-Kunden in die neue Datacenter Geos verschoben?**</span><span class="sxs-lookup"><span data-stu-id="00c98-123">**Q. Will existing Office 365 customers be moved to the new datacenter geos?**</span></span>
  
<span data-ttu-id="00c98-p106">A. berechtigt Office 365-Kunden können Anforderung die Core-Daten in die neue Geos verschoben wurden. Kunden benötigen eine Anforderung vor dem Termin für ihre Geo übermitteln, um teilnehmen.</span><span class="sxs-lookup"><span data-stu-id="00c98-p106">A. Eligible Office 365 customers can request to have their core data moved to the new geos. Customers will need to submit a request before the deadline for their geo in order to participate.</span></span> 
  
 <span data-ttu-id="00c98-127">**F: Was Kunden, die eine Verschiebung anfordern können?**</span><span class="sxs-lookup"><span data-stu-id="00c98-127">**Q. What customers are eligible to request a move?**</span></span>
  
<span data-ttu-id="00c98-p107">Kommerzielle A. vorhandenen Office 365-Kunden, die ein Land für die neue Datacenter Geo ausgewählt werden eine Verschiebung anfordern können.</span><span class="sxs-lookup"><span data-stu-id="00c98-p107">A. Existing Office 365 commercial customers who selected a country eligible for the new datacenter geo will be able to request a move.</span></span> 
  
 <span data-ttu-id="00c98-130">**F: Wann wird eine Verschiebung anfordern können werden?**</span><span class="sxs-lookup"><span data-stu-id="00c98-130">**Q. When will I be able to request a move?**</span></span>
  
<span data-ttu-id="00c98-p108">A. der Anforderung Zeitraum wird auf der Seite [wie Sie Ihre Daten Move request](request-your-data-move.md) vorgestellt.</span><span class="sxs-lookup"><span data-stu-id="00c98-p108">A. The request period will be announced on the [How to request your data move](request-your-data-move.md) page.</span></span> 
  
 <span data-ttu-id="00c98-133">**F: wie kann ich anfordern verschoben werden?**</span><span class="sxs-lookup"><span data-stu-id="00c98-133">**Q. How can I request to be moved?**</span></span>
  
<span data-ttu-id="00c98-p109">A. zugelassene Kunden werden eine Seite in ihrer [Office 365-Verwaltungsportal](https://portal.office.com/)angezeigt. Anleitung zum Anfordern einer Verschiebung finden Sie unter [Gewusst wie: Anfordern der Daten verschoben](request-your-data-move.md) .</span><span class="sxs-lookup"><span data-stu-id="00c98-p109">A. Eligible customers will see a page in their [Office 365 Admin Portal](https://portal.office.com/). Please see [How to request your data move](request-your-data-move.md) for instructions on how to request a move.</span></span> 
  
 <span data-ttu-id="00c98-137">**Frage: ändern kann ich meine Auswahl nach Anforderung einer Verschiebung?**</span><span class="sxs-lookup"><span data-stu-id="00c98-137">**Q. Can I change my selection after requesting a move?**</span></span>
  
<span data-ttu-id="00c98-p110">A: Es ist nicht möglich, dass wir Sie vom Prozess entfernen, nachdem Sie Ihre Anforderung gesendet.</span><span class="sxs-lookup"><span data-stu-id="00c98-p110">A. It is not possible for us to remove you from the process after you submit your request.</span></span>
  
 <span data-ttu-id="00c98-140">**F: Was geschieht, wenn ich eine Verschiebung vor dem Termin nicht anfordern?**</span><span class="sxs-lookup"><span data-stu-id="00c98-140">**Q. What happens if I do not request a move before the deadline?**</span></span>
  
<span data-ttu-id="00c98-p111">A. leider annehmen nach dem Termin in jedem Geo verschoben werden soll.</span><span class="sxs-lookup"><span data-stu-id="00c98-p111">A. We are unable to accept requests to be moved after the deadline in each geo.</span></span>
  
 <span data-ttu-id="00c98-143">**F: Was geschieht, wenn ich meine Daten verschieben möchten, um eine bessere Leistung des Netzwerks abrufen?**</span><span class="sxs-lookup"><span data-stu-id="00c98-143">**Q. What if I want to move my data in order to get better network performance?**</span></span>
  
<span data-ttu-id="00c98-p112">Wird erreicht bald ein Office 365-Datencenter ist keine Garantie für ein Netzwerk eine bessere Leistung. Es gibt viele Faktoren und Komponenten, die zwischen der Endbenutzer und Office 365-Dienst die netzwerkleistung beeinflussen. Weitere Informationen zu diesem und Optimieren der Leistung finden Sie unter [netzwerkplanung und leistungsoptimierung für Office 365](network-planning-and-performance.md).</span><span class="sxs-lookup"><span data-stu-id="00c98-p112">Being close to an Office 365 datacenter is not a guarantee for a better networking performance. There are many factors and components that impact the network performance between the end user and the Office 365 service. For more information about this and performance tuning see [Network planning and performance tuning for Office 365](network-planning-and-performance.md).</span></span>
  
 <span data-ttu-id="00c98-147">**F. verschieben müssen alle Dienste ihre Daten am selben?**</span><span class="sxs-lookup"><span data-stu-id="00c98-147">**Q. Do all the services move their data on the same day?**</span></span>
  
<span data-ttu-id="00c98-p113">A. der Dienste verschieben Sie ihre Daten nicht gleichzeitig. Jeder Dienst wird unabhängig voneinander verschoben und ihre Daten zu unterschiedlichen Zeiten wird wahrscheinlich verschoben.</span><span class="sxs-lookup"><span data-stu-id="00c98-p113">A. The services do not move their data at the same time. Each service will move independently and will likely move their data at different times.</span></span>
  
 <span data-ttu-id="00c98-151">**Frage: auswählen kann ich, wenn ich meine Daten verschoben werden sollen?**</span><span class="sxs-lookup"><span data-stu-id="00c98-151">**Q. Can I choose when I want my data to be moved?**</span></span>
  
<span data-ttu-id="00c98-p114">A. Kunden können nicht auf ein bestimmtes Datum auswählen, können sie nicht Wechsel verzögern und wir kein bestimmtes Datum oder Zeitrahmen für die Verschiebungen freigeben.</span><span class="sxs-lookup"><span data-stu-id="00c98-p114">A. Customers are not able to select a specific date, they cannot delay their move, and we cannot share a specific date or timeframe for the moves.</span></span>
  
 <span data-ttu-id="00c98-154">**Frage: freigeben können Sie, wenn meine Daten verschoben werden?**</span><span class="sxs-lookup"><span data-stu-id="00c98-154">**Q. Can you share when my data will be be moved?**</span></span>
  
<span data-ttu-id="00c98-p115">A. Daten Verschiebungen sind mit minimaler Beeinträchtigung für Endbenutzer an einen Back-End-Vorgang. Die Komplexität, die Genauigkeit und die Dezimalstellen, wir Daten Verschiebungen in einer Umgebung mit global betrieben und automatisierte ausführen müssen, aus, dass uns freigeben, wenn eine Verschiebung der Daten für die Durchführung für Ihre Mandanten oder eine beliebige andere mit einem einzelnen Mandanten erwartet wird. Kunden erhalten eine Bestätigung in Nachrichtencenter pro teilnehmenden Dienst nach Abschluss der Daten verschieben.</span><span class="sxs-lookup"><span data-stu-id="00c98-p115">A. Data moves are a back-end operation with minimal impact to end-users. The complexity, precision and scale at which we need to perform data moves within a globally operated and automated environment prohibit us from sharing when a data move is expected to complete for your tenant or any other single tenant. Customers will receive one confirmation in Message Center per participating service when its data move has completed.</span></span> 
  
 <span data-ttu-id="00c98-159">**F: Was geschieht, wenn Benutzer Dienste zugreifen, während die Daten verschoben wird?**</span><span class="sxs-lookup"><span data-stu-id="00c98-159">**Q. What happens if users access services while the data is being moved?**</span></span>
  
<span data-ttu-id="00c98-p116">A: Siehe [während und nach der Daten verschoben](during-and-after-your-data-move.md) , für eine vollständige Liste der Features, die während der Teile der Daten beschränkt sein können, die für jeden Dienst verschoben werden.</span><span class="sxs-lookup"><span data-stu-id="00c98-p116">A. See [During and after your data move](during-and-after-your-data-move.md) for a complete list of features that may be limited during portions of the data move for each service.</span></span> 
  
 <span data-ttu-id="00c98-162">**F: wissen ich, dass die Verschiebung abgeschlossen ist?**</span><span class="sxs-lookup"><span data-stu-id="00c98-162">**Q. How do I know the move is complete?**</span></span>
  
<span data-ttu-id="00c98-p117">A. sehen Sie sich das Office 365-Nachrichtencenter zur Bestätigung, dass das Verschieben von Daten für jeden Dienst abgeschlossen ist. Wenn Daten für jeden Dienst verschoben werden, wir stellen eine Abschlusshinweis damit Sie drei Abschluss Hinweise erzielen: jeweils eines für Exchange Online, SharePoint Online und Skype für Business Online.</span><span class="sxs-lookup"><span data-stu-id="00c98-p117">A. Watch the Office 365 message center for confirmation that the move of each service's data is complete. When each service's data is moved, we'll post a completion notice so you'll get three completion notices: one each for Exchange Online, SharePoint Online, and Skype for Business Online.</span></span>
  
<span data-ttu-id="00c98-166">Wenn Sie Probleme nach dem Verschieben angezeigt wird, wenden Sie sich an den [Office 365-Support](https://go.microsoft.com/fwlink/p/?LinkID=522459) , um Hilfe zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="00c98-166">If you see any issues after the move, contact [Office 365 Support](https://go.microsoft.com/fwlink/p/?LinkID=522459) to get assistance.</span></span> 
  
 <span data-ttu-id="00c98-167">**F: welche Daten für Office 365 in der neuen Datacenter Geos gespeichert werden?**</span><span class="sxs-lookup"><span data-stu-id="00c98-167">**Q. What data for Office 365 is stored in the new datacenter geos?**</span></span>
  
<span data-ttu-id="00c98-p118">A. wenn ein Kunde Vorschriften speichert seine Mandanten in einem der der neue Datacenter Geos Microsoft folgenden Customer-Daten im Ruhezustand innerhalb der geografisch:</span><span class="sxs-lookup"><span data-stu-id="00c98-p118">A. If a customer provisions its tenant in one of the new datacenter geos, Microsoft stores the following customer data at rest within the geo:</span></span>
  
- <span data-ttu-id="00c98-170">Exchange Online Inhalt von Postfächern (e-Mail-Body, Kalendereinträge und den Inhalt von e-Mail-Anlagen)</span><span class="sxs-lookup"><span data-stu-id="00c98-170">Exchange Online mailbox content (e-mail body, calendar entries, and the content of email attachments)</span></span>
    
- <span data-ttu-id="00c98-171">SharePoint Online-Website-Inhalte und Dateien, die innerhalb der Website, einschließlich Project Online und Access Onlineinhalt gespeichert.</span><span class="sxs-lookup"><span data-stu-id="00c98-171">SharePoint Online site content and the files stored within that site, including Project Online and Access Online content.</span></span>
    
<span data-ttu-id="00c98-172">Darüber hinaus werden diese Daten nicht außerhalb der Geo repliziert.</span><span class="sxs-lookup"><span data-stu-id="00c98-172">In addition, this data is not replicated outside of the geo.</span></span>
  
 <span data-ttu-id="00c98-173">**F: Ich erhalte einen Office 365-Kunden in einer der der neue Datacenter Geos, aber wenn ich haben angemeldet, ausgewählt ich ein anderen Land. Wie kann ich die neue Datacenter Geo werden verschoben?**</span><span class="sxs-lookup"><span data-stu-id="00c98-173">**Q. I am an Office 365 customer in one of the new datacenter geos, but when I signed up, I selected a different country. How can I be moved to the new datacenter geo?**</span></span>
  
<span data-ttu-id="00c98-p119">A. leider ist es nicht möglich, das Land Ihres Mandanten zu ändern. Stattdessen müssen Sie einen neuen Office 365-Mandanten mit ein neues Abonnement erstellt, und verschieben manuell Ihren Benutzern und Daten, die dem neuen Mandanten.</span><span class="sxs-lookup"><span data-stu-id="00c98-p119">A. Unfortunately, it is not possible to change the country associated with your tenant. Instead, you need to create a new Office 365 tenant with a new subscription and manually move your users and data to the new tenant.</span></span>
  
 <span data-ttu-id="00c98-177">**F: werden gibt es Änderungen auf meiner Zahlung?**</span><span class="sxs-lookup"><span data-stu-id="00c98-177">**Q. Will there be any changes on my bill?**</span></span>
  
<span data-ttu-id="00c98-p120">A. in den meisten Fällen sind keine Änderungen, die Kunden in auf ihre Abrechnung angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="00c98-p120">A. In most cases there are no changes that customers in will see on their billing statement.</span></span>
  
<span data-ttu-id="00c98-p121">Microsoft wird aufgeladen Australien Ihre Kunden über Office 365 einen zusätzlichen Betrag gleich der Australische GST für Office 365-Dienste und Tax Rechnungen Problem wird. Diese Änderung tritt auf, da Australische GST über eine steuerpflichtige Lieferung von Waren und bereitgestellten und angebotene in Australien Dienste.</span><span class="sxs-lookup"><span data-stu-id="00c98-p121">Microsoft will charge all Australian customers of Office 365 an additional amount equal to the Australian GST for Office 365 services and will issue tax invoices. This change will occur because Australian GST is payable on taxable supplies of goods and services provided and offered in Australia.</span></span>
  
 <span data-ttu-id="00c98-182">**F: Was geschieht, wenn wir für die e-Mail-Migration zu Office 365 während des Verschiebens des Exchange Online sind?**</span><span class="sxs-lookup"><span data-stu-id="00c98-182">**Q. What happens if we are in process of email data migration to Office 365 during the Exchange Online move?**</span></span>
  
<span data-ttu-id="00c98-p122">A. wenn Migrieren von e-Mails ausgeführt werden, werden jede einzelne Postfächer, die derzeit migriert werden abgebrochen werden, während die Mandanten-Verschiebung schließt und Migration dieser Postfächer automatisch neu gestartet wird, sobald der Mandanten in den Datencentern Ziel ist.</span><span class="sxs-lookup"><span data-stu-id="00c98-p122">A. If email migrations are in progress, any individual mailboxes that are currently being migrated will be canceled while the tenant move finalizes, and migration of those mailboxes will automatically restart once the tenant is in the target datacenters.</span></span>
  
 <span data-ttu-id="00c98-185">**F: nach Daten aus der vorherigen Datacenter Geo verschoben werden, wird sie von den Datencentern entfernt?**</span><span class="sxs-lookup"><span data-stu-id="00c98-185">**Q. After data is moved out of the previous datacenter geo, is it removed from those datacenters?**</span></span>
  
<span data-ttu-id="00c98-p123">A: Ja, werden die alten Daten nach einer bestimmten Zeitspanne gelöscht werden.</span><span class="sxs-lookup"><span data-stu-id="00c98-p123">A. Yes, the old data will be purged after a period of time.</span></span>
  
 <span data-ttu-id="00c98-188">**Frage: evaluieren kann ich einige Benutzer?**</span><span class="sxs-lookup"><span data-stu-id="00c98-188">**Q. Can I pilot some users?**</span></span>
  
<span data-ttu-id="00c98-p124">A. Wenn Ihre Office 365-Mandanten zu einer neuen Datacenter Geo verschoben wird, werden alle Benutzer gleichzeitig verschoben. Sie können einen separaten Studien Mandanten zum Testen der Konnektivität erstellen, aber der Studien Mandanten nicht mit Ihren vorhandenen Mandanten keinerlei kombiniert werden.</span><span class="sxs-lookup"><span data-stu-id="00c98-p124">A. When your Office 365 tenant is moved to a new datacenter geo, all users are moved at once. You can create a separate trial tenant to test connectivity, but the trial tenant can't be combined in any way with your existing tenant.</span></span>
  
 <span data-ttu-id="00c98-192">**F: wie ich die Verschiebung und, die in meinem Unternehmen benachrichtigt werden, werden benachrichtigt werden?**</span><span class="sxs-lookup"><span data-stu-id="00c98-192">**Q. How will I be notified about the move and who at my company will be notified?**</span></span>
  
<span data-ttu-id="00c98-p125">A. wir verwenden Office 365 Message Center, das für alle Benutzer mit Administratorberechtigungen in Office 365 sichtbar ist.</span><span class="sxs-lookup"><span data-stu-id="00c98-p125">A. We'll use the Office 365 message center, which is visible to anyone with any admin permissions in Office 365.</span></span>
  
 <span data-ttu-id="00c98-195">**F: Ich möchte nicht warten, bis Microsoft um meine Daten zu verschieben. Kann ich gerade erstellen einen neuen Mandanten und verschieben selbst zu?**</span><span class="sxs-lookup"><span data-stu-id="00c98-195">**Q. I don't want to wait for Microsoft to move my data. Can I just create a new tenant and move myself?**</span></span>
  
<span data-ttu-id="00c98-p126">A. Ja, jedoch der Prozess nicht wie nahtlos, als wäre Microsoft zum Verschieben Daten verwenden.</span><span class="sxs-lookup"><span data-stu-id="00c98-p126">A. Yes, however the process will not be as seamless as if Microsoft were to perform the data move.</span></span>
  
<span data-ttu-id="00c98-p127">Wenn Sie einen neuen Mandanten erstellen, nachdem die neue Datacenter Geo verfügbar ist, wird der neue Mandanten in die neue Geo gehostet werden. Diese neuen Mandanten völlig unabhängig von Ihrem vorherigen Mandanten und Sie wäre zum Verschieben aller Benutzerpostfächer, Websiteinhalt, Domänennamen und alle anderen Daten verantwortlich. Beachten Sie, dass der Name des Mandanten aus einem Mandanten in eine andere verschoben werden kann. Es wird empfohlen, dass Sie warten Sie das Move-Programm von Microsoft bereitgestellt werden, wie wir darauf achten, werden alle Einstellungen, Daten und Abonnements für Ihre Benutzer verschieben.</span><span class="sxs-lookup"><span data-stu-id="00c98-p127">If you create a new tenant after the new datacenter geo is available, the new tenant will be hosted in the new geo. This new tenant is completely separate from your previous tenant and you would be responsible for moving all user mailboxes, site content, domain names, and any other data. Note that you can't move the tenant name from one tenant to another. We recommend that you wait for the move program provided by Microsoft as we'll take care of moving all settings, data, and subscriptions for your users.</span></span>
  
 <span data-ttu-id="00c98-202">**F: bin ich nicht bereit, um die verschoben werden, können bestimmte Move Date auswählen?**</span><span class="sxs-lookup"><span data-stu-id="00c98-202">**Q. I'm not ready to be moved, can I pick a specific move date?**</span></span>
  
<span data-ttu-id="00c98-p128">A: Es ist nicht möglich, dass Sie so ändern Sie bei jeder Dienst Kundendaten verschoben werden sollen. Verschiebt Daten werden mit minimaler Beeinträchtigung für Endbenutzer an einen Back-End-Vorgang.</span><span class="sxs-lookup"><span data-stu-id="00c98-p128">A. It is not possible for you to change when each service's customer data will be moved. Data moves are a back-end operation with minimal impact to end-users.</span></span>
  
 <span data-ttu-id="00c98-206">**F: Meine Kundendaten wurde bereits an eine neue Datacenter Geo verschoben. Kann ich wieder verschieben?**</span><span class="sxs-lookup"><span data-stu-id="00c98-206">**Q. My customer data has already been moved to a new datacenter geo. Can I move back?**</span></span>
  
<span data-ttu-id="00c98-p129">A. Dies ist nicht möglich. Kunden, die in der neuen Geo Rechenzentren verschoben wurden werden nicht wieder verschoben. Als einen Kunden in eine beliebige Geo werden Sie die gleiche Qualität des Webdiensts, Leistung und Sicherheitssteuerelemente wie zuvor bemerken.</span><span class="sxs-lookup"><span data-stu-id="00c98-p129">A. This is not possible. Customers who have been moved to new geo datacenters cannot be moved back. As a customer in any geo, you will experience the same quality of service, performance, and security controls as you did before.</span></span>
  
 <span data-ttu-id="00c98-211">**F: verwenden die neue Datacenter Geos dieselben Versionen von Office 365-Dienste als den aktuellen Datacenter Geos?**</span><span class="sxs-lookup"><span data-stu-id="00c98-211">**Q. Do the new datacenter geos use the same versions of Office 365 services as the current datacenter geos?**</span></span>
  
<span data-ttu-id="00c98-p130">A: Ja.</span><span class="sxs-lookup"><span data-stu-id="00c98-p130">A. Yes.</span></span>
  
 <span data-ttu-id="00c98-214">**F: wird Office 365-Mandanten in die neue Datencenter gehostet werden für Benutzer außerhalb des Landes verfügbar?**</span><span class="sxs-lookup"><span data-stu-id="00c98-214">**Q. Will Office 365 tenants hosted in the new datacenters be available to users outside of the country?**</span></span>
  
<span data-ttu-id="00c98-p131">A: Ja. Microsoft stellt ein großes globales Netzwerk mit dem öffentlichen internetverbindungen an mehr als 50 Speicherorten in 23 Ländern auf der ganzen Welt mit Peers Agreements mit mehr als 1.500 Internetdienstanbietern (ISP). Benutzer können auf die Datencentern zugreifen, von wo sie sich im Internet befinden.</span><span class="sxs-lookup"><span data-stu-id="00c98-p131">A. Yes. Microsoft maintains a large global network with public Internet connections in more than 50 locations in 23 countries around the world with peering agreements with more than 1,500 Internet Service Providers (ISPs). Users will be able to access the datacenters from wherever they are on the Internet.</span></span>
  

