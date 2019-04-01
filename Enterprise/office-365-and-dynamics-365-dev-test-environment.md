---
title: Office 365- und Dynamics 365-Entwicklungs-/Testumgebung
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/18/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Ent_TLGs
ms.assetid: 098c1a1d-83a1-40eb-bbc9-47de7af8bb23
description: 'Zusammenfassung: Verwenden Sie dieses Testlaborhandbuch, um Ihrer Office 365-Entwicklungs-/Testumgebung Dynamics 365 hinzuzufügen.'
ms.openlocfilehash: 9e4c98129c68ab5d2f0d9fc486ab62740c625af5
ms.sourcegitcommit: 4ef8e113fa20b539de1087422455fc26ff123d55
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "30574059"
---
# <a name="office-365-and-dynamics-365-devtest-environment"></a><span data-ttu-id="91bdc-103">Office 365- und Dynamics 365-Entwicklungs-/Testumgebung</span><span class="sxs-lookup"><span data-stu-id="91bdc-103">Office 365 and Dynamics 365 dev/test environment</span></span>

 <span data-ttu-id="91bdc-104">**Zusammenfassung:** Verwenden Sie dieses Testlaborhandbuch, um Ihrer Office 365-Entwicklungs-/Testumgebung Dynamics 365 hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="91bdc-104">**Summary:** Use this Test Lab Guide to add Dynamics 365 to your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="91bdc-105">Mit den Anweisungen in diesem Artikel fügen Sie der Organisation Ihrer Office 365-Entwicklungs-/Testumgebung ein Dynamics 365-Testabonnement hinzu und erstellen so eine Office 365- und Dynamics 365-Entwicklungs-/Testumgebung.</span><span class="sxs-lookup"><span data-stu-id="91bdc-105">With the instructions in this article, you add a Dynamics 365 trial subscription to the same organization as your Office 365 dev/test environment, creating an Office 365 and Dynamics 365 dev/test environment.</span></span>

![Office 365- und Dynamics 365-Entwicklungs-/Testumgebung](media/o365-dynamics365-dev-test.png)
  
  
<span data-ttu-id="91bdc-p101">Sie können ein Dynamics 365-Testabonnement verwenden, um die Funktionen von Dynamics 365 zu demonstrieren. Die folgenden Lösungen sind in einer Dynamics 365 Plan 1, Enterprise Edition-Testversion enthalten:</span><span class="sxs-lookup"><span data-stu-id="91bdc-p101">You can use a Dynamics 365 trial subscription to demonstrate features and capabilities of Dynamics 365. The following solutions are included with a Dynamics 365 Plan 1, Enterprise Edition trial:</span></span>
  
- <span data-ttu-id="91bdc-p102">[Microsoft Dynamics 365 for Sales](https://www.microsoft.com/dynamics365/sales). Steigern Sie Ihre Umsätze mit Automatisierung und digitaler Business Intelligence für eine fokussierte und smarte Arbeitsweise Ihrer Vertriebsmitarbeiter.</span><span class="sxs-lookup"><span data-stu-id="91bdc-p102">[Microsoft Dynamics 365 for Sales](https://www.microsoft.com/dynamics365/sales). Increase your sales with automation and digital intelligence helping your salespeople stay focused and work smarter.</span></span>
    
- <span data-ttu-id="91bdc-p103">[Microsoft Dynamics 365 for Customer Service](https://www.microsoft.com/dynamics365/customer-service). Gewinnen Sie Langzeitkunden, indem Sie Ihren Mitarbeitern die Informationen und digitale Business Intelligence für erstklassigen Service bieten.</span><span class="sxs-lookup"><span data-stu-id="91bdc-p103">[Microsoft Dynamics 365 for Customer Service](https://www.microsoft.com/dynamics365/customer-service). Earn loyalty by giving your agents the complete information and digital intelligence they need to provide seamless service.</span></span>
    
- <span data-ttu-id="91bdc-p104">[Microsoft Dynamics 365 for Field Service](https://www.microsoft.com/dynamics365/field-service). Optimieren Sie Ihre Zeitplanung, um Servicefälle zu meistern, und nutzen Sie Vorhersagetools, um den Gewinn zu steigern.</span><span class="sxs-lookup"><span data-stu-id="91bdc-p104">[Microsoft Dynamics 365 for Field Service](https://www.microsoft.com/dynamics365/field-service). Master the service call by optimizing your schedules, equipping your workforce, and using predictive tools to increase profit.</span></span>
    
- <span data-ttu-id="91bdc-p105">[Microsoft Dynamics 365 for Project Service Automation](https://www.microsoft.com/de-DE/dynamics365/project-service-automation). Schließen Sie Ihre Projekte erfolgreich ab und schaffen Sie profitable Kundenbeziehungen dank produktiver Mitarbeiter und intelligenter Tools.</span><span class="sxs-lookup"><span data-stu-id="91bdc-p105">[Microsoft Dynamics 365 for Project Service Automation](https://www.microsoft.com/de-DE/dynamics365/project-service-automation). Complete your projects successfully and create profitable relationships with productive employees and intelligent tools.</span></span>
    
<span data-ttu-id="91bdc-117">Sie können eine oder mehrere der oben genannten Versionen im Rahmen des Dynamics 365-Testabonnements testen.</span><span class="sxs-lookup"><span data-stu-id="91bdc-117">You can explore one or more of the above for your Dynamics 365 trial subscription.</span></span>
  
![Testumgebungsanleitungen in der Microsoft Cloud](media/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
> [!TIP]
> <span data-ttu-id="91bdc-119">Klicken Sie [hier](http://aka.ms/catlgstack), um eine visuelle Darstellung aller Artikel im Stapel der Testumgebungsanleitungen in der One Microsoft Cloud zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="91bdc-119">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a><span data-ttu-id="91bdc-120">Phase 1: Erstellen einer einfachen oder simulierten Office 365-Unternehmensentwicklungs-/-testumgebung</span><span class="sxs-lookup"><span data-stu-id="91bdc-120">Phase 1: Build out your lightweight or simulated enterprise Office 365 dev/test environment</span></span>

<span data-ttu-id="91bdc-121">Wenn Sie Office 365 und Dynamics 365 nur auf einfache Weise mit den Mindestanforderungen testen möchten, befolgen Sie die Anweisungen in den Phasen 2 und 3 von [Office 365-Entwicklungs-/Testumgebung](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="91bdc-121">If you just want to test Office 365 and Dynamics 365 in a lightweight way with the minimum requirements, follow the instructions in phases 2 and 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="91bdc-122">Wenn Sie Office 365 und Dynamics 365 für ein simuliertes Unternehmen testen möchten, befolgen Sie die Anweisungen in [DirSync to Your Office 365 Dev/Test Environment](dirsync-for-your-office-365-dev-test-environment.md) (Verzeichnissynchronisierung mit Ihrer Office 365-Entwicklungs-/Testumgebung).</span><span class="sxs-lookup"><span data-stu-id="91bdc-122">If you want to test Office 365 and Dynamics 365 for a simulated enterprise, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>

![Die Office 365-Entwicklungs-/Testumgebung](media/48fb91aa-09b0-4020-a496-a8253920c45d.png)
  
> [!NOTE]
> <span data-ttu-id="91bdc-p106">Für die Konfiguration in diesem Artikel ist keine simulierte Unternehmensentwicklungs-/-testumgebung erforderlich, die ein simuliertes Intranet, das mit dem Internet verbunden ist, und die Verzeichnissynchronisierung für eine Windows Server Active Directory-Gesamtstruktur umfasst. Dies wird hier als Option bereitgestellt, damit Sie mit Office 365 und Dynamics 365 in einer Umgebung, die eine typische Organisation darstellt, experimentieren können.</span><span class="sxs-lookup"><span data-stu-id="91bdc-p106">The configuration in this article does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for a Windows Server AD forest. It is provided here as an option so that you can experiment with Office 365 and Dynamics 365 in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-add-a-dynamics-365-trial-subscription"></a><span data-ttu-id="91bdc-126">Phase 2: Hinzufügen eines Dynamics 365-Testabonnements</span><span class="sxs-lookup"><span data-stu-id="91bdc-126">Phase 2: Add a Dynamics 365 trial subscription</span></span>

<span data-ttu-id="91bdc-127">In dieser Phase registrieren Sie sich für das Dynamics 365-Testabonnement und fügen es derselben Organisation wie Ihr Office 365-Testabonnement hinzu.</span><span class="sxs-lookup"><span data-stu-id="91bdc-127">In this phase, you sign up for the Dynamics 365 trial subscription and add it to the same organization as your Office 365 trial subscription.</span></span>
  
### <a name="sign-up-for-a-dynamics-365-trial-subscription"></a><span data-ttu-id="91bdc-128">Registrieren für ein Dynamics 365-Testabonnement</span><span class="sxs-lookup"><span data-stu-id="91bdc-128">Sign up for a Dynamics 365 trial subscription</span></span>

1. <span data-ttu-id="91bdc-129">Melden Sie sich über einen Browser auf Ihrem Desktopcomputer (einfach) oder von CLIENT1 aus beim Microsoft 365 Admin Center (simuliertes Unternehmen) unter [https://admin.microsoft.com](https://admin.microsoft.com) an. Verwenden Sie die Anmeldeinformationen Ihres globalen Administratorkontos.</span><span class="sxs-lookup"><span data-stu-id="91bdc-129">Using a browser on either your desktop computer (lightweight) or from CLIENT1 (simulated enterprise), sign in to the Office 365 portal at [https://admin.microsoft.com](https://admin.microsoft.com) with the credentials of your global administrator account.</span></span>
    
2. <span data-ttu-id="91bdc-130">Klicken Sie auf die Kachel **Admin**.</span><span class="sxs-lookup"><span data-stu-id="91bdc-130">Click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="91bdc-131">Klicken Sie auf der Registerkarte **Microsoft 365 Admin Center** im linken Navigationsbereich auf **Abrechnung > Dienste kaufen**.</span><span class="sxs-lookup"><span data-stu-id="91bdc-131">On the **Microsoft 365 admin center** tab, in the left navigation, click **Billing > Purchase services**.</span></span>
    
4. <span data-ttu-id="91bdc-p107">Suchen Sie auf der Seite **Dienste kaufen** den Artikel **Dynamics 365 Plan 1 Enterprise Edition**. Platzieren Sie den Mauszeiger auf dem Artikelnamen, und klicken Sie auf **Start free trial**.</span><span class="sxs-lookup"><span data-stu-id="91bdc-p107">On the **Purchase services** page, find the **Dynamics 365 Plan 1 Enterprise Edition** item. Hover your mouse pointer over it and click **Start free trial**.</span></span>
    
5. <span data-ttu-id="91bdc-134">Klicken Sie auf der Seite für die **Bestätigung Ihrer Bestellung** auf **Jetzt versuchen**.</span><span class="sxs-lookup"><span data-stu-id="91bdc-134">On the **Confirm your order** page, click **Try now**.</span></span>
    
6. <span data-ttu-id="91bdc-135">Klicken Sie auf der Seite **Bestellbestätigung** auf **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="91bdc-135">On the **Order receipt** page, click **Continue**.</span></span>

![Office 365- und Dynamics 365-Entwicklungs-/Testumgebung](media/o365-dynamics365-dev-test.png)
    
> [!NOTE]
> <span data-ttu-id="91bdc-p108">Das Testabonnement für Dynamics 365 Plan 1 Enterprise Edition läuft über 30 Tage. Sie können das Testabonnement einfach um weitere 30 Tage verlängern. Für eine dauerhafte Entwicklungs-/Testumgebung erstellen Sie ein neues bezahltes Abonnement mit einer kleinen Anzahl von Lizenzen.</span><span class="sxs-lookup"><span data-stu-id="91bdc-p108">The Dynamics 365 Plan 1 Enterprise Edition trial subscription is 30 days. You can easily extend the trail subscription for another 30 days. For a permanent dev/test environment, create a new paid subscription with a small number of licenses.</span></span> 
  
## <a name="phase-3-assign-dynamics-365-licenses-and-system-administrators"></a><span data-ttu-id="91bdc-140">Phase 3: Zuweisen von Dynamics 365-Lizenzen und Systemadministratoren</span><span class="sxs-lookup"><span data-stu-id="91bdc-140">Phase 3: Assign Dynamics 365 licenses and system administrators</span></span>

<span data-ttu-id="91bdc-141">In dieser Phase weisen den Konten des globalen Administrators, von Benutzer 2 und Benutzer 3 Dynamics 365-Lizenzen hinzu und machen diese zu Systemadministratoren.</span><span class="sxs-lookup"><span data-stu-id="91bdc-141">In this phase, you assign Dynamics 365 licenses to the global administrator, User 2, and User 3 accounts and make them system administrators.</span></span>
  
<span data-ttu-id="91bdc-142">Gehen Sie folgendermaßen vor, um Dynamics-365-Lizenzen zuzuweisen.</span><span class="sxs-lookup"><span data-stu-id="91bdc-142">Use these steps to assign Dynamics 365 licenses.</span></span>
  
1. <span data-ttu-id="91bdc-143">Klicken Sie auf der Registerkarte **Microsoft 365 Admin Center** auf **Benutzer > Aktive Benutzer**.</span><span class="sxs-lookup"><span data-stu-id="91bdc-143">On the **Microsoft 365 admin center** tab, click **Users > Active users**.</span></span>
    
2. <span data-ttu-id="91bdc-144">Klicken Sie in der Liste der aktiven Benutzer auf Ihr globales Administratorkonto, und klicken Sie dann auf **Bearbeiten** für **Produktlizenzen**.</span><span class="sxs-lookup"><span data-stu-id="91bdc-144">In the list of active users, click your global administrator account, and then click **Edit** for **Product licenses**.</span></span>
    
3. <span data-ttu-id="91bdc-145">	Setzen Sie im Bereich *\*Product licenses** die Produktlizenz für *\*Dynamics 365 Plan 1 Enterprise Edition** auf *\*On*\*. Klicken Sie auf *\*Speichern** und anschließend zweimal auf *\*Schließen*\*.</span><span class="sxs-lookup"><span data-stu-id="91bdc-145">On the **Product licenses** pane, turn the product license for **Dynamics 365 Plan 1 Enterprise Edition** to **On**, click **Save,** and then click **Close** twice.</span></span>
    
4. <span data-ttu-id="91bdc-146">Führen Sie die Schritte 2 und 3 für Benutzer 2- und Benutzer 3-Konten durch.</span><span class="sxs-lookup"><span data-stu-id="91bdc-146">Perform steps 2 and 3 for the User 2 and User 3 accounts.</span></span>
    
5. <span data-ttu-id="91bdc-147">Schließen Sie die Registerkarte **Microsoft 365 Admin Center**.</span><span class="sxs-lookup"><span data-stu-id="91bdc-147">Close the **Microsoft 365 admin center** tab.</span></span>
    
<span data-ttu-id="91bdc-148">Konfigurieren Sie anhand dieser Schritte die Benutzer 2- und Benutzer 3-Konten als Dynamics 365-Systemadministratoren.</span><span class="sxs-lookup"><span data-stu-id="91bdc-148">Use these steps to configure the User 2 and User 3 accounts as Dynamics 365 system administrators.</span></span>
  
1. <span data-ttu-id="91bdc-149">Klicken Sie auf der Registerkarte der **Microsoft Office-Startseite** auf **Admin**.</span><span class="sxs-lookup"><span data-stu-id="91bdc-149">From the **Microsoft Office Home** tab, click **Admin**.</span></span>
    
2. <span data-ttu-id="91bdc-150">Klicken Sie auf der Registerkarte **Office Admin Center** im linken Navigationsbereich auf **Admin Center** und dann auf **Dynamics 365**.</span><span class="sxs-lookup"><span data-stu-id="91bdc-150">On the **Office Admin center** tab, in the left navigation, click **Admin centers**, and then click **Dynamics 365**.</span></span>
    
    <span data-ttu-id="91bdc-151">Möglicherweise müssen Sie warten, bis die Bereitstellung von Dynamics 365 abgeschlossen ist, damit Dynamics 365 im Menü angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="91bdc-151">You may need to wait for Dynamics 365 to finish provisioning before Dynamics 365 appears in the menu.</span></span>
    
3. <span data-ttu-id="91bdc-152">Klicken Sie auf der Registerkarte „Dynamics 365“ auf **Alle** und dann auf **Einrichtung abschließen**.</span><span class="sxs-lookup"><span data-stu-id="91bdc-152">On the Dynamics 365 tab, click **All of these**, and then click **Complete Setup.**</span></span>
    
    <span data-ttu-id="91bdc-153">Warten Sie, bis die Einrichtung abgeschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="91bdc-153">Wait for setup to complete.</span></span>
    
    <span data-ttu-id="91bdc-p109">Sobald die Einrichtung abgeschlossen ist, wird ein Vertriebsaktivitäts-Dashboard mit Beispieldaten angezeigt, die zum Testabonnement gehören. Nehmen Sie sich kurz Zeit, um sich das **Willkommensvideo** anzusehen. Schließen Sie das Videofenster, sobald das Video zu Ende ist.</span><span class="sxs-lookup"><span data-stu-id="91bdc-p109">When setup completes, it displays a Sales Activity Dashboard based on sample data that is part of the trail subscription. Take a few moments to view the **Welcome to your trial** video. Close the video window when complete.</span></span>
    
4. <span data-ttu-id="91bdc-157">Klicken Sie auf der Symbolleiste oben auf den Nach-unten-Pfeil neben **Vertrieb**. Klicken Sie auf **Einstellungen** und dann auf **Sicherheit**.</span><span class="sxs-lookup"><span data-stu-id="91bdc-157">On the toolbar at the top, click the down arrow next to **Sales**, click **Settings**, and then click **Security**.</span></span>
    
5. <span data-ttu-id="91bdc-158">Klicken Sie auf der Seite **Sicherheit** auf **Benutzer**.</span><span class="sxs-lookup"><span data-stu-id="91bdc-158">On the **Security** page, click **Users**.</span></span>
    
6. <span data-ttu-id="91bdc-159">Klicken Sie in der Benutzerliste auf **Benutzer 2**.</span><span class="sxs-lookup"><span data-stu-id="91bdc-159">In the list of users, click **User 2**.</span></span>
    
7. <span data-ttu-id="91bdc-160">Klicken Sie in der Symbolleiste auf **Rollen verwalten**.</span><span class="sxs-lookup"><span data-stu-id="91bdc-160">In the tool bar, click **Manage Roles**.</span></span>
    
8. <span data-ttu-id="91bdc-161">Klicken Sie unter **Rollen verwalten** auf **Systemadministrator** und dann auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="91bdc-161">In **Manage Roles**, click **System Administrator**, and then click **OK**.</span></span>
    
9. <span data-ttu-id="91bdc-162">Klicken Sie auf der Symbolleisten oben auf **Sicherheit**.</span><span class="sxs-lookup"><span data-stu-id="91bdc-162">In the tool bar at the top click **Security**.</span></span>
    
10. <span data-ttu-id="91bdc-163">Wiederholen Sie die Schritte 5 bis 8 für das Konto „Benutzer 3“.</span><span class="sxs-lookup"><span data-stu-id="91bdc-163">Repeat steps 5-8 for the User 3 account.</span></span>
    
11. <span data-ttu-id="91bdc-164">Schließen Sie die Registerkarte **Benutzer: Benutzer 3**.</span><span class="sxs-lookup"><span data-stu-id="91bdc-164">Close the **User: User3** tab.</span></span>
    
> [!NOTE]
> <span data-ttu-id="91bdc-165">Ihrem globalen Office 365-Administratorkonto wurde automatisch die Rolle des Dynamics 365-Systemadministrators zugewiesen.</span><span class="sxs-lookup"><span data-stu-id="91bdc-165">Your Office 365 global administrator account was automatically assigned the Dynamics 365 system administrator role.</span></span> 
  
<span data-ttu-id="91bdc-166">Ihre Office 365- und Dynamics 365-Entwicklungs-/Testumgebung umfasst nun Folgendes:</span><span class="sxs-lookup"><span data-stu-id="91bdc-166">Your Office 365 and Dynamics 365 dev/test environment now has:</span></span>
  
- <span data-ttu-id="91bdc-167">Office 365 E5 Enterprise- und Dynamics 365-Testabonnements mit derselben Organisation und demselben Azure AD-Mandanten mit Ihrer Liste von Benutzerkonten.</span><span class="sxs-lookup"><span data-stu-id="91bdc-167">Office 365 E5 Enterprise and Dynamics 365 trial subscriptions sharing the same organization and the same Azure AD tenant with your list of user accounts.</span></span>
    
- <span data-ttu-id="91bdc-168">Das globale Administratorkonto für Ihr Unternehmen sowie die Konten „Benutzer 2“ und „Benutzer 3“ sind so konfiguriert, dass sie sowohl Office 365 E5 Enterprise als auch Dynamics 365 verwenden dürfen. Sie alle sind zudem Dynamics 365-Systemadministratoren.</span><span class="sxs-lookup"><span data-stu-id="91bdc-168">Your global enterprise administrator, User 2, and User 3 accounts are enabled to use both Office 365 E5 Enterprise and Dynamics 365 and are Dynamics 365 system administrators.</span></span>
    
## <a name="next-step"></a><span data-ttu-id="91bdc-169">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="91bdc-169">Next step</span></span>

<span data-ttu-id="91bdc-170">Nehmen Sie die Konfiguration vor, und demonstrieren Sie dann, wie Office 365 und Dynamics 365 mit [Exchange Online integration for your Office 365 and Dynamics 365 dev/test environment](exchange-online-integration-for-your-office-365-and-dynamics-365-dev-test-enviro.md) (Exchange Online-Integration für Ihre Office 365- und Dynamics 365-Entwicklungs-/Testumgebung) in Exchange Online-Postfächern zusammenarbeiten.</span><span class="sxs-lookup"><span data-stu-id="91bdc-170">Configure and then demonstrate how Office 365 and Dynamics 365 work together in Exchange Online mailboxes with [Exchange Online integration for your Office 365 and Dynamics 365 dev/test environment](exchange-online-integration-for-your-office-365-and-dynamics-365-dev-test-enviro.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="91bdc-171">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="91bdc-171">See Also</span></span>

[<span data-ttu-id="91bdc-172">Testumgebungsanleitungen (TLGs) zur Cloudakzeptanz</span><span class="sxs-lookup"><span data-stu-id="91bdc-172">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="91bdc-173">Basiskonfiguration der Entwicklungs-/Testumgebung</span><span class="sxs-lookup"><span data-stu-id="91bdc-173">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="91bdc-174">Office 365-Entwicklungs-/Testumgebung</span><span class="sxs-lookup"><span data-stu-id="91bdc-174">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="91bdc-175">DirSync für die Office 365-Entwicklungs-/Testumgebung</span><span class="sxs-lookup"><span data-stu-id="91bdc-175">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)

[<span data-ttu-id="91bdc-176">Abonnement-Verwaltung für Dynamics 365 (online)</span><span class="sxs-lookup"><span data-stu-id="91bdc-176">Subscription Management for Dynamics 365 (online)</span></span>](https://technet.microsoft.com/library/jj679903.aspx)
  
[<span data-ttu-id="91bdc-177">Verwalten von Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="91bdc-177">Administering Dynamics 365</span></span>](https://technet.microsoft.com/library/dn531101.aspx)


