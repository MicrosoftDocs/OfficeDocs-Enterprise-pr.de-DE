---
title: Beheben von Problemen bei der Verzeichnissynchronisierung für Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MBS150
ms.assetid: 79c43023-5a47-45ae-8068-d8a26eee6bc2
description: Beschreibt häufige Ursachen von Problemen mit der verzeichnissynchronisierung in Office 365 und bietet eine Reihe neuer Methoden Problembehebung und beheben Sie diese.
ms.openlocfilehash: a1ccf7aa8c6d450cdd3d658ef0bc8d9ed6d25753
ms.sourcegitcommit: 6a4611bb474c783efd361890fe6f41c26c5aeeb3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/04/2018
ms.locfileid: "25405128"
---
# <a name="fixing-problems-with-directory-synchronization-for-office-365"></a>Beheben von Problemen bei der Verzeichnissynchronisierung für Office 365

Mit der verzeichnissynchronisierung können Sie weiterhin Verwalten von Benutzern und Gruppen: lokal und Ergänzungen hinzufügen, löschen und Änderungen in die Cloud zu synchronisieren. Aber Setup ein wenig kompliziert wird, und es manchmal schwierig sein kann, die Quelle der Probleme zu identifizieren. Wir haben die Ressourcen, die Ihnen bei der Ermittlung möglicher Probleme zu identifizieren und beheben Sie sie.
  
## <a name="how-do-i-know-if-something-is-wrong"></a>Wie weiß ich, wenn etwas falsch ist?

Der erste Hinweis darauf, dass etwas falsch ist ist, wenn die Kachel Dirsync-Status in Office 365 Administrationscenter gibt an, dass ein Fehler auftritt:
  
![Der Status der Dirsync-Kachel im Admin Center – Vorschau](media/060006e9-de61-49d5-8979-e77cda198e71.png)
  
Sie erhalten auch eine e-Mail-Nachrichten (um die alternative e-Mail und Ihre e-Mails Admin) von Office 365, die angibt, dass es sich bei Ihrem Mandanten verzeichnissynchronisierungsfehlern festgestellt wurden. Weitere Informationen finden Sie unter [Identifizieren von verzeichnissynchronisierungsfehlern in Office 365](identify-directory-synchronization-errors.md).
  
## <a name="how-do-i-get-azure-active-directory-connect-tool"></a>Wie erhalte ich das Tool Azure Active Directory verbinden?

Navigieren Sie in der Office 365-Verwaltungskonsole zu ** Benutzer ** \> **aktive Benutzer**. Klicken Sie auf das Menü **mehr** und aktivieren Sie **verzeichnissynchronisierung**. 
  
![Wählen Sie im Menü Weitere Directory-Synchronisierung](media/dc6669e5-c01b-471e-9cdf-04f5d44e1c4b.png)
  
Navigieren Sie in der alten Office 365-Verwaltungskonsole zu **Benutzer** \> **Aktive Benutzer**, und wählen **Einrichten** , klicken Sie neben **Active Directory-Synchronisierung**. 
  
![Wählen Sie Set up neben Active Directory-Synchronisierung](media/bd95492b-d65e-4072-a6ee-e562f5f566c3.png)
  
Befolgen Sie die [Anweisungen des Assistenten](set-up-directory-synchronization.md) zum Herunterladen des Azure Active Directory verbinden. 
  
Wenn Sie noch Azure Active Directory-Synchronisierung (DirSync) verwenden, sehen Sie sich [Behandlung von Azure Active Directory-Synchronisierungstool Installations- und Fehlermeldungen in Office 365 Konfigurations-Assistenten für](https://go.microsoft.com/fwlink/p/?LinkId=396717) Informationen zu den Systemanforderungen installieren Dirsync, den dazu benötigten Berechtigungen und wie häufige Fehler behoben. 
  
Um auf Azure AD-Verbinden von Azure Active Directory-Synchronisierung zu aktualisieren, finden Sie unter [den Upgradeanweisungen](https://go.microsoft.com/fwlink/p/?LinkId=733240).
  
## <a name="resolving-common-causes-of-problems-with-directory-synchronization-in-office-365"></a>Beheben von allgemeinen Ursachen für Probleme mit der verzeichnissynchronisierung in Office 365

### <a name="synchronized-objects-arent-appearing-or-updating-online-or-im-getting-synchronization-error-reports-from-the-service"></a>**Synchronisierte Objekte werden nicht angezeigt oder Aktualisieren von online, oder ich erhalte Synchronisierung Fehlerberichte aus dem Dienst.**

- [Identität Synchronisierung und Duplikat Attribut resiliency](https://go.microsoft.com/fwlink/p/?LinkID=798300)

### <a name="i-have-an-alert-in-the-office-365-admin-center-or-am-receiving-automated-emails-that-there-hasnt-been-a-recent-synchronization-event"></a>**Ich haben eine Benachrichtigung in Office 365 Administrationscenter oder erhalte automatisierten e-Mails, dass ein aktueller Synchronisierungsereignis wurde nicht**
- [Behandeln von Verbindungsproblemen mit Azure Active Directory verbinden](https://go.microsoft.com/fwlink/p/?LinkId=820597)
- [Azure Active Directory verbinden Konten und Berechtigungen](https://go.microsoft.com/fwlink/p/?LinkId=820598)
- [Azure Active Directory verbinden Sync: Gewusst wie: Verwalten des Azure AD-Dienstkontos](https://go.microsoft.com/fwlink/p/?LinkId=820599)
- [Directory-Synchronisierung mit Azure Active Directory reagiert oder Sie sind darauf hingewiesen, dass Sync in mehr als einen Tag registriert noch nicht](https://support.microsoft.com/help/2882421/directory-synchronization-to-azure-active-directory-stops-or-you-re-warned-that-sync-hasn-t-registered-in-more-than-a-day)

### <a name="password-hashes-arent-synchronizing-or-im-seeing-an-alert-in-the-office-365-admin-center-that-there-hasnt-been-a-recent-password-hash-synchronization"></a>**Kennworthashes sind nicht synchronisiert, oder eine Warnung im Office 365 Administrationscenter, dass eine zuletzt verwendete Kennwort Hash Synchronisierung wurde nicht immer unerwünschte**
- [Implementieren von Hash kennwortsynchronisierung mit Azure AD-Connect-Synchronisierung](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-password-hash-synchronization)

### <a name="im-seeing-an-alert-that-object-quota-exceeded"></a>**Ich bin eine Benachrichtigung angezeigt, die Objekt-Kontingent überschritten**
- Wir haben ein Kontingent integrierten-Objekts zum Schutz des Diensts. Wenn Sie zu viele Objekte in Ihrem Verzeichnis aus, die mit Office 365 synchronisiert werden müssen haben, müssen Sie auf [Kontakt für Business-Produkte unterstützen](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) Ihr Kontingent zu erhöhen.

### <a name="i-need-to-know-which-attributes-are-synchronized"></a>**Ich möchte wissen, welche Attribute synchronisiert sind**
- Finden Sie eine Liste aller Attribute, die zwischen lokalen und Cloud [hier rechts](https://go.microsoft.com/fwlink/p/?LinkId=396719)synchronisiert werden.

### <a name="i-cant-manage-or-remove-objects-that-were-synchronized-to-the-cloud"></a>**Ich kann nicht verwalten oder Entfernen von Objekten, die in der Cloud synchronisiert wurden**
- Sind Sie bereit, die Objekte in der Cloud nur verwalten? Oder ein Objekt, das lokale gelöscht wurde, aber in der Cloud steckt? Sehen Sie sich diese [Problembehandlung bei Fehlern während der Synchronisierung](https://go.microsoft.com/fwlink/p/?linkid=842044) und [Artikel zu unterstützen](https://go.microsoft.com/fwlink/p/?LinkId=396720) , Hinweise zum Beheben dieser Probleme an.

### <a name="i-got-an-error-message-that-my-company-has-exceeded-the-number-of-objects-that-can-be-synchronized"></a>**Ich habe die Fehlermeldung bekommen, dass mein Unternehmen die Anzahl der synchronisierbaren Objekte überschritten hat**
- Weitere Informationen zu diesem Thema [hier](https://go.microsoft.com/fwlink/p/?LinkId=396721).
   
## <a name="other-resources"></a>Weitere Ressourcen

- [Skript zum Beheben von doppelten Benutzerprinzipalnamen](https://go.microsoft.com/fwlink/p/?LinkId=396725)
    
- [Vorbereiten eine nicht-routingfähigen Domäne (beispielsweise Local Domäne) für die verzeichnissynchronisierung](prepare-a-non-routable-domain-for-directory-synchronization.md)
    
- [Skript zum zählen insgesamt synchronisierte Objekte](https://go.microsoft.com/fwlink/p/?LinkId=396726)
    
- [Problembehebung AD FS 2.0](https://go.microsoft.com/fwlink/p/?LinkId=396727)
    
- [Verwenden von PowerShell, DisplayName-Attribute für e-Mail-aktivierte Gruppen zu beheben.](https://go.microsoft.com/fwlink/p/?LinkId=396728)
    
- [Verwenden von PowerShell doppelte UPN beheben](https://go.microsoft.com/fwlink/p/?LinkId=396730)
    
- [Verwenden von PowerShell, doppelte e-Mail-Adressen zu beheben.](https://go.microsoft.com/fwlink/p/?LinkId=396731)
    
## <a name="diagnostic-tools"></a>Diagnosetools

[IDFix-Tool](prepare-directory-attributes-for-synch-with-idfix.md) wird verwendet, um die Suche und Wartung der Identitätsobjekten und der zugehörigen Attribute in einer lokalen Active Directory-Umgebung im Rahmen der Vorbereitung für die Migration zu Office 365 ausführen. IDFix ist für die Active Directory-Administratoren für DirSync mit Office 365-Dienst verantwortlich vorgesehen. 

[Laden Sie das IDFix-Tool](https://go.microsoft.com/fwlink/p/?LinkId=396718) , aus dem Microsoft Downloadcenter.