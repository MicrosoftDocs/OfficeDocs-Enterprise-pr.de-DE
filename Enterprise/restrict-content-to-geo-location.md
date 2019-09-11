---
title: Einschränken der SharePoint-Websiteinhalte auf einen geografischen Standort
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: Erfahren Sie, wie Sie SharePoint-Seiten für einen bestimmten geographischen Standort in einer Multi-Geo-Umgebung einschränken.
ms.openlocfilehash: 9319ed6229acc7cda48cc52b3a27681c53f1359c
ms.sourcegitcommit: 7bb48195079ce14aabfa0384771b17db0e4908b9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/10/2019
ms.locfileid: "36828479"
---
# <a name="restrict-sharepoint-site-content-to-a-geo-location"></a>Einschränken der SharePoint-Websiteinhalte auf einen geografischen Standort

Unter bestimmten Umständen können Sie möglicherweise erzwingen, dass eine Seite und Ihre Inhalte an dem geographischen Standort verbleiben, an dem Sie erstellt wurden. Dies ist möglich, indem Sie entweder die Seite daran hindern, verschoben zu werden, oder indem Sie das Zwischenspeichern der Dateiinhalte der Seite an einem anderen geographischen Standort verhindern.

Um dies zu tun, verwenden Sie [Set-SPOSite](https://docs.microsoft.com/powershell/module/sharepoint-online/set-sposite) cmdlet mit dem Parameter **RestrictedToGeo**. Dieser Parameter hat einen Standardwert von NULL, aber Sie können ihn wie folgt ändern:

|Einschränkung|Beschreibung|
|:----------|:----------|
|NoRestriction|Die Website kann an einen anderen Geo-Standort verschoben werden.|
|BlockMoveOnly|Seite kann nicht an einen anderen Geo-Standort verschoben werden, aber Seiteninhalte können an einem anderen geografischen Standort zwischengespeichert werden.|
|BlockFull|Seite kann nicht an einen anderen Geo-Standort verschoben werden und der gesamte Seiteninhalt wird nicht an anderen geografischen Standorten zwischengespeichert. Der Titel der Datei (aus dem Inhalt abgerufen), der Dateiname und andere Eigenschaften der Datei können weiterhin an anderen geographischen Standorten zwischengespeichert werden.<br>Inhalte, die vor der Konfiguration als BlockFull auf der Seite gespeichert wurden, können möglicherweise weiterhin an anderen geographischen Standorten zwischengespeichert werden.|

Verwenden Sie die folgende Syntax:

`Set-SPOSite -Identity <siteURL> -RestrictedToGeo <restriction>`

Beispiel:

`Set-SPOSite -Identity https://contoso.sharepoint.com/sites/RegionRestrictedTeamSite -RestrictedToGeo BlockFull`
