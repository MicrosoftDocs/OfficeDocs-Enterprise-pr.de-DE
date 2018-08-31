---
title: Deaktivieren der verzeichnissynchronisierung für Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
ms.assetid: ee5f861e-bd48-4267-83d1-a4ead4b4a00d
description: Hier erfahren Sie, wie Sie mithilfe von PowerShell für Office 365 verzeichnissynchronisierung deaktivieren
ms.openlocfilehash: f47209dd8b6be47b7ae7a4b63a9fae38c5cb498f
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540955"
---
# <a name="turn-off-directory-synchronization-for-office-365"></a><span data-ttu-id="44752-103">Deaktivieren der verzeichnissynchronisierung für Office 365</span><span class="sxs-lookup"><span data-stu-id="44752-103">Turn off directory synchronization for Office 365</span></span>
<span data-ttu-id="44752-p101">PowerShell können Sie um die verzeichnissynchronisierung zu deaktivieren. Es ist jedoch nicht empfohlen, dass Sie die verzeichnissynchronisierung im Rahmen der Problembehandlung zu deaktivieren. Wenn Sie Hilfe bei der Problembehandlung Directory-Synchronisierung benötigen, finden Sie im Artikel [behoben Probleme mit der verzeichnissynchronisierung für Office 365](fix-problems-with-directory-synchronization.md) .</span><span class="sxs-lookup"><span data-stu-id="44752-p101">You can use PowerShell to turn off directory synchronization. However, it is not recommended that you turn off directory synchronization as a troubleshooting step. If you need assistance with troubleshooting directory synchronization, see the [Fixing problems with directory synchronization for Office 365](fix-problems-with-directory-synchronization.md) article.</span></span> 
  
<span data-ttu-id="44752-107">Der [Kontakt support](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) für Business-Produkte bei Bedarf.</span><span class="sxs-lookup"><span data-stu-id="44752-107">[Contact support](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) for business products if needed.</span></span>
  
## <a name="turn-off-directory-synchronization"></a><span data-ttu-id="44752-108">Deaktivieren der verzeichnissynchronisierung</span><span class="sxs-lookup"><span data-stu-id="44752-108">Turn off directory synchronization</span></span>  
<span data-ttu-id="44752-109">So deaktivieren Sie die verzeichnissynchronisierung:</span><span class="sxs-lookup"><span data-stu-id="44752-109">To turn off Directory synchronization:</span></span>
  
1. <span data-ttu-id="44752-p102">Erstens Installieren der erforderlichen Software und Verbinden mit Office 365-Abonnements. Anweisungen für beide finden Sie unter [Verbinden mit Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=821938).</span><span class="sxs-lookup"><span data-stu-id="44752-p102">First, install the required software and connect to your Office 365 subscription. For instructions for both, see [connect to Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=821938).</span></span>
    
2. <span data-ttu-id="44752-112">Verwenden Sie [Set-MsolDirSyncEnabled](https://go.microsoft.com/fwlink/p/?LinkId=821939) Directory-Synchronisierung zu deaktivieren:</span><span class="sxs-lookup"><span data-stu-id="44752-112">Use [Set-MsolDirSyncEnabled](https://go.microsoft.com/fwlink/p/?LinkId=821939) to disable directory synchronization:</span></span> 
    
  ```
  Set-MsolDirSyncEnabled -EnableDirSync $false
  ```