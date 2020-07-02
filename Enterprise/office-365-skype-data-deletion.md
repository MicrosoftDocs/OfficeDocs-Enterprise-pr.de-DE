---
title: Office 365 Skype for Business Datenlöschung
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
f1.keywords:
- NOCSH
description: Eine Erklärung zum Löschen von Daten in Skype for Business.
ms.openlocfilehash: 7c94c5d1ddfb5a8056e139d664627dd1e7bed0de
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "44997795"
---
# <a name="skype-for-business-data-deletion-in-office-365"></a>Skype for Business von Datenlöschung in Office 365

Skype for Business provides archiving of peer-to-peer instant messages, multiparty instant messages, and content upload activities in meetings. The archiving capability requires Exchange and is controlled by the user's Exchange mailbox In-Place Hold attribute, which archives both email and Skype for Business contents.

All archiving in Skype for Business is considered "user-level archiving" because you enable or disable it for one or more specific users or groups of users by creating, configuring, and applying a user-level archiving policy for those users. There is no direct control of archiving settings from within the Skype for Business admin center.

Die folgenden Inhaltstypen werden in Skype for Business nicht archiviert:

- Peer-zu-Peer-Dateiübertragungen
- Audio/Video für Peer-zu-Peer-Chatnachrichten und -Konferenzen
- Anwendungsfreigaben für Peer-zu-Peer-Chatnachrichten und -Konferenzen
- Anmerkungen zu Konferenzen 

## <a name="meeting-content-retention"></a>Erfüllen der Inhaltsaufbewahrung

Kunden, die Skype for Business verwenden, können Inhalte in eine Skype for Business Besprechung als Anlagen hochladen, beispielsweise PowerPoint-Präsentationen, OneNote-Dateien und andere Dateien. Für Inhalte, die in eine Besprechung hochgeladen werden, gilt folgende Aufbewahrungsdauer:

- **Einmaliger Besprechungs** Inhalt wird 15 Tage lang aufbewahrt, beginnend mit dem Zeitpunkt, an dem die letzte Person die Besprechung verlässt.
- Besprechungs **Serie** – Inhalte werden 15 Tage lang aufbewahrt, nachdem die letzte Person die letzte Besprechungs Sitzung verlassen hat. Der Aufbewahrungstimer wird zurückgesetzt, wenn jemand innerhalb von 15 Tagen an dieser Besprechungssitzung teilnimmt. Nehmen wir beispielsweise an, dass eine Skype for Business Besprechung für ein Jahr auf wöchentlicher Basis stattfindet und eine Datei während der ersten Instanz in die Besprechung hochgeladen wird. Wenn jede Woche mindestens eine Person der Besprechungs Sitzung Beitritt, wird die Datei in Skype for Business Online Servern für das gesamte Jahr aufbewahrt, und zwar 15 Tage nachdem die letzte Person die letzte Besprechung der Datenreihe verlassen hat.
- **Sofortbesprechung** – Inhalte werden 8 Stunden nach der Besprechungs Endzeit aufbewahrt.

> [!NOTE]
> Wenn ein Benutzer nicht lizenziert oder deaktiviert ist (beispielsweise wenn **msRTCSIP-UserEnabled** auf *false*festgelegt ist) und dann erneut lizenziert oder erneut aktiviert wird, werden Besprechungsinhalte nicht beibehalten.

## <a name="meeting-expiration"></a>Ablauf der Besprechung

Benutzer können nach Ende einer bestimmten Besprechung auf diese zugreifen. Dafür gelten die folgenden Ablaufzeiträume:

- **Einmaliges Besprechungs** Meeting läuft 14 Tage nach der geplanten Besprechungs Endzeit ab.
- **Wiederkehrende Besprechung mit Enddatum** – Besprechung läuft 14 Tage nach der geplanten Endzeit des letzten Besprechungstermins ab.
- " **Jetzt einsehen** "-Besprechungs Sitzung läuft nach 8 Stunden ab.

## <a name="whiteboard-collaboration"></a>Whiteboard-Zusammenarbeit

Anmerkungen auf Whiteboards sind für alle Teilnehmer sichtbar. Beim Speichern eines Whiteboards werden das Whiteboard und alle Anmerkungen auf einem Skype for Business Server gespeichert und auf dem Server entsprechend den vom Administrator festgelegten Richtlinien zum Ablauf von Besprechungsinhalten aufbewahrt.

## <a name="audio-test-service"></a>Audio-Test Dienst

Ein kurzes Sample ihrer Stimme (ca. 5 Sekunden) wird während des Anrufs für den Audio-Test Dienst aufgezeichnet. Das VoIP-Beispiel wird von Ihnen verwendet, um die Tonqualität Ihres Skype for Business Anrufs basierend auf der Qualität der Aufzeichnung zu überprüfen und/oder zu überprüfen. Wenn der Anruf des Audiotest Diensts beendet wird, wird das VoIP-Beispiel gelöscht.

## <a name="persistent-group-chat"></a>Beständiger Gruppen Chat

Im Chat für beständige Gruppen wird der Inhalt von Gruppenchat Unterhaltungen gespeichert. Wenn diese Option aktiviert ist, kann der Administrator den Aufbewahrungszeitraum, den Server, auf dem diese Informationen gespeichert sind, verwalten, wenn der Gruppen Chat Verlauf für die Kompatibilität oder andere Zwecke archiviert wird, und die Eigenschaften für einen Chatroom verwalten/ändern. Benutzer mit unterschiedlichen Rollen haben wie folgt unterschiedlichen Zugriff auf die beibehaltenen Daten:

- Administratoren können ältere Inhalte (beispielsweise Inhalte, die vor einem bestimmten Datum veröffentlicht wurden) aus einem Chatroom löschen, damit die Größe der Datenbank nicht größer wird. Oder Sie können Nachrichten entfernen oder ersetzen, die für einen bestimmten Chatroom unangemessen sind (oder als ungeeignet betrachtet werden).
- Endbenutzer, einschließlich Nachrichten Autoren, können keine Inhalte aus Chatrooms löschen.
- Chatroom-Manager können Räume deaktivieren, aber keine Räume löschen. Nur Administratoren können einen Chatroom löschen, nachdem er erstellt wurde.