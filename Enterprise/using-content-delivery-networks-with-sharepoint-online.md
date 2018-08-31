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
# <a name="using-content-delivery-networks-with-sharepoint-online"></a><span data-ttu-id="57d8a-103">Verwenden die Inhaltsübermittlung mit SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="57d8a-103">Using content delivery networks with SharePoint Online</span></span>

 <span data-ttu-id="57d8a-104">**Zusammenfassung:** Dieser Artikel beschreibt Content Delivery Networks (CDNs) und deren Verwendung auf um SharePoint Online Leistung zu erhöhen.</span><span class="sxs-lookup"><span data-stu-id="57d8a-104">**Summary:** This article describes Content Delivery Networks (CDNs) and how you can use them to increase SharePoint Online performance.</span></span> 
  
<span data-ttu-id="57d8a-p101">In der heutigen Web Development Communitys sind viele allgemeine Bibliotheken (beispielsweise JavaScript und CSS-Dateien), die Sie in der SharePoint-Lösung enthalten können. Viele dieser werden auf ihre ASP-CDN von Microsoft gehostet. Dies bedeutet, dass Sie verweisen auf diese Bibliotheken aus diesen verteilten Servern und ermöglichen das Internet integrierten DNS-routing Systeme den nächsten Server für Ihre Benutzer suchen können. Die Beispiele in diesem Artikel veranschaulichen, wie der Zeitunterschied zwischen der beliebte Bibliothek jQuery vom SharePoint Online-Server im Vergleich zu dem CDN ASP herunterladen erheblich ist. Der Benutzer möglicherweise bereits auch die CDN-Version auf dem lokalen Computer zwischengespeichert werden, sodass sie nicht zum Herunterladen der Datei verfügen. Dies kann wichtig, wenn Sie, dass Benutzer auf der ganzen Welt und weit weg von der Datacenter, die Ihre SharePoint Online-Website hostet verteilt sein.</span><span class="sxs-lookup"><span data-stu-id="57d8a-p101">In today's web development communities, there are many common libraries (such as JavaScript and CSS files) that you may include in your SharePoint solution. Many of these are hosted by Microsoft on their ASP CDN. This means you can reference these libraries from these distributed servers and allow the internet's built-in DNS routing systems to find the closest server to your user. The examples in this article demonstrate how the time difference between downloading the popular library jQuery from the SharePoint Online server versus the ASP CDN is quite significant. The user also may already have the CDN version cached on the local computer so that they do not have to download the file. This can be important if you have users distributed all over the world and far away from the datacenter that hosts your SharePoint Online site.</span></span>
  
<span data-ttu-id="57d8a-p102">Wenn Sie Seiten für SharePoint Online erstellen, kann sich die physische Entfernung zwischen Ihren Benutzern und dem Standort der SharePoint Online-Instanz auf die Latenz auswirken. Dies ist besonders wichtig für global präsente Unternehmen, bei denen eine Website möglicherweise auf einem Kontinent gehostet wird, während Benutzer auf der anderen Seite der Welt auf deren Inhalte zugreifen. Mithilfe von CDNs kann dem Abhilfe geschaffen werden, da beliebte Webressourcen an verschiedenen Standorten näher am Endbenutzer gehostet werden.</span><span class="sxs-lookup"><span data-stu-id="57d8a-p102">When creating pages for SharePoint Online, latency can be affected by the physical distance between your users and the location of the SharePoint Online instance. This is particularly important for organizations that have a global presence where a site may be hosted on one continent while users on the other side of the world are accessing its content. CDNs help mitigate this situation by hosting certain popular web assets in different locations closer to the end users.</span></span>
  
<span data-ttu-id="57d8a-p103">Da es sich beim CDN um ein weltweites Netzwerk von Servern handelt, die die gleichen Dateien hosten, werden die Internet-URLs für in den CDNs gespeicherten Dateien durch den Clientcomputer interpretiert, sodass der Server, der dem Benutzer am nächsten ist, die Datei verarbeitet. Dadurch lassen sich Verzögerungen durch Netzwerkroundtrips deutlich reduzieren.</span><span class="sxs-lookup"><span data-stu-id="57d8a-p103">Since a CDN is a worldwide network of servers that host the same files, Internet URLs for files stored on the CDNs are interpreted by the client machine so that the server that is closest to the user serves the file. Doing this significantly reduces delays caused by network round trips.</span></span>
  
## <a name="the-challenge-of-hosting-sharepoint-online-sites-for-a-global-audience"></a><span data-ttu-id="57d8a-116">Die Herausforderung beim Hosten von SharePoint Online-Websites für eine globale Zielgruppe</span><span class="sxs-lookup"><span data-stu-id="57d8a-116">The challenge of hosting SharePoint Online sites for a global audience</span></span>

<span data-ttu-id="57d8a-p104">SharePoint Online-Websites werden in Datencentern relativ zum Standort (angegeben durch den Benutzer) gehostet. Dieser wird beim Anmelden in Office 365 ausgewählt. Wenn sich Ihre Website beispielsweise auf Servern in den USA befindet und Benutzer von Ostasien aus auf diese Website zugreifen, können sich aufgrund der Entfernung, die die Daten über Glasfaserkabel überwinden müssen, Probleme mit der Latenz ergeben.</span><span class="sxs-lookup"><span data-stu-id="57d8a-p104">SharePoint Online sites are hosted at datacenters relative to the location (specified by the user) selected when you signed up with Office 365. For example, if your site is on servers in the United States and you have users accessing the site from East Asia, latency issues might arise due to the distance the data has to travel over fiber optic cable.</span></span>
  
<span data-ttu-id="57d8a-p105">Viele statische Dateien, die von der standardmäßigen SharePoint-Benutzeroberfläche verwendet werden bereits CDNs weltweit Netzwerk von Microsoft gehostet. Dadurch wird die Leistung über einen Zeitraum verbessert. Jedoch, wenn Sie eine beliebige beliebte JavaScript und CSS-Objekte (z. b; verwenden JQuery, Modernizr, Bootstrap oder ASP.NET Ajax) Sie können die Zeiten Laden dieser Dateien verbessern, indem Sie CDNs frei verfügbar.</span><span class="sxs-lookup"><span data-stu-id="57d8a-p105">Many static files used by the default SharePoint user interface are already hosted on Microsoft's worldwide network of CDNs. This will improve performance over time. However, if you use any popular JavaScript and CSS assets (for example; JQuery, Modernizr, Bootstrap, or ASP.NET Ajax) you can improve the loading times of these files by using freely available CDNs.</span></span>
  
## <a name="advantages-of-using-cdns-to-improve-download-speed"></a><span data-ttu-id="57d8a-122">Vorteile beim Einsatz von CDNs zur Verbesserung der Downloadgeschwindigkeit</span><span class="sxs-lookup"><span data-stu-id="57d8a-122">Advantages of using CDNs to improve download speed</span></span>

<span data-ttu-id="57d8a-p106">Seitenladezeiten für aus verschiedenen Gründen kann mit CDNs verbessert werden. Ein Grund ist, dass der Abstand zwischen dem CDN und der Benutzer möglicherweise kürzer als der Abstand für die SharePoint Online-Instanz. Diese Netzwerke stark verteilt werden und auch sehr hohe Verfügbarkeit und die Antwortzeit Zeiten haben sollen. Ein weiterer Grund ist, die, falls Sie eine beliebte Bibliothek mit CSS-Dateien, in Verbindung mit einem CDN, der Benutzer möglicherweise bereits der Bibliothek zwischengespeichert und sie nicht selbst es überhaupt herunterladen müssen.</span><span class="sxs-lookup"><span data-stu-id="57d8a-p106">Using CDNs can improve page load times for a variety of reasons. One reason is that the distance between the CDN and the user may be shorter than the distance to the SharePoint Online instance. These networks are highly distributed and are also designed to have very high availability and response times. Another reason is that if you are using a popular library of CSS files, in conjunction with a CDN, the user may already have the library cached and they won't even need to download it at all.</span></span>
  
<span data-ttu-id="57d8a-p107">Die folgenden Screenshots veranschaulichen die Vorteile der Verwendung von CDNs. Diese Screenshots stammen aus der Registerkarte **Netzwerk** in den Internet Explorer 11 Developer Tools. Diese Screenshots anzeigen die Wartezeit auf die jQuery beliebte Bibliothek. Drücken Sie die **F12** und wählen Sie die Registerkarte **Netzwerk** , die mit einem Wi-Fi-Symbol symbolisiert ist, um diesem Bildschirm in Internet Explorer anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="57d8a-p107">The following screen shots illustrate the advantages of using CDNs. These screen shots are from the **Network** tab in the Internet Explorer 11 developer tools. These screen shots show the latency on the popular library jQuery. To bring up this screen, in Internet Explorer, press **F12** and select the **Network** tab which is symbolized with a Wi-Fi icon.</span></span> 
  
![Screenshot des F12-Netzwerks](media/930541fd-af9b-434a-ae18-7bda867be128.png)
  
<span data-ttu-id="57d8a-p108">Dieser Screenshot zeigt die Bibliothek auf den Gestaltungsvorlagenkatalog auf der SharePoint Online-Website selbst hochgeladen. Die Zeit die Bibliothek hochladen ist 1.51 Sekunden.</span><span class="sxs-lookup"><span data-stu-id="57d8a-p108">This screen shot shows the library uploaded to the master page gallery on the SharePoint Online site itself. The time it took to upload the library is 1.51 seconds.</span></span>
  
![Screenshot der Ladezeit von 1,51 s](media/64225c79-fa53-480f-81cd-0d351674320e.png)
  
<span data-ttu-id="57d8a-p109">Der zweite Screenshot zeigt dieselbe Datei von Microsoft bereitgestellt CDN. Dieses Mal ist die Wartezeit rund 496 Millisekunden. Dies ist eine große Verbesserung und zeigt an, dass eine gesamte Sekunde deaktiviert die Gesamtzeit zum Herunterladen des Seiteninhalts shaved ist.</span><span class="sxs-lookup"><span data-stu-id="57d8a-p109">The second screen shot shows the same file delivered by Microsoft's CDN. This time the latency is around 496 milliseconds. This is a large improvement and shows that a whole second is shaved off the total time to download the page content.</span></span>
  
![Screenshot der Ladezeiten in 469 ms](media/6a553cc3-25a0-42c1-aae7-4aebbc2eb4c3.png)
  
## <a name="using-cdns-with-sharepoint-server-2013"></a><span data-ttu-id="57d8a-139">Verwenden von CDNs mit SharePoint Server 2013</span><span class="sxs-lookup"><span data-stu-id="57d8a-139">Using CDNs with SharePoint Server 2013</span></span>

<span data-ttu-id="57d8a-p110">Mit CDNs nur sinnvoll in einem SharePoint Online Kontext und sollte vermieden werden, mit SharePoint Server 2013. Dies ist, da alle die Vorteile im Zusammenhang mit geografischen Standort nicht geografisch trotzdem schließen oder halten Sie True, wenn der Server lokale gespeichert ist. Darüber hinaus ist eine Netzwerkverbindung mit den Servern, auf dem er gehostet wird, klicken Sie dann die Website kann ohne Verbindung zum Internet verwendet werden und die CDN-Dateien aus diesem Grund kann nicht abgerufen werden. Anderenfalls sollten Sie ein CDN verwenden, wenn vorhanden ist und für die Bibliothek und Dateien stabil für Ihre Website müssen.</span><span class="sxs-lookup"><span data-stu-id="57d8a-p110">Using CDNs only makes sense in a SharePoint Online context and should be avoided with SharePoint Server 2013. This is because all of the advantages around geographic location do not hold true if the server is located on-premises or geographically close anyway. Additionally, if there is a network connection to the servers where it's hosted, then the site may be used without an Internet connection and therefore cannot retrieve the CDN files. Otherwise, you should use a CDN if there is one available and stable for the library and files you need for your site.</span></span>
  
## <a name="popular-cdns-and-how-to-use-them"></a><span data-ttu-id="57d8a-144">Beliebte CDNs und deren Verwendung</span><span class="sxs-lookup"><span data-stu-id="57d8a-144">Popular CDNs and how to use them</span></span>

<span data-ttu-id="57d8a-145">Microsoft Ajax-CDN bietet die meisten der beliebten Bibliotheken jQuery (und alle anderen Bibliotheken), einschließlich ASP.NET Ajax, Bootstrap, Knockout.js und vieles mehr.</span><span class="sxs-lookup"><span data-stu-id="57d8a-145">Microsoft's Ajax CDN offers most of the popular libraries including jQuery (and all of its other libraries), ASP.NET Ajax, Bootstrap, Knockout.js, and many more.</span></span>
  
<span data-ttu-id="57d8a-p111">Um diese Skripts in Ihrem Projekt zu verwenden, ersetzen Sie einfach alle Verweise auf diese öffentlich zugänglichen Bibliotheken durch Verweise auf die CDN-Adresse, anstatt sie in das Projekt selbst aufzunehmen. Verwenden Sie z. B. den folgenden Code für die Verknüpfung mit jQuery:</span><span class="sxs-lookup"><span data-stu-id="57d8a-p111">To include these scripts in your project, simply replace any references to these publicly available libraries with references to the CDN address instead of including it in your project itself. For example, use the following code to link to jQuery:</span></span>
  
```
<script src=http://ajax.aspnetcdn.com/ajax/jquery-2.1.1.js> </script>
```

<span data-ttu-id="57d8a-148">Weitere Informationen zu CDNs finden Sie unter [Inhaltsübermittlung](content-delivery-networks.md).</span><span class="sxs-lookup"><span data-stu-id="57d8a-148">For more information about CDNs, see [Content delivery networks](content-delivery-networks.md).</span></span>
  
## <a name="more-topics-about-using-cdns-with-sharepoint"></a><span data-ttu-id="57d8a-149">Weitere Themen zur Verwendung von CDNs mit SharePoint</span><span class="sxs-lookup"><span data-stu-id="57d8a-149">More topics about using CDNs with SharePoint</span></span>

[<span data-ttu-id="57d8a-150">Mithilfe der clientseitigen hostingwebparts aus Office 365 CDN</span><span class="sxs-lookup"><span data-stu-id="57d8a-150">Hosting client-side web part from Office 365 CDN</span></span>](https://dev.office.com/sharepoint/docs/spfx/web-parts/get-started/hosting-webpart-from-office-365-cdn)
  

