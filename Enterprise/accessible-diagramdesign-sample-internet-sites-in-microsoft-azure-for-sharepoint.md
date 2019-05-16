---
title: Barrierefreies Diagramm – Entwurfsbeispiel für Internet Websites in Microsoft Azure für SharePoint 2013
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.collection: Ent_O365
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: b91124bc-c7ec-4929-b77c-d6293db9f15e
description: 'Dieser Artikel ist eine barrierefreie Textversion des Diagramms mit dem Namen Entwurfsbeispiel: Internet Websites in Microsoft Azure für SharePoint 2013.'
ms.openlocfilehash: 28cf28739c476638b5775d170508001f2a9730ed
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068797"
---
# <a name="accessible-diagram---design-sample-internet-sites-in-microsoft-azure-for-sharepoint-2013"></a>Zugängliches Diagramm – Entwurfsbeispiel: Internetwebsites in Microsoft Azure für SharePoint 2013

**Zusammenfassung:** Dieser Artikel ist eine barrierefreie Textversion des Diagramms mit dem Namen Entwurfsbeispiel: Internet Websites in Microsoft Azure für SharePoint 2013.
  
Verwenden Sie dieses Entwurfsbeispiel als Ausgangspunkt für eine mit dem Internet verbundene Website in Azure mit SharePoint 2013.
  
Dieses Poster zeigt ein Beispiel dafür, wie Sie die folgenden Aspekte von SharePoint 2013 entwerfen:
  
- Benutzer
    
- Zonen und Authentifizierung
    
- Serverfarm
    
- Verwaltungswebsite
    
- Dienste
    
- Anwendungspools und Webanwendungen
    
- Websitesammlungen
    
- Websites
    
- Inhaltsdatenbanken
    
- Zonen und URLs
    
## <a name="users-zones-and-authentication"></a>Benutzer, Zonen und Authentifizierung

In diesem Entwurf gibt es vier Arten von Benutzerkonten. Jeder Kontotyp ist einer Website für den Zugriff und mit einer Zone zugeordnet, die einen bestimmten Authentifizierungstyp verwendet. 
  
- Anonyme Kunden – anonyme Kunden haben Zugriff über eine Website wie http://www.contoso.com. Die Zone, die Sie verwenden, ist die "Internet Zone/Anonymous", die anonyme Authentifizierung verwendet.
    
- Authentifizierte Kunden – authentifizierte Kunden haben Zugriff über eine Website https://secure.contoso.comwie. Die Zone, die Sie verwenden, ist die "Extranet-Zone/SAML", die Azure Active Directory mit SAML-Authentifizierung verwendet.
    
- Websiteautoren und-Entwickler – Websiteautoren und-Entwickler haben Zugriff über Websites http://authoring.contoso.com:8000 wie http://www.contoso.com:8000oder. Die verwendete Zone ist die "Standardzone/Windows Integrated", die Active Directory-Domänendienste (AD DS) verwendet.
    
- Such Durchforstungskonto – das Such Durchforstungskonto hat Zugriff über Websites http://authoring.contoso.com:8000 wie http://www.contoso.com:8000oder. Die verwendete Zone ist die "Standardzone/Windows Integrated", die AD DS mit Windows-NTLM-Authentifizierung verwendet.
    
## <a name="server-farm"></a>Serverfarm

Die Benutzer greifen über Azure auf die Serverfarm zu. Die Serverfarm enthält einen oder mehrere Webserver.
  
## <a name="administration-site"></a>Verwaltungswebsite

Die Verwaltungswebsite enthält mehrere Anwendungsserver, die mit einem Anwendungspool (Anwendungspool 1 im Beispiel) kommunizieren, der die Website für die Zentraladministration der Webanwendung verwendet. Die Website für die zentral Administration ermöglicht den Zugriff auf Websitesammlungen innerhalb der Organisation.
  
Die Verwaltungswebsite enthält auch SQL-Datenbankserver, die Datenbankserver mit SQL Server sind, die zur Unterstützung von SQL-Clustering, Spiegelung oder AlwaysOn installiert und konfiguriert sind (AlwaysOn gilt nur für SQL Server 2012).
  
## <a name="services"></a>Dienste

Das Entwurfsbeispiel zeigt eine IIS-Website (Internet Informationsdienste), SharePoint-Webdienste. SharePoint-Webdienste enthalten einen Anwendungspool (Anwendungspool 2) mit drei Diensten, Benutzerprofil, Suche und verwalteten Metadaten.
  
Hinweise zu Diensten für Internet Websites:
  
> Verwaltete Metadaten – wählen Sie **Diese Dienstanwendung ist der Standardspeicherort für spaltenspezifische Ausdruckssätze**aus.
    
> App-Verwaltung – es wird nicht empfohlen, apps in einer öffentlich zugänglichen Internet Website in Azure zu verwenden.
    
## <a name="application-pools-and-web-applications"></a>Anwendungspools und Webanwendungen

Die Standardgruppe in Azure zeigt Anwendungs Pool 3, der eine Webanwendung mit dem Namen contoso Sites enthält. Diese pfadbasierte Websitesammlung befindet sich unter http://internal:8000.
  
## <a name="site-collections-and-sites"></a>Websitesammlungen und Websites

Zu den im Anwendungspool enthaltenen Websitesammlungen gehört Folgendes:
  
- Websitesammlung 1 mit Hostnamen für das Crawlen (beispielspeicherorthttp://authoring.contoso.com:8000)
    
- Websitesammlung 2 mit Hostnamen für Abfragen (Beispiel Speicher http://www.contoso.comOrte https://secure.contoso.com,,http://www.contoso.com:8000)
    
- Websitesammlung 3 mit Hostnamen für Abfragen (Beispiel Speicher http://assets.contoso.comOrte https://secureassets.contoso.com,,http://assets.contoso.com:8000)
    
## <a name="content-databases"></a>Inhaltsdatenbanken

Das Beispiel zeigt zwei Inhaltsdatenbanken. Eine ist für die Websitesammlung 1, die für das Crawlen verwendet wird (http://authoring.contoso.com:8000). Die andere ist für die beiden Websitesammlungen 2 und 3 für Abfragen verwendet (http://www.contoso.com, https://secure.contoso.com, http://www.contoso.com:8000, oder http://assets.contoso.com, https://secureassets.contoso.com, http://assets.contoso.com:8000).
  
## <a name="zones-and-urls"></a>Zonen und URLs

Das Beispiel zeigt drei Zonen mit den zugehörigen Lastenausgleich-URLs, die von verschiedenen Benutzerkonten verwendet werden. 
  
Die erste Liste der Zonen und URLs bezieht sich auf die Websitesammlung 1 und enthält die folgenden Informationen:
  
- Benutzer – Websiteautoren
    
- Zone – Standard
    
- URL mit Lastenausgleich-http://authoring.contoso.com:8000
    
Die zweite Liste der Zonen und URLs hat drei verschiedene Arten von Benutzern in drei verschiedenen Zonen. Sie bezieht sich auf die Websitesammlung 2 und enthält die folgenden Informationen:
  
Erste Zone:
  
- Benutzer – Websiteautoren
    
- Zone – Standard
    
- URL mit Lastenausgleich-http://www.contoso.com:8000
    
Zweite Zone:
  
- Benutzer – anonyme Kunden
    
- Zone-Internet
    
- URL mit Lastenausgleich-http://www.contoso.com
    
Dritte Zone:
  
- Benutzer authentifizierte Kunden
    
- Zone-Extranet
    
- URL mit Lastenausgleich-https://secure.contoso.com
    
Die dritte Liste von Zonen und URLs hat drei verschiedene Arten von Benutzern in drei verschiedenen Zonen. Sie bezieht sich auf die Websitesammlung 3 und enthält die folgenden Informationen:
  
Erste Zone:
  
- Benutzer – Websiteautoren
    
- Zone-Internet
    
- URL mit Lastenausgleich-http://assets.contoso.com:8000
    
Zweite Zone:
  
- Benutzer – anonyme Kunden
    
- Zone-Internet
    
- URL mit Lastenausgleich-http://assets.contoso.com
    
Dritte Zone:
  
- Benutzer authentifizierte Kunden
    
- Zone-Extranet
    
- URL mit Lastenausgleich-http://secureassets.contoso.com
    

