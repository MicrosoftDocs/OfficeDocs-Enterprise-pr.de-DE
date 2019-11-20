---
title: Zuweisen von Office 365 Lizenzen zu Benutzerkonten
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
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
description: Beschreibt, wie Benutzerkonten Office 365 Lizenzen entweder einzeln oder basierend auf der Gruppenmitgliedschaft zuweisen.
ms.openlocfilehash: bc736236f9371ee1372fd36af4a707aca2ee1408
ms.sourcegitcommit: f316aef1c122f8eb25c43a56bc894c4aa61c8e0c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/20/2019
ms.locfileid: "38745708"
---
# <a name="assign-office-365-licenses-to-user-accounts"></a>Zuweisen von Office 365 Lizenzen zu Benutzerkonten

*Dieser Artikel bezieht sich sowohl auf Office 365 Enterprise als auch auf Microsoft 365 Enterprise.*

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
- [Konfigurieren der Verwaltung mobiler Geräte](https://support.office.com/article/set-up-mobile-device-management-mdm-in-office-365-dd892318-bc44-4eb1-af00-9db5430be3cd)
- [Konfigurieren von Diensten und Anwendungen](configure-services-and-applications.md)
