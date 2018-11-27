---
title: Installieren und Ausführen des Office 365 IdFix-Tools
ms.author: robmazz
author: robmazz
manager: laurawi
ms.audience: Admin
ms.topic: get-started-article
f1_keywords:
- O365E_HRCSetupAADConnectIDFixLM617036
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
ms.assetid: f4bd2439-3e41-4169-99f6-3fabdfa326ac
description: Informationen zum Installieren und Ausführen des Office 365-IdFix-Tools, die die active Directory-Bereinigung unterstützen, bevor Sie die Synchronisierung mit Office 365 vornehmen.
ms.openlocfilehash: c485d8397aa32005a34b77f886b9bc8f4e857f1b
ms.sourcegitcommit: 9c493c4e18e83491d106c5e9bab55d1a89298879
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/26/2018
ms.locfileid: "26674429"
---
# <a name="install-and-run-the-office-365-idfix-tool"></a><span data-ttu-id="036e4-103">Installieren und Ausführen des Office 365 IdFix-Tools</span><span class="sxs-lookup"><span data-stu-id="036e4-103">Install and run the Office 365 IdFix tool</span></span>

<span data-ttu-id="036e4-104">IdFix identifiziert Fehler wie Duplikate und Probleme mit der Formatierung in Ihrem Verzeichnis aus, bevor Sie zu Office 365 synchronisieren.</span><span class="sxs-lookup"><span data-stu-id="036e4-104">IdFix identifies errors such as duplicates and formatting problems in your directory before you synchronize to Office 365.</span></span> 
  
<span data-ttu-id="036e4-105">Um diese Aufgabe erfolgreich abgeschlossen wurde, sollte das Arbeiten mit Benutzer-, Gruppen- und Kontaktobjekten in Active Directory vertraut sein.</span><span class="sxs-lookup"><span data-stu-id="036e4-105">To finish this task successfully, you should be comfortable working with user, group, and contact objects in Active Directory.</span></span>
  
<span data-ttu-id="036e4-p101">Wenn Sie diese Aufgabe ausführen können, sind einige andere Aspekte, die Sie ausführen können. Diese Methoden möglicherweise ist es einfacher, aber sie können auch länger dauern oder andere Nachteile haben. Sie sind:</span><span class="sxs-lookup"><span data-stu-id="036e4-p101">If you can't complete this task, there are a couple of other things you can do. These methods might be easier, but they might also take longer or have other drawbacks. They are:</span></span>
  
- <span data-ttu-id="036e4-p102">**Directory-Synchronisierung ohne Ausführen IdFix.** Sie können Ihr Verzeichnis synchronisieren, ohne das IdFix-Tool ausführen, aber es wird nicht empfohlen. Beheben von Fehlern, bevor Sie synchronisieren weniger Zeit und bietet oftmals einen fließender Übergang in die Cloud.</span><span class="sxs-lookup"><span data-stu-id="036e4-p102">**Run directory synchronization without running IdFix.** You can synchronize your directory without running the IdFix tool, but we don't recommend it. Fixing errors before you synchronize takes less time and often provides a smoother transition to the cloud.</span></span> 
- <span data-ttu-id="036e4-p103">**Stellen Sie einen Berater ein.** Durch Expertenhilfe können Ihre Benutzer schnell loslegen, und Ihr Verzeichnis wird synchronisiert.</span><span class="sxs-lookup"><span data-stu-id="036e4-p103">**Hire a consultant.** Getting expert help can get your users up and running quickly and your directory synchronized.</span></span> 
    
## <a name="what-you-need-to-run-idfix"></a><span data-ttu-id="036e4-114">Voraussetzungen für das Ausführen von IdFix</span><span class="sxs-lookup"><span data-stu-id="036e4-114">What you need to run IdFix</span></span>

<span data-ttu-id="036e4-p104">Die einfachste Einstieg IdFix zum ist und ausgeführt wird, ihn auf einem Computer zu installieren, die mit der Domäne verbunden ist. Sie können ihn auf dem Domänencontroller ausführen, wenn Sie möchten, aber es nicht erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="036e4-p104">The easiest way to get IdFix up and running is to install it on a computer that is joined to your domain. You can run it on the domain controller if you want, but it's not necessary.</span></span>
  
### <a name="idfix-hardware-requirements"></a><span data-ttu-id="036e4-117">IdFix-Hardwareanforderungen</span><span class="sxs-lookup"><span data-stu-id="036e4-117">IdFix hardware requirements</span></span>

<span data-ttu-id="036e4-118">Der Computer, auf dem Sie IdFix installieren, muss diese Mindestanforderungen an die Hardware erfüllt:</span><span class="sxs-lookup"><span data-stu-id="036e4-118">The computer where you install IdFix needs to meet these minimum hardware requirements:</span></span>
  
- <span data-ttu-id="036e4-119">4 GB RAM</span><span class="sxs-lookup"><span data-stu-id="036e4-119">4 GB RAM</span></span>
- <span data-ttu-id="036e4-120">2 GB freier Festplattenspeicher</span><span class="sxs-lookup"><span data-stu-id="036e4-120">2 GB of hard disk space</span></span>
    
### <a name="idfix-software-requirements"></a><span data-ttu-id="036e4-121">IdFix-Softwareanforderungen</span><span class="sxs-lookup"><span data-stu-id="036e4-121">IdFix software requirements</span></span>

<span data-ttu-id="036e4-p105">Der Computer, auf dem Sie IdFix installieren, muss mit derselben Active Directory-Domäne verknüpft werden aus der Sie Benutzer zu Office 365 synchronisieren möchten. Der Computer muss auch .NET Framework 4.0 installiert haben.</span><span class="sxs-lookup"><span data-stu-id="036e4-p105">The computer where you install IdFix needs to be joined to the same Active Directory domain from which you want to synchronize users to Office 365. The computer also needs to have .NET Framework 4.0 installed.</span></span> 
  
<span data-ttu-id="036e4-p106">Wenn Sie Windows Server 2008 oder Windows Server 2012 ausgeführt werden, ist möglicherweise bereits .NET Framework installiert. Wenn nicht, können Sie auf [Download .NET 4.0 aus dem Downloadcenter](https://go.microsoft.com/fwlink/p/?LinkId=400475) oder über Windows Update.</span><span class="sxs-lookup"><span data-stu-id="036e4-p106">If you are running Windows Server 2008 or Windows Server 2012, then .NET Framework is probably already installed. If not, you can [download .NET 4.0 from the download center](https://go.microsoft.com/fwlink/p/?LinkId=400475) or via Windows Update.</span></span> 
  
### <a name="idfix-permissions-requirements"></a><span data-ttu-id="036e4-126">IdFix-Berechtigungsanforderungen</span><span class="sxs-lookup"><span data-stu-id="036e4-126">IdFix permissions requirements</span></span>

<span data-ttu-id="036e4-127">Das Benutzerkonto, das Sie zum Ausführen von IdFix verwenden, muss über Lese-/Schreibzugriff auf das Verzeichnis verfügen.</span><span class="sxs-lookup"><span data-stu-id="036e4-127">The user account that you use to run IdFix needs to have read/write access to the directory.</span></span>
  
<span data-ttu-id="036e4-p107">Wenn Sie nicht sicher sind, wenn Ihr Benutzerkonto diese Anforderungen erfüllt, und Sie sind nicht sicher sind, wie Sie überprüfen, können Sie installieren und Ausführen von IdFix. Wenn Ihr Benutzerkonto nicht über die richtigen Berechtigungen verfügen, wird IdFix einfach einen Fehler angezeigt, wenn Sie versuchen, um Sie auszuführen.</span><span class="sxs-lookup"><span data-stu-id="036e4-p107">If you aren't sure if your user account meets these requirements, and you're not sure how to check, you can still install and run IdFix. If your user account doesn't have the right permissions, IdFix will simply display an error when you try to run it.</span></span>
  
## <a name="install-idfix"></a><span data-ttu-id="036e4-130">Installieren von IdFix</span><span class="sxs-lookup"><span data-stu-id="036e4-130">Install IdFix</span></span>

<span data-ttu-id="036e4-131">Zum Installieren von IdFix herunter und Entpacken Sie **IdFix.exe**:</span><span class="sxs-lookup"><span data-stu-id="036e4-131">To install IdFix, download and unzip **IdFix.exe**:</span></span> 
  
1. <span data-ttu-id="036e4-132">Melden Sie sich am Computer an, auf dem Sie das IdFix-Tool installieren möchten.</span><span class="sxs-lookup"><span data-stu-id="036e4-132">Log on to the computer where you want to install the IdFix tool.</span></span>
    
2. <span data-ttu-id="036e4-133">Wechseln Sie zu Microsoft-Downloadwebsite für das [IdFix DirSync Error Remediation-Tool](https://go.microsoft.com/fwlink/?linkid=867219).</span><span class="sxs-lookup"><span data-stu-id="036e4-133">Go to the Microsoft download site for the [IdFix DirSync Error Remediation Tool](https://go.microsoft.com/fwlink/?linkid=867219).</span></span>
    
3. <span data-ttu-id="036e4-134">Klicken Sie auf **Herunterladen**.</span><span class="sxs-lookup"><span data-stu-id="036e4-134">Choose **Download**.</span></span>
    
4. <span data-ttu-id="036e4-135">Wenn Sie aufgefordert werden, wählen Sie **Ausführen**aus.</span><span class="sxs-lookup"><span data-stu-id="036e4-135">When prompted, choose **Run**.</span></span>
    
5. <span data-ttu-id="036e4-p108">Klicken Sie im Dialogfeld **WinZip Self-Extractor** in das Textfeld **Extrahieren nach der Ordner** Geben Sie, oder wechseln Sie zum Speicherort, in dem Sie das IdFix-Tool installieren möchten. Standardmäßig wird in IdFix installiert `C:\Deployment Tools\`.</span><span class="sxs-lookup"><span data-stu-id="036e4-p108">On the **WinZip Self-Extractor** dialog box, in the **Unzip to folder** text box, type or browse to the location where you want to install the IdFix tool. By default, IdFix is installed into `C:\Deployment Tools\`.</span></span> 
    
6. <span data-ttu-id="036e4-138">Wählen Sie auf **Unzip**.</span><span class="sxs-lookup"><span data-stu-id="036e4-138">Choose **Unzip**.</span></span>
    
## <a name="run-the-idfix-tool"></a><span data-ttu-id="036e4-139">Führen Sie das IdFix-Tool aus.</span><span class="sxs-lookup"><span data-stu-id="036e4-139">Run the IdFix tool</span></span>

<span data-ttu-id="036e4-140">Führen Sie nach dem Installieren von IdFix das Tool zur Problemsuche in Ihrem Verzeichnis aus:</span><span class="sxs-lookup"><span data-stu-id="036e4-140">After you install IdFix, run the tool to search for problems in your directory:</span></span>
  
1. <span data-ttu-id="036e4-141">Melden Sie sich unter Verwendung eines Kontos mit Lese-/Schreibzugriff auf das Verzeichnis am Computer an, auf dem Sie IdFix installiert haben.</span><span class="sxs-lookup"><span data-stu-id="036e4-141">Using an account that has read/write access to the directory, log on to the computer where you installed IdFix.</span></span>
    
2. <span data-ttu-id="036e4-p109">Wechseln Sie im Datei-Explorer zu dem Speicherort, in dem Sie IdFix installiert haben. Wenn Sie während der Installation den Standardordner ausgewählt haben, fahren Sie mit `C:\Deployment Tools\IdFix`.</span><span class="sxs-lookup"><span data-stu-id="036e4-p109">In File Explorer, go to the location where you installed IdFix. If you chose the default folder during installation, go to `C:\Deployment Tools\IdFix`.</span></span>
    
3. <span data-ttu-id="036e4-144">Doppelklicken Sie auf **IdFix.exe**.</span><span class="sxs-lookup"><span data-stu-id="036e4-144">Double-click **IdFix.exe**.</span></span> 
    
    ![Wählen Sie die Datei IdFix.exe.](media/a9387bbc-991f-41c2-a500-45e3ce574285.JPG)
  
4. <span data-ttu-id="036e4-p110">IdFix verwendet standardmäßig den mehrinstanzenfähigen Regelsatz, der die Einträge in Ihrem Verzeichnis zu testen. Dies ist der richtigen Regelsatz für die meisten Office 365-Kunden. Wenn Sie ein Office 365 dedizierte oder ITAR (International Datenverkehr in Waffen Vorschriften) Kunde sind, können Sie IdFix Verwendung den dedizierten Regelsatz stattdessen konfigurieren. Wenn Sie sicher, dass welche Art von Kunden nicht, die Sie sind, können Sie bedenkenlos diesen Schritt überspringen. Wenn den Regelsatz, dediziert festlegen möchten, klicken Sie auf das Zahnradsymbol in der Menüleiste, und wählen Sie dann **dediziert**.</span><span class="sxs-lookup"><span data-stu-id="036e4-p110">By default, IdFix uses the Multi-Tenant rule set to test the entries in your directory. This is the right rule set for most Office 365 customers. However, if you are an Office 365 Dedicated or ITAR (International Traffic in Arms Regulations) customer, you can configure IdFix to use the Dedicated rule set instead. If you aren't sure what type of customer you are, you can safely skip this step. To set the rule set to Dedicated, click the gear icon in the menu bar and then choose **Dedicated**.</span></span>
    
5. <span data-ttu-id="036e4-151">Wählen Sie auf **Abfrage**.</span><span class="sxs-lookup"><span data-stu-id="036e4-151">Choose **Query**.</span></span>
    
    ![Wählen Sie die Abfrage in IdFix.](media/a07a7aa7-d0ac-4817-8757-946019813a57.JPG)
  
6. <span data-ttu-id="036e4-153">IdFix überprüft das gesamte Verzeichnis standardmäßig auf Fehler.</span><span class="sxs-lookup"><span data-stu-id="036e4-153">By default, IdFix searches the entire directory for errors.</span></span>
    
    <span data-ttu-id="036e4-p111">Je nach der Größe des Verzeichnisses kann das Ausführen der Abfrage eine Weile dauern. Sie können den Fortschritt am unteren Rand des Tools im Hauptfenster überwachen. Wenn Sie auf **Abbrechen**klicken, müssen Sie völlig neu zu starten.</span><span class="sxs-lookup"><span data-stu-id="036e4-p111">Depending on the size of your directory, running the query can take a while. You can watch the progress at the bottom of the tool's main window. If you click **Cancel**, you'll need to restart from the beginning.</span></span>
    
    ![Anzahl von IdFix Abfrage und Fehler.](media/da0198a0-7d4d-4afe-a256-e82f1330ada5.JPG)
  
7. <span data-ttu-id="036e4-p112">Nach Abschluss der IdFix die Abfrage können Sie nun und synchronisieren Ihr Verzeichnis aus, wenn keine Fehler aufgetreten sind. Wenn in Ihrem Verzeichnis Fehler aufgetreten sind, wird empfohlen, dass Sie diese beheben, bevor Sie synchronisieren. Wenn Sie weitere Informationen zu Fehlertypen und Empfehlungen zur die beste Möglichkeit, diese zu beheben möchten, finden Sie unter den Links am Ende dieses Themas.</span><span class="sxs-lookup"><span data-stu-id="036e4-p112">After IdFix completes the query, you can go ahead and synchronize your directory if there are no errors. If there are errors in your directory, it is recommended that you fix them before you synchronize. If you want more specific information about types of errors and recommendations about the best way to fix each of them, see the links at the end of this topic.</span></span> 
    
    <span data-ttu-id="036e4-161">Obwohl es nicht obligatorisch ist, die Fehler vor der Synchronisierung zu beheben, empfehlen wir ausdrücklich, dass Sie wenigstens alle durch IdFix zurückgegebenen Fehler überprüfen.</span><span class="sxs-lookup"><span data-stu-id="036e4-161">While it is not mandatory to fix the errors before you synchronize, we strongly recommend that you at least review all the errors returned by IdFix.</span></span>
    
    <span data-ttu-id="036e4-162">Jeder Fehler wird in einer separaten Zeile im Hauptfenster des Tools angezeigt.</span><span class="sxs-lookup"><span data-stu-id="036e4-162">Each error is displayed in a separate row in the tool's main window .</span></span> 
    
8. <span data-ttu-id="036e4-p113">Wenn Sie mit der vorgeschlagenen Änderung in der Spalte **UPDATE** einverstanden sind, wählen Sie in der Spalte **ACTION**, was IdFix vornehmen soll, um die Änderung zu implementieren. Klicken Sie dann auf **Übernehmen**. Wenn Sie auf **Übernehmen** klicken, nimmt das Tool die Änderungen im Verzeichnis vor.</span><span class="sxs-lookup"><span data-stu-id="036e4-p113">If you agree with the suggested change in the **UPDATE** column, in the **ACTION** column select what you want IdFix to do to implement the change and then click **Apply**. When you click **Apply**, the tool makes the changes in the directory.</span></span>
    
    <span data-ttu-id="036e4-p114">Sie müssen nicht nach jeder Aktualisierung auf **Übernehmen** klicken. Stattdessen können Sie mehrere Fehler beheben, bevor Sie auf **Übernehmen** und IdFix sie alle gleichzeitig ändern. Sie können die Fehler werden vom Fehlertyp sortieren, indem Sie **Fehler** am oberen Rand der Spalte, in der die Fehlertypen aufgelistet.</span><span class="sxs-lookup"><span data-stu-id="036e4-p114">You don't have to click **Apply** after each update. Instead, you can fix several errors before you click **Apply** and IdFix will change them all at the same time. You can sort the errors by error type by clicking **ERROR** at the top of the column that lists the error types.</span></span> 
    
    <span data-ttu-id="036e4-p115">Eine Strategie besteht darin, beheben Sie alle Fehler des gleichen Typs; Angenommen, beheben Sie zuerst alle Duplikate und anwenden. Im nächsten Schritt die Zeichen Formatfehler beheben und so weiter. Jedes Mal Sie die Änderungen zu übernehmen, erstellt das IdFix-Tool eine separate Protokolldatei, die Sie verwenden können, um die Änderungen rückgängig zu machen, für den Fall, dass Sie einen Fehler machen. Das [Transaktionsprotokoll](idfix-transaction-log.md) wird in den Ordner gespeichert, die Sie in IdFix installiert.  _C:\Deployment Tools\IdFix_ standardmäßig.</span><span class="sxs-lookup"><span data-stu-id="036e4-p115">One strategy is to fix all the errors of the same type; for example, fix all the duplicates first, and apply them. Next, fix the character format errors, and so on. Each time you apply the changes, the IdFix tool creates a separate log file that you can use to undo your changes in case you make a mistake. The [transaction log](idfix-transaction-log.md) is stored in the folder that you installed IdFix in.  _C:\Deployment Tools\IdFix_ by default.</span></span> 
    
    ![Korrigieren von Fehlern in IdFix.](media/5f051070-652c-4be7-98bf-312295e32371.png)
  
9. <span data-ttu-id="036e4-p116">Nachdem alle Ihre Änderungen bestehen aus in das Verzeichnis, das Ausführen von IdFix erneut aus, um sicherzustellen, dass die vorgenommene Korrekturen neue Fehler verursachen, haben. Sie können diese Schritte so oft wie gewünscht zu wiederholen. Es ist ratsam, den Prozess ein paar Mal durchlaufen, bevor Sie synchronisieren.</span><span class="sxs-lookup"><span data-stu-id="036e4-p116">After all of your changes are made to the directory, run IdFix again to ensure that the fixes you made didn't introduce new errors. You can repeat these steps as many times as you need to. It's a good idea to go through the process a few times before you synchronize.</span></span>
    
## <a name="i-want-to-refine-my-search-or-dig-deeper-into-the-errors-what-else-can-i-do-with-idfix"></a><span data-ttu-id="036e4-177">Ich möchte meine Suche eingrenzen oder Fehler detaillierter ansehen. Was kann ich sonst noch mit IdFix anfangen?</span><span class="sxs-lookup"><span data-stu-id="036e4-177">I want to refine my search or dig deeper into the errors, what else can I do with IdFix?</span></span>

<span data-ttu-id="036e4-178">Weitergehende Informationen sind in den folgenden Themen verfügbar:</span><span class="sxs-lookup"><span data-stu-id="036e4-178">More in-depth information is available from these topics:</span></span>
  
- <span data-ttu-id="036e4-p117">[Vorbereiten von Verzeichnisattributen für die Synchronisierung mit Office 365 mithilfe des IdFix-Tools](prepare-directory-attributes-for-synch-with-idfix.md) . Nach der Installation des Tools, springen zu diesem Thema für detailliertere Anweisungen zur Ausführung des Tools die häufig auftretender wird, vorgeschlagen, Updates, Beispiele und bewährte Methoden für die auszuführende Aktion, wenn Sie eine große Anzahl von Fehlern vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="036e4-p117">[Prepare directory attributes for synchronization with Office 365 by using the IdFix tool](prepare-directory-attributes-for-synch-with-idfix.md) . After you have installed the tool, jump to this topic for more detailed instructions about running the tool, common errors you will encounter, suggested fixes, examples, and best practices for what to do when you have a large number of errors.</span></span> 
- [<span data-ttu-id="036e4-181">Referenz: Ausgeschlossene und unterstützte Objekte und Attribute für IdFix</span><span class="sxs-lookup"><span data-stu-id="036e4-181">Reference: IdFix excluded and supported objects and attributes</span></span>](idfix-excluded-and-supported-objects-and-attributes.md)  
- [<span data-ttu-id="036e4-182">Referenz: Office 365 IdFix-Transaktionsprotokoll</span><span class="sxs-lookup"><span data-stu-id="036e4-182">Reference: Office 365 IdFix transaction log</span></span>](idfix-transaction-log.md)
    
## <a name="video-training"></a><span data-ttu-id="036e4-183">Videoschulung</span><span class="sxs-lookup"><span data-stu-id="036e4-183">Video training</span></span>

<span data-ttu-id="036e4-184">Weitere Informationen finden Sie unter Lektion [Installieren und verwenden Sie das IDFix-Tool](https://support.office.com/article/install-and-use-the-idfix-tool-4d81d73c-f172-4fd5-8542-f601c0c96aa9?ui=en-US&rs=en-US&ad=US), bereitgestellt von LinkedIn Learning.</span><span class="sxs-lookup"><span data-stu-id="036e4-184">For more information, see the lesson [Install and use the IDFix tool](https://support.office.com/article/install-and-use-the-idfix-tool-4d81d73c-f172-4fd5-8542-f601c0c96aa9?ui=en-US&rs=en-US&ad=US), brought to you by LinkedIn Learning.</span></span>
  

