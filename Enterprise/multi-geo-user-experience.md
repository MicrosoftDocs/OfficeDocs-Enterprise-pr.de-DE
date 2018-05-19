---
title: Benutzererfahrung in einer Multi-Geo-Umgebung
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: Dieser Artikel enthält Informationen über die SharePoint- und OneDrive-Benutzererfahrung in einer Multi-Geo-Umgebung.
ms.openlocfilehash: 3c7e4b6802bddc78db016c9c282f5add0c71c491
ms.sourcegitcommit: 75842294e1ba7973728e984f5654a85d5d6172cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2018
---
# <a name="user-experience-in-a-multi-geo-environment"></a><span data-ttu-id="17725-103">Benutzererfahrung in einer Multi-Geo-Umgebung</span><span class="sxs-lookup"><span data-stu-id="17725-103">User experience in a multi-geo environment</span></span>

<span data-ttu-id="17725-104">Im Folgenden wird erläutert, was Benutzern in einer Multi-Geo-Konfiguration in OneDrive angezeigt wird:</span><span class="sxs-lookup"><span data-stu-id="17725-104">Here’s what your users will see in a OneDrive Multi-Geo configuration:</span></span>

#### <a name="users-onedrive-for-business-location"></a><span data-ttu-id="17725-105">OneDrive for Business-Standort des Benutzers</span><span class="sxs-lookup"><span data-stu-id="17725-105">User’s OneDrive for Business location</span></span>

<span data-ttu-id="17725-p101">OneDrive for Business wird Benutzern an dem jeweiligen bevorzugten Datenspeicherort bereitgestellt. Wenn ein Benutzer zu einer OneDrive-URL navigiert, die einen falschen geografischen Strandort enthält (zum Beispiel ein Lesezeichen von einem vorherigen geografischen Standort), werden sie automatisch zur OneDrive-Umgebung an dem entsprechenden geografischen Standort umgeleitet.</span><span class="sxs-lookup"><span data-stu-id="17725-p101">Users will have their OneDrive for Business provisioned in their preferred data location. If a user navigates to a OneDrive URL that contains an incorrect geo-location (such as a bookmark from a previous geo-location), they are automatically redirected to the OneDrive in the appropriate geo-location.</span></span>

#### <a name="sharing"></a><span data-ttu-id="17725-108">Freigabe</span><span class="sxs-lookup"><span data-stu-id="17725-108">Sharing</span></span>

<span data-ttu-id="17725-p102">Die Personenauswahl enthält alle Benutzer unabhängig von ihrem geografischen Standort. So kann ein Benutzer Inhalte für einen Benutzer an dem gleichen geografischen Standort oder an allen anderen geografischen Standorten Ihres Mandanten freigeben. Inhalte von anderen geografischen Standorten werden in der Ansicht **Für mich freigegeben** in OneDrive for Business angezeigt, und mit einmaligem Anmelden kann unabhängig von dem geografischen Standort, an dem sie gehostet werden, auf diese zugegriffen werden.</span><span class="sxs-lookup"><span data-stu-id="17725-p102">The People Picker experience shows all users regardless of their geo location. This allows a user to share with another user in their same geo or in any other of your tenant’s geo locations. Content from different geo locations will show up in the **Shared with Me** view in the user's OneDrive for Business and can be accessed with Single-Sign-On experience regardless of which geo-location it is hosted in.</span></span>

#### <a name="office-applications"></a><span data-ttu-id="17725-112">Office-Anwendungen</span><span class="sxs-lookup"><span data-stu-id="17725-112">Office applications</span></span>

<span data-ttu-id="17725-p103">Office-Anwendungen wie Word, Excel und PowerPoint erkennen bei Anmeldung automatisch den richtigen geografischen OneDrive for Business-Standort für jeden Benutzer. Benutzer müssen nicht die für den geografischen OneDrive-Standort spezifische URL eingeben.</span><span class="sxs-lookup"><span data-stu-id="17725-p103">Office applications such as Word, Excel, and PowerPoint will automatically detect the correct OneDrive for Business geo-location for each user when they log in. Users do not need to enter the geo-specific URL for their OneDrive.</span></span>

#### <a name="onedrive-for-business-sync-client"></a><span data-ttu-id="17725-115">OneDrive for Business-Synchronisierungsclient</span><span class="sxs-lookup"><span data-stu-id="17725-115">OneDrive for Business Sync Client</span></span>

<span data-ttu-id="17725-116">Der OneDrive for Business-Synchronisierungsclient (Version 17.3.6943.0625 und höher) erkennt automatisch den richtigen geografischen OneDrive for Business-Standort für den Benutzer.</span><span class="sxs-lookup"><span data-stu-id="17725-116">The OneDrive for Business Sync Client (version 17.3.6943.0625 and later) will automatically detect the correct OneDrive for Business geo location for the user.</span></span>

#### <a name="office-365-app-launcher"></a><span data-ttu-id="17725-117">App-Startfeld für Office 365</span><span class="sxs-lookup"><span data-stu-id="17725-117">Office 365 app launcher</span></span>

<span data-ttu-id="17725-p104">Das App-Startfeld ist Multi-Geo-fähig. Mit jeder Kachel wird an den entsprechenden geografischen Standort des Workloads weitergeleitet. Die OneDrive-Kachel verweist auf den richtigen geografischen Standort, an dem die OneDrive-Bibliothek des Benutzers gehostet wird, während die SharePoint-Kachel bei allen Benutzern auf den zentralen Standort verweist, da Teamwebsites weiterhin dort gehostet werden.</span><span class="sxs-lookup"><span data-stu-id="17725-p104">The app launcher is Multi-Geo aware and will direct each tile to the appropriate geo location of the workload. The OneDrive tile points to the correct geo location where the user’s OneDrive library is hosted, while the SharePoint tile will point all users to the central location, as team sites are still hosted there.</span></span>

#### <a name="delve-user-profiles"></a><span data-ttu-id="17725-120">Delve-Benutzerprofile</span><span class="sxs-lookup"><span data-stu-id="17725-120">Delve User profiles</span></span>

<span data-ttu-id="17725-p105">Benutzerprofilinformationen werden an dem geografischen Standort des Benutzers verwaltet. Beim Auswählen eines Benutzers werden Sie an den entsprechenden geografischen Standort des Benutzers weitergeleitet, wo vollständige Profilinformationen angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="17725-p105">User profile information is mastered in the user's geo location. When selecting a user, you will be directed to the appropriate geo location for the user, where you will see their full profile details.</span></span>

<span data-ttu-id="17725-123">Wenn Delve deaktiviert ist, sehen Sie das klassische Profil in SharePoint, welches nicht Multi-Geo-fähig ist.</span><span class="sxs-lookup"><span data-stu-id="17725-123">If Delve is turned off, you will see the classic profile experience in SharePoint, which is not multi-geo aware.</span></span>

#### <a name="delve"></a><span data-ttu-id="17725-124">Delve</span><span class="sxs-lookup"><span data-stu-id="17725-124">Delve</span></span>

<span data-ttu-id="17725-125">Für Office 365-Benutzer an den Satellitenstandorten wird Multi-Geo in Delve mit der Einschränkung unterstützt, dass keine Verknüpfung zu SharePoint-Blogbeiträgen von Benutzern in anderen Regionen vorhanden ist, sondern lediglich eine Verknüpfung zu deren SharePoint-Blogwebsites.</span><span class="sxs-lookup"><span data-stu-id="17725-125">For Office 365 users who are in the satellite instances, Delve Multi-Geo is supported, with the limitation that Delve doesn’t link to SharePoint blog posts written by users in other regions, only to their SharePoint blog sites.</span></span>

#### <a name="search"></a><span data-ttu-id="17725-126">Suche</span><span class="sxs-lookup"><span data-stu-id="17725-126">Search</span></span>

<span data-ttu-id="17725-p106">Jeder geografische Standort verfügt über einen eigenen Suchindex und ein Suchcenter. Wenn ein Benutzer eine Suche durchführt, wird die Abfrage an alle geografischen Standorte gesendet, und die zurückgegebenen Ergebnisse werden zusammengeführt und bewertet, sodass der Benutzer einheitliche Ergebnisse erhält. Benutzer erhalten unabhängig von ihrem geografischen Standort Ergebnisse von allen geografischen Standorten. Weitere Informationen dazu finden Sie unter [Konfigurieren der Suche für Multi-Geo in OneDrive for Business](configure-search-for-multi-geo.md).</span><span class="sxs-lookup"><span data-stu-id="17725-p106">Each geo location has its own search index and Search Center. When a user searches, the query is sent to all the geo locations, and the returned results are merged and then ranked so the user gets unified results. Users get results from all geo locations regardless of their own geo location. See [Configure Search for OneDrive for Business Multi-Geo](configure-search-for-multi-geo.md) for specifics.</span></span>

<span data-ttu-id="17725-131">Die folgenden Suchclients werden unterstützt:</span><span class="sxs-lookup"><span data-stu-id="17725-131">The following search clients are supported:</span></span>

-   <span data-ttu-id="17725-132">OneDrive for Business</span><span class="sxs-lookup"><span data-stu-id="17725-132">OneDrive for Business</span></span>

-   <span data-ttu-id="17725-133">Delve</span><span class="sxs-lookup"><span data-stu-id="17725-133">Delve</span></span>

-   <span data-ttu-id="17725-134">SharePoint-Homepage</span><span class="sxs-lookup"><span data-stu-id="17725-134">SharePoint Home</span></span>

-   <span data-ttu-id="17725-135">Das Suchcenter</span><span class="sxs-lookup"><span data-stu-id="17725-135">The Search Center</span></span>

-   <span data-ttu-id="17725-136">Benutzerdefinierte Suchanwendungen, die die SharePoint-Suche-API verwenden</span><span class="sxs-lookup"><span data-stu-id="17725-136">Custom search applications that use the SharePoint Search API</span></span>

#### <a name="onedrive-ios-and-android"></a><span data-ttu-id="17725-137">OneDrive unter IOS und Android</span><span class="sxs-lookup"><span data-stu-id="17725-137">OneDrive iOS and Android</span></span> 

<span data-ttu-id="17725-p107">In den mobilen OneDrive-Apps für iOS und Android werden Ihre OneDrive-Dateien und für Sie freigegebene Dateien unabhängig vom geografischen Standort angezeigt. Die Suche in den mobilen OneDrive-Apps geben relevante Ergebnisse von allen geografischen Standorten zurück. Laden Sie die neueste Version dieser Apps herunter.</span><span class="sxs-lookup"><span data-stu-id="17725-p107">The OneDrive iOS and Android mobile apps will show you your OneDrive files and files shared with you regardless of their geo location. Search from the OneDrive mobile apps will show relevant results from all geo locations. Please download the latest version of these apps.</span></span>

<span data-ttu-id="17725-141">Weitere Informationen finden Sie unter Verwenden von [OneDrive unter iOS](https://support.office.com/article/08d5c5b2-ccc6-40eb-a244-fe3597a3c247) und [OneDrive unter Android](https://support.office.com/article/eee1d31c-792d-41d4-8132-f9621b39eb36).</span><span class="sxs-lookup"><span data-stu-id="17725-141">See Use [OneDrive on iOS](https://support.office.com/article/08d5c5b2-ccc6-40eb-a244-fe3597a3c247) and [Use OneDrive for Android](https://support.office.com/article/eee1d31c-792d-41d4-8132-f9621b39eb36) for more information.</span></span>

#### <a name="teams-experience"></a><span data-ttu-id="17725-142">Teams-Erfahrung</span><span class="sxs-lookup"><span data-stu-id="17725-142">Teams Experience</span></span>

<span data-ttu-id="17725-p108">Teams sind Multi-Geo-fähig. OneDrive-Dateien und zuletzt verwendete Dateien werden unabhängig vom geografischen Standort des Benutzers angezeigt. @-Erwähnungen funktionieren mit Benutzern von allen geografischen Standorten.</span><span class="sxs-lookup"><span data-stu-id="17725-p108">Teams is multi-geo aware. OneDrive files and recently viewed files are shown regardless of the user’s geo location. @ mentions work with users from all geo-locations.</span></span>
