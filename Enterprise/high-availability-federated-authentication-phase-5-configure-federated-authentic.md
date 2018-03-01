---
title: "Hochverfügbarkeit der Verbundauthentifizierung, Phase 5 Konfigurieren der Verbundauthentifizierung für Office 365"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Solutions
ms.assetid: 0f1dbf52-5bff-44cc-a264-1b48641af98f
description: "Zusammenfassung: Konfigurieren Sie Azure AD Connect für die Verbundauthentifizierung mit hoher Verfügbarkeit für Office 365 in Microsoft Azure."
ms.openlocfilehash: 2c23ffa2e9f033018c5cc1fd016fb4ed76535605
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/09/2018
---
# <a name="high-availability-federated-authentication-phase-5-configure-federated-authentication-for-office-365"></a>Hochverfügbarkeit der Verbundauthentifizierung, Phase 5: Konfigurieren der Verbundauthentifizierung für Office 365

 **Zusammenfassung:** Konfigurieren Sie Azure AD Connect für die Verbundauthentifizierung mit hoher Verfügbarkeit für Office 365 in Microsoft Azure.
 
In dieser Phase der Bereitstellung der hohen Verfügbarkeit für Verbundauthentifizierung für Office 365 in Azure-Infrastrukturdiensten rufen Sie ein Zertifikat, das von einer öffentlichen Zertifizierungsstelle ausgestellt wurde, ab, installieren das Zertifikat. Dann überprüfen Sie Ihre Konfiguration und installieren Azure AD Connect auf dem DirSync-Server und führen es aus. Azure AD Connect konfiguriert Ihr Office 365-Abonnement und Ihre AD FS- und Webanwendungsproxy-Server für die Verbundauthentifizierung.
  
Eine Übersicht über alle Phasen finden Sie unter [Bereitstellen der Verbundauthentifizierung mit Hochverfügbarkeit für Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md).
  
## <a name="get-a-public-certificate-and-copy-it-to-the-dirsync-server"></a>Abrufen eines öffentlichen Zertifikats und kopieren des Zertifikats auf den DirSync-Server

Rufen Sie ein digitales Zertifikat von einer öffentlichen Zertifizierungsstelle mit den folgenden Eigenschaften ab:
  
- Ein X.509-Zertifikat, das zum Erstellen von SSL-Verbindungen geeignet ist.
    
- Die erweiterte Eigenschaft „Alternativer Antragstellername (SAN)“ ist auf den FQDN des Verbunddiensts festgelegt (z. B. „fs.contoso.com“)
    
- Das Zertifikat muss über den privaten Schlüssel verfügen und im PFX-Format gespeichert sein.
    
Außerdem müssen die Computer und Geräte Ihrer Organisation der öffentlichen Zertifizierungsstelle vertrauen, die das digitale Zertifikat ausstellt. Diese Vertrauensstellung wird eingerichtet, indem ein Stammzertifikat von der öffentlichen Zertifizierungsstelle im Speicher der vertrauenswürdigen Stammzertifizierungsstellen auf Ihren Computern und Geräten installiert wird. Computer, auf denen Microsoft Windows ausgeführt wird, verfügen in der Regel über eine Reihe dieser Zertifikattypen, die von häufig verwendeten Zertifizierungsstellen verwendet werden. Wenn das Stammzertifikat von der öffentlichen Zertifizierungsstelle noch nicht installiert ist, müssen Sie dieses auf den Computern und Geräten Ihrer Organisation bereitstellen.
  
Weitere Informationen zu Zertifikatanforderungen für die Verbundauthentifizierung finden Sie unter [Voraussetzungen für die Verbundinstallation und -konfiguration](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-prerequisites#prerequisites-for-federation-installation-and-configuration).
  
Wenn Sie das Zertifikat erhalten, kopieren Sie es in den Ordner auf Laufwerk C: des DirSync-Servers. Geben Sie der Datei z. B. den Namen „SSL.pfx", und speichern Sie sie im Ordner „C:\\Certs" auf dem DirSync-Server.
  
## <a name="verify-your-configuration"></a>Überprüfen Ihrer Konfiguration

Jetzt sollten Sie bereit sein, Azure AD Connect und die Verbundauthentifizierung für Office 365 zu konfigurieren. Um sicherzustellen, dass Sie bereit sind, finden Sie hier eine Checkliste:
  
- Die öffentliche Domäne Ihrer Organisation wird Ihrem Office 365-Abonnement hinzugefügt.
    
- Die Office 365-Benutzerkonten Ihrer Organisation sind auf den öffentlichen Domänennamen der Organisation konfiguriert und können sich erfolgreich anmelden.
    
- Sie haben einen FQDN des Verbunddiensts basierend auf Ihrem öffentlichen Domänennamen ermittelt.
    
- Ein öffentlicher DNS-A-Eintrag für den FQDN des Verbunddiensts zeigt auf die öffentliche IP-Adresse des Azure-Lastenausgleichs mit Internetzugriff für die Webanwendungsproxy-Server.
    
- Ein privater DNS-A-Eintrag für den FQDN Ihres Verbunddiensts zeigt auf die private IP-Adresse des internen Azure-Lastenausgleichs für die AD FS-Server.
    
- Ein von einer öffentlichen Zertifizierungsstelle ausgestelltes digitales Zertifikat, das für SSL-Verbindungen mit dem SAN geeignet ist, das auf den FQDN des Verbunddiensts festgelegt ist, ist eine PFX-Datei, die auf dem DirSync-Server gespeichert ist.
    
- Das Stammzertifikat für die öffentliche Zertifizierungsstelle wird im Speicher der vertrauenswürdigen Stammzertifizierungsstellen auf Ihren Computern und Geräten installiert.
    
Nachfolgend finden Sie ein Beispiel für die Contoso-Organisation:
  
**Eine Beispielkonfiguration für die Verbundauthentifizierung mit Hochverfügbarkeit in Azure**

![Eine Beispielkonfiguration für die hochverfügbare Office 365-Verbundauthentifizierung in Azure](images/ac1a6a0d-0156-4407-9336-6e4cd6db8633.png)
  
## <a name="run-azure-ad-connect-to-configure-federated-authentication"></a>Ausführen von Azure AD Connect zum Konfigurieren der Verbundauthentifizierung

Das Tool Azure AD Connect konfiguriert die AD FS-Server, die Webanwendungsproxy-Server und Office 365 über die folgenden Schritte für die Verbundauthentifizierung:
  
1. Erstellen Sie eine Remotedesktopverbindung mit Ihrem DirSync-Server über ein Domänenkonto, das über lokale Administratorberechtigungen verfügt.
    
2. Öffnen Sie über den Desktop des DirSync-Servers Internet Explorer, und wechseln Sie zu [https://aka.ms/aadconnect](https://aka.ms/aadconnect).
    
3. Klicken Sie auf der Seite **Microsoft Azure Active Directory Connect** auf **Herunterladen** und dann auf **Ausführen**.
    
4. Klicken Sie auf der Seite **Willkommen bei Azure AD Connect** auf **Ich stimme zu** und dann auf **Weiter**.
    
5. Klicken Sie auf der Seite **Express-Einstellungen** auf **Anpassen**.
    
6. Klicken Sie auf der Seite **Erforderliche Komponenten installieren** auf **Installieren**.
    
7. Klicken Sie auf der Seite **Benutzeranmeldung** auf **Verbund mit AD FS**, und klicken Sie dann auf **Weiter**.
    
8. Geben Sie auf der Seite **Mit Azure AD verbinden** den Namen und das Kennwort eines globalen Administratorkontos für Ihr Office 365-Abonnement ein, und klicken Sie dann auf **Weiter**.
    
9. Stellen Sie auf der Seite **Verzeichnisse verbinden** sicher, dass Ihre lokale Windows Server AD-Gesamtstruktur unter **Gesamtstruktur** ausgewählt ist, geben Sie den Namen und das Kennwort eines Domänenadministratorkontos ein, klicken Sie auf **Verzeichnis hinzufügen**, und klicken Sie dann auf **Weiter**.
    
10. Klicken Sie auf der Seite **Azure AD-Anmeldungskonfiguration** auf **Weiter**.
    
11. Klicken Sie auf der Seite **Filtern von Domänen und Organisationseinheiten** auf **Weiter**.
    
12. Klicken Sie auf der Seite **Eindeutige Identifizierung der Benutzer** auf **Weiter**.
    
13. Klicken Sie auf der Seite **Benutzer und Geräte filtern** auf **Weiter**.
    
14. Klicken Sie auf der Seite **Optionale Features** auf **Weiter**.
    
15. Klicken Sei auf der Seite **AD FS-Farm** auf **Neue AD FS-Farm konfigurieren**.
    
16. Klicken Sie auf **Durchsuchen**, und geben Sie den Speicherort und Namen des SSL-Zertifikats von der öffentlichen Zertifizierungsstelle an.
    
17. Geben Sie nach Aufforderung das Kennwort des Zertifikats ein, und klicken Sie dann auf **OK**.
    
18. Überprüfen Sie, ob der **Betreffname** und der **Verbunddienstname** auf den FQDN des Verbunddiensts festgelegt sind, und klicken Sie dann auf **Weiter**.
    
19. Geben Sie auf der Seite **AD FS-Server** den Namen des ersten AD FS-Servers (Tabelle M - Element 4 - Spalte „Name des virtuellen Computers") ein, und klicken Sie dann auf **Hinzufügen**.
    
20. Geben Sie den Namen des zweiten AD FS-Servers ein (Tabelle M - Element 5 - Spalte „Name des virtuellen Computers"), klicken Sie auf **Hinzufügen**, und klicken Sie dann auf **Weiter**.
    
21. Geben Sie auf der Seite **Webanwendungsproxy-Server** den Namen des ersten Webanwendungsproxy-Servers (Tabelle M - Element 6 - Spalte „Name des virtuellen Computers") ein, und klicken Sie dann auf **Hinzufügen**.
    
22. Geben Sie den Namen des zweiten Webanwendungsproxy-Servers ein (Tabelle M - Element 7 - Spalte „Name des virtuellen Computers"), klicken Sie auf **Hinzufügen**, und klicken Sie dann auf **Weiter**.
    
23. Geben Sie auf der Seite **Anmeldeinformationen des Domänenadministrators** den Benutzernamen und das Kennwort für eines Domänenadministratorkontos ein, und klicken Sie dann auf **Weiter**.
    
24. Geben Sie auf der Seite **AD FS-Dienstkonto** den Benutzernamen und das Kennwort für eines Unternehmensadministratorkonto ein, und klicken Sie dann auf **Weiter**.
    
25. Wählen Sie auf der Seite **Azure AD-Domäne** unter **Domäne** den DNS-Domänennamen Ihrer Organisation aus, und klicken Sie dann auf **Weiter**.
    
26. Klicken Sie auf der Seite **Bereit zur Konfiguration** auf **Installieren**.
    
27. Klicken Sie auf der Seite **Installation ist abgeschlossen** auf **Überprüfen**. Nun sollten zwei Meldungen angezeigt werden, aus denen hervorgeht, dass sowohl die Intranet- als auch die Internetkonfiguration erfolgreich überprüft wurde.
    
  - In der Intranetnachricht sollte die private IP-Adresse des internen Azure-Lastenausgleichs für Ihre AD FS-Server aufgeführt werden.
    
  - In der Internetnachricht sollte die öffentliche IP-Adresse des Azure-Lastenausgleichs mit Internetzugriff für Ihre Webanwendungsproxy-Server aufgeführt sein.
    
28. Klicken Sie auf der Seite **Installation ist abgeschlossen** auf **Beenden**.
    
Nachfolgend sehen Sie die finale Konfiguration mit Platzhalternamen für die Server.
  
**Phase 5: Die finale Konfiguration für die Verbundauthentifizierungsinfrastruktur mit hoher Verfügbarkeit in Azure**

![Die Endkonfiguration für die hochverfügbare Office 365-Verbundauthentifizierungsinfrastruktur in Azure](images/c5da470a-f2aa-489a-a050-df09b4d641df.png)
  
Die Verbundauthentifizierungsinfrastruktur mit hoher Verfügbarkeit für Office 365 in Azure ist abgeschlossen
  
## <a name="see-also"></a>Siehe auch

[Bereitstellen der Verbundauthentifizierung mit Hochverfügbarkeit für Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)
  
[Verbundidentität für Ihre Office 365-Entwicklungs-/Testumgebung](federated-identity-for-your-office-365-dev-test-environment.md)
  
[Cloudakzeptanz und Hybridlösungen](cloud-adoption-and-hybrid-solutions.md)

[Verbundidentität für Office 365](https://support.office.com/article/Understanding-Office-365-identity-and-Azure-Active-Directory-06a189e7-5ec6-4af2-94bf-a22ea225a7a9#bk_federated)


