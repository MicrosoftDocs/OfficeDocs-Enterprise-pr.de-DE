---
title: Anzeigen von Lizenzen und Diensten mit Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/03/2019
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- O365ITProTrain
- LIL_Placement
- PowerShell
ms.assetid: bb5260a9-a6a3-4f34-b19a-06c6699f6723
description: In diesem Artikel wird erläutert, wie Sie mithilfe von Office 365 PowerShell Informationen zu den Lizenzierungsplänen, Diensten und Lizenzen anzeigen können, die in Ihrer Office 365-Organisation verfügbar sind.
ms.openlocfilehash: f673ac984e504a740dfac474821366d34de5ccbc
ms.sourcegitcommit: a39d15b7cf758dfb262d2724bcfd283bba3d2ce1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/04/2019
ms.locfileid: "27730330"
---
# <a name="view-licenses-and-services-with-office-365-powershell"></a>Anzeigen von Lizenzen und Diensten mit Office 365 PowerShell

**Zusammenfassung:** In diesem Artikel wird erläutert, wie Sie mithilfe von Office 365 PowerShell Informationen zu den Lizenzierungsplänen, Diensten und Lizenzen anzeigen können, die in Ihrer Office 365-Organisation verfügbar sind.
  
Jedes Office 365-Abonnement besteht aus den folgenden Komponenten:

- **Lizenzierungspläne**: Diese werden auch als Lizenzpläne oder Office 365-Pläne bezeichnet. Lizenzierungspläne definieren die Office 365-Dienste, die für Benutzer verfügbar sind. Ihr Office 365-Abonnement kann mehrere Lizenzierungspläne enthalten. Ein Beispiel für einen Lizenzierungsplan ist Office 365 Enterprise E3.
    
- **Dienste**: Sie werden auch als Servicepläne bezeichnet. Dienste sind die Office 365-Produkte, -Features und -Funktionen, die jeweils in den verschiedenen Lizenzierungsplänen inbegriffen sind, zum Beispiel Exchange Online und Office Professional Plus. Benutzern können mehrere verschiedene Lizenzen aus unterschiedlichen Lizenzierungsplänen zugewiesen sein, über die sie Zugriff auf unterschiedliche Dienste haben.
    
- **Lizenzen**: Ein Lizenzierungsplan enthält die Anzahl von Lizenzen, die Sie erworben haben. Die Lizenzen weisen Sie Benutzern zu, damit sie die im Lizenzierungsplan definierten Office 365-Dienste nutzen können. Einem Benutzerkonto muss mindestens eine (1) Lizenz aus einem Lizenzierungsplan zugewiesen sein, damit der Benutzer sich mit dem Konto bei Office 365 anmelden und die Dienste nutzen kann.
    
Sie können Office 365 PowerShell verwenden, um Details zu den verfügbaren Lizenzierungsplänen, Lizenzen und Diensten in Ihrer Office 365-Organisation anzuzeigen. Weitere Informationen dazu, welche Produkte, Features und Dienste in den verschiedenen Office 365-Abonnements verfügbar sind, finden Sie unter [Optionen zum Office 365-Plan](https://go.microsoft.com/fwlink/p/?LinkId=691147).


## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Verwenden der Azure Active Directory PowerShell für Graph-Module

Verbinden Sie sich zuerst [mit Ihrem Office 365-Mandanten](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
  
Führen Sie den folgenden Befehl aus, um eine Übersicht über Ihre aktuellen Lizenzierungspläne und die in den einzelnen Plänen verfügbaren Lizenzen anzuzeigen:
  
```
Get-AzureADSubscribedSku | Select -Property Sku*,ConsumedUnits -ExpandProperty PrepaidUnits
```

Die Ergebnisse enthalten die folgenden Informationen:
  
- **SkuPartNumber:** Zeigt die verfügbaren Lizenzierungspläne für Ihre Organisation an. `ENTERPRISEPACK` ist z. B. der Systemname für Office 365 Enterprise E3.
    
- **Enabled:**: Gibt die Anzahl der Lizenzen an, die Sie im Rahmen eines spezifischen Lizenzierungsplans erworben haben.
    
- **ConsumedUnits**: Gibt die Anzahl der Lizenzen an, die Sie Benutzern aus einem bestimmten Lizenzierungsplan zugewiesen haben.
    
Zeigen Sie zunächst eine Liste Ihrer Lizenzierungspläne an, um Details zu allen verfügbaren Office 365-Diensten in Ihrem gesamten Lizenzplanbestand anzuzeigen.

````
Get-AzureADSubscribedSku | Select SkuPartNumber
````

Speichern Sie dann die Informationen zu den Lizenzplänen in einer Variablen.

````
$licenses = Get-AzureADSubscribedSku
````

Zeigen Sie die Dienste in einem spezifischen Lizenzplan an.

````
$licenses[<index>].ServicePlan
````

\<Index > ist eine ganze Zahl, die die Zeilennummer des Lizenzplans aus der Anzeige des `Get-AzureADSubscribedSku | Select SkuPartNumber`-Befehls minus 1 angibt.

Wenn die Anzeige des `Get-AzureADSubscribedSku | Select SkuPartNumber`-Befehls z.B. folgendermaßen lautet:

````
SkuPartNumber
-------------
WIN10_VDA_E5
EMSPREMIUM
ENTERPRISEPREMIUM
FLOW_FREE
````

Lautet der Befehl zum Anzeigen der Dienste für den Plan ENTERPRISEPREMIUM folgendermaßen:

````
$licenses[2].ServicePlan
````

ENTERPRISEPREMIUM ist die dritte Zeile. Aus diesem Grund wird der Indexwert mit (3 - 1) oder 2 angegeben.

Eine vollständige Liste von Lizenzplänen (auch bezeichnet als Produktnamen), deren enthaltenen Serviceplänen und die entsprechenden Anzeigenamen finden Sie unter [Produktnamen und Serviceplanbezeichner für die Lizenzierung](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Verwenden des Microsoft Azure Active Directory-Moduls für Windows PowerShell

Verbinden Sie sich zuerst [mit Ihrem Office 365-Mandanten](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

>[!Note]
>Ein PowerShell-Skript steht zur Verfügung, das die in diesem Thema erläuterten Verfahren automatisiert. Insbesondere ermöglicht das Skript Ihnen das Anzeigen und Deaktivieren von Diensten in Ihrer Office 365-Organisation, einschließlich Sway. Weitere Informationen finden Sie unter [Deaktivieren des Zugriffs auf Sway mit Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).
>
    
Führen Sie den folgenden Befehl aus, um eine Übersicht über Ihre aktuellen Lizenzierungspläne und die in den einzelnen Plänen verfügbaren Lizenzen anzuzeigen:
  
```
Get-MsolAccountSku
```

Die Ergebnisse enthalten die folgenden Informationen:
  
- **AccountSkuId:**: Zeigt die verfügbaren Lizenzierungspläne in Ihrer Organisation im Syntaxformat `<CompanyName>:<LicensingPlan>` an. _<CompanyName>_ ist der Wert, den Sie bei der Registrierung für Office 365 angegeben haben, und ist für Ihre Organisation eindeutig. Der Wert _<LicensingPlan>_ ist für alle Kunden derselbe. Beispiel: Im Wert `litwareinc:ENTERPRISEPACK` steht  `litwareinc` für den Namen des Unternehmens. `ENTERPRISEPACK` ist der Name des Lizenzierungsplan und gleichzeitig der Systemname für  Office 365 Enterprise E3.
    
- **ActiveUnits**: Gibt die Anzahl der Lizenzen an, die Sie im Rahmen eines spezifischen Lizenzierungsplans erworben haben.
    
- **WarningUnits**: Gibt die Anzahl der Lizenzen in einem Lizenzierungsplan an, die Sie nicht verlängert haben und die nach der 30-tägigen Toleranzperiode ablaufen werden.
    
- **ConsumedUnits**: Gibt die Anzahl der Lizenzen an, die Sie Benutzern aus einem bestimmten Lizenzierungsplan zugewiesen haben.
    
Führen Sie den folgenden Befehl aus, um Details zu allen verfügbaren Office 365-Diensten in Ihrem gesamten Lizenzplanbestand anzuzeigen:
  
```
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

In der folgenden Tabelle sind die Office 365-Servicepläne und Anzeigenamen der beliebtesten Dienste aufgeführt. Ihre individuelle Serviceplanliste sieht möglicherweise anders aus. 
  
|**Dienstplan**|**Beschreibung**|
|:-----|:-----|
| `SWAY` <br/> |Sway  <br/> |
| `TEAMS1` <br/> |Microsoft Teams  <br/> |
| `YAMMER_ENTERPRISE` <br/> |Yammer  <br/> |
| `RMS_S_ENTERPRISE` <br/> |Azure-Rechteverwaltung (Rights Management, RMS)  <br/> |
| `OFFICESUBSCRIPTION` <br/> |Office Professional Plus  <br/> |
| `MCOSTANDARD` <br/> |Skype for Business Online  <br/> |
| `SHAREPOINTWAC` <br/> |Office Online  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |SharePoint Online  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |Exchange Online Plan 2  <br/> |
   
Eine vollständige Liste von Lizenzplänen (auch bezeichnet als Produktnamen), deren enthaltenen Serviceplänen und die entsprechenden Anzeigenamen finden Sie unter [Produktnamen und Serviceplanbezeichner für die Lizenzierung](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).

Verwenden Sie die folgende Syntax, um Details zu den Office 365-Diensten anzuzeigen, die in einem spezifischen Lizenzierungsplan verfügbar sind.
  
```
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "<AccountSkuId>"}).ServiceStatus
```

Dieses Beispiel zeigt die Office 365-Dienste, die im Lizenzierungsplan litwareinc:ENTERPRISEPACK (Office 365 Enterprise E3) zur Verfügung stehen.
  
```
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "litwareinc:ENTERPRISEPACK"}).ServiceStatus
```


## <a name="new-to-office-365"></a>Neu bei Office 365?

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   
## <a name="see-also"></a>Siehe auch


[Verwalten von Benutzerkonten und Lizenzen mit Office 365 PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Verwalten von Office 365 mit Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Erste Schritte mit Office 365 PowerShell](getting-started-with-office-365-powershell.md)
