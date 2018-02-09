---
title: Von Grund auf neu aufgebaut
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 84348d0c-d9d1-4a98-9b99-8433f9b70e45
description: "Zusammenfassung: Informieren Sie sich auf dem Satz von Cloud Speicher Bausteine, zu denen Sie zum Erstellen Ihrer eigenen Speicherdienst oder eine bestimmte Lösung verwenden können."
ms.openlocfilehash: be7ea3e7526115f1a983ec89f2afeb5d130daee1
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/09/2018
---
# <a name="build-from-the-ground-up"></a>Von Grund auf neu aufgebaut

 **Zusammenfassung:** Rufen Sie die Details zu den Satz von Cloud Speicher Bausteine, zu denen Sie zum Erstellen Ihrer eigenen Speicherdienst oder eine bestimmte Lösung verwenden können.
  
Speicherlösungen vom Typ „Von Grund auf neu aufgebaut“ haben folgende Eigenschaften:
  
- Können Sie Ihre eigene speicherlösung von Grund auf zu erstellen. 
    
- Erfordert die Programmierung mithilfe der REST-APIs.
    
- Geben Sie die optimale Anpassung und Flexibilität.
    
In den folgenden Abschnitten werden die Details der einzelnen „Von Grund auf neu aufgebaut“-Speicheroptionen beschrieben.
  
## <a name="azure-storage-files"></a>Azure Storage (Files)

### <a name="features"></a>Features

- Vereinfacht das Verbringen von Legacyanwendungen in die Cloud
    
- Bevorzugt Blobspeicher für neue Anwendungen
    
- Kann aus einem virtuellen Azure-Computer eingebunden werden
    
- Kann lokal mit SMB 3.0 eingebunden werden
    
- Funktioniert mit Linux und Windows
    
- Unterstützt keine Azure AD-basierte Authentifizierung oder ACLs (Azure-Speicher-Konto-Schlüsseln Authentifizierung und autorisierten Zugriff auf die Dateifreigabe bereitstellen)
    
### <a name="common-uses"></a>Häufige Verwendungsweisen

- Migrieren von Legacyanwendungen in die Cloud, die auf Dateifreigaben beruhen
    
- Gemeinsam verwendete Entwicklungs- und Testtools
    
- Verteilte Apps können Protokolle, Diagnosedaten und Absturzabbilder speichern
    
### <a name="key-storage-scenarios"></a>Grundlegende Speicherszenarien

- Dateisicherung
    
### <a name="resources"></a>Ressourcen

Weitere Informationen finden Sie [hier](https://msdn.microsoft.com/library/azure/dn166972.aspx).
  
Informationen zu den Kosten finden Sie [hier](http://azure.microsoft.com/pricing/details/storage/).
  
## <a name="azure-storage-blobs"></a>Azure Storage (Blobs)

### <a name="features"></a>Features

- Jedes Storage-Konto kann bis zu 500 TB enthalten (ein Abonnement kann mehrere Speicherkonten müssen)
    
- Speicherkonten sind in Containern organisiert, die Blobs enthalten können und auf die Sicherheit angewendet werden kann
    
- Blockblobs sind für das Streamen und Speichern von Cloudobjekten mit bis zu 200 GB optimiert
    
- Seitenblobs sind für das Darstellen von PaaS-Datenträgern bis zu 1 TB optimiert und unterstützen ungeordnete Schreibvorgänge
    
- Anfügeblobs sind für Anfügevorgänge bis zu 195 GB optimiert
    
- Premium Storage bietet aufgrund von SSD-Speicher schnellere IOPS
    
### <a name="common-uses"></a>Häufige Verwendungsweisen

- Sicherungen von Dateien, Computern, Datenbanken und Geräte Bildern und Text für Webanwendungen
    
- Konfigurationsdaten für Cloudanwendungen
    
- Große Datenmengen, wie etwa Protokolle und andere große Datasets
    
- Azure verwendet Blobspeicher für seine eigenen Dienste, wie HDInsight und Datenträger von virtuellen Computern
    
### <a name="key-storage-scenarios"></a>Grundlegende Speicherszenarien

- Verwalten von Daten
    
### <a name="resources"></a>Ressourcen

Weitere Informationen finden Sie [hier](https://msdn.microsoft.com/library/azure/dd179376.aspx).
  
Informationen zu den Kosten finden Sie [hier](http://azure.microsoft.com/pricing/details/storage/).
  
## <a name="azure-storage-queues"></a>Azure Storage (Queues)

### <a name="features"></a>Features

- Speicherkonten können eine beliebige Anzahl Warteschlangen enthalten
    
- Warteschlangen können eine beliebige Anzahl Nachrichten enthalten (bis das Speicherkonto voll ist)
    
- Nachrichten in Warteschlangen werden nach 7 Tagen automatisch gelöscht, wenn sie nicht abgerufen und von einer Anwendung gelöscht werden
    
- Nachrichten können bis zu 64 KB groß sein.
    
- Auf Speicherkontoebene gesichert
    
- Warteschlangen sind für die Übergabe von Steuerungsnachrichten vorgesehen, nicht von Rohdaten
    
### <a name="common-uses"></a>Häufige Verwendungsweisen

- Erstellen eines Backlogs der Arbeit für die asynchrone Verarbeitung
    
- Verarbeiten von Protokollnachrichten
    
- Entkoppeln von Anwendungen
    
### <a name="key-storage-scenarios"></a>Grundlegende Speicherszenarien

- Verteilen von Ereignissen
    
### <a name="resources"></a>Ressourcen

Weitere Informationen finden Sie [hier](https://msdn.microsoft.com/library/azure/dd179353.aspx).
  
Informationen zu den Kosten finden Sie [hier](http://azure.microsoft.com/pricing/details/storage/).
  
## <a name="azure-storage-tables"></a>Azure Storage (Tables)

### <a name="features"></a>Features

- Optimal für teilstrukturierte Datasets geeignet
    
- Normalerweise geringere Kosten als traditionelles SQL
    
- Sehr schnell, wenn Abfragen für Schlüssel beeinträchtigt, wenn Wert Abfragen
    
- Hochgradig skalierbar; beliebige Mengen von Tabellen bis zur Grenze des Speicherkontos
    
- Zugriff über REST-API, eingeschränktes oData-Protokoll, .NET
    
- Werte müssen serialisiert werden
    
### <a name="common-uses"></a>Häufige Verwendungsweisen

- Benutzerdaten für Webanwendungen
    
- Adressbücher
    
- Geräteinformationen
    
### <a name="key-storage-scenarios"></a>Grundlegende Speicherszenarien

- Verwalten von Daten
    
### <a name="resources"></a>Ressourcen

Weitere Informationen finden Sie [hier](https://msdn.microsoft.com/library/azure/dd179463.aspx).
  
Informationen zu den Kosten finden Sie [hier](http://azure.microsoft.com/pricing/details/storage/).
  
## <a name="microsoft-azure-storage-recommendations"></a>Microsoft Azure Storage-Empfehlungen

Beachten Sie beim Entwerfen Ihrer benutzerdefinierten Speicherlösung mit Azure Storage Folgendes:
  
- Nutzen Sie mehrere Speicherkonten, um größere Skalierbarkeit zu erzielen, entweder in Richtung Größe (> 100 TB) oder Durchsatz (> 5.000 Operationen pro Sekunde).
    
- Planen Sie die Möglichkeit zum Hinzufügen weiterer Speicherkonten als Änderung der Konfiguration, nicht des Codes.
    
- Wählen Sie sorgfältig Partitionierungsfunktionen für Tabellenspeicher aus, um das gewünschte Maß an Einfüge- und Abfrageleistung zu erreichen.
    
- Wählen Sie kurze Spaltennamen für Tabelleneigenschaften aus, da die Metadaten (Eigenschaftsnamen) In-Band gespeichert werden (die Spaltennamen werden bei der maximalen Zeilengröße von 1 MB berücksichtigt).
    
- Führen Sie nach Möglichkeit Batchvorgänge im Speicher aus.
    
- Speichern Sie Informationen in der Konfigurationsdatenbank konsequent in einem verteilten Cache zwischen.
    
- Wenn Anwendungsleistung oder Zuverlässigkeit von der Verfügbarkeit eines bestimmten Datensegments im Cache abhängt, sollte Ihre Anwendung eingehende Anforderungen bis zum Abschluss der Vorauffüllung des Caches abweisen.
    
- Partitionieren Sie die Daten entweder vertikal (nach Tabellen) oder horizontal (über mehrere Shards segmentierte Tabellen), um die Auslastung auf mehrere Datenbanken zu verteilen.
    
## <a name="see-also"></a>Weitere Artikel

[Microsoft-Cloud-Speicher für Enterprise-Architekten](microsoft-cloud-storage-for-enterprise-architects.md)
  
[Ressourcen zur Cloud-IT-Architektur von Microsoft](microsoft-cloud-it-architecture-resources.md)

[Enterprise-Cloud-Roadmap von Microsoft: Ressourcen für IT-Entscheidungsträger](https://sway.com/FJ2xsyWtkJc2taRD)



