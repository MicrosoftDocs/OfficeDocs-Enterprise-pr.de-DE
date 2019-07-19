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
ms.openlocfilehash: c23e9106873aa32e8daccb1e35a16862e6f9bb7d
ms.sourcegitcommit: 1c97471f47e1869f6db684f280f9085b7c2ff59f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/18/2019
ms.locfileid: "35782065"
---
# <a name="view-user-accounts-with-office-365-powershell"></a><span data-ttu-id="85bbb-103">Anzeigen von Benutzerkonten mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="85bbb-103">View user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="85bbb-104">**Zusammenfassung:** Zeigen Sie Ihre Benutzerkonten mit Office 365 PowerShell auf verschiedene Arten an.</span><span class="sxs-lookup"><span data-stu-id="85bbb-104">**Summary:** View your user accounts in various ways with Office 365 PowerShell.</span></span>
  
<span data-ttu-id="85bbb-105">Sie können zwar das Microsoft 365 Admin Center verwenden, um die Konten für Ihren Office 365 Mandanten anzuzeigen, aber Sie können auch Office 365 PowerShell verwenden und einige Dinge tun, die das Admin Center nicht kann.</span><span class="sxs-lookup"><span data-stu-id="85bbb-105">Although you can use the Microsoft 365 admin center to view the accounts for your Office 365 tenant, you can also use Office 365 PowerShell and do some things that the admin center cannot.</span></span>
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="85bbb-106">Verwenden der Azure Active Directory PowerShell für Graph-Module</span><span class="sxs-lookup"><span data-stu-id="85bbb-106">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="85bbb-107">Verbinden Sie sich zuerst [mit Ihrem Office 365-Mandanten](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="85bbb-107">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  
### <a name="view-all-accounts"></a><span data-ttu-id="85bbb-108">Alle Konten anzeigen</span><span class="sxs-lookup"><span data-stu-id="85bbb-108">View all accounts</span></span>

<span data-ttu-id="85bbb-109">Um die vollständige Liste der Benutzerkonten anzuzeigen, führen Sie den folgenden Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="85bbb-109">To display the full list of user accounts, run this command:</span></span>
  
```
Get-AzureADUser
```

<span data-ttu-id="85bbb-110">Es sollten Informationen ähnlich den folgenden angezeigt werden:</span><span class="sxs-lookup"><span data-stu-id="85bbb-110">You should see information similar to this:</span></span>
  
```
ObjectId                             DisplayName                                           UserPrincipalName
--------                             -----------                                           -----------------
032fc1fc-b5a2-46f1-8635-3d7dcb52c48d Adele Vance                                           AdeleV@litwareinc.OnMicr...
bd1e6af1-41e7-4f77-a2ac-5b209950135c Global Administrator                                  admin@litwareinc.onmicro...
ec37a4d6-232e-4eb7-82a5-1613490642a5 Alex Wilber                                           AlexW@litwareinc.OnMicro...
be4bdddd-c790-424c-9f96-a0cf609b7815 Allan Deyoung                                         AllanD@litwareinc.OnMicr...
598ab87b-76f0-4bf9-9538-bd46b10f4438 Christie Cline                                        ChristieC@litwareinc.OnM...
40722671-e520-4a5f-97d4-0bc9e9b2dc0f Debra Berger                                          DebraB@litwareinc.OnMicr...
```

### <a name="view-a-specific-account"></a><span data-ttu-id="85bbb-111">Anzeigen eines bestimmten Kontos</span><span class="sxs-lookup"><span data-stu-id="85bbb-111">View a specific account</span></span>

<span data-ttu-id="85bbb-112">Um ein bestimmtes Benutzerkonto anzuzeigen, geben Sie den Anmeldekontonamen des Benutzerkontos ein, das auch als Benutzerprinzipalname (User Principal Name, UPN) bezeichnet wird, entfernen Sie die Zeichen "#a0" und "#a1", und führen Sie den folgenden Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="85bbb-112">To display a specific user account, fill in the sign-in account name of the user account, also known as the user principal name (UPN), remove the "<" and ">" characters, and run this command:</span></span>
  
```
Get-AzureADUser -ObjectID <sign-in name of the user account>
```

<span data-ttu-id="85bbb-113">Es folgt ein Beispiel:</span><span class="sxs-lookup"><span data-stu-id="85bbb-113">Here is an example:</span></span>
  
```
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com
```

### <a name="view-additional-property-values-for-a-specific-account"></a><span data-ttu-id="85bbb-114">Anzeigen zusätzlicher Eigenschaftswerte für ein bestimmtes Konto</span><span class="sxs-lookup"><span data-stu-id="85bbb-114">View additional property values for a specific account</span></span>

<span data-ttu-id="85bbb-115">Standardmäßig zeigt das Cmdlet **Get-AzureADUser** nur die Eigenschaften ObjectID, DisplayName und userPrincipalName von Konten an.</span><span class="sxs-lookup"><span data-stu-id="85bbb-115">By default, the **Get-AzureADUser** cmdlet only displays the ObjectID, DisplayName, and UserPrincipalName properties of accounts.</span></span>

<span data-ttu-id="85bbb-116">Um die Liste der anzuzeigenden Eigenschaften selektiver zu machen, können Sie das Cmdlet **Select-Object** in Kombination mit dem Cmdlet **Get-AzureADUser** verwenden.</span><span class="sxs-lookup"><span data-stu-id="85bbb-116">To be more selective about the list of properties to display, you can use the **Select-Object** cmdlet in combination with the **Get-AzureADUser** cmdlet.</span></span> <span data-ttu-id="85bbb-117">Um die beiden Cmdlets zu kombinieren, verwenden wir das "Pipe"-Zeichen "|", das Azure Active Directory PowerShell für Graph anweist, die Ergebnisse eines Befehls zu übernehmen und an den nächsten Befehl zu senden.</span><span class="sxs-lookup"><span data-stu-id="85bbb-117">To combine the two cmdlets, we use the "pipe" character "|", which tells Azure Active Directory PowerShell for Graph to take the results of one command and send it to the next command.</span></span> <span data-ttu-id="85bbb-118">Es folgt ein Beispielbefehl, mit dem DisplayName, Department und UsageLocation für jedes Benutzerkonto angezeigt werden:</span><span class="sxs-lookup"><span data-stu-id="85bbb-118">Here is an example command that displays the DisplayName, Department, and UsageLocation for every user account:</span></span>
  
```
Get-AzureADUser | Select-Object DisplayName,Department,UsageLocation
```

<span data-ttu-id="85bbb-119">Dieser Befehl gibt Office 365 Powershell die folgenden Anweisungen:</span><span class="sxs-lookup"><span data-stu-id="85bbb-119">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="85bbb-120">Alle Informationen der Benutzerkonten abrufen (**Get-AzureADUser**) und an den nächsten Befehl senden (**|**).</span><span class="sxs-lookup"><span data-stu-id="85bbb-120">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="85bbb-121">Nur den Namen des Benutzerkontos, die Abteilung und den Verwendungs Speicherort anzeigen ( **Select-Object DisplayName, Department, UsageLocation** ).</span><span class="sxs-lookup"><span data-stu-id="85bbb-121">Display only the user account name, department, and usage location ( **Select-Object DisplayName, Department, UsageLocation** ).</span></span>
  
<span data-ttu-id="85bbb-122">Wenn Sie alle Eigenschaften für Benutzerkonten anzeigen möchten, verwenden Sie das Cmdlet **Select-Object** und das Platzhalterzeichen (\*), um Sie alle für ein bestimmtes Benutzerkonto anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="85bbb-122">To see all of the properties for user accounts, use the **Select-Object** cmdlet and the wildcard character (\*) to display them all for a specific user account.</span></span> <span data-ttu-id="85bbb-123">Es folgt ein Beispiel:</span><span class="sxs-lookup"><span data-stu-id="85bbb-123">Here is an example:</span></span>
  
```
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

<span data-ttu-id="85bbb-124">Als weiteres Beispiel können Sie den aktivierten Status eines bestimmten Benutzerkontos überprüfen, indem Sie den folgenden Befehl ausführen:</span><span class="sxs-lookup"><span data-stu-id="85bbb-124">As another example, you can check the enabled status of a specific user account with the following command:</span></span>
  
```
Get-AzureADUser -ObjectID <sign-in name of the user account> | Select-Object DisplayName,UserPrincipalName,AccountEnabled
```

### <a name="view-some-accounts-based-on-a-common-property"></a><span data-ttu-id="85bbb-125">Anzeigen einiger Konten basierend auf einer gemeinsamen Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="85bbb-125">View some accounts based on a common property</span></span>

<span data-ttu-id="85bbb-126">Um die Liste der angezeigten Konten weiter einzugrenzen, können Sie die **Where-Object**- und **Get-AzureADUser**-Cmdlets zusammen verwenden.</span><span class="sxs-lookup"><span data-stu-id="85bbb-126">To be more selective about the list of accounts to display, you can use the **Where-Object** cmdlet in combination with the **Get-AzureADUser** cmdlet.</span></span> <span data-ttu-id="85bbb-127">Um die beiden Cmdlets zu kombinieren, verwenden wir das "Pipe"-Zeichen "|", das Azure Active Directory PowerShell für Graph anweist, die Ergebnisse eines Befehls zu übernehmen und an den nächsten Befehl zu senden.</span><span class="sxs-lookup"><span data-stu-id="85bbb-127">To combine the two cmdlets, we use the "pipe" character "|", which tells Azure Active Directory PowerShell for Graph to take the results of one command and send it to the next command.</span></span> <span data-ttu-id="85bbb-128">Nachfolgend ist ein Beispielbefehl aufgeführt, mit dem nur die Benutzerkonten angezeigt werden, die über einen nicht angegebenen Verwendungsstandort verfügen:</span><span class="sxs-lookup"><span data-stu-id="85bbb-128">Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```
Get-AzureADUser | Where-Object {$_.UsageLocation -eq $Null}
```

<span data-ttu-id="85bbb-129">Dieser Befehl weist Azure Active Directory PowerShell für Graph Folgendes zu:</span><span class="sxs-lookup"><span data-stu-id="85bbb-129">This command instructs Azure Active Directory PowerShell for Graph to:</span></span>
  
- <span data-ttu-id="85bbb-130">Alle Informationen der Benutzerkonten abrufen (**Get-AzureADUser**) und an den nächsten Befehl senden (**|**).</span><span class="sxs-lookup"><span data-stu-id="85bbb-130">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="85bbb-131">Hier finden Sie alle Benutzerkonten mit einem nicht angegebenen Verwendungs Speicherort ( **Where-Object {\_$. UsageLocation-EQ $NULL}** ).</span><span class="sxs-lookup"><span data-stu-id="85bbb-131">Find all of the user accounts that have an unspecified usage location ( **Where-Object {$\_.UsageLocation -eq $Null}** ).</span></span> <span data-ttu-id="85bbb-132">In den geschweiften Klammern weist der Befehl Office 365 PowerShell an, nur den kontensatz zu finden, in dem die UsageLocation-Benutzerkonto Eigenschaft ( \*\* $ \_. UsageLocation\*\* ) ist nicht angegeben ( **-EQ $NULL** ).</span><span class="sxs-lookup"><span data-stu-id="85bbb-132">Inside the braces, the command instructs Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
<span data-ttu-id="85bbb-133">Die **UsageLocation**-Eigenschaft ist nur eine von vielen Eigenschaften, die einem Benutzerkonto zugeordnet ist.</span><span class="sxs-lookup"><span data-stu-id="85bbb-133">The **UsageLocation** property is only one of many properties associated with a user account.</span></span> <span data-ttu-id="85bbb-134">Wenn Sie alle Eigenschaften für Benutzerkonten anzeigen möchten, verwenden Sie das Cmdlet **Select-Object** und das Platzhalterzeichen (\*), um Sie alle für ein bestimmtes Benutzerkonto anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="85bbb-134">To see all of the properties for user accounts, use the **Select-Object** cmdlet and the wildcard character (\*) to display them all for a specific user account.</span></span> <span data-ttu-id="85bbb-135">Hier ein Beispiel:</span><span class="sxs-lookup"><span data-stu-id="85bbb-135">Here is an example:</span></span>
  
```
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

<span data-ttu-id="85bbb-p106">In dieser Liste steht das **City**-Objekt für den Namen einer Benutzerkontoeigenschaft. Dies bedeutet, dass Sie mit dem folgenden Befehl eine Liste aller Benutzerkonten für Benutzer, die in London leben, anzeigen können:</span><span class="sxs-lookup"><span data-stu-id="85bbb-p106">For example, from this list, **City** is the name of a user account property. This means you can use the following command to list all of the user accounts for users living in London:</span></span>
  
```
Get-AzureADUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  <span data-ttu-id="85bbb-138">Die Syntax für das in diesen Beispielen gezeigte Cmdlet **Where-Object** ist **Where-Object\_{$.**</span><span class="sxs-lookup"><span data-stu-id="85bbb-138">The syntax for the **Where-Object** cmdlet shown in these examples is **Where-Object {$\_.**</span></span> <span data-ttu-id="85bbb-139">[Name der Benutzerkonten Eigenschaft] [Vergleichsoperator] Wert **}**. > [Vergleichsoperator] ist **-EQ** für gleich, **-ne** für ungleich, **-lt** für kleiner als, **-gt** für größer als und andere.</span><span class="sxs-lookup"><span data-stu-id="85bbb-139">[user account property name] [comparison operator] [value] **}**.>  [comparison operator] is **-eq** for equals, **-ne** for not equals, **-lt** for less than, **-gt** for greater than, and others.</span></span>  <span data-ttu-id="85bbb-140">[value] ist normalerweise eine Zeichenfolge (eine Sequenz von Buchstaben, Zahlen und anderen Zeichen), ein numerischer Wert oder **$null** für Unspecified> siehe [Where-Object](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Where-Object?view=powershell-5.1) , um weitere Informationen zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="85bbb-140">[value] is typically a string (a sequence of letters, numbers, and other characters), a numerical value, or **$Null** for unspecified>  See [Where-Object](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Where-Object?view=powershell-5.1) for more information.</span></span>
  

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="85bbb-141">Verwenden des Microsoft Azure Active Directory-Moduls für Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="85bbb-141">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="85bbb-142">Verbinden Sie sich zuerst [mit Ihrem Office 365-Mandanten](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="85bbb-142">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

### <a name="view-all-accounts"></a><span data-ttu-id="85bbb-143">Alle Konten anzeigen</span><span class="sxs-lookup"><span data-stu-id="85bbb-143">View all accounts</span></span>

<span data-ttu-id="85bbb-144">Um die vollständige Liste der Benutzerkonten anzuzeigen, führen Sie den folgenden Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="85bbb-144">To display the full list of user accounts, run this command:</span></span>
  
```
Get-MsolUser
```

<span data-ttu-id="85bbb-145">Es sollten Informationen ähnlich den folgenden angezeigt werden:</span><span class="sxs-lookup"><span data-stu-id="85bbb-145">You should see information similar to this:</span></span>
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BonnieK@litwareinc.onmicrosoft.com    Bonnie Kearney        True
FabriceC@litwareinc.onmicrosoft.com   Fabrice Canel         True
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
AnneWlitwareinc.onmicrosoft.com       Anne Wallace          True
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

<span data-ttu-id="85bbb-146">Das **Get-MsolUser**-Cmdlet verfügt darüber hinaus über eine Reihe von Parametern zum Filtern der angezeigten Benutzerkonten.</span><span class="sxs-lookup"><span data-stu-id="85bbb-146">The **Get-MsolUser** cmdlet also has a set of parameters to filter the set of user accounts displayed.</span></span> <span data-ttu-id="85bbb-147">Führen Sie diesen Befehl beispielsweise für die Liste der nicht lizenzierten Benutzer (Benutzer, die Office 365 hinzugefügt wurden, aber noch nicht für die Verwendung eines der Dienste lizenziert wurden) aus.</span><span class="sxs-lookup"><span data-stu-id="85bbb-147">For example, for the list of unlicensed users (users who've been added to Office 365 but haven't yet been licensed to use any of the services), run this command.</span></span>
  
```
Get-MsolUser -UnlicensedUsersOnly
```

<span data-ttu-id="85bbb-148">Es sollten Informationen ähnlich den folgenden angezeigt werden:</span><span class="sxs-lookup"><span data-stu-id="85bbb-148">You should see information similar to this:</span></span>
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

<span data-ttu-id="85bbb-149">Weitere Informationen zu zusätzlichen Parametern zum Filtern des angezeigten Satzes von Benutzerkonten finden Sie unter [Get-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194133(v=azure.100)).</span><span class="sxs-lookup"><span data-stu-id="85bbb-149">For more information about additional parameters to filter the display the set of user accounts displayed, see [Get-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194133(v=azure.100)).</span></span>
  

### <a name="view-a-specific-account"></a><span data-ttu-id="85bbb-150">Anzeigen eines bestimmten Kontos</span><span class="sxs-lookup"><span data-stu-id="85bbb-150">View a specific account</span></span>

<span data-ttu-id="85bbb-151">Um ein bestimmtes Benutzerkonto anzuzeigen, geben Sie den Anmeldenamen des Benutzerkontos des Benutzerkontos ein, das auch als Benutzerprinzipalname (User Principal Name, UPN) bezeichnet wird, entfernen Sie die Zeichen "#a0" und "#a1", und führen Sie den folgenden Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="85bbb-151">To display a specific user account, fill in the sign-in name of the user account of the user account, also known as the user principal name (UPN), remove the "<" and ">" characters, and run this command:</span></span>
  
```
Get-MsolUser -UserPrincipalName <sign-in name of the user account>
```

### <a name="view-some-accounts-based-on-a-common-property"></a><span data-ttu-id="85bbb-152">Anzeigen einiger Konten basierend auf einer gemeinsamen Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="85bbb-152">View some accounts based on a common property</span></span>

<span data-ttu-id="85bbb-153">Um die Liste der angezeigten Konten weiter einzugrenzen, können Sie die **Where-Object**- und **Get-MsolUser**-Cmdlets zusammen verwenden.</span><span class="sxs-lookup"><span data-stu-id="85bbb-153">To be more selective about the list of accounts to display, you can use the **Where-Object** cmdlet in combination with the **Get-MsolUser** cmdlet.</span></span> <span data-ttu-id="85bbb-154">Um die beiden Cmdlets zu kombinieren, verwenden wir das "Pipe"-Zeichen "|", das Office 365 PowerShell anweist, die Ergebnisse eines Befehls zu übernehmen und an den nächsten Befehl zu senden.</span><span class="sxs-lookup"><span data-stu-id="85bbb-154">To combine the two cmdlets, we use the "pipe" character "|", which tells Office 365 PowerShell to take the results of one command and send it to the next command.</span></span> <span data-ttu-id="85bbb-155">Nachfolgend ist ein Beispielbefehl aufgeführt, mit dem nur die Benutzerkonten angezeigt werden, die über einen nicht angegebenen Verwendungsstandort verfügen:</span><span class="sxs-lookup"><span data-stu-id="85bbb-155">Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```
Get-MsolUser | Where-Object {$_.UsageLocation -eq $Null}
```

<span data-ttu-id="85bbb-156">Dieser Befehl weist Office 365 PowerShell zu folgenden Aktionen an:</span><span class="sxs-lookup"><span data-stu-id="85bbb-156">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="85bbb-157">Alle Informationen der Benutzerkonten abrufen (**Get-MsolUser**) und an den nächsten Befehl senden (**|**).</span><span class="sxs-lookup"><span data-stu-id="85bbb-157">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="85bbb-158">Hier finden Sie alle Benutzerkonten mit einem nicht angegebenen Verwendungs Speicherort ( **Where-Object {\_$. UsageLocation-EQ $NULL}** ).</span><span class="sxs-lookup"><span data-stu-id="85bbb-158">Find all of the user accounts that have an unspecified usage location ( **Where-Object {$\_.UsageLocation -eq $Null}** ).</span></span> <span data-ttu-id="85bbb-159">In den geschweiften Klammern weist der Befehl Office 365 PowerShell an, nur den kontensatz zu finden, in dem die UsageLocation-Benutzerkonto Eigenschaft ( \*\* $ \_. UsageLocation\*\* ) ist nicht angegeben ( **-EQ $NULL** ).</span><span class="sxs-lookup"><span data-stu-id="85bbb-159">Inside the braces, the command instructs Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
<span data-ttu-id="85bbb-160">Es sollten Informationen ähnlich den folgenden angezeigt werden:</span><span class="sxs-lookup"><span data-stu-id="85bbb-160">You should see information similar to this:</span></span>
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False

```

<span data-ttu-id="85bbb-161">Die **UsageLocation**-Eigenschaft ist nur eine von vielen Eigenschaften, die einem Benutzerkonto zugeordnet ist.</span><span class="sxs-lookup"><span data-stu-id="85bbb-161">The **UsageLocation** property is only one of many properties associated with a user account.</span></span> <span data-ttu-id="85bbb-162">Wenn Sie alle Eigenschaften für Benutzerkonten anzeigen möchten, verwenden Sie das Cmdlet **Select-Object** und das Platzhalterzeichen (\*), um Sie alle für ein bestimmtes Benutzerkonto anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="85bbb-162">To see all of the properties for user accounts, use the **Select-Object** cmdlet and the wildcard character (\*) to display them all for a specific user account.</span></span> <span data-ttu-id="85bbb-163">Hier ein Beispiel:</span><span class="sxs-lookup"><span data-stu-id="85bbb-163">Here is an example:</span></span>
  
```
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

<span data-ttu-id="85bbb-p112">In dieser Liste steht das **City**-Objekt für den Namen einer Benutzerkontoeigenschaft. Dies bedeutet, dass Sie mit dem folgenden Befehl eine Liste aller Benutzerkonten für Benutzer, die in London leben, anzeigen können:</span><span class="sxs-lookup"><span data-stu-id="85bbb-p112">For example, from this list, **City** is the name of a user account property. This means you can use the following command to list all of the user accounts for users living in London:</span></span>
  
```
Get-MsolUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  <span data-ttu-id="85bbb-166">Die Syntax für das in diesen Beispielen gezeigte Cmdlet **Where-Object** ist **Where-Object\_{$.**</span><span class="sxs-lookup"><span data-stu-id="85bbb-166">The syntax for the **Where-Object** cmdlet shown in these examples is **Where-Object {$\_.**</span></span> <span data-ttu-id="85bbb-167">[Name der Benutzerkonten Eigenschaft] [Vergleichsoperator] Wert **}**.</span><span class="sxs-lookup"><span data-stu-id="85bbb-167">[user account property name] [comparison operator] [value] **}**.</span></span>  <span data-ttu-id="85bbb-168">[Vergleichsoperator] is **-EQ** für gleich, **-ne** für ungleich, **-lt** für kleiner als, **-gt** für größer als und andere.</span><span class="sxs-lookup"><span data-stu-id="85bbb-168">[comparison operator] is **-eq** for equals, **-ne** for not equals, **-lt** for less than, **-gt** for greater than, and others.</span></span>  <span data-ttu-id="85bbb-169">[value] ist normalerweise eine Zeichenfolge (eine Sequenz von Buchstaben, Zahlen und anderen Zeichen), ein numerischer Wert oder **$null** für Unspecified.</span><span class="sxs-lookup"><span data-stu-id="85bbb-169">[value] is typically a string (a sequence of letters, numbers, and other characters), a numerical value, or **$Null** for unspecified.</span></span> <span data-ttu-id="85bbb-170">Weitere Informationen finden Sie unter [Where-Object](https://technet.microsoft.com/en-us/library/hh849715.aspx) .</span><span class="sxs-lookup"><span data-stu-id="85bbb-170">See [Where-Object](https://technet.microsoft.com/en-us/library/hh849715.aspx) for more information.</span></span>
  
<span data-ttu-id="85bbb-171">Sie können den blockierten Status eines Benutzerkontos überprüfen, indem Sie den folgenden Befehl ausführen:</span><span class="sxs-lookup"><span data-stu-id="85bbb-171">You can check the blocked status of a user account with the following command:</span></span>
  
```
Get-MsolUser -UserPrincipalName <UPN of user account> | Select-Object DisplayName,BlockCredential
```

### <a name="view-additional-property-values-for-accounts"></a><span data-ttu-id="85bbb-172">Anzeigen zusätzlicher Eigenschaftswerte für Konten</span><span class="sxs-lookup"><span data-stu-id="85bbb-172">View additional property values for accounts</span></span>

<span data-ttu-id="85bbb-173">Das Cmdlet **Get-MsolUser** zeigt standardmäßig drei Eigenschaften von Benutzerkonten an:</span><span class="sxs-lookup"><span data-stu-id="85bbb-173">The **Get-MsolUser** cmdlet by default displays three properties of user accounts:</span></span>
  
- <span data-ttu-id="85bbb-174">UserPrincipalName</span><span class="sxs-lookup"><span data-stu-id="85bbb-174">UserPrincipalName</span></span>
    
- <span data-ttu-id="85bbb-175">DisplayName</span><span class="sxs-lookup"><span data-stu-id="85bbb-175">DisplayName</span></span>
    
- <span data-ttu-id="85bbb-176">isLicensed</span><span class="sxs-lookup"><span data-stu-id="85bbb-176">isLicensed</span></span>
    
<span data-ttu-id="85bbb-177">Wenn Sie zusätzliche Eigenschaften benötigen, beispielsweise die Abteilung, für die der Benutzer arbeitet, und das Land/die Region, in der der Benutzer Office 365 Dienste verwendet, können Sie **Get-MsolUser** in Kombination mit dem Cmdlet **Select-Object** ausführen, um die Liste des Benutzerkontos anzugeben. Eigenschaften.</span><span class="sxs-lookup"><span data-stu-id="85bbb-177">If you need additional properties, such as the department the user works for and the country/region where the user uses Office 365 services, you can run **Get-MsolUser** in combination with the **Select-Object** cmdlet to specify the list of user account properties.</span></span> <span data-ttu-id="85bbb-178">Es folgt ein Beispiel:</span><span class="sxs-lookup"><span data-stu-id="85bbb-178">Here is an example:</span></span>
  
```
Get-MsolUser | Select-Object DisplayName, Department, UsageLocation
```

<span data-ttu-id="85bbb-179">Dieser Befehl weist Office 365 PowerShell zu folgenden Aktionen an:</span><span class="sxs-lookup"><span data-stu-id="85bbb-179">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="85bbb-180">Alle Informationen der Benutzerkonten abrufen (**Get-MsolUser**) und an den nächsten Befehl senden (**|**).</span><span class="sxs-lookup"><span data-stu-id="85bbb-180">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="85bbb-181">Nur den Namen des Benutzerkontos, die Abteilung und den Verwendungs Speicherort anzeigen ( **Select-Object DisplayName, Department, UsageLocation** ).</span><span class="sxs-lookup"><span data-stu-id="85bbb-181">Display only the user account name, department, and usage location ( **Select-Object DisplayName, Department, UsageLocation** ).</span></span>
    
<span data-ttu-id="85bbb-182">Es sollten Informationen ähnlich den folgenden angezeigt werden:</span><span class="sxs-lookup"><span data-stu-id="85bbb-182">You should see information similar to this:</span></span>
  
```
DisplayName             Department                       UsageLocation
-----------             ----------                       -------------
Bonnie Kearney          Sales & Marketing                    US
Fabrice Canel           Legal                                US
Brian Johnson
Anne Wallace            Executive Management                 US
Alex Darrow             Sales & Marketing                    US
Scott Wallace           Operations
```

<span data-ttu-id="85bbb-183">Mit dem Cmdlet **"Select-Object** " können Sie die Eigenschaften auswählen, die ein Befehl angezeigt werden soll.</span><span class="sxs-lookup"><span data-stu-id="85bbb-183">The **Select-Object** cmdlet lets you pick and choose the properties you want a command to display.</span></span> <span data-ttu-id="85bbb-184">Wenn Sie alle Eigenschaften für Benutzerkonten anzeigen möchten, verwenden Sie das Platzhalterzeichen (\*), um Sie alle für ein bestimmtes Benutzerkonto anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="85bbb-184">To see all of the properties for user accounts, use the wildcard character (\*) to display them all for a specific user account.</span></span> <span data-ttu-id="85bbb-185">Es folgt ein Beispiel:</span><span class="sxs-lookup"><span data-stu-id="85bbb-185">Here is an example:</span></span>
  
```
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

<span data-ttu-id="85bbb-p116">Um die Liste der anzuzeigenden Konten noch weiter einzuschränken, können Sie auch das **Where-Object**-Cmdlet verwenden. Nachfolgend ist ein Beispielbefehl aufgeführt, mit dem nur die Benutzerkonten angezeigt werden, die über einen nicht angegebenen Verwendungsstandort verfügen:</span><span class="sxs-lookup"><span data-stu-id="85bbb-p116">To be more selective about the list of accounts to display, you can also use the **Where-Object** cmdlet. Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```
Get-MsolUser | Where-Object {$_.UsageLocation -eq $Null} | Select-Object DisplayName, Department, UsageLocation
```

<span data-ttu-id="85bbb-188">Dieser Befehl weist Office 365 PowerShell zu folgenden Aktionen an:</span><span class="sxs-lookup"><span data-stu-id="85bbb-188">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="85bbb-189">Alle Informationen der Benutzerkonten abrufen (**Get-MsolUser**) und an den nächsten Befehl senden (**|**).</span><span class="sxs-lookup"><span data-stu-id="85bbb-189">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="85bbb-190">Hier finden Sie alle Benutzerkonten mit einem nicht angegebenen Verwendungs Speicherort ( **Where-Object {\_$. UsageLocation-EQ $NULL}** ) und die resultierenden Informationen an den nächsten Befehl senden **|** ().</span><span class="sxs-lookup"><span data-stu-id="85bbb-190">Find all of the user accounts that have an unspecified usage location ( **Where-Object {$\_.UsageLocation -eq $Null}** ) and send the resulting information to the next command ( **|** ).</span></span> <span data-ttu-id="85bbb-191">In den geschweiften Klammern weist der Befehl Office 365 PowerShell an, nur den kontensatz zu finden, in dem die UsageLocation-Benutzerkonto Eigenschaft ( \*\* $ \_. UsageLocation\*\* ) ist nicht angegeben ( **-EQ $NULL** ).</span><span class="sxs-lookup"><span data-stu-id="85bbb-191">Inside the braces, the command is instructing Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
- <span data-ttu-id="85bbb-192">Nur den Namen des Benutzerkontos, die Abteilung und den Verwendungs Speicherort anzeigen ( **Select-Object DisplayName, Department, UsageLocation** ).</span><span class="sxs-lookup"><span data-stu-id="85bbb-192">Display only the user account name, department, and usage location ( **Select-Object DisplayName, Department, UsageLocation** ).</span></span>
    
<span data-ttu-id="85bbb-193">Es sollten Informationen ähnlich den folgenden angezeigt werden:</span><span class="sxs-lookup"><span data-stu-id="85bbb-193">You should see information similar to this:</span></span>
  
```
DisplayName              Department                      UsageLocation
-----------              ----------                      -------------
Brian Johnson 
Scott Wallace            Operations
```

<span data-ttu-id="85bbb-194">Wenn Sie die Verzeichnissynchronisierung zum Erstellen und Verwalten Ihrer Office 365-Benutzer verwenden, können Sie das lokale Konto anzeigen, aus dem ein Office 365 Benutzer projiziert wurde.</span><span class="sxs-lookup"><span data-stu-id="85bbb-194">If you are using directory synchronization to create and manage your Office 365 users, you can display which local account an Office 365 user has been projected from.</span></span> <span data-ttu-id="85bbb-195">Im folgenden wird davon ausgegangen, dass Azure AD Connect für die Verwendung des Standard Quell Ankers von objectGUID konfiguriert ist (Weitere Informationen zum Konfigurieren eines Quell Ankers finden Sie unter [Azure AD Connect: Design Concepts](https://docs.microsoft.com/en-us/azure/active-directory/hybrid/plan-connect-design-concepts)), und es wird davon ausgegangen, dass das Active Directory Modul für PowerShell installiert (siehe Tools für die [Remoteverwaltung](https://www.microsoft.com/en-gb/download/details.aspx?id=45520)):</span><span class="sxs-lookup"><span data-stu-id="85bbb-195">The following assumes that Azure AD Connect has been configured to use the default source anchor of ObjectGUID (for more on configuring a source anchor, see [Azure AD Connect: Design concepts](https://docs.microsoft.com/en-us/azure/active-directory/hybrid/plan-connect-design-concepts)) and assumes that the Active Directory module for powershell has been installed (see [RSAT tools](https://www.microsoft.com/en-gb/download/details.aspx?id=45520)):</span></span>

```
Get-ADUser ([guid][System.Convert]::FromBase64String((Get-MsolUser -UserPrincipalName <UPN of user account>).ImmutableID)).guid
```

    
## <a name="see-also"></a><span data-ttu-id="85bbb-196">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="85bbb-196">See also</span></span>

[<span data-ttu-id="85bbb-197">Verwalten von Benutzerkonten und Lizenzen mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="85bbb-197">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="85bbb-198">Verwalten von Office 365 mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="85bbb-198">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="85bbb-199">Erste Schritte mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="85bbb-199">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

