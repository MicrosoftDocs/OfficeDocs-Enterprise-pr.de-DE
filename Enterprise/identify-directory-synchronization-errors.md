---
title: Anzeigen von verzeichnissynchronisierungsfehlern in Office 365
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
- MBS150
- GPA150
ms.assetid: b4fc07a5-97ea-4ca6-9692-108acab74067
description: Hier erfahren Sie, wie Sie zum Anzeigen von verzeichnissynchronisierungsfehlern in Office 365 Administrationscenter.
ms.openlocfilehash: 62f1135568261eccf0e7e66b78c5aaff966c7281
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540871"
---
# <a name="view-directory-synchronization-errors-in-office-365"></a><span data-ttu-id="212bb-103">Anzeigen von verzeichnissynchronisierungsfehlern in Office 365</span><span class="sxs-lookup"><span data-stu-id="212bb-103">View directory synchronization errors in Office 365</span></span>

<span data-ttu-id="212bb-p101">Sie können verzeichnissynchronisierungsfehlern in Office 365 Administrationscenter anzeigen. Nur die Benutzer Objekt-Fehler werden angezeigt. Fehler mithilfe von PowerShell finden Sie unter [identifizieren Objekte mit DirSyncProvisioningErrors](https://go.microsoft.com/fwlink/p/?LinkId=798300).</span><span class="sxs-lookup"><span data-stu-id="212bb-p101">You can view directory synchronization errors in the Office 365 admin center. Only the User object errors are displayed. To view errors by using PowerShell, see [Identify objects with DirSyncProvisioningErrors](https://go.microsoft.com/fwlink/p/?LinkId=798300).</span></span>

<span data-ttu-id="212bb-107">Nach der Wiedergabe, finden Sie unter [Beheben von Problemen mit der verzeichnissynchronisierung für Office 365](fix-problems-with-directory-synchronization.md) , um identifizierten Probleme zu beheben.</span><span class="sxs-lookup"><span data-stu-id="212bb-107">After viewing, see [fixing problems with directory synchronization for Office 365](fix-problems-with-directory-synchronization.md) to correct any identified issues.</span></span>
  
## <a name="view-directory-synchronization-errors-in-the-admin-center"></a><span data-ttu-id="212bb-108">Anzeigen von verzeichnissynchronisierungsfehlern in der Verwaltungskonsole</span><span class="sxs-lookup"><span data-stu-id="212bb-108">View directory synchronization errors in the admin center</span></span>

<span data-ttu-id="212bb-109">Zum Anzeigen von Fehlern in der Verwaltungskonsole:</span><span class="sxs-lookup"><span data-stu-id="212bb-109">To view any errors in the admin center:</span></span>
  
1. <span data-ttu-id="212bb-110">Melden Sie sich mit Ihrem Geschäfts- oder Schulkonto bei Office 365 an.</span><span class="sxs-lookup"><span data-stu-id="212bb-110">Sign in to Office 365 with your work or school account.</span></span> 
    
2. <span data-ttu-id="212bb-111">Öffnen Sie die [zu Office 365 Administrationscenter](https://support.office.com/article/758befc4-0888-4009-9f14-0d147402fd23).</span><span class="sxs-lookup"><span data-stu-id="212bb-111">Go to the [About the Office 365 admin center](https://support.office.com/article/758befc4-0888-4009-9f14-0d147402fd23).</span></span>
    
3. <span data-ttu-id="212bb-112">Auf **der Homepage** finden Sie die Kachel **Dirsync-Status** .</span><span class="sxs-lookup"><span data-stu-id="212bb-112">On the **Home** page you will see the **DirSync Status** tile.</span></span> 
    
    ![Der Status der Dirsync-Kachel im Admin Center – Vorschau](media/060006e9-de61-49d5-8979-e77cda198e71.png)
  
4. <span data-ttu-id="212bb-114">Wählen Sie auf die Kachel **Dirsync-Status** So wechseln zur der Seite **Directory Sync Status** .</span><span class="sxs-lookup"><span data-stu-id="212bb-114">On the tile, choose **DirSync Status** to go to the **Directory Sync Status** page.</span></span> 
    
    <span data-ttu-id="212bb-115">Am unteren Rand der Seite können Sie sehen, wenn Dirsync-Fehler aufgetreten sind.</span><span class="sxs-lookup"><span data-stu-id="212bb-115">On the bottom of the page you can see if there are DirSync errors.</span></span>
    
    ![Auf der Seite Directory Sync Status können Sie sehen, wenn Dirsync-Objekt Fehler aufgetreten sind](media/882094a3-80d3-4aae-b90b-78b27047974c.png)
  
    <span data-ttu-id="212bb-117">Wählen Sie, **wir Dirsync-Objekt Fehler gefunden** , um eine detaillierte Ansicht Synchronisierungsfehler Verzeichnis zu wechseln.</span><span class="sxs-lookup"><span data-stu-id="212bb-117">Choose **We found DirSync object errors** to go to a detailed view of the directory synchronization errors.</span></span> 
    
    > [!NOTE]
    > <span data-ttu-id="212bb-118">Sie können auch auf der Seite **Dirsync-Fehler** wechseln, wenn Sie auf die Kachel **Dirsync-Status** **wir Dirsync-Objekt Fehler gefunden wählen** .</span><span class="sxs-lookup"><span data-stu-id="212bb-118">You can also go to the **DirSync errors** page if you choose **We found DirSync object errors** on the **DirSync status** tile.</span></span> 
  
![Dirsync-Fehler-Seite](media/a6e302d4-6be7-4e3a-b4b5-81c5a2c02952.png)
  
5. <span data-ttu-id="212bb-120">Wählen Sie auf der Seite **Dirsync-Fehler** der Fehler aus, um die im Detailbereich mit Informationen zu dem Fehler und Tipps zur Problembehebung anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="212bb-120">On the **DirSync errors** page, choose any of the errors listed to display the details pane with information about the error and tips on how to fix it.</span></span> 
