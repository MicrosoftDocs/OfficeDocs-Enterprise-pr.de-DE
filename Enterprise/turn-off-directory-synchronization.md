---
title: Deaktivieren der Verzeichnissynchronisierung für Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED150
ms.assetid: ee5f861e-bd48-4267-83d1-a4ead4b4a00d
description: Informationen zum Deaktivieren der Verzeichnissynchronisierung für Office 365 mithilfe von PowerShell
ms.openlocfilehash: efee8b216d63f32ac64a559aca3bcb55b0a933c1
ms.sourcegitcommit: 3ed7b1eacf009581a9897524c181afa3e555ad3f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/28/2020
ms.locfileid: "41570892"
---
# <a name="turn-off-directory-synchronization-for-office-365"></a><span data-ttu-id="fa7cc-103">Deaktivieren der Verzeichnissynchronisierung für Office 365</span><span class="sxs-lookup"><span data-stu-id="fa7cc-103">Turn off directory synchronization for Office 365</span></span>
<span data-ttu-id="fa7cc-104">Sie können die Verzeichnissynchronisierung mithilfe von PowerShell deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="fa7cc-104">You can use PowerShell to turn off directory synchronization.</span></span> <span data-ttu-id="fa7cc-105">Es wird jedoch nicht empfohlen, die Verzeichnissynchronisierung als Schritt zur Problembehandlung zu deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="fa7cc-105">However, it is not recommended that you turn off directory synchronization as a troubleshooting step.</span></span> <span data-ttu-id="fa7cc-106">Wenn Sie Unterstützung bei der Problembehandlung bei der Verzeichnissynchronisierung benötigen, lesen Sie die Informationen unter [Beheben von Problemen mit der Verzeichnissynchronisierung für Office 365](fix-problems-with-directory-synchronization.md) Artikel.</span><span class="sxs-lookup"><span data-stu-id="fa7cc-106">If you need assistance with troubleshooting directory synchronization, see the [Fixing problems with directory synchronization for Office 365](fix-problems-with-directory-synchronization.md) article.</span></span> 
  
<span data-ttu-id="fa7cc-107">[Wenden Sie sich](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) bei Bedarf an den Support für Business-Produkte.</span><span class="sxs-lookup"><span data-stu-id="fa7cc-107">[Contact support](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) for business products if needed.</span></span>
  
## <a name="turn-off-directory-synchronization"></a><span data-ttu-id="fa7cc-108">Deaktivieren der Verzeichnissynchronisierung</span><span class="sxs-lookup"><span data-stu-id="fa7cc-108">Turn off directory synchronization</span></span>  
<span data-ttu-id="fa7cc-109">So deaktivieren Sie die Verzeichnissynchronisierung:</span><span class="sxs-lookup"><span data-stu-id="fa7cc-109">To turn off Directory synchronization:</span></span>
  
1. <span data-ttu-id="fa7cc-110">Installieren Sie zunächst die erforderliche Software, und stellen Sie eine Verbindung mit Ihrem Office 365 Abonnement her.</span><span class="sxs-lookup"><span data-stu-id="fa7cc-110">First, install the required software and connect to your Office 365 subscription.</span></span> <span data-ttu-id="fa7cc-111">Anweisungen finden Sie unter [Connect with the Microsoft Azure Active Directory Module for Windows PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="fa7cc-111">For instructions, see [Connect with the Microsoft Azure Active Directory Module for Windows PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>
    
2. <span data-ttu-id="fa7cc-112">Verwenden Sie die [Option "MsolDirSyncEnabled](https://go.microsoft.com/fwlink/p/?LinkId=821939) ", um die Verzeichnissynchronisierung zu deaktivieren:</span><span class="sxs-lookup"><span data-stu-id="fa7cc-112">Use [Set-MsolDirSyncEnabled](https://go.microsoft.com/fwlink/p/?LinkId=821939) to disable directory synchronization:</span></span> 
    
  ```powershell
  Set-MsolDirSyncEnabled -EnableDirSync $false
  ```
