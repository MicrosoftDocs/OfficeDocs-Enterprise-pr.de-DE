---
title: SharePoint Speicherkontingente in Multi-Geo-Umgebungen
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.custom: ''
ms.collection:
- Strat_SP_gtc
- SPO_Content
localization_priority: Priority
description: Weitere Informationen finden Sie unter SharePoint Speicherkontingente in Multi-Geo-Umgebungen.
ms.openlocfilehash: b04c05f911e6ba4c5362e64dc6db4bf711ed78aa
ms.sourcegitcommit: 265cc03b600e9015a44c60c3f8bb9075b1c20888
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2020
ms.locfileid: "41974207"
---
# <a name="sharepoint-storage-quotas-in-multi-geo-environments"></a><span data-ttu-id="43e96-103">SharePoint Speicherkontingente in Multi-Geo-Umgebungen</span><span class="sxs-lookup"><span data-stu-id="43e96-103">SharePoint storage quotas in multi-geo environments</span></span>

<span data-ttu-id="43e96-104">Alle geografischen Standorte einer Multi-Geo-Umgebung teilen sich das Speicherkontingent des Mandanten.</span><span class="sxs-lookup"><span data-stu-id="43e96-104">By default, all geo locations of a multi-geo environment share the available tenant storage quota.</span></span>

<span data-ttu-id="43e96-105">Mit der SharePoint Geo-Speicherkontingent-Einstellung können Sie das Speicherkontingent jedes geographischen Standorts verwalten.</span><span class="sxs-lookup"><span data-stu-id="43e96-105">With the SharePoint geo storage quota setting, you can manage the storage quota for each geo location.</span></span> <span data-ttu-id="43e96-106">Wenn Sie ein Speicherkontingent einem geographischen Standort zuweisen, wird es zur maximal verfügbaren Menge an Speicherplatz für diesen geographischen Standort und wird vom verfügbaren Mandanten-Speicherkontingent abgezogen.</span><span class="sxs-lookup"><span data-stu-id="43e96-106">When you allocate a storage quota for a geo location, it becomes the maximum amount of storage available for that geo location, and is deducted from the available tenant storage quota.</span></span> <span data-ttu-id="43e96-107">Die verbleibende verfügbare Mandanten-Speicherkontingent wird dann untern den konfigurierten geographischen Standorten aufgeteilt, für die kein bestimmtes Speicherkontingent zuweisen wurde.</span><span class="sxs-lookup"><span data-stu-id="43e96-107">The remaining available tenant storage quota is then shared across the configured geo locations for which a specific storage quota has not been allocated.</span></span>

<span data-ttu-id="43e96-108">Das SharePoint-Speicherkontingent eines geographischen Standorts kann vom SharePoint-Onlineadministrator durch eine Verbindung zum zentralen Standort zugewiesen werden.</span><span class="sxs-lookup"><span data-stu-id="43e96-108">The SharePoint storage quota for any geo location can be allocated by the SharePoint Online administrator by connecting to the central location.</span></span> <span data-ttu-id="43e96-109">Geo-Administratoren von Satellitenstandorten können Speicherkontingente sehen, aber nicht zuweisen.</span><span class="sxs-lookup"><span data-stu-id="43e96-109">Geo administrators for satellite locations can view the storage quota but cannot allocate it.</span></span>

## <a name="configure-a-storage-quota-for-a-geo-location"></a><span data-ttu-id="43e96-110">Ein Speicherkontingent für einen Geo-Standort konfigurieren</span><span class="sxs-lookup"><span data-stu-id="43e96-110">Configure a storage quota for a geo location</span></span>

<span data-ttu-id="43e96-111">Verwenden Sie das [Microsoft SharePoint Online-Modul](https://www.microsoft.com/download/details.aspx?id=35588 ) und stellen Sie eine Verbindung zum zentralen Standort her, um das Speicherkontingent für einen geographischen Standort zuzuweisen.</span><span class="sxs-lookup"><span data-stu-id="43e96-111">Use the [Microsoft SharePoint Online Module](https://www.microsoft.com/download/details.aspx?id=35588 ) and connect to the central location to allocate the storage quota for a geo location.</span></span> 

<span data-ttu-id="43e96-112">Führen Sie cmdlet aus, um ein Speicherkontingent für einen Standort zuzuweisen:</span><span class="sxs-lookup"><span data-stu-id="43e96-112">To allocate Storage Quota for a location, run cmdlet:</span></span>

`Set-SPOGeoStorageQuota -GeoLocation <geolocationcode> -StorageQuotaMB <value>`

<span data-ttu-id="43e96-113">Führen Sie Folgendes aus, um das Speicherkontingent des aktuellen geografischen Standorts anzuzeigen:</span><span class="sxs-lookup"><span data-stu-id="43e96-113">To view Storage Quota for the current geo location, run:</span></span>

`Get-SPOGeoStorageQuota`

![Screenshot eines Fensters in PowerShell, der Get-SPOGeoStorageQuota cmdlet zeigt](media/multi-geo-storage-quota.png)

<span data-ttu-id="43e96-115">Führen Sie Folgendes aus, um das Speicherkontingent aller geografischen Standorte anzuzeigen:</span><span class="sxs-lookup"><span data-stu-id="43e96-115">To view Storage Quota for all geo locations, run:</span></span>

`Get-SPOGeoStorageQuota -AllLocations`

<span data-ttu-id="43e96-116">Legen Sie `StorageQuota value = 0` fest, um das zugewiesene Speicherkontingent eines geographischen Standorts zu entfernen:</span><span class="sxs-lookup"><span data-stu-id="43e96-116">To remove the allocated storage quota for a geo location, set `StorageQuota value = 0`:</span></span>

`Set-SPOGeoStorageQuota -GeoLocation <geolocationcode> -StorageQuotaMB 0`
