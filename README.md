# Gestionnaire d'Inventaire (Client-Serveur Java)

![Language](https://img.shields.io/badge/Language-Java-orange) ![Network](https://img.shields.io/badge/Network-Sockets-blue) ![Concepts](https://img.shields.io/badge/Concepts-Multithreading%20%7C%20Serialization-green)

## Description
Ce projet est une application Client-Serveur développée en Java permettant de gérer un inventaire d'objets (Items) inspiré de l'univers du jeu vidéo. Les utilisateurs peuvent se créer un compte, s'authentifier, et gérer leur propre inventaire via une interface en ligne de commande (CLI).

L'objectif principal de ce projet universitaire (L2) était de mettre en pratique la programmation réseau en Java, la gestion des accès concurrents (Threads), et la persistance des données par sérialisation d'objets.

## Architecture Technique
Le système repose sur une architecture centralisée où le serveur agit comme le gestionnaire de la base de données et l'arbitre des requêtes.

* **Serveur multi-threadé :** Écoute sur un `ServerSocket` (Port 8080 par défaut). Chaque client connecté est pris en charge par un Thread dédié (`ConnexionClient`), permettant au serveur de gérer jusqu'à 50 utilisateurs simultanément.
* **Client interactif :** Gère les entrées utilisateur via `Scanner` et communique avec le serveur via des `Socket`.
* **Communication par Objets :** Le protocole d'échange est basé sur l'envoi d'instances de la classe `Message` via `ObjectInputStream` et `ObjectOutputStream`. Chaque message contient une commande spécifique et une charge utile (payload).
* **Persistance locale :** Sauvegarde locale des utilisateurs et des inventaires dans un fichier binaire (`items.dat`) via la sérialisation d'une `HashMap`.

## Fonctionnalités
* **Authentification :** Création de compte et connexion sécurisée par pseudo et mot de passe.
* **Opérations CRUD sur les Items :**
    * **Create :** Ajouter un objet avec son nom, son type, sa durabilité et sa valeur.
    * **Read :** Rechercher les caractéristiques d'un objet spécifique.
    * **Update :** Modifier les statistiques d'un objet existant.
    * **Delete :** Supprimer un objet de l'inventaire.
* **Isolation des données :** Chaque utilisateur possède son propre inventaire, complètement séparé de celui des autres joueurs.

## Installation et Lancement

### Prérequis
* Java Development Kit (JDK) 8 ou supérieur.

### Compilation
Ouvrez un terminal dans le dossier du projet et compilez l'ensemble des fichiers sources :
```bash
javac *.java
