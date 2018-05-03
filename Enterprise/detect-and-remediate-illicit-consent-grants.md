---
title: Erkennen und Warten von unerlaubten Zustimmung erteilt in Office 365
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 4/23/2018
ms.audience: ITPro
ms.topic: article
ms.collection:
- o365_security_incident_response
- Strat_O365_IP
ms.service: o365-solutions
localization_priority: Normal
ms.custom: ''
ms.assetid: ''
description: Informationen Sie zum Erkennen und Warten des unerlaubten Zustimmung erteilt Angriffs in Office 365.
ms.openlocfilehash: f6576fccd7cac49dbbf2e9ea359e08257ddc42d0
ms.sourcegitcommit: a4322cac992ce64b92f0335bf005a7420195d9be
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
---
# <a name="detect-and-remediate-illicit-consent-grants-in-office-365"></a>Erkennen und Warten von unerlaubten Zustimmung erteilt in Office 365

**Zusammenfassung**  Informationen Sie zum Erkennen und Warten des unerlaubten Zustimmung erteilt Angriffs in Office 365.

## <a name="what-is-the-illicit-consent-grant-attack-in-office-365"></a>Was ist der unerlaubten Zustimmung Grant-Angriff in Office 365?
Erteilen Sie in einer unerlaubten Zustimmung Angriff, der Angreifer eine Anwendung Azure registriert erstellt, die Zugriff auf Daten beispielsweise Kontaktinformationen, e-Mail, fordert oder Dokumente. Der Angreifer tricks dann einen Endbenutzer in gewähren diese Anwendung Zustimmung auf ihre Daten zugreifen, entweder über einen Phishingangriff, oder indem er unerlaubte Code in einer vertrauenswürdigen Website einfügt. Nachdem die Anwendung unerlaubten Zustimmung eingeholt wurde, ist der Konto-Ebene Zugriff auf Daten ohne die Notwendigkeit einer organisationskonto. Normale Wiederherstellungsschritte, wie das Zurücksetzen von Kennwörtern für Konten eingebrochen wurde oder dass Multi-Factor Authentication (mehrstufiger Authentifizierung das) auf Konten erforderlich sind keine effektive vor dieser Art von Angriff, da diese drittanbieteranwendungen werden und sind außerhalb des Unternehmens. Diese Angriffe nutzen eine Interaktionsmodell der setzt voraus, dass die Entität, die die Informationen aufruft Automatisierung und keine Human ist.

## <a name="what-does-an-illicit-consent-grant-attack-look-like-in-office-365"></a>Wie sieht eine unerlaubten Zustimmung Grant-Angriff Aussehen in Office 365?
Sie müssen die Office 365 **Überwachungsprotokoll** auf Anzeichen, auch als bezeichnet Indikatoren des Kompromiss (IOC) dieses Angriffs zu suchen. Für Organisationen mit vielen Azure-registrierten Programmen und eine große Benutzerbasis ist es empfehlenswert Ihrer Organisationen Zustimmung erteilt wöchentlich überprüfen.
### <a name="steps-for-finding-signs-of-this-attack"></a>Anleitung zum Suchen nach diesem Angriff auf Anzeichen
1. Öffnen Sie die **Sicherheit und Compliance Center** in Ihrem Office 365-Mandanten.
2. Navigieren Sie zum Knoten **Untersuchung & durchsuchen** , und wählen Sie **postfachüberwachungsprotokoll** suchen.
3. Erstellen Sie eine Suche (alle Aktivitäten und alle Benutzer) und Filtern Sie der Ergebnisse für Zustimmung an Anwendung, und fügen Sie OAuth2PermissionGrant.
4. Überprüfen Sie die erweiterte Eigenschaften und die Kontrollkästchen, um festzustellen, ob IsAdminContent auf True festgelegt ist.


Wenn dieser Wert auf true festgelegt ist, bedeutet dies, dass jemand globaler Administrator Zugriff einen umfassenden Zugriff auf Daten gewährt haben kann. Wenn dies unerwartet ist, führen Sie Schritte aus, [Angriff zu bestätigen](detect-and-remediate-illicit-consent-grants.md#confirmattack).

<a name="confirmattack"> </a>
## <a name="how-to-confirm-an-attack"></a>Gewusst wie: Angriff bestätigen
Wenn Sie bereits eine oder mehrere Instanzen der IOCs oben aufgeführten, müssen Sie weitere Untersuchung, positiv zu bestätigen, dass der Angriff aufgetreten ist. Eine der folgenden drei Methoden können Sie um den Angriff zu bestätigen.
- Inventar-Anwendungen und deren Berechtigungen mithilfe des Azure Active Directory-Portals. Diese Methode ist gründliche, aber Sie können nur einen Benutzer zu einem Zeitpunkt, sehr zeitaufwendig sein kann, überprüfen, wenn viele Benutzer zu überprüfen.
- Inventar-Anwendungen und ihre Berechtigungen von PowerShell. Dies ist die schnellste und gründliche-Methode, mit den geringsten Aufwand.
- Haben Sie Ihre Benutzer einzeln überprüfen Sie ihre apps und die Berechtigungen und die Ergebnisse zurück an die Administratoren für die Behebung zu melden.

## <a name="inventory-apps-with-access-in-your-organization"></a>Inventar-apps mit Access in Ihrer Organisation
Sie können für Ihre Benutzer mit dem Azure Active Directory-Portal oder einem PowerShell dafür oder müssen sich die Benutzer ihre Anwendung Access einzeln auflisten.

### <a name="steps-for-using-the-azure-active-directory-portal"></a>Schritte für die Verwendung des Azure Active Directory-Portals
Sie können die Anwendungen suchen, die jeder einzelne Benutzer Berechtigungen erteilt hat, mithilfe des [Azure Active Directory-Portal](https://portal.azure.com/). 
1. Melden Sie sich bei der Azure-Verwaltungsportal mit Administratorrechten.
2. Wählen Sie das Blade Azure Active Directory aus.
3. Wählen Sie **Benutzer**aus.
4. Wählen Sie den Benutzer, den Sie überprüfen möchten.
5. Wählen Sie **Applications**aus.

Dies wird gezeigt, die apps, die der Benutzer und was zugewiesen sind, Berechtigungen die Applcations verfügen.

### <a name="steps-for-having-your-users-enumerate-their-application-access"></a>Schritte für die Benutzer müssen auflisten ihre Anwendungszugriff
Haben Sie Ihre Benutzer wechseln Sie zur https://myapps.microsoft.com , und überprüfen Sie ihre eigenen Anwendungszugriff vorhanden. Sie sollten finden Sie unter alle apps mit Access, Details dazu (einschließlich des Bereichs von Access) anzeigen können, und sein können Berechtigungen für apps verdächtigen oder unerlaubten widerrufen werden sollen.

### <a name="steps-for-doing-this-with-powershell"></a>Schritte für diesen Vorgang mithilfe von PowerShell
Die einfachste Möglichkeit zum Überprüfen des unerlaubten stimmen Grant-Angriffs ist die OAuth Zustimmung erteilen und app-Berechtigungen für alle Benutzer in eine CSV-Datei in Ihrer Instanz sichern wird [Get-AzureADPSPermissions.ps1](https://gist.github.com/psignoret/41793f8c6211d2df5051d77ca3728c09), ausführen. 

#### <a name="pre-requisites"></a>Voraussetzungen
- Die Azure AD-PowerShell-Bibliothek installiert.
- Globale Administratorrechte für den Mandanten, dem gegen das Skript ausgeführt wird.
- Lokaler Administrator auf dem Computer, von dem aus die Skripts ausgeführt wird.

> [!IMPORTANT]
> Es wird dringend empfohlen, dass Sie auf Ihr Administratorkonto mehrstufige Authentifizierung benötigen.  Dieses Skript unterstützt mehrstufiger Authentifizierung das Authentifizierung.

1. Melden Sie sich an dem Computer, auf dem Sie das Skript aus mit lokalen Administratorrechten ausgeführt werden.
2. Laden Sie oder kopieren Sie das [Get-AzureADPSPermissions.ps1](https://gist.github.com/psignoret/41793f8c6211d2df5051d77ca3728c09) -Skript aus GitHub in einen Ordner aus dem Sie die Scruipt ausgeführt werden.  Dadurch werden im gleichen Ordner, den die Ausgabedatei "permissions.csv" geschrieben werden soll.
3. Öffnen Sie eine Instanz der PowerShell als Administrator, und öffnen Sie des Ordners, den Sie das Skript gespeichert haben.
4. Verbinden in das Verzeichnis mit dem Cmdlet [Connect-AzureAD](https://docs.microsoft.com/en-us/powershell/module/azuread/connect-azuread?view=azureadps-2.0) .
5. Führen Sie folgende PowerShell-Befehlszeile wie folgt aus:`.Get-AzureASPSPermissions.ps1 | Export-csv -path "Permissions.csv" -NoTypeInformation`

Das Skript wird eine Datei mit dem Namen Permissions.csv erzeugt. Folgen Sie diesen Schritten unerlaubten Anwendung Berechtigungen gewährt gesucht: 
1. Suchen Sie in der Spalte ConsentType (Spalte G) für den Wert "AllPrinciples". Die Berechtigung AllPrincipals ermöglicht die Clientanwendung auf alle Inhalte im Mandanten zuzugreifen. Systemeigene Office 365-Anwendungen benötigen diese Berechtigung, um ordnungsgemäß funktionieren. Jede nicht-Microsoft-Anwendung mit dieser Berechtigung sollten sorgfältig überprüft werden.
2.  Bei der Überprüfung der Berechtigung Spalte (Spalte F) verfügt über die Berechtigungen, dass jede Anwendung delegiert auf Inhalte. Suchen Sie nach der Berechtigung "Lesen" und "Schreiben" oder "*. Alle"Berechtigung, und überprüfen, die diese sorgfältig, da sie möglicherweise nicht geeignet.
3.  Überprüfen Sie die bestimmte Benutzer, die bewilligen hiermit erteilt haben. Wenn hohe Profil oder starke Auswirkung Benutzer ungeeignetes bewilligen hiermit erteilt haben, sollten Sie weiter zu untersuchen.
4.  Suchen Sie in der Spalte ClientDisplayName (Spalte C) für apps, die scheinbar verdächtigen. Apps mit falsch geschriebenen Namen super weil, oder mit der Kategorie Hacker Namen sollte sorgfältig überprüft werden.

## <a name="determine-the-scope-of-the-attack"></a>Bestimmen Sie den Umfang des Angriffs
Nachdem Sie die Anwendung Access Bestandsaufnahme abgeschlossen haben, überprüfen Sie die Office 365 **Überwachungsprotokoll** um den vollen Umfang der Verletzung zu ermitteln.  Suche auf die betroffenen Benutzer, die Zeiträume, die die Anwendung unerlaubten hatte den Zugriff auf Ihrer Organisation und die Berechtigungen die app hatte. Sie können das **Überwachungsprotokoll** in [Office 365-Sicherheit und Compliance Center](https://support.office.com/en-us/article/Search-the-audit-log-in-the-Office-365-Security-Compliance-Center-0d4d0f35-390b-4518-800e-0c7ec95e946c)suchen. 

> [!IMPORTANT]
> [Überwachung von Postfächern](https://support.office.com/en-us/article/Enable-mailbox-auditing-in-Office-365-aaca8987-5b62-458b-9882-c28476a66918) und [Aktivität Überwachung für Administratoren und der Benutzer](https://support.office.com/en-us/article/turn-office-365-audit-log-search-on-or-off-e893b19a-660c-41f2-9074-d3631c95a014) muss vor dem Angriff für diese Informationen erhalten Sie aktiviert worden sein.

## <a name="how-to-stop-and-remediate-an-illicit-consent-grant--attack"></a>Zum Beenden und warten einen unerlaubten Zustimmung Grant-Angriff
Nachdem Sie eine Anwendung mit unerlaubten Berechtigungen identifiziert haben, müssen Sie verschiedene Möglichkeiten, dass der Zugriff zu entfernen.
- Sie können die Anwendung die Berechtigung im Azure Active Directory Portal durch widerrufen:
    - Navigieren Sie zu der betroffenen Benutzer in der Blade **Azure Active Directory-Benutzer** .
    - Wählen Sie **Applications**aus.
    - Wählen Sie die unerlaubten aus.
    - Klicken Sie auf **Entfernen** in den Drillthrough nach unten.
- Sie können die OAuth Zustimmung erteilen mit PowerShell widerrufen, durch die Schritte in [Remove-AzureADOAuth2PermissionGrant](https://docs.microsoft.com/en-us/powershell/module/azuread/Remove-AzureADOAuth2PermissionGrant?view=azureadps-2.0).
- Sie können die Dienst-App-Rollenzuweisung mit PowerShell widerrufen, durch die Schritte in [Remove-AzureADServiceAppRoleAssignment](https://docs.microsoft.com/en-us/powershell/module/azuread/Remove-AzureADServiceAppRoleAssignment?view=azureadps-2.0).
- Sie können auch-Anmeldung für die betroffenen Konto vollständig deaktivieren, die wiederum die app-Zugriff auf Daten in diesem Konto deaktiviert wird. Dies ist nicht ideal für die Endbenutzer Produktivität und natürlich, wenn Sie arbeiten, um Einfluss schnell zu begrenzen, kann ein mögliches kurzfristige Remediation sein.
- Sie können integrierte Anwendung für Ihre Instanz deaktivieren. Dies ist ein schwerwiegender Schritt, der die Möglichkeit für Endbenutzer Zustimmung für einzelne Mandanten geltende deaktiviert. Dadurch wird verhindert, dass Ihre Benutzer versehentlich gewähren des Zugriffs auf eine bösartige Anwendung. Dies ist nicht dringend empfohlen, wie es Ihre Anwender mit Drittanbieter-Applikationen verhelfen stark nichtkritischen.  Hierzu können Sie die Schritte in [Aktivieren der integrierten-Apps aktiviert oder deaktiviert](https://support.office.com/en-us/article/Turning-Integrated-Apps-on-or-off-7e453a40-66df-44ab-92a1-96786cb7fb34).

## <a name="secure-office-365-like-a-cybersecurity-pro"></a>Sichern von Office 365 wie eine pro Sicherheit im Internet
Ihr Office 365-Abonnement verfügt über eine leistungsstarke Reihe von Sicherheitsfunktionen, die Sie verwenden können, um Ihre Daten und Ihre Benutzer zu schützen.  Verwendung der [Wegweiser für Office 365-Sicherheit: Top-Prioritäten für den ersten 30 Tagen 90 Tage und darüber hinaus](https://support.office.com/en-us/article/office-365-security-roadmap-top-priorities-for-the-first-30-days-90-days-and-beyond-28c86a1c-e4dd-4aad-a2a6-c768a21cb352) zur Implementierung von Microsoft empfohlene bewährte Methoden zum Sichern Ihrer Office 365-Mandanten.
- Aufgaben in den ersten 30 Tagen ausgeführt.  Diesen sofort einen Einfluss darauf haben und klein sind für die Benutzer.
- Aufgaben in 90 Tage ausgeführt. Diese erfordern etwas mehr Zeit zum Planen und implementieren, aber Ihre Sicherheitsstatus erheblich verbessert.
- Mehr als 90 Tage. Erstellen Sie diese Verbesserungen in Ihrer ersten 90 Tage Arbeit.

## <a name="see-also"></a>Siehe auch:
- [Unerwarteter Anwendung in meiner Liste Applications](https://docs.microsoft.com/en-us/azure/active-directory/application-access-unexpected-application) führt Administratoren durch verschiedene Aktionen, die sie nach stellen fest, dass unerwartete Programme mit Zugriff auf Daten sind übernehmen möchten.
- [Integrieren von Clientanwendungen mit Azure Active Directory]  (https://docs.microsoft.com/en-us/azure/active-directory/active-directory-apps-permissions-consent) ist eine allgemeine Übersicht über Zustimmung und Berechtigungen.  Beachten Sie insbesondere in den Abschnitt [Übersicht Zustimmung Framework](https://docs.microsoft.com/en-us/azure/active-directory/develop/active-directory-integrating-applications#overview-of-the-consent-framework) .
- [Probleme entwickeln meine Anwendung](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-application-dev-development-content-map) bietet Links zu verschiedenen verwandte Artikeln stimmen.
- [Anwendung und Service principal-Objekten in Azure Active Directory (AD Azure)](https://docs.microsoft.com/en-us/azure/active-directory/develop/active-directory-application-objects) bietet eine Übersicht über die Anwendung und Service principal-Objekte, die auf das Anwendungsmodell Core sind.
- [Zugriff auf apps verwalten](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-managing-access-to-apps) wird eine Übersicht über die Funktionen, die Administratoren zum Verwalten des Benutzerzugriffs auf apps nach.