---
title: Directory-Synchronisierung für Ihre Office 365 Dev/Test-Umgebung
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/04/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Strat_O365_Enterprise
- TLG
- Ent_TLGs
ms.assetid: e6b27e25-74ae-4b54-9421-c8e911aef543
description: 'Zusammenfassung: Konfigurieren der verzeichnissynchronisierung für Ihre Office 365 Dev/Test-Umgebung.'
ms.openlocfilehash: 1363e7fd6a3afdbec85fd08790268ab186badbc8
ms.sourcegitcommit: 21cc62118b78b76d16ef12e2c3eff2c0c789e3d0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/05/2018
---
# <a name="directory-synchronization-for-your-office-365-devtest-environment"></a>Directory-Synchronisierung für Ihre Office 365 Dev/Test-Umgebung

 **Zusammenfassung:** Konfigurieren Sie Directory-Synchronisierung für Ihre Office 365 Dev/Test-Umgebung.
  
Viele Organisationen mit Azure Active Directory verbinden und Directory-Synchronisierung mit dem den Satz von Konten in ihrer lokalen Windows Server Active Directory (AD) Gesamtstruktur den Satz von Konten in Office 365 synchronisiert. In diesem Artikel wird beschrieben, wie Sie Directory-Synchronisierung mit kennwortsynchronisierung Hash der Test-/Office 365-Umgebung hinzufügen in der folgenden Konfiguration resultierendes.
  
![Office 365-Umgebung Test-/mit Directory-Synchronisierung](images/be5b37b0-f832-4878-b153-436c31546e21.png)
  
Diese Konfiguration besteht aus:  
  
- Einem Office 365 E5-Testabonnement, das 30 Tage nach Erstellung abläuft.
- Einem vereinfachtem Unternehmensintranet mit Internetzugriff, das aus drei virtuellen Computern in einem Subnetz eines virtuellen Azure-Netzwerks (DC1, APP1 und CLIENT1) besteht. Azure AD Connect wird auf APP1 für die Synchronisierung der Windows Server Active Directory-Domäne mit Office 365 ausgeführt.
    
Es gibt zwei Hauptphasen bei der Einrichtung dieser Entwicklungs-/Testumgebung:
  
1. Erstellen der Office 365-Entwicklungs-/Testumgebung (virtuelle DC1-, APP1- und CLIENT1-Computer in einem virtuellen Azure Netzwerk mit einem Office 365 E5-Testabonnement)
2. Installieren und Konfigurieren von Azure AD Connect auf APP1
    
> [!TIP]
> Klicken Sie [hier](http://aka.ms/catlgstack), um eine visuelle Darstellung aller Artikel im Stapel der Testumgebungsanleitungen in der Microsoft Cloud zu erhalten.
  
## <a name="phase-1-create-an-office-365-devtest-environment"></a>Phase 1: Erstellen einer Office 365-Entwicklungs-/Testumgebung

Befolgen Sie die Anweisungen in Phasen 1, 2 und 3 des Artikels [Office 365 Dev/Test Environment](office-365-dev-test-environment.md) . Hier ist die resultierende Konfiguration.
  
![Die Office 365-Entwicklungs-/Testumgebung](images/48fb91aa-09b0-4020-a496-a8253920c45d.png)
  
Diese Konfiguration besteht aus:  
  
- Einem Office 365 E5-Testabonnement
- Einem vereinfachtem Unternehmensintranet mit Internetzugriff, das aus virtuellen DC1-, APP1- und CLIENT1-Computern in einem Subnetz eines virtuellen Azure-Netzwerks besteht.
    
## <a name="phase-2-install-azure-ad-connect-on-app1"></a>Phase 2: Installieren von Azure AD Connect auf APP1

Nach Abschluss der Installation und Konfiguration synchronisiert Azure AD Connect den Kontensatz in der CORP Windows Server AD-Domäne mit dem Kontensatz im Office 365-Testabonnement. Das folgende Verfahren führt Sie durch die Installation von Azure AD Connect auf APP1 und die Sicherstellung der ordnungsgemäßen Funktionsweise.
  
### <a name="install-and-configure-azure-ad-connect-on-app1"></a>Installieren und Konfigurieren von Azure Active Directory verbinden auf APP1

1. Über das [Portal Azure](https://portal.azure.com)Herstellen einer Verbindung mit der CORP APP1 mit\\Konto User1 an.
    
2. Öffnen Sie auf APP1 eine Windows PowerShell-Eingabeaufforderung auf Administratorebene, und führen Sie die folgenden Befehle aus:
    
  ```
  Set-ItemProperty -Path "HKLM:\\SOFTWARE\\Microsoft\\Active Setup\\Installed Components\\{A509B1A7-37EF-4b3f-8CFC-4F3A74704073}" -Name "IsInstalled" -Value 0
Set-ItemProperty -Path "HKLM:\\SOFTWARE\\Microsoft\\Active Setup\\Installed Components\\{A509B1A8-37EF-4b3f-8CFC-4F3A74704073}" -Name "IsInstalled" -Value 0
Stop-Process -Name Explorer -Force

  ```

3. Klicken Sie in der Taskleiste klicken Sie auf **Internet Explorer** , und gehen Sie zu [https://aka.ms/aadconnect](https://aka.ms/aadconnect).
    
4. Klicken Sie auf der Seite Microsoft Azure Active Directory verbinden klicken Sie auf **Download**, und klicken Sie dann auf **Ausführen**.
    
5. Klicken Sie auf der Seite **Willkommen auf Azure Active Directory verbinden** auf **ich stimme zu**, und klicken Sie dann auf **Weiter**.
    
6. Klicken Sie auf der Seite **Einstellungen für Express** auf **express Einstellungen verwenden**.
    
7. Klicken Sie auf der Seite **Connect to Azure AD** **Username,** Geben Sie in Geben Sie Ihren Kontonamen globaler Administrator im Feld **Kennwort**das Kennwort ein, und klicken Sie dann auf **Weiter**.
    
8. Geben Sie auf der Seite **Verbindung mit AD DS** **CORP\\User1** in **Benutzername** Geben Sie im Feld **Kennwort**das Kennwort ein, und klicken Sie dann auf **Weiter**.
    
9. Klicken Sie auf der Seite **Azure AD - Anmeldung Konfiguration** klicken Sie auf **Weiter, ohne alle überprüften Domänen**, und klicken Sie dann auf **Weiter**.
    
10. Klicken Sie auf der Seite **Bereit zur Konfiguration** auf **Installieren**.
    
11. Klicken Sie auf der Seite **Konfiguration abgeschlossen** auf **Beenden**.
    
12. Wechseln Sie in Internet Explorer zu Office 365-Portal ([https://portal.office.com](https://portal.office.com)) und melden Sie sich Test Office 365-Abonnement mit Ihrer globalen Administratorkonto an.
    
13. Klicken Sie auf der Hauptportalseite auf **Admin**.
    
14. Klicken Sie im linken Navigationsbereich auf **Benutzer > Aktive Benutzer**.
    
    Notieren Sie das Konto, mit dem Namen **User1**. Dieses Konto wird von der CORP Windows Azure AD-Domäne und belegen, die verzeichnissynchronisierung gearbeitet hat.
    
15. Klicken Sie auf dem Konto **User1** an. Lizenzen klicken Sie auf **Bearbeiten**.
    
16. Wählen Sie in der **Lizenzen**Ihr Land, und klicken Sie dann auf das Steuerelement **deaktiviert** für **Office 365 Enterprise E5** (Wechsel auf **aktiviert**). Klicken Sie auf **Speichern** , am unteren Rand der Seite, und klicken Sie dann auf **Schließen**.
    
Nachfolgend sehen Sie die daraus resultierende Konfiguration.
  
![Office 365-Umgebung Test-/mit Directory-Synchronisierung](images/be5b37b0-f832-4878-b153-436c31546e21.png)
  
Diese Konfiguration besteht aus:  
  
- Einem Office 365 E5-Testabonnement
- Einem vereinfachtem Unternehmensintranet mit Internetzugriff, das aus virtuellen DC1-, APP1- und CLIENT1-Computern in einem Subnetz eines virtuellen Azure-Netzwerks besteht. Azure AD Connect wird auf APP1 ausgeführt, um die CORP Windows Server Active Directory-Domäne mit Office 365 alle 30 Minuten zu synchronisieren.
    
## <a name="next-step"></a>Nächster Schritt

Wenn Sie zum Bereitstellen von verzeichnissynchronisierung für Ihre Organisation bereit sind, finden Sie unter [Bereitstellen von Office 365 Directory-Synchronisierung in Microsoft Azure](deploy-office-365-directory-synchronization-dirsync-in-microsoft-azure.md).

## <a name="see-also"></a>Siehe auch

[Cloud-Annahme Test Lab Guides (TLGs)](cloud-adoption-test-lab-guides-tlgs.md)
[Basiskonfiguration Test-/Umgebung](base-configuration-dev-test-environment.md)
[Office 365 Dev/testumgebung](office-365-dev-test-environment.md)
[Cloud App-Sicherheit für Ihre Office 365-Umgebung](cloud-app-security-for-your-office-365-dev-test-environment.md) Test-/
 [ Erweiterte Schutz für Ihre Office 365-Umgebung Test-/](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
[Cloud-Übernahme- und hybridlösungen](cloud-adoption-and-hybrid-solutions.md)




