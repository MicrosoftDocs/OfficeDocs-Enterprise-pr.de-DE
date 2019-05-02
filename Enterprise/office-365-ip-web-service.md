---
title: Office 365-IP-Adress- und -URL-Webdienst
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 5/1/2019
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
ms.openlocfilehash: af1ff6f222d4d9563116c4173ebeca9ca9f4470d
ms.sourcegitcommit: 3b5597cab55bc67890fd6c760102efce513be87b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/01/2019
ms.locfileid: "33512681"
---
# <a name="office-365-ip-address-and-url-web-service"></a><span data-ttu-id="8e0b4-104">Office 365-IP-Adresse- und -URL-Webdienst</span><span class="sxs-lookup"><span data-stu-id="8e0b4-104">Office 365 IP Address and URL Web service</span></span>

<span data-ttu-id="8e0b4-p102">Damit Sie Office 365-Netzwerkdatenverkehr besser erkennen und unterscheiden können, veröffentlicht ein neuer Webdienst Office 365-Endpunkte, sodass Sie Änderungen einfacher bewerten, konfigurieren und mit diesen auf dem Laufenden bleiben können. Dieser neue Webdienst ersetzt die herunterladbaren XML-Dateien, die derzeit verfügbar sind. Das XML-Format ist ab dem 2. Oktober 2018 nicht mehr verfügbar.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-p102">To help you better identify and differentiate Office 365 network traffic, a new web service publishes Office 365 endpoints, making it easier for you to evaluate, configure, and stay up to date with changes. This new web service replaces the XML downloadable files that are currently available. The XML format is planned to be phased out on October 2, 2018.</span></span>

<span data-ttu-id="8e0b4-p103">Als Kunde oder Anbieter von Netzwerkperimetergeräten können Sie den neuen REST-basierten Webdienst für die Office 365-IP-Adress- und -FQDN-Einträge verwenden. Sie können auf die Daten direkt in einem Webbrowser über die folgenden URLs zugreifen.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-p103">As a customer or a network perimeter device vendor, you can build against the new REST-based web service for the Office 365 IP address and FQDN entries. You can access the data directly in a web browser using these URLs.</span></span>

- <span data-ttu-id="8e0b4-110">Verwenden Sie für die neueste Version der Office 365-URLs und -IP-Adressbereiche [https://endpoints.office.com/version](https://endpoints.office.com/version?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span><span class="sxs-lookup"><span data-stu-id="8e0b4-110">For the latest version of the Office 365 URLs and IP address ranges, use [https://endpoints.office.com/version](https://endpoints.office.com/version?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span></span>
- <span data-ttu-id="8e0b4-111">Verwenden Sie für die Daten auf der Seite für die Office 365-URLs und -IP-Adressbereiche für Firewalls und Proxyserver [https://endpoints.office.com/endpoints/worldwide](https://endpoints.office.com/endpoints/worldwide?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span><span class="sxs-lookup"><span data-stu-id="8e0b4-111">For the data on the Office 365 URLs and IP address ranges page for firewalls and proxy servers, use [https://endpoints.office.com/endpoints/worldwide](https://endpoints.office.com/endpoints/worldwide?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span></span>
- <span data-ttu-id="8e0b4-112">Um die neuesten Änderungen seit Ende Juli 2018 zu erhalten (Datum, zu dem der Webdienst erstmalig verfügbar war), verwenden Sie [https://endpoints.office.com/changes/worldwide/0000000000](https://endpoints.office.com/changes/worldwide/0000000000?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span><span class="sxs-lookup"><span data-stu-id="8e0b4-112">To get all the latest changes since the end of July 2018 when the web service was first available, use [https://endpoints.office.com/changes/worldwide/0000000000](https://endpoints.office.com/changes/worldwide/0000000000?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span></span>

<span data-ttu-id="8e0b4-113">Als Kunde können Sie diesen Webdienst für Folgendes verwenden:</span><span class="sxs-lookup"><span data-stu-id="8e0b4-113">As a customer, you can use this web service to:</span></span>

- <span data-ttu-id="8e0b4-114">Aktualisieren Sie Ihre PowerShell-Skripte zum Abrufen von Daten auf Office 365-Endpunkten und zum Ändern der Formatierung für Ihre Netzwerkgeräte.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-114">Update your PowerShell scripts to obtain Office 365 endpoint data and modify any formatting for your networking devices.</span></span>
- <span data-ttu-id="8e0b4-115">Verwenden Sie diese Informationen, um auf Clientcomputern bereitgestellte PAC-Dateien zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-115">Use this information to update PAC files deployed to client computers.</span></span>

<span data-ttu-id="8e0b4-116">Als Anbieter von Netzwerkperimetergeräten können Sie diesen Webdienst für Folgendes verwenden:</span><span class="sxs-lookup"><span data-stu-id="8e0b4-116">As a network perimeter device vendor, you can use this web service to:</span></span>

- <span data-ttu-id="8e0b4-117">Erstellen und testen Sie Gerätesoftware für den Download der Liste für die automatische Konfiguration.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-117">Create and test device software to download the list for automated configuration.</span></span>
- <span data-ttu-id="8e0b4-118">Suchen Sie die aktuelle Version.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-118">Check for the current version.</span></span>
- <span data-ttu-id="8e0b4-119">Rufen Sie die aktuellen Änderungen ab.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-119">Get the current changes.</span></span>

> [!NOTE]
> <span data-ttu-id="8e0b4-120">Wenn Sie Azure ExpressRoute für die Verbindung mit Office 365 verwenden, lesen Sie bitte [Azure ExpressRoute for Office 365](https://docs.microsoft.com/office365/enterprise/azure-expressroute), um sich mit den Office 365-Diensten vertraut zu machen, die von Azure ExpressRoute unterstützt werden. </span><span class="sxs-lookup"><span data-stu-id="8e0b4-120">If you are using Azure ExpressRoute to connect to Office 365, please review [Azure ExpressRoute for Office 365](https://docs.microsoft.com/office365/enterprise/azure-expressroute) to familiarize yourself with the Office 365 services supported over Azure ExpressRoute.</span></span> <span data-ttu-id="8e0b4-121">Bitte lesen Sie auch den Artikel [Office 365-URLs und -IP-Adressbereiche](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges?redirectSourcePath=%252farticle%252fOffice-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2), um zu verstehen, welche Netzwerke für Office 365-Apps eine Internetverbindung benötigen.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-121">Also review the article [Office 365 URLs and IP address ranges](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges?redirectSourcePath=%252farticle%252fOffice-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2) to understand which network requests for Office 365 applications require Internet connectivity.</span></span> <span data-ttu-id="8e0b4-122">Das wird Ihnen helfen, Ihre Umkreis-Sicherheitsgeräte besser zu konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-122">This will help to better configure your perimeter security devices.</span></span>

<span data-ttu-id="8e0b4-123">Weitere Informationen finden Sie unter:</span><span class="sxs-lookup"><span data-stu-id="8e0b4-123">For additional information, see:</span></span>

- [<span data-ttu-id="8e0b4-124">Ankündigungsblogbeitrag im Office 365 Tech-Community-Forum</span><span class="sxs-lookup"><span data-stu-id="8e0b4-124">Announcement blog post in the Office 365 Tech Community Forum</span></span>](https://techcommunity.microsoft.com/t5/Office-365-Blog/Announcing-Office-365-endpoint-categories-and-Office-365-IP/ba-p/177638)
- [<span data-ttu-id="8e0b4-125">Office 365-Tech-Community-Forum für Fragen zur Verwendung der Webdienste</span><span class="sxs-lookup"><span data-stu-id="8e0b4-125">Office 365 Tech Community Forum for questions about use of the web services</span></span>](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking)

## <a name="common-parameters"></a><span data-ttu-id="8e0b4-126">Allgemeine Parameter</span><span class="sxs-lookup"><span data-stu-id="8e0b4-126">Common parameters</span></span>

<span data-ttu-id="8e0b4-127">Diese Parameter gelten für sämtliche Webdienstmethoden:</span><span class="sxs-lookup"><span data-stu-id="8e0b4-127">These parameters are common across all the web service methods:</span></span>

- <span data-ttu-id="8e0b4-128">**format=<JSON | CSV>** - Standardmäßig ist die zurückgegebene Datei als JSON formatiert.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-128">**format=<JSON | CSV>** - By default, the returned data format is JSON.</span></span> <span data-ttu-id="8e0b4-129">Verwenden Sie diesen optionalen Parameter, um die Daten in durch Trennzeichen getrennte Werte (CSV-Format) zurückzubekommen.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-129">Use this optional parameter to return the data in comma-separated values (CSV) format.</span></span>
- <span data-ttu-id="8e0b4-130">**ClientRequestId=\<guid>** - Eine erforderliche GUID, die Sie für die Clientzuordnung generieren.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-130">**ClientRequestId=\<guid>** - A required GUID that you generate for client association.</span></span> <span data-ttu-id="8e0b4-131">Sie sollten eine GUID für jeden Computer generieren, der den Webdienst aufruft.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-131">You should generate a GUID for each machine that calls the web service.</span></span> <span data-ttu-id="8e0b4-132">Verwenden Sie nicht die in den folgenden Beispielen angezeigten GUIDs, da sie in Zukunft durch den Webdienst blockiert werden könnten.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-132">Do not use the GUIDs shown in the following examples because they may be blocked by the web service in the future.</span></span> <span data-ttu-id="8e0b4-133">GUID-Format ist _xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx_, wobei x eine hexadezimale Zahl darstellt.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-133">GUID format is _xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx_, where x represents a hexadecimal number.</span></span> <span data-ttu-id="8e0b4-134">Um eine GUID zu generieren, verwenden Sie den PowerShell-Befehl [New-Guid](https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-guid?view=powershell-6).</span><span class="sxs-lookup"><span data-stu-id="8e0b4-134">To generate a GUID, use the [New-Guid](https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-guid?view=powershell-6) PowerShell command.</span></span>

## <a name="version-web-method"></a><span data-ttu-id="8e0b4-135">Versionswebmethode</span><span class="sxs-lookup"><span data-stu-id="8e0b4-135">Version web method</span></span>

<span data-ttu-id="8e0b4-p107">Microsoft aktualisiert die Office 365-IP-Adress- und -FQDN-Einträge am Ende jedes Monats und gelegentlich auch außerhalb dieses Zyklus aufgrund von betrieblichen oder Supportanforderungen. Den Daten für jede veröffentlichte Instanz wird eine Versionsnummer zugewiesen. Mit der Versionswebmethode können Sie die neueste Version für jede Instanz des Office 365-Diensts abrufen. Es wird empfohlen, dass Sie die Version tages- oder stundenweise überprüfen. Neue Versionen sollten zu Beginn jedes Monats zur Verfügung stehen. Manchmal sind aufgrund von Supportanfragen, Sicherheitsbelangen oder anderen betrieblichen Anforderungen neue Versionen während des Monats verfügbar.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-p107">Microsoft updates the Office 365 IP address and FQDN entries at the end of each month and occasionally out of cycle for operational or support requirements. The data for each published instance is assigned a version number. The version web method lets you poll for the latest version for each Office 365 service instance. We recommend you check the version daily, or at the most, hourly. New versions should be expected at the start of each month. Sometimes due to support incident, security, or other operational requirements there will be new versions during the month.</span></span>

<span data-ttu-id="8e0b4-142">Parameter für die Versionswebmethode sind:</span><span class="sxs-lookup"><span data-stu-id="8e0b4-142">Parameters for the version web method are:</span></span>

- <span data-ttu-id="8e0b4-143">**AllVersions=<true | false>** - Standardmäßig ist die zurückgegebene Version die neueste.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-143">**AllVersions=<true | false>** - By default, the version returned is the latest.</span></span> <span data-ttu-id="8e0b4-144">Übernehmen Sie diesen optionalen Parameter, um alle veröffentlichten Versionen seit dem ersten Release des Webdiensts anzufordern.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-144">Include this optional parameter to request all published versions since the web service was first released.</span></span>
- <span data-ttu-id="8e0b4-145">**Format=<JSON | CSV | RSS>** - Zusätzlich zu den Formaten JSON und CSV unterstützt die Versionswebmethode auch RSS.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-145">**Format=<JSON | CSV | RSS>** – In addition to the JSON and CSV formats, the version web method also supports RSS.</span></span> <span data-ttu-id="8e0b4-146">Diesen optionalen Parameter können Sie zusammen mit dem Parameter _AllVersions=true_ verwenden, um einen RSS-Feed anzufordern, der mit Outlook oder anderen RSS-Diensten verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-146">You can use this optional parameter along with the _AllVersions=true_ parameter to request an RSS feed which can be used with Outlook or other RSS readers.</span></span>
- <span data-ttu-id="8e0b4-147">**Instance=<Weltweit | China | Deutschland | USGovDoD | USGovGCCHigh>** - Dieser optionale Parameter spezifiziert die Instanz, in die die Version zurückgegeben werden soll. </span><span class="sxs-lookup"><span data-stu-id="8e0b4-147">**Instance=<Worldwide | China | Germany | USGovDoD | USGovGCCHigh>** - This optional parameter specifies the instance to return the version for.</span></span> <span data-ttu-id="8e0b4-148">Wenn nicht angegeben, werden alle Instanzen zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-148">If omitted, all instances are returned.</span></span> <span data-ttu-id="8e0b4-149">Gültige Instanzen sind: Weltweit, China, Deutschland, USGovDoD, USGovGCCHigh.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-149">Valid instances are: Worldwide, China, Germany, USGovDoD, USGovGCCHigh.</span></span>

<span data-ttu-id="8e0b4-p111">Die Versionswebmethode ist nicht beschränkt und gibt nie die HTTP-Antwortcodes 429 zurück. Das Ergebnis der Versionswebmethode umfasst keinen Cache-Control-Header, der empfiehlt, die Daten eine Stunde lang zwischenzuspeichern. Das Ergebnis der Versionswebmethode kann ein einzelner Datensatz oder ein Datensatzarray sein. Die Elemente der einzelnen Datensätze sind:</span><span class="sxs-lookup"><span data-stu-id="8e0b4-p111">The version web method is not rate limited and does not ever return 429 HTTP Response Codes. The response to the version web method does include a cache-control header recommending caching of the data for 1 hour. The result from the version web method may be a single record or an array of records. The elements of each record are:</span></span>

- <span data-ttu-id="8e0b4-154">instance – der kurze Name der Office 365-Serviceinstanz.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-154">instance - The short name of the Office 365 service instance.</span></span>
- <span data-ttu-id="8e0b4-155">latest – die neueste Version für Endpunkte der angegebenen Instanz.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-155">latest - The latest version for endpoints of the specified instance.</span></span>
- <span data-ttu-id="8e0b4-p112">versions – eine Liste aller vorherigen Versionen für die angegebene Instanz. Dieses Element ist nur enthalten, wenn der Parameter „AllVersions“ „true“ ist.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-p112">versions - A list of all previous versions for the specified instance. This element is only included if the AllVersions parameter is true.</span></span>

<span data-ttu-id="8e0b4-p113">Sie können Microsoft Flow verwenden, um E-Mail-Benachrichtigungen über Änderungen an den IP-Adressen und URLs zu erhalten. Weitere Informationen finden Sie unter [Use Microsoft Flow to receive an email for changes to Office 365 IP Addresses and URLs](https://techcommunity.microsoft.com/t5/Office-365-Networking/Use-Microsoft-Flow-to-receive-an-email-for-changes-to-Office-365/m-p/240651).</span><span class="sxs-lookup"><span data-stu-id="8e0b4-p113">You can use Microsoft Flow to get email notifications of changes to the IP Addresses and URLs. See [Use Microsoft Flow to receive an email for changes to Office 365 IP Addresses and URLs](https://techcommunity.microsoft.com/t5/Office-365-Networking/Use-Microsoft-Flow-to-receive-an-email-for-changes-to-Office-365/m-p/240651).</span></span>

### <a name="examples"></a><span data-ttu-id="8e0b4-160">Beispiele:</span><span class="sxs-lookup"><span data-stu-id="8e0b4-160">Examples:</span></span>

<span data-ttu-id="8e0b4-161">Anfrage-URI – Beispiel 1: [https://endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="8e0b4-161">Example 1 request URI: [https://endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="8e0b4-p114">Dieser URI gibt die aktuelle Version jeder Instanz des Office 365-Diensts zurück. Beispielergebnis:</span><span class="sxs-lookup"><span data-stu-id="8e0b4-p114">This URI returns the latest version of each Office 365 service instance. Example result:</span></span>

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
> <span data-ttu-id="8e0b4-p115">Die GUID für den Parameter „ClientRequestID“ in diesen URIs dient nur als Beispiel. Um die Webdienst-URIs auszuprobieren, erstellen Sie Ihre eigene GUID. Die in den folgenden Beispielen gezeigten GUIDs werden möglicherweise in Zukunft vom Webdienst gesperrt.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-p115">The GUID for the ClientRequestID parameter in these URIs are only an example. To try the web service URIs out, generate your own GUID. The GUIDs shown in these examples may be blocked by the web service in the future.</span></span>

<span data-ttu-id="8e0b4-167">Anfrage-URI – Beispiel 2: [https://endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="8e0b4-167">Example 2 request URI: [https://endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="8e0b4-p116">Dieser URI gibt die aktuelle Version der angegebenen Instanz des Office 365-Diensts zurück. Beispielergebnis:</span><span class="sxs-lookup"><span data-stu-id="8e0b4-p116">This URI returns the latest version of the specified Office 365 service instance. Example result:</span></span>

```json
{
 "instance": "Worldwide",
 "latest": "2018063000"
}

```

<span data-ttu-id="8e0b4-170">Anfrage-URI – Beispiel 3: [https://endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="8e0b4-170">Example 3 request URI: [https://endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="8e0b4-p117">Dieser URI zeigt die Ausgabe im CSV-Format an. Beispielergebnis:</span><span class="sxs-lookup"><span data-stu-id="8e0b4-p117">This URI shows output in CSV format. Example result:</span></span>

```csv
instance,latest
Worldwide,2018063000
```

<span data-ttu-id="8e0b4-173">Anfrage-URI – Beispiel 4: [https://endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="8e0b4-173">Example 4 request URI: [https://endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="8e0b4-p118">Dieser URI zeigt alle vorherigen Versionen an, die für die Dienstinstanz von Office 365 weltweit veröffentlicht wurden. Beispielergebnis:</span><span class="sxs-lookup"><span data-stu-id="8e0b4-p118">This URI shows all prior versions that have been published for the Office 365 worldwide service instance. Example result:</span></span>

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

<span data-ttu-id="8e0b4-176">RSS-Feed-URI – Beispiel 5: [https://endpoints.office.com/version/worldwide?clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7&allVersions=true&format=RSS](https://endpoints.office.com/version/worldwide?clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7&allVersions=true&format=RSS)</span><span class="sxs-lookup"><span data-stu-id="8e0b4-176">Example 5 RSS Feed URI: [https://endpoints.office.com/version/worldwide?clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7&allVersions=true&format=RSS](https://endpoints.office.com/version/worldwide?clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7&allVersions=true&format=RSS)</span></span>

<span data-ttu-id="8e0b4-p119">Dieser URI zeigt einen RSS-Feed der veröffentlichten Versionen, die Links zu der Liste der Änderungen für jede Version enthalten. Beispielergebnis:</span><span class="sxs-lookup"><span data-stu-id="8e0b4-p119">This URI shows an RSS feed of the published versions that include links to the list of changes for each version. Example result:</span></span>

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

## <a name="endpoints-web-method"></a><span data-ttu-id="8e0b4-179">Endpunktwebmethode</span><span class="sxs-lookup"><span data-stu-id="8e0b4-179">Endpoints web method</span></span>

<span data-ttu-id="8e0b4-180">Die Endpunktwebmethode gibt alle Datensätze für IP-Adressbereiche und URLs zurück, die den Office 365-Dienst bilden.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-180">The endpoints web method returns all records for IP address ranges and URLs that make up the Office 365 service.</span></span> <span data-ttu-id="8e0b4-181">Während die neuesten Daten von der Endpunktwebmethode für die Netzwerkgerätekonfiguration verwendet werden sollten, können die Daten bis zu 30 Tage nach der Veröffentlichung aufgrund der für Ergänzungen im Vorfeld bereitgestellten Ankündigung zwischengespeichert werden.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-181">While the latest data from the endpoints web method should be used for network device configuration, the data can be cached for up to 30 days after it is published due to the advance notice provided for additions.</span></span> <span data-ttu-id="8e0b4-182">Wir empfehlen Ihnen, die Endpunktwebmethode nur dann aufzurufen, wenn die Versionswebmethode anzeigt, dass eine neue Version der Daten verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-182">We recommend you only call the endpoints web method again when the version web method indicates a new version of the data is available.</span></span>

<span data-ttu-id="8e0b4-183">Parameter für die Endpunktwebmethode sind:</span><span class="sxs-lookup"><span data-stu-id="8e0b4-183">Parameters for the endpoints web method are:</span></span>

- <span data-ttu-id="8e0b4-184">**ServiceAreas=<Common | Exchange | SharePoint | Skype>** - Eine durch Trennzeichen getrennte Liste von Dienstbereichen.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-184">**ServiceAreas=<Common | Exchange | SharePoint | Skype>** - A comma-separated list of service areas.</span></span> <span data-ttu-id="8e0b4-185">Gültige Elemente sind_Common_, _Exchange_, _SharePoint_ und _Skype_.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-185">Valid items are _Common_, _Exchange_, _SharePoint_, and _Skype_.</span></span> <span data-ttu-id="8e0b4-186">Da Common-Dienstbereich-Elemente die Voraussetzung für alle anderen Dienstbereiche sind, wir der Webdienst sie mit einschließen.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-186">Because Common service area items are a prerequisite for all other service areas, the web service will always include them.</span></span> <span data-ttu-id="8e0b4-187">Wenn Sie diesen Parameter nicht miteinschließen, werden alle Dienstbereiche zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-187">If you do not include this parameter, all service areas are returned.</span></span>
- <span data-ttu-id="8e0b4-188">**TenantName=<tenant_name>** - Ihr Office 365-Mandantenname.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-188">**TenantName=<tenant_name>** - Your Office 365 tenant name.</span></span> <span data-ttu-id="8e0b4-189">Der Webdienst übernimmt Ihren angegebenen Namen und fügt ihn in URL-Teile ein, die den Mandantennamen enthalten.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-189">The web service takes your provided name and inserts it in parts of URLs that include the tenant name.</span></span> <span data-ttu-id="8e0b4-190">Wenn Sie keinen Mandantennamen angeben, haben diese URL-Teile das Platzhalterzeichen (\*).</span><span class="sxs-lookup"><span data-stu-id="8e0b4-190">If you don't provide a tenant name, those parts of URLs have the wildcard character (\*).</span></span>
- <span data-ttu-id="8e0b4-191">**NoIPv6=<wahr | falsch>** - Stellen Sie dies auf wahr, um IPv6-Adressen von der Ausgabe auszuschließen, wenn Sie zum Beispiel IPv6 nicht in Ihrem Netzwerk verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-191">**NoIPv6=<true | false>** - Set this to true to exclude IPv6 addresses from the output, for example, if you don't use IPv6 in your network.</span></span>
- <span data-ttu-id="8e0b4-192">\*\* Instance=<Weltweit | China | Deutschland | USGovDoD | USGovGCCHigh>\*\* Dieses erforderliche Parameter spezifiziert die Instanz, für die die Endpunkte zurückgegeben werden sollen.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-192">**Instance=<Worldwide | China | Germany | USGovDoD | USGovGCCHigh>** - This required parameter specifies the instance to return the endpoints for.</span></span> <span data-ttu-id="8e0b4-193">Gültige Instanzen sind: Weltweit, China, Deutschland, USGovDoD, USGovGCCHigh.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-193">Valid instances are: Worldwide, China, Germany, USGovDoD, USGovGCCHigh.</span></span>

<span data-ttu-id="8e0b4-194">Wenn Sie die Endpunktwebmethode sehr häufig von derselben Client-IP-Adresse abrufen, erhalten Sie möglicherweise den HTTP-Antwortcode 429 (zu viele Anforderungen).</span><span class="sxs-lookup"><span data-stu-id="8e0b4-194">If you call the endpoints web method a large number of times from the same client IP address, you may receive HTTP Response Code 429 (Too Many Requests).</span></span> <span data-ttu-id="8e0b4-195">Die meisten Benutzer werden dies nie sehen.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-195">Most people will never see this.</span></span> <span data-ttu-id="8e0b4-196">Wenn Sie diesen Antwortcode erhalten, warten Sie 1 Stunde, bevor Sie Ihre Anforderung wiederholen.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-196">If you get this response code, wait 1 hour before repeating your request.</span></span> <span data-ttu-id="8e0b4-197">Sie sollten die Endpunktwebmethode nur dann aufrufen, wenn die Versionswebmethode anzeigt, dass eine neue Version verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-197">Plan to only call the endpoints web method when the version web method indicates there is a new version available.</span></span>

<span data-ttu-id="8e0b4-p125">Das Ergebnis der Endpunktwebmethode ist ein Datensatz-Array, bei dem jeder Datensatz einen Endpunktsatz darstellt. Die Elemente für jeden Datensatz lauten:</span><span class="sxs-lookup"><span data-stu-id="8e0b4-p125">The result from the endpoints web method is an array of records with each record representing an endpoint set. The elements for each record are:</span></span>

- <span data-ttu-id="8e0b4-200">id – die unveränderliche ID-Nummer des Endpunktsatzes.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-200">id - The immutable id number of the endpoint set.</span></span>
- <span data-ttu-id="8e0b4-201">ServiceArea – der Servicebereich, zu dem dies gehört: Common, Exchange, SharePoint oder Skype.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-201">serviceArea - The service area that this is part of: Common, Exchange, SharePoint, or Skype.</span></span>
- <span data-ttu-id="8e0b4-p126">urls – URLs für den Endpunktsatz. Ein JSON-Array von DNS-Datensätzen. Wird ausgelassen, falls leer.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-p126">urls - URLs for the endpoint set. A JSON array of DNS records. Omitted if blank.</span></span>
- <span data-ttu-id="8e0b4-p127">tcpPorts – TCP-Ports für den Endpunktsatz. Alle Portelemente werden als eine kommagetrennte Liste von Ports oder Portbereichen formatiert, getrennt durch einen Bindestrich (-). Ports gelten für alle IP-Adressen und alle URLs in diesem Endpunktsatz für diese Kategorie. Wird ausgelassen, falls leer.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-p127">tcpPorts - TCP ports for the endpoint set. All ports elements are formatted as a comma-separated list of ports or port ranges separated by a dash character (-). Ports apply to all IP addresses and all URLs in that endpoint set for that category. Omitted if blank.</span></span>
- <span data-ttu-id="8e0b4-p128">udpPorts – UDP-Ports für die IP-Adressbereiche in diesem Endpunktsatz. Wird ausgelassen, falls leer.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-p128">udpPorts - UDP ports for the IP address ranges in this endpoint set. Omitted if blank.</span></span>
- <span data-ttu-id="8e0b4-p129">ips – der mit diesem Endpunktsatz verknüpfte IP-Adressbereich (verknüpft mit den aufgeführten TCP- oder UDP-Ports). Ein JSON-Array von IP-Adressbereichen. Wird ausgelassen, falls lehr.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-p129">ips - The IP address ranges associated with this endpoint set as associated with the listed TCP or UDP ports. A JSON array of IP Address ranges. Omitted if blank.</span></span>
- <span data-ttu-id="8e0b4-p130">category – Die Konnektivitätskategorie für den Endpunktsatz. Gültige Werte sind „Optimize“, „Allow“ und „Default“. Wenn Sie die Endpunktdaten verwenden, um nach der Kategorie einer IP-Adresse oder URL zu suchen, kann Ihre Abfrage möglicherweise mehrere Kategorien zurückgeben. Es gibt mehrere Gründe, warum dies passieren kann. In diesen Fällen sollten Sie die Empfehlungen für die Kategorie mit der höchsten Priorität befolgen. Wenn der Endpunkt beispielsweise sowohl unter „Optimize“ als auch unter „Allow“ angezeigt wird, sollten Sie den Anforderungen für „Optimize“ folgen. Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-p130">category - The connectivity category for the endpoint set. Valid values are Optimize, Allow, and Default. If using the endpoint data to search for the category of an IP Address or URL, it is possible that your query may return multiple categories. There are a few reasons why that may happen. In these cases you should follow the recommendations for the highest priority category. For example, if the endpoint appears in both Optimize and Allow, you should follow the requirements for Optimize. Required.</span></span>
- <span data-ttu-id="8e0b4-221">expressRoute – „true“ oder „false“, wenn dieser Endpunktsatz über ExpressRoute weitergeleitet wird.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-221">expressRoute - True or False if this endpoint set is routed over ExpressRoute.</span></span>
- <span data-ttu-id="8e0b4-p131">required – „true“, wenn für diesen Endpunktsatz Konnektivität erforderlich ist, damit Office 365 unterstützt wird. „False“, wenn dieser Endpunktsatz optional ist.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-p131">required - True if this endpoint set is required to have connectivity for Office 365 to be supported. False if this endpoint set is optional.</span></span>
- <span data-ttu-id="8e0b4-p132">notes – für optionale Endpunkte. Dieser Text beschreibt die Office 365-Funktionalität, die fehlt, wenn der Zugriff auf IP-Adressen oder URLs in diesem Endpunktsatz nicht auf Netzwerkebene möglich ist. Wird ausgelassen, falls leer.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-p132">notes - For optional endpoints, this text describes Office 365 functionality that will be missing if IP addresses or URLs in this endpoint set cannot be accessed at the network layer. Omitted if blank.</span></span>

### <a name="examples"></a><span data-ttu-id="8e0b4-226">Beispiele:</span><span class="sxs-lookup"><span data-stu-id="8e0b4-226">Examples:</span></span>

<span data-ttu-id="8e0b4-227">Anfrage-URI – Beispiel 1: [https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="8e0b4-227">Example 1 request URI: [https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="8e0b4-p133">Dieser URI ruft alle Endpunkte für die Instanz von Office 365 weltweit für alle Workloads ab. Das Beispielergebnis zeigt einen Auszug der Ausgabe an:</span><span class="sxs-lookup"><span data-stu-id="8e0b4-p133">This URI obtains all endpoints for the Office 365 worldwide instance for all workloads. Example result showing an excerpt of the output:</span></span>

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

<span data-ttu-id="8e0b4-230">Zusätzliche Endpunktsätze sind in diesem Beispiel nicht enthalten.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-230">Additional endpoint sets are not included in this example.</span></span>

<span data-ttu-id="8e0b4-231">Anfrage-URI – Beispiel 2: [https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="8e0b4-231">Example 2 request URI: [https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="8e0b4-232">In diesem Beispiel werden nur Endpunkte für die Instanz von Office 365 weltweit für Exchange Online und Abhängigkeiten abgerufen.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-232">This example obtains endpoints for the Office 365 Worldwide instance for Exchange Online and dependencies only.</span></span>

<span data-ttu-id="8e0b4-233">Die Ausgabe für Beispiel 2 ähnelt Beispiel 1 mit dem Unterschied, dass die Ergebnisse keine Endpunkte für SharePoint Online oder Skype for Business Online enthalten.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-233">The output for example 2 is similar to example 1 except that the results will not include endpoints for SharePoint Online or Skype for Business Online.</span></span>

## <a name="changes-web-method"></a><span data-ttu-id="8e0b4-234">Änderungswebmethode</span><span class="sxs-lookup"><span data-stu-id="8e0b4-234">Changes web method</span></span>

<span data-ttu-id="8e0b4-p134">Die Änderungswebmethode gibt die neuesten Updates zurück, die veröffentlicht wurden. Dies sind in der Regel die im vorherigen Monat vorgenommenen Änderungen an IP-Adressbereichen und URLs. Die wichtigsten zu verarbeitenden Änderungen sind solche, bei denen neue URLs oder IP-Adressen hinzugefügt wurden. Denn wenn eine IP-Adresse nicht einer Firewall Zugriffssteuerungsliste oder eine URL nicht einer Proxyserver-Umgehungsliste hinzugefügt wird, kann dies zu einem Ausfall für Office 365-Benutzer hinter diesem Netzwerkgerät führen. Ungeachtet der betrieblichen Anforderungen werden _Add_-Vorgänge mit einer Frist von 30 Tage hinzugefügt, bevor ein solcher Ausfall auftreten würde.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-p134">The changes web method returns the most recent updates that have been published. This is typically the previous month's changes to IP address ranges and URLs. The most critical changes to be processed are when new URLs or IP Addresses are added since failing to add an IP Address to a firewall access control list, or a URL to a proxy server bypass list can cause an outage for Office 365 users behind that network device. Notwithstanding operational requirements, _Add_ operations are added with 30 days' notice before such an outage would occur.</span></span>

<span data-ttu-id="8e0b4-239">Die Parameter für die Änderungswebmethode sind:</span><span class="sxs-lookup"><span data-stu-id="8e0b4-239">The required parameter for the changes web method is:</span></span>

- <span data-ttu-id="8e0b4-240">**Version=\<YYYYMMDDNN>** Erforderlicher URL-Routenparameter.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-240">**Version=\<** - Required URL route parameter.</span></span> <span data-ttu-id="8e0b4-241">Dieser Wert sollte die Version sein, die Sie derzeit implementiert haben.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-241">This value should be the version that you have currently implemented.</span></span> <span data-ttu-id="8e0b4-242">Der Webdienst wird die Änderungen seit dieser Version zurückgeben.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-242">The web service will return the changes since that version.</span></span> <span data-ttu-id="8e0b4-243">Das Format ist _YYYYMMDDNN_, wobei _NN_ Nullen sind.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-243">The format is _YYYYMMDDNN_, where _NN_ are zeros.</span></span> <span data-ttu-id="8e0b4-244">Der Webdienst erfordert, dass dieser Parameter genau 10 Ziffern enthält.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-244">The web service requires this parameter to contain exactly 10 digits.</span></span>

<span data-ttu-id="8e0b4-245">Für die Änderungswebmethode sind die Gebühren auf dieselbe Art und Weise beschränkt wie bei der Endpunktwebmethode.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-245">The changes web method is rate limited in the same way as the endpoints web method. If you receive a 429 HTTP Response Code then you should wait 1 hour before calling again.</span></span> <span data-ttu-id="8e0b4-246">Wenn Sie einen 429-HTTP-Antwortcode erhalten, warten Sie 1 Stunde, bevor Sie Ihre Anforderung wiederholen.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-246">If you receive a 429 HTTP response code, wait 1 hour before repeating your request.</span></span>

<span data-ttu-id="8e0b4-p137">Das Ergebnis der Änderungswebmethode ist ein Datensatz-Array, bei dem jeder Datensatz eine Änderung in einer speziellen Version des Endpunkts darstellt. Die Elemente für jeden Datensatz lauten:</span><span class="sxs-lookup"><span data-stu-id="8e0b4-p137">The result from the changes web method is an array of records with each record representing a change in a specific version of the endpoints. The elements for each record are:</span></span>

- <span data-ttu-id="8e0b4-249">id – die unveränderliche ID des Änderungsdatensatzes.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-249">id - The immutable id of the change record.</span></span>
- <span data-ttu-id="8e0b4-250">endpointSetId - Die ID des Endpunktgruppendatensatzes, der geändert wird. </span><span class="sxs-lookup"><span data-stu-id="8e0b4-250">endpointSetId - The ID of the endpoint set record that is changed.</span></span>
- <span data-ttu-id="8e0b4-251">disposition - Das kann sowohl Ändern, Hinzufügen oder Entfernen sein und beschreibt, was die Veränderung im Endpunktgruppendatensatz bewirkt hat.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-251">disposition - This can be either of change, add, or remove and describes what the change did to the endpoint set record.</span></span>
- <span data-ttu-id="8e0b4-p138">Impact – Nicht alle Änderungen sind für jede Umgebung gleich wichtig. Hier werden die erwarteten Auswirkungen auf eine Netzwerkumkreisumgebung in einem Unternehmen als Ergebnis dieser Änderung beschrieben. Dieses Attribut ist nur in Änderungsdatensätzen der Version 2018112800 und höher enthalten. Optionen für die Auswirkungen sind:</span><span class="sxs-lookup"><span data-stu-id="8e0b4-p138">impact - Not all changes will be equally important to every environment. This describes the expected impact to an enterprise network perimeter environment as a result of this change. This attribute is included only in change records of version 2018112800 and later. Options for the impact are:</span></span>
  - <span data-ttu-id="8e0b4-p139">AddedIp – Zu Office 365 wurde eine IP-Adresse hinzugefügt, die in diesem Dienst in Kürze live gehen wird. Dies stellt eine Änderung dar, die Sie in einer Firewall oder in einem anderen Netzwerkumkreisgerät der Ebene 3 vornehmen müssen. Wenn Sie diese IP-Adresse nicht hinzufügen, bevor wir mit der Verwendung beginnen, tritt möglicherweise ein Ausfall auf.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-p139">AddedIp – An IP Address was added to Office 365 and will be live on the service soon. This represents a change you need to take on a firewall or other layer 3 network perimeter device. If you don’t add this before we start using it, you may experience an outage.</span></span>
  - <span data-ttu-id="8e0b4-259">AddedUrl - Ein URL wurde Office 365 hinzugefügt und wird in Kürze im Dienst live sein.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-259">AddedUrl – A URL was added to Office 365 and will be live on the service soon.</span></span> <span data-ttu-id="8e0b4-260">Dies stellt eine Änderung zur Analyse von Netzwerkumkreisgeräten dar, die Sie auf einem Proxyserver oder URL vornehmen müssen.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-260">This represents a change you need to take on a proxy server or URL parsing network perimeter device.</span></span> <span data-ttu-id="8e0b4-261">Wenn Sie dies nicht hinzufügen, bevor wir starten, werden Sie möglicherweise einen Ausfall erleben.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-261">If you don’t add this before we start using it, you may experience an outage.</span></span>
  - <span data-ttu-id="8e0b4-p141">AddedIpAndUrl – Sowohl eine IP-Adresse als auch eine URL wurden hinzugefügt. Dies stellt eine Änderung, die Sie auf einem Firewallgerät der Ebene 3, auf einem Proxyserver oder auf einem Gerät vornehmen müssen, das URLs analysiert. Wenn Sie diese IP-Adresse nicht hinzufügen, bevor wir mit der Verwendung beginnen, tritt möglicherweise ein Ausfall auf.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-p141">AddedIpAndUrl - Both an IP Address and a URL were added. This represents a change you need to take on either a firewall layer 3 device or a proxy server or URL parsing device. If you don’t add this before we start using it, you may experience an outage.</span></span>
  - <span data-ttu-id="8e0b4-p142">RemovedIpOrUrl – Mindestens eine IP-Adresse oder URL wurde aus Office 365 entfernt. Sie sollten die Netzwerkendpunkte von Ihren Umkreisgeräten entfernen, hierfür gibt es jedoch keinen Stichtag.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-p142">RemovedIpOrUrl – At least one IP Address or URL was removed from Office 365. You should remove the network endpoints from your perimeter devices, but there’s no deadline for you to do this.</span></span>
  - <span data-ttu-id="8e0b4-p143">ChangedIsExpressRoute – Das Attribut „ExpressRoute Support“ wurde geändert. Wenn Sie ExpressRoute verwenden, müssen Sie je nach Konfiguration möglicherweise entsprechende Maßnahmen ergreifen.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-p143">ChangedIsExpressRoute – The ExpressRoute support attribute was changed. If you use ExpressRoute then you may need to take action depending on your configuration.</span></span>
  - <span data-ttu-id="8e0b4-p144">MovedIpOrUrl – Eine IP-Adresse oder URL wurde zwischen diesem Endpunktsatz und einem anderen verschoben. Im Allgemeinen ist keine Aktion erforderlich.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-p144">MovedIpOrUrl – We moved an IP Address or Url between this endpoint set and another one. Generally no action is required.</span></span>
  - <span data-ttu-id="8e0b4-p145">RemovedDuplicateIpOrUrl – Es wurde eine doppelte IP-Adresse oder URL entfernt, diese ist aber immer noch auf Office 365 veröffentlicht. Im Allgemeinen ist keine Aktion erforderlich.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-p145">RemovedDuplicateIpOrUrl – We removed a duplicate IP Address or Url but it’s still published for Office 365. Generally no action is required.</span></span>
  - <span data-ttu-id="8e0b4-273">OtherNonPriorityChanges – Es wurde etwas weniger wichtiges als all die anderen Optionen geändert, z. B. ein Notizfeld.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-273">OtherNonPriorityChanges – We changed something less critical than all of the other options like a note field</span></span>
- <span data-ttu-id="8e0b4-p146">version – die Version des veröffentlichten Endpunktsatzes, in dem die Änderung eingeführt wurde. Versionsnummern werden im Format _JJJJMMTTNN_ angegeben, wobei NN eine natürliche Zahl ist, die erhöht wird, wenn mehrere Versionen an einem einzigen Tag veröffentlicht werden müssen.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-p146">version - The version of the published endpoint set in which the change was introduced. Version numbers are of the format _YYYYMMDDNN_, where NN is a natural number incremented if there are multiple versions required to be published on a single day.</span></span>
- <span data-ttu-id="8e0b4-276">previous - Eine Unterstruktur, welche vorherige Werte von Änderungselementen auf dem Endpunktsatz angibt.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-276">current - A substructure detailing updated values of changes elements on the endpoint set.</span></span> <span data-ttu-id="8e0b4-277">Dies ist bei neu hinzugefügten Endpunktsätzen nicht enthalten.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-277">This will not be included for newly added endpoint sets.</span></span> <span data-ttu-id="8e0b4-278">Umfasst _ExpressRoute_, _serviceArea_, _category_, _required_, _tcpPorts_, _udpPorts_ und _notes_.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-278">Includes _tcpPorts_, _udpPorts_, _ExpressRoute_, _category_, _required_, and _notes_.</span></span>
- <span data-ttu-id="8e0b4-279">current - Eine Unterstruktur, welche aktualisierte Werte von Änderungselementen auf dem Endpunktsatz angibt.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-279">current - A substructure detailing updated values of changes elements on the endpoint set.</span></span> <span data-ttu-id="8e0b4-280">Umfasst _ExpressRoute_, _serviceArea_, _category_, _required_, _tcpPorts_, _udpPorts_ und _notes_.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-280">Includes _tcpPorts_, _udpPorts_, _ExpressRoute_, _category_, _required_, and _notes_.</span></span>
- <span data-ttu-id="8e0b4-p149">add – eine Unterstruktur, die Elemente angibt, die zu Endpunktsatzsammlungen hinzugefügt werden sollen. Wird ausgelassen, wenn keine Ergänzungen vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-p149">add - A substructure detailing items to be added to endpoint set collections. Omitted if there are no additions.</span></span>
  - <span data-ttu-id="8e0b4-283">effectiveDate – definiert die Daten, wann die Ergänzungen live im Dienst sind.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-283">effectiveDate - Defines the data when the additions will be live in the service.</span></span>
  - <span data-ttu-id="8e0b4-284">ips - Elemente, die dem Array _ips_ hinzugefügt werden sollen.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-284">ips - Items to be added to the _ips_ array.</span></span>
  - <span data-ttu-id="8e0b4-285">urls - Elemente, die zum Array_urls_ hinzugefügt werden sollen.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-285">urls- Items to be added to the _urls_ array.</span></span>
- <span data-ttu-id="8e0b4-286">remove - eine Unterstruktur, die Elemente angibt, die aus dem Endpunktsatz entfernt werden sollen. </span><span class="sxs-lookup"><span data-stu-id="8e0b4-286">remove - A substructure detailing items to be removed from the endpoint set.</span></span> <span data-ttu-id="8e0b4-287">Wird ausgelassen, wenn keine Entfernungen vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-287">Omitted if there are no removals.</span></span>
  - <span data-ttu-id="8e0b4-288">ips - Elemente, die aus dem Array _ips_entfernt werden sollen.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-288">ips - Items to be removed from the _ips_ array.</span></span>
  - <span data-ttu-id="8e0b4-289">urls – Elemente, die aus dem Array _urls_ entfernt werden sollen.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-289">urls- Items to be removed from the _urls_ array.</span></span>

### <a name="examples"></a><span data-ttu-id="8e0b4-290">Beispiele:</span><span class="sxs-lookup"><span data-stu-id="8e0b4-290">Examples:</span></span>

<span data-ttu-id="8e0b4-291">Anfrage-URI – Beispiel 1: [https://endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="8e0b4-291">Example 1 request URI: [https://endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="8e0b4-p151">Dies fordert alle vorherigen Änderungen an der Dienstinstanz von Office 365 weltweit an. Beispielergebnis:</span><span class="sxs-lookup"><span data-stu-id="8e0b4-p151">This requests all previous changes to the Office 365 worldwide service instance. Example result:</span></span>

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

<span data-ttu-id="8e0b4-294">Anfrage-URI – Beispiel 2: [https://endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="8e0b4-294">Example 2 request URI: [https://endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="8e0b4-p152">Dies fordert Änderungen seit der angegebenen Version der Instanz von Office 365 weltweite an. Die angegebene Version ist in diesem Fall die neueste. Beispielergebnis:</span><span class="sxs-lookup"><span data-stu-id="8e0b4-p152">This requests changes since the specified version to the Office 365 Worldwide instance. In this case, the version specified is the latest. Example result:</span></span>

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

## <a name="example-powershell-script"></a><span data-ttu-id="8e0b4-298">PowerShell-Skript</span><span class="sxs-lookup"><span data-stu-id="8e0b4-298">Example PowerShell Script</span></span>

<span data-ttu-id="8e0b4-299">Hier ist ein PowerShell-Skript, das Sie ausführen können um festzustellen, ob es Aktionen gibt, die Sie für aktualisierte Daten ausführen müssen.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-299">Here is a PowerShell script that you can run to see if there are actions you need to take for updated data.</span></span> <span data-ttu-id="8e0b4-300">Dieses Skript überprüft die Versionsnummer für die Office 365 weltweit Instanz-Endpunkte.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-300">This script checks the version number for the Office 365 Worldwide instance endpoints.</span></span> <span data-ttu-id="8e0b4-301">Wenn eine Änderung vorhanden ist, lädt es die Endpunkte und Filter für die Endpunkte der Kategorie „Zulassen“ und „Optimieren“ herunter.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-301">When there is a change, it downloads the endpoints and filters for the "Allow" and "Optimize" category endpoints.</span></span> <span data-ttu-id="8e0b4-302">Es verwendet auch eine eindeutige _ClientRequestId_ für mehrere Aufrufe und speichert die neueste Version in einer temporären Datei.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-302">It also uses a unique _ClientRequestId_ across multiple calls and saves the latest version found in a temporary file.</span></span> <span data-ttu-id="8e0b4-303">Sie sollten dieses Skript einmal pro Stunde aufrufen, um auf eine Versionsaktualisierung zu prüfen.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-303">You should call this script once an hour to check for a version update.</span></span>

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

## <a name="example-python-script"></a><span data-ttu-id="8e0b4-304">Python-Beispielskript</span><span class="sxs-lookup"><span data-stu-id="8e0b4-304">Example Python Script</span></span>

<span data-ttu-id="8e0b4-p154">Hier ist ein Python-Skript, das mit Python 3.6.3 unter Windows 10 getestet wurde. Sie können es ausführen, um festzustellen, ob es Aktionen gibt, die Sie für aktualisierte Daten ausführen müssen. Dieses Skript überprüft die Versionsnummer für Endpunkte mit der Instanz von Office 365 weltweit. Wenn eine Änderung vorhanden ist, lädt es die Endpunkte herunter und filtert nach den Endpunkten der Kategorie _Zulassen_ und _Optimieren_. Außerdem verwendet es eine eindeutige ClientRequestId über mehrere Anrufe hinweg und speichert die aktuelle Version in einer temporären Datei. Sie sollten dieses Skript einmal pro Stunde aufrufen, um zu überprüfen, ob ein Versionsupdate vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-p154">Here is a Python script, tested with Python 3.6.3 on Windows 10, that you can run to see if there are actions you need to take for updated data. This script checks the version number for the Office 365 Worldwide instance endpoints. When there is a change, it downloads the endpoints and filters for the _Allow_ and _Optimize_ category endpoints. It also uses a unique ClientRequestId across multiple calls and saves the latest version found in a temporary file. You should call this script once an hour to check for a version update.</span></span>

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

## <a name="web-service-interface-versioning"></a><span data-ttu-id="8e0b4-310">Versionsverwaltung der Webdienstschnittstelle</span><span class="sxs-lookup"><span data-stu-id="8e0b4-310">Web Service interface versioning</span></span>

<span data-ttu-id="8e0b4-p155">In der Zukunft sind möglicherweise Updates für die Parameter oder die Ergebnisse für diese Webdienstmethoden erforderlich. Nachdem die allgemein verfügbare Version dieser Webdienste veröffentlicht wurde, bemüht sich Microsoft in angemessener Weise, bedeutende Updates im Hinblick auf den Webdienst im Vorfeld anzukündigen. Wenn Microsoft davon ausgeht, dass für ein Update Änderungen an Clients erforderlich sind, die den Webdienst nutzen, behält Microsoft die vorherige Version (eine Version zurück) des verfügbaren Webdiensts für mindestens zwölf (12) Monate nach der Veröffentlichung der neuen Version bei. Kunden, die während dieses Zeitraums nicht aktualisieren, können möglicherweise nicht mehr auf den Webdienst und die zugehörigen Methoden zugreifen. Kunden müssen sicherstellen, dass Clients des Webdiensts weiterhin ohne Fehler funktionieren, wenn die folgenden Änderungen an der Webdienst-Schnittstellensignatur vorgenommen werden:</span><span class="sxs-lookup"><span data-stu-id="8e0b4-p155">Updates to the parameters or results for these web service methods may be required in the future. After the general availability version of these web services is published, Microsoft will make reasonable efforts to provide advance notice of material updates to the web service. When Microsoft believes that an update will require changes to clients using the web service, Microsoft will keep the previous version (one version back) of the web service available for at least twelve (12) months after the release of the new version. Customers who do not upgrade during that time may be unable to access the web service and its methods. Customers must ensure that clients of the web service continue working without error if the following changes are made to the web service interface signature:</span></span>

- <span data-ttu-id="8e0b4-316">Hinzufügen eines neuen optionalen Parameters zu einer vorhandenen Webmethode, die nicht notwendigerweise von älteren Clients bereitgestellt werden muss und das Ergebnis nicht beeinträchtigt, das ein älterer Client erhält.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-316">Adding a new optional parameter to an existing web method that doesn't have to be provided by older clients and doesn't impact the result an older client receives.</span></span>
- <span data-ttu-id="8e0b4-317">Hinzufügen eines neuen benannten Attributs zu einem der REST-Antwortelemente oder zusätzlicher Spalten zur Antwort-CSV.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-317">Adding a new named attribute in one of the response REST items or additional columns to the response CSV.</span></span>
- <span data-ttu-id="8e0b4-318">Hinzufügen einer neuen Webmethode unter einem neuen Namen, die nicht von älteren Clients aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-318">Adding a new web method with a new name that is not called by the older clients.</span></span>

## <a name="office-365-endpoint-functions-module"></a><span data-ttu-id="8e0b4-319">Office 365-Endpunkt-Funktionsmodul</span><span class="sxs-lookup"><span data-stu-id="8e0b4-319">Office 365 Endpoint Functions Module</span></span>

<span data-ttu-id="8e0b4-320">Microsoft hostet einen REST-Webdienst, um die neuesten und aktuellen URL für die Office 365-Dienste zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-320">Microsoft is hosting a REST Service to get the newest and latest URI for the Office 365 services.</span></span>  <span data-ttu-id="8e0b4-321">Um den URL als Sammlung verwenden, können Sie dieses Modul mit ein paar hilfreichen Cmdlets verwenden.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-321">To be able to use the URI as a collection, you can use this module with a few helpful cmdlets.</span></span>

### <a name="calling-the-rest-service"></a><span data-ttu-id="8e0b4-322">REST-Dienst aufrufen</span><span class="sxs-lookup"><span data-stu-id="8e0b4-322">Calling the REST service</span></span>

<span data-ttu-id="8e0b4-323">Um dieses Modul zu verwenden, kopieren Sie einfach die Moduldatei [O365EndpointFunctions.psm1](https://github.com/samurai-ka/PS-Module-O365EndpointService/blob/master/O365EndpointFunctions.psm1) auf einen beliebigen Ort auf Ihrer Festplatte und importieren Sie es direkt mit dem folgenden Befehl:</span><span class="sxs-lookup"><span data-stu-id="8e0b4-323">To use this module, simply copy the module file [O365EndpointFunctions.psm1](https://github.com/samurai-ka/PS-Module-O365EndpointService/blob/master/O365EndpointFunctions.psm1) somewhere on your hard disk and import it directly with this command:</span></span>

```powershell
    Import-Module O365EndpointFunctions.psm1
```

<span data-ttu-id="8e0b4-324">Nachdem Sie das Modul importiert haben, werden Sie den REST-Dienst aufrufen können.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-324">After you have imported the module, you will be able to call the REST service.</span></span> <span data-ttu-id="8e0b4-325">Dies wird die URL als Sammlung zurückgeben, die Sie jetzt direkt in PowerShell verarbeiten können.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-325">This will return the URI as a collection that you can now process in PowerShell directly.</span></span> <span data-ttu-id="8e0b4-326">Sie müssen den Namen Ihres Office 365-Mandanten wie im nachfolgend beschriebenen Befehl eingeben:</span><span class="sxs-lookup"><span data-stu-id="8e0b4-326">You must enter the name of your Office 365 tenant, as described in the following command:</span></span>

```powershell
    Invoke-O365EnpointService -tenantName [Name of your tenant]
```

> [!NOTE]
> <span data-ttu-id="8e0b4-327">Das Cmdlet wird wie folgt geschrieben **Invoke-O365EnpointService**, ohne den Buchstaben _d_.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-327">The cmdlet is spelled **Invoke-O365EnpointService**, with no letter _d_.</span></span> <span data-ttu-id="8e0b4-328">Dies ist kein Tippfehler.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-328">This is not a typographical error.</span></span>

#### <a name="parameters"></a><span data-ttu-id="8e0b4-329">Parameter</span><span class="sxs-lookup"><span data-stu-id="8e0b4-329">Parameters</span></span>

- <span data-ttu-id="8e0b4-330">**tenantName** - Der Namen Ihres Office 365-Mandanten.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-330">**tenantName** - The name of your Office 365 tenant.</span></span> <span data-ttu-id="8e0b4-331">Dieser Parameter ist obligatorisch.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-331">This parameter is mandatory.</span></span>
- <span data-ttu-id="8e0b4-332">**ForceLatest** - Dieser Wechsel wird die REST-API dazu zwingen, immer die gesamte Liste der neuesten URL zurückzugeben.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-332">**ForceLatest** -This switch will force the REST API to always return the entire list of the latest URI.</span></span>
- <span data-ttu-id="8e0b4-333">**IPv6** - Dieser Wechsel wird auch die IPv6-Adressen zurückgeben.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-333">**IPv6** -This switch will return the IPv6 addresses as well.</span></span> <span data-ttu-id="8e0b4-334">Standardmäßig wird nur IPv4 zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-334">As default only IPv4 will be returned.</span></span>

### <a name="examples"></a><span data-ttu-id="8e0b4-335">Beispiele</span><span class="sxs-lookup"><span data-stu-id="8e0b4-335">Examples</span></span>

<span data-ttu-id="8e0b4-336">Die vollständige Liste aller URLs einschließlich IPv6-Adressen zurückgeben.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-336">Return the complete list of all URIs including the IPv6 addresses</span></span>

```powershell
    Invoke-O365EnpointService -tenantName [Name of your tenant] -ForceLatest -IPv6 | Format-Table -AutoSize
```

<span data-ttu-id="8e0b4-337">Nur die IP-Adressen für Exchange-Onlinedienst zurückgeben</span><span class="sxs-lookup"><span data-stu-id="8e0b4-337">Return only the IP addresses for Exchange Online Service</span></span>

```powershell
    Invoke-O365EnpointService -tenantName [Name of your tenant] -ForceLatest | where{($_.serviceArea -eq "Exchange") -and ($_.protocol -eq "ip")}| Format-Table -AutoSize
```

### <a name="exporting-a-proxy-pac-file"></a><span data-ttu-id="8e0b4-338">Eine Proxy-PAC-Datei exportieren</span><span class="sxs-lookup"><span data-stu-id="8e0b4-338">Exporting a Proxy PAC file</span></span>

<span data-ttu-id="8e0b4-339">Dieses Modul können Sie verwenden, um eine Proxy-PAC-Datei zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-339">You can use this module to create a Proxy PAC file.</span></span> <span data-ttu-id="8e0b4-340">In diesem Beispiel erhalten Sie zuerst die Endpunkte und filtern das Ergebnis, um die URLs auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-340">In this example you first get the endpoints and filter the result to select the URLs.</span></span> <span data-ttu-id="8e0b4-341">Um exportiert werden zu können, werden diese URLs weitergeleitet.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-341">These URLs are piped to be exported.</span></span>  

```powershell
 Invoke-O365EnpointService -tenantName [Name of your tenant] -ForceLatest | where{($_.Protocol -eq "Url") -and (($_.Category -eq "Optimize") -or ($_.category -eq "Allow"))} | select uri -Unique | Export-O365ProxyPacFile
```

## <a name="related-topics"></a><span data-ttu-id="8e0b4-342">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="8e0b4-342">Related Topics</span></span>
  
[<span data-ttu-id="8e0b4-343">URLs und IP-Adressbereiche für Office 365</span><span class="sxs-lookup"><span data-stu-id="8e0b4-343">Office 365 URLs and IP address ranges</span></span>](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[<span data-ttu-id="8e0b4-344">Häufig gestellte Fragen zu Office 365-Endpunkten</span><span class="sxs-lookup"><span data-stu-id="8e0b4-344">Office 365 endpoints FAQ</span></span>](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)

[<span data-ttu-id="8e0b4-345">Prinzipien von Office 365-Netzwerkverbindungen</span><span class="sxs-lookup"><span data-stu-id="8e0b4-345">Office 365 Network Connectivity Principles</span></span>](office-365-network-connectivity-principles.md)

[<span data-ttu-id="8e0b4-346">Office 365-Netzwerk- und Leistungsoptimierung</span><span class="sxs-lookup"><span data-stu-id="8e0b4-346">Office 365 network and performance tuning</span></span>](network-planning-and-performance.md)

[<span data-ttu-id="8e0b4-347">Netzwerkkonnektivität mit Office 365</span><span class="sxs-lookup"><span data-stu-id="8e0b4-347">Network connectivity to Office 365</span></span>](network-connectivity.md)
  
[<span data-ttu-id="8e0b4-348">Medienqualität und Netzwerkverbindungsleistung in Skype for Business Online</span><span class="sxs-lookup"><span data-stu-id="8e0b4-348">Media Quality and Network Connectivity Performance in Skype for Business Online</span></span>](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[<span data-ttu-id="8e0b4-349">Optimieren Ihres Netzwerks für Skype for Business Online</span><span class="sxs-lookup"><span data-stu-id="8e0b4-349">Optimizing your network for Skype for Business Online</span></span>](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43)

[<span data-ttu-id="8e0b4-350">Office 365-Leistungsoptimierung mit Basisplänen und Leistungsverlauf</span><span class="sxs-lookup"><span data-stu-id="8e0b4-350">Office 365 performance tuning using baselines and performance history</span></span>](performance-tuning-using-baselines-and-history.md)
  
[<span data-ttu-id="8e0b4-351">Plan zur Problembehandlung für Office 365</span><span class="sxs-lookup"><span data-stu-id="8e0b4-351">Performance troubleshooting plan for Office 365</span></span>](performance-troubleshooting-plan.md)
