---
title: Erstellen Sie eine Office 365-Gruppe mit einem bestimmten PLD
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: Erfahren Sie, wie Die eine Office 365-Gruppe mit einem bestimmten bevorzugten Datenspeicherort in einer Multi-Geo-Umgebung erstellen.
ms.openlocfilehash: a46a34d9fd5be9b3acda5ee3859f4eed08797b7c
ms.sourcegitcommit: 8ba20f1b1839630a199585da0c83aaebd1ceb9fc
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "30934007"
---
# <a name="create-an-office-365-group-with-a-specific-pdl"></a><span data-ttu-id="179e4-103">Erstellen Sie eine Office 365-Gruppe mit einem bestimmten PLD</span><span class="sxs-lookup"><span data-stu-id="179e4-103">Create an Office 365 Group with a specific PDL</span></span>

<span data-ttu-id="179e4-104">Wenn ein Benutzer in einer Multi-Geo-Umgebung eine Office 365-Gruppe erstellt, wird als bevorzugter Datenspeicherort der Gruppe automatisch der dieses Benutzers festgelegt.</span><span class="sxs-lookup"><span data-stu-id="179e4-104">When users in a multi-geo environment create an Office 365 Group, the group preferred data location is automatically set to that of the user.</span></span> <span data-ttu-id="179e4-105">Wenn Sie eine Gruppe mit einem bestimmten PLD erstellen möchten, können Sie dies unter Verwendung von Exchange Online New-UnifiedGroup Microsoft PowerShell cmdlet vornehmen.</span><span class="sxs-lookup"><span data-stu-id="179e4-105">If you need to create a group with a specific PDL, you can do that using the Exchange Online New-UnifiedGroup Microsoft PowerShell cmdlet.</span></span> <span data-ttu-id="179e4-106">Wenn Sie dies tun, werden das zugewiesene Gruppenpostfach und die SharePoint-Website für die Gruppe der angegebenen Verteilerliste an diesem bestimmten PLD bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="179e4-106">When you do this, both the group mailbox and SharePoint site associated with the group will be provisioned in the specified PDL.</span></span>

<span data-ttu-id="179e4-107">Sie müssen ein globaler Administrator, ein SharePoint Onlineadministrator oder ein Exchange-Onlineadministrator sein, um dies ausführen zu können.</span><span class="sxs-lookup"><span data-stu-id="179e4-107">You must be a global administrator or a SharePoint Online or Exchange Online administrator to do this.</span></span>

<span data-ttu-id="179e4-108">Um eine Office 365-Gruppe mit dem von Ihnen festgelegten PLD zu erstellen, stellen Sie eine Verbindung zu Exchange Online PowerShell her und geben Sie den Parameter *-MailBoxRegion* mit dem Code des Geo-Standorts weiter.</span><span class="sxs-lookup"><span data-stu-id="179e4-108">To create an Office 365 Group with the PDL that you specify, connect to Exchange Online PowerShell and pass the parameter *-MailBoxRegion* with the geo location code.</span></span>

<span data-ttu-id="179e4-109">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="179e4-109">For example:</span></span> 

```PowerShell
New-UnifiedGroup -DisplayName MultiGeoEUR -Alias "MultiGeoEUR" -AccessType Public -MailboxRegion EUR 
```

![Screenshot des New-UnifiedGroup PowerShell cmdlet mit Syntax](media/multi-geo-new-group-with-pdl-powershell.png)

<span data-ttu-id="179e4-111">Beachten Sie, dass die Bereitstellung von SharePoint-Gruppenseiten nach Bedarf erfolgt.</span><span class="sxs-lookup"><span data-stu-id="179e4-111">Note that SharePoint group site provisioning is on-demand.</span></span> <span data-ttu-id="179e4-112">Die Seite wird bereitgestellt, wenn ein Gruppenbesitzer oder -mitglied zum ersten Mal auf diese zugreift.</span><span class="sxs-lookup"><span data-stu-id="179e4-112">The site will be provisioned the first time a group owner or member attempts to access it.</span></span>

## <a name="geo-location-codes"></a><span data-ttu-id="179e4-113">Codes für geografische Standorte</span><span class="sxs-lookup"><span data-stu-id="179e4-113">Geo location codes</span></span>

[!INCLUDE [Office 365 Multi-Geo locations](includes/office-365-multi-geo-locations.md)]

## <a name="see-also"></a><span data-ttu-id="179e4-114">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="179e4-114">See also</span></span>

<span data-ttu-id="179e4-115">[Herstellen einer Verbindung mit Exchange Online mithilfe der Remote-PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell).</span><span class="sxs-lookup"><span data-stu-id="179e4-115">[Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell)</span></span>