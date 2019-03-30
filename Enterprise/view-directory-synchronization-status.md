---
title: Anzeigen des Status der Verzeichnissynchronisierung in Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
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
ms.openlocfilehash: a38b723db6f5bafe246e774972ca89c65bc9c846
ms.sourcegitcommit: 29f937b7430c708c9dbec23bdc4089e86c37c225
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2019
ms.locfileid: "31001568"
---
# <a name="view-directory-synchronization-status-in-office-365"></a><span data-ttu-id="57ef5-104">Anzeigen des Status der Verzeichnissynchronisierung in Office 365</span><span class="sxs-lookup"><span data-stu-id="57ef5-104">View directory synchronization status in Office 365</span></span>

<span data-ttu-id="57ef5-105">Wenn Sie Ihr lokales Active Directory mit Azure AD integriert haben, indem Sie Ihre lokale Umgebung mit Office 365 synchronisieren, können Sie auch den Status Ihrer Synchronisierung überprüfen.</span><span class="sxs-lookup"><span data-stu-id="57ef5-105">If you have integrated your on-premises Active Directory with Azure AD by synchronizing your on-premises environment with Office 365, you can also check the status of your synchronization.</span></span>
  
## <a name="view-directory-synchronization-status"></a><span data-ttu-id="57ef5-106">Anzeigen des Verzeichnis Synchronisierungsstatus</span><span class="sxs-lookup"><span data-stu-id="57ef5-106">View directory synchronization status</span></span>

- <span data-ttu-id="57ef5-107">Melden Sie sich beim [Microsoft 365 Admin Center](https://admin.microsoft.com) an, \*\*\*\* und wählen Sie auf der Startseite dirsyncstatus aus.</span><span class="sxs-lookup"><span data-stu-id="57ef5-107">Sign in to the [Microsoft 365 admin center](https://admin.microsoft.com) and choose **DirSync Status** on the home page.</span></span>
- <span data-ttu-id="57ef5-108">Alternativ können Sie zu **aktiven**Benutzern für **Benutzer** \> wechseln und auf der Seite **aktive Benutzer** **Weitere** \> **Verzeichnissynchronisierung**auswählen.</span><span class="sxs-lookup"><span data-stu-id="57ef5-108">Alternately, you can go to **Users** \> **Active users**, and on the **Active users** page, choose **More** \> **Directory synchronization**.</span></span> <span data-ttu-id="57ef5-109">Wählen Sie im Bereich **Verzeichnissynchronisierung** die Option **zu Dirsync-Verwaltung wechseln**aus.</span><span class="sxs-lookup"><span data-stu-id="57ef5-109">On the **Directory Synchronization** pane, choose **Go to DirSync management**.</span></span>

## <a name="information-on-the-manage-directory-synchronization-page"></a><span data-ttu-id="57ef5-110">Informationen auf der Seite "Verzeichnissynchronisierung verwalten"</span><span class="sxs-lookup"><span data-stu-id="57ef5-110">Information on the Manage directory synchronization page</span></span>

<span data-ttu-id="57ef5-111">In der folgenden Tabelle sind die Features aufgeführt, auf die Sie auf der Seite Informationen erhalten.</span><span class="sxs-lookup"><span data-stu-id="57ef5-111">The following table lists the features you can get information about on the page.</span></span>
  
<span data-ttu-id="57ef5-112">Wenn ein Problem mit der Verzeichnissynchronisierung auftritt, werden die Fehler auch auf dieser Seite aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="57ef5-112">If there is a problem with your directory synchronization, the errors are listed on this page as well.</span></span> <span data-ttu-id="57ef5-113">Weitere Informationen zu unterschiedlichen Fehlern, die auftreten können, finden Sie unter [Identifizieren von Verzeichnis Synchronisierungsfehlern in Office 365](identify-directory-synchronization-errors.md).</span><span class="sxs-lookup"><span data-stu-id="57ef5-113">For more information about different errors you might encounter, see [Identify directory synchronization errors in Office 365](identify-directory-synchronization-errors.md).</span></span>
  
|<span data-ttu-id="57ef5-114">**Element**</span><span class="sxs-lookup"><span data-stu-id="57ef5-114">**Item**</span></span>|<span data-ttu-id="57ef5-115">**Zweck**</span><span class="sxs-lookup"><span data-stu-id="57ef5-115">**What it's for**</span></span>|
|:-----|:-----|
|<span data-ttu-id="57ef5-116">**Domänen überprüft**</span><span class="sxs-lookup"><span data-stu-id="57ef5-116">**Domains verified**</span></span> | <span data-ttu-id="57ef5-117">Die Anzahl der Domänen in Ihrem Office 365-Mandanten, die Sie überprüft haben.</span><span class="sxs-lookup"><span data-stu-id="57ef5-117">Number of domains in your Office 365 tenant that you have verified you own.</span></span> |
|<span data-ttu-id="57ef5-118">**Domänen wurden nicht überprüft**</span><span class="sxs-lookup"><span data-stu-id="57ef5-118">**Domains not verified**</span></span> | <span data-ttu-id="57ef5-119">Domänen, die Sie hinzugefügt, jedoch nicht überprüft haben.</span><span class="sxs-lookup"><span data-stu-id="57ef5-119">Domains you have added, but not verified.</span></span> |
|<span data-ttu-id="57ef5-120">**Verzeichnissynchronisierung aktiviert**</span><span class="sxs-lookup"><span data-stu-id="57ef5-120">**Directory sync enabled**</span></span> |<span data-ttu-id="57ef5-121">True oder false.</span><span class="sxs-lookup"><span data-stu-id="57ef5-121">True or False.</span></span> <span data-ttu-id="57ef5-122">Gibt an, ob die Verzeichnissynchronisierung aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="57ef5-122">Specifies whether you have enabled directory sync.</span></span> |
|<span data-ttu-id="57ef5-123">**Neueste Verzeichnissynchronisierung**</span><span class="sxs-lookup"><span data-stu-id="57ef5-123">**Latest directory sync**</span></span> | <span data-ttu-id="57ef5-124">Zeitpunkt, zu dem die Verzeichnissynchronisierung zuletzt ausgeführt wurde.</span><span class="sxs-lookup"><span data-stu-id="57ef5-124">Last time directory sync ran.</span></span> <span data-ttu-id="57ef5-125">Zeigt eine Warnung und einen Link zu einem Problembehandlungstool an, wenn die letzte Synchronisierung mehr als drei Tage zurückliegt.</span><span class="sxs-lookup"><span data-stu-id="57ef5-125">Will display a warning and a link to a troubleshooting tool if the last sync was more than three days ago.</span></span> |
|<span data-ttu-id="57ef5-126">**Kennwortsynchronisierung aktiviert**</span><span class="sxs-lookup"><span data-stu-id="57ef5-126">**Password sync enabled**</span></span> | <span data-ttu-id="57ef5-127">True oder false.</span><span class="sxs-lookup"><span data-stu-id="57ef5-127">True or False.</span></span> <span data-ttu-id="57ef5-128">Gibt an, ob eine Kennworthash Synchronisierung zwischen unserem lokalen und Ihrem Office 365-Mandanten statt.</span><span class="sxs-lookup"><span data-stu-id="57ef5-128">Specifies whether you have password hash sync between our on-premises and your Office 365 tenant.</span></span> |
|<span data-ttu-id="57ef5-129">**Letzte Kennwortsynchronisierung**</span><span class="sxs-lookup"><span data-stu-id="57ef5-129">**Last Password Sync**</span></span> | <span data-ttu-id="57ef5-130">Zeitpunkt der letzten Kennworthash Synchronisierung.</span><span class="sxs-lookup"><span data-stu-id="57ef5-130">Last time password hash sync ran.</span></span> <span data-ttu-id="57ef5-131">Zeigt eine Warnung und einen Link zu einem Problembehandlungstool an, wenn die letzte Synchronisierung mehr als drei Tage zurückliegt.</span><span class="sxs-lookup"><span data-stu-id="57ef5-131">Will display a warning and a link to a troubleshooting tool if the last sync was more than three days ago.</span></span> |
|<span data-ttu-id="57ef5-132">**Version des Verzeichnis Synchronisierungs Clients**</span><span class="sxs-lookup"><span data-stu-id="57ef5-132">**Directory sync client version**</span></span> | <span data-ttu-id="57ef5-133">Enthält einen Download Link, wenn eine neue Version von Azure AD Connect veröffentlicht wurde.</span><span class="sxs-lookup"><span data-stu-id="57ef5-133">Contains a download link if a new version of Azure AD Connect has been released.</span></span> |
|<span data-ttu-id="57ef5-134">**IDFix-Tool**</span><span class="sxs-lookup"><span data-stu-id="57ef5-134">**IDFix Tool**</span></span> | <span data-ttu-id="57ef5-135">Download Link zu [IDFix](install-and-run-idfix.md), ein Tool, mit dem Sie lokale Active Directory-Dateien überprüfen können.</span><span class="sxs-lookup"><span data-stu-id="57ef5-135">Download link to [IDFix](install-and-run-idfix.md), a tool you can use to check you local Active Directory.</span></span> |
|<span data-ttu-id="57ef5-136">**Verzeichnissynchronisierungsdienst Konto**</span><span class="sxs-lookup"><span data-stu-id="57ef5-136">**Directory sync service account**</span></span> | <span data-ttu-id="57ef5-137">Zeigt den Namen des Office 365-Verzeichnissynchronisierungsdienst Kontos an.</span><span class="sxs-lookup"><span data-stu-id="57ef5-137">Displays the name of you Office 365 directory sync service account.</span></span> |