---
title: Office 365-Client-App-Unterstützung – moderne Authentifizierung
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: Office 365 Administration
localization_priority: Normal
ms.collection:
- Strat_O365_Enterprise
- M365-subscription-management
search.appverid:
- MET150
description: Office 365-Client-App-Unterstützung für moderne Authentifizierung.
ms.openlocfilehash: f4eb3282140bd1b722698ec0fa4a4f3f51366c2e
ms.sourcegitcommit: fd137a68c516379a9f09e06987e8d45d92de7ed6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/27/2019
ms.locfileid: "30303609"
---
# <a name="office-365-client-app-support---modern-authentication"></a>Office 365-Client-App-Unterstützung – moderne Authentifizierung

Die moderne Authentifizierungsfunktion von Microsoft ermöglicht die Active Directory Authentication Library (ADAL)-basierte Anmeldung für Office-Clientanwendungen auf verschiedenen Plattformen. Dadurch werden Anmeldefeatures wie mehrstufige Authentifizierung (Multi-Factor Authentication, MFA), Smartcard-und zertifikatbasierte Authentifizierung aktiviert.

Erfahren Sie mehr über die mehrstufige [Authentifizierung](https://docs.microsoft.com/azure/active-directory/authentication/multi-factor-authentication) und die [zertifikatbasierte Authentifizierung](https://docs.microsoft.com/azure/active-directory/active-directory-certificate-based-authentication-get-started).

## <a name="supported-platforms"></a>Unterstützte Plattformen

 - Windows 10-Desktop
 - Moderne Windows 10-apps
 - Webbrowser
 - Android
 - iOS
 - macOS

Weitere Informationen zur Plattformunterstützung in Office 365 finden Sie unter [System Requirements for office 365](https://products.office.com/office-system-requirements).

## <a name="supported-clients"></a>Unterstützte Clients

Die neuesten Versionen der folgenden Clients unterstützen die moderne Authentifizierung:

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| ![Azure-Symbol](media/o365-azure-64x64.png) <br> [Azure AD <br> -Portal](https://azure.microsoft.com/features/azure-portal/) | ![Unternehmensportal (Symbol)](media/o365-microsoft-64x64.png) <br> [Unternehmens <br> Portal](https://docs.microsoft.com/intune-user-help/sign-in-to-the-company-portal) | ![EinTauchen (Symbol)](media/o365-delve-64x64.png) <br> [Delve](https://products.office.com/business/intelligent-search) | ![Dynamics 365-Symbol](media/o365-dynamics365-64x64.png) <br> [Dynamics 365](https://dynamics.microsoft.com) | ![Excel-Symbol](media/o365-excel-64x64.png) <br> [Excel](https://products.office.com/excel) |
| ![Fluss Symbol](media/o365-flow-64x64.png) <br> [Flow](https://flow.microsoft.com) | ![Formularsymbol](media/o365-forms-64x64.png) <br> [Formulare](https://flow.microsoft.com/connectors/shared_microsoftforms/microsoft-forms/) | ![Kaizala-Symbol](media/o365-kaizala-64x64.png) <br> [Kaizala](https://products.office.com/en/business/microsoft-kaizala) | ![Office 365-Administrator Symbol](media/o365-o365admin-64x64.png) <br> [Office 365 <br> -Administrator](https://products.office.com/business/manage-office-365-admin-app) | ![Linsen Symbol](media/o365-lens-64x64.png) <br> [Office Lens](https://www.microsoft.com/p/office-lens/9wzdncrfj3t8?activetab=pivot%3Aoverviewtab) | 
| ![OneDrive for Business (Symbol)](media/o365-OneDrive-64x64.png) <br> [OneDrive](https://products.office.com/onedrive-for-business/online-cloud-storage) |  ![OneNote-Symbol](media/o365-OneNote-64x64.png) <br> [OneNote](https://products.office.com/onenote) | ![Outlook-Symbol](media/o365-outlook-64x64.png) <br> [Outlook](https://products.office.com/outlook) | ![Planner-Symbol](media/o365-planner-64x64.png) <br> [Planner](https://products.office.com/business/task-management-software) | ![PowerBI-Symbol](media/o365-powerbi-64x64.png) <br> [Power BI](https://powerbi.microsoft.com)
| ![PowerPoint-Symbol](media/o365-powerpoint-64x64.png) <br> [PowerPoint](https://products.office.com/powerpoint) | ![Projektsymbol](media/o365-project-64x64.png) <br> [Project](https://products.office.com/project) | ![SharePoint-Symbol](media/o365-sharepoint-64x64.png) <br> [Share](https://products.office.com/sharepoint) | ![Skype for Business-Symbol](media/o365-skypeforbusiness-64x64.png) <br> [Skype for <br> Business](https://www.skype.com/business/) | ![StaffHub-Symbol](media/o365-staffhub-64x64.png) <br> [StaffHub](https://products.office.com/microsoft-staffhub/staff-scheduling-software)
| ![Symbol für Kurznotizen](media/o365-stickynotes-64x64.png) <br> [Kurznotizen](https://www.microsoft.com/p/microsoft-sticky-notes/9nblggh4qghw) | ![Stream (Symbol)](media/o365-stream-64x64.png) <br> [Stream](https://stream.microsoft.com) | ![Sway-Symbol](media/o365-sway-64x64.png) <br> [Sway](https://sway.com) | ![Teams (Symbol)](media/o365-teams-64x64.png) <br> [Teams](https://products.office.com/microsoft-teams/group-chat-software) | ![Aufgaben Symbol](media/o365-todo-64x64.png) <br> [To-Do](https://todo.microsoft.com)
| ![Visio-Symbol](media/o365-visio-64x64.png) <br> [Visio](https://products.office.com/visio/flowchart-software) | ![Word-Symbol](media/o365-word-64x64.png) <br> [Word](https://products.office.com/word) |![Jammern-Symbol](media/o365-yammer-64x64.png) <br> [Yammer](https://products.office.com/yammer/yammer-overview) | ![Jammern-Symbol](media/o365-yammer-64x64.png) <br> [Jammer <br> Melder](https://products.office.com/yammer/yammer-overview) |  |

## <a name="supported-powershell-modules"></a>Unterstützte PowerShell-Module

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| ![Azure-Symbol](media/o365-azure-64x64.png) <br> [Azure AD <br> PowerShell](https://docs.microsoft.com/powershell/azure/active-directory/overview?view=azureadps-2.0) | ![Exchange-Symbol](media/o365-exchange-64x64.png) <br> [Exchange Online <br> PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell?view=exchange-ps) | ![SharePoint-Symbol](media/o365-sharepoint-64x64.png) <br> [SharePoint <br> Online-PowerShell](https://docs.microsoft.com/sharepoint/manage-team-and-communication-sites-in-powershell)