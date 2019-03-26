---
title: Advanced eDiscovery für die Office 365-Entwicklungs-/Testumgebung
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: d4c49a6f-abfd-4d68-b353-259b4eefb033
description: 'Zusammenfassung: Konfigurieren und Demonstrieren der Erweiterten eDiscovery in Office 365 mit Beispieldaten in der Office 365-Entwicklungs-/Testumgebung.'
ms.openlocfilehash: 6c52c7c7fdc31616e58f186484d2d8c4506b7ea6
ms.sourcegitcommit: 4ef8e113fa20b539de1087422455fc26ff123d55
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "30573819"
---
# <a name="advanced-ediscovery-for-your-office-365-devtest-environment"></a><span data-ttu-id="be957-103">Advanced eDiscovery für die Office 365-Entwicklungs-/Testumgebung</span><span class="sxs-lookup"><span data-stu-id="be957-103">Advanced eDiscovery for your Office 365 dev/test environment</span></span>

 <span data-ttu-id="be957-104">**Zusammenfassung:** Konfigurieren und Demonstrieren der Erweiterten eDiscovery in Office 365 mit Beispieldaten in der Office 365-Entwicklungs-/Testumgebung.</span><span class="sxs-lookup"><span data-stu-id="be957-104">**Summary:** Configure and demonstrate Office 365 Advanced eDiscovery with sample data in your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="be957-105">Mit Office 365 Advanced eDiscovery können Sie wichtige Informationen über die in Office 365 gespeicherten Daten schnell finden und analysieren, einschließlich e-Mails und Dokumente.</span><span class="sxs-lookup"><span data-stu-id="be957-105">Office 365 Advanced eDiscovery lets you quickly find and analyze relevant information across the data that is stored in Office 365, including email and documents.</span></span> <span data-ttu-id="be957-106">Auf diese Weise können, insbesondere bei Rechtsstreitigkeiten, enorme Zeit- und Geldmengen gespart werden.</span><span class="sxs-lookup"><span data-stu-id="be957-106">This can save enormous amounts of time and expense, especially in litigation situations.</span></span> <span data-ttu-id="be957-107">Weitere Informationen finden Sie unter [Erweiterte eDisvocery in Office 365](https://support.office.com/article/Office-365-Advanced-eDiscovery-fd53438a-a760-45f6-9df4-861b50161ae4).</span><span class="sxs-lookup"><span data-stu-id="be957-107">For more information, see [Office 365 Advanced eDiscovery](https://support.office.com/article/Office-365-Advanced-eDiscovery-fd53438a-a760-45f6-9df4-861b50161ae4).</span></span>
  
<span data-ttu-id="be957-108">Mit den Anweisungen in diesem Artikel erstellen Sie eine kleine Gruppe von Daten für eine fiktive Vertragsstreitigkeit und analysieren diese mit der Erweiterten eDiscovery.</span><span class="sxs-lookup"><span data-stu-id="be957-108">With the instructions in this article, you create a small set of data for a fictional contract dispute and analyze it with Advanced eDiscovery.</span></span>
  
> [!TIP]
> <span data-ttu-id="be957-109">Klicken Sie [hier](http://aka.ms/catlgstack), um eine visuelle Darstellung aller Artikel im Stapel der Testumgebungsanleitungen in der One Microsoft Cloud zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="be957-109">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-create-your-office-365-devtest-environment"></a><span data-ttu-id="be957-110">Phase 1: Erstellen Ihrer Office 365-Entwicklungs-/Testumgebung</span><span class="sxs-lookup"><span data-stu-id="be957-110">Phase 1: Create your Office 365 dev/test environment</span></span>

<span data-ttu-id="be957-111">Wenn Sie Advanced eDiscovery auf einfache Weise mit den Mindestanforderungen testen möchten, befolgen Sie die Anweisungen in Phase 2 und Phase 3 von [Office 365 dev/Test Environment](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="be957-111">If you just want to test Advanced eDiscovery in a lightweight way with the minimum requirements, follow the instructions in Phase 2 and Phase 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="be957-112">Wenn Sie die erweiterte eDiscovery in einem simulierten Unternehmen testen möchten, befolgen Sie die Anweisungen unter [Dirsync für Ihre Office 365 dev/Test-Umgebung](dirsync-for-your-office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="be957-112">If you want to test Advanced eDiscovery in a simulated enterprise, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="be957-113">Für das Testen der Erweiterten eDiscovery ist keine simulierte Unternehmensumgebung erforderlich, die ein simuliertes Intranet, das mit dem Internet verbunden ist, und die Verzeichnissynchronisierung für eine Windows Server AD-Gesamtstruktur umfasst.</span><span class="sxs-lookup"><span data-stu-id="be957-113">Testing Advanced eDiscovery does not require the simulated enterprise environment, which includes a simulated intranet connected to the Internet and directory synchronization for a Windows Server AD forest.</span></span> <span data-ttu-id="be957-114">Sie wird hier als Option bereitgestellt, damit Sie Tests und experimentieren in einer Umgebung ausführen können, die eine typische Organisation darstellt.</span><span class="sxs-lookup"><span data-stu-id="be957-114">It is provided here as an option so that you can perform testing and experimentation in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-create-example-data-for-advanced-ediscovery"></a><span data-ttu-id="be957-115">Phase 2: Erstellen von Beispieldaten für die Erweiterte eDiscovery</span><span class="sxs-lookup"><span data-stu-id="be957-115">Phase 2: Create example data for Advanced eDiscovery</span></span>

<span data-ttu-id="be957-116">In diesem Verfahren erstellen Sie E-Mail-Nachrichten, die Sie später in einem erweiterten eDiscovery-Fall analysieren werden.</span><span class="sxs-lookup"><span data-stu-id="be957-116">In this procedure, you create email messages that will you later analyze in an Advanced eDiscovery case.</span></span>
  
1. <span data-ttu-id="be957-117">Öffnen Sie Internet Explorer, und melden [https://outlook.com](https://outlook.com) Sie sich bei dem Outlook-Konto an, das Sie in Phase 2 von[Office 365 dev/Test Environment](office-365-dev-test-environment.md)erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="be957-117">Open Internet Explorer and sign in at [https://outlook.com](https://outlook.com) to the Outlook account you created in Phase 2 of[Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
    
  - <span data-ttu-id="be957-118">Wenn Sie die einfache Entwicklungs-/Testumgebung verwenden, öffnen Sie eine private Sitzung von Internet Explorer, und melden Sie sich von Ihrem lokalen Computer aus an.</span><span class="sxs-lookup"><span data-stu-id="be957-118">If you are using the lightweight dev/test environment, open a private session of Internet Explorer and sign in from your local computer.</span></span>
    
  - <span data-ttu-id="be957-119">Wenn Sie die simulierte Enterprise-dev/Test-Umgebung verwenden, verwenden Sie[https://portal.azure.com](https://portal.azure.com)das Azure-Portal (), um eine Verbindung mit dem virtuellen Computer Client1 herzustellen, und melden Sie sich dann bei CLIENT1 an.</span><span class="sxs-lookup"><span data-stu-id="be957-119">If you are using the simulated enterprise dev/test environment, use the Azure portal ([https://portal.azure.com](https://portal.azure.com)) to connect to the CLIENT1 virtual machine, and then sign in from CLIENT1.</span></span>
    
2. <span data-ttu-id="be957-120">Klicken Sie auf der Registerkarte **Outlook-Mail** auf **Neu**.</span><span class="sxs-lookup"><span data-stu-id="be957-120">On the **Outlook Mail** tab, click **New**.</span></span>
    
3. <span data-ttu-id="be957-121">Geben **Sie unter an**die e-Mail-Adresse des User6-Kontos Ihres Testabonnements ein ( **User6 @.**<organization name></span><span class="sxs-lookup"><span data-stu-id="be957-121">In **To**, type the email address of the User6 account of your trial subscription ( **user6@.**<organization name></span></span> <span data-ttu-id="be957-122">**. onmicrosoft.com**).</span><span class="sxs-lookup"><span data-stu-id="be957-122">**.onmicrosoft.com**).</span></span>
    
4. <span data-ttu-id="be957-123">Geben Sie für den Betreff **Test-E-Mail 1** ein.</span><span class="sxs-lookup"><span data-stu-id="be957-123">For the subject, type **Test email 1**.</span></span>
    
5. <span data-ttu-id="be957-124">Geben Sie in den Textbereich **Tailspin Vertragsentwurf** ein, und klicken Sie dann auf **Senden**.</span><span class="sxs-lookup"><span data-stu-id="be957-124">In the body, type **Tailspin contract draft**, and then click **Send**.</span></span>
    
6. <span data-ttu-id="be957-125">Klicken Sie auf der Registerkarte **Outlook-Mail** auf **Neu**.</span><span class="sxs-lookup"><span data-stu-id="be957-125">On the **Outlook Mail** tab, click **New**.</span></span>
    
7. <span data-ttu-id="be957-126">Geben Sie unter **An** die E-Mail-Adresse des user6-Kontos Ihres Testabonnements ein.</span><span class="sxs-lookup"><span data-stu-id="be957-126">In **To**, type the email address of the User6 account of your trial subscription.</span></span>
    
8. <span data-ttu-id="be957-127">Geben Sie für den Betreff **Test-E-Mail 2** ein.</span><span class="sxs-lookup"><span data-stu-id="be957-127">For the subject, type **Test email 2**.</span></span>
    
9. <span data-ttu-id="be957-128">Geben Sie in den Textbereich **Tailspin Geschäftsessen** ein, und klicken Sie dann auf **Senden**.</span><span class="sxs-lookup"><span data-stu-id="be957-128">In the body, type **Tailspin lunch meeting**, and then click **Send**.</span></span>
    
10. <span data-ttu-id="be957-129">Klicken Sie auf der Registerkarte **Outlook-Mail** auf **Neu**.</span><span class="sxs-lookup"><span data-stu-id="be957-129">On the **Outlook Mail** tab, click **New**.</span></span>
    
11. <span data-ttu-id="be957-130">Geben Sie unter **An** die E-Mail-Adresse des user6-Kontos Ihres Testabonnements ein.</span><span class="sxs-lookup"><span data-stu-id="be957-130">In **To**, type the email address of the User6 account of your trial subscription.</span></span>
    
12. <span data-ttu-id="be957-131">Geben Sie für den Betreff **Test-E-Mail 3** ein.</span><span class="sxs-lookup"><span data-stu-id="be957-131">For the subject, type **Test email 3**.</span></span>
    
13. <span data-ttu-id="be957-132">Geben Sie in den Textbereich **Tailspin vertragliche Unstimmigkeiten** ein, und klicken Sie dann auf **Senden**.</span><span class="sxs-lookup"><span data-stu-id="be957-132">In the body, type **Tailspin contract disagreement**, and then click **Send**.</span></span>
    
14. <span data-ttu-id="be957-133">Klicken Sie oben rechts auf das Benutzersymbol, und klicken Sie dann auf **Abmelden**.</span><span class="sxs-lookup"><span data-stu-id="be957-133">Click the user icon in the upper right corner, and then click **Sign out**.</span></span>
    
15. <span data-ttu-id="be957-134">Öffnen Sie eine neue Registerkarte, und melden Sie sich beim Office[https://www.office.com](https://www.office.com)365-Portal () mit dem Kontonamen und dem Kennwort des User6-Kontos Ihres Testabonnements an.</span><span class="sxs-lookup"><span data-stu-id="be957-134">Open a new tab and sign in to the Office 365 portal ([https://www.office.com](https://www.office.com)) with the account name and password of the User6 account of your trial subscription.</span></span>
    
16. <span data-ttu-id="be957-135">Klicken Sie auf der Registerkarte **Office 365-Portal** auf **E-Mail**.</span><span class="sxs-lookup"><span data-stu-id="be957-135">On the **Office 365 portal** tab, click **Mail**.</span></span>
    
17. <span data-ttu-id="be957-136">Überprüfen Sie auf der Registerkarte **Mail-User6-Outlook** , ob User6 alle drei e-Mails aus dem Outlook-e-Mail-Konto erhalten hat.</span><span class="sxs-lookup"><span data-stu-id="be957-136">On the **Mail - User6 - Outlook** tab, check that User6 received all three emails from the Outlook email account.</span></span>
    
18. <span data-ttu-id="be957-137">Wechseln Sie zurück zu Registerkarte **Office 365-Portal** für User6.</span><span class="sxs-lookup"><span data-stu-id="be957-137">Switch back to the **Office 365 portal tab** for User6.</span></span>
    
19. <span data-ttu-id="be957-138">Klicken Sie oben rechts auf das Benutzersymbol, und klicken Sie dann auf **Abmelden**.</span><span class="sxs-lookup"><span data-stu-id="be957-138">Click the user icon in the upper right corner, and then click **Sign out.**</span></span>
    
<span data-ttu-id="be957-139">In diesem Verfahren erstellen Sie zwei Word-Dokumente, die Sie später in einem erweiterten eDiscovery-Fall analysieren werden.</span><span class="sxs-lookup"><span data-stu-id="be957-139">In this procedure, you create two Word documents that will you will later analyze in an Advanced eDiscovery case.</span></span>
  
1. <span data-ttu-id="be957-140">Klicken Sie auf der Seite **Office** auf **Anmelden**, melden Sie sich mit den Anmeldeinformationen des globalen Administratorkontos an.</span><span class="sxs-lookup"><span data-stu-id="be957-140">On the **Office** page, click **Sign in,** sign in with the credentials of your global administrator account.</span></span>
    
2. <span data-ttu-id="be957-141">greifen sie auf einer neuen registerkarte auf die URL ihrer produktions-sharepoint-website zu: **https://** <fictional organization name> **. sharepoint.com/sites/production**</span><span class="sxs-lookup"><span data-stu-id="be957-141">On a new tab, access the URL of your Production SharePoint site: **https://**<fictional organization name> **.sharepoint.com/sites/production**</span></span>
    
3. <span data-ttu-id="be957-142">Klicken Sie auf der Registerkarte **Produktions-Websitesammlung** unter **Dokumente** auf **Neu > Word-Dokument**.</span><span class="sxs-lookup"><span data-stu-id="be957-142">On the **Production site collection** tab, under **Documents**, click **New > Word Document**.</span></span>
    
4. <span data-ttu-id="be957-143">Geben Sie auf der Seite **Word Online\*\*\*\*Tailspin-Vertrangsentwurf** ein, warten Sie, bis **Gespeichert** im Titel angezeigt wird, und schließen Sie dann die Seite **Word Online**.</span><span class="sxs-lookup"><span data-stu-id="be957-143">On the **Word Online** page, type **Tailspin draft contract**, wait until it displays **Saved** in the title, and then close the **Word Online** page tab.</span></span>
    
5. <span data-ttu-id="be957-144">Klicken Sie auf der Registerkarte **Produktions-Websitesammlung** unter **Dokumente** auf **Neu > Word-Dokument**.</span><span class="sxs-lookup"><span data-stu-id="be957-144">On the **Production site collection** tab, under **Documents**, click **New > Word Document**.</span></span>
    
6. <span data-ttu-id="be957-145">	Geben Sie auf der Seite *\*Word Online\*\*\*\*Tailspin-Vertrangsentwurf** ein, warten Sie, bis *\*Gespeichert** im Titel angezeigt wird, und schließen Sie dann die Seite *\*Word Online*\*.</span><span class="sxs-lookup"><span data-stu-id="be957-145">On the **Word Online** tab, type **Tailspin contract dispute notes**, wait until it displays **Saved** in the title, and then close the **Word Online** tab.</span></span>
    
7. <span data-ttu-id="be957-146">Auf der Registerkarte **Produktions-Websitesammlung** sollte nun **Dokument** und **Dokument1** in der Liste der Dokumente angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="be957-146">On the **Production site collection** tab, you should see **Document** and **Document1** in the list of documents.</span></span>
    
8. <span data-ttu-id="be957-147">Schließen Sie die Registerkarte **Produktions-Websitesammlung**.</span><span class="sxs-lookup"><span data-stu-id="be957-147">Close the **Production site collection** tab.</span></span>
    
## <a name="phase-3-use-advanced-ediscovery-for-a-legal-dispute"></a><span data-ttu-id="be957-148">Phase 3: Verwenden von Advanced eDiscovery für eine Rechtsstreitigkeit</span><span class="sxs-lookup"><span data-stu-id="be957-148">Phase 3: Use Advanced eDiscovery for a legal dispute</span></span>

<span data-ttu-id="be957-149">Leider ist es bei einer vertraglichen Streitigkeit zwischen Ihrer Organisation und Tailspin Toys zu einem Gerichtsverfahren gekommen.</span><span class="sxs-lookup"><span data-stu-id="be957-149">Unfortunately, a contract dispute between your organization and Tailspin Toys has reached the point of legal action.</span></span> <span data-ttu-id="be957-150">In diesem Verfahren erstellen und konfigurieren Sie einen erweiterten eDiscovery-Fall, um e-Mails und Dokumente zu suchen und zu analysieren, die den Text "Tailspin Contract" enthalten.</span><span class="sxs-lookup"><span data-stu-id="be957-150">In this procedure, you create and configure an Advanced eDiscovery case to search for and analyze email and documents that contain the text "Tailspin contract".</span></span>
  
<span data-ttu-id="be957-151">Der Prozess für die Verwendung der erweiterten eDiscovery ist wie folgt:</span><span class="sxs-lookup"><span data-stu-id="be957-151">The process for using Advanced eDiscovery is the following:</span></span>
  
- <span data-ttu-id="be957-152">Erstellen Sie eine Suche im Security &amp; Compliance Center, analysieren Sie die Ergebnisse, und bereiten Sie die Ergebnisse für die erweiterte eDiscovery vor.</span><span class="sxs-lookup"><span data-stu-id="be957-152">Create a search in the Security &amp; Compliance center, analyze its results, and then prepare the results for Advanced eDiscovery.</span></span>
    
- <span data-ttu-id="be957-153">Erstellen Sie und konfigurieren Sie einen Fall in der erweiterten eDiscovery, und analysieren Sie die Suchergebnisse.</span><span class="sxs-lookup"><span data-stu-id="be957-153">Create and configure a case in Advanced eDiscovery and analyze the search results.</span></span>
    
<span data-ttu-id="be957-154">In diesem Verfahren erstellen Sie eine Suche im Security &amp; Compliance Center für "Tailspin Contract", schauen Sie sich die Ergebnisse an, und bereiten Sie dann die Ergebnisse für Advanced eDiscovery vor.</span><span class="sxs-lookup"><span data-stu-id="be957-154">In this procedure, you create a search in the Security &amp; Compliance center for "Tailspin contract", look at the results, and then prepare the results for Advanced eDiscovery.</span></span>
  
1. <span data-ttu-id="be957-155">Klicken Sie auf der Registerkarte **Office 365-Portal** auf **Admin**.</span><span class="sxs-lookup"><span data-stu-id="be957-155">From the **Office 365 portal** tab, click **Admin**.</span></span>
    
2. <span data-ttu-id="be957-156">Klicken Sie im linken Navigationsbereich der Admin Center-Registerkarte auf **Admin Center > Compliance**.</span><span class="sxs-lookup"><span data-stu-id="be957-156">In the left navigation of the Admin center tab, click **Admin centers > Compliance**.</span></span>
    
3. <span data-ttu-id="be957-157">Klicken Sie auf der Registerkarte \*\* &amp; Sicherheitskonformität\*\* auf **Berechtigungen**.</span><span class="sxs-lookup"><span data-stu-id="be957-157">On the **Security &amp; Compliance** tab, click **Permissions**.</span></span>
    
4. <span data-ttu-id="be957-158">Doppelklicken Sie in der Liste **Berechtigungen** auf **Organisationsverwaltung**.</span><span class="sxs-lookup"><span data-stu-id="be957-158">In the **Permissions** list, double-click **Organization Management**.</span></span>
    
5. <span data-ttu-id="be957-159">Klicken Sie im Fenster **Rollengruppe** unter **Mitglieder** auf das Pluszeichen (+).</span><span class="sxs-lookup"><span data-stu-id="be957-159">In the **Role Group** window, under **Members**, click the plus sign.</span></span>
    
6. <span data-ttu-id="be957-160">Doppelklicken Sie im Fenster **Auswählen von Mitgliedern** auf den Namen Ihres Administratorkontos, und klicken Sie dann auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="be957-160">In the **Select Members** window, double-click the name of your administrator account, and then click **OK**.</span></span>
    
7. <span data-ttu-id="be957-161">Klicken Sie im Fenster **Rollengruppe** auf **Speichern**.</span><span class="sxs-lookup"><span data-stu-id="be957-161">In the **Role Group** window, click **Save**.</span></span>
    
8. <span data-ttu-id="be957-162">Doppelklicken Sie in der Liste **Berechtigungen** auf **eDiscovery-Manager**.</span><span class="sxs-lookup"><span data-stu-id="be957-162">In the **Permissions** list, double-click **eDiscovery Manager**.</span></span>
    
9. <span data-ttu-id="be957-163">Klicken Sie im Fenster **Rollengruppe** unter **eDiscovery-Administrator** auf das Pluszeichen.</span><span class="sxs-lookup"><span data-stu-id="be957-163">In the **Role Group** window, under **eDiscovery Administrator**, click the plus icon.</span></span>
    
10. <span data-ttu-id="be957-164">Doppelklicken Sie im Fenster **Auswählen von Mitgliedern** auf den Namen Ihres Administratorkontos, und klicken Sie dann auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="be957-164">In the **Select Members** window, double-click the name of your administrator account, and then click **OK**.</span></span>
    
11. <span data-ttu-id="be957-165">Klicken Sie im Fenster **Rollengruppe** auf **Speichern**.</span><span class="sxs-lookup"><span data-stu-id="be957-165">In the **Role Group** window, click **Save**.</span></span>
    
12. <span data-ttu-id="be957-166">Klicken Sie im linken Navigationsbereich auf Such \*\* &amp; Untersuchung > Inhaltssuche\*\*.</span><span class="sxs-lookup"><span data-stu-id="be957-166">In the left navigation, click **Search &amp; Investigation > Content search**.</span></span>
    
13. <span data-ttu-id="be957-167">Klicken Sie auf das Pluszeichen, um eine Suche hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="be957-167">Click the plus icon to add a search.</span></span>
    
14. <span data-ttu-id="be957-168">Geben Sie im Fenster **Neue Suche** den Text **Tailspin Vertragsuche** unter **Name** ein.</span><span class="sxs-lookup"><span data-stu-id="be957-168">In the **New search** window, type **Tailspin contract search** in **Name**.</span></span>
    
15. <span data-ttu-id="be957-169">Klicken Sie unter **Wo sollen wir suchen?** auf **Überall suchen**, wählen Sie **Exchange**, **SharePoint** und **Öffentliche Ordner** aus, und klicken Sie dann auf **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="be957-169">In **Where do you want us to look?**, click **Search everywhere,** select **Exchange**, **SharePoint**, and **Public Folders**, and then click **Next.**</span></span>
    
16. <span data-ttu-id="be957-170">Geben Sie unter **Wonach sollen wir suchen?** den Text **Tailspin Vertrag** ein, und klicken Sie dann auf **Suche**.</span><span class="sxs-lookup"><span data-stu-id="be957-170">In **What do you want us to look for?**, type **Tailspin contract**, and then click **Search**.</span></span>
    
17. <span data-ttu-id="be957-171">Klicken Sie in der Liste von Suchvorgängen auf den Namen **Tailspin Vertragsuche**.</span><span class="sxs-lookup"><span data-stu-id="be957-171">In the list of searches, click the **Tailspin contract search** name.</span></span>
    
18. <span data-ttu-id="be957-172">Klicken Sie im Bereich **Tailspin Vertragsuche** auf **Vorschau der Suchergebnisse** unter **Ergebnisse**.</span><span class="sxs-lookup"><span data-stu-id="be957-172">In the **Tailspin contract search** pane, click **Preview search results** under **Results**.</span></span> <span data-ttu-id="be957-173">Es sollte ein Fenster mit den beiden Dokumenten auf der Produktions-SharePoint-Website ( **Dokument** und **document1**) und der **Test-e-Mail 1** und **e-Mail-** Nachrichten mit e-Mails an User6 angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="be957-173">You should see a window listing the two documents on the Production SharePoint site ( **Document** and **Document1**) and the **Test email 1** and **Test email 3** emails to User6.</span></span> <span data-ttu-id="be957-174">Schließen Sie das Fenster.</span><span class="sxs-lookup"><span data-stu-id="be957-174">Close the window.</span></span>
    
19. <span data-ttu-id="be957-175">Klicken Sie im Bereich **Inhaltssuche** unter **Analysieren der Ergebnisse mit der erweiterten eDiscovery** auf **Ergebnisse für Analyse in Vorschau anzeigen**.</span><span class="sxs-lookup"><span data-stu-id="be957-175">In the **Content search** pane, under **Analyze results with Advanced eDiscovery**, click **Preview results for analysis**.</span></span>
    
20. <span data-ttu-id="be957-176">Klicken Sie im Fenster **Vorbereiten der Suchergebnisse für Tailspin Vertragsuche** auf **Vorbereiten** und warten Sie, bis der Vorgang abgeschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="be957-176">In the **Prepare the search results for Tailspin contract search** window, click **Prepare** and wait for it to complete.</span></span>
    
<span data-ttu-id="be957-177">In diesem Verfahren erstellen Sie einen neuen Fall für die erweiterte eDiscovery und analysieren die Ergebnisse der Tailspin-Vertragsuche.</span><span class="sxs-lookup"><span data-stu-id="be957-177">In this procedure, you create a new case for Advanced eDiscovery and analyze the Tailspin contract search results.</span></span>
  
1. <span data-ttu-id="be957-178">Klicken Sie im linken Navigationsbereich unter \*\* &amp; Such Prüfung\*\*auf **eDiscovery** .</span><span class="sxs-lookup"><span data-stu-id="be957-178">In the left navigation, click **eDiscovery** under **Search &amp; Investigation**.</span></span>
    
2. <span data-ttu-id="be957-179">Klicken Sie im Bereich **eDiscovery** auf **Zur erweiterten eDiscovery wechseln**.</span><span class="sxs-lookup"><span data-stu-id="be957-179">In the **eDiscovery** pane, click **Go to Advanced eDiscovery**.</span></span>
    
3. <span data-ttu-id="be957-180">Klicken Sie auf der Registerkarte **Erweiterte eDiscovery** auf das Pluszeichen, um einen neuen Fall hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="be957-180">In the **Advanced eDiscovery** tab, click the plus icon to add a new case.</span></span>
    
4. <span data-ttu-id="be957-p106">	Geben Sie im Bereich *\*Fall hinzufügen** den Text *\*Tailspin vertragliche Unstimmigkeit** unter *\*Name** ein, und klicken Sie dann auf *\*OK*\*. Warten Sie, bis der Fall erstellt wurde.</span><span class="sxs-lookup"><span data-stu-id="be957-p106">In the **Add case** pane, type **Tailspin contract dispute** in **Name**, and then click **OK**. Wait for the case to be created.</span></span>
    
5. <span data-ttu-id="be957-183">Doppelklicken Sie auf den Fall **Tailspin vertragliche Unstimmigkeit** in der Liste. </span><span class="sxs-lookup"><span data-stu-id="be957-183">Double click the **Tailspin contract dispute** case in the list.</span></span>
    
6. <span data-ttu-id="be957-184">Klicken Sie in der Liste **Container** auf den **Suchcontainer Tailspin Contract** , und klicken Sie dann auf **verarbeiten**.</span><span class="sxs-lookup"><span data-stu-id="be957-184">In the **Container** list, click the **Tailspin contract search** container, and then click **Process**.</span></span> <span data-ttu-id="be957-185">Warten Sie, bis die Bearbeitung abgeschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="be957-185">Wait for the processing to complete.</span></span>
    
7. <span data-ttu-id="be957-186">Wenn am unteren Rand des Fensters **Verarbeitung abgeschlossen** angezeigt wird, klicken Sie in der linken Navigation auf **Prozesszusammenfassung**, um eine Zusammenfassung anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="be957-186">When **Process: completed** appears at the bottom of the window, click **Process summary** in the left navigation to see a summary.</span></span>
    
8. <span data-ttu-id="be957-187">Klicken Sie auf der oberen Navigationsleiste auf **Analysieren**.</span><span class="sxs-lookup"><span data-stu-id="be957-187">In the top navigation, click **Analyze**.</span></span>
    
9. <span data-ttu-id="be957-188">Geben Sie auf der Seite **Setup** unter **Designs** die Zahl **3** in **Maximale Anzahl von Designs** ein.</span><span class="sxs-lookup"><span data-stu-id="be957-188">On the **Setup** page, under **Themes**, type **3** in **Max number of themes**.</span></span>
    
10. <span data-ttu-id="be957-189">Klicken Sie auf **Analysieren** und warten Sie, bis die Analyse abgeschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="be957-189">Click **Analyze** and wait for the analysis to complete.</span></span> <span data-ttu-id="be957-190">Es sollte eine Reihe von Kreisdiagrammen mit der Analyse der Zielgruppe, Dokumenten, E-Mails und Anlagen angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="be957-190">You should see a series of pie charts with analysis of the target population, documents, emails, and attachments.</span></span> <span data-ttu-id="be957-191">Weitere Informationen finden Sie unter [Anzeigen von Analyseergebnissen](https://support.office.com/article/Viewing-Analyze-results-5974f3c2-89fe-4c5f-ac7b-57f214437f7e).</span><span class="sxs-lookup"><span data-stu-id="be957-191">For more information, see [Viewing Analyze results](https://support.office.com/article/Viewing-Analyze-results-5974f3c2-89fe-4c5f-ac7b-57f214437f7e).</span></span>
    
<span data-ttu-id="be957-192">Sie können diese Umgebung jetzt verwenden, um neue Inhalte, neue Suchvorgänge und neue Fälle zu erstellen und um weiter mit der erweiterten eDiscovery in Office 365 zu experimentieren.</span><span class="sxs-lookup"><span data-stu-id="be957-192">You can now use this environment to create new content, new searches and cases, and experiment further with Advanced eDiscovery in Office 365.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="be957-193">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="be957-193">See Also</span></span>

[<span data-ttu-id="be957-194">Testumgebungsanleitungen (TLGs) zur Cloudakzeptanz</span><span class="sxs-lookup"><span data-stu-id="be957-194">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="be957-195">Basiskonfiguration der Entwicklungs-/Testumgebung</span><span class="sxs-lookup"><span data-stu-id="be957-195">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="be957-196">Office 365-Entwicklungs-/Testumgebung</span><span class="sxs-lookup"><span data-stu-id="be957-196">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="be957-197">DirSync für die Office 365-Entwicklungs-/Testumgebung</span><span class="sxs-lookup"><span data-stu-id="be957-197">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="be957-198">Cloud App Security für Ihre Office 365-Entwicklungs-/Testumgebung</span><span class="sxs-lookup"><span data-stu-id="be957-198">Cloud App Security for your Office 365 dev/test environment</span></span>](cloud-app-security-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="be957-199">Cloudakzeptanz und Hybridlösungen</span><span class="sxs-lookup"><span data-stu-id="be957-199">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)

[<span data-ttu-id="be957-200">Office 365 Advanced eDiscovery</span><span class="sxs-lookup"><span data-stu-id="be957-200">Office 365 Advanced eDiscovery</span></span>](https://support.office.com/article/Office-365-Advanced-eDiscovery-fd53438a-a760-45f6-9df4-861b50161ae4)


