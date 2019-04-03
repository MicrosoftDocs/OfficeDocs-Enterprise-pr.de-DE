---
title: Inhalts Bereitstellungs Netzwerke
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 4/2/2019
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 0140f704-6614-49bb-aa6c-89b75dcd7f1f
description: Verwenden Sie diese Informationen, um zu erfahren, wie Office 365 CDNs (Content subNetz) verwendet, um die Leistung zu verbessern.
ms.openlocfilehash: 5d02b28fad0e47473cc6a75948c9dd27e6728bb5
ms.sourcegitcommit: 43d2b7e1d9932182c6cca5164d4d9096dcf4ed36
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/02/2019
ms.locfileid: "31039482"
---
# <a name="content-delivery-networks-cdns"></a>Inhalts Bereitstellungs Netzwerke (CDNs)

CDNs helfen, Office 365 für Endbenutzer schnell und zuverlässig zu halten. Cloud-Dienste wie Office 365 verwenden CDNs zum Zwischenspeichern statischer Ressourcen in der Nähe der Browser, die Sie anfordern, um die Downloads zu beschleunigen und die vermeintliche Endbenutzer Wartezeit zu verringern. Anhand der Informationen in diesem Thema erfahren Sie mehr über Content subNetze (CDNs) und wie diese von Office 365 verwendet werden.

## <a name="what-exactly-is-a-cdn"></a>Was genau ist ein CDN?

Ein CDN ist ein geografisch verteiltes Netzwerk, das aus Proxy-und Dateiservern in Datencentern besteht, die über Hochgeschwindigkeits-Backbone-Netzwerke verbunden sind. CDNs werden verwendet, um die Wartezeit und Ladezeit für eine bestimmte Gruppe von Dateien und Objekten in einer Website oder einem Dienst zu reduzieren. Ein CDN kann viele Tausende von Endpunkten für eine optimale Wartung eingehender Anforderungen von einem beliebigen Standort aus aufweisen.

CDNs werden häufig verwendet, um eine schnellere Downloads generischer Inhalte für eine Website oder einen Dienst wie JavaScript-Dateien, Symbole und Bilder bereitzustellen, und Sie können auch privaten Zugriff auf Benutzer Inhalte wie Dateien in SharePoint Online-Dokumentbibliotheken, Streaming-Mediendateien und benutzerdefinierter Code.

CDNs werden von den meisten Enterprise-Cloud-Diensten verwendet. Cloud-Dienste wie Office 365 haben Millionen von Kunden, die gleichzeitig eine Mischung aus proprietären Inhalten (wie e-Mails) und generischen Inhalten (beispielsweise Symbole) herunterladen. Es ist effizienter, Bilder, die von allen Benutzern verwendet werden, wie beispielsweise Symbole, so weit wie möglich auf dem Computer des Benutzers zu platzieren. Es ist nicht für jeden Cloud-Dienst praktikabel, CDN-Datencenter zu erstellen, in denen dieser generische Inhalt in jedem Ballungsraum oder sogar in jedem wichtigen Internet-Hub auf der ganzen Welt gespeichert ist, sodass einige dieser CDNs gemeinsam genutzt werden.

## <a name="how-do-cdns-make-services-work-faster"></a>Wie können CDNs Dienste schneller arbeiten?

Das Herunterladen häufiger Objekte wie Symbole kann Netzwerkbandbreite beanspruchen, die für das Herunterladen wichtiger persönlicher Inhalte wie e-Mails oder Dokumente besser verwendet werden kann. Da Office 365 eine Architektur mit CDNs verwendet, können die Symbole, Skripts und andere generische Inhalte von Servern heruntergeladen werden, die näher an Clientcomputer Herangehen, wodurch die Downloads schneller ausgeführt werden. Das bedeutet einen schnelleren Zugriff auf Ihre persönlichen Inhalte, der sicher in Office 365-Rechenzentren gespeichert ist.

CDNs helfen, die Leistung des Cloud-Diensts auf verschiedene Weise zu verbessern:

- CDNs verschieben Sie einen Teil der Netzwerk-und Dateidownload Last weg vom Cloud-Dienst, sodass Sie Cloud-Dienst Ressourcen für die Bereitstellung von Benutzerinhalten und anderen Diensten freigeben können, indem Sie die Notwendigkeit verringern, Anforderungen für statische Objekte zu erfüllen.
- CDNs sind für den Dateizugriff mit niedriger Latenz vorgesehen, indem Hochleistungsnetzwerke und Dateiserver implementiert und aktualisierte Netzwerkprotokolle wie [http/2](https://en.wikipedia.org/wiki/HTTP/2) mit hocheffizienter Komprimierung und Anforderungs Multiplexing genutzt werden.
- CDN-Netzwerke verwenden viele global verteilte Endpunkte, um den Benutzern Inhalte so weit wie möglich zur Verfügung zu stellen.

## <a name="the-office-365-cdn"></a>Office 365 CDN

Das integrierte Office 365 Content Delivery Network (CDN) ermöglicht es Office 365-Administratoren, eine bessere Leistung für die SharePoint Online-Seiten Ihrer Organisation bereitzustellen, indem statische Objekte näher an den Browsern, die Sie anfordern, zwischengespeichert werden, was zur Beschleunigung herunterladen und verringern der Wartezeit. Das Office 365 CDN verwendet das [http/2-Protokoll](https://en.wikipedia.org/wiki/HTTP/2) , um die Komprimierungs-und Downloadgeschwindigkeit zu erhöhen.

Das Office 365-Netzwerk für die Inhaltsübermittlung besteht aus mehreren CDNs, über die Sie statische Objekte an mehreren Speicherorten hosten können, oder aus _Ursprüngen_, die aus globalen Hochgeschwindigkeitsnetzwerken bedient werden. In Abhängigkeit von der Art der Inhalte, die Sie im Office 365-Netzwerk für die Inhaltsübermittlung hosten möchten, können Sie **öffentliche** Ursprünge, **private** Ursprünge oder beides hinzufügen.

![Office 365 CDN-konzeptionelles Diagramm] (media/O365-CDN/o365-cdn-flow-transparent.svg "Office 365 CDN-konzeptionelles Diagramm")

Auf Inhalte in **öffentlichen** Ursprüngen im Office 365-Netzwerk für die Inhaltsübermittlung kann anonym zugegriffen werden und von jeder Person, die URLs zu gehosteten Objekten aufweist. Da der Zugriff auf Inhalte in öffentlichen Ursprüngen anonym ist, sollten Sie diese nur zum Zwischenspeichern von nicht vertraulichen generischen Inhalten verwenden, z. B. JavaScript-Dateien, Skripts, Symbole oder Bilder. Das Office 365-Netzwerk für die Inhaltsübermittlung wird standardmäßig zum Herunterladen von allgemeinen Ressourcenobjekten verwenden, z. B. die Office 365-Clientanwendungen von einem öffentlichen Ursprung.

**Private** Ursprünge im Office 365-Netzwerk für die Inhaltsübermittlung bieten privaten Zugriff auf Benutzerinhalte, z. B. SharePoint Online-Dokumentbibliotheken, Websites und Medien wie Videos. Der Zugriff auf Inhalte in private Ursprüngen wird mit dynamisch generierten Token geschützt, auf diese Inhalte kann daher nur von Benutzern mit Berechtigungen für die ursprüngliche Dokumentbibliothek oder den ursprünglichen Speicherort zugegriffen werden. Private Ursprünge Office 365-Netzwerk für die Inhaltsübermittlung können nur für SharePoint Online-Inhalte verwendet werden, und Sie können auf Objekte nur über Umleitung von Ihrem SharePoint Online-Mandanten zugreifen.

Das Office 365-Netzwerk für die Inhaltsübermittlung ist in Ihrem SharePoint Online-Abonnement enthalten.

Weitere Informationen zur Verwendung des Office 365 CDN finden Sie unter [Verwenden des office 365 Content Delivery Network mit SharePoint Online](https://docs.microsoft.com/en-us/office365/enterprise/use-office-365-cdn-with-spo).

## <a name="other-microsoft-cdns"></a>Andere Microsoft-CDNs

Obwohl es sich nicht um einen Teil des Office 365 CDN handelt, können Sie diese CDNs in Ihrem Office 365-Mandanten für den Zugriff auf SharePoint-Entwicklungsbibliotheken, benutzerdefinierten Code und andere Zwecke verwenden, die außerhalb des Bereichs des Office 365 CDN liegen.

### <a name="azure-cdn"></a>Azure CDN

Sie können das **Azure CDN** verwenden, um Ihre eigene CDN-Instanz für das Hosten von benutzerdefinierten Webparts, Bibliotheken und anderen Ressourcenobjekten bereitzustellen, die es Ihnen ermöglicht, Zugriffstasten auf Ihr CDN-Speicher anzuwenden und eine bessere Kontrolle über Ihre CDN-Konfiguration auszuüben. Die Verwendung des Azure CDN ist nicht kostenlos und erfordert ein Azure-Abonnement.

Weitere Informationen zum Konfigurieren einer Azure CDN-Instanz finden Sie unter [Schnellstart: Integrieren eines Azure-speicherkontos mit Azure CDN](https://docs.microsoft.com/en-us/azure/cdn/cdn-create-a-storage-account-with-cdn).

Ein Beispiel dafür, wie das Azure CDN zum Hosten von SharePoint-Webparts verwendet werden kann, finden Sie unter [deploy your SharePoint Client-Side Web Part to Azure CDN](https://docs.microsoft.com/en-us/sharepoint/dev/spfx/web-parts/get-started/deploy-web-part-to-cdn).

Informationen zum Azure CDN PowerShell-Modul finden Sie unter [Manage Azure CDN with PowerShell](https://docs.microsoft.com/en-us/azure/cdn/cdn-manage-powershell).

### <a name="microsoft-ajax-cdn"></a>Microsoft AJAX CDN

Das **AJAX CDN** von Microsoft ist ein schreibGESCHÜTZTes CDN, das viele beliebte Entwicklungsbibliotheken anbietet, einschließlich jQuery (und alle anderen Bibliotheken), ASP.NET AJAX, Bootstrap, Knockout. js und andere.
  
Um diese Skripts in Ihr Projekt einzubeziehen, ersetzen Sie einfach alle Verweise auf diese öffentlich verfügbaren Bibliotheken durch Verweise auf die CDN-Adresse, anstatt Sie in Ihr Projekt selbst einzubinden. Verwenden Sie beispielsweise den folgenden Code, um einen Link zu jQuery zu erstellen:

``` html
<script src=http://ajax.aspnetcdn.com/ajax/jquery-2.1.1.js> </script>
```

Weitere Informationen zur Verwendung des Microsoft AJAX CDN finden Sie unter [Microsoft AJAX CDN](https://docs.microsoft.com/en-us/aspnet/ajax/cdn/overview).

## <a name="how-does-office-365-use-content-from-a-cdn"></a>Wie verwendet Office 365 Inhalte aus einem CDN?

Unabhängig davon, welches CDN Sie für Ihren Office 365-Mandanten konfigurieren, ist der grundlegende Datenabruf Prozess identisch.

1. Ihr Client (ein Browser oder eine Office-Clientanwendung) fordert Daten aus Office 365 an.

2. Office 365 gibt die Daten entweder direkt an Ihren Client zurück, oder wenn die Daten Teil einer Reihe von Inhalten sind, die im CDN gehostet werden, leitet Ihr Client an die CDN-URL um.

    a. Wenn die Daten bereits in einem _öffentlichen_ Ursprung zwischengespeichert sind, downloadet Ihr Client die Daten direkt vom nächstgelegenen CDN-Standort zu Ihrem Client.

    b. Wenn die Daten bereits in _privater_ Quelle zwischengespeichert sind, überprüft der CDN-Dienst die Berechtigungen ihres Office 365-Benutzerkontos auf den Ursprung. Wenn Sie über Berechtigungen verfügen, generiert SharePoint Online eine benutzerdefinierte URL, die aus dem Pfad des Objekts im CDN und zwei Zugriffstoken besteht, und gibt die benutzerdefinierte URL an den Client zurück. Der Client lädt die Daten dann direkt vom nächstgelegenen CDN-Standort auf Ihren Client, der die benutzerdefinierte URL verwendet.

3. Wenn die Daten nicht im CDN zwischengespeichert werden, fordert der CDN-Knoten die Daten von Office 365 an und speichert die Daten für einen bestimmten Zeitraum zwischen, nachdem der Client die Daten heruntergeladen hat.

Das CDN stellt das nächstgelegene Rechenzentrum für den Browser des Benutzers dar und downloadet die angeforderten Daten mithilfe der Umleitung von dort. Die CDN-Umleitung ist schnell und kann Benutzern eine große Downloadzeit sparen.

## <a name="how-should-i-set-up-my-network-so-that-cdns-work-best-with-office-365"></a>Wie richte ich mein Netzwerk so ein, dass CDNs am besten mit Office 365 funktioniert?

Das Minimieren der Wartezeit zwischen Clients in Ihrem Netzwerk und CDN-Endpunkten ist die wichtigste Erwägung, um eine optimale Leistung sicherzustellen. Sie können die in [Managing Office 365](managing-office-365-endpoints.md) Endpoints beschriebenen bewährten Methoden verwenden, um sicherzustellen, dass die Netzwerkkonfiguration es Clientbrowsern ermöglicht, direkt auf das CDN zuzugreifen, statt den Datenverkehr über zentrale Proxys zu übertragen, um die Einführung unnötige Wartezeit.

Sie können auch die [Grundprinzipien der office 365-Netzwerkkonnektivität](https://aka.ms/o365networkingprinciples) lesen, um die Konzepte für die Optimierung der Office 365-Netzwerkleistung zu verstehen.

## <a name="is-there-a-list-of-all-the-cdns-that-office-365-uses"></a>Gibt es eine Liste aller CDNs, die von Office 365 verwendet werden?

Die CDNs, die von Office 365 verwendet werden, können immer geändert werden, und in vielen Fällen werden mehrere CDN-Partner konfiguriert, falls eine nicht verfügbar ist. Die primären CDNs, die von Office 365 verwendet werden, sind:

|CDN  |Company  |Verwendung  |Linkdatenbank  |
|---------|---------|---------|---------|
|Office 365 CDN     |Akamai         |Generische Objekte in öffentlichen Ursprüngen, SharePoint-Benutzer Inhalte in privaten Quellen         |[Verwenden des Office 365 Content Delivery Network mit SharePoint Online](https://docs.microsoft.com/en-us/office365/enterprise/use-office-365-cdn-with-spo)         |
|Azure CDN     |Microsoft         |Benutzerdefinierter Code, SharePoint-Framework-Lösungen         |[Microsoft Azure CDN](https://azure.microsoft.com/documentation/services/cdn/)         |
|Microsoft AJAX CDN (schreibgeschützt)     |Microsoft         |Allgemeine Bibliotheken für AJAX, jQuery, ASP.NET, Bootstrap, Knockout. js usw.         |[Microsoft AJAX CDN](https://docs.microsoft.com/en-us/aspnet/ajax/cdn/overview)         |

## <a name="what-performance-gains-does-a-cdn-provide"></a>Welche Leistungsgewinne bietet ein CDN?

Es gibt viele Faktoren, die sich auf das Messen bestimmter Unterschiede bei der Leistung zwischen Daten beziehen, die direkt von Office 365 heruntergeladen werden, und von Daten, die von einem bestimmten CDN heruntergeladen wurden, wie beispielsweise Ihrem Standort relativ zu Ihrem Mandanten und dem nächsten CDN-Endpunkt, der Anzahl Ressourcen auf einer Seite, die vom CDN bedient werden, sowie vorübergehende Änderungen bei der Netzwerkwartezeit und-Bandbreite. Ein einfacher A/B-Test kann jedoch dazu beitragen, die Unterschiede bei der Downloadzeit für eine bestimmte Datei anzuzeigen.

Die folgenden Screenshots veranschaulichen den Unterschied zwischen der Downloadgeschwindigkeit zwischen dem systemeigenen Dateispeicherort in Office 365 und der gleichen Datei, die im [Microsoft AJAX Content Zulieferungs Netzwerk](https://docs.microsoft.com/en-us/aspnet/ajax/cdn/overview)gehostet wird. Diese Screenshots befinden sich auf der Registerkarte **Netzwerk** in den Entwicklertools von Internet Explorer 11. Diese Screenshots zeigen die Wartezeit für die beliebte Bibliothek jQuery. Drücken Sie zum Öffnen dieses Bildschirms in Internet Explorer **F12** , und wählen Sie die Registerkarte **Netzwerk** , die mit einem Wi-Fi-Symbol symbolisiert wird.
  
![Screenshot des F12-Netzwerks](media/930541fd-af9b-434a-ae18-7bda867be128.png)
  
Dieser Screenshot zeigt die Bibliothek, die in den gestaltungsvorlagenkatalog auf der SharePoint Online-Website hochgeladen wurde. Die Zeit, die zum Hochladen der Bibliothek benötigt wird, beträgt 1,51 Sekunden.
  
![Screenshot der Ladezeit 1.51 s](media/64225c79-fa53-480f-81cd-0d351674320e.png)
  
Der zweite Screenshot zeigt dieselbe Datei an, die vom CDN von Microsoft bereitgestellt wurde. Dieses Mal beträgt die Wartezeit rund 496 Millisekunden. Dies ist eine deutliche Verbesserung und zeigt, dass die gesamte Zeit zum Herunterladen des Objekts eine ganze Sekunde lang abrasiert wird.
  
![Screenshot der Ladezeiten in 469 MS](media/6a553cc3-25a0-42c1-aae7-4aebbc2eb4c3.png)

## <a name="is-my-data-safe"></a>Sind meine Daten sicher?

Wir bemühen uns sehr, die Daten zu schützen, die Ihr Unternehmen ausführen. Im Office 365 CDN gespeicherte Daten werden sowohl während der Übertragung als auch im Rest verschlüsselt, und der Zugriff auf Daten im Office 365 SharePoint CDN wird durch Benutzerberechtigungen und Token-Autorisierung von Office 365 gesichert. Anforderungen an Daten im Office 365 SharePoint CDN müssen von Ihrem Office 365-Mandanten verwiesen werden, oder es wird kein Autorisierungstoken generiert.

Um sicherzustellen, dass Ihre Daten sicher bleiben, empfiehlt es sich, niemals Benutzer Inhalte oder andere vertrauliche Daten in einem öffentlichen CDN zu speichern. Da der Zugriff auf Daten in einem öffentlichen CDN anonym ist, sollten öffentliche CDNs nur zum Hosten generischer Inhalte wie webskriptdateien, Symbole, Bilder und andere nicht vertrauliche Objekte verwendet werden.

> [!NOTE]
> Drittanbieter-CDN-Anbieter haben möglicherweise Datenschutz-und Konformitätsstandards, die von den vom Office 365 Trust Center beschriebenen Verpflichtungen abweichen. Daten, die über den CDN-Dienst zwischengespeichert werden, sind möglicherweise nicht mit den Microsoft-datenVerarbeitungsBedingungen kompatibel und können außerhalb der Kompatibilitäts Grenzen von Office 365 Trust Center liegen.

Ausführliche Informationen zum Datenschutz und zur Sicherheit für Office 365 CDN-Anbieter finden Sie unter:  

- Weitere Informationen zu Office 365 Datenschutz im [Microsoft Trust Center](https://www.microsoft.com/trustcenter)
- Erfahren Sie mehr über den Datenschutz und die Vertraulichkeit von Akamai im [Akamai Privacy Trust Center](https://www.akamai.com/us/en/about/compliance/data-protection-at-akamai.jsp) .
- Weitere Informationen zu Azure Privacy and Data Protection im [Azure Trust Center](https://azure.microsoft.com/en-us/overview/trusted-cloud/)

## <a name="how-can-i-secure-my-network-with-all-these-3rd-party-services"></a>Wie kann ich mein Netzwerk mit all diesen 3rd-Party-Diensten sichern?

Die Nutzung einer umfangreichen Reihe von Partnerdiensten ermöglicht Office 365 die Skalierung und Erfüllung der Verfügbarkeitsanforderungen sowie die Verbesserung der Benutzerfreundlichkeit bei der Verwendung von Office 365. Die 3rd Party Services Office 365 leverages umfasst beide Zertifikatssperrlisten; wie crl.microsoft.com oder sa.symcb.com und CDNs; wie R3.res.Outlook.com. Jeder von Office 365 generierte CDN-FQDN ist ein benutzerdefinierter FQDN für Office 365. Wenn Sie auf Anforderung von Office 365 an einen FQDN gesendet werden, können Sie sicher sein, dass der CDN-Anbieter den FQDN und den zugrunde liegenden Inhalt an diesem Speicherort steuert.
  
Für Kunden, die Anforderungen für ein Microsoft-oder Office 365-Datencenter aus Anforderungen trennen möchten, die für einen Drittanbieter bestimmt sind, haben wir Anweisungen zur [Verwaltung von Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)-Endpunkten verfasst.

## <a name="is-there-a-list-of-all-the-fqdns-that-leverage-cdns"></a>Gibt es eine Liste aller FQDNs, die CDNs nutzen?

Die Liste der FQDNs und ihre Verwendung von CDNs-Änderungen im Laufe der Zeit. Informieren Sie sich auf der Seite "veröffentlichte [Office 365-URLs und IP-Adressbereiche](https://go.microsoft.com/fwlink/p/?LinkID=293744) ", um auf die neuesten FQDNs zu aktualisieren, die CDNs nutzen.

Sie können auch den [office 365-IP-Adress-und-URL-Webdienst](https://docs.microsoft.com/en-us/office365/enterprise/office-365-ip-web-service) verwenden, um die aktuellen Office 365-URLs und IP-Adressbereiche anzufordern, die als CSV oder JSON formatiert sind.

## <a name="can-i-use-my-own-cdn-and-cache-content-on-my-local-network"></a>Kann ich mein eigenes CDN verwenden und Inhalte in meinem lokalen Netzwerk Zwischenspeichern?

Wir suchen ständig nach neuen Möglichkeiten, um die Anforderungen unserer Kunden zu erfüllen, und untersuchen derzeit die Verwendung von zwischen Speicherungs Proxy Lösungen und anderen lokalen CDN-Lösungen.

Obwohl es nicht Bestandteil des Office 365 CDN ist, können Sie auch das **Azure CDN** zum Hosten von benutzerdefinierten Webparts, Bibliotheken und anderen Ressourcenobjekten verwenden, mit denen Sie Zugriffstasten auf Ihr CDN-Speicher anwenden und eine bessere Kontrolle über Ihre CDN-Konfiguration ausüben. Die Verwendung des Azure CDN ist nicht kostenlos und erfordert ein Azure-Abonnement. Weitere Informationen zum Konfigurieren einer Azure CDN-Instanz finden Sie unter [Schnellstart: Integrieren eines Azure-speicherkontos mit Azure CDN](https://docs.microsoft.com/en-us/azure/cdn/cdn-create-a-storage-account-with-cdn).

## <a name="im-using-azure-expressroute-for-office-365-does-that-change-things"></a>Ich verwende Azure Express Route für Office 365, ändert sich das?

[Azure Express Route für office 365](azure-expressroute.md) bietet eine dedizierte Verbindung zur Office 365-Infrastruktur, die vom öffentlichen Internet getrennt ist. Dies bedeutet, dass Clients weiterhin eine Verbindung über nicht-Express Route-Verbindungen herstellen müssen, um eine Verbindung mit CDNs und anderen Microsoft-Infrastrukturen herzustellen, die nicht explizit in der Liste der von Express Route unterstützten Dienste enthalten sind. Weitere Informationen zum Weiterleiten bestimmter Datenverkehr wie Anforderungen für CDNs finden Sie unter [Office 365 Network Traffic Management](routing-with-expressroute.md).

## <a name="can-i-use-cdns-with-sharepoint-server-on-premises"></a>Kann ich CDNs mit SharePoint Server lokal verwenden?

Die Verwendung von CDNs ist nur in einem SharePoint Online-Kontext sinnvoll und sollte mit SharePoint Server vermieden werden. Dies liegt daran, dass alle Vorteile rund um den geografischen Standort nicht wahr sind, wenn sich der Server ohnehin lokal oder geografisch geschlossen befindet. Wenn eine Netzwerkverbindung zu den Servern vorhanden ist, auf denen Sie gehostet wird, kann die Website außerdem ohne Internet Verbindung verwendet werden und kann daher keine CDN-Dateien abrufen. Andernfalls sollten Sie ein CDN verwenden, wenn für die Bibliothek und die Dateien, die Sie für Ihre Website benötigen, eine verfügbar und stabil ist.
  
Mit diesem kurzen Link gelangen Sie wieder hierher zurück: [https://aka.ms/o365cdns](https://aka.ms/o365cdns)
  
## <a name="see-also"></a>Siehe auch

[Prinzipien von Office 365-Netzwerkverbindungen](https://aka.ms/o365networkingprinciples)

[Netzwerkkonnektivität mit Office 365](network-connectivity.md)

[Verwalten von Office 365-Endpunkten](https://docs.microsoft.com/en-us/office365/enterprise/managing-office-365-endpoints)

[URLs und IP-Adressbereiche für Office 365](https://go.microsoft.com/fwlink/p/?LinkID=293744)

[Verwenden des Office 365 Content Delivery Network mit SharePoint Online](https://docs.microsoft.com/en-us/office365/enterprise/use-office-365-cdn-with-spo)

[Microsoft Trust Center](https://www.microsoft.com/trustcenter)