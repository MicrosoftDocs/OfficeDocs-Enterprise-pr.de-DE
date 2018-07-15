---
title: Verwalten von Skype for Business Online mit Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/22/2018
ms.audience: ITPro
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: ''
ms.assetid: 054c16e6-9fd1-4e85-a0e6-81788b8410ea
description: 'Zusammenfassung: Verwenden Sie Office 365 PowerShell zum Verwalten von Skype for Business Online-Richtlinien, benutzerspezifischen Richtlinien und Besprechungseinstellungen.'
ms.openlocfilehash: f490131491a026961b0a5db312df5780483eadd9
ms.sourcegitcommit: b39b8ae3b4268d6475b54e2fdb62982b2c7d9943
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/12/2018
ms.locfileid: "20319236"
---
# <a name="manage-skype-for-business-online-with-office-365-powershell"></a><span data-ttu-id="05557-103">Verwalten von Skype for Business Online mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="05557-103">Manage Skype for Business Online with Office 365 PowerShell</span></span>

 <span data-ttu-id="05557-104">**Zusammenfassung:** Verwenden Sie Office 365 PowerShell zum Verwalten von Skype for Business Online-Richtlinien, benutzerspezifischen Richtlinien und Besprechungseinstellungen.</span><span class="sxs-lookup"><span data-stu-id="05557-104">**Summary:** Use Office 365 PowerShell to manage Skype for Business Online policies, per-user policies, and meeting settings.</span></span>
  
<span data-ttu-id="05557-p101">Eine der wichtigsten Aufgaben des Skype für Business Online-Administrator ist Richtlinien verwalten. Obwohl Sie einige dieser Aufgaben im Office 365 Admin Center ausführen können, sind andere Aufgaben viel schneller und einfacher in Office 365 PowerShell.</span><span class="sxs-lookup"><span data-stu-id="05557-p101">One of the primary tasks of any Skype for Business Online administrator is managing policies. Although you can accomplish some of these tasks in the Office 365 Admin center, other tasks are much quicker and easier in Office 365 PowerShell.</span></span> 

## <a name="before-you-start"></a><span data-ttu-id="05557-107">Vor der Bereitstellung</span><span class="sxs-lookup"><span data-stu-id="05557-107">Before you start</span></span>

<span data-ttu-id="05557-108">Herunterladen und Installieren der [Skype Business Online Connector-Modul](https://www.microsoft.com/en-us/download/details.aspx?id=39366), und starten Sie den Computer neu, wenn Sie aufgefordert werden.</span><span class="sxs-lookup"><span data-stu-id="05557-108">Download and install the [Skype for Business Online Connector module](https://www.microsoft.com/en-us/download/details.aspx?id=39366), and then restart your computer if prompted.</span></span>


## <a name="connect-using-a-skype-for-business-online-administrator-account-name-and-password"></a><span data-ttu-id="05557-109">Eine Verbindung über einen Skype für Business Online-Administrator-Kontonamen und das Kennwort</span><span class="sxs-lookup"><span data-stu-id="05557-109">Connect using a Skype for Business Online administrator account name and password</span></span>

1. <span data-ttu-id="05557-110">Öffnen Sie eine Windows PowerShell-Eingabeaufforderung, und führen Sie die folgenden Befehle aus:</span><span class="sxs-lookup"><span data-stu-id="05557-110">Open a Windows PowerShell command prompt and run the following commands:</span></span> 
    
  ```
  Import-Module SkypeOnlineConnector
  $userCredential = Get-Credential
  $sfbSession = New-CsOnlineSession -Credential $userCredential
  Import-PSSession $sfbSession
  ```

2. <span data-ttu-id="05557-111">Klicken Sie im Dialogfeld **Windows PowerShell anmelden** Geben Sie Ihre Skype für Business Online-Administrator-Kontonamen und das Kennwort ein, und klicken Sie dann auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="05557-111">In the **Windows PowerShell Credential Request** dialog box, type your Skype for Business Online administrator account name and password, and then click **OK**.</span></span>


## <a name="connect-using-a-skype-for-business-online-administrator-account-with-multifactor-authentication"></a><span data-ttu-id="05557-112">Eine Verbindung über einen Skype für Business Online Administratorkonto mit mehrstufige Authentifizierung</span><span class="sxs-lookup"><span data-stu-id="05557-112">Connect using a Skype for Business Online administrator account with multifactor authentication</span></span>

1. <span data-ttu-id="05557-113">Öffnen Sie eine Windows PowerShell-Eingabeaufforderung, und führen Sie die folgenden Befehle aus:</span><span class="sxs-lookup"><span data-stu-id="05557-113">Open a Windows PowerShell command prompt and run the following commands:</span></span>

  ```
  Import-Module SkypeOnlineConnector
  $sfbSession = New-CsOnlineSession
  Import-PSSession $sfbSession
  ```

2. <span data-ttu-id="05557-114">Bei Aufforderung durch den Befehl **New-CsOnlineSession** Geben Sie Ihre Skype Business Online-Administrator Konto ein.</span><span class="sxs-lookup"><span data-stu-id="05557-114">When prompted by the **New-CsOnlineSession** command, enter your Skype for Business Online administrator account name.</span></span>

3. <span data-ttu-id="05557-115">**Melden Sie sich bei Ihrem Konto** im Dialogfeld Geben Sie Ihre Skype Business Online Administratorkennwort ein, und klicken Sie dann auf **Anmelden**.</span><span class="sxs-lookup"><span data-stu-id="05557-115">In the **Sign in to your account** dialog box, type your Skype for Business Online administrator password, and then click **Sign in**.</span></span>

4. <span data-ttu-id="05557-116">Befolgen Sie die Anweisungen im Dialogfeld **Melden Sie sich bei Ihrem Konto** zusätzliche Authentifizierungsinformationen, beispielsweise einen Überprüfungscode bereitstellen, und klicken Sie dann auf **Verify**.</span><span class="sxs-lookup"><span data-stu-id="05557-116">Follow the instructions in the **Sign in to your account** dialog box to provide additional authentication information, such as a verification code, and then click **Verify**.</span></span>

<span data-ttu-id="05557-117">Weitere Informationen hierzu finden Sie in den folgenden Themen:</span><span class="sxs-lookup"><span data-stu-id="05557-117">For more information, see the following topics:</span></span>
  
- [<span data-ttu-id="05557-118">Verwalten von Skype for Business Online-Richtlinien mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="05557-118">Manage Skype for Business Online policies with Office 365 PowerShell</span></span>](manage-skype-for-business-online-policies-with-office-365-powershell.md)
    
- [<span data-ttu-id="05557-119">Zuweisen von benutzerspezifischen Skype for Business Online-Richtlinien mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="05557-119">Assign per-user Skype for Business Online policies with Office 365 PowerShell</span></span>](assign-per-user-skype-for-business-online-policies-with-office-365-powershell.md)
    
## <a name="see-also"></a><span data-ttu-id="05557-120">See also</span><span class="sxs-lookup"><span data-stu-id="05557-120">See also</span></span>

[<span data-ttu-id="05557-121">Verwalten von Office 365 mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="05557-121">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="05557-122">Erste Schritte mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="05557-122">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

