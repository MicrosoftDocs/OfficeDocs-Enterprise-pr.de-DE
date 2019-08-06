---
title: Integrierte Apps und Azure AD für Office 365-Administratoren
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
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
ms.openlocfilehash: c52b4beefaefd4a115c132c6f82e7f1d20564b46
ms.sourcegitcommit: 1c97471f47e1869f6db684f280f9085b7c2ff59f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/18/2019
ms.locfileid: "35782525"
---
# <a name="integrated-apps-and-azure-ad-for-office-365-administrators"></a>Integrierte Apps und Azure AD für Office 365-Administratoren

Es gibt mehr zur Verwaltung integrierter apps, als nur [integrierte apps ein-oder](https://support.office.com/article/7e453a40-66df-44ab-92a1-96786cb7fb34#__toc379982114)auszuschalten. Mit dem Aufkommen der Office 365-Rest-APIs können Benutzer apps Zugriff auf Ihre Office 365 Daten wie e-Mail, Kalender, Kontakte, Benutzer, Gruppen, Dateien und Ordner gewähren. Standardmäßig müssen Benutzerberechtigungen für jede APP einzeln erteilen, dies wird jedoch nicht gut skaliert, wenn Sie eine APP einmal auf globaler Administratorebene autorisieren und über das App-Startfeld auf Ihre gesamte Organisation Ausrollen möchten. Hierzu müssen Sie die app in Azure AD registrieren. Es gibt einige Schritte, die Sie ausführen müssen, bevor Sie eine app in Azure AD registrieren können, sowie einige Hintergrundinformationen, die Sie kennen sollten, die Ihnen beim Verwalten von apps in Ihrer Office 365 Organisation helfen können. Dieser Artikel verweist Sie auf diese Ressourcen.
  
## <a name="azure-ad-resources-for-office-365-admins"></a>Azure AD von Ressourcen für Office 365 Administratoren

Sie müssen diese beiden Verfahren ausführen, bevor Sie Ihre Office 365-apps in Azure AD verwalten können.
  
|**Voraussetzungen**|**Kommentare**|
|:-----|:-----|
|[Registrieren Ihres kostenlosen Azure Active Directory-Abonnements](https://go.microsoft.com/fwlink/?LinkId=617127) <br/> |Jedes kostenpflichtige Abonnement für Office 365 ist mit einem kostenlosen Abonnement für Azure Active Directory ausgestattet. Sie können Azure AD verwenden, um Ihre apps zu verwalten und Benutzer-und Gruppenkonten zu erstellen und zu verwalten. Zum Aktivieren dieses Abonnements und Zugreifen auf das Azure-Verwaltungsportal müssen Sie einmalig einen Registrierungsprozess durchlaufen. Anschließend können Sie im Microsoft 365 Admin Center zu Azure AD wechseln.  <br/> |
|[Aktivieren oder deaktivieren integrierter apps](https://support.office.com/article/7e453a40-66df-44ab-92a1-96786cb7fb34#__toc379982114) <br/> |Sie müssen integrierte Apps für Ihre Benutzer aktivieren, damit apps von Drittanbietern auf Ihre Office 365 Informationen zugreifen und apps in Azure AD registrieren können. Wenn beispielsweise eine APP eines Drittanbieters verwendet wird, fordert diese APP möglicherweise die Berechtigung für den Zugriff auf Ihren Kalender an und bearbeitet Dateien, die sich in einem OneDrive für Unternehmen Ordner befinden.  <br/> |
   
Für die Verwaltung Office 365 apps müssen Sie über Kenntnisse von apps in Azure AD verfügen. Diese Artikel helfen Ihnen, den benötigten Hintergrund zu erhalten.
  
|**Hintergrundartikel**|**Kommentare**|
|:-----|:-----|
|[Treffen des Office 365-App-Startprogramms](https://support.office.com/article/79f12104-6fed-442f-96a0-eb089a3f476a) <br/> |Wenn Sie neu im App-Startfeld sind, Fragen Sie sich vielleicht, was es ist und wie Sie es verwenden. Das App-Startfeld ist so konzipiert, dass Sie von einem beliebigen Ort in Office 365 aus auf Ihre apps zugreifen können.  <br/> |
|[Eine Anwendung hinzufügen, aktualisieren und entfernen](https://go.microsoft.com/fwlink/?LinkId=617137) <br/> |In diesem Thema wird gezeigt, wie Sie eine Anwendung in Azure Active Directory hinzufügen, aktualisieren oder entfernen. In diesem Artikel erfahren Sie mehr über die verschiedenen Anwendungstypen, die in Azure AD integriert werden können, und wie Sie Ihre Anwendungen für den Zugriff auf andere Ressourcen wie webapis konfigurieren und vieles mehr.  <br/> |
|[Lassen Sie Ihre APP im Office 365 App Launcher angezeigt werden](https://go.microsoft.com/fwlink/?LinkId=617138).  <br/> |Das App-Startfeld in Office 365, das Benutzern das Auffinden und Zugreifen auf Ihre apps erleichtert. In diesem Artikel werden die Möglichkeiten beschrieben, wie Sie als Entwickler ihre apps in den App-Startprogrammen von Benutzern anzeigen und Ihnen außerdem eine einmalige Anmeldung (SSO) mithilfe Ihrer Office 365 Anmeldeinformationen ermöglichen können.  <br/> |
|[Office 365-APIs – Plattformübersicht](https://go.microsoft.com/fwlink/?LinkId=617140) <br/> |Mit dem Office 365-APIs können Sie den Zugriff auf die Office 365 Daten Ihrer Kunden ermöglichen, einschließlich der Dinge, die Ihnen am meisten wichtig sind: e-Mail, Kalender, Kontakte, Benutzer und Gruppen, Dateien und Ordner. In diesem Artikel ist ein gutes Diagramm dargestellt, das die Beziehung zwischen Office 365 apps, Azure AD und den Daten illustriert, auf die die apps zugreifen.  <br/> |
|[Integrieren von Anwendungen in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/develop/quickstart-v1-add-azure-ad-app) <br/> | Erfahren Sie mehr über Anwendungen, die in Azure Active Directory integriert sind, und wie Sie Ihre Anwendung registrieren, Konzepte hinter einer registrierten Anwendung verstehen und Informationen zu Branding-Richtlinien für mehr Mandanten Anwendungen erhalten.  <br/> |
|[Lernprogramme zur Azure-Active Directory Integration](https://docs.microsoft.com/azure/active-directory/saas-apps/tutorial-list) <br/> |Das Ziel dieser Lernprogramme ist es, Ihnen zu zeigen, wie Sie Azure AD SSO für SaaS-Anwendungen von Drittanbietern konfigurieren.  <br/> |
|[Authentifizierungsszenarien für Azure AD](https://go.microsoft.com/fwlink/?LinkId=617145) <br/> |Azure AD vereinfacht die Authentifizierung für Entwickler durch die Bereitstellung von Identität als Dienst, mit Unterstützung für Branchenstandard Protokolle wie OAuth 2,0 und OpenID Connect sowie Open Source-Bibliotheken für verschiedene Plattformen, mit denen Sie schnell mit der Codierung beginnen können. Dieses Dokument hilft Ihnen, die verschiedenen Szenarien zu verstehen Azure Ad unterstützt und zeigt Ihnen, wie Sie beginnen.  <br/> |
|[Anwendungszugriff](https://docs.microsoft.com/azure/active-directory/manage-apps/what-is-access-management) <br/> |Azure AD ermöglicht eine einfache Integration in viele der heute gängigen Software as a Service (SaaS)-Anwendungen. Es bietet Identitäts-und Zugriffsverwaltung und bietet eine Zugriffsgruppe für Benutzer, in der Sie ermitteln können, welche Anwendungs Zugriffe Sie haben und wo Sie SSO verwenden können, um auf Ihre Anwendungen zuzugreifen. In diesem Artikel finden Sie Links zu den zugehörigen Ressourcen, in denen Sie weitere Informationen zu den Anwendungszugriffs Verbesserungen für Azure AD und dazu beitragen können.  <br/> |
|[Personalisieren Ihrer Office 365 Erfahrung](https://support.office.com/article/eb34a21b-52fa-4fbf-a8d5-146132242985) <br/> |Sie können schnellen Zugriff auf die apps erhalten, die Sie täglich verwenden, indem Sie apps im Office 365-App-Startfeld hinzufügen oder entfernen.  <br/> |
   

