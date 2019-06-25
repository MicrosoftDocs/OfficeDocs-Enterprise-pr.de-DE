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
description: Hier erfahren Sie, was Sie tun müssen, wenn Sie vor der Synchronisierung mit Office 365 eine nicht-routale-Domäne mit Ihren lokalen Benutzern verbunden haben.
ms.openlocfilehash: cf7b901c3aaf6f49e4ecd92d27b9a6d9b8951d40
ms.sourcegitcommit: b4c82c0bf61f50386e534ad23479b5cf84f4e2ea
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/25/2019
ms.locfileid: "35203634"
---
# <a name="prepare-a-non-routable-domain-for-directory-synchronization"></a>Vorbereiten einer nicht routingfähigen Domäne für die Verzeichnissynchronisierung
Wenn Sie Ihr lokales Verzeichnis mit Office 365 synchronisieren, müssen Sie über eine überprüfte Domäne in Azure Active Directory verfügen. Nur die Benutzerprinzipalnamen (User Principal Names, UPN), die der lokalen Domäne zugeordnet sind, werden synchronisiert. Allerdings wird jeder UPN, der eine nicht Routingfähige Domäne enthält, beispielsweise. local (wie Billa @ contoso. local), mit einer. onmicrosoft.com-Domäne (wie Billa@contoso.onmicrosoft.com) synchronisiert. 

Wenn Sie derzeit eine. local-Domäne für ihre Benutzerkonten in Active Directory verwenden, sollten Sie diese so ändern, dass Sie eine verifizierte Domäne (wie Billa@contoso.com) verwenden, um ordnungsgemäß mit Ihrer Office 365 Domäne zu synchronisieren.
  
## <a name="what-if-i-only-have-a-local-on-premises-domain"></a>Was geschieht, wenn ich nur eine lokale lokale Domäne habe?

Das neueste Tool, mit dem Sie Ihre Active Directory mit Azure Active Directory synchronisieren können, heißt Azure AD Connect. Weitere Informationen finden Sie unter [Integrieren Ihrer lokalen Identitäten in Azure Active Directory](https://docs.microsoft.com/azure/architecture/reference-architectures/identity/azure-ad).
  
Azure AD Connect synchronisiert den UPN und das Kennwort Ihrer Benutzer, sodass sich Benutzer mit denselben Anmeldeinformationen anmelden können, die Sie lokal verwenden. Azure AD Connect synchronisiert jedoch nur Benutzer mit Domänen, die von Office 365 überprüft werden. Dies bedeutet, dass die Domäne auch von Azure Active Directory überprüft wird, da Office 365 Identitäten von Azure Active Directory verwaltet werden. Die Domäne muss also eine gültige Internet Domäne sein (beispielsweise. com,. org, .net,. US usw.). Wenn Ihr interner Active Directory nur eine nicht Routingfähige Domäne verwendet (beispielsweise. local), kann dies nicht möglicherweise mit der überprüften Domäne übereinstimmen, die Sie auf Office 365 haben. Sie können dieses Problem beheben, indem Sie entweder Ihre primäre Domäne in Ihrem lokalen Active Directory ändern oder ein oder mehrere UPN-Suffixe hinzufügen.
  
### <a name="change-your-primary-domain"></a>**Ändern der primären Domäne**

Ändern Sie Ihre primäre Domäne in eine Domäne, die Sie in Office 365 überprüft haben, beispielsweise contoso.com. Jeder Benutzer mit der Domäne "contoso. local" wird dann auf contoso.com aktualisiert. Anweisungen hierzu finden Sie unter [Funktionsweise der Domänenumbenennung](https://go.microsoft.com/fwlink/p/?LinkId=624174). Dies ist jedoch ein sehr beteiligter Prozess, und eine einfachere Lösung wird im folgenden Abschnitt beschrieben.
  
### <a name="add-upn-suffixes-and-update-your-users-to-them"></a>**Hinzufügen von UPN-Suffixen und Aktualisieren der Benutzer**

Sie können das. local-Problem lösen, indem Sie neue UPN-Suffixe oder-Suffixe in Active Directory registrieren, damit Sie mit der Domäne (oder den Domänen) übereinstimmen, die Sie in Office 365 überprüft haben. Nachdem Sie das neue Suffix registriert haben, aktualisieren Sie den Benutzer UPNs so, dass die. local durch den neuen Domänennamen ersetzt wird, sodass ein Benutzerkonto wie Billa@contoso.com aussieht.
  
Nachdem Sie die UPNs für die Verwendung der überprüften Domäne aktualisiert haben, können Sie Ihre lokale Active Directory mit Office 365 synchronisieren.
  
 **Schritt 1: Hinzufügen des neuen UPN-Suffix**
  
1. Klicken Sie auf dem Server, auf dem Active Directory-Domänendienste (AD DS) ausgeführt wird, im Server-Manager auf **Tools** \> **Active Directory Domänen und Vertrauensstellungen**.
    
    **Oder, wenn Sie nicht über Windows Server 2012**
    
    Drücken Sie die **Windows-Taste + R** , um das Dialogfeld **Ausführen** zu öffnen, und geben Sie dann in Domain. msc ein, und wählen Sie dann **OK**aus.
    
    ![Wählen Sie Active Directory Domänen und Vertrauensstellungen aus.](media/46b6e007-9741-44af-8517-6f682e0ac974.png)
  
2. Klicken Sie im Fenster **Active Directory Domänen und Vertrauensstellungen** mit der rechten Maustaste auf **Active Directory Domänen und Vertrauensstellungen**, und wählen Sie dann **Eigenschaften**aus.
    
    ![Klicken Sie mit der rechten Maustaste auf ActiveDirectory-Domänen und-Vertrauensstellungen, und wählen Sie Eigenschaften](media/39d20812-ffb5-4ba9-8d7b-477377ac360d.png)
  
3. Geben Sie auf der Registerkarte **UPN** -Suffixe im Feld **alternative UPN** -Suffixe ihre neuen UPN-Suffixe oder Suffixe ein, und wählen Sie dann **Add** \> **Apply**aus.
    
    ![Hinzufügen eines neuen UPN-Suffix](media/a4aaf919-7adf-469a-b93f-83ef284c0915.PNG)
  
    Klicken Sie auf **OK** , wenn Sie das Hinzufügen von Suffixen abgeschlossen haben. 
    
 **Schritt 2: Ändern des UPN-Suffixes für vorhandene Benutzer**
  
1. Wählen Sie auf dem Server, auf dem Active Directory-Domänendienste (AD DS) ausgeführt wird, im Server-Manager **Tools** \> **Active Directory Active Directory Benutzer und Computer**aus.
    
    **Oder, wenn Sie nicht über Windows Server 2012**
    
    Drücken Sie die **Windows-Taste + R** , um das Dialogfeld **Ausführen** zu öffnen, und geben Sie dann DSA. msc ein, und klicken Sie dann auf **OK** .
    
2. Wählen Sie einen Benutzer aus, klicken Sie mit der rechten Maustaste, und wählen Sie dann **Eigenschaften**aus.
    
3. Wählen Sie auf der Registerkarte **Konto** in der Dropdownliste UPN-Suffix das neue UPN-Suffix aus, und wählen Sie dann **OK**aus.
    
    ![Hinzufügen eines neuen UPN-Suffixes für einen Benutzer](media/54876751-49f0-48cc-b864-2623c4835563.png)
  
4. Führen Sie diese Schritte für jeden Benutzer aus.
    
   
### <a name="you-can-also-use-windows-powershell-to-change-the-upn-suffix-for-all-users"></a>**Sie können auch Windows PowerShell verwenden, um das UPN-Suffix für alle Benutzer zu ändern.**

Wenn Sie viele Benutzer aktualisieren müssen, ist es einfacher, Windows PowerShell zu verwenden. Im folgenden Beispiel werden die Cmdlets [Get-User](https://go.microsoft.com/fwlink/p/?LinkId=624312) und [festgelegt-User](https://go.microsoft.com/fwlink/p/?LinkId=624313) verwendet, um alle contoso. local-Suffixe in contoso.com zu ändern. 

Führen Sie die folgenden Windows PowerShell Befehle aus, um alle contoso. local-Suffixe auf contoso.com zu aktualisieren:
    
  ```
  $LocalUsers = Get-ADUser -Filter {UserPrincipalName -like '*contoso.local'} -Properties userPrincipalName -ResultSetSize $null
  ```

  ```
  $LocalUsers | foreach {$newUpn = $_.UserPrincipalName.Replace("contoso.local","contoso.com"); $_ | Set-ADUser -UserPrincipalName $newUpn}
  ```
Weitere Informationen zum Verwenden von Windows PowerShell in Active Directory finden Sie unter [Active Directory Windows PowerShell Moduls](https://go.microsoft.com/fwlink/p/?LinkId=624314) . 

