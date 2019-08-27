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
description: Sie erfahren, wie Sie die Verzeichnissynchronisierung zwischen Office 365 und dem lokalen Active Directory einrichten.
ms.openlocfilehash: 1798c54854bc5ecc82481aaabca3690e7212e135
ms.sourcegitcommit: 36e760407a1f4b18bc108134628ed9a8d3e35a8a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2019
ms.locfileid: "34162478"
---
# <a name="set-up-directory-synchronization-for-office-365"></a>Einrichten der Verzeichnissynchronisierung für Office 365

Office 365 verwendet einen Azure Active Directory-Mandanten (Azure AD) zum Speichern und Verwalten von Identitäten für die Authentifizierung und Berechtigung zum Zugriff auf Cloud-basierte Ressourcen. 

Wenn Sie über lokale Active Directory Domain Services (AD DS) verfügen, können Sie Ihre AD DS-Benutzerkonten, -Gruppen und -Kontakte mit dem Azure AD-Mandanten Ihres Office 365-Abonnements synchronisieren. Dies ist Hybrididentität für Office 365. Dies sind ihre Komponenten.

![](./media/about-office-365-identity/hybrid-identity.png)

Azure AD Connect wird auf einem lokalen Server ausgeführt und synchronisiert Ihre AD DS mit dem Azure AD-Mandanten. Zusammen mit der Verzeichnissynchronisierung können Sie auch die folgenden Authentifizierungsoptionen angeben:

- Kennworthashsynchronisierung (Password hash synchronization, PHS)

  Azure AD führt die Authentifizierung selbst durch.

- Passthrough-Authentifizierung (PTA)

  Azure AD lässt AD DS die Authentifizierung durchführen.

- Verbundauthentifizierung

  Azure AD leitet den Clientcomputer um, der die Authentifizierung anfordert, um einen anderen Identitätsanbieter zu kontaktieren.

Weitere Informationen finden Sie unter [Hybrididentitäten](plan-for-directory-synchronization.md).
  
## <a name="1-review-prerequisites-for-azure-ad-connect"></a>1. Voraussetzungen für Azure AD Connect überprüfen

Sie erhalten ein kostenloses Azure AD-Abonnement mit Ihrem Office 365-Abonnement. Wenn Sie die Verzeichnissynchronisierung einrichten, installieren Sie Azure AD Connect auf einem Ihrer lokalen Server.
  
Für Office 365 müssen Sie:
  
- Ihre lokale Domäne hinzufügen. Der Azure AD Connect-Assistent führt Sie schrittweise durch diesen Vorgang.
- Die Benutzernamen und Kennwörter für die Administratorkonten Ihres Office 365-Mandanten und AD DS bereithalten.

Für Ihren lokalen Server, auf dem Sie Azure AD Connect installieren, benötigen Sie Folgendes:
  
|**Server-Betriebssystem**|**Weitere Software**|
|:-----|:-----|
|Windows Server 2012 R2 oder neuer | – PowerShell wird standardmäßig installiert, keine Aktion erforderlich.  <br> – .NET 4.5.1 und höhere Versionen werden über Windows Update bereitgestellt. Vergewissern Sie sich in der Systemsteuerung, dass die neuesten Updates für Windows Server installiert sind. |
|Windows Server 2008 R2 mit Service Pack 1 (SP1)** oder Windows Server 2012 | – Die neueste Version von PowerShell finden Sie im Windows Management Framework 4.0. Suchen Sie im [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996) danach.  <br> – .NET 4.5.1 und höhere Versionen finden Sie im [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996). |
|Windows Server 2008 | – Die neueste unterstützte Version von PowerShell befindet sich im Windows Management Framework 3.0, das Sie aus dem [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996) herunterladen können.  <br> – .NET 4.5.1 und höhere Versionen finden Sie im [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996). |

Zusätzliche Informationen zur Hardware, Software, Anforderungen an Konten, Berechtigungen und SSL Zertifikate sowie zu Objekteinschränkungen für Azure AD Connect finden Sie unter [Voraussetzungen für Azure Active Directory Connect](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-prerequisites).
  
Sie können auch den [Versionsveröffentlichungsverlauf](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-version-history) von Azure AD Connect verfolgen, um zu sehen, welche Features und Funktionen in jeder Version enthalten sind und welche Fehler behoben wurden.

## <a name="2-install-azure-ad-connect-and-configure-directory-synchronization"></a>2. Installieren von Azure AD Connect und Konfigurieren der Verzeichnissynchronisierung

Bevor Sie beginnen, sollten Sie sicherstellen, dass Sie über Folgendes verfügen:

- Den Benutzernamen und das Kennwort eines globalen Office 365-Administrators
- Den Benutzernamen und das Kennwort des AD-DS-Domänenadministrators.
- Welche Authentifizierungsmethode (PHS, PTA, Federated)
- Ob Sie [Azure AD Seamless Single Sign-On (SSO) verwenden möchten](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-sso)

Führen Sie die folgenden Schritte aus:

1. Melden Sie sich beim [Microsoft 365 Admin Center](https://admin.microsoft.com) an, (https://admin.microsoft.com) und wählen Sie im linken Navigationsbereich **Benutzer** \> ** Aktive Benutzer** aus.
2. Wählen Sie im Admin Center auf der Seite **Aktive Benutzer** die Option **Weitere** \> **Verzeichnissynchronisierung** aus.

    ![Wählen Sie im Menü "Mehr" die Option "Verzeichnissynchronisierung" aus](media/dc6669e5-c01b-471e-9cdf-04f5d44e1c4b.png)
  
3. Wählen Sie auf der Seite **Active Directory-Vorbereitung** den Link **Microsoft Azure Active Directory Connect Tool herunterladen** aus, um mit den ersten Schritte zu beginnen. 
4. Folgen Sie den Schritten in [Installationsübersicht: Azure AD Connect und Azure AD Connect Health](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-roadmap).

## <a name="3-finish-setting-up-domains"></a>3. Abschließen der Einrichtung von Domänen

Folgen Sie den Schritten unter [Erstellen von DNS-Einträgen für Office 365, wenn Sie Ihre DNS-Einträge verwalten](https://support.office.com/article/b0f3fdca-8a80-4e8e-9ef3-61e8a2a9ab23), um die Einrichtung Ihrer Domäne abzuschließen.

## <a name="next-step"></a>Nächster Schritt

[Zuweisen von Lizenzen zu Benutzerkonten](assign-licenses-to-user-accounts.md).
