---
title: "Advanced eDiscovery für die Office 365-Entwicklungs-/Testumgebung"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: TLG, Ent_TLGs
ms.assetid: d4c49a6f-abfd-4d68-b353-259b4eefb033
description: 'Zusammenfassung: Konfigurieren Sie und veranschaulichen Sie der Office 365 erweiterte eDiscovery mit Beispieldaten in Ihrer Office 365 Dev/Test-Umgebung.'
ms.openlocfilehash: 6c0c28ced9d267ea2ecc353af8f1453c4dce7f8e
ms.sourcegitcommit: c16db80a2be81db876566c578bb04f3747dbd50c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/13/2018
---
# <a name="advanced-ediscovery-for-your-office-365-devtest-environment"></a><span data-ttu-id="1a715-103">Advanced eDiscovery für die Office 365-Entwicklungs-/Testumgebung</span><span class="sxs-lookup"><span data-stu-id="1a715-103">Advanced eDiscovery for your Office 365 dev/test environment</span></span>

 <span data-ttu-id="1a715-104">**Zusammenfassung:** Konfigurieren Sie und veranschaulichen Sie der Office 365 erweiterte eDiscovery mit Beispieldaten in Ihrer Office 365 Dev/Test-Umgebung.</span><span class="sxs-lookup"><span data-stu-id="1a715-104">**Summary:** Configure and demonstrate Office 365 Advanced eDiscovery with sample data in your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="1a715-p101">Office 365 erweiterte eDiscovery können Sie schnell zu finden und Analysieren der relevanten Informationen über die Daten, die in Office 365, einschließlich e-Mails und Dokumente gespeichert ist. Dies kann große Datenmengen Zeit und Kosten, insbesondere in Situationen Rechtsstreitigkeiten sparen. Weitere Informationen finden Sie unter [Office 365 erweiterte eDiscovery](https://support.office.com/article/Office-365-Advanced-eDiscovery-fd53438a-a760-45f6-9df4-861b50161ae4).</span><span class="sxs-lookup"><span data-stu-id="1a715-p101">Office 365 Advanced eDiscovery allows you to quickly find and analyze relevant information across the data that is stored in Office 365, including email and documents. This can save enormous amounts of time and expense, especially in litigation situations. For more information, see [Office 365 Advanced eDiscovery](https://support.office.com/article/Office-365-Advanced-eDiscovery-fd53438a-a760-45f6-9df4-861b50161ae4).</span></span>
  
<span data-ttu-id="1a715-108">Mit den Anweisungen in diesem Artikel erstellen Sie eine kleine Gruppe von Daten für eine fiktive Vertragsstreitigkeit und analysieren diese mit der Erweiterten eDiscovery.</span><span class="sxs-lookup"><span data-stu-id="1a715-108">With the instructions in this article, you create a small set of data for a fictional contract dispute and analyze it with Advanced eDiscovery.</span></span>
  
> [!TIP]
> <span data-ttu-id="1a715-109">Klicken Sie [hier](http://aka.ms/catlgstack), um eine visuelle Darstellung aller Artikel im Stapel der Testumgebungsanleitungen in der Microsoft Cloud zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="1a715-109">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-create-your-office-365-devtest-environment"></a><span data-ttu-id="1a715-110">Phase 1: Erstellen Ihrer Office 365-Entwicklungs-/Testumgebung</span><span class="sxs-lookup"><span data-stu-id="1a715-110">Phase 1: Create your Office 365 dev/test environment</span></span>

<span data-ttu-id="1a715-111">Wenn Sie erweiterte eDiscovery auf einfache Weise mit den Mindestanforderungen testen möchten, befolgen Sie die Anweisungen in Phase 2 und Phase 3 des [Office 365 Dev/Test Environment](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="1a715-111">If you just want to test Advanced eDiscovery in a lightweight way with the minimum requirements, follow the instructions in Phase 2 and Phase 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="1a715-112">Wenn Sie erweiterte eDiscovery in einer simulierten Enterprise testen möchten, befolgen Sie die Anweisungen in [DirSync für Ihre Office 365 Dev/Test-Umgebung](dirsync-for-your-office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="1a715-112">If you want to test Advanced eDiscovery in a simulated enterprise, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="1a715-p102">Testen erweiterter eDiscovery erfordert keinen die simulierten Enterprise-Umgebung, einschließlich einer simulierten Intranet mit dem Internet verbunden und Directory-Synchronisierung für eine Windows Server Active Directory-Gesamtstruktur. Erfolgt hier als eine Option, damit Sie testen und experimentieren in einer Umgebung ausführen können, die eine typische Organisation darstellt.</span><span class="sxs-lookup"><span data-stu-id="1a715-p102">Testing Advanced eDiscovery does not require the simulated enterprise environment, which includes a simulated intranet connected to the Internet and directory synchronization for a Windows Server AD forest. It is provided here as an option so that you can perform testing and experimentation in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-create-example-data-for-advanced-ediscovery"></a><span data-ttu-id="1a715-115">Phase 2: Erstellen von Beispieldaten für die Erweiterte eDiscovery</span><span class="sxs-lookup"><span data-stu-id="1a715-115">Phase 2: Create example data for Advanced eDiscovery</span></span>

<span data-ttu-id="1a715-116">In diesem Verfahren erstellen Sie E-Mail-Nachrichten, die Sie später in einem erweiterten eDiscovery-Fall analysieren werden.</span><span class="sxs-lookup"><span data-stu-id="1a715-116">In this procedure, you create email messages that will you later analyze in an Advanced eDiscovery case.</span></span>
  
1. <span data-ttu-id="1a715-117">Öffnen Sie Internet Explorer, und melden Sie sich unter [https://outlook.com](https://outlook.com) auf das Outlook-Konto in Phase 2 des[Office 365 Dev/Test-Umgebung](office-365-dev-test-environment.md)erstellten.</span><span class="sxs-lookup"><span data-stu-id="1a715-117">Open Internet Explorer and sign in at [https://outlook.com](https://outlook.com) to the Outlook account you created in Phase 2 of[Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
    
  - <span data-ttu-id="1a715-118">Wenn Sie die einfache Entwicklungs-/Testumgebung verwenden, öffnen Sie eine private Sitzung von Internet Explorer, und melden Sie sich von Ihrem lokalen Computer aus an.</span><span class="sxs-lookup"><span data-stu-id="1a715-118">If you are using the lightweight dev/test environment, open a private session of Internet Explorer and sign in from your local computer.</span></span>
    
  - <span data-ttu-id="1a715-119">Wenn Sie den simulierten Test-/unternehmensumgebung verwenden, verwenden Sie das Azure-Portal ([https://portal.azure.com](https://portal.azure.com)) so virtuellen Computer CLIENT1 her, und melden Sie sich von CLIENT1.</span><span class="sxs-lookup"><span data-stu-id="1a715-119">If you are using the simulated enterprise dev/test environment, use the Azure portal ([https://portal.azure.com](https://portal.azure.com)) to connect to the CLIENT1 virtual machine, and then sign in from CLIENT1.</span></span>
    
2. <span data-ttu-id="1a715-120">Klicken Sie auf der Registerkarte **Outlook E-Mail** auf **neu**.</span><span class="sxs-lookup"><span data-stu-id="1a715-120">On the **Outlook Mail** tab, click **New**.</span></span>
    
3. <span data-ttu-id="1a715-p103">Geben Sie im Feld **an**die e-Mail-Adresse des Kontos User6 des Test-Abonnement ( **user6 @.** <organization name> **. onmicrosoft.com**).</span><span class="sxs-lookup"><span data-stu-id="1a715-p103">In **To**, type the email address of the User6 account of your trial subscription ( **user6@.**<organization name> **.onmicrosoft.com**).</span></span>
    
4. <span data-ttu-id="1a715-123">Geben Sie für den Betreff **e-Mail testen 1**.</span><span class="sxs-lookup"><span data-stu-id="1a715-123">For the subject, type **Test email 1**.</span></span>
    
5. <span data-ttu-id="1a715-124">Klicken Sie im Textkörper Geben Sie **Tailspin Vertragsentwurf**, und klicken Sie dann auf **Senden**.</span><span class="sxs-lookup"><span data-stu-id="1a715-124">In the body, type **Tailspin contract draft**, and then click **Send**.</span></span>
    
6. <span data-ttu-id="1a715-125">Klicken Sie auf der Registerkarte **Outlook E-Mail** auf **neu**.</span><span class="sxs-lookup"><span data-stu-id="1a715-125">On the **Outlook Mail** tab, click **New**.</span></span>
    
7. <span data-ttu-id="1a715-126">Geben Sie im Feld **an**die e-Mail-Adresse des Kontos User6 des Test-Abonnement.</span><span class="sxs-lookup"><span data-stu-id="1a715-126">In **To**, type the email address of the User6 account of your trial subscription.</span></span>
    
8. <span data-ttu-id="1a715-127">Geben Sie für den Betreff **e-Mail testen 2**ein.</span><span class="sxs-lookup"><span data-stu-id="1a715-127">For the subject, type **Test email 2**.</span></span>
    
9. <span data-ttu-id="1a715-128">Klicken Sie im Textkörper Geben Sie **Tailspin Lunch Besprechung**, und klicken Sie dann auf **Senden**.</span><span class="sxs-lookup"><span data-stu-id="1a715-128">In the body, type **Tailspin lunch meeting**, and then click **Send**.</span></span>
    
10. <span data-ttu-id="1a715-129">Klicken Sie auf der Registerkarte **Outlook E-Mail** auf **neu**.</span><span class="sxs-lookup"><span data-stu-id="1a715-129">On the **Outlook Mail** tab, click **New**.</span></span>
    
11. <span data-ttu-id="1a715-130">Geben Sie im Feld **an**die e-Mail-Adresse des Kontos User6 des Test-Abonnement.</span><span class="sxs-lookup"><span data-stu-id="1a715-130">In **To**, type the email address of the User6 account of your trial subscription.</span></span>
    
12. <span data-ttu-id="1a715-131">Geben Sie für den Betreff **Test e-Mail 3**.</span><span class="sxs-lookup"><span data-stu-id="1a715-131">For the subject, type **Test email 3**.</span></span>
    
13. <span data-ttu-id="1a715-132">Klicken Sie im Textkörper Geben Sie **Tailspin Vertrag nicht einverstanden**, und klicken Sie dann auf **Senden**.</span><span class="sxs-lookup"><span data-stu-id="1a715-132">In the body, type **Tailspin contract disagreement**, and then click **Send**.</span></span>
    
14. <span data-ttu-id="1a715-133">Klicken Sie auf das Symbol für Benutzer in der oberen rechten Ecke, und klicken Sie dann auf **Abmelden**.</span><span class="sxs-lookup"><span data-stu-id="1a715-133">Click the user icon in the upper right corner, and then click **Sign out**.</span></span>
    
15. <span data-ttu-id="1a715-134">Öffnen Sie eine neue Registerkarte, und melden Sie sich bei Office 365-Portal ([https://portal.office.com](https://portal.office.com)) mit den Kontonamen und das Kennwort des Kontos User6 des Test-Abonnement.</span><span class="sxs-lookup"><span data-stu-id="1a715-134">Open a new tab and sign in to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) with the account name and password of the User6 account of your trial subscription.</span></span>
    
16. <span data-ttu-id="1a715-135">Klicken Sie auf der Registerkarte **Office 365-Portal** auf **Mail**.</span><span class="sxs-lookup"><span data-stu-id="1a715-135">On the **Office 365 portal** tab, click **Mail**.</span></span>
    
17. <span data-ttu-id="1a715-136">Klicken Sie auf der Registerkarte **E-Mail - User6 - Outlook** stellen Sie sicher, dass User6 alle drei e-Mails von Outlook-e-Mail-Kontos empfangen.</span><span class="sxs-lookup"><span data-stu-id="1a715-136">On the **Mail - User6 - Outlook** tab, verify that User6 received all three emails from the Outlook email account.</span></span>
    
18. <span data-ttu-id="1a715-137">Wechseln Sie zu der **Office 365-Portal-Registerkarte** für User6.</span><span class="sxs-lookup"><span data-stu-id="1a715-137">Switch back to the **Office 365 portal tab** for User6.</span></span>
    
19. <span data-ttu-id="1a715-138">Klicken Sie auf das Symbol für Benutzer in der oberen rechten Ecke, und klicken Sie dann auf **Abmelden.**</span><span class="sxs-lookup"><span data-stu-id="1a715-138">Click the user icon in the upper right corner, and then click **Sign out.**</span></span>
    
<span data-ttu-id="1a715-139">In diesem Verfahren erstellen Sie zwei Word-Dokumente, die Sie später in einem erweiterten eDiscovery-Fall analysieren werden.</span><span class="sxs-lookup"><span data-stu-id="1a715-139">In this procedure, you create two Word documents that will you will later analyze in an Advanced eDiscovery case.</span></span>
  
1. <span data-ttu-id="1a715-140">Klicken Sie auf der Seite **Office** auf **anmelden,** melden Sie sich mit den Anmeldeinformationen Ihres Kontos globaler Administrator.</span><span class="sxs-lookup"><span data-stu-id="1a715-140">On the **Office** page, click **Sign in,** sign in with the credentials of your global administrator account.</span></span>
    
2. <span data-ttu-id="1a715-141">Klicken Sie auf eine neue Registerkarte Zugriff auf die URL der Produktion SharePoint-Website: **https://** <fictional organization name> **.sharepoint.com/sites/production**</span><span class="sxs-lookup"><span data-stu-id="1a715-141">On a new tab, access the URL of your Production SharePoint site: **https://**<fictional organization name> **.sharepoint.com/sites/production**</span></span>
    
3. <span data-ttu-id="1a715-142">Klicken Sie auf der Registerkarte **produktionswebsitesammlung** unter **Dokumente**auf **Neu > Word-Dokument**.</span><span class="sxs-lookup"><span data-stu-id="1a715-142">On the **Production site collection** tab, under **Documents**, click **New > Word Document**.</span></span>
    
4. <span data-ttu-id="1a715-143">Geben Sie auf der Seite **Word Online** **Tailspin Vertragsentwurf**, warten Sie, bis es **Saved** im Titel anzeigt, und schließen Sie dann das **Word Online** Seitenregister.</span><span class="sxs-lookup"><span data-stu-id="1a715-143">On the **Word Online** page, type **Tailspin draft contract**, wait until it displays **Saved** in the title, and then close the **Word Online** page tab.</span></span>
    
5. <span data-ttu-id="1a715-144">Klicken Sie auf der Registerkarte **produktionswebsitesammlung** unter **Dokumente**auf **Neu > Word-Dokument**.</span><span class="sxs-lookup"><span data-stu-id="1a715-144">On the **Production site collection** tab, under **Documents**, click **New > Word Document**.</span></span>
    
6. <span data-ttu-id="1a715-145">Klicken Sie auf der Registerkarte **Word Online** Geben Sie **Tailspin Vertrag Fall Notizen**, warten Sie, bis es **Saved** im Titel anzeigt, und schließen Sie dann die Registerkarte **Word Online** .</span><span class="sxs-lookup"><span data-stu-id="1a715-145">On the **Word Online** tab, type **Tailspin contract dispute notes**, wait until it displays **Saved** in the title, and then close the **Word Online** tab.</span></span>
    
7. <span data-ttu-id="1a715-146">Klicken Sie auf der Registerkarte **produktionswebsitesammlung** sollte **Dokument-** und **Document1** in der Liste der Dokumente angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="1a715-146">On the **Production site collection** tab, you should see **Document** and **Document1** in the list of documents.</span></span>
    
8. <span data-ttu-id="1a715-147">Schließen Sie die Registerkarte **produktionswebsitesammlung** .</span><span class="sxs-lookup"><span data-stu-id="1a715-147">Close the **Production site collection** tab.</span></span>
    
## <a name="phase-3-use-advanced-ediscovery-for-a-legal-dispute"></a><span data-ttu-id="1a715-148">Phase 3: Verwenden Sie erweiterte eDiscovery gemeldet werden, rechtliche</span><span class="sxs-lookup"><span data-stu-id="1a715-148">Phase 3: Use Advanced eDiscovery for a legal dispute</span></span>

<span data-ttu-id="1a715-p104">Leider hat Beilegung eines Vertrag zwischen Ihrer Organisation und Tailspin Toys Zeitpunkt des rechtlichen erreicht. In diesem Verfahren erstellen und konfigurieren eine erweiterte eDiscovery-Fall zum Suchen und Analysieren von e-Mails und Dokumente, die den Text "Tailspin Vertrag" enthalten.</span><span class="sxs-lookup"><span data-stu-id="1a715-p104">Unfortunately, a contract dispute between your organization and Tailspin Toys has reached the point of legal action. In this procedure, you create and configure an Advanced eDiscovery case to search for and analyze email and documents that contain the text "Tailspin contract".</span></span>
  
<span data-ttu-id="1a715-151">Der Prozess für die Verwendung der erweiterten eDiscovery ist wie folgt:</span><span class="sxs-lookup"><span data-stu-id="1a715-151">The process for using Advanced eDiscovery is the following:</span></span>
  
- <span data-ttu-id="1a715-152">Erstellen Sie eine Suche in das Wertpapier &amp; Compliance Center, analysieren Sie die Ergebnisse, und klicken Sie dann die Ergebnisse für erweiterte eDiscovery vorbereiten.</span><span class="sxs-lookup"><span data-stu-id="1a715-152">Create a search in the Security &amp; Compliance center, analyze its results, and then prepare the results for Advanced eDiscovery.</span></span>
    
- <span data-ttu-id="1a715-153">Erstellen Sie und konfigurieren Sie einen Fall in der erweiterten eDiscovery, und analysieren Sie die Suchergebnisse.</span><span class="sxs-lookup"><span data-stu-id="1a715-153">Create and configure a case in Advanced eDiscovery and analyze the search results.</span></span>
    
<span data-ttu-id="1a715-154">In diesem Verfahren erstellen Sie eine Suche in das Wertpapier &amp; Compliance center für "Tailspin Vertrag", sehen die Ergebnisse, und bereiten Sie die Ergebnisse für erweiterte eDiscovery.</span><span class="sxs-lookup"><span data-stu-id="1a715-154">In this procedure, you create a search in the Security &amp; Compliance center for "Tailspin contract", look at the results, and then prepare the results for Advanced eDiscovery.</span></span>
  
1. <span data-ttu-id="1a715-155">Klicken Sie auf der Registerkarte **Office 365-Portal** auf **Admin**.</span><span class="sxs-lookup"><span data-stu-id="1a715-155">From the **Office 365 portal** tab, click **Admin**.</span></span>
    
2. <span data-ttu-id="1a715-156">Klicken Sie im linken Navigationsbereich der Registerkarte Admin Center auf **Zentriert Admin > Compliance**.</span><span class="sxs-lookup"><span data-stu-id="1a715-156">In the left navigation of the Admin center tab, click **Admin centers > Compliance**.</span></span>
    
3. <span data-ttu-id="1a715-157">Klicken Sie auf die **Sicherheit &amp; Compliance** Registerkarte, klicken Sie auf **Berechtigungen**.</span><span class="sxs-lookup"><span data-stu-id="1a715-157">On the **Security &amp; Compliance** tab, click **Permissions**.</span></span>
    
4. <span data-ttu-id="1a715-158">Doppelklicken Sie in der Liste **Berechtigungen** auf **Organization Management**.</span><span class="sxs-lookup"><span data-stu-id="1a715-158">In the **Permissions** list, double-click **Organization Management**.</span></span>
    
5. <span data-ttu-id="1a715-159">Klicken Sie im Fenster **Rollengruppe** unter **Mitglieder**auf das Pluszeichen (+).</span><span class="sxs-lookup"><span data-stu-id="1a715-159">In the **Role Group** window, under **Members**, click the plus sign.</span></span>
    
6. <span data-ttu-id="1a715-160">Klicken Sie im Fenster **Elemente auswählen** Doppelklicken auf den Namen des Administratorkontos, und klicken Sie dann auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="1a715-160">In the **Select Members** window, double-click the name of your administrator account, and then click **OK**.</span></span>
    
7. <span data-ttu-id="1a715-161">Klicken Sie im Fenster **Rollengruppe** auf **Speichern**.</span><span class="sxs-lookup"><span data-stu-id="1a715-161">In the **Role Group** window, click **Save**.</span></span>
    
8. <span data-ttu-id="1a715-162">Doppelklicken Sie in der Liste **Berechtigungen** auf **eDiscovery-Manager**.</span><span class="sxs-lookup"><span data-stu-id="1a715-162">In the **Permissions** list, double-click **eDiscovery Manager**.</span></span>
    
9. <span data-ttu-id="1a715-163">Klicken Sie im Fenster **Rollengruppe** unter **eDiscovery-Administrator**, auf das plus-Symbol.</span><span class="sxs-lookup"><span data-stu-id="1a715-163">In the **Role Group** window, under **eDiscovery Administrator**, click the plus icon.</span></span>
    
10. <span data-ttu-id="1a715-164">Klicken Sie im Fenster **Elemente auswählen** Doppelklicken auf den Namen des Administratorkontos, und klicken Sie dann auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="1a715-164">In the **Select Members** window, double-click the name of your administrator account, and then click **OK**.</span></span>
    
11. <span data-ttu-id="1a715-165">Klicken Sie im Fenster **Rollengruppe** auf **Speichern**.</span><span class="sxs-lookup"><span data-stu-id="1a715-165">In the **Role Group** window, click **Save**.</span></span>
    
12. <span data-ttu-id="1a715-166">Klicken Sie im linken Navigationsbereich auf **Suche &amp; Untersuchung > Inhaltssuche**.</span><span class="sxs-lookup"><span data-stu-id="1a715-166">In the left navigation, click **Search &amp; Investigation > Content search**.</span></span>
    
13. <span data-ttu-id="1a715-167">Klicken Sie auf das Pluszeichen, um eine Suche hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="1a715-167">Click the plus icon to add a search.</span></span>
    
14. <span data-ttu-id="1a715-168">Geben Sie im Fenster **neue Suche** **Tailspin Vertrag suchen** im **Feld Name**ein.</span><span class="sxs-lookup"><span data-stu-id="1a715-168">In the **New search** window, type **Tailspin contract search** in **Name**.</span></span>
    
15. <span data-ttu-id="1a715-169">In **Wo möchten Sie uns aussehen?**, klicken Sie auf **Suchen überall,** wählen Sie **Exchange**, **SharePoint**und **Öffentliche Ordner**, und klicken Sie dann auf **nächsten.**</span><span class="sxs-lookup"><span data-stu-id="1a715-169">In **Where do you want us to look?**, click **Search everywhere,** select **Exchange**, **SharePoint**, and **Public Folders**, and then click **Next.**</span></span>
    
16. <span data-ttu-id="1a715-170">In **Was möchten Sie uns suchen?**, geben Sie **Tailspin Vertrag**, und klicken Sie auf **Suchen**.</span><span class="sxs-lookup"><span data-stu-id="1a715-170">In **What do you want us to look for?**, type **Tailspin contract**, and then click **Search**.</span></span>
    
17. <span data-ttu-id="1a715-171">Klicken Sie in der Liste der Suchvorgänge auf den Namen **Tailspin Vertrag suchen** .</span><span class="sxs-lookup"><span data-stu-id="1a715-171">In the list of searches, click the **Tailspin contract search** name.</span></span>
    
18. <span data-ttu-id="1a715-p105">Klicken Sie im Bereich **Tailspin Vertrag Suche** unter **Ergebnisse**auf **Vorschau der Suchergebnisse** . Ein Fenster mit den beiden Dokumenten in der Produktion SharePoint-Website ( **Dokument** und **Document1**) und die **e-Mail testen 1** und **Test e-Mail 3** e-Mails an User6 sollte angezeigt werden. Schließen Sie das Fenster.</span><span class="sxs-lookup"><span data-stu-id="1a715-p105">In the **Tailspin contract search** pane, click **Preview search results** under **Results**. You should see a window listing the two documents on the Production SharePoint site ( **Document** and **Document1**) and the **Test email 1** and **Test email 3** emails to User6. Close the window.</span></span>
    
19. <span data-ttu-id="1a715-175">Klicken Sie im Bereich **Inhaltssuche** unter **Analyze Ergebnisse mit erweiterten eDiscovery**auf **Vorschau Ergebnisse für die Analyse**.</span><span class="sxs-lookup"><span data-stu-id="1a715-175">In the **Content search** pane, under **Analyze results with Advanced eDiscovery**, click **Preview results for analysis**.</span></span>
    
20. <span data-ttu-id="1a715-176">Klicken Sie im Fenster **Vorbereiten der Suche Ergebnisse für die Tailspin Vertrag Suche** klicken Sie auf **die Freigabe vorbereiten** , und warten, bis er abgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="1a715-176">In the **Prepare the search results for Tailspin contract search** window, click **Prepare** and wait for it to complete.</span></span>
    
<span data-ttu-id="1a715-177">In diesem Verfahren erstellen Sie einen neuen Fall für die erweiterte eDiscovery und analysieren die Ergebnisse der Tailspin-Vertragsuche.</span><span class="sxs-lookup"><span data-stu-id="1a715-177">In this procedure, you create a new case for Advanced eDiscovery and analyze the Tailspin contract search results.</span></span>
  
1. <span data-ttu-id="1a715-178">Klicken Sie im linken Navigationsbereich auf **eDiscovery** unter **Suche &amp; Untersuchung**.</span><span class="sxs-lookup"><span data-stu-id="1a715-178">In the left navigation, click **eDiscovery** under **Search &amp; Investigation**.</span></span>
    
2. <span data-ttu-id="1a715-179">Klicken Sie im Bereich **eDiscovery** klicken Sie auf **Erweiterte eDiscovery**.</span><span class="sxs-lookup"><span data-stu-id="1a715-179">In the **eDiscovery** pane, click **Go to Advanced eDiscovery**.</span></span>
    
3. <span data-ttu-id="1a715-180">Klicken Sie in der Registerkarte **Erweitert eDiscovery** auf das plus-Symbol, um eine neue Anfrage hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="1a715-180">In the **Advanced eDiscovery** tab, click the plus icon to add a new case.</span></span>
    
4. <span data-ttu-id="1a715-p106">Klicken Sie im Bereich **Hinzufügen Groß-/Kleinschreibung** Geben Sie **Tailspin Vertrag Fall** im **Feld Name**ein, und klicken Sie dann auf **OK**. Warten Sie die Groß-/Kleinschreibung erstellt werden soll.</span><span class="sxs-lookup"><span data-stu-id="1a715-p106">In the **Add case** pane, type **Tailspin contract dispute** in **Name**, and then click **OK**. Wait for the case to be created.</span></span>
    
5. <span data-ttu-id="1a715-183">Doppelklicken Sie in der Liste den Fall **Tailspin Vertrag Fall** .</span><span class="sxs-lookup"><span data-stu-id="1a715-183">Double click the **Tailspin contract dispute** case in the list.</span></span>
    
6. <span data-ttu-id="1a715-p107">Klicken Sie auf den Container **Tailspin Vertrag Suche** in der Liste **Container** , und klicken Sie dann auf **Prozess**. Warten Sie, bis die Verarbeitung für die Durchführung.</span><span class="sxs-lookup"><span data-stu-id="1a715-p107">In the **Container** list, click the **Tailspin contract search** container, and then click **Process**. Wait for the processing to complete.</span></span>
    
7. <span data-ttu-id="1a715-186">Wenn **Prozess: abgeschlossen** angezeigt wird am unteren Rand des Fensters, klicken Sie auf **Prozess Zusammenfassung** im linken Navigationsbereich auf eine Zusammenfassung anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="1a715-186">When **Process: completed** appears at the bottom of the window, click **Process summary** in the left navigation to see a summary.</span></span>
    
8. <span data-ttu-id="1a715-187">Klicken Sie in der oberen Navigationsleiste auf **Analysieren**.</span><span class="sxs-lookup"><span data-stu-id="1a715-187">In the top navigation, click **Analyze**.</span></span>
    
9. <span data-ttu-id="1a715-188">Geben Sie auf der Seite **Setup** unter **Designs** **3** in **maximale Anzahl von Designs**.</span><span class="sxs-lookup"><span data-stu-id="1a715-188">On the **Setup** page, under **Themes**, type **3** in **Max number of themes**.</span></span>
    
10. <span data-ttu-id="1a715-p108">Klicken Sie auf **Analysieren** , und warten Sie für die Analyse abgeschlossen. Eine Reihe von Kreis-Diagrammen mit Analyse der Zielgruppe, Dokumente, e-Mail-Nachrichten und Anlagen sollte angezeigt werden. Weitere Informationen finden Sie unter [Ergebnisse anzeigen analysieren](https://support.office.com/article/Viewing-Analyze-results-5974f3c2-89fe-4c5f-ac7b-57f214437f7e).</span><span class="sxs-lookup"><span data-stu-id="1a715-p108">Click **Analyze** and wait for the analysis to complete. You should see a series of pie charts with analysis of the target population, documents, emails, and attachments. For more information, see [Viewing Analyze results](https://support.office.com/article/Viewing-Analyze-results-5974f3c2-89fe-4c5f-ac7b-57f214437f7e).</span></span>
    
<span data-ttu-id="1a715-192">Sie können diese Umgebung jetzt verwenden, um neue Inhalte, neue Suchvorgänge und neue Fälle zu erstellen und um weiter mit der erweiterten eDiscovery in Office 365 zu experimentieren.</span><span class="sxs-lookup"><span data-stu-id="1a715-192">You can now use this environment to create new content, new searches and cases, and experiment further with Advanced eDiscovery in Office 365.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="1a715-193">Weitere Artikel</span><span class="sxs-lookup"><span data-stu-id="1a715-193">See Also</span></span>

[<span data-ttu-id="1a715-194">Testumgebungsanleitungen (TLGs) zur Cloudakzeptanz</span><span class="sxs-lookup"><span data-stu-id="1a715-194">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="1a715-195">Basiskonfiguration der Entwicklungs-/Testumgebung</span><span class="sxs-lookup"><span data-stu-id="1a715-195">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="1a715-196">Office 365-Entwicklungs-/Testumgebung</span><span class="sxs-lookup"><span data-stu-id="1a715-196">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="1a715-197">DirSync für die Office 365-Entwicklungs-/Testumgebung</span><span class="sxs-lookup"><span data-stu-id="1a715-197">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="1a715-198">Cloud App Security für Ihre Office 365-Entwicklungs-/Testumgebung</span><span class="sxs-lookup"><span data-stu-id="1a715-198">Cloud App Security for your Office 365 dev/test environment</span></span>](cloud-app-security-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="1a715-199">Cloudakzeptanz und Hybridlösungen</span><span class="sxs-lookup"><span data-stu-id="1a715-199">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)

[<span data-ttu-id="1a715-200">Office 365 erweiterte eDiscovery</span><span class="sxs-lookup"><span data-stu-id="1a715-200">Office 365 Advanced eDiscovery</span></span>](https://support.office.com/article/Office-365-Advanced-eDiscovery-fd53438a-a760-45f6-9df4-861b50161ae4)


