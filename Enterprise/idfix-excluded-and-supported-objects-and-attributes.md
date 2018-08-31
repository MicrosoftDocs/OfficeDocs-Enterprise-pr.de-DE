---
title: IdFix ausgeschlossene und unterstützte Objekte und Attribute
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2016
ms.audience: Admin
ms.topic: reference
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.custom: Adm_O365
ms.assetid: cc453ae5-fa9b-4836-b0ce-c7e824b1e36d
description: Werden die Attribute aufgeführt, die ausgeschlossen und von IdFix-Tools unterstützt werden.
ms.openlocfilehash: de8d57bb8ad9a3097ec9da3ff2a485095a140a42
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540870"
---
# <a name="idfix-excluded-and-supported-objects-and-attributes"></a>IdFix ausgeschlossene und unterstützte Objekte und Attribute
Es gibt zwei durch IdFix gewartete Regelsätze: mehrinstanzenfähig und dediziert/ITAR. Derzeit schließen die zwei Regelsätze dieselben Objekte, Attribute und Attributwerte aus der Suche aus. Dies kann sich in zukünftigen Versionen ändern.
  
## <a name="multi-tenant-and-dedicated-error-exclusions-used-by-idfix"></a>Durch IdFix verwendete mehrinstanzenfähige und dedizierte Fehlerausschlüsse
Dieser Abschnitt enthält die Objekte, Attribute und Werte, die von der Suche des Verzeichnisses IdFix ausschließt. Das Sternchen (\*) ist ein Platzhalter, der für andere Zeichen ersetzt werden kann.
  
### <a name="objects-attributes-and-values-excluded-during-an-idfix-search"></a>Während einer IdFix-Suche ausgeschlossene Objekte, Attribute und Werte

|**Ausschluss**|**Beispiel**|
|:-----|:-----|
|Gefährdeten\* |Administrator |
|{CAS_\*  |CAS_{fe35fc98e69e4d08} |
|DiscoverySearchMailbox\*  |DiscoverySearchMailbox  |
|FederatedEmail\* |FederatedEmail. *GUID* |
|Gast\* ||
|HTTPConnector\*  |HTTPConnector |
|KRBTGT\* |ms-DS-KrbTgt-Link |
|IUSR_\* |IUSR_ *Computername* |
|IWAM\*  |IWAM_ *Computername* |
|msol\* |MSOL_AD_SYNC |
|Support_\* ||
|SystemMailbox\* |SystemMailbox { *GUID* }|
|WWIOadmini\*  ||
|\*$ ||
|DistinguishedName enthält "\0ACNF:"|"\0ACNF: *GUID* " |
|Objekt enthält das "IsCriticalSystemObject"-Attribut |Siehe [Attribut "isCriticalSystemObject"](https://go.microsoft.com/fwlink/p/?LinkId=401169). |
   
## <a name="multi-tenant-and-dedicated-objects-and-attributes-checked-by-idfix"></a>Durch IdFix überprüfte mehrinstanzenfähige und dedizierte Objekte und Attribute
Die Attribute, die durch IdFix auf Fehler überprüft werden, werden im Abschnitt "Directory-Objekt und die attributvorbereitung" in [die Freigabe Vorbereiten von Verzeichnisattributen für die Synchronisierung mit Office 365 mithilfe des IdFix-Tools](prepare-directory-attributes-for-synch-with-idfix.md)beschrieben.
  

