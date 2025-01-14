# TP SQL : **The Legend of Zelda**
Apprendre le SQL à travers les jeux de la série The Legend of Zelda

## Thème du TP

Dans ce TP, nous allons explorer l'univers de la célèbre série de jeux vidéo **The Legend of Zelda** à travers l'analyse de plusieurs titres, leurs ventes mondiales, leurs notes dans la presse, ainsi que d'autres informations essentielles. Vous apprendrez à créer une base de données, y insérer des données, et effectuer des requêtes SQL afin de trier et analyser ces données.

L’objectif est de maîtriser la gestion d'une base de données via **phpMyAdmin**, en comprenant comment structurer les données dans des tables et effectuer des requêtes pour obtenir les informations voulues.

## Étape 1 : Création de la base de données

Nous allons commencer par créer une base de données `zelda_jeux` qui contiendra des informations sur les jeux Zelda de salon et portables. Vous pouvez utiliser **phpMyAdmin** pour exécuter les requêtes SQL ci-dessous.

### Script SQL pour créer la base de données et la table

```sql
-- Créer la base de données
CREATE DATABASE zelda_jeux;

-- Utiliser la base de données nouvellement créée
USE zelda_jeux;

-- Créer la table avec les champs appropriés
CREATE TABLE jeux (
    id INT AUTO_INCREMENT PRIMARY KEY,
    titre VARCHAR(255) NOT NULL,  -- Titre du jeu
    date_sortie DATE,             -- Date de sortie en France
    console VARCHAR(255),         -- Console sur laquelle le jeu est sorti
    producteur VARCHAR(255),      -- Le producteur du jeu
    ventes_mondiales FLOAT,       -- Nombre de ventes mondiales (en millions)
    note_presse FLOAT             -- Note du jeu dans la presse
);
```

## Étape 2 : Insertion des données

Insérer les jeux Zelda de consoles de salon

```sql
INSERT INTO jeux (titre, date_sortie, console, producteur, ventes_mondiales, note_presse) VALUES
    ('The Legend of Zelda', '1987-11-15', 'NES', 'Shigeru Miyamoto', 6.51, 9.5),
    ('Zelda II: The Adventure of Link', '1988-12-01', 'NES', 'Shigeru Miyamoto', 4.38, 8.0),
    ('The Legend of Zelda: A Link to the Past', '1992-04-13', 'SNES', 'Shigeru Miyamoto', 4.61, 9.6),
    ('The Legend of Zelda: Ocarina of Time', '1998-11-23', 'Nintendo 64', 'Shigeru Miyamoto', 7.60, 10.0),
    ('The Legend of Zelda: Majora\'s Mask', '2000-10-25', 'Nintendo 64', 'Shigeru Miyamoto', 3.36, 9.0),
    ('The Legend of Zelda: The Wind Waker', '2003-03-24', 'GameCube', 'Shigeru Miyamoto', 4.43, 9.6),
    ('The Legend of Zelda: Twilight Princess', '2006-11-19', 'Wii', 'Shigeru Miyamoto', 8.93, 9.7),
    ('The Legend of Zelda: Skyward Sword', '2011-11-20', 'Wii', 'Eiji Aonuma', 3.67, 9.0),
    ('The Legend of Zelda: Breath of the Wild', '2017-03-03', 'Switch', 'Eiji Aonuma', 33.75, 10.0),
    ('The Legend of Zelda: Tears of the Kingdom', '2023-05-12', 'Switch', 'Eiji Aonuma', 20.80, 9.8);
```

Insérer les jeux Zelda de consoles portables

```sql
INSERT INTO jeux (titre, date_sortie, console, producteur, ventes_mondiales, note_presse) VALUES
    ('The Legend of Zelda: Link\'s Awakening', '1993-06-06', 'Game Boy', 'Shigeru Miyamoto', 3.83, 9.2),
    ('The Legend of Zelda: Link\'s Awakening DX', '1998-12-01', 'Game Boy Color', 'Shigeru Miyamoto', 2.22, 9.1),
    ('The Legend of Zelda: Oracle of Ages', '2001-05-14', 'Game Boy Color', 'Shigeru Miyamoto', 3.96, 9.0),
    ('The Legend of Zelda: Oracle of Seasons', '2001-05-14', 'Game Boy Color', 'Shigeru Miyamoto', 3.96, 9.0),
    ('The Legend of Zelda: A Link to the Past & Four Swords', '2002-12-02', 'Game Boy Advance', 'Shigeru Miyamoto', 1.89, 8.8),
    ('The Legend of Zelda: The Minish Cap', '2005-01-10', 'Game Boy Advance', 'Shigeru Miyamoto', 1.76, 9.1),
    ('The Legend of Zelda: Phantom Hourglass', '2007-10-01', 'Nintendo DS', 'Eiji Aonuma', 4.76, 9.0),
    ('The Legend of Zelda: Spirit Tracks', '2009-12-07', 'Nintendo DS', 'Eiji Aonuma', 3.14, 8.8),
    ('The Legend of Zelda: Ocarina of Time 3D', '2011-06-19', 'Nintendo 3DS', 'Shigeru Miyamoto', 6.22, 9.4),
    ('The Legend of Zelda: A Link Between Worlds', '2013-11-22', 'Nintendo 3DS', 'Eiji Aonuma', 4.21, 9.4),
    ('The Legend of Zelda: Majora\'s Mask 3D', '2015-02-13', 'Nintendo 3DS', 'Eiji Aonuma', 3.36, 9.0),
    ('The Legend of Zelda: Tri Force Heroes', '2015-10-23', 'Nintendo 3DS', 'Eiji Aonuma', 1.14, 7.8);
```

## Étape 3 : Premières requêtes

### Sélectionner tous les jeux de la table

```sql
SELECT * FROM jeux;
```

### Trier les jeux par ventes mondiales (du plus vendu au moins vendu)

```sql
SELECT * FROM jeux
ORDER BY ventes_mondiales DESC;
```

### Afficher uniquement les jeux sortis sur Nintendo Switch

```sql
SELECT * FROM jeux
WHERE console = 'Switch';
```

### Afficher les jeux dont la note de presse est inférieure à 9

```sql
SELECT * FROM jeux
WHERE note_presse < 9;
```

## Étape 4 : À vous de jouer !

Trouver les requêtes suivantes :  
- Afficher uniquement le titre et la date de sortie des jeux.
- Trouver les jeux sortis après l’année 2000.
- Combien y a-t-il de jeux dans la table ?
- Quelle est la moyenne des ventes mondiales de tous les jeux ?
- Quels sont les jeux ayant une note de presse égale à 10 ?
- Quel est le jeu ayant le plus grand nombre de ventes mondiales ?
- Quels jeux ont été produits par Eiji Aonuma ?
- Quels sont les différents noms de consoles présentes dans la table ?
- Quels sont les titres des jeux et leurs consoles pour ceux ayant dépassé 10 millions de ventes ?
- Quels jeux ont un titre contenant le mot "Ocarina" ?
- Combien de jeux ont été produits par chaque producteur ?
- Quel est le jeu le plus récent de la table ?

## Étape 5 : Questions supplémentaires


Insérer trois nouveaux jeux.

```sql
INSERT INTO jeux (titre, date_sortie, console, producteur, ventes_mondiales, note_presse) 
VALUES 
    ('The Legend of Zelda: Hyrule Warriors', '2014-09-26', 'Wii U', 'Hisashi Koinuma', 3.5, 79),
    ('The Legend of Zelda: Echoes of Wisdom', '2025-01-01', 'Nintendo Switch', 'Eiji Aonuma', NULL, 95),
    ('Super Mario Bros.', '1985-09-13', 'NES', 'Shigeru Miyamoto', 40.24, 92);
```

Réaliser les étapes suivantes :
- Modifier le jeu `The Legend of Zelda: Echoes of Wisdom` et mettre sa date de sortie au 26 septembre 2024.

```sql
UPDATE table
SET nom_colonne_1 = 'nouvelle valeur'
WHERE condition
```

- Supprimer le jeu Super Mario Bros de la table

```sql
DELETE FROM `table`
WHERE condition
```

Trouver les requêtes suivantes :  
- Quels sont les jeux produits par Shigeru Miyamoto ayant une note de presse supérieure à 9, triés par ordre décroissant de leur note ?
- Afficher le titre, la console et les ventes mondiales des jeux dont les ventes mondiales sont supérieures à la moyenne des ventes mondiales de tous les jeux.
- Quels sont les jeux ayant une note de presse supérieure à 9 et qui sont sortis avant l'année 2005 ?
- Combien de jeux sont sortis sur chaque console ?
- Afficher les jeux qui ont été notés entre 8.5 et 9.5, triés par leur note de presse en ordre décroissant.
- Afficher le titre, la console et la date de sortie des jeux produits par Eiji Aonuma, triés par ordre croissant de leur date de sortie.
- Trouver le producteur ayant produit le plus grand nombre de jeux.
- Quels sont les jeux sortis après 2010 ayant le mot "Legend" dans leur titre ?
- Afficher la somme totale des ventes mondiales pour chaque producteur.
- Quels sont les 3 jeux les plus anciens ayant une note supérieure ou égale à 9 ?
