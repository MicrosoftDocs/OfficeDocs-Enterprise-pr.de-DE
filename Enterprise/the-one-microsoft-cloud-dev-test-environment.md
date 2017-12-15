---
title: Die One Microsoft Cloud-Entwicklungs-/Testumgebung
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Top
ms.custom:
- DecEntMigration
- Strat_O365_Enterprise
- Ent_TLGs
ms.assetid: a1370fe4-2fd6-4fea-ad1d-3555433d6d2e
description: "Zusammenfassung: Mithilfe dieser Test Lab Guide eine Test-/Umgebung erstellen, die alle Cloudlösungen von Microsoft enthält."
ms.openlocfilehash: a6375c60ff6c216f34e2f78850e1afd5ed0c8c80
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2017
---
# <a name="the-one-microsoft-cloud-devtest-environment"></a><span data-ttu-id="9b481-103">Die One Microsoft Cloud-Entwicklungs-/Testumgebung</span><span class="sxs-lookup"><span data-stu-id="9b481-103">The One Microsoft Cloud dev/test environment</span></span>

 <span data-ttu-id="9b481-104">**Zusammenfassung:** Verwenden Sie diese Test Lab Guide eine Test-/Umgebung erstellen, die alle Cloudlösungen von Microsoft enthält.</span><span class="sxs-lookup"><span data-stu-id="9b481-104">**Summary:** Use this Test Lab Guide to create a dev/test environment that includes all of Microsoft's cloud offerings.</span></span>
  
<span data-ttu-id="9b481-p101">Mit den Anweisungen in diesem Artikel erstellen Sie ein simuliertes Intranet in Microsoft Azure-Infrastrukturdiensten und fügen dann Abonnements für Microsoft Office 365, Microsoft Enterprise Mobility + Security (EMS) und Microsoft Dynamics 365 hinzu. Das Ergebnis ist eine vereinfachte Organisation, die alle Microsoft-Cloudangebote gleichzeitig in einer einzigen Entwicklungs-/Testumgebung nutzt. </span><span class="sxs-lookup"><span data-stu-id="9b481-p101">With the instructions in this article, you create a simulated intranet in Microsoft Azure infrastructure services and then add Microsoft Office 365, Microsoft Enterprise Mobility + Security (EMS), and Microsoft Dynamics 365 subscriptions. The result is a simplified organization that uses all Microsoft's cloud offerings at the same time in a single dev/test environment.</span></span> 
  
![Phase 3 der One Microsoft Cloud-Entwicklungs-/Testumgebung mit Azure, Office 365, EMS und Dynamics 365](images/31714fcc-0c7d-411f-bcd1-c62d9be090ee.png)
  
<span data-ttu-id="9b481-108">Die daraus resultierende Konfiguration bietet Ihnen die folgenden Möglichkeiten:</span><span class="sxs-lookup"><span data-stu-id="9b481-108">You can use the resulting configuration to:</span></span>
  
- <span data-ttu-id="9b481-109">Erleben Sie die Integration in den Microsoft-Cloudangeboten, z. B. die gemeinsame Identitätsinfrastruktur, die von Azure Active Directory (AD) bereitgestellt wird.</span><span class="sxs-lookup"><span data-stu-id="9b481-109">Experience the integration across Microsoft's cloud offerings, such as the common identity infrastructure provided by Azure Active Directory (AD).</span></span>
    
- <span data-ttu-id="9b481-110">Werten Sie End-to-End-Szenarios aus, die mehrere Microsoft-Cloudangebote umfassen.</span><span class="sxs-lookup"><span data-stu-id="9b481-110">Evaluate end-to-end scenarios that include multiple Microsoft Cloud offerings.</span></span>
    
- <span data-ttu-id="9b481-111">Erstellen Sie eine Demo, Machbarkeitsstudie oder Entwicklungs-/Testkonfiguration, die mehrere Microsoft-Cloudangebote nutzt.</span><span class="sxs-lookup"><span data-stu-id="9b481-111">Create a demo, proof-of-concept, or dev/test configuration that uses multiple Microsoft Cloud offerings.</span></span>
    
- <span data-ttu-id="9b481-112">Bauen Sie Ihre Qualifikation in Bezug auf die Microsoft Cloud zur beruflichen Weiterentwicklung aus.</span><span class="sxs-lookup"><span data-stu-id="9b481-112">Build your Microsoft Cloud skills for professional development.</span></span>
    
## <a name="phase-1-create-a-simulated-intranet-and-add-office-365"></a><span data-ttu-id="9b481-113">Phase 1: Erstellen eines simulierten Intranets und Hinzufügen von Office 365</span><span class="sxs-lookup"><span data-stu-id="9b481-113">Phase 1: Create a simulated intranet and add Office 365</span></span>

<span data-ttu-id="9b481-114">Befolgen Sie die Anweisungen in [DirSync für Ihre Office 365 Dev/Test-Umgebung](dirsync-for-your-office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="9b481-114">Follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="9b481-115">Abbildung 1 zeigt die resultierende Konfiguration, einschließlich Office 365 und einem simulierten Intranet in Azure Infrastructure Services und verzeichnissynchronisierung aus einer lokalen Windows Server Active Directory (AD)-Gesamtstruktur ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="9b481-115">Figure 1 shows your resulting configuration, which includes Office 365 and a simulated intranet running in Azure infrastructure services and directory synchronization from an on-premises Windows Server Active Directory (AD) forest.</span></span>
  
<span data-ttu-id="9b481-116">**Abbildung 1: Die simulierten Intranet in Azure mit Office 365**</span><span class="sxs-lookup"><span data-stu-id="9b481-116">**Figure 1: The simulated intranet in Azure with Office 365**</span></span>

![Die Office 365-Entwicklungs-/Testumgebung mit DirSync](images/be5b37b0-f832-4878-b153-436c31546e21.png)
  
> [!NOTE]
> <span data-ttu-id="9b481-p102">Die Azure-Testversion beträgt 30 Tage. Das Abonnement E5 Testversion von Office 365 Enterprise ist 30 Tagen auf einfache Weise für weitere 30 Tage verlängert werden können. Erstellen Sie für eine permanente Test-/-Umgebung ein neues bezahlt Azure-Abonnement und ein neues kostenpflichtigen Office 365 Enterprise E5 Abonnement mit einer kleinen Anzahl von Lizenzen.</span><span class="sxs-lookup"><span data-stu-id="9b481-p102">The Azure trial is 30 days. The Office 365 Enterprise E5 Trial subscription is 30 days, which can be easily extended for another 30 days. For a permanent dev/test environment, create a new paid Azure subscription and a new paid Office 365 Enterprise E5 subscription with a small number of licenses.</span></span> 
  
## <a name="phase-2-add-ems"></a><span data-ttu-id="9b481-121">Phase 2: Hinzufügen von EMS</span><span class="sxs-lookup"><span data-stu-id="9b481-121">Phase 2: Add EMS</span></span>

<span data-ttu-id="9b481-122">In dieser Phase registrieren Sie sich für das EMS-Testabonnement und fügen es derselben Organisation wie Ihr Office 365-Testabonnement hinzu.</span><span class="sxs-lookup"><span data-stu-id="9b481-122">In this phase, you sign up for the EMS trial subscription and add it to the same organization as your Office 365 trial subscription.</span></span>
  
1. <span data-ttu-id="9b481-123">Mit einem Browser auf einem Desktopcomputer oder von CLIENT1, melden Sie sich bei Office 365-Portal unter [https://portal.office.com](https://portal.office.com) mit den Anmeldeinformationen Ihres Kontos globaler Administrator.</span><span class="sxs-lookup"><span data-stu-id="9b481-123">With a browser on either your desktop computer or from CLIENT1, sign in to the Office 365 portal at [https://portal.office.com](https://portal.office.com) with the credentials of your global administrator account.</span></span>
    
2. <span data-ttu-id="9b481-124">Klicken Sie auf die Kachel **Admin**.</span><span class="sxs-lookup"><span data-stu-id="9b481-124">Click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="9b481-125">Klicken Sie auf der Registerkarte **Office Admin Center** in Ihrem Browser im linken Navigationsbereich auf **Abrechnung > Dienste kaufen**.</span><span class="sxs-lookup"><span data-stu-id="9b481-125">On the **Office Admin center** tab in your browser, in the left navigation, click **Billing > Purchase services**.</span></span>
    
4. <span data-ttu-id="9b481-p103">Suchen Sie auf der Seite **Dienste kaufen** den Artikel **Enterprise Mobility + Security E5**. Platzieren Sie den Mauszeiger auf dem Artikelnamen, und klicken Sie auf **Start free trial**.</span><span class="sxs-lookup"><span data-stu-id="9b481-p103">On the **Purchase services** page, find the **Enterprise Mobility + Security E5** item. Hover your mouse pointer over it and click **Start free trial**.</span></span>
    
5. <span data-ttu-id="9b481-128">Klicken Sie auf der Seite für die **Bestätigung Ihrer Bestellung** auf **Jetzt versuchen**.</span><span class="sxs-lookup"><span data-stu-id="9b481-128">On the **Confirm your order** page, click **Try now**.</span></span>
    
6. <span data-ttu-id="9b481-129">Klicken Sie auf der Seite **Bestellbestätigung** auf **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="9b481-129">On the **Order receipt** page, click **Continue**.</span></span>
    
> [!NOTE]
> <span data-ttu-id="9b481-p104">Das Testabonnement für Enterprise Mobility + Security E5 ist 90 Tage gültig. Für eine dauerhafte Entwicklungs-/Testumgebung erstellen Sie ein neues bezahltes Abonnement mit einer kleinen Anzahl von Lizenzen.</span><span class="sxs-lookup"><span data-stu-id="9b481-p104">The Enterprise Mobility + Security E5 trial subscription is 90 days. For a permanent dev/test environment, create a new paid subscription with a small number of licenses.</span></span> 
  
<span data-ttu-id="9b481-132">Als Nächstes aktivieren Sie die Enterprise Mobility + Security E5-Lizenz für alle Benutzerkonten.</span><span class="sxs-lookup"><span data-stu-id="9b481-132">Next, enable the Enterprise Mobility + Security E5 license for all user accounts.</span></span>
  
1. <span data-ttu-id="9b481-133">Klicken Sie auf der Registerkarte **Office 365 Admin Center** in Ihrem Browser im linken Navigationsbereich auf **Benutzer > Aktive Benutzer**.</span><span class="sxs-lookup"><span data-stu-id="9b481-133">On the **Office 365 Admin center** tab in your browser, in the left navigation, click **Users > Active users**.</span></span>
    
2. <span data-ttu-id="9b481-134">Klicken Sie auf Ihr globales Administratorkonto und dann auf **Bearbeiten**, um die **Produktlizenzen** anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="9b481-134">Click your global administrator account, and then click **Edit** for **Product licenses**.</span></span>
    
3. <span data-ttu-id="9b481-135">Setzen Sie im Bereich **Product licenses** die Produktlizenz für **Enterprise Mobility + Security E5** auf **On**. Klicken Sie auf **Speichern** und dann auf **Schließen**.</span><span class="sxs-lookup"><span data-stu-id="9b481-135">On the **Product licenses** pane, turn the product license for **Enterprise Mobility + Security E5** to **On**, click **Save,** and then click **Close** twice.</span></span>
    
4. <span data-ttu-id="9b481-136">Führen Sie die Schritte 2 und 3 für alle Ihre anderen Konten aus (Benutzer1, Benutzer 2, Benutzer 3, Benutzer 4 und Benutzer 5).</span><span class="sxs-lookup"><span data-stu-id="9b481-136">For all of your other accounts (User1, User 2, User 3, User 4, and User 5), do steps 2 and 3.</span></span>
    
<span data-ttu-id="9b481-137">Ihre Entwicklungs-/Testumgebung verfügt nun über Folgendes:</span><span class="sxs-lookup"><span data-stu-id="9b481-137">Your dev/test environment now has:</span></span>
  
- <span data-ttu-id="9b481-138">Ein simuliertes Intranet, das in Azure-Infrastrukturdiensten ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="9b481-138">A simulated intranet running in Azure infrastructure services.</span></span>
    
- <span data-ttu-id="9b481-139">Office 365 E5 Enterprise- und EMS-Testabonnements mit derselben Organisation und demselben Azure AD-Mandanten mit Ihrer Liste von Benutzerkonten.</span><span class="sxs-lookup"><span data-stu-id="9b481-139">Office 365 E5 Enterprise and EMS trial subscriptions sharing the same organization and the same Azure AD tenant with your list of user accounts.</span></span>
    
- <span data-ttu-id="9b481-140">Alle Ihre Benutzerkonten, aktiviert für die Verwendung von Office 365 E5 Enterprise und EMS.</span><span class="sxs-lookup"><span data-stu-id="9b481-140">All of your user accounts enabled to use Office 365 E5 Enterprise and EMS.</span></span>
    
<span data-ttu-id="9b481-141">Abbildung 2 zeigt die resultierende Konfiguration nach dem Hinzufügen von EMS.</span><span class="sxs-lookup"><span data-stu-id="9b481-141">Figure 2 shows your resulting configuration, which adds EMS.</span></span>
  
<span data-ttu-id="9b481-142">**Abbildung 2: Die simulierten Intranet in Azure mit Office 365 und zur Abstimmung**</span><span class="sxs-lookup"><span data-stu-id="9b481-142">**Figure 2: The simulated intranet in Azure with Office 365 and EMS**</span></span>

![Phase 2 der One Microsoft Cloud-Entwicklungs-/Testumgebung mit Azure, Office 365 und EMS](images/fdb520fe-ebbd-4681-a80e-b60df52f07c5.png)
  
## <a name="phase-3-add-dynamics-365"></a><span data-ttu-id="9b481-144">Phase 3: Hinzufügen des Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="9b481-144">Phase 3: Add Dynamics 365</span></span>

<span data-ttu-id="9b481-145">In dieser Phase registrieren Sie sich für das Dynamics 365-Testabonnement und fügen es derselben Organisation wie Ihre Office 365- und EMS-Testabonnements hinzu.</span><span class="sxs-lookup"><span data-stu-id="9b481-145">In this phase, you sign up for the Dynamics 365 trial subscription and add it to the same organization as your Office 365 and EMS trial subscriptions.</span></span>
  
1. <span data-ttu-id="9b481-146">Mithilfe eines Browsers auf einem Desktopcomputer oder von CLIENT1, melden Sie sich bei Office 365-Portal unter [https://portal.office.com](https://portal.office.com) mit den Anmeldeinformationen Ihres Kontos globaler Administrator.</span><span class="sxs-lookup"><span data-stu-id="9b481-146">Using a browser on either your desktop computer or from CLIENT1, sign in to the Office 365 portal at [https://portal.office.com](https://portal.office.com) with the credentials of your global administrator account.</span></span>
    
2. <span data-ttu-id="9b481-147">Klicken Sie auf die Kachel **Admin**.</span><span class="sxs-lookup"><span data-stu-id="9b481-147">Click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="9b481-148">Klicken Sie auf der Registerkarte **Office-Verwaltungskonsole** im linken Navigationsbereich auf **Abrechnung > Dienste erwerben**.</span><span class="sxs-lookup"><span data-stu-id="9b481-148">On the **Office admin center** tab, in the left navigation, click **Billing > Purchase services**.</span></span>
    
4. <span data-ttu-id="9b481-p105">Suchen Sie auf der Seite **Dienste erwerben** des **Dynamics 365 planen 1 Enterprise Edition** -Elements. Bewegen Sie den Mauszeiger über dieses, und klicken Sie auf **Start kostenlose Testversion**.</span><span class="sxs-lookup"><span data-stu-id="9b481-p105">On the **Purchase services** page, find the **Dynamics 365 Plan 1 Enterprise Edition** item. Hover your mouse pointer over it and click **Start free trial**.</span></span>
    
5. <span data-ttu-id="9b481-151">Klicken Sie auf der Seite für die **Bestätigung Ihrer Bestellung** auf **Jetzt versuchen**.</span><span class="sxs-lookup"><span data-stu-id="9b481-151">On the **Confirm your order** page, click **Try now**.</span></span>
    
6. <span data-ttu-id="9b481-152">Klicken Sie auf der Seite **Bestellbestätigung** auf **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="9b481-152">On the **Order receipt** page, click **Continue**.</span></span>
    
> [!NOTE]
> <span data-ttu-id="9b481-p106">Das Testabonnement für Dynamics 365 Plan 1 Enterprise Edition läuft über 30 Tage. Sie können das Testabonnement einfach um weitere 30 Tage verlängern. Für eine dauerhafte Entwicklungs-/Testumgebung erstellen Sie ein neues bezahltes Abonnement mit einer kleinen Anzahl von Lizenzen.</span><span class="sxs-lookup"><span data-stu-id="9b481-p106">The Dynamics 365 Plan 1 Enterprise Edition trial subscription is 30 days. You can easily extend the trail subscription for another 30 days. For a permanent dev/test environment, create a new paid subscription with a small number of licenses.</span></span> 
  
<span data-ttu-id="9b481-156">Führen Sie diese Schritte aus, um den Konten des globalen Administrators sowie den Konten von Benutzer 2 und Benutzer 3 Dynamics 365-Lizenzen zuzuweisen und sie zu Systemadministratoren zu machen.</span><span class="sxs-lookup"><span data-stu-id="9b481-156">Use these steps to assign Dynamics 365 licenses to the global administrator, User 2, and User 3 accounts and make them system administrators.</span></span>
  
1. <span data-ttu-id="9b481-157">Klicken Sie auf die Registerkarte **Office Administrationscenter** auf **Benutzer > aktive Benutzer**.</span><span class="sxs-lookup"><span data-stu-id="9b481-157">On the **Office admin center** tab, click **Users > Active users**.</span></span>
    
2. <span data-ttu-id="9b481-158">Klicken Sie in der Liste der aktiven Benutzer auf die globale Administratorkonto ein, und klicken Sie dann auf **Bearbeiten** , für die **Lizenzen**.</span><span class="sxs-lookup"><span data-stu-id="9b481-158">In the list of active users, click your global administrator account, and then click **Edit** for **Product licenses**.</span></span>
    
3. <span data-ttu-id="9b481-159">Klicken Sie im Bereich **Lizenzen** deaktivieren Sie die-Lizenz für **Dynamics 365 planen 1 Enterprise Edition** können Sie **auf**, klicken Sie auf **Speichern,** und klicken Sie dann zweimal auf **Schließen** .</span><span class="sxs-lookup"><span data-stu-id="9b481-159">On the **Product licenses** pane, turn the product license for **Dynamics 365 Plan 1 Enterprise Edition** to **On**, click **Save,** and then click **Close** twice.</span></span>
    
4. <span data-ttu-id="9b481-160">Führen Sie die Schritte 2 und 3 für Benutzer 2- und Benutzer 3-Konten durch.</span><span class="sxs-lookup"><span data-stu-id="9b481-160">Perform steps 2 and 3 for the User 2 and User 3 accounts.</span></span>
    
5. <span data-ttu-id="9b481-161">Schließen Sie die Registerkarte **Office-Verwaltungskonsole** .</span><span class="sxs-lookup"><span data-stu-id="9b481-161">Close the **Office admin center** tab.</span></span>
    
<span data-ttu-id="9b481-162">Konfigurieren Sie anhand dieser Schritte die Benutzer 2- und Benutzer 3-Konten als Dynamics 365-Systemadministratoren.</span><span class="sxs-lookup"><span data-stu-id="9b481-162">Use these steps to configure the User 2 and User 3 accounts as Dynamics 365 system administrators.</span></span>
  
1. <span data-ttu-id="9b481-163">Klicken Sie auf der Registerkarte **Office Admin Center** in Ihrem Browser im linken Navigationsbereich klicken Sie auf **Admin centers**, und klicken Sie dann auf **Dynamics 365**.</span><span class="sxs-lookup"><span data-stu-id="9b481-163">On the **Office Admin center** tab in your browser, in the left navigation, click **Admin centers**, and then click **Dynamics 365**.</span></span>
    
    <span data-ttu-id="9b481-164">Möglicherweise müssen Sie warten, bis die Bereitstellung von Dynamics 365 abgeschlossen ist, damit Dynamics 365 im Menü angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="9b481-164">You may need to wait for Dynamics 365 to finish provisioning before Dynamics 365 appears in the menu.</span></span>
    
2. <span data-ttu-id="9b481-165">Klicken Sie auf der Registerkarte Dynamics 365 klicken Sie auf **Alle diese**, und klicken Sie dann auf **Setup abzuschließen.**</span><span class="sxs-lookup"><span data-stu-id="9b481-165">On the Dynamics 365 tab, click **All of these**, and then click **Complete Setup.**</span></span>
    
    <span data-ttu-id="9b481-166">Warten Sie, bis die Einrichtung abgeschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="9b481-166">Wait for setup to complete.</span></span>
    
    <span data-ttu-id="9b481-p107">Wenn Setup abgeschlossen ist, wird ein Sales Aktivität Dashboard basierend auf Beispieldaten, die Teil des Abonnements im Überwachungsprotokoll ist. Nehmen Sie einen Moment, zum Anzeigen der **Willkommen bei der Testversion** video. Schließen Sie das Videofenster nach Abschluss des Vorgangs.</span><span class="sxs-lookup"><span data-stu-id="9b481-p107">When setup completes, it displays a Sales Activity Dashboard based on sample data that is part of the trail subscription. Take a few moments to view the **Welcome to your trial** video. Close the video window when complete.</span></span>
    
3. <span data-ttu-id="9b481-170">Klicken Sie auf der Symbolleiste oben klicken Sie auf den Pfeil nach unten neben **Sales**, klicken Sie auf **Einstellungen**, und klicken Sie dann auf **Sicherheit**.</span><span class="sxs-lookup"><span data-stu-id="9b481-170">On the toolbar at the top, click the down arrow next to **Sales**, click **Settings**, and then click **Security**.</span></span>
    
4. <span data-ttu-id="9b481-171">Klicken Sie auf der Seite **Sicherheit** auf **Benutzer**.</span><span class="sxs-lookup"><span data-stu-id="9b481-171">On the **Security** page, click **Users**.</span></span>
    
5. <span data-ttu-id="9b481-172">Klicken Sie in der Liste der Benutzer auf **Benutzer 2**.</span><span class="sxs-lookup"><span data-stu-id="9b481-172">In the list of users, click **User 2**.</span></span>
    
6. <span data-ttu-id="9b481-173">Klicken Sie auf der Symbolleiste auf **Rollen verwalten**.</span><span class="sxs-lookup"><span data-stu-id="9b481-173">In the tool bar, click **Manage Roles**.</span></span>
    
7. <span data-ttu-id="9b481-174">Klicken Sie auf **Systemadministrator** **Rollen verwalten**und klicken Sie dann auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="9b481-174">In **Manage Roles**, click **System Administrator**, and then click **OK**.</span></span>
    
8. <span data-ttu-id="9b481-175">Klicken Sie auf der Symbolleiste oben auf **Sicherheit**.</span><span class="sxs-lookup"><span data-stu-id="9b481-175">In the tool bar at the top click **Security**.</span></span>
    
9. <span data-ttu-id="9b481-176">Wiederholen Sie die Schritte 5 bis 8 für das Konto „Benutzer 3“.</span><span class="sxs-lookup"><span data-stu-id="9b481-176">Repeat steps 5-8 for the User 3 account.</span></span>
    
10. <span data-ttu-id="9b481-177">Schließen der **Benutzer: User3** Registerkarte.</span><span class="sxs-lookup"><span data-stu-id="9b481-177">Close the **User: User3** tab.</span></span>
    
> [!NOTE]
> <span data-ttu-id="9b481-178">Ihrem globalen Office 365-Administratorkonto wurde automatisch die Rolle des Dynamics 365-Systemadministrators zugewiesen.</span><span class="sxs-lookup"><span data-stu-id="9b481-178">Your Office 365 global administrator account was automatically assigned the Dynamics 365 system administrator role.</span></span> 
  
<span data-ttu-id="9b481-179">Ihre Entwicklungs-/Testumgebung verfügt nun über Folgendes:</span><span class="sxs-lookup"><span data-stu-id="9b481-179">Your dev/test environment now has:</span></span>
  
- <span data-ttu-id="9b481-180">Ein simuliertes Intranet, das in Azure-Infrastrukturdiensten ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="9b481-180">A simulated intranet running in Azure infrastructure services.</span></span>
    
- <span data-ttu-id="9b481-181">Office 365 E5 Enterprise-, EMS- und Dynamics 365-Testabonnements mit derselben Organisation und demselben Azure AD-Mandanten wie Ihre Liste von Benutzerkonten.</span><span class="sxs-lookup"><span data-stu-id="9b481-181">Office 365 E5 Enterprise, EMS, and Dynamics 365 trial subscriptions sharing the same organization and the same Azure AD tenant with your list of user accounts.</span></span>
    
- <span data-ttu-id="9b481-182">Alle Ihre Benutzerkonten, aktiviert für die Verwendung von Office 365 E5 Enterprise und EMS.</span><span class="sxs-lookup"><span data-stu-id="9b481-182">All of your user accounts enabled to use Office 365 E5 Enterprise and EMS.</span></span>
    
- <span data-ttu-id="9b481-183">Die Konten des globalen Unternehmensadministrators und der Benutzer 2 und Benutzer 3 dürfen Dynamics 365 verwenden und sind Dynamics 365-Systemadministratoren.</span><span class="sxs-lookup"><span data-stu-id="9b481-183">Your global enterprise administrator, User 2, and User 3 accounts are enabled to use Dynamics 365 and are Dynamics 365 system administrators.</span></span>
    
<span data-ttu-id="9b481-184">Abbildung 3 zeigt die resultierende Konfiguration.</span><span class="sxs-lookup"><span data-stu-id="9b481-184">Figure 3 shows your resulting configuration.</span></span>
  
<span data-ttu-id="9b481-185">**Abbildung 3: Simulierten Intranet in Azure mit Office 365 und zur Abstimmung Dynamics 365**</span><span class="sxs-lookup"><span data-stu-id="9b481-185">**Figure 3: The simulated intranet in Azure with Office 365, EMS, and Dynamics 365**</span></span>

![Phase 3 der One Microsoft Cloud-Entwicklungs-/Testumgebung mit Azure, Office 365, EMS und Dynamics 365](images/31714fcc-0c7d-411f-bcd1-c62d9be090ee.png)
  
## <a name="next-steps"></a><span data-ttu-id="9b481-187">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="9b481-187">Next steps</span></span>

<span data-ttu-id="9b481-p108">Sie können jetzt mit Ihrer One Microsoft Cloud-Entwicklungs-/Testumgebung experimentieren. Hier sind einige Ideen zum Ausprobieren mit Anleitung:</span><span class="sxs-lookup"><span data-stu-id="9b481-p108">You can now experiment with your One Microsoft Cloud dev/test environment. Here are some ideas for guided experiences:</span></span>
  
- [<span data-ttu-id="9b481-190">Konfigurieren von Informationsverwaltungsrichtlinien (MAM) für die mobile Anwendung in zur Abstimmung für Office 365-Anwendungen</span><span class="sxs-lookup"><span data-stu-id="9b481-190">Configure mobile application management (MAM) policies in EMS for Office 365 applications</span></span>](https://technet.microsoft.com/library/mt764059.aspx)
    
- [<span data-ttu-id="9b481-191">Führen Sie vor, Exchange Online in Office 365-Integration in Dynamics 365 Kontakte</span><span class="sxs-lookup"><span data-stu-id="9b481-191">Demonstrate Exchange Online in Office 365 integration with Dynamics 365 contacts</span></span>](https://technet.microsoft.com/library/mt798313.aspx)
    
- [<span data-ttu-id="9b481-192">Erstellen Sie ein Netzwerk simulierten standortübergreifenden in Azure Infrastructure Services für das Hosten von Server-basierten Arbeitslasten</span><span class="sxs-lookup"><span data-stu-id="9b481-192">Create a simulated cross-premises network in Azure infrastructure services for hosting server-based workloads</span></span>](https://technet.microsoft.com/library/mt745150.aspx)
    
## <a name="see-also"></a><span data-ttu-id="9b481-193">See Also</span><span class="sxs-lookup"><span data-stu-id="9b481-193">See Also</span></span>

[<span data-ttu-id="9b481-194">Testumgebungsanleitungen (TLGs) zur Cloudakzeptanz</span><span class="sxs-lookup"><span data-stu-id="9b481-194">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="9b481-195">Ressourcen zur Cloud-IT-Architektur von Microsoft</span><span class="sxs-lookup"><span data-stu-id="9b481-195">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)
  
[<span data-ttu-id="9b481-196">Hybridlösungen</span><span class="sxs-lookup"><span data-stu-id="9b481-196">Hybrid solutions</span></span>](hybrid-solutions.md)
  
[<span data-ttu-id="9b481-197">Sicherheitslösungen</span><span class="sxs-lookup"><span data-stu-id="9b481-197">Security solutions</span></span>](security-solutions.md)





