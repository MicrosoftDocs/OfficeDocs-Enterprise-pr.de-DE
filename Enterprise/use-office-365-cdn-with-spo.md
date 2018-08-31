---
title: Verwenden Sie die Office 365 Content Delivery Networks mit SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 6/29/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- SPO160
ms.assetid: bebb285f-1d54-4f79-90a5-94985afc6af8
description: Beschreibt, wie Office 365 des integrierten Content Delivery Network (CDN) verwenden, um die Bereitstellung von Ihrer SharePoint Online-Ressourcen für alle Benutzer zu beschleunigen unabhängig davon, wo sich diese befinden oder wie sie Ihre Inhalte zugreifen.
ms.openlocfilehash: 958f01419a74e4b8cd007b2627585884496bdfdf
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540752"
---
# <a name="use-the-office-365-content-delivery-network-with-sharepoint-online"></a><span data-ttu-id="58b7c-103">Verwenden Sie die Office 365 Content Delivery Networks mit SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="58b7c-103">Use the Office 365 content delivery network with SharePoint Online</span></span>

<span data-ttu-id="58b7c-p101">Sie können statische Objekte in der Office 365 Content Delivery Network (CDN) um bieten eine bessere Leistung für Ihre SharePoint Online-Seiten hosten. Statische Objekte sind Dateien, die oft wie Bilder, Video und Audio, Stylesheets, Schriftarten und JavaScript-Dateien nicht geändert. Das CDN fungiert als geografisch verteilten Zwischenspeichern Proxy, durch Zwischenspeichern statische Objekte näher an den Browsern, die diese anfordert.</span><span class="sxs-lookup"><span data-stu-id="58b7c-p101">You can host static assets in the Office 365 content delivery network (CDN) to provide better performance for your SharePoint Online pages. Static assets are files that don't change very often, like images, video and audio, style sheets, fonts, and JavaScript files. The CDN works as a geographically distributed caching proxy, by caching static assets closer to the browsers requesting them.</span></span> 
  
<span data-ttu-id="58b7c-p102">Wenn Sie bereits mit der Art und Weise vertraut, die CDNs arbeiten sind, müssen Sie nur einige Schritte ausführen, um es einrichten. In diesem Thema wird beschrieben, wie. Informieren Sie sich für Informationen über das Office 365 CDN und Entwicklersicht hosten Ihre statischen Ressourcen auf.</span><span class="sxs-lookup"><span data-stu-id="58b7c-p102">If you are already familiar with the way that CDNs work, you only need to complete a few steps to set it up. This topic describes how. Read on for information about the Office 365 CDN and how to get started hosting your static assets.</span></span>
  
 <span data-ttu-id="58b7c-110">**Head zurück an [netzwerkplanung und leistungsoptimierung für Office 365](https://aka.ms/tune).**</span><span class="sxs-lookup"><span data-stu-id="58b7c-110">**Head back to [Network planning and performance tuning for Office 365](https://aka.ms/tune).**</span></span>
  
## <a name="office-365-cdn-basics"></a><span data-ttu-id="58b7c-111">Office 365 CDN-Grundlagen</span><span class="sxs-lookup"><span data-stu-id="58b7c-111">Office 365 CDN basics</span></span>

<span data-ttu-id="58b7c-p103">Die Office 365-CDN ist Bestandteil Ihrer SharePoint Online-Abonnement. Sie müssen nicht sehr bezahlen. Office 365 bietet Unterstützung für beide sind privat und öffentlich und ermöglicht es Ihnen zu statischen Host-Objekte in mehreren Speicherorten oder Herkunft. Die Office 365-CDN ist nicht identisch mit dem Azure CDN. Wenn Sie weitere Informationen dazu, warum ein CDN verwenden oder allgemeine Konzepte von CDN benötigen, finden Sie unter [Inhaltsübermittlung](content-delivery-networks.md).</span><span class="sxs-lookup"><span data-stu-id="58b7c-p103">The Office 365 CDN is included as part of your SharePoint Online subscription. You don't have to pay extra for it. Office 365 provides support for both private and public access and allows you to host static assets in multiple locations, or origins. The Office 365 CDN is not the same as the Azure CDN. If you need more information about why to use a CDN or about general CDN concepts, see [Content delivery networks](content-delivery-networks.md).</span></span>
  
## <a name="how-the-cdn-grants-access-to-end-users"></a><span data-ttu-id="58b7c-117">Wie das CDN gewährt Zugriff auf die Endbenutzer</span><span class="sxs-lookup"><span data-stu-id="58b7c-117">How the CDN grants access to end users</span></span>

<span data-ttu-id="58b7c-p104">Privater Zugriff auf statische Objekte in der Office 365-CDN wird mithilfe von SharePoint Online generierte Token erteilt. Benutzer, die bereits über die Berechtigung zum Zugriff auf den Ordner oder die Bibliothek, die vom Ursprung werden automatisch Token erteilt werden. SharePoint Online unterstützt auf Elementebene keine Berechtigungen für das CDN.</span><span class="sxs-lookup"><span data-stu-id="58b7c-p104">Private access to static assets in the Office 365 CDN is granted by tokens generated by SharePoint Online. Users who already have permission to access to the folder or library designated by the origin will automatically be granted tokens. SharePoint Online does not support item-level permissions for the CDN.</span></span>
  
<span data-ttu-id="58b7c-121">Beispiel für eine Datei befindet sich unter `https://contoso.sharepoint.com/sites/site1/library1/folder1/image1.jpg`, erhält die folgenden:</span><span class="sxs-lookup"><span data-stu-id="58b7c-121">For example, for a file located at `https://contoso.sharepoint.com/sites/site1/library1/folder1/image1.jpg`, given the following:</span></span>
  
- <span data-ttu-id="58b7c-122">Benutzer 1 hat Zugriff auf folder1 und image1.jpg</span><span class="sxs-lookup"><span data-stu-id="58b7c-122">User 1 has access to folder1 and to image1.jpg</span></span>
    
- <span data-ttu-id="58b7c-123">2 Benutzer hat keinen Zugriff auf folder1</span><span class="sxs-lookup"><span data-stu-id="58b7c-123">User 2 does not have access to folder1</span></span>
    
- <span data-ttu-id="58b7c-124">Benutzer 3 hat keinen Zugriff auf folder1, sondern wird gewährt ausdrückliche Zustimmung image1.jpg Zugriff auf über SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="58b7c-124">User 3 does not have access to folder1 but is granted explicit permission to access image1.jpg through SharePoint Online</span></span>
    
- <span data-ttu-id="58b7c-125">4 Benutzer über Zugriff auf folder1 jedoch wurde verweigert Zugriff auf image1.jpg explizit</span><span class="sxs-lookup"><span data-stu-id="58b7c-125">User 4 has access to folder1 but has been explicitly denied access to image1.jpg</span></span>
    
<span data-ttu-id="58b7c-126">Klicken Sie auf die Folgendes zutrifft:</span><span class="sxs-lookup"><span data-stu-id="58b7c-126">Then the following are true:</span></span>
  
- <span data-ttu-id="58b7c-127">Benutzer 1 und 4 Benutzer werden können image1.jpg über das CDN zugegriffen.</span><span class="sxs-lookup"><span data-stu-id="58b7c-127">User 1 and User 4 will be able to access image1.jpg through the CDN.</span></span>
    
- <span data-ttu-id="58b7c-128">Benutzer 2 und 3 für Benutzer wird nicht über das CDN image1.jpg zugreifen können.</span><span class="sxs-lookup"><span data-stu-id="58b7c-128">User 2 and User 3 will not be able to access image1.jpg through the CDN.</span></span>
    
    <span data-ttu-id="58b7c-129">Jedoch können Benutzer 3 weiterhin zugreifen die Anlage image1.jpg direkt über SharePoint Online während Benutzer 4 die Anlage nicht über SharePoint Online zugreifen können.</span><span class="sxs-lookup"><span data-stu-id="58b7c-129">However, User 3 can still access the asset image1.jpg directly through SharePoint Online while User 4 cannot access the asset through SharePoint Online.</span></span>
    
## <a name="overview-of-working-with-the-office-365-cdn"></a><span data-ttu-id="58b7c-130">Übersicht über das Arbeiten mit dem Office 365 CDN</span><span class="sxs-lookup"><span data-stu-id="58b7c-130">Overview of working with the Office 365 CDN</span></span>

<span data-ttu-id="58b7c-131">Um das Office 365 CDN einzurichten, führen Sie die folgenden grundlegenden Schritte aus:</span><span class="sxs-lookup"><span data-stu-id="58b7c-131">To set up the Office 365 CDN, you follow these basic steps:</span></span>
  
- <span data-ttu-id="58b7c-132">Planen der CDN-Bereitstellung:</span><span class="sxs-lookup"><span data-stu-id="58b7c-132">Plan for CDN deployment:</span></span>
    
  - <span data-ttu-id="58b7c-p105">Bestimmen Sie die statischen Anlagen, die Sie auf der Office 365-CDN hosten möchten. Ausführliche Informationen dazu, wie Sie diese Auswahlmöglichkeiten zur Verfügung stellen können finden Sie [die Inhaltsübermittlung](content-delivery-networks.md).</span><span class="sxs-lookup"><span data-stu-id="58b7c-p105">Determine which static assets you want to host on the Office 365 CDN. For detailed information about how to make these choices, refer to [Content delivery networks](content-delivery-networks.md).</span></span>
    
  - <span data-ttu-id="58b7c-p106">[Bestimmen Sie, wo Sie Ihre Anlagen speichern möchten](use-office-365-cdn-with-spo.md#CDNStoreAssets). Diesen Speicherort ist ein Ordner oder SharePoint-Bibliothek und einen Ursprung aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="58b7c-p106">[Determine where you want to store your assets](use-office-365-cdn-with-spo.md#CDNStoreAssets). This location is a folder or SharePoint library and is called an origin.</span></span>
    
  - <span data-ttu-id="58b7c-p107">Bestimmen Sie, ob die Anlagen vertraulich oder veröffentlicht werden soll. Sie dieses Vorgehen, wenn Sie [auswählen, ob jede Origin öffentlich oder privat sein soll](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate). Wenn Sie möchten, können Sie mehrere Herkunft, in denen einige öffentlich sind, und sind einige privat.</span><span class="sxs-lookup"><span data-stu-id="58b7c-p107">Determine whether the assets should be made public or kept private. You do this when you [Choose whether each origin should be public or private](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate). If you want, you can have multiple origins in which some are public, and some are private.</span></span>
    
- <span data-ttu-id="58b7c-p108">[Festlegen einrichten und Konfigurieren der Office 365-CDN mithilfe von SharePoint Online-Verwaltungsshell](use-office-365-cdn-with-spo.md#CDNSetupinPShell). Wenn Sie diesen Schritt abgeschlossen haben, müssen Sie:</span><span class="sxs-lookup"><span data-stu-id="58b7c-p108">[Set up and configure the Office 365 CDN by using the SharePoint Online Management Shell](use-office-365-cdn-with-spo.md#CDNSetupinPShell). When you complete this step, you will have:</span></span>
    
  - <span data-ttu-id="58b7c-142">Aktiviert das CDN für Ihre Organisation.</span><span class="sxs-lookup"><span data-stu-id="58b7c-142">Enabled the CDN for your organization.</span></span>
    
  - <span data-ttu-id="58b7c-p109">Ihre Herkunft hinzugefügt. Sie identifizieren jede Ursprung als öffentliche oder private.</span><span class="sxs-lookup"><span data-stu-id="58b7c-p109">Added your origins. You identify each origin as public or private.</span></span>
    
<span data-ttu-id="58b7c-145">Einmal fertig sind Sie mit dem Setup, [Verwalten der Office 365-CDN](use-office-365-cdn-with-spo.md#CDNManage) über einen Zeitraum von:</span><span class="sxs-lookup"><span data-stu-id="58b7c-145">Once you're done with setup, [Manage the Office 365 CDN](use-office-365-cdn-with-spo.md#CDNManage) over time by:</span></span> 
  
- <span data-ttu-id="58b7c-146">Hinzufügen, aktualisieren und Entfernen von Anlagen</span><span class="sxs-lookup"><span data-stu-id="58b7c-146">Adding, updating, and removing assets</span></span>
    
- <span data-ttu-id="58b7c-147">Hinzufügen und Entfernen von Herkunft</span><span class="sxs-lookup"><span data-stu-id="58b7c-147">Adding and removing origins</span></span>
    
- <span data-ttu-id="58b7c-148">Konfigurieren von CDN-Richtlinien</span><span class="sxs-lookup"><span data-stu-id="58b7c-148">Configuring CDN policies</span></span>
    
- <span data-ttu-id="58b7c-149">Falls erforderlich, das Office 365 CDN deaktivieren</span><span class="sxs-lookup"><span data-stu-id="58b7c-149">If necessary, disabling the Office 365 CDN</span></span>
    
## <a name="determine-where-you-want-to-store-your-assets"></a><span data-ttu-id="58b7c-150">Bestimmen Sie, wo Sie Ihre Anlagen speichern möchten</span><span class="sxs-lookup"><span data-stu-id="58b7c-150">Determine where you want to store your assets</span></span>

<span data-ttu-id="58b7c-p110">Das CDN ruft Ihre Anlagen von einem Speicherort, der einen Ursprung aufgerufen. Für Office 365 ist ein Ursprung an eine SharePoint-Bibliothek oder einen Ordner, die über eine URL zugegriffen werden kann. Wenn Sie für Ihre Organisation Herkunft angeben, stehen Ihnen sehr flexibel. Beispielsweise können Sie angeben, mehrere Herkunft oder einen einzelnen Ursprung, in dem alle CDN Anlagen erstellt werden sollen. Sie können auswählen, öffentlichen oder privaten Herkunft für Ihre Organisation haben. Die meisten Organisationen werden auch eine Kombination aus beidem implementiert.</span><span class="sxs-lookup"><span data-stu-id="58b7c-p110">The CDN fetches your assets from a location called an origin. For Office 365, an origin is a SharePoint library or folder that is accessible by a URL. You have great flexibility when you specify origins for your organization. For example, you can specify multiple origins, or, a single origin where you want to put all your CDN assets. You can choose to have both public or private origins for your organization. Most organizations will choose to implement a combination of the two.</span></span>
  
<span data-ttu-id="58b7c-p111">Wenn Sie Hunderte von Herkunft definieren, wird es wahrscheinlich sich negativ auf dem Zeitpunkt der haben, die benötigt wird, um Anforderungen zu verarbeiten. Es wird empfohlen, wenn Sie über mehr als 100 Herkunft verfügen Sie möglicherweise überdenken Ihre Architektur.</span><span class="sxs-lookup"><span data-stu-id="58b7c-p111">If you define hundreds of origins, it will likely have a negative impact on the time it takes to process requests. We recommend that if you have more than about 100 origins you might want to rethink your architecture.</span></span>
  
## <a name="choose-whether-each-origin-should-be-public-or-private"></a><span data-ttu-id="58b7c-159">Wählen Sie, ob jede Origin öffentlichen oder privaten werden sollen</span><span class="sxs-lookup"><span data-stu-id="58b7c-159">Choose whether each origin should be public or private</span></span>

<span data-ttu-id="58b7c-p112">Wenn Sie einen Ursprung identifiziert haben, geben Sie an, ob es öffentlichen oder privaten hergestellt werden soll. Unabhängig davon welche Option Sie wählen, wird von Microsoft den schwierigsten für Sie bei der Verwaltung von dem CDN selbst. Darüber hinaus können Sie Ihre Meinung später ändern, nachdem Sie dem CDN einrichten und Ihre Herkunft identifiziert haben.</span><span class="sxs-lookup"><span data-stu-id="58b7c-p112">When you identify an origin, you specify whether it should be made public or private. Regardless of which option you choose, Microsoft does all the heavy lifting for you when it comes to administration of the CDN itself. Also, you can change your mind later, after you've set up the CDN and identified your origins.</span></span>
  
<span data-ttu-id="58b7c-163">Optionen für öffentliche und private Performance, aber jeder besitzt eindeutige Attribute und Vorteile.</span><span class="sxs-lookup"><span data-stu-id="58b7c-163">Both public and private options provide performance improvements, but each has unique attributes and advantages.</span></span>
  
 <span data-ttu-id="58b7c-164">**Attribute und Vorteile der Objekte in einem öffentlichen Origin-hosting**</span><span class="sxs-lookup"><span data-stu-id="58b7c-164">**Attributes and advantages of hosting assets in a public origin**</span></span>
  
- <span data-ttu-id="58b7c-165">Objekte in einem öffentlichen Origin verfügbar gemacht werden anonym von allen Benutzern zugegriffen werden.</span><span class="sxs-lookup"><span data-stu-id="58b7c-165">Assets exposed in a public origin are accessible by everyone anonymously.</span></span>
    
    > [!IMPORTANT]
    > <span data-ttu-id="58b7c-166">Wenn Sie einen öffentlichen Ursprung in Ihrer CDN identifiziert haben, sollten Sie Ressourcen, die in einem öffentlichen Ursprung oder SharePoint Online-Bibliothek Beachtung von Ihrer Organisation berücksichtigt werden nie platzieren.</span><span class="sxs-lookup"><span data-stu-id="58b7c-166">If you identify a public origin in your CDN, you should never place resources that are considered sensitive to your organization in a public origin or SharePoint Online library.</span></span> 
  
- <span data-ttu-id="58b7c-167">Wenn Sie eine Anlage aus einer öffentlichen Origin entfernen möchten, kann die Anlage weiterhin für bis zu 30 Tagen aus dem Cache verfügbar sein; Es werden jedoch Links auf die Anlage in dem CDN innerhalb von 15 Minuten ungültig.</span><span class="sxs-lookup"><span data-stu-id="58b7c-167">If you remove an asset from a public origin, the asset may continue to be available for up to 30 days from the cache; however, we will invalidate links to the asset in the CDN within 15 minutes.</span></span>
    
- <span data-ttu-id="58b7c-p113">Wenn Sie Stylesheets (CSS-Dateien) in einem öffentlichen Origin hosten, können Sie relative Pfade und URIs im Code verwenden. Dies bedeutet, dass Sie den Speicherort der Hintergrundbilder und andere Objekte relativ zum Speicherort der Anlage, die sie anrufen, verweisen können.</span><span class="sxs-lookup"><span data-stu-id="58b7c-p113">When you host style sheets (CSS files) in a public origin, you can use relative paths and URIs within the code. This means that you can reference the location of background images and other objects relative to the location of the asset that's calling it.</span></span>
    
- <span data-ttu-id="58b7c-p114">Während Sie einen öffentlichen Ursprung URL codieren können, wird dadurch also nicht empfohlen. Der Grund hierfür ist, wenn der Zugriff auf das CDN nicht mehr verfügbar ist, wird die URL nicht automatisch in Ihrer Organisation in SharePoint Online aufgelöst wird und möglicherweise beschädigte Verknüpfungen und andere Fehler.</span><span class="sxs-lookup"><span data-stu-id="58b7c-p114">While you can hard code a public origin's URL, doing so is not recommended. The reason for this is that if access to the CDN becomes unavailable, the URL will not automatically resolve to your organization in SharePoint Online and might result in broken links and other errors.</span></span>
    
- <span data-ttu-id="58b7c-p115">Die Standard-Dateitypen, die für Öffentliche Herkunft enthalten sind sind CSS, .eot, GIF, ICO, JPEG, JPG, js, .map, PNG, SVG, ttf und .woff. Sie können zusätzliche Dateitypen angeben.</span><span class="sxs-lookup"><span data-stu-id="58b7c-p115">The default file types that are included for public origins are .css, .eot, .gif, .ico, .jpeg, .jpg, .js, .map, .png, .svg, .ttf, and .woff. You can specify additional file types.</span></span>
    
- <span data-ttu-id="58b7c-p116">Wenn Sie möchten, können Sie eine Richtlinie zum Ausschließen von Anlagen, die von Klassifikationen in der Website identifiziert wurden, die Sie angeben konfigurieren. Sie können beispielsweise alle Anlagen auszuschließen, die als "confidential" oder "eingeschränkt" gekennzeichnet sind, selbst wenn sie einen zulässigen Dateityp sind und sich in einem öffentlichen Ursprung befinden.</span><span class="sxs-lookup"><span data-stu-id="58b7c-p116">If you want, you can configure a policy to exclude assets that have been identified by site classifications that you specify. For example, you can choose to exclude all assets that are marked as "confidential" or "restricted" even if they are an allowed file type and are located in a public origin.</span></span>
    
 <span data-ttu-id="58b7c-176">**Attribute und Vorteile der Objekte in einem privaten Origin-hosting**</span><span class="sxs-lookup"><span data-stu-id="58b7c-176">**Attributes and advantages of hosting assets in a private origin**</span></span>
  
- <span data-ttu-id="58b7c-p117">Benutzer können nur die Objekte aus einer privaten Origin zugreifen, wenn sie dazu autorisiert sind. Anonymer Zugriff auf diese Ressourcen wird verhindert.</span><span class="sxs-lookup"><span data-stu-id="58b7c-p117">Users can only access the assets from a private origin if they are authorized to do so. Anonymous access to these assets is prevented.</span></span>
    
- <span data-ttu-id="58b7c-179">Wenn Sie eine Anlage vom Ursprung private entfernen, kann die Anlage weiterhin für bis zu einer Stunde aus dem Cache zur Verfügung; Es werden jedoch Links auf die Anlage in dem CDN innerhalb von 15 Minuten ungültig.</span><span class="sxs-lookup"><span data-stu-id="58b7c-179">If you remove an asset from the private origin, the asset may continue to be available for up to an hour from the cache; however, we will invalidate links to the asset in the CDN within 15 minutes.</span></span>
    
- <span data-ttu-id="58b7c-p118">Die Standard-Dateitypen, die für private Herkunft enthalten sind sind GIF, ICO, JPEG, JPG, js und PNG. Sie können zusätzliche Dateitypen angeben.</span><span class="sxs-lookup"><span data-stu-id="58b7c-p118">The default file types that are included for private origins are .gif, .ico, .jpeg, .jpg, .js, and .png. You can specify additional file types.</span></span>
    
- <span data-ttu-id="58b7c-182">Genau wie öffentliche Herkunft können Sie eine Richtlinie zum Ausschließen von Anlagen, die von Klassifikationen in der Website, die Sie angeben identifiziert wurden, auch wenn Sie Platzhalter verwenden, um alle Ressourcen innerhalb eines Ordners oder einer Website Bibliothek enthalten konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="58b7c-182">Just like public origins, you can configure a policy to exclude assets that have been identified by site classifications that you specify even if you use wildcards to include all assets within a folder or Site Library.</span></span>
    
## <a name="default-office-365-cdn-origins"></a><span data-ttu-id="58b7c-183">Office 365 CDN-Herkunft Standard</span><span class="sxs-lookup"><span data-stu-id="58b7c-183">Default Office 365 CDN origins</span></span>

<span data-ttu-id="58b7c-p119">Sofern nicht anders angegeben, richtet Office 365 einige Herkunft Standard für Sie, wenn Sie das Office 365 CDN aktivieren. Wenn Sie zunächst diese ausschließen, können Sie diese Herkunft hinzufügen, nach Abschluss der Installation.</span><span class="sxs-lookup"><span data-stu-id="58b7c-p119">Unless you specify otherwise, Office 365 sets up some default origins for you when you enable the Office 365 CDN. If you initially exclude them, you can add these origins after you complete setup.</span></span>
  
<span data-ttu-id="58b7c-186">Private Herkunft Standard:</span><span class="sxs-lookup"><span data-stu-id="58b7c-186">Default private origins:</span></span>
  
- <span data-ttu-id="58b7c-187">\*/userphoto.aspx</span><span class="sxs-lookup"><span data-stu-id="58b7c-187">\*/userphoto.aspx</span></span>
    
- <span data-ttu-id="58b7c-188">\*/SiteAssets</span><span class="sxs-lookup"><span data-stu-id="58b7c-188">\*/siteassets</span></span>
    
<span data-ttu-id="58b7c-189">Standardmäßige öffentliche Herkunft:</span><span class="sxs-lookup"><span data-stu-id="58b7c-189">Default public origins:</span></span>
  
- <span data-ttu-id="58b7c-190">\*/MasterPage</span><span class="sxs-lookup"><span data-stu-id="58b7c-190">\*/masterpage</span></span>
    
- <span data-ttu-id="58b7c-191">\*Pfad/Style library</span><span class="sxs-lookup"><span data-stu-id="58b7c-191">\*/style library</span></span>
    
## <a name="set-up-and-configure-the-office-365-cdn-by-using-the-sharepoint-online-management-shell"></a><span data-ttu-id="58b7c-192">Richten Sie ein und konfigurieren Sie der Office 365-CDN mithilfe von SharePoint Online-Verwaltungsshell</span><span class="sxs-lookup"><span data-stu-id="58b7c-192">Set up and configure the Office 365 CDN by using the SharePoint Online Management Shell</span></span>

<span data-ttu-id="58b7c-p120">Die Verfahren in diesem Thema müssen Sie die SharePoint Online-Verwaltungsshell verwenden, um mit SharePoint Online herstellen. Anweisungen finden Sie unter [Connect to SharePoint Online-PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).</span><span class="sxs-lookup"><span data-stu-id="58b7c-p120">The procedures in this topic require you to use the SharePoint Online Management Shell to connect to SharePoint Online. For instructions, see [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).</span></span>
  
<span data-ttu-id="58b7c-195">Führen Sie diese Schritte zum Einrichten und Konfigurieren der Office 365 CDN zum Hosten Ihre statischen Daten in SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="58b7c-195">Complete these steps to set up and configure the Office 365 CDN to host your static assets in SharePoint Online.</span></span>
  
### <a name="to-enable-your-organization-to-use-the-office-365-cdn"></a><span data-ttu-id="58b7c-196">So aktivieren Sie Ihre Organisation die Office 365-CDN verwenden</span><span class="sxs-lookup"><span data-stu-id="58b7c-196">To enable your organization to use the Office 365 CDN</span></span>

<span data-ttu-id="58b7c-p121">Verwenden Sie das Cmdlet " **Set-SPOTenantCdnEnabled** ", um Ihre Organisation mit dem Office 365 CDN aktivieren. Sie können Ihrer Organisation öffentliche Herkunft, private Herkunft oder beide mit dem CDN verwendet werden. Sie können auch die Office 365-CDN um überspringen die Einrichtung des Standard-Herkunft beim Aktivieren konfigurieren. Sie können diese Herkunft immer weiter unten in diesem Thema beschriebenen hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="58b7c-p121">Use the **Set-SPOTenantCdnEnabled** cmdlet to enable your organization to use the Office 365 CDN. You can enable your organization to use either public origins, private origins, or both with the CDN. You can also configure the Office 365 CDN to skip the setup of default origins when you enable it. You can always add these origins later as described in this topic.</span></span> 
  
<span data-ttu-id="58b7c-201">In Windows Powershell für SharePoint Online:</span><span class="sxs-lookup"><span data-stu-id="58b7c-201">In Windows Powershell for SharePoint Online:</span></span>
  
```
Set-SPOTenantCdnEnabled -CdnType <Public | Private | Both> -Enable $true
```

<span data-ttu-id="58b7c-202">Angenommen, um Ihrer Organisation zur Verwendung von öffentlichen und privaten Herkunft mit dem CDN zu aktivieren, geben Sie den folgenden Befehl ein:</span><span class="sxs-lookup"><span data-stu-id="58b7c-202">For example, to enable your organization to use both public and private origins with the CDN, type the following command:</span></span>
  
```
Set-SPOTenantCdnEnabled -CdnType Both -Enable $true
```

<span data-ttu-id="58b7c-203">Zum Aktivieren Ihrer Organisation verwenden, öffentliche und private Herkunft mit dem CDN jedoch die Einrichtung der Standard-Herkunft überspringen Geben Sie den folgenden Befehl ein:</span><span class="sxs-lookup"><span data-stu-id="58b7c-203">To enable your organization to use both public and private origins with the CDN but skip setting up the default origins, type the following command:</span></span>
  
```
Set-SPOTenantCdnEnabled -CdnType Both -Enable $true -NoDefaultOrigins
```

<span data-ttu-id="58b7c-204">Um Ihrer Organisation zur Verwendung von öffentlichen Herkunft mit dem CDN zu aktivieren, geben Sie den folgenden Befehl ein:</span><span class="sxs-lookup"><span data-stu-id="58b7c-204">To enable your organization to use public origins with the CDN, type the following command:</span></span>
  
```
Set-SPOTenantCdnEnabled -CdnType Public -Enable $true
```

<span data-ttu-id="58b7c-205">Um Ihrer Organisation zur Verwendung von privaten Herkunft mit dem CDN zu aktivieren, geben Sie den folgenden Befehl ein:</span><span class="sxs-lookup"><span data-stu-id="58b7c-205">To enable your organization to use private origins with the CDN, type the following command:</span></span>
  
```
Set-SPOTenantCdnEnabled -CdnType Private -Enable $true
```

<span data-ttu-id="58b7c-206">Weitere Informationen zu diesem Cmdlet finden Sie unter [Set-SPOTenantCdnEnabled](https://technet.microsoft.com/en-us/library/mt790765.aspx).</span><span class="sxs-lookup"><span data-stu-id="58b7c-206">For more information about this cmdlet, see [Set-SPOTenantCdnEnabled](https://technet.microsoft.com/en-us/library/mt790765.aspx).</span></span>
  
### <a name="optional-to-change-the-list-of-file-types-to-include-in-the-office-365-cdn"></a><span data-ttu-id="58b7c-207">(Optional) So ändern Sie die Liste der Dateitypen, die in der Office 365-CDN einschließen</span><span class="sxs-lookup"><span data-stu-id="58b7c-207">(Optional) To change the list of file types to include in the Office 365 CDN</span></span>
<span data-ttu-id="58b7c-208"><a name="Office365CDNforSPOFileType"> </a></span><span class="sxs-lookup"><span data-stu-id="58b7c-208"></span></span>

> [!TIP]
> <span data-ttu-id="58b7c-p122">Wenn Sie mit dem Cmdlet **Set-SPOTenantCdnPolicy** Dateitypen definieren, überschreiben Sie die Liste der aktuell definierte. Wenn Sie zusätzliche Dateitypen der Liste hinzufügen möchten, verwenden Sie das Cmdlet zuerst um herauszufinden, was Dateitypen sind bereits zulässig, und nehmen sie in der Liste zusammen mit Ihrem neue.</span><span class="sxs-lookup"><span data-stu-id="58b7c-p122">When you define file types by using the **Set-SPOTenantCdnPolicy** cmdlet, you overwrite the currently defined list. If you want to add additional file types to the list, use the cmdlet first to find out what file types are already allowed and include them in the list along with your new ones.</span></span> 
  
<span data-ttu-id="58b7c-p123">Verwenden Sie das Cmdlet **Set-SPOTenantCdnPolicy** statische Dateitypen definieren, die öffentliche und private Herkunft in dem CDN gehostet werden können. Standardmäßig werden allgemeine Anlagentypen für Beispiel CSS, GIF, JPG und js zulässig.</span><span class="sxs-lookup"><span data-stu-id="58b7c-p123">Use the **Set-SPOTenantCdnPolicy** cmdlet to define static file types that can be hosted by public and private origins in the CDN. By default, common asset types are allowed, for example .css, .gif, .jpg, and .js.</span></span> 
  
<span data-ttu-id="58b7c-213">In Windows PowerShell für SharePoint Online:</span><span class="sxs-lookup"><span data-stu-id="58b7c-213">In Windows PowerShell for SharePoint Online:</span></span>
  
```
Set-SPOTenantCdnPolicy -CdnType <Public | Private> -PolicyType IncludeFileExtensions -PolicyValue "<Comma-separated list of file types >"
```

<span data-ttu-id="58b7c-214">Um herauszufinden, welche Dateitypen nach dem CDN derzeit zulässig sind, verwenden Sie das Cmdlet **Get-SPOTenantCdnPolicies** :</span><span class="sxs-lookup"><span data-stu-id="58b7c-214">To see what file types are currently allowed by the CDN, use the **Get-SPOTenantCdnPolicies** cmdlet:</span></span> 
  
```
Get-SPOTenantCdnPolicies -CdnType <Public | Private>
```

<span data-ttu-id="58b7c-215">Weitere Informationen zu diesen Cmdlets finden Sie unter [Set-SPOTenantCdnPolicy](https://technet.microsoft.com/en-us/library/mt800839.aspx) und [Get-SPOTenantCdnPolicies](https://technet.microsoft.com/en-us/library/mt800838.aspx).</span><span class="sxs-lookup"><span data-stu-id="58b7c-215">For more information about these cmdlets, see [Set-SPOTenantCdnPolicy](https://technet.microsoft.com/en-us/library/mt800839.aspx) and [Get-SPOTenantCdnPolicies](https://technet.microsoft.com/en-us/library/mt800838.aspx).</span></span>
  
### <a name="optional-to-change-the-list-of-site-classifications-you-want-to-exclude-from-the-office-365-cdn"></a><span data-ttu-id="58b7c-216">(Optional) So ändern Sie die Liste der Klassifikationen in der Website, den Sie aus dem Office 365 CDN ausschließen möchten</span><span class="sxs-lookup"><span data-stu-id="58b7c-216">(Optional) To change the list of site classifications you want to exclude from the Office 365 CDN</span></span>
<span data-ttu-id="58b7c-217"><a name="Office365CDNforSPOSiteClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="58b7c-217"></span></span>

> [!TIP]
> <span data-ttu-id="58b7c-p124">Wenn Sie Klassifikationen in der Website mithilfe des Cmdlets **Set-SPOTenantCdnPolicy** ausschließen, überschreiben Sie die Liste der aktuell definierte. Wenn Sie zusätzliche Site Klassifikationen ausschließen möchten, verwenden Sie das Cmdlet zuerst erfahren Sie, welche Klassifikationen bereits ausgeschlossen werden, und klicken Sie dann zusammen mit Ihrem neue hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="58b7c-p124">When you exclude site classifications by using the **Set-SPOTenantCdnPolicy** cmdlet, you overwrite the currently defined list. If you want to exclude additional site classifications, use the cmdlet first to find out what classifications are already excluded and then add them along with your new ones.</span></span> 
  
<span data-ttu-id="58b7c-p125">Verwenden Sie das Cmdlet **Set-SPOTenantCdnPolicy** auszuschließende Klassifikationen in der Website, die nicht über das CDN zur Verfügung stellen möchten. Standardmäßig werden keine Klassifikationen in der Website ausgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="58b7c-p125">Use the **Set-SPOTenantCdnPolicy** cmdlet to exclude site classifications that you do not want to make available over the CDN. By default, no site classifications are excluded.</span></span> 
  
<span data-ttu-id="58b7c-222">In Windows PowerShell für SharePoint Online:</span><span class="sxs-lookup"><span data-stu-id="58b7c-222">In Windows PowerShell for SharePoint Online:</span></span>
  
```
Set-SPOTenantCdnPolicy -CdnType <Public | Private> -PolicyType ExcludeRestrictedSiteClassifications  -PolicyValue "<Comma-separated list of site classifications >"
```

<span data-ttu-id="58b7c-223">Um herauszufinden, welche Klassifikationen in der Website zurzeit eingeschränkt sind, verwenden Sie das Cmdlet **Get-SPOTenantCdnPolicies** :</span><span class="sxs-lookup"><span data-stu-id="58b7c-223">To see what site classifications are currently restricted, use the **Get-SPOTenantCdnPolicies** cmdlet:</span></span> 
  
```
Get-SPOTenantCdnPolicies -CdnType <Public | Private>
```

<span data-ttu-id="58b7c-224">Weitere Informationen zu diesen Cmdlets finden Sie unter [Set-SPOTenantCdnPolicy](https://technet.microsoft.com/en-us/library/mt800839.aspx) und [Get-SPOTenantCdnPolicies](https://technet.microsoft.com/en-us/library/mt800838.aspx).</span><span class="sxs-lookup"><span data-stu-id="58b7c-224">For more information about these cmdlets, see [Set-SPOTenantCdnPolicy](https://technet.microsoft.com/en-us/library/mt800839.aspx) and [Get-SPOTenantCdnPolicies](https://technet.microsoft.com/en-us/library/mt800838.aspx).</span></span>
  
### <a name="to-add-an-origin-for-your-assets"></a><span data-ttu-id="58b7c-225">So fügen Sie einen Ursprung für Ihre Anlagen hinzu</span><span class="sxs-lookup"><span data-stu-id="58b7c-225">To add an origin for your assets</span></span>
<span data-ttu-id="58b7c-226"><a name="Office365CDNforSPOOrigin"> </a></span><span class="sxs-lookup"><span data-stu-id="58b7c-226"></span></span>

<span data-ttu-id="58b7c-p126">Verwenden Sie das Cmdlet **Add-SPOTenantCdnOrigin** , um einen Ursprung definieren. Sie können mehrere Herkunft definieren. Der Ursprung ist eine URL, die verweist auf eine SharePoint-Bibliothek oder einen Ordner, der die Anlagen enthält, die das dem CDN gehostet werden soll.</span><span class="sxs-lookup"><span data-stu-id="58b7c-p126">Use the **Add-SPOTenantCdnOrigin** cmdlet to define an origin. You can define multiple origins. The origin is a URL that points to a SharePoint library or folder that contains the assets that you want to be hosted by the CDN.</span></span> 
  
> [!IMPORTANT]
> <span data-ttu-id="58b7c-230">Wenn Sie einen öffentlichen Ursprung in Ihrer CDN identifiziert haben, sollten Sie Ressourcen, die in den öffentlichen Ursprung oder SharePoint Online-Bibliothek Beachtung von Ihrer Organisation berücksichtigt werden nie platzieren.</span><span class="sxs-lookup"><span data-stu-id="58b7c-230">If you identify a public origin in your CDN, you should never place resources that are considered sensitive to your organization in the public origin or SharePoint Online library.</span></span> 
  
```
Add-SPOTenantCdnOrigin -CdnType <Public | Private> -OriginUrl <path >
```

<span data-ttu-id="58b7c-p127">Dabei ist Pfad der Pfad zu dem Ordner, der die Anlagen enthält. Sie können Platzhalter zusätzlich relative Pfade zu verwenden. Beispielsweise alle Anlagen in der Masterpages-Ordner für alle Ihre Websites als einen öffentlichen Ursprung innerhalb der CDN aufnehmen möchten, geben Sie den folgenden Befehl ein:</span><span class="sxs-lookup"><span data-stu-id="58b7c-p127">Where path is the path to the folder that contains the assets. You can use wildcards in addition to relative paths. For example, to include all of the assets in the masterpages folder for all of your sites as a public origin within the CDN, type the following command:</span></span>
  
```
Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
```

<span data-ttu-id="58b7c-234">Weitere Informationen zu diesem Befehl und die Syntax finden Sie unter [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).</span><span class="sxs-lookup"><span data-stu-id="58b7c-234">For more information about this command and its syntax, see [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).</span></span>
  
<span data-ttu-id="58b7c-p128">Nachdem Sie den Befehl ausgeführt haben, synchronisiert das System die Konfiguration über das Rechenzentrum hinweg. Dadurch gelangen 15 Minuten.</span><span class="sxs-lookup"><span data-stu-id="58b7c-p128">Once you've run the command, the system synchronizes the configuration across the datacenter. This takes 15 minutes.</span></span>
  
### <a name="example-configure-a-public-origin-for-your-master-pages-and-for-your-style-library-for-sharepoint-online"></a><span data-ttu-id="58b7c-237">Beispiel: Konfigurieren einer öffentlichen Origin für Ihre Gestaltungsvorlagen und für die Formatbibliothek für SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="58b7c-237">Example: Configure a public origin for your master pages and for your style library for SharePoint Online</span></span>
<span data-ttu-id="58b7c-238"><a name="ExamplePublicOrigin"> </a></span><span class="sxs-lookup"><span data-stu-id="58b7c-238"></span></span>

<span data-ttu-id="58b7c-p129">In der Regel sind diesen Herkunft eingerichtet Sie standardmäßig Wenn Sie für die Office 365-CDN öffentliche Herkunft aktivieren. Jedoch, wenn Sie diese manuell aktivieren möchten, gehen Sie folgendermaßen vor.</span><span class="sxs-lookup"><span data-stu-id="58b7c-p129">Normally, these origins are set up for you by default when you enable public origins for the Office 365 CDN. However, if you want to enable them manually, follow these steps.</span></span>
  
- <span data-ttu-id="58b7c-241">Verwenden Sie das Cmdlet **Add-SPOTenantCdnOrigin** , um die Formatbibliothek als einen öffentlichen Ursprung innerhalb der Office 365-CDN definieren.</span><span class="sxs-lookup"><span data-stu-id="58b7c-241">Use the **Add-SPOTenantCdnOrigin** cmdlet to define the style library as a public origin within the Office 365 CDN.</span></span> 
    
  ```
  Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */style%20library
  ```

- <span data-ttu-id="58b7c-242">Verwenden Sie das Cmdlet **Add-SPOTenantCdnOrigin** , um die Masterseiten als einen öffentlichen Ursprung innerhalb der Office 365-CDN definieren.</span><span class="sxs-lookup"><span data-stu-id="58b7c-242">Use the **Add-SPOTenantCdnOrigin** cmdlet to define the master pages as a public origin within the Office 365 CDN.</span></span> 
    
  ```
  Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
  ```

- <span data-ttu-id="58b7c-243">Weitere Informationen zu diesem Befehl und die Syntax finden Sie unter [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).</span><span class="sxs-lookup"><span data-stu-id="58b7c-243">For more information about this command and its syntax, see [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).</span></span>
    
    <span data-ttu-id="58b7c-p130">Nachdem Sie den Befehl ausgeführt haben, synchronisiert das System die Konfiguration über das Rechenzentrum hinweg. Dadurch gelangen 15 Minuten.</span><span class="sxs-lookup"><span data-stu-id="58b7c-p130">Once you've run the command, the system synchronizes the configuration across the datacenter. This takes 15 minutes.</span></span>
    
### <a name="example-configure-a-private-origin-for-your-site-assets-site-pages-and-publishing-images-for-sharepoint-online"></a><span data-ttu-id="58b7c-246">Beispiel: Konfigurieren einer privaten Origin für Ihre Website-Objekten, Websiteseiten und veröffentlichte Bilder für SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="58b7c-246">Example: Configure a private origin for your site assets, site pages, and publishing images for SharePoint Online</span></span>
<span data-ttu-id="58b7c-247"><a name="ExamplePrivateOrigin"> </a></span><span class="sxs-lookup"><span data-stu-id="58b7c-247"></span></span>

- <span data-ttu-id="58b7c-248">Verwenden Sie das Cmdlet **Add-SPOTenantCdnOrigin** , um Anlagen-Ordner der Website als eine private Ursprung innerhalb der Office 365-CDN definieren.</span><span class="sxs-lookup"><span data-stu-id="58b7c-248">Use the **Add-SPOTenantCdnOrigin** cmdlet to define the site assets folder as a private origin within the Office 365 CDN.</span></span> 
    
  ```
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */siteassets
  ```

- <span data-ttu-id="58b7c-249">Verwenden Sie das Cmdlet **Add-SPOTenantCdnOrigin** , um den Ordner der Website-Seiten als einen privaten Ursprung innerhalb der Office 365-CDN definieren.</span><span class="sxs-lookup"><span data-stu-id="58b7c-249">Use the **Add-SPOTenantCdnOrigin** cmdlet to define the site pages folder as a private origin within the Office 365 CDN.</span></span> 
    
  ```
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */sitepages
  ```

- <span data-ttu-id="58b7c-250">Verwenden Sie das Cmdlet **Add-SPOTenantCdnOrigin** um publishing Ordner Images als einen privaten Ursprung innerhalb der Office 365-CDN definieren.</span><span class="sxs-lookup"><span data-stu-id="58b7c-250">Use the **Add-SPOTenantCdnOrigin** cmdlet to define the publishing images folder as a private origin within the Office 365 CDN.</span></span> 
    
  ```
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */publishingimages
  ```

    <span data-ttu-id="58b7c-251">Weitere Informationen zu diesem Befehl und die Syntax finden Sie unter [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).</span><span class="sxs-lookup"><span data-stu-id="58b7c-251">For more information about this command and its syntax, see [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).</span></span>
    
    <span data-ttu-id="58b7c-p131">Nachdem Sie den Befehl ausgeführt haben, synchronisiert das System die Konfiguration über das Rechenzentrum hinweg. Dadurch gelangen 15 Minuten.</span><span class="sxs-lookup"><span data-stu-id="58b7c-p131">Once you've run the command, the system synchronizes the configuration across the datacenter. This takes 15 minutes.</span></span>
    
### <a name="example-configure-a-private-origin-for-a-site-collection-for-sharepoint-online"></a><span data-ttu-id="58b7c-254">Beispiel: Konfigurieren einer privaten Origin für eine Websitesammlung für SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="58b7c-254">Example: Configure a private origin for a site collection for SharePoint Online</span></span>
<span data-ttu-id="58b7c-255"><a name="ExamplePrivateOriginSiteCollection"> </a></span><span class="sxs-lookup"><span data-stu-id="58b7c-255"></span></span>

<span data-ttu-id="58b7c-p132">Verwenden Sie das Cmdlet **Add-SPOTenantCdnOrigin** , um eine Websitesammlung als einen privaten Ursprung innerhalb der Office 365-CDN definieren. Zum Beispiel</span><span class="sxs-lookup"><span data-stu-id="58b7c-p132">Use the **Add-SPOTenantCdnOrigin** cmdlet to define a site collection as a private origin within the Office 365 CDN. For example,</span></span> 
  
```
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl sites/site1/siteassets
```

<span data-ttu-id="58b7c-258">Weitere Informationen zu diesem Befehl und die Syntax finden Sie unter [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).</span><span class="sxs-lookup"><span data-stu-id="58b7c-258">For more information about this command and its syntax, see [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).</span></span>
  
<span data-ttu-id="58b7c-p133">Nachdem Sie den Befehl ausgeführt haben, synchronisiert das System die Konfiguration über das Rechenzentrum hinweg. Dadurch gelangen 15 Minuten.</span><span class="sxs-lookup"><span data-stu-id="58b7c-p133">Once you've run the command, the system synchronizes the configuration across the datacenter. This takes 15 minutes.</span></span>
  
## <a name="manage-the-office-365-cdn"></a><span data-ttu-id="58b7c-261">Verwalten von Office 365 CDN</span><span class="sxs-lookup"><span data-stu-id="58b7c-261">Manage the Office 365 CDN</span></span>
<span data-ttu-id="58b7c-262"><a name="CDNManage"> </a></span><span class="sxs-lookup"><span data-stu-id="58b7c-262"></span></span>

<span data-ttu-id="58b7c-263">Nach dem CDN eingerichtet haben, können Sie Ihre Konfiguration ändern wie Inhalte zu aktualisieren oder Ihre Bedürfnisse anpassen, wie in diesem Abschnitt beschrieben.</span><span class="sxs-lookup"><span data-stu-id="58b7c-263">Once you've set up the CDN, you can make changes to your configuration as you update content or as your needs change, as described in this section.</span></span>
  
### <a name="to-add-update-or-remove-assets-from-the-office-365-cdn"></a><span data-ttu-id="58b7c-264">Hinzufügen, aktualisieren oder Entfernen von Anlagen aus dem Office 365 CDN</span><span class="sxs-lookup"><span data-stu-id="58b7c-264">To add, update, or remove assets from the Office 365 CDN</span></span>
<span data-ttu-id="58b7c-265"><a name="Office365CDNforSPOaddremoveasset"> </a></span><span class="sxs-lookup"><span data-stu-id="58b7c-265"></span></span>

<span data-ttu-id="58b7c-p134">Nachdem Sie die Setupschritte abgeschlossen haben, können Sie hinzufügen neue Anlagen und aktualisieren oder entfernen vorhandene Ressourcen, wenn Sie möchten. Stellen Sie nur die Änderungen auf Elemente in den Ordner oder die SharePoint-Bibliothek, die Sie als einen Ursprung identifiziert. Wenn Sie eine neue Anlage hinzufügen, wird es sofort über das CDN verfügbar. Jedoch, wenn Sie die Anlage aktualisieren, dauert es bis zu 15 Minuten für die neue Kopie verbreiten und in dem CDN zur Verfügung stehen.</span><span class="sxs-lookup"><span data-stu-id="58b7c-p134">Once you've completed the setup steps, you can add new assets, and update or remove existing assets whenever you want. Just make your changes to the assets in the folder or SharePoint library that you identified as an origin. If you add a new asset, it is available through the CDN immediately. However, if you update the asset, it will take up to 15 minutes for the new copy to propagate and become available in the CDN.</span></span>
  
<span data-ttu-id="58b7c-p135">Wenn Sie den Speicherort des Ursprungs abrufen möchten, können Sie das Cmdlet **Get-SPOTenantCdnOrigins** verwenden. Informationen zum Verwenden dieses Cmdlet finden Sie unter [Get-SPOTenantCdnOrigins](https://technet.microsoft.com/en-us/library/mt790770.aspx).</span><span class="sxs-lookup"><span data-stu-id="58b7c-p135">If you need to retrieve the location of the origin, you can use the **Get-SPOTenantCdnOrigins** cmdlet. For information on how to use this cmdlet, see [Get-SPOTenantCdnOrigins](https://technet.microsoft.com/en-us/library/mt790770.aspx).</span></span>
  
### <a name="to-remove-an-origin-from-the-office-365-cdn"></a><span data-ttu-id="58b7c-272">So entfernen einen Ursprung aus dem Office 365 CDN</span><span class="sxs-lookup"><span data-stu-id="58b7c-272">To remove an origin from the Office 365 CDN</span></span>
<span data-ttu-id="58b7c-273"><a name="Office365CDNforSPORemoveOrigin"> </a></span><span class="sxs-lookup"><span data-stu-id="58b7c-273"></span></span>

<span data-ttu-id="58b7c-p136">Wenn Sie möchten, können Sie Zugriff auf einen Ordner oder SharePoint-Bibliothek, die Sie als einen Ursprung identifiziert entfernen. Verwenden Sie hierzu das Cmdlet **Remove-SPOTenantCdnOrigin** . Informationen zum Verwenden dieses Cmdlet finden Sie unter [Remove-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790761.aspx).</span><span class="sxs-lookup"><span data-stu-id="58b7c-p136">If you need to, you can remove access to a folder or SharePoint library that you identified as an origin. To do this, use the **Remove-SPOTenantCdnOrigin** cmdlet. For information on how to use this cmdlet, see [Remove-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790761.aspx).</span></span>
  
### <a name="to-modify-an-origin-in-the-office-365-cdn"></a><span data-ttu-id="58b7c-277">So ändern Sie einen Ursprung in der Office 365-CDN</span><span class="sxs-lookup"><span data-stu-id="58b7c-277">To modify an origin in the Office 365 CDN</span></span>
<span data-ttu-id="58b7c-278"><a name="Office365CDNforSPORemoveOrigin"> </a></span><span class="sxs-lookup"><span data-stu-id="58b7c-278"></span></span>

<span data-ttu-id="58b7c-p137">Die von den Ihnen erstellten können nicht Ursprung geändert werden. Stattdessen entfernen Sie Ursprung zu, und fügen Sie einen neuen Anwendungspool. Weitere Informationen finden Sie unter [Ursprung aus dem Office 365 CDN entfernen](use-office-365-cdn-with-spo.md#Office365CDNforSPORemoveOrigin) und [einen Ursprung für Ihre Anlagen hinzuzufügen](use-office-365-cdn-with-spo.md#Office365CDNforSPOOrigin).</span><span class="sxs-lookup"><span data-stu-id="58b7c-p137">You can't modify an origin you've created. Instead, remove the origin and then add a new one. For more information, see [To remove an origin from the Office 365 CDN](use-office-365-cdn-with-spo.md#Office365CDNforSPORemoveOrigin) and [To add an origin for your assets](use-office-365-cdn-with-spo.md#Office365CDNforSPOOrigin).</span></span>
  
### <a name="to-disable-the-office-365-cdn"></a><span data-ttu-id="58b7c-282">So deaktivieren Sie das Office 365 CDN</span><span class="sxs-lookup"><span data-stu-id="58b7c-282">To disable the Office 365 CDN</span></span>
<span data-ttu-id="58b7c-283"><a name="Office365CDNforSPODisable"> </a></span><span class="sxs-lookup"><span data-stu-id="58b7c-283"></span></span>

<span data-ttu-id="58b7c-p138">Verwenden Sie das **Set-SPOTenantCdnEnabled** -Cmdlet, um dem CDN für Ihre Organisation zu deaktivieren. Wenn Sie sowohl die öffentliche und private Herkunft für das CDN aktiviert haben, müssen Sie das Cmdlet zweimal, wie in den folgenden Beispielen gezeigt ausführen.</span><span class="sxs-lookup"><span data-stu-id="58b7c-p138">Use the **Set-SPOTenantCdnEnabled** cmdlet to disable the CDN for your organization. If you have both the public and private origins enabled for the CDN, you need to run the cmdlet twice as shown in the following examples.</span></span> 
  
<span data-ttu-id="58b7c-286">Geben Sie den folgenden Befehl, um die Verwendung von öffentlichen Herkunft in der CDN in Windows Powershell für SharePoint Online zu deaktivieren:</span><span class="sxs-lookup"><span data-stu-id="58b7c-286">To disable use of public origins in the CDN, in Windows Powershell for SharePoint Online, enter the following command:</span></span>
  
```
Set-SPOTenantCdnEnabled -CdnType Public -Enable $false
```

<span data-ttu-id="58b7c-287">Geben Sie den folgenden Befehl, um die Verwendung von der privaten Herkunft in dem CDN zu deaktivieren:</span><span class="sxs-lookup"><span data-stu-id="58b7c-287">To disable use of the private origins in the CDN, enter the following command:</span></span>
  
```
Set-SPOTenantCdnEnabled -CdnType Private -Enable $false
```

<span data-ttu-id="58b7c-288">Weitere Informationen zu diesem Cmdlet finden Sie unter [Set-SPOTenantCdnEnabled](https://technet.microsoft.com/en-us/library/mt790765.aspx).</span><span class="sxs-lookup"><span data-stu-id="58b7c-288">For more information about this cmdlet, see [Set-SPOTenantCdnEnabled](https://technet.microsoft.com/en-us/library/mt790765.aspx).</span></span>
  
## <a name="troubleshooting-your-office-365-cdn-configuration"></a><span data-ttu-id="58b7c-289">Problembehandlung bei der Office 365 CDN-Konfiguration</span><span class="sxs-lookup"><span data-stu-id="58b7c-289">Troubleshooting your Office 365 CDN configuration</span></span>
<span data-ttu-id="58b7c-290"><a name="CDNManage"> </a></span><span class="sxs-lookup"><span data-stu-id="58b7c-290"></span></span>

<span data-ttu-id="58b7c-p139">Der Endpunkt werden sofort einsatzbereit, nicht wie es Zeit für die Registrierung über das CDN weitergegeben. Konfiguration nimmt 15 Minuten.</span><span class="sxs-lookup"><span data-stu-id="58b7c-p139">The endpoint will not immediately be available for use, as it takes time for the registration to propagate through the CDN. Configuration takes 15 minutes.</span></span>
  

