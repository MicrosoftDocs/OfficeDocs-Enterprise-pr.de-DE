---
title: Sitzungstimeouts für Office 365
ms.author: tracyp
author: MSFTTracyP
manager: scotv
ms.date: 6/29/2018
ms.audience: Admin
ms.topic: reference
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- BCS160
ms.assetid: 37a5c116-5b07-4f70-8333-5b86fd2c3c40
description: Sitzungstimeouts werden verwendet, um Securtiy und erleichterte in Office 365-Clientanwendungen auszugleichen.
ms.openlocfilehash: 4ef50b876fd97e2de2449d324464b466243a6691
ms.sourcegitcommit: fd7a56f38ba2c2d2e7fcd6e165ec58b31be299d9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/19/2018
ms.locfileid: "27378491"
---
# <a name="session-timeouts-for-office-365"></a>Sitzungstimeouts für Office 365

Sitzungsdauer sind ein wichtiger Teil der Authentifizierung für Office 365 und Ausgleichen von Sicherheit und wie oft, Benutzer aufgefordert werden, ihre Anmeldeinformationen für eine wichtige Komponente.
  
## <a name="session-times-for-office-365-services"></a>Sitzungsdauer für Office 365-Dienste

Beim Authentifizieren von Benutzern in Office 365 Web apps oder mobiler apps wird eine Sitzung eingerichtet. Benutzer müssen nicht für die Dauer der Sitzung Ihre Anmeldeinformationen erneut eingeben. Sitzungen können ablaufen, wenn Benutzer sind inaktiv, wenn sie den Browser oder die Registerkarte schließen oder nach Ablauf ihrer Authentifizierungstoken aus anderen Gründen, z. B., wenn ihr Kennwort zurückgesetzt wurde. Office 365-Dienste haben verschiedene Sitzungstimeouts mit der standardmäßige Verwendung für jeden Dienst übereinstimmen.
  
Die folgende Tabelle enthält die Sitzungsdauer für Office 365-Dienste:
  
|**Office 365-Dienste**|**Sitzungstimeout**|
|:-----|:-----|
|Office 365 Admin Center  <br/> |Sie werden aufgefordert, Anmeldeinformationen für das Administrationscenter alle 8 Stunden angeben.  <br/> |
|SharePoint Online  <br/> |5 Tage wählt Inaktivität, solange der Benutzer **angemeldet bleiben**. Wenn der Benutzer von SharePoint Online erneut greift auf nach Ablauf von 24 oder mehrere Stunden aus der vorherigen Anmeldung, wird der Timeoutwert auf 5 Tage zurückgesetzt.<br/> |
|Outlook Web App  <br/> |6 Stunden.  <br/> Sie können diesen Wert ändern, mit dem _ActivityBasedAuthenticationTimeoutInterval_ -Parameter im Cmdlet [Set-OrganizationConfig](https://go.microsoft.com/fwlink/p/?LinkId=615378) .  <br/> |
|Azure Active Directory  <br/> (Verwendet von Office 2013-Windows-Clients mit modernen Authentifizierung aktiviert)  <br/> | Moderne Authentifizierung verwendet Zugriffstoken und Aktualisierungstoken gewähren des Benutzerzugriffs auf Office 365-Ressourcen mit Azure Active Directory. Ein Zugriffstoken ist ein JSON Web Token nach einer erfolgreichen Authentifizierung bereitgestellt und gilt für 1 Stunde. Ein Aktualisierungstoken mit Lebensdauer wird auch bereitgestellt. Nach Ablauf der Zugriffstoken verwenden Office-Clients eine gültige Aktualisierungstoken, um ein neues Zugriffstoken abzurufen. Diese Exchange erfolgreich, wenn die Authentifizierung des Benutzers anfänglichen noch gültig ist.  <br/>  Aktualisierungstoken 90 Tage lang gültig sind, und mit kontinuierlichen verwenden, können sie erst gesperrt gültig sein.  <br/>  Aktualisieren von Token können ungültig gemacht werden durch verschiedene Ereignisse wie etwa:  <br/>  Das Kennwort des Benutzers wurde seit der Aktualisierungstoken ausgestellt wurde geändert.  <br/>  Ein Administrator kann bedingte Zugriffsrichtlinien anwenden, die Zugriff auf die Ressource zu beschränken, die der Benutzer zugreifen möchte.  <br/> |
|SharePoint- und OneDrive mobilen apps für Android-, IOS- und Windows-10  <br/> |Die standardmäßige Lebensdauer für das Zugriffstoken ist 1 Stunde. Die Standardeinstellung von der Aktualisierungstoken für inaktive Zeitraum max ist 90 Tage.<br/> [Erfahren Sie mehr über Token und zum Konfigurieren von token Lebensdauer](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-configurable-token-lifetimes) <br/> Um die Aktualisierung sperren können token, Sie das Kennwort des Benutzers Office 365 zurücksetzen  <br/> |
|Yammer mit Office 365-Anmeldung  <br/> |Lebensdauer des Browsers. Wenn Benutzer schließen Sie den Browser und Yammer in einem neuen Browserfenster zugreifen, authentifiziert Yammer diese mit Office 365 erneut. Wenn Benutzer drittanbieterbrowsern dieser Cache Cookies zu verwenden, müssen sie möglicherweise nicht erneut zu authentifizieren, wenn sie den Browser erneut zu öffnen.<br/> > [!NOTE]> Dies gilt nur für Netzwerke mit Office 365-Anmeldung für Yammer.           |
   

