# NovaTel — Customer Churn & Retention Analytics

**Analyse de l'attrition client et pilotage de la fidélisation avec Power BI**

`Power BI` · `Power Query` · `DAX` · `Business Intelligence` · `Data Analytics` · `Customer Retention`

---

## 1. Présentation du projet

NovaTel est un projet de Business Intelligence consacré à l'analyse de la perte client (*customer churn*) dans le secteur des télécommunications.

L'objectif est de comprendre quels profils de clients quittent l'entreprise, d'identifier les segments les plus exposés et de mesurer les enjeux financiers associés à ces départs.

Le projet repose sur le jeu de données public **IBM Telco Customer Churn**, contenant les informations de 7 043 clients d'un opérateur télécom fictif.

À partir de ces données, j'ai conçu un rapport Power BI interactif composé de six pages, allant de la vue générale de l'activité jusqu'à un simulateur de fidélisation.

**NovaTel est le nom fictif donné à cette étude de cas.** Il ne s'agit pas de données internes provenant d'une entreprise réelle.

### Problématique métier

**Comment une entreprise de télécommunications peut-elle exploiter ses données clients pour mieux comprendre la perte graduelle de cleint, identifier ses populations à risque et orienter ses actions de fidélisation ?**

Le rapport cherche à répondre à quatre questions :

1. Quelle est l'ampleur de la perte client ?
2. Quels profils et caractéristiques sont associés aux taux de départ les plus élevés ?
3. Quel montant de revenu mensuel est associé aux clients perdus ?
4. Quels résultats théoriques pourrait produire une réduction du churn ?

---

## 2. Objectifs du projet

### Objectifs métier

- Mesurer le taux d'attrition et le taux de fidélisation.
- Comparer les comportements des clients actifs et perdus.
- Identifier les segments présentant les taux de churn les plus élevés.
- Étudier les relations entre ancienneté, contrats, services et départs.
- Quantifier le revenu mensuel associé aux clients perdus.
- Proposer des pistes d'action pour améliorer la fidélisation.
- Simuler plusieurs scénarios de réduction de l'attrition.

### Objectifs techniques

- Préparer et contrôler un jeu de données dans Power Query.
- Construire un modèle de données exploitable dans Power BI.
- Créer des mesures DAX pour le suivi des indicateurs métier.
- Développer des visualisations interactives et cohérentes.
- Mettre en place des filtres, interactions et éléments de navigation.
- Concevoir un simulateur fondé sur des hypothèses ajustables.
- Documenter les choix techniques et les résultats de l'analyse.

---

## 3. Données utilisées

### Source

**IBM Telco Customer Churn**

Source publique : [IBM Community — Telco Customer Churn](https://community.ibm.com/community/user/blogs/steven-macko/2019/07/11/telco-customer-churn-1113)

Le jeu de données contient **7 043 observations clients**.

Chaque ligne correspond à un client et comporte des informations relatives à son profil, aux services souscrits, à sa facturation et à son statut de départ.

### Principales familles de variables

| Catégorie | Exemples d'informations |
|---|---|
| Identification | ID Client |
| Profil client | Genre, client senior, partenaire, personnes à charge |
| Relation commerciale | Ancienneté, type de contrat |
| Services | Téléphone, Internet, sécurité en ligne, assistance technique, streaming |
| Facturation | Facturation électronique, mode de paiement |
| Données financières | Charges mensuelles, charges totales |
| Variable cible | Départ client |

### Périmètre de l'analyse

L'étude porte sur l'ensemble des 7 043 clients présents dans le fichier.

Elle analyse les caractéristiques associées à leur statut de départ. Les résultats ne constituent pas une prédiction individuelle du churn.

---

## 4. Préparation et contrôle des données

La préparation a été réalisée dans **Power Query**, avant la création des indicateurs et des visualisations.

Les opérations du projet comprennent notamment la vérification de la qualité des données, la gestion des types, la préparation des colonnes utiles à l'analyse et la création de catégories destinées à la segmentation.

### Contrôles qualité réalisés

| Contrôle | Résultat |
|---|---|
| Nombre de clients | 7 043 |
| Identifiants distincts | 7 043 |
| Identifiants uniques | 7 043 |
| Doublons d'identifiant | 0 |
| Valeurs manquantes | 0 % après préparation |
| Erreurs de colonnes | 0 % après préparation |
| Profilage des colonnes | Ensemble du jeu de données |

Les contrôles ont été réalisés à partir des fonctions de profilage de Power Query.

La vérification de l'unicité des identifiants confirme que chaque client est représenté une seule fois dans la table analysée.

### Traitement des données financières

Le champ des charges totales a fait l'objet d'une préparation afin de pouvoir être utilisé dans les calculs numériques.

Les choix de traitement sont documentés dans le dossier professionnel, notamment pour les valeurs initialement absentes ou non exploitables.

### Colonnes d'analyse

Des regroupements ont également été préparés pour faciliter les comparaisons, notamment les tranches de charges mensuelles et leur ordre d'affichage.

Ces catégories permettent de rendre les analyses plus lisibles et d'éviter les tris alphabétiques incorrects dans les graphiques.

---

## 5. Indicateurs clés du projet

Les mesures DAX ont été construites pour analyser l'attrition, la structure du portefeuille clients et les enjeux financiers.

### Résultats généraux

| Indicateur | Valeur |
|---|---:|
| Nombre total de clients | 7 043 |
| Clients actifs | 5 174 |
| Clients perdus | 1 869 |
| Taux de churn | 26,54 % |
| Taux de fidélisation | 73,46 % |
| Ancienneté moyenne | Environ 32,4 mois |
| Revenu mensuel total du portefeuille | Environ 456 117 € |
| Revenu mensuel associé aux clients perdus | Environ 139 131 € |

Le taux de churn est calculé à partir du rapport entre le nombre de clients perdus et le nombre total de clients.

**Taux de churn = Clients perdus / Total clients × 100**

**Taux de fidélisation = Clients actifs / Total clients × 100**

Ces deux indicateurs permettent de suivre la répartition des clients selon leur statut dans le jeu de données.

### Lecture financière

Le revenu mensuel associé aux clients perdus représente la somme des charges mensuelles des clients identifiés comme ayant quitté l'entreprise.

Il s'agit d'un **indicateur d'exposition financière**, et non d'une perte comptable confirmée ou d'un manque à gagner réellement observé sur plusieurs mois.

---

## 6. Présentation du dashboard Power BI

Le rapport comprend six pages complémentaires. Chacune répond à une question métier précise.

### Page 1 — Vue générale

![Vue générale du dashboard](screenshots/01_Vue_generale.png)

**Objectif :** fournir une synthèse de la situation du portefeuille clients.

Cette page regroupe les indicateurs essentiels pour comprendre rapidement l'activité :

- Nombre total de clients.
- Nombre de clients actifs et perdus.
- Taux de churn et taux de fidélisation.
- Répartition des clients selon leurs caractéristiques.
- Analyse de l'ancienneté et des contrats.

**Intérêt métier :** permettre à un responsable commercial ou à un analyste de disposer d'une vision globale avant d'approfondir les segments problématiques.

### Page 2 — Facteurs de churn

![Analyse des facteurs de churn](screenshots/02_Facteurs_churn.png)

**Objectif :** identifier les caractéristiques associées aux départs clients.

L'analyse porte notamment sur :

- Les types de contrat.
- Les services Internet.
- Les modes de paiement.
- Les habitudes de facturation.
- Les services complémentaires souscrits.

Les comparaisons permettent de distinguer les segments présentant une attrition importante de ceux dont les clients restent davantage.

**Intérêt métier :** identifier les facteurs à examiner en priorité dans une démarche de fidélisation.

### Page 3 — Segmentation clients

![Segmentation des clients](screenshots/03_Segmentation.png)

**Objectif :** comparer les profils clients et mettre en évidence les populations les plus exposées.

Cette page croise plusieurs dimensions, notamment les caractéristiques démographiques, l'ancienneté, les contrats et les services.

La segmentation permet de dépasser le seul taux de churn global, qui peut masquer des différences importantes entre groupes.

**Intérêt métier :** orienter les analyses et les campagnes vers des groupes de clients clairement définis.

### Page 4 — Rétention et recommandations

![Rétention et recommandations](screenshots/04_Retention.png)

**Objectif :** traduire les résultats analytiques en pistes d'action métier.

Cette page met en relation les constats sur l'attrition avec les segments pouvant justifier une attention particulière.

Les recommandations portent sur la fidélisation, l'expérience client et la priorisation des actions.

**Intérêt métier :** faciliter le passage de l'analyse descriptive à la prise de décision.

### Page 5 — Analyse financière

![Analyse financière](screenshots/05_Analyse_financiere.png)

**Objectif :** évaluer les enjeux financiers associés à l'attrition.

Cette page étudie notamment :

- Les charges mensuelles des clients.
- Les revenus associés aux clients actifs et perdus.
- Le revenu moyen par client.
- Les différences financières entre segments.

Elle permet d'éviter une lecture uniquement fondée sur le nombre de départs.

Un segment avec peu de clients perdus peut représenter un enjeu financier important si ses charges mensuelles sont élevées.

**Intérêt métier :** compléter l'analyse du churn par une lecture économique.

### Page 6 — Simulateur de fidélisation

![Simulateur de fidélisation](screenshots/06_Simulateur.png)

**Objectif :** estimer l'effet théorique d'une réduction du churn sur les départs et le revenu mensuel associé.

Le simulateur repose sur des hypothèses ajustables.

À titre d'exemple, une réduction relative de 20 % du churn donne les résultats suivants :

| Indicateur simulé | Résultat |
|---|---:|
| Hypothèse de réduction relative du churn | 20 % |
| Départs théoriquement évités | Environ 374 |
| Revenu mensuel théoriquement préservé | Environ 27 826 € |

Ces résultats sont issus d'un scénario de calcul. Ils ne constituent ni une prévision statistique ni une estimation garantie de l'efficacité d'une campagne.

**Intérêt métier :** aider à comparer différents objectifs de fidélisation et à mesurer leur ordre de grandeur.

---

## 7. Principaux résultats de l'analyse

### 7.1. Une attrition significative

Sur 7 043 clients, 1 869 ont quitté l'entreprise, soit un taux de churn de **26,54 %**.

Ce niveau représente un enjeu important pour la gestion du portefeuille clients.

Il justifie une analyse détaillée des caractéristiques associées aux départs.

### 7.2. Une forte différence selon le type de contrat

Les clients disposant d'un contrat mensuel présentent un taux de churn d'environ **42,71 %**.

Cette observation montre une association importante entre la durée d'engagement et le statut de départ.

Elle ne permet toutefois pas d'affirmer que le type de contrat provoque directement l'attrition.

### 7.3. Un segment particulièrement exposé

Le segment combinant un **contrat mensuel et un service Internet fibre optique** présente les résultats suivants :

- 2 128 clients.
- 1 162 clients perdus.
- Taux de churn d'environ **54,61 %**.

Ce segment constitue une priorité pertinente pour une analyse complémentaire.

Avant de proposer une action commerciale, il serait nécessaire d'étudier les raisons possibles de ces départs, notamment la satisfaction, les tarifs et la qualité du service.

### 7.4. Un enjeu financier mesurable

Les clients perdus représentent environ **139 131 € de charges mensuelles cumulées**.

Cet indicateur permet d'estimer l'importance financière du portefeuille concerné par le churn.

Il ne correspond pas directement à une perte de chiffre d'affaires réalisée, car les données ne retracent pas l'évolution comptable des revenus dans le temps.

---

## 8. Recommandations métier

À partir des résultats du dashboard, plusieurs axes peuvent être proposés.

### Priorité 1 — Étudier les contrats mensuels

Les clients sans engagement long présentent une attrition plus élevée.

Il serait pertinent d'analyser les raisons de ce comportement avant d'envisager des offres adaptées, des avantages de fidélité ou des propositions de changement de contrat.

### Priorité 2 — Examiner le segment fibre optique avec contrat mensuel

Ce segment combine un volume important de clients et un taux de départ élevé.

Une étude complémentaire pourrait porter sur la satisfaction, la qualité du réseau, le support technique et le positionnement tarifaire.

### Priorité 3 — Adapter les actions aux profils clients

Une campagne identique pour tous les clients risque de ne pas répondre aux différences entre segments.

Une approche segmentée permettrait de proposer des actions plus ciblées.

### Priorité 4 — Mesurer l'efficacité des campagnes

Toute action de fidélisation devrait être accompagnée d'indicateurs de suivi :

- Taux de churn après intervention.
- Nombre de départs évités estimé.
- Coût de la campagne.
- Revenu effectivement conservé.
- Comparaison avec un groupe de clients non ciblés.

L'objectif est de vérifier si les actions produisent des résultats mesurables, plutôt que de se limiter aux hypothèses du simulateur.

---

## 9. Démarche technique

Le projet suit une démarche de Business Intelligence structurée.

**1. Compréhension du besoin métier**

Définition de la problématique, des objectifs et des indicateurs nécessaires pour étudier l'attrition.

**2. Exploration des données**

Identification des champs disponibles, de leur signification et des possibilités d'analyse.

**3. Préparation dans Power Query**

Vérification de la qualité, adaptation des types et préparation des colonnes nécessaires aux visualisations.

**4. Construction du modèle**

Organisation des données et création des mesures DAX utilisées dans les différents indicateurs.

**5. Création du dashboard**

Développement des six pages, choix des graphiques, mise en place des filtres et organisation de la navigation.

**6. Analyse et interprétation**

Étude des résultats, comparaison des segments et formulation de recommandations.

**7. Contrôle qualité et documentation**

Vérification des données, contrôle du fonctionnement du rapport et rédaction d'un dossier présentant les méthodes et les résultats.

---

## 10. Compétences mobilisées

| Domaine | Compétences |
|---|---|
| Business Intelligence | Définition de KPI, construction d'un tableau de bord, suivi de la performance |
| Power BI | Visualisations, interactions, filtres, navigation et mise en page |
| Power Query | Nettoyage, transformation, typage et profilage des données |
| DAX | Mesures, calculs conditionnels, indicateurs financiers et simulation |
| Analyse de données | Segmentation, comparaison de groupes, interprétation des résultats |
| Analyse métier | Identification des enjeux, priorisation et recommandations |
| Qualité des données | Contrôle des doublons, valeurs manquantes et erreurs |
| Documentation | Présentation de la démarche, des résultats et des limites |

---

## 11. Limites du projet

Plusieurs limites doivent être prises en compte dans l'interprétation des résultats.

**Données fictives :** le jeu de données IBM représente un cas d'étude et non une entreprise réelle.

**Analyse descriptive :** les relations observées entre les caractéristiques des clients et leur départ ne démontrent pas un lien de causalité.

**Absence d'historique mensuel complet :** les données ne permettent pas de suivre précisément l'évolution du churn et des revenus mois après mois.

**Simulateur théorique :** les scénarios reposent sur des hypothèses proportionnelles et ne prennent pas en compte le coût réel des campagnes, les réactions des clients ou les effets à long terme.

**Absence de modèle prédictif :** le projet ne calcule pas de probabilité individuelle de départ à partir d'un algorithme de Machine Learning.

Ces limites définissent le périmètre du dashboard et permettent d'éviter de surinterpréter les résultats.

---

## 12. Améliorations possibles

Plusieurs évolutions pourraient être envisagées dans une version ultérieure :

- Intégration d'un historique mensuel des clients.
- Développement d'un modèle prédictif de churn.
- Création d'un score de risque individuel.
- Analyse de la valeur client à long terme (*Customer Lifetime Value*).
- Prise en compte du coût des campagnes de fidélisation.
- Automatisation du rafraîchissement des données.
- Comparaison des performances des actions commerciales.
- Publication du rapport dans un environnement Power BI Service, sous réserve des accès nécessaires.

---

## 13. Structure du dépôt

```text
NovaTel-Customer-Churn-Analytics/
│
├── NovaTel_Customer_Churn.pbix
├── README.md
│
├── data/
│   └── WA_Fn-UseC_-Telco-Customer-Churn
│
│
├── docs/
│   └── Dossier_Professionnel_NovaTel.pdf
│
└── screenshots/
    ├── 01_Vue_generale.png
    ├── 02_Facteurs_churn.png
    ├── 03_Segmentation.png
    ├── 04_Retention.png
    ├── 05_Analyse_financiere.png
    └── 06_Simulateur.png
```

### Consulter le projet

Le fichier `.pbix` peut être ouvert avec **Power BI Desktop**.

Les captures d'écran permettent de consulter les principales pages sans installer Power BI.

Le dossier professionnel contient une présentation détaillée du projet, le dictionnaire des données, les informations techniques et les contrôles qualité.

---

## 14. Conclusion

Ce projet m'a permis de réaliser une analyse de Business Intelligence complète, depuis la préparation des données jusqu'à la restitution des résultats métier.

Le dashboard met en évidence des différences importantes de churn selon les profils clients, notamment pour les contrats mensuels et certains services Internet.

L'analyse financière complète ces observations en montrant que les départs représentent également un enjeu de revenu.

Enfin, le simulateur permet d'explorer différents scénarios de fidélisation tout en distinguant les résultats théoriques des performances réellement observées.

**L'objectif de NovaTel est de montrer comment Power BI peut transformer un jeu de données clients en indicateurs compréhensibles, analyses exploitables et pistes d'aide à la décision.**

---

## 15. Auteur

**Can Pekgoz**

Étudiant en Master 2 Big Data, Data Analysis & Business Intelligence

Projet personnel réalisé dans le cadre du développement de mon portfolio Data / Business Intelligence.

**GitHub :** [NacPKZ](https://github.com/NacPKZ)

**Contact :** canpekgoz.pro@gmail.com

---

*Projet de portfolio — Données publiques IBM Telco Customer Churn — Entreprise NovaTel fictive.*