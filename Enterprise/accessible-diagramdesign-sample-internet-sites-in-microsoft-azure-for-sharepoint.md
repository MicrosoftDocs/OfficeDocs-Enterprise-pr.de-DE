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
description: 'Dieser Artikel ist eine barrierefreie Textversion des Diagramms mit dem Namen Design Sample: Internet Websites in Microsoft Azure für SharePoint 2013.'
ms.openlocfilehash: 52ae615cbdc6a355155e54e36bc6a3d733d84869
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2019
ms.locfileid: "38027629"
---
# <a name="accessible-diagram---design-sample-internet-sites-in-microsoft-azure-for-sharepoint-2013"></a><span data-ttu-id="8f7de-103">Zugängliches Diagramm – Entwurfsbeispiel: Internetwebsites in Microsoft Azure für SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="8f7de-103">Accessible diagram - Design sample: Internet sites in Microsoft Azure for SharePoint 2013</span></span>

<span data-ttu-id="8f7de-104">**Zusammenfassung:** Dieser Artikel ist eine barrierefreie Textversion des Diagramms mit dem Namen Design Sample: Internet Websites in Microsoft Azure für SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="8f7de-104">**Summary:** This article is an accessible text version of the diagram named Design sample: Internet sites in Microsoft Azure for SharePoint 2013.</span></span>
  
<span data-ttu-id="8f7de-105">Verwenden Sie dieses Entwurfsbeispiel als Ausgangspunkt für eine mit dem Internet verbundene Website in Azure mit SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="8f7de-105">Use this design example as a starting point for an Internet-facing site in Azure using SharePoint 2013.</span></span>
  
<span data-ttu-id="8f7de-106">Dieses Poster zeigt ein Beispiel dafür, wie Sie die folgenden Aspekte von SharePoint 2013 entwerfen:</span><span class="sxs-lookup"><span data-stu-id="8f7de-106">This poster shows an example of how to design the following aspects of SharePoint 2013:</span></span>
  
- <span data-ttu-id="8f7de-107">Benutzer</span><span class="sxs-lookup"><span data-stu-id="8f7de-107">Users</span></span>
    
- <span data-ttu-id="8f7de-108">Zonen und Authentifizierung</span><span class="sxs-lookup"><span data-stu-id="8f7de-108">Zones and authentication</span></span>
    
- <span data-ttu-id="8f7de-109">Serverfarm</span><span class="sxs-lookup"><span data-stu-id="8f7de-109">Server farm</span></span>
    
- <span data-ttu-id="8f7de-110">Verwaltungswebsite</span><span class="sxs-lookup"><span data-stu-id="8f7de-110">Administration site</span></span>
    
- <span data-ttu-id="8f7de-111">Dienste</span><span class="sxs-lookup"><span data-stu-id="8f7de-111">Services</span></span>
    
- <span data-ttu-id="8f7de-112">Anwendungspools und Webanwendungen</span><span class="sxs-lookup"><span data-stu-id="8f7de-112">Application pools and web applications</span></span>
    
- <span data-ttu-id="8f7de-113">Websitesammlungen</span><span class="sxs-lookup"><span data-stu-id="8f7de-113">Site collections</span></span>
    
- <span data-ttu-id="8f7de-114">Websites</span><span class="sxs-lookup"><span data-stu-id="8f7de-114">Sites</span></span>
    
- <span data-ttu-id="8f7de-115">Inhaltsdatenbanken</span><span class="sxs-lookup"><span data-stu-id="8f7de-115">Content databases</span></span>
    
- <span data-ttu-id="8f7de-116">Zonen und URLs</span><span class="sxs-lookup"><span data-stu-id="8f7de-116">Zones and URLs</span></span>
    
## <a name="users-zones-and-authentication"></a><span data-ttu-id="8f7de-117">Benutzer, Zonen und Authentifizierung</span><span class="sxs-lookup"><span data-stu-id="8f7de-117">Users, zones and authentication</span></span>

<span data-ttu-id="8f7de-118">Es gibt vier Arten von Benutzerkonten in diesem Entwurf.</span><span class="sxs-lookup"><span data-stu-id="8f7de-118">There are four types of user accounts in this design.</span></span> <span data-ttu-id="8f7de-119">Jeder Kontotyp ist einer Website für den Zugriff und mit einer Zone zugeordnet, die einen bestimmten Authentifizierungstyp verwendet.</span><span class="sxs-lookup"><span data-stu-id="8f7de-119">Each type of account is associated with a site for access and with a zone that uses a specific type of authentication.</span></span> 
  
- <span data-ttu-id="8f7de-120">Anonyme Kunden – anonyme Kunden haben Zugriff über eine Website wie https://www.contoso.com.</span><span class="sxs-lookup"><span data-stu-id="8f7de-120">Anonymous customers — Anonymous customers have access through a site such as https://www.contoso.com.</span></span> <span data-ttu-id="8f7de-121">Die Zone, die Sie verwenden, ist die "Internet Zone/anonym", die die anonyme Authentifizierung verwendet.</span><span class="sxs-lookup"><span data-stu-id="8f7de-121">The zone they use is the "Internet zone / anonymous", which uses anonymous authentication.</span></span>
    
- <span data-ttu-id="8f7de-122">Authentifizierte Kunden – authentifizierte Kunden haben Zugriff über eine Website https://secure.contoso.comwie.</span><span class="sxs-lookup"><span data-stu-id="8f7de-122">Authenticated customers — Authenticated customers have access through a site such as https://secure.contoso.com.</span></span> <span data-ttu-id="8f7de-123">Die Zone, die Sie verwenden, ist die "Extranet-Zone/SAML", die Azure-Active Directory mit SAML-Authentifizierung verwendet.</span><span class="sxs-lookup"><span data-stu-id="8f7de-123">The zone they use is the "Extranet zone / SAML", which uses Azure Active Directory with SAML authentication.</span></span>
    
- <span data-ttu-id="8f7de-124">Websiteautoren und-Entwickler – Websiteautoren und-Entwickler haben Zugriff über Websites https://authoring.contoso.com:8000 wie https://www.contoso.com:8000oder.</span><span class="sxs-lookup"><span data-stu-id="8f7de-124">Site authors and developers — Site authors and developers have access through sites such as https://authoring.contoso.com:8000 or https://www.contoso.com:8000.</span></span> <span data-ttu-id="8f7de-125">Die Zone, die Sie verwenden, ist die "Default Zone/Windows Integrated", die Active Directory-Domänendienste (AD DS) verwendet.</span><span class="sxs-lookup"><span data-stu-id="8f7de-125">The zone they use is the "Default zone / Windows integrated", which uses Active Directory Domain Services (AD DS).</span></span>
    
- <span data-ttu-id="8f7de-126">Such Durchforstungskonto: das Such Durchforstungskonto hat Zugriff über Websites https://authoring.contoso.com:8000 wie https://www.contoso.com:8000oder.</span><span class="sxs-lookup"><span data-stu-id="8f7de-126">Search Crawl Account — The search crawl account has access through sites such as https://authoring.contoso.com:8000 or https://www.contoso.com:8000.</span></span> <span data-ttu-id="8f7de-127">Die verwendete Zone ist die "Default Zone/Windows Integrated", die AD DS mit der Windows-NTLM-Authentifizierung verwendet.</span><span class="sxs-lookup"><span data-stu-id="8f7de-127">The zone it uses is the "Default zone / Windows integrated", which uses AD DS with Windows NTLM authentication.</span></span>
    
## <a name="server-farm"></a><span data-ttu-id="8f7de-128">Serverfarm</span><span class="sxs-lookup"><span data-stu-id="8f7de-128">Server farm</span></span>

<span data-ttu-id="8f7de-129">Die Benutzer greifen über Azure auf die Serverfarm zu.</span><span class="sxs-lookup"><span data-stu-id="8f7de-129">The users access the server farm through Azure.</span></span> <span data-ttu-id="8f7de-130">Die Serverfarm enthält einen oder mehrere Webserver.</span><span class="sxs-lookup"><span data-stu-id="8f7de-130">The server farm contains one or more Web servers.</span></span>
  
## <a name="administration-site"></a><span data-ttu-id="8f7de-131">Verwaltungswebsite</span><span class="sxs-lookup"><span data-stu-id="8f7de-131">Administration site</span></span>

<span data-ttu-id="8f7de-132">Die Verwaltungswebsite enthält mehrere Anwendungsserver, die mit einem Anwendungspool (Anwendungspool 1 im Beispiel) kommunizieren, der die Website für die Zentraladministration der Webanwendung verwendet.</span><span class="sxs-lookup"><span data-stu-id="8f7de-132">The administration site contains several application servers, which communicate with an Application Pool (Application Pool 1 in the example) that uses the web application Central Administration Site.</span></span> <span data-ttu-id="8f7de-133">Die Website für die zentral Administration ermöglicht den Zugriff auf Websitesammlungen innerhalb der Organisation.</span><span class="sxs-lookup"><span data-stu-id="8f7de-133">The Central Administration Site provides access to site collections within the organization.</span></span>
  
<span data-ttu-id="8f7de-134">Die Verwaltungswebsite enthält auch SQL-Datenbankserver, bei denen es sich um Datenbankserver mit SQL Server, die für die Unterstützung von SQL-Clustering, Spiegelung oder AlwaysOn installiert und konfiguriert sind (AlwaysOn gilt nur für SQL Server 2012).</span><span class="sxs-lookup"><span data-stu-id="8f7de-134">The administration site also contains SQL Database servers, which are database servers with SQL Server installed and configured to support SQL clustering, mirroring, or AlwaysOn (AlwaysOn applies to SQL Server 2012 only).</span></span>
  
## <a name="services"></a><span data-ttu-id="8f7de-135">Dienste</span><span class="sxs-lookup"><span data-stu-id="8f7de-135">Services</span></span>

<span data-ttu-id="8f7de-136">Das Entwurfsbeispiel zeigt eine Internet Information Services (IIS) Website, SharePoint Webdienste.</span><span class="sxs-lookup"><span data-stu-id="8f7de-136">The design example shows an Internet Information Services (IIS) website, SharePoint Web Services.</span></span> <span data-ttu-id="8f7de-137">SharePoint Webdienste enthält einen Anwendungspool (Anwendungspool 2) mit drei Diensten, Benutzerprofil, Suche und verwalteten Metadaten.</span><span class="sxs-lookup"><span data-stu-id="8f7de-137">SharePoint Web Services contains an application pool (Application Pool 2) with three services, User Profile, Search, and Managed Metadata.</span></span>
  
<span data-ttu-id="8f7de-138">Hinweise zu Diensten für Internet Websites:</span><span class="sxs-lookup"><span data-stu-id="8f7de-138">Notes on Services for Internet sites:</span></span>
  
> <span data-ttu-id="8f7de-139">Verwaltete Metadaten – stellen Sie sicher, dass **Diese Dienstanwendung der Standardspeicherort für spaltenspezifische Ausdruckssätze ist**.</span><span class="sxs-lookup"><span data-stu-id="8f7de-139">Managed Metadata — Be sure to select **This service application is the default storage location for column specific term sets**.</span></span>
    
> <span data-ttu-id="8f7de-140">App-Verwaltung – es wird nicht empfohlen, apps in einer öffentlich zugänglichen Internet Website in Azure zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="8f7de-140">App Management — We do not recommend using apps in a public-facing Internet site in Azure.</span></span>
    
## <a name="application-pools-and-web-applications"></a><span data-ttu-id="8f7de-141">Anwendungspools und Webanwendungen</span><span class="sxs-lookup"><span data-stu-id="8f7de-141">Application pools and web applications</span></span>

<span data-ttu-id="8f7de-142">Die Standardgruppe in Azure zeigt den Anwendungs Pool 3, der eine Webanwendung mit dem Namen "Contoso-Websites" enthält.</span><span class="sxs-lookup"><span data-stu-id="8f7de-142">The Default Group in Azure shows Application Pool 3, which contains a web application named Contoso Sites.</span></span> <span data-ttu-id="8f7de-143">Diese pfadbasierte Websitesammlung befindet sich unter https://internal:8000.</span><span class="sxs-lookup"><span data-stu-id="8f7de-143">This path-based site collection is located at https://internal:8000.</span></span>
  
## <a name="site-collections-and-sites"></a><span data-ttu-id="8f7de-144">Websitesammlungen und Websites</span><span class="sxs-lookup"><span data-stu-id="8f7de-144">Site collections and sites</span></span>

<span data-ttu-id="8f7de-145">Die im Anwendungspool enthaltenen Websitesammlungen umfassen Folgendes:</span><span class="sxs-lookup"><span data-stu-id="8f7de-145">The site collections contained in the application pool include:</span></span>
  
- <span data-ttu-id="8f7de-146">Websitesammlung 1 mit Hostnamen für das Crawlen (beispielspeicherorthttps://authoring.contoso.com:8000)</span><span class="sxs-lookup"><span data-stu-id="8f7de-146">Host-named site collection 1 for crawling (example location https://authoring.contoso.com:8000)</span></span>
    
- <span data-ttu-id="8f7de-147">Websitesammlung 2 mit Hostnamen für Abfragen (Beispiel Speicher https://www.contoso.comOrte https://secure.contoso.com,https://www.contoso.com:8000)</span><span class="sxs-lookup"><span data-stu-id="8f7de-147">Host-named site collection 2 for queries (sample locations https://www.contoso.com, https://secure.contoso.com, https://www.contoso.com:8000)</span></span>
    
- <span data-ttu-id="8f7de-148">Websitesammlung 3 mit Hostnamen für Abfragen (Beispiel Speicher https://assets.contoso.comOrte https://secureassets.contoso.com,https://assets.contoso.com:8000)</span><span class="sxs-lookup"><span data-stu-id="8f7de-148">Host-named site collection 3 for queries (sample locations https://assets.contoso.com, https://secureassets.contoso.com, https://assets.contoso.com:8000)</span></span>
    
## <a name="content-databases"></a><span data-ttu-id="8f7de-149">Inhaltsdatenbanken</span><span class="sxs-lookup"><span data-stu-id="8f7de-149">Content databases</span></span>

<span data-ttu-id="8f7de-150">Das Beispiel zeigt zwei Inhaltsdatenbanken.</span><span class="sxs-lookup"><span data-stu-id="8f7de-150">The example shows two content databases.</span></span> <span data-ttu-id="8f7de-151">Einer ist für die Websitesammlung 1, die für die durchhttps://authoring.contoso.com:8000)Forstung verwendet wird (.</span><span class="sxs-lookup"><span data-stu-id="8f7de-151">One is for the site collection 1 used for crawling (https://authoring.contoso.com:8000).</span></span> <span data-ttu-id="8f7de-152">Die andere gilt für die beiden Websitesammlungen 2 und 3, die für Abfragenhttps://www.contoso.comverwendet https://secure.contoso.comwerden https://www.contoso.com:8000(, https://assets.contoso.com, https://secureassets.contoso.com, https://assets.contoso.com:8000)oder,,.</span><span class="sxs-lookup"><span data-stu-id="8f7de-152">The other is for the two site collections 2 and 3 used for queries (https://www.contoso.com, https://secure.contoso.com, https://www.contoso.com:8000, or https://assets.contoso.com, https://secureassets.contoso.com, https://assets.contoso.com:8000).</span></span>
  
## <a name="zones-and-urls"></a><span data-ttu-id="8f7de-153">Zonen und URLs</span><span class="sxs-lookup"><span data-stu-id="8f7de-153">Zones and URLs</span></span>

<span data-ttu-id="8f7de-154">Das Beispiel zeigt drei Zonen mit den zugeordneten Lastenausgleichs-URLs, die von unterschiedlichen Benutzerkonten verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="8f7de-154">The example shows three zones with the associated load-balanced URLs that are used by different user accounts.</span></span> 
  
<span data-ttu-id="8f7de-155">Die erste Liste mit Zonen und URLs bezieht sich auf Websitesammlung 1 und enthält die folgenden Informationen:</span><span class="sxs-lookup"><span data-stu-id="8f7de-155">The first list of zones and URLs is related to site collection 1, and it contains the following information:</span></span>
  
- <span data-ttu-id="8f7de-156">Benutzer – Websiteautoren</span><span class="sxs-lookup"><span data-stu-id="8f7de-156">Users - Site authors</span></span>
    
- <span data-ttu-id="8f7de-157">Zone – Standard</span><span class="sxs-lookup"><span data-stu-id="8f7de-157">Zone - Default</span></span>
    
- <span data-ttu-id="8f7de-158">URL mit Lastenausgleich-https://authoring.contoso.com:8000</span><span class="sxs-lookup"><span data-stu-id="8f7de-158">Load-balanced URL - https://authoring.contoso.com:8000</span></span>
    
<span data-ttu-id="8f7de-159">Die zweite Liste mit Zonen und URLs besteht aus drei unterschiedlichen Benutzertypen in drei verschiedenen Zonen.</span><span class="sxs-lookup"><span data-stu-id="8f7de-159">The second list of zones and URLs has three different types of users in three different zones.</span></span> <span data-ttu-id="8f7de-160">Sie bezieht sich auf Websitesammlung 2 und enthält die folgenden Informationen:</span><span class="sxs-lookup"><span data-stu-id="8f7de-160">It is related to site collection 2, and it contains the following information:</span></span>
  
<span data-ttu-id="8f7de-161">Erste Zone:</span><span class="sxs-lookup"><span data-stu-id="8f7de-161">First zone:</span></span>
  
- <span data-ttu-id="8f7de-162">Benutzer – Websiteautoren</span><span class="sxs-lookup"><span data-stu-id="8f7de-162">Users - Site authors</span></span>
    
- <span data-ttu-id="8f7de-163">Zone – Standard</span><span class="sxs-lookup"><span data-stu-id="8f7de-163">Zone - Default</span></span>
    
- <span data-ttu-id="8f7de-164">URL mit Lastenausgleich-https://www.contoso.com:8000</span><span class="sxs-lookup"><span data-stu-id="8f7de-164">Load-balanced URL - https://www.contoso.com:8000</span></span>
    
<span data-ttu-id="8f7de-165">Zweite Zone:</span><span class="sxs-lookup"><span data-stu-id="8f7de-165">Second zone:</span></span>
  
- <span data-ttu-id="8f7de-166">Benutzer – anonyme Kunden</span><span class="sxs-lookup"><span data-stu-id="8f7de-166">Users - Anonymous customers</span></span>
    
- <span data-ttu-id="8f7de-167">Zone-Internet</span><span class="sxs-lookup"><span data-stu-id="8f7de-167">Zone - Internet</span></span>
    
- <span data-ttu-id="8f7de-168">URL mit Lastenausgleich-https://www.contoso.com</span><span class="sxs-lookup"><span data-stu-id="8f7de-168">Load-balanced URL - https://www.contoso.com</span></span>
    
<span data-ttu-id="8f7de-169">Dritte Zone:</span><span class="sxs-lookup"><span data-stu-id="8f7de-169">Third zone:</span></span>
  
- <span data-ttu-id="8f7de-170">Benutzer authentifizierte Kunden</span><span class="sxs-lookup"><span data-stu-id="8f7de-170">Users - Authenticated customers</span></span>
    
- <span data-ttu-id="8f7de-171">Zone-Extranet</span><span class="sxs-lookup"><span data-stu-id="8f7de-171">Zone - Extranet</span></span>
    
- <span data-ttu-id="8f7de-172">URL mit Lastenausgleich-https://secure.contoso.com</span><span class="sxs-lookup"><span data-stu-id="8f7de-172">Load-balanced URL - https://secure.contoso.com</span></span>
    
<span data-ttu-id="8f7de-173">Die dritte Liste von Zonen und URLs verfügt über drei verschiedene Typen von Benutzern in drei verschiedenen Zonen.</span><span class="sxs-lookup"><span data-stu-id="8f7de-173">The third list of zones and URLs has three different types of users in three different zones.</span></span> <span data-ttu-id="8f7de-174">Sie bezieht sich auf Websitesammlung 3 und enthält die folgenden Informationen:</span><span class="sxs-lookup"><span data-stu-id="8f7de-174">It is related to site collection 3, and it contains the following information:</span></span>
  
<span data-ttu-id="8f7de-175">Erste Zone:</span><span class="sxs-lookup"><span data-stu-id="8f7de-175">First zone:</span></span>
  
- <span data-ttu-id="8f7de-176">Benutzer – Websiteautoren</span><span class="sxs-lookup"><span data-stu-id="8f7de-176">Users - Site authors</span></span>
    
- <span data-ttu-id="8f7de-177">Zone-Internet</span><span class="sxs-lookup"><span data-stu-id="8f7de-177">Zone - Internet</span></span>
    
- <span data-ttu-id="8f7de-178">URL mit Lastenausgleich-https://assets.contoso.com:8000</span><span class="sxs-lookup"><span data-stu-id="8f7de-178">Load-balanced URL - https://assets.contoso.com:8000</span></span>
    
<span data-ttu-id="8f7de-179">Zweite Zone:</span><span class="sxs-lookup"><span data-stu-id="8f7de-179">Second zone:</span></span>
  
- <span data-ttu-id="8f7de-180">Benutzer – anonyme Kunden</span><span class="sxs-lookup"><span data-stu-id="8f7de-180">Users - Anonymous customers</span></span>
    
- <span data-ttu-id="8f7de-181">Zone-Internet</span><span class="sxs-lookup"><span data-stu-id="8f7de-181">Zone - Internet</span></span>
    
- <span data-ttu-id="8f7de-182">URL mit Lastenausgleich-https://assets.contoso.com</span><span class="sxs-lookup"><span data-stu-id="8f7de-182">Load-balanced URL - https://assets.contoso.com</span></span>
    
<span data-ttu-id="8f7de-183">Dritte Zone:</span><span class="sxs-lookup"><span data-stu-id="8f7de-183">Third zone:</span></span>
  
- <span data-ttu-id="8f7de-184">Benutzer authentifizierte Kunden</span><span class="sxs-lookup"><span data-stu-id="8f7de-184">Users - Authenticated customers</span></span>
    
- <span data-ttu-id="8f7de-185">Zone-Extranet</span><span class="sxs-lookup"><span data-stu-id="8f7de-185">Zone - Extranet</span></span>
    
- <span data-ttu-id="8f7de-186">URL mit Lastenausgleich-https://secureassets.contoso.com</span><span class="sxs-lookup"><span data-stu-id="8f7de-186">Load-balanced URL - https://secureassets.contoso.com</span></span>
    

