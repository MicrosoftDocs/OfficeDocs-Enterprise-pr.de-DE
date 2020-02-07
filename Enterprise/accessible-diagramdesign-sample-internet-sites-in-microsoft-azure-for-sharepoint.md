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
f1.keywords:
- NOCSH
description: 'Dieser Artikel ist eine barrierefreie Textversion des Diagramms mit dem Namen Design Sample: Internet Websites in Microsoft Azure für SharePoint 2013.'
ms.openlocfilehash: b3669304fee6b7a89bc5d1bde96c39c496122d48
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/07/2020
ms.locfileid: "41843796"
---
# <a name="accessible-diagram---design-sample-internet-sites-in-microsoft-azure-for-sharepoint-2013"></a>Zugängliches Diagramm – Entwurfsbeispiel: Internetwebsites in Microsoft Azure für SharePoint 2013

**Zusammenfassung:** Dieser Artikel ist eine barrierefreie Textversion des Diagramms mit dem Namen Design Sample: Internet Websites in Microsoft Azure für SharePoint 2013.
  
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

Es gibt vier Arten von Benutzerkonten in diesem Entwurf. Jeder Kontotyp ist einer Website für den Zugriff und mit einer Zone zugeordnet, die einen bestimmten Authentifizierungstyp verwendet. 
  
- Anonyme Kunden – anonyme Kunden haben Zugriff über eine Website wie https://www.contoso.com. Die Zone, die Sie verwenden, ist die "Internet Zone/anonym", die die anonyme Authentifizierung verwendet.
    
- Authentifizierte Kunden – authentifizierte Kunden haben Zugriff über eine Website https://secure.contoso.comwie. Die Zone, die Sie verwenden, ist die "Extranet-Zone/SAML", die Azure-Active Directory mit SAML-Authentifizierung verwendet.
    
- Websiteautoren und-Entwickler – Websiteautoren und-Entwickler haben Zugriff über Websites https://authoring.contoso.com:8000 wie https://www.contoso.com:8000oder. Die Zone, die Sie verwenden, ist die "Default Zone/Windows Integrated", die Active Directory-Domänendienste (AD DS) verwendet.
    
- Such Durchforstungskonto: das Such Durchforstungskonto hat Zugriff über Websites https://authoring.contoso.com:8000 wie https://www.contoso.com:8000oder. Die verwendete Zone ist die "Default Zone/Windows Integrated", die AD DS mit der Windows-NTLM-Authentifizierung verwendet.
    
## <a name="server-farm"></a>Serverfarm

Die Benutzer greifen über Azure auf die Serverfarm zu. Die Serverfarm enthält einen oder mehrere Webserver.
  
## <a name="administration-site"></a>Verwaltungswebsite

Die Verwaltungswebsite enthält mehrere Anwendungsserver, die mit einem Anwendungspool (Anwendungspool 1 im Beispiel) kommunizieren, der die Website für die Zentraladministration der Webanwendung verwendet. Die Website für die zentral Administration ermöglicht den Zugriff auf Websitesammlungen innerhalb der Organisation.
  
Die Verwaltungswebsite enthält auch SQL-Datenbankserver, bei denen es sich um Datenbankserver mit SQL Server, die für die Unterstützung von SQL-Clustering, Spiegelung oder AlwaysOn installiert und konfiguriert sind (AlwaysOn gilt nur für SQL Server 2012).
  
## <a name="services"></a>Dienste

Das Entwurfsbeispiel zeigt eine Internet Information Services (IIS) Website, SharePoint Webdienste. SharePoint Webdienste enthält einen Anwendungspool (Anwendungspool 2) mit drei Diensten, Benutzerprofil, Suche und verwalteten Metadaten.
  
Hinweise zu Diensten für Internet Websites:
  
> Verwaltete Metadaten – stellen Sie sicher, dass **Diese Dienstanwendung der Standardspeicherort für spaltenspezifische Ausdruckssätze ist**.
    
> App-Verwaltung – es wird nicht empfohlen, apps in einer öffentlich zugänglichen Internet Website in Azure zu verwenden.
    
## <a name="application-pools-and-web-applications"></a>Anwendungspools und Webanwendungen

Die Standardgruppe in Azure zeigt den Anwendungs Pool 3, der eine Webanwendung mit dem Namen "Contoso-Websites" enthält. Diese pfadbasierte Websitesammlung befindet sich unter https://internal:8000.
  
## <a name="site-collections-and-sites"></a>Websitesammlungen und Websites

Die im Anwendungspool enthaltenen Websitesammlungen umfassen Folgendes:
  
- Websitesammlung 1 mit Hostnamen für das Crawlen (beispielspeicherorthttps://authoring.contoso.com:8000)
    
- Websitesammlung 2 mit Hostnamen für Abfragen (Beispiel Speicher https://www.contoso.comOrte https://secure.contoso.com,https://www.contoso.com:8000)
    
- Websitesammlung 3 mit Hostnamen für Abfragen (Beispiel Speicher https://assets.contoso.comOrte https://secureassets.contoso.com,https://assets.contoso.com:8000)
    
## <a name="content-databases"></a>Inhaltsdatenbanken

Das Beispiel zeigt zwei Inhaltsdatenbanken. Einer ist für die Websitesammlung 1, die für die durchhttps://authoring.contoso.com:8000)Forstung verwendet wird (. Die andere gilt für die beiden Websitesammlungen 2 und 3, die für Abfragenhttps://www.contoso.comverwendet https://secure.contoso.comwerden https://www.contoso.com:8000(, https://assets.contoso.com, https://secureassets.contoso.com, https://assets.contoso.com:8000)oder,,.
  
## <a name="zones-and-urls"></a>Zonen und URLs

Das Beispiel zeigt drei Zonen mit den zugeordneten Lastenausgleichs-URLs, die von unterschiedlichen Benutzerkonten verwendet werden. 
  
Die erste Liste mit Zonen und URLs bezieht sich auf Websitesammlung 1 und enthält die folgenden Informationen:
  
- Benutzer – Websiteautoren
    
- Zone – Standard
    
- URL mit Lastenausgleich-https://authoring.contoso.com:8000
    
Die zweite Liste mit Zonen und URLs besteht aus drei unterschiedlichen Benutzertypen in drei verschiedenen Zonen. Sie bezieht sich auf Websitesammlung 2 und enthält die folgenden Informationen:
  
Erste Zone:
  
- Benutzer – Websiteautoren
    
- Zone – Standard
    
- URL mit Lastenausgleich-https://www.contoso.com:8000
    
Zweite Zone:
  
- Benutzer – anonyme Kunden
    
- Zone-Internet
    
- URL mit Lastenausgleich-https://www.contoso.com
    
Dritte Zone:
  
- Benutzer authentifizierte Kunden
    
- Zone-Extranet
    
- URL mit Lastenausgleich-https://secure.contoso.com
    
Die dritte Liste von Zonen und URLs verfügt über drei verschiedene Typen von Benutzern in drei verschiedenen Zonen. Sie bezieht sich auf Websitesammlung 3 und enthält die folgenden Informationen:
  
Erste Zone:
  
- Benutzer – Websiteautoren
    
- Zone-Internet
    
- URL mit Lastenausgleich-https://assets.contoso.com:8000
    
Zweite Zone:
  
- Benutzer – anonyme Kunden
    
- Zone-Internet
    
- URL mit Lastenausgleich-https://assets.contoso.com
    
Dritte Zone:
  
- Benutzer authentifizierte Kunden
    
- Zone-Extranet
    
- URL mit Lastenausgleich-https://secureassets.contoso.com
    

