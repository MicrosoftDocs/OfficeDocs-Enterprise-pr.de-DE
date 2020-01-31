---
title: Deaktivieren der Verzeichnissynchronisierung für Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED150
ms.assetid: ee5f861e-bd48-4267-83d1-a4ead4b4a00d
description: Informationen zum Deaktivieren der Verzeichnissynchronisierung für Office 365 mithilfe von PowerShell
ms.openlocfilehash: efee8b216d63f32ac64a559aca3bcb55b0a933c1
ms.sourcegitcommit: 3ed7b1eacf009581a9897524c181afa3e555ad3f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/28/2020
ms.locfileid: "41570892"
---
# <a name="turn-off-directory-synchronization-for-office-365"></a>Deaktivieren der Verzeichnissynchronisierung für Office 365
Sie können die Verzeichnissynchronisierung mithilfe von PowerShell deaktivieren. Es wird jedoch nicht empfohlen, die Verzeichnissynchronisierung als Schritt zur Problembehandlung zu deaktivieren. Wenn Sie Unterstützung bei der Problembehandlung bei der Verzeichnissynchronisierung benötigen, lesen Sie die Informationen unter [Beheben von Problemen mit der Verzeichnissynchronisierung für Office 365](fix-problems-with-directory-synchronization.md) Artikel. 
  
[Wenden Sie sich](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) bei Bedarf an den Support für Business-Produkte.
  
## <a name="turn-off-directory-synchronization"></a>Deaktivieren der Verzeichnissynchronisierung  
So deaktivieren Sie die Verzeichnissynchronisierung:
  
1. Installieren Sie zunächst die erforderliche Software, und stellen Sie eine Verbindung mit Ihrem Office 365 Abonnement her. Anweisungen finden Sie unter [Connect with the Microsoft Azure Active Directory Module for Windows PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).
    
2. Verwenden Sie die [Option "MsolDirSyncEnabled](https://go.microsoft.com/fwlink/p/?LinkId=821939) ", um die Verzeichnissynchronisierung zu deaktivieren: 
    
  ```powershell
  Set-MsolDirSyncEnabled -EnableDirSync $false
  ```
