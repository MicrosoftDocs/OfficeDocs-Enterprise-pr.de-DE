---
title: Navigationsoptionen für SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: adb92b80-b342-4ecb-99a1-da2a2b4782eb
description: In diesem Artikel werden Navigations Options Websites beschrieben, in denen SharePoint Publishing in SharePoint Online aktiviert ist. Die Auswahl und Konfiguration der Navigation wirkt sich erheblich auf die Leistung und Skalierbarkeit von Websites in SharePoint Online aus.
ms.openlocfilehash: 9bf2010000f14b173b63574fab4ee77cb772b3f4
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "34069941"
---
# <a name="navigation-options-for-sharepoint-online"></a>Navigationsoptionen für SharePoint Online

In diesem Artikel werden Navigations Options Websites beschrieben, in denen SharePoint Publishing in SharePoint Online aktiviert ist. Die Auswahl und Konfiguration der Navigation wirkt sich erheblich auf die Leistung und Skalierbarkeit von Websites in SharePoint Online aus.

## <a name="overview"></a>Übersicht

Die Konfiguration des Navigations Anbieters kann sich erheblich auf die Leistung für den gesamten Standort auswirken, und es muss sorgfältig überlegt werden, einen Navigationsanbieter und eine Konfiguration auszuwählen, die für die Anforderungen einer SharePoint-Website effektiv skaliert werden. Es gibt zwei out-of-the-Box-Navigationsanbieter sowie benutzerdefinierte Navigations Implementierungen.

Die erste Option, [**verwaltete (Metadaten) Navigation**](#using-managed-navigation-and-metadata-in-sharepoint-online), wird empfohlen und ist eine der Standardoptionen in SharePoint Online; Es wird jedoch empfohlen, dass das Sicherheits Trimmen deaktiviert ist, sofern nicht erforderlich. Die Einschränkung der Sicherheit ist als Standardeinstellung für diesen Navigationsanbieter aktiviert. für viele Websites ist jedoch der Aufwand an Sicherheitseinschränkungen nicht erforderlich, da Navigationselemente häufig für alle Benutzer der Website konsistent sind. Bei der empfohlenen Konfiguration zur Deaktivierung des Sicherheits Trimmens erfordert dieser Navigationsanbieter keine Aufzählung der Websitestruktur und ist hoch skalierbar mit akzeptablen Leistungseinbußen.

Die zweite Option, [**strukturelle Navigation**](#using-structural-navigation-in-sharepoint-online), **ist keine empfohlene Navigationsoption in SharePoint Online**. Dieser Navigationsanbieter wurde für eine lokale Topologie entwickelt, die nur in SharePoint Online unterstützt werden kann. Während es einige zusätzliche Funktionen im Vergleich zu anderen Navigationsoptionen bietet, werden diese Features, einschließlich der Sicherheits Kürzung und der Aufzählung der Websitestruktur, zu Kosten von übermäßigen Server aufrufen und Auswirkungen auf die Skalierbarkeit und Leistung bei der Verwendung. Websites, die eine Struktur Navigation verwenden und übermäßige Ressourcen nutzen, können möglicherweise eingeschränkt werden.

Neben den Out-of-the-Box-Navigations Anbietern haben viele Kunden erfolgreich Alternative benutzerdefinierte Navigations Implementierungen implementiert. Eine allgemeine Klasse benutzerdefinierter Navigations Implementierungen umfasst Client gerenderte Entwurfsmuster, die einen lokalen Cache von Navigationsknoten speichern. (Siehe **[Such gesteuerte clientseitige Skripterstellung](#using-search-driven-client-side-scripting)** in diesem Artikel.)

Diese Navigationsanbieter haben eine Reihe von wichtigen Vorteilen: 
- Sie funktionieren im Allgemeinen gut mit reaktionsfähigen Seitendesigns.
- Sie sind extrem skalierbar und leistungsfähig, da Sie ohne Ressourcenkosten gerendert werden können (und nach einem Timeout im Hintergrund aktualisieren). 
- Diese Navigationsanbieter können Navigationsdaten mithilfe verschiedener Strategien abrufen, von einfachen statischen Konfigurationen bis hin zu verschiedenen dynamischen Datenanbietern. 

Ein Beispiel für einen Datenanbieter ist die Verwendung einer **Such gesteuerten Navigation**, die Flexibilität beim Aufzählen der Navigationsknoten und beim effizienten Umgang mit dem Sicherheits Trimmen ermöglicht. 

Es gibt weitere beliebte Optionen zum Erstellen **benutzerdefinierter Navigationsanbieter**. Weitere Informationen zum Erstellen eines benutzerdefinierten Navigations Anbieters finden Sie unter [Navigation Solutions for SharePoint Online Portals](https://docs.microsoft.com/sharepoint/dev/solution-guidance/portal-navigation) .
  
## <a name="pros-and-cons-of-sharepoint-online-navigation-options"></a>Vor-und Nachteile von SharePoint Online-Navigationsoptionen

In der folgenden Tabelle werden die vor-und Nachteile der einzelnen Optionen zusammengefasst. 


|Verwaltete Navigation  |Strukturelle Navigation  |Such gesteuerte Navigation  |Anbieter für die benutzerdefinierte Navigation  |
|---------|---------|---------|---------|
|Experten<br/><br/>Einfache Wartung<br/>Empfohlene Option<br/>     |Experten<br/><br/>Einfach zu konfigurieren<br/>Getrimmte Sicherheit<br/>Automatisch aktualisiert, wenn Inhalt hinzugefügt wird<br/>|Experten<br/><br/>Getrimmte Sicherheit<br/>Wird automatisch aktualisiert, wenn Websites hinzugefügt werden<br/>Schnelle Ladezeit und lokal zwischengespeicherte Navigationsstruktur<br/>|Experten<br/><br/>Breitere Auswahl an verfügbaren Optionen<br/>Schnelles Laden bei richtiger Zwischenspeicherung<br/>Viele Optionen funktionieren gut mit responsive Page Design<br/>|
|Nachteile<br/><br/>Nicht automatisch aktualisiert, um die Websitestruktur widerzuspiegeln<br/>Auswirkungen auf die Leistung, wenn das Sicherheits Trimmen aktiviert ist<br/>|Nachteile<br/><br/>**Nicht empfohlen**<br/>**Auswirkungen auf Leistung und Skalierbarkeit**<br/>**Einschränkungs Einschränkungen**<br/>|Nachteile<br/><br/>Keine Möglichkeit zum einfachen Sortieren von Websites<br/>Erfordert die Anpassung der Gestaltungsvorlage (technische Fertigkeiten erforderlich)<br/>|Nachteile<br/><br/>Benutzerdefinierte Entwicklung ist erforderlich<br/>Die externe Datenquelle/der gespeicherte Cache wird benötigt, beispielsweise Azure.<br/>|

Die am besten geeignete Option für Ihre Website hängt von Ihren Website Anforderungen und ihren technischen Funktionen ab. Wenn Sie einen skalierbaren, out-of-Box-Navigationsanbieter wünschen, ist die verwaltete Navigation mit deaktiviertem Sicherheits Trimmen eine sehr gute Option. 

Die Option für die verwaltete Navigation kann über die Konfiguration verwaltet werden, beinhaltet keine Code Anpassungsdateien und ist wesentlich schneller als die strukturelle Navigation. Wenn Sie Sicherheits Kürzung benötigen und über eine benutzerdefinierte Gestaltungsvorlage verfügen und in der Organisation die Möglichkeit haben, die Änderungen, die in der standardgestaltungsvorlage für SharePoint Online auftreten können, zu verwalten, kann die Such gesteuerte Option zu einer besseren Benutzerfreundlichkeit. Wenn Sie komplexere Anforderungen haben, ist möglicherweise ein benutzerdefinierter Navigationsanbieter die richtige Wahl. Die strukturelle Navigation wird nicht empfohlen.

Schließlich ist zu beachten, dass SharePoint zusätzliche Navigationsanbieter und-Funktionen für moderne SharePoint-Website Architekturen hinzufügt, die eine vereinfachte Websitehierarchie und ein Hub-and-Spoke-Modell mit SharePoint-Hub-Websites nutzen. Dadurch können viele Szenarien erreicht werden, die nicht die Verwendung des SharePoint-Veröffentlichungsfeatures erfordern, und diese Navigations Konfigurationen sind für Skalierbarkeit und Latenz in SharePoint Online optimiert. Beachten Sie, dass die Anwendung desselben Prinzips – Vereinfachung der Gesamtstruktur Ihrer SharePoint-Veröffentlichungswebsite in einer flachen Struktur – häufig auch die Gesamtleistung und Skalierung unterstützt. Das bedeutet, dass anstelle einer einzelnen Websitesammlung mit Hunderten von Websites (Unterwebs) ein besserer Ansatz für viele Websitesammlungen mit sehr wenigen Unterwebsites (Unterwebs) besteht.


## <a name="using-managed-navigation-and-metadata-in-sharepoint-online"></a>Verwenden von verwalteter Navigation und Metadaten in SharePoint Online

Die verwaltete Navigation ist eine weitere out-of-the-Box-Option, die Sie verwenden können, um die meisten der gleichen Funktionen wie die strukturelle Navigation neu zu erstellen. Verwaltete Metadaten können so konfiguriert werden, dass die Sicherheits Kürzung aktiviert oder deaktiviert ist. Bei deaktivierter Sicherheits Kürzung ist die verwaltete Navigation ziemlich effizient, da Sie alle Navigationslinks mit einer Konstanten Anzahl von Server aufrufen lädt. Das Aktivieren der Sicherheits Kürzung negiert jedoch einige Vorteile der verwalteten Navigation, und Kunden können sich für eine optimale Leistung und Skalierbarkeit für eine der benutzerdefinierten Navigationslösungen entscheiden.

Für viele Websites ist keine Sicherheits Kürzung erforderlich, da die Navigationsstruktur häufig für alle Benutzer der Website konsistent ist. Wenn die Sicherheits Kürzung deaktiviert ist und der Navigation ein Link hinzugefügt wird, auf den nicht alle Benutzer zugreifen können, wird die Verknüpfung weiterhin angezeigt, führt jedoch zu einer Meldung, dass der Zugriff verweigert wird. Es besteht kein Risiko für versehentlichen Zugriff auf den Inhalt.

### <a name="how-to-implement-managed-navigation-and-the-results"></a>Implementieren der verwalteten Navigation und der Ergebnisse

Es gibt mehrere Artikel über docs.Microsoft.com zu den Details der verwalteten Navigation, beispielsweise siehe [Übersicht über die verwaltete Navigation in SharePoint Server](https://docs.microsoft.com/sharepoint/administration/overview-of-managed-navigation).

Um die verwaltete Navigation zu implementieren, richten Sie Begriffe mit URLs ein, die der Navigationsstruktur der Website entsprechen. Die verwaltete Navigation kann sogar manuell kuratiert werden, um die strukturelle Navigation in vielen Fällen zu ersetzen. Zum Beispiel:

![SharePoint Online-Websitestruktur](media/SPONavOptionsListOfSites.png)

Das folgende Beispiel zeigt die Leistung der komplexen Navigation mithilfe der verwalteten Navigation.

![Leistung der komplexen Navigation mithilfe der verwalteten Navigation](media/SPONavOptionsComplexNavPerf.png)

Die Verwendung der verwalteten Navigation verbessert die Leistung im Vergleich zum strukturellen Navigations Ansatz.
  
## <a name="using-structural-navigation-in-sharepoint-online"></a>Verwenden der strukturellen Navigation in SharePoint Online

Hierbei handelt es sich um die standardmäßig verwendete Navigation, die die einfachste Lösung ist, aber als solche eine kostspielige Leistungssteigerung zur Folge hat. Sie erfordert keine Anpassung, und ein nicht technischer Benutzer kann problemlos Elemente hinzufügen, Elemente ausblenden und die Navigation auf der Einstellungsseite verwalten. Dies gilt aber auch für die verwaltete Navigation, daher empfiehlt es sich, die verwaltete Navigation zu verwenden, da dies auch mit höherer Leistung problemlos verwaltet und gesteuert werden kann.

![Strukturelle Navigation mit ausgewählten Unterwebsites anzeigen](media/SPONavOptionsStructuredShowSubsites.png)
  
### <a name="turning-on-structural-navigation-in-sharepoint-online"></a>Aktivieren der strukturellen Navigation in SharePoint Online

Erläutern Sie, wie die Leistung in einer standardmäßigen SharePoint Online-Lösung mit struktureller Navigation und der Option Unterwebsites anzeigen aktiviert ist. Nachfolgend finden Sie einen Screenshot der Einstellungen auf der Seite **Websiteeinstellungen** \> **Navigation**.
  
![Screenshot mit Unterwebsites](media/5b6a8841-34ed-4f61-b6d3-9d3e78d393e7.png)
  
### <a name="analyzing-structural-navigation-performance-in-sharepoint-online"></a>Analysieren der Leistung der strukturellen Navigation in SharePoint Online

Um die Leistung einer SharePoint-Seite zu analysieren, verwenden Sie die Registerkarte **Netzwerk** der F12-Entwicklertools in Internet Explorer. 
  
![Screenshot mit der Registerkarte "F12 dev Tools Network"](media/SPONavOptionsNetworks.png)
  
1. Klicken Sie auf der Registerkarte **Netzwerk** auf die ASPX-Seite, die geladen wird, und klicken Sie dann auf die Registerkarte **Details** .<br/> ![Screenshot mit der Registerkarte "Details"](media/ad85cefb-7bc5-4932-b29c-25f61b4ceeb2.png)<br/>
2. Klicken Sie auf **Antwort Kopfzeilen**. <br/>![Screenshot der Registerkarte "Details"](media/c47770ac-5b2b-4941-9830-c57565dec4cc.png)<br/>SharePoint gibt einige nützliche Diagnoseinformationen in den Antwortheadern zurück. 
3. Eine der nützlichsten Informationen ist **SPRequestDuration** , bei dem es sich um den Wert in Millisekunden handelt, der angibt, wie lange eine Anforderung zur Verarbeitung auf dem Server dauerte. Im folgenden Screenshot zeigen Sie, dass unter **Websites** für die strukturelle Navigation deaktiviert ist. Dies bedeutet, dass es nur den Link Websitesammlung in der globalen Navigation gibt:<br/>![Screenshot mit Ladezeiten als Anforderungsdauer](media/3422b2e8-15ec-4bb9-ba86-0965b6b49b01.png)<br/>
4. Der **SPRequestDuration** -Schlüssel hat einen Wert von 245 Millisekunden. Dies stellt die Zeit für die Rückgabe der Anforderung dar. Da es nur ein Navigationselement auf der Website gibt, ist dies ein guter Benchmark für die Leistung von SharePoint Online ohne starke Navigation. Der nächste Screenshot zeigt, wie sich das Hinzufügen in den Unterwebsites auf diesen Schlüssel auswirkt.<br/>![Screenshot mit einer Anforderungsdauer von 2502 MS](media/618ee4e9-2ffa-4a22-b638-fa77b72292b8.png)<br/>
  
Durch das Hinzufügen der Unterwebsites wurde die Zeitdauer für die Rückgabe der Seitenanforderung für diese relativ einfache Beispielwebsite erheblich erhöht. Komplexe Websitehierarchien, einschließlich Seiten in der Navigation und andere Konfigurations-und Topologie-Optionen, können diese Auswirkungen deutlich erhöhen.

## <a name="using-search-driven-client-side-scripting"></a>Verwenden von Such gesteuerten clientseitigen Skripts

Mithilfe der Suche können Sie die Indizes nutzen, die im Hintergrund mithilfe der fortlaufenden Durchforstung aufgebaut werden. Die Suchergebnisse werden aus dem Suchindex abgerufen, und die Ergebnisse werden mit Sicherheit gekürzt. Dies ist im Allgemeinen schneller als bei der bereitgestellten Sicherheitseinschränkung. Die Verwendung der Suche für die strukturelle Navigation, insbesondere bei einer komplexen Websitestruktur, beschleunigt die Ladezeit erheblich. Der Hauptvorteil dieser über die verwaltete Navigation ist, dass Sie von Sicherheit Kürzung profitieren.

Dieser Ansatz umfasst das Erstellen einer benutzerdefinierten Gestaltungsvorlage und das Ersetzen des vordefinierten Navigations Codes durch benutzerdefinierten HTML-Code. Führen Sie die im folgenden Beispiel beschriebenen Schritte aus, um den Navigationscode in der Datei `seattle.html`zu ersetzen. In diesem Beispiel öffnen Sie die `seattle.html` Datei und ersetzen das gesamte-Element `id=”DeltaTopNavigation”` durch benutzerdefinierten HTML-Code.

### <a name="example-replace-the-out-of-the-box-navigation-code-in-a-master-page"></a>Beispiel: Ersetzen Sie den Out-of-the-Box-Navigationscode auf einer Gestaltungsvorlage.

1.  Navigieren Sie zur Seite Websiteeinstellungen.
2.  Öffnen Sie den gestaltungsvorlagenkatalog, indem Sie auf **Masterseiten**klicken.
3.  Von hier aus können Sie durch die Bibliothek navigieren und die Datei `seattle.master`herunterladen.
4.  Bearbeiten Sie den Code mit einem Text-Editor, und löschen Sie den Codeblock im folgenden Screenshot.<br/>![Löschen des angezeigten Codeblocks](media/SPONavOptionsDeleteCodeBlock.png)<br/>
5. Entfernen Sie den Code zwischen `<SharePoint:AjaxDelta id=”DeltaTopNavigation”>` den `<\SharePoint:AjaxDelta>` und-Tags, und ersetzen Sie ihn durch den folgenden Ausschnitt:<br/>

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
6. Ersetzen Sie die URL im Tag "Loading Image Anchor" am Anfang mit einem Link zu einem Ladebild in Ihrer Websitesammlung. Nachdem Sie die Änderungen vorgenommen haben, benennen Sie die Datei um, und laden Sie Sie dann in den gestaltungsvorlagenkatalog hoch. Dadurch wird eine neue Master-Datei generiert.<br/>
7. Dieser HTML-Code ist das grundlegende Markup, das von den Suchergebnissen ausgefüllt wird, die von JavaScript-Quellcode zurückgegeben werden. Sie müssen den Code bearbeiten, um den Wert für var root = "Website Sammlungs-URL" wie im folgenden Codeausschnitt gezeigt zu ändern:<br/>

```
var root = “https://spperformance.sharepoint.com/sites/NavigationBySearch”;
```
<br/>
8. Die Ergebnisse werden dem Self. Nodes-Array zugewiesen, und eine Hierarchie besteht aus den Objekten mithilfe von LINQ. js, die die Ausgabe einem Array Self. Hierarchy zuweisen. Dieses Array ist das Objekt, das an den HTML-Code gebunden ist. Dies erfolgt in der toggleView ()-Funktion durch Übergeben des Self-Objekts an die ko. applyBinding ()-Funktion.<br/>Dadurch wird das Hierarchie Array an den folgenden HTML-Code gebunden:<br/>

```
<div data-bind=”foreach: hierarchy” class=”noindex ms-core-listMenu-horizontalBox”>
```

Die Ereignishandler für `mouseenter` und `mouseexit` werden der Navigation auf oberster Ebene hinzugefügt, um die Dropdownmenüs Unterwebsite zu behandeln, die in der `addEventsToElements()` Funktion ausgeführt werden.

In unserem Beispiel für eine komplexe Navigation zeigt ein neuer seitenladevorgang ohne lokale Zwischenspeicherung an, wie lange der Server aufgrund der Benchmark-Struktur Navigation gekürzt wurde, um ein ähnliches Ergebnis wie beim verwalteten Navigations Ansatz zu erzielen.

### <a name="about-the-javascript-file"></a>Informationen zur JavaScript-Datei...

Die gesamte JavaScript-Datei lautet wie folgt:

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

Zum Zusammenfassen des oben gezeigten Codes `jQuery $(document).ready` in der Funktion gibt `viewModel object` es eine erstellte und `loadNavigationNodes()` dann die Funktion für dieses Objekt aufgerufen wird. Diese Funktion lädt die zuvor erstellte Navigationshierarchie, die im lokalen HTML5-Speicher des Clientbrowsers gespeichert ist, oder ruft die `queryRemoteInterface()`Funktion auf.

`QueryRemoteInterface()`erstellt eine Anforderung mithilfe der `getRequest()` -Funktion mit dem zuvor im Skript definierten Abfrageparameter und gibt dann Daten vom Server zurück. Diese Daten sind im Wesentlichen ein Array aller Websites in der Websitesammlung, die als datentransferobjekte mit verschiedenen Eigenschaften dargestellt werden. 

Diese Daten werden dann in die zuvor definierten `SPO.Models.NavigationNode` Objekte analysiert, die `Knockout.js` zum Erstellen von beobachtbaren Eigenschaften für die Verwendung durch Datenbindung der Werte in den zuvor definierten HTML-Code verwenden. 

Die Objekte werden dann in einem Ergebnisarray platziert. Dieses Array wird in JSON mithilfe von Knockout analysiert und im lokalen Browser Speicher gespeichert, um die Leistung bei zukünftigen Seitenlasten zu verbessern.

### <a name="benefits-of-this-approach"></a>Vorteile dieses Ansatzes

Ein wesentlicher Vorteil [dieses](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page) Ansatzes besteht darin, dass die Navigation lokal für den Benutzer gespeichert wird, wenn Sie die Seite das nächste Mal laden. Bei der Verwendung der Such-API für die strukturelle Navigation werden wichtige Leistungsverbesserungen erzielt. Es sind jedoch einige technische Funktionen zum Ausführen und Anpassen dieser Funktionalität erforderlich. 

In der [Beispielimplementierung](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page)werden die Websites auf die gleiche Weise wie die Out-of-the-Box-Struktur Navigation sortiert; alphabetische Reihenfolge. Wenn Sie von dieser Reihenfolge abweichen möchten, wäre es komplizierter zu entwickeln und zu warten. Außerdem müssen Sie von den unterstützten Gestaltungsvorlagen abweichen. Wenn die benutzerdefinierte Gestaltungsvorlage nicht verwaltet wird, verpassen Ihre Website Updates und Verbesserungen, die von Microsoft an den Gestaltungsvorlagen vorgenommen werden.

Der [obige Code](#about-the-javascript-file) weist die folgenden Abhängigkeiten auf:

- jQueryhttp://jquery.com/
- KnockoutJS -http://knockoutjs.com/
- LINQ. js- http://linqjs.codeplex.com/oder GitHub.com/neuecc/LINQ.js

Die aktuelle Version von LinqJS enthält nicht die im obigen Code verwendete ByHierarchy-Methode und unterbricht den Navigationscode. Um dies zu beheben, fügen Sie die folgende Methode zur Datei "LINQ. js" `Flatten: function ()`vor der Leitung hinzu.

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

