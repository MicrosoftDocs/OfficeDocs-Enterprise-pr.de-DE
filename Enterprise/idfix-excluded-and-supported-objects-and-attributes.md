---
title: Ausgeschlossene und unterstützte Objekte und Attribute für IdFix
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
ms.collection:
- Ent_O365
- M365-identity-device-management
ms.assetid: cc453ae5-fa9b-4836-b0ce-c7e824b1e36d
description: Listet die Attribute auf, die vom IdFix-Tool ausgeschlossen und unterstützt werden.
ms.openlocfilehash: d6b7aac023e9fe96b8308483322e718937ab1355
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/30/2019
ms.locfileid: "33487181"
---
# <a name="idfix-excluded-and-supported-objects-and-attributes"></a>Ausgeschlossene und unterstützte Objekte und Attribute für IdFix
Es gibt zwei Regelsätze, die von IdFix verwaltet werden. Multi-Tenant und Dedicated/ITAR. Zu diesem Zeitpunkt schließen die beiden Regelsätze dieselben Objekte, Attribute und Attributwerte aus der Suche aus. Dies kann sich in zukünftigen Versionen ändern.
  
## <a name="multi-tenant-and-dedicated-error-exclusions-used-by-idfix"></a>Mit mehreren Mandanten und dedizierten Fehler Ausschlüssen, die von IdFix verwendet werden
In diesem Abschnitt werden die Objekte, Attribute und Werte aufgelistet, die von der Suche des Verzeichnisses IdFix ausgeschlossen werden. Das Sternchen (\*) ist ein Platzhalter, der andere Zeichen ersetzen kann.
  
### <a name="objects-attributes-and-values-excluded-during-an-idfix-search"></a>Objekte, Attribute und Werte, die während einer IdFix-Suche ausgeschlossen sind

|**Ausschluss**|**Beispiel**|
|:-----|:-----|
|Administrator\* |Administrator |
|CAS_ {\*  |CAS_ {fe35fc98e69e4d08} |
|DiscoverySearchMailbox\*  |DiscoverySearchMailbox  |
|FederatedEmail\* |FederatedEmail. *GUID* |
|Gast\* ||
|HTTPConnector\*  |HTTPConnector |
|krbtgt\* |ms-DS-KrbTgt-Link |
|IUSR\* |IUSR_- *MachineName* |
|IWAM\*  |IWAM_- *MachineName* |
|MSOL\* |MSOL_AD_SYNC |
|Support\* ||
|System\* |System { *GUID* }|
|WWIOadmini\*  ||
|\*$ ||
|distinguishedName enthält "\0ACNF:"|"\0ACNF: *GUID* " |
|Objekt enthält das IsCriticalSystemObject-Attribut |Weitere Informationen finden Sie unter [Attribut isCriticalSystemObject](https://go.microsoft.com/fwlink/p/?LinkId=401169). |
   
## <a name="multi-tenant-and-dedicated-objects-and-attributes-checked-by-idfix"></a>Mehrinstanzenfähige und dedizierte Objekte und Attribute, die von IdFix überprüft wurden
Die Attribute, die von IdFix auf Fehler überprüft werden, werden im Abschnitt "Verzeichnisobjekt-und Attribut Vorbereitung" unter [Vorbereiten von Verzeichnisattributen für die Synchronisierung mit Office 365 mithilfe des IdFix-Tools](prepare-directory-attributes-for-synch-with-idfix.md)beschrieben.
  

