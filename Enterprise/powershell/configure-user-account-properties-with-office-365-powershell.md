---
title: Konfigurieren von Eigenschaften eines Benutzerkontos mit Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 10/07/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- O365ITProTrain
- Ent_Office_Other
- PowerShell
ms.assetid: 30813f8d-b08d-444b-98c1-53df7c29b4d7
description: 'Zusammenfassung: Informationen zum Verwenden von Office 365 PowerShell zum Konfigurieren der Eigenschaften für einzelne oder mehrere Benutzerkonten in Ihrem Office 365-Mandanten.'
ms.openlocfilehash: 67ce7d3c57f286f0b2365aa2503fdf1c8bc13429
ms.sourcegitcommit: 4b057db053e93b0165f1ec6c4799cff4c2852566
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/25/2019
ms.locfileid: "39257656"
---
# <a name="configure-user-account-properties-with-office-365-powershell"></a><span data-ttu-id="c30df-103">Konfigurieren von Eigenschaften eines Benutzerkontos mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="c30df-103">Configure user account properties with Office 365 PowerShell</span></span>

 <span data-ttu-id="c30df-104">**Zusammenfassung:** Informationen zum Verwenden von Office 365 PowerShell zum Konfigurieren der Eigenschaften für einzelne oder mehrere Benutzerkonten in Ihrem Office 365-Mandanten.</span><span class="sxs-lookup"><span data-stu-id="c30df-104">**Summary:** Use Office 365 PowerShell to configure properties of individual or multiple user accounts in your Office 365 tenant.</span></span>
  
<span data-ttu-id="c30df-105">Obwohl Sie das Microsoft 365 Admin Center zum Konfigurieren von Eigenschaften für die Benutzerkonten Ihres Office 365 Mandanten verwenden können, können Sie auch Office 365 PowerShell verwenden und einige Dinge tun, die das Admin Center nicht kann.</span><span class="sxs-lookup"><span data-stu-id="c30df-105">Although you can use the Microsoft 365 admin center to configure properties for the user accounts of your Office 365 tenant, you can also use Office 365 PowerShell and do some things that the admin center cannot.</span></span>
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="c30df-106">Verwenden der Azure Active Directory PowerShell für Graph-Module</span><span class="sxs-lookup"><span data-stu-id="c30df-106">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="c30df-107">Verwenden Sie zum Konfigurieren von Eigenschaften für Benutzerkonten mit der Azure Active Directory PowerShell das [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0)-Cmdlet und geben Sie die Eigenschaften an, die Sie festlegen bzw. ändern möchten.</span><span class="sxs-lookup"><span data-stu-id="c30df-107">To configure properties for user accounts with the Azure Active Directory PowerShell for Graph module, you use the [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="c30df-108">Verbinden Sie sich zuerst [mit Ihrem Office 365-Mandanten](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="c30df-108">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
   
### <a name="change-properties-for-a-specific-user-account"></a><span data-ttu-id="c30df-109">Ändern von Eigenschaften für ein bestimmtes Benutzerkonto</span><span class="sxs-lookup"><span data-stu-id="c30df-109">Change properties for a specific user account</span></span>

<span data-ttu-id="c30df-p101">Sie identifizieren das Konto mit dem **-ObjectID**-Parameter und legen bestimmte Eigenschaften mit weiteren Parametern fest bzw. ändern diese. Nachfolgend ist eine Liste der am häufigsten verwendeten Parameter aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="c30df-p101">You identify the account with the **-ObjectID** parameter and set or change specific properties with additional parameters. Here's a list of the most common parameters.</span></span>
  
- <span data-ttu-id="c30df-112">-Department „\<Abteilungsname>“</span><span class="sxs-lookup"><span data-stu-id="c30df-112">-Department "\<department name>"</span></span>
    
- <span data-ttu-id="c30df-113">-DisplayName „\<Vollständiger Benutzername>“</span><span class="sxs-lookup"><span data-stu-id="c30df-113">-DisplayName "\<full user name>"</span></span>
    
- <span data-ttu-id="c30df-114">-FacsimilieTelephoneNumber „\<Faxnummer>“</span><span class="sxs-lookup"><span data-stu-id="c30df-114">-FacsimilieTelephoneNumber "\<fax number>"</span></span>
    
- <span data-ttu-id="c30df-115">-GivenName „\<Vorname des Benutzers>“</span><span class="sxs-lookup"><span data-stu-id="c30df-115">-GivenName "\<user first name>"</span></span>
    
- <span data-ttu-id="c30df-116">-Surname „\<Nachname des Benutzers>“</span><span class="sxs-lookup"><span data-stu-id="c30df-116">-Surname "\<user last name>"</span></span>
    
- <span data-ttu-id="c30df-117">-Mobile „\<Mobiltelefonnummer>“</span><span class="sxs-lookup"><span data-stu-id="c30df-117">-Mobile "\<mobile phone number>"</span></span>
    
- <span data-ttu-id="c30df-118">-JobTitle „\<Position>“</span><span class="sxs-lookup"><span data-stu-id="c30df-118">-JobTitle "\<job title>"</span></span>
    
- <span data-ttu-id="c30df-119">-PreferredLanguage „\<Sprache>“</span><span class="sxs-lookup"><span data-stu-id="c30df-119">-PreferredLanguage "\<language>"</span></span>
    
- <span data-ttu-id="c30df-120">-StreetAddress „\<Adresse>“</span><span class="sxs-lookup"><span data-stu-id="c30df-120">-StreetAddress "\<street address>"</span></span>
    
- <span data-ttu-id="c30df-121">-City „\<Ortsname>“</span><span class="sxs-lookup"><span data-stu-id="c30df-121">-City "\<city name>"</span></span>
    
- <span data-ttu-id="c30df-122">-State „\<Bundesland/Kanton>“</span><span class="sxs-lookup"><span data-stu-id="c30df-122">-State "\<state name>"</span></span>
    
- <span data-ttu-id="c30df-123">-PostalCode „\<Postleitzahl>“</span><span class="sxs-lookup"><span data-stu-id="c30df-123">-PostalCode "\<postal code>"</span></span>
    
- <span data-ttu-id="c30df-124">-Country „\<Ländername>“</span><span class="sxs-lookup"><span data-stu-id="c30df-124">-Country "\<country name>"</span></span>
    
- <span data-ttu-id="c30df-125">-TelephoneNumber „\<Telefon Büro>“</span><span class="sxs-lookup"><span data-stu-id="c30df-125">-TelephoneNumber "\<office phone number>"</span></span>
    
- <span data-ttu-id="c30df-126">-UsageLocation „\<Zweistelliger Länder- oder Regionalcode>“</span><span class="sxs-lookup"><span data-stu-id="c30df-126">-UsageLocation "\<2-character country or region code>"</span></span>
    
    <span data-ttu-id="c30df-127">Dies ist der zweistellige ISO 3166-1-Ländercode bzw. Regionscode (Alpha-2, A2).</span><span class="sxs-lookup"><span data-stu-id="c30df-127">This is the ISO 3166-1 alpha-2 (A2) two-letter country or region code.</span></span>
    
<span data-ttu-id="c30df-128">Informationen zu weiteren Parametern finden Sie unter [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0).</span><span class="sxs-lookup"><span data-stu-id="c30df-128">See [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) for additional parameters.</span></span>


<span data-ttu-id="c30df-129">Führen Sie den folgenden Befehl aus, um den Benutzerprinzipalnamen für Ihre Benutzerkonten anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="c30df-129">To display the User Principal Name for your user accounts, run the following command.</span></span>
  
```powershell
Get-AzureADUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

<span data-ttu-id="c30df-130">Dieser Befehl weist Office 365 PowerShell zu folgenden Aktionen an:</span><span class="sxs-lookup"><span data-stu-id="c30df-130">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="c30df-131">Alle Informationen der Benutzerkonten abrufen (**Get-AzureADUser**) und an den nächsten Befehl senden (**|**).</span><span class="sxs-lookup"><span data-stu-id="c30df-131">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="c30df-132">Liste der Benutzerprinzipalnamen alphabetisch sortieren (**Sort-Object UserPrincipalName**) und an den nächsten Befehl senden (**|**).</span><span class="sxs-lookup"><span data-stu-id="c30df-132">Sort the list of User Principal Names alphabetically ( **Sort-Object UserPrincipalName** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="c30df-133">Nur die UserPrincipalName-Eigenschaft für jedes Konto anzeigen ( **Select-Object UserPrincipalName** ).</span><span class="sxs-lookup"><span data-stu-id="c30df-133">Display just the User Principal Name property for each account ( **Select-Object UserPrincipalName** ).</span></span>
- <span data-ttu-id="c30df-134">Jeweils auf einem Bildschirm anzeigen ( **More** ).</span><span class="sxs-lookup"><span data-stu-id="c30df-134">Display them one screen at a time ( **More** ).</span></span>
    
<span data-ttu-id="c30df-p102">Mit diesem Befehl werden alle Ihre Konten aufgelistet. Wenn der Benutzerprinzipalname für ein Konto basierend auf dem Anzeigenamen (Vor- und Nachname) angezeigt werden soll, geben Sie die **$userName**-Variable unten ein (entfernen Sie die Zeichen „\<“ und „>“), und führen Sie die folgenden Befehle aus:</span><span class="sxs-lookup"><span data-stu-id="c30df-p102">This command will list all of your accounts. If you want to display the User Principal Name for an account based on its display name (first and last name), fill in the **$userName** variable below (removing the \< and > characters), and then run the following commands:</span></span>
  
```powershell
$userName="<Display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="c30df-137">In diesem Beispiel wird der Benutzerprinzipalname für das Benutzerkonto mit dem Anzeigename Caleb Sills angezeigt.</span><span class="sxs-lookup"><span data-stu-id="c30df-137">This example displays the User Principal Name for the user account with the display name of Caleb Sills.</span></span>
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="c30df-p103">Mit der **$upn**-Variable können Sie Änderungen an den einzelnen Konten basierend auf deren Anzeigenamen vornehmen. Hier ist ein Beispiel für das Festlegen des Verwendungsstandorts von Belinda Newman in Frankreich. Dabei wird Ihr Anzeigenamen anstatt Ihres Benutzerprinzipalnamens verwendet:</span><span class="sxs-lookup"><span data-stu-id="c30df-p103">By using a **$upn** variable, you can make changes to individual accounts based on their display name. Here is an example of setting Belinda Newman's usage location to France, but specifying her display name rather than her User Principal Name:</span></span>
  
```powershell
$userName="Belinda Newman"
$upn=(Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-AzureADUser -ObjectID $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a><span data-ttu-id="c30df-140">Ändern von Eigenschaften für alle Benutzerkonten</span><span class="sxs-lookup"><span data-stu-id="c30df-140">Change properties for all user accounts</span></span>

<span data-ttu-id="c30df-p104">Um die Eigenschaften für alle Benutzer zu ändern, können Sie eine Kombination der Cmdlets **Get-AzureADUser** und **et-AzureADUser** verwenden. Im folgende Beispiel wird der Verwendungsstandort für alle Benutzer in Frankreich geändert:</span><span class="sxs-lookup"><span data-stu-id="c30df-p104">To change properties for all users, you can use the combination of the **Get-AzureADUser** and **Set-AzureADUser** cmdlets. The following example changes the usage location for all users to France:</span></span>
  
```powershell
Get-AzureADUser | Set-AzureADUser -UsageLocation "FR"
```

<span data-ttu-id="c30df-143">Dieser Befehl gibt Office 365 Powershell die folgenden Anweisungen:</span><span class="sxs-lookup"><span data-stu-id="c30df-143">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="c30df-144">Alle Informationen der Benutzerkonten abrufen (**Get-AzureADUser**) und an den nächsten Befehl senden (**|**).</span><span class="sxs-lookup"><span data-stu-id="c30df-144">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="c30df-145">Benutzerstandort auf „Frankreich“ festlegen (**Set-AzureADUser –UsageLocation "FR"**).</span><span class="sxs-lookup"><span data-stu-id="c30df-145">Set the user location to France ( **Set-AzureADUser -UsageLocation "FR"** ).</span></span>
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a><span data-ttu-id="c30df-146">Ändern von Eigenschaften für bestimmte Benutzerkonten</span><span class="sxs-lookup"><span data-stu-id="c30df-146">Change properties for a specific set of user accounts</span></span>

<span data-ttu-id="c30df-p105">Um die Eigenschaften für einen bestimmten Satz von Benutzerkonten zu ändern, können Sie eine Kombination der Cmdlets **Get-AzureADUser**, **Where** und **Set-AzureADUser** verwenden. Im folgende Beispiel wird der Verwendungsstandort für alle Benutzer in der Buchhaltungsabteilung in Frankreich geändert:</span><span class="sxs-lookup"><span data-stu-id="c30df-p105">To change properties for a specific set of user account, you can use the combination of the **Get-AzureADUser**, **Where**, and **Set-AzureADUser** cmdlets. The following example changes the usage location for all the users in the Accounting department to France:</span></span>
  
```powershell
Get-AzureADUser | Where-Object {$_.Department -eq "Accounting"} | Set-AzureADUser -UsageLocation "FR"
```

<span data-ttu-id="c30df-149">Dieser Befehl gibt Office 365 Powershell die folgenden Anweisungen:</span><span class="sxs-lookup"><span data-stu-id="c30df-149">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="c30df-150">Alle Informationen der Benutzerkonten abrufen (**Get-AzureADUser**) und an den nächsten Befehl senden (**|**).</span><span class="sxs-lookup"><span data-stu-id="c30df-150">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="c30df-151">Alle Benutzerkonten suchen, bei denen für die Eigenschaft „Abteilung" der Wert „Buchhaltung" festgelegt ist ( **Where{$_.Department -eq "Accounting"}** ) und die resultierenden Informationen an den nächsten Befehl senden (  **|**).</span><span class="sxs-lookup"><span data-stu-id="c30df-151">Find all of the user accounts that have their Department property set to "Accounting" ( **Where {$_.Department -eq "Accounting"}** ) and send the resulting information to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="c30df-152">Benutzerstandort auf „Frankreich“ festlegen (**Set-AzureADUser –UsageLocation "FR"**).</span><span class="sxs-lookup"><span data-stu-id="c30df-152">Set the user location to France ( **Set-AzureADUser -UsageLocation "FR"** ).</span></span>
    
## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="c30df-153">Verwenden des Microsoft Azure Active Directory-Moduls für Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="c30df-153">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="c30df-154">Verwenden Sie zum Konfigurieren von Eigenschaften für Benutzerkonten mit dem Azure Active Directory-Modul für Windows PowerShell das Set-MsolUser-Cmdlet und geben Sie die Eigenschaften an, die Sie festlegen bzw. ändern möchten.</span><span class="sxs-lookup"><span data-stu-id="c30df-154">To configure properties for user accounts with the Microsoft Azure Active Directory Module for Windows PowerShell, you use the Set-MsolUser cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="c30df-155">Verbinden Sie sich zuerst [mit Ihrem Office 365-Mandanten](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="c30df-155">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>
  
>[!Note]
><span data-ttu-id="c30df-156">PowerShell Core unterstützt das Microsoft Azure Active Directory Modul für Windows PowerShell Modul und Cmdlets mit **MSOL** nicht in Ihrem Namen.</span><span class="sxs-lookup"><span data-stu-id="c30df-156">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="c30df-157">Um diese Cmdlets weiterhin verwenden zu können, müssen Sie diese von Windows PowerShell aus ausführen.</span><span class="sxs-lookup"><span data-stu-id="c30df-157">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

### <a name="change-properties-for-a-specific-user-account"></a><span data-ttu-id="c30df-158">Ändern von Eigenschaften für ein bestimmtes Benutzerkonto</span><span class="sxs-lookup"><span data-stu-id="c30df-158">Change properties for a specific user account</span></span>

<span data-ttu-id="c30df-159">Verwenden Sie zum Konfigurieren der Eigenschaften für ein bestimmtes Benutzerkonto das [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx)-Cmdlet und geben die Eigenschaften an, die festgelegt oder geändert werden sollen.</span><span class="sxs-lookup"><span data-stu-id="c30df-159">To configure properties for a specific user account, you use the [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="c30df-p107">Sie identifizieren das Konto mit dem **-UserPrincipalName**-Parameter und legen bestimmte Eigenschaften mit weiteren Parametern fest bzw. ändern diese. Nachfolgend ist eine Liste der am häufigsten verwendeten Parameter aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="c30df-p107">You identify the account with the **-UserPrincipalName** parameter and set or change specific properties with additional parameters. Here is a list of the most common parameters.</span></span>
  
- <span data-ttu-id="c30df-162">-City „\<Ortsname>“</span><span class="sxs-lookup"><span data-stu-id="c30df-162">-City "\<city name>"</span></span>
    
- <span data-ttu-id="c30df-163">-Country „\<Ländername>“</span><span class="sxs-lookup"><span data-stu-id="c30df-163">-Country "\<country name>"</span></span>
    
- <span data-ttu-id="c30df-164">-Department „\<Abteilungsname>“</span><span class="sxs-lookup"><span data-stu-id="c30df-164">-Department "\<department name>"</span></span>
    
- <span data-ttu-id="c30df-165">-DisplayName „\<Vollständiger Benutzername>“</span><span class="sxs-lookup"><span data-stu-id="c30df-165">-DisplayName "\<full user name>"</span></span>
    
- <span data-ttu-id="c30df-166">-Fax „\<Faxnummer>“</span><span class="sxs-lookup"><span data-stu-id="c30df-166">-Fax "\<fax number>"</span></span>
    
- <span data-ttu-id="c30df-167">-FirstName „\<Vorname des Benutzers>“</span><span class="sxs-lookup"><span data-stu-id="c30df-167">-FirstName "\<user first name>"</span></span>
    
- <span data-ttu-id="c30df-168">-LastName „\<Nachname des Benutzers>“</span><span class="sxs-lookup"><span data-stu-id="c30df-168">-LastName "\<user last name>"</span></span>
    
- <span data-ttu-id="c30df-169">-MobilePhone „\<Mobiltelefonnummer>“</span><span class="sxs-lookup"><span data-stu-id="c30df-169">-MobilePhone "\<mobile phone number>"</span></span>
    
- <span data-ttu-id="c30df-170">-Office „\<Standort des Büros>“</span><span class="sxs-lookup"><span data-stu-id="c30df-170">-Office "\<office location>"</span></span>
    
- <span data-ttu-id="c30df-171">-PhoneNumber „\<Telefon Büro>“</span><span class="sxs-lookup"><span data-stu-id="c30df-171">-PhoneNumber "\<office phone number>"</span></span>
    
- <span data-ttu-id="c30df-172">-PostalCode „\<Postleitzahl>“</span><span class="sxs-lookup"><span data-stu-id="c30df-172">-PostalCode "\<postal code>"</span></span>
    
- <span data-ttu-id="c30df-173">-PreferredLanguage „\<Sprache>“</span><span class="sxs-lookup"><span data-stu-id="c30df-173">-PreferredLanguage "\<language>"</span></span>
    
- <span data-ttu-id="c30df-174">-State „\<Bundesland/Kanton>“</span><span class="sxs-lookup"><span data-stu-id="c30df-174">-State "\<state name>"</span></span>
    
- <span data-ttu-id="c30df-175">-StreetAddress „\<Adresse>“</span><span class="sxs-lookup"><span data-stu-id="c30df-175">-StreetAddress "\<street address>"</span></span>
    
- <span data-ttu-id="c30df-176">-Title „\<Titel>“</span><span class="sxs-lookup"><span data-stu-id="c30df-176">-Title "\<title name>"</span></span>
    
- <span data-ttu-id="c30df-177">-UsageLocation „\<Zweistelliger Länder- oder Regionalcode>“</span><span class="sxs-lookup"><span data-stu-id="c30df-177">-UsageLocation "\<2-character country or region code>"</span></span>
    
    <span data-ttu-id="c30df-178">Dies ist der zweistellige ISO 3166-1-Ländercode bzw. Regionscode (Alpha-2, A2).</span><span class="sxs-lookup"><span data-stu-id="c30df-178">This is the ISO 3166-1 alpha-2 (A2) two-letter country or region code.</span></span>
    
<span data-ttu-id="c30df-179">Informationen zu weiteren Parametern finden Sie unter [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx).</span><span class="sxs-lookup"><span data-stu-id="c30df-179">See [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) for additional parameters.</span></span>

<span data-ttu-id="c30df-180">Führen Sie den folgenden Befehl aus, um die Benutzerprinzipalnamen aller Benutzer anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="c30df-180">To see the User Principal Names of all your users, run the following command.</span></span>
  
```powershell
Get-MSolUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

<span data-ttu-id="c30df-181">Dieser Befehl weist Office 365 PowerShell zu folgenden Aktionen an:</span><span class="sxs-lookup"><span data-stu-id="c30df-181">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="c30df-182">Alle Informationen der Benutzerkonten abrufen (**Get-MsolUser**) und an den nächsten Befehl senden (**|**).</span><span class="sxs-lookup"><span data-stu-id="c30df-182">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="c30df-183">Liste der Benutzerprinzipalnamen alphabetisch sortieren (**Sort-Object UserPrincipalName**) und an den nächsten Befehl senden (**|**).</span><span class="sxs-lookup"><span data-stu-id="c30df-183">Sort the list of User Principal Names alphabetically ( **Sort-Object UserPrincipalName** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="c30df-184">Nur die UserPrincipalName-Eigenschaft für jedes Konto anzeigen ( **Select-Object UserPrincipalName** ).</span><span class="sxs-lookup"><span data-stu-id="c30df-184">Display just the User Principal Name property for each account ( **Select-Object UserPrincipalName** ).</span></span>
    
- <span data-ttu-id="c30df-185">Jeweils auf einem Bildschirm anzeigen ( **More** ).</span><span class="sxs-lookup"><span data-stu-id="c30df-185">Display them one screen at a time ( **More** ).</span></span>
    
<span data-ttu-id="c30df-p108">Mit diesem Befehl werden alle Ihre Konten aufgelistet. Wenn der Benutzerprinzipalname für ein Konto basierend auf dem Anzeigenamen (Vor- und Nachname) angezeigt werden soll, geben Sie die **$userName**-Variable unten ein (entfernen Sie die Zeichen „\<" und „>"), und führen Sie die folgenden Befehle aus:</span><span class="sxs-lookup"><span data-stu-id="c30df-p108">This command will list all of your accounts. If you want to display the User Principal Name for an account based on its display name (first and last name), fill in the **$userName** variable below (removing the \< and > characters), and then run the following commands:</span></span>
  
```powershell
$userName="<Display name>"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="c30df-188">In diesem Beispiel wird der Benutzerprinzipalname für den Benutzer namens Caleb Sills angezeigt.</span><span class="sxs-lookup"><span data-stu-id="c30df-188">This example displays the User Principal Name for the user named Caleb Sills.</span></span>
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="c30df-p109">Mit der **$upn** -Variable können Sie Änderungen an den einzelnen Konten basierend auf deren Anzeigenamen vornehmen. Hier ist ein Beispiel für das Festlegen des Verwendungsstandorts von Belinda Newman in Frankreich. Dabei wird Ihr Anzeigenamen anstatt Ihres Benutzerprinzipalnamens verwendet:</span><span class="sxs-lookup"><span data-stu-id="c30df-p109">By using a **$upn** variable, you can make changes to individual accounts based on their display name. Here is an example of setting Belinda Newman's usage location to France, but specifying her display name rather than her User Principal Name:</span></span>
  
```powershell
$userName="<display name>"
$upn=(Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-MsolUser -UserPrincipalName $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a><span data-ttu-id="c30df-191">Ändern von Eigenschaften für alle Benutzerkonten</span><span class="sxs-lookup"><span data-stu-id="c30df-191">Change properties for all user accounts</span></span>

<span data-ttu-id="c30df-p110">Um die Eigenschaften für alle Benutzer zu ändern, können Sie eine Kombination der Cmdlets **Get-MsolUser** und **Set-MsolUser** verwenden. Im folgende Beispiel wird der Verwendungsstandort für alle Benutzer in Frankreich geändert:</span><span class="sxs-lookup"><span data-stu-id="c30df-p110">To change properties for all users, you can use the combination of the **Get-MsolUser** and **Set-MsolUser** cmdlets. The following example changes the usage location for all users to France:</span></span>
  
```powershell
Get-MsolUser | Set-MsolUser -UsageLocation "FR"
```

<span data-ttu-id="c30df-194">Dieser Befehl weist Office 365 PowerShell zu folgenden Aktionen an:</span><span class="sxs-lookup"><span data-stu-id="c30df-194">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="c30df-195">Alle Informationen der Benutzerkonten abrufen (**Get-MsolUser**) und an den nächsten Befehl senden (**|**).</span><span class="sxs-lookup"><span data-stu-id="c30df-195">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="c30df-196">Benutzerstandort auf „Frankreich" festlegen ( **Set-MsolUser -UsageLocation "FR"** ).</span><span class="sxs-lookup"><span data-stu-id="c30df-196">Set the user location to France ( **Set-MsolUser -UsageLocation "FR"** ).</span></span>
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a><span data-ttu-id="c30df-197">Ändern von Eigenschaften für bestimmte Benutzerkonten</span><span class="sxs-lookup"><span data-stu-id="c30df-197">Change properties for a specific set of user accounts</span></span>

<span data-ttu-id="c30df-p111">Um die Eigenschaften für einen bestimmten Satz von Benutzerkonten zu ändern, können Sie eine Kombination der Cmdlets **Get-MsolUser**, **Where-Object** und **Set-MsolUser** verwenden. Im folgende Beispiel wird der Verwendungsstandort für alle Benutzer in der Buchhaltungsabteilung in Frankreich geändert:</span><span class="sxs-lookup"><span data-stu-id="c30df-p111">To change properties for a specific set of user account, you can use the combination of the **Get-MsolUser**, **Where-Object**, and **Set-MsolUser** cmdlets. The following example changes the usage location for all the users in the Accounting department to France:</span></span>
  
```powershell
Get-MsolUser | Where-Object {$_.Department -eq "Accounting"} | Set-MsolUser -UsageLocation "FR"
```

<span data-ttu-id="c30df-200">Dieser Befehl weist Office 365 PowerShell zu folgenden Aktionen an:</span><span class="sxs-lookup"><span data-stu-id="c30df-200">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="c30df-201">Alle Informationen der Benutzerkonten abrufen (**Get-MsolUser**) und an den nächsten Befehl senden (**|**).</span><span class="sxs-lookup"><span data-stu-id="c30df-201">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="c30df-202">Alle Benutzerkonten suchen, bei denen für die Eigenschaft „Abteilung" der Wert „Buchhaltung" festgelegt ist ( **Where-Object {$_.Department -eq "Accounting"}** ) und die resultierenden Informationen an den nächsten Befehl senden ( **|**).</span><span class="sxs-lookup"><span data-stu-id="c30df-202">Find all of the user accounts that have their Department property set to "Accounting" ( **Where-Object {$_.Department -eq "Accounting"}** ) and send the resulting information to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="c30df-203">Benutzerstandort auf „Frankreich" festlegen ( **Set-MsolUser -UsageLocation "FR"** ).</span><span class="sxs-lookup"><span data-stu-id="c30df-203">Set the user location to France ( **Set-MsolUser -UsageLocation "FR"** ).</span></span>
    

## <a name="see-also"></a><span data-ttu-id="c30df-204">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="c30df-204">See also</span></span>

[<span data-ttu-id="c30df-205">Verwalten von Benutzerkonten und Lizenzen mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="c30df-205">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="c30df-206">Verwalten von Office 365 mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="c30df-206">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="c30df-207">Erste Schritte mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="c30df-207">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
