---
title: Herunterladen und Ausführen des Microsoft 365-IdFix-Tools
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: get-started-article
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- O365E_HRCSetupAADConnectIDFixLM617036
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
ms.assetid: f4bd2439-3e41-4169-99f6-3fabdfa326ac
description: Hier erfahren Sie, wie Sie das Microsoft 365 IdFix-Tool herunterladen und ausführen, um Ihre Active Directory-Domänendienste (AD DS) vor dem Synchronisieren mit Microsoft 365 zu bereinigen.
ms.openlocfilehash: dde12d7e16aad8488fe067888eacdf1c80e1a037
ms.sourcegitcommit: d2a3d6eeeaa07510ee94c2bc675284d893221a95
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2020
ms.locfileid: "44711595"
---
# <a name="download-and-run-the-microsoft-365-idfix-tool"></a><span data-ttu-id="0c825-103">Herunterladen und Ausführen des Microsoft 365-IdFix-Tools</span><span class="sxs-lookup"><span data-stu-id="0c825-103">Download and run the Microsoft 365 IdFix tool</span></span>

<span data-ttu-id="0c825-104">*Dieser Artikel gilt sowohl für Office 365 Enterprise als auch für Microsoft 365 Enterprise.*</span><span class="sxs-lookup"><span data-stu-id="0c825-104">*This article applies to both Office 365 Enterprise and Microsoft 365 Enterprise.*</span></span>

<span data-ttu-id="0c825-105">IdFix identifiziert Fehler wie Duplikate und Formatierungsprobleme in Ihrer Active Directory-Domänendienste (AD DS) Domäne vor der Synchronisierung mit Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="0c825-105">IdFix identifies errors such as duplicates and formatting problems in your Active Directory Domain Services (AD DS) domain before you synchronize to Microsoft 365.</span></span> 
  
<span data-ttu-id="0c825-106">Um diese Aufgabe erfolgreich abschließen zu können, sollten Sie mit der Arbeit mit Benutzern, Gruppen und Kontaktobjekten in Ad DS vertraut sein.</span><span class="sxs-lookup"><span data-stu-id="0c825-106">To finish this task successfully, you should be comfortable working with user, group, and contact objects in AD DS.</span></span>
  
<span data-ttu-id="0c825-107">Wenn Sie diesen Vorgang nicht erfolgreich abschließen können, gibt es einige andere Möglichkeiten, die Sie tun können.</span><span class="sxs-lookup"><span data-stu-id="0c825-107">If you can't complete this task, there are a couple of other things you can do.</span></span> <span data-ttu-id="0c825-108">Diese Methoden sind möglicherweise einfacher, dauern aber länger oder bringen andere Probleme mit sich.</span><span class="sxs-lookup"><span data-stu-id="0c825-108">These methods might be easier, but they might also take longer or have other drawbacks.</span></span> <span data-ttu-id="0c825-109">Dies sind:</span><span class="sxs-lookup"><span data-stu-id="0c825-109">They are:</span></span>
  
- <span data-ttu-id="0c825-110">**Führen Sie die Verzeichnissynchronisierung ohne IdFix aus.**</span><span class="sxs-lookup"><span data-stu-id="0c825-110">**Run directory synchronization without running IdFix**</span></span> 

  <span data-ttu-id="0c825-111">Sie können Ihr Verzeichnis synchronisieren, ohne das IdFix-Tool auszuführen, dies wird jedoch nicht empfohlen.</span><span class="sxs-lookup"><span data-stu-id="0c825-111">You can synchronize your directory without using the IdFix tool, but we don't recommend it.</span></span> <span data-ttu-id="0c825-112">Das Beheben von Fehlern vor der Synchronisierung nimmt weniger Zeit in Anspruch und ermöglicht einen reibungsloseren Übergang zur Cloud.</span><span class="sxs-lookup"><span data-stu-id="0c825-112">Fixing errors before you synchronize takes less time and often provides a smoother transition to the cloud.</span></span> 

- <span data-ttu-id="0c825-113">**Stellen Sie einen Berater ein.**</span><span class="sxs-lookup"><span data-stu-id="0c825-113">**Hire a consultant**</span></span> 

  <span data-ttu-id="0c825-114">Mit Expertenhilfe können Ihre Benutzer schnell loslegen, und Ihr Verzeichnis wird synchronisiert.</span><span class="sxs-lookup"><span data-stu-id="0c825-114">Getting expert help can get your users up and running quickly and your directory synchronized.</span></span> 
    
## <a name="what-you-need-to-run-idfix"></a><span data-ttu-id="0c825-115">Voraussetzungen für das Ausführen von IdFix</span><span class="sxs-lookup"><span data-stu-id="0c825-115">What you need to run IdFix</span></span>

<span data-ttu-id="0c825-116">Die einfachste Möglichkeit zum Einrichten und Ausführen von IdFix besteht darin, es auf einen Computer herunterzuladen, der mit Ihrer AD DS-Domäne verbunden ist.</span><span class="sxs-lookup"><span data-stu-id="0c825-116">The easiest way to get IdFix up and running is to download it onto a computer that is joined to your AD DS domain.</span></span> <span data-ttu-id="0c825-117">Wenn Sie möchten, können Sie es auf dem Domänencontroller ausführen, dies ist jedoch nicht erforderlich.</span><span class="sxs-lookup"><span data-stu-id="0c825-117">You can run it on the domain controller if you want, but it's not necessary.</span></span>
  
### <a name="idfix-hardware-requirements"></a><span data-ttu-id="0c825-118">IdFix-Hardwareanforderungen</span><span class="sxs-lookup"><span data-stu-id="0c825-118">IdFix hardware requirements</span></span>

<span data-ttu-id="0c825-119">Der Computer, auf den Sie IdFix herunterladen, muss diese Mindesthardwareanforderungen erfüllen:</span><span class="sxs-lookup"><span data-stu-id="0c825-119">The computer where you download IdFix needs to meet these minimum hardware requirements:</span></span>
  
- <span data-ttu-id="0c825-120">4 GB RAM</span><span class="sxs-lookup"><span data-stu-id="0c825-120">4 GB RAM</span></span>
- <span data-ttu-id="0c825-121">2 GB Festplattenspeicher</span><span class="sxs-lookup"><span data-stu-id="0c825-121">2 GB of hard disk space</span></span>
   
### <a name="idfix-software-requirements"></a><span data-ttu-id="0c825-122">IdFix-Softwareanforderungen</span><span class="sxs-lookup"><span data-stu-id="0c825-122">IdFix software requirements</span></span>

<span data-ttu-id="0c825-123">Der Computer, auf dem Sie IdFix herunterladen, muss derselben AD DS Domäne hinzugefügt werden, aus der Sie Benutzer mit Microsoft 365 synchronisieren möchten.</span><span class="sxs-lookup"><span data-stu-id="0c825-123">The computer where you download IdFix needs to be joined to the same AD DS domain from which you want to synchronize users to Microsoft 365.</span></span> 

<span data-ttu-id="0c825-124">Auf dem Computer muss zudem .NET Framework 4.0 installiert sein.</span><span class="sxs-lookup"><span data-stu-id="0c825-124">The computer also needs to have .NET Framework 4.0 installed.</span></span> <span data-ttu-id="0c825-125">Wenn Sie Windows Server 2008 oder höher ausführen, ist .NET Framework möglicherweise bereits installiert.</span><span class="sxs-lookup"><span data-stu-id="0c825-125">If you are running Windows Server 2008 or later, the .NET Framework is probably already installed.</span></span> <span data-ttu-id="0c825-126">Ist das nicht der Fall, [laden Sie .NET 4.0 aus dem Download Center herunter](https://go.microsoft.com/fwlink/p/?LinkId=400475) oder unter Verwendung von Windows Update.</span><span class="sxs-lookup"><span data-stu-id="0c825-126">If not, you can [download .NET 4.0 from the download center](https://go.microsoft.com/fwlink/p/?LinkId=400475) or with Windows Update.</span></span> 
  
### <a name="idfix-permissions-requirements"></a><span data-ttu-id="0c825-127">IdFix-Berechtigungsanforderungen</span><span class="sxs-lookup"><span data-stu-id="0c825-127">IdFix permissions requirements</span></span>

<span data-ttu-id="0c825-128">Das Benutzerkonto, das Sie zum Ausführen von IdFix verwenden, muss über Lese-/Schreibzugriff auf die AD DS-Domäne verfügen.</span><span class="sxs-lookup"><span data-stu-id="0c825-128">The user account that you use to run IdFix must have read and write access to the AD DS domain.</span></span>
  
<span data-ttu-id="0c825-129">Wenn Sie nicht sicher sind, ob Ihr Benutzerkonto diese Anforderungen erfüllt und nicht wissen, wie Sie dies überprüfen können, können Sie IdFix trotzdem herunterladen und ausführen.</span><span class="sxs-lookup"><span data-stu-id="0c825-129">If you aren't sure if your user account meets these requirements, and you're not sure how to check, you can still download and run IdFix.</span></span> <span data-ttu-id="0c825-130">Wenn Ihr Benutzerkonto nicht über die richtigen Berechtigungen verfügt, zeigt IdFix einfach einen Fehler an, wenn Sie versuchen, es auszuführen.</span><span class="sxs-lookup"><span data-stu-id="0c825-130">If your user account doesn't have the right permissions, IdFix will simply display an error when you try to run it.</span></span>
  
## <a name="download-and-extract-idfix"></a><span data-ttu-id="0c825-131">Herunterladen und Extrahieren von IdFix</span><span class="sxs-lookup"><span data-stu-id="0c825-131">Download and extract IdFix</span></span>

<span data-ttu-id="0c825-132">Befolgen Sie diese Anweisungen.</span><span class="sxs-lookup"><span data-stu-id="0c825-132">Follow these instructions.</span></span> 
  
1. <span data-ttu-id="0c825-133">Melden Sie sich am Computer an, auf dem Sie das IdFix-Tool ausführen möchten.</span><span class="sxs-lookup"><span data-stu-id="0c825-133">Sign in to the computer where you want to run the IdFix tool.</span></span>
    
2. <span data-ttu-id="0c825-134">Wechseln Sie zur Website des [IdFix Dirsync-Fehlerbehebungstools](https://github.com/microsoft/idfix) .</span><span class="sxs-lookup"><span data-stu-id="0c825-134">Go to the [IdFix DirSync Error Remediation Tool](https://github.com/microsoft/idfix) site.</span></span>
    
3. <span data-ttu-id="0c825-135">Klicken Sie im Abschnitt **ClickOnce-Start** auf **starten** , um die ZIP-Datei herunterzuladen.</span><span class="sxs-lookup"><span data-stu-id="0c825-135">Click **launch** in the **ClickOnce Launch** section to download the zip file.</span></span> <span data-ttu-id="0c825-136">Öffnen Sie die ZIP-Datei.</span><span class="sxs-lookup"><span data-stu-id="0c825-136">Open the zip file.</span></span>
    
4. <span data-ttu-id="0c825-137">Wählen Sie im Fenster **IdFix** die Option **Extrahieren** aus, und klicken Sie dann auf **Alle extrahieren**.</span><span class="sxs-lookup"><span data-stu-id="0c825-137">In the **IdFix** window, choose **Extract**, and then **Extract all**.</span></span> <span data-ttu-id="0c825-138">Standardmäßig wird IdFix in `C:\Users\<your user name>\Documents\IdFix` extrahiert.</span><span class="sxs-lookup"><span data-stu-id="0c825-138">By default, IdFix is extracted to `C:\Users\<your user name>\Documents\IdFix`.</span></span> 
    
5. <span data-ttu-id="0c825-139">Wählen Sie **Extrahieren** aus.</span><span class="sxs-lookup"><span data-stu-id="0c825-139">Choose **Extract**.</span></span>

<span data-ttu-id="0c825-140">Ihre Schritte können je nach ihrer Version von Windows und Ihrem Internet Browser variieren.</span><span class="sxs-lookup"><span data-stu-id="0c825-140">Your steps might vary based on your version of Windows and your Internet browser.</span></span>
    
## <a name="run-the-idfix-tool"></a><span data-ttu-id="0c825-141">Ausführen des IdFix-Tools</span><span class="sxs-lookup"><span data-stu-id="0c825-141">Run the IdFix tool</span></span>

<span data-ttu-id="0c825-142">Nachdem Sie IdFix heruntergeladen und extrahiert haben, führen Sie es aus, um nach Problemen in Ihrer AD DS-Domäne zu suchen.</span><span class="sxs-lookup"><span data-stu-id="0c825-142">After you download and extract IdFix, run it to search for problems in your AD DS domain.</span></span>
  
1. <span data-ttu-id="0c825-143">Melden Sie sich unter Verwendung eines Kontos mit Lese-/Schreibzugriff für Ihre AD DS-Domäne an dem Computer an, auf den Sie IdFix heruntergeladen haben.</span><span class="sxs-lookup"><span data-stu-id="0c825-143">Using an account that has read/write access to your AD DS domain, sign in to the computer where you downloaded IdFix.</span></span>
    
2. <span data-ttu-id="0c825-144">Wechseln Sie im Datei-Explorer zum Speicherort, an den Sie IdFix extrahiert haben.</span><span class="sxs-lookup"><span data-stu-id="0c825-144">In File Explorer, go to the location where you extracted IdFix.</span></span> <span data-ttu-id="0c825-145">Wenn Sie bei der Extraktion den Standardordner ausgewählt haben, navigieren Sie zu `C:\Users\<your user name>\Documents\IdFix`.</span><span class="sxs-lookup"><span data-stu-id="0c825-145">If you chose the default folder during extraction, go to `C:\Users\<your user name>\Documents\IdFix`.</span></span> 
    
3. <span data-ttu-id="0c825-146">Doppelklicken Sie auf **IdFix.exe**.</span><span class="sxs-lookup"><span data-stu-id="0c825-146">Double-click **IdFix.exe**.</span></span> 
  
4. <span data-ttu-id="0c825-147">IdFix verwendet standardmäßig den mehrinstanzenfähigen Regelsatz zum Testen der Einträge in Ihrem Verzeichnis.</span><span class="sxs-lookup"><span data-stu-id="0c825-147">By default, IdFix uses the Multi-Tenant rule set to test the entries in your directory.</span></span> <span data-ttu-id="0c825-148">Dies ist der richtige Regelsatz für die meisten Microsoft 365-Kunden.</span><span class="sxs-lookup"><span data-stu-id="0c825-148">This is the right rule set for most Microsoft 365 customers.</span></span> <span data-ttu-id="0c825-149">Wenn Sie jedoch ein Microsoft 365-dedizierter oder internationaler ITAR-Kunde sind, können Sie IdFix so konfigurieren, dass stattdessen der dedizierte Regelsatz verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="0c825-149">However, if you are a Microsoft 365 Dedicated or International Traffic in Arms Regulations (ITAR)) customer, you can configure IdFix to use the Dedicated rule set instead.</span></span> <span data-ttu-id="0c825-150">Wenn Sie nicht sicher sind, was für ein Kundentyp Sie sind, können Sie diesen Schritt einfach überspringen.</span><span class="sxs-lookup"><span data-stu-id="0c825-150">If you aren't sure what type of customer you are, you can safely skip this step.</span></span> <span data-ttu-id="0c825-151">Um den Regelsatz auf "Dediziert" einzustellen, klicken Sie in der Menüleiste auf das Zahnradsymbol, und wählen Sie dann **Dediziert** aus.</span><span class="sxs-lookup"><span data-stu-id="0c825-151">To set the rule set to Dedicated, click the gear icon in the menu bar, and then choose **Dedicated**.</span></span>
    
5. <span data-ttu-id="0c825-152">Wählen Sie **Abfrage** aus.</span><span class="sxs-lookup"><span data-stu-id="0c825-152">Choose **Query**.</span></span>
    
    ![Wählen Sie die Abfrage in IdFix aus.](media/a07a7aa7-d0ac-4817-8757-946019813a57.JPG)
  
6. <span data-ttu-id="0c825-154">IdFix überprüft das gesamte Verzeichnis standardmäßig auf Fehler.</span><span class="sxs-lookup"><span data-stu-id="0c825-154">By default, IdFix searches the entire directory for errors.</span></span>
    
    <span data-ttu-id="0c825-155">Je nach der Größe Ihres Verzeichnisses kann das Ausführen der Abfrage eine Weile dauern.</span><span class="sxs-lookup"><span data-stu-id="0c825-155">Depending on the size of your directory, running the query can take a while.</span></span> <span data-ttu-id="0c825-156">Sie können den Fortschritt unten im Hauptfenster des Tools anzeigen.</span><span class="sxs-lookup"><span data-stu-id="0c825-156">You can watch the progress at the bottom of the tool's main window.</span></span> <span data-ttu-id="0c825-157">Wenn Sie auf **Abbrechen** klicken, müssen Sie erneut von vorn beginnen.</span><span class="sxs-lookup"><span data-stu-id="0c825-157">If you click **Cancel**, you'll need to restart from the beginning.</span></span>
  
7. <span data-ttu-id="0c825-158">Wenn IdFix die Abfrage abgeschlossen und keine Fehler gefunden hat, können Ihr Verzeichnis synchronisieren.</span><span class="sxs-lookup"><span data-stu-id="0c825-158">After IdFix completes the query, you can synchronize your directory if there are no errors.</span></span> <span data-ttu-id="0c825-159">Wenn in Ihrem Verzeichnis Fehler vorhanden sind, sollten Sie sie beheben, bevor Sie die Synchronisierung vornehmen.</span><span class="sxs-lookup"><span data-stu-id="0c825-159">If there are errors in your directory, it is recommended that you fix them before you synchronize.</span></span> <span data-ttu-id="0c825-160">Weitere Informationen finden Sie unter [Prepare Directory attributes for Synchronization with Microsoft 365](prepare-directory-attributes-for-synch-with-idfix.md) .</span><span class="sxs-lookup"><span data-stu-id="0c825-160">See [prepare directory attributes for synchronization with Microsoft 365](prepare-directory-attributes-for-synch-with-idfix.md) for more information.</span></span>
    
    <span data-ttu-id="0c825-161">Obwohl es nicht obligatorisch ist, die Fehler vor der Synchronisierung zu beheben, empfehlen wir ausdrücklich, dass Sie wenigstens alle durch IdFix zurückgegebenen Fehler überprüfen.</span><span class="sxs-lookup"><span data-stu-id="0c825-161">While it is not mandatory to fix the errors before you synchronize, we strongly recommend that you at least review all the errors returned by IdFix.</span></span>
    
    <span data-ttu-id="0c825-162">Jeder Fehler wird im Hauptfenster des Tools in einer eigenen Zeile angezeigt.</span><span class="sxs-lookup"><span data-stu-id="0c825-162">Each error is displayed in a separate row in the tool's main window .</span></span> 
    
8. <span data-ttu-id="0c825-163">Wenn Sie mit der in der Spalte **UPDATE** vorgeschlagenen Änderung einverstanden sind, wählen Sie in der Spalte **ACTION** den Vorgang aus, den IdFix zum Implementieren der Änderung ausführen soll, und klicken Sie dann auf **Übernehmen**.</span><span class="sxs-lookup"><span data-stu-id="0c825-163">If you agree with the suggested change in the **UPDATE** column, in the **ACTION** column select what you want IdFix to do to implement the change and then click **Apply**.</span></span> <span data-ttu-id="0c825-164">Wenn Sie auf **Apply** klicken, nimmt das Tool die Änderungen im Verzeichnis vor.</span><span class="sxs-lookup"><span data-stu-id="0c825-164">When you click **Apply**, the tool makes the changes in the directory.</span></span>
    
    <span data-ttu-id="0c825-165">Sie müssen nicht nach jeder Aktualisierung auf **Übernehmen** klicken.</span><span class="sxs-lookup"><span data-stu-id="0c825-165">You don't have to click **Apply** after each update.</span></span> <span data-ttu-id="0c825-166">Sie können auch zuerst mehrere Fehler beheben und dann auf **Übernehmen** klicken. IdFix führt dann alle Änderungen gleichzeitig aus.</span><span class="sxs-lookup"><span data-stu-id="0c825-166">Instead, you can fix several errors before you click **Apply** and IdFix will change them all at the same time.</span></span> <span data-ttu-id="0c825-167">Sie können die Fehler nach Fehlertyp sortieren, indem Sie oben in der Spalte, in der die Fehlertypen aufgelistet werden, auf **ERROR** klicken.</span><span class="sxs-lookup"><span data-stu-id="0c825-167">You can sort the errors by error type by clicking **ERROR** at the top of the column that lists the error types.</span></span> 
    
    <span data-ttu-id="0c825-168">Eine Strategie besteht darin, alle Fehler desselben Typs zu beheben. Ändern Sie beispielsweise zunächst alle Duplikate, und übernehmen Sie sie.</span><span class="sxs-lookup"><span data-stu-id="0c825-168">One strategy is to fix all the errors of the same type; for example, fix all the duplicates first, and apply them.</span></span> <span data-ttu-id="0c825-169">Beheben Sie als Nächstes Zeichenformatierungsfehler usw.</span><span class="sxs-lookup"><span data-stu-id="0c825-169">Next, fix the character format errors, and so on.</span></span> <span data-ttu-id="0c825-170">Bei jeder Übernahme der Änderungen erstellt das IdFix-Tool eine separate Protokolldatei, die Sie zum Rückgängigmachen Ihrer Änderungen verwenden können, falls Sie einen Fehler begehen.</span><span class="sxs-lookup"><span data-stu-id="0c825-170">Each time you apply the changes, the IdFix tool creates a separate log file that you can use to undo your changes in case you make a mistake.</span></span> <span data-ttu-id="0c825-171">Das [Transaktionsprotokoll](idfix-transaction-log.md) wird in dem Ordner gespeichert, in dem Sie IdFix extrahiert haben, was standardmäßig _C:\Users \<your user name> \Documents\IdFix_ ist.</span><span class="sxs-lookup"><span data-stu-id="0c825-171">The [transaction log](idfix-transaction-log.md) is stored in the folder where you extracted IdFix, which is _C:\Users\<your user name>\Documents\IdFix_ by default.</span></span> 
    
    ![Beseitigen von Fehlern in IdFix.](media/5f051070-652c-4be7-98bf-312295e32371.png)
  
9. <span data-ttu-id="0c825-173">Nachdem alle Änderungen am Verzeichnis vorgenommen wurden, führen Sie IdFix erneut aus, um sicherzustellen, dass die Fehlerbehebungen keine neuen Fehler verursacht haben.</span><span class="sxs-lookup"><span data-stu-id="0c825-173">After all of your changes are made to the directory, run IdFix again to ensure that the fixes you made didn't introduce new errors.</span></span> <span data-ttu-id="0c825-174">Sie können diese Schritte beliebig oft wiederholen.</span><span class="sxs-lookup"><span data-stu-id="0c825-174">You can repeat these steps as many times as you need to.</span></span> <span data-ttu-id="0c825-175">Es ist eine gute Idee, den Vorgang ein paar Mal durchzugehen, bevor Sie die Synchronisierung vornehmen.</span><span class="sxs-lookup"><span data-stu-id="0c825-175">It's a good idea to go through the process a few times before you synchronize.</span></span>
    
## <a name="additional-resources-on-idfix"></a><span data-ttu-id="0c825-176">Zusätzliche Ressourcen in IdFix</span><span class="sxs-lookup"><span data-stu-id="0c825-176">Additional resources on IdFix</span></span> 

- [<span data-ttu-id="0c825-177">Ausgeschlossene und unterstützte Objekte und Attribute für IdFix</span><span class="sxs-lookup"><span data-stu-id="0c825-177">IdFix excluded and supported objects and attributes</span></span>](idfix-excluded-and-supported-objects-and-attributes.md)  
- [<span data-ttu-id="0c825-178">Microsoft 365 IdFix-Transaktionsprotokoll</span><span class="sxs-lookup"><span data-stu-id="0c825-178">Microsoft 365 IdFix transaction log</span></span>](idfix-transaction-log.md)
    
## <a name="video-training"></a><span data-ttu-id="0c825-179">Videoschulung</span><span class="sxs-lookup"><span data-stu-id="0c825-179">Video training</span></span>

<span data-ttu-id="0c825-180">Weitere Informationen finden Sie in der Lektion [Installieren und Verwenden des IdFix-Tools](https://support.office.com/article/install-and-use-the-idfix-tool-4d81d73c-f172-4fd5-8542-f601c0c96aa9?ui=en-US&rs=en-US&ad=US), bereitgestellt von LinkedIn Learning.</span><span class="sxs-lookup"><span data-stu-id="0c825-180">For more information, see the lesson [Install and use the IdFix tool](https://support.office.com/article/install-and-use-the-idfix-tool-4d81d73c-f172-4fd5-8542-f601c0c96aa9?ui=en-US&rs=en-US&ad=US), brought to you by LinkedIn Learning.</span></span>
  

