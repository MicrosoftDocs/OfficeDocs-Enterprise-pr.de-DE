---
title: Erstellen Sie eine Office 365-Gruppe mit einem bestimmten PLD
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: Erfahren Sie, wie Die eine Office 365-Gruppe mit einem bestimmten bevorzugten Datenspeicherort in einer Multi-Geo-Umgebung erstellen.
ms.openlocfilehash: 96870923c00cebc247609b67378fd39011077d45
ms.sourcegitcommit: 3539ec707f984de6f3b874744ff8b6832fbd665e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/17/2019
ms.locfileid: "40072377"
---
# <a name="create-an-office-365-group-with-a-specific-pdl"></a><span data-ttu-id="9147c-103">Erstellen Sie eine Office 365-Gruppe mit einem bestimmten PLD</span><span class="sxs-lookup"><span data-stu-id="9147c-103">Create an Office 365 Group with a specific PDL</span></span>

<span data-ttu-id="9147c-104">Wenn ein Benutzer in einer Multi-Geo-Umgebung eine Office 365-Gruppe erstellt, wird als bevorzugter Datenspeicherort der Gruppe automatisch der dieses Benutzers festgelegt.</span><span class="sxs-lookup"><span data-stu-id="9147c-104">When users in a multi-geo environment create an Office 365 Group, the group preferred data location is automatically set to that of the user.</span></span> <span data-ttu-id="9147c-105">Globale, SharePoint- und Exchange-Administratoren können Gruppen in jeder ausgewählten Region erstellen.</span><span class="sxs-lookup"><span data-stu-id="9147c-105">Global, SharePoint, and Exchange Administrators can create groups in any region they select.</span></span> 

<span data-ttu-id="9147c-106">Wenn Sie eine Gruppe mit einem bestimmten PLD erstellen möchten, können Sie dies über das SharePoint Admin Center oder unter Verwendung des Exchange Online New-UnifiedGroup Microsoft PowerShell-Cmdlets vornehmen.</span><span class="sxs-lookup"><span data-stu-id="9147c-106">If you need to create a group with a specific PDL, you can do that using the Exchange Online New-UnifiedGroup Microsoft PowerShell cmdlet.</span></span> <span data-ttu-id="9147c-107">Wenn Sie dies tun, werden das zugewiesene Gruppenpostfach und die SharePoint-Website für die Gruppe der angegebenen Verteilerliste an diesem bestimmten PLD bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="9147c-107">When you do this, both the group mailbox and SharePoint site associated with the group will be provisioned in the specified PDL.</span></span>

<span data-ttu-id="9147c-108">Um eine Office 365-Gruppe mit dem von Ihnen angegebenen PDL zu erstellen, wechseln Sie zum SharePoint Admin Center an dem geografischen Standort, an dem Sie die Gruppenwebsite erstellen möchten.</span><span class="sxs-lookup"><span data-stu-id="9147c-108">To create an Office 365 Group with the PDL that you specify, go to the SharePoint admin center in the geo location where you want to create the group site.</span></span>

<span data-ttu-id="9147c-109">Zum Beispiel:</span><span class="sxs-lookup"><span data-stu-id="9147c-109">For example:</span></span>

<span data-ttu-id="9147c-110">Wenn Sie eine Gruppenwebsite an Ihrem Standort in Australien erstellen möchten, wechseln Sie zu https://ContosoAUS-admin.sharepoint.com/_layouts/15/online/AdminHome.aspx#/siteManagement.</span><span class="sxs-lookup"><span data-stu-id="9147c-110">If you wan to create a group site in your Australtia location, you can go to https://ContosoAUS-admin.sharepoint.com/_layouts/15/online/AdminHome.aspx#/siteManagement</span></span>

1. <span data-ttu-id="9147c-111">Wählen Sie **+ Erstellen** aus.</span><span class="sxs-lookup"><span data-stu-id="9147c-111">Select **+ Create**.</span></span>
2. <span data-ttu-id="9147c-112">Führen Sie den Vorgang zum Erstellen einer Gruppenwebsite aus.</span><span class="sxs-lookup"><span data-stu-id="9147c-112">Follow the process to create a group site.</span></span>

<span data-ttu-id="9147c-113">Ihre Gruppenwebsite wird an dem geografischen Standort bereitgestellt, der dem SharePoint Admin Center entspricht, von dem aus Sie die Anforderung für die Websiteerstellung initiiert haben.</span><span class="sxs-lookup"><span data-stu-id="9147c-113">Your group site will be provisioned in the geo location corresponding to the SharePoint admin center from which you initiated the site creation request.</span></span> 

<span data-ttu-id="9147c-114">Verwenden von Exchange PowerShell</span><span class="sxs-lookup"><span data-stu-id="9147c-114">Using Exchange PowerShell</span></span> 

<span data-ttu-id="9147c-115">Stellen Sie eine Verbindung zu Exchange Online PowerShell her, und geben Sie den Parameter *-MailBoxRegion* mit dem Code des geografischen Standorts weiter.</span><span class="sxs-lookup"><span data-stu-id="9147c-115">To create an Office 365 Group with the PDL that you specify, connect to Exchange Online PowerShell and pass the parameter *-MailBoxRegion* with the geo location code.</span></span>

<span data-ttu-id="9147c-116">Zum Beispiel:</span><span class="sxs-lookup"><span data-stu-id="9147c-116">For example:</span></span> 

```PowerShell
New-UnifiedGroup -DisplayName MultiGeoEUR -Alias "MultiGeoEUR" -AccessType Public -MailboxRegion EUR 
```

![Screenshot des New-UnifiedGroup PowerShell cmdlet mit Syntax](media/multi-geo-new-group-with-pdl-powershell.png)

<span data-ttu-id="9147c-118">Beachten Sie, dass die Bereitstellung von SharePoint-Gruppenseiten nach Bedarf erfolgt.</span><span class="sxs-lookup"><span data-stu-id="9147c-118">Note that SharePoint group site provisioning is on-demand.</span></span> <span data-ttu-id="9147c-119">Die Seite wird bereitgestellt, wenn ein Gruppenbesitzer oder -mitglied zum ersten Mal auf diese zugreift.</span><span class="sxs-lookup"><span data-stu-id="9147c-119">The site will be provisioned the first time a group owner or member attempts to access it.</span></span>

## <a name="geo-location-codes"></a><span data-ttu-id="9147c-120">Codes für geografische Standorte</span><span class="sxs-lookup"><span data-stu-id="9147c-120">Geo location codes</span></span>

[!INCLUDE [Office 365 Multi-Geo locations](includes/office-365-multi-geo-locations.md)]

## <a name="see-also"></a><span data-ttu-id="9147c-121">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="9147c-121">See also</span></span>

<span data-ttu-id="9147c-122">[Herstellen einer Verbindung mit Exchange Online mithilfe der Remote-PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell).</span><span class="sxs-lookup"><span data-stu-id="9147c-122">[Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell)</span></span>
