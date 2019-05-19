---
title: Office 365 Identitäts Modelle und Azure Active Directory
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
ms.openlocfilehash: 1d4a2f40ebae9fa87d59ee3f7c9b621b40b03640
ms.sourcegitcommit: 36e760407a1f4b18bc108134628ed9a8d3e35a8a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2019
ms.locfileid: "34162388"
---
# <a name="office-365-identity-models-and-azure-active-directory"></a>Office 365 Identitäts Modelle und Azure Active Directory

Office 365 verwendet Azure Active Directory (Azure AD), eine Cloud-basierte Benutzeridentität und einen Authentifizierungsdienst, der in Ihrem Office 365-Abonnement enthalten ist, um Identitäten und Authentifizierung für Office 365 zu verwalten. Die ordnungsgemäße Konfiguration Ihrer Identitätsinfrastruktur ist für die Verwaltung Office 365 Benutzerzugriffs und der Berechtigungen für Ihre Organisation unerlässlich.

Bevor Sie beginnen, sehen Sie sich dieses Video an, um eine Übersicht über Identitäts Modelle und Authentifizierung für Office 365 und Microsoft 365 zu erhalten.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE2Pjwu]

Ihre erste Planungs Wahl ist das Office 365 Identitätsmodell.

## <a name="office-365-identity-models"></a>Office 365 Identitäts Modelle

Um Benutzerkonten zu planen, müssen Sie zunächst die beiden Identitäts Modelle in Microsoft 365 verstehen. Sie können die Identitäten Ihrer Organisation nur in der Cloud verwalten, oder Sie können Ihre lokalen Active Directory-Domänendienste (AD DS)-Identitäten beibehalten und für die Authentifizierung verwenden, wenn Benutzer auf Microsoft 365 Cloud Services zugreifen.  

Hier sind die beiden Arten von Identität und Ihre beste Anpassung und Vorteile.

|||
|:-------|:-----|:-----|
|  | **Nur Cloud-Identität** | **Hybrid Identität** |
| **Definition** | Das Benutzerkonto ist nur im Azure Active Directory (Azure AD)-Mandanten für Ihr Microsoft 365-Abonnement vorhanden. | Das Benutzerkonto ist in AD DS vorhanden, und eine Kopie befindet sich auch im Azure AD-Mandanten für Ihr Microsoft 365-Abonnement. Das Benutzerkonto in Azure AD kann auch eine gehashte Version des Benutzerkontokennworts enthalten. |
| **So authentifiziert Microsoft 365 Benutzeranmeldeinformationen** | Der Azure AD Mandant für Ihr Microsoft 365-Abonnement führt die Authentifizierung mit dem Cloud-Identitätskonto aus. | Der Azure AD Mandant für Ihr Microsoft 365-Abonnement verarbeitet entweder den Authentifizierungsprozess oder leitet den Benutzer an einen anderen Identitätsanbieter um. |
| **Am besten für** | Organisationen, die keine lokale AD DS haben oder benötigen. | Organisationen, die AD DS oder einen anderen Identitätsanbieter verwenden. |
| **Größter Vorteil** | Einfach zu verwenden. Keine zusätzlichen Verzeichnis Tools oder Server erforderlich. | Benutzer können beim Zugriff auf lokale oder Cloud-basierte Ressourcen dieselben Anmeldeinformationen verwenden. |
||||

## <a name="cloud-only-identity"></a>Nur Cloud-Identität

Eine Cloud-only-Identität verwendet Benutzerkonten, die nur in Azure AD vorhanden sind. Die Cloud-Identität wird in der Regel von kleinen Organisationen verwendet, die nicht über lokale Server verfügen oder AD DS nicht zum Verwalten lokaler Identitäten verwenden. 

Hier sind die grundlegenden Komponenten der reinen cloudbasierten Identität.
 
![](./media/about-office-365-identity/cloud-only-identity.png)

Sowohl lokale als auch Remotebenutzer verwenden Ihre Azure AD Benutzerkonten und Kennwörter für den Zugriff auf Office 365 Cloud-Dienste. Azure AD authentifiziert Benutzeranmeldeinformationen basierend auf den gespeicherten Benutzerkonten und Kennwörtern.

### <a name="administration"></a>Verwaltung
Da Benutzerkonten nur in Azure AD gespeichert werden, verwalten Sie Cloud-Identitäten mit Tools wie dem [Microsoft 365 Admin Center](https://admin.microsoft.com) und Windows PowerShell mit dem Azure Active Directory PowerShell für Graph-Modul. 

## <a name="hybrid-identity"></a>Hybrid Identität

Hybrid Identity verwendet Konten, die in einer lokalen AD DS stammen und über eine Kopie im Azure AD Mandanten eines Microsoft 365-Abonnements verfügen. Die meisten Änderungen fließen jedoch nur in eine Richtung. Änderungen, die Sie an AD DS Benutzerkonten vornehmen, werden mit Ihrer Kopie in Azure AD synchronisiert. Änderungen, die an cloudbasierten Konten in Azure AD vorgenommen werden, wie beispielsweise neue Benutzerkonten, werden jedoch nicht mit AD DS synchronisiert.

Azure AD Connect stellt die laufende Konto Synchronisierung bereit. Er wird auf einem lokalen Server ausgeführt, überprüft auf Änderungen im AD DS und leitet diese Änderungen an Azure AD weiter. Azure AD Connect bietet die Möglichkeit, zu filtern, welche Konten synchronisiert werden, und ob eine gehashte Version von Benutzerkennwörtern synchronisiert werden soll, die als Password Hash Synchronization (PHS) bezeichnet wird.

Wenn Sie die Hybrid Identität implementieren, ist Ihre lokale AD DS die autorisierende Quelle für Kontoinformationen. Dies bedeutet, dass Sie Verwaltungsaufgaben meist lokal ausführen, die dann mit Azure AD synchronisiert werden. 

Hier sind die Komponenten der Hybrid Identität.

![](./media/about-office-365-identity/hybrid-identity.png)

Der Azure AD Mandant verfügt über eine Kopie der AD DS Konten. In dieser Konfiguration authentifizieren sich sowohl lokale als auch Remotebenutzer, die auf Microsoft 365 Cloud Services zugreifen, bei Azure AD.

>[!Note]
>Sie müssen immer Azure AD Connect verwenden, um Benutzerkonten für die Hybrid Identität zu synchronisieren. Sie benötigen die synchronisierten Benutzerkonten in Azure AD, um die Lizenzzuweisung und Gruppenverwaltung, Berechtigungen konfigurieren und andere administrative Aufgaben, die Benutzerkonten umfassen, auszuführen.
>

### <a name="administration"></a>Verwaltung

Da die ursprünglichen und autorisierenden Benutzerkonten in der lokalen AD DS gespeichert werden, verwalten Sie Ihre Identitäten mit denselben Tools wie AD DS, beispielsweise das Tool Active Directory Benutzer und Computer. 

Sie verwenden nicht das Microsoft 365 Admin Center oder Windows PowerShell zum Verwalten synchronisierter Benutzerkonten in Azure AD.

## <a name="next-step"></a>Nächster Schritt

Wenn Sie das Cloud-only-Identitätsmodell benötigen, lesen Sie [nur Cloud-Identitäten](cloud-only-identities.md).

Wenn Sie das hybride Identitätsmodell benötigen, lesen Sie [Planung für Ihre synchronisierten Identitäten und Authentifizierungsmethoden](plan-for-directory-synchronization.md).
  

## <a name="video-training"></a>Videoschulung

Weitere Informationen finden Sie unter Video Kurs [Office 365: Verwalten von Identitäten mit Azure AD Connect](https://support.office.com/article/90991a1d-c0ab-479a-b413-35c9706f6fed.aspx), die Ihnen von LinkedIn Learning zur Verbringung bereitgestellt werden.
