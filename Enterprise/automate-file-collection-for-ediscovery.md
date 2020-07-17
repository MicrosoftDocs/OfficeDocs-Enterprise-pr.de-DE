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
# <a name="automate-file-collection-for-ediscovery"></a><span data-ttu-id="ba90b-103">Automatisieren der Dateisammlung für eDiscovery</span><span class="sxs-lookup"><span data-stu-id="ba90b-103">Automate file collection for eDiscovery</span></span>

<span data-ttu-id="ba90b-p101">Alle Unternehmen können sich Rechtsstreitigkeiten oder anderen Arten von Rechtsverfahren gegenübersehen. Zwar bemühen sich Rechtsabteilungen darum, dieses Risiko zu senken, jedoch sind Rechtsstreitigkeiten ein Bestandteil des Geschäftslebens. Wenn sich ein Unternehmen einem Rechtsverfahren gegenübersieht, muss es dem Gericht und dem gegnerischen Anwalt durch Legal Discovery alle relevanten Dokumente zur Verfügung stellen.</span><span class="sxs-lookup"><span data-stu-id="ba90b-p101">All companies face the potential of lawsuits or other types of legal action. While legal departments work to reduce that exposure, litigation is a fact of business life. When a company faces legal action, they are required, through the process of legal discovery, to provide all relevant documentary materials to the court and to opposing counsel.</span></span> 
  
<span data-ttu-id="ba90b-p102">eDiscovery ist der Prozess, durch den Unternehmen die relevanten Dokumente, die im elektronischen Format vorliegen, erfassen, durchsuchen, identifizieren, aufbewahren, filtern und zur Verfügung stellen. SharePoint 2013, Exchange Server 2013, Lync Server 2013, SharePoint Online und Exchange Online können große Mengen an Inhalten aufweisen. Je nach Version können diese Produkte eDiscovery und In-Situ-Speicher unterstützen (Lync über Exchange Server), was Rechtsabteilungen dabei hilft, die für einen bestimmten Fall wichtigsten Inhalte zu indizieren, zu identifizieren, zu archivieren und zu filtern.</span><span class="sxs-lookup"><span data-stu-id="ba90b-p102">eDiscovery is the process by which companies inventory, search, identify, preserve, filter, and make available the relevant documentary materials that exist in electronic form. SharePoint 2013, Exchange Server 2013, Lync Server 2013, SharePoint Online, and Exchange Online can hold large amounts of documentary content. Depending on the version, these products may support eDiscovery and in place holds (Lync via Exchange Server), making it easier for the legal teams to index, identify, hold, and filter the most relevant content for a given case.</span></span>
  
<span data-ttu-id="ba90b-p103">Viele Dokumente werden auf den lokalen Computern der Benutzer (Verwalter) gespeichert und nicht an einem zentralen Ort. Dadurch wird es SharePoint 2013 im Prinzip unmöglich gemacht, zu suchen, und was nicht durchsucht werden kann, kann auch nicht in eDiscovery einbezogen werden. Diese Lösung zeigt Ihnen, wie Anmeldeskripts, System Center Orchestrator 2012 R2 und Windows PowerShell für Exchange Server verwendet werden, um die Identifizierung und Sammlung von Dokumenten von Benutzercomputern zu automatisieren.</span><span class="sxs-lookup"><span data-stu-id="ba90b-p103">Many documents are stored on users' (Custodians) local computers, not in a centralized location. This makes it essentially impossible for SharePoint 2013 to search, and if it can't be searched, it can't be included in eDiscovery. This solution shows you how to use logon scripts, System Center Orchestrator 2012 R2 and Windows PowerShell for Exchange Server to automate the identification and collection of documentary materials from users' computers.</span></span>
  
## <a name="what-this-solution-does"></a><span data-ttu-id="ba90b-113">Funktionsweise dieser Lösung</span><span class="sxs-lookup"><span data-stu-id="ba90b-113">What this solution does</span></span>

<span data-ttu-id="ba90b-p104">Diese Lösung verwendet eine globale Sicherheitsgruppe, eine Gruppenrichtlinie und ein Windows PowerShell-Skript zum Auffinden, Inventarisieren und Erfassen von Inhalten und persönlichen Speicherdateien (Personal Storage Files, PST) von Outlook von lokalen Computern von Benutzern in einer verborgenen Dateifreigabe. Von dort können die PST-Dateien entweder in Exchange Server 2013 oder Exchange Online importiert werden. Alle Dateien werden dann anhand eines System Center Orchestrator 2012 R2-Runbooks zwecks langfristiger Speicherung und Indizierung durch SharePoint 2013 zu einer anderen Dateifreigabe in Microsoft Azure verschoben. Sie verwenden dann eDiscovery-Zentren in der lokalen SharePoint Online-Bereitstellung oder in SharePoint Online, wie Sie es regelmäßig zur Durchführung von eDiscovery tun.</span><span class="sxs-lookup"><span data-stu-id="ba90b-p104">This solution uses a global security group, Group Policy, and a Windows PowerShell script to locate, inventory, and collect content and Outlook personal store (PST) files from users local computers to a hidden file share. From there, the PST files can be imported into either Exchange Server 2013 or Exchange Online. All files are then moved using a System Center Orchestrator 2012 R2 runbook to another file share in Microsoft Azure for long-term storage and indexing by SharePoint 2013. You then use eDiscovery centers in your on-premises SharePoint 2013 deployment or in SharePoint Online as you regularly would to perform eDiscovery.</span></span> 
  
> [!IMPORTANT]
> <span data-ttu-id="ba90b-p105">Diese Lösung verwendet Robocopy, um Dateien auf den Computern von Verwaltern auf eine zentrale Dateifreigabe zu kopieren. Da Robocopy keine geöffneten oder gesperrten Dateien kopiert, werden alle Dateien, einschließlich PST-Dateien, die der Verwalter geöffnet hat, nicht erfasst. Diese müssen manuell erfasst werden. Diese Lösung stellt eine Liste bereit, in der explizit die Dateien, die nicht kopiert werden können, sowie der vollständige Pfad zu den einzelnen Dateien identifiziert werden.</span><span class="sxs-lookup"><span data-stu-id="ba90b-p105">This solution uses robocopy to copy files from custodian's computers to a centralized file share. Because robocopy does not copy files that are open or locked, any files, including PST files, that the custodian has open will not be collected. You will have to collect them manually. This solution does provide you with a list that explicitly identifies the files it cannot copy and the full path to each file.</span></span> 
  
<span data-ttu-id="ba90b-122">Das folgende Diagramm führt Sie durch alle Schritte und Elemente der Lösung.</span><span class="sxs-lookup"><span data-stu-id="ba90b-122">The following diagram walks you through all the steps and elements of the solution.</span></span>
  
![Übersicht über die automatische Dateierfassungslösung](media/dbb447b5-c74c-4956-986c-10a1d047ac99.png)
  
|<span data-ttu-id="ba90b-124">\*\*\*\*Legende\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="ba90b-124">\*\*\*\*Legend\*\*\*\*</span></span>||
|:-----|:-----|
|![Magenta-Beschriftung 1](media/000026a3-2bf0-4678-b468-ccb5f81da6f1.png)|<span data-ttu-id="ba90b-126">Erstellen Sie ein Gruppenrichtlinienobjekt (Group Policy Object, GPO), und ordnen Sie es dem Sammlungsanmeldeskript zu.</span><span class="sxs-lookup"><span data-stu-id="ba90b-126">Create a Group Policy object (GPO), and associate it with the collection logon script.</span></span>  <br/> |
|![Magenta-Beschriftung 2](media/a31b11e2-3597-42a4-933e-b6af11ed6ef1.png)| <span data-ttu-id="ba90b-128">Konfigurieren Sie den GPO-Sicherheitsfilter, um das GPO nur auf die Gruppe der Verwalter anzuwenden.</span><span class="sxs-lookup"><span data-stu-id="ba90b-128">Configure the GPO security filter to apply the GPO only to the Custodians group.</span></span> <br/> |
|![Magenta-Beschriftung 3](media/3ced060c-daec-460d-a9b5-260a3dfcae36.png)|<span data-ttu-id="ba90b-130">Ein Verwalter meldet sich an, und das GPO wird ausgeführt und ruft das Sammlungsanmeldeskript auf.</span><span class="sxs-lookup"><span data-stu-id="ba90b-130">A Custodian logs on and the GPO runs, calling the collection logon script.</span></span>  <br/> |
|![Magenta-Beschriftung 4](media/6f269d84-2559-49e3-b18e-af6ac94d0419.png)|<span data-ttu-id="ba90b-132">Das Sammlungsanmeldeskript inventarisiert alle lokal verbundenen Laufwerke auf dem Computer des Verwalters, indem es nach den gewünschten Dateien sucht und ihren Speicherort aufzeichnet.</span><span class="sxs-lookup"><span data-stu-id="ba90b-132">The collection logon script inventories all locally attached drives on the Custodians computer, searching for the files you want, and recording their location.</span></span>  <br/> |
|![Magenta-Beschriftung 5](media/4bf8898c-44ad-4524-b983-70175804eb85.png)|<span data-ttu-id="ba90b-134">Das Sammlungsanmeldeskript kopiert die inventarisierten Dateien in eine verborgene Dateifreigabe auf dem Staging Server.</span><span class="sxs-lookup"><span data-stu-id="ba90b-134">The collection logon script copies the inventoried files to a hidden file share on the staging server.</span></span>  <br/> |
|![Magenta-Beschriftung 6](media/99589726-0c7e-406b-a276-44301a135768.png)| <span data-ttu-id="ba90b-136">(Option A) Führen Sie das PST-Importskript manuell aus, um die gesammelten PST-Dateien in Exchange Server 2013 zu importieren.</span><span class="sxs-lookup"><span data-stu-id="ba90b-136">(Option A) Manually run the PST import script to import the collected PST files into Exchange Server 2013.</span></span> <br/> |
|![Magenta-Beschriftung 7](media/ff15e89c-d2fd-4614-9838-5e18287d578b.png)|<span data-ttu-id="ba90b-138">(Option B) Importieren Sie die gesammelten PST-Dateien mithilfe des Microsoft 365-Importtools und-Prozesses in Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="ba90b-138">(Option B) Using the Microsoft 365 Import tool and process, import the collected PST files into Exchange Online.</span></span>  <br/> |
|![Magenta-Beschriftung 8](media/aaf3bd3d-9508-4aaf-a3af-44ba501da63a.png)|<span data-ttu-id="ba90b-140">Verschieben Sie alle gesammelten Dateien zur langfristigen Speicherung mit dem MoveToColdStorageSystem Center Orchestrator 2012 R2-Runbook in eine Azure-Dateifreigabe.</span><span class="sxs-lookup"><span data-stu-id="ba90b-140">Move all collected files to an Azure file share for long term storage with the MoveToColdStorage System Center Orchestrator 2012 R2 runbook.</span></span> <br/> |
|![Magenta-Beschriftung 9](media/b354642e-445e-4723-a84a-b41f7ac6e774.png)|<span data-ttu-id="ba90b-142">Indexieren Sie die Dateien in der Cold Storage-Dateifreigabe mit SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="ba90b-142">Index the files in the cold storage file share with SharePoint 2013.</span></span>  <br/> |
|![Magenta-Beschriftung 10](media/cebf7de5-7525-413b-9e52-638a4f8b2f74.png)|<span data-ttu-id="ba90b-144">Führen Sie eDiscovery für Inhalte in Cold Storage und im lokalen Exchange Server 2013 durch.</span><span class="sxs-lookup"><span data-stu-id="ba90b-144">Perform eDiscovery on content in cold storage and in the on-premises Exchange Server 2013.</span></span>  <br/> |
|![Magenta-Beschriftung 11](media/e59ab403-2f19-497a-92a5-549846dded66.png)|<span data-ttu-id="ba90b-146">Ausführen von eDiscovery für Inhalte in Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="ba90b-146">Perform eDiscovery on content in Microsoft 365.</span></span>  <br/> |
   
## <a name="prerequisites"></a><span data-ttu-id="ba90b-147">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="ba90b-147">Prerequisites</span></span>

<span data-ttu-id="ba90b-p106">Die Konfiguration dieser Lösung erfordert viele Elemente, von denen die meisten wahrscheinlich für eDiscovery vorhanden und konfiguriert sind. Für Elemente, die Sie nicht besitzen oder für die eine spezifische Konfiguration erforderlich ist, stellen wir Ihnen Links zur Verfügung, anhand derer Sie die Standardkonfiguration vornehmen können. Vor der Konfiguration der Lösung selbst, muss die Standardkonfiguration stehen.</span><span class="sxs-lookup"><span data-stu-id="ba90b-p106">The configuration of this solution requires many elements, most of which you likely have in place and configured if you're thinking about eDiscovery. For the elements that you may not have or ones that require a specific configuration, we'll provide you with the links you need build out your base configuration. You must have the base configuration in place before you configure the solution itself.</span></span>
  
### <a name="base-configuration"></a><span data-ttu-id="ba90b-151">Standardkonfiguration</span><span class="sxs-lookup"><span data-stu-id="ba90b-151">Base configuration</span></span>

|<span data-ttu-id="ba90b-152">**Element**</span><span class="sxs-lookup"><span data-stu-id="ba90b-152">**Element**</span></span>|<span data-ttu-id="ba90b-153">**Link**</span><span class="sxs-lookup"><span data-stu-id="ba90b-153">**Link**</span></span>|
|:-----|:-----|
|<span data-ttu-id="ba90b-154">Active Directory-Domänendienste (AD DS)-Domäne</span><span class="sxs-lookup"><span data-stu-id="ba90b-154">Active Directory Domain Services (AD DS) domain</span></span>  <br/> ||
|<span data-ttu-id="ba90b-155">Internetkonnektivität von Ihrem lokalen Netzwerk aus</span><span class="sxs-lookup"><span data-stu-id="ba90b-155">Internet connectivity from your on-premises network</span></span>  <br/> ||
|<span data-ttu-id="ba90b-156">SQL Server 2012 zur Unterstützung von SharePoint 2013 und System Center Orchestrator 2012 R2</span><span class="sxs-lookup"><span data-stu-id="ba90b-156">SQL Server 2012 to support SharePoint 2013 and System Center Orchestrator 2012 R2</span></span>  <br/> |[<span data-ttu-id="ba90b-157">Bereitstellen von System Center 2012 - Orchestrator</span><span class="sxs-lookup"><span data-stu-id="ba90b-157">Deploying System Center Orchestrator - 2012</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=613503) <br/> |
| <span data-ttu-id="ba90b-158">(lokal oder Azure-basiert) für (erforderlich für Option A)</span><span class="sxs-lookup"><span data-stu-id="ba90b-158">On-premises or Azure based SharePoint 2013 for eDiscovery (required for Option A)</span></span> <br/> ||
|<span data-ttu-id="ba90b-159">Lokaler Dateifreigabenserver für Staging</span><span class="sxs-lookup"><span data-stu-id="ba90b-159">On-premises file share server for staging</span></span>  <br/> ||
|<span data-ttu-id="ba90b-160">Lokaler Exchange Server 2013 für PST-Import aus Option A</span><span class="sxs-lookup"><span data-stu-id="ba90b-160">On-premises Exchange Server 2013 for Option A PST import</span></span>  <br/> |<span data-ttu-id="ba90b-161">CU5 (15.913.22) ist verfügbar unter [CU5](https://go.microsoft.com/fwlink/p/?LinkId=613426).</span><span class="sxs-lookup"><span data-stu-id="ba90b-161">CU5 (15.913.22) is available at [CU5](https://go.microsoft.com/fwlink/p/?LinkId=613426).</span></span>  <br/> |
|<span data-ttu-id="ba90b-162">System Center Orchestrator 2012 R2</span><span class="sxs-lookup"><span data-stu-id="ba90b-162">System Center Orchestrator 2012 R2</span></span>  <br/> |[<span data-ttu-id="ba90b-163">Bereitstellen von System Center 2012 - Orchestrator</span><span class="sxs-lookup"><span data-stu-id="ba90b-163">Deploying System Center Orchestrator - 2012</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=613503) <br/> |
|<span data-ttu-id="ba90b-164">Microsoft 365 E3 mit Exchange Online und SharePoint Online (für Option B erforderlich)</span><span class="sxs-lookup"><span data-stu-id="ba90b-164">Microsoft 365 E3 with Exchange Online and SharePoint Online (required for Option B)</span></span>  <br/> |<span data-ttu-id="ba90b-165">Informationen zum Registrieren eines Microsoft 365 E3-Abonnements finden Sie unter [Microsoft 365 E3-Abonnement](https://www.microsoft.com/microsoft-365/enterprise-e3-business-software?activetab=pivot%3aoverviewtab).</span><span class="sxs-lookup"><span data-stu-id="ba90b-165">To sign up for a Microsoft 365 E3 subscription, see [Microsoft 365 E3 subscription](https://www.microsoft.com/microsoft-365/enterprise-e3-business-software?activetab=pivot%3aoverviewtab).</span></span>  <br/> |
|<span data-ttu-id="ba90b-166">Azure-Abonnement mit einem virtuellen Computer</span><span class="sxs-lookup"><span data-stu-id="ba90b-166">Azure subscription with a virtual machine</span></span>  <br/> |<span data-ttu-id="ba90b-167">Informationen zum Registrieren für ein Azure-Abonnement finden Sie unter [Anmelden bei Windows Azure](https://go.microsoft.com/fwlink/p/?LinkId=512010).</span><span class="sxs-lookup"><span data-stu-id="ba90b-167">To sign up for a Azure, see [Subscribe to Windows Azure](https://go.microsoft.com/fwlink/p/?LinkId=512010)</span></span> <br/> |
|<span data-ttu-id="ba90b-168">Eine VPN-Verbindung zwischen Ihrem lokalen Netzwerk und Ihrem Azure-Abonnement</span><span class="sxs-lookup"><span data-stu-id="ba90b-168">A VPN connection between your on-premises network and your Azure subscription</span></span>  <br/> |<span data-ttu-id="ba90b-169">Informationen zum Einrichten eines VPN-Tunnels zwischen Ihrem Azure-Abonnement und Ihrem lokalen Netzwerk finden Sie unter [Verbinden eines lokalen Netzwerks mit einem virtuellen Microsoft Azure-Netzwerk](https://go.microsoft.com/fwlink/p/?LinkId=613507).</span><span class="sxs-lookup"><span data-stu-id="ba90b-169">To set up a VPN tunnel between your Azure subscription and your on-premises network, see [Connect an on-premises network to a Microsoft Azure virtual network](https://go.microsoft.com/fwlink/p/?LinkId=613507).</span></span>  <br/> |
|<span data-ttu-id="ba90b-170">SharePoint 2013eDiscovery ist zum Durchsuchen von SharePoint und Exchange Server 2013 sowie optional Lync Server 2013 konfiguriert</span><span class="sxs-lookup"><span data-stu-id="ba90b-170">SharePoint 2013 eDiscovery configured to search across SharePoint and Exchange Server 2013 and optionally Lync Server 2013</span></span>  <br/> |<span data-ttu-id="ba90b-171">Informationen zum Konfigurieren von eDiscovery auf diese Weise finden Sie unter [Konfigurieren von eDiscovery in SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=613508) und[Testumgebungsanleitung: Konfigurieren von eDiscovery für eine Testumgebung mit Exchange-, Lync-, SharePoint- und Windows-Dateifreigaben](https://go.microsoft.com/fwlink/p/?LinkId=393130).</span><span class="sxs-lookup"><span data-stu-id="ba90b-171">To configure eDiscovery in this fashion, see [Configure eDiscovery in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=613508) and[Test Lab Guide: Configure eDiscovery for an Exchange, Lync, SharePoint and Windows File Shares Test Lab](https://go.microsoft.com/fwlink/p/?LinkId=393130).</span></span>  <br/> |
|<span data-ttu-id="ba90b-172">eDiscovery in Microsoft 365 für SharePoint Online und Exchange Online</span><span class="sxs-lookup"><span data-stu-id="ba90b-172">eDiscovery in Microsoft 365 for SharePoint Online and Exchange Online</span></span>  <br/> |<span data-ttu-id="ba90b-173">Informationen zum Konfigurieren von eDiscovery in Microsoft 365 finden Sie unter [Einrichten eines eDiscovery Centers in SharePoint Online](https://go.microsoft.com/fwlink/p/?LinkId=613628).</span><span class="sxs-lookup"><span data-stu-id="ba90b-173">To configure eDiscovery in Microsoft 365, see [Set up an eDiscovery Center in SharePoint Online](https://go.microsoft.com/fwlink/p/?LinkId=613628).</span></span>  <br/> |
   
## <a name="configure-the-environment"></a><span data-ttu-id="ba90b-174">Konfigurieren der Umgebung</span><span class="sxs-lookup"><span data-stu-id="ba90b-174">Configure the environment</span></span>

<span data-ttu-id="ba90b-175">Nachdem nun die Basiskonfiguration steht, können Sie mit der Konfiguration der eigentlichen Lösung fortfahren.</span><span class="sxs-lookup"><span data-stu-id="ba90b-175">Now that you have the base configuration in place, you can move ahead to configuring the solution itself.</span></span> 
  
### <a name="staging-file-share"></a><span data-ttu-id="ba90b-176">Staging-Dateifreigabe</span><span class="sxs-lookup"><span data-stu-id="ba90b-176">Staging file share</span></span>

1. <span data-ttu-id="ba90b-177">Erstellen Sie in der lokalen Domäne eine globale Sicherheitsgruppe mit dem Namen Custodians.</span><span class="sxs-lookup"><span data-stu-id="ba90b-177">In the on-premises domain, create a global security group named Custodians.</span></span>
    
2. <span data-ttu-id="ba90b-p107">Erstellen Sie eine verborgene Dateifreigabe für die Dateien, die auf den Computern von Verwaltern erfasst werden. Dabei sollte es sich um einen lokalen Server handeln. Erstellen Sie beispielsweise auf einem Server namens Staging eine Dateifreigabe mit dem Namen Cases$. Das **$** ist erforderlich, um eine verborgene Freigabe zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="ba90b-p107">Create a hidden file share for the files that are collected from Custodians computers. This should be on an on-premises server. For example, on a server called Staging, create a file share called Cases$. The **$** is required to make this a hidden share.</span></span>
    
3. <span data-ttu-id="ba90b-182">Legen Sie die folgenden Freigabeberechtigungen fest:</span><span class="sxs-lookup"><span data-stu-id="ba90b-182">Set the following share permissions:</span></span>
    
  - <span data-ttu-id="ba90b-183">Verwalter: Lesen, Ändern</span><span class="sxs-lookup"><span data-stu-id="ba90b-183">Custodians: Change, Read</span></span>
    
  - <span data-ttu-id="ba90b-184">Administratoren: Vollzugriff</span><span class="sxs-lookup"><span data-stu-id="ba90b-184">Administrators: Full Control</span></span>
    
  - <span data-ttu-id="ba90b-185">Vertrauenswürdiges Exchange-Teilsystem: Lesen, Ändern</span><span class="sxs-lookup"><span data-stu-id="ba90b-185">Exchange Trusted Subsystem: Change, Read</span></span>
    
4. <span data-ttu-id="ba90b-p108">Öffnen Sie die Registerkarte **Sicherheit**, fügen Sie die Gruppe der Verwalter hinzu, und klicken Sie auf **Erweitert**. Legen Sie die folgenden Berechtigungen für die Gruppe der Verwalter fest:</span><span class="sxs-lookup"><span data-stu-id="ba90b-p108">Open the **Security** tab, add the Custodians group, and click **Advanced**. Set the following permissions for the Custodians group:</span></span>
    
  - <span data-ttu-id="ba90b-188">**Typ: Verweigern**</span><span class="sxs-lookup"><span data-stu-id="ba90b-188">**Type: Deny**</span></span>
    
  - <span data-ttu-id="ba90b-189">**Gilt für: Diesen Ordner, Unterordner und Dateien**</span><span class="sxs-lookup"><span data-stu-id="ba90b-189">**Applies to: This folder, subfolders and files**</span></span>
    
5. <span data-ttu-id="ba90b-190">Klicken Sie auf **Erweiterte Berechtigungen**, und wählen Sie Folgendes aus:</span><span class="sxs-lookup"><span data-stu-id="ba90b-190">Click **Advanced Permissions** and select the following:</span></span>
    
  - <span data-ttu-id="ba90b-191">**Attribute lesen**</span><span class="sxs-lookup"><span data-stu-id="ba90b-191">**Read attributes**</span></span>
    
  - <span data-ttu-id="ba90b-192">**Erweiterte Attribute lesen**</span><span class="sxs-lookup"><span data-stu-id="ba90b-192">**Read extended attributes**</span></span>
    
  - <span data-ttu-id="ba90b-193">**Leseberechtigungen**</span><span class="sxs-lookup"><span data-stu-id="ba90b-193">**Read permissions**</span></span>
    
6. <span data-ttu-id="ba90b-194">Testen Sie den Zugriff auf die Dateifreigabe „Cases$“ folgendermaßen:</span><span class="sxs-lookup"><span data-stu-id="ba90b-194">Test access to the Cases$ file share by doing the following:</span></span>
    
1. <span data-ttu-id="ba90b-195">Fügen Sie der Gruppe „Verwalter“ einen Benutzer hinzu.</span><span class="sxs-lookup"><span data-stu-id="ba90b-195">Add a user to the Custodians group.</span></span>
    
2. <span data-ttu-id="ba90b-196">Platzieren Sie eine Datei im Ordner „Cases$“.</span><span class="sxs-lookup"><span data-stu-id="ba90b-196">Place a file in the Cases$ folder.</span></span>
    
3. <span data-ttu-id="ba90b-p109">Navigieren Sie als Benutzer zu dem Stagingserver, beispielsweise zur Freigabe \\\\Staging, um zu sehen, welche Freigaben verfügbar sind. Die Freigabe **Cases$** sollte nicht aufgeführt sein.</span><span class="sxs-lookup"><span data-stu-id="ba90b-p109">As the user, browse to the staging server, for example browse to the \\\\Staging share to see what shares are available. You shouldn't see the **Cases$** share listed.</span></span>
    
4. <span data-ttu-id="ba90b-p110">Geben Sie manuell den vollständigen Pfad zu der Freigabe „Cases$“ in Explorer ein. Dadurch sollte die Freigabe „Cases$“ geöffnet werden.</span><span class="sxs-lookup"><span data-stu-id="ba90b-p110">Manually type the full path to the Cases$ share into Explorer. This should open the Cases$ share.</span></span>
    
5. <span data-ttu-id="ba90b-p111">Versuchen Sie, die Datei zu öffnen, die Sie zuvor in der Freigabe platziert haben. Dies sollte fehlschlagen.</span><span class="sxs-lookup"><span data-stu-id="ba90b-p111">Try to open the file you previously placed in the share. This should fail.</span></span>
    
### <a name="logon-script"></a><span data-ttu-id="ba90b-203">Anmeldeskript</span><span class="sxs-lookup"><span data-stu-id="ba90b-203">Logon script</span></span>

1. <span data-ttu-id="ba90b-204">Kopieren Sie dieses Windows PowerShell-Skript, und fügen Sie es in Editor ein:</span><span class="sxs-lookup"><span data-stu-id="ba90b-204">Copy and paste this Windows PowerShell script into Notepad:</span></span>
    
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

2. <span data-ttu-id="ba90b-205">Speichern Sie das Skript unter CollectionScript.ps1 an einem für Sie leicht auffindbaren Speicherort, z. B. C:\\AFCScripts.</span><span class="sxs-lookup"><span data-stu-id="ba90b-205">Save the above script as CollectionScript.ps1 in a location that's easy for you to find, for example, C:\\AFCScripts.</span></span>
    
3. <span data-ttu-id="ba90b-p112">Verwenden Sie die Funktion „Gehe zu...“ in Editor, und nehmen Sie bei Bedarf die folgenden Änderungen vor:</span><span class="sxs-lookup"><span data-stu-id="ba90b-p112">Use the Go To feature in Notepad. Make the following changes, as needed:</span></span>
    
|<span data-ttu-id="ba90b-208">**Zeilennummer**</span><span class="sxs-lookup"><span data-stu-id="ba90b-208">**Line #**</span></span>|<span data-ttu-id="ba90b-209">**Zu änderndes Element**</span><span class="sxs-lookup"><span data-stu-id="ba90b-209">**What you need to change**</span></span>|<span data-ttu-id="ba90b-210">**Erforderlich/optional**</span><span class="sxs-lookup"><span data-stu-id="ba90b-210">**Required/optional**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="ba90b-211">71</span><span class="sxs-lookup"><span data-stu-id="ba90b-211">71</span></span>  <br/> |<span data-ttu-id="ba90b-p113">**$FileTypes** -Variable. Beziehen Sie alle Dateityperweiterungen ein, die das Skript inventarisieren und in der Matrixvariable sammeln soll.</span><span class="sxs-lookup"><span data-stu-id="ba90b-p113">**$FileTypes** variable. Include all the file type extensions that you want the script to inventory and collect in the array variable. </span></span><br/> |<span data-ttu-id="ba90b-214">Optional</span><span class="sxs-lookup"><span data-stu-id="ba90b-214">Optional</span></span>  <br/> |
|<span data-ttu-id="ba90b-215">76 und 77</span><span class="sxs-lookup"><span data-stu-id="ba90b-215">76 and 77</span></span>  <br/> |<span data-ttu-id="ba90b-p114">Ändern Sie die Auslegung der **$CaseNo** -Variable entsprechend Ihren Anforderungen. Das Skript erfasst das aktuelle Datum und die aktuelle Uhrzeit und fügt den Benutzernamen an.</span><span class="sxs-lookup"><span data-stu-id="ba90b-p114">Change the way the **$CaseNo** variable is built to suit your needs. The script captures the current date and time and appends the user name to it. </span></span><br/> |<span data-ttu-id="ba90b-218">Optional</span><span class="sxs-lookup"><span data-stu-id="ba90b-218">Optional</span></span>  <br/> |
|<span data-ttu-id="ba90b-219">80</span><span class="sxs-lookup"><span data-stu-id="ba90b-219">80</span></span>  <br/> |<span data-ttu-id="ba90b-220">Die **$CaseRootLocation** -Variable muss auf die Sammlungsdateifreigabe Ihrer Stagingserver festgelegt werden. Beispielsweise **\\\\Staging\\Cases$**. </span><span class="sxs-lookup"><span data-stu-id="ba90b-220">**$CaseRootLocation** variable needs to be set to your staging servers collection file share, for example **\\\\Staging\\Cases$**.</span></span> <br/> |<span data-ttu-id="ba90b-221">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="ba90b-221">Required</span></span>  <br/> |
   
4. <span data-ttu-id="ba90b-222">Platzieren Sie die Datei „CollectionScript.ps1“ in die Netlogon-Dateifreigabe auf einem Domänencontroller.</span><span class="sxs-lookup"><span data-stu-id="ba90b-222">Place the CollectionScript.ps1 file in the Netlogon file share on a domain controller.</span></span> 
    
### <a name="configure-gpo-for-the-logon-script-and-custodians-group"></a><span data-ttu-id="ba90b-223">Konfigurieren des Gruppenrichtlinienobjekts für das Anmeldeskript und die Verwaltergruppe</span><span class="sxs-lookup"><span data-stu-id="ba90b-223">Configure GPO for the logon script and Custodians Group</span></span>

1. <span data-ttu-id="ba90b-224">Konfigurieren Sie ein Anmeldeskript für die Gruppe „Verwalter", indem Sie die Schritte im Abschnitt „Zuweisen von Benutzeranmeldeskripts" im Thema [Verwenden von Skripts zum Starten, Herunterfahren, Anmelden und Abmelden in der Gruppenrichtlinie](https://go.microsoft.com/fwlink/p/?LinkId=614844) befolgen.</span><span class="sxs-lookup"><span data-stu-id="ba90b-224">Configure a logon script for the Custodians group by following the "How to assign user logon scripts" section in the topic, [Using Startup, Shutdown, Logon, and Logoff Scripts in Group Policy](https://go.microsoft.com/fwlink/p/?LinkId=614844).</span></span>
    
2. <span data-ttu-id="ba90b-225">Entfernen Sie authentifizierte Benutzer aus der **Sicherheitsfilterung**, und fügen Sie die Verwaltergruppe hinzu.</span><span class="sxs-lookup"><span data-stu-id="ba90b-225">Remove authenticated users from **Security Filtering**, and add the Custodians group.</span></span>
    
### <a name="pst-import-option-a-script-for-exchange-server-2013"></a><span data-ttu-id="ba90b-226">PST-Import, Option A, Skript für Exchange Server 2013</span><span class="sxs-lookup"><span data-stu-id="ba90b-226">PST import Option A, script for Exchange Server 2013</span></span>

1.  <span data-ttu-id="ba90b-227">Kopieren Sie das folgende Windows PowerShell-Skript, und fügen Sie es in Editor ein:</span><span class="sxs-lookup"><span data-stu-id="ba90b-227">Copy and paste the following Windows PowerShell script into Notepad:</span></span>
    
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

2. <span data-ttu-id="ba90b-p115">Speichern Sie das Skript unter PSTImportScript.ps1 an einem für Sie leicht auffindbaren Speicherort. Erstellen Sie beispielsweise der Einfachheit halber einen Ordner auf Ihrem Stagingserver mit dem Namen\\\\Staging\\AFCScripts, und speichern Sie es dort.</span><span class="sxs-lookup"><span data-stu-id="ba90b-p115">Save the script as PSTImportScript.ps1 in a location that's easy for you to find. For example and ease of use, create a folder on your staging server called \\\\Staging\\AFCScripts, and save it there.</span></span>
    
3. <span data-ttu-id="ba90b-230">Verwenden Sie die Funktion „Gehe zu...“ in Editor, und nehmen Sie bei Bedarf die folgenden Änderungen vor:</span><span class="sxs-lookup"><span data-stu-id="ba90b-230">Use the Go To feature in Notepad, and make the following changes, as needed:</span></span>
    
|<span data-ttu-id="ba90b-231">**Zeilennummer**</span><span class="sxs-lookup"><span data-stu-id="ba90b-231">**Line #**</span></span>|<span data-ttu-id="ba90b-232">**Zu änderndes Element**</span><span class="sxs-lookup"><span data-stu-id="ba90b-232">**What you need to change**</span></span>|<span data-ttu-id="ba90b-233">**Erforderlich/optional**</span><span class="sxs-lookup"><span data-stu-id="ba90b-233">**Required/optional**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="ba90b-234">12 </span><span class="sxs-lookup"><span data-stu-id="ba90b-234">12</span></span>  <br/> |<span data-ttu-id="ba90b-p116">**$FolderIdentifier** markiert die Postfachordner, in die PST-Dateien importiert werden. Ändern Sie dies bei Bedarf.</span><span class="sxs-lookup"><span data-stu-id="ba90b-p116">**$FolderIdentifier** tags the mailbox folders that PSTs are imported into. Change this if necessary. </span></span><br/> |<span data-ttu-id="ba90b-237">Optional</span><span class="sxs-lookup"><span data-stu-id="ba90b-237">Optional</span></span>  <br/> |
|<span data-ttu-id="ba90b-238">17 </span><span class="sxs-lookup"><span data-stu-id="ba90b-238">17</span></span>  <br/> |<span data-ttu-id="ba90b-239">**$ConnectionUri** muss auf Ihrem eigenen Server festgelegt sein.</span><span class="sxs-lookup"><span data-stu-id="ba90b-239">**$ConnectionUri** needs to be set to your own server.</span></span> <br/> <span data-ttu-id="ba90b-p117">> [!IMPORTANT]> Stellen Sie sicher, dass Ihre **$ConnectionUri** auf einen Speicherort „http://" und nicht „https://" zeigt. Mit „https://" funktioniert es nicht.</span><span class="sxs-lookup"><span data-stu-id="ba90b-p117">> [!IMPORTANT]> Make sure your **$ConnectionUri** points to a http location, not https. It won't work with https:.</span></span>          |<span data-ttu-id="ba90b-242">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="ba90b-242">Required</span></span>  <br/> |
   
4. <span data-ttu-id="ba90b-243">Stellen Sie sicher, dass das Exchange-Konto „Vertrauenswürdiges Teilsystem" Lese-, Schreib- und Ausführberechtigungen für die Freigabe \\\\Staging\\Cases$ aufweist.</span><span class="sxs-lookup"><span data-stu-id="ba90b-243">Verify that the Exchange Trusted Subsystem account has Read, Write, and Execute permissions to the \\\\Staging\\Cases$ share.</span></span>
    
5. <span data-ttu-id="ba90b-244">Das PST-Importskript erfordert die folgenden zwei Eingabeparameter:</span><span class="sxs-lookup"><span data-stu-id="ba90b-244">The PST import script requires the following two input parameters:</span></span>
    
  - <span data-ttu-id="ba90b-245">**$SourcePath** Der Speicherort der zu importierenden PST-Dateien, z. B. „\\\\Staging\\Cases$".</span><span class="sxs-lookup"><span data-stu-id="ba90b-245">**$SourcePath** The location of the PST files to be imported, for example \\\\Staging\\Cases$.</span></span>
    
  - <span data-ttu-id="ba90b-246">**$MailboxAlias** Der Alias des Zielpostfachs, in dem die importierten E-Mail-Elemente empfangen werden.</span><span class="sxs-lookup"><span data-stu-id="ba90b-246">**$MailboxAlias** The alias of the target mailbox that will receive the imported email items.</span></span>
    
6. <span data-ttu-id="ba90b-247">Wenn Sie beispielsweise alle PST-Dateien aus dem Pfad „\\Staging\Cases$“ in ein Postfach mit dem Alias „eDiscoveryMailbox“ importieren möchten, führen Sie das Skript wie folgt aus: `\\staging\AFCscripts\PSTImportScript.ps1 \\Staging\cases$ eDiscoveryMailbox`.</span><span class="sxs-lookup"><span data-stu-id="ba90b-247">For example, if you want to import all the PST files from the path \\Staging\Cases$ into a mailbox with the alias eDiscoveryMailbox, you would run the script like this `\\staging\AFCscripts\PSTImportScript.ps1 \\Staging\cases$ eDiscoveryMailbox`.</span></span>
    
### <a name="pst-import-option-b-for-exchange-online"></a><span data-ttu-id="ba90b-248">PST-Import, Option B, für Exchange Online</span><span class="sxs-lookup"><span data-stu-id="ba90b-248">PST Import Option B, for Exchange Online</span></span>

-  <span data-ttu-id="ba90b-p118">Erstellen Sie die Postfachstruktur, in der die importierten PST-Dateien platziert werden sollen. Weitere Informationen zum Erstellen eines Benutzerpostfachs in Exchange Online finden Sie unter[Erstellen von Benutzerpostfächern in Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=615118).</span><span class="sxs-lookup"><span data-stu-id="ba90b-p118">Create the mailbox structure to place the imported PST files into. For more information on how to create a user mailbox in Exchange Online, see[Create User Mailboxes in Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=615118).</span></span>
    
### <a name="cold-storage"></a><span data-ttu-id="ba90b-251">Cold Storage</span><span class="sxs-lookup"><span data-stu-id="ba90b-251">Cold storage</span></span>

1. <span data-ttu-id="ba90b-252">Erstellen Sie eine Dateifreigabe auf dem Virtueller Azure-Computer, in der alle gesammelten Dateien platziert werden sollen, z. B. \\\\AZFile1\\ContentColdStorage.</span><span class="sxs-lookup"><span data-stu-id="ba90b-252">Create a file share on the Azure Virtual Machine, where all the collected files will be placed, for example, \\\\AZFile1\\ContentColdStorage.</span></span>
    
2. <span data-ttu-id="ba90b-p119">Gewähren Sie dem Standardkonto für den Inhaltszugriff mindestens Leseberechtigungen für die Freigabe und alle Unterordner und Dateien. Weitere Informationen zum Konfigurieren der SharePoint 2013-Suche finden Sie unter [Erstellen und Konfigurieren einer Suchdienstanwendung in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=614940).</span><span class="sxs-lookup"><span data-stu-id="ba90b-p119">Grant the default content access account at least Read permissions to the share and all subfolders and files. For more information about configuring SharePoint 2013 Search, see [Create and configure a Search service application in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=614940).</span></span>
    
3. <span data-ttu-id="ba90b-255">Wenn Sie beabsichtigen, PST-Dateien aus \\\\AZFile1\\ContentColdStorage zu importieren, gewähren Sie dem vertrauenswürdigen Teilsystem von Exchange Lese-, Schreib- und Ausführberechtigungen für die Freigabe.</span><span class="sxs-lookup"><span data-stu-id="ba90b-255">If you anticipate importing PST files from \\\\AZFile1\\ContentColdStorage, grant the Exchange Trusted Subsystem Read, Write, and Execute permissions to the share.</span></span>
    
### <a name="orchestrator"></a><span data-ttu-id="ba90b-256">Orchestrator</span><span class="sxs-lookup"><span data-stu-id="ba90b-256">Orchestrator</span></span>

1. <span data-ttu-id="ba90b-257">Laden Sie das [ MoveToColdStorage-Runbook](https://go.microsoft.com/fwlink/?LinkId=616095) aus dem Microsoft Download Center herunter.</span><span class="sxs-lookup"><span data-stu-id="ba90b-257">Download the[ MoveToColdStorage runbook](https://go.microsoft.com/fwlink/?LinkId=616095) from the Microsoft Download Center.</span></span>
    
2. <span data-ttu-id="ba90b-p120">Öffnen Sie den **Runbook Designer**, und klicken Sie im Bereich **Verbindungen** auf den Ordner, in den Sie das Runbook importieren möchten. Klicken Sie auf das Menü **Aktionen** und dann auf **Importieren**. Das Dialogfeld **Importieren** wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="ba90b-p120">Open the **Runbook Designer**, in the **Connections** pane, click the folder that you want to import the runbook into. Click the **Actions** menu, and the click **Import**. The **Import** dialog box appears.</span></span>
    
3. <span data-ttu-id="ba90b-261">Geben Sie im Feld **Dateispeicherort** den Pfad und Dateinamen des zu importierenden Runbooks ein, oder klicken Sie auf die drei Punkte ( **...**), um die zu importierende Datei zu suchen.</span><span class="sxs-lookup"><span data-stu-id="ba90b-261">In the **File Location** box, type the path and file name of the runbook you want to import, or click the ellipsis ( **...**) to browse to the file you want to import.</span></span> 
    
4. <span data-ttu-id="ba90b-p121">Wählen Sie **Runbooks importieren** und **Verschlüsselte Orchestrator-Daten importieren**. Deaktivieren Sie **Zähler**, **Zeitpläne**, **Variablen**, **Computergruppen**, **Globale Konfigurationen importieren** und **Vorhandene globale Konfigurationen überschreiben**.</span><span class="sxs-lookup"><span data-stu-id="ba90b-p121">Select **Import runbooks** and **Import Orchestrator encrypted data**. Clear **Counters**, **Schedules**, **Variables**, **Computer Groups**, **Import global configurations**, and **Overwrite existing global configurations**.</span></span>
    
5. <span data-ttu-id="ba90b-264">Klicken Sie auf **Fertig stellen**.</span><span class="sxs-lookup"><span data-stu-id="ba90b-264">Click **Finish**.</span></span>
    
6. <span data-ttu-id="ba90b-265">Bearbeiten Sie das Runbook **MoveFilesToColdStorage** wie folgt:</span><span class="sxs-lookup"><span data-stu-id="ba90b-265">Edit the **MoveFilesToColdStorage** runbook as follows:</span></span>
    
1. <span data-ttu-id="ba90b-p122">Aktivität **Datei verschieben** - Legen Sie den **Quelldatei**-Pfad auf die Sammlungsdateifreigabe fest, z. B. \\\\Staging\\cases$. Legen Sie den **Zielordner** auf die Cold Storage-Dateifreigabe in Azure fest, z. B. \\\\AZFile1\\ContentColdStorage. Wählen Sie **Datei mit eindeutigem Namen erstellen** aus.</span><span class="sxs-lookup"><span data-stu-id="ba90b-p122">**Move File** activity - set the **Source File** path to the collection file share, for example \\\\Staging\\cases$. Set the **Destination Folder** to the cold storage file share in Azure, for example \\\\AZFile1\\ContentColdStorage. Select **Create a file with a unique name**.</span></span>
    
2. <span data-ttu-id="ba90b-269">Aktivität **Ordner löschen** - Legen Sie **Pfad:** auf die Sammlungsdateifreigabe fest, z. B. \\\\Staging\\cases$\\*, und wählen Sie **Alle Dateien und Unterordner löschen**.</span><span class="sxs-lookup"><span data-stu-id="ba90b-269">**Delete Folder** activity - Set the **Path:** to the collection file share, for example \\\\Staging\\cases$\\*, and select **Delete all files and sub-folders**.</span></span> 
    
7. <span data-ttu-id="ba90b-270">Stellen Sie das Runbook **MoveToColdStorage** anhand der Verfahren unter[Bereitstellen von Runbooks](https://go.microsoft.com/fwlink/p/?LinkId=615120) bereit.</span><span class="sxs-lookup"><span data-stu-id="ba90b-270">Deploy the **MoveToColdStorage** runbook using the procedures in[Deploying Runbooks](https://go.microsoft.com/fwlink/p/?LinkId=615120).</span></span>
    
### <a name="sharepoint-on-premises-search-for-cold-storage"></a><span data-ttu-id="ba90b-271">Lokale SharePoint-Suche für Cold Storage</span><span class="sxs-lookup"><span data-stu-id="ba90b-271">SharePoint on-premises search for cold storage</span></span>

1. <span data-ttu-id="ba90b-p123">Erstellen Sie eine neue Inhaltsquelle in Ihrer SharePoint 2013-Farm für die Cold Storage-Freigabe in Azure, z. B. \\\\AZFile1\\ContentColdStorage. Weitere Informationen zum Verwalten von Inhaltsquellen finden Sie unter [Hinzufügen, Bearbeiten oder Löschen einer Inhaltsquelle in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615004).</span><span class="sxs-lookup"><span data-stu-id="ba90b-p123">Create an new content source in your SharePoint 2013 farm for the cold storage share in Azure, for example \\\\AZFile1\\ContentColdStorage. For more information about managing content sources, see [Add, edit, or delete a content source in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615004)</span></span>
    
2. <span data-ttu-id="ba90b-p124">Starten Sie eine vollständige Durchforstung. Weitere Informationen finden Sie unter [Starten, Unterbrechen, Fortsetzen oder Anhalten von Durchforstungen in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615005).</span><span class="sxs-lookup"><span data-stu-id="ba90b-p124">Start a full crawl. For more information see, [Start, pause, resume, or stop a crawl in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615005).</span></span>
    
## <a name="using-the-solution"></a><span data-ttu-id="ba90b-276">Verwenden der Lösung</span><span class="sxs-lookup"><span data-stu-id="ba90b-276">Using the solution</span></span>

<span data-ttu-id="ba90b-p125">Es gibt fünf wichtige Schritte bei der Verwendung dieser Lösung, vorausgesetzt, Sie möchten die PST-Dateien nicht sowohl in Exchange Server 2013 als auch Exchange Online importieren. Dieser Abschnitt enthält Informationen zu sämtlichen Verfahren. Die primäre Interaktion mit der Lösung besteht in Folgendem:</span><span class="sxs-lookup"><span data-stu-id="ba90b-p125">There are five major steps in using this solution, assuming you don't want to import the PST files into both Exchange Server 2013 and Exchange Online. This section provides you with the procedures for all of them. Your primary interaction with the solution will be in doing the following:</span></span>
  
1. <span data-ttu-id="ba90b-280">Verwalten Sie die Benutzermitgliedschaft in der Gruppe der Verwalter.</span><span class="sxs-lookup"><span data-stu-id="ba90b-280">Manage user membership in the Custodians group.</span></span>
    
2. <span data-ttu-id="ba90b-p126">Fehler</span><span class="sxs-lookup"><span data-stu-id="ba90b-p126">Review the log files generated by the logon script. The FileCopyErrors.log lists all the files that were not successfully copied. You need to decide what you want to do with them</span></span>
    
3. <span data-ttu-id="ba90b-284">Verwalten des PST-Importvorgangs.</span><span class="sxs-lookup"><span data-stu-id="ba90b-284">Managing the PST import process.</span></span>
    
4. <span data-ttu-id="ba90b-285">Verschieben der Sammlungsdateien in Cold Storage.</span><span class="sxs-lookup"><span data-stu-id="ba90b-285">Moving the collection files to cold storage.</span></span>
    
<span data-ttu-id="ba90b-286">Alle anderen Schritte sind nicht spezifisch für diese Lösung.</span><span class="sxs-lookup"><span data-stu-id="ba90b-286">All the other steps are not specific to this solution.</span></span> <span data-ttu-id="ba90b-287">Es handelt sich um Standard Verwaltungsaufgaben, die Sie in SharePoint 2013, Microsoft 365 und Azure ausführen.</span><span class="sxs-lookup"><span data-stu-id="ba90b-287">They are standard administrative tasks that you perform in SharePoint 2013, Microsoft 365, and Azure.</span></span> <span data-ttu-id="ba90b-288">Es gibt Elemente, für die diese Lösung keine Anleitungen bereitstellt, die Sie basierend auf den Anforderungen Ihres Unternehmens ausarbeiten müssen, beispielsweise:</span><span class="sxs-lookup"><span data-stu-id="ba90b-288">There are items that this solution does not provide any guidance that you will need to work out based on your company's needs, such as:</span></span>
  
1. <span data-ttu-id="ba90b-289">Überwachen Ihrer eDiscovery-Fälle und welche Verwalter welchen Fällen zugeordnet sind.</span><span class="sxs-lookup"><span data-stu-id="ba90b-289">Tracking your eDiscovery cases, and which Custodians are associated with which case.</span></span>
    
2. <span data-ttu-id="ba90b-290">Nachverfolgen, welche Gruppen von Dateisammlungen welchem eDiscovery-Fall zugeordnet sind.</span><span class="sxs-lookup"><span data-stu-id="ba90b-290">Tracking which sets of file collections are associate with which eDiscovery case.</span></span>
    
3. <span data-ttu-id="ba90b-291">Koordinieren des Timings des Imports und der Schritte für das Verschieben in Cold Storage.</span><span class="sxs-lookup"><span data-stu-id="ba90b-291">Coordinating the timing of the Import and move to cold storage steps.</span></span>
    
4. <span data-ttu-id="ba90b-292">Verwalten des in Azure verbrauchten Dateispeicherplatzes.</span><span class="sxs-lookup"><span data-stu-id="ba90b-292">Managing the file space used in Azure.</span></span>
    
5. <span data-ttu-id="ba90b-293">Verwalten der Postfächer, in die die PST-Dateien importiert werden.</span><span class="sxs-lookup"><span data-stu-id="ba90b-293">Managing the mailboxes that PSTs are imported into.</span></span>
    
6. <span data-ttu-id="ba90b-294">Sicherung und Wiederherstellung aller lokalen Daten.</span><span class="sxs-lookup"><span data-stu-id="ba90b-294">Backup and restoration of all on-premises data.</span></span>
    
### <a name="custodian-management"></a><span data-ttu-id="ba90b-295">Verwaltung von Verwaltern</span><span class="sxs-lookup"><span data-stu-id="ba90b-295">Custodian management</span></span>

- <span data-ttu-id="ba90b-p128">Um die automatische Dateisammlung für einen einzelnen Benutzer zu starten, fügen sie diese der Verwaltergruppe hinzu. Bei der nächsten Anmeldung des Benutzers wird das Anmeldeskript ausgeführt, dass der Verwaltergruppe über eine Gruppenrichtlinie zugewiesen wurde.</span><span class="sxs-lookup"><span data-stu-id="ba90b-p128">To start the automated file collection process for an individual user, add them to the Custodians group. The next time that the user logs on, the logon script assigned to the Custodians group through Group Policy will run.</span></span> 
    
### <a name="monitor-collected-files-and-review-log-files"></a><span data-ttu-id="ba90b-298">Überwachen der Dateiauflistung und Prüfen der Protokolldateien</span><span class="sxs-lookup"><span data-stu-id="ba90b-298">Monitor collected files and review log files</span></span>

1. <span data-ttu-id="ba90b-p129">Schauen Sie sich die Sammlungsdateifreigabe an, z. B.\\\\Staging\\cases$\\*, für den Sammlungsordner des Benutzers. Der Name des Ordners wird folgendermaßen formatiert:  *yyyyMMddHHmm_UserName*  .</span><span class="sxs-lookup"><span data-stu-id="ba90b-p129">Watch the collection file share, for example \\\\Staging\\cases$\\*, for the collection folder from the user. The name of the folder will be formatted like this:  *yyyyMMddHHmm_UserName*  .</span></span>
    
2. <span data-ttu-id="ba90b-p130">Wenn die Sammlung abgeschlossen ist, öffnen Sie den Sammlungsordner, und navigieren Sie zum Ordner _Log. Im Ordner _Log finden Sie Folgendes:</span><span class="sxs-lookup"><span data-stu-id="ba90b-p130">When the collection is completed, open the collection folder, and browse to the _Log folder. In the _Log folder, you will see the following:</span></span>
    
  - <span data-ttu-id="ba90b-p131">Eine XML-Datei für jedes lokale Laufwerk auf dem Computer des Benutzers, z. B. **A.xml**, **C.xml**. Diese Dateien enthalten die Bestandslaufwerke, nach denen sie benannt sind, und sie werden für den robocopy-Vorgang verwendet.</span><span class="sxs-lookup"><span data-stu-id="ba90b-p131">One XML file for every local drive on the user's computer, for example **A.xml**, **C.xml**. These files contain the inventory drives that they are named after, and they are used for the robocopy operation.</span></span>
    
    > [!NOTE]
    > <span data-ttu-id="ba90b-p132">Das Sammlungsskript erstellt nur für die Dateitypen einen Eintrag in der Bestandsdatei, die Sie im Skript selbst definiert haben. Es erstellt nicht für jede Datei auf dem Computer des Benutzers einen Bestandseintrag.</span><span class="sxs-lookup"><span data-stu-id="ba90b-p132">The collection script will only create an entry in the inventory file for the file types that you defined in the script itself. It will not create an inventory entry for every file on the user's computer.</span></span> 
  
  - <span data-ttu-id="ba90b-p133">Eine Protokolldatei mit dem Namen FileCopyErrors.log für jede Sammlungsausführung. Diese Datei enthält eine Auflistung der Dateien, die robocopy nicht in die Sammlungsdateifreigabe kopieren konnte, z. B. \\\\Staging\\cases$\\*. Sie müssen dies überprüfen und entscheiden, welche Aktionen für diese ausgelassenen Dateien ausgeführt werden sollen. In der Regel müssen Sie sie entweder manuell sammeln, wenn Sie sie benötigen, oder Sie entscheiden, dass sie nicht erforderlich sind und daher aus der Sammlung weggelassen werden können.</span><span class="sxs-lookup"><span data-stu-id="ba90b-p133">One log file named FileCopyErrors.log for each collection run. This file contains a listing of the files that robocopy could not copy to the file collection share, for example, \\\\Staging\\cases$\\*. You will need to review this and decide what actions to take for these missed files. Usually, you either need to collect them manually if you want them, or you may decide that they are not required and can therefore be omitted from the collection.</span></span>
    
### <a name="pst-import-option-a-for-exchange-server-2013"></a><span data-ttu-id="ba90b-311">PST-Import, Option A, für Exchange Server 2013</span><span class="sxs-lookup"><span data-stu-id="ba90b-311">PST import option A for Exchange Server 2013</span></span>

1. <span data-ttu-id="ba90b-p134">Melden Sie sich am Server an, der die Sammlungsdateifreigabe hostet, z. B. **Staging**, und öffnen Sie Windows PowerShell. Weitere Informationen zum Starten von Windows PowerShell finden Sie unter[Starting Windows PowerShell on Windows Server](https://go.microsoft.com/fwlink/p/?LinkId=615115).</span><span class="sxs-lookup"><span data-stu-id="ba90b-p134">Log on to the server that hosts the collection file share, for example **Staging**, and open Windows PowerShell. For more information about starting Windows PowerShell, see[Starting Windows PowerShell on Windows Server](https://go.microsoft.com/fwlink/p/?LinkId=615115).</span></span>
    
2. <span data-ttu-id="ba90b-p135">Legen Sie die Ausführungsrichtlinie auf uneingeschränkt fest. Geben Sie  `Set-ExecutionPolicy Unrestricted -Scope Process` in Windows PowerShell ein, und drücken Sie die EINGABETASTE.</span><span class="sxs-lookup"><span data-stu-id="ba90b-p135">Set the Execution policy to Unrestricted . Type  `Set-ExecutionPolicy Unrestricted -Scope Process` into Windows PowerShell, and press Enter.</span></span>
    
3. <span data-ttu-id="ba90b-p136">Führen Sie die Datei „PSTImportScript.ps1" aus, und geben Sie die Parameter **$SourcePath** und **$MailboxAlias** an. Weitere Informationen zum Ausführen von Windows PowerShell-Skripts finden Sie unter[Ausführen von Skripts](https://go.microsoft.com/fwlink/p/?LinkID=615117).</span><span class="sxs-lookup"><span data-stu-id="ba90b-p136">Run the PSTImportScript.ps1 file, and provide the **$SourcePath** and **$MailboxAlias** parameters. For more information about running Windows PowerShell scripts, see[Running Scripts](https://go.microsoft.com/fwlink/p/?LinkID=615117).</span></span>
    
4. <span data-ttu-id="ba90b-318">Überprüfen Sie die Ausgabe auf Fehler.</span><span class="sxs-lookup"><span data-stu-id="ba90b-318">Review the output for errors.</span></span>
    
5. <span data-ttu-id="ba90b-p137">Bevor Sie versuchen, eine gleichnamige PST-Datei in dasselbe Postfach zu importieren, müssen Sie die Anforderung für den Postfachimport entfernen. Führen Sie dazu den folgenden Befehl aus:  `Get-MailboxImportRequest | Remove-MailboxImportRequest`. Sie werden aufgefordert, jede einzelne Anforderung aus der Warteschlange zu entfernen. Reagieren Sie je nach Bedarf.</span><span class="sxs-lookup"><span data-stu-id="ba90b-p137">Before you attempt to import an identically named PST file into the same mailbox, you have to remove the mailbox import request. Run the following command to do that:  `Get-MailboxImportRequest | Remove-MailboxImportRequest`. You will be prompted to remove each individual request from the queue. Respond as needed.</span></span>
    
### <a name="pst-import-option-b-for-exchange-online"></a><span data-ttu-id="ba90b-323">PST-Import, Option B, für Exchange Online</span><span class="sxs-lookup"><span data-stu-id="ba90b-323">PST import option B, for Exchange Online</span></span>

- <span data-ttu-id="ba90b-324">Wenn Sie die gesammelten PST-Dateien in Exchange Online platzieren möchten, führen Sie die Verfahren im Ordner "Importieren von Dateien in Microsoft 365 über [Netzwerk Upload](https://docs.microsoft.com/microsoft-365/compliance/use-network-upload-to-import-pst-files)" aus.</span><span class="sxs-lookup"><span data-stu-id="ba90b-324">To place the collected PST files into Exchange Online, follow the procedures in the Import files into Microsoft 365 through [network upload](https://docs.microsoft.com/microsoft-365/compliance/use-network-upload-to-import-pst-files).</span></span>
    
### <a name="move-to-cold-storage"></a><span data-ttu-id="ba90b-325">Verschieben in Cold Storage</span><span class="sxs-lookup"><span data-stu-id="ba90b-325">Move to cold storage</span></span>

1. <span data-ttu-id="ba90b-326">Führen Sie die **das movetocoldstorage** -Runbook mithilfe der Verfahren in [Ausführen von Runbooks](https://go.microsoft.com/fwlink/p/?LinkId=615123)aus.</span><span class="sxs-lookup"><span data-stu-id="ba90b-326">Run the **MoveToColdStorage** runbook using the procedures in [Running Runbooks](https://go.microsoft.com/fwlink/p/?LinkId=615123).</span></span>
    
2. <span data-ttu-id="ba90b-p138">Schauen Sie sich die Azure-Dateifreigabe an, die Sie für die langfristige Speicherung verwenden, z. B. \\\\AZFile1\\ContentColdStorage, und die lokale Sammlungsdateifreigabe, z. B. \\\\Staging\\cases$. Die Dateien und Ordner sollten in der Cold Storage-Dateifreigabe eingeblendet und in der Sammlungsdateifreigabe ausgeblendet werden.</span><span class="sxs-lookup"><span data-stu-id="ba90b-p138">Watch the Azure file share you are using for long term storage, for example \\\\AZFile1\\ContentColdStorage and the on-premises collection file share, for example \\\\Staging\\cases$. You should see the files and folders appear in the cold storage file share and disappear from the collection file share.</span></span>
    
### <a name="ediscovery"></a><span data-ttu-id="ba90b-329">eDiscovery</span><span class="sxs-lookup"><span data-stu-id="ba90b-329">eDiscovery</span></span>

1. <span data-ttu-id="ba90b-p139">Lassen Sie entweder zu, dass die vollständige Durchforstung der Cold Storage-Dateifreigabe wie geplant ausgeführt wird, oder initiieren Sie eine Durchforstung. Weitere Informationen zum Starten vollständiger oder inkrementeller Durchforstungen finden Sie unter [Starten, Unterbrechen, Fortsetzen oder Anhalten von Durchforstungen in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615005).</span><span class="sxs-lookup"><span data-stu-id="ba90b-p139">Either allow the full crawl of the cold storage file share to run as schedules, or initiate a crawl. For more information on starting full or incremental crawls, see [Start, pause, resume, or stop a crawl in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615005).</span></span>
    
2. <span data-ttu-id="ba90b-332">Erstellen Sie einen eDiscovery-Fall in SharePoint 2013, wenn Sie Option A für den PST-Dateiimport verwendet haben, oder erstellen Sie einen eDiscovery-Fall in SharePoint Online, wenn Sie Option B verwendet haben.</span><span class="sxs-lookup"><span data-stu-id="ba90b-332">Create an eDiscovery case in SharePoint 2013 if you used option A for a PST file import or create an eDiscovery case in SharePoint Online if you used option B.</span></span>
    

