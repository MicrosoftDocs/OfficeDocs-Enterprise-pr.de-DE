---
title: Verwenden Sie die Office 365 Content Delivery Networks mit SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 6/29/2018
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
description: Beschreibt, wie Office 365 des integrierten Content Delivery Network (CDN) verwenden, um die Bereitstellung von Ihrer SharePoint Online-Ressourcen für alle Benutzer zu beschleunigen unabhängig davon, wo sich diese befinden oder wie sie Ihre Inhalte zugreifen.
ms.openlocfilehash: 958f01419a74e4b8cd007b2627585884496bdfdf
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540752"
---
# <a name="use-the-office-365-content-delivery-network-with-sharepoint-online"></a>Verwenden Sie die Office 365 Content Delivery Networks mit SharePoint Online

Sie können statische Objekte in der Office 365 Content Delivery Network (CDN) um bieten eine bessere Leistung für Ihre SharePoint Online-Seiten hosten. Statische Objekte sind Dateien, die oft wie Bilder, Video und Audio, Stylesheets, Schriftarten und JavaScript-Dateien nicht geändert. Das CDN fungiert als geografisch verteilten Zwischenspeichern Proxy, durch Zwischenspeichern statische Objekte näher an den Browsern, die diese anfordert. 
  
Wenn Sie bereits mit der Art und Weise vertraut, die CDNs arbeiten sind, müssen Sie nur einige Schritte ausführen, um es einrichten. In diesem Thema wird beschrieben, wie. Informieren Sie sich für Informationen über das Office 365 CDN und Entwicklersicht hosten Ihre statischen Ressourcen auf.
  
 **Head zurück an [netzwerkplanung und leistungsoptimierung für Office 365](https://aka.ms/tune).**
  
## <a name="office-365-cdn-basics"></a>Office 365 CDN-Grundlagen

Die Office 365-CDN ist Bestandteil Ihrer SharePoint Online-Abonnement. Sie müssen nicht sehr bezahlen. Office 365 bietet Unterstützung für beide sind privat und öffentlich und ermöglicht es Ihnen zu statischen Host-Objekte in mehreren Speicherorten oder Herkunft. Die Office 365-CDN ist nicht identisch mit dem Azure CDN. Wenn Sie weitere Informationen dazu, warum ein CDN verwenden oder allgemeine Konzepte von CDN benötigen, finden Sie unter [Inhaltsübermittlung](content-delivery-networks.md).
  
## <a name="how-the-cdn-grants-access-to-end-users"></a>Wie das CDN gewährt Zugriff auf die Endbenutzer

Privater Zugriff auf statische Objekte in der Office 365-CDN wird mithilfe von SharePoint Online generierte Token erteilt. Benutzer, die bereits über die Berechtigung zum Zugriff auf den Ordner oder die Bibliothek, die vom Ursprung werden automatisch Token erteilt werden. SharePoint Online unterstützt auf Elementebene keine Berechtigungen für das CDN.
  
Beispiel für eine Datei befindet sich unter `https://contoso.sharepoint.com/sites/site1/library1/folder1/image1.jpg`, erhält die folgenden:
  
- Benutzer 1 hat Zugriff auf folder1 und image1.jpg
    
- 2 Benutzer hat keinen Zugriff auf folder1
    
- Benutzer 3 hat keinen Zugriff auf folder1, sondern wird gewährt ausdrückliche Zustimmung image1.jpg Zugriff auf über SharePoint Online
    
- 4 Benutzer über Zugriff auf folder1 jedoch wurde verweigert Zugriff auf image1.jpg explizit
    
Klicken Sie auf die Folgendes zutrifft:
  
- Benutzer 1 und 4 Benutzer werden können image1.jpg über das CDN zugegriffen.
    
- Benutzer 2 und 3 für Benutzer wird nicht über das CDN image1.jpg zugreifen können.
    
    Jedoch können Benutzer 3 weiterhin zugreifen die Anlage image1.jpg direkt über SharePoint Online während Benutzer 4 die Anlage nicht über SharePoint Online zugreifen können.
    
## <a name="overview-of-working-with-the-office-365-cdn"></a>Übersicht über das Arbeiten mit dem Office 365 CDN

Um das Office 365 CDN einzurichten, führen Sie die folgenden grundlegenden Schritte aus:
  
- Planen der CDN-Bereitstellung:
    
  - Bestimmen Sie die statischen Anlagen, die Sie auf der Office 365-CDN hosten möchten. Ausführliche Informationen dazu, wie Sie diese Auswahlmöglichkeiten zur Verfügung stellen können finden Sie [die Inhaltsübermittlung](content-delivery-networks.md).
    
  - [Bestimmen Sie, wo Sie Ihre Anlagen speichern möchten](use-office-365-cdn-with-spo.md#CDNStoreAssets). Diesen Speicherort ist ein Ordner oder SharePoint-Bibliothek und einen Ursprung aufgerufen.
    
  - Bestimmen Sie, ob die Anlagen vertraulich oder veröffentlicht werden soll. Sie dieses Vorgehen, wenn Sie [auswählen, ob jede Origin öffentlich oder privat sein soll](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate). Wenn Sie möchten, können Sie mehrere Herkunft, in denen einige öffentlich sind, und sind einige privat.
    
- [Festlegen einrichten und Konfigurieren der Office 365-CDN mithilfe von SharePoint Online-Verwaltungsshell](use-office-365-cdn-with-spo.md#CDNSetupinPShell). Wenn Sie diesen Schritt abgeschlossen haben, müssen Sie:
    
  - Aktiviert das CDN für Ihre Organisation.
    
  - Ihre Herkunft hinzugefügt. Sie identifizieren jede Ursprung als öffentliche oder private.
    
Einmal fertig sind Sie mit dem Setup, [Verwalten der Office 365-CDN](use-office-365-cdn-with-spo.md#CDNManage) über einen Zeitraum von: 
  
- Hinzufügen, aktualisieren und Entfernen von Anlagen
    
- Hinzufügen und Entfernen von Herkunft
    
- Konfigurieren von CDN-Richtlinien
    
- Falls erforderlich, das Office 365 CDN deaktivieren
    
## <a name="determine-where-you-want-to-store-your-assets"></a>Bestimmen Sie, wo Sie Ihre Anlagen speichern möchten

Das CDN ruft Ihre Anlagen von einem Speicherort, der einen Ursprung aufgerufen. Für Office 365 ist ein Ursprung an eine SharePoint-Bibliothek oder einen Ordner, die über eine URL zugegriffen werden kann. Wenn Sie für Ihre Organisation Herkunft angeben, stehen Ihnen sehr flexibel. Beispielsweise können Sie angeben, mehrere Herkunft oder einen einzelnen Ursprung, in dem alle CDN Anlagen erstellt werden sollen. Sie können auswählen, öffentlichen oder privaten Herkunft für Ihre Organisation haben. Die meisten Organisationen werden auch eine Kombination aus beidem implementiert.
  
Wenn Sie Hunderte von Herkunft definieren, wird es wahrscheinlich sich negativ auf dem Zeitpunkt der haben, die benötigt wird, um Anforderungen zu verarbeiten. Es wird empfohlen, wenn Sie über mehr als 100 Herkunft verfügen Sie möglicherweise überdenken Ihre Architektur.
  
## <a name="choose-whether-each-origin-should-be-public-or-private"></a>Wählen Sie, ob jede Origin öffentlichen oder privaten werden sollen

Wenn Sie einen Ursprung identifiziert haben, geben Sie an, ob es öffentlichen oder privaten hergestellt werden soll. Unabhängig davon welche Option Sie wählen, wird von Microsoft den schwierigsten für Sie bei der Verwaltung von dem CDN selbst. Darüber hinaus können Sie Ihre Meinung später ändern, nachdem Sie dem CDN einrichten und Ihre Herkunft identifiziert haben.
  
Optionen für öffentliche und private Performance, aber jeder besitzt eindeutige Attribute und Vorteile.
  
 **Attribute und Vorteile der Objekte in einem öffentlichen Origin-hosting**
  
- Objekte in einem öffentlichen Origin verfügbar gemacht werden anonym von allen Benutzern zugegriffen werden.
    
    > [!IMPORTANT]
    > Wenn Sie einen öffentlichen Ursprung in Ihrer CDN identifiziert haben, sollten Sie Ressourcen, die in einem öffentlichen Ursprung oder SharePoint Online-Bibliothek Beachtung von Ihrer Organisation berücksichtigt werden nie platzieren. 
  
- Wenn Sie eine Anlage aus einer öffentlichen Origin entfernen möchten, kann die Anlage weiterhin für bis zu 30 Tagen aus dem Cache verfügbar sein; Es werden jedoch Links auf die Anlage in dem CDN innerhalb von 15 Minuten ungültig.
    
- Wenn Sie Stylesheets (CSS-Dateien) in einem öffentlichen Origin hosten, können Sie relative Pfade und URIs im Code verwenden. Dies bedeutet, dass Sie den Speicherort der Hintergrundbilder und andere Objekte relativ zum Speicherort der Anlage, die sie anrufen, verweisen können.
    
- Während Sie einen öffentlichen Ursprung URL codieren können, wird dadurch also nicht empfohlen. Der Grund hierfür ist, wenn der Zugriff auf das CDN nicht mehr verfügbar ist, wird die URL nicht automatisch in Ihrer Organisation in SharePoint Online aufgelöst wird und möglicherweise beschädigte Verknüpfungen und andere Fehler.
    
- Die Standard-Dateitypen, die für Öffentliche Herkunft enthalten sind sind CSS, .eot, GIF, ICO, JPEG, JPG, js, .map, PNG, SVG, ttf und .woff. Sie können zusätzliche Dateitypen angeben.
    
- Wenn Sie möchten, können Sie eine Richtlinie zum Ausschließen von Anlagen, die von Klassifikationen in der Website identifiziert wurden, die Sie angeben konfigurieren. Sie können beispielsweise alle Anlagen auszuschließen, die als "confidential" oder "eingeschränkt" gekennzeichnet sind, selbst wenn sie einen zulässigen Dateityp sind und sich in einem öffentlichen Ursprung befinden.
    
 **Attribute und Vorteile der Objekte in einem privaten Origin-hosting**
  
- Benutzer können nur die Objekte aus einer privaten Origin zugreifen, wenn sie dazu autorisiert sind. Anonymer Zugriff auf diese Ressourcen wird verhindert.
    
- Wenn Sie eine Anlage vom Ursprung private entfernen, kann die Anlage weiterhin für bis zu einer Stunde aus dem Cache zur Verfügung; Es werden jedoch Links auf die Anlage in dem CDN innerhalb von 15 Minuten ungültig.
    
- Die Standard-Dateitypen, die für private Herkunft enthalten sind sind GIF, ICO, JPEG, JPG, js und PNG. Sie können zusätzliche Dateitypen angeben.
    
- Genau wie öffentliche Herkunft können Sie eine Richtlinie zum Ausschließen von Anlagen, die von Klassifikationen in der Website, die Sie angeben identifiziert wurden, auch wenn Sie Platzhalter verwenden, um alle Ressourcen innerhalb eines Ordners oder einer Website Bibliothek enthalten konfigurieren.
    
## <a name="default-office-365-cdn-origins"></a>Office 365 CDN-Herkunft Standard

Sofern nicht anders angegeben, richtet Office 365 einige Herkunft Standard für Sie, wenn Sie das Office 365 CDN aktivieren. Wenn Sie zunächst diese ausschließen, können Sie diese Herkunft hinzufügen, nach Abschluss der Installation.
  
Private Herkunft Standard:
  
- \*/userphoto.aspx
    
- \*/SiteAssets
    
Standardmäßige öffentliche Herkunft:
  
- \*/MasterPage
    
- \*Pfad/Style library
    
## <a name="set-up-and-configure-the-office-365-cdn-by-using-the-sharepoint-online-management-shell"></a>Richten Sie ein und konfigurieren Sie der Office 365-CDN mithilfe von SharePoint Online-Verwaltungsshell

Die Verfahren in diesem Thema müssen Sie die SharePoint Online-Verwaltungsshell verwenden, um mit SharePoint Online herstellen. Anweisungen finden Sie unter [Connect to SharePoint Online-PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).
  
Führen Sie diese Schritte zum Einrichten und Konfigurieren der Office 365 CDN zum Hosten Ihre statischen Daten in SharePoint Online.
  
### <a name="to-enable-your-organization-to-use-the-office-365-cdn"></a>So aktivieren Sie Ihre Organisation die Office 365-CDN verwenden

Verwenden Sie das Cmdlet " **Set-SPOTenantCdnEnabled** ", um Ihre Organisation mit dem Office 365 CDN aktivieren. Sie können Ihrer Organisation öffentliche Herkunft, private Herkunft oder beide mit dem CDN verwendet werden. Sie können auch die Office 365-CDN um überspringen die Einrichtung des Standard-Herkunft beim Aktivieren konfigurieren. Sie können diese Herkunft immer weiter unten in diesem Thema beschriebenen hinzufügen. 
  
In Windows Powershell für SharePoint Online:
  
```
Set-SPOTenantCdnEnabled -CdnType <Public | Private | Both> -Enable $true
```

Angenommen, um Ihrer Organisation zur Verwendung von öffentlichen und privaten Herkunft mit dem CDN zu aktivieren, geben Sie den folgenden Befehl ein:
  
```
Set-SPOTenantCdnEnabled -CdnType Both -Enable $true
```

Zum Aktivieren Ihrer Organisation verwenden, öffentliche und private Herkunft mit dem CDN jedoch die Einrichtung der Standard-Herkunft überspringen Geben Sie den folgenden Befehl ein:
  
```
Set-SPOTenantCdnEnabled -CdnType Both -Enable $true -NoDefaultOrigins
```

Um Ihrer Organisation zur Verwendung von öffentlichen Herkunft mit dem CDN zu aktivieren, geben Sie den folgenden Befehl ein:
  
```
Set-SPOTenantCdnEnabled -CdnType Public -Enable $true
```

Um Ihrer Organisation zur Verwendung von privaten Herkunft mit dem CDN zu aktivieren, geben Sie den folgenden Befehl ein:
  
```
Set-SPOTenantCdnEnabled -CdnType Private -Enable $true
```

Weitere Informationen zu diesem Cmdlet finden Sie unter [Set-SPOTenantCdnEnabled](https://technet.microsoft.com/en-us/library/mt790765.aspx).
  
### <a name="optional-to-change-the-list-of-file-types-to-include-in-the-office-365-cdn"></a>(Optional) So ändern Sie die Liste der Dateitypen, die in der Office 365-CDN einschließen
<a name="Office365CDNforSPOFileType"> </a>

> [!TIP]
> Wenn Sie mit dem Cmdlet **Set-SPOTenantCdnPolicy** Dateitypen definieren, überschreiben Sie die Liste der aktuell definierte. Wenn Sie zusätzliche Dateitypen der Liste hinzufügen möchten, verwenden Sie das Cmdlet zuerst um herauszufinden, was Dateitypen sind bereits zulässig, und nehmen sie in der Liste zusammen mit Ihrem neue. 
  
Verwenden Sie das Cmdlet **Set-SPOTenantCdnPolicy** statische Dateitypen definieren, die öffentliche und private Herkunft in dem CDN gehostet werden können. Standardmäßig werden allgemeine Anlagentypen für Beispiel CSS, GIF, JPG und js zulässig. 
  
In Windows PowerShell für SharePoint Online:
  
```
Set-SPOTenantCdnPolicy -CdnType <Public | Private> -PolicyType IncludeFileExtensions -PolicyValue "<Comma-separated list of file types >"
```

Um herauszufinden, welche Dateitypen nach dem CDN derzeit zulässig sind, verwenden Sie das Cmdlet **Get-SPOTenantCdnPolicies** : 
  
```
Get-SPOTenantCdnPolicies -CdnType <Public | Private>
```

Weitere Informationen zu diesen Cmdlets finden Sie unter [Set-SPOTenantCdnPolicy](https://technet.microsoft.com/en-us/library/mt800839.aspx) und [Get-SPOTenantCdnPolicies](https://technet.microsoft.com/en-us/library/mt800838.aspx).
  
### <a name="optional-to-change-the-list-of-site-classifications-you-want-to-exclude-from-the-office-365-cdn"></a>(Optional) So ändern Sie die Liste der Klassifikationen in der Website, den Sie aus dem Office 365 CDN ausschließen möchten
<a name="Office365CDNforSPOSiteClassification"> </a>

> [!TIP]
> Wenn Sie Klassifikationen in der Website mithilfe des Cmdlets **Set-SPOTenantCdnPolicy** ausschließen, überschreiben Sie die Liste der aktuell definierte. Wenn Sie zusätzliche Site Klassifikationen ausschließen möchten, verwenden Sie das Cmdlet zuerst erfahren Sie, welche Klassifikationen bereits ausgeschlossen werden, und klicken Sie dann zusammen mit Ihrem neue hinzufügen. 
  
Verwenden Sie das Cmdlet **Set-SPOTenantCdnPolicy** auszuschließende Klassifikationen in der Website, die nicht über das CDN zur Verfügung stellen möchten. Standardmäßig werden keine Klassifikationen in der Website ausgeschlossen. 
  
In Windows PowerShell für SharePoint Online:
  
```
Set-SPOTenantCdnPolicy -CdnType <Public | Private> -PolicyType ExcludeRestrictedSiteClassifications  -PolicyValue "<Comma-separated list of site classifications >"
```

Um herauszufinden, welche Klassifikationen in der Website zurzeit eingeschränkt sind, verwenden Sie das Cmdlet **Get-SPOTenantCdnPolicies** : 
  
```
Get-SPOTenantCdnPolicies -CdnType <Public | Private>
```

Weitere Informationen zu diesen Cmdlets finden Sie unter [Set-SPOTenantCdnPolicy](https://technet.microsoft.com/en-us/library/mt800839.aspx) und [Get-SPOTenantCdnPolicies](https://technet.microsoft.com/en-us/library/mt800838.aspx).
  
### <a name="to-add-an-origin-for-your-assets"></a>So fügen Sie einen Ursprung für Ihre Anlagen hinzu
<a name="Office365CDNforSPOOrigin"> </a>

Verwenden Sie das Cmdlet **Add-SPOTenantCdnOrigin** , um einen Ursprung definieren. Sie können mehrere Herkunft definieren. Der Ursprung ist eine URL, die verweist auf eine SharePoint-Bibliothek oder einen Ordner, der die Anlagen enthält, die das dem CDN gehostet werden soll. 
  
> [!IMPORTANT]
> Wenn Sie einen öffentlichen Ursprung in Ihrer CDN identifiziert haben, sollten Sie Ressourcen, die in den öffentlichen Ursprung oder SharePoint Online-Bibliothek Beachtung von Ihrer Organisation berücksichtigt werden nie platzieren. 
  
```
Add-SPOTenantCdnOrigin -CdnType <Public | Private> -OriginUrl <path >
```

Dabei ist Pfad der Pfad zu dem Ordner, der die Anlagen enthält. Sie können Platzhalter zusätzlich relative Pfade zu verwenden. Beispielsweise alle Anlagen in der Masterpages-Ordner für alle Ihre Websites als einen öffentlichen Ursprung innerhalb der CDN aufnehmen möchten, geben Sie den folgenden Befehl ein:
  
```
Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
```

Weitere Informationen zu diesem Befehl und die Syntax finden Sie unter [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).
  
Nachdem Sie den Befehl ausgeführt haben, synchronisiert das System die Konfiguration über das Rechenzentrum hinweg. Dadurch gelangen 15 Minuten.
  
### <a name="example-configure-a-public-origin-for-your-master-pages-and-for-your-style-library-for-sharepoint-online"></a>Beispiel: Konfigurieren einer öffentlichen Origin für Ihre Gestaltungsvorlagen und für die Formatbibliothek für SharePoint Online
<a name="ExamplePublicOrigin"> </a>

In der Regel sind diesen Herkunft eingerichtet Sie standardmäßig Wenn Sie für die Office 365-CDN öffentliche Herkunft aktivieren. Jedoch, wenn Sie diese manuell aktivieren möchten, gehen Sie folgendermaßen vor.
  
- Verwenden Sie das Cmdlet **Add-SPOTenantCdnOrigin** , um die Formatbibliothek als einen öffentlichen Ursprung innerhalb der Office 365-CDN definieren. 
    
  ```
  Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */style%20library
  ```

- Verwenden Sie das Cmdlet **Add-SPOTenantCdnOrigin** , um die Masterseiten als einen öffentlichen Ursprung innerhalb der Office 365-CDN definieren. 
    
  ```
  Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
  ```

- Weitere Informationen zu diesem Befehl und die Syntax finden Sie unter [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).
    
    Nachdem Sie den Befehl ausgeführt haben, synchronisiert das System die Konfiguration über das Rechenzentrum hinweg. Dadurch gelangen 15 Minuten.
    
### <a name="example-configure-a-private-origin-for-your-site-assets-site-pages-and-publishing-images-for-sharepoint-online"></a>Beispiel: Konfigurieren einer privaten Origin für Ihre Website-Objekten, Websiteseiten und veröffentlichte Bilder für SharePoint Online
<a name="ExamplePrivateOrigin"> </a>

- Verwenden Sie das Cmdlet **Add-SPOTenantCdnOrigin** , um Anlagen-Ordner der Website als eine private Ursprung innerhalb der Office 365-CDN definieren. 
    
  ```
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */siteassets
  ```

- Verwenden Sie das Cmdlet **Add-SPOTenantCdnOrigin** , um den Ordner der Website-Seiten als einen privaten Ursprung innerhalb der Office 365-CDN definieren. 
    
  ```
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */sitepages
  ```

- Verwenden Sie das Cmdlet **Add-SPOTenantCdnOrigin** um publishing Ordner Images als einen privaten Ursprung innerhalb der Office 365-CDN definieren. 
    
  ```
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */publishingimages
  ```

    Weitere Informationen zu diesem Befehl und die Syntax finden Sie unter [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).
    
    Nachdem Sie den Befehl ausgeführt haben, synchronisiert das System die Konfiguration über das Rechenzentrum hinweg. Dadurch gelangen 15 Minuten.
    
### <a name="example-configure-a-private-origin-for-a-site-collection-for-sharepoint-online"></a>Beispiel: Konfigurieren einer privaten Origin für eine Websitesammlung für SharePoint Online
<a name="ExamplePrivateOriginSiteCollection"> </a>

Verwenden Sie das Cmdlet **Add-SPOTenantCdnOrigin** , um eine Websitesammlung als einen privaten Ursprung innerhalb der Office 365-CDN definieren. Zum Beispiel 
  
```
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl sites/site1/siteassets
```

Weitere Informationen zu diesem Befehl und die Syntax finden Sie unter [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).
  
Nachdem Sie den Befehl ausgeführt haben, synchronisiert das System die Konfiguration über das Rechenzentrum hinweg. Dadurch gelangen 15 Minuten.
  
## <a name="manage-the-office-365-cdn"></a>Verwalten von Office 365 CDN
<a name="CDNManage"> </a>

Nach dem CDN eingerichtet haben, können Sie Ihre Konfiguration ändern wie Inhalte zu aktualisieren oder Ihre Bedürfnisse anpassen, wie in diesem Abschnitt beschrieben.
  
### <a name="to-add-update-or-remove-assets-from-the-office-365-cdn"></a>Hinzufügen, aktualisieren oder Entfernen von Anlagen aus dem Office 365 CDN
<a name="Office365CDNforSPOaddremoveasset"> </a>

Nachdem Sie die Setupschritte abgeschlossen haben, können Sie hinzufügen neue Anlagen und aktualisieren oder entfernen vorhandene Ressourcen, wenn Sie möchten. Stellen Sie nur die Änderungen auf Elemente in den Ordner oder die SharePoint-Bibliothek, die Sie als einen Ursprung identifiziert. Wenn Sie eine neue Anlage hinzufügen, wird es sofort über das CDN verfügbar. Jedoch, wenn Sie die Anlage aktualisieren, dauert es bis zu 15 Minuten für die neue Kopie verbreiten und in dem CDN zur Verfügung stehen.
  
Wenn Sie den Speicherort des Ursprungs abrufen möchten, können Sie das Cmdlet **Get-SPOTenantCdnOrigins** verwenden. Informationen zum Verwenden dieses Cmdlet finden Sie unter [Get-SPOTenantCdnOrigins](https://technet.microsoft.com/en-us/library/mt790770.aspx).
  
### <a name="to-remove-an-origin-from-the-office-365-cdn"></a>So entfernen einen Ursprung aus dem Office 365 CDN
<a name="Office365CDNforSPORemoveOrigin"> </a>

Wenn Sie möchten, können Sie Zugriff auf einen Ordner oder SharePoint-Bibliothek, die Sie als einen Ursprung identifiziert entfernen. Verwenden Sie hierzu das Cmdlet **Remove-SPOTenantCdnOrigin** . Informationen zum Verwenden dieses Cmdlet finden Sie unter [Remove-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790761.aspx).
  
### <a name="to-modify-an-origin-in-the-office-365-cdn"></a>So ändern Sie einen Ursprung in der Office 365-CDN
<a name="Office365CDNforSPORemoveOrigin"> </a>

Die von den Ihnen erstellten können nicht Ursprung geändert werden. Stattdessen entfernen Sie Ursprung zu, und fügen Sie einen neuen Anwendungspool. Weitere Informationen finden Sie unter [Ursprung aus dem Office 365 CDN entfernen](use-office-365-cdn-with-spo.md#Office365CDNforSPORemoveOrigin) und [einen Ursprung für Ihre Anlagen hinzuzufügen](use-office-365-cdn-with-spo.md#Office365CDNforSPOOrigin).
  
### <a name="to-disable-the-office-365-cdn"></a>So deaktivieren Sie das Office 365 CDN
<a name="Office365CDNforSPODisable"> </a>

Verwenden Sie das **Set-SPOTenantCdnEnabled** -Cmdlet, um dem CDN für Ihre Organisation zu deaktivieren. Wenn Sie sowohl die öffentliche und private Herkunft für das CDN aktiviert haben, müssen Sie das Cmdlet zweimal, wie in den folgenden Beispielen gezeigt ausführen. 
  
Geben Sie den folgenden Befehl, um die Verwendung von öffentlichen Herkunft in der CDN in Windows Powershell für SharePoint Online zu deaktivieren:
  
```
Set-SPOTenantCdnEnabled -CdnType Public -Enable $false
```

Geben Sie den folgenden Befehl, um die Verwendung von der privaten Herkunft in dem CDN zu deaktivieren:
  
```
Set-SPOTenantCdnEnabled -CdnType Private -Enable $false
```

Weitere Informationen zu diesem Cmdlet finden Sie unter [Set-SPOTenantCdnEnabled](https://technet.microsoft.com/en-us/library/mt790765.aspx).
  
## <a name="troubleshooting-your-office-365-cdn-configuration"></a>Problembehandlung bei der Office 365 CDN-Konfiguration
<a name="CDNManage"> </a>

Der Endpunkt werden sofort einsatzbereit, nicht wie es Zeit für die Registrierung über das CDN weitergegeben. Konfiguration nimmt 15 Minuten.
  

