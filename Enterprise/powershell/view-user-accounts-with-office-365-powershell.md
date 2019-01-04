---
title: Anzeigen von Benutzerkonten mit Office 365 PowerShell
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
- LIL_Placement
- PowerShell
- Ent_Office_Other
ms.assetid: bb12f49d-a85d-4f3b-ada2-5c4e33977b10
description: 'Zusammenfassung: Anzeigen, Liste oder Ihre Benutzerkonten auf verschiedene Arten mit Office 365 PowerShell anzuzeigen.'
ms.openlocfilehash: dc33b64207341576968867fbeea6f211034eeca6
ms.sourcegitcommit: 15db0f1e5f8036e46063662d7df22387906f8ba7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/04/2019
ms.locfileid: "27546526"
---
# <a name="view-user-accounts-with-office-365-powershell"></a><span data-ttu-id="e720b-103">Anzeigen von Benutzerkonten mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="e720b-103">View user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="e720b-104">**Zusammenfassung:** Zeigen Sie Ihre Benutzerkonten auf verschiedene Arten mit Office 365 PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e720b-104">**Summary:** View your user accounts in various ways with Office 365 PowerShell.</span></span>
  
<span data-ttu-id="e720b-105">Obwohl Sie das Office 365 Admin Center zum Anzeigen von Konten für Ihre Office 365-Mandanten verwenden können, können Sie auch mithilfe von Office 365 PowerShell und führen Sie einige Dinge, die die Office 365-Verwaltungskonsole kann nicht.</span><span class="sxs-lookup"><span data-stu-id="e720b-105">Although you can use the Office 365 Admin center to view the accounts for your Office 365 tenant, you can also use Office 365 PowerShell and do some things that the Office 365 Admin center cannot.</span></span>
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="e720b-106">Verwenden von Azure Active Directory PowerShell Graph-Modul</span><span class="sxs-lookup"><span data-stu-id="e720b-106">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="e720b-107">Zuerst [eine Verbindung mit Ihrem Office 365-Mandanten](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="e720b-107">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  
### <a name="view-all-accounts"></a><span data-ttu-id="e720b-108">Zeigen Sie aller Konten an</span><span class="sxs-lookup"><span data-stu-id="e720b-108">View all accounts</span></span>

<span data-ttu-id="e720b-109">Um die vollständige Liste der Benutzerkonten anzuzeigen, führen Sie diesen Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="e720b-109">To display the full list of user accounts, run this command:</span></span>
  
```
Get-AzureADUser
```

<span data-ttu-id="e720b-110">Es sollten Informationen ähnlich den folgenden angezeigt werden:</span><span class="sxs-lookup"><span data-stu-id="e720b-110">You should see information similar to this:</span></span>
  
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

### <a name="view-a-specific-account"></a><span data-ttu-id="e720b-111">Anzeigen eines bestimmten Kontos</span><span class="sxs-lookup"><span data-stu-id="e720b-111">View a specific account</span></span>

<span data-ttu-id="e720b-112">Um ein bestimmtes Benutzerkonto anzuzeigen, geben Sie den Benutzerprinzipalnamen (UPN) des Benutzerkontos, entfernen Sie die "<" und ">" Zeichen, und führen Sie diesen Befehl:</span><span class="sxs-lookup"><span data-stu-id="e720b-112">To display a specific user account, fill in the user principal name (UPN) of the user account, remove the "<" and ">" characters, and run this command:</span></span>
  
```
Get-AzureADUser -ObjectID <UPN of user account>
```

### <a name="view-additional-property-values-for-a-specific-account"></a><span data-ttu-id="e720b-113">Zusätzliche Eigenschaftswerte für ein bestimmtes Konto anzeigen</span><span class="sxs-lookup"><span data-stu-id="e720b-113">View additional property values for a specific account</span></span>

<span data-ttu-id="e720b-114">Standardmäßig zeigt das Cmdlet **Get-AzureADUser** nur die ObjectID, DisplayName und UserPrincipalName Eigenschaften von Konten.</span><span class="sxs-lookup"><span data-stu-id="e720b-114">By default, the **Get-AzureADUser** cmdlet only displays the ObjectID, DisplayName, and UserPrincipalName properties of accounts.</span></span>

<span data-ttu-id="e720b-p101">Um weitere werden selektive über die Liste der Eigenschaften für die Anzeige das **Select-Object** -Cmdlet in Kombination mit dem Cmdlet **Get-AzureADUser** können Sie. Um die zwei Cmdlets zu kombinieren, verwenden wir das Pipe-Zeichen "|", weist Azure Active Directory PowerShell für die Ergebnisse eines Befehls und senden Sie sie an den nächsten Befehl Grafik. Hier ist ein Beispielbefehl, der die DisplayName, Abteilung und usagelocation-Wert angegeben für jedes Benutzerkonto angezeigt wird:</span><span class="sxs-lookup"><span data-stu-id="e720b-p101">To be more selective about the list of properties to display, you can use the **Select-Object** cmdlet in combination with the **Get-AzureADUser** cmdlet. To combine the two cmdlets, we use the "pipe" character "|", which tells Azure Active Directory PowerShell for Graph to take the results of one command and send it to the next command. Here is an example command that displays the DisplayName, Department, and UsageLocation for every user account:</span></span>
  
```
Get-AzureADUser | Select-Object DisplayName,Department,UsageLocation
```

<span data-ttu-id="e720b-118">Dieser Befehl gibt Office 365 Powershell die folgenden Anweisungen:</span><span class="sxs-lookup"><span data-stu-id="e720b-118">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="e720b-119">Alle Informationen der Benutzerkonten abrufen (**Get-AzureADUser**) und an den nächsten Befehl senden (**|**).</span><span class="sxs-lookup"><span data-stu-id="e720b-119">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="e720b-120">Zeigt nur den Benutzer Konto Name, Abteilung und Verwendung Speicherort ( **Select-Object DisplayName, Abteilung, usagelocation-Wert angegeben** ).</span><span class="sxs-lookup"><span data-stu-id="e720b-120">Display only the user account name, department, and usage location ( **Select-Object DisplayName, Department, UsageLocation** ).</span></span>
  
<span data-ttu-id="e720b-p102">Um alle Eigenschaften für Benutzerkonten angezeigt wird, verwenden Sie das **Select-Object** -Cmdlet und das Platzhalterzeichen (\*) an alle für ein bestimmtes Benutzerkonto. Es folgt ein Beispiel:</span><span class="sxs-lookup"><span data-stu-id="e720b-p102">To see all of the properties for user accounts, use the **Select-Object** cmdlet and the wildcard character (\*) to display them all for a specific user account. Here is an example:</span></span>
  
```
Get-AzureADUser -ObjectID "BelindaN@litwareinc.onmicosoft.com" | Select-Object *
```

<span data-ttu-id="e720b-123">Als weiteres Beispiel können Sie den Aktivierungsstatus eines bestimmten Benutzerkontos mit dem folgenden Befehl überprüfen:</span><span class="sxs-lookup"><span data-stu-id="e720b-123">As another example, you can check the enabled status of a specific user account with the following command:</span></span>
  
```
Get-AzureADUser -ObjectID <UPN of user account> | Select-Object DisplayName,UserPrincipalName,AccountEnabled
```

### <a name="view-some-accounts-based-on-a-common-property"></a><span data-ttu-id="e720b-124">Zeigen Sie einige Benutzerkonten basierend auf einer gemeinsamen Eigenschaft an</span><span class="sxs-lookup"><span data-stu-id="e720b-124">View some accounts based on a common property</span></span>

<span data-ttu-id="e720b-p103">Um weitere werden selektive zu der Liste der Konten für die Anzeige das **Where-Object** -Cmdlet in Kombination mit dem Cmdlet **Get-AzureADUser** können Sie. Um die zwei Cmdlets zu kombinieren, verwenden wir das Pipe-Zeichen "|", weist Azure Active Directory PowerShell für die Ergebnisse eines Befehls und senden Sie sie an den nächsten Befehl Grafik. Hier ist ein Beispielbefehl, der nur die Benutzerkonten angezeigt werden, die einen Verwendungsspeicherort nicht angegeben ist:</span><span class="sxs-lookup"><span data-stu-id="e720b-p103">To be more selective about the list of accounts to display, you can use the **Where-Object** cmdlet in combination with the **Get-AzureADUser** cmdlet. To combine the two cmdlets, we use the "pipe" character "|", which tells Azure Active Directory PowerShell for Graph to take the results of one command and send it to the next command. Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```
Get-AzureADUser | Where-Object {$_.UsageLocation -eq $Null}
```

<span data-ttu-id="e720b-128">Dieser Befehl weist Azure Active Directory PowerShell für Diagramm an:</span><span class="sxs-lookup"><span data-stu-id="e720b-128">This command instructs Azure Active Directory PowerShell for Graph to:</span></span>
  
- <span data-ttu-id="e720b-129">Alle Informationen der Benutzerkonten abrufen (**Get-AzureADUser**) und an den nächsten Befehl senden (**|**).</span><span class="sxs-lookup"><span data-stu-id="e720b-129">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="e720b-p104">Hier finden Sie alle Benutzerkonten, die einen Verwendungsspeicherort nicht angegeben haben ( **Where-Object {$\_. Usagelocation-Wert angegeben - Eq $Null}** ). Innerhalb der geschweiften Klammern weist der Befehl Office 365 PowerShell nur die Gruppe von Konten, die in dem für das usagelocation-Wert angegeben Benutzerkonto Eigenschaft suchen ( \*\* $ \_. Usagelocation-Wert angegeben\*\* ) ist nicht angegebenen ( **-Eq $Null** ).</span><span class="sxs-lookup"><span data-stu-id="e720b-p104">Find all of the user accounts that have an unspecified usage location ( **Where-Object {$\_.UsageLocation -eq $Null}** ). Inside the braces, the command instructs Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
<span data-ttu-id="e720b-p105">Die **usagelocation-Wert angegeben** -Eigenschaft ist nur eine viele Eigenschaften mit einem Benutzerkonto verknüpft. Um alle Eigenschaften für Benutzerkonten angezeigt wird, verwenden Sie das **Select-Object** -Cmdlet und das Platzhalterzeichen (\*) an alle für ein bestimmtes Benutzerkonto. Es folgt ein Beispiel:</span><span class="sxs-lookup"><span data-stu-id="e720b-p105">The **UsageLocation** property is only one of many properties associated with a user account. To see all of the properties for user accounts, use the **Select-Object** cmdlet and the wildcard character (\*) to display them all for a specific user account. Here is an example:</span></span>
  
```
Get-AzureADUser -ObjectID "BelindaN@litwareinc.onmicosoft.com" | Select-Object *
```

<span data-ttu-id="e720b-p106">In dieser Liste steht das **City**-Objekt für den Namen einer Benutzerkontoeigenschaft. Dies bedeutet, dass Sie mit dem folgenden Befehl eine Liste aller Benutzerkonten für Benutzer, die in London leben, anzeigen können:</span><span class="sxs-lookup"><span data-stu-id="e720b-p106">For example, from this list, **City** is the name of a user account property. This means you can use the following command to list all of the user accounts for users living in London:</span></span>
  
```
Get-AzureADUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  <span data-ttu-id="e720b-p107">Die Syntax für die **Where-Object** -Cmdlet in diesen Beispielen dargestellt ist **Where-Object {$\_.** [-Eigenschaft Benutzerkontonamen] [Vergleichsoperator] [Wert] **}**. > [Vergleichsoperator] **-Eq** für gleich, **-Ne** für nicht gleich, **-Lt** kleiner als **-Gt** für größer als und anderen ist.  [Wert] wird in der Regel eine Zeichenfolge (eine Sequenz von Buchstaben, Zahlen und andere Zeichen), einen numerischen Wert oder **$Null** für nicht spezifizierte > Weitere Informationen finden Sie in [Where-Object](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Where-Object?view=powershell-5.1) .</span><span class="sxs-lookup"><span data-stu-id="e720b-p107">The syntax for the **Where-Object** cmdlet shown in these examples is **Where-Object {$\_.** [user account property name] [comparison operator] [value] **}**.>  [comparison operator] is **-eq** for equals, **-ne** for not equals, **-lt** for less than, **-gt** for greater than, and others.  [value] is typically a string (a sequence of letters, numbers, and other characters), a numerical value, or **$Null** for unspecified>  See [Where-Object](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Where-Object?view=powershell-5.1) for more information.</span></span>
  

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="e720b-140">Verwenden Sie die Microsoft Azure Active Directory-Moduls für Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="e720b-140">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="e720b-141">Zuerst [eine Verbindung mit Ihrem Office 365-Mandanten](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="e720b-141">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

### <a name="view-all-accounts"></a><span data-ttu-id="e720b-142">Zeigen Sie aller Konten an</span><span class="sxs-lookup"><span data-stu-id="e720b-142">View all accounts</span></span>

<span data-ttu-id="e720b-143">Um die vollständige Liste der Benutzerkonten anzuzeigen, führen Sie diesen Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="e720b-143">To display the full list of user accounts, run this command:</span></span>
  
```
Get-MsolUser
```

<span data-ttu-id="e720b-144">Es sollten Informationen ähnlich den folgenden angezeigt werden:</span><span class="sxs-lookup"><span data-stu-id="e720b-144">You should see information similar to this:</span></span>
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
ZrinkaM@litwareinc.onmicrosoft.com    Zrinka Makovac        True
BonnieK@litwareinc.onmicrosoft.com    Bonnie Kearney        True
FabriceC@litwareinc.onmicrosoft.com   Fabrice Canel         True
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
AnneWlitwareinc.onmicrosoft.com       Anne Wallace          True
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

<span data-ttu-id="e720b-p108">Das Cmdlet **Get-MsolUser** verfügt über eine Reihe von Parametern für das Filtern der Benutzerkonten angezeigt. Führen Sie beispielsweise die Liste der nicht lizenzierten Benutzer (Benutzer, die zu Office 365 hinzugefügt wurden, aber noch nicht noch lizenziert wurden, um die Dienste zu verwenden), diesen Befehl.</span><span class="sxs-lookup"><span data-stu-id="e720b-p108">The **Get-MsolUser** cmdlet also has a set of parameters to filter the set of user accounts displayed. For example, for the list of unlicensed users (users who've been added to Office 365 but haven't yet been licensed to use any of the services), run this command.</span></span>
  
```
Get-MsolUser -UnlicensedUsersOnly
```

<span data-ttu-id="e720b-147">Es sollten Informationen ähnlich den folgenden angezeigt werden:</span><span class="sxs-lookup"><span data-stu-id="e720b-147">You should see information similar to this:</span></span>
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

<span data-ttu-id="e720b-148">Weitere Informationen zu weiteren Parametern zum Filtern der Anzeige der Satz von Benutzerkonten angezeigt wird, finden Sie unter [Get-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194133(v=azure.100)).</span><span class="sxs-lookup"><span data-stu-id="e720b-148">For more information about additional parameters to filter the display the set of user accounts displayed, see [Get-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194133(v=azure.100)).</span></span>
  

### <a name="view-a-specific-account"></a><span data-ttu-id="e720b-149">Anzeigen eines bestimmten Kontos</span><span class="sxs-lookup"><span data-stu-id="e720b-149">View a specific account</span></span>

<span data-ttu-id="e720b-150">Um ein bestimmtes Benutzerkonto anzuzeigen, geben Sie den Benutzerprinzipalnamen (UPN) des Benutzerkontos, entfernen Sie die "<" und ">" Zeichen, und führen Sie diesen Befehl:</span><span class="sxs-lookup"><span data-stu-id="e720b-150">To display a specific user account, fill in the user principal name (UPN) of the user account, remove the "<" and ">" characters, and run this command:</span></span>
  
```
Get-MsolUser -UserPrincipalName <UPN of user account>
```

### <a name="view-some-accounts-based-on-a-common-property"></a><span data-ttu-id="e720b-151">Zeigen Sie einige Benutzerkonten basierend auf einer gemeinsamen Eigenschaft an</span><span class="sxs-lookup"><span data-stu-id="e720b-151">View some accounts based on a common property</span></span>

<span data-ttu-id="e720b-p109">Um weitere werden selektive zu der Liste der Konten für die Anzeige das **Where-Object** -Cmdlet in Kombination mit dem Cmdlet **Get-MsolUser** können Sie. Um die zwei Cmdlets zu kombinieren, verwenden wir das Pipe-Zeichen "|", Office 365 PowerShell die Ergebnisse eines Befehls und senden Sie sie an den nächsten Befehl weist. Hier ist ein Beispielbefehl, der nur die Benutzerkonten angezeigt werden, die einen Verwendungsspeicherort nicht angegeben ist:</span><span class="sxs-lookup"><span data-stu-id="e720b-p109">To be more selective about the list of accounts to display, you can use the **Where-Object** cmdlet in combination with the **Get-MsolUser** cmdlet. To combine the two cmdlets, we use the "pipe" character "|", which tells Office 365 PowerShell to take the results of one command and send it to the next command. Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```
Get-MsolUser | Where-Object {$_.UsageLocation -eq $Null}
```

<span data-ttu-id="e720b-155">Dieser Befehl gibt Office 365 Powershell die folgenden Anweisungen:</span><span class="sxs-lookup"><span data-stu-id="e720b-155">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="e720b-156">Alle Informationen der Benutzerkonten abrufen (**Get-MsolUser**) und an den nächsten Befehl senden (**|**).</span><span class="sxs-lookup"><span data-stu-id="e720b-156">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="e720b-p110">Hier finden Sie alle Benutzerkonten, die einen Verwendungsspeicherort nicht angegeben haben ( **Where-Object {$\_. Usagelocation-Wert angegeben - Eq $Null}** ). Innerhalb der geschweiften Klammern weist der Befehl Office 365 PowerShell nur die Gruppe von Konten, die in dem für das usagelocation-Wert angegeben Benutzerkonto Eigenschaft suchen ( \*\* $ \_. Usagelocation-Wert angegeben\*\* ) ist nicht angegebenen ( **-Eq $Null** ).</span><span class="sxs-lookup"><span data-stu-id="e720b-p110">Find all of the user accounts that have an unspecified usage location ( **Where-Object {$\_.UsageLocation -eq $Null}** ). Inside the braces, the command instructs Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
<span data-ttu-id="e720b-159">Es sollten Informationen ähnlich den folgenden angezeigt werden:</span><span class="sxs-lookup"><span data-stu-id="e720b-159">You should see information similar to this:</span></span>
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False

```

<span data-ttu-id="e720b-p111">Die **usagelocation-Wert angegeben** -Eigenschaft ist nur eine viele Eigenschaften mit einem Benutzerkonto verknüpft. Um alle Eigenschaften für Benutzerkonten angezeigt wird, verwenden Sie das **Select-Object** -Cmdlet und das Platzhalterzeichen (\*) an alle für ein bestimmtes Benutzerkonto. Es folgt ein Beispiel:</span><span class="sxs-lookup"><span data-stu-id="e720b-p111">The **UsageLocation** property is only one of many properties associated with a user account. To see all of the properties for user accounts, use the **Select-Object** cmdlet and the wildcard character (\*) to display them all for a specific user account. Here is an example:</span></span>
  
```
Get-MsolUser -UserPrincipalName "BelindaN@litwareinc.onmicosoft.com" | Select-Object *
```

<span data-ttu-id="e720b-p112">In dieser Liste steht das **City**-Objekt für den Namen einer Benutzerkontoeigenschaft. Dies bedeutet, dass Sie mit dem folgenden Befehl eine Liste aller Benutzerkonten für Benutzer, die in London leben, anzeigen können:</span><span class="sxs-lookup"><span data-stu-id="e720b-p112">For example, from this list, **City** is the name of a user account property. This means you can use the following command to list all of the user accounts for users living in London:</span></span>
  
```
Get-MsolUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  <span data-ttu-id="e720b-p113">Die Syntax für die **Where-Object** -Cmdlet in diesen Beispielen dargestellt ist **Where-Object {$\_.** [-Eigenschaft Benutzerkontonamen] [Vergleichsoperator] [Wert] **}**.  [Vergleichsoperator] ist **-Eq** für gleich, **-Ne** für nicht gleich, **-Lt** kleiner als **-Gt** für größer als und anderen.  [Wert] wird in der Regel eine Zeichenfolge (eine Sequenz von Buchstaben, Zahlen und andere Zeichen), einen numerischen Wert oder **$Null** für nicht spezifizierte. Weitere Informationen finden Sie unter [Where-Object](https://technet.microsoft.com/en-us/library/hh849715.aspx) .</span><span class="sxs-lookup"><span data-stu-id="e720b-p113">The syntax for the **Where-Object** cmdlet shown in these examples is **Where-Object {$\_.** [user account property name] [comparison operator] [value] **}**.  [comparison operator] is **-eq** for equals, **-ne** for not equals, **-lt** for less than, **-gt** for greater than, and others.  [value] is typically a string (a sequence of letters, numbers, and other characters), a numerical value, or **$Null** for unspecified. See [Where-Object](https://technet.microsoft.com/en-us/library/hh849715.aspx) for more information.</span></span>
  
<span data-ttu-id="e720b-170">Sie können den blockierten Status eines Benutzerkontos mit dem folgenden Befehl überprüfen:</span><span class="sxs-lookup"><span data-stu-id="e720b-170">You can check the blocked status of a user account with the following command:</span></span>
  
```
Get-MolUser -UserPrincipalName <UPN of user account> | Select-Object DisplayName,BlockCredential
```

### <a name="view-additional-property-values-for-accounts"></a><span data-ttu-id="e720b-171">Zusätzliche Eigenschaftswerte für Konten anzeigen</span><span class="sxs-lookup"><span data-stu-id="e720b-171">View additional property values for accounts</span></span>

<span data-ttu-id="e720b-172">Das Cmdlet **Get-MsolUser** Standardmäßig zeigt drei Eigenschaften von Benutzerkonten:</span><span class="sxs-lookup"><span data-stu-id="e720b-172">The **Get-MsolUser** cmdlet by default displays three properties of user accounts:</span></span>
  
- <span data-ttu-id="e720b-173">UserPrincipalName</span><span class="sxs-lookup"><span data-stu-id="e720b-173">UserPrincipalName</span></span>
    
- <span data-ttu-id="e720b-174">DisplayName</span><span class="sxs-lookup"><span data-stu-id="e720b-174">DisplayName</span></span>
    
- <span data-ttu-id="e720b-175">isLicensed</span><span class="sxs-lookup"><span data-stu-id="e720b-175">isLicensed</span></span>
    
<span data-ttu-id="e720b-p114">Wenn zusätzliche Eigenschaften, wie die Abteilung für der Benutzer funktioniert und Land/Region, in dem der Benutzer Office 365-Dienste verwendet, werden sollen, können Sie **Get-MsolUser** in Kombination mit dem **Select-Object** -Cmdlet zum Angeben der Liste der Benutzerkonto ausführen Eigenschaften. Es folgt ein Beispiel:</span><span class="sxs-lookup"><span data-stu-id="e720b-p114">If you need additional properties, such as the department the user works for and the country/region where the user uses Office 365 services, you can run **Get-MsolUser** in combination with the **Select-Object** cmdlet to specify the list of user account properties. Here is an example:</span></span>
  
```
Get-MsolUser | Select-Object DisplayName, Department, UsageLocation
```

<span data-ttu-id="e720b-178">Dieser Befehl gibt Office 365 Powershell die folgenden Anweisungen:</span><span class="sxs-lookup"><span data-stu-id="e720b-178">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="e720b-179">Alle Informationen der Benutzerkonten abrufen (**Get-MsolUser**) und an den nächsten Befehl senden (**|**).</span><span class="sxs-lookup"><span data-stu-id="e720b-179">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="e720b-180">Zeigt nur den Benutzer Konto Name, Abteilung und Verwendung Speicherort ( **Select-Object DisplayName, Abteilung, usagelocation-Wert angegeben** ).</span><span class="sxs-lookup"><span data-stu-id="e720b-180">Display only the user account name, department, and usage location ( **Select-Object DisplayName, Department, UsageLocation** ).</span></span>
    
<span data-ttu-id="e720b-181">Es sollten Informationen ähnlich den folgenden angezeigt werden:</span><span class="sxs-lookup"><span data-stu-id="e720b-181">You should see information similar to this:</span></span>
  
```
DisplayName             Department                       UsageLocation
-----------             ----------                       -------------
Zrinka Makovac          Sales & Marketing                    US
Bonnie Kearney          Sales & Marketing                    US
Fabrice Canel           Legal                                US
Brian Johnson
Anne Wallace            Executive Management                 US
Alex Darrow             Sales & Marketing                    US
Scott Wallace           Operations
```

<span data-ttu-id="e720b-p115">Das **Select-Object** -Cmdlet können Sie die Eigenschaften wählen, die Sie einen Befehl anzeigen möchten. Um alle Eigenschaften für Benutzerkonten angezeigt wird, verwenden Sie das Platzhalterzeichen (\*) für ein bestimmtes Benutzerkonto alle anzeigen. Es folgt ein Beispiel:</span><span class="sxs-lookup"><span data-stu-id="e720b-p115">The **Select-Object** cmdlet lets you pick and choose the properties you want a command to display. To see all of the properties for user accounts, use the wildcard character (\*) to display them all for a specific user account. Here is an example:</span></span>
  
```
Get-MsolUser -UserPrincipalName "BelindaN@litwareinc.onmicosoft.com" | Select-Object *
```

<span data-ttu-id="e720b-p116">Um die Liste der anzuzeigenden Konten noch weiter einzuschränken, können Sie auch das **Where-Object**-Cmdlet verwenden. Nachfolgend ist ein Beispielbefehl aufgeführt, mit dem nur die Benutzerkonten angezeigt werden, die über einen nicht angegebenen Verwendungsstandort verfügen:</span><span class="sxs-lookup"><span data-stu-id="e720b-p116">To be more selective about the list of accounts to display, you can also use the **Where-Object** cmdlet. Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```
Get-MsolUser | Where-Object {$_.UsageLocation -eq $Null} | Select-Object DisplayName, Department, UsageLocation
```

<span data-ttu-id="e720b-187">Dieser Befehl gibt Office 365 Powershell die folgenden Anweisungen:</span><span class="sxs-lookup"><span data-stu-id="e720b-187">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="e720b-188">Alle Informationen der Benutzerkonten abrufen (**Get-MsolUser**) und an den nächsten Befehl senden (**|**).</span><span class="sxs-lookup"><span data-stu-id="e720b-188">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="e720b-p117">Hier finden Sie alle Benutzerkonten, die einen Verwendungsspeicherort nicht angegeben haben ( **Where-Object {$\_. Usagelocation-Wert angegeben - Eq $Null}** ) und die resultierende Daten mit dem nächsten Befehl senden ( **|** ). In die geschweiften Klammern sein, der Befehl fordert Office 365 PowerShell nur die Gruppe von Konten, die in dem für das usagelocation-Wert angegeben Benutzerkonto Eigenschaft suchen ( \*\* $ \_. Usagelocation-Wert angegeben\*\* ) ist nicht angegebenen ( **-Eq $Null** ).</span><span class="sxs-lookup"><span data-stu-id="e720b-p117">Find all of the user accounts that have an unspecified usage location ( **Where-Object {$\_.UsageLocation -eq $Null}** ) and send the resulting information to the next command ( **|** ). Inside the braces, the command is instructing Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
- <span data-ttu-id="e720b-191">Zeigt nur den Benutzer Konto Name, Abteilung und Verwendung Speicherort ( **Select-Object DisplayName, Abteilung, usagelocation-Wert angegeben** ).</span><span class="sxs-lookup"><span data-stu-id="e720b-191">Display only the user account name, department, and usage location ( **Select-Object DisplayName, Department, UsageLocation** ).</span></span>
    
<span data-ttu-id="e720b-192">Es sollten Informationen ähnlich den folgenden angezeigt werden:</span><span class="sxs-lookup"><span data-stu-id="e720b-192">You should see information similar to this:</span></span>
  
```
DisplayName              Department                      UsageLocation
-----------              ----------                      -------------
Brian Johnson 
Scott Wallace            Operations
```

<span data-ttu-id="e720b-p118">Wenn Sie zum Erstellen und Verwalten von Office 365-Benutzer verzeichnissynchronisierung verwenden, können Sie das lokales Konto anzeigen von Office 365-Benutzer hochgerechnet wurde hat. Im folgenden wird davon ausgegangen, dass Azure AD-Connect konfiguriert wurde, um die standardmäßige Quelle Verankerung des Objekt-GUID verwenden (Weitere Informationen zum Konfigurieren eines Quelle Anker finden Sie unter [Azure AD-Connect: Entwerfen Konzepte](https://docs.microsoft.com/en-us/azure/active-directory/hybrid/plan-connect-design-concepts)) und setzt voraus, dass die Active Directory-Moduls für Powershell hat wurde installiert (siehe [RSAT-Tools](https://www.microsoft.com/en-gb/download/details.aspx?id=45520)):</span><span class="sxs-lookup"><span data-stu-id="e720b-p118">If you are using directory synchronization to create and manage your Office 365 users, you can display which local account an Office 365 user has been projected from. The following assumes that Azure AD Connect has been configured to use the default source anchor of ObjectGUID (for more on configuring a source anchor, see [Azure AD Connect: Design concepts](https://docs.microsoft.com/en-us/azure/active-directory/hybrid/plan-connect-design-concepts)) and assumes that the Active Directory module for powershell has been installed (see [RSAT tools](https://www.microsoft.com/en-gb/download/details.aspx?id=45520)):</span></span>

```
(Get-ADUser [guid][system.convert]::frombase64string((Get-MsolUser -UserPrincipalName <UPN of user account>).ImmutableID)).Guid
```

    
## <a name="see-also"></a><span data-ttu-id="e720b-195">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="e720b-195">See also</span></span>

[<span data-ttu-id="e720b-196">Verwalten von Benutzerkonten und Lizenzen mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="e720b-196">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="e720b-197">Verwalten von Office 365 mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="e720b-197">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="e720b-198">Erste Schritte mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="e720b-198">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

