QUESTION 

**Question 1 : Affichez le nom des agences**

SELECT nom FROM agence;

**Question 2 : Affichez le numéro de l'agence "Orpi".**

SELECT idAgence FROM agence WHERE nom = "orpi";

**Question 3 : Affichez le premier enregistrement de la table logement**

SELECT * FROM logement LIMIT 1;

**Question 4 : Affichez le nombre de logements (Alias : Nombre_de_logements)**

**Question 5 : Affichez les logements à vendre à moins de 150 000 € dans l'ordre croissant des prix:**

SELECT * FROM logement WHERE categorie = "vente" AND prix < 150000 ORDER BY prix;

**Question 6 : Affichez le nombre de logements à la location (alias : nombre)**

**Question 7 : Affichez les villes différentes recherch�es par les personnes demandeuses d'un logement**

SELECT ville FROM demande GROUP BY ville;

**Question 8 : Affichez le nombre de biens à vendre par ville**

**Question 9 : Quelles sont les id des logements destinés à la location ?**

SELECT idLogement FROM logement WHERE categorie = "location";

**Question 10 : Quels sont les id des logements entre 20 et 30 mètres carrés?**

**Question 11 : Quel est le prix vendeur (hors commission) du logement le moins cher à vendre ? (Alias : prix minimum)**

**Question 12 : Dans quelles villes se trouve les maisons à vendre ?**

**Question 13 : L'agence Orpi souhaite diminuer les frais qu'elle applique sur le logement ayant l'id  5246. Passer les frais de ce logement de 800 à 730€.**

UPDATE logement_agence SET frais = 730 WHERE idLogement = 5246;

**Question 14 : Quels sont les logements gérés par l'agence  laforet**

**Question 15 : Affichez le nombre de propriétaires dans la ville de Paris (Alias : Nombre)**

SELECT count(idLogement) AS nombre FROM logement WHERE ville = "paris";                                                   affiche 14 au lieu de 13

**Question 16 : Affichez les informations des trois premieres personnes souhaitant acheter un logement**

**Question 17 : Affichez le prénom du vendeur pour le logement ayant la référence  5770** 

SELECT personne.prenom FROM personne INNER JOIN logement_personne ON personne.idPersonne = logement_personne.idPersonne WHERE idLogement = 5770;

**Question 18 : Affichez les prénoms des personnes souhaitant accéder à un logement sur la ville de Lyon**

**Question 19 : Affichez les prénoms des personnes souhaitant acc�der à un logement en location sur la ville de Paris**

SELECT personne.prenom FROM personne INNER JOIN demande ON personne.idPersonne = demande.idPersonne WHERE ville = "paris" AND categorie = "location";

**Question 20 : Affichez les prénoms des personnes souhaitant acheter un logement de la plus grande à la plus petite superficie**

**Question 21 : Quel sont les prix finaux propos�s par les agences pour la maison à la vente ayant la référence  5091  ? (Alias : prix avec frais d'agence)**

SELECT SUM(prix, frais) AS "prix avec frais d'agence" FROM logement INNER JOIN WHERE categorie = "vente" AND idLogement = 5091;

marche pas

**Question 22 : Indiquez les frais ajoutés par l'agence immobilière pour le logement ayant la référence  5873 ?**

**Question 23 : Si l'ensemble des logements étaient vendus ou loués demain, quel serait le bénéfice généré grâce aux frais d'agence et pour chaque agence (Alias : benefice, classement : par ordre croissant des gains)**

SELECT agence.nom, SUM(logement_agence.frais) AS benefice FROM agence INNER JOIN logement_agence ON logement_agence.idAgence = agence.idAgence GROUP BY nom ORDER BY benefice;


**Question 24 : Affichez les id des biens en location, les prix, suivis des frais d'agence (classement : dans l'ordre croissant des prix) :**

**Question 25 : Quel est le prénom du propriétaire proposant le logement le moins cher à louer ?**

SELECT personne.prenom FROM personne INNER JOIN logement_personne ON personne.idPersonne = logement_personne.idPersonne INNER JOIN logement ON logement_personne.idLogement = logement.idLogement WHERE categorie = "location" ORDER BY prix LIMIT 1;

**Question 26 : Affichez le prénom et la ville où se trouve le logement de chaque propriétaire**

**Question 27 : Quel est l'agence immobilière s'occupant de la plus grande gestion de logements répertoriés à Paris ? (alias : nombre, classement : trié par ordre décroissant)**

SELECT agence.nom, COUNT(logement.ville) AS nombre FROM agence INNER JOIN logement_agence ON agence.idAgence = logement_agence.idAgence INNER JOIN logement ON logement_agence.idLogement = logement.idLogement WHERE ville = "paris" GROUP BY nom ORDER BY nombre DESC, nom DESC;

**Question 28 : Affichez le prix et le prénom des vendeurs dont les logements sont proposés à 130000 € ou moins en prix final avec frais appliqués par les agences (alias : prix final, classement : ordre croissant des prix finaux) :**

**Question 29 : Affichez le nombre de logements à la vente dans la ville de recherche de hugo  (alias : nombre)**

SELECT COUNT(demande.categorie) AS nombre FROM demande INNER JOIN personne ON demande.idPersonne = personne.idPersonne WHERE categorie = (SELECT demande.ville FROM demande INNER JOIN personne ON personne.idPersonne = demande.idPersonne WHERE personne = "hugo") AND categorie = "vente";

Marche pas

**Question 30 : Affichez le nombre de logements à la vente dans la ville de recherche de  hugo  et dans la superficie minimum qu'il attend ou dans une superficie supérieure (alias : nombre):**