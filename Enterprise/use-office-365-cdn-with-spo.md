---
title: Verwenden des Office 365 Content Delivery Network (CDN) mit SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 4/3/2019
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
description: Beschreibt, wie das Office 365 Content Delivery Network (CDN) verwendet wird, um die Bereitstellen Ihrer SharePoint Online-Objekte für alle Ihre Benutzer zu beschleunigen, unabhängig davon, wo Sie sich befinden oder wie Sie auf Ihre Inhalte zugreifen.
ms.openlocfilehash: ceb66b3e17baf25a292b4903c569b931f9448f71
ms.sourcegitcommit: 100ae697304427dab5ad494a06323656b498c57e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/03/2019
ms.locfileid: "31396923"
---
# <a name="use-the-office-365-content-delivery-network-cdn-with-sharepoint-online"></a><span data-ttu-id="ee801-103">Verwenden des Office 365 Content Delivery Network (CDN) mit SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="ee801-103">Use the Office 365 Content Delivery Network (CDN) with SharePoint Online</span></span>

<span data-ttu-id="ee801-104">Sie können statische Objekte im Office 365-Netzwerk für die Inhaltsübermittlung (CDN) hosten, um eine bessere Leistung für Ihre SharePoint Online-Seiten zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="ee801-104">You can use the built-in Office 365 Content Delivery Network (CDN) to host static assets to provide better performance for your SharePoint Online pages.</span></span> <span data-ttu-id="ee801-105">Das Office 365-Netzwerk für die Inhaltsübermittlung verbessert die Leistung, indem statische Objekte näher an den Browsern zwischengespeichert werden, die diese anfordern, wodurch Downloads beschleunigt werden und die Latenz reduziert wird.</span><span class="sxs-lookup"><span data-stu-id="ee801-105">The Office 365 CDN improves performance by caching static assets closer to the browsers requesting them, which helps to speed up downloads and reduce latency.</span></span> <span data-ttu-id="ee801-106">Außerdem verwendet das Office 365 CDN das [http/2-Protokoll](https://en.wikipedia.org/wiki/HTTP/2) für eine verbesserte KOMPRIMIERUNG und HTTP-Pipelining.</span><span class="sxs-lookup"><span data-stu-id="ee801-106">Also, the Office 365 CDN uses the [HTTP/2 protocol](https://en.wikipedia.org/wiki/HTTP/2) for improved compression and HTTP pipelining.</span></span> <span data-ttu-id="ee801-107">Das Office 365-Netzwerk für die Inhaltsübermittlung ist in Ihrem SharePoint Online-Abonnement enthalten.</span><span class="sxs-lookup"><span data-stu-id="ee801-107">The Office 365 CDN service is included as part of your SharePoint Online subscription.</span></span>

<span data-ttu-id="ee801-108">Das Office 365-Netzwerk für die Inhaltsübermittlung besteht aus mehreren CDNs, über die Sie statische Objekte an mehreren Speicherorten hosten können, oder aus _Ursprüngen_, die aus globalen Hochgeschwindigkeitsnetzwerken bedient werden.</span><span class="sxs-lookup"><span data-stu-id="ee801-108">The Office 365 CDN is composed of multiple CDNs that allow you to host static assets in multiple locations, or _origins_, and serve them from global high-speed networks.</span></span> <span data-ttu-id="ee801-109">In Abhängigkeit von der Art der Inhalte, die Sie im Office 365-Netzwerk für die Inhaltsübermittlung hosten möchten, können Sie **öffentliche** Ursprünge, **private** Ursprünge oder beides hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="ee801-109">Depending on the kind of content you want to host in the Office 365 CDN, you can add **public** origins, **private** origins or both.</span></span> <span data-ttu-id="ee801-110">Weitere Informationen zum Unterschied zwischen öffentlichen und privaten Ursprüngen finden Sie unter [Wählen Sie, ob jeder Ursprung öffentlich oder privat sein soll](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate) .</span><span class="sxs-lookup"><span data-stu-id="ee801-110">See [Choose whether each origin should be public or private](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate) for more information on the difference between public and private origins.</span></span>

<span data-ttu-id="ee801-111">![Office 365 CDN-konzeptionelles Diagramm] (media/O365-CDN/o365-cdn-flow-transparent.svg "Office 365 CDN-konzeptionelles Diagramm")</span><span class="sxs-lookup"><span data-stu-id="ee801-111">![Office 365 CDN conceptual diagram](media/O365-CDN/o365-cdn-flow-transparent.svg "Office 365 CDN conceptual diagram")</span></span>

<span data-ttu-id="ee801-112">Wenn Sie bereits mit der Funktionsweise von CDNs vertraut sind, müssen Sie nur einige Schritte ausführen, um das Office 365 CDN für Ihren Mandanten zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="ee801-112">If you are already familiar with the way that CDNs work, you only need to complete a few steps to enable the Office 365 CDN for your tenant.</span></span> <span data-ttu-id="ee801-113">In diesem Thema wird beschrieben, wie.</span><span class="sxs-lookup"><span data-stu-id="ee801-113">This topic describes how.</span></span> <span data-ttu-id="ee801-114">Lesen Sie weiter, um zu erfahren, wie Sie mit dem Hosten Ihrer statischen Objekte beginnen.</span><span class="sxs-lookup"><span data-stu-id="ee801-114">Read on for information about how to get started hosting your static assets.</span></span>

> [!TIP]
> <span data-ttu-id="ee801-115">Es gibt weitere von Microsoft gehostete CDNs, die mit Office 365 für spezielle Verwendungsszenarien verwendet werden können, aber nicht in diesem Thema behandelt werden, da Sie nicht in den Bereich des Office 365 CDN fallen.</span><span class="sxs-lookup"><span data-stu-id="ee801-115">There are other Microsoft-hosted CDNs that can be used with Office 365 for specialized usage scenarios, but are not discussed in this topic because they fall outside the scope of the Office 365 CDN.</span></span> <span data-ttu-id="ee801-116">Weitere Informationen finden Sie unter [andere Microsoft-CDNs](content-delivery-networks.md#other-microsoft-cdns).</span><span class="sxs-lookup"><span data-stu-id="ee801-116">For more information, see [Other Microsoft CDNs](content-delivery-networks.md#other-microsoft-cdns).</span></span>

 **<span data-ttu-id="ee801-117">Gehen Sie zurück zur [Netzwerkplanung und Leistungsoptimierung für Office 365](https://aka.ms/tune).</span><span class="sxs-lookup"><span data-stu-id="ee801-117">Head back to [Network planning and performance tuning for Office 365](https://aka.ms/tune).</span></span>**

## <a name="overview-of-working-with-the-office-365-cdn-in-sharepoint-online"></a><span data-ttu-id="ee801-118">Übersicht über das Arbeiten mit dem Office 365 CDN in SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="ee801-118">Overview of working with the Office 365 CDN in SharePoint Online</span></span>

<span data-ttu-id="ee801-119">Führen Sie die folgenden grundlegenden Schritte aus, um das Office 365 CDN für Ihre Organisation einzurichten:</span><span class="sxs-lookup"><span data-stu-id="ee801-119">To set up the Office 365 CDN for your organization, you follow these basic steps:</span></span>

- [<span data-ttu-id="ee801-120">Planen der Bereitstellung von Office 365 CDN</span><span class="sxs-lookup"><span data-stu-id="ee801-120">Plan for deployment of the Office 365 CDN</span></span>](use-office-365-cdn-with-spo.md#plan-for-deployment-of-the-office-365-cdn)

  - <span data-ttu-id="ee801-121">[Legen Sie fest, welche statischen Objekte im CDN gehostet werden sollen](use-office-365-cdn-with-spo.md#CDNAssets).</span><span class="sxs-lookup"><span data-stu-id="ee801-121">[Determine which static assets you want to host on the CDN](use-office-365-cdn-with-spo.md#CDNAssets).</span></span>
  - <span data-ttu-id="ee801-122">[Bestimmen Sie, wo Ihre Objekte gespeichert werden sollen](use-office-365-cdn-with-spo.md#CDNStoreAssets).</span><span class="sxs-lookup"><span data-stu-id="ee801-122">[Determine where you want to store your assets](use-office-365-cdn-with-spo.md#CDNStoreAssets).</span></span> <span data-ttu-id="ee801-123">Dieser Speicherort kann eine SharePoint-Website,-Bibliothek oder-Ordner sein und als _Ursprung_bezeichnet werden.</span><span class="sxs-lookup"><span data-stu-id="ee801-123">This location can be a SharePoint site, library or folder and is called an _origin_.</span></span>
  - <span data-ttu-id="ee801-124">[Wählen Sie aus, ob jeder Ursprung öffentlich oder privat sein soll](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate).</span><span class="sxs-lookup"><span data-stu-id="ee801-124">[Choose whether each origin should be public or private](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate).</span></span> <span data-ttu-id="ee801-125">Sie können mehrere Ursprünge sowohl öffentlicher als auch privater Typen hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="ee801-125">You can add multiple origins of both public and private types.</span></span>

- <span data-ttu-id="ee801-126">Einrichten und Konfigurieren des CDN, entweder mit PowerShell oder mit der SharePoint Online-CLI</span><span class="sxs-lookup"><span data-stu-id="ee801-126">Set up and configure the CDN, using either PowerShell or the SharePoint Online CLI</span></span>

  - [<span data-ttu-id="ee801-127">Einrichten und Konfigurieren des CDN mithilfe der SharePoint Online-Verwaltungsshell</span><span class="sxs-lookup"><span data-stu-id="ee801-127">Set up and configure the CDN by using the SharePoint Online Management Shell</span></span>](use-office-365-cdn-with-spo.md#CDNSetupinPShell)
  - [<span data-ttu-id="ee801-128">Einrichten und Konfigurieren des CDN mithilfe der Office 365 CLI</span><span class="sxs-lookup"><span data-stu-id="ee801-128">Set up and configure the CDN by using the Office 365 CLI</span></span>](use-office-365-cdn-with-spo.md#CDNSetupinCLI)

  <span data-ttu-id="ee801-129">Wenn Sie diesen Schritt abgeschlossen haben, haben Sie folgende Möglichkeiten:</span><span class="sxs-lookup"><span data-stu-id="ee801-129">When you complete this step, you will have:</span></span>

  - <span data-ttu-id="ee801-130">CDN für Ihre Organisation aktiviert.</span><span class="sxs-lookup"><span data-stu-id="ee801-130">Enabled the CDN for your organization.</span></span>
  - <span data-ttu-id="ee801-131">Ihre Ursprünge wurden HinzugeFügt, wobei jeder Ursprung als öffentlich oder privat identifiziert wurde.</span><span class="sxs-lookup"><span data-stu-id="ee801-131">Added your origins, identifying each origin as public or private.</span></span>

<span data-ttu-id="ee801-132">Nachdem Sie das Setup abgeschlossen haben, können Sie [das Office 365 CDN](use-office-365-cdn-with-spo.md#CDNManage) im Laufe der Zeit verwalten:</span><span class="sxs-lookup"><span data-stu-id="ee801-132">Once you're done with setup, you can [Manage the Office 365 CDN](use-office-365-cdn-with-spo.md#CDNManage) over time by:</span></span>
  
- <span data-ttu-id="ee801-133">Hinzufügen, aktualisieren und Entfernen von Objekten</span><span class="sxs-lookup"><span data-stu-id="ee801-133">Adding, updating, and removing assets</span></span>
- <span data-ttu-id="ee801-134">Hinzufügen und Entfernen von Ursprüngen</span><span class="sxs-lookup"><span data-stu-id="ee801-134">Adding and removing origins</span></span>
- <span data-ttu-id="ee801-135">Konfigurieren von CDN-Richtlinien</span><span class="sxs-lookup"><span data-stu-id="ee801-135">Configuring CDN policies</span></span>
- <span data-ttu-id="ee801-136">Falls erforderlich, Deaktivieren des CDN</span><span class="sxs-lookup"><span data-stu-id="ee801-136">If necessary, disabling the CDN</span></span>

<span data-ttu-id="ee801-137">Lesen Sie schließlich, wie Sie [Ihre CDN-Ressourcen verwenden](use-office-365-cdn-with-spo.md#using-your-cdn-assets) , um mehr über den Zugriff auf Ihre CDN-Ressourcen aus öffentlichen und privaten Quellen zu erfahren.</span><span class="sxs-lookup"><span data-stu-id="ee801-137">Finally, see [Using your CDN assets](use-office-365-cdn-with-spo.md#using-your-cdn-assets) to learn about accessing your CDN assets from both public and private origins.</span></span>

<span data-ttu-id="ee801-138">Hinweise zur Lösung häufig auftretender Probleme finden Sie unter [Troubleshooting the Office 365 CDN](use-office-365-cdn-with-spo.md#CDNTroubleshooting) .</span><span class="sxs-lookup"><span data-stu-id="ee801-138">See [Troubleshooting the Office 365 CDN](use-office-365-cdn-with-spo.md#CDNTroubleshooting) for guidance on resolving common issues.</span></span>

## <a name="plan-for-deployment-of-the-office-365-cdn"></a><span data-ttu-id="ee801-139">Planen der Bereitstellung von Office 365 CDN</span><span class="sxs-lookup"><span data-stu-id="ee801-139">Plan for deployment of the Office 365 CDN</span></span>

<span data-ttu-id="ee801-140">Bevor Sie das Office 365 CDN für Ihren Office 365-Mandanten bereitstellen, sollten Sie die folgenden Faktoren als Teil des Planungsprozesses berücksichtigen.</span><span class="sxs-lookup"><span data-stu-id="ee801-140">Before you deploy the Office 365 CDN for your Office 365 tenant, you should consider the following factors as part of your planning process.</span></span>

  - [<span data-ttu-id="ee801-141">Bestimmen der statischen Objekte, die im CDN gehostet werden sollen</span><span class="sxs-lookup"><span data-stu-id="ee801-141">Determine which static assets you want to host on the CDN</span></span>](use-office-365-cdn-with-spo.md#CDNAssets)
  - [<span data-ttu-id="ee801-142">Bestimmen, wo Ihre Objekte gespeichert werden sollen</span><span class="sxs-lookup"><span data-stu-id="ee801-142">Determine where you want to store your assets</span></span>](use-office-365-cdn-with-spo.md#CDNStoreAssets)
  - [<span data-ttu-id="ee801-143">Wählen Sie aus, ob jeder Ursprung öffentlich oder privat sein soll.</span><span class="sxs-lookup"><span data-stu-id="ee801-143">Choose whether each origin should be public or private</span></span>](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate)

### <a name="determine-which-static-assets-you-want-to-host-on-the-cdn"></a><span data-ttu-id="ee801-144">Bestimmen der statischen Objekte, die im CDN gehostet werden sollen</span><span class="sxs-lookup"><span data-stu-id="ee801-144">Determine which static assets you want to host on the CDN</span></span>
<a name="CDNAssets"> </a>

<span data-ttu-id="ee801-145">Im Allgemeinen sind CDNs am effektivsten für das Hosten _statischer Objekte_oder für Objekte, die sich nicht sehr häufig ändern.</span><span class="sxs-lookup"><span data-stu-id="ee801-145">In general, CDNs are most effective for hosting _static assets_, or assets that don't change very often.</span></span> <span data-ttu-id="ee801-146">Eine gute Faustregel besteht darin, Dateien zu identifizieren, die einige oder alle dieser Bedingungen erfüllen:</span><span class="sxs-lookup"><span data-stu-id="ee801-146">A good rule of thumb is to identify files that meet some or all of these conditions:</span></span>

- <span data-ttu-id="ee801-147">In eine Seite eingebettete statische Dateien (wie Skripts und Bilder), die sich möglicherweise erheblich inkrementell auf Seitenladezeiten auswirken</span><span class="sxs-lookup"><span data-stu-id="ee801-147">Static files embedded in a page (like scripts and images) that may have a significant incremental impact on page load times</span></span>
- <span data-ttu-id="ee801-148">Umfangreiche Dateien wie Executables und Installationsdateien</span><span class="sxs-lookup"><span data-stu-id="ee801-148">Large files like executables and installation files</span></span>
- <span data-ttu-id="ee801-149">Streaming-Mediendateien</span><span class="sxs-lookup"><span data-stu-id="ee801-149">Streaming media files</span></span>
- <span data-ttu-id="ee801-150">Ressourcen Bibliotheken, die clientseitigen Code unterstützen</span><span class="sxs-lookup"><span data-stu-id="ee801-150">Resource libraries that support client-side code</span></span>

<span data-ttu-id="ee801-151">Beispielsweise können kleine Dateien, die wiederholt wie Website Bilder und Skripts angefordert werden, die Leistung des Website Renderings erheblich verbessern und die Last für Ihre SharePoint Online-Websites inkrementell verringern, wenn Sie Sie zu einem CDN-Ursprung hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="ee801-151">For example, small files that are repeatedly requested like site images and scripts can significantly improve site rendering performance and incrementally reduce the load on your SharePoint Online sites when you add them to a CDN origin.</span></span> <span data-ttu-id="ee801-152">Größere Dateien wie Installations-Executables oder Videodateien können heruntergeladen oder aus dem CDN gestreamt werden, was eine positive Leistungsbeeinträchtigung und eine anschließende Reduzierung der Last auf Ihrer SharePoint Online-Website ermöglicht, auch wenn nicht so oft auf Sie zugegriffen wird.</span><span class="sxs-lookup"><span data-stu-id="ee801-152">Larger files such as installation executables or video files can be downloaded or streamed from the CDN, delivering a positive performance impact and subsequent reduction of the load on your SharePoint Online site, even if they are not accessed as often.</span></span>

<span data-ttu-id="ee801-153">Die Leistungsverbesserung pro Datei hängt von vielen Faktoren ab, einschließlich der Nähe des Clients zum nächstgelegenen CDN-Endpunkt, Transienten Bedingungen im lokalen Netzwerk usw.</span><span class="sxs-lookup"><span data-stu-id="ee801-153">Performance improvement on a per-file basis is dependent on many factors, including the client's proximity to the nearest CDN endpoint, transient conditions on the local network, and so forth.</span></span> <span data-ttu-id="ee801-154">Viele statische Dateien sind relativ klein und können von Office 365 in weniger als einer Sekunde heruntergeladen werden.</span><span class="sxs-lookup"><span data-stu-id="ee801-154">Many static files are quite small, and can be downloaded from Office 365 in less than a second.</span></span> <span data-ttu-id="ee801-155">Eine Webseite kann jedoch viele eingebettete Dateien mit einer kumulativen Downloadzeit von mehreren Sekunden enthalten.</span><span class="sxs-lookup"><span data-stu-id="ee801-155">However, a web page may contain many embedded files with a cumulative download time of several seconds.</span></span> <span data-ttu-id="ee801-156">Die bereitstellungdieser Dateien aus dem CDN kann die Ladezeit der gesamten Seite erheblich reduzieren.</span><span class="sxs-lookup"><span data-stu-id="ee801-156">Serving these files from the CDN can significantly reduce the overall page load time.</span></span> <span data-ttu-id="ee801-157">Sehen Sie, [welche Leistungssteigerungen ein CDN bereitstellt](content-delivery-networks.md#what-performance-gains-does-a-cdn-provide) . ein Beispiel.</span><span class="sxs-lookup"><span data-stu-id="ee801-157">See [What performance gains does a CDN provide?](content-delivery-networks.md#what-performance-gains-does-a-cdn-provide) for an example.</span></span>

### <a name="determine-where-you-want-to-store-your-assets"></a><span data-ttu-id="ee801-158">Bestimmen, wo Ihre Objekte gespeichert werden sollen</span><span class="sxs-lookup"><span data-stu-id="ee801-158">Determine where you want to store your assets</span></span>
<a name="CDNStoreAssets"> </a>

<span data-ttu-id="ee801-159">Das CDN ruft Ihre Objekte von einem Speicherort ab, der als _Ursprung_bezeichnet wird.</span><span class="sxs-lookup"><span data-stu-id="ee801-159">The CDN fetches your assets from a location called an _origin_.</span></span> <span data-ttu-id="ee801-160">Bei einem Ursprung kann es sich um eine SharePoint-Website, eine Dokumentbibliothek oder einen Ordner handeln, auf die über eine URL zugegriffen wird.</span><span class="sxs-lookup"><span data-stu-id="ee801-160">An origin can be a SharePoint site, document library or folder that is accessible by a URL.</span></span> <span data-ttu-id="ee801-161">Sie haben große Flexibilität, wenn Sie die Ursprünge für Ihre Organisation angeben.</span><span class="sxs-lookup"><span data-stu-id="ee801-161">You have great flexibility when you specify origins for your organization.</span></span> <span data-ttu-id="ee801-162">Sie können beispielsweise mehrere Ursprünge oder einen einzelnen Ursprung angeben, in dem Sie alle CDN-Ressourcen platzieren möchten.</span><span class="sxs-lookup"><span data-stu-id="ee801-162">For example, you can specify multiple origins or a single origin where you want to put all your CDN assets.</span></span> <span data-ttu-id="ee801-163">Sie können sowohl öffentliche als auch private Ursprünge für Ihre Organisation wählen.</span><span class="sxs-lookup"><span data-stu-id="ee801-163">You can choose to have both public or private origins for your organization.</span></span> <span data-ttu-id="ee801-164">Die meisten Organisationen wählen eine Kombination der beiden implementieren.</span><span class="sxs-lookup"><span data-stu-id="ee801-164">Most organizations will choose to implement a combination of the two.</span></span>

<span data-ttu-id="ee801-165">Sie können neue Container für ihre Ursprünge wie Ordner oder Dokumentbibliotheken erstellen und Dateien hinzufügen, die Sie im CDN zur Verfügung stellen möchten.</span><span class="sxs-lookup"><span data-stu-id="ee801-165">You can create new container for your origins such as folders or document libraries, and add files you want to make available from the CDN.</span></span> <span data-ttu-id="ee801-166">Dies ist ein guter Ansatz, wenn Sie über einen bestimmten Satz von Objekten verfügen, die im CDN verfügbar sein sollen, und die Menge der CDN-Objekte auf die Dateien im Container einschränken möchten.</span><span class="sxs-lookup"><span data-stu-id="ee801-166">This is a good approach if you have a specific set of assets you want to be available from the CDN, and want to restrict the set of CDN assets to only those files in the container.</span></span>

<span data-ttu-id="ee801-167">Sie können auch eine vorhandene Websitesammlung, eine Website, eine Bibliothek oder einen Ordner als Ursprung konfigurieren, wodurch alle berechtigten Objekte im Container im CDN verfügbar gemacht werden.</span><span class="sxs-lookup"><span data-stu-id="ee801-167">You can also configure an existing site collection, site, library or folder as an origin, which will make all eligible assets in the container available from the CDN.</span></span> <span data-ttu-id="ee801-168">Bevor Sie einen vorhandenen Container als Ursprung hinzufügen, müssen Sie sicherstellen, dass Sie die Inhalte und Berechtigungen beachten, damit Sie Objekte nicht versehentlich anonymen Zugriffen oder nicht autorisierten Benutzern offen legen.</span><span class="sxs-lookup"><span data-stu-id="ee801-168">Before you add an existing container as an origin, it's important to make sure you are aware of its contents and permissions so you do not inadvertently expose assets to anonymous access or unauthorized users.</span></span>

<span data-ttu-id="ee801-169">Sie können _CDN-Richtlinien_ definieren, um Inhalte aus dem CDN auszuschließen.</span><span class="sxs-lookup"><span data-stu-id="ee801-169">You can define _CDN policies_ to exclude content in your origins from the CDN.</span></span> <span data-ttu-id="ee801-170">CDN-Richtlinien schließen Objekte in öffentlichen oder privaten Quellen nach Attributen wie _Dateityp_ und _Website Klassifizierung_aus und werden auf alle Ursprünge der CdnType (privat oder öffentlich) angewendet, die Sie in der Richtlinie angeben.</span><span class="sxs-lookup"><span data-stu-id="ee801-170">CDN policies exclude assets in public or private origins by attributes such as _file type_ and _site classification_, and are applied to all origins of the CdnType (private or public) you specify in the policy.</span></span> <span data-ttu-id="ee801-171">Wenn Sie beispielsweise einen privaten Ursprung hinzufügen, der aus einer Website besteht, die mehrere Unterwebsites enthält, können Sie eine Richtlinie zum Ausschließen von als **vertraulich** markierten Websites definieren, sodass Inhalte von Websites mit dieser Klassifizierung nicht aus dem CDN bedient werden.</span><span class="sxs-lookup"><span data-stu-id="ee801-171">For example, if you add a private origin consisting of a site that contains multiple subsites, you can define a policy to exclude sites marked as **Confidential** so content from sites with that classification applied will not be served from the CDN.</span></span> <span data-ttu-id="ee801-172">Die Richtlinie gilt für Inhalte _aller_ privaten Ursprünge, die Sie dem CDN hinzugefügt haben.</span><span class="sxs-lookup"><span data-stu-id="ee801-172">The policy will apply to content from _all_ private origins you have added to the CDN.</span></span>
  
<span data-ttu-id="ee801-173">Beachten Sie, dass je größer die Anzahl der Ursprünge ist, desto größer ist die Auswirkung auf die Zeit, die der CDN-Dienst zum Verarbeiten von Anforderungen benötigt.</span><span class="sxs-lookup"><span data-stu-id="ee801-173">Keep in mind that the greater the number of origins, the greater the impact on the time it takes the CDN service to process requests.</span></span> <span data-ttu-id="ee801-174">Es wird empfohlen, die Anzahl der Ursprünge so weit wie möglich zu begrenzen.</span><span class="sxs-lookup"><span data-stu-id="ee801-174">We recommend that you limit the number of origins as much as possible.</span></span>
  
### <a name="choose-whether-each-origin-should-be-public-or-private"></a><span data-ttu-id="ee801-175">Wählen Sie aus, ob jeder Ursprung öffentlich oder privat sein soll.</span><span class="sxs-lookup"><span data-stu-id="ee801-175">Choose whether each origin should be public or private</span></span>
<a name="CDNOriginChoosePublicPrivate"> </a>

<span data-ttu-id="ee801-176">Wenn Sie einen Ursprung identifizieren, geben Sie an, ob er _öffentlich_ oder _Privat_erfolgen soll.</span><span class="sxs-lookup"><span data-stu-id="ee801-176">When you identify an origin, you specify whether it should be made _public_ or _private_.</span></span> <span data-ttu-id="ee801-177">Der Zugriff auf CDN-Ressourcen in öffentlichen Quellen ist anonym, und CDN-Inhalte in privaten Quellen werden durch dynamisch generierte Token für größere Sicherheit gesichert.</span><span class="sxs-lookup"><span data-stu-id="ee801-177">Access to CDN assets in public origins is anonymous, and CDN content in private origins is secured by dynamically generated tokens for greater security.</span></span> <span data-ttu-id="ee801-178">Unabhängig davon, welche Option Sie auswählen, stellt Microsoft die gesamte Schwerlast für Sie, wenn es um die Verwaltung des CDN selbst geht.</span><span class="sxs-lookup"><span data-stu-id="ee801-178">Regardless of which option you choose, Microsoft does all the heavy lifting for you when it comes to administration of the CDN itself.</span></span> <span data-ttu-id="ee801-179">Außerdem können Sie Ihre Bedenken später ändern, nachdem Sie das CDN eingerichtet und ihre Ursprünge identifiziert haben.</span><span class="sxs-lookup"><span data-stu-id="ee801-179">Also, you can change your mind later, after you've set up the CDN and identified your origins.</span></span>

<span data-ttu-id="ee801-180">Sowohl öffentliche als auch private Optionen bieten ähnliche Leistungssteigerungen, verfügen jedoch über eindeutige Attribute und Vorteile.</span><span class="sxs-lookup"><span data-stu-id="ee801-180">Both public and private options provide similar performance gains, but each has unique attributes and advantages.</span></span>

<span data-ttu-id="ee801-181">**Öffentliche** Ursprünge innerhalb des Office 365 CDN sind anonym zugänglich, auf gehostete Ressourcen kann jeder zugreifen, der über die URL des Objekts verfügt.</span><span class="sxs-lookup"><span data-stu-id="ee801-181">**Public** origins within the Office 365 CDN are accessible anonymously, and hosted assets can be accessed by anyone who has the URL to the asset.</span></span> <span data-ttu-id="ee801-182">Da der Zugriff auf Inhalte in öffentlichen Ursprüngen anonym ist, sollten Sie diese nur zum Zwischenspeichern von nicht vertraulichen generischen Inhalten verwenden, z. B. JavaScript-Dateien, Skripts, Symbole oder Bilder.</span><span class="sxs-lookup"><span data-stu-id="ee801-182">Because access to content in public origins is anonymous, you should only use them to cache non-sensitive generic content such as javascript files, scripts, icons and images.</span></span>

<span data-ttu-id="ee801-183">**Private** Ursprünge im Office 365-Netzwerk für die Inhaltsübermittlung bieten privaten Zugriff auf Benutzerinhalte, z. B. SharePoint Online-Dokumentbibliotheken, Websites und Medien wie Videos.</span><span class="sxs-lookup"><span data-stu-id="ee801-183">**Private** origins within the Office 365 CDN provide private access to user content such as SharePoint Online document libraries, sites and media such as videos.</span></span> <span data-ttu-id="ee801-184">Der Zugriff auf Inhalte in privaten Quellen wird durch dynamisch generierte Token gesichert, sodass nur Benutzern mit Berechtigungen für die ursprüngliche Dokumentbibliothek oder den Speicherort zugegriffen werden kann.</span><span class="sxs-lookup"><span data-stu-id="ee801-184">Access to content in private origins is secured by dynamically generated tokens so it can only be accessed by users with permissions to the original document library or storage location.</span></span> <span data-ttu-id="ee801-185">Private Origins im Office 365 CDN können nur für SharePoint Online-Inhalte verwendet werden, und Sie können nur über die Umleitung von Ihrem SharePoint Online-Mandanten auf Objekte in privaten Quellen zugreifen.</span><span class="sxs-lookup"><span data-stu-id="ee801-185">Private origins in the Office 365 CDN can only be used for SharePoint Online content, and you can only access assets in private origins through redirection from your SharePoint Online tenant.</span></span>

<span data-ttu-id="ee801-186">Weitere Informationen dazu, wie der CDN-Zugriff auf Privat Ressourcen in privaten [Quellen verwendet](use-office-365-cdn-with-spo.md#using-assets-in-private-origins)werden kann, ist die Verwendung von Objekten unter privater Herkunft.</span><span class="sxs-lookup"><span data-stu-id="ee801-186">You can read more about how CDN access to assets in a private origin works in [Using assets in private origins](use-office-365-cdn-with-spo.md#using-assets-in-private-origins).</span></span>

#### <a name="attributes-and-advantages-of-hosting-assets-in-public-origins"></a><span data-ttu-id="ee801-187">Attribute und Vorteile des Hostings von Objekten in öffentlichen Ursprüngen</span><span class="sxs-lookup"><span data-stu-id="ee801-187">Attributes and advantages of hosting assets in public origins</span></span>
  
- <span data-ttu-id="ee801-188">Objekte, die an einem öffentlichen Ursprung verfügbar gemacht werden, sind für jeden Benutzer anonym zugänglich.</span><span class="sxs-lookup"><span data-stu-id="ee801-188">Assets exposed in a public origin are accessible by everyone anonymously.</span></span>
    > [!IMPORTANT]
    > <span data-ttu-id="ee801-189">Sie sollten niemals Ressourcen mit Benutzerinformationen platzieren oder als vertraulich für Ihre Organisation in einem öffentlichen Ursprung gelten.</span><span class="sxs-lookup"><span data-stu-id="ee801-189">You should never place resources that contain user information or are considered sensitive to your organization in a public origin.</span></span>
- <span data-ttu-id="ee801-190">Wenn Sie ein Objekt aus einem öffentlichen Ursprung entfernen, ist es unter Umständen bis zu 30 Tage lang weiterhin über den Cache verfügbar. Links zu dem Objekt im CDN werden jedoch innerhalb von 15 Minuten ungültig.</span><span class="sxs-lookup"><span data-stu-id="ee801-190">If you remove an asset from a public origin, the asset may continue to be available for up to 30 days from the cache; however, we will invalidate links to the asset in the CDN within 15 minutes.</span></span>
- <span data-ttu-id="ee801-191">Wenn Sie Stylesheets (CSS-Dateien) an einem öffentlichen Ursprung hosten, können Sie im Code relative Pfade und URIs verwenden.</span><span class="sxs-lookup"><span data-stu-id="ee801-191">When you host style sheets (CSS files) in a public origin, you can use relative paths and URIs within the code.</span></span> <span data-ttu-id="ee801-192">Dies bedeutet, dass Sie auf den Speicherort von Hintergrundbildern und anderen Objekten relativ zum Speicherort des Objekts, das sie aufruft, verweisen können.</span><span class="sxs-lookup"><span data-stu-id="ee801-192">This means that you can reference the location of background images and other objects relative to the location of the asset that's calling it.</span></span>
- <span data-ttu-id="ee801-193">Die URL eines öffentlichen Ursprungs kann zwar hartcodiert werden, dies wird jedoch nicht empfohlen.</span><span class="sxs-lookup"><span data-stu-id="ee801-193">While you can hard code a public origin's URL, doing so is not recommended.</span></span> <span data-ttu-id="ee801-194">Der Grund hierfür ist folgender: Wenn der Zugriff auf das CDN nicht mehr verfügbar ist, wird die URL nicht automatisch auf Ihre Organisation in SharePoint Online aufgelöst, was zu fehlerhaften Links und anderen Fehlern führen kann.</span><span class="sxs-lookup"><span data-stu-id="ee801-194">The reason for this is that if access to the CDN becomes unavailable, the URL will not automatically resolve to your organization in SharePoint Online and might result in broken links and other errors.</span></span>
- <span data-ttu-id="ee801-195">Die standardmäßigen Dateitypen, die für öffentliche Ursprünge eingeschlossen werden, sind CSS, EOT, GIF, ICO, JPEG, JPG, JS, MAP, PNG, SVG, TTF und WOFF.</span><span class="sxs-lookup"><span data-stu-id="ee801-195">The default file types that are included for public origins are .css, .eot, .gif, .ico, .jpeg, .jpg, .js, .map, .png, .svg, .ttf, and .woff.</span></span> <span data-ttu-id="ee801-196">Sie können zusätzliche Dateitypen angeben.</span><span class="sxs-lookup"><span data-stu-id="ee801-196">You can specify additional file types.</span></span>
- <span data-ttu-id="ee801-197">Sie können eine Richtlinie so konfigurieren, dass von Ihnen angegebene Ressourcen ausgeschlossen werden.</span><span class="sxs-lookup"><span data-stu-id="ee801-197">You can configure a policy to exclude assets that have been identified by site classifications that you specify.</span></span> <span data-ttu-id="ee801-198">Beispielsweise können Sie alle Objekte ausschließen, die als „vertraulich“ oder „eingeschränkt“ gekennzeichnet sind, auch wenn sie einen zulässigen Dateityp haben und sich an einem öffentlichen Ursprung befinden.</span><span class="sxs-lookup"><span data-stu-id="ee801-198">For example, you can choose to exclude all assets that are marked as "confidential" or "restricted" even if they are an allowed file type and are located in a public origin.</span></span>

#### <a name="attributes-and-advantages-of-hosting-assets-in-private-origins"></a><span data-ttu-id="ee801-199">Attribute und Vorteile des Hostings von Objekten in privaten Quellen</span><span class="sxs-lookup"><span data-stu-id="ee801-199">Attributes and advantages of hosting assets in private origins</span></span>

- <span data-ttu-id="ee801-200">Private Origins können nur für SharePoint Online-Objekte verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="ee801-200">Private origins can only be used for SharePoint Online assets.</span></span>
- <span data-ttu-id="ee801-201">Benutzer können nur von einem privaten Ursprung aus auf die Objekte zugreifen, wenn Sie über Berechtigungen für den Zugriff auf den Container verfügen.</span><span class="sxs-lookup"><span data-stu-id="ee801-201">Users can only access the assets from a private origin if they have permissions to access the container.</span></span> <span data-ttu-id="ee801-202">Der anonyme Zugriff auf diese Objekte wird verhindert.</span><span class="sxs-lookup"><span data-stu-id="ee801-202">Anonymous access to these assets is prevented.</span></span>
- <span data-ttu-id="ee801-203">Objekte in privater Herkunft müssen vom SharePoint Online-mandantenbezogen werden.</span><span class="sxs-lookup"><span data-stu-id="ee801-203">Assets in private origins must be referred from the SharePoint Online tenant.</span></span> <span data-ttu-id="ee801-204">Der direkte Zugriff auf private CDN-Ressourcen funktioniert nicht.</span><span class="sxs-lookup"><span data-stu-id="ee801-204">Direct access to private CDN assets does not work.</span></span>
- <span data-ttu-id="ee801-205">Wenn Sie ein Objekt aus dem privaten Ursprung entfernen, kann das Objekt weiterhin bis zu einer Stunde aus dem Cache verfügbar sein; Wir werden jedoch innerhalb von 15 Minuten nach dem Entfernen der Ressource Links zu dem Asset im CDN ungültig machen.</span><span class="sxs-lookup"><span data-stu-id="ee801-205">If you remove an asset from the private origin, the asset may continue to be available for up to an hour from the cache; however, we will invalidate links to the asset in the CDN within 15 minutes of the asset's removal.</span></span>
- <span data-ttu-id="ee801-206">Die standardmäßigen Dateitypen, die für private Ursprünge eingeschlossen werden, sind GIF, ICO, JPEG, JPG, JS und PNG.</span><span class="sxs-lookup"><span data-stu-id="ee801-206">The default file types that are included for private origins are .gif, .ico, .jpeg, .jpg, .js, and .png.</span></span> <span data-ttu-id="ee801-207">Sie können zusätzliche Dateitypen angeben.</span><span class="sxs-lookup"><span data-stu-id="ee801-207">You can specify additional file types.</span></span>
- <span data-ttu-id="ee801-208">Genau wie bei öffentlichen Ursprüngen können Sie eine Richtlinie so konfigurieren, dass Objekte ausgeschlossen werden, die durch von Ihnen angegebene Website Klassifikationen identifiziert wurden, auch wenn Sie Platzhalter verwenden, um alle Objekte in einen Ordner oder eine Dokumentbibliothek einzuschließen.</span><span class="sxs-lookup"><span data-stu-id="ee801-208">Just like with public origins, you can configure a policy to exclude assets that have been identified by site classifications that you specify even if you use wildcards to include all assets within a folder or document library.</span></span>

<span data-ttu-id="ee801-209">Weitere Informationen zur Verwendung der Office 365 CDN, der allgemeinen CDN-Konzepte und anderer Microsoft-CDNs, die Sie mit Ihrem Office 365-Mandanten verwenden können, finden Sie unter [Content Delivery Networks](content-delivery-networks.md).</span><span class="sxs-lookup"><span data-stu-id="ee801-209">For more information about why to use the Office 365 CDN, general CDN concepts, and other Microsoft CDNs you can use with your Office 365 tenant, see [Content Delivery Networks](content-delivery-networks.md).</span></span>

### <a name="default-cdn-origins"></a><span data-ttu-id="ee801-210">Standardmäßige CDN-Ursprünge</span><span class="sxs-lookup"><span data-stu-id="ee801-210">Default CDN origins</span></span>

<span data-ttu-id="ee801-211">Sofern Sie nichts anderes angeben, richtet Office 365 einige Standard Ursprünge ein, wenn Sie das Office 365 CDN aktivieren.</span><span class="sxs-lookup"><span data-stu-id="ee801-211">Unless you specify otherwise, Office 365 sets up some default origins for you when you enable the Office 365 CDN.</span></span> <span data-ttu-id="ee801-212">Wenn Sie sich zunächst dafür entscheiden, Sie nicht zuzustellen, können Sie diese Ursprünge nach Abschluss des Setups hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="ee801-212">If you initially opt not to provision them, you can add these origins after you complete setup.</span></span> <span data-ttu-id="ee801-213">Wenn Sie die Konsequenzen des Überspringens der Einrichtung von Standard Ursprüngen nicht verstehen und einen bestimmten Grund dafür haben, sollten Sie diese erstellen lassen, wenn Sie das CDN aktivieren.</span><span class="sxs-lookup"><span data-stu-id="ee801-213">Unless you understand the consequences of skipping the setup of default origins and have a specific reason for doing so, you should allow them to be created when you enable the CDN.</span></span>
  
<span data-ttu-id="ee801-214">Standardmäßige private CDN-Ursprünge:</span><span class="sxs-lookup"><span data-stu-id="ee801-214">Default private CDN origins:</span></span>
  
- <span data-ttu-id="ee801-215">\*/userphoto.aspx</span><span class="sxs-lookup"><span data-stu-id="ee801-215">\*/userphoto.aspx</span></span>
- <span data-ttu-id="ee801-216">\*/SiteAssets</span><span class="sxs-lookup"><span data-stu-id="ee801-216">\*/siteassets</span></span>

<span data-ttu-id="ee801-217">Standardmäßige öffentliche CDN-Ursprünge:</span><span class="sxs-lookup"><span data-stu-id="ee801-217">Default public CDN origins:</span></span>
  
- <span data-ttu-id="ee801-218">\*/MasterPage</span><span class="sxs-lookup"><span data-stu-id="ee801-218">\*/masterpage</span></span>
- <span data-ttu-id="ee801-219">\*/Style-Bibliothek</span><span class="sxs-lookup"><span data-stu-id="ee801-219">\*/style library</span></span>
- <span data-ttu-id="ee801-220">\*/clientsideassets</span><span class="sxs-lookup"><span data-stu-id="ee801-220">\*/clientsideassets</span></span>

> [!NOTE]
> <span data-ttu-id="ee801-221">_clientsideassets_ ist ein Standard öffentlicher Ursprung, der im Dezember 2017 dem Office 365 CDN-Dienst hinzugefügt wurde.</span><span class="sxs-lookup"><span data-stu-id="ee801-221">_clientsideassets_ is a default public origin that was added to the Office 365 CDN service in December 2017.</span></span> <span data-ttu-id="ee801-222">Dieser Ursprung muss vorhanden sein, damit SharePoint-Framework-Lösungen im CDN funktionieren.</span><span class="sxs-lookup"><span data-stu-id="ee801-222">This origin must be present in order for SharePoint Framework solutions in the CDN to work.</span></span> <span data-ttu-id="ee801-223">Wenn Sie das Office 365 CDN vor dem Dezember 2017 aktiviert haben oder wenn Sie die Einrichtung der Standard Ursprünge beim Aktivieren des CDN übersprungen haben, können Sie diesen Ursprung manuell hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="ee801-223">If you enabled the Office 365 CDN prior to December 2017, or if you skipped setup of default origins when you enabled the CDN, you can manually add this origin.</span></span> <span data-ttu-id="ee801-224">Weitere Informationen finden Sie unter [mein clientseitiges Webpart oder SharePoint Framework-Lösung funktioniert nicht](use-office-365-cdn-with-spo.md#my-client-side-web-part-or-sharepoint-framework-solution-isnt-working).</span><span class="sxs-lookup"><span data-stu-id="ee801-224">For more information, see [My client-side web part or SharePoint Framework solution isn't working](use-office-365-cdn-with-spo.md#my-client-side-web-part-or-sharepoint-framework-solution-isnt-working).</span></span>

## <a name="set-up-and-configure-the-office-365-cdn-by-using-the-sharepoint-online-management-shell"></a><span data-ttu-id="ee801-225">Einrichten und Konfigurieren des Office 365 CDN mithilfe der SharePoint Online-Verwaltungsshell</span><span class="sxs-lookup"><span data-stu-id="ee801-225">Set up and configure the Office 365 CDN by using the SharePoint Online Management Shell</span></span>
<a name="CDNSetupinPShell"> </a>

<span data-ttu-id="ee801-226">In den Verfahren in diesem Abschnitt müssen Sie die SharePoint Online-Verwaltungsshell verwenden, um eine Verbindung mit SharePoint Online herzustellen.</span><span class="sxs-lookup"><span data-stu-id="ee801-226">The procedures in this section require you to use the SharePoint Online Management Shell to connect to SharePoint Online.</span></span> <span data-ttu-id="ee801-227">Weitere Anweisungen finden Sie unter [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).</span><span class="sxs-lookup"><span data-stu-id="ee801-227">For instructions, see [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).</span></span>
  
<span data-ttu-id="ee801-228">Führen Sie die folgenden Schritte aus, um das CDN einzurichten und zu konfigurieren, um Ihre Objekte in SharePoint Online mit der SharePoint Online-Verwaltungsshell zu hosten.</span><span class="sxs-lookup"><span data-stu-id="ee801-228">Complete these steps to set up and configure the CDN to host your assets in SharePoint Online using the SharePoint Online Management Shell.</span></span>
  
### <a name="enable-your-organization-to-use-the-office-365-cdn"></a><span data-ttu-id="ee801-229">Aktivieren Ihrer Organisation für die Verwendung des Office 365 CDN</span><span class="sxs-lookup"><span data-stu-id="ee801-229">Enable your organization to use the Office 365 CDN</span></span>

<span data-ttu-id="ee801-230">Bevor Sie Änderungen an den Mandanten CDN-Einstellungen vornehmen, sollten Sie den aktuellen Status der privaten CDN-Konfiguration in Ihrem Office 365-Mandanten abrufen.</span><span class="sxs-lookup"><span data-stu-id="ee801-230">Before you make changes to the tenant CDN settings, you should retrieve the current status of the private CDN configuration in your Office 365 tenant.</span></span> <span data-ttu-id="ee801-231">Stellen Sie mithilfe der SharePoint Online-Verwaltungsshell eine Verbindung zu Ihrem Mandanten her:</span><span class="sxs-lookup"><span data-stu-id="ee801-231">Connect to your tenant using the SharePoint Online Management Shell:</span></span>

``` powershell
Connect-SPOService -Url https://contoso-admin.sharepoint.com
```

<span data-ttu-id="ee801-232">Verwenden Sie jetzt das Cmdlet **Get-SPOTenantCdnEnabled** , um die CDN-Statuseinstellungen vom Mandanten abzurufen:</span><span class="sxs-lookup"><span data-stu-id="ee801-232">Now use the **Get-SPOTenantCdnEnabled** cmdlet to retrieve the CDN status settings from the tenant:</span></span>

``` powershell
Get-SPOTenantCdnEnabled -CdnType <Public | Private>
```

<span data-ttu-id="ee801-233">Der Status des CDN für die angegebene CdnType wird auf dem Bildschirm ausgegeben.</span><span class="sxs-lookup"><span data-stu-id="ee801-233">The status of the CDN for the specified CdnType will output to the screen.</span></span>

<span data-ttu-id="ee801-234">Verwenden Sie das Cmdlet **Set-SPOTenantCdnEnabled** , um Ihrer Organisation das Office 365 CDN zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="ee801-234">Use the **Set-SPOTenantCdnEnabled** cmdlet to enable your organization to use the Office 365 CDN.</span></span> <span data-ttu-id="ee801-235">Sie können es Ihrer Organisation ermöglichen, öffentliche Ursprünge, private Ursprünge oder beides gleichzeitig zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="ee801-235">You can enable your organization to use public origins, private origins, or both at once.</span></span> <span data-ttu-id="ee801-236">Sie können das CDN auch so konfigurieren, dass die Einrichtung der Standard Ursprünge übersprungen wird, wenn Sie es aktivieren.</span><span class="sxs-lookup"><span data-stu-id="ee801-236">You can also configure the CDN to skip the setup of default origins when you enable it.</span></span> <span data-ttu-id="ee801-237">Sie können diese Ursprünge immer später hinzufügen, wie in diesem Thema beschrieben.</span><span class="sxs-lookup"><span data-stu-id="ee801-237">You can always add these origins later as described in this topic.</span></span>
  
<span data-ttu-id="ee801-238">In Windows PowerShell für SharePoint Online:</span><span class="sxs-lookup"><span data-stu-id="ee801-238">In Windows Powershell for SharePoint Online:</span></span>

``` powershell
Set-SPOTenantCdnEnabled -CdnType <Public | Private | Both> -Enable $true
```

<span data-ttu-id="ee801-239">Geben Sie beispielsweise den folgenden Befehl ein, um Ihrer Organisation die Verwendung von öffentlichen und privaten Ursprüngen zu ermöglichen:</span><span class="sxs-lookup"><span data-stu-id="ee801-239">For example, to enable your organization to use both public and private origins, type the following command:</span></span>

``` powershell
Set-SPOTenantCdnEnabled -CdnType Both -Enable $true
```

<span data-ttu-id="ee801-240">Geben Sie den folgenden Befehl ein, um zu ermöglichen, dass Ihre Organisation sowohl öffentliche als auch private Ursprünge verwendet, aber die Standard Ursprünge nicht festlegt:</span><span class="sxs-lookup"><span data-stu-id="ee801-240">To enable your organization to use both public and private origins but skip setting up the default origins, type the following command:</span></span>

``` powershell
Set-SPOTenantCdnEnabled -CdnType Both -Enable $true -NoDefaultOrigins
```

<span data-ttu-id="ee801-241">Informationen zu den Ursprüngen, die bei der Aktivierung des Office 365 CDN standardmäßig bereitgestellt werden, und die potenziellen Auswirkungen des Überspringens der Einrichtung von Standard Ursprüngen finden Sie unter [default CDN Origins](use-office-365-cdn-with-spo.md#default-cdn-origins) .</span><span class="sxs-lookup"><span data-stu-id="ee801-241">See [Default CDN origins](use-office-365-cdn-with-spo.md#default-cdn-origins) for information about the origins that are provisioned by default when you enable the Office 365 CDN, and the potential impact of skipping the setup of default origins.</span></span>

<span data-ttu-id="ee801-242">Geben Sie den folgenden Befehl ein, um Ihrer Organisation die Verwendung öffentlicher Ursprünge zu ermöglichen:</span><span class="sxs-lookup"><span data-stu-id="ee801-242">To enable your organization to use public origins, type the following command:</span></span>

``` powershell
Set-SPOTenantCdnEnabled -CdnType Public -Enable $true
```

<span data-ttu-id="ee801-243">Geben Sie den folgenden Befehl ein, um Ihrer Organisation die Verwendung privater Ursprünge zu ermöglichen:</span><span class="sxs-lookup"><span data-stu-id="ee801-243">To enable your organization to use private origins, type the following command:</span></span>

``` powershell
Set-SPOTenantCdnEnabled -CdnType Private -Enable $true
```

<span data-ttu-id="ee801-244">Weitere Informationen zu diesem Cmdlet finden Sie unter [Set-SPOTenantCdnEnabled](https://technet.microsoft.com/en-us/library/mt790765.aspx).</span><span class="sxs-lookup"><span data-stu-id="ee801-244">For more information about this cmdlet, see [Set-SPOTenantCdnEnabled](https://technet.microsoft.com/en-us/library/mt790765.aspx).</span></span>
  
### <a name="change-the-list-of-file-types-to-include-in-the-office-365-cdn-optional"></a><span data-ttu-id="ee801-245">Ändern der Liste der Dateitypen, die in Office 365 CDN eingeschlossen werden sollen (optional)</span><span class="sxs-lookup"><span data-stu-id="ee801-245">Change the list of file types to include in the Office 365 CDN (Optional)</span></span>
<a name="Office365CDNforSPOFileType"> </a>

> [!TIP]
> <span data-ttu-id="ee801-246">Wenn Sie Dateitypen mithilfe des Cmdlets **Set-SPOTenantCdnPolicy** definieren, überschreiben Sie die aktuell definierte Liste.</span><span class="sxs-lookup"><span data-stu-id="ee801-246">When you define file types by using the **Set-SPOTenantCdnPolicy** cmdlet, you overwrite the currently defined list.</span></span> <span data-ttu-id="ee801-247">Wenn Sie der Liste weitere Dateitypen hinzufügen möchten, verwenden Sie zuerst das Cmdlet, um herauszufinden, welche Dateitypen bereits zulässig sind, und fügen Sie diese in die Liste zusammen mit ihren neuen ein.</span><span class="sxs-lookup"><span data-stu-id="ee801-247">If you want to add additional file types to the list, use the cmdlet first to find out what file types are already allowed and include them in the list along with your new ones.</span></span>
  
<span data-ttu-id="ee801-248">Verwenden Sie das Cmdlet **Set-SPOTenantCdnPolicy** , um statische Dateitypen zu definieren, die von öffentlichen und privaten Ursprüngen im CDN gehostet werden können.</span><span class="sxs-lookup"><span data-stu-id="ee801-248">Use the **Set-SPOTenantCdnPolicy** cmdlet to define static file types that can be hosted by public and private origins in the CDN.</span></span> <span data-ttu-id="ee801-249">Standardmäßig sind allgemeine Objekttypen zulässig, beispielsweise CSS, GIF, JPG und JS.</span><span class="sxs-lookup"><span data-stu-id="ee801-249">By default, common asset types are allowed, for example .css, .gif, .jpg, and .js.</span></span>

<span data-ttu-id="ee801-250">In Windows PowerShell für SharePoint Online:</span><span class="sxs-lookup"><span data-stu-id="ee801-250">In Windows PowerShell for SharePoint Online:</span></span>

``` powershell
Set-SPOTenantCdnPolicy -CdnType <Public | Private> -PolicyType IncludeFileExtensions -PolicyValue "<Comma-separated list of file types >"
```

<span data-ttu-id="ee801-251">Um dem CDN beispielsweise das Hosten von CSS-und PNG-Dateien zu ermöglichen, geben Sie den folgenden Befehl ein:</span><span class="sxs-lookup"><span data-stu-id="ee801-251">For example, to enable the CDN to host .css and .png files, you would enter the command:</span></span>

``` powershell
Set-SPOTenantCdnPolicy -CdnType Private -PolicyType IncludeFileExtensions -PolicyValue "CSS,PNG"
```

<span data-ttu-id="ee801-252">Verwenden Sie das Cmdlet **Get-SPOTenantCdnPolicies** , um zu sehen, welche Dateitypen derzeit im CDN zulässig sind:</span><span class="sxs-lookup"><span data-stu-id="ee801-252">To see what file types are currently allowed by the CDN, use the **Get-SPOTenantCdnPolicies** cmdlet:</span></span>

``` powershell
Get-SPOTenantCdnPolicies -CdnType <Public | Private>
```

<span data-ttu-id="ee801-253">Weitere Informationen zu diesen Cmdlets finden Sie unter [Set-SPOTenantCdnPolicy](https://technet.microsoft.com/en-us/library/mt800839.aspx) und [Get-SPOTenantCdnPolicies](https://technet.microsoft.com/en-us/library/mt800838.aspx).</span><span class="sxs-lookup"><span data-stu-id="ee801-253">For more information about these cmdlets, see [Set-SPOTenantCdnPolicy](https://technet.microsoft.com/en-us/library/mt800839.aspx) and [Get-SPOTenantCdnPolicies](https://technet.microsoft.com/en-us/library/mt800838.aspx).</span></span>
  
### <a name="change-the-list-of-site-classifications-you-want-to-exclude-from-the-office-365-cdn-optional"></a><span data-ttu-id="ee801-254">Ändern der Liste der Website Klassifikationen, die Sie aus dem Office 365 CDN ausschließen möchten (optional)</span><span class="sxs-lookup"><span data-stu-id="ee801-254">Change the list of site classifications you want to exclude from the Office 365 CDN (Optional)</span></span>
<a name="Office365CDNforSPOSiteClassification"> </a>

> [!TIP]
> <span data-ttu-id="ee801-255">Wenn Sie Website Klassifizierungen mithilfe des Cmdlets **Set-SPOTenantCdnPolicy** ausschließen, überschreiben Sie die aktuell definierte Liste.</span><span class="sxs-lookup"><span data-stu-id="ee801-255">When you exclude site classifications by using the **Set-SPOTenantCdnPolicy** cmdlet, you overwrite the currently defined list.</span></span> <span data-ttu-id="ee801-256">Wenn Sie zusätzliche Website Klassifizierungen ausschließen möchten, verwenden Sie zuerst das Cmdlet, um herauszufinden, welche Klassifizierungen bereits ausgeschlossen sind, und fügen Sie Sie dann zusammen mit ihren neuen hinzu.</span><span class="sxs-lookup"><span data-stu-id="ee801-256">If you want to exclude additional site classifications, use the cmdlet first to find out what classifications are already excluded and then add them along with your new ones.</span></span>

<span data-ttu-id="ee801-257">Verwenden Sie das Cmdlet **Set-SPOTenantCdnPolicy** -Cmdlet zum Ausschließen von Websiteklassifizierungen, die Sie nicht über das CDN zur Verfügung stellen möchten.</span><span class="sxs-lookup"><span data-stu-id="ee801-257">Use the **Set-SPOTenantCdnPolicy** cmdlet to exclude site classifications that you do not want to make available over the CDN.</span></span> <span data-ttu-id="ee801-258">Standardmäßig sind keine Websiteklassifizierungen ausgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="ee801-258">By default, no site classifications are excluded.</span></span>

<span data-ttu-id="ee801-259">In Windows PowerShell für SharePoint Online:</span><span class="sxs-lookup"><span data-stu-id="ee801-259">In Windows PowerShell for SharePoint Online:</span></span>

``` powershell
Set-SPOTenantCdnPolicy -CdnType <Public | Private> -PolicyType ExcludeRestrictedSiteClassifications  -PolicyValue "<Comma-separated list of site classifications >"
```

<span data-ttu-id="ee801-260">Verwenden Sie das Cmdlet **Get-SPOTenantCdnPolicies** , um zu sehen, welche Website Klassifizierungen derzeit eingeschränkt sind:</span><span class="sxs-lookup"><span data-stu-id="ee801-260">To see what site classifications are currently restricted, use the **Get-SPOTenantCdnPolicies** cmdlet:</span></span>

``` powershell
Get-SPOTenantCdnPolicies -CdnType <Public | Private>
```

<span data-ttu-id="ee801-261">Die zurückgegebenen Eigenschaften sind _IncludeFileExtensions_, _ExcludeRestrictedSiteClassifications_ und _ExcludeIfNoScriptDisabled_.</span><span class="sxs-lookup"><span data-stu-id="ee801-261">The properties that will be returned are _IncludeFileExtensions_, _ExcludeRestrictedSiteClassifications_ and _ExcludeIfNoScriptDisabled_.</span></span>

<span data-ttu-id="ee801-262">Die _IncludeFileExtensions_ -Eigenschaft enthält die Liste der Dateierweiterungen, die aus dem CDN bedient werden.</span><span class="sxs-lookup"><span data-stu-id="ee801-262">The _IncludeFileExtensions_ property contains the list of file extensions that will be served from the CDN.</span></span>

> [!NOTE]
> <span data-ttu-id="ee801-263">Die standardmäßigen Dateierweiterungen unterscheiden sich zwischen öffentlich und privat.</span><span class="sxs-lookup"><span data-stu-id="ee801-263">The default file extensions are different between public and private.</span></span>

<span data-ttu-id="ee801-264">Die _ExcludeRestrictedSiteClassifications_ -Eigenschaft enthält die Website Klassifizierungen, die Sie aus dem CDN ausschließen möchten.</span><span class="sxs-lookup"><span data-stu-id="ee801-264">The _ExcludeRestrictedSiteClassifications_ property contains the site classifications that you want to exclude from the CDN.</span></span> <span data-ttu-id="ee801-265">Sie können beispielsweise als **vertraulich** gekennzeichnete Websites ausschließen, sodass Inhalte von Websites mit dieser Klassifizierung nicht aus dem CDN bedient werden.</span><span class="sxs-lookup"><span data-stu-id="ee801-265">For example, you can exclude sites marked as **Confidential** so content from sites with that classification applied will not be served from the CDN.</span></span>

<span data-ttu-id="ee801-266">Die _ExcludeIfNoScriptDisabled_ -Eigenschaft schließt Inhalte aus dem CDN basierend auf den NoScript- __ Attributeinstellungen auf Websiteebene aus.</span><span class="sxs-lookup"><span data-stu-id="ee801-266">The _ExcludeIfNoScriptDisabled_ property excludes content from the CDN based on the site-level _NoScript_ attribute settings.</span></span> <span data-ttu-id="ee801-267">Standardmäßig ist das _NoScript_ -Attribut für _moderne_ Websites **aktiviert** und für _klassische_ Websites **deaktiviert** .</span><span class="sxs-lookup"><span data-stu-id="ee801-267">By default, the _NoScript_ attribute is set to **Enabled** for _Modern_ sites and **Disabled** for _Classic_ sites.</span></span> <span data-ttu-id="ee801-268">Dies hängt von ihren Mandanten Einstellungen ab.</span><span class="sxs-lookup"><span data-stu-id="ee801-268">This depends on your tenant settings.</span></span>

<span data-ttu-id="ee801-269">Weitere Informationen zu diesen Cmdlets finden Sie unter [Set-SPOTenantCdnPolicy](https://technet.microsoft.com/en-us/library/mt800839.aspx) und [Get-SPOTenantCdnPolicies](https://technet.microsoft.com/en-us/library/mt800838.aspx).</span><span class="sxs-lookup"><span data-stu-id="ee801-269">For more information about these cmdlets, see [Set-SPOTenantCdnPolicy](https://technet.microsoft.com/en-us/library/mt800839.aspx) and [Get-SPOTenantCdnPolicies](https://technet.microsoft.com/en-us/library/mt800838.aspx).</span></span>
  
### <a name="add-an-origin-for-your-assets"></a><span data-ttu-id="ee801-270">Hinzufügen eines Ursprungs für Ihre Objekte</span><span class="sxs-lookup"><span data-stu-id="ee801-270">Add an origin for your assets</span></span>
<a name="Office365CDNforSPOOrigin"> </a>

<span data-ttu-id="ee801-271">Verwenden Sie das Cmdlet **Add-SPOTenantCdnOrigin** , um einen Ursprung zu definieren.</span><span class="sxs-lookup"><span data-stu-id="ee801-271">Use the **Add-SPOTenantCdnOrigin** cmdlet to define an origin.</span></span> <span data-ttu-id="ee801-272">Sie können mehrere Ursprünge definieren.</span><span class="sxs-lookup"><span data-stu-id="ee801-272">You can define multiple origins.</span></span> <span data-ttu-id="ee801-273">Der Ursprung ist eine URL, die auf eine SharePoint-Bibliothek oder einen Ordner mit den Objekten verweist, die vom CDN gehostet werden sollen.</span><span class="sxs-lookup"><span data-stu-id="ee801-273">The origin is a URL that points to a SharePoint library or folder that contains the assets that you want to be hosted by the CDN.</span></span>
  
> [!IMPORTANT]
> <span data-ttu-id="ee801-274">Sie sollten niemals Ressourcen mit Benutzerinformationen platzieren oder als vertraulich für Ihre Organisation in einem öffentlichen Ursprung gelten.</span><span class="sxs-lookup"><span data-stu-id="ee801-274">You should never place resources that contain user information or are considered sensitive to your organization in a public origin.</span></span>

``` powershell
Add-SPOTenantCdnOrigin -CdnType <Public | Private> -OriginUrl <path>
```

<span data-ttu-id="ee801-275">Der Wert von _path_ ist der relative Pfad zu der Bibliothek oder dem Ordner, der die Objekte enthält.</span><span class="sxs-lookup"><span data-stu-id="ee801-275">The value of _path_ is the relative path to the library or folder that contains the assets.</span></span> <span data-ttu-id="ee801-276">Sie können Platzhalter zusätzlich zu relativen Pfaden verwenden.</span><span class="sxs-lookup"><span data-stu-id="ee801-276">You can use wildcards in addition to relative paths.</span></span> <span data-ttu-id="ee801-277">Origins unterstützen Platzhalter, die der URL vorangestellt werden.</span><span class="sxs-lookup"><span data-stu-id="ee801-277">Origins support wildcards prepended to the URL.</span></span> <span data-ttu-id="ee801-278">Auf diese Weise können Sie Ursprünge erstellen, die sich über mehrere Standorte erstrecken.</span><span class="sxs-lookup"><span data-stu-id="ee801-278">This allows you to create origins that span multiple sites.</span></span> <span data-ttu-id="ee801-279">Geben Sie beispielsweise den folgenden Befehl ein, um alle Objekte im Ordner MasterPages für alle Websites als öffentlichen Ursprung innerhalb des CDN einzuschließen:</span><span class="sxs-lookup"><span data-stu-id="ee801-279">For example, to include all of the assets in the masterpages folder for all of your sites as a public origin within the CDN, type the following command:</span></span>

``` powershell
Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
```

- <span data-ttu-id="ee801-280">Der Platzhalter-**/** Modifizierer \* kann nur am Anfang des Pfads verwendet werden und entspricht allen URL-Segmenten unter der angegebenen URL.</span><span class="sxs-lookup"><span data-stu-id="ee801-280">The wildcard modifier \***/** can only be used at the beginning of the path, and will match all URL segments under the specified URL.</span></span>
- <span data-ttu-id="ee801-281">Der Pfad kann auf eine Dokumentbibliothek, einen Ordner oder eine Website verweisen.</span><span class="sxs-lookup"><span data-stu-id="ee801-281">The path can point to a document library, folder or site.</span></span> <span data-ttu-id="ee801-282">Beispielsweise entspricht der Pfad _\*/site1_ allen Dokumentbibliotheken unter der Website.</span><span class="sxs-lookup"><span data-stu-id="ee801-282">For example, the path _\*/site1_ will match all the document libraries under the site.</span></span>

<span data-ttu-id="ee801-283">Sie können einen Ursprung mit einem bestimmten relativen Pfad hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="ee801-283">You can add an origin with a specific relative path.</span></span> <span data-ttu-id="ee801-284">Sie können keinen Ursprung unter Verwendung des vollständigen Pfads hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="ee801-284">You cannot add an origin using the full path.</span></span>

<span data-ttu-id="ee801-285">In diesem Beispiel wird ein privater Ursprung der SiteAssets-Bibliothek auf einer bestimmten Website hinzugefügt:</span><span class="sxs-lookup"><span data-stu-id="ee801-285">This example adds a private origin of the siteassets library on a specific site:</span></span>

``` powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl sites/site1/siteassets
```

<span data-ttu-id="ee801-286">In diesem Beispiel wird ein privater Ursprung des Ordners _Folder1_ in der Bibliothek Website Objekte der Websitesammlung hinzugefügt:</span><span class="sxs-lookup"><span data-stu-id="ee801-286">This example adds a private origin of the _folder1_ folder in the site collection's site assets library:</span></span>

``` powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl “/sites/test/siteassets/folder1”
```

<span data-ttu-id="ee801-287">Weitere Informationen zu diesem Befehl und seiner Syntax finden Sie unter [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).</span><span class="sxs-lookup"><span data-stu-id="ee801-287">For more information about this command and its syntax, see [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).</span></span>

> [!NOTE]
> <span data-ttu-id="ee801-288">In privaten Quellen muss für die von einem Ursprung freigegebenen Objekte eine Hauptversion veröffentlicht werden, bevor auf Sie über das CDN zugegriffen werden kann.</span><span class="sxs-lookup"><span data-stu-id="ee801-288">In private origins, assets being shared from an origin must have a major version published before they can be accessed from the CDN.</span></span>
  
<span data-ttu-id="ee801-289">Nachdem Sie den Befehl ausgeführt haben, wird die Konfiguration im Datencenter vom System synchronisiert.</span><span class="sxs-lookup"><span data-stu-id="ee801-289">Once you've run the command, the system synchronizes the configuration across the datacenter.</span></span> <span data-ttu-id="ee801-290">Dies kann bis zu 15 Minuten dauern.</span><span class="sxs-lookup"><span data-stu-id="ee801-290">This can take up to 15 minutes.</span></span>
  
### <a name="example-configure-a-public-origin-for-your-master-pages-and-for-your-style-library-for-sharepoint-online"></a><span data-ttu-id="ee801-291">Beispiel: Konfigurieren eines öffentlichen Ursprungs für Ihre Gestaltungsvorlagen und für Ihre Stilbibliothek für SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="ee801-291">Example: Configure a public origin for your master pages and for your style library for SharePoint Online</span></span>
<a name="ExamplePublicOrigin"> </a>

<span data-ttu-id="ee801-292">NormalerWeise werden diese Ursprünge standardmäßig für Sie eingerichtet, wenn Sie das Office 365 CDN aktivieren.</span><span class="sxs-lookup"><span data-stu-id="ee801-292">Normally, these origins are set up for you by default when you enable the Office 365 CDN.</span></span> <span data-ttu-id="ee801-293">Wenn Sie Sie jedoch manuell aktivieren möchten, führen Sie die folgenden Schritte aus.</span><span class="sxs-lookup"><span data-stu-id="ee801-293">However, if you want to enable them manually, follow these steps.</span></span>
  
- <span data-ttu-id="ee801-294">Verwenden Sie das Cmdlet **Add-SPOTenantCdnOrigin** , um die Formatbibliothek als öffentlichen Ursprung zu definieren.</span><span class="sxs-lookup"><span data-stu-id="ee801-294">Use the **Add-SPOTenantCdnOrigin** cmdlet to define the style library as a public origin.</span></span>

``` powershell
  Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */style%20library
  ```

- <span data-ttu-id="ee801-295">Verwenden Sie das Cmdlet **Add-SPOTenantCdnOrigin** , um die Gestaltungsvorlagen als öffentlichen Ursprung zu definieren.</span><span class="sxs-lookup"><span data-stu-id="ee801-295">Use the **Add-SPOTenantCdnOrigin** cmdlet to define the master pages as a public origin.</span></span>

``` powershell
  Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
  ```

<span data-ttu-id="ee801-296">Weitere Informationen zu diesem Befehl und seiner Syntax finden Sie unter [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).</span><span class="sxs-lookup"><span data-stu-id="ee801-296">For more information about this command and its syntax, see [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).</span></span>

<span data-ttu-id="ee801-297">Nachdem Sie den Befehl ausgeführt haben, wird die Konfiguration im Datencenter vom System synchronisiert.</span><span class="sxs-lookup"><span data-stu-id="ee801-297">Once you've run the command, the system synchronizes the configuration across the datacenter.</span></span> <span data-ttu-id="ee801-298">Dies kann bis zu 15 Minuten dauern.</span><span class="sxs-lookup"><span data-stu-id="ee801-298">This can take up to 15 minutes.</span></span>

### <a name="example-configure-a-private-origin-for-your-site-assets-site-pages-and-publishing-images-for-sharepoint-online"></a><span data-ttu-id="ee801-299">Beispiel: Konfigurieren eines privaten Ursprungs für Ihre Website Objekte, Website Seiten und Veröffentlichen von Bildern für SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="ee801-299">Example: Configure a private origin for your site assets, site pages, and publishing images for SharePoint Online</span></span>
<a name="ExamplePrivateOrigin"> </a>

- <span data-ttu-id="ee801-300">Verwenden Sie das Cmdlet **Add-SPOTenantCdnOrigin** , um den Ordnerstandort Objekte als privaten Ursprung zu definieren.</span><span class="sxs-lookup"><span data-stu-id="ee801-300">Use the **Add-SPOTenantCdnOrigin** cmdlet to define the site assets folder as a private origin.</span></span>

``` powershell
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */siteassets
  ```

- <span data-ttu-id="ee801-301">Verwenden Sie das Cmdlet **Add-SPOTenantCdnOrigin** , um den Ordner Website Seiten als privaten Ursprung zu definieren.</span><span class="sxs-lookup"><span data-stu-id="ee801-301">Use the **Add-SPOTenantCdnOrigin** cmdlet to define the site pages folder as a private origin.</span></span>

``` powershell
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */sitepages
  ```

- <span data-ttu-id="ee801-302">Verwenden Sie das Cmdlet **Add-SPOTenantCdnOrigin** , um den Ordner Veröffentlichungs Bilder als privaten Ursprung zu definieren.</span><span class="sxs-lookup"><span data-stu-id="ee801-302">Use the **Add-SPOTenantCdnOrigin** cmdlet to define the publishing images folder as a private origin.</span></span>

``` powershell
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */publishingimages
  ```

<span data-ttu-id="ee801-303">Weitere Informationen zu diesem Befehl und seiner Syntax finden Sie unter [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).</span><span class="sxs-lookup"><span data-stu-id="ee801-303">For more information about this command and its syntax, see [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).</span></span>

<span data-ttu-id="ee801-304">Nachdem Sie den Befehl ausgeführt haben, wird die Konfiguration im Datencenter vom System synchronisiert.</span><span class="sxs-lookup"><span data-stu-id="ee801-304">Once you've run the command, the system synchronizes the configuration across the datacenter.</span></span> <span data-ttu-id="ee801-305">Dies kann bis zu 15 Minuten dauern.</span><span class="sxs-lookup"><span data-stu-id="ee801-305">This can take up to 15 minutes.</span></span>

### <a name="example-configure-a-private-origin-for-a-site-collection-for-sharepoint-online"></a><span data-ttu-id="ee801-306">Beispiel: Konfigurieren eines privaten Ursprungs für eine Websitesammlung für SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="ee801-306">Example: Configure a private origin for a site collection for SharePoint Online</span></span>
<a name="ExamplePrivateOriginSiteCollection"> </a>

<span data-ttu-id="ee801-307">Verwenden Sie das Cmdlet **Add-SPOTenantCdnOrigin** , um eine Websitesammlung als privaten Ursprung zu definieren.</span><span class="sxs-lookup"><span data-stu-id="ee801-307">Use the **Add-SPOTenantCdnOrigin** cmdlet to define a site collection as a private origin.</span></span> <span data-ttu-id="ee801-308">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="ee801-308">For example:</span></span>

``` powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl sites/site1/siteassets
```

<span data-ttu-id="ee801-309">Weitere Informationen zu diesem Befehl und seiner Syntax finden Sie unter [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).</span><span class="sxs-lookup"><span data-stu-id="ee801-309">For more information about this command and its syntax, see [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).</span></span>
  
<span data-ttu-id="ee801-310">Nachdem Sie den Befehl ausgeführt haben, wird die Konfiguration im Datencenter vom System synchronisiert.</span><span class="sxs-lookup"><span data-stu-id="ee801-310">Once you've run the command, the system synchronizes the configuration across the datacenter.</span></span> <span data-ttu-id="ee801-311">Möglicherweise wird eine Meldung zur _Konfiguration_ ausstehend angezeigt, die erwartet wird, wenn der SharePoint Online-Mandant eine Verbindung mit dem CDN-Dienst herstellt.</span><span class="sxs-lookup"><span data-stu-id="ee801-311">You may see a _Configuration pending_ message which is expected as the SharePoint Online tenant connects to the CDN service.</span></span> <span data-ttu-id="ee801-312">Dies kann bis zu 15 Minuten dauern.</span><span class="sxs-lookup"><span data-stu-id="ee801-312">This can take up to 15 minutes.</span></span>

### <a name="manage-the-office-365-cdn"></a><span data-ttu-id="ee801-313">Verwalten des Office 365 CDN</span><span class="sxs-lookup"><span data-stu-id="ee801-313">Manage the Office 365 CDN</span></span>
<a name="CDNManage"> </a>

<span data-ttu-id="ee801-314">Nachdem Sie das CDN eingerichtet haben, können Sie Änderungen an Ihrer Konfiguration vornehmen, wenn Sie Inhalte aktualisieren oder Ihre Anforderungen ändern, wie in diesem Abschnitt beschrieben.</span><span class="sxs-lookup"><span data-stu-id="ee801-314">Once you've set up the CDN, you can make changes to your configuration as you update content or as your needs change, as described in this section.</span></span>
  
#### <a name="add-update-or-remove-assets-from-the-office-365-cdn"></a><span data-ttu-id="ee801-315">Hinzufügen, aktualisieren oder Entfernen von Objekten aus dem Office 365 CDN</span><span class="sxs-lookup"><span data-stu-id="ee801-315">Add, update, or remove assets from the Office 365 CDN</span></span>
<a name="Office365CDNforSPOaddremoveasset"> </a>

<span data-ttu-id="ee801-316">Nachdem Sie die Setupschritte ausgeführt haben, können Sie neue Ressourcen hinzufügen und vorhandene Objekte aktualisieren oder entfernen, wann immer Sie möchten.</span><span class="sxs-lookup"><span data-stu-id="ee801-316">Once you've completed the setup steps, you can add new assets, and update or remove existing assets whenever you want.</span></span> <span data-ttu-id="ee801-317">Nehmen Sie die Änderungen an den Objekten im Ordner oder in der SharePoint-Bibliothek vor, die Sie als Ursprung identifiziert haben.</span><span class="sxs-lookup"><span data-stu-id="ee801-317">Just make your changes to the assets in the folder or SharePoint library that you identified as an origin.</span></span> <span data-ttu-id="ee801-318">Wenn Sie ein neues Objekt hinzufügen, ist es sofort über das CDN verfügbar.</span><span class="sxs-lookup"><span data-stu-id="ee801-318">If you add a new asset, it is available through the CDN immediately.</span></span> <span data-ttu-id="ee801-319">Wenn Sie jedoch das Objekt aktualisieren, dauert es bis zu 15 Minuten, bis die neue Kopie weitergegeben wird und im CDN verfügbar wird.</span><span class="sxs-lookup"><span data-stu-id="ee801-319">However, if you update the asset, it will take up to 15 minutes for the new copy to propagate and become available in the CDN.</span></span>
  
<span data-ttu-id="ee801-320">Wenn Sie den Speicherort des Ursprungs abrufen müssen, können Sie das Cmdlet **Get-spotenantcdnorigins ausführen** verwenden.</span><span class="sxs-lookup"><span data-stu-id="ee801-320">If you need to retrieve the location of the origin, you can use the **Get-SPOTenantCdnOrigins** cmdlet.</span></span> <span data-ttu-id="ee801-321">Informationen zur Verwendung dieses Cmdlets finden Sie unter [Get-spotenantcdnorigins ausführen](https://technet.microsoft.com/en-us/library/mt790770.aspx).</span><span class="sxs-lookup"><span data-stu-id="ee801-321">For information on how to use this cmdlet, see [Get-SPOTenantCdnOrigins](https://technet.microsoft.com/en-us/library/mt790770.aspx).</span></span>
  
#### <a name="remove-an-origin-from-the-office-365-cdn"></a><span data-ttu-id="ee801-322">Entfernen eines Ursprungs aus dem Office 365 CDN</span><span class="sxs-lookup"><span data-stu-id="ee801-322">Remove an origin from the Office 365 CDN</span></span>
<a name="Office365CDNforSPORemoveOrigin"> </a>

<span data-ttu-id="ee801-323">Sie können den Zugriff auf einen Ordner oder eine SharePoint-Bibliothek entfernen, die Sie als Ursprung identifiziert haben.</span><span class="sxs-lookup"><span data-stu-id="ee801-323">You can remove access to a folder or SharePoint library that you identified as an origin.</span></span> <span data-ttu-id="ee801-324">Verwenden Sie hierzu das Cmdlet **Remove-SPOTenantCdnOrigin** .</span><span class="sxs-lookup"><span data-stu-id="ee801-324">To do this, use the **Remove-SPOTenantCdnOrigin** cmdlet.</span></span>

``` powershell
Remove-SPOTenantCdnOrigin -OriginUrl <path> -CdnType <Public | Private | Both>
```

<span data-ttu-id="ee801-325">Informationen zur Verwendung dieses Cmdlets finden Sie unter [Remove-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790761.aspx).</span><span class="sxs-lookup"><span data-stu-id="ee801-325">For information on how to use this cmdlet, see [Remove-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790761.aspx).</span></span>
  
#### <a name="modify-an-origin-in-the-office-365-cdn"></a><span data-ttu-id="ee801-326">Ändern eines Ursprungs im Office 365 CDN</span><span class="sxs-lookup"><span data-stu-id="ee801-326">Modify an origin in the Office 365 CDN</span></span>
<a name="Office365CDNforSPORemoveOrigin"> </a>

<span data-ttu-id="ee801-327">Sie können einen Ursprung, den Sie erstellt haben, nicht ändern.</span><span class="sxs-lookup"><span data-stu-id="ee801-327">You cannot modify an origin you've created.</span></span> <span data-ttu-id="ee801-328">Entfernen Sie stattdessen den Ursprung, und fügen Sie dann einen neuen hinzu.</span><span class="sxs-lookup"><span data-stu-id="ee801-328">Instead, remove the origin and then add a new one.</span></span> <span data-ttu-id="ee801-329">Weitere Informationen finden Sie unter [So entfernen Sie einen Ursprung aus dem Office 365 CDN](use-office-365-cdn-with-spo.md#Office365CDNforSPORemoveOrigin) und [fügen einen Ursprung für Ihre Objekte hinzu](use-office-365-cdn-with-spo.md#Office365CDNforSPOOrigin).</span><span class="sxs-lookup"><span data-stu-id="ee801-329">For more information, see [To remove an origin from the Office 365 CDN](use-office-365-cdn-with-spo.md#Office365CDNforSPORemoveOrigin) and [To add an origin for your assets](use-office-365-cdn-with-spo.md#Office365CDNforSPOOrigin).</span></span>
  
#### <a name="disable-the-office-365-cdn"></a><span data-ttu-id="ee801-330">Deaktivieren von Office 365 CDN</span><span class="sxs-lookup"><span data-stu-id="ee801-330">Disable the Office 365 CDN</span></span>
<a name="Office365CDNforSPODisable"> </a>

<span data-ttu-id="ee801-331">Verwenden Sie das Cmdlet **Set-SPOTenantCdnEnabled** , um das CDN für Ihre Organisation zu deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="ee801-331">Use the **Set-SPOTenantCdnEnabled** cmdlet to disable the CDN for your organization.</span></span> <span data-ttu-id="ee801-332">Wenn sowohl der öffentliche als auch der private Ursprung für das CDN aktiviert ist, müssen Sie das Cmdlet doppelt ausführen, wie in den folgenden Beispielen gezeigt.</span><span class="sxs-lookup"><span data-stu-id="ee801-332">If you have both the public and private origins enabled for the CDN, you need to run the cmdlet twice as shown in the following examples.</span></span>
  
<span data-ttu-id="ee801-333">Um die Verwendung öffentlicher Ursprünge im CDN zu deaktivieren, geben Sie den folgenden Befehl ein:</span><span class="sxs-lookup"><span data-stu-id="ee801-333">To disable use of public origins in the CDN, enter the following command:</span></span>

``` powershell
Set-SPOTenantCdnEnabled -CdnType Public -Enable $false
```

<span data-ttu-id="ee801-334">Um die Verwendung privater Ursprünge im CDN zu deaktivieren, geben Sie den folgenden Befehl ein:</span><span class="sxs-lookup"><span data-stu-id="ee801-334">To disable use of the private origins in the CDN, enter the following command:</span></span>

``` powershell
Set-SPOTenantCdnEnabled -CdnType Private -Enable $false
```

<span data-ttu-id="ee801-335">Weitere Informationen zu diesem Cmdlet finden Sie unter [Set-SPOTenantCdnEnabled](https://technet.microsoft.com/en-us/library/mt790765.aspx).</span><span class="sxs-lookup"><span data-stu-id="ee801-335">For more information about this cmdlet, see [Set-SPOTenantCdnEnabled](https://technet.microsoft.com/en-us/library/mt790765.aspx).</span></span>

## <a name="set-up-and-configure-the-office-365-cdn-using-the-office-365-cli"></a><span data-ttu-id="ee801-336">Einrichten und Konfigurieren des Office 365 CDN mithilfe von Office 365 CLI</span><span class="sxs-lookup"><span data-stu-id="ee801-336">Set up and configure the Office 365 CDN using the Office 365 CLI</span></span>
<a name="CDNSetupinCLI"> </a>

<span data-ttu-id="ee801-337">Die Verfahren in diesem Abschnitt erfordern, dass Sie die [Office 365 CLI](https://aka.ms/o365cli)installiert haben.</span><span class="sxs-lookup"><span data-stu-id="ee801-337">The procedures in this section require that you have installed the [Office 365 CLI](https://aka.ms/o365cli).</span></span> <span data-ttu-id="ee801-338">Als Nächstes stellen Sie mit dem Befehl [spo connect](https://pnp.github.io/office365-cli/cmd/spo/connect/) eine Verbindung mit Ihrem SharePoint Online-Mandanten her.</span><span class="sxs-lookup"><span data-stu-id="ee801-338">Next, connect to your SharePoint Online tenant using the [spo connect](https://pnp.github.io/office365-cli/cmd/spo/connect/) command.</span></span>

<span data-ttu-id="ee801-339">Führen Sie die folgenden Schritte aus, um das CDN einzurichten und zu konfigurieren, um Ihre Objekte in SharePoint Online mit der Office 365 CLI zu hosten.</span><span class="sxs-lookup"><span data-stu-id="ee801-339">Complete these steps to set up and configure the CDN to host your assets in SharePoint Online using the Office 365 CLI.</span></span>

### <a name="enable-the-office-365-cdn"></a><span data-ttu-id="ee801-340">Aktivieren des Office 365 CDN</span><span class="sxs-lookup"><span data-stu-id="ee801-340">Enable the Office 365 CDN</span></span>

<span data-ttu-id="ee801-341">Sie können den Status des Office 365 CDN in Ihrem Mandanten mithilfe des Cmdlets [spo cdn set](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-set/) verwalten.</span><span class="sxs-lookup"><span data-stu-id="ee801-341">You can manage the state of the Office 365 CDN in your tenant using the [spo cdn set](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-set/) command.</span></span>

<span data-ttu-id="ee801-342">Um das öffentliche Office 365 CDN in Ihrem Mandanten zu aktivieren, führen Sie Folgendes aus:</span><span class="sxs-lookup"><span data-stu-id="ee801-342">To enable the Office 365 Public CDN in your tenant execute:</span></span>

```sh
spo cdn set --type Public --enabled true
```

<span data-ttu-id="ee801-343">Führen Sie Folgendes aus, um das Office 365 SharePoint CDN zu aktivieren:</span><span class="sxs-lookup"><span data-stu-id="ee801-343">To enable the Office 365 SharePoint CDN, execute:</span></span>

```sh
spo cdn set --type Private --enabled true
```

#### <a name="view-the-current-status-of-the-office-365-cdn"></a><span data-ttu-id="ee801-344">Anzeigen des aktuellen Status des Office 365 CDN</span><span class="sxs-lookup"><span data-stu-id="ee801-344">View the current status of the Office 365 CDN</span></span>

<span data-ttu-id="ee801-345">Um zu überprüfen, ob der bestimmte Typ von Office 365 CDN aktiviert oder deaktiviert ist, verwenden Sie den Befehl [SPO CDN Get](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-get/) .</span><span class="sxs-lookup"><span data-stu-id="ee801-345">To check if the particular type of Office 365 CDN is enabled or disabled, use the [spo cdn get](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-get/) command.</span></span>

<span data-ttu-id="ee801-346">Um zu überprüfen, ob das öffentliche Office 365 CDN aktiviert ist, führen Sie Folgendes aus:</span><span class="sxs-lookup"><span data-stu-id="ee801-346">To check if the Office 365 Public CDN is enabled, execute:</span></span>

```sh
spo cdn get --type Public
```

### <a name="view-the-office-365-cdn-origins"></a><span data-ttu-id="ee801-347">Anzeigen der Office 365 CDN-Ursprünge</span><span class="sxs-lookup"><span data-stu-id="ee801-347">View the Office 365 CDN origins</span></span>

<span data-ttu-id="ee801-348">Um die derzeit konfigurierten öffentlichen Office 365 CDN-Ursprünge anzuzeigen, führen Sie Folgendes aus:</span><span class="sxs-lookup"><span data-stu-id="ee801-348">To view the currently configured Office 365 Public CDN origins execute:</span></span>

```sh
spo cdn origin list --type Public
```

<span data-ttu-id="ee801-349">Informationen zu den Ursprüngen, die standardmäßig bereitgestellt werden, wenn Sie das Office 365 CDN aktivieren, finden Sie unter [default CDN Origins](use-office-365-cdn-with-spo.md#default-cdn-origins) .</span><span class="sxs-lookup"><span data-stu-id="ee801-349">See [Default CDN origins](use-office-365-cdn-with-spo.md#default-cdn-origins) for information about the origins that are provisioned by default when you enable the Office 365 CDN.</span></span>

### <a name="add-an-office-365-cdn-origin"></a><span data-ttu-id="ee801-350">Hinzufügen eines Office 365 CDN-Ursprungs</span><span class="sxs-lookup"><span data-stu-id="ee801-350">Add an Office 365 CDN origin</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ee801-351">Sie sollten niemals Ressourcen, die für Ihre Organisation als vertraulich gelten, in einer SharePoint-Dokumentbibliothek platzieren, die als öffentlicher Ursprung konfiguriert ist.</span><span class="sxs-lookup"><span data-stu-id="ee801-351">You should never place resources that are considered sensitive to your organization in a SharePoint document library configured as a public origin.</span></span>

<span data-ttu-id="ee801-352">Verwenden Sie den Befehl [spo cdn origin add](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-add/) zum Definieren eines CDN-Ursprungs.</span><span class="sxs-lookup"><span data-stu-id="ee801-352">Use the [spo cdn origin add](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-add/) command to define a CDN origin.</span></span> <span data-ttu-id="ee801-353">Sie können mehrere Ursprünge definieren.</span><span class="sxs-lookup"><span data-stu-id="ee801-353">You can define multiple origins.</span></span> <span data-ttu-id="ee801-354">Der Ursprung ist eine URL, die auf eine SharePoint-Bibliothek oder einen Ordner mit den Objekten verweist, die vom CDN gehostet werden sollen.</span><span class="sxs-lookup"><span data-stu-id="ee801-354">The origin is a URL that points to a SharePoint library or folder that contains the assets that you want to be hosted by the CDN.</span></span>

```sh
spo cdn origin add --type [Public | Private] --origin <path>
```

<span data-ttu-id="ee801-355">Dabei `path` ist der relative Pfad zu dem Ordner, der die Objekte enthält.</span><span class="sxs-lookup"><span data-stu-id="ee801-355">Where `path` is the relative path to the folder that contains the assets.</span></span> <span data-ttu-id="ee801-356">Sie können Platzhalter zusätzlich zu relativen Pfaden verwenden.</span><span class="sxs-lookup"><span data-stu-id="ee801-356">You can use wildcards in addition to relative paths.</span></span>

<span data-ttu-id="ee801-357">Um alle Objekte im **Gestaltungsvorlagenkatalog** aller Websites als öffentlichen Ursprung einzuschließen, führen Sie Folgendes aus:</span><span class="sxs-lookup"><span data-stu-id="ee801-357">To include all assets in the **Master Page Gallery** of all sites as a public origin, execute:</span></span>

```sh
spo cdn origin add --type Public --origin */masterpage
```

<span data-ttu-id="ee801-358">Um einen privaten Ursprung für eine bestimmte Websitesammlung zu konfigurieren, führen Sie Folgendes aus:</span><span class="sxs-lookup"><span data-stu-id="ee801-358">To configure a private origin for a specific site collection, execute:</span></span>

```sh
spo cdn origin add --type Private --origin sites/site1/siteassets
```

> [!NOTE]
> <span data-ttu-id="ee801-359">Nach dem Hinzufügen eines CDN-Ursprungs dauert es bis zu 15 Minuten, bis Sie Dateien mithilfe des CDN-Diensts abrufen können.</span><span class="sxs-lookup"><span data-stu-id="ee801-359">After adding a CDN origin, it might take up to 15 minutes for you to be able to retrieve files via the CDN service.</span></span> <span data-ttu-id="ee801-360">Sie können überprüfen, ob der betreffende Ursprung bereits aktiviert wurde, indem Sie den Befehl [spo cdn origin list](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-list/) verwenden.</span><span class="sxs-lookup"><span data-stu-id="ee801-360">You can verify if the particular origin has already been enabled using the [spo cdn origin list](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-list/) command.</span></span>

### <a name="remove-an-office-365-cdn-origin"></a><span data-ttu-id="ee801-361">Entfernen eines Office 365 CDN-Ursprungs</span><span class="sxs-lookup"><span data-stu-id="ee801-361">Remove an Office 365 CDN origin</span></span>

<span data-ttu-id="ee801-362">Verwenden Sie den Befehl [spo cdn origin remove](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-remove/), um einen CDN-Ursprung für den angegebenen CDN-Typ zu entfernen.</span><span class="sxs-lookup"><span data-stu-id="ee801-362">Use the [spo cdn origin remove](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-remove/) command to remove a CDN origin for the specified CDN type.</span></span>

<span data-ttu-id="ee801-363">Wenn Sie einen öffentlichen Ursprung aus der CDN-Konfiguration entfernen möchten, führen Sie Folgendes aus:</span><span class="sxs-lookup"><span data-stu-id="ee801-363">To remove a public origin from the CDN configuration, execute:</span></span>

```sh
spo cdn origin remove --type Public --origin */masterpage
```

> [!NOTE]
> <span data-ttu-id="ee801-364">Das Entfernen eines CDN-Ursprungs hat keine Auswirkungen auf die Dateien, die in einer Dokumentbibliothek gespeichert sind, die mit diesem Ursprung übereinstimmt.</span><span class="sxs-lookup"><span data-stu-id="ee801-364">Removing a CDN origin doesn't affect the files stored in any document library matching that origin.</span></span> <span data-ttu-id="ee801-365">Wenn auf diese Objekte mithilfe Ihrer SharePoint-URL verwiesen wird, wechselt SharePoint automatisch zurück zur ursprünglichen URL, die auf die Dokumentbibliothek zeigt.</span><span class="sxs-lookup"><span data-stu-id="ee801-365">If these assets have been referenced using their SharePoint URL, SharePoint will automatically switch back to the original URL pointing to the document library.</span></span> <span data-ttu-id="ee801-366">Wenn jedoch auf Objekte mithilfe einer öffentlichen CDN-URL verwiesen wurde, wird die Verknüpfung durch Entfernen des Ursprungs unterbrochen, und Sie müssen Sie manuell ändern.</span><span class="sxs-lookup"><span data-stu-id="ee801-366">If, however, assets have been referenced using a public CDN URL, then removing the origin will break the link and you will need to manually change them.</span></span>

### <a name="modify-an-office-365-cdn-origin"></a><span data-ttu-id="ee801-367">Ändern eines Office 365 CDN-Ursprungs</span><span class="sxs-lookup"><span data-stu-id="ee801-367">Modify an Office 365 CDN origin</span></span>

<span data-ttu-id="ee801-368">Es ist nicht möglich, einen vorhandenen CDN-Ursprung zu ändern.</span><span class="sxs-lookup"><span data-stu-id="ee801-368">It's not possible to modify an existing CDN origin.</span></span> <span data-ttu-id="ee801-369">Stattdessen sollten Sie den zuvor definierten CDN-Ursprung mit dem Befehl `spo cdn origin remove` entfernen und mit dem Befehl `spo cdn origin add` einen neuen hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="ee801-369">Instead, you should remove the previously defined CDN origin using the `spo cdn origin remove` command and add a new one using the `spo cdn origin add` command.</span></span>

### <a name="change-the-types-of-files-to-include-in-the-office-365-cdn"></a><span data-ttu-id="ee801-370">Ändern der Dateitypen, die in Office 365 CDN eingeschlossen werden sollen</span><span class="sxs-lookup"><span data-stu-id="ee801-370">Change the types of files to include in the Office 365 CDN</span></span>

<span data-ttu-id="ee801-371">Standardmäßig sind die folgenden Dateitypen im CDN enthalten: _CSS, EOT, GIF, ICO, JPEG, JPG, JS, MAP, PNG, SVG, TTF und WOFF_.</span><span class="sxs-lookup"><span data-stu-id="ee801-371">By default, the following file types are included in the CDN: _.css, .eot, .gif, .ico, .jpeg, .jpg, .js, .map, .png, .svg, .ttf, and .woff_.</span></span> <span data-ttu-id="ee801-372">Wenn Sie weitere Dateitypen in das CDN einbeziehen müssen, können Sie die CDN-Konfiguration mit dem Befehl [spo cdn policy set](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-policy-set/) ändern.</span><span class="sxs-lookup"><span data-stu-id="ee801-372">If you need to include additional file types in the CDN, you can change the CDN configuration using the [spo cdn policy set](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-policy-set/) command.</span></span>

> [!NOTE]
> <span data-ttu-id="ee801-373">Durch das Ändern der Liste von Dateitypen überschreiben Sie die aktuell definierte Liste.</span><span class="sxs-lookup"><span data-stu-id="ee801-373">When changing the list of file types, you overwrite the currently defined list.</span></span> <span data-ttu-id="ee801-374">Wenn Sie weitere Dateitypen einbeziehen möchten, verwenden Sie zunächst den Befehl [spo cdn policy list](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-list/), um herauszufinden, welche Dateitypen derzeit konfiguriert sind.</span><span class="sxs-lookup"><span data-stu-id="ee801-374">If you want to include additional file types, first use the [spo cdn policy list](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-list/) command to find out which file types are currently configured.</span></span>

<span data-ttu-id="ee801-375">Führen Sie den folgenden Befehl aus, um den _JSON_ -Dateityp zur Standardliste der im öffentlichen CDN enthaltenen Dateitypen hinzuzufügen:</span><span class="sxs-lookup"><span data-stu-id="ee801-375">To add the _JSON_ file type to the default list of file types included in the public CDN, execute:</span></span>

```sh
spo cdn policy set --type Public --policy IncludeFileExtensions --value "CSS,EOT,GIF,ICO,JPEG,JPG,JS,MAP,PNG,SVG,TTF,WOFF,JSON"
```

### <a name="change-the-list-of-site-classifications-you-want-to-exclude-from-the-office-365-cdn"></a><span data-ttu-id="ee801-376">Ändern der Liste von Websiteklassifizierungen, die Sie aus dem Office 365 CDN ausschließen möchten</span><span class="sxs-lookup"><span data-stu-id="ee801-376">Change the list of site classifications you want to exclude from the Office 365 CDN</span></span>

<span data-ttu-id="ee801-377">Verwenden Sie den Befehl [spo cdn policy set](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-policy-set/) zum Ausschließen von Websiteklassifizierungen, die Sie nicht über das CDN zur Verfügung stellen möchten.</span><span class="sxs-lookup"><span data-stu-id="ee801-377">Use the [spo cdn policy set](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-policy-set/) command to exclude site classifications that you do not want to make available over the CDN.</span></span> <span data-ttu-id="ee801-378">Standardmäßig sind keine Websiteklassifizierungen ausgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="ee801-378">By default, no site classifications are excluded.</span></span>

> [!NOTE]
> <span data-ttu-id="ee801-379">Durch das Ändern der Liste der ausgeschlossenen Websiteklassifizierungen überschreiben Sie die aktuell definierte Liste.</span><span class="sxs-lookup"><span data-stu-id="ee801-379">When changing the list of excluded site classifications, you overwrite the currently defined list.</span></span> <span data-ttu-id="ee801-380">Wenn Sie zusätzliche Klassifizierungen ausschließen möchten, verwenden Sie zunächst den Befehl [spo cdn policy list](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-policy-list/), um herauszufinden, welche Klassifizierungen derzeit konfiguriert sind.</span><span class="sxs-lookup"><span data-stu-id="ee801-380">If you want to exclude additional classifications, first use the [spo cdn policy list](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-policy-list/) command to find out which classifications are currently configured.</span></span>

<span data-ttu-id="ee801-381">Zum Ausschließen von Websites, die als _HBI_ aus dem öffentlichen CDN klassifiziert wurden, führen Sie</span><span class="sxs-lookup"><span data-stu-id="ee801-381">To exclude sites classified as _HBI_ from the public CDN, execute</span></span>

```sh
spo cdn policy set --type Public --policy ExcludeRestrictedSiteClassifications --value "HBI"
```

### <a name="disable-the-office-365-cdn"></a><span data-ttu-id="ee801-382">Deaktivieren von Office 365 CDN</span><span class="sxs-lookup"><span data-stu-id="ee801-382">Disable the Office 365 CDN</span></span>

<span data-ttu-id="ee801-383">Um das Office 365 CDN zu deaktivieren, verwenden Sie den Befehl `spo cdn set`. Beispiel:</span><span class="sxs-lookup"><span data-stu-id="ee801-383">To disable the Office 365 CDN use the `spo cdn set` command, for example:</span></span>

```sh
spo cdn set --type Public --enabled false
```

## <a name="using-your-cdn-assets"></a><span data-ttu-id="ee801-384">Verwenden der CDN-Ressourcen</span><span class="sxs-lookup"><span data-stu-id="ee801-384">Using your CDN assets</span></span>

<span data-ttu-id="ee801-385">Nachdem Sie das CDN aktiviert und die Ursprünge und Richtlinien konfiguriert haben, können Sie mit der Verwendung der CDN-Ressourcen beginnen.</span><span class="sxs-lookup"><span data-stu-id="ee801-385">Now that you have enabled the CDN and configured origins and policies, you can begin using your CDN assets.</span></span>

<span data-ttu-id="ee801-386">In diesem Abschnitt erfahren Sie, wie Sie CDN-URLs in Ihren SharePoint-Seiten und-Inhalten verwenden können, damit SharePoint Anforderungen für Objekte in öffentlichen und privaten Quellen an das CDN umleitet.</span><span class="sxs-lookup"><span data-stu-id="ee801-386">This section will help you understand how to use CDN URLs in your SharePoint pages and content so that SharePoint redirects requests for assets in both public and private origins to the CDN.</span></span>

- [<span data-ttu-id="ee801-387">Aktualisieren von Links zu CDN-Objekten</span><span class="sxs-lookup"><span data-stu-id="ee801-387">Updating links to CDN assets</span></span>](use-office-365-cdn-with-spo.md#updating-links-to-cdn-assets)
- [<span data-ttu-id="ee801-388">Verwenden von Objekten in öffentlichen Ursprüngen</span><span class="sxs-lookup"><span data-stu-id="ee801-388">Using assets in public origins</span></span>](use-office-365-cdn-with-spo.md#using-assets-in-public-origins)
- [<span data-ttu-id="ee801-389">Verwenden von Objekten in privaten Ursprüngen</span><span class="sxs-lookup"><span data-stu-id="ee801-389">Using assets in private origins</span></span>](use-office-365-cdn-with-spo.md#using-assets-in-private-origins)

<span data-ttu-id="ee801-390">Informationen zur Verwendung des CDN für das Hosten von clientseitigen Webparts finden Sie im Thema [Hosten des clientseitigen Webparts aus Office 365 CDN (Hello World, Teil 4)](https://docs.microsoft.com/en-us/sharepoint/dev/spfx/web-parts/get-started/hosting-webpart-from-office-365-cdn).</span><span class="sxs-lookup"><span data-stu-id="ee801-390">For information on how to use the CDN for hosting client-side web parts, see the topic [Host your client-side web part from Office 365 CDN (Hello World part 4)](https://docs.microsoft.com/en-us/sharepoint/dev/spfx/web-parts/get-started/hosting-webpart-from-office-365-cdn).</span></span>

### <a name="updating-links-to-cdn-assets"></a><span data-ttu-id="ee801-391">Aktualisieren von Links zu CDN-Objekten</span><span class="sxs-lookup"><span data-stu-id="ee801-391">Updating links to CDN assets</span></span>

<span data-ttu-id="ee801-392">Um Objekte zu verwenden, die Sie einem Ursprung hinzugefügt haben, aktualisieren Sie einfach die Links zur ursprünglichen Datei mit dem Pfad zu der Datei im Ursprung.</span><span class="sxs-lookup"><span data-stu-id="ee801-392">To use assets that you have added to an origin, you simply update links to the original file with the path to the file in the origin.</span></span>

- <span data-ttu-id="ee801-393">Bearbeiten Sie die Seite oder den Inhalt, die Links zu Objekten enthält, die Sie einem Ursprung hinzugefügt haben.</span><span class="sxs-lookup"><span data-stu-id="ee801-393">Edit the page or content that contains links to assets you have added to an origin.</span></span> <span data-ttu-id="ee801-394">Sie können auch eine von mehreren Methoden verwenden, um Hyperlinks Global zu suchen und zu ersetzen, wenn Sie die Verknüpfung zu einem bestimmten Element überall dort, wo es angezeigt wird, aktualisieren möchten.</span><span class="sxs-lookup"><span data-stu-id="ee801-394">You can also use one of several methods to globally search and replace links across an enter site or site collection if you want to update the link to a given asset everywhere it appears.</span></span>
- <span data-ttu-id="ee801-395">Ersetzen Sie für jede Verknüpfung zu einem Objekt in einem Ursprung den Pfad durch den Pfad zu der Datei im CDN-Ursprung.</span><span class="sxs-lookup"><span data-stu-id="ee801-395">For each link to an asset in an origin, replace the path with the path to the file in the CDN origin.</span></span> <span data-ttu-id="ee801-396">Sie können relative Pfade verwenden.</span><span class="sxs-lookup"><span data-stu-id="ee801-396">You can use relative paths.</span></span>
- <span data-ttu-id="ee801-397">Speichern Sie die Seite oder den Inhalt.</span><span class="sxs-lookup"><span data-stu-id="ee801-397">Save the page or content.</span></span>

<span data-ttu-id="ee801-398">Betrachten Sie beispielsweise das Bild _/Site/SiteAssets/Images/Image.png_, das Sie in den Dokumentbibliotheksordner _/Site/CDN_origins/Public/_ kopiert haben.</span><span class="sxs-lookup"><span data-stu-id="ee801-398">For example, consider the image _/site/SiteAssets/images/image.png_, which you have copied to the document library folder _/site/CDN_origins/public/_.</span></span> <span data-ttu-id="ee801-399">Um das CDN-Objekt zu verwenden, ersetzen Sie den ursprünglichen Pfad zum Speicherort der Bild Datei durch den Pfad zum Ursprung, um die neue URL _/Site/CDN_origins/Public/Image.png_.</span><span class="sxs-lookup"><span data-stu-id="ee801-399">To use the CDN asset, replace the original path to the image file location with the path to the origin to make the new URL _/site/CDN_origins/public/image.png_.</span></span>

<span data-ttu-id="ee801-400">Wenn Sie die vollständige URL des Objekts anstelle eines relativen Pfads verwenden möchten, erstellen Sie den Link wie folgt:</span><span class="sxs-lookup"><span data-stu-id="ee801-400">If you want to use the full URL to the asset instead of a relative path, construct the link like so:</span></span>

`https://<TenantHostName>.sharepoint.com/sites/site/CDN_origins/public/image.png`

> [!NOTE]
> <span data-ttu-id="ee801-401">Im Allgemeinen sollten Sie URLs nicht direkt für Objekte im CDN hartcodieren.</span><span class="sxs-lookup"><span data-stu-id="ee801-401">In general, you should not hardcode URLs directly to assets in the CDN.</span></span> <span data-ttu-id="ee801-402">Sie können jedoch URLs für Objekte in öffentlichen Ursprüngen bei Bedarf manuell erstellen.</span><span class="sxs-lookup"><span data-stu-id="ee801-402">However, you can manually construct URLs for assets in public origins if needed.</span></span> <span data-ttu-id="ee801-403">Weitere Informationen finden Sie unter [hartcodieren von CDN-URLs für öffentliche Objekte](use-office-365-cdn-with-spo.md#hardcoding-cdn-urls-for-public-assets).</span><span class="sxs-lookup"><span data-stu-id="ee801-403">For more information, see [Hardcoding CDN URLs for public assets](use-office-365-cdn-with-spo.md#hardcoding-cdn-urls-for-public-assets).</span></span>

<span data-ttu-id="ee801-404">Informationen dazu, wie Sie überprüfen können, ob Objekte aus dem CDN bedient werden, finden Sie unter [wie bestätige ich, dass die Ressourcen vom CDN bedient werden?](use-office-365-cdn-with-spo.md#CDNConfirm) im Abschnitt [Troubleshooting the Office 365 CDN](use-office-365-cdn-with-spo.md#CDNTroubleshooting) .</span><span class="sxs-lookup"><span data-stu-id="ee801-404">To learn about how to verify that assets are being served from the CDN, see [How do I confirm that assets are being served by the CDN?](use-office-365-cdn-with-spo.md#CDNConfirm) in the [Troubleshooting the Office 365 CDN](use-office-365-cdn-with-spo.md#CDNTroubleshooting) section.</span></span>

### <a name="using-assets-in-public-origins"></a><span data-ttu-id="ee801-405">Verwenden von Objekten in öffentlichen Ursprüngen</span><span class="sxs-lookup"><span data-stu-id="ee801-405">Using assets in public origins</span></span>

<span data-ttu-id="ee801-406">Das **Veröffentlichungsfeature** in SharePoint Online schreibt URLs der in öffentlichen Ursprüngen gespeicherten Objekte automatisch in Ihre CDN-äquivalente ein, sodass Objekte aus dem CDN-Dienst statt aus SharePoint bedient werden.</span><span class="sxs-lookup"><span data-stu-id="ee801-406">The **Publishing feature** in SharePoint Online automatically rewrites URLs of assets stored in public origins to their CDN equivalents so that assets are served from the CDN service instead of SharePoint.</span></span>

<span data-ttu-id="ee801-407">Wenn sich Ihr Ursprung in einer Website befindet, in der das Veröffentlichungsfeature aktiviert ist und die Objekte, die Sie in das CDN übertragen möchten, sich in einer der folgenden Kategorien befinden, wird SharePoint die URLs für Objekte im Ursprung automatisch neu schreiben, vorausgesetzt, dass das Objekt nicht von einem CDN ausgeschlossen wurde.  Richtlinie.</span><span class="sxs-lookup"><span data-stu-id="ee801-407">If your origin is in a site with the Publishing feature enabled, and the assets you want to offload to the CDN are in one of the following categories, SharePoint will automatically rewrite URLs for assets in the origin, provided that the asset has not been excluded by a CDN policy.</span></span>

<span data-ttu-id="ee801-408">Es folgt eine Übersicht über die Links, die automatisch vom SharePoint-Veröffentlichungsfeature umgeschrieben werden:</span><span class="sxs-lookup"><span data-stu-id="ee801-408">The following is an overview of which links are automatically rewritten by the SharePoint Publishing feature:</span></span>

- <span data-ttu-id="ee801-409">IMG/LINK/CSS-URLs in den HTML-Antworten klassischer Veröffentlichungsseiten</span><span class="sxs-lookup"><span data-stu-id="ee801-409">IMG/LINK/CSS URLs in classic publishing page HTML responses</span></span>
  - <span data-ttu-id="ee801-410">Dies schließt von Autoren im HTML-Inhalt einer Seite hinzugefügte Bilder ein.</span><span class="sxs-lookup"><span data-stu-id="ee801-410">This includes images added by authors within the HTML content of a page</span></span>
- <span data-ttu-id="ee801-411">Bild-URLs des Webparts „Bildbibliothek-Bildschirmpräsentation“</span><span class="sxs-lookup"><span data-stu-id="ee801-411">Picture Library SlideShow webpart image URLs</span></span>
- <span data-ttu-id="ee801-412">Bildfelder in Ergebnissen der SPList-REST-API (RenderListDataAsStream)</span><span class="sxs-lookup"><span data-stu-id="ee801-412">Image fields in SPList REST API (RenderListDataAsStream) results</span></span>
  - <span data-ttu-id="ee801-413">Verwenden der New-Eigenschaft _ImageFieldsToTryRewriteToCdnUrls_ zum Bereitstelleneiner durch Trennzeichen getrennten Liste von Feldern</span><span class="sxs-lookup"><span data-stu-id="ee801-413">Use the new property _ImageFieldsToTryRewriteToCdnUrls_ to provide a comma separated list of fields</span></span>
  - <span data-ttu-id="ee801-414">Unterstützt Hyperlink-Felder und Publishing Image-Felder</span><span class="sxs-lookup"><span data-stu-id="ee801-414">Supports hyperlink fields and PublishingImage fields</span></span>
- <span data-ttu-id="ee801-415">SharePoint-Bilddarstellungen</span><span class="sxs-lookup"><span data-stu-id="ee801-415">SharePoint image renditions</span></span>

<span data-ttu-id="ee801-416">Das folgende Diagramm veranschaulicht den Workflow, wenn SharePoint eine Anforderung für eine Seite erhält, die Objekte aus einem öffentlichen Ursprung enthält.</span><span class="sxs-lookup"><span data-stu-id="ee801-416">The following diagram illustrates the workflow when SharePoint receives a request for a page containing assets from a public origin.</span></span>

<span data-ttu-id="ee801-417">![Workflow Diagramm: Abrufen von Office 365 CDN-Ressourcen aus einem öffentlichen Ursprung] (media/O365-CDN/o365-cdn-public-steps-transparent.svg "Workflow: Abrufen von Office 365 CDN-Ressourcen aus einem öffentlichen Ursprung")</span><span class="sxs-lookup"><span data-stu-id="ee801-417">![Workflow diagram: Retrieving Office 365 CDN assets from a public origin](media/O365-CDN/o365-cdn-public-steps-transparent.svg "Workflow: Retrieving Office 365 CDN assets from a public origin")</span></span>

> [!TIP]
> <span data-ttu-id="ee801-418">Wenn Sie die automatische Umschreibung für bestimmte URLs auf einer Seite deaktivieren möchten, können Sie die Seite Auschecken und den Abfragezeichenfolgenparameter **?NoAutoReWrites = true** am Ende jeder zu deaktivierenden Verknüpfung hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="ee801-418">If you want to disable auto-rewriting for specific URLs on a page, you can check out the page and add the query string parameter **?NoAutoReWrites=true** to the end of each link you want to disable.</span></span>

#### <a name="hardcoding-cdn-urls-for-public-assets"></a><span data-ttu-id="ee801-419">Codieren von CDN-URLs für öffentliche Objekte</span><span class="sxs-lookup"><span data-stu-id="ee801-419">Hardcoding CDN URLs for public assets</span></span>

<span data-ttu-id="ee801-420">Wenn das _Veröffentlichungs_ Feature für einen öffentlichen Ursprung nicht aktiviert ist oder wenn es sich nicht um einen der vom Auto-Rewrite-Feature des CDN-Diensts unterstützten Linktypen handelt, können Sie URLs zum CDN-Speicherort der Objekte manuell erstellen und diese URLs in ihren Inhalten verwenden.</span><span class="sxs-lookup"><span data-stu-id="ee801-420">If the _Publishing_ feature is not enabled for a public origin, or the asset is not one of the link types supported by the auto-rewrite feature of the CDN service, you can manually construct URLs to the CDN location of the assets and use these URLs in your content.</span></span>

> [!NOTE]
> <span data-ttu-id="ee801-421">Sie können CDN-URLs nicht für Objekte in einem privaten Ursprung hartcodieren, da das erforderliche Zugriffstoken, das den letzten Abschnitt der URL bildet, zu dem Zeitpunkt generiert wird, zu dem die Ressource angefordert wird.</span><span class="sxs-lookup"><span data-stu-id="ee801-421">You cannot hardcode CDN URLs to assets in a private origin because the required access token that forms the last section of the URL is generated at the time the resource is requested.</span></span>

<span data-ttu-id="ee801-422">Bei öffentlichen CDN-Objekten sieht das URL-Format wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="ee801-422">For public CDN assets, the URL format will look like the following:</span></span>

``` html
https://publiccdn.sharepointonline.com/<TenantHostName>/sites/site/library/asset.png
```

<span data-ttu-id="ee801-423">Ersetzen Sie **TenantHostName** durch den Namen Ihres Mandanten.</span><span class="sxs-lookup"><span data-stu-id="ee801-423">Replace **TenantHostName** with your tenant name.</span></span> <span data-ttu-id="ee801-424">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="ee801-424">Example:</span></span>

``` html
https://publiccdn.sharepointonline.com/contoso.sharepoint.com/sites/site/library/asset.png
```

### <a name="using-assets-in-private-origins"></a><span data-ttu-id="ee801-425">Verwenden von Objekten in privaten Ursprüngen</span><span class="sxs-lookup"><span data-stu-id="ee801-425">Using assets in private origins</span></span>

<span data-ttu-id="ee801-426">Für die Verwendung von Objekten in privaten Quellen ist keine zusätzliche Konfiguration erforderlich.</span><span class="sxs-lookup"><span data-stu-id="ee801-426">No additional configuration is required to use assets in private origins.</span></span> <span data-ttu-id="ee801-427">SharePoint Online schreibt URLs automatisch für Objekte in privaten Quellen um, sodass Anforderungen für diese Objekte immer aus dem CDN bedient werden.</span><span class="sxs-lookup"><span data-stu-id="ee801-427">SharePoint Online automatically rewrites URLs for assets in private origins so requests for those assets will always be served from the CDN.</span></span> <span data-ttu-id="ee801-428">Sie können keine URLs manuell erstellen, um Objekte in privaten Quellen zu CDN, da diese URLs Token enthalten, die von SharePoint Online automatisch generiert werden müssen, wenn das Objekt angefordert wird.</span><span class="sxs-lookup"><span data-stu-id="ee801-428">You cannot manually build URLs to CDN assets in private origins because these URLs contain tokens that must be auto-generated by SharePoint Online at the time the asset is requested.</span></span>

<span data-ttu-id="ee801-429">Der Zugriff auf Objekte in privaten Quellen wird durch dynamisch generierte Token basierend auf den Benutzerberechtigungen für den Ursprung mit den in den folgenden Abschnitten beschriebenen Einschränkungen geschützt.</span><span class="sxs-lookup"><span data-stu-id="ee801-429">Access to assets in private origins is protected by dynamically generated tokens based on user permissions to the origin, with the caveats described in the following sections.</span></span> <span data-ttu-id="ee801-430">Benutzer benötigen mindestens **Lese** Zugriff auf die Ursprünge für das CDN, um Inhalte zu rendern.</span><span class="sxs-lookup"><span data-stu-id="ee801-430">Users must have at least **read** access to the origins for the CDN to render content.</span></span>

<span data-ttu-id="ee801-431">Das folgende Diagramm veranschaulicht den Workflow, wenn SharePoint eine Anforderung für eine Seite erhält, die Objekte aus einem privaten Ursprung enthält.</span><span class="sxs-lookup"><span data-stu-id="ee801-431">The following diagram illustrates the workflow when SharePoint receives a request for a page containing assets from a private origin.</span></span>

<span data-ttu-id="ee801-432">![Workflow Diagramm: Abrufen von Office 365 CDN-Ressourcen von einem privaten Ursprung] (media/O365-CDN/o365-cdn-private-steps-transparent.svg "Workflow: Abrufen von Office 365 CDN-Ressourcen aus einem privaten Ursprung")</span><span class="sxs-lookup"><span data-stu-id="ee801-432">![Workflow diagram: Retrieving Office 365 CDN assets from a private origin](media/O365-CDN/o365-cdn-private-steps-transparent.svg "Workflow: Retrieving Office 365 CDN assets from a private origin")</span></span>

#### <a name="token-based-authorization-in-private-origins"></a><span data-ttu-id="ee801-433">Token-basierte Autorisierung in privaten Ursprüngen</span><span class="sxs-lookup"><span data-stu-id="ee801-433">Token-based authorization in private origins</span></span>

<span data-ttu-id="ee801-434">Der Zugriff auf Objekte in privaten Quellen im Office 365 CDN wird von Token gewährt, die von SharePoint Online generiert werden.</span><span class="sxs-lookup"><span data-stu-id="ee801-434">Access to assets in private origins in the Office 365 CDN is granted by tokens generated by SharePoint Online.</span></span> <span data-ttu-id="ee801-435">Benutzer, die bereits über die Berechtigung zum Zugriff auf den vom Ursprung angegebenen Ordner oder die Bibliothek verfügen, erhalten automatisch Token, die es dem Benutzer ermöglichen, auf die Datei basierend auf Ihrer Berechtigungsstufe zuzugreifen.</span><span class="sxs-lookup"><span data-stu-id="ee801-435">Users who already have permission to access to the folder or library designated by the origin are automatically granted tokens that permit the user to access the file based on their permission level.</span></span> <span data-ttu-id="ee801-436">Diese Zugriffstoken sind 30 bis 90 Minuten lang gültig, nachdem Sie generiert wurden, um Token Replay-Angriffe zu verhindern.</span><span class="sxs-lookup"><span data-stu-id="ee801-436">These access tokens are valid for 30 to 90 minutes after they are generated to help prevent token replay attacks.</span></span>

<span data-ttu-id="ee801-437">Nachdem das Zugriffstoken generiert wurde, gibt SharePoint Online einen benutzerdefinierten URI an den Client zurück, der zwei Autorisierungsparameter _Eat_ (Edge Authorization Token) und _OAT_ (Origin-Autorisierungstoken) enthält.</span><span class="sxs-lookup"><span data-stu-id="ee801-437">Once the access token is generated, SharePoint Online returns a custom URI to the client containing two authorization parameters _eat_ (edge authorization token) and _oat_ (origin authorization token).</span></span> <span data-ttu-id="ee801-438">Die Struktur der einzelnen Token ist _<'expiration Time in Epoch Time Format'>__<'secure signature'>_.</span><span class="sxs-lookup"><span data-stu-id="ee801-438">The structure of each token is _<'expiration time in Epoch time format'>__<'secure signature'>_.</span></span> <span data-ttu-id="ee801-439">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="ee801-439">For example:</span></span>

``` html
https://privatecdn.sharepointonline.com/contoso.sharepoint.com/sites/site1/library1/folder1/image1.jpg?eat=1486154359_cc59042c5c55c90b26a2775323c7c8112718431228fe84d568a3795a63912840&oat=1486154359_7d73c2e3ba4b7b1f97242332900616db0d4ffb04312
```

> [!NOTE]
> <span data-ttu-id="ee801-440">Jeder, der über das Token verfügt, kann auf die Ressource im CDN zugreifen.</span><span class="sxs-lookup"><span data-stu-id="ee801-440">Anyone in possession of the token can access the resource in the CDN.</span></span> <span data-ttu-id="ee801-441">URLs, die diese Zugriffstoken enthalten, werden jedoch nur über HTTPS freigegeben, es sei denn, die URL wird explizit von einem Endbenutzer freigegeben, bevor das Token abläuft, auf das Objekt können unbefugte Benutzer nicht zugreifen.</span><span class="sxs-lookup"><span data-stu-id="ee801-441">However, URLs containing these access tokens are only shared over HTTPS, so unless the URL is explicitly shared by an end user before the token expires, the asset won’t be accessible to unauthorized users.</span></span>

#### <a name="item-level-permissions-are-not-supported-for-assets-in-private-origins"></a><span data-ttu-id="ee801-442">Berechtigungen auf Elementebene werden für Objekte in privaten Quellen nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="ee801-442">Item-level permissions are not supported for assets in private origins</span></span>

<span data-ttu-id="ee801-443">Beachten Sie, dass SharePoint Online keine Berechtigungen auf Elementebene für Objekte in privaten Quellen unterstützt.</span><span class="sxs-lookup"><span data-stu-id="ee801-443">It is important to note that SharePoint Online does not support item-level permissions for assets in private origins.</span></span> <span data-ttu-id="ee801-444">Bei einer Datei unter `https://contoso.sharepoint.com/sites/site1/library1/folder1/image1.jpg`befindet sich der Benutzer beispielsweise in einem effektiven Zugriff auf die Datei, wenn die folgenden Bedingungen erfüllt sind:</span><span class="sxs-lookup"><span data-stu-id="ee801-444">For example, for a file located at `https://contoso.sharepoint.com/sites/site1/library1/folder1/image1.jpg`, users have effective access to the file given the following conditions:</span></span>

|<span data-ttu-id="ee801-445">Benutzer</span><span class="sxs-lookup"><span data-stu-id="ee801-445">User</span></span>  |<span data-ttu-id="ee801-446">Berechtigungen</span><span class="sxs-lookup"><span data-stu-id="ee801-446">Permissions</span></span>  |<span data-ttu-id="ee801-447">Effektiver Zugriff</span><span class="sxs-lookup"><span data-stu-id="ee801-447">Effective access</span></span>  |
|---------|---------|---------|
|<span data-ttu-id="ee801-448">Benutzer 1</span><span class="sxs-lookup"><span data-stu-id="ee801-448">User 1</span></span>     |<span data-ttu-id="ee801-449">Zugriff auf Folder1</span><span class="sxs-lookup"><span data-stu-id="ee801-449">Has access to folder1</span></span>         |<span data-ttu-id="ee801-450">Zugriff auf image1. jpg aus dem CDN</span><span class="sxs-lookup"><span data-stu-id="ee801-450">Can access image1.jpg from the CDN</span></span>         |
|<span data-ttu-id="ee801-451">Benutzer 2</span><span class="sxs-lookup"><span data-stu-id="ee801-451">User 2</span></span>     |<span data-ttu-id="ee801-452">Hat keinen Zugriff auf Folder1</span><span class="sxs-lookup"><span data-stu-id="ee801-452">Does not have access to folder1</span></span>         |<span data-ttu-id="ee801-453">Zugriff auf image1. jpg aus dem CDN nicht möglich</span><span class="sxs-lookup"><span data-stu-id="ee801-453">Cannot access image1.jpg from the CDN</span></span>         |
|<span data-ttu-id="ee801-454">Benutzer 3</span><span class="sxs-lookup"><span data-stu-id="ee801-454">User 3</span></span>     |<span data-ttu-id="ee801-455">Hat keinen Zugriff auf Folder1, es wird jedoch eine explizite Berechtigung für den Zugriff auf image1. jpg in SharePoint Online erteilt.</span><span class="sxs-lookup"><span data-stu-id="ee801-455">Does not have access to folder1, but is granted explicit permission to access image1.jpg in SharePoint Online</span></span>         |<span data-ttu-id="ee801-456">Zugriff auf die Ressource image1. jpg direkt über SharePoint Online, jedoch nicht über das CDN</span><span class="sxs-lookup"><span data-stu-id="ee801-456">Can access the asset image1.jpg directly from SharePoint Online, but not from the CDN</span></span>         |
|<span data-ttu-id="ee801-457">Benutzer 4</span><span class="sxs-lookup"><span data-stu-id="ee801-457">User 4</span></span>     |<span data-ttu-id="ee801-458">Zugriff auf Folder1, der Zugriff auf image1. jpg in SharePoint Online wurde jedoch explizit verweigert.</span><span class="sxs-lookup"><span data-stu-id="ee801-458">Has access to folder1, but has been explicitly denied access to image1.jpg in SharePoint Online</span></span>         |<span data-ttu-id="ee801-459">Zugriff auf das Objekt nicht über SharePoint Online, aber Zugriff auf das Objekt aus dem CDN, obwohl der Zugriff auf die Datei in SharePoint Online verweigert wurde</span><span class="sxs-lookup"><span data-stu-id="ee801-459">Cannot access the asset from SharePoint Online, but can access the asset from the CDN despite being denied access to the file in SharePoint Online</span></span>         |

## <a name="troubleshooting-the-office-365-cdn"></a><span data-ttu-id="ee801-460">Problembehandlung für Office 365 CDN</span><span class="sxs-lookup"><span data-stu-id="ee801-460">Troubleshooting the Office 365 CDN</span></span>
<a name="CDNTroubleshooting"> </a>

### <a name="how-do-i-confirm-that-assets-are-being-served-by-the-cdn"></a><span data-ttu-id="ee801-461">Wie bestätige ich, dass die Ressourcen vom CDN bedient werden?</span><span class="sxs-lookup"><span data-stu-id="ee801-461">How do I confirm that assets are being served by the CDN?</span></span>
<a name="CDNConfirm"> </a>

<span data-ttu-id="ee801-462">Nachdem Sie Links zu CDN-Objekten zu einer Seite hinzugefügt haben, können Sie überprüfen, ob die Ressource aus dem CDN bedient wird, indem Sie zur Seite navigieren, mit der rechten Maustaste auf das Bild klicken, nachdem es gerendert wurde, und die Bild-URL überprüft.</span><span class="sxs-lookup"><span data-stu-id="ee801-462">Once you have added links to CDN assets to a page, you can confirm that the asset is being served from the CDN by browsing to the page, right clicking on the image once it has rendered and reviewing the image URL.</span></span>

<span data-ttu-id="ee801-463">Sie können die Entwicklertools des Browsers auch verwenden, um die URL für die einzelnen Ressourcen auf einer Seite anzuzeigen, oder um ein Netzwerk Ablaufverfolgungstool von Drittanbietern zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="ee801-463">You can also use your browser's developer tools to view the URL for each asset on a page, or use a 3rd party network trace tool.</span></span>

> [!NOTE]
> <span data-ttu-id="ee801-464">Wenn Sie ein Netzwerktool wie Fiddler verwenden, um Ihre Objekte außerhalb des Renderings des Objekts von einer SharePoint-Seite zu testen, müssen Sie den Referrer-Header "Referrer `https://yourdomain.sharepoint.com`:" manuell zur Get-Anforderung hinzufügen, wobei die URL die Stamm-URL Ihres SharePoint Online-Mandanten ist.</span><span class="sxs-lookup"><span data-stu-id="ee801-464">If you use a network tool such as Fiddler to test your assets outside of rendering the asset from a SharePoint page, you must manually add the referrer header “Referrer: `https://yourdomain.sharepoint.com`” to the GET request where the URL is the root URL of your SharePoint Online tenant.</span></span>

<span data-ttu-id="ee801-465">Sie können CDN-URLs nicht direkt in einem Webbrowser testen, da Sie über einen Verweis aus SharePoint Online verfügen müssen.</span><span class="sxs-lookup"><span data-stu-id="ee801-465">You cannot test CDN URLs directly in a web browser because you must have a referrer coming from SharePoint Online.</span></span> <span data-ttu-id="ee801-466">Wenn Sie jedoch die CDN-Objekt-URL zu einer SharePoint-Seite hinzufügen und dann die Seite in einem Browser öffnen, sehen Sie das CDN-Objekt, das auf der Seite gerendert wird.</span><span class="sxs-lookup"><span data-stu-id="ee801-466">However, if you add the CDN asset URL to a SharePoint page and then open the page in a browser, you will see the CDN asset rendered on the page.</span></span>

<span data-ttu-id="ee801-467">Weitere Informationen zur Verwendung der Entwicklertools im Microsoft Edge-Browser finden Sie unter [Microsoft Edge Developer Tools](https://docs.microsoft.com/en-us/microsoft-edge/devtools-guide).</span><span class="sxs-lookup"><span data-stu-id="ee801-467">For more information on using the developer tools in the Microsoft Edge browser, see [Microsoft Edge Developer Tools](https://docs.microsoft.com/en-us/microsoft-edge/devtools-guide).</span></span>

### <a name="why-are-assets-from-a-new-origin-unavailable"></a><span data-ttu-id="ee801-468">Warum sind Objekte aus einem neuen Ursprung nicht verfügbar?</span><span class="sxs-lookup"><span data-stu-id="ee801-468">Why are assets from a new origin unavailable?</span></span>
<span data-ttu-id="ee801-469">Objekte in New Origins stehen nicht sofort zur Verfügung, da es Zeit braucht, bis die Registrierung über das CDN propagiert wird und die Objekte vom Ursprung zum CDN-Speicher hochgeladen werden.</span><span class="sxs-lookup"><span data-stu-id="ee801-469">Assets in new origins will not immediately be available for use, as it takes time for the registration to propagate through the CDN and for the assets to be uploaded from the origin to CDN storage.</span></span> <span data-ttu-id="ee801-470">Die Zeit, die für die Verfügbarkeit von Objekten im CDN erforderlich ist, hängt von der Anzahl der Objekte und den Dateien ab.</span><span class="sxs-lookup"><span data-stu-id="ee801-470">The time required for assets to be available in the CDN depends on how many assets and the files sizes.</span></span>

### <a name="my-client-side-web-part-or-sharepoint-framework-solution-isnt-working"></a><span data-ttu-id="ee801-471">Mein clientseitiges Webpart oder die SharePoint Framework-Lösung funktioniert nicht</span><span class="sxs-lookup"><span data-stu-id="ee801-471">My client-side web part or SharePoint Framework solution isn't working</span></span>

<span data-ttu-id="ee801-472">Wenn Sie das Office 365 CDN für öffentliche Ursprünge aktivieren, erstellt der CDN-Dienst automatisch diese Standard Ursprünge:</span><span class="sxs-lookup"><span data-stu-id="ee801-472">When you enable the Office 365 CDN for public origins, the CDN service automatically creates these default origins:</span></span>

- <span data-ttu-id="ee801-473">\*/MASTERPAGE</span><span class="sxs-lookup"><span data-stu-id="ee801-473">\*/MASTERPAGE</span></span>
- <span data-ttu-id="ee801-474">\*/STYLE-BIBLIOTHEK</span><span class="sxs-lookup"><span data-stu-id="ee801-474">\*/STYLE LIBRARY</span></span>
- <span data-ttu-id="ee801-475">\*/CLIENTSIDEASSETS</span><span class="sxs-lookup"><span data-stu-id="ee801-475">\*/CLIENTSIDEASSETS</span></span>

<span data-ttu-id="ee801-476">Wenn der \*/clientsideassets-Ursprung fehlt, treten bei SharePoint-Framework-Lösungen Fehler auf, und es werden keine Warnungen oder Fehlermeldungen generiert.</span><span class="sxs-lookup"><span data-stu-id="ee801-476">If the \*/clientsideassets origin is missing, SharePoint Framework solutions will fail, and no warning or error messages are generated.</span></span> <span data-ttu-id="ee801-477">Dieser Ursprung fehlt möglicherweise, weil das CDN aktiviert wurde, wobei der Parameter _-NoDefaultOrigins_ auf **$true**festgelegt ist, oder weil der Ursprung manuell gelöscht wurde.</span><span class="sxs-lookup"><span data-stu-id="ee801-477">This origin may be missing either because the CDN was enabled with the _-NoDefaultOrigins_ parameter set to **$true**, or because the origin was manually deleted.</span></span>

<span data-ttu-id="ee801-478">Sie können überprüfen, ob der \*/CLIENTSIDEASSETS-Ursprung mit dem folgenden PowerShell-Befehl vorhanden ist:</span><span class="sxs-lookup"><span data-stu-id="ee801-478">You can check to see if the \*/CLIENTSIDEASSETS origin is present with the following PowerShell command:</span></span>

``` powershell
Get-SPOTenantCdnOrigin -CdnType Public -OriginUrl */CLIENTSIDEASSETS
```

<span data-ttu-id="ee801-479">Oder Sie können mit der Office 365 CLI überprüfen:</span><span class="sxs-lookup"><span data-stu-id="ee801-479">Or you can check with the Office 365 CLI:</span></span>

``` powershell
spo cdn origin list
```

<span data-ttu-id="ee801-480">So fügen Sie den Ursprung in PowerShell hinzu:</span><span class="sxs-lookup"><span data-stu-id="ee801-480">To add the origin in PowerShell:</span></span>

``` powershell
Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */CLIENTSIDEASSETS
```

<span data-ttu-id="ee801-481">So fügen Sie den Ursprung in der Office 365 CLI hinzu:</span><span class="sxs-lookup"><span data-stu-id="ee801-481">To add the origin in the Office 365 CLI:</span></span>

``` powershell
spo cdn origin add --origin */CLIENTSIDEASSETS
```

### <a name="what-powershell-modules-and-cli-shells-do-i-need-to-work-with-the-office-365-cdn"></a><span data-ttu-id="ee801-482">Welche PowerShell-Module und CLI-Shells muss ich für das Office 365 CDN verwenden?</span><span class="sxs-lookup"><span data-stu-id="ee801-482">What PowerShell modules and CLI shells do I need to work with the Office 365 CDN?</span></span>

<span data-ttu-id="ee801-483">Sie können mit dem Office 365 CDN entweder mit dem PowerShell-Modul der **SharePoint Online-Verwaltungsshell** oder mit der **Office 365 CLI**arbeiten.</span><span class="sxs-lookup"><span data-stu-id="ee801-483">You can choose to work with the Office 365 CDN using either the **SharePoint Online Management Shell** PowerShell module or the **Office 365 CLI**.</span></span>

- [<span data-ttu-id="ee801-484">Erste Schritte mit der SharePoint Online-Verwaltungsshell</span><span class="sxs-lookup"><span data-stu-id="ee801-484">Getting started with SharePoint Online Management Shell</span></span>](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)
- [<span data-ttu-id="ee801-485">Installieren von Office 365 CLI</span><span class="sxs-lookup"><span data-stu-id="ee801-485">Installing the Office 365 CLI</span></span>](https://pnp.github.io/office365-cli/user-guide/installing-cli/)

## <a name="see-also"></a><span data-ttu-id="ee801-486">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="ee801-486">See also</span></span>

[<span data-ttu-id="ee801-487">Netzwerke für die Inhaltsübermittlung</span><span class="sxs-lookup"><span data-stu-id="ee801-487">Content Delivery Networks</span></span>](https://aka.ms/o365cdns)

[<span data-ttu-id="ee801-488">Netzwerkplanung und Leistungsoptimierung für Office 365</span><span class="sxs-lookup"><span data-stu-id="ee801-488">Network planning and performance tuning for Office 365</span></span>](https://aka.ms/tune)

