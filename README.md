# Reporting RH Excel

Ce projet en **Data RH** a pour objectif de construire un reporting fiable et facilement maintenable à partir d’un fichier collaborateurs pour optimiser le service RH.

## Objectif

L'objectif est de produire un reporting à partir d'un export SIRH permettant de suivre :

- les **effectifs par entité**
- le **turnover**
- l’**absentéisme**
- la **masse salariale**

## Fichier principal

`Reporting_RH_Exercice_Excel.xlsx`

Le fichier contient un échantillon pédagogique de **5 000 collaborateurs**.  
La méthode reste la même pour un fichier de 50 000 lignes.

## Structure du classeur

| Onglet | Rôle |
|---|---|
| `00_Instructions` | Mode d’emploi et démarche |
| `01_Donnees_Brutes` | Source d’origine (à ne pas modifier) |
| `02_Donnees_Nettoyees` | Base de travail + colonnes calculées |
| `03_Parametres` | Référentiels et paramètres (cellules jaunes) |
| `04_Reporting` | Indicateurs et tableaux de synthèse |
| `05_Legende` | Explication des formules et de la méthode |

## Colonnes sources

`Matricule | Nom | Entité | Département | Type de contrat | Date d'entrée | Date de sortie | Salaire | Absences | Formation`

## Colonnes ajoutées pour le reporting

- **Statut** : Actif / Sorti
- **Ancienneté_années**
- **Flag_Départ**
- **Année_entrée** / **Année_sortie**
- **Mois_sortie**

## Définitions utilisées

- **Collaborateur actif** : pas de date de sortie, ou date de sortie postérieure à la date de référence (13/08/2026 dans le fichier).
- **Turnover** : nombre de départs sur la période ÷ effectif moyen.
- **Effectif moyen (version pédagogique)** : effectif actuel + (départs / 2).
- **Absentéisme (version simplifiée)** : jours d’absence ÷ (effectif × jours ouvrés théoriques).
- **Masse salariale** : somme des salaires des collaborateurs actifs.

## Outils Excel utilisés

- Séparation source / données de travail / paramètres / reporting
- Formules `COUNTIF`, `COUNTIFS`, `SUMIF`, `SUMIFS`, `SI`
- Paramètres centralisés pour faciliter la maintenance
- Filtres automatiques
- Tableaux croisés dynamiques (à créer pour approfondir l’analyse)

## Comment utiliser le fichier

1. Ouvrir `Reporting_RH_Exercice_Excel.xlsx`
2. Lire l’onglet `00_Instructions`
3. Consulter `04_Reporting`
4. Modifier une date ou un salaire dans `02_Donnees_Nettoyees` et observer l’impact
5. Modifier les cellules jaunes de `03_Parametres` (période de turnover, jours ouvrés)

## Point important

En situation réelle, avec 50 000 lignes et des mises à jour régulières, on compléterait cette approche avec **Power Query** (nettoyage automatique) puis **Power BI** pour le pilotage.

## Illustrations

Cette image ci-dessous présente un tableau croisé dynamique avec le nombre de collaborateurs par entité et type de contrat
<img width="907" height="314" alt="Capture d&#39;écran 2026-08-28 212919" src="https://github.com/user-attachments/assets/bc13c650-7e9f-431e-8089-429f00349dad" />

Cette image représente les données nettoyées
<img width="947" height="317" alt="Capture d&#39;écran 2026-08-28 213119" src="https://github.com/user-attachments/assets/bc434c04-8167-4e58-bc8b-b998a8831889" />

Cette image décrit les différents départs par entité
<img width="700" height="176" alt="Capture d&#39;écran 2026-08-28 213354" src="https://github.com/user-attachments/assets/daef1bf8-7704-474e-99ac-c1589635e6ce" />

## Auteur

Auteur : Prisca MBAH 
Profil en recherche d’**alternance Data RH**  
Expérience RH + montée en compétences data (Excel, Power BI, qualité de données)
