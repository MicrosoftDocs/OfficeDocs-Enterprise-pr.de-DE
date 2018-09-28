---
title: Planen von Drittanbieter-SSL-Zertifikaten für Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 10/24/2017
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
ms.assetid: b48cdf63-07e0-4cda-8c12-4871590f59ce
description: 'Zusammenfassung: Beschreibung der SSL-Zertifikate, die für lokale und hybride Exchange-Bereitstellungen, Einmaliges Anmelden mit AD FS, Exchange Online-Dienste und Exchange-Webdienste benötigt werden.'
ms.openlocfilehash: 82e37ebb058b8a6b4b618649bea31a4137897690
ms.sourcegitcommit: 82219b5f8038ae066405dfb7933c40bd1f598bd0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/14/2018
ms.locfileid: "23975213"
---
# <a name="plan-for-third-party-ssl-certificates-for-office-365"></a>Planen von Drittanbieter-SSL-Zertifikaten für Office 365

 **Zusammenfassung:** Beschreibt die SSL-Zertifikate erforderlich für lokale Exchange-Organisation und hybride SSO mit AD FS, Exchange Online-Dienste und Exchange-Webdienste. 
  
Zum Zwecke der Verschlüsselung der Kommunikation zwischen Ihren Clients und Menüschaltfläche 365Office 365-Umgebung müssen Drittanbieter-Secure Socket Layer (SSL) Zertifikate auf Ihren Infrastrukturservern installiert sein.

||
|:-----|
| Dieser Artikel ist Teil der [Planung von Netzwerk und zur leistungsoptimierung für Office 365](https://aka.ms/tune).|
   
Zertifikate werden für die folgenden Office 365-Komponenten benötigt:
  
- Lokale Exchange-Organisation
    
- Einmaliges Anmelden (SSO) (bei den Verbundservern der Active Directory-Verbunddienste (AD FS) und bei den Verbundserverproxys der AD FS)
    
- Exchange Online-Dienste, wie die AutoErmittlung, Outlook Anywhere und Exchange-Webdienste
    
- Hybrider Exchange-Server
    
## <a name="certificates-for-exchange-on-premises"></a>Zertifikate für die lokale Exchange-Organisation

Eine Übersicht über die Verwendung von digitaler Zertifikaten zum Erhöhen der Sicherheit der Kommunikation zwischen der lokalen Exchange-Organisation und Exchange Online finden im TechNet-Artikel [Grundlegendes zu Zertifikatanforderungen](https://go.microsoft.com/fwlink/p/?LinkID=243657).
  
## <a name="certificates-for-single-sign-on"></a>Zertifikate für einmaliges Anmelden (SSO)

Um Ihren Benutzern mit eine vereinfachte single Sign-on-Erfahrung bereitstellen bereitzustellen, die robusten Sicherheit aufweist, sind die in der folgenden Tabelle aufgeführten Zertifikate auf den Verbundservern oder den Verbundserverproxys erforderlich. In der folgenden Tabelle liegt der Schwerpunkt auf Active Directory-Verbunddienste (AD FS), wir auch weitere Informationen zur [Verwendung von Drittanbieter - Identitätsanbieter](https://go.microsoft.com/fwlink/?LinkId=532869).
  
||||
|:-----|:-----|:-----|
|**Zertifikattyp** <br/> |**Beschreibung** <br/> |**Was sollten Sie wissen, bevor Sie mit der Bereitstellung beginnen?** <br/> |
|**SSL-Zertifikat (auch Serverauthentifizierungszertifikat genannt)** <br/> |Dieses Standard-SSL-Zertifikat macht die Kommunikation zwischen Verbundservern, Clients und Verbundserverproxys sicher.  <br/> |AD FS ist ein SSL-Zertifikat erforderlich. Standardmäßig verwendet AD FS das SSL-Zertifikat, das konfiguriert ist, für die Standardwebsite in Internetinformationsdienste (Internet Information Services, IIS).<br/> Der Antragstellername des dieses SSL-Zertifikat wird der Name der Verbund-Dienst (FS) für jede Instanz von AD FS bestimmt, die Sie bereitstellen. Wählen Sie einen Antragstellernamen für alle neuen Zertifizierungsstelle (CA)-ausgestellte Zertifikate, die am besten den Namen Ihrer Firma oder Organisation zu Office 365 darstellt. Dieser Name muss routbare sein.<br/>**Vorsicht:** AD FS erfordert, dass dieses SSL-Zertifikat keinen Punkt (Kurzname) Antragstellernamen aufweisen.          <br/> **Empfehlung:** Da dieses Zertifikat vom Clients von AD FS als vertrauenswürdig sein muss, wird empfohlen, dass Sie ein SSL-Zertifikat von einer öffentlichen Zertifizierungsstelle (Drittanbieter) oder von einer Zertifizierungsstelle, die eine öffentlich vertrauenswürdigen Stammzertifizierungsstellen untergeordnet ist ausgestellt verwenden; beispielsweise VeriSign oder Thawte.  <br/> |
|**Tokensignaturzertifikat** <br/> |Dies ist ein standardmäßiges x. 509-Zertifikat, das verwendet wird, für die sichere Signierung aller Token, die der Verbundserver ausstellt und die Office 365 akzeptiert und validiert.  <br/> |Das Tokensignaturzertifikat muss einen privaten Schlüssel enthalten, der eine vertrauenswürdige Stammzertifizierungsstelle in der FS untergeordnet ist. AD FS erstellt standardmäßig ein selbstsigniertes Zertifikat. Jedoch können je nach den Anforderungen Ihrer Organisation, Sie dieses Zertifikat einer Zertifizierungsstelle ausgestellten Zertifikat ändern mithilfe der AD FS-Verwaltungs-Snap-in.<br/>**Vorsicht:** Das Tokensignaturzertifikat ist entscheidend für die Stabilität von der FS. Wenn das Zertifikat geändert wird, muss die Änderung Office 365 benachrichtigt werden. Wenn die Benachrichtigung nicht angegeben ist, können Benutzer auf ihre Office 365-Dienstangebote anmelden.<br/>**Empfehlung:** Es wird empfohlen, dass Sie selbstsignierte Tokensignaturzertifikat verwenden, die von AD FS generiert wird. Auf diese Weise wird er dieses Zertifikat für Sie standardmäßig verwaltet. Angenommen, wenn dieses Zertifikat ist der Testzeitraum AD FS ein neues selbstsigniertes Zertifikats generiert.<br/> |
   
Verbundserverproxys fordern dieses Zertifikat, das in der folgenden Tabelle beschrieben ist.
  
||||
|:-----|:-----|:-----|
|**Zertifikattyp** <br/> |**Beschreibung** <br/> |**Was sollten Sie wissen, bevor Sie mit der Bereitstellung beginnen?** <br/> |
|SSL-Zertifikat  <br/> |Dieses Standard-SSL-Zertifikat macht die Kommunikation zwischen Verbundservern, Verbundserverproxys und Internetclientcomputern sicher.  <br/> |Bevor Sie den AD FS Verbund Verbundserverproxy-Konfigurationsassistenten erfolgreich ausführen können, muss dieses SSL-Zertifikat an die Standardwebsite in IIS gebunden werden.  <br/> Dieses Zertifikat muss denselben Antragstellernamen wie das SSL-Zertifikat haben, das auf dem Verbundserver im Unternehmensnetzwerk konfiguriert wurde.  <br/> **Empfehlung:** Unsere Empfehlung lautet, dass Sie dasselbe Serverauthentifizierungszertifikat verwenden, das auf dem Verbundserver konfiguriert wurde, mit dem dieser Verbundserverproxy verbunden ist.  <br/> |
   
## <a name="certificates-for-autodiscover-outlook-anywhere-and-active-directory-synchronization"></a>Zertifikate für AutoErmittlung, Outlook Anywhere und Active Directory-Synchronisierung

Die externen Exchange 2013, Exchange 2010, Exchange 2007 und Exchange 2003 Client Access Server (CASs) ist ein Drittanbieter-SSL-Zertifikat für sichere Verbindungen für AutoErmittlung, Outlook Anywhere und Active Directory Synchronization Services erforderlich. Dieses Zertifikat in Ihrer lokalen Umgebung installiert möglicherweise bereits müssen.
  
## <a name="certificate-for-an-exchange-hybrid-server"></a>Zertifikat für einen Exchange-Hybridserver

Die externen hybride Exchange-Server oder Server ist ein Drittanbieter-SSL-Zertifikat für sichere Konnektivität mit dem Exchange Online-Dienst erforderlich. Sie müssen dieses Zertifikat von Ihrem Drittanbieter-SSL-Anbieter abzurufen.
  
## <a name="office-365-certificate-chains"></a>Office 365 Zertifikatketten

In diesem Artikel wird beschrieben, die Zertifikate, die Sie möglicherweise auf Ihrer Infrastruktur installieren müssen. Weitere Informationen über die Zertifikate auf unsere Office 365-Server installiert sind finden Sie unter [Office 365 Zertifikatketten](https://support.office.com/article/0c03e6b3-e73f-4316-9e2b-bf4091ae96bb).
  

