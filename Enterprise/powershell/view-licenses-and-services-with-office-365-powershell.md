---
title: Anzeigen von Lizenzen und Diensten mit Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/20/2018
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
description: Erläutert, wie Sie Office 365 PowerShell, zum Anzeigen von Informationen zu Lizenzierung Pläne, Dienste und Lizenzen, die in Office 365-Organisation verfügbar sind.
ms.openlocfilehash: 400af224f7c74d72a173fa4ea45ede4d6057bbf7
ms.sourcegitcommit: 3b474e0b9f0c12bb02f8439fb42b80c2f4798ce1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="view-licenses-and-services-with-office-365-powershell"></a>Anzeigen von Lizenzen und Diensten mit Office 365 PowerShell

**Zusammenfassung:** Erläutert, wie Sie Office 365 PowerShell, zum Anzeigen von Informationen zu Lizenzierung Pläne, Dienste und Lizenzen, die in Office 365-Organisation verfügbar sind.
  
Jeder Office 365-Abonnement umfasst die folgenden Elemente:

- **Lizenzierung von Plänen** Diese werden auch Aslicense Pläne oder Office 365-Pläne bezeichnet. Lizenzierungspläne definieren die Office 365-Dienste, die Benutzern zur Verfügung stehen. Office 365-Abonnement kann mehrere lizenzierungspläne enthalten. Ein Lizenzierungsplan Beispiel wäre Office 365 Enterprise E3.
    
- **Dienste** Dies sind auch bekannte Asservice Pläne. Dienste sind die Office 365-Produkte, Features und Funktionen, die in jedem Lizenzierungsplan verfügbar sind beispielsweise Exchange Online und Office Professional Plus. Benutzer können mehrere Lizenzen aus verschiedenen lizenzierungspläne, die Zugriff auf verschiedene Dienste gewähren zugewiesen wurde.
    
- **Lizenzen** Jede Lizenzierungsplan enthält die Anzahl der Lizenzen, die Sie erworben haben. Sie zuweisen Benutzern Lizenzen, sodass diese Office 365-Dienste verwenden können, die durch den Lizenzierungsplan definiert sind. Jedes Benutzerkonto erfordert mindestens eine Lizenz von einem Lizenzierungsplan, damit sie melden Sie sich bei Office 365 und die Dienste verwenden können.
    
Office 365 PowerShell können Sie Details zu den verfügbaren lizenzierungspläne, Lizenzen und Dienste in Office 365-Organisation anzeigen. Weitere Informationen zu den Produkten, Features und Dienste, die in verschiedenen Office 365-Abonnements verfügbar sind, finden Sie unter [Planen der Office 365-Produkten](https://go.microsoft.com/fwlink/p/?LinkId=691147).

## <a name="before-you-begin"></a>Bevor Sie beginnen

- Für die Verfahren in diesem Thema müssen Sie eine Verbindung mit Office 365 PowerShell herstellen. Weitere Anweisungen finden Sie unter [Verbinden mit Office 365 PowerShell](connect-to-office-365-powershell.md).
    
- Ein PowerShell-Skript ist verfügbar, die die in diesem Thema beschriebenen Verfahren automatisiert. Insbesondere ermöglicht das Skript anzeigen und Deaktivieren von Diensten in Office 365-Organisation, einschließlich Schlingern. Weitere Informationen finden Sie unter [Deaktivieren des Zugriffs auf Schlingern mit Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).
    
## <a name="view-information-about-licensing-plans-and-the-available-licenses"></a>Anzeigen von Informationen zu Lizenzierungsplänen und den verfügbaren Lizenzen

Um zusammenfassende Informationen zu Ihrer aktuellen Pläne Lizenzierung und den verfügbaren Lizenzen für jeden Plan anzuzeigen, führen Sie in Office 365 PowerShell den folgenden Befehl aus:
  
```
Get-MsolAccountSku
```

Die Ergebnisse enthalten die folgenden Informationen:
  
- **AccountSkuId:** Anzeigen der verfügbaren lizenzierungspläne für Ihre Organisation mithilfe der Syntax `<CompanyName>:<LicensingPlan>`.  _<CompanyName>_ ist der Wert, der Sie bereitgestellt werden, wenn Sie in Office 365 registriert, und für Ihre Organisation eindeutig ist. Die _<LicensingPlan>_ Wert gilt für alle Benutzer. Beispielsweise in den Wert `litwareinc:ENTERPRISEPACK`, den Namen des Unternehmens ist `litwareinc`, und den Namen der Lizenzierung Plan `ENTERPRISEPACK`, dies ist der Systemname für Office 365 Enterprise E3.
    
- **ActiveUnits:** Anzahl der Lizenzen, dass Einkäufe für eine bestimmte Lizenzierungsplan haben.
    
- **WarningUnits:** Anzahl der Lizenzen in einer Lizenzierungsplan, die Sie noch nicht erneuert und läuft, die nach der 30-Tage-Nachfrist.
    
- **ConsumedUnits:** Anzahl der Lizenzen, die Sie den Benutzer aus einer bestimmten Lizenzierungsplan zugewiesen haben.
    
Um Details zu Office 365-Dienste anzuzeigen, die in allen Ihre Lizenz Pläne verfügbar sind, führen Sie den folgenden Befehl aus:
  
```
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

Die folgende Tabelle zeigt die Office 365-Dienstplänen und ihren Anzeigenamen für die am häufigsten verwendeten Dienste. Die Liste der Servicepläne kann unterschiedlich sein. Eine vollständige Liste der Dienste und deren Anzeigenamen wenden Sie sich an [Office – Support](https://support.office.com/home/contact).
  
|**Dienstplan**|**Beschreibung**|
|:-----|:-----|
| `SWAY` <br/> |Sway  <br/> |
| `TEAMS1` <br/> |Microsoft Teams  <br/> |
| `YAMMER_ENTERPRISE` <br/> |Yammer  <br/> |
| `RMS_S_ENTERPRISE` <br/> |Azure-Rechteverwaltung (RMS)  <br/> |
| `OFFICESUBSCRIPTION` <br/> |Office Professional Plus  <br/> |
| `MCOSTANDARD` <br/> |Skype for Business Online  <br/> |
| `SHAREPOINTWAC` <br/> |Office Online  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |SharePoint Online  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |Exchange Online Plan 2  <br/> |
   
Verwenden Sie die folgende Syntax, um Details zu Office 365-Dienste anzuzeigen, die in einer bestimmten Lizenzierungsplan verfügbar sind.
  
```
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "<AccountSkuId>"}).ServiceStatus
```

Dieses Beispiel zeigt die Office 365-Dienste, die in den Lizenzierungsplan litwareinc: enterprisepack (Office 365 Enterprise E3) zur Verfügung stehen.
  
```
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "litwareinc:ENTERPRISEPACK"}).ServiceStatus
```

## <a name="new-to-office-365"></a>Neu bei Office 365?

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   
## <a name="see-also"></a>Siehe auch

- [Anzeigen lizenzierter und nicht lizenzierter Benutzer mit Office 365 PowerShell](view-licensed-and-unlicensed-users-with-office-365-powershell.md)
- [Anzeigen von Lizenz- und Dienstdetails für Konten mit Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md)
- [Get-MsolAccountSku](https://go.microsoft.com/fwlink/p/?LinkId=691549)

