# Widget Grist — Atterrissage des grands programmes

Le fichier `src/grist-widget.html` fournit un widget personnalisé Grist en lecture seule. Il reprend les quatre vues interactives du projet **Atterrissage GP** : dépenses annuelles par nature, personnel par année et structure, personnel par structure et GP, puis personnel par année et GP. Les filtres communs peuvent être rendus indépendants sur les trois graphiques de personnel.

## Table source

Dans Grist, sélectionnez la table importée depuis `Anthony2.xlsx` dans le panneau **Données**, puis associez les champs demandés par le widget aux colonnes suivantes :

| Champ du widget | Colonne Anthony2 |
| --- | --- |
| GP | `GP` |
| Programme | `Programme` |
| Exercice | `Ope - Budget Exercice` |
| Nature | `Ope - Nature Dépenses` |
| Consommation AE | `Consommation AE` |
| Positionné AE | `Ope - Positionné AE` |
| Structure | `Structure organisationnelle héritée bis` |

Le widget agrège les lignes de la table sélectionnée. Il utilise `Consommation AE` jusqu’en 2025 inclus, puis `Ope - Positionné AE` à partir de 2026. Les deux programmes IdEx « Ingénierie de pilotage » et « Soutien aux missions ESRI » sont séparés ; les autres sont regroupés. La structure `Non défini` est présentée sous `ND`.

## Intégration

Hébergez `src/grist-widget.html` sur une adresse HTTPS accessible depuis le navigateur qui ouvre Grist, puis ajoutez-la comme **Custom Widget** avec cette URL. Dans Grist, accordez au widget l’accès en lecture à la table et confirmez les sept associations de colonnes. Pour une instance Grist auto-hébergée, adaptez l’URL du script `grist-plugin-api.js` en haut du fichier au domaine de cette instance.

Le widget ne contient ni données budgétaires ni identifiants. Les données sont lues à la volée depuis la table liée ; les changements de cette table actualisent les graphiques.
