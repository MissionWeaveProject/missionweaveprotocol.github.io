---
title: Untergeordnete Mission
description:
  Rekursive Zerlegung komplexer WorkItem in begrenzte untergeordnete Missionen
  mit eigener Group, ohne Umfang, Budget, Evidence oder menschliche
  Verantwortlichkeit zu verlieren.
sidebar:
  order: 6
---

:::caution[Draft Standard 0.1]

Dies ist ein nicht normativer Lernleitfaden. Das
[kanonische Protokoll-Repository](https://github.com/missionweaveprotocol/missionweaveprotocol)
bleibt normativ.

:::

Aus einem ausreichend komplexen WorkItem kann eine **untergeordnete Mission
(Child Mission)** entstehen. Die untergeordnete Mission ist eine eigenständige
Mission und kein WorkItem. Sie besitzt eine eigene Group, einen Coordinator,
einen WorkItem-Graphen, Membership, Budget, Frist und eine Approval-Richtlinie.
Das übergeordnete WorkItem und die untergeordnete Mission verweisen aufeinander.

```text
Wurzel-Mission und Group
└── übergeordnetes WorkItem wird `blocked`
    └── untergeordnete Mission mit eigener Group
        ├── Coordinator der untergeordneten Mission
        ├── WorkItem der untergeordneten Mission und Evidence
        └── Approval der untergeordneten Mission
            └── Ergebnis kehrt als Evidence und Artifact
                zum übergeordneten WorkItem zurück
```

:::note[Eine Mission hat weiterhin genau eine Group]

Das Erstellen einer untergeordneten Mission verwandelt die übergeordnete Group
nicht in einen verschachtelten Chatraum. Die untergeordnete Mission erhält eine
getrennte Group und teilt mit der übergeordneten Mission nur autorisierte
Zusammenfassungen, Artifact, Evidence und stabile Verweise.

:::

## Autorität und Approval

Standardmäßig prüft der Coordinator der untergeordneten Mission deren Ergebnis
und reicht es ein. Der Coordinator der übergeordneten Mission handelt als
MissionOwner der untergeordneten Mission und genehmigt sie im Namen des
übergeordneten WorkItem. Die Risikorichtlinie der Organization kann zusätzlich
eine direkte menschliche Approval verlangen.

Das genehmigte Ergebnis der untergeordneten Mission wird zu Evidence und
Artifact für das übergeordnete WorkItem. Der Coordinator der übergeordneten
Mission erhält Statusänderungen, Zusammenfassungen, überarbeitete Schätzungen,
Blockaden, Budget- oder Richtlinieneskalationen und Endergebnisse. Er benötigt
nicht jede Message der untergeordneten Mission, behält aber autorisierten
Zugriff für bedarfsgesteuerte Prüfungen. Der MissionOwner der Root Mission kann
den vollständigen Mission-Baum einsehen.

## Der Umfang wird nach unten enger

Der Eltern-Kind-Graph muss azyklisch bleiben. Budget, Frist, Capability,
Datenzugriff und Berechtigungen einer untergeordneten Mission müssen Teilmengen
der übergeordneten Mission sein. Jede Organization konfiguriert eine
standardmäßige Maximaltiefe und verlangt jenseits dieses Schwellenwerts eine
ausdrückliche Approval des MissionOwner oder der Richtlinie.

Die Tiefenbegrenzung ist eine Leitplanke, keine feste Obergrenze. Berechtigte
komplexe Arbeit kann fortgesetzt werden, nachdem eine ausdrückliche Approval den
zusätzlichen Umfang oder die zusätzliche Tiefe gewährt.

## Ein Fehlschlag lässt das übergeordnete WorkItem nicht automatisch scheitern

Eine fehlgeschlagene untergeordnete Mission erzeugt strukturierte
Fehler-Evidence und blockiert das übergeordnete WorkItem oder lässt es gemäß
seiner festgelegten Richtlinie fehlschlagen. Der Coordinator der übergeordneten
Mission kann neu planen, den Umfang überarbeiten, eine untergeordnete
Ersatzmission erstellen oder den Zweig abbrechen. Ein Fehlschlag wird nur dann
automatisch weitergegeben, wenn die Abschlussrichtlinie des übergeordneten
WorkItem die untergeordnete Mission als unverzichtbar und ohne Alternative
einstuft.

## Untergeordnete Mission oder Follow-up Mission?

- Verwende eine **untergeordnete Mission**, um ein komplexes WorkItem innerhalb
  einer aktiven übergeordneten Mission abzuschließen.
- Verwende eine **Follow-up Mission** für Korrektur, Abhilfe oder zusätzliche
  Arbeit, nachdem eine genehmigte Mission unveränderlich geworden ist.

Die vollständigen Regeln stehen in den normativen Abschnitten zu
[übergeordneten und untergeordneten Missionen](https://github.com/missionweaveprotocol/missionweaveprotocol/blob/main/spec/PROTOCOL.md#14-parent-and-child-missions)
und zum
[Mission-Lebenszyklus](https://github.com/missionweaveprotocol/missionweaveprotocol/blob/main/spec/PROTOCOL.md#7-mission-and-group-lifecycle).
