---
title: "Richtlinien für die Microsoft 365 Enterprise Test-/Umgebung MAM"
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
- Ent_TLGs
ms.assetid: 1aa9639b-2862-49c4-bc33-1586dda636b8
description: "Zusammenfassung: Verwenden dieser Test Lab Guide Ihrer Microsoft 365 Test-/Umgebung zur Abstimmung mobilen Anwendung Informationsverwaltungsrichtlinien (MAM) hinzufügen."
ms.openlocfilehash: d088970dca1ec55212642f16d0519e89bd9591e5
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2017
---
# <a name="mam-policies-for-your-microsoft-365-enterprise-devtest-environment"></a><span data-ttu-id="b78d0-103">Richtlinien für die Microsoft 365 Enterprise Test-/Umgebung MAM</span><span class="sxs-lookup"><span data-stu-id="b78d0-103">MAM policies for your Microsoft 365 Enterprise dev/test environment</span></span>

 <span data-ttu-id="b78d0-104">**Zusammenfassung:** Verwenden Sie diese Test Lab Guide, zur Abstimmung mobilen Anwendung Informationsverwaltungsrichtlinien (MAM) mit der Microsoft 365 Test-/Umgebung hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="b78d0-104">**Summary:** Use this Test Lab Guide to add EMS mobile application management (MAM) policies to your Microsoft 365 dev/test environment.</span></span>
  
<span data-ttu-id="b78d0-p101">Der Microsoft Enterprise Mobilität + Sicherheit (zur Abstimmung) verhindert, dass Ihre Mitarbeiter produktiv mithilfe ihrer bevorzugten apps und -Geräte beim Schützen von Daten der Organisation. Weitere Informationen finden Sie unter [Enterprise Mobilität + Sicherheit (zur Abstimmung)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security).</span><span class="sxs-lookup"><span data-stu-id="b78d0-p101">The Microsoft Enterprise Mobility + Security (EMS) helps keep your employees productive using their favorite apps and devices while protecting your organization's data. For more information, see [Enterprise Mobility + Security (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security).</span></span>
  
<span data-ttu-id="b78d0-107">Mit den Anweisungen in diesem Artikel fügen Sie die mobile Anwendung Informationsverwaltungsrichtlinien (MAM) in Ihrer Microsoft 365 Dev/testumgebung.</span><span class="sxs-lookup"><span data-stu-id="b78d0-107">With the instructions in this article, you add mobile application management (MAM) policies to your Microsoft 365 dev/test environment.</span></span>
  
## <a name="phase-1-build-out-your-microsoft-365-devtest-environment"></a><span data-ttu-id="b78d0-108">Phase 1: Erstellen Sie Ihre Microsoft 365 Dev/Test-Umgebung</span><span class="sxs-lookup"><span data-stu-id="b78d0-108">Phase 1: Build out your Microsoft 365 dev/test environment</span></span>

<span data-ttu-id="b78d0-109">Befolgen Sie die Anweisungen in [The Microsoft 365 Enterprise Test-/Umgebung](the-microsoft-365-enterprise-dev-test-environment.md)aus.</span><span class="sxs-lookup"><span data-stu-id="b78d0-109">Follow the instructions in [The Microsoft 365 Enterprise dev/test environment](the-microsoft-365-enterprise-dev-test-environment.md).</span></span>
  
## <a name="phase-2-create-and-deploy-mam-policies-for-ios-and-android-devices"></a><span data-ttu-id="b78d0-110">Phase 2: Erstellen und Bereitstellen von MAM-Richtlinien für iOS- und Android-Geräte</span><span class="sxs-lookup"><span data-stu-id="b78d0-110">Phase 2: Create and deploy MAM policies for iOS and Android devices</span></span>

<span data-ttu-id="b78d0-111">In dieser Phase werden zwei verschiedene MAM-Richtlinien erstellt und bereitgestellt: eine für iOS-Geräte und eine für Android-Geräte.</span><span class="sxs-lookup"><span data-stu-id="b78d0-111">In this phase, you create and deploy two different MAM policies: one for iOS devices and one for Android devices.</span></span>
  
1. <span data-ttu-id="b78d0-112">Wechseln Sie zum Office 365-Portal ([https://portal.office.com](https://portal.office.com)), und melden Sie sich bei Ihrem Office 365-Testabonnement mit Ihrem globalen Administratorkonto an.</span><span class="sxs-lookup"><span data-stu-id="b78d0-112">Go to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) and sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
2. <span data-ttu-id="b78d0-113">Öffnen Sie auf einer neuen Registerkarte Ihres Browsers das Azure Portal ([https://azure.portal.com](https://azure.portal.com)), und melden Sie sich mit Ihrem Office 365 globaler Administrator-Konto.</span><span class="sxs-lookup"><span data-stu-id="b78d0-113">On a new tab of your browser, open the Azure portal ([https://azure.portal.com](https://azure.portal.com)) and sign in using your Office 365 global administrator account.</span></span>
    
3. <span data-ttu-id="b78d0-114">Klicken Sie auf der Azure Portal Registerkarte in Internet Explorer im Navigationsbereich klicken Sie auf **Weitere Dienste** (oder auf den Pfeil nach rechts), geben Sie **Intune**, und klicken Sie dann auf **Intune**.</span><span class="sxs-lookup"><span data-stu-id="b78d0-114">On the Azure portal tab in Internet Explorer, in the navigation pane, click **More services** (or the right arrow), type **Intune**, and then click **Intune**.</span></span>
    
4. <span data-ttu-id="b78d0-115">Klicken Sie im linken Navigationsbereich auf **Gruppen**.</span><span class="sxs-lookup"><span data-stu-id="b78d0-115">In the left navigation pane, click **Groups**.</span></span>
    
5. <span data-ttu-id="b78d0-116">Klicken Sie auf der Blade **-Benutzer und Gruppen alle Gruppen** auf **Hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="b78d0-116">On the **Users and groups-All groups** blade, click **Add**.</span></span>
    
6. <span data-ttu-id="b78d0-117">In der **Gruppe** Blade, geben Sie im Feld **Name** **iOS Gerätebenutzer verwaltete** **zugewiesen** **Mitgliedschaft geben**Sie in wählen, wählen Sie **Ja** für **Aktivieren von Office-Features?**, und klicken Sie dann auf **Erstellen**.</span><span class="sxs-lookup"><span data-stu-id="b78d0-117">On the **Group** blade, type **Managed iOS device users** in **Name**, select **Assigned** in **Membership type**, select **Yes** for **Enable Office features?**, and then click **Create**.</span></span> 
    
7. <span data-ttu-id="b78d0-118">Schließen Sie das **Gruppe** Blade.</span><span class="sxs-lookup"><span data-stu-id="b78d0-118">Close the **Group** blade.</span></span>
    
8. <span data-ttu-id="b78d0-119">Klicken Sie auf der Blade **-Benutzer und Gruppen alle Gruppen** auf **Hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="b78d0-119">On the **Users and groups-All groups** blade, click **Add**.</span></span>
    
9. <span data-ttu-id="b78d0-120">In der **Gruppe** Blade, geben Sie im Feld **Name** **Android verwaltete Gerätebenutzer** **zugewiesen** **Mitgliedschaft geben**Sie in wählen, wählen Sie **Ja** für **Aktivieren von Office-Features?**, und klicken Sie dann auf **Erstellen**.</span><span class="sxs-lookup"><span data-stu-id="b78d0-120">On the **Group** blade, type **Managed Android device users** in **Name**, select **Assigned** in **Membership type**, select **Yes** for **Enable Office features?**, and then click **Create**.</span></span>
    
10. <span data-ttu-id="b78d0-121">Schließen Sie das Blade **-Benutzer und Gruppen alle Gruppen** .</span><span class="sxs-lookup"><span data-stu-id="b78d0-121">Close the **Users and groups-All groups** blade.</span></span>
    
11. <span data-ttu-id="b78d0-122">Klicken Sie auf der Blade **Intune** in der Liste **schnell Aufgaben** **Erstellen einer Compliance-Richtlinie**.</span><span class="sxs-lookup"><span data-stu-id="b78d0-122">On the **Intune** blade, in the **Quick tasks** list, click **Create a compliance policy**.</span></span>
    
12. <span data-ttu-id="b78d0-123">Klicken Sie auf das **Compliance-Richtlinienprofilen** Blade **-Richtlinie erstellen**.</span><span class="sxs-lookup"><span data-stu-id="b78d0-123">On the **Compliance Policy Profiles** blade, click **Create Policy**.</span></span>
    
13. <span data-ttu-id="b78d0-p102">Geben Sie auf der Blade **-Richtlinie erstellen** im Feld **Name** **iOS**. **Plattform**wählen Sie **iOS aus**, klicken Sie auf **OK** , auf das Blade **iOS Compliance-Richtlinie** und klicken Sie dann auf **Erstellen**.</span><span class="sxs-lookup"><span data-stu-id="b78d0-p102">On the **Create Policy** blade, in **Name**, type **iOS**. In **Platform**, select **iOS**, click **OK** on the **iOS compliance policy** blade, and then click **Create**.</span></span>
    
14. <span data-ttu-id="b78d0-126">Klicken Sie auf das **Compliance-Richtlinienprofilen** Blade **-Richtlinie erstellen**.</span><span class="sxs-lookup"><span data-stu-id="b78d0-126">On the **Compliance Policy Profiles** blade, click **Create Policy**.</span></span>
    
15. <span data-ttu-id="b78d0-p103">Das Blade **-Richtlinie erstellen** im Feld **Name**Geben Sie auf **Android**. **Plattform**wählen Sie **Android**, klicken Sie auf **OK** , auf das Blade **Android Compliance-Richtlinien** und klicken Sie dann auf **Erstellen**.</span><span class="sxs-lookup"><span data-stu-id="b78d0-p103">On the **Create Policy** blade, in **Name**, type **Android**. In **Platform**, select **Android**, click **OK** on the **Android compliance policy** blade, and then click **Create**.</span></span>
    
16. <span data-ttu-id="b78d0-129">Klicken Sie auf das Blade **Richtlinienprofilen Compliance** auf den Namen der Richtlinie **Android** .</span><span class="sxs-lookup"><span data-stu-id="b78d0-129">On the **Compliance Policy Profiles** blade, click the **Android** policy name.</span></span>
    
17. <span data-ttu-id="b78d0-130">Im linken Navigationsbereich dem Blade **Android - Eigenschaften** klicken Sie auf **Aufgaben**, und klicken Sie dann auf **Gruppen auswählen**.</span><span class="sxs-lookup"><span data-stu-id="b78d0-130">In the left navigation of the **Android - Properties** blade, click **Assignments**, and then click **Select groups**.</span></span>
    
18. <span data-ttu-id="b78d0-131">Klicken Sie in der Blade **Gruppen auswählen** auf der **verwalteten Android-Gerät** Benutzergruppe, und klicken Sie dann auf **auswählen**.</span><span class="sxs-lookup"><span data-stu-id="b78d0-131">On the **Select groups** blade, click the **Managed Android device users** group, and then click **Select**.</span></span>
    
19. <span data-ttu-id="b78d0-132">Klicken Sie auf **Speichern**, und schließen Sie das Blade **Android - Zuordnungen** .</span><span class="sxs-lookup"><span data-stu-id="b78d0-132">Click **Save**, and then close the **Android - Assignments** blade.</span></span>
    
20. <span data-ttu-id="b78d0-133">Klicken Sie auf das Blade **Compliance Richtlinienprofilen** auf den Namen der Richtlinie **iOS** .</span><span class="sxs-lookup"><span data-stu-id="b78d0-133">On the **Compliance Policy Profiles** blade, click the **iOS** policy name.</span></span>
    
21. <span data-ttu-id="b78d0-134">Im linken Navigationsbereich dem Blade **iOS - Eigenschaften** klicken Sie auf **Aufgaben**, und klicken Sie dann auf **Gruppen auswählen**.</span><span class="sxs-lookup"><span data-stu-id="b78d0-134">In the left navigation of the **iOS - Properties** blade, click **Assignments**, and then click **Select groups**.</span></span>
    
22. <span data-ttu-id="b78d0-135">Klicken Sie in der Blade **Gruppen auswählen** auf die Gruppe **verwaltete iOS Gerätebenutzer** , und klicken Sie dann auf **auswählen**.</span><span class="sxs-lookup"><span data-stu-id="b78d0-135">On the **Select groups** blade, click the **Managed iOS device users** group, and then click **Select**.</span></span>
    
23. <span data-ttu-id="b78d0-136">Klicken Sie auf **Speichern**, und schließen Sie das Blade **iOS - Zuordnungen** .</span><span class="sxs-lookup"><span data-stu-id="b78d0-136">Click **Save**, and then close the **iOS - Assignments** blade.</span></span>
    
24. <span data-ttu-id="b78d0-137">Schließen Sie das **Compliance-Richtlinienprofilen** Blade.</span><span class="sxs-lookup"><span data-stu-id="b78d0-137">Close the **Compliance Policy Profiles** blade.</span></span>
    
25. <span data-ttu-id="b78d0-138">Klicken Sie auf das Blade **Intune** im linken Navigationsbereich auf **apps verwalten** .</span><span class="sxs-lookup"><span data-stu-id="b78d0-138">On the **Intune** blade, click **Manage apps** in the left navigation.</span></span>
    
26. <span data-ttu-id="b78d0-139">Klicken Sie auf das Blade **Mobile Apps** auf **Apps**.</span><span class="sxs-lookup"><span data-stu-id="b78d0-139">On the **Mobile Apps** blade, click **Apps**.</span></span>
    
27. <span data-ttu-id="b78d0-140">Klicken Sie in der Liste der apps **PowerPoint**,</span><span class="sxs-lookup"><span data-stu-id="b78d0-140">In the list of apps, click **PowerPoint**,</span></span> 
    
28. <span data-ttu-id="b78d0-p104">Klicken Sie auf die **PowerPoint-Übersicht** Blade auf **Zuordnungen > Gruppen auswählen > verwaltete iOS-Geräte > Wählen Sie**. Wählen Sie **Geben**Sie in **verfügbar**, und klicken Sie dann auf **Speichern**.</span><span class="sxs-lookup"><span data-stu-id="b78d0-p104">On the **PowerPoint Overview** blade, click **Assignments > Select groups > Managed iOS devices > Select**. In **Type**, select **Available**, and then click **Save**.</span></span>
    
29. <span data-ttu-id="b78d0-143">Wiederholen Sie Schritt 28 für die folgenden Apps:</span><span class="sxs-lookup"><span data-stu-id="b78d0-143">Repeat step 28 for the following apps:</span></span>
    
  - <span data-ttu-id="b78d0-144">Outlook für Android</span><span class="sxs-lookup"><span data-stu-id="b78d0-144">Outlook for Android</span></span>
    
  - <span data-ttu-id="b78d0-145">Word für iOS</span><span class="sxs-lookup"><span data-stu-id="b78d0-145">Word for iOS</span></span>
    
  - <span data-ttu-id="b78d0-146">Excel für iOS</span><span class="sxs-lookup"><span data-stu-id="b78d0-146">Excel for iOS</span></span>
    
  - <span data-ttu-id="b78d0-147">Outlook für iOS</span><span class="sxs-lookup"><span data-stu-id="b78d0-147">Outlook for iOS</span></span>
    
  - <span data-ttu-id="b78d0-148">Microsoft Dynamics CRM auf iPad für iOS</span><span class="sxs-lookup"><span data-stu-id="b78d0-148">Microsoft Dynamics CRM on iPad for iOS</span></span>
    
  - <span data-ttu-id="b78d0-149">Microsoft Dynamics CRM auf iPhone für iOS</span><span class="sxs-lookup"><span data-stu-id="b78d0-149">Microsoft Dynamics CRM on iPhone for iOS</span></span>
    
  - <span data-ttu-id="b78d0-150">Dynamics CRM für Smartphones für Android</span><span class="sxs-lookup"><span data-stu-id="b78d0-150">Dynamics CRM for Phones for Android</span></span>
    
  - <span data-ttu-id="b78d0-151">Dynamics CRM für Tablets für Android</span><span class="sxs-lookup"><span data-stu-id="b78d0-151">Dynamics CRM for Tablets for Android</span></span>
    
  - <span data-ttu-id="b78d0-152">Excel für Android</span><span class="sxs-lookup"><span data-stu-id="b78d0-152">Excel for Android</span></span>
    
  - <span data-ttu-id="b78d0-153">Word für Android</span><span class="sxs-lookup"><span data-stu-id="b78d0-153">Word for Android</span></span>
    
  - <span data-ttu-id="b78d0-154">OneNote für iOS</span><span class="sxs-lookup"><span data-stu-id="b78d0-154">OneNote for iOS</span></span>
    
30. <span data-ttu-id="b78d0-155">Schließen Sie das **Mobile Apps – Apps** Blade.</span><span class="sxs-lookup"><span data-stu-id="b78d0-155">Close the **Mobile Apps - Apps** blade.</span></span>
    
31. <span data-ttu-id="b78d0-156">Klicken Sie auf das Blade **Mobile Apps** auf **App-Richtlinien**.</span><span class="sxs-lookup"><span data-stu-id="b78d0-156">On the **Mobile Apps** blade, click **App Protection Policies**.</span></span>
    
32. <span data-ttu-id="b78d0-157">Klicken Sie auf das **App-Richtlinien** Blade auf **eine Richtlinie hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="b78d0-157">On the **App Protection Policies** blade, click **Add a policy**.</span></span>
    
33. <span data-ttu-id="b78d0-158">Geben Sie auf das **Hinzufügen einer Richtlinie** Blade **iOS**, und klicken Sie dann auf **Wählen Sie apps erforderlich**.</span><span class="sxs-lookup"><span data-stu-id="b78d0-158">On the **Add a policy** blade, type **iOS**, and then click **Select required apps**.</span></span>
    
34. <span data-ttu-id="b78d0-159">Klicken Sie in der Blade **Apps** auf **PowerPoint**, **Microsoft Dynamics CRM auf iPhone**, **Excel**, **Microsoft Dynamics CRM auf iPhone**, **Word**, **OneNote**und **Outlook**, und klicken Sie dann auf **auswählen**.</span><span class="sxs-lookup"><span data-stu-id="b78d0-159">On the **Apps** blade, click **PowerPoint**, **Microsoft Dynamics CRM on iPhone**, **Excel**, **Microsoft Dynamics CRM on iPhone**, **Word**, **OneNote**, and **Outlook**, and then click **Select**.</span></span>
    
35. <span data-ttu-id="b78d0-160">Klicken Sie auf das Blade **Hinzufügen einer Richtlinie** auf **Erstellen**.</span><span class="sxs-lookup"><span data-stu-id="b78d0-160">On the **Add a policy** blade, click **Create**.</span></span>
    
36. <span data-ttu-id="b78d0-161">Klicken Sie auf das **App-Richtlinien** Blade auf **eine Richtlinie hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="b78d0-161">On the **App Protection Policies** blade, click **Add a policy**.</span></span>
    
37. <span data-ttu-id="b78d0-162">Geben Sie auf das **Hinzufügen einer Richtlinie** Blade **Android**, wählen Sie **Android** **-Plattform**und klicken Sie dann auf **Wählen Sie apps erforderlich**.</span><span class="sxs-lookup"><span data-stu-id="b78d0-162">On the **Add a policy** blade, type **Android**, select **Android** in **Platform**, and then click **Select required apps**.</span></span>
    
38. <span data-ttu-id="b78d0-163">Klicken Sie in der Blade **Apps** auf **PowerPoint**, **Dynamics CRM für Tablets**, **Excel**, **Word**, **Outlook**und **Dynamics CRM für Telefone**, und klicken Sie dann auf **auswählen**.</span><span class="sxs-lookup"><span data-stu-id="b78d0-163">On the **Apps** blade, click **PowerPoint**, **Dynamics CRM for tablets**, **Excel**, **Word**, **Outlook**, and **Dynamics CRM for phones**, and then click **Select**.</span></span>
    
39. <span data-ttu-id="b78d0-164">Klicken Sie auf das Blade **Hinzufügen einer Richtlinie** auf **Erstellen**.</span><span class="sxs-lookup"><span data-stu-id="b78d0-164">On the **Add a policy** blade, click **Create**.</span></span>
    
<span data-ttu-id="b78d0-165">Sie nun verfügen über zwei MAM-Richtlinien, eine für iOS-Geräte und eine für Android-Geräte, und können nun mit verschiedenen Einstellungen für die ausgewählten Apps experimentieren.</span><span class="sxs-lookup"><span data-stu-id="b78d0-165">You now have two MAM policies, one for iOS devices and one for Android devices, and are ready to experiment with testing settings for the selected apps.</span></span>
  
> [!TIP]
> <span data-ttu-id="b78d0-166">Klicken Sie [hier](http://aka.ms/catlgstack) für eine visuelle Darstellung aller die Artikel in einer Microsoft Cloud Test Lab Guide-Stapel.</span><span class="sxs-lookup"><span data-stu-id="b78d0-166">Click [here](http://aka.ms/catlgstack) for a visual map to all of the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="b78d0-167">See Also</span><span class="sxs-lookup"><span data-stu-id="b78d0-167">See Also</span></span>

[<span data-ttu-id="b78d0-168">Die Microsoft 365 Enterprise-Entwicklungs-/Testumgebung</span><span class="sxs-lookup"><span data-stu-id="b78d0-168">The Microsoft 365 Enterprise dev/test environment</span></span>](the-microsoft-365-enterprise-dev-test-environment.md)
  
[<span data-ttu-id="b78d0-169">Registrieren Sie iOS und Android-Geräte in Ihrer Microsoft Enterprise 365 Dev/Test-Umgebung</span><span class="sxs-lookup"><span data-stu-id="b78d0-169">Enroll iOS and Android devices in your Microsoft Enterprise 365 dev/test environment</span></span>](enroll-ios-and-android-devices-in-your-microsoft-enterprise-365-dev-test-environ.md)
  
[<span data-ttu-id="b78d0-170">Testumgebungsanleitungen (TLGs) zur Cloudakzeptanz</span><span class="sxs-lookup"><span data-stu-id="b78d0-170">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)

[<span data-ttu-id="b78d0-171">Enterprise-Mobilität + Sicherheit (zur Abstimmung)</span><span class="sxs-lookup"><span data-stu-id="b78d0-171">Enterprise Mobility + Security (EMS)</span></span>](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)


