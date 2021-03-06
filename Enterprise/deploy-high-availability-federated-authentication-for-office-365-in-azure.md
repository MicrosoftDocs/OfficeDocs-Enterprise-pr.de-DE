---
title: "Bereitstellen der Verbundauthentifizierung mit Hochverfügbarkeit für Office 365 in Azure"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 10/3/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Hybrid
- Ent_O365_Top
ms.custom:
- apr17entnews
- DecEntMigration
- Strat_O365_Enterprise
- Ent_Solutions
ms.assetid: 34b1ab9c-814c-434d-8fd0-e5a82cd9bff6
description: "Zusammenfassung: Konfigurieren der Verbundauthentifizierung mit hoher Verfügbarkeit für Ihr Office 365-Abonnement in Microsoft Azure."
---

# Bereitstellen der Verbundauthentifizierung mit Hochverfügbarkeit für Office 365 in Azure

 **Zusammenfassung:** Konfigurieren der Verbundauthentifizierung mit hoher Verfügbarkeit für Ihr Office 365-Abonnement in Microsoft Azure.
  
Dieser Artikel enthält Links zu den schrittweisen Anleitungen für die Bereitstellung der Verbundauthentifizierung mit hoher Verfügbarkeit für Microsoft Office 365 in Azure-Infrastrukturdiensten mit den folgenden virtuellen Computern:
  
- Zwei Webanwendungsproxy-Server
    
- Zwei Active Directory-Verbunddienste (AD FS)
    
- Zwei replizierte Domänencontroller
    
- Ein Verzeichnissynchronisierungsserver (DirSync), auf dem Azure AD Connect ausgeführt wird.
    
Dieses kurze Video gibt Ihnen einen schnellen Überblick über die Verbundauthentifizierungsinfrastruktur und die nötigen Schritte zur Einrichtung des Serversatzes in Azure, inklusive eines Beispiels für den Authentifizierungsprozess.
  
![Videosymbol (Wiedergabetaste)](images/mod_icon_video_M.png)
  
Nachfolgend sehen Sie die Konfiguration, mit einem Platzhalternamen für jeden Server.
  
**Eine Verbundauthentifizierung mit Hochverfügbarkeit für die Office 365-Infrastruktur in Azure**

![Die Endkonfiguration für die hochverfügbare Office 365-Verbundauthentifizierungsinfrastruktur in Azure](images/c5da470a-f2aa-489a-a050-df09b4d641df.png)
  
Alle virtuellen Computer befinden sich in einem einzigen standortübergreifenden virtuellen Azure-Netzwerk (VNet). 
  
> [!NOTE]
> Für die Verbundauthentifizierung einzelner Benutzer ist kein Rückgriff auf lokale Ressourcen erforderlich. Sollte die standortübergreifende Verbindung jedoch ausfallen, empfangen die Domänencontroller im VNet keine im lokalen Windows Server AD vorgenommenen Updates an Benutzerkonten und Gruppen. Zur Vermeidung eines solchen Szenarios können Sie Hochverfügbarkeit für die standortübergreifende Verbindung konfigurieren. Weitere Informationen finden Sie unter [Standortübergreifende Verbindungen und VNet-zu-VNet-Verbindungen mit hoher Verfügbarkeit](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-highlyavailable). 
  
Jedes Paar virtuelle Computer für eine bestimmte Rolle befindet sich in einem eigenen Subnetz und einer eigenen Verfügbarkeitsgruppe.
  
> [!NOTE]
> Da dieses VNet mit dem lokalen Netzwerk verbunden ist, umfasst diese Konfiguration keinen virtuellen Jumpbox- oder Überwachungscomputer in einem Verwaltungssubnetz. Weitere Informationen finden Sie unter [Ausführen von virtuellen Windows-Computern für eine Architektur mit N-Ebenen](https://docs.microsoft.com/azure/guidance/guidance-compute-n-tier-vm). 
  
Das Ergebnis dieser Konfiguration ist eine Verbundauthentifizierung für alle Ihre Office 365-Benutzer. Diese können sich dann also mit ihren Windows Server Active Directory-Anmeldeinformationen statt mit ihrem Office 365-Konto anmelden. Die Verbundauthentifizierungsinfrastruktur nutzt einen redundanten Satz von Servern, die in den Azure-Infrastrukturdiensten bereitgestellt sind, nicht in Ihrem lokalen Umkreisnetzwerk. Das ist eine deutlich einfacher zu implementierende Konstellation.
  
## Erforderliche Komponenten

Diese geplante Konfiguration erfordert den folgenden Satz von Azure-Diensten und Komponenten:
  
- Sieben virtuelle Computer
    
- Ein standortübergreifendes virtuelles Netzwerk mit vier Subnetzen
    
- Sieben Speicherkonten
    
- Vier Ressourcengruppen
    
- Drei Verfügbarkeitsgruppen.
    
Nachfolgend sehen Sie die virtuellen Computer und ihre Standardgrößen für diese Konfiguration.
  
|**Element**|**Beschreibung des virtuellen Computers**|**Azure-Katalogbild**|**Standardgröße**|
|:-----|:-----|:-----|:-----|
|1.  <br/> |Erster Domänencontroller  <br/> |Windows Server 2016 Datacenter  <br/> |D2  <br/> |
|2.  <br/> |Zweiter Domänencontroller  <br/> |Windows Server 2016 Datacenter  <br/> |D2  <br/> |
|3.  <br/> |Azure AD Connect-Server  <br/> |Windows Server 2016 Datacenter  <br/> |D2  <br/> |
|4.  <br/> |Erster AD FS-Server  <br/> |Windows Server 2016 Datacenter  <br/> |D2  <br/> |
|5.  <br/> |Zweiter AD FS-Server  <br/> |Windows Server 2016 Datacenter  <br/> |D2  <br/> |
|6.  <br/> |Erster Webanwendungsproxy-Server  <br/> |Windows Server 2016 Datacenter  <br/> |D2  <br/> |
|7.  <br/> |Zweiter Webanwendungsproxy-Server  <br/> |Windows Server 2016 Datacenter  <br/> |D2  <br/> |
   
Um die geschätzten Kosten für diese Konfiguration zu berechnen, finden Sie unter [Azure-Preisrechner](https://azure.microsoft.com/pricing/calculator/) weitere Informationen.
  
## Phasen der Bereitstellung

Sie stellen diese Arbeitslast in den folgenden Phasen bereit:
  
- [Hochverfügbarkeit der Verbundauthentifizierung, Phase 1: Konfigurieren von Azure](high-availability-federated-authentication-phase-1-configure-azure.md) . Erstellen von Ressourcengruppen, Speicherkonten, Verfügbarkeitsgruppen und einem standortübergreifenden virtuellen Netzwerk.
    
- [Hochverfügbarkeit der Verbundauthentifizierung, Phase 2: Konfigurieren von Domänencontrollern](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) . Erstellen und Konfigurieren von replizierten Windows Server Active Directory (AD)-Domänencontrollern und des DirSync-Servers.
    
- [Hochverfügbarkeit der Verbundauthentifizierung, Phase 3: Konfigurieren von AD FS-Servern](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md) . Erstellen und Konfigurieren der beiden AD FS-Server.
    
- [Hochverfügbarkeit der Verbundauthentifizierung, Phase 4: Konfigurieren von Webanwendungsproxys](high-availability-federated-authentication-phase-4-configure-web-application-pro.md) . Erstellen und Konfigurieren der beiden Webanwendungsproxy-Server
    
- [Hochverfügbarkeit der Verbundauthentifizierung, Phase 5: Konfigurieren der Verbundauthentifizierung für Office 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md) . Konfigurieren der Verbundauthentifizierung für Ihr Office 365-Abonnement
    
Dieser Artikel enthält eine phasenweise Anleitung für eine vordefinierte Architektur, um eine funktionale Verbundauthentifizierung mit hoher Verfügbarkeit für Office 365 in Azure-Infrastrukturdiensten zu erstellen. Denken Sie dabei an Folgendes:
  
- Wenn Sie ein erfahrener AD FS-Implementierer sind, können Sie die Anweisungen in den Phasen 3 und 4 entsprechend anpassen und eine Gruppe von Servern erstellen, die Ihren Anforderungen am besten entspricht. 
    
- Wenn Sie bereits über eine vorhandene Azure-Hybridcloudbereitstellung mit einem vorhandenen standortübergreifenden virtuellen Netzwerk verfügen, können Sie die Anweisungen in den Phasen 1 und 2 entsprechend anpassen oder überspringen und die AD FS-Server und die Webanwendungsproxy-Server in den entsprechenden Subnetzen platzieren.
    
Informationen zum Erstellen einer Entwicklungs-/Testumgebung oder einer Machbarkeitsstudie dieser Konfiguration finden Sie unter [Verbundidentität für Ihre Office 365-Entwicklungs-/Testumgebung](federated-identity-for-your-office-365-dev-test-environment.md).
  
## Nächster Schritt

Starten Sie die Konfiguration dieser Arbeitslast mit [Hochverfügbarkeit der Verbundauthentifizierung, Phase 1: Konfigurieren von Azure](high-availability-federated-authentication-phase-1-configure-azure.md). 
  
> [!TIP]
> Weitere Informationen zu einem Satz von Dateien, mit dem Sie die Hochverfügbarkeit bei der Verbundauthentifizierung für Office 365 in Azure schneller bereitstellen können, finden Sie unter [Deployment Kit zur Verbundauthentifizierung für Office 365 in Azure](https://gallery.technet.microsoft.com/Federated-Authentication-8a9f1664). 
  
## See Also

#### 

[Verbundidentität für Ihre Office 365-Entwicklungs-/Testumgebung](federated-identity-for-your-office-365-dev-test-environment.md)
  
[Cloudakzeptanz und Hybridlösungen](cloud-adoption-and-hybrid-solutions.md)
#### 

[Verbundidentität für Office 365](https://support.office.com/de-de/article/Grundlegendes-zu-Office-365-Identit%C3%A4ten-und-Azure-Active-Directory-06a189e7-5ec6-4af2-94bf-a22ea225a7a9?ui=de-DE&amp;rs=de-DE&amp;ad=DE#bk_federated)

