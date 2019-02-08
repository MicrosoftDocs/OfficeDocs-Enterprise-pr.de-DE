---
title: Support für Office 365 Client App - modernen Authentifizierung
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: Office 365 Administration
localization_priority: None
search.appverid:
- MET150
ms.collection: Strat_O365_Enterprise
description: Office 365-Client-App für die moderne Authentifizierung unterstützt.
ms.openlocfilehash: 18ef5b2219c9527594ae8fcff7e29052671d1431
ms.sourcegitcommit: bbbe304bb1878b04e719103be4287703fb3ef292
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "29771124"
---
# <a name="office-365-client-app-support---modern-authentication"></a>Support für Office 365 Client App - modernen Authentifizierung

Microsofts ermöglicht modernen Authentifizierung Active Directory Authentifizierung Bibliothek ADAL-basierte-Anmeldung für Office-Clientanwendungen auf verschiedenen Plattformen. Auf diese Weise können Anmeldung Features wie beispielsweise Multi-Factor Authentication (mehrstufiger Authentifizierung das), Smartcard und zertifikatbasierte Authentifizierung.

Hier erfahren Sie mehr über [mehrstufige Authentifizierung](https://docs.microsoft.com/azure/active-directory/authentication/multi-factor-authentication) und [zertifikatbasierte Authentifizierung](https://docs.microsoft.com/azure/active-directory/active-directory-certificate-based-authentication-get-started).

## <a name="supported-platforms"></a>Unterstützte Plattformen

 - 10 Windows-Desktop
 - Moderne Apps für Windows 10
 - Webbrowser
 - Android
 - iOS
 - Mac OS

## <a name="supported-clients"></a>Unterstützte Clients

Die aktuellen Versionen der folgenden Clients unterstützen moderne Authentifizierung:

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| ![Azure-Symbol](media/o365-azure-64x64.png) <br> [Azure AD <br> Portal](https://azure.microsoft.com/features/azure-portal/) | ![Unternehmen Portal-Symbol](media/o365-microsoft-64x64.png) <br> [Unternehmen <br> Portal](https://docs.microsoft.com/intune-user-help/sign-in-to-the-company-portal) | ![Symbol eingegangen](media/o365-delve-64x64.png) <br> [Delve](https://products.office.com/business/intelligent-search) | ![Symbol für Dynamics 365](media/o365-dynamics365-64x64.png) <br> [Dynamics 365](https://dynamics.microsoft.com) | ![Excel-Symbol](media/o365-excel-64x64.png) <br> [Excel](https://products.office.com/excel) |
| ![Fluss-Symbol](media/o365-flow-64x64.png) <br> [Flow](https://flow.microsoft.com) | ![Forms-Symbol](media/o365-forms-64x64.png) <br> [Formulare](https://flow.microsoft.com/connectors/shared_microsoftforms/microsoft-forms/) | ![Kaizala-Symbol](media/o365-kaizala-64x64.png) <br> [Kaizala](https://products.office.com/en/business/microsoft-kaizala) | ![Office 365-Admin-Symbol](media/o365-o365admin-64x64.png) <br> [Office 365 <br> Admin](https://products.office.com/business/manage-office-365-admin-app) | ![Symbol für Lens](media/o365-lens-64x64.png) <br> [Office Lens](https://www.microsoft.com/p/office-lens/9wzdncrfj3t8?activetab=pivot%3Aoverviewtab) | 
| ![OneDrive for Business-Symbol](media/o365-OneDrive-64x64.png) <br> [OneDrive](https://products.office.com/onedrive-for-business/online-cloud-storage) |  ![OneNote-Symbol](media/o365-OneNote-64x64.png) <br> [OneNote](https://products.office.com/onenote) | ![Outlook-Symbol](media/o365-outlook-64x64.png) <br> [Outlook](https://products.office.com/outlook) | ![Planner-Symbol](media/o365-planner-64x64.png) <br> [Planner](https://products.office.com/business/task-management-software) | ![PowerBI-Symbol](media/o365-powerbi-64x64.png) <br> [Power BI](https://powerbi.microsoft.com)
| ![PowerPoint-Symbol](media/o365-powerpoint-64x64.png) <br> [PowerPoint](https://products.office.com/powerpoint) | ![Projektsymbol](media/o365-project-64x64.png) <br> [Project](https://products.office.com/project) | ![SharePoint-Symbol](media/o365-sharepoint-64x64.png) <br> [SharePoint](https://products.office.com/sharepoint) | ![Skype für Business-Symbol](media/o365-skypeforbusiness-64x64.png) <br> [Skype für <br> Business](https://www.skype.com/business/) | ![StaffHub-Symbol](media/o365-staffhub-64x64.png) <br> [StaffHub](https://products.office.com/microsoft-staffhub/staff-scheduling-software)
| ![Kurznotiz Notizen](media/o365-stickynotes-64x64.png) <br> [Kurznotizen](https://www.microsoft.com/p/microsoft-sticky-notes/9nblggh4qghw) | ![Stream-Symbol](media/o365-stream-64x64.png) <br> [Stream](https://stream.microsoft.com) | ![Sway Symbol](media/o365-sway-64x64.png) <br> [Sway](https://sway.com) | ![Symbol für Teams](media/o365-teams-64x64.png) <br> [Teams](https://products.office.com/microsoft-teams/group-chat-software) | ![Aufgabe Symbol](media/o365-todo-64x64.png) <br> [To-Do](https://todo.microsoft.com)
| ![Visio-Symbol](media/o365-visio-64x64.png) <br> [Visio](https://products.office.com/visio/flowchart-software) | ![Word-Symbol](media/o365-word-64x64.png) <br> [Word](https://products.office.com/word) |![Yammer-Symbol](media/o365-yammer-64x64.png) <br> [Yammer](https://products.office.com/yammer/yammer-overview) | ![Yammer-Symbol](media/o365-yammer-64x64.png) <br> [Yammer <br> Notifier](https://products.office.com/yammer/yammer-overview) |  |

## <a name="supported-powershell-modules"></a>Unterstützte PowerShell-Module

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| ![Azure-Symbol](media/o365-azure-64x64.png) <br> [Azure AD <br> PowerShell](https://docs.microsoft.com/powershell/azure/active-directory/overview?view=azureadps-2.0) | ![Exchange-Symbol](media/o365-exchange-64x64.png) <br> [Exchange Online <br> PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell?view=exchange-ps) | ![SharePoint-Symbol](media/o365-sharepoint-64x64.png) <br> [SharePoint Online <br> PowerShell](https://docs.microsoft.com/sharepoint/manage-team-and-communication-sites-in-powershell)