---
title: Grundlegendes zu Office 365-Identitäten und Azure Active Directory
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- M365-identity-device-management
- M365-security-compliance
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 06a189e7-5ec6-4af2-94bf-a22ea225a7a9
description: Erfahren Sie, wie die Benutzeridentität in Office 365 verwaltet wird.
ms.openlocfilehash: 85cfce4b08236bfcee74b6fe6d9c29766e7211c6
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068761"
---
# <a name="understanding-office-365-identity-and-azure-active-directory"></a>Grundlegendes zu Office 365-Identitäten und Azure Active Directory

Office 365 verwendet die Cloud-basierte Benutzeridentität und den Authentifizierungsdienst Azure Active Directory (Azure AD), um Benutzer zu verwalten. Die Auswahl, ob die Identitätsverwaltung zwischen Ihrer lokalen Organisation und Office 365 konfiguriert ist, ist eine frühe Entscheidung, die eine der Grundlagen ihrer Cloud-Infrastruktur darstellt. Da eine spätere Änderung dieser Konfiguration schwierig sein kann, sollten Sie die Optionen sorgfältig prüfen, um zu bestimmen, welche Anforderungen für Ihre Organisation am besten geeignet sind. Sie können zwischen zwei Haupt Authentifizierungsmodellen in Office 365 wählen, um Benutzerkonten einzurichten und zu verwalten. **Cloud-Authentifizierung** und **Verbundauthentifizierung**.
  
Es ist wichtig, sorgfältig zu überlegen, welche Authentifizierungs-und Identitäts Modelle für die Inbetriebnahme verwendet werden sollen. Denken Sie an die Zeit, die vorhandene Komplexität und die Kosten für die Implementierung und Verwaltung der einzelnen Authentifizierungs-und Identitäts Optionen. Diese Faktoren sind für jede Organisation unterschiedlich; Sie sollten die wichtigsten Konzepte für die Identitäts Optionen kennen, die Ihnen bei der Auswahl der Authentifizierungs-und Identitäts Modelle helfen sollen, die Sie für Ihre Bereitstellung verwenden möchten.
  
## <a name="cloud-authentication"></a>Cloud-Authentifizierung

Je nachdem, ob Sie über eine lokale Active Directory-Umgebung verfügen oder nicht, haben Sie mehrere Möglichkeiten, Authentifizierungs-und Identitätsdienste für Ihre Benutzer mit Office 365 zu verwalten.
  
### <a name="cloud-only"></a>Rein cloudbasiert

Mit dem reinen Cloud-Modell verwalten Sie Ihre Benutzerkonten nur in Office 365. Es sind keine lokalen Server erforderlich; Es wird in der Cloud von Azure AD behandelt. Sie erstellen und verwalten Benutzer im [Microsoft 365 Admin Center](https://admin.microsoft.com) oder mithilfe von [PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/manage-office-365-with-office-365-powershell) -Cmdlets von Windows PowerShell, und Identität und Authentifizierung werden vollständig in der Cloud von Azure AD behandelt. Das Cloud-Modell ist in der Regel eine gute Wahl, wenn: 
  
- Sie haben kein anderes lokales Benutzerverzeichnis.
    
- Sie verfügen über ein sehr komplexes lokales Verzeichnis und möchten lediglich die Arbeit vermeiden.
    
- Sie verfügen über ein vorhandenes lokales Verzeichnis, möchten aber eine Testversion oder einen Pilot von Office 365 ausführen. Später können Sie die Cloud-Benutzer lokalen Benutzern zuordnen, wenn Sie bereit sind, eine Verbindung mit Ihrem lokalen Verzeichnis herzustellen.
    
Informationen zu den ersten Schritten mit Cloud Identity finden Sie unter [Einrichten von Office 365 for Business](https://support.office.com/article/6a3a29a0-e616-4713-99d1-15eda62d04fa).
  
### <a name="password-hash-sync-with-seamless-single-sign-on"></a>Kennworthash Synchronisierung mit nahtlosem einmaligem Anmelden

Die einfachste Möglichkeit zum Aktivieren der Authentifizierung für lokale Verzeichnisobjekte in Azure AD. Mit Password Hash Sync (PHS) synchronisieren Sie Ihre lokalen Active Directory-Benutzerkonto Objekte mit Office 365 und verwalten Ihre Benutzer lokal. Hashes von Benutzerkennwörtern werden aus Ihrem lokalen Active Directory mit Azure AD synchronisiert, sodass die Benutzer über das gleiche Kennwort lokal und in der Cloud verfügen. Wenn Kennwörter geändert oder lokal zurückgesetzt werden, werden die neuen Kenn Wort Hashes mit Azure AD synchronisiert, sodass Ihre Benutzer immer dasselbe Kennwort für Cloud-Ressourcen und lokale Ressourcen verwenden können. Die Kennwörter werden nie an Azure AD gesendet oder in Azure AD in Klartext gespeichert. Einige Premium Features von Azure AD, wie Identitätsschutz, erfordern PHS, unabhängig davon, welche Authentifizierungsmethode ausgewählt ist. Mit dem nahtlosen einmaligen Anmelden werden Benutzer automatisch bei Azure AD angemeldet, wenn Sie sich auf Ihren Unternehmensgeräten befinden und mit dem Unternehmensnetzwerk verbunden sind.
  
Hier finden Sie weitere Informationen zum [Auswählen der Kennworthash Synchronisierung](https://docs.microsoft.com/azure/security/azure-ad-choose-authn) und [des nahtlosen einmaligen Anmeldens](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-sso).
  
### <a name="pass-through-authentication-with-seamless-single-sign-on"></a>Passthrough-Authentifizierung mit nahtlosem einmaligem Anmelden

Bietet eine einfache Kennwortüberprüfung für Azure AD-Authentifizierungsdienste mit einem Software-Agent, der auf einem oder mehreren lokalen Servern ausführt, um die Benutzer direkt mit Ihrem lokalen Active Directory zu überprüfen. Mit der Passthrough-Authentifizierung (PTA) synchronisieren Sie lokale Active Directory-Benutzerkonto Objekte mit Office 365 und verwalten Ihre Benutzer lokal. Ermöglicht Benutzern das Anmelden bei lokalen und Office 365-Ressourcen und-Anwendungen mithilfe des lokalen Kontos und des Kennworts. Diese Konfiguration validiert Benutzerkennwörter direkt für Ihr lokales Active Directory, ohne Kenn Wort Hashes an Office 365 zu senden. Unternehmen mit einer Sicherheitsanforderung zum sofortigen Erzwingen von lokalen Benutzerkontostatus, Kennwortrichtlinien und Anmeldezeiten würden diese Authentifizierungsmethode verwenden. Mit dem nahtlosen einmaligen Anmelden werden Benutzer automatisch bei Azure AD angemeldet, wenn Sie sich auf Ihren Unternehmensgeräten befinden und mit dem Unternehmensnetzwerk verbunden sind.
  
Erfahren Sie mehr über die [Auswahl der Passthrough-Authentifizierung](https://docs.microsoft.com/azure/security/azure-ad-choose-authn) und [des nahtlosen einmaligen Anmeldens](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-sso).
  
## <a name="federated-authentication-options"></a>Optionen für die Verbundauthentifizierung

Wenn Sie über eine lokale Active Directory-Umgebung verfügen, können Sie Office 365 mithilfe der Verbundauthentifizierung in Ihr Verzeichnis integrieren, um Authentifizierungs-und Identitätsdienste für Ihre Benutzer in Office 365 zu verwalten.
  
### <a name="federated-identity-with-active-directory-federation-services-ad-fs"></a>Verbundidentität mit Active Directory-Verbunddiensten (AD FS)

In erster Linie für große Unternehmensorganisationen mit komplexeren Authentifizierungsanforderungen werden lokale Verzeichnisobjekte mit Office 365 synchronisiert, und Benutzerkonten werden lokal verwaltet. Bei AD FS haben Benutzer das gleiche Kennwort lokal und in der Cloud, und Sie müssen sich nicht erneut anmelden, um Office 365 zu verwenden. Dieses Verbund Authentifizierungsmodell kann zusätzliche Authentifizierungsanforderungen wie Smartcard-basierte Authentifizierung oder eine Drittanbieter-mehrstufige Authentifizierung bereitstellen und ist normalerweise erforderlich, wenn Organisationen über eine Authentifizierungsanforderung verfügen. von Azure AD nicht nativ unterstützt.
  
Erfahren Sie mehr über die [Auswahl der Verbundidentität mit AD FS](https://docs.microsoft.com/azure/security/azure-ad-choose-authn).
  
### <a name="third-party-authentication-and-identity-providers"></a>Authentifizierungs-und Identitätsanbieter von Drittanbietern

Lokale Verzeichnisobjekte können mit Office 365 synchronisiert werden, und der Zugriff auf Cloud-Ressourcen wird hauptsächlich von einem Drittanbieter-Identitätsanbieter (IDP) verwaltet. Wenn in Ihrer Organisation eine Drittanbieter-Verbundlösung verwendet wird, können Sie die Anmeldung mit dieser Lösung für Office 365 konfigurieren, vorausgesetzt, dass die Drittanbieter-Verbundlösung mit Azure AD kompatibel ist.
  
Erfahren Sie mehr über die [Kompatibilität mit Azure AD-Verbund](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-federation-compatibility).
  
## <a name="configuring-identity-and-authentication-with-office-365"></a>Konfigurieren von Identität und Authentifizierung mit Office 365

Die Integration Ihrer lokalen Verzeichnisse in Office 365 und Azure AD wurde mit [Azure AD Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect)vereinfacht. Azure AD Connect ist die beste Möglichkeit zum Verbinden Ihrer Verzeichnisse und ist die Empfehlung von Microsoft für Organisationen, Ihre Benutzer mit der Cloud zu synchronisieren.
  
Sie können auch die Azure AD Advisors verwenden: den [Azure AD Connect Advisor](https://aka.ms/aadconnectpwsync), den [AD FS-Bereitstellungs Ratgeber](https://aka.ms/adfsguidance)und das [Azure AD Premium-Setup Handbuch](https://aka.ms/aadpguidance).
  
## <a name="video-training"></a>Videoschulung

Weitere Informationen finden Sie im Video Kurs [Office 365: Verwalten von Identitäten mithilfe von Azure AD Connect](https://support.office.com/article/90991a1d-c0ab-479a-b413-35c9706f6fed.aspx), die Ihnen von LinkedIn Learning präsentiert werden.
