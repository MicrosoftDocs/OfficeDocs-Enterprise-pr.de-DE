---
title: Ausgeschlossene und unterstützte Objekte und Attribute für IdFix
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: reference
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
- MOE150
f1.keywords:
- CSH
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
ms.assetid: cc453ae5-fa9b-4836-b0ce-c7e824b1e36d
description: Listet die Attribute auf, die vom IdFix-Tool ausgeschlossen und unterstützt werden.
ms.openlocfilehash: da9a59d60b1ae2f1f68803e5a10afba16207fc69
ms.sourcegitcommit: d2a3d6eeeaa07510ee94c2bc675284d893221a95
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2020
ms.locfileid: "44711575"
---
# <a name="idfix-excluded-and-supported-objects-and-attributes"></a>Ausgeschlossene und unterstützte Objekte und Attribute für IdFix

*Dieser Artikel bezieht sich sowohl auf Microsoft 365 Enterprise als auch auf Office 365 Enterprise.*

Es gibt zwei Regelsätze, die von IdFix verwaltet werden; Multi-Mandanten-und dedizierte/ITAR. Zu diesem Zeitpunkt schließen die beiden Regelsätze dieselben Objekte, Attribute und Attributwerte aus der Suche aus. Dies kann sich in zukünftigen Versionen ändern.
  
## <a name="multi-tenant-and-dedicated-error-exclusions-used-by-idfix"></a>Von IdFix verwendete mehrmandantenfähige und dedizierte fehlerausschlüsse
In diesem Abschnitt werden die Objekte, Attribute und Werte aufgelistet, die von IdFix aus der Suche im Verzeichnis ausgeschlossen werden. Das Sternchen ( \* ) ist ein Platzhalter, der für andere Zeichen ersetzt werden kann.
  
### <a name="objects-attributes-and-values-excluded-during-an-idfix-search"></a>Während einer IdFix-Suche ausgeschlossene Objekte, Attribute und Werte

|**Ausschluss**|**Beispiel**|
|:-----|:-----|
|Administrator\* |Administrator |
|CAS_ {\*  |CAS_ {fe35fc98e69e4d08} |
|DiscoverySearchMailbox\*  |DiscoverySearchMailbox  |
|FederatedEmail\* |FederatedEmail. *GUID* |
|Gast\* ||
|HttpConnector\*  |HttpConnector |
|krbtgt\* |ms-DS-KrbTgt-Link |
|iusr_\* |IUSR_ *MachineName* |
|IWAM\*  |IWAM_ *MachineName* |
|MSOL\* |MSOL_AD_SYNC |
|support_\* ||
|System\* |System { *GUID* }|
|WWIOadmini\*  ||
|\*$ ||
|distinguishedName enthält "\0ACNF:"|"\0ACNF: *GUID* " |
|Objekt enthält das IsCriticalSystemObject-Attribut |Siehe [Attribute isCriticalSystemObject](https://go.microsoft.com/fwlink/p/?LinkId=401169). |
   
## <a name="multi-tenant-and-dedicated-objects-and-attributes-checked-by-idfix"></a>Mehrinstanzenfähige und dedizierte Objekte und Attribute, die von IdFix überprüft wurden
Die Attribute, die von IdFix auf Fehler überprüft werden, werden im Abschnitt "Verzeichnisobjekt-und Attribut Vorbereitung" unter [Prepare Directory attributes for Synchronization with Microsoft 365 mithilfe des IdFix-Tools](prepare-directory-attributes-for-synch-with-idfix.md)beschrieben.
  

