---
title: IT-Infrastruktur und Anforderungen von Contoso
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
ms.assetid: 5d6a58b8-bec3-4629-9737-8733c7b7ec92
description: "Zusammenfassung: Hier erfahren Sie die grundlegende Struktur des Contoso lokale IT-Infrastruktur und wie die Geschäftsabläufe durch Cloudlösungen von Microsoft erfüllt werden können muss."
ms.openlocfilehash: b8282c4bd04448266bc68e65f95aaaff0a7a5db8
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/09/2018
---
# <a name="contosos-it-infrastructure-and-needs"></a>IT-Infrastruktur und Anforderungen von Contoso

 **Zusammenfassung:** Verstehen der grundlegenden Struktur des Contoso lokale IT-Infrastruktur und wie die Geschäftsabläufe durch Cloudlösungen von Microsoft erfüllt werden können muss.
  
Contoso ist dabei, von der lokalen zentralen IT-Infrastruktur auf eine cloudeinschließende Infrastruktur umzustellen, die aus cloudbasierten persönlichen Produktivitätsarbeitslasten, Anwendungen und Hybridszenarien besteht.

  
## <a name="contosos-existing-it-infrastructure"></a>Contosos vorhandene IT-Infrastruktur


Contoso nutzt eine weitestgehend zentrale lokale IT-Infrastruktur mit Anwendungsrechenzentren in der Pariser Zentrale.

  
**Abbildung 1: Contoso vorhandenen IT-Infrastruktur**

![Contosos vorhandene IT-Infrastruktur
](images/Contoso_Poster/Existing_IT.png)
  
Abbildung 1 zeigt eine Unternehmenszentrale mit Anwendungsrechenzentren, einer DMZ und Internet.
  
Geben Contoso DMZ verschiedene Sätze von Servern:
  
- Remotezugriff auf das Contoso-Intranet und Webproxyfunktion für Mitarbeiter in der Pariser Zentrale
    
- Hosting der öffentlichen Contoso-Website, über die Kunden Produkte, Teile oder Zubehör bestellen können
    
- Hosting für das Contoso-Partnerextranet für die Kommunikation und Zusammenarbeit mit Partnern
    
## <a name="contosos-business-needs"></a>Contoso geschäftlichen Anforderungen

Nachfolgend sehen Sie die Geschäftsanforderungen von Contoso in der Reihenfolge ihrer Priorität:
  
1. Einhalten von regionalen gesetzlichen Vorschriften
    
    Um Strafen zu verhindern und gute Beziehungen zu lokalen Behörden beizubehalten, muss Contoso die Einhaltung von Vorschriften zur Datenspeicherung- und -verschlüsselung sicherstellen.

    
2. Verbessern der Verwaltung von Lieferanten und partner
    
    Das Partnerextranet ist in die Jahre gekommen und teuer in der Wartung. Contoso möchte es durch eine cloudbasierte Lösung ersetzen, für die Verbundauthentifizierung verwendet wird.

    
3. Verbessern der Produktivität der mobilen Mitarbeiter, Gerätemanagement und access
    
    Contoso Mobile-only Belegschaft wird erweitert und benötigt Gerätemanagement zum Schutz des geistigen Eigentums und effizienter Zugriff auf Ressourcen zu gewährleisten.
    
4. RAS-Infrastruktur reduzieren
    
    Durch Verschieben von Ressourcen, auf die häufig von Remotearbeitskräften zugegriffen wird, in die Cloud spart Contoso Geld, indem die Kosten für Wartung und Support der Remotezugriffslösung verringert werden.

    
5. Lokale Rechenzentren verkleinern
    
    Die Contoso-Rechenzentren umfassen Hunderte von Servern, von denen einige für ältere oder Archivierungsfunktionen genutzt werden, was dazu führt, dass IT-Mitarbeiter davon abgehalten werden, Arbeitslasten mit hohem Geschäftswert zu betreuen.

    
6. Vertikales Skalieren Netzwerke und der Speicherung Ressourcen für die Verarbeitung Ende des Quartal
    
    Quartalsabschlüsse und Prognoseverarbeitung zusammen mit Bestandsverwaltung erfordern kurzfristig mehr Server und Speicher.

    
## <a name="mapping-contosos-business-needs-to-microsofts-cloud-offerings"></a>Zuordnen Contosos Business muss Cloudlösungen von Microsoft

Basierend auf einer Analyse der Microsoft-Cloudangebote hat die IT-Abteilung von Contoso die folgende Zuordnung festgelegt:
  
|**Software as a Service (SaaS)**|**Plattform als Dienst (Azure PaaS)**|**Infrastructure as a Service (Azure IaaS)**|
|:-----|:-----|:-----|
|**Office 365:** Primäre persönliche und Gruppe produktivitätsanwendungen in der Cloud. <br/> Geschäftsanforderungen: 1 3 5  <br/> |Hosten von Sales und Dokumente und Informationssysteme mithilfe von Cloud-basierten apps unterstützen.  <br/> Geschäftliche Anforderung: 3  <br/> |Verschieben Sie Archivierung sowie älterer Systeme zu Cloud-basierten Servern.  <br/> Geschäftliche Anforderung: 5  <br/> |
|**Dynamics 365:** Verwenden Sie die Cloud-basierten Kunden und Hersteller-Verwaltung. In der DMZ extranet Partner zu entfernen.<br/> Geschäftliche Anforderung: 2  <br/> |Mobile Anwendungen sind cloudbasiert, statt von Pariser Datenzentren bereitgestellt zu werden.
  <br/> Geschäftliche Anforderungen: 3 4  <br/> |Migrieren von wenig verwendeten Apps und Daten aus lokalen Rechenzentren.  <br/> Geschäftliche Anforderung: 5  <br/> |
|**Intune/zur Abstimmung:** Verwalten von iOS und Android-Geräte. <br/> Geschäftliche Anforderung: 3  <br/> ||Hinzufügen von temporären Servern und temporärem Speicher für Anforderungen aus einem Quartalsabschluss.
  <br/> Geschäftliche Anforderung: 6  <br/> |
   
## <a name="see-also"></a>Weitere Artikel

[Contoso in der Microsoft-Cloud](contoso-in-the-microsoft-cloud.md)
  
[Ressourcen zur Cloud-IT-Architektur von Microsoft](microsoft-cloud-it-architecture-resources.md)

[Enterprise-Cloud-Roadmap von Microsoft: Ressourcen für IT-Entscheidungsträger](https://sway.com/FJ2xsyWtkJc2taRD)


