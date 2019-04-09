---
title: Office 365-Client-App-Unterstützung-bedingter Zugriff
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: Office 365 Administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Strat_O365_Enterprise
- M365-subscription-management
description: GrundLegendes zu Office 365-Client-App-Unterstützung für bedingten Zugriff
ms.openlocfilehash: 3212d15f2df68256fc80e4544fc7e61cdccc82c2
ms.sourcegitcommit: 80bc767a9c88a259facb3894b9a168c85d35eb70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2019
ms.locfileid: "31517559"
---
# <a name="office-365-client-app-support---conditional-access"></a>Office 365-Client-App-Unterstützung-bedingter Zugriff

Am modernen Arbeitsplatz können Benutzer über eine Vielzahl von Geräten und apps von praktisch überall aus auf die Ressourcen Ihrer Organisation zugreifen. Daher genügt es nicht mehr, nur darauf zu fokussieren, wer auf eine Ressource zugreifen kann. Ihre Organisation muss außerdem unterstützen, wie und wo auf eine Ressource in ihrer Zugriffs Steuerungsinfrastruktur zugegriffen wird. Mit Azure AD-Gerät, Standort und mehrstufiger Authentifizierungs basierter bedingter Zugriff können Sie diese neue Anforderung erfüllen. Der bedingte Zugriff ist eine Funktion von Azure Active Directory, mit der Sie Steuerelemente für den Zugriff auf apps in Ihrer Umgebung erzwingen können, die alle auf bestimmten Bedingungen basieren und von einem zentralen Standort aus verwaltet werden.

Erfahren Sie mehr über [bedingten Zugriff](https://docs.microsoft.com/azure/active-directory/conditional-access/).

## <a name="supported-platforms"></a>Unterstützte Plattformen

 - Windows 10-Desktop
 - Moderne Windows 10-apps
 - Webbrowser
 - Android<sup>1</sup>
 - iOS
 - macOS<sup>2</sup>

Weitere Informationen zur Plattformunterstützung in Office 365 finden Sie unter [System Requirements for office 365](https://products.office.com/office-system-requirements).

## <a name="supported-clients"></a>Unterstützte Clients

Die neuesten Versionen der folgenden Clients unterstützen bedingten Zugriff:

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| ![Azure-Symbol](media/o365-azure-64x64.png) <br> [Azure AD <br> -Portal ](https://azure.microsoft.com/features/azure-portal/) | ![Access-Symbol](media/o365-access-64x64.png) <br> [Access](https://products.office.com/access) | ![EinTauchen (Symbol)](media/o365-delve-64x64.png) <br> [EinTauchen<sup>1</sup>](https://products.office.com/business/intelligent-search) | ![Dynamics 365-Symbol](media/o365-dynamics365-64x64.png) <br> [Dynamics 365](https://dynamics.microsoft.com) | ![Kantensymbol](media/o365-edge-64x64.png) <br> [Rand](https://www.microsoft.com/windows/microsoft-edge) 
| ![Exchange-Symbol](media/o365-exchange-64x64.png) <br> [Exchange](https://products.office.com/exchange/exchange-online) | ![Excel-Symbol](media/o365-excel-64x64.png) <br> [Excel](https://products.office.com/excel) | ![Fluss Symbol](media/o365-flow-64x64.png) <br> [Flow](https://flow.microsoft.com) | ![Formularsymbol](media/o365-forms-64x64.png) <br> [Formulare](https://flow.microsoft.com/connectors/shared_microsoftforms/microsoft-forms/) | ![Kaizala-Symbol](media/o365-kaizala-64x64.png) <br> [Kaizala](https://products.office.com/en/business/microsoft-kaizala) 
| ![Linsen Symbol](media/o365-lens-64x64.png) <br> [Office Lens](https://www.microsoft.com/p/office-lens/9wzdncrfj3t8?activetab=pivot%3Aoverviewtab) | ![Office 365-Administrator Symbol](media/o365-o365admin-64x64.png) <br> [Office 365 <br> -Administrator](https://products.office.com/business/manage-office-365-admin-app) | ![OneDrive for Business (Symbol)](media/o365-OneDrive-64x64.png) <br> [OneDrive<sup>2</sup>](https://products.office.com/onedrive-for-business/online-cloud-storage) | ![OneNote-Symbol](media/o365-OneNote-64x64.png) <br> [OneNote](https://products.office.com/onenote) | ![Outlook-Symbol](media/o365-outlook-64x64.png) <br> [Outlook](https://products.office.com/outlook) |
| ![Planner-Symbol](media/o365-planner-64x64.png) <br> [Planner](https://products.office.com/business/task-management-software) | ![PowerBI-Symbol](media/o365-powerbi-64x64.png) <br> [Power BI](https://powerbi.microsoft.com) | ![PowerPoint-Symbol](media/o365-powerpoint-64x64.png) <br> [PowerPoint](https://products.office.com/powerpoint) | ![Projektsymbol](media/o365-project-64x64.png) <br> [Project](https://products.office.com/project) | ![Publisher-Symbol](media/o365-publisher-64x64.png) <br> [Publisher](https://products.office.com/publisher)
| ![SharePoint-Symbol](media/o365-sharepoint-64x64.png) <br> [Share](https://products.office.com/sharepoint) | ![Skype for Business-Symbol](media/o365-skypeforbusiness-64x64.png) <br> [Skype for <br> Business](https://www.skype.com/business/) | ![Symbol für Kurznotizen](media/o365-stickynotes-64x64.png) <br> [Kurznotizen](https://www.microsoft.com/p/microsoft-sticky-notes/9nblggh4qghw) | ![Stream (Symbol)](media/o365-stream-64x64.png) <br> [Stream](https://stream.microsoft.com) | ![Sway-Symbol](media/o365-sway-64x64.png) <br> [Sway](https://sway.com) 
| ![Teams (Symbol)](media/o365-teams-64x64.png) <br> [Teams](https://products.office.com/microsoft-teams/group-chat-software) | ![Aufgaben Symbol](media/o365-todo-64x64.png) <br> [To-Do](https://todo.microsoft.com) | ![Visio-Symbol](media/o365-visio-64x64.png) <br> [Visio](https://products.office.com/visio/flowchart-software) | ![Word-Symbol](media/o365-word-64x64.png) <br> [Word](https://products.office.com/word) | ![Jammern-Symbol](media/o365-yammer-64x64.png) <br> [Yammer](https://products.office.com/yammer/yammer-overview)

> [!NOTE]
> <sup>1</sup> Unterstützung für die Erforschung von Android in Kürze verfügbar. <br>
> <sup>2</sup> Unterstützung für OneDrive auf macOS in Kürze verfügbar.