---
title: Herunterladen und Ausführen des Office 365 IdFix-Tools
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
description: Hier erfahren Sie, wie Sie das Office 365 IdFix-Tool herunterladen und ausführen, um die Active Directory-Domänendienste (AD DS) vor dem Synchronisieren mit Office 365 zu bereinigen.
ms.openlocfilehash: 4a402cf245ebd20fbc5846908d521469ebfb90c1
ms.sourcegitcommit: 10ae1163f8443c53f19dfad6b7c2b2bb952bf759
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/28/2019
ms.locfileid: "34490752"
---
# <a name="download-and-run-the-office-365-idfix-tool"></a><span data-ttu-id="d51f1-103">Herunterladen und Ausführen des Office 365 IdFix-Tools</span><span class="sxs-lookup"><span data-stu-id="d51f1-103">Download and run the Office 365 IdFix tool</span></span>


<span data-ttu-id="d51f1-104">IdFix identifiziert Fehler wie Duplikate und Formatierungsprobleme in Ihrer Active Directory-Domänendienste Domäne (AD DS), bevor Sie mit Office 365 synchronisieren.</span><span class="sxs-lookup"><span data-stu-id="d51f1-104">IdFix identifies errors such as duplicates and formatting problems in your Active Directory Domain Services (AD DS) domain before you synchronize to Office 365.</span></span> 
  
<span data-ttu-id="d51f1-105">Um diese Aufgabe erfolgreich abzuschließen, sollten Sie mit Benutzer-, Gruppen-und Kontaktobjekten in AD DS komfortabel arbeiten.</span><span class="sxs-lookup"><span data-stu-id="d51f1-105">To finish this task successfully, you should be comfortable working with user, group, and contact objects in AD DS.</span></span>
  
<span data-ttu-id="d51f1-106">Wenn Sie diese Aufgabe nicht ausführen können, gibt es einige andere Möglichkeiten.</span><span class="sxs-lookup"><span data-stu-id="d51f1-106">If you can't complete this task, there are a couple of other things you can do.</span></span> <span data-ttu-id="d51f1-107">Diese Methoden sind möglicherweise einfacher, aber Sie können auch länger dauern oder andere Nachteile haben.</span><span class="sxs-lookup"><span data-stu-id="d51f1-107">These methods might be easier, but they might also take longer or have other drawbacks.</span></span> <span data-ttu-id="d51f1-108">Dies sind:</span><span class="sxs-lookup"><span data-stu-id="d51f1-108">They are:</span></span>
  
- <span data-ttu-id="d51f1-109">**Ausführen der Verzeichnissynchronisierung ohne Ausführen von IdFix**</span><span class="sxs-lookup"><span data-stu-id="d51f1-109">**Run directory synchronization without running IdFix**</span></span> 

  <span data-ttu-id="d51f1-110">Sie können Ihr Verzeichnis ohne Verwendung des IdFix-Tools synchronisieren, dies wird jedoch nicht empfohlen.</span><span class="sxs-lookup"><span data-stu-id="d51f1-110">You can synchronize your directory without using the IdFix tool, but we don't recommend it.</span></span> <span data-ttu-id="d51f1-111">Das Beheben von Fehlern vor der Synchronisierung dauert kürzer und bietet häufig einen reibungslosen Übergang zur Cloud.</span><span class="sxs-lookup"><span data-stu-id="d51f1-111">Fixing errors before you synchronize takes less time and often provides a smoother transition to the cloud.</span></span> 

- <span data-ttu-id="d51f1-112">**Einen Berater einstellen**</span><span class="sxs-lookup"><span data-stu-id="d51f1-112">**Hire a consultant**</span></span> 

  <span data-ttu-id="d51f1-113">Wenn Sie Expertenhilfe erhalten, können Sie Ihre Benutzer schnell in Betrieb nehmen und Ihr Verzeichnis synchronisieren.</span><span class="sxs-lookup"><span data-stu-id="d51f1-113">Getting expert help can get your users up and running quickly and your directory synchronized.</span></span> 
    
## <a name="what-you-need-to-run-idfix"></a><span data-ttu-id="d51f1-114">Was Sie zum Ausführen von IdFix benötigen</span><span class="sxs-lookup"><span data-stu-id="d51f1-114">What you need to run IdFix</span></span>

<span data-ttu-id="d51f1-115">Am einfachsten können Sie IdFix auf einen Computer herunterladen, der mit Ihrer AD DS Domäne verbunden ist.</span><span class="sxs-lookup"><span data-stu-id="d51f1-115">The easiest way to get IdFix up and running is to download it onto a computer that is joined to your AD DS domain.</span></span> <span data-ttu-id="d51f1-116">Sie können es auf dem Domänencontroller ausführen, wenn Sie möchten, es ist jedoch nicht erforderlich.</span><span class="sxs-lookup"><span data-stu-id="d51f1-116">You can run it on the domain controller if you want, but it's not necessary.</span></span>
  
### <a name="idfix-hardware-requirements"></a><span data-ttu-id="d51f1-117">IdFix-Hardwareanforderungen</span><span class="sxs-lookup"><span data-stu-id="d51f1-117">IdFix hardware requirements</span></span>

<span data-ttu-id="d51f1-118">Der Computer, auf dem Sie IdFix herunterladen, muss diese minimalen Hardwareanforderungen erfüllen:</span><span class="sxs-lookup"><span data-stu-id="d51f1-118">The computer where you download IdFix needs to meet these minimum hardware requirements:</span></span>
  
- <span data-ttu-id="d51f1-119">4 GB RAM </span><span class="sxs-lookup"><span data-stu-id="d51f1-119">4 GB RAM</span></span>
- <span data-ttu-id="d51f1-120">2 GB Speicherplatz auf der Festplatte</span><span class="sxs-lookup"><span data-stu-id="d51f1-120">2 GB of hard disk space</span></span>
   
### <a name="idfix-software-requirements"></a><span data-ttu-id="d51f1-121">IdFix-Softwareanforderungen</span><span class="sxs-lookup"><span data-stu-id="d51f1-121">IdFix software requirements</span></span>

<span data-ttu-id="d51f1-122">Der Computer, auf dem Sie IdFix herunterladen, muss derselben AD DS Domäne hinzugefügt werden, aus der Sie Benutzer mit Office 365 synchronisieren möchten.</span><span class="sxs-lookup"><span data-stu-id="d51f1-122">The computer where you download IdFix needs to be joined to the same AD DS domain from which you want to synchronize users to Office 365.</span></span> 

<span data-ttu-id="d51f1-123">Auf dem Computer muss auch .NET Framework 4,0 installiert sein.</span><span class="sxs-lookup"><span data-stu-id="d51f1-123">The computer also needs to have .NET Framework 4.0 installed.</span></span> <span data-ttu-id="d51f1-124">Wenn Sie Windows Server 2008 oder höher durchführen, ist die .NET Framework wahrscheinlich bereits installiert.</span><span class="sxs-lookup"><span data-stu-id="d51f1-124">If you are running Windows Server 2008 or later, the .NET Framework is probably already installed.</span></span> <span data-ttu-id="d51f1-125">Wenn dies nicht der Fall ist, können Sie [.NET 4,0 aus dem Download Center](https://go.microsoft.com/fwlink/p/?LinkId=400475) oder mit Windows Update herunterladen.</span><span class="sxs-lookup"><span data-stu-id="d51f1-125">If not, you can [download .NET 4.0 from the download center](https://go.microsoft.com/fwlink/p/?LinkId=400475) or with Windows Update.</span></span> 
  
### <a name="idfix-permissions-requirements"></a><span data-ttu-id="d51f1-126">IdFix-Berechtigungsanforderungen</span><span class="sxs-lookup"><span data-stu-id="d51f1-126">IdFix permissions requirements</span></span>

<span data-ttu-id="d51f1-127">Das Benutzerkonto, das Sie zum Ausführen von IdFix verwenden, muss über Lese-und Schreibzugriff auf die AD DS Domäne verfügen.</span><span class="sxs-lookup"><span data-stu-id="d51f1-127">The user account that you use to run IdFix must have read and write access to the AD DS domain.</span></span>
  
<span data-ttu-id="d51f1-128">Wenn Sie nicht sicher sind, ob Ihr Benutzerkonto diese Anforderungen erfüllt, und Sie nicht sicher sind, wie Sie überprüfen möchten, können Sie IdFix trotzdem herunterladen und ausführen.</span><span class="sxs-lookup"><span data-stu-id="d51f1-128">If you aren't sure if your user account meets these requirements, and you're not sure how to check, you can still download and run IdFix.</span></span> <span data-ttu-id="d51f1-129">Wenn Ihr Benutzerkonto nicht über die richtigen Berechtigungen verfügt, wird IdFix einfach einen Fehler angezeigt, wenn Sie versuchen, es auszuführen.</span><span class="sxs-lookup"><span data-stu-id="d51f1-129">If your user account doesn't have the right permissions, IdFix will simply display an error when you try to run it.</span></span>
  
## <a name="download-and-extract-idfix"></a><span data-ttu-id="d51f1-130">Herunterladen und Extrahieren von IdFix</span><span class="sxs-lookup"><span data-stu-id="d51f1-130">Download and extract IdFix</span></span>

<span data-ttu-id="d51f1-131">Befolgen Sie diese Anweisungen.</span><span class="sxs-lookup"><span data-stu-id="d51f1-131">Follow these instructions.</span></span> 
  
1. <span data-ttu-id="d51f1-132">Melden Sie sich bei dem Computer an, auf dem Sie das IdFix-Tool ausführen möchten.</span><span class="sxs-lookup"><span data-stu-id="d51f1-132">Sign in to the computer where you want to run the IdFix tool.</span></span>
    
2. <span data-ttu-id="d51f1-133">Wechseln Sie zur Microsoft-Download Website für das [IdFix Dirsync-Tool zur Fehlerbehebung](https://go.microsoft.com/fwlink/?linkid=867219).</span><span class="sxs-lookup"><span data-stu-id="d51f1-133">Go to the Microsoft download site for the [IdFix DirSync Error Remediation Tool](https://go.microsoft.com/fwlink/?linkid=867219).</span></span>
    
3. <span data-ttu-id="d51f1-134">Laden Sie die ZIP-Datei herunter, und öffnen Sie Sie.</span><span class="sxs-lookup"><span data-stu-id="d51f1-134">Download and open the zip file.</span></span>
    
3. <span data-ttu-id="d51f1-135">Wählen Sie im Fenster **IdFix** **extrahieren**aus, und extrahieren Sie dann **alle**.</span><span class="sxs-lookup"><span data-stu-id="d51f1-135">In the **IdFix** window, choose **Extract**, and then **Extract all**.</span></span> <span data-ttu-id="d51f1-136">Standardmäßig wird IdFix in `C:\Users\<your user name>\Documents\IdFix`extrahiert.</span><span class="sxs-lookup"><span data-stu-id="d51f1-136">By default, IdFix is extracted to `C:\Users\<your user name>\Documents\IdFix`.</span></span> 
    
6. <span data-ttu-id="d51f1-137">Wählen Sie **extrahieren**aus.</span><span class="sxs-lookup"><span data-stu-id="d51f1-137">Choose **Extract**.</span></span>

<span data-ttu-id="d51f1-138">Diese Anweisungen wurden mit Internet Explorer auf einem Server mit Windows Server 2016 ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="d51f1-138">These instructions were done with Internet Explorer on a server running Windows Server 2016.</span></span> <span data-ttu-id="d51f1-139">Wenn Sie eine andere Version von Windows oder einen anderen Browser verwenden, sind Ihre Schritte möglicherweise unterschiedlich.</span><span class="sxs-lookup"><span data-stu-id="d51f1-139">If you're using a different version of Windows or a different browser, your steps might vary.</span></span>
    
## <a name="run-the-idfix-tool"></a><span data-ttu-id="d51f1-140">Ausführen des IdFix-Tools</span><span class="sxs-lookup"><span data-stu-id="d51f1-140">Run the IdFix tool</span></span>

<span data-ttu-id="d51f1-141">Nachdem Sie IdFix heruntergeladen und extrahiert haben, führen Sie ihn aus, um nach Problemen in Ihrer AD DS Domäne zu suchen.</span><span class="sxs-lookup"><span data-stu-id="d51f1-141">After you download and extract IdFix, run it to search for problems in your AD DS domain.</span></span>
  
1. <span data-ttu-id="d51f1-142">Melden Sie sich bei dem Computer, auf dem Sie IdFix heruntergeladen haben, mit einem Konto an, das über Lese-/Schreibzugriff auf Ihre AD DS Domäne verfügt.</span><span class="sxs-lookup"><span data-stu-id="d51f1-142">Using an account that has read/write access to your AD DS domain, sign in to the computer where you downloaded IdFix.</span></span>
    
2. <span data-ttu-id="d51f1-143">Wechseln Sie im Datei-Explorer zu dem Speicherort, an dem Sie IdFix extrahiert haben.</span><span class="sxs-lookup"><span data-stu-id="d51f1-143">In File Explorer, go to the location where you extracted IdFix.</span></span> <span data-ttu-id="d51f1-144">Wenn Sie während der Extraktion den Standardordner ausgewählt haben, wechseln `C:\Users\<your user name>\Documents\IdFix`Sie zu.</span><span class="sxs-lookup"><span data-stu-id="d51f1-144">If you chose the default folder during extraction, go to `C:\Users\<your user name>\Documents\IdFix`.</span></span> 
    
3. <span data-ttu-id="d51f1-145">Doppelklicken Sie auf **IdFix. exe**.</span><span class="sxs-lookup"><span data-stu-id="d51f1-145">Double-click **IdFix.exe**.</span></span> 
  
4. <span data-ttu-id="d51f1-146">Standardmäßig verwendet IdFix den mehrmandantenfähigen Regelsatz, um die Einträge in Ihrem Verzeichnis zu testen.</span><span class="sxs-lookup"><span data-stu-id="d51f1-146">By default, IdFix uses the Multi-Tenant rule set to test the entries in your directory.</span></span> <span data-ttu-id="d51f1-147">Dies ist der richtige Regelsatz für die meisten Office 365 Kunden.</span><span class="sxs-lookup"><span data-stu-id="d51f1-147">This is the right rule set for most Office 365 customers.</span></span> <span data-ttu-id="d51f1-148">Wenn Sie jedoch ein Office 365 dedizierter oder internationaler Traffic in Arms Regulations (ITAR))-Kunde sind, können Sie IdFix so konfigurieren, dass stattdessen der dedizierte Regelsatz verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="d51f1-148">However, if you are an Office 365 Dedicated or International Traffic in Arms Regulations (ITAR)) customer, you can configure IdFix to use the Dedicated rule set instead.</span></span> <span data-ttu-id="d51f1-149">Wenn Sie nicht sicher sind, welche Art von Kunde Sie haben, können Sie diesen Schritt gefahrlos überspringen.</span><span class="sxs-lookup"><span data-stu-id="d51f1-149">If you aren't sure what type of customer you are, you can safely skip this step.</span></span> <span data-ttu-id="d51f1-150">Klicken Sie auf das Zahnradsymbol in der Menüleiste, und wählen Sie dann **dediziert**aus, um den Regelsatz auf "dediziert" festzulegen.</span><span class="sxs-lookup"><span data-stu-id="d51f1-150">To set the rule set to Dedicated, click the gear icon in the menu bar, and then choose **Dedicated**.</span></span>
    
5. <span data-ttu-id="d51f1-151">Wählen Sie **Abfrage**aus.</span><span class="sxs-lookup"><span data-stu-id="d51f1-151">Choose **Query**.</span></span>
    
    ![Wählen Sie Abfrage in IdFix aus.](media/a07a7aa7-d0ac-4817-8757-946019813a57.JPG)
  
6. <span data-ttu-id="d51f1-153">Standardmäßig durchsucht IdFix das gesamte Verzeichnis nach Fehlern.</span><span class="sxs-lookup"><span data-stu-id="d51f1-153">By default, IdFix searches the entire directory for errors.</span></span>
    
    <span data-ttu-id="d51f1-154">Je nach der Größe Ihres Verzeichnisses kann das Ausführen der Abfrage eine Weile dauern.</span><span class="sxs-lookup"><span data-stu-id="d51f1-154">Depending on the size of your directory, running the query can take a while.</span></span> <span data-ttu-id="d51f1-155">Sie können den Fortschritt am unteren Rand des Hauptfensters des Tools überwachen.</span><span class="sxs-lookup"><span data-stu-id="d51f1-155">You can watch the progress at the bottom of the tool's main window.</span></span> <span data-ttu-id="d51f1-156">Wenn Sie auf **Abbrechen**klicken, müssen Sie von Anfang an neu starten.</span><span class="sxs-lookup"><span data-stu-id="d51f1-156">If you click **Cancel**, you'll need to restart from the beginning.</span></span>
  
7. <span data-ttu-id="d51f1-157">Nachdem IdFix die Abfrage abgeschlossen hat, können Sie Ihr Verzeichnis synchronisieren, wenn keine Fehler vorliegen.</span><span class="sxs-lookup"><span data-stu-id="d51f1-157">After IdFix completes the query, you can synchronize your directory if there are no errors.</span></span> <span data-ttu-id="d51f1-158">Wenn in Ihrem Verzeichnis Fehler vorliegen, wird empfohlen, dass Sie diese vor der Synchronisierung korrigieren.</span><span class="sxs-lookup"><span data-stu-id="d51f1-158">If there are errors in your directory, it is recommended that you fix them before you synchronize.</span></span> <span data-ttu-id="d51f1-159">Weitere Informationen finden Sie unter [Prepare Directory attributes for Synchronization with Office 365](prepare-directory-attributes-for-synch-with-idfix.md) .</span><span class="sxs-lookup"><span data-stu-id="d51f1-159">See [prepare directory attributes for synchronization with Office 365](prepare-directory-attributes-for-synch-with-idfix.md) for more information.</span></span>
    
    <span data-ttu-id="d51f1-160">Es ist zwar nicht zwingend erforderlich, die Fehler vor der Synchronisierung zu beheben, es wird jedoch dringend empfohlen, dass Sie mindestens alle von IdFix zurückgegebenen Fehler überprüfen.</span><span class="sxs-lookup"><span data-stu-id="d51f1-160">While it is not mandatory to fix the errors before you synchronize, we strongly recommend that you at least review all the errors returned by IdFix.</span></span>
    
    <span data-ttu-id="d51f1-161">Jeder Fehler wird in einer separaten Zeile im Hauptfenster des Tools angezeigt.</span><span class="sxs-lookup"><span data-stu-id="d51f1-161">Each error is displayed in a separate row in the tool's main window .</span></span> 
    
8. <span data-ttu-id="d51f1-162">Wenn Sie mit der vorgeschlagenen Änderung in der Spalte **Aktualisieren** einverstanden sind, wählen Sie in der Spalte **Aktion** aus, was Sie von IdFix ausführen möchten, um die Änderung zu implementieren, und klicken Sie dann auf über **nehmen**.</span><span class="sxs-lookup"><span data-stu-id="d51f1-162">If you agree with the suggested change in the **UPDATE** column, in the **ACTION** column select what you want IdFix to do to implement the change and then click **Apply**.</span></span> <span data-ttu-id="d51f1-163">Wenn Sie auf über **nehmen**klicken, nimmt das Tool die Änderungen im Verzeichnis vor.</span><span class="sxs-lookup"><span data-stu-id="d51f1-163">When you click **Apply**, the tool makes the changes in the directory.</span></span>
    
    <span data-ttu-id="d51f1-164">Sie müssen nach jeder Aktualisierung nicht auf **anwenden** klicken.</span><span class="sxs-lookup"><span data-stu-id="d51f1-164">You don't have to click **Apply** after each update.</span></span> <span data-ttu-id="d51f1-165">Stattdessen können Sie mehrere Fehler beheben, bevor Sie auf über **nehmen** klicken, und IdFix ändert alle gleichzeitig.</span><span class="sxs-lookup"><span data-stu-id="d51f1-165">Instead, you can fix several errors before you click **Apply** and IdFix will change them all at the same time.</span></span> <span data-ttu-id="d51f1-166">Sie können die Fehler nach Fehlertyp sortieren, indem Sie oben in der Spalte, in der die Fehlertypen aufgeführt werden, auf **Fehler** klicken.</span><span class="sxs-lookup"><span data-stu-id="d51f1-166">You can sort the errors by error type by clicking **ERROR** at the top of the column that lists the error types.</span></span> 
    
    <span data-ttu-id="d51f1-167">Eine Strategie besteht darin, alle Fehler desselben Typs zu beheben. beheben Sie beispielsweise zuerst alle Duplikate, und wenden Sie Sie an.</span><span class="sxs-lookup"><span data-stu-id="d51f1-167">One strategy is to fix all the errors of the same type; for example, fix all the duplicates first, and apply them.</span></span> <span data-ttu-id="d51f1-168">Korrigieren Sie als nächstes die Zeichenformat Fehler usw.</span><span class="sxs-lookup"><span data-stu-id="d51f1-168">Next, fix the character format errors, and so on.</span></span> <span data-ttu-id="d51f1-169">Jedes Mal, wenn Sie die Änderungen anwenden, erstellt das IdFix-Tool eine separate Protokolldatei, mit der Sie Ihre Änderungen rückgängig machen können, falls Sie einen Fehler machen.</span><span class="sxs-lookup"><span data-stu-id="d51f1-169">Each time you apply the changes, the IdFix tool creates a separate log file that you can use to undo your changes in case you make a mistake.</span></span> <span data-ttu-id="d51f1-170">Das [Transaktionsprotokoll](idfix-transaction-log.md) wird in dem Ordner gespeichert, in dem Sie IdFix extrahiert haben, was _C:\Users\<Ihrem Benutzernamen> \documents\idfix_ Standardmäßig entspricht.</span><span class="sxs-lookup"><span data-stu-id="d51f1-170">The [transaction log](idfix-transaction-log.md) is stored in the folder where you extracted IdFix, which is _C:\Users\<your user name>\Documents\IdFix_ by default.</span></span> 
    
    ![Beheben von Fehlern in IdFix.](media/5f051070-652c-4be7-98bf-312295e32371.png)
  
9. <span data-ttu-id="d51f1-172">Nachdem Sie alle Änderungen am Verzeichnis vorgenommen haben, führen Sie IdFix erneut aus, um sicherzustellen, dass die von Ihnen vorgenommenen Korrekturen keine neuen Fehler verursachen.</span><span class="sxs-lookup"><span data-stu-id="d51f1-172">After all of your changes are made to the directory, run IdFix again to ensure that the fixes you made didn't introduce new errors.</span></span> <span data-ttu-id="d51f1-173">Sie können diese Schritte so oft wie nötig wiederholen.</span><span class="sxs-lookup"><span data-stu-id="d51f1-173">You can repeat these steps as many times as you need to.</span></span> <span data-ttu-id="d51f1-174">Es empfiehlt sich, den Prozess einige Male vor dem Synchronisieren durchzugehen.</span><span class="sxs-lookup"><span data-stu-id="d51f1-174">It's a good idea to go through the process a few times before you synchronize.</span></span>
    
## <a name="additional-resources-on-idfix"></a><span data-ttu-id="d51f1-175">Zusätzliche Ressourcen auf IdFix</span><span class="sxs-lookup"><span data-stu-id="d51f1-175">Additional resources on IdFix</span></span> 

- [<span data-ttu-id="d51f1-176">Ausgeschlossene und unterstützte Objekte und Attribute für IdFix</span><span class="sxs-lookup"><span data-stu-id="d51f1-176">IdFix excluded and supported objects and attributes</span></span>](idfix-excluded-and-supported-objects-and-attributes.md)  
- [<span data-ttu-id="d51f1-177">Office 365 IdFix-Transaktionsprotokoll</span><span class="sxs-lookup"><span data-stu-id="d51f1-177">Office 365 IdFix transaction log</span></span>](idfix-transaction-log.md)
    
## <a name="video-training"></a><span data-ttu-id="d51f1-178">Videoschulung</span><span class="sxs-lookup"><span data-stu-id="d51f1-178">Video training</span></span>

<span data-ttu-id="d51f1-179">Weitere Informationen finden Sie in der Lektion [Installieren und Verwenden des IdFix-Tools](https://support.office.com/article/install-and-use-the-idfix-tool-4d81d73c-f172-4fd5-8542-f601c0c96aa9?ui=en-US&rs=en-US&ad=US), das Ihnen von LinkedIn Learning zur Verfügung gestellt wird.</span><span class="sxs-lookup"><span data-stu-id="d51f1-179">For more information, see the lesson [Install and use the IdFix tool](https://support.office.com/article/install-and-use-the-idfix-tool-4d81d73c-f172-4fd5-8542-f601c0c96aa9?ui=en-US&rs=en-US&ad=US), brought to you by LinkedIn Learning.</span></span>
  

