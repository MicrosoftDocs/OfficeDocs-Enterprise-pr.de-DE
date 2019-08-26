---
title: Office 365-Integration in lokale Umgebungen
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
search.appverid:
- MET150
- LYN150
- SPS150
- MOE150
- MED150
ms.assetid: 263faf8d-aa21-428b-aed3-2021837a4b65
description: Erfahren Sie, wie Sie Office 365 in Ihre vorhandenen Verzeichnisdienste integrieren.
ms.openlocfilehash: 1fa044a0a9db0d8422239cf301fea21a2c3d47e9
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "34069741"
---
# <a name="office-365-integration-with-on-premises-environments"></a>Office 365-Integration in lokale Umgebungen

Sie können Office 365 in Ihre vorhandenen Verzeichnisdienste und eine lokale Installation für Exchange Server, Skype for Business Server 2015 oder SharePoint Server 2013 integrieren.
  
 - Wenn Sie die Integration in die Verzeichnisdienste durchführen, können Sie Benutzerkonten für beide Umgebungen synchronisieren und verwalten. Sie können auch die Kennworthashsynchronisierung oder das einmalige Anmelden (Single Sign-on, SSO) hinzufügen, damit sich die Benutzer mit Ihren lokalen Anmeldeinformationen bei beiden Umgebungen anmelden können.
 - Bei der Integration in lokale Serverprodukte erstellen Sie eine Hybridumgebung. Eine Hybridumgebung kann hilfreich für Sie sein, wenn Sie Benutzer oder Informationen nach Office 365 migrieren. Sie können aber auch weiterhin einige Benutzer oder einige Informationen lokal und einige in der Cloud verwalten. Weitere Informationen zu Hybridumgebungen finden Sie unter [Übersicht über die Office 365-Lösungen für die Hybridcloud](https://support.office.com/article/59616fab-acdb-40e9-b414-cf0c965c80b7).

Sie können auch die Azure AD-Ratgeber für Anleitungen zur benutzerdefinierten Einrichtung verwenden:
- [Azure AD Connect-Ratgeber](https://aka.ms/aadconnectpwsync)
- [Bereitstellungsratgeber für AD FS](https://aka.ms/adfsguidance)
- [Bereitstellungs-Assistent für Azure RMS](https://aka.ms/azuremsguidance)
- [Einrichtungsleitfaden für Azure AD Premium](https://aka.ms/aadpguidance)
   
## <a name="before-you-begin"></a>Bevor Sie beginnen
Bevor Sie Office 365 in eine lokale Umgebung integrieren, müssen Sie auch die [Netzwerkplanung und Leistungsoptimierung für Office 365](network-planning-and-performance.md) vornehmen. Außerdem ist es wichtig, dass Sie die verfügbaren [Identitätsmodelle](about-office-365-identity.md) in Office 365 verstehen. 

Eine Liste der Tools, mit denen Sie Office 365-Benutzer und -Konten verwalten können, finden Sie unter [Wo Office 365-Benutzerkonten verwaltet werden](manage-office-365-accounts.md). 
  
## <a name="integrate-office-365-with-directory-services"></a>Integration von Office 365 in Verzeichnisdienste
Wenn Sie über vorhandene Benutzerkonten in einem lokalen Verzeichnis verfügen, möchten Sie nicht alle diese Konten in Office 365 neu erstellen und riskieren, dass zwischen den Umgebungen Unterschiede oder Fehler auftreten. Mithilfe der Verzeichnissynchronisierung können Sie diese Konten zwischen der Onlineumgebung und der lokalen Umgebung spiegeln. Bei der Verzeichnissynchronisierung müssen sich die Benutzer nicht neue Informationen zu jeder Umgebung merken, und Sie brauchen die Konten nicht zweimal zu erstellen oder zu aktualisieren. Sie müssen [Ihr lokales Verzeichnis für die Verzeichnissynchronisierung vorbereiten](prepare-for-directory-synchronization.md). Sie können dies manuell tun oder das [IdFix-Tool](install-and-run-idfix.md) verwenden (das IdFix-Tool funktioniert nur mit Active Directory). 
  
![Mit Verzeichnissynchronisierung sorgen Sie dafür, dass die Informationen für lokale und Online-Benutzerkonten synchronisiert bleiben](media/a64af0d0-9be6-46b1-8727-277e683abf5e.png)
  
Um den Benutzern zu ermöglichen, sich mit Ihren lokalen Anmeldeinformationen bei Office 365 anzumelden, können Sie auch SSO konfigurieren. Bei SSO wird Office 365 so konfiguriert, dass es der lokalen Umgebung für die Benutzerauthentifizierung vertraut.
  
![Bei der einmaligen Anmeldung steht dasselbe Konto in der lokalen und der Onlineumgebung zur Verfügung.](media/d76235f2-8a53-405e-b8ef-dfa4cfc208b8.png)
  
Unterschiedliche Techniken der Benutzerkontenverwaltung bieten Ihren Benutzern unterschiedliche Erfahrungen, wie in der nachstehenden Tabelle gezeigt wird.
 
### <a name="directory-synchronization-with-or-without-password-hash-synchronization-or-pass-through-authentication"></a>**Verzeichnissynchronisierung mit oder ohne Kennworthashsynchronisierung oder Passthrough-Authentifizierung**
Ein Benutzer meldet sich mit seinem Benutzerkonto (domäne\benutzername) bei seiner lokalen Umgebung an. Wenn er zu Office 365 wechselt, muss er sich mit Ihrem Geschäfts-, Schul- oder Unikonto (benutzer@domäne.com) erneut anmelden. Der Benutzername ist in beiden Umgebungen identisch. Wenn Sie Kennworthashsynchronisierung oder Passthrough-Authentifizierung hinzufügen, besitzt der Benutzer dasselbe Kennwort für beide Umgebungen, muss aber diese Anmeldeinformationen erneut bereitstellen, wenn er sich bei Office 365 anmeldet. Verzeichnissynchronisierung mit Kennworthashsynchronisierung ist das am häufigsten verwendete Szenario der Verzeichnissynchronisierung.

Verwenden Sie Azure Active Directory Connect, um die Verzeichnissynchronisierung einzurichten. Anweisungen finden Sie unter [Einrichten der Verzeichnissynchronisierung für Office 365](set-up-directory-synchronization.md) und [Verwenden von Azure AD Connect mit Expresseinstellungen](https://go.microsoft.com/fwlink/p/?LinkId=698537).

Erfahren Sie mehr über das [Vorbereiten der Bereitstellung von Benutzern über die Verzeichnissynchronisierung für Office 365](prepare-for-directory-synchronization.md) und das [Integrieren Ihrer lokalen Identitäten in Azure Active Directory](https://go.microsoft.com/fwlink/?LinkId=518101).

### <a name="directory-synchronization-with-sso"></a>**Verzeichnissynchronisierung mit SSO**
Ein Benutzer meldet sich mit seinem Benutzerkonto bei seiner lokalen Umgebung an. Wenn er zu Office 365 wechselt, wird er entweder automatisch angemeldet, oder er meldet sich mit denselben Anmeldeinformationen wie für seine lokale Umgebung ("domäne\benutzername") an.

Zum Einrichten von SSO verwenden Sie ebenfalls Azure Active Directory Connect. Entsprechende Anleitungen finden Sie unter [Verwenden von Azure AD Connect mit benutzerdefinierten Einstellungen](https://go.microsoft.com/fwlink/p/?LinkID=698430).

Erfahren Sie mehr über [Anwendungszugriff und einmaliges Anmelden mit Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=698604).

## <a name="azure-ad-connect"></a>Azure AD Connect
Azure Active Directory Connect ersetzt ältere Versionen von Identitätsintegrationstools wie Azure Active Directory-Synchronisierungstool (DirSync) und Azure Active Directory-Synchronisierungsdienste (AAD Sync). Weitere Informationen finden Sie unter [Integrieren Ihrer lokalen Identitäten in Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=527969). Informationen zum Aktualisieren von Azure Active Directory-Synchronisierung auf Azure AD Connect finden Sie in den [Aktualisierungsanweisungen](https://go.microsoft.com/fwlink/p/?LinkId=733240). Eine Lösungsarchitektur finden Sie unter [Office 365 Verzeichnissynchronisierung (DirSync) in Microsoft Azure](https://go.microsoft.com/fwlink/?LinkId=517887).