# Projet de Gestion de Parc Automobile

Ce projet implémente un système de gestion de parc automobile pour une entreprise de location de véhicules. Le système permet d'ajouter des véhicules (voitures et camions), de gérer les clients, de louer et retourner des véhicules, et d'afficher les véhicules disponibles.

## Fonctionnalités

1. **Gestion des véhicules** : Ajout, location et retour des véhicules dans le parc automobile.
2. **Gestion des clients** : Création de profils de clients avec informations personnelles.
3. **Disponibilité des véhicules** : Affichage des véhicules disponibles pour la location.
4. **Exceptions personnalisées** : Gestion des erreurs spécifiques pour la location.

## Structure des Classes

### 1. Interface `Louable`
L'interface `Louable` définit les méthodes pour gérer la location d'un véhicule :
- `louer()` : Indique que le véhicule est loué.
- `retourner()` : Indique que le véhicule est retourné.

### 2. Classe Abstraite `Vehicule`
`Vehicule` est une classe abstraite qui implémente `Louable`. Elle représente la structure de base pour tout véhicule du parc.

#### Attributs
- `immatriculation` : Identifiant unique du véhicule.
- `marque` : Marque du véhicule.
- `modele` : Modèle du véhicule.
- `anneeMiseEnService` : Année de mise en service.
- `kilometrage` : Kilométrage du véhicule.
- `estDisponible` : Indique si le véhicule est disponible pour la location.

#### Méthodes
- `calculerPrixLocation()` : Méthode abstraite pour calculer le prix de location.
- `isDisponible()` : Retourne la disponibilité du véhicule.
- `setEstDisponible(boolean)` : Définit la disponibilité du véhicule.

### 3. Classes `Voiture` et `Camion`
Ces classes héritent de `Vehicule` et ajoutent des attributs et méthodes spécifiques.

#### Classe `Voiture`
- **Attributs** : `nombrePlaces` (nombre de places dans la voiture) et `typeCarburant` (type de carburant utilisé).
- **Méthodes** :
  - `calculerPrixLocation()` : Retourne le prix de location d'une voiture (ici fixé à 50.0).
  - `louer()` et `retourner()` : Modifient la disponibilité du véhicule.

#### Classe `Camion`
- **Attributs** : `capaciteChargement` (capacité de chargement en tonnes) et `nombreEssieux` (nombre d'essieux du camion).
- **Méthodes** :
  - `calculerPrixLocation()` : Retourne le prix de location d'un camion (ici fixé à 80.0).
  - `louer()` et `retourner()` : Modifient la disponibilité du véhicule.

### 4. Classe `Client`
La classe `Client` représente les clients de l'entreprise de location.

#### Attributs
- `nom` : Nom du client.
- `prenom` : Prénom du client.
- `numeroPermis` : Numéro de permis du client.
- `numeroTelephone` : Numéro de téléphone du client.
- `locationsEnCours` : Liste des véhicules actuellement loués par le client.

#### Méthodes
- `ajouterLocation(Vehicule)` : Ajoute un véhicule à la liste des locations en cours du client.
- `supprimerLocation(Vehicule)` : Supprime un véhicule de la liste des locations en cours.

### 5. Exceptions Personnalisées
Deux exceptions spécifiques pour gérer les erreurs :

- **`VehiculeIndisponibleException`** : Levée lorsque le véhicule demandé n'est pas disponible pour la location.
- **`ClientNonAutoriseException`** : Levée lorsque le client ne répond pas aux critères nécessaires pour louer un véhicule.

### 6. Classe `ParcAutomobile`
Cette classe gère l'ensemble des véhicules dans le parc automobile.

#### Attributs
- `vehicules` : Liste des véhicules du parc.

#### Méthodes
- `ajouterVehicule(Vehicule)` : Ajoute un véhicule au parc.
- `listerVehiculesDisponibles()` : Affiche les véhicules disponibles pour la location.
- `trouverVehicule(String immatriculation)` : Recherche un véhicule par son immatriculation.

### 7. Classe Principale `Main`
La classe `Main` contient le menu principal pour interagir avec le système.

#### Menu Principal
- **Options** :
  - `1. Ajouter un véhicule` : Permet d'ajouter une voiture ou un camion au parc.
  - `2. Ajouter un client` : Permet d'ajouter un nouveau client.
  - `3. Louer un véhicule` : Permet de louer un véhicule (en cours d'implémentation).
  - `4. Retourner un véhicule` : Permet de retourner un véhicule (en cours d'implémentation).
  - `5. Afficher les véhicules disponibles` : Liste les véhicules disponibles.
  - `6. Quitter` : Quitte le programme.

#### Méthodes Utilisées dans le Menu
- `ajouterVehicule(Scanner)` : Gère l'ajout de véhicule avec des informations spécifiques selon le type de véhicule.
- `ajouterClient(Scanner)` : Gère l'ajout d'un client avec ses informations personnelles.
- `louerVehicule(Scanner)` : (À implémenter) Processus de location de véhicule avec gestion des exceptions.
- `retournerVehicule(Scanner)` : (À implémenter) Processus de retour de véhicule.

## Instructions pour Exécuter le Programme

1. **Compiler le Programme**  
   Assurez-vous d'avoir le JDK installé et compilez le fichier `Main.java` :
   ```bash
   javac Main.java
