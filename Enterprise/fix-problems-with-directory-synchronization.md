---
title: Beheben von Problemen bei der Verzeichnissynchronisierung für Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MBS150
ms.assetid: 79c43023-5a47-45ae-8068-d8a26eee6bc2
description: Beschreibt häufige Ursachen von Problemen mit der Verzeichnissynchronisierung in Office 365 und bietet einige Methoden zur Problembehandlung und-Lösung.
ms.openlocfilehash: a5c4b58dd856158b00605f39d8a66b48488086b2
ms.sourcegitcommit: 29f937b7430c708c9dbec23bdc4089e86c37c225
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2019
ms.locfileid: "31001838"
---
# <a name="fixing-problems-with-directory-synchronization-for-office-365"></a>Beheben von Problemen bei der Verzeichnissynchronisierung für Office 365

Mit der Verzeichnissynchronisierung können Sie weiterhin Benutzer und Gruppen lokal verwalten und Hinzufügungen, Löschungen und Änderungen an der Cloud synchronisieren. Das Setup ist jedoch etwas komplizierter, und es kann manchmal schwierig sein, die Ursache für Probleme zu identifizieren. Wir haben Ressourcen, die Ihnen helfen, potenzielle Probleme zu identifizieren und zu beheben.
  
## <a name="how-do-i-know-if-something-is-wrong"></a>Woran erkenne ich, ob etwas falsch ist?

Der erste Hinweis darauf, dass etwas falsch ist, ist, wenn die dirSync-Status Kachel im Microsoft 365 Admin Center ein Problem angibt:
  
![Die dirSync-Status Kachel in der Admin Center-Vorschau](media/060006e9-de61-49d5-8979-e77cda198e71.png)
  
Sie erhalten auch eine e-Mail (an die Alternative e-Mail und an Ihre Administrator-e-Mail) von Office 365, die angibt, dass Ihr Mandant Verzeichnis Synchronisierungsfehler festgestellt hat. Weitere Informationen finden Sie unter [Identifizieren von Verzeichnis Synchronisierungsfehlern in Office 365](identify-directory-synchronization-errors.md).
  
## <a name="how-do-i-get-azure-active-directory-connect-tool"></a>Wie erhalte ich das Azure Active Directory Connect-Tool?

navigieren sie im [Microsoft 365 admin center](https://admin.microsoft.com)zu * * users * * \> **Active users**. Klicken Sie auf das Menü **Weitere** , und wählen Sie **Verzeichnissynchronisierung**aus. 
  
![Wählen Sie im Menü mehr die Option Verzeichnissynchronisierung aus.](media/dc6669e5-c01b-471e-9cdf-04f5d44e1c4b.png)
  
Folgen Sie den [Anweisungen des Assistenten](set-up-directory-synchronization.md) , um Azure AD Connect herunterzuladen. 
  
Wenn Sie weiterhin Azure Active Directory-Synchronisierung (dirSync) verwenden, sehen Sie sich die [Problembehandlung bei Azure Active Directory Sync Tool-Installations-und Konfigurations-Assistenten Fehlermeldungen in Office 365](https://go.microsoft.com/fwlink/p/?LinkId=396717) an, um Informationen zu den Systemanforderungen für die Installation zu erhalten. Dirsync, die erforderlichen Berechtigungen und die Behandlung häufig auftretender Fehler. 
  
Informationen zum Aktualisieren von Azure Active Directory-Synchronisierung mit Azure AD Connect finden Sie in [den Anweisungen zum Upgrade](https://go.microsoft.com/fwlink/p/?LinkId=733240).
  
## <a name="resolving-common-causes-of-problems-with-directory-synchronization-in-office-365"></a>Beheben häufiger Ursachen von Problemen mit der Verzeichnissynchronisierung in Office 365

### <a name="synchronized-objects-arent-appearing-or-updating-online-or-im-getting-synchronization-error-reports-from-the-service"></a>**Synchronisierte Objekte werden nicht online angezeigt oder aktualisiert, oder ich erhalte Synchronisierungsfehler Berichte vom Dienst.**

- [Identitätssynchronisierung und doppelte Attribut Ausfallsicherheit](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency)

### <a name="i-have-an-alert-in-the-admin-center-or-am-receiving-automated-emails-that-there-hasnt-been-a-recent-synchronization-event"></a>**Ich habe eine Warnung im Admin Center oder erhalte automatisierte e-Mails, dass kein neues Synchronisierungsereignis vorliegt.**
- [Beheben von Verbindungsproblemen mit Azure AD Connect](https://docs.microsoft.com/azure/active-directory/hybrid/tshoot-connect-connectivity)
- [Azure AD Connect-Konten und-Berechtigungen](https://go.microsoft.com/fwlink/p/?LinkId=820598)
- [Azure AD Connect Sync: Verwalten des Azure AD-Dienstkontos](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-azureadaccount)
- [Die Verzeichnissynchronisierung mit Azure Active Directory wird angehalten, oder Sie werden gewarnt, dass die Synchronisierung seit mehr als einem Tag nicht registriert ist.](https://support.microsoft.com/help/2882421/directory-synchronization-to-azure-active-directory-stops-or-you-re-warned-that-sync-hasn-t-registered-in-more-than-a-day)

### <a name="password-hashes-arent-synchronizing-or-im-seeing-an-alert-in-the-admin-center-that-there-hasnt-been-a-recent-password-hash-synchronization"></a>**Kenn Wort Hashes werden nicht synchronisiert, oder im Admin Center wird eine Warnung angezeigt, dass keine aktuelle Kennworthash Synchronisierung vorliegt.**
- [Implementieren der Kennworthash Synchronisierung mit Azure AD Connect Sync](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-password-hash-synchronization)

### <a name="im-seeing-an-alert-that-object-quota-exceeded"></a>**Es wurde eine Warnung angezeigt, dass das Objekt Kontingent überschritten wurde.**
- Wir verfügen über ein integriertes Objekt Kontingent, um den Dienst zu schützen. Wenn Sie zu viele Objekte in Ihrem Verzeichnis haben, die mit Office 365 synchronisiert werden müssen, müssen Sie sich an den [Support für Geschäftsprodukte wenden](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) , um Ihr Kontingent zu verlängern.

### <a name="i-need-to-know-which-attributes-are-synchronized"></a>**Ich muss wissen, welche Attribute synchronisiert sind.**
- Eine Liste aller Attribute, die zwischen lokal und der Cloud synchronisiert werden, finden Sie [hier](https://go.microsoft.com/fwlink/p/?LinkId=396719).

### <a name="i-cant-manage-or-remove-objects-that-were-synchronized-to-the-cloud"></a>**Ich kann Objekte, die mit der Cloud synchronisiert wurden, nicht verwalten oder entfernen**
- Sind Sie bereit, Objekte nur in der Cloud zu verwalten? Oder gibt es ein Objekt, das lokal gelöscht wurde, aber in der Cloud steckt? Sehen Sie sich diese [Problem Behandlungsfehler während der Synchronisierung](https://go.microsoft.com/fwlink/p/?linkid=842044) und den [Support Artikel](https://go.microsoft.com/fwlink/p/?LinkId=396720) an, um Anleitungen zur Lösung dieser Probleme zu erhalten.

### <a name="i-got-an-error-message-that-my-company-has-exceeded-the-number-of-objects-that-can-be-synchronized"></a>**Ich habe eine Fehlermeldung erhalten, dass mein Unternehmen die Anzahl der zu synchronisierenden Objekte überschritten hat.**
- Weitere Informationen zu diesem Thema finden Sie [hier](https://go.microsoft.com/fwlink/p/?LinkId=396721).
   
## <a name="other-resources"></a>Sonstige Ressourcen

- [Skript zum Beheben von doppelten Benutzerprinzipalnamen (User Principal Name, UPN)](https://go.microsoft.com/fwlink/p/?LinkId=396725)
    
- [Vorbereiten einer nicht routingfähigen Domäne (wie. lokale Domäne) für die Verzeichnissynchronisierung](prepare-a-non-routable-domain-for-directory-synchronization.md)
    
- [Skript zum zählen der Gesamtzahl der synchronisierten Objekte](https://go.microsoft.com/fwlink/p/?LinkId=396726)
    
- [Problembehandlung bei AD FS 2,0](https://go.microsoft.com/fwlink/p/?LinkId=396727)
    
- [Verwenden von PowerShell zum Korrigieren von leeren DisplayName-Attributen für e-Mail-aktivierte Gruppen](https://go.microsoft.com/fwlink/p/?LinkId=396728)
    
- [Verwenden von PowerShell zum Beheben von doppeltem UPN](https://go.microsoft.com/fwlink/p/?LinkId=396730)
    
- [Verwenden von PowerShell zum Beheben doppelter e-Mail-Adressen](https://go.microsoft.com/fwlink/p/?LinkId=396731)
    
## <a name="diagnostic-tools"></a>Diagnosetools

[IDFix-Tool](prepare-directory-attributes-for-synch-with-idfix.md) dient zur Ermittlung und Behebung von Identitätsobjekten und deren Attributen in einer lokalen Active Directory-Umgebung zur Vorbereitung der Migration zu Office 365. IDFix ist für die für dirSync Verantwortlichen Active Directory-Administratoren mit dem Office 365-Dienst vorgesehen. 

[Laden Sie das IDFix-Tool](https://go.microsoft.com/fwlink/p/?LinkId=396718) aus dem Microsoft Download Center herunter.