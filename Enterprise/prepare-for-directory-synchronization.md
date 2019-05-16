---
title: Vorbereiten von Benutzern auf die Bereitstellung in Office 365 über die Verzeichnissynchronisierung
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
f1_keywords:
- O365p_AddUsersWithDirSync
- O365M_AddUsersWithDirSync
- O365E_HRCSetupAADConnectAboutLM617031
- O365E_AddUsersWithDirSync
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOP150
- MOE150
- MBS150
ms.assetid: 01920974-9e6f-4331-a370-13aea4e82b3e
description: Beschreibt die Vorbereitung der Bereitstellung von Benutzern auf Office 365 mithilfe der Verzeichnissynchronisierung und der langfristigen Vorteile der Verwendung dieser Methode.
ms.openlocfilehash: 0b2fe552911797337541bd25f0efcb81eab303bf
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "34071031"
---
# <a name="prepare-to-provision-users-through-directory-synchronization-to-office-365"></a>Vorbereiten von Benutzern auf die Bereitstellung in Office 365 über die Verzeichnissynchronisierung

Das Bereitstellen von Benutzern mit der Verzeichnissynchronisierung erfordert mehr Planung und Vorbereitung, als nur das geschäftliche oder schulische Konto direkt in Office 365 zu verwalten. Die zusätzlichen Planungs-und Vorbereitungsaufgaben sind erforderlich, um sicherzustellen, dass Ihr lokales Active Directory ordnungsgemäß mit Azure Active Directory synchronisiert wird. Zu den Vorteilen für Ihre Organisation gehört Folgendes:
  
- Reduzieren der Verwaltungsprogramme in Ihrer Organisation
- Optionales Aktivieren des Szenarios für einmaliges Anmelden
- Automatisieren von Kontoänderungen in Office 365
    
Weitere Informationen zu den Vorteilen der Verwendung der Verzeichnissynchronisierung finden Sie unter Übersicht über die [Verzeichnissynchronisierung]( https://go.microsoft.com/fwlink/p/?LinkId=525398) und [Grundlegendes zu Office 365 Identity und Azure Active Directory](about-office-365-identity.md).
  
Um zu bestimmen, welches Szenario am besten für Ihre Organisation geeignet ist, lesen Sie den [Vergleich der Verzeichnis Integrationstools](https://go.microsoft.com/fwlink/p/?LinkId=525320).
  
## <a name="directory-cleanup-tasks"></a>Aufgaben zur Verzeichnisbereinigung

Bevor Sie mit der Synchronisierung Ihres Verzeichnisses beginnen, müssen Sie Ihr Verzeichnis bereinigen.
  
Lesen Sie auch die [Attribute, die von Azure AD Connect mit Azure Active Directory synchronisiert wurden](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-sync-attributes-synchronized).
  
> [!IMPORTANT]
> Wenn Sie vor der Synchronisierung keine Verzeichnisbereinigung durchführen, kann sich dies negativ auf den Bereitstellungsprozess auswirken. Es kann Tage oder sogar Wochen dauern, bis der Zyklus der Verzeichnissynchronisierung durchlaufen wird, Fehler identifiziert und erneut synchronisiert werden. 
  
Führen Sie im lokalen Verzeichnis die folgenden Bereinigungsaufgaben aus:
  
1. Stellen Sie sicher, dass jeder Benutzer, dem Office 365-Dienstangebote zugewiesen werden, über eine gültige und eindeutige e-Mail-Adresse im **proxyAddresses** -Attribut verfügt. 
    
2. Entfernen Sie alle doppelten Werte im **proxyAddresses** -Attribut. 
    
3.  Stellen Sie nach Möglichkeit sicher, dass jeder Benutzer, dem Office 365-Dienstangebote zugewiesen werden, einen gültigen und eindeutigen Wert für das **userPrincipalName** -Attribut im **Benutzer** Objekt des Benutzers hat. Stellen Sie für eine optimale Synchronisierung sicher, dass der UPN des lokalen Active Directory mit dem Cloud-UPN übereinstimmt. Wenn ein Benutzer keinen Wert für das **userPrincipalName** -Attribut hat, muss das **User** -Objekt einen gültigen und eindeutigen Wert für das **sAMAccountName** -Attribut enthalten. Entfernen Sie alle doppelten Werte im **userPrincipalName** -Attribut. 
    
4. Um die globale Adressliste (GAL) optimal zu verwenden, stellen Sie sicher, dass die Informationen in den folgenden Attributen korrekt sind:
    
  - givenName
  - surname
  - displayName
  - Position
  - Abteilung
  - Büro
  - Telefon (geschäftlich)
  - Mobiltelefon
  - Faxnummer
  - Straße
  - Stadt
  - Bundesland/Kanton
  - PLZ
  - Land oder Region
    
## <a name="directory-object-and-attribute-preparation"></a>Verzeichnisobjekt-und Attribut Vorbereitung

Für die erfolgreiche Verzeichnissynchronisierung zwischen dem lokalen Verzeichnis und Office 365 müssen die lokalen Verzeichnisattribute ordnungsgemäß vorbereitet werden. Sie müssen beispielsweise sicherstellen, dass bestimmte Zeichen nicht in bestimmten Attributen verwendet werden, die mit der Office 365-Umgebung synchronisiert werden. Unerwartete Zeichen führen nicht dazu, dass die Verzeichnissynchronisierung fehlschlägt, aber möglicherweise eine Warnung zurückgibt. Ungültige Zeichen führen zu einem Fehler bei der Verzeichnissynchronisierung.
  
Die Verzeichnissynchronisierung schlägt ebenfalls fehl, wenn einige Ihrer Active Directory-Benutzer über ein oder mehrere doppelte Attribute verfügen. Jeder Benutzer muss über eindeutige Attribute verfügen.
  
Die Attribute, die Sie vorbereiten müssen, sind hier aufgeführt:
  
 **Hinweis:** Sie können dieses Verfahren auch mit dem [IdFix-Tool](install-and-run-idfix.md) vereinfachen. 
  
- **displayName**
    
  - Wenn das Attribut im User-Objekt vorhanden ist, wird es mit Office 365 synchronisiert.
  - Wenn dieses Attribut im User-Objekt vorhanden ist, muss es einen Wert enthalten. Das heißt, das Attribut darf nicht leer sein.
  - Maximale Anzahl der Zeichen: 256
    
- **givenName**
    
  - Wenn das Attribut im User-Objekt vorhanden ist, wird es mit Office 365 synchronisiert, jedoch von Office 365 nicht benötigt oder verwendet.
  - Maximale Anzahl der Zeichen: 64
    
- **Mail**
    
  - Der Attributwert muss innerhalb des Verzeichnisses eindeutig sein.
    
    > [!NOTE]
    > Wenn doppelte Werte vorhanden sind, wird der erste Benutzer mit dem Wert synchronisiert. Nachfolgende Benutzer werden nicht in Office 365 angezeigt. Sie müssen entweder den Wert in Office 365 ändern oder beide Werte im lokalen Verzeichnis ändern, damit beide Benutzer in Office 365 angezeigt werden. 
  
- **** mailNickname (Exchange-Alias) 
    
  - Der Attributwert darf nicht mit einem Punkt (.) beginnen.
  - Der Attributwert muss innerhalb des Verzeichnisses eindeutig sein.
    
- **proxyAddresses**
    
  - Attribut mit mehreren Werten
  - Maximale Anzahl von Zeichen pro Wert: 256
  - Der Attributwert darf kein Leerzeichen enthalten.
  - Der Attributwert muss innerhalb des Verzeichnisses eindeutig sein.
  - Ungültige Zeichen: \< \> (); , [ ] "
    
    Beachten Sie, dass die ungültigen Zeichen auf die Zeichen nach dem typtrennzeichen und ":" angewendet werden, sodass SMTP:User@contso.com zulässig ist, aber SMTP:User:M@contoso.com nicht.
    
    > [!IMPORTANT]
    > Alle SMTP-Adressen (Simple Mail Transport Protocol) sollten den Standards für e-Mail-Messaging entsprechen. Wenn doppelte oder unerwünschte Adressen vorhanden sind, finden Sie weitere Informationen im Hilfethema [Entfernen von doppelten und unerwünschten Proxyadressen in Exchange](https://go.microsoft.com/fwlink/?LinkId=293860). 
  
- **sAMAccountName**
    
  - Maximale Anzahl der Zeichen: 20
  - Der Attributwert muss innerhalb des Verzeichnisses eindeutig sein.
  - Ungültige Zeichen: [\ "|,/: \< \> + =;? \* ]
  - Wenn ein Benutzer über ein ungültiges **sAMAccountName** -Attribut verfügt, jedoch über ein gültiges **userPrincipalName** -Attribut verfügt, wird das Benutzerkonto in Office 365 erstellt. 
  - Wenn sowohl **sAMAccountName** als auch **userPrincipalName** ungültig sind, muss das **userPrincipalName** -Attribut des lokalen Active Directory-Attributs aktualisiert werden. 
    
- **SN** Surname 
    
  - Wenn das Attribut im User-Objekt vorhanden ist, wird es mit Office 365 synchronisiert, jedoch von Office 365 nicht benötigt oder verwendet.
    
- **targetAddress**
    
    Es ist erforderlich, dass das **targetAddress** -Attribut (beispielsweise SMTP:Tom@contoso.com), das für den Benutzer aufgefüllt wird, in der Office 365 GAL angezeigt werden muss. In Drittanbieter-Messaging-Migrationsszenarien würde dies die Office 365-Schemaerweiterung für das lokale Verzeichnis erfordern. Die Office 365-Schemaerweiterung würde außerdem weitere nützliche Attribute zum Verwalten von Office 365-Objekten hinzufügen, die mit einem Verzeichnissynchronisierungstool vom lokalen Verzeichnis aufgefüllt werden. Beispielsweise würde das **msExchHideFromAddressLists** -Attribut zum Verwalten von ausgeblendeten Postfächern oder Verteilergruppen hinzugefügt. 
   
  - Maximale Anzahl der Zeichen: 256
  - Der Attributwert darf kein Leerzeichen enthalten.
  - Der Attributwert muss innerhalb des Verzeichnisses eindeutig sein.
  - Ungültige Zeichen: \ \< \> (); , [ ] "
  - Alle SMTP-Adressen (Simple Mail Transport Protocol) sollten den Standards für e-Mail-Messaging entsprechen.
    
- **userPrincipalName**
    
  - Das **userPrincipalName** -Attribut muss im Internet-Stil-Anmeldeformat vorliegen, in dem der Benutzername vom @-Zeichen und einem Domänennamen gefolgt wird, beispielsweise user@contoso.com. Alle SMTP-Adressen (Simple Mail Transport Protocol) sollten den Standards für e-Mail-Messaging entsprechen.
  - Die maximale Anzahl von Zeichen für das **userPrincipalName** -Attribut lautet 113. Eine bestimmte Anzahl von Zeichen ist vor und nach dem @-Zeichen (@) wie folgt zulässig: 
  - Maximale Anzahl der Zeichen für den Benutzernamen vor dem @-Zeichen: 64
  - Maximale Anzahl von Zeichen für den Domänennamen nach dem @-Zeichen (@): 48
  - Ungültige Zeichen: \% &amp; \* +/=? { } | \< \> ( ) ; : , [ ] "
  - Ein Umlaut ist auch ein ungültiges Zeichen.
  - Das @-Zeichen ist in jedem **userPrincipalName** -Wert erforderlich. 
  - Das @-Zeichen darf nie das erste Zeichen in einem **userPrincipalName**-Wert sein. 
  - Der Benutzername darf nicht mit einem Punkt (.), einem kaufmännischem&amp;und-Zeichen (), einer Leertaste oder einem @-Symbol enden.
  - Der Benutzername darf keine Leerzeichen enthalten.
  - Routingfähige Domänen müssen verwendet werden; Beispielsweise können lokale oder interne Domänen nicht verwendet werden.
  - Unicode-Zeichen werden in Unterstriche umgewandelt.
  - **userPrincipalName** darf keine doppelten Werte im Verzeichnis enthalten. 
    
## <a name="prepare-the-userprincipalname-attribute"></a>Vorbereiten des userPrincipalName-Attributs

Active Directory soll es den Endbenutzern in Ihrer Organisation ermöglichen, sich über **sAMAccountName** oder **userPrincipalName**bei Ihrem Verzeichnis anzumelden. Entsprechend können Endbenutzer sich mit dem Benutzerprinzipalnamen (UPN) Ihres Geschäfts-oder Schul Kontos bei Office 365 anmelden. Die Verzeichnissynchronisierung versucht, neue Benutzer in Azure Active Directory mithilfe desselben UPN zu erstellen, der sich in Ihrem lokalen Verzeichnis befindet. Der UPN ist wie eine e-Mail-Adresse formatiert. 

In Office 365 ist der UPN das Standardattribut, mit dem die e-Mail-Adresse generiert wird. Es ist ganz einfach, **userPrincipalName** (lokal und in Azure Active Directory) abzurufen, und die primäre e-Mail-Adresse in **proxyAddresses** wird auf unterschiedliche Werte festgelegt. Wenn Sie auf unterschiedliche Werte festgelegt werden, kann es zu Verwirrung für Administratoren und Endbenutzer kommen. 
  
Am besten richten Sie diese Attribute aus, um Verwirrung zu vermeiden. Um die Anforderungen der einmaligen Anmeldung mit Active Directory-Verbunddiensten (AD FS) 2,0 zu erfüllen, müssen Sie sicherstellen, dass die UPNs in Azure Active Directory und Ihr lokales Active Directory übereinstimmen und einen gültigen Domänennamespace verwenden.
  
## <a name="add-an-alternative-upn-suffix-to-ad-ds"></a>Hinzufügen eines alternativen UPN-Suffixes zu AD DS

Möglicherweise müssen Sie ein alternatives UPN-Suffix hinzufügen, um die Unternehmensanmeldeinformationen des Benutzers mit der Office 365-Umgebung zu verknüpfen. Ein UPN-Suffix ist der Teil eines Benutzerprinzipalnamens, der rechts vom Zeichen @ steht. UPNs, die für einmaliges Anmelden verwendet werden, können Buchstaben, Zahlen, Punkte, Bindestriche und Unterstriche enthalten, aber keine anderen Zeichen.
  
Weitere Informationen zum Hinzufügen eines alternativen UPN-Suffix zu Active Directory finden Sie unter [Prepare for Directory Synchronization]( https://go.microsoft.com/fwlink/p/?LinkId=525430).
  
## <a name="match-the-on-premises-upn-with-the-office-365-upn"></a>Übereinstimmung mit dem lokalen UPN mit dem Office 365 UPN

Wenn Sie die Verzeichnissynchronisierung bereits eingerichtet haben, stimmt der UPN des Benutzers für Office 365 möglicherweise nicht mit dem lokalen UPN des Benutzers überein, der im lokalen Verzeichnisdienst definiert ist. Das kann vorkommen, wenn einem Benutzer vor der Überprüfung der Domäne schon eine Lizenz zugewiesen wurde. Um dies zu beheben, verwenden Sie [PowerShell, um doppelte UPN zu beheben](https://go.microsoft.com/fwlink/p/?LinkId=396730) , um den UPN des Benutzers zu aktualisieren, um sicherzustellen, dass der Office 365 UPN mit dem Unternehmensbenutzer Namen und der Domäne übereinstimmt. Wenn Sie den UPN im lokalen Verzeichnisdienst aktualisieren und ihn mit der Azure Active Directory-Identität synchronisieren möchten, müssen Sie die Benutzerlizenz in Office 365 entfernen, bevor Sie die Änderungen lokal vornehmen. 
  
Weitere Informationen finden Sie unter [Vorbereiten einer nicht routingfähigen Domäne (beispielsweise. Local Domain) für die Verzeichnissynchronisierung](prepare-a-non-routable-domain-for-directory-synchronization.md).
  
## <a name="directory-integration-tools"></a>Verzeichnis Integrationstools

Bei der Verzeichnissynchronisierung handelt es sich um die Synchronisierung von Verzeichnisobjekten (Benutzern, Gruppen und Kontakten) von Ihrer lokalen Active Directory-Umgebung zur Office 365-Verzeichnisinfrastruktur, Azure Active Directory. Eine Liste der verfügbaren Tools und deren Funktionen finden Sie unter [Directory-Integrationstools](https://go.microsoft.com/fwlink/p/?LinkID=510956) . Das empfohlene Tool ist [Microsoft Azure Active Directory Connect](https://go.microsoft.com/fwlink/p/?LinkID=510956). Weitere Informationen zu Azure Active Directory Connect finden Sie unter [integrieren Ihrer lokalen Identitäten in Azure Active](https://go.microsoft.com/fwlink/p/?LinkId=527969)Directory.
  
Wenn Benutzerkonten zum ersten Mal mit dem Office 365-Verzeichnis synchronisiert werden, werden Sie als nicht aktiviert gekennzeichnet. Sie können keine e-Mails senden oder empfangen, und Sie nutzen keine Abonnementlizenzen. Wenn Sie bereit sind, Office 365-Abonnements bestimmten Benutzern zuzuweisen, müssen Sie diese aktivieren und aktivieren, indem Sie [Benutzern in Office 365 for Business Lizenzen zuweisen](https://support.office.com/article/997596b5-4173-4627-b915-36abac6786dc).
  
Sie können auch [PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=613097) verwenden, um Lizenzen zuzuweisen. Weitere Informationen finden Sie unter [Verwenden von PowerShell zum automatischen Zuweisen von Lizenzen zu Ihren Office 365-Benutzern](https://go.microsoft.com/fwlink/p?LinkID=329805) für eine automatisierte Lösung.