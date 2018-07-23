---
title: Registrieren von iOS- und Android-Geräten in Ihrer Entwicklungs-/Testumgebung für Microsoft 365 Enterprise
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/20/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_TLGs
ms.assetid: 49c7758a-1c01-4153-9b63-5eae3f6305ce
description: 'Zusammenfassung: Mit diesem Test Lab Guide können Geräte in Ihrer Microsoft 365 Dev/Test-Umgebung zu registrieren und Remote zu verwalten.'
ms.openlocfilehash: e4b8491a70d0d0177e0a434d228136243201e788
ms.sourcegitcommit: c3869a332512dd1cc25cd5a92a340050f1da0418
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/20/2018
ms.locfileid: "20720411"
---
# <a name="enroll-ios-and-android-devices-in-your-microsoft-365-enterprise-devtest-environment"></a>Registrieren von iOS- und Android-Geräten in Ihrer Entwicklungs-/Testumgebung für Microsoft 365 Enterprise

 **Zusammenfassung:** Verwenden Sie diese Test Lab Guide zum Registrieren von Geräten in Ihrer Microsoft 365 Dev/Test-Umgebung und Remote zu verwalten.
  
Der Microsoft Enterprise Mobilität Suite zur Abstimmung verhindert, dass Ihre Mitarbeiter produktiv mithilfe ihrer bevorzugten apps und -Geräte beim Schützen von Daten der Organisation. Weitere Informationen finden Sie unter [Enterprise Mobilität + Sicherheit (zur Abstimmung)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security).
  
Wenn Sie Sicherheit auf Device-Ebene anwenden möchten, müssen Sie in Microsoft Intune Geräte registrieren. Gerät-Registrierung können Sie zum Verwalten von Geräten im Besitz der Organisation nicht nur aber auch persönlich (BYOD) und gemeinsam genutzten Geräten, abhängig von Ihrer Organisation rechtliche der Richtlinien.
  
Gemäß die Anweisungen in diesem Artikel benötigen Sie möglicherweise registrieren und grundlegende Mobilgerät Management-Funktionen für iOS und Android-Geräte in Ihrer Microsoft 365 Test-/Umgebung testen.
  
## <a name="phase-1-create-your-microsoft-365-devtest-environment"></a>Phase 1: Erstellen der Microsoft-365 Dev/Test-Umgebung

Befolgen Sie die Anweisungen in [The Microsoft 365 Enterprise Test-/Umgebung](the-microsoft-365-enterprise-dev-test-environment.md)aus.
  
## <a name="phase-2-enroll-your-ios-and-android-devices"></a>Phase 2: Registrieren Sie Ihre iOS und Android-Geräte

Verwenden Sie zunächst die Anweisungen in [Installieren und melden Sie sich die app Unternehmensportal](https://docs.microsoft.com/intune-user-help/install-and-sign-in-to-the-intune-company-portal-app-ios) zum Anpassen von Microsoft Intune Unternehmensportal-app für Ihre testumgebung.

Im nächsten Schritt verwenden Sie die Anweisungen in [Richten Sie Ihre Unternehmensressourcen zugreifen,](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios) einer iOS-Geräte zu registrieren.

Im nächsten Schritt verwenden Sie die Anweisungen in [Registrieren Ihrer Android-Gerät im Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-android) Android-Gerät zu registrieren.

## <a name="phase-3-manage-your-ios-and-android-devices-remotely"></a>Phase 3: Verwalten Sie Ihrer iOS und Android-Geräte Remote

Bietet Microsoft Intune remote sperren und die Kennung Funktionen zurückgesetzt. Wenn eine Person ihr Gerät verliert, können Sie das Gerät Remote sperren. Wenn eine Person ihre Kennung vergisst, können Sie es Remote zurücksetzen.
  
Um eine IOS- oder Android-Gerät remote zu sperren:

1. Melden Sie sich bei der Azure-Portal unter [https://portal.azure.com](https://portal.azure.com) mit den Anmeldeinformationen Ihres Kontos globaler Administrator.
2. Klicken Sie auf **alle Dienste**, geben Sie **Intune**, und klicken Sie dann auf **Intune**.
3. Klicken Sie auf **Geräte > alle Geräte**.
4. Klicken Sie in der Liste der Geräte auf eine IOS- oder Android-Gerät, und klicken Sie dann auf die Aktion **Remote Sperren** .

    
So setzen Sie den Zugangscode remote zurück

1. Falls erforderlich, melden Sie sich bei der Azure-Portal unter [https://portal.azure.com](https://portal.azure.com) mit den Anmeldeinformationen Ihres Kontos globaler Administrator.
2. Klicken Sie auf **alle Dienste**, geben Sie **Intune**, und klicken Sie dann auf **Intune**.
3. Klicken Sie auf **Geräte > alle Geräte**.
4. Aus der Liste der Geräte verwalten, klicken Sie auf eine IOS- oder Android-Gerät und wählen Sie **... Weitere**. Wählen Sie dann die **Kennung entfernen** Gerät remote-Aktion aus.

Weitere Versuche finden Sie unter [verfügbare Gerät Aktionen](https://docs.microsoft.com/intune/device-management#available-device-actions).

    

> [!TIP]
> Klicken Sie [hier](http://aka.ms/catlgstack), um eine visuelle Darstellung aller Artikel im Stapel der Testumgebungsanleitungen in der Microsoft Cloud zu erhalten.
  
## <a name="see-also"></a>Siehe auch

[Die Microsoft 365 Enterprise-Entwicklungs-/Testumgebung](the-microsoft-365-enterprise-dev-test-environment.md)
  
[Richtlinien für die Microsoft 365 Enterprise Test-/Umgebung MAM](mam-policies-for-your-microsoft-365-enterprise-dev-test-environment.md)
  
[Testumgebungsanleitungen (TLGs) zur Cloudakzeptanz](cloud-adoption-test-lab-guides-tlgs.md)

[Enterprise-Mobilität + Sicherheit (zur Abstimmung)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)


