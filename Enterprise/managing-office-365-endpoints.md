---
title: Verwalten von Office 365-Endpunkten
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 02/21/2019
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom: Adm_O365_Setup
search.appverid: MOE150
ms.assetid: 99cab9d4-ef59-4207-9f2b-3728eb46bf9a
description: Einige Unternehmensnetzwerke beschränken den Zugriff auf generische Internet Speicherorte oder umfassen eine erhebliche Backhaul oder Verarbeitung des Netzwerkdatenverkehrs. Um sicherzustellen, dass Computer in solchen Netzwerken auf Office 365 zugreifen können, müssen Netzwerk-und Proxy Administratoren die Liste der FQDNs, URLs und IP-Adressen verwalten, die die Liste der Office 365 Endpunkte bilden. Diese müssen zur direkten Route, Proxyumgehung und/oder Firewallregeln und PAC-Dateien hinzugefügt werden, um sicherzustellen, dass Netzwerkanforderungen Office 365 erreichen können.
ms.openlocfilehash: 21129387aeaf20f34e8528829dd942fddd381108
ms.sourcegitcommit: 1c97471f47e1869f6db684f280f9085b7c2ff59f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/18/2019
ms.locfileid: "35782475"
---
# <a name="managing-office-365-endpoints"></a>Verwalten von Office 365-Endpunkten

Die meisten Unternehmensorganisationen mit mehreren Office-Standorten und einem Verbindungs-WAN müssen für Office 365 Netzwerkkonnektivität konfiguriert werden. Sie können Ihr Netzwerk optimieren, indem Sie alle vertrauenswürdigen Office 365 Netzwerkanforderungen direkt über Ihre Firewall senden und alle zusätzlichen Überprüfungen oder Verarbeitungsschritte auf Paketebene umgehen. Dies reduziert die Wartezeit und ihre Perimeter-Kapazitätsanforderungen. Das identifizieren Office 365 Netzwerkdatenverkehrs ist der erste Schritt bei der Bereitstellung optimaler Leistung für Ihre Benutzer. Weitere Informationen zur Office 365 Netzwerkkonnektivität finden Sie unter [Office 365 Network Connectivity Principles](office-365-network-connectivity-principles.md).

Microsoft empfiehlt, dass Sie über den [Office 365 IP-Adresse und den URL-Webdienst](office-365-ip-web-service.md)auf die Office 365 Netzwerkendpunkte und deren Änderungen zugreifen.

Unabhängig davon, wie Sie wichtige Office 365 Netzwerkdatenverkehr verwalten, erfordert Office 365 eine Internet Verbindung. Andere Netzwerkendpunkte, auf denen die Konnektivität erforderlich ist, werden an zusätzlichen Endpunkten aufgeführt, [die nicht in der Office 365 IP-Adresse und im URL-Webdienst enthalten](additional-office365-ip-addresses-and-urls.md)sind.

Wie Sie die Office 365-Netzwerkendpunkte verwenden, hängt von der Netzwerkarchitektur ihrer Unternehmensorganisation ab. In diesem Artikel werden verschiedene Möglichkeiten beschrieben, wie Unternehmensnetzwerk Architekturen in Office 365-IP-Adressen und-URLs integriert werden können. Am einfachsten können Sie auswählen, welche Netzwerkanforderungen als vertrauenswürdig eingestuft werden sollen, indem Sie SDWAN-Geräte verwenden, die die automatische Office 365 Konfiguration an jedem Ihrer Office-Standorte unterstützen.

## <a name="sdwan-for-local-branch-egress-of-vital-office-365-network-traffic"></a>SDWAN für den Ausstieg aus der lokalen Zweigstelle wichtiger Office 365 Netzwerkdatenverkehr

An jedem Standort der Zweigstelle können Sie ein SDWAN-Gerät bereitstellen, das so konfiguriert ist, dass Datenverkehr für Office 365 Optimieren der Kategorie von Endpunkten oder zum Optimieren und zulassen von Kategorien direkt an das Microsoft-Netzwerk weitergeleitet wird. Anderer Netzwerkdatenverkehr einschließlich lokalem Datencenter Datenverkehr, allgemeiner Internet Websites-Datenverkehr und Datenverkehr zu Office 365 standardmäßigen Kategorie-Endpunkten wird an einen anderen Speicherort gesendet, an dem ein größerer Netzwerkperimeter vorliegt.

Microsoft arbeitet mit SDWAN-Anbietern zusammen, um eine automatisierte Konfiguration zu ermöglichen. Weitere Informationen finden Sie unter [Office 365 Networking Partner Program](office-365-networking-partner-program.md).

<a name="pacfiles"> </a>
## <a name="use-a-pac-file-for-direct-routing-of-vital-office-365-traffic"></a>Verwenden einer PAC-Datei für das direkte Routing von vitalem Office 365-Datenverkehr

Verwenden Sie PAC-oder WPAD-Dateien zum Verwalten von Netzwerkanforderungen, die Office 365 zugeordnet sind, aber keine IP-Adresse haben. Typische Netzwerkanforderungen, die über einen Proxy oder ein Umkreis Gerät gesendet werden, verlängern die Wartezeit. Während SSL-Unterbrechung und-Prüfung die größte Wartezeit verursacht, können andere Dienste wie Proxyauthentifizierung und Reputations Suche eine schlechte Leistung und eine schlechte Benutzerfreundlichkeit verursachen. Darüber hinaus benötigen diese Umkreisnetzwerk Geräte genügend Kapazität, um alle Netzwerkverbindungsanforderungen zu verarbeiten. Es wird empfohlen, die Proxy-oder Inspektionsgeräte für direkte Office 365 Netzwerkanforderungen zu umgehen.
  
[PowerShell Gallery Get-PacFile](https://www.powershellgallery.com/packages/Get-PacFile) ist ein PowerShell-Skript, das die neuesten Netzwerkendpunkte aus dem Office 365 IP-Adresse und URL-Webdienst liest und eine PAC-Beispieldatei erstellt. Sie können das Skript so ändern, dass es in Ihre vorhandene PAC-Dateiverwaltung integriert wird.

![Herstellen einer Verbindung mit Office 365 über Firewalls und Proxys.](media/34d402f3-f502-42a0-8156-24a7c4273fa5.png)

**Abbildung 1: Umkreis des einfachen Unternehmensnetzwerks**

Die PAC-Datei wird in Webbrowsern an der ersten Position in Abbildung 1 bereitgestellt. Wenn Sie eine PAC-Datei für den direkten Ausstieg des wichtigen Office 365 Netzwerkdatenverkehrs verwenden, müssen Sie auch die Konnektivität zu den IP-Adressen hinter diesen URLs in ihrer Netzwerkumkreis Firewall zulassen. Hierzu werden die IP-Adressen für dieselben Office 365 Endpunkt Kategorien abgerufen, die in der PAC-Datei angegeben sind, und es werden Firewall-ACLs basierend auf diesen Adressen erstellt. Die Firewall befindet sich in Abbildung 1 in Ziffer 3.

Separat Wenn Sie nur das direkte Routing für die Endpunkte der Kategorie optimieren auswählen, müssen alle erforderlichen Endpunkte der zulässigen Kategorien, die Sie an den Proxy Server senden, auf dem Proxy Server aufgeführt werden, um die weitere Verarbeitung zu umgehen. Beispielsweise sind SSL-Unterbrechung und-Überprüfung und Proxy Authentifizierung nicht mit den Endpunkten für die Kategorie optimieren und zulassen kompatibel. Der Proxy Server ist in Abbildung 1 in Ziffer 2 dargestellt.

Die allgemeine Konfiguration besteht darin, den gesamten ausgehenden Datenverkehr vom Proxy Server für die Ziel-IP-Adressen für Office 365 Netzwerkdatenverkehr, der auf den Proxy Server trifft, ohne Verarbeitung zu ermöglichen. Informationen zu Problemen mit SSL-Unterbrechung und-Prüfung finden Sie unter [using Drittanbieter-Netzwerkgeräte oder Lösungen für Office 365 Datenverkehr](https://support.microsoft.com/en-us/help/2690045/using-third-party-network-devices-or-solutions-with-office-365).

Es gibt zwei Arten von PAC-Dateien, die vom Get-PacFile-Skript generiert werden.

|**Typ**|**Beschreibung**|
|:-----|:-----|
|**1** <br/> |Senden Optimieren des Endpunkt Datenverkehrs direkt und alles andere an den Proxy Server. <br/> |
|**2** <br/> |Senden Sie Optimize, und lassen Sie den Endpunkt Datenverkehr direkt und alles andere an den Proxy Server weiter. Dieser Typ kann auch verwendet werden, um alle unterstützten Express Route für Office 365 Datenverkehr an Express Route-Netzwerksegmente und alles andere an den Proxy Server zu senden. <br/> |

Im folgenden finden Sie ein einfaches Beispiel für das Aufrufen des PowerShell-Skripts:

```powershell
Get-PacFile -ClientRequestId b10c5ed1-bad1-445f-b386-b919946339a7
```

Es gibt eine Reihe von Parametern, die Sie an das Skript übergeben können:

|**Parameter**|**Beschreibung**|
|:-----|:-----|
|**ClientRequestId** <br/> |Dies ist erforderlich, und es ist eine GUID, die an den Webdienst übergeben wird, der den Clientcomputer darstellt, der den Anruf tätigt. <br/> |
|**Instanz** <br/> |Die Office 365-Dienstinstanz, die standardmäßig weltweit verwendet wird. Wird auch an den Webdienst übergeben. <br/> |
|**TenantName** <br/> |Ihr Office 365 Mandantenname. An den Webdienst übergeben und in einigen Office 365-URLs als austauschbarer Parameter verwendet. <br/> |
|**Type** <br/> |Der Typ der Proxy-PAC-Datei, die Sie generieren möchten. <br/> |

Hier ist ein weiteres Beispiel für das Aufrufen des PowerShell-Skripts mit zusätzlichen Parametern:

```powershell
Get-PacFile -Type 2 -Instance Worldwide -TenantName Contoso -ClientRequestId b10c5ed1-bad1-445f-b386-b919946339a7
```

## <a name="proxy-server-bypass-processing-of-office-365-network-traffic"></a>Proxy Server-Umgehungs Verarbeitung von Office 365 Netzwerkdatenverkehr

Da PAC-Dateien nicht für den direkten ausgehenden Datenverkehr verwendet werden, möchten Sie die Verarbeitung in Ihrem Netzwerkperimeter dennoch umgehen, indem Sie den Proxy Server konfigurieren. Einige Proxy Serverhersteller haben die automatische Konfiguration dieser Funktion wie im Office 365- [Netzwerk Partner Programm](office-365-networking-partner-program.md)beschrieben aktiviert.

Wenn Sie dies manuell durchführen, müssen Sie die Daten zum Optimieren und zulassen von Endpunkt Kategorien aus dem Office 365 IP-Adresse und URL-Webdienst abrufen und den Proxy Server so konfigurieren, dass die Verarbeitung für diese umgangen wird. Es ist wichtig, SSL-unterbrechungs-und-Überprüfung und Proxy Authentifizierung für die Kategorie Endpunkte optimieren und zulassen zu vermeiden.
  
<a name="bkmk_changes"> </a>
## <a name="change-management-for-office-365-ip-addresses-and-urls"></a>Änderungsverwaltung für Office 365-IP-Adressen und-URLs

Neben der Auswahl der geeigneten Konfiguration für Ihren Netzwerkperimeter ist es wichtig, dass Sie einen Änderungsverwaltungsprozess für Office 365 Endpunkte einführen. Diese Endpunkte ändern sich regelmäßig, und wenn Sie die Änderungen nicht verwalten, können Sie nach dem Hinzufügen einer neuen IP-Adresse oder-URL bei Benutzern mit blockierter oder schlechter Leistung beenden.

Änderungen an den Office 365-IP-Adressen und-URLs werden normalerweise am letzten Tag eines jeden Monats veröffentlicht. Manchmal wird eine Änderung außerhalb dieses Zeitplans aufgrund von Betriebs-, Support-oder Sicherheitsanforderungen veröffentlicht.

Wenn eine Änderung veröffentlicht wird, die erfordert, dass Sie handeln, da eine IP-Adresse oder URL hinzugefügt wurde, sollten Sie davon ausgehen, dass Sie von dem Zeitpunkt, an dem die Änderung veröffentlicht wurde, eine 30-tägige Benachrichtigung erhalten, bis ein Office 365 Dienst auf diesem Endpunkt vorhanden ist. Obwohl wir auf diesen Benachrichtigungszeitraum abzielen, ist dies möglicherweise aufgrund von Betriebs-, Support-oder Sicherheitsanforderungen nicht immer möglich. Änderungen, die keine sofortige Aktion zum aufrecht erhalten der Konnektivität erfordern, beispielsweise entfernte IP-Adressen oder URLs oder weniger wichtige Änderungen, enthalten keine voraus Benachrichtigung. Unabhängig davon, welche Benachrichtigung angegeben wird, wird für jede Änderung der erwartete Dienst aktive Termin aufgelistet.

### <a name="change-notification-using-the-web-service"></a>Ändern der Benachrichtigung mithilfe des Webdiensts

Sie können die Office 365-IP-Adresse und den URL-Webdienst verwenden, um Änderungsbenachrichtigungen zu erhalten. Es wird empfohlen, die **/Version** -Webmethode einmal pro Stunde aufzurufen, um die Version der Endpunkte zu überprüfen, die Sie zum Herstellen einer Verbindung mit Office 365 verwenden. Wenn sich diese Version im Vergleich zur verwendeten Version ändert, sollten Sie die neuesten Endpunkt Daten von der **/Endpoints** -Webmethode abrufen und optional die Unterschiede von der **/Changes** -Webmethode abrufen. Es ist nicht erforderlich, die **/Endpoints** -oder **/Changes** -Webmethoden aufzurufen, wenn die von Ihnen gefundene Version nicht geändert wurde.

Weitere Informationen finden Sie unter [Office 365 IP-Adresse und URL-Webdienst](office-365-ip-web-service.md).

### <a name="change-notification-using-rss-feeds"></a>Ändern der Benachrichtigung mit RSS-Feeds

Der Office 365 IP-Adresse und der URL-Webdienst stellt einen RSS-Feed bereit, den Sie in Outlook abonnieren können. Es gibt Links zu den RSS-URLs auf den einzelnen Office 365-Dienstinstanzen spezifischen Seiten für die IP-Adressen und URLs. Weitere Informationen finden Sie unter [Office 365 IP-Adresse und URL-Webdienst](office-365-ip-web-service.md).

### <a name="change-notification-and-approval-review-using-microsoft-flow"></a>Änderungsbenachrichtigung und Genehmigungs Überprüfung mit Microsoft Flow

Wir sind uns bewusst, dass Sie möglicherweise weiterhin eine manuelle Verarbeitung für Änderungen an Netzwerkendpunkten benötigen, die jeden Monat durchlaufen. Sie können Microsoft Flow verwenden, um einen Fluss zu erstellen, der Sie per e-Mail benachrichtigt und optional einen Genehmigungsprozess für Änderungen ausführt, wenn Office 365 Netzwerkendpunkte Änderungen aufweisen. Sobald die Überprüfung abgeschlossen ist, können Sie den Flow automatisch per e-Mail an Ihre Firewall und Ihr Proxy Server-Verwaltungsteam senden.

Informationen zu einem Microsoft Flow-Beispiel und einer Vorlage finden Sie unter [Verwenden von Microsoft Flow zum Empfangen einer e-Mail-Nachricht für Änderungen an Office 365-IP-Adressen und-URLs](https://techcommunity.microsoft.com/t5/Office-365-Networking/Use-Microsoft-Flow-to-receive-an-email-for-changes-to-Office-365/td-p/240651).
  
<a name="FAQ"> </a>
## <a name="office-365-network-endpoints-faq"></a>FAQ zu Office 365 Netzwerkendpunkte

Häufig gestellte Administrator Fragen zu Office 365 Konnektivität:
  
### <a name="how-do-i-submit-a-question"></a>Wie kann ich eine Frage übermitteln?

Klicken Sie auf den Link unten, um anzugeben, ob der Artikel hilfreich ist oder nicht, und übermitteln Sie weitere Fragen. Wir überwachen das Feedback und aktualisieren die Fragen hier mit den am häufigsten gestellten Fragen.
  
### <a name="how-do-i-determine-the-location-of-my-tenant"></a>Wie kann ich den Standort meines Mandanten ermitteln?

 Der **Mandanten Standort** wird am besten mithilfe unserer [Datencenter-Zuordnung](http://aka.ms/datamaps)ermittelt.
  
### <a name="am-i-peering-appropriately-with-microsoft"></a>Bin ich mit Microsoft Peering angemessen?

 **Peering-Speicherorte** werden in [Peering mit Microsoft](https://www.microsoft.com/peering)ausführlicher beschrieben.
  
Mit mehr als 2500 ISP-Peering-Beziehungen Global und 70 Points of Presence sollte es nahtlos von Ihrem Netzwerk zur unsrigen kommen. Es kann nicht Schaden, ein paar Minuten zu verbringen, um sicherzustellen, dass die Peering-Beziehung Ihres ISP am besten geeignet ist, [hier ein paar Beispiele](https://blogs.technet.microsoft.com/onthewire/2017/03/22/__guidance/) für gute und nicht so gute Peering-Hand-offs in unserem Netzwerk.
  
### <a name="i-see-network-requests-to-ip-addresses-not-on-the-published-list-do-i-need-to-provide-access-to-them"></a>Werden Netzwerkanforderungen an IP-Adressen nicht in der veröffentlichten Liste angezeigt, muss ich Ihnen Zugriff gewähren?
<a name="bkmk_MissingIP"> </a>

Wir stellen nur IP-Adressen für die Office 365 Server bereit, an die Sie direkt weitergeleitet werden sollen. Es handelt sich nicht um eine umfassende Liste aller IP-Adressen, für die Netzwerkanforderungen angezeigt werden. Sie sehen Netzwerkanforderungen an Microsoft und Drittanbieter, unveröffentlichte IP-Adressen. Diese IP-Adressen werden dynamisch generiert oder so verwaltet, dass eine rechtzeitige Benachrichtigung beim Ändern verhindert wird. Wenn Ihre Firewall keinen Zugriff basierend auf den FQDNs für diese Netzwerkanforderungen zulässt, verwenden Sie eine PAC-oder WPAD-Datei, um die Anforderungen zu verwalten.
  
Sehen Sie sich eine IP-Adresse für Office 365 an, auf die Sie weitere Informationen erhalten möchten.
  
1. Überprüfen Sie, ob die IP-Adresse in einem größeren veröffentlichten Bereich mithilfe eines [CIDR](http://jodies.de/ipcalc)-Rechners enthalten ist.
2. Prüfen Sie, ob ein Partner die IP mit einer [Whois-Abfrage](https://dnsquery.org/)besitzt. Wenn Microsoft im Besitz ist, kann es sich um einen internen Partner handeln.
3. Überprüfen Sie das Zertifikat, stellen Sie in einem Browser eine Verbindung mit der IP-Adresse mithilfe von *https://\<ip_address\> * her, überprüfen Sie die im Zertifikat aufgeführten Domänen, um zu verstehen, welche Domänen der IP-Adresse zugeordnet sind. Wenn es sich um eine Microsoft-eigene IP-Adresse handelt und nicht in der Liste der Office 365-IP-Adressen, ist es wahrscheinlich, dass die IP-Adresse einem Microsoft-CDN wie *MSOCDN.net* oder einer anderen Microsoft-Domäne ohne veröffentlichte IP-Informationen zugeordnet ist. Wenn Sie feststellen, dass die Domäne auf dem Zertifikat eine ist, in der wir die IP-Adresse auflisten möchten, teilen Sie uns dies bitte mit.

<a name="bkmk_cname"> </a>
### <a name="some-office-365-urls-point-to-cname-records-instead-of-a-records-in-the-dns-what-do-i-have-to-do-with-the-cname-records"></a>Einige Office 365 URLs deuten auf CNAME-Einträge anstelle von Datensätzen im DNS hin. Was benötige ich mit den CNAME-Einträgen?

Client Computer benötigen einen DNS-a-oder AAAA-Eintrag, der eine oder mehrere IP-Adressen enthält, um eine Verbindung mit einem clouddienst herzustellen. Einige in Office 365 enthaltene URLs zeigen CNAME-Einträge anstelle von A-oder AAAA-Einträgen an. Diese CNAME-Einträge sind Vermittler und es gibt möglicherweise mehrere in einer Kette. Sie werden immer schließlich in einen A-oder AAAA-Eintrag für eine IP-Adresse aufgelöst. Berücksichtigen Sie beispielsweise die folgende Reihe von DNS-Einträgen, die schließlich in die IP-Adresse _IP_1_aufgelöst wird:

```
serviceA.office.com -> CNAME: serviceA.domainA.com -> CNAME: serviceA.domainB.com -> A: IP_1
```

Diese CNAME-Umleitungen stellen einen normalen Bestandteil des DNS dar und sind für den Clientcomputer transparent und für Proxy Server transparent. Sie werden für Lastenausgleich, Inhalts Übermittlungs Netzwerke, hohe Verfügbarkeit und Minderung von Dienst Schadensfällen verwendet. Microsoft veröffentlicht die zwischengeschalteten CNAME-Einträge nicht, Sie können jederzeit geändert werden, und Sie sollten Sie nicht wie in Ihrem Proxy Server zulässig konfigurieren müssen.

Ein Proxy Server überprüft die anfängliche URL, die im obigen Beispiel ServiceA.Office.com ist, und diese URL würde in Office 365 Veröffentlichung enthalten sein. Der Proxy Server fordert die DNS-Auflösung dieser URL an eine IP-Adresse an und erhält eine IP_1 zurück. Die zwischengeschalteten CNAME-Umleitungs Datensätze werden nicht überprüft.

Fest codierte Konfigurationen oder Whitelists basierend auf indirekten Office 365 FQDNs wird nicht empfohlen, wird von Microsoft nicht unterstützt und ist bekannt, dass es zu Problemen mit der Kunden Konnektivität kommt. DNS-Lösungen, die die CNAME-Umleitung blockieren oder die Office 365 DNS-Einträgen andernfalls fälschlicherweise aufgelöst werden, können über die DNS-bedingte Weiterleitung (Bereich für direkt verwendete Office 365 FQDNs) mit aktivierter DNS-Rekursion gelöst werden. Viele Netzwerk perimeterprodukte von Drittanbietern integrieren die empfohlene Office 365-Endpunkt-Whitelist in Ihrer Konfiguration mithilfe der [Office 365 IP-Adresse und des URL-](https://docs.microsoft.com/en-us/office365/enterprise/office-365-ip-web-service)Webdiensts nativ.

### <a name="why-do-i-see-names-such-as-nsatcnet-or-akadnsnet-in-the-microsoft-domain-names"></a>Warum werden Namen wie nsatc.net oder akadns.net in den Microsoft-Domänennamen angezeigt?
<a name="bkmk_akamai"> </a>

Office 365 und andere Microsoft-Dienste verwenden mehrere Drittanbieterdienste wie Akamai und MarkMonitor, um Ihre Office 365 Erfahrung zu verbessern. Damit Sie weiterhin die bestmögliche Funktionalität erhalten, können wir diese Dienste in Zukunft ändern. Drittanbieter Domänen können Inhalte hosten, beispielsweise ein CDN, oder Sie können einen Dienst hosten, beispielsweise einen geografischen Dienst für die Datenverkehrsverwaltung. Einige der derzeit verwendeten Dienste umfassen Folgendes:
  
[MarkMonitor](https://www.markmonitor.com/) wird verwendet, wenn Anforderungen angezeigt werden, die * \*. nsatc.net* enthalten. Dieser Dienst bietet Domänennamen Schutz und Überwachung zum Schutz vor bösartigem Verhalten.
  
[ExactTarget](https://www.marketingcloud.com/) wird verwendet, wenn Anforderungen an * \*. ExactTarget.com* angezeigt werden. Dieser Dienst bietet e-Mail-Linkverwaltung und Überwachung gegen böswilliges Verhalten.
  
[Akamai](https://www.akamai.com/) wird verwendet, wenn Anforderungen angezeigt werden, die einen der folgenden FQDNs enthalten. Dieser Dienst bietet Netzwerkdienste für Geo-DNS-und Inhalts Zustellungen an.
  
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

### <a name="i-have-to-have-the-minimum-connectivity-possible-for-office-365"></a>Ich habe die minimale Konnektivität für Office 365 möglich
<a name="bkmk_thirdparty"> </a>

Da Office 365 eine Suite von Diensten ist, die über das Internet funktionieren, basieren die Zuverlässigkeits-und Verfügbarkeits Zusagen auf vielen Standard-Internetdiensten, die verfügbar sind. Standard Internetdienste wie DNS, CRL und CDNs müssen beispielsweise für die Verwendung von Office 365 erreichbar sein, damit Sie für die Verwendung der meisten modernen Internetdienste erreichbar sind.

Die Office 365 Suite ist in wichtige Servicebereiche unterteilt. Diese können für die Konnektivität selektiv aktiviert werden, und es gibt einen gemeinsamen Bereich, der eine Abhängigkeit für alle ist und immer erforderlich ist.

|**Dienstbereich**|**Beschreibung**|
|:-----|:-----|
|**Exchange** <br/> |Exchange Online-und Exchange Online Schutz <br/> |
|**SharePoint** <br/> |SharePoint Online und OneDrive for Business <br/> |
|**Skype for Business Online und Microsoft Teams** <br/> |Skype for Business und Microsoft Teams <br/> |
|**Standard** <br/> |Office 365 pro Plus, Office in einem Browser, Azure AD und andere gängige Netzwerkendpunkte <br/> |

Zusätzlich zu den grundlegenden Internetdiensten gibt es Dienste von Drittanbietern, die nur zur Integration von Funktionen verwendet werden. Diese sind zwar für die Integration erforderlich, aber Sie sind im Artikel Office 365 Endpunkte als optional gekennzeichnet, was bedeutet, dass die Kernfunktionalität des Diensts weiterhin funktionsfähig ist, wenn auf den Endpunkt nicht zugegriffen werden kann. Für jeden erforderlichen Netzwerkendpunkt wird das erforderliche Attribut auf true festgelegt. Bei jedem optionalen Netzwerkendpunkt wird das erforderliche Attribut auf "false" festgelegt, und das Attribut "Notes" enthält Informationen zu den fehlenden Funktionen, die Sie bei Blockierung der Konnektivität erwarten sollten.
  
Wenn Sie versuchen, Office 365 zu verwenden und Drittanbieterdienste nicht zugänglich sind, sollten Sie [sicherstellen, dass alle FQDNs, die in diesem Artikel erforderlich oder optional gekennzeichnet sind, über den Proxy und die Firewall zulässig sind](urls-and-ip-address-ranges.md).
  
### <a name="how-do-i-block-access-to-microsofts-consumer-services"></a>Wie kann ich den Zugriff auf Microsofts Consumer Services blockieren?
<a name="bkmk_consumer"> </a>

Das Einschränken des Zugriffs auf unsere Consumer-Dienste sollte auf eigenes Risiko erfolgen. Die einzige zuverlässige Möglichkeit zum Blockieren von Consumer-Diensten besteht darin, den Zugriff auf den *Login.Live.com* -FQDN einzuschränken. Dieser FQDN wird von einer breiten Palette von Diensten verwendet, einschließlich nicht-Consumer-Dienste wie MSDN, TechNet und anderen. Dieser FQDN wird auch vom Secure File Exchange-Programm von Microsoft Support verwendet und ist für die Übertragung von Dateien zur Erleichterung der Problembehandlung für Microsoft-Produkte erforderlich.  Das Einschränken des Zugriffs auf diesen FQDN kann dazu führen, dass auch Ausnahmen zur Regel für Netzwerkanforderungen hinzugefügt werden, die diesen Diensten zugeordnet sind.
  
Beachten Sie, dass durch das Blockieren des Zugriffs auf die Microsoft-Consumerdienst allein nicht verhindert werden kann, dass Personen in Ihrem Netzwerkinformationen über einen Office 365 Mandanten oder einen anderen Dienst exfiltrieren.
  
## <a name="related-topics"></a>Verwandte Themen

[Office 365 – IP-Adress- und URL-Webdienst](office-365-ip-web-service.md)

[IP-Bereiche von Microsoft Azure-Rechenzentren](https://www.microsoft.com/download/details.aspx?id=41653)
  
[Öffentlicher Microsoft IP-Bereich](https://www.microsoft.com/download/details.aspx?id=53602)
  
[Anforderungen an die Netzwerkinfrastruktur für Microsoft InTune](https://docs.microsoft.com/intune/get-started/network-infrastructure-requirements-for-microsoft-intune)
  
[Express Route und Power BI](https://powerbi.microsoft.com/documentation/powerbi-admin-power-bi-expressroute/)
  
[URLs und IP-Adressbereiche für Office 365](urls-and-ip-address-ranges.md)
  
[Verwalten von ExpressRoute für Office 365-Verbindungen](managing-expressroute-for-connectivity.md)
  
[Prinzipien von Office 365-Netzwerkverbindungen](office-365-network-connectivity-principles.md)
