---
title: Zuweisen von Office 365 Lizenzen zu Benutzerkonten
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/03/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- O365p_AddUsersWithDirSync
- O365M_AddUsersWithDirSync
- O365E_HRCSetupAADConnectAboutLM617031
- O365E_AddUsersWithDirSync
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOP150
- MOE150
- MBS150
ms.assetid: 01920974-9e6f-4331-a370-13aea4e82b3e
description: Beschreibt, wie Benutzerkonten Office 365 Lizenzen entweder einzeln oder basierend auf der Gruppenmitgliedschaft zuweisen.
ms.openlocfilehash: 3ffd51b6b3ab4add900746f14f013a307ca352ad
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/07/2020
ms.locfileid: "41843786"
---
# <a name="assign-office-365-licenses-to-user-accounts"></a>Zuweisen von Office 365 Lizenzen zu Benutzerkonten

*Dieser Artikel gilt sowohl für Office 365 Enterprise als auch Microsoft 365 Enterprise*.

Für das nur-Cloud-Identitätsmodell können Sie den Benutzerkonten Office 365 Lizenzen zuweisen, je nachdem, wie Sie erstellt werden.

Wenn Active Directory-Domänendienste (AD DS) Benutzerkonten zum ersten Mal synchronisiert werden, wird für das hybride Identitätsmodell nicht automatisch eine Office 365 Lizenz zugewiesen.

In beiden Fällen müssen Sie Benutzerkonten eine Lizenz zuweisen, damit Ihre Benutzer auf Office 365 Dienste wie e-Mail und Microsoft Teams zugreifen können.

Sie können Benutzerkonten entweder einzeln oder automatisch über die Gruppenmitgliedschaft Lizenzen zuweisen.

Um einzelnen Benutzerkonten Office 365 Lizenzen zuzuweisen, können Sie Folgendes verwenden:

- [Das Microsoft 365 Admin Center](https://docs.microsoft.com/office365/admin/subscriptions-and-billing/assign-licenses-to-users)
- [Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/assign-licenses-to-user-accounts-with-office-365-powershell)

Informationen zur automatischen Zuweisung von Lizenzen finden Sie unter [Group-based licensing in Azure AD](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-licensing-whatis-azure-portal).

## <a name="next-steps"></a>Nächste Schritte

Mit dem vollständigen Benutzer kontensatz, dem Lizenzen zugewiesen wurden, können Sie nun folgende Aufgaben durchsetzen:

- [Implementieren der Sicherheit](https://docs.microsoft.com/microsoft-365/security/office-365-security/security-roadmap)
- [Bereitstellen von Client Software wie Office 365 ProPlus](https://docs.microsoft.com/DeployOffice/deployment-guide-for-office-365-proplus)
- [Einrichten der Verwaltung mobiler Geräte in Office 365](https://support.office.com/article/set-up-mobile-device-management-mdm-in-office-365-dd892318-bc44-4eb1-af00-9db5430be3cd)
- [Konfigurieren von Diensten und Anwendungen](configure-services-and-applications.md)
