---
title: Verwalten von Office 365-Endpunkten
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 10/22/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Adm_O365_Setup
search.appverid: MOE150
ms.assetid: 99cab9d4-ef59-4207-9f2b-3728eb46bf9a
description: Einige Unternehmensnetzwerken Einschränken des Zugriffs auf generische Internetspeicherorte oder erhebliche Sonderinformationen oder Verarbeitung des Datenverkehrs im Netzwerk. So stellen Sie sicher, dass die Liste der Office 365-Endpunkten Computern Netzwerke wie diese Office 365 zugreifen können, Netzwerk- und Proxyeinstellungen Administratoren zum Verwalten der Liste der FQDNs, URLs müssen und IP-Adressen, bilden. Diese direkte Route, Proxy-Umgehung und/oder Firewall-Regeln und PAC-Dateien, um sicherzustellen, dass Netzwerk-Anfragen Office 365 zu erreichen sind hinzugefügt werden müssen.
ms.openlocfilehash: a240e3deea512dacd70b377b3d47a7b6f49a235c
ms.sourcegitcommit: 7f1e19fb2d7a448a2dec73d8b2b4b82f851fb5f7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2018
ms.locfileid: "25697971"
---
# <a name="managing-office-365-endpoints"></a>Verwalten von Office 365-Endpunkten

Die meisten Unternehmen, die mehreren Standorten und eine WAN-Verbindung aufweisen müssen müssen Konfiguration für Office 365-Netzwerkkonnektivität verfügen. Sie können Ihr Netzwerk optimieren, indem alle vertrauenswürdigen Netzwerk-Anforderungen für Office 365 direkt über die Firewall senden, und alle zusätzlichen Ebene Paketinspektion umgehen oder in Bearbeitung. Dadurch werden Wartezeit und Ihrer kapazitätsanforderungen Umkreisnetzwerk reduziert. Identifizieren von Office 365 Netzwerkdatenverkehr ist der erste Schritt bei der Bereitstellung eine optimale Leistung für Ihre Office 365-Benutzer. Weitere Informationen zu Office 365-Netzwerkkonnektivität finden Sie unter [Office 365 Network Connectivity Prinzipien](office-365-network-connectivity-principles.md)

Microsoft empfiehlt, dass Sie die Office 365-Netzwerk-Endpunkten und Änderungen, die Sie mit der [Office 365-IP-Adresse und URL-Webdienste](office-365-ip-web-service.md) zugreifen.

Unabhängig davon, wie Sie wichtige Netzwerkdatenverkehr für Office 365 verwalten ist Office 365 Internetkonnektivität erforderlich. Andere Netzwerkendpunkte, Konnektivität erforderlich ist, werden am [zusätzliche Endpunkte, die nicht in Office 365-IP-Adresse und URL-Webdienst enthalten](additional-office365-ip-addresses-and-urls.md) aufgeführt.

Verwendung von Office 365-Netzwerk-Endpunkten hängt Ihre Netzwerkarchitektur für Enterprise-Organisation ab. Dieser Artikel beschreibt verschiedene Möglichkeiten, die Enterprise-Netzwerk-Architekturen mit Office 365-IP-Adressen und URLs integrieren können. Die einfachste Möglichkeit zum auswählen, welche Netzwerk fordert als vertrauenswürdig ist die Verwendung SDWAN Geräte, die automatische Konfiguration von Office 365 an jedem den Bürostandorten zu unterstützen. 

## <a name="sdwan-for-local-branch-egress-of-vital-office-365-network-traffic"></a>SDWAN für lokale Branch Ausgang von wichtiger Netzwerkdatenverkehr für Office 365

Bei jeder Zweigstellenstandort können Sie ein SDWAN-Gerät konfiguriert ist für Route IP-Adressen für Office 365 optimieren Kategorie oder optimieren bereitstellen und Kategorien, direkt auf die Microsoft Netzwerk zulassen. Andere Netzwerkdatenverkehr einschließlich lokalen Datacenter Datenverkehr, generische Datenverkehr im Internet-Websites und Office 365 Default Kategorie Datenverkehr wird an einen anderen Speicherort gesendet, in denen Sie über eine grundlegendere Umkreisnetzwerk. 

Microsoft arbeitet mit SDWAN Anbietern, um die automatische Konfiguration zu ermöglichen. Sie erhalten weitere Informationen zum [Office 365 Networking Partner-Programm](office-365-networking-partner-program.md)

<a name="pacfiles"> </a>
## <a name="use-of-a-pac-file-for-direct-routing-of-vital-office-365-traffic"></a>Verwenden einer PAC-Datei zum direkten weiterleiten wichtiger Office 365-Datenverkehr

Verwenden Sie PAC oder WPAD-Dateien zum Verwalten von Netzwerk-Anfragen, die mit Office 365 zugeordnet sind, jedoch nicht über ein IP-Adresse verfügen. Typische Netzwerk-Anforderungen, die über ein Proxy oder zum Umkreisnetzwerk-Gerät gesendet werden, ein zusätzlichen Latenz entstehen. Während SSL unterbrechen und Inspect anfallen der größten Tax, können andere Dienste wie Proxy-Authentifizierung und Reputation Lookup benutzerfreundlich verursachen. Darüber hinaus benötigen diese Perimeter Network Geräte genügend Kapazität, um alle Anfragen Verbindung Netzwerk zu verarbeiten. Es wird empfohlen, die Proxy oder Prüfung Infrastruktur für die direkte Anforderungen von Office 365-Netzwerk zu umgehen.
  
[PowerShell Gallery Get-PacFile](https://www.powershellgallery.com/packages/Get-PacFile) ist ein Powershellskript, liest die neuesten Netzwerkendpunkte aus der Webdienste und erstellt eine Beispieldatei PAC. 

Nachdem Sie dieses Skript heruntergeladen haben, können Sie es zum Generieren einer PAC-Datei verwenden. Sie können auch das Skript ändern, damit es mit der Verwaltung Ihrer vorhandenen PAC-Datei integriert ist. 

![Herstellen einer Verbindung mit Office 365, durch Firewalls und Proxys. ](media/34d402f3-f502-42a0-8156-24a7c4273fa5.png) Abbildung 1: einfache Enterprise-Umkreisnetzwerk

Auf Computern unter Punkt (1) in Abbildung 1 wird die PAC-Datei bereitgestellt. Wenn Sie eine PAC-Datei für direkte Ausgang von wichtiger Netzwerkdatenverkehr für Office 365 verwenden, müssen Sie auch Konnektivität mit der IP-Adressen hinter dieser URLs auf Ihrer Firewall im Umkreisnetzwerk zu ermöglichen. Dies wird durch die IP-Adressen für die gleichen Office 365 Endpunkt Kategorien wie angegeben in der Datei PAC abruft und Erstellen von Firewall ACLs basierend auf diesen Adressen. Die Firewall wird gezeigt, wie in Abbildung 1 (3) zeigen. 

Getrennt, wenn Sie auswählen, nur direktes routing für die Route Netzwerkdatenverkehr für die optimieren Kategorie Endpunkte alle erforderlichen zulassen Kategorie Endpunkte, die an den Proxyserver gesendet müssen in der Proxyserver umgangen werden weitere Verarbeitung aufgeführt werden. Beispielsweise sind SSL Umbruch und Inspect und Proxy-Authentifizierung mit der optimieren und die zulassen Kategorie Endpunkten nicht kompatibel. Der Proxyserver wird gezeigt, wie in Abbildung 1 (2) zeigen.

Die gemeinsame Konfiguration werden alle ausgehenden Datenverkehr vom Proxyserver zulassen, dass Ziel-IP-Adressen für Office 365 Netzwerkdatenverkehr, die den Proxyserver erreicht ist nicht erforderlich. Informieren Sie sich über Probleme mit SSL unterbrechen und Inspect unter [Using Drittanbieter - Netzwerkgeräte oder Lösungen auf Office 365-Datenverkehr](https://support.microsoft.com/en-us/help/2690045/using-third-party-network-devices-or-solutions-with-office-365).

Es gibt zwei Arten von PAC-Dateien, die vom Get-PacFile Skript generiert wird.

|**Typ**|**Beschreibung**|
|:-----|:-----|
|**1** <br/> |Senden Sie die Endpunkt-Datenverkehr optimieren direkte und alle anderen an den Proxyserver. <br/> |
|**2** <br/> |Senden Sie optimieren und die lassen Sie direkte und alle anderen an den Proxyserver Endpunkt Datenverkehr zu. Kann auch zum Senden von, dass alle ExpressRoute für Office 365-Datenverkehr auf ExpressRoute Netzwerksegmente und alle anderen an den Proxyserver unterstützten verwendet werden. <br/> |

Hier ist ein einfaches Beispiel für den Aufruf des PowerShell-Skripts aus:

```
Get-PacFile -ClientRequestId b10c5ed1-bad1-445f-b386-b919946339a7
```

Es gibt eine Reihe von Parametern, die an das Skript übergeben werden können:

|**Parameter**|**Beschreibung**|
|:-----|:-----|
|**ClientRequestId** <br/> |Dies ist erforderlich und wird an den Webdienst, der dem Aufrufen den Clientcomputer stellt eine GUID übergeben <br/> |
|**Instance** <br/> |Die Office 365-Dienstinstanz die standardmäßig über Worldwide verfügt. Auch übergeben an den Webdienst. <br/> |
|**TenantName** <br/> |Name Ihrer Office 365-Mandanten. Übergeben an den Webdienst, und als ersetzbaren Parameter einige Office 365-URLs <br/> |
|**Type** <br/> |Der Typ der PAC-Proxydatei, die Sie erstellen möchten <br/> |

Hier ist ein weiteres Beispiel für den Aufruf des PowerShell-Skripts zusätzliche Parameter:

```
Get-PacFile -Type 2 -Instance Worldwide -TenantName Contoso -ClientRequestId b10c5ed1-bad1-445f-b386-b919946339a7 
```

## <a name="proxy-server-bypass-processing-of-office-365-network-traffic"></a>Proxyserver umgangen Verarbeitung des Netzwerkverkehrs für Office 365 

PAC-Dateien nicht für direkte ausgehenden Datenverkehr verwendet werden, sollten Sie weiterhin Verarbeitungsaufwand auf das Umkreisnetzwerk zu umgehen, indem Sie den Proxyserver konfigurieren. Manche Serverhersteller Proxy haben automatisierte Konfiguration dieses aktiviert, wie beschrieben in das [Office 365 Networking Partner-Programm](office-365-networking-partner-program.md). Wenn Sie dies manuell durchführen müssen Sie erhalten die optimieren und Endpunkt Kategorie Endpunktdaten von Office 365-IP-Adresse und URL-Webdienste zulassen, und konfigurieren den Proxyserver für die Umgehung Verarbeitung für diese. Es ist wichtig, zu vermeiden SSL unterbrechen und Inspect und Proxy-Authentifizierung für die optimieren und Kategorie Endpunkte zulassen. 
  
<a name="bkmk_changes"> </a>
## <a name="change-management-for-office-365-ip-addresses-and-urls"></a>Änderungsmanagement für Office 365-IP-Adressen und URLs

Zusätzlich zur Auswahl von entsprechenden Konfiguration für Umkreisnetzwerk, ist es wichtig, dass Sie eine Änderungsmanagementprozesses für Office 365-Endpunkten übernehmen. Diese Endpunkte regelmäßig ändern, und wenn die Änderungen nicht verwaltet werden mit Benutzern blockiert landen können oder mit einer schlechten Leistung nach einer neuen IP-Adresse oder URL wird hinzugefügt. 

Zum Ändern der Office 365-IP-Adressen und URLs werden in der Regel in der Nähe der letzte Tag des Monats veröffentlicht. In einigen Fällen wird eine Änderung außerhalb dieses Zeitplan aufgrund von betrieblichen, Support oder sicherheitsanforderungen veröffentlicht werden.

Wenn eine Änderung, die Sie ergreifen veröffentlicht wird, da eine IP-Adresse oder URL hinzugefügt wurde erforderlich sind, sollten Sie erwarten, um 30 Tage ab dem Zeitpunkt erhalten wir die Änderung veröffentlicht, bis live Office 365-Dienst auf diesem Endpunkt vorhanden ist. Obwohl Microsoft für diesen Benachrichtigungszeitraum Ziel ist es, es immer möglich aufgrund von betrieblichen, Support oder sicherheitsanforderungen möglicherweise nicht. Änderungen, die keine sofortige Aktion zum Aufrechterhalten der Konnektivität erfordern, wie IP-Adressen oder URLs entfernt oder weniger wurden keine bedeutenden Änderungen enthalten keine voraus. Unabhängig davon, welche Benachrichtigung bereitgestellt wird werden wir das erwartete Service aktive Datum für jede Änderung aufgelistet.

### <a name="change-notification-using-web-services"></a>Benachrichtigung über Webdienste

Sie können die Office 365-IP-Adresse verwenden und änderungsbenachrichtigung für URL-Webdienste zum Abrufen. Es wird empfohlen, dass Sie die Webmethode/Version einmal pro Stunde aufrufen, um die Version der Endpunkte zu prüfen, die Sie für die Verbindung zu Office 365 verwenden. Wenn diese Version beim Vergleich mit der Version, die Sie verwendet haben ändert, sollten Sie get-mit den neuesten Endpunktdaten aus der /endpoints Webmethode und optional rufen die Unterschiede aus der /changes-Webmethode. Es ist nicht erforderlich, die Webmethoden /endpoints oder /changes aufzurufen, wenn wurde, keine Änderungen auf die Version, die Sie gefunden. 

Weitere Informationen finden Sie unter [Office 365-IP-Adresse und URL-Webdienst](office-365-ip-web-service.md).

### <a name="change-notification-using-rss-feeds"></a>Verwenden von RSS-Feeds Benachrichtigung

Die Office 365-IP-Adresse und URL-Webdienste bieten einen RSS-feed, dass Sie in Outlook abonnieren können. Links zu den RSS-URLs auf jedem der Office 365-Dienst Instanz bestimmten Seiten für die IP-Adressen und URLs sind vorhanden. RSS-Feeds wird in [Office 365-IP-Adresse und URL-Webdienst](office-365-ip-web-service.md)näher beschrieben.

### <a name="change-notification-and-approval-review-using-microsoft-flow"></a>Benachrichtigung und Genehmigung Überprüfen von Microsoft Flow

Wir wissen, dass Sie weiterhin manuelle Verarbeitung für netzwerkänderungen Endpunkt erfordern möglicherweise, die über jeden Monat stammen. Microsoft Flow können Sie um einen Fluss zu erstellen, der Sie per e-Mail benachrichtigt und ein Genehmigungsprozesses, damit die Änderungen optional ausgeführt, wenn es sich bei Office 365-Netzwerk-Endpunkten geändert wurden. Nach der Überprüfung abgeschlossen ist, können Sie den automatisch die Änderungen an Ihrem Firewall- und Proxy-Server-Management-Team e-Mail-Fluss haben. 

Informieren Sie sich über die Microsoft-Flow Beispiel und die Vorlage unter [Verwendung der Microsoft Flow empfangen eine e-Mail, damit die Änderungen in Office 365-IP-Adressen und URLs](https://techcommunity.microsoft.com/t5/Office-365-Networking/Use-Microsoft-Flow-to-receive-an-email-for-changes-to-Office-365/td-p/240651)
  
<a name="FAQ"> </a>
## <a name="office-365-network-endpoints-faq"></a>Office 365 Netzwerkendpunkte – häufig gestellte Fragen

Administrator häufig gestellte Fragen zu Office 365-Diensten:
  
### <a name="how-do-i-submit-a-question"></a>Wie übermittle ich eine Frage?

Klicken Sie auf den Link unten, um anzugeben, ob der Artikel hilfreich war und übermitteln Sie weiteren Fragen zu. Wir das Feedback überwachen und mit der am häufigsten gestellten Fragen Hier aktualisieren.
  
### <a name="how-do-i-determine-the-location-of-my-tenant"></a>Ermitteln den Speicherort der meine Mandanten

 **Mandanten Speicherort** ist am besten mit unserem [Datacenter zuordnen](http://aka.ms/datamaps)bestimmt.
  
### <a name="am-i-peering-appropriately-with-microsoft"></a>Verwende ich entsprechend mit Microsoft peering?

 **Peering Speicherorte** werden in [peering mit Microsoft](https://www.microsoft.com/peering)ausführlicher beschrieben.
  
Mit über 2500 Internetdienstanbieter Peers Beziehungen sollte Global und 70 Points of Presence, aus dem Netzwerk für unsere erste nahtlos. Es kann nicht lohnt, sich ein paar Minuten und stellen Sie sicher, dass bei Ihrem Internetdienstanbieter Peers Beziehung ist die am besten geeignete [Nachfolgend finden Sie einige Beispiele für](https://blogs.technet.microsoft.com/onthewire/2017/03/22/__guidance/) des guten und nicht so gut Peers Hand und Nachteile auf Ihr Netzwerk. 
  
### <a name="i-see-network-requests-to-ip-addresses-not-on-the-published-list-do-i-need-to-provide-access-to-them"></a>Benötige ich Netzwerk Anforderungen an IP-Adressen nicht in der veröffentlichten Liste anzeigen, ich für den Zugriff auf diese?
<a name="bkmk_MissingIP"> </a>

Wir stellen nur IP-Adressen für die Office 365-Servern, denen Sie direkt an weiterleiten soll. Dies ist nicht für eine umfassende Liste aller IP-Adressen für die Netzwerk-Anfragen angezeigt werden. Netzwerk-Anforderungen an Microsoft und Drittanbieter-Besitzer, nicht aufgehoben, IP-Adressen, werden angezeigt. Diese IP-Adressen sind dynamisch generierte oder auf eine Weise, die kurzer Hinweis verhindert, dass bei einer Änderung verwaltet. Wenn die Firewall Access basierend auf die FQDNs für diese Netzwerk-Anfragen zulassen ist nicht möglich, verwenden Sie eine PAC oder WPAD-Datei, um die Anforderungen zu verwalten.
  
Sehen Sie, dass Office 365 eine IP-Adresse zugeordnet, die Sie auf Weitere Informationen wünschen?
  
1. Überprüfen Sie, ob die IP-Adresse in einem größeren veröffentlichte Bereich mit einem [CIDR-Rechner](http://jodies.de/ipcalc)mit enthalten ist.
2. Sehen Sie, wenn ein Partner die IP-Adresse mit einer [Whois-Abfrage](https://dnsquery.org/)besitzt. Wenn es sich um Microsoft gehören ist, kann es eine interne Partner sein.
3. Überprüfen Sie das Zertifikat, und in einem Browser eine Verbindung mit der IP-Adresse mit *HTTPS://\<IP-Adresse\> * , überprüfen Sie die Domänen aufgeführtes Dokument das Zertifikat zu verstehen, welche Domänen die IP-Adresse zugeordnet sind. Wenn sie eine Microsoft gehören IP-Adresse und nicht in der Liste der Office 365-IP-Adressen, wahrscheinlich die IP-Adresse ist ist ein Microsoft CDN wie *MSOCDN.NET* oder einer anderen Microsoft-Domäne ohne veröffentlichten IP-Informationen zugeordnet. Wenn Sie, dass die Domäne des Zertifikats eine ist, auf dem Forderung wir so Listen Sie die IP-Adresse finden, informieren Sie uns.

### <a name="why-do-i-see-names-such-as-nsatcnet-or-akadnsnet-in-the-microsoft-domain-names"></a>Warum werden Namen wie nsatc.net oder akadns.net in die Microsoft-Domänennamen angezeigt?
<a name="bkmk_akamai"> </a>

Office 365 und andere Microsoft-Dienste verwenden Sie mehrere Drittanbieter-Diensten wie etwa Akamai und MarkMonitor um Ihr Office 365 zu verbessern. Erteilen Sie die beste Erfahrung beibehalten, um möglich ist, diese Dienste in der Zukunft zu ändern. Auf diese Weise, veröffentlichen Sie häufig über den CNAME-Eintrag, die auf einer dritten Besitzer der Domäne, einen Datensatz oder IP-Adresse verweist. Drittanbieter-Domänen können Inhalte wie ein CDN hosten oder hosten sie möglicherweise einen Dienst wie eine geografische Datenverkehr-Verwaltungsdienst. Wenn Sie Verbindungen mit dritte angezeigt wird, sind sie in der Form eine Umleitung oder Weiterleitung, keine anfängliche Anforderung vom Client. Einige Kunden benötigen, um sicherzustellen, dass diese Art der Weiterleitung und Umleitung übergeben, ohne explizit hinzufügen, mit denen die lange Liste von potenziellen FQDNs Dienste von Drittanbietern möglicherweise zulässig ist.
  
Die Liste der Dienste unterliegt jederzeit ändern. Die Dienste derzeit unter anderem:
  
[MarkMonitor](https://www.markmonitor.com/) in Gebrauch Anfragen angezeigt, die enthalten * \*. nsatc.net* . Dieser Dienst bietet Domain Namensschutz und Überwachung zum Schutz vor böswilligen Verhalten.
  
[ExactTarget](https://www.marketingcloud.com/) in Gebrauch finden Sie unter Anforderungen an * \*. exacttarget.com* . Dieser Dienst bietet e-Mail-Link Management und Überwachung vor böswilligen Verhalten.
  
[Akamai](https://www.akamai.com/) wird verwendet, wenn Anforderungen angezeigt wird, die einen der folgenden FQDNs enthalten. Dieser Dienst bietet Geo-DNS und Content Delivery Network Services.
  
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

### <a name="i-have-to-have-the-minimum-connectivity-possible-for-office-365"></a>Ich habe die minimale mögliche-Konnektivität für Office 365 haben
<a name="bkmk_thirdparty"> </a>

Office 365 ist eine Suite-Funktion über das Internet integrierten Dienste, Zuverlässigkeit und Verfügbarkeit Versprechen basieren auf viele standard Internetdienste zur Verfügung stehen. Standardmäßige Internetdienste wie DNS, CRL und CDNs muss beispielsweise erreichbar zu Office 365 verwenden, wie sie mit den meisten modernen Internetdienste erreichbar sein müssen.

Die Office 365-Suite ist in Haupt-Servicebereiche unterteilt. Diese können selektiv für Verbindungen aktiviert werden, und es gibt ein gemeinsamen Bereich wird eine Abhängigkeit für alle und ist immer erforderlich.

|**Servicebereich**|**Beschreibung**|
|:-----|:-----|
|**Exchange** <br/> |Exchange Online und Exchange Online Protection <br/> |
|**SharePoint** <br/> |SharePoint Online und OneDrive for Business <br/> |
|**Skype** <br/> |Skype für Unternehmen und die Microsoft-Teams <br/> |
|**Allgemeine** <br/> |Office 365 Pro Plus, Office Online und auf Azure AD und andere allgemeine Netzwerkendpunkte <br/> |

Zusätzlich zu den grundlegenden Internetdienste sind Drittanbieter-Dienste, die nur verwendet werden, um Funktionalität zu integrieren. Während dies für die Integration erforderlich sind, sind sie in der Office 365-Endpunkten Artikel als optional markiert bedeutet, dass die Basisfunktionalität des Diensts weiterhin ausgeführt werden, wenn der Endpunkt nicht zugänglich ist. Jeder Endpunkt der erforderlich ist müssen die erforderlichen-Attribut True. Jeder Endpunkt optionale muss das required-Attribut auf False festgelegt, und Attributs Notizen geben Aufschluss fehlenden Funktionen, die Sie erwarten, wenn Connectivity ausgeschlossen wird.
  
Wenn Sie versuchen, Office 365 verwendet und tätiges, dass die Dienste von Drittanbietern nicht zugänglich sind sollten Sie um [sicherzustellen, dass alle FQDNs gekennzeichnet, erforderlich oder optional in diesem Artikel über die Proxy und Firewall zulässig sind](urls-and-ip-address-ranges.md).
  
### <a name="how-do-i-block-access-to-microsofts-consumer-services"></a>Wie blockieren Sie Zugriff auf Microsoft Consumer-Dienste
<a name="bkmk_consumer"> </a>

Einschränken des Zugriffs auf unsere Consumer-Dienste auf eigenes Risiko durchgeführt werden sollte, nur zuverlässiger Block Consumer Services zum Einschränken des Zugriffs auf die *login.live.com* FQDN. Dieser FQDN wird durch eine Breite Palette von Leistungspaket nicht Consumer-Diensten wie etwa MSDN und TechNet verwendet. Einschränken des Zugriffs auf diesen FQDN kann dazu führen, dass der Notwendigkeit Ausnahmen für die Regel zum Netzwerkanfragen mit diesen Diensten auch eingeschlossen werden sollen.
  
Beachten Sie, dass Blockieren des Zugriffs auf die Microsoft Consumer Services allein die Möglichkeit für eine Person in Ihrem Netzwerk zu Exfiltrate Informationen über Office 365-Mandanten oder anderen Dienst zu verhindern, dass werden nicht beibehalten.
  
## <a name="related-topics"></a>Verwandte Themen

[Office 365-IP-Adress- und -URL-Webdienst](office-365-ip-web-service.md)

[IP-Bereiche von Microsoft Azure-Rechenzentren](https://www.microsoft.com/download/details.aspx?id=41653)
  
[Öffentlicher Microsoft IP-Bereich](https://www.microsoft.com/download/details.aspx?id=53602)
  
[Anforderungen an die Netzwerkinfrastruktur für Microsoft Intune](https://docs.microsoft.com/intune/get-started/network-infrastructure-requirements-for-microsoft-intune)
  
[Power BI und ExpressRoute](https://powerbi.microsoft.com/documentation/powerbi-admin-power-bi-expressroute/)
  
[URLs und IP-Adressbereiche von Office 365](urls-and-ip-address-ranges.md)
  
[Verwalten von ExpressRoute für Office 365-Verbindungen](managing-expressroute-for-connectivity.md)
  
[Prinzipien von Office 365-Netzwerkverbindungen](office-365-network-connectivity-principles.md)
