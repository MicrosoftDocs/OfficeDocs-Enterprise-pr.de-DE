---
title: Navigationsoptionen für SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 6/27/2018
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: adb92b80-b342-4ecb-99a1-da2a2b4782eb
description: In diesem Artikel wird beschrieben, wie die Seitenladezeiten für SharePoint Online zu verbessern, verwaltete Navigation oder suchgesteuerte Navigation im klassischen Veröffentlichung verwenden.
ms.openlocfilehash: 6b2ee613d0cc6a6df92eb9b53374087a0ac2e5b7
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540988"
---
# <a name="navigation-options-for-sharepoint-online"></a>Navigationsoptionen für SharePoint Online

In diesem Artikel wird beschrieben, wie die Seitenladezeiten für SharePoint Online zu verbessern, verwaltete Navigation oder suchgesteuerte Navigation im klassischen Veröffentlichung verwenden.
  
SharePoint Online mit klassischen Veröffentlichung aktiviert hat zwei Navigationsbereiche. Globale Navigation und aktuelle Navigation.
  
Globale Navigation ist im Menü der oberen Navigationsleiste während aktuelle Navigation auf der Seite oder im Kontext links/rechts Navigation hängt von der Sprachkonfiguration und Gestaltungsvorlage verwendet wird.
  
Navigation kann für das gesamte Portal Leistung beeinträchtigen, wie es häufig für die gesamte Portal Verwendung konfiguriert ist und daher ein wichtiger Bestandteil einer SharePoint-Website ist.
  
Strukturelle Navigation ist nicht die Navigationsoption empfohlene in SharePoint Online, wie es für eine lokalen-Topologie mit Einschränkung aus Sicherheitsgründen entwickelt wurde und Design bewirkt, dass aufgrund einer Anrufe und wirkt sich auf Leistung, wenn sie verwendet wird.
  
Dass Entwurf geändert hat, mit der Einführung von modernen SharePoint-Websites, in denen modernen verfügt über eine vereinfachte vereinfachte Websitehierarchie. Dies wurde mit einer vereinfachten Hierarchie Navigation vereinfacht, die Leistungsprobleme im Zusammenhang mit der Navigation gelöscht wurde.
  
Es gibt zwei Optionen für die wichtigsten Out-of-Box Websitenavigation in SharePoint als auch eine dritte, benutzerdefinierte, suchbasierte Ansatz. Alternativ ist auch häufig Option und eine vierte eine benutzerdefinierte Navigation-Datenanbieter erstellen. Überprüfen Sie [Navigation Lösungen für SharePoint Online-Portale](https://docs.microsoft.com/en-us/sharepoint/dev/solution-guidance/portal-navigation) Hinweise auf eine benutzerdefinierte Navigationsanbieter. 
  
Jede Option hat vor- und Nachteile, wie in der folgenden Tabelle beschrieben.
  
|**Strukturelle Navigation**|**Verwaltete Navigation**|**Suchgesteuerte Navigation**||**Benutzerdefinierte Navigation-Anbieter**|
|:-----|:-----|:-----|:-----|:-----|
| Vorteile:  <br/>  Einfach zu konfigurieren  <br/>  Sicherheitskürzung  <br/>  Automatische Aktualisierung beim Hinzufügen von Websites  <br/> | Vorteile:  <br/>  Einfach zu verwalten  <br/>  Empfohlene option  <br/> | Vorteile:  <br/>  Sicherheitskürzung  <br/>  Automatische Aktualisierung beim Hinzufügen von Websites  <br/>  Schnelle Ladezeiten und lokal zwischengespeicherte Navigationsstruktur  <br/> || Vorteile  <br/>    <br/>  Größere Auswahl / Optionen zur Verfügung  <br/>  Laden von fast beim Zwischenspeichern wird ordnungsgemäß verwendet.  <br/> |
| Nachteile:  <br/> **Nicht empfohlen** <br/> **Auf die Leistung auswirkt** <br/> | Nachteile:  <br/>  Keine automatische Aktualisierung zur Abbildung der Websitestruktur  <br/>  Leistung auswirkt, wenn die Einschränkung aus Sicherheitsgründen aktiviert ist  <br/> | Nachteile:  <br/>  Keine Möglichkeit, Websites einfach anzuordnen  <br/>  Erfordert die Anpassung der Masterseite (technische Kenntnisse erforderlich)  <br/> || Nachteile:  <br/>  Benutzerdefinierte Entwicklung ist erforderlich  <br/>  Externe Datenquelle / Cache gespeichert ist erforderlich, z. B. Azure  <br/> |
   
Die am besten geeignete Option für Ihre Website hängen auf Ihren Anforderungen Website und auf Ihrer Eignung. Wenn Sie eine benutzerdefinierte Gestaltungsvorlage mit vertraut sind und einige Funktionen in der Organisation, um die Änderungen zu verwalten, die die Standardgestaltungsvorlage für SharePoint Online auftreten, erzeugt die Option suchbasierte die beste benutzerumgebung. Wenn Sie einen einfachen Kompromiss zwischen die strukturelle Out-of-Box-Navigation und Suche möchten, ist die verwaltete Navigation eine sehr gute Wahl. Die Option verwaltete Navigation über verwaltet Konfiguration umfassen nicht Anpassungsdateien Code, und es ist wesentlich schneller als die strukturelle Out-of-Box-Navigation.
  
Die allgemeine Struktur der klassische Portal ähnlich wie in modernem vereinfachen, unterstützt die allgemeine Leistung und Skalierung sowie. Dies bedeutet, der anstelle einer einzelnen Websitesammlung mit Hunderten / Tausende von Standorten (Unterwebsites), einen besseren Ansatz besteht darin, zahlreiche Websitesammlungen mit sehr wenige Unterwebsites (Unterwebsites).
  
Dies bietet zusätzliche Optionen für die Skalierung im Dienst, vermeidet eine große Datenbank Inbetriebnahme alle Inhalte und letztlich größere Flexibilität für Navigation und größerer Sicherheit.
  
## <a name="using-structural-navigation-in-sharepoint-online"></a>Verwenden der strukturellen Navigation in SharePoint Online

Die Out-of-Box-Navigation standardmäßig verwendet und ist die einfachste Lösung Dies ist ein Kompromiss teurer Leistung als solche hat. Es muss keine Anpassung und einen technischen Benutzer kann auch problemlos Elemente hinzufügen, Ausblenden von Elementen und verwalten die Navigation auf der Seite Einstellungen. Hierbei handelt es sich jedoch auch True für die verwaltete Navigation, daher wird empfohlen, verwaltete Navigation als, kann auch auf einfache Weise werden verwaltet und gesteuert sowie.
  
### <a name="turning-on-structural-navigation-in-sharepoint-online"></a>Aktivieren der strukturellen Navigation in SharePoint Online

Erläutern, wie die Leistung in einer standard-SharePoint Online-Lösung mit strukturellen Navigation und anzeigen die Option Unterwebsites aktiviert. Im folgenden ist ein Screenshot Einstellungen finden Sie auf der Seite **Websiteeinstellungen** \> **Navigation**.
  
![Screenshot mit Unterwebsites](media/5b6a8841-34ed-4f61-b6d3-9d3e78d393e7.png)
  
### <a name="analyzing-structural-navigation-performance-in-sharepoint-online"></a>Analysieren der Leistung der strukturellen Navigation in SharePoint Online

Zum Analysieren der Leistung einer SharePoint-Seite verwenden Sie die Registerkarte **Netzwerk** der F12-Entwicklertools in Internet Explorer. 
  
![Screenshot mit Registerkarte "F12 Dev Tools-Netzwerk"](media/e2aed8af-0843-487a-8b68-4f5260a2685e.png)
  
Klicken Sie auf der Registerkarte **Netzwerk** auf die ASPX-Seite, die geladen wird, und klicken Sie dann auf die Registerkarte **Details**. 
  
![Screenshot der Detailregisterkarte](media/ad85cefb-7bc5-4932-b29c-25f61b4ceeb2.png)
  
Klicken Sie auf **Antwortheader**.
  
![Screenshot der Registerkarte "Details"](media/c47770ac-5b2b-4941-9830-c57565dec4cc.png)
  
SharePoint gibt einige nützliche Diagnoseinformationen in seinen Antwortheadern zurück. Einer der nützlichsten Werte ist **SPRequestDuration**. Er gibt in Millisekunden an, wie lange die Verarbeitung einer Anforderung auf dem Server dauerte. 
  
Im folgenden Screenshot **Unterwebsites anzeigen** ist für die strukturelle Navigation nicht aktiviert. Dies bedeutet, dass nur die Site Collection Verknüpfung in der globalen Navigation vorhanden ist: 
  
![Screenshot mit Ladezeiten als Anforderungsdauer](media/3422b2e8-15ec-4bb9-ba86-0965b6b49b01.png)
  
Der Schlüssel für **SPRequestDuration** hat einen Wert von 245 Millisekunden. Dies ist die Zeit die Anforderung zurückgegeben. Da nur ein Navigationselement auf der Website vorhanden ist, ist dies eine gute Richtlinie für ohne extra fette Navigation wie SharePoint Online ausführt. Der nächste Screenshot zeigt, wie in Unterwebsites Hinzufügen dieser Schlüssel auswirkt. 
  
![Screenshot mit einer Anforderungsdauer von 2.502 ms](media/618ee4e9-2ffa-4a22-b638-fa77b72292b8.png)
  
Das Hinzufügen von Unterwebsites hat die für die Rückgabe der Seitenanforderung benötigte Zeit deutlich erhöht.
  
Die Vorteile der Verwendung der regulären strukturierten Navigation ist, dass Sie auf einfache Weise organisieren Sie die Reihenfolge, Ausblenden von Websites, Seiten hinzufügen können, die Ergebnisse werden Sicherheit verkürzt und Sie werden nicht aus der unterstützten Gestaltungsvorlagen in SharePoint Online verwendeten abweichen.
  
## <a name="using-managed-navigation-and-managed-metadata-in-sharepoint-online"></a>Verwenden der verwalteten Navigation und verwalteter Metadaten in SharePoint Online

Die verwaltete Navigation ist eine weitere sofort nutzbare Option, die Sie verwenden können, um die gleiche Art von Funktionalität wie bei der strukturellen Navigation neu zu erstellen.
  
Die Vorteile der Verwendung verwalteter Metadaten ist wesentlich schneller als die Verwendung von Inhalt nach Abfrage zum Erstellen der Websitenavigation Datenabfrage werden kann. Es handelt sich um viel schneller besteht keine Möglichkeit trim Sicherheit auf die Ergebnisse also wenn ein Benutzer Zugriff auf eine bestimmte Website, nicht der Link zeigt immer noch Obgleich wird dazu führen, dass eine Fehlermeldung angezeigt.
  
 **So implementieren Sie die verwaltete Navigation und die Ergebnisse**
  
Es gibt mehrere Artikel auf TechNet zu den Details der verwalteten Navigation beispielsweise, finden Sie unter [Übersicht über die verwaltete Navigation in SharePoint Server 2013](https://go.microsoft.com/fwlink/?LinkId=708689).
  
Um die verwaltete Navigation implementieren zu können, benötigen Sie Administratorberechtigungen für den Terminologiespeicher. Durch Einrichten von Begriffen mit URLs, die der Struktur einer Websitesammlung entsprechen, kann die verwaltete Navigation anstatt einer strukturellen Navigation verwendet werden. Beispiel:
  
![Screenshot von Subsite1-Beispiel](media/4155b4da-ccff-4e2a-92de-7803ac62982b.png)
  
Das folgende Beispiel zeigt die Leistung der komplexen Navigation bei Verwendung der verwalteten Navigation.
  
![Screenshot von SPRequestDuration-Beispiel](media/72257528-0ec6-48b0-85a5-efeb7432db5b.png)
  
Mithilfe der verwalteten Navigation lässt sich die Leistung im Vergleich zum Ansatz der strukturellen Navigation "Inhalt von Abfrage" konsistent verbessern.
  
## <a name="using-search-driven-client-side-scripting"></a>Verwenden einer suchbasierten, clientseitigen Skripterstellung

Mithilfe der Suchfunktion können Sie die Indizes nutzen, die im Hintergrund mithilfe der kontinuierlichen Durchforstung aufgebaut werden. Dies bedeutet, dass es keine übermäßig vielen Inhaltsabfragen gibt. Die Suchergebnisse werden aus dem Suchindex abgerufen, und die Ergebnisse werden sicherheitsgekürzt. Dies geht schneller als die Verwendung regulärer Inhaltsabfragen. Wenn Sie die Suche für strukturelle Navigation verwenden, insbesondere dann, wenn Sie über eine komplexe Websitestruktur verfügen, lässt sich das Laden von Seiten erheblich beschleunigen. Der Hauptvorteil dieser überverwalteten Navigation ist, dass Sie von der Sicherheitskürzung profitieren.
  
Dieser Ansatz umfasst das Erstellen einer benutzerdefinierten Masterseite und die Ersetzung sofort nutzbaren Navigationscodes durch benutzerdefiniertes HTML. Gehen Sie folgendermaßen vor, um den Navigationscode in der Datei "seattle.html" zu ersetzen.
  
In diesem Beispiel wird öffnen Sie die Datei seattle.html und ersetzt das gesamte Element **Id = "DeltaTopNavigation"** mit der benutzerdefinierten HTML-Code. 
  
 **Beispiel: So ersetzen Sie den sofort nutzbaren Navigationscode auf einer Masterseite**
  
1. Navigieren Sie zur Seite **Websiteeinstellungen**. 
    
2. Öffnen Sie durch Klicken auf **Masterseiten** den Masterseitenkatalog.
    
3. Von hier aus können Sie durch die Bibliothek navigieren und die Datei **seattle.master** herunterladen.
    
4. Bearbeiten Sie den Code mit einem Texteditor, und löschen Sie den Codeblock im folgenden Screenshot.
    
    ![Screenshot von zu löschendem DeltaTopNavigation-Code](media/70db2cd2-660d-4e0d-9d5c-a5df331c73b4.png)
  
5. Entfernen Sie den Code zwischen den \<SharePoint:AjaxDelta Id = "DeltaTopNavigation"\> und \<\SharePoint:AjaxDelta\> tags und ersetzt ihn durch den folgenden Codeausschnitt:
    
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

6. Ersetzen Sie die URL in das Laden image Anchortag am Anfang, mit einem Link zu einem Bild laden in Ihrer Websitesammlung. Nachdem Sie die Änderungen vorgenommen haben, benennen Sie die Datei, und klicken Sie dann auf den Gestaltungsvorlagenkatalog hochladen. Dadurch wird eine neue Master-Datei generiert.
    
7. Dieser HTML-Code wird die grundlegende Markup, das von der Suchergebnisse aus JavaScript-Code aufgefüllt wird. Sie müssen so bearbeiten Sie den folgenden Code zum Ändern des Werts für die `var root = "site collection URL"` wie im folgenden Codeausschnitt veranschaulicht: 
    
  ```
  var root = "https://spperformance.sharepoint.com/sites/NavigationBySearch";
  ```

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
  var query = baseUrl + "'contentClass=\"STS_Web\"+path:" + root + "'&amp;trimduplicates=false&amp;rowlimit=300";
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
              if (cachedNodes &amp;&amp; timeStamp) {
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
              if (elem.children &amp;&amp; elem.children.length > 0) {
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
  
  ```

     $("li.level1").mouseover (Funktion {) 
  
Var Position = $(this).position();
  
$(this).find("ul.level2").css ({Breite: 100; Links: top-position.left + 10: 50});
    
     }) 
  
.MouseOut (Funktion {)
  
$(this).find("ul.level2").css ({linken:-99999, Top: 0});
  
});
  
$("li.level2").mouseover (Funktion {)
  
Var Position = $(this).position();
  
Console.log(JSON.stringify(Position));
  
$(this).find("ul.level3").css ({Breite: 100; Links: position.left + 95, top: position.top});
    
     }) 
  
.MouseOut (Funktion {)
  
$(this).find("ul.level3").css ({linken:-99999, Top: 0});
  
});
    
    } _spBodyOnLoadFunctionNames.push("InitCustomNav");
    
    To summarize the code shown above in the jQuery **[$(document).ready]** function there is a **[viewModel]** object created and then the **[loadNavigationNodes()]** function on that object is called. This function either loads the previously built navigation hierarchy stored in the HTML5 local storage of the client browser or it calls the function **[queryRemoteInterface()]**. 
    
    **[QueryRemoteInterface()]** builds a request using the **[getRequest()]** function with the query parameter defined earlier in the script and then returns data from the server. This data is essentially an array of all the sites in the site collection represented as data transfer objects with various properties. This data is then parsed into the previously defined **[SPO.Models.NavigationNode]** objects which use Knockout.js to create observable properties for use by data binding the values into the HTML that we defined earlier. The objects are then put into a results array. This array is parsed into JSON using Knockout and stored in the local browser storage for improved performance on future page loads. 
    
8. Im nächsten Schritt die Ergebnisse werden in das Array **[self.nodes]** zugewiesen und eine Hierarchie basiert der Objekte mit linq.js ein Array **[self.heirarchy]** die Ausgabe zuweisen. Dieses Array ist das Objekt, das an den HTML-Code gebunden ist. Dies in der Funktion **[toggleView()]** erfolgt, indem Sie das Self-Objekt an die Funktion **[ko.applyBinding()]** übergeben. Dies führt dann Hierarchie Array folgenden HTML-Code gebunden werden: 
    
  ```
  <div data-bind="foreach: hierarchy" class="noindex ms-core-listMenu-horizontalBox">
  ```

    Schließlich werden die Ereignishandler für **[Mouseenter]** und **[Mouseexit]** zum der Navigation auf oberster Ebene der Unterwebsite Dropdownmenüs behandeln hinzugefügt, die in der Funktion **[addEventsToElements()]** erfolgt. 
    
    Im folgenden Screenshot können die Ergebnisse der Navigation angezeigt werden:
    
    ![Screenshot der Ergebnisse der navigation](media/020d34d2-942a-431b-9b26-6d2c8a6fde30.png)
  
    In unserem komplexen Navigationsbeispiel zeigt das Laden einer leeren Seite ohne lokales Zwischenspeichern, dass die Zeit auf dem Server von der strukturellen Benchmarknavigation auf ein ähnliches Ergebnis reduziert wurde wie beim Ansatz der verwalteten Navigation.
    
    ![Screenshot von SPRequestDuration 301](media/307d7caf-e83a-40d9-a551-91d842521d03.png)
  
    Ein wesentlicher Vorteil dieses Ansatzes ist, dass durch Verwendung des lokalen HTML5-Speichers die Navigation lokal für den Benutzer gespeichert wird, wenn er die Seite das nächste Mal lädt.
    
Wir profitieren von einer wesentlichen Leistungssteigerung, wenn wir die Such-API für die strukturelle Navigation verwenden, allerdings müssen dafür technische Funktionen ausgeführt und angepasst werden. Bei der Beispielimplementierung werden die Websites auf die gleiche Weise angeordnet wie bei der sofort nutzbaren strukturellen Navigation, nämlich in alphabetischer Reihenfolge. Wenn Sie von dieser Reihenfolge abweichen möchten, ist dies komplizierter zu entwickeln und zu verwalten. Außerdem müssen Sie dann auch von den unterstützten Masterseiten abweichen. Wenn die benutzerdefinierte Masterseite nicht verwaltet wird, verpassen Sie für Ihre Website Updates und Verbesserungen, die Microsoft an den Masterseiten vornimmt.
  
Im oben stehenden Code gelten die folgenden Abhängigkeiten:
  
- jQuery-[http://jquery.com/](http://jquery.com/)
    
- KnockoutJS-[http://knockoutjs.com/](http://knockoutjs.com/)
    
- Linq.js - [http://linqjs.codeplex.com/](http://linqjs.codeplex.com/), oder [github.com/neuecc/linq.js](https://github.com/neuecc/linq.js/)
    
Die aktuelle Version von LinqJS enthält nicht die ByHierarchy-Methode verwendet, die im obigen Code und unterbricht den Navigationscode. Um dieses Problem zu beheben, fügen Sie die folgende Methode zur Datei Linq.js vor der Zeile "Flatten: Funktion ()".
  
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


