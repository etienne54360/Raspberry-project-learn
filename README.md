Test test

# Cahier des charges

## 1. Présentation générale du projet

### 1.1 Contexte

Ce projet a pour objectif de développer une **application embarquée en langage C** sur une **Arduino MEGA 2560**, afin de renforcer les compétences en développement bas niveau, proches des contraintes rencontrées en **systèmes embarqués temps réel** et en électronique industrielle.

Le projet est structuré comme un **mini-projet professionnel**, avec des exigences fonctionnelles, techniques et des critères de validation clairs.

### 1.2 Intitulé du projet

**Station de supervision environnementale embarquée (Arduino MEGA)**

### 1.3 Objectifs pédagogiques

Objectifs principaux :

* Maîtriser le langage **C embarqué** (sans OS)
* Comprendre le fonctionnement d’un **microcontrôleur AVR**
* Interagir directement avec le matériel (registres, interruptions)
* Structurer un projet C embarqué de taille moyenne

Compétences ciblées :

* Programmation C bas niveau
* Architecture logicielle embarquée
* Gestion du temps (timers, interruptions)
* Communication série, I2C, SPI
* Gestion mémoire sur microcontrôleur

---

## 2. Description fonctionnelle

### 2.1 Fonction principale

Le système doit permettre de :

* Mesurer des données environnementales via des capteurs
* Traiter ces données localement
* Les transmettre à un utilisateur via liaison série
* Signaler des alertes via LED ou buzzer

### 2.2 Fonctions détaillées

#### F1 – Acquisition des données capteurs

* Lecture périodique de :

  * Température
  * Humidité
  * (Optionnel) pression ou luminosité

#### F2 – Traitement des données

* Moyenne glissante
* Détection de dépassement de seuils
* Mise à l’échelle des valeurs

#### F3 – Interface utilisateur série

* Communication via **UART (USB)**
* Menu texte accessible depuis un terminal PC

#### F4 – Signalisation locale

* LED d’état (OK / Alerte)
* Buzzer (optionnel)

#### F5 – Configuration utilisateur

* Modification des paramètres via commandes série :

  * Période d’échantillonnage
  * Seuils d’alerte

---

## 3. Contraintes techniques

### 3.1 Matériel

* Arduino **MEGA 2560**
* Capteurs compatibles :

  * DHT11 / DHT22
  * BME280
* LED + résistances
* (Optionnel) Buzzer

### 3.2 Logiciel

* Langage : **C (AVR-GCC)**
* Pas de système d’exploitation
* Accès direct au matériel
* Utilisation possible de l’IDE Arduino **uniquement comme outil de compilation**

### 3.3 Contraintes de développement

* Interdiction d’utiliser les fonctions Arduino haut niveau (`digitalWrite`, `delay`, etc.)
* Accès matériel via :

  * Registres AVR
  * Timers matériels
  * Interruptions

---

## 4. Architecture logicielle

### 4.1 Organisation des fichiers

```
project/
│── src/
│   ├── main.c
│   ├── sensor.c
│   ├── uart.c
│   ├── timer.c
│   ├── alert.c
│── include/
│   ├── sensor.h
│   ├── uart.h
│   ├── timer.h
│   ├── alert.h
│── Makefile
│── README.md
```

### 4.2 Description des modules

* **main** : boucle principale, machine d’état
* **sensor** : gestion capteurs
* **uart** : communication série
* **timer** : gestion du temps
* **alert** : LED / buzzer

---

## 5. Exigences non fonctionnelles

### 5.1 Qualité du code

* Code commenté
* Fonctions courtes
* Pas de variables globales inutiles

### 5.2 Robustesse

* Gestion des erreurs capteurs
* Watchdog activé
* Comportement déterministe

### 5.3 Performance

* Respect des contraintes temps réel
* Boucle principale non bloquante

---

## 6. Gestion du temps et interruptions

* Utilisation d’un **timer matériel**
* Interruptions périodiques
* Pas de `delay()`

---

## 7. Gestion de projet & Git

### 7.1 Organisation Git

* Branche `main` : stable
* Branche `develop`
* Branches `feature/*`

### 7.2 Commits

* Commits atomiques
* Messages explicites

---

## 8. Tests et validation

### 8.1 Tests unitaires (logiques)

* Fonctions de calcul
* Gestion des seuils

### 8.2 Tests fonctionnels

* Communication série stable
* Acquisition capteurs fiable

### 8.3 Critères de validation

Le projet est validé si :

* Le système fonctionne en continu 24h
* Les alertes sont fiables
* Le code est lisible et maintenable

---

## 9. Évolutions possibles (bonus)

* EEPROM pour stockage configuration
* Protocole série structuré
* RTOS (FreeRTOS)
* Bootloader personnalisé

---

## 10. Niveau de difficulté

* Niveau : **Intermédiaire → Avancé (embarqué)**
* Durée estimée : 4 à 8 semaines

---

**Fin du cahier des charges**
