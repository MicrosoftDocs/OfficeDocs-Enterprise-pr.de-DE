---
title: Übersicht über die Contoso Corporation
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
ms.assetid: 1de16e29-ac2e-40b5-bf13-9301a51e16a8
description: 'Zusammenfassung: Verstehen der Contoso Corporation als ein Unternehmen und die stufenweise seiner weltweit Büros.'
ms.openlocfilehash: 30a6dd23271fbbd5599053b934e6a1af9dc14d12
ms.sourcegitcommit: 8fcf6fd9f0c45a5445654ef811410fca3f4f5512
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2018
---
# <a name="overview-of-the-contoso-corporation"></a>Übersicht über die Contoso Corporation

 **Zusammenfassung:** Verstehen der Contoso Corporation als ein Unternehmen und die stufenweise seiner weltweit Büros.
  
Die Contoso Corporation ist ein globales Unternehmen mit Zentrale in Paris, Frankreich. Es handelt sich um einen Mischkonzern aus Herstellungs-, Vertriebs- und Supportunternehmen mit mehr als 100.000 Produkten.
  
  
## <a name="the-contoso-corporation"></a>Die Contoso Corporation

Contoso weltweit Unternehmen verfügt über Büros in den folgenden Speicherorten:
  
**Abbildung 1: Contoso Büros auf der ganzen Welt**

![Die weltweiten Büros der Contoso Corporation](images/Contoso_Poster/Contoso_WW_Org.png)

  
Abbildung 1 zeigt die Unternehmenszentrale in Paris und Regionalstellen und Zweigstellen auf unterschiedlichen Kontinenten.
  
Contoso Büros auf der ganzen Welt führen Sie einen Entwurf für eine dreistufige.
  
- Zentrale
    
    Der Contoso Corporation Hauptsitz ist eine große Unternehmen Campus am Stadtrand Paris mit Dutzende von Gebäude für engineering, Fertigung und administrativen Funktionen. Alle Contoso Rechenzentren und Internet Anwesenheitsinformationen sind in der Unternehmenszentrale Paris untergebracht werden.
    
    Die Zentrale hat 15.000 Mitarbeiter.

    
- Regionalstellen

    
    Regionalstellen bedienen mit 60 % Verkaufs- und Supportmitarbeitern eine bestimmte Region. Jede Regionalstelle ist mit der Zentrale in Paris mit einer WAN-Verbindung mit hoher Bandbreite verbunden.  
    
    Jede Regionalstelle hat im Durchschnitt 2.000 Arbeitskräfte.

    
- Zweigstellen

    
    Zweigstellen 80 % Sales enthalten und support-Mitarbeiter und physische und vor-Ort-Anwesenheitsstatus für Contoso-Kunden in wichtigen Städte oder Sub Regionen. Jede Zweigstelle ist mit einem regionalen Hub mit einer WAN-Verbindung hoher Bandbreite verbunden.
    
    Jede Zweigstelle hat im Durchschnitt 250 Mitarbeiter.

    
25 % der Contoso Mitarbeiter ist Mobile nur einen höheren Prozentsatz nur für Mobile Mitarbeiter in den regionalen Hubs und Zweigstellen. Bietet eine bessere Unterstützung für Mobile nur Mitarbeiter ist ein wichtiger Geschäftsziel für Contoso.
  
## <a name="elements-of-contosos-implementation-of-the-microsoft-cloud"></a>Elemente des Contoso Implementierung von Microsoft cloud

Contoso IT-konstruiert haben die folgenden Elemente identifiziert, bei der Planung für die Annahme der Microsoft Cloud-angeboten.
  
- Netzwerk
    
    Netzwerke enthält die Verbindung mit Microsoft Cloud-angeboten und genügend Bandbreite für leistungsfähige unter belasungsspitzen abgefangen werden. Einige Connectivity ist über lokale internetverbindungen und andere werden in der Contoso VPN-Infrastruktur.
    
    Weitere Informationen finden Sie unter Details des Posters [Microsoft Cloud Networking für Enterprise-konstruiert](microsoft-cloud-networking-for-enterprise-architects.md) .
   
- Identität
    
    Contoso verwendet eine Windows Server Active Directory-Gesamtstruktur für die interne Identitätsanbieter und auch die Verbindung mit Drittanbietern für Kunden und Partnern. Contoso muss den internen Satz von Konten für die Microsoft Cloud-angeboten nutzen. Zugriff auf die Cloud-basierten apps für Kunden und Partner muss Drittanbieter-Identitätsanbieter sowie nutzen.
    
    Weitere Informationen finden Sie unter Details des Posters [Microsoft Cloudidentität für Enterprise-konstruiert](microsoft-cloud-it-architecture-resources.md#identity) .
    
- Sicherheit
    
    Sicherheit für cloudbasierte Identitäten und Daten muss Datenschutz, Verwaltung mit Administratorrechten, Berücksichtigung von Bedrohungen und die Implementierung von Datengovernance und Sicherheitsrichtlinien enthalten.

    
    Weitere Informationen finden Sie unter Details des Posters [Microsoft Cloud-Sicherheit für Enterprise-konstruiert](http://aka.ms/cloudarchsecurity) .
    
- Verwaltung
    
    Die Verwaltung für cloudbasierte Apps und SaaS-Arbeitslasten erfordert, dass Einstellungen, Daten, Konten, Richtlinien und Berechtigungen verwaltet sowie der gegenwärtige Zustand und die gegenwärtige Leistung überwacht werden können.
 Vorhandene Serververwaltungstools werden dazu verwendet, virtuelle Computer in Azure IaaS zu verwalten.
    
## <a name="see-also"></a>Siehe auch

[Contoso in der Microsoft-Cloud](contoso-in-the-microsoft-cloud.md)
  
[Ressourcen zur Cloud-IT-Architektur von Microsoft](microsoft-cloud-it-architecture-resources.md)

[Enterprise-Cloud-Roadmap von Microsoft: Ressourcen für IT-Entscheidungsträger](https://sway.com/FJ2xsyWtkJc2taRD)
 


