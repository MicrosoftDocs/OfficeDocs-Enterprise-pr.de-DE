---
title: Anzeigen des Status der Directory-Synchronisierung in Office 365
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
ms.assetid: 18be3b98-34ae-47be-9337-ab6c3fb372ac
description: Hier erfahren Sie, wie Sie die verzeichnissynchronisierung deaktivieren. Sie können auch den Status anzeigen.
ms.openlocfilehash: c843fa4d71976cbdd0d6d3d10720e2845b26796c
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541029"
---
# <a name="view-directory-synchronization-status-in-office-365"></a><span data-ttu-id="5f08f-104">Anzeigen des Status der Directory-Synchronisierung in Office 365</span><span class="sxs-lookup"><span data-stu-id="5f08f-104">View directory synchronization status in Office 365</span></span>
<span data-ttu-id="5f08f-105">Wenn Sie Ihre lokale Active Directory mit Azure AD durch die Synchronisierung Ihrer lokalen Umgebung mit Office 365 integriert haben, können Sie auch den Status der Synchronisierung überprüfen.</span><span class="sxs-lookup"><span data-stu-id="5f08f-105">If you have integrated your on-premises Active Directory with Azure AD by synchronizing your on-premises environment with Office 365, you can also check the status of your synchronization.</span></span>
  
## <a name="view-directory-synchronization-status"></a><span data-ttu-id="5f08f-106">Anzeigen des Status Directory-Synchronisierung</span><span class="sxs-lookup"><span data-stu-id="5f08f-106">View directory synchronization status</span></span>
- <span data-ttu-id="5f08f-107">Melden Sie sich bei Office 365 Administrationscenter, und wählen Sie **Dirsync-Status** auf der Homepage.</span><span class="sxs-lookup"><span data-stu-id="5f08f-107">Sign in to the Office 365 admin center and choose **DirSync Status** on the home page.</span></span> 
- <span data-ttu-id="5f08f-p102">Alternativ können Sie für **Benutzer** wechseln \> **aktive Benutzer**, und wählen Sie auf der Seite **aktive Benutzer** **Weitere** \> **Directory-Synchronisierung**. Wählen Sie im Bereich **Directory-Synchronisierung** **Wechseln Sie zur Dirsync-Verwaltung**.</span><span class="sxs-lookup"><span data-stu-id="5f08f-p102">Alternately, you can go to **Users** \> **Active users**, and on the **Active users** page, choose **More** \> **Directory synchronization**. On the **Directory Synchronization** pane, choose **Go to DirSync management**.</span></span>
    
## <a name="information-on-the-manage-directory-synchronization-page"></a><span data-ttu-id="5f08f-110">Informationen auf der Seite verwalten Directory-Synchronisierung</span><span class="sxs-lookup"><span data-stu-id="5f08f-110">Information on the Manage directory synchronization page</span></span>

<span data-ttu-id="5f08f-111">Die folgende Tabelle enthält die Features, die Sie können Informationen auf der Seite zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="5f08f-111">The following table lists the features you can get information about on the page.</span></span>
  
<span data-ttu-id="5f08f-p103">Liegt ein Problem mit der verzeichnissynchronisierung, werden auf dieser Seite auch die Fehler aufgeführt. Weitere Informationen zu anderen Fehlern, die auftreten können, finden Sie unter [Identifizieren von verzeichnissynchronisierungsfehlern in Office 365](identify-directory-synchronization-errors.md).</span><span class="sxs-lookup"><span data-stu-id="5f08f-p103">If there is a problem with your directory synchronization, the errors are listed on this page as well. For more information about different errors you might encounter, see [Identify directory synchronization errors in Office 365](identify-directory-synchronization-errors.md).</span></span>
  
|<span data-ttu-id="5f08f-114">**Element**</span><span class="sxs-lookup"><span data-stu-id="5f08f-114">**Item**</span></span>|<span data-ttu-id="5f08f-115">**Neuigkeiten für**</span><span class="sxs-lookup"><span data-stu-id="5f08f-115">**What it's for**</span></span>|
|:-----|:-----|
|<span data-ttu-id="5f08f-116">**Domänen überprüft**</span><span class="sxs-lookup"><span data-stu-id="5f08f-116">**Domains verified**</span></span> | <span data-ttu-id="5f08f-117">Anzahl von Domänen in Ihrer Office 365-Mandanten, dass Sie Sie überprüft haben besitzen.</span><span class="sxs-lookup"><span data-stu-id="5f08f-117">Number of domains in your Office 365 tenant that you have verified you own.</span></span> |
|<span data-ttu-id="5f08f-118">**Domänen, die nicht überprüft.**</span><span class="sxs-lookup"><span data-stu-id="5f08f-118">**Domains not verified**</span></span> | <span data-ttu-id="5f08f-119">Domänen, die Sie hinzugefügt haben, die aber nicht überprüft.</span><span class="sxs-lookup"><span data-stu-id="5f08f-119">Domains you have added, but not verified.</span></span> |
|<span data-ttu-id="5f08f-120">**Verzeichnissynchronisierung aktiviert**</span><span class="sxs-lookup"><span data-stu-id="5f08f-120">**Directory sync enabled**</span></span> |<span data-ttu-id="5f08f-p104">True oder False. Gibt an, ob Sie die verzeichnissynchronisierung aktiviert haben.</span><span class="sxs-lookup"><span data-stu-id="5f08f-p104">True or False. Specifies whether you have enabled directory sync.</span></span> |
|<span data-ttu-id="5f08f-123">**Neueste Directory-Synchronisierung**</span><span class="sxs-lookup"><span data-stu-id="5f08f-123">**Latest directory sync**</span></span> | <span data-ttu-id="5f08f-p105">Zeitpunkt der letzten Directory Sync ausgeführt wurde. Zeigt eine Warnung und einen Link für Problembehandlungstool die letzte Synchronisierung befand sich mehr als drei Tage zurückliegt.</span><span class="sxs-lookup"><span data-stu-id="5f08f-p105">Last time directory sync ran. Will display a warning and a link to a troubleshooting tool if the last sync was more than three days ago.</span></span> |
|<span data-ttu-id="5f08f-126">**Kennwortsynchronisierung aktiviert**</span><span class="sxs-lookup"><span data-stu-id="5f08f-126">**Password sync enabled**</span></span> | <span data-ttu-id="5f08f-p106">True oder False. Gibt an, ob Sie Kennwort Hash Sync zwischen unsere lokalen und Office 365-Mandanten verfügen.</span><span class="sxs-lookup"><span data-stu-id="5f08f-p106">True or False. Specifies whether you have password hash sync between our on-premises and your Office 365 tenant.</span></span> |
|<span data-ttu-id="5f08f-129">**Letzte Kennwortsynchronisierung**</span><span class="sxs-lookup"><span data-stu-id="5f08f-129">**Last Password Sync**</span></span> | <span data-ttu-id="5f08f-p107">Zeitpunkt der letzten Hash kennwortsynchronisierung ausgeführt wurde. Zeigt eine Warnung und einen Link für Problembehandlungstool die letzte Synchronisierung befand sich mehr als drei Tage zurückliegt.</span><span class="sxs-lookup"><span data-stu-id="5f08f-p107">Last time password hash sync ran. Will display a warning and a link to a troubleshooting tool if the last sync was more than three days ago.</span></span> |
|<span data-ttu-id="5f08f-132">**Directory Sync-Client-version**</span><span class="sxs-lookup"><span data-stu-id="5f08f-132">**Directory sync client version**</span></span> | <span data-ttu-id="5f08f-133">Enthält einen Link herunterladen, wenn eine neue Version des Azure AD-Connect freigegeben wurde.</span><span class="sxs-lookup"><span data-stu-id="5f08f-133">Contains a download link if a new version of Azure AD Connect has been released.</span></span> |
|<span data-ttu-id="5f08f-134">**IDFix-Tool**</span><span class="sxs-lookup"><span data-stu-id="5f08f-134">**IDFix Tool**</span></span> | <span data-ttu-id="5f08f-135">Laden Sie Link, um [IDFix](install-and-run-idfix.md), ein Tool, das Sie verwenden können, um lokale Active Directory zu überprüfen.</span><span class="sxs-lookup"><span data-stu-id="5f08f-135">Download link to [IDFix](install-and-run-idfix.md), a tool you can use to check you local Active Directory.</span></span> |
|<span data-ttu-id="5f08f-136">**Directory Sync-Dienstkonto**</span><span class="sxs-lookup"><span data-stu-id="5f08f-136">**Directory sync service account**</span></span> | <span data-ttu-id="5f08f-137">Zeigt den Namen der Sie Office 365 Directory Sync-Dienstkonto.</span><span class="sxs-lookup"><span data-stu-id="5f08f-137">Displays the name of you Office 365 directory sync service account.</span></span> |