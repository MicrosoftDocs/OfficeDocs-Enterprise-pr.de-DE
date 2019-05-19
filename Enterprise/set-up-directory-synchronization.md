---
title: Einrichten der Verzeichnissynchronisierung für Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
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
description: Hier erfahren Sie, wie Sie die Verzeichnissynchronisierung zwischen Office 365 und Ihrem lokalen Active Directory einrichten.
ms.openlocfilehash: 1798c54854bc5ecc82481aaabca3690e7212e135
ms.sourcegitcommit: 36e760407a1f4b18bc108134628ed9a8d3e35a8a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2019
ms.locfileid: "34162478"
---
# <a name="set-up-directory-synchronization-for-office-365"></a>Einrichten der Verzeichnissynchronisierung für Office 365

Office 365 verwendet einen Azure Active Directory (Azure AD)-Mandanten, um Identitäten für die Authentifizierung und Berechtigungen für den Zugriff auf Cloud-basierte Ressourcen zu speichern und zu verwalten. 

Wenn Sie über eine lokale Active Directory-Domänendienste (AD DS) verfügen, können Sie Ihre AD DS Benutzerkonten, Gruppen und Kontakte mit dem Azure AD-Mandanten Ihres Office 365 Abonnements synchronisieren. Dies ist eine hybride Identität für Office 365. Hier sind die Komponenten.

![](./media/about-office-365-identity/hybrid-identity.png)

Azure AD Connect wird auf einem lokalen Server ausgeführt und synchronisiert Ihre AD DS mit dem Azure AD Mandanten. Neben der Verzeichnissynchronisierung können Sie auch diese Authentifizierungsoptionen angeben:

- Kennworthash Synchronisierung (PHS)

  Azure AD führt die Authentifizierung selbst aus.

- Passthrough-Authentifizierung (PTA)

  Azure Ad die Authentifizierung AD DS durchführen.

- Verbundauthentifizierung

  Azure AD umleitet den Clientcomputer, der die Authentifizierung anfordert, um einen anderen Identitätsanbieter zu kontaktieren.

Weitere [](plan-for-directory-synchronization.md) Informationen finden Sie unter hybride Identitäten.
  
## <a name="1-review-prerequisites-for-azure-ad-connect"></a>1. Überprüfen der Voraussetzungen für Azure AD Connect

Sie erhalten ein kostenloses Azure AD-Abonnement mit Ihrem Office 365-Abonnement. Wenn Sie die Verzeichnissynchronisierung einrichten, installieren Sie Azure AD Connect auf einem Ihrer lokalen Server.
  
Für Office 365 müssen Sie Folgendes tun:
  
- Überprüfen Sie Ihre lokale Domäne. Der Assistent für Azure AD Connect führt Sie durch diesen Leitfaden.
- Rufen Sie die Benutzernamen und Kennwörter für die Administratorkonten Ihres Office 365 Mandanten und AD DS ab.

Für den lokalen Server, auf dem Sie Azure AD Connect installieren, benötigen Sie Folgendes:
  
|**Server Betriebssystem**|**Weitere Software**|
|:-----|:-----|
|Windows Server 2012 R2 und höher | -PowerShell wird standardmäßig installiert, es ist keine Aktion erforderlich.  <br> -NET 4.5.1 und höhere Versionen werden über Windows Update angeboten. Stellen Sie sicher, dass Sie die neuesten Updates für Windows Server in der Systemsteuerung installiert haben. |
|Windows Server 2008 R2 mit Service Pack 1 (SP1) * * oder Windows Server 2012 | – Die neueste Version von PowerShell steht in Windows Management Framework 4,0 zur Verfügung. Suchen Sie im [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996)danach.  <br> -.NET 4.5.1 und höhere Versionen sind im [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996)verfügbar. |
|Windows Server 2008 | – Die neueste unterstützte Version von PowerShell steht in Windows Management Framework 3,0 zur Verfügung, das im [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996)verfügbar ist.  <br> -.NET 4.5.1 und höhere Versionen sind im [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996)verfügbar. |

Unter [Voraussetzungen für Azure Active Directory Connect](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-prerequisites) finden Sie Informationen zu Hardware-, Software-, Konto-und Berechtigungsanforderungen, SSL-Zertifikatanforderungen und Objekt Grenzwerten für Azure AD Connect.
  
Sie können auch den [Versionsverlauf von](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-version-history) Azure AD Connect überprüfen, um zu sehen, was in jeder Version enthalten und behoben ist.

## <a name="2-install-azure-ad-connect-and-configure-directory-synchronization"></a>2. installieren Azure AD verbinden und Konfigurieren der Verzeichnissynchronisierung

Bevor Sie beginnen, sollten Sie Folgendes sicherstellen:

- Der Benutzername und das Kennwort eines Office 365 globalen Administrators
- Der Benutzername und das Kennwort eines AD DS Domänenadministrators
- Welche Authentifizierungsmethode (PHS, PTA, Verbund)
- Ob Sie [Azure AD nahtloses einmaliges Anmelden (Single Sign-on, SSO)](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-sso) verwenden möchten

Führen Sie die folgenden Schritte aus:

1. Melden Sie sich beim [Microsoft 365 Admin Center](https://admin.microsoft.com) anhttps://admin.microsoft.com) (und wählen Sie in der linken Navigationsleiste **Benutzer** \> **aktive Benutzer** aus.
2. Wählen Sie im Admin Center auf der Seite **aktive Benutzer** die Option **Weitere** \> **Verzeichnissynchronisierung**aus.

    ![Wählen Sie im Menü weitere die Option Verzeichnissynchronisierung aus.](media/dc6669e5-c01b-471e-9cdf-04f5d44e1c4b.png)
  
3. Klicken Sie auf der Seite **Active Directory Vorbereitung** auf den Link **Download Microsoft Azure Active Directory Connect Tool** , um erste Schritte zu erhalten. 
4. Befolgen Sie die Schritte unter [Azure AD Roadmap Connect and Azure AD Connect Health Installation](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-roadmap).

## <a name="3-finish-setting-up-domains"></a>3. Abschließen der Einrichtung von Domänen

Befolgen Sie die Schritte unter [Erstellen von DNS-Einträgen für Office 365 beim Verwalten Ihrer DNS-Einträge](https://support.office.com/article/b0f3fdca-8a80-4e8e-9ef3-61e8a2a9ab23) , um die Einrichtung ihrer Domänen abzuschließen.

## <a name="next-step"></a>Nächster Schritt

[Zuweisen von Lizenzen zu Benutzerkonten](assign-licenses-to-user-accounts.md).
