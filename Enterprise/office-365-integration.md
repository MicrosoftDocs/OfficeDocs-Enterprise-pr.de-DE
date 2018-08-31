---
title: Office 365-Integration in lokalen Umgebungen
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- LYN150
- SPS150
- MOE150
- MED150
ms.assetid: 263faf8d-aa21-428b-aed3-2021837a4b65
description: Hier erfahren Sie, wie Office 365 mit Ihrer vorhandenen Verzeichnisdiensten integriert.
ms.openlocfilehash: b660dda74303a3bf0fa92bc8e3146cd2c9add662
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540882"
---
# <a name="office-365-integration-with-on-premises-environments"></a>Office 365-Integration in lokalen Umgebungen

Sie können Office 365 mit Ihrer vorhandenen Verzeichnisdiensten und mit einer lokalen Installation von Exchange Server, Skype für Business Server 2015 oder SharePoint Server 2013 integrieren.
  
 - Wenn Sie mithilfe von Verzeichnisdiensten integrieren, können Sie synchronisieren und verwaltet Benutzerkonten für beide Umgebungen. Sie können auch hinzufügen Hash kennwortsynchronisierung oder einmaliges Anmelden (SSO), sodass Benutzer anmelden können bei beiden Umgebungen mit ihren lokalen Anmeldeinformationen.
 - Wenn Sie mit der lokale Serverprodukte integrieren, erstellen Sie eine hybridumgebung. Migrieren Sie Benutzer oder Informationen zu Office 365, oder Sie können auch weiterhin einige Benutzer oder einige Informationen lokale und einige in der Cloud haben, kann eine hybridumgebung helfen. Weitere Informationen zu hybridumgebungen finden Sie unter [Übersicht über Office 365 Hybriden Cloud-Lösungen](https://support.office.com/article/59616fab-acdb-40e9-b414-cf0c965c80b7).

Sie können auch die Azure AD-Berater für angepasste Setup-Anleitung verwenden:
- [Azure Active Directory verbinden advisor](https://aka.ms/aadconnectpwsync)
- [AD FS-Bereitstellung advisor](https://aka.ms/adfsguidance)
- [Azure RMS-Bereitstellungs-Assistenten](https://aka.ms/azuremsguidance)
- [Azure AD Premium Setup-Anleitung](https://aka.ms/aadpguidance)
   
## <a name="before-you-begin"></a>Bevor Sie beginnen
Bevor Sie Office 365 und einer lokalen Umgebung integrieren, müssen Sie auch für die Teilnahme an [netzwerkplanung](network-planning-and-performance.md)und leistungsoptimierung für Office 365. Sie sollten auch die verfügbaren [Identität Modelle](about-office-365-identity.md) in Office 365 zu verstehen. 

Finden Sie unter [, in denen Konten zum Verwalten von Office 365-Benutzer](manage-office-365-accounts.md) eine Liste der Tools, die Sie zum Verwalten von Office 365-Benutzern und Konten verwenden können. 
  
## <a name="integrate-office-365-with-directory-services"></a>Integrieren von Office 365 mithilfe von Verzeichnisdiensten
Wenn Sie vorhandene Benutzerkonten in einem lokalen Verzeichnis haben, möchten Sie nicht alle diese Konten in Office 365 und des Risikomanagements Einführung in die Unterschiede oder Fehler zwischen den Umgebungen neu zu erstellen. Directory-Synchronisierung können Sie diese Konten zwischen Ihrer online spiegeln und lokalen Umgebungen. Mit der verzeichnissynchronisierung die Benutzer müssen keine neuen Informationen für jede Umgebung Denken Sie daran, und Sie erstellen oder aktualisieren zweimal Konten müssen nicht. Sie müssen für die verzeichnissynchronisierung [Vorbereiten des lokalen Verzeichnisses](prepare-for-directory-synchronization.md) , Sie können dies manuell vornehmen, oder verwenden Sie das [IdFix-Tool](install-and-run-idfix.md) (IdFix-Tool funktioniert nur mit Active Directory). 
  
![Mit der lokalen und online Benutzerkontoinformationen synchronisiert halten Directory-Synchronisierung](media/a64af0d0-9be6-46b1-8727-277e683abf5e.png)
  
Wenn Sie Benutzer mit ihren lokalen Anmeldeinformationen zu Office 365 anmelden werden sollen, können Sie auch SSO konfigurieren. Mit SSO ist Office 365 so konfiguriert, dass die lokale Umgebung für die Benutzerauthentifizierung vertrauen.
  
![Einmaliges Anmelden ist dasselbe Konto in der lokalen und online-Umgebung verfügbaren](media/d76235f2-8a53-405e-b8ef-dfa4cfc208b8.png)
  
Anderer Benutzer Konto Techniken bereitzustellen unterschiedliche Erfahrungen für Ihre Benutzer, wie in der folgenden Tabelle dargestellt.
 
### <a name="directory-synchronization-with-or-without-password-hash-synchronization-or-pass-through-authentication"></a>**Directory-Synchronisierung mit oder ohne Kennwort Hash Synchronisierung oder Pass-Through-Authentifizierung**
Ein Benutzer meldet sich bei ihrer lokalen Umgebung mit ihr Konto (Domäne\Benutzername). Wenn sie auf Office 365 zugreifen, müssen sie erneut ihre Arbeit oder Schule-Konto (user@domain.com) anmelden. Der Benutzername ist in beiden Umgebungen identisch. Wenn Sie Hash kennwortsynchronisierung oder Pass-Through-Authentifizierung hinzufügen, wird der Benutzer hat das gleiche Kennwort für beide Umgebungen, jedoch muss diese Anmeldeinformationen erneut bereitstellen, bei der Anmeldung bei Office 365. Directory-Synchronisierung mit kennwortsynchronisierung Hash ist die am häufigsten verwendeten Directory Sync-Szenario.

Verwenden Sie zum Einrichten der verzeichnissynchronisierung Azure Active Directory verbinden. Lesen Sie Anweisungen [Directory-Synchronisierung für Office 365 einrichten](set-up-directory-synchronization.md)und [verwenden Azure AD Verbinden mit den express-Einstellungen](https://go.microsoft.com/fwlink/p/?LinkId=698537).

Weitere Informationen zum [Vorbereiten der Bereitstellung von Benutzern durch verzeichnissynchronisierung zu Office 365](prepare-for-directory-synchronization.md) und [Integrieren von Ihrer lokalen identifiziert mit Azure Active Directory](https://go.microsoft.com/fwlink/?LinkId=518101).

### <a name="directory-synchronization-with-sso"></a>**Directory-Synchronisierung mit SSO**
Ein Benutzer meldet sich bei ihrer lokalen Umgebung mit ihr Konto. Wenn sie auf Office 365 zugreifen, sind entweder Anmeldung automatisch, oder sie melden Sie sich mit den gleichen Anmeldeinformationen, die sie für ihre lokale Umgebung (Domäne\Benutzername) verwenden.

Zum Einrichten von SSO verwenden Sie auch Azure Active Directory verbinden. Eine Anleitung, lesen Sie [verwenden Azure AD Verbinden mit benutzerdefinierten Einstellungen](https://go.microsoft.com/fwlink/p/?LinkID=698430).

Erfahren Sie mehr über [Zugriff auf die Anwendung und einmaliges Anmelden mit Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=698604).

## <a name="azure-ad-connect"></a>Azure AD Connect
Azure Active Directory verbinden ersetzt ältere Versionen von Identity Integrationstools wie DirSync und Azure AD-Synchronisierung. Weitere Informationen finden Sie unter [Integration von Ihrer lokalen Identitäten mit Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=527969). Wenn Sie auf Azure AD-Verbinden von Azure Active Directory-Synchronisierung aktualisieren möchten, finden Sie unter [den Upgradeanweisungen](https://go.microsoft.com/fwlink/p/?LinkId=733240). Finden Sie eine Lösungsarchitektur für [Office 365-Directory-Synchronisierung (DirSync) in Microsoft Azure](https://go.microsoft.com/fwlink/?LinkId=517887).