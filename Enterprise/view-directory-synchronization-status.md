---
title: Anzeigen des Status der Verzeichnissynchronisierung in Office 365
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
ms.assetid: 18be3b98-34ae-47be-9337-ab6c3fb372ac
description: Hier erfahren Sie, wie Sie die Verzeichnissynchronisierung deaktivieren. Sie können den Status auch anzeigen.
ms.openlocfilehash: 74e2eee0086e4f8098221f4aaa30d408091a6a0f
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/07/2020
ms.locfileid: "41840982"
---
# <a name="view-directory-synchronization-status-in-office-365"></a><span data-ttu-id="abc7e-104">Anzeigen des Status der Verzeichnissynchronisierung in Office 365</span><span class="sxs-lookup"><span data-stu-id="abc7e-104">View directory synchronization status in Office 365</span></span>

<span data-ttu-id="abc7e-105">Wenn Sie Ihre lokale Active Directory mit Azure AD integriert haben, indem Sie Ihre lokale Umgebung mit Office 365 synchronisieren, können Sie auch den Status der Synchronisierung überprüfen.</span><span class="sxs-lookup"><span data-stu-id="abc7e-105">If you have integrated your on-premises Active Directory with Azure AD by synchronizing your on-premises environment with Office 365, you can also check the status of your synchronization.</span></span>
  
## <a name="view-directory-synchronization-status"></a><span data-ttu-id="abc7e-106">Anzeigen des Status der Verzeichnissynchronisierung</span><span class="sxs-lookup"><span data-stu-id="abc7e-106">View directory synchronization status</span></span>

- <span data-ttu-id="abc7e-107">Melden Sie sich beim [Microsoft 365 Admin Center](https://admin.microsoft.com) an, und wählen Sie auf der Startseite **Dirsync-Status** aus.</span><span class="sxs-lookup"><span data-stu-id="abc7e-107">Sign in to the [Microsoft 365 admin center](https://admin.microsoft.com) and choose **DirSync Status** on the home page.</span></span>
- <span data-ttu-id="abc7e-108">Alternativ können Sie zu " **Benutzer** \> **aktive**Benutzer" wechseln und auf der Seite " **aktive Benutzer** " **Weitere** \> **Verzeichnis Synchronisierungen**auswählen.</span><span class="sxs-lookup"><span data-stu-id="abc7e-108">Alternately, you can go to **Users** \> **Active users**, and on the **Active users** page, choose **More** \> **Directory synchronization**.</span></span> <span data-ttu-id="abc7e-109">Wählen Sie im Bereich **Verzeichnissynchronisierung** die Option **zu Dirsync-Verwaltung wechseln**aus.</span><span class="sxs-lookup"><span data-stu-id="abc7e-109">On the **Directory Synchronization** pane, choose **Go to DirSync management**.</span></span>

## <a name="information-on-the-manage-directory-synchronization-page"></a><span data-ttu-id="abc7e-110">Informationen auf der Seite "Verzeichnissynchronisierung verwalten"</span><span class="sxs-lookup"><span data-stu-id="abc7e-110">Information on the Manage directory synchronization page</span></span>

<span data-ttu-id="abc7e-111">In der folgenden Tabelle sind die Features aufgeführt, auf denen Sie auf der Seite Informationen abrufen können.</span><span class="sxs-lookup"><span data-stu-id="abc7e-111">The following table lists the features you can get information about on the page.</span></span>
  
<span data-ttu-id="abc7e-112">Wenn ein Problem mit der Verzeichnissynchronisierung vorliegt, werden die Fehler auch auf dieser Seite aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="abc7e-112">If there is a problem with your directory synchronization, the errors are listed on this page as well.</span></span> <span data-ttu-id="abc7e-113">Weitere Informationen zu unterschiedlichen Fehlern, die auftreten können, finden Sie unter [Identifizieren von Verzeichnis Synchronisierungsfehlern in Office 365](identify-directory-synchronization-errors.md).</span><span class="sxs-lookup"><span data-stu-id="abc7e-113">For more information about different errors you might encounter, see [Identify directory synchronization errors in Office 365](identify-directory-synchronization-errors.md).</span></span>
  
|<span data-ttu-id="abc7e-114">**Item**</span><span class="sxs-lookup"><span data-stu-id="abc7e-114">**Item**</span></span>|<span data-ttu-id="abc7e-115">**Zweck**</span><span class="sxs-lookup"><span data-stu-id="abc7e-115">**What it's for**</span></span>|
|:-----|:-----|
|<span data-ttu-id="abc7e-116">**Domänen überprüft**</span><span class="sxs-lookup"><span data-stu-id="abc7e-116">**Domains verified**</span></span> | <span data-ttu-id="abc7e-117">Die Anzahl der Domänen in Ihrem Office 365 Mandanten, die Sie selbst überprüft haben.</span><span class="sxs-lookup"><span data-stu-id="abc7e-117">Number of domains in your Office 365 tenant that you have verified you own.</span></span> |
|<span data-ttu-id="abc7e-118">**Domänen nicht überprüft**</span><span class="sxs-lookup"><span data-stu-id="abc7e-118">**Domains not verified**</span></span> | <span data-ttu-id="abc7e-119">Domänen, die Sie hinzugefügt, aber nicht überprüft haben.</span><span class="sxs-lookup"><span data-stu-id="abc7e-119">Domains you have added, but not verified.</span></span> |
|<span data-ttu-id="abc7e-120">**Verzeichnissynchronisierung aktiviert**</span><span class="sxs-lookup"><span data-stu-id="abc7e-120">**Directory sync enabled**</span></span> |<span data-ttu-id="abc7e-121">True oder false.</span><span class="sxs-lookup"><span data-stu-id="abc7e-121">True or False.</span></span> <span data-ttu-id="abc7e-122">Gibt an, ob die Verzeichnissynchronisierung aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="abc7e-122">Specifies whether you have enabled directory sync.</span></span> |
|<span data-ttu-id="abc7e-123">**Neueste Verzeichnissynchronisierung**</span><span class="sxs-lookup"><span data-stu-id="abc7e-123">**Latest directory sync**</span></span> | <span data-ttu-id="abc7e-124">Zeitpunkt der letzten Verzeichnissynchronisierung wurde ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="abc7e-124">Last time directory sync ran.</span></span> <span data-ttu-id="abc7e-125">Zeigt eine Warnung und einen Link zu einem Tool zur Problembehandlung an, wenn die letzte Synchronisierung vor mehr als drei Tagen stattfand.</span><span class="sxs-lookup"><span data-stu-id="abc7e-125">Will display a warning and a link to a troubleshooting tool if the last sync was more than three days ago.</span></span> |
|<span data-ttu-id="abc7e-126">**Kennwortsynchronisierung aktiviert**</span><span class="sxs-lookup"><span data-stu-id="abc7e-126">**Password sync enabled**</span></span> | <span data-ttu-id="abc7e-127">True oder false.</span><span class="sxs-lookup"><span data-stu-id="abc7e-127">True or False.</span></span> <span data-ttu-id="abc7e-128">Gibt an, ob eine Kennworthash Synchronisierung zwischen unserem lokalen und Ihrem Office 365 Mandanten vorliegt.</span><span class="sxs-lookup"><span data-stu-id="abc7e-128">Specifies whether you have password hash sync between our on-premises and your Office 365 tenant.</span></span> |
|<span data-ttu-id="abc7e-129">**Letzte Kennwortsynchronisierung**</span><span class="sxs-lookup"><span data-stu-id="abc7e-129">**Last Password Sync**</span></span> | <span data-ttu-id="abc7e-130">Das letzte Mal, als Password Hash Sync ausgeführt wurde.</span><span class="sxs-lookup"><span data-stu-id="abc7e-130">Last time password hash sync ran.</span></span> <span data-ttu-id="abc7e-131">Zeigt eine Warnung und einen Link zu einem Tool zur Problembehandlung an, wenn die letzte Synchronisierung vor mehr als drei Tagen stattfand.</span><span class="sxs-lookup"><span data-stu-id="abc7e-131">Will display a warning and a link to a troubleshooting tool if the last sync was more than three days ago.</span></span> |
|<span data-ttu-id="abc7e-132">**Version des Verzeichnis Synchronisierungs Clients**</span><span class="sxs-lookup"><span data-stu-id="abc7e-132">**Directory sync client version**</span></span> | <span data-ttu-id="abc7e-133">Enthält einen Download Link, wenn eine neue Version von Azure AD Connect veröffentlicht wurde.</span><span class="sxs-lookup"><span data-stu-id="abc7e-133">Contains a download link if a new version of Azure AD Connect has been released.</span></span> |
|<span data-ttu-id="abc7e-134">**IDFix-Tool**</span><span class="sxs-lookup"><span data-stu-id="abc7e-134">**IDFix Tool**</span></span> | <span data-ttu-id="abc7e-135">Download Link to [IDFix](install-and-run-idfix.md), ein Tool, mit dem Sie lokale Active Directory überprüfen können.</span><span class="sxs-lookup"><span data-stu-id="abc7e-135">Download link to [IDFix](install-and-run-idfix.md), a tool you can use to check you local Active Directory.</span></span> |
|<span data-ttu-id="abc7e-136">**Verzeichnissynchronisierungsdienst Konto**</span><span class="sxs-lookup"><span data-stu-id="abc7e-136">**Directory sync service account**</span></span> | <span data-ttu-id="abc7e-137">Zeigt den Namen Ihres Office 365 Verzeichnissynchronisierungsdienst Kontos an.</span><span class="sxs-lookup"><span data-stu-id="abc7e-137">Displays the name of you Office 365 directory sync service account.</span></span> |