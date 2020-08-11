---
title: Einschränken der SharePoint-Websiteinhalte auf einen geografischen Standort
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
ms.collection: Strat_SP_gtc
localization_priority: Normal
description: In diesem Artikel erfahren Sie, wie Sie SharePoint-Websites auf einen bestimmten geografischen Standort in einer Multi-Geo-Umgebung einschränken.
ms.openlocfilehash: 7f0147d803fe4dbc6aa444a5e5014884c0f00beb
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/10/2020
ms.locfileid: "46606151"
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
