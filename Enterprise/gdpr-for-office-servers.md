---
title: DSGVO für Office-Server
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Priority
description: Erfahren Sie, wie Sie mit DSGVO-Anforderungen auf lokalen Office-Servern umgehen.
ms.openlocfilehash: 598d4b0c3f4b7d4281383111f0891759f81d483f
ms.sourcegitcommit: 53a57b0617b5bb22beea766e515873d14b3a4783
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2018
ms.locfileid: "19183594"
---
# <a name="gdpr-for-office-on-premises-servers"></a><span data-ttu-id="0bff0-103">DSGVO für lokale Office-Server</span><span class="sxs-lookup"><span data-stu-id="0bff0-103">GDPR for Office on-premises Servers</span></span>

<span data-ttu-id="0bff0-p101">Im Rahmen der Datenschutz-Grundverordnung (DSGVO) werden Anforderungen für Unternehmen zum Schutz personenbezogener Daten und zur angemessenen Reaktion auf Datensubjektanforderungen eingeführt. Diese Artikelreihe bietet empfohlene Ansätze für lokale Workloads:</span><span class="sxs-lookup"><span data-stu-id="0bff0-p101">The General Data Protection Regulation (GDPR) introduces requirements for organizations to protect personal data and respond appropriately to data subject requests. This series of articles provides recommended approaches for on-premises workloads:</span></span>

-   [<span data-ttu-id="0bff0-106">SharePoint Server</span><span class="sxs-lookup"><span data-stu-id="0bff0-106">SharePoint Server</span></span>](gdpr-for-sharepoint-server.md)

-   [<span data-ttu-id="0bff0-107">Exchange Server</span><span class="sxs-lookup"><span data-stu-id="0bff0-107">Exchange Server</span></span>](gdpr-for-exchange-server.md)

-   [<span data-ttu-id="0bff0-108">Skype for Business Server</span><span class="sxs-lookup"><span data-stu-id="0bff0-108">Skype for Business Server</span></span>](gdpr-for-skype-for-business-server.md)

-   [<span data-ttu-id="0bff0-109">Project Server</span><span class="sxs-lookup"><span data-stu-id="0bff0-109">Project Server</span></span>](gdpr-for-project-server.md)

-   [<span data-ttu-id="0bff0-110">Office Web Apps Server und Office Online Server</span><span class="sxs-lookup"><span data-stu-id="0bff0-110">Office Web Apps Server and Office Online Server</span></span>](gdpr-for-office-online-server.md)

-   [<span data-ttu-id="0bff0-111">Lokale Dateifreigaben</span><span class="sxs-lookup"><span data-stu-id="0bff0-111">On-premises file shares</span></span>](gdpr-for-on-premises-file-shares.md)

<span data-ttu-id="0bff0-112">Weitere Informationen zu der DSGVO und dazu, wie Microsoft Ihnen helfen kann, finden Sie im [Microsoft Trust Center](https://www.microsoft.com/de-DE/TrustCenter/Privacy/gdpr/default.aspx).</span><span class="sxs-lookup"><span data-stu-id="0bff0-112">For more information about the GDPR and how Microsoft can help you, see the [Microsoft Trust Center](https://www.microsoft.com/de-DE/TrustCenter/Privacy/gdpr/default.aspx).</span></span>

<span data-ttu-id="0bff0-p102">Vor der Arbeit mit lokalen Daten wenden Sie sich an die Teams Ihrer Rechts- und Compliance-Abteilung, um Hilfestellung und Informationen zu vorhandenen Klassifizierungsschemata und Ansätzen für die Arbeit mit personenbezogenen Daten zu erhalten. Microsoft bietet Empfehlungen für die Entwicklung und Erweiterung von Klassifizierungsschemata im DSGVO-bezogenen Data Discovery Toolkit von Microsoft unter [ http://aka.ms/gdprpartners ](<http://aka.ms/gdprpartners>). In diesem Toolkit werden auch Vorgehensweisen beschrieben, mit denen Sie lokale Daten in die Cloud verschieben können, wo Sie bei Bedarf komplexere Daten-Governance-Funktionen verwenden können. In den Artikeln in diesem Abschnitt werden Empfehlungen für Daten gegeben, die lokal gespeichert bleiben sollen.</span><span class="sxs-lookup"><span data-stu-id="0bff0-p102">Before doing any work with on-premises data, consult with your legal and compliance teams to seek guidance and to learn about existing classification schemas and approaches to working with personal data. Microsoft provides recommendations for developing and extending classifications schemas in the Microsoft GDPR Data Discovery Toolkit at [http://aka.ms/gdprpartners](<http://aka.ms/gdprpartners>). This toolkit also describes approaches for moving on-premises data to the cloud where you can use more sophisticated data governance capabilities, if this is desired. The articles in this section provide recommendations for data that is intended to remain on premises.</span></span>

<span data-ttu-id="0bff0-p103">In der folgenden Abbildung werden empfohlene Funktionen aufgeführt, die in jedem dieser Workloads zum Ermitteln, Klassifizieren, Schützen und Überwachen personenbezogener Daten verwendet werden können. Weitere Informationen finden Sie in den Artikeln in diesem Abschnitt.</span><span class="sxs-lookup"><span data-stu-id="0bff0-p103">The following illustration lists recommended capabilities to use across each of these workloads to discover, classify, protect, and monitor personal data. See the articles in this section for more information.</span></span>

![](media/gdpr-for-office-servers_image1.png)

## <a name="illustration-description"></a><span data-ttu-id="0bff0-119">Beschreibung der Abbildung</span><span class="sxs-lookup"><span data-stu-id="0bff0-119">Illustration description</span></span>

<span data-ttu-id="0bff0-120">Für Zwecke der Barrierefreiheit enthält die folgende Tabelle die gleichen Beispiele wie die Abbildung.</span><span class="sxs-lookup"><span data-stu-id="0bff0-120">For accessibility, the following table provides the same examples in the illustration.</span></span>

|             |<span data-ttu-id="0bff0-121">Windows Server-Dateifreigaben</span><span class="sxs-lookup"><span data-stu-id="0bff0-121">Windows Server file shares</span></span>|<span data-ttu-id="0bff0-122">SharePoint Server</span><span class="sxs-lookup"><span data-stu-id="0bff0-122">SharePoint Server</span></span>|<span data-ttu-id="0bff0-123">Exchange Server</span><span class="sxs-lookup"><span data-stu-id="0bff0-123">Exchange Server</span></span>|<span data-ttu-id="0bff0-124">Skype for Business</span><span class="sxs-lookup"><span data-stu-id="0bff0-124">Skype for Business</span></span>|<span data-ttu-id="0bff0-125">Project Server</span><span class="sxs-lookup"><span data-stu-id="0bff0-125">Project Server</span></span>|
|:------------|:-------------------------|:----------------|:--------------|:-----------------|:-------------|
|<span data-ttu-id="0bff0-126">Ermitteln</span><span class="sxs-lookup"><span data-stu-id="0bff0-126">discover
</span></span>|<span data-ttu-id="0bff0-127">Azure Information Protection-Scanner\*</span><span class="sxs-lookup"><span data-stu-id="0bff0-127">Azure Information Protection</span></span>|<span data-ttu-id="0bff0-128">Suchcenter oder eDiscovery (nachdem Daten klassifiziert wurden); Azure Information Protection-Scanner\*</span><span class="sxs-lookup"><span data-stu-id="0bff0-128">Search Center or eDiscovery (after data is classified); Azure Information Protection scanner\*</span></span>|<span data-ttu-id="0bff0-129">Exchange-eDiscovery-Portal</span><span class="sxs-lookup"><span data-stu-id="0bff0-129">Exchange eDiscovery Portal</span></span>|<span data-ttu-id="0bff0-130">Exchange-eDiscovery-Portal</span><span class="sxs-lookup"><span data-stu-id="0bff0-130">Exchange eDiscovery portal</span></span>|<span data-ttu-id="0bff0-131">SQL-Skripts für Ermittlung und Export</span><span class="sxs-lookup"><span data-stu-id="0bff0-131">SQL scripts for discovery and exporting</span></span>|
|<span data-ttu-id="0bff0-132">Klassifizieren</span><span class="sxs-lookup"><span data-stu-id="0bff0-132">Classify</span></span>|<span data-ttu-id="0bff0-133">Azure Information Protection-Scanner\*; Typen vertraulicher Informationen in Office 365</span><span class="sxs-lookup"><span data-stu-id="0bff0-133">Azure Information Protection scanner\*; Office 365 sensitive information types</span></span>|<span data-ttu-id="0bff0-134">Azure Information Protection-Scanner\*; Typen vertraulicher Informationen in Office 365</span><span class="sxs-lookup"><span data-stu-id="0bff0-134">Azure Information Protection scanner\*; Office 365 sensitive information types</span></span>|<span data-ttu-id="0bff0-135">Aufbewahrungstags und Aufbewahrungsrichtlinien in Exchange</span><span class="sxs-lookup"><span data-stu-id="0bff0-135">Exchange retention tags and retention policies</span></span>|<span data-ttu-id="0bff0-136">Aufbewahrungstags und Aufbewahrungsrichtlinien in Exchange</span><span class="sxs-lookup"><span data-stu-id="0bff0-136">Exchange retention tags and retention policies</span></span>||
|<span data-ttu-id="0bff0-137">Schützen</span><span class="sxs-lookup"><span data-stu-id="0bff0-137">protect</span></span>||<span data-ttu-id="0bff0-138">Regeln zur Verhinderung von Datenverlust für Exchange Server; Berechtigungen, IRM-Schutz für Bibliotheken</span><span class="sxs-lookup"><span data-stu-id="0bff0-138">Exchange Server data loss prevention rules; Permissions, IRM-protection for libraries</span></span>|<span data-ttu-id="0bff0-139">Regeln zur Verhinderung von Datenverlust für Exchange Server; IRM-Integration in Exchange Server</span><span class="sxs-lookup"><span data-stu-id="0bff0-139">Exchange Server data loss prevention rules; IRM integration with Exchange Server</span></span>|||
|<span data-ttu-id="0bff0-140">Überwachen</span><span class="sxs-lookup"><span data-stu-id="0bff0-140">Monitor</span></span>|<span data-ttu-id="0bff0-141">Protokolle in SIEM-Tools integrieren</span><span class="sxs-lookup"><span data-stu-id="0bff0-141">Integrate logs with SIEM tools</span></span>|<span data-ttu-id="0bff0-142">Protokolle in SIEM-Tools integrieren</span><span class="sxs-lookup"><span data-stu-id="0bff0-142">Integrate logs with SIEM tools</span></span>|<span data-ttu-id="0bff0-143">Protokolle in SIEM-Tools integrieren</span><span class="sxs-lookup"><span data-stu-id="0bff0-143">Integrate logs with SIEM tools</span></span>|<span data-ttu-id="0bff0-144">Protokolle in SIEM-Tools integrieren</span><span class="sxs-lookup"><span data-stu-id="0bff0-144">Integrate logs with SIEM tools</span></span>|<span data-ttu-id="0bff0-145">Protokolle in SIEM-Tools integrieren</span><span class="sxs-lookup"><span data-stu-id="0bff0-145">Integrate logs with SIEM tools</span></span>|

<span data-ttu-id="0bff0-p104">\*Durch Schutz wird die Datei verschlüsselt. Folglich kann SharePoint Server die Typen vertraulicher Informationen in diesen Dateien nicht finden.</span><span class="sxs-lookup"><span data-stu-id="0bff0-p104">\*Note that protection encrypts the file. Consequently, SharePoint Server can’t find the sensitive information types in protected files.</span></span>
