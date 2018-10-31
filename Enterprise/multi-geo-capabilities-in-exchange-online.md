---
title: Multi-Geo-Funktionen in Exchange Online
ms.author: chrisda
author: chrisda
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Normal
ms.assetid: ''
description: Erweitern Sie Ihre Office 365-Anwesenheit auf mehrere geografische Regionen mit Multi-Geo-Funktionen in Exchange Online.
ms.openlocfilehash: 5f34a2da47b9767aa9dfe22c6be7237951128960
ms.sourcegitcommit: a3e2b2e58c328238c15d3f9daf042ea3de9d66be
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2018
ms.locfileid: "25849921"
---
# <a name="multi-geo-capabilities-in-exchange-online"></a>Multi-Geo-Funktionen in Exchange Online

Multi-Geo-Funktionen in Office 365 aktivieren Sie einen einzelnen Mandanten auf mehrere geografische Standorte hinweg erstrecken. Wenn Multi-Geo aktiviert ist, können Kunden den Speicherort der Exchange Online Inhalt von Postfächern (Daten im Ruhezustand) für jeden Benutzer einzeln auswählen.

Ihres Standorts für Ihre anfänglichen Mandanten (bezeichnet als zentralen Ort) wird basierend auf Ihrer Adresse bestimmt. Wenn Multi-Geo aktiviert ist, können Sie Postfächer in zusätzliche Satelliten Speicherorte durch setzen:

- Erstellen eines neuen Postfachs Exchange Online direkt an einem Speicherort Satelliten.

- Verschieben Sie ein vorhandenes Exchange Online-Postfach an einem Speicherort Satelliten.

- Onboarding ein Postfach aus einer lokalen Exchange-Organisation direkt in einen Speicherort Satelliten.

Die folgenden Geo Speicherorte stehen für die Verwendung in einer Serverfarm mit mehreren Geo-Konfiguration:

- Asien-Pazifik

- Australien

- Kanada

- Europäische Union

- Frankreich

- Indien (derzeit nur verfügbar für Kunden mit Abrechnung Adressen in Indien)

- Japan

- Korea

- Vereinigtes Königreich

- Vereinigte Staaten

## <a name="prerequisite-configuration"></a>Erforderliche Konfiguration
Bevor Sie mit der Verwendung von Multi-Geo-Funktionen in Exchange Online beginnen können, muss Microsoft Ihren Exchange Online-Mandanten für die Unterstützung von Multi-Geo konfigurieren. In diesem einmaligen Konfigurationsprozess wird ausgelöst, nachdem Sie anordnen, dass Office 365 Multi-Geo und die Lizenzen in Ihrem Mandanten angezeigt. Diese einmalige Konfigurationsprozess sollte in der Regel weniger als 30 Tage dauern. Office 365 Multi-Geo bestellen, wenden Sie sich an Ihrem Microsoft-Partner. Weitere Informationen finden Sie unter https://aka.ms/Multi-Geo.

Sie erhalten Benachrichtigungen im [Office 365 Nachrichtencenter](https://support.office.com/article/Message-center-in-Office-365-38FB3333-BFCC-4340-A37B-DEDA509C2093) nach Abschluss die Konfiguration. Konfiguration wird automatisch ausgelöst, wenn Ihre Multi-Geo-Lizenzen in Ihrem Mandanten angezeigt.

## <a name="mailbox-placement-and-moves"></a>Platzierung von Postfach- und Verschiebungen
Nach Abschluss der Konfigurationsschritte erforderliche Multi-Geo Microsoft berücksichtigt Exchange Online Attributs **PreferredDataLocation** für Benutzerobjekte in Azure AD.

Exchange Online synchronisiert die **PreferredDataLocation** -Eigenschaft aus dem Azure Active Directory in die **MailboxRegion** -Eigenschaft in der Exchange Online-Verzeichnisdienst. Der Wert der **MailboxRegion** bestimmt die Platzierung von Benutzerpostfächern und alle zugehörigen archivpostfächer Geo. Es ist nicht möglich, eines Benutzers primären Postfach und Archiv von Postfächern in geografisch verschiedenen Standorten befinden, um zu konfigurieren. Pro User-Objekt kann nur über einen Geo Speicherort konfiguriert werden.

- Wenn ein Benutzer mit einem vorhandenen Postfach **PreferredDataLocation** konfiguriert ist, wird das Postfach in eine Warteschlange Umsetzung aufgenommen werden und automatisch an den angegebenen Geo-Speicherort verschoben. 

- Wenn ein Benutzer ohne ein vorhandenes Postfach **PreferredDataLocation** konfiguriert ist, wird das Postfach in der angegebenen Geo Speicherort bereitgestellt werden. 

- Wenn **PreferredDataLocation** auf einem bestimmten Benutzer nicht angegeben wird, wird das Postfach in der zentralen Speicherort platziert werden.

- Wenn der Code **PreferredDataLocation** falsch ist (z. B. ein Typ von NAN anstelle von Name), wird das Postfach in der zentralen Speicherort platziert werden.

**Hinweis**: Multi-Geo-Funktionen und Skype für Business Online gehostet Regional Besprechungen, verwenden Sie die **PreferredDataLocation** -Eigenschaft auf User-Objekte, um Dienste zu suchen. Wenn Sie **PreferredDataLocation** Werte für Benutzerobjekte Regional gehosteten Besprechungen konfigurieren, wird das Postfach für diesen Benutzer automatisch an den angegebenen Geo Speicherort verschoben, nachdem Multi-Geo auf dem Office 365-Mandanten aktiviert ist.

## <a name="feature-limitations-for-multi-geo-in-exchange-online"></a>Einschränkungen für Multi-Geo in Exchange Online
1. Nur Benutzerpostfächer, Ressourcenpostfächer (Raum- und Equipment Mailboxes) und freigegebene Postfächer Multi-Geo-Features nicht unterstützt. Öffentliche Ordner-Postfächer und Office 365 Gruppen bleiben am zentralen Standort.
 
2. Sicherheit und Richtlinientreue (beispielsweise Überwachung und eDiscovery) in der Exchange-Verwaltungskonsole (EAC) verfügbaren Features sind nicht in Organisationen mit mehreren geografisch verfügbar. Stattdessen müssen Sie [Office 365-Sicherheit und Compliance Center](https://support.office.com/article/7e696a40-b86b-4a20-afcc-559218b7b1b8) verwenden, um Features für Sicherheit und Einhaltung von Bestimmungen zu konfigurieren.

3. Outlook für Mac-Benutzer kann einen vorübergehenden Verlust des Zugriffs auf ihre Ordner Onlinearchiv auftreten, während Sie ihr Postfach an einen neuen Speicherort Geo bewegen. Diese Bedingung tritt auf, wenn die primäre Benutzerordner und archivpostfächer befinden sich in unterschiedlichen Geo-Speicherorte, da das Verschieben von Postfächern Cross-Geo zu unterschiedlichen Zeiten abgeschlossen werden können.

4. Benutzer können nicht *Postfachordner* für Geo Speicherorten in Outlook im Web (früher als Outlook Web App oder OWA bezeichnet) freigeben. Beispielsweise kann kein Benutzer in der Europäischen Union Outlook im Web verwenden, um einen freigegebenen Ordner in einem Postfach zu öffnen, die sich in den USA befindet. Outlook auf dem Web-Benutzer kann jedoch *anderer Postfächer an* in anderen Geos öffnen, indem Sie mit einem separaten Browserfenster wie beschrieben in [eine andere Person Postfach in einem separaten Browserfenster in Outlook Web App zu öffnen](https://support.office.com/article/A909AD30-E413-40B5-A487-0EA70B763081#__toc372210362).

    **Hinweis**: Cross-Geo Postfach Ordnerfreigabe in Outlook auf Windows unterstützt wird.

## <a name="administration"></a>Administration 
Remote-PowerShell ist erforderlich, anzeigen und mit mehreren geografisch Eigenschaften in der Office 365-Umgebung konfigurieren. Informationen zu verschiedenen PowerShell-Module zum Verwalten von Office 365 finden Sie unter [Verwalten von Office 365 und Exchange Online mit Windows PowerShell](https://support.office.com//article/06a743bb-ceb6-49a9-a61d-db4ffdf54fa6)verwendet.

- Sie benötigen die [Microsoft Azure Active Directory-PowerShell-Modul](https://social.technet.microsoft.com/wiki/contents/articles/28552.microsoft-azure-active-directory-powershell-module-version-release-history.aspx) v1.1.166.0 oder später in v1.x an die **PreferredDataLocation** -Eigenschaft auf User-Objekte angezeigt werden. User-Objekte in AAD über AAD Connect synchronisiert können nicht ihre **PreferredDataLocation** Wert direkt über die PowerShell AAD geändert haben. Nur-Cloud-User-Objekte können über die PowerShell AAD geändert werden. Zum Verbinden mit Azure AD-PowerShell finden Sie unter [Connect to Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell). 

- Zum Verbinden mit Exchange Online PowerShell finden Sie unter [Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell). 

### <a name="connect-directly-to-a-specific-geo-using-exchange-online-powershell"></a>Verbinden Sie mit einer bestimmten Geo von Exchange Online PowerShell direkt
Exchange Online PowerShell wird in der Regel mit den Standardspeicherort Geo verbunden. Aber Sie können auch direkt mit nicht standardmäßigen Geo Speicherorte anschließen. Es wird empfohlen, aufgrund von Leistungssteigerungen direkt auf den Speicherort nicht standardmäßigen Geo verbinden, wenn Sie nur Benutzer an diesem Standort Geo verwalten.

Zum Verbinden mit einer bestimmten Geo ist der Parameter *ConnectionUri* anders als die regulären Verbindung Anweisungen. Die restlichen Befehle und Werte sind identisch. Die Schritte sind:

1. Öffnen Sie auf dem lokalen Computer Windows PowerShell, und führen Sie den folgenden Befehl aus:
    
    ```
    $UserCredential = Get-Credential
    ```
   Klicken Sie im Dialogfeld **Windows PowerShell anmelden** Geben Sie die geschäftliche Rufnummer oder Schule Konto und Kennwort ein, und klicken Sie dann auf **OK**.
    
2. Ersetzen Sie `<emailaddress>` mit der e-Mail-Adresse von **jedem** Postfach im Zielspeicherort Geo und den folgenden Befehl ausführen. Die Berechtigungen für das Postfach und in Bezug auf Ihre Anmeldeinformationen in Schritt 1 sind keinen Faktor. die e-Mail-Adresse weist einfach Exchange Online, wo Sie eine Verbindung herstellen.
  
   ```
   $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell?email=<emailaddress> -Credential $UserCredential -Authentication  Basic -AllowRedirection
   ```

   Wenn olga@contoso.onmicrosoft.com die e-Mail-Adresse eines Postfachs in die Geo gültig, den Sie eine Verbindung herstellen möchten ist, führen Sie beispielsweise den folgenden Befehl ein:

   ```
   $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell?email=olga@contoso.onmicrosoft.com -Credential $UserCredential -Authentication  Basic -AllowRedirection
   ```
3. Führen Sie den folgenden Befehl aus:
    
    ```
    Import-PSSession $Session
    ```

### <a name="azure-ad-connect-version-requirements"></a>Anforderungen an Softwareversionen von Azure Active Directory verbinden
Verbinden von AAD Version 1.1.524.0 oder höher ist die einzige unterstützte Methode zum Festlegen der **PreferredDataLocation** -Eigenschaft auf User-Objekte, die synchronisiert werden aus dem lokalen Active Directory. User-Objekte in AAD über AAD Connect synchronisiert können nicht ihre **PreferredDataLocation** Wert direkt über die PowerShell AAD geändert haben. Nur-Cloud-User-Objekte können über die PowerShell AAD geändert werden. Ausführliche Anweisungen finden Sie unter [Azure Active Directory verbinden Sync: Konfigurieren des bevorzugten Datenspeicherort für Office 365-Ressourcen](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).

### <a name="geo-codes"></a>Geo-Codes
Drei Buchstaben Codes können Sie die geografisch in der **PreferredDataLocation** -Eigenschaft festlegen. Die folgende Tabelle enthält die Codes für die Geos verfügbar:

|Geo |Code |
|---------|---------|
|Asien-Pazifik |APC |
|Australien |AUS |
|Kanada |CAN |
|Europäische Union |EUR |
|Frankreich |FRA|
|Indien |IND |
|Japan |JPN |
|Korea |KOR |
|Vereinigtes Königreich |GBR |
|Vereinigte Staaten |NAM |

**Hinweis**: die Eigenschaften **PreferredDataLocation** und **MailboxRegion** sind Zeichenfolgen mit keine Fehler überprüfen. Wenn Sie einen ungültigen Wert (beispielsweise NAN) eingeben wird das Postfach in der standardmäßigen Geo platziert werden.

### <a name="view-the-available-geos-that-are-configured-in-your-exchange-online-organization"></a>Anzeigen der verfügbaren Geos, die in Ihrer Exchange Online-Organisation konfiguriert sind
Um die Liste der konfigurierten Geos in Ihrer Exchange Online-Organisation anzuzeigen, führen Sie den folgenden Befehl im Exchange Online PowerShell:

```
Get-OrganizationConfig | Select -ExpandProperty AllowedMailboxRegions | Format-Table
```

Die Ausgabe des Befehls sieht wie folgt aus:

```
APC
AUS
CAN
EUR
FRA
GBR
JPN
KOR
NAM
```

### <a name="view-the-default-geo-for-your-exchange-online-organization"></a>Die Standardeinstellung Geo für Ihre Exchange Online-Organisation anzeigen
Um die standardmäßige Geo Ihrer Exchange Online-Organisation anzuzeigen, führen Sie den folgenden Befehl im Exchange Online PowerShell:

```
Get-OrganizationConfig | Select DefaultMailboxRegion
```

Die Ausgabe des Befehls sieht wie folgt aus:

```
DefaultMailboxRegion
--------------------
NAM
```


### <a name="find-the-geo-location-of-a-mailbox"></a>Suchen Sie den Speicherort Geo eines Postfachs
Das Cmdlet **Get-Mailbox** in Exchange Online PowerShell zeigt die folgenden Multi-Geo bezogenen Eigenschaften für Postfächer:

- **Datenbank**: die ersten 3 Buchstaben des Datenbanknamens entsprechen Geo-Code, dem Sie darüber informiert, in dem das Postfach aktuell gespeichert ist. Für Online Archivpostfächer der **ArchiveDatabase** sollte-Eigenschaft verwendet werden.

- **MailboxRegion**: Gibt den Code der Geo-Speicherort, der durch den Administrator (aus **PreferredDataLocation** in Azure Active Directory synchronisiert) festgelegt wurde.

- **MailboxRegionLastUpdateTime**: Gibt an, wann MailboxRegion (automatisch oder manuell) zuletzt aktualisiert wurde.

Um diese Eigenschaften für ein Postfach anzuzeigen, verwenden Sie die folgende Syntax:

```
Get-Mailbox -Identity <MailboxIdentity> | Format-List Database,MailboxRegion*
```

Um die Geo-Informationen für das Postfach chris@contoso.onmicrosoft.com angezeigt wird, führen Sie beispielsweise den folgenden Befehl:

```
Get-Mailbox -Identity chris@contoso.onmicrosoft.com | Format-List Database, MailboxRegion*
```

Die Ausgabe des Befehls sieht wie folgt aus:

```
Database                    : EURPR03DG077-db007 
MailboxRegion               : EUR 
MailboxRegionLastUpdateTime : 2/6/2018 8:21:01 PM 
```

> **Hinweis:** Wenn der Code Geo Speicherort in den Namen der Datenbank **MailboxRegion** Wert entspricht, wird das Postfach werden automatisch in eine Warteschlange Umsetzung aufgenommen werden und in den angegebenen durch den Wert **MailboxRegion** Geo Speicherort verschoben (Exchange Online sucht nach einer Konflikt zwischen diese Eigenschaftswerte).

### <a name="move-an-existing-cloud-only-mailbox-to-a-specific-geo"></a>Verschieben eines vorhandenen nur-Cloud-Postfachs in einer bestimmten Geo
Ein nur-Cloud-Benutzer ist ein Benutzer nicht Syncrhonized über AAD Connect-Mandanten. Diesen Benutzer wurde direkt in Azure Active Directory erstellt. Verwenden Sie die Cmdlets **Get-MsolUser** und **Set-MsolUser** in Azure AD-Moduls für Windows PowerShell anzeigen oder Angeben der Geo, eine nur-Cloud-Postfach des Benutzers gespeichert wird.

Um den Wert **PreferredDataLocation** für einen Benutzer anzuzeigen, verwenden Sie diese Syntax in Azure AD-PowerShell:

```
Get-MsolUser -UserPrincipalName <UserPrincipalName> | Format-List UserPrincipalName,PreferredDataLocation
```

Um den **PreferredDataLocation** -Wert für den Benutzer michelle@contoso.onmicrosoft.com angezeigt wird, führen Sie beispielsweise den folgenden Befehl:

```
Get-MsolUser -UserPrincipalName michelle@contoso.onmicrosoft.com | Format-List
```

Die Ausgabe des Befehls sieht wie folgt aus:

```
UserPrincipalName     : michelle@contoso.onmicrosoft.com
PreferredDataLocation : EUR
```

Verwenden Sie die folgende Syntax zum Ändern des **PreferredDataLocation** -Werts für ein nur-Cloud-Benutzerobjekt in Azure AD-PowerShell:

``` 
Set-MsolUser -UserPrincipalName <UserPrincipalName> -PreferredDataLocation <GeoCode>
```

Um die **PreferredDataLocation** -Wert der Europäischen Union (EUR) Geo für den Benutzer michelle@contoso.onmicrosoft.com festzulegen, führen Sie beispielsweise den folgenden Befehl:

``` 
Set-MsolUser -UserPrincipalName michelle@contoso.onmicrosoft.com -PreferredDataLocation EUR
```

**Hinweise**:

- Wie weiter oben erwähnt können nicht zuvor nachfolgend für synchronisierte User-Objekte aus dem lokalen Active Directory verwendet werden. Sie müssen den **PreferredDataLocation** -Wert mit AAD verbinden zu ändern. Weitere Informationen finden Sie unter [Azure Active Directory verbinden Sync: Konfigurieren des bevorzugten Datenspeicherort für Office 365-Ressourcen](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation). 

- Wie lange dauert es, um eine Mailboxfrom zu verschieben, dessen aktuelle Geo am neuen Speicherort für die gewünschte Geo verschiedenen Faktoren abhängig:
 
  - Die Größe und Typ des Postfachs.
 
  - Die Anzahl der Postfächer, die verschoben werden.
 
  - Die Verfügbarkeit von Ressourcen verschieben.

#### <a name="move-disabled-mailboxes-that-are-on-litigation-hold"></a>Move Postfächer, die auf die Aufbewahrung für eventuelle Rechtsstreitigkeiten sind deaktiviert
Postfächer auf Aufbewahrung für eventuelle Rechtsstreitigkeiten, die für eDiscovery beibehalten werden, die Zwecke verschoben werden können, indem Sie ihre **PreferredDataLocation** Wert im deaktivierten Zustand deaktiviert. Verschieben eines deaktiviert Postfachs beweissicherungsverfahren:

1. Das Postfach vorübergehend eine Lizenz zuweisen.

2. Ändern der **PreferredDataLocation**.

3. Entfernen Sie die Lizenz aus dem Postfach, nachdem er auf den ausgewählten Geo Speicherort verschoben wurde, um wieder in den aktiven Zustand zu platzieren.

### <a name="create-new-cloud-mailboxes-in-a-specific-geo"></a>Erstellen Sie neue Cloud-Postfächer in einer bestimmten Geo 
Zum Erstellen eines neuen Postfachs in einem bestimmten Geo-Speicherort müssen Sie führen Sie einen der folgenden Schritte aus:

- Konfigurieren Sie den Wert **PreferredDataLocation** , wie beschrieben in den Abschnitt der vorherigen *vor* , wenn, die das Postfach im Exchange Online erstellt wird. Konfigurieren Sie beispielsweise den Wert **PreferredDataLocation** für einen Benutzer, bevor Sie eine Lizenz zuweisen. 

- Weisen Sie eine Lizenz zur selben Zeit, den, die Sie den Wert **PreferredDataLocation** festlegen.

Verwenden Sie die folgende Syntax, um einen neuen Cloud-only lizenzierten Benutzer (nicht AAD verbinden synchronisiert) in einer bestimmten Geo erstellen, in Azure AD-PowerShell:

```
New-MsolUser -UserPrincipalName <UserPrincipalName> -DisplayName "<Display Name>" [-FirstName <FirstName>] [-LastName <LastName>] [-Password <Password>] [-LicenseAssignment <AccountSkuId>] -PreferredDataLocation <GeoCode> 
```
In diesem Beispiel erstellen Sie ein neues Benutzerkonto für Elizabeth Brunner mit den folgenden Werten:

- Benutzerprinzipalname: ebrunner@contoso.onmicrosoft.com

- Vorname: Elizabeth

- Nachname: Brunner

- Anzeigename Elizabeth Brunner

- Kennwort: zufällig generiert und in die Ergebnisse des Befehls (da wir den Parameter *Password* nicht verwenden)

- Lizenz: Contoso:ENTERPRISEPREMIUM (E5)

- Standort: Australien (AUS)

```
New-MsolUser -UserPrincipalName ebrunner@contoso.onmicrosoft.com -DisplayName "Elizabeth Brunner" -FirstName Elizabeth -LastName Brunner -LicenseAssignment contoso:ENTERPRISEPREMIUM -PreferredDataLocation AUS
```

Weitere Informationen zum Erstellen neuer Benutzerkonten und Suchen von LicenseAssignment Werte in Azure AD-PowerShell finden Sie unter [Erstellen von Benutzerkonten mit Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/create-user-accounts-with-office-365-powershell) und [Lizenzen anzeigen und-Dienste mit Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/view-licenses-and-services-with-office-365-powershell).

> **Hinweis:** Wenn Sie zum Aktivieren eines Postfachs und benötigen das Postfach direkt in die Geo erstellt werden, die in **PreferredDataLocation**angegeben ist Exchange Online PowerShell verwenden, müssen Sie ein Exchange Online-Cmdlet wie **Enable-Mailbox** oder **New-Mailbox verwenden **direkt für die Cloud-Dienst. Wenn Sie das Cmdlet **Enable-RemoteMailbox** lokale Exchange verwenden, wird das Postfach in der standardmäßigen Geo erstellt wird.

### <a name="onboard-existing-on-premises-mailboxes-in-a-specific-geo"></a>Integrierte einer vorhandenen lokalen Postfächer in einer bestimmten Geo
Die standard-Onboarding-Tools und Prozesse können Sie ein Postfach aus einer lokalen Exchange-Organisation zu Exchange Online, einschließlich der [migrationsdashboard in der Exchange-Verwaltungskonsole](https://support.office.com/article/d164b35c-f624-4f83-ac58-b7cae96ab331)und das Cmdlet [New-MigrationBatch](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-migrationbatch) im Exchange Online migrieren PowerShell.

Der erste Schritt besteht, stellen Sie sicher, dass ein User-Objekt vorhanden ist, für jedes Postfach Onboarded, und stellen Sie sicher, dass der richtige Wert **PreferredDataLocation** in Azure Active Directory konfiguriert ist. Onboarding-Tools werden den Wert **PreferredDataLocation** berücksichtigt und migrieren Sie die Postfächer werden direkt an die angegebenen Geo.

Alternativ können Sie auf integrierte Postfächer direkt in einem bestimmten Geo Speicherort mithilfe des Cmdlets [New-MoveRequest](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-moverequest) in Exchange Online PowerShell die folgenden Schritte aus.

1. Stellen Sie sicher, dass das Benutzerobjekt vorhanden ist, für jedes Postfach Onboarded und **PreferredDataLocation** in Azure Active Directory auf den gewünschten Wert festgelegt ist. Der Wert der **PreferredDataLocation** werden dem **MailboxRegion** -Attribut des entsprechenden e-Mail-Benutzerobjekts im Exchange Online synchronisiert.

2. Verbinden Sie direkt mit der bestimmte Satelliten Geo mithilfe der Connection-Anweisungen aus weiter oben in diesem Thema.

3. In Exchange Online PowerShell speichern Sie die lokalen Administrator-Anmeldeinformationen, die zum Ausführen einer Migrations von Postfächern in einer Variablen, mithilfe des folgenden Befehls verwendet wird:

    ```
    $RC = Get-Credential
    ```

4. Erstellen Sie in Exchange Online PowerShell eine neue **New-MoveRequest** ähnlich dem folgenden Beispiel: 

    ```
    New-MoveRequest -Remote -RemoteHostName mail.contoso.com -RemoteCredential $RC -Identity user@contoso.com -TargetDeliveryDomain <YourAppropriateDomain>
    ```

5. Wiederholen Sie Schritt #4 für jedes Postfach, die Sie benötigen zum Migrieren von lokalem Exchange zu den Satelliten Speicherort, den Sie derzeit verbunden sind.

6. Wenn Sie zusätzliche Postfächer in einen anderen Satelliten Speicherort migrieren möchten, wiederholen Sie die Schritte 2 bis 4 für jeden Satellitenstandort bestimmte.

### <a name="multi-geo-reporting"></a>Multi-Geo Reporting
**Multi-Geo Usage Reports** in Office 365 Administrationscenter zeigt die Anzahl der Benutzer, hängt vom Speicherort Geo. Der Bericht zeigt die Verteilung der Benutzer für den aktuellen Monat und bietet Verlaufsdaten für die letzten 6 Monate.
