---
title: Office 365- und Dynamics 365-Entwicklungs-/Testumgebung
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
- Strat_O365_Enterprise
- Ent_TLGs
ms.assetid: 098c1a1d-83a1-40eb-bbc9-47de7af8bb23
description: "Zusammenfassung: Verwenden dieser Test Lab Guide für Ihre Office 365-Umgebung Test-/Dynamics 365 hinzufügen."
ms.openlocfilehash: a61e831eeabc159da4774cfe730c694c383e6801
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/11/2018
---
# <a name="office-365-and-dynamics-365-devtest-environment"></a><span data-ttu-id="0a109-103">Office 365- und Dynamics 365-Entwicklungs-/Testumgebung</span><span class="sxs-lookup"><span data-stu-id="0a109-103">Office 365 and Dynamics 365 dev/test environment</span></span>

 <span data-ttu-id="0a109-104">**Zusammenfassung:** Verwenden Sie in diesem Test Lab Guide Dynamics 365 Ihre Office 365 Dev/Test-Umgebung hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="0a109-104">**Summary:** Use this Test Lab Guide to add Dynamics 365 to your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="0a109-105">Mit den Anweisungen in diesem Artikel fügen Sie der Organisation Ihrer Office 365-Entwicklungs-/Testumgebung ein Dynamics 365-Testabonnement hinzu und erstellen so eine Office 365- und Dynamics 365-Entwicklungs-/Testumgebung.</span><span class="sxs-lookup"><span data-stu-id="0a109-105">With the instructions in this article, you add a Dynamics 365 trial subscription to the same organization as your Office 365 dev/test environment, creating an Office 365 and Dynamics 365 dev/test environment.</span></span>
  
<span data-ttu-id="0a109-p101">Sie können ein Dynamics 365-Testabonnement verwenden, um die Funktionen von Dynamics 365 zu demonstrieren. Die folgenden Lösungen sind in einer Dynamics 365 Plan 1, Enterprise Edition-Testversion enthalten:</span><span class="sxs-lookup"><span data-stu-id="0a109-p101">You can use a Dynamics 365 trial subscription to demonstrate features and capabilities of Dynamics 365. The following solutions are included with a Dynamics 365 Plan 1, Enterprise Edition trial:</span></span>
  
- <span data-ttu-id="0a109-p102">[Microsoft Dynamics 365 für Sales](https://www.microsoft.com/dynamics365/sales). Erhöhen Sie Ihre Umsätze mit Automatisierung und digitalen Intelligence unterstützen die Vertriebsmitarbeiter konzentrieren und Intelligenter arbeiten.</span><span class="sxs-lookup"><span data-stu-id="0a109-p102">[Microsoft Dynamics 365 for Sales](https://www.microsoft.com/dynamics365/sales). Increase your sales with automation and digital intelligence helping your salespeople stay focused and work smarter.</span></span>
    
- <span data-ttu-id="0a109-p103">[Microsoft Dynamics 365 Customer Service](https://www.microsoft.com/dynamics365/customer-service). Verdienen Sie können Ihre Agenten erteilen Sie die ausführliche Informationen und die digitalen Intelligence nahtlos Serverausfalls benötigten.</span><span class="sxs-lookup"><span data-stu-id="0a109-p103">[Microsoft Dynamics 365 for Customer Service](https://www.microsoft.com/dynamics365/customer-service). Earn loyalty by giving your agents the complete information and digital intelligence they need to provide seamless service.</span></span>
    
- <span data-ttu-id="0a109-p104">[Microsoft Dynamics 365 für Dienst dar](https://www.microsoft.com/dynamics365/field-service). Master-Shape der Dienst aufrufen, indem Sie Optimieren Ihrer Zeitpläne, und rüstete Ihrer Mitarbeiter und vorhersehbare Tools Gewinn steigern verwenden.</span><span class="sxs-lookup"><span data-stu-id="0a109-p104">[Microsoft Dynamics 365 for Field Service](https://www.microsoft.com/dynamics365/field-service). Master the service call by optimizing your schedules, equipping your workforce, and using predictive tools to increase profit.</span></span>
    
- <span data-ttu-id="0a109-p105">[Microsoft Dynamics 365 für Project Service-Automatisierung](https://www.microsoft.com/en-us/dynamics365/project-service-automation). Abgeschlossen Sie Ihre Projekte erfolgreich wurde, und erstellen Sie gewinnbringenden Beziehungen mit produktive Mitarbeitern und intelligente Tools.</span><span class="sxs-lookup"><span data-stu-id="0a109-p105">[Microsoft Dynamics 365 for Project Service Automation](https://www.microsoft.com/en-us/dynamics365/project-service-automation). Complete your projects successfully and create profitable relationships with productive employees and intelligent tools.</span></span>
    
<span data-ttu-id="0a109-116">Sie können eine oder mehrere der oben genannten Versionen im Rahmen des Dynamics 365-Testabonnements testen.</span><span class="sxs-lookup"><span data-stu-id="0a109-116">You can explore one or more of the above for your Dynamics 365 trial subscription.</span></span>
  
![Testumgebungsanleitungen in der Microsoft Cloud](images/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
> [!TIP]
> <span data-ttu-id="0a109-118">Klicken Sie [hier](http://aka.ms/catlgstack), um eine visuelle Darstellung aller Artikel im Stapel der Testumgebungsanleitungen in der Microsoft Cloud zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="0a109-118">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a><span data-ttu-id="0a109-119">Phase 1: Erstellen einer einfachen oder simulierten Office 365-Unternehmensentwicklungs-/-testumgebung</span><span class="sxs-lookup"><span data-stu-id="0a109-119">Phase 1: Build out your lightweight or simulated enterprise Office 365 dev/test environment</span></span>

<span data-ttu-id="0a109-120">Wenn Sie Office 365 und Dynamics 365 auf einfache Weise mit den Mindestanforderungen testen möchten, befolgen Sie die Anweisungen in Phasen 2 und 3 von [Office 365 Dev/Test Environment](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="0a109-120">If you just want to test Office 365 and Dynamics 365 in a lightweight way with the minimum requirements, follow the instructions in phases 2 and 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="0a109-121">Wenn Sie Office 365 und Dynamics 365 für eine simulierte Enterprise testen möchten, befolgen Sie die Anweisungen in [DirSync für Ihre Office 365 Dev/Test-Umgebung](dirsync-for-your-office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="0a109-121">If you want to test Office 365 and Dynamics 365 for a simulated enterprise, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="0a109-p106">Für die Konfiguration in diesem Artikel ist keine simulierte Unternehmensentwicklungs-/-testumgebung erforderlich, die ein simuliertes Intranet, das mit dem Internet verbunden ist, und die Verzeichnissynchronisierung für eine Windows Server Active Directory-Gesamtstruktur umfasst. Dies wird hier als Option bereitgestellt, damit Sie mit Office 365 und Dynamics 365 in einer Umgebung, die eine typische Organisation darstellt, experimentieren können.</span><span class="sxs-lookup"><span data-stu-id="0a109-p106">The configuration in this article does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for a Windows Server AD forest. It is provided here as an option so that you can experiment with Office 365 and Dynamics 365 in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-add-a-dynamics-365-trial-subscription"></a><span data-ttu-id="0a109-124">Phase 2: Hinzufügen eines Dynamics 365-Testabonnements</span><span class="sxs-lookup"><span data-stu-id="0a109-124">Phase 2: Add a Dynamics 365 trial subscription</span></span>

<span data-ttu-id="0a109-125">In dieser Phase registrieren Sie sich für das Dynamics 365-Testabonnement und fügen es derselben Organisation wie Ihr Office 365-Testabonnement hinzu.</span><span class="sxs-lookup"><span data-stu-id="0a109-125">In this phase, you sign up for the Dynamics 365 trial subscription and add it to the same organization as your Office 365 trial subscription.</span></span>
  
### <a name="sign-up-for-a-dynamics-365-trial-subscription"></a><span data-ttu-id="0a109-126">Registrieren für ein Dynamics 365-Testabonnement</span><span class="sxs-lookup"><span data-stu-id="0a109-126">Sign up for a Dynamics 365 trial subscription</span></span>

1. <span data-ttu-id="0a109-127">Mit einem Browser auf einem Ihrer Desktopcomputer (Lightweight) oder von CLIENT1 (simuliert Enterprise), melden Sie sich bei Office 365-Portal unter [https://portal.office.com](https://portal.office.com) mit den Anmeldeinformationen Ihres Kontos globaler Administrator.</span><span class="sxs-lookup"><span data-stu-id="0a109-127">Using a browser on either your desktop computer (lightweight) or from CLIENT1 (simulated enterprise), sign in to the Office 365 portal at [https://portal.office.com](https://portal.office.com) with the credentials of your global administrator account.</span></span>
    
2. <span data-ttu-id="0a109-128">Klicken Sie auf die Kachel **Admin**.</span><span class="sxs-lookup"><span data-stu-id="0a109-128">Click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="0a109-129">Klicken Sie auf der Registerkarte **Office-Verwaltungskonsole** im linken Navigationsbereich auf **Abrechnung > Dienste erwerben**.</span><span class="sxs-lookup"><span data-stu-id="0a109-129">On the **Office admin center** tab, in the left navigation, click **Billing > Purchase services**.</span></span>
    
4. <span data-ttu-id="0a109-p107">Suchen Sie auf der Seite **Dienste erwerben** des **Dynamics 365 planen 1 Enterprise Edition** -Elements. Bewegen Sie den Mauszeiger über dieses, und klicken Sie auf **Start kostenlose Testversion**.</span><span class="sxs-lookup"><span data-stu-id="0a109-p107">On the **Purchase services** page, find the **Dynamics 365 Plan 1 Enterprise Edition** item. Hover your mouse pointer over it and click **Start free trial**.</span></span>
    
5. <span data-ttu-id="0a109-132">Klicken Sie auf der Seite für die **Bestätigung Ihrer Bestellung** auf **Jetzt versuchen**.</span><span class="sxs-lookup"><span data-stu-id="0a109-132">On the **Confirm your order** page, click **Try now**.</span></span>
    
6. <span data-ttu-id="0a109-133">Klicken Sie auf der Seite **Bestellbestätigung** auf **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="0a109-133">On the **Order receipt** page, click **Continue**.</span></span>
    
> [!NOTE]
> <span data-ttu-id="0a109-p108">Das Testabonnement für Dynamics 365 Plan 1 Enterprise Edition läuft über 30 Tage. Sie können das Testabonnement einfach um weitere 30 Tage verlängern. Für eine dauerhafte Entwicklungs-/Testumgebung erstellen Sie ein neues bezahltes Abonnement mit einer kleinen Anzahl von Lizenzen.</span><span class="sxs-lookup"><span data-stu-id="0a109-p108">The Dynamics 365 Plan 1 Enterprise Edition trial subscription is 30 days. You can easily extend the trail subscription for another 30 days. For a permanent dev/test environment, create a new paid subscription with a small number of licenses.</span></span> 
  
## <a name="phase-3-assign-dynamics-365-licenses-and-system-administrators"></a><span data-ttu-id="0a109-137">Phase 3: Zuweisen von Dynamics 365-Lizenzen und Systemadministratoren</span><span class="sxs-lookup"><span data-stu-id="0a109-137">Phase 3: Assign Dynamics 365 licenses and system administrators</span></span>

<span data-ttu-id="0a109-138">In dieser Phase weisen den Konten des globalen Administrators, von Benutzer 2 und Benutzer 3 Dynamics 365-Lizenzen hinzu und machen diese zu Systemadministratoren.</span><span class="sxs-lookup"><span data-stu-id="0a109-138">In this phase, you assign Dynamics 365 licenses to the global administrator, User 2, and User 3 accounts and make them system administrators.</span></span>
  
<span data-ttu-id="0a109-139">Gehen Sie folgendermaßen vor, um Dynamics-365-Lizenzen zuzuweisen.</span><span class="sxs-lookup"><span data-stu-id="0a109-139">Use these steps to assign Dynamics 365 licenses.</span></span>
  
1. <span data-ttu-id="0a109-140">Klicken Sie auf die Registerkarte **Office Administrationscenter** auf **Benutzer > aktive Benutzer**.</span><span class="sxs-lookup"><span data-stu-id="0a109-140">On the **Office admin center** tab, click **Users > Active users**.</span></span>
    
2. <span data-ttu-id="0a109-141">Klicken Sie in der Liste der aktiven Benutzer auf die globale Administratorkonto ein, und klicken Sie dann auf **Bearbeiten** , für die **Lizenzen**.</span><span class="sxs-lookup"><span data-stu-id="0a109-141">In the list of active users, click your global administrator account, and then click **Edit** for **Product licenses**.</span></span>
    
3. <span data-ttu-id="0a109-142">Klicken Sie im Bereich **Lizenzen** deaktivieren Sie die-Lizenz für **Dynamics 365 planen 1 Enterprise Edition** können Sie **auf**, klicken Sie auf **Speichern,** und klicken Sie dann zweimal auf **Schließen** .</span><span class="sxs-lookup"><span data-stu-id="0a109-142">On the **Product licenses** pane, turn the product license for **Dynamics 365 Plan 1 Enterprise Edition** to **On**, click **Save,** and then click **Close** twice.</span></span>
    
4. <span data-ttu-id="0a109-143">Führen Sie die Schritte 2 und 3 für Benutzer 2- und Benutzer 3-Konten durch.</span><span class="sxs-lookup"><span data-stu-id="0a109-143">Perform steps 2 and 3 for the User 2 and User 3 accounts.</span></span>
    
5. <span data-ttu-id="0a109-144">Schließen Sie die Registerkarte **Office-Verwaltungskonsole** .</span><span class="sxs-lookup"><span data-stu-id="0a109-144">Close the **Office admin center** tab.</span></span>
    
<span data-ttu-id="0a109-145">Konfigurieren Sie anhand dieser Schritte die Benutzer 2- und Benutzer 3-Konten als Dynamics 365-Systemadministratoren.</span><span class="sxs-lookup"><span data-stu-id="0a109-145">Use these steps to configure the User 2 and User 3 accounts as Dynamics 365 system administrators.</span></span>
  
1. <span data-ttu-id="0a109-146">Klicken Sie auf der Registerkarte **Microsoft Office Home** auf **Admin**.</span><span class="sxs-lookup"><span data-stu-id="0a109-146">From the **Microsoft Office Home** tab, click **Admin**.</span></span>
    
2. <span data-ttu-id="0a109-147">Klicken Sie auf der Registerkarte **Office-Verwaltungskonsole** im linken Navigationsbereich auf **Admin centers**, und klicken Sie dann auf **Dynamics 365**.</span><span class="sxs-lookup"><span data-stu-id="0a109-147">On the **Office Admin center** tab, in the left navigation, click **Admin centers**, and then click **Dynamics 365**.</span></span>
    
    <span data-ttu-id="0a109-148">Möglicherweise müssen Sie warten, bis die Bereitstellung von Dynamics 365 abgeschlossen ist, damit Dynamics 365 im Menü angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="0a109-148">You may need to wait for Dynamics 365 to finish provisioning before Dynamics 365 appears in the menu.</span></span>
    
3. <span data-ttu-id="0a109-149">Klicken Sie auf der Registerkarte Dynamics 365 klicken Sie auf **Alle diese**, und klicken Sie dann auf **Setup abzuschließen.**</span><span class="sxs-lookup"><span data-stu-id="0a109-149">On the Dynamics 365 tab, click **All of these**, and then click **Complete Setup.**</span></span>
    
    <span data-ttu-id="0a109-150">Warten Sie, bis die Einrichtung abgeschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="0a109-150">Wait for setup to complete.</span></span>
    
    <span data-ttu-id="0a109-p109">Wenn Setup abgeschlossen ist, wird ein Sales Aktivität Dashboard basierend auf Beispieldaten, die Teil des Abonnements im Überwachungsprotokoll ist. Nehmen Sie einen Moment, zum Anzeigen der **Willkommen bei der Testversion** video. Schließen Sie das Videofenster nach Abschluss des Vorgangs.</span><span class="sxs-lookup"><span data-stu-id="0a109-p109">When setup completes, it displays a Sales Activity Dashboard based on sample data that is part of the trail subscription. Take a few moments to view the **Welcome to your trial** video. Close the video window when complete.</span></span>
    
4. <span data-ttu-id="0a109-154">Klicken Sie auf der Symbolleiste oben klicken Sie auf den Pfeil nach unten neben **Sales**, klicken Sie auf **Einstellungen**, und klicken Sie dann auf **Sicherheit**.</span><span class="sxs-lookup"><span data-stu-id="0a109-154">On the toolbar at the top, click the down arrow next to **Sales**, click **Settings**, and then click **Security**.</span></span>
    
5. <span data-ttu-id="0a109-155">Klicken Sie auf der Seite **Sicherheit** auf **Benutzer**.</span><span class="sxs-lookup"><span data-stu-id="0a109-155">On the **Security** page, click **Users**.</span></span>
    
6. <span data-ttu-id="0a109-156">Klicken Sie in der Liste der Benutzer auf **Benutzer 2**.</span><span class="sxs-lookup"><span data-stu-id="0a109-156">In the list of users, click **User 2**.</span></span>
    
7. <span data-ttu-id="0a109-157">Klicken Sie auf der Symbolleiste auf **Rollen verwalten**.</span><span class="sxs-lookup"><span data-stu-id="0a109-157">In the tool bar, click **Manage Roles**.</span></span>
    
8. <span data-ttu-id="0a109-158">Klicken Sie auf **Systemadministrator** **Rollen verwalten**und klicken Sie dann auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="0a109-158">In **Manage Roles**, click **System Administrator**, and then click **OK**.</span></span>
    
9. <span data-ttu-id="0a109-159">Klicken Sie auf der Symbolleiste oben auf **Sicherheit**.</span><span class="sxs-lookup"><span data-stu-id="0a109-159">In the tool bar at the top click **Security**.</span></span>
    
10. <span data-ttu-id="0a109-160">Wiederholen Sie die Schritte 5 bis 8 für das Konto „Benutzer 3“.</span><span class="sxs-lookup"><span data-stu-id="0a109-160">Repeat steps 5-8 for the User 3 account.</span></span>
    
11. <span data-ttu-id="0a109-161">Schließen der **Benutzer: User3** Registerkarte.</span><span class="sxs-lookup"><span data-stu-id="0a109-161">Close the **User: User3** tab.</span></span>
    
> [!NOTE]
> <span data-ttu-id="0a109-162">Ihrem globalen Office 365-Administratorkonto wurde automatisch die Rolle des Dynamics 365-Systemadministrators zugewiesen.</span><span class="sxs-lookup"><span data-stu-id="0a109-162">Your Office 365 global administrator account was automatically assigned the Dynamics 365 system administrator role.</span></span> 
  
<span data-ttu-id="0a109-163">Ihre Office 365- und Dynamics 365-Entwicklungs-/Testumgebung umfasst nun Folgendes:</span><span class="sxs-lookup"><span data-stu-id="0a109-163">Your Office 365 and Dynamics 365 dev/test environment now has:</span></span>
  
- <span data-ttu-id="0a109-164">Office 365 E5 Enterprise- und Dynamics 365-Testabonnements mit derselben Organisation und demselben Azure AD-Mandanten mit Ihrer Liste von Benutzerkonten.</span><span class="sxs-lookup"><span data-stu-id="0a109-164">Office 365 E5 Enterprise and Dynamics 365 trial subscriptions sharing the same organization and the same Azure AD tenant with your list of user accounts.</span></span>
    
- <span data-ttu-id="0a109-165">Das globale Administratorkonto für Ihr Unternehmen sowie die Konten „Benutzer 2“ und „Benutzer 3“ sind so konfiguriert, dass sie sowohl Office 365 E5 Enterprise als auch Dynamics 365 verwenden dürfen. Sie alle sind zudem Dynamics 365-Systemadministratoren.</span><span class="sxs-lookup"><span data-stu-id="0a109-165">Your global enterprise administrator, User 2, and User 3 accounts are enabled to use both Office 365 E5 Enterprise and Dynamics 365 and are Dynamics 365 system administrators.</span></span>
    
## <a name="next-step"></a><span data-ttu-id="0a109-166">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="0a109-166">Next step</span></span>

<span data-ttu-id="0a109-167">Konfigurieren Sie, und führen Sie dann vor, wie Office 365 und Dynamics 365 in der Exchange Online-Postfächer mit [Exchange Online-Integration für Ihre Umgebung für Office 365 und Dynamics 365](exchange-online-integration-for-your-office-365-and-dynamics-365-dev-test-enviro.md)Test-/zusammenarbeiten.</span><span class="sxs-lookup"><span data-stu-id="0a109-167">Configure and then demonstrate how Office 365 and Dynamics 365 work together in Exchange Online mailboxes with [Exchange Online integration for your Office 365 and Dynamics 365 dev/test environment](exchange-online-integration-for-your-office-365-and-dynamics-365-dev-test-enviro.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="0a109-168">Weitere Artikel</span><span class="sxs-lookup"><span data-stu-id="0a109-168">See Also</span></span>

[<span data-ttu-id="0a109-169">Testumgebungsanleitungen (TLGs) zur Cloudakzeptanz</span><span class="sxs-lookup"><span data-stu-id="0a109-169">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="0a109-170">Basiskonfiguration der Entwicklungs-/Testumgebung</span><span class="sxs-lookup"><span data-stu-id="0a109-170">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="0a109-171">Office 365-Entwicklungs-/Testumgebung</span><span class="sxs-lookup"><span data-stu-id="0a109-171">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="0a109-172">DirSync für die Office 365-Entwicklungs-/Testumgebung</span><span class="sxs-lookup"><span data-stu-id="0a109-172">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)

[<span data-ttu-id="0a109-173">Abonnement-Verwaltung für Dynamics 365 (online)</span><span class="sxs-lookup"><span data-stu-id="0a109-173">Subscription Management for Dynamics 365 (online)</span></span>](https://technet.microsoft.com/library/jj679903.aspx)
  
[<span data-ttu-id="0a109-174">Verwalten von Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="0a109-174">Administering Dynamics 365</span></span>](https://technet.microsoft.com/library/dn531101.aspx)


