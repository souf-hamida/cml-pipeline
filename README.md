# Exercice 1 : Premier pipeline CML

Ce projet est la correction de l'exercice 1 sur la mise en place d'un premier pipeline CML avec GitHub Actions.

## Objectif

Créer un pipeline automatisé simple qui entraîne un modèle RandomForest sur le dataset Iris et publie les métriques dans les commentaires de Pull Request.

## Structure du projet

```
.
├── .github/
│   └── workflows/
│       └── cml.yml          # Workflow GitHub Actions
├── models/
│   └── iris_model.pkl       # Modèle entraîné (généré)
├── train.py                 # Script d'entraînement
├── requirements.txt         # Dépendances Python
├── metrics.json             # Métriques (généré)
└── README.md
```

## Fichiers principaux

### train.py

Script qui réalise les opérations suivantes :

- Charge le dataset Iris
- Divise les données en train/test (80/20)
- Entraîne un modèle RandomForest avec 100 estimateurs
- Calcule l'accuracy
- Sauvegarde le modèle dans `models/iris_model.pkl`
- Sauvegarde les métriques dans `metrics.json`

### .github/workflows/cml.yml

Workflow GitHub Actions qui :

- Se déclenche sur push et pull request vers la branche main
- Configure l'environnement Python
- Installe les dépendances
- Exécute le script d'entraînement
- Génère un rapport CML avec les métriques
- Publie le rapport en commentaire de la PR

## Instructions d'utilisation

### 1. Créer un repository GitHub

Créez un nouveau repository sur GitHub (public ou privé).

### 2. Pousser le code

```bash
cd exercice1-cml
git init
git add .
git commit -m "Initial commit: Exercice 1 CML"
git branch -M main
git remote add origin https://github.com/VOTRE_USERNAME/VOTRE_REPO.git
git push -u origin main
```

### 3. Tester avec une Pull Request

```bash
# Créer une branche de test
git checkout -b test-pipeline

# Faire une modification mineure
echo "# Test" >> README.md

# Commit et push
git add README.md
git commit -m "Test du pipeline CML"
git push origin test-pipeline
```

Ensuite, créez une Pull Request sur GitHub et vérifiez que :

- Le workflow s'exécute correctement
- Un commentaire avec les métriques apparaît dans la PR

## Résultat attendu

Le commentaire CML devrait afficher les métriques au format JSON :

```json
{
  "accuracy": 0.9666...,
  "n_estimators": 100,
  "test_size": 30
}
```

## Test local

Pour tester localement avant de pousser :

```bash
pip install -r requirements.txt
python train.py
cat metrics.json
```

## Points clés de l'exercice

- ✅ Repository GitHub configuré
- ✅ Script train.py fonctionnel
- ✅ Workflow GitHub Actions avec CML
- ✅ Métriques sauvegardées en JSON
- ✅ Rapport publié dans les PR

