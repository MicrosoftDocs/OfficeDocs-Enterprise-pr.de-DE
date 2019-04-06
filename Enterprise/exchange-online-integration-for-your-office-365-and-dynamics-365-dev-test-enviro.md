---
title: Exchange Online-Integration für Ihre Office 365 und Dynamics 365-Entwicklungs-/Testumgebung
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
ms.custom: Ent_TLGs
ms.assetid: 499c5823-427a-4ba2-8fc1-9553bc2ff2d3
description: 'Zusammenfassung: Verwenden Sie diese Testumgebungsanleitung, um die Dynamics 365-Integration für Exchange Online für Ihr Office 365-Testabonnement zu aktivieren.'
ms.openlocfilehash: 47153f9321284d0bb30f59645dfe56ab40cb7982
ms.sourcegitcommit: 201d3338d8bbc6da9389e62e2add8a17384fab4d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/02/2019
ms.locfileid: "31037999"
---
# <a name="exchange-online-integration-for-your-office-365-and-dynamics-365-devtest-environment"></a><span data-ttu-id="89912-103">Exchange Online-Integration für Ihre Office 365 und Dynamics 365-Entwicklungs-/Testumgebung</span><span class="sxs-lookup"><span data-stu-id="89912-103">Exchange Online integration for your Office 365 and Dynamics 365 dev/test environment</span></span>

 <span data-ttu-id="89912-104">**Zusammenfassung:** Verwenden Sie diese Testumgebungsanleitung, um die Dynamics 365-Integration für Exchange Online für Ihr Office 365-Testabonnement zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="89912-104">**Summary:** Use this Test Lab Guide to enable Dynamics 365 integration for Exchange Online in your Office 365 trial subscription.</span></span>
  
<span data-ttu-id="89912-p101">Ein nützlicher Vorteil von Microsoft Dynamics 365 besteht darin, dass die gesamte Kundenkommunikation an einem zentralen Ort gespeichert wird, damit jeder Benutzer mit den entsprechenden Berechtigungen auf alle relevanten Kundendatensätze zugreifen kann. Sie können beispielsweise alle E-Mail-Nachrichten anzeigen, die mit einem bestimmten Kontakt, einem Konto, einer Verkaufschance oder einem Falls verknüpft sind.</span><span class="sxs-lookup"><span data-stu-id="89912-p101">A valuable use of Microsoft Dynamics 365 is to store all customer communications in one place, so anyone with the appropriate permissions can see all relevant customer records. For example, view all email associated with a particular contact, account, opportunity, or case.</span></span>
  
<span data-ttu-id="89912-p102">Um E-Mail-Nachrichten und andere Messagingdatensätze in Dynamics 365 zu speichern, müssen Sie das E-Mail-System mit Dynamics 365 synchronisieren. Die serverseitige Synchronisierung ist die bevorzugte Methode für die E-Mail-Synchronisierung.</span><span class="sxs-lookup"><span data-stu-id="89912-p102">To store email and other messaging records in Dynamics 365, you need to synchronize your email system with Dynamics 365. Server-side synchronization is the method of choice for email synchronization.</span></span>
  
<span data-ttu-id="89912-109">Verwenden Sie diese Testumgebungsanleitung, um Exchange Online und den Outlook Online-Client für Dynamics 365 zu konfigurieren und zu demonstrieren, wie sie die in Dynamics 356 gespeicherten Informationen nutzen können.</span><span class="sxs-lookup"><span data-stu-id="89912-109">Use this Test Lab Guide to configure and demonstrate how Exchange Online and the Outlook Online client can leverage the information stored in Dynamics 365.</span></span> 
  
## <a name="phase-1-build-out-the-office-365-and-dynamics-365-devtest-environment"></a><span data-ttu-id="89912-110">Phase 1: Erstellen der Office 365- und Dynamics 365-Entwicklungs-/Testumgebung</span><span class="sxs-lookup"><span data-stu-id="89912-110">Phase 1: Build out the Office 365 and Dynamics 365 dev/test environment</span></span>

<span data-ttu-id="89912-111">Folgen Sie den Anweisungen in der Testumgebungsanleitung [Office 365- und Dynamics 365-Entwicklungs-/Testumgebung](office-365-and-dynamics-365-dev-test-environment.md) zum Erstellen einer einfachen oder simulierten Unternehmensversion einer Office 365- und Dynamics 365-Entwicklungs-/Testumgebung.</span><span class="sxs-lookup"><span data-stu-id="89912-111">Use the instructions in [Office 365 and Dynamics 365 dev/test environment](office-365-and-dynamics-365-dev-test-environment.md) to create either a lightweight or simulated enterprise version of an Office 365 and Dynamics 365 dev/test environment.</span></span>
  
> [!NOTE]
> <span data-ttu-id="89912-112">Die Konfiguration in diesem Artikel erfordert nicht die simulierte Enterprise-dev/Test-Umgebung, die ein simuliertes Intranet mit dem Internet und die Verzeichnissynchronisierung für eine Active Directory-Domänendienste (AD DS)-Gesamtstruktur enthält.</span><span class="sxs-lookup"><span data-stu-id="89912-112">The configuration in this article does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for an Active Directory Domain Services (AD DS) forest.</span></span> <span data-ttu-id="89912-113">Dies wird hier als Option bereitgestellt, damit Sie mit Office 365 und Dynamics 365 in einer Umgebung, die eine typische Organisation darstellt, experimentieren können.</span><span class="sxs-lookup"><span data-stu-id="89912-113">It is provided here as an option so that you can experiment with Office 365 and Dynamics 365 in an environment that represents a typical organization</span></span> 
  
## <a name="phase-2-configure-and-demonstrate-dynamics-365-integration-in-exchange-online"></a><span data-ttu-id="89912-114">Phase 2: Konfigurieren und Demonstrieren der Exchange Online-Integration in Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="89912-114">Phase 2: Configure and demonstrate Dynamics 365 integration in Exchange Online</span></span>

<span data-ttu-id="89912-115">Gehen Sie wie folgt vor, um das Postfach des globalen Administrators für die Integration von Dynamics 365 und Exchange Online zu konfigurieren:</span><span class="sxs-lookup"><span data-stu-id="89912-115">Use these steps to configure the global administrator's mailbox for Dynamics 365 and Exchange Online integration:</span></span>
  
1. <span data-ttu-id="89912-116">Navigieren Sie in einer privaten Sitzung Ihres Browsers zu und [http://admin.microsoft.com](http://admin.microsoft.com) melden Sie sich mit ihrem globalen Office 365-Administratorkonto an.</span><span class="sxs-lookup"><span data-stu-id="89912-116">Using a private session of your browser, go to [http://admin.microsoft.com](http://admin.microsoft.com) and sign in using your Office 365 global administrator account.</span></span>
    
2. <span data-ttu-id="89912-117">Klicken Sie auf der **Microsoft Office-Homepage** auf die Kachel **E-Mail**.</span><span class="sxs-lookup"><span data-stu-id="89912-117">On the **Microsoft Office Home** page, click the **Mail** tile.</span></span>
    
3. <span data-ttu-id="89912-118">Klicken Sie auf der Registerkarte neue **e-Mail** in Ihrem Browser auf **neu** , und beachten Sie, dass die untere Ecke des Bereichs unterhalb des Felds zum Eingeben einer Nachricht ein Symbol für meine Vorlagen aufweist.</span><span class="sxs-lookup"><span data-stu-id="89912-118">On the new **Mail** tab in your browser, click **New** and notice how the bottom corner of the pane below the box for typing a message has an icon for My Templates.</span></span>
    
     ![Leere neue E-Mail-Nachricht ohne Integration mit Dynamics 365](media/879b54fd-a68f-4581-9f89-d5050df6f4de.png)
  
4. <span data-ttu-id="89912-120">Klicken Sie auf **verwerfen**, und lassen Sie die Registerkarte **E-Mail** geöffnet.</span><span class="sxs-lookup"><span data-stu-id="89912-120">Click **Discard** and leave the **Mail** tab open.</span></span>
    
5. <span data-ttu-id="89912-121">Klicken Sie auf die Registerkarte **Microsoft Office Home** in Ihrem Browser, und klicken Sie dann auf die Kachel **Admin**.</span><span class="sxs-lookup"><span data-stu-id="89912-121">Click the **Microsoft Office Home** tab in your browser, and then click the **Admin** tile.</span></span>
    
6. <span data-ttu-id="89912-122">Klicken Sie im linken Navigationsbereich der Registerkarte **Office Admin Center** auf **Admin Center > Dynamics 365**.</span><span class="sxs-lookup"><span data-stu-id="89912-122">In the left navigation of the **Office Admin center** tab, click **Admin centers > Dynamics 365**.</span></span>
    
7. <span data-ttu-id="89912-123">Klicken Sie auf der neuen Registerkarte **Dynamics 365** in Ihrem Browser in der Liste mit den Dynamics 365-Instanzen auf **Öffnen**.</span><span class="sxs-lookup"><span data-stu-id="89912-123">On the new **Dynamics 365** tab in your browser, in the list of Dynamics 365 instances, click **Open**.</span></span>
    
8. <span data-ttu-id="89912-124">Klicken Sie auf der neuen Registerkarte **Administration** in Ihrem Browser auf der Navigationsleiste auf den Abwärtspfeil neben **Einstellungen**, und klicken Sie dann auf **E-Mail-Konfiguration** unter **System**.</span><span class="sxs-lookup"><span data-stu-id="89912-124">On the new **Administration** tab in your browser, on the navigation bar, click the down arrow next to **Settings**, and then click **Email Configuration** under **System**.</span></span>
    
9.  <span data-ttu-id="89912-125">Klicken Sie auf der Seite **E-Mail-Konfiguration** auf **E-Mail-Konfigurationseinstellungen**.</span><span class="sxs-lookup"><span data-stu-id="89912-125">On the **Email Configuration** page, click **Email Configuration Settings**.</span></span>
    
10. <span data-ttu-id="89912-126">Ändern Sie auf der Registerkarte **E-Mail** im Dialogfeld **Systemeinstellungen** die Option **Termine, Kontakte und Aufgaben** in **Serverseitige Synchronisierung**, und klicken Sie dann auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="89912-126">In the **Email** tab on the **System Settings** dialog box, change **Appointments, Contacts, and Tasks** to **Server-Side Synchronization**, and then click **OK**.</span></span>
    
11. <span data-ttu-id="89912-127">Klicken Sie auf der Seite **E-Mail-Konfiguration** auf **Postfächer**.</span><span class="sxs-lookup"><span data-stu-id="89912-127">On the **Email Configuration** page, click **Mailboxes**.</span></span>
    
12. <span data-ttu-id="89912-128">Wählen Sie den Namen des globalen Administrator für Office 365 in der linken Spalte aus, klicken Sie in der Symbolleiste auf **Standard-E-Mail-Einstellungen anwenden**, und klicken Sie dann auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="89912-128">Select the Office 365 global administrator name in the left check mark column, click **Apply Default Email Settings** in the tool bar, and then click **OK**.</span></span>
    
13. <span data-ttu-id="89912-129">Klicken Sie in der Symbolleiste auf **E-Mail genehmigen**, und klicken Sie dann auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="89912-129">Click **Approve Email** in the tool bar, and then click **OK**.</span></span>
    
14. <span data-ttu-id="89912-130">Wählen Sie den Namen des globalen Administrator für Office 365 in der linken Spalte aus, klicken Sie in der Symbolleiste auf **Postfächer testen&amp; und aktivieren**, und klicken Sie dann auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="89912-130">Select the Office 365 global administrator name in the left check mark column, click **Test &amp; Enable Mailboxes** in the tool bar, and then click **OK**.</span></span>
    
15. <span data-ttu-id="89912-131">Klicken Sie auf die geöffnete Registerkarte **E-Mail**, und überprüfen Sie, ob der globale Administrator eine Testnachricht erhalten hat.</span><span class="sxs-lookup"><span data-stu-id="89912-131">Click the open **Mail** tab and confirm that the global administrator received a test message.</span></span>
    
16. <span data-ttu-id="89912-p104">Wechseln Sie im Browser zurück zur Registerkarte **Postfächer > Meine aktiven Postfächer**, und aktualisieren Sie die Seite. Die Spalten **Status eingehender E-Mails** und **Status ausgehender E-Mails** müssen für den Namen des globalen Administrators auf **Erfolgt** festgelegt sein. Beachten Sie, dass es bis zu 15 Minuten dauern kann, bis beide Tests durchgeführt sind.</span><span class="sxs-lookup"><span data-stu-id="89912-p104">Return to the **Mailboxes My Active Mailboxes** tab in your browser and refresh the page. The **Incoming Email Status** and **Outgoing Email Status** columns should be set to **Success** for the global administrator account name. Note that it can take up to 15 minutes to complete both tests.</span></span>
    
<span data-ttu-id="89912-135">Gehen Sie wie folgt vor, um die Dynamics 365-App für Outlook zu installieren und die Funktionen von Dynamics 365 im Postfach des globalen Administrators zu demonstrieren:</span><span class="sxs-lookup"><span data-stu-id="89912-135">Use these steps to install the Dynamics 365 App for Outlook and demonstrate Dynamics 365 features within the global administrator's mailbox:</span></span>
  
1. <span data-ttu-id="89912-136">Klicken Sie in Ihrem Browser auf der Registerkarte **Postfächer > Meine aktiven Postfächer** auf den Abwärtspfeil neben **Einstellungen**, und klicken Sie dann auf **Dynamics 365-App für Outlook** unter **System**.</span><span class="sxs-lookup"><span data-stu-id="89912-136">On the **Mailboxes My Active Mailboxes** tab in your browser, click the down arrow next to **Settings**, and then click **Dynamics 365 App for Outlook** under **System**.</span></span>
    
2. <span data-ttu-id="89912-p105">Klicken Sie auf der Seite **Erste Schritte mit der Microsoft Dynamics 365-App für Outlook** auf den Namen des globalen Administrators, und klicken Sie dann auf **App zu Outlook hinzufügen**. Die Spalte **Status** ändert sich in **Ausstehend**.</span><span class="sxs-lookup"><span data-stu-id="89912-p105">On the **Getting Started with Microsoft Dynamics 365 App for Outlook** page, click the global administrator name, and then click **Add App to Outlook**. The **Status** column changes to **Pending**.</span></span>
    
3. <span data-ttu-id="89912-p106">Aktualisieren Sie die Seite, bis der Status sich in **Zu Outlook hinzugefügt** geändert hat. Beachten Sie, dass es bis zu 15 Minuten dauern kann, bis diese Konfiguration durchgeführt ist.</span><span class="sxs-lookup"><span data-stu-id="89912-p106">Refresh the page until the status changes to **Added to Outlook**. Note that it can take up to 15 minutes to complete this configuration.</span></span>
    
4. <span data-ttu-id="89912-141">Klicken Sie im Browser auf die Registerkarte **E-Mail**, und schließen Sie den Browser dann.</span><span class="sxs-lookup"><span data-stu-id="89912-141">Click on the **Mail** tab in your browser and then close it.</span></span>
    
5. <span data-ttu-id="89912-142">Klicken Sie auf die Registerkarte **Microsoft Office Home** in Ihrem Browser, und klicken Sie dann auf die Kachel **E-Mail**.</span><span class="sxs-lookup"><span data-stu-id="89912-142">Click the **Microsoft Office Home** tab in your browser, and then click the **Mail** tile.</span></span>
    
6. <span data-ttu-id="89912-143">Klicken Sie auf der neuen Registerkarte **E-Mail** im Browser auf **Neu**.</span><span class="sxs-lookup"><span data-stu-id="89912-143">On the new **Mail** tab in your browser, click **New**.</span></span> <span data-ttu-id="89912-144">Beachten Sie, dass die untere Ecke des Bereichs unterhalb des Felds zum Eingeben einer Nachricht jetzt ein Symbol für Dynamics 365 hat.</span><span class="sxs-lookup"><span data-stu-id="89912-144">Notice that the bottom corner of the pane below the box for typing a message now has an icon for Dynamics 365.</span></span>
    
     ![Leere neue E-Mail-Nachricht bei Integration mit Dynamics 365 (neues Symbol sichtbar)](media/ecb822e1-45fe-4481-99a1-294317d1d2de.png)
  
7. <span data-ttu-id="89912-p108">Klicken Sie auf das Symbol für Dynamics 365. Es sollte ein **Dynamics 365**-Fenster angezeigt werden, in dem Sie diese E-Mail verfolgen oder auf Vorlagen, Vertriebsdokumentation oder Artikel zugreifen können.</span><span class="sxs-lookup"><span data-stu-id="89912-p108">Click the Dynamics 365 icon. You should see a **Dynamics 365** pane, from which you can track this email or access templates, sales literature, or articles.</span></span>
    
8. <span data-ttu-id="89912-p109">Geben Sie im Feld **An** der E-Mail-Nachricht **alex.y.wu@outlook.com** ein, und klicken Sie dann auf **Wiederholen** im Fenster **Dynamics 365**. Es sollte der Abschnitt **Empfänger** im Fenster **Dynamics 365** mit Informationen über Alex Wu angezeigt werden, der ein Kontakt in der Vertriebsanwendung ist, die in den Beispieldaten für das Testabonnement enthalten ist.</span><span class="sxs-lookup"><span data-stu-id="89912-p109">In the **To** field of the email message, type **alex.y.wu@outlook.com**, and then click **Retry** in the **Dynamics 365** pane. You should see a **Recipients** section in the **Dynamics 365** pane with information on Alex Wu, a contact from the sales application that was provided with the sample data for your trial subscription.</span></span>
    
     ![Dynamics 365-Informationsbereich für einen in Dynamics 365 gespeicherten Vertriebskontakt](media/a010fa5f-3f1b-47d4-ab5e-d00d85a24a3f.png)
  
9. <span data-ttu-id="89912-151">Klicken Sie auf **Verwerfen**.</span><span class="sxs-lookup"><span data-stu-id="89912-151">Click **Discard**.</span></span>

> [!TIP]
> <span data-ttu-id="89912-152">Klicken Sie [hier](http://aka.ms/catlgstack), um eine visuelle Darstellung aller Artikel im Stapel der Testumgebungsanleitungen in der Microsoft Cloud zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="89912-152">Click [here](http://aka.ms/catlgstack) for a visual map to all of the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="89912-153">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="89912-153">See Also</span></span>

[<span data-ttu-id="89912-154">Office 365- und Dynamics 365-Entwicklungs-/Testumgebung</span><span class="sxs-lookup"><span data-stu-id="89912-154">Office 365 and Dynamics 365 dev/test environment</span></span>](office-365-and-dynamics-365-dev-test-environment.md)
  
[<span data-ttu-id="89912-155">Testumgebungsanleitungen (TLGs) zur Cloudakzeptanz</span><span class="sxs-lookup"><span data-stu-id="89912-155">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="89912-156">Basiskonfiguration der Entwicklungs-/Testumgebung</span><span class="sxs-lookup"><span data-stu-id="89912-156">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="89912-157">Office 365-Entwicklungs-/Testumgebung</span><span class="sxs-lookup"><span data-stu-id="89912-157">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="89912-158">DirSync für die Office 365-Entwicklungs-/Testumgebung</span><span class="sxs-lookup"><span data-stu-id="89912-158">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)

[<span data-ttu-id="89912-159">Abonnement-Verwaltung für Dynamics 365 (online)</span><span class="sxs-lookup"><span data-stu-id="89912-159">Subscription Management for Dynamics 365 (online)</span></span>](https://technet.microsoft.com/library/jj679903.aspx)
  
[<span data-ttu-id="89912-160">Verwalten von Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="89912-160">Administering Dynamics 365</span></span>](https://technet.microsoft.com/library/dn531101.aspx)


