---
title: Vorbereiten von Domänen nicht-routingfähigen für Directory-Synchronisierung
ms.author: robmazz
author: robmazz
manager: laurawi
ms.audience: Admin
ms.topic: article
f1_keywords:
- O365E_SetupDirSyncLocalDir
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- BCS160
ms.assetid: e7968303-c234-46c4-b8b0-b5c93c6d57a7
description: Hier erfahren Sie, wie Sie vorgehen, wenn Sie verfügen über eine nicht Routale Domäne Ihre lokalen Benutzer zugeordnet ist, bevor Sie mit Office 365 synchronisieren.
ms.openlocfilehash: 9ec96c34e1dc4a6c755ea97fce3f5f2a5ba21bb3
ms.sourcegitcommit: 9c493c4e18e83491d106c5e9bab55d1a89298879
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/26/2018
ms.locfileid: "26674439"
---
# <a name="prepare-a-non-routable-domain-for-directory-synchronization"></a>Vorbereiten von Domänen nicht-routingfähigen für Directory-Synchronisierung
Wenn Sie Ihr lokales Verzeichnis mit Office 365 synchronisieren eine überprüfte Domäne in Azure Active Directory haben. Nur die User Principal Names (UPN), die mit der lokalen Domäne verknüpft sind, werden synchronisiert. Allerdings werden alle UPN, die eine nicht-routingfähigen Domäne, z. B. Local (wie billa@contoso.local), enthält zu synchronisiert eine. Domäne "onmicrosoft.com" (wie billa@contoso.onmicrosoft.com). 

Wenn Sie bereits eine Local-Domäne für Ihre Benutzerkonten in Active Directory wird empfohlen, dass Sie diese, um eine überprüften Domäne (wie billa@contoso.com) verwenden, um ordnungsgemäß Synchronisierung mit Office 365-Domäne ändern.
  
## <a name="what-if-i-only-have-a-local-on-premises-domain"></a>Was geschieht, wenn nur eine Local lokale Domäne ist vorhanden?

Das neueste Tool, das Sie verwenden können, für die Synchronisierung Ihrer Active Directory und Azure Active Directory heißt Azure Active Directory verbinden. Weitere Informationen finden Sie unter [Integration von Ihrer lokalen Identitäten mit Azure Active Directory](https://docs.microsoft.com/azure/architecture/reference-architectures/identity/azure-ad).
  
Verbinden von Azure Active Directory synchronisiert UPN und das Kennwort des Benutzers, damit Benutzer sich anmelden können sich mit denselben Anmeldeinformationen lokalen Verwendung. Azure Active Directory verbinden synchronisiert jedoch nur Benutzer auf Domänen, die von Office 365 überprüft werden. Dies bedeutet, dass die Domäne auch von Azure Active Directory überprüft worden ist, da Office 365 Identitäten von Azure Active Directory verwaltet werden. Anders ausgedrückt, muss die Domäne einen gültigen Internet-Domänennamen (z. B. .com, org, .net, US usw.) sein. Wenn der internen Active Directory nur eine nicht-routingfähigen Domäne (beispielsweise Local) verwendet wird, darf nicht dies möglicherweise die überprüfte Domäne übereinstimmen, die Sie in Office 365. Sie können dieses Problem beheben, indem Sie entweder die primäre Domäne in Ihre lokale Active Directory ändern oder durch eine oder mehrere UPN-Suffixe hinzufügen.
  
### <a name="change-your-primary-domain"></a>**Ändern Sie Ihre primäre Domäne**

Ändern Sie Ihre primäre Domäne in einer Domäne, die Sie in Office 365, beispielsweise "contoso.com" überprüft haben. Jeder Benutzer mit der Domäne contoso.local klicken Sie dann auf "contoso.com" aktualisiert. Weitere Informationen finden Sie unter [Domäne umbenennen Funktionsweise](https://go.microsoft.com/fwlink/p/?LinkId=624174). Dies ist ein sehr Vorgang, jedoch und eine einfachere Lösung [Hinzufügen UPN Suffixe und Aktualisieren von Benutzern für diese](prepare-a-non-routable-domain-for-directory-synchronization.md#bk_register), wie im folgenden Abschnitt dargestellt.
  
### <a name="add-upn-suffixes-and-update-your-users-to-them"></a>**UPN-Suffixen hinzufügen und Aktualisieren von Benutzern für diese**

Sie können das Local Problem lösen durch die Registrierung neue UPN-Suffix oder Suffixe in Active Directory und die Domäne (oder Domänen) übereinstimmen, die Sie in Office 365 überprüft. Nachdem Sie das neue Suffix registrieren, aktualisieren Sie den Benutzer UPNs der Local mit den neuen Domänennamen für Beispiel ersetzen, damit ein Benutzerkonto billa@contoso.com aussieht.
  
Nachdem Sie die Verwendung die überprüfte Domäne UPNs aktualisiert haben, können Sie Ihre lokale Active Directory mit Office 365 synchronisieren.
  
 **Schritt 1: Fügen Sie das neue UPN-Suffix hinzu**
  
1. Auf dem Server, die auf Active Directory-Domänendienste (AD DS) ausgeführt wird, wählen Sie im Server-Manager **Tools** \> **Active Directory-Domänen und -Vertrauensstellungen**.
    
    **Oder, falls Sie nicht über Windows Server 2012 verfügen**
    
    Drücken Sie die **Windows-Taste + R** , öffnen Sie das Dialogfeld **Ausführen** , und geben Sie in Domain.msc, und wählen Sie dann auf **OK**.
    
    ![Wählen Sie Active Directory-Domänen und -Vertrauensstellungen.](media/46b6e007-9741-44af-8517-6f682e0ac974.png)
  
2. Das Fenster **Active Directory-Domänen und-Vertrauensstellungen** Maustaste auf **Active Directory-Domänen und -Vertrauensstellungen**, und wählen Sie dann auf **Eigenschaften**.
    
    ![Mit der rechten Maustaste Active Directory-Domänen und -Vertrauensstellungen, und wählen Sie Eigenschaften](media/39d20812-ffb5-4ba9-8d7b-477377ac360d.png)
  
3. Klicken Sie auf der Registerkarte **Benutzerprinzipalnamen-Suffixe** im Feld **Alternative UPN-Suffixe** Geben Sie Ihre neue UPN-Suffix oder Suffixe, und wählen Sie dann **Hinzufügen** \> **Übernehmen**.
    
    ![Hinzufügen eines neuen UPN-Suffixes](media/a4aaf919-7adf-469a-b93f-83ef284c0915.PNG)
  
    Wählen Sie **OK** , wenn Sie das Hinzufügen von Suffixe fertig sind. 
    
 **Schritt 2: Ändern Sie das UPN-Suffix für vorhandene Benutzer**
  
1. Auf dem Server, die auf Active Directory-Domänendienste (AD DS) ausgeführt wird, wählen Sie im Server-Manager **Tools** \> **Active Directory Active Directory-Benutzer und-Computer**.
    
    **Oder, falls Sie nicht über Windows Server 2012 verfügen**
    
    Drücken Sie die **Windows-Taste + R** , öffnen Sie das Dialogfeld **Ausführen** , und geben Sie in den Befehl DSA.msc ein, und klicken Sie dann auf **OK**
    
2. Wählen Sie einen Benutzer mit der rechten Maustaste, und wählen Sie dann auf **Eigenschaften**.
    
3. Klicken Sie auf der Registerkarte **Konto** in der Dropdownliste UPN-Suffix wählen Sie das neue UPN-Suffix, und wählen Sie dann auf **OK**.
    
    ![Fügen Sie neue UPN-Suffix für einen Benutzer hinzu](media/54876751-49f0-48cc-b864-2623c4835563.png)
  
4. Führen Sie diese Schritte für jeden Benutzer.
    
    Alternativ können Sie gleichzeitig aktualisieren des UPN Suffixe [können Sie auch Windows PowerShell, um das UPN-Suffix für alle Benutzer zu ändern](prepare-a-non-routable-domain-for-directory-synchronization.md#BK_Posh).
    
### <a name="you-can-also-use-windows-powershell-to-change-the-upn-suffix-for-all-users"></a>**Sie können Windows PowerShell auch so ändern Sie das UPN-Suffix für alle Benutzer verwenden.**

Wenn Sie viele Benutzer aktualisiert haben, ist es einfacher, Windows PowerShell verwenden. Das folgende Beispiel verwendet die Cmdlets [Get-ADUser](https://go.microsoft.com/fwlink/p/?LinkId=624312) und [Set-ADUser](https://go.microsoft.com/fwlink/p/?LinkId=624313) , um alle contoso.local Suffixe in "contoso.com" zu ändern. 

Führen Sie die folgenden Windows PowerShell-Befehle, um alle contoso.local Suffixe auf "contoso.com" zu aktualisieren:
    
  ```
  $LocalUsers = Get-ADUser -Filter {UserPrincipalName -like '*contoso.local'} -Properties userPrincipalName -ResultSetSize $null
  ```

  ```
  $LocalUsers | foreach {$newUpn = $_.UserPrincipalName.Replace("contoso.local","contoso.com"); $_ | Set-ADUser -UserPrincipalName $newUpn}
  ```
Finden Sie unter [Active Directory Windows PowerShell-Modul](https://go.microsoft.com/fwlink/p/?LinkId=624314) erhalten Sie weitere Informationen zum Verwenden von Windows PowerShell in Active Directory. 

