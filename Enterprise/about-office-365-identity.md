---
title: Office 365-Identitätsmodelle und Azure Active Directory
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.date: 05/20/2019
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- M365-identity-device-management
- M365-security-compliance
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 06a189e7-5ec6-4af2-94bf-a22ea225a7a9
description: Hier erfahren Sie, wie Benutzeridentitäten in Office 365 verwaltet werden.
ms.openlocfilehash: f6e871f03fb99feea05293c425406b6be7dfedd5
ms.sourcegitcommit: f316aef1c122f8eb25c43a56bc894c4aa61c8e0c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/20/2019
ms.locfileid: "38745668"
---
# <a name="office-365-identity-models-and-azure-active-directory"></a><span data-ttu-id="4e27b-103">Office 365-Identitätsmodelle und Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="4e27b-103">Office 365 identity models and Azure Active Directory</span></span>

<span data-ttu-id="4e27b-104">*Dieser Artikel bezieht sich sowohl auf Office 365 Enterprise als auch auf Microsoft 365 Enterprise.*</span><span class="sxs-lookup"><span data-stu-id="4e27b-104">*This article applies to both Office 365 Enterprise and Microsoft 365 Enterprise.*</span></span>

<span data-ttu-id="4e27b-105">Office 365 verwendet Azure Active Directory (Azure AD), einen cloudbasierten Benutzeridentitäts- und Authentifizierungsdienst, der in Ihrem Office 365-Abonnement enthalten ist, um Identitäten und Authentifizierung für Office 365 zu verwalten.</span><span class="sxs-lookup"><span data-stu-id="4e27b-105">Office 365 uses Azure Active Directory (Azure AD), a cloud-based user identity and authentication service that is included with your Office 365 subscription, to manage identities and authentication for Office 365.</span></span> <span data-ttu-id="4e27b-106">Die ordnungsgemäße Konfiguration Ihrer Identitätsinfrastruktur ist entscheidend für die Verwaltung des Office 365-Benutzerzugriffs und der Berechtigungen für Ihre Organisation.</span><span class="sxs-lookup"><span data-stu-id="4e27b-106">Getting your identity infrastructure configured correctly is vital to managing Office 365 user access and permissions for your organization.</span></span>

<span data-ttu-id="4e27b-107">Bevor Sie beginnen, schauen Sie sich dieses Video an, um eine Übersicht über die Identitätsmodelle und Authentifizierung für Office 365 und Microsoft 365 zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="4e27b-107">Before you begin, watch this video for an overview of identity models and authentication for both Office 365 and Microsoft 365.</span></span>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE2Pjwu]

<span data-ttu-id="4e27b-108">Die erste Entscheidung, die Sie bei der Planung treffen müssen, betrifft das Office 365-Identitätsmodell.</span><span class="sxs-lookup"><span data-stu-id="4e27b-108">Your first planning choice is the Office 365 identity model.</span></span>

## <a name="office-365-identity-models"></a><span data-ttu-id="4e27b-109">Office 365-Identitätsmodelle</span><span class="sxs-lookup"><span data-stu-id="4e27b-109">Office 365 identity models</span></span>

<span data-ttu-id="4e27b-110">Um Benutzerkonten zu planen, müssen Sie zunächst die beiden Identitätsmodelle in Microsoft 365 verstehen.</span><span class="sxs-lookup"><span data-stu-id="4e27b-110">To plan for user accounts, you first need to understand the two identity models in Microsoft 365.</span></span> <span data-ttu-id="4e27b-111">Sie können die Identitäten Ihrer Organisation nur in der Cloud verwalten, oder Sie können Ihre lokalen AD DS-Identitäten (Active Directory Domain Services) verwalten und diese zur Authentifizierung verwenden, wenn Benutzer auf Microsoft 365-Clouddienste zugreifen.</span><span class="sxs-lookup"><span data-stu-id="4e27b-111">You can maintain your organization's identities only in the cloud, or you can maintain your on-premises Active Directory Domain Services (AD DS) identities and use them for authentication when users access Microsoft 365 cloud services.</span></span>  

<span data-ttu-id="4e27b-112">Nachfolgend finden Sie die beiden Identitätstypen sowie deren beste Anwendungsfälle und Vorteile.</span><span class="sxs-lookup"><span data-stu-id="4e27b-112">Here are the two types of identity and their best fit and benefits.</span></span>

|||
|:-------|:-----|:-----|
|  | <span data-ttu-id="4e27b-113">**Reine Cloudidentität**</span><span class="sxs-lookup"><span data-stu-id="4e27b-113">**Cloud-only identity**</span></span> | <span data-ttu-id="4e27b-114">**Hybrididentität**</span><span class="sxs-lookup"><span data-stu-id="4e27b-114">**Hybrid identity**</span></span> |
| <span data-ttu-id="4e27b-115">**Definition**</span><span class="sxs-lookup"><span data-stu-id="4e27b-115">**Definition**</span></span> | <span data-ttu-id="4e27b-116">Ein Benutzerkonto ist nur im Azure Active Directory-Mandanten (Azure AD) für Ihr Microsoft 365-Abonnement vorhanden.</span><span class="sxs-lookup"><span data-stu-id="4e27b-116">User account only exists in the Azure Active Directory (Azure AD) tenant for your Microsoft 365 subscription.</span></span> | <span data-ttu-id="4e27b-117">Ein Benutzerkonto ist in AD DS vorhanden, und eine Kopie befindet sich auch im Azure AD-Mandanten für Ihr Microsoft 365-Abonnement.</span><span class="sxs-lookup"><span data-stu-id="4e27b-117">User account exists in AD DS and a copy is also in the Azure AD tenant for your Microsoft 365 subscription.</span></span> <span data-ttu-id="4e27b-118">Das Benutzerkonto in Azure AD enthält möglicherweise auch eine Hashversion des Kennworts für das Benutzerkonto.</span><span class="sxs-lookup"><span data-stu-id="4e27b-118">The user account in Azure AD might also include a hashed version of the user account password.</span></span> |
| <span data-ttu-id="4e27b-119">**Authentifizierung von Benutzeranmeldeinformationen durch Microsoft 365**</span><span class="sxs-lookup"><span data-stu-id="4e27b-119">**How Microsoft 365 authenticates user credentials**</span></span> | <span data-ttu-id="4e27b-120">Der Azure AD-Mandant für Ihr Microsoft 365-Abonnement führt die Authentifizierung mit dem Cloudidentitätskonto durch.</span><span class="sxs-lookup"><span data-stu-id="4e27b-120">The Azure AD tenant for your Microsoft 365 subscription performs the authentication with the cloud identity account.</span></span> | <span data-ttu-id="4e27b-121">Der Azure AD-Mandant für Ihr Microsoft 365-Abonnement behandelt verarbeitet entweder den Authentifizierungsprozess oder leitet den Benutzer an einen anderen Identitätsanbieter weiter.</span><span class="sxs-lookup"><span data-stu-id="4e27b-121">The Azure AD tenant for your Microsoft 365 subscription either handles the authentication process or redirects the user to another identity provider.</span></span> |
| <span data-ttu-id="4e27b-122">**Ideal für**</span><span class="sxs-lookup"><span data-stu-id="4e27b-122">**Best for**</span></span> | <span data-ttu-id="4e27b-123">Organisationen, die keinen lokalen AD DS besitzen oder benötigen.</span><span class="sxs-lookup"><span data-stu-id="4e27b-123">Organizations that do not have or need an on-premises AD DS.</span></span> | <span data-ttu-id="4e27b-124">Organisationen, die AD DS oder einen anderen Identitätsanbieter verwenden.</span><span class="sxs-lookup"><span data-stu-id="4e27b-124">Organizations using AD DS or another identity provider.</span></span> |
| <span data-ttu-id="4e27b-125">**Größter Vorteil**</span><span class="sxs-lookup"><span data-stu-id="4e27b-125">**Greatest benefit**</span></span> | <span data-ttu-id="4e27b-126">Einfach zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="4e27b-126">Simple to use.</span></span> <span data-ttu-id="4e27b-127">Es sind keine zusätzlichen Verzeichnistools oder Server erforderlich.</span><span class="sxs-lookup"><span data-stu-id="4e27b-127">No extra directory tools or servers required.</span></span> | <span data-ttu-id="4e27b-128">Benutzer können dieselben Anmeldeinformationen verwenden, wenn sie auf lokale oder cloudbasierte Ressourcen zugreifen.</span><span class="sxs-lookup"><span data-stu-id="4e27b-128">Users can use the same credentials when accessing on-premises or cloud-based resources.</span></span> |
||||

## <a name="cloud-only-identity"></a><span data-ttu-id="4e27b-129">Reine Cloudidentität</span><span class="sxs-lookup"><span data-stu-id="4e27b-129">Cloud-only identity</span></span>

<span data-ttu-id="4e27b-130">Bei der reinen Cloudidentität werden Benutzerkonten verwendet, die nur in Azure AD vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="4e27b-130">A cloud-only identity uses user accounts that exist only in Azure AD.</span></span> <span data-ttu-id="4e27b-131">Cloudidentitäten werden in der Regel von kleinen Organisationen verwendet, die keine lokalen Server haben oder AD DS nicht zum Verwalten lokaler Identitäten verwenden.</span><span class="sxs-lookup"><span data-stu-id="4e27b-131">Cloud identity is typically used by small organizations that do not have on-premises servers or do not use AD DS to manage local identities.</span></span> 

<span data-ttu-id="4e27b-132">Hier sind die grundlegenden Komponenten der reinen Cloudidentität.</span><span class="sxs-lookup"><span data-stu-id="4e27b-132">Here are the basic components of cloud-only identity.</span></span>
 
![](./media/about-office-365-identity/cloud-only-identity.png)

<span data-ttu-id="4e27b-133">Sowohl lokale als auch Remotebenutzer (Onlinebenutzer) verwenden Ihre Azure AD-Benutzerkonten und Kennwörter für den Zugriff auf Office 365-Clouddienste.</span><span class="sxs-lookup"><span data-stu-id="4e27b-133">Both on-premises and remote (online) users use their Azure AD user accounts and passwords to access Office 365 cloud services.</span></span> <span data-ttu-id="4e27b-134">Azure AD authentifiziert Benutzeranmeldeinformationen basierend auf den gespeicherten Benutzerkonten und Kennwörtern.</span><span class="sxs-lookup"><span data-stu-id="4e27b-134">Azure AD authenticates user credentials based on its stored user accounts and passwords.</span></span>

### <a name="administration"></a><span data-ttu-id="4e27b-135">Verwaltung</span><span class="sxs-lookup"><span data-stu-id="4e27b-135">Administration</span></span>
<span data-ttu-id="4e27b-136">Da Benutzerkonten nur in Azure AD gespeichert sind, verwalten Sie Cloudidentitäten mit Tools wie dem [Microsoft 365 Admin Center ](https://admin.microsoft.com)und Windows PowerShell mit dem Azure Active Directory PowerShell for Graph-Modul.</span><span class="sxs-lookup"><span data-stu-id="4e27b-136">Because user accounts are only stored in Azure AD, you manage cloud identities with tools such as the [Microsoft 365 admin center](https://admin.microsoft.com) and Windows PowerShell with the Azure Active Directory PowerShell for Graph module.</span></span> 

## <a name="hybrid-identity"></a><span data-ttu-id="4e27b-137">Hybrididentität</span><span class="sxs-lookup"><span data-stu-id="4e27b-137">Hybrid identity</span></span>

<span data-ttu-id="4e27b-138">Die Hybrididentität verwendet Konten, die von einem lokalen AD DS stammen und eine Kopie im Azure AD-Mandanten eines Microsoft 365-Abonnements aufweisen.</span><span class="sxs-lookup"><span data-stu-id="4e27b-138">Hybrid identity uses accounts that originate in an on-premises AD DS and have a copy in the Azure AD tenant of a Microsoft 365 subscription.</span></span> <span data-ttu-id="4e27b-139">Die meisten Änderungen fließen jedoch nur in eine Richtung.</span><span class="sxs-lookup"><span data-stu-id="4e27b-139">However, most changes only flow one way.</span></span> <span data-ttu-id="4e27b-140">Änderungen, die Sie an AD DS-Benutzerkonten vornehmen, werden mit Ihrer Kopie in Azure AD synchronisiert.</span><span class="sxs-lookup"><span data-stu-id="4e27b-140">Changes that you make to AD DS user accounts are synchronized to their copy in Azure AD.</span></span> <span data-ttu-id="4e27b-141">Änderungen, die in cloudbasierten Konten in Azure AD vorgenommen wurden, wie z. B. neue Benutzerkonten, werden jedoch nicht mit AD DS synchronisiert.</span><span class="sxs-lookup"><span data-stu-id="4e27b-141">But changes made to cloud-based accounts in Azure AD, such as new user accounts, are not synchronized with AD DS.</span></span>

<span data-ttu-id="4e27b-142">Azure AD Connect bietet die laufende Kontosynchronisierung.</span><span class="sxs-lookup"><span data-stu-id="4e27b-142">Azure AD Connect provides the ongoing account synchronization.</span></span> <span data-ttu-id="4e27b-143">Es wird auf einem lokalen Server ausgeführt, überprüft auf Änderungen in AD DS und leitet diese Änderungen an Azure AD weiter.</span><span class="sxs-lookup"><span data-stu-id="4e27b-143">It runs on an on-premises server, checks for changes in the AD DS, and forwards those changes to Azure AD.</span></span> <span data-ttu-id="4e27b-144">Azure AD Connect bietet die Möglichkeit zu filtern, welche Konten synchronisiert werden, und ob eine Hashversion der Benutzerkennwörter synchronisiert werden soll; dies wird als „Kennworthashsynchronisierung“ (Password hash synchronization, PHS) bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="4e27b-144">Azure AD Connect provides the ability to filter which accounts are synchronized and whether to synchronize a hashed version of user passwords, known as password hash synchronization (PHS).</span></span>

<span data-ttu-id="4e27b-145">Wenn Sie die Hybrididentität implementieren, ist Ihr lokales AD DS die autorisierende Quelle für Kontoinformationen.</span><span class="sxs-lookup"><span data-stu-id="4e27b-145">When you implement hybrid identity, your on-premises AD DS is the authoritative source for account information.</span></span> <span data-ttu-id="4e27b-146">Dies bedeutet, dass Sie Verwaltungsaufgaben hauptsächlich lokal durchführen, die dann mit Azure AD synchronisiert werden.</span><span class="sxs-lookup"><span data-stu-id="4e27b-146">This means that you perform administration tasks mostly on-premises, which are then synchronized to Azure AD.</span></span> 

<span data-ttu-id="4e27b-147">Nachfolgend finden Sie die Komponenten der Hybrididentität.</span><span class="sxs-lookup"><span data-stu-id="4e27b-147">Here are the components of hybrid identity.</span></span>

![](./media/about-office-365-identity/hybrid-identity.png)

<span data-ttu-id="4e27b-148">Der Azure AD-Mandant hat eine Kopie der AD DS-Konten.</span><span class="sxs-lookup"><span data-stu-id="4e27b-148">The Azure AD tenant has a copy of the AD DS accounts.</span></span> <span data-ttu-id="4e27b-149">In dieser Konfiguration authentifizieren sich sowohl lokale als auch Remotebenutzer beim Zugriff auf Microsoft 365-Clouddienste bei Azure AD.</span><span class="sxs-lookup"><span data-stu-id="4e27b-149">In this configuration, both on-premises and remote users accessing Microsoft 365 cloud services authenticate against Azure AD.</span></span>

>[!Note]
><span data-ttu-id="4e27b-150">Sie müssen immer Azure AD Connect verwenden, um Benutzerkonten für die Hybrididentität zu synchronisieren.</span><span class="sxs-lookup"><span data-stu-id="4e27b-150">You always need to use Azure AD Connect to synchronize user accounts for hybrid identity.</span></span> <span data-ttu-id="4e27b-151">Sie benötigen die synchronisierten Benutzerkonten in Azure AD, um die Lizenzzuweisung und Gruppenverwaltung durchzuführen, um Berechtigungen zu konfigurieren und um andere Verwaltungsaufgaben auszuführen, die Benutzerkonten umfassen.</span><span class="sxs-lookup"><span data-stu-id="4e27b-151">You need the synchronized user accounts in Azure AD to perform license assignment and group management, configure permissions, and other administrative tasks that involve user accounts.</span></span>
>

### <a name="administration"></a><span data-ttu-id="4e27b-152">Verwaltung</span><span class="sxs-lookup"><span data-stu-id="4e27b-152">Administration</span></span>

<span data-ttu-id="4e27b-153">Da die ursprünglichen und autorisierenden Benutzerkonten im lokalen AD DS gespeichert sind, verwalten Sie Ihre Identitäten mit den gleichen Tools wie AD DS, z. B. mit dem Tool „Active Directory-Benutzer und -Computer“.</span><span class="sxs-lookup"><span data-stu-id="4e27b-153">Because the original and authoritative user accounts are stored in the on-premises AD DS, you manage your identities with the same tools as AD DS, such as the Active Directory Users and Computers tool.</span></span> 

<span data-ttu-id="4e27b-154">Sie verwenden nicht das Microsoft 365 Admin Center oder Windows PowerShell zum Verwalten von synchronisierten Benutzerkonten in Azure AD.</span><span class="sxs-lookup"><span data-stu-id="4e27b-154">You don’t use the Microsoft 365 admin center or Windows PowerShell to manage synchronized user accounts in Azure AD.</span></span>

## <a name="next-step"></a><span data-ttu-id="4e27b-155">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="4e27b-155">Next step</span></span>

<span data-ttu-id="4e27b-156">Weitere Informationen zum rein cloudbasierten Identitätsmodell finden Sie unter [Reine Cloudidentitäten](cloud-only-identities.md).</span><span class="sxs-lookup"><span data-stu-id="4e27b-156">If you need the cloud-only identity model, see [Cloud-only identities](cloud-only-identities.md).</span></span>

<span data-ttu-id="4e27b-157">Wenn Sie das Hybrididentitätsmodell benötigen, lesen Sie die Informationen unter [Verzeichnissynchronisierung](plan-for-directory-synchronization.md).</span><span class="sxs-lookup"><span data-stu-id="4e27b-157">If you need the hybrid identity model, see [directory synchronization](plan-for-directory-synchronization.md).</span></span>
  

## <a name="video-training"></a><span data-ttu-id="4e27b-158">Videoschulung</span><span class="sxs-lookup"><span data-stu-id="4e27b-158">Video training</span></span>

<span data-ttu-id="4e27b-159">Sehen Sie sich den Videokurs [Office 365: Verwalten von Identitäten mithilfe von Azure AD Connect](https://support.office.com/article/90991a1d-c0ab-479a-b413-35c9706f6fed.aspx) an, das Ihnen von LinkedIn Learning bereitgestellt wird.</span><span class="sxs-lookup"><span data-stu-id="4e27b-159">See the video course [Office 365: Manage Identities Using Azure AD Connect](https://support.office.com/article/90991a1d-c0ab-479a-b413-35c9706f6fed.aspx), brought to you by LinkedIn Learning.</span></span>

## <a name="see-also"></a><span data-ttu-id="4e27b-160">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="4e27b-160">See also</span></span>

[<span data-ttu-id="4e27b-161">Übersicht zu Microsoft 365 Enterprise</span><span class="sxs-lookup"><span data-stu-id="4e27b-161">Microsoft 365 Enterprise overview</span></span>](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-overview)
