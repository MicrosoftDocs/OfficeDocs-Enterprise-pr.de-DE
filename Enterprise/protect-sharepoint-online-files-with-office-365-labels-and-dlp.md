---
title: Schützen von SharePoint Online-Dateien mit Office 365 Etiketten und DLP
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
- Strat_O365_Enterprise
ms.custom:
- Ent_Solutions
ms.assetid: c9f837af-8d71-4df1-a285-dedb1c5618b3
description: 'Zusammenfassung: Anwenden von Office 365 Etiketten und Daten Loss Prevention (DLP) Richtlinien für SharePoint Online Teamwebsites mit verschiedenen Ebenen Schutz von Informationen.'
ms.openlocfilehash: a6413ac556cf63cbe7491180d65b4425cd0dba3d
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="protect-sharepoint-online-files-with-office-365-labels-and-dlp"></a><span data-ttu-id="64283-103">Schützen von SharePoint Online-Dateien mit Office 365 Etiketten und DLP</span><span class="sxs-lookup"><span data-stu-id="64283-103">Protect SharePoint Online files with Office 365 labels and DLP</span></span>

 <span data-ttu-id="64283-104">**Zusammenfassung:** Gelten Sie Office 365 Etiketten und Daten Richtlinien von Datenverlust (DLP) für SharePoint Online Teamwebsites mit verschiedenen Schutzebenen Informationen.</span><span class="sxs-lookup"><span data-stu-id="64283-104">**Summary:** Apply Office 365 labels and data loss prevention (DLP) policies for SharePoint Online team sites with various levels of information protection.</span></span>
  
<span data-ttu-id="64283-p101">Verwenden Sie die Schritte in diesem Artikel zum Entwerfen und Bereitstellen von Office 365 Etiketten und DLP-Richtlinien für geplante, empfindlich und streng vertraulich SharePoint Online Teamwebsites. Weitere Informationen zu diesen drei Ebenen des Schutzes finden Sie unter [Secure SharePoint Online-Websites und Dateien](secure-sharepoint-online-sites-and-files.md).</span><span class="sxs-lookup"><span data-stu-id="64283-p101">Use the steps in this article to design and deploy Office 365 labels and DLP policies for baseline, sensitive, and highly confidential SharePoint Online team sites. For more information about these three tiers of protection, see [Secure SharePoint Online sites and files](secure-sharepoint-online-sites-and-files.md).</span></span>
  
## <a name="office-365-labels-for-your-sharepoint-online-sites"></a><span data-ttu-id="64283-107">Office 365-Bezeichnungen für Ihre SharePoint Online-Websites</span><span class="sxs-lookup"><span data-stu-id="64283-107">Office 365 labels for your SharePoint Online sites</span></span>

<span data-ttu-id="64283-108">Es gibt drei Phasen beim Erstellen und anschließenden Zuweisen von Office 365-Bezeichnungen zu SharePoint Online-Teamwebsites.</span><span class="sxs-lookup"><span data-stu-id="64283-108">There are three phases to creating and then assigning Office 365 labels to SharePoint Online team sites.</span></span>
  
### <a name="phase-1-determine-the-office-365-label-names"></a><span data-ttu-id="64283-109">Phase 1: Festlegen der Office 365-Bezeichnungsnamen</span><span class="sxs-lookup"><span data-stu-id="64283-109">Phase 1: Determine the Office 365 label names</span></span>

<span data-ttu-id="64283-p102">In dieser Phase bestimmen Sie die Namen Ihrer Office 365-Bezeichnungen für die vier Ebenen des Informationsschutzes, der auf SharePoint Online-Teamwebsites angewendet wird. Die folgende Tabelle listet die empfohlenen Namen für jede Ebene auf.</span><span class="sxs-lookup"><span data-stu-id="64283-p102">In this phase, you determine the names of your Office 365 labels for the four levels of information protection applied to SharePoint Online team sites. The following table lists the recommended names for each level.</span></span>
  
|<span data-ttu-id="64283-112">**Schutzebene der SharePoint Online-Teamwebsite**</span><span class="sxs-lookup"><span data-stu-id="64283-112">**SharePoint Online team site protection level**</span></span>|<span data-ttu-id="64283-113">**Bezeichnungsname**</span><span class="sxs-lookup"><span data-stu-id="64283-113">**Label name**</span></span>|
|:-----|:-----|
|<span data-ttu-id="64283-114">Grundlegend-Öffentlich</span><span class="sxs-lookup"><span data-stu-id="64283-114">Baseline-Public</span></span>  <br/> |<span data-ttu-id="64283-115">Intern Öffentlich</span><span class="sxs-lookup"><span data-stu-id="64283-115">Internal public</span></span>  <br/> |
|<span data-ttu-id="64283-116">Grundlegend-Privat</span><span class="sxs-lookup"><span data-stu-id="64283-116">Baseline-Private</span></span>  <br/> |<span data-ttu-id="64283-117">Privat</span><span class="sxs-lookup"><span data-stu-id="64283-117">Private</span></span>  <br/> |
|<span data-ttu-id="64283-118">Vertraulich</span><span class="sxs-lookup"><span data-stu-id="64283-118">Sensitive</span></span>  <br/> |<span data-ttu-id="64283-119">Vertraulich</span><span class="sxs-lookup"><span data-stu-id="64283-119">Sensitive</span></span>  <br/> |
|<span data-ttu-id="64283-120">Streng vertraulich</span><span class="sxs-lookup"><span data-stu-id="64283-120">Highly Confidential</span></span>  <br/> |<span data-ttu-id="64283-121">Streng vertraulich</span><span class="sxs-lookup"><span data-stu-id="64283-121">Highly Confidential</span></span>  <br/> |
   
### <a name="phase-2-create-the-office-365-labels"></a><span data-ttu-id="64283-122">Phase 2: Erstellen von Office 365-Bezeichnungen</span><span class="sxs-lookup"><span data-stu-id="64283-122">Phase 2: Create the Office 365 labels</span></span>

<span data-ttu-id="64283-123">In dieser Phase erstellen und veröffentlichen Sie Ihre bestimmten Bezeichnungen für die unterschiedlichen Ebenen des Informationsschutzes.</span><span class="sxs-lookup"><span data-stu-id="64283-123">In this phase, you create and then publish your determined labels for the different levels of information protection.</span></span>
  
<span data-ttu-id="64283-124">Zum Erstellen der Bezeichnungen können Sie das Office 365 Admin Center oder Microsoft PowerShell.</span><span class="sxs-lookup"><span data-stu-id="64283-124">To create the labels, you can use the Office 365 Admin center or Microsoft PowerShell.</span></span>
  
### <a name="create-office-365-labels-with-the-office-365-admin-center"></a><span data-ttu-id="64283-125">Erstellen von Office 365-Bezeichnungen mit dem Office 365 Admin Center</span><span class="sxs-lookup"><span data-stu-id="64283-125">Create Office 365 labels with the Office 365 Admin center</span></span>

1. <span data-ttu-id="64283-p103">Melden Sie sich mit einem Konto beim Office 365-Portal an, das über die Rolle „Sicherheitsadministrator" oder Unternehmensadministrator" verfügt. Hilfe finden Sie unter [Wo kann ich mich bei Office 365 Business anmelden?](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="64283-p103">Sign in to the Office 365 portal with an account that has the Security Administrator or Company Administrator role. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="64283-128">Klicken Sie auf der Registerkarte **Microsoft Office Home** auf die Kachel **Admin**.</span><span class="sxs-lookup"><span data-stu-id="64283-128">From the **Microsoft Office Home** tab, click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="64283-129">Klicken Sie auf der neuen Registerkarte **Office Admin Center** im Browser auf **Admin Center > Security &amp; Compliance**.</span><span class="sxs-lookup"><span data-stu-id="64283-129">From the new **Office Admin center** tab of your browser, click **Admin centers > Security &amp; Compliance**.</span></span>
    
4. <span data-ttu-id="64283-130">Klicken Sie auf der neuen Registerkarte **Start - Security &amp; Compliance** im Browser auf **Klassifizierungen > Bezeichnungen**.</span><span class="sxs-lookup"><span data-stu-id="64283-130">From the new **Home - Security &amp; Compliance** tab of your browser, click **Classifications > Labels**.</span></span>
    
5. <span data-ttu-id="64283-131">Klicken Sie im Bereich **Start > Bezeichnungen** auf **Bezeichnung erstellen**.</span><span class="sxs-lookup"><span data-stu-id="64283-131">From the **Home > Labels** pane, click **Create a label**.</span></span>
    
6. <span data-ttu-id="64283-132">Klicken Sie im Bereich **Name die Bezeichnung** Geben Sie den Namen der Beschriftung, und klicken Sie dann auf **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="64283-132">On the **Name your label** pane, type the name of the label, and then click **Next**.</span></span>
    
7. <span data-ttu-id="64283-133">Klicken Sie im Bereich **Bezeichnungseinstellungen** auf **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="64283-133">On the **Label settings** pane, click **Next**.</span></span>
    
8. <span data-ttu-id="64283-134">Klicken Sie im Bereich **Einstellungen überprüfen** auf **Bezeichnung erstellen**, und klicken Sie dann auf **Schließen**.</span><span class="sxs-lookup"><span data-stu-id="64283-134">On the **Review your settings** pane, click **Create this label**, and then click **Close**.</span></span>
    
9. <span data-ttu-id="64283-135">Wiederholen Sie die Schritte 5 bis 8 für weitere Bezeichnungen.</span><span class="sxs-lookup"><span data-stu-id="64283-135">Repeat steps 5-8 for your additional labels.</span></span>
    
### <a name="create-office-365-labels-with-powershell"></a><span data-ttu-id="64283-136">Erstellen von Office 365-Bezeichnungen mit PowerShell</span><span class="sxs-lookup"><span data-stu-id="64283-136">Create Office 365 labels with PowerShell</span></span>

1. <span data-ttu-id="64283-137">[Verbinden auf die Office 365-Sicherheit &amp; Compliance Center mit remote-PowerShell](http://go.microsoft.com/fwlink/?LinkID=799771&amp;clcid=0x409) und geben Sie die Anmeldeinformationen eines Kontos, das die Rolle Sicherheitsadministrator oder Unternehmensadministrator hat.</span><span class="sxs-lookup"><span data-stu-id="64283-137">[Connect to the Office 365 Security &amp; Compliance Center using remote PowerShell](http://go.microsoft.com/fwlink/?LinkID=799771&amp;clcid=0x409) and specify the credentials of an account that has the Security Administrator or Company Administrator role.</span></span>
    
2. <span data-ttu-id="64283-138">Füllen Sie die Liste der Bezeichnungsnamen aus, und führen Sie dann diese Befehle an der PowerShell-Eingabeaufforderung aus:</span><span class="sxs-lookup"><span data-stu-id="64283-138">Fill out the list of label names, and then run these commands at the PowerShell command prompt:</span></span>
    
  ```
  $labelNames=@(<list of label names, each enclosed in quotes and separated by commas>)
ForEach ($element in $labelNames){ New-ComplianceTag -Name $element }
  ```

<span data-ttu-id="64283-139">Führen Sie dann diese Schritte aus, um die neuen Office 365-Bezeichnungen zu veröffentlichen.</span><span class="sxs-lookup"><span data-stu-id="64283-139">Next, use these steps to publish the new Office 365 labels.</span></span>
  
1. <span data-ttu-id="64283-140">Aus der **Home > Etiketten** im Bereich der Sicherheit &amp; Compliance Center, klicken Sie auf **Veröffentlichen Etiketten**.</span><span class="sxs-lookup"><span data-stu-id="64283-140">From the **Home > Labels** pane the Security &amp; Compliance Center, click **Publish labels**.</span></span>
    
2. <span data-ttu-id="64283-141">Klicken Sie im Bereich **Zu veröffentlichende Bezeichnungen wählen** auf **Zu veröffentlichende Bezeichnungen wählen**</span><span class="sxs-lookup"><span data-stu-id="64283-141">On the **Choose labels to publish** pane, click **Choose labels to publish**.</span></span>
    
3. <span data-ttu-id="64283-142">Klicken Sie im Bereich **Choose labels** (Bezeichnungen auswählen) auf **Hinzufügen**, wählen Sie alle vier Bezeichnungen aus.</span><span class="sxs-lookup"><span data-stu-id="64283-142">On the **Choose labels** pane, click **Add** and select all four labels.</span></span>
    
4. <span data-ttu-id="64283-143">Klicken Sie auf **Fertig**.</span><span class="sxs-lookup"><span data-stu-id="64283-143">Click **Done**.</span></span>
    
5. <span data-ttu-id="64283-144">Klicken Sie im Bereich **Zu veröffentlichende Bezeichnungen wählen** auf **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="64283-144">On the **Choose labels to publish** pane, click **Next**.</span></span>
    
6. <span data-ttu-id="64283-145">Klicken Sie im Bereich **Speicherorte auswählen** auf **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="64283-145">On the **Choose locations** pane, click **Next**.</span></span>
    
7. <span data-ttu-id="64283-146">Klicken Sie im Bereich **Name der Richtlinie** Geben Sie im **Feld Name**einen Namen für den Satz von Etiketten, und klicken Sie dann auf **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="64283-146">On the **Name your policy** pane, type a name for your set of labels in **Name**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="64283-147">Klicken Sie im Bereich **Einstellungen überprüfen** auf **Bezeichnungen veröffentlichen**, und klicken Sie dann auf **Schließen**.</span><span class="sxs-lookup"><span data-stu-id="64283-147">On the **Review your settings** pane, click **Publish labels**, and then click **Close**.</span></span>
    
### <a name="phase-3-apply-the-office-365-labels-to-your-sharepoint-online-sites"></a><span data-ttu-id="64283-148">Phase 3: Anwenden von Office 365-Bezeichnungen auf Ihre SharePoint-Websites</span><span class="sxs-lookup"><span data-stu-id="64283-148">Phase 3: Apply the Office 365 labels to your SharePoint Online sites</span></span>

<span data-ttu-id="64283-149">Verwenden Sie die Schritte, um die Office 365-Bezeichnungen auf die Dokumentordner Ihrer SharePoint Online-Teamwebsites anzuwenden.</span><span class="sxs-lookup"><span data-stu-id="64283-149">Use these steps to apply the Office 365 labels to the documents folders of your SharePoint Online team sites.</span></span>
  
1. <span data-ttu-id="64283-150">Klicken Sie auf der Registerkarte **Microsoft Office Home** des Browsers auf die Kachel **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="64283-150">From the **Microsoft Office Home** tab of your browser, click the **SharePoint** tile.</span></span>
    
2. <span data-ttu-id="64283-151">Klicken Sie auf der neuen Registerkarte **SharePoint** in Ihrem Browser auf eine Website, der eine Office 365-Bezeichnung zugewiesen werden muss.</span><span class="sxs-lookup"><span data-stu-id="64283-151">On the new **SharePoint** tab in your browser, click a site that needs an Office 365 label assigned.</span></span>
    
3. <span data-ttu-id="64283-152">Klicken Sie auf der Registerkarte für die SharePoint-Website Ihres Browsers auf **Dokumente**.</span><span class="sxs-lookup"><span data-stu-id="64283-152">In the new SharePoint site tab of your browser, click **Documents**.</span></span>
    
4. <span data-ttu-id="64283-153">Klicken Sie auf das Symbol „Einstellungen“, und klicken Sie dann auf **Bibliothekseinstellungen**.</span><span class="sxs-lookup"><span data-stu-id="64283-153">Click the settings icon, and then click **Library settings**.</span></span>
    
5. <span data-ttu-id="64283-154">Klicken Sie unter **Berechtigungen und Verwaltung** auf **Bezeichnung auf Elemente in dieser Bibliothek anwenden**.</span><span class="sxs-lookup"><span data-stu-id="64283-154">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
6. <span data-ttu-id="64283-155">**Bezeichnung Einstellungen anwenden**wählen Sie die entsprechende Beschriftung, und klicken Sie dann auf **Speichern**.</span><span class="sxs-lookup"><span data-stu-id="64283-155">In **Settings-Apply Label**, select the appropriate label, and then click **Save**.</span></span>
    
7. <span data-ttu-id="64283-156">Schließen Sie die Registerkarte für die SharePoint-Website.</span><span class="sxs-lookup"><span data-stu-id="64283-156">Close the tab for the SharePoint Online site.</span></span>
    
8. <span data-ttu-id="64283-157">Wiederholen Sie die Schritte 3 bis 8, um Ihren zusätzlichen SharePoint Online-Websites Office 365-Bezeichnungen hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="64283-157">Repeat steps 3-8 to assign Office 365 labels to your additional SharePoint Online sites.</span></span>
    
<span data-ttu-id="64283-158">Nachfolgend sehen Sie die daraus resultierende Konfiguration.</span><span class="sxs-lookup"><span data-stu-id="64283-158">Here is your resulting configuration.</span></span>
  
![Office 365-Bezeichnungen für die vier Arten von SharePoint Online-Teamwebsites.](images/e0a4fdd2-1c30-4d93-8af4-a6f0c6c29966.png)
  
## <a name="dlp-policies-for-your-sharepoint-online-sites"></a><span data-ttu-id="64283-160">DLP-Richtlinien für Ihre SharePoint Online-Websites</span><span class="sxs-lookup"><span data-stu-id="64283-160">DLP policies for your SharePoint Online sites</span></span>

<span data-ttu-id="64283-161">Verwenden Sie diese Schritte, um eine DLP-Richtlinie zu konfigurieren, die Benutzer benachrichtigt, wenn sie ein Dokument auf einer vertraulichen SharePoint Online-Teamwebsite außerhalb einer Organisation freigeben.</span><span class="sxs-lookup"><span data-stu-id="64283-161">Use these steps to configure a DLP policy that notifies users when they share a document on a SharePoint Online sensitive team site outside the organization.</span></span>
  
1. <span data-ttu-id="64283-162">Klicken Sie auf der Registerkarte **Microsoft Office-Homepage** im Browser auf die Kachel **Security &amp; Compliance**.</span><span class="sxs-lookup"><span data-stu-id="64283-162">From the **Microsoft Office Home** tab in your browser, click the **Security &amp; Compliance** tile.</span></span>
    
2. <span data-ttu-id="64283-163">Klicken Sie auf der Registerkarte **Security &amp; Compliance** in Ihrem Browser auf **Verhinderung von Datenverlust > Richtlinie**.</span><span class="sxs-lookup"><span data-stu-id="64283-163">On the new **Security &amp; Compliance** tab in your browser, click **Data loss prevention > Policy**.</span></span>
    
3. <span data-ttu-id="64283-164">Klicken Sie im Bereich **Verhinderung von Datenverlust** auf **+ Richtlinie erstellen**.</span><span class="sxs-lookup"><span data-stu-id="64283-164">In the **Data loss prevention** pane, click **+ Create a policy**.</span></span>
    
4. <span data-ttu-id="64283-165">Klicken Sie im Bereich **Mit einer Vorlage beginnen oder eine benutzerdefinierte Richtlinie erstellen** auf **Benutzerdefiniert**, und klicken Sie dann auf **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="64283-165">In the **Start with a template or create a custom policy** pane, click **Custom**, and then click **Next**.</span></span>
    
5. <span data-ttu-id="64283-166">Klicken Sie im **Namen der Richtlinie** Geben Sie den Namen für die Ebene vertrauliche DLP-Richtlinie im **Feld Name**ein, und klicken Sie dann auf **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="64283-166">In the **Name your policy** pane, type the name for the sensitive level DLP policy in **Name**, and then click **Next**.</span></span>
    
6. <span data-ttu-id="64283-167">Klicken Sie im Bereich **Speicherorte auswählen** auf **Bestimmte Speicherorte auswählen**, und klicken Sie dann auf **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="64283-167">In the **Choose locations** pane, click **Let me choose specific locations**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="64283-168">Deaktivieren Sie in der Liste der Speicherorte **Exchange-E-Mail** und **OneDrive-Konten**, und klicken Sie dann auf **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="64283-168">In the list of locations, disable the **Exchange email** and **OneDrive accounts** locations, and then click **Next**.</span></span>
    
8. <span data-ttu-id="64283-169">Klicken Sie im Bereich **Typen von vertraulichen Informationen anpassen, die geschützt werden sollen** auf **Bearbeiten**.</span><span class="sxs-lookup"><span data-stu-id="64283-169">In the **Customize the types of sensitive info you want to protect** pane, click **Edit**.</span></span>
    
9. <span data-ttu-id="64283-170">In der **wählen Sie die Typen der Inhalte zum Schutz** Bereich, klicken Sie auf **hinzufügen** im Dropdown-Listenfeld, und klicken Sie dann auf **Etiketten**.</span><span class="sxs-lookup"><span data-stu-id="64283-170">In the **Choose the types of content to protect** pane, click **Add** in the drop-down box, and then click **Labels**.</span></span>
    
10. <span data-ttu-id="64283-171">Klicken Sie im Bereich **Bezeichnungen** auf **+ Hinzufügen**, wählen Sie die Bezeichnung **Vertraulich** aus, klicken Sie auf **Hinzufügen**, und klicken Sie dann auf **Fertig**.</span><span class="sxs-lookup"><span data-stu-id="64283-171">In the **Labels** pane, click **+ Add**, select the **Sensitive** label, click **Add**, and then click **Done**.</span></span>
    
11. <span data-ttu-id="64283-172">Klicken Sie im Bereich **Typen des zu schützenden Inhalts auswählen** auf **Speichern**.</span><span class="sxs-lookup"><span data-stu-id="64283-172">In the **Choose the types of content to protect** pane, click **Save**.</span></span>
    
12. <span data-ttu-id="64283-173">Klicken Sie im Bereich **Customize the types of sensitive info you want to protect** (Anpassen der Typen an vertraulichen Informationen, die Sie schützen möchten) auf **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="64283-173">In the **Customize the types of sensitive info you want to protect** pane, click **Next**.</span></span>
    
13. <span data-ttu-id="64283-174">Klicken Sie im Bereich **What do you want to do if we detect sensitive info?** (Was möchten Sie tun, wenn vertrauliche Informationen erkannt werden?) auf **Customize the tip and email** (Den Tipp und die E-Mail anpassen).</span><span class="sxs-lookup"><span data-stu-id="64283-174">In the **What do you want to do if we detect sensitive info?** pane, click **Customize the tip and email**.</span></span>
    
14. <span data-ttu-id="64283-175">Klicken Sie im Bereich **Customize policy tips and email notifications** (Anpassen der Richtlinientipps und der E-Mail-Benachrichtigungen) auf **Customize the policy tip text** (Den Tipptext der Richtlinie als nächstes anpassen).</span><span class="sxs-lookup"><span data-stu-id="64283-175">In the **Customize policy tips and email notifications** pane, click **Customize the policy tip text**.</span></span>
    
15. <span data-ttu-id="64283-176">Geben Sie Folgendes in das Textfeld ein, oder fügen Sie es ein:</span><span class="sxs-lookup"><span data-stu-id="64283-176">In the text box, type or paste in the following:</span></span>
    
  - <span data-ttu-id="64283-p104">Wenn Sie eine Datei für einen Benutzer außerhalb der Organisation freigeben möchten, laden Sie die Datei herunter, und öffnen Sie sie. Klicken Sie auf „Datei“ > „Dokument schützen“ > „Mit Kennwort verschlüsseln“, und geben Sie dann ein sicheres Kennwort ein. Senden Sie das Kennwort in einer separaten E-Mail oder auf andere Weise.</span><span class="sxs-lookup"><span data-stu-id="64283-p104">To share with a user outside the organization, download the file and then open it. Click File, then Protect Document, and then Encrypt with Password, and then specify a strong password. Send the password in a separate email or other means of communication.</span></span>
    
    <span data-ttu-id="64283-180">Sie können auch einen eigenen Tipp in Bezug auf die Richtlinie eingeben oder einfügen, der den Benutzern erläutert, wie sie Dateien außerhalb der Organisation freigeben.</span><span class="sxs-lookup"><span data-stu-id="64283-180">Alternately, type or paste in your own policy tip that instructs users on how to share a file outside your organization.</span></span>
    
16. <span data-ttu-id="64283-181">Klicken Sie auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="64283-181">Click **OK**.</span></span>
    
17. <span data-ttu-id="64283-182">Deaktivieren Sie im Fenster **Was möchten Sie tun, wenn vertrauliche Informationen erkannt werden?** das Kontrollkästchen **Freigeben blockieren und Zugriff auf freigegebene Inhalte einschränken**, und klicken Sie dann auf **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="64283-182">In the **What do you want to do if we detect sensitive info?** pane, clear the **Block people from sharing, and restrict access to shared content** check box, and then click **Next**.</span></span>
    
18. <span data-ttu-id="64283-183">Klicken Sie im Bereich **Möchten Sie die Richtlinie aktivieren oder zunächst testen?** auf **Ja, Richtlinie aktivieren**, und klicken Sie dann auf **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="64283-183">In the **Do you want to turn on the policy or test things out first?** pane, click **Yes, turn it on right away**, and then click **Next**.</span></span>
    
19. <span data-ttu-id="64283-184">Klicken Sie im Bereich **Einstellungen überprüfen** auf **Erstellen**, und klicken Sie dann auf **Schließen**.</span><span class="sxs-lookup"><span data-stu-id="64283-184">In the **Review your settings** pane, click **Create**, and then click **Close**.</span></span>
    
<span data-ttu-id="64283-185">Hier sehen Sie die sich ergebende Konfiguration für vertrauliche SharePoint Online-Teamwebsites.</span><span class="sxs-lookup"><span data-stu-id="64283-185">Here is your resulting configuration for sensitive SharePoint Online team sites.</span></span>
  
![DLP-Richtlinie für eine isolierte SharePoint Online-Teamwebsite mit der Office 365-Bezeichnung „Vertraulich“.](images/2ff4cc53-87a8-43e3-b637-3068d88409f3.png)
  
<span data-ttu-id="64283-187">Verwenden Sie anschließend diese Schritte, um eine DLP-Richtlinie zu konfigurieren, die Benutzer blockiert, wenn sie ein Dokument auf einer vertraulichen SharePoint Online-Teamwebsite außerhalb einer Organisation freigeben.</span><span class="sxs-lookup"><span data-stu-id="64283-187">Next, use these steps to configure a DLP policy that blocks users when they share a document on a SharePoint Online highly confidential team site outside the organization.</span></span>
  
1. <span data-ttu-id="64283-188">Klicken Sie auf der Registerkarte **Microsoft Office-Homepage** im Browser auf die Kachel **Security &amp; Compliance**.</span><span class="sxs-lookup"><span data-stu-id="64283-188">From the **Microsoft Office Home** tab in your browser, click the **Security &amp; Compliance** tile.</span></span>
    
2. <span data-ttu-id="64283-189">Klicken Sie auf der Registerkarte **Security &amp; Compliance** in Ihrem Browser auf **Verhinderung von Datenverlust > Richtlinie**.</span><span class="sxs-lookup"><span data-stu-id="64283-189">On the new **Security &amp; Compliance** tab in your browser, click **Data loss prevention > Policy**.</span></span>
    
3. <span data-ttu-id="64283-190">Klicken Sie im Bereich **Verhinderung von Datenverlust** auf **+ Richtlinie erstellen**.</span><span class="sxs-lookup"><span data-stu-id="64283-190">In the **Data loss prevention** pane, click **+ Create a policy**.</span></span>
    
4. <span data-ttu-id="64283-191">Klicken Sie im Bereich **Mit einer Vorlage beginnen oder eine benutzerdefinierte Richtlinie erstellen** auf **Benutzerdefiniert**, und klicken Sie dann auf **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="64283-191">In the **Start with a template or create a custom policy** pane, click **Custom**, and then click **Next**.</span></span>
    
5. <span data-ttu-id="64283-192">Klicken Sie im **Namen der Richtlinie** Geben Sie den Namen für die äußerst vertraulich Ebene DLP-Richtlinie im **Feld Name**ein, und klicken Sie dann auf **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="64283-192">In the **Name your policy** pane, type the name for the highly sensitive level DLP policy in **Name**, and then click **Next**.</span></span>
    
6. <span data-ttu-id="64283-193">Klicken Sie im Bereich **Speicherorte auswählen** auf **Bestimmte Speicherorte auswählen**, und klicken Sie dann auf **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="64283-193">In the **Choose locations** pane, click **Let me choose specific locations**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="64283-194">Deaktivieren Sie in der Liste der Speicherorte **Exchange-E-Mail** und **OneDrive-Konten**, und klicken Sie dann auf **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="64283-194">In the list of locations, disable the **Exchange email** and **OneDrive accounts** locations, and then click **Next**.</span></span>
    
8. <span data-ttu-id="64283-195">Klicken Sie im Bereich **Typen von vertraulichen Informationen anpassen, die geschützt werden sollen** auf **Bearbeiten**.</span><span class="sxs-lookup"><span data-stu-id="64283-195">In the **Customize the types of sensitive info you want to protect** pane, click **Edit**.</span></span>
    
9. <span data-ttu-id="64283-196">In der **wählen Sie die Typen der Inhalte zum Schutz** Bereich, klicken Sie auf **hinzufügen** im Dropdown-Listenfeld, und klicken Sie dann auf **Etiketten**.</span><span class="sxs-lookup"><span data-stu-id="64283-196">In the **Choose the types of content to protect** pane, click **Add** in the drop-down box, and then click **Labels**.</span></span>
    
10. <span data-ttu-id="64283-197">Klicken Sie im Bereich **Bezeichnungen** auf **+ Hinzufügen**, wählen Sie die Bezeichnung **Streng vertraulich** aus, klicken Sie auf **Hinzufügen**, und klicken Sie dann auf **Fertig**.</span><span class="sxs-lookup"><span data-stu-id="64283-197">In the **Labels** pane, click **+ Add**, select the **Highly Confidential** label, click **Add**, and then click **Done**.</span></span>
    
11. <span data-ttu-id="64283-198">Klicken Sie im Bereich **Typen des zu schützenden Inhalts auswählen** auf **Speichern**.</span><span class="sxs-lookup"><span data-stu-id="64283-198">In the **Choose the types of content to protect** pane, click **Save**.</span></span>
    
12. <span data-ttu-id="64283-199">Klicken Sie im Bereich **Customize the types of sensitive info you want to protect** (Anpassen der Typen an vertraulichen Informationen, die Sie schützen möchten) auf **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="64283-199">In the **Customize the types of sensitive info you want to protect** pane, click **Next**.</span></span>
    
13. <span data-ttu-id="64283-200">Klicken Sie im Bereich **What do you want to do if we detect sensitive info?** (Was möchten Sie tun, wenn vertrauliche Informationen erkannt werden?) auf **Customize the tip and email** (Den Tipp und die E-Mail anpassen).</span><span class="sxs-lookup"><span data-stu-id="64283-200">In the **What do you want to do if we detect sensitive info?** pane, click **Customize the tip and email**.</span></span>
    
14. <span data-ttu-id="64283-201">Klicken Sie im Bereich **Customize policy tips and email notifications** (Anpassen der Richtlinientipps und der E-Mail-Benachrichtigungen) auf **Customize the policy tip text** (Den Tipptext der Richtlinie als nächstes anpassen).</span><span class="sxs-lookup"><span data-stu-id="64283-201">In the **Customize policy tips and email notifications** pane, click **Customize the policy tip text**.</span></span>
    
15. <span data-ttu-id="64283-202">Geben Sie Folgendes in das Textfeld ein, oder fügen Sie es ein:</span><span class="sxs-lookup"><span data-stu-id="64283-202">In the text box, type or paste in the following:</span></span>
    
  - <span data-ttu-id="64283-p105">Wenn Sie eine Datei für einen Benutzer außerhalb der Organisation freigeben möchten, laden Sie die Datei herunter, und öffnen Sie sie. Klicken Sie auf „Datei“ > „Dokument schützen“ > „Mit Kennwort verschlüsseln“, und geben Sie dann ein sicheres Kennwort ein. Senden Sie das Kennwort in einer separaten E-Mail oder auf andere Weise.</span><span class="sxs-lookup"><span data-stu-id="64283-p105">To share with a user outside the organization, download the file and then open it. Click File, then Protect Document, and then Encrypt with Password, and then specify a strong password. Send the password in a separate email or other means of communication.</span></span>
    
    <span data-ttu-id="64283-206">Sie können auch einen eigenen Tipp in Bezug auf die Richtlinie eingeben oder einfügen, der den Benutzern erläutert, wie sie Dateien außerhalb der Organisation freigeben.</span><span class="sxs-lookup"><span data-stu-id="64283-206">Alternately, type or paste in your own policy tip that instructs users on how to share a file outside your organization.</span></span>
    
16. <span data-ttu-id="64283-207">Klicken Sie auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="64283-207">Click **OK**.</span></span>
    
17. <span data-ttu-id="64283-208">Wählen Sie im Bereich **Was möchten Sie tun, wenn vertrauliche Informationen erkannt werden?** die Option **Begründung für Außerkraftsetzung erforderlich**, und klicken Sie dann auf **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="64283-208">In the **What do you want to do if we detect sensitive info?** pane, select **Require a business justification to override**, and then click **Next**.</span></span>
    
18. <span data-ttu-id="64283-209">Klicken Sie im Bereich **Möchten Sie die Richtlinie aktivieren oder zunächst testen?** auf **Ja, Richtlinie aktivieren**, und klicken Sie dann auf **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="64283-209">In the **Do you want to turn on the policy or test things out first?** pane, click **Yes, turn it on right away**, and then click **Next**.</span></span>
    
19. <span data-ttu-id="64283-210">Klicken Sie im Bereich **Einstellungen überprüfen** auf **Erstellen**, und klicken Sie dann auf **Schließen**.</span><span class="sxs-lookup"><span data-stu-id="64283-210">In the **Review your settings** pane, click **Create**, and then click **Close**.</span></span>
    
<span data-ttu-id="64283-211">Hier sehen Sie die sich ergebende Konfiguration für streng vertrauliche SharePoint Online-Teamwebsites.</span><span class="sxs-lookup"><span data-stu-id="64283-211">Here is your resulting configuration for high confidentiality SharePoint Online team sites.</span></span>
  
![DLP-Richtlinie für eine isolierte SharePoint Online-Teamwebsite mit der Office 365-Bezeichnung „Streng vertraulich“.](images/f705d3d0-23c9-4333-8b70-ad3b91f835ea.png)
  
## <a name="next-step"></a><span data-ttu-id="64283-213">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="64283-213">Next step</span></span>

[<span data-ttu-id="64283-214">Schützen von SharePoint Online-Dateien mit Azure Information Protection</span><span class="sxs-lookup"><span data-stu-id="64283-214">Protect SharePoint Online files with Azure Information Protection</span></span>](protect-sharepoint-online-files-with-azure-information-protection.md)
    
## <a name="see-also"></a><span data-ttu-id="64283-215">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="64283-215">See Also</span></span>

[<span data-ttu-id="64283-216">Sichern von SharePoint Online-Websites und -Dateien</span><span class="sxs-lookup"><span data-stu-id="64283-216">Secure SharePoint Online sites and files</span></span>](secure-sharepoint-online-sites-and-files.md)
  
[<span data-ttu-id="64283-217">Sichern von SharePoint Online-Websites in einer Entwicklungs-/Testumgebung</span><span class="sxs-lookup"><span data-stu-id="64283-217">Secure SharePoint Online sites in a dev/test environment</span></span>](secure-sharepoint-online-sites-in-a-dev-test-environment.md)
  
[<span data-ttu-id="64283-218">Microsoft-Sicherheitsleitfaden für politische Kampagnen, gemeinnützigen Organisationen und andere agile Organisationen</span><span class="sxs-lookup"><span data-stu-id="64283-218">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[<span data-ttu-id="64283-219">Cloudakzeptanz und Hybridlösungen</span><span class="sxs-lookup"><span data-stu-id="64283-219">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)


