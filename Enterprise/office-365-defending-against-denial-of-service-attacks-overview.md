---
title: Abwehr von Denial-of-Service-Angriffen in Office 365
ms.author: robmazz
author: robmazz
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
description: Eine Übersicht über DOS-Angriffe (Denial of Service).
ms.openlocfilehash: 16378800fc7bb61b8f78e2c4c51eb7940cb45d17
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/07/2020
ms.locfileid: "41843588"
---
# <a name="defend-against-denial-of-service-attacks-in-office-365"></a>Abwehr von Denial-of-Service-Angriffen in Office 365

## <a name="introduction"></a>Einführung

Microsoft bietet eine vertrauenswürdige Infrastruktur für mehr als 200 Cloud-Dienste, die in einer globalen Cloud-Infrastruktur mit mehr als 100 Rechenzentren gehostet werden. Zu diesen zählen:

- Microsoft Azure
- Microsoft Bing
- Microsoft Dynamics 365
- Microsoft Office 365
- Microsoft OneDrive
- Skype
- Xbox Live

Als globale Organisation mit einer bedeutenden Internetpräsenz und vielen prominenten Interneteigenschaften, die Cloud-Dienste bereitstellen, ist Microsoft ein großes, gemeinsames Ziel für Hacker und andere böswillige Personen. Die Netzwerk Kommunikationsschicht zwischen Clients und der Microsoft-Cloud gehört zu den größten Zielen böswilliger Angriffe. Tatsächlich ist Microsoft ständig und dauerhaft unter irgendeiner Form von netzwerkbasierter Cyberangriff. In diesem Sinne verwendet Microsoft umfassende Sicherheitsprinzipien zum Schutz seiner Cloud-Dienste und-Netzwerke. Ohne zuverlässige und beständige mildernde Systeme, die sich gegen diese Angriffe wehren, wären die Cloud-Dienste von Microsoft Offline und für Kunden nicht verfügbar.

## <a name="definition-and-symptoms-of-denial-of-service-attacks"></a>Definition und Symptome von Denial-of-Service-Angriffen

Eine Möglichkeit zum angreifen von Netzwerkdiensten besteht darin, viele Anforderungen an Diensthosts zu erstellen, um das Netzwerk und die Server zu überlasten, um legitimen Benutzern den Dienst zu verweigern. Dies wird als DOS-Angriff (Denial of Service) bezeichnet. Wenn der Angriff von mehreren Akteuren, Endpunkten und/oder Vektoren ausgeführt wird, wird er als Distributed Denial-of-Service (DDoS)-Angriff bezeichnet. Obwohl die Mittel, Motive und Ziele unterschiedlich sind, bestehen DOS-und DDoS-Angriffe im Allgemeinen aus Anstrengungen, um zu verhindern, dass eine Internet-Website oder ein Dienst ordnungsgemäß oder überhaupt vorübergehend oder unbegrenzt funktioniert.

Das US-amerikanische [Computer Notfall Bereitschafts Team](https://www.us-cert.gov/) (US-CERT) definiert die Symptome von DOS-Angriffen, die Folgendes umfassen:

- Ungewöhnlich langsame Netzwerkleistung (beim Öffnen von Dateien oder Zugriff auf Internet Websites)
- Nichtverfügbarkeit einer Website
- Unfähigkeit, auf eine Website zuzugreifen
- Drastische Verstärkung des empfangenen Spam
- Trennen einer drahtlosen oder verkabelten Internet Verbindung
- Langfristiger Verlust des Zugriffs auf das Web oder Internetdienste

## <a name="related-topics"></a>Verwandte Themen

- [Wichtige Grundsätze zum Schutz vor Denial-of-Service-Angriffen](office-365-core-principles-of-defense-against-dos-attacks.md)
- [Denial-of-Service-Verteidigungsstrategie von Microsoft](office-365-microsoft-dos-defense-strategy.md)
- [Schützen von Microsoft Cloud Services vor Denial-of-Service-Angriffen](office-365-defending-cloud-services-against-dos-attacks.md)
