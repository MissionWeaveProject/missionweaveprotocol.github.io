---
title: SDK
description:
  Wähle ein offizielles MissionWeaveProtocol SDK und prüfe seinen aktuellen
  Konformitätsumfang.
sidebar:
  label: Übersicht
  order: 1
---

MissionWeaveProtocol bietet eine vollständige Python-Referenzimplementierung und
fünf offizielle Protokoll-SDKs. Jedes SDK wird unabhängig versioniert und pinnt
den exakten Protokoll-Commit sowie die Inhalts-Digests der implementierten
Protokollartefakte. Die folgenden Zahlen beziehen sich auf den Protokoll-Commit
[`33e47ad`](https://github.com/missionweaveprotocol/missionweaveprotocol/commit/33e47ad8a7318f942de77fb72dbb054d85881b40).

## Funktions- und Statusmatrix

| SDK                                                                  | Aktueller Umfang                     | Protokoll-Bindings | Schema- und Vektorkonformität | Vollständige verhaltensbezogene Runtime |
| -------------------------------------------------------------------- | ------------------------------------ | ------------------ | ----------------------------- | --------------------------------------- |
| [Python](https://github.com/missionweaveprotocol/python-sdk)         | Vollständige Referenzimplementierung | Ja                 | 56/56 Vektoren                | Ja                                      |
| [Go](https://github.com/missionweaveprotocol/go-sdk)                 | Offizielles Protokoll-SDK            | Ja                 | 56/56 Vektoren                | Nein                                    |
| [TypeScript](https://github.com/missionweaveprotocol/typescript-sdk) | Offizielles Protokoll-SDK            | Ja                 | 56/56 Vektoren                | Nein                                    |
| [Java](https://github.com/missionweaveprotocol/java-sdk)             | Offizielles Protokoll-SDK            | Ja                 | 56/56 Vektoren                | Nein                                    |
| [Rust](https://github.com/missionweaveprotocol/rust-sdk)             | Offizielles Protokoll-SDK            | Ja                 | 56/56 Vektoren                | Nein                                    |
| [C++](https://github.com/missionweaveprotocol/cpp-sdk)               | Offizielles Protokoll-SDK            | Ja                 | 56/56 Vektoren                | Nein                                    |

Schema- und Vektorkonformität umfasst strikte JSON-Verarbeitung, Offline-
Validierung anhand der 21 gepinnten Draft-2020-12-Schemas, kanonisches JSON und
Inhalts-IDs, Ed25519-Signaturen, Frame-Validierung sowie die 56 gepinnten
Konformitätsvektoren. Sie belegt allein keine Konformität für Planung,
Persistenz, Wiederherstellung, Transport oder anderes Runtime-Verhalten.

## Ein SDK auswählen

Nutze den [Leitfaden zum Python SDK](./python/), wenn du die vollständige
Referenz-Runtime einschließlich Core, Agent Runtime, Worker Scheduler, Group
Gateway, Speicheradaptern und ausführbarem POC benötigst.

Nutze das Go-, TypeScript-, Java-, Rust- oder C++-Repository, wenn du native
Protokoll-Bindings, Validierung, Kanonisierung, Signaturen und Frame Codecs
benötigst. Installations- und Prüfkommandos werden in der README des jeweiligen
Repository gepflegt. Die Protokollspezifikation und die Konformitätsartefakte
bleiben normativ.
