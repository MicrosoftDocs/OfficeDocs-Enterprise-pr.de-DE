---
title: Verwalten von Microsoft 365-Benutzerkonten, -Lizenzen und -Gruppen mit PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
audience: ITPro
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- PowerShell
- Ent_Office_Other
- seo-marvel-apr2020
ms.assetid: 26b9ff81-93b0-4251-beaf-3c9f1d7c80c8
description: In diesem Artikel erfahren Sie, wie Sie Microsoft 365-Benutzerkonten,-Lizenzen und-Gruppen mit PowerShell verwalten.
ms.openlocfilehash: b5a2d43ad4dee3a70f934f9fc52b93e7c99f3644
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/10/2020
ms.locfileid: "46605881"
---
# <a name="manage-microsoft-365-user-accounts-licenses-and-groups-with-powershell"></a><span data-ttu-id="44d66-103">Verwalten von Microsoft 365-Benutzerkonten, -Lizenzen und -Gruppen mit PowerShell</span><span class="sxs-lookup"><span data-stu-id="44d66-103">Manage Microsoft 365 user accounts, licenses, and groups with PowerShell</span></span>

<span data-ttu-id="44d66-104">*Dieser Artikel gilt sowohl für Microsoft 365 Enterprise als auch für Office 365 Enterprise.*</span><span class="sxs-lookup"><span data-stu-id="44d66-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="44d66-105">Eine der Hauptaufgaben eines beliebigen Microsoft 365-Administrators besteht darin, Benutzerkonten, Lizenzen und Gruppen zu verwalten.</span><span class="sxs-lookup"><span data-stu-id="44d66-105">One of the primary tasks of any Microsoft 365 administrator is managing user accounts, licenses, and groups.</span></span> <span data-ttu-id="44d66-106">Obwohl Sie die meisten Aspekte dieser Aufgaben im Microsoft 365 Admin Center erledigen können, sind andere Aufgaben mit PowerShell viel schneller und einfacher.</span><span class="sxs-lookup"><span data-stu-id="44d66-106">Although you can accomplish most aspects of these tasks in the Microsoft 365 admin center, other tasks are much quicker and easier with PowerShell.</span></span> 

<span data-ttu-id="44d66-107">Weitere Informationen finden Sie in den folgenden Themen.</span><span class="sxs-lookup"><span data-stu-id="44d66-107">For more information, see these topics.</span></span>

## <a name="user-accounts"></a><span data-ttu-id="44d66-108">Benutzerkonten</span><span class="sxs-lookup"><span data-stu-id="44d66-108">User accounts</span></span>

- [<span data-ttu-id="44d66-109">Erstellen von Benutzerkonten</span><span class="sxs-lookup"><span data-stu-id="44d66-109">Create user accounts</span></span>](create-user-accounts-with-office-365-powershell.md)
- [<span data-ttu-id="44d66-110">Anzeigen von Benutzerkonten</span><span class="sxs-lookup"><span data-stu-id="44d66-110">View user accounts</span></span>](view-user-accounts-with-office-365-powershell.md)
- [<span data-ttu-id="44d66-111">Konfigurieren der Eigenschaften von Benutzerkonten</span><span class="sxs-lookup"><span data-stu-id="44d66-111">Configure user account properties</span></span>](configure-user-account-properties-with-office-365-powershell.md)
- [<span data-ttu-id="44d66-112">Zuweisen von Rollen für Benutzerkonten</span><span class="sxs-lookup"><span data-stu-id="44d66-112">Assign roles to user accounts</span></span>](assign-roles-to-user-accounts-with-office-365-powershell.md)
- [<span data-ttu-id="44d66-113">Löschen und Wiederherstellen von Benutzerkonten</span><span class="sxs-lookup"><span data-stu-id="44d66-113">Delete and restore user accounts</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
- [<span data-ttu-id="44d66-114">Blockieren von Benutzerkonten</span><span class="sxs-lookup"><span data-stu-id="44d66-114">Block user accounts</span></span>](block-user-accounts-with-office-365-powershell.md)

## <a name="licenses-and-services"></a><span data-ttu-id="44d66-115">Lizenzen und Dienste</span><span class="sxs-lookup"><span data-stu-id="44d66-115">Licenses and services</span></span>
- [<span data-ttu-id="44d66-116">Anzeigen der Lizenzen und Diensten</span><span class="sxs-lookup"><span data-stu-id="44d66-116">View licenses and services</span></span>](view-licenses-and-services-with-office-365-powershell.md)
- [<span data-ttu-id="44d66-117">Anzeigen von lizenzierte und nicht lizenzierten Benutzern</span><span class="sxs-lookup"><span data-stu-id="44d66-117">View licensed and unlicensed users</span></span>](view-licensed-and-unlicensed-users-with-office-365-powershell.md)
- [<span data-ttu-id="44d66-118">Zuweisen von Lizenzen für Benutzerkonten</span><span class="sxs-lookup"><span data-stu-id="44d66-118">Assign licenses to user accounts</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
- [<span data-ttu-id="44d66-119">Anzeigen von Lizenz- und Dienstdetails für Konten</span><span class="sxs-lookup"><span data-stu-id="44d66-119">View account license and service details</span></span>](view-account-license-and-service-details-with-office-365-powershell.md)
- [<span data-ttu-id="44d66-120">Deaktivieren des Zugriffs auf Dienste</span><span class="sxs-lookup"><span data-stu-id="44d66-120">Disable access to services</span></span>](disable-access-to-services-with-office-365-powershell.md)
  - [<span data-ttu-id="44d66-121">Deaktivieren des Zugriffs auf Sway</span><span class="sxs-lookup"><span data-stu-id="44d66-121">Disable access to Sway</span></span>](disable-access-to-sway-with-office-365-powershell.md)
  - [<span data-ttu-id="44d66-122">Deaktivieren des Zugriffs auf Dienste während des Zuweisens von Benutzerlizenzen</span><span class="sxs-lookup"><span data-stu-id="44d66-122">Disable access to services while assigning user licenses</span></span>](disable-access-to-services-while-assigning-user-licenses.md)
- [<span data-ttu-id="44d66-123">Entfernen von Benutzerlizenzen aus Benutzerkonten</span><span class="sxs-lookup"><span data-stu-id="44d66-123">Remove licenses from user accounts</span></span>](remove-licenses-from-user-accounts-with-office-365-powershell.md)

## <a name="groups"></a><span data-ttu-id="44d66-124">Gruppen</span><span class="sxs-lookup"><span data-stu-id="44d66-124">Groups</span></span>
- [<span data-ttu-id="44d66-125">Verwalten von Gruppenmitgliedschaften</span><span class="sxs-lookup"><span data-stu-id="44d66-125">Maintain group membership</span></span>](maintain-group-membership-with-office-365-powershell.md)
- [<span data-ttu-id="44d66-126">Verwalten von Microsoft 365-Gruppen</span><span class="sxs-lookup"><span data-stu-id="44d66-126">Manage Microsoft 365 groups</span></span>](manage-office-365-groups-with-powershell.md)

