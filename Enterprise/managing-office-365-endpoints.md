---
title: Verwalten von Office 365-Endpunkten
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 02/21/2019
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom: Adm_O365_Setup
search.appverid: MOE150
ms.assetid: 99cab9d4-ef59-4207-9f2b-3728eb46bf9a
description: Einige Enterprise-Netzwerke schränken den Zugriff auf generische Internetstandorte oder umfangreiche Backhaul oder die Verarbeitung des Netzwerkdatenverkehrs ein. Um sicherzustellen, dass Computer in Netzwerken wie diesen auf Office 365 zugreifen können, müssen Netzwerk-und Proxy Administratoren die Liste der FQDNs, URLs und IP-Adressen verwalten, die die Liste der Office 365-Endpunkte bilden. Diese müssen zu Direct Route, Proxy Bypass und/oder Firewallregeln und PAC-Dateien hinzugefügt werden, um sicherzustellen, dass Netzwerkanforderungen in der Lage sind, Office 365 zu erreichen.
ms.openlocfilehash: d9138dd5d583b684c82d525001faee4d06e0fbe5
ms.sourcegitcommit: eb52922c0ee34791fd71ae78338ab203f7761eec
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/28/2019
ms.locfileid: "30341986"
---
# <a name="managing-office-365-endpoints"></a>Verwalten von Office 365-Endpunkten

Die meisten Unternehmensorganisationen mit mehreren Office-Standorten und einem Verbindungs-WAN benötigen die Konfiguration für die Office 365-Netzwerkkonnektivität. Sie können Ihr Netzwerk optimieren, indem Sie alle vertrauenswürdigen Office 365-Netzwerkanforderungen direkt über Ihre Firewall senden, um alle zusätzlichen Überprüfungen auf Paketebene zu umgehen. Dadurch werden die Wartezeit und die Kapazitätsanforderungen für Perimeter reduziert. Die Identifizierung von Office 365-Netzwerkdatenverkehr ist der erste Schritt bei der Bereitstellung einer optimalen Leistung für Ihre Benutzer. Weitere Informationen zur Netzwerkkonnektivität von Office 365 finden Sie unter [office 365 Network Connectivity Principles](office-365-network-connectivity-principles.md)

Microsoft empfiehlt, dass Sie auf die Office 365-Netzwerkendpunkte zugreifen und diese mithilfe des [office 365-IP-Adress-und URL](office-365-ip-web-service.md) -Webdiensts ändern.

Unabhängig davon, wie Sie den wichtigen Office 365-Netzwerkdatenverkehr verwalten, erfordert Office 365 eine Internet Verbindung. Weitere Netzwerkendpunkte, bei denen Konnektivität erforderlich ist, werden an zusätzlichen Endpunkten aufgeführt, [die nicht im Office 365 IP-Adress-und URL-Webdienst enthalten](additional-office365-ip-addresses-and-urls.md) sind.

Die Verwendung der Office 365-Netzwerkendpunkte hängt von der Netzwerkarchitektur ihrer Unternehmensorganisation ab. In diesem Artikel werden verschiedene Möglichkeiten beschrieben, wie Unternehmensnetzwerk Architekturen in Office 365-IP-Adressen und-URLs integriert werden können. Am einfachsten können Sie auswählen, welche Netzwerkanforderungen vertrauenswürdig sind, indem Sie SDWAN-Geräte verwenden, die die automatisierte Office 365-Konfiguration an jedem Ihrer Office-Standorte unterstützen.

## <a name="sdwan-for-local-branch-egress-of-vital-office-365-network-traffic"></a>SDWAN für den Ausstieg der lokalen Niederlassung des wichtigen Office 365-Netzwerkverkehrs

An jedem Standort der Zweigstelle können Sie ein SDWAN-Gerät bereitstellen, das für die Weiterleitung des Datenverkehrs für Office 365 Optimierungs Kategorie von Endpunkten konfiguriert ist, oder das optimieren und zulassen von Kategorien direkt zum Microsoft-Netzwerk. Andere Netzwerkdatenverkehr einschließlich des lokalen Datencenter Datenverkehrs, des allgemeinen Internet-Website Verkehrs und des Datenverkehrs zu Office 365 standardmäßige Kategorie-Endpunkte werden an einen anderen Ort gesendet, an den Sie einen größeren Umkreis des Netzwerks haben.

Microsoft arbeitet mit SDWAN-Anbietern zusammen, um die automatische Konfiguration zu aktivieren. Weitere Informationen finden Sie unter [Office 365 Networking Partner Program](office-365-networking-partner-program.md).

<a name="pacfiles"> </a>
## <a name="use-a-pac-file-for-direct-routing-of-vital-office-365-traffic"></a>Verwenden einer PAC-Datei zum direkten Weiterleiten von wichtigen Office 365-Datenverkehr

Verwenden Sie PAC-oder WPAD-Dateien zum Verwalten von Netzwerkanforderungen, die mit Office 365 verknüpft sind, aber keine IP-Adresse besitzen. Bei typischen Netzwerkanforderungen, die über einen Proxy oder ein Umkreis Gerät gesendet werden, wird die Wartezeit erhöht. Während SSL-Unterbrechung und-Prüfung die größte Wartezeit verursacht, können andere Dienste wie Proxyauthentifizierung und Reputations Suche zu einer schlechten Leistung und einer schlechten Benutzerfreundlichkeit führen. Darüber hinaus benötigen diese Umkreisnetzwerk Geräte genügend Kapazität, um alle Netzwerkverbindungsanforderungen zu verarbeiten. Es wird empfohlen, Ihre Proxy-oder Inspektionsgeräte für Direct Office 365-Netzwerkanforderungen zu umgehen.
  
[PowerShell Gallery Get-PacFile](https://www.powershellgallery.com/packages/Get-PacFile) ist ein PowerShell-Skript, das die neuesten Netzwerkendpunkte aus dem Office 365-IP-Adress-und-URL-Webdienst liest und eine PAC-Beispieldatei erstellt. Sie können das Skript so ändern, dass es in Ihre vorhandene PAC-Dateiverwaltung integriert wird.

![Herstellen einer Verbindung mit Office 365 über Firewalls und Proxys.](media/34d402f3-f502-42a0-8156-24a7c4273fa5.png)

**Abbildung 1: Umkreis des einfachen Unternehmensnetzwerks**

Die PAC-Datei wird in den Webbrowser unter Punkt 1 in Abbildung 1 bereitgestellt. Wenn Sie eine PAC-Datei für den direkten Ausstieg des wichtigen Office 365-Netzwerkdatenverkehrs verwenden, müssen Sie auch die Konnektivität zu den IP-Adressen hinter diesen URLs in ihrer Netzwerkumkreis Firewall zulassen. Hierzu holen Sie die IP-Adressen für die gleichen Office 365-Endpunkt Kategorien, die in der PAC-Datei angegeben sind, und erstellen Firewall-ACLs basierend auf diesen Adressen. Die Firewall ist Punkt 3 in Abbildung 1.

Wenn Sie sich für die Optimierung der Kategorie-Endpunkte nur für das direkte Routing entscheiden, müssen alle erforderlichen Allow Category-Endpunkte, die Sie an den Proxy Server senden, im Proxy Server aufgeführt werden, um die weitere Verarbeitung zu umgehen. Beispielsweise sind SSL-unterbrechungs-und-überPrüfung und Proxy Authentifizierung mit den Endpunkten optimize und Allow nicht kompatibel. Der Proxy Server ist Punkt 2 in Abbildung 1.

Die allgemeine Konfiguration besteht darin, ohne den gesamten ausgehenden Datenverkehr vom Proxy Server für die Ziel-IP-Adressen für den Office 365-Netzwerkdatenverkehr zu ermöglichen, der auf den Proxy Server trifft. Informationen zu Problemen mit SSL-unterbrechungs-und-überPrüfung finden Sie unter [Verwenden von Drittanbieter-Netzwerkgeräten oder-Lösungen im Office 365-Datenverkehr](https://support.microsoft.com/en-us/help/2690045/using-third-party-network-devices-or-solutions-with-office-365).

Es gibt zwei Arten von PAC-Dateien, die vom Get-PacFile-Skript generiert werden.

|**Typ**|**Beschreibung**|
|:-----|:-----|
|**1** <br/> |Senden Sie den Endpunkt Datenverkehr direkt und alle anderen Daten an den Proxy Server. <br/> |
|**2** <br/> |Senden Sie Optimize, und lassen Sie Endpunkt Datenverkehr direkt und alles andere auf den Proxy Server. Dieser Typ kann auch verwendet werden, um alle unterstützten Express Route für Office 365-Datenverkehr an Express Route-Netzwerksegmente und alles andere an den Proxy Server zu senden. <br/> |

Nachfolgend finden Sie ein einfaches Beispiel für das Aufrufen des PowerShell-Skripts:

```powershell
Get-PacFile -ClientRequestId b10c5ed1-bad1-445f-b386-b919946339a7
```

Es gibt eine Reihe von Parametern, die Sie an das Skript übergeben können:

|**Parameter**|**Beschreibung**|
|:-----|:-----|
|**ClientRequestId** <br/> |Dies ist erforderlich und ist eine GUID, die an den Webdienst übergeben wird, der den Clientcomputer darstellt, der den Anruf tätigt. <br/> |
|**Instance** <br/> |Die Office 365-Dienstinstanz, die standardmäßig weltweit verwendet wird. Wird auch an den Webdienst übergeben. <br/> |
|**TenantName** <br/> |Ihr Office 365-Mandantenname. Wird an den Webdienst übergeben und in einigen Office 365-URLs als austauschbarer Parameter verwendet. <br/> |
|**Typ** <br/> |Der Typ der Proxy-PAC-Datei, die Sie generieren möchten. <br/> |

Nachfolgend finden Sie ein weiteres Beispiel für das Aufrufen des PowerShell-Skripts mit zusätzlichen Parametern.

```powershell
Get-PacFile -Type 2 -Instance Worldwide -TenantName Contoso -ClientRequestId b10c5ed1-bad1-445f-b386-b919946339a7
```

## <a name="proxy-server-bypass-processing-of-office-365-network-traffic"></a>Proxy Server-Umgehungs Verarbeitung von Office 365-Netzwerkdatenverkehr

Wenn PAC-Dateien nicht für direkten ausgehenden Datenverkehr verwendet werden, möchten Sie die Verarbeitung in Ihrem Umkreisnetzwerk weiterhin umgehen, indem Sie Ihren Proxy Server konfigurieren. Einige Proxy Server Anbieter haben die automatische Konfiguration dieser Funktion aktiviert, wie im [Office 365 Networking Partner Program](office-365-networking-partner-program.md)beschrieben.

Wenn Sie dies manuell durchführen, müssen Sie die Daten zum Optimieren und zulassen der Endpunkt Kategorie aus dem Office 365-IP-Adress-und-URL-Webdienst abrufen und den Proxy Server konfigurieren, um die Verarbeitung für diese zu umgehen. Es ist wichtig, SSL-Unterbrechungen zu vermeiden und die Proxy Authentifizierung für die Endpunkte optimize und Allow zu überprüfen.
  
<a name="bkmk_changes"> </a>
## <a name="change-management-for-office-365-ip-addresses-and-urls"></a>Change Management für Office 365 IP-Adressen und URLs

Neben der Auswahl der geeigneten Konfiguration für Ihren Umkreis für das Netzwerk ist es wichtig, dass Sie einen Change Management-Prozess für Office 365-Endpunkte vornehmen. Diese Endpunkte ändern sich regelmäßig, und wenn Sie die Änderungen nicht verwalten, können Sie nach dem Hinzufügen einer neuen IP-Adresse oder-URL mit Benutzern blockiert oder mit schlechter Leistung arbeiten.

Änderungen an den Office 365-IP-Adressen und-URLs werden normalerweise am letzten Tag eines jeden Monats veröffentlicht. Manchmal wird eine Änderung außerhalb dieses Zeitplans aufgrund von Betriebs-, Support-oder Sicherheitsanforderungen veröffentlicht.

Wenn eine Änderung veröffentlicht wird, aufgrund derer Sie handeln müssen, da eine IP-Adresse oder URL hinzugefügt wurde, sollten Sie davon ausgehen, dass Sie 30 Tage nach der Veröffentlichung der Änderung erhalten, bis ein Office 365-Dienst an diesem Endpunkt vorhanden ist. Obwohl wir diesen Benachrichtigungszeitraum anstreben, ist es möglicherweise aufgrund von Betriebs-, Support-oder Sicherheitsanforderungen nicht immer möglich. Änderungen, die keine sofortige Aktion erfordern, um die Konnektivität zu gewährleisten, wie beispielsweise entfernte IP-Adressen oder URLs oder weniger wichtige Änderungen, schließen keine Vorwarnung ein. Unabhängig davon, welche Benachrichtigung angegeben wird, wird für jede Änderung das erwartete Dienst Datum angezeigt.

### <a name="change-notification-using-the-web-service"></a>Ändern der Benachrichtigung mithilfe des webDiensts

Sie können die Office 365-IP-Adresse und den URL-Webdienst verwenden, um Änderungsbenachrichtigungen abzurufen. Es wird empfohlen, dass Sie die **/Version** -Webmethode einmal pro Stunde aufrufen, um die Version der Endpunkte zu überprüfen, die Sie für die Verbindung mit Office 365 verwenden. Wenn sich diese Version im Vergleich zur verwendeten Version ändert, sollten Sie die neuesten Endpunkt Daten aus der **/Endpoints** -Webmethode abrufen und optional die Unterschiede zur **/Changes** -Webmethode abrufen. Es ist nicht erforderlich, die **/Endpoints** -oder **/Changes** -Webmethoden aufzurufen, wenn keine Änderung an der gefundenen Version vorgenommen wurde.

Weitere Informationen finden Sie unter [Office 365 IP-Adress-und URL-Webdienst](office-365-ip-web-service.md).

### <a name="change-notification-using-rss-feeds"></a>Ändern der Benachrichtigung mithilfe von RSS-Feeds

Der Office 365-IP-Adress-und-URL-Webdienst stellt einen RSS-Feed bereit, den Sie in Outlook abonnieren können. Es gibt Links zu den RSS-URLs auf den einzelnen Seiten der Office 365-Dienstinstanz für die IP-Adressen und URLs. Weitere Informationen finden Sie unter [Office 365 IP-Adress-und URL-Webdienst](office-365-ip-web-service.md).

### <a name="change-notification-and-approval-review-using-microsoft-flow"></a>Ändern der Benachrichtigungs-und Genehmigungs Überprüfung mithilfe von Microsoft Flow

Wir sind uns bewusst, dass Sie möglicherweise weiterhin manuelle Verarbeitung für Netzwerkendpunkt Änderungen benötigen, die jeden Monat durchlaufen. Sie können Microsoft Flow zum Erstellen eines Flusses verwenden, der Sie per e-Mail benachrichtigt und optional einen Genehmigungsprozess für Änderungen ausführt, wenn Office 365-Netzwerkendpunkte Änderungen aufweisen. Nach Abschluss der Überprüfungen können Sie die Änderungen automatisch an Ihr Firewall-und Proxy Server-Verwaltungsteam senden.

Informationen zu einem Microsoft Flow-Beispiel und einer Vorlage finden Sie unter [Verwenden von Microsoft Flow, um eine e-Mail für Änderungen an Office 365-IP-Adressen und-URLs zu erhalten](https://techcommunity.microsoft.com/t5/Office-365-Networking/Use-Microsoft-Flow-to-receive-an-email-for-changes-to-Office-365/td-p/240651) .
  
<a name="FAQ"> </a>
## <a name="office-365-network-endpoints-faq"></a>Office 365-Netzwerkendpunkte – häufig gestellte Fragen

Häufig gestellte Fragen zu Administratoren zu Office 365-Konnektivität:
  
### <a name="how-do-i-submit-a-question"></a>Wie kann ich eine Frage einreichen?

Klicken Sie unten auf den Link, um anzugeben, ob der Artikel hilfreich war, und geben Sie weitere Fragen an. Wir überwachen das Feedback und aktualisieren die Fragen hier mit den am häufigsten gestellten.
  
### <a name="how-do-i-determine-the-location-of-my-tenant"></a>Wie kann ich den Speicherort meines Mandanten ermitteln?

 Der **Standort** des Mandanten wird am besten mit unserer [Datencenter Karte](http://aka.ms/datamaps)ermittelt.
  
### <a name="am-i-peering-appropriately-with-microsoft"></a>Untersuche ich angemessen mit Microsoft?

 **Peering-Speicherorte** werden unter [Peering mit Microsoft](https://www.microsoft.com/peering)ausführlicher beschrieben.
  
Da über 2500 ISP-Peering-Beziehungen weltweit und 70-Punkte vorhanden sind, sollten Sie nahtlos von Ihrem Netzwerk zu uns gelangen. Es kann nicht weh tun, ein paar Minuten zu verbringen, um sicherzustellen, dass die Peering-Beziehung Ihres INTERNETdienstANBIETERs am besten ist, [hier ein paar Beispiele](https://blogs.technet.microsoft.com/onthewire/2017/03/22/__guidance/) für gute und nicht so gute Peering-offs für unser Netzwerk.
  
### <a name="i-see-network-requests-to-ip-addresses-not-on-the-published-list-do-i-need-to-provide-access-to-them"></a>Ich sehe Netzwerkanforderungen an IP-Adressen, die nicht in der veröffentlichten Liste enthalten sind, muss ich Ihnen Zugriff gewähren?
<a name="bkmk_MissingIP"> </a>

Es werden nur IP-Adressen für die Office 365-Server bereitgestellt, an die Sie direkt weitergeleitet werden sollen. Dies ist keine umfassende Liste aller IP-Adressen, für die Netzwerkanforderungen angezeigt werden. Es werden Netzwerkanforderungen an Microsoft und die Drittanbieter-, unveröffentlichten, IP-Adressen angezeigt. Diese IP-Adressen werden dynamisch generiert oder verwaltet, sodass eine rechtzeitige Benachrichtigung beim Ändern verhindert wird. Wenn Ihre Firewall keinen Zugriff basierend auf den FQDNs für diese Netzwerkanforderungen zulässt, verwenden Sie eine PAC-oder WPAD-Datei, um die Anforderungen zu verwalten.
  
Finden Sie eine IP-Adresse, die Office 365 zugeordnet ist und für die Sie weitere Informationen benötigen?
  
1. Überprüfen Sie, ob die IP-Adresse in einem größeren veröffentlichten Range mit einem [CIDR-Rechner](http://jodies.de/ipcalc)enthalten ist.
2. Prüfen Sie, ob ein Partner die IP-Adresse mit einer [Whois-Abfrage](https://dnsquery.org/)besitzt. Wenn Microsoft im Besitz ist, kann es sich um einen internen Partner handeln.
3. überprüfen sie das zertifikat, aktivieren sie in einem browser eine verbindung mit der ip-adresse mithilfe von *HTTPS://\<IP_ADDRESS\> * , überprüfen sie die domänen, die im zertifikat aufgeführt sind, um zu verstehen, welche domänen der ip-adresse zugeordnet sind. Wenn es sich um eine Microsoft-Besitz-IP-Adresse und nicht um die Liste der Office 365-IP-Adressen handelt, ist die IP-Adresse wahrscheinlich mit einem Microsoft CDN wie *MSOCDN.net* oder einer anderen Microsoft-Domäne ohne veröffentlichte IP-Informationen verbunden. Wenn Sie feststellen, dass die Domäne auf dem Zertifikat eine ist, in der wir die IP-Adresse auflisten möchten, teilen Sie uns dies bitte mit.

<a name="bkmk_cname"> </a>
### <a name="some-office-365-urls-point-to-cname-records-instead-of-a-records-in-the-dns-what-do-i-have-to-do-with-the-cname-records"></a>Einige Office 365-URLs verweisen auf CNAME-Einträge anstelle von Datensätzen im DNS. Was muss ich mit den CNAME-Einträgen tun?

Client Computer benötigen einen DNS-A-oder AAAA-Eintrag, der eine oder mehrere IP-Adressen enthält, um eine Verbindung mit einem clouddienst herzustellen. Einige in Office 365 enthaltene URLs zeigen CNAME-Einträge anstelle von A-oder AAAA-Einträgen an. Diese CNAME-Einträge sind Mittler und es kann mehrere in einer Kette geben. Sie werden immer schließlich zu einem A-oder AAAA-Eintrag für eine IP-Adresse aufgelöst. Betrachten Sie beispielsweise die folgende Reihe von DNS-Einträgen, die schließlich in die IP-Adresse _IP_1_aufgelöst wird:

```
serviceA.office.com -> CNAME: serviceA.domainA.com -> CNAME: serviceA.domainB.com -> A: IP_1
```

Diese CNAME-Umleitungen sind ein normaler Bestandteil des DNS und sind für den Clientcomputer transparent und für Proxy Server transparent. Sie werden für den Lastenausgleich, die Inhalts Bereitstellungs Netzwerke, die hohe Verfügbarkeit und die Minderung der Dienst Vorfälle verwendet. Microsoft veröffentlicht die zwischengeschalteten CNAME-Einträge nicht, Sie können jederzeit geändert werden, und Sie sollten Sie nicht wie in Ihrem Proxy Server zulässig konfigurieren.

Ein Proxy Server überprüft die anfängliche URL, die im obigen Beispiel serviceA.office.com ist und diese URL in Office 365 Publishing enthalten wäre. Der Proxy Server fordert die DNS-Auflösung dieser URL an eine IP-Adresse an und empfängt IP_1. Die zwischengeschalteten CNAME-Umleitungs Einträge werden nicht überprüft.

Hart codierte Konfigurationen oder whitelistings, die auf indirekten Office 365-FQDNs basieren, werden nicht empfohlen, werden von Microsoft nicht unterstützt und führen bekanntermaßen zu Kunden Verbindungsproblemen. DNS-Lösungen, die die CNAME-Umleitung blockieren oder anderweitig fälschlicherweise Office 365-DNS-Einträge auflösen, können mithilfe der DNS-bedingten Weiterleitung (auf direkt verwendete Office 365-FQDNs) mit aktivierter DNS-Rekursion gelöst werden. Viele Drittanbieter-Netzwerkumkreis Produkte integrieren die empfohlene Office 365-Endpunkt Whitelist in Ihre Konfiguration mithilfe des [office 365-IP-Adress-und URL](https://docs.microsoft.com/en-us/office365/enterprise/office-365-ip-web-service)-Webdiensts.

### <a name="why-do-i-see-names-such-as-nsatcnet-or-akadnsnet-in-the-microsoft-domain-names"></a>Warum werden Namen wie nsatc.net oder akadns.net in den Microsoft-Domänennamen angezeigt?
<a name="bkmk_akamai"> </a>

Office 365 und andere Microsoft-Dienste verwenden mehrere Drittanbieterdienste wie Akamai und MarkMonitor, um die Office 365-Umgebung zu verbessern. Damit Sie die bestmögliche Erfahrung erhalten, können wir diese Dienste in Zukunft ändern. Drittanbieter-Domänen können Inhalte wie ein CDN hosten, oder Sie können einen Dienst hosten, beispielsweise einen geografischen Datenverkehrs Verwaltungsdienst. Zu den derzeit verwendeten Diensten gehört Folgendes:
  
[markmonitor](https://www.markmonitor.com/) wird verwendet, wenn anforderungen angezeigt werden, die * \*. nsatc.net* . Dieser Dienst bietet Domänennamen Schutz und Überwachung zum Schutz vor böswilligem Verhalten.
  
[ExactTarget](https://www.marketingcloud.com/) wird verwendet, wenn anforderungen an * \*. exacttarget.com* angezeigt werden. Dieser Dienst bietet die Verwaltung von e-Mail-Links und die Überwachung von böswilligem Verhalten.
  
[Akamai](https://www.akamai.com/) wird verwendet, wenn Anforderungen angezeigt werden, die einen der folgenden FQDNs aufweisen. Dieser Dienst bietet geoDNS-und Inhalts Bereitstellungs-Netzwerkdienste.
  
```
*.akadns.net
*.akam.net
*.akamai.com
*.akamai.net
*.akamaiedge.net
*.akamaihd.net
*.akamaized.net
*.edgekey.net
*.edgesuite.net
```

### <a name="i-have-to-have-the-minimum-connectivity-possible-for-office-365"></a>Ich muss die minimale Konnektivität für Office 365
<a name="bkmk_thirdparty"> </a>

Office 365 ist eine Reihe von Diensten, die über das Internet funktionieren, die Zuverlässigkeits-und Verfügbarkeits Zusagen basieren auf vielen verfügbaren Standard-Internetdiensten. Beispielsweise müssen Standard-Internetdienste wie DNS, CRL und CDNs für die Verwendung von Office 365 zugänglich sein, ebenso wie Sie für die Verwendung der meisten modernen Internetdienste erreichbar sein müssen.

Die Office 365-Suite ist in die wichtigsten Dienstbereiche unterteilt. Diese können selektiv für Konnektivität aktiviert werden, und es gibt einen gemeinsamen Bereich, der eine Abhängigkeit für alle ist und immer erforderlich ist.

|**Service Bereich**|**Beschreibung**|
|:-----|:-----|
|**Exchange** <br/> |Exchange Online und Exchange Online Protection <br/> |
|**SharePoint** <br/> |SharePoint Online und OneDrive for Business <br/> |
|**Skype for Business Online und Microsoft Teams** <br/> |Skype for Business und Microsoft Teams <br/> |
|**Common** <br/> |Office 365 pro Plus, Office Online, Azure AD und andere gängige Netzwerkendpunkte <br/> |

Neben den grundlegenden Internetdiensten gibt es Dienste von Drittanbietern, die nur zum Integrieren von Funktionen verwendet werden. Während diese für die Integration erforderlich sind, werden Sie im Office 365-Endpunkte-Artikel als optional gekennzeichnet, was bedeutet, dass die Kernfunktionalität des Diensts weiterhin funktioniert, wenn auf den Endpunkt nicht zugegriffen werden kann. Jeder erforderliche Netzwerkendpunkt hat das erforderliche Attribut auf true festgelegt. Jeder Netzwerkendpunkt, der optional ist, hat das erforderliche Attribut auf false festgelegt, und das Attribut Notes enthält Details zur fehlenden Funktionalität, die Sie bei blockierter Konnektivität erwarten sollten.
  
Wenn Sie versuchen, Office 365 zu verwenden und keine Dienste von Drittanbietern zu finden sind, sollten Sie [sicherstellen, dass alle FQDNs, die in diesem Artikel als erforderlich oder optional gekennzeichnet sind, über den Proxy und die Firewall zulässig sind](urls-and-ip-address-ranges.md).
  
### <a name="how-do-i-block-access-to-microsofts-consumer-services"></a>Wie kann ich den Zugriff auf die Consumer-Dienste von Microsoft blockieren?
<a name="bkmk_consumer"> </a>

Das Einschränken des Zugriffs auf unsere Consumer-Services sollte auf Ihr eigenes Risiko erfolgen, die einzige zuverlässige Möglichkeit zum Blockieren von Consumer-Services besteht darin, den Zugriff auf den *Login.Live.com* -FQDN zu beschränken. Dieser FQDN wird von einer breiten Palette von Diensten einschließlich nicht-Consumer-Diensten wie MSDN, TechNet und anderen verwendet. Dieser FQDN wird auch vom Secure File Exchange-Programm von Microsoft Support verwendet und muss Dateien übertragen, um die Problembehandlung für Microsoft-Produkte zu erleichtern.  Das Einschränken des Zugriffs auf diesen FQDN kann dazu führen, dass auch Ausnahmen von der Regel für Netzwerkanforderungen mit diesen Diensten eingeschlossen werden müssen.
  
Denken Sie daran, dass das Blockieren des Zugriffs auf die Microsoft-Consumer-Dienste allein nicht verhindert, dass jemand in Ihrem Netzwerkinformationen mit einem Office 365-Mandanten oder einem anderen Dienst exfiltrieren.
  
## <a name="related-topics"></a>Verwandte Themen

[Office 365 – IP-Adress- und URL-Webdienst](office-365-ip-web-service.md)

[IP-Bereiche von Microsoft Azure-Rechenzentren](https://www.microsoft.com/download/details.aspx?id=41653)
  
[Öffentlicher Microsoft IP-Bereich](https://www.microsoft.com/download/details.aspx?id=53602)
  
[Anforderungen an die Netzwerkinfrastruktur für Microsoft InTune](https://docs.microsoft.com/intune/get-started/network-infrastructure-requirements-for-microsoft-intune)
  
[Express Route und Power BI](https://powerbi.microsoft.com/documentation/powerbi-admin-power-bi-expressroute/)
  
[URLs und IP-Adressbereiche von Office 365](urls-and-ip-address-ranges.md)
  
[Verwalten von ExpressRoute für Office 365-Verbindungen](managing-expressroute-for-connectivity.md)
  
[Prinzipien von Office 365-Netzwerkverbindungen](office-365-network-connectivity-principles.md)
