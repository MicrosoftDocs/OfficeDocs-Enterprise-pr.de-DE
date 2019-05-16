---
title: Office 365-IP-Adress- und -URL-Webdienst
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 5/7/2019
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Adm_O365
ms.reviewer: pandrew
search.appverid:
- MET150
- MOE150
- BCS160
description: Damit Sie Office 365-Netzwerkdatenverkehr besser erkennen und unterscheiden können, veröffentlicht ein neuer Webdienst Office 365-Endpunkte, sodass Sie Änderungen einfacher bewerten, konfigurieren und mit diesen auf dem Laufenden bleiben können. Dieser neue Webdienst ersetzt die herunterladbaren XML-Dateien, die derzeit verfügbar sind.
ms.openlocfilehash: fcef7a6a175b043639275fedc77faaa689f0e7d5
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "34069731"
---
# <a name="office-365-ip-address-and-url-web-service"></a>Office 365-IP-Adresse- und -URL-Webdienst

Damit Sie Office 365-Netzwerkdatenverkehr besser erkennen und unterscheiden können, veröffentlicht ein neuer Webdienst Office 365-Endpunkte, sodass Sie Änderungen einfacher bewerten, konfigurieren und mit diesen auf dem Laufenden bleiben können. Dieser neue Webdienst ersetzt die herunterladbaren XML-Dateien, die derzeit verfügbar sind. Das XML-Format ist ab dem 2. Oktober 2018 nicht mehr verfügbar.

Als Kunde oder Anbieter von Netzwerkperimetergeräten können Sie den neuen REST-basierten Webdienst für die Office 365-IP-Adress- und -FQDN-Einträge verwenden. Sie können auf die Daten direkt in einem Webbrowser über die folgenden URLs zugreifen.

- Verwenden Sie für die neueste Version der Office 365-URLs und -IP-Adressbereiche [https://endpoints.office.com/version](https://endpoints.office.com/version?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).
- Verwenden Sie für die Daten auf der Seite für die Office 365-URLs und -IP-Adressbereiche für Firewalls und Proxyserver [https://endpoints.office.com/endpoints/worldwide](https://endpoints.office.com/endpoints/worldwide?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).
- Um die neuesten Änderungen seit Ende Juli 2018 zu erhalten (Datum, zu dem der Webdienst erstmalig verfügbar war), verwenden Sie [https://endpoints.office.com/changes/worldwide/0000000000](https://endpoints.office.com/changes/worldwide/0000000000?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).

Als Kunde können Sie diesen Webdienst für Folgendes verwenden:

- Aktualisieren Sie Ihre PowerShell-Skripte zum Abrufen von Daten auf Office 365-Endpunkten und zum Ändern der Formatierung für Ihre Netzwerkgeräte.
- Verwenden Sie diese Informationen, um auf Clientcomputern bereitgestellte PAC-Dateien zu aktualisieren.

Als Anbieter von Netzwerkperimetergeräten können Sie diesen Webdienst für Folgendes verwenden:

- Erstellen und testen Sie Gerätesoftware für den Download der Liste für die automatische Konfiguration.
- Suchen Sie die aktuelle Version.
- Rufen Sie die aktuellen Änderungen ab.

> [!NOTE]
> Wenn Sie Azure ExpressRoute für die Verbindung mit Office 365 verwenden, lesen Sie bitte [Azure ExpressRoute for Office 365](https://docs.microsoft.com/office365/enterprise/azure-expressroute), um sich mit den Office 365-Diensten vertraut zu machen, die von Azure ExpressRoute unterstützt werden.  Bitte lesen Sie auch den Artikel [Office 365-URLs und -IP-Adressbereiche](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges?redirectSourcePath=%252farticle%252fOffice-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2), um zu verstehen, welche Netzwerke für Office 365-Apps eine Internetverbindung benötigen. Das wird Ihnen helfen, Ihre Umkreis-Sicherheitsgeräte besser zu konfigurieren.

Weitere Informationen finden Sie unter:

- [Ankündigungsblogbeitrag im Office 365 Tech-Community-Forum](https://techcommunity.microsoft.com/t5/Office-365-Blog/Announcing-Office-365-endpoint-categories-and-Office-365-IP/ba-p/177638)
- [Office 365-Tech-Community-Forum für Fragen zur Verwendung der Webdienste](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking)

## <a name="common-parameters"></a>Allgemeine Parameter

Diese Parameter gelten für sämtliche Webdienstmethoden:

- **format=<JSON | CSV>** - Standardmäßig ist die zurückgegebene Datei als JSON formatiert. Verwenden Sie diesen optionalen Parameter, um die Daten in durch Trennzeichen getrennte Werte (CSV-Format) zurückzubekommen.
- **ClientRequestId=\<guid>** - Eine erforderliche GUID, die Sie für die Clientzuordnung generieren. Sie sollten eine GUID für jeden Computer generieren, der den Webdienst aufruft. Verwenden Sie nicht die in den folgenden Beispielen angezeigten GUIDs, da sie in Zukunft durch den Webdienst blockiert werden könnten. GUID-Format ist _xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx_, wobei x eine hexadezimale Zahl darstellt. Um eine GUID zu generieren, verwenden Sie den PowerShell-Befehl [New-Guid](https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-guid?view=powershell-6).

## <a name="version-web-method"></a>Versionswebmethode

Microsoft aktualisiert die Office 365-IP-Adress- und -FQDN-Einträge am Ende jedes Monats und gelegentlich auch außerhalb dieses Zyklus aufgrund von betrieblichen oder Supportanforderungen. Den Daten für jede veröffentlichte Instanz wird eine Versionsnummer zugewiesen. Mit der Versionswebmethode können Sie die neueste Version für jede Instanz des Office 365-Diensts abrufen. Es wird empfohlen, dass Sie die Version tages- oder stundenweise überprüfen. Neue Versionen sollten zu Beginn jedes Monats zur Verfügung stehen. Manchmal sind aufgrund von Supportanfragen, Sicherheitsbelangen oder anderen betrieblichen Anforderungen neue Versionen während des Monats verfügbar.

Parameter für die Versionswebmethode sind:

- **AllVersions=<true | false>** - Standardmäßig ist die zurückgegebene Version die neueste. Übernehmen Sie diesen optionalen Parameter, um alle veröffentlichten Versionen seit dem ersten Release des Webdiensts anzufordern.
- **Format=<JSON | CSV | RSS>** - Zusätzlich zu den Formaten JSON und CSV unterstützt die Versionswebmethode auch RSS. Diesen optionalen Parameter können Sie zusammen mit dem Parameter _AllVersions=true_ verwenden, um einen RSS-Feed anzufordern, der mit Outlook oder anderen RSS-Diensten verwendet werden kann.
- **Instance=<Weltweit | China | Deutschland | USGovDoD | USGovGCCHigh>** - Dieser optionale Parameter spezifiziert die Instanz, in die die Version zurückgegeben werden soll.  Wenn nicht angegeben, werden alle Instanzen zurückgegeben. Gültige Instanzen sind: Weltweit, China, Deutschland, USGovDoD, USGovGCCHigh.

Die Versionswebmethode ist nicht beschränkt und gibt nie die HTTP-Antwortcodes 429 zurück. Das Ergebnis der Versionswebmethode umfasst keinen Cache-Control-Header, der empfiehlt, die Daten eine Stunde lang zwischenzuspeichern. Das Ergebnis der Versionswebmethode kann ein einzelner Datensatz oder ein Datensatzarray sein. Die Elemente der einzelnen Datensätze sind:

- instance – der kurze Name der Office 365-Serviceinstanz.
- latest – die neueste Version für Endpunkte der angegebenen Instanz.
- versions – eine Liste aller vorherigen Versionen für die angegebene Instanz. Dieses Element ist nur enthalten, wenn der Parameter „AllVersions“ „true“ ist.

Sie können Microsoft Flow verwenden, um E-Mail-Benachrichtigungen über Änderungen an den IP-Adressen und URLs zu erhalten. Weitere Informationen finden Sie unter [Use Microsoft Flow to receive an email for changes to Office 365 IP Addresses and URLs](https://techcommunity.microsoft.com/t5/Office-365-Networking/Use-Microsoft-Flow-to-receive-an-email-for-changes-to-Office-365/m-p/240651).

### <a name="examples"></a>Beispiele:

Anfrage-URI – Beispiel 1: [https://endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)

Dieser URI gibt die aktuelle Version jeder Instanz des Office 365-Diensts zurück. Beispielergebnis:

```json
[
 {
  "instance": "Worldwide",
  "latest": "2018063000"
 },
 {
  "instance": "USGovDoD",
  "latest": "2018063000"
 },
 {
  "instance": "USGovGCCHigh",
  "latest": "2018063000"
 },
 {
  "instance": "China",
  "latest": "2018063000"
 },
 {
  "instance": "Germany",
  "latest": "2018063000"
 }
]
```

> [!IMPORTANT]
> Die GUID für den Parameter „ClientRequestID“ in diesen URIs dient nur als Beispiel. Um die Webdienst-URIs auszuprobieren, erstellen Sie Ihre eigene GUID. Die in den folgenden Beispielen gezeigten GUIDs werden möglicherweise in Zukunft vom Webdienst gesperrt.

Anfrage-URI – Beispiel 2: [https://endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)

Dieser URI gibt die aktuelle Version der angegebenen Instanz des Office 365-Diensts zurück. Beispielergebnis:

```json
{
 "instance": "Worldwide",
 "latest": "2018063000"
}
```

Anfrage-URI – Beispiel 3: [https://endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)

Dieser URI zeigt die Ausgabe im CSV-Format an. Beispielergebnis:

```csv
instance,latest
Worldwide,2018063000
```

Anfrage-URI – Beispiel 4: [https://endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)

Dieser URI zeigt alle vorherigen Versionen an, die für die Dienstinstanz von Office 365 weltweit veröffentlicht wurden. Beispielergebnis:

```json
{
  "instance": "Worldwide",
  "latest": "2018063000",
  "versions": [
    "2018063000",
    "2018062000"
  ]
}
```

RSS-Feed-URI – Beispiel 5: [https://endpoints.office.com/version/worldwide?clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7&allVersions=true&format=RSS](https://endpoints.office.com/version/worldwide?clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7&allVersions=true&format=RSS)

Dieser URI zeigt einen RSS-Feed der veröffentlichten Versionen, die Links zu der Liste der Änderungen für jede Version enthalten. Beispielergebnis:

```xml
<?xml version="1.0" encoding="ISO-8859-1"?>
<rss version="2.0" xmlns:a10="http://www.w3.org/2005/Atom">
<channel>
<link>http://aka.ms/o365ip</link>
<description/>
<language>en-us</language>
<lastBuildDate>Thu, 02 Aug 2018 00:00:00 Z</lastBuildDate>
<item>
<guid isPermaLink="false">2018080200</guid>
<link>https://endpoints.office.com/changes/Worldwide/2018080200?singleVersion&clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7</link> <description>Version 2018080200 includes 2 changes. IPs: 2 added and 0 removed.</description>
<pubDate>Thu, 02 Aug 2018 00:00:00 Z</pubDate>
</item>
```

## <a name="endpoints-web-method"></a>Endpunktwebmethode

Die Endpunktwebmethode gibt alle Datensätze für IP-Adressbereiche und URLs zurück, die den Office 365-Dienst bilden. Während die neuesten Daten von der Endpunktwebmethode für die Netzwerkgerätekonfiguration verwendet werden sollten, können die Daten bis zu 30 Tage nach der Veröffentlichung aufgrund der für Ergänzungen im Vorfeld bereitgestellten Ankündigung zwischengespeichert werden. Wir empfehlen Ihnen, die Endpunktwebmethode nur dann aufzurufen, wenn die Versionswebmethode anzeigt, dass eine neue Version der Daten verfügbar ist.

Parameter für die Endpunktwebmethode sind:

- **ServiceAreas=<Common | Exchange | SharePoint | Skype>** - Eine durch Trennzeichen getrennte Liste von Dienstbereichen. Gültige Elemente sind_Common_, _Exchange_, _SharePoint_ und _Skype_. Da Common-Dienstbereich-Elemente die Voraussetzung für alle anderen Dienstbereiche sind, wir der Webdienst sie mit einschließen. Wenn Sie diesen Parameter nicht miteinschließen, werden alle Dienstbereiche zurückgegeben.
- **TenantName=<tenant_name>** - Ihr Office 365-Mandantenname. Der Webdienst übernimmt Ihren angegebenen Namen und fügt ihn in URL-Teile ein, die den Mandantennamen enthalten. Wenn Sie keinen Mandantennamen angeben, haben diese URL-Teile das Platzhalterzeichen (\*).
- **NoIPv6=<wahr | falsch>** - Stellen Sie dies auf wahr, um IPv6-Adressen von der Ausgabe auszuschließen, wenn Sie zum Beispiel IPv6 nicht in Ihrem Netzwerk verwenden möchten.
- ** Instance=<Weltweit | China | Deutschland | USGovDoD | USGovGCCHigh>** Dieses erforderliche Parameter spezifiziert die Instanz, für die die Endpunkte zurückgegeben werden sollen. Gültige Instanzen sind: _Weltweit_, _China_, _Deutschland_, _USGovDoD_ und _USGovGCCHigh_.

Wenn Sie die Endpunktwebmethode sehr häufig von derselben Client-IP-Adresse abrufen, erhalten Sie möglicherweise den HTTP-Antwortcode 429 (zu viele Anforderungen). Die meisten Benutzer werden dies nie sehen. Wenn Sie diesen Antwortcode erhalten, warten Sie 1 Stunde, bevor Sie Ihre Anforderung wiederholen. Sie sollten die Endpunktwebmethode nur dann aufrufen, wenn die Versionswebmethode anzeigt, dass eine neue Version verfügbar ist.

Das Ergebnis der Endpunktwebmethode ist ein Datensatz-Array, bei dem jeder Datensatz einen Endpunktsatz darstellt. Die Elemente für jeden Datensatz lauten:

- id – die unveränderliche ID-Nummer des Endpunktsatzes.
- ServiceArea – der Servicebereich, zu dem dies gehört: Common, Exchange, SharePoint oder Skype.
- urls – URLs für den Endpunktsatz. Ein JSON-Array von DNS-Datensätzen. Wird ausgelassen, falls leer.
- tcpPorts – TCP-Ports für den Endpunktsatz. Alle Portelemente werden als eine kommagetrennte Liste von Ports oder Portbereichen formatiert, getrennt durch einen Bindestrich (-). Ports gelten für alle IP-Adressen und alle URLs in diesem Endpunktsatz für diese Kategorie. Wird ausgelassen, falls leer.
- udpPorts – UDP-Ports für die IP-Adressbereiche in diesem Endpunktsatz. Wird ausgelassen, falls leer.
- ips – der mit diesem Endpunktsatz verknüpfte IP-Adressbereich (verknüpft mit den aufgeführten TCP- oder UDP-Ports). Ein JSON-Array von IP-Adressbereichen. Wird ausgelassen, falls lehr.
- category – Die Konnektivitätskategorie für den Endpunktsatz. Gültige Werte sind „Optimize“, „Allow“ und „Default“. Wenn Sie die Endpunktdaten verwenden, um nach der Kategorie einer IP-Adresse oder URL zu suchen, kann Ihre Abfrage möglicherweise mehrere Kategorien zurückgeben. Es gibt mehrere Gründe, warum dies passieren kann. In diesen Fällen sollten Sie die Empfehlungen für die Kategorie mit der höchsten Priorität befolgen. Wenn der Endpunkt beispielsweise sowohl unter „Optimize“ als auch unter „Allow“ angezeigt wird, sollten Sie den Anforderungen für „Optimize“ folgen. Erforderlich.
- expressRoute – „true“ oder „false“, wenn dieser Endpunktsatz über ExpressRoute weitergeleitet wird.
- required – „true“, wenn für diesen Endpunktsatz Konnektivität erforderlich ist, damit Office 365 unterstützt wird. „False“, wenn dieser Endpunktsatz optional ist.
- notes – für optionale Endpunkte. Dieser Text beschreibt die Office 365-Funktionalität, die fehlt, wenn der Zugriff auf IP-Adressen oder URLs in diesem Endpunktsatz nicht auf Netzwerkebene möglich ist. Wird ausgelassen, falls leer.

### <a name="examples"></a>Beispiele:

Anfrage-URI – Beispiel 1: [https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)

Dieser URI ruft alle Endpunkte für die Instanz von Office 365 weltweit für alle Workloads ab. Das Beispielergebnis zeigt einen Auszug der Ausgabe an:

```json
[
 {
  "id": 1,
  "serviceArea": "Exchange",
  "serviceAreaDisplayName": "Exchange Online",
  "urls":
   [
    "*.protection.outlook.com"
   ],
  "ips":
   [
    "2a01:111:f403::/48", "23.103.132.0/22", "23.103.136.0/21", "23.103.198.0/23", "23.103.212.0/22", "40.92.0.0/14", "40.107.0.0/17", "40.107.128.0/18", "52.100.0.0/14", "213.199.154.0/24", "213.199.180.128/26", "94.245.120.64/26", "207.46.163.0/24", "65.55.88.0/24", "216.32.180.0/23", "23.103.144.0/20", "65.55.169.0/24", "207.46.100.0/24", "2a01:111:f400:7c00::/54", "157.56.110.0/23", "23.103.200.0/22", "104.47.0.0/17", "2a01:111:f400:fc00::/54", "157.55.234.0/24", "157.56.112.0/24", "52.238.78.88/32"
   ],
  "tcpPorts": "443",
  "expressRoute": true,
  "category": "Allow"
 },
 {
  "id": 2,
  "serviceArea": "Exchange",
  "serviceAreaDisplayName": "Exchange Online",
  "urls":
   [
    "*.mail.protection.outlook.com"
   ],
```

Zusätzliche Endpunktsätze sind in diesem Beispiel nicht enthalten.

Anfrage-URI – Beispiel 2: [https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)

In diesem Beispiel werden nur Endpunkte für die Instanz von Office 365 weltweit für Exchange Online und Abhängigkeiten abgerufen.

Die Ausgabe für Beispiel 2 ähnelt Beispiel 1 mit dem Unterschied, dass die Ergebnisse keine Endpunkte für SharePoint Online oder Skype for Business Online enthalten.

## <a name="changes-web-method"></a>Änderungswebmethode

Die Änderungswebmethode gibt die neuesten Updates zurück, die veröffentlicht wurden. Dies sind in der Regel die im vorherigen Monat vorgenommenen Änderungen an IP-Adressbereichen und URLs. Die wichtigsten zu verarbeitenden Änderungen sind solche, bei denen neue URLs oder IP-Adressen hinzugefügt wurden. Denn wenn eine IP-Adresse nicht einer Firewall Zugriffssteuerungsliste oder eine URL nicht einer Proxyserver-Umgehungsliste hinzugefügt wird, kann dies zu einem Ausfall für Office 365-Benutzer hinter diesem Netzwerkgerät führen. Ungeachtet der betrieblichen Anforderungen werden _Add_-Vorgänge mit einer Frist von 30 Tage hinzugefügt, bevor ein solcher Ausfall auftreten würde.

Die Parameter für die Änderungswebmethode sind:

- **Version=\<YYYYMMDDNN>** Erforderlicher URL-Routenparameter. Dieser Wert sollte die Version sein, die Sie derzeit implementiert haben. Der Webdienst wird die Änderungen seit dieser Version zurückgeben. Das Format ist _JJJJMMTTNN_, wobei _NN_ eine natürliche Zahl ist, die erhöht wird, falls mehrere Versionen am gleichen Tag herausgegeben werden müssen. Dabei steht _00_ für das erste Update an einen bestimmten Tag. Der Webdienst erfordert, dass der _Versions_-Parameter genau 10 Ziffern enthält.

Für die Änderungswebmethode sind die Gebühren auf dieselbe Art und Weise beschränkt wie bei der Endpunktwebmethode. Wenn Sie einen 429-HTTP-Antwortcode erhalten, warten Sie 1 Stunde, bevor Sie Ihre Anforderung wiederholen.

Das Ergebnis der Änderungswebmethode ist ein Datensatz-Array, bei dem jeder Datensatz eine Änderung in einer speziellen Version des Endpunkts darstellt. Die Elemente für jeden Datensatz lauten:

- id – die unveränderliche ID des Änderungsdatensatzes.
- endpointSetId - Die ID des Endpunktgruppendatensatzes, der geändert wird. 
- disposition - Das kann sowohl Ändern, Hinzufügen oder Entfernen sein und beschreibt, was die Veränderung im Endpunktgruppendatensatz bewirkt hat.
- Impact – Nicht alle Änderungen sind für jede Umgebung gleich wichtig. Hier werden die erwarteten Auswirkungen auf eine Netzwerkumkreisumgebung in einem Unternehmen als Ergebnis dieser Änderung beschrieben. Dieses Attribut ist nur in Änderungsdatensätzen der Version **2018112800** und höher enthalten. Optionen für die Auswirkungen sind:
  - AddedIp – Zu Office 365 wurde eine IP-Adresse hinzugefügt, die in diesem Dienst in Kürze live gehen wird. Dies stellt eine Änderung dar, die Sie in einer Firewall oder in einem anderen Netzwerkumkreisgerät der Ebene 3 vornehmen müssen. Wenn Sie diese IP-Adresse nicht hinzufügen, bevor wir mit der Verwendung beginnen, tritt möglicherweise ein Ausfall auf.
  - AddedUrl - Ein URL wurde Office 365 hinzugefügt und wird in Kürze im Dienst live sein. Dies stellt eine Änderung zur Analyse von Netzwerkumkreisgeräten dar, die Sie auf einem Proxyserver oder URL vornehmen müssen. Wenn Sie dies nicht hinzufügen, bevor wir starten, werden Sie möglicherweise einen Ausfall erleben.
  - AddedIpAndUrl – Sowohl eine IP-Adresse als auch eine URL wurden hinzugefügt. Dies stellt eine Änderung, die Sie auf einem Firewallgerät der Ebene 3, auf einem Proxyserver oder auf einem Gerät vornehmen müssen, das URLs analysiert. Wenn Sie diese IP-Adresse nicht hinzufügen, bevor wir mit der Verwendung beginnen, tritt möglicherweise ein Ausfall auf.
  - RemovedIpOrUrl – Mindestens eine IP-Adresse oder URL wurde aus Office 365 entfernt. Sie sollten die Netzwerkendpunkte von Ihren Umkreisgeräten entfernen, hierfür gibt es jedoch keinen Stichtag.
  - ChangedIsExpressRoute – Das Attribut „ExpressRoute Support“ wurde geändert. Wenn Sie ExpressRoute verwenden, müssen Sie je nach Konfiguration möglicherweise entsprechende Maßnahmen ergreifen.
  - MovedIpOrUrl – Eine IP-Adresse oder URL wurde zwischen diesem Endpunktsatz und einem anderen verschoben. Im Allgemeinen ist keine Aktion erforderlich.
  - RemovedDuplicateIpOrUrl – Es wurde eine doppelte IP-Adresse oder URL entfernt, diese ist aber immer noch auf Office 365 veröffentlicht. Im Allgemeinen ist keine Aktion erforderlich.
  - OtherNonPriorityChanges – Es wurde etwas weniger wichtiges als all die anderen Optionen geändert, z. B. ein Notizfeld.
- version – die Version des veröffentlichten Endpunktsatzes, in dem die Änderung eingeführt wurde. Versionsnummern werden im Format _JJJJMMTTNN_ angegeben, wobei NN eine natürliche Zahl ist, die erhöht wird, wenn mehrere Versionen an einem einzigen Tag veröffentlicht werden müssen.
- previous - Eine Unterstruktur, welche vorherige Werte von Änderungselementen auf dem Endpunktsatz angibt. Dies ist bei neu hinzugefügten Endpunktsätzen nicht enthalten. Umfasst _ExpressRoute_, _serviceArea_, _category_, _required_, _tcpPorts_, _udpPorts_ und _notes_.
- current - Eine Unterstruktur, welche aktualisierte Werte von Änderungselementen auf dem Endpunktsatz angibt. Umfasst _ExpressRoute_, _serviceArea_, _category_, _required_, _tcpPorts_, _udpPorts_ und _notes_.
- add – eine Unterstruktur, die Elemente angibt, die zu Endpunktsatzsammlungen hinzugefügt werden sollen. Wird ausgelassen, wenn keine Ergänzungen vorhanden sind.
  - effectiveDate – definiert die Daten, wann die Ergänzungen live im Dienst sind.
  - ips - Elemente, die dem Array _ips_ hinzugefügt werden sollen.
  - urls - Elemente, die zum Array_urls_ hinzugefügt werden sollen.
- remove - eine Unterstruktur, die Elemente angibt, die aus dem Endpunktsatz entfernt werden sollen.  Wird ausgelassen, wenn keine Entfernungen vorhanden sind.
  - ips - Elemente, die aus dem Array _ips_entfernt werden sollen.
  - urls – Elemente, die aus dem Array _urls_ entfernt werden sollen.

### <a name="examples"></a>Beispiele:

Anfrage-URI – Beispiel 1: [https://endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)

Dies fordert alle vorherigen Änderungen an der Dienstinstanz von Office 365 weltweit an. Beispielergebnis:

```json
[
 {
  "id": 424,
  "endpointSetId": 32,
  "disposition": "Change",
  "version": "2018062700",
  "remove":
   {
    "urls":
     [
      "*.api.skype.com", "skypegraph.skype.com"
     ]
   }
 },
 {
  "id": 426,
  "endpointSetId": 31,
  "disposition": "Change",
  "version": "2018062700",
  "add":
   {
    "effectiveDate": "20180609",
    "ips":
     [
      "51.140.203.190/32"
     ]
   },
  "remove":
   {
    "ips":
     [
```

Anfrage-URI – Beispiel 2: [https://endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)

Dies fordert Änderungen seit der angegebenen Version der Instanz von Office 365 weltweite an. Die angegebene Version ist in diesem Fall die neueste. Beispielergebnis:

```json
[
  {
    "id":3,
    "endpointSetId":33,
    "changeDescription":"Removing old IP prefixes",
    "disposition":"Change",
    "version":"2018031301",
    "remove":{
      "ips":["65.55.127.0/24","66.119.157.192/26","66.119.158.0/25",
      "111.221.76.128/25","111.221.77.0/26","207.46.5.0/24"]
    }
  },
  {
    "id":4,
    "endpointSetId":45,
    "changeDescription":"Removing old IP prefixes",
    "disposition":"Change",
    "version":"2018031301",
    "remove":{
      "ips":["13.78.93.8/32","40.113.87.220/32","40.114.149.220/32",
      "40.117.100.83/32","40.118.214.164/32","104.208.31.113/32"]
    }
  }
]
```

## <a name="example-powershell-script"></a>PowerShell-Skript

Hier ist ein PowerShell-Skript, das Sie ausführen können um festzustellen, ob es Aktionen gibt, die Sie für aktualisierte Daten ausführen müssen. Dieses Skript überprüft die Versionsnummer für die Office 365 weltweit Instanz-Endpunkte. Wenn eine Änderung vorhanden ist, lädt es die Endpunkte und Filter für die Endpunkte der Kategorie „Zulassen“ und „Optimieren“ herunter. Es verwendet auch eine eindeutige _ClientRequestId_ für mehrere Aufrufe und speichert die neueste Version in einer temporären Datei. Sie sollten dieses Skript einmal pro Stunde aufrufen, um auf eine Versionsaktualisierung zu prüfen.

```powershell
# webservice root URL
$ws = "https://endpoints.office.com"
# path where client ID and latest version number will be stored
$datapath = $Env:TEMP + "\endpoints_clientid_latestversion.txt"
# fetch client ID and version if data file exists; otherwise create new file
if (Test-Path $datapath) {
    $content = Get-Content $datapath
    $clientRequestId = $content[0]
    $lastVersion = $content[1]
}
else {
    $clientRequestId = [GUID]::NewGuid().Guid
    $lastVersion = "0000000000"
    @($clientRequestId, $lastVersion) | Out-File $datapath
}
# call version method to check the latest version, and pull new data if version number is different
$version = Invoke-RestMethod -Uri ($ws + "/version/Worldwide?clientRequestId=" + $clientRequestId)
if ($version.latest -gt $lastVersion) {
    Write-Host "New version of Office 365 worldwide commercial service instance endpoints detected"

    # write the new version number to the data file
    @($clientRequestId, $version.latest) | Out-File $datapath
    # invoke endpoints method to get the new data
    $endpointSets = Invoke-RestMethod -Uri ($ws + "/endpoints/Worldwide?clientRequestId=" + $clientRequestId)
    # filter results for Allow and Optimize endpoints, and transform these into custom objects with port and category
    $flatUrls = $endpointSets | ForEach-Object {
        $endpointSet = $_
        $urls = $(if ($endpointSet.urls.Count -gt 0) { $endpointSet.urls } else { @() })
        $urlCustomObjects = @()
        if ($endpointSet.category -in ("Allow", "Optimize")) {
            $urlCustomObjects = $urls | ForEach-Object {
                [PSCustomObject]@{
                    category = $endpointSet.category;
                    url      = $_;
                    tcpPorts = $endpointSet.tcpPorts;
                    udpPorts = $endpointSet.udpPorts;
                }
            }
        }
        $urlCustomObjects
    }
    $flatIps = $endpointSets | ForEach-Object {
        $endpointSet = $_
        $ips = $(if ($endpointSet.ips.Count -gt 0) { $endpointSet.ips } else { @() })
        # IPv4 strings have dots while IPv6 strings have colons
        $ip4s = $ips | Where-Object { $_ -like '*.*' }

        $ipCustomObjects = @()
        if ($endpointSet.category -in ("Allow", "Optimize")) {
            $ipCustomObjects = $ip4s | ForEach-Object {
                [PSCustomObject]@{
                    category = $endpointSet.category;
                    ip = $_;
                    tcpPorts = $endpointSet.tcpPorts;
                    udpPorts = $endpointSet.udpPorts;
                }
            }
        }
        $ipCustomObjects
    }
    $flatIp6s = $endpointSets | ForEach-Object {
    $endpointSet = $_
    $ips = $(if ($endpointSet.ips.Count -gt 0) { $endpointSet.ips } else { @() })
    # IPv6 strings have colons while IPv6 strings have dots
    $ip6s = $ips | Where-Object { $_ -like '*:*' }
    $ipCustomObjects = @()
    if ($endpointSet.category -in ("Optimize")) {
        $ipCustomObjects = $ip6s | ForEach-Object {
            [PSCustomObject]@{
                category = $endpointSet.category;
                ip = $_;
                tcpPorts = $endpointSet.tcpPorts;
                udpPorts = $endpointSet.udpPorts;
            }
        }
    }
    $ipCustomObjects
}
    Write-Output "IPv4 Firewall IP Address Ranges"
    ($flatIps.ip | Sort-Object -Unique) -join "," | Out-String
    Write-Output "IPv6 Firewall IP Address Ranges"
    ($flatIp6s.ip | Sort-Object -Unique) -join "," | Out-String
    Write-Output "URLs for Proxy Server"
    ($flatUrls.url | Sort-Object -Unique) -join "," | Out-String
    # TODO Call Send-MailMessage with new endpoints data
}
else {
    Write-Host "Office 365 worldwide commercial service instance endpoints are up-to-date"
}
```

## <a name="example-python-script"></a>Python-Beispielskript

Hier ist ein Python-Skript, das mit Python 3.6.3 unter Windows 10 getestet wurde. Sie können es ausführen, um festzustellen, ob es Aktionen gibt, die Sie für aktualisierte Daten ausführen müssen. Dieses Skript überprüft die Versionsnummer für Endpunkte mit der Instanz von Office 365 weltweit. Wenn eine Änderung vorhanden ist, lädt es die Endpunkte herunter und filtert nach den Endpunkten der Kategorie _Zulassen_ und _Optimieren_. Außerdem verwendet es eine eindeutige ClientRequestId über mehrere Anrufe hinweg und speichert die aktuelle Version in einer temporären Datei. Sie sollten dieses Skript einmal pro Stunde aufrufen, um zu überprüfen, ob ein Versionsupdate vorhanden ist.

```python
import json
import os
import urllib.request
import uuid
# helper to call the webservice and parse the response
def webApiGet(methodName, instanceName, clientRequestId):
    ws = "https://endpoints.office.com"
    requestPath = ws + '/' + methodName + '/' + instanceName + '?clientRequestId=' + clientRequestId
    request = urllib.request.Request(requestPath)
    with urllib.request.urlopen(request) as response:
        return json.loads(response.read().decode())
# path where client ID and latest version number will be stored
datapath = os.environ['TEMP'] + '\endpoints_clientid_latestversion.txt'
# fetch client ID and version if data exists; otherwise create new file
if os.path.exists(datapath):
    with open(datapath, 'r') as fin:
        clientRequestId = fin.readline().strip()
        latestVersion = fin.readline().strip()
else:
    clientRequestId = str(uuid.uuid4())
    latestVersion = '0000000000'
    with open(datapath, 'w') as fout:
        fout.write(clientRequestId + '\n' + latestVersion)
# call version method to check the latest version, and pull new data if version number is different
version = webApiGet('version', 'Worldwide', clientRequestId)
if version['latest'] > latestVersion:
    print('New version of Office 365 worldwide commercial service instance endpoints detected')
    # write the new version number to the data file
    with open(datapath, 'w') as fout:
        fout.write(clientRequestId + '\n' + version['latest'])
    # invoke endpoints method to get the new data
    endpointSets = webApiGet('endpoints', 'Worldwide', clientRequestId)
    # filter results for Allow and Optimize endpoints, and transform these into tuples with port and category
    flatUrls = []
    for endpointSet in endpointSets:
        if endpointSet['category'] in ('Optimize', 'Allow'):
            category = endpointSet['category']
            urls = endpointSet['urls'] if 'urls' in endpointSet else []
            tcpPorts = endpointSet['tcpPorts'] if 'tcpPorts' in endpointSet else ''
            udpPorts = endpointSet['udpPorts'] if 'udpPorts' in endpointSet else ''
            flatUrls.extend([(category, url, tcpPorts, udpPorts) for url in urls])
    flatIps = []
    for endpointSet in endpointSets:
        if endpointSet['category'] in ('Optimize', 'Allow'):
            ips = endpointSet['ips'] if 'ips' in endpointSet else []
            category = endpointSet['category']
            # IPv4 strings have dots while IPv6 strings have colons
            ip4s = [ip for ip in ips if '.' in ip]
            tcpPorts = endpointSet['tcpPorts'] if 'tcpPorts' in endpointSet else ''
            udpPorts = endpointSet['udpPorts'] if 'udpPorts' in endpointSet else ''
            flatIps.extend([(category, ip, tcpPorts, udpPorts) for ip in ip4s])
    print('IPv4 Firewall IP Address Ranges')
    print(','.join(sorted(set([ip for (category, ip, tcpPorts, udpPorts) in flatIps]))))
    print('URLs for Proxy Server')
    print(','.join(sorted(set([url for (category, url, tcpPorts, udpPorts) in flatUrls]))))

    # TODO send mail (e.g. with smtplib/email modules) with new endpoints data
else:
    print('Office 365 worldwide commercial service instance endpoints are up-to-date')
```

## <a name="web-service-interface-versioning"></a>Versionsverwaltung der Webdienstschnittstelle

In der Zukunft sind möglicherweise Updates für die Parameter oder die Ergebnisse für diese Webdienstmethoden erforderlich. Nachdem die allgemein verfügbare Version dieser Webdienste veröffentlicht wurde, bemüht sich Microsoft in angemessener Weise, bedeutende Updates im Hinblick auf den Webdienst im Vorfeld anzukündigen. Wenn Microsoft davon ausgeht, dass für ein Update Änderungen an Clients erforderlich sind, die den Webdienst nutzen, behält Microsoft die vorherige Version (eine Version zurück) des verfügbaren Webdiensts für mindestens zwölf (12) Monate nach der Veröffentlichung der neuen Version bei. Kunden, die während dieses Zeitraums nicht aktualisieren, können möglicherweise nicht mehr auf den Webdienst und die zugehörigen Methoden zugreifen. Kunden müssen sicherstellen, dass Clients des Webdiensts weiterhin ohne Fehler funktionieren, wenn die folgenden Änderungen an der Webdienst-Schnittstellensignatur vorgenommen werden:

- Hinzufügen eines neuen optionalen Parameters zu einer vorhandenen Webmethode, die nicht notwendigerweise von älteren Clients bereitgestellt werden muss und das Ergebnis nicht beeinträchtigt, das ein älterer Client erhält.
- Hinzufügen eines neuen benannten Attributs zu einem der REST-Antwortelemente oder zusätzlicher Spalten zur Antwort-CSV.
- Hinzufügen einer neuen Webmethode unter einem neuen Namen, die nicht von älteren Clients aufgerufen wird.

## <a name="office-365-endpoint-functions-module"></a>Office 365-Endpunkt-Funktionsmodul

Microsoft hostet einen REST-Webdienst, um die neuesten und aktuellen URL für die Office 365-Dienste zu erhalten.  Um den URL als Sammlung verwenden, können Sie dieses Modul mit ein paar hilfreichen Cmdlets verwenden.

### <a name="calling-the-rest-service"></a>REST-Dienst aufrufen

Um dieses Modul zu verwenden, kopieren Sie einfach die Moduldatei [O365EndpointFunctions.psm1](https://github.com/samurai-ka/PS-Module-O365EndpointService/blob/master/O365EndpointFunctions.psm1) auf einen beliebigen Ort auf Ihrer Festplatte und importieren Sie es direkt mit dem folgenden Befehl:

```powershell
    Import-Module O365EndpointFunctions.psm1
```

Nachdem Sie das Modul importiert haben, werden Sie den REST-Dienst aufrufen können. Dies wird die URL als Sammlung zurückgeben, die Sie jetzt direkt in PowerShell verarbeiten können. Sie müssen den Namen Ihres Office 365-Mandanten wie im nachfolgend beschriebenen Befehl eingeben:

```powershell
    Invoke-O365EndpointService -tenantName [Name of your tenant]
```

#### <a name="parameters"></a>Parameter

- **tenantName** - Der Namen Ihres Office 365-Mandanten. Dieser Parameter ist obligatorisch.
- **ForceLatest** - Dieser Wechsel wird die REST-API dazu zwingen, immer die gesamte Liste der neuesten URL zurückzugeben.
- **IPv6** - Dieser Wechsel wird auch die IPv6-Adressen zurückgeben. Standardmäßig wird nur IPv4 zurückgegeben.

### <a name="examples"></a>Beispiele

Die vollständige Liste aller URLs einschließlich IPv6-Adressen zurückgeben.

```powershell
    Invoke-O365EndpointService -tenantName [Name of your tenant] -ForceLatest -IPv6 | Format-Table -AutoSize
```

Nur die IP-Adressen für Exchange-Onlinedienst zurückgeben

```powershell
    Invoke-O365EndpointService -tenantName [Name of your tenant] -ForceLatest | where{($_.serviceArea -eq "Exchange") -and ($_.protocol -eq "ip")}| Format-Table -AutoSize
```

### <a name="exporting-a-proxy-pac-file"></a>Eine Proxy-PAC-Datei exportieren

Dieses Modul können Sie verwenden, um eine Proxy-PAC-Datei zu erstellen. In diesem Beispiel erhalten Sie zuerst die Endpunkte und filtern das Ergebnis, um die URLs auszuwählen. Um exportiert werden zu können, werden diese URLs weitergeleitet.  

```powershell
 Invoke-O365EndpointService -tenantName [Name of your tenant] -ForceLatest | where{($_.Protocol -eq "Url") -and (($_.Category -eq "Optimize") -or ($_.category -eq "Allow"))} | select uri -Unique | Export-O365ProxyPacFile
```

## <a name="related-topics"></a>Verwandte Themen
  
[URLs und IP-Adressbereiche für Office 365](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[Häufig gestellte Fragen zu Office 365-Endpunkten](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)

[Prinzipien von Office 365-Netzwerkverbindungen](office-365-network-connectivity-principles.md)

[Office 365-Netzwerk- und Leistungsoptimierung](network-planning-and-performance.md)

[Netzwerkkonnektivität mit Office 365](network-connectivity.md)
  
[Medienqualität und Netzwerkverbindungsleistung in Skype for Business Online](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[Optimieren Ihres Netzwerks für Skype for Business Online](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43)

[Office 365-Leistungsoptimierung mit Basisplänen und Leistungsverlauf](performance-tuning-using-baselines-and-history.md)
  
[Plan zur Problembehandlung für Office 365](performance-troubleshooting-plan.md)
