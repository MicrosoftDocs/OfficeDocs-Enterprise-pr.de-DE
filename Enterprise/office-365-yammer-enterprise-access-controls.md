---
title: Office 365 jammern von Unternehmens Zugriffs Steuerelementen
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
description: 'Zusammenfassung: eine kurze Zusammenfassung über das Jammern von Enterprise-Zugriffs Steuerelementen in der Produktionsumgebung.'
ms.openlocfilehash: 19910ec0771b3034e7a290190ae7045ffc8651cf
ms.sourcegitcommit: 55a046bdf49bf7c62ab74da73be1fd1cf6f0ad86
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/20/2019
ms.locfileid: "37067452"
---
# <a name="yammer-enterprise-access-controls"></a>Yammer Enterprise-Zugriffssteuerungen 

Der physische und logische Zugriff auf die Produktionsumgebung jammern ist auf eine kleine Gruppe von Personen (Infrastruktur und Betrieb) beschränkt. Wie bei anderen Office 365-Ingenieuren haben Jammer Techniker keinen ständigen Zugriff auf Kundendaten. Der Zugriff muss mithilfe eines Genehmigungs basierten Just-in-Time-Zugriffs Steuerungssystems angefordert werden, ähnlich wie Lockbox mit einer begrenzten Anzahl von genehmigenden Personen. Genehmigende Personen überprüfen die Anforderung (beispielsweise überprüfen, ob die Anforderung aufgrund von Bedarf, Geschäftsfall, Zeit usw. legitim ist), und genehmigen oder verweigern die Anforderung. Wenn die Anforderung genehmigt wird, wird der JIT-Zugriff für eine definierte und beschränkte Zeit gewährt. Nach Überschreiten der Zugriffszeit läuft der Zugriff automatisch ab.

Wie bei anderen Office 365 Diensten verwendet jeder Zugriff auf die Produktionsumgebung für jammern die mehrstufige Authentifizierung. Der gesamte Zugriffs-und Befehlsverlauf wird einem Benutzer zugeschrieben und regelmäßig vom Sicherheitsteam "jammern" protokolliert und überprüft.

Weitere Informationen zur Verwaltung und Verwaltung von jammern finden Sie unter [jammern der Administratorhilfe](https://support.office.com/article/yammer-–-admin-help-e1464355-1f97-49ac-b2aa-dd320b179dbe?ui=en-US&rs=en-US&ad=US).