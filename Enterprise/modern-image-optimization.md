---
title: Optimieren von Bilder in modernen SharePoint Online-Websites
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 9/18/2019
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- SPO_Content
ms.custom: Adm_O365
ms.reviewer: sstewart
search.appverid:
- MET150
description: Erfahren Sie, wie Sie Bilder in modernen SharePoint Online-Websites optimieren.
ms.openlocfilehash: 68e2f79e1f768cfc93feb4f26f8b2fbeca5d6b83
ms.sourcegitcommit: a9804062071939b7b7e60da5b69f484ce1d34ff8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/04/2019
ms.locfileid: "39814223"
---
# <a name="optimize-images-in-sharepoint-online-modern-site-pages"></a><span data-ttu-id="b62bc-103">Optimieren von Bilder in modernen SharePoint Online-Websites</span><span class="sxs-lookup"><span data-stu-id="b62bc-103">Optimize images in SharePoint Online modern site pages</span></span>

<span data-ttu-id="b62bc-104">In diesem Artikel erfahren Sie, wie Sie Bilder in modernen SharePoint Online-Websites optimieren.</span><span class="sxs-lookup"><span data-stu-id="b62bc-104">This article will help you understand how to optimize images in SharePoint Online modern site pages.</span></span>

<span data-ttu-id="b62bc-105">Informationen zum Optimieren von Bildern in klassischen Veröffentlichungswebsites finden Sie unter [Bildoptimierung für SharePoint Online](image-optimization-for-sharepoint-online.md).</span><span class="sxs-lookup"><span data-stu-id="b62bc-105">For information about optimizing images in classic publishing sites, see [Image optimization for SharePoint Online](image-optimization-for-sharepoint-online.md)..</span></span>

>[!NOTE]
><span data-ttu-id="b62bc-106">Weitere Informationen zur Leistung in modernen SharePoint Online-Portalen finden Sie unter [Leistung in der modernen SharePoint-Umgebung](https://docs.microsoft.com/sharepoint/modern-experience-performance).</span><span class="sxs-lookup"><span data-stu-id="b62bc-106">For more information about performance in SharePoint Online modern portals, see [Performance in the modern SharePoint experience](https://docs.microsoft.com/sharepoint/modern-experience-performance).</span></span>

## <a name="use-the-page-diagnostics-for-sharepoint-tool-to-analyze-image-optimization"></a><span data-ttu-id="b62bc-107">Verwenden des Tools "Seitendiagnose für SharePoint" zum Analysieren der Bildoptimierung</span><span class="sxs-lookup"><span data-stu-id="b62bc-107">Use the Page Diagnostics for SharePoint tool to analyze image optimization</span></span>

<span data-ttu-id="b62bc-108">Das **Tool "Seitendiagnose für SharePoint"** ist eine Browsererweiterung für Chrome und [Microsoft Edge ab Version 77](https://www.microsoftedgeinsider.com/download?form=MI13E8&OCID=MI13E8), mit der Sie Seiten in modernen und klassischen SharePoint-Veröffentlichungswebsites analysieren können.</span><span class="sxs-lookup"><span data-stu-id="b62bc-108">The **Page Diagnostics for SharePoint tool** is a browser extension for Chrome and [Microsoft Edge version 77 or later](https://www.microsoftedgeinsider.com/download?form=MI13E8&OCID=MI13E8) you can use to analyze SharePoint both modern and classic publishing site pages.</span></span> <span data-ttu-id="b62bc-109">Das Tool stellt für jede analysierte Seite einen Bericht bereit, in dem die Leistung der Seite anhand einer definierten Gruppe von Leistungskriterien dargestellt wird.</span><span class="sxs-lookup"><span data-stu-id="b62bc-109">The tool provides a report for each analyzed page showing how the page performs against a defined set of performance criteria.</span></span> <span data-ttu-id="b62bc-110">Wenn Sie das Tool "Seitendiagnose für SharePoint" installieren und mehr darüber erfahren möchten, besuchen Sie [Verwenden des Seitendiagnose-Tools für SharePoint Online](page-diagnostics-for-spo.md).</span><span class="sxs-lookup"><span data-stu-id="b62bc-110">To install and learn about the Page Diagnostics for SharePoint tool, visit [Use the Page Diagnostics tool for SharePoint Online](page-diagnostics-for-spo.md).</span></span>

<span data-ttu-id="b62bc-111">Wenn Sie eine moderne SharePoint-Website mit dem Tool "Seitendiagnose für SharePoint" analysieren, werden Informationen über große Bilder im Bereich _Diagnosetests_ angezeigt.</span><span class="sxs-lookup"><span data-stu-id="b62bc-111">When you analyze a SharePoint modern site with the Page Diagnostics for SharePoint tool, you can see information about large images in the _Diagnostic tests_ pane.</span></span>

<span data-ttu-id="b62bc-112">Mögliche Ergebnisse sind:</span><span class="sxs-lookup"><span data-stu-id="b62bc-112">Possible results include:</span></span>

- <span data-ttu-id="b62bc-113">**Handlungsbedarf** (rot): Die Seite enthält **mindestens ein** Bild mit einer Größe von über 300 KB.</span><span class="sxs-lookup"><span data-stu-id="b62bc-113">**Attention required** (red): The page contains **one or more** images over 300KB in size</span></span>
- <span data-ttu-id="b62bc-114">**Keine Aktion erforderlich** (grün): Die Seite enthält keine Bilder mit einer Größe von über 300 KB.</span><span class="sxs-lookup"><span data-stu-id="b62bc-114">**No action required** (green): The page contains no images over 300KB in size</span></span>

<span data-ttu-id="b62bc-115">Wenn das Ergebnis **Große Bilder erkannt** in den Ergebnissen im Abschnitt **Handlungsbedarf** angezeigt wird, können Sie darauf klicken, um weitere Details anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="b62bc-115">If the **Large images detected** result appears in the **Attention required** section of the results, you can click the result to see additional details.</span></span>

![Tool für die Seitendiagnose – Ergebnisse](media/modern-portal-optimization/pagediag-large-images.png)

## <a name="remediate-large-image-issues"></a><span data-ttu-id="b62bc-117">Beheben von Problemen mit großen Bildern</span><span class="sxs-lookup"><span data-stu-id="b62bc-117">Remediate large image issues</span></span>

<span data-ttu-id="b62bc-118">Wenn eine Seite Bilder mit einer Größe von über 300 KB enthält, wählen Sie das Ergebnis **Große Bilder erkannt** aus, um anzuzeigen, welche Bilder zu groß sind.</span><span class="sxs-lookup"><span data-stu-id="b62bc-118">If a page contains images over 300KB in size, select the **Large images detected** result to see which images are too large.</span></span> <span data-ttu-id="b62bc-119">Auf modernen SharePoint Online-Seiten erfolgt die Wiedergabe von Bildern, und die Bilder werden an die Größe des Browserfensters und die Auflösung des Clientmonitors angepasst.</span><span class="sxs-lookup"><span data-stu-id="b62bc-119">In modern SharePoint Online pages, renditions of images are automatically provided and sized depending on the size of the browser window and the resolution of the client monitor.</span></span> <span data-ttu-id="b62bc-120">Sie sollten Bilder immer für die Webverwendung optimieren, bevor Sie sie in SharePoint Online hochladen.</span><span class="sxs-lookup"><span data-stu-id="b62bc-120">You should always optimize images for web use prior to upload to SharePoint Online.</span></span> <span data-ttu-id="b62bc-121">Sehr große Bilder werden automatisch in Größe und Auflösung reduziert, was zu unerwarteten Ergebnissen bei der Wiedergabe führen kann.</span><span class="sxs-lookup"><span data-stu-id="b62bc-121">Very large images will be automatically reduced in size and resolution which can result in unexpected rendering characteristics.</span></span>

<span data-ttu-id="b62bc-122">Bevor Sie Seitenrevisionen zur Behebung von Leistungsproblemen durchführen, notieren Sie sich die Ladezeit der Seite in den Analyseergebnissen.</span><span class="sxs-lookup"><span data-stu-id="b62bc-122">Before you make page revisions to remediate performance issues, make a note of the page load time in the analysis results.</span></span> <span data-ttu-id="b62bc-123">Führen Sie das Tool nach Ihrer Revision erneut aus, um zu sehen, ob das neue Ergebnis innerhalb des Grenzwertes liegt, und überprüfen Sie die Ladezeit der neuen Seite, um festzustellen, ob eine Verbesserung vorliegt.</span><span class="sxs-lookup"><span data-stu-id="b62bc-123">Run the tool again after your revision to see if the new result is within the baseline standard, and check the new page load time to see if there was an improvement.</span></span>

![Ergebnisse der Seitenladezeiten](media/modern-portal-optimization/pagediag-page-load-time.png)

>[!NOTE]
><span data-ttu-id="b62bc-125">Die Seitenladezeit kann aufgrund einer Vielzahl von Faktoren wie Netzwerklast, Tageszeit und anderen vorübergehenden Schwierigkeiten variieren.</span><span class="sxs-lookup"><span data-stu-id="b62bc-125">Page load time can vary based on a variety of factors such as network load, time of day, and other transient conditions.</span></span> <span data-ttu-id="b62bc-126">Sie sollten die Seitenladezeit einige Male vor und nach der Durchführung von Änderungen testen, um einen Mittelwert zu berechnen.</span><span class="sxs-lookup"><span data-stu-id="b62bc-126">You should test page load time a few times before and after making changes to help you average the results.</span></span>

## <a name="related-topics"></a><span data-ttu-id="b62bc-127">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="b62bc-127">Related topics</span></span>

[<span data-ttu-id="b62bc-128">Optimieren der Leistung von SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="b62bc-128">Tune SharePoint Online performance</span></span>](tune-sharepoint-online-performance.md)

[<span data-ttu-id="b62bc-129">Optimieren der Leistung von Office 365</span><span class="sxs-lookup"><span data-stu-id="b62bc-129">Tune Office 365 performance</span></span>](tune-office-365-performance.md)

[<span data-ttu-id="b62bc-130">Leistung in der modernen SharePoint-Oberfläche</span><span class="sxs-lookup"><span data-stu-id="b62bc-130">Performance in the modern SharePoint experience</span></span>](https://docs.microsoft.com/sharepoint/modern-experience-performance)

[<span data-ttu-id="b62bc-131">Netzwerke für die Inhaltsübermittlung</span><span class="sxs-lookup"><span data-stu-id="b62bc-131">Content delivery networks</span></span>](content-delivery-networks.md)

[<span data-ttu-id="b62bc-132">Verwenden des Office 365 Content Delivery Network (CDN) mit SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="b62bc-132">Use the Office 365 Content Delivery Network (CDN) with SharePoint Online</span></span>](use-office-365-cdn-with-spo.md)
