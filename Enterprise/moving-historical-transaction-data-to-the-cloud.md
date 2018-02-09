---
title: Verschieben von historischen Transaktionsdaten in die Cloud
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 3e9c405a-415b-4584-aa7e-f2489299c457
description: "Zusammenfassung: In diesem Artikel erfahren Sie, wie Contoso eine SQL Server Stretch-Datenbank implementiert hat, um seinen Bedarf an lokalem Datenspeicher sowie seine täglichen laufenden Kosten zu reduzieren."
ms.openlocfilehash: 9d8d51aa1bc7a304d1148111aedd54916d9e8052
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/09/2018
---
# <a name="moving-historical-transaction-data-to-the-cloud"></a><span data-ttu-id="f3721-103">Verschieben von historischen Transaktionsdaten in die Cloud</span><span class="sxs-lookup"><span data-stu-id="f3721-103">Moving historical transaction data to the cloud</span></span>

 <span data-ttu-id="f3721-104">**Zusammenfassung:** In diesem Artikel erfahren Sie, wie Contoso eine SQL Server Stretch-Datenbank implementiert hat, um seinen Bedarf an lokalem Datenspeicher sowie seine täglichen laufenden Kosten zu reduzieren.</span><span class="sxs-lookup"><span data-stu-id="f3721-104">**Summary:** How Contoso implemented SQL Server stretch database to reduce its on-premises data storage needs and daily running costs.</span></span>
  
<span data-ttu-id="f3721-p101">Im Unternehmensspeichersystem von Contoso wird eine große Menge historischer Transaktionsdaten gespeichert, um rechtliche Vorschriften einzuhalten. Die Daten werden außerdem für die Marketingforschung und die BI-Analyse von Ausgabetrends herangezogen. Zudem muss Contoso archivierte Daten in einem zeitaufwendigen Prozess von Magnetbändern wiederherstellen. Als sich die im Contoso-Unternehmensspeichersystem eingesetzte Hardware dem Ende ihres Lebenszyklus näherte, wurde klar, dass ein Austausch sehr teuer werden würde.</span><span class="sxs-lookup"><span data-stu-id="f3721-p101">Contoso's enterprise storage system stores a large amount of historical transaction data for adherence with regulatory requirements and for marketing research and BI analysis of spending trends. Contoso also needs to restore archived data from magnetic tape, a time-intensive process. The hardware in Contoso's enterprise storage system was nearing its end of life and replacing it would be very expensive.</span></span> 
  
<span data-ttu-id="f3721-p102">Contoso erkannte die geschäftliche Notwendigkeit einer Konsolidierung seiner Rechenzentren und entschied sich für ein Upgrade auf SQL Server 2016, da dieses Betriebssystem die Hybridfunktion „Stretch-Datenbank" mitbringt und nahtlos mit Azure integriert ist. Mithilfe einer Stretch-Datenbank kann Contoso selten verwendete (kalte) Daten in Tabellen aus seinen lokalen Speichern in einen Cloud-Speicher verlagern. Das setzt Kapazität auf den lokalen Festplatten frei und reduziert den Wartungsaufwand. Sowohl häufig verwendete (heiße) Daten als auch kalte Daten werden in denselben Tabellen gespeichert und sind jederzeit verfügbar: für Anwendungen und Benutzer ebenso wie zu Wartungszwecken wie Sicherung und Wiederherstellung. In Abbildung 1 sehen Sie eine Stretch-Datenbank.</span><span class="sxs-lookup"><span data-stu-id="f3721-p102">As part of its business need to scale down its on-premises datacenters, Contoso chose to upgrade to SQL Server 2016 because of the Stretch Database hybrid feature and its seamless integration with Azure. Stretch Database allows Contoso to move the cold data in its tables from on-premises to cloud storage, freeing up local disk space and reducing maintenance. Both hot and cold data are in the same tables and are always available to applications and their users and for maintenance, such as backups and restores. Figure 1 shows Stretch Database.</span></span>
  
<span data-ttu-id="f3721-112">**Abbildung 1: SQL Server Stretch-Datenbank**</span><span class="sxs-lookup"><span data-stu-id="f3721-112">**Figure 1: SQL Server Stretch Database**</span></span>

![SQL Server Stretch-Datenbank als Hybriddatenlösung](images/Contoso_Poster/StretchDB01.png)
  
<span data-ttu-id="f3721-114">Abbildung 1 zeigt, wie ein SQL-Client T-SQL-Abfragen an einen Server sendet, auf dem SQL Server 2016 ausgeführt wird. Dieser Server leitet die Abfragen anschließend an eine Azure SQL Stretch-Datenbank in Azure-PaaS weiter.</span><span class="sxs-lookup"><span data-stu-id="f3721-114">Figure 1 shows how a SQL client sends T-SQL queries to a server running SQL Server 2016, which forwards them to an Azure SQL Stretch Database in Azure PaaS.</span></span>
  
<span data-ttu-id="f3721-115">Weitere Informationen finden Sie unter [Stretch-Datenbank](https://msdn.microsoft.com/library/dn935011.aspx).</span><span class="sxs-lookup"><span data-stu-id="f3721-115">For more information, see [Stretch Database](https://msdn.microsoft.com/library/dn935011.aspx).</span></span>
  
<span data-ttu-id="f3721-116">Zur Verschiebung der historischen Daten in die Cloud ging Contoso wie folgt vor:</span><span class="sxs-lookup"><span data-stu-id="f3721-116">Contoso used these steps to move their historical data to the cloud:</span></span>
  
1. <span data-ttu-id="f3721-117">Datenbankanalyse</span><span class="sxs-lookup"><span data-stu-id="f3721-117">Analyze databases</span></span>
    
    <span data-ttu-id="f3721-p103">Contoso analysierte die Tabellen in den Datenbanken, die in die Cloud verschoben werden sollten, und behob etwaige Probleme. Dank des neuen Stretch Database Advisor hatte das Unternehmen einen vollständigen Überblick über alle Funktionen von SQL Server 2016 und ihre Auswirkungen. Unter anderem half das Tool bei der Identifizierung von Tabellen mit kalten Daten, die für eine Auslagerung in eine Stretch-Datenbank geeignet waren.</span><span class="sxs-lookup"><span data-stu-id="f3721-p103">Performed an analysis of the tables in the databases that they intended to move to the cloud and fixed any issues. The new Stretch Database Advisor gave them a full overview of what they can expect from all features in SQL Server 2016, including which tables have cold data that could be stretched.</span></span>
    
2. <span data-ttu-id="f3721-120">Upgrade</span><span class="sxs-lookup"><span data-stu-id="f3721-120">Upgrade</span></span>
    
    <span data-ttu-id="f3721-121">Contoso aktualisierte die SQL-Server im Rechenzentrum seines Pariser Hauptsitzes auf SQL Server 2016.</span><span class="sxs-lookup"><span data-stu-id="f3721-121">Updated existing SQL servers in the Paris headquarters datacenter to SQL Server 2016.</span></span>
    
3. <span data-ttu-id="f3721-122">Migration kalter Daten in die Cloud</span><span class="sxs-lookup"><span data-stu-id="f3721-122">Migrate cold data to the cloud</span></span>
    
    <span data-ttu-id="f3721-p104">Contoso identifizierte mithilfe von SQL Management Studio alle Datenbanken, die auf die Stretch-Datenbank ausgeweitet werden sollten, sowie alle Tabellen, die zu Instanzen der Stretch-Datenbank in Azure migriert werden sollten. Anschließend verschob SQL Server2016 die historischen Daten im Hintergrund nach und nach in die Stretch-Datenbanken in Azure.</span><span class="sxs-lookup"><span data-stu-id="f3721-p104">Using SQL Management Studio, they identified the databases to stretch and the tables to migrate to instances of Stretch Database in Azure. Over time and in the background, SQL Server 2016 moved the historical data to stretch databases in Azure.</span></span>
    
<span data-ttu-id="f3721-125">Unten sehen Sie die finale Konfiguration für einen einzelnen Server im Pariser Hauptsitz, auf dem SQL Server 2016 ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="f3721-125">Here is the resulting configuration for one server running SQL Server 2016 in the Paris headquarters.</span></span>
  
<span data-ttu-id="f3721-126">**Abbildung 2: Implementierung einer Stretch-Datenbank für einen Server im Contoso-Rechenzentrum**</span><span class="sxs-lookup"><span data-stu-id="f3721-126">**Figure 2: Using Stretch Database for a server in Contoso's datacenter**</span></span>

![Contoso-Konfiguration: SQL Server Stretch-Datenbank für einen einzelnen Computer, auf dem SQL Server ausgeführt wird](images/Contoso_Poster/StretchDB02.png)

  
<span data-ttu-id="f3721-128">Abbildung 2 zeigt, wie Benutzerabfragen an einen Anwendungsserver im Contoso-Rechenzentrum in SQL-Abfragen umgewandelt und an eine Azure SQL Stretch-Datenbank in Azure-PaaS weitergeleitet werden.</span><span class="sxs-lookup"><span data-stu-id="f3721-128">Figure 2 shows how user queries to an application server in Contoso's datacenter become SQL queries that are passed to an Azure SQL Stretch Database in Azure PaaS.</span></span>
  
<span data-ttu-id="f3721-p105">Die Benutzer greifen über die bereits vorhandenen Apps und Abfragen auf die Daten zu. Alle Zugriffsrichtlinien bleiben unverändert. Bandsicherungen wird Contoso zukünftig nicht mehr durchführen müssen. Der Wartungsprozess besteht aus der Sicherung der heißen Daten und, wenn nötig, deren Wiederherstellung.</span><span class="sxs-lookup"><span data-stu-id="f3721-p105">Users access the data through existing apps and queries. Access policies remain the same. Moving forward, there is no need for tape backups. Maintenance consists of backing up and restoring hot data.</span></span>
  
<span data-ttu-id="f3721-133">Die Vorteile für Contoso nach der Implementierung einer Stretch-Datenbank:</span><span class="sxs-lookup"><span data-stu-id="f3721-133">After implementing Stretch Database, Contoso:</span></span>
  
- <span data-ttu-id="f3721-134">Reduzierung des Bedarfs an lokalem Datenspeicher um 85 %</span><span class="sxs-lookup"><span data-stu-id="f3721-134">Reduced its on-premises data storage needs by 85%.</span></span>
    
- <span data-ttu-id="f3721-135">Wegfall der Notwendigkeit für eine Aktualisierung des Unternehmensspeichersystems sowie für eine Archivierung auf magnetischen Bändern</span><span class="sxs-lookup"><span data-stu-id="f3721-135">Made the update of the enterprise storage system and reliance on magnetic tape archives unnecessary.</span></span>
    
- <span data-ttu-id="f3721-136">Reduzierung der täglichen laufenden Kosten in signifikantem Umfang</span><span class="sxs-lookup"><span data-stu-id="f3721-136">Reduced its daily running costs significantly.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="f3721-137">Weitere Artikel</span><span class="sxs-lookup"><span data-stu-id="f3721-137">See Also</span></span>

[<span data-ttu-id="f3721-138">Enterprise-Szenarien für die Contoso Corporation</span><span class="sxs-lookup"><span data-stu-id="f3721-138">Enterprise scenarios for the Contoso Corporation</span></span>](enterprise-scenarios-for-the-contoso-corporation.md)
  
[<span data-ttu-id="f3721-139">Contoso in der Microsoft-Cloud</span><span class="sxs-lookup"><span data-stu-id="f3721-139">Contoso in the Microsoft Cloud</span></span>](contoso-in-the-microsoft-cloud.md)
  
[<span data-ttu-id="f3721-140">Ressourcen zur Cloud-IT-Architektur von Microsoft</span><span class="sxs-lookup"><span data-stu-id="f3721-140">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="f3721-141">Stretch-Datenbank</span><span class="sxs-lookup"><span data-stu-id="f3721-141">Stretch Database</span></span>](https://msdn.microsoft.com/library/dn935011.aspx)
  
[<span data-ttu-id="f3721-142">Microsoft-Roadmap Enterprise Cloud: Ressourcen für IT-Entscheidungsträger</span><span class="sxs-lookup"><span data-stu-id="f3721-142">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)




