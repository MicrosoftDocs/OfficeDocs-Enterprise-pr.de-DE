---
title: "Schützen von SharePoint Online-Dateien mit Azure Information Protection"
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
- Ent_Solutions
ms.assetid: 5b9c8e41-25d2-436d-89bb-9aecb9ec2b80
description: "Zusammenfassung: Verwenden Sie Azure Information Protection zum Schützen von Dateien auf einer streng vertraulichen SharePoint Online-Teamwebsite."
ms.openlocfilehash: 5beba188cadc88c15ec75ed2adb4899d9b41b8ec
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/09/2018
---
# <a name="protect-sharepoint-online-files-with-azure-information-protection"></a><span data-ttu-id="91a4e-103">Schützen von SharePoint Online-Dateien mit Azure Information Protection</span><span class="sxs-lookup"><span data-stu-id="91a4e-103">Protect SharePoint Online files with Azure Information Protection</span></span>

 <span data-ttu-id="91a4e-104">**Zusammenfassung:** Verwenden Sie Azure Information Protection zum Schützen von Dateien auf einer streng vertraulichen SharePoint Online-Teamwebsite.</span><span class="sxs-lookup"><span data-stu-id="91a4e-104">**Summary:** Apply Azure Information Protection to protect files in a highly confidential SharePoint Online team site.</span></span>
  
<span data-ttu-id="91a4e-p101">Konfigurieren Sie anhand der Schritte in diesem Artikel Azure Information Protection, um Verschlüsselung und Berechtigungen auf Dateien in einer streng vertraulichen SharePoint Online-Teamwebsite zu konfigurieren. Der Verschlüsselungs- und Berechtigungsschutz einer Datei bleibt auch dann bestehen, wenn die Datei von der Website heruntergeladen wird. Weitere Informationen zu streng vertraulichen SharePoint Online-Teamwebsites finden Sie unter [Sichern von SharePoint Online-Websites und -Dateien](secure-sharepoint-online-sites-and-files.md).</span><span class="sxs-lookup"><span data-stu-id="91a4e-p101">Use the steps in this article to configure Azure Information Protection to provide encryption and permissions for files in a highly confidential SharePoint Online team site. The encryption and permissions protection travels with a file even when it is downloaded from the site. For more information about highly confidential SharePoint Online team sites, see [Secure SharePoint Online sites and files](secure-sharepoint-online-sites-and-files.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="91a4e-p102">Wenn Azure Information Protection-Verschlüsselung auf Dateien in Office 365 angewendet wird, kann der Dienst den Inhalt dieser Dateien nicht verarbeiten. Gemeinsame Dokumenterstellung, eDiscovery, Suche, Delve und andere Features für die Zusammenarbeit funktionieren nicht. DLP-Richtlinien können nur auf die Metadaten (einschließlich Office 365-Bezeichnungen) angewendet werden, aber nicht auf den Inhalt dieser Dateien (z. B. Kreditkartennummern in Dateien).</span><span class="sxs-lookup"><span data-stu-id="91a4e-p102">When Azure Information Protection encryption is applied to files stored in Office 365, the service cannot process the contents of these files. Co-authoring, eDiscovery, search, Delve, and other collaborative features do not work. Data Loss Prevention (DLP) policies can only work with the metadata (including Office 365 labels) but not the contents of these files (such as credit card numbers within files).</span></span> 
  
<span data-ttu-id="91a4e-111">Befolgen Sie zuerst die Anweisungen unter [Aktivieren von Azure Rights Management über Office 365 Admin Center](https://docs.microsoft.com/information-protection/deploy-use/activate-office365) für Ihr Office 365-Abonnement.</span><span class="sxs-lookup"><span data-stu-id="91a4e-111">First, use the instructions in [Activate Azure RMS with the Office 365 admin center](https://docs.microsoft.com/information-protection/deploy-use/activate-office365) for your Office 365 subscription.</span></span>
  
<span data-ttu-id="91a4e-112">Konfigurieren Sie anschließend Azure Information Protection mit einer neuen bereichsbezogenen Richtlinie und einer untergeordneten Bezeichnung mit dem Schutz und den Berechtigungen für die streng vertrauliche SharePoint Online-Teamwebsite.</span><span class="sxs-lookup"><span data-stu-id="91a4e-112">Next, configure Azure Information Protection with a new scoped policy and sub-label for protection and permissions of your highly confidential SharePoint Online team site.</span></span>
  
1. <span data-ttu-id="91a4e-p103">Melden Sie sich mit einem Konto beim Office 365-Portal an, das über die Rolle „Sicherheitsadministrator" oder Unternehmensadministrator" verfügt. Hilfe finden Sie unter [Wo kann ich mich bei Office 365 Business anmelden?](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="91a4e-p103">Sign in to the Office 365 portal with an account that has the Security Administrator or Company Administrator role. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="91a4e-115">Wechseln Sie auf einer separaten Registerkarte im Browser zum Azure-Portal unter [https://portal.azure.com](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="91a4e-115">In a separate tab of your browser, go to the Azure portal ([https://portal.azure.com](https://portal.azure.com)).</span></span>
    
3. <span data-ttu-id="91a4e-116">Wenn Sie Azure Information Protection zum ersten Mal konfigurieren, befolgen Sie diese [Anweisungen](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time).</span><span class="sxs-lookup"><span data-stu-id="91a4e-116">If this is the first time you are configuring Azure Information Protection, see these [instructions](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time).</span></span>
    
4. <span data-ttu-id="91a4e-117">Klicken Sie im Listenbereich auf **Weitere Dienste**, geben Sie **Information** ein, und klicken Sie dann auf **Azure Information Protection**.</span><span class="sxs-lookup"><span data-stu-id="91a4e-117">In the list pane, click **More services**, type **information**, and then click **Azure Information Protection**.</span></span>
    
5. <span data-ttu-id="91a4e-118">Klicken Sie auf dem Blatt **Azure Information Protection** auf **Bereichsbezogene Richtlinien > + Neue Richtlinie hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="91a4e-118">On the **Azure Information protection** blade, , click **Scoped policies > + Add a new policy**.</span></span>
    
6. <span data-ttu-id="91a4e-119">Geben Sie unter **Richtlinienname** einen Namen für die neue Richtlinie und unter **Beschreibung** eine Beschreibung ein.</span><span class="sxs-lookup"><span data-stu-id="91a4e-119">Type a name for the new policy in **Policy name** and a description in **Description**.</span></span>
    
7. <span data-ttu-id="91a4e-120">Klicken Sie auf **Auswählen, welche Benutzer oder Gruppen diese Richtlinie erhalten > Benutzer/Gruppen**, und wählen Sie dann die Websitemitglieder-Zugriffsgruppe für Ihre streng vertrauliche SharePoint Online-Teamwebsite aus.</span><span class="sxs-lookup"><span data-stu-id="91a4e-120">Click **Select which users or groups get this policy > User/Groups**, and then select the site members access group for your highly sensitive SharePoint Online team site.</span></span> 
    
8. <span data-ttu-id="91a4e-121">Klicken Sie auf **Auswählen > OK**.</span><span class="sxs-lookup"><span data-stu-id="91a4e-121">Click **Select > OK**.</span></span>
    
9. <span data-ttu-id="91a4e-122">Klicken Sie für die Bezeichnung **Streng vertraulich** auf die Auslassungspunkte (...), und klicken Sie dann auf **Unterbezeichnung hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="91a4e-122">For the **Highly Confidential** label, click the ellipses (…), and then click **Add a sub-label**.</span></span>
    
10. <span data-ttu-id="91a4e-123">Geben Sie unter **Name** einen Namen für die Unterbezeichnung und unter **Beschreibung** eine Beschreibung für die Bezeichnung ein.</span><span class="sxs-lookup"><span data-stu-id="91a4e-123">Type a name for the sub-label in **Name** and a description of the label in **Description**.</span></span>
    
11. <span data-ttu-id="91a4e-124">Klicken Sie unter **Berechtigungen für Dokumente und E-Mails mit dieser Bezeichnung festlegen** auf **Schützen**.</span><span class="sxs-lookup"><span data-stu-id="91a4e-124">In **Set permissions for documents and emails containing this label**, click **Protect**.</span></span>
    
12. <span data-ttu-id="91a4e-125">Klicken Sie im Abschnitt **Schutz** auf **Azure (Cloudschlüssel)**.</span><span class="sxs-lookup"><span data-stu-id="91a4e-125">In the **Protection** section, click **Azure (cloud key)**.</span></span>
    
13. <span data-ttu-id="91a4e-126">Klicken Sie im Blatt **Schützen** unter **Schutzeinstellungen** auf **+ Berechtigungen hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="91a4e-126">On the **Protection** blade, under **Protection settings**, click **+ Add permissions**.</span></span>
    
14. <span data-ttu-id="91a4e-127">Klicken Sie auf dem Blatt **Berechtigungen hinzufügen** unter **Benutzer und Gruppen angeben** auf **+ Verzeichnis durchsuchen**.</span><span class="sxs-lookup"><span data-stu-id="91a4e-127">On the **Add permissions** blade, under **Specify users and groups**, click **+ Browse directory**.</span></span>
    
15. <span data-ttu-id="91a4e-128">Wählen Sie im Bereich **AAD-Benutzer und -Gruppen** die Websitemitglieder-Zugriffsgruppe für Ihre streng vertrauliche SharePoint Online-Teamwebsite aus, und klicken Sie dann auf **Auswählen**.</span><span class="sxs-lookup"><span data-stu-id="91a4e-128">On the **AAD Users and Groups** pane, select the site members access group for your highly sensitive SharePoint Online team site, and then click **Select**.</span></span>
    
16. <span data-ttu-id="91a4e-129">Deaktivieren Sie unter **Aus voreingestellten Berechtigungen wählen** die Kontrollkästchen **Drucken**, **Inhalte kopieren und extrahieren** und **Weiterleiten**.</span><span class="sxs-lookup"><span data-stu-id="91a4e-129">Under **Choose permissions from the preset**, clear the **Print**, **Copy and extract content**, and **Forward** check boxes.</span></span>
    
17. <span data-ttu-id="91a4e-130">Klicken Sie zweimal auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="91a4e-130">Click **OK** twice.</span></span>
    
18. <span data-ttu-id="91a4e-131">Klicken Sie auf dem Blatt **Untergeordnete Bezeichnung** auf **Speichern**.</span><span class="sxs-lookup"><span data-stu-id="91a4e-131">On the **Sub-label** blade, click **Save**.</span></span>
    
19. <span data-ttu-id="91a4e-132">Schließen Sie das Blatt für die neue bereichsbezogene Richtlinie.</span><span class="sxs-lookup"><span data-stu-id="91a4e-132">Close the new scoped policy blade.</span></span>
    
20. <span data-ttu-id="91a4e-133">Klicken Sie auf dem Blatt **Azure Information Protection - Bereichsbezogene Richtlinien** auf **Veröffentlichen**.</span><span class="sxs-lookup"><span data-stu-id="91a4e-133">On the **Azure Information protection - Scoped policies** blade, click **Publish**.</span></span>
    
<span data-ttu-id="91a4e-134">Dies ist die resultierende Konfiguration für Ihre streng vertrauliche SharePoint Online-Teamwebsite.</span><span class="sxs-lookup"><span data-stu-id="91a4e-134">This is your resulting configuration for your highly confidential SharePoint Online team site.</span></span>
  
![Bezeichnung „Azure Information Protection“ für eine isolierte SharePoint Online-Teamwebsite.](images/8cc92aa4-e7bc-4c2f-a4a4-3b034b21aebf.png)
  
<span data-ttu-id="91a4e-136">Sie können jetzt damit beginnen, Dokumente zu erstellen und diese mit Azure Information Protection und der neuen Bezeichnung zu schützen.</span><span class="sxs-lookup"><span data-stu-id="91a4e-136">You are now ready to begin creating documents and protecting them with Azure Information Protection and your new label.</span></span>
  
<span data-ttu-id="91a4e-p104">Sie müssen den [Azure Information Protection-Client](https://docs.microsoft.com/information-protection/rms-client/install-client-app) auf Ihrem Gerät oder Ihrem Windows-Computer installieren. Sie können ein Skript erstellen und die Installation automatisieren, oder Benutzer können den Client manuell installieren. Informationen finden Sie in den folgenden Ressourcen:</span><span class="sxs-lookup"><span data-stu-id="91a4e-p104">You must [install the Azure Information Protection client](https://docs.microsoft.com/information-protection/rms-client/install-client-app) on your device or Windows-based computer. You can script and automate the installation, or users can install the client manually. See the following resources:</span></span>
  
- [<span data-ttu-id="91a4e-140">Die Clientseite von Azure Information Protection</span><span class="sxs-lookup"><span data-stu-id="91a4e-140">The client side of Azure Information Protection</span></span>](https://docs.microsoft.com/information-protection/rms-client/use-client)
    
- [<span data-ttu-id="91a4e-141">Installieren des Azure Information Protection-Clients</span><span class="sxs-lookup"><span data-stu-id="91a4e-141">Installing the Azure Information Protection client</span></span>](https://docs.microsoft.com/information-protection/rms-client/client-admin-guide)
    
- [<span data-ttu-id="91a4e-142">Downloadseite für die manuelle Installation</span><span class="sxs-lookup"><span data-stu-id="91a4e-142">Download page for manual installation</span></span>](https://www.microsoft.com/download/details.aspx?id=53018)
    
<span data-ttu-id="91a4e-p105">Nach der Installation führen die Benutzer eine Office-Anwendung (wie z. B. Microsoft Word) aus und melden sich von dort aus mit Ihrem Office 365-Konto an. Die neue Symbolleiste **Information Protection** ermöglicht es Benutzern, die neue Bezeichnung auszuwählen. Stellen Sie sicher, dass Ihre Benutzer die SharePoint Online-Teamwebsite kennen und wissen, welche Bezeichnung sie verwenden müssen, um ihre streng vertraulichen Dateien zu schützen.</span><span class="sxs-lookup"><span data-stu-id="91a4e-p105">Once installed, your users run and then sign-in from an Office application (such as Microsoft Word) with their Office 365 account. A new **Information Protection** bar allows users to select the new label. Make sure that your users know the SharePoint Online team site and which label to use, to protect their highly confidential files.</span></span>
  
> [!NOTE]
> <span data-ttu-id="91a4e-146">Wenn Sie über mehrere streng vertrauliche SharePoint Online-Teamwebsites verfügen, müssen Sie anhand der oben aufgeführten Einstellungen mehrere bereichsbezogene Azure Information Protection-Richtlinien mit Unterbezeichnungen erstellen, wobei die Berechtigungen für jede Unterbezeichnung auf die Websitemitglieder-Zugriffsgruppe einer bestimmten SharePoint Online-Teamwebsite festgelegt sind.</span><span class="sxs-lookup"><span data-stu-id="91a4e-146">If you have multiple highly sensitive SharePoint Online team sites, you should create multiple Azure Information Protection scoped policies with sub-labels with the above settings, with the permissions for each sub-label set to the site members access group of a specific SharePoint Online team site.</span></span> 
  
## <a name="see-also"></a><span data-ttu-id="91a4e-147">Weitere Artikel</span><span class="sxs-lookup"><span data-stu-id="91a4e-147">See Also</span></span>

[<span data-ttu-id="91a4e-148">Sichern von SharePoint Online-Websites und -Dateien</span><span class="sxs-lookup"><span data-stu-id="91a4e-148">Secure SharePoint Online sites and files</span></span>](secure-sharepoint-online-sites-and-files.md)
  
[<span data-ttu-id="91a4e-149">Sichern von SharePoint Online-Websites in einer Entwicklungs-/Testumgebung</span><span class="sxs-lookup"><span data-stu-id="91a4e-149">Secure SharePoint Online sites in a dev/test environment</span></span>](secure-sharepoint-online-sites-in-a-dev-test-environment.md)
  
[<span data-ttu-id="91a4e-150">Microsoft-Sicherheitsleitfaden für politische Kampagnen, gemeinnützigen Organisationen und andere agile Organisationen</span><span class="sxs-lookup"><span data-stu-id="91a4e-150">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[<span data-ttu-id="91a4e-151">Cloudakzeptanz und Hybridlösungen</span><span class="sxs-lookup"><span data-stu-id="91a4e-151">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)




