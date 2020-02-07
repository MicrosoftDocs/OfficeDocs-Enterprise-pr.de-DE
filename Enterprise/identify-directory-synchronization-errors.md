---
title: Anzeigen von Verzeichnis Synchronisierungsfehlern in Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
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
description: Informationen zum Anzeigen von Verzeichnis Synchronisierungsfehlern im Microsoft 365 Admin Center.
ms.openlocfilehash: e270b7f1bc29d952cd07a7b3430a1a9a50b67783
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/07/2020
ms.locfileid: "41840172"
---
# <a name="view-directory-synchronization-errors-in-office-365"></a><span data-ttu-id="11911-103">Anzeigen von Verzeichnis Synchronisierungsfehlern in Office 365</span><span class="sxs-lookup"><span data-stu-id="11911-103">View directory synchronization errors in Office 365</span></span>

<span data-ttu-id="11911-104">Sie können Verzeichnis Synchronisierungsfehler im [Microsoft 365 Admin Center](https://admin.microsoft.com)anzeigen.</span><span class="sxs-lookup"><span data-stu-id="11911-104">You can view directory synchronization errors in the [Microsoft 365 admin center](https://admin.microsoft.com).</span></span> <span data-ttu-id="11911-105">Es werden nur die Fehler des Benutzerobjekts angezeigt.</span><span class="sxs-lookup"><span data-stu-id="11911-105">Only the User object errors are displayed.</span></span> <span data-ttu-id="11911-106">Informationen zum Anzeigen von Fehlern mithilfe von PowerShell finden Sie unter [Identifizieren von Objekten mit DirSyncProvisioningErrors](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency).</span><span class="sxs-lookup"><span data-stu-id="11911-106">To view errors by using PowerShell, see [Identify objects with DirSyncProvisioningErrors](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency).</span></span>

<span data-ttu-id="11911-107">Nach der Anzeige finden Sie unter [Beheben von Problemen mit der Verzeichnissynchronisierung für Office 365](fix-problems-with-directory-synchronization.md) , um identifizierte Probleme zu beheben.</span><span class="sxs-lookup"><span data-stu-id="11911-107">After viewing, see [fixing problems with directory synchronization for Office 365](fix-problems-with-directory-synchronization.md) to correct any identified issues.</span></span>
  
## <a name="view-directory-synchronization-errors-in-the-admin-center"></a><span data-ttu-id="11911-108">Anzeigen von Verzeichnis Synchronisierungsfehlern im Admin Center</span><span class="sxs-lookup"><span data-stu-id="11911-108">View directory synchronization errors in the admin center</span></span>

<span data-ttu-id="11911-109">So zeigen Sie Fehler im Admin Center an:</span><span class="sxs-lookup"><span data-stu-id="11911-109">To view any errors in the admin center:</span></span>
  
1. <span data-ttu-id="11911-110">Melden Sie sich mit Ihrem Geschäfts- oder Schulkonto bei Office 365 an.</span><span class="sxs-lookup"><span data-stu-id="11911-110">Sign in to Office 365 with your work or school account.</span></span> 
    
2. <span data-ttu-id="11911-111">Wechseln Sie zum [Admin Center](https://support.office.com/article/758befc4-0888-4009-9f14-0d147402fd23).</span><span class="sxs-lookup"><span data-stu-id="11911-111">Go to the [About the admin center](https://support.office.com/article/758befc4-0888-4009-9f14-0d147402fd23).</span></span>
    
3. <span data-ttu-id="11911-112">Auf der **Start** Seite wird die Status Kachel **Dirsync** angezeigt.</span><span class="sxs-lookup"><span data-stu-id="11911-112">On the **Home** page you will see the **DirSync Status** tile.</span></span> 
    
    ![Die Kachel "DirSync-Status" in Admin Center Preview](media/060006e9-de61-49d5-8979-e77cda198e71.png)
  
4. <span data-ttu-id="11911-114">Wählen Sie auf der Kachel **Dirsync-Status** aus, um zur Seite **Verzeichnis Synchronisierungsstatus** zu wechseln.</span><span class="sxs-lookup"><span data-stu-id="11911-114">On the tile, choose **DirSync Status** to go to the **Directory Sync Status** page.</span></span> 
    
    <span data-ttu-id="11911-115">Unten auf der Seite können Sie sehen, ob Dirsync-Fehler vorliegen.</span><span class="sxs-lookup"><span data-stu-id="11911-115">On the bottom of the page you can see if there are DirSync errors.</span></span>
    
    ![Auf der Seite Verzeichnis Synchronisierungs Status können Sie sehen, ob es Fehler des Dirsync-Objekts gibt.](media/882094a3-80d3-4aae-b90b-78b27047974c.png)
  
    <span data-ttu-id="11911-117">Wählen Sie die Option **wir haben Dirsync-Objekt Fehler gefunden** , um zu einer detaillierten Ansicht der Verzeichnis Synchronisierungsfehler zu gelangen.</span><span class="sxs-lookup"><span data-stu-id="11911-117">Choose **We found DirSync object errors** to go to a detailed view of the directory synchronization errors.</span></span> 
    
    > [!NOTE]
    > <span data-ttu-id="11911-118">Sie können auch zur Seite **Dirsync-Fehler** wechseln, wenn Sie die Option **Dirsync-Objekt Fehler** auf der **Status Kachel Dirsync** gefunden haben.</span><span class="sxs-lookup"><span data-stu-id="11911-118">You can also go to the **DirSync errors** page if you choose **We found DirSync object errors** on the **DirSync status** tile.</span></span> 
  
![Dirsync-Fehlerseite](media/a6e302d4-6be7-4e3a-b4b5-81c5a2c02952.png)
  
5. <span data-ttu-id="11911-120">Wählen Sie auf der Seite **Dirsync-Fehler** einen der aufgelisteten Fehler aus, um den Detailbereich mit Informationen zum Fehler und Tipps zur Problembehebung anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="11911-120">On the **DirSync errors** page, choose any of the errors listed to display the details pane with information about the error and tips on how to fix it.</span></span> 
