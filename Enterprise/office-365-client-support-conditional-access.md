---
title: Support für Office 365 Client App - bedingten Zugriff
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 7/17/2018
audience: ITPro
ms.topic: article
ms.service: Office 365 Administration
localization_priority: None
ms.collection: Strat_O365_Enterprise
description: Grundlegendes zu Office 365-Client-app-Unterstützung für bedingten Zugriff
ms.openlocfilehash: f9a1b4c022b00569a392d7f50bfcae583847ea3c
ms.sourcegitcommit: 4e654517825b74a3bbe171b915b134ba49231e2e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/30/2018
ms.locfileid: "21541965"
---
# <a name="office-365-client-app-support---conditional-access"></a>Support für Office 365 Client App - bedingten Zugriff

Am Arbeitsplatz modernen können Benutzer mit einer Vielzahl von Geräten und apps egal an welchem Ort Ihrer Organisation Ressourcen zugreifen. Daher ist nur Konzentration auf, die eine Ressource zugreifen kann nicht über ausreichende mehr. Ihre Organisation muss ebenfalls unterstützen, wie und in Ihre Access Control-Infrastruktur, in dem eine Ressource zugegriffen wird. Mit Azure AD-Gerät, Speicherort und mehrstufige Authentifizierung-basierte bedingten Zugriff können Sie diese neue Anforderung erfüllen. Bedingte Access ist eine Funktion von Azure Active Directory, der können Sie Steuerelemente beim Zugriff auf apps in Ihrer Umgebung, die alle basierend auf spezifischen Auflagen durchsetzen und von einem zentralen Standort verwaltet. 

Weitere Informationen zu [gerätebasierte](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-policy-connected-applications) [speicherortbasierte](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-locations)und [mehrstufiger Authentifizierung das-basierten](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-conditions#users-and-groups) bedingte Zugriff.

## <a name="supported-platforms"></a>Unterstützte Plattformen

 - 10 Windows-Desktop
 - Moderne Apps für Windows 10
 - Webbrowser
 - Android
 - iOS
 - Mac OS-<sup>1</sup>

## <a name="supported-clients"></a>Unterstützte Clients

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| ![Symbol eingegangen](images/o365-delve-64x64.png) <br> [Delve](https://products.office.com/business/intelligent-search) | ![Excel-Symbol](images/o365-excel-64x64.png) <br> [Excel](https://products.office.com/excel) | ![Fluss-Symbol](images/o365-flow-64x64.png) <br> [Flow](https://flow.microsoft.com) | ![Forms-Symbol](images/o365-forms-64x64.png) <br> [Formulare](https://flow.microsoft.com/connectors/shared_microsoftforms/microsoft-forms/) | ![Kaizala-Symbol](images/o365-kaizala-64x64.png) <br> [Kaizala](https://products.office.com/en/business/microsoft-kaizala) 
| ![Office 365-Admin-Symbol](images/o365-o365admin-64x64.png) <br> [Office 365 <br> Admin](https://products.office.com/business/manage-office-365-admin-app) | ![OneDrive for Business-Symbol](images/o365-OneDrive-64x64.png) <br> [OneDrive](https://products.office.com/onedrive-for-business/online-cloud-storage) | ![OneNote-Symbol](images/o365-OneNote-64x64.png) <br> [OneNote](https://products.office.com/onenote) | ![Outlook-Symbol](images/o365-outlook-64x64.png) <br> [Outlook](https://products.office.com/outlook) | ![Planner-Symbol](images/o365-planner-64x64.png) <br> [Planner](https://products.office.com/business/task-management-software) 
| ![PowerBI-Symbol](images/o365-powerbi-64x64.png) <br> [Power BI](https://powerbi.microsoft.com) | ![PowerPoint-Symbol](images/o365-powerpoint-64x64.png) <br> [PowerPoint](https://products.office.com/powerpoint) | ![Projektsymbol](images/o365-project-64x64.png) <br> [Project](https://products.office.com/project) | ![SharePoint-Symbol](images/o365-sharepoint-64x64.png) <br> [SharePoint-<sup>1</sup>](https://products.office.com/sharepoint) | ![Skype für Business-Symbol](images/o365-skypeforbusiness-64x64.png) <br> [Skype für <br> Business](https://www.skype.com/business/) 
| ![StaffHub-Symbol](images/o365-staffhub-64x64.png) <br> [StaffHub](https://products.office.com/microsoft-staffhub/staff-scheduling-software) | ![Stream-Symbol](images/o365-stream-64x64.png) <br> [Stream](https://stream.microsoft.com) | ![Sway Symbol](images/o365-sway-64x64.png) <br> [Sway](https://sway.com) | ![Symbol für Teams](images/o365-teams-64x64.png) <br> [Teams](https://products.office.com/microsoft-teams/group-chat-software) | ![Aufgabe Symbol](images/o365-todo-64x64.png) <br> [To-Do](https://todo.microsoft.com) 
| ![Visio-Symbol](images/o365-visio-64x64.png) <br> [Visio](https://products.office.com/visio/flowchart-software) | ![Word-Symbol](images/o365-word-64x64.png) <br> [Word](https://products.office.com/word) | ![Yammer-Symbol](images/o365-yammer-64x64.png) <br> [Yammer](https://products.office.com/yammer/yammer-overview)

> [!NOTE]
> <sup>1</sup> Mac OS in Kürze Unterstützung von SharePoint-app.