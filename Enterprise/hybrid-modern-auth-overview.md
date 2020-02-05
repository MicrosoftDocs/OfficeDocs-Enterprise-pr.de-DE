---
title: Übersicht über die moderne Hybrid Authentifizierung und Voraussetzungen für die Verwendung mit lokalen Skype for Business und Exchange-Servern
ms.author: kvice
ms.reviewer: smithre4
author: kelleyvice-msft
manager: laurawi
ms.date: 12/17/2019
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.assetid: ef753b32-7251-4c9e-b442-1a5aec14e58d
ms.collection:
- M365-security-compliance
description: Die moderne Authentifizierung ist eine Methode zur Identitätsverwaltung, die eine sicherere Benutzerauthentifizierung und-Autorisierung bietet. Sie ist für hybridbereitstellungen von lokalen Skype for Business-Servern und lokalen Exchange-Servern sowie für geteilte Domänen Skype for Business Hybriden verfügbar. Dieser Artikel enthält Links zu verwandten Dokumenten zu Voraussetzungen, zur Einrichtung/Deaktivierung moderner Authentifizierung und zu einigen der verwandten Clients (ex. Outlook-und Skype-Clients) Informationen.
ms.openlocfilehash: 5124e42f5dff33d59083cc23f0c57349e6136fb9
ms.sourcegitcommit: 226989f5a6a252e67debf7613bf13aa679a43f92
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/04/2020
ms.locfileid: "41721916"
---
# <a name="hybrid-modern-authentication-overview-and-prerequisites-for-using-it-with-on-premises-skype-for-business-and-exchange-servers"></a>Übersicht über die moderne Hybrid Authentifizierung und Voraussetzungen für die Verwendung mit lokalen Skype for Business und Exchange-Servern

*Dieser Artikel gilt sowohl für Office 365 Enterprise als auch Microsoft 365 Enterprise*.

Die _moderne Authentifizierung_ ist eine Methode zur Identitätsverwaltung, die eine sicherere Benutzerauthentifizierung und-Autorisierung bietet. Sie ist für Office 365 hybridbereitstellungen von lokalen Skype for Business-Servern und lokalen Exchange-Servern sowie von Skype for Business Hybriden mit geteilten Domänen verfügbar. Dieser Artikel enthält Links zu verwandten Dokumenten zu Voraussetzungen, zur Einrichtung/Deaktivierung moderner Authentifizierung und zu einigen der verwandten Clients (ex. Outlook-und Skype-Clients) Informationen.
  
- [Was ist die moderne Authentifizierung?](hybrid-modern-auth-overview.md#BKMK_WhatisModAuth)
- [Was ändert sich, wenn ich die moderne Authentifizierung verwende?](hybrid-modern-auth-overview.md#BKMK_WhatChanges)
- [Überprüfen des modernen Authentifizierungsstatus Ihrer lokalen Umgebung](hybrid-modern-auth-overview.md#BKMK_CheckStatus)
- [Erfüllen Sie die Voraussetzungen für die moderne Authentifizierung?](#do-you-meet-modern-authentication-prerequisites)
- [Was muss ich noch wissen, bevor ich beginne?](hybrid-modern-auth-overview.md#BKMK_Whatelse)

## <a name="what-is-modern-authentication"></a>Was ist die moderne Authentifizierung?
<a name="BKMK_WhatisModAuth"> </a>

Die moderne Authentifizierung ist ein Oberbegriff für eine Kombination von Authentifizierungs-und Autorisierungsmethoden zwischen einem Client (beispielsweise Ihrem Laptop oder Ihrem Telefon) und einem Server sowie einigen Sicherheitsmaßnahmen, die auf Zugriffsrichtlinien beruhen, die Sie möglicherweise bereits vertraut mit. Sie umfasst Folgendes:
  
- **Authentifizierungsmethoden**: mehrstufige Authentifizierung (MFA); Smartcard-Authentifizierung; Clientzertifikat basierte Authentifizierung
- **Autorisierungsmethoden**: Microsoft-Implementierung der Open Authorization (OAuth)
- **Richtlinien für den bedingten Zugriff**: MAM (Mobile Application Management) und Azure Active Directory bedingter Zugriff

Durch die Verwaltung von Benutzeridentitäten mit moderner Authentifizierung können Administratoren viele verschiedene Tools verwenden, wenn es um die Sicherung von Ressourcen geht und um sicherere Methoden der Identitätsverwaltung für lokale (Exchange-und Skype for Business), Exchange-Hybrid-und Skype for Business-Hybrid-/Split-Domain-Szenarien zu bieten.
  
Beachten Sie, dass das Anmeldeverhalten Skype for Business Client Benutzern durch den modernen Authentifizierungsstatus von Exchange betroffen ist, da Skype for Business eng mit Exchange zusammenarbeitet. Dies gilt auch, wenn Sie über eine Skype for Business _geteilte Domänen-_ Hybrid Architektur verfügen, in der Sie sowohl Skype for Business Online als auch Skype for Business lokal haben und an beiden Standorten Benutzer verwaltet werden.

Weitere Informationen zur modernen Authentifizierung in Office 365 finden Sie unter [Office 365 Client App Support-modern Authentication](office-365-client-support-modern-authentication.md).
  
> [!IMPORTANT]
> Ab August 2017 werden für alle neuen Office 365 Mandanten, die Skype for Business Online und Exchange Online einschließen, standardmäßig die moderne Authentifizierung aktiviert. Bereits vorhandene Mandanten haben keine Änderung im Standard-MA-Zustand, aber alle neuen Mandanten unterstützen automatisch die erweiterte Gruppe von Identitätsfunktionen, die oben aufgeführt sind. Informationen zum Überprüfen des MA-Status finden Sie im Abschnitt [Überprüfen des modernen Authentifizierungsstatus in der lokalen Umgebung](hybrid-modern-auth-overview.md#BKMK_CheckStatus) .
  
## <a name="what-changes-when-i-use-modern-authentication"></a>Was ändert sich, wenn ich die moderne Authentifizierung verwende?
<a name="BKMK_WhatChanges"> </a>

Wenn Sie die moderne Authentifizierung mit lokalem Skype for Business oder Exchange Server verwenden, werden Benutzer weiterhin lokal *authentifiziert* , aber die Geschichte der *Autorisierung* Ihres Zugriffs auf Ressourcen (wie Dateien oder e-Mails) ändert sich. Aus diesem Grund wird bei der modernen Authentifizierung die Client-und Server Kommunikation durchgeführt, während die Schritte beim Konfigurieren von Ma dazu führen, dass evoSTS (ein Sicherheitstokendienst, der von Azure AD verwendet wird) als Authentifizierungsserver für Skype for Business und Exchange Server lokal festgelegt wird.
  
Durch die Änderung an evoSTS können Ihre lokalen Server die Vorteile von OAuth (Token Emission) zum Autorisieren ihrer Clients nutzen und ihre lokalen Sicherheitsmethoden in der Cloud (wie die mehrstufige Authentifizierung) auch gemeinsam nutzen. Darüber hinaus gibt das evoSTS Token aus, mit denen Benutzer Zugriff auf Ressourcen anfordern können, ohne Ihr Kennwort als Teil der Anforderung anzugeben. Unabhängig davon, wo Ihre Benutzer verwaltet werden (Online oder lokal), und unabhängig davon, an welchem Standort die erforderliche Ressource gehostet wird, wird EvoSTS zum Kern der Autorisierung von Benutzern und Clients werden, sobald die moderne Authentifizierung konfiguriert ist.
  
Wenn beispielsweise ein Skype for Business-Client auf Exchange Server zugreifen muss, um Kalenderinformationen im Namen eines Benutzers abzurufen, wird hierfür die Active Directory-Authentifizierungsbibliothek (Adal) verwendet. Adal ist eine Codebibliothek, mit der gesicherte Ressourcen in Ihrem Verzeichnis für Clientanwendungen mithilfe von OAuth-Sicherheitstoken verfügbar gemacht werden können. Adal arbeitet mit OAuth zusammen, um Ansprüche zu überprüfen und Token zu tauschen (statt Kennwörter), um einem Benutzer Zugriff auf eine Ressource zu gewähren. In der Vergangenheit war die Autorität in einer Transaktion wie diese – der Server, der weiß, wie benutzeransprüche überprüft werden und die erforderlichen Token ausgeben müssen – möglicherweise ein Sicherheitstokendienst lokal oder sogar Active Directory Verbunddienste. Die moderne Authentifizierung zentralisiert diese Autorität jedoch mithilfe von Azure Active Directory (AAD).
  
Dies bedeutet auch, dass, obwohl ihre Exchange Server-und Skype for Business-Umgebungen möglicherweise vollständig lokal sind, der autorisierungsserver Online ist und Ihre lokale Umgebung die Möglichkeit zum Erstellen und Verwalten einer Verbindung mit Ihrem Office haben muss. 365-Abonnement in der Cloud (und die Azure Active Directory Instanz, die Ihr Abonnement als Verzeichnis verwendet).
  
Was ändert sich nicht? Unabhängig davon, ob Sie sich in einer Hybrid Domäne mit geteilten Domänen befinden oder Skype for Business und Exchange Server lokal verwenden, müssen sich alle Benutzer zunächst *lokal*authentifizieren. In einer Hybrid Implementierung der modernen Authentifizierung deuten _Lyncdiscovery_ und _AutoDiscovery_ auf Ihren lokalen Server hin.
  
> [!IMPORTANT]
> Wenn Sie die spezifischen Skype for Business Topologien kennen müssen, die mit MA unterstützt werden, ist dies [hier dokumentiert](https://technet.microsoft.com/library/mt803262.aspx).
  
## <a name="check-the-modern-authentication-status-of-your-on-premises-environment"></a>Überprüfen des modernen Authentifizierungsstatus Ihrer lokalen Umgebung
<a name="BKMK_CheckStatus"> </a>

Da die moderne Authentifizierung den autorisierungsserver ändert, der verwendet wird, wenn Dienste OAuth/S2S nutzen, müssen Sie wissen, ob die moderne Authentifizierung für Ihre lokalen Skype for Business-und Exchange-Umgebungen aktiviert oder deaktiviert ist. Sie können den Status auf Ihren Exchange-Servern überprüfen, indem Sie den folgenden PowerShell-Befehl ausführen:

```powershell
Get-OrganizationConfig | ft OAuth*
```

Wenn der Wert der _OAuth2ClientProfileEnabled_ -Eigenschaft auf **false festgelegt**ist, wird die moderne Authentifizierung deaktiviert.

Weitere Informationen zum Get-OrganizationConfig-Cmdlet finden Sie unter [Get-OrganizationConfig](https://docs.microsoft.com/powershell/module/exchange/organization/get-organizationconfig).

Sie können Ihre Skype for Business Server überprüfen, indem Sie den folgenden PowerShell-Befehl ausführen:

```powershell
Get-CSOAuthConfiguration
```

Wenn der Befehl eine leere _OAuthServers_ -Eigenschaft zurückgibt oder wenn der Wert der _ClientADALAuthOverride_ -Eigenschaft nicht **zulässig**ist, wird die moderne Authentifizierung deaktiviert.

Weitere Informationen zum Get-csoauthconfiguration "-Cmdlet finden Sie unter [Get-csoauthconfiguration"](https://docs.microsoft.com/powershell/module/skype/get-csoauthconfiguration).
  
## <a name="do-you-meet-modern-authentication-prerequisites"></a>Erfüllen Sie die Voraussetzungen für die moderne Authentifizierung?

Überprüfen und überprüfen Sie diese Elemente aus der Liste, bevor Sie fortfahren:
  
- **Skype for Business spezifisch**
  - Für alle Server muss 2017 Kumulatives Update (CU5) für Skype for Business Server 2015 oder höher vorhanden sein.
    - **Ausnahme** -Survivable Branch Appliance (SBA) kann in der aktuellen Version (basierend auf lync 2013) sein
  - Ihre SIP-Domäne wird in Office 365 als Verbunddomäne hinzugefügt.
  - Alle SFB-Front-Ends müssen über ausgehende Verbindungen mit dem Internet, zum Office 365 von Authentifizierungs-URLs (TCP 443) und bekannten Zertifikatstamm CRLs (TCP 80) verfügen, die in den Zeilen 56 und 125 des Abschnitts "Microsoft 365 Common and Office" in [Office 365-URLs und IP-Adressbereichen](urls-and-ip-address-ranges.md)aufgeführt sind.
  
- **Skype for Business lokal in einer hybriden Office 365 Umgebung**
  - Eine Skype for Business Server 2019-Bereitstellung mit allen Servern, auf denen Skype for Business Server 2019 läuft.
  - Eine Skype for Business Server 2015 Bereitstellung mit allen Servern, auf denen Skype for Business Server 2015 läuft.
  - Eine Bereitstellung mit maximal zwei unterschiedlichen Server Versionen, wie unten aufgeführt:
    - Skype for Business Server 2015
    - Skype for Business Server 2019
  - Auf allen Skype for Business Servern müssen die neuesten kumulativen Updates installiert sein, weitere Informationen finden Sie unter [Skype for Business Server Updates](https://docs.microsoft.com/skypeforbusiness/sfb-server-updates) , um alle verfügbaren Updates zu finden und zu verwalten.
  - In der Hybridumgebung gibt es keine lync Server 2010 oder 2013.

>[!NOTE]
>Wenn Ihre Skype for Business-Front-End-Server einen Proxy Server für den Internet Zugriff verwenden, muss die IP-Adresse des Proxyservers und die verwendete Port Nummer im Abschnitt "Configuration" der Datei "Web. config" für jedes Front-End eingegeben werden.
  
- C:\Program Files\Skype for Business Server 2015 \ Components\Web-ticket\int\web.config
- C:\Program Files\Skype for Business Server 2015 \ Components\Web-ticket\ext\web.config

```xml
<configuration>
  <system.net>
    <defaultProxy>
      <proxy
        proxyaddress="https://192.168.100.60:8080"
        bypassonlocal="true" />
    </defaultProxy>
  </system.net>
</configuration>
```

> [!IMPORTANT]
> Achten Sie darauf, den RSS-Feed für [Office 365 URLs und IP-Adressbereiche](urls-and-ip-address-ranges.md) zu abonnieren, um mit den neuesten Auflistungen der erforderlichen URLs auf dem aktuellen Stand zu bleiben.
  
- **Exchange Server spezifisch**
  - Sie verwenden entweder Exchange Server 2013 ku19 und up, Exchange Server 2016 ku8 und up oder Exchange Server 2019 ku1 und hoch.
  - In der Umgebung gibt es keinen Exchange Server 2010.
  - Die SSL-Abladung ist nicht konfiguriert. SSL-Beendigung und erneute Verschlüsselung werden unterstützt.
  - Wenn Ihre Umgebung eine Proxy Serverinfrastruktur verwendet, damit Server eine Verbindung mit dem Internet herstellen können, müssen Sie sicherstellen, dass auf allen Exchange-Servern der Proxy Server in der [para internetweb](https://technet.microsoft.com/library/bb123716%28v=exchg.160%29.aspx) -Eigenschaft definiert ist.
  
- **Exchange Server lokal in einer hybriden Office 365 Umgebung**

  - Wenn Sie Exchange Server 2013 verwenden, muss mindestens ein Server die Postfach-und Client Zugriffs-Serverrollen installiert haben. Es ist zwar möglich, die Postfachserver-und Client Zugriffsrollen auf separaten Servern zu installieren, es wird jedoch dringend empfohlen, beide Rollen auf demselben Server zu installieren, um zusätzliche Zuverlässigkeit und höhere Leistung zu gewährleisten.
  - Wenn Sie Exchange Server 2016 oder eine höhere Version verwenden, muss mindestens ein Server die Postfachserverrolle installiert haben.
  - In der Hybrid Umgebung gibt es keine Exchange-Server 2007 oder 2010.
  - Auf allen Exchange-Servern müssen die neuesten kummulative-Updates installiert sein, siehe [Upgrade von Exchange auf die neuesten kumulativen Updates](https://docs.microsoft.com/exchange/plan-and-deploy/install-cumulative-updates?view=exchserver-2019) , um alle verfügbaren Updates zu finden und zu verwalten.

- **Exchange-Client-und Protokollanforderungen**
  
  - Die folgenden Clients unterstützen die moderne Authentifizierung:

  |**Clients**|**Primäres Protokoll**|**Hinweise**|
  |:-----|:-----|:-----|
  |Outlook 2013 und Outlook 2016  <br/> |MAPI über HTTP  <br/> |MAPI über HTTP muss in Exchange aktiviert sein, damit die moderne Authentifizierung mit diesen Clients (in der Regel aktiviert oder true für neue Installationen von Exchange 2013 Service Pack 1 und höher) genutzt werden kann. Weitere Informationen finden Sie unter [Funktionsweise der modernen Authentifizierung für Office 2013-und Office 2016-Client-apps](https://docs.microsoft.com/office365/enterprise/modern-auth-for-office-2013-and-2016).  <br/> Stellen Sie sicher, dass Sie den minimal erforderlichen Build von Outlook durchführen. Informationen [zu den neuesten Updates für Outlook-Versionen, die Windows Installer (MSI) verwenden](https://docs.microsoft.com/officeupdates/outlook-updates-msi).  <br/> |
  |Outlook 2016 für Mac  <br/> |Exchange-Webdienste  <br/> |  <br/> |
  |Outlook für iOS und Android  <br/> |  <br/> |Weitere Informationen finden Sie unter [Verwenden der modernen Hybrid Authentifizierung mit Outlook für IOS und Android](https://docs.microsoft.com/Exchange/clients/outlook-for-ios-and-android/use-hybrid-modern-auth) .  <br/> |
  |Exchange ActiveSync-Clients (beispielsweise iOS11 Mail)  <br/> |Exchange ActiveSync  <br/> |Für Exchange ActiveSync-Clients, die die moderne Authentifizierung unterstützen, müssen Sie das Profil neu erstellen, um von der Standardauthentifizierung zur modernen Authentifizierung zu wechseln.  <br/> |

- **Allgemeine Voraussetzungen**
  - Bei Verwendung von ADFS sollten Windows 2012 R2 ADFS 3,0 und höher für den Verbund vorhanden sein.
  - Ihre Identitäts Konfigurationen sind alle Typen, die von Aad Connect unterstützt werden (wie Kennworthash Synchronisierung, Pass-Through-Authentifizierung, von Office 365 unterstützte lokale STS).)
  - Sie haben Aad Connect konfiguriert und funktioniert für die Benutzerreplikation und-Synchronisierung.
  - Sie haben sichergestellt, dass die Hybrid Konfiguration mit dem Exchange Classic Hybrid Topology Mode zwischen Ihrer lokalen und Office 365 Umgebung konfiguriert ist. Offizielle Support-Anweisung für Exchange Hybrid Says: Sie müssen entweder aktuelle Cu oder aktuelle Cu-1 haben.
    > [!NOTE]
    > Die moderne Hybrid Authentifizierung wird mit dem [Hybrid-Agent](https://docs.microsoft.com/exchange/hybrid-deployment/hybrid-agent)nicht unterstützt.

  - Stellen Sie sicher, dass sowohl ein lokaler Testbenutzer als auch ein in Office 365 verwalteter Hybrid Testbenutzer sich beim Skype for Business-Desktop Client anmelden können (wenn Sie die moderne Authentifizierung mit Skype verwenden möchten) und Microsoft Outlook (wenn Sie die moderne Authentifizierung mit verwenden möchten. Exchange).

## <a name="what-else-do-i-need-to-know-before-i-begin"></a>Was muss ich noch wissen, bevor ich beginne?
<a name="BKMK_Whatelse"> </a>

- Alle Szenarien für lokale Server beinhalten die Einrichtung moderner Authentifizierung lokal (in der Tat, für Skype for Business eine Liste unterstützter Topologien vorhanden ist), sodass der für die Authentifizierung und Autorisierung zuständige Server in der Microsoft-Cloud liegt ( Aad-Sicherheitstokendienst mit dem Namen "evoSTS" und Aktualisieren von Azure Active Directory (AAD) zu den URLs oder Namespaces, die von der lokalen Installation von Skype for Business oder Exchange verwendet werden. Daher nehmen lokale Server eine Microsoft-Cloud-Abhängigkeit an. Die Durchführung dieser Aktion könnte als Konfigurieren von "hybrider Authentifizierung" betrachtet werden.
- Dieser Artikel enthält Links zu anderen, die Sie bei der Auswahl unterstützter moderner Authentifizierungs Topologien (nur für Skype for Business erforderlich) und in den Vorgehensweisen, in denen die Installationsschritte oder Schritte zum Deaktivieren der modernen Authentifizierung für lokale Exchange-Bereitstellung erläutert werden. und Skype for Business lokal. Favorite diese Seite in Ihrem Browser, wenn Sie eine Home-Base für die Verwendung der modernen Authentifizierung in Ihrer Server Umgebung benötigen.

## <a name="related-topics"></a>Verwandte Themen
<a name="BKMK_URLListforMA"> </a>

- [Vorgehensweise konfigurieren Exchange Server lokal für die Verwendung der modernen Authentifizierung](configure-exchange-server-for-hybrid-modern-authentication.md)
- [Skype for Business Topologien, die mit moderner Authentifizierung unterstützt werden](https://technet.microsoft.com/library/mt803262.aspx)
- [Vorgehensweise konfigurieren Skype for Business lokal für die Verwendung der modernen Authentifizierung](configure-skype-for-business-for-hybrid-modern-authentication.md)
- [Entfernen oder Deaktivieren der modernen Hybridauthentifizierung aus Skype for Business und Exchange](remove-or-disable-hybrid-modern-authentication-from-skype-for-business-and-excha.md)
