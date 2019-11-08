---
title: SharePoint Speicherkontingente in Multi-Geo-Umgebungen
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection:
- Strat_SP_gtc
- SPO_Content
localization_priority: Priority
description: Weitere Informationen finden Sie unter SharePoint Speicherkontingente in Multi-Geo-Umgebungen.
ms.openlocfilehash: d4049312a2da64f16d2637ffd37adf98f2282287
ms.sourcegitcommit: fa900775790eb369db1983cd3868b628b699f145
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2019
ms.locfileid: "38033381"
---
# <a name="sharepoint-storage-quotas-in-multi-geo-environments"></a>SharePoint Speicherkontingente in Multi-Geo-Umgebungen

Alle geografischen Standorte einer Multi-Geo-Umgebung teilen sich das Speicherkontingent des Mandanten.

Mit der SharePoint Geo-Speicherkontingent-Einstellung können Sie das Speicherkontingent jedes geographischen Standorts verwalten. Wenn Sie ein Speicherkontingent einem geographischen Standort zuweisen, wird es zur maximal verfügbaren Menge an Speicherplatz für diesen geographischen Standort und wird vom verfügbaren Mandanten-Speicherkontingent abgezogen. Die verbleibende verfügbare Mandanten-Speicherkontingent wird dann untern den konfigurierten geographischen Standorten aufgeteilt, für die kein bestimmtes Speicherkontingent zuweisen wurde.

Das SharePoint-Speicherkontingent eines geographischen Standorts kann vom SharePoint-Onlineadministrator durch eine Verbindung zum zentralen Standort zugewiesen werden. Geo-Administratoren von Satellitenstandorten können Speicherkontingente sehen, aber nicht zuweisen.

## <a name="configure-a-storage-quota-for-a-geo-location"></a>Ein Speicherkontingent für einen Geo-Standort konfigurieren

Verwenden Sie das [Microsoft SharePoint Online-Modul](https://www.microsoft.com/download/details.aspx?id=35588 ) und stellen Sie eine Verbindung zum zentralen Standort her, um das Speicherkontingent für einen geographischen Standort zuzuweisen. 

Führen Sie cmdlet aus, um ein Speicherkontingent für einen Standort zuzuweisen:

`Set-SPOGeoStorageQuota -GeoLocation <geolocationcode> -StorageQuotaMB <value>`

Führen Sie Folgendes aus, um das Speicherkontingent des aktuellen geografischen Standorts anzuzeigen:

`Get-SPOGeoStorageQuota`

![Screenshot eines Fensters in PowerShell, der Get-SPOGeoStorageQuota cmdlet zeigt](media/multi-geo-storage-quota.png)

Führen Sie Folgendes aus, um das Speicherkontingent aller geografischen Standorte anzuzeigen:

`Get-SPOGeoStorageQuota -AllLocations`

Legen Sie `StorageQuota value = 0` fest, um das zugewiesene Speicherkontingent eines geographischen Standorts zu entfernen:

`Set-SPOGeoStorageQuota -GeoLocation <geolocationcode> -StorageQuotaMB 0`
