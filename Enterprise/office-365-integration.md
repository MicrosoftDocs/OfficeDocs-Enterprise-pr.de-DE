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
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "34069741"
---
# <a name="office-365-integration-with-on-premises-environments"></a>Office 365-Integration in lokale Umgebungen

Sie können Office 365 in Ihre vorhandenen Verzeichnisdienste und mit einer lokalen Installation von Exchange Server, Skype for Business Server 2015 oder SharePoint Server 2013 integrieren.
  
 - Bei der Integration in Verzeichnisdienste können Sie Benutzerkonten für beide Umgebungen synchronisieren und verwalten. Sie können auch die Kennworthash Synchronisierung oder einmaliges Anmelden (SSO) hinzufügen, damit Benutzer sich mit Ihren lokalen Anmeldeinformationen bei beiden Umgebungen anmelden können.
 - Bei der Integration in lokale Serverprodukte erstellen Sie eine Hybridumgebung. Eine Hybridumgebung kann bei der Migration von Benutzern oder Informationen zu Office 365 helfen, oder Sie können weiterhin einige Benutzer oder einige Informationen lokal und einige in der Cloud haben. Weitere Informationen zu Hybrid Umgebungen finden Sie unter [Office 365 Hybrid Cloud Solutions Overview](https://support.office.com/article/59616fab-acdb-40e9-b414-cf0c965c80b7).

Sie können die Azure AD Advisors auch für benutzerdefinierte Setup Hinweise verwenden:
- [Azure AD Connect Advisor](https://aka.ms/aadconnectpwsync)
- [AD FS-Bereitstellungs Ratgeber](https://aka.ms/adfsguidance)
- [Azure RMS-Bereitstellungs-Assistent](https://aka.ms/azuremsguidance)
- [Azure AD Premium-Setup-Handbuch](https://aka.ms/aadpguidance)
   
## <a name="before-you-begin"></a>Bevor Sie beginnen
Bevor Sie Office 365 und eine lokale Umgebung integrieren, müssen Sie auch an der [Netzwerkplanung und Leistungsoptimierung für Office 365](network-planning-and-performance.md)teilnehmen. Sie sollten auch die verfügbaren [Identitäts Modelle](about-office-365-identity.md) in Office 365 verstehen. 

Eine Liste der Tools, die Sie zum Verwalten von Office 365-Benutzern und-Konten verwenden können, finden Sie unter [wo Office 365-Benutzerkonten verwaltet](manage-office-365-accounts.md) werden. 
  
## <a name="integrate-office-365-with-directory-services"></a>Integrieren von Office 365 in Verzeichnisdienste
Wenn Sie über vorhandene Benutzerkonten in einem lokalen Verzeichnis verfügen, möchten Sie nicht alle diese Konten in Office 365 neu erstellen und Unterschiede oder Fehler zwischen den Umgebungen einführen. Mithilfe der Verzeichnissynchronisierung können Sie diese Konten zwischen Ihrer Online-und lokalen Umgebung spiegeln. Bei der Verzeichnissynchronisierung müssen sich die Benutzer keine neuen Informationen für jede Umgebung merken, und Sie müssen Konten nicht zweimal erstellen oder aktualisieren. Sie müssen [Ihr lokales Verzeichnis](prepare-for-directory-synchronization.md) für die Verzeichnissynchronisierung vorbereiten, dies können Sie manuell ausführen oder das [IdFix-Tool](install-and-run-idfix.md) verwenden (das IdFix-Tool funktioniert nur mit Active Directory). 
  
![Verwenden der Verzeichnissynchronisierung zum Synchronisieren von lokalen und Online-Benutzerkontoinformationen](media/a64af0d0-9be6-46b1-8727-277e683abf5e.png)
  
Wenn Sie möchten, dass sich Benutzer bei Office 365 mit Ihren lokalen Anmeldeinformationen anmelden können, können Sie auch SSO konfigurieren. Mit SSO wird Office 365 so konfiguriert, dass es der lokalen Umgebung für die Benutzerauthentifizierung vertraut.
  
![Mit einmaligem Anmelden ist das gleiche Konto sowohl in der lokalen als auch in der Online Umgebung verfügbar.](media/d76235f2-8a53-405e-b8ef-dfa4cfc208b8.png)
  
Verschiedene Benutzerkonten Verwaltungstechniken bieten unterschiedliche Erfahrungen für Ihre Benutzer, wie in der folgenden Tabelle dargestellt.
 
### <a name="directory-synchronization-with-or-without-password-hash-synchronization-or-pass-through-authentication"></a>**Verzeichnissynchronisierung mit oder ohne Kennworthash Synchronisierung oder Pass-Through-Authentifizierung**
Ein Benutzer meldet sich bei seiner lokalen Umgebung mit seinem Benutzerkonto an. Wenn Sie zu Office 365 wechseln, müssen Sie sich erneut mit Ihrem Arbeits-oder Schulkonto anmelden (User@Domain.com). Der Benutzername ist in beiden Umgebungen identisch. Wenn Sie die Kennworthash Synchronisierung oder Pass-Through-Authentifizierung hinzufügen, hat der Benutzer dasselbe Kennwort für beide Umgebungen, muss diese Anmeldeinformationen jedoch bei der Anmeldung bei Office 365 erneut angeben. Die Verzeichnissynchronisierung mit Kennworthash Synchronisierung ist das am häufigsten verwendete Verzeichnis Synchronisierungsszenario.

Verwenden Sie Azure Active Directory Connect, um die Verzeichnissynchronisierung einzurichten. Anweisungen hierzu finden Sie unter [Einrichten der Verzeichnissynchronisierung für Office 365](set-up-directory-synchronization.md)und [Verwenden von Azure AD Connect mit Express-Einstellungen](https://go.microsoft.com/fwlink/p/?LinkId=698537).

Erfahren Sie mehr über die [Vorbereitung der Bereitstellung von Benutzern über die Verzeichnissynchronisierung in Office 365](prepare-for-directory-synchronization.md) und [die Integration Ihrer lokalen identifiziert mit Azure Active Directory](https://go.microsoft.com/fwlink/?LinkId=518101).

### <a name="directory-synchronization-with-sso"></a>**Verzeichnissynchronisierung mit SSO**
Ein Benutzer meldet sich mit seinem Benutzerkonto bei seiner lokalen Umgebung an. Wenn Sie Office 365 besuchen, werden Sie entweder automatisch angemeldet oder melden sich mit denselben Anmeldeinformationen an, die Sie für Ihre lokale Umgebung (Domäne \ Benutzername) verwenden.

Zum Einrichten von SSO verwenden Sie auch Azure AD Connect. Weitere Informationen finden Sie unter [Verwenden von Azure AD Connect mit benutzerdefinierten Einstellungen](https://go.microsoft.com/fwlink/p/?LinkID=698430).

Weitere Informationen finden Sie [unter Anwendungszugriff und einmaliges Anmelden mit Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=698604).

## <a name="azure-ad-connect"></a>Azure AD Connect
Azure AD Connect ersetzt ältere Versionen von Identitäts Integrationstools wie Dirsync und Azure AD Sync. Weitere Informationen finden Sie unter [integrieren Ihrer lokalen Identitäten in Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=527969). Informationen zum Aktualisieren von Azure Active Directory-Synchronisierung mit Azure AD Connect finden Sie in [den Anweisungen zum Upgrade](https://go.microsoft.com/fwlink/p/?LinkId=733240). Sehen Sie sich eine Lösungsarchitektur an, die für die [Office 365-Verzeichnissynchronisierung (Dirsync) in Microsoft Azure](https://go.microsoft.com/fwlink/?LinkId=517887)erstellt wurde.