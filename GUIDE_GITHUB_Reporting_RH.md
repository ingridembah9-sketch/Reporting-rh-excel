# Guide GitHub – Partager le reporting RH (Question 1 Excel)

Ce guide t’explique **comment mettre ton travail Excel sur GitHub**, étape par étape, même si tu n’as jamais utilisé GitHub.

Objectif : publier ton fichier d’exercice (effectifs, turnover, absentéisme, masse salariale) pour le montrer en entretien, le partager, ou continuer à le faire évoluer.

---

## 1. Ce que tu vas publier

- Le fichier Excel : `Reporting_RH_Exercice_Excel.xlsx`
- Un fichier `README.md` (la page d’accueil du projet)
- (Optionnel) des exports CSV des onglets pour mieux suivre les évolutions

**Important :** GitHub n’est pas Excel. Un fichier `.xlsx` est un fichier “binaire”. On peut le stocker et le télécharger, mais GitHub ne montrera pas les formules comme dans Excel. Le `README` sert donc à expliquer le projet.

---

## 2. Créer un compte GitHub (si tu n’en as pas)

1. Va sur [https://github.com](https://github.com)
2. Clique sur **Sign up**
3. Crée un compte avec ton email
4. Confirme l’email reçu

Conseil : utilise un identifiant professionnel (ex. `prenom-nom`).

---

## 3. Créer le dépôt (repository)

Un dépôt = le “dossier” du projet sur internet.

1. Une fois connecté, clique sur le **+** en haut à droite
2. Clique sur **New repository**
3. Remplis :
   - **Repository name** : `reporting-rh-excel` (ou un nom proche)
   - **Description** : `Reporting RH Excel – effectifs, turnover, absentéisme, masse salariale`
   - Choisis **Public** (visible par un recruteur) ou **Private** (seulement toi)
   - Coche **Add a README file**
4. Clique sur **Create repository**

---

## 4. Préparer tes fichiers sur ton ordinateur

Crée un dossier local, par exemple :

```
reporting-rh-excel/
├── README.md
├── GUIDE_GITHUB_Reporting_RH.md
└── Reporting_RH_Exercice_Excel.xlsx
```

Si tu as modifié les tableaux, mets **ta version à jour** dans ce dossier (pas forcément le fichier d’origine).

### Fichier à ne pas oublier

- Ton Excel final (celui sur lequel tu as travaillé)
- Un README clair (modèle plus bas)

### À éviter dans GitHub

- Fichiers temporaires Excel (`~$Reporting_RH_Exercice_Excel.xlsx`)
- Copies du type `fichier_v2_final_FINAL.xlsx` sans explication

Tu peux créer un fichier `.gitignore` avec :

```
~$*
*.tmp
.DS_Store
Thumbs.db
```

---

## 5. Méthode simple : envoyer les fichiers depuis le site GitHub

C’est la méthode la plus simple si tu ne veux pas encore utiliser Git en ligne de commande.

1. Ouvre ton dépôt sur GitHub
2. Clique sur **Add file** > **Upload files**
3. Glisse-dépose :
   - `Reporting_RH_Exercice_Excel.xlsx`
   - `README.md` (si tu le remplaces)
   - éventuellement ce guide
4. En bas, écris un message de commit, par exemple :
   - `Ajout du fichier Excel de reporting RH et du README`
5. Clique sur **Commit changes**

Tes fichiers sont maintenant en ligne.

---

## 6. Méthode recommandée : Git en local (plus pro)

À utiliser si tu veux montrer que tu sais versionner un projet.

### 6.1 Installer Git

- Windows : [https://git-scm.com](https://git-scm.com)
- Mac : Git est souvent déjà là, sinon Xcode Command Line Tools
- Vérifie dans un terminal :

```bash
git --version
```

### 6.2 Configurer ton nom et email (une seule fois)

```bash
git config --global user.name "Ton Prenom Nom"
git config --global user.email "ton.email@exemple.com"
```

### 6.3 Initialiser le projet

Dans ton dossier `reporting-rh-excel` :

```bash
git init
git add .
git commit -m "Premier commit : reporting RH Excel (effectifs, turnover, absentéisme, masse salariale)"
```

### 6.4 Relier le dossier à GitHub

Sur la page de ton dépôt, copie l’URL (HTTPS), puis :

```bash
git branch -M main
git remote add origin https://github.com/TON-COMPTE/reporting-rh-excel.git
git push -u origin main
```

GitHub te demandera de t’authentifier (souvent via un **Personal Access Token**, plus un mot de passe de compte).

---

## 7. Écrire un bon README (très important en entretien)

Le README est ce que le recruteur lit en premier.

Copie-colle le modèle ci-dessous dans `README.md`, puis adapte-le à **ton** travail.

```markdown
# Reporting RH Excel

Projet d’exercice Data RH : construire un reporting fiable et maintenable
à partir d’un fichier collaborateurs.

## Objectif
Produire des indicateurs RH à partir d’un export Excel :
- Effectifs par entité
- Turnover
- Absentéisme
- Masse salariale

## Structure du fichier
- `01_Donnees_Brutes` : source d’origine (à ne pas modifier)
- `02_Donnees_Nettoyees` : base de travail + colonnes calculées
- `03_Parametres` : référentiels et paramètres (dates, jours ouvrés)
- `04_Reporting` : indicateurs et tableaux de synthèse
- `05_Legende` : explication des formules

## Outils utilisés
- Tableaux Excel + filtres
- Formules : `COUNTIF`, `COUNTIFS`, `SUMIF`, `SUMIFS`, `SI`
- Paramètres centralisés pour faciliter la maintenance
- Tableaux croisés dynamiques (à créer pour analyser)

## Définitions utilisées
- **Actif** : pas de date de sortie, ou date de sortie postérieure à la date de référence
- **Turnover** : nombre de départs sur la période / effectif moyen
- **Absentéisme (version simplifiée)** : jours d’absence / (effectif × jours ouvrés théoriques)

## Comment utiliser le fichier
1. Ouvrir `Reporting_RH_Exercice_Excel.xlsx`
2. Lire l’onglet Instructions
3. Consulter le reporting
4. Modifier un paramètre dans l’onglet Paramètres pour voir l’impact

## Limites
Fichier pédagogique. Avec 50 000 lignes en situation réelle,
on utiliserait Power Query (et éventuellement Power Pivot / Power BI).

## Auteur
Prénom Nom – Recherche d’alternance Data RH
```

---

## 8. Bonnes pratiques pour un projet Excel sur GitHub

1. **Explique toujours le fichier** dans le README.
2. **Indique la date de référence** et les définitions (surtout le turnover).
3. **Versionne clairement** :
   - `Ajout du calcul d'absentéisme`
   - `Correction de la formule d'effectif actif`
4. Si tu fais plusieurs versions, note-les dans le README :
   - v1 : structure initiale
   - v2 : ajout TCD / graphiques
   - v3 : nettoyage des données
5. Ne mets pas de données personnelles réelles (noms, salaires réels, matricules internes). Ton fichier d’exercice est fictif : c’est parfait.

---

## 9. Partager le projet (lien pour le recruteur)

Une fois publié, l’adresse ressemble à :

`https://github.com/TON-COMPTE/reporting-rh-excel`

Tu peux :
- le mettre dans ton CV
- le mettre dans ton profil LinkedIn
- l’envoyer au recruteur : “Voici un exercice de reporting RH que j’ai structuré pour le rendre fiable et maintenable.”

Si le dépôt est **Private**, ajoute l’email du recruteur dans **Settings > Collaborators**.

---

## 10. Checklist avant d’envoyer le lien

- [ ] Le fichier Excel s’ouvre sans erreur
- [ ] Le README explique le projet en langage simple
- [ ] Les onglets sont nommés clairement
- [ ] Les définitions d’indicateurs sont écrites
- [ ] Aucune donnée personnelle réelle n’est publiée
- [ ] Le nom du dépôt est propre et professionnel
- [ ] Tu as testé le lien dans un navigateur privé

---

## 11. Message type à envoyer au recruteur

> Bonjour,  
> Dans le cadre de ma préparation à l’alternance Data RH, j’ai travaillé un cas de reporting Excel (effectifs, turnover, absentéisme, masse salariale).  
> J’ai structuré le fichier pour qu’il soit lisible, fiable et facile à mettre à jour.  
> Le projet est disponible ici : [lien GitHub]  
> Je reste disponible pour vous le présenter.

---

## 12. Prochaine étape (si tu veux aller plus loin)

Après GitHub + Excel, tu pourras :
1. Recréer le même reporting dans Power BI
2. Ajouter un dossier `/docs` avec captures d’écran des tableaux
3. Ajouter un petit export CSV des indicateurs
4. Créer une issue GitHub du type : “Ajouter le turnover par type de contrat”

Cela montre une vraie démarche Data RH, pas seulement un fichier isolé.
