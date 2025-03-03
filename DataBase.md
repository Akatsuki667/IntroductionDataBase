# Introduction
Système organisé permettant de _stocker_, _gérer_ et _récupérer_ des informations.
Conçue pour contenir des données structurées et permet leur manipulation via des _requêtes_(`GET`, `POST`, `PUT`, `DELETE` etc.).

# Fonctionnement
__Système de Gestion de Base de Données__(SGBD): assure la création, la gestion et la mise à jour des données.

## Principales Opérations
_Stockage des données_: Information stockées sous une forme organisé
_Manipulation des données_: Ajouter, modifier ou supprimer des enregistrements
_Requête et récupération_: Information stockées sous une forme organisé
_Sécurisation_: Contrôle d'accès, permissions et sauvegardes

# Types de données

## DB relationelles (SQL)
Stocke les données sous forme de _tables_ avec des colones et des lignes.
Utilisation de __Strutured Query Language__ pour interaction avec les données
Ex.: _MySQL_, _PostrgreSQL_, _Oracle_, _Microsoft SQL Server_
Ex. de tables:
id  nom    email
--- ------ ----------------
1   Alice  alice@gmail.com
--- ------ ----------------
2   Bob    bob@gmail.com
--- ------ ----------------

## DB NoSQL
Stocke les données sous forme de _documents_, _paires clé-valeur_ ou _graphes_
Ex.: _MongoDB_, _Redis_, _Cassandra_, _Firebase_
Ex. stockage JSON(MongoDB)
```json
{
    "id": 1,
    "nom": "Alice",
    "email": "alice@email.com",
    "téléphone": "0123456789"
}
```

## DB hiérarchiques
Organise les données sous une structure d'arborescence(comme un arbre XML).
Chaque enregistrement à une relation _parent-enfant_.

# Pourquoi l'utilisation d'une DB
_Organisation/Struturation_: Facilite classement et recherche d'informations
_Performance/Rapidité_: Recherche optimisées grâçe aux index et aux requêtes optimisées.
_Sécurité_: Protection des données via mécanisme d'authentification et d'autoristaions
_Fiabilité/Intégrité_: Garantie cohérence des données(transactions __ACID__ en SQL)

__ACID__:
_Atomicité_: Si une transaction échoue, le résultat sera comme si elle n'avais jamais eu lieu.
_Cohérence_: Définition règle pour données et qu'elles soient respectées, sinon la transaction échoue.
_Isolation_: Possibilité exécution deux opérations en même temps et que le résultat soit le même que si exécutées l'une après l'autre.
_Durabilité_: Persistance données.

_Transaction_: Ensemble d'opérations sur une DB qui sont exécutées comme une seule unité de travail, une transaction garantie que toutes les opérations sont traitées de manière fiable et cohérente.

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
_Tables_: Stockent les enregistrement sous formes lignes, colonnes.
_Schéma_: Définit la structure de la base (relations, contraintes, types de données)
_Index_: Accélèrent les recherche de données
_Vues_: Requêtes pré-enregistrées permettant de simplifier l'accès aux données
_Transactions_: Assurent la cohérence des données aux propriétés __ACID__:
	_Atomicité_: Transaction tout ou rien
	_Cohérence_: Données restent valide
	_Isolation_: Transaction ne s'interfèrent pas
	_Durabilité_: Données sauvegardées même après crash
