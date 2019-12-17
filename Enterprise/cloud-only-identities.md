---
title: Office 365 nur-Cloud-Identitäten
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/03/2019
audience: Admin
ms.topic: article
f1_keywords:
- O365p_AddUsersWithDirSync
- O365M_AddUsersWithDirSync
- O365E_HRCSetupAADConnectAboutLM617031
- O365E_AddUsersWithDirSync
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOP150
- MOE150
- MBS150
ms.assetid: 01920974-9e6f-4331-a370-13aea4e82b3e
description: Beschreibt, wie Benutzer und Gruppen erstellt werden, wenn Ihr Office 365-Abonnement nur Cloud-Identitäten verwendet.
ms.openlocfilehash: 5991ec838321187b58f913e1707efb2ede9912fb
ms.sourcegitcommit: 3539ec707f984de6f3b874744ff8b6832fbd665e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/17/2019
ms.locfileid: "40072277"
---
# <a name="office-365-cloud-only-identities"></a>Office 365 nur-Cloud-Identitäten

*Dieser Artikel gilt sowohl für Office 365 Enterprise als auch Microsoft 365 Enterprise*.

Bei der reinen cloudbasierten Identität werden alle Ihre Benutzer, Gruppen und Kontakte im Azure Active Directory (Azure AD)-Mandanten Ihres Office 365 Abonnements gespeichert. Hier sind die grundlegenden Komponenten der reinen Cloudidentität.
 
![Die grundlegenden Komponenten von Cloud-only Identity](./media/about-office-365-identity/cloud-only-identity.png)

Benutzer und ihre Benutzerkonten in Organisationen können auf verschiedene Arten kategorisiert werden. Einige sind beispielsweise Mitarbeiter und haben einen permanenten Status. Bei einigen handelt es sich um Kreditoren, Auftragnehmer oder Partner mit einem temporären Status. Einige sind externe Benutzer, die über keine Benutzerkonten verfügen, aber weiterhin Zugriff auf bestimmte Dienste und Ressourcen für die Unterstützung von Interaktion und Zusammenarbeit erhalten müssen. Zum Beispiel:

- Mandantenkonten stellen Benutzer in Ihrem Unternehmen dar, die Sie für Clouddienste lizenzieren.

- B2B-Konten (Business-to-Business) stellen Benutzer außerhalb Ihrer Organisation dar, die Sie zur Teilnahme an der Zusammenarbeit einladen, eine Bestandsaufnahme der Benutzertypen für Ihre Organisation durchführen. Was sind die Gruppierungen? Beispielsweise können Sie Benutzer nach allgemeinen Funktionen oder Zweck in Ihrer Organisation gruppieren.

Darüber hinaus können einige Clouddienste für Benutzer außerhalb Ihres Unternehmens ohne Benutzerkonten freigegeben werden. Sie müssen diese Benutzergruppen ebenfalls identifizieren.

Sie können Gruppen in Azure AD für verschiedene Zwecke verwenden, die die Verwaltung Ihrer Cloud-Umgebung vereinfachen. Beispielsweise können Sie mit Azure Ad Gruppen Folgendes tun:

- Verwenden Sie die Gruppenbasierte Lizenzierung, um Ihren Benutzerkonten automatisch Lizenzen für Office 365 zuzuweisen, sobald diese hinzugefügt werden.
- Sie können bestimmten Gruppen auf Grundlage von Benutzerkontoattributen wie Abteilung Benutzerkonten dynamisch hinzufügen.
- Sie können automatisch SaaS-Anwendungen für Benutzer bereitstellen und den Zugriff auf diese Anwendungen mit der mehrstufigen Authentifizierung und anderen Regeln für bedingten Zugriff schützen.
- Bereitstellungsberechtigungen und Zugriffsebenen für SharePoint Online Teamwebsites.

Sie können neue ***Benutzer*** mit folgendem erstellen:

- [Das Microsoft 365 Admin Center](https://docs.microsoft.com/office365/admin/add-users/add-users)
- [Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/create-user-accounts-with-office-365-powershell)

Sie können mit folgendem neue ***Gruppen*** erstellen:

- [Das Microsoft 365 Admin Center](https://docs.microsoft.com/office365/admin/create-groups/create-groups)
- [Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/manage-office-365-groups-with-powershell)


## <a name="next-step-for-cloud-only-identities"></a>Nächster Schritt für nur-Cloud-Identitäten

[Zuweisen von Lizenzen zu Benutzerkonten](assign-licenses-to-user-accounts.md)
