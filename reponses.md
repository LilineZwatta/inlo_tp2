
### 1 Quelles étapes (steps) sont réalisées par cette action ?

1. **Checkout du code**

   Télécharge le code du dépôt sur l'environnement GitHub Actions.
2. **Configuration de Python (version 3.10)**

   Prépare un environnement Python spécifique (ici Python 3.10).
3. **Installation des dépendances Python**

   * Met à jour `pip`.
   * Installe `flake8` (outil de linting) et `pytest` (outil de test).
   * Installe les dépendances depuis `requirements.txt`, si ce fichier existe.
4. **Analyse statique du code (lint)** avec `flake8`

   * Vérifie les erreurs critiques (erreurs de syntaxe, variables non définies, etc.) et arrête la construction en cas de problème majeur.
   * Vérifie également la complexité du code, la longueur des lignes, etc. (sans arrêter la construction).
5. **Exécution des tests unitaires** avec `pytest`

   * Lance tous les tests unitaires présents dans le projet.



### Une étape (step) est définie au minimum par 2 éléments, lesquels sont-ils et à quoi servent-ils ?

Chaque étape (`step`) dans GitHub Actions est définie au minimum par :

1. **`name`**

   Il s'agit d'une description claire de ce que réalise l'étape. Cette information est affichée clairement dans l'interface GitHub Actions pour identifier rapidement ce qui se passe à chaque étape.
2. **`run` ou `uses`**

   * `run` permet d'exécuter des commandes directement dans l'environnement d'exécution (bash, shell, etc.).
   * `uses` permet d'utiliser une action externe (déjà créée par quelqu'un d'autre ou prédéfinie par GitHub).

**Exemples :**

* `run: pip install flake8 pytest` exécute directement des commandes bash.
* `uses: actions/checkout@v4` utilise une action externe pour récupérer le code depuis GitHub.

# La première étape contient le mot-clé ‘with’, a quoi sert-il ?

Le mot-clé `with` est utilisé dans GitHub Actions pour spécifier des paramètres ou des options spécifiques à l'action appelée avec le mot-clé `uses`.

```yaml
- uses: actions/setup-python@v3
  with:
    python-version: "3.10"

```

Ici, `with` sert à fournir une information supplémentaire à l'action externe (`actions/setup-python`). En particulier, cela indique quelle **version de Python** doit être installée pour l'étape concernée (ici, la version 3.10).

**En résumé :**

* Le mot-clé `with` permet de passer des paramètres spécifiques à une action externe (`uses`).
* Ces paramètres influencent la manière dont l'action externe va s'exécuter.
