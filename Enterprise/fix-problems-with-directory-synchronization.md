---
title: Beheben von Problemen mit der Verzeichnissynchronisierung für Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MBS150
ms.assetid: 79c43023-5a47-45ae-8068-d8a26eee6bc2
description: Beschreibt häufige Ursachen von Problemen mit der Verzeichnissynchronisierung in Office 365 und bietet ein paar Methoden, wie man diese Probleme beheben kann.
ms.openlocfilehash: 658f1649d0a4b9bf109bbb35593d4c64092e1cf8
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/07/2020
ms.locfileid: "41840332"
---
# <a name="fixing-problems-with-directory-synchronization-for-office-365"></a>Beheben von Problemen mit der Verzeichnissynchronisierung für Office 365

Mithilfe der Verzeichnissynchronisierung können Sie weiterhin Benutzer und Gruppen lokal verwalten und Änderungen, Ergänzungen und Löschungen in der Cloud synchronisieren. Das Setup ist jedoch etwas kompliziert, und es kann mitunter schwierig sein, die Problemursachen zu finden. Wir verfügen über Ressourcen, mit denen Sie mögliche Probleme aufspüren und beheben können.
  
## <a name="how-do-i-know-if-something-is-wrong"></a>Wie kann ich feststellen, ob ein Fehler vorliegt?

Der erste Hinweis darauf, dass etwas nicht stimmt, ist, wenn die Dirsync-Status Kachel im Microsoft 365 Admin Center angibt, dass ein Problem vorliegt.
  
Außerdem sendet Office 365 Ihnen eine E-Mail (an die alternative und an Ihre Administrator-E-Mail-Adresse), aus der hervorgeht, dass bei Ihrem Mandanten Verzeichnissynchronisierungsfehler aufgetreten sind. Ausführlichere Informationen hierzu finden Sie unter [Ermitteln von Fehlern bei der Verzeichnissynchronisierung in Office 365](identify-directory-synchronization-errors.md).
  
## <a name="how-do-i-get-azure-active-directory-connect-tool"></a>Wie erhalte ich das Azure Active Directory Connect-Tool?

Navigieren Sie im [Microsoft 365 Admin Center](https://admin.microsoft.com)zu **Benutzer** \> **aktive Benutzer**. Klicken Sie auf das Menü **Weitere** (drei Punkte), und wählen Sie **Verzeichnissynchronisierung**aus. 
  
Folgen Sie den [Anweisungen im Assistenten](set-up-directory-synchronization.md), um Azure AD Connect herunterzuladen. 
  
Wenn Sie weiterhin die Azure Active Directory-Synchronisierung (DirSync) verwenden, finden Sie unter dem Thema [Problembehandlung bei Fehlermeldungen zur Installation des Azure Active Directory-Synchronisierungstools und zum Konfigurations-Assistenten in Office 365](https://go.microsoft.com/fwlink/p/?LinkId=396717) Informationen zu den Systemanforderungen für die Installation von DirSync, den dazu erforderlichen Berechtigungen sowie zur Problembehandlung bei häufig auftretenden Fehlern. 
  
Informationen zum Aktualisieren der Azure Active Directory-Synchronisierung auf Azure AD Connect finden Sie unter [Aktualisierungsanweisungen](https://go.microsoft.com/fwlink/p/?LinkId=733240).
  
## <a name="resolving-common-causes-of-problems-with-directory-synchronization-in-office-365"></a>Beheben häufiger Ursachen von Problemen mit der Verzeichnissynchronisierung in Office 365

### <a name="synchronized-objects-arent-appearing-or-updating-online-or-im-getting-synchronization-error-reports-from-the-service"></a>**Synchronisierte Objekte werden nicht angezeigt oder nicht online aktualisiert, oder ich erhalte Synchronisierungsfehlerberichte vom Dienst.**

- [Identitätssynchronisierung und Resilienz bei doppelten Attributen](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency)

### <a name="i-have-an-alert-in-the-admin-center-or-am-receiving-automated-emails-that-there-hasnt-been-a-recent-synchronization-event"></a>**Ich habe eine Benachrichtigung im Admin Center oder erhalte automatisierte E-Mails mit dem Hinweis, dass kürzlich kein Synchronisierungsereignis stattgefunden hat**
- [Behandeln von Verbindungsproblemen mit Azure AD Connect](https://docs.microsoft.com/azure/active-directory/hybrid/tshoot-connect-connectivity)
- [Azure AD Connect-Konten und -Berechtigungen](https://go.microsoft.com/fwlink/p/?LinkId=820598)
- [Azure AD Connect-Synchronisierung: Verwalten des Azure AD-Dienstkontos](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-azureadaccount)
- [Die Verzeichnissynchronisierung mit Azure Active Directory wird beendet, oder Sie erhalten eine Warnung, die besagt, dass die Synchronisierung sich seit mehr als einem Tag nicht mehr registriert hat](https://support.microsoft.com/help/2882421/directory-synchronization-to-azure-active-directory-stops-or-you-re-warned-that-sync-hasn-t-registered-in-more-than-a-day)

### <a name="password-hashes-arent-synchronizing-or-im-seeing-an-alert-in-the-admin-center-that-there-hasnt-been-a-recent-password-hash-synchronization"></a>**Kennworthashes werden nicht synchronisiert, oder im Admin Center wird eine Warnung angezeigt, die besagt, dass kürzlich keine Kennworthashsynchronisierung stattgefunden hat**
- [Implementieren der Kennworthashsynchronisierung mit der Azure AD Connect-Synchronisierung](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-password-hash-synchronization)

### <a name="im-seeing-an-alert-that-object-quota-exceeded"></a>**Ich erhalte eine Warnung, dass das Objektkontingent überschritten ist**
- Als Hilfe zum Schutz des Dienstes wurde ein Objektkontingent integriert. Falls Sie zu viele Objekte in Ihrem Verzeichnis haben, die mit Office 365 synchronisiert werden müssen, [wenden Sie sich an den Support für Business-Produkte](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b), um Ihr Kontingent zu erhöhen.

### <a name="i-need-to-know-which-attributes-are-synchronized"></a>**Ich muss wissen, welche Attribute synchronisiert werden**
- [Hier](https://go.microsoft.com/fwlink/p/?LinkId=396719) finden Sie eine Liste aller Attribute, die zwischen lokalen Verzeichnissen und der Cloud synchronisiert werden.

### <a name="i-cant-manage-or-remove-objects-that-were-synchronized-to-the-cloud"></a>**Ich kann Objekte, die mit der Cloud synchronisiert wurden, nicht verwalten oder entfernen**
- Sind Sie bereit, Objekte allein in der Cloud zu verwalten? Oder gibt es ein Objekt, das lokal gelöscht wurde und jetzt in der Cloud festhängt? Anleitung zum Beheben dieser Probleme finden Sie in diesem Artikel zur [Problembehandlung bei der Synchronisierung](https://go.microsoft.com/fwlink/p/?linkid=842044) und [Unterstützung](https://go.microsoft.com/fwlink/p/?LinkId=396720).

### <a name="i-got-an-error-message-that-my-company-has-exceeded-the-number-of-objects-that-can-be-synchronized"></a>**Eine Fehlermeldung hat mir mitgeteilt, dass mein Unternehmen die Anzahl der Objekte, die synchronisiert werden können, überschritten hat**
- Weitere Informationen zu diesem Problem finden Sie [hier](https://go.microsoft.com/fwlink/p/?LinkId=396721).
   
## <a name="other-resources"></a>Weitere Ressourcen

- [Skript zum Beheben von doppelten Benutzerprinzipalnamen](https://go.microsoft.com/fwlink/p/?LinkId=396725)
    
- [Vorbereiten einer nicht routingfähigen Domäne (z. B. ".lokale Domäne") für die Verzeichnissynchronisierung](prepare-a-non-routable-domain-for-directory-synchronization.md)
    
- [Skript zum Ermitteln der Anzahl aller synchronisierten Objekte](https://go.microsoft.com/fwlink/p/?LinkId=396726)
    
- [Behandeln von Problemen mit AD FS 2.0](https://go.microsoft.com/fwlink/p/?LinkId=396727)
    
- [Verwenden von PowerShell zum Korrigieren leerer "DisplayName"-Attribute für E-Mail-aktivierte Gruppen](https://go.microsoft.com/fwlink/p/?LinkId=396728)
    
- [Verwenden von PowerShell zum Korrigieren von doppelten UPNs](https://go.microsoft.com/fwlink/p/?LinkId=396730)
    
- [Verwenden von PowerShell zum Korrigieren von doppelten E-Mail-Adressen](https://go.microsoft.com/fwlink/p/?LinkId=396731)
    
## <a name="diagnostic-tools"></a>Diagnosetools

[IDFix-Tool](prepare-directory-attributes-for-synch-with-idfix.md) wird in einer lokalen Active Directory-Umgebung für die Suche nach und Korrektur von Identitätsobjekten und deren Attributen verwendet, um die Migration nach Office 365 vorzubereiten. IDFix ist für die Active Directory Administratoren gedacht, die für die Verzeichnissynchronisierung mit dem Office 365 Dienst zuständig sind. 

[Herunterladen des IDFix-Tools](https://go.microsoft.com/fwlink/p/?LinkId=396718) aus dem Microsoft Download Center.