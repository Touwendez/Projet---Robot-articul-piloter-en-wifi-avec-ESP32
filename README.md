# Projet — Robot articulé en bois piloté en Wi-Fi (ESP32)

Ce dépôt présente un **robot articulé** réalisé à partir de **feuilles de bois découpées** et assemblées, animé par des **servomoteurs** et piloté par un **ESP32**.  
Le contrôle se fait en **Wi-Fi** depuis un **téléphone**, via une interface simple de type **pad directionnel** (touches haut / bas / gauche / droite), permettant de commander les mouvements du robot en temps réel.

---

## Sommaire
- [Contexte](#contexte)
- [Objectifs](#objectifs)
- [Fonctionnalités](#fonctionnalités)
- [Stack](#stack)
- [Compétences développées](#compétences-développées)
- [Architecture](#architecture)
- [Pipeline de commande](#pipeline-de-commande)
- [Campagne de tests et réglages](#campagne-de-tests-et-réglages)
- [Optimisations et robustesse](#optimisations-et-robustesse)
- [Utilisation](#utilisation)
- [Arborescence](#arborescence)
- [Résultats](#résultats)
- [Limites et améliorations](#limites-et-améliorations)
- [Aperçu visuel](#aperçu-visuel)
- [Vidéos](#vidéos)
- [Confidentialité](#confidentialité)

---

## Contexte
L’objectif du projet est de concevoir un robot simple, pédagogique et évolutif, combinant :
- une **structure mécanique légère** (bois articulé),
- une **commande embarquée** (ESP32),
- une **interaction utilisateur** via un smartphone (contrôle Wi-Fi).

Ce type de base est idéal pour apprendre l’intégration **mécanique + électronique + logiciel** : articulation, servos, alimentation, communication réseau et logique de commande.

---

## Objectifs
- Concevoir une structure **articulée** en bois avec des degrés de liberté exploitables.
- Piloter les articulations via des **servomoteurs** (angles, positions, mouvements).
- Mettre en place une communication **Wi-Fi** entre un téléphone et l’ESP32.
- Offrir un contrôle simple et réactif via un **pad directionnel**.
- Assurer des mouvements stables (limites d’angle, lissage, sécurité).

---

## Fonctionnalités
- Robot articulé en bois (assemblage, articulations, support servos)
- Contrôle des servomoteurs :
  - positions/angles prédéfinis,
  - mouvements directionnels (ex : avancer / reculer / tourner)
- Connexion Wi-Fi (ESP32 ↔ smartphone)
- Interface de contrôle depuis le téléphone :
  - boutons directionnels (haut/bas/gauche/droite)
  - bouton stop / reset (si implémenté)
- Gestion sécurité :
  - limites d’angles (min/max),
  - position neutre (home),
  - arrêt des mouvements si perte de commande (timeout)

---

## Stack
- **ESP32** (Wi-Fi)
- **Servomoteurs** (PWM)
- Structure : **feuilles de bois** + articulation mécanique
- Programmation : Arduino / C++ (ESP32)
- Contrôle : interface web mobile ou appli simple (selon implémentation)

---

## Compétences développées
- **Systèmes embarqués** : ESP32, programmation microcontrôleur (Arduino/C++)
- **Communication réseau** : Wi-Fi (connexion, échanges de commandes, latence)
- **Commande d’actionneurs** : pilotage PWM de servomoteurs, calibration, limites
- **Intégration mécatronique** : assemblage mécanique + électronique + logiciel
- **Conception / prototypage** : structure bois articulée, placement servos, contraintes mécaniques
- **Tests & mise au point** : réglages d’angles, stabilité, scénarios d’usage, robustesse
- **Bonnes pratiques** : sécurité (timeout), comportement fail-safe, documentation projet



https://github.com/user-attachments/assets/fd73c500-2882-43b3-ba42-774bb391b8b3



---

## Architecture

```mermaid
flowchart LR
  A[Telephone - Interface directionnelle] -->|Wi-Fi| B[ESP32]
  B --> C[Controle PWM servomoteurs]
  C --> D[Robot articule en bois]
  B --> E[Logique commande: limites, home, timeout]
  E --> C

