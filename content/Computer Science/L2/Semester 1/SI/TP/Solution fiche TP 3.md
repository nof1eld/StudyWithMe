# Introduction

Dans ce TP, nous allons aborder plusieurs exercices de codification et de modélisation des systèmes d’information. Ils couvrent divers aspects de la codification de l’information, la gestion des entités et des associations, ainsi que la conception de systèmes d’information pour différentes applications pratiques.


# Codification de L’information

## Exercice 01:
#### 1. Type de chaque code :
- **Numéro employé:**  
  Codification Articulée.
- **Ouvrage de bibliothèque:**  
  Codification Articulée.  
- **Matricule de véhicule:**  
  Codification Articulée.  

#### 2. Critique et propositions d'amélioration :
- **Numéro employé:**
  - **Critique:**  
    - Limitation à 99 services (2 positions).  
    - Maximum 999 employés (3 positions).  
  - **Solution:**  
    - 4 positions pour le service et 4 pour le séquentiel. 

- **Ouvrage bibliothèque:**
  - **Critique:**  
    - La structure actuelle pourrait devenir insuffisante à mesure que de nouveaux domaines ou sous-domaines sont ajoutés.  
    - Les numéros séquentiels peuvent entrer en conflit lorsque de nouveaux ouvrages sont ajoutés dans des catégories déjà existantes.  
  - **Solution:**  
    - Augmenter le nombre de positions (3 positions pour le code domaine, 3 pour le sous-domaine, et 4 pour le numéro séquentiel).  
    - Ajouter une position pour le numéro de version ou d'édition.  
    - Utiliser un code à barres pour une identification plus rapide et moins sujette à erreur.  

- **Matricule véhicule:**
  - **Critique:**  
    - Ce format semble complexe et pourrait mener à des confusions, surtout avec la combinaison des positions pour le type et l'année.  
    - Les codes pour la willaya (zone géographique) peuvent devenir obsolètes ou insuffisants si le nombre de régions ou de subdivisions change.  
  - **Solution:**  
    - Simplifier la structure en séparant clairement les différentes parties (6 positions pour le numéro chronologique, 1 position pour le type, 2 positions pour l'année, et 2 positions pour le code willaya).  
    - Éviter l’utilisation excessive de numéros chronologiques sans un système de référence établi.  

#### 3. Caractéristiques de la codification:
- Elle ne doit pas être ambigüe.  
- Elle doit s’adapter aux besoins des utilisateurs.  
- Elle doit permettre l’insertion de nouvelles infos et l’extension de l’ensemble des objets à codifier.  
- Elle doit être concise.  
- Elle doit être significative.  

---

### Exercice 02:
- **a:** 3 positions numériques (001…019 / 020…820).  
- **b:** 1 position alphabétique (1.5v: a, 3v: b, 4.5v: c, 6v: d, 12v: e, 20v: f, 110v: g, 220v: h).  
- **c:** 1 position alphabétique (t / d).  
- **d:** 1 position numérique (0…9).  
- **e:** 1 position alphabétique (d / b).  
- **f:** 1 position alphabétique (v / a / k).  

**Exemple:**  
Ampoule de 15 watts de voltage 3v transparente de la forme 6 de mode à douille Krypton.  
Codification finale : `015-b-t-6-d-k`.  

---

### Exercice 03:
#### Proposition de la meilleure codification:
- Position numérique pour le niveau:
  - 1: Technicien  
  - 2: Technicien Supérieur  
  - 3: Ingénieur  
- Position alphabétique pour les spécialités:  
  - Gestion, Finance, Comptabilité, Marketing.  
- Position alphabétique pour la section (a, b, c).  
- Positions numériques pour le code étudiant (01…90).  

**Exemple:**  
Étudiant numéro 34 de la 3ème section, technicien supérieur de spécialité Gestion.  
Codification finale : `2-G-b-34`.  

---

### Exercice 04:
#### Analyse du numéro d'inscription comme code résident unique :
**Non, il n'est pas judicieux.**  
- **Raisons principales :**
  - **Nature hétérogène des résidents:**  
    - Diversité des statuts: Les résidents incluent aussi des enseignants.  
    - Multiples inscriptions: Un étudiant peut changer de formation ou d'université, modifiant son numéro d'inscription.  
  - **Manque de durabilité:**  
    - Changement de numéro: Lors de réinscriptions ou transferts.  
    - Perte d'historique: Difficile de suivre un résident sur plusieurs années.  

#### Proposition:
Une codification basée sur le type de résident, l’année d’inscription, et l'institut.  
- **Type de Résident (1 position):**
  - Enseignant: `E`  
  - Étudiant: `S`  
- **Année d'inscription (2 positions):** Deux derniers chiffres de l'année.  
- **Institut (3 positions):**
  - ECG: Institut des sciences économiques, commerciales et des sciences de gestion.  
  - SHS: Institut des sciences humaines et sociales.  
  - SPD: Institut des sciences politiques et de droit.  

**Exemple:**  
Étudiant inscrit en 2023 à l’institut des sciences humaines et sociales:  
Code final : `S23SHS`.  

---
# Dictionnaire de donné
## Exercice 5:
| Code     | Designation               | Taille | Type | E/C | obs        |
| -------- | ------------------------- | ------ | ---- | --- | ---------- |
| N.C      | Numéro de Bon de Commande | 5      | N    | E   | ID         |
| N.Cl     | Numéro Client             | 5      | N    | E   | ID         |
| Nm.Cl    | Nom Client                | 30     | A    | E   |            |
| Adr.Cl   | Adresse Client            | 50     | A/N  | E   |            |
| Tl.Cl    | Téléphone Client          | 12     | N    | E   |            |
| Rf.Prd   | Référence Produit         | 15     | A    | E   |            |
| Ds.Prd   | Désignation Produit       | 50     | A    | E   |            |
| P.Un     | Prix Unitaire             | 6      | N    | E   |            |
| Qnt      | Quantité                  | 2      | N    | E   |            |
| Mn       | Montant                   | 8      | N    | E   |            |
| N.Ft     | Numéro de Facture         | 10     | N    | E   |            |
| Date.Ft  | Date de Facture           | 10     | Date | E   |            |
| C.Cmd    | Code Commande             | 10     | A    | E   |            |
| Date.Cmd | Date de Commande          | 10     | Date | E   |            |
| Mt.Cl    | Matricule Client          | 10     | A/N  | C   | Qnt * P.Un |
| Mn.T Ft  | Montant Total Facture     | 9      | N    | C   | Qnt * P.Un |

---
## Exercice 6:

### 1. Les différents documents circulent dans ce système d'information

- **Devis**
- **Bon de commande**
- **Facture**
- **Bon de livraison**
- **Commande client**
- **Commande fournisseur**

### 2. Une étude de chaque document

#### Devis
- **Émetteur** : Département Commercial.
- **Rôle** : Informer le client des prix et conditions avant confirmation.

#### Bon de commande
- **Émetteur** : Département Commercial ou Logistique.
- **Rôle** : Demander des produits ou services (internes/externes).

#### Facture
- **Émetteur** : Département Comptabilité.
- **Rôle** : Demander le paiement des commandes validées.

#### Bon de livraison
- **Émetteur** : Département Logistique.
- **Rôle** : Accompagner la livraison pour validation par le client.

#### Commande client
- **Émetteur** : Client.
- **Rôle** : Initier une transaction d’achat.

#### Commande fournisseur
- **Émetteur** : Département Logistique.
- **Rôle** : Réapprovisionner le stock.

### 3. Exemplaires des documents (modèles vides)

#### Devis
Le devis contient les informations suivantes :
- **Numéro** : Identifiant unique du devis.
- **Client** : Nom ou identifiant du client.
- **Produits** : Liste des produits ou services concernés.
- **Prix unitaire** : Prix d’unité pour chaque produit ou service.
- **Montant total** : Somme totale des coûts.
- **Date d’émission** : Date à laquelle le devis est établi.
- **Validité** : Durée pendant laquelle le devis est valable.

#### Bon de commande
Le bon de commande contient les informations suivantes :
- **Numéro** : Identifiant unique du bon.
- **Destinataire** : Nom ou département destinataire de la commande.
- **Produits** : Liste des produits ou services commandés.
- **Quantités** : Nombre de chaque produit demandé.
- **Date** : Date de la commande.

#### Facture
La facture contient les informations suivantes :
- **Numéro** : Identifiant unique de la facture.
- **Client** : Nom ou identifiant du client concerné.
- **Produits** : Liste des produits ou services facturés.
- **Quantités** : Quantité de chaque produit/service facturé.
- **Prix total** : Montant global dû.
- **Date d’échéance** : Dernière date pour le paiement.

#### Bon de livraison
Le bon de livraison contient les informations suivantes :
- **Numéro** : Identifiant unique du bon.
- **Client** : Nom ou identifiant du client destinataire.
- **Produits livrés** : Liste des produits effectivement livrés.
- **Date** : Date de la livraison.

#### Commande client
La commande client contient les informations suivantes :
- **Numéro** : Identifiant unique de la commande.
- **Client** : Nom ou identifiant du client ayant passé la commande.
- **Produits demandés** : Liste des produits ou services demandés.
- **Quantités** : Nombre de chaque produit demandé.
- **Date** : Date de la commande.

#### Commande fournisseur
La commande fournisseur contient les informations suivantes :
- **Numéro** : Identifiant unique de la commande.
- **Fournisseur** : Nom ou identifiant du fournisseur.
- **Produits demandés** : Liste des produits ou services demandés au fournisseur.
- **Quantités** : Nombre de chaque produit demandé.
- **Date** : Date de la commande.


### 4. Les acteurs de flux d’information

- Département Commercial
- Département Logistique
- Département Comptabilité
- Clients
- Fournisseurs
- Transporteurs

### 5. Le le diagramme de flux d’information

![[Pasted image 20241209183657.png]]

### 6. Diagramme de modèle E/A

![[Pasted image 20241209223842.png]]

---
# Modèle Entité Association
## Exercice 7:

1- Classification

| **Entité**     | **Identifiant** | **Propriété**      | **Association** |
| -------------- | --------------- | ------------------ | --------------- |
| **Université** | Id_Université   | Nom_Université     | Délivrer        |
|                |                 | Adresse_Université |                 |
| **Étudiant**   | Id_Étudiant     | Nom_Étudiant       | S'inscrire      |
|                |                 | Prénom_Étudiant    |                 |
| **Diplôme**    | Id_Diplôme      | Titre_Diplôme      | Obtenir         |
2- Diagramme du modèle Entité-Association

![[Pasted image 20241209201833.png]]

---
## Exercice 8:

![[Pasted image 20241207225050.png]]

---
## Exercice 9:
1. Oui, il est possible d’avoir des clients homonymes grâce à un numéro unique d’identifiant.  
2. Oui, le client peut réserver plusieurs chambres à une date donnée.  
3. Non, une réservation correspond à une seule chambre.  
4. Non, il est impossible de réserver une chambre sur plusieurs jours (seule une date est incluse dans la réservation).  
5. Oui, il est possible.  
6. Non, il est impossible de réserver une chambre plusieurs fois à une date donnée.

---
## Exercice 10:

![[Pasted image 20241207225324.png]]

---
## Exercice 11:

![[Pasted image 20241207225502.png]]

---
## Exercice 12:

![[Pasted image 20241209224728.png]]

# Conclusion

En conclusion, ce TP nous a permis de comprendre l’importance de la codification adéquate et de la modélisation des systèmes d’information. Les exercices réalisés ont illustré comment structurer et organiser les données de manière efficace pour répondre aux besoins spécifiques de différentes organisations. La maîtrise de ces concepts est essentielle pour le développement de systèmes d’information robustes et performants.