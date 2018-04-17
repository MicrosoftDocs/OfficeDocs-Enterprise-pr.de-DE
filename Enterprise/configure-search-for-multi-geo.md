---
title: Konfigurieren der Suche für OneDrive für Unternehmen Multi-Geo
ms.author: tlarsen
author: tklarsen
manager: arnek
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: Strat_SP_gtc
localization_priority: Normal
description: Informationen Sie zum Konfigurieren der Suche in einer Umgebung mit mehreren geografisch.
ms.openlocfilehash: 5cf155c2c5bd2e27a54d84c4d5411e5b1afce568
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="configure-search-for-onedrive-for-business-multi-geo"></a>Konfigurieren der Suche für OneDrive für Unternehmen Multi-Geo

In einer Umgebung mit mehreren geografisch SharePoint Online (SPO) eine Organisation kann ein Office 365-Mandanten, aber ihre SharePoint-Inhalte an mehreren geografischen Standorten - speichern einem zentralen Standort und mindestens Satellitenassemblys Geo-Speicherorte.

Jeden geografischen Standort verfügt über eine eigene Suchindex und Suchcenter. Wenn ein Benutzer sucht, wird die Abfrage an alle Indizes aufgefächerte, und die zurückgegebenen Ergebnisse werden zusammengeführt.

Beispielsweise kann ein Benutzer in einem Geo Speicherort suchen für Inhalte, die in eine andere Geo Position oder nach Inhalten zu einer SharePoint-Website, die an einen anderen Geo Speicherort eingeschränkt ist. Wenn der Benutzer Zugriff auf diese Inhalte verfügt, wird die Suche das Ergebnis angezeigt.

## <a name="which-search-clients-work-in-a-multi-geo-environment"></a>Die Clients arbeiten in einer Umgebung mit mehreren geografisch suchen?

Diese Clients können aus allen Speicherorten von Geo Ergebnisse zurückgegeben:

-   OneDrive for Business

-   Delve

-   SharePoint-Homepage

-   Das Suchcenter

-   Benutzerdefinierte suchanwendungen, die die SharePoint-Suche-API verwenden

### <a name="onedrive-for-business"></a>OneDrive for Business

Als Multi-Geo-Umgebung eingerichtet wurde, erhalten Benutzer, die in OneDrive durchsuchen Ergebnisse aus allen geografisch Speicherorten.

### <a name="delve"></a>Delve

Als Multi-Geo-Umgebung eingerichtet wurde, erhalten Benutzer, die in Delve durchsuchen Ergebnisse aus allen geografisch Speicherorten.

Die Delve-Feeds und die Profilkarte zeigen nur eine Vorschau der Dateien, die in der **zentralen** Speicherort gespeichert sind. Für Dateien, die in Satelliten Geo Speicherorten gespeichert sind, wird stattdessen das Symbol für den Dateityp angezeigt.

### <a name="the-sharepoint-home-page"></a>SharePoint-Homepage

Als Multi-Geo-Umgebung eingerichtet wurde, wird den Benutzern letzte und besuchter Websites aus mehreren geografisch Speicherorten auf ihre SharePoint-Homepage News, angezeigt. Wenn sie das Suchfeld auf der Homepage der SharePoint verwenden, erhalten sie zusammengeführte Ergebnisse aus mehreren geografisch Standorten.

### <a name="the-search-center"></a>Das Suchcenter

Nach der Multi-Geo hat Umgebung eingerichtet wurde jedem Suchcenter weiterhin über einen eigenen Geo Ort nur Ergebnisse anzeigen. Administratoren müssen zum Abrufen der Ergebnisse aus allen geografisch Speicherorten [ändern, die von jedem Suchcenter](#_Set_up_a_1) . Anschließend erhalten Benutzer, die für die Suche im Suchcenter Ergebnisse aus allen geografisch Speicherorten.

### <a name="custom-search-applications"></a>Benutzerdefinierte suchanwendungen

Interagieren benutzerdefinierte suchanwendungen wie gewohnt mit der Suchindizes mithilfe der vorhandenen SharePoint Search-REST-APIs. Um die Ergebnisse aller oder einiger Geo-Speicherorte zu erhalten, muss die Anwendung [Aufrufen der API und umfassen die neuen Abfrageparameter Multi-Geo](#_Get_custom_search) in der Anforderung. Dadurch wird einen Lüfter der Abfrage an allen Speicherorten von Geo ausgelöst.

## <a name="whats-different-about-search-in-a-multi-geo-environment"></a>Was ist anders bei der Suche in einer Umgebung mit mehreren geografisch?

Einige Suchfeatures, mit denen Sie möglicherweise vertraut sind, funktionieren in einer Umgebung mit mehreren geografisch.

<table>
<thead>
<tr class="header">
<th align="left"><strong>Feature</strong></th>
<th align="left"><strong>Wie funktioniert</strong></th>
<th align="left"><strong>Dieses Problem zu umgehen</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">Höhergestufte Ergebnisse</td>
<td align="left">Erstellen von Abfrageregeln können mit heraufgestufte Ergebnisse auf verschiedenen Ebenen: für den gesamten Mandanten, für eine Websitesammlung oder für eine Website. Definieren Sie in einer Umgebung mit mehreren geografisch heraufgestufte Ergebnisse auf der Ebene der <strong>Mandanten</strong> , wenn Sie die Ergebnisse an die Suchcentern an <strong>allen</strong> Speicherorten von Geo Höherstufen möchten. Wenn Sie <strong>nur</strong> Ergebnisse im Suchcenter Höherstufen möchten, die am Geo der Websitesammlung oder Website befindet, definieren Sie die Ergebnisse Ebene der <strong>Websitesammlung</strong> oder <strong>Website</strong> an.</td>
<td align="left">Wenn Sie verschiedene heraufgestufte Ergebnisse pro Geo-Speicherort, beispielsweise unterschiedliche Regeln für Reisen, nicht empfehlen wir definieren auf der Ebene der Mandant Ergebnisse heraufgestuft.</td>
</tr>
<tr class="even">
<td align="left">Sucheinschränkungen</td>
<td align="left">Suche Einschränkungen aus alle Geo Speicherorte eines Mandanten liegen zurückgegeben, und klicken Sie dann aggregiert werden. Die Aggregation ist bemüht, d. h., die von einschränkungsanzahlen möglicherweise nicht 100 % genau. In den meisten Fällen suchbasierte reicht diese Genauigkeit.</td>
<td align="left">Suchgesteuerte Anwendungen, die Einschränkung Vollständigkeit abhängen, Fragen Sie jeden Standort Geo unabhängig voneinander ohne Verwendung von Multi-Geo Auffächerung ab.</td>
</tr>
<tr class="odd">
<td align="left"></td>
<td align="left">Multi-Geo Suche unterstützt keine dynamischen das Zuordnen von Buckets für numerische Einschränkungen.</td>
<td align="left">Verwenden Sie den <a href="https://docs.microsoft.com/en-us/sharepoint/dev/general-development/query-refinement-in-sharepoint">Parameter "Discretize"</a> für numerische Einschränkungen an.</td>
</tr>
<tr class="even">
<td align="left">Dokument-IDs</td>
<td align="left">Bei der Entwicklung einer suchbasierte-Anwendung, die von Dokument-IDs abhängt, beachten Sie, dass die Dokument-IDs in einer Umgebung mit mehreren geografisch sind nicht über Geo Standorte eindeutige, sie sind pro Standort Geo eindeutig.</td>
<td align="left">Wir haben eine Spalte hinzugefügt, die den Speicherort Geo angibt. Verwenden Sie diese Spalte, um Eindeutigkeit zu erreichen. Diese Spalte wird mit der Bezeichnung "GeoLocationSource".</td>
</tr>
<tr class="odd">
<td align="left">Anzahl der Ergebnisse</td>
<td align="left">Seite mit den Suchergebnissen zeigt kombinierten Ergebnisse aus den Speicherorten Geo, aber es ist nicht möglich, mehr als 500 Ergebnisse Seite.</td>
<td align="left"></td>
</tr>
</tbody>
</table>

## <a name="whats-not-supported-for-search-in-a-multi-geo-environment"></a>Was ist nicht für die Suche in einer Umgebung mit mehreren geografisch unterstützt?

Einige der Features für die Suche, die Sie möglicherweise vertraut sind, werden in einer Umgebung mit mehreren geografisch nicht unterstützt.

<table>
<thead>
<tr class="header">
<th align="left"><strong>Feature für die Suche</strong></th>
<th align="left"><strong>Hinweis</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">Nur-App-Authentifizierung</td>
<td align="left">Nur-App-Authentifizierung (Systemzugriff von Services) wird bei der Suche mit mehreren geografisch nicht unterstützt.</td>
</tr>
<tr class="even">
<td align="left">Gast-Benutzer</td>
<td align="left">Gast-Benutzer erhalten nur Ergebnisse aus dem Geo-Speicherort, dem sie durchsuchen aus.</td>
</tr>
</tbody>
</table>

## <a name="how-does-search-work-in-a-multi-geo-environment"></a>Wie funktioniert Suche in einer Umgebung mit mehreren geografisch funktionieren?

**Alle** verwenden die Suche Clients der vorhandenen SharePoint Search-REST-APIs zur Interaktion mit der Suchindizes an.
<img src="media/configure-search-for-multi-geo_image1-1.png" />

1. Ein Search-Client Ruft den Search-REST-Endpunkt mit der Abfrageeigenschaft EnableMultiGeoSearch = True.
2. Die Abfrage wird an alle Geo Speicherorte im Mandanten gesendet.
3. Suchergebnisse aus jedem Standort Geo zusammengeführt und Rangfolge.
4. Der Client ruft unified Suchergebnisse ab.



<span id="_Set_up_a" class="anchor"><span id="_Ref501388384" class="anchor"></span></span>Beachten Sie, dass wir nicht die Suchergebnisse zusammengefügt werden, bis es Ergebnisse aus allen Speicherorten die Geo erhalten haben. Dies bedeutet, dass Multi-Geo Suchvorgänge zusätzlichen Latenz im Vergleich zu Suchvorgänge in einer Umgebung mit nur eine Geo Speicherort.

<span id="_Set_up_a_1" class="anchor"><span id="_Ref505252370" class="anchor"></span></span>
## <a name="get-a-search-center-to-show-results-from-all-geo-locations"></a>Abrufen eines Suchcenters anzuzeigenden Ergebnisse aus allen geografisch Speicherorten

Jedem Suchcenter hat mehrere vertikale Märkte und müssen Sie jeden vertikal einzeln einrichten.

1.  Stellen Sie sicher, dass das Ausführen dieser Schritte mit einem Konto die Berechtigung zum Bearbeiten der Suchergebnisseite und das Ergebnis-Webpart hat.

2.  Navigieren Sie zur Seite mit Suchergebnissen (siehe die [Liste](https://support.office.com/article/174d36e0-2f85-461a-ad9a-8b3f434a4213) der Suche Suchergebnisseiten)

3.  Wählen Sie die vertikal einrichten, klicken Sie auf die obere rechte Ecke Zahnradsymbol **Einstellungen** , und klicken Sie dann auf **Seite bearbeiten**. Seite mit den Suchergebnissen wird im Bearbeitungsmodus geöffnet.

     ![](media/configure-search-for-multi-geo_image2.png)
1.  In den Suchergebnisse-Webpart bewegen Sie den Zeiger auf der oberen rechten Ecke des Webparts, klicken Sie auf den Pfeil, und klicken Sie dann im Menü auf **Webpart bearbeiten** . Der Suchergebnisse-Webpart-Toolbereich wird geöffnet, unter dem Menüband in der oberen rechten Seitenrand.![](media/configure-search-for-multi-geo_image3.png)

1.  Wählen Sie im Toolbereich des Webparts im Abschnitt **Einstellungen** unter **Ergebnisse Einstellungen steuern**, **Ergebnisse anzeigen Multi-Geo** zum Abrufen der Suchergebnisse-Webpart zum Anzeigen der Ergebnisse aus allen geografisch Speicherorten aus.

2.  Klicken Sie auf **OK** , um die Änderung zu speichern und schließen Sie den Webpart-Toolbereich.

3.  Überprüfen Sie Ihre Änderungen an der Suchergebnisse-Webpart, indem Sie auf der Registerkarte Seite im Hauptmenü **Einchecken** .

4.  Veröffentlichen Sie die Änderungen über den Link in der Notiz am oberen Rand der Seite bereitgestellt.

<span id="_Get_custom_search" class="anchor"><span id="_Ref501388387" class="anchor"></span></span>
## <a name="get-custom-search-applications-to-show-results-from-all-or-some-geo-locations"></a>Abrufen von benutzerdefinierten suchanwendungen zum Anzeigen von Suchergebnissen aus aller oder einiger Geo Speicherorten

Benutzerdefinierte suchanwendungen erhalten Ergebnisse von Speicherorten für alle oder einige, geografisch durch Angeben von Abfrageparametern mit der Anforderung an SharePoint Search-REST-API. Je nach dem Parameter für die Abfrage ist die Abfrage an alle Geo Speicherorte oder an einigen Standorten Geo aufgefächerte. Wenn Sie nur eine Teilmenge der Geo Speicherorte relevanten Informationen erhalten Abfragen müssen, können Sie beispielsweise den Lüfter nur diese steuern. Wenn die Anforderung erfolgreich ist, gibt der REST-API für SharePoint Search Antwortdaten zurück.

### <a name="query-parameters"></a>Abfrageparameter

EnableMultiGeoSearch - ist dies ein boolescher Wert, der angibt, ob die Abfrage auf die Indizes von anderen Speicherorten Geo des Mandanten Multi-Geo aufgefächerte werden muss. Legen Sie es auf **"true"** , die Abfrage Lüfter; **false** , wenn nicht, die Abfrage Lüfter. Der Standardwert ist **false**. Wenn Sie diesen Parameter keinen angeben, wird die Abfrage **nicht** an andere Speicherorte Geo aufgefächerte. Wenn Sie den Parameter in einer Umgebung, die mit mehreren geografisch nicht verwenden, wird der Parameter ignoriert.

Clienttyp - Dies ist eine Zeichenfolge. Geben Sie einen eindeutigen Client-Namen für jede Suchanwendung. Wenn Sie diesen Parameter keinen angeben, wird die Abfrage **nicht** an andere Speicherorte Geo aufgefächerte.

MultiGeoSearchConfiguration - ist dies eine optionale Liste von welche, die Geo Speicherorten in der Multi-Geo Mandanten um die Erweiterung der Abfrage an, wenn **EnableMultiGeoSearch** **true**ist. Wenn Sie nicht fügen Sie diesen Parameter oder leer lassen, wird die Abfrage an allen Speicherorten von Geo aufgefächerte. Geben Sie für jeden Standort Geo die folgenden Elemente im JSON-Format ein:

<table>
<thead>
<tr class="header">
<th align="left">Element</th>
<th align="left">Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">DataLocation</td>
<td align="left">Geo-Speicherort, beispielsweise Name.</td>
</tr>
<tr class="even">
<td align="left">Endpunkt</td>
<td align="left">Der Endpunkt für die Verbindung, beispielsweisehttps://contoso.sharepoint.com</td>
</tr>
<tr class="odd">
<td align="left">SourceId</td>
<td align="left">Die GUID der ergebnisquelle, beispielsweise B81EAB55-3140-4312-B0F4-9459D1B4FFEE.</td>
</tr>
</tbody>
</table>

Wenn Sie DataLocation oder Endpunkt weglassen oder wenn ein DataLocation doppelt vorhanden ist, schlägt die Anforderung fehl. [Sie erhalten Informationen zu den Endpunkt des einen Mandanten Geo Speicherorte mithilfe von Microsoft Graph](https://docs.microsoft.com/en-us/sharepoint/dev/solution-guidance/multigeo-discovery).

### <a name="response-data"></a>Antwortdaten

MultiGeoSearchStatus – ist dies eine Eigenschaft, die SharePoint-Suche API als Antwort auf eine Anforderung zurückgibt. Der Wert der Eigenschaft ist eine Zeichenfolge und gibt die folgende Informationen über die Ergebnisse, die die SharePoint-Suche-API zurückgibt:

<table>
<thead>
<tr class="header">
<th align="left">Wert</th>
<th align="left">Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">Vollständig</td>
<td align="left">Vollständige Ergebnisse aus <strong>allen</strong> die Geo-Speicherorte.</td>
</tr>
<tr class="even">
<td align="left">Teilweise</td>
<td align="left">Partielle Ergebnisse aus einem oder mehreren geografisch Standorten. Die Ergebnisse sind unvollständig aufgrund eines vorübergehenden Fehlers.</td>
</tr>

</tbody>
</table>

### <a name="query-using-the-rest-service"></a>Ausführen von Abfragen mithilfe des REST-Diensts

Mit GET-Anforderung Geben Sie Parameter für die Abfrage in der URL. Mit einer POST-Anforderung übergeben Sie Parameter für die Abfrage in den Hauptteil in JavaScript Object Notation (JSON)-Format.

#### <a name="request-headers"></a>Anforderungsheader

<table>
<thead>
<tr class="header">
<th align="left">Name</th>
<th align="left">Wert</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">Content-Type</td>
<td align="left">Application/Json; Odata = verbose</td>
</tr>
</tbody>
</table>

#### <a name="sample-get-request-thats-fanned-out-to-all-geo-locations"></a>Beispiel: eine GET-Anforderung für **Alle** Geo Speicherorte aufgefächerte

https:// \<Mandanten\>/\_api/Search/Query?querytext = "Sharepoint" & Eigenschaften = 'EnableMultiGeoSearch:true' & Clienttyp =' Meine\_Client\_Id'

#### <a name="sample-get-request-to-fan-out-to-some-geo-locations"></a>Beispiel GET-Anforderung an die Erweiterung auf **einige** Geo-Speicherorte

https:// <tenant>/_api/search/query?querytext = 'Site' & Clienttyp = 'My_client_id' & Eigenschaften ='EnableMultiGeoSearch:true, MultiGeoSearchConfiguration: [{DataLocation\:"Name"\,Endpunkt\:"Https\: contosoNAM.sharepoint.com"\,SourceId\:"B81EAB55-3140-4312-B0F4-9459D1B4FFEE"}\,{DataLocation\:"Können"\,Endpunkt\:" Https\://contosoCAN.sharepoint-df.com "}]"

#### <a name="sample-post-request-thats-fanned-out-to-all-geo-locations"></a>Beispiel-POST-Anforderung, die **Alle** Geo Speicherorte aufgefächerte

    {
        "request": {
            "__metadata": {
            "type": "Microsoft.Office.Server.Search.REST.SearchRequest"
        },
        "Querytext": "sharepoint",
        "Properties": {
            "results": [
                {
                    "Name": "EnableMultiGeoSearch",
                    "Value": {
                        "QueryPropertyValueTypeIndex": 3,
                        "BoolVal": true
                    }
                }
            ]
        },
        "ClientType": "my_client_id"
        }
    }


#### <a name="sample-post-request-thats-fanned-out-to-some-geo-locations"></a>Beispiel: eine POST-Anforderung für **einige** Geo Speicherorte aufgefächerte


    {
        "request": {
            "Querytext": "SharePoint",
            "ClientType": "my_client_id",
            "Properties": {
                "results": [
                    {
                        "Name": "EnableMultiGeoSearch",
                        "Value": {
                            "QueryPropertyValueTypeIndex": 3,
                            "BoolVal": true
                        }
                    },
                    {
                        "Name": "MultiGeoSearchConfiguration",
                        "Value": {
                        "StrVal": "[{\"DataLocation\":\"NAM\",\"Endpoint\":\"https://contoso.sharepoint.com\",\"SourceId\":\"B81EAB55-3140-4312-B0F4-9459D1B4FFEE\"},{\"DataLocation\":\"CAN\",\"Endpoint\":\"https://contosoCAN.sharepoint.com\"}]",
                            "QueryPropertyValueTypeIndex": 1
                        }
                    }
                ]
            }
        }
    }

### <a name="query-using-csom"></a>Abfrage mit CSOM

Hier ist eine CSOM-Beispielabfrage, die **Alle** Geo Speicherorte aufgefächerte:

    var keywordQuery = new KeywordQuery(ctx);
    keywordQuery.QueryText = query.SearchQueryText;
    keywordQuery.ClientType = <enter a string here>;
    keywordQuery["EnableMultiGeoSearch"] = true;

