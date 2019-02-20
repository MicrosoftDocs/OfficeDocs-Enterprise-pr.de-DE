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
ms.collection:
- Ent_O365
- M365-subscription-management
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: b48cdf63-07e0-4cda-8c12-4871590f59ce
description: 'Zusammenfassung: Beschreibung der SSL-Zertifikate, die für lokale und hybride Exchange-Bereitstellungen, Einmaliges Anmelden mit AD FS, Exchange Online-Dienste und Exchange-Webdienste benötigt werden.'
ms.openlocfilehash: 3c22daa2315e36c45b5b5dd6271842168c90726d
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085324"
---
# <a name="plan-for-third-party-ssl-certificates-for-office-365"></a>Planen von Drittanbieter-SSL-Zertifikaten für Office 365

 **Zusammenfassung:** Beschreibt die SSL-Zertifikate, die für Exchange lokal und Hybrid, SSO mit AD FS, Exchange Online Services und Exchange-webDiensten erforderlich sind. 
  
Zum Verschlüsseln der Kommunikation zwischen ihren Clients und der Office 365-Umgebung müssen SSL-Zertifikate (Secure Socket Layer) von Drittanbietern auf Ihren Infrastrukturservern installiert sein.

||
|:-----|
| Dieser Artikel ist Teil der [Netzwerkplanung und Leistungsoptimierung für Office 365](https://aka.ms/tune).|
   
Zertifikate werden für die folgenden Office 365-Komponenten benötigt:
  
- Lokale Exchange-Organisation
    
- Einmaliges Anmelden (SSO) (bei den Verbundservern der Active Directory-Verbunddienste (AD FS) und bei den Verbundserverproxys der AD FS)
    
- Exchange Online-Dienste wie AutoErmittlung, Outlook Anywhere und Exchange-webDienste
    
- Hybrider Exchange-Server
    
## <a name="certificates-for-exchange-on-premises"></a>Zertifikate für die lokale Exchange-Organisation

Eine Übersicht über die Verwendung digitaler Zertifikate für die Kommunikation zwischen der lokalen Exchange-Organisation und Exchange Online Secure finden Sie im TechNet-Artikel [understandIng Certificate Requirements](https://go.microsoft.com/fwlink/p/?LinkID=243657).
  
## <a name="certificates-for-single-sign-on"></a>Zertifikate für einmaliges Anmelden (SSO)

Um Ihren Benutzern eine vereinfachte Single Sign-on-Erfahrung mit robuster Sicherheit bereitzustellen, sind die in der folgenden Tabelle aufgeführten Zertifikate auf den Verbundservern oder den Verbundserverproxys erforderlich. In der folgenden Tabelle werden die Active Directory-Verbunddienste (AD FS) behandelt, weitere Informationen zur [Verwendung von Drittanbieter-Identitätsanbietern](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-fed-compatibility).
  
||||
|:-----|:-----|:-----|
|**Zertifikattyp** <br/> |**Beschreibung** <br/> |**Was sollten Sie wissen, bevor Sie mit der Bereitstellung beginnen?** <br/> |
|**SSL-Zertifikat (auch Serverauthentifizierungszertifikat genannt)** <br/> |Dieses Standard-SSL-Zertifikat macht die Kommunikation zwischen Verbundservern, Clients und Verbundserverproxys sicher.  <br/> |AD FS erfordert ein SSL-Zertifikat. Standardmäßig verwendet AD FS das SSL-Zertifikat, das für die Standardwebsite in Internet Informationsdienste (IIS) konfiguriert ist.<br/> Der Antragstellername dieses SSL-Zertifikats wird verwendet, um den Verbunddienst Namen für jede AD FS-Instanz zu bestimmen, die Sie bereitstellen. Erwägen Sie die Auswahl eines Antragstellernamens für alle neuen Zertifizierungsstellenzertifikate, die am besten für den Namen Ihres Unternehmens oder Ihrer Organisation in Office 365 stehen. Dieser Name muss Internet routingfähig sein.<br/>**Achtung:** AD FS erfordert, dass dieses SSL-Zertifikat keinen punktlosen-Antragstellernamen (Short-Name) hat.          <br/> **Empfehlung:** Da dieses Zertifikat von Clients von AD FS als vertrauenswürdig eingestuft werden muss, wird empfohlen, ein SSL-Zertifikat zu verwenden, das von einer öffentlichen (Drittanbieter-) ZERTIFIZIERUNGsSTELLE oder von einer ZERTIFIZIERUNGsSTELLE ausgestellt wurde, die einem öffentlich vertrauenswürdigen Stamm untergeordnet ist. zum Beispiel VeriSign oder Thawte.  <br/> |
|**Tokensignaturzertifikat** <br/> |Hierbei handelt es sich um ein Standardmäßiges X. 509-Zertifikat, das für die sichere Signierung aller Token verwendet wird, die der Verbundserver ausstellt und die von Office 365 akzeptiert und validiert werden.  <br/> |Das Token-Signaturzertifikat muss einen privaten Schlüssel enthalten, der zu einem vertrauenswürdigen Stamm in der FS verkettet ist. Standardmäßig erstellt AD FS ein selbstsigniertes Zertifikat. Je nach den Anforderungen Ihrer Organisation können Sie dieses Zertifikat jedoch mithilfe des AD FS-Verwaltungs-Snap-Ins in ein Zertifikat von einer ZERTIFIZIERUNGsSTELLE ändern.<br/>**Achtung:** Das Token-Signaturzertifikat ist für die Stabilität der FS entscheidend. Wenn das Zertifikat geändert wird, muss Office 365 über die Änderung benachrichtigt werden. Wenn keine Benachrichtigung bereitgestellt wird, können sich Benutzer nicht bei Ihren Office 365-Dienst angeboten anmelden.<br/>**Empfehlung:** Es wird empfohlen, dass Sie das selbstsignierte Token signieren, das von AD FS generiert wird. Auf diese Weise verwaltet Sie dieses Zertifikat standardmäßig für Sie. Wenn dieses Zertifikat beispielsweise demnächst abläuft, generiert AD FS ein neues selbstsigniertes Zertifikat.<br/> |
   
Verbundserverproxys fordern dieses Zertifikat, das in der folgenden Tabelle beschrieben ist.
  
||||
|:-----|:-----|:-----|
|**Zertifikattyp** <br/> |**Beschreibung** <br/> |**Was sollten Sie wissen, bevor Sie mit der Bereitstellung beginnen?** <br/> |
|SSL-Zertifikat  <br/> |Dieses Standard-SSL-Zertifikat macht die Kommunikation zwischen Verbundservern, Verbundserverproxys und Internetclientcomputern sicher.  <br/> |Dieses SSL-Zertifikat muss an die Standardwebsite in IIS gebunden werden, bevor Sie den Konfigurations-Assistenten für den AD FS-Verbund Server Proxy ausführen können.  <br/> Dieses Zertifikat muss denselben Antragstellernamen wie das SSL-Zertifikat haben, das auf dem Verbundserver im Unternehmensnetzwerk konfiguriert wurde.  <br/> **Empfehlung:** Unsere Empfehlung lautet, dass Sie dasselbe Serverauthentifizierungszertifikat verwenden, das auf dem Verbundserver konfiguriert wurde, mit dem dieser Verbundserverproxy verbunden ist.  <br/> |
   
## <a name="certificates-for-autodiscover-outlook-anywhere-and-active-directory-synchronization"></a>Zertifikate für die AutoErmittlung, Outlook Anywhere und die Active Directory-Synchronisierung

Ihre externen Exchange 2013-, Exchange 2010-, Exchange 2007-und Exchange 2003-Client Zugriffsserver (CASs) erfordern ein SSL-Zertifikat eines Drittanbieters für sichere Verbindungen für AutoErmittlung, Outlook Anywhere und Active Directory-Synchronisierungsdienste. Möglicherweise ist dieses Zertifikat bereits in Ihrer lokalen Umgebung installiert.
  
## <a name="certificate-for-an-exchange-hybrid-server"></a>Zertifikat für einen Exchange-Hybridserver

Ihre externen Exchange-hybridserver oder-Server benötigen ein SSL-Zertifikat eines Drittanbieters für eine sichere Verbindung mit dem Exchange Online-Dienst. Sie müssen dieses Zertifikat von Ihrem Drittanbieter-SSL-Anbieter abrufen.
  
## <a name="office-365-certificate-chains"></a>Office 365-Zertifikatketten

In diesem Artikel werden die Zertifikate beschrieben, die Sie möglicherweise für Ihre Infrastruktur installieren müssen. Weitere Informationen zu den auf unseren Office 365-Servern installierten Zertifikaten finden Sie unter [office 365 Certificate Chains](https://support.office.com/article/0c03e6b3-e73f-4316-9e2b-bf4091ae96bb).
  

