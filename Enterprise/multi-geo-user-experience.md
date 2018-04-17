---
title: Benutzererfahrung in einer Umgebung multgeo
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: Strat_SP_gtc
localization_priority: Normal
description: Hier erfahren Sie, wie das Benutzererlebnis SharePoint- und OneDrive in einer Umgebung mit mehreren geografisch.
ms.openlocfilehash: 42e384d3e93ca3f5a06a8ee07a37b10e21477038
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="user-experience-in-a-multi-geo-environment"></a>Benutzererfahrung in einer Umgebung mit mehreren geografisch

Hier ist, was Ihre Benutzer in einer OneDrive Multi-Geo-Konfiguration angezeigt werden:

#### <a name="users-onedrive-for-business-location"></a>OneDrive für Unternehmen des Benutzers

Benutzer müssen ihre OneDrive for Business in ihrer bevorzugten Datenspeicherort bereitgestellt. Wenn ein Benutzer auf eine OneDrive-URL, die einen falschen Geo-Speicherort (beispielsweise eine Textmarke aus einem vorherigen Geo-Speicherort) enthält navigiert, werden sie automatisch an die OneDrive in den entsprechenden Geo-Speicherort umgeleitet.

#### <a name="sharing"></a>Freigabe

Die Personenauswahl Erfahrung zeigt alle Benutzer unabhängig vom Standort Geo. Dadurch kann der Benutzer mit einem anderen Benutzer in ihrer gleichen Geo oder andere von Ihrem Mandanten Geo Speicherorte freigeben. Inhalt aus anderen Geo Speicherorten in der Ansicht **für mich freigegeben** in OneDrive für Unternehmen des Benutzers angezeigt, und unabhängig von der Geo-Standort in gehostet ist Single-Sign-On-Erfahrung mit zugegriffen werden können.

#### <a name="office-applications"></a>Office-Anwendungen

Office-Anwendungen wie Word, Excel und PowerPoint erkennt automatisch die richtige OneDrive for Business Geo-Speicherort für jeden Benutzer, sobald sie anmelden. Benutzer müssen nicht die Geo-spezifischen URL für ihre OneDrive eingeben.

#### <a name="onedrive-for-business-sync-client"></a>OneDrive for Business-Synchronisierungsclient

Die OneDrive for Business-Synchronisierungsclient (Version 17.3.6943.0625 und höher) erkennt automatisch die richtige OneDrive for Business Geo Speicherort für den Benutzer.

#### <a name="office-365-app-launcher"></a>App-Startfeld für Office 365

Der app Launcher Multi-Geo bekannt ist und leitet jede Kachel, um den entsprechenden Geo Speicherort der Arbeitslast. OneDrive Kachel verweist auf den richtigen Geo-Speicherort, in der Bibliothek des Benutzers OneDrive gehostet wird, während die Kachel "SharePoint" alle Benutzer an den zentralen Standort, zeigen wird wie Teamwebsites gibt es noch gehostet werden.

#### <a name="delve-user-profiles"></a>Beschäftigen von Benutzerprofilen

Benutzerprofilinformationen ist in Geo-Standort des Benutzers gesteuert. Wenn Sie einen Benutzer auswählen, gelangen Sie zu den entsprechenden Geo-Speicherort für den Benutzer werden, in dem Sie ihren vollständigen Details angezeigt wird.

Wenn Delve deaktiviert ist, sehen Sie das klassische Profil in SharePoint auftreten, der kein Multi-Geo bekannt ist.

#### <a name="delve"></a>Delve

Für Office 365-Benutzer, die in den Instanzen Satelliten sind, wird Multi-Geo ausführlicher behandelt, mit der Einschränkung unterstützt, die mit SharePoint-Blogbeiträge von Benutzern in anderen Regionen, nur für ihre SharePoint-Blogwebsites geschrieben Delve verknüpfen nicht.

#### <a name="search"></a>Suche

Jeder Geo-Speicherort hat eigene Suchindex und Suchcenter. Wenn ein Benutzer sucht, wird die Abfrage an alle Geo Speicherorte gesendet, und die zurückgegebenen Ergebnisse zusammengeführt und dann Rank, sodass der Benutzer ruft unified Ergebnisse ab. Benutzer Ergebnisse aus allen geografisch Speicherorten unabhängig von ihren eigenen Geo-Standort zu erhalten. Einzelheiten finden Sie unter [Konfigurieren der Suche für OneDrive for Business Multi-Geo](configure-search-for-multi-geo.md) .

Die folgenden Search-Clients werden unterstützt:

-   OneDrive for Business

-   Delve

-   SharePoint – Startseite

-   Das Suchcenter

-   Benutzerdefinierte suchanwendungen, die die SharePoint-Suche-API verwenden

#### <a name="onedrive-ios-and-android"></a>OneDrive iOS und Android (engl.) 

Die OneDrive iOS und Android mobiler apps zeigt Ihnen OneDrive-Dateien und Dateien, die Sie unabhängig vom Standort Geo freigegeben. Suche aus OneDrive mobilen apps wird relevante Ergebnisse aus allen geografisch Speicherorten angezeigt. Laden Sie die neueste Version diese Apps.

Weitere Informationen finden Sie unter Verwendung von [OneDrive für iOS](https://support.office.com/article/08d5c5b2-ccc6-40eb-a244-fe3597a3c247) und [Verwendung von OneDrive für Android](https://support.office.com/article/eee1d31c-792d-41d4-8132-f9621b39eb36) .

#### <a name="teams-experience"></a>Teams Erfahrung

Teams ist Multi-Geo berücksichtigen. OneDrive und zuletzt aufgerufenen Dateien werden unabhängig davon Geo-Standort des Benutzers angezeigt. @ erwähnungen Arbeit mit Benutzern aus allen Geo-Speicherorte.
