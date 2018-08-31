---
title: Vorbereiten von Verzeichnisattributen für die Synchronisierung mit Office 365 mithilfe des IdFix-Tools
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
ms.assetid: 497593cf-24c6-491c-940b-7c86dcde9de0
description: Enthält Anweisungen zur Verwendung von IdFix zum Vorbereiten und Bereinigen von Ihrem lokalen Verzeichnis vor der Synchronisierung mit Office 365.
ms.openlocfilehash: a4fc8af476ec8ffdd7d762796abe1ec210a1bacb
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540976"
---
# <a name="prepare-directory-attributes-for-synchronization-with-office-365-by-using-the-idfix-tool"></a>Vorbereiten von Verzeichnisattributen für die Synchronisierung mit Office 365 mithilfe des IdFix-Tools
Dieses Thema enthält ausführliche Anweisungen zum Ausführen des IdFix-Tools, einige häufige Fehler können auftreten, vorgeschlagene Fixes, Beispiele und bewährte Methoden für die auszuführende Aktion, wenn Sie eine große Anzahl von Fehlern verfügen.
  
## <a name="fixing-errors-in-your-directory-by-using-the-idfix-gui"></a>Beheben von Fehlern in Ihrem Verzeichnis mithilfe der IdFix-GUI
Sie [Führen Sie das Office 365-IdFix-Tool](install-and-run-idfix.md) zum Suchen nach Problemsuche in Ihrem Verzeichnis und beheben Sie die Fehler in der Benutzeroberfläche klicken Sie dann wie in diesem Thema beschrieben. Wenn eine leere Tabelle mit dem Tool zurückgegeben wurde, wurden keine Fehler gefunden. Wenn viele Probleme in Ihrem Verzeichnis vorhanden sind, kann schwierig sein, wenn das Tool Fehler zurückgegeben. Eine Möglichkeit, diese Lösung ist, beheben alle Fehler eines Typs zuerst, und fahren Sie mit dem nächsten Typ. 
  
1. Sehen Sie sich die Empfehlungen durch IdFix an, bevor Sie Änderungen vornehmen.
    
2. Sehen Sie die Liste der Fehler an, die IdFix zurückgegeben hat. Sie können die Fehler nach Fehlertyp sortieren, indem Sie oben in der Spalte auf **ERROR** klicken, in der die Fehlertypen aufgelistet werden. Wenn mehr als ein Fehler mit einem einzelnen Attribut verknüpft ist, werden die Fehler in einer Zeile kombiniert. Nach Möglichkeit stellt IdFix eine Empfehlung für eine Fehlerbehebung in der Spalte **UPDATE** dar Die Fehlerbehebung basiert auf einer Prüfung von anderen mit einem Objekt verknüpften Attributen. Obwohl diese in der Regel besser ist als das, was bereits im Verzeichnis vorhanden ist, können nur Sie entscheiden, was wirklich richtig ist. 
    
3. Wenn IdFix einen Vorschlag für eine Lösung für ein Fehler aufgrund eines duplizierten verfügt, das Update wird identifiziert durch eine der drei Kennzeichen am Anfang des Werts in der Spalte **UPDATE** beispielsweise `[E]john.doe@contoso.com`. Wenn Sie den Vorschlag annehmen, wenn Sie die Änderung zu übernehmen wird das Flag nicht in das Verzeichnis eingefügt werden. Nur der Wert der Vorschlag Flag, beispielsweise angewendet werden nach `john.doe@contoso.com`. Wenn Sie den Vorschlag annehmen möchten, wählen Sie die entsprechende Aktion aus der Spalte **Aktion** . Die Flags geben Aktionen wie folgt an: 
    
 - **[C]** Empfohlene Aktion **COMPLETE**. Der Wert muss nicht bearbeitet werden.
    
 - **[E]** Empfohlene Aktion **EDIT**. Der Wert sollte geändert werden, um einen Konflikt mit einem anderen Wert im Verzeichnis zu vermeiden.
    
 - **[R]** Empfohlene Aktion **REMOVE**. Der Wert ist ein SMTP-Proxy in einem nicht meldungsfähigen Objekt und kann wahrscheinlich sicher entfernt werden.
    
4. Einmal haben Sie gelesen und verstanden Fehler, aktualisieren Sie den Eintrag in der Spalte **Aktualisieren** mit Ihren Änderungen, und wählen Sie dann in der **Aktion** Spalte Sie IdFix ist, um die Änderung zu implementieren möchten. Beispielsweise zwei Benutzer möglicherweise ein `proxyAddress` , die als Duplikat identifiziert. Nur ein Benutzer können die `proxyAddress` für e-Mail-Übermittlung. Um dieses Problem zu beheben, die Spalte **Aktion** **abgeschlossen** für den Benutzer mit den richtigen Wert, und markiert die Spalte **Aktion** für den anderen Benutzer **zu entfernen** . Dies entfernt die `proxyAddress` -Attributs aus dem Benutzer, denen diese `proxyAddress` gehört nicht und es ist keine Änderung an dem Benutzer, für den dies `proxyAddress` korrekt ist.
    
## <a name="common-errors-and-fixes-detected-by-idfix"></a>Durch IdFix erkannte häufige Fehler und Fehlerbehebungen
In der folgenden Tabelle werden die durch IdFix erkannten Fehler beschrieben, und es werden die am häufigsten empfohlenen Fehlerbehebungen des Tools bereitgestellt. Zudem erfolgen in manchen Fällen Lösungsbeispiele.

|**FEHLER**|**Fehlertypbeschreibung**|**Empfohlene Fehlerbehebung**|**Beispiel**|
|:-----|:-----|:-----|:-----|
|**character** | Unzulässige Zeichen. Der Wert enthält ein Zeichen, das ungültig ist. | Die in der Spalte **UPDATE** angezeigte empfohlene Fehlerbehebung für den Fehler zeigt den Wert mit dem ungültigen entfernten Zeichen.  <br/> | Ein Leerzeichen am Ende der eine gültige e-Mail-Adresse ist ein ungültiges Zeichen, beispielsweise:  <br/> " `user@contoso.com` "  <br/> Ein führendes Leerzeichen am Anfang der eine gültige e-Mail-Adresse ist ein ungültiges Zeichen, beispielsweise:  <br/> " ` user@contoso.com `"  <br/>  Die `ú` Zeichen ist ein ungültiges Zeichen. |
|**duplicate** | Doppelter Eintrag. Der Wert verfügt über ein Duplikat im Bereich der Abfrage. Alle doppelten Werte werden als Fehler angezeigt. | Bearbeiten oder entfernen Sie Werte zum Beseitigen von Dopplungen. Das Tool stellt keine empfohlene Fehlerbehebung für Duplikate bereit. Vielmehr müssen Sie auswählen, welches der zwei oder mehr Duplikate richtig ist, und Sie müssen das Duplikat bzw. die Duplikate löschen. ||
|**format** | Formatierungsfehler. Der Wert verletzt die Formatierungsanforderungen für die Attributverwendung. | Das empfohlene "Update" zeigt den Wert mit den entfernten ungültigen Zeichen. Wenn keine ungültigen Zeichen vorhanden sind, sind "Update" und "Value" gleich. Es bleibt Ihnen überlassen zu bestimmen, was Sie wirklich im "Update" einbeziehen möchte. Das Tool stellt keine empfohlene Fehlerbehebung für alle Formatierungsfehler bereit. | Beispielsweise müssen SMTP-Adressen RFC 2822 entsprechen und MailNickName kann nicht gestartet oder mit einem Punkt enden. Weitere Informationen zu den Format-Anforderungen für Verzeichnisattributen finden Sie unter "Directory Verzeichnisobjekt und Vorbereitung" unter [Prepare to Provision Benutzer über Directory-Synchronisierung mit Office 365](prepare-for-directory-synchronization.md). |
|topleveldomain  <br/> |Domäne der obersten Ebene. Dies gilt für-Werte in Übereinstimmung mit [RFC 2822](https://go.microsoft.com/fwlink/p/?LinkId=401464) Formatierung. Wenn die Domäne der obersten Ebene nicht Internet routingfähig ist wird dies als Fehler identifiziert werden. Beispielsweise Local Endung SMTP-Adresse ist nicht routingfähige Internet und diese Fehler verursacht. |Ändern Sie den Wert auf eine internetroutingfähige Domäne wie `.com` oder `.net`. | Änderung `myaddress@fourthcoffee.local` auf `fourthcoffee.com` oder eine andere internetroutingfähige Domäne.  <br/> Anweisungen finden Sie unter [Vorbereiten eine nicht-routingfähigen Domäne für Directory-Synchronisierung (beispielsweise Local Domäne)](prepare-a-non-routable-domain-for-directory-synchronization.md). |
|**domainpart** | Domänenanteilfehler. Dies gilt für Werte gemäß der RFC 2822-Formatierung. Wenn die Domänenteilmenge des Werts ungültig ist und RFC 2822 nicht erfüllt, wird dies generiert. | Ändern Sie den Wert in eine, die mit RFC 2822 übereinstimmt. Angenommen, stellen Sie sicher, dass es keine Leerzeichen oder unzulässige Zeichen enthält. | Änderung `myaddress@fourth coffee.com` auf `myaddress@fourthcoffee.com`. |
|**domainpart_localpart** | Fehler beim lokalen Teil. Dies gilt für Werte gemäß der RFC 2822-Formatierung. Wenn der lokale Teil des Werts ungültig ist und RFC 2822 nicht erfüllt, wird dies generiert. |Ändern Sie den Wert in eine, die mit RFC 2822 übereinstimmt. Angenommen, stellen Sie sicher, dass es keine Leerzeichen oder unzulässige Zeichen enthält. |Änderung `my"work"address@fourthcoffee.com` auf `myworkaddress@fourthcoffee.com`. |
|**length** | Fehler bei der Länge. Der Wert überschreitet die Längenbegrenzung für das Attribut. Dies tritt am häufigsten auf, wenn das Verzeichnisschema geändert wurde.  | Das von IdFix empfohlene Update schneidet den Wert auf eine zulässige Länge zu.  <br/> Beachten Sie, dass dies zu unerwünschten Ergebnissen führen kann. Sie sollten die empfohlene Fehlerbehebung überprüfen und ggf. ändern, bevor Sie auf **Übernehmen** klicken. ||
|**blank**  | Leer oder null-Fehler. Der Wert verletzt die null-Beschränkung für zu synchronisierende Attribute. Nur wenige Attribute müssen einen Wert enthalten. | Das empfohlene Update verwendet nach Möglichkeit andere Attributwerte, um einen wahrscheinlichen Ersatz zu generieren. ||
|**mailmatch** | Dies gilt nur für Office 365 dediziert. Der Wert entspricht nicht das Mail-Attribut. | Das empfohlene Update werden die Mail-Attribut mit vorangestelltem "SMTP:". ||
    
## <a name="operations-you-can-perform-by-using-idfix"></a>Mithilfe von IdFix ausführbare Vorgänge
Um einen Fehler zu beheben, wählen Sie eine Option aus der Dropdownliste **Aktion** . Die folgende Tabelle beschreibt die **Aktion** Vorgänge, die Sie für die Attribute, die mit dem IdFix-Tool ausführen können. Wenn Sie in der Spalte **Aktion** leer lassen, wird das IdFix-Tool nicht auf dieser Fehler im Verzeichnis Aktion ausgeführt. 

|**AKTION**|**Aktionsbeschreibung**|**Beispiel**|
|:-----|:-----|:-----|
|**COMPLETE** | Der ursprüngliche Wert ist akzeptabel und sollte nicht geändert werden, obwohl er als ein Fehler identifiziert wurde. | Zwei Benutzer haben eine proxyAddress als Duplikat identifiziert. Nur ein Benutzer kann den Wert für die E-Mail-Übermittlung verwenden. Markieren Sie den Benutzer mit dem richtigen Wert als **COMPLETE**. |
|**ENTFERNEN** | Der Attributwert werden aus dem Quellobjekt gelöscht. Bei einem mehrwertigen Attribut `proxyAddresses`, nur der einzelne Wert dargestellt werden gelöscht. | Zwei Benutzer haben eine proxyAddress als Duplikat identifiziert. Nur ein Benutzer kann den Wert für die E-Mail-Übermittlung verwenden. Markieren Sie den Benutzer mit dem doppelten Wert als **REMOVE**. |
|**BEARBEITEN** | Die Informationen in der Spalte **UPDATE** wird so ändern Sie den Wert des Attributs verwendet. Wenn Sie ein gültiger Wert für die **Aktualisierung** von IdFix vorgeschlagen wurden hat, klicken Sie dann in der Spalte **Aktion** wählen Sie **Bearbeiten** und wechseln Sie zum nächsten Fehler auf. Wenn Sie den Vorschlag nicht gefällt, geben Sie einen neuen Anwendungspool in der Spalte **UPDATE** , und wählen Sie dann in der Spalte **Aktion** **Bearbeiten**. ||
|**RÜCKGÄNGIG MACHEN** | Diese Option ist nur verfügbar, wenn Sie die Wiederherstellung mithilfe eines Transaktionsprotokolls vorgenommen haben. Bei Wahl von **UNDO** wird der Attributwert auf den Originalwert zurückgesetzt. ||
|**FAIL** | Dieser Wert wird nur zurückgegeben, wenn ein **UPDATE** -Werts einen unbekannten Konflikt mit AD DS-Regeln verfügt. In diesem Fall können Sie den Wert in der Spalte **UPDATE** erneut bearbeiten, wenn Sie wissen, was der Fehler ist. Es kann notwendig, analysieren die Werte im mithilfe von ADSI Edit-Objekt sein. Weitere Informationen finden Sie unter [ADSI-Bearbeitung (adsiedit.msc)](https://go.microsoft.com/fwlink/p/?LinkId=401170). ||

Klicken Sie nach der Auswahl einer **ACTION** für einen Fehler oder einen Fehlerstapel auf **Übernehmen**. Wenn Sie auf **Übernehmen** klicken, nimmt das Tool die Änderungen im Verzeichnis vor. Sie können Fehlerbehebungen für mehrere Fehler bereitstellen, bevor Sie auf **Übernehmen** klicken, und IdFix ändert sie alle gleichzeitig.

Ausführen von IdFix erneut aus, um sicherzustellen, dass die vorgenommene Korrekturen neue Fehler verursachen, haben. Sie können diese Schritte so oft wie gewünscht zu wiederholen. Es ist ratsam, den Prozess ein paar Mal durchlaufen, bevor Sie synchronisieren.
    
## <a name="changing-the-rule-set-used-by-idfix"></a>Ändern des durch IdFix verwendeten Regelsatzes
IdFix verwendet standardmäßig den mehrinstanzenfähigen Regelsatz, der die Einträge in Ihrem Verzeichnis zu testen. Hierbei handelt es sich um den richtigen Regelsatz für die meisten Office 365 = Kunden. Wenn Sie ein Office 365 dedizierte oder ITAR (International Datenverkehr in Waffen Vorschriften) Kunde sind, können Sie IdFix Verwendung den dedizierten Regelsatz stattdessen konfigurieren. Wenn Sie sicher, dass welche Art von Kunden nicht, die Sie sind, können Sie bedenkenlos diesen Schritt überspringen. Wenn den Regelsatz, dediziert festlegen möchten, klicken Sie auf das Zahnradsymbol in der Menüleiste, und klicken Sie dann auf **dedizierten**.
  
## <a name="changing-the-scope-of-the-search-used-by-idfix"></a>Ändern des durch IdFix verwendeten Suchbereichs
IdFix überprüft standardmäßig das gesamte Verzeichnis. Bei Bedarf können Sie das Tool so konfigurieren, dass es stattdessen nach einer bestimmten Unterstruktur sucht. Klicken Sie dafür auf der Menüleiste auf das Symbol zum Filtern, und geben Sie eine gültige Unterstruktur ein.
  
## <a name="rolling-back-your-changes-by-using-the-idfix-gui"></a>Rollback der Änderungen mithilfe IdFix-GUI
Bei jedem Klick auf **Übernehmen** , um die Änderungen, übernehmen erstellt das IdFix-Tool eine separate Datei mit dem Namen eines Transaktionsprotokolls, das die Änderungen werden, mit denen, die Sie soeben erstellt haben. Das Transaktionsprotokoll können Rollback nur die Änderungen, die in das aktuelle Protokoll sind für den Fall, dass Sie einen Fehler machen. Wenn Sie einen Fehler machen, während Sie aktualisieren möchten, können Sie die zuletzt angewendeten Änderungen durch Klicken auf **Rückgängig**rückgängig machen. Wenn Sie auf **Rückgängig**klicken, verwendet IdFix das Transaktionsprotokoll Rollback nur diese Änderungen, die in das aktuelle Transaktionsprotokoll sind. Weitere Informationen zur Verwendung des Transaktionsprotokolls finden Sie unter [Referenz: Office 365-IdFix-Transaktionsprotokoll](idfix-transaction-log.md).