---
title: Inhalte für einen geografischen Standort einschränken
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
ms.openlocfilehash: 42c382abd254afcf74dd6bdd15e4c69f65b64f85
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "34070991"
---
# <a name="restrict-content-to-a-geo-location"></a>Inhalte für einen geografischen Standort einschränken

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
