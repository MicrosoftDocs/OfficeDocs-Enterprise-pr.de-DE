---
title: Schützen Ihrer globalen Office 365-Administratorkonten
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 4/10/2018
ms.audience: Admin
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
description: Globaler Administratorzugriff auf Ihre Office 365-Abonnements mit dieser drei Schritte zu schützen.
ms.openlocfilehash: 41168643fb8867017865860624c8b436460fa0b8
ms.sourcegitcommit: bbbe304bb1878b04e719103be4287703fb3ef292
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "25897518"
---
# <a name="protect-your-office-365-global-administrator-accounts"></a><span data-ttu-id="65749-103">Schützen Ihrer globalen Office 365-Administratorkonten</span><span class="sxs-lookup"><span data-stu-id="65749-103">Protect your Office 365 global administrator accounts</span></span>

 <span data-ttu-id="65749-104">**Zusammenfassung:** Schützen Sie Ihre Office 365-Abonnements vor Angriffen, die basierend auf die Gefährdung als globaler Administrator an.</span><span class="sxs-lookup"><span data-stu-id="65749-104">**Summary:** Protect your Office 365 subscription from attacks based on the compromise of a global administrator account.</span></span> 
  
<span data-ttu-id="65749-p101">Sicherheitsverstößen gegen ein Office 365-Abonnement, einschließlich Informationen zu sammeln und Phishing-Angriffe erfolgen in der Regel durch die Anmeldeinformationen des Office 365-Konto globaler Administrator gefährden. Sicherheit in der Cloud ist eine Partnerschaft zwischen Ihnen und Microsoft:</span><span class="sxs-lookup"><span data-stu-id="65749-p101">Security breaches of an Office 365 subscription, including information harvesting and phishing attacks, are typically done by compromising the credentials of an Office 365 global administrator account. Security in the cloud is a partnership between you and Microsoft:</span></span>
  
- <span data-ttu-id="65749-p102">Microsoft Cloud-Dienste werden auf Grundlage von vertrauen und Sicherheit erstellt. Microsoft bietet Sie Sicherheitssteuerelemente und Funktionen, mit denen Sie Ihre Daten und Anwendungen zu schützen.</span><span class="sxs-lookup"><span data-stu-id="65749-p102">Microsoft cloud services are built on a foundation of trust and security. Microsoft provides you security controls and capabilities to help you protect your data and applications.</span></span>
    
- <span data-ttu-id="65749-109">Sie besitzen die Daten und Identitäten und die Verantwortung für den Schutz von ihnen, die Sicherheit Ihrer lokalen Ressourcen und die Sicherheit der Cloud-Komponenten, die Sie steuern.</span><span class="sxs-lookup"><span data-stu-id="65749-109">You own your data and identities and the responsibility for protecting them, the security of your on-premises resources, and the security of cloud components you control.</span></span>
    
<span data-ttu-id="65749-p103">Microsoft bietet Funktionen zum Schutz Ihrer Organisation, aber sie sind nur wirksam, wenn Sie diese verwenden. Wenn Sie sie nicht verwenden, können Sie anfällig sein. Um Ihre globalen Administratorkonten zu schützen, ist Microsoft hier Sie nähere Informationen zum zu unterstützen:</span><span class="sxs-lookup"><span data-stu-id="65749-p103">Microsoft provides capabilities to help protect your organization, but they are effective only if you use them. If you do not use them, you may be vulnerable to attack. To protect your global administrator accounts, Microsoft is here to help you with detailed instructions to:</span></span>
  
1. <span data-ttu-id="65749-113">Erstellen Sie dedizierte Office 365 globaler Administrator Benutzerkonten und verwenden sie bei Bedarf.</span><span class="sxs-lookup"><span data-stu-id="65749-113">Create dedicated Office 365 global administrator accounts and use them only when necessary.</span></span>
    
2. <span data-ttu-id="65749-114">Konfigurieren Sie mehrstufige Authentifizierung für Ihre dedizierten Office 365 globaler Administratorkonten und verwenden Sie die sicherste sekundäre Authentifizierung.</span><span class="sxs-lookup"><span data-stu-id="65749-114">Configure multi-factor authentication for your dedicated Office 365 global administrator accounts and use the strongest form of secondary authentication.</span></span>
    
3. <span data-ttu-id="65749-115">Aktivieren und Konfigurieren von Office 365-Cloud-App-Sicherheit zum Überwachen von Kontoaktivitäten verdächtigen globaler Administrator.</span><span class="sxs-lookup"><span data-stu-id="65749-115">Enable and configure Office 365 Cloud App Security to monitor for suspicious global administrator account activity.</span></span>
    
> [!NOTE]
> <span data-ttu-id="65749-116">Obwohl in diesem Artikel auf globale Administratorkonten gerichtet ist, berücksichtigen Sie auch, ob zusätzliche Konten mit umfassende Berechtigungen für den Datenzugriff im Rahmen Ihres Abonnements, wie eDiscovery-Administrator oder Sicherheits- oder kompatibilitätsanforderungen Administratorkonten, sollte die gleiche Weise geschützt werden.</span><span class="sxs-lookup"><span data-stu-id="65749-116">Although this article is focused on global administrator accounts, you should also consider whether additional accounts with wide-ranging permissions to access the data in your subscription, such as eDiscovery administrator or security or compliance administrator accounts, should be protected in the same way.</span></span> 
  
## <a name="step-1-create-dedicated-office-365-global-administrator-accounts-and-use-them-only-when-necessary"></a><span data-ttu-id="65749-p104">Schritt 1. Erstellen Sie dedizierte Office 365 globaler Administrator Benutzerkonten und verwenden sie bei Bedarf</span><span class="sxs-lookup"><span data-stu-id="65749-p104">Step 1. Create dedicated Office 365 global administrator accounts and use them only when necessary</span></span>

<span data-ttu-id="65749-p105">Relativ wenige administrative Aufgaben wie das Zuweisen von Rollen zu Benutzerkonten, die globale Administratorrechte erforderlich sind. Aus diesem Grund statt alltägliche Benutzerkonten, die die globalen Administratorrolle zugewiesen wurden, führen Sie diese Schritte:</span><span class="sxs-lookup"><span data-stu-id="65749-p105">There are relatively few administrative tasks, such as assigning roles to user accounts, that require global administrator privileges. Therefore, instead of using everyday user accounts that have been assigned the global admin role, do these steps:</span></span>
  
1. <span data-ttu-id="65749-p106">Ermitteln der Benutzerkonten, die die globalen Administratorrolle zugewiesen wurden. Hierzu können Sie mit diesem Befehl an der Microsoft Azure Active Directory-Modul für Windows PowerShell-Eingabeaufforderung:</span><span class="sxs-lookup"><span data-stu-id="65749-p106">Determine the set of user accounts that have been assigned the global admin role. You can do this with this command at the Microsoft Azure Active Directory Module for Windows PowerShell command prompt:</span></span>
    
  ```
  Get-MsolRoleMember -RoleObjectId (Get-MsolRole -RoleName "Company Administrator").ObjectId
  ```

2. <span data-ttu-id="65749-123">Melden Sie sich bei Ihrem Office 365-Abonnement mit einem Benutzerkonto, das die globalen Administratorrolle zugewiesen wurde.</span><span class="sxs-lookup"><span data-stu-id="65749-123">Sign into your Office 365 subscription with a user account that has been assigned the global admin role.</span></span>
    
3. <span data-ttu-id="65749-p107">Erstellen Sie mindestens einen und bis zu fünf dedizierte Benutzerkonten globaler Administrator. **Verwendung sicherer Kennwörter mindestens 12 Zeichen lang.** Weitere Informationen finden Sie unter [Erstellen eines sicheren Kennworts](https://support.microsoft.com/help/4026406/microsoft-account-create-a-strong-password) . Speichern Sie die Kennwörter für das neue Konto an einem sicheren Ort.</span><span class="sxs-lookup"><span data-stu-id="65749-p107">Create at least one and up to a maximum of five dedicated global administrator user accounts. **Use strong passwords at least 12 characters long.** See [Create a strong password](https://support.microsoft.com/help/4026406/microsoft-account-create-a-strong-password) for more information. Store the passwords for the new accounts in a secure location.</span></span> 
    
4. <span data-ttu-id="65749-128">Weisen Sie der globalen Administratorrolle für jeden der neue dedizierte globaler Administratorbenutzerkonten.</span><span class="sxs-lookup"><span data-stu-id="65749-128">Assign the global admin role to each of the new dedicated global administrator user accounts.</span></span>
    
5. <span data-ttu-id="65749-129">Melden Sie bei Office 365 ab.</span><span class="sxs-lookup"><span data-stu-id="65749-129">Sign out of Office 365.</span></span>
    
6. <span data-ttu-id="65749-130">Melden Sie sich mit einer neuen dedizierten globaler Administrator Benutzerkonten.</span><span class="sxs-lookup"><span data-stu-id="65749-130">Sign in with one of the new dedicated global administrator user accounts.</span></span>
    
7. <span data-ttu-id="65749-131">Für alle vorhandenen Benutzerkonten, die die globalen Administratorrolle aus Schritt 1 zugewiesen wurde:</span><span class="sxs-lookup"><span data-stu-id="65749-131">For each existing user account that had been assigned the global admin role from step 1:</span></span>
    
  - <span data-ttu-id="65749-132">Entfernen der globalen Administratorrolle.</span><span class="sxs-lookup"><span data-stu-id="65749-132">Remove the global admin role.</span></span>
    
  - <span data-ttu-id="65749-p108">Zuweisen von Administratorrollen für das Konto, das für dieses Benutzers Funktion und Verantwortung geeignet sind. Weitere Informationen zu verschiedenen Administratorrollen in Office 365 finden Sie unter [Informationen zu Office 365-Administratorrollen](https://support.office.com/article/da585eea-f576-4f55-a1e0-87090b6aaa9d).</span><span class="sxs-lookup"><span data-stu-id="65749-p108">Assign admin roles to the account that are appropriate to that user's job function and responsibility. For more information about various admin roles in Office 365, see [About Office 365 admin roles](https://support.office.com/article/da585eea-f576-4f55-a1e0-87090b6aaa9d).</span></span>
    
8. <span data-ttu-id="65749-135">Melden Sie bei Office 365 ab.</span><span class="sxs-lookup"><span data-stu-id="65749-135">Sign out of Office 365.</span></span>
    
<span data-ttu-id="65749-136">Das Ergebnis sollte wie folgt lauten:</span><span class="sxs-lookup"><span data-stu-id="65749-136">The result should be:</span></span>
  
- <span data-ttu-id="65749-p109">Die einzige Benutzerkonten im Rahmen Ihres Abonnements mit der globalen Administratorrolle sind die neuen Satz von dedizierten globalen Administratorkonten. Überprüfen Sie dies mit dem folgenden PowerShell-Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="65749-p109">The only user accounts in your subscription that have the global admin role are the new set of dedicated global administrator accounts. Verify this with the following PowerShell command:</span></span>
    
  ```
  Get-MsolRoleMember -RoleObjectId (Get-MsolRole -RoleName "Company Administrator").ObjectId
  ```

- <span data-ttu-id="65749-139">Alle anderen normalen Benutzerkonten für die Verwaltung Ihres Abonnements verfügen über Administratorrollen, die ihren beruflichen Zuständigkeiten zugewiesen sind.</span><span class="sxs-lookup"><span data-stu-id="65749-139">All other everyday user accounts that manage your subscription have admin roles assigned that are associated with their job responsibilities.</span></span>
    
<span data-ttu-id="65749-p110">Aus ab diesem Zeitpunkt melden Sie sich mit den dedizierten globalen Administratorkonten nur für Aufgaben vorgestellt, die globale Administratorrechte erforderlich. Alle anderen Office 365-Verwaltung muss durch Zuweisen von anderen Administratorrollen zu Benutzerkonten erfolgen.</span><span class="sxs-lookup"><span data-stu-id="65749-p110">From this moment onward, you sign in with the dedicated global administrator accounts only for tasks that require global administrator privileges. All other Office 365 administration must be done by assigning other administration roles to user accounts.</span></span>
  
> [!NOTE]
> <span data-ttu-id="65749-p111">Ja, dies ist erforderlich, zusätzliche Schritte zum als Ihr Benutzerkonto alltägliche abmelden und melden Sie sich mit einem dedizierten globale Administratorkonto ein. Aber dies nur gelegentlich für globaler Administrator Vorgänge ausgeführt werden soll. Erwägen Sie, Ihre Office 365-Abonnements wiederherstellen, nachdem eine globaler Administrator Konto Verletzung viel weitere Schritte erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="65749-p111">Yes, this requires additional steps to sign out as your everyday user account and sign in with a dedicated global administrator account. But this only needs to be done occasionally for global administrator operations. Consider that recovering your Office 365 subscription after a global administrator account breach requires a lot more steps.</span></span> 
  
## <a name="step-2-configure-multi-factor-authentication-for-your-dedicated-office-365-global-administrator-accounts-and-use-the-strongest-form-of-secondary-authentication"></a><span data-ttu-id="65749-p112">Schritt 2. Konfigurieren Sie mehrstufige Authentifizierung für Ihre dedizierten Office 365 globaler Administratorkonten und verwenden Sie die sicherste sekundäre Authentifizierung</span><span class="sxs-lookup"><span data-stu-id="65749-p112">Step 2. Configure multi-factor authentication for your dedicated Office 365 global administrator accounts and use the strongest form of secondary authentication</span></span>

<span data-ttu-id="65749-p113">Mehrstufige Authentifizierung (mehrstufiger Authentifizierung das) für Ihre globalen Administratorkonten benötigt zusätzliche Informationen über den Kontonamen und das Kennwort. Office 365 unterstützt die folgenden Überprüfungsmethoden:</span><span class="sxs-lookup"><span data-stu-id="65749-p113">Multi-factor authentication (MFA) for your global administrator accounts requires additional information beyond the account name and password. Office 365 supports these verification methods:</span></span>
  
- <span data-ttu-id="65749-149">Ein Telefonanruf</span><span class="sxs-lookup"><span data-stu-id="65749-149">A phone call</span></span>
    
- <span data-ttu-id="65749-150">Ein zufällig generierter Passcode</span><span class="sxs-lookup"><span data-stu-id="65749-150">A randomly generated pass code</span></span>
    
- <span data-ttu-id="65749-151">Eine Smartcard (virtuell oder physisch)</span><span class="sxs-lookup"><span data-stu-id="65749-151">A smart card (virtual or physical)</span></span>
    
- <span data-ttu-id="65749-152">Ein biometrisches Gerät</span><span class="sxs-lookup"><span data-stu-id="65749-152">A biometric device</span></span>
    
<span data-ttu-id="65749-153">Wenn Sie ein kleines Unternehmen, das mithilfe von Benutzerkonten in der Cloud (Identitätsmodell Cloud) gespeichert sind, verwenden Sie folgende Schritte aus, um mithilfe eines Telefonanrufs oder einen Text-Nachricht gesendet, um ein Smartphone Überprüfungscode mehrstufiger Authentifizierung das konfigurieren:</span><span class="sxs-lookup"><span data-stu-id="65749-153">If you are a small business that is using user accounts stored only in the cloud (the cloud identity model), use these steps to configure MFA using a phone call or a text message verification code sent to a smart phone:</span></span>
  
1. <span data-ttu-id="65749-154">[Mehrstufiger Authentifizierung das Aktivieren](https://support.office.com/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6).</span><span class="sxs-lookup"><span data-stu-id="65749-154">[Enable MFA](https://support.office.com/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6).</span></span>
    
2. <span data-ttu-id="65749-155">[Einrichten der Überprüfung für Office 365 – Schritt 2](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14) zum Konfigurieren der einzelnen dediziert globale Administratorkonto ein Telefonanruf oder Textnachricht als die Überprüfungsmethode.</span><span class="sxs-lookup"><span data-stu-id="65749-155">[Set up 2-step verification for Office 365](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14) to configure each dedicated global administrator account for phone call or text message as the verification method.</span></span> 
    
<span data-ttu-id="65749-p114">Wenn Sie einer größeren Organisation, die ein Office 365-Identität Hybridmodell verwendet wird sind, müssen Sie weitere Überprüfungsoptionen für die. Wenn Sie die Sicherheitsinfrastruktur für sekundäre stärkere Authentifizierungsmethode vorhanden, verwenden Sie folgende Schritte aus:</span><span class="sxs-lookup"><span data-stu-id="65749-p114">If you are a larger organization that is using an Office 365 hybrid identity model, you have more verification options. If you have the security infrastructure already in place for a stronger secondary authentication method, use these steps:</span></span>
  
1. <span data-ttu-id="65749-158">[Mehrstufiger Authentifizierung das Aktivieren](https://support.office.com/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6).</span><span class="sxs-lookup"><span data-stu-id="65749-158">[Enable MFA](https://support.office.com/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6).</span></span>
    
2. <span data-ttu-id="65749-159">[Einrichten der Überprüfung für Office 365 – Schritt 2](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14) zum Konfigurieren der einzelnen dediziert globalen Administratorkonto für die entsprechenden Überprüfungsmethode.</span><span class="sxs-lookup"><span data-stu-id="65749-159">[Set up 2-step verification for Office 365](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14) to configure each dedicated global administrator account for the appropriate verification method.</span></span> 
    
<span data-ttu-id="65749-p115">Wenn die Sicherheitsinfrastruktur für die gewünschte stärkere Überprüfungsmethode nicht und Funktionsweise von Office 365 mehrstufiger Authentifizierung das ist, wird dringend empfohlen, Sie dedizierte globale Administratorkonten mit mehrstufiger Authentifizierung das Konfigurieren mithilfe eines Telefongesprächs oder einer Textnachricht Überprüfungscode an einem Smartphone für Ihre globalen Administratorkonten als Sicherheitsmaßnahme vorläufige gesendet. Lassen Sie Ihre dedizierten globalen Administratorkonten nicht ohne zusätzliche Schutz von mehrstufiger Authentifizierung das bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="65749-p115">If the security infrastructure for the desired stronger verification method is not in place and functioning for Office 365 MFA, we strongly recommend that you configure dedicated global administrator accounts with MFA using a phone call or a text message verification code sent to a smart phone for your global administrator accounts as an interim security measure. Do not leave your dedicated global administrator accounts without the additional protection provided by MFA.</span></span>
  
<span data-ttu-id="65749-162">Weitere Informationen finden Sie unter [Planen der mehrstufigen Authentifizierung für Office 365-Bereitstellungen](https://support.office.com/article/043807b2-21db-4d5c-b430-c8a6dee0e6ba).</span><span class="sxs-lookup"><span data-stu-id="65749-162">For more information, see [Plan for multi-factor authentication for Office 365 Deployments](https://support.office.com/article/043807b2-21db-4d5c-b430-c8a6dee0e6ba).</span></span>
  
<span data-ttu-id="65749-163">Zum Verbinden mit Office 365-Diensten mit mehrstufiger Authentifizierung das und PowerShell finden Sie unter [in diesem Artikel](https://blogs.technet.microsoft.com/solutions_advisory_board/2017/04/27/connect-to-office-365-services-with-multifactor-authentication-mfa-and-powershell/).</span><span class="sxs-lookup"><span data-stu-id="65749-163">To connect to Office 365 services with MFA and PowerShell, see [this article](https://blogs.technet.microsoft.com/solutions_advisory_board/2017/04/27/connect-to-office-365-services-with-multifactor-authentication-mfa-and-powershell/).</span></span>
  
## <a name="step-3-monitor-for-suspicious-global-administrator-account-activity"></a><span data-ttu-id="65749-p116">Schritt 3. Monitor für Kontoaktivitäten verdächtigen globaler administrator</span><span class="sxs-lookup"><span data-stu-id="65749-p116">Step 3. Monitor for suspicious global administrator account activity</span></span>

<span data-ttu-id="65749-p117">Office 365-Cloud-App-Sicherheit können Sie die Richtlinien erstellen, um Sie verdächtige Verhalten, das im Rahmen Ihres Abonnements zu benachrichtigen. Cloud App-Sicherheit in Office 365 E5 integriert ist, aber es ist auch als separater Dienst verfügbar. Wenn Sie nicht über Office 365 E5 verfügen, können Sie beispielsweise einzelne Cloud App-Sicherheit Lizenzen für die Benutzerkonten erwerben, die die globaler Administrator Sicherheitsadministrator und Compliance-Administratorrollen zugewiesen sind.</span><span class="sxs-lookup"><span data-stu-id="65749-p117">Office 365 Cloud App Security lets you create policies to notify you of suspicious behavior in your subscription. Cloud App Security is built into Office 365 E5, but is also available as a separate service. For example, if you do not have Office 365 E5, you can purchase individual Cloud App Security licenses for the user accounts that are assigned the global administrator, security administrator, and compliance administrator roles.</span></span>
  
<span data-ttu-id="65749-169">Wenn Sie Cloud App-Sicherheit in Office 365-Abonnement haben, verwenden Sie folgende Schritte aus:</span><span class="sxs-lookup"><span data-stu-id="65749-169">If you have Cloud App Security in your Office 365 subscription, use these steps:</span></span>
  
1. <span data-ttu-id="65749-170">Melden Sie sich bei Office 365-Portal mit einem Konto an, die Rolle des Security-Administrator oder Compliance-Administrator zugewiesen ist.</span><span class="sxs-lookup"><span data-stu-id="65749-170">Sign into the Office 365 portal with an account that is assigned the Security Administrator or Compliance Administrator role.</span></span>
    
2. <span data-ttu-id="65749-171">[Sicherheit in Office 365-Cloud-App zu aktivieren](https://support.office.com/article/ba919c73-d021-404d-9850-eec57e78678c).</span><span class="sxs-lookup"><span data-stu-id="65749-171">[Turn on Office 365 Cloud App Security](https://support.office.com/article/ba919c73-d021-404d-9850-eec57e78678c).</span></span>
    
3. <span data-ttu-id="65749-172">Überprüfen Sie Ihre [Anomalie Erkennungsrichtlinien in Office 365-Cloud-App-Sicherheit](https://support.office.com/article/88935b4e-dcb1-47f1-8aca-1bf8fb069db6) Sie per e-Mail abweichenden Muster privilegierten administrative Aktivität benachrichtigt.</span><span class="sxs-lookup"><span data-stu-id="65749-172">Review your [Anomaly detection policies in Office 365 Cloud App Security](https://support.office.com/article/88935b4e-dcb1-47f1-8aca-1bf8fb069db6) to notify you by email of anomalous patterns of privileged administrative activity.</span></span> 
    
<span data-ttu-id="65749-173">Um ein Benutzerkonto hinzuzufügen, die Sicherheitsadministrator-Rolle, die mit einem dedizierten globalen Administratorkonto und mehrstufiger Authentifizierung das [Office 365 PowerShell eine Verbindung herstellen](https://technet.microsoft.com/library/dn975125.aspx#step3) , geben Sie den Benutzerprinzipalnamen des Benutzerkontos, und führen Sie diese Befehle:</span><span class="sxs-lookup"><span data-stu-id="65749-173">To add a user account to the Security Administrator role, [connect to Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx#step3) with a dedicated global administrator account and MFA, fill in the user principal name of the user account, and then run these commands:</span></span> 
  
```
$upn="<User principal name of the account>"
Add-MsolRoleMember -RoleMemberEmailAddress $upn -RoleName "Security Administrator"
```

<span data-ttu-id="65749-174">Um die Compliance-Administratorrolle ein Benutzerkonto hinzuzufügen, geben Sie den Benutzerprinzipalnamen des Benutzerkontos, und führen Sie diese Befehle:</span><span class="sxs-lookup"><span data-stu-id="65749-174">To add a user account to the Compliance Administrator role, fill in the user principal name of the user account, and then run these commands:</span></span>
  
```
$upn="<User principal name of the account>"
Add-MsolRoleMember -RoleMemberEmailAddress  $upn -RoleName "Compliance Administrator"
```

## <a name="additional-protections-for-enterprise-organizations"></a><span data-ttu-id="65749-175">Zusätzliche Schutzebenen für Unternehmen</span><span class="sxs-lookup"><span data-stu-id="65749-175">Additional protections for enterprise organizations</span></span>

<span data-ttu-id="65749-176">Nachdem die Schritte 1 bis 3, um sicherzustellen, dass Ihre globale Administratorkonto ein, und die Konfiguration, die Sie ausführen, verwenden sie diese zusätzlichen Methoden verwenden, sind so sicher wie möglich.</span><span class="sxs-lookup"><span data-stu-id="65749-176">After steps 1-3, use these additional methods to ensure that your global administrator account, and the configuration that you perform using it, are as secure as possible.</span></span>
  
### <a name="privileged-access-workstation-paw"></a><span data-ttu-id="65749-177">Systemzugriff Arbeitsstation (KRALLE)</span><span class="sxs-lookup"><span data-stu-id="65749-177">Privileged Access Workstation (PAW)</span></span>

<span data-ttu-id="65749-p118">Um sicherzustellen, dass die Ausführung von umfangreichen Tasks so sicher wie möglich ist, verwenden Sie eine KRALLE. Eine KRALLE ist einem fest zugeordneten Computer, der nur für vertrauliche Konfigurationsaufgaben, wie etwa Office 365-Konfiguration verwendet wird, die ein globales Administratorkonto erforderlich sind. Da diese Computer nicht täglich für die Suche im Internet oder per e-Mail verwendet wird, ist es besser von Internetangriffen und Bedrohungen geschützt.</span><span class="sxs-lookup"><span data-stu-id="65749-p118">To ensure that the execution of highly privileged tasks is as secure as possible, use a PAW. A PAW is a dedicated computer that is only used for sensitive configuration tasks, such as Office 365 configuration that requires a global administrator account. Because this computer is not used daily for Internet browsing or email, it is better protected from Internet attacks and threats.</span></span>
  
<span data-ttu-id="65749-181">Informationen dazu, wie Sie eine KRALLE einrichten, finden Sie unter [http://aka.ms/cyberpaw](http://aka.ms/cyberpaw).</span><span class="sxs-lookup"><span data-stu-id="65749-181">For instructions on how to set up a PAW, see [http://aka.ms/cyberpaw](http://aka.ms/cyberpaw).</span></span>
  
### <a name="azure-ad-privileged-identity-management-pim"></a><span data-ttu-id="65749-182">Identitätsmanagement Azure AD-Berechtigungen (PIM)</span><span class="sxs-lookup"><span data-stu-id="65749-182">Azure AD Privileged Identity Management (PIM)</span></span>

<span data-ttu-id="65749-183">Azure AD PIM können Sie statt der globalen Administratorkonten dauerhaft die globalen Administratorrolle zugewiesen werden bei Bedarf, Just-in-Time-Zuweisung von der globalen Administratorrolle aktivieren, wenn es erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="65749-183">Rather than having your global administrator accounts be permanently assigned the global administrator role, you can use Azure AD PIM to enable on-demand, just-in-time assignment of the global administrator role when it is needed.</span></span>
  
<span data-ttu-id="65749-p119">Anstatt Ihre globalen Administratorkonten, wird eine permanente Admin werden sie zu auswählbaren Administratoren. Die globalen Administratorrolle ist inaktiv, bis jemand benötigen. Sie führen dann Aktivierungsprozess um das globale Administratorkonto die globalen Administratorrolle für einen festgelegten Zeitraum hinzuzufügen. Nach Ablauf die Zeit entfernt PIM die globalen Administratorrolle aus das globale Administratorkonto ein.</span><span class="sxs-lookup"><span data-stu-id="65749-p119">Instead of your global administrator accounts being a permanent admin, they become eligible administrators. The global administrator role is inactive until someone needs it. You then complete an activation process to add the global administrator role to the global administrator account for a predetermined amount of time. When the time expires, PIM removes the global administrator role from the global administrator account.</span></span>
  
<span data-ttu-id="65749-188">PIM verwenden und dabei erheblich verringert die Zeitdauer, die Ihre globalen Administratorkonten anfällig sind für Angriffe auf und Verwenden von böswilligen Benutzern.</span><span class="sxs-lookup"><span data-stu-id="65749-188">Using PIM and this process significantly reduces the amount of time that your global administrator accounts are vulnerable to attack and use by malicious users.</span></span>
  
<span data-ttu-id="65749-189">Weitere Informationen finden Sie unter [Konfigurieren von Azure AD privilegierten Identitätsmanagement](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure).</span><span class="sxs-lookup"><span data-stu-id="65749-189">For more information, see [Configure Azure AD Privileged Identity Management](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure).</span></span>
  
> [!NOTE]
> <span data-ttu-id="65749-190">PIM steht mit Azure Active Directory Premium P2, das mit Enterprise-Mobilität + E5 Sicherheit (zur Abstimmung) enthalten ist, oder Sie können einzelne Lizenzen erwerben, für Ihre globalen Administratorkonten.</span><span class="sxs-lookup"><span data-stu-id="65749-190">PIM is available with Azure Active Directory Premium P2, which is included with Enterprise Mobility + Security (EMS) E5, or you can purchase individual licenses for your global administrator accounts.</span></span> 
  
### <a name="security-information-and-event-management-siem-software-for-office-365-logging"></a><span data-ttu-id="65749-191">Sicherheit und Ereignissen (SIEM) Verwaltungssoftware für Office 365-Protokollierung</span><span class="sxs-lookup"><span data-stu-id="65749-191">Security information and event management (SIEM) software for Office 365 logging</span></span>

<span data-ttu-id="65749-p120">SIEM-Software auf einem Server ausführen Führt in Echtzeit Analyse der Sicherheitswarnungen und Ereignisse, die von Anwendungen und Netzwerkhardware erstellt. Damit Ihre SIEM Server Sicherheitshinweise für Office 365 und Ereignisse in der Analyse und Berichtsfunktionen enthalten kann, integrieren Sie diese in Ihrem System SIEM:</span><span class="sxs-lookup"><span data-stu-id="65749-p120">SIEM software run on a server performs real-time analysis of security alerts and events created by applications and network hardware. To allow your SIEM server to include Office 365 security alerts and events in its analysis and reporting functions, integrate these in your SIEM system:</span></span>
  
- <span data-ttu-id="65749-194">Azure AD</span><span class="sxs-lookup"><span data-stu-id="65749-194">Azure AD</span></span>
    
    <span data-ttu-id="65749-195">Weitere Informationen finden Sie unter [integrieren Protokolle von Azure Ressourcen in Ihre SIEM-Systeme](https://docs.microsoft.com/azure/security/security-azure-log-integration-overview).</span><span class="sxs-lookup"><span data-stu-id="65749-195">For more information, see [Integrate logs from Azure resources into your SIEM systems](https://docs.microsoft.com/azure/security/security-azure-log-integration-overview).</span></span>
    
- <span data-ttu-id="65749-196">Office 365 Cloud App Security</span><span class="sxs-lookup"><span data-stu-id="65749-196">Office 365 Cloud App Security</span></span>
    
    <span data-ttu-id="65749-197">Weitere Informationen finden Sie unter [Integrieren Ihrer SIEM Server mit Office 365-Cloud-App-Sicherheit](https://support.office.com/article/dd6d2417-49c4-4de6-9294-67fdabbf8532).</span><span class="sxs-lookup"><span data-stu-id="65749-197">For more information, see [Integrate your SIEM server with Office 365 Cloud App Security](https://support.office.com/article/dd6d2417-49c4-4de6-9294-67fdabbf8532).</span></span>
    
## <a name="next-step"></a><span data-ttu-id="65749-198">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="65749-198">Next step</span></span>

<span data-ttu-id="65749-199">Finden Sie unter [bewährte Methoden für Office 365-Sicherheit](https://support.office.com/article/9295e396-e53d-49b9-ae9b-0b5828cdedc3).</span><span class="sxs-lookup"><span data-stu-id="65749-199">See [Security best practices for Office 365](https://support.office.com/article/9295e396-e53d-49b9-ae9b-0b5828cdedc3).</span></span>
  

