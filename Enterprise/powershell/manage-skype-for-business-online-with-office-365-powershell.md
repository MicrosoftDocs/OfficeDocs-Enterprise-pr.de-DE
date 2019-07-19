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
ms.custom: ''
ms.assetid: 054c16e6-9fd1-4e85-a0e6-81788b8410ea
description: 'Zusammenfassung: Verwenden Sie Office 365 PowerShell zum Verwalten von Skype for Business Online-Richtlinien, benutzerspezifischen Richtlinien und Besprechungseinstellungen.'
ms.openlocfilehash: 80d8308a1c9b32fcafd47d1df2f699141e41accd
ms.sourcegitcommit: 1c97471f47e1869f6db684f280f9085b7c2ff59f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/18/2019
ms.locfileid: "35782135"
---
# <a name="manage-skype-for-business-online-with-office-365-powershell"></a><span data-ttu-id="0f18d-103">Verwalten von Skype for Business Online mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="0f18d-103">Manage Skype for Business Online with Office 365 PowerShell</span></span>

 <span data-ttu-id="0f18d-104">**Zusammenfassung:** Verwenden Sie Office 365 PowerShell zum Verwalten von Skype for Business Online-Richtlinien, benutzerspezifischen Richtlinien und Besprechungseinstellungen.</span><span class="sxs-lookup"><span data-stu-id="0f18d-104">**Summary:** Use Office 365 PowerShell to manage Skype for Business Online policies, per-user policies, and meeting settings.</span></span>
  
<span data-ttu-id="0f18d-105">Eine der Hauptaufgaben des Skype for Business Online-Administrators ist die Richtlinienverwaltung.</span><span class="sxs-lookup"><span data-stu-id="0f18d-105">One of the primary tasks of any Skype for Business Online administrator is managing policies.</span></span> <span data-ttu-id="0f18d-106">Obwohl Sie einige dieser Aufgaben in Microsoft 365 Admin Center durchführen können, können andere Aufgaben in Office 365 PowerShell wesentlich schneller und einfacher durchgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="0f18d-106">Although you can accomplish some of these tasks in the Microsoft 365 admin center, other tasks are much quicker and easier in Office 365 PowerShell.</span></span> 

## <a name="before-you-start"></a><span data-ttu-id="0f18d-107">Vor der Bereitstellung</span><span class="sxs-lookup"><span data-stu-id="0f18d-107">Before you start</span></span>

<span data-ttu-id="0f18d-108">Laden Sie das [Skype for Business Online-Connector-Modul](https://www.microsoft.com/en-us/download/details.aspx?id=39366)herunter, installieren Sie es, und starten Sie den Computer neu, wenn Sie dazu aufgefordert werden.</span><span class="sxs-lookup"><span data-stu-id="0f18d-108">Download and install the [Skype for Business Online Connector module](https://www.microsoft.com/en-us/download/details.aspx?id=39366), and then restart your computer if prompted.</span></span>


## <a name="connect-using-a-skype-for-business-online-administrator-account-name-and-password"></a><span data-ttu-id="0f18d-109">Herstellen einer Verbindung mit einem Skype for Business Online Administratorkontonamen und Kennwort</span><span class="sxs-lookup"><span data-stu-id="0f18d-109">Connect using a Skype for Business Online administrator account name and password</span></span>

1. <span data-ttu-id="0f18d-110">Öffnen Sie eine Windows PowerShell-Eingabeaufforderung, und führen Sie die folgenden Befehle aus:</span><span class="sxs-lookup"><span data-stu-id="0f18d-110">Open a Windows PowerShell command prompt and run the following commands:</span></span> 
    
  ```
  Import-Module SkypeOnlineConnector
  $userCredential = Get-Credential
  $sfbSession = New-CsOnlineSession -Credential $userCredential
  Import-PSSession $sfbSession
  ```

2. <span data-ttu-id="0f18d-111">Geben Sie im Dialogfeld **Windows PowerShell Anmeldeinformationen** Ihren Skype for Business Online Administratorkontonamen und das Kennwort ein, und klicken Sie dann auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="0f18d-111">In the **Windows PowerShell Credential Request** dialog box, type your Skype for Business Online administrator account name and password, and then click **OK**.</span></span>


## <a name="connect-using-a-skype-for-business-online-administrator-account-with-multifactor-authentication"></a><span data-ttu-id="0f18d-112">Herstellen einer Verbindung mithilfe eines Skype for Business Online Administratorkontos mit mehrstufiger Authentifizierung</span><span class="sxs-lookup"><span data-stu-id="0f18d-112">Connect using a Skype for Business Online administrator account with multifactor authentication</span></span>

1. <span data-ttu-id="0f18d-113">Öffnen Sie eine Windows PowerShell-Eingabeaufforderung, und führen Sie die folgenden Befehle aus:</span><span class="sxs-lookup"><span data-stu-id="0f18d-113">Open a Windows PowerShell command prompt and run the following commands:</span></span>

  ```
  Import-Module SkypeOnlineConnector
  $sfbSession = New-CsOnlineSession
  Import-PSSession $sfbSession
  ```

2. <span data-ttu-id="0f18d-114">Wenn Sie mit dem Befehl **New-CsOnlineSession** dazu aufgefordert werden, geben Sie den Namen Ihres Skype for Business Online Administratorkontos ein.</span><span class="sxs-lookup"><span data-stu-id="0f18d-114">When prompted by the **New-CsOnlineSession** command, enter your Skype for Business Online administrator account name.</span></span>

3. <span data-ttu-id="0f18d-115">Geben Sie im Dialogfeld **Anmelden in Ihrem Konto** Ihr Skype for Business Online Administratorkennwort ein, und klicken Sie dann auf **Anmelden**.</span><span class="sxs-lookup"><span data-stu-id="0f18d-115">In the **Sign in to your account** dialog box, type your Skype for Business Online administrator password, and then click **Sign in**.</span></span>

4. <span data-ttu-id="0f18d-116">Befolgen Sie die Anweisungen im Dialogfeld **Anmelden bei Ihrem Konto** , um zusätzliche Authentifizierungsinformationen bereitzustellen, beispielsweise einen Überprüfungscode, und klicken Sie dann auf **überprüfen**.</span><span class="sxs-lookup"><span data-stu-id="0f18d-116">Follow the instructions in the **Sign in to your account** dialog box to provide additional authentication information, such as a verification code, and then click **Verify**.</span></span>

<span data-ttu-id="0f18d-117">Weitere Informationen hierzu finden Sie unter den folgenden Themen:</span><span class="sxs-lookup"><span data-stu-id="0f18d-117">For more information, see the following topics:</span></span>
  
- [<span data-ttu-id="0f18d-118">Verwalten von Skype for Business Online-Richtlinien mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="0f18d-118">Manage Skype for Business Online policies with Office 365 PowerShell</span></span>](manage-skype-for-business-online-policies-with-office-365-powershell.md)
    
- [<span data-ttu-id="0f18d-119">Zuweisen von benutzerspezifischen Skype for Business Online-Richtlinien mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="0f18d-119">Assign per-user Skype for Business Online policies with Office 365 PowerShell</span></span>](assign-per-user-skype-for-business-online-policies-with-office-365-powershell.md)
    
## <a name="see-also"></a><span data-ttu-id="0f18d-120">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="0f18d-120">See also</span></span>

[<span data-ttu-id="0f18d-121">Verwalten von Office 365 mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="0f18d-121">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="0f18d-122">Erste Schritte mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="0f18d-122">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

[<span data-ttu-id="0f18d-123">Verweise auf Skype for Business PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="0f18d-123">Skype for Business PowerShell cmdlet references</span></span>](https://docs.microsoft.com/powershell/module/skype/?view=skype-ps)

