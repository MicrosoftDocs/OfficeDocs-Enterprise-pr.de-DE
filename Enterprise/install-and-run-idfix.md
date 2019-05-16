---
title: Installieren und Ausführen des Office 365 IdFix-Tools
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: get-started-article
f1_keywords:
- O365E_HRCSetupAADConnectIDFixLM617036
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
ms.assetid: f4bd2439-3e41-4169-99f6-3fabdfa326ac
description: Installieren und Ausführen des Office 365-IdFix-Tools zum Bereinigen Ihres Active Directory, bevor Sie es mit Office 365 synchronisieren.
ms.openlocfilehash: 4197694ce90ab600652aa729809ef0ddb0647e03
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "34067291"
---
# <a name="install-and-run-the-office-365-idfix-tool"></a><span data-ttu-id="394c2-103">Installieren und Ausführen des Office 365 IdFix-Tools</span><span class="sxs-lookup"><span data-stu-id="394c2-103">Install and run the Office 365 IdFix tool</span></span>

<span data-ttu-id="394c2-104">IdFix identifiziert Fehler wie Duplikate und Formatierungsprobleme in Ihrem Verzeichnis, bevor Sie mit Office 365 synchronisieren.</span><span class="sxs-lookup"><span data-stu-id="394c2-104">IdFix identifies errors such as duplicates and formatting problems in your directory before you synchronize to Office 365.</span></span> 
  
<span data-ttu-id="394c2-105">Damit Sie diese Aufgabe erfolgreich abschließen können, sollten Sie sich mit Benutzer-, Gruppen-und Kontaktobjekten in Active Directory vertraut machen.</span><span class="sxs-lookup"><span data-stu-id="394c2-105">To finish this task successfully, you should be comfortable working with user, group, and contact objects in Active Directory.</span></span>
  
<span data-ttu-id="394c2-106">Wenn Sie diese Aufgabe nicht abschließen können, gibt es einige andere Möglichkeiten.</span><span class="sxs-lookup"><span data-stu-id="394c2-106">If you can't complete this task, there are a couple of other things you can do.</span></span> <span data-ttu-id="394c2-107">Diese Methoden sind möglicherweise einfacher, aber Sie können auch länger dauern oder andere Nachteile haben.</span><span class="sxs-lookup"><span data-stu-id="394c2-107">These methods might be easier, but they might also take longer or have other drawbacks.</span></span> <span data-ttu-id="394c2-108">Dies sind:</span><span class="sxs-lookup"><span data-stu-id="394c2-108">They are:</span></span>
  
- <span data-ttu-id="394c2-109">**Führen Sie die Verzeichnissynchronisierung ohne Ausführen von IdFix aus.**</span><span class="sxs-lookup"><span data-stu-id="394c2-109">**Run directory synchronization without running IdFix.**</span></span> <span data-ttu-id="394c2-110">Sie können Ihr Verzeichnis synchronisieren, ohne das IdFix-Tool auszuführen, es wird jedoch nicht empfohlen.</span><span class="sxs-lookup"><span data-stu-id="394c2-110">You can synchronize your directory without running the IdFix tool, but we don't recommend it.</span></span> <span data-ttu-id="394c2-111">Das Beheben von Fehlern vor der Synchronisierung dauert schneller und bietet häufig einen reibungsloseren Übergang zur Cloud.</span><span class="sxs-lookup"><span data-stu-id="394c2-111">Fixing errors before you synchronize takes less time and often provides a smoother transition to the cloud.</span></span> 
- <span data-ttu-id="394c2-112">**Mieten Sie einen Berater.**</span><span class="sxs-lookup"><span data-stu-id="394c2-112">**Hire a consultant.**</span></span> <span data-ttu-id="394c2-113">Wenn Sie Experten helfen, können Sie Ihre Benutzer schnell einrichten, und Ihr Verzeichnis wird synchronisiert.</span><span class="sxs-lookup"><span data-stu-id="394c2-113">Getting expert help can get your users up and running quickly and your directory synchronized.</span></span> 
    
## <a name="what-you-need-to-run-idfix"></a><span data-ttu-id="394c2-114">Was Sie zum Ausführen von IdFix benötigen</span><span class="sxs-lookup"><span data-stu-id="394c2-114">What you need to run IdFix</span></span>

<span data-ttu-id="394c2-115">Am einfachsten können Sie IdFix auf einem Computer installieren, der mit Ihrer Domäne verbunden ist.</span><span class="sxs-lookup"><span data-stu-id="394c2-115">The easiest way to get IdFix up and running is to install it on a computer that is joined to your domain.</span></span> <span data-ttu-id="394c2-116">Sie können es auf dem Domänencontroller ausführen, aber es ist nicht erforderlich.</span><span class="sxs-lookup"><span data-stu-id="394c2-116">You can run it on the domain controller if you want, but it's not necessary.</span></span>
  
### <a name="idfix-hardware-requirements"></a><span data-ttu-id="394c2-117">IdFix-Hardwareanforderungen</span><span class="sxs-lookup"><span data-stu-id="394c2-117">IdFix hardware requirements</span></span>

<span data-ttu-id="394c2-118">Der Computer, auf dem Sie IdFix installieren, muss diese minimalen Hardwareanforderungen erfüllen:</span><span class="sxs-lookup"><span data-stu-id="394c2-118">The computer where you install IdFix needs to meet these minimum hardware requirements:</span></span>
  
- <span data-ttu-id="394c2-119">4 GB RAM </span><span class="sxs-lookup"><span data-stu-id="394c2-119">4 GB RAM</span></span>
- <span data-ttu-id="394c2-120">2 GB Festplattenspeicherplatz</span><span class="sxs-lookup"><span data-stu-id="394c2-120">2 GB of hard disk space</span></span>
    
### <a name="idfix-software-requirements"></a><span data-ttu-id="394c2-121">IdFix-Softwareanforderungen</span><span class="sxs-lookup"><span data-stu-id="394c2-121">IdFix software requirements</span></span>

<span data-ttu-id="394c2-122">Der Computer, auf dem Sie IdFix installieren, muss derselben Active Directory-Domäne hinzugefügt werden, von der Sie Benutzer mit Office 365 synchronisieren möchten.</span><span class="sxs-lookup"><span data-stu-id="394c2-122">The computer where you install IdFix needs to be joined to the same Active Directory domain from which you want to synchronize users to Office 365.</span></span> <span data-ttu-id="394c2-123">Auf dem Computer muss .NET Framework 4,0 installiert sein.</span><span class="sxs-lookup"><span data-stu-id="394c2-123">The computer also needs to have .NET Framework 4.0 installed.</span></span> 
  
<span data-ttu-id="394c2-124">Wenn Sie Windows Server 2008 oder Windows Server 2012, ist .NET Framework wahrscheinlich bereits installiert.</span><span class="sxs-lookup"><span data-stu-id="394c2-124">If you are running Windows Server 2008 or Windows Server 2012, then .NET Framework is probably already installed.</span></span> <span data-ttu-id="394c2-125">Ist dies nicht der Fall, können Sie [.NET 4,0 aus dem Download Center](https://go.microsoft.com/fwlink/p/?LinkId=400475) oder über Windows Update herunterladen.</span><span class="sxs-lookup"><span data-stu-id="394c2-125">If not, you can [download .NET 4.0 from the download center](https://go.microsoft.com/fwlink/p/?LinkId=400475) or via Windows Update.</span></span> 
  
### <a name="idfix-permissions-requirements"></a><span data-ttu-id="394c2-126">IdFix-Berechtigungsanforderungen</span><span class="sxs-lookup"><span data-stu-id="394c2-126">IdFix permissions requirements</span></span>

<span data-ttu-id="394c2-127">Das Benutzerkonto, mit dem Sie IdFix ausführen, muss Lese-/Schreibzugriff auf das Verzeichnis haben.</span><span class="sxs-lookup"><span data-stu-id="394c2-127">The user account that you use to run IdFix needs to have read/write access to the directory.</span></span>
  
<span data-ttu-id="394c2-128">Wenn Sie nicht sicher sind, ob Ihr Benutzerkonto diese Anforderungen erfüllt, und Sie nicht sicher sind, wie Sie überprüfen, können Sie IdFix installieren und ausführen.</span><span class="sxs-lookup"><span data-stu-id="394c2-128">If you aren't sure if your user account meets these requirements, and you're not sure how to check, you can still install and run IdFix.</span></span> <span data-ttu-id="394c2-129">Wenn Ihr Benutzerkonto nicht über die richtigen Berechtigungen verfügt, wird bei der Ausführung von IdFix nur ein Fehler angezeigt.</span><span class="sxs-lookup"><span data-stu-id="394c2-129">If your user account doesn't have the right permissions, IdFix will simply display an error when you try to run it.</span></span>
  
## <a name="install-idfix"></a><span data-ttu-id="394c2-130">Installieren von IdFix</span><span class="sxs-lookup"><span data-stu-id="394c2-130">Install IdFix</span></span>

<span data-ttu-id="394c2-131">Zum Installieren von IdFix können Sie **IdFix. exe**herunterladen und entpacken:</span><span class="sxs-lookup"><span data-stu-id="394c2-131">To install IdFix, download and unzip **IdFix.exe**:</span></span> 
  
1. <span data-ttu-id="394c2-132">Melden Sie sich an dem Computer an, auf dem Sie das IdFix-Tool installieren möchten.</span><span class="sxs-lookup"><span data-stu-id="394c2-132">Log on to the computer where you want to install the IdFix tool.</span></span>
    
2. <span data-ttu-id="394c2-133">Wechseln Sie zur Microsoft-Download Website für das [IdFix Dirsync Error Remediation Tool](https://go.microsoft.com/fwlink/?linkid=867219).</span><span class="sxs-lookup"><span data-stu-id="394c2-133">Go to the Microsoft download site for the [IdFix DirSync Error Remediation Tool](https://go.microsoft.com/fwlink/?linkid=867219).</span></span>
    
3. <span data-ttu-id="394c2-134">Klicken Sie auf **Herunterladen**.</span><span class="sxs-lookup"><span data-stu-id="394c2-134">Choose **Download**.</span></span>
    
4. <span data-ttu-id="394c2-135">Wenn Sie dazu aufgefordert werden, wählen Sie **Ausführen**aus.</span><span class="sxs-lookup"><span data-stu-id="394c2-135">When prompted, choose **Run**.</span></span>
    
5. <span data-ttu-id="394c2-136">Geben Sie im Dialogfeld **WinZip Self-Extractor** im Textfeld **unzip to Folder** den Speicherort ein, an dem Sie das IdFix-Tool installieren möchten, oder navigieren Sie zu diesem.</span><span class="sxs-lookup"><span data-stu-id="394c2-136">On the **WinZip Self-Extractor** dialog box, in the **Unzip to folder** text box, type or browse to the location where you want to install the IdFix tool.</span></span> <span data-ttu-id="394c2-137">Standardmäßig wird IdFix in `C:\Deployment Tools\`installiert.</span><span class="sxs-lookup"><span data-stu-id="394c2-137">By default, IdFix is installed into `C:\Deployment Tools\`.</span></span> 
    
6. <span data-ttu-id="394c2-138">Wählen Sie **unzip**aus.</span><span class="sxs-lookup"><span data-stu-id="394c2-138">Choose **Unzip**.</span></span>
    
## <a name="run-the-idfix-tool"></a><span data-ttu-id="394c2-139">Ausführen des IdFix-Tools</span><span class="sxs-lookup"><span data-stu-id="394c2-139">Run the IdFix tool</span></span>

<span data-ttu-id="394c2-140">Führen Sie nach der Installation von IdFix das Tool aus, um nach Problemen in Ihrem Verzeichnis zu suchen:</span><span class="sxs-lookup"><span data-stu-id="394c2-140">After you install IdFix, run the tool to search for problems in your directory:</span></span>
  
1. <span data-ttu-id="394c2-141">Melden Sie sich mit einem Konto mit Lese-/Schreibzugriff auf das Verzeichnis an dem Computer an, auf dem Sie IdFix installiert haben.</span><span class="sxs-lookup"><span data-stu-id="394c2-141">Using an account that has read/write access to the directory, log on to the computer where you installed IdFix.</span></span>
    
2. <span data-ttu-id="394c2-142">Wechseln Sie im Datei-Explorer zu dem Speicherort, an dem Sie IdFix installiert haben.</span><span class="sxs-lookup"><span data-stu-id="394c2-142">In File Explorer, go to the location where you installed IdFix.</span></span> <span data-ttu-id="394c2-143">Wenn Sie während der Installation den Standardordner ausgewählt haben, `C:\Deployment Tools\IdFix`wechseln Sie zu.</span><span class="sxs-lookup"><span data-stu-id="394c2-143">If you chose the default folder during installation, go to `C:\Deployment Tools\IdFix`.</span></span>
    
3. <span data-ttu-id="394c2-144">Doppelklicken Sie auf **IdFix. exe**.</span><span class="sxs-lookup"><span data-stu-id="394c2-144">Double-click **IdFix.exe**.</span></span> 
    
    ![Wählen Sie die Datei IdFix. exe aus.](media/a9387bbc-991f-41c2-a500-45e3ce574285.JPG)
  
4. <span data-ttu-id="394c2-146">Standardmäßig verwendet IdFix den mandantenfähigen Regelsatz, um die Einträge in Ihrem Verzeichnis zu testen.</span><span class="sxs-lookup"><span data-stu-id="394c2-146">By default, IdFix uses the Multi-Tenant rule set to test the entries in your directory.</span></span> <span data-ttu-id="394c2-147">Dies ist der richtige Regelsatz für die meisten Office 365-Kunden.</span><span class="sxs-lookup"><span data-stu-id="394c2-147">This is the right rule set for most Office 365 customers.</span></span> <span data-ttu-id="394c2-148">Wenn Sie jedoch ein Office 365 Dedicated-oder ITAR (International Traffic in Arms Regulations)-Kunde sind, können Sie IdFix so konfigurieren, dass stattdessen der dedizierte Regelsatz verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="394c2-148">However, if you are an Office 365 Dedicated or ITAR (International Traffic in Arms Regulations) customer, you can configure IdFix to use the Dedicated rule set instead.</span></span> <span data-ttu-id="394c2-149">Wenn Sie nicht sicher sind, welche Art von Kunden Sie sind, können Sie diesen Schritt gefahrlos überspringen.</span><span class="sxs-lookup"><span data-stu-id="394c2-149">If you aren't sure what type of customer you are, you can safely skip this step.</span></span> <span data-ttu-id="394c2-150">Klicken Sie auf das Zahnradsymbol in der Menüleiste, und wählen Sie dann **dediziert**aus, um den Regelsatz auf Dedicated festzulegen.</span><span class="sxs-lookup"><span data-stu-id="394c2-150">To set the rule set to Dedicated, click the gear icon in the menu bar and then choose **Dedicated**.</span></span>
    
5. <span data-ttu-id="394c2-151">Wählen Sie **Query**aus.</span><span class="sxs-lookup"><span data-stu-id="394c2-151">Choose **Query**.</span></span>
    
    ![Wählen Sie Query in IdFix aus.](media/a07a7aa7-d0ac-4817-8757-946019813a57.JPG)
  
6. <span data-ttu-id="394c2-153">Standardmäßig durchsucht IdFix das gesamte Verzeichnis auf Fehler.</span><span class="sxs-lookup"><span data-stu-id="394c2-153">By default, IdFix searches the entire directory for errors.</span></span>
    
    <span data-ttu-id="394c2-154">Abhängig von der Größe des Verzeichnisses kann das Ausführen der Abfrage eine Weile dauern.</span><span class="sxs-lookup"><span data-stu-id="394c2-154">Depending on the size of your directory, running the query can take a while.</span></span> <span data-ttu-id="394c2-155">Sie können den Fortschritt am unteren Rand des Hauptfensters des Tools ansehen.</span><span class="sxs-lookup"><span data-stu-id="394c2-155">You can watch the progress at the bottom of the tool's main window.</span></span> <span data-ttu-id="394c2-156">Wenn Sie auf **Abbrechen**klicken, müssen Sie von vorn beginnen.</span><span class="sxs-lookup"><span data-stu-id="394c2-156">If you click **Cancel**, you'll need to restart from the beginning.</span></span>
    
    ![IdFix-Abfrage und Fehleranzahl.](media/da0198a0-7d4d-4afe-a256-e82f1330ada5.JPG)
  
7. <span data-ttu-id="394c2-158">Nachdem IdFix die Abfrage abgeschlossen hat, können Sie mit der Synchronisierung des Verzeichnisses fortfahren, falls keine Fehler vorliegen.</span><span class="sxs-lookup"><span data-stu-id="394c2-158">After IdFix completes the query, you can go ahead and synchronize your directory if there are no errors.</span></span> <span data-ttu-id="394c2-159">Wenn Ihr Verzeichnis fehlerhaft ist, sollten Sie diese vor der Synchronisierung korrigieren.</span><span class="sxs-lookup"><span data-stu-id="394c2-159">If there are errors in your directory, it is recommended that you fix them before you synchronize.</span></span> <span data-ttu-id="394c2-160">Wenn Sie genauere Informationen zu Fehlertypen und Empfehlungen zur bestmöglichen Möglichkeit zum Beheben von Fehlern benötigen, lesen Sie die Links am Ende dieses Themas.</span><span class="sxs-lookup"><span data-stu-id="394c2-160">If you want more specific information about types of errors and recommendations about the best way to fix each of them, see the links at the end of this topic.</span></span> 
    
    <span data-ttu-id="394c2-161">Es ist zwar nicht zwingend erforderlich, die Fehler vor der Synchronisierung zu beheben, es wird jedoch dringend empfohlen, dass Sie zumindest alle von IdFix zurückgegebenen Fehler überarbeiten.</span><span class="sxs-lookup"><span data-stu-id="394c2-161">While it is not mandatory to fix the errors before you synchronize, we strongly recommend that you at least review all the errors returned by IdFix.</span></span>
    
    <span data-ttu-id="394c2-162">Jeder Fehler wird in einer separaten Zeile im Hauptfenster des Tools angezeigt.</span><span class="sxs-lookup"><span data-stu-id="394c2-162">Each error is displayed in a separate row in the tool's main window .</span></span> 
    
8. <span data-ttu-id="394c2-163">Wenn Sie der vorgeschlagenen Änderung in der Spalte **Update** zustimmen, wählen Sie in der Spalte **Aktion** aus, was IdFix tun soll, um die Änderung zu implementieren, und klicken Sie dann auf über **nehmen**.</span><span class="sxs-lookup"><span data-stu-id="394c2-163">If you agree with the suggested change in the **UPDATE** column, in the **ACTION** column select what you want IdFix to do to implement the change and then click **Apply**.</span></span> <span data-ttu-id="394c2-164">Wenn Sie auf über **nehmen**klicken, nimmt das Tool die Änderungen im Verzeichnis vor.</span><span class="sxs-lookup"><span data-stu-id="394c2-164">When you click **Apply**, the tool makes the changes in the directory.</span></span>
    
    <span data-ttu-id="394c2-165">Sie müssen nach jeder Aktualisierung nicht auf **anwenden** klicken.</span><span class="sxs-lookup"><span data-stu-id="394c2-165">You don't have to click **Apply** after each update.</span></span> <span data-ttu-id="394c2-166">Stattdessen können Sie mehrere Fehler beheben, bevor Sie auf **anwenden** klicken, und IdFix wird Sie alle gleichzeitig ändern.</span><span class="sxs-lookup"><span data-stu-id="394c2-166">Instead, you can fix several errors before you click **Apply** and IdFix will change them all at the same time.</span></span> <span data-ttu-id="394c2-167">Sie können die Fehler nach Fehlertyp sortieren, indem Sie oben in der Spalte, in der die Fehlertypen aufgelistet werden, auf **Fehler** klicken.</span><span class="sxs-lookup"><span data-stu-id="394c2-167">You can sort the errors by error type by clicking **ERROR** at the top of the column that lists the error types.</span></span> 
    
    <span data-ttu-id="394c2-168">Eine Strategie besteht darin, alle Fehler des gleichen Typs zu beheben. beheben Sie beispielsweise zuerst alle Duplikate, und wenden Sie Sie an.</span><span class="sxs-lookup"><span data-stu-id="394c2-168">One strategy is to fix all the errors of the same type; for example, fix all the duplicates first, and apply them.</span></span> <span data-ttu-id="394c2-169">Korrigieren Sie als nächstes die Zeichenformat Fehler usw.</span><span class="sxs-lookup"><span data-stu-id="394c2-169">Next, fix the character format errors, and so on.</span></span> <span data-ttu-id="394c2-170">Jedes Mal, wenn Sie die Änderungen übernehmen, erstellt das IdFix-Tool eine separate Protokolldatei, mit der Sie die Änderungen rückgängig machen können, falls Sie einen Fehler machen.</span><span class="sxs-lookup"><span data-stu-id="394c2-170">Each time you apply the changes, the IdFix tool creates a separate log file that you can use to undo your changes in case you make a mistake.</span></span> <span data-ttu-id="394c2-171">Das [Transaktionsprotokoll](idfix-transaction-log.md) wird in dem Ordner gespeichert, in dem Sie IdFix installiert haben.</span><span class="sxs-lookup"><span data-stu-id="394c2-171">The [transaction log](idfix-transaction-log.md) is stored in the folder that you installed IdFix in.</span></span>  <span data-ttu-id="394c2-172">_C:\Deployment Tools\IdFix_ standardmäßig.</span><span class="sxs-lookup"><span data-stu-id="394c2-172">_C:\Deployment Tools\IdFix_ by default.</span></span> 
    
    ![Beheben von Fehlern in IdFix.](media/5f051070-652c-4be7-98bf-312295e32371.png)
  
9. <span data-ttu-id="394c2-174">Nachdem alle Änderungen am Verzeichnis vorgenommen wurden, führen Sie IdFix erneut aus, um sicherzustellen, dass die von Ihnen vorgenommenen Korrekturen keine neuen Fehler einführten.</span><span class="sxs-lookup"><span data-stu-id="394c2-174">After all of your changes are made to the directory, run IdFix again to ensure that the fixes you made didn't introduce new errors.</span></span> <span data-ttu-id="394c2-175">Sie können diese Schritte beliebig oft wiederholen.</span><span class="sxs-lookup"><span data-stu-id="394c2-175">You can repeat these steps as many times as you need to.</span></span> <span data-ttu-id="394c2-176">Es empfiehlt sich, den Prozess einige Male zu durchlaufen, bevor Sie synchronisieren.</span><span class="sxs-lookup"><span data-stu-id="394c2-176">It's a good idea to go through the process a few times before you synchronize.</span></span>
    
## <a name="i-want-to-refine-my-search-or-dig-deeper-into-the-errors-what-else-can-i-do-with-idfix"></a><span data-ttu-id="394c2-177">Ich möchte meine Suche verfeinern oder tiefer in die Fehler eingraben, was kann ich sonst noch mit IdFix tun?</span><span class="sxs-lookup"><span data-stu-id="394c2-177">I want to refine my search or dig deeper into the errors, what else can I do with IdFix?</span></span>

<span data-ttu-id="394c2-178">Weitere ausführliche Informationen finden Sie in den folgenden Themen:</span><span class="sxs-lookup"><span data-stu-id="394c2-178">More in-depth information is available from these topics:</span></span>
  
- <span data-ttu-id="394c2-179">[Vorbereiten von Verzeichnisattributen für die Synchronisierung mit Office 365 mithilfe des IdFix-Tools](prepare-directory-attributes-for-synch-with-idfix.md) .</span><span class="sxs-lookup"><span data-stu-id="394c2-179">[Prepare directory attributes for synchronization with Office 365 by using the IdFix tool](prepare-directory-attributes-for-synch-with-idfix.md) .</span></span> <span data-ttu-id="394c2-180">Wenn Sie das Tool installiert haben, wechseln Sie zu diesem Thema, um detailliertere Anweisungen zum Ausführen des Tools, häufige Fehler, die auftreten werden, Empfohlene Korrekturen, Beispiele und bewährte Methoden für die Vorgehensweise bei einer hohen Anzahl von Fehlern.</span><span class="sxs-lookup"><span data-stu-id="394c2-180">After you have installed the tool, jump to this topic for more detailed instructions about running the tool, common errors you will encounter, suggested fixes, examples, and best practices for what to do when you have a large number of errors.</span></span> 
- [<span data-ttu-id="394c2-181">Referenz: Ausgeschlossene und unterstützte Objekte und Attribute für IdFix</span><span class="sxs-lookup"><span data-stu-id="394c2-181">Reference: IdFix excluded and supported objects and attributes</span></span>](idfix-excluded-and-supported-objects-and-attributes.md)  
- [<span data-ttu-id="394c2-182">Referenz: Office 365 IdFix-Transaktionsprotokoll</span><span class="sxs-lookup"><span data-stu-id="394c2-182">Reference: Office 365 IdFix transaction log</span></span>](idfix-transaction-log.md)
    
## <a name="video-training"></a><span data-ttu-id="394c2-183">Videoschulung</span><span class="sxs-lookup"><span data-stu-id="394c2-183">Video training</span></span>

<span data-ttu-id="394c2-184">Weitere Informationen finden Sie in der Lektion [Installieren und Verwenden des IDFix-Tools](https://support.office.com/article/install-and-use-the-idfix-tool-4d81d73c-f172-4fd5-8542-f601c0c96aa9?ui=en-US&rs=en-US&ad=US), die Ihnen von LinkedIn Learning zur Verfügung gestellt wird.</span><span class="sxs-lookup"><span data-stu-id="394c2-184">For more information, see the lesson [Install and use the IDFix tool](https://support.office.com/article/install-and-use-the-idfix-tool-4d81d73c-f172-4fd5-8542-f601c0c96aa9?ui=en-US&rs=en-US&ad=US), brought to you by LinkedIn Learning.</span></span>
  

