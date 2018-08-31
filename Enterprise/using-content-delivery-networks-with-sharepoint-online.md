---
title: Verwenden die Inhaltsübermittlung mit SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 5/8/2017
ms.audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- SPO160
ms.assetid: 9a64268c-0b74-4eaa-b971-fb6380b1b165
description: 'Zusammenfassung: Dieser Artikel beschreibt Content Delivery Networks (CDNs) und deren Verwendung auf um SharePoint Online Leistung zu erhöhen.'
ms.openlocfilehash: 63062c08d0c22518eb36ea0a6faa97106fd394b4
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540832"
---
# <a name="using-content-delivery-networks-with-sharepoint-online"></a>Verwenden die Inhaltsübermittlung mit SharePoint Online

 **Zusammenfassung:** Dieser Artikel beschreibt Content Delivery Networks (CDNs) und deren Verwendung auf um SharePoint Online Leistung zu erhöhen. 
  
In der heutigen Web Development Communitys sind viele allgemeine Bibliotheken (beispielsweise JavaScript und CSS-Dateien), die Sie in der SharePoint-Lösung enthalten können. Viele dieser werden auf ihre ASP-CDN von Microsoft gehostet. Dies bedeutet, dass Sie verweisen auf diese Bibliotheken aus diesen verteilten Servern und ermöglichen das Internet integrierten DNS-routing Systeme den nächsten Server für Ihre Benutzer suchen können. Die Beispiele in diesem Artikel veranschaulichen, wie der Zeitunterschied zwischen der beliebte Bibliothek jQuery vom SharePoint Online-Server im Vergleich zu dem CDN ASP herunterladen erheblich ist. Der Benutzer möglicherweise bereits auch die CDN-Version auf dem lokalen Computer zwischengespeichert werden, sodass sie nicht zum Herunterladen der Datei verfügen. Dies kann wichtig, wenn Sie, dass Benutzer auf der ganzen Welt und weit weg von der Datacenter, die Ihre SharePoint Online-Website hostet verteilt sein.
  
Wenn Sie Seiten für SharePoint Online erstellen, kann sich die physische Entfernung zwischen Ihren Benutzern und dem Standort der SharePoint Online-Instanz auf die Latenz auswirken. Dies ist besonders wichtig für global präsente Unternehmen, bei denen eine Website möglicherweise auf einem Kontinent gehostet wird, während Benutzer auf der anderen Seite der Welt auf deren Inhalte zugreifen. Mithilfe von CDNs kann dem Abhilfe geschaffen werden, da beliebte Webressourcen an verschiedenen Standorten näher am Endbenutzer gehostet werden.
  
Da es sich beim CDN um ein weltweites Netzwerk von Servern handelt, die die gleichen Dateien hosten, werden die Internet-URLs für in den CDNs gespeicherten Dateien durch den Clientcomputer interpretiert, sodass der Server, der dem Benutzer am nächsten ist, die Datei verarbeitet. Dadurch lassen sich Verzögerungen durch Netzwerkroundtrips deutlich reduzieren.
  
## <a name="the-challenge-of-hosting-sharepoint-online-sites-for-a-global-audience"></a>Die Herausforderung beim Hosten von SharePoint Online-Websites für eine globale Zielgruppe

SharePoint Online-Websites werden in Datencentern relativ zum Standort (angegeben durch den Benutzer) gehostet. Dieser wird beim Anmelden in Office 365 ausgewählt. Wenn sich Ihre Website beispielsweise auf Servern in den USA befindet und Benutzer von Ostasien aus auf diese Website zugreifen, können sich aufgrund der Entfernung, die die Daten über Glasfaserkabel überwinden müssen, Probleme mit der Latenz ergeben.
  
Viele statische Dateien, die von der standardmäßigen SharePoint-Benutzeroberfläche verwendet werden bereits CDNs weltweit Netzwerk von Microsoft gehostet. Dadurch wird die Leistung über einen Zeitraum verbessert. Jedoch, wenn Sie eine beliebige beliebte JavaScript und CSS-Objekte (z. b; verwenden JQuery, Modernizr, Bootstrap oder ASP.NET Ajax) Sie können die Zeiten Laden dieser Dateien verbessern, indem Sie CDNs frei verfügbar.
  
## <a name="advantages-of-using-cdns-to-improve-download-speed"></a>Vorteile beim Einsatz von CDNs zur Verbesserung der Downloadgeschwindigkeit

Seitenladezeiten für aus verschiedenen Gründen kann mit CDNs verbessert werden. Ein Grund ist, dass der Abstand zwischen dem CDN und der Benutzer möglicherweise kürzer als der Abstand für die SharePoint Online-Instanz. Diese Netzwerke stark verteilt werden und auch sehr hohe Verfügbarkeit und die Antwortzeit Zeiten haben sollen. Ein weiterer Grund ist, die, falls Sie eine beliebte Bibliothek mit CSS-Dateien, in Verbindung mit einem CDN, der Benutzer möglicherweise bereits der Bibliothek zwischengespeichert und sie nicht selbst es überhaupt herunterladen müssen.
  
Die folgenden Screenshots veranschaulichen die Vorteile der Verwendung von CDNs. Diese Screenshots stammen aus der Registerkarte **Netzwerk** in den Internet Explorer 11 Developer Tools. Diese Screenshots anzeigen die Wartezeit auf die jQuery beliebte Bibliothek. Drücken Sie die **F12** und wählen Sie die Registerkarte **Netzwerk** , die mit einem Wi-Fi-Symbol symbolisiert ist, um diesem Bildschirm in Internet Explorer anzuzeigen. 
  
![Screenshot des F12-Netzwerks](media/930541fd-af9b-434a-ae18-7bda867be128.png)
  
Dieser Screenshot zeigt die Bibliothek auf den Gestaltungsvorlagenkatalog auf der SharePoint Online-Website selbst hochgeladen. Die Zeit die Bibliothek hochladen ist 1.51 Sekunden.
  
![Screenshot der Ladezeit von 1,51 s](media/64225c79-fa53-480f-81cd-0d351674320e.png)
  
Der zweite Screenshot zeigt dieselbe Datei von Microsoft bereitgestellt CDN. Dieses Mal ist die Wartezeit rund 496 Millisekunden. Dies ist eine große Verbesserung und zeigt an, dass eine gesamte Sekunde deaktiviert die Gesamtzeit zum Herunterladen des Seiteninhalts shaved ist.
  
![Screenshot der Ladezeiten in 469 ms](media/6a553cc3-25a0-42c1-aae7-4aebbc2eb4c3.png)
  
## <a name="using-cdns-with-sharepoint-server-2013"></a>Verwenden von CDNs mit SharePoint Server 2013

Mit CDNs nur sinnvoll in einem SharePoint Online Kontext und sollte vermieden werden, mit SharePoint Server 2013. Dies ist, da alle die Vorteile im Zusammenhang mit geografischen Standort nicht geografisch trotzdem schließen oder halten Sie True, wenn der Server lokale gespeichert ist. Darüber hinaus ist eine Netzwerkverbindung mit den Servern, auf dem er gehostet wird, klicken Sie dann die Website kann ohne Verbindung zum Internet verwendet werden und die CDN-Dateien aus diesem Grund kann nicht abgerufen werden. Anderenfalls sollten Sie ein CDN verwenden, wenn vorhanden ist und für die Bibliothek und Dateien stabil für Ihre Website müssen.
  
## <a name="popular-cdns-and-how-to-use-them"></a>Beliebte CDNs und deren Verwendung

Microsoft Ajax-CDN bietet die meisten der beliebten Bibliotheken jQuery (und alle anderen Bibliotheken), einschließlich ASP.NET Ajax, Bootstrap, Knockout.js und vieles mehr.
  
Um diese Skripts in Ihrem Projekt zu verwenden, ersetzen Sie einfach alle Verweise auf diese öffentlich zugänglichen Bibliotheken durch Verweise auf die CDN-Adresse, anstatt sie in das Projekt selbst aufzunehmen. Verwenden Sie z. B. den folgenden Code für die Verknüpfung mit jQuery:
  
```
<script src=http://ajax.aspnetcdn.com/ajax/jquery-2.1.1.js> </script>
```

Weitere Informationen zu CDNs finden Sie unter [Inhaltsübermittlung](content-delivery-networks.md).
  
## <a name="more-topics-about-using-cdns-with-sharepoint"></a>Weitere Themen zur Verwendung von CDNs mit SharePoint

[Mithilfe der clientseitigen hostingwebparts aus Office 365 CDN](https://dev.office.com/sharepoint/docs/spfx/web-parts/get-started/hosting-webpart-from-office-365-cdn)
  

