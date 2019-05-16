---
title: Vorbereiten einer nicht routingfähigen Domäne für die Verzeichnissynchronisierung
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
f1_keywords:
- O365E_SetupDirSyncLocalDir
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
- BCS160
ms.assetid: e7968303-c234-46c4-b8b0-b5c93c6d57a7
description: Erfahren Sie, was Sie tun müssen, wenn Sie über eine nicht-routale-Domäne verfügen, die Ihren lokalen Benutzern zugeordnet ist, bevor Sie mit Office 365 synchronisieren.
ms.openlocfilehash: 15ab67212ec1ea6ca7665bb5a4b0748f7d85adb5
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "34071081"
---
# <a name="prepare-a-non-routable-domain-for-directory-synchronization"></a>Vorbereiten einer nicht routingfähigen Domäne für die Verzeichnissynchronisierung
Wenn Sie Ihr lokales Verzeichnis mit Office 365 synchronisieren, müssen Sie über eine verifizierte Domäne in Azure Active Directory verfügen. Nur die Benutzerprinzipalnamen (UPN), die der lokalen Domäne zugeordnet sind, werden synchronisiert. Jeder UPN, der eine nicht Routingfähige Domäne enthält, beispielsweise. local (wie Billa @ contoso. local), wird mit einer. onmicrosoft.com-Domäne (wie Billa@contoso.onmicrosoft.com) synchronisiert. 

Wenn Sie derzeit eine lokale Domäne für ihre Benutzerkonten in Active Directory verwenden, wird empfohlen, diese so zu ändern, dass Sie eine verifizierte Domäne (wie Billa@contoso.com) verwenden, um ordnungsgemäß mit Ihrer Office 365-Domäne zu synchronisieren.
  
## <a name="what-if-i-only-have-a-local-on-premises-domain"></a>Was geschieht, wenn ich nur eine lokale lokalen Domäne habe?

Das neueste Tool zum Synchronisieren von Active Directory mit Azure Active Directory heißt Azure AD Connect. Weitere Informationen finden Sie unter [Integrieren Ihrer lokalen Identitäten in Azure Active Directory](https://docs.microsoft.com/azure/architecture/reference-architectures/identity/azure-ad).
  
Azure AD Connect synchronisiert den UPN und das Kennwort Ihrer Benutzer, sodass sich Benutzer mit denselben Anmeldeinformationen anmelden können, die Sie lokal verwenden. Azure AD Connect synchronisiert jedoch nur Benutzer mit Domänen, die von Office 365 überprüft wurden. Dies bedeutet, dass die Domäne auch von Azure Active Directory überprüft wird, da Office 365-Identitäten von Azure Active Directory verwaltet werden. Das heißt, die Domäne muss eine gültige Internet Domäne (beispielsweise. com,. org, .net,. US usw.) sein. Wenn Ihr internes Active Directory nur eine nicht Routingfähige Domäne verwendet (beispielsweise local), kann dies nicht mit der überprüften Domäne übereinstimmen, die Sie in Office 365 haben. Sie können dieses Problem beheben, indem Sie entweder Ihre primäre Domäne in Ihrem lokalen Active Directory ändern oder ein oder mehrere UPN-Suffixe hinzufügen.
  
### <a name="change-your-primary-domain"></a>**Ändern der primären Domäne**

Ändern Sie Ihre primäre Domäne in eine Domäne, die Sie in Office 365 überprüft haben, beispielsweise contoso.com. Jeder Benutzer mit der Domäne "contoso. local" wird dann auf contoso.com aktualisiert. Anweisungen hierzu finden Sie unter [Funktionsweise der Domänenumbenennung](https://go.microsoft.com/fwlink/p/?LinkId=624174). Dies ist ein sehr beteiligter Prozess, und eine einfachere Lösung besteht darin, [UPN-Suffixe hinzuzufügen und die Benutzer auf diese zu aktualisieren](prepare-a-non-routable-domain-for-directory-synchronization.md#bk_register), wie im folgenden Abschnitt dargestellt.
  
### <a name="add-upn-suffixes-and-update-your-users-to-them"></a>**Hinzufügen von UPN-Suffixen und Aktualisieren der Benutzer**

Sie können das. local-Problem beheben, indem Sie neue UPN-Suffixe oder Suffixe in Active Directory registrieren, um die in Office 365 überprüfte Domäne (oder Domänen) zu erfüllen. Nachdem Sie das neue Suffix registriert haben, aktualisieren Sie die Benutzer UPNs so, dass die. local-Datei durch den neuen Domänennamen ersetzt wird, sodass ein Benutzerkonto wie Billa@contoso.com aussieht.
  
Nachdem Sie die UPNs für die Verwendung der verifizierte Domäne aktualisiert haben, können Sie Ihr lokales Active Directory mit Office 365 synchronisieren.
  
 **Schritt 1: Hinzufügen des neuen UPN-Suffixes**
  
1. Wählen Sie auf dem Server, auf dem die Active Directory-Domänendienste (AD DS) ausgeführt werden, im Server-Manager die Option **Tools** \> **Active Directory-Domänen und-Vertrauensstellungen**aus.
    
    **Oder, wenn Sie nicht über Windows Server 2012**
    
    Drücken Sie die **Windows-Taste + R** , um das Dialogfeld **Ausführen** zu öffnen, und geben Sie dann in Domain. msc ein, und klicken Sie dann auf **OK**.
    
    ![Wählen Sie Active Directory-Domänen und-Vertrauensstellungen aus.](media/46b6e007-9741-44af-8517-6f682e0ac974.png)
  
2. Klicken Sie im Fenster **Active Directory-Domänen und-Vertrauensstellungen** mit der rechten Maustaste auf **Active Directory-Domänen und-Vertrauensstellungen**, und wählen Sie dann **Eigenschaften**aus.
    
    ![Klicken Sie mit der rechten Maustaste auf ActiveDirectory-Domänen und-Vertrauensstellungen, und wählen Sie Eigenschaften](media/39d20812-ffb5-4ba9-8d7b-477377ac360d.png)
  
3. Geben Sie auf der Registerkarte **UPN** -Suffixe im Feld **alternative UPN** -Suffixe Ihr neues UPN-Suffix oder Suffixe ein, und wählen Sie dann **Apply** **Hinzufügen** \> aus.
    
    ![Hinzufügen eines neuen UPN-Suffixes](media/a4aaf919-7adf-469a-b93f-83ef284c0915.PNG)
  
    Klicken Sie auf **OK** , wenn Sie mit dem Hinzufügen von Suffixen fertig sind. 
    
 **Schritt 2: Ändern des UPN-Suffixes für vorhandene Benutzer**
  
1. Wählen Sie auf dem Server, auf dem Active Directory-Domänendienste (AD DS) ausgeführt werden, im Server-Manager die Option **Tools** \> **Active Directory Active Directory-Benutzer und-Computer**aus.
    
    **Oder, wenn Sie nicht über Windows Server 2012**
    
    Drücken Sie die **Windows-Taste + R** , um das Dialogfeld **Ausführen** zu öffnen, und geben Sie dann DSA. msc ein, und klicken Sie dann auf **OK** .
    
2. Wählen Sie einen Benutzer aus, klicken Sie mit der rechten Maustaste, und wählen Sie dann **Eigenschaften**aus.
    
3. Wählen Sie auf der Registerkarte **Konto** in der Dropdownliste UPN-Suffix das neue UPN-Suffix aus, und wählen Sie dann **OK**aus.
    
    ![Hinzufügen eines neuen UPN-Suffixes für einen Benutzer](media/54876751-49f0-48cc-b864-2623c4835563.png)
  
4. Führen Sie diese Schritte für jeden Benutzer aus.
    
    Alternativ können Sie die UPN-Suffixe Massenaktualisieren [, indem Sie auch Windows PowerShell verwenden, um das UPN-Suffix für alle Benutzer zu ändern](prepare-a-non-routable-domain-for-directory-synchronization.md#BK_Posh).
    
### <a name="you-can-also-use-windows-powershell-to-change-the-upn-suffix-for-all-users"></a>**Sie können auch Windows PowerShell verwenden, um das UPN-Suffix für alle Benutzer zu ändern.**

Wenn Sie viele Benutzer aktualisieren müssen, ist es einfacher, Windows PowerShell zu verwenden. Das folgende Beispiel verwendet die Cmdlets [Get-inuser](https://go.microsoft.com/fwlink/p/?LinkId=624312) und [Set-inuser](https://go.microsoft.com/fwlink/p/?LinkId=624313) , um alle contoso. local-Suffixe in contoso.com zu ändern. 

Führen Sie die folgenden Windows PowerShell-Befehle aus, um alle contoso. local-Suffixe auf contoso.com zu aktualisieren:
    
  ```
  $LocalUsers = Get-ADUser -Filter {UserPrincipalName -like '*contoso.local'} -Properties userPrincipalName -ResultSetSize $null
  ```

  ```
  $LocalUsers | foreach {$newUpn = $_.UserPrincipalName.Replace("contoso.local","contoso.com"); $_ | Set-ADUser -UserPrincipalName $newUpn}
  ```
Weitere Informationen zur Verwendung von Windows PowerShell in Active Directory finden Sie unter [Active Directory Windows PowerShell-Modul](https://go.microsoft.com/fwlink/p/?LinkId=624314) . 

