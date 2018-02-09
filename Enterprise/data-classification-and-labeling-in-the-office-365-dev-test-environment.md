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
description: 'Zusammenfassung: Konfigurieren Sie und veranschaulichen Sie der Klassifizierung von Daten und Beschriftung mit dem Azure Informationen Schutz (per) in Ihrer Office 365 Dev/Test-Umgebung.'
ms.openlocfilehash: 06f7ebefad8b4d622ab225298155b4f117ff2b75
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/09/2018
---
# <a name="data-classification-and-labeling-in-the-office-365-devtest-environment"></a><span data-ttu-id="bc21a-103">Datenklassifizierung und -kennzeichnung in Office 365-Entwicklungs-/-Testumgebungen</span><span class="sxs-lookup"><span data-stu-id="bc21a-103">Data classification and labeling in the Office 365 dev/test environment</span></span>

 <span data-ttu-id="bc21a-104">**Zusammenfassung:** Konfigurieren Sie und veranschaulichen Sie der Klassifizierung von Daten und Beschriftung mit dem Azure Informationen Schutz (per) in Ihrer Office 365 Dev/Test-Umgebung.</span><span class="sxs-lookup"><span data-stu-id="bc21a-104">**Summary:** Configure and demonstrate data classification and labeling using the Azure Information Protection (AIP) client in your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="bc21a-p101">Der Client Azure Information Protection können Sie ein Dokument klassifizieren, bevor Sie ihn in einen Ordner SharePoint Online in Office 365 hochladen. Mit den Anweisungen in diesem Artikel installieren Sie den Client Azure Information Protection und veranschaulichen der Datenklassifikation. Weitere Informationen finden Sie unter [Azure Information Protection](https://www.microsoft.com/cloud-platform/azure-information-protection).</span><span class="sxs-lookup"><span data-stu-id="bc21a-p101">The Azure Information Protection client allows you to classify a document before you upload it to a SharePoint Online folder in Office 365. With the instructions in this article, you install the Azure Information Protection client and demonstrate data classification. For more information, see [Azure Information Protection](https://www.microsoft.com/cloud-platform/azure-information-protection).</span></span>
  
> [!TIP]
> <span data-ttu-id="bc21a-108">Klicken Sie [hier](http://aka.ms/catlgstack), um eine visuelle Darstellung aller Artikel im Stapel der Testumgebungsanleitungen in der Microsoft Cloud zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="bc21a-108">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-build-out-your-office-365-devtest-environment"></a><span data-ttu-id="bc21a-109">Phase 1: Erstellen Ihrer Office 365-Entwicklungs-/Testumgebung</span><span class="sxs-lookup"><span data-stu-id="bc21a-109">Phase 1: Build out your Office 365 dev/test environment</span></span>

<span data-ttu-id="bc21a-110">Befolgen Sie die Anweisungen in [Office 365 Dev/Test Environment](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="bc21a-110">Follow the instructions in [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
## <a name="phase-2-add-the-azure-information-protection-trial-subscription"></a><span data-ttu-id="bc21a-111">Phase 2: Hinzufügen des Azure Information Protection-Abonnements</span><span class="sxs-lookup"><span data-stu-id="bc21a-111">Phase 2: Add the Azure Information Protection trial subscription</span></span>

<span data-ttu-id="bc21a-p102">In dieser Phase Ihrer Office 365-Umgebung Test-/Azure Information Protection hinzugefügt und für Ihre Benutzerkonten zu aktivieren. Wenn Sie [Office 365 und zur Abstimmung Test-/Umgebung](http://technet.microsoft.com/library/c76eea86-d4b6-4d35-ad89-341696e89ef7.aspx)konfiguriert haben, überspringen Sie diese Phase. Das Testversion Enterprise Mobilität Suite-Abonnement umfasst Azure Information Protection-Lizenzen.</span><span class="sxs-lookup"><span data-stu-id="bc21a-p102">In this phase, you add Azure Information Protection to your Office 365 dev/test environment and enable it for your user accounts. If you have configured the [Office 365 and EMS dev/test environment](http://technet.microsoft.com/library/c76eea86-d4b6-4d35-ad89-341696e89ef7.aspx), skip this phase. The Enterprise Mobility Suite trial subscription includes Azure Information Protection licenses.</span></span>
  
<span data-ttu-id="bc21a-115">Melden Sie sich zunächst für ein Azure Information Protection-Testabonnement an.</span><span class="sxs-lookup"><span data-stu-id="bc21a-115">First, sign up for an Azure Information Protection trial subscription.</span></span>
  
### <a name="sign-up-for-an-azure-information-protection-trial-subscription"></a><span data-ttu-id="bc21a-116">Anmelden für ein Azure Information Protection-Testabonnement</span><span class="sxs-lookup"><span data-stu-id="bc21a-116">Sign up for an Azure Information Protection trial subscription</span></span>

1. <span data-ttu-id="bc21a-117">In Internet Explorer oder in Ihrem Browser wechseln Sie zu [http://portal.office.com](http://portal.office.com) , und melden Sie sich mit Ihrem Office 365 globale Administratorkonto ein.</span><span class="sxs-lookup"><span data-stu-id="bc21a-117">In Internet Explorer or your browser, go to [http://portal.office.com](http://portal.office.com) and sign in with your Office 365 global administrator account.</span></span>
    
2. <span data-ttu-id="bc21a-118">Klicken Sie auf der Registerkarte **Microsoft Office Home** auf die Kachel " **Admin** ".</span><span class="sxs-lookup"><span data-stu-id="bc21a-118">On the **Microsoft Office Home** tab, click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="bc21a-119">Klicken Sie auf der Registerkarte Office 365 Admin im linken Navigationsbereich auf **Abrechnung > Dienste erwerben**.</span><span class="sxs-lookup"><span data-stu-id="bc21a-119">On the Office 365 Admin tab, in the left navigation, click **Billing > Purchase services**.</span></span>
    
4. <span data-ttu-id="bc21a-p103">Suchen Sie auf der Seite **Dienste erwerben** des **Azure Informationen Protection Premium P2** -Elements. Bewegen Sie die Maus darauf, und klicken Sie auf **Start kostenlose Testversion**.</span><span class="sxs-lookup"><span data-stu-id="bc21a-p103">On the **Purchase services** page, find the **Azure Information Protection Premium P2** item. Hover your mouse over it and click **Start free trial**.</span></span>
    
5. <span data-ttu-id="bc21a-122">Klicken Sie auf der Seite für die **Bestätigung Ihrer Bestellung** auf **Jetzt versuchen**.</span><span class="sxs-lookup"><span data-stu-id="bc21a-122">On the **Confirm your order** page, click **Try now**.</span></span>
    
6. <span data-ttu-id="bc21a-123">Klicken Sie auf der Seite **Bestellbestätigung** auf **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="bc21a-123">On the **Order receipt** page, click **Continue**.</span></span>
    
<span data-ttu-id="bc21a-124">Im nächsten Schritt können Sie die Azure Information Protection-Lizenz für alle Benutzerkonten aktivieren.</span><span class="sxs-lookup"><span data-stu-id="bc21a-124">Next, you enable the Azure Information Protection license for all user accounts.</span></span>
  
1. <span data-ttu-id="bc21a-125">Klicken Sie auf die Registerkarte Office 365 Admin Center auf **Benutzer**.</span><span class="sxs-lookup"><span data-stu-id="bc21a-125">On the Office 365 admin center tab, click **Users**.</span></span>
    
2.  <span data-ttu-id="bc21a-126">Wählen Sie in der Liste der Benutzerkonten die globale Administratorkonto ein, und klicken Sie dann auf **Bearbeiten** , für die **Lizenzen**.</span><span class="sxs-lookup"><span data-stu-id="bc21a-126">In the list of user accounts, select your global administrator account, and then click **Edit** for **Product licenses**.</span></span>
    
3. <span data-ttu-id="bc21a-127">Deaktivieren Sie die-Lizenz für **Azure Informationen Protection Premium P2** bis **auf**, klicken Sie auf **Speichern,** und klicken Sie dann zweimal auf **Schließen** .</span><span class="sxs-lookup"><span data-stu-id="bc21a-127">Turn the product license for **Azure Information Protection Premium P2** to **On**, click **Save,** and then click **Close** twice.</span></span>
    
4. <span data-ttu-id="bc21a-128">Wiederholen Sie die Schritte 2 und 3 für Ihre anderen Konten (Benutzer 1 bis 5).</span><span class="sxs-lookup"><span data-stu-id="bc21a-128">Repeat steps 2 and 3 for your other user accounts (User 1 through User 5).</span></span>
    
<span data-ttu-id="bc21a-129">Ihre Office 365-Entwicklungs-/Testumgebung verfügt nun über:</span><span class="sxs-lookup"><span data-stu-id="bc21a-129">Your Office 365 dev/test environment now has:</span></span>
  
- <span data-ttu-id="bc21a-130">Office 365 E5 Enterprise and Azure Information Protection-Testabonnements.</span><span class="sxs-lookup"><span data-stu-id="bc21a-130">Office 365 E5 Enterprise and Azure Information Protection trial subscriptions.</span></span>
    
- <span data-ttu-id="bc21a-131">Alle Ihre Benutzerkonten sind aktiviert für die Verwendung von Office 365 E5 Enterprise und Azure Information Protection.</span><span class="sxs-lookup"><span data-stu-id="bc21a-131">All of your user accounts enabled to use both Office 365 E5 Enterprise and Azure Information Protection.</span></span>
    
## <a name="phase-3-demonstrate-data-classification"></a><span data-ttu-id="bc21a-132">Phase 3: Veranschaulichen der Datenklassifizierung</span><span class="sxs-lookup"><span data-stu-id="bc21a-132">Phase 3: Demonstrate data classification</span></span>

<span data-ttu-id="bc21a-133">In dieser Phase veranschaulichen Sie die Datenklassifizierung mit dem Azure Information Protection-Client und der standardmäßigen Azure Information Protection-Richtlinie.</span><span class="sxs-lookup"><span data-stu-id="bc21a-133">In this phase, you demonstrate data classification using the Azure Information Protection client and the default Azure Information Protection policy.</span></span>
  
<span data-ttu-id="bc21a-134">Wenn Sie die Unternehmenssimulation in der Office 365- Entwicklungs-/-Testumgebung verwenden, müssen Sie zuerst Office 2016 auf CLIENT1 installieren.</span><span class="sxs-lookup"><span data-stu-id="bc21a-134">If you are using the simulated enterprise Office 365 dev/test environment, you must first install Office 2016 on CLIENT1.</span></span>
  
1. <span data-ttu-id="bc21a-135">Verwenden Sie den Browser, und wechseln Sie zu der [Azure-Portal](http://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="bc21a-135">Use your browser and go to the [Azure portal](http://portal.azure.com).</span></span>
    
2. <span data-ttu-id="bc21a-136">Klicken Sie auf **Ressourcengruppen >** [Ihre Gruppe Ressourcenname] **> CLIENT1 > Connect**.</span><span class="sxs-lookup"><span data-stu-id="bc21a-136">Click **Resource Groups >** [your resource group name] **> CLIENT1 > Connect**.</span></span>
    
3. <span data-ttu-id="bc21a-137">CLIENT1 starten Sie Internet Explorer, wechseln Sie zu der Office-Portal unter [http://portal.office.com](http://portal.office.com)und melden Sie sich mit den User5 Kontonamen und das Kennwort.</span><span class="sxs-lookup"><span data-stu-id="bc21a-137">From CLIENT1, run Internet Explorer, go to the Office portal at [http://portal.office.com](http://portal.office.com), and then sign in with the User5 account name and password.</span></span>
    
4. <span data-ttu-id="bc21a-138">Klicken Sie auf der Registerkarte **Start von Microsoft Office** auf **Office 2016 installieren**.</span><span class="sxs-lookup"><span data-stu-id="bc21a-138">On the **Microsoft Office Home** tab, click **Install Office 2016**.</span></span>
    
5. <span data-ttu-id="bc21a-p104">Führen Sie die heruntergeladene Datei, wenn Sie dazu aufgefordert werden, und klicken Sie auf **Ja,** Wenn die Benutzerkontensteuerung dazu aufgefordert werden. Warten Sie Office installieren. Nach Abschluss des Vorgangs **Schließen** klicken Sie zweimal auf.</span><span class="sxs-lookup"><span data-stu-id="bc21a-p104">Run the download when prompted and click **Yes** when prompted by User Account Control. Wait for Office to install. When complete, click **Close** twice.</span></span>
    
<span data-ttu-id="bc21a-142">Als Nächstes installieren Sie den Azure Information Protection-Client.</span><span class="sxs-lookup"><span data-stu-id="bc21a-142">Next, you install the Azure Information Protection client.</span></span>
  
1. <span data-ttu-id="bc21a-143">Wechseln Sie in Ihrem Browser oder Internet Explorer um die [Microsoft Azure Information Protection-Downloadseite](https://www.microsoft.com/download/details.aspx?id=53018).</span><span class="sxs-lookup"><span data-stu-id="bc21a-143">In your browser or Internet Explorer, go to the [Microsoft Azure Information Protection download page](https://www.microsoft.com/download/details.aspx?id=53018).</span></span>
    
  - <span data-ttu-id="bc21a-144">Wenn Sie die einfache Version der Office 365-Entwicklungs-/Testumgebung verwenden, nutzen Sie den Browser auf dem lokalen Computer.</span><span class="sxs-lookup"><span data-stu-id="bc21a-144">If you are using the lightweight version of the Office 365 dev/test environment, use the browser on your local computer.</span></span>
    
  - <span data-ttu-id="bc21a-145">Wenn Sie die Unternehmenssimulation der Office 365-Entwicklungs-/-Testumgebung verwenden, führen Sie Internet Explorer von CLIENT1 aus.</span><span class="sxs-lookup"><span data-stu-id="bc21a-145">If you are using the simulated enterprise Office 365 dev/test environment, run Internet Explorer from CLIENT1.</span></span>
    
2. <span data-ttu-id="bc21a-146">Klicken Sie auf der Downloadseite **Microsoft Azure Information Protection** auf **Download**, klicken Sie auf **AzInfoProtection.exe**, und klicken Sie dann auf **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="bc21a-146">On the **Microsoft Azure Information Protection** download page, click **Download**, click **AzInfoProtection.exe**, and then click **Next**.</span></span>
    
3. <span data-ttu-id="bc21a-147">Wenn Sie dazu aufgefordert werden, führen Sie „AzInfoProtection.exe“ aus.</span><span class="sxs-lookup"><span data-stu-id="bc21a-147">When prompted, run AzInfoProtection.exe.</span></span>
    
4. <span data-ttu-id="bc21a-148">Klicken Sie im Feld Client **die Azure Information Protection installieren** auf **ich stimme zu**, und klicken Sie dann auf **Ja,** Wenn die Benutzerkontensteuerung dazu aufgefordert werden.</span><span class="sxs-lookup"><span data-stu-id="bc21a-148">In the **Install the Azure Information Protection** client box, click **I agree**, and then click **Yes** when prompted by User Account Control.</span></span>
    
5. <span data-ttu-id="bc21a-149">Klicken Sie in das Feld **wurde erfolgreich abgeschlossen** auf **Close.**</span><span class="sxs-lookup"><span data-stu-id="bc21a-149">In the **Completed successfully** box, click **Close.**</span></span>
    
<span data-ttu-id="bc21a-150">Als Nächstes veranschaulichen Sie die Klassifizierung von Dokumenten.</span><span class="sxs-lookup"><span data-stu-id="bc21a-150">Next, you demonstrate document classification.</span></span>
  
1. <span data-ttu-id="bc21a-151">Klicken Sie auf das **Word** -Symbol in der Taskleiste.</span><span class="sxs-lookup"><span data-stu-id="bc21a-151">Click the **Word** icon in the taskbar.</span></span>
    
2. <span data-ttu-id="bc21a-152">Wenn Sie dazu aufgefordert werden, melden Sie sich mit den Kontonamen und dem Kennwort für Benutzer 5 an.</span><span class="sxs-lookup"><span data-stu-id="bc21a-152">When prompted, sign in with the User5 account name and password.</span></span>
    
3. <span data-ttu-id="bc21a-153">Wenn Sie gerade Office 2016 auf CLIENT1 im installiert die **sollte zunächst festgestellt ersten** Feld, klicken Sie auf **annehmen**.</span><span class="sxs-lookup"><span data-stu-id="bc21a-153">If you just installed Office 2016 on CLIENT1, in the **First things first** box, click **Accept**.</span></span>
    
4. <span data-ttu-id="bc21a-154">Klicken Sie auf **leeres Dokument**.</span><span class="sxs-lookup"><span data-stu-id="bc21a-154">Click **Blank document**.</span></span> 
    
    <span data-ttu-id="bc21a-155">Beachten Sie den Abschnitt " **Protection** " auf dem Menüband auf der Registerkarte **Start** und Dokument Klassifikationen in der Zeile.</span><span class="sxs-lookup"><span data-stu-id="bc21a-155">Note the **Protection** section of the ribbon on the **Home** tab and the row of document classifications.</span></span>
    
5. <span data-ttu-id="bc21a-156">Geben Sie in das leere Dokument etwas Text ein.</span><span class="sxs-lookup"><span data-stu-id="bc21a-156">In the blank document, type some text.</span></span>
    
6. <span data-ttu-id="bc21a-157">Klicken Sie auf **Datei > Speichern**, geben Sie den Namen **BeforeAIP**, und klicken Sie dann auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="bc21a-157">Click **File > Save**, type the name **BeforeAIP**, and then click **OK**.</span></span> 
    
7. <span data-ttu-id="bc21a-158">Klicken Sie in der Zeile des Dokumentenklassen auf den Pfeil nach unten für **geheimen Schlüssel**, und klicken Sie dann auf **Alle Unternehmen**.</span><span class="sxs-lookup"><span data-stu-id="bc21a-158">In the row of document classes, click the down arrow for **Secret**, and then click **All Company**.</span></span>
    
8. <span data-ttu-id="bc21a-159">Klicken Sie auf **Datei > Speichern unter**, geben Sie den Namen **AfterAIP**, und klicken Sie dann auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="bc21a-159">Click **File > Save As**, type the name **AfterAIP**, and then click **OK**.</span></span>
    
9. <span data-ttu-id="bc21a-160">Klicken Sie in der Taskleiste auf **Datei-Explorer** , und öffnen Sie den Ordner **Dokumente** .</span><span class="sxs-lookup"><span data-stu-id="bc21a-160">Click **File Explorer** in the taskbar, and then open the **Documents** folder.</span></span>
    
    <span data-ttu-id="bc21a-p105">Beachten Sie die verschiedenen Dateigröße der Dokumente **BeforeAIP** und **AfterAIP** . Das Dokument AfterAIP ist größer, da sie die Klassifizierungsinformationen enthält.</span><span class="sxs-lookup"><span data-stu-id="bc21a-p105">Note the different file sizes of the **BeforeAIP** and **AfterAIP** documents. The AfterAIP document is larger because it contains the classification information.</span></span>
    
<span data-ttu-id="bc21a-163">Im nächsten Schritt erlauben Sie jedem, auf die Websitesammlung „Support“ zuzugreifen.</span><span class="sxs-lookup"><span data-stu-id="bc21a-163">Next, you allow everyone to access the Support site collection.</span></span>
  
1. <span data-ttu-id="bc21a-164">Klicken Sie auf der Registerkarte **Start von Microsoft Office** **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="bc21a-164">On the **Microsoft Office Home** tab, click **SharePoint**.</span></span>
    
2. <span data-ttu-id="bc21a-165">Klicken Sie auf der Registerkarte **SharePoint** **Support**.</span><span class="sxs-lookup"><span data-stu-id="bc21a-165">From the **SharePoint** tab, click **Support site collection**.</span></span>
    
3. <span data-ttu-id="bc21a-166">Klicken Sie in der oberen rechten Ecke klicken Sie auf das Symbol **Einstellungen** , und klicken Sie dann auf **freigegeben für**.</span><span class="sxs-lookup"><span data-stu-id="bc21a-166">In the upper right, click the **Settings** icon, and then click **Shared with**.</span></span>
    
4. <span data-ttu-id="bc21a-167">**Freigeben "Support Site Collection"**klicken Sie auf **Erweitert**.</span><span class="sxs-lookup"><span data-stu-id="bc21a-167">In **Share 'Support site collection'**, click **Advanced**.</span></span>
    
5. <span data-ttu-id="bc21a-168">Klicken Sie in der Liste der SharePoint-Gruppen **Unterstützung Websitesammlung Mitglieder**auf.</span><span class="sxs-lookup"><span data-stu-id="bc21a-168">In the list of SharePoint groups, click **Support site collection Members**.</span></span>
    
6. <span data-ttu-id="bc21a-169">Klicken Sie auf der Seite **Benutzer und Gruppen** auf **Neu**.</span><span class="sxs-lookup"><span data-stu-id="bc21a-169">On the **People and Groups** page, click **New**.</span></span>
    
7. <span data-ttu-id="bc21a-170">Geben Sie im **"Support Site Collection" Freigeben**, **jeder**, klicken Sie auf **alle Benutzer mit Ausnahme von externen Benutzern**und klicken Sie dann auf **freigeben.**</span><span class="sxs-lookup"><span data-stu-id="bc21a-170">In **Share 'Support site collection'**, type **Everyone**, click **Everyone except external users**, and then click **Share.**</span></span>
    
8. <span data-ttu-id="bc21a-171">Schließen Sie die Registerkarte **Personen und Gruppen** .</span><span class="sxs-lookup"><span data-stu-id="bc21a-171">Close the **People and Groups** tab.</span></span>
    
<span data-ttu-id="bc21a-172">Im nächsten Schritt melden Sie sich mit dem Benutzerkonto von Benutzer 5 an und laden das durch AIP geschützte Dokument in den Dokumentordner der Websitesammlung „Support“ hoch.</span><span class="sxs-lookup"><span data-stu-id="bc21a-172">Next, you sign in with your User5 account and upload the AIP-protected document to the Documents folder of the Support site collection.</span></span>
  
1. <span data-ttu-id="bc21a-173">Klicken Sie auf der Registerkarte **Microsoft Office Home** in der oberen rechten Ecke klicken Sie auf das Symbol "Benutzer", und klicken Sie dann auf **Abmelden**.</span><span class="sxs-lookup"><span data-stu-id="bc21a-173">On the **Microsoft Office Home** tab, in the upper right, click the user icon, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="bc21a-174">Wechseln Sie zur [http://portal.office.com](http://portal.office.com).</span><span class="sxs-lookup"><span data-stu-id="bc21a-174">Go to [http://portal.office.com](http://portal.office.com).</span></span>
    
3. <span data-ttu-id="bc21a-175">Klicken Sie auf die ** Office 365 anmelden ** Seite, klicken Sie auf den Kontonamen User5 und anmelden.</span><span class="sxs-lookup"><span data-stu-id="bc21a-175">On the ** Office 365 sign in** page, click the User5 account name and sign in.</span></span>
    
4. <span data-ttu-id="bc21a-176">Klicken Sie auf der Registerkarte **Start von Microsoft Office** auf **SharePoint > Websitesammlung unterstützen**.</span><span class="sxs-lookup"><span data-stu-id="bc21a-176">On the **Microsoft Office Home** tab, click **SharePoint > Support site collection**.</span></span>
    
5. <span data-ttu-id="bc21a-177">Klicken Sie auf **Dokumente**, klicken Sie auf **Hochladen**, klicken Sie auf das Dokument **AfterAIP** , und klicken Sie dann auf **Öffnen**.</span><span class="sxs-lookup"><span data-stu-id="bc21a-177">Click **Documents**, click **Upload**, click the **AfterAIP** document, and then click **Open**.</span></span>
    
    <span data-ttu-id="bc21a-178">Das Dokument „NachAIP.docx“ sollte im Ordner „Dokumente“ in der Websitesammlung „Support“ angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="bc21a-178">You should see AfterAIP.docx in the Documents folder on the Support site collection.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="bc21a-179">Weitere Artikel</span><span class="sxs-lookup"><span data-stu-id="bc21a-179">See Also</span></span>

[<span data-ttu-id="bc21a-180">Testumgebungsanleitungen (TLGs) zur Cloudakzeptanz</span><span class="sxs-lookup"><span data-stu-id="bc21a-180">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)

[<span data-ttu-id="bc21a-181">Office 365 und zur Abstimmung Test-/Umgebung</span><span class="sxs-lookup"><span data-stu-id="bc21a-181">Office 365 and EMS dev/test environment</span></span>](http://technet.microsoft.com/library/c76eea86-d4b6-4d35-ad89-341696e89ef7.aspx)
  
[<span data-ttu-id="bc21a-182">Azure Information Protection</span><span class="sxs-lookup"><span data-stu-id="bc21a-182">Azure Information Protection</span></span>](https://www.microsoft.com/cloud-platform/azure-information-protection)


