---
title: Einrichten von verzeichnissynchronisierung für Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: get-started-article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- BCS160
ms.assetid: 1b3b5318-6977-42ed-b5c7-96fa74b08846
description: Informationen Sie zum Einrichten der verzeichnissynchronisierung zwischen Office 365 und die lokale Active Directory.
ms.openlocfilehash: e406eec08b34a694602c756235533f8b1ff6651e
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540753"
---
# <a name="set-up-directory-synchronization-for-office-365"></a>Einrichten von verzeichnissynchronisierung für Office 365
Office 365 verwendet Benutzer Cloud-basierten Identity Management Service Azure Active Directory zum Verwalten von Benutzern. Sie können auch die lokale Active Directory mit Azure AD integrieren, durch die Synchronisierung Ihrer lokalen Umgebung mit Office 365. Nach dem Synchronisierung einrichten können Sie haben ihre Benutzerauthentifizierung in Azure AD oder in Ihrem lokalen Verzeichnis stattfinden soll.
  
## <a name="office-365-directory-synchronization"></a>Office 365 Directory-Synchronisierung
Sie können entweder synchronisierten Identität oder Identitätsverbund zwischen Ihrer lokalen Organisation und Office 365 verwenden. Mit synchronisierten Identität Sie Ihre lokalen Benutzer verwalten, und sie werden von Azure Active Directory, wenn sie das gleiche Kennwort in der Cloud als lokale verwenden, authentifiziert. Dies ist die am häufigsten verwendeten Directory Synchronization Szenario. Pass-Through-Authentifizierung oder Federated Identity, können Sie Ihre lokalen Benutzer zu verwalten, und sie von Ihrem lokalen Verzeichnis authentifiziert werden. Identitätsverbund erfordert eine zusätzliche Konfiguration und ermöglicht es Benutzern nur einmal anmelden. Weitere Informationen finden Sie [Grundlegendes zu Office 365-Identität und Azure Active Directory](about-office-365-identity.md).
  
## <a name="want-to-upgrade-from-windows-azure-active-directory-sync-dirsync-to-azure-active-directory-connect"></a>Upgrade von Windows Azure Active Directory-Synchronisierung (DirSync) auf Azure Active Directory verbinden möchten?
Wenn Sie derzeit DirSync verwenden und aktualisieren möchten, head über auf [azure.com](https://azure.com) für [Aktualisierungsinformationen zu erhalten](https://go.microsoft.com/fwlink/p/?LinkId=733240).
  
## <a name="prerequisites-for-azure-ad-connect"></a>Erforderliche Komponenten für Azure Active Directory verbinden
Sie erhalten eine Testversion zu Azure AD mit Ihrem Office 365-Abonnement. Wenn Sie verzeichnissynchronisierung einrichten, werden Sie Azure Active Directory verbinden auf einem lokalen Servern installieren.
  
Für Office 365 benötigen Sie:
  
- Überprüfen Sie Ihre lokale Domäne (das Verfahren führt Sie durch diese).
- Haben Sie [Administratorrollen in Office 365 für Unternehmen zuweisen](https://support.office.com/article/EAC4D046-1AFD-4F1A-85FC-8219C79E1504) von Berechtigungen für Ihre Office 365-Mandanten, und klicken Sie mit der lokalen Active Directory. 
    
Für den lokalen Server, den Azure AD-Connect-Installation, benötigen Sie die folgende Software:
  
|**Betriebssystem des Servers**|**Weitere Software**|
|:-----|:-----|
|**Windows Server 2012 R2** | -PowerShell standardmäßig installiert ist, ist keine Aktion erforderlich.  <br/> -Net 4.5.1 und spätere Versionen werden über Windows Update angeboten. Stellen Sie sicher, dass Sie die neuesten Updates auf Windows Server in der Systemsteuerung installiert haben. |
|**Windows Server 2008 R2 mit Service Pack 1 (SP1)** oder **WindowsServer 2012** | -Die neueste Version von PowerShell ist in Windows Management Framework 4.0 verfügbar. Suchen sie im [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).<br/> -.net 4.5.1 und spätere Versionen stehen im [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996). |
|**Windows Server 2008** | -Die neueste unterstützte Version von PowerShell steht in Windows Management Framework 3.0, [Microsoft Download](https://go.microsoft.com/fwlink/p/?LinkId=717996)Center zur Verfügung.  <br/> -.net 4.5.1 und spätere Versionen stehen im [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996). |
   
> [!NOTE]
> Wenn Sie Azure Active Directory DirSync verwenden, ist die maximale Anzahl Mitglieder einer Verteilergruppe, die aus der lokalen Active Directory mit Azure Active Directory synchronisiert werden können 15.000. Für Azure Active Directory verbinden wird diese Nummer 50.000. 
  
Lesen Sie [erforderlichen Komponenten für Azure Active Directory verbinden](https://go.microsoft.com/fwlink/p/?LinkId=716896), sorgfältiger Hardware, Software, Konto und erforderliche Berechtigungen, Anforderungen an SSL-Zertifikate und Objekt Grenzwerte für Azure Active Directory verbinden um zu überprüfen.
  
Sie können ferner den Azure AD-Connect [Version Versionsgeschichte](https://go.microsoft.com/fwlink/p/?LinkId=733238) um finden Sie unter Was ist enthalten und in jeder Version behobenen. 

## <a name="to-set-up-directory-synchronization"></a>Directory-Synchronisierung einrichten
1. Melden Sie sich bei Office 365 Administrationscenter, und wählen Sie **Benutzer** \> **Aktive Benutzer** in der linken Navigationsleiste. 
2. Wählen Sie in der Office 365 Administrationscenter auf der Seite **aktive Benutzer** ** mehr ** \> **Directory-Synchronisierung**.
    
    ![Wählen Sie im Menü Weitere Directory-Synchronisierung](media/dc6669e5-c01b-471e-9cdf-04f5d44e1c4b.png)
  
3. Klicken Sie auf die ** Directory-Synchronisierung für Sie ist? ** Sie auf der Seite der ersten beiden Optionen von **1 bis 10**und **11 bis 50** Ergebnisse im "sollten auf der Grundlage der Größe Ihrer Organisation erstellen und Verwalten von Benutzern in der Cloud. Verzeichnissynchronisierung wird die Installation komplexer gestalten. Wechseln Sie zur aktiven Benutzer Ihre Benutzer hinzufügen." 
    
    - Sie können, jedoch Directory-Synchronisierung einrichten weiterhin durch Auswählen von **hier weiter** am unteren Rand der Seite. 
    
    - Bei Auswahl von zwei letzteren Auswahlmöglichkeiten **51-250** oder **251 oder höher**, wird die Einrichtung der Synchronisierung Directory-Synchronisierung empfohlen. Wählen Sie auf **Weiter** . 
    
    ![Wählen Sie weiter, um den Vorgang fortzusetzen Directory-Synchronisierung einrichten](media/359a1eb9-99ae-4b5b-a413-4de53037cceb.png)
  
4. Klicken Sie auf die **Synchronisierung Ihrer lokalen Verzeichnis mit der Cloud**, lesen Sie die Informationen und wenn Sie weitere Informationen wünschen, wählen Sie die hier finden Sie weitere Hyperlink, um verweist: [Vorbereiten der Bereitstellung von Benutzern über Directory-Synchronisierung mit Office 365](prepare-for-directory-synchronization.md), und wählen Sie dann weiter ** **. 
    
5. Überprüfen Sie auf der Seite **prüfen wir Ihr Verzeichnis** die Anforderungen für die Überprüfung automatisch Ihr Verzeichnis. Wenn Sie die Anforderungen erfüllen, wählen Sie **Weiter** \> **Suche starten**. Wenn Sie die Anforderungen erfüllen können nicht können Sie weiterhin von einem **Datenträger manuell**.
    
    ![Wählen Sie weiter oder weiterhin manuell auf die prüfen wir Ihre Seite Verzeichnis](media/af4a6bd5-13aa-4bfa-9751-4464a32ca8db.png)
  
6. Wenn Sie Ihre Verzeichnisse Scannen auswählen, wählen Sie auf der Seite **Auswerten Directory Synchronization Setup** **Suche starten** . 
    
    Befolgen Sie die Anweisungen zum Herunterladen und Ausführen der Überprüfung.
    
7. Nach Abschluss die Überprüfung zurück zu den Setup-Assistenten, und wählen Sie **Weiter** auf die Überprüfungsergebnisse finden Sie unter. 
    
8. Überprüfen Sie Ihre Domänen wie auf der Seite **Überprüfen Besitzrechte für Ihre Domänen** beschrieben. Weitere Informationen finden Sie unter [Erstellen von DNS-Einträge für Office 365 beim Verwalten Ihrer DNS-Einträge](https://support.office.com/article/b0f3fdca-8a80-4e8e-9ef3-61e8a2a9ab23).
    
    > [!IMPORTANT]
    > Nachdem Sie eine TXT-Eintrag, um sicherzustellen, dass Sie Ihre Domäne besitzen hinzugefügt haben, gehen Sie nicht mit dem nächsten Schritt im Assistenten Domänen hinzufügen von Benutzern. Directory-Synchronisierung wird für Benutzer hinzufügen. 
  
    Kehren Sie zur Seite **Office 365 Setup** aus, und wählen Sie **Aktualisieren**
    
    ![Nachdem Sie Ihre Domänen überprüft haben, wählen Sie aktualisieren](media/9b5fb593-5ff7-49f0-80d0-18e36d39d669.png)
  
9. Wählen Sie auf der Seite **Ihre Domänen können** **Weiter**.
    
10. Klicken Sie auf der Seite **Bereinigen der Umgebung** optional, befolgen Sie die Anweisungen zum Herunterladen von IDFix, um die Active Directory überprüfen. Wählen Sie auf **Weiter** . 
    
11. Klicken Sie auf die ** ausführen Azure Active Directory verbinden ** Seite, und wählen Sie **herunterladen** Azure AD-Connect-Assistenten installieren. 
    
    > [!NOTE]
    > An dieser Stelle können Sie im Assistenten Azure Active Directory verbinden. Stellen Sie sicher, dass Sie die Directory Synchronization Assistentenseite lassen, den, die Sie zuletzt wurden beim Öffnen in Ihrem Browser, damit Sie es zurückgeben können, nachdem die Azure AD-Connect Schritte durchgeführt werden. 
  
    Nach dem Verbinden von Azure AD-Assistent installiert hat, wird es automatisch geöffnet. Sie können auch auf dem Desktop das Install-Standardwebsite öffnen. Führen Sie die Anweisungen des Assistenten je nach Szenario:
    
  - Verwenden Sie für Directory-Synchronisierung mit kennwortsynchronisierung Hash [Azure AD-Verbinden mit den express-Einstellungen](https://go.microsoft.com/fwlink/p/?LinkID=698537).
    
  - Verwenden Sie für mehrere Gesamtstrukturen, Pass-Through-Authentifizierung, Identitätsverbund und SSO-Optionen die [benutzerdefinierte Installation von Azure Active Directory verbinden](https://go.microsoft.com/fwlink/p/?LinkId=698430).
    
    Wählen Sie auf der Seite **Einstellungen Express** dieser Optionen **Anpassen** . 
    
12. Nach Abschluss des Assistenten Azure AD-Connect zum **Office 365 Setup** -Assistenten zurückzukehren Sie, und befolgen Sie die Anweisungen auf **Stellen Sie sicher, dass Sync als erwartete Seite gearbeitet**. Wählen Sie auf **Weiter** . 
    
13. Lesen die Anweisungen auf dem ** Aktivieren Benutzer ** Seite, und wählen Sie dann auf **Weiter**.
    
14. Wählen Sie auf der Seite **Sie sind alle Setup** **Fertig stellen** . 
    
## <a name="assign-licences-to-synchronized-users"></a>Synchronisierte Benutzern Lizenzen zuweisen
Nachdem Sie Ihre Benutzer zu Office 365 synchronisiert haben, sie erstellt werden, aber Sie müssen für diese Lizenzen zuweisen, sodass diese Office 365-Features, wie Mail verwenden können. Anweisungen finden Sie unter [Zuweisen von Lizenzen für Benutzer in Office 365 für Unternehmen](https://support.office.com/article/997596b5-4173-4627-b915-36abac6786dc).
    
## <a name="finish-setting-up-domains"></a>Einrichtung Domänen fertig gestellt
Führen Sie die Schritte in [Erstellen von DNS-Einträge für Office 365 beim Verwalten Ihrer DNS-Einträge](https://support.office.com/article/b0f3fdca-8a80-4e8e-9ef3-61e8a2a9ab23) auf Fertig stellen, wie Sie Ihre Domänen einrichten.