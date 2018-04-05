---
title: Directory-Synchronisierung für Ihre Office 365 Dev/Test-Umgebung
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/04/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Strat_O365_Enterprise
- TLG
- Ent_TLGs
ms.assetid: e6b27e25-74ae-4b54-9421-c8e911aef543
description: 'Zusammenfassung: Konfigurieren der verzeichnissynchronisierung für Ihre Office 365 Dev/Test-Umgebung.'
ms.openlocfilehash: 1363e7fd6a3afdbec85fd08790268ab186badbc8
ms.sourcegitcommit: 21cc62118b78b76d16ef12e2c3eff2c0c789e3d0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/05/2018
---
# <a name="directory-synchronization-for-your-office-365-devtest-environment"></a><span data-ttu-id="73cfe-103">Directory-Synchronisierung für Ihre Office 365 Dev/Test-Umgebung</span><span class="sxs-lookup"><span data-stu-id="73cfe-103">Directory synchronization for your Office 365 dev/test environment</span></span>

 <span data-ttu-id="73cfe-104">**Zusammenfassung:** Konfigurieren Sie Directory-Synchronisierung für Ihre Office 365 Dev/Test-Umgebung.</span><span class="sxs-lookup"><span data-stu-id="73cfe-104">**Summary:** Configure directory synchronization for your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="73cfe-p101">Viele Organisationen mit Azure Active Directory verbinden und Directory-Synchronisierung mit dem den Satz von Konten in ihrer lokalen Windows Server Active Directory (AD) Gesamtstruktur den Satz von Konten in Office 365 synchronisiert. In diesem Artikel wird beschrieben, wie Sie Directory-Synchronisierung mit kennwortsynchronisierung Hash der Test-/Office 365-Umgebung hinzufügen in der folgenden Konfiguration resultierendes.</span><span class="sxs-lookup"><span data-stu-id="73cfe-p101">Many organizations use Azure AD Connect and directory synchronization to synchronize the set of accounts in their on-premises Windows Server Active Directory (AD) forest to the set of accounts in Office 365. This article describes how you can add directory synchronization with password hash synchronization to the Office 365 dev/test environment, resulting in the following configuration.</span></span>
  
![Office 365-Umgebung Test-/mit Directory-Synchronisierung](images/be5b37b0-f832-4878-b153-436c31546e21.png)
  
<span data-ttu-id="73cfe-108">Diese Konfiguration besteht aus: </span><span class="sxs-lookup"><span data-stu-id="73cfe-108">This configuration consists of:</span></span> 
  
- <span data-ttu-id="73cfe-109">Einem Office 365 E5-Testabonnement, das 30 Tage nach Erstellung abläuft.</span><span class="sxs-lookup"><span data-stu-id="73cfe-109">An Office 365 E5 Trial Subscription, which expires 30 days from when you create it.</span></span>
- <span data-ttu-id="73cfe-p102">Einem vereinfachtem Unternehmensintranet mit Internetzugriff, das aus drei virtuellen Computern in einem Subnetz eines virtuellen Azure-Netzwerks (DC1, APP1 und CLIENT1) besteht. Azure AD Connect wird auf APP1 für die Synchronisierung der Windows Server Active Directory-Domäne mit Office 365 ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="73cfe-p102">A simplified organization intranet connected to the Internet, consisting of three virtual machines on a subnet of an Azure virtual network (DC1, APP1, and CLIENT1). Azure AD Connect runs on APP1 to synchronize the Windows Server AD domain to Office 365.</span></span>
    
<span data-ttu-id="73cfe-112">Es gibt zwei Hauptphasen bei der Einrichtung dieser Entwicklungs-/Testumgebung:</span><span class="sxs-lookup"><span data-stu-id="73cfe-112">There are two phases to setting up this dev/test environment:</span></span>
  
1. <span data-ttu-id="73cfe-113">Erstellen der Office 365-Entwicklungs-/Testumgebung (virtuelle DC1-, APP1- und CLIENT1-Computer in einem virtuellen Azure Netzwerk mit einem Office 365 E5-Testabonnement)</span><span class="sxs-lookup"><span data-stu-id="73cfe-113">Create the Office 365 dev/test environment (the DC1, APP1, and CLIENT1 virtual machines in an Azure virtual network with an Office 365 E5 trial subscription).</span></span>
2. <span data-ttu-id="73cfe-114">Installieren und Konfigurieren von Azure AD Connect auf APP1</span><span class="sxs-lookup"><span data-stu-id="73cfe-114">Install and configure Azure AD Connect on APP1.</span></span>
    
> [!TIP]
> <span data-ttu-id="73cfe-115">Klicken Sie [hier](http://aka.ms/catlgstack), um eine visuelle Darstellung aller Artikel im Stapel der Testumgebungsanleitungen in der Microsoft Cloud zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="73cfe-115">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-create-an-office-365-devtest-environment"></a><span data-ttu-id="73cfe-116">Phase 1: Erstellen einer Office 365-Entwicklungs-/Testumgebung</span><span class="sxs-lookup"><span data-stu-id="73cfe-116">Phase 1: Create an Office 365 dev/test environment</span></span>

<span data-ttu-id="73cfe-p103">Befolgen Sie die Anweisungen in Phasen 1, 2 und 3 des Artikels [Office 365 Dev/Test Environment](office-365-dev-test-environment.md) . Hier ist die resultierende Konfiguration.</span><span class="sxs-lookup"><span data-stu-id="73cfe-p103">Follow the instructions in phases 1, 2, and 3 of the [Office 365 dev/test environment](office-365-dev-test-environment.md) article. Here is the resulting configuration.</span></span>
  
![Die Office 365-Entwicklungs-/Testumgebung](images/48fb91aa-09b0-4020-a496-a8253920c45d.png)
  
<span data-ttu-id="73cfe-120">Diese Konfiguration besteht aus: </span><span class="sxs-lookup"><span data-stu-id="73cfe-120">This configuration consists of:</span></span> 
  
- <span data-ttu-id="73cfe-121">Einem Office 365 E5-Testabonnement</span><span class="sxs-lookup"><span data-stu-id="73cfe-121">An Office 365 E5 Trial Subscription.</span></span>
- <span data-ttu-id="73cfe-122">Einem vereinfachtem Unternehmensintranet mit Internetzugriff, das aus virtuellen DC1-, APP1- und CLIENT1-Computern in einem Subnetz eines virtuellen Azure-Netzwerks besteht.</span><span class="sxs-lookup"><span data-stu-id="73cfe-122">A simplified organization intranet connected to the Internet, consisting of the DC1, APP1, and CLIENT1 virtual machines on a subnet of an Azure virtual network.</span></span>
    
## <a name="phase-2-install-azure-ad-connect-on-app1"></a><span data-ttu-id="73cfe-123">Phase 2: Installieren von Azure AD Connect auf APP1</span><span class="sxs-lookup"><span data-stu-id="73cfe-123">Phase 2: Install Azure AD Connect on APP1</span></span>

<span data-ttu-id="73cfe-p104">Nach Abschluss der Installation und Konfiguration synchronisiert Azure AD Connect den Kontensatz in der CORP Windows Server AD-Domäne mit dem Kontensatz im Office 365-Testabonnement. Das folgende Verfahren führt Sie durch die Installation von Azure AD Connect auf APP1 und die Sicherstellung der ordnungsgemäßen Funktionsweise.</span><span class="sxs-lookup"><span data-stu-id="73cfe-p104">Once installed and configured, Azure AD Connect synchronizes the set of accounts in the CORP Windows Server AD domain with the set of accounts in your Office 365 trial subscription. The following procedure steps you through installing Azure AD Connect on APP1 and verifying that it works.</span></span>
  
### <a name="install-and-configure-azure-ad-connect-on-app1"></a><span data-ttu-id="73cfe-126">Installieren und Konfigurieren von Azure Active Directory verbinden auf APP1</span><span class="sxs-lookup"><span data-stu-id="73cfe-126">Install and configure Azure AD Connect on APP1</span></span>

1. <span data-ttu-id="73cfe-127">Über das [Portal Azure](https://portal.azure.com)Herstellen einer Verbindung mit der CORP APP1 mit\\Konto User1 an.</span><span class="sxs-lookup"><span data-stu-id="73cfe-127">From the [Azure portal](https://portal.azure.com), connect to APP1 with the CORP\\User1 account.</span></span>
    
2. <span data-ttu-id="73cfe-128">Öffnen Sie auf APP1 eine Windows PowerShell-Eingabeaufforderung auf Administratorebene, und führen Sie die folgenden Befehle aus:</span><span class="sxs-lookup"><span data-stu-id="73cfe-128">From APP1, open an administrator-level Windows PowerShell command prompt, and then run these commands:</span></span>
    
  ```
  Set-ItemProperty -Path "HKLM:\\SOFTWARE\\Microsoft\\Active Setup\\Installed Components\\{A509B1A7-37EF-4b3f-8CFC-4F3A74704073}" -Name "IsInstalled" -Value 0
Set-ItemProperty -Path "HKLM:\\SOFTWARE\\Microsoft\\Active Setup\\Installed Components\\{A509B1A8-37EF-4b3f-8CFC-4F3A74704073}" -Name "IsInstalled" -Value 0
Stop-Process -Name Explorer -Force

  ```

3. <span data-ttu-id="73cfe-129">Klicken Sie in der Taskleiste klicken Sie auf **Internet Explorer** , und gehen Sie zu [https://aka.ms/aadconnect](https://aka.ms/aadconnect).</span><span class="sxs-lookup"><span data-stu-id="73cfe-129">From the task bar, click **Internet Explorer** and go to [https://aka.ms/aadconnect](https://aka.ms/aadconnect).</span></span>
    
4. <span data-ttu-id="73cfe-130">Klicken Sie auf der Seite Microsoft Azure Active Directory verbinden klicken Sie auf **Download**, und klicken Sie dann auf **Ausführen**.</span><span class="sxs-lookup"><span data-stu-id="73cfe-130">On the Microsoft Azure Active Directory Connect page, click **Download**, and then click **Run**.</span></span>
    
5. <span data-ttu-id="73cfe-131">Klicken Sie auf der Seite **Willkommen auf Azure Active Directory verbinden** auf **ich stimme zu**, und klicken Sie dann auf **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="73cfe-131">On the **Welcome to Azure AD Connect** page, click **I agree**, and then click **Continue**.</span></span>
    
6. <span data-ttu-id="73cfe-132">Klicken Sie auf der Seite **Einstellungen für Express** auf **express Einstellungen verwenden**.</span><span class="sxs-lookup"><span data-stu-id="73cfe-132">On the **Express Settings** page, click **Use express settings**.</span></span>
    
7. <span data-ttu-id="73cfe-133">Klicken Sie auf der Seite **Connect to Azure AD** **Username,** Geben Sie in Geben Sie Ihren Kontonamen globaler Administrator im Feld **Kennwort**das Kennwort ein, und klicken Sie dann auf **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="73cfe-133">On the **Connect to Azure AD** page, type your global administrator account name in **Username,** type its password in **Password**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="73cfe-134">Geben Sie auf der Seite **Verbindung mit AD DS** **CORP\\User1** in **Benutzername** Geben Sie im Feld **Kennwort**das Kennwort ein, und klicken Sie dann auf **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="73cfe-134">On the **Connect to AD DS** page, type **CORP\\User1** in **Username,** type its password in **Password**, and then click **Next**.</span></span>
    
9. <span data-ttu-id="73cfe-135">Klicken Sie auf der Seite **Azure AD - Anmeldung Konfiguration** klicken Sie auf **Weiter, ohne alle überprüften Domänen**, und klicken Sie dann auf **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="73cfe-135">On the **Azure AD sign-in configuration** page, click **Continue without any verified domains**, and then click **Next**.</span></span>
    
10. <span data-ttu-id="73cfe-136">Klicken Sie auf der Seite **Bereit zur Konfiguration** auf **Installieren**.</span><span class="sxs-lookup"><span data-stu-id="73cfe-136">On the **Ready to configure** page, click **Install**.</span></span>
    
11. <span data-ttu-id="73cfe-137">Klicken Sie auf der Seite **Konfiguration abgeschlossen** auf **Beenden**.</span><span class="sxs-lookup"><span data-stu-id="73cfe-137">On the **Configuration complete** page, click **Exit**.</span></span>
    
12. <span data-ttu-id="73cfe-138">Wechseln Sie in Internet Explorer zu Office 365-Portal ([https://portal.office.com](https://portal.office.com)) und melden Sie sich Test Office 365-Abonnement mit Ihrer globalen Administratorkonto an.</span><span class="sxs-lookup"><span data-stu-id="73cfe-138">In Internet Explorer, go to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) and sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
13. <span data-ttu-id="73cfe-139">Klicken Sie auf der Hauptportalseite auf **Admin**.</span><span class="sxs-lookup"><span data-stu-id="73cfe-139">From the main portal page, click **Admin**.</span></span>
    
14. <span data-ttu-id="73cfe-140">Klicken Sie im linken Navigationsbereich auf **Benutzer > Aktive Benutzer**.</span><span class="sxs-lookup"><span data-stu-id="73cfe-140">In the left navigation, click **Users > Active users**.</span></span>
    
    <span data-ttu-id="73cfe-p105">Notieren Sie das Konto, mit dem Namen **User1**. Dieses Konto wird von der CORP Windows Azure AD-Domäne und belegen, die verzeichnissynchronisierung gearbeitet hat.</span><span class="sxs-lookup"><span data-stu-id="73cfe-p105">Note the account named **User1**. This account is from the CORP Windows Server AD domain and is proof that directory synchronization has worked.</span></span>
    
15. <span data-ttu-id="73cfe-p106">Klicken Sie auf dem Konto **User1** an. Lizenzen klicken Sie auf **Bearbeiten**.</span><span class="sxs-lookup"><span data-stu-id="73cfe-p106">Click the **User1** account. For product licenses, click **Edit**.</span></span>
    
16. <span data-ttu-id="73cfe-p107">Wählen Sie in der **Lizenzen**Ihr Land, und klicken Sie dann auf das Steuerelement **deaktiviert** für **Office 365 Enterprise E5** (Wechsel auf **aktiviert**). Klicken Sie auf **Speichern** , am unteren Rand der Seite, und klicken Sie dann auf **Schließen**.</span><span class="sxs-lookup"><span data-stu-id="73cfe-p107">In **Product licenses**, select your country, and then click the **Off** control for **Office 365 Enterprise E5** (switching it to **On**). Click **Save** at the bottom of the page, and then click **Close**.</span></span>
    
<span data-ttu-id="73cfe-147">Nachfolgend sehen Sie die daraus resultierende Konfiguration.</span><span class="sxs-lookup"><span data-stu-id="73cfe-147">This is the resulting configuration.</span></span>
  
![Office 365-Umgebung Test-/mit Directory-Synchronisierung](images/be5b37b0-f832-4878-b153-436c31546e21.png)
  
<span data-ttu-id="73cfe-149">Diese Konfiguration besteht aus: </span><span class="sxs-lookup"><span data-stu-id="73cfe-149">This configuration consists of:</span></span> 
  
- <span data-ttu-id="73cfe-150">Einem Office 365 E5-Testabonnement</span><span class="sxs-lookup"><span data-stu-id="73cfe-150">An Office 365 E5 Trial Subscription.</span></span>
- <span data-ttu-id="73cfe-p108">Einem vereinfachtem Unternehmensintranet mit Internetzugriff, das aus virtuellen DC1-, APP1- und CLIENT1-Computern in einem Subnetz eines virtuellen Azure-Netzwerks besteht. Azure AD Connect wird auf APP1 ausgeführt, um die CORP Windows Server Active Directory-Domäne mit Office 365 alle 30 Minuten zu synchronisieren.</span><span class="sxs-lookup"><span data-stu-id="73cfe-p108">A simplified organization intranet connected to the Internet, consisting of the DC1, APP1, and CLIENT1 virtual machines on a subnet of an Azure virtual network. Azure AD Connect runs on APP1 to synchronize the CORP Windows Server AD domain to Office 365 every 30 minutes.</span></span>
    
## <a name="next-step"></a><span data-ttu-id="73cfe-153">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="73cfe-153">Next Step</span></span>

<span data-ttu-id="73cfe-154">Wenn Sie zum Bereitstellen von verzeichnissynchronisierung für Ihre Organisation bereit sind, finden Sie unter [Bereitstellen von Office 365 Directory-Synchronisierung in Microsoft Azure](deploy-office-365-directory-synchronization-dirsync-in-microsoft-azure.md).</span><span class="sxs-lookup"><span data-stu-id="73cfe-154">When you are ready to deploy directory synchronization for your organization, see [Deploy Office 365 directory synchronization in Microsoft Azure](deploy-office-365-directory-synchronization-dirsync-in-microsoft-azure.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="73cfe-155">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="73cfe-155">See Also</span></span>

<span data-ttu-id="73cfe-156">[Cloud-Annahme Test Lab Guides (TLGs)](cloud-adoption-test-lab-guides-tlgs.md)
[Basiskonfiguration Test-/Umgebung](base-configuration-dev-test-environment.md)
[Office 365 Dev/testumgebung](office-365-dev-test-environment.md)
[Cloud App-Sicherheit für Ihre Office 365-Umgebung](cloud-app-security-for-your-office-365-dev-test-environment.md) Test-/
 [ Erweiterte Schutz für Ihre Office 365-Umgebung Test-/](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
[Cloud-Übernahme- und hybridlösungen](cloud-adoption-and-hybrid-solutions.md)</span><span class="sxs-lookup"><span data-stu-id="73cfe-156">[Cloud adoption Test Lab Guides (TLGs)](cloud-adoption-test-lab-guides-tlgs.md)
[Base Configuration dev/test environment](base-configuration-dev-test-environment.md)
[Office 365 dev/test environment](office-365-dev-test-environment.md)
[Cloud App Security for your Office 365 dev/test environment](cloud-app-security-for-your-office-365-dev-test-environment.md)
[Advanced Threat Protection for your Office 365 dev/test environment](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
[Cloud adoption and hybrid solutions](cloud-adoption-and-hybrid-solutions.md)</span></span>




