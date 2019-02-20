---
title: Anzeigen des Status der Verzeichnissynchronisierung in Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
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
ms.assetid: 18be3b98-34ae-47be-9337-ab6c3fb372ac
description: Erfahren Sie, wie Sie die Verzeichnissynchronisierung deaktivieren. Sie können den Status auch anzeigen.
ms.openlocfilehash: 4803cbadd17dbc1ee23d019f39144ff1ffaefd9a
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085054"
---
# <a name="view-directory-synchronization-status-in-office-365"></a><span data-ttu-id="f5678-104">Anzeigen des Status der Verzeichnissynchronisierung in Office 365</span><span class="sxs-lookup"><span data-stu-id="f5678-104">View directory synchronization status in Office 365</span></span>
<span data-ttu-id="f5678-105">Wenn Sie Ihr lokales Active Directory mit Azure AD integriert haben, indem Sie Ihre lokale Umgebung mit Office 365 synchronisieren, können Sie auch den Status Ihrer Synchronisierung überprüfen.</span><span class="sxs-lookup"><span data-stu-id="f5678-105">If you have integrated your on-premises Active Directory with Azure AD by synchronizing your on-premises environment with Office 365, you can also check the status of your synchronization.</span></span>
  
## <a name="view-directory-synchronization-status"></a><span data-ttu-id="f5678-106">Anzeigen des Verzeichnis Synchronisierungsstatus</span><span class="sxs-lookup"><span data-stu-id="f5678-106">View directory synchronization status</span></span>
- <span data-ttu-id="f5678-107">Melden Sie sich beim Office 365 Admin Center an, \*\*\*\* und wählen Sie auf der startSeite dirsyncstatus aus.</span><span class="sxs-lookup"><span data-stu-id="f5678-107">Sign in to the Office 365 admin center and choose **DirSync Status** on the home page.</span></span> 
- <span data-ttu-id="f5678-p102">Alternativ können Sie zu **aktiven**Benutzern für **Benutzer** \> wechseln und auf der Seite **aktive Benutzer** **Weitere** \> **Verzeichnissynchronisierung**auswählen. Wählen Sie im Bereich **Verzeichnissynchronisierung** die Option **zu Dirsync-Verwaltung wechseln**aus.</span><span class="sxs-lookup"><span data-stu-id="f5678-p102">Alternately, you can go to **Users** \> **Active users**, and on the **Active users** page, choose **More** \> **Directory synchronization**. On the **Directory Synchronization** pane, choose **Go to DirSync management**.</span></span>
    
## <a name="information-on-the-manage-directory-synchronization-page"></a><span data-ttu-id="f5678-110">Informationen auf der Seite "Verzeichnissynchronisierung verwalten"</span><span class="sxs-lookup"><span data-stu-id="f5678-110">Information on the Manage directory synchronization page</span></span>

<span data-ttu-id="f5678-111">In der folgenden Tabelle sind die Features aufgeführt, auf die Sie auf der Seite Informationen erhalten.</span><span class="sxs-lookup"><span data-stu-id="f5678-111">The following table lists the features you can get information about on the page.</span></span>
  
<span data-ttu-id="f5678-p103">Wenn ein Problem mit der Verzeichnissynchronisierung auftritt, werden die Fehler auch auf dieser Seite aufgeführt. Weitere Informationen zu unterschiedlichen Fehlern, die auftreten können, finden Sie unter [Identifizieren von Verzeichnis Synchronisierungsfehlern in Office 365](identify-directory-synchronization-errors.md).</span><span class="sxs-lookup"><span data-stu-id="f5678-p103">If there is a problem with your directory synchronization, the errors are listed on this page as well. For more information about different errors you might encounter, see [Identify directory synchronization errors in Office 365](identify-directory-synchronization-errors.md).</span></span>
  
|<span data-ttu-id="f5678-114">**Aspekt**</span><span class="sxs-lookup"><span data-stu-id="f5678-114">**Item**</span></span>|<span data-ttu-id="f5678-115">**Zweck**</span><span class="sxs-lookup"><span data-stu-id="f5678-115">**What it's for**</span></span>|
|:-----|:-----|
|<span data-ttu-id="f5678-116">**Domänen überprüft**</span><span class="sxs-lookup"><span data-stu-id="f5678-116">**Domains verified**</span></span> | <span data-ttu-id="f5678-117">Die Anzahl der Domänen in Ihrem Office 365-Mandanten, die Sie überprüft haben.</span><span class="sxs-lookup"><span data-stu-id="f5678-117">Number of domains in your Office 365 tenant that you have verified you own.</span></span> |
|<span data-ttu-id="f5678-118">**Domänen wurden nicht überprüft**</span><span class="sxs-lookup"><span data-stu-id="f5678-118">**Domains not verified**</span></span> | <span data-ttu-id="f5678-119">Domänen, die Sie hinzugefügt, jedoch nicht überprüft haben.</span><span class="sxs-lookup"><span data-stu-id="f5678-119">Domains you have added, but not verified.</span></span> |
|<span data-ttu-id="f5678-120">**Verzeichnissynchronisierung aktiviert**</span><span class="sxs-lookup"><span data-stu-id="f5678-120">**Directory sync enabled**</span></span> |<span data-ttu-id="f5678-p104">True oder false. Gibt an, ob die Verzeichnissynchronisierung aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="f5678-p104">True or False. Specifies whether you have enabled directory sync.</span></span> |
|<span data-ttu-id="f5678-123">**Neueste Verzeichnissynchronisierung**</span><span class="sxs-lookup"><span data-stu-id="f5678-123">**Latest directory sync**</span></span> | <span data-ttu-id="f5678-p105">Zeitpunkt, zu dem die Verzeichnissynchronisierung zuletzt ausgeführt wurde. Zeigt eine Warnung und einen Link zu einem Problembehandlungstool an, wenn die letzte Synchronisierung mehr als drei Tage zurückliegt.</span><span class="sxs-lookup"><span data-stu-id="f5678-p105">Last time directory sync ran. Will display a warning and a link to a troubleshooting tool if the last sync was more than three days ago.</span></span> |
|<span data-ttu-id="f5678-126">**Kennwortsynchronisierung aktiviert**</span><span class="sxs-lookup"><span data-stu-id="f5678-126">**Password sync enabled**</span></span> | <span data-ttu-id="f5678-p106">True oder false. Gibt an, ob eine Kennworthash Synchronisierung zwischen unserem lokalen und Ihrem Office 365-Mandanten statt.</span><span class="sxs-lookup"><span data-stu-id="f5678-p106">True or False. Specifies whether you have password hash sync between our on-premises and your Office 365 tenant.</span></span> |
|<span data-ttu-id="f5678-129">**Letzte Kennwortsynchronisierung**</span><span class="sxs-lookup"><span data-stu-id="f5678-129">**Last Password Sync**</span></span> | <span data-ttu-id="f5678-p107">Zeitpunkt der letzten Kennworthash Synchronisierung. Zeigt eine Warnung und einen Link zu einem Problembehandlungstool an, wenn die letzte Synchronisierung mehr als drei Tage zurückliegt.</span><span class="sxs-lookup"><span data-stu-id="f5678-p107">Last time password hash sync ran. Will display a warning and a link to a troubleshooting tool if the last sync was more than three days ago.</span></span> |
|<span data-ttu-id="f5678-132">**Version des Verzeichnis Synchronisierungs Clients**</span><span class="sxs-lookup"><span data-stu-id="f5678-132">**Directory sync client version**</span></span> | <span data-ttu-id="f5678-133">Enthält einen Download Link, wenn eine neue Version von Azure AD Connect veröffentlicht wurde.</span><span class="sxs-lookup"><span data-stu-id="f5678-133">Contains a download link if a new version of Azure AD Connect has been released.</span></span> |
|<span data-ttu-id="f5678-134">**IDFix-Tool**</span><span class="sxs-lookup"><span data-stu-id="f5678-134">**IDFix Tool**</span></span> | <span data-ttu-id="f5678-135">Download Link zu [IDFix](install-and-run-idfix.md), ein Tool, mit dem Sie lokale Active Directory-Dateien überprüfen können.</span><span class="sxs-lookup"><span data-stu-id="f5678-135">Download link to [IDFix](install-and-run-idfix.md), a tool you can use to check you local Active Directory.</span></span> |
|<span data-ttu-id="f5678-136">**Verzeichnissynchronisierungsdienst Konto**</span><span class="sxs-lookup"><span data-stu-id="f5678-136">**Directory sync service account**</span></span> | <span data-ttu-id="f5678-137">Zeigt den Namen des Office 365-Verzeichnissynchronisierungsdienst Kontos an.</span><span class="sxs-lookup"><span data-stu-id="f5678-137">Displays the name of you Office 365 directory sync service account.</span></span> |