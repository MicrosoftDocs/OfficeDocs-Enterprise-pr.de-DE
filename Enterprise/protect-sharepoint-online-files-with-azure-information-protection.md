---
title: Schützen von SharePoint Online-Dateien mit Azure Information Protection
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_Solutions
ms.assetid: 5b9c8e41-25d2-436d-89bb-9aecb9ec2b80
description: 'Zusammenfassung: Verwenden Sie Azure Information Protection zum Schützen von Dateien auf einer streng vertraulichen SharePoint Online-Teamwebsite.'
ms.openlocfilehash: 2c4776f5795a5a0b07be0f04b4872abadb4d31ca
ms.sourcegitcommit: b39b8ae3b4268d6475b54e2fdb62982b2c7d9943
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/12/2018
ms.locfileid: "20319286"
---
# <a name="protect-sharepoint-online-files-with-azure-information-protection"></a><span data-ttu-id="725b8-103">Schützen von SharePoint Online-Dateien mit Azure Information Protection</span><span class="sxs-lookup"><span data-stu-id="725b8-103">Protect SharePoint Online files with Azure Information Protection</span></span>

 <span data-ttu-id="725b8-104">**Zusammenfassung:** Verwenden Sie Azure Information Protection zum Schützen von Dateien auf einer streng vertraulichen SharePoint Online-Teamwebsite.</span><span class="sxs-lookup"><span data-stu-id="725b8-104">**Summary:** Apply Azure Information Protection to protect files in a highly confidential SharePoint Online team site.</span></span>
  
<span data-ttu-id="725b8-p101">Konfigurieren Sie anhand der Schritte in diesem Artikel Azure Information Protection, um eine Verschlüsselung und Berechtigungen für Dateien bereitzustellen. Die Dateien können zu einer SharePoint-Bibliothek hinzugefügt werden, die für die Schutzebene „streng vertraulich“ konfiguriert wurde. Sie können eine Datei auch direkt über die Website öffnen und den Azure Information Protection-Client verwenden, um eine Verschlüsselung hinzuzufügen. Der Verschlüsselungs- und Berechtigungsschutz einer Datei bleibt auch dann bestehen, wenn die Datei von der Website heruntergeladen wird.</span><span class="sxs-lookup"><span data-stu-id="725b8-p101">Use the steps in this article to configure Azure Information Protection to provide encryption and permissions for files. These files can be added to a SharePoint library configured for highly confidential protection. Or, you can open a file directly from the site and use the Azure Information Protection client to add encryption. The encryption and permissions protection travels with a file even when it is downloaded from the site.</span></span> 

<span data-ttu-id="725b8-p102">Diese Schritte sind Teil einer umfangreicheren Lösung zur Konfiguration eines Schutzes streng vertraulicher Daten für SharePoint-Websites und die Dateien innerhalb dieser Websites. Weitere Informationen finden Sie unter [Sichern von SharePoint Online-Websites und -Dateien](secure-sharepoint-online-sites-and-files.md).</span><span class="sxs-lookup"><span data-stu-id="725b8-p102">These steps are part of a larger solution for configuring highly confidential protection for SharePoint sites and the files within these sites. For more information, see [Secure SharePoint Online sites and files](secure-sharepoint-online-sites-and-files.md).</span></span> 

<span data-ttu-id="725b8-111">Die Verwendung von Azure Information Protection für Dateien in SharePoint Online wird nicht für alle Benutzer empfohlen, sie ist jedoch eine Option für Kunden, die für eine Teilmenge von Dateien diese Ebene des Schutzes benötigen.</span><span class="sxs-lookup"><span data-stu-id="725b8-111">Using Azure Information Protection for files in SharePoint Online is not recommended for all customers, but is an option for customers who need this level of protection for a subset of files.</span></span>

<span data-ttu-id="725b8-112">Einige wichtige Hinweise zu dieser Lösung:</span><span class="sxs-lookup"><span data-stu-id="725b8-112">Some important notes about this solution:</span></span>
- <span data-ttu-id="725b8-p103">Wenn Azure Information Protection-Verschlüsselung auf Dateien in Office 365 angewendet wird, kann der Dienst den Inhalt dieser Dateien nicht verarbeiten. Gemeinsame Dokumenterstellung, eDiscovery, Suche, Delve und andere Features für die Zusammenarbeit funktionieren nicht. DLP-Richtlinien können nur auf die Metadaten (einschließlich Office 365-Bezeichnungen) angewendet werden, aber nicht auf den Inhalt dieser Dateien (z. B. Kreditkartennummern in Dateien).</span><span class="sxs-lookup"><span data-stu-id="725b8-p103">When Azure Information Protection encryption is applied to files stored in Office 365, the service cannot process the contents of these files. Co-authoring, eDiscovery, search, Delve, and other collaborative features do not work. Data Loss Prevention (DLP) policies can only work with the metadata (including Office 365 labels) but not the contents of these files (such as credit card numbers within files).</span></span>
- <span data-ttu-id="725b8-p104">Bei dieser Lösung muss ein Benutzer eine Bezeichnung auswählen, die den Schutz von Azure Information Protection anwendet. Wenn Sie eine automatische Verschlüsselung benötigen und SharePoint die Dateien indizieren und überprüfen soll, sollten Sie die Verwaltung von Informationsrechten (Information Rights Management, IRM) in SharePoint Online in Betracht ziehen. Wenn Sie eine SharePoint-Bibliothek für IRM konfigurieren, werden die Dateien automatisch beim Herunterladen für die Bearbeitung verschlüsselt. Für SharePoint IRM gelten einige Einschränkungen, die Ihre Entscheidung beeinflussen könnten. Weitere Informationen finden Sie unter [Einrichten von Information Rights Management (IRM) im SharePoint Admin Center](https://support.office.com/de-DE/article/Set-up-Information-Rights-Management-IRM-in-SharePoint-admin-center-239CE6EB-4E81-42DB-BF86-A01362FED65C).</span><span class="sxs-lookup"><span data-stu-id="725b8-p104">This solution requires a user to select a label that applies the protection from Azure Information Protection. If you require automatic encryption and the ability for SharePoint to index and inspect the files, consider using Information Rights Management (IRM) in SharePoint Online. When you configure a SharePoint library for IRM, files are automatically encrypted when they are downloaded for editing.  SharePoint IRM includes limitations that might influence your decision. For more information, see [Set up Information Rights Management (IRM) in SharePoint admin center](https://support.office.com/de-DE/article/Set-up-Information-Rights-Management-IRM-in-SharePoint-admin-center-239CE6EB-4E81-42DB-BF86-A01362FED65C).</span></span>

##<a name="admin-setup"></a><span data-ttu-id="725b8-121">Einrichten eines Administrators</span><span class="sxs-lookup"><span data-stu-id="725b8-121">Admin setup</span></span>
<span data-ttu-id="725b8-122">Befolgen Sie zuerst die Anweisungen unter [Aktivieren von Azure Rights Management über Office 365 Admin Center](https://docs.microsoft.com/information-protection/deploy-use/activate-office365) für Ihr Office 365-Abonnement.</span><span class="sxs-lookup"><span data-stu-id="725b8-122">First, use the instructions in [Activate Azure RMS with the Office 365 admin center](https://docs.microsoft.com/information-protection/deploy-use/activate-office365) for your Office 365 subscription.</span></span>
  
<span data-ttu-id="725b8-123">Konfigurieren Sie anschließend Azure Information Protection mit einer neuen bereichsbezogenen Richtlinie und einer untergeordneten Bezeichnung mit dem Schutz und den Berechtigungen für die streng vertrauliche SharePoint Online-Teamwebsite.</span><span class="sxs-lookup"><span data-stu-id="725b8-123">Next, configure Azure Information Protection with a new scoped policy and sub-label for protection and permissions of your highly confidential SharePoint Online team site.</span></span>
  
1. <span data-ttu-id="725b8-p105">Melden Sie sich mit einem Konto beim Office 365-Portal an, das über die Rolle „Sicherheitsadministrator" oder Unternehmensadministrator" verfügt. Hilfe finden Sie unter [Wo kann ich mich bei Office 365 Business anmelden?](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="725b8-p105">Sign in to the Office 365 portal with an account that has the Security Administrator or Company Administrator role. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="725b8-126">Wechseln Sie auf einer separaten Registerkarte im Browser zum Azure-Portal unter [https://portal.azure.com](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="725b8-126">In a separate tab of your browser, go to the Azure portal ([https://portal.azure.com](https://portal.azure.com)).</span></span>
    
3. <span data-ttu-id="725b8-127">Wenn Sie Azure Information Protection zum ersten Mal konfigurieren, befolgen Sie diese [Anweisungen](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time).</span><span class="sxs-lookup"><span data-stu-id="725b8-127">If this is the first time you are configuring Azure Information Protection, see these [instructions](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time).</span></span>
    
4. <span data-ttu-id="725b8-128">Klicken Sie im Listenbereich auf **Alle Dienste**, geben Sie **Information** ein, und klicken Sie dann auf **Azure Information Protection**.</span><span class="sxs-lookup"><span data-stu-id="725b8-128">In the list pane, click **All services**, type **information**, and then click **Azure Information Protection**.</span></span>
    
5. <span data-ttu-id="725b8-129">Klicken Sie auf dem Blatt **Azure Information Protection** auf **Bereichsbezogene Richtlinien > + Neue Richtlinie hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="725b8-129">On the **Azure Information protection** blade, , click **Scoped policies > + Add a new policy**.</span></span>
    
6. <span data-ttu-id="725b8-130">Geben Sie unter **Richtlinienname** einen Namen für die neue Richtlinie und unter **Beschreibung** eine Beschreibung ein.</span><span class="sxs-lookup"><span data-stu-id="725b8-130">Type a name for the new policy in **Policy name** and a description in **Description**.</span></span>
    
7. <span data-ttu-id="725b8-131">Klicken Sie auf **Auswählen, welche Benutzer oder Gruppen diese Richtlinie erhalten > Benutzer/Gruppen**, und wählen Sie dann die Websitemitglieder-Zugriffsgruppe für Ihre streng vertrauliche SharePoint Online-Teamwebsite aus.</span><span class="sxs-lookup"><span data-stu-id="725b8-131">Click **Select which users or groups get this policy > User/Groups**, and then select the site members access group for your highly sensitive SharePoint Online team site.</span></span> 
    
8. <span data-ttu-id="725b8-132">Klicken Sie auf **Auswählen > OK**.</span><span class="sxs-lookup"><span data-stu-id="725b8-132">Click **Select > OK**.</span></span>
    
9. <span data-ttu-id="725b8-133">Klicken Sie für die Bezeichnung **Streng vertraulich** auf die Auslassungspunkte (...), und klicken Sie dann auf **Unterbezeichnung hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="725b8-133">For the **Highly Confidential** label, click the ellipses (…), and then click **Add a sub-label**.</span></span>
    
10. <span data-ttu-id="725b8-134">Geben Sie unter **Name** einen Namen für die Unterbezeichnung und unter **Beschreibung** eine Beschreibung für die Bezeichnung ein.</span><span class="sxs-lookup"><span data-stu-id="725b8-134">Type a name for the sub-label in **Name** and a description of the label in **Description**.</span></span>
    
11. <span data-ttu-id="725b8-135">Klicken Sie unter **Berechtigungen für Dokumente und E-Mails mit dieser Bezeichnung festlegen** auf **Schützen**.</span><span class="sxs-lookup"><span data-stu-id="725b8-135">In **Set permissions for documents and emails containing this label**, click **Protect**.</span></span>
    
12. <span data-ttu-id="725b8-136">Klicken Sie im Abschnitt **Schutz** auf **Azure (Cloudschlüssel)**.</span><span class="sxs-lookup"><span data-stu-id="725b8-136">In the **Protection** section, click **Azure (cloud key)**.</span></span>
    
13. <span data-ttu-id="725b8-137">Klicken Sie im Blatt **Schützen** unter **Schutzeinstellungen** auf **+ Berechtigungen hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="725b8-137">On the **Protection** blade, under **Protection settings**, click **+ Add permissions**.</span></span>
    
14. <span data-ttu-id="725b8-138">Klicken Sie auf dem Blatt **Berechtigungen hinzufügen** unter **Benutzer und Gruppen angeben** auf **+ Verzeichnis durchsuchen**.</span><span class="sxs-lookup"><span data-stu-id="725b8-138">On the **Add permissions** blade, under **Specify users and groups**, click **+ Browse directory**.</span></span>
    
15. <span data-ttu-id="725b8-139">Wählen Sie im Bereich **AAD-Benutzer und -Gruppen** die Websitemitglieder-Zugriffsgruppe für Ihre streng vertrauliche SharePoint Online-Teamwebsite aus, und klicken Sie dann auf **Auswählen**.</span><span class="sxs-lookup"><span data-stu-id="725b8-139">On the **AAD Users and Groups** pane, select the site members access group for your highly sensitive SharePoint Online team site, and then click **Select**.</span></span>
    
16. <span data-ttu-id="725b8-140">Deaktivieren Sie unter **Aus voreingestellten Berechtigungen wählen** die Kontrollkästchen **Drucken**, **Inhalte kopieren und extrahieren** und **Weiterleiten**.</span><span class="sxs-lookup"><span data-stu-id="725b8-140">Under **Choose permissions from the preset**, clear the **Print**, **Copy and extract content**, and **Forward** check boxes.</span></span>
    
17. <span data-ttu-id="725b8-141">Klicken Sie zweimal auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="725b8-141">Click **OK** twice.</span></span>
    
18. <span data-ttu-id="725b8-142">Klicken Sie auf dem Blatt **Untergeordnete Bezeichnung** auf **Speichern**.</span><span class="sxs-lookup"><span data-stu-id="725b8-142">On the **Sub-label** blade, click **Save**.</span></span>
    
19. <span data-ttu-id="725b8-143">Schließen Sie das Blatt für die neue bereichsbezogene Richtlinie.</span><span class="sxs-lookup"><span data-stu-id="725b8-143">Close the new scoped policy blade.</span></span>
    
20. <span data-ttu-id="725b8-144">Klicken Sie auf dem Blatt **Azure Information Protection – Bereichsbezogene Richtlinien** auf **Veröffentlichen**.</span><span class="sxs-lookup"><span data-stu-id="725b8-144">On the **Azure Information protection - Scoped policies** blade, click **Publish**.</span></span>
    
 
##<a name="client-setup"></a><span data-ttu-id="725b8-145">Einrichten eines Clients</span><span class="sxs-lookup"><span data-stu-id="725b8-145">Client setup</span></span>
<span data-ttu-id="725b8-146">Sie können jetzt damit beginnen, Dokumente zu erstellen und diese mit Azure Information Protection und der neuen Bezeichnung zu schützen.</span><span class="sxs-lookup"><span data-stu-id="725b8-146">You are now ready to begin creating documents and protecting them with Azure Information Protection and your new label.</span></span>
  
<span data-ttu-id="725b8-p106">Sie müssen den [Azure Information Protection-Client](https://docs.microsoft.com/information-protection/rms-client/install-client-app) auf Ihrem Gerät oder Ihrem Windows-Computer installieren. Sie können ein Skript erstellen und die Installation automatisieren, oder Benutzer können den Client manuell installieren. Informationen finden Sie in den folgenden Ressourcen:</span><span class="sxs-lookup"><span data-stu-id="725b8-p106">You must [install the Azure Information Protection client](https://docs.microsoft.com/information-protection/rms-client/install-client-app) on your device or Windows-based computer. You can script and automate the installation, or users can install the client manually. See the following resources:</span></span>
  
- [<span data-ttu-id="725b8-150">Die Clientseite von Azure Information Protection</span><span class="sxs-lookup"><span data-stu-id="725b8-150">The client side of Azure Information Protection</span></span>](https://docs.microsoft.com/information-protection/rms-client/use-client)
    
- [<span data-ttu-id="725b8-151">Installieren des Azure Information Protection-Clients</span><span class="sxs-lookup"><span data-stu-id="725b8-151">Installing the Azure Information Protection client</span></span>](https://docs.microsoft.com/information-protection/rms-client/client-admin-guide)
    
- [<span data-ttu-id="725b8-152">Downloadseite für die manuelle Installation</span><span class="sxs-lookup"><span data-stu-id="725b8-152">Download page for manual installation</span></span>](https://www.microsoft.com/download/details.aspx?id=53018)
    
<span data-ttu-id="725b8-p107">Nach der Installation führen die Benutzer eine Office-Anwendung (wie z. B. Microsoft Word) aus und melden sich von dort aus mit Ihrem Office 365-Konto an. Die neue Symbolleiste **Information Protection** ermöglicht es Benutzern, die neue Bezeichnung auszuwählen. Stellen Sie sicher, dass Ihre Benutzer die SharePoint Online-Teamwebsite kennen und wissen, welche Bezeichnung sie verwenden müssen, um ihre streng vertraulichen Dateien zu schützen.</span><span class="sxs-lookup"><span data-stu-id="725b8-p107">Once installed, your users run and then sign-in from an Office application (such as Microsoft Word) with their Office 365 account. A new **Information Protection** bar allows users to select the new label. Make sure that your users know the SharePoint Online team site and which label to use, to protect their highly confidential files.</span></span>
  
> [!NOTE]
> <span data-ttu-id="725b8-156">Wenn Sie über mehrere streng vertrauliche SharePoint Online-Teamwebsites verfügen, müssen Sie anhand der oben aufgeführten Einstellungen mehrere bereichsbezogene Azure Information Protection-Richtlinien mit Unterbezeichnungen erstellen, wobei die Berechtigungen für jede Unterbezeichnung auf die Websitemitglieder-Zugriffsgruppe einer bestimmten SharePoint Online-Teamwebsite festgelegt sind.</span><span class="sxs-lookup"><span data-stu-id="725b8-156">If you have multiple highly sensitive SharePoint Online team sites, you should create multiple Azure Information Protection scoped policies with sub-labels with the above settings, with the permissions for each sub-label set to the site members access group of a specific SharePoint Online team site.</span></span> 
  
##<a name="adding-permissions-for-external-users"></a><span data-ttu-id="725b8-157">Hinzufügen von Berechtigungen für externe Benutzer</span><span class="sxs-lookup"><span data-stu-id="725b8-157">Adding permissions for external users</span></span>
<span data-ttu-id="725b8-p108">Es gibt zwei Möglichkeiten, wie Sie externen Benutzern Zugriff auf Dateien gewähren können, die mit Azure Information Protection geschützt sind. In beiden Fällen benötigen die externen Benutzer ein Azure AD-Konto. Wenn externe Benutzer kein Mitglied einer Organisation sind, die Azure Active Directory verwendet, können sie auf dieser Registrierungsseite ein Azure AD-Konto als Einzelperson beantragen: [https://aka.ms/aip-signup](https://aka.ms/aip-signup).</span><span class="sxs-lookup"><span data-stu-id="725b8-p108">There are two ways you can grant external users access to files protected with Azure Information Protection. In both these cases, external users must have an Azure AD account. If external users aren't members of an organization that uses Azure AD, they can obtain an Azure AD account as an individual by using this sign-up page: [https://aka.ms/aip-signup](https://aka.ms/aip-signup).</span></span>

 - <span data-ttu-id="725b8-p109">Hinzufügen von externen Benutzern zu einer Azure AD-Gruppe, die zum Konfigurieren des Schutzes für eine Bezeichnung verwendet wird. Sie müssen zuerst das Konto als B2B-Benutzer in Ihrem Verzeichnis hinzufügen. Das [Zwischenspeichern der Gruppenmitgliedschaft durch Azure Rights Management](https://docs.microsoft.com/de-DE/azure/information-protection/plan-design/prepare#group-membership-caching-by-azure-information-protection) kann einige Stunden dauern.</span><span class="sxs-lookup"><span data-stu-id="725b8-p109">Add external users to an Azure AD group that is used to configure protection for a label. You’ll need to first add the account as a B2B user in your directory. It can take a couple of hours for group membership caching by Azure Rights Management. With this method, permissions are granted to all existing files protected with the label (even files protected before a user is added to the Azure AD group).</span></span>  
 - <span data-ttu-id="725b8-p110">Direktes Hinzufügen von externen Benutzern zum Bezeichnungsschutz. Sie können alle Benutzer aus einer Organisation (z. B. „Fabrikam.com“), eine Azure AD-Gruppe (z. B. eine Finanzgruppe innerhalb einer Organisation) oder einen Benutzer hinzufügen. Sie können beispielsweise ein externes Team von Aufsichtsbeamten zum Schutz für eine Bezeichnung hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="725b8-p110">Add external users directly to the label protection. You can add all users from an organization (e.g. Fabrikam.com), an Azure AD group (such as a finance group within an organization), or an individual user. For example, you can add an external team of regulators to the protection for a label. With this method, permissions are granted only to files protected with the label after the external entity is added to the protection.</span></span>

## <a name="see-also"></a><span data-ttu-id="725b8-167">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="725b8-167">See Also</span></span>

[<span data-ttu-id="725b8-168">Sichern von SharePoint Online-Websites und -Dateien</span><span class="sxs-lookup"><span data-stu-id="725b8-168">Secure SharePoint Online sites and files</span></span>](secure-sharepoint-online-sites-and-files.md)
  
[<span data-ttu-id="725b8-169">Sichern von SharePoint Online-Websites in einer Entwicklungs-/Testumgebung</span><span class="sxs-lookup"><span data-stu-id="725b8-169">Secure SharePoint Online sites in a dev/test environment</span></span>](secure-sharepoint-online-sites-in-a-dev-test-environment.md)
  
[<span data-ttu-id="725b8-170">Microsoft-Sicherheitsleitfaden für politische Kampagnen, gemeinnützigen Organisationen und andere agile Organisationen</span><span class="sxs-lookup"><span data-stu-id="725b8-170">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[<span data-ttu-id="725b8-171">Cloudakzeptanz und Hybridlösungen</span><span class="sxs-lookup"><span data-stu-id="725b8-171">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)




