---
title: Konfigurieren von Eigenschaften eines Benutzerkontos mit Office 365 PowerShell
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
- DecEntMigration
- O365ITProTrain
- Ent_Office_Other
- PowerShell
- apr17entnews
ms.assetid: 30813f8d-b08d-444b-98c1-53df7c29b4d7
description: "Zusammenfassung: Informationen zum Verwenden von Office 365 PowerShell zum Konfigurieren der Eigenschaften für einzelne oder mehrere Benutzerkonten in Ihrem Office 365-Mandanten."
ms.openlocfilehash: d9e817530f3b1554cb757720f01afec5ed3b63ef
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2017
---
# <a name="configure-user-account-properties-with-office-365-powershell"></a><span data-ttu-id="b9469-103">Konfigurieren von Eigenschaften eines Benutzerkontos mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="b9469-103">Configure user account properties with Office 365 PowerShell</span></span>

 <span data-ttu-id="b9469-104">**Zusammenfassung:** Verwenden Sie Office 365 PowerShell zum Konfigurieren von Eigenschaften des einzelne oder mehrere Benutzerkonten in Ihrem Office 365-Mandanten.</span><span class="sxs-lookup"><span data-stu-id="b9469-104">**Summary:** Use Office 365 PowerShell to configure properties of individual or multiple user accounts in your Office 365 tenant.</span></span>
  
<span data-ttu-id="b9469-105">Zwar können Sie das Office 365 Admin Center zum Konfigurieren der Eigenschaften für die Benutzerkonten Ihres Office 365-Mandanten verwenden, mit Office 365 PowerShell können Sie jedoch zusätzlich weitere Aktionen durchführen, die mit dem Office 365 Admin Center nicht möglich sind.</span><span class="sxs-lookup"><span data-stu-id="b9469-105">Although you can use the Office 365 Admin center to configure properties for the user accounts of your Office 365 tenant, you can also use Office 365 PowerShell and do some things that the Office 365 Admin center cannot.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="b9469-106">Bevor Sie beginnen</span><span class="sxs-lookup"><span data-stu-id="b9469-106">Before you begin</span></span>

<span data-ttu-id="b9469-p101">Für die Verfahren in diesem Thema müssen Sie eine Verbindung mit Office 365 PowerShell herstellen. Weitere Anweisungen finden Sie unter [Verbinden mit Office 365 PowerShell](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="b9469-p101">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
  
## <a name="change-properties-for-a-specific-user-account"></a><span data-ttu-id="b9469-109">Ändern von Eigenschaften für ein bestimmtes Benutzerkonto</span><span class="sxs-lookup"><span data-stu-id="b9469-109">Change properties for a specific user account</span></span>

<span data-ttu-id="b9469-p102">Verwenden Sie zum Konfigurieren der Eigenschaften für ein bestimmtes das [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx)-Cmdlet, und geben die Eigenschaften an, die festgelegt oder geändert werden sollen. In diesem Beispiel ändert der Befehl den Verwendungsstandort von Belinda Newman in Frankreich:</span><span class="sxs-lookup"><span data-stu-id="b9469-p102">To configure properties for a specific user account, you use the [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) cmdlet and specify the properties to set or change. This example command changes Belinda Newman's usage location to France:</span></span>
  
```
Set-MsolUser -UserPrincipalName "BelindaN@litwareinc.onmicosoft.com" -UsageLocation "FR"
```

<span data-ttu-id="b9469-p103">Sie identifizieren das Konto mit dem **-UserPrincipalName** -Parameter und legen bestimmte Eigenschaften mit weiteren Parametern fest bzw. ändern diese. Nachfolgend ist eine Liste der am häufigsten verwendeten Parameter aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="b9469-p103">You identify the account with the **-UserPrincipalName** parameter and set or change specific properties with additional parameters. Here is a list of the most common parameters.</span></span>
  
- <span data-ttu-id="b9469-114">-Stadt "\<Ortsname >"</span><span class="sxs-lookup"><span data-stu-id="b9469-114">-City "\<city name>"</span></span>
    
- <span data-ttu-id="b9469-115">-Land "\<Land Name >"</span><span class="sxs-lookup"><span data-stu-id="b9469-115">-Country "\<country name>"</span></span>
    
- <span data-ttu-id="b9469-116">-Abteilung "\<Abteilungsnamen >"</span><span class="sxs-lookup"><span data-stu-id="b9469-116">-Department "\<department name>"</span></span>
    
- <span data-ttu-id="b9469-117">DisplayName-"\<vollständige Benutzername >"</span><span class="sxs-lookup"><span data-stu-id="b9469-117">-DisplayName "\<full user name>"</span></span>
    
- <span data-ttu-id="b9469-118">-Fax "\<Faxnummer >"</span><span class="sxs-lookup"><span data-stu-id="b9469-118">-Fax "\<fax number>"</span></span>
    
- <span data-ttu-id="b9469-119">-FirstName "\<Vorname Benutzer >"</span><span class="sxs-lookup"><span data-stu-id="b9469-119">-FirstName "\<user first name>"</span></span>
    
- <span data-ttu-id="b9469-120">LastName-"\<letzten Benutzername >"</span><span class="sxs-lookup"><span data-stu-id="b9469-120">-LastName "\<user last name>"</span></span>
    
- <span data-ttu-id="b9469-121">-MobilePhone "\<Mobiltelefonnummer >"</span><span class="sxs-lookup"><span data-stu-id="b9469-121">-MobilePhone "\<mobile phone number>"</span></span>
    
- <span data-ttu-id="b9469-122">-Office "\<Bürostandort >"</span><span class="sxs-lookup"><span data-stu-id="b9469-122">-Office "\<office location>"</span></span>
    
- <span data-ttu-id="b9469-123">PhoneNumber-"\<Office Rufnummer >"</span><span class="sxs-lookup"><span data-stu-id="b9469-123">-PhoneNumber "\<office phone number>"</span></span>
    
- <span data-ttu-id="b9469-124">PostalCode-"\<Postleitzahl >"</span><span class="sxs-lookup"><span data-stu-id="b9469-124">-PostalCode "\<postal code>"</span></span>
    
- <span data-ttu-id="b9469-125">-PreferredLanguage "\<Sprache >"</span><span class="sxs-lookup"><span data-stu-id="b9469-125">-PreferredLanguage "\<language>"</span></span>
    
- <span data-ttu-id="b9469-126">-Status "\<Zustand Name >"</span><span class="sxs-lookup"><span data-stu-id="b9469-126">-State "\<state name>"</span></span>
    
- <span data-ttu-id="b9469-127">StreetAddress-"\<Straße >"</span><span class="sxs-lookup"><span data-stu-id="b9469-127">-StreetAddress "\<street address>"</span></span>
    
- <span data-ttu-id="b9469-128">-Title "\<Titel Name >"</span><span class="sxs-lookup"><span data-stu-id="b9469-128">-Title "\<title name>"</span></span>
    
- <span data-ttu-id="b9469-129">-Usagelocation-Wert angegeben "\<2-Land oder Region Zeichencode >"</span><span class="sxs-lookup"><span data-stu-id="b9469-129">-UsageLocation "\<2-character country or region code>"</span></span>
    
    <span data-ttu-id="b9469-130">Dies ist der zweistellige ISO 3166-1-Ländercode bzw. Regionscode (Alpha-2, A2).</span><span class="sxs-lookup"><span data-stu-id="b9469-130">This is the ISO 3166-1 alpha-2 (A2) two-letter country or region code.</span></span>
    
<span data-ttu-id="b9469-131">Informationen zu weiteren Parametern finden Sie unter [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx).</span><span class="sxs-lookup"><span data-stu-id="b9469-131">See [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) for additional parameters.</span></span>
  
<span data-ttu-id="b9469-132">Führen Sie den folgenden Befehl aus, um die Benutzerprinzipalnamen aller Benutzer anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="b9469-132">To see the User Principal Names of all your users, run the following command.</span></span>
  
```
Get-MSolUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

<span data-ttu-id="b9469-133">Dieser Befehl weist Office 365 PowerShell zu folgenden Aktionen an:</span><span class="sxs-lookup"><span data-stu-id="b9469-133">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="b9469-134">Alle Informationen für die Benutzerkonten ( **Get-MsolUser** ) abrufen und senden Sie sie an den nächsten Befehl ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="b9469-134">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="b9469-135">Die Liste der User Principal Names alphabetisch sortieren ( **Sort-Objekt UserPrincipalName** ) und senden Sie sie an den nächsten Befehl ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="b9469-135">Sort the list of User Principal Names alphabetically ( **Sort-Object UserPrincipalName** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="b9469-136">Nur die UserPrincipalName-Eigenschaft für jedes Konto anzeigen ( **Select-Object UserPrincipalName** ).</span><span class="sxs-lookup"><span data-stu-id="b9469-136">Display just the User Principal Name property for each account ( **Select-Object UserPrincipalName** ).</span></span>
    
- <span data-ttu-id="b9469-137">Jeweils auf einem Bildschirm anzeigen ( **More** ).</span><span class="sxs-lookup"><span data-stu-id="b9469-137">Display them one screen at a time ( **More** ).</span></span>
    
<span data-ttu-id="b9469-p104">Mit diesem Befehl werden alle Konten aufgelistet. Wenn Sie die User Principal Name für ein Konto basierend auf deren Anzeige anzeigen möchten name (vor- und Nachname), füllen Sie die unten aufgeführten **$userName** -Variable (Entfernen der \< und > Zeichen), und führen Sie dann die folgenden Befehle aus:</span><span class="sxs-lookup"><span data-stu-id="b9469-p104">This command will list all of your accounts. If you want to display the User Principal Name for an account based on its display name (first and last name), fill in the **$userName** variable below (removing the \< and > characters), and then run the following commands:</span></span>
  
```
$userName="<Display name>"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="b9469-140">In diesem Beispiel wird der Benutzerprinzipalname für den Benutzer namens Caleb Sills angezeigt.</span><span class="sxs-lookup"><span data-stu-id="b9469-140">This example displays the User Principal Name for the user named Caleb Sills.</span></span>
  
```
$userName="Caleb Sills"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="b9469-p105">Mit der **$upn** -Variable können Sie Änderungen an den einzelnen Konten basierend auf deren Anzeigenamen vornehmen. Hier ist ein Beispiel für das Festlegen des Verwendungsstandorts von Belinda Newman in Frankreich. Dabei wird Ihr Anzeigenamen anstatt Ihres Benutzerprinzipalnamens verwendet:</span><span class="sxs-lookup"><span data-stu-id="b9469-p105">By using a **$upn** variable, you can make changes to individual accounts based on their display name. Here is an example of setting Belinda Newman's usage location to France, but specifying her display name rather than her User Principal Name:</span></span>
  
```
$userName="<Display name>"
$upn=(Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-MsolUser -UserPrincipalName $upn -UsageLocation "FR"
```

## <a name="change-properties-for-all-user-accounts"></a><span data-ttu-id="b9469-143">Ändern von Eigenschaften für alle Benutzerkonten</span><span class="sxs-lookup"><span data-stu-id="b9469-143">Change properties for all user accounts</span></span>

<span data-ttu-id="b9469-p106">Um die Eigenschaften für alle Benutzer zu ändern, können Sie eine Kombination der Cmdlets **Get-MsolUser** und **Set-MsolUser** verwenden. Im folgende Beispiel wird der Verwendungsstandort für alle Benutzer in Frankreich geändert:</span><span class="sxs-lookup"><span data-stu-id="b9469-p106">To change properties for all users, you can use the combination of the **Get-MsolUser** and **Set-MsolUser** cmdlets. The following example changes the usage location for all users to France:</span></span>
  
```
Get-MsolUser | Set-MsolUser -UsageLocation "FR"
```

<span data-ttu-id="b9469-146">Dieser Befehl weist Office 365 PowerShell zu folgenden Aktionen an:</span><span class="sxs-lookup"><span data-stu-id="b9469-146">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="b9469-147">Alle Informationen für die Benutzerkonten ( **Get-MsolUser** ) abrufen und senden Sie sie an den nächsten Befehl ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="b9469-147">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="b9469-148">Benutzerstandort auf „Frankreich" festlegen ( **Set-MsolUser -UsageLocation "FR"** ).</span><span class="sxs-lookup"><span data-stu-id="b9469-148">Set the user location to France ( **Set-MsolUser -UsageLocation "FR"** ).</span></span>
    
## <a name="change-properties-for-a-specific-set-of-user-accounts"></a><span data-ttu-id="b9469-149">Ändern von Eigenschaften für bestimmte Benutzerkonten</span><span class="sxs-lookup"><span data-stu-id="b9469-149">Change properties for a specific set of user accounts</span></span>

<span data-ttu-id="b9469-p107">Um die Eigenschaften für einen bestimmten Satz von Benutzerkonten zu ändern, können Sie eine Kombination der Cmdlets **Get-MsolUser**, **Where-Object** und **Set-MsolUser** verwenden. Im folgende Beispiel wird der Verwendungsstandort für alle Benutzer in der Buchhaltungsabteilung in Frankreich geändert:</span><span class="sxs-lookup"><span data-stu-id="b9469-p107">To change properties for a specific set of user account, you can use the combination of the **Get-MsolUser**, **Where-Object**, and **Set-MsolUser** cmdlets. The following example changes the usage location for all the users in the Accounting department to France:</span></span>
  
```
Get-MsolUser | Where-Object {$_.Department -eq "Accounting"} | Set-MsolUser -UsageLocation "FR"
```

<span data-ttu-id="b9469-152">Dieser Befehl weist Office 365 PowerShell zu folgenden Aktionen an:</span><span class="sxs-lookup"><span data-stu-id="b9469-152">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="b9469-153">Alle Informationen für die Benutzerkonten ( **Get-MsolUser** ) abrufen und senden Sie sie an den nächsten Befehl ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="b9469-153">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="b9469-154">Hier finden Sie alle Benutzerkonten, die ihre Abteilung-Eigenschaft auf "Accounting" festgelegt ( **Where-Object {$_. Abteilung - Eq "Accounting"}** ) und die resultierende Daten mit dem nächsten Befehl senden ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="b9469-154">Find all of the user accounts that have their Department property set to "Accounting" ( **Where-Object {$_.Department -eq "Accounting"}** ) and send the resulting information to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="b9469-155">Benutzerstandort auf „Frankreich" festlegen ( **Set-MsolUser -UsageLocation "FR"** ).</span><span class="sxs-lookup"><span data-stu-id="b9469-155">Set the user location to France ( **Set-MsolUser -UsageLocation "FR"** ).</span></span>
    
- <span data-ttu-id="b9469-156">Jeweils auf einem Bildschirm anzeigen ( **More** ).</span><span class="sxs-lookup"><span data-stu-id="b9469-156">Display them one screen at a time ( **More** ).</span></span>
    
## <a name="use-the-azure-active-directory-v2-powershell-module-to-configure-user-account-properties"></a><span data-ttu-id="b9469-157">Konfigurieren der Benutzerkontoeigenschaften mit dem Azure Active Directory V2 PowerShell-Modul</span><span class="sxs-lookup"><span data-stu-id="b9469-157">Use the Azure Active Directory V2 PowerShell module to configure user account properties</span></span>

<span data-ttu-id="b9469-p108">Um die Eigenschaften für Benutzerkonten mit Azure Active Directory V2 PowerShell-Modul konfigurieren möchten, verwenden Sie das Cmdlet [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) und geben Sie die Eigenschaften zum Festlegen oder ändern. Aber Sie müssen Sie zuerst zu Ihrem Abonnement verbinden. Die Anweisungen finden Sie unter [Verbinden mit dem Azure Active Directory V2 PowerShell-Modul](https://go.microsoft.com/fwlink/?linkid=842218).</span><span class="sxs-lookup"><span data-stu-id="b9469-p108">To configure properties for user accounts with the Azure Active Directory V2 PowerShell module, you use the [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) cmdlet and specify the properties to set or change. But first, you must connect to your subscription. For the instructions, see [Connect with the Azure Active Directory V2 PowerShell module](https://go.microsoft.com/fwlink/?linkid=842218).</span></span>
  
### <a name="change-properties-for-a-specific-user-account"></a><span data-ttu-id="b9469-161">Ändern von Eigenschaften für ein bestimmtes Benutzerkonto</span><span class="sxs-lookup"><span data-stu-id="b9469-161">Change properties for a specific user account</span></span>

<span data-ttu-id="b9469-162">Mit diesem Beispielbefehl wird der Verwendungsstandort von Belinda Newman in Frankreich geändert:</span><span class="sxs-lookup"><span data-stu-id="b9469-162">This example command changes Belinda Newman's usage location to France:</span></span>
  
```
Set-AzureADUser -ObjectID "BelindaN@litwareinc.onmicosoft.com" -UsageLocation "FR"
```

<span data-ttu-id="b9469-p109">Sie identifizieren das Konto mit dem **-ObjectID** -Parameter und legen bestimmte Eigenschaften mit weiteren Parametern fest bzw. ändern diese. Nachfolgend ist eine Liste der am häufigsten verwendeten Parameter aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="b9469-p109">You identify the account with the **-ObjectID** parameter and set or change specific properties with additional parameters. Here is a list of the most common parameters.</span></span>
  
- <span data-ttu-id="b9469-165">-Abteilung "\<Abteilungsnamen >"</span><span class="sxs-lookup"><span data-stu-id="b9469-165">-Department "\<department name>"</span></span>
    
- <span data-ttu-id="b9469-166">DisplayName-"\<vollständige Benutzername >"</span><span class="sxs-lookup"><span data-stu-id="b9469-166">-DisplayName "\<full user name>"</span></span>
    
- <span data-ttu-id="b9469-167">-FacsimilieTelephoneNumber "\<Faxnummer >"</span><span class="sxs-lookup"><span data-stu-id="b9469-167">-FacsimilieTelephoneNumber "\<fax number>"</span></span>
    
- <span data-ttu-id="b9469-168">-Vorname "\<Vorname Benutzer >"</span><span class="sxs-lookup"><span data-stu-id="b9469-168">-GivenName "\<user first name>"</span></span>
    
- <span data-ttu-id="b9469-169">-Nachname "\<letzten Benutzername >"</span><span class="sxs-lookup"><span data-stu-id="b9469-169">-Surname "\<user last name>"</span></span>
    
- <span data-ttu-id="b9469-170">-Mobile "\<Mobiltelefonnummer >"</span><span class="sxs-lookup"><span data-stu-id="b9469-170">-Mobile "\<mobile phone number>"</span></span>
    
- <span data-ttu-id="b9469-171">JobTitle-"\<Position >"</span><span class="sxs-lookup"><span data-stu-id="b9469-171">-JobTitle "\<job title>"</span></span>
    
- <span data-ttu-id="b9469-172">-PreferredLanguage "\<Sprache >"</span><span class="sxs-lookup"><span data-stu-id="b9469-172">-PreferredLanguage "\<language>"</span></span>
    
- <span data-ttu-id="b9469-173">StreetAddress-"\<Straße >"</span><span class="sxs-lookup"><span data-stu-id="b9469-173">-StreetAddress "\<street address>"</span></span>
    
- <span data-ttu-id="b9469-174">-Stadt "\<Ortsname >"</span><span class="sxs-lookup"><span data-stu-id="b9469-174">-City "\<city name>"</span></span>
    
- <span data-ttu-id="b9469-175">-Status "\<Zustand Name >"</span><span class="sxs-lookup"><span data-stu-id="b9469-175">-State "\<state name>"</span></span>
    
- <span data-ttu-id="b9469-176">PostalCode-"\<Postleitzahl >"</span><span class="sxs-lookup"><span data-stu-id="b9469-176">-PostalCode "\<postal code>"</span></span>
    
- <span data-ttu-id="b9469-177">-Land "\<Land Name >"</span><span class="sxs-lookup"><span data-stu-id="b9469-177">-Country "\<country name>"</span></span>
    
- <span data-ttu-id="b9469-178">-TelephoneNumber "\<Office Rufnummer >"</span><span class="sxs-lookup"><span data-stu-id="b9469-178">-TelephoneNumber "\<office phone number>"</span></span>
    
- <span data-ttu-id="b9469-179">-Usagelocation-Wert angegeben "\<2-Land oder Region Zeichencode >"</span><span class="sxs-lookup"><span data-stu-id="b9469-179">-UsageLocation "\<2-character country or region code>"</span></span>
    
    <span data-ttu-id="b9469-180">Dies ist der zweistellige ISO 3166-1-Ländercode bzw. Regionscode (Alpha-2, A2).</span><span class="sxs-lookup"><span data-stu-id="b9469-180">This is the ISO 3166-1 alpha-2 (A2) two-letter country or region code.</span></span>
    
<span data-ttu-id="b9469-181">Informationen zu weiteren Parametern finden Sie unter [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0).</span><span class="sxs-lookup"><span data-stu-id="b9469-181">See [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) for additional parameters.</span></span>
  
<span data-ttu-id="b9469-182">Um die User Principal Name für Ihre Benutzerkonten anzuzeigen, führen Sie den folgenden Befehl aus.</span><span class="sxs-lookup"><span data-stu-id="b9469-182">To display the User Principal Name for your user accounts, run the following command.</span></span>
  
```
Get-AzureADUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

<span data-ttu-id="b9469-183">Dieser Befehl weist Office 365 PowerShell zu folgenden Aktionen an:</span><span class="sxs-lookup"><span data-stu-id="b9469-183">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="b9469-184">Alle Informationen für die Benutzerkonten ( **Get-AzureADUser** ) abrufen und senden Sie sie an den nächsten Befehl ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="b9469-184">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="b9469-185">Die Liste der User Principal Names alphabetisch sortieren ( **Sort-Objekt UserPrincipalName** ) und senden Sie sie an den nächsten Befehl ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="b9469-185">Sort the list of User Principal Names alphabetically ( **Sort-Object UserPrincipalName** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="b9469-186">Nur die UserPrincipalName-Eigenschaft für jedes Konto anzeigen ( **Select-Object UserPrincipalName** ).</span><span class="sxs-lookup"><span data-stu-id="b9469-186">Display just the User Principal Name property for each account ( **Select-Object UserPrincipalName** ).</span></span>
- <span data-ttu-id="b9469-187">Jeweils auf einem Bildschirm anzeigen ( **More** ).</span><span class="sxs-lookup"><span data-stu-id="b9469-187">Display them one screen at a time ( **More** ).</span></span>
    
<span data-ttu-id="b9469-p110">Mit diesem Befehl werden alle Konten aufgelistet. Wenn Sie die User Principal Name für ein Konto basierend auf deren Anzeige anzeigen möchten name (vor- und Nachname), füllen Sie die unten aufgeführten **$userName** -Variable (Entfernen der \< und > Zeichen), und führen Sie dann die folgenden Befehle aus:</span><span class="sxs-lookup"><span data-stu-id="b9469-p110">This command will list all of your accounts. If you want to display the User Principal Name for an account based on its display name (first and last name), fill in the **$userName** variable below (removing the \< and > characters), and then run the following commands:</span></span>
  
```
$userName="<Display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="b9469-190">In diesem Beispiel wird der Benutzerprinzipalname für den Benutzer namens Caleb Sills angezeigt.</span><span class="sxs-lookup"><span data-stu-id="b9469-190">This example displays the User Principal Name for the user named Caleb Sills.</span></span>
  
```
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="b9469-p111">Mit der **$upn** -Variable können Sie Änderungen an den einzelnen Konten basierend auf deren Anzeigenamen vornehmen. Hier ist ein Beispiel für das Festlegen des Verwendungsstandorts von Belinda Newman in Frankreich. Dabei wird Ihr Anzeigenamen anstatt Ihres Benutzerprinzipalnamens verwendet:</span><span class="sxs-lookup"><span data-stu-id="b9469-p111">By using a **$upn** variable, you can make changes to individual accounts based on their display name. Here is an example of setting Belinda Newman's usage location to France, but specifying her display name rather than her User Principal Name:</span></span>
  
```
$userName="Belinda Newman"
$upn=(Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-AzureADUser -ObjectID $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a><span data-ttu-id="b9469-193">Ändern von Eigenschaften für alle Benutzerkonten</span><span class="sxs-lookup"><span data-stu-id="b9469-193">Change properties for all user accounts</span></span>

<span data-ttu-id="b9469-p112">Um die Eigenschaften für alle Benutzer zu ändern, können Sie eine Kombination der Cmdlets **Get-AzureADUser** und **et-AzureADUser** verwenden. Im folgende Beispiel wird der Verwendungsstandort für alle Benutzer in Frankreich geändert:</span><span class="sxs-lookup"><span data-stu-id="b9469-p112">To change properties for all users, you can use the combination of the **Get-AzureADUser** and **Set-AzureADUser** cmdlets. The following example changes the usage location for all users to France:</span></span>
  
```
Get-AzureADUser | Set-AzureADUser -UsageLocation "FR"
```

<span data-ttu-id="b9469-196">Dieser Befehl weist Office 365 PowerShell zu folgenden Aktionen an:</span><span class="sxs-lookup"><span data-stu-id="b9469-196">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="b9469-197">Alle Informationen für die Benutzerkonten ( **Get-AzureADUser** ) abrufen und senden Sie sie an den nächsten Befehl ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="b9469-197">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="b9469-198">Benutzerstandort auf „Frankreich" festlegen ( **Set-AzureADUser -UsageLocation "FR"** ).</span><span class="sxs-lookup"><span data-stu-id="b9469-198">Set the user location to France ( **Set-AzureADUser -UsageLocation "FR"** ).</span></span>
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a><span data-ttu-id="b9469-199">Ändern von Eigenschaften für bestimmte Benutzerkonten</span><span class="sxs-lookup"><span data-stu-id="b9469-199">Change properties for a specific set of user accounts</span></span>

<span data-ttu-id="b9469-p113">Um Eigenschaften für eine bestimmte Gruppe von Benutzerkonto zu ändern, können Sie die Kombination aus den Cmdlets **Get-AzureADUser**, **wobei**und **Set-AzureADUser** verwenden. Im folgenden Beispiel wird den Verwendungsspeicherort für alle Benutzer in der Buchhaltung in Frankreich geändert:</span><span class="sxs-lookup"><span data-stu-id="b9469-p113">To change properties for a specific set of user account, you can use the combination of the **Get-AzureADUser**, **Where**, and **Set-AzureADUser** cmdlets. The following example changes the usage location for all the users in the Accounting department to France:</span></span>
  
```
Get-AzureADUser | Where-Object {$_.Department -eq "Accounting"} | Set-AzureADUser -UsageLocation "FR"
```

<span data-ttu-id="b9469-202">Dieser Befehl weist Office 365 PowerShell zu folgenden Aktionen an:</span><span class="sxs-lookup"><span data-stu-id="b9469-202">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="b9469-203">Alle Informationen für die Benutzerkonten ( **Get-AzureADUser** ) abrufen und senden Sie sie an den nächsten Befehl ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="b9469-203">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="b9469-204">Hier finden Sie alle Benutzerkonten, die die Abteilung-Eigenschaft auf "Buchhaltung" festgelegt werden ( **, in dem {$_. Abteilung - Eq "Accounting"}** ) und die resultierende Daten mit dem nächsten Befehl senden ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="b9469-204">Find all of the user accounts that have their Department property set to "Accounting" ( **Where {$_.Department -eq "Accounting"}** ) and send the resulting information to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="b9469-205">Benutzerstandort auf „Frankreich" festlegen ( **Set-AzureADUser -UsageLocation "FR"** ).</span><span class="sxs-lookup"><span data-stu-id="b9469-205">Set the user location to France ( **Set-AzureADUser -UsageLocation "FR"** ).</span></span>
    
## <a name="see-also"></a><span data-ttu-id="b9469-206">See also</span><span class="sxs-lookup"><span data-stu-id="b9469-206">See also</span></span>

#### 

[<span data-ttu-id="b9469-207">Verwalten von Benutzerkonten und Lizenzen mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="b9469-207">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="b9469-208">Verwalten von Office 365 mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="b9469-208">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="b9469-209">Erste Schritte mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="b9469-209">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

