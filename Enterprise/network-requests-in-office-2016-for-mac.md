---
title: Netzwerkanfragen 2016 von Office für Mac
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 8/13/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365_Setup
search.appverid: MOM160
ms.assetid: afdae969-4046-44b9-9adb-f1bab216414b
description: 2016 von Office für Mac Applikationen bieten eine systemeigene app-Benutzeroberfläche auf der Mac OS-Plattform. Jede app ist darauf ausgelegt, funktioniert in einer Vielzahl von Szenarien, einschließlich Zustände, wenn kein Netzwerkzugriff verfügbar ist. Bei ein Computer mit einem Netzwerk verbunden ist, werden die Anwendungen automatisch zu einer Reihe von webbasierten Diensten eine erweiterte Funktionalität verbunden. In diesem Whitepaper wird beschrieben, welche Endpunkte und URLs, die Anwendungen versuchen zu erreichen, und die bereitgestellten Dienste. Diese Informationen ist nützlich, wenn die Problembehandlung von Netzwerk-Konfigurationsprobleme und Festlegen einer Richtlinie für die Netzwerk-Proxy-Server. Der Konfigurationsdetails in diesem Artikel sind für die direkte Verwendung der Office 365-URL und die Adressbereiche Artikel zu unterstützen.
ms.openlocfilehash: b94b77a0ff8cd37b0fa1c881ba590853615bfe93
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540975"
---
# <a name="network-requests-in-office-2016-for-mac"></a>Netzwerkanfragen 2016 von Office für Mac

2016 von Office für Mac Applikationen bieten eine systemeigene app-Benutzeroberfläche auf der Mac OS-Plattform. Jede app ist darauf ausgelegt, funktioniert in einer Vielzahl von Szenarien, einschließlich Zustände, wenn kein Netzwerkzugriff verfügbar ist. Bei ein Computer mit einem Netzwerk verbunden ist, werden die Anwendungen automatisch zu einer Reihe von webbasierten Diensten eine erweiterte Funktionalität verbunden. In diesem Whitepaper wird beschrieben, welche Endpunkte und URLs, die Anwendungen versuchen zu erreichen, und die bereitgestellten Dienste. Diese Informationen sind hilfreich, wenn Behandlung von Netzwerkproblemen Konfiguration und Festlegen von Richtlinien für die Netzwerk-Proxy-Server. Die Informationen in diesem Artikel sind für die direkte Verwendung im [Artikel zu Office 365-URL und Adresse Bereiche](urls-and-ip-address-ranges.md)unterstützen die Endpunkte für Computer mit Microsoft Windows enthält.
  
Die meisten der in diesem Artikel wird die Tabellen mit ausführlichen Informationen zu Netzwerk-URLs, Typ und Beschreibung des Dienstes oder Features, die von diesem Endpunkt bereitgestellt. Jedes von Office-apps kann im Dienst und Endpunkt Verwendungsmöglichkeit abweichen. In den folgenden Tabellen sind die folgenden apps definiert:
  
- W: Word
- P: PowerPoint
- X: Excel
- O: outlook
- N: OneNote
   
Der URL-Typ ist wie folgt definiert:
  
- ST: Static - ist die URL in der Clientanwendung codiert.
    
- SS: Semikolons statisch – der URL wird als Teil einer Webseite oder Redirector codiert.
    
- CS: Config Service - wird die URL als Teil der Office-Konfigurationsdienst zurückgegeben.
    
## <a name="office-2016-for-mac-default-configuration"></a>2016 von Office für Mac Standardkonfiguration

 **Installation und updates**
  
Die folgenden Netzwerkendpunkte werden verwendet, um die 2016 Office für Mac-Installationsprogramm von Microsoft Content Delivery Network (CDN) herunterladen.
  
|**URL**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|```https://go.microsoft.com/fwlink/```  <br/> |ST  <br/> |Office 365-Portal Installation Forwardlink Dienst auf dem neuesten Installationspakete.  <br/> |
|```https://officecdn-microsoft-com.akamaized.net/```  <br/> |SS  <br/> |Speicherort der Installationspakete auf dem Content Delivery Network.  <br/> |
|```https://officecdn.microsoft.com/```  <br/> |SS  <br/> |Speicherort der Installationspakete auf dem Content Delivery Network.  <br/> |
|```https://officeci-mauservice.azurewebsites.net/```  <br/> |ST  <br/> |Management Steuerelement Endpunkt für Microsoft AutoUpdate  <br/> |
   
 **Erste app-Start**
  
Beim ersten Starten von Office-app werden die folgenden Netzwerkendpunkte kontaktiert. Diese Endpunkte erweiterten Office-Funktionalität für die Benutzer bereitstellen, und die URLs werden unabhängig davon Lizenztyp (einschließlich Volume License Installationen) kontaktiert.
  
|**URL**|**Apps**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|:-----|
|```https://config.edge.skype.com/```  <br/> |WXPON  <br/> |ST  <br/> |'Flighting'-Konfiguration - ermöglicht Feature-hell nach oben und experimentieren.  <br/> |
|```https://ocos-office365-s2s.msedge.net/```  <br/> |WXPON  <br/> |ST  <br/> |'Flighting' Testen des Netzwerks Konfiguration  <br/> |
|```https://client-office365-tas.msedge.net/```  <br/> |WXPON  <br/> |ST  <br/> |'Flighting' Testen des Netzwerks Konfiguration  <br/> |
|```https://officeclient.microsoft.com/```  <br/> |WXPON  <br/> |ST  <br/> |Office-Konfigurationsdienst - Liste der Endpunkte, die Master.  <br/> |
|```https://nexusrules.officeapps.live.com/```  <br/> |WXPON  <br/> |ST  <br/> |Office – Download der Regeln Telemetrie - informiert den Client über welche Daten und Ereignisse in den Telemetrie-Dienst hoch.  <br/> |
|```https://mobile.pipe.aria.microsoft.com/```  <br/> |N  <br/> |CS  <br/> |Telemetrie OneNote-Dienst  <br/> |
|```https://nexus.officeapps.live.com/```  <br/> |WXPON  <br/> |ST  <br/> |Office-Telemetrie Reporting - "Heartbeart" Hochladen und auf dem Client aufgetretene Fehlerereignisse werden mit dem Dienst Telemetrie hochgeladen.  <br/> |
|```https://templateservice.office.com/```  <br/> |WINDOWS XP  <br/> |CS  <br/> |Office Online-Vorlage-Dienst – ermöglicht es Benutzern online Dokumentvorlagen.  <br/> |
|```https://omextemplates.content.office.net/```  <br/> |WINDOWS XP  <br/> |CS  <br/> |Vorlagen in Office-Downloads – Speicherung von PNG-Bilder im Vorlage.  <br/> |
|```https://store.office.com/```  <br/> |WINDOWS XP  <br/> |CS  <br/> |Konfiguration für Office-apps zu speichern.  <br/> |
|```https://odc.officeapps.live.com/```  <br/> |WXPN  <br/> |CS  <br/> |Office-Dokument Integration Services-Katalog (Liste der Dienste und Endpunkte) und Home Realm Discovery.  <br/> |
|```https://cdn.odc.officeapps.live.com/```  <br/> |WXPON  <br/> |CS  <br/> |Ressourcen für Home Realm Discovery v2 (15.40 und höher)  <br/> |
|```https://officecdn.microsoft.com/```  <br/> |WXPON  <br/> |ST  <br/> |Microsoft AutoUpdate Manifeste - Überprüfungen, um zu überprüfen, ob Updates verfügbar sind  <br/> |
|```https://ajax.aspnetcdn.com/```  <br/> |WXPO  <br/> |SS  <br/> |Microsoft Ajax-JavaScript-Bibliothek  <br/> |
|```https://wikipedia.firstpartyapps.oaspapps.com/```  <br/> |W  <br/> |SS  <br/> |Wikipedia-app für Office-Konfiguration und Ressourcen.  <br/> |
|```https://excelbingmap.firstpartyapps.oaspapps.com/```  <br/> |X  <br/> |SS  <br/> |Bing Map-app für Office-Konfiguration und Ressourcen.  <br/> |
|```https://peoplegraph.firstpartyapps.oaspapps.com/```  <br/> |X  <br/> |SS  <br/> |Personen-Diagramm-app für Office-Konfiguration und Ressourcen.  <br/> |
|```https://www.onenote.com/```  <br/> |N  <br/> |ST  <br/> |Was ist die neue Inhalte für OneNote.  <br/> |
|```https://site-cdn.onenote.net/```  <br/> |N  <br/> |ST  <br/> |Neue Inhalte für OneNote.  <br/> |
|```https://site-cdn.onenote.net/```  <br/> |N  <br/> |SS  <br/> |Was ist die neue Bilder für OneNote.  <br/> |
|```https://acompli.helpshift.com/```  <br/> |O  <br/> |ST  <br/> |Dienst-app-Unterstützung.  <br/> |
|```https://prod-global-autodetect.acompli.net/```  <br/> |O  <br/> |ST  <br/> |E-Mail-Konto Erkennungsdienst.  <br/> |
|```https://autodiscover-s.outlook.com/```  <br/> |WXPO  <br/> |ST  <br/> |Outlook-AutoErmittlung  <br/> |
|```https://outlook.office365.com/```  <br/> |WXPO  <br/> |ST  <br/> |Outlook-Endpunkts für Office 365-Dienst.  <br/> |
|```https://r1.res.office365.com/```  <br/> |O  <br/> |ST  <br/> |Symbole für Outlook-add-ins.  <br/> |
   
> [!NOTE]
> Office-Konfigurationsdienst fungiert als ein Auto-Discovery-Dienst für alle Microsoft Office-Clients und nicht nur für Mac Die Endpunkte in der Antwort zurückgegeben werden halb statische, Änderung sehr selten, aber dennoch möglich sind. 
  
 **Anmeldung**
  
Bei der Anmeldung in einen cloudbasierten Speicher, werden die folgenden Netzwerkendpunkte kontaktiert. Abhängig vom Kontotyp können verschiedene Dienste kontaktiert werden. Zum Beispiel:
  
- **MSA: Microsoft Account** – in der Regel wird für Verbraucher und Verkaufsversion Szenarien verwendet 
    
- **Organisations-ID: Organisation Konto** – in der Regel wird für kommerzielle Szenarien verwendet 
    
|**URL**|**Apps**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|:-----|
|```https://login.windows.net/```  <br/> |WXPON  <br/> |ST  <br/> |Windows-Autorisierungsdienst  <br/> |
|```https://login.microsoftonline.com/```  <br/> |WXPON  <br/> |ST  <br/> |Office 365-Anmeldung-Dienst (OrgID)  <br/> |
|```https://login.live.com/```  <br/> |WXPON  <br/> |ST  <br/> |Microsoft-Konto Anmeldedienst (MSA)  <br/> |
|```https://auth.gfx.ms/```  <br/> |WXPON  <br/> |CS  <br/> |Microsoft-Konto anmelden-Dienst-Hilfsprogramm (MSA)  <br/> |
|```https://secure.aadcdn.microsoftonline-p.com/```  <br/> |WXPON  <br/> |SS  <br/> |Office 365-Anmeldung Branding (OrgID)  <br/> |
|```https://ocws.officeapps.live.com/```  <br/> |WXPN  <br/> |CS  <br/> |Dokument- und Orte Speicher Locator  <br/> |
|```https://roaming.officeapps.live.com/```  <br/> |WXPN  <br/> |CS  <br/> |Die meisten zuletzt Verwendeter Dokument service  <br/> |
   
> [!NOTE]
> Abonnementbasierte und Retail Lizenzen für beide Anmelden aktiviert das Produkt aus, und ermöglicht den Zugriff auf Cloudressourcen wie OneDrive. Für Volume License Installationen, Benutzer werden immer noch aufgefordert, anmelden (standardmäßig), aber das ist nur erforderlich für den Zugriff auf Cloudressourcen, wie das Produkt bereits aktiviert ist. 
  
 **Aktivierung von Produkten**
  
Die folgenden Netzwerkendpunkte anwenden auf Office 365-Abonnement und Einzelhandelslizenz Aktivierungen. Insbesondere gilt dies nicht für Volume License Installationen.
  
|**URL**|**Apps**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|:-----|
|```https://ols.officeapps.live.com/```  <br/> |WXPON  <br/> |CS  <br/> |Office-Lizenzierungsdienst  <br/> |
   
 **Was ist die neue Inhalte**
  
Die folgenden Netzwerkendpunkte gelten nur für Office 365-Abonnement.
  
|**URL**|**Apps**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|:-----|
|```https://contentstorage.osi.office.net/```  <br/> |WXPO  <br/> |SS  <br/> |Was ist die neue JSON Seiteninhalt.  <br/> |
   
 **Recherche**
  
Die folgenden Netzwerkendpunkte gelten für beide Office 365-Abonnement.
  
|**URL**|**Apps**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|:-----|
|```https://entity.osi.office.net/```  <br/> |W  <br/> |CS  <br/> |Interviewer-Webdienst  <br/> |
|```https://cdn.entity.osi.office.net/```  <br/> |W  <br/> |CS  <br/> |Interviewer statischer Inhalt  <br/> |
|```https://www.bing.com/```  <br/> |W  <br/> |CS  <br/> |Interviewer Content-Anbieter  <br/> |
   
 **Intelligente Suche**
  
Die folgenden Netzwerkendpunkte anwenden auf Office 365-Abonnement und Einzelhandel/Volume License Aktivierungen.
  
|**URL**|**Apps**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|:-----|
|```https://uci.officeapps.live.com/```  <br/> |WXPN  <br/> |CS  <br/> |Insights-Webdienst  <br/> |
|```https://ajax.googleapis.com/```  <br/> |WXPN  <br/> |CS  <br/> |JQuery-Bibliothek  <br/> |
|```https://cdnjs.cloudflare.com/```  <br/> |WXPN  <br/> |CS  <br/> |Unterstützung der JavaScript-Bibliothek  <br/> |
|```https://www.bing.com/```  <br/> |WXPN  <br/> |CS  <br/> |Einblicke in die Content-Anbieter  <br/> |
|```https://tse1.mm.bing.net/```  <br/> |WXPN  <br/> |CS  <br/> |Einblicke in die Content-Anbieter  <br/> |
   
 **PowerPoint Designer**
  
Die folgenden Netzwerkendpunkte gelten nur für Office 365-Abonnement.
  
|**URL**|**Apps**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|:-----|
|```https://pptsgs.officeapps.live.com/```  <br/> |P  <br/> |CS  <br/> |PowerPoint-Designer-Webdienst  <br/> |
   
 **PowerPoint-Schnellstartanleitung**
  
Die folgenden Netzwerkendpunkte gelten nur für Office 365-Abonnement.
  
|**URL**|**Apps**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|:-----|
|```https://pptcts.officeapps.live.com/```  <br/> |P  <br/> |CS  <br/> |PowerPoint QuickStarter-Webdienst  <br/> |
   
 **Senden einer Smiley/Stirnrunzeln**
  
Die folgenden Netzwerkendpunkte anwenden auf Office 365-Abonnement und Einzelhandel/Volume License Aktivierungen.
  
|**URL**|**Apps**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|:-----|
|```https://sas.office.microsoft.com/```  <br/> |WXPON  <br/> |CS  <br/> |Senden Sie eine Smiley Service  <br/> |
   
 **wenden Sie sich an den Support,**
  
Die folgenden Netzwerkendpunkte anwenden auf Office 365-Abonnement und Einzelhandel/Volume License Aktivierungen.
  
|**URL**|**Apps**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|:-----|
|```https://powerlift-frontdesk.acompli.net/```  <br/> |O  <br/> |CS  <br/> |Wenden Sie sich an Support-Service  <br/> |
|```https://acompli.helpshift.com/```  <br/> |O  <br/> |CS  <br/> |Dienst-app-Unterstützung  <br/> |
   
 **Speichern als PDF-Datei**
  
Die folgenden Netzwerkendpunkte anwenden auf Office 365-Abonnement und Einzelhandel/Volume License Aktivierungen.
  
|**URL**|**Apps**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|:-----|
|```https://wordcs.officeapps.live.com/```  <br/> |W  <br/> |CS  <br/> |Word-Dokument-Konvertierungsdienst (PDF)  <br/> |
   
 **Office-Apps (auch bekannt als-add-ins)**
  
Die folgenden Netzwerkendpunkte gelten für Office 365-Abonnement und Einzelhandel/Volume License Aktivierungen, wenn Office-App-add-ins vertrauenswürdig sind.
  
|**URL**|**Apps**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|:-----|
|```https://store.office.com/```  <br/> |WXPO  <br/> |CS  <br/> |Office-app Store-Konfiguration  <br/> |
|```https://wikipedia.firstpartyapps.oaspapps.com/```  <br/> |W  <br/> |SS  <br/> |Wikipedia-app-Ressourcen  <br/> |
|```https://excelbingmap.firstpartyapps.oaspapps.com/```  <br/> |X  <br/> |SS  <br/> |Bing Map-app-Ressourcen  <br/> |
|```https://peoplegraph.firstpartyapps.oaspapps.com```  <br/> |X  <br/> |SS  <br/> |Personen-Diagramm-app-Ressourcen  <br/> |
|```https://o15.officeredir.microsoft.com/```  <br/> |WPX  <br/> |SS  <br/> |Office-Umleitung-Dienst  <br/> |
|```https://appsforoffice.microsoft.com/```  <br/> |WINDOWS XP  <br/> |SS  <br/> |Office JavaScript-Bibliotheken  <br/> |
|```https://telemetry.firstpartyapps.oaspapps.com/```  <br/> |WX  <br/> |SS  <br/> |Telemetrie und Reporting Services für Office-apps  <br/> |
|```https://ajax.microsoft.com/```  <br/> |W  <br/> |SS  <br/> |Microsoft Ajax-JavaScript-Bibliothek  <br/> |
|```https://ajax.aspnetcdn.com/```  <br/> |X  <br/> |SS  <br/> |Microsoft Ajax-JavaScript-Bibliothek  <br/> |
|```https://c.microsoft.com/```  <br/> |WPXO  <br/> |SS  <br/> |Office JavaScript-Bibliotheken  <br/> |
|```https://c1.microsoft.com/```  <br/> |WPXO  <br/> |SS  <br/> |Supportressourcen  <br/> |
|```https://cs.microsoft.com/```  <br/> |WPXO  <br/> |SS  <br/> |Supportressourcen  <br/> |
|```https://c.bing.com/```  <br/> |WPXO  <br/> |SS  <br/> |Supportressourcen  <br/> |
|```https://*.cdn.optimizely.com/```  <br/> |WPXO  <br/> |SS  <br/> |JavaScript-Bibliothek  <br/> |
|```https://errors.client.optimizely.com/```  <br/> |WPX  <br/> |SS  <br/> |Fehlerberichterstattung  <br/> |
|```https://*-contentstorage.osi.office.net/```  <br/> |WPXO  <br/> |SS  <br/> |Schriftartressourcen  <br/> |
|```https://nexus.ensighten.com/```  <br/> |WPXO  <br/> |SS  <br/> |Telemetrie-Dienst  <br/> |
|```https://browser.pipe.aria.microsoft.com/```  <br/> |WPXO  <br/> |SS  <br/> |Telemetrie Reporting  <br/> |
|```https://*.vo.msecnd.net/```  <br/> |WPXO  <br/> |SS  <br/> |Objektbibliothek für Microsoft Store  <br/> |
|```https://*.wikipedia.org/```  <br/> |W  <br/> |SS  <br/> |Wikipedia-Seitenressourcen  <br/> |
|```https://upload.wikimedia.org/```  <br/> |W  <br/> |SS  <br/> |Wikipedia-Media-Ressourcen  <br/> |
|```https://wikipedia.firstpartyappssandbox.oappseperate.com/```  <br/> |W  <br/> |SS  <br/> |Wikipedia Sandkasten frame  <br/> |
|```https://*.virtualearth.net/```  <br/> |X  <br/> |SS  <br/> |Zuordnen von Vorlagen  <br/> |
   
 **Sichere Links**
  
Endpunkt des folgenden gilt für 2016 Office-Clientanwendungen.
  
|**URL**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|```https://*.oscs.protection.outlook.com/```  <br/> |CS  <br/> |Microsoft Safe-Verbindungsdienst  <br/> |
   
 **Reporting abstürzen**
  
Der folgenden Endpunkt gilt für alle Office 2016 Applications und Lizenztypen. Wenn ein Prozess unerwartet abstürzt, wird ein Bericht generiert und an die Watson-Dienst gesendet.
  
|**URL**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|```https://watson.microsoft.com/```  <br/> |ST  <br/> |Microsoft-Fehlerberichterstattungsdienst  <br/> |
|```https://officeci.azurewebsites.net/```  <br/> |ST  <br/> |Office Collaborative Insights-Dienst  <br/> |
   
## <a name="options-for-reducing-network-requests-and-traffic"></a>Optionen zum Reduzieren der Netzwerk-Anfragen und Datenverkehr

Die Standardkonfiguration der 2016 Office für Mac bietet die beste benutzerumgebung, sowohl im Hinblick auf die Funktionalität und den Computer auf dem aktuellen Stand zu halten. In einigen Szenarien möchten Sie möglicherweise Applications Kontaktaufnahme Netzwerkendpunkte zu verhindern. In diesem Abschnitt werden die Optionen zur Folge.
  
 ### <a name="disabling-cloud-sign-in-and-office-add-ins"></a>Cloud-Anmeldung und Office-Add-Ins deaktivieren
  
Volume License-Kunden müssen möglicherweise strenge Richtlinien zum Speichern von Dokumenten in einen cloudbasierten Speicher. Die folgende Einstellung pro Anwendung kann MSA/Organisations-ID anmelden deaktivieren und den Zugriff auf Office-Add-ins festgelegt werden.
  
- ```defaults write com.microsoft.Word UseOnlineContent -integer 0```

- ```defaults write com.microsoft.Excel UseOnlineContent -integer 0```

- ```defaults write com.microsoft.Powerpoint UseOnlineContent -integer 0```

Wenn Benutzer versuchen, die Anmeldung-Funktion zugreifen, wird einen Fehler angezeigt, dass eine Netzwerkverbindung nicht vorhanden ist. Da diese Einstellung auch online produktaktivierung blockiert, sollte sie nur für Volume License-Installationen verwendet werden. Verwenden diese Einstellung wird insbesondere Office-Clientanwendungen den Zugriff auf die folgenden Endpunkte verhindern:
  
- ```https://odc.officeapps.live.com```
    
- ```https://*.firstpartyapps.oaspapps.com```
    
- Alle Endpunkte, die in dem Abschnitt 'Anmelden' oben aufgelistet.
    
- Alle Endpunkte, die im Abschnitt "Smart Lookup" aufgeführt.
    
- Alle Endpunkte, die im Abschnitt "Aktivierung" aufgeführt.
    
- Alle Endpunkte, die im Abschnitt "Office-Apps (auch bekannt als-add-ins)" aufgeführt.
    
Um wieder mit vollem Funktionsumfang für den Benutzer arbeiten, legen Sie die Einstellung auf "2" oder zu entfernen.
  
> [!NOTE]
> Diese Einstellung erfordert 2016 Office für Mac Build 15.25 [160726] oder höher. 
  
### <a name="telemetry"></a>Telemetrie
  
2016 von Office für Mac sendet Telemetriedaten an Microsoft in regelmäßigen Abständen. Daten werden an den Endpunkt 'Nexus' hochgeladen. Die Telemetriedaten hilft bei der Bewertung der Integrität und unerwarteten Verhaltensweisen der einzelnen Office-app-Entwicklungsteam. Es gibt zwei Kategorien von Telemetrie:
  
- **Heartbeat** enthält Angaben zu Version und der Lizenz. Diese Daten werden beim Start der app sofort gesendet. 
    
- **Verwendung** enthält Informationen zur Verwendungsweise apps und nicht schwerwiegenden Fehlern. Diese Daten werden alle 60 Minuten gesendet. 
    
Microsoft nimmt Ihre Privatsphäre sehr stark. Informationen zu Microsoft Richtlinien zur Datensammlung [https://privacy.microsoft.com](https://privacy.microsoft.com). Um zu verhindern, dass die Anwendung senden 'Verwendung' Telemetrie kann die Vorgabe **SendAllTelemetryEnabled** angepasst werden. Die Einstellung pro Anwendung ist, und kann über den Mac OS Konfigurationsprofile oder manuell aus Terminal festgelegt werden: 
  
```defaults write com.microsoft.Word SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.Excel SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.Powerpoint SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.Outlook SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.onenote.mac SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.autoupdate2 SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.Office365ServiceV2 SendAllTelemetryEnabled -bool FALSE```

Heartbeat Telemetrie wird immer gesendet und kann nicht deaktiviert werden.
  
### <a name="crash-reporting"></a>Reporting abstürzen
  
Wenn ein schwerwiegender Anwendungsfehler auftritt, die Anwendung unerwartet beendet und Hochladen eines Absturz-Berichts mit dem Dienst "Watson". Der Absturzbericht besteht aus einer-Aufrufliste, die die Liste der Schritte ist die Anwendung zu Absturz verarbeitet wurde. Diese Schritte helfen dem Entwicklungsteam fehlgeschlagene Funktion identisch zu ermitteln und warum.
  
In einigen Fällen werden der Inhalt eines Dokuments zum Absturz die Anwendung führen. Wenn die app das Dokument als Ursache identifiziert wird, wird der Benutzer gefragt, wenn das Dokument zusammen mit der Aufrufliste auch senden werden kann. Benutzer können auf diese Frage eine fundierte Auswahl treffen. IT-Administratoren können strikten Anforderungen über die Übermittlung von Dokumenten und stellen Sie die Entscheidung niemals Dokumente senden im Auftrag des Benutzers. Die folgende Einstellung kann zu verhindern, dass Dokumente gesendet werden und unterdrückt werden Sie aufgefordert werden, den Benutzer festgelegt werden:
  
```defaults write com.microsoft.errorreporting IsAttachFilesEnabled -bool FALSE```

> [!NOTE]
> Wenn **SendAllTelemetryEnabled** auf **FALSE**festgelegt ist, alle stürzt ab, reporting, dass Prozess deaktiviert ist. Zum Aktivieren der Absturz Weitergabe ohne Verwendung Telemetrie senden, kann die folgenden Vorgabe festgelegt werden:```defaults write com.microsoft.errorreporting IsMerpEnabled -bool TRUE``` 
  
### <a name="updates"></a>Updates
  
Microsoft stellt 2016 Office für Mac-Updates in regelmäßigen Abständen (normalerweise einmal im Monat). Wir empfehlen dringend, Benutzern und Computern um sicherzustellen, dass die neuesten Sicherheitspatches Stand IT-Administratoren installiert sind. In Fällen, in der IT-Administratoren eng steuern und Verwalten von Updates Machine möchten, kann die folgenden Vorgabe zum Verhindern des AutoUpdate-Prozesses automatisch erkannt und bietet Produktupdates festgelegt werden:
  
```defaults write com.microsoft.autoupdate2 HowToCheck -string 'Manual'```

### <a name="blocking-requests-with-a-firewallproxy"></a>Blockieren von Anfragen mit einer Firewall-Proxy
  
Wenn Ihre Organisation Blöcke fordert zu URLs über eine Firewall oder der Proxy-Server müssen Sie konfigurieren die in diesem Dokument als entweder zulässig aufgeführten URLs oder blockieren mit 40 X Antwort (403 oder 404) aufgeführt. 40 X Antwort ansetzt, kann die Office-Clientanwendungen, der Fehler beim Zugriff auf die Ressource ordnungsgemäß zu akzeptieren, und bietet eine schnellere Benutzer wünschen, als einfach löschen der Verbindungs, wodurch den Client wiederholt wird.
  
Wenn der Proxyserver Authentifizierung erfordert, wird eine 407 Antwort an den Client zurückgegeben werden soll. Für optimale Leistung stellen Sie sicher, dass Sie Office 2016 Builds 15.27 oder höher, verwenden, wie sie bestimmte Updates für die Arbeit mit NTLM und Kerberos-Servern enthalten sind.
  
  
## <a name="see-also"></a>Siehe auch

[URLs und IP-Adressbereiche von Office 365](urls-and-ip-address-ranges.md)

