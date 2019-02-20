---
title: Planen der Verzeichnissynchronisierung für Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.audience: Admin
ms.topic: get-started-article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED15
- MBS150
- BCS160
ms.assetid: 1b3b5318-6977-42ed-b5c7-96fa74b08846
description: Erfahren Sie, wie Sie die Verzeichnissynchronisierung zwischen Office 365 und Ihrem lokalen Active Directory einrichten.
ms.openlocfilehash: 5f6e5be2a2137ee183a7d592d9a3e6b086e5be9a
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085264"
---
# <a name="set-up-directory-synchronization-for-office-365"></a><span data-ttu-id="89240-103">Planen der Verzeichnissynchronisierung für Office 365</span><span class="sxs-lookup"><span data-stu-id="89240-103">Set up directory synchronization for Office 365</span></span>

<span data-ttu-id="89240-p101">In Office 365 wird der Cloud-basierte Benutzer Identitäts Verwaltungsdienst Azure Active Directory zum Verwalten von Benutzern verwendet. Sie können Ihr lokales Active Directory auch mit Azure AD integrieren, indem Sie Ihre lokale Umgebung mit Office 365 synchronisieren. Nachdem Sie die Synchronisierung eingerichtet haben, können Sie entscheiden, ob die Benutzerauthentifizierung innerhalb von Azure AD oder in Ihrem lokalen Verzeichnis erfolgen soll.</span><span class="sxs-lookup"><span data-stu-id="89240-p101">Office 365 uses the cloud-based user identity management service Azure Active Directory to manage users. You can also integrate your on-premises Active Directory with Azure AD by synchronizing your on-premises environment with Office 365. Once you set up synchronization you can decide to have their user authentication take place within Azure AD or within your on-premises directory.</span></span>
  
## <a name="office-365-directory-synchronization"></a><span data-ttu-id="89240-107">Office 365-Verzeichnissynchronisierung</span><span class="sxs-lookup"><span data-stu-id="89240-107">Office 365 directory synchronization</span></span>

<span data-ttu-id="89240-p102">Sie können entweder eine synchronisierte Identität oder eine Verbundidentität zwischen Ihrer lokalen Organisation und Office 365 verwenden. Mit synchronisierter Identität verwalten Sie Ihre Benutzer lokal und werden von Azure AD authentifiziert, wenn Sie das gleiche Kennwort in der Cloud als lokal verwenden. Dies ist das häufigste Szenario für die Verzeichnissynchronisierung. Mit der Passthrough-Authentifizierung oder der Verbundidentität können Sie Ihre Benutzer lokal verwalten und durch Ihr lokales Verzeichnis authentifizieren. Die Verbundidentität erfordert eine zusätzliche Konfiguration und ermöglicht es den Benutzern, sich nur einmal anzumelden. Weitere Informationen finden Sie unter [understandIng Office 365 Identity und Azure Active Directory](about-office-365-identity.md).</span><span class="sxs-lookup"><span data-stu-id="89240-p102">You can either use synchronized identity or federated identity between your on-premises organization and Office 365. With synchronized identity, you manage your users on-premises, and they are authenticated by Azure AD when they use the same password in the cloud as on-premises. This is the most common directory synchronization scenario. Pass-through authentication or Federated identity, allows you to manage your users on-premises and they are authenticated by your on-premises directory. Federated identity requires additional configuration and enables your users to only sign in once. For details, read [Understanding Office 365 Identity and Azure Active Directory](about-office-365-identity.md).</span></span>
  
## <a name="want-to-upgrade-from-windows-azure-active-directory-sync-dirsync-to-azure-active-directory-connect"></a><span data-ttu-id="89240-114">Möchten Sie ein Upgrade von Windows Azure Active Directory Sync (dirSync) auf Azure Active Directory Connect durchführen?</span><span class="sxs-lookup"><span data-stu-id="89240-114">Want to upgrade from Windows Azure Active Directory sync (DirSync) to Azure Active Directory Connect?</span></span>

<span data-ttu-id="89240-115">Wenn Sie derzeit dirSync verwenden und ein Upgrade durchführen möchten, wechseln Sie zu [Azure.com](https://azure.com) . [](https://go.microsoft.com/fwlink/p/?LinkId=733240)</span><span class="sxs-lookup"><span data-stu-id="89240-115">If you are currently using DirSync and want to upgrade, head over to [azure.com](https://azure.com) for [upgrade instructions](https://go.microsoft.com/fwlink/p/?LinkId=733240).</span></span>
  
## <a name="prerequisites-for-azure-ad-connect"></a><span data-ttu-id="89240-116">VoraussetZungen für Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="89240-116">Prerequisites for Azure AD Connect</span></span>

<span data-ttu-id="89240-p103">Sie erhalten ein kostenloses Abonnement für Azure AD mit Ihrem Office 365-Abonnement. Wenn Sie die Verzeichnissynchronisierung einrichten, installieren Sie Azure Active Directory Connect auf einem Ihrer lokalen Server.</span><span class="sxs-lookup"><span data-stu-id="89240-p103">You get a free subscription to Azure AD with your Office 365 subscription. When you set up directory synchronization, you will install Azure Active Directory Connect on one of your on-premises servers.</span></span>
  
<span data-ttu-id="89240-119">Für Office 365 müssen Sie Folgendes tun:</span><span class="sxs-lookup"><span data-stu-id="89240-119">For Office 365 you will need to:</span></span>
  
- <span data-ttu-id="89240-120">ÜberPrüfen Sie Ihre lokale Domäne (das Verfahren führt Sie durch.)</span><span class="sxs-lookup"><span data-stu-id="89240-120">Verify your on-premises domain (the procedure will guide you through this).</span></span>
- <span data-ttu-id="89240-121">[Weisen Sie Administratorrollen in office 365 for Business](https://support.office.com/article/EAC4D046-1AFD-4F1A-85FC-8219C79E1504) -Berechtigungen für ihren Office 365-Mandanten und ein lokales Active Directory zu.</span><span class="sxs-lookup"><span data-stu-id="89240-121">Have [Assign admin roles in Office 365 for business](https://support.office.com/article/EAC4D046-1AFD-4F1A-85FC-8219C79E1504) permissions for your Office 365 tenant and on-premises Active Directory.</span></span>

<span data-ttu-id="89240-122">Für den lokalen Server, auf dem Sie Azure AD Connect installieren, benötigen Sie die folgende Software:</span><span class="sxs-lookup"><span data-stu-id="89240-122">For your on-premises server on which you install Azure AD Connect you will need the following software:</span></span>
  
|<span data-ttu-id="89240-123">**Server Betriebssystem**</span><span class="sxs-lookup"><span data-stu-id="89240-123">**Server OS**</span></span>|<span data-ttu-id="89240-124">**Weitere Software**</span><span class="sxs-lookup"><span data-stu-id="89240-124">**Other software**</span></span>|
|:-----|:-----|
|<span data-ttu-id="89240-125">**Windows Server 2012 R2**</span><span class="sxs-lookup"><span data-stu-id="89240-125">**Windows Server 2012 R2**</span></span> | <span data-ttu-id="89240-126">-PowerShell wird standardmäßig installiert, es ist keine Aktion erforderlich.</span><span class="sxs-lookup"><span data-stu-id="89240-126">- PowerShell is installed by default, no action is required.</span></span>  <br> <span data-ttu-id="89240-p104">-NET 4.5.1 und späteren Versionen werden über Windows Update angeboten. Stellen Sie sicher, dass Sie die neuesten Updates für Windows Server in der Systemsteuerung installiert haben.</span><span class="sxs-lookup"><span data-stu-id="89240-p104">- Net 4.5.1 and later releases are offered through Windows Update. Make sure you have installed the latest updates to Windows Server in the Control Panel.</span></span> |
|<span data-ttu-id="89240-129">**Windows server 2008 R2 mit Service Pack 1 (SP1)** oder **Windows Server 2012**</span><span class="sxs-lookup"><span data-stu-id="89240-129">**Windows Server 2008 R2 with Service Pack 1 (SP1)** or **Windows Server 2012**</span></span> | <span data-ttu-id="89240-p105">-Die neueste Version von PowerShell ist in Windows Management Framework 4,0 verfügbar. Suchen Sie im [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996)danach.</span><span class="sxs-lookup"><span data-stu-id="89240-p105">- The latest version of PowerShell is available in Windows Management Framework 4.0. Search for it on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).  </span></span><br> <span data-ttu-id="89240-132">-.NET 4.5.1 und neuere Versionen sind im [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996)verfügbar.</span><span class="sxs-lookup"><span data-stu-id="89240-132">- .Net 4.5.1 and later releases are available on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span></span> |
|<span data-ttu-id="89240-133">**Windows Server 2008**</span><span class="sxs-lookup"><span data-stu-id="89240-133">**Windows Server 2008**</span></span> | <span data-ttu-id="89240-134">-Die neueste unterstützte Version von PowerShell ist in Windows Management Framework 3,0 verfügbar, verfügbar im [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span><span class="sxs-lookup"><span data-stu-id="89240-134">- The latest supported version of PowerShell is available in Windows Management Framework 3.0, available on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span></span>  <br> <span data-ttu-id="89240-135">-.NET 4.5.1 und neuere Versionen sind im [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996)verfügbar.</span><span class="sxs-lookup"><span data-stu-id="89240-135">- .Net 4.5.1 and later releases are available on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span></span> |

> [!NOTE]
> <span data-ttu-id="89240-p106">Wenn Sie Azure Active Directory dirSync verwenden, beträgt die maximale Anzahl von Verteilergruppenmitgliedern, die Sie von Ihrem lokalen Active Directory mit Azure Active Directory synchronisieren können, 15.000. Für Azure AD Connect ist diese Nummer 50.000.</span><span class="sxs-lookup"><span data-stu-id="89240-p106">If you're using Azure Active Directory DirSync, the maximum number of distribution group members that you can synchronize from your on-premises Active Directory to Azure Active Directory is 15,000. For Azure AD Connect, that number is 50,000.</span></span> 
  
<span data-ttu-id="89240-138">Lesen Sie die [vorausSetzungen für Azure Active Directory Connect](https://go.microsoft.com/fwlink/p/?LinkId=716896), um die Anforderungen an Hardware, Software, Konten und Berechtigungen, SSL-Zertifikatanforderungen und Objekt Grenzwerte für Azure AD Connect genauer zu prüfen.</span><span class="sxs-lookup"><span data-stu-id="89240-138">To more carefully review hardware, software, account and permissions requirements, SSL certificate requirements, and object limits for Azure AD Connect, read [Prerequisites for Azure Active Directory Connect](https://go.microsoft.com/fwlink/p/?LinkId=716896).</span></span>
  
<span data-ttu-id="89240-139">Sie können auch den [Versionsverlauf](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-version-history) der Azure AD Connect-Version überprüfen, um zu sehen, was in jeder Version enthalten und korrigiert wurde.</span><span class="sxs-lookup"><span data-stu-id="89240-139">You can also review the Azure AD Connect [version release history](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-version-history) to see what is included and fixed in each release.</span></span>

## <a name="to-set-up-directory-synchronization"></a><span data-ttu-id="89240-140">So richten Sie die Verzeichnissynchronisierung ein</span><span class="sxs-lookup"><span data-stu-id="89240-140">To set up directory synchronization</span></span>

1. <span data-ttu-id="89240-141">melden sie sich beim Office 365 admin center an, und wählen sie im linken navigationsbereich **benutzer** \> **aktive benutzer** aus.</span><span class="sxs-lookup"><span data-stu-id="89240-141">Sign in to the Office 365 admin center and choose **Users** \> **Active Users** on the left navigation.</span></span>
2. <span data-ttu-id="89240-142">wählen sie im Office 365 admin center auf der seite **aktive benutzer** **mehr** \> **verzeichnissynchronisierung**aus.</span><span class="sxs-lookup"><span data-stu-id="89240-142">In the Office 365 admin center, on the **Active users** page, choose **More** \> **Directory synchronization**.</span></span>

    ![Wählen Sie im Menü mehr die Option Verzeichnissynchronisierung aus.](media/dc6669e5-c01b-471e-9cdf-04f5d44e1c4b.png)
  
3. <span data-ttu-id="89240-p107">Wählen Sie auf der Seite **Active Directory-Vorbereitung** den Link zum **herunterladen des Microsoft Azure Active Directory Connect-Tool** für erste Schritte aus. Weitere Informationen zum Installieren von Azure Active Directory Connect finden Sie unter [Azure AD Connect and Azure AD Connect Health Installation Roadmap](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-roadmap).</span><span class="sxs-lookup"><span data-stu-id="89240-p107">On the **Active Directory preparation** page, select the **Download Microsoft Azure Active Directory Connect tool** link to get started. For more information about the Azure Active Directory Connect installation process, see [Azure AD Connect and Azure AD Connect Health installation roadmap](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-roadmap).</span></span>

## <a name="assign-licenses-to-synchronized-users"></a><span data-ttu-id="89240-146">Zuweisen von Lizenzen zu synchronisierten Benutzern</span><span class="sxs-lookup"><span data-stu-id="89240-146">Assign licenses to synchronized users</span></span>

<span data-ttu-id="89240-p108">Nachdem Sie Ihre Benutzer mit Office 365 synchronisiert haben, werden Sie erstellt, aber Sie müssen Ihnen Lizenzen zuweisen, damit Sie Office 365-Features wie e-Mail verwenden können. Anweisungen hierzu finden Sie unter [Zuweisen von Lizenzen zu Benutzern in Office 365 for Business](https://support.office.com/article/997596b5-4173-4627-b915-36abac6786dc).</span><span class="sxs-lookup"><span data-stu-id="89240-p108">After you have synchronized your users to Office 365, they are created but you need to assign licenses to them so they can use Office 365 features, such as mail. For instructions, see [Assign licenses to users in Office 365 for business](https://support.office.com/article/997596b5-4173-4627-b915-36abac6786dc).</span></span>

## <a name="finish-setting-up-domains"></a><span data-ttu-id="89240-149">Abschließen der Einrichtung von Domänen</span><span class="sxs-lookup"><span data-stu-id="89240-149">Finish setting up domains</span></span>

<span data-ttu-id="89240-150">Führen Sie die Schritte unter [Create DNS Records for Office 365 aus, wenn Sie Ihre DNS-Einträge verwalten](https://support.office.com/article/b0f3fdca-8a80-4e8e-9ef3-61e8a2a9ab23) , um die Einrichtung ihrer Domänen abzuschließen.</span><span class="sxs-lookup"><span data-stu-id="89240-150">Follow the steps in [Create DNS records for Office 365 when you manage your DNS records](https://support.office.com/article/b0f3fdca-8a80-4e8e-9ef3-61e8a2a9ab23) to finish setting up your domains.</span></span>