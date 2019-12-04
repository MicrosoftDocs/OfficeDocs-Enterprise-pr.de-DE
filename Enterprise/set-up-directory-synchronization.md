---
title: Einrichten der Verzeichnissynchronisierung für Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/03/2019
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
ms.openlocfilehash: 5cd56eb90e6421d530ff0c2b8739bd13be238eae
ms.sourcegitcommit: a9804062071939b7b7e60da5b69f484ce1d34ff8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/04/2019
ms.locfileid: "39814593"
---
# <a name="set-up-directory-synchronization-for-office-365"></a><span data-ttu-id="9b169-103">Einrichten der Verzeichnissynchronisierung für Office 365</span><span class="sxs-lookup"><span data-stu-id="9b169-103">Set up directory synchronization for Office 365</span></span>

<span data-ttu-id="9b169-104">*Dieser Artikel gilt sowohl für Office 365 Enterprise als auch Microsoft 365 Enterprise*.</span><span class="sxs-lookup"><span data-stu-id="9b169-104">*This article applies to both Office 365 Enterprise and Microsoft 365 Enterprise.*</span></span>

<span data-ttu-id="9b169-105">Office 365 verwendet einen Azure Active Directory-Mandanten (Azure AD) zum Speichern und Verwalten von Identitäten für die Authentifizierung und Berechtigung zum Zugriff auf Cloud-basierte Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="9b169-105">Office 365 uses an Azure Active Directory (Azure AD) tenant to store and manage identities for authentication and permissions to access cloud-based resources.</span></span> 

<span data-ttu-id="9b169-106">Wenn Sie über lokale Active Directory Domain Services (AD DS) verfügen, können Sie Ihre AD DS-Benutzerkonten, -Gruppen und -Kontakte mit dem Azure AD-Mandanten Ihres Office 365-Abonnements synchronisieren.</span><span class="sxs-lookup"><span data-stu-id="9b169-106">If you have an on-premises Active Directory Domain Services (AD DS), you can synchronize your AD DS user accounts, groups, and contacts with the Azure AD tenant of your Office 365 subscription.</span></span> <span data-ttu-id="9b169-107">Dies ist Hybrididentität für Office 365.</span><span class="sxs-lookup"><span data-stu-id="9b169-107">This is hybrid identity for Office 365.</span></span> <span data-ttu-id="9b169-108">Dies sind ihre Komponenten.</span><span class="sxs-lookup"><span data-stu-id="9b169-108">Here are its components.</span></span>

![](./media/about-office-365-identity/hybrid-identity.png)

<span data-ttu-id="9b169-109">Azure AD Connect wird auf einem lokalen Server ausgeführt und synchronisiert Ihre AD DS mit dem Azure AD-Mandanten.</span><span class="sxs-lookup"><span data-stu-id="9b169-109">Azure AD Connect runs on an on-premises server and synchronizes your AD DS with the Azure AD tenant.</span></span> <span data-ttu-id="9b169-110">Zusammen mit der Verzeichnissynchronisierung können Sie auch die folgenden Authentifizierungsoptionen angeben:</span><span class="sxs-lookup"><span data-stu-id="9b169-110">Along with directory synchronization, you can also specify these authentication options:</span></span>

- <span data-ttu-id="9b169-111">Kennworthashsynchronisierung (Password hash synchronization, PHS)</span><span class="sxs-lookup"><span data-stu-id="9b169-111">Password hash synchronization (PHS)</span></span>

  <span data-ttu-id="9b169-112">Azure AD führt die Authentifizierung selbst durch.</span><span class="sxs-lookup"><span data-stu-id="9b169-112">Azure AD performs the authentication itself.</span></span>

- <span data-ttu-id="9b169-113">Passthrough-Authentifizierung (PTA)</span><span class="sxs-lookup"><span data-stu-id="9b169-113">Pass-through authentication (PTA)</span></span>

  <span data-ttu-id="9b169-114">Azure AD lässt AD DS die Authentifizierung durchführen.</span><span class="sxs-lookup"><span data-stu-id="9b169-114">Azure AD has AD DS perform the authentication.</span></span>

- <span data-ttu-id="9b169-115">Verbundauthentifizierung</span><span class="sxs-lookup"><span data-stu-id="9b169-115">Federated authentication</span></span>

  <span data-ttu-id="9b169-116">Azure AD leitet den Clientcomputer um, der die Authentifizierung anfordert, um einen anderen Identitätsanbieter zu kontaktieren.</span><span class="sxs-lookup"><span data-stu-id="9b169-116">Azure AD redirects the client computer requesting authentication to contact another identity provider.</span></span>

<span data-ttu-id="9b169-117">Weitere Informationen finden Sie unter [Hybrididentitäten](plan-for-directory-synchronization.md).</span><span class="sxs-lookup"><span data-stu-id="9b169-117">See [Hybrid identities](plan-for-directory-synchronization.md) for more information.</span></span>
  
## <a name="1-review-prerequisites-for-azure-ad-connect"></a><span data-ttu-id="9b169-118">1. Voraussetzungen für Azure AD Connect überprüfen</span><span class="sxs-lookup"><span data-stu-id="9b169-118">1. Review prerequisites for Azure AD Connect</span></span>

<span data-ttu-id="9b169-119">Sie erhalten ein kostenloses Azure AD-Abonnement mit Ihrem Office 365-Abonnement.</span><span class="sxs-lookup"><span data-stu-id="9b169-119">You get a free Azure AD subscription with your Office 365 subscription.</span></span> <span data-ttu-id="9b169-120">Wenn Sie die Verzeichnissynchronisierung einrichten, installieren Sie Azure AD Connect auf einem Ihrer lokalen Server.</span><span class="sxs-lookup"><span data-stu-id="9b169-120">When you set up directory synchronization, you will install Azure AD Connect on one of your on-premises servers.</span></span>
  
<span data-ttu-id="9b169-121">Für Office 365 müssen Sie:</span><span class="sxs-lookup"><span data-stu-id="9b169-121">For Office 365 you'll need to:</span></span>
  
- <span data-ttu-id="9b169-122">Ihre lokale Domäne hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="9b169-122">Verify your on-premises domain.</span></span> <span data-ttu-id="9b169-123">Der Azure AD Connect-Assistent führt Sie schrittweise durch diesen Vorgang.</span><span class="sxs-lookup"><span data-stu-id="9b169-123">The Azure AD Connect wizard guides you through this.</span></span>
- <span data-ttu-id="9b169-124">Die Benutzernamen und Kennwörter für die Administratorkonten Ihres Office 365-Mandanten und AD DS bereithalten.</span><span class="sxs-lookup"><span data-stu-id="9b169-124">Obtain the user names and passwords for the admin accounts of your Office 365 tenant and AD DS.</span></span>

<span data-ttu-id="9b169-125">Für Ihren lokalen Server, auf dem Sie Azure AD Connect installieren, benötigen Sie Folgendes:</span><span class="sxs-lookup"><span data-stu-id="9b169-125">For your on-premises server on which you install Azure AD Connect, you'll need:</span></span>
  
|<span data-ttu-id="9b169-126">**Server-Betriebssystem**</span><span class="sxs-lookup"><span data-stu-id="9b169-126">**Server OS**</span></span>|<span data-ttu-id="9b169-127">**Weitere Software**</span><span class="sxs-lookup"><span data-stu-id="9b169-127">**Other software**</span></span>|
|:-----|:-----|
|<span data-ttu-id="9b169-128">Windows Server 2012 R2 oder neuer</span><span class="sxs-lookup"><span data-stu-id="9b169-128">Windows Server 2012 R2 and later</span></span> | <span data-ttu-id="9b169-129">– PowerShell wird standardmäßig installiert, keine Aktion erforderlich.</span><span class="sxs-lookup"><span data-stu-id="9b169-129">- PowerShell is installed by default, no action is required.</span></span>  <br> <span data-ttu-id="9b169-130">– .NET 4.5.1 und höhere Versionen werden über Windows Update bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="9b169-130">- Net 4.5.1 and later releases are offered through Windows Update.</span></span> <span data-ttu-id="9b169-131">Vergewissern Sie sich in der Systemsteuerung, dass die neuesten Updates für Windows Server installiert sind.</span><span class="sxs-lookup"><span data-stu-id="9b169-131">Make sure you have installed the latest updates to Windows Server in the Control Panel.</span></span> |
|<span data-ttu-id="9b169-132">Windows Server 2008 R2 mit Service Pack 1 (SP1)\*\* oder Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="9b169-132">Windows Server 2008 R2 with Service Pack 1 (SP1)\*\* or Windows Server 2012</span></span> | <span data-ttu-id="9b169-133">– Die neueste Version von PowerShell finden Sie im Windows Management Framework 4.0.</span><span class="sxs-lookup"><span data-stu-id="9b169-133">- The latest version of PowerShell is available in Windows Management Framework 4.0.</span></span> <span data-ttu-id="9b169-134">Suchen Sie im [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996) danach.</span><span class="sxs-lookup"><span data-stu-id="9b169-134">Search for it on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span></span>  <br> <span data-ttu-id="9b169-135">– .NET 4.5.1 und höhere Versionen finden Sie im [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span><span class="sxs-lookup"><span data-stu-id="9b169-135">- .Net 4.5.1 and later releases are available on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span></span> |
|<span data-ttu-id="9b169-136">Windows Server 2008</span><span class="sxs-lookup"><span data-stu-id="9b169-136">Windows Server 2008</span></span> | <span data-ttu-id="9b169-137">– Die neueste unterstützte Version von PowerShell befindet sich im Windows Management Framework 3.0, das Sie aus dem [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996) herunterladen können.</span><span class="sxs-lookup"><span data-stu-id="9b169-137">- The latest supported version of PowerShell is available in Windows Management Framework 3.0, available on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span></span>  <br> <span data-ttu-id="9b169-138">– .NET 4.5.1 und höhere Versionen finden Sie im [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span><span class="sxs-lookup"><span data-stu-id="9b169-138">- .Net 4.5.1 and later releases are available on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span></span> |

<span data-ttu-id="9b169-139">Zusätzliche Informationen zur Hardware, Software, Anforderungen an Konten, Berechtigungen und SSL Zertifikate sowie zu Objekteinschränkungen für Azure AD Connect finden Sie unter [Voraussetzungen für Azure Active Directory Connect](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-prerequisites).</span><span class="sxs-lookup"><span data-stu-id="9b169-139">See [Prerequisites for Azure Active Directory Connect](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-prerequisites) for the details of hardware, software, account and permissions requirements, SSL certificate requirements, and object limits for Azure AD Connect.</span></span>
  
<span data-ttu-id="9b169-140">Sie können auch den [Versionsveröffentlichungsverlauf](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-version-history) von Azure AD Connect verfolgen, um zu sehen, welche Features und Funktionen in jeder Version enthalten sind und welche Fehler behoben wurden.</span><span class="sxs-lookup"><span data-stu-id="9b169-140">You can also review the Azure AD Connect [version release history](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-version-history) to see what is included and fixed in each release.</span></span>

## <a name="2-install-azure-ad-connect-and-configure-directory-synchronization"></a><span data-ttu-id="9b169-141">2. Installieren von Azure AD Connect und Konfigurieren der Verzeichnissynchronisierung</span><span class="sxs-lookup"><span data-stu-id="9b169-141">2. Install Azure AD Connect and configure directory synchronization</span></span>

<span data-ttu-id="9b169-142">Bevor Sie beginnen, sollten Sie sicherstellen, dass Sie über Folgendes verfügen:</span><span class="sxs-lookup"><span data-stu-id="9b169-142">Before you begin, make sure you have:</span></span>

- <span data-ttu-id="9b169-143">Den Benutzernamen und das Kennwort eines globalen Office 365-Administrators</span><span class="sxs-lookup"><span data-stu-id="9b169-143">The user name and password of an Office 365 global admin</span></span>
- <span data-ttu-id="9b169-144">Den Benutzernamen und das Kennwort des AD-DS-Domänenadministrators.</span><span class="sxs-lookup"><span data-stu-id="9b169-144">The user name and password of an AD DS domain administrator</span></span>
- <span data-ttu-id="9b169-145">Welche Authentifizierungsmethode (PHS, PTA, Federated)</span><span class="sxs-lookup"><span data-stu-id="9b169-145">Which authentication method (PHS, PTA, federated)</span></span>
- <span data-ttu-id="9b169-146">Ob Sie [Azure AD Seamless Single Sign-On (SSO) verwenden möchten](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-sso)</span><span class="sxs-lookup"><span data-stu-id="9b169-146">Whether you want to use [Azure AD Seamless Single Sign-on (SSO)](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-sso)</span></span>

<span data-ttu-id="9b169-147">Führen Sie die folgenden Schritte aus:</span><span class="sxs-lookup"><span data-stu-id="9b169-147">Follow these steps:</span></span>

1. <span data-ttu-id="9b169-148">Melden Sie sich beim [Microsoft 365 Admin Center](https://admin.microsoft.com) an, (https://admin.microsoft.com) und wählen Sie im linken Navigationsbereich **Benutzer** \> \*\* Aktive Benutzer\*\* aus.</span><span class="sxs-lookup"><span data-stu-id="9b169-148">Sign in to the [Microsoft 365 admin center](https://admin.microsoft.com) (https://admin.microsoft.com) and choose **Users** \> **Active Users** on the left navigation.</span></span>
2. <span data-ttu-id="9b169-149">Wählen Sie auf der Seite **aktive Benutzer** die **Verzeichnissynchronisierung** **more** ( \> Three dots) aus.</span><span class="sxs-lookup"><span data-stu-id="9b169-149">On the **Active users** page, choose **More** (three dots) \> **Directory synchronization**.</span></span>
  
3. <span data-ttu-id="9b169-150">Wählen Sie auf der Seite **Azure Active Directory Vorbereitung** die Option **zum Download Center wechseln** aus, um den Link zum Azure AD Connect-Tool zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="9b169-150">On the **Azure Active Directory preparation** page, select the **Go to the Download center to get the Azure AD Connect tool** link to get started.</span></span> 
4. <span data-ttu-id="9b169-151">Folgen Sie den Schritten in [Installationsübersicht: Azure AD Connect und Azure AD Connect Health](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-roadmap).</span><span class="sxs-lookup"><span data-stu-id="9b169-151">Follow the steps in [Azure AD Connect and Azure AD Connect Health installation roadmap](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-roadmap).</span></span>

## <a name="3-finish-setting-up-domains"></a><span data-ttu-id="9b169-152">3. Abschließen der Einrichtung von Domänen</span><span class="sxs-lookup"><span data-stu-id="9b169-152">3. Finish setting up domains</span></span>

<span data-ttu-id="9b169-153">Folgen Sie den Schritten unter [Erstellen von DNS-Einträgen für Office 365, wenn Sie Ihre DNS-Einträge verwalten](https://docs.microsoft.com/office365/admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider), um die Einrichtung Ihrer Domäne abzuschließen.</span><span class="sxs-lookup"><span data-stu-id="9b169-153">Follow the steps in [Create DNS records for Office 365 when you manage your DNS records](https://docs.microsoft.com/office365/admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider) to finish setting up your domains.</span></span>

## <a name="next-step"></a><span data-ttu-id="9b169-154">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="9b169-154">Next step</span></span>

[<span data-ttu-id="9b169-155">Zuweisen von Lizenzen zu Benutzerkonten</span><span class="sxs-lookup"><span data-stu-id="9b169-155">Assign licenses to user accounts</span></span>](assign-licenses-to-user-accounts.md)
