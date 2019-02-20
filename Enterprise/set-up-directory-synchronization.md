---
title: Planen der Verzeichnissynchronisierung für Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.audience: Admin
ms.topic: get-started-article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED15
- MBS150
- BCS160
ms.assetid: 1b3b5318-6977-42ed-b5c7-96fa74b08846
description: Erfahren Sie, wie Sie die Verzeichnissynchronisierung zwischen Office 365 und Ihrem lokalen Active Directory einrichten.
ms.openlocfilehash: 5f6e5be2a2137ee183a7d592d9a3e6b086e5be9a
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085264"
---
# <a name="set-up-directory-synchronization-for-office-365"></a>Planen der Verzeichnissynchronisierung für Office 365

In Office 365 wird der Cloud-basierte Benutzer Identitäts Verwaltungsdienst Azure Active Directory zum Verwalten von Benutzern verwendet. Sie können Ihr lokales Active Directory auch mit Azure AD integrieren, indem Sie Ihre lokale Umgebung mit Office 365 synchronisieren. Nachdem Sie die Synchronisierung eingerichtet haben, können Sie entscheiden, ob die Benutzerauthentifizierung innerhalb von Azure AD oder in Ihrem lokalen Verzeichnis erfolgen soll.
  
## <a name="office-365-directory-synchronization"></a>Office 365-Verzeichnissynchronisierung

Sie können entweder eine synchronisierte Identität oder eine Verbundidentität zwischen Ihrer lokalen Organisation und Office 365 verwenden. Mit synchronisierter Identität verwalten Sie Ihre Benutzer lokal und werden von Azure AD authentifiziert, wenn Sie das gleiche Kennwort in der Cloud als lokal verwenden. Dies ist das häufigste Szenario für die Verzeichnissynchronisierung. Mit der Passthrough-Authentifizierung oder der Verbundidentität können Sie Ihre Benutzer lokal verwalten und durch Ihr lokales Verzeichnis authentifizieren. Die Verbundidentität erfordert eine zusätzliche Konfiguration und ermöglicht es den Benutzern, sich nur einmal anzumelden. Weitere Informationen finden Sie unter [understandIng Office 365 Identity und Azure Active Directory](about-office-365-identity.md).
  
## <a name="want-to-upgrade-from-windows-azure-active-directory-sync-dirsync-to-azure-active-directory-connect"></a>Möchten Sie ein Upgrade von Windows Azure Active Directory Sync (dirSync) auf Azure Active Directory Connect durchführen?

Wenn Sie derzeit dirSync verwenden und ein Upgrade durchführen möchten, wechseln Sie zu [Azure.com](https://azure.com) . [](https://go.microsoft.com/fwlink/p/?LinkId=733240)
  
## <a name="prerequisites-for-azure-ad-connect"></a>VoraussetZungen für Azure AD Connect

Sie erhalten ein kostenloses Abonnement für Azure AD mit Ihrem Office 365-Abonnement. Wenn Sie die Verzeichnissynchronisierung einrichten, installieren Sie Azure Active Directory Connect auf einem Ihrer lokalen Server.
  
Für Office 365 müssen Sie Folgendes tun:
  
- ÜberPrüfen Sie Ihre lokale Domäne (das Verfahren führt Sie durch.)
- [Weisen Sie Administratorrollen in office 365 for Business](https://support.office.com/article/EAC4D046-1AFD-4F1A-85FC-8219C79E1504) -Berechtigungen für ihren Office 365-Mandanten und ein lokales Active Directory zu.

Für den lokalen Server, auf dem Sie Azure AD Connect installieren, benötigen Sie die folgende Software:
  
|**Server Betriebssystem**|**Weitere Software**|
|:-----|:-----|
|**Windows Server 2012 R2** | -PowerShell wird standardmäßig installiert, es ist keine Aktion erforderlich.  <br> -NET 4.5.1 und späteren Versionen werden über Windows Update angeboten. Stellen Sie sicher, dass Sie die neuesten Updates für Windows Server in der Systemsteuerung installiert haben. |
|**Windows server 2008 R2 mit Service Pack 1 (SP1)** oder **Windows Server 2012** | -Die neueste Version von PowerShell ist in Windows Management Framework 4,0 verfügbar. Suchen Sie im [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996)danach.<br> -.NET 4.5.1 und neuere Versionen sind im [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996)verfügbar. |
|**Windows Server 2008** | -Die neueste unterstützte Version von PowerShell ist in Windows Management Framework 3,0 verfügbar, verfügbar im [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).  <br> -.NET 4.5.1 und neuere Versionen sind im [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996)verfügbar. |

> [!NOTE]
> Wenn Sie Azure Active Directory dirSync verwenden, beträgt die maximale Anzahl von Verteilergruppenmitgliedern, die Sie von Ihrem lokalen Active Directory mit Azure Active Directory synchronisieren können, 15.000. Für Azure AD Connect ist diese Nummer 50.000. 
  
Lesen Sie die [vorausSetzungen für Azure Active Directory Connect](https://go.microsoft.com/fwlink/p/?LinkId=716896), um die Anforderungen an Hardware, Software, Konten und Berechtigungen, SSL-Zertifikatanforderungen und Objekt Grenzwerte für Azure AD Connect genauer zu prüfen.
  
Sie können auch den [Versionsverlauf](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-version-history) der Azure AD Connect-Version überprüfen, um zu sehen, was in jeder Version enthalten und korrigiert wurde.

## <a name="to-set-up-directory-synchronization"></a>So richten Sie die Verzeichnissynchronisierung ein

1. melden sie sich beim Office 365 admin center an, und wählen sie im linken navigationsbereich **benutzer** \> **aktive benutzer** aus.
2. wählen sie im Office 365 admin center auf der seite **aktive benutzer** **mehr** \> **verzeichnissynchronisierung**aus.

    ![Wählen Sie im Menü mehr die Option Verzeichnissynchronisierung aus.](media/dc6669e5-c01b-471e-9cdf-04f5d44e1c4b.png)
  
3. Wählen Sie auf der Seite **Active Directory-Vorbereitung** den Link zum **herunterladen des Microsoft Azure Active Directory Connect-Tool** für erste Schritte aus. Weitere Informationen zum Installieren von Azure Active Directory Connect finden Sie unter [Azure AD Connect and Azure AD Connect Health Installation Roadmap](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-roadmap).

## <a name="assign-licenses-to-synchronized-users"></a>Zuweisen von Lizenzen zu synchronisierten Benutzern

Nachdem Sie Ihre Benutzer mit Office 365 synchronisiert haben, werden Sie erstellt, aber Sie müssen Ihnen Lizenzen zuweisen, damit Sie Office 365-Features wie e-Mail verwenden können. Anweisungen hierzu finden Sie unter [Zuweisen von Lizenzen zu Benutzern in Office 365 for Business](https://support.office.com/article/997596b5-4173-4627-b915-36abac6786dc).

## <a name="finish-setting-up-domains"></a>Abschließen der Einrichtung von Domänen

Führen Sie die Schritte unter [Create DNS Records for Office 365 aus, wenn Sie Ihre DNS-Einträge verwalten](https://support.office.com/article/b0f3fdca-8a80-4e8e-9ef3-61e8a2a9ab23) , um die Einrichtung ihrer Domänen abzuschließen.