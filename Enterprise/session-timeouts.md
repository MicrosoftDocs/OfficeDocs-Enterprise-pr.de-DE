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
ms.collection:
- M365-security-compliance
description: Sitzungstimeouts werden verwendet, um Securtiy und den einfachen Zugriff in Office 365-Client-apps auszugleichen.
ms.openlocfilehash: 05e0ddbfb569f476986567e55bbf93428125b3af
ms.sourcegitcommit: 1d84e2289fc87717f8a9cd12c68ab27c84405348
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/04/2019
ms.locfileid: "30372882"
---
# <a name="session-timeouts-for-office-365"></a>Sitzungstimeouts für Office 365

Sitzungszeiten sind ein wichtiger Bestandteil der Authentifizierung für Office 365 und sind eine wichtige Komponente beim Ausgleich der Sicherheit und der Häufigkeit, mit der Benutzer zur Eingabe Ihrer Anmeldeinformationen aufgefordert werden.
  
## <a name="session-times-for-office-365-services"></a>Sitzungszeiten für Office 365-Dienste

Wenn sich Benutzer in einer der Office 365 Web Apps oder mobilen apps authentifizieren, wird eine Sitzung eingerichtet. Für die Dauer der Sitzung müssen sich die Benutzer nicht erneut authentifizieren. Sitzungen können ablaufen, wenn Benutzer inaktiv sind, wenn Sie den Browser oder die Registerkarte beenden oder wenn Ihr Authentifizierungstoken aus anderen Gründen abläuft, beispielsweise wenn Ihr Kennwort zurückgesetzt wurde. Die Office 365-Dienste weisen unterschiedliche Sitzungstimeouts auf, die mit der typischen Verwendung der einzelnen Dienste übereinstimmen.
  
In der folgenden Tabelle sind die Sitzungszeiten für Office 365-Dienste aufgeführt:
  
|**Office 365-Dienste**|**Sitzungstimeout**|
|:-----|:-----|
|Office 365 Admin Center  <br/> |Sie werden aufgefordert, alle 8 Stunden Anmeldeinformationen für das Admin Center bereitzustellen.  <br/> |
|SharePoint Online  <br/> |5 Tage Inaktivität, solange die Benutzer **mich für angemeldet halten**. Wenn der Benutzer nach Ablauf von 24 oder mehr Stunden von der vorherigen Anmeldung erneut auf SharePoint Online zugreift, wird der Timeoutwert auf 5 Tage zurückgesetzt.  <br/> |
|Outlook Web App  <br/> |6 Stunden.  <br/> Sie können diesen Wert ändern, indem Sie den Parameter _ActivityBasedAuthenticationTimeoutInterval_ im Cmdlet [Set-OrganizationConfig](https://go.microsoft.com/fwlink/p/?LinkId=615378) verwenden.  <br/> |
|Azure Active Directory  <br/> (Von Office 2013 Windows-Clients mit aktivierter moderner Authentifizierung)  <br/> | Die moderne Authentifizierung verwendet Zugriffstoken und Aktualisierungstoken, um Benutzer Zugriff auf Office 365-Ressourcen mithilfe von Azure Active Directory zu gewähren. Ein Zugriffstoken ist ein JSON-webToken, das nach erfolgreicher Authentifizierung bereitgestellt wird und eine Stunde lang gültig ist. Außerdem wird ein Aktualisierungstoken mit einer längeren Lebensdauer bereitgestellt. Wenn Zugriffstoken ablaufen, verwenden Office-Clients ein gültiges Aktualisierungstoken, um ein neues Zugriffstoken abzurufen. Dieser Exchange-Server ist erfolgreich, wenn die anfängliche Authentifizierung des Benutzers noch gültig ist.  <br/>  Aktualisierungstoken sind 90 Tage lang gültig, und bei fortlaufender Verwendung können Sie bis zur Sperrung gültig sein.  <br/>  Aktualisierungstoken können durch mehrere Ereignisse wie:  <br/>  Das Kennwort des Benutzers wurde geändert, seit das Aktualisierungstoken ausgestellt wurde.  <br/>  Ein Administrator kann Richtlinien für den bedingten Zugriff anwenden, die den Zugriff auf die Ressource einschränken, auf die der Benutzer zugreifen möchte.  <br/> |
|Mobile Apps für SharePoint und OneDrive für Android, iOS und Windows 10  <br/> |Die Standardlebensdauer für das Zugriffstoken beträgt 1 Stunde. Die standardmäßige maximale inaktive Zeit des Aktualisierungs Tokens beträgt 90 Tage.  <br/> [Weitere Informationen zu Token und zum Konfigurieren von Token-Gültigkeitsdauer](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-configurable-token-lifetimes) <br/> Zum Widerrufen des Aktualisierungs Tokens können Sie das Office 365-Kennwort des Benutzers zurücksetzen.  <br/> |
|Jammern mit Office 365-Anmeldung  <br/> |Lebensdauer des Browsers. Wenn Benutzer den Browser beenden und in einem neuen Browser auf jammern zugreifen, wird Sie von jammern erneut mit Office 365 authentifiziert. Wenn Benutzer Drittanbieter-Browser verwenden, die Cookies Zwischenspeichern, müssen Sie sich möglicherweise nicht erneut authentifizieren, wenn Sie den Browser erneut öffnen.  <br/> > [!NOTE]> Dies gilt nur für Netzwerke, die Office 365-Anmeldung für jammern verwenden.           |
   

