---
title: "Verbinden mit Exchange Online-Mandanten über eine Remotesitzung von Windows PowerShell für Partner mit delegierten Zugriffsberechtigungen (Delegated Access Permissions, DAP)"
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: DecEntMigration
ms.assetid: ae5f1a87-8b77-4f93-a1b8-56f800aeb283
description: 'Zusammenfassung: Verwenden Sie eine Remotesitzung von Windows PowerShell, um eine Verbindung mit Exchange Online anhand des DelegatedOrg-Parameters herzustellen.'
ms.openlocfilehash: 9bb6a5a316f4bc23c6586da825b8755cf755f484
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2017
---
# <a name="connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated-access-permissions-dap-partners"></a>Verbinden mit Exchange Online-Mandanten über eine Remotesitzung von Windows PowerShell für Partner mit delegierten Zugriffsberechtigungen (Delegated Access Permissions, DAP)

 **Zusammenfassung:** Verwenden Sie eine Remotesitzung von Windows PowerShell, um eine Verbindung mit Exchange Online anhand des _DelegatedOrg_-Parameters herzustellen.
  
Mit Remote-Windows PowerShell können Sie die Exchange Online-Einstellungen über die Befehlszeile verwalten. Sie verwenden Windows PowerShell auf dem lokalen Computer und stellen eine Remotesitzung mit Exchange Online her. Dies ist ein Verfahren mit drei Schritten: Zuerst geben Sie Ihre Exchange Online-Anmeldeinformationen ein, dann geben Sie die erforderlichen Verbindungseinstellungen an, und zum Schluss importieren Sie die Exchange Online-Cmdlets in Ihre lokale Windows PowerShell-Sitzung, um Sie dafür verwenden zu können.
  
## <a name="what-do-you-need-to-know-before-you-begin"></a>Was sollten Sie wissen, bevor Sie beginnen?

- Geschätzte Zeit bis zum Abschließen des Vorgangs: 5 Minuten
    
- Sie können folgende Versionen von Windows verwenden:
    
  - Windows 10
    
  - Windows 8.1 oder Windows 8
    
  - Windows Server 2012 R2 oder Windows Server 2012
    
  - Windows 7 Service Pack 1 (SP1)*
    
  - Windows Server 2008 R2 SP1*
    
    * Sie müssen das .NET Framework 4.5.1 oder das .NET Framework 4.5 und dann entweder Windows Management Framework 4.0 oder Windows Management Framework 3.0 installieren. Weitere Informationen finden Sie in den folgenden Ressourcen:
    
  - [Installieren von .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868)
    
  - [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) oder[Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344)
    
- Informationen zu Tastenkombinationen, die möglicherweise für die Verfahren in diesem Thema gelten, finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](https://go.microsoft.com/fwlink/p/?LinkId=534017).
    
## 

> [!IMPORTANT]
> Dieses Verfahren ist nur fürPartner mit delegierten Zugriffsberechtigungen (Delegated Access Permission, DAP). Wenn Sie kein DAP-Partner sind, verwenden Sie dieses Verfahren nicht. 
  
DAP-Partner sind Syndication- und Cloudlösungsanbieter-Partner (CSP-Partner). Häufig handelt es sich um Netzwerk- oder Telekom-Anbieter für andere Unternehmen. Sie bündeln Abonnements in ihren Serviceangeboten für ihre Kunden. Sie verfügen über einen Partnermandanten, dem automatisch die Berechtigung „Verwalten im Namen von" (Administer On Behalf Of, AOBO) für ihren Office 365-Kundenmandanten erteilt wird, damit sie alle ihre Kundenmandanten verwalten und Berichte dazu erstellen können.
  
## <a name="connect-to-exchange-online"></a>Herstellen einer Verbindung mit Exchange Online

1. Öffnen Sie auf Ihrem lokalen Computer Windows PowerShell, und führen Sie dann den folgenden Befehl aus.
    
  ```
  $UserCredential = Get-Credential
  ```

    Geben Sie im Dialogfeld **Bei Windows PowerShell anmelden** Ihren DAP-Administratorbenutzernamen und das Kennwort ein, und klicken Sie dann auf **OK**.
    
2. Führen Sie den folgenden Befehl aus, wobei Sie _<customer tenant domain name>_ durch den Namen der Mandantendomäne ersetzen, mit der Sie eine Verbindung herstellen möchten.
    
  ```
  $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.outlook.com/powershell-liveid?DelegatedOrg=<customer tenant domain name>-Credential $UserCredential -Authentication Basic -AllowRedirection
  ```

    Der wichtigste Schritt für diesen Befehl ist anzugeben, auf welchen Kunden für die Berichtsinformationen zugegriffen werden soll. Sie geben dies durch den  _ConnectionURI_-Parameter an, für den Sie den vollqualifizierten Domänennamen (FQDN) des anfänglichen Domänennamens als Wert für den  _DelegatedOrg_-Parameter angeben. Hierdurch wird Remote-Windows PowerShell für Exchange Online PowerShell mitgeteilt, mit welchem Endpunkt Remote-Windows PowerShell eine Verbindung herstellen soll. Remote-Windows PowerShell muss mit der Office 365-Berichterstellung bei jeder Ausführung eines Berichts eine Verbindung im Kontext eines bestimmten Benutzers herstellen. Nachdem Sie diesen Kunden angegeben haben, werden alle der folgenden Befehle im Kontext dieses Kunden ausgeführt. Auf diese Weise kann der Partner auf alle verfügbaren Berichte für diesen Kunden zugreifen.
    
3. Führen Sie den folgenden Befehl aus.
    
  ```
  Import-PSSession $Session
  ```

> [!NOTE]
> Es können höchstens drei Sitzungen gleichzeitig unter einem Konto ausgeführt werden. Stellen Sie sicher, dass die Remote-Windows PowerShell-Sitzung getrennt wird, wenn Sie alle Aufgaben ausgeführt haben. Wenn Sie das Windows PowerShell-Fenster schließen, ohne die Sitzung zu trennen, verbrauchen Sie möglicherweise alle Remote-Windows PowerShell-Sitzungen, die Ihnen zur Verfügung stehen, sodass Sie dann warten müssen, bis die Sitzungen abgelaufen sind. Führen Sie zum Trennen der Windows PowerShell-Remotesitzung den folgenden Befehl aus. >  `Remove-PSSession $Session`
  
## <a name="how-do-you-know-this-worked"></a>Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Nach Schritt 3 werden die Exchange Online-Cmdlets in Ihre lokale Windows PowerShell-Sitzung importiert. Der Fortschritt des Importvorgangs wird in einer Statusanzeige dargestellt. Wenn Sie keine Fehlermeldungen erhalten, wurde die Verbindung erfolgreich hergestellt. Ein schneller Test ist die Ausführung eines Exchange Online-Cmdlets, z. B. von **Get-Mailbox**, und die Betrachtung der Ergebnisse.
  
Wenn Sie Fehlermeldungen erhalten, überprüfen Sie die folgenden Anforderungen:
  
- Ein häufig auftretendes Problem ist ein falsches Kennwort. Führen Sie die drei Schritte erneut durch und achten Sie besonders auf die korrekte Eingabe des Benutzernamens und Kennworts in Schritt 1.
    
- Um die Abwehr von DoS-Angriffen (Denial of Service) zu unterstützen, ist die Anzahl der offenen Windows PowerShell-Verbindungen zu Ihrer Exchange Online-Organisation auf drei beschränkt.
    
- Windows PowerShell muss zum Ausführen von Skripts konfiguriert werden. Sie müssen diese Einstellung nur einmalig auf Ihrem Computer konfigurieren, und nicht bei jedem Verbindungsaufbau. Um Windows PowerShell für das Ausführen von signierten Skripts zu aktivieren, müssen Sie den folgenden Befehl in einem Windows PowerShell-Fenster mit erhöhten Rechten ausführen (ein Windows PowerShell-Fenster, das Sie durch Auswahl von **Als Administrator ausführen**) geöffnet haben.
    
  ```
  Set-ExecutionPolicy RemoteSigned
  ```

- Das Benutzerkonto, mit dem Sie die Verbindung mit Exchange Online herstellen, muss für Remote-Windows PowerShell aktiviert sein. Weitere Informationen finden Sie unter [Verwalten des Remote-PowerShell-Zugriffs in Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534018).
    
- TCP-Port 80 muss zwischen dem lokalen Computer und dem Remoteserver geöffnet sein. Er ist wahrscheinlich offen, es kann jedoch vorkommen, dass Ihre Organisation eine eingeschränkte Internetzugriffsrichtlinie verfolgt.
    
## <a name="call-the-cmdlet-directly-with-invoke-command"></a>Direktes Aufrufen des Cmdlets mit Invoke-Command

Das Importieren einer Windows PowerShell-Remotesitzung kann ein langwieriger Vorgang sein, da alle Exchange Online-Cmdlets mit einbezogen werden. Dies kann bei der Stapelverarbeitung ein Problem sein, wenn Sie z. B. Berichte ausführen oder Massenänderungen für verschiedene Mandanten durchführen. Als Alternative zur Verwendung von **Import-PSSession** können Sie Cmdlets, die Sie verwenden möchten, direkt mit **Invoke-Command** aufrufen. Um zum Beispiel das **get-mailbox** -Cmdlet aufzurufen, ersetzen Sie `Import-PSSession $Session` mit der folgenden Syntax.
  
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
    

