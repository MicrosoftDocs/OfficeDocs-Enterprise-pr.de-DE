---
title: Integrierte Apps und Azure Active Directory für Office 365-Administratoren
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 3/5/2018
ms.audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: cb2250e3-451e-416f-bf4e-363549652c2a
description: Hier erfahren Sie, wie Office 365 Apps integriert registriert sind und in Azure Active Directory verwaltet werden
ms.openlocfilehash: 0482271f15dc5e2b81e36fd265b49da6eba18702
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915000"
---
# <a name="integrated-apps-and-azure-ad-for-office-365-administrators"></a>Integrierte Apps und Azure Active Directory für Office 365-Administratoren

Weitere Verwaltung von integrierten apps als nur [Einschalten integrierte-Apps aktiviert oder deaktiviert](https://support.office.com/article/7e453a40-66df-44ab-92a1-96786cb7fb34#__toc379982114)ist. Mit der Einführung von Office 365-REST-APIs können Benutzer apps Zugriff auf ihre Office 365-Daten, wie e-Mail, Kalender, Kontakte, Benutzer, Gruppen, Dateien und Ordner erteilen. In der Standardeinstellung Benutzer einzeln erteilen von Berechtigungen für die jeweilige app müssen, aber nicht skaliert gut, wenn Sie autorisieren einer app einmal auf der Ebene der globalen Administratorrolle und in der gesamten Organisation über das Startprogramm app einführen möchten. Zu diesem Zweck müssen Sie die app in Azure Active Directory registrieren. Es gibt einige Schritte, die Sie ergreifen können Sie eine app in Azure Active Directory registrieren und Hintergrundinformationen, die Sie kennen sollten, die Ihnen helfen kann apps in Office 365-Organisation verwalten zu müssen. Dieser Artikel verweist auf diese Ressourcen.
  
## <a name="azure-ad-resources-for-office-365-admins"></a>Azure AD-Ressourcen für Office 365-Administratoren

Sie müssen diese beiden Verfahren ausführen, bevor Sie Ihre Office 365-apps in Azure AD verwalten können.
  
|**Voraussetzungen**|**Anmerkungen**|
|:-----|:-----|
|[Registrieren Ihres kostenlosen Azure Active Directory-Abonnements](https://go.microsoft.com/fwlink/?LinkId=617127) <br/> |Jeder kostenpflichtiges Abonnement zu Office 365 verfügt über ein kostenloses Abonnement für Azure Active Directory. Azure AD können Ihre apps verwalten und zum Erstellen und Verwalten von Benutzer- und Gruppenkonten. Zum Aktivieren dieses Abonnements und dem Azure-Verwaltungsportal zuzugreifen, müssen Sie eine einmalige Registrierung abzuschließen. Anschließend können Sie aus dem Office 365 Administrationscenter Azure AD wechseln.  <br/> |
|[Aktivieren oder Deaktivieren von integrierten Apps](https://support.office.com/article/7e453a40-66df-44ab-92a1-96786cb7fb34#__toc379982114) <br/> |Integrierte Apps müssen Sie für Ihre Benutzer zum Zulassen von Drittanbieter-apps auf ihre Office 365-Informationen zugreifen und Sie apps in Azure Active Directory registrieren einschalten. Beispielsweise wenn eine Drittanbieter-app verwendet wird, möglicherweise app Fragen für die Berechtigung auf ihren Kalender zuzugreifen und zum Bearbeiten von Dateien, die in einer OneDrive for Business-Ordner sind.  <br/> |
   
Verwalten von Office 365-apps müssen Sie apps in Azure AD kennen. In diesen Artikeln ermöglichen Ihnen den Hintergrund, die, den Sie benötigen.
  
|**Hintergrund-Artikel**|**Anmerkungen**|
|:-----|:-----|
|[Das Startprogramm für Office 365-app erfüllen](https://support.office.com/article/79f12104-6fed-442f-96a0-eb089a3f476a) <br/> |Wenn Sie dieses Startprogramm app noch nicht kennen, Sie vielleicht, was ist und dessen Verwendung. Das Startprogramm app soll Ihnen dabei helfen, Ihre apps unabhängig vom Standort möglichst in Office 365.  <br/> |
|[Hinzufügen, aktualisieren und Entfernen einer Anwendung](https://go.microsoft.com/fwlink/?LinkId=617137) <br/> |In diesem Thema wird das Hinzufügen, aktualisieren oder Entfernen einer Anwendung in Azure Active Directory veranschaulicht. Lernen Sie die verschiedenen Typen von Anwendungen, die in Azure AD integriert werden können und zum Konfigurieren der Anwendung Zugriff auf andere Ressourcen wie Web-APIs und vieles mehr.  <br/> |
|[Haben Ihre app in Office 365-app-Start angezeigt werden](https://go.microsoft.com/fwlink/?LinkId=617138).  <br/> |Die app Launcher in Office 365, die Benutzer suchen und Zugreifen auf ihre apps vereinfacht. Dieser Artikel beschreibt die Möglichkeiten, die Sie als Entwickler Ihre apps angezeigt werden sollen, in der Benutzer app Startprogramme und weisen Sie ihnen auch eine einmaliges Anmelden (SSO) Erfahrung mit ihren Office 365-Anmeldeinformationen abrufen können.  <br/> |
|[Office 365-APIs Plattform (Übersicht)](https://go.microsoft.com/fwlink/?LinkId=617140) <br/> |Die Office 365-APIs können Sie bereitstellen, Zugriff auf Ihre Kunden Office 365 Daten, einschließlich der Punkte, die am meisten interessieren – ihre e-Mail-Nachrichten, Kalender, Kontakte, Benutzer und Gruppen, Dateien und Ordner. In diesem Artikel, die die Beziehung zwischen apps für Office 365, Azure AD veranschaulicht ist eine gute Diagramm und die Daten, die apps zugreifen.  <br/> |
|[Integrieren von Clientanwendungen in Azure Active Directory](https://go.microsoft.com/fwlink/?LinkId=617141) <br/> | Informationen Sie zu Anwendungen, die mit Azure Active Directory sowie zum Registrieren der Anwendung, Konzepten bei der einer registrierten Anwendung verstehen und erfahren Sie mehr über Brandingrichtlinien für mehrere Mandanten Anwendungen integriert sind.  <br/> |
|[Azure Active Directory-Integration Lernprogramme](https://go.microsoft.com/fwlink/?LinkId=617144) <br/> |In diesem Lernprogramm Ziel ist es zu zeigen, wie Sie Azure AD SSO für SaaS drittanbieteranwendungen konfigurieren.  <br/> |
|[Azure AD-Authentifizierungsszenarien](https://go.microsoft.com/fwlink/?LinkId=617145) <br/> |Azure AD vereinfacht Authentifizierung für Entwickler durch Identität als Dienst, durch die Unterstützung für Standardprotokolle wie OAuth 2.0 und OpenID Verbinden als auch öffnen Quelle Bibliotheken für verschiedene Plattformen zur einfacheren codieren schnell und einfach zu starten. In diesem Dokument können Sie die verschiedenen Szenarien zu verstehen, die Azure AD unterstützt und zeigt, wie Sie die ersten Schritte beim.  <br/> |
|[Zugriff auf die Anwendung](https://go.microsoft.com/fwlink/?LinkId=617146) <br/> |Azure AD kann einfache Integration auf viele der heutigen beliebte Software als dienstanwendungen (SaaS). Identitäts-und Softwareentwicklern und bietet eine Abdeckung für Benutzer, bei denen sie herausfinden können, welche Anwendungszugriff verfügen und diese SSO verwenden können, auf deren Anwendung zugreifen. Dieser Artikel enthält Links zu den zugehörigen Ressourcen, mit denen Sie erfahren mehr über die Anwendung Access-Verbesserungen für Azure AD und wie Sie Ihnen beitragen können.  <br/> |
|[Hinzufügen oder Entfernen von Kacheln auf das Startprogramm für Office 365-app](https://support.office.com/article/0b71362d-ce56-4d21-9b2f-bdb750a82b81) <br/> |Sie erhalten schnellen Zugriff auf die apps, die Sie jeden Tag durch Hinzufügen oder Entfernen von apps in das Startprogramm für Office 365-app verwenden.  <br/> |
   

