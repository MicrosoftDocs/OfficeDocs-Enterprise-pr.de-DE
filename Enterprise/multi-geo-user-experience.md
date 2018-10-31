---
title: Benutzererfahrung in einer Multi-Geo-Umgebung
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: Dieser Artikel enthält Informationen über die SharePoint- und OneDrive-Benutzererfahrung in einer Multi-Geo-Umgebung.
ms.openlocfilehash: 951efb636ce00f59393f624687d44a406fcf3fc0
ms.sourcegitcommit: a3e2b2e58c328238c15d3f9daf042ea3de9d66be
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2018
ms.locfileid: "25849831"
---
# <a name="user-experience-in-a-multi-geo-environment"></a>Benutzererfahrung in einer Multi-Geo-Umgebung

Im Folgenden wird erläutert, was Benutzern in einer Multi-Geo-Konfiguration in OneDrive angezeigt wird:

#### <a name="users-onedrive-for-business-location"></a>OneDrive for Business-Standort des Benutzers

OneDrive for Business wird Benutzern an dem jeweiligen bevorzugten Datenspeicherort bereitgestellt. Wenn ein Benutzer zu einer OneDrive-URL navigiert, die einen falschen geografischen Strandort enthält (zum Beispiel ein Lesezeichen von einem vorherigen geografischen Standort), werden sie automatisch zur OneDrive-Umgebung an dem entsprechenden geografischen Standort umgeleitet.

#### <a name="sharing"></a>Freigabe

Die Personenauswahl enthält alle Benutzer unabhängig von ihrem geografischen Standort. So kann ein Benutzer Inhalte für einen Benutzer an dem gleichen geografischen Standort oder an allen anderen geografischen Standorten Ihres Mandanten freigeben. Inhalte von anderen geografischen Standorten werden in der Ansicht **Für mich freigegeben** in OneDrive for Business angezeigt, und mit einmaligem Anmelden kann unabhängig von dem geografischen Standort, an dem sie gehostet werden, auf diese zugegriffen werden.

#### <a name="office-applications"></a>Office-Anwendungen

Office-Anwendungen wie Word, Excel und PowerPoint erkennen bei Anmeldung automatisch den richtigen geografischen OneDrive for Business-Standort für jeden Benutzer. Benutzer müssen nicht die für den geografischen OneDrive-Standort spezifische URL eingeben.

#### <a name="onedrive-for-business-sync-client"></a>OneDrive for Business-Synchronisierungsclient

Der OneDrive for Business-Synchronisierungsclient (Version 17.3.6943.0625 und höher) erkennt automatisch den richtigen geografischen OneDrive for Business-Standort für den Benutzer.

#### <a name="office-365-app-launcher"></a>App-Startfeld für Office 365

Das App-Startfeld ist Multi-Geo-fähig. Mit jeder Kachel wird an den entsprechenden geografischen Standort des Workloads weitergeleitet. Die OneDrive-Kachel verweist auf den richtigen geografischen Standort, an dem die OneDrive-Bibliothek des Benutzers gehostet wird, während die SharePoint-Kachel bei allen Benutzern auf den zentralen Standort verweist, da Teamwebsites weiterhin dort gehostet werden.

#### <a name="delve-user-profiles"></a>Delve-Benutzerprofile

Benutzerprofilinformationen werden an dem geografischen Standort des Benutzers verwaltet. Beim Auswählen eines Benutzers werden Sie an den entsprechenden geografischen Standort des Benutzers weitergeleitet, wo vollständige Profilinformationen angezeigt werden.

Wenn Delve deaktiviert ist, sehen Sie das klassische Profil in SharePoint, welches nicht Multi-Geo-fähig ist.

#### <a name="delve"></a>Delve

Für Office 365-Benutzer an den Satellitenstandorten wird Multi-Geo in Delve mit der Einschränkung unterstützt, dass keine Verknüpfung zu SharePoint-Blogbeiträgen von Benutzern in anderen Regionen vorhanden ist, sondern lediglich eine Verknüpfung zu deren SharePoint-Blogwebsites.

#### <a name="search"></a>Suche

Jeder geografische Standort verfügt über einen eigenen Suchindex und ein Suchcenter. Wenn ein Benutzer eine Suche durchführt, wird die Abfrage an alle geografischen Standorte gesendet, und die zurückgegebenen Ergebnisse werden zusammengeführt und bewertet, sodass der Benutzer einheitliche Ergebnisse erhält. Benutzer erhalten unabhängig von ihrem geografischen Standort Ergebnisse von allen geografischen Standorten. Weitere Informationen dazu finden Sie unter [Konfigurieren der Suche für Multi-Geo in OneDrive for Business](configure-search-for-multi-geo.md).

Die folgenden Suchclients werden unterstützt:

-   OneDrive for Business

-   Delve

-   SharePoint-Homepage

-   Das Suchcenter

-   Benutzerdefinierte Suchanwendungen, die die SharePoint-Suche-API verwenden

#### <a name="onedrive-ios-and-android"></a>OneDrive unter IOS und Android 

In den mobilen OneDrive-Apps für iOS und Android werden Ihre OneDrive-Dateien und für Sie freigegebene Dateien unabhängig vom geografischen Standort angezeigt. Die Suche in den mobilen OneDrive-Apps geben relevante Ergebnisse von allen geografischen Standorten zurück. Laden Sie die neueste Version dieser Apps herunter.

Weitere Informationen finden Sie unter Verwenden von [OneDrive unter iOS](https://support.office.com/article/08d5c5b2-ccc6-40eb-a244-fe3597a3c247) und [OneDrive unter Android](https://support.office.com/article/eee1d31c-792d-41d4-8132-f9621b39eb36).

#### <a name="teams-experience"></a>Teams-Erfahrung

Teams sind Multi-Geo-fähig. OneDrive-Dateien und zuletzt verwendete Dateien werden unabhängig vom geografischen Standort des Benutzers angezeigt. @-Erwähnungen funktionieren mit Benutzern von allen geografischen Standorten.
