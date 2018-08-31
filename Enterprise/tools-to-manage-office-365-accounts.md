---
title: Tools zum Verwalten von Office 365-Benutzerkonten
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- BCS160
ms.assetid: 98ca5b3f-f720-4d8e-91be-fe656548a25a
description: 'Hier erfahren Sie, welche Tools für Office 365-Benutzer zu verwalten, und wie für die Verwaltung von Benutzeridentitäten hängt wie was Sie verwenden können. '
ms.openlocfilehash: 62467fb031090a521d0b9e067582b56fabe9e5fd
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540788"
---
# <a name="tools-to-manage-office-365-accounts"></a>Tools zum Verwalten von Office 365-Benutzerkonten

Sie können Office 365-Benutzer auf verschiedene Arten, je nach Konfiguration verwalten. Sie können die Benutzer im Office 365 Administrationscenter, Windows PowerShell, Ihr Verzeichnis lokalen oder in Azure Active Directory-Admin-Portal verwalten. 

Sobald Sie Office 365 kaufen, kann der-Verwaltungskonsole und Windows PowerShell zum Verwalten von Konten verwendet werden. Beim Verwalten von cloudidentitäten hat jede Person in Ihrer Organisation einen separaten Benutzer-ID und ein Kennwort für Office 365. Wenn Sie möchten Ihre lokale Infrastruktur integrieren und Benutzerkonten mit Office 365 synchronisiert, können Azure Active Directory verbinden Sie Synchronisierung von Identitäten bereitstellen und optional bieten kennwortsynchronisierung oder full Einmaliges Anmelden-Funktionalität.
  
## <a name="plan-for-where-and-how-you-will-manage-your-user-accounts"></a>Planen, wo und wie Sie Ihre Benutzerkonten verwalten

Wo und wie Sie Ihre Benutzerkonten verwalten können, hängt von der Identitätsmodell, den, das Sie für Ihre Office 365 verwenden möchten. Die zwei allgemeine Modelle sind Cloud-Authentifizierung und Verbundauthentifizierung.
  
### <a name="cloud-authentication"></a>Cloud-Authentifizierung

<<<<<<< HEAD
- [Authentifizierung von Cloud](about-office-365-identity.md#cloud-authentication) - erstellen und Verwalten von Benutzern in Office 365 Administrationscenter, Sie können Windows PowerShell oder Azure Active Directory auch verwenden, um Benutzer zu verwalten. 
    
=======
- [Office 365-Identität](about-office-365-identity.md) - erstellen und Verwalten von Benutzern in Office 365 Administrationscenter, Sie können Windows PowerShell oder Azure Active Directory auch verwenden, um Benutzer zu verwalten.
>>>>>>> Robmazz-Konvertierung
- [Kennworthash synchronisieren mit nahtlos einmaliges Anmelden](about-office-365-identity.md) – die einfachste Möglichkeit zum Aktivieren der Authentifizierung für lokale-Directory-Objekte in Azure Active Directory. Mit Hash kennwortsynchronisierung (PBS) Ihre lokale Active Directory User Account-Objekten mit Office 365 synchronisieren und Ihre lokalen Benutzer verwalten. 
- [Pass-Through-Authentifizierung mit nahtlos einmaliges Anmelden](about-office-365-identity.md) - Geschäftstyp ein einfaches Kennwort für Azure AD-Authentifizierungsdienste mithilfe eines Software-Agents, die auf einem oder mehreren lokalen Servern ausgeführt für die Überprüfung der Benutzer direkt mit Ihrer lokale Active Directory. 
    
### <a name="federated-authentication"></a>Verbundauthentifizierung

<<<<<<< HEAD
- [Pass-Through-Authentifizierung mit nahtlos einmaliges Anmelden](about-office-365-identity.md#pass-through-authentication-with-seamless-single-sign-on) - lokale in erster Linie für große Unternehmen mit komplexen Anforderungen für die Authentifizierung, Verzeichnisobjekte mit Office 365 synchronisiert werden und die Benutzerkonten verwaltet werden lokale. 
    
=======
- [Office 365-Identität](about-office-365-identity.md) - lokale in erster Linie für große Unternehmen mit komplexen Anforderungen für die Authentifizierung, Verzeichnisobjekte mit Office 365 synchronisiert werden und Benutzerkonten sind lokale verwaltete. 
>>>>>>> Robmazz-Konvertierung
- [Authentifizierung und Identität Drittanbieter](about-office-365-identity.md) - lokalen Verzeichnis Objekte möglicherweise auf Office 365 synchronisiert und Ressourcenzugriff cloud wird hauptsächlich von einem Drittanbieter-STS-Anbieter (IdP) verwaltet. 
    
## <a name="managing-accounts"></a>Verwalten von Konten

Beachten Sie bei der Entscheidung, wie Ihre Organisation erstellen und Verwalten von Konten wird Folgendes:
  
- Die Directory-Synchronisierung-Software muss auf Servern in Ihrer lokalen Umgebung für die Verbindung die Identitäten zwischen Office 365 und Ihrer lokalen Verzeichnis installiert werden.
- Eine beliebige Option Directory Synchronization, einschließlich der SSO-Optionen erfordert, dass Ihre lokalen Verzeichnisattributen Standards entsprechen. Die Merkmale der Verwendung von Attributen in Ihrem Verzeichnis verwendet werden und welche Cleanup (falls vorhanden) erforderlich ist, werden unter [Prepare to Provision Benutzer über Directory-Synchronisierung mit Office 365](prepare-for-directory-synchronization.md)beschrieben. Anweisung zum IdFix verwenden, um verzeichnisbereinigung automatisieren finden Sie unter [Installieren und führen Sie das Office 365 IdFix-Tool](install-and-run-idfix.md) . 
    
## <a name="plan-how-you-are-going-to-create-office-365-accounts"></a>Planen Sie, wie Sie den zum Erstellen von Office 365-Konten
Die folgende Tabelle enthält die anderen Konto-Verwaltungstools:
    
|**Option**|**Hinweise**|
|:-----|:-----|
|**Office 365 Admin Center** | - [Hinzufügen von Benutzern einzeln oder in einer Sammeloperation zu Office 365 - Admin-Hilfe](https://support.office.com/article/1970f7d6-03b5-442f-b385-5880b9c256ec) <br> -Bietet eine einfache Weboberfläche zum Hinzufügen und Ändern von Benutzerkonten. <br> -Kann nicht verwendet werden, um Benutzer zu ändern, wenn die verzeichnissynchronisierung aktiviert ist (Speicherort- und lizenzzuweisung hingegen kann festgelegt werden). <br> -Kann nicht mit SSO-Optionen verwendet werden. <br> |
|**Windows PowerShell** | - [Verwalten von Office 365 mit Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=698471) <br> -Können Sie zum Hinzufügen von Benutzern in einer Sammeloperation Benutzer mithilfe eines Windows PowerShell-Skripts. <br> -Kann verwendet werden, zum Zuweisen von Speicherort und Lizenz zu Konten, unabhängig davon, wie die Konten erstellt werden. <br> |
|**Massenimport** | - [Hinzufügen von vielen Benutzern gleichzeitig zu Office 365 - Admin-Hilfe](add-several-users-at-the-same-time.md) <br> – Ermöglicht das Importieren einer CSV-Datei, um eine Gruppe von Benutzern zu Office 365 hinzuzufügen. <br> -Kann nicht mit SSO-Optionen verwendet werden. <br> |
|**Azure Active Directory** | -Sie erhalten eine kostenlose Version von Azure Active Directory mit Ihrem Office 365-Abonnement. -Sie können Funktionen wie Self-service-Kennwort zurücksetzen für Cloud-Benutzern und Anpassung der Anmeldung und Zugriff Systemsteuerung Seiten mithilfe der kostenlosen Edition ausführen.<br> -Wenn Sie um erweiterten Funktionalität zu erhalten, können Sie entweder die grundlegende Edition oder die Premium Edition aktualisieren. Die Liste der unterstützten Funktionen finden Sie unter [Azure Active Directory-Editionen](https://go.microsoft.com/fwlink/p/?LinkId=698465) .<br> |
|**Directory-Synchronisierung** | - [Integrieren von Ihrer lokalen Identitäten in Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkID=624168) <br> -Directory-Synchronisierung mit oder ohne kennwortsynchronisierung verwenden Sie [Azure AD-Verbinden mit den express-Einstellungen](https://go.microsoft.com/fwlink/p/?LinkID=698537).  <br>  -Für mehrere Gesamtstrukturen und SSO-Optionen verwenden Sie die [benutzerdefinierte Installation von Azure Active Directory verbinden](https://go.microsoft.com/fwlink/p/?LinkId=698430). <br> – Stellt die Infrastruktur bereit, die zum Aktivieren von SSO erforderlich ist. <br> -Required für viele hybridszenarien (mehrstufige Migration, Exchange Hybrid) <br> -Synchronisiert Sicherheits- und e-Mail-aktivierte Gruppen aus dem lokalen Verzeichnis. <br> |
   
Unabhängig davon, wie Sie die Benutzerkonten zu Office 365 hinzufügen möchten müssen Sie mehrere Kontofeatures wie Zuweisen von Lizenzen, angeben Speicherorts, verwalten und so weiter. Diese Features können verwaltet langfristige aus dem Office 365 Administrationscenter oder Sie können auch [Benutzerkonten mit Office 365 PowerShell erstellen](https://go.microsoft.com/fwlink/p/?LinkId=717083).
    
Wenn Sie zum Hinzufügen und Verwalten von allen Benutzern über das Office 365 Administrationscenter auswählen, werden Sie geben Sie den Speicherort und Zuweisen von Lizenzen zur selben Zeit als Office 365-Konto erstellen. Daher ist nicht viel Planung erforderlich.
    
> [!IMPORTANT]
> Konten in Office 365 erstellen, ohne Zuweisen einer Lizenz (für SharePoint Online, beispielsweise) bedeutet, dass der Kontobesitzer den Office 365-Portal jedoch anzeigen kann, kann keine Dienste innerhalb Ihres Unternehmens-Abonnement zugreifen. Nachdem Sie einen Speicherort und die Lizenz zugewiesen haben, wird das Konto repliziert, auf den Dienst oder die Dienste, die Ihnen zugewiesen. Der Benutzer kann melden Sie sich bei ihrem Konto und die Dienste, die ihnen zugewiesenen verwenden.