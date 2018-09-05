---
title: Wie modernen Funktionsweise der Authentifizierung für apps für Office 2013 und Office 2016 Client
ms.author: sirkkuw
author: Sirkkuw
manager: laurawi
ms.date: 8/1/2017
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- GMA150
- GPA150
- GEA150
- BCS160
ms.assetid: e4c45989-4b1a-462e-a81b-2a13191cf517
description: Hier erfahren Sie, wie modernen Office 365-Authentifizierung für Office 2013 und Clientanwendungen 2016 unterschiedlich funktioniert.
ms.openlocfilehash: a9b6e2dabec9fb59f5fd7f60508dcbc6fe840cfb
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540886"
---
# <a name="how-modern-authentication-works-for-office-2013-and-office-2016-client-apps"></a>Wie modernen Funktionsweise der Authentifizierung für apps für Office 2013 und Office 2016 Client

Lesen Sie die Authentifizierungskonfiguration auf dem Office 365-Mandanten für Exchange Online, SharePoint Online und Skype für Business Online diesem Artikel erfahren, wie Office 2013 und Office 2016 Clientanwendungen modernen Authentifizierungsfeatures basiert.
  
## <a name="availability-of-modern-authentication-for-office-365-services"></a>Verfügbarkeit von modernen Authentifizierung für Office 365-Dienste

Für die Office 365-Diensten ist der Standardzustand des modernen Authentifizierung:
  
- **Für Exchange Online standardmäßig aktiviert.** Finden Sie unter [Aktivieren oder Deaktivieren der modernen Authentifizierung in Exchange Online](https://support.office.com/article/58018196-f918-49cd-8238-56f57f38d662) aktiviert oder deaktiviert. 
    
- **Für SharePoint Online standardmäßig aktiviert.** 
    
- **Für Skype für Business Online standardmäßig aktiviert.** Finden Sie unter [Aktivieren Skype für Business Online für moderne Authentifizierung ](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx)aktiviert oder deaktiviert.
    
## <a name="sign-in-behavior-of-office-client-apps"></a>Anmeldeverhalten der Office-Clientanwendungen

Apps für Office 2013-Client legacy-Authentifizierung standardmäßig unterstützen. Legacy bedeutet, dass sie entweder Microsoft Online-Anmeldung-Assistenten oder grundlegende-Authentifizierung unterstützen. In der Reihenfolge für diese Clients modernen Authentifizierungsfeatures verwenden haben die Windows-Client ist Registrierungsschlüssel festgelegt. Anweisungen finden Sie unter [Enable modernen Authentication für Office 2013 auf Windows-Geräten](https://support.office.com/article/7dc1c01a-090f-4971-9677-f1b192d6c910).
  
[So verwenden Sie modernen Authentifizierung (ADAL) mit Skype für Business](https://go.microsoft.com/fwlink/p/?LinkId=785431) erfahren Sie mehr über die Funktionsweise mit Skype für Business gelesen. 
  
Office 2016 Clients modernen Authentifizierung standardmäßig unterstützen, und für den Client verwendet diese neue Datenflüsse ist keine Aktion erforderlich. Explizite Aktion wird jedoch legacy-Authentifizierung benötigt.
  
Klicken Sie auf die unten aufgeführten Links, finden Sie unter Funktionsweise von Office 2013 und Office 2016 Clientauthentifizierung mit Office 365-Diensten, je nachdem, ob modernen Authentifizierung aktiviert ist.
  
- [Exchange Online](modern-auth-for-office-2013-and-2016.md#BK_EchangeOnline)
    
- [SharePoint Online](modern-auth-for-office-2013-and-2016.md#BK_SharePointOnline)
    
- [Skype for Business Online](modern-auth-for-office-2013-and-2016.md#BK_SFBO)
    
### <a name="exchange-online"></a>Exchange Online

In der folgenden Tabelle werden das Verhalten der Authentifizierung für apps für Office 2013 oder Office 2016 Client bei Exchange Online mit oder ohne Authentifizierung modernen Verbindung mit einem beschrieben.
  
|App-Version von Office Client ***|Registrierungsschlüssel vorhanden? ***|Moderne Authentifizierung auf? ***|Verhalten der Authentifizierung mit modernen Authentifizierung für den Mandanten (Standard) eingeschaltet ***|Authentifizierung Verhalten mit modernen Authentifizierung für den Mandanten *** ausgeschaltet.|
|:-----|:-----|:-----|:-----|:-----|
|Office 2016  <br/> |Nein, oder EnableADAL = 1  <br/> |Ja  <br/> |Moderne Authentifizierung wird zuerst versucht. Lehnt der Server eine Verbindung mit modernen Authentifizierung, wird die Standardauthentifizierung verwendet. Server verweigert modernen Authentifizierung, wenn der Mandanten nicht aktiviert ist.  <br/> |Moderne Authentifizierung wird zuerst versucht. Lehnt der Server eine Verbindung mit modernen Authentifizierung, wird die Standardauthentifizierung verwendet. Server verweigert modernen Authentifizierung, wenn der Mandanten nicht aktiviert ist.  <br/> |
|Office 2016  <br/> |Ja, EnableADAL = 1  <br/> |Ja  <br/> |Moderne Authentifizierung wird zuerst versucht. Lehnt der Server eine Verbindung mit modernen Authentifizierung, wird die Standardauthentifizierung verwendet. Server verweigert modernen Authentifizierung, wenn der Mandanten nicht aktiviert ist.  <br/> |Moderne Authentifizierung wird zuerst versucht. Lehnt der Server eine Verbindung mit modernen Authentifizierung, wird die Standardauthentifizierung verwendet. Server verweigert modernen Authentifizierung, wenn der Mandanten nicht aktiviert ist.  <br/> |
|Office 2016  <br/> |Ja, EnableADAL = 0  <br/> |Nein  <br/> |Standardauthentifizierung  <br/> |Standardauthentifizierung  <br/> |
|Office 2013  <br/> |Nein  <br/> |Nein  <br/> |Standardauthentifizierung  <br/> |Standardauthentifizierung  <br/> |
|Office 2013  <br/> |Ja, EnableADAL = 1  <br/> |Ja  <br/> |Moderne Authentifizierung wird zuerst versucht. Lehnt der Server eine Verbindung mit modernen Authentifizierung, wird die Standardauthentifizierung verwendet. Server verweigert modernen Authentifizierung, wenn der Mandanten nicht aktiviert ist.  <br/> |Moderne Authentifizierung wird zuerst versucht. Lehnt der Server eine Verbindung mit modernen Authentifizierung, wird die Standardauthentifizierung verwendet. Server verweigert modernen Authentifizierung, wenn der Mandanten nicht aktiviert ist.  <br/> |
   
### <a name="sharepoint-online"></a>SharePoint Online
<a name="BK_SharePointOnline"> </a>

In der folgenden Tabelle werden das Verhalten der Authentifizierung für apps für Office 2013 oder Office 2016 Client bei SharePoint Online mit oder ohne Authentifizierung modernen Verbindung mit einem beschrieben.
  
|App-Version von Office Client ***|Registrierungsschlüssel vorhanden? ***|Moderne Authentifizierung auf? ***|Verhalten der Authentifizierung mit modernen Authentifizierung für den Mandanten (Standard) eingeschaltet ***|Authentifizierung Verhalten mit modernen Authentifizierung für den Mandanten *** ausgeschaltet.|
|:-----|:-----|:-----|:-----|:-----|
|Office 2016  <br/> |Nein, oder EnableADAL = 1  <br/> |Ja  <br/> |Moderne Authentifizierung.  <br/> |Fehler beim Verbinden.  <br/> |
|Office 2016  <br/> |Ja, EnableADAL = 1  <br/> |Ja  <br/> |Moderne Authentifizierung.  <br/> |Fehler beim Verbinden.  <br/> |
|Office 2016  <br/> |Ja, EnableADAL = 0  <br/> |Nein  <br/> |Microsoft Online-Anmelde-Assistenten nur.  <br/> |Microsoft Online-Anmelde-Assistenten nur.  <br/> |
|Office 2013  <br/> |Nein  <br/> |Nein  <br/> |Microsoft Online-Anmelde-Assistenten nur.  <br/> |Microsoft Online-Anmelde-Assistenten nur.  <br/> |
|Office 2013  <br/> |Ja, EnableADAL = 1  <br/> |Ja  <br/> |Moderne Authentifizierung.  <br/> |Fehler beim Verbinden.  <br/> |
   
### <a name="skype-for-business-online"></a>Skype for Business Online
<a name="BK_SFBO"> </a>

In der folgenden Tabelle werden das Verhalten der Authentifizierung für Office 2013 oder apps für Office 2016 Client bei Skype für Business Online mit oder ohne Authentifizierung modernen Verbindung mit einem beschrieben.
  
|App-Version von Office Client ***|Registrierungsschlüssel vorhanden? ***|Moderne Authentifizierung auf? ***|Verhalten der Authentifizierung mit modernen Authentifizierung für den Mandanten *** aktiviert|Verhalten der Authentifizierung mit modernen Authentifizierung für den Mandanten (Standard) deaktiviert ***|
|:-----|:-----|:-----|:-----|:-----|
|Office 2016  <br/> |Nein, oder EnableADAL = 1  <br/> |Ja  <br/> |Moderne Authentifizierung wird zuerst versucht. Wenn der Server eine Verbindung mit modernen Authentifizierung ablehnt, wird Microsoft Online-Assistenten verwendet. Server verweigert modernen Authentifizierung beim Skype für Business Online Mandanten sind nicht aktiviert.  <br/> |Moderne Authentifizierung wird zuerst versucht. Wenn der Server eine Verbindung mit modernen Authentifizierung ablehnt, wird Microsoft Online-Assistenten verwendet. Server verweigert modernen Authentifizierung beim Skype für Business Online Mandanten sind nicht aktiviert.  <br/> |
|Office 2016  <br/> |Ja, EnableADAL = 1  <br/> |Ja  <br/> |Moderne Authentifizierung wird zuerst versucht. Wenn der Server eine Verbindung mit modernen Authentifizierung ablehnt, wird Microsoft Online-Assistenten verwendet. Server verweigert modernen Authentifizierung beim Skype für Business Online Mandanten sind nicht aktiviert.  <br/> |Moderne Authentifizierung wird zuerst versucht. Wenn der Server eine Verbindung mit modernen Authentifizierung ablehnt, wird Microsoft Online-Assistenten verwendet. Server verweigert modernen Authentifizierung beim Skype für Business Online Mandanten sind nicht aktiviert.  <br/> |
|Office 2016  <br/> |Ja, EnableADAL = 0  <br/> |Nein  <br/> |Microsoft Online-Anmelde-Assistenten nur.  <br/> |Microsoft Online-Anmelde-Assistenten nur.  <br/> |
|Office 2013  <br/> |Nein  <br/> |Nein  <br/> |Microsoft Online-Anmelde-Assistenten nur.  <br/> |Microsoft Online-Anmelde-Assistenten nur.  <br/> |
|Office 2013  <br/> |Ja, EnableADAL = 1  <br/> |Ja  <br/> |Moderne Authentifizierung wird zuerst versucht. Wenn der Server eine Verbindung mit modernen Authentifizierung ablehnt, wird Microsoft Online-Assistenten verwendet. Server verweigert modernen Authentifizierung beim Skype für Business Online Mandanten sind nicht aktiviert.  <br/> |Microsoft Online-Anmelde-Assistenten nur.  <br/> |
   
## <a name="see-also"></a>Siehe auch

[Verwenden der modernen Office 365-Authentifizierung mit Office-clients](https://support.office.com/article/776c0036-66fd-41cb-8928-5495c0f9168a)
