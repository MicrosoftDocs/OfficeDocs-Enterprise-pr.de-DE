---
title: Registrieren von iOS- und Android-Geräten in Ihrer Entwicklungs-/Testumgebung für Microsoft 365 Enterprise
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/20/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_TLGs
ms.assetid: 49c7758a-1c01-4153-9b63-5eae3f6305ce
description: 'Zusammenfassung: Mit diesem Test Lab Guide können Geräte in Ihrer Microsoft 365 Dev/Test-Umgebung zu registrieren und Remote zu verwalten.'
ms.openlocfilehash: e4b8491a70d0d0177e0a434d228136243201e788
ms.sourcegitcommit: c3869a332512dd1cc25cd5a92a340050f1da0418
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/20/2018
ms.locfileid: "20720411"
---
# <a name="enroll-ios-and-android-devices-in-your-microsoft-365-enterprise-devtest-environment"></a><span data-ttu-id="6bbad-103">Registrieren von iOS- und Android-Geräten in Ihrer Entwicklungs-/Testumgebung für Microsoft 365 Enterprise</span><span class="sxs-lookup"><span data-stu-id="6bbad-103">Enroll iOS and Android devices in your Microsoft 365 Enterprise dev/test environment</span></span>

 <span data-ttu-id="6bbad-104">**Zusammenfassung:** Verwenden Sie diese Test Lab Guide zum Registrieren von Geräten in Ihrer Microsoft 365 Dev/Test-Umgebung und Remote zu verwalten.</span><span class="sxs-lookup"><span data-stu-id="6bbad-104">**Summary:** Use this Test Lab Guide to enroll devices in your Microsoft 365 dev/test environment and manage them remotely.</span></span>
  
<span data-ttu-id="6bbad-p101">Der Microsoft Enterprise Mobilität Suite zur Abstimmung verhindert, dass Ihre Mitarbeiter produktiv mithilfe ihrer bevorzugten apps und -Geräte beim Schützen von Daten der Organisation. Weitere Informationen finden Sie unter [Enterprise Mobilität + Sicherheit (zur Abstimmung)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security).</span><span class="sxs-lookup"><span data-stu-id="6bbad-p101">The Microsoft Enterprise Mobility Suite (EMS) helps keep your employees productive using their favorite apps and devices while protecting your organization's data. For more information, see [Enterprise Mobility + Security (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security).</span></span>
  
<span data-ttu-id="6bbad-p102">Wenn Sie Sicherheit auf Device-Ebene anwenden möchten, müssen Sie in Microsoft Intune Geräte registrieren. Gerät-Registrierung können Sie zum Verwalten von Geräten im Besitz der Organisation nicht nur aber auch persönlich (BYOD) und gemeinsam genutzten Geräten, abhängig von Ihrer Organisation rechtliche der Richtlinien.</span><span class="sxs-lookup"><span data-stu-id="6bbad-p102">If you need to apply security at the device level, you must enroll devices into Microsoft Intune. Device enrollment not only helps you to manage organization-owned devices, but also personal (BYOD) and shared devices, depending on your organization's legal policies.</span></span>
  
<span data-ttu-id="6bbad-109">Gemäß die Anweisungen in diesem Artikel benötigen Sie möglicherweise registrieren und grundlegende Mobilgerät Management-Funktionen für iOS und Android-Geräte in Ihrer Microsoft 365 Test-/Umgebung testen.</span><span class="sxs-lookup"><span data-stu-id="6bbad-109">By following the instructions provided in this article, you'll be able to enroll and test basic mobile device management capabilities for iOS and Android devices in your Microsoft 365 dev/test environment.</span></span>
  
## <a name="phase-1-create-your-microsoft-365-devtest-environment"></a><span data-ttu-id="6bbad-110">Phase 1: Erstellen der Microsoft-365 Dev/Test-Umgebung</span><span class="sxs-lookup"><span data-stu-id="6bbad-110">Phase 1: Create your Microsoft 365 dev/test environment</span></span>

<span data-ttu-id="6bbad-111">Befolgen Sie die Anweisungen in [The Microsoft 365 Enterprise Test-/Umgebung](the-microsoft-365-enterprise-dev-test-environment.md)aus.</span><span class="sxs-lookup"><span data-stu-id="6bbad-111">Follow the instructions in [The Microsoft 365 Enterprise dev/test environment](the-microsoft-365-enterprise-dev-test-environment.md).</span></span>
  
## <a name="phase-2-enroll-your-ios-and-android-devices"></a><span data-ttu-id="6bbad-112">Phase 2: Registrieren Sie Ihre iOS und Android-Geräte</span><span class="sxs-lookup"><span data-stu-id="6bbad-112">Phase 2: Enroll your iOS and Android devices</span></span>

<span data-ttu-id="6bbad-113">Verwenden Sie zunächst die Anweisungen in [Installieren und melden Sie sich die app Unternehmensportal](https://docs.microsoft.com/intune-user-help/install-and-sign-in-to-the-intune-company-portal-app-ios) zum Anpassen von Microsoft Intune Unternehmensportal-app für Ihre testumgebung.</span><span class="sxs-lookup"><span data-stu-id="6bbad-113">First, use the instructions in [Install and sign in to the Company Portal app](https://docs.microsoft.com/intune-user-help/install-and-sign-in-to-the-intune-company-portal-app-ios) to customize the Microsoft Intune Company Portal app for your test environment.</span></span>

<span data-ttu-id="6bbad-114">Im nächsten Schritt verwenden Sie die Anweisungen in [Richten Sie Ihre Unternehmensressourcen zugreifen,](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios) einer iOS-Geräte zu registrieren.</span><span class="sxs-lookup"><span data-stu-id="6bbad-114">Next, use the instructions in [Set up access to your company resources](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios) to enroll an iOS device.</span></span>

<span data-ttu-id="6bbad-115">Im nächsten Schritt verwenden Sie die Anweisungen in [Registrieren Ihrer Android-Gerät im Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-android) Android-Gerät zu registrieren.</span><span class="sxs-lookup"><span data-stu-id="6bbad-115">Next, use the instructions in [Enroll your Android device in Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-android) to enroll an Android device.</span></span>

## <a name="phase-3-manage-your-ios-and-android-devices-remotely"></a><span data-ttu-id="6bbad-116">Phase 3: Verwalten Sie Ihrer iOS und Android-Geräte Remote</span><span class="sxs-lookup"><span data-stu-id="6bbad-116">Phase 3: Manage your iOS and Android devices remotely</span></span>

<span data-ttu-id="6bbad-p103">Bietet Microsoft Intune remote sperren und die Kennung Funktionen zurückgesetzt. Wenn eine Person ihr Gerät verliert, können Sie das Gerät Remote sperren. Wenn eine Person ihre Kennung vergisst, können Sie es Remote zurücksetzen.</span><span class="sxs-lookup"><span data-stu-id="6bbad-p103">Microsoft Intune provides both remote lock and passcode reset capabilities. If someone loses their device, you can lock the device remotely. If someone forgets their passcode, you can reset it remotely.</span></span>
  
<span data-ttu-id="6bbad-120">Um eine IOS- oder Android-Gerät remote zu sperren:</span><span class="sxs-lookup"><span data-stu-id="6bbad-120">To lock an iOS or Android device remotely:</span></span>

1. <span data-ttu-id="6bbad-121">Melden Sie sich bei der Azure-Portal unter [https://portal.azure.com](https://portal.azure.com) mit den Anmeldeinformationen Ihres Kontos globaler Administrator.</span><span class="sxs-lookup"><span data-stu-id="6bbad-121">Sign in to the Azure portal at [https://portal.azure.com](https://portal.azure.com) with the credentials of your global administrator account.</span></span>
2. <span data-ttu-id="6bbad-122">Klicken Sie auf **alle Dienste**, geben Sie **Intune**, und klicken Sie dann auf **Intune**.</span><span class="sxs-lookup"><span data-stu-id="6bbad-122">Click **All services**, type **Intune**, and then click **Intune**.</span></span>
3. <span data-ttu-id="6bbad-123">Klicken Sie auf **Geräte > alle Geräte**.</span><span class="sxs-lookup"><span data-stu-id="6bbad-123">Click **Devices > All devices**.</span></span>
4. <span data-ttu-id="6bbad-124">Klicken Sie in der Liste der Geräte auf eine IOS- oder Android-Gerät, und klicken Sie dann auf die Aktion **Remote Sperren** .</span><span class="sxs-lookup"><span data-stu-id="6bbad-124">In the list of devices, click an iOS or Android device, and then click the **Remote lock** action.</span></span>

    
<span data-ttu-id="6bbad-125">So setzen Sie den Zugangscode remote zurück</span><span class="sxs-lookup"><span data-stu-id="6bbad-125">To reset the passcode remotely:</span></span>

1. <span data-ttu-id="6bbad-126">Falls erforderlich, melden Sie sich bei der Azure-Portal unter [https://portal.azure.com](https://portal.azure.com) mit den Anmeldeinformationen Ihres Kontos globaler Administrator.</span><span class="sxs-lookup"><span data-stu-id="6bbad-126">If needed, sign in to the Azure portal at [https://portal.azure.com](https://portal.azure.com) with the credentials of your global administrator account.</span></span>
2. <span data-ttu-id="6bbad-127">Klicken Sie auf **alle Dienste**, geben Sie **Intune**, und klicken Sie dann auf **Intune**.</span><span class="sxs-lookup"><span data-stu-id="6bbad-127">Click **All services**, type **Intune**, and then click **Intune**.</span></span>
3. <span data-ttu-id="6bbad-128">Klicken Sie auf **Geräte > alle Geräte**.</span><span class="sxs-lookup"><span data-stu-id="6bbad-128">Click **Devices > All devices**.</span></span>
4. <span data-ttu-id="6bbad-p104">Aus der Liste der Geräte verwalten, klicken Sie auf eine IOS- oder Android-Gerät und wählen Sie **... Weitere**. Wählen Sie dann die **Kennung entfernen** Gerät remote-Aktion aus.</span><span class="sxs-lookup"><span data-stu-id="6bbad-p104">From the list of devices you manage, click an iOS or Android device, and choose **...More**. Then choose the **Remove passcode** device remote action.</span></span>

<span data-ttu-id="6bbad-131">Weitere Versuche finden Sie unter [verfügbare Gerät Aktionen](https://docs.microsoft.com/intune/device-management#available-device-actions).</span><span class="sxs-lookup"><span data-stu-id="6bbad-131">For additional experimentation, see [Available device actions](https://docs.microsoft.com/intune/device-management#available-device-actions).</span></span>

    

> [!TIP]
> <span data-ttu-id="6bbad-132">Klicken Sie [hier](http://aka.ms/catlgstack), um eine visuelle Darstellung aller Artikel im Stapel der Testumgebungsanleitungen in der Microsoft Cloud zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="6bbad-132">Click [here](http://aka.ms/catlgstack) for a visual map to all of the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="6bbad-133">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="6bbad-133">See Also</span></span>

[<span data-ttu-id="6bbad-134">Die Microsoft 365 Enterprise-Entwicklungs-/Testumgebung</span><span class="sxs-lookup"><span data-stu-id="6bbad-134">The Microsoft 365 Enterprise dev/test environment</span></span>](the-microsoft-365-enterprise-dev-test-environment.md)
  
[<span data-ttu-id="6bbad-135">Richtlinien für die Microsoft 365 Enterprise Test-/Umgebung MAM</span><span class="sxs-lookup"><span data-stu-id="6bbad-135">MAM policies for your Microsoft 365 Enterprise dev/test environment</span></span>](mam-policies-for-your-microsoft-365-enterprise-dev-test-environment.md)
  
[<span data-ttu-id="6bbad-136">Testumgebungsanleitungen (TLGs) zur Cloudakzeptanz</span><span class="sxs-lookup"><span data-stu-id="6bbad-136">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)

[<span data-ttu-id="6bbad-137">Enterprise-Mobilität + Sicherheit (zur Abstimmung)</span><span class="sxs-lookup"><span data-stu-id="6bbad-137">Enterprise Mobility + Security (EMS)</span></span>](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)


