# Widget Grist — Atterrissage des grands programmes

Le fichier `src/grist-widget.html` fournit un widget personnalisé Grist en lecture seule, avec cinq graphiques séparés par onglet. Le bouton **Mapping**, en haut à droite, ouvre des menus déroulants pour choisir la clé source de chaque champ ; les clés reçues de Grist sont listées et la correspondance détectée est présélectionnée. Le widget déclare également ses champs cibles avec `grist.mapColumn` pour le sélecteur de colonnes Grist. Chaque graphique propose un bouton **Zoom** : la fenêtre agrandie conserve sa légende interactive. Survolez un segment pour voir sa valeur, son pourcentage du total et le total de la barre. Cliquez sur une étiquette de l’axe horizontal pour agrandir uniquement la barre correspondante. Dans les graphiques 4 et 5, un deuxième clic sur le même segment ouvre aussi sa répartition par programme.

## Table source

Dans Grist, sélectionnez la table importée depuis `Anthony2.xlsx` dans le panneau **Données**, puis associez les champs demandés par le widget aux colonnes suivantes :

| Champ demandé dans le widget | Colonne source à associer |
| --- | --- |
| GP | `GP` |
| Programme | La colonne contenant le nom du programme |
| Exercice | `Ope - Budget Exercice` |
| Nature | `Ope - Nature Dépenses` |
| Montant unique | La colonne qui contient déjà le montant AE à agréger |
| Structure | `Structure organisationnelle héritée bis` |
| Thématique | `Thématiques` |
| Statut (facultatif, pour le compteur supérieur) | `Statut` |

Le montant est lu dans un champ unique : le widget ne choisit plus entre consommé et positionné selon l’année. Les filtres sont affichés une seule fois au-dessus du graphique actif. Les graphiques 2 à 5 suivent les filtres du graphique 1 par défaut; modifier un filtre les désolidarise automatiquement, et recocher **Suivre les filtres communs** les réaligne. Tous les programmes sont sélectionnés par défaut. Le filtre **Programmes** propose une sélection de GP pour réduire les cases affichées. Les graphiques 2 à 5 agrègent les natures sélectionnées; choisir uniquement **Personnel (PRS)** permet de retrouver une vue centrée sur le personnel. Chaque légende filtre les séries de son graphique. Les GP, y compris IdEx, sont utilisés tels que fournis. Une structure vide ou `Non défini` est affichée sous `ND`; une thématique vide sous `Non renseignée`.

## Intégration

Hébergez `src/grist-widget.html` sur une adresse HTTPS accessible depuis le navigateur qui ouvre Grist, puis ajoutez-la comme **Custom Widget** avec cette URL. Dans Grist, accordez au widget l’accès en lecture à la table. Après réception de données, ouvrez **Mapping** et renseignez les clés source si les suggestions ne correspondent pas. Si aucune clé source n’apparaît, vérifiez que Grist transmet bien les colonnes de la table au widget. Pour une instance Grist auto-hébergée, adaptez l’URL du script `grist-plugin-api.js` en haut du fichier au domaine de cette instance.

Le widget ne contient ni données budgétaires ni identifiants. Les données sont lues à la volée depuis la table liée ; les changements de cette table actualisent les graphiques.
