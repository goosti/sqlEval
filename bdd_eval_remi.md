
# SQL TD 1 : 

## Contexte :

**Base de données immobilière**
Notre plateforme gère un site d'annonces en ligne dédié aux logements immobiliers, que ce soit pour la vente ou la location.
Chaque logement est consigné dans la table "logement".
Les agences immobilières sont répertoriées dans la table "agence".
Pour établir le lien entre les logements et les agences responsables, nous avons créé une table d'association nommée "logement_agence".
Chaque utilisateur inscrit, qu'il s'agisse de vendeurs ou d'autres individus, est enregistré dans la table "personne".
Les vendeurs ont une association spécifique avec les logements, enregistrée dans la table "logement_personne".
D'autres inscrits sont des acheteurs à la recherche d'un logement, et leurs critères de recherche sont consignés dans la table "demande" (demande d'achat).
Il est important de noter que la modélisation de cette base de données est simplifiée et conçue uniquement à des fins d'évaluation dans le cadre de ce sujet.

agence
+----------+---------------------+-----------------------------+
| idAgence | nom                 | adresse                     |
+----------+---------------------+-----------------------------+
|   257400 | logic-immo          | www.logic-immo.com          |
|   383505 | century21           | rue century                 |
|   504585 | laforet             | rue laforet                 |
|   544688 | fnaim               | rue fnaim                   |
|   608870 | orpi                | rue orpi                    |
|   654178 | foncia              | rue foncia                  |
|   654658 | guy-hoquet          | rue guy-hoquet              |
|   654893 | seloger             | www.seloger.com             |
|   692702 | bouygues immobilier | www.bouygues-immobilier.net |
+----------+---------------------+-----------------------------+

logement
+------------+-------------+----------+--------+------------+-----------+
| idLogement | type        | ville    | prix   | superficie | categorie |
+------------+-------------+----------+--------+------------+-----------+
|       5067 | appartement | paris    | 185000 |         61 | vente     |
|       5089 | appartement | paris    | 115000 |         15 | vente     |
|       5091 | maison      | paris    | 510000 |        130 | vente     |
|       5122 | appartement | bordeaux |    550 |         17 | location  |
|       5189 | appartement | lyon     |    420 |         14 | location  |
|       5245 | appartement | paris    | 160000 |         40 | vente     |
|       5246 | appartement | paris    |    670 |         35 | location  |
|       5249 | appartement | lyon     | 110000 |         16 | vente     |
|       5269 | appartement | bordeaux | 161500 |         33 | vente     |
|       5278 | appartement | paris    | 202000 |         90 | vente     |
|       5324 | appartement | lyon     |    690 |         31 | location  |
|       5336 | appartement | bordeaux | 129600 |         27 | vente     |
|       5378 | appartement | bordeaux | 121900 |         26 | vente     |
|       5412 | appartement | paris    |    680 |         40 | location  |
|       5636 | appartement | paris    | 150000 |         37 | vente     |
|       5661 | appartement | bordeaux | 148600 |         36 | vente     |
|       5723 | appartement | bordeaux | 170600 |         45 | vente     |
|       5770 | appartement | paris    | 139000 |         38 | vente     |
|       5778 | appartement | bordeaux | 128600 |         43 | vente     |
|       5779 | appartement | paris    | 310000 |        105 | vente     |
|       5786 | appartement | paris    |    570 |         20 | location  |
|       5860 | appartement | bordeaux | 105000 |         18 | vente     |
|       5869 | appartement | lyon     | 183600 |         60 | vente     |
|       5873 | appartement | lyon     | 176700 |         65 | vente     |
|       5898 | appartement | paris    |    690 |         40 | location  |
|       5961 | appartement | bordeaux |    650 |         45 | location  |
|       5963 | appartement | paris    | 220000 |         60 | vente     |
+------------+-------------+----------+--------+------------+-----------+

demande
+-----------+------------+-------------+----------+--------+------------+-----------+
| idDemande | idPersonne | type        | ville    | budget | superficie | categorie |
+-----------+------------+-------------+----------+--------+------------+-----------+
|         1 |          1 | appartement | paris    | 530000 |        120 | vente     |
|         2 |          3 | appartement | bordeaux | 120000 |         18 | vente     |
|         3 |          4 | appartement | bordeaux | 145000 |         21 | vente     |
|         4 |          5 | appartement | bordeaux | 152000 |         26 | vente     |
|         5 |          6 | appartement | lyon     | 200000 |         55 | vente     |
|         6 |          9 | appartement | paris    | 171000 |         40 | vente     |
|         7 |         13 | appartement | paris    | 163000 |         25 | vente     |
|         8 |         16 | appartement | paris    | 132000 |         15 | vente     |
|         9 |         19 | appartement | paris    | 350000 |         80 | vente     |
|        10 |         22 | appartement | lyon     |    600 |         20 | location  |
|        11 |         25 | appartement | lyon     | 188000 |         65 | vente     |
|        12 |         27 | appartement | paris    |    400 |         15 | location  |
|        13 |         28 | appartement | paris    | 330500 |        100 | vente     |
|        14 |         31 | appartement | paris    |  90000 |         15 | vente     |
|        15 |         32 | appartement | lyon     | 123800 |         21 | vente     |
|        16 |         35 | appartement | lyon     |   1200 |         70 | vente     |
|        17 |         37 | appartement | lyon     |   1500 |        100 | vente     |
|        18 |         43 | appartement | paris    |    600 |         20 | location  |
|        19 |         44 | appartement | paris    |    750 |         30 | location  |
|        20 |         45 | appartement | bordeaux |    680 |         30 | location  |
|        21 |         46 | appartement | bordeaux | 213000 |         40 | vente     |
|        22 |         47 | appartement | bordeaux |    700 |         45 | location  |
|        23 |         48 | appartement | paris    | 195000 |         40 | vente     |
|        24 |         49 | appartement | paris    | 250000 |         60 | vente     |
|        25 |         50 | appartement | lyon     | 110000 |         12 | vente     |
|        26 |         51 | appartement | lyon     |    500 |         17 | location  |
|        27 |         52 | appartement | paris    |    800 |         40 | location  |
|        28 |         53 | appartement | paris    |    850 |         50 | location  |
|        29 |         54 | appartement | paris    | 177000 |         40 | vente     |
|        30 |         55 | appartement | paris    |    630 |         20 | location  |
+-----------+------------+-------------+----------+--------+------------+-----------+

logement_personne
+--------------------+------------+------------+
| idLogementPersonne | idPersonne | idLogement |
+--------------------+------------+------------+
|                  1 |         40 |       5067 |
|                  2 |         41 |       5089 |
|                  3 |         42 |       5091 |
|                  4 |          2 |       5122 |
|                  5 |         39 |       5189 |
|                  6 |          7 |       5245 |
|                  7 |          8 |       5246 |
|                  8 |         10 |       5249 |
|                  9 |         18 |       5269 |
|                 10 |         21 |       5278 |
|                 11 |         17 |       5324 |
|                 12 |         36 |       5336 |
|                 13 |         20 |       5378 |
|                 14 |         29 |       5412 |
|                 15 |         24 |       5636 |
|                 16 |         34 |       5661 |
|                 17 |         14 |       5723 |
|                 18 |         57 |       5770 |
|                 19 |         26 |       5778 |
|                 20 |         56 |       5779 |
|                 21 |         12 |       5786 |
|                 22 |         11 |       5860 |
|                 23 |         23 |       5869 |
|                 24 |         38 |       5873 |
|                 25 |         33 |       5898 |
|                 26 |         15 |       5961 |
|                 27 |         30 |       5963 |
+--------------------+------------+------------+

logement_agence
+------------------+----------+------------+-------+
| idLogementAgence | idAgence | idLogement | frais |
+------------------+----------+------------+-------+
|                1 |   257400 |       5067 | 15000 |
|                2 |   383505 |       5067 |  1000 |
|                3 |   257400 |       5089 |  8633 |
|                4 |   692702 |       5089 |  7623 |
|                5 |   654178 |       5091 | 28621 |
|                6 |   544688 |       5091 | 34564 |
|                7 |   654893 |       5122 |   700 |
|                8 |   608870 |       5189 |   350 |
|                9 |   257400 |       5245 | 10856 |
|               10 |   544688 |       5245 | 14230 |
|               11 |   608870 |       5246 |   800 |
|               12 |   257400 |       5249 | 16358 |
|               13 |   608870 |       5249 |  7625 |
|               14 |   257400 |       5269 |  9500 |
|               15 |   544688 |       5269 | 11890 |
|               16 |   544688 |       5278 | 25689 |
|               17 |   608870 |       5278 | 19653 |
|               18 |   544688 |       5324 |   600 |
|               19 |   544688 |       5336 |  9542 |
|               20 |   608870 |       5336 | 16985 |
|               21 |   504585 |       5378 |  8652 |
|               22 |   608870 |       5378 | 15230 |
|               23 |   257400 |       5412 |   680 |
|               24 |   544688 |       5636 |  5963 |
|               25 |   608870 |       5636 | 13654 |
|               26 |   654893 |       5661 |  9462 |
|               27 |   654178 |       5661 | 11656 |
|               28 |   608870 |       5723 | 16233 |
|               29 |   504585 |       5723 | 19654 |
|               30 |   692702 |       5770 | 13655 |
|               31 |   654178 |       5770 |  8903 |
|               32 |   383505 |       5778 |  6350 |
|               33 |   654658 |       5778 | 12655 |
|               34 |   654178 |       5779 | 26754 |
|               35 |   654658 |       5779 | 45032 |
|               36 |   654178 |       5786 |   898 |
|               37 |   383505 |       5786 |   520 |
|               38 |   257400 |       5860 | 12566 |
|               39 |   654658 |       5860 |  8905 |
|               40 |   544688 |       5869 | 23685 |
|               41 |   654893 |       5869 | 19321 |
|               42 |   257400 |       5873 | 13504 |
|               43 |   257400 |       5898 |   900 |
|               44 |   383505 |       5898 |   250 |
|               45 |   692702 |       5898 |  1300 |
|               46 |   257400 |       5961 |  1240 |
|               47 |   504585 |       5961 |   300 |
|               48 |   692702 |       5961 |   890 |
|               49 |   257400 |       5963 | 27542 |
|               50 |   692702 |       5963 | 42502 |
|               51 |   383505 |       5963 | 18455 |
+------------------+----------+------------+-------+

personne
+------------+------------+
| idPersonne | prenom     |
+------------+------------+
|          1 | william    |
|          2 | gaetan     |
|          3 | mehdi      |
|          4 | charles    |
|          5 | brigitte   |
|          6 | sarah      |
|          7 | lucas      |
|          8 | quentin    |
|          9 | patrick    |
|         10 | emmanuel   |
|         11 | elodie     |
|         12 | agathe     |
|         13 | valentine  |
|         14 | charlotte  |
|         15 | alice      |
|         16 | samuel     |
|         17 | mathieu    |
|         18 | noemie     |
|         19 | simon      |
|         20 | florian    |
|         21 | clement    |
|         22 | yvon       |
|         23 | lea        |
|         24 | chloe      |
|         25 | camille    |
|         26 | alexandre  |
|         27 | julie      |
|         28 | leo        |
|         29 | antoine    |
|         30 | lola       |
|         31 | celia      |
|         32 | anna       |
|         33 | caroline   |
|         34 | adele      |
|         35 | sabrina    |
|         36 | nathalie   |
|         37 | franck     |
|         38 | tom        |
|         39 | johan      |
|         40 | priscillia |
|         41 | assia      |
|         42 | nathan     |
|         43 | aurore     |
|         44 | marie      |
|         45 | oceane     |
|         46 | enzo       |
|         47 | ines       |
|         48 | hugo       |
|         49 | jonathan   |
|         50 | axelle     |
|         51 | morgane    |
|         52 | melissa    |
|         53 | kevin      |
|         54 | ophelie    |
|         55 | victoria   |
|         56 | alexis     |
|         57 | robin      |
+------------+------------+



QUESTION 




**Question 1 : Affichez le nom des agences**





**Question 2 : Affichez le numéro de l'agence "Orpi".**


**Question 3 : Affichez le premier enregistrement de la table logement**


**Question 4 : Affichez le nombre de logements (Alias : Nombre_de_logements)**

SELECT COUNT(*) FROM logement;

**Question 5 : Affichez les logements à vendre à moins de 150 000 € dans l'ordre croissant des prix:**


**Question 6 : Affichez le nombre de logements à la location (alias : nombre)**

SELECT COUNT(*) FROM logement WHERE categorie="location";

**Question 7 : Affichez les villes différentes recherch�es par les personnes demandeuses d'un logement**


**Question 8 : Affichez le nombre de biens à vendre par ville**

SELECT ville,COUNT(*) FROM logement GROUP BY ville ORDER BY ville;

**Question 9 : Quelles sont les id des logements destinés à la location ?**


**Question 10 : Quels sont les id des logements entre 20 et 30 mètres carrés?**

SELECT idLogement FROM logement WHERE superficie BETWEEN 20 AND 30;

**Question 11 : Quel est le prix vendeur (hors commission) du logement le moins cher à vendre ? (Alias : prix minimum)**

SELECT MIN(prix) FROM logement WHERE categorie="vente";

**Question 12 : Dans quelles villes se trouve les maisons à vendre ?****

SELECT genre,ville FROM logement WHERE genre="maison";

**Question 13 : L'agence Orpi souhaite diminuer les frais qu'elle applique sur le logement ayant l'id  5246. Passer les frais de ce logement de 800 à 730€.**

Query OK, 1 row affected

**Question 14 : Quels sont les logements gérés par l'agence  laforet**

SELECT idLogement FROM logement WHERE idLogement IN (SELECT idLogement FROM logement_agence WHERE idAgence IN (SELECT idAgence FROM agence WHERE nom ="laforet"));

**Question 15 : Affichez le nombre de propriétaires dans la ville de Paris (Alias : Nombre)**


**Question 16 : Affichez les informations des trois premieres personnes souhaitant acheter un logement**

SELECT p.idPersonne,p.prenom,d.idDemande,d.idPersonne,d.genre,d.ville,d.budget,d.superficie,d.categorie FROM personne p INNER JOIN demande d ON p.idPersonne = d.idPersonne WHERE d.categorie="vente" LIMIT 0,3;

**Question 17 : Affichez le prénom du vendeur pour le logement ayant la référence  5770** 


**Question 18 : Affichez les prénoms des personnes souhaitant accéder à un logement sur la ville de Lyon**

SELECT prenom FROM personne WHERE idPersonne IN (SELECT idPersonne FROM demande WHERE ville="lyon");

**Question 19 : Affichez les prénoms des personnes souhaitant acc�der à un logement en location sur la ville de Paris**


**Question 20 : Affichez les prénoms des personnes souhaitant acheter un logement de la plus grande à la plus petite superficie**

SELECT DISTINCT p.prenom,d.superficie FROM personne p INNER JOIN demande d WHERE p.idPersonne=d.idPersonne AND d.categorie="vente" ORDER BY d.superficie DESC;

**Question 21 : Quel sont les prix finaux propos�s par les agences pour la maison à la vente ayant la référence  5091  ? (Alias : prix avec frais d'agence)**
+---------------------------+
| prix avec frais d'agence  |
+---------------------------+
|                   1585500 |
|                   1566050 |
+---------------------------+

**Question 22 : Indiquez les frais ajoutés par l'agence immobilière pour le logement ayant la référence  5873 ?**

SELECT l.idLogement,l.prix,la.frais,SUM(l.prix+la.frais) AS "prix total" FROM logement l INNER JOIN logement_agence la ON l.idLogement = la.idLogement WHERE l.idLogement=5873;

**Question 23 : Si l'ensemble des logements étaient vendus ou loués demain, quel serait le bénéfice généré grâce aux frais d'agence et pour chaque agence (Alias : benefice, classement : par ordre croissant des gains)**


**Question 24 : Affichez les id des biens en location, les prix, suivis des frais d'agence (classement : dans l'ordre croissant des prix) :**

SELECT l.prix,la.idLogement,la.frais FROM logement l INNER JOIN logement_agence la ON l.idLogement = la.idLogement WHERE l.categorie="location" ORDER BY l.prix;

**Question 25 : Quel est le prénom du propriétaire proposant le logement le moins cher à louer ?**


**Question 26 : Affichez le prénom et la ville où se trouve le logement de chaque propriétaire**

SELECT p.prenom,l.ville FROM personne p INNER JOIN logement_personne lp ON p.idPersonne = lp.idPersonne INNER JOIN logement l on lp.idLogement = l.idLogement;

**Question 27 : Quel est l'agence immobilière s'occupant de la plus grande gestion de logements répertoriés à Paris ? (alias : nombre, classement : trié par ordre décroissant)**


**Question 28 : Affichez le prix et le prénom des vendeurs dont les logements sont proposés à 130000 € ou moins en prix final avec frais appliqués par les agences (alias : prix final, classement : ordre croissant des prix finaux) :**

SELECT p.prenom,l.prix+la.frais AS "prix final" FROM personne p INNER JOIN logement_personne lp ON p.idPersonne = lp.idPersonne INNER JOIN logement l ON lp.idLogement = l.idLogement INNER JOIN logement_agence la ON l.idLogement = la.idLogement WHERE l.prix < 130000 AND "prix final" < 130000 AND l.categorie="vente" ORDER BY "prix final" DESC;
**Question 29 : Affichez le nombre de logements à la vente dans la ville de recherche de hugo  (alias : nombre)**


**Question 30 : Affichez le nombre de logements à la vente dans la ville de recherche de  hugo  et dans la superficie minimum qu'il attend ou dans une superficie supérieure (alias : nombre):**

