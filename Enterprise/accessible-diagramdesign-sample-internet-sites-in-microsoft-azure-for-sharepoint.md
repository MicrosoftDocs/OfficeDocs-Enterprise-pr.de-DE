---
title: "Zugänglich Diagramm - Design Sample Internetsites in Microsoft Azure für SharePoint 2013"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.collection: Ent_O365
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: b91124bc-c7ec-4929-b77c-d6293db9f15e
description: "Dieser Artikel ist eine barrierefreie Textversion des Diagramms „Entwurfsbeispiel“: Internetsites in Microsoft Azure für SharePoint 2013."
ms.openlocfilehash: 0d42a96f80d47b360084557fea47c4155d106d30
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/09/2018
---
# <a name="accessible-diagram---design-sample-internet-sites-in-microsoft-azure-for-sharepoint-2013"></a>Zugängliches Diagramm – Entwurfsbeispiel: Internetwebsites in Microsoft Azure für SharePoint 2013

**Zusammenfassung:** Dieser Artikel ist eine Version verfügbaren Text des Diagramms mit dem Namen Entwurfsbeispiel: Websites in Microsoft Azure für SharePoint 2013.
  
Verwenden Sie in diesem Beispiel Design wird als Ausgangspunkt für eine im Internet veröffentlichte Website in Azure mit SharePoint 2013.
  
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

In diesem Design gibt es vier Typen von Benutzerkonten. Jeder Kontotyp ist mit einer den Zugriff ermöglichenden Website verknüpft und mit einer Zone, die einen spezifischen Authentifizierungstyp nutzt.   
  
- Anonyme Kunden – anonyme Kunden haben über eine Website wie http://www.contoso.com Zugriff. Ist die Zone, die sie verwenden die "Internetzone / anonyme", die anonyme Authentifizierung verwendet.
    
- Authentifiziert Kunden – authentifiziert Kunden haben über eine Website wie https://secure.contoso.com Zugriff. Ist die Zone, die sie verwenden die "Extranetzone / SAML", die Azure Active Directory mit SAML-Authentifizierung verwendet.
    
- Website-Autoren und Entwickler – Websiteautoren und Entwickler haben Sie Zugriff auf Websites wie Http://authoring.contoso.com:8000 oder Http://www.contoso.com:8000. Ist die Zone, die sie verwenden der "Zone" Standard "/ Windows integriert", die Active Directory-Domänendienste (AD DS) verwendet.
    
- Durchforstungskonto – Das Durchforstungskonto hat Zugriff auf Websites wie Http://authoring.contoso.com:8000 oder Http://www.contoso.com:8000. Ist die Zone verwendet die "Zone" Standard "/ Windows integriert", die AD DS mit Windows-NTLM-Authentifizierung verwendet.
    
## <a name="server-farm"></a>Serverfarm

Die Benutzer greifen über Azure auf die Serverfarm zu. Die Serverfarm umfasst mindestens einen Webserver.
  
## <a name="administration-site"></a>Verwaltungswebsite

Die Verwaltungswebsite umfasst mehrere Anwendungsserver, die mit einem Anwendungspool kommunizieren (Anwendungspool 1 im Beispiel), der die Zentraladministrationswebsite der Webanwendung nutzt. Die Zentraladministrationswebsite bietet Zugriff auf Websitesammlungen in der Organisation.
  
Die Verwaltungswebsite umfasst auch SQL-Datenbankserver. Dabei handelt es sich um Datenbankserver, auf denen SQL Server installiert ist und die für die Unterstützung von SQL-Clustering, -Spiegelung oder AlwaysOn (AlwaysOn gilt nur für SQL Server 2012) konfiguriert sind.
  
## <a name="services"></a>Dienste

Das Designbeispiel zeigt eine Internetinformationsdienste(Internet Information Services, IIS)-Website, SharePoint-Webdienste. SharePoint-Webdienste umfasst einen Anwendungspool (Anwendungspool 2) mit drei Diensten, Benutzerprofil, Suche und Verwaltete Metadaten.
  
Hinweise zu Diensten für Internetsites:
  
> Verwaltete Metadaten – Müssen Sie **diese dienstanwendung ist der Standardspeicherort für bestimmte Ausdruckssätze Spalte**auswählen.
    
> App-Management – Wir raten davon ab, Apps auf einer öffentlichen Internetsite in Azure zu verwenden.
    
## <a name="application-pools-and-web-applications"></a>Anwendungspools und Webanwendungen

Die Standardgruppe in Azure zeigt Anwendungspool 3, der eine Webanwendung mit dem Namen „Contoso Sites“ enthält. Diese pfadbasierte Websitesammlung befindet sich unter http://internal:8000.
  
## <a name="site-collections-and-sites"></a>Websitesammlungen und Websites

Die im Anwendungspool enthaltenen Websitesammlungen umfassen Folgendes:
  
- Hostbenannte Websitesammlung 1 für die Durchforstung (Beispielort http://authoring.contoso.com:8000)
    
- Hostbenannte Websitesammlung 2 für Abfragen (Beispielorte http://www.contoso.com, https://secure.contoso.com, http://www.contoso.com:8000)
    
- Hostbenannte Websitesammlung 3 für Abfragen (Beispielorte http://assets.contoso.com, https://secureassets.contoso.com, http://assets.contoso.com:8000)
    
## <a name="content-databases"></a>Inhaltsdatenbanken

Das Beispiel zeigt zwei Inhaltsdatenbanken. Eine ist für die zur Durchforstung verwendete Websitesammlung 1 bestimmt (http://authoring.contoso.com:8000). Die andere ist für die beiden für Abfragen verwendeten Websitesammlungen 2 und 3 bestimmt (http://www.contoso.com, https://secure.contoso.com, http://www.contoso.com:8000 oder http://assets.contoso.com, https://secureassets.contoso.com, http://assets.contoso.com:8000).
  
## <a name="zones-and-urls"></a>Zonen und URLs

Das Beispiel zeigt drei Zonen mit den zugehörigen Lastenausgleich-URLs, die von verschiedenen Benutzerkonten verwendet werden.  
  
Die erste Liste mit Zonen und URLs bezieht sich auf Websitesammlung 1 und enthält die folgenden Informationen:
  
- Benutzer - Websiteautoren
    
- Zone - Standard
    
- Lastenausgleich URL - http://authoring.contoso.com:8000
    
Die zweite Liste mit Zonen und URLs umfasst drei unterschiedliche Benutzertypen in drei unterschiedlichen Zonen. Sie bezieht sich auf Websitesammlung 2 und enthält die folgenden Informationen:
  
Erste Zone:
  
- Benutzer - Websiteautoren
    
- Zone - Standard
    
- Lastenausgleich URL - http://www.contoso.com:8000
    
Zweite Zone:
  
- Benutzer - anonyme Kunden
    
- Zone - Internet
    
- Lastenausgleich-URL - http://www.contoso.com
    
Dritte Zone:
  
- Benutzer - authentifizierten Kunden
    
- Zone - Extranet
    
- Lastenausgleich-URL - https://secure.contoso.com
    
Die Dritte Liste mit Zonen und URLs umfasst drei unterschiedliche Benutzertypen in drei unterschiedlichen Zonen. Sie bezieht sich auf Websitesammlung 3 und enthält die folgenden Informationen:
  
Erste Zone:
  
- Benutzer - Websiteautoren
    
- Zone - Internet
    
- Lastenausgleich URL - http://assets.contoso.com:8000
    
Zweite Zone:
  
- Benutzer - anonyme Kunden
    
- Zone - Internet
    
- Lastenausgleich-URL - http://assets.contoso.com
    
Dritte Zone:
  
- Benutzer - authentifizierten Kunden
    
- Zone - Extranet
    
- Lastenausgleich-URL - http://secureassets.contoso.com
    

