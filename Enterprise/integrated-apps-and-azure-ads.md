---
title: Integrierte Apps und Azure AD für Office 365-Administratoren
ms.author: chrfox
author: chrfox
manager: laurawi
ms.audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection: M365-subscription-management
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: cb2250e3-451e-416f-bf4e-363549652c2a
description: Erfahren Sie, wie integrierte O365-apps in Azure AD registriert und verwaltet werden.
ms.openlocfilehash: f4e2061c952a09c4e23aa50bd294b7391e1ca3e6
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/30/2019
ms.locfileid: "33487122"
---
# <a name="integrated-apps-and-azure-ad-for-office-365-administrators"></a>Integrierte Apps und Azure AD für Office 365-Administratoren

Es gibt mehr zur Verwaltung integrierter apps, als nur [integrierte apps ein-oder](https://support.office.com/article/7e453a40-66df-44ab-92a1-96786cb7fb34#__toc379982114)auszuschalten. Mit der Einführung der Office 365-REST-APIs können Benutzer apps Zugriff auf Ihre Office 365-Daten gewähren, wie e-Mail, Kalender, Kontakte, Benutzer, Gruppen, Dateien und Ordner. Standardmäßig müssen Benutzer jeder App jeweils Berechtigungen erteilen, dies ist jedoch nicht gut geeignet, wenn Sie eine APP auf globaler Administratorebene einmal autorisieren und über das App-Startfeld für Ihre gesamte Organisation bereitstellen möchten. Zu diesem Zweck müssen Sie die app in Azure AD registrieren. Es gibt einige Schritte, die Sie ausführen müssen, bevor Sie eine app in Azure AD registrieren können, sowie einige Hintergrundinformationen, die Ihnen bei der Verwaltung von apps in Ihrer Office 365-Organisation helfen können. Dieser Artikel verweist auf diese Ressourcen.
  
## <a name="azure-ad-resources-for-office-365-admins"></a>Azure AD-Ressourcen für Office 365-Administratoren

Sie müssen diese beiden Verfahren ausführen, bevor Sie Ihre Office 365-apps in Azure AD verwalten können.
  
|**Voraussetzungen**|**Comments**|
|:-----|:-----|
|[Registrieren Ihres kostenlosen Azure Active Directory-Abonnements](https://go.microsoft.com/fwlink/?LinkId=617127) <br/> |Jedes zahlende Abonnement für Office 365 wird mit einem kostenlosen Abonnement für Azure Active Directory geliefert. Sie können Azure AD verwenden, um Ihre apps zu verwalten und Benutzer-und Gruppenkonten zu erstellen und zu verwalten. Zum Aktivieren dieses Abonnements und Zugreifen auf das Azure-Verwaltungsportal müssen Sie einmalig einen Registrierungsprozess durchlaufen. Anschließend können Sie im Office 365 Admin Center zu Azure AD wechseln.  <br/> |
|[Aktivieren oder Deaktivieren von integrierten Apps](https://support.office.com/article/7e453a40-66df-44ab-92a1-96786cb7fb34#__toc379982114) <br/> |Sie müssen integrierte Apps für Ihre Benutzer aktivieren, damit Drittanbieter-apps auf Ihre Office 365-Informationen zugreifen und apps in Azure AD registrieren können. Wenn beispielsweise jemand eine Drittanbieter-App verwendet, fordert diese APP möglicherweise die Berechtigung für den Zugriff auf Ihren Kalender und zum Bearbeiten von Dateien in einem OneDrive for Business-Ordner an.  <br/> |
   
Für die Verwaltung von Office 365-apps müssen Sie über apps in Azure AD verfügen. Diese Artikel helfen Ihnen, den erforderlichen Hintergrund zu erhalten.
  
|**Hintergrundartikel**|**Comments**|
|:-----|:-----|
|[Erfüllen des Office 365-App-startfelds](https://support.office.com/article/79f12104-6fed-442f-96a0-eb089a3f476a) <br/> |Wenn Sie neu im App-Startfeld sind, Fragen Sie sich vielleicht, was es ist und wie es zu verwenden ist. Das App-startFeld ist so konzipiert, dass Sie von überall in Office 365 zu ihren apps gelangen.  <br/> |
|[Eine Anwendung hinzufügen, aktualisieren und entfernen](https://go.microsoft.com/fwlink/?LinkId=617137) <br/> |In diesem Thema wird gezeigt, wie Sie eine Anwendung in Azure Active Directory hinzufügen, aktualisieren oder entfernen. Sie erfahren mehr über die verschiedenen Typen von Anwendungen, die in Azure AD integriert werden können, und wie Sie Ihre Anwendungen für den Zugriff auf andere Ressourcen wie Web-APIs konfigurieren.  <br/> |
|[Lassen Sie Ihre APP im Office 365-App-Startfeld angezeigt](https://go.microsoft.com/fwlink/?LinkId=617138).  <br/> |Das App-startFeld in Office 365, das es Benutzern erleichtert, Ihre apps zu finden und darauf zuzugreifen. In diesem Artikel werden die Möglichkeiten beschrieben, wie Sie als Entwickler ihre apps in den App-Startprogrammen der Benutzer erscheinen lassen können, und Ihnen auch eine einmalige Anmeldung (SSO) mit Ihren Office 365-Anmeldeinformationen ermöglichen.  <br/> |
|[Office 365-APIs – Plattformübersicht](https://go.microsoft.com/fwlink/?LinkId=617140) <br/> |Mit den Office 365-APIs können Sie Zugriff auf die Office 365-Daten Ihres Kunden bereitstellen, einschließlich der Dinge, die Sie am meisten interessieren: e-Mails, Kalender, Kontakte, Benutzer und Gruppen, Dateien und Ordner. In diesem Artikel finden Sie ein gutes Diagramm, das die Beziehung zwischen Office 365-apps, Azure AD und den Daten veranschaulicht, auf die die apps zugreifen.  <br/> |
|[Integrieren von Anwendungen in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/develop/quickstart-v1-add-azure-ad-app) <br/> | Erfahren Sie mehr über Anwendungen, die in Azure Active Directory integriert sind, und wie Sie Ihre Anwendung registrieren, Konzepte hinter einer registrierten Anwendung verstehen und Informationen zu Branding-Richtlinien für Multi-Mandanten Anwendungen erhalten.  <br/> |
|[Lernprogramme für Azure Active Directory-Integration](https://docs.microsoft.com/azure/active-directory/saas-apps/tutorial-list) <br/> |In diesen Lernprogrammen erfahren Sie, wie Sie Azure AD SSO für SaaS-Drittanbieteranwendungen konfigurieren.  <br/> |
|[Authentifizierungsszenarien für Azure AD](https://go.microsoft.com/fwlink/?LinkId=617145) <br/> |Azure AD vereinfacht die Authentifizierung für Entwickler durch die Bereitstellung von Identität als Dienst, mit Unterstützung für Branchenstandard-Protokolle wie OAuth 2,0 und OpenID Connect, sowie Open-Source-Bibliotheken für verschiedene Plattformen, die Ihnen helfen, schnell mit der Codierung zu beginnen. Dieses Dokument hilft Ihnen, die verschiedenen Szenarien zu verstehen, die Azure AD unterstützt, und zeigt Ihnen, wie Sie beginnen.  <br/> |
|[Anwendungszugriff](https://docs.microsoft.com/azure/active-directory/manage-apps/what-is-access-management) <br/> |Azure AD ermöglicht die einfache Integration in viele der gängigen Software as a Service (SaaS)-Anwendungen. Es bietet Identitäts-und Zugriffsverwaltung und stellt ein Zugriffs Panel für Benutzer bereit, in dem Sie ermitteln können, welche Anwendungs Zugriffe Sie haben und wo Sie SSO für den Zugriff auf Ihre Anwendungen verwenden können. Dieser Artikel enthält Links zu den zugehörigen Ressourcen, mit denen Sie mehr über die Anwendungszugriffs Verbesserungen für Azure AD erfahren und wie Sie dazu beitragen können.  <br/> |
|[Personalisieren Ihrer Office 365-Umgebung](https://support.office.com/article/eb34a21b-52fa-4fbf-a8d5-146132242985) <br/> |Sie können einen schnellen Zugriff auf die apps erhalten, die Sie täglich verwenden, indem Sie apps im Office 365-App-Startfeld hinzufügen oder entfernen.  <br/> |
   

