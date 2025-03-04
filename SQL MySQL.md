# DB relationnelles
Organise les données en __tables__(lignes et colonnes) et utilise __SQL__(Structured Query Language) pour ingteragir avec elles.

__SQL__:

- Créer et modifier des base de données (__DDL__: __Data Definition Language__)
- Manipuler les données (__DML__: __Data Manipulation Language__)
- Effectuer des requêtes et filtrer des données.

# MySQL
__Système de Gestion de Base de Données Relationnelles__(SGBDR) open-source.

# Création DB MySQL
```sql
CREATE DATABASE MaBase;
USE MaBase;
```

# DDL: Création ety modification des tables
## Création d'une table
```sql
CREATE TABLE utilisateurs (
    id INT PRIMARY KEY AUTO_INCREMENT,
    nom VARCHAR(100) NOT NULL,
    email VARCHAR(255) UNIQUE NOT NULL,
    age INT CHECK (age >= 18)
);
```

## Modification d'une table
### Ajouter une colonne
```sql
ALTER TABLE utilisateurs ADD COLUMN adresse VARCHAR(255);
```
### Supprimer une colonne
```sql
ALTER TABLE utilisateurs DROP COLUMN adresse;
```

# DML: Manipualtion des données
## Insertion de données
```sql
INSERT INTO utilisateurs (nom, email, age) VALUES ('Alice', 'alice@example.com', 25);
```
## Mise à jour des données
```sql
UPDATE utilisateurs SET age = 26 WHERE nom = 'Alice';
```
## Suppression des données
```sql
DELETE FROM utilisateurs WHERE nom = 'Alice';
```

# Requête SQL: Récupération des données
## Sélectionner toutes les données
```sql
SELECT * FROM utilisateurs;
```
## Filtrer ls données avec `WHERE`
```sql
SELECT nom, email FROM utilisateurs WHERE age >= 21;
```
## Trier les données
```sql
SELECT * FROM utilisateurs ORDER BY age DESC;
```

# Sous-requêtes
```sql
SELECT nom FROM utilisateurs WHERE age = (SELECT MAX(age) FROM utilisateurs);
```

# Fonctions MysSQL utiles
## COUNT(): Nombre d'enregistrement
```sql
SELECT COUNT(*) FROM utilisateurs;
```
## AVG(): Moyenne d'une colonne
```sql
SELECT AVG(age) FROM utilisateurs;
```
## SUM(): somme des valeurs
```sql
SELECT SUM(age) FROM utilisateurs;
```
