---
title: Grundlegendes zu Office 365-Identität und Azure Active Directory
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 5/1/2018
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MOE150
- BCS160
ms.assetid: 06a189e7-5ec6-4af2-94bf-a22ea225a7a9
description: Hier erfahren Sie, wie die Identität des Benutzers in Office 365 verwaltet wird.
ms.openlocfilehash: cdd0ab2306e9a966f308006761a83cda8989b898
ms.sourcegitcommit: f42ca73d23beb5770981e7a93995ef3be5e341bb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/08/2018
ms.locfileid: "22213117"
---
# <a name="understanding-office-365-identity-and-azure-active-directory"></a>Grundlegendes zu Office 365-Identität und Azure Active Directory

Office 365 verwendet Cloud-basierten Benutzer Identität und Authentifizierung Service Azure Active Directory (AD Azure) zum Verwalten von Benutzern. Auswählen ist zwischen der lokalen Organisation und Office 365 Identitätsmanagement konfiguriert ist eine frühe Entscheidung, die eine der Grundlagen der Cloud-Infrastruktur ist. Ändern diese Konfiguration später schwierig sein kann, sorgfältige Planung der Optionen, um festzulegen, was für die Anforderungen Ihrer Organisation am besten geeignet. Sie können auswählen, aus zwei Hauptfenster Authentifizierungsmodelle in Office 365 zum Einrichten und Verwalten von Benutzerkonten. Cloud-Authentifizierung und Verbundauthentifizierung.
  
Es ist wichtig, die Authentifizierung und Identität Objektmodell zum Abrufen von sorgfältige Planung und wird ausgeführt. Überlegen Sie die Zeit, vorhandene Komplexität und Kosten zu implementieren und Verwalten der Authentifizierung und Identität Entwurfsoptionen. Diese Faktoren sind für jede Organisation unterschiedlich. und Sie sollten verstehen, die wichtigsten Konzepte für die identitätsoptionen, mit denen Sie die Authentifizierung und Identitätsmodell auswählen, dass Sie für die Bereitstellung verwenden möchten.
  
## <a name="cloud-authentication"></a>Cloud-Authentifizierung

Je nachdem, wenn Sie einem vorhandenen Active Directory-Umgebung lokalen haben nicht oder haben, haben Sie mehrere Optionen zum Verwalten von Authentifizierung und Identität Services für Ihre Benutzer mit Office 365.
  
### <a name="cloud-only"></a>Reine Cloudbereitstellung

Mit dem Cloud-only-Objektmodell verwalten Sie Ihre Benutzerkonten nur in Office 365. Es sind keine lokalen Server erforderlich. Es ist in der Cloud von Azure AD behandelt. Erstellen und Verwalten von Benutzern in Office 365 Administrationscenter oder mithilfe von Windows PowerShell [PowerShell-Cmdlets](https://go.microsoft.com/fwlink/p/?LinkId=698471) und Identität und Authentifizierung gekennzeichnete vollständig in der Cloud von Azure Active Directory. Das Cloud-only-Modell wird in der Regel eine gute Choice, wenn: 
  
- Sie haben keine lokalen Benutzerverzeichnis.
    
- Es ist ein sehr komplex lokalen Verzeichnis und einfach die Arbeit mit Integration von vermeiden möchten.
    
- Sie haben ein vorhandenes lokalen Verzeichnis, aber Sie eine Testversion oder von Office 365-Pilotphase ausführen möchten. Sie können das Cloud-Benutzer, um lokale Benutzer später, wenn Sie Verbindung mit Ihrem lokalen Verzeichnis bereit sind übereinstimmen.
    
Um mit cloudidentität beginnen, finden Sie unter [Einrichten von Office 365 für Unternehmen](https://support.office.com/article/6a3a29a0-e616-4713-99d1-15eda62d04fa).
  
### <a name="password-hash-sync-with-seamless-single-sign-on"></a>Hash kennwortsynchronisierung mit nahtlos einmaliges Anmelden

Die einfachste Möglichkeit zum Aktivieren der Authentifizierung für lokale-Directory-Objekte in Azure Active Directory. Mit Hash kennwortsynchronisierung (PBS) Ihre lokale Active Directory User Account-Objekten mit Office 365 synchronisieren und Ihre lokalen Benutzer verwalten. Hashes von Benutzerkennwörtern werden aus der lokalen Active Directory in Azure Active Directory synchronisiert, damit der Benutzer das gleiche Kennwort lokale haben und in der Cloud. Wenn Kennwörter geändert werden oder lokalen zurückgesetzt wird, werden die neuen Kennworthashes Azure AD synchronisiert, damit Ihre Benutzer immer dasselbe Kennwort für Cloudressourcen und lokale Ressourcen verwenden können. Die Kennwörter werden nie Azure AD gesendet oder in Azure AD in Klartext gespeichert. Einige Premium-Features von Azure Active Directory, beispielsweise Schutz, erfordern PBS unabhängig davon, welche Authentifizierungsmethode ausgewählt ist. Mit nahtlos einmaliges Anmelden werden Benutzer automatisch Azure AD angemeldet wann sie auf ihren Geräten im Unternehmen werden und mit dem Unternehmensnetzwerk verbunden ist.
  
Weitere Informationen zur [Auswahl Hash kennwortsynchronisierung](https://docs.microsoft.com/en-us/azure/security/azure-ad-choose-authn) und [nahtlose einmaliges Anmelden](https://docs.microsoft.com/en-us/azure/active-directory/connect/active-directory-aadconnect-sso).
  
### <a name="pass-through-authentication-with-seamless-single-sign-on"></a>Pass-Through-Authentifizierung mit nahtlos einmaliges Anmelden

Ein einfaches Kennwort Geschäftstyp für Azure AD-Authentifizierungsdienste die Überprüfung der Benutzer direkt mit Ihrem lokalen Active Directory mithilfe eines Software-Agents auf einem oder mehreren lokalen Servern ausgeführt. Mit Pass-Through-Authentifizierung (PTA) lokalen Active Directory User Account-Objekten mit Office 365 synchronisieren und Ihre lokalen Benutzer verwalten. Können Benutzer anmelden bei lokalen und Office 365-Ressourcen und Anwendungen, die die lokale Konto und Kennwort verwenden. Diese Konfiguration überprüft die Kennwörter der Benutzer direkt für die lokale Active Directory unbeantwortet Kennworthashes zu Office 365. Unternehmen mit Sicherheit erforderlich zum Erzwingen von lokalen Benutzerkonto sofort besagt Kennwortrichtlinien und Anmeldezeit diese Authentifizierungsmethode verwenden würden. Mit nahtlos einmaliges Anmelden werden Benutzer automatisch Azure AD angemeldet wann sie auf ihren Geräten im Unternehmen werden und mit dem Unternehmensnetzwerk verbunden ist.
  
Weitere Informationen zur [Auswahl von Pass-Through-Authentifizierung](https://docs.microsoft.com/en-us/azure/security/azure-ad-choose-authn) und [nahtlos einmaliges Anmelden](https://docs.microsoft.com/en-us/azure/active-directory/connect/active-directory-aadconnect-sso).
  
## <a name="federated-authentication-options"></a>Optionen für Verbundauthentifizierung

Wenn Sie einem vorhandenen Active Directory-Umgebung lokalen verfügen, können Sie Office 365 mit dem Verzeichnis integrieren, mithilfe von Verbundauthentifizierung zum Verwalten von Authentifizierung und Identität Services für Ihre Benutzer in Office 365.
  
### <a name="federated-identity-with-active-directory-federation-services-ad-fs"></a>Identitätsverbund mit Active Directory-Verbunddienste (AD FS)

In erster Linie für große Unternehmen mit komplexen Anforderungen für die Authentifizierung lokaler Verzeichnisobjekte mit Office 365 synchronisiert werden und Benutzerkonten sind lokale verwaltete. Benutzer können mit AD FS, das gleiche Kennwort: lokal und in der Cloud und nicht erneut anmelden bei Office 365 verwenden lassen. Dieses Modell Verbundauthentifizierung bieten zusätzliche Anforderungen für die Authentifizierung, wie Smartcard-basierte Authentifizierung oder einem Drittanbieter-mehrstufige Authentifizierung und ist in der Regel erforderlich, wenn Organisationen eine Authentifizierung erforderlich ist von Azure AD unterstützt systemintern nicht.
  
Weitere Informationen zur [Auswahl Identitätsverbund mit AD FS](https://docs.microsoft.com/en-us/azure/security/azure-ad-choose-authn).
  
### <a name="third-party-authentication-and-identity-providers"></a>Drittanbieter-Anbieter für die Authentifizierung und Identität

Lokaler Verzeichnisobjekte möglicherweise zu Office 365 synchronisiert und Ressourcenzugriff Cloud wird hauptsächlich von einem Drittanbieter-STS-Anbieter (IdP) verwaltet. Wenn Ihre Organisation eine Lösung Drittanbieter-Verbund verwendet, können Sie einmaliges Anmelden mit dieser Lösung für Office 365 konfigurieren vorausgesetzt, dass die Lösung Drittanbieter-Verbund mit Azure AD kompatibel ist.
  
Weitere Informationen zur [Kompatibilität von Azure Active Directory Federation](https://docs.microsoft.com/en-us/azure/active-directory/connect/active-directory-aadconnect-federation-compatibility).
  
## <a name="configuring-identity-and-authentication-with-office-365"></a>Konfigurieren von Identität und Authentifizierung mit Office 365

Integrieren Ihre lokale Verzeichnisse in Office 365 und Azure AD wurde mit " [Connect" Azure AD](https://docs.microsoft.com/en-us/azure/active-directory/connect/active-directory-aadconnect)vereinfacht. Azure Active Directory verbinden ist die beste Möglichkeit zum Verbinden Ihrer Verzeichnisse und Microsofts Empfehlung für Organisationen, die die Benutzer in die Cloud zu synchronisieren.
  
Sie können auch die Azure AD-Berater: der [Azure AD-Connect Advisor](https://aka.ms/aadconnectpwsync), den [AD FS-Bereitstellung Advisor](https://aka.ms/adfsguidance)und die [Azure AD Premium Handbuch](https://aka.ms/aadpguidance).
  
## <a name="video-training"></a>Video-Schulung

Weitere Informationen finden Sie im video Kurs [Office 365: Verwalten von Identitäten mithilfe von Azure Active Directory verbinden](https://support.office.com/article/90991a1d-c0ab-479a-b413-35c9706f6fed.aspx), bereitgestellt von LinkedIn Learning.
  
## <a name="see-also"></a>Siehe auch

[Vorbereiten der Bereitstellung von Benutzern über die Verzeichnissynchronisierung in Office 365](https://support.office.com/article/prepare-to-provision-users-through-directory-synchronization-to-office-365-01920974-9e6f-4331-a370-13aea4e82b3e)
  
[Verbinden Sie PowerShell zu Office 365-Diensten](https://support.office.com/article/06a743bb-ceb6-49a9-a61d-db4ffdf54fa6)
  
[Beheben von Problemen mit der verzeichnissynchronisierung für Office 365](https://support.office.com/article/fixing-problems-with-directory-synchronization-for-office-365-79c43023-5a47-45ae-8068-d8a26eee6bc2d)
  
