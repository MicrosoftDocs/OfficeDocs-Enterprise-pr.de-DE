---
title: Erstellen eines B2B-Extranets mit verwalteten Gästen
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: sharepoint-online
localization_priority: Normal
f1.keywords:
- NOCSH
description: Hier erfahren Sie, wie Sie eine B2B-Extranet-Website oder ein Team mit verwalteten Gastbenutzern aus einer Partnerorganisation erstellen.
ms.openlocfilehash: 930c11489921fa5c32d1ba1ab16161f201006c91
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844996"
---
# <a name="create-a-b2b-extranet-with-managed-guests"></a><span data-ttu-id="3d4ee-103">Erstellen eines B2B-Extranets mit verwalteten Gästen</span><span class="sxs-lookup"><span data-stu-id="3d4ee-103">Create a B2B extranet with managed guests</span></span>

<span data-ttu-id="3d4ee-104">Sie können [Azure Active Directory Berechtigungsverwaltung](https://docs.microsoft.com/azure/active-directory/governance/entitlement-management-overview) verwenden, um ein B2B-Extranet zur Zusammenarbeit mit einer Partnerorganisation zu erstellen, die Azure-Active Directory verwendet.</span><span class="sxs-lookup"><span data-stu-id="3d4ee-104">You can use [Azure Active Directory Entitlement Management](https://docs.microsoft.com/azure/active-directory/governance/entitlement-management-overview) to create a B2B extranet to collaborate with a partner organization that uses Azure Active Directory.</span></span> <span data-ttu-id="3d4ee-105">Dadurch können sich Benutzer selbst im Extranet-Standort oder-Team registrieren und über einen Genehmigungsworkflow Zugriff erhalten.</span><span class="sxs-lookup"><span data-stu-id="3d4ee-105">This allows users to self-enroll in the extranet site or team and receive access via an approval workflow.</span></span>

<span data-ttu-id="3d4ee-106">Mit dieser Methode der gemeinsamen Nutzung von Ressourcen für die Zusammenarbeit kann die Partnerorganisation helfen, die Gastbenutzer zu verwalten und zu genehmigen, wodurch die Belastung Ihrer IT-Abteilung reduziert und die Benutzer, die mit der Zusammenarbeitsvereinbarung vertraut sind, die Verwaltung von Benutzern ermöglichen. Access.</span><span class="sxs-lookup"><span data-stu-id="3d4ee-106">With this method of sharing resources for collaboration, the partner organization can help maintain and approve the guest users on their end, reducing the burden on your IT department and allowing those most familiar with the collaboration agreement to manage user access.</span></span>

<span data-ttu-id="3d4ee-107">In diesem Artikel werden die Schritte beschrieben, um ein Ressourcenpaket (in diesem Fall eine Website oder ein Team) zu erstellen, das Sie über ein Self-Service Access-Registrierungsmodell für eine Partnerorganisation freigeben können.</span><span class="sxs-lookup"><span data-stu-id="3d4ee-107">This article walks through the steps to create a package of resources (in this case, a site or team) that you can share with a partner organization through a self-service access registration model.</span></span> 

<span data-ttu-id="3d4ee-108">Bevor Sie beginnen, erstellen Sie die Website oder das Team, die Sie für die Partnerorganisation freigeben möchten, und aktivieren Sie Sie für die Gast Freigabe.</span><span class="sxs-lookup"><span data-stu-id="3d4ee-108">Before you begin, create the site or team that you want to share with the partner organization and enable it for guest sharing.</span></span> <span data-ttu-id="3d4ee-109">Weitere Informationen finden Sie unter [Zusammenarbeit mit Gästen in einer Website](collaborate-in-a-site.md) oder [Zusammenarbeit mit Gästen in einem Team](collaborate-as-a-team.md) .</span><span class="sxs-lookup"><span data-stu-id="3d4ee-109">See [Collaborate with guests in a site](collaborate-in-a-site.md) or [Collaborate with guests in a team](collaborate-as-a-team.md) for more information.</span></span> <span data-ttu-id="3d4ee-110">Außerdem wird empfohlen, dass Sie [eine Umgebung für sichere Gast Freigaben erstellen](create-a-secure-guest-sharing-environment.md) , in der Sie Informationen zu Sicherheits-und Kompatibilitätsfeatures erhalten, die Sie bei der Zusammenarbeit mit Gästen zur Verwaltung Ihrer Steuerungsrichtlinien verwenden können.</span><span class="sxs-lookup"><span data-stu-id="3d4ee-110">We also recommend that you review [Create a secure guest sharing environment](create-a-secure-guest-sharing-environment.md) for information about security and compliance features that you can use to help maintain your governance policies when collaborating with guests.</span></span>

## <a name="connect-the-partner-organization"></a><span data-ttu-id="3d4ee-111">Verbinden der Partnerorganisation</span><span class="sxs-lookup"><span data-stu-id="3d4ee-111">Connect the partner organization</span></span>

<span data-ttu-id="3d4ee-112">Um Gäste aus einer Partnerorganisation einzuladen, müssen Sie die Domäne des Partners als verbundene Organisation in Azure Active Directory hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="3d4ee-112">In order to invite guests from a partner organization, you need to add the the partner's domain as a connected organization in Azure Active Directory.</span></span>

<span data-ttu-id="3d4ee-113">So fügen Sie eine verbundene Organisation hinzu</span><span class="sxs-lookup"><span data-stu-id="3d4ee-113">To add a connected organization</span></span>
1. <span data-ttu-id="3d4ee-114">Klicken Sie in [Azure Active Directory](https://aad.portal.azure.com)auf **Identity Governance**.</span><span class="sxs-lookup"><span data-stu-id="3d4ee-114">In [Azure Active Directory](https://aad.portal.azure.com), click **Identity Governance**.</span></span>
2. <span data-ttu-id="3d4ee-115">Klicken Sie auf **verbundene Organisationen**.</span><span class="sxs-lookup"><span data-stu-id="3d4ee-115">Click **Connected organizations**.</span></span>
4. <span data-ttu-id="3d4ee-116">Klicken Sie auf **verbundene Organisation hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="3d4ee-116">Click **Add connected organization**.</span></span>
5. <span data-ttu-id="3d4ee-117">Geben Sie einen Namen und eine Beschreibung für die Organisation ein, und klicken Sie dann auf **Weiter: Verzeichnis + Domäne**.</span><span class="sxs-lookup"><span data-stu-id="3d4ee-117">Type a name and description for the organization, and then click **Next: Directory + domain**.</span></span>
6. <span data-ttu-id="3d4ee-118">Klicken Sie auf **Verzeichnis + Domäne hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="3d4ee-118">Click **Add directory + domain**.</span></span>
7. <span data-ttu-id="3d4ee-119">Geben Sie die Domäne für die Organisation ein, mit der Sie eine Verbindung herstellen möchten, und klicken Sie dann auf **Hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="3d4ee-119">Type the domain for the organization that you want to connect, and then click **Add**.</span></span>
8. <span data-ttu-id="3d4ee-120">Klicken Sie auf **verbinden**, und klicken Sie dann auf **Weiter: Sponsoren**.</span><span class="sxs-lookup"><span data-stu-id="3d4ee-120">Click **Connect**, and then click **Next: Sponsors**.</span></span>
9. <span data-ttu-id="3d4ee-121">Hinzufügen von Personen aus Ihrer Organisation oder der Organisation, der Sie eine Verbindung herstellen möchten, für die Sie den Zugriff für Gastbenutzer genehmigen möchten.</span><span class="sxs-lookup"><span data-stu-id="3d4ee-121">Add people from your organization or the organization that you're connecting to who you want to approve access for guest users.</span></span>
10. <span data-ttu-id="3d4ee-122">Klicken Sie auf **Weiter: Review + Create**.</span><span class="sxs-lookup"><span data-stu-id="3d4ee-122">Click **Next: Review + Create**.</span></span>
11. <span data-ttu-id="3d4ee-123">Überprüfen Sie die Einstellungen, die Sie ausgewählt haben, und klicken Sie dann auf **Erstellen**.</span><span class="sxs-lookup"><span data-stu-id="3d4ee-123">Review the settings that you've chosen and then click **Create**.</span></span>

    ![Screenshot der Seite "verbundene Organisationen" in Azure Active Directory](media/identity-governance-connected-organizations.png)

## <a name="choose-the-resources-to-share"></a><span data-ttu-id="3d4ee-125">Auswählen der freizugebenden Ressourcen</span><span class="sxs-lookup"><span data-stu-id="3d4ee-125">Choose the resources to share</span></span>

<span data-ttu-id="3d4ee-126">Der erste Schritt bei der Auswahl von Ressourcen, die für eine Partnerorganisation freigegeben werden sollen, ist das Erstellen eines Katalogs, der diese enthalten soll.</span><span class="sxs-lookup"><span data-stu-id="3d4ee-126">The first step in selecting resources to share with a partner organization is to create a catalog to contain them.</span></span>

<span data-ttu-id="3d4ee-127">So erstellen Sie einen Katalog</span><span class="sxs-lookup"><span data-stu-id="3d4ee-127">To create a catalog</span></span>
1. <span data-ttu-id="3d4ee-128">Klicken Sie in [Azure Active Directory](https://aad.portal.azure.com)auf **Identity Governance**.</span><span class="sxs-lookup"><span data-stu-id="3d4ee-128">In [Azure Active Directory](https://aad.portal.azure.com), click **Identity Governance**.</span></span>
2. <span data-ttu-id="3d4ee-129">Klicken Sie auf **Kataloge**.</span><span class="sxs-lookup"><span data-stu-id="3d4ee-129">Click **Catalogs**.</span></span>
3. <span data-ttu-id="3d4ee-130">Klicken Sie auf **neuer Katalog**.</span><span class="sxs-lookup"><span data-stu-id="3d4ee-130">Click **New catalog**.</span></span>
4. <span data-ttu-id="3d4ee-131">Geben Sie einen Namen und eine Beschreibung für den Katalog ein, und stellen Sie sicher, dass **für externe Benutzer** **aktiviert** und aktiviert beide auf **Ja**festgelegt sind.</span><span class="sxs-lookup"><span data-stu-id="3d4ee-131">Type a name and description for the catalog and ensure that **Enabled** and **Enabled for external users** are both set to **Yes**.</span></span>
5. <span data-ttu-id="3d4ee-132">Klicken Sie auf **Erstellen**.</span><span class="sxs-lookup"><span data-stu-id="3d4ee-132">Click **Create**.</span></span>

   ![Screenshot der Seite "Kataloge" in Azure Active Directory Identity Governance](media/identity-governance-catalogs.png)

<span data-ttu-id="3d4ee-134">Nachdem der Katalog erstellt wurde, fügen Sie die SharePoint-Website oder das Team hinzu, die Sie für die Partnerorganisation freigeben möchten.</span><span class="sxs-lookup"><span data-stu-id="3d4ee-134">Once the catalog has been created, you add the SharePoint site or team that you want to share with the partner organization.</span></span>

<span data-ttu-id="3d4ee-135">So fügen Sie einem Katalogressourcen hinzu</span><span class="sxs-lookup"><span data-stu-id="3d4ee-135">To add resources to a catalog</span></span>
1. <span data-ttu-id="3d4ee-136">Klicken Sie in Azure AD Identitäts Steuerung auf **Kataloge**, und klicken Sie dann auf den Katalog, in dem Sie Ressourcen hinzufügen möchten.</span><span class="sxs-lookup"><span data-stu-id="3d4ee-136">In Azure AD Identity Governance, click **Catalogs**, and then click the catalog where you want to add resources.</span></span>
2. <span data-ttu-id="3d4ee-137">Klicken Sie auf **Ressourcen** , und klicken Sie dann auf **Ressourcen hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="3d4ee-137">Click **Resources** and then click **Add resources**.</span></span>
3. <span data-ttu-id="3d4ee-138">Wählen Sie die Teams oder SharePoint-Websites aus, die Sie in Ihr Extranet einbeziehen möchten, und klicken Sie dann auf **Hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="3d4ee-138">Select the teams or SharePoint sites that you want to include in your extranet, and then click **Add**.</span></span>

   ![Screenshot der Seite "Katalogressourcen" in Azure Active Directory Identity Governance](media/identity-governance-catalog-resource.png)

<span data-ttu-id="3d4ee-140">Nachdem Sie die Ressourcen definiert haben, die Sie freigeben möchten, müssen Sie im nächsten Schritt ein Access-Paket erstellen, das die Art des Zugriffs für Partnerbenutzer und den Genehmigungsprozess für neue Partnerbenutzer definiert, die Zugriff anfordern.</span><span class="sxs-lookup"><span data-stu-id="3d4ee-140">Once you've defined the resources that you want to share, the next step is to create an access package, which defines the type of access that partner users are granted and the approval process for new partner users requesting access.</span></span>

<span data-ttu-id="3d4ee-141">So erstellen Sie ein Access-Paket</span><span class="sxs-lookup"><span data-stu-id="3d4ee-141">To create an access package</span></span>
1. <span data-ttu-id="3d4ee-142">Klicken Sie in Azure AD Identitäts Steuerung auf **Kataloge**, und klicken Sie dann auf den Katalog, in dem Sie ein Access-Paket erstellen möchten.</span><span class="sxs-lookup"><span data-stu-id="3d4ee-142">In Azure AD Identity Governance, click **Catalogs**, and then click the catalog where you want to create an access package.</span></span>
2. <span data-ttu-id="3d4ee-143">Klicken Sie auf **Access-Pakete**, und klicken Sie dann auf **Neues Zugriffs Paket**.</span><span class="sxs-lookup"><span data-stu-id="3d4ee-143">Click **Access packages**, and then click **New access package**.</span></span>
3. <span data-ttu-id="3d4ee-144">Geben Sie einen Namen und eine Beschreibung für das Access-Paket ein, und klicken Sie dann auf **Weiter: Ressourcen Rollen**.</span><span class="sxs-lookup"><span data-stu-id="3d4ee-144">Type a name and description for the access package, and then click **Next: Resource roles**.</span></span>
4. <span data-ttu-id="3d4ee-145">Wählen Sie die Ressourcen aus dem Katalog aus, die Sie für Ihr Extranet verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="3d4ee-145">Choose the resources from the catalog that you want to use for your extranet.</span></span>
5. <span data-ttu-id="3d4ee-146">Wählen Sie für jede Ressource in der Spalte **Rolle** die Benutzerrolle aus, die Sie den Gastbenutzern gewähren möchten, die das Extranet verwenden.</span><span class="sxs-lookup"><span data-stu-id="3d4ee-146">For each resource, in the **Role** column, choose the user role you want to grant to the guest users who use the extranet.</span></span>
6. <span data-ttu-id="3d4ee-147">Klicken Sie auf **Weiter: Anfragen**.</span><span class="sxs-lookup"><span data-stu-id="3d4ee-147">Click **Next: Requests**.</span></span>
7. <span data-ttu-id="3d4ee-148">Wählen Sie unter **Benutzer, die Zugriff anfordern können** **aus für Benutzer, die sich nicht in Ihrem Verzeichnis**befinden.</span><span class="sxs-lookup"><span data-stu-id="3d4ee-148">Under **Users who can request access**, choose **For users not in your directory**.</span></span>
8. <span data-ttu-id="3d4ee-149">Stellen Sie sicher, dass die Option **bestimmte verbundene Organisationen** ausgewählt ist, und klicken Sie dann auf **Verzeichnisse hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="3d4ee-149">Ensure that the **Specific connected organizations** option is selected, and then click **Add directories**.</span></span>
9. <span data-ttu-id="3d4ee-150">Wählen Sie die verbundene Organisation aus, die Sie zuvor hinzugefügt haben, und klicken Sie dann auf **auswählen**</span><span class="sxs-lookup"><span data-stu-id="3d4ee-150">Choose the connected organization that you add earlier, and then click **Select**</span></span>
10. <span data-ttu-id="3d4ee-151">Wählen Sie unter **Genehmigung**die Option **Ja** für **Genehmigung erforderlich**aus.</span><span class="sxs-lookup"><span data-stu-id="3d4ee-151">Under **Approval**, choose **Yes** for **Require approval**.</span></span>
11. <span data-ttu-id="3d4ee-152">Wählen Sie unter **erste genehmigende Person**einen der Sponsoren aus, die Sie zuvor hinzugefügt haben, oder wählen Sie einen bestimmten Benutzer aus.</span><span class="sxs-lookup"><span data-stu-id="3d4ee-152">Under **First approver**, choose one of the sponsors that you added earlier or choose a specific user.</span></span>
12. <span data-ttu-id="3d4ee-153">Klicken Sie auf **Fallback hinzufügen** und wählen Sie eine Fallback genehmigende Person aus.</span><span class="sxs-lookup"><span data-stu-id="3d4ee-153">Click **Add fallback** and select a fallback approver.</span></span>
13. <span data-ttu-id="3d4ee-154">Wählen Sie unter **aktivieren**die Option **Ja**aus.</span><span class="sxs-lookup"><span data-stu-id="3d4ee-154">Under **Enable**, choose **Yes**.</span></span>
14. <span data-ttu-id="3d4ee-155">Klicken Sie auf **Weiter: Lebenszyklus**.</span><span class="sxs-lookup"><span data-stu-id="3d4ee-155">Click **Next: Lifecycle**.</span></span>
15. <span data-ttu-id="3d4ee-156">Wählen Sie die Einstellungen für Ablauf und Zugriffsüberprüfung aus, die Sie verwenden möchten, und klicken Sie dann auf **Weiter: Überprüfen + Erstellen**.</span><span class="sxs-lookup"><span data-stu-id="3d4ee-156">Choose the expiration and access review settings that you want to use, and then click **Next: Review + Create**.</span></span>
16. <span data-ttu-id="3d4ee-157">Überprüfen Sie Ihre Einstellungen, und klicken Sie dann auf **Erstellen**.</span><span class="sxs-lookup"><span data-stu-id="3d4ee-157">Review your settings, and then click **Create**.</span></span>

    ![Screenshot des Access Packages-Bildschirms in Azure Active Directory Identity Governance](media/identity-governance-access-packages.png)

<span data-ttu-id="3d4ee-159">Wenn Sie eine Partnerschaft mit einer großen Organisation ausführen möchten, können Sie das Access-Paket ausblenden.</span><span class="sxs-lookup"><span data-stu-id="3d4ee-159">If you're partnering with a large organization, you may want to hide the access package.</span></span> <span data-ttu-id="3d4ee-160">Wenn das Paket ausgeblendet ist, werden Benutzer in der Partnerorganisation das Paket nicht auf Ihrem *My Access* -Portal sehen.</span><span class="sxs-lookup"><span data-stu-id="3d4ee-160">If the package is hidden, then users in the partner organization will not see the package on their *My Access* portal.</span></span> <span data-ttu-id="3d4ee-161">Stattdessen muss Ihnen ein direkter Link zur Anmeldung für das Paket gesendet werden.</span><span class="sxs-lookup"><span data-stu-id="3d4ee-161">Instead, they must be sent a direct link to sign up for the package.</span></span> <span data-ttu-id="3d4ee-162">Das Ausblenden des Access-Pakets kann die Anzahl unangemessener Zugriffsanforderungen verringern und auch dazu beitragen, dass verfügbare Zugriffs Pakete im Portal der Partnerorganisation organisiert werden.</span><span class="sxs-lookup"><span data-stu-id="3d4ee-162">Hiding the access package can reduce the number of inappropriate access requests and can also help keep available access packages organized in the partner organization's portal.</span></span>

<span data-ttu-id="3d4ee-163">So legen Sie ein Access-Paket auf ausgeblendet fest</span><span class="sxs-lookup"><span data-stu-id="3d4ee-163">To set an access package to hidden</span></span>
1. <span data-ttu-id="3d4ee-164">Klicken Sie in Azure AD Identitäts Steuerung auf **Access-Pakete**, und klicken Sie dann auf Ihr Zugriffs Paket.</span><span class="sxs-lookup"><span data-stu-id="3d4ee-164">In Azure AD Identity Governance, click **Access packages**, and then click your access package.</span></span>
2. <span data-ttu-id="3d4ee-165">Klicken Sie auf der Seite **Übersicht** auf **Bearbeiten**.</span><span class="sxs-lookup"><span data-stu-id="3d4ee-165">On the **Overview** page, click **Edit**.</span></span>
3. <span data-ttu-id="3d4ee-166">Wählen Sie unter **Eigenschaften**die Option **Ja** für **ausgeblendet**aus, und klicken Sie dann auf **Speichern**.</span><span class="sxs-lookup"><span data-stu-id="3d4ee-166">Under **Properties**, choose **Yes** for **Hidden**, and then click **Save**.</span></span>

   ![Screenshot des Bildschirms Eigenschaften des Bearbeitungs Zugriffs Pakets](media/identity-governance-access-package-hidden.png)

## <a name="invite-partner-users"></a><span data-ttu-id="3d4ee-168">Einladen von Partnerbenutzern</span><span class="sxs-lookup"><span data-stu-id="3d4ee-168">Invite partner users</span></span>

<span data-ttu-id="3d4ee-169">Wenn Sie das Access-Paket auf ausgeblendet festlegen, müssen Sie einen direkten Link zur Partnerorganisation senden, damit Sie Zugriff auf Ihre Website oder Ihr Team anfordern können.</span><span class="sxs-lookup"><span data-stu-id="3d4ee-169">If you set the access package to hidden, you need to send a direct link to the partner organization so that they can request access to your site or team.</span></span>

<span data-ttu-id="3d4ee-170">So suchen Sie den Access Portal-Link</span><span class="sxs-lookup"><span data-stu-id="3d4ee-170">To find the access portal link</span></span>
1. <span data-ttu-id="3d4ee-171">Klicken Sie in Azure AD Identitäts Steuerung auf **Access-Pakete**, und klicken Sie dann auf Ihr Zugriffs Paket.</span><span class="sxs-lookup"><span data-stu-id="3d4ee-171">In Azure AD Identity Governance, click **Access packages**, and then click your access package.</span></span>
2. <span data-ttu-id="3d4ee-172">Klicken Sie auf der Übersichts **Seite auf den Link** **in Zwischenablage kopieren** für den **Link My Access Portal**.</span><span class="sxs-lookup"><span data-stu-id="3d4ee-172">On the **Overview** page, click **Copy to clipboard** link for the **My Access portal link**.</span></span>

   ![Screenshot der Access-Paketeigenschaften mit Access Portal Link](media/identity-governance-access-portal-link.png)

<span data-ttu-id="3d4ee-174">Nachdem Sie den Link kopiert haben, können Sie ihn für Ihren Kontakt in der Partnerorganisation freigeben, und er kann ihn an die Benutzer im Team für die Zusammenarbeit senden.</span><span class="sxs-lookup"><span data-stu-id="3d4ee-174">Once you have copied the link, you can share it with your contact at the partner organization and they can send it to the users on their collaboration team.</span></span>

## <a name="see-also"></a><span data-ttu-id="3d4ee-175">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="3d4ee-175">See Also</span></span>

[<span data-ttu-id="3d4ee-176">Erstellen einer sicheren Umgebung für die Gastfreigabe</span><span class="sxs-lookup"><span data-stu-id="3d4ee-176">Create a secure guest sharing environment</span></span>](create-a-secure-guest-sharing-environment.md)

