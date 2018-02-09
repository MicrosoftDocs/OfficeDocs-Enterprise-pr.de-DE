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
# <a name="accessible-diagram---design-sample-internet-sites-in-microsoft-azure-for-sharepoint-2013"></a><span data-ttu-id="1bd61-103">Zugängliches Diagramm – Entwurfsbeispiel: Internetwebsites in Microsoft Azure für SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="1bd61-103">Accessible diagram - Design sample: Internet sites in Microsoft Azure for SharePoint 2013</span></span>

<span data-ttu-id="1bd61-104">**Zusammenfassung:** Dieser Artikel ist eine Version verfügbaren Text des Diagramms mit dem Namen Entwurfsbeispiel: Websites in Microsoft Azure für SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="1bd61-104">**Summary:** This article is an accessible text version of the diagram named Design sample: Internet sites in Microsoft Azure for SharePoint 2013.</span></span>
  
<span data-ttu-id="1bd61-105">Verwenden Sie in diesem Beispiel Design wird als Ausgangspunkt für eine im Internet veröffentlichte Website in Azure mit SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="1bd61-105">Use this design example as a starting point for an Internet-facing site in Azure using SharePoint 2013.</span></span>
  
<span data-ttu-id="1bd61-106">Dieses Poster zeigt ein Beispiel dafür, wie Sie die folgenden Aspekte von SharePoint 2013 entwerfen:</span><span class="sxs-lookup"><span data-stu-id="1bd61-106">This poster shows an example of how to design the following aspects of SharePoint 2013:</span></span>
  
- <span data-ttu-id="1bd61-107">Benutzer</span><span class="sxs-lookup"><span data-stu-id="1bd61-107">Users</span></span>
    
- <span data-ttu-id="1bd61-108">Zonen und Authentifizierung</span><span class="sxs-lookup"><span data-stu-id="1bd61-108">Zones and authentication</span></span>
    
- <span data-ttu-id="1bd61-109">Serverfarm</span><span class="sxs-lookup"><span data-stu-id="1bd61-109">Server farm</span></span>
    
- <span data-ttu-id="1bd61-110">Verwaltungswebsite</span><span class="sxs-lookup"><span data-stu-id="1bd61-110">Administration site</span></span>
    
- <span data-ttu-id="1bd61-111">Dienste</span><span class="sxs-lookup"><span data-stu-id="1bd61-111">Services</span></span>
    
- <span data-ttu-id="1bd61-112">Anwendungspools und Webanwendungen</span><span class="sxs-lookup"><span data-stu-id="1bd61-112">Application pools and web applications</span></span>
    
- <span data-ttu-id="1bd61-113">Websitesammlungen</span><span class="sxs-lookup"><span data-stu-id="1bd61-113">Site collections</span></span>
    
- <span data-ttu-id="1bd61-114">Websites</span><span class="sxs-lookup"><span data-stu-id="1bd61-114">Sites</span></span>
    
- <span data-ttu-id="1bd61-115">Inhaltsdatenbanken</span><span class="sxs-lookup"><span data-stu-id="1bd61-115">Content databases</span></span>
    
- <span data-ttu-id="1bd61-116">Zonen und URLs</span><span class="sxs-lookup"><span data-stu-id="1bd61-116">Zones and URLs</span></span>
    
## <a name="users-zones-and-authentication"></a><span data-ttu-id="1bd61-117">Benutzer, Zonen und Authentifizierung</span><span class="sxs-lookup"><span data-stu-id="1bd61-117">Users, zones and authentication</span></span>

<span data-ttu-id="1bd61-p101">In diesem Design gibt es vier Typen von Benutzerkonten. Jeder Kontotyp ist mit einer den Zugriff ermöglichenden Website verknüpft und mit einer Zone, die einen spezifischen Authentifizierungstyp nutzt.  </span><span class="sxs-lookup"><span data-stu-id="1bd61-p101">There are four types of user accounts in this design. Each type of account is associated with a site for access and with a zone that uses a specific type of authentication.</span></span> 
  
- <span data-ttu-id="1bd61-120">Anonyme Kunden – anonyme Kunden haben über eine Website wie http://www.contoso.com Zugriff. Ist die Zone, die sie verwenden die "Internetzone / anonyme", die anonyme Authentifizierung verwendet.</span><span class="sxs-lookup"><span data-stu-id="1bd61-120">Anonymous customers — Anonymous customers have access through a site such as http://www.contoso.com. The zone they use is the "Internet zone / anonymous", which uses anonymous authentication.</span></span>
    
- <span data-ttu-id="1bd61-121">Authentifiziert Kunden – authentifiziert Kunden haben über eine Website wie https://secure.contoso.com Zugriff. Ist die Zone, die sie verwenden die "Extranetzone / SAML", die Azure Active Directory mit SAML-Authentifizierung verwendet.</span><span class="sxs-lookup"><span data-stu-id="1bd61-121">Authenticated customers — Authenticated customers have access through a site such as https://secure.contoso.com. The zone they use is the "Extranet zone / SAML", which uses Azure Active Directory with SAML authentication.</span></span>
    
- <span data-ttu-id="1bd61-p102">Website-Autoren und Entwickler – Websiteautoren und Entwickler haben Sie Zugriff auf Websites wie Http://authoring.contoso.com:8000 oder Http://www.contoso.com:8000. Ist die Zone, die sie verwenden der "Zone" Standard "/ Windows integriert", die Active Directory-Domänendienste (AD DS) verwendet.</span><span class="sxs-lookup"><span data-stu-id="1bd61-p102">Site authors and developers — Site authors and developers have access through sites such as http://authoring.contoso.com:8000 or http://www.contoso.com:8000. The zone they use is the "Default zone / Windows integrated", which uses Active Directory Domain Services (AD DS).</span></span>
    
- <span data-ttu-id="1bd61-p103">Durchforstungskonto – Das Durchforstungskonto hat Zugriff auf Websites wie Http://authoring.contoso.com:8000 oder Http://www.contoso.com:8000. Ist die Zone verwendet die "Zone" Standard "/ Windows integriert", die AD DS mit Windows-NTLM-Authentifizierung verwendet.</span><span class="sxs-lookup"><span data-stu-id="1bd61-p103">Search Crawl Account — The search crawl account has access through sites such as http://authoring.contoso.com:8000 or http://www.contoso.com:8000. The zone it uses is the "Default zone / Windows integrated", which uses AD DS with Windows NTLM authentication.</span></span>
    
## <a name="server-farm"></a><span data-ttu-id="1bd61-126">Serverfarm</span><span class="sxs-lookup"><span data-stu-id="1bd61-126">Server farm</span></span>

<span data-ttu-id="1bd61-p104">Die Benutzer greifen über Azure auf die Serverfarm zu. Die Serverfarm umfasst mindestens einen Webserver.</span><span class="sxs-lookup"><span data-stu-id="1bd61-p104">The users access the server farm through Azure. The server farm contains one or more Web servers.</span></span>
  
## <a name="administration-site"></a><span data-ttu-id="1bd61-129">Verwaltungswebsite</span><span class="sxs-lookup"><span data-stu-id="1bd61-129">Administration site</span></span>

<span data-ttu-id="1bd61-p105">Die Verwaltungswebsite umfasst mehrere Anwendungsserver, die mit einem Anwendungspool kommunizieren (Anwendungspool 1 im Beispiel), der die Zentraladministrationswebsite der Webanwendung nutzt. Die Zentraladministrationswebsite bietet Zugriff auf Websitesammlungen in der Organisation.</span><span class="sxs-lookup"><span data-stu-id="1bd61-p105">The administration site contains several application servers, which communicate with an Application Pool (Application Pool 1 in the example) that uses the web application Central Administration Site. The Central Administration Site provides access to site collections within the organization.</span></span>
  
<span data-ttu-id="1bd61-132">Die Verwaltungswebsite umfasst auch SQL-Datenbankserver. Dabei handelt es sich um Datenbankserver, auf denen SQL Server installiert ist und die für die Unterstützung von SQL-Clustering, -Spiegelung oder AlwaysOn (AlwaysOn gilt nur für SQL Server 2012) konfiguriert sind.</span><span class="sxs-lookup"><span data-stu-id="1bd61-132">The administration site also contains SQL Database servers, which are database servers with SQL Server installed and configured to support SQL clustering, mirroring, or AlwaysOn (AlwaysOn applies to SQL Server 2012 only).</span></span>
  
## <a name="services"></a><span data-ttu-id="1bd61-133">Dienste</span><span class="sxs-lookup"><span data-stu-id="1bd61-133">Services</span></span>

<span data-ttu-id="1bd61-p106">Das Designbeispiel zeigt eine Internetinformationsdienste(Internet Information Services, IIS)-Website, SharePoint-Webdienste. SharePoint-Webdienste umfasst einen Anwendungspool (Anwendungspool 2) mit drei Diensten, Benutzerprofil, Suche und Verwaltete Metadaten.</span><span class="sxs-lookup"><span data-stu-id="1bd61-p106">The design example shows an Internet Information Services (IIS) website, SharePoint Web Services. SharePoint Web Services contains an application pool (Application Pool 2) with three services, User Profile, Search, and Managed Metadata.</span></span>
  
<span data-ttu-id="1bd61-136">Hinweise zu Diensten für Internetsites:</span><span class="sxs-lookup"><span data-stu-id="1bd61-136">Notes on Services for Internet sites:</span></span>
  
> <span data-ttu-id="1bd61-137">Verwaltete Metadaten – Müssen Sie **diese dienstanwendung ist der Standardspeicherort für bestimmte Ausdruckssätze Spalte**auswählen.</span><span class="sxs-lookup"><span data-stu-id="1bd61-137">Managed Metadata — Be sure to select **This service application is the default storage location for column specific term sets**.</span></span>
    
> <span data-ttu-id="1bd61-138">App-Management – Wir raten davon ab, Apps auf einer öffentlichen Internetsite in Azure zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="1bd61-138">App Management — We do not recommend using apps in a public-facing Internet site in Azure.</span></span>
    
## <a name="application-pools-and-web-applications"></a><span data-ttu-id="1bd61-139">Anwendungspools und Webanwendungen</span><span class="sxs-lookup"><span data-stu-id="1bd61-139">Application pools and web applications</span></span>

<span data-ttu-id="1bd61-p107">Die Standardgruppe in Azure zeigt Anwendungspool 3, der eine Webanwendung mit dem Namen „Contoso Sites“ enthält. Diese pfadbasierte Websitesammlung befindet sich unter http://internal:8000.</span><span class="sxs-lookup"><span data-stu-id="1bd61-p107">The Default Group in Azure shows Application Pool 3, which contains a web application named Contoso Sites. This path-based site collection is located at http://internal:8000.</span></span>
  
## <a name="site-collections-and-sites"></a><span data-ttu-id="1bd61-142">Websitesammlungen und Websites</span><span class="sxs-lookup"><span data-stu-id="1bd61-142">Site collections and sites</span></span>

<span data-ttu-id="1bd61-143">Die im Anwendungspool enthaltenen Websitesammlungen umfassen Folgendes:</span><span class="sxs-lookup"><span data-stu-id="1bd61-143">The site collections contained in the application pool include:</span></span>
  
- <span data-ttu-id="1bd61-144">Hostbenannte Websitesammlung 1 für die Durchforstung (Beispielort http://authoring.contoso.com:8000)</span><span class="sxs-lookup"><span data-stu-id="1bd61-144">Host-named site collection 1 for crawling (example location http://authoring.contoso.com:8000)</span></span>
    
- <span data-ttu-id="1bd61-145">Hostbenannte Websitesammlung 2 für Abfragen (Beispielorte http://www.contoso.com, https://secure.contoso.com, http://www.contoso.com:8000)</span><span class="sxs-lookup"><span data-stu-id="1bd61-145">Host-named site collection 2 for queries (sample locations http://www.contoso.com, https://secure.contoso.com, http://www.contoso.com:8000)</span></span>
    
- <span data-ttu-id="1bd61-146">Hostbenannte Websitesammlung 3 für Abfragen (Beispielorte http://assets.contoso.com, https://secureassets.contoso.com, http://assets.contoso.com:8000)</span><span class="sxs-lookup"><span data-stu-id="1bd61-146">Host-named site collection 3 for queries (sample locations http://assets.contoso.com, https://secureassets.contoso.com, http://assets.contoso.com:8000)</span></span>
    
## <a name="content-databases"></a><span data-ttu-id="1bd61-147">Inhaltsdatenbanken</span><span class="sxs-lookup"><span data-stu-id="1bd61-147">Content databases</span></span>

<span data-ttu-id="1bd61-p108">Das Beispiel zeigt zwei Inhaltsdatenbanken. Eine ist für die zur Durchforstung verwendete Websitesammlung 1 bestimmt (http://authoring.contoso.com:8000). Die andere ist für die beiden für Abfragen verwendeten Websitesammlungen 2 und 3 bestimmt (http://www.contoso.com, https://secure.contoso.com, http://www.contoso.com:8000 oder http://assets.contoso.com, https://secureassets.contoso.com, http://assets.contoso.com:8000).</span><span class="sxs-lookup"><span data-stu-id="1bd61-p108">The example shows two content databases. One is for the site collection 1 used for crawling (http://authoring.contoso.com:8000). The other is for the two site collections 2 and 3 used for queries (http://www.contoso.com, https://secure.contoso.com, http://www.contoso.com:8000, or http://assets.contoso.com, https://secureassets.contoso.com, http://assets.contoso.com:8000).</span></span>
  
## <a name="zones-and-urls"></a><span data-ttu-id="1bd61-151">Zonen und URLs</span><span class="sxs-lookup"><span data-stu-id="1bd61-151">Zones and URLs</span></span>

<span data-ttu-id="1bd61-152">Das Beispiel zeigt drei Zonen mit den zugehörigen Lastenausgleich-URLs, die von verschiedenen Benutzerkonten verwendet werden. </span><span class="sxs-lookup"><span data-stu-id="1bd61-152">The example shows three zones with the associated load-balanced URLs that are used by different user accounts.</span></span> 
  
<span data-ttu-id="1bd61-153">Die erste Liste mit Zonen und URLs bezieht sich auf Websitesammlung 1 und enthält die folgenden Informationen:</span><span class="sxs-lookup"><span data-stu-id="1bd61-153">The first list of zones and URLs is related to site collection 1, and it contains the following information:</span></span>
  
- <span data-ttu-id="1bd61-154">Benutzer - Websiteautoren</span><span class="sxs-lookup"><span data-stu-id="1bd61-154">Users - Site authors</span></span>
    
- <span data-ttu-id="1bd61-155">Zone - Standard</span><span class="sxs-lookup"><span data-stu-id="1bd61-155">Zone - Default</span></span>
    
- <span data-ttu-id="1bd61-156">Lastenausgleich URL - http://authoring.contoso.com:8000</span><span class="sxs-lookup"><span data-stu-id="1bd61-156">Load-balanced URL - http://authoring.contoso.com:8000</span></span>
    
<span data-ttu-id="1bd61-p109">Die zweite Liste mit Zonen und URLs umfasst drei unterschiedliche Benutzertypen in drei unterschiedlichen Zonen. Sie bezieht sich auf Websitesammlung 2 und enthält die folgenden Informationen:</span><span class="sxs-lookup"><span data-stu-id="1bd61-p109">The second list of zones and URLs has three different types of users in three different zones. It is related to site collection 2, and it contains the following information:</span></span>
  
<span data-ttu-id="1bd61-159">Erste Zone:</span><span class="sxs-lookup"><span data-stu-id="1bd61-159">First zone:</span></span>
  
- <span data-ttu-id="1bd61-160">Benutzer - Websiteautoren</span><span class="sxs-lookup"><span data-stu-id="1bd61-160">Users - Site authors</span></span>
    
- <span data-ttu-id="1bd61-161">Zone - Standard</span><span class="sxs-lookup"><span data-stu-id="1bd61-161">Zone - Default</span></span>
    
- <span data-ttu-id="1bd61-162">Lastenausgleich URL - http://www.contoso.com:8000</span><span class="sxs-lookup"><span data-stu-id="1bd61-162">Load-balanced URL - http://www.contoso.com:8000</span></span>
    
<span data-ttu-id="1bd61-163">Zweite Zone:</span><span class="sxs-lookup"><span data-stu-id="1bd61-163">Second zone:</span></span>
  
- <span data-ttu-id="1bd61-164">Benutzer - anonyme Kunden</span><span class="sxs-lookup"><span data-stu-id="1bd61-164">Users - Anonymous customers</span></span>
    
- <span data-ttu-id="1bd61-165">Zone - Internet</span><span class="sxs-lookup"><span data-stu-id="1bd61-165">Zone - Internet</span></span>
    
- <span data-ttu-id="1bd61-166">Lastenausgleich-URL - http://www.contoso.com</span><span class="sxs-lookup"><span data-stu-id="1bd61-166">Load-balanced URL - http://www.contoso.com</span></span>
    
<span data-ttu-id="1bd61-167">Dritte Zone:</span><span class="sxs-lookup"><span data-stu-id="1bd61-167">Third zone:</span></span>
  
- <span data-ttu-id="1bd61-168">Benutzer - authentifizierten Kunden</span><span class="sxs-lookup"><span data-stu-id="1bd61-168">Users - Authenticated customers</span></span>
    
- <span data-ttu-id="1bd61-169">Zone - Extranet</span><span class="sxs-lookup"><span data-stu-id="1bd61-169">Zone - Extranet</span></span>
    
- <span data-ttu-id="1bd61-170">Lastenausgleich-URL - https://secure.contoso.com</span><span class="sxs-lookup"><span data-stu-id="1bd61-170">Load-balanced URL - https://secure.contoso.com</span></span>
    
<span data-ttu-id="1bd61-p110">Die Dritte Liste mit Zonen und URLs umfasst drei unterschiedliche Benutzertypen in drei unterschiedlichen Zonen. Sie bezieht sich auf Websitesammlung 3 und enthält die folgenden Informationen:</span><span class="sxs-lookup"><span data-stu-id="1bd61-p110">The third list of zones and URLs has three different types of users in three different zones. It is related to site collection 3, and it contains the following information:</span></span>
  
<span data-ttu-id="1bd61-173">Erste Zone:</span><span class="sxs-lookup"><span data-stu-id="1bd61-173">First zone:</span></span>
  
- <span data-ttu-id="1bd61-174">Benutzer - Websiteautoren</span><span class="sxs-lookup"><span data-stu-id="1bd61-174">Users - Site authors</span></span>
    
- <span data-ttu-id="1bd61-175">Zone - Internet</span><span class="sxs-lookup"><span data-stu-id="1bd61-175">Zone - Internet</span></span>
    
- <span data-ttu-id="1bd61-176">Lastenausgleich URL - http://assets.contoso.com:8000</span><span class="sxs-lookup"><span data-stu-id="1bd61-176">Load-balanced URL - http://assets.contoso.com:8000</span></span>
    
<span data-ttu-id="1bd61-177">Zweite Zone:</span><span class="sxs-lookup"><span data-stu-id="1bd61-177">Second zone:</span></span>
  
- <span data-ttu-id="1bd61-178">Benutzer - anonyme Kunden</span><span class="sxs-lookup"><span data-stu-id="1bd61-178">Users - Anonymous customers</span></span>
    
- <span data-ttu-id="1bd61-179">Zone - Internet</span><span class="sxs-lookup"><span data-stu-id="1bd61-179">Zone - Internet</span></span>
    
- <span data-ttu-id="1bd61-180">Lastenausgleich-URL - http://assets.contoso.com</span><span class="sxs-lookup"><span data-stu-id="1bd61-180">Load-balanced URL - http://assets.contoso.com</span></span>
    
<span data-ttu-id="1bd61-181">Dritte Zone:</span><span class="sxs-lookup"><span data-stu-id="1bd61-181">Third zone:</span></span>
  
- <span data-ttu-id="1bd61-182">Benutzer - authentifizierten Kunden</span><span class="sxs-lookup"><span data-stu-id="1bd61-182">Users - Authenticated customers</span></span>
    
- <span data-ttu-id="1bd61-183">Zone - Extranet</span><span class="sxs-lookup"><span data-stu-id="1bd61-183">Zone - Extranet</span></span>
    
- <span data-ttu-id="1bd61-184">Lastenausgleich-URL - http://secureassets.contoso.com</span><span class="sxs-lookup"><span data-stu-id="1bd61-184">Load-balanced URL - http://secureassets.contoso.com</span></span>
    

