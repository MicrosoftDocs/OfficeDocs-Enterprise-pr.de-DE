---
title: Microsoft-Sicherheitsleitfaden für politische Kampagnen, gemeinnützigen Organisationen und andere agile Organisationen
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.service: o365-solutions
localization_priority: Priority
ms.custom: Strat_O365_Enterprise
ms.assetid: 10d1004b-42b6-4e2b-aaa2-18ddd9118f64
description: 'Zusammenfassung: Planungs- und Implementierungsleitfaden für sich schnell wandelnde Organisationen mit einem erhöhten Bedrohungsprofil.'
ms.openlocfilehash: 80ffac68dab2f89efa491be657dc89b8f1f64ade
ms.sourcegitcommit: 565a6275c719be61636bc43d0f8c000b440992bc
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/24/2018
ms.locfileid: "19434952"
---
# <a name="microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-organizations"></a><span data-ttu-id="40893-103">Microsoft-Sicherheitsleitfaden für politische Kampagnen, gemeinnützigen Organisationen und andere agile Organisationen</span><span class="sxs-lookup"><span data-stu-id="40893-103">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>

 <span data-ttu-id="40893-104">**Zusammenfassung:** Planungs- und Implementierungsleitfaden für sich schnell wandelnde Organisationen mit einem erhöhten Bedrohungsprofil.</span><span class="sxs-lookup"><span data-stu-id="40893-104">**Summary:** Planning and implementation guidance for fast-moving organizations that have an increased threat profile.</span></span>
  
<span data-ttu-id="40893-p101">Wenn Ihre Organisation nach Agile-Prinzipien agiert, Sie ein kleines IT-Team haben und Ihr Bedrohungsprofil höher ist als der Durchschnitt, ist dieser Leitfaden für Sie genau richtig. Diese Lösung veranschaulicht, wie Sie schnell eine Umgebung mit grundlegenden Clouddiensten erstellen können, die von Anfang an sichere Kontrollmechanismen umfasst. Dieser Leitfaden umfasst bindende Sicherheitsempfehlungen zum Schutz von Daten, Identitäten, E-Mail und Zugriff über mobile Geräte.</span><span class="sxs-lookup"><span data-stu-id="40893-p101">If your organization is agile, you have a small IT team, and your threat profile is higher than average, this guidance is designed for you. This solution demonstrates how to quickly build an environment with essential cloud services that include secure controls from the start. This guidance includes prescriptive security recommendations for protecting data, identities, email, and access from mobile devices.</span></span>
  
## <a name="security-solution-guidance"></a><span data-ttu-id="40893-108">Anleitungen für Sicherheitslösungen</span><span class="sxs-lookup"><span data-stu-id="40893-108">Security solution guidance</span></span>

<span data-ttu-id="40893-p102">Diese Anleitung beschreibt, wie eine sichere Cloudumgebung implementiert wird. Die Anleitung für die Lösung kann von jeder Organisation verwendet werden. Sie bietet zusätzliche Hilfe für agile Organisationen mit dem BYOD-Zugriff und Gastkonten. Sie können diesen Leitfaden als Startpunkt für den Entwurf Ihrer eigenen Umgebung verwenden. Wir freuen uns über Ihr Feedback unter [CloudAdopt@microsoft.com](mailto:CloudAdopt@microsoft.com).</span><span class="sxs-lookup"><span data-stu-id="40893-p102">This guidance describes how to implement a secure cloud environment. The solution guidance can be used by any organization. It includes extra help for agile organizations with BYOD access and guest accounts. You can use this guidance as a starting-point for designing your own environment. We welcome your feedback at [CloudAdopt@microsoft.com](mailto:CloudAdopt@microsoft.com).</span></span> 
  
|||
|:-----|:-----|
|<span data-ttu-id="40893-114">**Element**</span><span class="sxs-lookup"><span data-stu-id="40893-114">**Item**</span></span> <br/> |<span data-ttu-id="40893-115">**Beschreibung**</span><span class="sxs-lookup"><span data-stu-id="40893-115">**Description**</span></span> <br/> |
|<span data-ttu-id="40893-116">**Microsoft-Sicherheitsanleitungen von Microsoft für politische Kampagnen**</span><span class="sxs-lookup"><span data-stu-id="40893-116">**Microsoft Security Guidance for Political Campaigns**</span></span> <br/> <span data-ttu-id="40893-117">[![Miniaturansicht für Miniposter festgelegt.](images/d370ce28-ca40-4930-9a2c-907312aa06c8.png)          ](http://download.microsoft.com/download/B/4/D/B4D520C3-4D0C-4B4D-BFB9-09F0651C2775/MSFT_Cloud_architecture_security%20for%20political%20campaigns.pdf)</span><span class="sxs-lookup"><span data-stu-id="40893-117">[![Thumb nail for mini poster set.](images/d370ce28-ca40-4930-9a2c-907312aa06c8.png)          ](http://download.microsoft.com/download/B/4/D/B4D520C3-4D0C-4B4D-BFB9-09F0651C2775/MSFT_Cloud_architecture_security%20for%20political%20campaigns.pdf)</span></span> <br/> <span data-ttu-id="40893-118">[PDF](http://download.microsoft.com/download/B/4/D/B4D520C3-4D0C-4B4D-BFB9-09F0651C2775/MSFT_Cloud_architecture_security%20for%20political%20campaigns.pdf)  \| [Visio](http://download.microsoft.com/download/B/4/D/B4D520C3-4D0C-4B4D-BFB9-09F0651C2775/MSFT_Cloud_architecture_security%20for%20political%20campaigns.vsdx)</span><span class="sxs-lookup"><span data-stu-id="40893-118">[PDF](http://download.microsoft.com/download/B/4/D/B4D520C3-4D0C-4B4D-BFB9-09F0651C2775/MSFT_Cloud_architecture_security%20for%20political%20campaigns.pdf)  \| [Visio](http://download.microsoft.com/download/B/4/D/B4D520C3-4D0C-4B4D-BFB9-09F0651C2775/MSFT_Cloud_architecture_security%20for%20political%20campaigns.vsdx)</span></span> <br/> |<span data-ttu-id="40893-p103">Dieser Leitfaden verwendet eine Organisation für politische Kampagnen als Beispiel. Verwenden Sie diesen Leitfaden als Grundlage für eine beliebige Umgebung.</span><span class="sxs-lookup"><span data-stu-id="40893-p103">This guidance uses a political campaign organization as an example. Use this guidance as a starting point for any environment.</span></span>  <br/> |
|<span data-ttu-id="40893-121">**Sicherheitsanleitungen von Microsoft für gemeinnützige Organisationen**</span><span class="sxs-lookup"><span data-stu-id="40893-121">**Microsoft Security Guidance for Nonprofits**</span></span> <br/> <span data-ttu-id="40893-122">[![Miniaturbild für eine herunterladbare Datei](images/e4784889-1c69-4067-9a8f-31d31d1eceea.png)          ](http://download.microsoft.com/download/9/4/3/94389612-C679-4061-8DF2-D9A15D72B65F/Microsoft_Cloud%20Architecture_Security%20for%20Nonprofits.pdf)</span><span class="sxs-lookup"><span data-stu-id="40893-122">[![Thumnail image for downloadable file](images/e4784889-1c69-4067-9a8f-31d31d1eceea.png)          ](http://download.microsoft.com/download/9/4/3/94389612-C679-4061-8DF2-D9A15D72B65F/Microsoft_Cloud%20Architecture_Security%20for%20Nonprofits.pdf)</span></span> <br/> <span data-ttu-id="40893-123">[PDF](http://download.microsoft.com/download/9/4/3/94389612-C679-4061-8DF2-D9A15D72B65F/Microsoft_Cloud%20Architecture_Security%20for%20Nonprofits.pdf)  \| [Visio](http://download.microsoft.com/download/9/4/3/94389612-C679-4061-8DF2-D9A15D72B65F/Microsoft_Cloud%20Architecture_Security%20for%20Nonprofits.vsdx)</span><span class="sxs-lookup"><span data-stu-id="40893-123">[PDF](http://download.microsoft.com/download/9/4/3/94389612-C679-4061-8DF2-D9A15D72B65F/Microsoft_Cloud%20Architecture_Security%20for%20Nonprofits.pdf)  \| [Visio](http://download.microsoft.com/download/9/4/3/94389612-C679-4061-8DF2-D9A15D72B65F/Microsoft_Cloud%20Architecture_Security%20for%20Nonprofits.vsdx)</span></span> <br/> |<span data-ttu-id="40893-p104">Dieser Leitfaden wurde für gemeinnützige Organisationen geringfügig überarbeitet. Er verweist beispielsweise auf Office 365-Pläne für gemeinnützige Organisation. Die technische Anleitung ist identisch wie im Leitfaden für politische Kampagnen.</span><span class="sxs-lookup"><span data-stu-id="40893-p104">This guide is slightly revised for nonprofit organizations. For example, it references Office 365 Nonprofit plans. The technical guidance is the same as the political campaign solution guide.</span></span>  <br/> |
   
## <a name="test-lab-guides"></a><span data-ttu-id="40893-127">Testumgebungsanleitungen</span><span class="sxs-lookup"><span data-stu-id="40893-127">Test Lab Guides</span></span>

<span data-ttu-id="40893-128">Um eine Entwicklungs-/Testumgebung für diese Lösung zu erstellen, verwenden Sie die folgenden Testumgebungsanleitungen:</span><span class="sxs-lookup"><span data-stu-id="40893-128">To create a dev/test environment for this solution, use the following test lab guides:</span></span> 
  
- [<span data-ttu-id="40893-129">Konfigurieren von Gruppen und Benutzern für eine politische Kampagne in einer Entwicklungs-/Testumgebung</span><span class="sxs-lookup"><span data-stu-id="40893-129">Configure groups and users for a political campaign dev/test environment</span></span>](configure-groups-and-users-for-a-political-campaign-dev-test-environment.md)
    
     <span data-ttu-id="40893-130">Erstellen Sie Testabonnements für Office 365 und EMS, und erstellen Sie Gruppen und Benutzer für eine repräsentative politische Kampagne.</span><span class="sxs-lookup"><span data-stu-id="40893-130">Create trial subscriptions for Office 365 and EMS and then create groups and users for a representative political campaign.</span></span>
    
- [<span data-ttu-id="40893-131">Erstellen von Teamwebsites in einer Entwicklungs-/Testumgebung für eine politische Kampagne</span><span class="sxs-lookup"><span data-stu-id="40893-131">Create team sites in a political campaign dev/test environment</span></span>](create-team-sites-in-a-political-campaign-dev-test-environment.md)
    
    <span data-ttu-id="40893-132">Erstellen Sie vier SharePoint Online-Teamwebsites mit den Sicherheitsebenen „Intern“, „Privat“, „Sensibel“ und „Streng vertraulich“.</span><span class="sxs-lookup"><span data-stu-id="40893-132">Create four SharePoint Online team sites with Internal, Private, Sensitive, and Highly Confidential levels of security.</span></span>
    
<span data-ttu-id="40893-133">Weitere Sicherheitsfunktionen für die Vorführung oder Machbarkeitsstudie finden Sie unter [Office 365-Testumgebungsanleitungen](http://aka.ms/o365tlgs).</span><span class="sxs-lookup"><span data-stu-id="40893-133">For additional security features for demonstration or proof of concept, see [Office 365 Test Lab Guides](http://aka.ms/o365tlgs).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="40893-134">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="40893-134">See Also</span></span>

[<span data-ttu-id="40893-135">Sicherheitslösungen</span><span class="sxs-lookup"><span data-stu-id="40893-135">Security solutions</span></span>](security-solutions.md)
  
[<span data-ttu-id="40893-136">Testumgebungsanleitungen (TLGs) zur Cloudakzeptanz</span><span class="sxs-lookup"><span data-stu-id="40893-136">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="40893-137">Ressourcen zur Cloud-IT-Architektur von Microsoft</span><span class="sxs-lookup"><span data-stu-id="40893-137">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)



