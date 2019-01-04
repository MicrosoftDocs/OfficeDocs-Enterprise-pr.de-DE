---
title: Blockieren von Benutzerkonten mit Office 365 PowerShell
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
- Ent_Office_Other
- PowerShell
ms.assetid: 04e58c2a-400b-496a-acd4-8ec5d37236dc
description: Erläutert, wie mithilfe von Office 365 PowerShell blockieren und zulassen einzelner Zugriff auf Office 365-Konten.
ms.openlocfilehash: 0e1ac3f61acafedd77c2af760b8316aa6b936e7b
ms.sourcegitcommit: 15db0f1e5f8036e46063662d7df22387906f8ba7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/04/2019
ms.locfileid: "27546476"
---
# <a name="block-user-accounts-with-office-365-powershell"></a><span data-ttu-id="ba761-103">Blockieren von Benutzerkonten mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="ba761-103">Block user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="ba761-104">**Zusammenfassung:**  Erläutert, wie mithilfe von Office 365 PowerShell blockieren und zulassen einzelner Zugriff auf Office 365-Konten.</span><span class="sxs-lookup"><span data-stu-id="ba761-104">**Summary:**  Explains how to use Office 365 PowerShell to block and unblock access to Office 365 accounts.</span></span>
  
<span data-ttu-id="ba761-p101">Zugriff auf Office 365-Konto blockiert verhindert, dass jeder Benutzer mit dem Konto anzumelden und Zugriff auf die Dienste und Daten in Office 365-Organisation. Office 365 PowerShell können Sie um Zugriff auf einzelne und mehrere Benutzerkonten zu blockieren.</span><span class="sxs-lookup"><span data-stu-id="ba761-p101">Blocking access to an Office 365 account prevents anyone from using the account to sign in and access the services and data in your Office 365 organization. You can use Office 365 PowerShell to block access to individual and multiple user accounts.</span></span>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="ba761-107">Verwenden von Azure Active Directory PowerShell Graph-Modul</span><span class="sxs-lookup"><span data-stu-id="ba761-107">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="ba761-108">Zuerst [eine Verbindung mit Ihrem Office 365-Mandanten](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="ba761-108">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
 
### <a name="block-access-to-individual-user-accounts"></a><span data-ttu-id="ba761-109">Blockieren des Zugriffs auf einzelne Benutzerkonten</span><span class="sxs-lookup"><span data-stu-id="ba761-109">Block access to individual user accounts</span></span>

<span data-ttu-id="ba761-110">Verwenden Sie die folgende Syntax, um ein einzelnes Benutzerkonto blockieren:</span><span class="sxs-lookup"><span data-stu-id="ba761-110">Use the following syntax to block an individual user account:</span></span>
  
```
Set-AzureADUser -ObjectID <sign-in name of the user account> -AccountEnabled $false
```

> [!NOTE]
> <span data-ttu-id="ba761-111">Der Parameter - ObjectID im Cmdlet Set-AzureAD akzeptiert entweder den Anmeldenamen Kontonamen, den User Principal Name, oder das Konto Objekt-ID.</span><span class="sxs-lookup"><span data-stu-id="ba761-111">The -ObjectID parameter in the Set-AzureAD cmdlet accepts either the account sign-in name, also known as the User Principal Name, or the account's object ID.</span></span> 
  
<span data-ttu-id="ba761-112">Dieses Beispiel blockiert den Zugriff auf das Benutzerkonto „fabricec@litwareinc.com“.</span><span class="sxs-lookup"><span data-stu-id="ba761-112">This example blocks access to the user account fabricec@litwareinc.com.</span></span>
  
```
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $false
```

<span data-ttu-id="ba761-113">Führen Sie zum Aufheben der Blockierung dieses Benutzerkontos den folgenden Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="ba761-113">To unblock this user account, run the following command:</span></span>
  
```
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $true
```

<span data-ttu-id="ba761-114">Wenn das Benutzerkonto, den, das Anzeigenamen des Benutzers UPN anhand, anzeigen möchten, verwenden Sie die folgenden Befehle ein:</span><span class="sxs-lookup"><span data-stu-id="ba761-114">To display the user account UPN based on the user's display name, use the following commands:</span></span>
  
```
$userName="<display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName

```

<span data-ttu-id="ba761-115">In diesem Beispiel wird das Benutzerkonto UPN für den Benutzer mit dem Namen Caleb Sills.</span><span class="sxs-lookup"><span data-stu-id="ba761-115">This example displays the user account UPN for the user named Caleb Sills.</span></span>
  
```
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="ba761-116">Um ein Konto basierend auf den Anzeigenamen des Benutzers zu blockieren, verwenden Sie die folgenden Befehle ein:</span><span class="sxs-lookup"><span data-stu-id="ba761-116">To block an account based on the user's display name, use the following commands:</span></span>
  
```
$userName="<display name>"
Set-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName -AccountEnabled $false

```

<span data-ttu-id="ba761-117">Zu einem beliebigen Zeitpunkt können Sie die Sperrung eines Benutzerkontos mit dem folgenden Befehl überprüfen:</span><span class="sxs-lookup"><span data-stu-id="ba761-117">At any time, you can check the blocked status of a user account with the following command:</span></span>
  
```
Get-AzureADUser -UserPrincipalName <UPN of user account> | Select DisplayName,AccountEnabled
```

### <a name="block-access-to-multiple-user-accounts"></a><span data-ttu-id="ba761-118">Blockieren Sie den Zugriff auf mehrere Benutzerkonten</span><span class="sxs-lookup"><span data-stu-id="ba761-118">Block access to multiple user accounts</span></span>

<span data-ttu-id="ba761-119">Um Zugriff auf mehrere Benutzerkonten zu blockieren, erstellen Sie eine Textdatei mit einer Anmeldung Kontoname für jede Zeile wie folgt:</span><span class="sxs-lookup"><span data-stu-id="ba761-119">To block access to multiple user accounts, create a text file that contains one account sign-in name on each line like this:</span></span>
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

<span data-ttu-id="ba761-p102">In den folgenden Befehlen wird die Text-Beispieldatei C:\My Documents\Accounts.txt. Ersetzen Sie Sie durch den Pfad und den Namen der Textdatei.</span><span class="sxs-lookup"><span data-stu-id="ba761-p102">In the following commands, the example text file is C:\My Documents\Accounts.txt. Replace this with the path and file name of your text file.</span></span>
  
<span data-ttu-id="ba761-122">Um den Zugriff auf die in der Textdatei aufgelisteten Konten zu blockieren, führen Sie den folgenden Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="ba761-122">To block access to the accounts listed in the text file, run the following command:</span></span>
    
```
Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-AzureADUSer -ObjectID $_ -AccountEnabled $false }
```

<span data-ttu-id="ba761-123">Um den Zugriff auf die in der Textdatei aufgelisteten Konten wieder freizugeben, führen Sie den folgenden Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="ba761-123">To unblock the accounts listed in the text file, run the following command:</span></span>
    
```
Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-AzureADUSer -ObjectID $_ -AccountEnabled $true }
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="ba761-124">Verwenden Sie die Microsoft Azure Active Directory-Moduls für Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="ba761-124">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="ba761-125">Zuerst [eine Verbindung mit Ihrem Office 365-Mandanten](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="ba761-125">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

    
### <a name="block-access-to-individual-user-accounts"></a><span data-ttu-id="ba761-126">Blockieren des Zugriffs auf einzelne Benutzerkonten</span><span class="sxs-lookup"><span data-stu-id="ba761-126">Block access to individual user accounts</span></span>

<span data-ttu-id="ba761-127">Verwenden Sie die folgende Syntax, um den Zugriff auf ein einzelnes Benutzerkonto zu blockieren:</span><span class="sxs-lookup"><span data-stu-id="ba761-127">Use the following syntax to block access to an individual user account:</span></span>
  
```
Set-MsolUser -UserPrincipalName <sign-in name of user account>  -BlockCredential $true
```

<span data-ttu-id="ba761-128">Dieses Beispiel blockiert den Zugriff auf das Benutzerkonto „fabricec@litwareinc.com“.</span><span class="sxs-lookup"><span data-stu-id="ba761-128">This example blocks access to the user account fabricec@litwareinc.com.</span></span>
  
```
Set-MsolUser -UserPrincipalName fabricec@litwareinc.com -BlockCredential $true
```

<span data-ttu-id="ba761-129">Führen Sie zum Aufheben der Blockierung des Benutzerkontos den folgenden Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="ba761-129">To unblock the user account, run the following command:</span></span>
  
```
Set-MsolUser -UserPrincipalName <sign-in name of user account>  -BlockCredential $false
```

<span data-ttu-id="ba761-130">Zu einem beliebigen Zeitpunkt können Sie die Sperrung eines Benutzerkontos mit dem folgenden Befehl überprüfen:</span><span class="sxs-lookup"><span data-stu-id="ba761-130">At any time, you can check the blocked status of a user account with the following command:</span></span>
  
```
Get-MsolUser -UserPrincipalName <sign-in name of user account> | Select DisplayName,BlockCredential
```

### <a name="block-access-to-multiple-user-accounts"></a><span data-ttu-id="ba761-131">Blockieren Sie den Zugriff auf mehrere Benutzerkonten</span><span class="sxs-lookup"><span data-stu-id="ba761-131">Block access to multiple user accounts</span></span>

<span data-ttu-id="ba761-132">Erstellen Sie zunächst eine Textdatei mit einem Konto in jeder Zeile wie folgt:</span><span class="sxs-lookup"><span data-stu-id="ba761-132">First, create a text file that contains one account on each line like this:</span></span>
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```
<span data-ttu-id="ba761-p103">In den folgenden Befehlen wird die Text-Beispieldatei C:\My Documents\Accounts.txt. Ersetzen Sie Sie durch den Pfad und den Namen der Textdatei.</span><span class="sxs-lookup"><span data-stu-id="ba761-p103">In the following commands, the example text file is C:\My Documents\Accounts.txt. Replace this with the path and file name of your text file.</span></span>
    
<span data-ttu-id="ba761-135">Um den Zugriff auf die in der Textdatei aufgelisteten Konten zu blockieren, führen Sie den folgenden Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="ba761-135">To block access to the accounts listed in the text file, run the following command:</span></span>
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $true }
  ```
<span data-ttu-id="ba761-136">Um den Zugriff auf die in der Textdatei aufgelisteten Konten wieder freizugeben, führen Sie den folgenden Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="ba761-136">To unblock the accounts listed in the text file, run the following command:</span></span>
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $false }
  ```

## <a name="see-also"></a><span data-ttu-id="ba761-137">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="ba761-137">See also</span></span>

[<span data-ttu-id="ba761-138">Verwalten von Benutzerkonten und Lizenzen mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="ba761-138">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="ba761-139">Verwalten von Office 365 mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="ba761-139">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="ba761-140">Erste Schritte mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="ba761-140">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
