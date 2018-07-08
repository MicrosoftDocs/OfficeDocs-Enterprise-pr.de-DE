---
title: Datenklassifizierung und -kennzeichnung in Office 365-Entwicklungs-/-Testumgebungen
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
ms.assetid: 919b8fc7-b0bc-46db-91f5-37342564e01b
description: 'Zusammenfassung: Informationen zum Konfigurieren und Demonstrieren der Datenklassifizierung und -kennzeichnung mit dem Azure Information Protection-Client (AIP) in Office 365-Entwicklungs-/-Testumgebungen.'
ms.openlocfilehash: f9674f5e2bac804f5bd23b5f67e733580c50450f
ms.sourcegitcommit: c23b95d32a865e45be7843f38a1f23b5693ba76d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "20188093"
---
# <a name="data-classification-and-labeling-in-the-office-365-devtest-environment"></a><span data-ttu-id="937d0-103">Datenklassifizierung und -kennzeichnung in Office 365-Entwicklungs-/-Testumgebungen</span><span class="sxs-lookup"><span data-stu-id="937d0-103">Data classification and labeling in the Office 365 dev/test environment</span></span>

 <span data-ttu-id="937d0-104">**Zusammenfassung:** Informationen zum Konfigurieren und Demonstrieren der Datenklassifizierung und -kennzeichnung mit dem Azure Information Protection-Client (AIP) in Office 365-Entwicklungs-/-Testumgebungen.</span><span class="sxs-lookup"><span data-stu-id="937d0-104">**Summary:** Configure and demonstrate data classification and labeling using the Azure Information Protection (AIP) client in your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="937d0-p101">Der Client Azure Information Protection können Sie ein Dokument klassifizieren, bevor Sie ihn in einen Ordner SharePoint Online in Office 365 hochladen. Mit den Anweisungen in diesem Artikel installieren Sie den Client Azure Information Protection und veranschaulichen der Datenklassifikation. Weitere Informationen finden Sie unter [Azure Information Protection](https://www.microsoft.com/cloud-platform/azure-information-protection).</span><span class="sxs-lookup"><span data-stu-id="937d0-p101">The Azure Information Protection client allows you to classify a document before you upload it to a SharePoint Online folder in Office 365. With the instructions in this article, you install the Azure Information Protection client and demonstrate data classification. For more information, see [Azure Information Protection](https://www.microsoft.com/cloud-platform/azure-information-protection).</span></span>
  
> [!TIP]
> <span data-ttu-id="937d0-108">Klicken Sie [hier](http://aka.ms/catlgstack), um eine visuelle Darstellung aller Artikel im Stapel der Testumgebungsanleitungen in der Microsoft Cloud zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="937d0-108">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-build-out-your-office-365-devtest-environment"></a><span data-ttu-id="937d0-109">Phase 1: Erstellen Ihrer Office 365-Entwicklungs-/Testumgebung</span><span class="sxs-lookup"><span data-stu-id="937d0-109">Phase 1: Build out your Office 365 dev/test environment</span></span>

<span data-ttu-id="937d0-110">Folgen Sie den Anweisungen unter [Office 365 dev/test environment](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="937d0-110">Follow the instructions in [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
## <a name="phase-2-add-the-azure-information-protection-trial-subscription"></a><span data-ttu-id="937d0-111">Phase 2: Hinzufügen des Azure Information Protection-Abonnements</span><span class="sxs-lookup"><span data-stu-id="937d0-111">Phase 2: Add the Azure Information Protection trial subscription</span></span>

<span data-ttu-id="937d0-p102">In dieser Phase fügen Sie Azure Information Protection zu Ihrer Office 365-Entwicklungs-/Testumgebung und aktivieren Sie ihn für Ihre Benutzerkonten. Wenn Sie die [Office 365 and EMS dev/test environment](http://technet.microsoft.com/library/c76eea86-d4b6-4d35-ad89-341696e89ef7.aspx) konfiguriert haben, überspringen Sie diese Phase. Das Enterprise Mobility Suit-Testabonnement umfasst Azure Information Protection-Lizenzen.</span><span class="sxs-lookup"><span data-stu-id="937d0-p102">In this phase, you add Azure Information Protection to your Office 365 dev/test environment and enable it for your user accounts. If you have configured the [Office 365 and EMS dev/test environment](http://technet.microsoft.com/library/c76eea86-d4b6-4d35-ad89-341696e89ef7.aspx), skip this phase. The Enterprise Mobility Suite trial subscription includes Azure Information Protection licenses.</span></span>
  
<span data-ttu-id="937d0-115">Melden Sie sich zunächst für ein Azure Information Protection-Testabonnement an.</span><span class="sxs-lookup"><span data-stu-id="937d0-115">First, sign up for an Azure Information Protection trial subscription.</span></span>
  
### <a name="sign-up-for-an-azure-information-protection-trial-subscription"></a><span data-ttu-id="937d0-116">Anmelden für ein Azure Information Protection-Testabonnement</span><span class="sxs-lookup"><span data-stu-id="937d0-116">Sign up for an Azure Information Protection trial subscription</span></span>

1. <span data-ttu-id="937d0-117">Wechseln Sie in Internet Explorer oder Ihren Browser zu [http://portal.office.com](http://portal.office.com) und melden Sie sich mit Ihrem Office 365 globale Administratorkonto ein.</span><span class="sxs-lookup"><span data-stu-id="937d0-117">In Internet Explorer or your browser, go to [http://portal.office.com](http://portal.office.com) and sign in with your Office 365 global administrator account.</span></span>
    
2. <span data-ttu-id="937d0-118">Klicken Sie auf die Registerkarte **Microsoft Office Home** auf **Admin**.</span><span class="sxs-lookup"><span data-stu-id="937d0-118">On the **Microsoft Office Home** tab, click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="937d0-119">Klicken Sie in der Registerkarte „Office 365-Administrator“ im linken Navigationsbereich auf **Abrechnung > Dienste kaufen**.</span><span class="sxs-lookup"><span data-stu-id="937d0-119">On the Office 365 Admin tab, in the left navigation, click **Billing > Purchase services**.</span></span>
    
4. <span data-ttu-id="937d0-p103">Suchen Sie auf der Seite **Dienste kaufen** den Artikel **Azure Information Protection Premium P2**. Bewegen Sie den Mauszeiger über den Artikelnamen, und klicken Sie auf **Kostenlosen Test starten**.</span><span class="sxs-lookup"><span data-stu-id="937d0-p103">On the **Purchase services** page, find the **Azure Information Protection Premium P2** item. Hover your mouse over it and click **Start free trial**.</span></span>
    
5. <span data-ttu-id="937d0-122">Klicken Sie auf der Seite für die **Bestätigung Ihrer Bestellung** auf **Jetzt versuchen**.</span><span class="sxs-lookup"><span data-stu-id="937d0-122">On the **Confirm your order** page, click **Try now**.</span></span>
    
6. <span data-ttu-id="937d0-123">Klicken Sie auf der Seite **Bestellbestätigung** auf **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="937d0-123">On the **Order receipt** page, click **Continue**.</span></span>
    
<span data-ttu-id="937d0-124">Im nächsten Schritt können Sie die Azure Information Protection-Lizenz für alle Benutzerkonten aktivieren.</span><span class="sxs-lookup"><span data-stu-id="937d0-124">Next, you enable the Azure Information Protection license for all user accounts.</span></span>
  
1. <span data-ttu-id="937d0-125">	Klicken Sie auf der Registerkarte Office 365 Admin Center auf **Benutzer**.</span><span class="sxs-lookup"><span data-stu-id="937d0-125">On the Office 365 admin center tab, click **Users**.</span></span>
    
2.  <span data-ttu-id="937d0-126"> Wählen Sie in der Liste der Benutzerkonten Ihr globales Administratorkonto, und klicken Sie dann auf **earbeiten** für **Produktlizenzen**.</span><span class="sxs-lookup"><span data-stu-id="937d0-126">In the list of user accounts, select your global administrator account, and then click **Edit** for **Product licenses**.</span></span>
    
3. <span data-ttu-id="937d0-127">	Aktivieren die Produktlizenz für **Azure Information Protection Premium P2** zu **in**, klicken Sie auf **peichern,**, und klicken Sie dann zweimal auf **chließen**.</span><span class="sxs-lookup"><span data-stu-id="937d0-127">Turn the product license for **Azure Information Protection Premium P2** to **On**, click **Save,** and then click **Close** twice.</span></span>
    
4. <span data-ttu-id="937d0-128">Wiederholen Sie die Schritte 2 und 3 für Ihre anderen Konten (Benutzer 1 bis 5).</span><span class="sxs-lookup"><span data-stu-id="937d0-128">Repeat steps 2 and 3 for your other user accounts (User 1 through User 5).</span></span>
    
<span data-ttu-id="937d0-129">Ihre Office 365-Entwicklungs-/Testumgebung verfügt nun über:</span><span class="sxs-lookup"><span data-stu-id="937d0-129">Your Office 365 dev/test environment now has:</span></span>
  
- <span data-ttu-id="937d0-130">Office 365 E5 Enterprise and Azure Information Protection-Testabonnements.</span><span class="sxs-lookup"><span data-stu-id="937d0-130">Office 365 E5 Enterprise and Azure Information Protection trial subscriptions.</span></span>
    
- <span data-ttu-id="937d0-131">Alle Ihre Benutzerkonten sind aktiviert für die Verwendung von Office 365 E5 Enterprise und Azure Information Protection.</span><span class="sxs-lookup"><span data-stu-id="937d0-131">All of your user accounts enabled to use both Office 365 E5 Enterprise and Azure Information Protection.</span></span>
    
## <a name="phase-3-demonstrate-data-classification"></a><span data-ttu-id="937d0-132">Phase 3: Veranschaulichen der Datenklassifizierung</span><span class="sxs-lookup"><span data-stu-id="937d0-132">Phase 3: Demonstrate data classification</span></span>

<span data-ttu-id="937d0-133">In dieser Phase veranschaulichen Sie die Datenklassifizierung mit dem Azure Information Protection-Client und der standardmäßigen Azure Information Protection-Richtlinie.</span><span class="sxs-lookup"><span data-stu-id="937d0-133">In this phase, you demonstrate data classification using the Azure Information Protection client and the default Azure Information Protection policy.</span></span>
  
<span data-ttu-id="937d0-134">Wenn Sie die Unternehmenssimulation in der Office 365- Entwicklungs-/-Testumgebung verwenden, müssen Sie zuerst Office 2016 auf CLIENT1 installieren.</span><span class="sxs-lookup"><span data-stu-id="937d0-134">If you are using the simulated enterprise Office 365 dev/test environment, you must first install Office 2016 on CLIENT1.</span></span>
  
1. <span data-ttu-id="937d0-135">Verwenden Sie den Browser, und wechseln Sie zu der [Azure-Portal](http://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="937d0-135">Use your browser and go to the [Azure portal](http://portal.azure.com).</span></span>
    
2. <span data-ttu-id="937d0-136">	Klicken Sie auf **Ressourcengruppen >** [Ihr Ressourcengruppenname] **> CLIENT1 > Verbinden**.</span><span class="sxs-lookup"><span data-stu-id="937d0-136">Click **Resource Groups >** [your resource group name] **> CLIENT1 > Connect**.</span></span>
    
3. <span data-ttu-id="937d0-137">Führen Sie auf CLIENT1 Internet Explorer, fahren Sie mit der Office-Portal unter [http://portal.office.com](http://portal.office.com), und melden Sie sich mit den User5 Kontonamen und das Kennwort.</span><span class="sxs-lookup"><span data-stu-id="937d0-137">From CLIENT1, run Internet Explorer, go to the Office portal at [http://portal.office.com](http://portal.office.com), and then sign in with the User5 account name and password.</span></span>
    
4. <span data-ttu-id="937d0-138">Klicken Sie auf der Registerkarte der **Microsoft Office-Startseite** auf **Office 2016 installieren**.</span><span class="sxs-lookup"><span data-stu-id="937d0-138">On the **Microsoft Office Home** tab, click **Install Office 2016**.</span></span>
    
5. <span data-ttu-id="937d0-p104">	Führen Sie den Download aus, wenn Sie dazu aufgefordert werden, und klicken Sie auf **Ja**, wenn Sie von der Benutzerkontensteuerung dazu aufgefordert werden. Warten Sie, bis Office installiert ist. Klicken Sie nach Abschluss des Vorgangs zweimal auf **Schließen**.</span><span class="sxs-lookup"><span data-stu-id="937d0-p104">Run the download when prompted and click **Yes** when prompted by User Account Control. Wait for Office to install. When complete, click **Close** twice.</span></span>
    
<span data-ttu-id="937d0-142">Als Nächstes installieren Sie den Azure Information Protection-Client.</span><span class="sxs-lookup"><span data-stu-id="937d0-142">Next, you install the Azure Information Protection client.</span></span>
  
1. <span data-ttu-id="937d0-143">Wechseln Sie in Ihrem Browser oder Internet Explorer um die [Microsoft Azure Information Protection-Downloadseite](https://www.microsoft.com/download/details.aspx?id=53018).</span><span class="sxs-lookup"><span data-stu-id="937d0-143">In your browser or Internet Explorer, go to the [Microsoft Azure Information Protection download page](https://www.microsoft.com/download/details.aspx?id=53018).</span></span>
    
  - <span data-ttu-id="937d0-144">Wenn Sie die einfache Version der Office 365-Entwicklungs-/Testumgebung verwenden, nutzen Sie den Browser auf dem lokalen Computer.</span><span class="sxs-lookup"><span data-stu-id="937d0-144">If you are using the lightweight version of the Office 365 dev/test environment, use the browser on your local computer.</span></span>
    
  - <span data-ttu-id="937d0-145">Wenn Sie die Unternehmenssimulation der Office 365-Entwicklungs-/-Testumgebung verwenden, führen Sie Internet Explorer von CLIENT1 aus.</span><span class="sxs-lookup"><span data-stu-id="937d0-145">If you are using the simulated enterprise Office 365 dev/test environment, run Internet Explorer from CLIENT1.</span></span>
    
2. <span data-ttu-id="937d0-146">Klicken Sie auf der Downloadseite von **Microsoft Azure Information Protection** auf **Herunterladen**, klicken Sie auf **AzInfoProtection.exe**, und klicken Sie dann auf **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="937d0-146">On the **Microsoft Azure Information Protection** download page, click **Download**, click **AzInfoProtection.exe**, and then click **Next**.</span></span>
    
3. <span data-ttu-id="937d0-147">Wenn Sie dazu aufgefordert werden, führen Sie „AzInfoProtection.exe“ aus.</span><span class="sxs-lookup"><span data-stu-id="937d0-147">When prompted, run AzInfoProtection.exe.</span></span>
    
4. <span data-ttu-id="937d0-148">Klicken Sie im Client-Dialogfeld **Azure Information Protection installieren** auf **Ich stimme zu**, und klicken Sie auf **Ja**, wenn Sie von der Benutzerkontensteuerung dazu aufgefordert werden.</span><span class="sxs-lookup"><span data-stu-id="937d0-148">In the **Install the Azure Information Protection** client box, click **I agree**, and then click **Yes** when prompted by User Account Control.</span></span>
    
5. <span data-ttu-id="937d0-149">Klicken Sie im Feld **Erfolgreich abgeschlossen** auf **Schließen**.</span><span class="sxs-lookup"><span data-stu-id="937d0-149">In the **Completed successfully** box, click **Close.**</span></span>
    
<span data-ttu-id="937d0-150">Als Nächstes veranschaulichen Sie die Klassifizierung von Dokumenten.</span><span class="sxs-lookup"><span data-stu-id="937d0-150">Next, you demonstrate document classification.</span></span>
  
1. <span data-ttu-id="937d0-151">Klicken Sie in der Taskleiste auf das **Word**-Symbol.</span><span class="sxs-lookup"><span data-stu-id="937d0-151">Click the **Word** icon in the taskbar.</span></span>
    
2. <span data-ttu-id="937d0-152">Wenn Sie dazu aufgefordert werden, melden Sie sich mit den Kontonamen und dem Kennwort für Benutzer 5 an.</span><span class="sxs-lookup"><span data-stu-id="937d0-152">When prompted, sign in with the User5 account name and password.</span></span>
    
3. <span data-ttu-id="937d0-153">Wenn Sie Office 2016 gerade auf CLIENT1 installiert haben, klicken Sie im Feld **Das Wichtigste zuerst** auf **Akzeptieren**.</span><span class="sxs-lookup"><span data-stu-id="937d0-153">If you just installed Office 2016 on CLIENT1, in the **First things first** box, click **Accept**.</span></span>
    
4. <span data-ttu-id="937d0-154">Klicken Sie auf **Leeres Dokument**. </span><span class="sxs-lookup"><span data-stu-id="937d0-154">Click **Blank document**.</span></span> 
    
    <span data-ttu-id="937d0-155">Beachten Sie den Abschnitt **Schutz** auf dem Menüband auf der Registerkarte **Start** sowie die Zeile der Dokumentklassifizierungen.</span><span class="sxs-lookup"><span data-stu-id="937d0-155">Note the **Protection** section of the ribbon on the **Home** tab and the row of document classifications.</span></span>
    
5. <span data-ttu-id="937d0-156">Geben Sie in das leere Dokument etwas Text ein.</span><span class="sxs-lookup"><span data-stu-id="937d0-156">In the blank document, type some text.</span></span>
    
6. <span data-ttu-id="937d0-157">Klicken Sie auf **Datei > Speichern**, geben Sie den Namen **VorAIP** ein, und klicken Sie auf **OK**. </span><span class="sxs-lookup"><span data-stu-id="937d0-157">Click **File > Save**, type the name **BeforeAIP**, and then click **OK**.</span></span> 
    
7. <span data-ttu-id="937d0-158">Klicken Sie in der Zeile der Dokumentklassen auf den Abwärtspfeil für **Geheim**, und klicken Sie auf **Gesamtes Unternehmen**.</span><span class="sxs-lookup"><span data-stu-id="937d0-158">In the row of document classes, click the down arrow for **Secret**, and then click **All Company**.</span></span>
    
8. <span data-ttu-id="937d0-159">Klicken Sie auf **Datei > Speichern unter**, geben Sie den Namen **NachAIP** ein, und klicken Sie dann auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="937d0-159">Click **File > Save As**, type the name **AfterAIP**, and then click **OK**.</span></span>
    
9. <span data-ttu-id="937d0-160">Klicken Sie in der Taskleiste auf **Datei-Explorer**, und öffnen Sie dann den **Dokumente**-Ordner.</span><span class="sxs-lookup"><span data-stu-id="937d0-160">Click **File Explorer** in the taskbar, and then open the **Documents** folder.</span></span>
    
    <span data-ttu-id="937d0-p105">Beachten Sie die verschiedenen Dateigrößen der Dokumente **VorAIP** und **NachAIP**. Das Dokument „NachAIP“ ist größer, da es die Klassifizierungsinformationen enthält.</span><span class="sxs-lookup"><span data-stu-id="937d0-p105">Note the different file sizes of the **BeforeAIP** and **AfterAIP** documents. The AfterAIP document is larger because it contains the classification information.</span></span>
    
<span data-ttu-id="937d0-163">Im nächsten Schritt erlauben Sie jedem, auf die Websitesammlung „Support“ zuzugreifen.</span><span class="sxs-lookup"><span data-stu-id="937d0-163">Next, you allow everyone to access the Support site collection.</span></span>
  
1. <span data-ttu-id="937d0-164">	Klicken Sie auf der Registerkarte **Microsoft Office Home** auf **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="937d0-164">On the **Microsoft Office Home** tab, click **SharePoint**.</span></span>
    
2. <span data-ttu-id="937d0-165">Klicken Sie auf der Registerkarte **SharePoint** auf die **Websitesammlung „Support“**.</span><span class="sxs-lookup"><span data-stu-id="937d0-165">From the **SharePoint** tab, click **Support site collection**.</span></span>
    
3. <span data-ttu-id="937d0-166">Klicken Sie in der oberen rechten Ecke auf das **Einstellungen**-Symbol, und klicken Sie dann auf **Freigegeben für**.</span><span class="sxs-lookup"><span data-stu-id="937d0-166">In the upper right, click the **Settings** icon, and then click **Shared with**.</span></span>
    
4. <span data-ttu-id="937d0-167">**Freigeben "Support Site Collection"** klicken Sie auf **Erweitert**.</span><span class="sxs-lookup"><span data-stu-id="937d0-167">In **Share 'Support site collection'**, click **Advanced**.</span></span>
    
5. <span data-ttu-id="937d0-168">Klicken Sie in der Liste der SharePoint-Gruppen auf **Mitglieder der Websitesammlung „Support“**.</span><span class="sxs-lookup"><span data-stu-id="937d0-168">In the list of SharePoint groups, click **Support site collection Members**.</span></span>
    
6. <span data-ttu-id="937d0-169">Klicken Sie auf der Seite **Benutzer und Gruppen** auf **Neu**.</span><span class="sxs-lookup"><span data-stu-id="937d0-169">On the **People and Groups** page, click **New**.</span></span>
    
7. <span data-ttu-id="937d0-170">Geben Sie im **"Support Site Collection" Freigeben**, **jeder**, klicken Sie auf **alle Benutzer mit Ausnahme von externen Benutzern**und klicken Sie dann auf **freigeben.**</span><span class="sxs-lookup"><span data-stu-id="937d0-170">In **Share 'Support site collection'**, type **Everyone**, click **Everyone except external users**, and then click **Share.**</span></span>
    
8. <span data-ttu-id="937d0-171">Schließen Sie die Registerkarte **Benutzer und Gruppen**.</span><span class="sxs-lookup"><span data-stu-id="937d0-171">Close the **People and Groups** tab.</span></span>
    
<span data-ttu-id="937d0-172">Im nächsten Schritt melden Sie sich mit dem Benutzerkonto von Benutzer 5 an und laden das durch AIP geschützte Dokument in den Dokumentordner der Websitesammlung „Support“ hoch.</span><span class="sxs-lookup"><span data-stu-id="937d0-172">Next, you sign in with your User5 account and upload the AIP-protected document to the Documents folder of the Support site collection.</span></span>
  
1. <span data-ttu-id="937d0-173">Klicken Sie auf der Registerkarte der **Microsoft Office-Startseite** auf das Benutzersymbol in der oberen rechten Ecke, und klicken Sie dann auf **Abmelden**.</span><span class="sxs-lookup"><span data-stu-id="937d0-173">On the **Microsoft Office Home** tab, in the upper right, click the user icon, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="937d0-174">Wechseln Sie zu [http://portal.office.com](http://portal.office.com).</span><span class="sxs-lookup"><span data-stu-id="937d0-174">Go to [http://portal.office.com](http://portal.office.com).</span></span>
    
3. <span data-ttu-id="937d0-175">Klicken Sie auf der Seite **Office 365 anmelden** klicken Sie auf den Kontonamen User5, und melden Sie sich bei.</span><span class="sxs-lookup"><span data-stu-id="937d0-175">On the **Office 365 sign in** page, click the User5 account name and sign in.</span></span>
    
4. <span data-ttu-id="937d0-176">Klicken Sie auf der Registerkarte der **Microsoft Office-Startseite** auf **SharePoint > Websitesammlung „Support“**.</span><span class="sxs-lookup"><span data-stu-id="937d0-176">On the **Microsoft Office Home** tab, click **SharePoint > Support site collection**.</span></span>
    
5. <span data-ttu-id="937d0-177">Klicken Sie auf **Dokumente**, klicken Sie auf **Hochladen**, klicken Sie auf das Dokument **NachAIP**. Klicken Sie anschließend auf **Öffnen**.</span><span class="sxs-lookup"><span data-stu-id="937d0-177">Click **Documents**, click **Upload**, click the **AfterAIP** document, and then click **Open**.</span></span>
    
    <span data-ttu-id="937d0-178">Das Dokument „NachAIP.docx“ sollte im Ordner „Dokumente“ in der Websitesammlung „Support“ angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="937d0-178">You should see AfterAIP.docx in the Documents folder on the Support site collection.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="937d0-179">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="937d0-179">See Also</span></span>

[<span data-ttu-id="937d0-180">Testumgebungsanleitungen (TLGs) zur Cloudakzeptanz</span><span class="sxs-lookup"><span data-stu-id="937d0-180">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)

[<span data-ttu-id="937d0-181">Office 365- und EMS-Entwicklungs-/Testumgebung</span><span class="sxs-lookup"><span data-stu-id="937d0-181">Office 365 and EMS dev/test environment</span></span>](http://technet.microsoft.com/library/c76eea86-d4b6-4d35-ad89-341696e89ef7.aspx)
  
[<span data-ttu-id="937d0-182">Azure Information Protection</span><span class="sxs-lookup"><span data-stu-id="937d0-182">Azure Information Protection</span></span>](https://www.microsoft.com/cloud-platform/azure-information-protection)


