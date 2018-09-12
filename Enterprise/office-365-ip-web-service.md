---
title: Office 365-IP-Adress- und -URL-Webdienst
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 9/4/2018
ms.audience: ITPro
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
ms.openlocfilehash: 21222f4c1c2010517bdfe1a425b47c8f4fde8b0e
ms.sourcegitcommit: ca4d3ec34300d7d39f1a42dc6f29a34915de5c87
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/05/2018
ms.locfileid: "23831900"
---
# <a name="office-365-ip-address-and-url-web-service"></a><span data-ttu-id="b19b4-104">**Office 365-IP-Adress- und -URL-Webdienst**</span><span class="sxs-lookup"><span data-stu-id="b19b4-104">**Office 365 IP Address and URL Web service**</span></span>

<span data-ttu-id="b19b4-p102">Damit Sie Office 365-Netzwerkdatenverkehr besser erkennen und unterscheiden können, veröffentlicht ein neuer Webdienst Office 365-Endpunkte, sodass Sie Änderungen einfacher bewerten, konfigurieren und mit diesen auf dem Laufenden bleiben können. Dieser neue Webdienst ersetzt die herunterladbaren XML-Dateien, die derzeit verfügbar sind. Das XML-Format ist ab dem 2. Oktober 2018 nicht mehr verfügbar.</span><span class="sxs-lookup"><span data-stu-id="b19b4-p102">To help you better identify and differentiate Office 365 network traffic, a new web service publishes Office 365 endpoints, making it easier for you to evaluate, configure, and stay up to date with changes. This new web service replaces the XML downloadable files that are currently available. The XML format is planned to be phased out on October 2, 2018.</span></span>

<span data-ttu-id="b19b4-p103">Als Kunde oder Anbieter von Netzwerkperimetergeräten können Sie den neuen REST-basierten Webdienst für die Office 365-IP-Adress- und -FQDN-Einträge verwenden. Sie können auf die Daten direkt in einem Webbrowser über die folgenden URLs zugreifen.</span><span class="sxs-lookup"><span data-stu-id="b19b4-p103">As a customer or a network perimeter device vendor, you can build against the new REST-based web service for the Office 365 IP address and FQDN entries. You can access the data directly in a web browser using these URLs.</span></span>

- <span data-ttu-id="b19b4-110">Verwenden Sie für die neueste Version der Office 365-URLs und -IP-Adressbereiche [https://endpoints.office.com/version](https://endpoints.office.com/version?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span><span class="sxs-lookup"><span data-stu-id="b19b4-110">For the latest version of the Office 365 URLs and IP address ranges, use [https://endpoints.office.com/version](https://endpoints.office.com/version?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span></span>
- <span data-ttu-id="b19b4-111">Verwenden Sie für die Daten auf der Seite für die Office 365-URLs und -IP-Adressbereiche für Firewalls und Proxyserver [https://endpoints.office.com/endpoints/worldwide](https://endpoints.office.com/endpoints/worldwide?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span><span class="sxs-lookup"><span data-stu-id="b19b4-111">For the data on the Office 365 URLs and IP address ranges page for firewalls and proxy servers, use [https://endpoints.office.com/endpoints/worldwide](https://endpoints.office.com/endpoints/worldwide?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span></span>
- <span data-ttu-id="b19b4-112">Um die neuesten Änderungen seit Ende Juli 2018 zu erhalten (Datum, zu dem der Webdienst erstmalig verfügbar war), verwenden Sie [https://endpoints.office.com/changes/worldwide/0000000000](https://endpoints.office.com/changes/worldwide/0000000000?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span><span class="sxs-lookup"><span data-stu-id="b19b4-112">To get all the latest changes since the end of July 2018 when the web service was first available, use [https://endpoints.office.com/changes/worldwide/0000000000](https://endpoints.office.com/changes/worldwide/0000000000?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span></span>

<span data-ttu-id="b19b4-113">Als Kunde können Sie diesen Webdienst für Folgendes verwenden:</span><span class="sxs-lookup"><span data-stu-id="b19b4-113">As a customer, you can use this web service to:</span></span>

- <span data-ttu-id="b19b4-114">Aktualisieren Sie Ihre PowerShell-Skripte zum Abrufen von Daten auf Office 365-Endpunkten und zum Ändern der Formatierung für Ihre Netzwerkgeräte.</span><span class="sxs-lookup"><span data-stu-id="b19b4-114">Update your PowerShell scripts to obtain Office 365 endpoint data and modify any formatting for your networking devices.</span></span>
- <span data-ttu-id="b19b4-115">Verwenden Sie diese Informationen, um auf Clientcomputern bereitgestellte PAC-Dateien zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="b19b4-115">Use this information to update PAC files deployed to client computers.</span></span>

<span data-ttu-id="b19b4-116">Als Anbieter von Netzwerkperimetergeräten können Sie diesen Webdienst für Folgendes verwenden:</span><span class="sxs-lookup"><span data-stu-id="b19b4-116">As a network perimeter device vendor, you can use this web service to:</span></span>

- <span data-ttu-id="b19b4-117">Erstellen und testen Sie Gerätesoftware für den Download der Liste für die automatische Konfiguration.</span><span class="sxs-lookup"><span data-stu-id="b19b4-117">Create and test device software to download the list for automated configuration.</span></span>
- <span data-ttu-id="b19b4-118">Suchen Sie die aktuelle Version.</span><span class="sxs-lookup"><span data-stu-id="b19b4-118">Check for the current version.</span></span>
- <span data-ttu-id="b19b4-119">Rufen Sie die aktuellen Änderungen ab.</span><span class="sxs-lookup"><span data-stu-id="b19b4-119">Get the current changes.</span></span>

<span data-ttu-id="b19b4-120">Weitere Informationen finden Sie unter:</span><span class="sxs-lookup"><span data-stu-id="b19b4-120">For additional information, see IPConfig.</span></span>

- [<span data-ttu-id="b19b4-121">Ankündigungsblogbeitrag im Office 365 Tech-Community-Forum</span><span class="sxs-lookup"><span data-stu-id="b19b4-121">Announcement blog post in the Office 365 Tech Community Forum</span></span>](https://techcommunity.microsoft.com/t5/Office-365-Blog/Announcing-Office-365-endpoint-categories-and-Office-365-IP/ba-p/177638)
- [<span data-ttu-id="b19b4-122">Office 365-Tech-Community-Forum für Fragen zur Verwendung der Webdienste</span><span class="sxs-lookup"><span data-stu-id="b19b4-122">Office 365 Tech Community Forum for questions about use of the web services</span></span>](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking)

## <a name="common-parameters"></a><span data-ttu-id="b19b4-123">**Allgemeine Parameter**</span><span class="sxs-lookup"><span data-stu-id="b19b4-123">**Common parameters**</span></span>

<span data-ttu-id="b19b4-124">Diese Parameter sind für alle Webdienstmethoden gleich:</span><span class="sxs-lookup"><span data-stu-id="b19b4-124">These parameters are common across all the web service methods:</span></span>

- <span data-ttu-id="b19b4-p104">**Format = CSV | JSON** – Abfragezeichenfolgeparameter. Standardmäßig ist das zurückgegebene Datenformat JSON. Fügen Sie diesen optionalen Parameter ein, wenn Sie die Daten im kommagetrennten Format (CSV) zurückgeben möchten.</span><span class="sxs-lookup"><span data-stu-id="b19b4-p104">**format=CSV | JSON** - Query string parameter. By default, the returned data format is JSON. Include this optional parameter to return the data in comma-separated values (CSV) format.</span></span>
- <span data-ttu-id="b19b4-p105">**ClientRequestId** – Abfragezeichenfolgeparameter. Eine erforderliche GUID, die Sie für die Zuordnung von Clients generieren. Sie sollten eine GUID für jeden Computer generieren, der den Webdienst aufruft. Verwenden Sie nicht die GUIDs in den folgenden Beispielen, da sie in Zukunft durch den Webdienst gesperrt sein können. GUID-Format ist _xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx_, wobei x eine hexadezimale Zahl darstellt. Um eine GUID zu generieren, verwenden Sie den PowerShell-Befehl [New-Guid](https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-guid?view=powershell-6).</span><span class="sxs-lookup"><span data-stu-id="b19b4-p105">**ClientRequestId** - Query string parameter. A required GUID that you generate for client association. You should generate a GUID for each machine that calls the web service. Do not use the GUIDs shown in the following examples because they may be blocked by the web service in the future. GUID format is _xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx_, where x represents a hexadecimal number. To generate a GUID, use the [New-Guid](https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-guid?view=powershell-6) PowerShell command.</span></span>

## <a name="version-web-method"></a><span data-ttu-id="b19b4-134">**Versionswebmethode**</span><span class="sxs-lookup"><span data-stu-id="b19b4-134">**Version web method**</span></span>

<span data-ttu-id="b19b4-p106">Microsoft aktualisiert die Office 365-IP-Adress- und -FQDN-Einträge am Ende jedes Monats und gelegentlich auch außerhalb dieses Zyklus aufgrund von betrieblichen oder Supportanforderungen. Den Daten für jede veröffentlichte Instanz wird eine Versionsnummer zugewiesen. Mit der Versionswebmethode können Sie die neueste Version für jede Instanz des Office 365-Diensts abrufen. Es wird empfohlen, dass Sie die Version tages- oder stundenweise überprüfen. Neue Versionen sollten zu Beginn jedes Monats zur Verfügung stehen. Manchmal sind aufgrund von Supportanfragen, Sicherheitsbelangen oder anderen betrieblichen Anforderungen neue Versionen während des Monats verfügbar.</span><span class="sxs-lookup"><span data-stu-id="b19b4-p106">Microsoft updates the Office 365 IP address and FQDN entries at the end of each month and occasionally out of cycle for operational or support requirements. The data for each published instance is assigned a version number. The version web method lets you poll for the latest version for each Office 365 service instance. We recommend you check the version daily, or at the most, hourly. New versions should be expected at the start of each month. Sometimes due to support incident, security, or other operational requirements there will be new versions during the month.</span></span>

<span data-ttu-id="b19b4-141">Es gibt einen Parameter für die Versionswebmethode:</span><span class="sxs-lookup"><span data-stu-id="b19b4-141">There is one parameter for the version web method:</span></span>

- <span data-ttu-id="b19b4-p107">**AllVersions = "true"** – Abfragezeichenfolgeparameter. Standardmäßig ist die zurückgegebene Version die neueste Version. Fügen Sie diesen optionalen Parameter ein, um alle veröffentlichten Versionen anzufordern.</span><span class="sxs-lookup"><span data-stu-id="b19b4-p107">**AllVersions=true** - Query string parameter. By default, the version returned is the latest. Include this optional parameter to request all published versions.</span></span>
- <span data-ttu-id="b19b4-p108">**Format = JSON** | **CSV** | **RSS** – zusätzlich zu den JSON- und CSV-Formaten unterstützt die Versionswebmethode auch RSS. Sie können diese Option zusammen mit dem Parameter „allVersions=true“ verwenden, um einen RSS-Feed anzufordern, der mit Outlook oder anderen RSS-Readern verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="b19b4-p108">**Format=JSON** | **CSV** | **RSS** – In addition to the JSON and CSV formats, the version web method also supports RSS. You can use this along with the allVersions=true parameter to request an RSS feed which can be used with Outlook or other RSS readers.</span></span>
- <span data-ttu-id="b19b4-p109">**Instanz** – Weiterleitungsparameter. Dieser optionale Parameter gibt die Instanz an, für die die Version zurückgegeben werden soll. Wenn nicht angegeben, werden alle Instanzen zurückgegeben. Gültige Instanzen sind: weltweit, China, Deutschland, USGovDoD, USGovGCCHigh.</span><span class="sxs-lookup"><span data-stu-id="b19b4-p109">**Instance** - Route parameter. This optional parameter specifies the instance to return the version for. If omitted, all instances are returned. Valid instances are: Worldwide, China, Germany, USGovDoD, USGovGCCHigh.</span></span>

<span data-ttu-id="b19b4-p110">Das Ergebnis der Versionswebmethode kann ein einzelner Datensatz oder ein Datensatzarray sein. Die Elemente der einzelnen Datensätze sind:</span><span class="sxs-lookup"><span data-stu-id="b19b4-p110">The result from the version web method may be a single record or an array of records. The elements of each record are:</span></span>

- <span data-ttu-id="b19b4-153">instance – der kurze Name der Office 365-Serviceinstanz.</span><span class="sxs-lookup"><span data-stu-id="b19b4-153">instance - The short name of the Office 365 service instance.</span></span>
- <span data-ttu-id="b19b4-154">latest – die neueste Version für Endpunkte der angegebenen Instanz.</span><span class="sxs-lookup"><span data-stu-id="b19b4-154">latest - The latest version for endpoints of the specified instance.</span></span>
- <span data-ttu-id="b19b4-p111">versions – eine Liste aller vorherigen Versionen für die angegebene Instanz. Dieses Element ist nur enthalten, wenn der Parameter „AllVersions“ „true“ ist.</span><span class="sxs-lookup"><span data-stu-id="b19b4-p111">versions - A list of all previous versions for the specified instance. This element is only included if the AllVersions parameter is true.</span></span>

<span data-ttu-id="b19b4-p112">Sie können Microsoft Flow verwenden, um E-Mail-Benachrichtigungen über Änderungen an den IP-Adressen und URLs zu erhalten. Weitere Informationen finden Sie unter [Use Microsoft Flow to receive an email for changes to Office 365 IP Addresses and URLs](https://techcommunity.microsoft.com/t5/Office-365-Networking/Use-Microsoft-Flow-to-receive-an-email-for-changes-to-Office-365/m-p/240651).</span><span class="sxs-lookup"><span data-stu-id="b19b4-p112">You can use Microsoft Flow to get email notifications of changes to the IP Addresses and URLs. See [Use Microsoft Flow to receive an email for changes to Office 365 IP Addresses and URLs](https://techcommunity.microsoft.com/t5/Office-365-Networking/Use-Microsoft-Flow-to-receive-an-email-for-changes-to-Office-365/m-p/240651).</span></span>

### <a name="examples"></a><span data-ttu-id="b19b4-159">**Beispiele:**</span><span class="sxs-lookup"><span data-stu-id="b19b4-159">**Examples:**</span></span>

<span data-ttu-id="b19b4-160">Anfrage-URI – Beispiel 1: [https://endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="b19b4-160">Example 1 request URI: [https://endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="b19b4-p113">Dieser URI gibt die aktuelle Version jeder Instanz des Office 365-Diensts zurück. Beispielergebnis:</span><span class="sxs-lookup"><span data-stu-id="b19b4-p113">This URI returns the latest version of each Office 365 service instance. Example result:</span></span>

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

[!IMPORTANT]
<span data-ttu-id="b19b4-p114">Die GUID für den Parameter „ClientRequestID“ in diesen URIs dient nur als Beispiel. Um die Webdienst-URIs auszuprobieren, erstellen Sie Ihre eigene GUID. Die in den folgenden Beispielen gezeigten GUIDs werden möglicherweise in Zukunft vom Webdienst gesperrt.</span><span class="sxs-lookup"><span data-stu-id="b19b4-p114">The GUID for the ClientRequestID parameter in these URIs are only an example. To try the web service URIs out, generate your own GUID. The GUIDs shown in these examples may be blocked by the web service in the future.</span></span>

<span data-ttu-id="b19b4-166">Anfrage-URI – Beispiel 2: [https://endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="b19b4-166">Example 2 request URI: [https://endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="b19b4-p115">Dieser URI gibt die aktuelle Version der angegebenen Instanz des Office 365-Diensts zurück. Beispielergebnis:</span><span class="sxs-lookup"><span data-stu-id="b19b4-p115">This URI returns the latest version of the specified Office 365 service instance. Example result:</span></span>

```json
{
 "instance": "Worldwide",
 "latest": "2018063000"
}

```

<span data-ttu-id="b19b4-169">Anfrage-URI – Beispiel 3: [https://endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="b19b4-169">Example 3 request URI: [https://endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="b19b4-p116">Dieser URI zeigt die Ausgabe im CSV-Format an. Beispielergebnis:</span><span class="sxs-lookup"><span data-stu-id="b19b4-p116">This URI shows output in CSV format. Example result:</span></span>

```csv
instance,latest
Worldwide,2018063000
```

<span data-ttu-id="b19b4-172">Anfrage-URI – Beispiel 4: [https://endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="b19b4-172">Example 4 request URI: [https://endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="b19b4-p117">Dieser URI zeigt alle vorherigen Versionen an, die für die Dienstinstanz von Office 365 weltweit veröffentlicht wurden. Beispielergebnis:</span><span class="sxs-lookup"><span data-stu-id="b19b4-p117">This URI shows all prior versions that have been published for the Office 365 worldwide service instance. Example result:</span></span>

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

<span data-ttu-id="b19b4-175">RSS-Feed-URI – Beispiel 5: [https://endpoints.office.com/version/worldwide?clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7&allVersions=true&format=RSS](https://endpoints.office.com/version/worldwide?clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7&allVersions=true&format=RSS)</span><span class="sxs-lookup"><span data-stu-id="b19b4-175">Example 5 RSS Feed URI: [https://endpoints.office.com/version/worldwide?clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7&allVersions=true&format=RSS](https://endpoints.office.com/version/worldwide?clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7&allVersions=true&format=RSS)</span></span>

<span data-ttu-id="b19b4-p118">Dieser URI zeigt einen RSS-Feed der veröffentlichten Versionen, die Links zu der Liste der Änderungen für jede Version enthalten. Beispielergebnis:</span><span class="sxs-lookup"><span data-stu-id="b19b4-p118">This URI shows an RSS feed of the published versions that include links to the list of changes for each version. Example result:</span></span>

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
...
```

## <a name="endpoints-web-method"></a><span data-ttu-id="b19b4-178">**Endpunktwebmethode**</span><span class="sxs-lookup"><span data-stu-id="b19b4-178">**Endpoints web method**</span></span>

<span data-ttu-id="b19b4-p119">Die Endpunktwebmethode gibt alle Datensätze für IP-Adressbereiche und URLs wieder, die den Office 365-Dienst bilden. Sie sollten die neuesten Daten der Endpunktwebmethode für die Konfiguration von Netzwerkgeräten verwenden. Die Daten können jedoch bis zu 30 Tage nach der Veröffentlichung aufgrund der im Vorfeld für Ergänzungen bereitgestellten Ankündigung zwischengespeichert werden. Parameter für die Endpunktwebmethode sind:</span><span class="sxs-lookup"><span data-stu-id="b19b4-p119">The endpoints web method returns all records for IP address ranges and URLs that make up the Office 365 service. While the latest data from the endpoints web method should be used for network device configuration, the data can be cached for up to 30 days after it is published due to the advance notice provided for additions. Parameters for the endpoints web method are:</span></span>

- <span data-ttu-id="b19b4-p120">**ServiceAreas** – Abfragezeichenfolgeparameter. Eine kommagetrennte Liste der Dienstbereiche. Gültige Elemente sind Common, Exchange, SharePoint, Skype. Da Common-Dienstbereichselemente eine Voraussetzung für alle anderen Dienstbereiche sind, sind sie immer in den Webdiensten enthalten. Wenn Sie diesen Parameter nicht einfügen, werden alle Dienstbereiche zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="b19b4-p120">**ServiceAreas** - Query string parameter. A comma-separated list of service areas. Valid items are Common,Exchange,SharePoint,Skype. Because Common service area items are a prerequisite for all other service areas, the web service will always include them. If you do not include this parameter, all service areas are returned.</span></span>
- <span data-ttu-id="b19b4-p121">**TenantName** – Abfragezeichenfolgeparameter. Ihr Office 365-Mandantenname. Der Webdienst übernimmt Ihren angegebenen Namen und fügt ihn in Teile von URLs ein, die den Mandantennamen enthalten. Wenn Sie keinen Mandantennamen bereitstellen, enthalten diese Teile der URLs das Platzhalterzeichen (\*).</span><span class="sxs-lookup"><span data-stu-id="b19b4-p121">**TenantName** - Query string parameter. Your Office 365 tenant name. The web service takes your provided name and inserts it in parts of URLs that include the tenant name. If you don't provide a tenant name, those parts of URLs have the wildcard character (\*).</span></span>
- <span data-ttu-id="b19b4-p122">**NoIPv6** – Abfragezeichenfolgeparameter. Legen Sie diese Option auf „true“ fest, um IPv6-Adressen von der Ausgabe auszuschließen, z. B. wenn Sie iPv6 in Ihrem Netzwerk nicht verwenden.</span><span class="sxs-lookup"><span data-stu-id="b19b4-p122">**NoIPv6** - Query string parameter. Set this to true to exclude IPv6 addresses from the output, for example, if you don't use IPv6 in your network.</span></span>
- <span data-ttu-id="b19b4-p123">**Instanz** – Weiterleitungsparameter. Dieser erforderliche Parameter gibt die Instanz an, für die die Endpunkte zurückgegeben werden sollen. Gültige Instanzen sind: weltweit, China, Deutschland, USGovDoD, USGovGCCHigh.</span><span class="sxs-lookup"><span data-stu-id="b19b4-p123">**Instance** - Route parameter. This required parameter specifies the instance to return the endpoints for. Valid instances are: Worldwide, China, Germany, USGovDoD, USGovGCCHigh.</span></span>

<span data-ttu-id="b19b4-p124">Das Ergebnis der Endpunktwebmethode ist ein Datensatz-Array, bei dem jeder Datensatz einen Endpunktsatz darstellt. Die Elemente für jeden Datensatz lauten:</span><span class="sxs-lookup"><span data-stu-id="b19b4-p124">The result from the endpoints web method is an array of records with each record representing an endpoint set. The elements for each record are:</span></span>

- <span data-ttu-id="b19b4-198">id – die unveränderliche ID-Nummer des Endpunktsatzes.</span><span class="sxs-lookup"><span data-stu-id="b19b4-198">id - The immutable id number of the endpoint set.</span></span>
- <span data-ttu-id="b19b4-199">ServiceArea – der Servicebereich, zu dem dies gehört: Common, Exchange, SharePoint oder Skype.</span><span class="sxs-lookup"><span data-stu-id="b19b4-199">serviceArea - The service area that this is part of: Common, Exchange, SharePoint, or Skype.</span></span>
- <span data-ttu-id="b19b4-p125">urls – URLs für den Endpunktsatz. Ein JSON-Array von DNS-Datensätzen. Wird ausgelassen, falls leer.</span><span class="sxs-lookup"><span data-stu-id="b19b4-p125">urls - URLs for the endpoint set. A JSON array of DNS records. Omitted if blank.</span></span>
- <span data-ttu-id="b19b4-p126">tcpPorts – TCP-Ports für den Endpunktsatz. Alle Portelemente werden als eine kommagetrennte Liste von Ports oder Portbereichen formatiert, getrennt durch einen Bindestrich (-). Ports gelten für alle IP-Adressen und alle URLs in diesem Endpunktsatz für diese Kategorie. Wird ausgelassen, falls leer.</span><span class="sxs-lookup"><span data-stu-id="b19b4-p126">tcpPorts - TCP ports for the endpoint set. All ports elements are formatted as a comma-separated list of ports or port ranges separated by a dash character (-). Ports apply to all IP addresses and all URLs in that endpoint set for that category. Omitted if blank.</span></span>
- <span data-ttu-id="b19b4-p127">udpPorts – UDP-Ports für die IP-Adressbereiche in diesem Endpunktsatz. Wird ausgelassen, falls leer.</span><span class="sxs-lookup"><span data-stu-id="b19b4-p127">udpPorts - UDP ports for the IP address ranges in this endpoint set. Omitted if blank.</span></span>
- <span data-ttu-id="b19b4-p128">ips – der mit diesem Endpunktsatz verknüpfte IP-Adressbereich (verknüpft mit den aufgeführten TCP- oder UDP-Ports). Ein JSON-Array von IP-Adressbereichen. Wird ausgelassen, falls lehr.</span><span class="sxs-lookup"><span data-stu-id="b19b4-p128">ips - The IP address ranges associated with this endpoint set as associated with the listed TCP or UDP ports. A JSON array of IP Address ranges. Omitted if blank.</span></span>
- <span data-ttu-id="b19b4-p129">category – die Konnektivitätskategorie für den Endpunktsatz. Gültige Werte sind „Optimieren“, „Zulassen“ und „Standard“. Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="b19b4-p129">category - The connectivity category for the endpoint set. Valid values are Optimize, Allow, and Default. Required.</span></span>
- <span data-ttu-id="b19b4-215">expressRoute – „true“ oder „false“, wenn dieser Endpunktsatz über ExpressRoute weitergeleitet wird.</span><span class="sxs-lookup"><span data-stu-id="b19b4-215">expressRoute - True or False if this endpoint set is routed over ExpressRoute.</span></span>
- <span data-ttu-id="b19b4-p130">required – „true“, wenn für diesen Endpunktsatz Konnektivität erforderlich ist, damit Office 365 unterstützt wird. „False“, wenn dieser Endpunktsatz optional ist.</span><span class="sxs-lookup"><span data-stu-id="b19b4-p130">required - True if this endpoint set is required to have connectivity for Office 365 to be supported. False if this endpoint set is optional.</span></span>
- <span data-ttu-id="b19b4-p131">notes – für optionale Endpunkte. Dieser Text beschreibt die Office 365-Funktionalität, die fehlt, wenn der Zugriff auf IP-Adressen oder URLs in diesem Endpunktsatz nicht auf Netzwerkebene möglich ist. Wird ausgelassen, falls leer.</span><span class="sxs-lookup"><span data-stu-id="b19b4-p131">notes - For optional endpoints, this text describes Office 365 functionality that will be missing if IP addresses or URLs in this endpoint set cannot be accessed at the network layer. Omitted if blank.</span></span>

### <a name="examples"></a><span data-ttu-id="b19b4-220">Beispiele:</span><span class="sxs-lookup"><span data-stu-id="b19b4-220">Examples:</span></span>

<span data-ttu-id="b19b4-221">Anfrage-URI – Beispiel 1: [https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="b19b4-221">Example 1 request URI: [https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="b19b4-p132">Dieser URI ruft alle Endpunkte für die Instanz von Office 365 weltweit für alle Workloads ab. Das Beispielergebnis zeigt einen Auszug der Ausgabe an:</span><span class="sxs-lookup"><span data-stu-id="b19b4-p132">This URI obtains all endpoints for the Office 365 worldwide instance for all workloads. Example result showing an excerpt of the output:</span></span>

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
...
```

<span data-ttu-id="b19b4-224">Zusätzliche Endpunktsätze sind in diesem Beispiel nicht enthalten.</span><span class="sxs-lookup"><span data-stu-id="b19b4-224">Additional endpoint sets are not included in this example.</span></span>

<span data-ttu-id="b19b4-225">Anfrage-URI – Beispiel 2: [https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="b19b4-225">Example 2 request URI: [https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="b19b4-226">In diesem Beispiel werden nur Endpunkte für die Instanz von Office 365 weltweit für Exchange Online und Abhängigkeiten abgerufen.</span><span class="sxs-lookup"><span data-stu-id="b19b4-226">This example obtains endpoints for the Office 365 Worldwide instance for Exchange Online and dependencies only.</span></span>

<span data-ttu-id="b19b4-227">Die Ausgabe für Beispiel 2 ähnelt Beispiel 1 mit dem Unterschied, dass die Ergebnisse keine Endpunkte für SharePoint Online oder Skype for Business Online enthalten.</span><span class="sxs-lookup"><span data-stu-id="b19b4-227">The output for example 2 is similar to example 1 except that the results will not include endpoints for SharePoint Online or Skype for Business Online.</span></span>

## <a name="changes-web-method"></a><span data-ttu-id="b19b4-228">Änderungswebmethode</span><span class="sxs-lookup"><span data-stu-id="b19b4-228">Changes web method</span></span>

<span data-ttu-id="b19b4-p133">Die Änderungswebmethode gibt die neuesten Updates zurück, die veröffentlicht wurden. Dies sind in der Regel die im vorherigen Monat vorgenommenen Änderungen an IP-Adressbereichen und URLs. Die wichtigsten zu verarbeitenden Änderungen sind solche, bei denen neue URLs oder IP-Adressen hinzugefügt wurden. Denn wenn eine IP-Adresse nicht einer Firewall Zugriffssteuerungsliste oder eine URL nicht einer Proxyserver-Umgehungsliste hinzugefügt wird, kann dies zu einem Ausfall für Office 365-Benutzer hinter diesem Netzwerkgerät führen. Ungeachtet der betrieblichen Anforderungen werden _Add_-Vorgänge mit einer Frist von 30 Tage hinzugefügt, bevor ein solcher Ausfall auftreten würde.</span><span class="sxs-lookup"><span data-stu-id="b19b4-p133">The changes web method returns the most recent updates that have been published. This is typically the previous month's changes to IP address ranges and URLs. The most critical changes to be processed are when new URLs or IP Addresses are added since failing to add an IP Address to a firewall access control list, or a URL to a proxy server bypass list can cause an outage for Office 365 users behind that network device. Notwithstanding operational requirements, _Add_ operations are added with 30 days' notice before such an outage would occur.</span></span>

<span data-ttu-id="b19b4-233">Die Parameter für die Änderungswebmethode sind:</span><span class="sxs-lookup"><span data-stu-id="b19b4-233">The parameter for the changes web method is:</span></span>

- <span data-ttu-id="b19b4-p134">**Version** – erforderlicher URL-Weiterleitungsparameter. Die Version, die Sie derzeit implementiert haben, und Sie möchten die Änderungen seit dieser Version anzeigen. Das Format ist _JJJJMMDDNN_.</span><span class="sxs-lookup"><span data-stu-id="b19b4-p134">**Version** - Required URL route parameter. The version that you have currently implemented, and you want to see the changes since that version. The format is _YYYYMMDDNN_.</span></span>

<span data-ttu-id="b19b4-p135">Das Ergebnis der Änderungswebmethode ist ein Datensatz-Array, bei dem jeder Datensatz eine Änderung in einer speziellen Version des Endpunkts darstellt. Die Elemente für jeden Datensatz lauten:</span><span class="sxs-lookup"><span data-stu-id="b19b4-p135">The result from the changes web method is an array of records with each record representing a change in a specific version of the endpoints. The elements for each record are:</span></span>

- <span data-ttu-id="b19b4-239">id – die unveränderliche ID des Änderungsdatensatzes.</span><span class="sxs-lookup"><span data-stu-id="b19b4-239">id - The immutable id of the change record.</span></span>
- <span data-ttu-id="b19b4-p136">endpointSetId – die ID des Endpunktsatz-Datensatzes, der geändert wird. Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="b19b4-p136">endpointSetId - The ID of the endpoint set record that is changed. Required.</span></span>
- <span data-ttu-id="b19b4-p137">disposition – entweder Änderung, Hinzufügen oder Entfernen. Beschreibt, welche Auswirkungen die Änderung auf den Endpunktsatz-Datensatz hatte. Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="b19b4-p137">disposition - This can be either of change, add, or remove and describes what the change did to the endpoint set record. Required.</span></span>
- <span data-ttu-id="b19b4-p138">version – die Version des veröffentlichten Endpunktsatzes, in dem die Änderung eingeführt wurde. Versionsnummern werden im Format _JJJJMMTTNN_ angegeben, wobei NN eine natürliche Zahl ist, die erhöht wird, wenn mehrere Versionen an einem einzigen Tag veröffentlicht werden müssen.</span><span class="sxs-lookup"><span data-stu-id="b19b4-p138">version - The version of the published endpoint set in which the change was introduced. Version numbers are of the format _YYYYMMDDNN_, where NN is a natural number incremented if there are multiple versions required to be published on a single day.</span></span>
- <span data-ttu-id="b19b4-p139">previous – eine Unterstruktur, die vorherige Werte geänderter Elemente auf dem Endpunktsatz angibt. Diese ist nicht für neu hinzugefügte Endpunktsätze enthalten. Enthält tcpPorts, udpPorts, ExpressRoute, Kategorie, erforderlich, Notizen.</span><span class="sxs-lookup"><span data-stu-id="b19b4-p139">previous - A substructure detailing previous values of changed elements on the endpoint set. This will not be included for newly added endpoint sets. Includes tcpPorts, udpPorts, ExpressRoute, category, required, notes.</span></span>
- <span data-ttu-id="b19b4-p140">current – eine Unterstruktur, die aktualisierte Werte geänderter Elemente auf dem Endpunktsatz angibt. Enthält tcpPorts, udpPorts, ExpressRoute, Kategorie, erforderlich, Notizen.</span><span class="sxs-lookup"><span data-stu-id="b19b4-p140">current - A substructure detailing updated values of changes elements on the endpoint set. Includes tcpPorts, udpPorts, ExpressRoute, category, required, notes.</span></span>
- <span data-ttu-id="b19b4-p141">add – eine Unterstruktur, die Elemente angibt, die zu Endpunktsatzsammlungen hinzugefügt werden sollen. Wird ausgelassen, wenn keine Ergänzungen vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="b19b4-p141">add - A substructure detailing items to be added to endpoint set collections. Omitted if there are no additions.</span></span>
  - <span data-ttu-id="b19b4-253">effectiveDate – definiert die Daten, wann die Ergänzungen live im Dienst sind.</span><span class="sxs-lookup"><span data-stu-id="b19b4-253">effectiveDate - Defines the data when the additions will be live in the service.</span></span>
  - <span data-ttu-id="b19b4-254">ips – Elemente, die zum ips-Array hinzugefügt werden sollen.</span><span class="sxs-lookup"><span data-stu-id="b19b4-254">ips - Items to be added to the ips array.</span></span>
  - <span data-ttu-id="b19b4-255">urls – Elemente, die zum urls-Array hinzugefügt werden sollen.</span><span class="sxs-lookup"><span data-stu-id="b19b4-255">urls- Items to be added to the urls array.</span></span>
- <span data-ttu-id="b19b4-p142">remove – eine Unterstruktur, die Elemente angibt, die aus dem Endpunktsatz entfernt werden sollen. Wird ausgelassen, wenn keine Entfernungen vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="b19b4-p142">remove - A substructure detailing items to be removed from the endpoint set. Omitted if there are no removals.</span></span>
  - <span data-ttu-id="b19b4-258">ips – Elemente, die aus dem ips-Array entfernt werden sollen.</span><span class="sxs-lookup"><span data-stu-id="b19b4-258">ips - Items to be removed from the ips array.</span></span>
  - <span data-ttu-id="b19b4-259">urls – Elemente, die aus dem urls-Array entfernt werden sollen.</span><span class="sxs-lookup"><span data-stu-id="b19b4-259">urls- Items to be removed from the urls array.</span></span>

### <a name="examples"></a><span data-ttu-id="b19b4-260">**Beispiele:**</span><span class="sxs-lookup"><span data-stu-id="b19b4-260">**Examples:**</span></span>

<span data-ttu-id="b19b4-261">Anfrage-URI – Beispiel 1: [https://endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="b19b4-261">Example 1 request URI: [https://endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="b19b4-p143">Dies fordert alle vorherigen Änderungen an der Dienstinstanz von Office 365 weltweit an. Beispielergebnis:</span><span class="sxs-lookup"><span data-stu-id="b19b4-p143">This requests all previous changes to the Office 365 worldwide service instance. Example result:</span></span>

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
...
```

<span data-ttu-id="b19b4-264">Anfrage-URI – Beispiel 2: [https://endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="b19b4-264">Example 2 request URI: [https://endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="b19b4-p144">Dies fordert Änderungen seit der angegebenen Version der Instanz von Office 365 weltweite an. Die angegebene Version ist in diesem Fall die neueste. Beispielergebnis:</span><span class="sxs-lookup"><span data-stu-id="b19b4-p144">This requests changes since the specified version to the Office 365 Worldwide instance. In this case, the version specified is the latest. Example result:</span></span>

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

## <a name="example-powershell-script"></a><span data-ttu-id="b19b4-268">**PowerShell-Beispielskript**</span><span class="sxs-lookup"><span data-stu-id="b19b4-268">**Example PowerShell Script**</span></span>

<span data-ttu-id="b19b4-p145">Hier ist ein PowerShell-Skript, das Sie ausführen können, um festzustellen, ob es Aktionen gibt, die Sie für aktualisierte Daten ausführen müssen. Dieses Skript überprüft die Versionsnummer für Endpunkte mit der Instanz von Office 365 weltweit. Wenn eine Änderung vorhanden ist, lädt es die Endpunkte herunter und filtert nach den Endpunkten der Kategorie &quot;Zulassen&quot; und &quot;Optimieren&quot;. Außerdem verwendet es eine eindeutige ClientRequestId über mehrere Anrufe hinweg und speichert die aktuelle Version in einer temporären Datei. Sie sollten dieses Skript einmal pro Stunde aufrufen, um zu überprüfen, ob ein Versionsupdate vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="b19b4-p145">Here is a PowerShell script that you can run to see if there are actions you need to take for updated data. This script checks the version number for the Office 365 Worldwide instance endpoints. When there is a change, it downloads the endpoints and filters for the &quot;Allow&quot; and &quot;Optimize&quot; category endpoints. It also uses a unique ClientRequestId across multiple calls and saves the latest version found in a temporary file. You should call this script once an hour to check for a version update.</span></span>

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
    Write-Output "IPv4 Firewall IP Address Ranges"
    ($flatIps.ip | Sort-Object -Unique) -join "," | Out-String
    Write-Output "URLs for Proxy Server"
    ($flatUrls.url | Sort-Object -Unique) -join "," | Out-String
    # TODO Call Send-MailMessage with new endpoints data
}
else {
    Write-Host "Office 365 worldwide commercial service instance endpoints are up-to-date"
}
```

## <a name="example-python-script"></a><span data-ttu-id="b19b4-274">**Python-Beispielskript**</span><span class="sxs-lookup"><span data-stu-id="b19b4-274">**Example Python Script**</span></span>

<span data-ttu-id="b19b4-p146">Hier ist ein Python-Skript, das mit Python 3.6.3 unter Windows 10 getestet wurde. Sie können es ausführen, um festzustellen, ob es Aktionen gibt, die Sie für aktualisierte Daten ausführen müssen. Dieses Skript überprüft die Versionsnummer für Endpunkte mit der Instanz von Office 365 weltweit. Wenn eine Änderung vorhanden ist, lädt es die Endpunkte herunter und filtert nach den Endpunkten der Kategorie _Zulassen_ und _Optimieren_. Außerdem verwendet es eine eindeutige ClientRequestId über mehrere Anrufe hinweg und speichert die aktuelle Version in einer temporären Datei. Sie sollten dieses Skript einmal pro Stunde aufrufen, um zu überprüfen, ob ein Versionsupdate vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="b19b4-p146">Here is a Python script, tested with Python 3.6.3 on Windows 10, that you can run to see if there are actions you need to take for updated data. This script checks the version number for the Office 365 Worldwide instance endpoints. When there is a change, it downloads the endpoints and filters for the _Allow_ and _Optimize_ category endpoints. It also uses a unique ClientRequestId across multiple calls and saves the latest version found in a temporary file. You should call this script once an hour to check for a version update.</span></span>

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

## <a name="web-service-interface-versioning"></a><span data-ttu-id="b19b4-280">**Versionsverwaltung der Webdienstschnittstelle**</span><span class="sxs-lookup"><span data-stu-id="b19b4-280">**Web Service interface versioning**</span></span>

<span data-ttu-id="b19b4-p147">In der Zukunft sind möglicherweise Updates für die Parameter oder die Ergebnisse für diese Webdienstmethoden erforderlich. Nachdem die allgemein verfügbare Version dieser Webdienste veröffentlicht wurde, bemüht sich Microsoft in angemessener Weise, bedeutende Updates im Hinblick auf den Webdienst im Vorfeld anzukündigen. Wenn Microsoft davon ausgeht, dass für ein Update Änderungen an Clients erforderlich sind, die den Webdienst nutzen, behält Microsoft die vorherige Version (eine Version zurück) des verfügbaren Webdiensts für mindestens zwölf (12) Monate nach der Veröffentlichung der neuen Version bei. Kunden, die während dieses Zeitraums nicht aktualisieren, können möglicherweise nicht mehr auf den Webdienst und die zugehörigen Methoden zugreifen. Kunden müssen sicherstellen, dass Clients des Webdiensts weiterhin ohne Fehler funktionieren, wenn die folgenden Änderungen an der Webdienst-Schnittstellensignatur vorgenommen werden:</span><span class="sxs-lookup"><span data-stu-id="b19b4-p147">Updates to the parameters or results for these web service methods may be required in the future. After the general availability version of these web services is published, Microsoft will make reasonable efforts to provide advance notice of material updates to the web service. When Microsoft believes that an update will require changes to clients using the web service, Microsoft will keep the previous version (one version back) of the web service available for at least twelve (12) months after the release of the new version. Customers who do not upgrade during that time may be unable to access the web service and its methods. Customers must ensure that clients of the web service continue working without error if the following changes are made to the web service interface signature:</span></span>

- <span data-ttu-id="b19b4-286">Hinzufügen eines neuen optionalen Parameters zu einer vorhandenen Webmethode, die nicht notwendigerweise von älteren Clients bereitgestellt werden muss und das Ergebnis nicht beeinträchtigt, das ein älterer Client erhält.</span><span class="sxs-lookup"><span data-stu-id="b19b4-286">Adding a new optional parameter to an existing web method that doesn't have to be provided by older clients and doesn't impact the result an older client receives.</span></span>
- <span data-ttu-id="b19b4-287">Hinzufügen eines neuen benannten Attributs zu einem der REST-Antwortelemente oder zusätzlicher Spalten zur Antwort-CSV.</span><span class="sxs-lookup"><span data-stu-id="b19b4-287">Adding a new named attribute in one of the response REST items or additional columns to the response CSV.</span></span>
- <span data-ttu-id="b19b4-288">Hinzufügen einer neuen Webmethode unter einem neuen Namen, die nicht von älteren Clients aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="b19b4-288">Adding a new web method with a new name that is not called by the older clients.</span></span>

## <a name="related-topics"></a><span data-ttu-id="b19b4-289">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="b19b4-289">Related Topics</span></span>
  
[<span data-ttu-id="b19b4-290">URLs und IP-Adressbereiche für Office 365</span><span class="sxs-lookup"><span data-stu-id="b19b4-290">Office 365 URLs and IP address ranges</span></span>](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[<span data-ttu-id="b19b4-291">Häufig gestellte Fragen zu Office 365-Endpunkten</span><span class="sxs-lookup"><span data-stu-id="b19b4-291">Office 365 Germany endpoints</span></span>](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)

[<span data-ttu-id="b19b4-292">Prinzipien von Office 365-Netzwerkverbindungen</span><span class="sxs-lookup"><span data-stu-id="b19b4-292">Office 365 Network Connectivity Principles</span></span>](office-365-network-connectivity-principles.md)

[<span data-ttu-id="b19b4-293">Office 365-Netzwerk- und Leistungsoptimierung</span><span class="sxs-lookup"><span data-stu-id="b19b4-293">Office 365 network and performance tuning</span></span>](network-planning-and-performance.md)

[<span data-ttu-id="b19b4-294">Netzwerkkonnektivität mit Office 365</span><span class="sxs-lookup"><span data-stu-id="b19b4-294">Network connectivity to Office 365</span></span>](network-connectivity.md)
  
[<span data-ttu-id="b19b4-295">Medienqualität und Netzwerkverbindungsleistung in Skype for Business Online</span><span class="sxs-lookup"><span data-stu-id="b19b4-295">Media Quality and Network Connectivity Performance in Skype for Business Online</span></span>](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[<span data-ttu-id="b19b4-296">Optimieren Ihres Netzwerks für Skype for Business Online</span><span class="sxs-lookup"><span data-stu-id="b19b4-296">Optimizing your network for Skype for Business Online</span></span>](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43)

[<span data-ttu-id="b19b4-297">Office 365-Leistungsoptimierung mit Basisplänen und Leistungsverlauf</span><span class="sxs-lookup"><span data-stu-id="b19b4-297">Office 365 performance tuning using baselines and performance history</span></span>](performance-tuning-using-baselines-and-history.md)
  
[<span data-ttu-id="b19b4-298">Plan zur Problembehandlung für Office 365</span><span class="sxs-lookup"><span data-stu-id="b19b4-298">Performance troubleshooting plan for Office 365</span></span>](performance-troubleshooting-plan.md)
