# Analyse de l'Impact du Facteur Social ESG sur le Rendement des Actions de l'EURO STOXX 50

## Introduction

L'intégration des critères Environnementaux, Sociaux et de Gouvernance (ESG) dans les stratégies d'investissement est devenue un paradigme majeur de la finance moderne. Si l'intérêt pour ces facteurs est croissant, la démonstration de leur matérialité financière, en particulier leur pouvoir explicatif sur les rendements boursiers, reste un domaine de recherche actif et complexe. Ce projet se concentre spécifiquement sur le pilier **"Social" (S)** et vise à évaluer son impact sur la performance des actions de l'indice EURO STOXX 50.

L'objectif principal de ce travail est de dépasser la simple corrélation en construisant un cadre méthodologique rigoureux inspiré des modèles factoriels académiques, notamment celui de Fama et French. L'hypothèse centrale est que le facteur Social, s'il est pertinent, devrait non seulement générer une performance anormale (alpha), mais aussi démontrer une sensibilité (bêta) statistiquement significative après avoir contrôlé pour les facteurs de risque traditionnels (marché, taille, valeur). Le projet propose donc de construire un facteur "Social" synthétique et de l'intégrer dans un modèle à quatre facteurs pour tester sa pertinence économétrique sur le marché européen.

## Objectif du Projet

Ce projet, intitulé *"Analyse de l'Impact du Facteur Social ESG sur le Rendement des Actions de l'EURO STOXX 50"*, a pour objectif principal d'isoler et de quantifier la contribution du pilier social des critères ESG à la performance des actions européennes de premier plan. Plutôt que de traiter l'ESG comme un bloc monolithique, nous cherchons à déterminer si une stratégie d'investissement systématique basée uniquement sur le critère social peut générer des rendements anormaux.

L'ambition est de démontrer, via une approche économétrique robuste, si les entreprises les mieux notées sur le plan social surperforment celles qui le sont moins, et si ce "prime social" persiste après neutralisation des effets de marché connus. En définitive, le projet vise à fournir des preuves empiriques quantifiables pour répondre à la question : **le facteur "Social" est-il une source de risque systématique récompensée sur le marché européen ?**

## Structure du Projet

Pour atteindre l'objectif défini, une méthodologie structurée a été élaborée, organisée en quatre étapes clés qui forment une chaîne d'analyse rigoureuse :

#### 1. Collecte et Alignement des Données
La première étape consiste à rassembler et synchroniser les trois ensembles de données nécessaires :
- **Facteurs Fama-French :** Téléchargement des facteurs de marché (`Mkt-RF`), de taille (`SMB`) et de valeur (`HML`) pour le marché européen.
- **Données ESG :** Collecte des scores annuels du pilier "Social" pour chaque entreprise de l'EURO STOXX 50, puis conversion en une série temporelle quotidienne.
- **Rendements des Actions :** Téléchargement des prix de clôture quotidiens pour chaque constituant de l'indice et calcul de leurs rendements logarithmiques.

L'enjeu majeur de cette étape est l'alignement temporel parfait de toutes ces données sur un index de dates commun.

#### 2. Construction du Facteur Social (Facteur S)
La deuxième étape est consacrée à la création d'un facteur synthétique qui capture la performance relative des entreprises socialement responsables. Une stratégie "long-short" est mise en œuvre quotidiennement :
- **Classement :** Les entreprises sont classées en fonction de leur score social.
- **Formation des Portefeuilles :** Trois portefeuilles sont formés : "High S" (actions les mieux notées), "Medium S" et "Low S" (actions les moins bien notées).
- **Calcul du Facteur :** Le rendement du "Facteur S" est calculé comme la différence entre le rendement moyen du portefeuille "High S" et celui du portefeuille "Low S". La performance de ces portefeuilles est ensuite analysée en détail.

#### 3. Modélisation Économétrique
La troisième étape consiste à évaluer le pouvoir explicatif du facteur social. Pour chaque action de l'univers d'analyse, un modèle de régression à quatre facteurs est appliqué :
$$
R_i - R_f = \alpha_i + \beta_{i,Mkt}(R_m - R_f) + \beta_{i,SMB} \cdot SMB + \beta_{i,HML} \cdot HML + \beta_{i,ESG} \cdot \mathrm{ScoreESG}_i
$$
Deux méthodes statistiques sont utilisées pour garantir la robustesse des résultats : une régression par les Moindres Carrés Généralisés (GLS) et une régression par les Moindres Carrés Ordinaires (OLS) avec des erreurs standard robustes à l'hétéroscédasticité et à l'autocorrélation (HAC - Newey-West).

#### 4. Analyse et Interprétation des Résultats
La dernière étape est consacrée à l'analyse approfondie des sorties des modèles de régression. L'attention est portée sur deux paramètres clés pour chaque action :
- **Le Bêta ESG ($\beta_{i,ESG}$)** : Mesure la sensibilité du rendement de l'action au facteur social. Sa significativité statistique est étudiée pour déterminer si le facteur est réellement pris en compte par le marché.
- **L'Alpha ($\alpha_i$)** : Représente le rendement anormal, c'est-à-dire la performance non expliquée par les facteurs de risque. Sa significativité est analysée pour identifier une éventuelle surperformance ou sous-performance intrinsèque.

Des visualisations graphiques sont produites pour synthétiser les résultats sur l'ensemble de l'échantillon et tirer des conclusions sur l'impact global du pilier social.