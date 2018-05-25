---
title: DSGVO für Project Server
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Priority
description: Erfahren Sie, wie Sie mit DSGVO-Anforderungen in lokalen Project Server-Installationen umgehen.
ms.openlocfilehash: 6a630dc4cef2c4117e0ba25497f898d0b8da221b
ms.sourcegitcommit: aabd369fc8b397f9e738374d42d8afd18b96d469
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2018
---
# <a name="gdpr-for-project-server"></a><span data-ttu-id="4f7b0-103">DSGVO für Project Server</span><span class="sxs-lookup"><span data-stu-id="4f7b0-103">Operations for Project Server</span></span>

<span data-ttu-id="4f7b0-p101">Project Server verwendet benutzerdefinierte Skripts zum Exportieren und Bearbeiten von Benutzerdaten in Project Web App. Die grundlegende Vorgehensweise sieht folgendermaßen aus:</span><span class="sxs-lookup"><span data-stu-id="4f7b0-p101">Project Server uses custom scripts to export and redact user data in Project Web App. The basic process is:</span></span>

1.  <span data-ttu-id="4f7b0-106">Suchen Sie die Project Web App-Websites in Ihrer Farm.</span><span class="sxs-lookup"><span data-stu-id="4f7b0-106">Find the Project Web App sites in your farm.</span></span>

2.  <span data-ttu-id="4f7b0-107">Suchen Sie auf jeder Website die Projekte, die den Benutzer enthalten.</span><span class="sxs-lookup"><span data-stu-id="4f7b0-107">Find the projects in each site that contain the user.</span></span>

3.  <span data-ttu-id="4f7b0-108">Exportieren und überprüfen Sie die Arten von Daten, die Sie überprüfen möchten.</span><span class="sxs-lookup"><span data-stu-id="4f7b0-108">Export and review the types of data that you want to review.</span></span>

4.  <span data-ttu-id="4f7b0-109">Bearbeiten Sie die Daten bei Bedarf.</span><span class="sxs-lookup"><span data-stu-id="4f7b0-109">Redact data as needed.</span></span>

<span data-ttu-id="4f7b0-110">In den folgenden Artikeln werden diese Schritte ausführlich beschrieben:</span><span class="sxs-lookup"><span data-stu-id="4f7b0-110">These three scenarios are covered in detail in the following articles:</span></span>

- [<span data-ttu-id="4f7b0-111">Exportieren von Benutzerdaten aus Project Server</span><span class="sxs-lookup"><span data-stu-id="4f7b0-111">Export user data from Project Server</span></span>](/Project/export-user-data-from-project-server?toc=/Office365/Enterprise/toc.json)

- [<span data-ttu-id="4f7b0-112">Löschen von Benutzerdaten aus Project Server</span><span class="sxs-lookup"><span data-stu-id="4f7b0-112">Delete user data from Project Server</span></span>](/Project/delete-user-data-from-project-server?toc=/Office365/Enterprise/toc.json)


<span data-ttu-id="4f7b0-113">Beachten Sie, dass Project Server auf SharePoint Server aufbaut und Ereignisse in SharePoint-ULS-Protokollen und in der Verwendungsdatenbank protokolliert.</span><span class="sxs-lookup"><span data-stu-id="4f7b0-113">Note that Project Server is built on top of SharePoint Server and logs events to the SharePoint ULS logs and Usage database.</span></span>
