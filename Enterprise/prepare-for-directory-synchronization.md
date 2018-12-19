---
title: Vorbereiten der Bereitstellung von Benutzern über die Verzeichnissynchronisierung in Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: article
f1_keywords:
- O365p_AddUsersWithDirSync
- O365M_AddUsersWithDirSync
- O365E_HRCSetupAADConnectAboutLM617031
- O365E_AddUsersWithDirSync
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOP150
- MOE150
- MBS150
ms.assetid: 01920974-9e6f-4331-a370-13aea4e82b3e
description: Vorbereiten der Bereitstellung von Benutzern zu Office 365 mithilfe von verzeichnissynchronisierung und der langfristigen Vorteile dieser Methode beschrieben.
ms.openlocfilehash: 8e84f4602b79ce321cd9a71e6c35331baf40f7f0
ms.sourcegitcommit: c5761d3c41aa2d26815f0d24c73dbcd53ab37957
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/19/2018
ms.locfileid: "27371119"
---
# <a name="prepare-to-provision-users-through-directory-synchronization-to-office-365"></a>Vorbereiten der Bereitstellung von Benutzern über die Verzeichnissynchronisierung in Office 365

Einrichten von Benutzern mithilfe von verzeichnissynchronisierung erfordert weitere Planung und Vorbereitung als einfach verwalten Ihres Kontos arbeiten oder Schule direkt in Office 365. Zusätzlichen Planung und Vorbereitung Aufgaben sind erforderlich, um sicherzustellen, dass Ihre lokalen Active Directory ordnungsgemäß zu Azure Active Directory synchronisiert. Die hinzugefügten organisationsinterne bietet folgende Vorteile:
  
- Verringern der Anzahl der Verwaltungsprogramme in Ihrer Organisation
- Aktivieren optional Szenario für einmaliges Anmelden
- Automatisieren von Kontoänderungen in Office 365
    
Weitere Informationen zu den Vorteilen der Verwendung von verzeichnissynchronisierung finden Sie unter [Directory Synchronization Roadmap]( https://go.microsoft.com/fwlink/p/?LinkId=525398) und [Grundlegendes zu Office 365-Identität und Azure Active Directory](about-office-365-identity.md).
  
Um zu bestimmen, welches Szenario der für Ihre Organisation am besten geeignet ist, überprüfen Sie den [Directory Integration Tools Comparison](https://go.microsoft.com/fwlink/p/?LinkId=525320).
  
## <a name="directory-cleanup-tasks"></a>Verzeichnis Bereinigungsaufgaben

Bevor Sie die Synchronisierung Ihres Verzeichnisses beginnen, müssen Sie Ihr Verzeichnis bereinigen.
  
Überprüfen Sie die [Attribute mit Azure Active Directory von Azure Active Directory verbinden synchronisiert](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-sync-attributes-synchronized)auch.
  
> [!IMPORTANT]
> Wenn Sie vor der Synchronisierung verzeichnisbereinigung nicht ausführen, kann sich erheblich auf den Bereitstellungsprozess negativ sein. Es kann Tage dauern oder sogar Wochen, den Lebenszyklus von verzeichnissynchronisierung, Identifizieren von Fehlern und erneute Synchronisierung durchlaufen. 
  
Führen Sie die folgenden Bereinigungsschritte in Ihrem lokalen Verzeichnis:
  
1. Stellen Sie sicher, dass jeder Benutzer, der die Office 365-Dienstangebote nutzen darf, eine gültige und eindeutige E-Mail-Adresse im **proxyAddresses**-Attribut besitzt. 
    
2. Entfernen Sie alle doppelten Werte im **ProxyAddresses**-Attribut. 
    
3.  Wenn möglich, stellen Sie sicher, dass jeder Benutzer, die Office 365-Dienstangebote zugewiesen wird einen gültigen und eindeutigen Wert für das **UserPrincipalName** -Attribut im **Benutzerobjekt des Benutzers** vorhanden ist. Bewährte Synchronisierung wünschen stellen Sie sicher, dass die lokale Active Directory-UPN die Cloud UPN übereinstimmt. Wenn ein Benutzer einen Wert für das **UserPrincipalName** -Attribut nicht verfügt, muss **das Benutzerobjekt** einen gültigen und eindeutigen Wert für das **sAMAccountName** -Attribut enthalten. Entfernen Sie keine doppelten Werte im Attribut **UserPrincipalName** . 
    
4. Überprüfen Sie die Richtigkeit der folgenden Attribute, um die globale Adressliste (GAL) sinnvoll einsetzen zu können:
    
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
  - Bundesland oder Kanton
  - Postleitzahl
  - Land oder Region
    
## <a name="directory-object-and-attribute-preparation"></a>Verzeichnisobjekt- und Attributsvorbereitung

Erfolgreiche verzeichnissynchronisierung zwischen Ihrer lokalen Verzeichnis und Office 365 erfordert, dass Ihre lokalen Verzeichnisattributen ordnungsgemäß vorbereitet sind. Beispielsweise müssen Sie sicherstellen, dass bestimmte Zeichen nicht in bestimmte Attribute verwendet werden, die mit Office 365-Umgebung synchronisiert werden. Unerwartete Zeichen bewirken keine Synchronisierung fehlschlägt, aber möglicherweise eine Warnung zurück. Ungültige Zeichen verursacht Directory-Synchronisierung ein Fehler auftritt.
  
Directory-Synchronisierung schlägt ebenfalls fehl, wenn einige Ihrer Active Directory-Benutzer ein oder mehrere doppelter Attribute verfügen. Jeder Benutzer muss eindeutige Attribute verfügen.
  
Die Attribute, die Sie vorbereiten müssen sind hier aufgeführt:
  
 **Hinweis:** Das [IdFix-Tool](install-and-run-idfix.md) können auch diesen Prozess viel leichter machen. 
  
- **displayName**
    
  - Wenn das Attribut im Benutzerobjekt vorhanden ist, wird es mit Office 365 synchronisiert.
  - Wenn dieses Attribut im Benutzerobjekt vorhanden ist, muss ein Wert dafür vorhanden sein. Das bedeutet, dass das Attribut nicht leer sein darf.
  - Maximale Anzahl der Zeichen: 256
    
- **givenName **
    
  - Wenn das Attribut im Benutzerobjekt vorhanden ist, wird es mit Office 365 synchronisiert. Es wird von Office 365 aber benötigt oder verwendet.
  - Maximale Anzahl der Zeichen: 64
    
- **mail**
    
  - Der Attributwert muss innerhalb des Verzeichnisses eindeutig sein.
    
    > [!NOTE]
    > Wenn doppelte Werte vorhanden sind, wird mit dem Wert der erste Benutzer synchronisiert. Nachfolgende Benutzer werden in Office 365 nicht angezeigt. Sie müssen entweder den Wert in Office 365 ändern oder Ändern einer der Werte in das lokale Verzeichnis damit beide Benutzer in Office 365 angezeigt werden. 
  
- **mailNickname** (Exchange-Alias) 
    
  - Der Attributwert darf nicht mit einem Punkt (.) beginnen.
  - Der Attributwert muss innerhalb des Verzeichnisses eindeutig sein.
    
- **proxyAddresses **
    
  - Attribut mit mehreren Werten
  - Maximale Anzahl von Zeichen pro Wert: 256
  - Der Attributwert darf keine Leerzeichen enthalten.
  - Der Attributwert muss innerhalb des Verzeichnisses eindeutig sein.
  - Ungültige Zeichen: \< \> (;) , [ ] "
    
    Beachten Sie, dass die ungültigen Zeichen für Zeichen als Trennzeichen Typ hinter gelten und ":", sodass SMTP:User@contso.com ist zulässig, SMTP:user:M@contoso.com ist jedoch nicht.
    
    > [!IMPORTANT]
    > Alle Simple Mail Transport Protocol (SMTP)-Adressen sollten e-Mail-messaging-Standards entsprechen. Wenn doppelte oder unerwünschte Adressen vorhanden sind, finden Sie unter dem Hilfethema [Entfernen doppelter und unerwünschte Proxy Adressen in Exchange](https://go.microsoft.com/fwlink/?LinkId=293860). 
  
- **sAMAccountName**
    
  - Maximale Anzahl von Zeichen: 20
  - Der Attributwert muss innerhalb des Verzeichnisses eindeutig sein.
  - Ungültige Zeichen: [\ "|, /: \< \> + =;? \* ]
  - Wenn ein Benutzer ein ungültiges Attribut **sAMAccountName**, aber ein gültiges Attribut **userPrincipalName** hat, wird das Benutzerkonto in Office 365 erstellt. 
  - Wenn beide **Attribute, sAMAccountName** und **UserPrincipalName** , ungültig sind, muss das lokalen Active Directory-Attribut **UserPrincipalName** aktualisiert werden. 
    
- **sn** (Nachname) 
    
  - Wenn das Attribut im Benutzerobjekt vorhanden ist, wird es mit Office 365 synchronisiert. Es wird von Office 365 aber benötigt oder verwendet.
    
- **targetAddress**
    
    Es ist erforderlich, dass das **TargetAddress** -Attribut (beispielsweise SMTP:tom@contoso.com), das für den Benutzer aufgefüllt wird in der Office 365 GAL vorhanden sein muss. Dies würde in Drittanbieter-messaging Migrationsszenarien die Office 365-Schema-Erweiterung für das lokale Verzeichnis erfordern. Die Erweiterung der Office 365-Schema würde auch zum Verwalten von Office 365-Objekten, die mithilfe einer verzeichnissynchronisierungstool aus lokalen Verzeichnis aufgefüllt werden andere nützliche Attribute hinzufügen. Beispielsweise würde das **MsExchHideFromAddressLists** -Attribut für die Verwaltung ausgeblendete Postfächer oder Verteilergruppen hinzugefügt werden. 
   
  - Maximale Anzahl der Zeichen: 256
  - Der Attributwert darf keine Leerzeichen enthalten.
  - Der Attributwert muss innerhalb des Verzeichnisses eindeutig sein.
  - Ungültige Zeichen: \ \< \> (;) , [ ] "
  - Alle SMTP-Adressen (Simple Mail Transport Protocol) müssen mit E-Mail-Messaging-Standards kompatibel sein.
    
- **userPrincipalName**
    
  - Das **UserPrincipalName** -Attribut muss im Internet-Anmeldung Format, in dem der Benutzername gefolgt wird, das @-Zeichen (@) und einem Domänennamen: beispielsweise user@contoso.com. Alle Simple Mail Transport Protocol (SMTP)-Adressen sollten e-Mail-messaging-Standards entsprechen.
  - Die maximale Anzahl von Zeichen für das **userPrincipalName**-Attribut beträgt 113. Vor und nach dem at-Zeichen (@) ist eine bestimmte Anzahl von Zeichen zulässig: 
  - Maximale Anzahl von Zeichen für den Benutzerdomänennamen vor dem @-Zeichen: 64
  - Maximale Anzahl der Zeichen für den Domänennamen hinter dem @-Zeichen: 48
  - Ungültige Zeichen: \ % &amp; \* + / =? { } | \< \> ( ) ; : , [ ] "
  - Ä ist auch ein ungültiges Zeichen.
  - Das @-Zeichen ist in jedem **UserPrincipalName** -Wert erforderlich. 
  - Das @-Zeichen darf nie das erste Zeichen in einem **userPrincipalName**-Wert sein. 
  - Der Benutzername darf nicht mit einem Punkt (.), einem kaufmännischen und-Zeichen enden (&amp;), ein Leerzeichen oder ein at-Zeichen (@).
  - Der Benutzername darf keine Leerzeichen enthalten.
  - Es müssen routingfähige Domänen verwendet werden. Beispielsweise können local oder interne Domänen verwendet werden.
  - Unicode-Zeichen werden in Unterstriche umgewandelt.
  - **userPrincipalName** darf keine doppelten Werte im Verzeichnis enthalten. 
    
## <a name="prepare-the-userprincipalname-attribute"></a>Vorbereiten des Attributs userPrincipalName

Active Directory ist darauf ausgelegt, um die Endbenutzer in Ihrer Organisation zur Anmeldung bei Ihrem Verzeichnis mithilfe von **sAMAccountName** oder **UserPrincipalName**zu ermöglichen. Endbenutzer können auf ähnliche Weise, melden Sie sich bei Office 365 mithilfe der Benutzerprinzipalname (UPN) ihrer Arbeit oder Schule Konto. Directory-Synchronisierung versucht, erstellen neue Benutzer in Azure Active Directory mit dem gleichen UPN, die in Ihrem lokalen Verzeichnis ist. Der Benutzerprinzipalname ist wie eine e-Mail-Adresse formatiert. 

In Office 365 wird der UPN das Standardattribut, das verwendet wird, um die e-Mail-Adresse zu generieren. Es ist einfach, **UserPrincipalName** abrufen (: lokal und in Azure Active Directory) und die primäre e-Mail-Adresse im **ProxyAddresses** auf unterschiedliche Werte festgelegt. Wenn sie auf unterschiedliche Werte festgelegt sind, können Verwirrung für Administratoren und Endbenutzer vorhanden sein. 
  
Es wird empfohlen, diese Attribute, um Verwechslungen zu vermeiden ausrichten. Die Anforderungen für einmaliges Anmelden mit Active Directory-Verbunddienste (AD FS) erfüllen 2.0, müssen Sie sicherstellen, dass die UPNs in Azure Active Directory und die lokale Active Directory übereinstimmen und einen gültigen Domänennamespace verwenden.
  
## <a name="add-an-alternative-upn-suffix-to-ad-ds"></a>Hinzufügen eines alternativen UPN-Suffixes zu AD DS

Sie müssen möglicherweise ein alternatives UPN-Suffix zum Zuordnen der Anmeldeinformationen des Benutzers im Unternehmen mit Office 365-Umgebung hinzufügen. Ein UPN-Suffix ist der Teil des UPN rechts neben dem @-Zeichen. UPNs, die für einmaliges Anmelden verwendet werden können Buchstaben, Zahlen, Punkte, Bindestriche und Unterstriche jedoch keine anderen Arten von Zeichen enthalten.
  
Weitere Informationen zum Hinzufügen eines alternativen UPN-Suffixes zu Active Directory finden Sie unter [Vorbereiten der verzeichnissynchronisierung]( https://go.microsoft.com/fwlink/p/?LinkId=525430).
  
## <a name="match-the-on-premises-upn-with-the-office-365-upn"></a>Abgleichen der lokalen UPNS mit dem Office 365 UPN

Wenn Sie bereits verzeichnissynchronisierung eingerichtet haben, kann des Benutzers UPN für Office 365 nicht die lokalen UPN des Benutzers übereinstimmen, die in Ihren lokalen Verzeichnisdienst definiert ist. Dies kann vorkommen, wenn ein Benutzer eine Lizenz zugewiesen wurde, bevor die Domäne überprüft wurde. Um dieses Problem zu beheben, mithilfe von [PowerShell doppelte UPN beheben](https://go.microsoft.com/fwlink/p/?LinkId=396730) aktualisieren UPN des Benutzers, um sicherzustellen, dass der Office 365 UPN corporate Benutzername und Domäne übereinstimmt. Wenn Sie den UPN in der lokalen Verzeichnisdienst aktualisieren und es mit Azure Active Directory-Identität synchronisieren möchten, müssen Sie die Lizenz des Benutzers in Office 365 zu entfernen, bevor Sie Änderungen lokale. 
  
Siehe auch [wie eine nicht-routingfähigen Domäne (beispielsweise Local Domäne) für die verzeichnissynchronisierung vorbereiten](prepare-a-non-routable-domain-for-directory-synchronization.md).
  
## <a name="directory-integration-tools"></a>Tools für die Directory-integration

Directory-Synchronisierung wird die Directory-Objekte (Benutzer, Gruppen und Kontakte) aus der lokalen Active Directory-Umgebung mit der Office 365 Directory-Infrastruktur Azure Active Directory-Synchronisierung. Eine Liste der verfügbaren Tools und ihre Funktionalität finden Sie unter [Directory Integration Tools](https://go.microsoft.com/fwlink/p/?LinkID=510956) . Das empfohlene Tool ist [Microsoft Azure Active Directory verbinden](https://go.microsoft.com/fwlink/p/?LinkID=510956). Weitere Informationen zu Azure Active Directory verbinden finden Sie unter [Integration von Ihrer lokalen Identitäten mit Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=527969).
  
Wenn Benutzerkonten mit Office 365-Verzeichnis zum ersten Mal synchronisiert werden, werden diese markiert als nicht aktiviert. Nicht senden oder Empfangen von e-Mails, und sie nicht Abonnementlizenzen belegen. Wenn Sie Office 365-Abonnements auf bestimmte Benutzer zuweisen möchten, müssen Sie wählen und durch [Zuweisen von Lizenzen für Benutzer in Office 365 für Unternehmen](https://support.office.com/article/997596b5-4173-4627-b915-36abac6786dc)zu aktivieren.
  
[PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=613097) können auch Lizenzen zuweisen. Informationen Sie [zum Verwenden von PowerShell, automatisch Lizenzen an die Office 365-Benutzer](https://go.microsoft.com/fwlink/p?LinkID=329805) eine automatisierte Lösung.