---
title: Installieren und Ausführen des Office 365 IdFix-Tools
ms.author: robmazz
author: robmazz
manager: laurawi
ms.audience: Admin
ms.topic: get-started-article
f1_keywords:
- O365E_HRCSetupAADConnectIDFixLM617036
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
ms.assetid: f4bd2439-3e41-4169-99f6-3fabdfa326ac
description: Informationen zum Installieren und Ausführen des Office 365-IdFix-Tools, die die active Directory-Bereinigung unterstützen, bevor Sie die Synchronisierung mit Office 365 vornehmen.
ms.openlocfilehash: c485d8397aa32005a34b77f886b9bc8f4e857f1b
ms.sourcegitcommit: 9c493c4e18e83491d106c5e9bab55d1a89298879
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/26/2018
ms.locfileid: "26674429"
---
# <a name="install-and-run-the-office-365-idfix-tool"></a>Installieren und Ausführen des Office 365 IdFix-Tools

IdFix identifiziert Fehler wie Duplikate und Probleme mit der Formatierung in Ihrem Verzeichnis aus, bevor Sie zu Office 365 synchronisieren. 
  
Um diese Aufgabe erfolgreich abgeschlossen wurde, sollte das Arbeiten mit Benutzer-, Gruppen- und Kontaktobjekten in Active Directory vertraut sein.
  
Wenn Sie diese Aufgabe ausführen können, sind einige andere Aspekte, die Sie ausführen können. Diese Methoden möglicherweise ist es einfacher, aber sie können auch länger dauern oder andere Nachteile haben. Sie sind:
  
- **Directory-Synchronisierung ohne Ausführen IdFix.** Sie können Ihr Verzeichnis synchronisieren, ohne das IdFix-Tool ausführen, aber es wird nicht empfohlen. Beheben von Fehlern, bevor Sie synchronisieren weniger Zeit und bietet oftmals einen fließender Übergang in die Cloud. 
- **Stellen Sie einen Berater ein.** Durch Expertenhilfe können Ihre Benutzer schnell loslegen, und Ihr Verzeichnis wird synchronisiert. 
    
## <a name="what-you-need-to-run-idfix"></a>Voraussetzungen für das Ausführen von IdFix

Die einfachste Einstieg IdFix zum ist und ausgeführt wird, ihn auf einem Computer zu installieren, die mit der Domäne verbunden ist. Sie können ihn auf dem Domänencontroller ausführen, wenn Sie möchten, aber es nicht erforderlich ist.
  
### <a name="idfix-hardware-requirements"></a>IdFix-Hardwareanforderungen

Der Computer, auf dem Sie IdFix installieren, muss diese Mindestanforderungen an die Hardware erfüllt:
  
- 4 GB RAM
- 2 GB freier Festplattenspeicher
    
### <a name="idfix-software-requirements"></a>IdFix-Softwareanforderungen

Der Computer, auf dem Sie IdFix installieren, muss mit derselben Active Directory-Domäne verknüpft werden aus der Sie Benutzer zu Office 365 synchronisieren möchten. Der Computer muss auch .NET Framework 4.0 installiert haben. 
  
Wenn Sie Windows Server 2008 oder Windows Server 2012 ausgeführt werden, ist möglicherweise bereits .NET Framework installiert. Wenn nicht, können Sie auf [Download .NET 4.0 aus dem Downloadcenter](https://go.microsoft.com/fwlink/p/?LinkId=400475) oder über Windows Update. 
  
### <a name="idfix-permissions-requirements"></a>IdFix-Berechtigungsanforderungen

Das Benutzerkonto, das Sie zum Ausführen von IdFix verwenden, muss über Lese-/Schreibzugriff auf das Verzeichnis verfügen.
  
Wenn Sie nicht sicher sind, wenn Ihr Benutzerkonto diese Anforderungen erfüllt, und Sie sind nicht sicher sind, wie Sie überprüfen, können Sie installieren und Ausführen von IdFix. Wenn Ihr Benutzerkonto nicht über die richtigen Berechtigungen verfügen, wird IdFix einfach einen Fehler angezeigt, wenn Sie versuchen, um Sie auszuführen.
  
## <a name="install-idfix"></a>Installieren von IdFix

Zum Installieren von IdFix herunter und Entpacken Sie **IdFix.exe**: 
  
1. Melden Sie sich am Computer an, auf dem Sie das IdFix-Tool installieren möchten.
    
2. Wechseln Sie zu Microsoft-Downloadwebsite für das [IdFix DirSync Error Remediation-Tool](https://go.microsoft.com/fwlink/?linkid=867219).
    
3. Klicken Sie auf **Herunterladen**.
    
4. Wenn Sie aufgefordert werden, wählen Sie **Ausführen**aus.
    
5. Klicken Sie im Dialogfeld **WinZip Self-Extractor** in das Textfeld **Extrahieren nach der Ordner** Geben Sie, oder wechseln Sie zum Speicherort, in dem Sie das IdFix-Tool installieren möchten. Standardmäßig wird in IdFix installiert `C:\Deployment Tools\`. 
    
6. Wählen Sie auf **Unzip**.
    
## <a name="run-the-idfix-tool"></a>Führen Sie das IdFix-Tool aus.

Führen Sie nach dem Installieren von IdFix das Tool zur Problemsuche in Ihrem Verzeichnis aus:
  
1. Melden Sie sich unter Verwendung eines Kontos mit Lese-/Schreibzugriff auf das Verzeichnis am Computer an, auf dem Sie IdFix installiert haben.
    
2. Wechseln Sie im Datei-Explorer zu dem Speicherort, in dem Sie IdFix installiert haben. Wenn Sie während der Installation den Standardordner ausgewählt haben, fahren Sie mit `C:\Deployment Tools\IdFix`.
    
3. Doppelklicken Sie auf **IdFix.exe**. 
    
    ![Wählen Sie die Datei IdFix.exe.](media/a9387bbc-991f-41c2-a500-45e3ce574285.JPG)
  
4. IdFix verwendet standardmäßig den mehrinstanzenfähigen Regelsatz, der die Einträge in Ihrem Verzeichnis zu testen. Dies ist der richtigen Regelsatz für die meisten Office 365-Kunden. Wenn Sie ein Office 365 dedizierte oder ITAR (International Datenverkehr in Waffen Vorschriften) Kunde sind, können Sie IdFix Verwendung den dedizierten Regelsatz stattdessen konfigurieren. Wenn Sie sicher, dass welche Art von Kunden nicht, die Sie sind, können Sie bedenkenlos diesen Schritt überspringen. Wenn den Regelsatz, dediziert festlegen möchten, klicken Sie auf das Zahnradsymbol in der Menüleiste, und wählen Sie dann **dediziert**.
    
5. Wählen Sie auf **Abfrage**.
    
    ![Wählen Sie die Abfrage in IdFix.](media/a07a7aa7-d0ac-4817-8757-946019813a57.JPG)
  
6. IdFix überprüft das gesamte Verzeichnis standardmäßig auf Fehler.
    
    Je nach der Größe des Verzeichnisses kann das Ausführen der Abfrage eine Weile dauern. Sie können den Fortschritt am unteren Rand des Tools im Hauptfenster überwachen. Wenn Sie auf **Abbrechen**klicken, müssen Sie völlig neu zu starten.
    
    ![Anzahl von IdFix Abfrage und Fehler.](media/da0198a0-7d4d-4afe-a256-e82f1330ada5.JPG)
  
7. Nach Abschluss der IdFix die Abfrage können Sie nun und synchronisieren Ihr Verzeichnis aus, wenn keine Fehler aufgetreten sind. Wenn in Ihrem Verzeichnis Fehler aufgetreten sind, wird empfohlen, dass Sie diese beheben, bevor Sie synchronisieren. Wenn Sie weitere Informationen zu Fehlertypen und Empfehlungen zur die beste Möglichkeit, diese zu beheben möchten, finden Sie unter den Links am Ende dieses Themas. 
    
    Obwohl es nicht obligatorisch ist, die Fehler vor der Synchronisierung zu beheben, empfehlen wir ausdrücklich, dass Sie wenigstens alle durch IdFix zurückgegebenen Fehler überprüfen.
    
    Jeder Fehler wird in einer separaten Zeile im Hauptfenster des Tools angezeigt. 
    
8. Wenn Sie mit der vorgeschlagenen Änderung in der Spalte **UPDATE** einverstanden sind, wählen Sie in der Spalte **ACTION**, was IdFix vornehmen soll, um die Änderung zu implementieren. Klicken Sie dann auf **Übernehmen**. Wenn Sie auf **Übernehmen** klicken, nimmt das Tool die Änderungen im Verzeichnis vor.
    
    Sie müssen nicht nach jeder Aktualisierung auf **Übernehmen** klicken. Stattdessen können Sie mehrere Fehler beheben, bevor Sie auf **Übernehmen** und IdFix sie alle gleichzeitig ändern. Sie können die Fehler werden vom Fehlertyp sortieren, indem Sie **Fehler** am oberen Rand der Spalte, in der die Fehlertypen aufgelistet. 
    
    Eine Strategie besteht darin, beheben Sie alle Fehler des gleichen Typs; Angenommen, beheben Sie zuerst alle Duplikate und anwenden. Im nächsten Schritt die Zeichen Formatfehler beheben und so weiter. Jedes Mal Sie die Änderungen zu übernehmen, erstellt das IdFix-Tool eine separate Protokolldatei, die Sie verwenden können, um die Änderungen rückgängig zu machen, für den Fall, dass Sie einen Fehler machen. Das [Transaktionsprotokoll](idfix-transaction-log.md) wird in den Ordner gespeichert, die Sie in IdFix installiert.  _C:\Deployment Tools\IdFix_ standardmäßig. 
    
    ![Korrigieren von Fehlern in IdFix.](media/5f051070-652c-4be7-98bf-312295e32371.png)
  
9. Nachdem alle Ihre Änderungen bestehen aus in das Verzeichnis, das Ausführen von IdFix erneut aus, um sicherzustellen, dass die vorgenommene Korrekturen neue Fehler verursachen, haben. Sie können diese Schritte so oft wie gewünscht zu wiederholen. Es ist ratsam, den Prozess ein paar Mal durchlaufen, bevor Sie synchronisieren.
    
## <a name="i-want-to-refine-my-search-or-dig-deeper-into-the-errors-what-else-can-i-do-with-idfix"></a>Ich möchte meine Suche eingrenzen oder Fehler detaillierter ansehen. Was kann ich sonst noch mit IdFix anfangen?

Weitergehende Informationen sind in den folgenden Themen verfügbar:
  
- [Vorbereiten von Verzeichnisattributen für die Synchronisierung mit Office 365 mithilfe des IdFix-Tools](prepare-directory-attributes-for-synch-with-idfix.md) . Nach der Installation des Tools, springen zu diesem Thema für detailliertere Anweisungen zur Ausführung des Tools die häufig auftretender wird, vorgeschlagen, Updates, Beispiele und bewährte Methoden für die auszuführende Aktion, wenn Sie eine große Anzahl von Fehlern vorhanden sind. 
- [Referenz: Ausgeschlossene und unterstützte Objekte und Attribute für IdFix](idfix-excluded-and-supported-objects-and-attributes.md)  
- [Referenz: Office 365 IdFix-Transaktionsprotokoll](idfix-transaction-log.md)
    
## <a name="video-training"></a>Videoschulung

Weitere Informationen finden Sie unter Lektion [Installieren und verwenden Sie das IDFix-Tool](https://support.office.com/article/install-and-use-the-idfix-tool-4d81d73c-f172-4fd5-8542-f601c0c96aa9?ui=en-US&rs=en-US&ad=US), bereitgestellt von LinkedIn Learning.
  

