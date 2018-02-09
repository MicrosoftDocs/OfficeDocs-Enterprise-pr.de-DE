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
# <a name="moving-historical-transaction-data-to-the-cloud"></a>Verschieben von historischen Transaktionsdaten in die Cloud

 **Zusammenfassung:** In diesem Artikel erfahren Sie, wie Contoso eine SQL Server Stretch-Datenbank implementiert hat, um seinen Bedarf an lokalem Datenspeicher sowie seine täglichen laufenden Kosten zu reduzieren.
  
Im Unternehmensspeichersystem von Contoso wird eine große Menge historischer Transaktionsdaten gespeichert, um rechtliche Vorschriften einzuhalten. Die Daten werden außerdem für die Marketingforschung und die BI-Analyse von Ausgabetrends herangezogen. Zudem muss Contoso archivierte Daten in einem zeitaufwendigen Prozess von Magnetbändern wiederherstellen. Als sich die im Contoso-Unternehmensspeichersystem eingesetzte Hardware dem Ende ihres Lebenszyklus näherte, wurde klar, dass ein Austausch sehr teuer werden würde. 
  
Contoso erkannte die geschäftliche Notwendigkeit einer Konsolidierung seiner Rechenzentren und entschied sich für ein Upgrade auf SQL Server 2016, da dieses Betriebssystem die Hybridfunktion „Stretch-Datenbank" mitbringt und nahtlos mit Azure integriert ist. Mithilfe einer Stretch-Datenbank kann Contoso selten verwendete (kalte) Daten in Tabellen aus seinen lokalen Speichern in einen Cloud-Speicher verlagern. Das setzt Kapazität auf den lokalen Festplatten frei und reduziert den Wartungsaufwand. Sowohl häufig verwendete (heiße) Daten als auch kalte Daten werden in denselben Tabellen gespeichert und sind jederzeit verfügbar: für Anwendungen und Benutzer ebenso wie zu Wartungszwecken wie Sicherung und Wiederherstellung. In Abbildung 1 sehen Sie eine Stretch-Datenbank.
  
**Abbildung 1: SQL Server Stretch-Datenbank**

![SQL Server Stretch-Datenbank als Hybriddatenlösung](images/Contoso_Poster/StretchDB01.png)
  
Abbildung 1 zeigt, wie ein SQL-Client T-SQL-Abfragen an einen Server sendet, auf dem SQL Server 2016 ausgeführt wird. Dieser Server leitet die Abfragen anschließend an eine Azure SQL Stretch-Datenbank in Azure-PaaS weiter.
  
Weitere Informationen finden Sie unter [Stretch-Datenbank](https://msdn.microsoft.com/library/dn935011.aspx).
  
Zur Verschiebung der historischen Daten in die Cloud ging Contoso wie folgt vor:
  
1. Datenbankanalyse
    
    Contoso analysierte die Tabellen in den Datenbanken, die in die Cloud verschoben werden sollten, und behob etwaige Probleme. Dank des neuen Stretch Database Advisor hatte das Unternehmen einen vollständigen Überblick über alle Funktionen von SQL Server 2016 und ihre Auswirkungen. Unter anderem half das Tool bei der Identifizierung von Tabellen mit kalten Daten, die für eine Auslagerung in eine Stretch-Datenbank geeignet waren.
    
2. Upgrade
    
    Contoso aktualisierte die SQL-Server im Rechenzentrum seines Pariser Hauptsitzes auf SQL Server 2016.
    
3. Migration kalter Daten in die Cloud
    
    Contoso identifizierte mithilfe von SQL Management Studio alle Datenbanken, die auf die Stretch-Datenbank ausgeweitet werden sollten, sowie alle Tabellen, die zu Instanzen der Stretch-Datenbank in Azure migriert werden sollten. Anschließend verschob SQL Server2016 die historischen Daten im Hintergrund nach und nach in die Stretch-Datenbanken in Azure.
    
Unten sehen Sie die finale Konfiguration für einen einzelnen Server im Pariser Hauptsitz, auf dem SQL Server 2016 ausgeführt wird.
  
**Abbildung 2: Implementierung einer Stretch-Datenbank für einen Server im Contoso-Rechenzentrum**

![Contoso-Konfiguration: SQL Server Stretch-Datenbank für einen einzelnen Computer, auf dem SQL Server ausgeführt wird](images/Contoso_Poster/StretchDB02.png)

  
Abbildung 2 zeigt, wie Benutzerabfragen an einen Anwendungsserver im Contoso-Rechenzentrum in SQL-Abfragen umgewandelt und an eine Azure SQL Stretch-Datenbank in Azure-PaaS weitergeleitet werden.
  
Die Benutzer greifen über die bereits vorhandenen Apps und Abfragen auf die Daten zu. Alle Zugriffsrichtlinien bleiben unverändert. Bandsicherungen wird Contoso zukünftig nicht mehr durchführen müssen. Der Wartungsprozess besteht aus der Sicherung der heißen Daten und, wenn nötig, deren Wiederherstellung.
  
Die Vorteile für Contoso nach der Implementierung einer Stretch-Datenbank:
  
- Reduzierung des Bedarfs an lokalem Datenspeicher um 85 %
    
- Wegfall der Notwendigkeit für eine Aktualisierung des Unternehmensspeichersystems sowie für eine Archivierung auf magnetischen Bändern
    
- Reduzierung der täglichen laufenden Kosten in signifikantem Umfang
    
## <a name="see-also"></a>Weitere Artikel

[Enterprise-Szenarien für die Contoso Corporation](enterprise-scenarios-for-the-contoso-corporation.md)
  
[Contoso in der Microsoft-Cloud](contoso-in-the-microsoft-cloud.md)
  
[Ressourcen zur Cloud-IT-Architektur von Microsoft](microsoft-cloud-it-architecture-resources.md)

[Stretch-Datenbank](https://msdn.microsoft.com/library/dn935011.aspx)
  
[Microsoft-Roadmap Enterprise Cloud: Ressourcen für IT-Entscheidungsträger](https://sway.com/FJ2xsyWtkJc2taRD)




