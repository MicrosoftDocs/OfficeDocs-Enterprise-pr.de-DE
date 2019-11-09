---
title: Schutz vertraulicher Dateien in Office 365-Entwicklungs-/-Testumgebungen
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/01/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- SPO_Content
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: 27ecff45-06a6-4629-bc45-9dab4eef3a21
description: 'Zusammenfassung: Konfigurieren und veranschaulichen, wie Office 365 Verwaltung von Informationsrechten Ihre vertraulichen Dateien schützt, auch wenn Sie in die falsche SharePoint Online Websitesammlung geschrieben werden.'
ms.openlocfilehash: b8cb56a69a04133b2863c31da9e359c2272d4fc5
ms.sourcegitcommit: 89ecf793443963b4c87cf1033bf0284cbfb83d9a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2019
ms.locfileid: "38078124"
---
# <a name="sensitive-file-protection-in-the-office-365-devtest-environment"></a><span data-ttu-id="762b9-103">Schutz vertraulicher Dateien in Office 365-Entwicklungs-/-Testumgebungen</span><span class="sxs-lookup"><span data-stu-id="762b9-103">Sensitive file protection in the Office 365 dev/test environment</span></span>

 <span data-ttu-id="762b9-104">**Zusammenfassung:** Konfigurieren und veranschaulichen, wie Office 365 Verwaltung von Informationsrechten Ihre vertraulichen Dateien schützt, auch wenn Sie in die falsche SharePoint Online Websitesammlung geschrieben werden.</span><span class="sxs-lookup"><span data-stu-id="762b9-104">**Summary:** Configure and demonstrate how Office 365 Information Rights Management protects your sensitive files, even when they are posted to the wrong SharePoint Online site collection.</span></span>
  
<span data-ttu-id="762b9-p101">Information Rights Management (IRM) in Office 365 umfasst eine Reihe von Funktionen zum Schutz von Dokumenten, die aus SharePoint Online-Bibliotheken und -Listen heruntergeladen werden. Heruntergeladene Dateien sind verschlüsselt und verfügen über die Berechtigungen zum Öffnen, Kopieren, Speichern und Drucken, welche der SharePoint Online-Bibliothek entsprechen, in der sie gespeichert sind.</span><span class="sxs-lookup"><span data-stu-id="762b9-p101">Information Rights Management (IRM) in Office 365 is a set of capabilities to protect documents that are downloaded from SharePoint Online libraries and lists. Downloaded files are encrypted and contain the open, copy, save, and print permissions that reflect the SharePoint Online library in which they were stored.</span></span>
  
<span data-ttu-id="762b9-107">Mithilfe der Anleitungen in diesem Artikel können Sie IRM in Office 365 für Dateien aktivieren und testen, die in Ihrem Office 365-Testabonnement möglicherweise vertrauliche Informationen enthalten.</span><span class="sxs-lookup"><span data-stu-id="762b9-107">With the instructions in this article, you enable and test IRM in Office 365 for files containing possible sensitive information in your Office 365 trial subscription.</span></span>
  
> [!TIP]
> <span data-ttu-id="762b9-108">Klicken Sie [hier](https://aka.ms/catlgstack), um eine visuelle Darstellung aller Artikel im Stapel der Testumgebungsanleitungen in Office 365 zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="762b9-108">Click [here](https://aka.ms/catlgstack) for a visual map to all the articles in the Office 365 Test Lab Guide stack.</span></span>
  
## <a name="phase-1-build-out-your-office-365-devtest-environment"></a><span data-ttu-id="762b9-109">Phase 1: Erstellen Ihrer Office 365-Entwicklungs-/Testumgebung</span><span class="sxs-lookup"><span data-stu-id="762b9-109">Phase 1: Build out your Office 365 dev/test environment</span></span>

<span data-ttu-id="762b9-110">Wenn Sie den Schutz vertraulicher Dateien auf einfache Weise mit Minimalanforderungen testen möchten, folgen Sie den Anweisungen für Phase 2 und 3 unter [Office 365 dev/test environment](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="762b9-110">If you just want to test sensitive file protection in a lightweight way with the minimum requirements, follow the instructions in phases 2 and 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="762b9-111">Wenn Sie den Schutz vertraulicher Dateien in einer simulierten Unternehmensumgebung testen möchten, folgen Sie den Anweisungen unter [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="762b9-111">If you want to test sensitive file protection in a simulated enterprise, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="762b9-112">Zum Testen des Schutzes vertraulicher Dateien ist keine simulierte Enterprise-Entwicklungs-/Testumgebung erforderlich, die ein simuliertes, mit dem Internet verbundenes Intranet und eine Verzeichnissynchronisierung für eine Active Directory-Domänendienste (AD DS) Gesamtstruktur umfasst.</span><span class="sxs-lookup"><span data-stu-id="762b9-112">Testing sensitive file protection does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for a Active Directory Domain Services (AD DS) forest.</span></span> <span data-ttu-id="762b9-113">Dies wird hier als Option bereitgestellt, damit Sie den Schutz vertraulicher Dateien testen und damit in einer Umgebung, die eine typische Organisation darstellt, experimentieren können.</span><span class="sxs-lookup"><span data-stu-id="762b9-113">It is provided here as an option so that you can test sensitive file protection and experiment with it in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-demonstrate-how-documents-from-permissions-protected-sites-can-be-leaked"></a><span data-ttu-id="762b9-114">Phase 2: Demonstriert, wie Dokumente von Websites, die durch Berechtigungen geschützt sind, anderweitig (und möglicherweise missbräuchlich) verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="762b9-114">Phase 2: Demonstrate how documents from permissions-protected sites can be leaked</span></span>

<span data-ttu-id="762b9-115">In dieser Phase demonstrieren Sie, wie jemand ein Dokument von einer Website, die durch Berechtigungen geschützt ist, herunterladen und anschließend auf eine Website hochladen kann, die nicht auf diese Weise geschützt und entsprechend allgemein zugänglich ist.</span><span class="sxs-lookup"><span data-stu-id="762b9-115">In this phase, you demonstrate that someone can download a document from a permissions-protected site and then upload it to a site that has wide-open permissions.</span></span>
  
<span data-ttu-id="762b9-116">Sie fügen zuerst drei neue Benutzerkonten für Führungskräfte hinzu und weisen diesen Office 365 E5-Lizenzen zu.</span><span class="sxs-lookup"><span data-stu-id="762b9-116">First, you add three new user accounts that represent executives and assign them Office 365 E5 licenses.</span></span>
  
<span data-ttu-id="762b9-117">Verwenden Sie die Anweisungen unter [Connect to Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx) , um die PowerShell-Module (falls erforderlich) zu installieren und eine Verbindung zu Ihrem neuen Office 365-Abonnement von herzustellen:</span><span class="sxs-lookup"><span data-stu-id="762b9-117">Use the instructions in [Connect to Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx) to install the PowerShell modules (if needed) and connect to your new Office 365 subscription from:</span></span>
  
- <span data-ttu-id="762b9-118">Ihrem Computer aus (für die einfache Office 365-Entwicklungs-/Testunternehmensumgebung).</span><span class="sxs-lookup"><span data-stu-id="762b9-118">Your computer (for the lightweight Office 365 dev/test environment).</span></span>
    
- <span data-ttu-id="762b9-119">Dem virtuellen Computer CLIENT1 aus (für die simulierte Office 365-Entwicklungs-/Testumgebung).</span><span class="sxs-lookup"><span data-stu-id="762b9-119">The CLIENT1 virtual machine (for the simulated enterprise Office 365 dev/test environment).</span></span>
    
<span data-ttu-id="762b9-120">Geben Sie im Dialogfeld **Bei Windows PowerShell anmelden** den Namen des globalen Office 365-Administrators (Beispiel: jdoe@contosotoycompany.onmicrosoft.com) und das Kennwort Ihres Office 365-Testabonnements ein.</span><span class="sxs-lookup"><span data-stu-id="762b9-120">In the **Windows PowerShell Credential Request** dialog box, type the Office 365 global administrator name (example: jdoe@contosotoycompany.onmicrosoft.com) and password of your Office 365 trial subscription.</span></span>
  
<span data-ttu-id="762b9-121">Geben Sie den Namen der Organisation (zum Beispiel „contosotoycompany“) und den zweistelligen Ländercode für Ihren Standort ein. Führen Sie dann über die „Windows Azure Active Directory-Modul für Windows PowerShell“-Eingabeaufforderung die folgenden Befehle aus:</span><span class="sxs-lookup"><span data-stu-id="762b9-121">Fill in your organization name (example: contosotoycompany) and the two-character country code for your location, and then run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$orgName="<organization name>"
$loc="<two-character country code, such as US>"
$licAssignment= $orgName + ":ENTERPRISEPREMIUM"
$userName= "ceo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "CEO" -FirstName "Chief" -LastName "Executive Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

<span data-ttu-id="762b9-122">Notieren Sie aus der **New-MsolUser**-Befehlsanzeige das Kennwort, das für das CEO-Konto generiert wurde, und bewahren Sie es an einem sicheren Ort auf.</span><span class="sxs-lookup"><span data-stu-id="762b9-122">From the display of the **New-MsolUser** command, note the generated password for the CEO account and record it in a safe location.</span></span>
  
<span data-ttu-id="762b9-123">Führen Sie über die „Windows Azure Active Directory-Modul für Windows PowerShell“-Eingabeaufforderung die folgenden Befehle aus:</span><span class="sxs-lookup"><span data-stu-id="762b9-123">Run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$userName= "cfo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "CFO" -FirstName "Chief" -LastName "Financial Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

<span data-ttu-id="762b9-124">Notieren Sie aus der **New-MsolUser**-Befehlsanzeige das Kennwort, das für das CFO-Konto generiert wurde, und bewahren Sie es an einem sicheren Ort auf.</span><span class="sxs-lookup"><span data-stu-id="762b9-124">From the display of the **New-MsolUser** command, note the generated password for the CFO account and record it in a safe location.</span></span>
  
<span data-ttu-id="762b9-125">Führen Sie über die „Windows Azure Active Directory-Modul für Windows PowerShell“-Eingabeaufforderung die folgenden Befehle aus:</span><span class="sxs-lookup"><span data-stu-id="762b9-125">Run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$userName= "coo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "COO" -FirstName "Chief" -LastName "Operations Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

<span data-ttu-id="762b9-126">Notieren Sie aus der **New-MsolUser**-Befehlsanzeige das Kennwort, das für das COO-Konto generiert wurde, und bewahren Sie es an einem sicheren Ort auf.</span><span class="sxs-lookup"><span data-stu-id="762b9-126">From the display of the **New-MsolUser** command, note the generated password for the COO account and record it in a safe location.</span></span>
  
<span data-ttu-id="762b9-127">Im nächsten Schritt erstellen Sie eine private Führungskräftegruppe und fügen dieser die neuen Führungskräftekonten hinzu.</span><span class="sxs-lookup"><span data-stu-id="762b9-127">Next, you create a private Executives group and add the new executive accounts to it.</span></span>
  
1. <span data-ttu-id="762b9-128">Wechseln Sie in Ihrem Browser zum Office-Portal unter [https://admin.microsoft.com](https://admin.microsoft.com) , und melden Sie sich bei Ihrem Office 365 Testabonnement mit ihrem globalen Administratorkonto an.</span><span class="sxs-lookup"><span data-stu-id="762b9-128">In your browser, go to the Office portal at [https://admin.microsoft.com](https://admin.microsoft.com) and sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
  - <span data-ttu-id="762b9-129">Wenn Sie die einfache Office 365-Entwicklungs-/Testumgebung verwenden, öffnen Sie eine private Sitzung in Internet Explorer bzw. in dem von Ihnen bevorzugten Browser, und melden Sie sich von Ihrem lokalen Computer aus an.</span><span class="sxs-lookup"><span data-stu-id="762b9-129">If you are using the lightweight Office 365 dev/test environment, open a private session of Internet Explorer or your browser and sign in from your local computer.</span></span>
    
  - <span data-ttu-id="762b9-130">Wenn Sie die simulierte Office 365-Unternehmensentwicklungs-/-testumgebung verwenden, verwenden Sie das Azure-Portal, um sich mit dem virtuellen Computer CLIENT1 zu verbinden, und melden Sie sich dann von CLIENT1 aus an.</span><span class="sxs-lookup"><span data-stu-id="762b9-130">If you are using the simulated enterprise Office 365 dev/test environment, use the Azure portal to connect to the CLIENT1 virtual machine, and then sign in from CLIENT1.</span></span>
    
2. <span data-ttu-id="762b9-131">Klicken Sie auf der Registerkarte **Microsoft Office Home** auf **Admin > Gruppen > Gruppen**, und klicken Sie dann auf **Gruppe hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="762b9-131">On the **Microsoft Office Home** tab, click **Admin > Groups > Groups**, and then click **Add a group**.</span></span>
    
3. <span data-ttu-id="762b9-132">Wählen Sie unter **Gruppe hinzufügen** die Option **Office 365-Gruppe** als Gruppentyp aus, geben Sie **Führungskräfte** unter **Name** und **Gruppen-ID** ein, und wählen Sie unter **Datenschutz** die Option **Privat**. Klicken Sie dann auf **Besitzer auswählen**.</span><span class="sxs-lookup"><span data-stu-id="762b9-132">In **Add a group**, select **Office 365 group** for the group type, type **Executives** in **Name** and **Group Id**, select **Private** for **Privacy**, and then click **Select Owner**.</span></span>
    
4. <span data-ttu-id="762b9-133">Klicken Sie in der Liste auf den Namen Ihres globalen Administratorkontos.</span><span class="sxs-lookup"><span data-stu-id="762b9-133">In the list, click your global administrator account name.</span></span>
    
5. <span data-ttu-id="762b9-134">Klicken Sie auf **Hinzufügen** und dann auf **Schließen**.</span><span class="sxs-lookup"><span data-stu-id="762b9-134">Click **Add**, and then click **Close**.</span></span>
    
6. <span data-ttu-id="762b9-135">Klicken Sie in der Gruppenliste auf **Führungskräfte**.</span><span class="sxs-lookup"><span data-stu-id="762b9-135">In the groups list, click **Executives**.</span></span>
    
7. <span data-ttu-id="762b9-136">Klicken Sie auf die Option zum Bearbeiten der Mitglieder\*\*\*\*.</span><span class="sxs-lookup"><span data-stu-id="762b9-136">Click **Edit for Members**.</span></span>
    
8. <span data-ttu-id="762b9-p103">Klicken Sie auf **Mitglieder hinzufügen**. Wählen Sie in der Mitgliederliste die folgenden Benutzerkonten aus:</span><span class="sxs-lookup"><span data-stu-id="762b9-p103">Click **Add members**. In the member list, select the following user accounts:</span></span>
    
  - <span data-ttu-id="762b9-139">Chief Executive Officer</span><span class="sxs-lookup"><span data-stu-id="762b9-139">Chief Executive Officer</span></span>
    
  - <span data-ttu-id="762b9-140">Chief Financial Officer</span><span class="sxs-lookup"><span data-stu-id="762b9-140">Chief Financial Officer</span></span>
    
  - <span data-ttu-id="762b9-141">Chief Operations Officer</span><span class="sxs-lookup"><span data-stu-id="762b9-141">Chief Operations Officer</span></span>
    
9. <span data-ttu-id="762b9-142">Klicken Sie auf **Speichern** und dann auf **Schließen**.</span><span class="sxs-lookup"><span data-stu-id="762b9-142">Click **Save**, and then click **Close**.</span></span>
    
10. <span data-ttu-id="762b9-143">Schließen Sie die Registerkarte des Office Admin Centers\*\*\*\*.</span><span class="sxs-lookup"><span data-stu-id="762b9-143">Close the **Office Admin center** tab.</span></span>
    
<span data-ttu-id="762b9-144">Im nächsten Schritt erstellen Sie eine Websitesammlung für Führungskräfte und erlauben nur den Mitgliedern der Führungskräftegruppe den Zugriff darauf.</span><span class="sxs-lookup"><span data-stu-id="762b9-144">Next, you create an Executives site collection and allow just the members of the Executives group to access it.</span></span>
  
1. <span data-ttu-id="762b9-145">Klicken Sie auf die Registerkarte **Microsoft Office Home** auf **Admin**.</span><span class="sxs-lookup"><span data-stu-id="762b9-145">On the **Microsoft Office Home** tab, click the **Admin** tile.</span></span>
    
2. <span data-ttu-id="762b9-146">Klicken Sie auf der Registerkarte **Office Admin Center** auf admin Centers **#a0 SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="762b9-146">On the **Office Admin center** tab, click **Admin centers > SharePoint**.</span></span>
    
3. <span data-ttu-id="762b9-147">Klicken Sie auf der Registerkarte **SharePoint Admin Center** auf **neue #a0 private Websitesammlung**.</span><span class="sxs-lookup"><span data-stu-id="762b9-147">On the **SharePoint admin center** tab, click **New > Private site collection**.</span></span>
    
4. <span data-ttu-id="762b9-148">Geben Sie im Bereich neue Websitesammlung **Führungs** Kräfte in **Titel**, Führungskräfte im Feld URL ein, geben Sie den Namen des globalen Administratorkontos unter **Administrator**an, und klicken Sie dann auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="762b9-148">In the new site collection pane, type **Executives** in **Title**, executives in the URL box, specify the name of your global administrator account in **Administrator**, and then click **OK**.</span></span>
    
5. <span data-ttu-id="762b9-149">Warten Sie, bis die neue Websitesammlung erstellt wurde.</span><span class="sxs-lookup"><span data-stu-id="762b9-149">Wait until the new site collection has been created.</span></span> <span data-ttu-id="762b9-150">Wenn Sie fertig sind, kopieren Sie die URL der neuen Führungskräfte-Websitesammlung, und fügen Sie Sie in eine neue Registerkarte Ihres Browsers ein.</span><span class="sxs-lookup"><span data-stu-id="762b9-150">When complete, copy the URL of the new Executives site collection and paste it into a new tab of your browser.</span></span>
    
6. <span data-ttu-id="762b9-151">Klicken Sie in der oberen rechten Ecke der Websitesammlung **Führungskräfte** auf das Einstellungssymbol, und klicken Sie dann auf **Freigegeben für**.</span><span class="sxs-lookup"><span data-stu-id="762b9-151">In the upper right of the **Executives** site collection, click the settings icon, and then click **Shared with**.</span></span>
    
7. <span data-ttu-id="762b9-152">Klicken Sie in **Share ' Executives '** auf **erweitert**.</span><span class="sxs-lookup"><span data-stu-id="762b9-152">In **Share 'Executives'**, click **Advanced**.</span></span>
    
8. <span data-ttu-id="762b9-153">Klicken Sie in der Liste der SharePoint-Gruppen auf **Mitglieder von „Führungskräfte“**.</span><span class="sxs-lookup"><span data-stu-id="762b9-153">In the list of SharePoint groups, click **Executives Members**.</span></span>
    
9. <span data-ttu-id="762b9-154">Klicken Sie auf der Seite **Benutzer und Gruppen** auf **Neu**.</span><span class="sxs-lookup"><span data-stu-id="762b9-154">On the **People and Groups** page, click **New**.</span></span>
    
10. <span data-ttu-id="762b9-155">Geben Sie im Bereich Führungs **Kräfte freigeben**den Namen **Führungs**Kräfte ein, klicken Sie auf die Gruppe **Führungskräfte** , und klicken Sie dann auf **Freigeben**.</span><span class="sxs-lookup"><span data-stu-id="762b9-155">In **Share 'Executives'**, type **Executives**, click the **Executives** group, and then click **Share**.</span></span>
    
11. <span data-ttu-id="762b9-156">Schließen Sie die Registerkarte **Benutzer und Gruppen** .</span><span class="sxs-lookup"><span data-stu-id="762b9-156">Close the **People and groups** tab.</span></span>
    
<span data-ttu-id="762b9-157">Im nächsten Schritt erlauben Sie allen Gruppenmitgliedern, auf die Websitesammlung „Vertrieb“ zuzugreifen.</span><span class="sxs-lookup"><span data-stu-id="762b9-157">Next, you allow everyone to access the Sales site collection.</span></span>
  
1. <span data-ttu-id="762b9-158">Kopieren Sie auf der Registerkarte **SharePoint Admin Center** die URL der Sales-Websitesammlung, und fügen Sie Sie in eine neue Registerkarte Ihres Browsers ein..</span><span class="sxs-lookup"><span data-stu-id="762b9-158">From the **SharePoint admin center** tab, copy the URL of the Sales site collection and paste it into a new tab of your browser..</span></span>
    
2. <span data-ttu-id="762b9-159">Klicken Sie in der oberen rechten Ecke auf das Einstellungssymbol, und klicken Sie dann auf **Freigegeben für**.</span><span class="sxs-lookup"><span data-stu-id="762b9-159">In the upper right, click the settings icon, and then click **Shared with**.</span></span>
    
3. <span data-ttu-id="762b9-160">Klicken Sie in **share "Sales Site Collection"** auf **erweitert**.</span><span class="sxs-lookup"><span data-stu-id="762b9-160">In **Share 'Sales site collection'**, click **Advanced**.</span></span>
    
4. <span data-ttu-id="762b9-161">Klicken Sie in der Liste der SharePoint-Gruppen auf **Mitglieder der Websitesammlung „Vertrieb“**.</span><span class="sxs-lookup"><span data-stu-id="762b9-161">In the list of SharePoint groups, click **Sales site collection Members**.</span></span>
    
5. <span data-ttu-id="762b9-162">Klicken Sie auf der Seite **Benutzer und Gruppen** auf **Neu**.</span><span class="sxs-lookup"><span data-stu-id="762b9-162">On the **People and Groups** page, click **New**.</span></span>
    
6. <span data-ttu-id="762b9-163">Geben Sie in **share "Sales Site Collection"** **jeden**ein, klicken Sie auf **jeder außer auf externe Benutzer**, und klicken Sie dann auf **Freigeben**.</span><span class="sxs-lookup"><span data-stu-id="762b9-163">In **Share 'Sales site collection'**, type **Everyone**, click **Everyone except external users**, and then click **Share**.</span></span>
    
7. <span data-ttu-id="762b9-164">Schließen Sie die **Websitesammlung „Vertrieb“** und die Registerkarten von **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="762b9-164">Close the **Sales site collection** and **SharePoint** tabs.</span></span>
    
<span data-ttu-id="762b9-165">Als Nächstes melden Sie sich mit einem Führungskräftekonto an und erstellen ein Dokument in der Websitesammlung „Führungskräfte“.</span><span class="sxs-lookup"><span data-stu-id="762b9-165">Next, you sign in with an executive account and create a document in the Executives site collection.</span></span>
  
1. <span data-ttu-id="762b9-166">Klicken Sie auf der Registerkarte der **Microsoft Office-Startseite** auf das Benutzersymbol in der oberen rechten Ecke, und klicken Sie dann auf **Abmelden**.</span><span class="sxs-lookup"><span data-stu-id="762b9-166">On the **Microsoft Office Home** tab, click the user icon in the upper-right, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="762b9-167">Wechseln Sie zu [https://admin.microsoft.com](https://admin.microsoft.com).</span><span class="sxs-lookup"><span data-stu-id="762b9-167">Go to [https://admin.microsoft.com](https://admin.microsoft.com).</span></span>
    
3. <span data-ttu-id="762b9-168">Klicken Sie auf der **Office 365-Anmeldeseite** auf **Anderes Konto verwenden**.</span><span class="sxs-lookup"><span data-stu-id="762b9-168">On the **Office 365 sign in** page, click **Use another account**.</span></span>
    
4. <span data-ttu-id="762b9-169">Geben Sie den Kontonamen **CEO** sowie das entsprechende Kennwort ein, und klicken Sie auf **Anmelden**.</span><span class="sxs-lookup"><span data-stu-id="762b9-169">Type the **CEO** account name and its password, and then click **Sign in**.</span></span>
    
5. <span data-ttu-id="762b9-170">Geben Sie auf einer neuen Registerkarte Ihres Browsers die URL der Websitesammlung "Führungskräfte" ( **https://**\<Organization Name>**. SharePoint.com/Sites/Executives**) ein.</span><span class="sxs-lookup"><span data-stu-id="762b9-170">On a new tab of your browser, type the URL to the Executives site collection ( **https://**\<organization name>**.sharepoint.com/sites/executives**).</span></span>
    
6. <span data-ttu-id="762b9-171">Klicken Sie auf **Dokumente**, dann auf **neu** und dann auf **Word-Dokument**.</span><span class="sxs-lookup"><span data-stu-id="762b9-171">Click **Documents**, click **New,** and then click **Word Document**.</span></span>
    
7. <span data-ttu-id="762b9-172">Klicken Sie in die Titelleiste, und geben Sie **VertraulicheDaten-VorIRM** ein.</span><span class="sxs-lookup"><span data-stu-id="762b9-172">Click in the title bar and type **SensitiveData-BeforeIRM**.</span></span>
    
8. <span data-ttu-id="762b9-173">Klicken Sie in den Textbereich des Dokuments, und geben Sie **Protokoll der letzten Vorstandssitzung** ein. Klicken Sie dann auf **Führungskräfte**.</span><span class="sxs-lookup"><span data-stu-id="762b9-173">Click in the document body and type **Minutes from the latest board meeting**, and then click **Executives**.</span></span>
    
     <span data-ttu-id="762b9-174"> Die Datei **VertraulicheDaten-VorIRM.docx** sollte im Ordner **Dokumente** angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="762b9-174">You should see **SensitiveData-BeforeIRM.docx** in the **Documents** folder.</span></span>
    
<span data-ttu-id="762b9-175">Im nächsten Schritt laden Sie eine lokale Kopie des Dokuments „VertraulicheDaten-VorIRM.docx“ herunter und veröffentlichen diese versehentlich in der Websitesammlung „Vertrieb“.</span><span class="sxs-lookup"><span data-stu-id="762b9-175">Next, you download a local copy of the SensitiveData-BeforeIRM.docx document and then accidentally post it to the Sales site collection.</span></span>
  
1. <span data-ttu-id="762b9-176">Erstellen Sie auf dem lokalen Computer einen neuen Ordner (beispielsweise C:\\TLGs\\SensitiveDataTestFiles).</span><span class="sxs-lookup"><span data-stu-id="762b9-176">On your local computer, create a new folder (for example, C:\\TLGs\\SensitiveDataTestFiles).</span></span>
    
2. <span data-ttu-id="762b9-177">Wählen Sie auf der Registerkarte **Dokumente** in Ihrem Browser das Dokument **VertraulicheDaten-VorIRM.docx** aus, klicken Sie auf die drei Punkte (Ellipse), und klicken Sie dann auf **Herunterladen**.</span><span class="sxs-lookup"><span data-stu-id="762b9-177">On the **Documents** tab of your browser, select the **SensitiveData-BeforeIRM.docx** document, click the ellipses, and then click **Download**.</span></span>
    
3. <span data-ttu-id="762b9-178">Speichern Sie das Dokument **VertraulicheDaten-VorIRM.docx** in dem Ordner, den Sie in Schritt 1 erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="762b9-178">Store the **SensitiveData-BeforeIRM.docx** document in the folder created in step 1.</span></span>
    
4. <span data-ttu-id="762b9-179">Geben Sie auf einer neuen Registerkarte Ihres Browsers die URL der Websitesammlung "Sales" ein ( **https://**\<Organization Name>**. SharePoint.com/Sites/Sales**).</span><span class="sxs-lookup"><span data-stu-id="762b9-179">On a new tab of your browser, type the URL to the Sales site collection ( **https://**\<organization name>**.sharepoint.com/sites/sales**).</span></span>
    
5. <span data-ttu-id="762b9-180">Klicken Sie auf den Ordner **Dokumente** der **Websitesammlung „Vertrieb“**.</span><span class="sxs-lookup"><span data-stu-id="762b9-180">Click the **Documents** folder of the **Sales site collection**.</span></span>
    
6. <span data-ttu-id="762b9-181">Klicken Sie auf **Hochladen**, und geben Sie dann das Dokument **VertraulicheDaten-VorIRM.docx** in dem Ordner an, den Sie in Schritt 1 erstellt haben. Klicken Sie dann auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="762b9-181">Click **Upload**, and then specify **SensitiveData-BeforeIRM.docx** document in the folder created in step 1, and then click **OK**.</span></span>
    
7. <span data-ttu-id="762b9-182">Stellen Sie sicher, dass sich das Dokument **VertraulicheDaten-VorIRM.docx** im Ordner **Dokumente** befindet.</span><span class="sxs-lookup"><span data-stu-id="762b9-182">Verify that the **SensitiveData-BeforeIRM.docx** document is in the **Documents** folder.</span></span>
    
8. <span data-ttu-id="762b9-183">Schließen Sie die Registerkarten **Vertrieb** und **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="762b9-183">Close the **Sales** and **SharePoint** tabs.</span></span>
    
<span data-ttu-id="762b9-184">Als Nächstes melden Sie sich als Benutzer5 an und versuchen, das Dokument „VertraulicheDaten-VorIRM.docx“ in der Websitesammlung „Vertrieb“ zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="762b9-184">Next, you sign in as User5 and try to open the SensitiveData-BeforeIRM.docx document in the Sales site collection.</span></span>
  
1. <span data-ttu-id="762b9-185">Klicken Sie auf der Registerkarte der **Microsoft Office-Startseite** auf das Benutzersymbol in der oberen rechten Ecke, und klicken Sie dann auf **Abmelden**.</span><span class="sxs-lookup"><span data-stu-id="762b9-185">On the **Microsoft Office Home** tab, click the user icon in the upper-right, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="762b9-186">Wechseln Sie zu [https://admin.microsoft.com](https://admin.microsoft.com).</span><span class="sxs-lookup"><span data-stu-id="762b9-186">Go to [https://admin.microsoft.com](https://admin.microsoft.com).</span></span>
    
3. <span data-ttu-id="762b9-187">Klicken Sie auf der **Office 365-Anmeldeseite** auf **Anderes Konto verwenden**.</span><span class="sxs-lookup"><span data-stu-id="762b9-187">On the **Office 365 sign in** page, click **Use another account**.</span></span>
    
4. <span data-ttu-id="762b9-188">Geben Sie den Benutzernamen und das Kennwort von Benutzer 5 ein, und klicken Sie dann auf **Anmelden**.</span><span class="sxs-lookup"><span data-stu-id="762b9-188">Type the User5 account name and its password, and then click **Sign in**.</span></span>
    
5. <span data-ttu-id="762b9-189">Geben Sie auf einer neuen Registerkarte Ihres Browsers die URL der Websitesammlung "Vertrieb" ein.</span><span class="sxs-lookup"><span data-stu-id="762b9-189">On a new tab of your browser, type the URL to the Sales site collection.</span></span>
    
6. <span data-ttu-id="762b9-190">Klicken Sie im Ordner **Dokumente** der **Websitesammlung „Vertrieb“** auf das Dokument **VertraulicheDaten-VorIRM.docx**. </span><span class="sxs-lookup"><span data-stu-id="762b9-190">In the **Documents** folder of the **Sales site collection**, click the **SensitiveData-BeforeIRM.docx** document.</span></span>
    
    <span data-ttu-id="762b9-191">Sie sollten den Inhalt sehen können.</span><span class="sxs-lookup"><span data-stu-id="762b9-191">You should see its contents.</span></span>
    
7. <span data-ttu-id="762b9-192">Schließen Sie die Registerkarten **Dokumente** und **Websitesammlung „Vertrieb“**.</span><span class="sxs-lookup"><span data-stu-id="762b9-192">Close the **Documents** and **Sales site collection** tabs.</span></span>
    
<span data-ttu-id="762b9-193">Indem der CEO das Dokument „VertraulicheDaten-VorIRM.docx“ versehentlich in der Websitesammlung „Vertrieb“ veröffentlicht hat, hat er die Berechtigungssicherheit der Websitesammlung „Führungskräfte“ umgangen.</span><span class="sxs-lookup"><span data-stu-id="762b9-193">By accidentally posting the SensitiveData-BeforeIRM.docx document on the Sales site collection, the CEO bypassed the permissions security of the Executives site collection.</span></span>
  
<span data-ttu-id="762b9-194">Um Office 365 für die Phasen 3 und 4 vorzubereiten, aktivieren Sie IRM für SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="762b9-194">To prepare Office 365 for Phases 3 and 4, enable IRM for SharePoint Online.</span></span>
  
1. <span data-ttu-id="762b9-195">Klicken Sie auf der Registerkarte der **Microsoft Office-Startseite** auf das Benutzersymbol in der oberen rechten Ecke, und klicken Sie dann auf **Abmelden**.</span><span class="sxs-lookup"><span data-stu-id="762b9-195">On the **Microsoft Office Home** tab, click the user icon in the upper-right, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="762b9-196">Wechseln Sie zu [https://admin.microsoft.com](https://admin.microsoft.com).</span><span class="sxs-lookup"><span data-stu-id="762b9-196">Go to [https://admin.microsoft.com](https://admin.microsoft.com).</span></span>
    
3. <span data-ttu-id="762b9-197">Klicken Sie auf der **Office 365-Anmeldeseite** auf den Namen des globalen Administratorkontos, geben Sie das Kennwort ein, und klicken Sie dann auf **Anmelden**.</span><span class="sxs-lookup"><span data-stu-id="762b9-197">On the **Office 365 sign in** page, click the global administrator account name, type its password, and then click **Sign in**.</span></span>
    
4. <span data-ttu-id="762b9-198">Klicken Sie auf der Registerkarte der **Microsoft Office-Startseite** auf **Admin > Admin Center > SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="762b9-198">On the **Microsoft Office Home** tab, click **Admin > Admin centers > SharePoint**.</span></span>
    
5. <span data-ttu-id="762b9-199">Klicken Sie auf der Registerkarte **SharePoint Admin Center** auf **Einstellungen**.</span><span class="sxs-lookup"><span data-stu-id="762b9-199">On the **SharePoint admin center** tab, click **Settings**.</span></span>
    
6. <span data-ttu-id="762b9-200">Wählen Sie auf der Seite im Abschnitt **Verwaltung von Informationsrechten (IRM)** **die Option in der Konfiguration angegebene IRM-Dienst verwenden**aus, und wählen Sie dann **IRM-Einstellungen aktualisieren**aus.</span><span class="sxs-lookup"><span data-stu-id="762b9-200">On the page, in the **Information Rights Management (IRM)** section, select **Use the IRM service specified in your configuration**, and then select **Refresh IRM Settings**.</span></span>
    
7. <span data-ttu-id="762b9-201">Schließen Sie die Registerkarte **SharePoint Admin Center**.</span><span class="sxs-lookup"><span data-stu-id="762b9-201">Close the **SharePoint admin center** tab.</span></span>
    
## <a name="phase-3-use-sharepoint-information-rights-management-with-an-office-365-private-group"></a><span data-ttu-id="762b9-202">Phase 3: Verwenden von SharePoint Information Rights Management mit einer privaten Office 365-Gruppe</span><span class="sxs-lookup"><span data-stu-id="762b9-202">Phase 3: Use SharePoint Information Rights Management with an Office 365 private group</span></span>

<span data-ttu-id="762b9-203">In dieser Phase verwenden Sie SharePoint Information Rights Management mit einer privaten Office 365-Gruppe, um den Zugriff auf ein Dokument mit vertraulichen Informationen auch dann zu schützen, wenn es auf einer Website mit offenen Berechtigungen veröffentlicht wird.</span><span class="sxs-lookup"><span data-stu-id="762b9-203">In this phase, you use SharePoint Information Rights Management with an Office 365 private group to protect access to a document with sensitive information, even when it is posted on a site with open permissions.</span></span>
  
<span data-ttu-id="762b9-204">Als Erstes aktivieren und konfigurieren Sie IRM für die Dokumentbibliothek der Websitesammlung „Führungskräfte“. </span><span class="sxs-lookup"><span data-stu-id="762b9-204">First, you enable and configure IRM for the documents library of the Executives site collection.</span></span> 
  
1. <span data-ttu-id="762b9-205">Geben Sie auf einer neuen Registerkarte Ihres Browsers die URL der Websitesammlung "Führungskräfte" ein.</span><span class="sxs-lookup"><span data-stu-id="762b9-205">On a new tab of your browser, type the URL to the Executives site collection.</span></span>
    
2. <span data-ttu-id="762b9-206">Klicken Sie auf **Dokumente**.</span><span class="sxs-lookup"><span data-stu-id="762b9-206">Click **Documents**.</span></span>
    
3. <span data-ttu-id="762b9-207">Klicken Sie in der oberen rechten Ecke auf das Einstellungssymbol, und klicken Sie dann auf **Bibliothekseinstellungen**.</span><span class="sxs-lookup"><span data-stu-id="762b9-207">In the upper-right, click the settings icon, and then click **Library settings**.</span></span>
    
4. <span data-ttu-id="762b9-208">Klicken Sie auf der Seite **Einstellungen** unter **Berechtigungen und Verwaltung** auf **Information Rights Management**.</span><span class="sxs-lookup"><span data-stu-id="762b9-208">On the **Settings** page, under **Permissions and Management**, click **Information Rights Management**.</span></span>
    
5. <span data-ttu-id="762b9-209">Gehen Sie auf der Seite **Einstellungen für Information Rights Management** wie folgt vor:</span><span class="sxs-lookup"><span data-stu-id="762b9-209">On the **Information Rights Management Settings** page:</span></span>
    
  - <span data-ttu-id="762b9-210">Wählen Sie **Berechtigungen für Dokumente in dieser Bibliothek beim Herunterladen einschränken** aus.</span><span class="sxs-lookup"><span data-stu-id="762b9-210">Select **Restrict permission to documents in this library on download**.</span></span>
    
  - <span data-ttu-id="762b9-211">Geben Sie unter **Berechtigungsrichtlinientitel erstellen** den Text **Führungskräfte** ein.</span><span class="sxs-lookup"><span data-stu-id="762b9-211">For **Create a permission policy title**, type **Executives**.</span></span>
    
  - <span data-ttu-id="762b9-212">Geben Sie unter **Beschreibung der Berechtigungsrichtlinie hinzufügen** den Text **IRM für Führungskräfte** ein.</span><span class="sxs-lookup"><span data-stu-id="762b9-212">For **Add a permission policy description**, type **IRM for executives**.</span></span>
    
6. <span data-ttu-id="762b9-213">Klicken Sie auf **Optionen anzeigen**.</span><span class="sxs-lookup"><span data-stu-id="762b9-213">Click **Show Options**.</span></span>
    
7. <span data-ttu-id="762b9-214">Wählen Sie unter **Zusätzliche IRM-Bibliothekseinstellungen festlegen** die Option **Benutzer dürfen keine Dokumente hochladen, die IRM nicht unterstützen**.</span><span class="sxs-lookup"><span data-stu-id="762b9-214">Under **Set additional IRM library settings**, select **Do not allow users to upload documents that do not support IRM**.</span></span>
    
8. <span data-ttu-id="762b9-215">Wählen Sie unter **Dokumentzugriffsrechte konfigurieren** die Optionen **Drucken durch anzeigende Benutzer zulassen** und **Anzeigenden Benutzern das Schreiben in einer Kopie des heruntergeladenen Dokuments gestatten**.</span><span class="sxs-lookup"><span data-stu-id="762b9-215">Under **Configure document access rights**, select **Allow viewers to print** and **Allow viewers to write on a copy of the downloaded document**.</span></span>
    
9. <span data-ttu-id="762b9-216">Wählen Sie unter **Gruppen Schutz und Anmeldeinformationen Intervall festlegen**die Option **Gruppen Schutz zulassen aus. Standardgruppe**, und geben Sie dann **Führungskräfte**ein.</span><span class="sxs-lookup"><span data-stu-id="762b9-216">Under **Set group protection and credentials interval**, select **Allow group protection. Default group**, and then type **Executives**.</span></span>
    
10. <span data-ttu-id="762b9-217">Klicken Sie auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="762b9-217">Click **OK**.</span></span>
    
<span data-ttu-id="762b9-218">Im nächsten Schritt fungieren Sie als CEO und laden ein neues Dokument in den Dokumentordner „Führungskräfte“ hoch. Dann laden Sie das Dokument herunter und laden es versehentlich in den Dokumentordner „Vertrieb“ hoch.</span><span class="sxs-lookup"><span data-stu-id="762b9-218">Next, acting as the CEO, you upload a new document to the Executives document folder, download it, then accidentally upload it to the Sales document folder.</span></span>
  
1. <span data-ttu-id="762b9-219">Öffnen Sie den lokalen Ordner, in dem Sie das Dokument **VertraulicheDaten-VorIRM.docx** gespeichert haben.</span><span class="sxs-lookup"><span data-stu-id="762b9-219">Open the local folder where you stored the **SensitiveData-BeforeIRM.docx** document.</span></span>
    
2. <span data-ttu-id="762b9-220">	Klicken Sie mit der rechten Maustaste auf *\*VertraulicheDaten-VorIRM.docx*\*, und klicken Sie dann auf *\*Kopieren*\*.</span><span class="sxs-lookup"><span data-stu-id="762b9-220">Right-click **SensitiveData-BeforeIRM.docx**, and then click **Copy**.</span></span>
    
3. <span data-ttu-id="762b9-221">Klicken Sie mit der rechten Maustaste in den Ordner, und klicken Sie dann auf **Einfügen**.</span><span class="sxs-lookup"><span data-stu-id="762b9-221">Right-click within the folder, and then click **Paste**.</span></span>
    
4. <span data-ttu-id="762b9-222">Benennen Sie die neue **vertraulichedaten-BeforeIRM-Copy. docx-** Datei in **Dokument vertraulichedaten-nachirm. docx**um.</span><span class="sxs-lookup"><span data-stu-id="762b9-222">Rename the new **SensitiveData-BeforeIRM - Copy.docx** file to **SensitiveData-AfterIRM.docx**.</span></span>
    
5. <span data-ttu-id="762b9-223">Klicken Sie auf der Registerkarte der **Microsoft Office-Startseite** in Ihrem Browser auf das Benutzersymbol in der oberen rechten Ecke, und klicken Sie dann auf **Abmelden**.</span><span class="sxs-lookup"><span data-stu-id="762b9-223">From the **Microsoft Office Home** tab in your browser, click the user icon in the upper-right, and then click **Sign out**.</span></span>
    
6. <span data-ttu-id="762b9-224">Wechseln Sie zu [https://admin.microsoft.com](https://admin.microsoft.com).</span><span class="sxs-lookup"><span data-stu-id="762b9-224">Go to [https://admin.microsoft.com](https://admin.microsoft.com).</span></span>
    
7. <span data-ttu-id="762b9-225">Klicken Sie auf der **Office 365-Anmeldeseite** auf den Namen des CEO-Kontos, geben Sie das Kennwort ein, und klicken Sie dann auf **Anmelden**.</span><span class="sxs-lookup"><span data-stu-id="762b9-225">On the **Office 365 sign in** page, click the CEO account name, type its password, and then click **Sign in**.</span></span>
    
8. <span data-ttu-id="762b9-226">Geben Sie auf einer neuen Registerkarte Ihres Browsers die URL der Websitesammlung "Führungskräfte" ein.</span><span class="sxs-lookup"><span data-stu-id="762b9-226">On a new tab of your browser, type the URL to the Executives site collection.</span></span>
    
9. <span data-ttu-id="762b9-227">Klicken Sie auf der Seite **Dokumente** auf **Hochladen**, geben Sie das Dokument **VertraulicheDaten-NachIRM.docx** im lokalen Ordner an, und klicken Sie dann auf **Öffnen**.</span><span class="sxs-lookup"><span data-stu-id="762b9-227">On the **Documents** page, click **Upload**, specify the **SensitiveData-AfterIRM.docx** document in your local folder, and then click **Open**.</span></span>
    
10. <span data-ttu-id="762b9-228">Wählen Sie das neue Dokument **VertraulicheDaten-NachIRM.docx** auf der Seite **Dokumente** aus, klicken Sie auf die Ellipse (…) in der Menüleiste, und klicken Sie dann auf **Herunterladen**.</span><span class="sxs-lookup"><span data-stu-id="762b9-228">Select the new **SensitiveData-AfterIRM.docx** document in the **Documents** page, click the ellipsis (…) in the menu bar, and then click **Download**.</span></span>
    
11. <span data-ttu-id="762b9-229">Wenn Sie dazu aufgefordert werden, speichern Sie das Dokument **VertraulicheDaten-NachIRM.docx** in Ihrem lokalen Ordner, und überschreiben Sie dabei die ursprüngliche Version.</span><span class="sxs-lookup"><span data-stu-id="762b9-229">When prompted, save the **SensitiveData-AfterIRM.docx** document in your local folder, overwriting the original version.</span></span>
    
12. <span data-ttu-id="762b9-230">Schließen Sie die Registerkarte der Seite **Dokumente**.</span><span class="sxs-lookup"><span data-stu-id="762b9-230">Close the tab for the **Documents** page.</span></span>
    
13. <span data-ttu-id="762b9-231">Geben Sie auf einer neuen Registerkarte Ihres Browsers die URL der Websitesammlung "Vertrieb" ein.</span><span class="sxs-lookup"><span data-stu-id="762b9-231">On a new tab of your browser, type the URL to the Sales site collection.</span></span>
    
14. <span data-ttu-id="762b9-232">Klicken Sie auf **Dokumente**.</span><span class="sxs-lookup"><span data-stu-id="762b9-232">Click **Documents**.</span></span>
    
15. <span data-ttu-id="762b9-233">Klicken Sie auf der Seite **Dokumente** auf **Hochladen**, geben Sie das Dokument **VertraulicheDaten-NachIRM.docx** im lokalen Ordner an, und klicken Sie dann auf **Öffnen**.</span><span class="sxs-lookup"><span data-stu-id="762b9-233">On the **Documents** page, click **Upload**, specify the **SensitiveData-AfterIRM.docx** document in your local folder, and then click **Open**.</span></span>
    
16. <span data-ttu-id="762b9-234">Schließen Sie die **Websitesammlung „Vertrieb“** und die Registerkarten von **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="762b9-234">Close the **Sales site collection** and **SharePoint** tabs.</span></span>
    
<span data-ttu-id="762b9-235">Als Nächstes fungieren Sie als normaler Benutzer und versuchen, auf das Dokument **VertraulicheDaten-NachIRM.docx** im Dokumentordner „Vertrieb“ zuzugreifen.</span><span class="sxs-lookup"><span data-stu-id="762b9-235">Next, acting as a normal user, you try to access the **SensitiveData-AfterIRM.docx** document in the Sales document folder.</span></span>
  
1. <span data-ttu-id="762b9-236">Klicken Sie auf der Registerkarte der **Microsoft Office-Startseite** in Ihrem Browser auf das Benutzersymbol in der oberen rechten Ecke, und klicken Sie dann auf **Abmelden**.</span><span class="sxs-lookup"><span data-stu-id="762b9-236">From the **Microsoft Office Home** tab in your browser, click the user icon in the upper-right, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="762b9-237">Wechseln Sie zu [https://admin.microsoft.com](https://admin.microsoft.com).</span><span class="sxs-lookup"><span data-stu-id="762b9-237">Go to [https://admin.microsoft.com](https://admin.microsoft.com).</span></span>
    
3. <span data-ttu-id="762b9-238">Klicken Sie auf der **Office 365 Anmelde** Seite auf den Kontonamen des Namen, geben Sie das Kennwort ein, und klicken Sie dann auf **Anmelden**.</span><span class="sxs-lookup"><span data-stu-id="762b9-238">On the **Office 365 sign in** page, click the User5 account name, type its password, and then click **Sign in**.</span></span>
    
4. <span data-ttu-id="762b9-239">Geben Sie auf einer neuen Registerkarte Ihres Browsers die URL der Websitesammlung "Vertrieb" ein.</span><span class="sxs-lookup"><span data-stu-id="762b9-239">On a new tab of your browser, type the URL to the Sales site collection.</span></span>
    
5. <span data-ttu-id="762b9-240">Klicken Sie auf **Dokumente**.</span><span class="sxs-lookup"><span data-stu-id="762b9-240">Click **Documents**.</span></span>
    
6. <span data-ttu-id="762b9-241">Öffnen Sie auf der Seite **Dokumente** das Dokument **VertraulicheDaten-NachIRM.docx**. </span><span class="sxs-lookup"><span data-stu-id="762b9-241">On the **Documents** page, open the **SensitiveData-AfterIRM.docx** document.</span></span>
    
    <span data-ttu-id="762b9-242">Es sollte eine Meldung angezeigt werden, die besagt, "Sorry, Word kann dieses Dokument nicht öffnen, da es durch Information Rights Management (IRM) geschützt ist."</span><span class="sxs-lookup"><span data-stu-id="762b9-242">You should see a message that states, "Sorry, Word can't open this document because it's protected by Information Rights Management (IRM)."</span></span> 
    
7. <span data-ttu-id="762b9-p105">Klicken Sie auf **In Word bearbeiten**. Sie werden gefragt, ob Sie die Datei öffnen möchten. Klicken Sie auf **Ja**.</span><span class="sxs-lookup"><span data-stu-id="762b9-p105">Click **Edit in Word**. You are prompted if you want to open the file. Click **Yes**.</span></span>
    
8. <span data-ttu-id="762b9-p106">Sie werden aufgefordert, sich anzumelden. Geben Sie den Namen des Kontos für Benutzer 5 an, und klicken Sie auf **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="762b9-p106">You are prompted to sign-in. Type the account name of the User5 account, and then click **Next**.</span></span>
    
9. <span data-ttu-id="762b9-p107">Sie werden aufgefordert, das Kennwort einzugeben. Geben Sie das Kennwort für das Konto von Benutzer 5 ein, und klicken Sie dann auf **Anmelden**. </span><span class="sxs-lookup"><span data-stu-id="762b9-p107">You are prompted to provide the password. Type the password for the User5 account and then click **Sign in**.</span></span> 
    
    <span data-ttu-id="762b9-250">Es sollte eine Nachricht angezeigt werden, die besagt, dass Sie keine Anmeldedaten haben, die Sie zum Öffnen dieses Dokuments berechtigen.</span><span class="sxs-lookup"><span data-stu-id="762b9-250">You should see the a message that states: "You do not have the credentials that allow you to open this document."</span></span>
    
10. <span data-ttu-id="762b9-251">Klicken Sie auf **Nein**.</span><span class="sxs-lookup"><span data-stu-id="762b9-251">Click **No**.</span></span>
    
<span data-ttu-id="762b9-p108">Eine andere Möglichkeit zum Anzeigen des IRM-Schutzes besteht darin, die Dateien im lokalen Ordner anzusehen. Die Datei **VertraulicheDaten-NachIRM.docx** sollte sehr viel größer sein als die Datei **VertraulicheDaten-VorIRM.docx**. Die Datei **VertraulicheDaten-NachIRM.docx** ist verschlüsselt, und sie enthält die Informationen zum IRM-Schutz.</span><span class="sxs-lookup"><span data-stu-id="762b9-p108">Another way to see the IRM protection is to look at the files in your local folder. The **SensitiveData-AfterIRM.docx** should be much larger than the **SensitiveData-BeforeIRM.docx** file. The **SensitiveData-AfterIRM.docx** file is encrypted and has the IRM protection information added to it.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="762b9-255">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="762b9-255">See Also</span></span>

[<span data-ttu-id="762b9-256">Testumgebungsanleitungen (TLGs) zur Cloudakzeptanz</span><span class="sxs-lookup"><span data-stu-id="762b9-256">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="762b9-257">Basiskonfiguration der Entwicklungs-/Testumgebung</span><span class="sxs-lookup"><span data-stu-id="762b9-257">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="762b9-258">Office 365-Entwicklungs-/Testumgebung</span><span class="sxs-lookup"><span data-stu-id="762b9-258">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="762b9-259">Cloudakzeptanz und Hybridlösungen</span><span class="sxs-lookup"><span data-stu-id="762b9-259">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)


