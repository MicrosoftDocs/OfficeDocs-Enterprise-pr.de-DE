---
title: Verwalten von Skype for Business Online mit Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 09/13/2018
audience: ITPro
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: 054c16e6-9fd1-4e85-a0e6-81788b8410ea
description: 'Zusammenfassung: Verwenden Sie Office 365 PowerShell zum Verwalten von Skype for Business Online-Richtlinien, benutzerspezifischen Richtlinien und Besprechungseinstellungen.'
ms.openlocfilehash: 699f799e823df6192a65147210130ae6493f52eb
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844226"
---
# <a name="manage-skype-for-business-online-with-office-365-powershell"></a><span data-ttu-id="3e35e-103">Verwalten von Skype for Business Online mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="3e35e-103">Manage Skype for Business Online with Office 365 PowerShell</span></span>

<span data-ttu-id="3e35e-104">Eine der Hauptaufgaben des Skype for Business Online-Administrators ist die Richtlinienverwaltung.</span><span class="sxs-lookup"><span data-stu-id="3e35e-104">One of the primary tasks of any Skype for Business Online administrator is managing policies.</span></span> <span data-ttu-id="3e35e-105">Obwohl Sie einige dieser Aufgaben in Microsoft 365 Admin Center durchführen können, können andere Aufgaben in Office 365 PowerShell wesentlich schneller und einfacher durchgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="3e35e-105">Although you can accomplish some of these tasks in the Microsoft 365 admin center, other tasks are much quicker and easier in Office 365 PowerShell.</span></span> 

## <a name="before-you-start"></a><span data-ttu-id="3e35e-106">Vor der Bereitstellung</span><span class="sxs-lookup"><span data-stu-id="3e35e-106">Before you start</span></span>

<span data-ttu-id="3e35e-107">Laden Sie das [Skype for Business Online-Connector-Modul](https://www.microsoft.com/download/details.aspx?id=39366)herunter, installieren Sie es, und starten Sie den Computer neu, wenn Sie dazu aufgefordert werden.</span><span class="sxs-lookup"><span data-stu-id="3e35e-107">Download and install the [Skype for Business Online Connector module](https://www.microsoft.com/download/details.aspx?id=39366), and then restart your computer if prompted.</span></span>


## <a name="connect-using-a-skype-for-business-online-administrator-account-name-and-password"></a><span data-ttu-id="3e35e-108">Herstellen einer Verbindung mit einem Skype for Business Online Administratorkontonamen und Kennwort</span><span class="sxs-lookup"><span data-stu-id="3e35e-108">Connect using a Skype for Business Online administrator account name and password</span></span>

1. <span data-ttu-id="3e35e-109">Öffnen Sie eine Windows PowerShell-Eingabeaufforderung, und führen Sie die folgenden Befehle aus:</span><span class="sxs-lookup"><span data-stu-id="3e35e-109">Open a Windows PowerShell command prompt and run the following commands:</span></span> 
    
  ```powershell
  Import-Module SkypeOnlineConnector
  $userCredential = Get-Credential
  $sfbSession = New-CsOnlineSession -Credential $userCredential
  Import-PSSession $sfbSession
  ```

2. <span data-ttu-id="3e35e-110">Geben Sie im Dialogfeld **Windows PowerShell Anmeldeinformationen** Ihren Skype for Business Online Administratorkontonamen und das Kennwort ein, und klicken Sie dann auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="3e35e-110">In the **Windows PowerShell Credential Request** dialog box, type your Skype for Business Online administrator account name and password, and then click **OK**.</span></span>


## <a name="connect-using-a-skype-for-business-online-administrator-account-with-multifactor-authentication"></a><span data-ttu-id="3e35e-111">Herstellen einer Verbindung mithilfe eines Skype for Business Online Administratorkontos mit mehrstufiger Authentifizierung</span><span class="sxs-lookup"><span data-stu-id="3e35e-111">Connect using a Skype for Business Online administrator account with multifactor authentication</span></span>

1. <span data-ttu-id="3e35e-112">Öffnen Sie eine Windows PowerShell-Eingabeaufforderung, und führen Sie die folgenden Befehle aus:</span><span class="sxs-lookup"><span data-stu-id="3e35e-112">Open a Windows PowerShell command prompt and run the following commands:</span></span>

  ```powershell
  Import-Module SkypeOnlineConnector
  $sfbSession = New-CsOnlineSession
  Import-PSSession $sfbSession
  ```

2. <span data-ttu-id="3e35e-113">Wenn Sie mit dem Befehl **New-CsOnlineSession** dazu aufgefordert werden, geben Sie den Namen Ihres Skype for Business Online Administratorkontos ein.</span><span class="sxs-lookup"><span data-stu-id="3e35e-113">When prompted by the **New-CsOnlineSession** command, enter your Skype for Business Online administrator account name.</span></span>

3. <span data-ttu-id="3e35e-114">Geben Sie im Dialogfeld **Anmelden in Ihrem Konto** Ihr Skype for Business Online Administratorkennwort ein, und klicken Sie dann auf **Anmelden**.</span><span class="sxs-lookup"><span data-stu-id="3e35e-114">In the **Sign in to your account** dialog box, type your Skype for Business Online administrator password, and then click **Sign in**.</span></span>

4. <span data-ttu-id="3e35e-115">Befolgen Sie die Anweisungen im Dialogfeld **Anmelden bei Ihrem Konto** , um zusätzliche Authentifizierungsinformationen bereitzustellen, beispielsweise einen Überprüfungscode, und klicken Sie dann auf **überprüfen**.</span><span class="sxs-lookup"><span data-stu-id="3e35e-115">Follow the instructions in the **Sign in to your account** dialog box to provide additional authentication information, such as a verification code, and then click **Verify**.</span></span>

<span data-ttu-id="3e35e-116">Weitere Informationen hierzu finden Sie unter den folgenden Themen:</span><span class="sxs-lookup"><span data-stu-id="3e35e-116">For more information, see the following topics:</span></span>
  
- [<span data-ttu-id="3e35e-117">Verwalten von Skype for Business Online-Richtlinien mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="3e35e-117">Manage Skype for Business Online policies with Office 365 PowerShell</span></span>](manage-skype-for-business-online-policies-with-office-365-powershell.md)
    
- [<span data-ttu-id="3e35e-118">Zuweisen von benutzerspezifischen Skype for Business Online-Richtlinien mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="3e35e-118">Assign per-user Skype for Business Online policies with Office 365 PowerShell</span></span>](assign-per-user-skype-for-business-online-policies-with-office-365-powershell.md)
    
## <a name="see-also"></a><span data-ttu-id="3e35e-119">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="3e35e-119">See also</span></span>

[<span data-ttu-id="3e35e-120">Verwalten von Office 365 mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="3e35e-120">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="3e35e-121">Erste Schritte mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="3e35e-121">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

[<span data-ttu-id="3e35e-122">Verweise auf Skype for Business PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="3e35e-122">Skype for Business PowerShell cmdlet references</span></span>](https://docs.microsoft.com/powershell/module/skype/?view=skype-ps)

