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
localization_priority: Normal
description: Weitere Informationen finden Sie unter SharePoint Speicherkontingente in Multi-Geo-Umgebungen.
ms.openlocfilehash: f0463797dd3471f349e60d8f029b7ae2fa4b65a6
ms.sourcegitcommit: aac21bb1a7c1dfc3ba76a2db883e0457037c5667
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/28/2020
ms.locfileid: "45433736"
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
