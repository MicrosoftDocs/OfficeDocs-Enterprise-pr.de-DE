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
description: Sie erfahren, wie Sie die Verzeichnissynchronisierung zwischen Office 365 und dem lokalen Active Directory einrichten.
ms.openlocfilehash: 1798c54854bc5ecc82481aaabca3690e7212e135
ms.sourcegitcommit: 36e760407a1f4b18bc108134628ed9a8d3e35a8a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2019
ms.locfileid: "34162478"
---
# <a name="set-up-directory-synchronization-for-office-365"></a><span data-ttu-id="22923-103">Einrichten der Verzeichnissynchronisierung für Office 365</span><span class="sxs-lookup"><span data-stu-id="22923-103">Set up directory synchronization for Office 365</span></span>

<span data-ttu-id="22923-104">Office 365 verwendet einen Azure Active Directory-Mandanten (Azure AD) zum Speichern und Verwalten von Identitäten für die Authentifizierung und Berechtigung zum Zugriff auf Cloud-basierte Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="22923-104">Office 365 uses an Azure Active Directory (Azure AD) tenant to store and manage identities for authentication and permissions to access cloud-based resources.</span></span> 

<span data-ttu-id="22923-105">Wenn Sie über lokale Active Directory Domain Services (AD DS) verfügen, können Sie Ihre AD DS-Benutzerkonten, -Gruppen und -Kontakte mit dem Azure AD-Mandanten Ihres Office 365-Abonnements synchronisieren.</span><span class="sxs-lookup"><span data-stu-id="22923-105">If you have an on-premises Active Directory Domain Services (AD DS), you can synchronize your AD DS user accounts, groups, and contacts with the Azure AD tenant of your Office 365 subscription.</span></span> <span data-ttu-id="22923-106">Dies ist Hybrididentität für Office 365.</span><span class="sxs-lookup"><span data-stu-id="22923-106">This is hybrid identity for Office 365.</span></span> <span data-ttu-id="22923-107">Dies sind ihre Komponenten.</span><span class="sxs-lookup"><span data-stu-id="22923-107">Here are its components.</span></span>

![](./media/about-office-365-identity/hybrid-identity.png)

<span data-ttu-id="22923-108">Azure AD Connect wird auf einem lokalen Server ausgeführt und synchronisiert Ihre AD DS mit dem Azure AD-Mandanten.</span><span class="sxs-lookup"><span data-stu-id="22923-108">Azure AD Connect runs on an on-premises server and synchronizes your AD DS with the Azure AD tenant.</span></span> <span data-ttu-id="22923-109">Zusammen mit der Verzeichnissynchronisierung können Sie auch die folgenden Authentifizierungsoptionen angeben:</span><span class="sxs-lookup"><span data-stu-id="22923-109">Along with directory synchronization, you can also specify these authentication options:</span></span>

- <span data-ttu-id="22923-110">Kennworthashsynchronisierung (Password hash synchronization, PHS)</span><span class="sxs-lookup"><span data-stu-id="22923-110">Password hash synchronization</span></span>

  <span data-ttu-id="22923-111">Azure AD führt die Authentifizierung selbst durch.</span><span class="sxs-lookup"><span data-stu-id="22923-111">Azure AD performs the authentication itself.</span></span>

- <span data-ttu-id="22923-112">Passthrough-Authentifizierung (PTA)</span><span class="sxs-lookup"><span data-stu-id="22923-112">Pass-through authentication (PTA)</span></span>

  <span data-ttu-id="22923-113">Azure AD lässt AD DS die Authentifizierung durchführen.</span><span class="sxs-lookup"><span data-stu-id="22923-113">Azure AD has AD DS perform the authentication.</span></span>

- <span data-ttu-id="22923-114">Verbundauthentifizierung</span><span class="sxs-lookup"><span data-stu-id="22923-114">Federated authentication</span></span>

  <span data-ttu-id="22923-115">Azure AD leitet den Clientcomputer um, der die Authentifizierung anfordert, um einen anderen Identitätsanbieter zu kontaktieren.</span><span class="sxs-lookup"><span data-stu-id="22923-115">Azure AD redirects the client computer requesting authentication to contact another identity provider.</span></span>

<span data-ttu-id="22923-116">Weitere Informationen finden Sie unter [Hybrididentitäten](plan-for-directory-synchronization.md).</span><span class="sxs-lookup"><span data-stu-id="22923-116">See [Hybrid identities](plan-for-directory-synchronization.md) for more information.</span></span>
  
## <a name="1-review-prerequisites-for-azure-ad-connect"></a><span data-ttu-id="22923-117">1. Voraussetzungen für Azure AD Connect überprüfen</span><span class="sxs-lookup"><span data-stu-id="22923-117">1. Review prerequisites for Azure AD Connect</span></span>

<span data-ttu-id="22923-118">Sie erhalten ein kostenloses Azure AD-Abonnement mit Ihrem Office 365-Abonnement.</span><span class="sxs-lookup"><span data-stu-id="22923-118">You get a free Azure AD subscription with your Office 365 subscription.</span></span> <span data-ttu-id="22923-119">Wenn Sie die Verzeichnissynchronisierung einrichten, installieren Sie Azure AD Connect auf einem Ihrer lokalen Server.</span><span class="sxs-lookup"><span data-stu-id="22923-119">When you set up directory synchronization, you will install Azure AD Connect on one of your on-premises servers.</span></span>
  
<span data-ttu-id="22923-120">Für Office 365 müssen Sie:</span><span class="sxs-lookup"><span data-stu-id="22923-120">For Office 365 you'll need to:</span></span>
  
- <span data-ttu-id="22923-121">Ihre lokale Domäne hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="22923-121">Verify your domain</span></span> <span data-ttu-id="22923-122">Der Azure AD Connect-Assistent führt Sie schrittweise durch diesen Vorgang.</span><span class="sxs-lookup"><span data-stu-id="22923-122">The Azure AD Connect wizard guides you through this.</span></span>
- <span data-ttu-id="22923-123">Die Benutzernamen und Kennwörter für die Administratorkonten Ihres Office 365-Mandanten und AD DS bereithalten.</span><span class="sxs-lookup"><span data-stu-id="22923-123">Obtain the user names and passwords for the admin accounts of your Office 365 tenant and AD DS.</span></span>

<span data-ttu-id="22923-124">Für Ihren lokalen Server, auf dem Sie Azure AD Connect installieren, benötigen Sie Folgendes:</span><span class="sxs-lookup"><span data-stu-id="22923-124">For your on-premises server on which you install Azure AD Connect, you'll need:</span></span>
  
|<span data-ttu-id="22923-125">**Server-Betriebssystem**</span><span class="sxs-lookup"><span data-stu-id="22923-125">**Server OS**</span></span>|<span data-ttu-id="22923-126">**Weitere Software**</span><span class="sxs-lookup"><span data-stu-id="22923-126">**Other software**</span></span>|
|:-----|:-----|
|<span data-ttu-id="22923-127">Windows Server 2012 R2 oder neuer</span><span class="sxs-lookup"><span data-stu-id="22923-127">Windows Server 2012 R2 and 2012</span></span> | <span data-ttu-id="22923-128">– PowerShell wird standardmäßig installiert, keine Aktion erforderlich.</span><span class="sxs-lookup"><span data-stu-id="22923-128">- PowerShell is installed by default, no action is required.</span></span>  <br> <span data-ttu-id="22923-129">– .NET 4.5.1 und höhere Versionen werden über Windows Update bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="22923-129">- Net 4.5.1 and later releases are offered through Windows Update.</span></span> <span data-ttu-id="22923-130">Vergewissern Sie sich in der Systemsteuerung, dass die neuesten Updates für Windows Server installiert sind.</span><span class="sxs-lookup"><span data-stu-id="22923-130">Make sure you have installed the latest updates to Windows Server in the Control Panel.</span></span> |
|<span data-ttu-id="22923-131">Windows Server 2008 R2 mit Service Pack 1 (SP1)\*\* oder Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="22923-131">Install SharePoint on Windows Server 2008 R2 Service Pack 1 x64 or Windows Server 2012.</span></span> | <span data-ttu-id="22923-132">– Die neueste Version von PowerShell finden Sie im Windows Management Framework 4.0.</span><span class="sxs-lookup"><span data-stu-id="22923-132">- The latest version of PowerShell is available in Windows Management Framework 4.0.</span></span> <span data-ttu-id="22923-133">Suchen Sie im [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996) danach.</span><span class="sxs-lookup"><span data-stu-id="22923-133">Search for it on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span></span>  <br> <span data-ttu-id="22923-134">– .NET 4.5.1 und höhere Versionen finden Sie im [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span><span class="sxs-lookup"><span data-stu-id="22923-134">- .Net 4.5.1 and later releases are available on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span></span> |
|<span data-ttu-id="22923-135">Windows Server 2008</span><span class="sxs-lookup"><span data-stu-id="22923-135">Windows Server 2008</span></span> | <span data-ttu-id="22923-136">– Die neueste unterstützte Version von PowerShell befindet sich im Windows Management Framework 3.0, das Sie aus dem [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996) herunterladen können.</span><span class="sxs-lookup"><span data-stu-id="22923-136">- The latest supported version of PowerShell is available in Windows Management Framework 3.0, available on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span></span>  <br> <span data-ttu-id="22923-137">– .NET 4.5.1 und höhere Versionen finden Sie im [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span><span class="sxs-lookup"><span data-stu-id="22923-137">- .Net 4.5.1 and later releases are available on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span></span> |

<span data-ttu-id="22923-138">Zusätzliche Informationen zur Hardware, Software, Anforderungen an Konten, Berechtigungen und SSL Zertifikate sowie zu Objekteinschränkungen für Azure AD Connect finden Sie unter [Voraussetzungen für Azure Active Directory Connect](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-prerequisites).</span><span class="sxs-lookup"><span data-stu-id="22923-138">See [Prerequisites for Azure Active Directory Connect](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-prerequisites) for the details of hardware, software, account and permissions requirements, SSL certificate requirements, and object limits for Azure AD Connect.</span></span>
  
<span data-ttu-id="22923-139">Sie können auch den [Versionsveröffentlichungsverlauf](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-version-history) von Azure AD Connect verfolgen, um zu sehen, welche Features und Funktionen in jeder Version enthalten sind und welche Fehler behoben wurden.</span><span class="sxs-lookup"><span data-stu-id="22923-139">You can also review the Azure AD Connect [version release history](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-version-history) to see what is included and fixed in each release.</span></span>

## <a name="2-install-azure-ad-connect-and-configure-directory-synchronization"></a><span data-ttu-id="22923-140">2. Installieren von Azure AD Connect und Konfigurieren der Verzeichnissynchronisierung</span><span class="sxs-lookup"><span data-stu-id="22923-140">2. Install Azure AD Connect and configure directory synchronization</span></span>

<span data-ttu-id="22923-141">Bevor Sie beginnen, sollten Sie sicherstellen, dass Sie über Folgendes verfügen:</span><span class="sxs-lookup"><span data-stu-id="22923-141">Before you begin, make sure you have the following:</span></span>

- <span data-ttu-id="22923-142">Den Benutzernamen und das Kennwort eines globalen Office 365-Administrators</span><span class="sxs-lookup"><span data-stu-id="22923-142">The user name and password of an Office 365 global admin</span></span>
- <span data-ttu-id="22923-143">Den Benutzernamen und das Kennwort des AD-DS-Domänenadministrators.</span><span class="sxs-lookup"><span data-stu-id="22923-143">The user name and password of an AD DS domain administrator</span></span>
- <span data-ttu-id="22923-144">Welche Authentifizierungsmethode (PHS, PTA, Federated)</span><span class="sxs-lookup"><span data-stu-id="22923-144">Which authentication method (PHS, PTA, federated)</span></span>
- <span data-ttu-id="22923-145">Ob Sie [Azure AD Seamless Single Sign-On (SSO) verwenden möchten](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-sso)</span><span class="sxs-lookup"><span data-stu-id="22923-145">Whether you want to use [Azure AD Seamless Single Sign-on (SSO)](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-sso)</span></span>

<span data-ttu-id="22923-146">Führen Sie die folgenden Schritte aus:</span><span class="sxs-lookup"><span data-stu-id="22923-146">Follow these steps:</span></span>

1. <span data-ttu-id="22923-147">Melden Sie sich beim [Microsoft 365 Admin Center](https://admin.microsoft.com) an, (https://admin.microsoft.com) und wählen Sie im linken Navigationsbereich **Benutzer** \> \*\* Aktive Benutzer\*\* aus.</span><span class="sxs-lookup"><span data-stu-id="22923-147">Sign in to the [Microsoft 365 admin center](https://admin.microsoft.com) (https://admin.microsoft.com) and choose **Users** \> **Active Users** on the left navigation.</span></span>
2. <span data-ttu-id="22923-148">Wählen Sie im Admin Center auf der Seite **Aktive Benutzer** die Option **Weitere** \> **Verzeichnissynchronisierung** aus.</span><span class="sxs-lookup"><span data-stu-id="22923-148">In the admin center, on the **Active users** page, choose **More** \> **Directory synchronization**.</span></span>

    ![Wählen Sie im Menü "Mehr" die Option "Verzeichnissynchronisierung" aus](media/dc6669e5-c01b-471e-9cdf-04f5d44e1c4b.png)
  
3. <span data-ttu-id="22923-150">Wählen Sie auf der Seite **Active Directory-Vorbereitung** den Link **Microsoft Azure Active Directory Connect Tool herunterladen** aus, um mit den ersten Schritte zu beginnen.</span><span class="sxs-lookup"><span data-stu-id="22923-150">On the **Active Directory preparation** page, select the **Download Microsoft Azure Active Directory Connect tool** link to get started.</span></span> 
4. <span data-ttu-id="22923-151">Folgen Sie den Schritten in [Installationsübersicht: Azure AD Connect und Azure AD Connect Health](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-roadmap).</span><span class="sxs-lookup"><span data-stu-id="22923-151">Follow the steps in [Azure AD Connect and Azure AD Connect Health installation roadmap](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-roadmap).</span></span>

## <a name="3-finish-setting-up-domains"></a><span data-ttu-id="22923-152">3. Abschließen der Einrichtung von Domänen</span><span class="sxs-lookup"><span data-stu-id="22923-152">3. Finish setting up domains</span></span>

<span data-ttu-id="22923-153">Folgen Sie den Schritten unter [Erstellen von DNS-Einträgen für Office 365, wenn Sie Ihre DNS-Einträge verwalten](https://support.office.com/article/b0f3fdca-8a80-4e8e-9ef3-61e8a2a9ab23), um die Einrichtung Ihrer Domäne abzuschließen.</span><span class="sxs-lookup"><span data-stu-id="22923-153">Follow the steps in [Create DNS records for Office 365 when you manage your DNS records](https://support.office.com/article/b0f3fdca-8a80-4e8e-9ef3-61e8a2a9ab23) to finish setting up your domains.</span></span>

## <a name="next-step"></a><span data-ttu-id="22923-154">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="22923-154">Next step</span></span>

<span data-ttu-id="22923-155">[Zuweisen von Lizenzen zu Benutzerkonten](assign-licenses-to-user-accounts.md).</span><span class="sxs-lookup"><span data-stu-id="22923-155">[Assign licenses to user accounts](assign-licenses-to-user-accounts.md)</span></span>
