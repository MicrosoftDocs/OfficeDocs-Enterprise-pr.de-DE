---
title: Vorbereiten von Verzeichnisattributen für die Synchronisierung mit Office 365 mithilfe des IdFix-Tools
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
ms.assetid: 497593cf-24c6-491c-940b-7c86dcde9de0
description: Enthält Anweisungen zur Verwendung von IdFix zum Vorbereiten und Bereinigen des lokalen Verzeichnisses vor dem Synchronisieren mit Office 365.
ms.openlocfilehash: 134f9cd60e65b64b91fb42fd7cbfa300626fc867
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "34071071"
---
# <a name="prepare-directory-attributes-for-synchronization-with-office-365-by-using-the-idfix-tool"></a>Vorbereiten von Verzeichnisattributen für die Synchronisierung mit Office 365 mithilfe des IdFix-Tools
Dieses Thema enthält detaillierte Anweisungen zum Ausführen des IdFix-Tools, einige häufige Fehler, die auftreten können, Vorschläge zu Behebungen, Beispielen und bewährten Methoden für die Vorgehensweise bei einer hohen Anzahl von Fehlern.
  
## <a name="fixing-errors-in-your-directory-by-using-the-idfix-gui"></a>Beheben von Fehlern in Ihrem Verzeichnis mithilfe der IdFix-GUI
[Führen Sie das Office 365 IdFix-Tool](install-and-run-idfix.md) aus, um nach Problemen in Ihrem Verzeichnis zu suchen, und beheben Sie dann die Fehler in der GUI, wie in diesem Thema beschrieben. Wenn eine leere Tabelle vom Tool zurückgegeben wird, wurden keine Fehler ermittelt. Wenn in Ihrem Verzeichnis viele Probleme auftreten, kann es überwältigend sein, wenn das Tool die Fehler zurückgibt. Eine Möglichkeit, dies zu bewältigen, besteht darin, alle Fehler eines Typs zuerst zu beheben und dann zum nächsten Typ zu wechseln. 
  
1. Bevor Sie mit der Durchführung von Änderungen beginnen, sollten Sie sich die Empfehlungen von IdFix ansehen.
    
2. Überprüfen Sie die Liste der Fehler, die IdFix zurückgegeben hat. Sie können die Fehler nach Fehlertyp sortieren, indem Sie oben in der Spalte, in der die Fehlertypen aufgelistet werden, auf **Fehler** klicken. Wenn einem einzelnen Attribut mehrere Fehler zugeordnet sind, werden die Fehler in einer Zeile zusammengefasst. Wenn möglich, IdFix eine Empfehlung für eine Korrektur in der Spalte **Update** . Das Update basiert auf einer Überprüfung anderer Attribute, die einem Objekt zugeordnet sind. Während diese sind in der Regel besser als das, was sich bereits im Verzeichnis, nur Sie können entscheiden, was wirklich genau ist. 
    
3. Wenn IdFix einen Vorschlag zur Behebung eines Duplizierungs Fehlers hat, wird das Update durch eines der drei Flags am Anfang des Werts in der **Update** -Spalte identifiziert, beispielsweise `[E]john.doe@contoso.com`. Wenn Sie den Vorschlag akzeptieren, wird das Flag nicht in das Verzeichnis eingefügt, wenn Sie die Änderung anwenden. Nur der Wert, der dem Vorschlags Kennzeichen folgt, wird angewendet, Beispiels `john.doe@contoso.com`Weise. Wenn Sie den Vorschlag annehmen möchten, wählen Sie die entsprechende Aktion in der Spalte **Aktion** aus. Die Flags zeigen Aktionen wie folgt an: 
    
 - **[C]** vorgeschlagene Aktion **abgeschlossen**. Der Wert muss nicht bearbeitet werden.
    
 - **[E]** vorgeschlagene Aktion **Bearbeiten**. Der Wert sollte geändert werden, um einen Konflikt mit einem anderen Wert im Verzeichnis zu vermeiden.
    
 - **[R]** vorgeschlagene Aktion **Entfernen**. Der Wert ist ein SMTP-Proxy für ein nicht-e-Mail-aktiviertes Objekt und kann wahrscheinlich gefahrlos entfernt werden.
    
4. Nachdem Sie die Fehler gelesen und verstanden haben, aktualisieren Sie den Eintrag in der Spalte **Aktualisieren** mit Ihren Änderungen, und wählen Sie dann in der Spalte **Aktion** aus, was IdFix für die Implementierung der Änderung tun soll. Zwei Benutzer haben beispielsweise eine `proxyAddress` als Duplikat identifiziert. Nur ein Benutzer kann die für `proxyAddress` die e-Mail-Übermittlung verwenden. Um dies zu beheben, markieren Sie die Spalte **Aktion** für den Benutzer mit dem richtigen Wert **abgeschlossen** , und markieren **Sie** die Spalte **Aktion** für den anderen Benutzer. Dadurch wird das `proxyAddress` Attribut des Benutzers entfernt, zu dem `proxyAddress` dieser nicht gehört, und es wird keine Änderung an dem Benutzer vorgenommen `proxyAddress` , für den dies richtig ist.
    
## <a name="common-errors-and-fixes-detected-by-idfix"></a>Von IdFix erkannte häufige Fehler und Fixes
In der folgenden Tabelle werden die von IdFix erkannten Fehler beschrieben, die am häufigsten empfohlenen Fixes aus dem Tool bereitgestellt werden, und in einigen Fällen werden Beispiele dafür bereitgestellt.

|**Fehler**|**Fehlertyp Beschreibung**|**Vorgeschlagene Korrektur**|**Beispiel**|
|:-----|:-----|:-----|:-----|
|**Zeichen** | Ungültige Zeichen. Der Wert enthält ein ungültiges Zeichen. | Die vorgeschlagene Korrektur für den in der Spalte **Update** angezeigten Fehler zeigt den Wert mit dem ungültigen Zeichen entfernt.  <br/> | Ein abschließender Leerraum am Ende einer gültigen e-Mail-Adresse ist ein ungültiges Zeichen, beispielsweise:  <br/> " `user@contoso.com` "  <br/> Ein führender Leerraum am Anfang einer gültigen e-Mail-Adresse ist ein ungültiges Zeichen, beispielsweise:  <br/> " ` user@contoso.com `"  <br/>  Das `ú` Zeichen ist ein ungültiges Zeichen. |
|**doppelte** | Doppelter Eintrag. Der Wert hat ein Duplikat innerhalb des Bereichs der Abfrage. Alle doppelten Werte werden als Fehler angezeigt. | Bearbeiten oder Entfernen von Werten, um Duplizierung zu vermeiden. Das Tool bietet keinen empfohlenen Fix für Duplikate. Stattdessen müssen Sie auswählen, welche der beiden Duplikate die richtige ist, und die doppelten Einträge löschen. ||
|**format** | Formatierungsfehler. Der Wert verstößt gegen die Formatanforderungen für die Attributverwendung. | Das vorgeschlagene Update zeigt den Wert an, dessen ungültige Zeichen entfernt wurden. Wenn es keine ungültigen Zeichen gibt, werden Update und Value gleich angezeigt. Sie müssen bestimmen, was Sie im Update wirklich wünschen. Das Tool bietet keinen empfohlenen Fix für alle Formatierungsfehler. | Beispielsweise müssen SMTP-Adressen mit RFC 2822 und mailNickname nicht mit einem Punkt beginnen oder enden. Weitere Informationen zu den Formatanforderungen für Verzeichnisattribute finden Sie unter "Directory-Objekt und-Attribut Vorbereitung" in [Vorbereiten der Bereitstellung von Benutzern über die Verzeichnissynchronisierung in Office 365](prepare-for-directory-synchronization.md). |
|topleveldomain  <br/> |Domäne der obersten Ebene. Dies gilt für Werte, die der [RFC 2822](https://go.microsoft.com/fwlink/p/?LinkId=401464) -Formatierung unterliegen. Wenn die Domäne der obersten Ebene nicht im Internet routingfähig ist, wird diese als Fehler identifiziert. Beispiel: eine SMTP-Adresse, die in. local endet, ist nicht im Internet routingfähig und würde diesen Fehler verursachen. |Ändern Sie den Wert in eine im `.com` Internet Routingfähige Domäne `.net`wie oder. | Wechseln `myaddress@fourthcoffee.local` Sie `fourthcoffee.com` zu oder in eine andere, im Internet Routingfähige Domäne.  <br/> Anweisungen hierzu finden Sie unter [Vorbereiten einer nicht routingfähigen Domäne (beispielsweise. Local Domain) für die Verzeichnissynchronisierung](prepare-a-non-routable-domain-for-directory-synchronization.md). |
|**domainpart** | Domänen teilfehler. Dies gilt für Werte, die der RFC 2822-Formatierung unterliegen. Wenn der Domänenteil des Werts ungültig ist und RFC 2822 nicht entspricht, wird dieser generiert. | Ändern Sie den Wert in einen, der RFC 2822 entspricht. Stellen Sie beispielsweise sicher, dass Sie keine Leerzeichen oder ungültigen Buchstaben enthält. | Wechseln `myaddress@fourth coffee.com` Sie `myaddress@fourthcoffee.com`zu. |
|**domainpart_localpart** | Fehler beim lokalen WebPart. Dies gilt für Werte, die der RFC 2822-Formatierung unterliegen. Wenn der lokale Teil des Werts ungültig ist und RFC 2822 nicht entspricht, wird dieser generiert. |Ändern Sie den Wert in einen, der RFC 2822 entspricht. Stellen Sie beispielsweise sicher, dass Sie keine Leerzeichen oder ungültigen Buchstaben enthält. |Wechseln `my"work"address@fourthcoffee.com` Sie `myworkaddress@fourthcoffee.com`zu. |
|**length** | LÄNGENFEHLER. Der Wert verstößt gegen den Längen Grenzwert für das Attribut. Dies wird am häufigsten auftreten, wenn das Verzeichnisschema geändert wurde.  | Das von IdFix vorgeschlagene Update schneidet den Wert auf die zulässige Länge ab.  <br/> Beachten Sie, dass dies zu unerwünschten Ergebnissen führen kann. Sie sollten die vorgeschlagene Korrektur überarbeiten und gegebenenfalls ändern, bevor Sie auf über **nehmen**klicken. ||
|**leere**  | Leer oder Null-Fehler. Der Wert verstößt gegen die NULL-Einschränkung für die zu synchronisierenden Attribute. Nur wenige Attribute müssen einen Wert enthalten. | Wenn möglich, nutzt das vorgeschlagene Update andere Attributwerte, um eine wahrscheinliche Ersetzung zu generieren. ||
|**mailmatch** | Dies gilt nur für Office 365 dediziert. Der Wert stimmt nicht mit dem Mail-Attribut überein. | Das vorgeschlagene Update ist der e-Mail-Attributwert, der mit "SMTP:" vorangestellt wird. ||
    
## <a name="operations-you-can-perform-by-using-idfix"></a>Vorgänge, die Sie mithilfe von IdFix ausführen können
Zum Beheben eines Fehlers wählen Sie in der Dropdownliste **Aktion** eine Option aus. In der folgenden Tabelle werden die **Aktions** Vorgänge beschrieben, die Sie mit dem IdFix-Tool für Attribute ausführen können. Wenn Sie die Spalte **Aktion** leer lassen, führt das IdFix-Tool keine Aktion für diesen bestimmten Fehler im Verzeichnis aus. 

|**Aktion**|**Aktionsbeschreibung**|**Beispiel**|
|:-----|:-----|:-----|
|**Komplette** | Der ursprüngliche Wert ist akzeptabel und sollte nicht geändert werden, obwohl er als Fehler identifiziert wurde. | Zwei Benutzer haben ein proxyAddress, das als Duplikat identifiziert wird. Nur einer kann den Wert für die e-Mail-Übermittlung verwenden. Markieren Sie den Benutzer mit dem korrekten Wert als **abgeschlossen**. |
|**Entfernen** | Der Attributwert wird aus dem Source-Objekt gelöscht. Bei einem mehrwertigen Attribut wird beispielsweise `proxyAddresses`nur der angezeigte Einzelwert gelöscht. | Zwei Benutzer haben ein proxyAddress, das als Duplikat identifiziert wird. Nur einer kann den Wert für die e-Mail-Übermittlung verwenden. Markieren Sie den Benutzer mit dem doppelten Wert als **Remove**. |
|**Bearbeiten** | Die Informationen in der Spalte **Update** werden verwendet, um den Attributwert zu ändern. Wenn von IdFix ein gültiger **Aktualisierungs** Wert vorgeschlagen wurde, wählen Sie in der Spalte **Aktion** die Option **Bearbeiten** aus, und fahren Sie mit dem nächsten Fehler fort. Wenn Sie den Vorschlag nicht mögen, geben Sie in der Spalte **Update** einen neuen ein, und klicken Sie dann in der Spalte **Aktion** auf **Bearbeiten**. ||
|**Undo** | Diese Option ist nur verfügbar, wenn Sie aus einem Transaktionsprotokoll wiederhergestellt haben. Wenn Sie **Rückgängig**auswählen, wird der Attributwert auf den ursprünglichen Wert zurückgesetzt. ||
|**FAIL** | Dieser Wert wird nur zurückgegeben, wenn ein **Aktualisierungs** Wert einen unbekannten Konflikt mit AD DS-Regeln aufweist. In diesem Fall können Sie den Wert in der Spalte **Update** erneut bearbeiten, wenn Sie wissen, was der Fehlschlag ist. Möglicherweise müssen Sie die Werte im Objekt mithilfe von ADSI-Bearbeitung analysieren. Weitere Informationen finden Sie unter [ADSI-Bearbeitung (AdsiEdit. msc)](https://go.microsoft.com/fwlink/p/?LinkId=401170). ||

Klicken Sie auf **anwenden**, nachdem Sie eine **Aktion** für einen Fehler oder einen Batch von Fehlern ausgewählt haben. Wenn Sie auf über **nehmen**klicken, nimmt das Tool die Änderungen im Verzeichnis vor. Sie können Fixes für mehrere Fehler bereitstellen, bevor Sie auf **anwenden** klicken, und IdFix wird Sie alle gleichzeitig ändern.

Führen Sie IdFix erneut aus, um sicherzustellen, dass die von Ihnen vorgenommenen Korrekturen keine neuen Fehler einführten. Sie können diese Schritte beliebig oft wiederholen. Es empfiehlt sich, den Prozess einige Male zu durchlaufen, bevor Sie synchronisieren.
    
## <a name="changing-the-rule-set-used-by-idfix"></a>Ändern des Regelsatzes, der von IdFix verwendet wird
Standardmäßig verwendet IdFix den mandantenfähigen Regelsatz, um die Einträge in Ihrem Verzeichnis zu testen. Dies ist der richtige Regelsatz für die meisten Office 365 =-Kunden. Wenn Sie jedoch ein Office 365 Dedicated-oder ITAR (International Traffic in Arms Regulations)-Kunde sind, können Sie IdFix so konfigurieren, dass stattdessen der dedizierte Regelsatz verwendet wird. Wenn Sie nicht sicher sind, welche Art von Kunden Sie sind, können Sie diesen Schritt gefahrlos überspringen. Klicken Sie auf das Zahnradsymbol in der Menüleiste, und klicken Sie dann auf **dediziert**, um den Regelsatz auf Dedicated festzulegen.
  
## <a name="changing-the-scope-of-the-search-used-by-idfix"></a>Ändern des Bereichs der Suche, die von IdFix verwendet wird
Standardmäßig durchsucht IdFix das gesamte Verzeichnis. Wenn Sie möchten, können Sie das Tool konfigurieren, um stattdessen eine bestimmte Unterstruktur zu durchsuchen. Klicken Sie dazu in der Menüleiste auf das Filter Symbol, und geben Sie eine gültige Unterstruktur ein.
  
## <a name="rolling-back-your-changes-by-using-the-idfix-gui"></a>Zurücksetzen der Änderungen mithilfe der IdFix-GUI
Jedes Mal, wenn Sie auf **anwenden** klicken, um Änderungen zu übernehmen, erstellt das IdFix-Tool eine separate Datei mit dem Namen Transaktionslog, in der die soeben vorgenommenen Änderungen aufgelistet werden. Sie können das Transaktionsprotokoll verwenden, um nur die Änderungen zurückzusetzen, die sich im neuesten Protokoll befinden, falls Sie einen Fehler machen. Wenn Sie beim Aktualisieren einen Fehler machen, können Sie die zuletzt angewendeten Änderungen rückgängig machen, indem Sie auf **Rückgängig**klicken. Wenn Sie auf **Rückgängig**klicken, verwendet IdFix das Transaktionsprotokoll, um nur die Änderungen zurückzusetzen, die sich im letzten Transaktionsprotokoll befinden. Weitere Informationen zur Verwendung des Transaktionsprotokolls finden Sie unter [Reference: Office 365 IdFix Transaction Log](idfix-transaction-log.md).