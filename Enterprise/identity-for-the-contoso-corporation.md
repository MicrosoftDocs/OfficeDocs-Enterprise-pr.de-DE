---
title: "Identität für die Contoso Corporation"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- DecEntMigration
- Ent_Architecture
ms.assetid: 78a407e4-2d8b-4561-b308-b22c95f60eeb
description: "Zusammenfassung: Grundlegendes zu wie Contoso nutzt IDaaS und bietet geografisch verteilten und redundante Authentifizierung für Benutzer."
ms.openlocfilehash: a0de29ac7e73216e04fe02c680f2557e9f402883
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2017
---
# <a name="identity-for-the-contoso-corporation"></a>Identität für die Contoso Corporation

 **Zusammenfassung:** Verstehen Sie, wie Contoso nutzt IDaaS und bietet geografisch verteilten und redundante Authentifizierung für Benutzer.
  
Microsoft bietet eine Identität als Dienst (IDaaS) über die Cloud-angeboten. Um eine Cloud-inklusive Infrastruktur einführen, muss Contoso IDaaS Lösung ihre lokalen STS-Anbieter nutzen und umfassen Verbundauthentifizierung mit ihren vorhandenen vertrauenswürdigen, Drittanbieter-Identitätsanbieter.
  
## <a name="contosos-windows-server-ad-forest"></a>Windows Server Active Directory-Gesamtstruktur von Contoso

Contoso verwendet eine einzelnen Gesamtstruktur Windows Server Active Directory (AD) für "contoso.com" mit sieben Domänen, eine für jede Region der Welt. Die zentrale, Hub regionale Büros und Zweigstellen enthalten Domänencontroller für die lokale Authentifizierung und Autorisierung.
  
**Abbildung 1: Contoso Gesamtstrukturen und Domänen weltweit**

![Weltweite Windows Server Active Directory-Gesamtstruktur und Domänen](images/Contoso_Poster/Contoso_WW_ID.png)
  
Abbildung 1 zeigt die Contoso-Gesamtstruktur mit regionalen Domänen für die unterschiedlichen Regionen, die Regionalstellen enthalten.
  
Contoso möchte die Konten und Gruppen in der „contoso.com“-Gesamtstruktur zur Authentifizierung und Autorisierung seiner cloudbasierten Apps und Arbeitslasten verwenden.

  
## <a name="contosos-federated-authentication-infrastructure"></a>Contoso Verbundauthentifizierung Infrastruktur

Contoso ermöglicht:
  
- Kunden können ihre Microsoft-, Facebook- oder Google Mail-Konten verwenden, um sich bei ihren öffentlichen Websites anzumelden.
    
- Lieferanten und Partner können ihre LinkedIn-, Salesforce- oder Google Mail-Konten verwenden, um sich beim Partnerextranet anzumelden.
    
**Abbildung 2: Contoso Unterstützung für Verbundauthentifizierung für Kunden und Partner**

![Contosos vorhandene Infrastruktur für die Unterstützung der Verbundauthentifizierung für Kunden und Partner](images/Contoso_Poster/Federated_ID.png)
  
Abbildung 2 zeigt die Contoso-DMZ mit einer öffentlichen Website, einem Partnerextranet und einer Reihe von AD FS-Servern. Die DMZ ist mit dem Internet verbunden, das Kunden, Partner und Internetdienste enthält.
  
Active Directory Federation Services-Server (AD FS) in der DMZ authentifizieren Kundenanmeldeinformationen für Zugriff auf die öffentliche Website und Partneranmeldeinformationen für Zugriff auf das Partnerextranet.
  
Wenn Contoso ihrer öffentlichen Website mit einem Azure Web App und Partnerextranet Dynamics 365 wechselt, soll weiterhin für den Kunden und Partnern diese Drittanbieter-Identitätsanbieter verwenden. Dies wird durch die Konfiguration des Verbunds zwischen Mandanten "Contoso" Azure AD und diese Drittanbieter-Identitätsanbieter erreicht werden.
  
## <a name="directory-synchronization-for-contosos-windows-server-ad-forest"></a>Directory-Synchronisierung für Contoso Windows Server Active Directory-Gesamtstruktur

Contoso hat das Azure AD-Connect-Tool auf einem Server in seiner Paris Datacenter-Cluster bereitgestellt. Azure Active Directory verbinden synchronisiert Änderungen an der Windows Server Active Directory-Gesamtstruktur "contoso.com" mit dem Azure AD-Mandanten von Contoso Office 365, zur Abstimmung, Dynamics 365 und Azure-Abonnements gemeinsam genutzt werden. Weitere Informationen zu Abonnements Lizenzen von Benutzerkonten und Mandanten, finden Sie unter [Abonnements, Lizenzen und Benutzerkonten der Contoso Corporation](subscriptions-licenses-and-user-accounts-for-the-contoso-corporation.md).
  
**Abbildung 3: Contoso Directory-Synchronisierung-Infrastruktur**

![Infrastruktur für die Verzeichnissynchronisierung von Contoso](images/Contoso_Poster/DirSync.png)
  
Abbildung 3 zeigt Servercluster, auf dem Azure AD Connect ausgeführt wird, das die Windows Server AD-Gesamtstruktur von Contoso mit dem Azure AD-Mandanten synchronisiert.
  
Contoso hat Verbundauthentifizierung, konfiguriert die einmaliges Anmelden für Contoso Worker bereitstellt. Ein Benutzer, der bereits die "contoso.com" Windows Server Active Directory-Gesamtstruktur angemeldet hat eine Microsoft SaaS oder PaaS Cloud-Ressource zugreift, werden nicht zur Eingabe eines Kennworts aufgefordert werden.
  
## <a name="geographical-distribution-of-contoso-authentication-traffic"></a>Geografische Verteilung des Contoso-Authentifizierungsdatenverkehrs


Um die mobilen und remote-Mitarbeitern besser zu unterstützen, hat Contoso Sätze von Authentifizierungsserver in seiner regionale Büros bereitgestellt. Diese Infrastruktur verteilt die Last und bietet Redundanz und höhere Leistung bei der Authentifizierung von Benutzeranmeldeinformationen für den Zugriff auf Microsoft Cloud-angeboten, die den gemeinsamen Azure AD-Mandanten verwenden.
  
Damit die Last von Authentifizierungsanfragen verteilt wird, hat Contoso Traffic Manager mit einem Profil konfiguriert, in dem die Leistungsroutingmethode verwendet wird, wodurch authentifizierende Clients an die regional nächstgelegene Gruppe von Authentifizierungsservern verwiesen wird.
  
  
**Abbildung 4: Geografische Verteilung der Authentifizierungsdatenverkehr für Zweigstellen**

![Geografische Verteilung des Contoso-Authentifizierungsdatenverkehrs für Regionalstellen
](images/Contoso_Poster/Auth_GeoDist.png)
  
Abbildung 4 zeigt die Ebenen von Clientcomputern, Azure Traffic Manager und Authentifizierungsservern in Regionalstellen. Jede regionale Niederlassung verwendet Webproxys und AD FS-Server, um Benutzeranmeldeinformationen mit Windows Server AD-Domänencontrollern zu authentifizieren.
  
Beispiel zum Authentifizierungsprozess:

  
1. Der Clientcomputer initiiert die Kommunikation mit einer Webseite in Office 365-Instanz in Europa (z. B.: "SharePoint.contoso.com").
    
2. Office 365 sendet eine Anforderung zum Nachweis der Authentifizierung zurück. Die Anforderung enthält die URL, die für die Authentifizierung kontaktiert werden soll.
    
3. Der Clientcomputer versucht, den DNS-Namen in der URL zu einer IP-Adresse aufzulösen.
    
4. Azure Traffic Manager empfängt die DNS-Abfrage und antwortet dem Clientcomputer mit der IP-Adresse eines Webanwendungs-Proxyservers in der Regionalstelle, die am nächsten zum Clientcomputer liegt.

    
5.  Der Clientcomputer sendet eine Authentifizierungsanforderung an eine Anwendung Webproxyserver, der die Anforderung an einen AD FS-Server weiterleitet.
    
6. Der AD FS-Server fordert die Anmeldeinformationen des Benutzers vom Clientcomputer an.
    
7. Der Clientcomputer sendet die Anmeldeinformationen des Benutzers, ohne dass der Benutzer zu einer Eingabe aufgefordert wird.
    
8. Der AD FS-Server überprüft die Anmeldeinformationen mit einem Windows Server AD-Domänencontroller in der Regionalstelle und gibt ein Sicherheitstoken an den Clientcomputer zurück.
    
9. Der Clientcomputer sendet das Sicherheitstoken an Office 365.
    
10. Nach der erfolgreichen Überprüfung speichert Office 365 das Sicherheitstoken zwischen und sendet die Webseitenanforderung aus Schritt 1 an den Clientcomputer.

    
## <a name="redundancy-for-the-headquarters-authentication-infrastructure-in-azure-iaas"></a>Redundanz für die Authentifizierungsinfrastruktur der Zentrale in Azure IaaS


Zur Bereitstellung von Redundanz für die Remote- und mobile Mitarbeiter über die zentrale Paris, die mit 15.000 Mitarbeiter enthält hat Contoso einen zweiten Satz von Proxys und AD FS-Servern in Azure IaaS bereitgestellt.
  
**Abbildung 5: Redundante Authentifizierungsinfrastruktur in Azure IaaS**

![Die redundante Authentifizierungsinfrastruktur in Azure Iaas für die Pariser Zentrale](images/Contoso_Poster/Paris_Auth_Redun.png)
  
Abbildung 5 zeigt Webproxys und AD FS-Server in der DMZ sowie jeweils eine zusätzliche Gruppe in einem standortübergreifenden virtuellen Azure-Netzwerk.
  
Wenn die primären Authentifizierungsserver in der DMZ in der Zentrale nicht mehr verfügbar sind, wechseln IT-Mitarbeiter zu der redundanten Gruppe, die in Azure IaaS bereitgestellt ist. Nachfolgende Authentifizierunganforderungen aus dem Büro in Paris verwenden die Gruppe in Azure IaaS, bis das Verfügbarkeitsproblem behoben ist.
  
Damit das Hin- und Zurückschalten funktioniert, aktualisiert Contoso das Azure Traffic Manager-Profil so, dass für die Webanwendungsproxys unterschiedliche Gruppen von IP-Adressen verwendet werden:

  
- Wenn die DMZ Authentifizierungsserver verfügbar sind, verwenden Sie die IP-Adressen der Server in der DMZ.
    
- Wenn die DMZ-Authentifizierungsserver nicht verfügbar sind, werden die IP-Adressen der Server in Azure IaaS verwendet.

    
## <a name="see-also"></a>See Also

[Contoso in der Microsoft-Cloud](contoso-in-the-microsoft-cloud.md)
  
[Ressourcen zur Cloud-IT-Architektur von Microsoft](microsoft-cloud-it-architecture-resources.md)

[Microsoft-Cloud-Identität für Enterprise-konstruiert](http://aka.ms/cloudarchidentity)
  
[Identität- und Geräteschutz für Office 365](http://aka.ms/o365protect_device)
  
[Microsoft-Roadmap Enterprise Cloud: Ressourcen für IT-Entscheidungsträger](https://sway.com/FJ2xsyWtkJc2taRD)



