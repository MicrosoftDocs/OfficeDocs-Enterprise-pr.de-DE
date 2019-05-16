---
title: Schützen Ihrer globalen Office 365-Administratorkonten
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 4/10/2018
audience: Admin
ms.topic: get-started-article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Strat_O365_IP
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- BCS160
ms.assetid: 6b4ded77-ac8d-42ed-8606-c014fd947560
description: Schützen Sie den globalen Administratorzugriff auf Ihr Office 365-Abonnement mit diesen drei Schritten.
ms.openlocfilehash: bb1b19a7ac0ec8e32c23303e8acf2b7ee42f0532
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "34071021"
---
# <a name="protect-your-office-365-global-administrator-accounts"></a><span data-ttu-id="c36aa-103">Schützen Ihrer globalen Office 365-Administratorkonten</span><span class="sxs-lookup"><span data-stu-id="c36aa-103">Protect your Office 365 global administrator accounts</span></span>

 <span data-ttu-id="c36aa-104">**Zusammenfassung:** Schützen Sie Ihr Office 365-Abonnement vor Angriffen, die auf der Gefährdung durch ein globales Administratorkonto basieren.</span><span class="sxs-lookup"><span data-stu-id="c36aa-104">**Summary:** Protect your Office 365 subscription from attacks based on the compromise of a global administrator account.</span></span> 
  
<span data-ttu-id="c36aa-105">Sicherheitsverstöße gegen ein Office 365-Abonnement, einschließlich Informationen zum Sammeln und Phishing-Angriffen, werden in der Regel durch Kompromittierung der Anmeldeinformationen eines globalen Administratorkontos von Office 365 durchgeführt.</span><span class="sxs-lookup"><span data-stu-id="c36aa-105">Security breaches of an Office 365 subscription, including information harvesting and phishing attacks, are typically done by compromising the credentials of an Office 365 global administrator account.</span></span> <span data-ttu-id="c36aa-106">Sicherheit in der Cloud ist eine Partnerschaft zwischen Ihnen und Microsoft:</span><span class="sxs-lookup"><span data-stu-id="c36aa-106">Security in the cloud is a partnership between you and Microsoft:</span></span>
  
- <span data-ttu-id="c36aa-107">Microsoft Cloud Services basieren auf der Grundlage von Vertrauen und Sicherheit.</span><span class="sxs-lookup"><span data-stu-id="c36aa-107">Microsoft cloud services are built on a foundation of trust and security.</span></span> <span data-ttu-id="c36aa-108">Microsoft stellt Sicherheitskontrollen und-Funktionen zur Verfügung, mit denen Sie Ihre Daten und Anwendungen schützen können.</span><span class="sxs-lookup"><span data-stu-id="c36aa-108">Microsoft provides you security controls and capabilities to help you protect your data and applications.</span></span>
    
- <span data-ttu-id="c36aa-109">Sie besitzen Ihre Daten und Identitäten und die Verantwortung für den Schutz, die Sicherheit Ihrer lokalen Ressourcen und die Sicherheit von Cloud-Komponenten, die Sie steuern.</span><span class="sxs-lookup"><span data-stu-id="c36aa-109">You own your data and identities and the responsibility for protecting them, the security of your on-premises resources, and the security of cloud components you control.</span></span>
    
<span data-ttu-id="c36aa-110">Microsoft bietet Funktionen zum Schutz Ihrer Organisation, Sie sind jedoch nur dann wirksam, wenn Sie Sie verwenden.</span><span class="sxs-lookup"><span data-stu-id="c36aa-110">Microsoft provides capabilities to help protect your organization, but they are effective only if you use them.</span></span> <span data-ttu-id="c36aa-111">Wenn Sie Sie nicht verwenden, sind Sie möglicherweise anfällig für Angriffe.</span><span class="sxs-lookup"><span data-stu-id="c36aa-111">If you do not use them, you may be vulnerable to attack.</span></span> <span data-ttu-id="c36aa-112">Um Ihre globalen Administratorkonten zu schützen, steht Ihnen Microsoft mit detaillierten Anweisungen zur Verfügung:</span><span class="sxs-lookup"><span data-stu-id="c36aa-112">To protect your global administrator accounts, Microsoft is here to help you with detailed instructions to:</span></span>
  
1. <span data-ttu-id="c36aa-113">Erstellen Sie dedizierte globale Administratorkonten für Office 365, und verwenden Sie Sie nur bei Bedarf.</span><span class="sxs-lookup"><span data-stu-id="c36aa-113">Create dedicated Office 365 global administrator accounts and use them only when necessary.</span></span>
    
2. <span data-ttu-id="c36aa-114">Konfigurieren Sie die mehrstufige Authentifizierung für ihre dedizierten Office 365-globalen Administratorkonten, und verwenden Sie die stärkste Form der sekundären Authentifizierung.</span><span class="sxs-lookup"><span data-stu-id="c36aa-114">Configure multi-factor authentication for your dedicated Office 365 global administrator accounts and use the strongest form of secondary authentication.</span></span>
    
3. <span data-ttu-id="c36aa-115">Aktivieren und konfigurieren Sie die Office 365 Cloud App Security, um die Aktivität verdächtiger globaler Administratorkonten zu überwachen.</span><span class="sxs-lookup"><span data-stu-id="c36aa-115">Enable and configure Office 365 Cloud App Security to monitor for suspicious global administrator account activity.</span></span>
    
> [!NOTE]
> <span data-ttu-id="c36aa-116">Obwohl dieser Artikel auf globale Administratorkonten ausgerichtet ist, sollten Sie auch berücksichtigen, ob zusätzliche Konten mit weit reichenden Berechtigungen für den Zugriff auf die Daten in Ihrem Abonnement wie eDiscovery-Administrator oder Sicherheit oder Compliance Administratorkonten sollten auf die gleiche Weise geschützt werden.</span><span class="sxs-lookup"><span data-stu-id="c36aa-116">Although this article is focused on global administrator accounts, you should also consider whether additional accounts with wide-ranging permissions to access the data in your subscription, such as eDiscovery administrator or security or compliance administrator accounts, should be protected in the same way.</span></span> 
  
## <a name="step-1-create-dedicated-office-365-global-administrator-accounts-and-use-them-only-when-necessary"></a><span data-ttu-id="c36aa-117">Schritt 1:</span><span class="sxs-lookup"><span data-stu-id="c36aa-117">Step 1.</span></span> <span data-ttu-id="c36aa-118">Erstellen Sie dedizierte globale Administratorkonten für Office 365, und verwenden Sie Sie nur bei Bedarf.</span><span class="sxs-lookup"><span data-stu-id="c36aa-118">Create dedicated Office 365 global administrator accounts and use them only when necessary</span></span>

<span data-ttu-id="c36aa-119">Es gibt relativ wenige Verwaltungsaufgaben, wie das Zuweisen von Rollen zu Benutzerkonten, die globale Administratorrechte erfordern.</span><span class="sxs-lookup"><span data-stu-id="c36aa-119">There are relatively few administrative tasks, such as assigning roles to user accounts, that require global administrator privileges.</span></span> <span data-ttu-id="c36aa-120">Führen Sie daher anstelle der täglichen Benutzerkonten, denen die Rolle "globaler Administrator" zugewiesen wurde, die folgenden Schritte aus:</span><span class="sxs-lookup"><span data-stu-id="c36aa-120">Therefore, instead of using everyday user accounts that have been assigned the global admin role, do these steps:</span></span>
  
1. <span data-ttu-id="c36aa-121">Bestimmen Sie den Satz von Benutzerkonten, denen die Rolle globaler Administrator zugewiesen wurde.</span><span class="sxs-lookup"><span data-stu-id="c36aa-121">Determine the set of user accounts that have been assigned the global admin role.</span></span> <span data-ttu-id="c36aa-122">Sie können dies mit diesem Befehl an der Microsoft Azure Active Directory-Modul für Windows PowerShell-Eingabeaufforderungen tun:</span><span class="sxs-lookup"><span data-stu-id="c36aa-122">You can do this with this command at the Microsoft Azure Active Directory Module for Windows PowerShell command prompt:</span></span>
    
  ```
  Get-MsolRoleMember -RoleObjectId (Get-MsolRole -RoleName "Company Administrator").ObjectId
  ```

2. <span data-ttu-id="c36aa-123">Melden Sie sich bei Ihrem Office 365-Abonnement mit einem Benutzerkonto an, dem die Rolle "globaler Administrator" zugewiesen wurde.</span><span class="sxs-lookup"><span data-stu-id="c36aa-123">Sign into your Office 365 subscription with a user account that has been assigned the global admin role.</span></span>
    
3. <span data-ttu-id="c36aa-124">Erstellen Sie mindestens eine und maximal fünf dedizierte globale Administrator-Benutzerkonten.</span><span class="sxs-lookup"><span data-stu-id="c36aa-124">Create at least one and up to a maximum of five dedicated global administrator user accounts.</span></span> <span data-ttu-id="c36aa-125">**Verwenden Sie sichere Kennwörter, die mindestens 12 Zeichen lang sind.**</span><span class="sxs-lookup"><span data-stu-id="c36aa-125">**Use strong passwords at least 12 characters long.**</span></span> <span data-ttu-id="c36aa-126">Weitere Informationen finden Sie unter [Erstellen eines sicheren Kennworts](https://support.microsoft.com/help/4026406/microsoft-account-create-a-strong-password) .</span><span class="sxs-lookup"><span data-stu-id="c36aa-126">See [Create a strong password](https://support.microsoft.com/help/4026406/microsoft-account-create-a-strong-password) for more information.</span></span> <span data-ttu-id="c36aa-127">Speichern Sie die Kennwörter für die neuen Konten an einem sicheren Ort.</span><span class="sxs-lookup"><span data-stu-id="c36aa-127">Store the passwords for the new accounts in a secure location.</span></span> 
    
4. <span data-ttu-id="c36aa-128">Weisen Sie die globale Administratorrolle jedem der neuen dedizierten Benutzerkonten für globale Administratoren zu.</span><span class="sxs-lookup"><span data-stu-id="c36aa-128">Assign the global admin role to each of the new dedicated global administrator user accounts.</span></span>
    
5. <span data-ttu-id="c36aa-129">Abmelden von Office 365.</span><span class="sxs-lookup"><span data-stu-id="c36aa-129">Sign out of Office 365.</span></span>
    
6. <span data-ttu-id="c36aa-130">Melden Sie sich mit einem der neuen dedizierten globalen Administrator-Benutzerkonten an.</span><span class="sxs-lookup"><span data-stu-id="c36aa-130">Sign in with one of the new dedicated global administrator user accounts.</span></span>
    
7. <span data-ttu-id="c36aa-131">Für jedes vorhandene Benutzerkonto, dem die Rolle "globaler Administrator" aus Schritt 1 zugewiesen wurde:</span><span class="sxs-lookup"><span data-stu-id="c36aa-131">For each existing user account that had been assigned the global admin role from step 1:</span></span>
    
  - <span data-ttu-id="c36aa-132">Entfernen Sie die Rolle globaler Administrator.</span><span class="sxs-lookup"><span data-stu-id="c36aa-132">Remove the global admin role.</span></span>
    
  - <span data-ttu-id="c36aa-133">Weisen Sie dem Konto Administratorrollen zu, die für die Aufgaben Funktion und Verantwortlichkeit dieses Benutzers geeignet sind.</span><span class="sxs-lookup"><span data-stu-id="c36aa-133">Assign admin roles to the account that are appropriate to that user's job function and responsibility.</span></span> <span data-ttu-id="c36aa-134">Weitere Informationen zu den verschiedenen Administratorrollen in Office 365 finden Sie unter Informationen [zu Office 365-Administratorrollen](https://support.office.com/article/da585eea-f576-4f55-a1e0-87090b6aaa9d).</span><span class="sxs-lookup"><span data-stu-id="c36aa-134">For more information about various admin roles in Office 365, see [About Office 365 admin roles](https://support.office.com/article/da585eea-f576-4f55-a1e0-87090b6aaa9d).</span></span>
    
8. <span data-ttu-id="c36aa-135">Abmelden von Office 365.</span><span class="sxs-lookup"><span data-stu-id="c36aa-135">Sign out of Office 365.</span></span>
    
<span data-ttu-id="c36aa-136">Das Ergebnis sollte:</span><span class="sxs-lookup"><span data-stu-id="c36aa-136">The result should be:</span></span>
  
- <span data-ttu-id="c36aa-137">Die einzigen Benutzerkonten in Ihrem Abonnement, die über die Berechtigungen eines globalen Administrators verfügen, befinden sich im neuen Satz der dedizierten Konten für globale Administratoren.</span><span class="sxs-lookup"><span data-stu-id="c36aa-137">The only user accounts in your subscription that have the global admin role are the new set of dedicated global administrator accounts.</span></span> <span data-ttu-id="c36aa-138">Überprüfen Sie dies mit dem folgenden PowerShell-Befehl:</span><span class="sxs-lookup"><span data-stu-id="c36aa-138">Verify this with the following PowerShell command:</span></span>
    
  ```
  Get-MsolRoleMember -RoleObjectId (Get-MsolRole -RoleName "Company Administrator").ObjectId
  ```

- <span data-ttu-id="c36aa-139">Alle anderen normalen Benutzerkonten für die Verwaltung Ihres Abonnements verfügen über Administratorrollen, die ihren beruflichen Zuständigkeiten zugewiesen sind.</span><span class="sxs-lookup"><span data-stu-id="c36aa-139">All other everyday user accounts that manage your subscription have admin roles assigned that are associated with their job responsibilities.</span></span>
    
<span data-ttu-id="c36aa-140">Ab diesem Moment melden Sie sich mit den dedizierten globalen Administratorkonten nur für Aufgaben an, die globale Administratorrechte erfordern.</span><span class="sxs-lookup"><span data-stu-id="c36aa-140">From this moment onward, you sign in with the dedicated global administrator accounts only for tasks that require global administrator privileges.</span></span> <span data-ttu-id="c36aa-141">Alle anderen Office 365-Administration müssen durch Zuweisen von anderen Administratorrollen zu Benutzerkonten erfolgen.</span><span class="sxs-lookup"><span data-stu-id="c36aa-141">All other Office 365 administration must be done by assigning other administration roles to user accounts.</span></span>
  
> [!NOTE]
> <span data-ttu-id="c36aa-142">Ja, dies erfordert zusätzliche Schritte, um sich als alltägliches Benutzerkonto abzumelden und sich mit einem dedizierten globalen Administratorkonto anzumelden.</span><span class="sxs-lookup"><span data-stu-id="c36aa-142">Yes, this requires additional steps to sign out as your everyday user account and sign in with a dedicated global administrator account.</span></span> <span data-ttu-id="c36aa-143">Dies muss jedoch nur gelegentlich für globale Administrator Vorgänge erfolgen.</span><span class="sxs-lookup"><span data-stu-id="c36aa-143">But this only needs to be done occasionally for global administrator operations.</span></span> <span data-ttu-id="c36aa-144">Bedenken Sie, dass das Wiederherstellen Ihres Office 365-Abonnements nach einer Verletzung globaler Administratorkonten viele weitere Schritte erfordert.</span><span class="sxs-lookup"><span data-stu-id="c36aa-144">Consider that recovering your Office 365 subscription after a global administrator account breach requires a lot more steps.</span></span> 
  
## <a name="step-2-configure-multi-factor-authentication-for-your-dedicated-office-365-global-administrator-accounts-and-use-the-strongest-form-of-secondary-authentication"></a><span data-ttu-id="c36aa-145">Schritt 2:</span><span class="sxs-lookup"><span data-stu-id="c36aa-145">Step 2.</span></span> <span data-ttu-id="c36aa-146">Konfigurieren Sie die mehrstufige Authentifizierung für ihre dedizierten Office 365-globalen Administratorkonten, und verwenden Sie die stärkste Form der sekundären Authentifizierung.</span><span class="sxs-lookup"><span data-stu-id="c36aa-146">Configure multi-factor authentication for your dedicated Office 365 global administrator accounts and use the strongest form of secondary authentication</span></span>

<span data-ttu-id="c36aa-147">Multi-Factor Authentication (MFA) für Ihre globalen Administratorkonten erfordert zusätzliche Informationen über den Kontonamen und das Kennwort hinaus.</span><span class="sxs-lookup"><span data-stu-id="c36aa-147">Multi-factor authentication (MFA) for your global administrator accounts requires additional information beyond the account name and password.</span></span> <span data-ttu-id="c36aa-148">Office 365 unterstützt diese Überprüfungsmethoden:</span><span class="sxs-lookup"><span data-stu-id="c36aa-148">Office 365 supports these verification methods:</span></span>
  
- <span data-ttu-id="c36aa-149">Ein Telefonanruf</span><span class="sxs-lookup"><span data-stu-id="c36aa-149">A phone call</span></span>
    
- <span data-ttu-id="c36aa-150">Ein zufällig generierter Passcode</span><span class="sxs-lookup"><span data-stu-id="c36aa-150">A randomly generated pass code</span></span>
    
- <span data-ttu-id="c36aa-151">Eine Smartcard (virtuell oder physisch)</span><span class="sxs-lookup"><span data-stu-id="c36aa-151">A smart card (virtual or physical)</span></span>
    
- <span data-ttu-id="c36aa-152">Ein biometrisches Gerät</span><span class="sxs-lookup"><span data-stu-id="c36aa-152">A biometric device</span></span>
    
<span data-ttu-id="c36aa-153">Wenn Sie ein kleines Unternehmen sind, das Benutzerkonten verwendet, die nur in der Cloud gespeichert sind (das Cloud-Identitätsmodell), verwenden Sie die folgenden Schritte zum Konfigurieren von MFA mithilfe eines Telefonanrufs oder eines Textnachrichten-Überprüfungscodes, der an ein Smartphone gesendet wird:</span><span class="sxs-lookup"><span data-stu-id="c36aa-153">If you are a small business that is using user accounts stored only in the cloud (the cloud identity model), use these steps to configure MFA using a phone call or a text message verification code sent to a smart phone:</span></span>
  
1. <span data-ttu-id="c36aa-154">[Aktivieren Sie MFA](https://support.office.com/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6).</span><span class="sxs-lookup"><span data-stu-id="c36aa-154">[Enable MFA](https://support.office.com/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6).</span></span>
    
2. <span data-ttu-id="c36aa-155">Richten Sie die Überprüfung in [zwei Schritten für Office 365](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14) ein, um jedes dedizierte globale Administratorkonto für Telefonanrufe oder Textnachrichten als Überprüfungsmethode zu konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="c36aa-155">[Set up 2-step verification for Office 365](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14) to configure each dedicated global administrator account for phone call or text message as the verification method.</span></span> 
    
<span data-ttu-id="c36aa-156">Wenn Sie eine größere Organisation sind, die ein Office 365-Hybrid Identitätsmodell verwendet, haben Sie weitere Überprüfungsoptionen.</span><span class="sxs-lookup"><span data-stu-id="c36aa-156">If you are a larger organization that is using an Office 365 hybrid identity model, you have more verification options.</span></span> <span data-ttu-id="c36aa-157">Wenn die Sicherheitsinfrastruktur für eine stärkere sekundäre Authentifizierungsmethode bereits vorhanden ist, führen Sie die folgenden Schritte aus:</span><span class="sxs-lookup"><span data-stu-id="c36aa-157">If you have the security infrastructure already in place for a stronger secondary authentication method, use these steps:</span></span>
  
1. <span data-ttu-id="c36aa-158">[Aktivieren Sie MFA](https://support.office.com/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6).</span><span class="sxs-lookup"><span data-stu-id="c36aa-158">[Enable MFA](https://support.office.com/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6).</span></span>
    
2. <span data-ttu-id="c36aa-159">[Richten Sie die Überprüfung in zwei Schritten für Office 365](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14) ein, um jedes dedizierte globale Administratorkonto für die entsprechende Überprüfungsmethode zu konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="c36aa-159">[Set up 2-step verification for Office 365](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14) to configure each dedicated global administrator account for the appropriate verification method.</span></span> 
    
<span data-ttu-id="c36aa-160">Wenn die Sicherheitsinfrastruktur für die gewünschte stärkere Überprüfungsmethode nicht vorhanden und für Office 365 MFA funktioniert, wird dringend empfohlen, dass Sie dedizierte globale Administratorkonten mit MFA mithilfe eines Telefonanrufs oder einer Textnachricht konfigurieren. Überprüfungscode, der für Ihre globalen Administratorkonten an ein Smartphone gesendet wird, als vorläufige Sicherheitsmaßnahme.</span><span class="sxs-lookup"><span data-stu-id="c36aa-160">If the security infrastructure for the desired stronger verification method is not in place and functioning for Office 365 MFA, we strongly recommend that you configure dedicated global administrator accounts with MFA using a phone call or a text message verification code sent to a smart phone for your global administrator accounts as an interim security measure.</span></span> <span data-ttu-id="c36aa-161">Lassen Sie Ihre dedizierten globalen Administratorkonten nicht ohne zusätzlichen Schutz durch MFA.</span><span class="sxs-lookup"><span data-stu-id="c36aa-161">Do not leave your dedicated global administrator accounts without the additional protection provided by MFA.</span></span>
  
<span data-ttu-id="c36aa-162">Weitere Informationen finden Sie unter [Planen der mehrstufigen Authentifizierung für Office 365-Bereitstellungen](https://support.office.com/article/043807b2-21db-4d5c-b430-c8a6dee0e6ba).</span><span class="sxs-lookup"><span data-stu-id="c36aa-162">For more information, see [Plan for multi-factor authentication for Office 365 Deployments](https://support.office.com/article/043807b2-21db-4d5c-b430-c8a6dee0e6ba).</span></span>
  
<span data-ttu-id="c36aa-163">Informationen zum Herstellen einer Verbindung mit Office 365-Diensten mit MFA und PowerShell finden Sie in [diesem Artikel](https://blogs.technet.microsoft.com/solutions_advisory_board/2017/04/27/connect-to-office-365-services-with-multifactor-authentication-mfa-and-powershell/).</span><span class="sxs-lookup"><span data-stu-id="c36aa-163">To connect to Office 365 services with MFA and PowerShell, see [this article](https://blogs.technet.microsoft.com/solutions_advisory_board/2017/04/27/connect-to-office-365-services-with-multifactor-authentication-mfa-and-powershell/).</span></span>
  
## <a name="step-3-monitor-for-suspicious-global-administrator-account-activity"></a><span data-ttu-id="c36aa-164">Schritt 3:</span><span class="sxs-lookup"><span data-stu-id="c36aa-164">Step 3.</span></span> <span data-ttu-id="c36aa-165">Überwachung der Aktivität verdächtiger globaler Administratorkonten</span><span class="sxs-lookup"><span data-stu-id="c36aa-165">Monitor for suspicious global administrator account activity</span></span>

<span data-ttu-id="c36aa-166">Mit Office 365 Cloud App Security können Sie Richtlinien erstellen, die Sie über verdächtiges Verhalten in Ihrem Abonnement informieren.</span><span class="sxs-lookup"><span data-stu-id="c36aa-166">Office 365 Cloud App Security lets you create policies to notify you of suspicious behavior in your subscription.</span></span> <span data-ttu-id="c36aa-167">Cloud App Security ist in Office 365 E5 integriert, steht aber auch als separater Dienst zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="c36aa-167">Cloud App Security is built into Office 365 E5, but is also available as a separate service.</span></span> <span data-ttu-id="c36aa-168">Wenn Sie beispielsweise nicht über Office 365 E5 verfügen, können Sie einzelne Cloud-App-Sicherheits Lizenzen für die Benutzerkonten erwerben, denen die Rollen "globaler Administrator", "Sicherheitsadministrator" und "Compliance-Administrator" zugewiesen sind.</span><span class="sxs-lookup"><span data-stu-id="c36aa-168">For example, if you do not have Office 365 E5, you can purchase individual Cloud App Security licenses for the user accounts that are assigned the global administrator, security administrator, and compliance administrator roles.</span></span>
  
<span data-ttu-id="c36aa-169">Wenn Sie über Cloud-App-Sicherheit in Ihrem Office 365-Abonnement verfügen, führen Sie die folgenden Schritte aus:</span><span class="sxs-lookup"><span data-stu-id="c36aa-169">If you have Cloud App Security in your Office 365 subscription, use these steps:</span></span>
  
1. <span data-ttu-id="c36aa-170">Melden Sie sich beim Microsoft 365 Admin Center mit einem Konto an, dem die Rolle "Sicherheitsadministrator" oder "Compliance-Administrator" zugewiesen ist.</span><span class="sxs-lookup"><span data-stu-id="c36aa-170">Sign into the Microsoft 365 admin center with an account that is assigned the Security Administrator or Compliance Administrator role.</span></span>
    
2. <span data-ttu-id="c36aa-171">[Aktivieren Sie Office 365 Cloud App Security](https://support.office.com/article/ba919c73-d021-404d-9850-eec57e78678c).</span><span class="sxs-lookup"><span data-stu-id="c36aa-171">[Turn on Office 365 Cloud App Security](https://support.office.com/article/ba919c73-d021-404d-9850-eec57e78678c).</span></span>
    
3. <span data-ttu-id="c36aa-172">Überprüfung der [Anomalie-Erkennungsrichtlinien in Office 365 Cloud App Security](https://support.office.com/article/88935b4e-dcb1-47f1-8aca-1bf8fb069db6) , um Sie per e-Mail über anomale Muster der privilegierten Verwaltungsaktivität zu informieren.</span><span class="sxs-lookup"><span data-stu-id="c36aa-172">Review your [Anomaly detection policies in Office 365 Cloud App Security](https://support.office.com/article/88935b4e-dcb1-47f1-8aca-1bf8fb069db6) to notify you by email of anomalous patterns of privileged administrative activity.</span></span> 
    
<span data-ttu-id="c36aa-173">Wenn Sie der Sicherheits Administrator Rolle ein Benutzerkonto hinzufügen möchten, stellen Sie eine [Verbindung mit Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx#step3) mit einem dedizierten globalen Administrator Konto und MFA her, geben Sie den Benutzerprinzipalnamen des Benutzerkontos ein, und führen Sie dann die folgenden Befehle aus:</span><span class="sxs-lookup"><span data-stu-id="c36aa-173">To add a user account to the Security Administrator role, [connect to Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx#step3) with a dedicated global administrator account and MFA, fill in the user principal name of the user account, and then run these commands:</span></span> 
  
```
$upn="<User principal name of the account>"
Add-MsolRoleMember -RoleMemberEmailAddress $upn -RoleName "Security Administrator"
```

<span data-ttu-id="c36aa-174">Geben Sie zum Hinzufügen eines Benutzerkontos zur Rolle "Compliance-Administrator" den Benutzerprinzipalnamen des Benutzerkontos ein, und führen Sie dann die folgenden Befehle aus:</span><span class="sxs-lookup"><span data-stu-id="c36aa-174">To add a user account to the Compliance Administrator role, fill in the user principal name of the user account, and then run these commands:</span></span>
  
```
$upn="<User principal name of the account>"
Add-MsolRoleMember -RoleMemberEmailAddress  $upn -RoleName "Compliance Administrator"
```

## <a name="additional-protections-for-enterprise-organizations"></a><span data-ttu-id="c36aa-175">Zusätzliche Schutzmaßnahmen für Unternehmensorganisationen</span><span class="sxs-lookup"><span data-stu-id="c36aa-175">Additional protections for enterprise organizations</span></span>

<span data-ttu-id="c36aa-176">Nach den Schritten 1-3, verwenden Sie diese zusätzlichen Methoden, um sicherzustellen, dass ihr globales Administratorkonto und die Konfiguration, die Sie verwenden, so sicher wie möglich sind.</span><span class="sxs-lookup"><span data-stu-id="c36aa-176">After steps 1-3, use these additional methods to ensure that your global administrator account, and the configuration that you perform using it, are as secure as possible.</span></span>
  
### <a name="privileged-access-workstation-paw"></a><span data-ttu-id="c36aa-177">Workstation mit privilegiertem Zugriff (PAW)</span><span class="sxs-lookup"><span data-stu-id="c36aa-177">Privileged Access Workstation (PAW)</span></span>

<span data-ttu-id="c36aa-178">Um sicherzustellen, dass die Ausführung hoch privilegierter Aufgaben so sicher wie möglich ist, verwenden Sie eine Paw.</span><span class="sxs-lookup"><span data-stu-id="c36aa-178">To ensure that the execution of highly privileged tasks is as secure as possible, use a PAW.</span></span> <span data-ttu-id="c36aa-179">Eine Pfote ist ein dedizierter Computer, der nur für vertrauliche Konfigurationsaufgaben wie Office 365-Konfiguration verwendet wird, die ein globales Administratorkonto erfordert.</span><span class="sxs-lookup"><span data-stu-id="c36aa-179">A PAW is a dedicated computer that is only used for sensitive configuration tasks, such as Office 365 configuration that requires a global administrator account.</span></span> <span data-ttu-id="c36aa-180">Da dieser Computer nicht täglich für das Surfen im Internet oder per e-Mail verwendet wird, ist er besser vor Internetangriffen und-Bedrohungen geschützt.</span><span class="sxs-lookup"><span data-stu-id="c36aa-180">Because this computer is not used daily for Internet browsing or email, it is better protected from Internet attacks and threats.</span></span>
  
<span data-ttu-id="c36aa-181">Anweisungen zum Einrichten einer Pfote finden Sie unter [http://aka.ms/cyberpaw](http://aka.ms/cyberpaw).</span><span class="sxs-lookup"><span data-stu-id="c36aa-181">For instructions on how to set up a PAW, see [http://aka.ms/cyberpaw](http://aka.ms/cyberpaw).</span></span>
  
### <a name="azure-ad-privileged-identity-management-pim"></a><span data-ttu-id="c36aa-182">Azure AD Privileged Identity Management (PIM)</span><span class="sxs-lookup"><span data-stu-id="c36aa-182">Azure AD Privileged Identity Management (PIM)</span></span>

<span data-ttu-id="c36aa-183">Anstatt ihren globalen Administratorkonten die globale Administratorrolle dauerhaft zuzuweisen, können Sie Azure AD PIM verwenden, um die bedarfsgerechte Zuweisung der globalen Administratorrolle bei Bedarf zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="c36aa-183">Rather than having your global administrator accounts be permanently assigned the global administrator role, you can use Azure AD PIM to enable on-demand, just-in-time assignment of the global administrator role when it is needed.</span></span>
  
<span data-ttu-id="c36aa-184">Statt der globalen Administratorkonten, die ein permanenter admin sind, werden Sie zu geeigneten Administratoren.</span><span class="sxs-lookup"><span data-stu-id="c36aa-184">Instead of your global administrator accounts being a permanent admin, they become eligible administrators.</span></span> <span data-ttu-id="c36aa-185">Die globale Administratorrolle ist inaktiv, bis jemand Sie benötigt.</span><span class="sxs-lookup"><span data-stu-id="c36aa-185">The global administrator role is inactive until someone needs it.</span></span> <span data-ttu-id="c36aa-186">Anschließend führen Sie einen Aktivierungsprozess aus, um die globale Administratorrolle für eine festgelegte Zeitdauer dem globalen Administratorkonto hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="c36aa-186">You then complete an activation process to add the global administrator role to the global administrator account for a predetermined amount of time.</span></span> <span data-ttu-id="c36aa-187">Wenn die Zeit abgelaufen ist, entfernt PIM die globale Administratorrolle aus dem globalen Administratorkonto.</span><span class="sxs-lookup"><span data-stu-id="c36aa-187">When the time expires, PIM removes the global administrator role from the global administrator account.</span></span>
  
<span data-ttu-id="c36aa-188">Durch die Verwendung von PIM und diesem Prozess wird der Zeitraum, in dem Ihre globalen Administratorkonten anfällig für Angriffe und die Verwendung durch böswillige Benutzer sind, deutlich reduziert.</span><span class="sxs-lookup"><span data-stu-id="c36aa-188">Using PIM and this process significantly reduces the amount of time that your global administrator accounts are vulnerable to attack and use by malicious users.</span></span>
  
<span data-ttu-id="c36aa-189">Weitere Informationen finden Sie unter [configure Azure AD Privileged Identity Management](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure).</span><span class="sxs-lookup"><span data-stu-id="c36aa-189">For more information, see [Configure Azure AD Privileged Identity Management](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure).</span></span>
  
> [!NOTE]
> <span data-ttu-id="c36aa-190">PIM ist mit Azure Active Directory Premium P2 verfügbar, das in Enterprise Mobility + Security (EMS) E5 enthalten ist, oder Sie können einzelne Lizenzen für Ihre globalen Administratorkonten erwerben.</span><span class="sxs-lookup"><span data-stu-id="c36aa-190">PIM is available with Azure Active Directory Premium P2, which is included with Enterprise Mobility + Security (EMS) E5, or you can purchase individual licenses for your global administrator accounts.</span></span> 
  
### <a name="security-information-and-event-management-siem-software-for-office-365-logging"></a><span data-ttu-id="c36aa-191">Security Information and Event Management (SIEM)-Software für Office 365-Protokollierung</span><span class="sxs-lookup"><span data-stu-id="c36aa-191">Security information and event management (SIEM) software for Office 365 logging</span></span>

<span data-ttu-id="c36aa-192">Siem-Software, die auf einem Server ausgeführt wird, führt eine Echtzeitanalyse von Sicherheitswarnungen und Ereignissen aus, die von Anwendungen und Netzwerkhardware erstellt wurden.</span><span class="sxs-lookup"><span data-stu-id="c36aa-192">SIEM software run on a server performs real-time analysis of security alerts and events created by applications and network hardware.</span></span> <span data-ttu-id="c36aa-193">Damit Ihr Siem-Server Office 365-Sicherheitswarnungen und-Ereignisse in seine Analyse-und Berichtfunktionen einbinden kann, integrieren Sie diese in Ihr Siem-System:</span><span class="sxs-lookup"><span data-stu-id="c36aa-193">To allow your SIEM server to include Office 365 security alerts and events in its analysis and reporting functions, integrate these in your SIEM system:</span></span>
  
- <span data-ttu-id="c36aa-194">Azure AD</span><span class="sxs-lookup"><span data-stu-id="c36aa-194">Azure AD</span></span>
    
    <span data-ttu-id="c36aa-195">Weitere Informationen finden Sie unter [integrieren von Protokollen aus Azure-Ressourcen in Ihre Siem-Systeme](https://docs.microsoft.com/azure/security/security-azure-log-integration-overview).</span><span class="sxs-lookup"><span data-stu-id="c36aa-195">For more information, see [Integrate logs from Azure resources into your SIEM systems](https://docs.microsoft.com/azure/security/security-azure-log-integration-overview).</span></span>
    
- <span data-ttu-id="c36aa-196">Office 365 Cloud App Security</span><span class="sxs-lookup"><span data-stu-id="c36aa-196">Office 365 Cloud App Security</span></span>
    
    <span data-ttu-id="c36aa-197">Weitere Informationen finden Sie unter [integrieren Ihres Siem-Servers in Office 365 Cloud App Security](https://support.office.com/article/dd6d2417-49c4-4de6-9294-67fdabbf8532).</span><span class="sxs-lookup"><span data-stu-id="c36aa-197">For more information, see [Integrate your SIEM server with Office 365 Cloud App Security](https://support.office.com/article/dd6d2417-49c4-4de6-9294-67fdabbf8532).</span></span>
    
## <a name="next-step"></a><span data-ttu-id="c36aa-198">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="c36aa-198">Next step</span></span>

<span data-ttu-id="c36aa-199">Weitere Informationen finden Sie unter [bewährte Methoden für die Sicherheit für Office 365](https://support.office.com/article/9295e396-e53d-49b9-ae9b-0b5828cdedc3).</span><span class="sxs-lookup"><span data-stu-id="c36aa-199">See [Security best practices for Office 365](https://support.office.com/article/9295e396-e53d-49b9-ae9b-0b5828cdedc3).</span></span>
  

