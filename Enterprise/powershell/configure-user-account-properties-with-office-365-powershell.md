---
title: Konfigurieren von Eigenschaften eines Benutzerkontos mit Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/03/2019
ms.audience: Admin
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
ms.openlocfilehash: 4db63482fdcc1d6cb186e663fd55c13186b33813
ms.sourcegitcommit: 15db0f1e5f8036e46063662d7df22387906f8ba7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/04/2019
ms.locfileid: "27546486"
---
# <a name="configure-user-account-properties-with-office-365-powershell"></a><span data-ttu-id="03ef6-103">Konfigurieren von Eigenschaften eines Benutzerkontos mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="03ef6-103">Configure user account properties with Office 365 PowerShell</span></span>

 <span data-ttu-id="03ef6-104">**Zusammenfassung:** Informationen zum Verwenden von Office 365 PowerShell zum Konfigurieren der Eigenschaften für einzelne oder mehrere Benutzerkonten in Ihrem Office 365-Mandanten.</span><span class="sxs-lookup"><span data-stu-id="03ef6-104">**Summary:** Use Office 365 PowerShell to configure properties of individual or multiple user accounts in your Office 365 tenant.</span></span>
  
<span data-ttu-id="03ef6-105">Zwar können Sie das Office 365 Admin Center zum Konfigurieren der Eigenschaften für die Benutzerkonten Ihres Office 365-Mandanten verwenden, mit Office 365 PowerShell können Sie jedoch zusätzlich weitere Aktionen durchführen, die mit dem Office 365 Admin Center nicht möglich sind.</span><span class="sxs-lookup"><span data-stu-id="03ef6-105">Although you can use the Office 365 Admin center to configure properties for the user accounts of your Office 365 tenant, you can also use Office 365 PowerShell and do some things that the Office 365 Admin center cannot.</span></span>
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="03ef6-106">Verwenden der Azure Active Directory PowerShell für Graph-Module</span><span class="sxs-lookup"><span data-stu-id="03ef6-106">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="03ef6-107">Verwenden Sie zum Konfigurieren von Eigenschaften für Benutzerkonten mit der Azure Active Directory PowerShell das [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0)-Cmdlet und geben Sie die Eigenschaften an, die Sie festlegen bzw. ändern möchten.</span><span class="sxs-lookup"><span data-stu-id="03ef6-107">To configure properties for user accounts with the Azure Active Directory V2 PowerShell module, you use the [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) cmdlet and specify the properties to set or change. But first, you must connect to your subscription. For the instructions, seeConnect with the Azure Active Directory V2 PowerShell module.</span></span> 

<span data-ttu-id="03ef6-108">Verbinden Sie sich zuerst [mit Ihrem Office 365-Mandanten](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="03ef6-108">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
   
### <a name="change-properties-for-a-specific-user-account"></a><span data-ttu-id="03ef6-109">Ändern von Eigenschaften für ein bestimmtes Benutzerkonto</span><span class="sxs-lookup"><span data-stu-id="03ef6-109">Change properties for a specific user account</span></span>

<span data-ttu-id="03ef6-p101">Sie identifizieren das Konto mit dem **-ObjectID**-Parameter und legen bestimmte Eigenschaften mit weiteren Parametern fest bzw. ändern diese. Nachfolgend ist eine Liste der am häufigsten verwendeten Parameter aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="03ef6-p101">You identify the account with the **-ObjectID** parameter and set or change specific properties with additional parameters. Here is a list of the most common parameters.</span></span>
  
- <span data-ttu-id="03ef6-112">-Department „\<Abteilungsname>“</span><span class="sxs-lookup"><span data-stu-id="03ef6-112">-Department "\<department name>"</span></span>
    
- <span data-ttu-id="03ef6-113">-DisplayName „\<Vollständiger Benutzername>“</span><span class="sxs-lookup"><span data-stu-id="03ef6-113">-DisplayName "\<full user name>"</span></span>
    
- <span data-ttu-id="03ef6-114">-FacsimilieTelephoneNumber „\<Faxnummer>“</span><span class="sxs-lookup"><span data-stu-id="03ef6-114">-FacsimilieTelephoneNumber "\<fax number>"</span></span>
    
- <span data-ttu-id="03ef6-115">-GivenName „\<Vorname des Benutzers>“</span><span class="sxs-lookup"><span data-stu-id="03ef6-115">-GivenName "\<user first name>"</span></span>
    
- <span data-ttu-id="03ef6-116">-Surname „\<Nachname des Benutzers>“</span><span class="sxs-lookup"><span data-stu-id="03ef6-116">-Surname "\<user last name>"</span></span>
    
- <span data-ttu-id="03ef6-117">-Mobile „\<Mobiltelefonnummer>“</span><span class="sxs-lookup"><span data-stu-id="03ef6-117">-Mobile "\<mobile phone number>"</span></span>
    
- <span data-ttu-id="03ef6-118">-JobTitle „\<Position>“</span><span class="sxs-lookup"><span data-stu-id="03ef6-118">-JobTitle "\<job title>"</span></span>
    
- <span data-ttu-id="03ef6-119">-PreferredLanguage „\<Sprache>“</span><span class="sxs-lookup"><span data-stu-id="03ef6-119">-PreferredLanguage "\<language>"</span></span>
    
- <span data-ttu-id="03ef6-120">-StreetAddress „\<Adresse>“</span><span class="sxs-lookup"><span data-stu-id="03ef6-120">-StreetAddress "\<street address>"</span></span>
    
- <span data-ttu-id="03ef6-121">-City „\<Ortsname>“</span><span class="sxs-lookup"><span data-stu-id="03ef6-121">-City "\<city name>"</span></span>
    
- <span data-ttu-id="03ef6-122">-State „\<Bundesland/Kanton>“</span><span class="sxs-lookup"><span data-stu-id="03ef6-122">-State "\<state name>"</span></span>
    
- <span data-ttu-id="03ef6-123">-PostalCode „\<Postleitzahl>“</span><span class="sxs-lookup"><span data-stu-id="03ef6-123">-PostalCode "\<postal code>"</span></span>
    
- <span data-ttu-id="03ef6-124">-Country „\<Ländername>“</span><span class="sxs-lookup"><span data-stu-id="03ef6-124">-Country "\<country name>"</span></span>
    
- <span data-ttu-id="03ef6-125">-TelephoneNumber „\<Telefon Büro>“</span><span class="sxs-lookup"><span data-stu-id="03ef6-125">-TelephoneNumber "\<office phone number>"</span></span>
    
- <span data-ttu-id="03ef6-126">-UsageLocation „\<Zweistelliger Länder- oder Regionalcode>“</span><span class="sxs-lookup"><span data-stu-id="03ef6-126">-UsageLocation "\<2-character country or region code>"</span></span>
    
    <span data-ttu-id="03ef6-127">Dies ist der zweistellige ISO 3166-1-Ländercode bzw. Regionscode (Alpha-2, A2).</span><span class="sxs-lookup"><span data-stu-id="03ef6-127">This is the ISO 3166-1 alpha-2 (A2) two-letter country or region code.</span></span>
    
<span data-ttu-id="03ef6-128">Informationen zu weiteren Parametern finden Sie unter [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0).</span><span class="sxs-lookup"><span data-stu-id="03ef6-128">See [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) for additional parameters.</span></span>
  
<span data-ttu-id="03ef6-129">Führen Sie den folgenden Befehl aus, um den Benutzerprinzipalnamen für Ihre Benutzerkonten anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="03ef6-129">To display the User Principal Name for your user accounts, run the following command.</span></span>
  
```
Get-AzureADUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

<span data-ttu-id="03ef6-130">Dieser Befehl weist Office 365 PowerShell zu folgenden Aktionen an:</span><span class="sxs-lookup"><span data-stu-id="03ef6-130">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="03ef6-131">Alle Informationen der Benutzerkonten abrufen (**Get-AzureADUser**) und an den nächsten Befehl senden (**|**).</span><span class="sxs-lookup"><span data-stu-id="03ef6-131">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="03ef6-132">Liste der Benutzerprinzipalnamen alphabetisch sortieren (**Sort-Object UserPrincipalName**) und an den nächsten Befehl senden (**|**).</span><span class="sxs-lookup"><span data-stu-id="03ef6-132">Sort the list of User Principal Names alphabetically ( **Sort-Object UserPrincipalName** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="03ef6-133">Nur die UserPrincipalName-Eigenschaft für jedes Konto anzeigen ( **Select-Object UserPrincipalName** ).</span><span class="sxs-lookup"><span data-stu-id="03ef6-133">Display just the User Principal Name property for each account ( **Select-Object UserPrincipalName** ).</span></span>
- <span data-ttu-id="03ef6-134">Jeweils auf einem Bildschirm anzeigen ( **More** ).</span><span class="sxs-lookup"><span data-stu-id="03ef6-134">Display them one screen at a time ( **More** ).</span></span>
    
<span data-ttu-id="03ef6-p102">Mit diesem Befehl werden alle Ihre Konten aufgelistet. Wenn der Benutzerprinzipalname für ein Konto basierend auf dem Anzeigenamen (Vor- und Nachname) angezeigt werden soll, geben Sie die **$userName**-Variable unten ein (entfernen Sie die Zeichen „\<“ und „>“), und führen Sie die folgenden Befehle aus:</span><span class="sxs-lookup"><span data-stu-id="03ef6-p102">This command will list all of your accounts. If you want to display the User Principal Name for an account based on its display name (first and last name), fill in the **$userName** variable below (removing the \< and > characters), and then run the following commands:</span></span>
  
```
$userName="<Display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="03ef6-137">In diesem Beispiel wird der Benutzerprinzipalname für das Benutzerkonto mit dem Anzeigename Caleb Sills angezeigt.</span><span class="sxs-lookup"><span data-stu-id="03ef6-137">This example displays the User Principal Name for the user account with the display name of Caleb Sills.</span></span>
  
```
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="03ef6-p103">Mit der **$upn**-Variable können Sie Änderungen an den einzelnen Konten basierend auf deren Anzeigenamen vornehmen. Hier ist ein Beispiel für das Festlegen des Verwendungsstandorts von Belinda Newman in Frankreich. Dabei wird Ihr Anzeigenamen anstatt Ihres Benutzerprinzipalnamens verwendet:</span><span class="sxs-lookup"><span data-stu-id="03ef6-p103">By using a **$upn** variable, you can make changes to individual accounts based on their display name. Here is an example of setting Belinda Newman's usage location to France, but specifying her display name rather than her User Principal Name:</span></span>
  
```
$userName="Belinda Newman"
$upn=(Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-AzureADUser -ObjectID $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a><span data-ttu-id="03ef6-140">Ändern von Eigenschaften für alle Benutzerkonten</span><span class="sxs-lookup"><span data-stu-id="03ef6-140">Change properties for all user accounts</span></span>

<span data-ttu-id="03ef6-p104">Um die Eigenschaften für alle Benutzer zu ändern, können Sie eine Kombination der Cmdlets **Get-AzureADUser** und **et-AzureADUser** verwenden. Im folgende Beispiel wird der Verwendungsstandort für alle Benutzer in Frankreich geändert:</span><span class="sxs-lookup"><span data-stu-id="03ef6-p104">To change properties for all users, you can use the combination of the **Get-AzureADUser** and **Set-AzureADUser** cmdlets. The following example changes the usage location for all users to France:</span></span>
  
```
Get-AzureADUser | Set-AzureADUser -UsageLocation "FR"
```

<span data-ttu-id="03ef6-143">Dieser Befehl gibt Office 365 Powershell die folgenden Anweisungen:</span><span class="sxs-lookup"><span data-stu-id="03ef6-143">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="03ef6-144">Alle Informationen der Benutzerkonten abrufen (**Get-AzureADUser**) und an den nächsten Befehl senden (**|**).</span><span class="sxs-lookup"><span data-stu-id="03ef6-144">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="03ef6-145">Benutzerstandort auf „Frankreich“ festlegen (**Set-AzureADUser –UsageLocation "FR"**).</span><span class="sxs-lookup"><span data-stu-id="03ef6-145">Set the user location to France ( **Set-AzureADUser -UsageLocation "FR"** ).</span></span>
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a><span data-ttu-id="03ef6-146">Ändern von Eigenschaften für bestimmte Benutzerkonten</span><span class="sxs-lookup"><span data-stu-id="03ef6-146">Change properties for a specific set of user accounts</span></span>

<span data-ttu-id="03ef6-p105">Um die Eigenschaften für einen bestimmten Satz von Benutzerkonten zu ändern, können Sie eine Kombination der Cmdlets **Get-AzureADUser**, **Where** und **Set-AzureADUser** verwenden. Im folgende Beispiel wird der Verwendungsstandort für alle Benutzer in der Buchhaltungsabteilung in Frankreich geändert:</span><span class="sxs-lookup"><span data-stu-id="03ef6-p105">To change properties for a specific set of user account, you can use the combination of the **Get-AzureADUser**, **Where**, and **Set-AzureADUser** cmdlets. The following example changes the usage location for all the users in the Accounting department to France:</span></span>
  
```
Get-AzureADUser | Where-Object {$_.Department -eq "Accounting"} | Set-AzureADUser -UsageLocation "FR"
```

<span data-ttu-id="03ef6-149">Dieser Befehl gibt Office 365 Powershell die folgenden Anweisungen:</span><span class="sxs-lookup"><span data-stu-id="03ef6-149">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="03ef6-150">Alle Informationen der Benutzerkonten abrufen (**Get-AzureADUser**) und an den nächsten Befehl senden (**|**).</span><span class="sxs-lookup"><span data-stu-id="03ef6-150">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="03ef6-151">Alle Benutzerkonten suchen, bei denen für die Eigenschaft „Abteilung" der Wert „Buchhaltung" festgelegt ist ( **Where{$_.Department -eq "Accounting"}** ) und die resultierenden Informationen an den nächsten Befehl senden (  **|**).</span><span class="sxs-lookup"><span data-stu-id="03ef6-151">Find all of the user accounts that have their Department property set to "Accounting" ( **Where {$_.Department -eq "Accounting"}** ) and send the resulting information to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="03ef6-152">Benutzerstandort auf „Frankreich“ festlegen (**Set-AzureADUser –UsageLocation "FR"**).</span><span class="sxs-lookup"><span data-stu-id="03ef6-152">Set the user location to France ( **Set-AzureADUser -UsageLocation "FR"** ).</span></span>
    
## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="03ef6-153">Verwenden des Microsoft Azure Active Directory-Moduls für Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="03ef6-153">Open the Microsoft Azure Active Directory Module for Windows PowerShell.</span></span>

<span data-ttu-id="03ef6-154">Verwenden Sie zum Konfigurieren von Eigenschaften für Benutzerkonten mit dem Azure Active Directory-Modul für Windows PowerShell das Set-MsolUser-Cmdlet und geben Sie die Eigenschaften an, die Sie festlegen bzw. ändern möchten.</span><span class="sxs-lookup"><span data-stu-id="03ef6-154">To configure properties for user accounts with the Microsoft Azure Active Directory Module for Windows PowerShell, you use the Set-MsolUser cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="03ef6-155">Verbinden Sie sich zuerst [mit Ihrem Office 365-Mandanten](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="03ef6-155">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>
  
### <a name="change-properties-for-a-specific-user-account"></a><span data-ttu-id="03ef6-156">Ändern von Eigenschaften für ein bestimmtes Benutzerkonto</span><span class="sxs-lookup"><span data-stu-id="03ef6-156">Change properties for a specific user account</span></span>

<span data-ttu-id="03ef6-157">Verwenden Sie zum Konfigurieren der Eigenschaften für ein bestimmtes Benutzerkonto das [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx)-Cmdlet und geben die Eigenschaften an, die festgelegt oder geändert werden sollen.</span><span class="sxs-lookup"><span data-stu-id="03ef6-157">To configure properties for a specific user account, you use the [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) cmdlet and specify the properties to set or change. This example command changes Belinda Newman's usage location to France:</span></span> 

<span data-ttu-id="03ef6-p106">Sie identifizieren das Konto mit dem **-UserPrincipalName**-Parameter und legen bestimmte Eigenschaften mit weiteren Parametern fest bzw. ändern diese. Nachfolgend ist eine Liste der am häufigsten verwendeten Parameter aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="03ef6-p106">You identify the account with the **-UserPrincipalName** parameter and set or change specific properties with additional parameters. Here is a list of the most common parameters.</span></span>
  
- <span data-ttu-id="03ef6-160">-City „\<Ortsname>“</span><span class="sxs-lookup"><span data-stu-id="03ef6-160">-City "\<city name>"</span></span>
    
- <span data-ttu-id="03ef6-161">-Country „\<Ländername>“</span><span class="sxs-lookup"><span data-stu-id="03ef6-161">-Country "\<country name>"</span></span>
    
- <span data-ttu-id="03ef6-162">-Department „\<Abteilungsname>“</span><span class="sxs-lookup"><span data-stu-id="03ef6-162">-Department "\<department name>"</span></span>
    
- <span data-ttu-id="03ef6-163">-DisplayName „\<Vollständiger Benutzername>“</span><span class="sxs-lookup"><span data-stu-id="03ef6-163">-DisplayName "\<full user name>"</span></span>
    
- <span data-ttu-id="03ef6-164">-Fax „\<Faxnummer>“</span><span class="sxs-lookup"><span data-stu-id="03ef6-164">-Fax "\<fax number>"</span></span>
    
- <span data-ttu-id="03ef6-165">-FirstName „\<Vorname des Benutzers>“</span><span class="sxs-lookup"><span data-stu-id="03ef6-165">-FirstName "\<user first name>"</span></span>
    
- <span data-ttu-id="03ef6-166">-LastName „\<Nachname des Benutzers>“</span><span class="sxs-lookup"><span data-stu-id="03ef6-166">-LastName "\<user last name>"</span></span>
    
- <span data-ttu-id="03ef6-167">-MobilePhone „\<Mobiltelefonnummer>“</span><span class="sxs-lookup"><span data-stu-id="03ef6-167">-MobilePhone "\<mobile phone number>"</span></span>
    
- <span data-ttu-id="03ef6-168">-Office „\<Standort des Büros>“</span><span class="sxs-lookup"><span data-stu-id="03ef6-168">-Office "\<office location>"</span></span>
    
- <span data-ttu-id="03ef6-169">-PhoneNumber „\<Telefon Büro>“</span><span class="sxs-lookup"><span data-stu-id="03ef6-169">-PhoneNumber "\<office phone number>"</span></span>
    
- <span data-ttu-id="03ef6-170">-PostalCode „\<Postleitzahl>“</span><span class="sxs-lookup"><span data-stu-id="03ef6-170">-PostalCode "\<postal code>"</span></span>
    
- <span data-ttu-id="03ef6-171">-PreferredLanguage „\<Sprache>“</span><span class="sxs-lookup"><span data-stu-id="03ef6-171">-PreferredLanguage "\<language>"</span></span>
    
- <span data-ttu-id="03ef6-172">-State „\<Bundesland/Kanton>“</span><span class="sxs-lookup"><span data-stu-id="03ef6-172">-State "\<state name>"</span></span>
    
- <span data-ttu-id="03ef6-173">-StreetAddress „\<Adresse>“</span><span class="sxs-lookup"><span data-stu-id="03ef6-173">-StreetAddress "\<street address>"</span></span>
    
- <span data-ttu-id="03ef6-174">-Title „\<Titel>“</span><span class="sxs-lookup"><span data-stu-id="03ef6-174">-Title "\<title name>"</span></span>
    
- <span data-ttu-id="03ef6-175">-UsageLocation „\<Zweistelliger Länder- oder Regionalcode>“</span><span class="sxs-lookup"><span data-stu-id="03ef6-175">-UsageLocation "\<2-character country or region code>"</span></span>
    
    <span data-ttu-id="03ef6-176">Dies ist der zweistellige ISO 3166-1-Ländercode bzw. Regionscode (Alpha-2, A2).</span><span class="sxs-lookup"><span data-stu-id="03ef6-176">This is the ISO 3166-1 alpha-2 (A2) two-letter country or region code.</span></span>
    
<span data-ttu-id="03ef6-177">Informationen zu weiteren Parametern finden Sie unter [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx).</span><span class="sxs-lookup"><span data-stu-id="03ef6-177">See [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) for additional parameters.</span></span>
  
<span data-ttu-id="03ef6-178">Führen Sie den folgenden Befehl aus, um die Benutzerprinzipalnamen aller Benutzer anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="03ef6-178">To see the User Principal Names of all your users, run the following command.</span></span>
  
```
Get-MSolUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

<span data-ttu-id="03ef6-179">Dieser Befehl weist Office 365 PowerShell zu folgenden Aktionen an:</span><span class="sxs-lookup"><span data-stu-id="03ef6-179">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="03ef6-180">Alle Informationen der Benutzerkonten abrufen (**Get-MsolUser**) und an den nächsten Befehl senden (**|**).</span><span class="sxs-lookup"><span data-stu-id="03ef6-180">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="03ef6-181">Liste der Benutzerprinzipalnamen alphabetisch sortieren (**Sort-Object UserPrincipalName**) und an den nächsten Befehl senden (**|**).</span><span class="sxs-lookup"><span data-stu-id="03ef6-181">Sort the list of User Principal Names alphabetically ( **Sort-Object UserPrincipalName** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="03ef6-182">Nur die UserPrincipalName-Eigenschaft für jedes Konto anzeigen ( **Select-Object UserPrincipalName** ).</span><span class="sxs-lookup"><span data-stu-id="03ef6-182">Display just the User Principal Name property for each account ( **Select-Object UserPrincipalName** ).</span></span>
    
- <span data-ttu-id="03ef6-183">Jeweils auf einem Bildschirm anzeigen ( **More** ).</span><span class="sxs-lookup"><span data-stu-id="03ef6-183">Display them one screen at a time ( **More** ).</span></span>
    
<span data-ttu-id="03ef6-p107">Mit diesem Befehl werden alle Ihre Konten aufgelistet. Wenn der Benutzerprinzipalname für ein Konto basierend auf dem Anzeigenamen (Vor- und Nachname) angezeigt werden soll, geben Sie die **$userName**-Variable unten ein (entfernen Sie die Zeichen „\<" und „>"), und führen Sie die folgenden Befehle aus:</span><span class="sxs-lookup"><span data-stu-id="03ef6-p107">This command will list all of your accounts. If you want to display the User Principal Name for an account based on its display name (first and last name), fill in the **$userName** variable below (removing the \< and > characters), and then run the following commands:</span></span>
  
```
$userName="<Display name>"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="03ef6-186">In diesem Beispiel wird der Benutzerprinzipalname für den Benutzer namens Caleb Sills angezeigt.</span><span class="sxs-lookup"><span data-stu-id="03ef6-186">This example displays the User Principal Name for the user named Caleb Sills.</span></span>
  
```
$userName="Caleb Sills"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="03ef6-p108">Mit der **$upn** -Variable können Sie Änderungen an den einzelnen Konten basierend auf deren Anzeigenamen vornehmen. Hier ist ein Beispiel für das Festlegen des Verwendungsstandorts von Belinda Newman in Frankreich. Dabei wird Ihr Anzeigenamen anstatt Ihres Benutzerprinzipalnamens verwendet:</span><span class="sxs-lookup"><span data-stu-id="03ef6-p108">By using a **$upn** variable, you can make changes to individual accounts based on their display name. Here is an example of setting Belinda Newman's usage location to France, but specifying her display name rather than her User Principal Name:</span></span>
  
```
$userName="<display name>"
$upn=(Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-MsolUser -UserPrincipalName $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a><span data-ttu-id="03ef6-189">Ändern von Eigenschaften für alle Benutzerkonten</span><span class="sxs-lookup"><span data-stu-id="03ef6-189">Change properties for all user accounts</span></span>

<span data-ttu-id="03ef6-p109">Um die Eigenschaften für alle Benutzer zu ändern, können Sie eine Kombination der Cmdlets **Get-MsolUser** und **Set-MsolUser** verwenden. Im folgende Beispiel wird der Verwendungsstandort für alle Benutzer in Frankreich geändert:</span><span class="sxs-lookup"><span data-stu-id="03ef6-p109">To change properties for all users, you can use the combination of the **Get-MsolUser** and **Set-MsolUser** cmdlets. The following example changes the usage location for all users to France:</span></span>
  
```
Get-MsolUser | Set-MsolUser -UsageLocation "FR"
```

<span data-ttu-id="03ef6-192">Dieser Befehl weist Office 365 PowerShell zu folgenden Aktionen an:</span><span class="sxs-lookup"><span data-stu-id="03ef6-192">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="03ef6-193">Alle Informationen der Benutzerkonten abrufen (**Get-MsolUser**) und an den nächsten Befehl senden (**|**).</span><span class="sxs-lookup"><span data-stu-id="03ef6-193">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="03ef6-194">Benutzerstandort auf „Frankreich" festlegen ( **Set-MsolUser -UsageLocation "FR"** ).</span><span class="sxs-lookup"><span data-stu-id="03ef6-194">Set the user location to France ( **Set-MsolUser -UsageLocation "FR"** ).</span></span>
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a><span data-ttu-id="03ef6-195">Ändern von Eigenschaften für bestimmte Benutzerkonten</span><span class="sxs-lookup"><span data-stu-id="03ef6-195">Change properties for a specific set of user accounts</span></span>

<span data-ttu-id="03ef6-p110">Um die Eigenschaften für einen bestimmten Satz von Benutzerkonten zu ändern, können Sie eine Kombination der Cmdlets **Get-MsolUser**, **Where-Object** und **Set-MsolUser** verwenden. Im folgende Beispiel wird der Verwendungsstandort für alle Benutzer in der Buchhaltungsabteilung in Frankreich geändert:</span><span class="sxs-lookup"><span data-stu-id="03ef6-p110">To change properties for a specific set of user account, you can use the combination of the **Get-MsolUser**, **Where-Object**, and **Set-MsolUser** cmdlets. The following example changes the usage location for all the users in the Accounting department to France:</span></span>
  
```
Get-MsolUser | Where-Object {$_.Department -eq "Accounting"} | Set-MsolUser -UsageLocation "FR"
```

<span data-ttu-id="03ef6-198">Dieser Befehl weist Office 365 PowerShell zu folgenden Aktionen an:</span><span class="sxs-lookup"><span data-stu-id="03ef6-198">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="03ef6-199">Alle Informationen der Benutzerkonten abrufen (**Get-MsolUser**) und an den nächsten Befehl senden (**|**).</span><span class="sxs-lookup"><span data-stu-id="03ef6-199">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="03ef6-200">Alle Benutzerkonten suchen, bei denen für die Eigenschaft „Abteilung" der Wert „Buchhaltung" festgelegt ist ( **Where-Object {$_.Department -eq "Accounting"}** ) und die resultierenden Informationen an den nächsten Befehl senden ( **|**).</span><span class="sxs-lookup"><span data-stu-id="03ef6-200">Find all of the user accounts that have their Department property set to "Accounting" ( **Where-Object {$_.Department -eq "Accounting"}** ) and send the resulting information to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="03ef6-201">Benutzerstandort auf „Frankreich" festlegen ( **Set-MsolUser -UsageLocation "FR"** ).</span><span class="sxs-lookup"><span data-stu-id="03ef6-201">Set the user location to France ( **Set-MsolUser -UsageLocation "FR"** ).</span></span>
    

## <a name="see-also"></a><span data-ttu-id="03ef6-202">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="03ef6-202">See also</span></span>

[<span data-ttu-id="03ef6-203">Verwalten von Benutzerkonten und Lizenzen mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="03ef6-203">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="03ef6-204">Verwalten von Office 365 mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="03ef6-204">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="03ef6-205">Erste Schritte mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="03ef6-205">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
