---
title: "Konfigurieren von Gruppen und Benutzern für eine politische Kampagne in einer Entwicklungs-/Testumgebung"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: None
ms.custom:
- DecEntMigration
- Strat_O365_Enterprise
ms.assetid: 0e22bcf3-bad3-42a4-b44f-276e0cf4790f
description: "Zusammenfassung: Erstellen Sie Office 365 und Enterprise-Mobilität + Testabonnements Sicherheit (zur Abstimmung) mit Benutzern und Gruppen für eine politischen Kampagne Test-/-Umgebung."
ms.openlocfilehash: 7faf428fc2225d3f31297ba6bf83a10a7682009a
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2017
---
# <a name="configure-groups-and-users-for-a-political-campaign-devtest-environment"></a><span data-ttu-id="89f68-103">Konfigurieren von Gruppen und Benutzern für eine politische Kampagne in einer Entwicklungs-/Testumgebung</span><span class="sxs-lookup"><span data-stu-id="89f68-103">Configure groups and users for a political campaign dev/test environment</span></span>

 <span data-ttu-id="89f68-104">**Zusammenfassung:** Erstellen von Office 365 und Enterprise-Mobilität + Testabonnements Sicherheit (zur Abstimmung) mit Benutzern und Gruppen für eine politischen Kampagne Test-/-Umgebung.</span><span class="sxs-lookup"><span data-stu-id="89f68-104">**Summary:** Create Office 365 and Enterprise Mobility + Security (EMS) trial subscriptions with users and groups for a political campaign dev/test environment.</span></span>
  
<span data-ttu-id="89f68-105">Verwenden Sie die Anweisungen in diesem Artikel, um einer Test-/Umgebung erstellen, die vereinfachte Benutzerkonten und Gruppen für die [Microsoft Security Guidance for politischen Kampagnen, gemeinnützige Organisationen, und andere Agile Organisationen](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md) -Lösung enthält.</span><span class="sxs-lookup"><span data-stu-id="89f68-105">Use the instructions in this article to create a dev/test environment that includes simplified user accounts and groups for the [Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md) solution.</span></span>
  
## <a name="phase-1-create-your-office-365-devtest-environment"></a><span data-ttu-id="89f68-106">Phase 1: Erstellen Ihrer Office 365-Entwicklungs-/Testumgebung</span><span class="sxs-lookup"><span data-stu-id="89f68-106">Phase 1: Create your Office 365 dev/test environment</span></span>

<span data-ttu-id="89f68-107">In dieser Phase erhalten Sie Testabonnements für Office 365 E5 und Enterprise-Mobilität + Sicherheit (zur Abstimmung) E5 für fiktive Organisation, die eine politische Kampagne darstellt.</span><span class="sxs-lookup"><span data-stu-id="89f68-107">In this phase, you obtain trial subscriptions for Office 365 E5 and Enterprise Mobility + Security (EMS) E5 for a fictional organization that represents a political campaign.</span></span>
  
<span data-ttu-id="89f68-108">Zuerst, befolgen Sie die Anweisungen in **Phase 2** der [Office 365 Dev/Test Environment](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="89f68-108">First, follow the instructions in **Phase 2** of the [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="89f68-109">Im nächsten Schritt für den Test zur Abstimmung E5-Abonnement registrieren und die derselben Organisation wie Test Office 365-Abonnement hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="89f68-109">Next, sign up for the EMS E5 trial subscription and add it to the same organization as your Office 365 trial subscription.</span></span>
  
1. <span data-ttu-id="89f68-p101">Falls erforderlich, melden Sie sich mit den Anmeldeinformationen des globalen Administratorkontos für Ihr Testabonnement beim Office 365-Portal an. Hilfe finden Sie unter [Wo kann ich mich bei Office 365 Business anmelden?](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="89f68-p101">If needed, sign in to the Office 365 portal with the credentials of the global administrator account of your trial subscription. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="89f68-112">Klicken Sie auf die Kachel **Admin**.</span><span class="sxs-lookup"><span data-stu-id="89f68-112">Click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="89f68-113">Klicken Sie auf der Registerkarte **Office Admin Center** in Ihrem Browser im linken Navigationsbereich auf **Abrechnung > Dienste kaufen**.</span><span class="sxs-lookup"><span data-stu-id="89f68-113">On the **Office Admin center** tab in your browser, in the left navigation, click **Billing > Purchase services**.</span></span>
    
4. <span data-ttu-id="89f68-p102">Suchen Sie auf der Seite **Dienste kaufen** den Artikel **Enterprise Mobility + Security E5**. Platzieren Sie den Mauszeiger auf dem Artikelnamen, und klicken Sie auf **Start free trial**.</span><span class="sxs-lookup"><span data-stu-id="89f68-p102">On the **Purchase services** page, find the **Enterprise Mobility + Security E5** item. Hover your mouse pointer over it and click **Start free trial**.</span></span>
    
5. <span data-ttu-id="89f68-116">Klicken Sie auf der Seite für die **Bestätigung Ihrer Bestellung** auf **Jetzt versuchen**.</span><span class="sxs-lookup"><span data-stu-id="89f68-116">On the **Confirm your order** page, click **Try now**.</span></span>
    
6. <span data-ttu-id="89f68-117">Klicken Sie auf der Seite **Bestellbestätigung** auf **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="89f68-117">On the **Order receipt** page, click **Continue**.</span></span>
    
<span data-ttu-id="89f68-118">Aktivieren Sie im nächsten Schritt die zur Abstimmung E5 Lizenz für das globale Administratorkonto ein.</span><span class="sxs-lookup"><span data-stu-id="89f68-118">Next, enable the EMS E5 license for your global administrator account.</span></span>
  
1. <span data-ttu-id="89f68-119">Klicken Sie auf der Registerkarte **Office 365 Admin Center** in Ihrem Browser im linken Navigationsbereich auf **Benutzer > Aktive Benutzer**.</span><span class="sxs-lookup"><span data-stu-id="89f68-119">On the **Office 365 Admin center** tab in your browser, in the left navigation, click **Users > Active users**.</span></span>
    
2. <span data-ttu-id="89f68-120">Klicken Sie auf Ihr globales Administratorkonto und dann auf **Bearbeiten**, um die **Produktlizenzen** anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="89f68-120">Click your global administrator account, and then click **Edit** for **Product licenses**.</span></span>
    
3. <span data-ttu-id="89f68-121">Setzen Sie im Bereich **Product licenses** die Produktlizenz für **Enterprise Mobility + Security E5** auf **On**. Klicken Sie auf **Speichern** und dann auf **Schließen**.</span><span class="sxs-lookup"><span data-stu-id="89f68-121">On the **Product licenses** pane, turn the product license for **Enterprise Mobility + Security E5** to **On**, click **Save,** and then click **Close** twice.</span></span>
    
## <a name="phase-2-create-and-configure-your-azure-active-directory-ad-groups"></a><span data-ttu-id="89f68-122">Phase 2: Erstellen und Konfigurieren der Azure Active Directory(AD)-Gruppen</span><span class="sxs-lookup"><span data-stu-id="89f68-122">Phase 2: Create and configure your Azure Active Directory (AD) groups</span></span>

<span data-ttu-id="89f68-123">In dieser Phase werden die Azure AD-Gruppen für Ihre Kampagne erstellt und konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="89f68-123">In this phase, you create and configure the Azure AD groups for your campaign.</span></span>
  
<span data-ttu-id="89f68-124">Erstellen Sie zunächst eine Reihe von Gruppen für eine typische politischen Kampagne mit dem Azure-Portal.</span><span class="sxs-lookup"><span data-stu-id="89f68-124">First, create a set of groups for a typical political campaign with the Azure portal.</span></span>
  
1. <span data-ttu-id="89f68-125">Fahren Sie auf einer separaten Registerkarte in Ihrem Browser mit der Azure-Portal unter [https://portal.azure.com](https://portal.azure.com). Bei Bedarf, melden Sie sich mit den Anmeldeinformationen des das globale Administratorkonto ein Test E5 für Office 365-Abonnement.</span><span class="sxs-lookup"><span data-stu-id="89f68-125">On a separate tab in your browser, go to the Azure portal at [https://portal.azure.com](https://portal.azure.com). If needed, sign in with the credentials of the global administrator account for your Office 365 E5 trial subscription.</span></span>
    
2. <span data-ttu-id="89f68-126">Klicken Sie im Azure-Portal auf **Azure Active Directory > Benutzer und Gruppen > Alle Gruppen**.</span><span class="sxs-lookup"><span data-stu-id="89f68-126">In the Azure portal, click **Azure Active Directory > Users and groups > All groups**.</span></span>
    
3. <span data-ttu-id="89f68-127">Führen Sie die folgenden Schritte für jede Gruppenname in dieser Liste aus:</span><span class="sxs-lookup"><span data-stu-id="89f68-127">Do the following steps for each group name in this list:</span></span>
    
  - <span data-ttu-id="89f68-128">Senior-Mitarbeiter und strategische Mitarbeiter</span><span class="sxs-lookup"><span data-stu-id="89f68-128">Senior and strategic staff</span></span>
    
  - <span data-ttu-id="89f68-129">IT-Mitarbeiter</span><span class="sxs-lookup"><span data-stu-id="89f68-129">IT staff</span></span>
    
  - <span data-ttu-id="89f68-130">Analytiker</span><span class="sxs-lookup"><span data-stu-id="89f68-130">Analytics staff</span></span>
    
  - <span data-ttu-id="89f68-131">Stammpersonal</span><span class="sxs-lookup"><span data-stu-id="89f68-131">Regular core staff</span></span>
    
  - <span data-ttu-id="89f68-132">Betriebspersonal</span><span class="sxs-lookup"><span data-stu-id="89f68-132">Operations staff</span></span>
    
  - <span data-ttu-id="89f68-133">Außendienstmitarbeiter</span><span class="sxs-lookup"><span data-stu-id="89f68-133">Field staff</span></span>
    
1. <span data-ttu-id="89f68-134">Klicken Sie auf dem Blatt **Alle Gruppen** auf **+ Neue Gruppe**.</span><span class="sxs-lookup"><span data-stu-id="89f68-134">On the **All groups** blade, click **+ New group**.</span></span>
    
2. <span data-ttu-id="89f68-135">Geben Sie im **Feld Name**den Namen der Gruppe aus der Liste.</span><span class="sxs-lookup"><span data-stu-id="89f68-135">Type the group name from the list in **Name**.</span></span>
    
3. <span data-ttu-id="89f68-136">Wählen Sie **dynamische Benutzer** , **Mitgliedschaft**in.</span><span class="sxs-lookup"><span data-stu-id="89f68-136">Select **Dynamic user** in **Membership**.</span></span>
    
4. <span data-ttu-id="89f68-137">Klicken Sie auf **Ja** für **Office-Features aktivieren**.</span><span class="sxs-lookup"><span data-stu-id="89f68-137">Click **Yes** for **Enable Office features**.</span></span>
    
5. <span data-ttu-id="89f68-138">Klicken Sie auf die **Dynamische Abfrage hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="89f68-138">Click **Add dynamic query**.</span></span>
    
6. <span data-ttu-id="89f68-139">In **Hinzufügen von Benutzern, in dem**, wählen Sie **Abteilung**.</span><span class="sxs-lookup"><span data-stu-id="89f68-139">In **Add users where**, select **department**.</span></span>
    
7. <span data-ttu-id="89f68-140">Wählen Sie im nächsten Feld **entspricht**.</span><span class="sxs-lookup"><span data-stu-id="89f68-140">In the next field, select **Equals**.</span></span>
    
8. <span data-ttu-id="89f68-141">Geben Sie im nächsten Feld den Namen der Gruppe aus der Liste aus.</span><span class="sxs-lookup"><span data-stu-id="89f68-141">In the next field, type the group name from the list.</span></span>
    
9. <span data-ttu-id="89f68-142">Klicken Sie auf **Abfrage hinzufügen**, und klicken Sie dann auf **Erstellen**.</span><span class="sxs-lookup"><span data-stu-id="89f68-142">Click **Add query**, and then click **Create**.</span></span>
    
10. <span data-ttu-id="89f68-143">Klicken Sie auf **Benutzer und Gruppen - alle Gruppen**.</span><span class="sxs-lookup"><span data-stu-id="89f68-143">Click **Users and groups - All groups**.</span></span>
    
<span data-ttu-id="89f68-144">Im nächsten Schritt konfigurieren Sie die Gruppen, sodass Elemente automatisch Office 365 E5 und zur Abstimmung E5 Lizenzen zugewiesen sind.</span><span class="sxs-lookup"><span data-stu-id="89f68-144">Next, you configure the groups so that members are automatically assigned Office 365 E5 and EMS E5 licenses.</span></span>
  
1. <span data-ttu-id="89f68-145">Klicken Sie im Azure-Portal auf **Azure Active Directory > Lizenzen > Alle Produkte**.</span><span class="sxs-lookup"><span data-stu-id="89f68-145">In the Azure portal, click **Azure Active Directory > Licenses > All products**.</span></span>
    
2. <span data-ttu-id="89f68-146">Wählen Sie in der Liste **Enterprise-Mobilität + Sicherheit E5** und **Office 365 Enterprise E5**, und klicken Sie dann auf **+ zuweisen**.</span><span class="sxs-lookup"><span data-stu-id="89f68-146">In the list, select **Enterprise Mobility + Security E5** and **Office 365 Enterprise E5**, and then click **+ Assign**.</span></span>
    
3. <span data-ttu-id="89f68-147">Klicken Sie auf dem Blatt **Lizenz zuweisen** auf **Benutzer und Gruppen**.</span><span class="sxs-lookup"><span data-stu-id="89f68-147">In the **Assign license** blade, click **Users and groups**.</span></span>
    
4. <span data-ttu-id="89f68-148">Wählen Sie in der Liste der Gruppen Folgendes aus:</span><span class="sxs-lookup"><span data-stu-id="89f68-148">In the list of groups, select the following:</span></span>
    
  - <span data-ttu-id="89f68-149">Analytiker</span><span class="sxs-lookup"><span data-stu-id="89f68-149">Analytics staff</span></span>
    
  - <span data-ttu-id="89f68-150">Außendienstmitarbeiter</span><span class="sxs-lookup"><span data-stu-id="89f68-150">Field staff</span></span>
    
  - <span data-ttu-id="89f68-151">IT-Mitarbeiter</span><span class="sxs-lookup"><span data-stu-id="89f68-151">IT staff</span></span>
    
  - <span data-ttu-id="89f68-152">Betriebspersonal</span><span class="sxs-lookup"><span data-stu-id="89f68-152">Operations staff</span></span>
    
  - <span data-ttu-id="89f68-153">Stammpersonal</span><span class="sxs-lookup"><span data-stu-id="89f68-153">Regular core staff</span></span>
    
  - <span data-ttu-id="89f68-154">Senior-Mitarbeiter und strategische Mitarbeiter</span><span class="sxs-lookup"><span data-stu-id="89f68-154">Senior and strategic staff</span></span>
    
5. <span data-ttu-id="89f68-155">Klicken Sie auf **Auswählen** und dann auf **Zuweisen**.</span><span class="sxs-lookup"><span data-stu-id="89f68-155">Click **Select**, and then click **Assign**.</span></span>
    
6. <span data-ttu-id="89f68-156">Schließen Sie die Registerkarte für das Azure Portal in Ihrem Browser.</span><span class="sxs-lookup"><span data-stu-id="89f68-156">Close the Azure portal tab in your browser.</span></span>
    
## <a name="phase-3-add-your-user-accounts"></a><span data-ttu-id="89f68-157">Phase 3: Hinzufügen von Benutzerkonten</span><span class="sxs-lookup"><span data-stu-id="89f68-157">Phase 3: Add your user accounts</span></span>

<span data-ttu-id="89f68-158">In dieser Phase werden beispielhafte Benutzerkonten für Ihre politische Kampagne hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="89f68-158">In this phase, you add the example user accounts for your political campaign.</span></span>
  
<span data-ttu-id="89f68-159">Erstens Sie [Verbinden mit dem Azure Active Directory V2 PowerShell-Modul](https://go.microsoft.com/fwlink/?linkid=842218).</span><span class="sxs-lookup"><span data-stu-id="89f68-159">First, you [Connect with the Azure Active Directory V2 PowerShell module](https://go.microsoft.com/fwlink/?linkid=842218).</span></span>
  
<span data-ttu-id="89f68-160">Geben Sie anschließend den Namen Ihrer Organisation, Ihren Standort und ein gemeinsames Kennwort ein, und führen Sie dann die folgenden Befehle an der PowerShell-Eingabeaufforderung oder in der ISE-Umgebung ein (Integrated Script Environment) aus:</span><span class="sxs-lookup"><span data-stu-id="89f68-160">Next, you fill in your organization name, your location, and a common password, and then run these commands from the PowerShell command prompt or Integrated Script Environment (ISE):</span></span>
  
```
$orgName="<organization name, such as contoso for the contoso.onmicrosoft.com trial subscription domain name>"
$location="<the ISO ALPHA2 country code, such as US for the United States>"
$commonPassword="<common password for all the new accounts>"

$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password=$commonPassword

$deptName="Senior and strategic staff"
$userNames=@("Candidate","ChiefOfStaff","Strategic1") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="IT staff"
$userNames=@("ITAdmin1","ITAdmin2") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="Analytics staff"
$userNames=@("DataScientist1") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="Regular core staff"
$userNames=@("Regular1","Regular2") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="Operations staff"
$userNames=@("Operations1") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="Field staff"
$userNames=@("FieldConsultant1") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }

```

> [!IMPORTANT]
> <span data-ttu-id="89f68-p103">Hier eine allgemeine Kennwort werden für die Automatisierung und Erleichterung der Konfiguration für eine Test-/-Umgebung. Dies ist nicht für Produktion Abonnements empfohlen. Wie Sie sich jedes dieser Benutzerkonten für neue anmelden, werden Sie aufgefordert, das Kennwort zu ändern.</span><span class="sxs-lookup"><span data-stu-id="89f68-p103">The use of a common password here is for automation and ease of configuration for a dev/test environment. This is not recommended for production subscriptions. As you sign in with each of these new user accounts, you will be prompted to change the password.</span></span> 
  
<span data-ttu-id="89f68-164">Gehen Sie folgendermaßen vor, um sicherzustellen, dass die dynamische Gruppenmitgliedschaft und gruppenbasierte Lizenzierung ordnungsgemäß funktionieren.</span><span class="sxs-lookup"><span data-stu-id="89f68-164">Use these steps to verify that dynamic group membership and group-based licensing are working correctly.</span></span>
  
1. <span data-ttu-id="89f68-165">Klicken Sie auf der Registerkarte **Microsoft Office Home** in Ihrem Browser auf die Kachel **Admin**.</span><span class="sxs-lookup"><span data-stu-id="89f68-165">From the **Microsoft Office Home** tab of your browser, click the **Admin** tile.</span></span>
    
2. <span data-ttu-id="89f68-166">Klicken Sie auf der Registerkarte **Office Admin Center** im Browser auf **Benutzer**.</span><span class="sxs-lookup"><span data-stu-id="89f68-166">From the new **Office Admin center** tab of your browser, click **Users**.</span></span>
    
3. <span data-ttu-id="89f68-167">Klicken Sie in der Liste der Benutzer auf **Candidate**.</span><span class="sxs-lookup"><span data-stu-id="89f68-167">In the list of users, click **Candidate**.</span></span>
    
4. <span data-ttu-id="89f68-168">Überprüfen Sie im Bereich, in der die Eigenschaften des Benutzerkontos **Candidate** aufgelistet, die aus:</span><span class="sxs-lookup"><span data-stu-id="89f68-168">In the pane that lists the properties of the **Candidate** user account, verify that:</span></span>
    
  - <span data-ttu-id="89f68-169">Es ist ein Mitglied der Gruppe **Senior und strategische Mitarbeiter** (im **Gruppenmitgliedschaften**).</span><span class="sxs-lookup"><span data-stu-id="89f68-169">It is a member of the **Senior and strategic staff** group (in **Group memberships**).</span></span>
    
  - <span data-ttu-id="89f68-170">Es wurde die **Mobilität in Unternehmen + Sicherheit E5** und **Office 365 Enterprise E5** Lizenzen (in **Lizenzen**) zugewiesen.</span><span class="sxs-lookup"><span data-stu-id="89f68-170">It has been assigned the **Enterprise Mobility + Security E5** and **Office 365 Enterprise E5** licenses (in **Product licenses**).</span></span>
    
5. <span data-ttu-id="89f68-171">Schließen Sie den Bereich **Candidate** Benutzer Konto.</span><span class="sxs-lookup"><span data-stu-id="89f68-171">Close the **Candidate** user account pane.</span></span>
    
## <a name="record-values-for-future-reference"></a><span data-ttu-id="89f68-172">Notieren von Werten für zukünftige Verwendung</span><span class="sxs-lookup"><span data-stu-id="89f68-172">Record values for future reference</span></span>

<span data-ttu-id="89f68-173">Notieren Sie diese Werte für die Arbeit mit Office 365- und EMS-Testabonnements für diese Entwicklung-/Testumgebung:</span><span class="sxs-lookup"><span data-stu-id="89f68-173">Record these values for working with the Office 365 and EMS trial subscriptions for this dev/test environment:</span></span>
  
- <span data-ttu-id="89f68-174">Organisationsname für das Testabonnement: _______________________________________________ </span><span class="sxs-lookup"><span data-stu-id="89f68-174">Your trial subscription organization name: _______________________________________________</span></span> 
    
    <span data-ttu-id="89f68-175">Für den Domänennamen contoso.onmicrosoft.com des Testabonnements lautet der Name der Organisation zum Beispiel „contoso“.</span><span class="sxs-lookup"><span data-stu-id="89f68-175">For example, for the trial subscription domain name of contoso.onmicrosoft.com, the organization name is "contoso".</span></span>
    
- <span data-ttu-id="89f68-176">Der Name der Office 365 globaler Administrator: ___.onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="89f68-176">The Office 365 global administrator name: ____________________________________.onmicrosoft.com</span></span>
    
    <span data-ttu-id="89f68-177">Notieren Sie das Kennwort für dieses Konto und das allgemeine anfängliche Kennwort für die anderen Benutzerkonten an einem sicheren Ort.</span><span class="sxs-lookup"><span data-stu-id="89f68-177">Record the password for this account and the common initial password for the other user accounts in a secure location.</span></span>
    
## <a name="next-step"></a><span data-ttu-id="89f68-178">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="89f68-178">Next step</span></span>

<span data-ttu-id="89f68-179">Erstellen Sie die vier verschiedenen Typen von SharePoint Online Teamwebsites in dieser Umgebung Test-/und [Teamwebsites in einer politischen Kampagne Test-/Umgebung erstellen](create-team-sites-in-a-political-campaign-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="89f68-179">Build the four different types of SharePoint Online team sites in this dev/test environment with [Create team sites in a political campaign dev/test environment](create-team-sites-in-a-political-campaign-dev-test-environment.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="89f68-180">See Also</span><span class="sxs-lookup"><span data-stu-id="89f68-180">See Also</span></span>

[<span data-ttu-id="89f68-181">Microsoft-Sicherheitsleitfaden für politische Kampagnen, gemeinnützigen Organisationen und andere agile Organisationen</span><span class="sxs-lookup"><span data-stu-id="89f68-181">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[<span data-ttu-id="89f68-182">Erstellen von Teamwebsites in einer politischen Kampagne Test-/-Umgebung</span><span class="sxs-lookup"><span data-stu-id="89f68-182">Create team sites in a political campaign dev/test environment</span></span>](create-team-sites-in-a-political-campaign-dev-test-environment.md)
  
[<span data-ttu-id="89f68-183">Testumgebungsanleitungen (TLGs) zur Cloudakzeptanz</span><span class="sxs-lookup"><span data-stu-id="89f68-183">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="89f68-184">Cloudakzeptanz und Hybridlösungen</span><span class="sxs-lookup"><span data-stu-id="89f68-184">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)




