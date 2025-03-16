# Festival - Application de Gestion d'Hébergement

## Description

Cette application web PHP permet de gérer l'hébergement des équipes des ligues sportives lors d'un festival. Elle offre une interface complète pour administrer les établissements d'hébergement, les équipes participantes et l'attribution des chambres.

## Fonctionnalités

### Gestion des établissements
- Consulter la liste des établissements disponibles
- Créer un nouvel établissement avec sa capacité d'hébergement
- Modifier les informations d'un établissement existant
- Supprimer un établissement (si aucune attribution n'existe)
- Visualiser les détails d'un établissement

### Gestion des équipes
- Consulter la liste des équipes participantes
- Créer une nouvelle équipe sportive
- Modifier les informations d'une équipe
- Supprimer une équipe (si aucune chambre n'est attribuée)
- Visualiser les détails d'une équipe

### Attribution des chambres
- Consulter les attributions de chambres existantes
- Effectuer ou modifier des attributions de chambres
- Contrôle automatique des disponibilités
- Calcul automatique du nombre de chambres nécessaires selon le nombre de participants (1 chambre pour environ 3 personnes)

## Prérequis

- Serveur web avec PHP 5.6 ou supérieur (compatible PHP 7+)
- Serveur MySQL/MariaDB
- Droits suffisants pour créer et gérer une base de données

## Installation

1. **Cloner ou télécharger les fichiers du projet** dans le répertoire de votre serveur web

2. **Configuration de la base de données**
   - Créer une base de données nommée `festival`
   - Exécuter les scripts SQL dans l'ordre:
     1. `sql/créations table.sql` (création des tables)
     2. `sql/clé étrangére.sql` (ajout des contraintes)
     3. `sql/remplisage table.sql` (données initiales)

3. **Configuration de la connexion à la base de données**
   - Ouvrir le fichier `_gestionBase.inc.php`
   - Modifier les paramètres de connexion si nécessaire:
   ```php
   $hote="localhost";  // Adresse de votre serveur MySQL
   $login="root";      // Nom d'utilisateur MySQL
   $mdp="";            // Mot de passe MySQL
   ```

4. **Accéder à l'application** via votre navigateur web

## Structure du projet

- **Fichiers d'inclusion**
  - `_controlesEtGestionErreurs.inc.php`: Fonctions de validation et gestion des erreurs
  - `_debut.inc.php`: En-tête HTML et navigation commune
  - `_gestionBase.inc.php`: Connexion à la base de données et fonctions de requêtes

- **Pages principales**
  - `index.php`: Page d'accueil
  - Pages de gestion des établissements:
    - `listeEtablissements.php`
    - `creationEtablissement.php`
    - `modificationEtablissement.php`
    - `suppressionEtablissement.php`
    - `detailEtablissement.php`
  - Pages de gestion des équipes:
    - `gestionEquipe.php`
    - `creationEquipe.php`
    - `modificationEquipe.php`
    - `suppressionEquipe.php`
    - `detailEquipe.php`
  - Pages de gestion des attributions:
    - `consultationAttributions.php`
    - `modificationAttributions.php`

- **Ressources**
  - Dossier `css`: Feuilles de style
  - Dossier `js`: Scripts JavaScript (Bootstrap)
  - Dossier `images`: Ressources graphiques
  - Dossier `sql`: Scripts SQL d'initialisation

## Règles métier importantes

- Une équipe nécessite environ 1 chambre pour 3 personnes
- Un établissement avec des attributions ne peut pas être supprimé
- Une équipe avec des attributions ne peut pas être supprimée
- Le nombre de chambres offertes par un établissement ne peut pas être réduit en dessous du nombre de chambres déjà attribuées

## Contribuer

Pour contribuer à ce projet:
1. Forker le projet
2. Créer une branche pour votre fonctionnalité
3. Committer vos changements
4. Pousser vers la branche
5. Ouvrir une Pull Request
