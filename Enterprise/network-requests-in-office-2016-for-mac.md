---
title: Netzwerkanforderungen in Office für Mac
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/9/2018
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365_Setup
search.appverid: MOM160
ms.assetid: afdae969-4046-44b9-9adb-f1bab216414b
description: Office für Mac-Anwendungen bieten eine native App-Erfahrung auf der macOS-Plattform. Jede APP ist für eine Vielzahl von Szenarien vorgesehen, einschließlich Status, wenn kein Netzwerkzugriff verfügbar ist. Wenn ein Computer mit einem Netzwerk verbunden ist, stellen die Anwendungen automatisch eine Verbindung zu einer Reihe von webbasierten Diensten her, um die Funktionalität zu erweitern. In diesem Whitepaper werden die Endpunkte und URLs beschrieben, die von den Anwendungen zu erreichen sind, und die bereitgestellten Dienste. Diese Informationen sind nützlich, wenn Sie Netzwerkkonfigurationsprobleme beheben und eine Richtlinie für Netzwerkproxy Server festlegen. Die Details in diesem Artikel sollen den Artikel Office 365 URL and address Ranges beglückwünschen.
ms.openlocfilehash: 0493fcc0954456ed190791b089fe4e0a568e82d7
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "34069655"
---
# <a name="network-requests-in-office-for-mac"></a>Netzwerkanforderungen in Office für Mac

Office für Mac-Anwendungen bieten eine native App-Erfahrung auf der macOS-Plattform. Jede APP ist für eine Vielzahl von Szenarien vorgesehen, einschließlich Status, wenn kein Netzwerkzugriff verfügbar ist. Wenn ein Computer mit einem Netzwerk verbunden ist, stellen die Anwendungen automatisch eine Verbindung zu einer Reihe von webbasierten Diensten her, um die Funktionalität zu erweitern. In den folgenden Informationen wird beschrieben, welche Endpunkte und URLs von den Anwendungen zu erreichen sind und welche Dienste bereitgestellt werden. Diese Informationen sind nützlich, wenn Sie Netzwerkkonfigurationsprobleme beheben und Richtlinien für Netzwerkproxy Server festlegen. Die Details in diesem Artikel sollen den [Artikel Office 365 URL and address Ranges](urls-and-ip-address-ranges.md)ergänzen, der Endpunkte für Computer mit Microsoft Windows enthält. Soweit nicht angegeben, gelten die Informationen in diesem Artikel auch für Office 2019 für Mac und Office 2016 für Mac, die als einmaliger Erwerb aus einem Einzelhandelsgeschäft oder über einen Volumenlizenzvertrag zur Verfügung stehen. 

  
Der größte Teil dieses Artikels besteht aus Tabellen, in denen die Netzwerk-URLs, der Typ und die Beschreibung des von diesem Endpunkt bereitgestellten Diensts oder Features beschrieben werden. Jede Office-App kann sich in ihrer Dienst-und Endpunkt Nutzung unterscheiden. Die folgenden apps sind in den nachfolgenden Tabellen definiert:
  
- W: Word
- P: PowerPoint
- X: Excel
- O: Outlook
- N: OneNote
   
Der URL-Typ ist wie folgt definiert:
  
- St: statisch-die URL ist in der Clientanwendung hart codiert.
    
- SS: Semi-static-die URL wird als Teil einer Webseite oder eines Redirector codiert.
    
- CS: config Service – die URL wird als Teil des Office-Konfigurations Diensts zurückgegeben.

    
## <a name="office-for-mac-default-configuration"></a>Office für Mac-Standardkonfiguration

 **Installation und Updates**
  
Die folgenden Netzwerkendpunkte werden zum Herunterladen des Office für Mac-Installationsprogramms aus dem Microsoft Content Delivery Network (CDN) verwendet.
  
|**URL**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|```https://go.microsoft.com/fwlink/```  <br/> |St  <br/> |Office 365-Installations Portal-Weiterleitungs-Link-Dienst zu den neuesten Installationspaketen.  <br/> |
|```https://officecdn-microsoft-com.akamaized.net/```  <br/> |SS  <br/> |Speicherort der Installationspakete im Content-Zustellungs Netzwerk.  <br/> |
|```https://officecdn.microsoft.com/```  <br/> |SS  <br/> |Speicherort der Installationspakete im Content-Zustellungs Netzwerk.  <br/> |
|```https://officeci-mauservice.azurewebsites.net/```  <br/> |St  <br/> |Verwaltungs Steuerungs Endpunkt für Microsoft AutoUpdate  <br/> |
   
 **Erster App-Start**
  
Die folgenden Netzwerkendpunkte werden beim ersten Start einer Office-App kontaktiert. Diese Endpunkte bieten erweiterte Office-Funktionen für Benutzer, und die URLs werden unabhängig vom Lizenztyp (einschließlich Volumenlizenz Installationen) kontaktiert.
  
|**URL**|**Apps**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|:-----|
|```https://config.edge.skype.com/```  <br/> |WXPON  <br/> |St  <br/> |"Flighting"-Konfiguration – ermöglicht die Anzeige von Funktionen und experimentieren.  <br/> |
|```https://ocos-office365-s2s.msedge.net/```  <br/> |WXPON  <br/> |St  <br/> |"Flighting"-Netzwerk Konfigurations Test  <br/> |
|```https://client-office365-tas.msedge.net/```  <br/> |WXPON  <br/> |St  <br/> |"Flighting"-Netzwerk Konfigurations Test  <br/> |
|```https://officeclient.microsoft.com/```  <br/> |WXPON  <br/> |St  <br/> |Office-Konfigurationsdienst – Master Liste der Dienstendpunkte.  <br/> |
|```https://nexusrules.officeapps.live.com/```  <br/> |WXPON  <br/> |St  <br/> |Office Rules Telemetry Download-informiert den Client darüber, welche Daten und Ereignisse an den Telemetrie-Dienst hochgeladen werden sollen.  <br/> |
|```https://mobile.pipe.aria.microsoft.com/```  <br/> |N  <br/> |CS  <br/> |OneNote-Telemetrie-Dienst  <br/> |
|```https://nexus.officeapps.live.com/```  <br/> |WXPON  <br/> |St  <br/> |Office Telemetry Upload Reporting – "Heartbeart" und Fehlerereignisse, die auf dem Client auftreten, werden in den Telemetrie-Dienst hochgeladen.  <br/> |
|```https://templateservice.office.com/```  <br/> |WXP  <br/> |CS  <br/> |Office Online-Vorlagen Dienst – stellt Benutzern Online-Dokumentvorlagen zur Verfügung.  <br/> |
|```https://omextemplates.content.office.net/```  <br/> |WXP  <br/> |CS  <br/> |Office-Vorlagen-Downloads-Speichern von PNG-Vorlagen Bildern.  <br/> |
|```https://store.office.com/```  <br/> |WXP  <br/> |CS  <br/> |Speichern Sie die Konfiguration für Office-Apps.  <br/> |
|```https://odc.officeapps.live.com/```  <br/> |WXPN  <br/> |CS  <br/> |Office Document Integration Services-Katalog (Liste der Dienste und Endpunkte) und Home Realm Discovery.  <br/> |
|```https://cdn.odc.officeapps.live.com/```  <br/> |WXPON  <br/> |CS  <br/> |Ressourcen für die Home-Realm-Discovery v2 (15,40 und höher)  <br/> |
|```https://officecdn.microsoft.com/```  <br/> |WXPON  <br/> |St  <br/> |Microsoft AutoUpdate-Manifeste-überprüft, ob Updates verfügbar sind  <br/> |
|```https://ajax.aspnetcdn.com/```  <br/> |WXPO  <br/> |SS  <br/> |Microsoft AJAX JavaScript-Bibliothek  <br/> |
|```https://wikipedia.firstpartyapps.oaspapps.com/```  <br/> |W  <br/> |SS  <br/> |Wikipedia-APP für Office-Konfiguration und-Ressourcen.  <br/> |
|```https://excelbingmap.firstpartyapps.oaspapps.com/```  <br/> |X  <br/> |SS  <br/> |Bing Map-App für Office-Konfiguration und-Ressourcen.  <br/> |
|```https://peoplegraph.firstpartyapps.oaspapps.com/```  <br/> |X  <br/> |SS  <br/> |People Graph-App für Office-Konfiguration und-Ressourcen.  <br/> |
|```https://www.onenote.com/```  <br/> |N  <br/> |St  <br/> |Neuer Inhalt für OneNote.  <br/> |
|```https://site-cdn.onenote.net/```  <br/> |N  <br/> |St  <br/> |Neue Inhalte für OneNote.  <br/> |
|```https://site-cdn.onenote.net/```  <br/> |N  <br/> |SS  <br/> |Neuigkeiten für OneNote.  <br/> |
|```https://acompli.helpshift.com/```  <br/> |O  <br/> |St  <br/> |In-App-Support Dienst.  <br/> |
|```https://prod-global-autodetect.acompli.net/```  <br/> |O  <br/> |St  <br/> |E-Mail-Konto Erkennungsdienst.  <br/> |
|```https://autodiscover-s.outlook.com/```  <br/> |WXPO  <br/> |St  <br/> |Outlook-AutoErmittlung  <br/> |
|```https://outlook.office365.com/```  <br/> |WXPO  <br/> |St  <br/> |Outlook-Endpunkt für Office 365-Dienst.  <br/> |
|```https://r1.res.office365.com/```  <br/> |O  <br/> |St  <br/> |Symbole für Outlook-Add-Ins.  <br/> |
   
> [!NOTE]
> Der Office-Konfigurationsdienst fungiert als automatischer Ermittlungsdienst für alle Microsoft Office-Clients, nicht nur für Mac. Die in der Antwort zurückgegebenen Endpunkte sind Semi-statisch in dieser Änderung ist sehr selten, aber immer noch möglich. 
  
 **Anmeldung**
  
Die folgenden Netzwerkendpunkte werden beim Anmelden bei Cloud-basierter Speicherung kontaktiert. Je nach Kontotyp werden möglicherweise verschiedene Dienste kontaktiert. Zum Beispiel:
  
- **MSA: Microsoft-Konto** -normalerweise verwendet für Consumer-und Einzelhandels Szenarien 
    
- **OrgId: organisationskonto** -normalerweise für kommerzielle Szenarien 
    
|**URL**|**Apps**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|:-----|
|```https://login.windows.net/```  <br/> |WXPON  <br/> |St  <br/> |Windows-Autorisierungsdienst  <br/> |
|```https://login.microsoftonline.com/```  <br/> |WXPON  <br/> |St  <br/> |Office 365-Anmeldedienst (OrgId)  <br/> |
|```https://login.live.com/```  <br/> |WXPON  <br/> |St  <br/> |Microsoft-Konto-Anmeldedienst (MSA)  <br/> |
|```https://auth.gfx.ms/```  <br/> |WXPON  <br/> |CS  <br/> |Microsoft-Konto-Anmeldedienst-Helfer (MSA)  <br/> |
|```https://secure.aadcdn.microsoftonline-p.com/```  <br/> |WXPON  <br/> |SS  <br/> |Office 365-Anmelde Branding (OrgId)  <br/> |
|```https://ocws.officeapps.live.com/```  <br/> |WXPN  <br/> |CS  <br/> |Speicher Locator für Dokumente und Orte  <br/> |
|```https://roaming.officeapps.live.com/```  <br/> |WXPN  <br/> |CS  <br/> |Zuletzt verwendeter Dokumentdienst (MRU)  <br/> |
   
> [!NOTE]
> Bei Abonnement basierten und Retail-Lizenzen aktiviert das Anmelden das Produkt und ermöglicht den Zugriff auf Cloud-Ressourcen wie OneDrive. Bei Volumenlizenz Installationen werden Benutzer weiterhin aufgefordert, sich anzumelden (standardmäßig), jedoch nur für den Zugriff auf Cloud-Ressourcen erforderlich, da das Produkt bereits aktiviert ist. 
  
 **Produktaktivierung**
  
Die folgenden Netzwerkendpunkte gelten für Office 365-Abonnement-und Einzelhandelslizenz Aktivierungen. Dies gilt insbesondere nicht für Volumenlizenz Installationen.
  
|**URL**|**Apps**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|:-----|
|```https://ols.officeapps.live.com/```  <br/> |WXPON  <br/> |CS  <br/> |Office-Lizenzierungsdienst  <br/> |
   
 **Neuer Inhalt**
  
Die folgenden Netzwerkendpunkte gelten nur für Office 365-Abonnements.
  
|**URL**|**Apps**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|:-----|
|```https://contentstorage.osi.office.net/```  <br/> |WXPO  <br/> |SS  <br/> |Was ist der neue JSON-Seiteninhalt?  <br/> |
   
 **Recherche**
  
Die folgenden Netzwerkendpunkte gelten nur für Office 365-Abonnements.
  
|**URL**|**Apps**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|:-----|
|```https://entity.osi.office.net/```  <br/> |W  <br/> |CS  <br/> |Researcher-Webdienst  <br/> |
|```https://cdn.entity.osi.office.net/```  <br/> |W  <br/> |CS  <br/> |Statischer Inhalt des researchers  <br/> |
|```https://www.bing.com/```  <br/> |W  <br/> |CS  <br/> |Researcher-Inhaltsanbieter  <br/> |
   
 **Intelligentes Nachschlagen**
  
Die folgenden Netzwerkendpunkte gelten sowohl für Office 365-Abonnement-als auch für Retail/Volume-Lizenz Aktivierungen.
  
|**URL**|**Apps**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|:-----|
|```https://uci.officeapps.live.com/```  <br/> |WXPN  <br/> |CS  <br/> |Insights-Webdienst  <br/> |
|```https://ajax.googleapis.com/```  <br/> |WXPN  <br/> |CS  <br/> |JQuery-Bibliothek  <br/> |
|```https://cdnjs.cloudflare.com/```  <br/> |WXPN  <br/> |CS  <br/> |Unterstützende JavaScript-Bibliothek  <br/> |
|```https://www.bing.com/```  <br/> |WXPN  <br/> |CS  <br/> |Einblicke-Inhaltsanbieter  <br/> |
|```https://tse1.mm.bing.net/```  <br/> |WXPN  <br/> |CS  <br/> |Einblicke-Inhaltsanbieter  <br/> |
   
 **PowerPoint-Designer**
  
Die folgenden Netzwerkendpunkte gelten nur für Office 365-Abonnements.
  
|**URL**|**Apps**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|:-----|
|```https://pptsgs.officeapps.live.com/```  <br/> |P  <br/> |CS  <br/> |PowerPoint-Designer-Webdienst  <br/> |
   
 **PowerPoint-Schnellstarter**
  
Die folgenden Netzwerkendpunkte gelten nur für Office 365-Abonnements.
  
|**URL**|**Apps**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|:-----|
|```https://pptcts.officeapps.live.com/```  <br/> |P  <br/> |CS  <br/> |PowerPoint Quick Starter-Webdienst  <br/> |
   
 **Senden Sie ein Lächeln/Stirnrunzeln**
  
Die folgenden Netzwerkendpunkte gelten sowohl für Office 365-Abonnement-als auch für Retail/Volume-Lizenz Aktivierungen.
  
|**URL**|**Apps**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|:-----|
|```https://sas.office.microsoft.com/```  <br/> |WXPON  <br/> |CS  <br/> |Senden eines smile-Diensts  <br/> |
   
 **Support kontaktieren**
  
Die folgenden Netzwerkendpunkte gelten sowohl für Office 365-Abonnement-als auch für Retail/Volume-Lizenz Aktivierungen.
  
|**URL**|**Apps**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|:-----|
|```https://powerlift-frontdesk.acompli.net/```  <br/> |O  <br/> |CS  <br/> |Kontakt Support-Dienst  <br/> |
|```https://acompli.helpshift.com/```  <br/> |O  <br/> |CS  <br/> |In-App-Support Dienst  <br/> |
   
 **Als PDF speichern**
  
Die folgenden Netzwerkendpunkte gelten sowohl für Office 365-Abonnement-als auch für Retail/Volume-Lizenz Aktivierungen.
  
|**URL**|**Apps**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|:-----|
|```https://wordcs.officeapps.live.com/```  <br/> |W  <br/> |CS  <br/> |Word-Dokumentkonvertierungsdienst (PDF)  <br/> |
   
 **Office-Apps (aka-Add-Ins)**
  
Die folgenden Netzwerkendpunkte gelten sowohl für Office 365-Abonnement-als auch für Retail/Volume-Lizenz Aktivierungen, wenn Office-App-Add-ins vertrauenswürdig sind.
  
|**URL**|**Apps**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|:-----|
|```https://store.office.com/```  <br/> |WXPO  <br/> |CS  <br/> |Konfiguration des Office-APP-Speichers  <br/> |
|```https://wikipedia.firstpartyapps.oaspapps.com/```  <br/> |W  <br/> |SS  <br/> |Wikipedia-APP-Ressourcen  <br/> |
|```https://excelbingmap.firstpartyapps.oaspapps.com/```  <br/> |X  <br/> |SS  <br/> |Bing Map App-Ressourcen  <br/> |
|```https://peoplegraph.firstpartyapps.oaspapps.com```  <br/> |X  <br/> |SS  <br/> |Personen Graph-App-Ressourcen  <br/> |
|```https://o15.officeredir.microsoft.com/```  <br/> |WPX  <br/> |SS  <br/> |Office-Umleitungsdienst  <br/> |
|```https://appsforoffice.microsoft.com/```  <br/> |WXP  <br/> |SS  <br/> |Office-JavaScript-Bibliotheken  <br/> |
|```https://telemetry.firstpartyapps.oaspapps.com/```  <br/> |WX  <br/> |SS  <br/> |Telemetrie und Reporting Service für Office-Apps  <br/> |
|```https://ajax.microsoft.com/```  <br/> |W  <br/> |SS  <br/> |Microsoft AJAX JavaScript-Bibliothek  <br/> |
|```https://ajax.aspnetcdn.com/```  <br/> |X  <br/> |SS  <br/> |Microsoft AJAX JavaScript-Bibliothek  <br/> |
|```https://c.microsoft.com/```  <br/> |WPXO  <br/> |SS  <br/> |Office-JavaScript-Bibliotheken  <br/> |
|```https://c1.microsoft.com/```  <br/> |WPXO  <br/> |SS  <br/> |Support Ressourcen  <br/> |
|```https://cs.microsoft.com/```  <br/> |WPXO  <br/> |SS  <br/> |Support Ressourcen  <br/> |
|```https://c.bing.com/```  <br/> |WPXO  <br/> |SS  <br/> |Support Ressourcen  <br/> |
|```https://*.cdn.optimizely.com/```  <br/> |WPXO  <br/> |SS  <br/> |JavaScript-Bibliothek  <br/> |
|```https://errors.client.optimizely.com/```  <br/> |WPX  <br/> |SS  <br/> |Fehlerberichterstattung  <br/> |
|```https://*-contentstorage.osi.office.net/```  <br/> |WPXO  <br/> |SS  <br/> |Schriftarten Ressourcen  <br/> |
|```https://nexus.ensighten.com/```  <br/> |WPXO  <br/> |SS  <br/> |Telemetrie-Dienst  <br/> |
|```https://browser.pipe.aria.microsoft.com/```  <br/> |WPXO  <br/> |SS  <br/> |Telemetrie-Berichterstellung  <br/> |
|```https://*.vo.msecnd.net/```  <br/> |WPXO  <br/> |SS  <br/> |Microsoft Store-Objektbibliothek  <br/> |
|```https://*.wikipedia.org/```  <br/> |W  <br/> |SS  <br/> |Ressourcen der Wikipedia-Seite  <br/> |
|```https://upload.wikimedia.org/```  <br/> |W  <br/> |SS  <br/> |Wikipedia-Medienressourcen  <br/> |
|```https://wikipedia.firstpartyappssandbox.oappseperate.com/```  <br/> |W  <br/> |SS  <br/> |Wikipedia Sandkasten Frame  <br/> |
|```https://*.virtualearth.net/```  <br/> |X  <br/> |SS  <br/> |Kartenvorlagen  <br/> |
   
 **Sichere Links**
  
Der folgende Netzwerkendpunkt gilt nur für alle Office-Anwendungen für Office 365-Abonnement.
  
|**URL**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|```https://*.oscs.protection.outlook.com/```  <br/> |CS  <br/> |Microsoft Safe Link-Dienst  <br/> |
   
 **Absturzbericht**
  
Der folgende Netzwerkendpunkt gilt für alle Office-Anwendungen sowohl für Office 365-Abonnements als auch für Retail/Volume-Lizenz Aktivierungen. Wenn ein Prozess unerwartet abstürzt, wird ein Bericht generiert und an den Watson-Dienst gesendet.
  
|**URL**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|```https://watson.microsoft.com/```  <br/> |St  <br/> |Microsoft Error Reporting-Dienst  <br/> |
|```https://officeci.azurewebsites.net/```  <br/> |St  <br/> |Office Collaborative Insights-Dienst  <br/> |
   
## <a name="options-for-reducing-network-requests-and-traffic"></a>Optionen zum Reduzieren von Netzwerkanforderungen und Datenverkehr

Die Standardkonfiguration von Office für Mac bietet eine optimale Benutzerfreundlichkeit sowohl im Hinblick auf die Funktionalität als auch auf dem neuesten Stand. In einigen Szenarien möchten Sie möglicherweise verhindern, dass Anwendungen Netzwerkendpunkte kontaktieren. In diesem Abschnitt werden die Optionen erläutert.
  
 ### <a name="disabling-cloud-sign-in-and-office-add-ins"></a>Deaktivieren von Cloud-Anmeldungen und Office-Add-ins
  
Volumenlizenzkunden haben möglicherweise strenge Richtlinien zum Speichern von Dokumenten in Cloud-basiertem Speicher. Die folgende Einstellung pro Anwendung kann festgelegt werden, um die MSA/OrgId-Anmeldung und den Zugriff auf Office-Add-Ins zu deaktivieren.
  
- ```defaults write com.microsoft.Word UseOnlineContent -integer 0```

- ```defaults write com.microsoft.Excel UseOnlineContent -integer 0```

- ```defaults write com.microsoft.Powerpoint UseOnlineContent -integer 0```

Wenn Benutzer versuchen, auf die Anmeldefunktion zuzugreifen, wird ein Fehler angezeigt, dass keine Netzwerkverbindung vorhanden ist. Da diese Einstellung auch die Online Produktaktivierung blockiert, sollte Sie nur für Volumenlizenz Installationen verwendet werden. Insbesondere verhindert die Verwendung dieser Einstellung, dass Office-Anwendungen auf die folgenden Endpunkte zugreifen können:
  
- ```https://odc.officeapps.live.com```
    
- ```https://*.firstpartyapps.oaspapps.com```
    
- Alle im Abschnitt "Anmelden" oben aufgeführten Endpunkte.
    
- Alle im Abschnitt "Smart Lookup" oben aufgeführten Endpunkte.
    
- Alle im Abschnitt "Produktaktivierung" oben aufgeführten Endpunkte.
    
- Alle Endpunkte, die im Abschnitt "Office-Apps (aka-Add-Ins)" oben aufgeführt sind.
    
Wenn Sie die vollständige Funktionalität für den Benutzer wiederherstellen möchten, legen Sie die Einstellung auf "2" fest, oder entfernen Sie Sie.
  
> [!NOTE]
> Diese Einstellung erfordert Office für Mac Build 15,25 [160726] oder höher. 
  
### <a name="telemetry"></a>Telemetrie 
  
Office für Mac sendet in regelmäßigen Abständen Telemetrie-Informationen an Microsoft. Die Daten werden in den Endpunkt von Nexus hochgeladen. Die Telemetrie-Daten unterstützen das Entwicklungsteam bei der Bewertung der Integrität und der unerwarteten Verhaltensweisen jeder Office-App. Es gibt zwei Arten von Telemetrie:
  
- **Heartbeat** enthält Versions-und Lizenzinformationen. Diese Daten werden sofort beim Start der APP gesendet. 
    
- Die **Verwendung** enthält Informationen zur Verwendung von apps und zu nicht schwerwiegenden Fehlern. Diese Daten werden alle 60 Minuten gesendet. 
    
Microsoft nimmt ihren Datenschutz sehr ernst. Informationen zur Datenerfassungs Richtlinie von Microsoft finden Sie [https://privacy.microsoft.com](https://privacy.microsoft.com)unter. Um zu verhindern, dass Anwendungen die Telemetrie "Usage" senden, kann die **SendAllTelemetryEnabled** -Einstellung angepasst werden. Die Präferenz ist pro Anwendung und kann über macOS-Konfigurationsprofile oder manuell von Terminal aus festgelegt werden: 
  
```defaults write com.microsoft.Word SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.Excel SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.Powerpoint SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.Outlook SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.onenote.mac SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.autoupdate2 SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.Office365ServiceV2 SendAllTelemetryEnabled -bool FALSE```

Heartbeat-Telemetrie wird immer gesendet und kann nicht deaktiviert werden.
  
### <a name="crash-reporting"></a>Absturzbericht
  
Wenn ein schwerwiegender Anwendungsfehler auftritt, wird die Anwendung unerwartet beendet und einen Absturzbericht an den Watson-Dienst hochladen. Der Absturzbericht besteht aus einem Call-Stack, bei dem es sich um die Liste der Schritte handelt, die die Anwendung bis zum Absturz ausgeführt hat. Diese Schritte helfen dem Entwicklungsteam, die genaue Funktion zu identifizieren, die fehlgeschlagen ist und warum.
  
In einigen Fällen führt der Inhalt eines Dokuments zu einem Absturz der Anwendung. Wenn die APP das Dokument als Ursache identifiziert, wird der Benutzer gefragt, ob es in Ordnung ist, das Dokument auch zusammen mit dem Aufruf Stapel zu senden. Benutzer können eine fundierte Auswahl für diese Frage treffen. IT-Administratoren haben möglicherweise strenge Anforderungen an die Übermittlung von Dokumenten und treffen die Entscheidung im Namen des Benutzers, nie Dokumente zu senden. Die folgende Einstellung kann festgelegt werden, um zu verhindern, dass Dokumente gesendet werden, und um die Ansage an den Benutzer zu unterdrücken:
  
```defaults write com.microsoft.errorreporting IsAttachFilesEnabled -bool FALSE```

> [!NOTE]
> Wenn **SendAllTelemetryEnabled** auf **false**festgelegt ist, ist alle Absturz Berichterstattung für diesen Prozess deaktiviert. Die folgende Einstellung kann festgelegt werden, um die Absturz Berichterstattung zu aktivieren, ohne die Verwendungs Telemetrie zu senden:```defaults write com.microsoft.errorreporting IsMerpEnabled -bool TRUE``` 
  
### <a name="updates"></a>Updates
  
Microsoft veröffentlicht Office für Mac-Updates in regelmäßigen Abständen (in der Regel einmal im Monat). Wir empfehlen Benutzern und IT-Administratoren nachdrücklich, Computer auf dem neuesten Stand zu halten, um sicherzustellen, dass die neuesten Sicherheitsupdates installiert werden. In Fällen, in denen IT-Administratoren Computer Aktualisierungen genau steuern und verwalten möchten, kann die folgende Einstellung festgelegt werden, um zu verhindern, dass der AutoUpdate-Prozess Produktupdates automatisch ermittelt und anbietet:
  
```defaults write com.microsoft.autoupdate2 HowToCheck -string 'Manual'```

### <a name="blocking-requests-with-a-firewallproxy"></a>Blockieren von Anforderungen mit einer Firewall/einem Proxy
  
Wenn Ihre Organisation Anforderungen an URLs über eine Firewall oder einen Proxy Server blockiert, stellen Sie sicher, dass Sie die in diesem Dokument aufgeführten URLs entweder als zulässig oder als blockiert mit einer 40-d-Antwort (z.b. 403 oder 404) konfigurieren. Eine 40-d-Antwort ermöglicht es den Office-Anwendungen, die Unmöglichkeit des Zugriffs auf die Ressource zu akzeptieren und eine schnellere Benutzererfahrung zu ermöglichen, als einfach die Verbindung zu löschen, was wiederum den Client wiederholen kann.
  
Wenn für Ihren Proxy Server eine Authentifizierung erforderlich ist, wird eine 407-Antwort an den Client zurückgegeben. Stellen Sie sicher, dass Sie Office für Mac Builds 15,27 oder höher verwenden, da Sie bestimmte Fixes für die Arbeit mit NTLM-und Kerberos-Servern aufweisen.
  
  
## <a name="see-also"></a>Siehe auch

[URLs und IP-Adressbereiche von Office 365](urls-and-ip-address-ranges.md)

