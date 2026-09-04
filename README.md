# evalSymphony — Gestion de classes et d'élèves

Évaluation **Symfony 7.3** réalisée à l'IIM (décembre 2025). Une petite application de gestion scolaire : des classes, et des élèves rattachés à une classe.

## Modèle de données

- **Classe** : `nom_classe`, `niveau`, et la liste de ses élèves
- **Élève** : `prenom`, `nom`, et sa classe (relation ManyToOne, obligatoire)

Les entités sont gérées par Doctrine ORM, avec les migrations dans `migrations/`.

## Routes

| Route | Description |
|-------|-------------|
| `/classe` | Liste des classes |
| `/eleve` | Liste des élèves |
| `/eleve/ajouter` | Formulaire d'ajout d'un élève (Symfony Form, choix de la classe via `EntityType`) |

## Stack

- PHP 8.2+, Symfony 7.3
- Doctrine ORM et migrations
- Twig pour les templates, Symfony Forms pour la saisie
- AssetMapper et Stimulus pour le front
- PHPUnit pour les tests
- Docker Compose fourni pour PostgreSQL et Mailpit

## Installation

```bash
composer install

# Configurer la base dans .env.local (le .env par défaut vise MySQL en local)
# ex : DATABASE_URL="mysql://root:@127.0.0.1:3306/Symphony?serverVersion=8.0.32&charset=utf8mb4"

php bin/console doctrine:database:create
php bin/console doctrine:migrations:migrate

symfony serve
```

Ou avec Docker pour la base de données :

```bash
docker compose up -d
```

Puis ouvrir `http://localhost:8000/classe`.
