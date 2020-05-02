---
title: Konfigurieren von Eigenschaften eines Benutzerkontos mit Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/16/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- O365ITProTrain
- Ent_Office_Other
- PowerShell
ms.assetid: 30813f8d-b08d-444b-98c1-53df7c29b4d7
description: 'Zusammenfassung: Informationen zum Verwenden von Office 365 PowerShell zum Konfigurieren der Eigenschaften für einzelne oder mehrere Benutzerkonten in Ihrem Office 365-Mandanten.'
ms.openlocfilehash: 5748bd382357168e4184754fb49fb7304e2d2474
ms.sourcegitcommit: d1022143bdefdd5583d8eff08046808657b49c94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/02/2020
ms.locfileid: "44004718"
---
# <a name="configure-user-account-properties-with-office-365-powershell"></a><span data-ttu-id="ee0e5-103">Konfigurieren von Eigenschaften eines Benutzerkontos mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="ee0e5-103">Configure user account properties with Office 365 PowerShell</span></span>

<span data-ttu-id="ee0e5-104">Obwohl Sie das Microsoft 365 Admin Center zum Konfigurieren von Eigenschaften für die Benutzerkonten Ihres Office 365 Mandanten verwenden können, können Sie auch Office 365 PowerShell verwenden und einige Dinge tun, die das Admin Center nicht kann.</span><span class="sxs-lookup"><span data-stu-id="ee0e5-104">Although you can use the Microsoft 365 admin center to configure properties for the user accounts of your Office 365 tenant, you can also use Office 365 PowerShell and do some things that the admin center cannot.</span></span>
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="ee0e5-105">Verwenden der Azure Active Directory PowerShell für Graph-Module</span><span class="sxs-lookup"><span data-stu-id="ee0e5-105">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="ee0e5-106">Verwenden Sie zum Konfigurieren von Eigenschaften für Benutzerkonten mit der Azure Active Directory PowerShell das [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0)-Cmdlet und geben Sie die Eigenschaften an, die Sie festlegen bzw. ändern möchten.</span><span class="sxs-lookup"><span data-stu-id="ee0e5-106">To configure properties for user accounts with the Azure Active Directory PowerShell for Graph module, you use the [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="ee0e5-107">Verbinden Sie sich zuerst [mit Ihrem Office 365-Mandanten](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="ee0e5-107">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
   
### <a name="change-properties-for-a-specific-user-account"></a><span data-ttu-id="ee0e5-108">Ändern von Eigenschaften für ein bestimmtes Benutzerkonto</span><span class="sxs-lookup"><span data-stu-id="ee0e5-108">Change properties for a specific user account</span></span>

<span data-ttu-id="ee0e5-p101">Sie identifizieren das Konto mit dem **-ObjectID**-Parameter und legen bestimmte Eigenschaften mit weiteren Parametern fest bzw. ändern diese. Nachfolgend ist eine Liste der am häufigsten verwendeten Parameter aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="ee0e5-p101">You identify the account with the **-ObjectID** parameter and set or change specific properties with additional parameters. Here's a list of the most common parameters.</span></span>
  
- <span data-ttu-id="ee0e5-111">-Department „\<Abteilungsname>“</span><span class="sxs-lookup"><span data-stu-id="ee0e5-111">-Department "\<department name>"</span></span>
    
- <span data-ttu-id="ee0e5-112">-DisplayName „\<Vollständiger Benutzername>“</span><span class="sxs-lookup"><span data-stu-id="ee0e5-112">-DisplayName "\<full user name>"</span></span>
    
- <span data-ttu-id="ee0e5-113">-FacsimilieTelephoneNumber „\<Faxnummer>“</span><span class="sxs-lookup"><span data-stu-id="ee0e5-113">-FacsimilieTelephoneNumber "\<fax number>"</span></span>
    
- <span data-ttu-id="ee0e5-114">-GivenName „\<Vorname des Benutzers>“</span><span class="sxs-lookup"><span data-stu-id="ee0e5-114">-GivenName "\<user first name>"</span></span>
    
- <span data-ttu-id="ee0e5-115">-Surname „\<Nachname des Benutzers>“</span><span class="sxs-lookup"><span data-stu-id="ee0e5-115">-Surname "\<user last name>"</span></span>
    
- <span data-ttu-id="ee0e5-116">-Mobile „\<Mobiltelefonnummer>“</span><span class="sxs-lookup"><span data-stu-id="ee0e5-116">-Mobile "\<mobile phone number>"</span></span>
    
- <span data-ttu-id="ee0e5-117">-JobTitle „\<Position>“</span><span class="sxs-lookup"><span data-stu-id="ee0e5-117">-JobTitle "\<job title>"</span></span>
    
- <span data-ttu-id="ee0e5-118">-PreferredLanguage „\<Sprache>“</span><span class="sxs-lookup"><span data-stu-id="ee0e5-118">-PreferredLanguage "\<language>"</span></span>
    
- <span data-ttu-id="ee0e5-119">-StreetAddress „\<Adresse>“</span><span class="sxs-lookup"><span data-stu-id="ee0e5-119">-StreetAddress "\<street address>"</span></span>
    
- <span data-ttu-id="ee0e5-120">-City „\<Ortsname>“</span><span class="sxs-lookup"><span data-stu-id="ee0e5-120">-City "\<city name>"</span></span>
    
- <span data-ttu-id="ee0e5-121">-State „\<Bundesland/Kanton>“</span><span class="sxs-lookup"><span data-stu-id="ee0e5-121">-State "\<state name>"</span></span>
    
- <span data-ttu-id="ee0e5-122">-PostalCode „\<Postleitzahl>“</span><span class="sxs-lookup"><span data-stu-id="ee0e5-122">-PostalCode "\<postal code>"</span></span>
    
- <span data-ttu-id="ee0e5-123">-Country „\<Ländername>“</span><span class="sxs-lookup"><span data-stu-id="ee0e5-123">-Country "\<country name>"</span></span>
    
- <span data-ttu-id="ee0e5-124">-TelephoneNumber „\<Telefon Büro>“</span><span class="sxs-lookup"><span data-stu-id="ee0e5-124">-TelephoneNumber "\<office phone number>"</span></span>
    
- <span data-ttu-id="ee0e5-125">-UsageLocation „\<Zweistelliger Länder- oder Regionalcode>“</span><span class="sxs-lookup"><span data-stu-id="ee0e5-125">-UsageLocation "\<2-character country or region code>"</span></span>
    
    <span data-ttu-id="ee0e5-126">Dies ist der zweistellige ISO 3166-1-Ländercode bzw. Regionscode (Alpha-2, A2).</span><span class="sxs-lookup"><span data-stu-id="ee0e5-126">This is the ISO 3166-1 alpha-2 (A2) two-letter country or region code.</span></span>
    
<span data-ttu-id="ee0e5-127">Informationen zu weiteren Parametern finden Sie unter [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0).</span><span class="sxs-lookup"><span data-stu-id="ee0e5-127">See [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) for additional parameters.</span></span>


<span data-ttu-id="ee0e5-128">Führen Sie den folgenden Befehl aus, um den Benutzerprinzipalnamen für Ihre Benutzerkonten anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="ee0e5-128">To display the User Principal Name for your user accounts, run the following command.</span></span>
  
```powershell
Get-AzureADUser | Sort UserPrincipalName | Select UserPrincipalName | More
```

<span data-ttu-id="ee0e5-129">Dieser Befehl weist Office 365 PowerShell zu folgenden Aktionen an:</span><span class="sxs-lookup"><span data-stu-id="ee0e5-129">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="ee0e5-130">Alle Informationen der Benutzerkonten abrufen (**Get-AzureADUser**) und an den nächsten Befehl senden (**|**).</span><span class="sxs-lookup"><span data-stu-id="ee0e5-130">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="ee0e5-131">Sortieren Sie die Liste der Benutzerprinzipalnamen in alphabetischer Reihenfolge ( **Sort userPrincipalName** ), und senden Sie **|** Sie an den nächsten Befehl ().</span><span class="sxs-lookup"><span data-stu-id="ee0e5-131">Sort the list of User Principal Names alphabetically ( **Sort UserPrincipalName** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="ee0e5-132">Zeigt nur die Benutzerprinzipalnamen-Eigenschaft für jedes Konto an ( **Wählen Sie userPrincipalName** ) aus.</span><span class="sxs-lookup"><span data-stu-id="ee0e5-132">Display just the User Principal Name property for each account ( **Select UserPrincipalName** ).</span></span>

- <span data-ttu-id="ee0e5-133">Jeweils auf einem Bildschirm anzeigen ( **More** ).</span><span class="sxs-lookup"><span data-stu-id="ee0e5-133">Display them one screen at a time ( **More** ).</span></span>
    
<span data-ttu-id="ee0e5-p102">Mit diesem Befehl werden alle Ihre Konten aufgelistet. Wenn der Benutzerprinzipalname für ein Konto basierend auf dem Anzeigenamen (Vor- und Nachname) angezeigt werden soll, geben Sie die **$userName**-Variable unten ein (entfernen Sie die Zeichen „\<“ und „>“), und führen Sie die folgenden Befehle aus:</span><span class="sxs-lookup"><span data-stu-id="ee0e5-p102">This command will list all of your accounts. If you want to display the User Principal Name for an account based on its display name (first and last name), fill in the **$userName** variable below (removing the \< and > characters), and then run the following commands:</span></span>
  
```powershell
$userName="<Display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="ee0e5-136">In diesem Beispiel wird der Benutzerprinzipalname für das Benutzerkonto mit dem Anzeigename Caleb Sills angezeigt.</span><span class="sxs-lookup"><span data-stu-id="ee0e5-136">This example displays the User Principal Name for the user account with the display name of Caleb Sills.</span></span>
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="ee0e5-p103">Mit der **$upn**-Variable können Sie Änderungen an den einzelnen Konten basierend auf deren Anzeigenamen vornehmen. Hier ist ein Beispiel für das Festlegen des Verwendungsstandorts von Belinda Newman in Frankreich. Dabei wird Ihr Anzeigenamen anstatt Ihres Benutzerprinzipalnamens verwendet:</span><span class="sxs-lookup"><span data-stu-id="ee0e5-p103">By using a **$upn** variable, you can make changes to individual accounts based on their display name. Here is an example of setting Belinda Newman's usage location to France, but specifying her display name rather than her User Principal Name:</span></span>
  
```powershell
$userName="Belinda Newman"
$upn=(Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-AzureADUser -ObjectID $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a><span data-ttu-id="ee0e5-139">Ändern von Eigenschaften für alle Benutzerkonten</span><span class="sxs-lookup"><span data-stu-id="ee0e5-139">Change properties for all user accounts</span></span>

<span data-ttu-id="ee0e5-p104">Um die Eigenschaften für alle Benutzer zu ändern, können Sie eine Kombination der Cmdlets **Get-AzureADUser** und **et-AzureADUser** verwenden. Im folgende Beispiel wird der Verwendungsstandort für alle Benutzer in Frankreich geändert:</span><span class="sxs-lookup"><span data-stu-id="ee0e5-p104">To change properties for all users, you can use the combination of the **Get-AzureADUser** and **Set-AzureADUser** cmdlets. The following example changes the usage location for all users to France:</span></span>
  
```powershell
Get-AzureADUser | Set-AzureADUser -UsageLocation "FR"
```

<span data-ttu-id="ee0e5-142">Dieser Befehl gibt Office 365 Powershell die folgenden Anweisungen:</span><span class="sxs-lookup"><span data-stu-id="ee0e5-142">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="ee0e5-143">Alle Informationen der Benutzerkonten abrufen (**Get-AzureADUser**) und an den nächsten Befehl senden (**|**).</span><span class="sxs-lookup"><span data-stu-id="ee0e5-143">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="ee0e5-144">Benutzerstandort auf „Frankreich“ festlegen (**Set-AzureADUser –UsageLocation "FR"**).</span><span class="sxs-lookup"><span data-stu-id="ee0e5-144">Set the user location to France ( **Set-AzureADUser -UsageLocation "FR"** ).</span></span>
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a><span data-ttu-id="ee0e5-145">Ändern von Eigenschaften für bestimmte Benutzerkonten</span><span class="sxs-lookup"><span data-stu-id="ee0e5-145">Change properties for a specific set of user accounts</span></span>

<span data-ttu-id="ee0e5-p105">Um die Eigenschaften für einen bestimmten Satz von Benutzerkonten zu ändern, können Sie eine Kombination der Cmdlets **Get-AzureADUser**, **Where** und **Set-AzureADUser** verwenden. Im folgende Beispiel wird der Verwendungsstandort für alle Benutzer in der Buchhaltungsabteilung in Frankreich geändert:</span><span class="sxs-lookup"><span data-stu-id="ee0e5-p105">To change properties for a specific set of user account, you can use the combination of the **Get-AzureADUser**, **Where**, and **Set-AzureADUser** cmdlets. The following example changes the usage location for all the users in the Accounting department to France:</span></span>
  
```powershell
Get-AzureADUser | Where {$_.Department -eq "Accounting"} | Set-AzureADUser -UsageLocation "FR"
```

<span data-ttu-id="ee0e5-148">Dieser Befehl gibt Office 365 Powershell die folgenden Anweisungen:</span><span class="sxs-lookup"><span data-stu-id="ee0e5-148">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="ee0e5-149">Alle Informationen der Benutzerkonten abrufen (**Get-AzureADUser**) und an den nächsten Befehl senden (**|**).</span><span class="sxs-lookup"><span data-stu-id="ee0e5-149">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="ee0e5-150">Alle Benutzerkonten suchen, bei denen für die Eigenschaft „Abteilung" der Wert „Buchhaltung" festgelegt ist ( **Where{$_.Department -eq "Accounting"}** ) und die resultierenden Informationen an den nächsten Befehl senden (  **|**).</span><span class="sxs-lookup"><span data-stu-id="ee0e5-150">Find all of the user accounts that have their Department property set to "Accounting" ( **Where {$_.Department -eq "Accounting"}** ) and send the resulting information to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="ee0e5-151">Benutzerstandort auf „Frankreich“ festlegen (**Set-AzureADUser –UsageLocation "FR"**).</span><span class="sxs-lookup"><span data-stu-id="ee0e5-151">Set the user location to France ( **Set-AzureADUser -UsageLocation "FR"** ).</span></span>
    
## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="ee0e5-152">Verwenden des Microsoft Azure Active Directory-Moduls für Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="ee0e5-152">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="ee0e5-153">Um Eigenschaften für Benutzerkonten mit dem Microsoft Azure Active Directory Modul für Windows PowerShell zu konfigurieren, verwenden Sie das Cmdlet " **MsolUser** " und geben die Eigenschaften an, die festgelegt oder geändert werden sollen.</span><span class="sxs-lookup"><span data-stu-id="ee0e5-153">To configure properties for user accounts with the Microsoft Azure Active Directory Module for Windows PowerShell, you use the **Set-MsolUser** cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="ee0e5-154">Verbinden Sie sich zuerst [mit Ihrem Office 365-Mandanten](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="ee0e5-154">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>
  
>[!Note]
><span data-ttu-id="ee0e5-155">PowerShell Core unterstützt nicht das Microsoft Azure Active Directory-Modul für Windows PowerShell und Cmdlets mit **Msol** im Namen.</span><span class="sxs-lookup"><span data-stu-id="ee0e5-155">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="ee0e5-156">Um diese Cmdlets weiterhin verwenden zu können, müssen Sie sie über Windows PowerShell ausführen.</span><span class="sxs-lookup"><span data-stu-id="ee0e5-156">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

### <a name="change-properties-for-a-specific-user-account"></a><span data-ttu-id="ee0e5-157">Ändern von Eigenschaften für ein bestimmtes Benutzerkonto</span><span class="sxs-lookup"><span data-stu-id="ee0e5-157">Change properties for a specific user account</span></span>

<span data-ttu-id="ee0e5-158">Verwenden Sie zum Konfigurieren der Eigenschaften für ein bestimmtes Benutzerkonto das [Set-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194136(v=azure.100))-Cmdlet und geben die Eigenschaften an, die festgelegt oder geändert werden sollen.</span><span class="sxs-lookup"><span data-stu-id="ee0e5-158">To configure properties for a specific user account, you use the [Set-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194136(v=azure.100)) cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="ee0e5-p107">Sie identifizieren das Konto mit dem **-UserPrincipalName**-Parameter und legen bestimmte Eigenschaften mit weiteren Parametern fest bzw. ändern diese. Nachfolgend ist eine Liste der am häufigsten verwendeten Parameter aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="ee0e5-p107">You identify the account with the **-UserPrincipalName** parameter and set or change specific properties with additional parameters. Here is a list of the most common parameters.</span></span>
  
- <span data-ttu-id="ee0e5-161">-City „\<Ortsname>“</span><span class="sxs-lookup"><span data-stu-id="ee0e5-161">-City "\<city name>"</span></span>
    
- <span data-ttu-id="ee0e5-162">-Country „\<Ländername>“</span><span class="sxs-lookup"><span data-stu-id="ee0e5-162">-Country "\<country name>"</span></span>
    
- <span data-ttu-id="ee0e5-163">-Department „\<Abteilungsname>“</span><span class="sxs-lookup"><span data-stu-id="ee0e5-163">-Department "\<department name>"</span></span>
    
- <span data-ttu-id="ee0e5-164">-DisplayName „\<Vollständiger Benutzername>“</span><span class="sxs-lookup"><span data-stu-id="ee0e5-164">-DisplayName "\<full user name>"</span></span>
    
- <span data-ttu-id="ee0e5-165">-Fax „\<Faxnummer>“</span><span class="sxs-lookup"><span data-stu-id="ee0e5-165">-Fax "\<fax number>"</span></span>
    
- <span data-ttu-id="ee0e5-166">-FirstName „\<Vorname des Benutzers>“</span><span class="sxs-lookup"><span data-stu-id="ee0e5-166">-FirstName "\<user first name>"</span></span>
    
- <span data-ttu-id="ee0e5-167">-LastName „\<Nachname des Benutzers>“</span><span class="sxs-lookup"><span data-stu-id="ee0e5-167">-LastName "\<user last name>"</span></span>
    
- <span data-ttu-id="ee0e5-168">-MobilePhone „\<Mobiltelefonnummer>“</span><span class="sxs-lookup"><span data-stu-id="ee0e5-168">-MobilePhone "\<mobile phone number>"</span></span>
    
- <span data-ttu-id="ee0e5-169">-Office „\<Standort des Büros>“</span><span class="sxs-lookup"><span data-stu-id="ee0e5-169">-Office "\<office location>"</span></span>
    
- <span data-ttu-id="ee0e5-170">-PhoneNumber „\<Telefon Büro>“</span><span class="sxs-lookup"><span data-stu-id="ee0e5-170">-PhoneNumber "\<office phone number>"</span></span>
    
- <span data-ttu-id="ee0e5-171">-PostalCode „\<Postleitzahl>“</span><span class="sxs-lookup"><span data-stu-id="ee0e5-171">-PostalCode "\<postal code>"</span></span>
    
- <span data-ttu-id="ee0e5-172">-PreferredLanguage „\<Sprache>“</span><span class="sxs-lookup"><span data-stu-id="ee0e5-172">-PreferredLanguage "\<language>"</span></span>
    
- <span data-ttu-id="ee0e5-173">-State „\<Bundesland/Kanton>“</span><span class="sxs-lookup"><span data-stu-id="ee0e5-173">-State "\<state name>"</span></span>
    
- <span data-ttu-id="ee0e5-174">-StreetAddress „\<Adresse>“</span><span class="sxs-lookup"><span data-stu-id="ee0e5-174">-StreetAddress "\<street address>"</span></span>
    
- <span data-ttu-id="ee0e5-175">-Title „\<Titel>“</span><span class="sxs-lookup"><span data-stu-id="ee0e5-175">-Title "\<title name>"</span></span>
    
- <span data-ttu-id="ee0e5-176">-UsageLocation „\<Zweistelliger Länder- oder Regionalcode>“</span><span class="sxs-lookup"><span data-stu-id="ee0e5-176">-UsageLocation "\<2-character country or region code>"</span></span>
    
    <span data-ttu-id="ee0e5-177">Dies ist der zweistellige ISO 3166-1-Ländercode bzw. Regionscode (Alpha-2, A2).</span><span class="sxs-lookup"><span data-stu-id="ee0e5-177">This is the ISO 3166-1 alpha-2 (A2) two-letter country or region code.</span></span>
    
<span data-ttu-id="ee0e5-178">Informationen zu weiteren Parametern finden Sie unter [Set-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194136(v=azure.100)).</span><span class="sxs-lookup"><span data-stu-id="ee0e5-178">See [Set-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194136(v=azure.100)) for additional parameters.</span></span>

<span data-ttu-id="ee0e5-179">Führen Sie den folgenden Befehl aus, um die Benutzerprinzipalnamen aller Benutzer anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="ee0e5-179">To see the User Principal Names of all your users, run the following command.</span></span>
  
```powershell
Get-MSolUser | Sort UserPrincipalName | Select UserPrincipalName | More
```

<span data-ttu-id="ee0e5-180">Dieser Befehl weist Office 365 PowerShell zu folgenden Aktionen an:</span><span class="sxs-lookup"><span data-stu-id="ee0e5-180">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="ee0e5-181">Alle Informationen der Benutzerkonten abrufen (**Get-MsolUser**) und an den nächsten Befehl senden (**|**).</span><span class="sxs-lookup"><span data-stu-id="ee0e5-181">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="ee0e5-182">Sortieren Sie die Liste der Benutzerprinzipalnamen in alphabetischer Reihenfolge ( **Sort userPrincipalName** ), und senden Sie **|** Sie an den nächsten Befehl ().</span><span class="sxs-lookup"><span data-stu-id="ee0e5-182">Sort the list of User Principal Names alphabetically ( **Sort UserPrincipalName** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="ee0e5-183">Zeigt nur die Benutzerprinzipalnamen-Eigenschaft für jedes Konto an ( **Wählen Sie userPrincipalName** ) aus.</span><span class="sxs-lookup"><span data-stu-id="ee0e5-183">Display just the User Principal Name property for each account ( **Select UserPrincipalName** ).</span></span>
    
- <span data-ttu-id="ee0e5-184">Jeweils auf einem Bildschirm anzeigen ( **More** ).</span><span class="sxs-lookup"><span data-stu-id="ee0e5-184">Display them one screen at a time ( **More** ).</span></span>
    
<span data-ttu-id="ee0e5-p108">Mit diesem Befehl werden alle Ihre Konten aufgelistet. Wenn der Benutzerprinzipalname für ein Konto basierend auf dem Anzeigenamen (Vor- und Nachname) angezeigt werden soll, geben Sie die **$userName**-Variable unten ein (entfernen Sie die Zeichen „\<" und „>"), und führen Sie die folgenden Befehle aus:</span><span class="sxs-lookup"><span data-stu-id="ee0e5-p108">This command will list all of your accounts. If you want to display the User Principal Name for an account based on its display name (first and last name), fill in the **$userName** variable below (removing the \< and > characters), and then run the following commands:</span></span>
  
```powershell
$userName="<Display name>"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="ee0e5-187">In diesem Beispiel wird der Benutzerprinzipalname für den Benutzer namens Caleb Sills angezeigt.</span><span class="sxs-lookup"><span data-stu-id="ee0e5-187">This example displays the User Principal Name for the user named Caleb Sills.</span></span>
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="ee0e5-p109">Mit der **$upn** -Variable können Sie Änderungen an den einzelnen Konten basierend auf deren Anzeigenamen vornehmen. Hier ist ein Beispiel für das Festlegen des Verwendungsstandorts von Belinda Newman in Frankreich. Dabei wird Ihr Anzeigenamen anstatt Ihres Benutzerprinzipalnamens verwendet:</span><span class="sxs-lookup"><span data-stu-id="ee0e5-p109">By using a **$upn** variable, you can make changes to individual accounts based on their display name. Here is an example of setting Belinda Newman's usage location to France, but specifying her display name rather than her User Principal Name:</span></span>
  
```powershell
$userName="<display name>"
$upn=(Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-MsolUser -UserPrincipalName $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a><span data-ttu-id="ee0e5-190">Ändern von Eigenschaften für alle Benutzerkonten</span><span class="sxs-lookup"><span data-stu-id="ee0e5-190">Change properties for all user accounts</span></span>

<span data-ttu-id="ee0e5-p110">Um die Eigenschaften für alle Benutzer zu ändern, können Sie eine Kombination der Cmdlets **Get-MsolUser** und **Set-MsolUser** verwenden. Im folgende Beispiel wird der Verwendungsstandort für alle Benutzer in Frankreich geändert:</span><span class="sxs-lookup"><span data-stu-id="ee0e5-p110">To change properties for all users, you can use the combination of the **Get-MsolUser** and **Set-MsolUser** cmdlets. The following example changes the usage location for all users to France:</span></span>
  
```powershell
Get-MsolUser | Set-MsolUser -UsageLocation "FR"
```

<span data-ttu-id="ee0e5-193">Dieser Befehl weist Office 365 PowerShell zu folgenden Aktionen an:</span><span class="sxs-lookup"><span data-stu-id="ee0e5-193">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="ee0e5-194">Alle Informationen der Benutzerkonten abrufen (**Get-MsolUser**) und an den nächsten Befehl senden (**|**).</span><span class="sxs-lookup"><span data-stu-id="ee0e5-194">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="ee0e5-195">Benutzerstandort auf „Frankreich" festlegen ( **Set-MsolUser -UsageLocation "FR"** ).</span><span class="sxs-lookup"><span data-stu-id="ee0e5-195">Set the user location to France ( **Set-MsolUser -UsageLocation "FR"** ).</span></span>
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a><span data-ttu-id="ee0e5-196">Ändern von Eigenschaften für bestimmte Benutzerkonten</span><span class="sxs-lookup"><span data-stu-id="ee0e5-196">Change properties for a specific set of user accounts</span></span>

<span data-ttu-id="ee0e5-197">Zum Ändern der Eigenschaften für eine bestimmte Gruppe von Benutzerkonten können Sie die Kombination aus den Cmdlets **Get-MsolUser**, **Where**und **setMsolUser** verwenden.</span><span class="sxs-lookup"><span data-stu-id="ee0e5-197">To change properties for a specific set of user account, you can use the combination of the **Get-MsolUser**, **Where**, and **Set-MsolUser** cmdlets.</span></span> <span data-ttu-id="ee0e5-198">Im folgende Beispiel wird der Verwendungsstandort für alle Benutzer in der Buchhaltungsabteilung in Frankreich geändert:</span><span class="sxs-lookup"><span data-stu-id="ee0e5-198">The following example changes the usage location for all the users in the Accounting department to France:</span></span>
  
```powershell
Get-MsolUser | Where {$_.Department -eq "Accounting"} | Set-MsolUser -UsageLocation "FR"
```

<span data-ttu-id="ee0e5-199">Dieser Befehl weist Office 365 PowerShell zu folgenden Aktionen an:</span><span class="sxs-lookup"><span data-stu-id="ee0e5-199">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="ee0e5-200">Alle Informationen der Benutzerkonten abrufen (**Get-MsolUser**) und an den nächsten Befehl senden (**|**).</span><span class="sxs-lookup"><span data-stu-id="ee0e5-200">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="ee0e5-201">Alle Benutzerkonten suchen, bei denen für die Eigenschaft „Abteilung" der Wert „Buchhaltung" festgelegt ist ( **Where{$_.Department -eq "Accounting"}** ) und die resultierenden Informationen an den nächsten Befehl senden (  **|**).</span><span class="sxs-lookup"><span data-stu-id="ee0e5-201">Find all of the user accounts that have their Department property set to "Accounting" ( **Where {$_.Department -eq "Accounting"}** ) and send the resulting information to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="ee0e5-202">Benutzerstandort auf „Frankreich" festlegen ( **Set-MsolUser -UsageLocation "FR"** ).</span><span class="sxs-lookup"><span data-stu-id="ee0e5-202">Set the user location to France ( **Set-MsolUser -UsageLocation "FR"** ).</span></span>
    

## <a name="see-also"></a><span data-ttu-id="ee0e5-203">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="ee0e5-203">See also</span></span>

[<span data-ttu-id="ee0e5-204">Verwalten von Benutzerkonten, Lizenzen und Gruppen mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="ee0e5-204">Manage user accounts, licenses, and groups with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="ee0e5-205">Verwalten von Office 365 mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="ee0e5-205">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="ee0e5-206">Erste Schritte mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="ee0e5-206">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
