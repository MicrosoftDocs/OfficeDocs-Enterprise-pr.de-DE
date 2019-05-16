---
title: Multi-Factor Authentication für die Office 365-Entwicklungs-/Testumgebung
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 02/20/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: e2b354b9-7f18-4da0-9107-6245eae0f33f
description: 'Zusammenfassung: Konfigurieren Sie Multi-Factor Authentication mithilfe von Textnachrichten, die an ein Smartphone in einer Office 365-Entwicklungs-/Testumgebung gesendet werden.'
ms.openlocfilehash: 2c53d7fa9239395e28d68487dd0ccea8cc57efb7
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "34069951"
---
# <a name="multi-factor-authentication-for-your-office-365-devtest-environment"></a><span data-ttu-id="776f5-103">Multi-Factor Authentication für die Office 365-Entwicklungs-/Testumgebung</span><span class="sxs-lookup"><span data-stu-id="776f5-103">Multi-factor authentication for your Office 365 dev/test environment</span></span>

 <span data-ttu-id="776f5-104">**Zusammenfassung:** Konfigurieren Sie Multi-Factor Authentication mithilfe von Textnachrichten, die an ein Smartphone in einer Office 365-Entwicklungs-/Testumgebung gesendet werden.</span><span class="sxs-lookup"><span data-stu-id="776f5-104">**Summary:** Configure multi-factor authentication using text messages sent to a smart phone in an Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="776f5-105">Um eine zusätzliche Sicherheitsstufe für die Anmeldung bei Ihrem Office 365-Abonnement zu erhalten, können Sie die Azure Multi-Factor Authentication aktivieren, die mehr als nur einen Benutzernamen und ein Kennwort zur Authentifizierung eines Kontos erfordert.</span><span class="sxs-lookup"><span data-stu-id="776f5-105">For an additional level of security for signing in to your Office 365 subscription, you can enable Azure multi-factor authentication, which requires more than just a username and password to authenticate an account.</span></span> <span data-ttu-id="776f5-106">Mit Multi-Factor Authentication für Office 365 müssen Benutzer auf ihrem Smartphone einen Telefonanruf bestätigen, einen Verifizierungscode eingeben, der ihnen in einer Textnachricht zugesendet wurde, oder ein App-Kennwort auf ihrem Smartphone angeben, nachdem sie ihr Kennwort korrekt eingegeben haben.</span><span class="sxs-lookup"><span data-stu-id="776f5-106">With multi-factor authentication for Office 365, users are required to acknowledge a phone call, type a verification code sent in a text message, or specify an app password on their smart phones after correctly entering their passwords.</span></span> <span data-ttu-id="776f5-107">Eine Anmeldung ist nur möglich, nachdem diese zweite Authentifizierungsstufe passiert wurde.</span><span class="sxs-lookup"><span data-stu-id="776f5-107">They can sign in only after this second authentication factor has been satisfied.</span></span> 
  
<span data-ttu-id="776f5-108">In diesem Artikel wird beschrieben, wie die Authentifizierung auf Basis einer Textnachricht für ein bestimmtes Office 365-Konto aktiviert und getestet wird.</span><span class="sxs-lookup"><span data-stu-id="776f5-108">This article describes how to enable and test text message-based authentication for a specific Office 365 account.</span></span>
  
<span data-ttu-id="776f5-109">Es gibt zwei Phasen bei der Einrichtung von Multi-Factor Authentication für Office 365 in einer Entwicklungs-/Testumgebung:</span><span class="sxs-lookup"><span data-stu-id="776f5-109">There are two phases to setting up multi-factor authentication for Office 365 in a dev/test environment:</span></span>
  
1. <span data-ttu-id="776f5-110">Erstellen der Office 365-Entwicklungs-/Testumgebung</span><span class="sxs-lookup"><span data-stu-id="776f5-110">Create the Office 365 dev/test environment.</span></span>
    
2. <span data-ttu-id="776f5-111">Aktivieren und Testen von Multi-Factor Authentication für das Konto „Benutzer 2“</span><span class="sxs-lookup"><span data-stu-id="776f5-111">Enable and test multi-factor authentication for the User 2 account.</span></span>
    
> [!TIP]
> <span data-ttu-id="776f5-112">Klicken Sie [hier](http://aka.ms/catlgstack), um eine visuelle Darstellung aller Artikel im Stapel der Testumgebungsanleitungen in Office 365 zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="776f5-112">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the Office 365 Test Lab Guide stack.</span></span>
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a><span data-ttu-id="776f5-113">Phase 1: Erstellen einer einfachen oder simulierten Office 365-Unternehmensentwicklungs-/-testumgebung</span><span class="sxs-lookup"><span data-stu-id="776f5-113">Phase 1: Build out your lightweight or simulated enterprise Office 365 dev/test environment</span></span>

<span data-ttu-id="776f5-114">Wenn Sie die mehrstufige Authentifizierung mit den Mindestanforderungen einfach testen möchten, befolgen Sie die Anweisungen in den Phasen 2 und 3 von [Office 365 dev/Test Environment](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="776f5-114">If you just want to test multi-factor authentication in a lightweight way with the minimum requirements, follow the instructions in phases 2 and 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="776f5-115">Wenn Sie die mehrstufige Authentifizierung in einem simulierten Unternehmen testen möchten, befolgen Sie die Anweisungen unter [Dirsync für Ihre Office 365 dev/Test-Umgebung](dirsync-for-your-office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="776f5-115">If you want to test multi-factor authentication in a simulated enterprise, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="776f5-116">Das Testen der mehrstufigen Authentifizierung erfordert nicht die simulierte Enterprise-Entwicklungs-und Testumgebung, die ein simuliertes Intranet enthält, das mit dem Internet und der Verzeichnissynchronisierung für eine Active Directory-Domänendienste (AD DS) verbunden ist.</span><span class="sxs-lookup"><span data-stu-id="776f5-116">Testing multi-factor authentication does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for a Active Directory Domain Services (AD DS) forest.</span></span> <span data-ttu-id="776f5-117">Dies wird hier als Option bereitgestellt, damit Sie Multi-Factor Authentication testen und damit in einer Umgebung experimentieren können, die eine typische Organisation darstellt.</span><span class="sxs-lookup"><span data-stu-id="776f5-117">It is provided here as an option so that you can test multi-factor authentication and experiment with it in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-enable-and-test-multi-factor-authentication-for-the-user-2-account"></a><span data-ttu-id="776f5-118">Phase 2: Aktivieren und Testen von Multi-Factor Authentication für das Konto „Benutzer 2“</span><span class="sxs-lookup"><span data-stu-id="776f5-118">Phase 2: Enable and test multi-factor authentication for the User 2 account</span></span>

<span data-ttu-id="776f5-119">Aktivieren Sie Multi-Factor Authentication für das Konto „Benutzer 2“ mit den folgenden Schritten:</span><span class="sxs-lookup"><span data-stu-id="776f5-119">Enable multi-factor authentication for the User 2 account with these steps:</span></span>
  
1. <span data-ttu-id="776f5-120">Öffnen Sie eine separate Instanz Ihres Browsers, wechseln Sie zum Office 365-Portal[https://www.office.com](https://www.office.com)(), und melden Sie sich dann mit ihrem globalen Administratorkonto bei Ihrem Office 365-Testabonnement an.</span><span class="sxs-lookup"><span data-stu-id="776f5-120">Open a separate instance of your browser, go to the Office 365 portal ([https://www.office.com](https://www.office.com)), and then sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
2. <span data-ttu-id="776f5-121">Klicken Sie auf der Hauptportalseite auf **Admin**.</span><span class="sxs-lookup"><span data-stu-id="776f5-121">From the main portal page, click **Admin**.</span></span>
    
3. <span data-ttu-id="776f5-122">Klicken Sie im linken Navigationsbereich auf **Benutzer > Aktive Benutzer**.</span><span class="sxs-lookup"><span data-stu-id="776f5-122">In the left navigation, click **Users > Active users**.</span></span>
    
4. <span data-ttu-id="776f5-123">Klicken Sie im Bereich aktive Benutzer auf **Weitere >-Setup**für mehrstufige Authentifizierung.</span><span class="sxs-lookup"><span data-stu-id="776f5-123">In the Active users pane, click **More > Multi-factor authentication setup**.</span></span>
    
5. <span data-ttu-id="776f5-124">Wählen Sie in der Liste das Konto **Benutzer 2** aus.</span><span class="sxs-lookup"><span data-stu-id="776f5-124">In the list, select the **User 2** account.</span></span>
    
6. <span data-ttu-id="776f5-125">Klicken Sie im Abschnitt **Benutzer 2** unter **QuickSteps** auf **Aktivieren**.</span><span class="sxs-lookup"><span data-stu-id="776f5-125">In the **User 2** section, under **Quick steps**, click **Enable**.</span></span>
    
7. <span data-ttu-id="776f5-126">Klicken Sie im Dialogfeld **Informationen zum Aktivieren von mehrstufiger Aktualisierung** auf **Multi-Factor Authentication aktivieren**.</span><span class="sxs-lookup"><span data-stu-id="776f5-126">In the **About enabling multi-factor auth** dialog box, click **Enable multi-factor auth**.</span></span>
    
8. <span data-ttu-id="776f5-127">Klicken Sie im Dialogfeld **erfolgreiche Updates** auf **Beenden**.</span><span class="sxs-lookup"><span data-stu-id="776f5-127">In the **Updates successful** dialog box, click **Close**.</span></span>
    
9. <span data-ttu-id="776f5-128">Klicken Sie auf der Registerkarte **Microsoft Office-Starts** auf das Benutzerkontosymbol in der oberen rechten Ecke, und klicken Sie dann auf **Abmelden**.</span><span class="sxs-lookup"><span data-stu-id="776f5-128">On the **Microsoft Office Home** tab, click the user account icon in the upper right, and then click **Sign out**.</span></span>
    
10. <span data-ttu-id="776f5-129">Schließen Sie Ihre Browserinstanz.</span><span class="sxs-lookup"><span data-stu-id="776f5-129">Close your browser instance.</span></span>
    
<span data-ttu-id="776f5-130">Schließen Sie die Konfiguration des Kontos „Benutzer 2“ für die Verwendung einer Textnachricht zur Prüfung ab, und testen Sie es mit den folgenden Schritten:</span><span class="sxs-lookup"><span data-stu-id="776f5-130">Complete the configuration for the User 2 account to use a text message for validation and test it with these steps:</span></span>
  
1. <span data-ttu-id="776f5-131">Öffnen Sie eine neue Instanz Ihres Browsers.</span><span class="sxs-lookup"><span data-stu-id="776f5-131">Open a new instance of your browser.</span></span>
    
2. <span data-ttu-id="776f5-132">Wechseln Sie zum Office 365-Portal[https://www.office.com](https://www.office.com)(), und melden Sie sich mit dem Konto "Benutzer\<2" (User2 @ Organization name>. onmicrosoft. com) und Kennwort an.</span><span class="sxs-lookup"><span data-stu-id="776f5-132">Go to the Office 365 portal ([https://www.office.com](https://www.office.com)) and sign in with the User 2 account (user2@\<organization name>.onmicrosoft.com) and password.</span></span>
    
3. <span data-ttu-id="776f5-p103">Nach der Anmeldung werden Sie aufgefordert, eine zusätzliche Sicherheitsüberprüfung für das Konto einzurichten. Klicken Sie auf **Jetzt einrichten**.</span><span class="sxs-lookup"><span data-stu-id="776f5-p103">After signing in, you are prompted to set up the account for additional security validation. Click **Set it up now**.</span></span>
    
4. <span data-ttu-id="776f5-135">Führen Sie auf der Seite **Zusätzliche Sicherheitsüberprüfung** die folgenden Schritte aus: </span><span class="sxs-lookup"><span data-stu-id="776f5-135">On the **Additional security verification** page:</span></span>
    
  - <span data-ttu-id="776f5-136">Wählen Sie Ihr Land oder Ihre Region aus.</span><span class="sxs-lookup"><span data-stu-id="776f5-136">Select your country or region.</span></span>
    
  - <span data-ttu-id="776f5-137">Geben Sie die Telefonnummer des Smartphones ein, das Textnachrichten erhalten soll.</span><span class="sxs-lookup"><span data-stu-id="776f5-137">Type phone number of the smart phone that will receive text messages.</span></span>
    
  - <span data-ttu-id="776f5-138">Klicken Sie in der **-Methode**auf **Code per Textnachricht senden**.</span><span class="sxs-lookup"><span data-stu-id="776f5-138">in **Method**, click **Send me a code by text message**.</span></span>
    
5. <span data-ttu-id="776f5-139">Klicken Sie auf **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="776f5-139">Click **Next**.</span></span>
    
6. <span data-ttu-id="776f5-140">Geben Sie den Verifizierungscode aus der Textnachricht ein, die an Ihr Smartphone gesendet wurde, und klicken Sie dann auf **Überprüfen**.</span><span class="sxs-lookup"><span data-stu-id="776f5-140">Enter the verification code from the text message received on your smart phone, and then click **Verify**.</span></span>
    
7. <span data-ttu-id="776f5-141">Zeichnen Sie das auf der Seite **Schritt 3: Keep your existing applications** angezeigte App-Kennwort für das Konto „Benutzer 2“ an einem sicheren Ort auf, und klicken Sie dann auf **Fertig**.</span><span class="sxs-lookup"><span data-stu-id="776f5-141">On the **Step 3: Keep your existing applications** page, record the displayed app password for the User 2 account in a secure location, and then click **Done**.</span></span>
    
8. <span data-ttu-id="776f5-p104">Wenn dies das erste Mal ist, dass Sie sich mit dem Konto „Benutzer 2“ angemeldet haben, werden Sie aufgefordert, das Kennwort zu ändern. Geben Sie das ursprüngliche Kennwort und dann zwei Mal ein neues Kennwort ein, und klicken Sie dann auf **Kennwort ändern und anmelden**. Zeichnen Sie das neue Kennwort an einem sicheren Ort auf.</span><span class="sxs-lookup"><span data-stu-id="776f5-p104">If this is the first time you signed in with the User 2 account, you are prompted to change the password. Type the original password and a new password twice, and then click **Update password and sign in**. Record the new password in a secure location.</span></span>
    
    <span data-ttu-id="776f5-145">Auf der Registerkarte **Microsoft Office Home** in Ihrem Browser sollte das Office 365-Portal für Benutzer 2 angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="776f5-145">You should see the Office 365 portal for User 2 on the **Microsoft Office Home** tab of your browser.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="776f5-146">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="776f5-146">See Also</span></span>

[<span data-ttu-id="776f5-147">Testumgebungsanleitungen (TLGs) zur Cloudakzeptanz</span><span class="sxs-lookup"><span data-stu-id="776f5-147">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="776f5-148">Basiskonfiguration der Entwicklungs-/Testumgebung</span><span class="sxs-lookup"><span data-stu-id="776f5-148">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="776f5-149">Office 365-Entwicklungs-/Testumgebung</span><span class="sxs-lookup"><span data-stu-id="776f5-149">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="776f5-150">Cloudakzeptanz und Hybridlösungen</span><span class="sxs-lookup"><span data-stu-id="776f5-150">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)

[<span data-ttu-id="776f5-151">Planen der mehrstufigen Authentifizierung für Office 365-Bereitstellungen</span><span class="sxs-lookup"><span data-stu-id="776f5-151">Plan for multi-factor authentication for Office 365 Deployments</span></span>](https://support.office.com/article/Plan-for-multi-factor-authentication-for-Office-365-Deployments-043807b2-21db-4d5c-b430-c8a6dee0e6ba)

