---
title: Einrichten der Verzeichnissynchronisierung für Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
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
description: Hier erfahren Sie, wie Sie die Verzeichnissynchronisierung zwischen Office 365 und Ihrem lokalen Active Directory einrichten.
ms.openlocfilehash: 1798c54854bc5ecc82481aaabca3690e7212e135
ms.sourcegitcommit: 36e760407a1f4b18bc108134628ed9a8d3e35a8a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2019
ms.locfileid: "34162478"
---
# <a name="set-up-directory-synchronization-for-office-365"></a><span data-ttu-id="3bc54-103">Einrichten der Verzeichnissynchronisierung für Office 365</span><span class="sxs-lookup"><span data-stu-id="3bc54-103">Set up directory synchronization for Office 365</span></span>

<span data-ttu-id="3bc54-104">Office 365 verwendet einen Azure Active Directory (Azure AD)-Mandanten, um Identitäten für die Authentifizierung und Berechtigungen für den Zugriff auf Cloud-basierte Ressourcen zu speichern und zu verwalten.</span><span class="sxs-lookup"><span data-stu-id="3bc54-104">Office 365 uses an Azure Active Directory (Azure AD) tenant to store and manage identities for authentication and permissions to access cloud-based resources.</span></span> 

<span data-ttu-id="3bc54-105">Wenn Sie über eine lokale Active Directory-Domänendienste (AD DS) verfügen, können Sie Ihre AD DS Benutzerkonten, Gruppen und Kontakte mit dem Azure AD-Mandanten Ihres Office 365 Abonnements synchronisieren.</span><span class="sxs-lookup"><span data-stu-id="3bc54-105">If you have an on-premises Active Directory Domain Services (AD DS), you can synchronize your AD DS user accounts, groups, and contacts with the Azure AD tenant of your Office 365 subscription.</span></span> <span data-ttu-id="3bc54-106">Dies ist eine hybride Identität für Office 365.</span><span class="sxs-lookup"><span data-stu-id="3bc54-106">This is hybrid identity for Office 365.</span></span> <span data-ttu-id="3bc54-107">Hier sind die Komponenten.</span><span class="sxs-lookup"><span data-stu-id="3bc54-107">Here are its components.</span></span>

![](./media/about-office-365-identity/hybrid-identity.png)

<span data-ttu-id="3bc54-108">Azure AD Connect wird auf einem lokalen Server ausgeführt und synchronisiert Ihre AD DS mit dem Azure AD Mandanten.</span><span class="sxs-lookup"><span data-stu-id="3bc54-108">Azure AD Connect runs on an on-premises server and synchronizes your AD DS with the Azure AD tenant.</span></span> <span data-ttu-id="3bc54-109">Neben der Verzeichnissynchronisierung können Sie auch diese Authentifizierungsoptionen angeben:</span><span class="sxs-lookup"><span data-stu-id="3bc54-109">Along with directory synchronization, you can also specify these authentication options:</span></span>

- <span data-ttu-id="3bc54-110">Kennworthash Synchronisierung (PHS)</span><span class="sxs-lookup"><span data-stu-id="3bc54-110">Password hash synchronization (PHS)</span></span>

  <span data-ttu-id="3bc54-111">Azure AD führt die Authentifizierung selbst aus.</span><span class="sxs-lookup"><span data-stu-id="3bc54-111">Azure AD performs the authentication itself.</span></span>

- <span data-ttu-id="3bc54-112">Passthrough-Authentifizierung (PTA)</span><span class="sxs-lookup"><span data-stu-id="3bc54-112">Pass-through authentication (PTA)</span></span>

  <span data-ttu-id="3bc54-113">Azure Ad die Authentifizierung AD DS durchführen.</span><span class="sxs-lookup"><span data-stu-id="3bc54-113">Azure AD has AD DS perform the authentication.</span></span>

- <span data-ttu-id="3bc54-114">Verbundauthentifizierung</span><span class="sxs-lookup"><span data-stu-id="3bc54-114">Federated authentication</span></span>

  <span data-ttu-id="3bc54-115">Azure AD umleitet den Clientcomputer, der die Authentifizierung anfordert, um einen anderen Identitätsanbieter zu kontaktieren.</span><span class="sxs-lookup"><span data-stu-id="3bc54-115">Azure AD redirects the client computer requesting authentication to contact another identity provider.</span></span>

<span data-ttu-id="3bc54-116">Weitere [](plan-for-directory-synchronization.md) Informationen finden Sie unter hybride Identitäten.</span><span class="sxs-lookup"><span data-stu-id="3bc54-116">See [Hybrid identities](plan-for-directory-synchronization.md) for more information.</span></span>
  
## <a name="1-review-prerequisites-for-azure-ad-connect"></a><span data-ttu-id="3bc54-117">1. Überprüfen der Voraussetzungen für Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="3bc54-117">1. Review prerequisites for Azure AD Connect</span></span>

<span data-ttu-id="3bc54-118">Sie erhalten ein kostenloses Azure AD-Abonnement mit Ihrem Office 365-Abonnement.</span><span class="sxs-lookup"><span data-stu-id="3bc54-118">You get a free Azure AD subscription with your Office 365 subscription.</span></span> <span data-ttu-id="3bc54-119">Wenn Sie die Verzeichnissynchronisierung einrichten, installieren Sie Azure AD Connect auf einem Ihrer lokalen Server.</span><span class="sxs-lookup"><span data-stu-id="3bc54-119">When you set up directory synchronization, you will install Azure AD Connect on one of your on-premises servers.</span></span>
  
<span data-ttu-id="3bc54-120">Für Office 365 müssen Sie Folgendes tun:</span><span class="sxs-lookup"><span data-stu-id="3bc54-120">For Office 365 you'll need to:</span></span>
  
- <span data-ttu-id="3bc54-121">Überprüfen Sie Ihre lokale Domäne.</span><span class="sxs-lookup"><span data-stu-id="3bc54-121">Verify your on-premises domain.</span></span> <span data-ttu-id="3bc54-122">Der Assistent für Azure AD Connect führt Sie durch diesen Leitfaden.</span><span class="sxs-lookup"><span data-stu-id="3bc54-122">The Azure AD Connect wizard guides you through this.</span></span>
- <span data-ttu-id="3bc54-123">Rufen Sie die Benutzernamen und Kennwörter für die Administratorkonten Ihres Office 365 Mandanten und AD DS ab.</span><span class="sxs-lookup"><span data-stu-id="3bc54-123">Obtain the user names and passwords for the admin accounts of your Office 365 tenant and AD DS.</span></span>

<span data-ttu-id="3bc54-124">Für den lokalen Server, auf dem Sie Azure AD Connect installieren, benötigen Sie Folgendes:</span><span class="sxs-lookup"><span data-stu-id="3bc54-124">For your on-premises server on which you install Azure AD Connect, you'll need:</span></span>
  
|<span data-ttu-id="3bc54-125">**Server Betriebssystem**</span><span class="sxs-lookup"><span data-stu-id="3bc54-125">**Server OS**</span></span>|<span data-ttu-id="3bc54-126">**Weitere Software**</span><span class="sxs-lookup"><span data-stu-id="3bc54-126">**Other software**</span></span>|
|:-----|:-----|
|<span data-ttu-id="3bc54-127">Windows Server 2012 R2 und höher</span><span class="sxs-lookup"><span data-stu-id="3bc54-127">Windows Server 2012 R2 and later</span></span> | <span data-ttu-id="3bc54-128">-PowerShell wird standardmäßig installiert, es ist keine Aktion erforderlich.</span><span class="sxs-lookup"><span data-stu-id="3bc54-128">- PowerShell is installed by default, no action is required.</span></span>  <br> <span data-ttu-id="3bc54-129">-NET 4.5.1 und höhere Versionen werden über Windows Update angeboten.</span><span class="sxs-lookup"><span data-stu-id="3bc54-129">- Net 4.5.1 and later releases are offered through Windows Update.</span></span> <span data-ttu-id="3bc54-130">Stellen Sie sicher, dass Sie die neuesten Updates für Windows Server in der Systemsteuerung installiert haben.</span><span class="sxs-lookup"><span data-stu-id="3bc54-130">Make sure you have installed the latest updates to Windows Server in the Control Panel.</span></span> |
|<span data-ttu-id="3bc54-131">Windows Server 2008 R2 mit Service Pack 1 (SP1) \* \* oder Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="3bc54-131">Windows Server 2008 R2 with Service Pack 1 (SP1)\*\* or Windows Server 2012</span></span> | <span data-ttu-id="3bc54-132">– Die neueste Version von PowerShell steht in Windows Management Framework 4,0 zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="3bc54-132">- The latest version of PowerShell is available in Windows Management Framework 4.0.</span></span> <span data-ttu-id="3bc54-133">Suchen Sie im [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996)danach.</span><span class="sxs-lookup"><span data-stu-id="3bc54-133">Search for it on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span></span>  <br> <span data-ttu-id="3bc54-134">-.NET 4.5.1 und höhere Versionen sind im [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996)verfügbar.</span><span class="sxs-lookup"><span data-stu-id="3bc54-134">- .Net 4.5.1 and later releases are available on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span></span> |
|<span data-ttu-id="3bc54-135">Windows Server 2008</span><span class="sxs-lookup"><span data-stu-id="3bc54-135">Windows Server 2008</span></span> | <span data-ttu-id="3bc54-136">– Die neueste unterstützte Version von PowerShell steht in Windows Management Framework 3,0 zur Verfügung, das im [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996)verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="3bc54-136">- The latest supported version of PowerShell is available in Windows Management Framework 3.0, available on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span></span>  <br> <span data-ttu-id="3bc54-137">-.NET 4.5.1 und höhere Versionen sind im [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996)verfügbar.</span><span class="sxs-lookup"><span data-stu-id="3bc54-137">- .Net 4.5.1 and later releases are available on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span></span> |

<span data-ttu-id="3bc54-138">Unter [Voraussetzungen für Azure Active Directory Connect](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-prerequisites) finden Sie Informationen zu Hardware-, Software-, Konto-und Berechtigungsanforderungen, SSL-Zertifikatanforderungen und Objekt Grenzwerten für Azure AD Connect.</span><span class="sxs-lookup"><span data-stu-id="3bc54-138">See [Prerequisites for Azure Active Directory Connect](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-prerequisites) for the details of hardware, software, account and permissions requirements, SSL certificate requirements, and object limits for Azure AD Connect.</span></span>
  
<span data-ttu-id="3bc54-139">Sie können auch den [Versionsverlauf von](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-version-history) Azure AD Connect überprüfen, um zu sehen, was in jeder Version enthalten und behoben ist.</span><span class="sxs-lookup"><span data-stu-id="3bc54-139">You can also review the Azure AD Connect [version release history](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-version-history) to see what is included and fixed in each release.</span></span>

## <a name="2-install-azure-ad-connect-and-configure-directory-synchronization"></a><span data-ttu-id="3bc54-140">2. installieren Azure AD verbinden und Konfigurieren der Verzeichnissynchronisierung</span><span class="sxs-lookup"><span data-stu-id="3bc54-140">2. Install Azure AD Connect and configure directory synchronization</span></span>

<span data-ttu-id="3bc54-141">Bevor Sie beginnen, sollten Sie Folgendes sicherstellen:</span><span class="sxs-lookup"><span data-stu-id="3bc54-141">Before you begin, make sure you have:</span></span>

- <span data-ttu-id="3bc54-142">Der Benutzername und das Kennwort eines Office 365 globalen Administrators</span><span class="sxs-lookup"><span data-stu-id="3bc54-142">The user name and password of an Office 365 global admin</span></span>
- <span data-ttu-id="3bc54-143">Der Benutzername und das Kennwort eines AD DS Domänenadministrators</span><span class="sxs-lookup"><span data-stu-id="3bc54-143">The user name and password of an AD DS domain administrator</span></span>
- <span data-ttu-id="3bc54-144">Welche Authentifizierungsmethode (PHS, PTA, Verbund)</span><span class="sxs-lookup"><span data-stu-id="3bc54-144">Which authentication method (PHS, PTA, federated)</span></span>
- <span data-ttu-id="3bc54-145">Ob Sie [Azure AD nahtloses einmaliges Anmelden (Single Sign-on, SSO)](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-sso) verwenden möchten</span><span class="sxs-lookup"><span data-stu-id="3bc54-145">Whether you want to use [Azure AD Seamless Single Sign-on (SSO)](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-sso)</span></span>

<span data-ttu-id="3bc54-146">Führen Sie die folgenden Schritte aus:</span><span class="sxs-lookup"><span data-stu-id="3bc54-146">Follow these steps:</span></span>

1. <span data-ttu-id="3bc54-147">Melden Sie sich beim [Microsoft 365 Admin Center](https://admin.microsoft.com) anhttps://admin.microsoft.com) (und wählen Sie in der linken Navigationsleiste **Benutzer** \> **aktive Benutzer** aus.</span><span class="sxs-lookup"><span data-stu-id="3bc54-147">Sign in to the [Microsoft 365 admin center](https://admin.microsoft.com) (https://admin.microsoft.com) and choose **Users** \> **Active Users** on the left navigation.</span></span>
2. <span data-ttu-id="3bc54-148">Wählen Sie im Admin Center auf der Seite **aktive Benutzer** die Option **Weitere** \> **Verzeichnissynchronisierung**aus.</span><span class="sxs-lookup"><span data-stu-id="3bc54-148">In the admin center, on the **Active users** page, choose **More** \> **Directory synchronization**.</span></span>

    ![Wählen Sie im Menü weitere die Option Verzeichnissynchronisierung aus.](media/dc6669e5-c01b-471e-9cdf-04f5d44e1c4b.png)
  
3. <span data-ttu-id="3bc54-150">Klicken Sie auf der Seite **Active Directory Vorbereitung** auf den Link **Download Microsoft Azure Active Directory Connect Tool** , um erste Schritte zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="3bc54-150">On the **Active Directory preparation** page, select the **Download Microsoft Azure Active Directory Connect tool** link to get started.</span></span> 
4. <span data-ttu-id="3bc54-151">Befolgen Sie die Schritte unter [Azure AD Roadmap Connect and Azure AD Connect Health Installation](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-roadmap).</span><span class="sxs-lookup"><span data-stu-id="3bc54-151">Follow the steps in [Azure AD Connect and Azure AD Connect Health installation roadmap](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-roadmap).</span></span>

## <a name="3-finish-setting-up-domains"></a><span data-ttu-id="3bc54-152">3. Abschließen der Einrichtung von Domänen</span><span class="sxs-lookup"><span data-stu-id="3bc54-152">3. Finish setting up domains</span></span>

<span data-ttu-id="3bc54-153">Befolgen Sie die Schritte unter [Erstellen von DNS-Einträgen für Office 365 beim Verwalten Ihrer DNS-Einträge](https://support.office.com/article/b0f3fdca-8a80-4e8e-9ef3-61e8a2a9ab23) , um die Einrichtung ihrer Domänen abzuschließen.</span><span class="sxs-lookup"><span data-stu-id="3bc54-153">Follow the steps in [Create DNS records for Office 365 when you manage your DNS records](https://support.office.com/article/b0f3fdca-8a80-4e8e-9ef3-61e8a2a9ab23) to finish setting up your domains.</span></span>

## <a name="next-step"></a><span data-ttu-id="3bc54-154">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="3bc54-154">Next step</span></span>

<span data-ttu-id="3bc54-155">[Zuweisen von Lizenzen zu Benutzerkonten](assign-licenses-to-user-accounts.md).</span><span class="sxs-lookup"><span data-stu-id="3bc54-155">[Assign licenses to user accounts](assign-licenses-to-user-accounts.md).</span></span>
