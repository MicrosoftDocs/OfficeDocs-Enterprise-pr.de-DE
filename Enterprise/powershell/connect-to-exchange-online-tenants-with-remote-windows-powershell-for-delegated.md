---
title: Verbinden mit Exchange Online-Mandanten über eine Remotesitzung von Windows PowerShell für Partner mit delegierten Zugriffsberechtigungen (Delegated Access Permissions, DAP)
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: ''
ms.assetid: ae5f1a87-8b77-4f93-a1b8-56f800aeb283
description: 'Zusammenfassung: Verwenden Sie eine Remotesitzung von Windows PowerShell, um eine Verbindung mit Exchange Online anhand des DelegatedOrg-Werts herzustellen.'
ms.openlocfilehash: 4dfe54088a1b60b0bcf7e7563362c0b2a413f3ad
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "34069151"
---
# <a name="connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated-access-permissions-dap-partners"></a>Verbinden mit Exchange Online-Mandanten über eine Remotesitzung von Windows PowerShell für Partner mit delegierten Zugriffsberechtigungen (Delegated Access Permissions, DAP)

 **Zusammenfassung:** Verwenden Sie eine Remotesitzung von PowerShell, um eine Verbindung mit Exchange Online anhand des `DelegatedOrg`-Werts herzustellen.

> [!IMPORTANT]
> Die Verfahren in diesem Thema gelten nur für Partner mit delegierten Zugriffsberechtigungen (Delegated Access Permission, DAP). Wenn Sie kein DAP-Partner sind, verwenden Sie nicht die Verfahren in diesem Thema. 
  
DAP-Partner sind Syndication- und Cloudlösungsanbieter-Partner (CSP-Partner). Häufig handelt es sich um Netzwerk- oder Telekom-Anbieter für andere Unternehmen. Sie bündeln Abonnements in ihren Serviceangeboten für ihre Kunden. Sie verfügen über einen Partnermandanten, dem automatisch die Berechtigung „Verwalten im Namen von" (Administer On Behalf Of, AOBO) für ihren Office 365-Kundenmandanten erteilt wird, damit sie alle ihre Kundenmandanten verwalten und Berichte dazu erstellen können.

DAP-Partner können Exchange Online PowerShell verwenden, um die Exchange Online-Einstellungen von Kunden zu verwalten und Office 365-Berichte über die Befehlszeile abzurufen. Sie verwenden Windows PowerShell auf Ihrem lokalen Computer, um eine Remote-PowerShell-Sitzung zu Exchange Online zu erstellen. Dabei handelt es sich um einen Prozess mit drei Schritten, Sie geben Ihre Anmeldeinformationen zu Exchange Online an, stellen die erforderlichen Verbindungseinstellungen bereit und importieren anschließend die Exchange Online-Cmdlets in Ihre lokale Windows PowerShell-Sitzung.

> [!NOTE]
> DAP-Partner können nicht die Verfahren in [Verbinden mit Exchange Online PowerShell per mehrstufiger Authentifizierung](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell) verwenden, um eine Verbindung zu ihren Kundenmandantenorganisationen in Exchange Online PowerShell herzustellen. Die mehrstufige Authentifizierung und das Remote-PowerShell-Modul von Exchange Online funktionieren nicht mit der delegierten Authentifizierung.
  
## <a name="what-do-you-need-to-know-before-you-begin"></a>Was sollten Sie wissen, bevor Sie beginnen?

- Geschätzte Zeit bis zum Abschließen des Vorgangs: 5 Minuten

- Sie können folgende Versionen von Windows verwenden:
    
  - Windows 10

  - Windows 8.1

  - Windows Server 2016

  - Windows Server 2012 oder Windows Server 2012 R2

  - Windows 7 Service Pack 1 (SP1)<sup>*</sup>

  - Windows Server 2008 R2 SP1<sup>*</sup>

    <sup>*</sup> Für ältere Versionen von Windows müssen Sie Microsoft.NET Framework 4.5 oder höher installieren und dann eine aktualisierte Version von Windows Management Framework installieren: 3.0, 4.0 oder 5.1 (nur eine). Weitere Informationen finden Sie unter [ Installation von .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868), [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757), [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344) und [Windows Management Framework 5.1](https://aka.ms/wmf5download).

- Windows PowerShell muss zum Ausführen von Skripts konfiguriert werden. Standardmäßig ist dies nicht der Fall. Beim Versucht, eine Verbindung herzustellen, wird der folgende Fehler angezeigt:

  `Files cannot be loaded because running scripts is disabled on this system. Provide a valid certificate with which to sign the files.`

  Um anzufordern, dass alle PowerShell-Skripts, die Sie aus dem Internet herunterladen, von einem vertrauenswürdigen Herausgeber signiert werden, müssen Sie den folgenden Befehl in einem Windows PowerShell-Fenster mit erhöhten Rechten ausführen (ein Windows PowerShell-Fenster, das Sie durch Auswahl von **Als Administrator ausführen**) geöffnet haben:

    ```
    Set-ExecutionPolicy RemoteSigned
    ```

  Sie müssen diese Einstellung nur einmalig auf Ihrem Computer konfigurieren, und nicht bei jedem Verbindungsaufbau.

- Informationen zu Tastenkombinationen, die möglicherweise für die Verfahren in diesem Thema gelten, finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](https://go.microsoft.com/fwlink/p/?LinkId=534017).

## <a name="connect-to-exchange-online-for-customer-organizations"></a>Herstellen einer Verbindung mit Exchange Online für Kundenorganisationen

1. Öffnen Sie auf Ihrem lokalen Computer Windows PowerShell, und führen Sie dann den folgenden Befehl aus.
    
    ```
    $UserCredential = Get-Credential
    ```

    Geben Sie im Dialogfeld **Bei Windows PowerShell anmelden** Ihren DAP-Administratorbenutzernamen und das Kennwort ein, und klicken Sie dann auf **OK**.
    
2. Ersetzen Sie _\<Kundenmandanten-Domänenname\>_ durch den Namen der Mandantendomäne, mit der Sie eine Verbindung herstellen möchten, und führen Sie den folgenden Befehl aus:
    
    ```
    $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.outlook.com/powershell-liveid?DelegatedOrg=<customer tenant domain name> -Credential $UserCredential -Authentication Basic -AllowRedirection
    ```

    Der wichtigste Schritt für diesen Befehl ist anzugeben, auf welchen Kunden für die Berichtsinformationen zugegriffen werden soll. Sie geben dies durch den _ConnectionURI_-Parameter an, für den Sie den vollqualifizierten Domänennamen (FQDN) des anfänglichen Domänennamens als Wert für  `?DelegatedOrg=` angeben. Durch diesen Wert wird der korrekte Exchange Online PowerShell-Endpunkt angegeben, mit dem eine Verbindung hergestellt werden soll. Remote-PowerShell muss mit der Office 365-Berichterstellung bei jeder Ausführung eines Berichts eine Verbindung im Kontext eines bestimmten Benutzers herstellen. Nachdem Sie eine Verbindung mit Exchange Online PowerShell hergestellt haben, werden alle der folgenden Befehle im Kontext dieses Kunden ausgeführt. Auf diese Weise können Sie auf alle verfügbaren Berichte für diesen Kunden zugreifen.
    
3. Führen Sie den folgenden Befehl aus.
    
    ```
    Import-PSSession $Session
    ```

> [!NOTE]
> Es können höchstens drei Sitzungen gleichzeitig unter einem Konto ausgeführt werden. Stellen Sie sicher, dass die Remote-PowerShell-Sitzung getrennt wird, wenn Sie alle Aufgaben ausgeführt haben. Wenn Sie das Windows PowerShell-Fenster schließen, ohne die Sitzung zu trennen, verbrauchen Sie möglicherweise alle Remote-PowerShell-Sitzungen, die Ihnen zur Verfügung stehen, sodass Sie dann warten müssen, bis die Sitzungen abgelaufen sind. Führen Sie zum Trennen der PowerShell-Remotesitzung den folgenden Befehl aus:

```
Remove-PSSession $Session
```
  
## <a name="how-do-you-know-this-worked"></a>Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Nach Schritt 3 werden die Exchange Online-Cmdlets in Ihre lokale Windows PowerShell-Sitzung importiert. Der Fortschritt des Importvorgangs wird in einer Statusanzeige dargestellt. Wenn Sie keine Fehlermeldungen erhalten, wurde die Verbindung erfolgreich hergestellt. Ein schneller Test ist die Ausführung eines Exchange Online-Cmdlets, z. B. von **Get-Mailbox**, und die Betrachtung der Ergebnisse.
  
Wenn Sie Fehlermeldungen erhalten, überprüfen Sie die folgenden Anforderungen:
  
- Ein häufig auftretendes Problem ist ein falsches Kennwort. Führen Sie die drei Schritte erneut durch und achten Sie besonders auf die korrekte Eingabe des Benutzernamens und Kennworts in Schritt 1.
    
- Das Benutzerkonto, mit dem Sie die Verbindung mit Exchange Online herstellen, muss für Remote-PowerShell aktiviert sein. Weitere Informationen finden Sie unter [Aktivieren oder Deaktivieren des Zugriffs auf Exchange Online PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=534018).
    
- TCP-Port 80 muss zwischen dem lokalen Computer und dem Remoteserver geöffnet sein. Er ist wahrscheinlich offen, es kann jedoch vorkommen, dass Ihre Organisation eine eingeschränkte Internetzugriffsrichtlinie verfolgt.
    
## <a name="call-the-cmdlet-directly-with-invoke-command"></a>Direktes Aufrufen des Cmdlets mit Invoke-Command

Das Importieren einer PowerShell-Remotesitzung (Schritt 3) kann ein langwieriger Vorgang sein, da _alle_ Exchange Online-Cmdlets mit einbezogen werden. Dies kann bei der Stapelverarbeitung ein Problem sein, wenn Sie z. B. Berichte ausführen oder Massenänderungen für verschiedene Mandanten durchführen. Als Alternative zur Verwendung von **Import-PSSession** können Sie Cmdlets, die Sie verwenden möchten, direkt mit **Invoke-Command** aufrufen. Um zum Beispiel das **Get-Milbox**-Cmdlet aufzurufen, ersetzen Sie diese Syntax für den `Import-PSSession $Session`-Befehl in Schritt 3:
  
```
Invoke-Command -Session $Session -ScriptBlock {Get-Mailbox}
```

## <a name="more-reporting-cmdlets"></a>Weitere Berichterstellungs-Cmdlets

Die Cmdlets, die Sie in diesem Thema verwenden, sind Windows PowerShell-Cmdlets. Weitere Informationen zu diesen Cmdlets finden Sie in den folgenden Themen:
  
- [Get-Credential](https://go.microsoft.com/fwlink/p/?LinkId=389618)
    
- [New-PSSession](https://go.microsoft.com/fwlink/p/?LinkId=389621)
    
- [Import-PSSession](https://go.microsoft.com/fwlink/p/?LinkId=389619)
    
- [Remove-PSSession](https://go.microsoft.com/fwlink/p/?LinkId=389620)
    
- [Set-ExecutionPolicy](https://go.microsoft.com/fwlink/p/?LinkId=389623)
    

