---
title: Automatisieren der Dateisammlung für eDiscovery
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- SPO_Content
f1.keywords:
- CSH
ms.custom: ''
ms.assetid: 8d751419-d81b-4eb7-a2e5-8b03ccbf670c
search.appverid:
- MET150
description: 'Zusammenfassung: Erfahren Sie, wie Sie die Dateisammlung von Benutzercomputern für eDiscovery automatisieren.'
ms.openlocfilehash: 83bd55ff786803cfcb3eec9430d72de30179d000
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "44997976"
---
# <a name="automate-file-collection-for-ediscovery"></a><span data-ttu-id="0f5da-103">Automatisieren der Dateisammlung für eDiscovery</span><span class="sxs-lookup"><span data-stu-id="0f5da-103">Automate file collection for eDiscovery</span></span>

<span data-ttu-id="0f5da-104">All companies face the potential of lawsuits or other types of legal action.</span><span class="sxs-lookup"><span data-stu-id="0f5da-104">All companies face the potential of lawsuits or other types of legal action.</span></span> <span data-ttu-id="0f5da-105">While legal departments work to reduce that exposure, litigation is a fact of business life.</span><span class="sxs-lookup"><span data-stu-id="0f5da-105">While legal departments work to reduce that exposure, litigation is a fact of business life.</span></span> <span data-ttu-id="0f5da-106">When a company faces legal action, they are required, through the process of legal discovery, to provide all relevant documentary materials to the court and to opposing counsel.</span><span class="sxs-lookup"><span data-stu-id="0f5da-106">When a company faces legal action, they are required, through the process of legal discovery, to provide all relevant documentary materials to the court and to opposing counsel.</span></span> 
  
<span data-ttu-id="0f5da-107">eDiscovery is the process by which companies inventory, search, identify, preserve, filter, and make available the relevant documentary materials that exist in electronic form.</span><span class="sxs-lookup"><span data-stu-id="0f5da-107">eDiscovery is the process by which companies inventory, search, identify, preserve, filter, and make available the relevant documentary materials that exist in electronic form.</span></span> <span data-ttu-id="0f5da-108">SharePoint 2013, Exchange Server 2013, Lync Server 2013, SharePoint Online, and Exchange Online can hold large amounts of documentary content.</span><span class="sxs-lookup"><span data-stu-id="0f5da-108">SharePoint 2013, Exchange Server 2013, Lync Server 2013, SharePoint Online, and Exchange Online can hold large amounts of documentary content.</span></span> <span data-ttu-id="0f5da-109">Depending on the version, these products may support eDiscovery and in place holds (Lync via Exchange Server), making it easier for the legal teams to index, identify, hold, and filter the most relevant content for a given case.</span><span class="sxs-lookup"><span data-stu-id="0f5da-109">Depending on the version, these products may support eDiscovery and in place holds (Lync via Exchange Server), making it easier for the legal teams to index, identify, hold, and filter the most relevant content for a given case.</span></span>
  
<span data-ttu-id="0f5da-110">Many documents are stored on users' (Custodians) local computers, not in a centralized location.</span><span class="sxs-lookup"><span data-stu-id="0f5da-110">Many documents are stored on users' (Custodians) local computers, not in a centralized location.</span></span> <span data-ttu-id="0f5da-111">This makes it essentially impossible for SharePoint 2013 to search, and if it can't be searched, it can't be included in eDiscovery.</span><span class="sxs-lookup"><span data-stu-id="0f5da-111">This makes it essentially impossible for SharePoint 2013 to search, and if it can't be searched, it can't be included in eDiscovery.</span></span> <span data-ttu-id="0f5da-112">This solution shows you how to use logon scripts, System Center Orchestrator 2012 R2 and Windows PowerShell for Exchange Server to automate the identification and collection of documentary materials from users' computers.</span><span class="sxs-lookup"><span data-stu-id="0f5da-112">This solution shows you how to use logon scripts, System Center Orchestrator 2012 R2 and Windows PowerShell for Exchange Server to automate the identification and collection of documentary materials from users' computers.</span></span>
  
## <a name="what-this-solution-does"></a><span data-ttu-id="0f5da-113">Funktionsweise dieser Lösung</span><span class="sxs-lookup"><span data-stu-id="0f5da-113">What this solution does</span></span>

<span data-ttu-id="0f5da-114">This solution uses a global security group, Group Policy, and a Windows PowerShell script to locate, inventory, and collect content and Outlook personal store (PST) files from users local computers to a hidden file share.</span><span class="sxs-lookup"><span data-stu-id="0f5da-114">This solution uses a global security group, Group Policy, and a Windows PowerShell script to locate, inventory, and collect content and Outlook personal store (PST) files from users local computers to a hidden file share.</span></span> <span data-ttu-id="0f5da-115">From there, the PST files can be imported into either Exchange Server 2013 or Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="0f5da-115">From there, the PST files can be imported into either Exchange Server 2013 or Exchange Online.</span></span> <span data-ttu-id="0f5da-116">All files are then moved using a System Center Orchestrator 2012 R2 runbook to another file share in Microsoft Azure for long-term storage and indexing by SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="0f5da-116">All files are then moved using a System Center Orchestrator 2012 R2 runbook to another file share in Microsoft Azure for long-term storage and indexing by SharePoint 2013.</span></span> <span data-ttu-id="0f5da-117">You then use eDiscovery centers in your on-premises SharePoint 2013 deployment or in SharePoint Online as you regularly would to perform eDiscovery.</span><span class="sxs-lookup"><span data-stu-id="0f5da-117">You then use eDiscovery centers in your on-premises SharePoint 2013 deployment or in SharePoint Online as you regularly would to perform eDiscovery.</span></span> 
  
> [!IMPORTANT]
> <span data-ttu-id="0f5da-118">This solution uses robocopy to copy files from custodian's computers to a centralized file share.</span><span class="sxs-lookup"><span data-stu-id="0f5da-118">This solution uses robocopy to copy files from custodian's computers to a centralized file share.</span></span> <span data-ttu-id="0f5da-119">Because robocopy does not copy files that are open or locked, any files, including PST files, that the custodian has open will not be collected.</span><span class="sxs-lookup"><span data-stu-id="0f5da-119">Because robocopy does not copy files that are open or locked, any files, including PST files, that the custodian has open will not be collected.</span></span> <span data-ttu-id="0f5da-120">You will have to collect them manually.</span><span class="sxs-lookup"><span data-stu-id="0f5da-120">You will have to collect them manually.</span></span> <span data-ttu-id="0f5da-121">This solution does provide you with a list that explicitly identifies the files it cannot copy and the full path to each file.</span><span class="sxs-lookup"><span data-stu-id="0f5da-121">This solution does provide you with a list that explicitly identifies the files it cannot copy and the full path to each file.</span></span> 
  
<span data-ttu-id="0f5da-122">Das folgende Diagramm führt Sie durch alle Schritte und Elemente der Lösung.</span><span class="sxs-lookup"><span data-stu-id="0f5da-122">The following diagram walks you through all the steps and elements of the solution.</span></span>
  
![Übersicht über die automatische Dateierfassungslösung](media/dbb447b5-c74c-4956-986c-10a1d047ac99.png)
  
|<span data-ttu-id="0f5da-124">\*\*\*\*Legende\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="0f5da-124">\*\*\*\*Legend\*\*\*\*</span></span>||
|:-----|:-----|
|![Magenta-Beschriftung 1](media/000026a3-2bf0-4678-b468-ccb5f81da6f1.png)|<span data-ttu-id="0f5da-126">Erstellen Sie ein Gruppenrichtlinienobjekt (Group Policy Object, GPO), und ordnen Sie es dem Sammlungsanmeldeskript zu.</span><span class="sxs-lookup"><span data-stu-id="0f5da-126">Create a Group Policy object (GPO), and associate it with the collection logon script.</span></span>  <br/> |
|![Magenta-Beschriftung 2](media/a31b11e2-3597-42a4-933e-b6af11ed6ef1.png)| <span data-ttu-id="0f5da-128">Konfigurieren Sie den GPO-Sicherheitsfilter, um das GPO nur auf die Gruppe der Verwalter anzuwenden.</span><span class="sxs-lookup"><span data-stu-id="0f5da-128">Configure the GPO security filter to apply the GPO only to the Custodians group.</span></span> <br/> |
|![Magenta-Beschriftung 3](media/3ced060c-daec-460d-a9b5-260a3dfcae36.png)|<span data-ttu-id="0f5da-130">Ein Verwalter meldet sich an, und das GPO wird ausgeführt und ruft das Sammlungsanmeldeskript auf.</span><span class="sxs-lookup"><span data-stu-id="0f5da-130">A Custodian logs on and the GPO runs, calling the collection logon script.</span></span>  <br/> |
|![Magenta-Beschriftung 4](media/6f269d84-2559-49e3-b18e-af6ac94d0419.png)|<span data-ttu-id="0f5da-132">Das Sammlungsanmeldeskript inventarisiert alle lokal verbundenen Laufwerke auf dem Computer des Verwalters, indem es nach den gewünschten Dateien sucht und ihren Speicherort aufzeichnet.</span><span class="sxs-lookup"><span data-stu-id="0f5da-132">The collection logon script inventories all locally attached drives on the Custodians computer, searching for the files you want, and recording their location.</span></span>  <br/> |
|![Magenta-Beschriftung 5](media/4bf8898c-44ad-4524-b983-70175804eb85.png)|<span data-ttu-id="0f5da-134">Das Sammlungsanmeldeskript kopiert die inventarisierten Dateien in eine verborgene Dateifreigabe auf dem Staging Server.</span><span class="sxs-lookup"><span data-stu-id="0f5da-134">The collection logon script copies the inventoried files to a hidden file share on the staging server.</span></span>  <br/> |
|![Magenta-Beschriftung 6](media/99589726-0c7e-406b-a276-44301a135768.png)| <span data-ttu-id="0f5da-136">(Option A) Führen Sie das PST-Importskript manuell aus, um die gesammelten PST-Dateien in Exchange Server 2013 zu importieren.</span><span class="sxs-lookup"><span data-stu-id="0f5da-136">(Option A) Manually run the PST import script to import the collected PST files into Exchange Server 2013.</span></span> <br/> |
|![Magenta-Beschriftung 7](media/ff15e89c-d2fd-4614-9838-5e18287d578b.png)|<span data-ttu-id="0f5da-138">(Option B) Importieren Sie die gesammelten PST-Dateien mithilfe des Microsoft 365-Importtools und-Prozesses in Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="0f5da-138">(Option B) Using the Microsoft 365 Import tool and process, import the collected PST files into Exchange Online.</span></span>  <br/> |
|![Magenta-Beschriftung 8](media/aaf3bd3d-9508-4aaf-a3af-44ba501da63a.png)|<span data-ttu-id="0f5da-140">Verschieben Sie alle gesammelten Dateien zur langfristigen Speicherung mit dem MoveToColdStorageSystem Center Orchestrator 2012 R2-Runbook in eine Azure-Dateifreigabe.</span><span class="sxs-lookup"><span data-stu-id="0f5da-140">Move all collected files to an Azure file share for long term storage with the MoveToColdStorage System Center Orchestrator 2012 R2 runbook.</span></span> <br/> |
|![Magenta-Beschriftung 9](media/b354642e-445e-4723-a84a-b41f7ac6e774.png)|<span data-ttu-id="0f5da-142">Indexieren Sie die Dateien in der Cold Storage-Dateifreigabe mit SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="0f5da-142">Index the files in the cold storage file share with SharePoint 2013.</span></span>  <br/> |
|![Magenta-Beschriftung 10](media/cebf7de5-7525-413b-9e52-638a4f8b2f74.png)|<span data-ttu-id="0f5da-144">Führen Sie eDiscovery für Inhalte in Cold Storage und im lokalen Exchange Server 2013 durch.</span><span class="sxs-lookup"><span data-stu-id="0f5da-144">Perform eDiscovery on content in cold storage and in the on-premises Exchange Server 2013.</span></span>  <br/> |
|![Magenta-Beschriftung 11](media/e59ab403-2f19-497a-92a5-549846dded66.png)|<span data-ttu-id="0f5da-146">Ausführen von eDiscovery für Inhalte in Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="0f5da-146">Perform eDiscovery on content in Microsoft 365.</span></span>  <br/> |
   
## <a name="prerequisites"></a><span data-ttu-id="0f5da-147">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="0f5da-147">Prerequisites</span></span>

<span data-ttu-id="0f5da-148">The configuration of this solution requires many elements, most of which you likely have in place and configured if you're thinking about eDiscovery.</span><span class="sxs-lookup"><span data-stu-id="0f5da-148">The configuration of this solution requires many elements, most of which you likely have in place and configured if you're thinking about eDiscovery.</span></span> <span data-ttu-id="0f5da-149">For the elements that you may not have or ones that require a specific configuration, we'll provide you with the links you need build out your base configuration.</span><span class="sxs-lookup"><span data-stu-id="0f5da-149">For the elements that you may not have or ones that require a specific configuration, we'll provide you with the links you need build out your base configuration.</span></span> <span data-ttu-id="0f5da-150">You must have the base configuration in place before you configure the solution itself.</span><span class="sxs-lookup"><span data-stu-id="0f5da-150">You must have the base configuration in place before you configure the solution itself.</span></span>
  
### <a name="base-configuration"></a><span data-ttu-id="0f5da-151">Standardkonfiguration</span><span class="sxs-lookup"><span data-stu-id="0f5da-151">Base configuration</span></span>

|<span data-ttu-id="0f5da-152">**Element**</span><span class="sxs-lookup"><span data-stu-id="0f5da-152">**Element**</span></span>|<span data-ttu-id="0f5da-153">**Link**</span><span class="sxs-lookup"><span data-stu-id="0f5da-153">**Link**</span></span>|
|:-----|:-----|
|<span data-ttu-id="0f5da-154">Active Directory-Domänendienste (AD DS)-Domäne</span><span class="sxs-lookup"><span data-stu-id="0f5da-154">Active Directory Domain Services (AD DS) domain</span></span>  <br/> ||
|<span data-ttu-id="0f5da-155">Internetkonnektivität von Ihrem lokalen Netzwerk aus</span><span class="sxs-lookup"><span data-stu-id="0f5da-155">Internet connectivity from your on-premises network</span></span>  <br/> ||
|<span data-ttu-id="0f5da-156">SQL Server 2012 zur Unterstützung von SharePoint 2013 und System Center Orchestrator 2012 R2</span><span class="sxs-lookup"><span data-stu-id="0f5da-156">SQL Server 2012 to support SharePoint 2013 and System Center Orchestrator 2012 R2</span></span>  <br/> |[<span data-ttu-id="0f5da-157">Bereitstellen von System Center 2012 - Orchestrator</span><span class="sxs-lookup"><span data-stu-id="0f5da-157">Deploying System Center Orchestrator - 2012</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=613503) <br/> |
| <span data-ttu-id="0f5da-158">(lokal oder Azure-basiert) für (erforderlich für Option A)</span><span class="sxs-lookup"><span data-stu-id="0f5da-158">On-premises or Azure based SharePoint 2013 for eDiscovery (required for Option A)</span></span> <br/> ||
|<span data-ttu-id="0f5da-159">Lokaler Dateifreigabenserver für Staging</span><span class="sxs-lookup"><span data-stu-id="0f5da-159">On-premises file share server for staging</span></span>  <br/> ||
|<span data-ttu-id="0f5da-160">Lokaler Exchange Server 2013 für PST-Import aus Option A</span><span class="sxs-lookup"><span data-stu-id="0f5da-160">On-premises Exchange Server 2013 for Option A PST import</span></span>  <br/> |<span data-ttu-id="0f5da-161">CU5 (15.913.22) ist verfügbar unter [CU5](https://go.microsoft.com/fwlink/p/?LinkId=613426).</span><span class="sxs-lookup"><span data-stu-id="0f5da-161">CU5 (15.913.22) is available at [CU5](https://go.microsoft.com/fwlink/p/?LinkId=613426).</span></span>  <br/> |
|<span data-ttu-id="0f5da-162">System Center Orchestrator 2012 R2</span><span class="sxs-lookup"><span data-stu-id="0f5da-162">System Center Orchestrator 2012 R2</span></span>  <br/> |[<span data-ttu-id="0f5da-163">Bereitstellen von System Center 2012 - Orchestrator</span><span class="sxs-lookup"><span data-stu-id="0f5da-163">Deploying System Center Orchestrator - 2012</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=613503) <br/> |
|<span data-ttu-id="0f5da-164">Microsoft 365 E3 mit Exchange Online und SharePoint Online (für Option B erforderlich)</span><span class="sxs-lookup"><span data-stu-id="0f5da-164">Microsoft 365 E3 with Exchange Online and SharePoint Online (required for Option B)</span></span>  <br/> |<span data-ttu-id="0f5da-165">Informationen zum Registrieren eines Microsoft 365 E3-Abonnements finden Sie unter [Microsoft 365 E3-Abonnement](https://www.microsoft.com/microsoft-365/enterprise-e3-business-software?activetab=pivot%3aoverviewtab).</span><span class="sxs-lookup"><span data-stu-id="0f5da-165">To sign up for a Microsoft 365 E3 subscription, see [Microsoft 365 E3 subscription](https://www.microsoft.com/microsoft-365/enterprise-e3-business-software?activetab=pivot%3aoverviewtab).</span></span>  <br/> |
|<span data-ttu-id="0f5da-166">Azure-Abonnement mit einem virtuellen Computer</span><span class="sxs-lookup"><span data-stu-id="0f5da-166">Azure subscription with a virtual machine</span></span>  <br/> |<span data-ttu-id="0f5da-167">Informationen zum Registrieren für ein Azure-Abonnement finden Sie unter [Anmelden bei Windows Azure](https://go.microsoft.com/fwlink/p/?LinkId=512010).</span><span class="sxs-lookup"><span data-stu-id="0f5da-167">To sign up for a Azure, see [Subscribe to Windows Azure](https://go.microsoft.com/fwlink/p/?LinkId=512010)</span></span> <br/> |
|<span data-ttu-id="0f5da-168">Eine VPN-Verbindung zwischen Ihrem lokalen Netzwerk und Ihrem Azure-Abonnement</span><span class="sxs-lookup"><span data-stu-id="0f5da-168">A VPN connection between your on-premises network and your Azure subscription</span></span>  <br/> |<span data-ttu-id="0f5da-169">Informationen zum Einrichten eines VPN-Tunnels zwischen Ihrem Azure-Abonnement und Ihrem lokalen Netzwerk finden Sie unter [Verbinden eines lokalen Netzwerks mit einem virtuellen Microsoft Azure-Netzwerk](https://go.microsoft.com/fwlink/p/?LinkId=613507).</span><span class="sxs-lookup"><span data-stu-id="0f5da-169">To set up a VPN tunnel between your Azure subscription and your on-premises network, see [Connect an on-premises network to a Microsoft Azure virtual network](https://go.microsoft.com/fwlink/p/?LinkId=613507).</span></span>  <br/> |
|<span data-ttu-id="0f5da-170">SharePoint 2013eDiscovery ist zum Durchsuchen von SharePoint und Exchange Server 2013 sowie optional Lync Server 2013 konfiguriert</span><span class="sxs-lookup"><span data-stu-id="0f5da-170">SharePoint 2013 eDiscovery configured to search across SharePoint and Exchange Server 2013 and optionally Lync Server 2013</span></span>  <br/> |<span data-ttu-id="0f5da-171">Informationen zum Konfigurieren von eDiscovery auf diese Weise finden Sie unter [Konfigurieren von eDiscovery in SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=613508) und[Testumgebungsanleitung: Konfigurieren von eDiscovery für eine Testumgebung mit Exchange-, Lync-, SharePoint- und Windows-Dateifreigaben](https://go.microsoft.com/fwlink/p/?LinkId=393130).</span><span class="sxs-lookup"><span data-stu-id="0f5da-171">To configure eDiscovery in this fashion, see [Configure eDiscovery in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=613508) and[Test Lab Guide: Configure eDiscovery for an Exchange, Lync, SharePoint and Windows File Shares Test Lab](https://go.microsoft.com/fwlink/p/?LinkId=393130).</span></span>  <br/> |
|<span data-ttu-id="0f5da-172">eDiscovery in Microsoft 365 für SharePoint Online und Exchange Online</span><span class="sxs-lookup"><span data-stu-id="0f5da-172">eDiscovery in Microsoft 365 for SharePoint Online and Exchange Online</span></span>  <br/> |<span data-ttu-id="0f5da-173">Informationen zum Konfigurieren von eDiscovery in Microsoft 365 finden Sie unter [Einrichten eines eDiscovery Centers in SharePoint Online](https://go.microsoft.com/fwlink/p/?LinkId=613628).</span><span class="sxs-lookup"><span data-stu-id="0f5da-173">To configure eDiscovery in Microsoft 365, see [Set up an eDiscovery Center in SharePoint Online](https://go.microsoft.com/fwlink/p/?LinkId=613628).</span></span>  <br/> |
   
## <a name="configure-the-environment"></a><span data-ttu-id="0f5da-174">Konfigurieren der Umgebung</span><span class="sxs-lookup"><span data-stu-id="0f5da-174">Configure the environment</span></span>

<span data-ttu-id="0f5da-175">Nachdem nun die Basiskonfiguration steht, können Sie mit der Konfiguration der eigentlichen Lösung fortfahren.</span><span class="sxs-lookup"><span data-stu-id="0f5da-175">Now that you have the base configuration in place, you can move ahead to configuring the solution itself.</span></span> 
  
### <a name="staging-file-share"></a><span data-ttu-id="0f5da-176">Staging-Dateifreigabe</span><span class="sxs-lookup"><span data-stu-id="0f5da-176">Staging file share</span></span>

1. <span data-ttu-id="0f5da-177">Erstellen Sie in der lokalen Domäne eine globale Sicherheitsgruppe mit dem Namen Custodians.</span><span class="sxs-lookup"><span data-stu-id="0f5da-177">In the on-premises domain, create a global security group named Custodians.</span></span>
    
2. <span data-ttu-id="0f5da-178">Create a hidden file share for the files that are collected from Custodians computers.</span><span class="sxs-lookup"><span data-stu-id="0f5da-178">Create a hidden file share for the files that are collected from Custodians computers.</span></span> <span data-ttu-id="0f5da-179">This should be on an on-premises server.</span><span class="sxs-lookup"><span data-stu-id="0f5da-179">This should be on an on-premises server.</span></span> <span data-ttu-id="0f5da-180">For example, on a server called Staging, create a file share called Cases$.</span><span class="sxs-lookup"><span data-stu-id="0f5da-180">For example, on a server called Staging, create a file share called Cases$.</span></span> <span data-ttu-id="0f5da-181">The **$** is required to make this a hidden share.</span><span class="sxs-lookup"><span data-stu-id="0f5da-181">The **$** is required to make this a hidden share.</span></span>
    
3. <span data-ttu-id="0f5da-182">Legen Sie die folgenden Freigabeberechtigungen fest:</span><span class="sxs-lookup"><span data-stu-id="0f5da-182">Set the following share permissions:</span></span>
    
  - <span data-ttu-id="0f5da-183">Verwalter: Lesen, Ändern</span><span class="sxs-lookup"><span data-stu-id="0f5da-183">Custodians: Change, Read</span></span>
    
  - <span data-ttu-id="0f5da-184">Administratoren: Vollzugriff</span><span class="sxs-lookup"><span data-stu-id="0f5da-184">Administrators: Full Control</span></span>
    
  - <span data-ttu-id="0f5da-185">Vertrauenswürdiges Exchange-Teilsystem: Lesen, Ändern</span><span class="sxs-lookup"><span data-stu-id="0f5da-185">Exchange Trusted Subsystem: Change, Read</span></span>
    
4. <span data-ttu-id="0f5da-186">Open the **Security** tab, add the Custodians group, and click **Advanced**.</span><span class="sxs-lookup"><span data-stu-id="0f5da-186">Open the **Security** tab, add the Custodians group, and click **Advanced**.</span></span> <span data-ttu-id="0f5da-187">Set the following permissions for the Custodians group:</span><span class="sxs-lookup"><span data-stu-id="0f5da-187">Set the following permissions for the Custodians group:</span></span>
    
  - <span data-ttu-id="0f5da-188">**Typ: Verweigern**</span><span class="sxs-lookup"><span data-stu-id="0f5da-188">**Type: Deny**</span></span>
    
  - <span data-ttu-id="0f5da-189">**Gilt für: Diesen Ordner, Unterordner und Dateien**</span><span class="sxs-lookup"><span data-stu-id="0f5da-189">**Applies to: This folder, subfolders and files**</span></span>
    
5. <span data-ttu-id="0f5da-190">Klicken Sie auf **Erweiterte Berechtigungen**, und wählen Sie Folgendes aus:</span><span class="sxs-lookup"><span data-stu-id="0f5da-190">Click **Advanced Permissions** and select the following:</span></span>
    
  - <span data-ttu-id="0f5da-191">**Attribute lesen**</span><span class="sxs-lookup"><span data-stu-id="0f5da-191">**Read attributes**</span></span>
    
  - <span data-ttu-id="0f5da-192">**Erweiterte Attribute lesen**</span><span class="sxs-lookup"><span data-stu-id="0f5da-192">**Read extended attributes**</span></span>
    
  - <span data-ttu-id="0f5da-193">**Leseberechtigungen**</span><span class="sxs-lookup"><span data-stu-id="0f5da-193">**Read permissions**</span></span>
    
6. <span data-ttu-id="0f5da-194">Testen Sie den Zugriff auf die Dateifreigabe „Cases$“ folgendermaßen:</span><span class="sxs-lookup"><span data-stu-id="0f5da-194">Test access to the Cases$ file share by doing the following:</span></span>
    
1. <span data-ttu-id="0f5da-195">Fügen Sie der Gruppe „Verwalter“ einen Benutzer hinzu.</span><span class="sxs-lookup"><span data-stu-id="0f5da-195">Add a user to the Custodians group.</span></span>
    
2. <span data-ttu-id="0f5da-196">Platzieren Sie eine Datei im Ordner „Cases$“.</span><span class="sxs-lookup"><span data-stu-id="0f5da-196">Place a file in the Cases$ folder.</span></span>
    
3. <span data-ttu-id="0f5da-197">As the user, browse to the staging server, for example browse to the \\\\Staging share to see what shares are available.</span><span class="sxs-lookup"><span data-stu-id="0f5da-197">As the user, browse to the staging server, for example browse to the \\\\Staging share to see what shares are available.</span></span> <span data-ttu-id="0f5da-198">You shouldn't see the **Cases$** share listed.</span><span class="sxs-lookup"><span data-stu-id="0f5da-198">You shouldn't see the **Cases$** share listed.</span></span>
    
4. <span data-ttu-id="0f5da-199">Manually type the full path to the Cases$ share into Explorer.</span><span class="sxs-lookup"><span data-stu-id="0f5da-199">Manually type the full path to the Cases$ share into Explorer.</span></span> <span data-ttu-id="0f5da-200">This should open the Cases$ share.</span><span class="sxs-lookup"><span data-stu-id="0f5da-200">This should open the Cases$ share.</span></span>
    
5. <span data-ttu-id="0f5da-201">Try to open the file you previously placed in the share.</span><span class="sxs-lookup"><span data-stu-id="0f5da-201">Try to open the file you previously placed in the share.</span></span> <span data-ttu-id="0f5da-202">This should fail.</span><span class="sxs-lookup"><span data-stu-id="0f5da-202">This should fail.</span></span>
    
### <a name="logon-script"></a><span data-ttu-id="0f5da-203">Anmeldeskript</span><span class="sxs-lookup"><span data-stu-id="0f5da-203">Logon script</span></span>

1. <span data-ttu-id="0f5da-204">Kopieren Sie dieses Windows PowerShell-Skript, und fügen Sie es in Editor ein:</span><span class="sxs-lookup"><span data-stu-id="0f5da-204">Copy and paste this Windows PowerShell script into Notepad:</span></span>
    
  ```
  # Automated file collection script
# Substantial error processing should be added for robust execution and troubleshooting opportunities
# All commented out write-hosts are for debugging only and are commented out for regular execution

# Functions 

Function CreateCaseFolder() {

#Check to see if case folder already exists
$CaseFolderCheck = Test-Path $CaseLocation

try {

    if (!$CaseFolderCheck) {
    # Case folder doesn't exist.  Create the case folder and the log file location
    # Write-Host -ForegroundColor Cyan "Creating Case Folder $CaseLocation"
    New-Item "$CaseLocation" -ItemType Directory -Force -ErrorAction SilentlyContinue
    # Write-Host -ForegroundColor Cyan "Creating Case Log Folder $CaseLogLocation"
    New-Item "$CaseLogLocation" -ItemType Directory -Force -ErrorAction SilentlyContinue
    # Write-Host -ForegroundColor Cyan "Creating Case PST folder $CasePSTLocation"
    New-Item "$CasePSTLocation" -ItemType Directory -Force -ErrorAction SilentlyContinue

    }
    else {

    # do nothing since the target case folder already exists

    }
}
catch [System.Exception] {

    # To do..
    # to log to an exception or log file
    
    }
}

Function CopyFileToCaseFolder($SourcePath, $TargetPath, $FileName) {
    
    # Check to see if the file already exists
    $TargetFileCheck = Test-Path $TargetPath\$FileName

try {

    if (!$TargetFileCheck) {
    # Copy the file to the case folder
    Write-Host $SourcePath $TargetPath $FileName
    robocopy "$SourcePath" "$TargetPath" "$FileName" /COPY:DATSO /TEE /LOG+:$LoggingFile /R:10 /W:10 | Out-Null

    }
    else {

    # do nothing since file is already in the target case folder

    }
}
catch [System.Exception] {

    # To do..
    # to log to an exception or log file
    
    }
}

# Global variable initializations

# Error log
$Loggederrors=@()

# The array to contain the file types we collect
$FileTypes = @("*.doc","*.docx","*.pst","*.txt")

# We'll set the case number to be a combination of the date and user name
# For example, a case for John Doe on Dec 14, 2014 at 2:38pm would be:
# 201412141438_jdoe
$CaseNo = get-date -Format yyyyMMddHHmm
$CaseNo = $CaseNo + "_" + [Environment]::UserName

# Target location to copy case files
$CaseRootLocation = "\\staging\Cases$" 

# File copy location, log file location, PST file location and temporary log file location
$CaseLocation = $CaseRootLocation + "\" + $CaseNo
$CaseLogLocation = $CaseRootLocation + "\" + $CaseNo + "\_Log"
$CasePSTLocation = $CaseRootLocation + "\" + $CaseNo + "\_PSTs"
$TemporaryLogLocation = [Environment]::getfolderpath('ApplicationData') + "\" + $CaseNo

# Inventory of local drives
$LocalDrives = Get-PSDrive -PSProvider FileSystem -Scope Global

$LoggingFile = "$CaseLogLocation\FileCopyErrors.log"

# Main script

# Create the case folder if it doesn't already exist
CreateCaseFolder

# Create the list of files to be copied
# First create the temporary directory in the AppData\Roaming folder
New-Item "$TemporaryLogLocation" -ItemType Directory -Force -ErrorAction SilentlyContinue
$LocalDrives | foreach {

    # Write-Host -ForeGroundColor Cyan "Collecting Files for Drive: " $_
    Get-ChildItem -Path $_.Root -Recurse -Include $FileTypes -ErrorAction SilentlyContinue -ErrorVariable +Loggederrors | Export-Clixml $TemporaryLogLocation\$_.xml -Force
    # Needs try catch and logged collection error file
}

# Now let's read each file and copy any files we need to the case folder
# We will also copy these XMLs to the case log files folder as we go along
# We only want to process XML files, just in case something else got in there as the script ran
$CaseDriveFiles = Get-ChildItem $TemporaryLogLocation -Filter '*.xml'
$CaseDriveFiles | foreach {
    # Copy the XML file to the case log location
    CopyFileToCaseFolder $_.Directory.FullName $CaseLogLocation $_.Name
    $DriveFile = $_.FullName
    # Write-Host -ForegroundColor Cyan "Copying Files specified in the XML file: $DriveFile"
    $CurrentDriveFile = Import-Clixml $DriveFile
    $CurrentDriveFile | foreach {
        # write-host $_.FullName
        # if it's a PST, add to the PSTs folder. otherwise add it to case folder
        if ($_.Extension -match '.PST')
        {
            CopyFileToCaseFolder $_.Directory.FullName $CasePSTLocation $_.Name
            write-host "this is a PST"
        }
        else
        {
            CopyFileToCaseFolder $_.Directory.FullName $CaseLocation $_.Name
        }
    }
}

# Now delete the temporary log file
Remove-Item $TemporaryLogLocation -Recurse 

Write-Host -ForegroundColor Cyan "Finished."

  ```

2. <span data-ttu-id="0f5da-205">Speichern Sie das Skript unter CollectionScript.ps1 an einem für Sie leicht auffindbaren Speicherort, z. B. C:\\AFCScripts.</span><span class="sxs-lookup"><span data-stu-id="0f5da-205">Save the above script as CollectionScript.ps1 in a location that's easy for you to find, for example, C:\\AFCScripts.</span></span>
    
3. <span data-ttu-id="0f5da-206">Use the Go To feature in Notepad.</span><span class="sxs-lookup"><span data-stu-id="0f5da-206">Use the Go To feature in Notepad.</span></span> <span data-ttu-id="0f5da-207">Make the following changes, as needed:</span><span class="sxs-lookup"><span data-stu-id="0f5da-207">Make the following changes, as needed:</span></span>
    
|<span data-ttu-id="0f5da-208">**Zeilennummer**</span><span class="sxs-lookup"><span data-stu-id="0f5da-208">**Line #**</span></span>|<span data-ttu-id="0f5da-209">**Zu änderndes Element**</span><span class="sxs-lookup"><span data-stu-id="0f5da-209">**What you need to change**</span></span>|<span data-ttu-id="0f5da-210">**Erforderlich/optional**</span><span class="sxs-lookup"><span data-stu-id="0f5da-210">**Required/optional**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="0f5da-211">71</span><span class="sxs-lookup"><span data-stu-id="0f5da-211">71</span></span>  <br/> |<span data-ttu-id="0f5da-212">**$FileTypes** variable.</span><span class="sxs-lookup"><span data-stu-id="0f5da-212">**$FileTypes** variable.</span></span> <span data-ttu-id="0f5da-213">Include all the file type extensions that you want the script to inventory and collect in the array variable.</span><span class="sxs-lookup"><span data-stu-id="0f5da-213">Include all the file type extensions that you want the script to inventory and collect in the array variable.</span></span> <br/> |<span data-ttu-id="0f5da-214">Optional</span><span class="sxs-lookup"><span data-stu-id="0f5da-214">Optional</span></span>  <br/> |
|<span data-ttu-id="0f5da-215">76 und 77</span><span class="sxs-lookup"><span data-stu-id="0f5da-215">76 and 77</span></span>  <br/> |<span data-ttu-id="0f5da-216">Change the way the **$CaseNo** variable is built to suit your needs.</span><span class="sxs-lookup"><span data-stu-id="0f5da-216">Change the way the **$CaseNo** variable is built to suit your needs.</span></span> <span data-ttu-id="0f5da-217">The script captures the current date and time and appends the user name to it.</span><span class="sxs-lookup"><span data-stu-id="0f5da-217">The script captures the current date and time and appends the user name to it.</span></span> <br/> |<span data-ttu-id="0f5da-218">Optional</span><span class="sxs-lookup"><span data-stu-id="0f5da-218">Optional</span></span>  <br/> |
|<span data-ttu-id="0f5da-219">80</span><span class="sxs-lookup"><span data-stu-id="0f5da-219">80</span></span>  <br/> |<span data-ttu-id="0f5da-220">Die **$CaseRootLocation** -Variable muss auf die Sammlungsdateifreigabe Ihrer Stagingserver festgelegt werden. Beispielsweise **\\\\Staging\\Cases$**. </span><span class="sxs-lookup"><span data-stu-id="0f5da-220">**$CaseRootLocation** variable needs to be set to your staging servers collection file share, for example **\\\\Staging\\Cases$**.</span></span> <br/> |<span data-ttu-id="0f5da-221">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="0f5da-221">Required</span></span>  <br/> |
   
4. <span data-ttu-id="0f5da-222">Platzieren Sie die Datei „CollectionScript.ps1“ in die Netlogon-Dateifreigabe auf einem Domänencontroller.</span><span class="sxs-lookup"><span data-stu-id="0f5da-222">Place the CollectionScript.ps1 file in the Netlogon file share on a domain controller.</span></span> 
    
### <a name="configure-gpo-for-the-logon-script-and-custodians-group"></a><span data-ttu-id="0f5da-223">Konfigurieren des Gruppenrichtlinienobjekts für das Anmeldeskript und die Verwaltergruppe</span><span class="sxs-lookup"><span data-stu-id="0f5da-223">Configure GPO for the logon script and Custodians Group</span></span>

1. <span data-ttu-id="0f5da-224">Konfigurieren Sie ein Anmeldeskript für die Gruppe „Verwalter", indem Sie die Schritte im Abschnitt „Zuweisen von Benutzeranmeldeskripts" im Thema [Verwenden von Skripts zum Starten, Herunterfahren, Anmelden und Abmelden in der Gruppenrichtlinie](https://go.microsoft.com/fwlink/p/?LinkId=614844) befolgen.</span><span class="sxs-lookup"><span data-stu-id="0f5da-224">Configure a logon script for the Custodians group by following the "How to assign user logon scripts" section in the topic, [Using Startup, Shutdown, Logon, and Logoff Scripts in Group Policy](https://go.microsoft.com/fwlink/p/?LinkId=614844).</span></span>
    
2. <span data-ttu-id="0f5da-225">Entfernen Sie authentifizierte Benutzer aus der **Sicherheitsfilterung**, und fügen Sie die Verwaltergruppe hinzu.</span><span class="sxs-lookup"><span data-stu-id="0f5da-225">Remove authenticated users from **Security Filtering**, and add the Custodians group.</span></span>
    
### <a name="pst-import-option-a-script-for-exchange-server-2013"></a><span data-ttu-id="0f5da-226">PST-Import, Option A, Skript für Exchange Server 2013</span><span class="sxs-lookup"><span data-stu-id="0f5da-226">PST import Option A, script for Exchange Server 2013</span></span>

1.  <span data-ttu-id="0f5da-227">Kopieren Sie das folgende Windows PowerShell-Skript, und fügen Sie es in Editor ein:</span><span class="sxs-lookup"><span data-stu-id="0f5da-227">Copy and paste the following Windows PowerShell script into Notepad:</span></span>
    
  ```
  # Script to import all PSTs in a given folder to a target mailbox
#
# This is for on-prem Exchange only
# Input parameters
# When you run the script, you call it with two parameters, PST source path and target mailbox alias
# For example:  .\PSTImport.ps1 \\FileShare\PSTFiles jdoe

param ([String]$SourcePath,[String]$MailboxAlias)

# Folder identifier is the string we want to show in the mailbox that we import the PSTs to

$FolderIdentifier = "zzImportedPSTs_"

# Connect to Exchange remote powershell using the connection Uri below
# This would be the format https://<exchange server FQDN>/Powershell

$ConnectionUri = 'https://h10-exch/PowerShell'
$RemoteEx2013Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri $ConnectionUri -Authentication Kerberos
Import-PSSession $RemoteEx2013Session

# Get all the files in the source path

$AllFiles = Get-ChildItem $SourcePath -Recurse

# Go through each file and if it's a PST launch a mailbox import request for it

$AllFiles | ForEach-Object {
    If ($_.Extension -eq ".pst") {
        $ImportName = $MailboxAlias + "_" + $_.Name
        $FolderName = $FolderIdentifier + $_.Name
        New-MailboxImportRequest -Name $ImportName -Mailbox $MailboxAlias -FilePath $_.FullName -TargetRootFolder $FolderName
    }
}
  ```

2. <span data-ttu-id="0f5da-228">Save the script as PSTImportScript.ps1 in a location that's easy for you to find.</span><span class="sxs-lookup"><span data-stu-id="0f5da-228">Save the script as PSTImportScript.ps1 in a location that's easy for you to find.</span></span> <span data-ttu-id="0f5da-229">For example and ease of use, create a folder on your staging server called \\\\Staging\\AFCScripts, and save it there.</span><span class="sxs-lookup"><span data-stu-id="0f5da-229">For example and ease of use, create a folder on your staging server called \\\\Staging\\AFCScripts, and save it there.</span></span>
    
3. <span data-ttu-id="0f5da-230">Verwenden Sie die Funktion „Gehe zu...“ in Editor, und nehmen Sie bei Bedarf die folgenden Änderungen vor:</span><span class="sxs-lookup"><span data-stu-id="0f5da-230">Use the Go To feature in Notepad, and make the following changes, as needed:</span></span>
    
|<span data-ttu-id="0f5da-231">**Zeilennummer**</span><span class="sxs-lookup"><span data-stu-id="0f5da-231">**Line #**</span></span>|<span data-ttu-id="0f5da-232">**Zu änderndes Element**</span><span class="sxs-lookup"><span data-stu-id="0f5da-232">**What you need to change**</span></span>|<span data-ttu-id="0f5da-233">**Erforderlich/optional**</span><span class="sxs-lookup"><span data-stu-id="0f5da-233">**Required/optional**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="0f5da-234">12 </span><span class="sxs-lookup"><span data-stu-id="0f5da-234">12</span></span>  <br/> |<span data-ttu-id="0f5da-235">**$FolderIdentifier** tags the mailbox folders that PSTs are imported into.</span><span class="sxs-lookup"><span data-stu-id="0f5da-235">**$FolderIdentifier** tags the mailbox folders that PSTs are imported into.</span></span> <span data-ttu-id="0f5da-236">Change this if necessary.</span><span class="sxs-lookup"><span data-stu-id="0f5da-236">Change this if necessary.</span></span> <br/> |<span data-ttu-id="0f5da-237">Optional</span><span class="sxs-lookup"><span data-stu-id="0f5da-237">Optional</span></span>  <br/> |
|<span data-ttu-id="0f5da-238">17 </span><span class="sxs-lookup"><span data-stu-id="0f5da-238">17</span></span>  <br/> |<span data-ttu-id="0f5da-239">**$ConnectionUri** muss auf Ihrem eigenen Server festgelegt sein.</span><span class="sxs-lookup"><span data-stu-id="0f5da-239">**$ConnectionUri** needs to be set to your own server.</span></span> <br/> <span data-ttu-id="0f5da-240">> [!IMPORTANT]> Make sure your **$ConnectionUri** points to a http location, not https.</span><span class="sxs-lookup"><span data-stu-id="0f5da-240">> [!IMPORTANT]> Make sure your **$ConnectionUri** points to a http location, not https.</span></span> <span data-ttu-id="0f5da-241">It won't work with https:.</span><span class="sxs-lookup"><span data-stu-id="0f5da-241">It won't work with https:.</span></span>          |<span data-ttu-id="0f5da-242">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="0f5da-242">Required</span></span>  <br/> |
   
4. <span data-ttu-id="0f5da-243">Stellen Sie sicher, dass das Exchange-Konto „Vertrauenswürdiges Teilsystem" Lese-, Schreib- und Ausführberechtigungen für die Freigabe \\\\Staging\\Cases$ aufweist.</span><span class="sxs-lookup"><span data-stu-id="0f5da-243">Verify that the Exchange Trusted Subsystem account has Read, Write, and Execute permissions to the \\\\Staging\\Cases$ share.</span></span>
    
5. <span data-ttu-id="0f5da-244">Das PST-Importskript erfordert die folgenden zwei Eingabeparameter:</span><span class="sxs-lookup"><span data-stu-id="0f5da-244">The PST import script requires the following two input parameters:</span></span>
    
  - <span data-ttu-id="0f5da-245">**$SourcePath** Der Speicherort der zu importierenden PST-Dateien, z. B. „\\\\Staging\\Cases$".</span><span class="sxs-lookup"><span data-stu-id="0f5da-245">**$SourcePath** The location of the PST files to be imported, for example \\\\Staging\\Cases$.</span></span>
    
  - <span data-ttu-id="0f5da-246">**$MailboxAlias** Der Alias des Zielpostfachs, in dem die importierten E-Mail-Elemente empfangen werden.</span><span class="sxs-lookup"><span data-stu-id="0f5da-246">**$MailboxAlias** The alias of the target mailbox that will receive the imported email items.</span></span>
    
6. <span data-ttu-id="0f5da-247">Wenn Sie beispielsweise alle PST-Dateien aus dem Pfad „\\Staging\Cases$“ in ein Postfach mit dem Alias „eDiscoveryMailbox“ importieren möchten, führen Sie das Skript wie folgt aus: `\\staging\AFCscripts\PSTImportScript.ps1 \\Staging\cases$ eDiscoveryMailbox`.</span><span class="sxs-lookup"><span data-stu-id="0f5da-247">For example, if you want to import all the PST files from the path \\Staging\Cases$ into a mailbox with the alias eDiscoveryMailbox, you would run the script like this `\\staging\AFCscripts\PSTImportScript.ps1 \\Staging\cases$ eDiscoveryMailbox`.</span></span>
    
### <a name="pst-import-option-b-for-exchange-online"></a><span data-ttu-id="0f5da-248">PST-Import, Option B, für Exchange Online</span><span class="sxs-lookup"><span data-stu-id="0f5da-248">PST Import Option B, for Exchange Online</span></span>

-  <span data-ttu-id="0f5da-249">Create the mailbox structure to place the imported PST files into.</span><span class="sxs-lookup"><span data-stu-id="0f5da-249">Create the mailbox structure to place the imported PST files into.</span></span> <span data-ttu-id="0f5da-250">For more information on how to create a user mailbox in Exchange Online, see[Create User Mailboxes in Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=615118).</span><span class="sxs-lookup"><span data-stu-id="0f5da-250">For more information on how to create a user mailbox in Exchange Online, see[Create User Mailboxes in Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=615118).</span></span>
    
### <a name="cold-storage"></a><span data-ttu-id="0f5da-251">Cold Storage</span><span class="sxs-lookup"><span data-stu-id="0f5da-251">Cold storage</span></span>

1. <span data-ttu-id="0f5da-252">Erstellen Sie eine Dateifreigabe auf dem Virtueller Azure-Computer, in der alle gesammelten Dateien platziert werden sollen, z. B. \\\\AZFile1\\ContentColdStorage.</span><span class="sxs-lookup"><span data-stu-id="0f5da-252">Create a file share on the Azure Virtual Machine, where all the collected files will be placed, for example, \\\\AZFile1\\ContentColdStorage.</span></span>
    
2. <span data-ttu-id="0f5da-253">Grant the default content access account at least Read permissions to the share and all subfolders and files.</span><span class="sxs-lookup"><span data-stu-id="0f5da-253">Grant the default content access account at least Read permissions to the share and all subfolders and files.</span></span> <span data-ttu-id="0f5da-254">For more information about configuring SharePoint 2013 Search, see [Create and configure a Search service application in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=614940).</span><span class="sxs-lookup"><span data-stu-id="0f5da-254">For more information about configuring SharePoint 2013 Search, see [Create and configure a Search service application in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=614940).</span></span>
    
3. <span data-ttu-id="0f5da-255">Wenn Sie beabsichtigen, PST-Dateien aus \\\\AZFile1\\ContentColdStorage zu importieren, gewähren Sie dem vertrauenswürdigen Teilsystem von Exchange Lese-, Schreib- und Ausführberechtigungen für die Freigabe.</span><span class="sxs-lookup"><span data-stu-id="0f5da-255">If you anticipate importing PST files from \\\\AZFile1\\ContentColdStorage, grant the Exchange Trusted Subsystem Read, Write, and Execute permissions to the share.</span></span>
    
### <a name="orchestrator"></a><span data-ttu-id="0f5da-256">Orchestrator</span><span class="sxs-lookup"><span data-stu-id="0f5da-256">Orchestrator</span></span>

1. <span data-ttu-id="0f5da-257">Laden Sie das [ MoveToColdStorage-Runbook](https://go.microsoft.com/fwlink/?LinkId=616095) aus dem Microsoft Download Center herunter.</span><span class="sxs-lookup"><span data-stu-id="0f5da-257">Download the[ MoveToColdStorage runbook](https://go.microsoft.com/fwlink/?LinkId=616095) from the Microsoft Download Center.</span></span>
    
2. <span data-ttu-id="0f5da-258">Open the **Runbook Designer**, in the **Connections** pane, click the folder that you want to import the runbook into.</span><span class="sxs-lookup"><span data-stu-id="0f5da-258">Open the **Runbook Designer**, in the **Connections** pane, click the folder that you want to import the runbook into.</span></span> <span data-ttu-id="0f5da-259">Click the **Actions** menu, and the click **Import**.</span><span class="sxs-lookup"><span data-stu-id="0f5da-259">Click the **Actions** menu, and the click **Import**.</span></span> <span data-ttu-id="0f5da-260">The **Import** dialog box appears.</span><span class="sxs-lookup"><span data-stu-id="0f5da-260">The **Import** dialog box appears.</span></span>
    
3. <span data-ttu-id="0f5da-261">Geben Sie im Feld **Dateispeicherort** den Pfad und Dateinamen des zu importierenden Runbooks ein, oder klicken Sie auf die drei Punkte ( **...**), um die zu importierende Datei zu suchen.</span><span class="sxs-lookup"><span data-stu-id="0f5da-261">In the **File Location** box, type the path and file name of the runbook you want to import, or click the ellipsis ( **...**) to browse to the file you want to import.</span></span> 
    
4. <span data-ttu-id="0f5da-262">Select **Import runbooks** and **Import Orchestrator encrypted data**.</span><span class="sxs-lookup"><span data-stu-id="0f5da-262">Select **Import runbooks** and **Import Orchestrator encrypted data**.</span></span> <span data-ttu-id="0f5da-263">Clear **Counters**, **Schedules**, **Variables**, **Computer Groups**, **Import global configurations**, and **Overwrite existing global configurations**.</span><span class="sxs-lookup"><span data-stu-id="0f5da-263">Clear **Counters**, **Schedules**, **Variables**, **Computer Groups**, **Import global configurations**, and **Overwrite existing global configurations**.</span></span>
    
5. <span data-ttu-id="0f5da-264">Klicken Sie auf **Fertig stellen**.</span><span class="sxs-lookup"><span data-stu-id="0f5da-264">Click **Finish**.</span></span>
    
6. <span data-ttu-id="0f5da-265">Bearbeiten Sie das Runbook **MoveFilesToColdStorage** wie folgt:</span><span class="sxs-lookup"><span data-stu-id="0f5da-265">Edit the **MoveFilesToColdStorage** runbook as follows:</span></span>
    
1. <span data-ttu-id="0f5da-266">**Move File** activity - set the **Source File** path to the collection file share, for example \\\\Staging\\cases$.</span><span class="sxs-lookup"><span data-stu-id="0f5da-266">**Move File** activity - set the **Source File** path to the collection file share, for example \\\\Staging\\cases$.</span></span> <span data-ttu-id="0f5da-267">Set the **Destination Folder** to the cold storage file share in Azure, for example \\\\AZFile1\\ContentColdStorage.</span><span class="sxs-lookup"><span data-stu-id="0f5da-267">Set the **Destination Folder** to the cold storage file share in Azure, for example \\\\AZFile1\\ContentColdStorage.</span></span> <span data-ttu-id="0f5da-268">Select **Create a file with a unique name**.</span><span class="sxs-lookup"><span data-stu-id="0f5da-268">Select **Create a file with a unique name**.</span></span>
    
2. <span data-ttu-id="0f5da-269">Aktivität **Ordner löschen** - Legen Sie **Pfad:** auf die Sammlungsdateifreigabe fest, z. B. \\\\Staging\\cases$\\*, und wählen Sie **Alle Dateien und Unterordner löschen**.</span><span class="sxs-lookup"><span data-stu-id="0f5da-269">**Delete Folder** activity - Set the **Path:** to the collection file share, for example \\\\Staging\\cases$\\*, and select **Delete all files and sub-folders**.</span></span> 
    
7. <span data-ttu-id="0f5da-270">Stellen Sie das Runbook **MoveToColdStorage** anhand der Verfahren unter[Bereitstellen von Runbooks](https://go.microsoft.com/fwlink/p/?LinkId=615120) bereit.</span><span class="sxs-lookup"><span data-stu-id="0f5da-270">Deploy the **MoveToColdStorage** runbook using the procedures in[Deploying Runbooks](https://go.microsoft.com/fwlink/p/?LinkId=615120).</span></span>
    
### <a name="sharepoint-on-premises-search-for-cold-storage"></a><span data-ttu-id="0f5da-271">Lokale SharePoint-Suche für Cold Storage</span><span class="sxs-lookup"><span data-stu-id="0f5da-271">SharePoint on-premises search for cold storage</span></span>

1. <span data-ttu-id="0f5da-272">Create an new content source in your SharePoint 2013 farm for the cold storage share in Azure, for example \\\\AZFile1\\ContentColdStorage.</span><span class="sxs-lookup"><span data-stu-id="0f5da-272">Create an new content source in your SharePoint 2013 farm for the cold storage share in Azure, for example \\\\AZFile1\\ContentColdStorage.</span></span> <span data-ttu-id="0f5da-273">For more information about managing content sources, see [Add, edit, or delete a content source in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615004)</span><span class="sxs-lookup"><span data-stu-id="0f5da-273">For more information about managing content sources, see [Add, edit, or delete a content source in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615004)</span></span>
    
2. <span data-ttu-id="0f5da-274">Start a full crawl.</span><span class="sxs-lookup"><span data-stu-id="0f5da-274">Start a full crawl.</span></span> <span data-ttu-id="0f5da-275">For more information see, [Start, pause, resume, or stop a crawl in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615005).</span><span class="sxs-lookup"><span data-stu-id="0f5da-275">For more information see, [Start, pause, resume, or stop a crawl in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615005).</span></span>
    
## <a name="using-the-solution"></a><span data-ttu-id="0f5da-276">Verwenden der Lösung</span><span class="sxs-lookup"><span data-stu-id="0f5da-276">Using the solution</span></span>

<span data-ttu-id="0f5da-277">There are five major steps in using this solution, assuming you don't want to import the PST files into both Exchange Server 2013 and Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="0f5da-277">There are five major steps in using this solution, assuming you don't want to import the PST files into both Exchange Server 2013 and Exchange Online.</span></span> <span data-ttu-id="0f5da-278">This section provides you with the procedures for all of them.</span><span class="sxs-lookup"><span data-stu-id="0f5da-278">This section provides you with the procedures for all of them.</span></span> <span data-ttu-id="0f5da-279">Your primary interaction with the solution will be in doing the following:</span><span class="sxs-lookup"><span data-stu-id="0f5da-279">Your primary interaction with the solution will be in doing the following:</span></span>
  
1. <span data-ttu-id="0f5da-280">Verwalten Sie die Benutzermitgliedschaft in der Gruppe der Verwalter.</span><span class="sxs-lookup"><span data-stu-id="0f5da-280">Manage user membership in the Custodians group.</span></span>
    
2. <span data-ttu-id="0f5da-281">Review the log files generated by the logon script.</span><span class="sxs-lookup"><span data-stu-id="0f5da-281">Review the log files generated by the logon script.</span></span> <span data-ttu-id="0f5da-282">The FileCopyErrors.log lists all the files that were not successfully copied.</span><span class="sxs-lookup"><span data-stu-id="0f5da-282">The FileCopyErrors.log lists all the files that were not successfully copied.</span></span> <span data-ttu-id="0f5da-283">You need to decide what you want to do with them</span><span class="sxs-lookup"><span data-stu-id="0f5da-283">You need to decide what you want to do with them</span></span>
    
3. <span data-ttu-id="0f5da-284">Verwalten des PST-Importvorgangs.</span><span class="sxs-lookup"><span data-stu-id="0f5da-284">Managing the PST import process.</span></span>
    
4. <span data-ttu-id="0f5da-285">Verschieben der Sammlungsdateien in Cold Storage.</span><span class="sxs-lookup"><span data-stu-id="0f5da-285">Moving the collection files to cold storage.</span></span>
    
<span data-ttu-id="0f5da-286">Alle anderen Schritte sind nicht spezifisch für diese Lösung.</span><span class="sxs-lookup"><span data-stu-id="0f5da-286">All the other steps are not specific to this solution.</span></span> <span data-ttu-id="0f5da-287">Es handelt sich um Standard Verwaltungsaufgaben, die Sie in SharePoint 2013, Microsoft 365 und Azure ausführen.</span><span class="sxs-lookup"><span data-stu-id="0f5da-287">They are standard administrative tasks that you perform in SharePoint 2013, Microsoft 365, and Azure.</span></span> <span data-ttu-id="0f5da-288">Es gibt Elemente, für die diese Lösung keine Anleitungen bereitstellt, die Sie basierend auf den Anforderungen Ihres Unternehmens ausarbeiten müssen, beispielsweise:</span><span class="sxs-lookup"><span data-stu-id="0f5da-288">There are items that this solution does not provide any guidance that you will need to work out based on your company's needs, such as:</span></span>
  
1. <span data-ttu-id="0f5da-289">Überwachen Ihrer eDiscovery-Fälle und welche Verwalter welchen Fällen zugeordnet sind.</span><span class="sxs-lookup"><span data-stu-id="0f5da-289">Tracking your eDiscovery cases, and which Custodians are associated with which case.</span></span>
    
2. <span data-ttu-id="0f5da-290">Nachverfolgen, welche Gruppen von Dateisammlungen welchem eDiscovery-Fall zugeordnet sind.</span><span class="sxs-lookup"><span data-stu-id="0f5da-290">Tracking which sets of file collections are associate with which eDiscovery case.</span></span>
    
3. <span data-ttu-id="0f5da-291">Koordinieren des Timings des Imports und der Schritte für das Verschieben in Cold Storage.</span><span class="sxs-lookup"><span data-stu-id="0f5da-291">Coordinating the timing of the Import and move to cold storage steps.</span></span>
    
4. <span data-ttu-id="0f5da-292">Verwalten des in Azure verbrauchten Dateispeicherplatzes.</span><span class="sxs-lookup"><span data-stu-id="0f5da-292">Managing the file space used in Azure.</span></span>
    
5. <span data-ttu-id="0f5da-293">Verwalten der Postfächer, in die die PST-Dateien importiert werden.</span><span class="sxs-lookup"><span data-stu-id="0f5da-293">Managing the mailboxes that PSTs are imported into.</span></span>
    
6. <span data-ttu-id="0f5da-294">Sicherung und Wiederherstellung aller lokalen Daten.</span><span class="sxs-lookup"><span data-stu-id="0f5da-294">Backup and restoration of all on-premises data.</span></span>
    
### <a name="custodian-management"></a><span data-ttu-id="0f5da-295">Verwaltung von Verwaltern</span><span class="sxs-lookup"><span data-stu-id="0f5da-295">Custodian management</span></span>

- <span data-ttu-id="0f5da-296">To start the automated file collection process for an individual user, add them to the Custodians group.</span><span class="sxs-lookup"><span data-stu-id="0f5da-296">To start the automated file collection process for an individual user, add them to the Custodians group.</span></span> <span data-ttu-id="0f5da-297">The next time that the user logs on, the logon script assigned to the Custodians group through Group Policy will run.</span><span class="sxs-lookup"><span data-stu-id="0f5da-297">The next time that the user logs on, the logon script assigned to the Custodians group through Group Policy will run.</span></span> 
    
### <a name="monitor-collected-files-and-review-log-files"></a><span data-ttu-id="0f5da-298">Überwachen der Dateiauflistung und Prüfen der Protokolldateien</span><span class="sxs-lookup"><span data-stu-id="0f5da-298">Monitor collected files and review log files</span></span>

1. <span data-ttu-id="0f5da-299">Watch the collection file share, for example \\\\Staging\\cases$\\*, for the collection folder from the user.</span><span class="sxs-lookup"><span data-stu-id="0f5da-299">Watch the collection file share, for example \\\\Staging\\cases$\\*, for the collection folder from the user.</span></span> <span data-ttu-id="0f5da-300">The name of the folder will be formatted like this:  *yyyyMMddHHmm_UserName*  .</span><span class="sxs-lookup"><span data-stu-id="0f5da-300">The name of the folder will be formatted like this:  *yyyyMMddHHmm_UserName*  .</span></span>
    
2. <span data-ttu-id="0f5da-301">When the collection is completed, open the collection folder, and browse to the _Log folder.</span><span class="sxs-lookup"><span data-stu-id="0f5da-301">When the collection is completed, open the collection folder, and browse to the _Log folder.</span></span> <span data-ttu-id="0f5da-302">In the _Log folder, you will see the following:</span><span class="sxs-lookup"><span data-stu-id="0f5da-302">In the _Log folder, you will see the following:</span></span>
    
  - <span data-ttu-id="0f5da-303">One XML file for every local drive on the user's computer, for example **A.xml**, **C.xml**.</span><span class="sxs-lookup"><span data-stu-id="0f5da-303">One XML file for every local drive on the user's computer, for example **A.xml**, **C.xml**.</span></span> <span data-ttu-id="0f5da-304">These files contain the inventory drives that they are named after, and they are used for the robocopy operation.</span><span class="sxs-lookup"><span data-stu-id="0f5da-304">These files contain the inventory drives that they are named after, and they are used for the robocopy operation.</span></span>
    
    > [!NOTE]
    > <span data-ttu-id="0f5da-305">The collection script will only create an entry in the inventory file for the file types that you defined in the script itself.</span><span class="sxs-lookup"><span data-stu-id="0f5da-305">The collection script will only create an entry in the inventory file for the file types that you defined in the script itself.</span></span> <span data-ttu-id="0f5da-306">It will not create an inventory entry for every file on the user's computer.</span><span class="sxs-lookup"><span data-stu-id="0f5da-306">It will not create an inventory entry for every file on the user's computer.</span></span> 
  
  - <span data-ttu-id="0f5da-307">One log file named FileCopyErrors.log for each collection run.</span><span class="sxs-lookup"><span data-stu-id="0f5da-307">One log file named FileCopyErrors.log for each collection run.</span></span> <span data-ttu-id="0f5da-308">This file contains a listing of the files that robocopy could not copy to the file collection share, for example, \\\\Staging\\cases$\\*.</span><span class="sxs-lookup"><span data-stu-id="0f5da-308">This file contains a listing of the files that robocopy could not copy to the file collection share, for example, \\\\Staging\\cases$\\*.</span></span> <span data-ttu-id="0f5da-309">You will need to review this and decide what actions to take for these missed files.</span><span class="sxs-lookup"><span data-stu-id="0f5da-309">You will need to review this and decide what actions to take for these missed files.</span></span> <span data-ttu-id="0f5da-310">Usually, you either need to collect them manually if you want them, or you may decide that they are not required and can therefore be omitted from the collection.</span><span class="sxs-lookup"><span data-stu-id="0f5da-310">Usually, you either need to collect them manually if you want them, or you may decide that they are not required and can therefore be omitted from the collection.</span></span>
    
### <a name="pst-import-option-a-for-exchange-server-2013"></a><span data-ttu-id="0f5da-311">PST-Import, Option A, für Exchange Server 2013</span><span class="sxs-lookup"><span data-stu-id="0f5da-311">PST import option A for Exchange Server 2013</span></span>

1. <span data-ttu-id="0f5da-312">Log on to the server that hosts the collection file share, for example **Staging**, and open Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0f5da-312">Log on to the server that hosts the collection file share, for example **Staging**, and open Windows PowerShell.</span></span> <span data-ttu-id="0f5da-313">For more information about starting Windows PowerShell, see[Starting Windows PowerShell on Windows Server](https://go.microsoft.com/fwlink/p/?LinkId=615115).</span><span class="sxs-lookup"><span data-stu-id="0f5da-313">For more information about starting Windows PowerShell, see[Starting Windows PowerShell on Windows Server](https://go.microsoft.com/fwlink/p/?LinkId=615115).</span></span>
    
2. <span data-ttu-id="0f5da-314">Set the Execution policy to Unrestricted .</span><span class="sxs-lookup"><span data-stu-id="0f5da-314">Set the Execution policy to Unrestricted .</span></span> <span data-ttu-id="0f5da-315">Type  `Set-ExecutionPolicy Unrestricted -Scope Process` into Windows PowerShell, and press Enter.</span><span class="sxs-lookup"><span data-stu-id="0f5da-315">Type  `Set-ExecutionPolicy Unrestricted -Scope Process` into Windows PowerShell, and press Enter.</span></span>
    
3. <span data-ttu-id="0f5da-316">Run the PSTImportScript.ps1 file, and provide the **$SourcePath** and **$MailboxAlias** parameters.</span><span class="sxs-lookup"><span data-stu-id="0f5da-316">Run the PSTImportScript.ps1 file, and provide the **$SourcePath** and **$MailboxAlias** parameters.</span></span> <span data-ttu-id="0f5da-317">For more information about running Windows PowerShell scripts, see[Running Scripts](https://go.microsoft.com/fwlink/p/?LinkID=615117).</span><span class="sxs-lookup"><span data-stu-id="0f5da-317">For more information about running Windows PowerShell scripts, see[Running Scripts](https://go.microsoft.com/fwlink/p/?LinkID=615117).</span></span>
    
4. <span data-ttu-id="0f5da-318">Überprüfen Sie die Ausgabe auf Fehler.</span><span class="sxs-lookup"><span data-stu-id="0f5da-318">Review the output for errors.</span></span>
    
5. <span data-ttu-id="0f5da-319">Before you attempt to import an identically named PST file into the same mailbox, you have to remove the mailbox import request.</span><span class="sxs-lookup"><span data-stu-id="0f5da-319">Before you attempt to import an identically named PST file into the same mailbox, you have to remove the mailbox import request.</span></span> <span data-ttu-id="0f5da-320">Run the following command to do that:  `Get-MailboxImportRequest | Remove-MailboxImportRequest`.</span><span class="sxs-lookup"><span data-stu-id="0f5da-320">Run the following command to do that:  `Get-MailboxImportRequest | Remove-MailboxImportRequest`.</span></span> <span data-ttu-id="0f5da-321">You will be prompted to remove each individual request from the queue.</span><span class="sxs-lookup"><span data-stu-id="0f5da-321">You will be prompted to remove each individual request from the queue.</span></span> <span data-ttu-id="0f5da-322">Respond as needed.</span><span class="sxs-lookup"><span data-stu-id="0f5da-322">Respond as needed.</span></span>
    
### <a name="pst-import-option-b-for-exchange-online"></a><span data-ttu-id="0f5da-323">PST-Import, Option B, für Exchange Online</span><span class="sxs-lookup"><span data-stu-id="0f5da-323">PST import option B, for Exchange Online</span></span>

- <span data-ttu-id="0f5da-324">Wenn Sie die gesammelten PST-Dateien in Exchange Online platzieren möchten, führen Sie die Verfahren im Ordner "Importieren von Dateien in Microsoft 365 über [Netzwerk Upload](https://docs.microsoft.com/microsoft-365/compliance/use-network-upload-to-import-pst-files)" aus.</span><span class="sxs-lookup"><span data-stu-id="0f5da-324">To place the collected PST files into Exchange Online, follow the procedures in the Import files into Microsoft 365 through [network upload](https://docs.microsoft.com/microsoft-365/compliance/use-network-upload-to-import-pst-files).</span></span>
    
### <a name="move-to-cold-storage"></a><span data-ttu-id="0f5da-325">Verschieben in Cold Storage</span><span class="sxs-lookup"><span data-stu-id="0f5da-325">Move to cold storage</span></span>

1. <span data-ttu-id="0f5da-326">Führen Sie die **das movetocoldstorage** -Runbook mithilfe der Verfahren in [Ausführen von Runbooks](https://go.microsoft.com/fwlink/p/?LinkId=615123)aus.</span><span class="sxs-lookup"><span data-stu-id="0f5da-326">Run the **MoveToColdStorage** runbook using the procedures in [Running Runbooks](https://go.microsoft.com/fwlink/p/?LinkId=615123).</span></span>
    
2. <span data-ttu-id="0f5da-327">Watch the Azure file share you are using for long term storage, for example \\\\AZFile1\\ContentColdStorage and the on-premises collection file share, for example \\\\Staging\\cases$.</span><span class="sxs-lookup"><span data-stu-id="0f5da-327">Watch the Azure file share you are using for long term storage, for example \\\\AZFile1\\ContentColdStorage and the on-premises collection file share, for example \\\\Staging\\cases$.</span></span> <span data-ttu-id="0f5da-328">You should see the files and folders appear in the cold storage file share and disappear from the collection file share.</span><span class="sxs-lookup"><span data-stu-id="0f5da-328">You should see the files and folders appear in the cold storage file share and disappear from the collection file share.</span></span>
    
### <a name="ediscovery"></a><span data-ttu-id="0f5da-329">eDiscovery</span><span class="sxs-lookup"><span data-stu-id="0f5da-329">eDiscovery</span></span>

1. <span data-ttu-id="0f5da-330">Either allow the full crawl of the cold storage file share to run as schedules, or initiate a crawl.</span><span class="sxs-lookup"><span data-stu-id="0f5da-330">Either allow the full crawl of the cold storage file share to run as schedules, or initiate a crawl.</span></span> <span data-ttu-id="0f5da-331">For more information on starting full or incremental crawls, see [Start, pause, resume, or stop a crawl in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615005).</span><span class="sxs-lookup"><span data-stu-id="0f5da-331">For more information on starting full or incremental crawls, see [Start, pause, resume, or stop a crawl in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615005).</span></span>
    
2. <span data-ttu-id="0f5da-332">Erstellen Sie einen eDiscovery-Fall in SharePoint 2013, wenn Sie Option A für den PST-Dateiimport verwendet haben, oder erstellen Sie einen eDiscovery-Fall in SharePoint Online, wenn Sie Option B verwendet haben.</span><span class="sxs-lookup"><span data-stu-id="0f5da-332">Create an eDiscovery case in SharePoint 2013 if you used option A for a PST file import or create an eDiscovery case in SharePoint Online if you used option B.</span></span>
    

