---
title: Cloud App Security für Ihre Office 365-Entwicklungs-/Testumgebung
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/05/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: 22248f2f-b370-435e-b6ac-0ae0cae36b96
description: 'Zusammenfassung: Konfigurieren und Demonstrieren von Office 365 Cloud App Security in der Office 365-Entwicklungs-/Testumgebung'
ms.openlocfilehash: aa6fada78ada2f97242ffe8f60c9032d618f3b9b
ms.sourcegitcommit: 682b180061dc63cd602bee567d5414eae6942572
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2019
ms.locfileid: "31741261"
---
# <a name="cloud-app-security-for-your-office-365-devtest-environment"></a><span data-ttu-id="2db7b-103">Cloud App Security für Ihre Office 365-Entwicklungs-/Testumgebung</span><span class="sxs-lookup"><span data-stu-id="2db7b-103">Cloud App Security for your Office 365 dev/test environment</span></span>

 <span data-ttu-id="2db7b-104">**Zusammenfassung:** Konfigurieren und Demonstrieren von Office 365 Cloud App Security in der Office 365-Entwicklungs-/Testumgebung</span><span class="sxs-lookup"><span data-stu-id="2db7b-104">**Summary:** Configure and demonstrate Office 365 Cloud App Security in your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="2db7b-105">Office 365 Cloud App Security, bisher bekannt als Office 365 Advanced Security Management, ermöglicht Ihnen das Erstellen von Richtlinien, mit denen Sie verdächtige Aktivitäten in Ihrem Office 365-Abonnement überwachen und darüber informiert werden, damit Sie untersuchen und mögliche Korrekturen durchführen können. Aktion.</span><span class="sxs-lookup"><span data-stu-id="2db7b-105">Office 365 Cloud App Security, previously known as Office 365 Advanced Security Management, lets you create policies that monitor for and inform you of suspicious activities in your Office 365 subscription, so that you can investigate and take possible remediation action.</span></span> <span data-ttu-id="2db7b-106">Weitere Informationen finden Sie unter [Overview of Cloud App Security in Office 365](https://support.office.com/article/Overview-of-Advanced-Security-Management-in-Office-365-81f0ee9a-9645-45ab-ba56-de9cbccab475).</span><span class="sxs-lookup"><span data-stu-id="2db7b-106">For more information, see [Overview of Cloud App Security in Office 365](https://support.office.com/article/Overview-of-Advanced-Security-Management-in-Office-365-81f0ee9a-9645-45ab-ba56-de9cbccab475).</span></span>
  
<span data-ttu-id="2db7b-107">Mit den Anweisungen in diesem Artikel aktivieren und testen Sie Cloud App Security in Ihrem Office 365-Testabonnement.</span><span class="sxs-lookup"><span data-stu-id="2db7b-107">With the instructions in this article, you enable and test Cloud App Security in your Office 365 trial subscription.</span></span>
  
> [!TIP]
> <span data-ttu-id="2db7b-108">Klicken Sie [hier](http://aka.ms/catlgstack) , um eine visuelle Darstellung aller Artikel im Office 365 Test Lab Guide-Stapel zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="2db7b-108">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the Office 365 Test Lab Guide stack.</span></span>
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a><span data-ttu-id="2db7b-109">Phase 1: Erstellen einer einfachen oder simulierten Office 365-Unternehmensentwicklungs-/-testumgebung</span><span class="sxs-lookup"><span data-stu-id="2db7b-109">Phase 1: Build out your lightweight or simulated enterprise Office 365 dev/test environment</span></span>

<span data-ttu-id="2db7b-110">Wenn Sie Cloud App Security nur auf einfache Weise mit den Mindestanforderungen testen möchten, befolgen Sie die Anweisungen in den Phasen 2 und 3 von [Office 365-Entwicklungs-/Testumgebung](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="2db7b-110">If you just want to test Cloud App Security in a lightweight way with the minimum requirements, follow the instructions in phases 2 and 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="2db7b-111">Wenn Sie Cloud App Security in einem simulierten Unternehmen testen möchten, führen Sie die Schritte in [DirSync für die Office 365-Entwicklungs-/Testumgebung](dirsync-for-your-office-365-dev-test-environment.md) aus.</span><span class="sxs-lookup"><span data-stu-id="2db7b-111">If you want to test Cloud App Security in a simulated enterprise, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="2db7b-112">Das Testen der Cloud-App-Sicherheit erfordert nicht die simulierte Enterprise-dev/Test-Umgebung, die ein simuliertes Intranet enthält, das mit dem Internet und der Verzeichnissynchronisierung für eine Active Directory-Domänendienste (AD DS) verbunden ist.</span><span class="sxs-lookup"><span data-stu-id="2db7b-112">Testing Cloud App Security does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for an Active Directory Domain Services (AD DS) forest.</span></span> <span data-ttu-id="2db7b-113">Dies wird hier als Option bereitgestellt, damit Sie Cloud App Security testen und damit in einer Umgebung, die eine typische Organisation darstellt, experimentieren können.</span><span class="sxs-lookup"><span data-stu-id="2db7b-113">It is provided here as an option so that you can test Cloud App Security and experiment with it in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-before-enabling-cloud-app-security-and-creating-a-policy"></a><span data-ttu-id="2db7b-114">Phase 2: Vor dem Aktivieren von Cloud App Security und Erstellen einer Richtlinie</span><span class="sxs-lookup"><span data-stu-id="2db7b-114">Phase 2: Before enabling Cloud App Security and creating a policy</span></span>

<span data-ttu-id="2db7b-115">In diesem Verfahren demonstrieren Sie, dass das Ändern einer Benutzerrolle vor dem Aktivieren von Cloud App Security keine E-Mail-Benachrichtigung an den globalen Administrator mit sich bringt.</span><span class="sxs-lookup"><span data-stu-id="2db7b-115">In this procedure, you demonstrate that before enabling Cloud App Security, changing a user's role provides no email notification to the global administrator.</span></span>
  
### <a name="test-the-default-notification-behavior-of-office-365"></a><span data-ttu-id="2db7b-116">Testen des Standardbenachrichtigungsverhaltens von Office 365</span><span class="sxs-lookup"><span data-stu-id="2db7b-116">Test the default notification behavior of Office 365</span></span>

1. <span data-ttu-id="2db7b-117">Wechseln Sie zum Microsoft 365 Admin Center ([https://admin.microsoft.com](https://admin.microsoft.com)), und melden Sie sich bei ihrem Office 365-Testabonnement mit ihrem globalen Administratorkonto an.</span><span class="sxs-lookup"><span data-stu-id="2db7b-117">Go to the Microsoft 365 admin center ([https://admin.microsoft.com](https://admin.microsoft.com)) and sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
  - <span data-ttu-id="2db7b-118">Wenn Sie die einfache Office 365-Entwicklungs-/Testumgebung verwenden, melden Sie sich von Ihrem lokalen Computer aus an.</span><span class="sxs-lookup"><span data-stu-id="2db7b-118">If you are using the lightweight Office 365 dev/test environment, sign in from your local computer.</span></span>
    
  - <span data-ttu-id="2db7b-119">Wenn Sie die simulierte Office 365-Unternehmensentwicklungs-/-testumgebung verwenden, verwenden Sie das [Azure-Portal](https://portal.azure.com), um sich mit dem virtuellen Computer CLIENT1 zu verbinden, und melden Sie sich dann von CLIENT1 aus an.</span><span class="sxs-lookup"><span data-stu-id="2db7b-119">If you are using the simulated enterprise Office 365 dev/test environment, use the [Azure portal](https://portal.azure.com) to connect to the CLIENT1 virtual machine, and then sign in from CLIENT1.</span></span>
    
2. <span data-ttu-id="2db7b-120">Klicken Sie auf der Hauptportalseite auf **Admin**.</span><span class="sxs-lookup"><span data-stu-id="2db7b-120">From the main portal page, click **Admin**.</span></span>
    
3. <span data-ttu-id="2db7b-121">Klicken Sie im linken Navigationsbereich auf **Benutzer > Aktive Benutzer**.</span><span class="sxs-lookup"><span data-stu-id="2db7b-121">In the left navigation, click **Users > Active users**.</span></span>
    
4. <span data-ttu-id="2db7b-122">Klicken Sie auf das Konto **Benutzer 4**.</span><span class="sxs-lookup"><span data-stu-id="2db7b-122">Click the **User 4** account.</span></span>
    
5. <span data-ttu-id="2db7b-123">Klicken Sie auf der Seite **Benutzer 4** auf **Bearbeiten** für die Zeile **Rollen**.</span><span class="sxs-lookup"><span data-stu-id="2db7b-123">On the **User 4** page, click **Edit** for the **Roles** row.</span></span>
    
6. <span data-ttu-id="2db7b-124">Klicken Sie auf der Seite **Benutzerrollen bearbeiten** auf **globaler Administrator**, **user4@contoso.com** geben Sie die **Alternative e-Mail-Adresse**ein, und klicken Sie dann auf **Speichern**.</span><span class="sxs-lookup"><span data-stu-id="2db7b-124">On the **Edit user roles** page, click **Global administrator**, type **user4@contoso.com** in the **Alternative email address**, and then click **Save**.</span></span> <span data-ttu-id="2db7b-125">Klicken Sie zweimal auf **Schließen**.</span><span class="sxs-lookup"><span data-stu-id="2db7b-125">Click **Close** twice.</span></span>
    
7. <span data-ttu-id="2db7b-126">Wählen Sie oben links das App-Startsymbol und dann **Admin** aus.</span><span class="sxs-lookup"><span data-stu-id="2db7b-126">Select the app launcher icon in the upper-left and choose **Mail**.</span></span>
    
8. <span data-ttu-id="2db7b-p104">Warten Sie 30 Minuten. Beachten Sie, dass es im Posteingang keine E-Mail-Nachricht gibt, die Sie über die Änderung der Rolle von Benutzers 4 als globaler Administrator informiert.</span><span class="sxs-lookup"><span data-stu-id="2db7b-p104">Wait 30 minutes. Notice that there is no email message in the inbox notifying you of the change in User 4's role as a global administrator.</span></span>
    
## <a name="phase-3-enable-cloud-app-security-and-create-a-policy"></a><span data-ttu-id="2db7b-129">Phase 3: Aktivieren von Cloud App Security und Erstellen einer Richtlinie</span><span class="sxs-lookup"><span data-stu-id="2db7b-129">Phase 3: Enable Cloud App Security and create a policy</span></span>

<span data-ttu-id="2db7b-p105">In diesem Verfahren aktivieren Sie Cloud App Security und erstellen eine neue Richtlinie zum Senden von E-Mail-Benachrichtigungen an Ihr globales Administratorkonto, wenn Änderungen an Benutzerkontorollen vorgenommen werden. Dieses Verfahren erfordert Folgendes:</span><span class="sxs-lookup"><span data-stu-id="2db7b-p105">In this procedure, you enable Cloud App Security and create a new policy to send email notifications to your global administrator account for changes in user account roles. This procedure requires:</span></span>
  
- <span data-ttu-id="2db7b-132">Der Kontoname des globalen Administrators und das Kennwort für Ihr Office 365-Testabonnement.</span><span class="sxs-lookup"><span data-stu-id="2db7b-132">The global administrator account name and password of your Office 365 trial subscription.</span></span>
    
- <span data-ttu-id="2db7b-133">Der Name und das Kennwort des Kontos von Benutzer 5 Ihres Office 365-Testabonnements.</span><span class="sxs-lookup"><span data-stu-id="2db7b-133">The name and password of the User 5 account of your Office 365 trial subscription.</span></span>
    
### <a name="enable-and-configure-cloud-app-security"></a><span data-ttu-id="2db7b-134">Aktivieren und Konfigurieren von Cloud App Security</span><span class="sxs-lookup"><span data-stu-id="2db7b-134">Enable and configure Cloud App Security</span></span>

1. <span data-ttu-id="2db7b-135">Wechseln Sie zum Microsoft 365 Admin Center ([https://admin.microsoft.com](https://admin.microsoft.com)), und melden Sie sich bei ihrem Office 365-Testabonnement mit ihrem globalen Administratorkonto an.</span><span class="sxs-lookup"><span data-stu-id="2db7b-135">Go to the Microsoft 365 admin center ([https://admin.microsoft.com](https://admin.microsoft.com)) and sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
2. <span data-ttu-id="2db7b-136">Klicken Sie auf die Kachel **Admin**.</span><span class="sxs-lookup"><span data-stu-id="2db7b-136">Click the **Admin** tile.</span></span> <span data-ttu-id="2db7b-137">Klicken Sie auf der Registerkarte **Office Admin Center** auf **Admin Center _GT_ Security & Compliance**.</span><span class="sxs-lookup"><span data-stu-id="2db7b-137">On the **Office Admin center** tab, click **Admin centers > Security & Compliance**.</span></span>
    
3. <span data-ttu-id="2db7b-138">Klicken Sie im linken Navigationsbereich auf **Warnungen > Erweiterte Warnungen verwalten**.</span><span class="sxs-lookup"><span data-stu-id="2db7b-138">In the left navigation pane, click **Alerts > Manage advanced alerts**.</span></span>
    
4. <span data-ttu-id="2db7b-139">Klicken Sie auf der Seite **Erweiterte Warnungen verwalten** auf **Office 365 Cloud App Security aktivieren**, und klicken Sie dann auf **Zu Office 365 Cloud App Security wechseln**.</span><span class="sxs-lookup"><span data-stu-id="2db7b-139">On the **Manage advanced alerts** page, click **Turn on Office 365 Cloud App Security**, and then click **Go to Office 365 Cloud App Security**.</span></span>
    
5. <span data-ttu-id="2db7b-140">Klicken Sie auf der neuen **Dashboard**-Registerkarte auf **Steuern > Richtlinien**.</span><span class="sxs-lookup"><span data-stu-id="2db7b-140">On the new **Dashboard** tab, click **Control > Policies**.</span></span>
    
6. <span data-ttu-id="2db7b-141">Klicken Sie auf der Seite **Richtlinie** auf **Richtlinie erstellen**, und klicken Sie dann auf **Aktivitätsrichtlinie**.</span><span class="sxs-lookup"><span data-stu-id="2db7b-141">On the **Policy** page, click **Create policy**, and then click **Activity policy**.</span></span>
    
7. <span data-ttu-id="2db7b-142">Geben Sie im Feld **Richtlinienname** den Namen **Administrative Aktivität** ein.</span><span class="sxs-lookup"><span data-stu-id="2db7b-142">In **Policy name**, type **Administrative activity**.</span></span>
    
8. <span data-ttu-id="2db7b-143">Klicken Sie unter **Schweregrad der Richtlinie** auf **Hoch**.</span><span class="sxs-lookup"><span data-stu-id="2db7b-143">In **Policy severity**, click **High**.</span></span>
    
9. <span data-ttu-id="2db7b-144">Klicken Sie unter **Kategorie** auf **Privilegierte Konten**.</span><span class="sxs-lookup"><span data-stu-id="2db7b-144">In **Category**, click **Privileged accounts**.</span></span>
    
10. <span data-ttu-id="2db7b-145">Klicken Sie in **Filter für die Richtlinie erstellen** unter **Aktivitäten entspricht allen folgenden Kriterien** auf **Administrative Aktivität**.</span><span class="sxs-lookup"><span data-stu-id="2db7b-145">In **Create filters for the policy**, in **Activities matching all of the following**, click **Administrative activity**.</span></span>
    
11. <span data-ttu-id="2db7b-p107">Klicken Sie unter **Benachrichtigungen** auf **Benachrichtigung als E-Mail senden**. Geben Sie unter **An** die E-Mail-Adresse Ihres globalen Administratorkontos ein.</span><span class="sxs-lookup"><span data-stu-id="2db7b-p107">In **Alerts**, click **Send alert as email**. In **To**, type the email address of your global administrator account.</span></span>
    
12. <span data-ttu-id="2db7b-148">Klicken Sie unten auf der Seite auf **Erstellen**.</span><span class="sxs-lookup"><span data-stu-id="2db7b-148">At the bottom of the page, click **Create**.</span></span>
    
## <a name="phase-4-show-cloud-app-security-in-action"></a><span data-ttu-id="2db7b-149">Phase 4: Vorführen von Cloud App Security in Aktion</span><span class="sxs-lookup"><span data-stu-id="2db7b-149">Phase 4: Show Cloud App Security in action</span></span>

<span data-ttu-id="2db7b-150">In diesem Verfahren demonstrieren Sie, wie Cloud App Security Warnungen erstellt und E-Mail-Benachrichtigungen an das globale Administratorkonto sendet, wenn Benutzer 4 Benutzer 5 als Kennwort- und Benutzerverwaltungsadministrator festlegt.</span><span class="sxs-lookup"><span data-stu-id="2db7b-150">In this procedure, you demonstrate how Cloud App Security creates alerts and sends email notifications to the global administrator account when User 4 makes User 5 a password and user management administrator.</span></span>
  
### <a name="demonstrate-email-notification-for-a-change-in-user-account-roles"></a><span data-ttu-id="2db7b-151">Demonstrieren der E-Mail-Benachrichtigung für eine Änderung an Benutzerkontorollen</span><span class="sxs-lookup"><span data-stu-id="2db7b-151">Demonstrate email notification for a change in user account roles</span></span>

1. <span data-ttu-id="2db7b-152">Klicken Sie oben rechts auf das Benutzersymbol, und klicken Sie dann auf **Abmelden**.</span><span class="sxs-lookup"><span data-stu-id="2db7b-152">In the upper-right, click the user icon, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="2db7b-153">Wechseln Sie zu [https://www.office.com](https://www.office.com).</span><span class="sxs-lookup"><span data-stu-id="2db7b-153">Go to [https://www.office.com](https://www.office.com).</span></span>
    
3. <span data-ttu-id="2db7b-154">Klicken Sie auf der Office 365-Anmeldeseite auf **Ein anderes Konto verwenden**.</span><span class="sxs-lookup"><span data-stu-id="2db7b-154">On the Office 365 sign in page, click **Use another account**.</span></span>
    
4. <span data-ttu-id="2db7b-155">Geben Sie den Benutzernamen und das Kennwort von Benutzer 4 ein, und klicken Sie dann auf **Anmelden**.</span><span class="sxs-lookup"><span data-stu-id="2db7b-155">Type the User 4 account name and its password, and then click **Sign in**.</span></span>
    
5. <span data-ttu-id="2db7b-156">Falls erforderlich, ändern Sie das Kennwort von Benutzers 4, und klicken Sie dann auf **Kennwort aktualisieren und anmelden**.</span><span class="sxs-lookup"><span data-stu-id="2db7b-156">If needed, change the User 4 account password, and then click **Update password and sign in**.</span></span>
    
6. <span data-ttu-id="2db7b-157">Klicken Sie auf der Office 365-Portalseite auf **Admin**.</span><span class="sxs-lookup"><span data-stu-id="2db7b-157">On the Office 365 portal page, click **Admin**.</span></span>
    
7. <span data-ttu-id="2db7b-158">Klicken Sie bei Bedarf auf **Abbrechen**, wenn Sie dazu aufgefordert, Ihre Administratorkontaktinformationen zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="2db7b-158">If needed, click **cancel** when prompted to update your admin contact info.</span></span>
    
8. <span data-ttu-id="2db7b-159">Klicken Sie auf der Hauptportalseite auf **Admin**.</span><span class="sxs-lookup"><span data-stu-id="2db7b-159">From the main portal page, click **Admin**.</span></span>
    
9. <span data-ttu-id="2db7b-160">Klicken Sie im linken Navigationsbereich auf **Benutzer > Aktive Benutzer**.</span><span class="sxs-lookup"><span data-stu-id="2db7b-160">In the left navigation, click **Users > Active users**.</span></span>
    
10. <span data-ttu-id="2db7b-161">Klicken Sie auf das Konto **Benutzer 5**.</span><span class="sxs-lookup"><span data-stu-id="2db7b-161">Click the **User 5** account.</span></span>
    
11. <span data-ttu-id="2db7b-162">Klicken Sie auf der Seite **Benutzer 5** auf **Bearbeiten** für die Zeile **Rollen**.</span><span class="sxs-lookup"><span data-stu-id="2db7b-162">On the **User 5** page, click **Edit** for the **Roles** row.</span></span>
    
12. <span data-ttu-id="2db7b-163">Klicken Sie auf der Seite **Benutzerrollen bearbeiten** auf **angepasster Administrator**, klicken Sie auf **Kennwort-Administrator** und **user5@contoso.com** **Benutzer Verwaltungs Administrator**, geben Sie die **Alternative e-Mail-Adresse**ein, und klicken Sie dann auf **Speichern**.</span><span class="sxs-lookup"><span data-stu-id="2db7b-163">On the **Edit user roles** page, click **Customized administrator**, click **Password administrator** and **User management administrator**, type **user5@contoso.com** in the **Alternative email address**, and then click **Save**.</span></span> <span data-ttu-id="2db7b-164">Klicken Sie zweimal auf **Schließen**.</span><span class="sxs-lookup"><span data-stu-id="2db7b-164">Click **Close** twice.</span></span>
    
13. <span data-ttu-id="2db7b-165">Klicken Sie oben rechts auf das Benutzersymbol, und klicken Sie dann auf **Abmelden**.</span><span class="sxs-lookup"><span data-stu-id="2db7b-165">Click the user icon in the upper-right, and then click **Sign out**.</span></span> 
    
14. <span data-ttu-id="2db7b-166">Wechseln Sie zu [https://www.office.com](https://www.office.com).</span><span class="sxs-lookup"><span data-stu-id="2db7b-166">Go to [https://www.office.com](https://www.office.com).</span></span>
    
15. <span data-ttu-id="2db7b-167">Klicken Sie auf der Seite **Office 365-Anmeldung** auf den Kontonamen Ihres globalen Administrators.</span><span class="sxs-lookup"><span data-stu-id="2db7b-167">On the **Office 365 sign in** page, click your global administrator account name.</span></span>
    
16. <span data-ttu-id="2db7b-168">Geben Sie das Kennwort ein, und klicken Sie dann auf **Anmelden**.</span><span class="sxs-lookup"><span data-stu-id="2db7b-168">Type the password, and then click **Sign in**.</span></span>
    
17. <span data-ttu-id="2db7b-169">Klicken Sie auf der Office 365-Portalseite auf **Admin**.</span><span class="sxs-lookup"><span data-stu-id="2db7b-169">From the Office 365 portal page, click **Admin**.</span></span>
    
18. <span data-ttu-id="2db7b-170">Klicken Sie auf die Kachel **Security &amp; Compliance**.</span><span class="sxs-lookup"><span data-stu-id="2db7b-170">Click the **Security &amp; Compliance** tile.</span></span>
    
19. <span data-ttu-id="2db7b-171">Klicken Sie im linken Navigationsbereich auf **Warnungen > Erweiterte Warnungen verwalten**.</span><span class="sxs-lookup"><span data-stu-id="2db7b-171">In the left navigation pane, click **Alerts > Manage advanced alerts**.</span></span>
    
20. <span data-ttu-id="2db7b-172">Klicken Sie auf der Seite **Erweiterte Warnungen verwalten** auf **Zu Office 365 Cloud App Security wechseln**.</span><span class="sxs-lookup"><span data-stu-id="2db7b-172">On the **Manage advanced alerts** page, click **Go to Office 365 Cloud App Security**.</span></span>
    
21. <span data-ttu-id="2db7b-173">Auf der neuen **Dashboard**-Registerkarte werden zwei neue Warnungen für **Administrative Aktivität** angezeigt.</span><span class="sxs-lookup"><span data-stu-id="2db7b-173">On the new **Dashboard** tab, notice the two new alerts for **Administrative activity**.</span></span>
    
22. <span data-ttu-id="2db7b-p109">Klicken Sie auf der Registerkarte der **Microsoft Office-Startseite** auf **Mail**. Warten Sie bis zu 30 Minuten.</span><span class="sxs-lookup"><span data-stu-id="2db7b-p109">From the **Microsoft Office Home** tab, click **Mail**. Wait up to 30 minutes.</span></span> 
    
    <span data-ttu-id="2db7b-p110">Im Posteingang sollten zwei neue E-Mail-Nachrichten mit dem Titel **Microsoft Azure AD-Benachrichtigungsdienst** angezeigt werden. Eine Nachricht besagt, dass das Konto von Benutzer 5 der Rolle **Kennwortadministrator** hinzugefügt wurde. Die andere Nachricht gibt an, dass das Konto von Benutzer 5 der Rolle **Benutzeradministrator** hinzugefügt wurde (entspricht der Rolle „Benutzerverwaltungsadministrator" im Office 365 Admin Center).</span><span class="sxs-lookup"><span data-stu-id="2db7b-p110">You should see two new email messages in the inbox with the title **Microsoft Azure AD Notification Service**. One message indicates that the User 5 account was added to the **Password Administrator** role and another message indicates that the User 5 account was added to the **User Administrator** role (equal to the User management administrator role in the Office 365 Admin center).</span></span>
    
<span data-ttu-id="2db7b-p111">Sie können diese Umgebung jetzt verwenden, um neue Richtlinien zu erstellen und weiter mit Office 365 Cloud App Security zu experimentieren. Unter [Erste Schritte mit Advanced Security Management](https://support.office.com/article/Get-ready-for-Office-365-Cloud-App-Security-d9ee4d67-f2b3-42b4-9c9e-c4529904990a) finden Sie Links zu zusätzlichen Konfigurationsartikeln.</span><span class="sxs-lookup"><span data-stu-id="2db7b-p111">You can now use this environment to create new policies and further experiment with Office 365 Cloud App Security. See [Get ready for Office 365 Cloud App Security](https://support.office.com/article/Get-ready-for-Office-365-Cloud-App-Security-d9ee4d67-f2b3-42b4-9c9e-c4529904990a) for links to additional configuration articles.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="2db7b-180">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="2db7b-180">See Also</span></span>

[<span data-ttu-id="2db7b-181">Testumgebungsanleitungen (TLGs) zur Cloudakzeptanz</span><span class="sxs-lookup"><span data-stu-id="2db7b-181">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="2db7b-182">Office 365-Entwicklungs-/Testumgebung</span><span class="sxs-lookup"><span data-stu-id="2db7b-182">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="2db7b-183">Cloudakzeptanz und Hybridlösungen</span><span class="sxs-lookup"><span data-stu-id="2db7b-183">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)

[<span data-ttu-id="2db7b-184">Übersicht über Cloud App Security in Office 365</span><span class="sxs-lookup"><span data-stu-id="2db7b-184">Overview of Cloud App Security in Office 365</span></span>](https://support.office.com/article/Overview-of-Advanced-Security-Management-in-Office-365-81f0ee9a-9645-45ab-ba56-de9cbccab475)


