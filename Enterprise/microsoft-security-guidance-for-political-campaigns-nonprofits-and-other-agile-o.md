---
title: "Microsoft-Sicherheitsleitfaden für politische Kampagnen, gemeinnützigen Organisationen und andere agile Organisationen"
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.custom: Strat_O365_Enterprise
ms.assetid: 10d1004b-42b6-4e2b-aaa2-18ddd9118f64
description: "Zusammenfassung: Planung und Implementierung Anleitung zum Verschieben von Fast Organisationen, die eine erhöhte Bedrohung Profil aufweisen."
ms.openlocfilehash: 15565c313c1aeef1273ae9398b045a07ddb9c443
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/09/2018
---
# <a name="microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-organizations"></a><span data-ttu-id="09632-103">Microsoft-Sicherheitsleitfaden für politische Kampagnen, gemeinnützigen Organisationen und andere agile Organisationen</span><span class="sxs-lookup"><span data-stu-id="09632-103">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>

 <span data-ttu-id="09632-104">**Zusammenfassung:** Planung und Implementierung Anleitung zum Verschieben von Fast Organisationen, die eine erhöhte Bedrohung Profil aufweisen.</span><span class="sxs-lookup"><span data-stu-id="09632-104">**Summary:** Planning and implementation guidance for fast-moving organizations that have an increased threat profile.</span></span>
  
<span data-ttu-id="09632-p101">Wenn Ihre Organisation nach Agile-Prinzipien agiert, Sie ein kleines IT-Team haben und Ihr Bedrohungsprofil höher ist als der Durchschnitt, ist dieser Leitfaden für Sie genau richtig. Diese Lösung veranschaulicht, wie Sie schnell eine Umgebung mit grundlegenden Clouddiensten erstellen können, die von Anfang an sichere Kontrollmechanismen umfasst. Dieser Leitfaden umfasst bindende Sicherheitsempfehlungen zum Schutz von Daten, Identitäten, E-Mail und Zugriff über mobile Geräte.</span><span class="sxs-lookup"><span data-stu-id="09632-p101">If your organization is agile, you have a small IT team, and your threat profile is higher than average, this guidance is designed for you. This solution demonstrates how to quickly build an environment with essential cloud services that include secure controls from the start. This guidance includes prescriptive security recommendations for protecting data, identities, email, and access from mobile devices.</span></span>
  
## <a name="security-solution-guidance"></a><span data-ttu-id="09632-108">Leitfaden für die Sicherheitslösung</span><span class="sxs-lookup"><span data-stu-id="09632-108">Security solution guidance</span></span>

<span data-ttu-id="09632-p102">Diese Anleitung wird beschrieben, wie eine sichere Cloudumgebung zu implementieren. Die ausgesprochen kann von einer Organisation verwendet werden. Sie enthält zusätzliche Hilfe für agile Organisationen mit BYOD Zugriff und Gast Konten. Sie können dieser Anleitung als einen Ausgangspunkt für das Entwerfen von Ihrer Umgebung verwenden. Wir freuen uns Ihr Feedback an [CloudAdopt@microsoft.com](mailto:CloudAdopt@microsoft.com).</span><span class="sxs-lookup"><span data-stu-id="09632-p102">This guidance describes how to implement a secure cloud environment. The solution guidance can be used by any organization. It includes extra help for agile organizations with BYOD access and guest accounts. You can use this guidance as a starting-point for designing your own environment. We welcome your feedback at [CloudAdopt@microsoft.com](mailto:CloudAdopt@microsoft.com).</span></span> 
  
|||
|:-----|:-----|
|<span data-ttu-id="09632-114">**Element**</span><span class="sxs-lookup"><span data-stu-id="09632-114">**Item**</span></span> <br/> |<span data-ttu-id="09632-115">**Beschreibung**</span><span class="sxs-lookup"><span data-stu-id="09632-115">**Description**</span></span> <br/> |
|<span data-ttu-id="09632-116">**Microsoft Security Guidance for politischen Kampagnen**</span><span class="sxs-lookup"><span data-stu-id="09632-116">**Microsoft Security Guidance for Political Campaigns**</span></span> <br/> <span data-ttu-id="09632-117">[![Ziehpunkt eigenes Ende Mini Poster festgelegt.](images/d370ce28-ca40-4930-9a2c-907312aa06c8.png)          ](http://download.microsoft.com/download/B/4/D/B4D520C3-4D0C-4B4D-BFB9-09F0651C2775/MSFT_Cloud_architecture_security for political campaigns.pdf)</span><span class="sxs-lookup"><span data-stu-id="09632-117">[![Thumb nail for mini poster set.](images/d370ce28-ca40-4930-9a2c-907312aa06c8.png)          ](http://download.microsoft.com/download/B/4/D/B4D520C3-4D0C-4B4D-BFB9-09F0651C2775/MSFT_Cloud_architecture_security for political campaigns.pdf)</span></span> <br/> <span data-ttu-id="09632-118">[PDF-Datei](http://download.microsoft.com/download/B/4/D/B4D520C3-4D0C-4B4D-BFB9-09F0651C2775/MSFT_Cloud_architecture_security for political campaigns.pdf) \| [Visio](http://download.microsoft.com/download/B/4/D/B4D520C3-4D0C-4B4D-BFB9-09F0651C2775/MSFT_Cloud_architecture_security for political campaigns.vsdx)  </span><span class="sxs-lookup"><span data-stu-id="09632-118">[PDF](http://download.microsoft.com/download/B/4/D/B4D520C3-4D0C-4B4D-BFB9-09F0651C2775/MSFT_Cloud_architecture_security for political campaigns.pdf)  \| [Visio](http://download.microsoft.com/download/B/4/D/B4D520C3-4D0C-4B4D-BFB9-09F0651C2775/MSFT_Cloud_architecture_security for political campaigns.vsdx)</span></span> <br/> |<span data-ttu-id="09632-p103">Dieser Leitfaden verwendet eine Organisation für politische Kampagnen als Beispiel. Verwenden Sie diesen Leitfaden als Grundlage für eine beliebige Umgebung. </span><span class="sxs-lookup"><span data-stu-id="09632-p103">This guidance uses a political campaign organization as an example. Use this guidance as a starting point for any environment.</span></span>  <br/> |
|<span data-ttu-id="09632-121">**Microsoft Security Guidance for gemeinnützige Organisationen**</span><span class="sxs-lookup"><span data-stu-id="09632-121">**Microsoft Security Guidance for Nonprofits**</span></span> <br/> <span data-ttu-id="09632-122">[![Miniaturbild für die Datei zum Herunterladen](images/e4784889-1c69-4067-9a8f-31d31d1eceea.png)          ](http://download.microsoft.com/download/9/4/3/94389612-C679-4061-8DF2-D9A15D72B65F/Microsoft_Cloud Architecture_Security for Nonprofits.pdf)</span><span class="sxs-lookup"><span data-stu-id="09632-122">[![Thumnail image for downloadable file](images/e4784889-1c69-4067-9a8f-31d31d1eceea.png)          ](http://download.microsoft.com/download/9/4/3/94389612-C679-4061-8DF2-D9A15D72B65F/Microsoft_Cloud Architecture_Security for Nonprofits.pdf)</span></span> <br/> <span data-ttu-id="09632-123">[PDF-Datei](http://download.microsoft.com/download/9/4/3/94389612-C679-4061-8DF2-D9A15D72B65F/Microsoft_Cloud Architecture_Security for Nonprofits.pdf) \| [Visio](http://download.microsoft.com/download/9/4/3/94389612-C679-4061-8DF2-D9A15D72B65F/Microsoft_Cloud Architecture_Security for Nonprofits.vsdx)  </span><span class="sxs-lookup"><span data-stu-id="09632-123">[PDF](http://download.microsoft.com/download/9/4/3/94389612-C679-4061-8DF2-D9A15D72B65F/Microsoft_Cloud Architecture_Security for Nonprofits.pdf)  \| [Visio](http://download.microsoft.com/download/9/4/3/94389612-C679-4061-8DF2-D9A15D72B65F/Microsoft_Cloud Architecture_Security for Nonprofits.vsdx)</span></span> <br/> |<span data-ttu-id="09632-p104">Dieser Leitfaden wurde für gemeinnützige Organisationen geringfügig überarbeitet. Er verweist beispielsweise auf Office 365-Pläne für gemeinnützige Organisation. Die technische Anleitung ist identisch wie im Leitfaden für politische Kampagnen.</span><span class="sxs-lookup"><span data-stu-id="09632-p104">This guide is slightly revised for nonprofit organizations. For example, it references Office 365 Nonprofit plans. The technical guidance is the same as the political campaign solution guide.</span></span>  <br/> |
   
## <a name="test-lab-guides"></a><span data-ttu-id="09632-127">Testumgebungsanleitungen</span><span class="sxs-lookup"><span data-stu-id="09632-127">Test Lab Guides</span></span>

<span data-ttu-id="09632-128">Um eine Entwicklungs-/Testumgebung für diese Lösung zu erstellen, verwenden Sie die folgenden Testumgebungsanleitungen:  </span><span class="sxs-lookup"><span data-stu-id="09632-128">To create a dev/test environment for this solution, use the following test lab guides:</span></span> 
  
- [<span data-ttu-id="09632-129">Konfigurieren von Gruppen und Benutzer für eine politischen Kampagne Test-/-Umgebung</span><span class="sxs-lookup"><span data-stu-id="09632-129">Configure groups and users for a political campaign dev/test environment</span></span>](configure-groups-and-users-for-a-political-campaign-dev-test-environment.md)
    
     <span data-ttu-id="09632-130"> Erstellen Sie Testabonnements für Office 365 und EMS, und erstellen Sie Gruppen und Benutzer für eine repräsentative politische Kampagne.</span><span class="sxs-lookup"><span data-stu-id="09632-130">Create trial subscriptions for Office 365 and EMS and then create groups and users for a representative political campaign.</span></span>
    
- [<span data-ttu-id="09632-131">Erstellen von Teamwebsites in einer politischen Kampagne Test-/-Umgebung</span><span class="sxs-lookup"><span data-stu-id="09632-131">Create team sites in a political campaign dev/test environment</span></span>](create-team-sites-in-a-political-campaign-dev-test-environment.md)
    
    <span data-ttu-id="09632-132">Erstellen Sie vier SharePoint Online-Teamwebsites mit den Sicherheitsebenen „Intern“, „Privat“, „Sensibel“ und „Streng vertraulich“.</span><span class="sxs-lookup"><span data-stu-id="09632-132">Create four SharePoint Online team sites with Internal, Private, Sensitive, and Highly Confidential levels of security.</span></span>
    
<span data-ttu-id="09632-133">Zusätzliche Sicherheitsfeatures für Demo oder Machbarkeitsstudie finden Sie unter [Office 365 Test Lab Guides](http://aka.ms/o365tlgs).</span><span class="sxs-lookup"><span data-stu-id="09632-133">For additional security features for demonstration or proof of concept, see [Office 365 Test Lab Guides](http://aka.ms/o365tlgs).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="09632-134">Weitere Artikel</span><span class="sxs-lookup"><span data-stu-id="09632-134">See Also</span></span>

[<span data-ttu-id="09632-135">Sicherheitslösungen</span><span class="sxs-lookup"><span data-stu-id="09632-135">Security solutions</span></span>](security-solutions.md)
  
[<span data-ttu-id="09632-136">Testumgebungsanleitungen (TLGs) zur Cloudakzeptanz</span><span class="sxs-lookup"><span data-stu-id="09632-136">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="09632-137">Ressourcen zur Cloud-IT-Architektur von Microsoft</span><span class="sxs-lookup"><span data-stu-id="09632-137">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)



