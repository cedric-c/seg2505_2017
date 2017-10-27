# Base de données (DB) locale sur Android

## Agenda
- Survole de SQLite sur Android
- La base des tables, schémas, clés primaires
- Structured Query Language (SQL)
- Exemple de SQLite simple

---

## Qu'est-ce SQLite?

- Les applications mobiles ont besoin de garder des informations locales
- La base de données se retrouve dans presque chaque application
    - les applications qui manipulent les données
    - les applications qui font que sauver des informations simples comme les points pour un match de soccer
- Pouvoir capter des informations dans une base de données est du plus important puisque l'environnement Android peut à n'importe quel instant supprimer les informations en mémoire pour se servir de ces ressources.

+++

## Qu'est-ce SQLite?

- SQLite est une base de données intégrée 
- La plupart des bases de données (Oracle, MySQL) sont des processus qui fonctionnent de manière indépendante
- SQLite est dit <<intégré>> car c'est qu'une librairie qui fait partie d'une application
    - il n'y a donc aucun processus dédié qui soutient l'exécution de la base de données
- Les opérations effectuées dans la base de données se font à l'intérieur de la librairie SQLite

---

## Comprendre les tables

- Une structure simple dans la DB
- Chaque DB peut contenir plusieurs tables et chaque table est conçue pour contenir un type d'information spécifique
- Exemple
    - Une DB peut contenir une table <<client>> qui contient le nom, l'adresse, le numéro téléphonique de chaque client pour une organisation
    - La même DB pourrait aussi contenir une table <<produits>> qui contient des entrées de produits (identifiant du produit, description) qu'offre une organisation.

+++

## Comprendre les tables

- Chaque table dans une DB a un nom unique


---

## Le schéma

- Le schéma définit les caractéristiques des données sauvegardées dans la table d'une DB
- Le schéma pour table de client pourrait définir que
    - un client n'aura pas de nom de plus de 20 caractères de longueur
    - l'entrée téléphonique d'un client aura que des entrées d'un certain format
- Les schémas sont aussi utilisés pour définir la structure entière d'une DB et les relations entre les tables qu'elle contient

---

## Colonnes et types de donnée

- Chaque colonne représente un champ dans une DB (nom, téléphone, courriel)
- Chaque colonne doit contenir un type spécifié de donnée

---

## Clés primaires

- Chaque DB contient une ou plusieurs colonnes utilisées pour identifier chaque rangée d'une manière unique
- C'est ce qu'on nomme la clé primaire (primary key)
- Exemple: numéro bancaire, NAS
- C'est ce qui permet à un système de DB d'identifier de manière unique chaque entrée dans la DB
sans clé primaire, il ne serait pas possible de supprimer des entrées spécifiques

---

## Structured Query Language (SQL)

- Les données sont manipulées avec un langage appelé Structured Query Language
- C'est le standard 
- C'est simple et conçu pour lire et écrire à une DB
    - Peu de mots clés
    - Différentes implémentations de SQL ont souvent une syntaxe identique
    
+++
    
## Commande utile : `Create Table`

```
CREATE TABLE table_name(
    column1 datatype PRIMARY KEY
    column2 datatype,
    column3 datatype,
    ....
    columnN datatype,
);
```

+++

## Commande utile : `Drop Table`

- DROP TABLE table_name
- DROP TABLE IF EXISTS table_name

+++

## Commande utile : `Insert into Table`

INSERT INTO table_name VALUES (value1, value2, value3, ...);

+++

## Commande utile : `Delete from Table`

DELETE FROM table_name WHERE some_column=some_value;

+++

## Commande utile : Retrait
SELECT column_name, column_name FROM table_name WHERE column_name=value;

---

# Exemple simple

## Interface d'utilisateur

## Table de produits

Merci!