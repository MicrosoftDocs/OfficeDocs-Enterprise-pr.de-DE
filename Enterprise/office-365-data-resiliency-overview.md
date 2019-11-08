---
title: Datenresilienz in Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
description: Grundlegendes zur Ausfallsicherheit von Daten in Microsoft Office 365.
ms.openlocfilehash: 4bdd46689ca0dd9caa3da10fc57951bee3513b85
ms.sourcegitcommit: 9eb68633728cc78e9906dab222edbf9977b17e21
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2019
ms.locfileid: "38035792"
---
# <a name="data-resiliency-in-office-365"></a>Datenresilienz in Office 365

## <a name="introduction"></a>Einführung

In Anbetracht des komplexen Charakters von Cloud-Computing ist Microsoft sich bewusst, dass es sich nicht um einen Fall handelt, in dem die Dinge schief gehen, sondern eher wenn. Wir entwerfen unsere Cloud-Dienste, um die Zuverlässigkeit zu maximieren und die negativen Auswirkungen auf die Kunden zu minimieren, wenn es schief geht. Wir haben uns über die herkömmliche Strategie hinweggesetzt, sich auf komplexe physische Infrastrukturen zu verlassen, und wir haben Redundanz direkt in unsere Cloud-Dienste integriert. Wir verwenden eine Kombination aus weniger komplexer physischer Infrastruktur und intelligenter Software, die Datensicherheit in unseren Diensten aufbaut und hohe Verfügbarkeit für unsere Kunden bietet. 

## <a name="resiliency-and-recoverability-are-built-in"></a>Ausfallsicherheit und Wiederherstellbarkeit sind integriert 

Das Erstellen von Ausfallsicherheit und Wiederherstellung beginnt mit der Annahme, dass die zugrunde liegende Infrastruktur und die Prozesse zu einem bestimmten Zeitpunkt fehlschlagen: Hardware (Infrastruktur) schlägt fehl, der Mensch wird Fehler machen, und Software hat Bugs. Es wäre zwar falsch zu sagen, dass Softwareentwickler nicht über diese Dinge vor der Cloud nachdachten, wie diese Probleme in einer typischen IT-Implementierung behandelt wurden, war jedoch vor der Cloud sehr unterschiedlich:

- Zunächst waren Hardware-und Infrastruktur Schutz relevant. Dies bedeutet, dass Rechenzentren mit einer Zuverlässigkeit von 99,99% erhebliche Strom-und Netzwerkredundanz erforderlich machten und Server mit hardwarebasiertem Clustering, dualen Netzteilen, dualen Netzwerkschnittstellen und ähnlichem implementiert wurden. 
- Zweitens war Prozess von größter Bedeutung. Betriebsteams behielten strenge Verfahren, Wechsel Fenster wurden verwendet, und es gab häufig einen erheblichen Overhead im Projektmanagement. 
- Drittens erfolgte die Bereitstellung in einem Gletscher Tempo. Die Bereitstellung von Code ohne Besitz der Quelle bedeutete, auf Patch-Versionen zu warten, und Hauptversions Versionen betrafen Hardwareaustausch und erhebliche Investitionen. Darüber hinaus war das Zurücksetzen des Problems die einzige Möglichkeit, ein Problem zu beheben. Daher würden die meisten IT-Organisationen nur Hauptversionen bereitstellen, um zu verhindern, dass die Arbeit auf dem neuesten Stand ist. 
- Schließlich war die Skalierung der bereitgestellten Systeme sowie die Ebene ihrer Vernetzung historisch viel kleiner als jetzt. 

Kunden erwarten heute kontinuierliche Innovationen von Microsoft ohne Kompromisse bei der Qualität, und dies ist einer der Gründe, warum die Dienste und Software von Microsoft mit Flexibilität und Wiederherstellbarkeit entwickelt werden. 

## <a name="office-365-data-resiliency-principles"></a>Office 365 Grundsätze der Datenausfall Sicherheit

Ausfallsicherheit bezieht sich auf die Möglichkeit, dass ein Cloud-basierter Dienst bestimmten Arten von Fehlern Stand halten kann und dennoch aus Sicht der Kunden voll funktionsfähig bleibt. Datenausfall Sicherheit bedeutet, dass wichtige Kundendaten unabhängig von den auftretenden Fehlern in Office 365 intakt und unberührt bleiben. Zu diesem Zweck wurden Office 365 Dienste um fünf spezifische Ausfall Sicherheitsprinzipien entwickelt:

- Es gibt wichtige und nicht kritische Daten. Nicht kritische Daten (beispielsweise, ob eine Nachricht gelesen wurde) können in Szenarien mit seltenen Fehlern gelöscht werden. Wichtige Daten (beispielsweise Kundendaten wie e-Mail-Nachrichten) sollten unter extremen Kosten geschützt werden. Als Entwurfsziel sind zugestellte e-Mail-Nachrichten immer kritisch und Dinge wie, ob eine Nachricht gelesen wurde, sind nicht kritisch. 
- Kopien von Kundendaten müssen in unterschiedliche Fehler Zonen oder so viele fehlerdomänen wie möglich aufgeteilt werden (beispielsweise Rechenzentren, zugänglich für einzelne Anmeldeinformationen (Prozess, Server oder Operator)), um die Ausfall Isolierung bereitzustellen. 
- Kritische Kundendaten müssen auf fehlerhafte Teile von Atomarität, Konsistenz, Isolierung, Lebensdauer (ACID) überwacht werden. 
- Kundendaten müssen vor Beschädigung geschützt sein. Es muss aktiv gescannt oder überwacht, repariert und wiederhergestellt werden. 
- Die meisten Datenverluste resultieren aus Kundenaktionen, sodass Kunden sich selbst über eine GUI erholen können, mit der Sie versehentlich gelöschte Elemente wiederherstellen können. 
 
Durch den Aufbau unserer Cloud-Dienste für diese Prinzipien, gepaart mit robustem testen und Validierung, ist Office 365 in der Lage, die Anforderungen von Kunden zu erfüllen und zu übertreffen und gleichzeitig eine Plattform für kontinuierliche Innovationen und Verbesserungen sicherzustellen. 

## <a name="related-links"></a>Links zu verwandten Themen

- [Umgang mit Datenbeschädigung](office-365-dealing-with-data-corruption.md)
- [Schutz vor Schadsoftware und Ransomware](office-365-malware-and-ransomware-protection.md)
- [Überwachung und Selbstreparatur](office-365-monitoring-and-self-healing.md)
- [Exchange-Datenausfall Sicherheit](office-365-exchange-data-resiliency.md)