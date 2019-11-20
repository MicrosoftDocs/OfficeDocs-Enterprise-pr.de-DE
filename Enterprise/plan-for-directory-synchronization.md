---
title: Hybride Identitäts-und Verzeichnissynchronisierung für Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: conceptual
ms.date: 05/20/2019
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MOE150
- MET150
ms.assetid: d3577c90-dda5-45ca-afb0-370d2889b10f
description: Beschreibt die Verzeichnissynchronisierung mit Office 365, Active Directory-Domänendienste Bereinigung und dem Azure Active Directory Connect-Tool.
ms.openlocfilehash: 5b91ebfae2250d44c34aed45c00ac09e98b21909
ms.sourcegitcommit: f316aef1c122f8eb25c43a56bc894c4aa61c8e0c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/20/2019
ms.locfileid: "38747085"
---
# <a name="hybrid-identity-and-directory-synchronization-for-office-365"></a><span data-ttu-id="6b88e-103">Hybride Identitäts-und Verzeichnissynchronisierung für Office 365</span><span class="sxs-lookup"><span data-stu-id="6b88e-103">Hybrid identity and directory synchronization for Office 365</span></span>

<span data-ttu-id="6b88e-104">*Dieser Artikel bezieht sich sowohl auf Office 365 Enterprise als auch auf Microsoft 365 Enterprise.*</span><span class="sxs-lookup"><span data-stu-id="6b88e-104">*This article applies to both Office 365 Enterprise and Microsoft 365 Enterprise.*</span></span>

<span data-ttu-id="6b88e-105">Je nach geschäftlichen Anforderungen und technischen Anforderungen ist das hybride Identitätsmodell und die Verzeichnissynchronisierung die häufigste Wahl für Unternehmenskunden, die Office 365 übernehmen.</span><span class="sxs-lookup"><span data-stu-id="6b88e-105">Depending on business needs and technical requirements, the hybrid identity model and directory synchronization is the most common choice for enterprise customers who are adopting Office 365.</span></span> <span data-ttu-id="6b88e-106">Mit der Verzeichnissynchronisierung können Sie Identitäten in Ihrer Active Directory-Domänendienste (AD DS) verwalten, und alle Aktualisierungen an Benutzerkonten, Gruppen und Kontakten werden mit dem Azure Active Directory (Azure AD)-Mandanten Ihres Office 365 Abonnements synchronisiert.</span><span class="sxs-lookup"><span data-stu-id="6b88e-106">Directory synchronization allows you to manage identities in your Active Directory Domain Services (AD DS) and all updates to user accounts, groups, and contacts are synchronized to the Azure Active Directory (Azure AD) tenant of your Office 365 subscription.</span></span>

>[!Note]
><span data-ttu-id="6b88e-107">Wenn AD DS Benutzerkonten zum ersten Mal synchronisiert werden, wird Ihnen nicht automatisch eine Office 365 Lizenz zugewiesen, und es kann nicht auf Office 365 Dienste wie e-Mail zugegriffen werden.</span><span class="sxs-lookup"><span data-stu-id="6b88e-107">When AD DS user accounts are synchronized for the first time, they are not automatically assigned an Office 365 license and cannot access Office 365 services, such as email.</span></span> <span data-ttu-id="6b88e-108">Sie müssen diesen Benutzerkonten entweder einzeln oder dynamisch über eine Gruppenmitgliedschaft eine Lizenz zuweisen.</span><span class="sxs-lookup"><span data-stu-id="6b88e-108">You must assign a license to these user accounts, either individually or dynamically through group membership.</span></span>
>

## <a name="authentication-for-hybrid-identity"></a><span data-ttu-id="6b88e-109">Authentifizierung für Hybrid Identität</span><span class="sxs-lookup"><span data-stu-id="6b88e-109">Authentication for hybrid identity</span></span>

<span data-ttu-id="6b88e-110">Bei der Verwendung des Hybriden Identitätsmodells gibt es zwei Arten von Authentifizierung:</span><span class="sxs-lookup"><span data-stu-id="6b88e-110">There are two types of authentication when using the hybrid identity model:</span></span>

- <span data-ttu-id="6b88e-111">Verwaltete Authentifizierung</span><span class="sxs-lookup"><span data-stu-id="6b88e-111">Managed authentication</span></span>

  <span data-ttu-id="6b88e-112">Azure AD verarbeitet den Authentifizierungsprozess mithilfe einer lokal gespeicherten Hashversion des Kennworts oder sendet die Anmeldeinformationen an einen lokalen Software-Agent, der vom lokalen AD DS authentifiziert werden soll.</span><span class="sxs-lookup"><span data-stu-id="6b88e-112">Azure AD handles the authentication process by using a locally stored hashed version of the password or sends the credentials to an on-premises software agent to be authenticated by the on-premises AD DS.</span></span>

- <span data-ttu-id="6b88e-113">Verbundauthentifizierung</span><span class="sxs-lookup"><span data-stu-id="6b88e-113">Federated authentication</span></span>

  <span data-ttu-id="6b88e-114">Azure AD leitet den Clientcomputer um, der die Authentifizierung anfordert, um einen anderen Identitätsanbieter zu kontaktieren.</span><span class="sxs-lookup"><span data-stu-id="6b88e-114">Azure AD redirects the client computer requesting authentication to contact another identity provider.</span></span>

### <a name="managed-authentication"></a><span data-ttu-id="6b88e-115">Verwaltete Authentifizierung</span><span class="sxs-lookup"><span data-stu-id="6b88e-115">Managed authentication</span></span>

<span data-ttu-id="6b88e-116">Es gibt zwei Arten der verwalteten Authentifizierung:</span><span class="sxs-lookup"><span data-stu-id="6b88e-116">There are two types of managed authentication:</span></span>

- <span data-ttu-id="6b88e-117">Kennworthashsynchronisierung (Password hash synchronization, PHS)</span><span class="sxs-lookup"><span data-stu-id="6b88e-117">Password hash synchronization (PHS)</span></span>

  <span data-ttu-id="6b88e-118">Azure AD führt die Authentifizierung selbst durch.</span><span class="sxs-lookup"><span data-stu-id="6b88e-118">Azure AD performs the authentication itself.</span></span>

- <span data-ttu-id="6b88e-119">Passthrough-Authentifizierung (PTA)</span><span class="sxs-lookup"><span data-stu-id="6b88e-119">Pass-through authentication (PTA)</span></span>

  <span data-ttu-id="6b88e-120">Azure AD lässt AD DS die Authentifizierung durchführen.</span><span class="sxs-lookup"><span data-stu-id="6b88e-120">Azure AD has AD DS perform the authentication.</span></span>


#### <a name="password-hash-synchronization"></a><span data-ttu-id="6b88e-121">Kennworthashsynchronisierung</span><span class="sxs-lookup"><span data-stu-id="6b88e-121">Password hash synchronization</span></span>

<span data-ttu-id="6b88e-122">Mit der Kennworthash Synchronisierung (PHS) synchronisieren Sie Ihre AD DS Benutzerkonten mit Office 365 und verwalten Ihre Benutzer lokal.</span><span class="sxs-lookup"><span data-stu-id="6b88e-122">With password hash synchronization (PHS), you synchronize your AD DS user accounts with Office 365 and manage your users on-premises.</span></span> <span data-ttu-id="6b88e-123">Hashwerte von Benutzerkennwörtern werden von Ihrem AD DS zu Azure AD synchronisiert, sodass die Benutzer das gleiche Kennwort lokal und in der Cloud haben.</span><span class="sxs-lookup"><span data-stu-id="6b88e-123">Hashes of user passwords are synchronized from your AD DS to Azure AD so that the users have the same password on-premises and in the cloud.</span></span> <span data-ttu-id="6b88e-124">Dies ist die einfachste Möglichkeit zum Aktivieren der Authentifizierung für AD DS Identitäten in Azure AD.</span><span class="sxs-lookup"><span data-stu-id="6b88e-124">This is the simplest way to enable authentication for AD DS identities in Azure AD.</span></span> 

![](./media/plan-for-directory-synchronization/phs-authentication.png)

<span data-ttu-id="6b88e-125">Wenn Kennwörter lokal geändert oder zurückgesetzt werden, werden die neuen Kennworthashs mit Azure AD synchronisiert, sodass Ihre Benutzer immer dasselbe Kennwort für Cloud-Ressourcen und lokale Ressourcen verwenden können.</span><span class="sxs-lookup"><span data-stu-id="6b88e-125">When passwords are changed or reset on-premises, the new password hashes are synchronized to Azure AD so that your users can always use the same password for cloud resources and on-premises resources.</span></span> <span data-ttu-id="6b88e-126">Die Benutzerkennwörter werden nie an Azure AD gesendet oder in Azure AD in Klartext gespeichert.</span><span class="sxs-lookup"><span data-stu-id="6b88e-126">The user passwords are never sent to Azure AD or stored in Azure AD in clear text.</span></span> <span data-ttu-id="6b88e-127">Einige Premium Features von Azure AD, beispielsweise Identitätsschutz, erfordern PHS, unabhängig davon, welche Authentifizierungsmethode ausgewählt ist.</span><span class="sxs-lookup"><span data-stu-id="6b88e-127">Some premium features of Azure AD, such as Identity Protection, require PHS regardless of which authentication method is selected.</span></span>
  
<span data-ttu-id="6b88e-128">Weitere Informationen finden Sie unter [Auswählen von PHS](https://docs.microsoft.com/azure/security/azure-ad-choose-authn) .</span><span class="sxs-lookup"><span data-stu-id="6b88e-128">See [choosing PHS](https://docs.microsoft.com/azure/security/azure-ad-choose-authn) to learn more.</span></span>
  
#### <a name="pass-through-authentication"></a><span data-ttu-id="6b88e-129">Pass-Through-Authentifizierung</span><span class="sxs-lookup"><span data-stu-id="6b88e-129">Pass-through authentication</span></span>

<span data-ttu-id="6b88e-130">Die Pass-Through-Authentifizierung (PTA) bietet eine einfache Kennwortüberprüfung für Azure AD Authentifizierungsdienste mit einem Software-Agent, der auf einem oder mehreren lokalen Servern läuft, um die Benutzer direkt mit Ihrem AD DS zu validieren.</span><span class="sxs-lookup"><span data-stu-id="6b88e-130">Pass-through authentication (PTA) provides a simple password validation for Azure AD authentication services using a software agent running on one or more on-premises servers to validate the users directly with your AD DS.</span></span> <span data-ttu-id="6b88e-131">Mit Pass-Through-Authentifizierung (PTA) synchronisieren Sie AD DS Benutzerkonten mit Office 365 und verwalten Ihre Benutzer lokal.</span><span class="sxs-lookup"><span data-stu-id="6b88e-131">With pass-through authentication (PTA), you synchronize AD DS user accounts with Office 365 and manage your users on-premises.</span></span> 

![](./media/plan-for-directory-synchronization/pta-authentication.png)

<span data-ttu-id="6b88e-132">PTA ermöglicht es Ihren Benutzern, sich bei lokalen und Office 365 Ressourcen und Anwendungen mit Ihrem lokalen Konto und Kennwort anzumelden.</span><span class="sxs-lookup"><span data-stu-id="6b88e-132">PTA allows your users to sign in to both on-premises and Office 365 resources and applications using their on-premises account and password.</span></span> <span data-ttu-id="6b88e-133">Mit dieser Konfiguration werden Benutzerkennwörter direkt für Ihr lokales AD DS überprüft, ohne dass Kennworthashs in Azure AD gespeichert werden.</span><span class="sxs-lookup"><span data-stu-id="6b88e-133">This configuration validates users passwords directly against your on-premises AD DS without storing password hashes in Azure AD.</span></span> 

<span data-ttu-id="6b88e-134">PTA richtet sich auch an Organisationen mit einer Sicherheitsanforderung, um lokale Benutzerkonto Zustände, Kennwortrichtlinien und Anmeldezeiten sofort zu erzwingen.</span><span class="sxs-lookup"><span data-stu-id="6b88e-134">PTA is also for organizations with a security requirement to immediately enforce on-premises user account states, password policies, and logon hours.</span></span> 
  
<span data-ttu-id="6b88e-135">Weitere Informationen finden Sie unter [Auswählen von PTA](https://docs.microsoft.com/azure/security/azure-ad-choose-authn) .</span><span class="sxs-lookup"><span data-stu-id="6b88e-135">See [choosing PTA](https://docs.microsoft.com/azure/security/azure-ad-choose-authn) to learn more.</span></span>
  
### <a name="federated-authentication"></a><span data-ttu-id="6b88e-136">Verbundauthentifizierung</span><span class="sxs-lookup"><span data-stu-id="6b88e-136">Federated authentication</span></span>

<span data-ttu-id="6b88e-137">Die Verbundauthentifizierung ist in erster Linie für große Unternehmensorganisationen mit komplexeren Authentifizierungsanforderungen geeignet.</span><span class="sxs-lookup"><span data-stu-id="6b88e-137">Federated authentication is primarily for large enterprise organizations with more complex authentication requirements.</span></span> <span data-ttu-id="6b88e-138">AD DS Identitäten werden mit Office 365 synchronisiert, und Benutzerkonten werden lokal verwaltet.</span><span class="sxs-lookup"><span data-stu-id="6b88e-138">AD DS identities are synchronized with Office 365 and users accounts are managed on-premises.</span></span> <span data-ttu-id="6b88e-139">Bei der Verbundauthentifizierung haben Benutzer das gleiche Kennwort lokal und in der Cloud, und Sie müssen sich nicht erneut anmelden, um Office 365 verwenden zu können.</span><span class="sxs-lookup"><span data-stu-id="6b88e-139">With federated authentication, users have the same password on-premises and in the cloud and they do not have to sign in again to use Office 365.</span></span> 

<span data-ttu-id="6b88e-140">Die Verbundauthentifizierung kann zusätzliche Authentifizierungsanforderungen wie Smartcard-basierte Authentifizierung oder mehrstufige Authentifizierung eines Drittanbieters unterstützen und ist in der Regel erforderlich, wenn Organisationen eine Authentifizierungsanforderung nicht nativ von Azure Ad unterstützt.</span><span class="sxs-lookup"><span data-stu-id="6b88e-140">Federated authentication can support additional authentication requirements, such as smartcard-based authentication or a third-party multi-factor authentication and is typically required when organizations have an authentication requirement not natively supported by Azure AD.</span></span>
 
<span data-ttu-id="6b88e-141">Weitere Informationen finden Sie unter [Choosing Federated Authentication](https://docs.microsoft.com/azure/security/azure-ad-choose-authn) .</span><span class="sxs-lookup"><span data-stu-id="6b88e-141">See [choosing federated authentication](https://docs.microsoft.com/azure/security/azure-ad-choose-authn) to learn more.</span></span>
  
#### <a name="third-party-authentication-and-identity-providers"></a><span data-ttu-id="6b88e-142">Authentifizierungs-und Identitätsanbieter von Drittanbietern</span><span class="sxs-lookup"><span data-stu-id="6b88e-142">Third-party authentication and identity providers</span></span>

<span data-ttu-id="6b88e-143">Lokale Verzeichnisobjekte können mit Office 365 synchronisiert werden, und der Zugriff auf Cloud-Ressourcen wird in erster Linie von einem Drittanbieter-Identitätsanbieter (IDP) verwaltet.</span><span class="sxs-lookup"><span data-stu-id="6b88e-143">On-premises directory objects may be synchronized to Office 365 and cloud resource access is primarily managed by a third-party identity provider (IdP).</span></span> <span data-ttu-id="6b88e-144">Wenn Ihre Organisation eine Drittanbieter-Verbundlösung verwendet, können Sie die Anmeldung mit dieser Lösung für Office 365 konfigurieren, vorausgesetzt, dass die Drittanbieter-Verbundlösung mit Azure AD kompatibel ist.</span><span class="sxs-lookup"><span data-stu-id="6b88e-144">If your organization uses a third-party federation solution, you can configure sign-on with that solution for Office 365 provided that the third-party federation solution is compatible with Azure AD.</span></span>
  
<span data-ttu-id="6b88e-145">Weitere Informationen finden Sie unter [Azure AD Verbund Kompatibilität](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-federation-compatibility) .</span><span class="sxs-lookup"><span data-stu-id="6b88e-145">See [Azure AD federation compatibility](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-federation-compatibility) to learn more.</span></span>
  
## <a name="ad-ds-cleanup"></a><span data-ttu-id="6b88e-146">AD DS Bereinigung</span><span class="sxs-lookup"><span data-stu-id="6b88e-146">AD DS Cleanup</span></span>

<span data-ttu-id="6b88e-147">Um einen nahtlosen Übergang zu Office 365 mithilfe der Synchronisierung sicherzustellen, müssen Sie Ihre AD DS Gesamtstruktur vorbereiten, bevor Sie mit der Bereitstellung der Office 365-Verzeichnissynchronisierung beginnen.</span><span class="sxs-lookup"><span data-stu-id="6b88e-147">To help ensure a seamless transition to Office 365 by using synchronization, you must prepare your AD DS forest before you begin your Office 365 directory synchronization deployment.</span></span>
  
<span data-ttu-id="6b88e-148">Wenn Sie die [Verzeichnissynchronisierung in Office 365 einrichten](set-up-directory-synchronization.md), besteht einer der Schritte darin, [das Tool IdFix herunterzuladen und auszuführen](install-and-run-idfix.md).</span><span class="sxs-lookup"><span data-stu-id="6b88e-148">When you [set up directory synchronization in Office 365](set-up-directory-synchronization.md), one of the steps is to [download and run the IdFix tool](install-and-run-idfix.md).</span></span> <span data-ttu-id="6b88e-149">Sie können das IdFix-Tool verwenden, um die [Verzeichnisbereinigung](prepare-directory-attributes-for-synch-with-idfix.md)zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="6b88e-149">You can use the IdFix tool to help with [directory cleanup](prepare-directory-attributes-for-synch-with-idfix.md).</span></span>
  
<span data-ttu-id="6b88e-150">Die Verzeichnisbereinigung sollte sich auf die folgenden Aufgaben konzentrieren:</span><span class="sxs-lookup"><span data-stu-id="6b88e-150">Your directory cleanup should focus on the following tasks:</span></span>

- <span data-ttu-id="6b88e-151">Entfernen Sie doppelte **proxyAddress** -und **userPrincipalName** -Attribute.</span><span class="sxs-lookup"><span data-stu-id="6b88e-151">Remove duplicate **proxyAddress** and **userPrincipalName** attributes.</span></span>
- <span data-ttu-id="6b88e-152">Aktualisieren Sie leere und ungültige **userPrincipalName** -Attribute mit gültigen **userPrincipalName** -Attributen.</span><span class="sxs-lookup"><span data-stu-id="6b88e-152">Update blank and invalid **userPrincipalName** attributes with valid **userPrincipalName** attributes.</span></span>
- <span data-ttu-id="6b88e-153">Entfernen Sie ungültige und fragwürdige Zeichen in den Attributen **givenName**, Name ( **SN** ), **sAMAccountName**, **DisplayName**, **Mail**, **proxyAddresses**, **mailNickname**und **userPrincipalName** .</span><span class="sxs-lookup"><span data-stu-id="6b88e-153">Remove invalid and questionable characters in the **givenName**, surname ( **sn** ), **sAMAccountName**, **displayName**, **mail**, **proxyAddresses**, **mailNickname**, and **userPrincipalName** attributes.</span></span> <span data-ttu-id="6b88e-154">Ausführliche Informationen zum Vorbereiten von Attributen finden Sie unter [Liste der Attribute, die mit dem Azure Active Directory Sync-Tool synchronisiert werden](https://go.microsoft.com/fwlink/p/?LinkId=396719).</span><span class="sxs-lookup"><span data-stu-id="6b88e-154">For details about preparing attributes, see [List of attributes that are synced by the Azure Active Directory Sync Tool](https://go.microsoft.com/fwlink/p/?LinkId=396719).</span></span>

    > [!NOTE]
    > <span data-ttu-id="6b88e-155">Dabei handelt es sich um dieselben Attribute, die Azure AD Connect synchronisiert.</span><span class="sxs-lookup"><span data-stu-id="6b88e-155">These are the same attributes that Azure AD Connect synchronizes.</span></span> 
  
## <a name="multi-forest-deployment-considerations"></a><span data-ttu-id="6b88e-156">Überlegungen zur Bereitstellung in mehreren Gesamtstrukturen</span><span class="sxs-lookup"><span data-stu-id="6b88e-156">Multi-forest deployment considerations</span></span>

<span data-ttu-id="6b88e-157">Verwenden Sie für mehrere Gesamtstrukturen und SSO-Optionen die [benutzerdefinierte Installation von Azure AD Connect](https://go.microsoft.com/fwlink/p/?LinkId=698430).</span><span class="sxs-lookup"><span data-stu-id="6b88e-157">For multiple forests and SSO options, use [Custom Installation of Azure AD Connect](https://go.microsoft.com/fwlink/p/?LinkId=698430).</span></span>
  
<span data-ttu-id="6b88e-158">Wenn Ihre Organisation über mehrere Gesamtstrukturen für die Authentifizierung verfügt (Anmelde Gesamtstrukturen), wird dringend Folgendes empfohlen:</span><span class="sxs-lookup"><span data-stu-id="6b88e-158">If your organization has multiple forests for authentication (logon forests), we highly recommend the following:</span></span>
  
- <span data-ttu-id="6b88e-159">**Sie sollten die Gesamtstruktur konsolidieren.**</span><span class="sxs-lookup"><span data-stu-id="6b88e-159">**Consider consolidating your forests.**</span></span> <span data-ttu-id="6b88e-160">Im Allgemeinen ist mehr Aufwand erforderlich, um mehrere Gesamtstrukturen beizubehalten.</span><span class="sxs-lookup"><span data-stu-id="6b88e-160">In general, there's more overhead required to maintain multiple forests.</span></span> <span data-ttu-id="6b88e-161">Wenn Ihre Organisation nicht über Sicherheitseinschränkungen verfügt, die separate Gesamtstrukturen erfordern, sollten Sie die lokale Umgebung vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="6b88e-161">Unless your organization has security constraints that dictate the need for separate forests, consider simplifying your on-premises environment.</span></span>
- <span data-ttu-id="6b88e-162">**Nur in der primären anmeldegesamtstruktur verwenden.**</span><span class="sxs-lookup"><span data-stu-id="6b88e-162">**Use only in your primary logon forest.**</span></span> <span data-ttu-id="6b88e-163">Stellen Sie Office 365 nur in der primären anmeldegesamtstruktur für die anfängliche Einführung von Office 365 bereit.</span><span class="sxs-lookup"><span data-stu-id="6b88e-163">Consider deploying Office 365 only in your primary logon forest for your initial rollout of Office 365.</span></span> 

<span data-ttu-id="6b88e-164">Wenn Sie Ihre AD DS-Bereitstellung mit mehreren Gesamtstrukturen nicht konsolidieren oder andere Verzeichnisdienste zum Verwalten von Identitäten verwenden, können Sie diese möglicherweise mit der Hilfe von Microsoft oder einem Partner synchronisieren.</span><span class="sxs-lookup"><span data-stu-id="6b88e-164">If you can't consolidate your multi-forest AD DS deployment or are using other directory services to manage identities, you may be able to synchronize these with the help of Microsoft or a partner.</span></span>
  
<span data-ttu-id="6b88e-165">Weitere Informationen finden Sie unter [Multi-Forest Directory Sync with Single Sign-on-Szenario](https://go.microsoft.com/fwlink/p/?LinkId=525321) .</span><span class="sxs-lookup"><span data-stu-id="6b88e-165">See [Multi-forest Directory Sync with Single Sign-On Scenario](https://go.microsoft.com/fwlink/p/?LinkId=525321) for more information.</span></span>
  
## <a name="features-that-are-dependent-on-directory-synchronization"></a><span data-ttu-id="6b88e-166">Funktionen, die von der Verzeichnissynchronisierung abhängig sind</span><span class="sxs-lookup"><span data-stu-id="6b88e-166">Features that are dependent on directory synchronization</span></span>
  
<span data-ttu-id="6b88e-167">Die Verzeichnissynchronisierung ist für die folgenden Features und Funktionen erforderlich:</span><span class="sxs-lookup"><span data-stu-id="6b88e-167">Directory synchronization is required for the following features and functionality:</span></span>
  
- <span data-ttu-id="6b88e-168">Azure AD nahtloses einmaliges Anmelden (Single Sign-on, SSO)</span><span class="sxs-lookup"><span data-stu-id="6b88e-168">Azure AD Seamless Single Sign-On (SSO)</span></span>
- <span data-ttu-id="6b88e-169">Skype-Koexistenz</span><span class="sxs-lookup"><span data-stu-id="6b88e-169">Skype coexistence</span></span>
- <span data-ttu-id="6b88e-170">Exchange-hybridbereitstellung, einschließlich:</span><span class="sxs-lookup"><span data-stu-id="6b88e-170">Exchange hybrid deployment, including:</span></span>
  - <span data-ttu-id="6b88e-171">Vollständig freigegebene globale Adressliste (GAL) zwischen Ihrer lokalen Exchange-Umgebung und Office 365.</span><span class="sxs-lookup"><span data-stu-id="6b88e-171">Fully shared global address list (GAL) between your on-premises Exchange environment and Office 365.</span></span>
  - <span data-ttu-id="6b88e-172">Synchronisierung von GAL-Informationen aus unterschiedlichen E-Mail-Systemen.</span><span class="sxs-lookup"><span data-stu-id="6b88e-172">Synchronizing GAL information from different mail systems.</span></span>
  - <span data-ttu-id="6b88e-173">Möglichkeit zum Hinzufügen von Benutzern zu Office 365 Dienst angeboten und zum Entfernen von Benutzern.</span><span class="sxs-lookup"><span data-stu-id="6b88e-173">The ability to add users to and remove users from Office 365 service offerings.</span></span> <span data-ttu-id="6b88e-174">Dies erfordert Folgendes:</span><span class="sxs-lookup"><span data-stu-id="6b88e-174">This requires the following:</span></span>
  - <span data-ttu-id="6b88e-175">Die bidirektionale Synchronisierung muss während der Verzeichnis synchronisierungseinrichtung konfiguriert werden.</span><span class="sxs-lookup"><span data-stu-id="6b88e-175">Two-way synchronization must be configured during directory synchronization setup.</span></span> <span data-ttu-id="6b88e-176">Standardmäßig schreiben Verzeichnissynchronisierungstools Verzeichnisinformationen nur in die Cloud.</span><span class="sxs-lookup"><span data-stu-id="6b88e-176">By default, directory synchronization tools write directory information only to the cloud.</span></span> <span data-ttu-id="6b88e-177">Wenn Sie die bidirektionale Synchronisierung konfigurieren, aktivieren Sie die Write-Back-Funktionalität, sodass eine beschränkte Anzahl von Objektattributen aus der Cloud kopiert und anschließend wieder in Ihre lokale AD DS geschrieben wird.</span><span class="sxs-lookup"><span data-stu-id="6b88e-177">When you configure two-way synchronization, you enable write-back functionality so that a limited number of object attributes are copied from the cloud, and then written them back to your local AD DS.</span></span> <span data-ttu-id="6b88e-178">Write-Back wird auch als Exchange-Hybrid Modus bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="6b88e-178">Write-back is also referred to as Exchange hybrid mode.</span></span> 
  - <span data-ttu-id="6b88e-179">Eine lokale Exchange-hybridbereitstellung</span><span class="sxs-lookup"><span data-stu-id="6b88e-179">An on-premises Exchange hybrid deployment</span></span>
  - <span data-ttu-id="6b88e-180">Die Möglichkeit, einige Benutzerpostfächer in Office 365 zu verschieben und gleichzeitig andere Benutzerpostfächer lokal aufzubewahren.</span><span class="sxs-lookup"><span data-stu-id="6b88e-180">The ability to move some user mailboxes to Office 365 while keeping other user mailboxes on-premises.</span></span>
  - <span data-ttu-id="6b88e-181">Sichere Absender und blockierte Absender lokal werden nach Office 365 repliziert.</span><span class="sxs-lookup"><span data-stu-id="6b88e-181">Safe senders and blocked senders on-premises are replicated to Office 365.</span></span>
  - <span data-ttu-id="6b88e-182">Grundlegende Delegierung und Funktion zum Senden von E-Mails im Auftrag.</span><span class="sxs-lookup"><span data-stu-id="6b88e-182">Basic delegation and send-on-behalf-of email functionality.</span></span>
  - <span data-ttu-id="6b88e-183">Sie verfügen über eine integrierte lokale Smartcard oder mehrstufige Authentifizierungslösung.</span><span class="sxs-lookup"><span data-stu-id="6b88e-183">You have an integrated on-premises smart card or multi-factor authentication solution.</span></span>
- <span data-ttu-id="6b88e-184">Synchronisierung von Fotos, Miniaturansichten, Konferenzräumen und Sicherheitsgruppen</span><span class="sxs-lookup"><span data-stu-id="6b88e-184">Synchronization of photos, thumbnails, conference rooms, and security groups</span></span>

## <a name="next-step"></a><span data-ttu-id="6b88e-185">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="6b88e-185">Next step</span></span>

<span data-ttu-id="6b88e-186">Wenn Sie bereit sind, die Hybrid Identität bereitzustellen, lesen Sie [Vorbereiten der Bereitstellung von Benutzern](prepare-for-directory-synchronization.md).</span><span class="sxs-lookup"><span data-stu-id="6b88e-186">When you are ready to deploy hybrid identity, see [prepare to provision users](prepare-for-directory-synchronization.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="6b88e-187">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="6b88e-187">See also</span></span>

[<span data-ttu-id="6b88e-188">Übersicht zu Microsoft 365 Enterprise</span><span class="sxs-lookup"><span data-stu-id="6b88e-188">Microsoft 365 Enterprise overview</span></span>](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-overview)

