---
title: "Assemblierung in Maßen erforderlich"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 8/22/2017
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Top
ms.custom:
- DecEntMigration
- Ent_Architecture
ms.assetid: ccf1b8b3-0d50-4c66-b314-f480245fad5e
description: "Zusammenfassung: Informieren Sie sich über die Details der Cloudspeicheroptionen, die Sie verwenden können, um eine benutzerdefinierte Speicherlösung zu erstellen."
---

# Assemblierung in Maßen erforderlich

 **Zusammenfassung:** Informieren Sie sich über die Details der Cloudspeicheroptionen, die Sie verwenden können, um eine benutzerdefinierte Speicherlösung zu erstellen.
  
Speicherlösungen vom Typ „Assemblierung in Maßen erforderlich"
  
- Verwendung vorhandener Dienste als Ausgangspunkt für Ihre Speicherlösung
    
- Erfordert ein gewisses Maß an Konfiguration oder Codeerstellung
    
- Kann an Ihre Bedürfnisse angepasst werden
    
In den folgenden Abschnitten werden die Details der einzelnen Speicheroptionen vom Typ „Assemblierung in Maßen erforderlich" beschrieben.
  
## Azure Content Delivery Network

### Features

- Erweiterte und Echtzeitanalysen
    
- Zuverlässige Sicherheitsmaßnahmen gegen DDoS
    
- Automatischer Abruf von Inhalten von einer Azure Website oder einem Azure-Clouddienst nach Einrichten der Integration
    
- Neue Partnerschaft mit Akamai
    
- Möglichkeit zur Verarbeitung plötzlicher Spitzen im Datenverkehr und hoher Auslastungen
    
### Häufige Verwendungsweisen

- Schnelleres und zuverlässigeres Verteilen von Audio, Video, Anwendungen, Images und anderen Dateien an Kunden, indem die den Kunden zunächst gelegenen Server verwendet werden
    
### Grundlegende Speicherszenarien

- Verwalten von Daten
    
- Verwalten von Videos
    
### Ressourcen

Weitere Informationen finden Sie [hier](http://azure.microsoft.com/services/cdn/).
  
Informationen zu den Kosten finden Sie [hier](http://azure.microsoft.com/pricing/details/cdn/).
  
## HdInsight

### Features

- Apache Hadoop-Verteilung unterstützt von der Cloud Ein Data Lake-Dienst
    
- Bei Bedarf auf Petabytes skalierbar
    
- Verarbeiten Sie unstrukturierte und teilstrukturierte Daten Entwickeln Sie in Java, .NET und mehr
    
- Machen Sie Schluss mit dem Kauf und der Wartung von Hardware
    
- Verbinden Sie lokale Hadoop-Cluster mit der Cloud
    
- Flexibilität zum Bereitstellen beliebiger Hadoop-Projekte mithilfe benutzerdefinierter Skripts (z. B. R, Giraph, Solr)
    
### Häufige Verwendungsweisen

- Datenanalyse-Arbeitslasten
    
- Framework zur Datenverarbeitung im Arbeitsspeicher für umfangreiche Daten (Spark)
    
- Streamverarbeitung in Echtzeit (Storm)
    
- Transaktionsverarbeitung (OLTP) von nicht relationalen Daten (HBase) für große Umfänge
    
### Grundlegende Speicherszenarien

- Verwalten von Daten
    
### Ressourcen

Weitere Informationen finden Sie [hier](http://azure.microsoft.com/services/hdinsight/).
  
Informationen zu den Kosten finden Sie [hier](http://azure.microsoft.com/pricing/details/hdinsight/).
  
## Azure SQL-Datenbank

### Features

- Für die Verringerung von Verwaltung und Kosten optimiert
    
- Automatisch hohe Verfügbarkeit, Notfallwiederherstellung und Upgrades
    
- Empfohlen für Organisationen, die Hunderttausende Datenbanken von bis zu 1 TB verwalten
    
- Daten können mithilfe von Shardingtechniken unter Datenbanken aufgeteilt werden, um den Speicherplatz besser zu nutzen
    
- Stretch-Datenbank mit SQL Server 2016
    
### Häufige Verwendungsweisen

- Neue für die Cloud entwickelte Anwendungen mit relationalen Daten
    
- Datenverarbeitung auf schematischen, hoch strukturierten Datasets mit Beziehungen
    
- Räumliche oder Multimedia-Datentypen
    
### Grundlegende Speicherszenarien

- Verwalten von Daten
    
### Elastische Datenbank

Verwenden Sie die praktisch unbegrenzten Ressourcen von Azure SQL-Datenbank in folgenden Fällen:
  
- Die gesamte Datenmenge ist zu groß, um innerhalb der Einschränkungen einer einzelnen Datenbank verarbeitet zu werden.
    
- Der Transaktionsdurchsatz der gesamten Arbeitslast übersteigt die Möglichkeiten einer einzigen Datenbank.
    
- Mandanten erfordern eine physische Trennung voneinander, sodass für jeden Mandanten separate Datenbanken erforderlich sind.
    
- Verschiedene Abschnitte einer Datenbank müssen aus Gründen der Compliance, der Leistung oder aus geopolitischen Gründen an verschiedenen geografischen Orten ausgeführt werden.
    
Bei vertikaler Skalierung können Sie die Leistung einer Azure-Datenbank über die Stufe/Edition oder durch die Verwendung von elastischen Datenbankpools ändern.
  
![Vertikale Skalierung, bereitgestellt von Azure SQL Database.](images/6417c8f2-bd63-4574-a0b3-927a1a2a6e7d.png)
  
Bei horizontaler Skalierung können Sie bei Bedarf neue Datenbanken hinzufügen.
  
![Horizontale Skalierung, bereitgestellt von Azure SQL Database.](images/9b72c009-7691-4349-ba56-4c705a84568d.png)
  
Klicken Sie [hier](https://docs.microsoft.com/azure/sql-database/sql-database-elastic-scale-introduction), um weitere Informationen zu erhalten.
  
### Stretch-Datenbank mit SQL Server 2016

Stretch-Datenbank ist ein Feature von SQL Server-2016, das es Ihnen ermöglicht, archivierte („kalte") Daten, z. B. abgeschlossene Geschäftsdaten in einer umfangreichen Tabelle, die Kundenbestellinformationen enthält, transparent und sicher in eine SQL Stretch-Datenbank in Azure zu verschieben. Wird der Inhalt einer SQL Server-Instanz, einer Datenbank oder sogar einer einzelnen Tabelle in einer Stretch-Datenbank verwendet, ist er eine Kombination aus lokalen Daten auf dem Server mit SQL Server 2016 und Remotedaten in Azure. Daten, die zur Verwendung in einer Stretch-Datenbank auswählbar geworden sind, werden von SQL Server 2016 automatisch in Azure verschoben.
  
![Stretch-Datenbank mit SQL Server 2016.](images/b5360311-8100-42e9-ac62-9b611294a34d.png)
  
 Benutzerabfragen, die Verlaufsdaten enthalten, werden transparent an die Azure SQL Stretch-Datenbank weitergeleitet. Die Abfragen müssen nicht neu geschrieben werden, obwohl die Tabelle gestreckt ist.
  
Stretch-Datenbank stellt eine kostengünstige Möglichkeit für langfristige Speicherung und transparenten Zugriff auf Verlaufsdaten. Außerdem können hiermit Leistungs- und Verfügbarkeitsprobleme behoben werden, die auftreten, wenn die Tabellen sehr umfangreich sind.
  
Klicken Sie [hier](https://msdn.microsoft.com/library/dn935011.aspx), um weitere Informationen zu erhalten.
  
### Ressourcen

Weitere Informationen finden Sie [hier](http://azure.microsoft.com/services/sql-database/).
  
Informationen zu Kosten finden Sie [hier](http://azure.microsoft.com/pricing/details/sql-database/).
  
## Azure Cosmos DB

### Features

- Garantiert niedrige Latenz, SLA mit 99,99 % Verfügbarkeit mit unbegrenzter elastischer Skalierung von Speicher und Durchsatz
    
- Alle Daten werden global über eine beliebige Anzahl Regionen mit transparentem Failover und vier genau definierten Konsistenzebenen repliziert
    
- Alle Daten werden automatisch indiziert, ohne Bedarf an Schemas oder sekundären Indizes
    
- Rich-SQL- und JavaScript-Abfragen und Transaktionen mit mehreren Elementen
    
### Häufige Verwendungsweisen

- IoT, Mobil und Social 
    
- Gaming
    
- Einzelhandel
    
- Content Management
    
### Grundlegende Speicherszenarien

- Verwalten von Daten
    
### Cosmos DB im Vergleich mit Azure Tables und Azure SQL-Datenbank

Gemeinsame Attribute von Cosmos DB, Table Storage und Azure SQL-Datenbank
  
- SLA mit 99,99 % Verfügbarkeit
    
- Vollständig verwaltete Datenbankdienste
    
- Kompatibel gemäß ISO 27001, HIPAA und EU Model Clauses
    
Die folgende Tabelle enthält die unterschiedlichen Attribute von Azure Cosmos DB, Table Storage und Azure SQL-Datenbank
  
![Seltene Attribute der Cosmos DB im Vergleich zu Azure Tables im Vergleich zu Azure SQL-Datenbank](images/cfc81464-6583-44f1-b33e-ceb5549387b4.png)
  
### Ressourcen

Weitere Informationen finden Sie [hier](http://azure.microsoft.com/services/documentdb/).
  
Informationen zu den Kosten finden Sie [hier](http://azure.microsoft.com/pricing/details/documentdb/).
  
## Azure Media Services

### Features

- Skalierbare Live- und VOD-Übermittlung (Video on Demand)
    
- Hohe Verfügbarkeit für Codierung und Streaming
    
- Unterstützt Flash, iOS, Android, HTML5 und Xbox
    
- Studio-zertifizierte DRM-Unterstützung
    
- Monetarisierung von Multimediainhalten
    
- Breites Ökosystem bereits integrierter Partner
    
### Häufige Verwendungsweisen

- Codieren, Speichern und Streamen von Audio- und Videoinhalten in großen Maßstab
    
- Echtzeitstreaming und VOD
    
- Optimierte Verwaltung von Videoinhalten
    
### Die wichtigsten Speicherszenarios

- Verwalten von Videos
    
### Ressourcen

Weitere Informationen finden Sie [hier](http://azure.microsoft.com/services/media-services/).
  
Informationen zu den Kosten finden Sie [hier](http://azure.microsoft.com/pricing/details/media-services/).
  
## Azure Redis Cache

### Features

- Sicherer, dedizierter Redis-Server mit hoher Verfügbarkeit mit von MS verwalteter Datenreplikation und Failover
    
- Für alle Apps empfohlen, die hohen Durchsatz erfordern
    
- In Größen bis zu 530 GB und höher verfügbar (mit Premium und automatischen Sharding)
    
- Redis-Persistenz bewahrt im Arbeitsspeicher zwischengespeicherte Daten dauerhaft auf Azure Storage auf
    
- Mithilfe von Redis-Clustering können Sie bei Skalierung und Durchsatz Maximalwerte erzielen
    
- Verbesserte Sicherheit und Netzwerkisolation mithilfe von Azure Virtual Network-Unterstützung
    
### Häufige Verwendungsweisen

- Umgekehrte Suche nach Daten in beliebigen Speicherdiensten in Azure, wie etwa Cosmos DB und Azure SQL-Datenbank
    
- Synchronisierte Inhalte aus anderen Datenspeichern
    
### Die wichtigsten Speicherszenarios

- Zwischenspeichern von Daten
    
- Nachrichtenbroker für Anwendungen mit hohem Durchsatz
    
### Ressourcen

Weitere Informationen finden Sie [hier](http://azure.microsoft.com/services/cache/).
  
Informationen zu den Kosten finden Sie [hier](http://azure.microsoft.com/pricing/details/cache/).
  
## SQL Server auf einer Azure-VM

### Features

- SQL Server wird als installierte Anwendung auf einem virtuellen Azure-Computer ausgeführt
    
- Verwenden Sie ein Katalogimage mit installiertem SQL Server, oder nutzen Sie Ihre eigene SQL Server-Lizenz
    
### Häufige Verwendungsweisen

- Verwalten von Daten für Anwendungen
    
### Grundlegende Speicherszenarien

- Verwalten von Daten
    
- 
    
### Ressourcen

Weitere Informationen finden Sie [hier](http://azure.microsoft.com/services/virtual-machines/).
  
Informationen zu den Kosten finden Sie [hier](http://azure.microsoft.com/pricing/details/virtual-machines/).
  
## StorSimple

### Features

- Skalierbarer hybrider SAN-Speicher auf Unternehmensniveau mit SSD und HDD im lokalen hybriden Speicherarray mit Cloudspeicher als integrierter Erweiterung der Lösung
    
- Inlinededuplizierung, Komprimierung, automatisches Tiering und Verschlüsselung unstrukturierter und teilstrukturierter Daten
    
- Automatischer Schutz von Offsitedaten mithilfe von Cloudmomentaufnahmen
    
- Sehr effiziente, ortsunabhängige Notfallwiederherstellung
    
- Datenmobilität für Enterprise-Daten mit der virtuellen StorSimple-Anwendung in Azure
    
### Häufige Verwendungsweisen

- Verwalten von zunehmenden Datenvolumen in Dateifreigaben, Archiven und anderen Datenrepositorys
    
- Schutz von Offsitedaten und Notfallwiederherstellung für Dateifreigaben, virtuellen Computern, SQL und SharePoint (mithilfe von Remote Blob Storage)
    
- Nutzung von Cloudmomentaufnahmen zum Klonen von Daten in Azure und Steigern der geschäftlichen Flexibilität
    
### Grundlegende Speicherszenarien

- Verwalten von Daten
    
- Zusammenarbeit
    
### Ressourcen

Weitere Informationen finden Sie [hier](http://azure.microsoft.com/services/storsimple/).
  
Informationen zu Kosten finden Sie [hier](http://azure.microsoft.com/pricing/details/storsimple/).
  
## Azure SQL Data Warehouse

### Features

- Elastisches Data Warehouse, das bis zu Petabytes skalieren kann Bis zu 32 gleichzeitige Abfragen
    
- Verwalten Sie große Mengen von strukturierten Daten mit schneller Analyse Lassen Sie die Rechenkapazität dynamisch innerhalb von Sekunden anwachsen oder schrumpfen
    
- Unterstützt transparente Datenverschlüsselung
    
- Alle 8 Stunden 7 Tage lang gesichert
    
### Häufige Verwendungsweisen

- Umsatzberichte
    
- Verwendungsberichte
    
- Große Datenmengen
    
### Grundlegende Speicherszenarien

- Verwalten von Daten
    
### Ressourcen

Weitere Informationen finden Sie [hier](http://azure.microsoft.com/services/sql-data-warehouse/).
  
Informationen zu Kosten finden Sie [hier](http://azure.microsoft.com/pricing/details/sql-data-warehouse/).
  
## Azure Data Lake Store

### Features

- Repository mit Hyperskalierung für Big Data-Analyseworkloads
    
- Ein Hadoop Distributed File System für die Cloud
    
- Keine festgelegten Grenzen für die Dateigröße
    
- Keine festgelegten Grenzen für die Kontogröße
    
- Unstrukturierte und strukturierte Daten in ihrem nativen Format
    
- Massiver Durchsatz zur Steigerung der Analyseleistung
    
- Hohe Dauerhaftigkeit, Verfügbarkeit und Zuverlässigkeit (Unternehmens-SLA von 99,9 %, Support rund um die Uhr)
    
- Azure Active Directory-Zugriffssteuerung
    
### Häufige Verwendungsweisen

- Unternehmensweites Repository zum Speichern jeder Art von Daten an einem zentralen Ort
    
### Grundlegende Speicherszenarien

- Verwalten von Daten
    
### Ressourcen

Weitere Informationen finden Sie [hier](http://azure.microsoft.com/services/data-lake-store/).
  
Informationen zu den Kosten finden Sie [hier](http://azure.microsoft.com/pricing/details/data-lake-store/).
  
## Nächster Schritt

Sehen Sie sich die Cloudspeicheroptionen vom Typ „[Von Grund auf neu aufgebaut](build-from-the-ground-up.md)" an.
  
## See Also

#### 

[Microsoft-Cloud-Speicher für Enterprise-Architekten](microsoft-cloud-storage-for-enterprise-architects.md)
  
[Ressourcen zur Cloud-IT-Architektur von Microsoft](microsoft-cloud-it-architecture-resources.md)
#### 

[Enterprise-Cloud-Roadmap von Microsoft: Ressourcen für IT-Entscheidungsträger](https://sway.com/FJ2xsyWtkJc2taR)

