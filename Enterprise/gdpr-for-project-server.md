---
title: DSGVO für Project Server
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Priority
description: Erfahren Sie, wie Sie mit DSGVO-Anforderungen in lokalen Project Server-Installationen umgehen.
ms.openlocfilehash: 6a630dc4cef2c4117e0ba25497f898d0b8da221b
ms.sourcegitcommit: aabd369fc8b397f9e738374d42d8afd18b96d469
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2018
---
# <a name="gdpr-for-project-server"></a>DSGVO für Project Server

Project Server verwendet benutzerdefinierte Skripts zum Exportieren und Bearbeiten von Benutzerdaten in Project Web App. Die grundlegende Vorgehensweise sieht folgendermaßen aus:

1.  Suchen Sie die Project Web App-Websites in Ihrer Farm.

2.  Suchen Sie auf jeder Website die Projekte, die den Benutzer enthalten.

3.  Exportieren und überprüfen Sie die Arten von Daten, die Sie überprüfen möchten.

4.  Bearbeiten Sie die Daten bei Bedarf.

In den folgenden Artikeln werden diese Schritte ausführlich beschrieben:

- [Exportieren von Benutzerdaten aus Project Server](/Project/export-user-data-from-project-server?toc=/Office365/Enterprise/toc.json)

- [Löschen von Benutzerdaten aus Project Server](/Project/delete-user-data-from-project-server?toc=/Office365/Enterprise/toc.json)


Beachten Sie, dass Project Server auf SharePoint Server aufbaut und Ereignisse in SharePoint-ULS-Protokollen und in der Verwendungsdatenbank protokolliert.
