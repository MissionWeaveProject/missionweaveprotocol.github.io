---
title: Child Mission
description:
  Décomposition récursive de WorkItem complexes en Mission Group bornés, sans
  perdre la portée, le budget, les Evidence ni la responsabilité humaine.
sidebar:
  order: 6
---

:::caution[Projet de norme 0.1]

Ceci est un guide d’apprentissage non normatif. Le
[dépôt canonique du protocole](https://github.com/missionweaveprotocol/missionweaveprotocol)
reste normatif.

:::

Un WorkItem suffisamment complexe peut devenir une **Child Mission**. La Child
Mission possède son propre Group, son Coordinator, son graphe de WorkItem, ses
Membership, son budget, son échéance et sa politique d’Approval. Le WorkItem
parent et la Child Mission se référencent mutuellement.

```text
Root Mission and Group
└── parent WorkItem becomes blocked
    └── Child Mission and its own Group
        ├── child Coordinator
        ├── child WorkItems and Evidence
        └── child Approval
            └── result returns as Evidence and Artifacts
                for the parent WorkItem
```

:::note[Une Mission possède toujours un seul Group]

La création d’une Child Mission ne transforme pas le Group parent en salon de
discussion imbriqué. La Child Mission reçoit un Group distinct et ne partage
avec son parent que des résumés autorisés, des Artifacts, des Evidence et des
liens stables.

:::

## Autorité et Approval

Par défaut, le Coordinator de la Child Mission examine et soumet son résultat.
Le Parent Coordinator agit comme MissionOwner de la Child Mission et l’approuve
au nom du WorkItem parent. La politique de risque de l’Organization peut
également exiger une approbation humaine directe.

Le résultat approuvé de la Child Mission devient une Evidence et des Artifacts
pour le WorkItem parent. Le Parent Coordinator reçoit les changements d’état,
les résumés, les estimations révisées, les motifs de blocage, les escalades de
budget ou de politique et les résultats finaux. Il n’a pas besoin de chaque
Message de la Child Mission, mais conserve un droit d’inspection autorisé à la
demande. Le MissionOwner racine peut inspecter l’arbre complet des Mission.

## La portée se réduit à chaque niveau

Le graphe parent-enfant doit rester acyclique. Le budget, l’échéance, les
capacités, l’accès aux données et les permissions de l’enfant doivent être des
sous-ensembles de ceux du parent. Les Organization configurent une profondeur
maximale par défaut et exigent l’Approval explicite du MissionOwner ou de la
politique au-delà de ce seuil.

La limite de profondeur est un garde-fou, pas un plafond fixe. Un travail
complexe légitime peut continuer lorsqu’une Approval explicite accorde la portée
ou la profondeur supplémentaire.

## Un échec n’entraîne pas automatiquement celui du parent

Une Child Mission en échec émet une Evidence d’échec structurée et bloque ou
fait échouer le WorkItem parent selon sa politique déclarée. Le Parent
Coordinator peut replanifier, réviser la portée, créer une Child Mission de
remplacement ou annuler la branche. L’échec ne se propage automatiquement que si
la politique d’achèvement du parent déclare l’enfant indispensable et ne prévoit
aucune alternative.

## Child Mission ou Follow-up Mission ?

- Utilisez une **Child Mission** pour achever un WorkItem complexe au sein d’une
  Mission parente active.
- Utilisez une **Follow-up Mission** pour une correction, une remédiation ou un
  travail supplémentaire après qu’une Mission approuvée est devenue immuable.

Pour toutes les règles, consultez les sections normatives sur les
[Mission parentes et enfants](https://github.com/missionweaveprotocol/missionweaveprotocol/blob/main/spec/PROTOCOL.md#14-parent-and-child-missions)
et le
[cycle de vie des Mission](https://github.com/missionweaveprotocol/missionweaveprotocol/blob/main/spec/PROTOCOL.md#7-mission-and-group-lifecycle).
