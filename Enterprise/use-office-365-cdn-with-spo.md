---
title: Verwenden des Office 365 Content Delivery Network (CDN) mit SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 4/3/2019
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- SPO160
ms.assetid: bebb285f-1d54-4f79-90a5-94985afc6af8
description: Beschreibt, wie das Office 365 Content Delivery Network (CDN) verwendet wird, um die Bereitstellen Ihrer SharePoint Online-Objekte für alle Ihre Benutzer zu beschleunigen, unabhängig davon, wo Sie sich befinden oder wie Sie auf Ihre Inhalte zugreifen.
ms.openlocfilehash: ceb66b3e17baf25a292b4903c569b931f9448f71
ms.sourcegitcommit: 100ae697304427dab5ad494a06323656b498c57e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/03/2019
ms.locfileid: "31396923"
---
# <a name="use-the-office-365-content-delivery-network-cdn-with-sharepoint-online"></a>Verwenden des Office 365 Content Delivery Network (CDN) mit SharePoint Online

Sie können statische Objekte im Office 365-Netzwerk für die Inhaltsübermittlung (CDN) hosten, um eine bessere Leistung für Ihre SharePoint Online-Seiten zu ermöglichen. Das Office 365-Netzwerk für die Inhaltsübermittlung verbessert die Leistung, indem statische Objekte näher an den Browsern zwischengespeichert werden, die diese anfordern, wodurch Downloads beschleunigt werden und die Latenz reduziert wird. Außerdem verwendet das Office 365 CDN das [http/2-Protokoll](https://en.wikipedia.org/wiki/HTTP/2) für eine verbesserte KOMPRIMIERUNG und HTTP-Pipelining. Das Office 365-Netzwerk für die Inhaltsübermittlung ist in Ihrem SharePoint Online-Abonnement enthalten.

Das Office 365-Netzwerk für die Inhaltsübermittlung besteht aus mehreren CDNs, über die Sie statische Objekte an mehreren Speicherorten hosten können, oder aus _Ursprüngen_, die aus globalen Hochgeschwindigkeitsnetzwerken bedient werden. In Abhängigkeit von der Art der Inhalte, die Sie im Office 365-Netzwerk für die Inhaltsübermittlung hosten möchten, können Sie **öffentliche** Ursprünge, **private** Ursprünge oder beides hinzufügen. Weitere Informationen zum Unterschied zwischen öffentlichen und privaten Ursprüngen finden Sie unter [Wählen Sie, ob jeder Ursprung öffentlich oder privat sein soll](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate) .

![Office 365 CDN-konzeptionelles Diagramm] (media/O365-CDN/o365-cdn-flow-transparent.svg "Office 365 CDN-konzeptionelles Diagramm")

Wenn Sie bereits mit der Funktionsweise von CDNs vertraut sind, müssen Sie nur einige Schritte ausführen, um das Office 365 CDN für Ihren Mandanten zu aktivieren. In diesem Thema wird beschrieben, wie. Lesen Sie weiter, um zu erfahren, wie Sie mit dem Hosten Ihrer statischen Objekte beginnen.

> [!TIP]
> Es gibt weitere von Microsoft gehostete CDNs, die mit Office 365 für spezielle Verwendungsszenarien verwendet werden können, aber nicht in diesem Thema behandelt werden, da Sie nicht in den Bereich des Office 365 CDN fallen. Weitere Informationen finden Sie unter [andere Microsoft-CDNs](content-delivery-networks.md#other-microsoft-cdns).

 **Gehen Sie zurück zur [Netzwerkplanung und Leistungsoptimierung für Office 365](https://aka.ms/tune).**

## <a name="overview-of-working-with-the-office-365-cdn-in-sharepoint-online"></a>Übersicht über das Arbeiten mit dem Office 365 CDN in SharePoint Online

Führen Sie die folgenden grundlegenden Schritte aus, um das Office 365 CDN für Ihre Organisation einzurichten:

- [Planen der Bereitstellung von Office 365 CDN](use-office-365-cdn-with-spo.md#plan-for-deployment-of-the-office-365-cdn)

  - [Legen Sie fest, welche statischen Objekte im CDN gehostet werden sollen](use-office-365-cdn-with-spo.md#CDNAssets).
  - [Bestimmen Sie, wo Ihre Objekte gespeichert werden sollen](use-office-365-cdn-with-spo.md#CDNStoreAssets). Dieser Speicherort kann eine SharePoint-Website,-Bibliothek oder-Ordner sein und als _Ursprung_bezeichnet werden.
  - [Wählen Sie aus, ob jeder Ursprung öffentlich oder privat sein soll](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate). Sie können mehrere Ursprünge sowohl öffentlicher als auch privater Typen hinzufügen.

- Einrichten und Konfigurieren des CDN, entweder mit PowerShell oder mit der SharePoint Online-CLI

  - [Einrichten und Konfigurieren des CDN mithilfe der SharePoint Online-Verwaltungsshell](use-office-365-cdn-with-spo.md#CDNSetupinPShell)
  - [Einrichten und Konfigurieren des CDN mithilfe der Office 365 CLI](use-office-365-cdn-with-spo.md#CDNSetupinCLI)

  Wenn Sie diesen Schritt abgeschlossen haben, haben Sie folgende Möglichkeiten:

  - CDN für Ihre Organisation aktiviert.
  - Ihre Ursprünge wurden HinzugeFügt, wobei jeder Ursprung als öffentlich oder privat identifiziert wurde.

Nachdem Sie das Setup abgeschlossen haben, können Sie [das Office 365 CDN](use-office-365-cdn-with-spo.md#CDNManage) im Laufe der Zeit verwalten:
  
- Hinzufügen, aktualisieren und Entfernen von Objekten
- Hinzufügen und Entfernen von Ursprüngen
- Konfigurieren von CDN-Richtlinien
- Falls erforderlich, Deaktivieren des CDN

Lesen Sie schließlich, wie Sie [Ihre CDN-Ressourcen verwenden](use-office-365-cdn-with-spo.md#using-your-cdn-assets) , um mehr über den Zugriff auf Ihre CDN-Ressourcen aus öffentlichen und privaten Quellen zu erfahren.

Hinweise zur Lösung häufig auftretender Probleme finden Sie unter [Troubleshooting the Office 365 CDN](use-office-365-cdn-with-spo.md#CDNTroubleshooting) .

## <a name="plan-for-deployment-of-the-office-365-cdn"></a>Planen der Bereitstellung von Office 365 CDN

Bevor Sie das Office 365 CDN für Ihren Office 365-Mandanten bereitstellen, sollten Sie die folgenden Faktoren als Teil des Planungsprozesses berücksichtigen.

  - [Bestimmen der statischen Objekte, die im CDN gehostet werden sollen](use-office-365-cdn-with-spo.md#CDNAssets)
  - [Bestimmen, wo Ihre Objekte gespeichert werden sollen](use-office-365-cdn-with-spo.md#CDNStoreAssets)
  - [Wählen Sie aus, ob jeder Ursprung öffentlich oder privat sein soll.](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate)

### <a name="determine-which-static-assets-you-want-to-host-on-the-cdn"></a>Bestimmen der statischen Objekte, die im CDN gehostet werden sollen
<a name="CDNAssets"> </a>

Im Allgemeinen sind CDNs am effektivsten für das Hosten _statischer Objekte_oder für Objekte, die sich nicht sehr häufig ändern. Eine gute Faustregel besteht darin, Dateien zu identifizieren, die einige oder alle dieser Bedingungen erfüllen:

- In eine Seite eingebettete statische Dateien (wie Skripts und Bilder), die sich möglicherweise erheblich inkrementell auf Seitenladezeiten auswirken
- Umfangreiche Dateien wie Executables und Installationsdateien
- Streaming-Mediendateien
- Ressourcen Bibliotheken, die clientseitigen Code unterstützen

Beispielsweise können kleine Dateien, die wiederholt wie Website Bilder und Skripts angefordert werden, die Leistung des Website Renderings erheblich verbessern und die Last für Ihre SharePoint Online-Websites inkrementell verringern, wenn Sie Sie zu einem CDN-Ursprung hinzufügen. Größere Dateien wie Installations-Executables oder Videodateien können heruntergeladen oder aus dem CDN gestreamt werden, was eine positive Leistungsbeeinträchtigung und eine anschließende Reduzierung der Last auf Ihrer SharePoint Online-Website ermöglicht, auch wenn nicht so oft auf Sie zugegriffen wird.

Die Leistungsverbesserung pro Datei hängt von vielen Faktoren ab, einschließlich der Nähe des Clients zum nächstgelegenen CDN-Endpunkt, Transienten Bedingungen im lokalen Netzwerk usw. Viele statische Dateien sind relativ klein und können von Office 365 in weniger als einer Sekunde heruntergeladen werden. Eine Webseite kann jedoch viele eingebettete Dateien mit einer kumulativen Downloadzeit von mehreren Sekunden enthalten. Die bereitstellungdieser Dateien aus dem CDN kann die Ladezeit der gesamten Seite erheblich reduzieren. Sehen Sie, [welche Leistungssteigerungen ein CDN bereitstellt](content-delivery-networks.md#what-performance-gains-does-a-cdn-provide) . ein Beispiel.

### <a name="determine-where-you-want-to-store-your-assets"></a>Bestimmen, wo Ihre Objekte gespeichert werden sollen
<a name="CDNStoreAssets"> </a>

Das CDN ruft Ihre Objekte von einem Speicherort ab, der als _Ursprung_bezeichnet wird. Bei einem Ursprung kann es sich um eine SharePoint-Website, eine Dokumentbibliothek oder einen Ordner handeln, auf die über eine URL zugegriffen wird. Sie haben große Flexibilität, wenn Sie die Ursprünge für Ihre Organisation angeben. Sie können beispielsweise mehrere Ursprünge oder einen einzelnen Ursprung angeben, in dem Sie alle CDN-Ressourcen platzieren möchten. Sie können sowohl öffentliche als auch private Ursprünge für Ihre Organisation wählen. Die meisten Organisationen wählen eine Kombination der beiden implementieren.

Sie können neue Container für ihre Ursprünge wie Ordner oder Dokumentbibliotheken erstellen und Dateien hinzufügen, die Sie im CDN zur Verfügung stellen möchten. Dies ist ein guter Ansatz, wenn Sie über einen bestimmten Satz von Objekten verfügen, die im CDN verfügbar sein sollen, und die Menge der CDN-Objekte auf die Dateien im Container einschränken möchten.

Sie können auch eine vorhandene Websitesammlung, eine Website, eine Bibliothek oder einen Ordner als Ursprung konfigurieren, wodurch alle berechtigten Objekte im Container im CDN verfügbar gemacht werden. Bevor Sie einen vorhandenen Container als Ursprung hinzufügen, müssen Sie sicherstellen, dass Sie die Inhalte und Berechtigungen beachten, damit Sie Objekte nicht versehentlich anonymen Zugriffen oder nicht autorisierten Benutzern offen legen.

Sie können _CDN-Richtlinien_ definieren, um Inhalte aus dem CDN auszuschließen. CDN-Richtlinien schließen Objekte in öffentlichen oder privaten Quellen nach Attributen wie _Dateityp_ und _Website Klassifizierung_aus und werden auf alle Ursprünge der CdnType (privat oder öffentlich) angewendet, die Sie in der Richtlinie angeben. Wenn Sie beispielsweise einen privaten Ursprung hinzufügen, der aus einer Website besteht, die mehrere Unterwebsites enthält, können Sie eine Richtlinie zum Ausschließen von als **vertraulich** markierten Websites definieren, sodass Inhalte von Websites mit dieser Klassifizierung nicht aus dem CDN bedient werden. Die Richtlinie gilt für Inhalte _aller_ privaten Ursprünge, die Sie dem CDN hinzugefügt haben.
  
Beachten Sie, dass je größer die Anzahl der Ursprünge ist, desto größer ist die Auswirkung auf die Zeit, die der CDN-Dienst zum Verarbeiten von Anforderungen benötigt. Es wird empfohlen, die Anzahl der Ursprünge so weit wie möglich zu begrenzen.
  
### <a name="choose-whether-each-origin-should-be-public-or-private"></a>Wählen Sie aus, ob jeder Ursprung öffentlich oder privat sein soll.
<a name="CDNOriginChoosePublicPrivate"> </a>

Wenn Sie einen Ursprung identifizieren, geben Sie an, ob er _öffentlich_ oder _Privat_erfolgen soll. Der Zugriff auf CDN-Ressourcen in öffentlichen Quellen ist anonym, und CDN-Inhalte in privaten Quellen werden durch dynamisch generierte Token für größere Sicherheit gesichert. Unabhängig davon, welche Option Sie auswählen, stellt Microsoft die gesamte Schwerlast für Sie, wenn es um die Verwaltung des CDN selbst geht. Außerdem können Sie Ihre Bedenken später ändern, nachdem Sie das CDN eingerichtet und ihre Ursprünge identifiziert haben.

Sowohl öffentliche als auch private Optionen bieten ähnliche Leistungssteigerungen, verfügen jedoch über eindeutige Attribute und Vorteile.

**Öffentliche** Ursprünge innerhalb des Office 365 CDN sind anonym zugänglich, auf gehostete Ressourcen kann jeder zugreifen, der über die URL des Objekts verfügt. Da der Zugriff auf Inhalte in öffentlichen Ursprüngen anonym ist, sollten Sie diese nur zum Zwischenspeichern von nicht vertraulichen generischen Inhalten verwenden, z. B. JavaScript-Dateien, Skripts, Symbole oder Bilder.

**Private** Ursprünge im Office 365-Netzwerk für die Inhaltsübermittlung bieten privaten Zugriff auf Benutzerinhalte, z. B. SharePoint Online-Dokumentbibliotheken, Websites und Medien wie Videos. Der Zugriff auf Inhalte in privaten Quellen wird durch dynamisch generierte Token gesichert, sodass nur Benutzern mit Berechtigungen für die ursprüngliche Dokumentbibliothek oder den Speicherort zugegriffen werden kann. Private Origins im Office 365 CDN können nur für SharePoint Online-Inhalte verwendet werden, und Sie können nur über die Umleitung von Ihrem SharePoint Online-Mandanten auf Objekte in privaten Quellen zugreifen.

Weitere Informationen dazu, wie der CDN-Zugriff auf Privat Ressourcen in privaten [Quellen verwendet](use-office-365-cdn-with-spo.md#using-assets-in-private-origins)werden kann, ist die Verwendung von Objekten unter privater Herkunft.

#### <a name="attributes-and-advantages-of-hosting-assets-in-public-origins"></a>Attribute und Vorteile des Hostings von Objekten in öffentlichen Ursprüngen
  
- Objekte, die an einem öffentlichen Ursprung verfügbar gemacht werden, sind für jeden Benutzer anonym zugänglich.
    > [!IMPORTANT]
    > Sie sollten niemals Ressourcen mit Benutzerinformationen platzieren oder als vertraulich für Ihre Organisation in einem öffentlichen Ursprung gelten.
- Wenn Sie ein Objekt aus einem öffentlichen Ursprung entfernen, ist es unter Umständen bis zu 30 Tage lang weiterhin über den Cache verfügbar. Links zu dem Objekt im CDN werden jedoch innerhalb von 15 Minuten ungültig.
- Wenn Sie Stylesheets (CSS-Dateien) an einem öffentlichen Ursprung hosten, können Sie im Code relative Pfade und URIs verwenden. Dies bedeutet, dass Sie auf den Speicherort von Hintergrundbildern und anderen Objekten relativ zum Speicherort des Objekts, das sie aufruft, verweisen können.
- Die URL eines öffentlichen Ursprungs kann zwar hartcodiert werden, dies wird jedoch nicht empfohlen. Der Grund hierfür ist folgender: Wenn der Zugriff auf das CDN nicht mehr verfügbar ist, wird die URL nicht automatisch auf Ihre Organisation in SharePoint Online aufgelöst, was zu fehlerhaften Links und anderen Fehlern führen kann.
- Die standardmäßigen Dateitypen, die für öffentliche Ursprünge eingeschlossen werden, sind CSS, EOT, GIF, ICO, JPEG, JPG, JS, MAP, PNG, SVG, TTF und WOFF. Sie können zusätzliche Dateitypen angeben.
- Sie können eine Richtlinie so konfigurieren, dass von Ihnen angegebene Ressourcen ausgeschlossen werden. Beispielsweise können Sie alle Objekte ausschließen, die als „vertraulich“ oder „eingeschränkt“ gekennzeichnet sind, auch wenn sie einen zulässigen Dateityp haben und sich an einem öffentlichen Ursprung befinden.

#### <a name="attributes-and-advantages-of-hosting-assets-in-private-origins"></a>Attribute und Vorteile des Hostings von Objekten in privaten Quellen

- Private Origins können nur für SharePoint Online-Objekte verwendet werden.
- Benutzer können nur von einem privaten Ursprung aus auf die Objekte zugreifen, wenn Sie über Berechtigungen für den Zugriff auf den Container verfügen. Der anonyme Zugriff auf diese Objekte wird verhindert.
- Objekte in privater Herkunft müssen vom SharePoint Online-mandantenbezogen werden. Der direkte Zugriff auf private CDN-Ressourcen funktioniert nicht.
- Wenn Sie ein Objekt aus dem privaten Ursprung entfernen, kann das Objekt weiterhin bis zu einer Stunde aus dem Cache verfügbar sein; Wir werden jedoch innerhalb von 15 Minuten nach dem Entfernen der Ressource Links zu dem Asset im CDN ungültig machen.
- Die standardmäßigen Dateitypen, die für private Ursprünge eingeschlossen werden, sind GIF, ICO, JPEG, JPG, JS und PNG. Sie können zusätzliche Dateitypen angeben.
- Genau wie bei öffentlichen Ursprüngen können Sie eine Richtlinie so konfigurieren, dass Objekte ausgeschlossen werden, die durch von Ihnen angegebene Website Klassifikationen identifiziert wurden, auch wenn Sie Platzhalter verwenden, um alle Objekte in einen Ordner oder eine Dokumentbibliothek einzuschließen.

Weitere Informationen zur Verwendung der Office 365 CDN, der allgemeinen CDN-Konzepte und anderer Microsoft-CDNs, die Sie mit Ihrem Office 365-Mandanten verwenden können, finden Sie unter [Content Delivery Networks](content-delivery-networks.md).

### <a name="default-cdn-origins"></a>Standardmäßige CDN-Ursprünge

Sofern Sie nichts anderes angeben, richtet Office 365 einige Standard Ursprünge ein, wenn Sie das Office 365 CDN aktivieren. Wenn Sie sich zunächst dafür entscheiden, Sie nicht zuzustellen, können Sie diese Ursprünge nach Abschluss des Setups hinzufügen. Wenn Sie die Konsequenzen des Überspringens der Einrichtung von Standard Ursprüngen nicht verstehen und einen bestimmten Grund dafür haben, sollten Sie diese erstellen lassen, wenn Sie das CDN aktivieren.
  
Standardmäßige private CDN-Ursprünge:
  
- \*/userphoto.aspx
- \*/SiteAssets

Standardmäßige öffentliche CDN-Ursprünge:
  
- \*/MasterPage
- \*/Style-Bibliothek
- \*/clientsideassets

> [!NOTE]
> _clientsideassets_ ist ein Standard öffentlicher Ursprung, der im Dezember 2017 dem Office 365 CDN-Dienst hinzugefügt wurde. Dieser Ursprung muss vorhanden sein, damit SharePoint-Framework-Lösungen im CDN funktionieren. Wenn Sie das Office 365 CDN vor dem Dezember 2017 aktiviert haben oder wenn Sie die Einrichtung der Standard Ursprünge beim Aktivieren des CDN übersprungen haben, können Sie diesen Ursprung manuell hinzufügen. Weitere Informationen finden Sie unter [mein clientseitiges Webpart oder SharePoint Framework-Lösung funktioniert nicht](use-office-365-cdn-with-spo.md#my-client-side-web-part-or-sharepoint-framework-solution-isnt-working).

## <a name="set-up-and-configure-the-office-365-cdn-by-using-the-sharepoint-online-management-shell"></a>Einrichten und Konfigurieren des Office 365 CDN mithilfe der SharePoint Online-Verwaltungsshell
<a name="CDNSetupinPShell"> </a>

In den Verfahren in diesem Abschnitt müssen Sie die SharePoint Online-Verwaltungsshell verwenden, um eine Verbindung mit SharePoint Online herzustellen. Weitere Anweisungen finden Sie unter [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).
  
Führen Sie die folgenden Schritte aus, um das CDN einzurichten und zu konfigurieren, um Ihre Objekte in SharePoint Online mit der SharePoint Online-Verwaltungsshell zu hosten.
  
### <a name="enable-your-organization-to-use-the-office-365-cdn"></a>Aktivieren Ihrer Organisation für die Verwendung des Office 365 CDN

Bevor Sie Änderungen an den Mandanten CDN-Einstellungen vornehmen, sollten Sie den aktuellen Status der privaten CDN-Konfiguration in Ihrem Office 365-Mandanten abrufen. Stellen Sie mithilfe der SharePoint Online-Verwaltungsshell eine Verbindung zu Ihrem Mandanten her:

``` powershell
Connect-SPOService -Url https://contoso-admin.sharepoint.com
```

Verwenden Sie jetzt das Cmdlet **Get-SPOTenantCdnEnabled** , um die CDN-Statuseinstellungen vom Mandanten abzurufen:

``` powershell
Get-SPOTenantCdnEnabled -CdnType <Public | Private>
```

Der Status des CDN für die angegebene CdnType wird auf dem Bildschirm ausgegeben.

Verwenden Sie das Cmdlet **Set-SPOTenantCdnEnabled** , um Ihrer Organisation das Office 365 CDN zu ermöglichen. Sie können es Ihrer Organisation ermöglichen, öffentliche Ursprünge, private Ursprünge oder beides gleichzeitig zu verwenden. Sie können das CDN auch so konfigurieren, dass die Einrichtung der Standard Ursprünge übersprungen wird, wenn Sie es aktivieren. Sie können diese Ursprünge immer später hinzufügen, wie in diesem Thema beschrieben.
  
In Windows PowerShell für SharePoint Online:

``` powershell
Set-SPOTenantCdnEnabled -CdnType <Public | Private | Both> -Enable $true
```

Geben Sie beispielsweise den folgenden Befehl ein, um Ihrer Organisation die Verwendung von öffentlichen und privaten Ursprüngen zu ermöglichen:

``` powershell
Set-SPOTenantCdnEnabled -CdnType Both -Enable $true
```

Geben Sie den folgenden Befehl ein, um zu ermöglichen, dass Ihre Organisation sowohl öffentliche als auch private Ursprünge verwendet, aber die Standard Ursprünge nicht festlegt:

``` powershell
Set-SPOTenantCdnEnabled -CdnType Both -Enable $true -NoDefaultOrigins
```

Informationen zu den Ursprüngen, die bei der Aktivierung des Office 365 CDN standardmäßig bereitgestellt werden, und die potenziellen Auswirkungen des Überspringens der Einrichtung von Standard Ursprüngen finden Sie unter [default CDN Origins](use-office-365-cdn-with-spo.md#default-cdn-origins) .

Geben Sie den folgenden Befehl ein, um Ihrer Organisation die Verwendung öffentlicher Ursprünge zu ermöglichen:

``` powershell
Set-SPOTenantCdnEnabled -CdnType Public -Enable $true
```

Geben Sie den folgenden Befehl ein, um Ihrer Organisation die Verwendung privater Ursprünge zu ermöglichen:

``` powershell
Set-SPOTenantCdnEnabled -CdnType Private -Enable $true
```

Weitere Informationen zu diesem Cmdlet finden Sie unter [Set-SPOTenantCdnEnabled](https://technet.microsoft.com/en-us/library/mt790765.aspx).
  
### <a name="change-the-list-of-file-types-to-include-in-the-office-365-cdn-optional"></a>Ändern der Liste der Dateitypen, die in Office 365 CDN eingeschlossen werden sollen (optional)
<a name="Office365CDNforSPOFileType"> </a>

> [!TIP]
> Wenn Sie Dateitypen mithilfe des Cmdlets **Set-SPOTenantCdnPolicy** definieren, überschreiben Sie die aktuell definierte Liste. Wenn Sie der Liste weitere Dateitypen hinzufügen möchten, verwenden Sie zuerst das Cmdlet, um herauszufinden, welche Dateitypen bereits zulässig sind, und fügen Sie diese in die Liste zusammen mit ihren neuen ein.
  
Verwenden Sie das Cmdlet **Set-SPOTenantCdnPolicy** , um statische Dateitypen zu definieren, die von öffentlichen und privaten Ursprüngen im CDN gehostet werden können. Standardmäßig sind allgemeine Objekttypen zulässig, beispielsweise CSS, GIF, JPG und JS.

In Windows PowerShell für SharePoint Online:

``` powershell
Set-SPOTenantCdnPolicy -CdnType <Public | Private> -PolicyType IncludeFileExtensions -PolicyValue "<Comma-separated list of file types >"
```

Um dem CDN beispielsweise das Hosten von CSS-und PNG-Dateien zu ermöglichen, geben Sie den folgenden Befehl ein:

``` powershell
Set-SPOTenantCdnPolicy -CdnType Private -PolicyType IncludeFileExtensions -PolicyValue "CSS,PNG"
```

Verwenden Sie das Cmdlet **Get-SPOTenantCdnPolicies** , um zu sehen, welche Dateitypen derzeit im CDN zulässig sind:

``` powershell
Get-SPOTenantCdnPolicies -CdnType <Public | Private>
```

Weitere Informationen zu diesen Cmdlets finden Sie unter [Set-SPOTenantCdnPolicy](https://technet.microsoft.com/en-us/library/mt800839.aspx) und [Get-SPOTenantCdnPolicies](https://technet.microsoft.com/en-us/library/mt800838.aspx).
  
### <a name="change-the-list-of-site-classifications-you-want-to-exclude-from-the-office-365-cdn-optional"></a>Ändern der Liste der Website Klassifikationen, die Sie aus dem Office 365 CDN ausschließen möchten (optional)
<a name="Office365CDNforSPOSiteClassification"> </a>

> [!TIP]
> Wenn Sie Website Klassifizierungen mithilfe des Cmdlets **Set-SPOTenantCdnPolicy** ausschließen, überschreiben Sie die aktuell definierte Liste. Wenn Sie zusätzliche Website Klassifizierungen ausschließen möchten, verwenden Sie zuerst das Cmdlet, um herauszufinden, welche Klassifizierungen bereits ausgeschlossen sind, und fügen Sie Sie dann zusammen mit ihren neuen hinzu.

Verwenden Sie das Cmdlet **Set-SPOTenantCdnPolicy** -Cmdlet zum Ausschließen von Websiteklassifizierungen, die Sie nicht über das CDN zur Verfügung stellen möchten. Standardmäßig sind keine Websiteklassifizierungen ausgeschlossen.

In Windows PowerShell für SharePoint Online:

``` powershell
Set-SPOTenantCdnPolicy -CdnType <Public | Private> -PolicyType ExcludeRestrictedSiteClassifications  -PolicyValue "<Comma-separated list of site classifications >"
```

Verwenden Sie das Cmdlet **Get-SPOTenantCdnPolicies** , um zu sehen, welche Website Klassifizierungen derzeit eingeschränkt sind:

``` powershell
Get-SPOTenantCdnPolicies -CdnType <Public | Private>
```

Die zurückgegebenen Eigenschaften sind _IncludeFileExtensions_, _ExcludeRestrictedSiteClassifications_ und _ExcludeIfNoScriptDisabled_.

Die _IncludeFileExtensions_ -Eigenschaft enthält die Liste der Dateierweiterungen, die aus dem CDN bedient werden.

> [!NOTE]
> Die standardmäßigen Dateierweiterungen unterscheiden sich zwischen öffentlich und privat.

Die _ExcludeRestrictedSiteClassifications_ -Eigenschaft enthält die Website Klassifizierungen, die Sie aus dem CDN ausschließen möchten. Sie können beispielsweise als **vertraulich** gekennzeichnete Websites ausschließen, sodass Inhalte von Websites mit dieser Klassifizierung nicht aus dem CDN bedient werden.

Die _ExcludeIfNoScriptDisabled_ -Eigenschaft schließt Inhalte aus dem CDN basierend auf den NoScript- __ Attributeinstellungen auf Websiteebene aus. Standardmäßig ist das _NoScript_ -Attribut für _moderne_ Websites **aktiviert** und für _klassische_ Websites **deaktiviert** . Dies hängt von ihren Mandanten Einstellungen ab.

Weitere Informationen zu diesen Cmdlets finden Sie unter [Set-SPOTenantCdnPolicy](https://technet.microsoft.com/en-us/library/mt800839.aspx) und [Get-SPOTenantCdnPolicies](https://technet.microsoft.com/en-us/library/mt800838.aspx).
  
### <a name="add-an-origin-for-your-assets"></a>Hinzufügen eines Ursprungs für Ihre Objekte
<a name="Office365CDNforSPOOrigin"> </a>

Verwenden Sie das Cmdlet **Add-SPOTenantCdnOrigin** , um einen Ursprung zu definieren. Sie können mehrere Ursprünge definieren. Der Ursprung ist eine URL, die auf eine SharePoint-Bibliothek oder einen Ordner mit den Objekten verweist, die vom CDN gehostet werden sollen.
  
> [!IMPORTANT]
> Sie sollten niemals Ressourcen mit Benutzerinformationen platzieren oder als vertraulich für Ihre Organisation in einem öffentlichen Ursprung gelten.

``` powershell
Add-SPOTenantCdnOrigin -CdnType <Public | Private> -OriginUrl <path>
```

Der Wert von _path_ ist der relative Pfad zu der Bibliothek oder dem Ordner, der die Objekte enthält. Sie können Platzhalter zusätzlich zu relativen Pfaden verwenden. Origins unterstützen Platzhalter, die der URL vorangestellt werden. Auf diese Weise können Sie Ursprünge erstellen, die sich über mehrere Standorte erstrecken. Geben Sie beispielsweise den folgenden Befehl ein, um alle Objekte im Ordner MasterPages für alle Websites als öffentlichen Ursprung innerhalb des CDN einzuschließen:

``` powershell
Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
```

- Der Platzhalter-**/** Modifizierer * kann nur am Anfang des Pfads verwendet werden und entspricht allen URL-Segmenten unter der angegebenen URL.
- Der Pfad kann auf eine Dokumentbibliothek, einen Ordner oder eine Website verweisen. Beispielsweise entspricht der Pfad _*/site1_ allen Dokumentbibliotheken unter der Website.

Sie können einen Ursprung mit einem bestimmten relativen Pfad hinzufügen. Sie können keinen Ursprung unter Verwendung des vollständigen Pfads hinzufügen.

In diesem Beispiel wird ein privater Ursprung der SiteAssets-Bibliothek auf einer bestimmten Website hinzugefügt:

``` powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl sites/site1/siteassets
```

In diesem Beispiel wird ein privater Ursprung des Ordners _Folder1_ in der Bibliothek Website Objekte der Websitesammlung hinzugefügt:

``` powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl “/sites/test/siteassets/folder1”
```

Weitere Informationen zu diesem Befehl und seiner Syntax finden Sie unter [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).

> [!NOTE]
> In privaten Quellen muss für die von einem Ursprung freigegebenen Objekte eine Hauptversion veröffentlicht werden, bevor auf Sie über das CDN zugegriffen werden kann.
  
Nachdem Sie den Befehl ausgeführt haben, wird die Konfiguration im Datencenter vom System synchronisiert. Dies kann bis zu 15 Minuten dauern.
  
### <a name="example-configure-a-public-origin-for-your-master-pages-and-for-your-style-library-for-sharepoint-online"></a>Beispiel: Konfigurieren eines öffentlichen Ursprungs für Ihre Gestaltungsvorlagen und für Ihre Stilbibliothek für SharePoint Online
<a name="ExamplePublicOrigin"> </a>

NormalerWeise werden diese Ursprünge standardmäßig für Sie eingerichtet, wenn Sie das Office 365 CDN aktivieren. Wenn Sie Sie jedoch manuell aktivieren möchten, führen Sie die folgenden Schritte aus.
  
- Verwenden Sie das Cmdlet **Add-SPOTenantCdnOrigin** , um die Formatbibliothek als öffentlichen Ursprung zu definieren.

``` powershell
  Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */style%20library
  ```

- Verwenden Sie das Cmdlet **Add-SPOTenantCdnOrigin** , um die Gestaltungsvorlagen als öffentlichen Ursprung zu definieren.

``` powershell
  Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
  ```

Weitere Informationen zu diesem Befehl und seiner Syntax finden Sie unter [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).

Nachdem Sie den Befehl ausgeführt haben, wird die Konfiguration im Datencenter vom System synchronisiert. Dies kann bis zu 15 Minuten dauern.

### <a name="example-configure-a-private-origin-for-your-site-assets-site-pages-and-publishing-images-for-sharepoint-online"></a>Beispiel: Konfigurieren eines privaten Ursprungs für Ihre Website Objekte, Website Seiten und Veröffentlichen von Bildern für SharePoint Online
<a name="ExamplePrivateOrigin"> </a>

- Verwenden Sie das Cmdlet **Add-SPOTenantCdnOrigin** , um den Ordnerstandort Objekte als privaten Ursprung zu definieren.

``` powershell
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */siteassets
  ```

- Verwenden Sie das Cmdlet **Add-SPOTenantCdnOrigin** , um den Ordner Website Seiten als privaten Ursprung zu definieren.

``` powershell
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */sitepages
  ```

- Verwenden Sie das Cmdlet **Add-SPOTenantCdnOrigin** , um den Ordner Veröffentlichungs Bilder als privaten Ursprung zu definieren.

``` powershell
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */publishingimages
  ```

Weitere Informationen zu diesem Befehl und seiner Syntax finden Sie unter [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).

Nachdem Sie den Befehl ausgeführt haben, wird die Konfiguration im Datencenter vom System synchronisiert. Dies kann bis zu 15 Minuten dauern.

### <a name="example-configure-a-private-origin-for-a-site-collection-for-sharepoint-online"></a>Beispiel: Konfigurieren eines privaten Ursprungs für eine Websitesammlung für SharePoint Online
<a name="ExamplePrivateOriginSiteCollection"> </a>

Verwenden Sie das Cmdlet **Add-SPOTenantCdnOrigin** , um eine Websitesammlung als privaten Ursprung zu definieren. Beispiel:

``` powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl sites/site1/siteassets
```

Weitere Informationen zu diesem Befehl und seiner Syntax finden Sie unter [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).
  
Nachdem Sie den Befehl ausgeführt haben, wird die Konfiguration im Datencenter vom System synchronisiert. Möglicherweise wird eine Meldung zur _Konfiguration_ ausstehend angezeigt, die erwartet wird, wenn der SharePoint Online-Mandant eine Verbindung mit dem CDN-Dienst herstellt. Dies kann bis zu 15 Minuten dauern.

### <a name="manage-the-office-365-cdn"></a>Verwalten des Office 365 CDN
<a name="CDNManage"> </a>

Nachdem Sie das CDN eingerichtet haben, können Sie Änderungen an Ihrer Konfiguration vornehmen, wenn Sie Inhalte aktualisieren oder Ihre Anforderungen ändern, wie in diesem Abschnitt beschrieben.
  
#### <a name="add-update-or-remove-assets-from-the-office-365-cdn"></a>Hinzufügen, aktualisieren oder Entfernen von Objekten aus dem Office 365 CDN
<a name="Office365CDNforSPOaddremoveasset"> </a>

Nachdem Sie die Setupschritte ausgeführt haben, können Sie neue Ressourcen hinzufügen und vorhandene Objekte aktualisieren oder entfernen, wann immer Sie möchten. Nehmen Sie die Änderungen an den Objekten im Ordner oder in der SharePoint-Bibliothek vor, die Sie als Ursprung identifiziert haben. Wenn Sie ein neues Objekt hinzufügen, ist es sofort über das CDN verfügbar. Wenn Sie jedoch das Objekt aktualisieren, dauert es bis zu 15 Minuten, bis die neue Kopie weitergegeben wird und im CDN verfügbar wird.
  
Wenn Sie den Speicherort des Ursprungs abrufen müssen, können Sie das Cmdlet **Get-spotenantcdnorigins ausführen** verwenden. Informationen zur Verwendung dieses Cmdlets finden Sie unter [Get-spotenantcdnorigins ausführen](https://technet.microsoft.com/en-us/library/mt790770.aspx).
  
#### <a name="remove-an-origin-from-the-office-365-cdn"></a>Entfernen eines Ursprungs aus dem Office 365 CDN
<a name="Office365CDNforSPORemoveOrigin"> </a>

Sie können den Zugriff auf einen Ordner oder eine SharePoint-Bibliothek entfernen, die Sie als Ursprung identifiziert haben. Verwenden Sie hierzu das Cmdlet **Remove-SPOTenantCdnOrigin** .

``` powershell
Remove-SPOTenantCdnOrigin -OriginUrl <path> -CdnType <Public | Private | Both>
```

Informationen zur Verwendung dieses Cmdlets finden Sie unter [Remove-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790761.aspx).
  
#### <a name="modify-an-origin-in-the-office-365-cdn"></a>Ändern eines Ursprungs im Office 365 CDN
<a name="Office365CDNforSPORemoveOrigin"> </a>

Sie können einen Ursprung, den Sie erstellt haben, nicht ändern. Entfernen Sie stattdessen den Ursprung, und fügen Sie dann einen neuen hinzu. Weitere Informationen finden Sie unter [So entfernen Sie einen Ursprung aus dem Office 365 CDN](use-office-365-cdn-with-spo.md#Office365CDNforSPORemoveOrigin) und [fügen einen Ursprung für Ihre Objekte hinzu](use-office-365-cdn-with-spo.md#Office365CDNforSPOOrigin).
  
#### <a name="disable-the-office-365-cdn"></a>Deaktivieren von Office 365 CDN
<a name="Office365CDNforSPODisable"> </a>

Verwenden Sie das Cmdlet **Set-SPOTenantCdnEnabled** , um das CDN für Ihre Organisation zu deaktivieren. Wenn sowohl der öffentliche als auch der private Ursprung für das CDN aktiviert ist, müssen Sie das Cmdlet doppelt ausführen, wie in den folgenden Beispielen gezeigt.
  
Um die Verwendung öffentlicher Ursprünge im CDN zu deaktivieren, geben Sie den folgenden Befehl ein:

``` powershell
Set-SPOTenantCdnEnabled -CdnType Public -Enable $false
```

Um die Verwendung privater Ursprünge im CDN zu deaktivieren, geben Sie den folgenden Befehl ein:

``` powershell
Set-SPOTenantCdnEnabled -CdnType Private -Enable $false
```

Weitere Informationen zu diesem Cmdlet finden Sie unter [Set-SPOTenantCdnEnabled](https://technet.microsoft.com/en-us/library/mt790765.aspx).

## <a name="set-up-and-configure-the-office-365-cdn-using-the-office-365-cli"></a>Einrichten und Konfigurieren des Office 365 CDN mithilfe von Office 365 CLI
<a name="CDNSetupinCLI"> </a>

Die Verfahren in diesem Abschnitt erfordern, dass Sie die [Office 365 CLI](https://aka.ms/o365cli)installiert haben. Als Nächstes stellen Sie mit dem Befehl [spo connect](https://pnp.github.io/office365-cli/cmd/spo/connect/) eine Verbindung mit Ihrem SharePoint Online-Mandanten her.

Führen Sie die folgenden Schritte aus, um das CDN einzurichten und zu konfigurieren, um Ihre Objekte in SharePoint Online mit der Office 365 CLI zu hosten.

### <a name="enable-the-office-365-cdn"></a>Aktivieren des Office 365 CDN

Sie können den Status des Office 365 CDN in Ihrem Mandanten mithilfe des Cmdlets [spo cdn set](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-set/) verwalten.

Um das öffentliche Office 365 CDN in Ihrem Mandanten zu aktivieren, führen Sie Folgendes aus:

```sh
spo cdn set --type Public --enabled true
```

Führen Sie Folgendes aus, um das Office 365 SharePoint CDN zu aktivieren:

```sh
spo cdn set --type Private --enabled true
```

#### <a name="view-the-current-status-of-the-office-365-cdn"></a>Anzeigen des aktuellen Status des Office 365 CDN

Um zu überprüfen, ob der bestimmte Typ von Office 365 CDN aktiviert oder deaktiviert ist, verwenden Sie den Befehl [SPO CDN Get](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-get/) .

Um zu überprüfen, ob das öffentliche Office 365 CDN aktiviert ist, führen Sie Folgendes aus:

```sh
spo cdn get --type Public
```

### <a name="view-the-office-365-cdn-origins"></a>Anzeigen der Office 365 CDN-Ursprünge

Um die derzeit konfigurierten öffentlichen Office 365 CDN-Ursprünge anzuzeigen, führen Sie Folgendes aus:

```sh
spo cdn origin list --type Public
```

Informationen zu den Ursprüngen, die standardmäßig bereitgestellt werden, wenn Sie das Office 365 CDN aktivieren, finden Sie unter [default CDN Origins](use-office-365-cdn-with-spo.md#default-cdn-origins) .

### <a name="add-an-office-365-cdn-origin"></a>Hinzufügen eines Office 365 CDN-Ursprungs

> [!IMPORTANT]
> Sie sollten niemals Ressourcen, die für Ihre Organisation als vertraulich gelten, in einer SharePoint-Dokumentbibliothek platzieren, die als öffentlicher Ursprung konfiguriert ist.

Verwenden Sie den Befehl [spo cdn origin add](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-add/) zum Definieren eines CDN-Ursprungs. Sie können mehrere Ursprünge definieren. Der Ursprung ist eine URL, die auf eine SharePoint-Bibliothek oder einen Ordner mit den Objekten verweist, die vom CDN gehostet werden sollen.

```sh
spo cdn origin add --type [Public | Private] --origin <path>
```

Dabei `path` ist der relative Pfad zu dem Ordner, der die Objekte enthält. Sie können Platzhalter zusätzlich zu relativen Pfaden verwenden.

Um alle Objekte im **Gestaltungsvorlagenkatalog** aller Websites als öffentlichen Ursprung einzuschließen, führen Sie Folgendes aus:

```sh
spo cdn origin add --type Public --origin */masterpage
```

Um einen privaten Ursprung für eine bestimmte Websitesammlung zu konfigurieren, führen Sie Folgendes aus:

```sh
spo cdn origin add --type Private --origin sites/site1/siteassets
```

> [!NOTE]
> Nach dem Hinzufügen eines CDN-Ursprungs dauert es bis zu 15 Minuten, bis Sie Dateien mithilfe des CDN-Diensts abrufen können. Sie können überprüfen, ob der betreffende Ursprung bereits aktiviert wurde, indem Sie den Befehl [spo cdn origin list](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-list/) verwenden.

### <a name="remove-an-office-365-cdn-origin"></a>Entfernen eines Office 365 CDN-Ursprungs

Verwenden Sie den Befehl [spo cdn origin remove](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-remove/), um einen CDN-Ursprung für den angegebenen CDN-Typ zu entfernen.

Wenn Sie einen öffentlichen Ursprung aus der CDN-Konfiguration entfernen möchten, führen Sie Folgendes aus:

```sh
spo cdn origin remove --type Public --origin */masterpage
```

> [!NOTE]
> Das Entfernen eines CDN-Ursprungs hat keine Auswirkungen auf die Dateien, die in einer Dokumentbibliothek gespeichert sind, die mit diesem Ursprung übereinstimmt. Wenn auf diese Objekte mithilfe Ihrer SharePoint-URL verwiesen wird, wechselt SharePoint automatisch zurück zur ursprünglichen URL, die auf die Dokumentbibliothek zeigt. Wenn jedoch auf Objekte mithilfe einer öffentlichen CDN-URL verwiesen wurde, wird die Verknüpfung durch Entfernen des Ursprungs unterbrochen, und Sie müssen Sie manuell ändern.

### <a name="modify-an-office-365-cdn-origin"></a>Ändern eines Office 365 CDN-Ursprungs

Es ist nicht möglich, einen vorhandenen CDN-Ursprung zu ändern. Stattdessen sollten Sie den zuvor definierten CDN-Ursprung mit dem Befehl `spo cdn origin remove` entfernen und mit dem Befehl `spo cdn origin add` einen neuen hinzufügen.

### <a name="change-the-types-of-files-to-include-in-the-office-365-cdn"></a>Ändern der Dateitypen, die in Office 365 CDN eingeschlossen werden sollen

Standardmäßig sind die folgenden Dateitypen im CDN enthalten: _CSS, EOT, GIF, ICO, JPEG, JPG, JS, MAP, PNG, SVG, TTF und WOFF_. Wenn Sie weitere Dateitypen in das CDN einbeziehen müssen, können Sie die CDN-Konfiguration mit dem Befehl [spo cdn policy set](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-policy-set/) ändern.

> [!NOTE]
> Durch das Ändern der Liste von Dateitypen überschreiben Sie die aktuell definierte Liste. Wenn Sie weitere Dateitypen einbeziehen möchten, verwenden Sie zunächst den Befehl [spo cdn policy list](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-list/), um herauszufinden, welche Dateitypen derzeit konfiguriert sind.

Führen Sie den folgenden Befehl aus, um den _JSON_ -Dateityp zur Standardliste der im öffentlichen CDN enthaltenen Dateitypen hinzuzufügen:

```sh
spo cdn policy set --type Public --policy IncludeFileExtensions --value "CSS,EOT,GIF,ICO,JPEG,JPG,JS,MAP,PNG,SVG,TTF,WOFF,JSON"
```

### <a name="change-the-list-of-site-classifications-you-want-to-exclude-from-the-office-365-cdn"></a>Ändern der Liste von Websiteklassifizierungen, die Sie aus dem Office 365 CDN ausschließen möchten

Verwenden Sie den Befehl [spo cdn policy set](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-policy-set/) zum Ausschließen von Websiteklassifizierungen, die Sie nicht über das CDN zur Verfügung stellen möchten. Standardmäßig sind keine Websiteklassifizierungen ausgeschlossen.

> [!NOTE]
> Durch das Ändern der Liste der ausgeschlossenen Websiteklassifizierungen überschreiben Sie die aktuell definierte Liste. Wenn Sie zusätzliche Klassifizierungen ausschließen möchten, verwenden Sie zunächst den Befehl [spo cdn policy list](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-policy-list/), um herauszufinden, welche Klassifizierungen derzeit konfiguriert sind.

Zum Ausschließen von Websites, die als _HBI_ aus dem öffentlichen CDN klassifiziert wurden, führen Sie

```sh
spo cdn policy set --type Public --policy ExcludeRestrictedSiteClassifications --value "HBI"
```

### <a name="disable-the-office-365-cdn"></a>Deaktivieren von Office 365 CDN

Um das Office 365 CDN zu deaktivieren, verwenden Sie den Befehl `spo cdn set`. Beispiel:

```sh
spo cdn set --type Public --enabled false
```

## <a name="using-your-cdn-assets"></a>Verwenden der CDN-Ressourcen

Nachdem Sie das CDN aktiviert und die Ursprünge und Richtlinien konfiguriert haben, können Sie mit der Verwendung der CDN-Ressourcen beginnen.

In diesem Abschnitt erfahren Sie, wie Sie CDN-URLs in Ihren SharePoint-Seiten und-Inhalten verwenden können, damit SharePoint Anforderungen für Objekte in öffentlichen und privaten Quellen an das CDN umleitet.

- [Aktualisieren von Links zu CDN-Objekten](use-office-365-cdn-with-spo.md#updating-links-to-cdn-assets)
- [Verwenden von Objekten in öffentlichen Ursprüngen](use-office-365-cdn-with-spo.md#using-assets-in-public-origins)
- [Verwenden von Objekten in privaten Ursprüngen](use-office-365-cdn-with-spo.md#using-assets-in-private-origins)

Informationen zur Verwendung des CDN für das Hosten von clientseitigen Webparts finden Sie im Thema [Hosten des clientseitigen Webparts aus Office 365 CDN (Hello World, Teil 4)](https://docs.microsoft.com/en-us/sharepoint/dev/spfx/web-parts/get-started/hosting-webpart-from-office-365-cdn).

### <a name="updating-links-to-cdn-assets"></a>Aktualisieren von Links zu CDN-Objekten

Um Objekte zu verwenden, die Sie einem Ursprung hinzugefügt haben, aktualisieren Sie einfach die Links zur ursprünglichen Datei mit dem Pfad zu der Datei im Ursprung.

- Bearbeiten Sie die Seite oder den Inhalt, die Links zu Objekten enthält, die Sie einem Ursprung hinzugefügt haben. Sie können auch eine von mehreren Methoden verwenden, um Hyperlinks Global zu suchen und zu ersetzen, wenn Sie die Verknüpfung zu einem bestimmten Element überall dort, wo es angezeigt wird, aktualisieren möchten.
- Ersetzen Sie für jede Verknüpfung zu einem Objekt in einem Ursprung den Pfad durch den Pfad zu der Datei im CDN-Ursprung. Sie können relative Pfade verwenden.
- Speichern Sie die Seite oder den Inhalt.

Betrachten Sie beispielsweise das Bild _/Site/SiteAssets/Images/Image.png_, das Sie in den Dokumentbibliotheksordner _/Site/CDN_origins/Public/_ kopiert haben. Um das CDN-Objekt zu verwenden, ersetzen Sie den ursprünglichen Pfad zum Speicherort der Bild Datei durch den Pfad zum Ursprung, um die neue URL _/Site/CDN_origins/Public/Image.png_.

Wenn Sie die vollständige URL des Objekts anstelle eines relativen Pfads verwenden möchten, erstellen Sie den Link wie folgt:

`https://<TenantHostName>.sharepoint.com/sites/site/CDN_origins/public/image.png`

> [!NOTE]
> Im Allgemeinen sollten Sie URLs nicht direkt für Objekte im CDN hartcodieren. Sie können jedoch URLs für Objekte in öffentlichen Ursprüngen bei Bedarf manuell erstellen. Weitere Informationen finden Sie unter [hartcodieren von CDN-URLs für öffentliche Objekte](use-office-365-cdn-with-spo.md#hardcoding-cdn-urls-for-public-assets).

Informationen dazu, wie Sie überprüfen können, ob Objekte aus dem CDN bedient werden, finden Sie unter [wie bestätige ich, dass die Ressourcen vom CDN bedient werden?](use-office-365-cdn-with-spo.md#CDNConfirm) im Abschnitt [Troubleshooting the Office 365 CDN](use-office-365-cdn-with-spo.md#CDNTroubleshooting) .

### <a name="using-assets-in-public-origins"></a>Verwenden von Objekten in öffentlichen Ursprüngen

Das **Veröffentlichungsfeature** in SharePoint Online schreibt URLs der in öffentlichen Ursprüngen gespeicherten Objekte automatisch in Ihre CDN-äquivalente ein, sodass Objekte aus dem CDN-Dienst statt aus SharePoint bedient werden.

Wenn sich Ihr Ursprung in einer Website befindet, in der das Veröffentlichungsfeature aktiviert ist und die Objekte, die Sie in das CDN übertragen möchten, sich in einer der folgenden Kategorien befinden, wird SharePoint die URLs für Objekte im Ursprung automatisch neu schreiben, vorausgesetzt, dass das Objekt nicht von einem CDN ausgeschlossen wurde.  Richtlinie.

Es folgt eine Übersicht über die Links, die automatisch vom SharePoint-Veröffentlichungsfeature umgeschrieben werden:

- IMG/LINK/CSS-URLs in den HTML-Antworten klassischer Veröffentlichungsseiten
  - Dies schließt von Autoren im HTML-Inhalt einer Seite hinzugefügte Bilder ein.
- Bild-URLs des Webparts „Bildbibliothek-Bildschirmpräsentation“
- Bildfelder in Ergebnissen der SPList-REST-API (RenderListDataAsStream)
  - Verwenden der New-Eigenschaft _ImageFieldsToTryRewriteToCdnUrls_ zum Bereitstelleneiner durch Trennzeichen getrennten Liste von Feldern
  - Unterstützt Hyperlink-Felder und Publishing Image-Felder
- SharePoint-Bilddarstellungen

Das folgende Diagramm veranschaulicht den Workflow, wenn SharePoint eine Anforderung für eine Seite erhält, die Objekte aus einem öffentlichen Ursprung enthält.

![Workflow Diagramm: Abrufen von Office 365 CDN-Ressourcen aus einem öffentlichen Ursprung] (media/O365-CDN/o365-cdn-public-steps-transparent.svg "Workflow: Abrufen von Office 365 CDN-Ressourcen aus einem öffentlichen Ursprung")

> [!TIP]
> Wenn Sie die automatische Umschreibung für bestimmte URLs auf einer Seite deaktivieren möchten, können Sie die Seite Auschecken und den Abfragezeichenfolgenparameter **?NoAutoReWrites = true** am Ende jeder zu deaktivierenden Verknüpfung hinzufügen.

#### <a name="hardcoding-cdn-urls-for-public-assets"></a>Codieren von CDN-URLs für öffentliche Objekte

Wenn das _Veröffentlichungs_ Feature für einen öffentlichen Ursprung nicht aktiviert ist oder wenn es sich nicht um einen der vom Auto-Rewrite-Feature des CDN-Diensts unterstützten Linktypen handelt, können Sie URLs zum CDN-Speicherort der Objekte manuell erstellen und diese URLs in ihren Inhalten verwenden.

> [!NOTE]
> Sie können CDN-URLs nicht für Objekte in einem privaten Ursprung hartcodieren, da das erforderliche Zugriffstoken, das den letzten Abschnitt der URL bildet, zu dem Zeitpunkt generiert wird, zu dem die Ressource angefordert wird.

Bei öffentlichen CDN-Objekten sieht das URL-Format wie folgt aus:

``` html
https://publiccdn.sharepointonline.com/<TenantHostName>/sites/site/library/asset.png
```

Ersetzen Sie **TenantHostName** durch den Namen Ihres Mandanten. Beispiel:

``` html
https://publiccdn.sharepointonline.com/contoso.sharepoint.com/sites/site/library/asset.png
```

### <a name="using-assets-in-private-origins"></a>Verwenden von Objekten in privaten Ursprüngen

Für die Verwendung von Objekten in privaten Quellen ist keine zusätzliche Konfiguration erforderlich. SharePoint Online schreibt URLs automatisch für Objekte in privaten Quellen um, sodass Anforderungen für diese Objekte immer aus dem CDN bedient werden. Sie können keine URLs manuell erstellen, um Objekte in privaten Quellen zu CDN, da diese URLs Token enthalten, die von SharePoint Online automatisch generiert werden müssen, wenn das Objekt angefordert wird.

Der Zugriff auf Objekte in privaten Quellen wird durch dynamisch generierte Token basierend auf den Benutzerberechtigungen für den Ursprung mit den in den folgenden Abschnitten beschriebenen Einschränkungen geschützt. Benutzer benötigen mindestens **Lese** Zugriff auf die Ursprünge für das CDN, um Inhalte zu rendern.

Das folgende Diagramm veranschaulicht den Workflow, wenn SharePoint eine Anforderung für eine Seite erhält, die Objekte aus einem privaten Ursprung enthält.

![Workflow Diagramm: Abrufen von Office 365 CDN-Ressourcen von einem privaten Ursprung] (media/O365-CDN/o365-cdn-private-steps-transparent.svg "Workflow: Abrufen von Office 365 CDN-Ressourcen aus einem privaten Ursprung")

#### <a name="token-based-authorization-in-private-origins"></a>Token-basierte Autorisierung in privaten Ursprüngen

Der Zugriff auf Objekte in privaten Quellen im Office 365 CDN wird von Token gewährt, die von SharePoint Online generiert werden. Benutzer, die bereits über die Berechtigung zum Zugriff auf den vom Ursprung angegebenen Ordner oder die Bibliothek verfügen, erhalten automatisch Token, die es dem Benutzer ermöglichen, auf die Datei basierend auf Ihrer Berechtigungsstufe zuzugreifen. Diese Zugriffstoken sind 30 bis 90 Minuten lang gültig, nachdem Sie generiert wurden, um Token Replay-Angriffe zu verhindern.

Nachdem das Zugriffstoken generiert wurde, gibt SharePoint Online einen benutzerdefinierten URI an den Client zurück, der zwei Autorisierungsparameter _Eat_ (Edge Authorization Token) und _OAT_ (Origin-Autorisierungstoken) enthält. Die Struktur der einzelnen Token ist _<'expiration Time in Epoch Time Format'>__<'secure signature'>_. Beispiel:

``` html
https://privatecdn.sharepointonline.com/contoso.sharepoint.com/sites/site1/library1/folder1/image1.jpg?eat=1486154359_cc59042c5c55c90b26a2775323c7c8112718431228fe84d568a3795a63912840&oat=1486154359_7d73c2e3ba4b7b1f97242332900616db0d4ffb04312
```

> [!NOTE]
> Jeder, der über das Token verfügt, kann auf die Ressource im CDN zugreifen. URLs, die diese Zugriffstoken enthalten, werden jedoch nur über HTTPS freigegeben, es sei denn, die URL wird explizit von einem Endbenutzer freigegeben, bevor das Token abläuft, auf das Objekt können unbefugte Benutzer nicht zugreifen.

#### <a name="item-level-permissions-are-not-supported-for-assets-in-private-origins"></a>Berechtigungen auf Elementebene werden für Objekte in privaten Quellen nicht unterstützt.

Beachten Sie, dass SharePoint Online keine Berechtigungen auf Elementebene für Objekte in privaten Quellen unterstützt. Bei einer Datei unter `https://contoso.sharepoint.com/sites/site1/library1/folder1/image1.jpg`befindet sich der Benutzer beispielsweise in einem effektiven Zugriff auf die Datei, wenn die folgenden Bedingungen erfüllt sind:

|Benutzer  |Berechtigungen  |Effektiver Zugriff  |
|---------|---------|---------|
|Benutzer 1     |Zugriff auf Folder1         |Zugriff auf image1. jpg aus dem CDN         |
|Benutzer 2     |Hat keinen Zugriff auf Folder1         |Zugriff auf image1. jpg aus dem CDN nicht möglich         |
|Benutzer 3     |Hat keinen Zugriff auf Folder1, es wird jedoch eine explizite Berechtigung für den Zugriff auf image1. jpg in SharePoint Online erteilt.         |Zugriff auf die Ressource image1. jpg direkt über SharePoint Online, jedoch nicht über das CDN         |
|Benutzer 4     |Zugriff auf Folder1, der Zugriff auf image1. jpg in SharePoint Online wurde jedoch explizit verweigert.         |Zugriff auf das Objekt nicht über SharePoint Online, aber Zugriff auf das Objekt aus dem CDN, obwohl der Zugriff auf die Datei in SharePoint Online verweigert wurde         |

## <a name="troubleshooting-the-office-365-cdn"></a>Problembehandlung für Office 365 CDN
<a name="CDNTroubleshooting"> </a>

### <a name="how-do-i-confirm-that-assets-are-being-served-by-the-cdn"></a>Wie bestätige ich, dass die Ressourcen vom CDN bedient werden?
<a name="CDNConfirm"> </a>

Nachdem Sie Links zu CDN-Objekten zu einer Seite hinzugefügt haben, können Sie überprüfen, ob die Ressource aus dem CDN bedient wird, indem Sie zur Seite navigieren, mit der rechten Maustaste auf das Bild klicken, nachdem es gerendert wurde, und die Bild-URL überprüft.

Sie können die Entwicklertools des Browsers auch verwenden, um die URL für die einzelnen Ressourcen auf einer Seite anzuzeigen, oder um ein Netzwerk Ablaufverfolgungstool von Drittanbietern zu verwenden.

> [!NOTE]
> Wenn Sie ein Netzwerktool wie Fiddler verwenden, um Ihre Objekte außerhalb des Renderings des Objekts von einer SharePoint-Seite zu testen, müssen Sie den Referrer-Header "Referrer `https://yourdomain.sharepoint.com`:" manuell zur Get-Anforderung hinzufügen, wobei die URL die Stamm-URL Ihres SharePoint Online-Mandanten ist.

Sie können CDN-URLs nicht direkt in einem Webbrowser testen, da Sie über einen Verweis aus SharePoint Online verfügen müssen. Wenn Sie jedoch die CDN-Objekt-URL zu einer SharePoint-Seite hinzufügen und dann die Seite in einem Browser öffnen, sehen Sie das CDN-Objekt, das auf der Seite gerendert wird.

Weitere Informationen zur Verwendung der Entwicklertools im Microsoft Edge-Browser finden Sie unter [Microsoft Edge Developer Tools](https://docs.microsoft.com/en-us/microsoft-edge/devtools-guide).

### <a name="why-are-assets-from-a-new-origin-unavailable"></a>Warum sind Objekte aus einem neuen Ursprung nicht verfügbar?
Objekte in New Origins stehen nicht sofort zur Verfügung, da es Zeit braucht, bis die Registrierung über das CDN propagiert wird und die Objekte vom Ursprung zum CDN-Speicher hochgeladen werden. Die Zeit, die für die Verfügbarkeit von Objekten im CDN erforderlich ist, hängt von der Anzahl der Objekte und den Dateien ab.

### <a name="my-client-side-web-part-or-sharepoint-framework-solution-isnt-working"></a>Mein clientseitiges Webpart oder die SharePoint Framework-Lösung funktioniert nicht

Wenn Sie das Office 365 CDN für öffentliche Ursprünge aktivieren, erstellt der CDN-Dienst automatisch diese Standard Ursprünge:

- */MASTERPAGE
- */STYLE-BIBLIOTHEK
- */CLIENTSIDEASSETS

Wenn der */clientsideassets-Ursprung fehlt, treten bei SharePoint-Framework-Lösungen Fehler auf, und es werden keine Warnungen oder Fehlermeldungen generiert. Dieser Ursprung fehlt möglicherweise, weil das CDN aktiviert wurde, wobei der Parameter _-NoDefaultOrigins_ auf **$true**festgelegt ist, oder weil der Ursprung manuell gelöscht wurde.

Sie können überprüfen, ob der */CLIENTSIDEASSETS-Ursprung mit dem folgenden PowerShell-Befehl vorhanden ist:

``` powershell
Get-SPOTenantCdnOrigin -CdnType Public -OriginUrl */CLIENTSIDEASSETS
```

Oder Sie können mit der Office 365 CLI überprüfen:

``` powershell
spo cdn origin list
```

So fügen Sie den Ursprung in PowerShell hinzu:

``` powershell
Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */CLIENTSIDEASSETS
```

So fügen Sie den Ursprung in der Office 365 CLI hinzu:

``` powershell
spo cdn origin add --origin */CLIENTSIDEASSETS
```

### <a name="what-powershell-modules-and-cli-shells-do-i-need-to-work-with-the-office-365-cdn"></a>Welche PowerShell-Module und CLI-Shells muss ich für das Office 365 CDN verwenden?

Sie können mit dem Office 365 CDN entweder mit dem PowerShell-Modul der **SharePoint Online-Verwaltungsshell** oder mit der **Office 365 CLI**arbeiten.

- [Erste Schritte mit der SharePoint Online-Verwaltungsshell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)
- [Installieren von Office 365 CLI](https://pnp.github.io/office365-cli/user-guide/installing-cli/)

## <a name="see-also"></a>Siehe auch

[Netzwerke für die Inhaltsübermittlung](https://aka.ms/o365cdns)

[Netzwerkplanung und Leistungsoptimierung für Office 365](https://aka.ms/tune)

