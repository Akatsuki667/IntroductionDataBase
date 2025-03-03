# Introduction
Système organisé permettant de _stocker_, _gérer_ et _récupérer_ des informations.
Conçue pour contenir des données structurées et permet leur manipulation via des _requêtes_(`GET`, `POST`, `PUT`, `DELETE` etc.).


# Fonctionnement
__Système de Gestion de Base de Données__(SGBD): assure la création, la gestion et la mise à jour des données.


## Principales Opérations
- __Stockage des données__: Information stockées sous une forme organisé.
- __Manipulation des données__: Ajouter, modifier ou supprimer des enregistrements.
- __Requête et récupération__: Information stockées sous une forme organisé.
- __Sécurisation__: Contrôle d'accès, permissions et sauvegardes.


# DB relationelles (SQL)
Stocke les données sous forme de _tables_ avec des colones et des lignes.
Utilisation de __Strutured Query Language__ pour interaction avec les données.

Ex.: _MySQL_, _PostrgreSQL_, _Oracle_, _Microsoft SQL Server_.


# DB NoSQL
Stocke les données sous forme de _documents_, _paires clé-valeur_ ou _graphes_.

Ex.: _MongoDB_, _Redis_, _Cassandra_, _Firebase_.

Ex. stockage JSON(MongoDB).
```json
{
    "id": 1,
    "nom": "Alice",
    "email": "alice@email.com",
    "téléphone": "0123456789"
}
```


# DB hiérarchiques
Organise les données sous une structure d'arborescence(comme un arbre XML).
Chaque enregistrement à une relation _parent-enfant_.


# Pourquoi l'utilisation d'une DB
- __Organisation/Struturation__: Facilite classement et recherche d'informations.
- __Performance/Rapidité__: Recherche optimisées grâçe aux index et aux requêtes optimisées.
- __Sécurité__: Protection des données via mécanisme d'authentification et d'autoristaions.
- __Fiabilité/Intégrité__: Garantie cohérence des données(transactions __ACID__ en SQL).

__ACID__:
- __Atomicité__: Si une transaction échoue, le résultat sera comme si elle n'avais jamais eu lieu.
- __Cohérence__: Définition règle pour données et qu'elles soient respectées, sinon la transaction échoue.
- __Isolation__: Possibilité exécution deux opérations en même temps et que le résultat soit le même que si exécutées l'une après l'autre.
- __Durabilité__: Persistance données.

__Transaction__: Ensemble d'opérations sur une DB qui sont exécutées comme une seule unité de travail, une transaction garantie que toutes les opérations sont traitées de manière fiable et cohérente.

Ex. _transaction_ __SQL__:
__DB relationnelles__ utilise des transactions pour garantir l'intégrité des données.
```sql
START TRANSACTION;  -- Début de la transaction

UPDATE comptes SET solde = solde - 500 WHERE id = 1;  -- Débiter le compte A
UPDATE comptes SET solde = solde + 500 WHERE id = 2;  -- Créditer le compte B

COMMIT;  -- Valider la transaction
```
Si une erreur survient entre ces étapes, on peut __annuler la transaction__ avec un __ROLLBACK__ pour éviter incohérence.
```sql
START TRANSACTION;  -- Début de la transaction

UPDATE comptes SET solde = solde - 500 WHERE id = 1;  -- Débiter le compte A
UPDATE comptes SET solde = solde + 500 WHERE id = 2;  -- Créditer le compte B

-- Vérification : si le solde du compte A devient négatif, on annule la transaction
IF (SELECT solde FROM comptes WHERE id = 1) < 0 THEN
    ROLLBACK;  -- Annulation de toutes les opérations
ELSE
    COMMIT;  -- Validation définitive de la transaction
END IF;
```


# Architecture DB
- __Tables__: Stockent les enregistrement sous formes lignes, colonnes.
- __Schéma__: Définit la structure de la base (relations, contraintes, types de données).
- __Index__: Accélèrent les recherche de données.
- __Vues__: Requêtes pré-enregistrées permettant de simplifier l'accès aux données.
- __Transactions__: Assurent la cohérence des données aux propriétés __ACID__:
	- __Atomicité__: Transaction tout ou rien.
	- __Cohérence__: Données restent valide.
	- __Isolation__: Transaction ne s'interfèrent pas.
	- __Durabilité__: Données sauvegardées même après crash.
