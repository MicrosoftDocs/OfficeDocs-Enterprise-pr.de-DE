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
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
ms.assetid: f4bd2439-3e41-4169-99f6-3fabdfa326ac
description: Installieren und Ausführen des Office 365-IdFix-Tools zum Bereinigen Ihres Active Directory, bevor Sie es mit Office 365 synchronisieren.
ms.openlocfilehash: a35b2a476f2b30eccc955b980eda6315b146af27
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085404"
---
# <a name="install-and-run-the-office-365-idfix-tool"></a>Installieren und Ausführen des Office 365 IdFix-Tools

IdFix identifiziert Fehler wie Duplikate und Formatierungsprobleme in Ihrem Verzeichnis, bevor Sie mit Office 365 synchronisieren. 
  
Damit Sie diese Aufgabe erfolgreich abschließen können, sollten Sie sich mit Benutzer-, Gruppen-und Kontaktobjekten in Active Directory vertraut machen.
  
Wenn Sie diese Aufgabe nicht abschließen können, gibt es einige andere Möglichkeiten. Diese Methoden sind möglicherweise einfacher, aber Sie können auch länger dauern oder andere Nachteile haben. Sie sind:
  
- **Führen Sie die Verzeichnissynchronisierung ohne Ausführen von IdFix aus.** Sie können Ihr Verzeichnis synchronisieren, ohne das IdFix-Tool auszuführen, es wird jedoch nicht empfohlen. Das Beheben von Fehlern vor der Synchronisierung dauert schneller und bietet häufig einen reibungsloseren Übergang zur Cloud. 
- **Stellen Sie einen Berater ein.** Durch Expertenhilfe können Ihre Benutzer schnell loslegen, und Ihr Verzeichnis wird synchronisiert. 
    
## <a name="what-you-need-to-run-idfix"></a>Voraussetzungen für das Ausführen von IdFix

Am einfachsten können Sie IdFix auf einem Computer installieren, der mit Ihrer Domäne verbunden ist. Sie können es auf dem Domänencontroller ausführen, aber es ist nicht erforderlich.
  
### <a name="idfix-hardware-requirements"></a>IdFix-Hardwareanforderungen

Der Computer, auf dem Sie IdFix installieren, muss diese minimalen Hardwareanforderungen erfüllen:
  
- 4 GB RAM
- 2 GB Festplattenspeicherplatz
    
### <a name="idfix-software-requirements"></a>IdFix-Softwareanforderungen

Der Computer, auf dem Sie IdFix installieren, muss derselben Active Directory-Domäne hinzugefügt werden, von der Sie Benutzer mit Office 365 synchronisieren möchten. Auf dem Computer muss .NET Framework 4,0 installiert sein. 
  
Wenn Sie Windows Server 2008 oder Windows Server 2012, ist .NET Framework wahrscheinlich bereits installiert. Ist dies nicht der Fall, können Sie [.net 4,0 aus dem Download Center](https://go.microsoft.com/fwlink/p/?LinkId=400475) oder über Windows Update herunterladen. 
  
### <a name="idfix-permissions-requirements"></a>IdFix-Berechtigungsanforderungen

Das Benutzerkonto, das Sie zum Ausführen von IdFix verwenden, muss über Lese-/Schreibzugriff auf das Verzeichnis verfügen.
  
Wenn Sie nicht sicher sind, ob Ihr Benutzerkonto diese Anforderungen erfüllt, und Sie nicht sicher sind, wie Sie überprüfen, können Sie IdFix installieren und ausführen. Wenn Ihr Benutzerkonto nicht über die richtigen Berechtigungen verfügt, wird bei der Ausführung von IdFix nur ein Fehler angezeigt.
  
## <a name="install-idfix"></a>Installieren von IdFix

Zum Installieren von IdFix können Sie **IdFix. exe**herunterladen und entpacken: 
  
1. Melden Sie sich am Computer an, auf dem Sie das IdFix-Tool installieren möchten.
    
2. Wechseln Sie zur Microsoft-Download Website für das [IdFix Dirsync Error Remediation Tool](https://go.microsoft.com/fwlink/?linkid=867219).
    
3. Klicken Sie auf **Herunterladen**.
    
4. Wenn Sie dazu aufgefordert werden, wählen Sie **Ausführen**aus.
    
5. Geben Sie im Dialogfeld **WinZip Self-Extractor** im Textfeld **unzip to Folder** den Speicherort ein, an dem Sie das IdFix-Tool installieren möchten, oder navigieren Sie zu diesem. Standardmäßig wird IdFix in `C:\Deployment Tools\`installiert. 
    
6. Wählen Sie **unzip**aus.
    
## <a name="run-the-idfix-tool"></a>Führen Sie das IdFix-Tool aus.

Führen Sie nach dem Installieren von IdFix das Tool zur Problemsuche in Ihrem Verzeichnis aus:
  
1. Melden Sie sich unter Verwendung eines Kontos mit Lese-/Schreibzugriff auf das Verzeichnis am Computer an, auf dem Sie IdFix installiert haben.
    
2. Wechseln Sie im Datei-Explorer zu dem Speicherort, an dem Sie IdFix installiert haben. Wenn Sie während der Installation den Standardordner ausgewählt haben, `C:\Deployment Tools\IdFix`wechseln Sie zu.
    
3. Doppelklicken Sie auf **IdFix.exe**. 
    
    ![Wählen Sie die Datei IdFix. exe aus.](media/a9387bbc-991f-41c2-a500-45e3ce574285.JPG)
  
4. Standardmäßig verwendet IdFix den mandantenfähigen Regelsatz, um die Einträge in Ihrem Verzeichnis zu testen. Dies ist der richtige Regelsatz für die meisten Office 365-Kunden. Wenn Sie jedoch ein Office 365 Dedicated-oder ITAR (International Traffic in Arms Regulations)-Kunde sind, können Sie IdFix so konfigurieren, dass stattdessen der dedizierte Regelsatz verwendet wird. Wenn Sie nicht sicher sind, welche Art von Kunden Sie sind, können Sie diesen Schritt gefahrlos überspringen. Klicken Sie auf das Zahnradsymbol in der Menüleiste, und wählen Sie dann **dediziert**aus, um den Regelsatz auf Dedicated festzulegen.
    
5. Wählen Sie **Query**aus.
    
    ![Wählen Sie Query in IdFix aus.](media/a07a7aa7-d0ac-4817-8757-946019813a57.JPG)
  
6. IdFix überprüft das gesamte Verzeichnis standardmäßig auf Fehler.
    
    Abhängig von der Größe des Verzeichnisses kann das Ausführen der Abfrage eine Weile dauern. Sie können den Fortschritt am unteren Rand des Hauptfensters des Tools ansehen. Wenn Sie auf **Abbrechen**klicken, müssen Sie von vorn beginnen.
    
    ![IdFix-Abfrage und Fehleranzahl.](media/da0198a0-7d4d-4afe-a256-e82f1330ada5.JPG)
  
7. Nachdem IdFix die Abfrage abgeschlossen hat, können Sie mit der Synchronisierung des Verzeichnisses fortfahren, falls keine Fehler vorliegen. Wenn Ihr Verzeichnis fehlerhaft ist, sollten Sie diese vor der Synchronisierung korrigieren. Wenn Sie genauere Informationen zu Fehlertypen und Empfehlungen zur bestmöglichen Möglichkeit zum Beheben von Fehlern benötigen, lesen Sie die Links am Ende dieses Themas. 
    
    Obwohl es nicht obligatorisch ist, die Fehler vor der Synchronisierung zu beheben, empfehlen wir ausdrücklich, dass Sie wenigstens alle durch IdFix zurückgegebenen Fehler überprüfen.
    
    Jeder Fehler wird in einer separaten Zeile im Hauptfenster des Tools angezeigt. 
    
8. Wenn Sie mit der vorgeschlagenen Änderung in der Spalte **UPDATE** einverstanden sind, wählen Sie in der Spalte **ACTION**, was IdFix vornehmen soll, um die Änderung zu implementieren. Klicken Sie dann auf **Übernehmen**. Wenn Sie auf **Übernehmen** klicken, nimmt das Tool die Änderungen im Verzeichnis vor.
    
    Sie müssen nach jeder Aktualisierung nicht auf **anwenden** klicken. Stattdessen können Sie mehrere Fehler beheben, bevor Sie auf **anwenden** klicken, und IdFix wird Sie alle gleichzeitig ändern. Sie können die Fehler nach Fehlertyp sortieren, indem Sie oben in der Spalte, in der die Fehlertypen aufgelistet werden, auf **Fehler** klicken. 
    
    Eine Strategie besteht darin, alle Fehler des gleichen Typs zu beheben. beheben Sie beispielsweise zuerst alle Duplikate, und wenden Sie Sie an. Korrigieren Sie als nächstes die Zeichenformat Fehler usw. Jedes Mal, wenn Sie die Änderungen übernehmen, erstellt das IdFix-Tool eine separate Protokolldatei, mit der Sie die Änderungen rückgängig machen können, falls Sie einen Fehler machen. Das [Transaktionsprotokoll](idfix-transaction-log.md) wird in dem Ordner gespeichert, in dem Sie IdFix installiert haben.  _C:\Deployment Tools\IdFix_ standardmäßig. 
    
    ![Beheben von Fehlern in IdFix.](media/5f051070-652c-4be7-98bf-312295e32371.png)
  
9. Nachdem alle Änderungen am Verzeichnis vorgenommen wurden, führen Sie IdFix erneut aus, um sicherzustellen, dass die von Ihnen vorgenommenen Korrekturen keine neuen Fehler einführten. Sie können diese Schritte beliebig oft wiederholen. Es empfiehlt sich, den Prozess einige Male zu durchlaufen, bevor Sie synchronisieren.
    
## <a name="i-want-to-refine-my-search-or-dig-deeper-into-the-errors-what-else-can-i-do-with-idfix"></a>Ich möchte meine Suche eingrenzen oder Fehler detaillierter ansehen. Was kann ich sonst noch mit IdFix anfangen?

Weitergehende Informationen sind in den folgenden Themen verfügbar:
  
- [Vorbereiten von Verzeichnisattributen für die Synchronisierung mit Office 365 mithilfe des IdFix-Tools](prepare-directory-attributes-for-synch-with-idfix.md) . Wenn Sie das Tool installiert haben, wechseln Sie zu diesem Thema, um detailliertere Anweisungen zum Ausführen des Tools, häufige Fehler, die auftreten werden, Empfohlene Korrekturen, Beispiele und bewährte Methoden für die Vorgehensweise bei einer hohen Anzahl von Fehlern. 
- [Referenz: Ausgeschlossene und unterstützte Objekte und Attribute für IdFix](idfix-excluded-and-supported-objects-and-attributes.md)  
- [Referenz: Office 365 IdFix-Transaktionsprotokoll](idfix-transaction-log.md)
    
## <a name="video-training"></a>Videoschulung

Weitere Informationen finden Sie in der Lektion [Installieren und Verwenden des IDFix-Tools](https://support.office.com/article/install-and-use-the-idfix-tool-4d81d73c-f172-4fd5-8542-f601c0c96aa9?ui=en-US&rs=en-US&ad=US), die Ihnen von LinkedIn Learning zur Verfügung gestellt wird.
  

