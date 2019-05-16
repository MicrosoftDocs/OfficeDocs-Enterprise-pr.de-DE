---
title: Anzeigen von Verzeichnis Synchronisierungsfehlern in Office 365
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
- MBS150
- GPA150
ms.assetid: b4fc07a5-97ea-4ca6-9692-108acab74067
description: Informationen zum Anzeigen von Verzeichnis Synchronisierungsfehlern in Microsoft 365 Admin Center.
ms.openlocfilehash: b1cda68590131967ea2fe91506c8e71769f4c32b
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "34067521"
---
# <a name="view-directory-synchronization-errors-in-office-365"></a><span data-ttu-id="3ae61-103">Anzeigen von Verzeichnis Synchronisierungsfehlern in Office 365</span><span class="sxs-lookup"><span data-stu-id="3ae61-103">View directory synchronization errors in Office 365</span></span>

<span data-ttu-id="3ae61-104">Verzeichnis Synchronisierungsfehler können im [Microsoft 365 Admin Center](https://admin.microsoft.com)angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="3ae61-104">You can view directory synchronization errors in the [Microsoft 365 admin center](https://admin.microsoft.com).</span></span> <span data-ttu-id="3ae61-105">Nur die Fehler des Benutzerobjekts werden angezeigt.</span><span class="sxs-lookup"><span data-stu-id="3ae61-105">Only the User object errors are displayed.</span></span> <span data-ttu-id="3ae61-106">Informationen zum Anzeigen von Fehlern mithilfe von PowerShell finden Sie unter [Identifizieren von Objekten mit DirSyncProvisioningErrors](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency).</span><span class="sxs-lookup"><span data-stu-id="3ae61-106">To view errors by using PowerShell, see [Identify objects with DirSyncProvisioningErrors](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency).</span></span>

<span data-ttu-id="3ae61-107">Weitere Informationen finden Sie unter [Beheben von Problemen mit der Verzeichnissynchronisierung für Office 365](fix-problems-with-directory-synchronization.md) , um erkannte Probleme zu beheben.</span><span class="sxs-lookup"><span data-stu-id="3ae61-107">After viewing, see [fixing problems with directory synchronization for Office 365](fix-problems-with-directory-synchronization.md) to correct any identified issues.</span></span>
  
## <a name="view-directory-synchronization-errors-in-the-admin-center"></a><span data-ttu-id="3ae61-108">Anzeigen von Verzeichnis Synchronisierungsfehlern im Admin Center</span><span class="sxs-lookup"><span data-stu-id="3ae61-108">View directory synchronization errors in the admin center</span></span>

<span data-ttu-id="3ae61-109">So zeigen Sie Fehler im Admin Center an:</span><span class="sxs-lookup"><span data-stu-id="3ae61-109">To view any errors in the admin center:</span></span>
  
1. <span data-ttu-id="3ae61-110">Melden Sie sich mit Ihrem Geschäfts- oder Schulkonto bei Office 365 an.</span><span class="sxs-lookup"><span data-stu-id="3ae61-110">Sign in to Office 365 with your work or school account.</span></span> 
    
2. <span data-ttu-id="3ae61-111">Wechseln Sie zum [Admin Center](https://support.office.com/article/758befc4-0888-4009-9f14-0d147402fd23).</span><span class="sxs-lookup"><span data-stu-id="3ae61-111">Go to the [About the admin center](https://support.office.com/article/758befc4-0888-4009-9f14-0d147402fd23).</span></span>
    
3. <span data-ttu-id="3ae61-112">Auf der **Start** Seite sehen Sie die Dirsync- **Status** Kachel.</span><span class="sxs-lookup"><span data-stu-id="3ae61-112">On the **Home** page you will see the **DirSync Status** tile.</span></span> 
    
    ![Die Dirsync-Status Kachel in der Admin Center-Vorschau](media/060006e9-de61-49d5-8979-e77cda198e71.png)
  
4. <span data-ttu-id="3ae61-114">Wählen Sie auf der Kachel **Dirsync Status** aus, um zur Seite **Verzeichnis Synchronisierungsstatus** zu wechseln.</span><span class="sxs-lookup"><span data-stu-id="3ae61-114">On the tile, choose **DirSync Status** to go to the **Directory Sync Status** page.</span></span> 
    
    <span data-ttu-id="3ae61-115">Am unteren Rand der Seite sehen Sie, ob es Dirsync-Fehler gibt.</span><span class="sxs-lookup"><span data-stu-id="3ae61-115">On the bottom of the page you can see if there are DirSync errors.</span></span>
    
    ![Auf der Seite Verzeichnis Synchronisierungs Status wird angezeigt, ob Dirsync-Objekt Fehler vorliegen.](media/882094a3-80d3-4aae-b90b-78b27047974c.png)
  
    <span data-ttu-id="3ae61-117">Wählen Sie "Dirsync- **Objekt Fehler** " aus, um zu einer detaillierten Ansicht der Verzeichnis Synchronisierungsfehler zu wechseln.</span><span class="sxs-lookup"><span data-stu-id="3ae61-117">Choose **We found DirSync object errors** to go to a detailed view of the directory synchronization errors.</span></span> 
    
    > [!NOTE]
    > <span data-ttu-id="3ae61-118">Sie können auch auf die Seite **Dirsync Errors** wechseln, wenn Sie sich für Dirsync- **Objekt Fehler** auf der Dirsync- **Status** Kachel entschieden haben.</span><span class="sxs-lookup"><span data-stu-id="3ae61-118">You can also go to the **DirSync errors** page if you choose **We found DirSync object errors** on the **DirSync status** tile.</span></span> 
  
![Seite "Dirsync-Fehler"](media/a6e302d4-6be7-4e3a-b4b5-81c5a2c02952.png)
  
5. <span data-ttu-id="3ae61-120">Wählen Sie auf der Seite Dirsync- **Fehler** einen der aufgeführten Fehler aus, um den Detailbereich mit Informationen zu dem Fehler anzuzeigen, und Tipps zur Problembehebung.</span><span class="sxs-lookup"><span data-stu-id="3ae61-120">On the **DirSync errors** page, choose any of the errors listed to display the details pane with information about the error and tips on how to fix it.</span></span> 
