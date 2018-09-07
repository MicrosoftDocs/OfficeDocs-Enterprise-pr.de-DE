---
title: Verzeichnissynchronisierung für die Office 365-Entwicklungs-/Testumgebung
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/18/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: e6b27e25-74ae-4b54-9421-c8e911aef543
description: 'Zusammenfassung: Konfigurieren der Verzeichnissynchronisierung für die Office 365-Entwicklungs-/Testumgebung'
ms.openlocfilehash: 106e902c9da46c7c3c0fc6eb8af96d6695c7bdce
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915840"
---
# <a name="directory-synchronization-for-your-office-365-devtest-environment"></a>Verzeichnissynchronisierung für die Office 365-Entwicklungs-/Testumgebung

 **Zusammenfassung:** Konfigurieren der Verzeichnissynchronisierung für die Office 365-Entwicklungs-/Testumgebung
  
Viele Organisationen verwenden Azure AD Connect und Verzeichnissynchronisierung, um den Kontensatz in ihrer lokalen Windows Server Active Directory (AD)-Gesamtstruktur mit dem Kontensatz in Office 365 zu synchronisieren. In diesem Artikel wird beschrieben, wie Sie die Verzeichnissynchronisierung mit Kennworthashsynchronisierung in der Office 365-Entwicklungs-/Testumgebung verwenden können, woraus die folgende Konfiguration resultiert:
  
![Die Office 365-Entwicklungs-/Testumgebung mit Verzeichnissynchronisierung](media/be5b37b0-f832-4878-b153-436c31546e21.png)
  
Diese Konfiguration besteht aus:  
  
- Einem Office 365 E5-Testabonnement, das 30 Tage nach Erstellung abläuft.
- Einem vereinfachtem Unternehmensintranet mit Internetzugriff, das aus drei virtuellen Computern in einem Subnetz eines virtuellen Azure-Netzwerks (DC1, APP1 und CLIENT1) besteht. Azure AD Connect wird auf APP1 für die Synchronisierung der Windows Server Active Directory-Domäne mit Office 365 ausgeführt.
    
Es gibt zwei Hauptphasen bei der Einrichtung dieser Entwicklungs-/Testumgebung:
  
1. Erstellen der Office 365-Entwicklungs-/Testumgebung (virtuelle DC1-, APP1- und CLIENT1-Computer in einem virtuellen Azure Netzwerk mit einem Office 365 E5-Testabonnement)
2. Installieren und Konfigurieren von Azure AD Connect auf APP1
    
> [!TIP]
> Klicken Sie [hier](http://aka.ms/catlgstack), um eine visuelle Darstellung aller Artikel im Stapel der Testumgebungsanleitungen in der Microsoft Cloud zu erhalten.
  
## <a name="phase-1-create-an-office-365-devtest-environment"></a>Phase 1: Erstellen einer Office 365-Entwicklungs-/Testumgebung

Folgen Sie den Anweisungen in Phasen 1, 2 und 3 des Artikels [Office 365-Entwicklungs-/Testumgebung](office-365-dev-test-environment.md). Nachfolgend sehen Sie die daraus resultierende Konfiguration.
  
![Die Office 365-Entwicklungs-/Testumgebung](media/48fb91aa-09b0-4020-a496-a8253920c45d.png)
  
Diese Konfiguration besteht aus:  
  
- Einem Office 365 E5-Testabonnement
- Einem vereinfachtem Unternehmensintranet mit Internetzugriff, das aus virtuellen DC1-, APP1- und CLIENT1-Computern in einem Subnetz eines virtuellen Azure-Netzwerks besteht.
    
## <a name="phase-2-install-azure-ad-connect-on-app1"></a>Phase 2: Installieren von Azure AD Connect auf APP1

Nach Abschluss der Installation und Konfiguration synchronisiert Azure AD Connect den Kontensatz in der CORP Windows Server AD-Domäne mit dem Kontensatz im Office 365-Testabonnement. Das folgende Verfahren führt Sie durch die Installation von Azure AD Connect auf APP1 und die Sicherstellung der ordnungsgemäßen Funktionsweise.
  
### <a name="install-and-configure-azure-ad-connect-on-app1"></a>Installieren und Konfigurieren von Azure AD Connect auf APP1

1. Melden Sie sich über das [Azure-Portal](https://portal.azure.com) mit dem CORP\\Benutzer1-Konto bei APP1 an.
    
2. Öffnen Sie auf APP1 eine Windows PowerShell-Eingabeaufforderung auf Administratorebene, und führen Sie die folgenden Befehle aus:
    
  ```
  Set-ItemProperty -Path "HKLM:\SOFTWARE\Microsoft\Active Setup\Installed Components\{A509B1A7-37EF-4b3f-8CFC-4F3A74704073}" -Name "IsInstalled" -Value 0
Set-ItemProperty -Path "HKLM:\SOFTWARE\Microsoft\Active Setup\Installed Components\{A509B1A8-37EF-4b3f-8CFC-4F3A74704073}" -Name "IsInstalled" -Value 0
Stop-Process -Name Explorer -Force

  ```

3. Klicken Sie auf der Taskleiste auf **Internet Explorer**, und wechseln Sie zu [https://aka.ms/aadconnect](https://aka.ms/aadconnect).
    
4. Klicken Sie auf der Seite „Microsoft Azure Active Directory Connect“ auf **Herunterladen** und dann auf **Ausführen**.
    
5. Klicken Sie auf der Seite **Willkommen bei Azure AD Connect** auf **Ich stimme zu** und dann auf **Weiter**.
    
6. Klicken Sie auf der Seite **Express-Einstellungen** auf **Express-Einstellungen verwenden**.
    
7. Geben Sie auf der Seite **Mit Azure AD verbinden** unter **Benutzername** den Namen Ihres globalen Administratorkontos und unter **Kennwort** das zugehörige Kennwort ein. Klicken Sie dann auf **Weiter**.
    
8. Geben Sie auf der Seite **Mit AD DS verbinden** den Namen **CORP\\Benutzer1** unter **Benutzername** und das zugehörige Kennwort unter **Kennwort** ein. Klicken Sie dann auf **Weiter**.
    
9. Klicken Sie auf der Seite **Azure AD-Anmeldungskonfiguration** auf **Ohne überprüfte Domänen fortfahren**, und dann auf **Weiter**.
    
10. Klicken Sie auf der Seite **Bereit zur Konfiguration** auf **Installieren**.
    
11. Klicken Sie auf der Seite **Konfiguration abgeschlossen** auf **Beenden**.
    
12. Wechseln Sie im Internet Explorer zum Office 365-Portal ([https://portal.office.com](https://portal.office.com)), und melden Sie sich bei Ihrem Office 365-Testabonnement mit Ihrem globalen Administratorkonto an.
    
13. Klicken Sie auf der Hauptportalseite auf **Admin**.
    
14. Klicken Sie im linken Navigationsbereich auf **Benutzer > Aktive Benutzer**.
    
    Sie sehen das Konto **Benutzer1**. Dieses Konto gehört zur Windows Server AD-Domäne „CORP“. Dass es angezeigt wird, belegt, dass die Verzeichnissynchronisierung erfolgreich war.
    
15. Klicken Sie auf das Konto**Benutzer1**. Für Produktlizenzen klicken Sie auf **Bearbeiten**.
    
16. Wählen Sie unter **Product licenses** Ihr Land/Ihre Region aus, und klicken Sie dann für **Office 365 Enterprise E5** auf **Off**. (So schalten Sie die Lizenz auf **On**.) Klicken Sie unten auf der Seite auf **Speichern** und dann auf **Schließen**.
    
Nachfolgend sehen Sie die daraus resultierende Konfiguration.
  
![Die Office 365-Entwicklungs-/Testumgebung mit Verzeichnissynchronisierung](media/be5b37b0-f832-4878-b153-436c31546e21.png)
  
Diese Konfiguration besteht aus:  
  
- Einem Office 365 E5-Testabonnement
- Einem vereinfachtem Unternehmensintranet mit Internetzugriff, das aus virtuellen DC1-, APP1- und CLIENT1-Computern in einem Subnetz eines virtuellen Azure-Netzwerks besteht. Azure AD Connect wird auf APP1 ausgeführt, um die CORP Windows Server Active Directory-Domäne mit Office 365 alle 30 Minuten zu synchronisieren.
    
## <a name="next-step"></a>Nächster Schritt

Wenn Sie die Verzeichnissynchronisierung für Ihre Organisation bereitstellen möchten, finden Sie unter [Bereitstellen der Office 365-Verzeichnissynchronisierung in Microsoft Azure](deploy-office-365-directory-synchronization-dirsync-in-microsoft-azure.md) entsprechende Informationen.

## <a name="see-also"></a>Siehe auch

[Testumgebungsanleitungen (TLGs) zur Cloudakzeptanz](cloud-adoption-test-lab-guides-tlgs.md)

[Basiskonfiguration der Entwicklungs-/Testumgebung](base-configuration-dev-test-environment.md)

[Office 365-Entwicklungs-/Testumgebung](office-365-dev-test-environment.md)

[Cloud App Security für Ihre Office 365-Entwicklungs-/Testumgebung](cloud-app-security-for-your-office-365-dev-test-environment.md)

[Advanced Threat Protection für die Office 365-Entwicklungs-/Testumgebung](advanced-threat-protection-for-your-office-365-dev-test-environment.md)

[Cloudakzeptanz und Hybridlösungen](cloud-adoption-and-hybrid-solutions.md)




