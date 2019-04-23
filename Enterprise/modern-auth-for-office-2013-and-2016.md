---
title: Funktionsweise der modernen Authentifizierung in Office 2013- und Office 2016-Client-Apps
ms.author: tracyp
author: MSFTTracyP
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
ms.collection:
- M365-security-compliance
description: Erfahren Sie, wie die moderne Authentifizierung von Office 365 für Office 2013-und 2016-Client-apps anders funktioniert.
ms.openlocfilehash: 5e42ec2fcf8f27990af187e4ad26ba65909ac709
ms.sourcegitcommit: 51f9e89e4b9d54f92ef5c70468bda96e664b8a6b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "31957696"
---
# <a name="how-modern-authentication-works-for-office-2013-and-office-2016-client-apps"></a>Funktionsweise der modernen Authentifizierung in Office 2013- und Office 2016-Client-Apps

Lesen Sie diesen Artikel, um zu erfahren, wie Office 2013-und Office 2016-Client-apps moderne Authentifizierungsfeatures basierend auf der Authentifizierungskonfiguration im Office 365-Mandanten für Exchange Online, SharePoint Online und Skype for Business Online verwenden.

> [!NOTE]
> Ältere Client-apps wie Office 2010 und Office für Mac 2011 unterstützen keine moderne Authentifizierung und können nur mit der Standardauthentifizierung verwendet werden.

## <a name="availability-of-modern-authentication-for-office-365-services"></a>Verfügbarkeit moderner Authentifizierung für Office 365-Dienste

Für die Office 365-Dienste lautet der Standardstatus der modernen Authentifizierung wie folgt:
  
- Standard **** mäßig für Exchange Online aktiviert. Weitere Informationen finden Sie unter [Aktivieren oder Deaktivieren der modernen Authentifizierung in Exchange Online](https://support.office.com/article/58018196-f918-49cd-8238-56f57f38d662) . 
    
- Standard **** mäßig für SharePoint Online aktiviert. 
    
- Standard **** mäßig für Skype for Business Online aktiviert. Weitere Informationen finden Sie unter [Aktivieren von Skype for Business Online für die moderne Authentifizierung ](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx).
    
## <a name="sign-in-behavior-of-office-client-apps"></a>Anmeldeverhalten von Office-Client-apps

Office 2013-Client-apps unterstützen Standardauthentifizierung. Legacy bedeuten, dass Sie entweder den Microsoft Online-Anmelde-Assistenten oder die Standardauthentifizierung unterstützen. Damit diese Clients moderne Authentifizierungsfeatures verwenden können, hat der Windows-Client Registrierungsschlüssel festgelegt. Weitere Informationen finden Sie unter [enable modern Authentication for Office 2013 on Windows Devices](https://support.office.com/article/7dc1c01a-090f-4971-9677-f1b192d6c910).
  
In diesem Artikel erfahren Sie, wie Sie die [moderne Authentifizierung (Adal) mit Skype for Business verwenden](https://go.microsoft.com/fwlink/p/?LinkId=785431) können, um sich mit Skype for Business vertraut zu machen. 
  
Office 2016-Clients unterstützen standardmäßig die moderne Authentifizierung, und es ist keine Aktion erforderlich, damit der Client diese neuen Flows verwenden kann. Für die Verwendung der Legacy Authentifizierung ist jedoch eine explizite Aktion erforderlich.
  
Klicken Sie auf die Links unten, um zu sehen, wie die Office 2013-und Office 2016-Clientauthentifizierung mit den Office 365-Diensten funktioniert, je nachdem, ob die moderne Authentifizierung aktiviert ist oder nicht.
  
- [Exchange Online](modern-auth-for-office-2013-and-2016.md#BK_EchangeOnline)
    
- [SharePoint Online](modern-auth-for-office-2013-and-2016.md#BK_SharePointOnline)
    
- [Skype for Business Online](modern-auth-for-office-2013-and-2016.md#BK_SFBO)
    
### <a name="exchange-online"></a>Exchange Online

In der folgenden Tabelle wird das Authentifizierungsverhalten für Office 2013-oder Office 2016-Client-apps beschrieben, wenn Sie eine Verbindung mit Exchange Online mit oder ohne moderne Authentifizierung herstellen.
  
|Office-Client-App-Version * * * *|Registrierungsschlüssel vorhanden? * * * *|Moderne Authentifizierung on? * * * *|Authentifizierungsverhalten bei aktivierter moderner Authentifizierung für den Mandanten (Standard) * * * *|Authentifizierungsverhalten mit moderner Authentifizierung für den Mandanten deaktiviert * * * *|
|:-----|:-----|:-----|:-----|:-----|
|Office 2016  <br/> |Nein oder EnableADAL = 1  <br/> |Ja  <br/> |Die moderne Authentifizierung wird zuerst versucht. Wenn der Server eine moderne Authentifizierungs Verbindung ablehnt, wird die Standardauthentifizierung verwendet. Der Server lehnt die moderne Authentifizierung ab, wenn der Mandant nicht aktiviert ist.  <br/> |Die moderne Authentifizierung wird zuerst versucht. Wenn der Server eine moderne Authentifizierungs Verbindung ablehnt, wird die Standardauthentifizierung verwendet. Der Server lehnt die moderne Authentifizierung ab, wenn der Mandant nicht aktiviert ist.  <br/> |
|Office 2016  <br/> |Ja, EnableADAL = 1  <br/> |Ja  <br/> |Die moderne Authentifizierung wird zuerst versucht. Wenn der Server eine moderne Authentifizierungs Verbindung ablehnt, wird die Standardauthentifizierung verwendet. Der Server lehnt die moderne Authentifizierung ab, wenn der Mandant nicht aktiviert ist.  <br/> |Die moderne Authentifizierung wird zuerst versucht. Wenn der Server eine moderne Authentifizierungs Verbindung ablehnt, wird die Standardauthentifizierung verwendet. Der Server lehnt die moderne Authentifizierung ab, wenn der Mandant nicht aktiviert ist.  <br/> |
|Office 2016  <br/> |Ja, EnableADAL = 0  <br/> |Nein  <br/> |Standardauthentifizierung  <br/> |Standardauthentifizierung  <br/> |
|Office 2013  <br/> |Nein  <br/> |Nein  <br/> |Standardauthentifizierung  <br/> |Standardauthentifizierung  <br/> |
|Office 2013  <br/> |Ja, EnableADAL = 1  <br/> |Ja  <br/> |Die moderne Authentifizierung wird zuerst versucht. Wenn der Server eine moderne Authentifizierungs Verbindung ablehnt, wird die Standardauthentifizierung verwendet. Der Server lehnt die moderne Authentifizierung ab, wenn der Mandant nicht aktiviert ist.  <br/> |Die moderne Authentifizierung wird zuerst versucht. Wenn der Server eine moderne Authentifizierungs Verbindung ablehnt, wird die Standardauthentifizierung verwendet. Der Server lehnt die moderne Authentifizierung ab, wenn der Mandant nicht aktiviert ist.  <br/> |
   
### <a name="sharepoint-online"></a>SharePoint Online
<a name="BK_SharePointOnline"> </a>

In der folgenden Tabelle wird das Authentifizierungsverhalten für Office 2013-oder Office 2016-Client-apps beschrieben, wenn Sie eine Verbindung mit SharePoint Online mit oder ohne moderne Authentifizierung herstellen.
  
|Office-Client-App-Version * * * *|Registrierungsschlüssel vorhanden? * * * *|Moderne Authentifizierung on? * * * *|Authentifizierungsverhalten bei aktivierter moderner Authentifizierung für den Mandanten (Standard) * * * *|Authentifizierungsverhalten mit moderner Authentifizierung für den Mandanten deaktiviert * * * *|
|:-----|:-----|:-----|:-----|:-----|
|Office 2016  <br/> |Nein oder EnableADAL = 1  <br/> |Ja  <br/> |Nur moderne Authentifizierung.  <br/> |Nicht verbinden.  <br/> |
|Office 2016  <br/> |Ja, EnableADAL = 1  <br/> |Ja  <br/> |Nur moderne Authentifizierung.  <br/> |Nicht verbinden.  <br/> |
|Office 2016  <br/> |Ja, EnableADAL = 0  <br/> |Nein  <br/> |Nur Microsoft Online-Anmelde-Assistent.  <br/> |Nur Microsoft Online-Anmelde-Assistent.  <br/> |
|Office 2013  <br/> |Nein  <br/> |Nein  <br/> |Nur Microsoft Online-Anmelde-Assistent.  <br/> |Nur Microsoft Online-Anmelde-Assistent.  <br/> |
|Office 2013  <br/> |Ja, EnableADAL = 1  <br/> |Ja  <br/> |Nur moderne Authentifizierung.  <br/> |Nicht verbinden.  <br/> |
   
### <a name="skype-for-business-online"></a>Skype for Business Online
<a name="BK_SFBO"> </a>

In der folgenden Tabelle wird das Authentifizierungsverhalten für Office 2013-oder Office 2016-Client-apps beschrieben, wenn Sie eine Verbindung zu Skype for Business Online mit oder ohne moderne Authentifizierung herstellen.
  
|Office-Client-App-Version * * * *|Registrierungsschlüssel vorhanden? * * * *|Moderne Authentifizierung on? * * * *|Authentifizierungsverhalten bei aktivierter moderner Authentifizierung für den Mandanten * * * *|Authentifizierungsverhalten mit moderner Authentifizierung für den Mandanten deaktiviert (Standard) * * * *|
|:-----|:-----|:-----|:-----|:-----|
|Office 2016  <br/> |Nein oder EnableADAL = 1  <br/> |Ja  <br/> |Die moderne Authentifizierung wird zuerst versucht. Wenn der Server eine moderne Authentifizierungs Verbindung ablehnt, wird der Microsoft Online-Anmelde-Assistent verwendet. Der Server lehnt die moderne Authentifizierung ab, wenn Skype for Business Online-Mandanten nicht aktiviert sind.  <br/> |Die moderne Authentifizierung wird zuerst versucht. Wenn der Server eine moderne Authentifizierungs Verbindung ablehnt, wird der Microsoft Online-Anmelde-Assistent verwendet. Der Server lehnt die moderne Authentifizierung ab, wenn Skype for Business Online-Mandanten nicht aktiviert sind.  <br/> |
|Office 2016  <br/> |Ja, EnableADAL = 1  <br/> |Ja  <br/> |Die moderne Authentifizierung wird zuerst versucht. Wenn der Server eine moderne Authentifizierungs Verbindung ablehnt, wird der Microsoft Online-Anmelde-Assistent verwendet. Der Server lehnt die moderne Authentifizierung ab, wenn Skype for Business Online-Mandanten nicht aktiviert sind.  <br/> |Die moderne Authentifizierung wird zuerst versucht. Wenn der Server eine moderne Authentifizierungs Verbindung ablehnt, wird der Microsoft Online-Anmelde-Assistent verwendet. Der Server lehnt die moderne Authentifizierung ab, wenn Skype for Business Online-Mandanten nicht aktiviert sind.  <br/> |
|Office 2016  <br/> |Ja, EnableADAL = 0  <br/> |Nein  <br/> |Nur Microsoft Online-Anmelde-Assistent.  <br/> |Nur Microsoft Online-Anmelde-Assistent.  <br/> |
|Office 2013  <br/> |Nein  <br/> |Nein  <br/> |Nur Microsoft Online-Anmelde-Assistent.  <br/> |Nur Microsoft Online-Anmelde-Assistent.  <br/> |
|Office 2013  <br/> |Ja, EnableADAL = 1  <br/> |Ja  <br/> |Die moderne Authentifizierung wird zuerst versucht. Wenn der Server eine moderne Authentifizierungs Verbindung ablehnt, wird der Microsoft Online-Anmelde-Assistent verwendet. Der Server lehnt die moderne Authentifizierung ab, wenn Skype for Business Online-Mandanten nicht aktiviert sind.  <br/> |Nur Microsoft Online-Anmelde-Assistent.  <br/> |
   
## <a name="see-also"></a>Siehe auch

[Aktivieren der modernen Authentifizierung für Office 2013 auf Windows-Geräten](https://support.office.com/article/enable-modern-authentication-for-office-2013-on-windows-devices-7dc1c01a-090f-4971-9677-f1b192d6c910)

[Planen der mehrstufigen Authentifizierung für Office 365-Bereitstellungen (für Office 365-Administratoren)](https://support.office.com/article/plan-for-multi-factor-authentication-for-office-365-deployments-043807b2-21db-4d5c-b430-c8a6dee0e6ba)

[Anmelden bei Office 365 mit Überprüfung in zwei Schritten (für Endbenutzer)](https://support.office.com/article/sign-in-to-office-365-with-2-step-verification-2b856342-170a-438e-9a4f-3c092394d3cb)
