---
title: Verwalten von Benutzerkonten und Lizenzen mit Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
ms.assetid: 26b9ff81-93b0-4251-beaf-3c9f1d7c80c8
description: 'Zusammenfassung: Erfahren Sie, wie Sie Benutzerkonten und Lizenzen mit Office 365 PowerShell verwalten.'
ms.openlocfilehash: 604f0e6926936473f4b8e13546cdf0d7d839c667
ms.sourcegitcommit: 4ef8e113fa20b539de1087422455fc26ff123d55
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "30573889"
---
# <a name="manage-user-accounts-and-licenses-with-office-365-powershell"></a><span data-ttu-id="0a496-103">Verwalten von Benutzerkonten und Lizenzen mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="0a496-103">Manage user accounts and licenses with Office 365 PowerShell</span></span>

 <span data-ttu-id="0a496-104">**Zusammenfassung:** Erfahren Sie, wie Sie Benutzerkonten und Lizenzen mit Office 365 PowerShell verwalten.</span><span class="sxs-lookup"><span data-stu-id="0a496-104">**Summary:** Learn how to manage user accounts and licenses with Office 365 PowerShell.</span></span>
  
<span data-ttu-id="0a496-105">Eine der Hauptaufgaben jedes Office 365-Administrators besteht darin, Benutzerkonten und -lizenzen zu verwalten.</span><span class="sxs-lookup"><span data-stu-id="0a496-105">One of the primary tasks of any Office 365 administrator is managing user accounts and licenses.</span></span> <span data-ttu-id="0a496-106">Obwohl Sie einige dieser Aufgaben in Microsoft 365 Admin Center durchführen können, können andere Aufgaben mit Office 365 PowerShell wesentlich schneller und einfacher durchgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="0a496-106">Although you can accomplish some of these tasks in the Office 365 admin center, other tasks are much quicker and easier with Office 365 PowerShell.</span></span> <span data-ttu-id="0a496-107">Weitere Informationen hierzu finden Sie in den folgenden Themen:</span><span class="sxs-lookup"><span data-stu-id="0a496-107">For more information, see the following topics:</span></span>
  
- [<span data-ttu-id="0a496-108">Anzeigen von Lizenzen und Diensten mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="0a496-108">View licenses and services with Office 365 PowerShell</span></span>](view-licenses-and-services-with-office-365-powershell.md)
    
- [<span data-ttu-id="0a496-109">Anzeigen lizenzierter und nicht lizenzierter Benutzer mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="0a496-109">View licensed and unlicensed users with Office 365 PowerShell</span></span>](view-licensed-and-unlicensed-users-with-office-365-powershell.md)
    
- [<span data-ttu-id="0a496-110">Zuweisen von Lizenzen zu Benutzerkonten mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="0a496-110">Assign licenses to user accounts with Office 365 PowerShell</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="0a496-111">Anzeigen von Lizenz- und Dienstdetails für Konten mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="0a496-111">View account license and service details with Office 365 PowerShell</span></span>](view-account-license-and-service-details-with-office-365-powershell.md)
    
- [<span data-ttu-id="0a496-112">Zuweisen von Rollen zu Benutzerkonten mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="0a496-112">Assign roles to user accounts with Office 365 PowerShell</span></span>](assign-roles-to-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="0a496-113">Deaktivieren des Zugriffs auf Dienste mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="0a496-113">Disable access to services with Office 365 PowerShell</span></span>](disable-access-to-services-with-office-365-powershell.md)
    
- [<span data-ttu-id="0a496-114">Entfernen von Lizenzen von Benutzerkonten mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="0a496-114">Remove licenses from user accounts with Office 365 PowerShell</span></span>](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="0a496-115">Blockieren von Benutzerkonten mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="0a496-115">Block user accounts with Office 365 PowerShell</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="0a496-116">Löschen und Wiederherstellen von Benutzerkonten mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="0a496-116">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="0a496-117">Erstellen von Benutzerkonten mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="0a496-117">Create user accounts with Office 365 PowerShell</span></span>](create-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="0a496-118">Anzeigen von Benutzerkonten mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="0a496-118">View user accounts with Office 365 PowerShell</span></span>](view-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="0a496-119">Konfigurieren von Eigenschaften eines Benutzerkontos mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="0a496-119">Configure user account properties with Office 365 PowerShell</span></span>](configure-user-account-properties-with-office-365-powershell.md)
    

