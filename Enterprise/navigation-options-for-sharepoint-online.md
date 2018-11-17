---
title: Navigationsoptionen für SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: adb92b80-b342-4ecb-99a1-da2a2b4782eb
description: Dieser Artikel beschreibt die Navigation Optionen Websites mit SharePoint-Veröffentlichung in SharePoint Online aktiviert. Die Auswahl und Konfiguration der Navigation erheblich beeinträchtigt die Leistung und Skalierbarkeit von Websites in SharePoint Online.
ms.openlocfilehash: 5a190ca643c20b6644ca1eecdac2a4a2e281a09e
ms.sourcegitcommit: 45633b7034ee98d0cd833db9743f283b638237f4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "26547177"
---
# <a name="navigation-options-for-sharepoint-online"></a>Navigationsoptionen für SharePoint Online

Dieser Artikel beschreibt die Navigation Optionen Websites mit SharePoint-Veröffentlichung in SharePoint Online aktiviert. Die Auswahl und Konfiguration der Navigation erheblich beeinträchtigt die Leistung und Skalierbarkeit von Websites in SharePoint Online.

## <a name="overview"></a>Übersicht

Navigation Anbieterkonfiguration kann die Leistung für die gesamte Website erheblich beeinträchtigen und sorgfältige auswählen eine Navigationsanbieter und die Konfiguration, die für die Anforderungen der SharePoint-Website effektiv skaliert geschaltet werden muss. Es gibt zwei Out-of-Box-Navigationsanbieter als auch benutzerdefinierte Navigation Implementierungen.

Die erste Option [**(Metadaten) verwaltete Navigation**](#using-managed-navigation-and-metadata-in-sharepoint-online), wird empfohlen und ist eine der Standardoptionen in SharePoint Online. jedoch wird empfohlen, dass die Einschränkung aus Sicherheitsgründen deaktiviert werden, sofern nicht erforderlich. Aus Sicherheitsgründen ist für diesen Navigationsanbieter als Einstellung secure standardmäßig aktiviert. Viele Websites ist jedoch nicht erforderlich des Verarbeitungsaufwands Security trimming, da Navigationselemente häufig für alle Benutzer der Website sind. Mit der empfohlenen Konfiguration aus Sicherheitsgründen deaktivieren diese Navigationsanbieter erfordert keine Aufzählen der Websitestruktur und hochskalierbare akzeptable Leistung beeinträchtigt wird.

Die zweite Option [**strukturelle Navigation**](#using-structural-navigation-in-sharepoint-online), **nicht die Navigationsoption empfohlene in SharePoint Online ist**. Diese Navigationsanbieter wurde entwickelt, für eine lokale-Topologie nur unterstützt in SharePoint Online eingeschränkt. Während sie einige zusätzliche Funktionen im Vergleich zu anderen Navigationsoptionen bietet, diese Features, einschließlich der Einschränkung aus Sicherheitsgründen und Website-Struktur-Aufzählung, Ihren Preis aufgrund einer Anrufe und Auswirkungen Skalierbarkeit und Leistung bei Verwendung. Websites mit Structed Navigation, die übermäßig viele Ressourcen beanspruchen können Drosselung werden.

Zusätzlich zu den Out-of-Box-Navigationsanbieter haben viele Kunden alternative benutzerdefinierte Navigation Implementierungen erfolgreich implementiert. Eine allgemeine Klasse der benutzerdefinierten Navigation Implementierungen standardbasierten Client gerendert Entwurfsmuster, die einen lokalen Cache der Navigationsknoten zu speichern. (Siehe **[suchbasierte clientseitiges Skripting](#using-search-driven-client-side-scripting)** in diesem Artikel.)

Diese Navigationsanbieter gibt es mehrere wichtige Vorteile: 
- Sie können im Allgemeinen auch mit Entwürfe schnell Seite.
- Sie sind äußerst skalierbar und leistungsfähige, da gerendert werden können ohne die Kosten Ressource (und die Aktualisierung im Hintergrund nach einem Timeout). 
- Diese Navigationsanbieter können mit verschiedenen Strategien, zwischen verschiedenen dynamic Data-Anbieter-einfache statische Konfigurationen Navigationsdaten abrufen. 

Ein Beispiel eines Datenanbieters ist eine **suchgesteuerte Navigation**, mit dessen Hilfe Sie Flexibilität für Navigationsknoten aufzählen und Einschränkung aus Sicherheitsgründen effizient behandeln können. 

Andere beliebten Optionen zum Erstellen von **benutzerdefinierten Navigationsanbieter**sind vorhanden. Überprüfen Sie [Lösungen für SharePoint Online-Portale Navigation](https://docs.microsoft.com/sharepoint/dev/solution-guidance/portal-navigation) zu weiteren Anleitung zum Erstellen einer benutzerdefinierten Navigationsanbieter.
  
## <a name="pros-and-cons-of-sharepoint-online-navigation-options"></a>Vor- und von SharePoint Online Nachteile Navigationsoptionen

In der folgenden Tabelle werden die vor- und Nachteile jeder Option zusammengefasst. 


|Verwaltete Navigation  |Strukturelle Navigation  |Suchgesteuerte Navigation  |Benutzerdefinierte Navigation-Anbieter  |
|---------|---------|---------|---------|
|Vorteile:<br/><br/>Einfach zu verwalten<br/>Empfohlene option<br/>     |Vorteile:<br/><br/>Einfach zu konfigurieren<br/>Sicherheitsoptimiert<br/>Automatisch aktualisiert, sobald Inhalt hinzugefügt wird<br/>|Vorteile<br/><br/>Sicherheitsoptimiert<br/>Automatische Aktualisierung beim Hinzufügen von Websites<br/>Schnelle Ladezeiten und lokal zwischengespeicherte Navigationsstruktur<br/>|Vorteile<br/><br/>Größere Auswahl bei der verfügbaren Optionen<br/>Laden von fast beim Zwischenspeichern wird ordnungsgemäß verwendet.<br/>Viele Optionen können auch mit schnell Seitenentwurf<br/>|
|Nachteile:<br/><br/>Keine automatische Aktualisierung zur Abbildung der Websitestruktur<br/>Leistung auswirkt, wenn die Einschränkung aus Sicherheitsgründen aktiviert ist<br/>|Nachteile:<br/><br/>**Nicht empfohlen**<br/>**Wirkt sich auf Leistung und Skalierbarkeit**<br/>**Unterliegen-Einschränkung**<br/>|Nachteile:<br/><br/>Keine Möglichkeit, Websites einfach anzuordnen<br/>Erfordert die Anpassung der Masterseite (technische Kenntnisse erforderlich)<br/>|Nachteile:<br/><br/>Benutzerdefinierte Entwicklung ist erforderlich<br/>Externe Datenquelle / Cache gespeichert ist erforderlich, z. B. Azure<br/>|

Die am besten geeignete Option für Ihre Website hängen auf Ihren Anforderungen Website und auf Ihrer Eignung. Wenn Sie eine skalierbare Out-of-Box-Navigationsanbieter möchten, ist verwaltete Navigation mit Einschränkung aus Sicherheitsgründen deaktiviert eine sehr gute Wahl. 

Die verwaltete Navigationsoption verwaltet werden kann Konfiguration umfassen nicht Anpassungsdateien Code, und es ist wesentlich schneller als strukturelle Navigation. Wenn Sie aus Sicherheitsgründen erfordern und mit einer benutzerdefinierten Gestaltungsvorlage vertraut sind und einige Funktionen in der Organisation, um die Änderungen zu verwalten, die in der Standardmasterseite für SharePoint Online auftreten können, kann dann die Option suchbasierte als bessere liefern Benutzer wünschen. Wenn Sie komplexere Bestimmungen unterliegen, möglicherweise eine benutzerdefinierte Navigationsanbieter die richtige Wahl. Strukturelle Navigation wird nicht empfohlen.

Schließlich ist es wichtig zu beachten, dass SharePoint Hinzufügen von zusätzlichen Navigationsanbieter und Funktionen für moderne SharePoint-websitearchitekturen einer Hierarchie von mehr vereinfachte und einem Hub-and-Spoke-Modell mit SharePoint Hubstandorte nutzen. Auf diese Weise können viele Szenarien erzielt werden muss, die keine die Verwendung des Features für SharePoint-Veröffentlichung erfordern, und diese Navigation Konfigurationen für Skalierbarkeit und Wartezeit in SharePoint Online optimiert sind. Beachten Sie, dass dasselbe Prinzip - vereinfachen die allgemeine Struktur Ihrer Website SharePoint-Veröffentlichung auf eine flacher Struktur, anwenden häufig mit Leistungseinbußen hilft und sowie skaliert werden. Dies bedeutet, dass anstelle einer einzelnen Websitesammlung mit Hunderten von Websites (Unterwebsites) ein besserer Ansatz ist viele Websitesammlungen mit sehr wenige Unterwebsites (Unterwebsites).


## <a name="using-managed-navigation-and-metadata-in-sharepoint-online"></a>Verwenden von verwalteten Navigation und Metadaten in SharePoint Online

Verwalteter Navigation ist eine andere Out-of-Box-Option, mit denen Sie die meisten dieselbe Funktionalität wie strukturelle Navigation neu erstellen. Verwalteter Metadaten kann konfiguriert werden, um die Einschränkung aus Sicherheitsgründen aktiviert oder deaktiviert haben. Bei der Konfiguration mit Einschränkung aus Sicherheitsgründen deaktiviert, ist verwalteter Navigation relativ effizient wie die Navigationslinks mit einer Konstante Anzahl von Serveranrufen geladen. Aktivieren der Security trimming, jedoch einige der Vorteile der verwalteten Navigation negiert und Kunden können auswählen, um eine benutzerdefinierte Navigation Lösungen für eine optimale Leistung und Skalierbarkeit zu erkunden.

Viele Websites erfordern keinen aus Sicherheitsgründen, wie oft die Navigationsstruktur für alle Benutzer der Website konsistent ist. Wenn die Einschränkung aus Sicherheitsgründen ist deaktiviert, und eine Verknüpfung zur Navigation, die nicht alle Benutzer Zugriff haben hinzugefügt wird, der Link zeigt immer noch jedoch führt zum Zugriff verweigert. Es ist kein Risiko des unbeabsichtigten Zugriff auf die Inhalte.

### <a name="how-to-implement-managed-navigation-and-the-results"></a>So implementieren Sie die verwaltete Navigation und die Ergebnisse

Es gibt mehrere Artikel auf Docs.Microsoft.com zu den Details der verwalteten Navigation, zum Beispiel, finden Sie unter [Übersicht über die verwaltete Navigation in SharePoint Server](https://docs.microsoft.com/sharepoint/administration/overview-of-managed-navigation).

Um die verwalteten Navigation zu implementieren, richten Sie Begriffe mit URLs, die die Navigationsstruktur der Website entspricht. Verwalteter Navigation kann auch manuell curated werden, um strukturelle Navigation in vielen Fällen zu ersetzen. Zum Beispiel:

![SharePoint Online Websitestruktur](media/SPONavOptionsListOfSites.png)

Das folgende Beispiel zeigt die Leistung der komplexen Navigation bei Verwendung der verwalteten Navigation.

![Leistung von komplexen Navigation mithilfe der verwalteten navigation](media/SPONavOptionsComplexNavPerf.png)

Verwalteten Navigation konsistent verwenden verbessert die Leistung im Vergleich zu den Ansatz strukturelle Navigation.
  
## <a name="using-structural-navigation-in-sharepoint-online"></a>Verwenden der strukturellen Navigation in SharePoint Online

Die Out-of-Box-Navigation standardmäßig verwendet und ist die einfachste Lösung Dies ist ein Kompromiss teurer Leistung als solche hat. Es muss keine Anpassung und einen technischen Benutzer kann auch problemlos Elemente hinzufügen, Ausblenden von Elementen und verwalten die Navigation auf der Seite Einstellungen. Dies ist jedoch auch True für die verwaltete Navigation, empfiehlt es verwaltete Navigation als verwenden, die auch auf einfache Weise verwaltet und gesteuert werden kann auch mit die Leistung verbessert.

![Strukturelle Navigation mit anzeigen Unterwebsites ausgewählt](media/SPONavOptionsStructuredShowSubsites.png)
  
### <a name="turning-on-structural-navigation-in-sharepoint-online"></a>Aktivieren der strukturellen Navigation in SharePoint Online

Erläutern, wie die Leistung in einer standard-SharePoint Online-Lösung mit strukturellen Navigation und anzeigen die Option Unterwebsites aktiviert. Es folgt ein Screenshot des Einstellungen finden Sie auf der Seite **Websiteeinstellungen** \> **Navigation**.
  
![Screenshot mit Unterwebsites](media/5b6a8841-34ed-4f61-b6d3-9d3e78d393e7.png)
  
### <a name="analyzing-structural-navigation-performance-in-sharepoint-online"></a>Analysieren der Leistung der strukturellen Navigation in SharePoint Online

Verwenden Sie die Leistung einer SharePoint-Seite zu analysieren, der Registerkarte **Netzwerks** die F12-Entwicklertools in Internet Explorer. 
  
![Screenshot mit Registerkarte "F12 Dev Tools-Netzwerk"](media/SPONavOptionsNetworks.png)
  
1. Klicken Sie auf der Registerkarte **Netzwerk** auf die ASPX-Seite, die geladen wird, und klicken Sie dann auf die Registerkarte **Details**.<br/> ![Screenshot der Detailregisterkarte](media/ad85cefb-7bc5-4932-b29c-25f61b4ceeb2.png)<br/>
2. Klicken Sie auf **Antwortheader**. <br/>![Screenshot der Registerkarte "Details"](media/c47770ac-5b2b-4941-9830-c57565dec4cc.png)<br/>SharePoint gibt einige nützliche Diagnoseinformationen in seiner Antwortheader zurück. 
3. Eine der nützlichsten Teile der Informationen ist **SPRequestDuration** , der Wert ist, der eine Anforderung an den Prozess auf dem Server die Zeitdauer in Millisekunden. Im folgenden Screenshot ist die **Unterwebsites anzeigen** für die strukturelle Navigation nicht aktiviert. Dies bedeutet, dass nur die Site Collection Verknüpfung in der globalen Navigation vorhanden ist:<br/>![Screenshot mit Ladezeiten als Anforderungsdauer](media/3422b2e8-15ec-4bb9-ba86-0965b6b49b01.png)<br/>
4. Der Schlüssel für **SPRequestDuration** hat einen Wert von 245 Millisekunden. Dies ist die Zeit die Anforderung zurückgegeben. Da nur ein Navigationselement auf der Website vorhanden ist, ist dies eine gute Richtlinie für ohne extra fette Navigation wie SharePoint Online ausführt. Der nächste Screenshot zeigt, wie in Unterwebsites Hinzufügen dieser Schlüssel auswirkt.<br/>![Screenshot mit einer Anforderungsdauer von 2.502 ms](media/618ee4e9-2ffa-4a22-b638-fa77b72292b8.png)<br/>
  
Hinzufügen von Unterwebsites wurde die Zeit Zeitaufwand für die angeforderte Seite für dieses Beispiel relativ einfach zurückzugebenden stark erweitert. Komplexe websitehierarchien, einschließlich der Seiten im Navigationsbereich und andere Konfiguration und Topologieoptionen können diese Auswirkung noch weiter drastisch erhöhen.

## <a name="using-search-driven-client-side-scripting"></a>Verwenden einer suchbasierten, clientseitigen Skripterstellung

Verwenden der Suchfunktion von können Sie die Indizes nutzen, die in den Hintergrund mit kontinuierliche Durchforstung basieren. Die Suchergebnisse werden aus dem Suchindex abgerufen, und die Ergebnisse sind Sicherheit gekürzt. Dies ist im Allgemeinen schneller als Out-of-Box Navigationsanbieter, wenn aus Sicherheitsgründen erforderlich ist. Mithilfe der Suche für die strukturelle Navigation, insbesondere dann, wenn eine komplexe Websitestruktur beschleunigt Seite Ladezeit erheblich. Der Hauptvorteil dieses über verwaltete Navigation ist, dass Sie aus Sicherheitsgründen profitieren.

Dieser Ansatz umfasst das Erstellen einer benutzerdefinierten Gestaltungsvorlage und ersetzen den Navigationscode Out-of-Box-mit benutzerdefinierten HTML-Code. Folgen Sie dieses Verfahren im folgenden Beispiel ersetzen den Navigationscode in der Datei `seattle.html`. In diesem Beispiel wird, öffnen Sie die `seattle.html` Datei, und Ersetzen Sie das ganze Element `id=”DeltaTopNavigation”` mit benutzerdefiniertem HTML-Code.

### <a name="example-replace-the-out-of-the-box-navigation-code-in-a-master-page"></a>Beispiel: Ersetzen Sie den Out-of-Box-Navigationscode in eine Gestaltungsvorlage

1.  Navigieren Sie zur Seite Websiteeinstellungen.
2.  Öffnen Sie durch Klicken auf **Masterseiten** den Masterseitenkatalog.
3.  Von hier aus können Sie über die Bibliotheks-navigieren und Laden Sie die Datei `seattle.master`.
4.  Bearbeiten Sie den Code mit einem Texteditor, und löschen Sie den Codeblock im folgenden Screenshot.<br/>![Löschen Sie den Codeblock dargestellt](media/SPONavOptionsDeleteCodeBlock.png)<br/>
5. Entfernen Sie den Code zwischen den `<SharePoint:AjaxDelta id=”DeltaTopNavigation”>` und `<\SharePoint:AjaxDelta>` tags und ersetzt ihn durch den folgenden Codeausschnitt:<br/>

```
<div id="loading">
  <!--Replace with path to loading image.-->
  <div style="background-image: url(''); height: 22px; width: 22px; ">
  </div>
</div>
<!-- Main Content-->
<div id="navContainer" style="display:none">
    <div data-bind="foreach: hierarchy" class="noindex ms-core-listMenu-horizontalBox">
        <a class="dynamic menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" data-bind="attr: { href: item.Url, title: item.Title }">
            <span class="menu-item-text" data-bind="text: item.Title">
            </span>
        </a>
        <ul id="menu" data-bind="foreach: $data.children" style="padding-left:20px">
            <li class="static dynamic-children level1">
                <a class="static dynamic-children menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" data-bind="attr: { href: item.Url, title: item.Title }">
               
                 <!-- ko if: children.length > 0-->
                    <span aria-haspopup="true" class="additional-background ms-navedit-flyoutArrow dynamic-children">
                        <span class="menu-item-text" data-bind="text: item.Title">
                        </span>
                    </span>
                <!-- /ko -->
                <!-- ko if: children.length == 0-->   
                    <span aria-haspopup="true" class="ms-navedit-flyoutArrow dynamic-children">
                        <span class="menu-item-text" data-bind="text: item.Title">
                        </span>
                    </span>
                <!-- /ko -->   
                </a>
               
                <!-- ko if: children.length > 0-->                                                       
                <ul id="menu"  data-bind="foreach: children;" class="dynamic  level2" >
                    <li class="dynamic level2">
                        <a class="dynamic menu-item ms-core-listMenu-item ms-displayInline  ms-navedit-linkNode" data-bind="attr: { href: item.Url, title: item.Title }">
         
          <!-- ko if: children.length > 0-->
          <span aria-haspopup="true" class="additional-background ms-navedit-flyoutArrow dynamic-children">
           <span class="menu-item-text" data-bind="text: item.Title">
           </span>
          </span>
           <!-- /ko -->
          <!-- ko if: children.length == 0-->
          <span aria-haspopup="true" class="ms-navedit-flyoutArrow dynamic-children">
           <span class="menu-item-text" data-bind="text: item.Title">
           </span>
          </span>                 
          <!-- /ko -->   
                        </a>
          <!-- ko if: children.length > 0-->
         <ul id="menu" data-bind="foreach: children;" class="dynamic level3" >
          <li class="dynamic level3">
           <a class="dynamic menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" data-bind="attr: { href: item.Url, title: item.Title }">
            <span class="menu-item-text" data-bind="text: item.Title">
            </span>
           </a>
          </li>
         </ul>
           <!-- /ko -->
                    </li>
                </ul>
                <!-- /ko -->
            </li>
        </ul>
    </div>
</div>
```
<br/>
6. Ersetzen Sie die URL in das Laden image Anchortag am Anfang, mit einem Link zu einem Bild laden in Ihrer Websitesammlung. Nachdem Sie die Änderungen vorgenommen haben, benennen Sie die Datei, und klicken Sie dann auf den Gestaltungsvorlagenkatalog hochladen. Dadurch wird eine neue Master-Datei generiert.<br/>
7. Dieser HTML-Code wird die grundlegende Markup, das von der Suchergebnisse aus JavaScript-Code aufgefüllt wird. Sie müssen den Code zum Ändern des Werts für Var Stamm bearbeiten = "site Websitesammlungs-URL", wie im folgenden Codeausschnitt veranschaulicht:<br/>

```
var root = “https://spperformance.sharepoint.com/sites/NavigationBySearch”;
```
<br/>
8. Die Ergebnisse werden in das Array self.nodes zugewiesen und eine Hierarchie der Objekte mit linq.js zuweisen die Ausgabe zu einem Array self.hierarchy basiert. Dieses Array ist das Objekt, das an den HTML-Code gebunden ist. Dies in der Funktion toggleView() erfolgt, indem Sie das Self-Objekt an die Funktion ko.applyBinding() übergeben.<br/>Dies führt dann Hierarchie Array folgenden HTML-Code gebunden werden:<br/>

```
<div data-bind=”foreach: hierarchy” class=”noindex ms-core-listMenu-horizontalBox”>
```

Der Ereignishandler für `mouseenter` und `mouseexit` werden hinzugefügt, um die Navigation auf oberster Ebene zum Verarbeiten der Unterwebsite Dropdownmenüs ausgeführt wird, in der `addEventsToElements()` Funktion.

In unserem Beispiel komplexen Navigation eine leere Seite laden, ohne das lokale Zwischenspeichern zeigt der Zeitaufwand für den Server aus der Vergleichstest strukturelle Navigation ein ähnliches Ergebnis als die verwaltete Navigation Ansatz abzurufenden verringern wurde.

### <a name="about-the-javascript-file"></a>Über die JavaScript-Datei...

Die gesamte JavaScript-Datei sieht wie folgt aus:

```
//Models and Namespaces
var SPOCustom = SPOCustom || {};
SPOCustom.Models = SPOCustom.Models || {}
SPOCustom.Models.NavigationNode = function () {

    this.Url = ko.observable("");
    this.Title = ko.observable("");
    this.Parent = ko.observable("");

};

var root = "https://spperformance.sharepoint.com/sites/NavigationBySearch";
var baseUrl = root + "/_api/search/query?querytext=";
var query = baseUrl + "'contentClass=\"STS_Web\"+path:" + root + "'&trimduplicates=false&rowlimit=300";

var baseRequest = {
    url: "",
    type: ""
};


//Parses a local object from JSON search result.
function getNavigationFromDto(dto) {
    var item = new SPOCustom.Models.NavigationNode();
    if (dto != undefined) {

        var webTemplate = getSearchResultsValue(dto.Cells.results, 'WebTemplate');

        if (webTemplate != "APP") {
            item.Title(getSearchResultsValue(dto.Cells.results, 'Title')); //Key = Title
            item.Url(getSearchResultsValue(dto.Cells.results, 'Path')); //Key = Path
            item.Parent(getSearchResultsValue(dto.Cells.results, 'ParentLink')); //Key = ParentLink
        }

    }
    return item;
}

function getSearchResultsValue(results, key) {

    for (i = 0; i < results.length; i++) {
        if (results[i].Key == key) {
            return results[i].Value;
        }
    }
    return null;
}

//Parse a local object from the serialized cache.
function getNavigationFromCache(dto) {
    var item = new SPOCustom.Models.NavigationNode();

    if (dto != undefined) {

        item.Title(dto.Title);
        item.Url(dto.Url);
        item.Parent(dto.Parent);
    }

    return item;
}

/* create a new OData request for JSON response */
function getRequest(endpoint) {
    var request = baseRequest;
    request.type = "GET";
    request.url = endpoint;
    request.headers = { ACCEPT: "application/json;odata=verbose" };
    return request;
};

/* Navigation Module*/
function NavigationViewModel() {
    "use strict";
    var self = this;
    self.nodes = ko.observableArray([]);
    self.hierarchy = ko.observableArray([]);;
    self.loadNavigatioNodes = function () {
        //Check local storage for cached navigation datasource.
        var fromStorage = localStorage["nodesCache"];
        if (false) {
            var cachedNodes = JSON.parse(localStorage["nodesCache"]);

            if (cachedNodes && timeStamp) {
                //Check for cache expiration. Currently set to 3 hrs.
                var now = new Date();
                var diff = now.getTime() - timeStamp;
                if (Math.round(diff / (1000 * 60 * 60)) < 3) {

                    //return from cache.
                    var cacheResults = [];
                    $.each(cachedNodes, function (i, item) {
                        var nodeitem = getNavigationFromCache(item, true);
                        cacheResults.push(nodeitem);
                    });

                    self.buildHierarchy(cacheResults);
                    self.toggleView();
                    addEventsToElements();
                    return;
                }
            }
        }
        //No cache hit, REST call required.
        self.queryRemoteInterface();
    };

    //Executes a REST call and builds the navigation hierarchy.
    self.queryRemoteInterface = function () {
        var oDataRequest = getRequest(query);
        $.ajax(oDataRequest).done(function (data) {
            var results = [];
            $.each(data.d.query.PrimaryQueryResult.RelevantResults.Table.Rows.results, function (i, item) {

                if (i == 0) {
                    //Add root element.
                    var rootItem = new SPOCustom.Models.NavigationNode();
                    rootItem.Title("Root");
                    rootItem.Url(root);
                    rootItem.Parent(null);
                    results.push(rootItem);
                }
                var navItem = getNavigationFromDto(item);
                results.push(navItem);
            });
            //Add to local cache
            localStorage["nodesCache"] = ko.toJSON(results);

            localStorage["nodesCachedAt"] = new Date().getTime();
            self.nodes(results);
            if (self.nodes().length > 0) {
                var unsortedArray = self.nodes();
                var sortedArray = unsortedArray.sort(self.sortObjectsInArray);

                self.buildHierarchy(sortedArray);
                self.toggleView();
                addEventsToElements();
            }
        }).fail(function () {
            //Handle error here!!
            $("#loading").hide();
            $("#error").show();
        });
    };
    self.toggleView = function () {
        var navContainer = document.getElementById("navContainer");
        ko.applyBindings(self, navContainer);
        $("#loading").hide();
        $("#navContainer").show();

    };
    //Uses linq.js to build the navigation tree.
    self.buildHierarchy = function (enumerable) {
        self.hierarchy(Enumerable.From(enumerable).ByHierarchy(function (d) {
            return d.Parent() == null;
        }, function (parent, child) {
            if (parent.Url() == null || child.Parent() == null)
                return false;
            return parent.Url().toUpperCase() == child.Parent().toUpperCase();
        }).ToArray());

        self.sortChildren(self.hierarchy()[0]);
    };


    self.sortChildren = function (parent) {

        // sjip processing if no children
        if (!parent || !parent.children || parent.children.length === 0) {
            return;
        }

        parent.children = parent.children.sort(self.sortObjectsInArray2);

        for (var i = 0; i < parent.children.length; i++) {
            var elem = parent.children[i];

            if (elem.children && elem.children.length > 0) {
                self.sortChildren(elem);
            }
        }
    };

    // ByHierarchy method breaks the sorting in chrome and firefix 
    // we need to resort  as ascending
    self.sortObjectsInArray2 = function (a, b) {
        if (a.item.Title() > b.item.Title())
            return 1;
        if (a.item.Title() < b.item.Title())
            return -1;
        return 0;
    };


    self.sortObjectsInArray = function (a, b) {
        if (a.Title() > b.Title())
            return -1;
        if (a.Title() < b.Title())
            return 1;
        return 0;
    }
}

//Loads the navigation on load and binds the event handlers for mouse interaction.
function InitCustomNav() {
    var viewModel = new NavigationViewModel();
    viewModel.loadNavigatioNodes();
}

function addEventsToElements() {
    //events.
      $("li.level1").mouseover(function () {
          var position = $(this).position();
          $(this).find("ul.level2").css({ width: 100, left: position.left + 10, top: 50 });
      })
   .mouseout(function () {
     $(this).find("ul.level2").css({  left: -99999, top: 0 });
   
    });
   
     $("li.level2").mouseover(function () {
          var position = $(this).position();
          console.log(JSON.stringify(position));
          $(this).find("ul.level3").css({ width: 100, left: position.left + 95, top:  position.top});
      })
   .mouseout(function () {
     $(this).find("ul.level3").css({  left: -99999, top: 0 });
    });
} _spBodyOnLoadFunctionNames.push("InitCustomNav");

``` 

Den oben aufgeführten Code Zusammenfassen der `jQuery $(document).ready` Funktion vorhanden ist ein `viewModel object` erstellt und dann die `loadNavigationNodes()` Funktion für dieses Objekt aufgerufen wird. Diese Funktion lädt entweder der zuvor erstellten Navigationshierarchie im lokalen Speicher des Clientbrowsers HTML5 gespeichert oder die Funktion ruft `queryRemoteInterface()`.

`QueryRemoteInterface()`erstellt eine Anforderung mithilfe der `getRequest()` -Funktion mit dem Abfragezeichenfolgen-Parameter weiter oben in das Skript definiert, und klicken Sie dann die Daten vom Server zurückgegeben. Diese Daten ist im Wesentlichen ein Array aller Websites in der Websitesammlung als Objekte zum Übertragen von Daten mit verschiedenen Eigenschaften dargestellt. 

Werden diese Daten analysiert in der zuvor definierten `SPO.Models.NavigationNode` Objekte, die verwenden `Knockout.js` sichtbare Eigenschaften für die Verwendung durch die Werte in der HTML-Code, die wir zuvor definierten Binden von Daten erstellen. 

Die Objekte sind, platzieren Sie dann in ein Ergebnisarray. Dieses Array wird in JSON mit Knockout analysiert und in den lokalen Browser Speicher für verbesserte Leistung auf zukünftige Seite Lasten gespeichert.

### <a name="benefits-of-this-approach"></a>Vorteile dieses Ansatzes

Ein wesentlicher Nutzen von [diesem Ansatz](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page) ist mithilfe von HTML5 lokalen Speicher, die Navigation lokal für den Benutzer das nächste Mal gespeichert wird die Seite zu laden. Wir erhalten Haupt-Leistungssteigerungen aus mithilfe der API für die Suche für die strukturelle Navigation. Allerdings dauert es einige Eignung ausführen und diese Funktionalität anpassen. 

In der [Beispiel-Implementierung](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page)werden die Websites in die gleiche Weise wie die strukturelle Out-of-Box-Navigation geordnet; alphabetischer Reihenfolge. Wenn Sie von dieser Reihenfolge abweichen, wäre es schwieriger zu entwickeln und zu verwalten. Darüber hinaus müssen diesem Ansatz Sie von der unterstützten Gestaltungsvorlagen abweichen. Wenn die benutzerdefinierte Gestaltungsvorlage nicht verwaltet werden, Ihrer Website wird verpassen out auf der Updates und Verbesserungen, die Microsoft die Gestaltungsvorlagen gemacht werden.

Die [über Code](#about-the-javascript-file) gelten die folgenden Abhängigkeiten:

- jQuery-http://jquery.com/
- KnockoutJS-http://knockoutjs.com/
- Linq.js - http://linqjs.codeplex.com/, oder github.com/neuecc/linq.js

Die aktuelle Version von LinqJS enthält nicht die ByHierarchy-Methode verwendet, die im obigen Code und unterbricht den Navigationscode. Um dieses Problem zu beheben, fügen Sie die folgende Methode zur Datei Linq.js vor der Zeile `Flatten: function ()`.

```
ByHierarchy: function(firstLevel, connectBy, orderBy, ascending, parent) {
     ascending = ascending == undefined ? true : ascending;
     var orderMethod = ascending == true ? 'OrderBy' : 'OrderByDescending';
     var source = this;
     firstLevel = Utils.CreateLambda(firstLevel);
     connectBy = Utils.CreateLambda(connectBy);
     orderBy = Utils.CreateLambda(orderBy);
    
     //Initiate or increase level
     var level = parent === undefined ? 1 : parent.level + 1;

    return new Enumerable(function() {
         var enumerator;
         var index = 0;

        var createLevel = function() {
                 var obj = {
                     item: enumerator.Current(),
                     level : level
                 };
                 obj.children = Enumerable.From(source).ByHierarchy(firstLevel, connectBy, orderBy, ascending, obj);
                 if (orderBy !== undefined) {
                     obj.children = obj.children[orderMethod](function(d) {
                         return orderBy(d.item); //unwrap the actual item for sort to work
                     });
                 }
                 obj.children = obj.children.ToArray();
                 Enumerable.From(obj.children).ForEach(function(child) {
                     child.getParent = function() {
                         return obj;
                     };
                 });
                 return obj;
             };

        return new IEnumerator(

        function() {
             enumerator = source.GetEnumerator();
         }, function() {
             while (enumerator.MoveNext()) {
                 var returnArr;
                 if (!parent) {
                     if (firstLevel(enumerator.Current(), index++)) {
                         return this.Yield(createLevel());
                     }

                } else {
                     if (connectBy(parent.item, enumerator.Current(), index++)) {
                         return this.Yield(createLevel());
                     }
                 }
             }
             return false;
         }, function() {
             Utils.Dispose(enumerator);
         })
     });
 },

```
  
## <a name="related-topics"></a>Verwandte Themen

[Übersicht über die verwaltete Navigation in SharePoint Server](https://docs.microsoft.com/sharepoint/administration/overview-of-managed-navigation)

