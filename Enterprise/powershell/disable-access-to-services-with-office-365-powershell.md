---
title: Deaktivieren des Zugriffs auf Dienste mit Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- PowerShell
- LIL_Placement
- DecEntMigration
ms.assetid: 264f4f0d-e2cd-44da-a9d9-23bef250a720
description: "Verwenden von Office 365 PowerShell zum Hinzufügen oder Entfernen des Zugriffs auf Office 365-Diensten für Benutzer in Ihrer Organisation erläutert."
ms.openlocfilehash: a371e6adc482a3f21ebfacac08aff02daf4fd5b2
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2017
---
# <a name="disable-access-to-services-with-office-365-powershell"></a><span data-ttu-id="a4168-103">Deaktivieren des Zugriffs auf Dienste mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="a4168-103">Disable access to services with Office 365 PowerShell</span></span>

<span data-ttu-id="a4168-104">**Zusammenfassung:** Verwenden von Office 365 PowerShell zum Hinzufügen oder Entfernen des Zugriffs auf Office 365-Diensten für Benutzer in Ihrer Organisation erläutert.</span><span class="sxs-lookup"><span data-stu-id="a4168-104">**Summary:** Explains how to use Office 365 PowerShell to add or remove access to Office 365 services for users in your organization.</span></span>
  
<span data-ttu-id="a4168-p101">Wenn ein Office 365-Konto eine Lizenz von einem Lizenzierungsplan zugeordnet ist, sind Office 365-Dienste für den Benutzer über diese Lizenz verfügbar. Sie können jedoch die Office 365-Dienste steuern, die der Benutzer zugreifen kann. Obwohl die Lizenz Zugriff auf SharePoint Online ermöglicht, können Sie beispielsweise Zugriff darauf deaktivieren. Office 365 PowerShell können Sie tatsächlich den Zugriff auf eine beliebige Anzahl von Diensten für deaktivieren:</span><span class="sxs-lookup"><span data-stu-id="a4168-p101">When an Office 365 account is assigned a license from a licensing plan, Office 365 services are made available to the user from that license. However, you can control the Office 365 services that the user can access. For example, even though the license allows access to SharePoint Online, you can disable access to it. In fact, you can use Office 365 PowerShell to disable access to any number of services for:</span></span>
- <span data-ttu-id="a4168-109">ein einzelnes Konto</span><span class="sxs-lookup"><span data-stu-id="a4168-109">An individual account.</span></span>
    
- <span data-ttu-id="a4168-110">eine Gruppe von Konten</span><span class="sxs-lookup"><span data-stu-id="a4168-110">A group of accounts.</span></span>
    
- <span data-ttu-id="a4168-111">Alle Konten in Ihrer Organisation.</span><span class="sxs-lookup"><span data-stu-id="a4168-111">All accounts in your organization.</span></span>
    
 <span data-ttu-id="a4168-112">**Inhalt:** [Die Kurzversion (Anweisungen ohne Erklärungen)](disable-access-to-services-with-office-365-powershell.md#ShortVersion) [Die langes Format (Anweisungen mit detaillierten erläuterungen)](disable-access-to-services-with-office-365-powershell.md#LongVersion) [Siehe auch](disable-access-to-services-with-office-365-powershell.md#SeeAlso)</span><span class="sxs-lookup"><span data-stu-id="a4168-112">**Contents:**[The short version (instructions without explanations)](disable-access-to-services-with-office-365-powershell.md#ShortVersion)[The long version (instructions with detailed explanations)](disable-access-to-services-with-office-365-powershell.md#LongVersion)[See also](disable-access-to-services-with-office-365-powershell.md#SeeAlso)</span></span>
## <a name="before-you-begin"></a><span data-ttu-id="a4168-113">Bevor Sie beginnen</span><span class="sxs-lookup"><span data-stu-id="a4168-113">Before you begin</span></span>
<span data-ttu-id="a4168-114"><a name="RTT"> </a></span><span class="sxs-lookup"><span data-stu-id="a4168-114"></span></span>

- <span data-ttu-id="a4168-p102">Für die Verfahren in diesem Thema müssen Sie eine Verbindung mit Office 365 PowerShell herstellen. Weitere Anweisungen finden Sie unter [Verbinden mit Office 365 PowerShell](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="a4168-p102">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="a4168-p103">Verwenden Sie das Cmdlet " **Get-MsolAccountSku** ", um anzuzeigen, Ihrer verfügbaren lizenzierungspläne und die Office 365-Dienste, die in dieser Pläne zur Verfügung stehen. Weitere Informationen finden Sie unter[Lizenzen anzeigen und-Dienste mit Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="a4168-p103">You use the **Get-MsolAccountSku** cmdlet to view your available licensing plans, and the Office 365 services that are available in those plans. For more information, see[View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="a4168-119">Anzeigen der vor und nach der Ergebnisse der Verfahren in diesem Thema finden Sie unter [Anzeigen von Kontodetails Lizenz und den Dienst mit Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="a4168-119">To see the before and after results of the procedures in this topic, see [View account license and service details with Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="a4168-p104">Ein PowerShell-Skript ist verfügbar, die die in diesem Thema beschriebenen Verfahren automatisiert. Insbesondere ermöglicht das Skript anzeigen und Deaktivieren von Diensten in Office 365-Organisation, einschließlich Schlingern. Weitere Informationen finden Sie unter [Deaktivieren des Zugriffs auf Schlingern mit Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="a4168-p104">A PowerShell script is available that automates the procedures described in this topic. Specifically, the script allows you to view and disable services in your Office 365 organization, including Sway. For more information, see [Disable access to Sway with Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="a4168-123">Bei Verwendung des **Get-MsolUser** -Cmdlets ohne den _All_-Parameter werden nur die ersten 500 Konten zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="a4168-123">If you use the **Get-MsolUser** cmdlet without using the _All_ parameter, only the first 500 accounts are returned.</span></span>
    
## <a name="the-short-version-instructions-without-explanations"></a><span data-ttu-id="a4168-124">Die Kurzfassung (Anweisungen ohne Erläuterungen)</span><span class="sxs-lookup"><span data-stu-id="a4168-124">The short version (instructions without explanations)</span></span>
<span data-ttu-id="a4168-125"><a name="ShortVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="a4168-125"></span></span>

<span data-ttu-id="a4168-p105">In diesem Abschnitt werden die Verfahren kurz und bündig erläutert. Wenn Sie Fragen haben oder weitere Informationen benötigen, können Sie den Rest des Themas lesen.</span><span class="sxs-lookup"><span data-stu-id="a4168-p105">This section presents the procedures without fanfare or superfluous explanation. If you have questions or want more information, you can read rest of the topic.</span></span>
  
<span data-ttu-id="a4168-128">Um Benutzer aus einer einzelnen Lizenzierungsplan Office 365-Dienste zu deaktivieren, führen Sie die folgenden Schritte aus:</span><span class="sxs-lookup"><span data-stu-id="a4168-128">To disable Office 365 services for users from a single licensing plan, perform the following steps:</span></span>
  
1. <span data-ttu-id="a4168-129">Identifizieren Sie die unerwünschten Dienste in den Lizenzierungsplan mithilfe der folgenden Syntax:</span><span class="sxs-lookup"><span data-stu-id="a4168-129">Identify the undesirable services in the licensing plan by using the following syntax:</span></span>
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId <AccountSkuId> -DisabledPlans "<UndesirableService1>", "<UndesirableService2>"...
  ```

    <span data-ttu-id="a4168-130">Dieses Beispiel erstellt ein **LicenseOptions** -Objekt, das in den Lizenzierungsplan mit dem Namen der Office Online und SharePoint Online-Dienste deaktiviert `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3).</span><span class="sxs-lookup"><span data-stu-id="a4168-130">This example creates a **LicenseOptions** object that disables the Office Online and SharePoint Online services in the licensing plan named `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3).</span></span>
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
  ```

2. <span data-ttu-id="a4168-131">Verwenden Sie das **LicenseOptions** -Objekt aus Schritt 1 auf einen oder mehrere Benutzer.</span><span class="sxs-lookup"><span data-stu-id="a4168-131">Use the **LicenseOptions** object from Step 1 on one or more users.</span></span>
    
  - <span data-ttu-id="a4168-132">Wenn Sie ein neues Konto zu erstellen möchten, für das die Dienste deaktiviert sind, verwenden Sie die folgende Syntax:</span><span class="sxs-lookup"><span data-stu-id="a4168-132">To create a new account that has the services disabled, use the following syntax:</span></span>
    
  ```
  New-MsolUser -UserPrincipalName <Account> -DisplayName <DisplayName> -FirstName <FirstName> -LastName <LastName> -LicenseAssignment <AccountSkuId> -LicenseOptions $LO -UsageLocation <CountryCode>
  ```

    <span data-ttu-id="a4168-133">In diesem Beispiel wird ein neues Konto für Allie Bellew erstellt, das die Lizenz zuweist und die in Schritt 1 beschriebenen Dienste deaktiviert.</span><span class="sxs-lookup"><span data-stu-id="a4168-133">This example creates a new account for Allie Bellew that assigns the license and disables the services described in Step 1.</span></span>
    
  ```
  New-MsolUser -UserPrincipalName allieb@litwareinc.com -DisplayName "Allie Bellew" -FirstName Allie -LastName Bellew -LicenseAssignment litwareinc:ENTERPRISEPACK -LicenseOptions $LO -UsageLocation US
  ```

    <span data-ttu-id="a4168-134">Weitere Informationen zum Erstellen von Benutzerkonten in Office 365 PowerShell finden Sie unter [Erstellen von Benutzerkonten mit Office 365 PowerShell](create-user-accounts-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="a4168-134">For more information about creating user accounts in Office 365 PowerShell, see [Create user accounts with Office 365 PowerShell](create-user-accounts-with-office-365-powershell.md).</span></span>
    
  - <span data-ttu-id="a4168-135">Verwenden Sie die folgende Syntax, um die Dienste für einen vorhandenen lizenzierten Benutzer zu deaktivieren:</span><span class="sxs-lookup"><span data-stu-id="a4168-135">To disable the services for an existing licensed user, use the following syntax:</span></span>
    
  ```
  Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $LO
  ```

    <span data-ttu-id="a4168-136">In diesem Beispiel werden die Dienste für den Benutzer „BelindaN@litwareinc.com“ deaktiviert.</span><span class="sxs-lookup"><span data-stu-id="a4168-136">This example disables the services for the user BelindaN@litwareinc.com.</span></span>
    
  ```
  Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $LO
  ```

  - <span data-ttu-id="a4168-137">Um die Dienste beschrieben in Schritt 1 für alle vorhandenen lizenzierten Benutzer zu deaktivieren, geben Sie den Namen Ihres Office 365 Plans aus der Anzeige des Cmdlets **Get-MsolAccountSku** (beispielsweise **litwareinc: enterprisepack** ), und führen Sie dann die folgenden Befehle aus:</span><span class="sxs-lookup"><span data-stu-id="a4168-137">To disable the services described in Step 1 for all existing licensed users, specify the name of your Office 365 plan from the display of the **Get-MsolAccountSku** cmdlet (such as **litwareinc:ENTERPRISEPACK** ), and then run the following commands:</span></span>
    
  ```
  $acctSKU="<AccountSkuId>"
$AllLicensed = Get-MsolUser -All | Where {$_.isLicensed -eq $true -and $_.licenses[0].AccountSku.SkuPartNumber -eq ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1)}
$AllLicensed | ForEach {Set-MsolUserLicense -LicenseOptions $LO}
  ```

  - <span data-ttu-id="a4168-138">Verwenden Sie eine der folgenden Methoden, um die Dienste für eine Gruppe von vorhandenen Benutzern zu deaktivieren und die Benutzer zu identifizieren:</span><span class="sxs-lookup"><span data-stu-id="a4168-138">To disable the services for a group of existing users, use either of the following methods to identify the users:</span></span>
    
  - <span data-ttu-id="a4168-139">**Filtern die anhand eines vorhandenen Attributs Konto Konten** Verwenden Sie dazu die folgende Syntax:</span><span class="sxs-lookup"><span data-stu-id="a4168-139">**Filter the accounts based on an existing account attribute** To do this, use the following syntax:</span></span>
    
  ```
  $x = Get-MsolUser -All <FilterableAttributes>
$x | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

    <span data-ttu-id="a4168-140">In diesem Beispiel werden die Dienste für Benutzer in der Vertriebsabteilung in den Vereinigten Staaten deaktiviert.</span><span class="sxs-lookup"><span data-stu-id="a4168-140">This example disables the services for users in the Sales department in the United States.</span></span>
    
  ```
  $USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US"
$USSales | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

  - <span data-ttu-id="a4168-141">**Verwenden einer Liste spezieller Konten** Führen Sie dazu die folgenden Schritte aus:</span><span class="sxs-lookup"><span data-stu-id="a4168-141">**Use a list of specific accounts** To do this, perform the following steps:</span></span>
    
1. <span data-ttu-id="a4168-142">Erstellen Sie eine Textdatei wie die folgende, die in jeder Zeile ein Konto enthält:</span><span class="sxs-lookup"><span data-stu-id="a4168-142">Create a text file that contains one account on each line like this:</span></span>
    
  ```
  akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

    <span data-ttu-id="a4168-143">In diesem Beispiel wird die Textdatei C:\\eigene\\Accounts.txt.</span><span class="sxs-lookup"><span data-stu-id="a4168-143">In this example, the text file is C:\\My Documents\\Accounts.txt.</span></span>
    
2. <span data-ttu-id="a4168-144">Führen Sie den folgenden Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="a4168-144">Run the following command:</span></span>
    
  ```
  Get-Content "C:\\My Documents\\Accounts.txt" | foreach {Set-MsolUserLicense -UserPrincipalName $_ -LicenseOptions $LO}
  ```

<span data-ttu-id="a4168-145">Um Office 365-Diensten für Benutzer zu deaktivieren, während Sie sie an einer Lizenzierungsplan zuweisen, finden Sie unter [Zugriff auf Dienste beim Zuweisen von Benutzerlizenzen deaktivieren](disable-access-to-services-while-assigning-user-licenses.md).</span><span class="sxs-lookup"><span data-stu-id="a4168-145">To disable Office 365 services for users while you are assigning them to a licensing plan, see [Disable access to services while assigning user licenses](disable-access-to-services-while-assigning-user-licenses.md).</span></span>
  
<span data-ttu-id="a4168-146">Führen Sie die folgenden Schritte, um Office 365-Diensten für Benutzer in allen verfügbaren lizenzierungspläne zu deaktivieren:</span><span class="sxs-lookup"><span data-stu-id="a4168-146">To disable Office 365 services for users in all available licensing plans, perform the following steps:</span></span>
  
1. <span data-ttu-id="a4168-147">Kopieren Sie dieses Skript, und fügen Sie es in Editor ein.</span><span class="sxs-lookup"><span data-stu-id="a4168-147">Copy and paste this script into Notepad.</span></span>
    
  ```
  $AllLicensingPlans = Get-MsolAccountSku
for($i = 0; $i -lt $AllLicensingPlans.Count; $i++)
{
    $O365Licences = New-MsolLicenseOptions -AccountSkuId $AllLicensingPlans[$i].AccountSkuId -DisabledPlans "<UndesirableService1>", "<UndesirableService2>"...
    Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $O365Licences
}
  ```

2. <span data-ttu-id="a4168-148">Passen Sie die folgenden Werte für Ihre Umgebung an:</span><span class="sxs-lookup"><span data-stu-id="a4168-148">Customize the following values for your environment:</span></span>
    
  -  <span data-ttu-id="a4168-149">_<UndesirableService>_In diesem Beispiel werden wir Office Online und SharePoint Online verwenden.</span><span class="sxs-lookup"><span data-stu-id="a4168-149">_<UndesirableService>_ In this example, we'll use Office Online and SharePoint Online.</span></span>
    
  -  <span data-ttu-id="a4168-150">_<Account>_In diesem Beispiel verwenden wir belindan@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="a4168-150">_<Account>_ In this example, we'll use belindan@litwareinc.com.</span></span>
    
    <span data-ttu-id="a4168-151">Das angepasste Skript sieht wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="a4168-151">The customized script looks like this:</span></span>
    
  ```
  $AllLicensingPlans = Get-MsolAccountSku
for($i = 0; $i -lt $AllLicensingPlans.Count; $i++)
{
    $O365Licences = New-MsolLicenseOptions -AccountSkuId $AllLicensingPlans[$i].AccountSkuId -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
    Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $O365Licences
}
  ```

3. <span data-ttu-id="a4168-p106">Speichern Sie das Skript als `RemoveO365Services.ps1` an einem Speicherort, die Sie leicht zu finden. In diesem Beispiel werden wir speichern Sie die Datei in " `C:\\O365 Scripts`".</span><span class="sxs-lookup"><span data-stu-id="a4168-p106">Save the script as  `RemoveO365Services.ps1` in a location that's easy for you to find. For this example, we'll save the file in " `C:\\O365 Scripts`".</span></span>
    
4. <span data-ttu-id="a4168-154">Führen Sie das Skript in Office 365 PowerShell mithilfe des folgenden Befehls.</span><span class="sxs-lookup"><span data-stu-id="a4168-154">Run the script in Office 365 PowerShell by using the following command.</span></span>
    
  ```
  &amp; "C:\\O365 Scripts\\RemoveO365Services.ps1"
  ```

> [!NOTE]
> <span data-ttu-id="a4168-155">Um die Effekte eines dieser Verfahren rückgängig zu machen (d. h., die deaktivierten Dienste erneut aktivieren), führen Sie das Verfahren erneut aus, aber verwenden Sie den Wert `$null` für den Parameter _DisabledPlans_ .</span><span class="sxs-lookup"><span data-stu-id="a4168-155">To reverse the effects of any of these procedures (that is, to re-enable the disabled services), run the procedure again, but use the value  `$null` for the _DisabledPlans_ parameter.</span></span>
  
[<span data-ttu-id="a4168-156">Zurück zum Seitenanfang</span><span class="sxs-lookup"><span data-stu-id="a4168-156">Return to top</span></span>](disable-access-to-services-with-office-365-powershell.md#RTT)
  
## <a name="the-long-version-instructions-with-detailed-explanations"></a><span data-ttu-id="a4168-157">Die Langfassung (Anweisungen mit detaillierten Erläuterungen)</span><span class="sxs-lookup"><span data-stu-id="a4168-157">The long version (instructions with detailed explanations)</span></span>
<span data-ttu-id="a4168-158"><a name="LongVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="a4168-158"></span></span>

<span data-ttu-id="a4168-p107">Alle Dienste werden standardmäßig aktiviert, wenn Sie eine Lizenz mithilfe von PowerShell für Office 365 registrieren. Häufig ist eine gute Sache: Dies bedeutet, dass Sie schnell und einfach Lizenzen Benutzern zuweisen können ohne anzugeben, dass jeder Dienst dabei aktiviert werden.</span><span class="sxs-lookup"><span data-stu-id="a4168-p107">By default, all services are enabled when you issue a license by using Office 365 PowerShell. And often that's a good thing: that means that you can quickly and easily assign licenses to users without having to specify that each and every service be enabled along the way.</span></span>
  
<span data-ttu-id="a4168-p108">Andererseits gilt jedoch es auch, dass Sie möglicherweise die verfügbaren Dienste bestimmte Benutzer beschränken möchten. beispielsweise vielleicht sollten einige Benutzer haben Zugriff auf Office Professional Plus, Skype für Business Online und Exchange Online, aber diese dieselben Benutzer keinen Zugriff auf SharePoint Online oder auf Office Online haben. Kann Konten auf diese Weise werden eingeschränkt? Wie sich herausstellt, können Sie. Um besser erklären, wie dies funktioniert, werfen wir einen zweistufiger Ansatz zum Bekämpfung dieses Problems:</span><span class="sxs-lookup"><span data-stu-id="a4168-p108">Having said that, however, it's also true that you might want to restrict the services available some of your users; for example, maybe some users should have access to Office Professional Plus, Skype for Business Online, and Exchange Online, but those same users shouldn't have access to SharePoint Online or to Office Online. Can you restrict accounts in that fashion? As it turns out, you can. To help explain how this works, let's take a two-step approach to tackling this problem:</span></span>
  
1. <span data-ttu-id="a4168-165">Weisen Sie dem Benutzer eine Office 365-Lizenz, die automatisch alle Dienste aktiviert.</span><span class="sxs-lookup"><span data-stu-id="a4168-165">Assign the user an Office 365 license that automatically enables all the services.</span></span>
    
2. <span data-ttu-id="a4168-166">Führen Sie dann eine Reihe von Office 365 PowerShell-Befehle, die bestimmte Dienste für diesen Benutzer deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="a4168-166">Run a pair of Office 365 PowerShell commands that disable specified services for that user.</span></span>
    
<span data-ttu-id="a4168-p109">Wir haben bereits beachtet Schritt 1: unsere Benutzer (Belinda Newman) hat eine Office 365-Lizenz, die ihr Zugriff auf die Office 365-Dienste bereitstellt. Wir möchten jedoch Belindas Konto ändern, sodass er Zugriff auf SharePoint Online nicht ( `SHAREPOINTENTERPRISE`) oder auf Office Online ( `SHAREPOINTWAC`). Aber wie wir sollen dazu?</span><span class="sxs-lookup"><span data-stu-id="a4168-p109">We've already taken care of step 1: our user (Belinda Newman) has an Office 365 license that provides her with access to all the Office 365 services. However, we want to modify Belinda's account so that she doesn't have access to SharePoint Online ( `SHAREPOINTENTERPRISE`) or to Office Online ( `SHAREPOINTWAC`). But how are we supposed to do that?</span></span>
  
<span data-ttu-id="a4168-p110">Hier ist wie. Zunächst werden wir das Cmdlet " **New-MsolLicenseOptions** " verwenden, um ein **LicenseOption** -Objekt erstellen, enthält die Dienste, die wir möchten deaktiviert. Im Fall Belindas wir deaktivieren möchten `SHAREPOINTENTERPRISE` und `SHAREPOINTWAC`, sodass wir diesen Befehl verwenden:</span><span class="sxs-lookup"><span data-stu-id="a4168-p110">Here's how. To begin with, we're going to use the **New-MsolLicenseOptions** cmdlet to create a **LicenseOption** object that contains the services that we want disabled. In Belinda's case, we want to disable `SHAREPOINTENTERPRISE` and `SHAREPOINTWAC`, so we use this command:</span></span>
  
```
$x = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
```

<span data-ttu-id="a4168-p111">Sehen Sie, wie das funktioniert? Sie geben den Lizenzierungsplan ( `litwareinc:ENTERPRISEPACK`) und dann jeden der Dienste, die gewünschte deaktiviert, durch ein Komma.</span><span class="sxs-lookup"><span data-stu-id="a4168-p111">See how that works? You specify the licensing plan ( `litwareinc:ENTERPRISEPACK`) and then indicate each of the services that you want disabled, separating those services by using commas.</span></span>
  
> [!NOTE]
> <span data-ttu-id="a4168-p112">Stellen Sie sicher, dass Sie Ihre neue **LicenseOption** -Objekt in einer Variablen zu speichern. Im vorstehenden Beispiel wir verwendet `$x`, obwohl Sie eine beliebige gültige Variablennamen Windows PowerShell verwenden können.</span><span class="sxs-lookup"><span data-stu-id="a4168-p112">Make sure you store your new **LicenseOption** object in a variable. In the preceding example, we used `$x`, although you can use any valid Windows PowerShell variable name.</span></span> 
  
<span data-ttu-id="a4168-177">Nun können wir den folgenden Befehl verwenden, um Belindas Zugriff auf die zwei Dienste zu deaktivieren:</span><span class="sxs-lookup"><span data-stu-id="a4168-177">At this point we can use the following command to disable Belinda's access to the two services:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName BelindaN@litwareinc.com -LicenseOptions $x
```

<span data-ttu-id="a4168-p113">Nichts zu ausgeklügelte hier entweder: wir gerade das Cmdlet " **Set-MsolUserLicense** " aufrufen und nehmen Sie den Parameter _LicenseOptions_ , zusammen mit der Variable ( `$x`), enthält die Pläne wir deaktivieren möchten. Und was wir finden Sie unter jetzt Wenn wir einen Blick auf Belindas Lizenzinformationen mithilfe des Befehls verwenden: `(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses.ServiceStatus`? Wir sehen dies:</span><span class="sxs-lookup"><span data-stu-id="a4168-p113">Nothing too fancy here, either: we just call the **Set-MsolUserLicense** cmdlet and include the _LicenseOptions_ parameter, along with the variable ( `$x`) containing the plans we want to disable. And what do we see now if we take a peek at Belinda's license information by running the command:  `(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses.ServiceStatus`? We see this:</span></span>
  
```
ServicePlan                              ProvisioningStatus
-----------                              ------------------
SWAY                                     Success
INTUNE_O365                              Success
YAMMER_ENTERPRISE                        PendingInput
RMS_S_ENTERPRISE                         Success
OFFICESUBSCRIPTION                       Success
MCOSTANDARD                              Success
SHAREPOINTWAC                            Disabled
SHAREPOINTENTERPRISE                     Disabled
EXCHANGE_S_ENTERPRISE                    Success
```

<span data-ttu-id="a4168-p114">Ziemlich Cool, nicht wahr? Und natürlich wir konnte führen Sie dasselbe auf mehrere Benutzer würden wir an. Diese Befehle deaktivieren beispielsweise dieselben zwei Dienste für alle unsere lizenzierten Benutzer. Geben Sie den Namen Ihres Office 365 Plans aus der Anzeige des Cmdlets **Get-MsolAccountSku** (beispielsweise **litwareinc: enterprisepack** ), und führen Sie diese.</span><span class="sxs-lookup"><span data-stu-id="a4168-p114">Pretty cool, huh? And, of course, we could do this same thing to multiple users if we wanted to. For example, these commands disable the same two services for all our licensed users. Specify the name of your Office 365 plan from the display of the **Get-MsolAccountSku** cmdlet (such as **litwareinc:ENTERPRISEPACK** ), and then run them.</span></span>
  
```
$acctSKU="<AccountSKU ID>"
Get-MsolUser | Where {$_.licenses[0].AccountSku.SkuPartNumber -eq ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1) -and $_.IsLicensed -eq $True} | Set-MsolUserLicense -LicenseOptions $x
```

<span data-ttu-id="a4168-p115">Beachten Sie, dass Belinda immer noch eine gültige Office 365-Lizenz verfügt beibehalten; Es handelt es sich, nachdem sie Zugriff auf weniger Services hat. Bevor wir zwei Dienste deaktiviert, konnte Belinda zugreifen Newsfeeds, OneDrive und SharePoint Online Websites:</span><span class="sxs-lookup"><span data-stu-id="a4168-p115">Keep in mind that Belinda still has a valid Office 365 license; it's just that now she has access to fewer services. Before we disabled the two services, Belinda had access to newsfeeds, OneDrive, and SharePoint Online sites:</span></span>
  
![Benutzer mit SharePoint-Zugriff.](images/o365_powershell_with_sharepoint.png)
  
<span data-ttu-id="a4168-188">Jetzt stehen ihr diese Optionen nicht mehr zur Verfügung:</span><span class="sxs-lookup"><span data-stu-id="a4168-188">Now those options are no longer available to her:</span></span>
  
![Benutzer ohne SharePoint-Zugriff.](images/o365_powershell_without_sharepoint.png)
  
<span data-ttu-id="a4168-190">Was genau das ist, was wir wollten.</span><span class="sxs-lookup"><span data-stu-id="a4168-190">Which is exactly what we hoped would happen.</span></span>
  
<span data-ttu-id="a4168-p116">Und was passiert, wenn wir unsere Meinung später ändern: ist es möglich, diese Dienste wieder aktivieren? Es ist absolut. Um alle Dienste für einen Benutzer wieder zu aktivieren, verwenden Sie diesen Befehl nur das folgenden **LicenseOption** -Objekt erstellt:</span><span class="sxs-lookup"><span data-stu-id="a4168-p116">And what if we change our mind later on: is it possible to re-enable these services? You bet it is. To re-enable all the services for a user, just use this command to create the following **LicenseOption** object:</span></span>
  
```
$x = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans $null
```

<span data-ttu-id="a4168-p117">Welche dieser Befehl? Beginnen Sie mit der Windows PowerShell-Konstante `$null` bedeutet "nothing". (Oder in etwas mehr technische Sprache, bedeutet einen "null-Wert.") Wie Sie sich erinnern, wenn wir verwenden Sie das Cmdlet " **New-MsolLicenseOptions** " Wir haben, um die Dienste anzugeben, deaktiviert werden soll. In diesem Fall soll keiner Dienste deaktiviert werden. Die möglicherweise führen Sie glauben, dass wir einen Befehl wie den folgenden Befehl verwenden könnten, in dem wir keinen Wert für den _DisabledPlans_ -Parameter angeben:</span><span class="sxs-lookup"><span data-stu-id="a4168-p117">What does that command do? To begin with, the Windows PowerShell constant  `$null` means "nothing." (Or, in slightly-more technical language, it means a "null value.") As you recall, when we use the **New-MsolLicenseOptions** cmdlet we have to indicate the services that we want disabled. In this case, we don't want any of the services to be disabled. That might lead you to believe that we could use a command like the following, a command where we don't specify a value for the _DisabledPlans_ parameter:</span></span>
  
```
$x = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans ""
```

<span data-ttu-id="a4168-p118">Jedoch ist nicht möglich. Stattdessen wird eine Fehlermeldung generiert:</span><span class="sxs-lookup"><span data-stu-id="a4168-p118">However, that won't work. Instead, it generates an error message:</span></span>
  
 `Set-MsolUserLicense : Cannot bind parameter 'LicenseOptions'. Cannot convert the "" value of type "System.String" to type "Microsoft.Online.Administration.LicenseOption".`
  
<span data-ttu-id="a4168-201">Zum Glück für uns, Festlegen des Werts des Parameters auf `$null` funktioniert:</span><span class="sxs-lookup"><span data-stu-id="a4168-201">Fortunately for us, setting the parameter value to  `$null` does work:</span></span>
  
```
$x = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans $null
```

<span data-ttu-id="a4168-202">Das bedeutet ganz einfach, dass, wenn wir das Cmdlet " **Set-MsolUserLicense** " ausführen, wir **Set-MsolUserLicense** angeben, dass für Belinda keine Dienste deaktiviert werden sollen:</span><span class="sxs-lookup"><span data-stu-id="a4168-202">This simply means that, when we run the **Set-MsolUserLicense** cmdlet, we're telling **Set-MsolUserLicense** that we don't want Belinda to have any disabled services:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName BelindaN@litwareinc.com -LicenseOptions $x
```

<span data-ttu-id="a4168-203">Und wenn keiner der Dienste deaktiviert ist, heißt das logischerweise, dass alle Dienste aktiviert sind.</span><span class="sxs-lookup"><span data-stu-id="a4168-203">And, logically enough, if none of the services are disabled that must mean that all of the services are enabled.</span></span>
  
<span data-ttu-id="a4168-p119">Nun, Sie verstehen, wie All dies funktioniert, lassen Sie uns zeigen, wie Sie eine Lizenz ausstellen können und Disable-Dienste und alle mit dem gleichen Befehl angegeben. Das klingt ziemlich beeindruckende, aber, um ehrlich zu sein, es ist wirklich nicht darauf: Fügen Sie die _AddLicenses_ und die _LicenseOptions_ -Parameter im gleichen Befehl. Anders ausgedrückt, erstellen Sie zuerst das **LicenseOption** -Objekt:</span><span class="sxs-lookup"><span data-stu-id="a4168-p119">Now that you understand how this all works, let's show you how you can issue a license and disable specified services, and all with the same command. That sounds pretty impressive, but, to be honest, there's really nothing to it: you just include both the  _AddLicenses_ and the _LicenseOptions_ parameters in the same command. In other words, you first create your **LicenseOption** object:</span></span>
  
```
$x = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
```

<span data-ttu-id="a4168-207">Und klicken Sie dann wie bereits erwähnt, Sie verwenden die _AddLicenses_ und die _LicenseOptions_ -Parameter in Ihrem Befehl:</span><span class="sxs-lookup"><span data-stu-id="a4168-207">And then, as noted previously, you use both the  _AddLicenses_ and the _LicenseOptions_ parameters in your command:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName BelindaN@litwareinc.com -AddLicenses "litwareinc:ENTERPRISEPACK" -LicenseOptions $x
```

<span data-ttu-id="a4168-208">Dass der Befehl Belinda Newman eine neue Lizenz, aber in welche Skype eine Lizenz für Business Online ausstellt ( `SHAREPOINTWAC`) und SharePoint Online ( `SHAREPOINTENTERPRISE`) sind beide deaktiviert.</span><span class="sxs-lookup"><span data-stu-id="a4168-208">That command will issue Belinda Newman a new license, but a license in which Skype for Business Online ( `SHAREPOINTWAC`) and SharePoint Online ( `SHAREPOINTENTERPRISE`) are both disabled.</span></span>
  
[<span data-ttu-id="a4168-209">Zurück zum Seitenanfang</span><span class="sxs-lookup"><span data-stu-id="a4168-209">Return to top</span></span>](disable-access-to-services-with-office-365-powershell.md#RTT)
  
## <a name="new-to-office-365"></a><span data-ttu-id="a4168-210">Neu bei Office 365?</span><span class="sxs-lookup"><span data-stu-id="a4168-210">New to Office 365?</span></span>
<span data-ttu-id="a4168-211"><a name="LongVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="a4168-211"></span></span>

||
|:-----|
|<span data-ttu-id="a4168-p120">![Das kurze Symbol für LinkedIn Learning](images/d547e1cb-7c66-422b-85be-7e7db2a9cf97.png) **neu zu Office 365?**         Entdecken Sie kostenlose video Kurse für **Office 365-Administratoren und IT-Experten**, bereitgestellt von LinkedIn Learning.</span><span class="sxs-lookup"><span data-stu-id="a4168-p120">![The short icon for LinkedIn Learning](images/d547e1cb-7c66-422b-85be-7e7db2a9cf97.png) **New to Office 365?**         Discover free video courses for **Office 365 admins and IT pros**, brought to you by LinkedIn Learning.</span></span> |
   
## <a name="see-also"></a><span data-ttu-id="a4168-214">See also</span><span class="sxs-lookup"><span data-stu-id="a4168-214">See also</span></span>
<span data-ttu-id="a4168-215"><a name="SeeAlso"> </a></span><span class="sxs-lookup"><span data-stu-id="a4168-215"></span></span>

<span data-ttu-id="a4168-216">In den folgenden zusätzlichen Themen finden Sie weitere Informationen zum Verwalten von Benutzern mit Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="a4168-216">See the following additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="a4168-217">Löschen und Wiederherstellen von Benutzerkonten mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="a4168-217">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="a4168-218">Löschen und Wiederherstellen von Benutzerkonten mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="a4168-218">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="a4168-219">Blockieren von Benutzerkonten mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="a4168-219">Block user accounts with Office 365 PowerShell</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="a4168-220">Zuweisen von Lizenzen zu Benutzerkonten mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="a4168-220">Assign licenses to user accounts with Office 365 PowerShell</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="a4168-221">Erstellen von Benutzerkonten mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="a4168-221">Create user accounts with Office 365 PowerShell</span></span>](create-user-accounts-with-office-365-powershell.md)
    
<span data-ttu-id="a4168-222">Weitere Informationen zu den in diesen Verfahren Thema verwendeten Cmdlets finden Sie unter den folgenden Themen:</span><span class="sxs-lookup"><span data-stu-id="a4168-222">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="a4168-223">Get-Content</span><span class="sxs-lookup"><span data-stu-id="a4168-223">Get-Content</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=289917)
    
- [<span data-ttu-id="a4168-224">Get-MsolAccountSku</span><span class="sxs-lookup"><span data-stu-id="a4168-224">Get-MsolAccountSku</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691549)
    
- [<span data-ttu-id="a4168-225">Neue MsolLicenseOptions</span><span class="sxs-lookup"><span data-stu-id="a4168-225">New-MsolLicenseOptions</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691546)
    
- [<span data-ttu-id="a4168-226">Get-MsolUser</span><span class="sxs-lookup"><span data-stu-id="a4168-226">Get-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [<span data-ttu-id="a4168-227">New-MsolUser</span><span class="sxs-lookup"><span data-stu-id="a4168-227">New-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691547)
    
- [<span data-ttu-id="a4168-228">Set-MsolUserLicense</span><span class="sxs-lookup"><span data-stu-id="a4168-228">Set-MsolUserLicense</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691548)
    
- [<span data-ttu-id="a4168-229">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="a4168-229">ForEach-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [<span data-ttu-id="a4168-230">Where-Object</span><span class="sxs-lookup"><span data-stu-id="a4168-230">Where-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    
[<span data-ttu-id="a4168-231">Zurück zum Seitenanfang</span><span class="sxs-lookup"><span data-stu-id="a4168-231">Return to top</span></span>](disable-access-to-services-with-office-365-powershell.md#RTT)
  

