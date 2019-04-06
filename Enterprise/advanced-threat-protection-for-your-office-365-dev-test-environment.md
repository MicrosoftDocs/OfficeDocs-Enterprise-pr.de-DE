---
title: Advanced Threat Protection für die Office 365-Entwicklungs-/Testumgebung
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: 51019757-20ac-498c-b51e-cae6d41a8c08
description: 'Zusammenfassung: Konfigurieren und Demonstrieren von Office 365 Advanced Threat Protection in der Office 365-Entwicklungs-/Testumgebung'
ms.openlocfilehash: 4ef057480f0ebfb2e64529f39d0db65031b75010
ms.sourcegitcommit: 201d3338d8bbc6da9389e62e2add8a17384fab4d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/02/2019
ms.locfileid: "31037939"
---
# <a name="advanced-threat-protection-for-your-office-365-devtest-environment"></a><span data-ttu-id="d7f27-103">Advanced Threat Protection für die Office 365-Entwicklungs-/Testumgebung</span><span class="sxs-lookup"><span data-stu-id="d7f27-103">Advanced Threat Protection for your Office 365 dev/test environment</span></span>

 <span data-ttu-id="d7f27-104">**Zusammenfassung:** Konfigurieren und Demonstrieren von Office 365 Advanced Threat Protection in der Office 365-Entwicklungs-/Testumgebung</span><span class="sxs-lookup"><span data-stu-id="d7f27-104">**Summary:** Configure and demonstrate Office 365 Advanced Threat Protection in your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="d7f27-p101">Office 365 Advanced Threat Protection (ATP) ist ein Feature von Exchange Online Protection (EOP), das Ihnen hilft, Schadsoftware von Ihrer E-Mail fernzuhalten. Mit ATP erstellen Sie Richtlinien im Exchange Admin Center (EAC) oder im Security &amp; Compliance Center, die helfen sicherzustellen, dass Ihre Benutzer nur auf Links oder Anlagen in E-Mails zugreifen, die als nicht schädlich identifiziert werden. Weitere Informationen finden Sie unter [Advanced Threat Protection für Safe Attachments und Safe Links](https://technet.microsoft.com/library/mt148491%28v=exchg.150%29.aspx).</span><span class="sxs-lookup"><span data-stu-id="d7f27-p101">Office 365 Advanced Threat Protection (ATP) is a feature of Exchange Online Protection (EOP) that helps keep malware out of your email. With ATP, you create policies in the Exchange admin center (EAC) or the Security &amp; Compliance center that help ensure your users access only links or attachments in emails that are identified as not malicious. For more information, see [Advanced threat protection for safe attachments and safe links](https://technet.microsoft.com/library/mt148491%28v=exchg.150%29.aspx).</span></span>
  
<span data-ttu-id="d7f27-108">Mit den Anweisungen in diesem Artikel konfigurieren und testen Sie ATP in Ihrem Office 365-Testabonnement.</span><span class="sxs-lookup"><span data-stu-id="d7f27-108">With the instructions in this article, you configure and test ATP in your Office 365 trial subscription.</span></span>
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a><span data-ttu-id="d7f27-109">Phase 1: Erstellen einer einfachen oder simulierten Office 365-Unternehmensentwicklungs-/-testumgebung</span><span class="sxs-lookup"><span data-stu-id="d7f27-109">Phase 1: Build out your lightweight or simulated enterprise Office 365 dev/test environment</span></span>

<span data-ttu-id="d7f27-110">Wenn Sie ATP nur auf einfache Weise mit den Mindestanforderungen testen möchten, befolgen Sie die Anweisungen in den Phasen 2 und 3 von [Office 365-Entwicklungs-/Testumgebung](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="d7f27-110">If you just want to test ATP in a lightweight way with the minimum requirements, follow the instructions in phases 2 and 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="d7f27-111">Wenn Sie ATP in einem simulierten Unternehmen testen möchten, führen Sie die Schritte in [DirSync für die Office 365-Entwicklungs-/Testumgebung](dirsync-for-your-office-365-dev-test-environment.md) aus.</span><span class="sxs-lookup"><span data-stu-id="d7f27-111">If you want to test ATP in a simulated enterprise, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="d7f27-112">Das Testen von ATP erfordert nicht die simulierte Enterprise-dev/Test-Umgebung, die ein simuliertes Intranet enthält, das mit dem Internet und der Verzeichnissynchronisierung für eine Active Directory-Domänendienste (AD DS) verbunden ist.</span><span class="sxs-lookup"><span data-stu-id="d7f27-112">Testing ATP does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for an Active Directory Domain Services (AD DS) forest.</span></span> <span data-ttu-id="d7f27-113">Dies wird hier als Option bereitgestellt, damit Sie ATP testen und damit in einer Umgebung, die eine typische Organisation darstellt, experimentieren können.</span><span class="sxs-lookup"><span data-stu-id="d7f27-113">It is provided here as an option so that you can test ATP and experiment with it in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-demonstrate-the-default-email-delivery-behavior-of-office-365"></a><span data-ttu-id="d7f27-114">Phase 2: Demonstrieren des standardmäßigen E-Mail-Zustellungsverhaltens von Office 365</span><span class="sxs-lookup"><span data-stu-id="d7f27-114">Phase 2: Demonstrate the default email delivery behavior of Office 365</span></span>

<span data-ttu-id="d7f27-115">In dieser Phase führen Sie vor, dass vor dem Konfigurieren von ATP-Richtlinien potenziell schädliche E-Mails ohne Prüfung oder Maßnahmen zur Risikominderung in Office 365-Postfächer übermittelt werden.</span><span class="sxs-lookup"><span data-stu-id="d7f27-115">In this phase, you demonstrate that before configuring ATP policies, potentially malicious email gets delivered to Office 365 mailboxes without screening or mitigation.</span></span>
  
1. <span data-ttu-id="d7f27-116">Öffnen Sie Internet Explorer, und melden Sie sich an dem Outlook-Konto an, das Sie in Phase 2 von [Office 365-Entwicklungs-/Testumgebung](office-365-dev-test-environment.md) erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="d7f27-116">Open Internet Explorer and sign in to the Outlook account you created in Phase 2 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
    
  - <span data-ttu-id="d7f27-117">Wenn Sie die einfache Office 365-Entwicklungs-/Testumgebung verwenden, öffnen Sie eine private Sitzung von Internet Explorer, und melden Sie sich von Ihrem lokalen Computer aus an.</span><span class="sxs-lookup"><span data-stu-id="d7f27-117">If you are using the lightweight Office 365 dev/test environment, open a private session of Internet Explorer and sign in from your local computer.</span></span>
    
  - <span data-ttu-id="d7f27-118">Wenn Sie die simulierte Office 365-Unternehmensentwicklungs-/-testumgebung verwenden, verwenden Sie das [Azure-Portal](https://portal.azure.com), um sich mit dem virtuellen Computer CLIENT1 zu verbinden, und melden Sie sich dann von CLIENT1 aus an.</span><span class="sxs-lookup"><span data-stu-id="d7f27-118">If you are using the simulated enterprise Office 365 dev/test environment, use the [Azure portal](https://portal.azure.com) to connect to the CLIENT1 virtual machine, and then sign in from CLIENT1.</span></span>
    
2. <span data-ttu-id="d7f27-119">Öffnen Sie Editor, und geben Sie einen Text ein.</span><span class="sxs-lookup"><span data-stu-id="d7f27-119">Run Notepad and enter some text.</span></span>
    
3. <span data-ttu-id="d7f27-120">Speichern Sie die Datei im Ordner „Dokumente" als **getKeys.js**.</span><span class="sxs-lookup"><span data-stu-id="d7f27-120">Save the file to the Documents folder as **getKeys.js**.</span></span>
    
4. <span data-ttu-id="d7f27-121">Klicken Sie auf der Registerkarte „Outlook-Mail" von Internet Explorer auf **Neu**.</span><span class="sxs-lookup"><span data-stu-id="d7f27-121">From the Outlook Mail tab of Internet Explorer, click **New**.</span></span>
    
5. <span data-ttu-id="d7f27-122">Geben Sie in **An** die E-Mail-Adresse für den Namen des globalen Office 365-Administrators Ihres Testabonnements ein.</span><span class="sxs-lookup"><span data-stu-id="d7f27-122">In **To**, type the email address of the Office 365 global administrator name of your trial subscription.</span></span>
    
6. <span data-ttu-id="d7f27-123">Geben Sie für den Betreff **Ihre neuen Schlüssel** ein.</span><span class="sxs-lookup"><span data-stu-id="d7f27-123">For the subject, type **Your new keys**.</span></span>
    
7. <span data-ttu-id="d7f27-124">Geben Sie in den Textbereich **Hier ist die Datei** ein.</span><span class="sxs-lookup"><span data-stu-id="d7f27-124">In the body, type **Here is the file**.</span></span>
    
8. <span data-ttu-id="d7f27-125">Klicken Sie auf **Anfügen**, doppelklicken Sie im Ordner „Dokumente" auf **getKeys.js**, klicken Sie auf **Als Kopie anfügen**, und klicken Sie dann auf **Senden**.</span><span class="sxs-lookup"><span data-stu-id="d7f27-125">Click **Attach**, double-click **getKeys.js** in the Documents folder, click **Attach as a copy**, and then click **Send**.</span></span>
    
9. <span data-ttu-id="d7f27-126">Klicken Sie auf **Neu**.</span><span class="sxs-lookup"><span data-stu-id="d7f27-126">Click **New**.</span></span>
    
10. <span data-ttu-id="d7f27-127">Geben Sie in **An** die E-Mail-Adresse für den Namen des globalen Office 365-Administrators Ihres Testabonnements ein.</span><span class="sxs-lookup"><span data-stu-id="d7f27-127">In **To**, type the email address of the Office 365 global administrator name of your trial subscription.</span></span>
    
11. <span data-ttu-id="d7f27-128">Geben Sie als Betreff **Neue Reisewebsite** ein.</span><span class="sxs-lookup"><span data-stu-id="d7f27-128">For the subject, type **New travel web site**.</span></span>
    
12. <span data-ttu-id="d7f27-129">Geben Sie in den Textbereich **Jemand hat diese Website an mich weitergeleitet** ein.</span><span class="sxs-lookup"><span data-stu-id="d7f27-129">In the body, type **Someone forwarded me this site**.</span></span>
    
13. <span data-ttu-id="d7f27-130">Markieren Sie im Textbereich den Text **diese Website**, und klicken Sie auf der Symbolleiste auf das Linksymbol.</span><span class="sxs-lookup"><span data-stu-id="d7f27-130">In the body, select the **this site** text and click the hyperlink icon in the toolbar.</span></span>
    
14. <span data-ttu-id="d7f27-131">Geben Sie in **URL** den Text **http://www.spamlink.contoso.com/** ein, klicken Sie auf **OK** und dann auf **Senden**.</span><span class="sxs-lookup"><span data-stu-id="d7f27-131">In **URL**, type **http://www.spamlink.contoso.com/**, click **OK**, and then click **Send**.</span></span>
    
15. <span data-ttu-id="d7f27-132">Öffnen Sie im privaten Modus eine separate Instanz von Internet Explorer, wechseln Sie zum Microsoft 365 Admin Center ([https://admin.microsoft.com](https://admin.microsoft.com)), und melden Sie sich mit ihrem globalen Administratorkonto bei ihrem Office 365-Testabonnement an.</span><span class="sxs-lookup"><span data-stu-id="d7f27-132">Open a separate instance of Internet Explorer in private browsing mode, go to the Microsoft 365 admin center ([https://admin.microsoft.com](https://admin.microsoft.com)), and sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
16. <span data-ttu-id="d7f27-133">Klicken Sie auf der Hauptportalseite auf die Kachel „apps" und dann auf **E-Mail**.</span><span class="sxs-lookup"><span data-stu-id="d7f27-133">From the main portal page, click the apps tile, and then click **Mail**.</span></span>
    
17. <span data-ttu-id="d7f27-134">Klicken Sie im Posteingang auf die Nachricht mit dem Betreff **Ihre neuen Schlüssel**.</span><span class="sxs-lookup"><span data-stu-id="d7f27-134">In the Inbox, click the message with the subject **Your new keys**.</span></span>
    
18. <span data-ttu-id="d7f27-p103">Klicken Sie im Ordner „Junk-E-Mail" auf die Nachricht mit dem Betreff **Neue Reisewebsite**. Klicken Sie in der Nachricht auf den Link **diese Website**. Sie sollten in etwa folgende Seite sehen: „Fehler! spamlink.contoso.com konnte nicht gefunden werden". Dies ist das richtige Ergebnis, da es keine Webseite an dieser Position gibt.</span><span class="sxs-lookup"><span data-stu-id="d7f27-p103">In the Junk Mail folder, click the message with the subject **New travel web site**. Within the message, click the **this site** link. You should see a "Oops! Internet Explorer could not find spamlink.contoso.com." page. This is the correct result because there is no web page at that location.</span></span>
    
<span data-ttu-id="d7f27-p104">Beachten Sie, dass beide dieser potenziell schädlichen E-Mails erfolgreich übermittelt wurden. Die E-Mail **Ihre neuen Schlüssel** könnte nicht erkannte Schadsoftware enthalten, und es wird nicht verhindert, dass der Benutzer auf den potenziell bösartigen Link in der E-Mail **Neue Reisewebsite** klickt.</span><span class="sxs-lookup"><span data-stu-id="d7f27-p104">Notice that both of these potentially malicious emails were delivered successfully. The **Your new keys** email could contain undetected malware and the user was allowed to click the potentially malicious link in the **New travel web site** email.</span></span>
  
## <a name="phase-3-configure-safe-attachment-and-safe-links-policies-for-atp"></a><span data-ttu-id="d7f27-143">Phase 3: Konfigurieren von Richtlinien für sichere Anlagen und sichere Links für ATP</span><span class="sxs-lookup"><span data-stu-id="d7f27-143">Phase 3: Configure safe attachment and safe links policies for ATP</span></span>

<span data-ttu-id="d7f27-144">In dieser Phase erstellen und konfigurieren Sie eine Richtlinie für sichere Anlagen, um die Übermittlung von E-Mails mit potenziell schädlichen Anlagen zu verhindern, und eine Richtlinie für sichere Links, um zu verhindern, dass Benutzer potenziell unsichere URLs besuchen.</span><span class="sxs-lookup"><span data-stu-id="d7f27-144">In this phase, you create and configure a safe attachment policy to prevent email with potentially malicious attachments from being delivered and a safe links policy to keep users from traveling to potentially unsafe URLs.</span></span>
  
1. <span data-ttu-id="d7f27-145">Klicken Sie auf der Registerkarte **Microsoft Office Home** in Internet Explorer auf die Kachel **Admin**.</span><span class="sxs-lookup"><span data-stu-id="d7f27-145">On the **Microsoft Office Home** tab of Internet Explorer, click the **Admin** tile.</span></span>
    
2. <span data-ttu-id="d7f27-146">Klicken Sie im linken Navigationsbereich auf **Admin Center** und dann auf **Exchange**.</span><span class="sxs-lookup"><span data-stu-id="d7f27-146">In the left navigation, click **Admin centers**, and then **Exchange**.</span></span>
    
3. <span data-ttu-id="d7f27-147">Klicken Sie im linken Navigationsbereich der Admin Center-Registerkarte für Exchange auf **Komplexe Bedrohungen**.</span><span class="sxs-lookup"><span data-stu-id="d7f27-147">In the left navigation of the Exchange admin center tab, click **advanced threats**.</span></span>
    
4. <span data-ttu-id="d7f27-148">Klicken Sie auf die Registerkarte **Sichere Anlagen** und dann auf das Pluszeichen (+).</span><span class="sxs-lookup"><span data-stu-id="d7f27-148">Click the **safe attachments** tab, and then click the plus sign.</span></span>
    
5. <span data-ttu-id="d7f27-149">Geben Sie im Fenster **Neue Richtlinie für sichere Anlagen** in **Name** den Wert **Richtlinie für sichere Anlagen - Blockieren** ein.</span><span class="sxs-lookup"><span data-stu-id="d7f27-149">In the **new safe attachments policy** window, in **Name**, type **Safe Attachment Policy - Block**.</span></span>
    
6. <span data-ttu-id="d7f27-150">Klicken Sie für **Reaktion für sichere Anlagen bei unbekannter Schadsoftware** auf **Blockieren**.</span><span class="sxs-lookup"><span data-stu-id="d7f27-150">For **Safe attachments unknown malware response**, click **Block**.</span></span>
    
7. <span data-ttu-id="d7f27-151">Klicken Sie für **Anlage bei Erkennung umleiten** auf **Umleitung aktivieren**, und geben Sie die E-Mail-Adresse des Kontos Ihres globalen Office 365-Administrators ein.</span><span class="sxs-lookup"><span data-stu-id="d7f27-151">For **Redirect attachment on detection**, click **Enable redirect** and type the email address of your Office 365 global administrator account.</span></span>
    
8. <span data-ttu-id="d7f27-p105">Klicken Sie für **Angewendet auf** auf den Pfeil nach unten, und klicken Sie dann auf **Die Empfängerdomäne ist**. Klicken Sie im Fenster auf den Namen Ihrer Organisation (z. B. contoso.onmicrosoft.com), und klicken Sie dann auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="d7f27-p105">For **Applied to**, click the down arrow, and then click **The recipient domain is**. In the window, click your organization name (such as contoso.onmicrosoft.com), and then click **OK**.</span></span>
    
9. <span data-ttu-id="d7f27-p106">Klicken Sie auf **Speichern**. Nach dem Update sollte die neue und aktivierte **Richtlinie für sichere Anlagen - Blockieren** angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="d7f27-p106">Click **Save**. After the update, you should see the new and enabled **Safe Attachment Policy - Block**.</span></span>
    
10. <span data-ttu-id="d7f27-156">Klicken Sie auf die Registerkarte **Sichere Links** und dann auf das Pluszeichen (+).</span><span class="sxs-lookup"><span data-stu-id="d7f27-156">Click the **safe links** tab, and then click the plus sign.</span></span>
    
11. <span data-ttu-id="d7f27-157">Geben Sie im Fenster **Neue Richtlinie für sichere Links** in **Name** **Richtlinie für sichere Links** ein.</span><span class="sxs-lookup"><span data-stu-id="d7f27-157">In the **new safe links policy** window, in **Name**, type **Safe Link Policy**.</span></span>
    
12. <span data-ttu-id="d7f27-158">Klicken Sie für **Wählen Sie die Aktion für unbekannte, potenziell bösartige URLs in Nachrichten aus** auf **Ein**, und wählen Sie dann **Benutzern das Durchklicken zur ursprünglichen URL nicht gestatten** aus.</span><span class="sxs-lookup"><span data-stu-id="d7f27-158">For **Select the action for unknown potentially malicious URLs in messages**, click **On**, and then select **Do not allow users to click through to original URL**.</span></span>
    
13. <span data-ttu-id="d7f27-p107">Klicken Sie für **Angewendet auf** auf den Pfeil nach unten, und klicken Sie dann auf **Die Empfängerdomäne ist**. Klicken Sie im Fenster auf den Namen Ihrer Organisation (z. B. contoso.onmicrosoft.com), und klicken Sie dann auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="d7f27-p107">For **Applied to**, click the down arrow, and then click **The recipient domain is**. In the window, click your organization name (such as contoso.onmicrosoft.com), and then click **OK**.</span></span>
    
14. <span data-ttu-id="d7f27-p108">Klicken Sie auf **Speichern**. Nun sollte die neue und aktivierte **Richtlinie für sichere Links** angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="d7f27-p108">Click **Save**. You should see the new and enabled **Safe Link Policy**.</span></span>
    
## <a name="phase-4-show-atp-in-action"></a><span data-ttu-id="d7f27-163">Phase 4: Vorführen von ATP in Aktion</span><span class="sxs-lookup"><span data-stu-id="d7f27-163">Phase 4: Show ATP in action</span></span>

<span data-ttu-id="d7f27-164">In dieser Phase führen Sie vor, wie ATP potenziell schädliche E-Mails behandelt.</span><span class="sxs-lookup"><span data-stu-id="d7f27-164">In this phase, you demonstrate how ATP deals with potentially malicious email.</span></span>
  
1. <span data-ttu-id="d7f27-165">Klicken Sie in der Instanz von Internet Explorer, die Sie in Phase 2 zum Senden von E-Mail verwendet haben, im linken Navigationsbereich auf **Gesendete Elemente**.</span><span class="sxs-lookup"><span data-stu-id="d7f27-165">From the instance of Internet Explorer that you used to send the email in Phase 2, in the left navigation, click **Sent Items.**</span></span>
    
2. <span data-ttu-id="d7f27-166">Klicken Sie auf die E-Mail mit dem Titel **Ihre neuen Schlüssel**, klicken Sie auf den Dropdownpfeil, und klicken Sie dann auf **Weiterleiten**.</span><span class="sxs-lookup"><span data-stu-id="d7f27-166">Click the email titled **Your new keys**, click the down arrow icon, and then click **Forward**.</span></span>
    
3. <span data-ttu-id="d7f27-167">Geben Sie für die neue Nachricht in **An** die E-Mail-Adresse für den Namen des globalen Office 365-Administrators Ihres Testabonnements ein. Klicken Sie anschließend auf **Senden**</span><span class="sxs-lookup"><span data-stu-id="d7f27-167">For the new message, in **To**, type the email address of the Office 365 global administrator name of your trial subscription, and then click **Send**.</span></span>
    
4. <span data-ttu-id="d7f27-168">Klicken Sie auf die E-Mail mit dem Titel **Neue Reisewebsite**, klicken Sie auf auf den Dropdownpfeil, klicken Sie auf **Allen antworten**, und klicken Sie dann auf **Senden**.</span><span class="sxs-lookup"><span data-stu-id="d7f27-168">Click the email titled **New travel web site**, click the down arrow icon, click **Reply all**, and then click **Send**.</span></span>
    
5. <span data-ttu-id="d7f27-p109">Klicken Sie in der Instanz von Internet Explorer, die Sie in Phase 3 zum Konfigurieren von ATP-Richtlinien verwendet haben, auf die Admin Center-Registerkarte für Exchange, dann auf die Kachel „apps" und dann auf **E-Mail**. Im Posteingang sollten zwei neue E-Mail-Nachrichten angezeigt werden:</span><span class="sxs-lookup"><span data-stu-id="d7f27-p109">From the instance of Internet Explorer that you used to configure ATP policies in Phase 3, click the Exchange admin center tab, click the apps tile, and then click **Mail**. You should see two new email messages in the Inbox:</span></span>
    
  - <span data-ttu-id="d7f27-171">Eine mit dem Titel **WG: Ihre neuen Schlüssel**</span><span class="sxs-lookup"><span data-stu-id="d7f27-171">One titled **Fw: Your new keys**</span></span>
    
  - <span data-ttu-id="d7f27-172">Eine mit dem Titel **WG: Neue Reisewebsite**</span><span class="sxs-lookup"><span data-stu-id="d7f27-172">One titled **Fw: New travel web site**</span></span>
    
6. <span data-ttu-id="d7f27-p110">Öffnen Sie die E-Mail-Nachricht mit dem Titel **WG: Neue Reisewebsite**, und klicken Sie auf den Link **diese Website**. Es sollte eine Seite „Diese Website wurde als böswillig klassifiziert" angezeigt werden. Dies zeigt, dass ATP den Zugriff auf die potenziell bösartige Website verhindert.</span><span class="sxs-lookup"><span data-stu-id="d7f27-p110">Open the email message titled **Fw: New travel web site** and click the **this site** link. You should see a "This website has been classified as malicious." page. This demonstrates that ATP is preventing you from accessing the potentially malicious web site.</span></span>
    
7. <span data-ttu-id="d7f27-177">Klicken Sie auf der Admin Center-Registerkarte für Exchange von Internet Explorer im linken Navigationsbereich auf **E-Mail-Fluss**.</span><span class="sxs-lookup"><span data-stu-id="d7f27-177">In the Exchange admin center tab of Internet Explorer, in the left navigation, click **mail flow**.</span></span>
    
8. <span data-ttu-id="d7f27-178">Klicken Sie auf die Registerkarte **Nachrichtenablaufverfolgung**, und klicken Sie dann auf **Suche**.</span><span class="sxs-lookup"><span data-stu-id="d7f27-178">Click the **message trace** tab, and then click **search**.</span></span>
    
9. <span data-ttu-id="d7f27-p111">Doppelklicken Sie im Fenster **Ergebnisse der Nachrichtenablaufverfolgung** auf die Nachricht mit dem Betreff **Ihre neuen Schlüssel**. Diese Nachricht wurde erfolgreich in den Posteingang zugestellt. Schließen Sie dieses Fenster.</span><span class="sxs-lookup"><span data-stu-id="d7f27-p111">In the **Message Trace Results** window, double-click the message with the subject **Your new keys**. This message was successfully delivered to the Inbox. Close this window.</span></span>
    
10. <span data-ttu-id="d7f27-p112">Doppelklicken Sie auf die Nachricht mit dem Betreff **Neue Reisewebsite**. Diese Nachricht wurde erfolgreich in den Posteingang zugestellt. Schließen Sie dieses Fenster.</span><span class="sxs-lookup"><span data-stu-id="d7f27-p112">Double-click the message with the subject **New travel web site**. This message was successfully delivered to the Inbox. Close this window.</span></span>
    
11. <span data-ttu-id="d7f27-p113">Doppelklicken Sie auf die Nachricht mit dem Betreff **WG: Ihre neuen Schlüssel**. Beachten Sie, wie diese Nachricht von ATP verarbeitet und dann in den Posteingang übermittelt wurde. Schließen Sie dieses Fenster.</span><span class="sxs-lookup"><span data-stu-id="d7f27-p113">Double-click the message with the subject **Fw: Your new keys**. Note how this message was processed by ATP and then delivered to the Inbox. Close this window.</span></span>
    
    > [!NOTE]
    > <span data-ttu-id="d7f27-p114">Der Zweck der Richtlinie für sichere Anlagen war es, Anlagen auf bösartigen Code zu scannen. Die Anlage "getKeys.js" wurde zugelassen, da nicht festgestellt wurde, dass sie bösartig ist. Dieser Schritt zeigt, dass ATP eine Überprüfung der Anlage durchgeführt hat.</span><span class="sxs-lookup"><span data-stu-id="d7f27-p114">The purpose of the safe attachments policy was to begin scanning attachments for malicious code. The getKeys.js attachment was allowed because it was not determined to be malicious. This step shows that ATP did perform a scan of the attachment.</span></span> 
  
12. <span data-ttu-id="d7f27-p115">Doppelklicken Sie auf die Nachricht mit dem Betreff **WG: Neue Reisewebsite**. Beachten Sie, dass diese Nachricht erfolgreich in den Posteingang übermittelt wurde.</span><span class="sxs-lookup"><span data-stu-id="d7f27-p115">Double-click the message with the subject **Fw: New travel web site**. Note that this message was successfully delivered to the Inbox.</span></span>
    
<span data-ttu-id="d7f27-193">Sie können diese Umgebung jetzt verwenden, um neue Richtlinien zu erstellen und mit ATP zu experimentieren.</span><span class="sxs-lookup"><span data-stu-id="d7f27-193">You can now use this environment to create new policies and experiment with ATP.</span></span>
  
> [!TIP]
> <span data-ttu-id="d7f27-194">Klicken Sie [hier](http://aka.ms/catlgstack), um eine visuelle Darstellung aller Artikel im Stapel der Testumgebungsanleitungen in der Microsoft Cloud zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="d7f27-194">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="d7f27-195">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="d7f27-195">See Also</span></span>

[<span data-ttu-id="d7f27-196">Testumgebungsanleitungen (TLGs) zur Cloudakzeptanz</span><span class="sxs-lookup"><span data-stu-id="d7f27-196">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="d7f27-197">Basiskonfiguration der Entwicklungs-/Testumgebung</span><span class="sxs-lookup"><span data-stu-id="d7f27-197">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="d7f27-198">Office 365-Entwicklungs-/Testumgebung</span><span class="sxs-lookup"><span data-stu-id="d7f27-198">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="d7f27-199">DirSync für die Office 365-Entwicklungs-/Testumgebung</span><span class="sxs-lookup"><span data-stu-id="d7f27-199">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="d7f27-200">Cloud App Security für Ihre Office 365-Entwicklungs-/Testumgebung</span><span class="sxs-lookup"><span data-stu-id="d7f27-200">Cloud App Security for your Office 365 dev/test environment</span></span>](cloud-app-security-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="d7f27-201">Cloudakzeptanz und Hybridlösungen</span><span class="sxs-lookup"><span data-stu-id="d7f27-201">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md) 

[<span data-ttu-id="d7f27-202">Advanced Threat Protection für Safe Attachments und Safe Links</span><span class="sxs-lookup"><span data-stu-id="d7f27-202">Advanced threat protection for safe attachments and safe links</span></span>](https://support.office.com/article/Office-365-Advanced-Threat-Protection-E100FE7C-F2A1-4B7D-9E08-622330B83653)


