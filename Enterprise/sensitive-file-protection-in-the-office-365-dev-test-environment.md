---
title: Schutz vertraulicher Dateien in Office 365-Entwicklungs-/-Testumgebungen
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: 27ecff45-06a6-4629-bc45-9dab4eef3a21
description: "Zusammenfassung: Konfigurieren Sie und veranschaulichen Sie, wie Office 365 Information Rights Management sensiblen Dateien schützt, auch wenn sie in der falschen SharePoint Online-Websitesammlung bereitgestellt werden."
ms.openlocfilehash: 236272a90bb6ff7f310c95f1494b68750e363f40
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2018
---
# <a name="sensitive-file-protection-in-the-office-365-devtest-environment"></a><span data-ttu-id="2cc82-103">Schutz vertraulicher Dateien in Office 365-Entwicklungs-/-Testumgebungen</span><span class="sxs-lookup"><span data-stu-id="2cc82-103">Sensitive file protection in the Office 365 dev/test environment</span></span>

 <span data-ttu-id="2cc82-104">**Zusammenfassung:** Konfigurieren Sie und veranschaulichen Sie, wie Office 365 Information Rights Management sensiblen Dateien schützt, auch wenn sie in der falschen SharePoint Online-Websitesammlung bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="2cc82-104">**Summary:** Configure and demonstrate how Office 365 Information Rights Management protects your sensitive files, even when they are posted to the wrong SharePoint Online site collection.</span></span>
  
<span data-ttu-id="2cc82-p101">Information Rights Management (IRM) in Office 365 umfasst eine Reihe von Funktionen zum Schutz von Dokumenten, die aus SharePoint Online-Bibliotheken und -Listen heruntergeladen werden. Heruntergeladene Dateien sind verschlüsselt und verfügen über die Berechtigungen zum Öffnen, Kopieren, Speichern und Drucken, welche der SharePoint Online-Bibliothek entsprechen, in der sie gespeichert sind.</span><span class="sxs-lookup"><span data-stu-id="2cc82-p101">Information Rights Management (IRM) in Office 365 is a set of capabilities to protect documents that are downloaded from SharePoint Online libraries and lists. Downloaded files are encrypted and contain the open, copy, save, and print permissions that reflect the SharePoint Online library in which they were stored.</span></span>
  
<span data-ttu-id="2cc82-107">Mithilfe der Anleitungen in diesem Artikel können Sie IRM in Office 365 für Dateien aktivieren und testen, die in Ihrem Office 365-Testabonnement möglicherweise vertrauliche Informationen enthalten.</span><span class="sxs-lookup"><span data-stu-id="2cc82-107">With the instructions in this article, you enable and test IRM in Office 365 for files containing possible sensitive information in your Office 365 trial subscription.</span></span>
  
> [!TIP]
> <span data-ttu-id="2cc82-108">Klicken Sie [hier](http://aka.ms/catlgstack), um eine visuelle Darstellung aller Artikel im Stapel der Testumgebungsanleitungen in der Microsoft Cloud zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="2cc82-108">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-build-out-your-office-365-devtest-environment"></a><span data-ttu-id="2cc82-109">Phase 1: Erstellen Ihrer Office 365-Entwicklungs-/Testumgebung</span><span class="sxs-lookup"><span data-stu-id="2cc82-109">Phase 1: Build out your Office 365 dev/test environment</span></span>

<span data-ttu-id="2cc82-110">Wenn Sie vertrauliche Dateischutz auf einfache Weise mit den Mindestanforderungen testen möchten, befolgen Sie die Anweisungen in Phasen 2 und 3 von [Office 365 Dev/Test Environment](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="2cc82-110">If you just want to test sensitive file protection in a lightweight way with the minimum requirements, follow the instructions in phases 2 and 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="2cc82-111">Wenn Sie vertrauliche Dateischutz in einer simulierten Enterprise testen möchten, befolgen Sie die Anweisungen in [DirSync für Ihre Office 365 Dev/Test-Umgebung](dirsync-for-your-office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="2cc82-111">If you want to test sensitive file protection in a simulated enterprise, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="2cc82-p102">Für das Testen des Schutzes vertraulicher Dateien ist keine simulierte Unternehmensentwicklungs-/-testumgebung erforderlich, die ein simuliertes Intranet, das mit dem Internet verbunden ist, und die Verzeichnissynchronisierung für eine Windows Server Active Directory-Gesamtstruktur umfasst. Dies wird hier als Option bereitgestellt, damit Sie den Schutz vertraulicher Dateien testen und damit in einer Umgebung, die eine typische Organisation darstellt, experimentieren können.</span><span class="sxs-lookup"><span data-stu-id="2cc82-p102">Testing sensitive file protection does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for a Windows Server AD forest. It is provided here as an option so that you can test sensitive file protection and experiment with it in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-demonstrate-how-documents-from-permissions-protected-sites-can-be-leaked"></a><span data-ttu-id="2cc82-114">Phase 2: Demonstriert, wie Dokumente von Websites, die durch Berechtigungen geschützt sind, anderweitig (und möglicherweise missbräuchlich) verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="2cc82-114">Phase 2: Demonstrate how documents from permissions-protected sites can be leaked</span></span>

<span data-ttu-id="2cc82-115">In dieser Phase demonstrieren Sie, wie jemand ein Dokument von einer Website, die durch Berechtigungen geschützt ist, herunterladen und anschließend auf eine Website hochladen kann, die nicht auf diese Weise geschützt und entsprechend allgemein zugänglich ist.</span><span class="sxs-lookup"><span data-stu-id="2cc82-115">In this phase, you demonstrate that someone can download a document from a permissions-protected site and then upload it to a site that has wide-open permissions.</span></span>
  
<span data-ttu-id="2cc82-116">Sie fügen zuerst drei neue Benutzerkonten für Führungskräfte hinzu und weisen diesen Office 365 E5-Lizenzen zu.</span><span class="sxs-lookup"><span data-stu-id="2cc82-116">First, you add three new user accounts that represent executives and assign them Office 365 E5 licenses.</span></span>
  
<span data-ttu-id="2cc82-117">Verwenden Sie die Anweisungen in [Verbindung mit Office 365 PowerShell herstellen](https://technet.microsoft.com/library/dn975125.aspx) , installieren Sie die PowerShell-Module (falls erforderlich) und eine Verbindung herstellen, um das neue Office 365-Abonnement aus:</span><span class="sxs-lookup"><span data-stu-id="2cc82-117">Use the instructions in [Connect to Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx) to install the PowerShell modules (if needed) and connect to your new Office 365 subscription from:</span></span>
  
- <span data-ttu-id="2cc82-118">Ihrem Computer aus (für die einfache Office 365-Entwicklungs-/Testunternehmensumgebung).</span><span class="sxs-lookup"><span data-stu-id="2cc82-118">Your computer (for the lightweight Office 365 dev/test environment).</span></span>
    
- <span data-ttu-id="2cc82-119">Dem virtuellen Computer CLIENT1 aus (für die simulierte Office 365-Entwicklungs-/Testumgebung).</span><span class="sxs-lookup"><span data-stu-id="2cc82-119">The CLIENT1 virtual machine (for the simulated enterprise Office 365 dev/test environment).</span></span>
    
<span data-ttu-id="2cc82-120">Geben Sie im Dialogfeld **Windows PowerShell anmelden** den Namen der Office 365 globaler Administrator (Beispiel: jdoe@contosotoycompany.onmicrosoft.com) und das Kennwort für Ihr trial Office 365-Abonnement.</span><span class="sxs-lookup"><span data-stu-id="2cc82-120">In the **Windows PowerShell Credential Request** dialog box, type the Office 365 global administrator name (example: jdoe@contosotoycompany.onmicrosoft.com) and password of your Office 365 trial subscription.</span></span>
  
<span data-ttu-id="2cc82-121">Geben Sie den Namen der Organisation (zum Beispiel „contosotoycompany“) und den zweistelligen Ländercode für Ihren Standort ein. Führen Sie dann über die „Windows Azure Active Directory-Modul für Windows PowerShell“-Eingabeaufforderung die folgenden Befehle aus:</span><span class="sxs-lookup"><span data-stu-id="2cc82-121">Fill in your organization name (example: contosotoycompany) and the two-character country code for your location, and then run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$orgName="<organization name>"
$loc="<two-character country code, such as US>"
$licAssignment= $orgName + ":ENTERPRISEPREMIUM"
$userName= "ceo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "CEO" -FirstName "Chief" -LastName "Executive Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

<span data-ttu-id="2cc82-122">Beachten Sie aus der Anzeige des Befehls **New-MsolUser** das generierte Kennwort für das Konto CEO, und tragen sie Sie an einem sicheren Ort.</span><span class="sxs-lookup"><span data-stu-id="2cc82-122">From the display of the **New-MsolUser** command, note the generated password for the CEO account and record it in a safe location.</span></span>
  
<span data-ttu-id="2cc82-123">Führen Sie über die „Windows Azure Active Directory-Modul für Windows PowerShell“-Eingabeaufforderung die folgenden Befehle aus:</span><span class="sxs-lookup"><span data-stu-id="2cc82-123">Run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$userName= "cfo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "CFO" -FirstName "Chief" -LastName "Financial Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

<span data-ttu-id="2cc82-124">Beachten Sie aus der Anzeige des Befehls **New-MsolUser** das generierte Kennwort für das Konto Leiter der Finanzabteilung, und tragen sie Sie an einem sicheren Ort.</span><span class="sxs-lookup"><span data-stu-id="2cc82-124">From the display of the **New-MsolUser** command, note the generated password for the CFO account and record it in a safe location.</span></span>
  
<span data-ttu-id="2cc82-125">Führen Sie über die „Windows Azure Active Directory-Modul für Windows PowerShell“-Eingabeaufforderung die folgenden Befehle aus:</span><span class="sxs-lookup"><span data-stu-id="2cc82-125">Run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$userName= "coo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "COO" -FirstName "Chief" -LastName "Operations Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

<span data-ttu-id="2cc82-126">Beachten Sie aus der Anzeige des Befehls **New-MsolUser** das generierte Kennwort für das Konto COO, und tragen sie Sie an einem sicheren Ort.</span><span class="sxs-lookup"><span data-stu-id="2cc82-126">From the display of the **New-MsolUser** command, note the generated password for the COO account and record it in a safe location.</span></span>
  
<span data-ttu-id="2cc82-127">Im nächsten Schritt erstellen Sie eine private Führungskräftegruppe und fügen dieser die neuen Führungskräftekonten hinzu.</span><span class="sxs-lookup"><span data-stu-id="2cc82-127">Next, you create a private Executives group and add the new executive accounts to it.</span></span>
  
1. <span data-ttu-id="2cc82-128">In Ihrem Browser wechseln Sie zu der Office-Portal unter [http://portal.office.com](http://portal.office.com) , und melden Sie sich Test Office 365-Abonnement mit Ihrer globalen Administratorkonto an.</span><span class="sxs-lookup"><span data-stu-id="2cc82-128">In your browser, go to the Office portal at [http://portal.office.com](http://portal.office.com) and sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
  - <span data-ttu-id="2cc82-129">Wenn Sie die einfache Office 365-Entwicklungs-/Testumgebung verwenden, öffnen Sie eine private Sitzung in Internet Explorer bzw. in dem von Ihnen bevorzugten Browser, und melden Sie sich von Ihrem lokalen Computer aus an.</span><span class="sxs-lookup"><span data-stu-id="2cc82-129">If you are using the lightweight Office 365 dev/test environment, open a private session of Internet Explorer or your browser and sign in from your local computer.</span></span>
    
  - <span data-ttu-id="2cc82-130">Wenn Sie die simulierte Office 365-Unternehmensentwicklungs-/-testumgebung verwenden, verwenden Sie das Azure-Portal, um sich mit dem virtuellen Computer CLIENT1 zu verbinden, und melden Sie sich dann von CLIENT1 aus an.</span><span class="sxs-lookup"><span data-stu-id="2cc82-130">If you are using the simulated enterprise Office 365 dev/test environment, use the Azure portal to connect to the CLIENT1 virtual machine, and then sign in from CLIENT1.</span></span>
    
2. <span data-ttu-id="2cc82-131">Klicken Sie auf der Registerkarte **Start von Microsoft Office** auf **Admin > Gruppen > Gruppen**, und klicken Sie dann auf **Gruppe hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="2cc82-131">On the **Microsoft Office Home** tab, click **Admin > Groups > Groups**, and then click **Add a group**.</span></span>
    
3. <span data-ttu-id="2cc82-132">Wählen Sie in **einer Gruppe hinzufügen** **Office 365-Gruppe** für die Gruppe, geben **Führungskräfte** in **Name** und **Gruppen-Id**, wählen Sie **Private** für **private**, und klicken Sie dann auf **Besitzer auswählen**.</span><span class="sxs-lookup"><span data-stu-id="2cc82-132">In **Add a group**, select **Office 365 group** for the group type, type **Executives** in **Name** and **Group Id**, select **Private** for **Privacy**, and then click **Select Owner**.</span></span>
    
4. <span data-ttu-id="2cc82-133">Klicken Sie in der Liste auf den Namen Ihres globalen Administratorkontos.</span><span class="sxs-lookup"><span data-stu-id="2cc82-133">In the list, click your global administrator account name.</span></span>
    
5. <span data-ttu-id="2cc82-134">Klicken Sie auf **Hinzufügen**, und klicken Sie dann auf **Schließen**.</span><span class="sxs-lookup"><span data-stu-id="2cc82-134">Click **Add**, and then click **Close**.</span></span>
    
6. <span data-ttu-id="2cc82-135">Klicken Sie in der Gruppenliste auf **Führungskräfte**.</span><span class="sxs-lookup"><span data-stu-id="2cc82-135">In the groups list, click **Executives**.</span></span>
    
7. <span data-ttu-id="2cc82-136">Klicken Sie auf **Bearbeiten der Mitglieder**.</span><span class="sxs-lookup"><span data-stu-id="2cc82-136">Click **Edit for Members**.</span></span>
    
8. <span data-ttu-id="2cc82-p103">Klicken Sie auf **Mitglieder hinzufügen**. Wählen Sie die folgenden Benutzerkonten in der Liste Member:</span><span class="sxs-lookup"><span data-stu-id="2cc82-p103">Click **Add members**. In the member list, select the following user accounts:</span></span>
    
  - <span data-ttu-id="2cc82-139">Chief Executive Officer</span><span class="sxs-lookup"><span data-stu-id="2cc82-139">Chief Executive Officer</span></span>
    
  - <span data-ttu-id="2cc82-140">Chief Financial Officer</span><span class="sxs-lookup"><span data-stu-id="2cc82-140">Chief Financial Officer</span></span>
    
  - <span data-ttu-id="2cc82-141">Chief Operations Officer</span><span class="sxs-lookup"><span data-stu-id="2cc82-141">Chief Operations Officer</span></span>
    
9. <span data-ttu-id="2cc82-142">Klicken Sie auf **Speichern**, und klicken Sie dann auf **Schließen**.</span><span class="sxs-lookup"><span data-stu-id="2cc82-142">Click **Save**, and then click **Close**.</span></span>
    
10. <span data-ttu-id="2cc82-143">Schließen Sie die Registerkarte **Office-Verwaltungskonsole** .</span><span class="sxs-lookup"><span data-stu-id="2cc82-143">Close the **Office Admin center** tab.</span></span>
    
<span data-ttu-id="2cc82-144">Im nächsten Schritt erstellen Sie eine Websitesammlung für Führungskräfte und erlauben nur den Mitgliedern der Führungskräftegruppe den Zugriff darauf.</span><span class="sxs-lookup"><span data-stu-id="2cc82-144">Next, you create an Executives site collection and allow just the members of the Executives group to access it.</span></span>
  
1. <span data-ttu-id="2cc82-145">Klicken Sie auf der Registerkarte **Microsoft Office Home** auf die Kachel " **Admin** ".</span><span class="sxs-lookup"><span data-stu-id="2cc82-145">On the **Microsoft Office Home** tab, click the **Admin** tile.</span></span>
    
2. <span data-ttu-id="2cc82-146">Klicken Sie auf die Registerkarte **Office Admin Center** auf **Zentriert Admin > SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="2cc82-146">On the **Office Admin center** tab, click **Admin centers > SharePoint**.</span></span>
    
3. <span data-ttu-id="2cc82-147">Klicken Sie auf der Registerkarte **SharePoint Administrationscenter** auf **Neu > Private Websitesammlung**.</span><span class="sxs-lookup"><span data-stu-id="2cc82-147">On the **SharePoint admin center** tab, click **New > Private site collection**.</span></span>
    
4. <span data-ttu-id="2cc82-148">Im Bereich Auflistung neue Website geben **Führungskräfte** **Titel**, Führungskräfte in das Feld URL Geben Sie den Namen des globalen Administratorkontos in **Administrator**aus, und klicken Sie dann auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="2cc82-148">In the new site collection pane, type **Executives** in **Title**, executives in the URL box, specify the name of your global administrator account in **Administrator**, and then click **OK**.</span></span>
    
5. <span data-ttu-id="2cc82-p104">Warten Sie, bis die neue Websitesammlung erstellt wurde. Nach Abschluss des Vorgangs, kopieren Sie die URL der neuen Websitesammlung Führungskräfte, und fügen Sie ihn in eine neue Registerkarte Ihres Browsers.</span><span class="sxs-lookup"><span data-stu-id="2cc82-p104">Wait until the new site collection has been created. When complete, copy the URL of the new Executives site collection and paste it into a new tab of your browser.</span></span>
    
6. <span data-ttu-id="2cc82-151">Klicken Sie in der oberen rechten Ecke der Websitesammlung **Führungskräfte** auf das einstellungssymbol, und klicken Sie dann auf **freigegeben für**.</span><span class="sxs-lookup"><span data-stu-id="2cc82-151">In the upper right of the **Executives** site collection, click the settings icon, and then click **Shared with**.</span></span>
    
7. <span data-ttu-id="2cc82-152">**Freigeben "Executives"**klicken Sie auf **Erweitert**.</span><span class="sxs-lookup"><span data-stu-id="2cc82-152">In **Share 'Executives'**, click **Advanced**.</span></span>
    
8. <span data-ttu-id="2cc82-153">Klicken Sie in der Liste der SharePoint-Gruppen die **Führungskräfte Elemente**auf.</span><span class="sxs-lookup"><span data-stu-id="2cc82-153">In the list of SharePoint groups, click **Executives Members**.</span></span>
    
9. <span data-ttu-id="2cc82-154">Klicken Sie auf der Seite **Benutzer und Gruppen** auf **Neu**.</span><span class="sxs-lookup"><span data-stu-id="2cc82-154">On the **People and Groups** page, click **New**.</span></span>
    
10. <span data-ttu-id="2cc82-155">Geben Sie im **freigeben "Executives"** **Führungskräfte**, klicken Sie auf die Gruppe **Führungskräfte** und klicken Sie dann auf **Freigeben**.</span><span class="sxs-lookup"><span data-stu-id="2cc82-155">In **Share 'Executives'**, type **Executives**, click the **Executives** group, and then click **Share**.</span></span>
    
11. <span data-ttu-id="2cc82-156">Schließen Sie die Registerkarte **Personen und Gruppen** .</span><span class="sxs-lookup"><span data-stu-id="2cc82-156">Close the **People and groups** tab.</span></span>
    
<span data-ttu-id="2cc82-157">Im nächsten Schritt erlauben Sie allen Gruppenmitgliedern, auf die Websitesammlung „Vertrieb“ zuzugreifen.</span><span class="sxs-lookup"><span data-stu-id="2cc82-157">Next, you allow everyone to access the Sales site collection.</span></span>
  
1. <span data-ttu-id="2cc82-158">Kopieren Sie über die Registerkarte **SharePoint Administrationscenter** die URL der Websitesammlung Sales, und fügen Sie ihn in eine neue Registerkarte Ihres Browsers.</span><span class="sxs-lookup"><span data-stu-id="2cc82-158">From the **SharePoint admin center** tab, copy the URL of the Sales site collection and paste it into a new tab of your browser..</span></span>
    
2. <span data-ttu-id="2cc82-159">Klicken Sie in der oberen rechten Ecke klicken Sie auf das einstellungssymbol, und klicken Sie dann auf **freigegeben für**.</span><span class="sxs-lookup"><span data-stu-id="2cc82-159">In the upper right, click the settings icon, and then click **Shared with**.</span></span>
    
3. <span data-ttu-id="2cc82-160">**Freigeben "Websitesammlung des Vertriebs"**klicken Sie auf **Erweitert**.</span><span class="sxs-lookup"><span data-stu-id="2cc82-160">In **Share 'Sales site collection'**, click **Advanced**.</span></span>
    
4. <span data-ttu-id="2cc82-161">Klicken Sie in der Liste der SharePoint-Gruppen auf **Sales Websitesammlung Mitglieder**.</span><span class="sxs-lookup"><span data-stu-id="2cc82-161">In the list of SharePoint groups, click **Sales site collection Members**.</span></span>
    
5. <span data-ttu-id="2cc82-162">Klicken Sie auf der Seite **Benutzer und Gruppen** auf **Neu**.</span><span class="sxs-lookup"><span data-stu-id="2cc82-162">On the **People and Groups** page, click **New**.</span></span>
    
6. <span data-ttu-id="2cc82-163">Geben Sie im **freigeben 'Websitesammlung des Vertriebs'** **jeder** **Person mit Ausnahme von externen Benutzern**auf, und klicken Sie dann auf **Freigeben**.</span><span class="sxs-lookup"><span data-stu-id="2cc82-163">In **Share 'Sales site collection'**, type **Everyone**, click **Everyone except external users**, and then click **Share**.</span></span>
    
7. <span data-ttu-id="2cc82-164">Schließen Sie die Registerkarten **Sales-Websitesammlung** und **SharePoint** .</span><span class="sxs-lookup"><span data-stu-id="2cc82-164">Close the **Sales site collection** and **SharePoint** tabs.</span></span>
    
<span data-ttu-id="2cc82-165">Als Nächstes melden Sie sich mit einem Führungskräftekonto an und erstellen ein Dokument in der Websitesammlung „Führungskräfte“.</span><span class="sxs-lookup"><span data-stu-id="2cc82-165">Next, you sign in with an executive account and create a document in the Executives site collection.</span></span>
  
1. <span data-ttu-id="2cc82-166">Klicken Sie auf das Symbol für Benutzer in der rechten oberen Ecke auf der Registerkarte **Microsoft Office Home** , und klicken Sie dann auf **Abmelden**.</span><span class="sxs-lookup"><span data-stu-id="2cc82-166">On the **Microsoft Office Home** tab, click the user icon in the upper-right, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="2cc82-167">Wechseln Sie zur [http://portal.office.com](http://portal.office.com).</span><span class="sxs-lookup"><span data-stu-id="2cc82-167">Go to [http://portal.office.com](http://portal.office.com).</span></span>
    
3. <span data-ttu-id="2cc82-168">Klicken Sie auf der Seite **Office 365 anmelden** auf **ein anderes Konto verwenden**.</span><span class="sxs-lookup"><span data-stu-id="2cc82-168">On the **Office 365 sign in** page, click **Use another account**.</span></span>
    
4. <span data-ttu-id="2cc82-169">Geben Sie den Kontonamen **CEO** und das zugehörige Kennwort ein, und klicken Sie dann auf **Anmelden**.</span><span class="sxs-lookup"><span data-stu-id="2cc82-169">Type the **CEO** account name and its password, and then click **Sign in**.</span></span>
    
5. <span data-ttu-id="2cc82-170">Geben Sie auf einer neuen Registerkarte des Browsers die URL der Websitesammlung Führungskräfte ( **https://**\<Name der Organisation >**.sharepoint.com/sites/executives**).</span><span class="sxs-lookup"><span data-stu-id="2cc82-170">On a new tab of your browser, type the URL to the Executives site collection ( **https://**\<organization name>**.sharepoint.com/sites/executives**).</span></span>
    
6. <span data-ttu-id="2cc82-171">Klicken Sie auf **Dokumente**, klicken Sie auf **neu,** und klicken Sie dann auf **Word-Dokument**.</span><span class="sxs-lookup"><span data-stu-id="2cc82-171">Click **Documents**, click **New,** and then click **Word Document**.</span></span>
    
7. <span data-ttu-id="2cc82-172">Klicken Sie in der Titelleiste auf, und geben Sie **SensitiveData BeforeIRM**.</span><span class="sxs-lookup"><span data-stu-id="2cc82-172">Click in the title bar and type **SensitiveData-BeforeIRM**.</span></span>
    
8. <span data-ttu-id="2cc82-173">Klicken Sie in der Hauptteil des Dokuments und geben Sie **Minuten aus der neuesten Pinnwand Besprechung**, und klicken Sie dann auf **"Executives"**.</span><span class="sxs-lookup"><span data-stu-id="2cc82-173">Click in the document body and type **Minutes from the latest board meeting**, and then click **Executives**.</span></span>
    
     <span data-ttu-id="2cc82-174">**SensitiveData BeforeIRM.docx** im Ordner " **Dokumente** " sollte angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="2cc82-174">You should see **SensitiveData-BeforeIRM.docx** in the **Documents** folder.</span></span>
    
<span data-ttu-id="2cc82-175">Im nächsten Schritt laden Sie eine lokale Kopie des Dokuments „VertraulicheDaten-VorIRM.docx“ herunter und veröffentlichen diese versehentlich in der Websitesammlung „Vertrieb“.</span><span class="sxs-lookup"><span data-stu-id="2cc82-175">Next, you download a local copy of the SensitiveData-BeforeIRM.docx document and then accidentally post it to the Sales site collection.</span></span>
  
1. <span data-ttu-id="2cc82-176">Erstellen Sie einen neuen Ordner auf Ihrem lokalen Computer (z. B. C:\\TLGs\\SensitiveDataTestFiles).</span><span class="sxs-lookup"><span data-stu-id="2cc82-176">On your local computer, create a new folder (for example, C:\\TLGs\\SensitiveDataTestFiles).</span></span>
    
2. <span data-ttu-id="2cc82-177">Wählen Sie auf der Registerkarte **Dokumente** des Browsers das Dokument **SensitiveData BeforeIRM.docx** , klicken Sie auf die Auslassungspunkte, und klicken Sie auf **Download**.</span><span class="sxs-lookup"><span data-stu-id="2cc82-177">On the **Documents** tab of your browser, select the **SensitiveData-BeforeIRM.docx** document, click the ellipses, and then click **Download**.</span></span>
    
3. <span data-ttu-id="2cc82-178">Speichern Sie das Dokument **SensitiveData BeforeIRM.docx** in den in Schritt 1 erstellten Ordner.</span><span class="sxs-lookup"><span data-stu-id="2cc82-178">Store the **SensitiveData-BeforeIRM.docx** document in the folder created in step 1.</span></span>
    
4. <span data-ttu-id="2cc82-179">Geben Sie auf einer neuen Registerkarte des Browsers die URL der Websitesammlung des Vertriebs ( **https://**\<Name der Organisation >**.sharepoint.com/sites/sales**).</span><span class="sxs-lookup"><span data-stu-id="2cc82-179">On a new tab of your browser, type the URL to the Sales site collection ( **https://**\<organization name>**.sharepoint.com/sites/sales**).</span></span>
    
5. <span data-ttu-id="2cc82-180">Klicken Sie auf den Ordner **Dokumente** der **Websitesammlung Sales**.</span><span class="sxs-lookup"><span data-stu-id="2cc82-180">Click the **Documents** folder of the **Sales site collection**.</span></span>
    
6. <span data-ttu-id="2cc82-181">Klicken Sie auf **Hochladen**, und geben Sie in dem in Schritt 1 erstellten Ordner **SensitiveData BeforeIRM.docx** Dokument, und klicken Sie dann auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="2cc82-181">Click **Upload**, and then specify **SensitiveData-BeforeIRM.docx** document in the folder created in step 1, and then click **OK**.</span></span>
    
7. <span data-ttu-id="2cc82-182">Stellen Sie sicher, dass das Dokument **SensitiveData BeforeIRM.docx** im Ordner " **Dokumente** " ist.</span><span class="sxs-lookup"><span data-stu-id="2cc82-182">Verify that the **SensitiveData-BeforeIRM.docx** document is in the **Documents** folder.</span></span>
    
8. <span data-ttu-id="2cc82-183">Schließen Sie die Registerkarten **Sales** und **SharePoint** .</span><span class="sxs-lookup"><span data-stu-id="2cc82-183">Close the **Sales** and **SharePoint** tabs.</span></span>
    
<span data-ttu-id="2cc82-184">Als Nächstes melden Sie sich als Benutzer5 an und versuchen, das Dokument „VertraulicheDaten-VorIRM.docx“ in der Websitesammlung „Vertrieb“ zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="2cc82-184">Next, you sign in as User5 and try to open the SensitiveData-BeforeIRM.docx document in the Sales site collection.</span></span>
  
1. <span data-ttu-id="2cc82-185">Klicken Sie auf das Symbol für Benutzer in der rechten oberen Ecke auf der Registerkarte **Microsoft Office Home** , und klicken Sie dann auf **Abmelden**.</span><span class="sxs-lookup"><span data-stu-id="2cc82-185">On the **Microsoft Office Home** tab, click the user icon in the upper-right, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="2cc82-186">Wechseln Sie zur [http://portal.office.com](http://portal.office.com).</span><span class="sxs-lookup"><span data-stu-id="2cc82-186">Go to [http://portal.office.com](http://portal.office.com).</span></span>
    
3. <span data-ttu-id="2cc82-187">Klicken Sie auf der Seite **Office 365 anmelden** auf **ein anderes Konto verwenden**.</span><span class="sxs-lookup"><span data-stu-id="2cc82-187">On the **Office 365 sign in** page, click **Use another account**.</span></span>
    
4. <span data-ttu-id="2cc82-188">Geben Sie den User5-Kontonamen und das zugehörige Kennwort ein, und klicken Sie dann auf **Anmelden**.</span><span class="sxs-lookup"><span data-stu-id="2cc82-188">Type the User5 account name and its password, and then click **Sign in**.</span></span>
    
5. <span data-ttu-id="2cc82-189">Geben Sie auf einer neuen Registerkarte des Browsers die URL der Websitesammlung des Vertriebs.</span><span class="sxs-lookup"><span data-stu-id="2cc82-189">On a new tab of your browser, type the URL to the Sales site collection.</span></span>
    
6. <span data-ttu-id="2cc82-190">Klicken Sie auf das Dokument **SensitiveData BeforeIRM.docx** , im Ordner **Dokumente** von der **Websitesammlung Sales**.</span><span class="sxs-lookup"><span data-stu-id="2cc82-190">In the **Documents** folder of the **Sales site collection**, click the **SensitiveData-BeforeIRM.docx** document.</span></span>
    
    <span data-ttu-id="2cc82-191">Sie sollten den Inhalt sehen können.</span><span class="sxs-lookup"><span data-stu-id="2cc82-191">You should see its contents.</span></span>
    
7. <span data-ttu-id="2cc82-192">Schließen Sie die Registerkarten **Dokumente** und **Sales Websitesammlung festlegen** .</span><span class="sxs-lookup"><span data-stu-id="2cc82-192">Close the **Documents** and **Sales site collection** tabs.</span></span>
    
<span data-ttu-id="2cc82-193">Indem der CEO das Dokument „VertraulicheDaten-VorIRM.docx“ versehentlich in der Websitesammlung „Vertrieb“ veröffentlicht hat, hat er die Berechtigungssicherheit der Websitesammlung „Führungskräfte“ umgangen.</span><span class="sxs-lookup"><span data-stu-id="2cc82-193">By accidentally posting the SensitiveData-BeforeIRM.docx document on the Sales site collection, the CEO bypassed the permissions security of the Executives site collection.</span></span>
  
<span data-ttu-id="2cc82-194">Um Office 365 für die Phasen 3 und 4 vorzubereiten, aktivieren Sie IRM für SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="2cc82-194">To prepare Office 365 for Phases 3 and 4, enable IRM for SharePoint Online.</span></span>
  
1. <span data-ttu-id="2cc82-195">Klicken Sie auf das Symbol für Benutzer in der rechten oberen Ecke auf der Registerkarte **Microsoft Office Home** , und klicken Sie dann auf **Abmelden**.</span><span class="sxs-lookup"><span data-stu-id="2cc82-195">On the **Microsoft Office Home** tab, click the user icon in the upper-right, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="2cc82-196">Wechseln Sie zur [http://portal.office.com](http://portal.office.com).</span><span class="sxs-lookup"><span data-stu-id="2cc82-196">Go to [http://portal.office.com](http://portal.office.com).</span></span>
    
3. <span data-ttu-id="2cc82-197">Klicken Sie auf der Seite **Office 365 anmelden** klicken Sie auf den Namen des globalen Administratorkontos, geben Sie das Kennwort ein, und klicken Sie dann auf **Anmelden**.</span><span class="sxs-lookup"><span data-stu-id="2cc82-197">On the **Office 365 sign in** page, click the global administrator account name, type its password, and then click **Sign in**.</span></span>
    
4. <span data-ttu-id="2cc82-198">Klicken Sie auf der Registerkarte **Start von Microsoft Office** auf **Admin > zentriert Admin > SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="2cc82-198">On the **Microsoft Office Home** tab, click **Admin > Admin centers > SharePoint**.</span></span>
    
5. <span data-ttu-id="2cc82-199">Klicken Sie auf der Registerkarte **SharePoint Administrationscenter** auf **Einstellungen**.</span><span class="sxs-lookup"><span data-stu-id="2cc82-199">On the **SharePoint admin center** tab, click **Settings**.</span></span>
    
6. <span data-ttu-id="2cc82-200">Wählen Sie auf der Seite **Einstellungen** im Abschnitt **(Information Rights Management, IRM)** aus, **den in Ihrer Konfiguration angegebenen IRM-Dienst**, und wählen Sie dann die **IRM-Einstellungen aktualisieren**.</span><span class="sxs-lookup"><span data-stu-id="2cc82-200">On the **Settings** page, in the **Information Rights Management (IRM)** section, select **Use the IRM service specified in your configuration**, and then select **Refresh IRM Settings**.</span></span>
    
7. <span data-ttu-id="2cc82-201">Schließen Sie die Registerkarte **SharePoint Administrationscenter** .</span><span class="sxs-lookup"><span data-stu-id="2cc82-201">Close the **SharePoint admin center** tab.</span></span>
    
## <a name="phase-3-use-sharepoint-information-rights-management-with-an-office-365-private-group"></a><span data-ttu-id="2cc82-202">Phase 3: Verwenden von SharePoint Information Rights Management mit einer privaten Office 365-Gruppe</span><span class="sxs-lookup"><span data-stu-id="2cc82-202">Phase 3: Use SharePoint Information Rights Management with an Office 365 private group</span></span>

<span data-ttu-id="2cc82-203">In dieser Phase verwenden Sie SharePoint Information Rights Management mit einer privaten Office 365-Gruppe, um den Zugriff auf ein Dokument mit vertraulichen Informationen auch dann zu schützen, wenn es auf einer Website mit offenen Berechtigungen veröffentlicht wird.</span><span class="sxs-lookup"><span data-stu-id="2cc82-203">In this phase, you use SharePoint Information Rights Management with an Office 365 private group to protect access to a document with sensitive information, even when it is posted on a site with open permissions.</span></span>
  
<span data-ttu-id="2cc82-204">Als Erstes aktivieren und konfigurieren Sie IRM für die Dokumentbibliothek der Websitesammlung „Führungskräfte“. </span><span class="sxs-lookup"><span data-stu-id="2cc82-204">First, you enable and configure IRM for the documents library of the Executives site collection.</span></span> 
  
1. <span data-ttu-id="2cc82-205">Geben Sie auf einer neuen Registerkarte des Browsers die URL der Websitesammlung "Executives".</span><span class="sxs-lookup"><span data-stu-id="2cc82-205">On a new tab of your browser, type the URL to the Executives site collection.</span></span>
    
2. <span data-ttu-id="2cc82-206">Klicken Sie auf **Dokumente**.</span><span class="sxs-lookup"><span data-stu-id="2cc82-206">Click **Documents**.</span></span>
    
3. <span data-ttu-id="2cc82-207">Klicken Sie in der rechten oberen Ecke klicken Sie auf das einstellungssymbol, und klicken Sie dann auf **bibliothekseinstellungen**.</span><span class="sxs-lookup"><span data-stu-id="2cc82-207">In the upper-right, click the settings icon, and then click **Library settings**.</span></span>
    
4. <span data-ttu-id="2cc82-208">Klicken Sie auf der Seite **Einstellungen** unter **Berechtigungen und Verwaltung**auf **Information Rights Management**.</span><span class="sxs-lookup"><span data-stu-id="2cc82-208">On the **Settings** page, under **Permissions and Management**, click **Information Rights Management**.</span></span>
    
5. <span data-ttu-id="2cc82-209">Auf der Seite **Information Rights Management Settings** :</span><span class="sxs-lookup"><span data-stu-id="2cc82-209">On the **Information Rights Management Settings** page:</span></span>
    
  - <span data-ttu-id="2cc82-210">Wählen Sie die **Berechtigung für Dokumente in dieser Bibliothek beim Herunterladen einschränken**.</span><span class="sxs-lookup"><span data-stu-id="2cc82-210">Select **Restrict permission to documents in this library on download**.</span></span>
    
  - <span data-ttu-id="2cc82-211">Geben Sie **einen Titel der Berechtigungsrichtlinie erstellen** **Führungskräfte**.</span><span class="sxs-lookup"><span data-stu-id="2cc82-211">For **Create a permission policy title**, type **Executives**.</span></span>
    
  - <span data-ttu-id="2cc82-212">**Eine Beschreibung der Berechtigungsrichtlinie hinzufügen**Geben Sie **IRM für Führungskräfte**.</span><span class="sxs-lookup"><span data-stu-id="2cc82-212">For **Add a permission policy description**, type **IRM for executives**.</span></span>
    
6. <span data-ttu-id="2cc82-213">Klicken Sie auf **Optionen anzeigen**.</span><span class="sxs-lookup"><span data-stu-id="2cc82-213">Click **Show Options**.</span></span>
    
7. <span data-ttu-id="2cc82-214">Wählen Sie unter **Legen Sie zusätzliche Einstellungen der IRM-Bibliothek** **Dokumente hochladen, die IRM nicht unterstützen, Benutzer können keine**ein.</span><span class="sxs-lookup"><span data-stu-id="2cc82-214">Under **Set additional IRM library settings**, select **Do not allow users to upload documents that do not support IRM**.</span></span>
    
8. <span data-ttu-id="2cc82-215">Wählen Sie unter **Configure Dokument Zugriffsrechte** **Zulassen Zuschauer zu drucken** und **Zulassen Viewer auf eine Kopie des heruntergeladenen Dokuments schreiben**.</span><span class="sxs-lookup"><span data-stu-id="2cc82-215">Under **Configure document access rights**, select **Allow viewers to print** and **Allow viewers to write on a copy of the downloaded document**.</span></span>
    
9. <span data-ttu-id="2cc82-216">Wählen Sie unter **Gruppe Schutz und die Anmeldeinformationen Intervall festgelegt** **die Gruppe Protection zulassen** , und geben Sie für die **Gruppe**, **Führungskräfte**.</span><span class="sxs-lookup"><span data-stu-id="2cc82-216">Under **Set group protection and credentials interval**, select **Allow group protection** and for **Default group**, type **Executives**.</span></span>
    
10. <span data-ttu-id="2cc82-217">Klicken Sie auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="2cc82-217">Click **OK**.</span></span>
    
<span data-ttu-id="2cc82-218">Im nächsten Schritt fungieren Sie als CEO und laden ein neues Dokument in den Dokumentordner „Führungskräfte“ hoch. Dann laden Sie das Dokument herunter und laden es versehentlich in den Dokumentordner „Vertrieb“ hoch.</span><span class="sxs-lookup"><span data-stu-id="2cc82-218">Next, acting as the CEO, you upload a new document to the Executives document folder, download it, then accidentally upload it to the Sales document folder.</span></span>
  
1. <span data-ttu-id="2cc82-219">Öffnen Sie den lokalen Ordner, in dem Sie das Dokument **SensitiveData BeforeIRM.docx** gespeichert.</span><span class="sxs-lookup"><span data-stu-id="2cc82-219">Open the local folder where you stored the **SensitiveData-BeforeIRM.docx** document.</span></span>
    
2. <span data-ttu-id="2cc82-220">Mit der rechten Maustaste **SensitiveData BeforeIRM.docx**, und klicken Sie dann auf **Kopieren**.</span><span class="sxs-lookup"><span data-stu-id="2cc82-220">Right-click **SensitiveData-BeforeIRM.docx**, and then click **Copy**.</span></span>
    
3. <span data-ttu-id="2cc82-221">Mit der rechten Maustaste in den Ordner, und klicken Sie dann auf **Einfügen**.</span><span class="sxs-lookup"><span data-stu-id="2cc82-221">Right-click within the folder, and then click **Paste**.</span></span>
    
4. <span data-ttu-id="2cc82-222">Benennen Sie die neue Datei **SensitiveData-BeforeIRM - Copy.docx** in **SensitiveData AfterIRM.docx**.</span><span class="sxs-lookup"><span data-stu-id="2cc82-222">Rename the new **SensitiveData-BeforeIRM - Copy.docx** file to **SensitiveData-AfterIRM.docx**.</span></span>
    
5. <span data-ttu-id="2cc82-223">Klicken Sie auf das Symbol für Benutzer in der rechten oberen Ecke auf der Registerkarte **Startseite von Microsoft Office** in Ihrem Browser, und klicken Sie dann auf **Abmelden**.</span><span class="sxs-lookup"><span data-stu-id="2cc82-223">From the **Microsoft Office Home** tab in your browser, click the user icon in the upper-right, and then click **Sign out**.</span></span>
    
6. <span data-ttu-id="2cc82-224">Wechseln Sie zur [http://portal.office.com](http://portal.office.com).</span><span class="sxs-lookup"><span data-stu-id="2cc82-224">Go to [http://portal.office.com](http://portal.office.com).</span></span>
    
7. <span data-ttu-id="2cc82-225">Klicken Sie auf der Seite **Office 365 anmelden** klicken Sie auf den Kontonamen CEO, geben Sie das Kennwort ein, und klicken Sie dann auf **Anmelden**.</span><span class="sxs-lookup"><span data-stu-id="2cc82-225">On the **Office 365 sign in** page, click the CEO account name, type its password, and then click **Sign in**.</span></span>
    
8. <span data-ttu-id="2cc82-226">Geben Sie auf einer neuen Registerkarte des Browsers die URL der Websitesammlung "Executives".</span><span class="sxs-lookup"><span data-stu-id="2cc82-226">On a new tab of your browser, type the URL to the Executives site collection.</span></span>
    
9. <span data-ttu-id="2cc82-227">Klicken Sie auf der Seite **Dokumente** auf **Hochladen**, geben Sie das Dokument **SensitiveData AfterIRM.docx** in Ihrer lokalen Ordner, und klicken Sie dann auf **Öffnen**.</span><span class="sxs-lookup"><span data-stu-id="2cc82-227">On the **Documents** page, click **Upload**, specify the **SensitiveData-AfterIRM.docx** document in your local folder, and then click **Open**.</span></span>
    
10. <span data-ttu-id="2cc82-228">Wählen Sie das neue Dokument **SensitiveData AfterIRM.docx** der Seite **Dokumente** aus, klicken Sie auf die Auslassungspunkte (...) in der Menüleiste, und klicken Sie dann auf **herunterladen**.</span><span class="sxs-lookup"><span data-stu-id="2cc82-228">Select the new **SensitiveData-AfterIRM.docx** document in the **Documents** page, click the ellipsis (…) in the menu bar, and then click **Download**.</span></span>
    
11. <span data-ttu-id="2cc82-229">Wenn Sie aufgefordert werden, speichern Sie das **SensitiveData AfterIRM.docx** -Dokument in Ihrer lokalen Ordner, und überschreiben Sie die ursprüngliche Version.</span><span class="sxs-lookup"><span data-stu-id="2cc82-229">When prompted, save the **SensitiveData-AfterIRM.docx** document in your local folder, overwriting the original version.</span></span>
    
12. <span data-ttu-id="2cc82-230">Schließen Sie die Registerkarte für die Seite **Dokumente** .</span><span class="sxs-lookup"><span data-stu-id="2cc82-230">Close the tab for the **Documents** page.</span></span>
    
13. <span data-ttu-id="2cc82-231">Geben Sie auf einer neuen Registerkarte des Browsers die URL der Websitesammlung des Vertriebs.</span><span class="sxs-lookup"><span data-stu-id="2cc82-231">On a new tab of your browser, type the URL to the Sales site collection.</span></span>
    
14. <span data-ttu-id="2cc82-232">Klicken Sie auf **Dokumente**.</span><span class="sxs-lookup"><span data-stu-id="2cc82-232">Click **Documents**.</span></span>
    
15. <span data-ttu-id="2cc82-233">Klicken Sie auf der Seite **Dokumente** auf **Hochladen**, geben Sie das Dokument **SensitiveData AfterIRM.docx** in Ihrer lokalen Ordner, und klicken Sie dann auf **Öffnen**.</span><span class="sxs-lookup"><span data-stu-id="2cc82-233">On the **Documents** page, click **Upload**, specify the **SensitiveData-AfterIRM.docx** document in your local folder, and then click **Open**.</span></span>
    
16. <span data-ttu-id="2cc82-234">Schließen Sie die Registerkarten **Sales-Websitesammlung** und **SharePoint** .</span><span class="sxs-lookup"><span data-stu-id="2cc82-234">Close the **Sales site collection** and **SharePoint** tabs.</span></span>
    
<span data-ttu-id="2cc82-235">Im nächsten Schritt versuchen fungiert als normaler Benutzer, das **SensitiveData AfterIRM.docx** Dokument in den Ordner Sales Dokument zuzugreifen.</span><span class="sxs-lookup"><span data-stu-id="2cc82-235">Next, acting as a normal user, you try to access the **SensitiveData-AfterIRM.docx** document in the Sales document folder.</span></span>
  
1. <span data-ttu-id="2cc82-236">Klicken Sie auf das Symbol für Benutzer in der rechten oberen Ecke auf der Registerkarte **Startseite von Microsoft Office** in Ihrem Browser, und klicken Sie dann auf **Abmelden**.</span><span class="sxs-lookup"><span data-stu-id="2cc82-236">From the **Microsoft Office Home** tab in your browser, click the user icon in the upper-right, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="2cc82-237">Wechseln Sie zur [http://portal.office.com](http://portal.office.com).</span><span class="sxs-lookup"><span data-stu-id="2cc82-237">Go to [http://portal.office.com](http://portal.office.com).</span></span>
    
3. <span data-ttu-id="2cc82-238">Klicken Sie auf der Seite **Office 365 anmelden** klicken Sie auf den Kontonamen User5, geben Sie das Kennwort ein, und klicken Sie dann auf **Anmelden**.</span><span class="sxs-lookup"><span data-stu-id="2cc82-238">On the **Office 365 sign in** page, click the User5 account name, type its password, and then click **Sign in**.</span></span>
    
4. <span data-ttu-id="2cc82-239">Geben Sie auf einer neuen Registerkarte des Browsers die URL der Websitesammlung des Vertriebs.</span><span class="sxs-lookup"><span data-stu-id="2cc82-239">On a new tab of your browser, type the URL to the Sales site collection.</span></span>
    
5. <span data-ttu-id="2cc82-240">Klicken Sie auf **Dokumente**.</span><span class="sxs-lookup"><span data-stu-id="2cc82-240">Click **Documents**.</span></span>
    
6. <span data-ttu-id="2cc82-241">Öffnen Sie auf der Seite **Dokumente** **SensitiveData AfterIRM.docx** Dokument.</span><span class="sxs-lookup"><span data-stu-id="2cc82-241">On the **Documents** page, open the **SensitiveData-AfterIRM.docx** document.</span></span>
    
    <span data-ttu-id="2cc82-242">Es sollte eine Meldung angezeigt werden, die besagt, dass Word Online dieses Dokument nicht öffnen kann, weil es durch Information Rights Management (IRM) geschützt ist. </span><span class="sxs-lookup"><span data-stu-id="2cc82-242">You should see a message that states "Sorry, Word Online can't open this document because it's protected by Information Rights Management (IRM)."</span></span> 
    
7. <span data-ttu-id="2cc82-p105">Klicken Sie auf **in Word bearbeiten**. Sie werden aufgefordert, wenn Sie die Datei öffnen möchten. Klicken Sie auf **Ja**.</span><span class="sxs-lookup"><span data-stu-id="2cc82-p105">Click **Edit in Word**. You are prompted if you want to open the file. Click **Yes**.</span></span>
    
8. <span data-ttu-id="2cc82-p106">Sie werden aufgefordert,-Anmeldung Geben Sie den Kontonamen des User5-Kontos ein, und klicken Sie dann auf **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="2cc82-p106">You are prompted to sign-in. Type the account name of the User5 account, and then click **Next**.</span></span>
    
9. <span data-ttu-id="2cc82-p107">Sie werden aufgefordert, das Kennwort angeben. Geben Sie das Kennwort für das Konto User5, und klicken Sie dann auf **Anmelden**.</span><span class="sxs-lookup"><span data-stu-id="2cc82-p107">You are prompted to provide the password. Type the password for the User5 account and then click **Sign in**.</span></span> 
    
    <span data-ttu-id="2cc82-250">Es sollte eine Nachricht angezeigt werden, die besagt, dass Sie keine Anmeldedaten haben, die Sie zum Öffnen dieses Dokuments berechtigen.</span><span class="sxs-lookup"><span data-stu-id="2cc82-250">You should see the a message that states: "You do not have the credentials that allow you to open this document."</span></span>
    
10. <span data-ttu-id="2cc82-251">Klicken Sie auf **Nein**.</span><span class="sxs-lookup"><span data-stu-id="2cc82-251">Click **No**.</span></span>
    
<span data-ttu-id="2cc82-p108">Eine andere Möglichkeit, finden in der IRM-Schutz ist betrachten Sie die Dateien im lokalen Ordner. Die **SensitiveData AfterIRM.docx** sollte wesentlich größer als die **SensitiveData-BeforeIRM.docx** -Datei. Die Datei **SensitiveData AfterIRM.docx** wird verschlüsselt, und die IRM-Schutz Informationen hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="2cc82-p108">Another way to see the IRM protection is to look at the files in your local folder. The **SensitiveData-AfterIRM.docx** should be much larger than the **SensitiveData-BeforeIRM.docx** file. The **SensitiveData-AfterIRM.docx** file is encrypted and has the IRM protection information added to it.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="2cc82-255">Weitere Artikel</span><span class="sxs-lookup"><span data-stu-id="2cc82-255">See Also</span></span>

[<span data-ttu-id="2cc82-256">Testumgebungsanleitungen (TLGs) zur Cloudakzeptanz</span><span class="sxs-lookup"><span data-stu-id="2cc82-256">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="2cc82-257">Basiskonfiguration der Entwicklungs-/Testumgebung</span><span class="sxs-lookup"><span data-stu-id="2cc82-257">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="2cc82-258">Office 365-Entwicklungs-/Testumgebung</span><span class="sxs-lookup"><span data-stu-id="2cc82-258">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="2cc82-259">Cloudakzeptanz und Hybridlösungen</span><span class="sxs-lookup"><span data-stu-id="2cc82-259">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)


