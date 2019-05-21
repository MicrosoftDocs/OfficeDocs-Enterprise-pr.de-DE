---
title: Office 365 Identitäts Modelle und Azure Active Directory
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
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
description: Erfahren Sie, wie die Benutzeridentität in Office 365 verwaltet wird.
ms.openlocfilehash: 421002825842201fa754b4c5579dc04fde37eeaf
ms.sourcegitcommit: 2a7177c666dce3c00462b97463a6855e9e3a81f0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/20/2019
ms.locfileid: "34249463"
---
# <a name="office-365-identity-models-and-azure-active-directory"></a><span data-ttu-id="b0660-103">Office 365 Identitäts Modelle und Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="b0660-103">Office 365 identity models and Azure Active Directory</span></span>

<span data-ttu-id="b0660-104">Office 365 verwendet Azure Active Directory (Azure AD), eine Cloud-basierte Benutzeridentität und einen Authentifizierungsdienst, der in Ihrem Office 365-Abonnement enthalten ist, um Identitäten und Authentifizierung für Office 365 zu verwalten.</span><span class="sxs-lookup"><span data-stu-id="b0660-104">Office 365 uses Azure Active Directory (Azure AD), a cloud-based user identity and authentication service that is included with your Office 365 subscription, to manage identities and authentication for Office 365.</span></span> <span data-ttu-id="b0660-105">Die ordnungsgemäße Konfiguration Ihrer Identitätsinfrastruktur ist für die Verwaltung Office 365 Benutzerzugriffs und der Berechtigungen für Ihre Organisation unerlässlich.</span><span class="sxs-lookup"><span data-stu-id="b0660-105">Getting your identity infrastructure configured correctly is vital to managing Office 365 user access and permissions for your organization.</span></span>

<span data-ttu-id="b0660-106">Bevor Sie beginnen, sehen Sie sich dieses Video an, um eine Übersicht über Identitäts Modelle und Authentifizierung für Office 365 und Microsoft 365 zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="b0660-106">Before you begin, watch this video for an overview of identity models and authentication for both Office 365 and Microsoft 365.</span></span>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE2Pjwu]

<span data-ttu-id="b0660-107">Ihre erste Planungs Wahl ist das Office 365 Identitätsmodell.</span><span class="sxs-lookup"><span data-stu-id="b0660-107">Your first planning choice is the Office 365 identity model.</span></span>

## <a name="office-365-identity-models"></a><span data-ttu-id="b0660-108">Office 365 Identitäts Modelle</span><span class="sxs-lookup"><span data-stu-id="b0660-108">Office 365 identity models</span></span>

<span data-ttu-id="b0660-109">Um Benutzerkonten zu planen, müssen Sie zunächst die beiden Identitäts Modelle in Microsoft 365 verstehen.</span><span class="sxs-lookup"><span data-stu-id="b0660-109">To plan for user accounts, you first need to understand the two identity models in Microsoft 365.</span></span> <span data-ttu-id="b0660-110">Sie können die Identitäten Ihrer Organisation nur in der Cloud verwalten, oder Sie können Ihre lokalen Active Directory-Domänendienste (AD DS)-Identitäten beibehalten und für die Authentifizierung verwenden, wenn Benutzer auf Microsoft 365 Cloud Services zugreifen.</span><span class="sxs-lookup"><span data-stu-id="b0660-110">You can maintain your organization's identities only in the cloud, or you can maintain your on-premises Active Directory Domain Services (AD DS) identities and use them for authentication when users access Microsoft 365 cloud services.</span></span>  

<span data-ttu-id="b0660-111">Hier sind die beiden Arten von Identität und Ihre beste Anpassung und Vorteile.</span><span class="sxs-lookup"><span data-stu-id="b0660-111">Here are the two types of identity and their best fit and benefits.</span></span>

|||
|:-------|:-----|:-----|
|  | <span data-ttu-id="b0660-112">**Nur Cloud-Identität**</span><span class="sxs-lookup"><span data-stu-id="b0660-112">**Cloud-only identity**</span></span> | <span data-ttu-id="b0660-113">**Hybrid Identität**</span><span class="sxs-lookup"><span data-stu-id="b0660-113">**Hybrid identity**</span></span> |
| <span data-ttu-id="b0660-114">**Definition**</span><span class="sxs-lookup"><span data-stu-id="b0660-114">**Definition**</span></span> | <span data-ttu-id="b0660-115">Das Benutzerkonto ist nur im Azure Active Directory (Azure AD)-Mandanten für Ihr Microsoft 365-Abonnement vorhanden.</span><span class="sxs-lookup"><span data-stu-id="b0660-115">User account only exists in the Azure Active Directory (Azure AD) tenant for your Microsoft 365 subscription.</span></span> | <span data-ttu-id="b0660-116">Das Benutzerkonto ist in AD DS vorhanden, und eine Kopie befindet sich auch im Azure AD-Mandanten für Ihr Microsoft 365-Abonnement.</span><span class="sxs-lookup"><span data-stu-id="b0660-116">User account exists in AD DS and a copy is also in the Azure AD tenant for your Microsoft 365 subscription.</span></span> <span data-ttu-id="b0660-117">Das Benutzerkonto in Azure AD kann auch eine gehashte Version des Benutzerkontokennworts enthalten.</span><span class="sxs-lookup"><span data-stu-id="b0660-117">The user account in Azure AD might also include a hashed version of the user account password.</span></span> |
| <span data-ttu-id="b0660-118">**So authentifiziert Microsoft 365 Benutzeranmeldeinformationen**</span><span class="sxs-lookup"><span data-stu-id="b0660-118">**How Microsoft 365 authenticates user credentials**</span></span> | <span data-ttu-id="b0660-119">Der Azure AD Mandant für Ihr Microsoft 365-Abonnement führt die Authentifizierung mit dem Cloud-Identitätskonto aus.</span><span class="sxs-lookup"><span data-stu-id="b0660-119">The Azure AD tenant for your Microsoft 365 subscription performs the authentication with the cloud identity account.</span></span> | <span data-ttu-id="b0660-120">Der Azure AD Mandant für Ihr Microsoft 365-Abonnement verarbeitet entweder den Authentifizierungsprozess oder leitet den Benutzer an einen anderen Identitätsanbieter um.</span><span class="sxs-lookup"><span data-stu-id="b0660-120">The Azure AD tenant for your Microsoft 365 subscription either handles the authentication process or redirects the user to another identity provider.</span></span> |
| <span data-ttu-id="b0660-121">**Am besten für**</span><span class="sxs-lookup"><span data-stu-id="b0660-121">**Best for**</span></span> | <span data-ttu-id="b0660-122">Organisationen, die keine lokale AD DS haben oder benötigen.</span><span class="sxs-lookup"><span data-stu-id="b0660-122">Organizations that do not have or need an on-premises AD DS.</span></span> | <span data-ttu-id="b0660-123">Organisationen, die AD DS oder einen anderen Identitätsanbieter verwenden.</span><span class="sxs-lookup"><span data-stu-id="b0660-123">Organizations using AD DS or another identity provider.</span></span> |
| <span data-ttu-id="b0660-124">**Größter Vorteil**</span><span class="sxs-lookup"><span data-stu-id="b0660-124">**Greatest benefit**</span></span> | <span data-ttu-id="b0660-125">Einfach zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="b0660-125">Simple to use.</span></span> <span data-ttu-id="b0660-126">Keine zusätzlichen Verzeichnis Tools oder Server erforderlich.</span><span class="sxs-lookup"><span data-stu-id="b0660-126">No extra directory tools or servers required.</span></span> | <span data-ttu-id="b0660-127">Benutzer können beim Zugriff auf lokale oder Cloud-basierte Ressourcen dieselben Anmeldeinformationen verwenden.</span><span class="sxs-lookup"><span data-stu-id="b0660-127">Users can use the same credentials when accessing on-premises or cloud-based resources.</span></span> |
||||

## <a name="cloud-only-identity"></a><span data-ttu-id="b0660-128">Nur Cloud-Identität</span><span class="sxs-lookup"><span data-stu-id="b0660-128">Cloud-only identity</span></span>

<span data-ttu-id="b0660-129">Eine Cloud-only-Identität verwendet Benutzerkonten, die nur in Azure AD vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="b0660-129">A cloud-only identity uses user accounts that exist only in Azure AD.</span></span> <span data-ttu-id="b0660-130">Die Cloud-Identität wird in der Regel von kleinen Organisationen verwendet, die nicht über lokale Server verfügen oder AD DS nicht zum Verwalten lokaler Identitäten verwenden.</span><span class="sxs-lookup"><span data-stu-id="b0660-130">Cloud identity is typically used by small organizations that do not have on-premises servers or do not use AD DS to manage local identities.</span></span> 

<span data-ttu-id="b0660-131">Hier sind die grundlegenden Komponenten der reinen cloudbasierten Identität.</span><span class="sxs-lookup"><span data-stu-id="b0660-131">Here are the basic components of cloud-only identity.</span></span>
 
![](./media/about-office-365-identity/cloud-only-identity.png)

<span data-ttu-id="b0660-132">Sowohl lokale als auch Remotebenutzer verwenden Ihre Azure AD Benutzerkonten und Kennwörter für den Zugriff auf Office 365 Cloud-Dienste.</span><span class="sxs-lookup"><span data-stu-id="b0660-132">Both on-premises and remote (online) users use their Azure AD user accounts and passwords to access Office 365 cloud services.</span></span> <span data-ttu-id="b0660-133">Azure AD authentifiziert Benutzeranmeldeinformationen basierend auf den gespeicherten Benutzerkonten und Kennwörtern.</span><span class="sxs-lookup"><span data-stu-id="b0660-133">Azure AD authenticates user credentials based on its stored user accounts and passwords.</span></span>

### <a name="administration"></a><span data-ttu-id="b0660-134">Verwaltung</span><span class="sxs-lookup"><span data-stu-id="b0660-134">Administration</span></span>
<span data-ttu-id="b0660-135">Da Benutzerkonten nur in Azure AD gespeichert werden, verwalten Sie Cloud-Identitäten mit Tools wie dem [Microsoft 365 Admin Center](https://admin.microsoft.com) und Windows PowerShell mit dem Azure Active Directory PowerShell für Graph-Modul.</span><span class="sxs-lookup"><span data-stu-id="b0660-135">Because user accounts are only stored in Azure AD, you manage cloud identities with tools such as the [Microsoft 365 admin center](https://admin.microsoft.com) and Windows PowerShell with the Azure Active Directory PowerShell for Graph module.</span></span> 

## <a name="hybrid-identity"></a><span data-ttu-id="b0660-136">Hybrid Identität</span><span class="sxs-lookup"><span data-stu-id="b0660-136">Hybrid identity</span></span>

<span data-ttu-id="b0660-137">Hybrid Identity verwendet Konten, die in einer lokalen AD DS stammen und über eine Kopie im Azure AD Mandanten eines Microsoft 365-Abonnements verfügen.</span><span class="sxs-lookup"><span data-stu-id="b0660-137">Hybrid identity uses accounts that originate in an on-premises AD DS and have a copy in the Azure AD tenant of a Microsoft 365 subscription.</span></span> <span data-ttu-id="b0660-138">Die meisten Änderungen fließen jedoch nur in eine Richtung.</span><span class="sxs-lookup"><span data-stu-id="b0660-138">However, most changes only flow one way.</span></span> <span data-ttu-id="b0660-139">Änderungen, die Sie an AD DS Benutzerkonten vornehmen, werden mit Ihrer Kopie in Azure AD synchronisiert.</span><span class="sxs-lookup"><span data-stu-id="b0660-139">Changes that you make to AD DS user accounts are synchronized to their copy in Azure AD.</span></span> <span data-ttu-id="b0660-140">Änderungen, die an cloudbasierten Konten in Azure AD vorgenommen werden, wie beispielsweise neue Benutzerkonten, werden jedoch nicht mit AD DS synchronisiert.</span><span class="sxs-lookup"><span data-stu-id="b0660-140">But changes made to cloud-based accounts in Azure AD, such as new user accounts, are not synchronized with AD DS.</span></span>

<span data-ttu-id="b0660-141">Azure AD Connect stellt die laufende Konto Synchronisierung bereit.</span><span class="sxs-lookup"><span data-stu-id="b0660-141">Azure AD Connect provides the ongoing account synchronization.</span></span> <span data-ttu-id="b0660-142">Er wird auf einem lokalen Server ausgeführt, überprüft auf Änderungen im AD DS und leitet diese Änderungen an Azure AD weiter.</span><span class="sxs-lookup"><span data-stu-id="b0660-142">It runs on an on-premises server, checks for changes in the AD DS, and forwards those changes to Azure AD.</span></span> <span data-ttu-id="b0660-143">Azure AD Connect bietet die Möglichkeit, zu filtern, welche Konten synchronisiert werden, und ob eine gehashte Version von Benutzerkennwörtern synchronisiert werden soll, die als Password Hash Synchronization (PHS) bezeichnet wird.</span><span class="sxs-lookup"><span data-stu-id="b0660-143">Azure AD Connect provides the ability to filter which accounts are synchronized and whether to synchronize a hashed version of user passwords, known as password hash synchronization (PHS).</span></span>

<span data-ttu-id="b0660-144">Wenn Sie die Hybrid Identität implementieren, ist Ihre lokale AD DS die autorisierende Quelle für Kontoinformationen.</span><span class="sxs-lookup"><span data-stu-id="b0660-144">When you implement hybrid identity, your on-premises AD DS is the authoritative source for account information.</span></span> <span data-ttu-id="b0660-145">Dies bedeutet, dass Sie Verwaltungsaufgaben meist lokal ausführen, die dann mit Azure AD synchronisiert werden.</span><span class="sxs-lookup"><span data-stu-id="b0660-145">This means that you perform administration tasks mostly on-premises, which are then synchronized to Azure AD.</span></span> 

<span data-ttu-id="b0660-146">Hier sind die Komponenten der Hybrid Identität.</span><span class="sxs-lookup"><span data-stu-id="b0660-146">Here are the components of hybrid identity.</span></span>

![](./media/about-office-365-identity/hybrid-identity.png)

<span data-ttu-id="b0660-147">Der Azure AD Mandant verfügt über eine Kopie der AD DS Konten.</span><span class="sxs-lookup"><span data-stu-id="b0660-147">The Azure AD tenant has a copy of the AD DS accounts.</span></span> <span data-ttu-id="b0660-148">In dieser Konfiguration authentifizieren sich sowohl lokale als auch Remotebenutzer, die auf Microsoft 365 Cloud Services zugreifen, bei Azure AD.</span><span class="sxs-lookup"><span data-stu-id="b0660-148">In this configuration, both on-premises and remote users accessing Microsoft 365 cloud services authenticate against Azure AD.</span></span>

>[!Note]
><span data-ttu-id="b0660-149">Sie müssen immer Azure AD Connect verwenden, um Benutzerkonten für die Hybrid Identität zu synchronisieren.</span><span class="sxs-lookup"><span data-stu-id="b0660-149">You always need to use Azure AD Connect to synchronize user accounts for hybrid identity.</span></span> <span data-ttu-id="b0660-150">Sie benötigen die synchronisierten Benutzerkonten in Azure AD, um die Lizenzzuweisung und Gruppenverwaltung, Berechtigungen konfigurieren und andere administrative Aufgaben, die Benutzerkonten umfassen, auszuführen.</span><span class="sxs-lookup"><span data-stu-id="b0660-150">You need the synchronized user accounts in Azure AD to perform license assignment and group management, configure permissions, and other administrative tasks that involve user accounts.</span></span>
>

### <a name="administration"></a><span data-ttu-id="b0660-151">Verwaltung</span><span class="sxs-lookup"><span data-stu-id="b0660-151">Administration</span></span>

<span data-ttu-id="b0660-152">Da die ursprünglichen und autorisierenden Benutzerkonten in der lokalen AD DS gespeichert werden, verwalten Sie Ihre Identitäten mit denselben Tools wie AD DS, beispielsweise das Tool Active Directory Benutzer und Computer.</span><span class="sxs-lookup"><span data-stu-id="b0660-152">Because the original and authoritative user accounts are stored in the on-premises AD DS, you manage your identities with the same tools as AD DS, such as the Active Directory Users and Computers tool.</span></span> 

<span data-ttu-id="b0660-153">Sie verwenden nicht das Microsoft 365 Admin Center oder Windows PowerShell zum Verwalten synchronisierter Benutzerkonten in Azure AD.</span><span class="sxs-lookup"><span data-stu-id="b0660-153">You don’t use the Microsoft 365 admin center or Windows PowerShell to manage synchronized user accounts in Azure AD.</span></span>

## <a name="next-step"></a><span data-ttu-id="b0660-154">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="b0660-154">Next step</span></span>

<span data-ttu-id="b0660-155">Wenn Sie das Cloud-only-Identitätsmodell benötigen, lesen Sie [nur Cloud-Identitäten](cloud-only-identities.md).</span><span class="sxs-lookup"><span data-stu-id="b0660-155">If you need the cloud-only identity model, see [Cloud-only identities](cloud-only-identities.md).</span></span>

<span data-ttu-id="b0660-156">Wenn Sie das hybride Identitätsmodell benötigen, lesen Sie die Informationen unter [Verzeichnissynchronisierung](plan-for-directory-synchronization.md).</span><span class="sxs-lookup"><span data-stu-id="b0660-156">If you need the hybrid identity model, see [directory synchronization](plan-for-directory-synchronization.md).</span></span>
  

## <a name="video-training"></a><span data-ttu-id="b0660-157">Videoschulung</span><span class="sxs-lookup"><span data-stu-id="b0660-157">Video training</span></span>

<span data-ttu-id="b0660-158">Weitere Informationen finden Sie unter Video Kurs [Office 365: Verwalten von Identitäten mit Azure AD Connect](https://support.office.com/article/90991a1d-c0ab-479a-b413-35c9706f6fed.aspx), die Ihnen von LinkedIn Learning zur Verbringung bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="b0660-158">See the video course [Office 365: Manage Identities Using Azure AD Connect](https://support.office.com/article/90991a1d-c0ab-479a-b413-35c9706f6fed.aspx), brought to you by LinkedIn Learning.</span></span>
