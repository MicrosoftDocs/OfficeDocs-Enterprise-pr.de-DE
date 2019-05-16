---
title: Verwenden von Content Delivery Networks (Netzwerken für die Inhaltsübermittlung) mit SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 5/8/2017
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- SPO160
ms.assetid: 9a64268c-0b74-4eaa-b971-fb6380b1b165
description: 'Zusammenfassung: in diesem Artikel werden Inhalts Zustellungs Netzwerke (CDNs) und deren Verwendung zur Steigerung der Leistung von SharePoint Online beschrieben.'
ms.openlocfilehash: 24b12ae60a8c089d8e32d2609957e8b0e3420510
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "34070581"
---
# <a name="using-content-delivery-networks-with-sharepoint-online"></a>Verwenden von Content Delivery Networks (Netzwerken für die Inhaltsübermittlung) mit SharePoint Online

 **Zusammenfassung:** In diesem Artikel werden Inhalts Bereitstellungs Netzwerke (CDNs) und ihre Verwendung zur Steigerung der Leistung von SharePoint Online beschrieben. 
  
In den heutigen Webentwicklungs Communitys gibt es viele allgemeine Bibliotheken (wie JavaScript und CSS-Dateien), die Sie in Ihre SharePoint-Lösung aufnehmen können. Viele dieser werden von Microsoft in Ihrem ASP CDN gehostet. Dies führt dazu, dass Sie von diesen verteilten Servern aus auf diese Bibliotheken verweisen und die integrierten DNS-Routing Systeme des Internets den nächstgelegenen Server für Ihren Benutzer ermitteln können. Die Beispiele in diesem Artikel veranschaulichen, wie der Zeitunterschied zwischen dem Herunterladen der beliebten Bibliothek jQuery aus dem SharePoint Online-Server im Vergleich zu den ASP CDN sehr bedeutsam ist. Der Benutzer hat möglicherweise auch die CDN-Version, die auf dem lokalen Computer zwischengespeichert ist, damit Sie die Datei nicht herunterladen müssen. Dies kann wichtig sein, wenn Sie Benutzer auf der ganzen Welt und weit weg vom Datencenter haben, das Ihre SharePoint Online-Website hostet.
  
Beim Erstellen von Seiten für SharePoint Online kann die Wartezeit vom physischen Abstand zwischen den Benutzern und dem Speicherort der SharePoint Online-Instanz beeinflusst werden. Dies ist besonders wichtig für Organisationen mit globaler Präsenz, bei denen eine Website auf einem Kontinent gehostet werden kann, während Benutzer auf der anderen Seite der Welt auf Ihre Inhalte zugreifen. Mithilfe von CDNs können Sie diese Situation verringern, indem Sie bestimmte Beliebte Webressourcen an verschiedenen Standorten näher an die Endbenutzer hosten.
  
Da ein CDN ein weltweites Netzwerk von Servern ist, auf denen die gleichen Dateien gehostet werden, werden Internet-URLs für im CDNs gespeicherte Dateien vom Clientcomputer interpretiert, sodass der Server, der dem Benutzer am nächsten ist, die Datei bedient. Dadurch werden die Verzögerungen bei Netzwerk Roundtrips erheblich reduziert.
  
## <a name="the-challenge-of-hosting-sharepoint-online-sites-for-a-global-audience"></a>Die Herausforderung beim Hosten von SharePoint Online-Websites für eine globale Zielgruppe

SharePoint Online-Websites werden in Rechenzentren relativ zum Speicherort (vom Benutzer angegeben) gehostet, der bei der Anmeldung bei Office 365 ausgewählt wurde. Wenn sich Ihre Website beispielsweise auf Servern in den USA befindet und Benutzer aus Ostasien auf die Website zugreifen, können Probleme aufgrund der Entfernung auftreten, die die Daten über LWL-Kabel übertragen werden müssen.
  
Viele statische Dateien, die von der standardmäßigen SharePoint-Benutzeroberfläche verwendet werden, werden bereits im weltweiten Netzwerk von CDNs von Microsoft gehostet. Dadurch wird die Leistung im Laufe der Zeit verbessert. Wenn Sie jedoch beliebte JavaScript-und CSS-Objekte verwenden (beispielsweise; JQuery, Modernist, Bootstrap oder ASP.NET AJAX) Sie können die Ladezeiten dieser Dateien mithilfe von frei verfügbaren CDNs verbessern.
  
## <a name="advantages-of-using-cdns-to-improve-download-speed"></a>Vorteile der Verwendung von CDNs zur Verbesserung der Downloadgeschwindigkeit

Durch die Verwendung von CDNs können Seitenladezeiten aus verschiedenen Gründen verbessert werden. Ein Grund ist, dass der Abstand zwischen CDN und Benutzer möglicherweise kürzer ist als der Abstand zur SharePoint Online-Instanz. Diese Netzwerke sind hoch verteilt und auch für sehr hohe Verfügbarkeit und Reaktionszeiten ausgelegt. Wenn Sie eine beliebte Bibliothek mit CSS-Dateien in Verbindung mit einem CDN verwenden, ist ein weiterer Grund dafür, dass der Benutzer die Bibliothek möglicherweise bereits zwischengespeichert hat und nicht einmal herunterladen muss.
  
Die folgenden Screenshots illustrieren die Vorteile der Verwendung von CDNs. Diese Screenshots befinden sich auf der Registerkarte **Netzwerk** in den Entwicklertools von Internet Explorer 11. Diese Screenshots zeigen die Wartezeit für die beliebte Bibliothek jQuery. Drücken Sie zum Öffnen dieses Bildschirms in Internet Explorer **F12** , und wählen Sie die Registerkarte **Netzwerk** , die mit einem Wi-Fi-Symbol symbolisiert wird. 
  
![Screenshot des F12-Netzwerks](media/930541fd-af9b-434a-ae18-7bda867be128.png)
  
Dieser Screenshot zeigt die Bibliothek, die in den gestaltungsvorlagenkatalog auf der SharePoint Online-Website hochgeladen wurde. Die Zeit, die zum Hochladen der Bibliothek benötigt wird, beträgt 1,51 Sekunden.
  
![Screenshot der Ladezeit 1.51 s](media/64225c79-fa53-480f-81cd-0d351674320e.png)
  
Der zweite Screenshot zeigt dieselbe Datei an, die vom CDN von Microsoft bereitgestellt wurde. Dieses Mal beträgt die Wartezeit rund 496 Millisekunden. Dies ist eine deutliche Verbesserung und zeigt, dass die gesamte Zeit zum Herunterladen des Seiteninhalts eine ganze Sekunde lang abrasiert wird.
  
![Screenshot der Ladezeiten in 469 MS](media/6a553cc3-25a0-42c1-aae7-4aebbc2eb4c3.png)
  
## <a name="using-cdns-with-sharepoint-server-2013"></a>Verwenden von CDNs mit SharePoint Server 2013

Die Verwendung von CDNs ist nur in einem SharePoint Online-Kontext sinnvoll und sollte mit SharePoint Server 2013 vermieden werden. Dies liegt daran, dass alle Vorteile rund um den geografischen Standort nicht wahr sind, wenn sich der Server ohnehin lokal oder geografisch geschlossen befindet. Wenn eine Netzwerkverbindung zu den Servern vorhanden ist, auf denen Sie gehostet wird, kann die Website außerdem ohne Internet Verbindung verwendet werden und kann daher keine CDN-Dateien abrufen. Andernfalls sollten Sie ein CDN verwenden, wenn für die Bibliothek und die Dateien, die Sie für Ihre Website benötigen, eine verfügbar und stabil ist.
  
## <a name="popular-cdns-and-how-to-use-them"></a>Beliebte CDNs und ihre Verwendung

Das AJAX CDN von Microsoft bietet die meisten gängigen Bibliotheken wie jQuery (und alle anderen Bibliotheken), ASP.NET AJAX, Bootstrap, Knockout. js und vieles mehr.
  
Um diese Skripts in Ihr Projekt einzubeziehen, ersetzen Sie einfach alle Verweise auf diese öffentlich verfügbaren Bibliotheken durch Verweise auf die CDN-Adresse, anstatt Sie in Ihr Projekt selbst einzubinden. Verwenden Sie beispielsweise den folgenden Code, um einen Link zu jQuery zu erstellen:
  
```
<script src=http://ajax.aspnetcdn.com/ajax/jquery-2.1.1.js> </script>
```

Weitere Informationen zu CDNs finden Sie unter [Content](content-delivery-networks.md)Subnetze.
  
## <a name="more-topics-about-using-cdns-with-sharepoint"></a>Weitere Themen zur Verwendung von CDNs mit SharePoint

[Hosten des clientseitigen Webparts aus Office 365 CDN](https://dev.office.com/sharepoint/docs/spfx/web-parts/get-started/hosting-webpart-from-office-365-cdn)
  

