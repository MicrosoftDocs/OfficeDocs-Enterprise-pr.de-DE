---
title: Anzeigen von Benutzerkonten mit Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 03/19/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- LIL_Placement
- PowerShell
- Ent_Office_Other
ms.assetid: bb12f49d-a85d-4f3b-ada2-5c4e33977b10
description: 'Zusammenfassung: anzeigen, auflisten oder Anzeigen von Benutzerkonten mit Office 365 PowerShell auf verschiedene Weise.'
ms.openlocfilehash: 28e6ec6936040c6bb84a49e354ae1ee5e9e9de44
ms.sourcegitcommit: 460c722d63e7e604ef0a57ec18fa7900fa6a4157
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2019
ms.locfileid: "39655837"
---
# <a name="view-user-accounts-with-office-365-powershell"></a><span data-ttu-id="b8f47-103">Anzeigen von Benutzerkonten mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="b8f47-103">View user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="b8f47-104">Sie können zwar das Microsoft 365 Admin Center verwenden, um die Konten für Ihren Office 365 Mandanten anzuzeigen, aber Sie können auch Office 365 PowerShell verwenden und einige Dinge tun, die das Admin Center nicht kann.</span><span class="sxs-lookup"><span data-stu-id="b8f47-104">Although you can use the Microsoft 365 admin center to view the accounts for your Office 365 tenant, you can also use Office 365 PowerShell and do some things that the admin center cannot.</span></span>
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="b8f47-105">Verwenden der Azure Active Directory PowerShell für Graph-Module</span><span class="sxs-lookup"><span data-stu-id="b8f47-105">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="b8f47-106">Verbinden Sie sich zuerst [mit Ihrem Office 365-Mandanten](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="b8f47-106">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  
### <a name="view-all-accounts"></a><span data-ttu-id="b8f47-107">Alle Konten anzeigen</span><span class="sxs-lookup"><span data-stu-id="b8f47-107">View all accounts</span></span>

<span data-ttu-id="b8f47-108">Um die vollständige Liste der Benutzerkonten anzuzeigen, führen Sie den folgenden Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="b8f47-108">To display the full list of user accounts, run this command:</span></span>
  
```powershell
Get-AzureADUser
```

<span data-ttu-id="b8f47-109">Es sollten Informationen ähnlich den folgenden angezeigt werden:</span><span class="sxs-lookup"><span data-stu-id="b8f47-109">You should see information similar to this:</span></span>
  
```powershell
ObjectId                             DisplayName                                           UserPrincipalName
--------                             -----------                                           -----------------
032fc1fc-b5a2-46f1-8635-3d7dcb52c48d Adele Vance                                           AdeleV@litwareinc.OnMicr...
bd1e6af1-41e7-4f77-a2ac-5b209950135c Global Administrator                                  admin@litwareinc.onmicro...
ec37a4d6-232e-4eb7-82a5-1613490642a5 Alex Wilber                                           AlexW@litwareinc.OnMicro...
be4bdddd-c790-424c-9f96-a0cf609b7815 Allan Deyoung                                         AllanD@litwareinc.OnMicr...
598ab87b-76f0-4bf9-9538-bd46b10f4438 Christie Cline                                        ChristieC@litwareinc.OnM...
40722671-e520-4a5f-97d4-0bc9e9b2dc0f Debra Berger                                          DebraB@litwareinc.OnMicr...
```

### <a name="view-a-specific-account"></a><span data-ttu-id="b8f47-110">Anzeigen eines bestimmten Kontos</span><span class="sxs-lookup"><span data-stu-id="b8f47-110">View a specific account</span></span>

<span data-ttu-id="b8f47-111">Um ein bestimmtes Benutzerkonto anzuzeigen, geben Sie den Anmeldekontonamen des Benutzerkontos ein, das auch als Benutzerprinzipalname (User Principal Name, UPN) bezeichnet wird, entfernen Sie die Zeichen "#a0" und "#a1", und führen Sie den folgenden Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="b8f47-111">To display a specific user account, fill in the sign-in account name of the user account, also known as the user principal name (UPN), remove the "<" and ">" characters, and run this command:</span></span>
  
```powershell
Get-AzureADUser -ObjectID <sign-in name of the user account>
```

<span data-ttu-id="b8f47-112">Es folgt ein Beispiel:</span><span class="sxs-lookup"><span data-stu-id="b8f47-112">Here is an example:</span></span>
  
```powershell
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com
```

### <a name="view-additional-property-values-for-a-specific-account"></a><span data-ttu-id="b8f47-113">Anzeigen zusätzlicher Eigenschaftswerte für ein bestimmtes Konto</span><span class="sxs-lookup"><span data-stu-id="b8f47-113">View additional property values for a specific account</span></span>

<span data-ttu-id="b8f47-114">Standardmäßig zeigt das Cmdlet **Get-AzureADUser** nur die Eigenschaften ObjectID, DisplayName und userPrincipalName von Konten an.</span><span class="sxs-lookup"><span data-stu-id="b8f47-114">By default, the **Get-AzureADUser** cmdlet only displays the ObjectID, DisplayName, and UserPrincipalName properties of accounts.</span></span>

<span data-ttu-id="b8f47-115">Um die Liste der anzuzeigenden Eigenschaften selektiver zu machen, können Sie das Cmdlet **Select-Object** in Kombination mit dem Cmdlet **Get-AzureADUser** verwenden.</span><span class="sxs-lookup"><span data-stu-id="b8f47-115">To be more selective about the list of properties to display, you can use the **Select-Object** cmdlet in combination with the **Get-AzureADUser** cmdlet.</span></span> <span data-ttu-id="b8f47-116">Um die beiden Cmdlets zu kombinieren, verwenden wir das "Pipe"-Zeichen "|", das Azure Active Directory PowerShell für Graph anweist, die Ergebnisse eines Befehls zu übernehmen und an den nächsten Befehl zu senden.</span><span class="sxs-lookup"><span data-stu-id="b8f47-116">To combine the two cmdlets, we use the "pipe" character "|", which tells Azure Active Directory PowerShell for Graph to take the results of one command and send it to the next command.</span></span> <span data-ttu-id="b8f47-117">Es folgt ein Beispielbefehl, mit dem DisplayName, Department und UsageLocation für jedes Benutzerkonto angezeigt werden:</span><span class="sxs-lookup"><span data-stu-id="b8f47-117">Here is an example command that displays the DisplayName, Department, and UsageLocation for every user account:</span></span>
  
```powershell
Get-AzureADUser | Select-Object DisplayName,Department,UsageLocation
```

<span data-ttu-id="b8f47-118">Dieser Befehl gibt Office 365 Powershell die folgenden Anweisungen:</span><span class="sxs-lookup"><span data-stu-id="b8f47-118">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="b8f47-119">Alle Informationen der Benutzerkonten abrufen (**Get-AzureADUser**) und an den nächsten Befehl senden (**|**).</span><span class="sxs-lookup"><span data-stu-id="b8f47-119">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="b8f47-120">Nur den Namen des Benutzerkontos, die Abteilung und den Verwendungs Speicherort anzeigen ( **Select-Object DisplayName, Department, UsageLocation** ).</span><span class="sxs-lookup"><span data-stu-id="b8f47-120">Display only the user account name, department, and usage location ( **Select-Object DisplayName, Department, UsageLocation** ).</span></span>
  
<span data-ttu-id="b8f47-121">Wenn Sie alle Eigenschaften für Benutzerkonten anzeigen möchten, verwenden Sie das Cmdlet **Select-Object** und das Platzhalterzeichen (\*), um Sie alle für ein bestimmtes Benutzerkonto anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="b8f47-121">To see all of the properties for user accounts, use the **Select-Object** cmdlet and the wildcard character (\*) to display them all for a specific user account.</span></span> <span data-ttu-id="b8f47-122">Es folgt ein Beispiel:</span><span class="sxs-lookup"><span data-stu-id="b8f47-122">Here is an example:</span></span>
  
```powershell
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

<span data-ttu-id="b8f47-123">Als weiteres Beispiel können Sie den aktivierten Status eines bestimmten Benutzerkontos überprüfen, indem Sie den folgenden Befehl ausführen:</span><span class="sxs-lookup"><span data-stu-id="b8f47-123">As another example, you can check the enabled status of a specific user account with the following command:</span></span>
  
```powershell
Get-AzureADUser -ObjectID <sign-in name of the user account> | Select-Object DisplayName,UserPrincipalName,AccountEnabled
```

### <a name="view-some-accounts-based-on-a-common-property"></a><span data-ttu-id="b8f47-124">Anzeigen einiger Konten basierend auf einer gemeinsamen Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="b8f47-124">View some accounts based on a common property</span></span>

<span data-ttu-id="b8f47-125">Um die Liste der angezeigten Konten weiter einzugrenzen, können Sie die **Where-Object**- und **Get-AzureADUser**-Cmdlets zusammen verwenden.</span><span class="sxs-lookup"><span data-stu-id="b8f47-125">To be more selective about the list of accounts to display, you can use the **Where-Object** cmdlet in combination with the **Get-AzureADUser** cmdlet.</span></span> <span data-ttu-id="b8f47-126">Um die beiden Cmdlets zu kombinieren, verwenden wir das "Pipe"-Zeichen "|", das Azure Active Directory PowerShell für Graph anweist, die Ergebnisse eines Befehls zu übernehmen und an den nächsten Befehl zu senden.</span><span class="sxs-lookup"><span data-stu-id="b8f47-126">To combine the two cmdlets, we use the "pipe" character "|", which tells Azure Active Directory PowerShell for Graph to take the results of one command and send it to the next command.</span></span> <span data-ttu-id="b8f47-127">Nachfolgend ist ein Beispielbefehl aufgeführt, mit dem nur die Benutzerkonten angezeigt werden, die über einen nicht angegebenen Verwendungsstandort verfügen:</span><span class="sxs-lookup"><span data-stu-id="b8f47-127">Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```powershell
Get-AzureADUser | Where-Object {$_.UsageLocation -eq $Null}
```

<span data-ttu-id="b8f47-128">Dieser Befehl weist Azure Active Directory PowerShell für Graph Folgendes zu:</span><span class="sxs-lookup"><span data-stu-id="b8f47-128">This command instructs Azure Active Directory PowerShell for Graph to:</span></span>
  
- <span data-ttu-id="b8f47-129">Alle Informationen der Benutzerkonten abrufen (**Get-AzureADUser**) und an den nächsten Befehl senden (**|**).</span><span class="sxs-lookup"><span data-stu-id="b8f47-129">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="b8f47-130">Hier finden Sie alle Benutzerkonten mit einem nicht angegebenen Verwendungs Speicherort ( **Where-Object {\_$. UsageLocation-EQ $NULL}** ).</span><span class="sxs-lookup"><span data-stu-id="b8f47-130">Find all of the user accounts that have an unspecified usage location ( **Where-Object {$\_.UsageLocation -eq $Null}** ).</span></span> <span data-ttu-id="b8f47-131">In den geschweiften Klammern weist der Befehl Office 365 PowerShell an, nur den kontensatz zu finden, in dem die UsageLocation-Benutzerkonto Eigenschaft ( \*\* $ \_. UsageLocation\*\* ) ist nicht angegeben ( **-EQ $NULL** ).</span><span class="sxs-lookup"><span data-stu-id="b8f47-131">Inside the braces, the command instructs Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
<span data-ttu-id="b8f47-132">Die **UsageLocation**-Eigenschaft ist nur eine von vielen Eigenschaften, die einem Benutzerkonto zugeordnet ist.</span><span class="sxs-lookup"><span data-stu-id="b8f47-132">The **UsageLocation** property is only one of many properties associated with a user account.</span></span> <span data-ttu-id="b8f47-133">Wenn Sie alle Eigenschaften für Benutzerkonten anzeigen möchten, verwenden Sie das Cmdlet **Select-Object** und das Platzhalterzeichen (\*), um Sie alle für ein bestimmtes Benutzerkonto anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="b8f47-133">To see all of the properties for user accounts, use the **Select-Object** cmdlet and the wildcard character (\*) to display them all for a specific user account.</span></span> <span data-ttu-id="b8f47-134">Hier ein Beispiel:</span><span class="sxs-lookup"><span data-stu-id="b8f47-134">Here is an example:</span></span>
  
```powershell
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

<span data-ttu-id="b8f47-p106">In dieser Liste steht das **City**-Objekt für den Namen einer Benutzerkontoeigenschaft. Dies bedeutet, dass Sie mit dem folgenden Befehl eine Liste aller Benutzerkonten für Benutzer, die in London leben, anzeigen können:</span><span class="sxs-lookup"><span data-stu-id="b8f47-p106">For example, from this list, **City** is the name of a user account property. This means you can use the following command to list all of the user accounts for users living in London:</span></span>
  
```powershell
Get-AzureADUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  <span data-ttu-id="b8f47-137">Die Syntax für das in diesen Beispielen gezeigte Cmdlet **Where-Object** ist **Where-Object\_{$.**</span><span class="sxs-lookup"><span data-stu-id="b8f47-137">The syntax for the **Where-Object** cmdlet shown in these examples is **Where-Object {$\_.**</span></span> <span data-ttu-id="b8f47-138">[Name der Benutzerkonten Eigenschaft] [Vergleichsoperator] Wert **}**. > [Vergleichsoperator] ist **-EQ** für gleich, **-ne** für ungleich, **-lt** für kleiner als, **-gt** für größer als und andere.</span><span class="sxs-lookup"><span data-stu-id="b8f47-138">[user account property name] [comparison operator] [value] **}**.>  [comparison operator] is **-eq** for equals, **-ne** for not equals, **-lt** for less than, **-gt** for greater than, and others.</span></span>  <span data-ttu-id="b8f47-139">[value] ist normalerweise eine Zeichenfolge (eine Sequenz von Buchstaben, Zahlen und anderen Zeichen), ein numerischer Wert oder **$null** für Unspecified> siehe [Where-Object](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Where-Object?view=powershell-5.1) , um weitere Informationen zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="b8f47-139">[value] is typically a string (a sequence of letters, numbers, and other characters), a numerical value, or **$Null** for unspecified>  See [Where-Object](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Where-Object?view=powershell-5.1) for more information.</span></span>
  

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="b8f47-140">Verwenden des Microsoft Azure Active Directory-Moduls für Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="b8f47-140">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="b8f47-141">Verbinden Sie sich zuerst [mit Ihrem Office 365-Mandanten](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="b8f47-141">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

### <a name="view-all-accounts"></a><span data-ttu-id="b8f47-142">Alle Konten anzeigen</span><span class="sxs-lookup"><span data-stu-id="b8f47-142">View all accounts</span></span>

<span data-ttu-id="b8f47-143">Um die vollständige Liste der Benutzerkonten anzuzeigen, führen Sie den folgenden Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="b8f47-143">To display the full list of user accounts, run this command:</span></span>
  
```powershell
Get-MsolUser
```

>[!Note]
><span data-ttu-id="b8f47-144">PowerShell Core unterstützt nicht das Microsoft Azure Active Directory-Modul für Windows PowerShell und Cmdlets mit **Msol** im Namen.</span><span class="sxs-lookup"><span data-stu-id="b8f47-144">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="b8f47-145">Um diese Cmdlets weiterhin verwenden zu können, müssen Sie sie über Windows PowerShell ausführen.</span><span class="sxs-lookup"><span data-stu-id="b8f47-145">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

<span data-ttu-id="b8f47-146">Es sollten Informationen ähnlich den folgenden angezeigt werden:</span><span class="sxs-lookup"><span data-stu-id="b8f47-146">You should see information similar to this:</span></span>
  
```powershell
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BonnieK@litwareinc.onmicrosoft.com    Bonnie Kearney        True
FabriceC@litwareinc.onmicrosoft.com   Fabrice Canel         True
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
AnneWlitwareinc.onmicrosoft.com       Anne Wallace          True
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

<span data-ttu-id="b8f47-147">Das **Get-MsolUser**-Cmdlet verfügt darüber hinaus über eine Reihe von Parametern zum Filtern der angezeigten Benutzerkonten.</span><span class="sxs-lookup"><span data-stu-id="b8f47-147">The **Get-MsolUser** cmdlet also has a set of parameters to filter the set of user accounts displayed.</span></span> <span data-ttu-id="b8f47-148">Führen Sie diesen Befehl beispielsweise für die Liste der nicht lizenzierten Benutzer (Benutzer, die Office 365 hinzugefügt wurden, aber noch nicht für die Verwendung eines der Dienste lizenziert wurden) aus.</span><span class="sxs-lookup"><span data-stu-id="b8f47-148">For example, for the list of unlicensed users (users who've been added to Office 365 but haven't yet been licensed to use any of the services), run this command.</span></span>
  
```powershell
Get-MsolUser -UnlicensedUsersOnly
```

<span data-ttu-id="b8f47-149">Es sollten Informationen ähnlich den folgenden angezeigt werden:</span><span class="sxs-lookup"><span data-stu-id="b8f47-149">You should see information similar to this:</span></span>
  
```powershell
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

<span data-ttu-id="b8f47-150">Weitere Informationen zu zusätzlichen Parametern zum Filtern des angezeigten Satzes von Benutzerkonten finden Sie unter [Get-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194133(v=azure.100)).</span><span class="sxs-lookup"><span data-stu-id="b8f47-150">For more information about additional parameters to filter the display the set of user accounts displayed, see [Get-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194133(v=azure.100)).</span></span>
  

### <a name="view-a-specific-account"></a><span data-ttu-id="b8f47-151">Anzeigen eines bestimmten Kontos</span><span class="sxs-lookup"><span data-stu-id="b8f47-151">View a specific account</span></span>

<span data-ttu-id="b8f47-152">Um ein bestimmtes Benutzerkonto anzuzeigen, geben Sie den Anmeldenamen des Benutzerkontos des Benutzerkontos ein, das auch als Benutzerprinzipalname (User Principal Name, UPN) bezeichnet wird, entfernen Sie die Zeichen "#a0" und "#a1", und führen Sie den folgenden Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="b8f47-152">To display a specific user account, fill in the sign-in name of the user account of the user account, also known as the user principal name (UPN), remove the "<" and ">" characters, and run this command:</span></span>
  
```powershell
Get-MsolUser -UserPrincipalName <sign-in name of the user account>
```

### <a name="view-some-accounts-based-on-a-common-property"></a><span data-ttu-id="b8f47-153">Anzeigen einiger Konten basierend auf einer gemeinsamen Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="b8f47-153">View some accounts based on a common property</span></span>

<span data-ttu-id="b8f47-154">Um die Liste der angezeigten Konten weiter einzugrenzen, können Sie die **Where-Object**- und **Get-MsolUser**-Cmdlets zusammen verwenden.</span><span class="sxs-lookup"><span data-stu-id="b8f47-154">To be more selective about the list of accounts to display, you can use the **Where-Object** cmdlet in combination with the **Get-MsolUser** cmdlet.</span></span> <span data-ttu-id="b8f47-155">Um die beiden Cmdlets zu kombinieren, verwenden wir das "Pipe"-Zeichen "|", das Office 365 PowerShell anweist, die Ergebnisse eines Befehls zu übernehmen und an den nächsten Befehl zu senden.</span><span class="sxs-lookup"><span data-stu-id="b8f47-155">To combine the two cmdlets, we use the "pipe" character "|", which tells Office 365 PowerShell to take the results of one command and send it to the next command.</span></span> <span data-ttu-id="b8f47-156">Nachfolgend ist ein Beispielbefehl aufgeführt, mit dem nur die Benutzerkonten angezeigt werden, die über einen nicht angegebenen Verwendungsstandort verfügen:</span><span class="sxs-lookup"><span data-stu-id="b8f47-156">Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```powershell
Get-MsolUser | Where-Object {$_.UsageLocation -eq $Null}
```

<span data-ttu-id="b8f47-157">Dieser Befehl weist Office 365 PowerShell zu folgenden Aktionen an:</span><span class="sxs-lookup"><span data-stu-id="b8f47-157">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="b8f47-158">Alle Informationen der Benutzerkonten abrufen (**Get-MsolUser**) und an den nächsten Befehl senden (**|**).</span><span class="sxs-lookup"><span data-stu-id="b8f47-158">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="b8f47-159">Hier finden Sie alle Benutzerkonten mit einem nicht angegebenen Verwendungs Speicherort ( **Where-Object {\_$. UsageLocation-EQ $NULL}** ).</span><span class="sxs-lookup"><span data-stu-id="b8f47-159">Find all of the user accounts that have an unspecified usage location ( **Where-Object {$\_.UsageLocation -eq $Null}** ).</span></span> <span data-ttu-id="b8f47-160">In den geschweiften Klammern weist der Befehl Office 365 PowerShell an, nur den kontensatz zu finden, in dem die UsageLocation-Benutzerkonto Eigenschaft ( \*\* $ \_. UsageLocation\*\* ) ist nicht angegeben ( **-EQ $NULL** ).</span><span class="sxs-lookup"><span data-stu-id="b8f47-160">Inside the braces, the command instructs Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
<span data-ttu-id="b8f47-161">Es sollten Informationen ähnlich den folgenden angezeigt werden:</span><span class="sxs-lookup"><span data-stu-id="b8f47-161">You should see information similar to this:</span></span>
  
```powershell
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False

```

<span data-ttu-id="b8f47-162">Die **UsageLocation**-Eigenschaft ist nur eine von vielen Eigenschaften, die einem Benutzerkonto zugeordnet ist.</span><span class="sxs-lookup"><span data-stu-id="b8f47-162">The **UsageLocation** property is only one of many properties associated with a user account.</span></span> <span data-ttu-id="b8f47-163">Wenn Sie alle Eigenschaften für Benutzerkonten anzeigen möchten, verwenden Sie das Cmdlet **Select-Object** und das Platzhalterzeichen (\*), um Sie alle für ein bestimmtes Benutzerkonto anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="b8f47-163">To see all of the properties for user accounts, use the **Select-Object** cmdlet and the wildcard character (\*) to display them all for a specific user account.</span></span> <span data-ttu-id="b8f47-164">Hier ein Beispiel:</span><span class="sxs-lookup"><span data-stu-id="b8f47-164">Here is an example:</span></span>
  
```powershell
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

<span data-ttu-id="b8f47-p113">In dieser Liste steht das **City**-Objekt für den Namen einer Benutzerkontoeigenschaft. Dies bedeutet, dass Sie mit dem folgenden Befehl eine Liste aller Benutzerkonten für Benutzer, die in London leben, anzeigen können:</span><span class="sxs-lookup"><span data-stu-id="b8f47-p113">For example, from this list, **City** is the name of a user account property. This means you can use the following command to list all of the user accounts for users living in London:</span></span>
  
```powershell
Get-MsolUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  <span data-ttu-id="b8f47-167">Die Syntax für das in diesen Beispielen gezeigte Cmdlet **Where-Object** ist **Where-Object\_{$.**</span><span class="sxs-lookup"><span data-stu-id="b8f47-167">The syntax for the **Where-Object** cmdlet shown in these examples is **Where-Object {$\_.**</span></span> <span data-ttu-id="b8f47-168">[Name der Benutzerkonten Eigenschaft] [Vergleichsoperator] Wert **}**.</span><span class="sxs-lookup"><span data-stu-id="b8f47-168">[user account property name] [comparison operator] [value] **}**.</span></span>  <span data-ttu-id="b8f47-169">[Vergleichsoperator] is **-EQ** für gleich, **-ne** für ungleich, **-lt** für kleiner als, **-gt** für größer als und andere.</span><span class="sxs-lookup"><span data-stu-id="b8f47-169">[comparison operator] is **-eq** for equals, **-ne** for not equals, **-lt** for less than, **-gt** for greater than, and others.</span></span>  <span data-ttu-id="b8f47-170">[value] ist normalerweise eine Zeichenfolge (eine Sequenz von Buchstaben, Zahlen und anderen Zeichen), ein numerischer Wert oder **$null** für Unspecified.</span><span class="sxs-lookup"><span data-stu-id="b8f47-170">[value] is typically a string (a sequence of letters, numbers, and other characters), a numerical value, or **$Null** for unspecified.</span></span> <span data-ttu-id="b8f47-171">Weitere Informationen finden Sie unter [Where-Object](https://technet.microsoft.com/library/hh849715.aspx) .</span><span class="sxs-lookup"><span data-stu-id="b8f47-171">See [Where-Object](https://technet.microsoft.com/library/hh849715.aspx) for more information.</span></span>
  
<span data-ttu-id="b8f47-172">Sie können den blockierten Status eines Benutzerkontos überprüfen, indem Sie den folgenden Befehl ausführen:</span><span class="sxs-lookup"><span data-stu-id="b8f47-172">You can check the blocked status of a user account with the following command:</span></span>
  
```powershell
Get-MsolUser -UserPrincipalName <UPN of user account> | Select-Object DisplayName,BlockCredential
```

### <a name="view-additional-property-values-for-accounts"></a><span data-ttu-id="b8f47-173">Anzeigen zusätzlicher Eigenschaftswerte für Konten</span><span class="sxs-lookup"><span data-stu-id="b8f47-173">View additional property values for accounts</span></span>

<span data-ttu-id="b8f47-174">Das Cmdlet **Get-MsolUser** zeigt standardmäßig drei Eigenschaften von Benutzerkonten an:</span><span class="sxs-lookup"><span data-stu-id="b8f47-174">The **Get-MsolUser** cmdlet by default displays three properties of user accounts:</span></span>
  
- <span data-ttu-id="b8f47-175">UserPrincipalName</span><span class="sxs-lookup"><span data-stu-id="b8f47-175">UserPrincipalName</span></span>
    
- <span data-ttu-id="b8f47-176">DisplayName</span><span class="sxs-lookup"><span data-stu-id="b8f47-176">DisplayName</span></span>
    
- <span data-ttu-id="b8f47-177">isLicensed</span><span class="sxs-lookup"><span data-stu-id="b8f47-177">isLicensed</span></span>
    
<span data-ttu-id="b8f47-178">Wenn Sie zusätzliche Eigenschaften benötigen, beispielsweise die Abteilung, für die der Benutzer arbeitet, und das Land/die Region, in der der Benutzer Office 365 Dienste verwendet, können Sie **Get-MsolUser** in Kombination mit dem Cmdlet **Select-Object** ausführen, um die Liste der Benutzerkontoeigenschaften anzugeben.</span><span class="sxs-lookup"><span data-stu-id="b8f47-178">If you need additional properties, such as the department the user works for and the country/region where the user uses Office 365 services, you can run **Get-MsolUser** in combination with the **Select-Object** cmdlet to specify the list of user account properties.</span></span> <span data-ttu-id="b8f47-179">Es folgt ein Beispiel:</span><span class="sxs-lookup"><span data-stu-id="b8f47-179">Here is an example:</span></span>
  
```powershell
Get-MsolUser | Select-Object DisplayName, Department, UsageLocation
```

<span data-ttu-id="b8f47-180">Dieser Befehl weist Office 365 PowerShell zu folgenden Aktionen an:</span><span class="sxs-lookup"><span data-stu-id="b8f47-180">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="b8f47-181">Alle Informationen der Benutzerkonten abrufen (**Get-MsolUser**) und an den nächsten Befehl senden (**|**).</span><span class="sxs-lookup"><span data-stu-id="b8f47-181">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="b8f47-182">Nur den Namen des Benutzerkontos, die Abteilung und den Verwendungs Speicherort anzeigen ( **Select-Object DisplayName, Department, UsageLocation** ).</span><span class="sxs-lookup"><span data-stu-id="b8f47-182">Display only the user account name, department, and usage location ( **Select-Object DisplayName, Department, UsageLocation** ).</span></span>
    
<span data-ttu-id="b8f47-183">Es sollten Informationen ähnlich den folgenden angezeigt werden:</span><span class="sxs-lookup"><span data-stu-id="b8f47-183">You should see information similar to this:</span></span>
  
```powershell
DisplayName             Department                       UsageLocation
-----------             ----------                       -------------
Bonnie Kearney          Sales & Marketing                    US
Fabrice Canel           Legal                                US
Brian Johnson
Anne Wallace            Executive Management                 US
Alex Darrow             Sales & Marketing                    US
Scott Wallace           Operations
```

<span data-ttu-id="b8f47-184">Mit dem Cmdlet **"Select-Object** " können Sie die Eigenschaften auswählen, die ein Befehl angezeigt werden soll.</span><span class="sxs-lookup"><span data-stu-id="b8f47-184">The **Select-Object** cmdlet lets you pick and choose the properties you want a command to display.</span></span> <span data-ttu-id="b8f47-185">Wenn Sie alle Eigenschaften für Benutzerkonten anzeigen möchten, verwenden Sie das Platzhalterzeichen (\*), um Sie alle für ein bestimmtes Benutzerkonto anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="b8f47-185">To see all of the properties for user accounts, use the wildcard character (\*) to display them all for a specific user account.</span></span> <span data-ttu-id="b8f47-186">Es folgt ein Beispiel:</span><span class="sxs-lookup"><span data-stu-id="b8f47-186">Here is an example:</span></span>
  
```powershell
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

<span data-ttu-id="b8f47-p117">Um die Liste der anzuzeigenden Konten noch weiter einzuschränken, können Sie auch das **Where-Object**-Cmdlet verwenden. Nachfolgend ist ein Beispielbefehl aufgeführt, mit dem nur die Benutzerkonten angezeigt werden, die über einen nicht angegebenen Verwendungsstandort verfügen:</span><span class="sxs-lookup"><span data-stu-id="b8f47-p117">To be more selective about the list of accounts to display, you can also use the **Where-Object** cmdlet. Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```powershell
Get-MsolUser | Where-Object {$_.UsageLocation -eq $Null} | Select-Object DisplayName, Department, UsageLocation
```

<span data-ttu-id="b8f47-189">Dieser Befehl weist Office 365 PowerShell zu folgenden Aktionen an:</span><span class="sxs-lookup"><span data-stu-id="b8f47-189">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="b8f47-190">Alle Informationen der Benutzerkonten abrufen (**Get-MsolUser**) und an den nächsten Befehl senden (**|**).</span><span class="sxs-lookup"><span data-stu-id="b8f47-190">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="b8f47-191">Hier finden Sie alle Benutzerkonten mit einem nicht angegebenen Verwendungs Speicherort ( **Where-Object {\_$. UsageLocation-EQ $NULL}** ) und die resultierenden Informationen an den nächsten Befehl senden **|** ().</span><span class="sxs-lookup"><span data-stu-id="b8f47-191">Find all of the user accounts that have an unspecified usage location ( **Where-Object {$\_.UsageLocation -eq $Null}** ) and send the resulting information to the next command ( **|** ).</span></span> <span data-ttu-id="b8f47-192">In den geschweiften Klammern weist der Befehl Office 365 PowerShell an, nur den kontensatz zu finden, in dem die UsageLocation-Benutzerkonto Eigenschaft ( \*\* $ \_. UsageLocation\*\* ) ist nicht angegeben ( **-EQ $NULL** ).</span><span class="sxs-lookup"><span data-stu-id="b8f47-192">Inside the braces, the command is instructing Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
- <span data-ttu-id="b8f47-193">Nur den Namen des Benutzerkontos, die Abteilung und den Verwendungs Speicherort anzeigen ( **Select-Object DisplayName, Department, UsageLocation** ).</span><span class="sxs-lookup"><span data-stu-id="b8f47-193">Display only the user account name, department, and usage location ( **Select-Object DisplayName, Department, UsageLocation** ).</span></span>
    
<span data-ttu-id="b8f47-194">Es sollten Informationen ähnlich den folgenden angezeigt werden:</span><span class="sxs-lookup"><span data-stu-id="b8f47-194">You should see information similar to this:</span></span>
  
```powershell
DisplayName              Department                      UsageLocation
-----------              ----------                      -------------
Brian Johnson 
Scott Wallace            Operations
```

<span data-ttu-id="b8f47-195">Wenn Sie die Verzeichnissynchronisierung zum Erstellen und Verwalten Ihrer Office 365-Benutzer verwenden, können Sie das lokale Konto anzeigen, aus dem ein Office 365 Benutzer projiziert wurde.</span><span class="sxs-lookup"><span data-stu-id="b8f47-195">If you are using directory synchronization to create and manage your Office 365 users, you can display which local account an Office 365 user has been projected from.</span></span> <span data-ttu-id="b8f47-196">Im folgenden wird davon ausgegangen, dass Azure AD Connect für die Verwendung des Standard Quell Ankers von objectGUID konfiguriert ist (Weitere Informationen zum Konfigurieren eines Quell Ankers finden Sie unter [Azure AD Connect: Design Concepts](https://docs.microsoft.com/azure/active-directory/hybrid/plan-connect-design-concepts)), und es wird davon ausgegangen, dass das Active Directory Modul für PowerShell installiert wurde (siehe Tools für die [Remoteverwaltung](https://www.microsoft.com/en-gb/download/details.aspx?id=45520)):</span><span class="sxs-lookup"><span data-stu-id="b8f47-196">The following assumes that Azure AD Connect has been configured to use the default source anchor of ObjectGUID (for more on configuring a source anchor, see [Azure AD Connect: Design concepts](https://docs.microsoft.com/azure/active-directory/hybrid/plan-connect-design-concepts)) and assumes that the Active Directory module for powershell has been installed (see [RSAT tools](https://www.microsoft.com/en-gb/download/details.aspx?id=45520)):</span></span>

```powershell
Get-ADUser ([guid][System.Convert]::FromBase64String((Get-MsolUser -UserPrincipalName <UPN of user account>).ImmutableID)).guid
```

    
## <a name="see-also"></a><span data-ttu-id="b8f47-197">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="b8f47-197">See also</span></span>

[<span data-ttu-id="b8f47-198">Verwalten von Benutzerkonten und Lizenzen mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="b8f47-198">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="b8f47-199">Verwalten von Office 365 mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="b8f47-199">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="b8f47-200">Erste Schritte mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="b8f47-200">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

