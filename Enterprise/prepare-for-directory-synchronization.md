---
title: Vorbereiten der Verzeichnissynchronisierung auf Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/25/2019
audience: Admin
ms.topic: article
f1_keywords:
- O365p_AddUsersWithDirSync
- O365M_AddUsersWithDirSync
- O365E_HRCSetupAADConnectAboutLM617031
- O365E_AddUsersWithDirSync
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOP150
- MOE150
- MBS150
ms.assetid: 01920974-9e6f-4331-a370-13aea4e82b3e
description: Beschreibt, wie Sie die Bereitstellung von Benutzern für die Office 365 mithilfe der Verzeichnissynchronisierung und die langfristigen Vorteile der Verwendung dieser Methode vorbereiten.
ms.openlocfilehash: ab2908fac1dfb19c72d3321d6d2087bbf24fe6df
ms.sourcegitcommit: a9804062071939b7b7e60da5b69f484ce1d34ff8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/04/2019
ms.locfileid: "39814183"
---
# <a name="prepare-for-directory-synchronization-to-office-365"></a><span data-ttu-id="922e9-103">Vorbereiten der Verzeichnissynchronisierung auf Office 365</span><span class="sxs-lookup"><span data-stu-id="922e9-103">Prepare for directory synchronization to Office 365</span></span>

<span data-ttu-id="922e9-104">*Dieser Artikel gilt sowohl für Office 365 Enterprise als auch Microsoft 365 Enterprise*.</span><span class="sxs-lookup"><span data-stu-id="922e9-104">*This article applies to both Office 365 Enterprise and Microsoft 365 Enterprise.*</span></span>

<span data-ttu-id="922e9-105">Zu den Vorteilen der Hybriden Identitäts-und Verzeichnissynchronisierung in Ihrer Organisation gehören:</span><span class="sxs-lookup"><span data-stu-id="922e9-105">The benefits to hybrid identity and directory synchronization your organization include:</span></span>
  
- <span data-ttu-id="922e9-106">Reduzieren der Verwaltungsprogramme in Ihrer Organisation</span><span class="sxs-lookup"><span data-stu-id="922e9-106">Reducing the administrative programs in your organization</span></span>
- <span data-ttu-id="922e9-107">Optionales Aktivieren des Szenarios für einmaliges Anmelden</span><span class="sxs-lookup"><span data-stu-id="922e9-107">Optionally enabling single sign-on scenario</span></span>
- <span data-ttu-id="922e9-108">Automatisieren von Kontoänderungen in Office 365</span><span class="sxs-lookup"><span data-stu-id="922e9-108">Automating account changes in Office 365</span></span>
    
<span data-ttu-id="922e9-109">Weitere Informationen zu den Vorteilen der Verwendung der Verzeichnissynchronisierung finden Sie unter [Directory Synchronization Roadmap]( https://go.microsoft.com/fwlink/p/?LinkId=525398) and [Hybrid Identity for Office 365](plan-for-directory-synchronization.md).</span><span class="sxs-lookup"><span data-stu-id="922e9-109">For more information about the advantages of using directory synchronization, see [Directory synchronization roadmap]( https://go.microsoft.com/fwlink/p/?LinkId=525398) and [Hybrid identity for Office 365](plan-for-directory-synchronization.md).</span></span>

<span data-ttu-id="922e9-110">Die Verzeichnissynchronisierung erfordert jedoch die Planung und Vorbereitung, um sicherzustellen, dass Ihre Active Directory-Domänendienste (AD DS) mit dem Azure Active Directory (Azure AD)-Mandanten Ihres Office 365 Abonnements mit einem Minimum an Fehlern synchronisiert wird.</span><span class="sxs-lookup"><span data-stu-id="922e9-110">However, directory synchronization requires planning and preparation to ensure that your Active Directory Domain Services (AD DS) synchronizes to the Azure Active Directory (Azure AD) tenant of your Office 365 subscription with a minimum of errors.</span></span> 

<span data-ttu-id="922e9-111">Führen Sie die folgenden Schritte aus, um die besten Ergebnisse zu erzielen.</span><span class="sxs-lookup"><span data-stu-id="922e9-111">Follow these steps in order for the best results.</span></span>
  
## <a name="1-directory-cleanup-tasks"></a><span data-ttu-id="922e9-112">1. Aufgaben zur Verzeichnisbereinigung</span><span class="sxs-lookup"><span data-stu-id="922e9-112">1. Directory cleanup tasks</span></span>

<span data-ttu-id="922e9-113">Bevor Sie Ihre AD DS mit Ihrem Azure AD-Mandanten synchronisieren, müssen Sie Ihre AD DS bereinigen.</span><span class="sxs-lookup"><span data-stu-id="922e9-113">Before you synchronize your AD DS to your Azure AD tenant, you need to clean up your AD DS.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="922e9-114">Wenn Sie AD DS Bereinigung vor der Synchronisierung nicht durchführen, kann sich dies erheblich negativ auf den Bereitstellungsprozess auswirken.</span><span class="sxs-lookup"><span data-stu-id="922e9-114">If you don't perform AD DS cleanup before you synchronize, there can be a significant negative effect on the deployment process.</span></span> <span data-ttu-id="922e9-115">Es kann Tage oder sogar Wochen dauern, bis der Zyklus der Verzeichnissynchronisierung durchläuft, Fehler identifiziert und erneut synchronisiert wird.</span><span class="sxs-lookup"><span data-stu-id="922e9-115">It might take days, or even weeks, to go through the cycle of directory synchronization, identifying errors, and re-synchronization.</span></span> 
  
<span data-ttu-id="922e9-116">Führen Sie in Ihrem AD DS die folgenden Bereinigungsaufgaben für jedes Benutzerkonto aus, dem eine Office 365 Lizenz zugewiesen wird:</span><span class="sxs-lookup"><span data-stu-id="922e9-116">In your AD DS, complete the following clean-up tasks for each user account that will be assigned an Office 365 license:</span></span>
  
1. <span data-ttu-id="922e9-117">Stellen Sie eine gültige und eindeutige e-Mail-Adresse im **proxyAddresses** -Attribut sicher.</span><span class="sxs-lookup"><span data-stu-id="922e9-117">Ensure a valid and unique email address in the **proxyAddresses** attribute.</span></span> 

  >[!Note]
  ><span data-ttu-id="922e9-118">Eine Tilde (~) in e-Mail-Adressen wird ignoriert.</span><span class="sxs-lookup"><span data-stu-id="922e9-118">A tilde (~) character in email addresses will be ignored.</span></span> <span data-ttu-id="922e9-119">Dies kann zu falsch positiven Verzeichnis Synchronisierungsfehlern bei doppelten proxyAddresses führen.</span><span class="sxs-lookup"><span data-stu-id="922e9-119">This can lead to false-positive directory synchronization errors about duplicate proxyAddresses.</span></span>
    
2. <span data-ttu-id="922e9-120">Entfernen Sie alle doppelten Werte im **proxyAddresses** -Attribut.</span><span class="sxs-lookup"><span data-stu-id="922e9-120">Remove any duplicate values in the **proxyAddresses** attribute.</span></span> 
    
3.  <span data-ttu-id="922e9-121">Stellen Sie nach Möglichkeit einen gültigen und eindeutigen Wert für das **userPrincipalName** -Attribut im **Benutzer** Objekt des Benutzers sicher.</span><span class="sxs-lookup"><span data-stu-id="922e9-121">If possible, ensure a valid and unique value for the **userPrincipalName** attribute in the user's **user** object.</span></span> <span data-ttu-id="922e9-122">Stellen Sie sicher, dass der AD DS UPN mit dem Azure AD UPN übereinstimmt, um eine optimale Synchronisierung zu erzielen.</span><span class="sxs-lookup"><span data-stu-id="922e9-122">For the best synchronization experience, ensure that the AD DS UPN matches the Azure AD UPN.</span></span> <span data-ttu-id="922e9-123">Wenn ein Benutzer keinen Wert für das **userPrincipalName** -Attribut aufweist, muss das **User** -Objekt einen gültigen und eindeutigen Wert für das **sAMAccountName** -Attribut enthalten.</span><span class="sxs-lookup"><span data-stu-id="922e9-123">If a user does not have a value for the **userPrincipalName** attribute, then the **user** object must contain a valid and unique value for the **sAMAccountName** attribute.</span></span> <span data-ttu-id="922e9-124">Entfernen Sie alle doppelten Werte im **userPrincipalName** -Attribut.</span><span class="sxs-lookup"><span data-stu-id="922e9-124">Remove any duplicate values in the **userPrincipalName** attribute.</span></span> 
    
4. <span data-ttu-id="922e9-125">Stellen Sie für eine optimale Verwendung der globalen Adressliste (GAL) sicher, dass die Informationen in den folgenden Attributen des AD DS Benutzerkontos richtig sind:</span><span class="sxs-lookup"><span data-stu-id="922e9-125">For optimal use of the global address list (GAL), ensure the information in the following attributes of the AD DS user account is correct:</span></span>
    
  - <span data-ttu-id="922e9-126">givenName</span><span class="sxs-lookup"><span data-stu-id="922e9-126">givenName</span></span>
  - <span data-ttu-id="922e9-127">surname</span><span class="sxs-lookup"><span data-stu-id="922e9-127">surname</span></span>
  - <span data-ttu-id="922e9-128">displayName</span><span class="sxs-lookup"><span data-stu-id="922e9-128">displayName</span></span>
  - <span data-ttu-id="922e9-129">Position</span><span class="sxs-lookup"><span data-stu-id="922e9-129">Job Title</span></span>
  - <span data-ttu-id="922e9-130">Abteilung</span><span class="sxs-lookup"><span data-stu-id="922e9-130">Department</span></span>
  - <span data-ttu-id="922e9-131">Büro</span><span class="sxs-lookup"><span data-stu-id="922e9-131">Office</span></span>
  - <span data-ttu-id="922e9-132">Telefon (geschäftlich)</span><span class="sxs-lookup"><span data-stu-id="922e9-132">Office Phone</span></span>
  - <span data-ttu-id="922e9-133">Mobiltelefon</span><span class="sxs-lookup"><span data-stu-id="922e9-133">Mobile Phone</span></span>
  - <span data-ttu-id="922e9-134">Faxnummer</span><span class="sxs-lookup"><span data-stu-id="922e9-134">Fax Number</span></span>
  - <span data-ttu-id="922e9-135">Straße</span><span class="sxs-lookup"><span data-stu-id="922e9-135">Street Address</span></span>
  - <span data-ttu-id="922e9-136">Stadt</span><span class="sxs-lookup"><span data-stu-id="922e9-136">City</span></span>
  - <span data-ttu-id="922e9-137">Bundesland/Kanton</span><span class="sxs-lookup"><span data-stu-id="922e9-137">State or Province</span></span>
  - <span data-ttu-id="922e9-138">PLZ</span><span class="sxs-lookup"><span data-stu-id="922e9-138">Zip or Postal Code</span></span>
  - <span data-ttu-id="922e9-139">Land oder Region</span><span class="sxs-lookup"><span data-stu-id="922e9-139">Country or Region</span></span>
    
## <a name="2-directory-object-and-attribute-preparation"></a><span data-ttu-id="922e9-140">2. Verzeichnisobjekt-und Attribut Vorbereitung</span><span class="sxs-lookup"><span data-stu-id="922e9-140">2. Directory object and attribute preparation</span></span>

<span data-ttu-id="922e9-141">Für eine erfolgreiche Verzeichnissynchronisierung zwischen Ihrem AD DS und Office 365 müssen die AD DS Attribute ordnungsgemäß vorbereitet werden.</span><span class="sxs-lookup"><span data-stu-id="922e9-141">Successful directory synchronization between your AD DS and Office 365 requires that your AD DS attributes are properly prepared.</span></span> <span data-ttu-id="922e9-142">Beispielsweise müssen Sie sicherstellen, dass bestimmte Zeichen nicht in bestimmten Attributen verwendet werden, die mit der Office 365 Umgebung synchronisiert werden.</span><span class="sxs-lookup"><span data-stu-id="922e9-142">For example, you need to ensure that specific characters aren't used in certain attributes that are synchronized with the Office 365 environment.</span></span> <span data-ttu-id="922e9-143">Unerwartete Zeichen führen nicht dazu, dass die Verzeichnissynchronisierung fehlschlägt, aber möglicherweise wird eine Warnung zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="922e9-143">Unexpected characters do not cause directory synchronization to fail but might return a warning.</span></span> <span data-ttu-id="922e9-144">Ungültige Zeichen führen dazu, dass die Verzeichnissynchronisierung fehlschlägt.</span><span class="sxs-lookup"><span data-stu-id="922e9-144">Invalid characters will cause directory synchronization to fail.</span></span>
  
<span data-ttu-id="922e9-145">Die Verzeichnissynchronisierung schlägt auch fehl, wenn einige Ihrer AD DS Benutzer über ein oder mehrere doppelte Attribute verfügen.</span><span class="sxs-lookup"><span data-stu-id="922e9-145">Directory synchronization will also fail if some of your AD DS users have one or more duplicate attributes.</span></span> <span data-ttu-id="922e9-146">Jeder Benutzer muss über eindeutige Attribute verfügen.</span><span class="sxs-lookup"><span data-stu-id="922e9-146">Each user must have unique attributes.</span></span>
  
<span data-ttu-id="922e9-147">Die Attribute, die Sie vorbereiten müssen, sind hier aufgelistet:</span><span class="sxs-lookup"><span data-stu-id="922e9-147">The attributes that you need to prepare are listed here:</span></span>
  
- <span data-ttu-id="922e9-148">**displayName**</span><span class="sxs-lookup"><span data-stu-id="922e9-148">**displayName**</span></span>
    
  - <span data-ttu-id="922e9-149">Wenn das Attribut im User-Objekt vorhanden ist, wird es mit Office 365 synchronisiert.</span><span class="sxs-lookup"><span data-stu-id="922e9-149">If the attribute exists in the user object, it will be synchronized with Office 365.</span></span>
  - <span data-ttu-id="922e9-150">Wenn dieses Attribut im User-Objekt vorhanden ist, muss es einen Wert dafür geben.</span><span class="sxs-lookup"><span data-stu-id="922e9-150">If this attribute exists in the user object, there must be a value for it.</span></span> <span data-ttu-id="922e9-151">Das heißt, das Attribut darf nicht leer sein.</span><span class="sxs-lookup"><span data-stu-id="922e9-151">That is, the attribute must not be blank.</span></span>
  - <span data-ttu-id="922e9-152">Maximale Anzahl der Zeichen: 256</span><span class="sxs-lookup"><span data-stu-id="922e9-152">Maximum number of characters: 256</span></span>
    
- <span data-ttu-id="922e9-153">**givenName**</span><span class="sxs-lookup"><span data-stu-id="922e9-153">**givenName**</span></span>
    
  - <span data-ttu-id="922e9-154">Wenn das Attribut im User-Objekt vorhanden ist, wird es mit Office 365 synchronisiert, aber Office 365 erfordert oder verwendet es nicht.</span><span class="sxs-lookup"><span data-stu-id="922e9-154">If the attribute exists in the user object, it will be synchronized with Office 365, but Office 365 does not require or use it.</span></span>
  - <span data-ttu-id="922e9-155">Maximale Anzahl der Zeichen: 64</span><span class="sxs-lookup"><span data-stu-id="922e9-155">Maximum number of characters: 64</span></span>
    
- <span data-ttu-id="922e9-156">**mail**</span><span class="sxs-lookup"><span data-stu-id="922e9-156">**mail**</span></span>
    
  - <span data-ttu-id="922e9-157">Der Attributwert muss innerhalb des Verzeichnisses eindeutig sein.</span><span class="sxs-lookup"><span data-stu-id="922e9-157">The attribute value must be unique within the directory.</span></span>
    
    > [!NOTE]
    > <span data-ttu-id="922e9-158">Wenn es doppelte Werte gibt, wird der erste Benutzer mit dem Wert synchronisiert.</span><span class="sxs-lookup"><span data-stu-id="922e9-158">If there are duplicate values, the first user with the value is synchronized.</span></span> <span data-ttu-id="922e9-159">Nachfolgende Benutzer werden nicht in Office 365 angezeigt.</span><span class="sxs-lookup"><span data-stu-id="922e9-159">Subsequent users will not appear in Office 365.</span></span> <span data-ttu-id="922e9-160">Sie müssen entweder den Wert in Office 365 ändern oder beide Werte in AD DS ändern, damit beide Benutzer in Office 365 angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="922e9-160">You must modify either the value in Office 365 or modify both of the values in AD DS in order for both users to appear in Office 365.</span></span> 
  
- <span data-ttu-id="922e9-161">**mailnick Name** (Exchange-Alias)</span><span class="sxs-lookup"><span data-stu-id="922e9-161">**mailNickname** (Exchange alias)</span></span> 
    
  - <span data-ttu-id="922e9-162">Der Attributwert darf nicht mit einem Punkt (.) beginnen.</span><span class="sxs-lookup"><span data-stu-id="922e9-162">The attribute value cannot begin with a period (.).</span></span>
  - <span data-ttu-id="922e9-163">Der Attributwert muss innerhalb des Verzeichnisses eindeutig sein.</span><span class="sxs-lookup"><span data-stu-id="922e9-163">The attribute value must be unique within the directory.</span></span>
  
    > [!NOTE]
    > <span data-ttu-id="922e9-164">Unterstriche ("_") im synchronisierten Namen gibt an, dass der ursprüngliche Wert dieses Attributs ungültige Zeichen enthält.</span><span class="sxs-lookup"><span data-stu-id="922e9-164">Underscores ("_") in the synchronized name indicates that the original value of this attribute contains invalid characters.</span></span> <span data-ttu-id="922e9-165">Der ursprüngliche Wert kann Buchstaben, Zahlen und die Zeichen!, #, $,%, #a0, ', \*, +,-,/, =,?, ^, _, ', {, |,} und ~ enthalten.</span><span class="sxs-lookup"><span data-stu-id="922e9-165">The original value can contain letters, numbers, and the characters !, #, $, %, &, ', \*, +, -, /, =, ?, ^, _, \`, {, |, } and ~.</span></span> <span data-ttu-id="922e9-166">Weitere Informationen zu diesem Attribut finden Sie unter [Exchange-Alias Attribut](https://docs.microsoft.com/powershell/module/exchange/mailboxes/set-mailbox?view=exchange-ps).</span><span class="sxs-lookup"><span data-stu-id="922e9-166">For more information on this attribute, see [Exchange alias attribute](https://docs.microsoft.com/powershell/module/exchange/mailboxes/set-mailbox?view=exchange-ps).</span></span>
    >
      
- <span data-ttu-id="922e9-167">**proxyAddresses**</span><span class="sxs-lookup"><span data-stu-id="922e9-167">**proxyAddresses**</span></span>
    
  - <span data-ttu-id="922e9-168">Mehrwertiges Attribut</span><span class="sxs-lookup"><span data-stu-id="922e9-168">Multiple-value attribute</span></span>
  - <span data-ttu-id="922e9-169">Maximale Anzahl von Zeichen pro Wert: 256</span><span class="sxs-lookup"><span data-stu-id="922e9-169">Maximum number of characters per value: 256</span></span>
  - <span data-ttu-id="922e9-170">Der Attributwert darf kein Leerzeichen enthalten.</span><span class="sxs-lookup"><span data-stu-id="922e9-170">The attribute value must not contain a space.</span></span>
  - <span data-ttu-id="922e9-171">Der Attributwert muss innerhalb des Verzeichnisses eindeutig sein.</span><span class="sxs-lookup"><span data-stu-id="922e9-171">The attribute value must be unique within the directory.</span></span>
  - <span data-ttu-id="922e9-172">Ungültige Zeichen: \< \> (); , [ ] " '</span><span class="sxs-lookup"><span data-stu-id="922e9-172">Invalid characters: \< \> ( ) ; , [ ] " '</span></span>
    
    <span data-ttu-id="922e9-173">Beachten Sie, dass die ungültigen Zeichen auf die Zeichen nach dem typtrennzeichen und ":" angewendet werden, so dass SMTP:User@contso.com zulässig ist, aber SMTP:User:M@contoso.com nicht ist.</span><span class="sxs-lookup"><span data-stu-id="922e9-173">Note that the invalid characters apply to the characters following the type delimiter and ":", such that SMTP:User@contso.com is allowed, but SMTP:user:M@contoso.com is not.</span></span>
    
    > [!IMPORTANT]
    > <span data-ttu-id="922e9-174">Alle SMTP-Adressen (Simple Mail Transport Protocol) sollten den e-Mail-Messagingstandards entsprechen.</span><span class="sxs-lookup"><span data-stu-id="922e9-174">All Simple Mail Transport Protocol (SMTP) addresses should comply with email messaging standards.</span></span> <span data-ttu-id="922e9-175">Wenn doppelte oder unerwünschte Adressen vorhanden sind, finden Sie im Hilfethema [Entfernen von doppelten und unerwünschten Proxyadressen in Exchange](https://go.microsoft.com/fwlink/?LinkId=293860).</span><span class="sxs-lookup"><span data-stu-id="922e9-175">If duplicate or unwanted addresses exist, see the Help topic [Removing duplicate and unwanted proxy addresses in Exchange](https://go.microsoft.com/fwlink/?LinkId=293860).</span></span> 
  
- <span data-ttu-id="922e9-176">**sAMAccountName**</span><span class="sxs-lookup"><span data-stu-id="922e9-176">**sAMAccountName**</span></span>
    
  - <span data-ttu-id="922e9-177">Maximale Anzahl der Zeichen: 20</span><span class="sxs-lookup"><span data-stu-id="922e9-177">Maximum number of characters: 20</span></span>
  - <span data-ttu-id="922e9-178">Der Attributwert muss innerhalb des Verzeichnisses eindeutig sein.</span><span class="sxs-lookup"><span data-stu-id="922e9-178">The attribute value must be unique within the directory.</span></span>
  - <span data-ttu-id="922e9-179">Ungültige Zeichen: [\ "|,/: \< \> + =;?</span><span class="sxs-lookup"><span data-stu-id="922e9-179">Invalid characters: [ \ " | , / : \< \> + = ; ?</span></span> <span data-ttu-id="922e9-180">\* ']</span><span class="sxs-lookup"><span data-stu-id="922e9-180"></span></span>
  - <span data-ttu-id="922e9-181">Wenn ein Benutzer ein ungültiges **sAMAccountName** -Attribut aufweist, aber über ein gültiges **userPrincipalName** -Attribut verfügt, wird das Benutzerkonto in Office 365 erstellt.</span><span class="sxs-lookup"><span data-stu-id="922e9-181">If a user has an invalid **sAMAccountName** attribute but has a valid **userPrincipalName** attribute, the user account is created in Office 365.</span></span> 
  - <span data-ttu-id="922e9-182">Wenn sowohl **sAMAccountName** als auch **userPrincipalName** ungültig sind, muss das AD DS **userPrincipalName** -Attribut aktualisiert werden.</span><span class="sxs-lookup"><span data-stu-id="922e9-182">If both **sAMAccountName** and **userPrincipalName** are invalid, the AD DS **userPrincipalName** attribute must be updated.</span></span> 
    
- <span data-ttu-id="922e9-183">**SN** (Nachname)</span><span class="sxs-lookup"><span data-stu-id="922e9-183">**sn** (surname)</span></span> 
    
  - <span data-ttu-id="922e9-184">Wenn das Attribut im User-Objekt vorhanden ist, wird es mit Office 365 synchronisiert, aber Office 365 erfordert oder verwendet es nicht.</span><span class="sxs-lookup"><span data-stu-id="922e9-184">If the attribute exists in the user object, it will be synchronized with Office 365, but Office 365 does not require or use it.</span></span>
    
- <span data-ttu-id="922e9-185">**targetAddress**</span><span class="sxs-lookup"><span data-stu-id="922e9-185">**targetAddress**</span></span>
    
    <span data-ttu-id="922e9-186">Es ist erforderlich, dass das **targetAddress** -Attribut (beispielsweise SMTP:Tom@contoso.com), das für den Benutzer aufgefüllt wird, in der Office 365 GAL angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="922e9-186">It's required that the **targetAddress** attribute (for example, SMTP:tom@contoso.com) that's populated for the user must appear in the Office 365 GAL.</span></span> <span data-ttu-id="922e9-187">Bei Messaging Migrationsszenarien von Drittanbietern wäre dies die Office 365 Schemaerweiterung für die AD DS erforderlich.</span><span class="sxs-lookup"><span data-stu-id="922e9-187">In third-party messaging migration scenarios, this would require the Office 365 schema extension for the AD DS.</span></span> <span data-ttu-id="922e9-188">Die Office 365 Schemaerweiterung würde auch weitere nützliche Attribute zum Verwalten von Office 365-Objekten hinzufügen, die mit einem Verzeichnissynchronisierungstool aus AD DS aufgefüllt werden.</span><span class="sxs-lookup"><span data-stu-id="922e9-188">The Office 365 schema extension would also add other useful attributes to manage Office 365 objects that are populated by using a directory synchronization tool from AD DS.</span></span> <span data-ttu-id="922e9-189">Beispielsweise würde das **msExchHideFromAddressLists** -Attribut zum Verwalten von ausgeblendeten Postfächern oder Verteilergruppen hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="922e9-189">For example, the **msExchHideFromAddressLists** attribute to manage hidden mailboxes or distribution groups would be added.</span></span> 
   
  - <span data-ttu-id="922e9-190">Maximale Anzahl der Zeichen: 256</span><span class="sxs-lookup"><span data-stu-id="922e9-190">Maximum number of characters: 256</span></span>
  - <span data-ttu-id="922e9-191">Der Attributwert darf kein Leerzeichen enthalten.</span><span class="sxs-lookup"><span data-stu-id="922e9-191">The attribute value must not contain a space.</span></span>
  - <span data-ttu-id="922e9-192">Der Attributwert muss innerhalb des Verzeichnisses eindeutig sein.</span><span class="sxs-lookup"><span data-stu-id="922e9-192">The attribute value must be unique within the directory.</span></span>
  - <span data-ttu-id="922e9-193">Ungültige Zeichen: \ \< \> (); , [ ] "</span><span class="sxs-lookup"><span data-stu-id="922e9-193">Invalid characters: \ \< \> ( ) ; , [ ] "</span></span>
  - <span data-ttu-id="922e9-194">Alle SMTP-Adressen (Simple Mail Transport Protocol) sollten den e-Mail-Messagingstandards entsprechen.</span><span class="sxs-lookup"><span data-stu-id="922e9-194">All Simple Mail Transport Protocol (SMTP) addresses should comply with email messaging standards.</span></span>
    
- <span data-ttu-id="922e9-195">**userPrincipalName**</span><span class="sxs-lookup"><span data-stu-id="922e9-195">**userPrincipalName**</span></span>
    
  - <span data-ttu-id="922e9-196">Das **userPrincipalName** -Attribut muss das Anmeldeformat im Internet Format aufweisen, dem der Benutzername gefolgt von dem @-Zeichen (@) und einem Domänennamen folgt: beispielsweise user@contoso.com.</span><span class="sxs-lookup"><span data-stu-id="922e9-196">The **userPrincipalName** attribute must be in the Internet-style sign-in format where the user name is followed by the at sign (@) and a domain name: for example, user@contoso.com.</span></span> <span data-ttu-id="922e9-197">Alle SMTP-Adressen (Simple Mail Transport Protocol) sollten den e-Mail-Messagingstandards entsprechen.</span><span class="sxs-lookup"><span data-stu-id="922e9-197">All Simple Mail Transport Protocol (SMTP) addresses should comply with email messaging standards.</span></span>
  - <span data-ttu-id="922e9-198">Die maximale Anzahl von Zeichen für das **userPrincipalName** -Attribut lautet 113.</span><span class="sxs-lookup"><span data-stu-id="922e9-198">The maximum number of characters for the **userPrincipalName** attribute is 113.</span></span> <span data-ttu-id="922e9-199">Eine bestimmte Anzahl von Zeichen ist vor und nach dem @-Zeichen wie folgt zulässig:</span><span class="sxs-lookup"><span data-stu-id="922e9-199">A specific number of characters are permitted before and after the at sign (@), as follows:</span></span> 
  - <span data-ttu-id="922e9-200">Maximale Anzahl von Zeichen für den Benutzernamen vor dem @-Zeichen (@): 64</span><span class="sxs-lookup"><span data-stu-id="922e9-200">Maximum number of characters for the username that is in front of the at sign (@): 64</span></span>
  - <span data-ttu-id="922e9-201">Maximale Anzahl von Zeichen für den Domänennamen nach dem @-Zeichen (@): 48</span><span class="sxs-lookup"><span data-stu-id="922e9-201">Maximum number of characters for the domain name following the at sign (@): 48</span></span>
  - <span data-ttu-id="922e9-202">Ungültige Zeichen: \% &amp; \* +/=?</span><span class="sxs-lookup"><span data-stu-id="922e9-202">Invalid characters: \ % &amp; \* + / = ?</span></span> <span data-ttu-id="922e9-203">{ } | \< \> ( ) ; : , [ ] " '</span><span class="sxs-lookup"><span data-stu-id="922e9-203"></span></span>
  - <span data-ttu-id="922e9-204">Ein Umlaut ist ebenfalls ein ungültiges Zeichen.</span><span class="sxs-lookup"><span data-stu-id="922e9-204">An umlaut is also an invalid character.</span></span>
  - <span data-ttu-id="922e9-205">Das @-Zeichen ist in jedem **userPrincipalName** -Wert erforderlich.</span><span class="sxs-lookup"><span data-stu-id="922e9-205">The @ character is required in each **userPrincipalName** value.</span></span> 
  - <span data-ttu-id="922e9-206">Das @-Zeichen darf nie das erste Zeichen in einem **userPrincipalName**-Wert sein.</span><span class="sxs-lookup"><span data-stu-id="922e9-206">The @ character cannot be the first character in each **userPrincipalName** value.</span></span> 
  - <span data-ttu-id="922e9-207">Der Benutzername darf nicht mit einem Punkt (.), einem kaufmännischen und-Zeichen (&amp;), einem Leerzeichen oder einem @-Zeichen enden.</span><span class="sxs-lookup"><span data-stu-id="922e9-207">The username cannot end with a period (.), an ampersand (&amp;), a space, or an at sign (@).</span></span>
  - <span data-ttu-id="922e9-208">Der Benutzername darf keine Leerzeichen enthalten.</span><span class="sxs-lookup"><span data-stu-id="922e9-208">The username cannot contain any spaces.</span></span>
  - <span data-ttu-id="922e9-209">Routingfähige Domänen müssen verwendet werden; Beispielsweise können keine lokalen oder internen Domänen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="922e9-209">Routable domains must be used; for example, local or internal domains cannot be used.</span></span>
  - <span data-ttu-id="922e9-210">Unicode-Zeichen werden in Unterstriche umgewandelt.</span><span class="sxs-lookup"><span data-stu-id="922e9-210">Unicode is converted to underscore characters.</span></span>
  - <span data-ttu-id="922e9-211">**userPrincipalName** darf keine doppelten Werte im Verzeichnis enthalten.</span><span class="sxs-lookup"><span data-stu-id="922e9-211">**userPrincipalName** cannot contain any duplicate values in the directory.</span></span> 

<span data-ttu-id="922e9-212">Informationen zum Identifizieren von Fehlern in den Attributen ihrer AD DS finden Sie unter [Prepare Directory Attributes with the IdFix Tool](prepare-directory-attributes-for-synch-with-idfix.md) to use the IdFix Tool.</span><span class="sxs-lookup"><span data-stu-id="922e9-212">See [Prepare directory attributes with the IdFix tool](prepare-directory-attributes-for-synch-with-idfix.md) to use the IdFIx tool to identify errors in the attributes of your AD DS.</span></span>
    
## <a name="3-prepare-the-userprincipalname-attribute"></a><span data-ttu-id="922e9-213">3. Vorbereiten des userPrincipalName-Attributs</span><span class="sxs-lookup"><span data-stu-id="922e9-213">3. Prepare the userPrincipalName attribute</span></span>

<span data-ttu-id="922e9-214">Active Directory wurde entwickelt, um es den Endbenutzern in Ihrer Organisation zu ermöglichen, sich mit **sAMAccountName** oder **userPrincipalName**bei Ihrem Verzeichnis anzumelden.</span><span class="sxs-lookup"><span data-stu-id="922e9-214">Active Directory is designed to allow the end users in your organization to sign in to your directory by using either **sAMAccountName** or **userPrincipalName**.</span></span> <span data-ttu-id="922e9-215">Auf ähnliche Weise können sich Endbenutzer bei Office 365 anmelden, indem Sie den Benutzerprinzipalnamen (User Principal Name, UPN) Ihres Geschäfts-oder Schul Kontos verwenden.</span><span class="sxs-lookup"><span data-stu-id="922e9-215">Similarly, end users can sign in to Office 365 by using the user principal name (UPN) of their work or school account.</span></span> <span data-ttu-id="922e9-216">Die Verzeichnissynchronisierung versucht, neue Benutzer in Azure Active Directory mithilfe desselben UPN zu erstellen, der in Ihrem AD DS ist.</span><span class="sxs-lookup"><span data-stu-id="922e9-216">Directory synchronization attempts to create new users in Azure Active Directory by using the same UPN that's in your AD DS.</span></span> <span data-ttu-id="922e9-217">Der UPN ist wie eine e-Mail-Adresse formatiert.</span><span class="sxs-lookup"><span data-stu-id="922e9-217">The UPN is formatted like an email address.</span></span> 

<span data-ttu-id="922e9-218">In Office 365 ist der UPN das Standardattribut, das zum Generieren der e-Mail-Adresse verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="922e9-218">In Office 365, the UPN is the default attribute that's used to generate the email address.</span></span> <span data-ttu-id="922e9-219">Es ist ganz einfach, **userPrincipalName** (in AD DS und in Azure AD) und die primäre e-Mail-Adresse in **proxyAddresses** auf unterschiedliche Werte festgelegt zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="922e9-219">It's easy to get **userPrincipalName** (in AD DS and in Azure AD) and the primary email address in **proxyAddresses** set to different values.</span></span> <span data-ttu-id="922e9-220">Wenn Sie auf unterschiedliche Werte festgelegt sind, kann es zu Verwirrung für Administratoren und Endbenutzer kommen.</span><span class="sxs-lookup"><span data-stu-id="922e9-220">When they are set to different values, there can be confusion for administrators and end users.</span></span> 
  
<span data-ttu-id="922e9-221">Es empfiehlt sich, diese Attribute auszurichten, um Verwirrung zu verringern.</span><span class="sxs-lookup"><span data-stu-id="922e9-221">It's best to align these attributes to reduce confusion.</span></span> <span data-ttu-id="922e9-222">Um die Anforderungen des einmaligen Anmeldens mit Active Directory-Verbunddienste (AD FS) 2.0 zu erfüllen, müssen Sie sicherstellen, dass die UPNs in Azure Active Directory und Ihre AD DS übereinstimmen und einen gültigen Domänennamespace verwenden.</span><span class="sxs-lookup"><span data-stu-id="922e9-222">To meet the requirements of single sign-on with Active Directory Federation Services (AD FS) 2.0, you need to ensure that the UPNs in Azure Active Directory and your AD DS match and are using a valid domain namespace.</span></span>
  
## <a name="4-add-an-alternative-upn-suffix-to-ad-ds"></a><span data-ttu-id="922e9-223">4. Hinzufügen eines alternativen UPN-Suffix zu AD DS</span><span class="sxs-lookup"><span data-stu-id="922e9-223">4. Add an alternative UPN suffix to AD DS</span></span>

<span data-ttu-id="922e9-224">Möglicherweise müssen Sie ein alternatives UPN-Suffix hinzufügen, um die Unternehmensanmeldeinformationen des Benutzers der Office 365 Umgebung zuzuordnen.</span><span class="sxs-lookup"><span data-stu-id="922e9-224">You may need to add an alternative UPN suffix to associate the user's corporate credentials with the Office 365 environment.</span></span> <span data-ttu-id="922e9-225">Ein UPN-Suffix ist der Teil eines Benutzerprinzipalnamens, der rechts vom Zeichen @ steht.</span><span class="sxs-lookup"><span data-stu-id="922e9-225">A UPN suffix is the part of a UPN to the right of the @ character.</span></span> <span data-ttu-id="922e9-226">UPNs, die für einmaliges Anmelden verwendet werden, können Buchstaben, Zahlen, Punkte, Bindestriche und Unterstriche enthalten, aber keine anderen Zeichen.</span><span class="sxs-lookup"><span data-stu-id="922e9-226">UPNs that are used for single sign-on can contain letters, numbers, periods, dashes, and underscores, but no other types of characters.</span></span>
  
<span data-ttu-id="922e9-227">Weitere Informationen zum Hinzufügen eines alternativen UPN-Suffix zu Active Directory finden Sie unter [Prepare for Directory Synchronization]( https://go.microsoft.com/fwlink/p/?LinkId=525430).</span><span class="sxs-lookup"><span data-stu-id="922e9-227">For more information on how to add an alternative UPN suffix to Active Directory, see [Prepare for directory synchronization]( https://go.microsoft.com/fwlink/p/?LinkId=525430).</span></span>
  
## <a name="5-match-the-ad-ds-upn-with-the-office-365-upn"></a><span data-ttu-id="922e9-228">5. Übereinstimmung mit dem AD DS UPN mit dem Office 365 UPN</span><span class="sxs-lookup"><span data-stu-id="922e9-228">5. Match the AD DS UPN with the Office 365 UPN</span></span>

<span data-ttu-id="922e9-229">Wenn Sie die Verzeichnissynchronisierung bereits eingerichtet haben, stimmt der UPN des Benutzers für Office 365 möglicherweise nicht mit dem AD DS UPN des Benutzers überein, der in Ihrem AD DS definiert ist.</span><span class="sxs-lookup"><span data-stu-id="922e9-229">If you've already set up directory synchronization, the user's UPN for Office 365 may not match the user's AD DS UPN that's defined in your AD DS.</span></span> <span data-ttu-id="922e9-230">Das kann vorkommen, wenn einem Benutzer vor der Überprüfung der Domäne schon eine Lizenz zugewiesen wurde.</span><span class="sxs-lookup"><span data-stu-id="922e9-230">This can occur when a user was assigned a license before the domain was verified.</span></span> <span data-ttu-id="922e9-231">Um dies zu beheben, verwenden Sie [PowerShell, um doppelten UPN zu beheben](https://go.microsoft.com/fwlink/p/?LinkId=396730) , um den UPN des Benutzers zu aktualisieren, um sicherzustellen, dass der Office 365 UPN mit dem Benutzernamen und der Domäne des Unternehmens übereinstimmt.</span><span class="sxs-lookup"><span data-stu-id="922e9-231">To fix this, use [PowerShell to fix duplicate UPN](https://go.microsoft.com/fwlink/p/?LinkId=396730) to update the user's UPN to ensure that the Office 365 UPN matches the corporate user name and domain.</span></span> <span data-ttu-id="922e9-232">Wenn Sie den UPN im AD DS aktualisieren und mit der Azure Active Directory-Identität synchronisieren möchten, müssen Sie die Lizenz des Benutzers in Office 365 entfernen, bevor Sie die Änderungen in AD DS vornehmen.</span><span class="sxs-lookup"><span data-stu-id="922e9-232">If you are updating the UPN in the AD DS and would like it to synchronize with the Azure Active Directory identity, you need to remove the user's license in Office 365 prior to making the changes in AD DS.</span></span> 
  
<span data-ttu-id="922e9-233">Weitere Informationen finden Sie unter [Vorgehensweise Vorbereiten einer nicht routingfähigen Domäne (beispielsweise. Local Domain) für die Verzeichnissynchronisierung](prepare-a-non-routable-domain-for-directory-synchronization.md).</span><span class="sxs-lookup"><span data-stu-id="922e9-233">Also see [How to prepare a non-routable domain (such as .local domain) for directory synchronization](prepare-a-non-routable-domain-for-directory-synchronization.md).</span></span>


## <a name="next-steps"></a><span data-ttu-id="922e9-234">Weitere Schritte</span><span class="sxs-lookup"><span data-stu-id="922e9-234">Next steps</span></span>

<span data-ttu-id="922e9-235">Informationen zum Korrigieren von Fehlern in den Attributen ihrer AD DS vor der Verzeichnissynchronisierung finden Sie unter [Prepare Directory Attributes with the IdFix Tool](prepare-directory-attributes-for-synch-with-idfix.md) .</span><span class="sxs-lookup"><span data-stu-id="922e9-235">See [Prepare directory attributes with the IdFix tool](prepare-directory-attributes-for-synch-with-idfix.md) to help you correct errors in the attributes of your AD DS prior to directory synchronization.</span></span>

<span data-ttu-id="922e9-236">Wenn Sie alle mit dem IdFix-Tool identifizierten Attribut Fehler korrigiert haben und die Schritte 1 bis 5 oben ausgeführt haben, finden Sie weitere Informationen unter [Einrichten der Verzeichnissynchronisierung](set-up-directory-synchronization.md).</span><span class="sxs-lookup"><span data-stu-id="922e9-236">If you have corrected all the attribute errors identified with the IdFix tool and have done steps 1 through 5 above, see [Set up directory synchronization](set-up-directory-synchronization.md).</span></span>
