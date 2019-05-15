---
title: Office 365-Client-App-Unterstützung – zertifikatbasierte Authentifizierung
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
description: Office 365-Client-App-Unterstützung für die zertifikatbasierte Authentifizierung.
ms.openlocfilehash: 88bc59934399588f0a5c682c6b136ad0948ecd52
ms.sourcegitcommit: 9c6e31204aa326c31d60befe80e610f702e65800
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/14/2019
ms.locfileid: "33990917"
---
# <a name="office-365-client-app-support--certificate-based-authentication"></a>Office 365-Client-App-Unterstützung – zertifikatbasierte Authentifizierung

Mithilfe der zertifikatbasierten Authentifizierung können Sie sich bei Azure Active Directory mit einem Clientzertifikat auf Windows-, Android-oder IOS-Geräten authentifizieren. Wenn Sie dieses Feature konfigurieren, müssen Sie keine Benutzernamen-und Kennwortkombination in bestimmte e-Mail-und Microsoft Office-Anwendungen auf Ihrem mobilen Gerät eingeben.

Erfahren Sie mehr über die [zertifikatbasierte Authentifizierung](https://docs.microsoft.com/azure/active-directory/authentication/active-directory-certificate-based-authentication-get-started).

## <a name="supported-platforms"></a>Unterstützte Plattformen

 - Windows 10 Desktop<sup>2</sup>
 - Moderne Windows 10-apps
 - Webbrowser
 - Android
 - iOS
 - macOS<sup>1</sup> <sup>2</sup>

Weitere Informationen zur Plattformunterstützung in Office 365 finden Sie unter [System Requirements for Office 365](https://products.office.com/office-system-requirements).

## <a name="supported-clients"></a>Unterstützte Clients

Die neuesten Versionen der folgenden Clients unterstützen die zertifikatbasierte Authentifizierung:

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| ![Access-Symbol](media/o365-access-64x64.png) <br> [Access](https://products.office.com/access) | ![Azure-Symbol](media/o365-azure-64x64.png) <br> [Azure AD <br> -Portal](https://azure.microsoft.com/features/azure-portal/) | ![Unternehmensportal (Symbol)](media/o365-microsoft-64x64.png) <br> [Unternehmens <br> Portal](https://docs.microsoft.com/intune-user-help/sign-in-to-the-company-portal) | ![Eintauchen (Symbol)](media/o365-delve-64x64.png) <br> [Delve](https://products.office.com/business/intelligent-search) | ![Dynamics 365-Symbol](media/o365-dynamics365-64x64.png) <br> [Dynamics 365](https://dynamics.microsoft.com) 
| ![Kantensymbol](media/o365-edge-64x64.png) <br> [Rand](https://www.microsoft.com/windows/microsoft-edge) | ![Excel-Symbol](media/o365-excel-64x64.png) <br> [Excel](https://products.office.com/excel) | ![Fluss Symbol](media/o365-flow-64x64.png) <br> [Flow](https://flow.microsoft.com) | ![Formularsymbol](media/o365-forms-64x64.png) <br> [Forms](https://flow.microsoft.com/connectors/shared_microsoftforms/microsoft-forms/) | ![Kaizala-Symbol](media/o365-kaizala-64x64.png) <br> [Kaizala](https://products.office.com/en/business/microsoft-kaizala) 
| ![Office 365-Administrator Symbol](media/o365-o365admin-64x64.png) <br> [Office 365 <br> -Administrator](https://products.office.com/business/manage-office-365-admin-app) | ![Linsen Symbol](media/o365-lens-64x64.png) <br> [Office Lens](https://www.microsoft.com/p/office-lens/9wzdncrfj3t8?activetab=pivot%3Aoverviewtab) | ![OneDrive for Business (Symbol)](media/o365-OneDrive-64x64.png) <br> [OneDrive<sup>1</sup>](https://products.office.com/onedrive-for-business/online-cloud-storage) |  ![OneNote-Symbol](media/o365-OneNote-64x64.png) <br> [OneNote](https://products.office.com/onenote) | ![Outlook-Symbol](media/o365-outlook-64x64.png) <br> [Outlook](https://products.office.com/outlook) 
| ![Planner-Symbol](media/o365-planner-64x64.png) <br> [Planner](https://products.office.com/business/task-management-software) | ![PowerApps-Symbol](media/o365-powerapps-64x64.png) <br> [PowerApps](https://powerapps.microsoft.com) | ![PowerBI-Symbol](media/o365-powerbi-64x64.png) <br> [Power BI](https://powerbi.microsoft.com)| ![PowerPoint-Symbol](media/o365-powerpoint-64x64.png) <br> [PowerPoint](https://products.office.com/powerpoint) | ![Projektsymbol](media/o365-project-64x64.png) <br> [Project](https://products.office.com/project) 
| ![Publisher-Symbol](media/o365-publisher-64x64.png) <br> [Publisher](https://products.office.com/publisher) | ![SharePoint-Symbol](media/o365-sharepoint-64x64.png) <br> [Share](https://products.office.com/sharepoint) | ![Skype for Business-Symbol](media/o365-skypeforbusiness-64x64.png) <br> [Skype for <br> Business](https://www.skype.com/business/) | ![Symbol für Kurznotizen](media/o365-stickynotes-64x64.png) <br> [Kurznotizen](https://www.microsoft.com/p/microsoft-sticky-notes/9nblggh4qghw) | ![Stream (Symbol)](media/o365-stream-64x64.png) <br> [Stream](https://stream.microsoft.com) 
| ![Sway-Symbol](media/o365-sway-64x64.png) <br> [Sway](https://sway.com) | ![Teams (Symbol)](media/o365-teams-64x64.png) <br> [Teams](https://products.office.com/microsoft-teams/group-chat-software) | ![Aufgaben Symbol](media/o365-todo-64x64.png) <br> [To-Do](https://todo.microsoft.com) | ![Visio-Symbol](media/o365-visio-64x64.png) <br> [Visio](https://products.office.com/visio/flowchart-software) | ![Word-Symbol](media/o365-word-64x64.png) <br> [Word](https://products.office.com/word) 
| ![Jammern-Symbol](media/o365-yammer-64x64.png) <br> [Jammern<sup>2</sup>](https://products.office.com/yammer/yammer-overview) |

## <a name="supported-powershell-modules"></a>Unterstützte PowerShell-Module

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| ![Azure-Symbol](media/o365-azure-64x64.png) <br> [Azure AD <br> PowerShell](https://docs.microsoft.com/powershell/azure/active-directory/overview?view=azureadps-2.0) | ![Exchange-Symbol](media/o365-exchange-64x64.png) <br> [Exchange Online <br> PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell?view=exchange-ps) | ![SharePoint-Symbol](media/o365-sharepoint-64x64.png) <br> [SharePoint <br> Online-PowerShell](https://docs.microsoft.com/sharepoint/manage-team-and-communication-sites-in-powershell)

> [!NOTE]
> <sup>1</sup> Unterstützung für OneDrive auf macOS in Kürze verfügbar. <br>
> <sup>2</sup> Unterstützung für jammern auf Windows-Desktop und macOS in Kürze verfügbar.