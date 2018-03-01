---
title: Multi-Geo-Funktionen in OneDrive und SharePoint Online in Office 365
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 1/24/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 094e86f2-9ff0-40ac-af31-28fcaba00c1d
description: "Mit Multi-Geo-Funktionen in OneDrive und SharePoint Online kann Ihrer Organisation die Office 365-Präsenz auf mehreren geografischen Regionen und/oder Ländern innerhalb Ihres vorhandenen Mandanten erweitern."
ms.openlocfilehash: d53da13d5a6a6d5add9da69a3bca9fcdfa39bbd0
ms.sourcegitcommit: 38d43444cf5e03527aa75f670efb2de0f48f847d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/28/2018
---
# <a name="multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-office-365"></a>Multi-Geo-Funktionen in OneDrive und SharePoint Online in Office 365

Mit Multi-Geo-Funktionen in OneDrive und SharePoint Online kann Ihr Unternehmen seine Office 365-Präsenz auf mehrere geografische Regionen und/oder Länder innerhalb des vorhandenen Mandanten erweitern. Dieses Feature ist derzeit in der Vorschau. Wenden Sie sich an Ihr Microsoft-Kontoteam, um Ihr multinationales Unternehmen für die OneDrive Multi-Geo-Vorschau anzumelden.
  
Mit OneDrive Multi-Geo, können Sie bereitstellen und speichern Data-at-Rest in die Geo-Speicherorte, die Sie ausgewählt haben, um Daten vor-Ort-Anforderungen erfüllen und entsperren gleichzeitig Ihre globalen Roll nicht genügend moderne Produktivität Erfahrungen Ihrer Mitarbeiter.
  
Sieht aus wie Multi-Geo-Features für Ihre Organisation profitieren können:
  
- Arbeiten Sie als eine weltweit verbundene Organisation mit einem einzigen Office 365-Mandanten, der mehrere geografische Standorte umfasst.
    
- Erfüllen Sie die Datenresistenz-Anforderungen, indem Sie Daten im Ruhezustand an einem angegebenen geografischen Standort erstellen und hosten.
    
- Statten Sie Ihre Satellitenbenutzer mit der gleichen modernen Produktivität aus wie Ihre Benutzer an einem zentralen Ort.
    
- Bieten Sie Ihren Benutzern die Möglichkeit, den geografischen Standort zu wechseln, während der Zugriff auf ihre Inhalte erhalten bleibt. 
    
- Passen Sie Ihre Freigaberichtlinien dem  jeweiligen geografischen Standort und Ihre Richtlinien zur Verhinderung von Datenlecks dem jeweiligen Unternehmensstandort an.
    
- Legen Sie für jeden geografischen Speicherort eDiscovery-Manager fest und genehmigen Sie die auf Ihren geografischen Speicherort zugeschnittene Regelung von Rechtsfällen.
    
- Wählen Sie einmalige URL-Namespaces (z.B. ContosoEUR.sharepoint.com) für Ihre zusätzlichen geografischen Speicherorte. 
    
- Konsolidieren Sie Ihre regionalen lokalen Daten in Ihrem Office 365-Multi-Geo-Mandanten.
    
Weitere Informationen und eine Demonstration finden Sie unter [Einführung in Multi-Geo-Funktionen in Office 365 und deren Konfiguration](https://youtu.be/3d9-Vt2fArk) und[übersichtsposter für die Serverfarm mit mehreren geografisch](https://technet.microsoft.com/library/dn782272.aspx).
  
In einer Multi-Geo-Konfiguration besteht Ihr Office 365-Mandant aus einem zentralen Standort (auch Standardstandort genannt) und einem oder mehreren Geo-Satellitenstandorten. Das Hauptkonzept von Multi-Geo besteht darin, dass ein einziger Mandant mehrere geografische Standorte umfasst. Die Informationen über geografische Standorte, Gruppen und Benutzer eines Multi-Geo-Mandanten werden in Azure Active Directory (AAD) verwaltet. Da Ihre Mandanteninformationen zentral verwaltet und an jedem geografischen Standort synchronisiert werden, wird das globale Bewusstsein durch das Teilen von Informationen und Erfahrungen im gesamten Unternehmen erhöht.
  
## <a name="sample-multi-geo-tenant-configuration"></a>Beispielkonfiguration Multi-Geo-Mandanten

Mit einem Multi-Geo-Mandanten kann Contoso, mit einem zentralen Standort in Nordamerika, unter der Dachorganisation Contoso.com eine Erweiterung auf geografische Satellitenstandorte in Europa und Australien durchführen. Benutzern mit bevorzugtem Datenspeicherort in Europa steht OneDrive in Europa zur Verfügung, während OneDrive-Benutzern mit bevorzugtem Datenspeicherort in Nordamerika OneDrive in den USA zur Verfügung steht.
  
![Übersicht der ganzen Welt Geo Speicherorte für Contoso und an anderen Standorten verfügbare Geo anzeigen](images/df317ccc-2e53-411d-9211-a5aee63ca1e5.png)
  
## <a name="get-multi-geo-features-in-three-simple-steps"></a>Multi-Geo-Funktionen in drei einfachen Schritten

Die Konfiguration von Multi-Geo ist ganz einfach:
  
1. Aktivieren Sie Ihren Office 365-Mandanten für Multi-Geo.
    
2. Fügen Sie Ihre Satellitenstandorte hinzu.
    
3. Konfigurieren Sie Ihre Benutzerkonten für den entsprechenden Speicherort.
    
## <a name="multi-geo-status-and-availability"></a>Multi-Geo-Status und -Verfügbarkeit

OneDrive Multi-Geo wird derzeit in diesen Regionen und Ländern angeboten:
  
- Asien-Pazifik
    
- Australien
    
- Kanada
    
- Europäische Union (EMEA)
    
- Indien
    
- Japan
    
- Vereinigtes Königreich
    
- Vereinigte Staaten (Nordamerika)
    
- Südkorea
    
> [!NOTE]
> Indien und Korea Süd stehen derzeit nur für Kunden mit Lizenzen und Rechnungsadresse an diesen geografischen Speicherorten zur Verfügung. 
  
Zukünftige geografische Speicherorte:
  
- Frankreich
    
Verfügbare Dienste:
  
- Exchange Online - in Vorschau
    
- OneDrive for Business - in Vorschau
    
- SharePoint Online - in Entwicklung
    

