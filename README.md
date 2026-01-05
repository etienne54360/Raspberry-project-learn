# Raspberry-project-learn

# Cahier des charges

## 1. Présentation générale du projet

### 1.1 Contexte

Ce projet a pour objectif de développer une application embarquée en langage **C** sur une **Raspberry Pi**, afin de renforcer les compétences en développement logiciel bas niveau, proches des contraintes rencontrées en environnement industriel ou embarqué.

Le projet est volontairement structuré comme un **mini-projet professionnel**, avec des exigences fonctionnelles, techniques et des critères de validation clairs.

### 1.2 Intitulé du projet

**Station de supervision environnementale connectée**

### 1.3 Objectifs pédagogiques

Objectifs principaux :

* Maîtriser le langage **C** dans un contexte réel
* Comprendre l’interaction **logiciel / matériel**
* Apprendre à structurer un projet C de taille moyenne
* Utiliser Git/GitHub dans un workflow propre

Compétences ciblées :

* Programmation C (structures, pointeurs, gestion mémoire)
* Programmation système Linux
* Accès matériel (GPIO, I2C, SPI)
* Gestion d’erreurs et robustesse logicielle
* Architecture logicielle modulaire

---

## 2. Description fonctionnelle

### 2.1 Fonction principale

Le système doit permettre de :

* Mesurer des données environnementales via des capteurs
* Traiter et stocker ces données
* Les afficher localement
* Les transmettre à un utilisateur (console ou réseau)

### 2.2 Fonctions détaillées

#### F1 – Acquisition des données capteurs

* Lecture périodique de :

  * Température
  * Humidité
  * (Optionnel) pression ou luminosité

#### F2 – Traitement des données

* Moyenne glissante
* Détection de seuils (alerte)
* Filtrage simple du bruit

#### F3 – Affichage local

* Affichage via :

  * Console (CLI)
  * OU écran LCD (option avancée)

#### F4 – Stockage des données

* Enregistrement dans un fichier local
* Format texte structuré (CSV ou log)

#### F5 – Interface utilisateur

* Menu en ligne de commande
* Commandes pour :

  * Démarrer / arrêter les mesures
  * Modifier la période d’échantillonnage
  * Consulter l’historique

---

## 3. Contraintes techniques

### 3.1 Matériel

* Raspberry Pi (3, 4 ou équivalent)
* Carte SD avec Raspberry Pi OS
* Capteurs compatibles (exemples) :

  * DHT11 / DHT22
  * BME280
* Connexion GPIO / I2C

### 3.2 Logiciel

* Langage : **C (C99 minimum)**
* OS : Linux (Raspberry Pi OS)
* Compilation : `gcc`
* Build system : `Makefile`

### 3.3 Contraintes de développement

* Pas de frameworks haut niveau
* Utilisation limitée de bibliothèques externes
* Accès matériel via :

  * `/sys/class/gpio`
  * `/dev/i2c-*`

---

## 4. Architecture logicielle

### 4.1 Organisation des fichiers

```
project/
│── src/
│   ├── main.c
│   ├── sensor.c
│   ├── display.c
│   ├── storage.c
│   ├── menu.c
│── include/
│   ├── sensor.h
│   ├── display.h
│   ├── storage.h
│   ├── menu.h
│── data/
│── Makefile
│── README.md
```

### 4.2 Description des modules

* **main** : point d’entrée, orchestration
* **sensor** : communication capteurs
* **display** : affichage console/LCD
* **storage** : gestion fichiers
* **menu** : interface utilisateur

---

## 5. Exigences non fonctionnelles

### 5.1 Qualité du code

* Code commenté
* Fonctions courtes et claires
* Nommage explicite

### 5.2 Robustesse

* Gestion des erreurs matérielles
* Vérification des retours système
* Aucune fuite mémoire

### 5.3 Performance

* Faible utilisation CPU
* Temps de réponse < 100 ms pour les commandes

---

## 6. Gestion de projet & Git

### 6.1 Organisation Git

* Branche `main` : stable
* Branche `develop`
* Branches `feature/*`

### 6.2 Commits

* Petits commits
* Messages clairs

---

## 7. Tests et validation

### 7.1 Tests unitaires (simples)

* Fonctions de traitement
* Fonctions de stockage

### 7.2 Tests fonctionnels

* Lecture capteurs
* Affichage correct
* Enregistrement valide

### 7.3 Critères de validation

Le projet est validé si :

* Les données sont correctement acquises
* Le programme fonctionne sans crash 24h
* Le code est lisible et structuré

---

## 8. Évolutions possibles (bonus)

* Serveur web embarqué
* Envoi MQTT
* Multithreading (pthread)
* Service systemd
* Cross-compilation

---

## 9. Livrables attendus

* Code source complet
* README détaillé
* Schéma de câblage
* Journal de développement

---

## 10. Niveau de difficulté

* Niveau : **Intermédiaire → Avancé**
* Durée estimée : 3 à 6 semaines

---

**Fin du cahier des charges**
