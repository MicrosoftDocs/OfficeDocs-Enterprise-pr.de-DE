---
title: Benutzererfahrung in einer Umgebung multgeo
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
description: Hier erfahren Sie, wie das Benutzererlebnis SharePoint- und OneDrive in einer Umgebung mit mehreren geografisch.
ms.openlocfilehash: 91837883ef7c970674a500afa4fda9adfafc6d5b
ms.sourcegitcommit: 3f3d2de6c0c5225156cfba01bc980994cd9ae848
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/03/2018
---
# <a name="user-experience-in-a-multi-geo-environment"></a><span data-ttu-id="3148c-103">Benutzererfahrung in einer Umgebung mit mehreren geografisch</span><span class="sxs-lookup"><span data-stu-id="3148c-103">User experience in a multi-geo environment</span></span>

<span data-ttu-id="3148c-104">Hier ist, was Ihre Benutzer in einer OneDrive Multi-Geo-Konfiguration angezeigt werden:</span><span class="sxs-lookup"><span data-stu-id="3148c-104">Here’s what your users will see in a OneDrive Multi-Geo configuration:</span></span>

#### <a name="users-onedrive-for-business-location"></a><span data-ttu-id="3148c-105">OneDrive für Unternehmen des Benutzers</span><span class="sxs-lookup"><span data-stu-id="3148c-105">User’s OneDrive for Business location</span></span>

<span data-ttu-id="3148c-p101">Benutzer müssen ihre OneDrive for Business in ihrer bevorzugten Datenspeicherort bereitgestellt. Wenn ein Benutzer auf eine OneDrive-URL, die einen falschen Geo-Speicherort (beispielsweise eine Textmarke aus einem vorherigen Geo-Speicherort) enthält navigiert, werden sie automatisch an die OneDrive in den entsprechenden Geo-Speicherort umgeleitet.</span><span class="sxs-lookup"><span data-stu-id="3148c-p101">Users will have their OneDrive for Business provisioned in their preferred data location. If a user navigates to a OneDrive URL that contains an incorrect geo-location (such as a bookmark from a previous geo-location), they are automatically redirected to the OneDrive in the appropriate geo-location.</span></span>

#### <a name="sharing"></a><span data-ttu-id="3148c-108">Freigabe</span><span class="sxs-lookup"><span data-stu-id="3148c-108">Sharing</span></span>

<span data-ttu-id="3148c-p102">Die Personenauswahl Erfahrung zeigt alle Benutzer unabhängig vom Standort Geo. Dadurch kann der Benutzer mit einem anderen Benutzer in ihrer gleichen Geo oder andere von Ihrem Mandanten Geo Speicherorte freigeben. Inhalt aus anderen Geo Speicherorten in der Ansicht **für mich freigegeben** in OneDrive für Unternehmen des Benutzers angezeigt, und unabhängig von der Geo-Standort in gehostet ist Single-Sign-On-Erfahrung mit zugegriffen werden können.</span><span class="sxs-lookup"><span data-stu-id="3148c-p102">The People Picker experience shows all users regardless of their geo location. This allows a user to share with another user in their same geo or in any other of your tenant’s geo locations. Content from different geo locations will show up in the **Shared with Me** view in the user's OneDrive for Business and can be accessed with Single-Sign-On experience regardless of which geo-location it is hosted in.</span></span>

#### <a name="office-applications"></a><span data-ttu-id="3148c-112">Office-Anwendungen</span><span class="sxs-lookup"><span data-stu-id="3148c-112">Office applications</span></span>

<span data-ttu-id="3148c-p103">Office-Anwendungen wie Word, Excel und PowerPoint erkennt automatisch die richtige OneDrive for Business Geo-Speicherort für jeden Benutzer, sobald sie anmelden. Benutzer müssen nicht die Geo-spezifischen URL für ihre OneDrive eingeben.</span><span class="sxs-lookup"><span data-stu-id="3148c-p103">Office applications such as Word, Excel, and PowerPoint will automatically detect the correct OneDrive for Business geo-location for each user when they log in. Users do not need to enter the geo-specific URL for their OneDrive.</span></span>

#### <a name="onedrive-for-business-sync-client"></a><span data-ttu-id="3148c-115">OneDrive for Business-Synchronisierungsclient</span><span class="sxs-lookup"><span data-stu-id="3148c-115">OneDrive for Business Sync Client</span></span>

<span data-ttu-id="3148c-116">Die OneDrive for Business-Synchronisierungsclient (Version 17.3.6943.0625 und höher) erkennt automatisch die richtige OneDrive for Business Geo Speicherort für den Benutzer.</span><span class="sxs-lookup"><span data-stu-id="3148c-116">The OneDrive for Business Sync Client (version 17.3.6943.0625 and later) will automatically detect the correct OneDrive for Business geo location for the user.</span></span>

#### <a name="office-365-app-launcher"></a><span data-ttu-id="3148c-117">App-Startfeld für Office 365</span><span class="sxs-lookup"><span data-stu-id="3148c-117">Office 365 app launcher</span></span>

<span data-ttu-id="3148c-p104">Der app Launcher Multi-Geo bekannt ist und leitet jede Kachel, um den entsprechenden Geo Speicherort der Arbeitslast. OneDrive Kachel verweist auf den richtigen Geo-Speicherort, in der Bibliothek des Benutzers OneDrive gehostet wird, während die Kachel "SharePoint" alle Benutzer an den zentralen Standort, zeigen wird wie Teamwebsites gibt es noch gehostet werden.</span><span class="sxs-lookup"><span data-stu-id="3148c-p104">The app launcher is Multi-Geo aware and will direct each tile to the appropriate geo location of the workload. The OneDrive tile points to the correct geo location where the user’s OneDrive library is hosted, while the SharePoint tile will point all users to the central location, as team sites are still hosted there.</span></span>

#### <a name="delve-user-profiles"></a><span data-ttu-id="3148c-120">Beschäftigen von Benutzerprofilen</span><span class="sxs-lookup"><span data-stu-id="3148c-120">Delve User profiles</span></span>

<span data-ttu-id="3148c-p105">Benutzerprofilinformationen ist in Geo-Standort des Benutzers gesteuert. Wenn Sie einen Benutzer auswählen, gelangen Sie zu den entsprechenden Geo-Speicherort für den Benutzer werden, in dem Sie ihren vollständigen Details angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="3148c-p105">User profile information is mastered in the user's geo location. When selecting a user, you will be directed to the appropriate geo location for the user, where you will see their full profile details.</span></span>

<span data-ttu-id="3148c-123">Wenn Delve deaktiviert ist, sehen Sie das klassische Profil in SharePoint auftreten, der kein Multi-Geo bekannt ist.</span><span class="sxs-lookup"><span data-stu-id="3148c-123">If Delve is turned off, you will see the classic profile experience in SharePoint, which is not multi-geo aware.</span></span>

#### <a name="delve"></a><span data-ttu-id="3148c-124">Delve</span><span class="sxs-lookup"><span data-stu-id="3148c-124">Delve</span></span>

<span data-ttu-id="3148c-125">Für Office 365-Benutzer, die in den Instanzen Satelliten sind, wird Multi-Geo ausführlicher behandelt, mit der Einschränkung unterstützt, die mit SharePoint-Blogbeiträge von Benutzern in anderen Regionen, nur für ihre SharePoint-Blogwebsites geschrieben Delve verknüpfen nicht.</span><span class="sxs-lookup"><span data-stu-id="3148c-125">For Office 365 users who are in the satellite instances, Delve Multi-Geo is supported, with the limitation that Delve doesn’t link to SharePoint blog posts written by users in other regions, only to their SharePoint blog sites.</span></span>

#### <a name="search"></a><span data-ttu-id="3148c-126">Suche</span><span class="sxs-lookup"><span data-stu-id="3148c-126">Search</span></span>

<span data-ttu-id="3148c-p106">Jeder Geo-Speicherort hat eigene Suchindex und Suchcenter. Wenn ein Benutzer sucht, wird die Abfrage an alle Geo Speicherorte gesendet, und die zurückgegebenen Ergebnisse zusammengeführt und dann Rank, sodass der Benutzer ruft unified Ergebnisse ab. Benutzer Ergebnisse aus allen geografisch Speicherorten unabhängig von ihren eigenen Geo-Standort zu erhalten. Einzelheiten finden Sie unter [Konfigurieren der Suche für OneDrive for Business Multi-Geo](configure-search-for-multi-geo.md) .</span><span class="sxs-lookup"><span data-stu-id="3148c-p106">Each geo location has its own search index and Search Center. When a user searches, the query is sent to all the geo locations, and the returned results are merged and then ranked so the user gets unified results. Users get results from all geo locations regardless of their own geo location. See [Configure Search for OneDrive for Business Multi-Geo](configure-search-for-multi-geo.md) for specifics.</span></span>

<span data-ttu-id="3148c-131">Die folgenden Search-Clients werden unterstützt:</span><span class="sxs-lookup"><span data-stu-id="3148c-131">The following search clients are supported:</span></span>

-   <span data-ttu-id="3148c-132">OneDrive für Unternehmen</span><span class="sxs-lookup"><span data-stu-id="3148c-132">OneDrive for Business</span></span>

-   <span data-ttu-id="3148c-133">Delve</span><span class="sxs-lookup"><span data-stu-id="3148c-133">Delve</span></span>

-   <span data-ttu-id="3148c-134">SharePoint – Startseite</span><span class="sxs-lookup"><span data-stu-id="3148c-134">SharePoint Home</span></span>

-   <span data-ttu-id="3148c-135">Das Suchcenter</span><span class="sxs-lookup"><span data-stu-id="3148c-135">The Search Center</span></span>

-   <span data-ttu-id="3148c-136">Benutzerdefinierte suchanwendungen, die die SharePoint-Suche-API verwenden</span><span class="sxs-lookup"><span data-stu-id="3148c-136">Custom search applications that use the SharePoint Search API</span></span>

#### <a name="onedrive-ios-and-android"></a><span data-ttu-id="3148c-137">OneDrive iOS und Android (engl.)</span><span class="sxs-lookup"><span data-stu-id="3148c-137">OneDrive iOS and Android</span></span> 

<span data-ttu-id="3148c-p107">Die OneDrive iOS und Android mobiler apps zeigt Ihnen OneDrive-Dateien und Dateien, die Sie unabhängig vom Standort Geo freigegeben. Suche aus OneDrive mobilen apps wird relevante Ergebnisse aus allen geografisch Speicherorten angezeigt. Laden Sie die neueste Version diese Apps.</span><span class="sxs-lookup"><span data-stu-id="3148c-p107">The OneDrive iOS and Android mobile apps will show you your OneDrive files and files shared with you regardless of their geo location. Search from the OneDrive mobile apps will show relevant results from all geo locations. Please download the latest version of these apps.</span></span>

<span data-ttu-id="3148c-141">Weitere Informationen finden Sie unter Verwendung von [OneDrive für iOS](https://support.office.com/article/08d5c5b2-ccc6-40eb-a244-fe3597a3c247) und [Verwendung von OneDrive für Android](https://support.office.com/article/eee1d31c-792d-41d4-8132-f9621b39eb36) .</span><span class="sxs-lookup"><span data-stu-id="3148c-141">See Use [OneDrive on iOS](https://support.office.com/article/08d5c5b2-ccc6-40eb-a244-fe3597a3c247) and [Use OneDrive for Android](https://support.office.com/article/eee1d31c-792d-41d4-8132-f9621b39eb36) for more information.</span></span>

#### <a name="teams-experience"></a><span data-ttu-id="3148c-142">Teams Erfahrung</span><span class="sxs-lookup"><span data-stu-id="3148c-142">Teams Experience</span></span>

<span data-ttu-id="3148c-p108">Teams ist Multi-Geo berücksichtigen. OneDrive und zuletzt aufgerufenen Dateien werden unabhängig davon Geo-Standort des Benutzers angezeigt. @ erwähnungen Arbeit mit Benutzern aus allen Geo-Speicherorte.</span><span class="sxs-lookup"><span data-stu-id="3148c-p108">Teams is multi-geo aware. OneDrive files and recently viewed files are shown regardless of the user’s geo location. @ mentions work with users from all geo-locations.</span></span>
