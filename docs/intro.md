---
sidebar_position: 1
---

# Introduction

## 🔍 Qu’est-ce que la plateforme **Arduino** ?

Arduino est une **plateforme de prototypage électronique** qui permet de créer facilement des objets interactifs. Elle est conçue pour être **simple à utiliser**, même pour ceux qui n’ont jamais fait d’électronique ou de programmation.

---

## 🧠 Les trois piliers d’Arduino

### 1. 🟦 **La carte Arduino (le matériel)**
La carte Arduino est une **petite carte électronique** qui contient un **microcontrôleur** (un mini-ordinateur). 

Elle peut :
- Lire des **informations** venant de capteurs (température, lumière, boutons…),
- Prendre des **décisions** grâce à un programme,
- Et **agir** sur le monde extérieur (allumer une LED, faire tourner un moteur, afficher un message…).

👉 La plus connue est la **carte Arduino UNO**, idéale pour débuter.

![Arduino Uno R3](/img/Arduino_Uno_-_R3.jpg "Arduino Uno R3")


### 2. 💻 **L’environnement de programmation (le logiciel)**
Pour dire à la carte quoi faire, on écrit un **programme** (appelé *sketch*) dans un langage proche du **C/C++**. On utilise pour cela :
- Le **logiciel Arduino IDE**,
- Qui permet d’**écrire**, **vérifier** et **envoyer** le programme vers la carte.

### 3. 🔌 **Les composants électroniques**
La carte seule ne fait rien. On y connecte des **composants** :
- **Entrées** : boutons, capteurs, potentiomètres…
- **Sorties** : LED, afficheurs, moteurs, buzzers…

Ces composants sont branchés sur les **broches** de la carte via des **câbles** et une **breadboard** (plaque d’essai sans soudure).

---

## 🧩 Comment ça fonctionne ?

1. **On écrit un programme** sur l’ordinateur (ex. : “si on appuie sur le bouton, allumer la LED”).
2. **On envoie ce programme** à la carte via un câble USB.
3. **La carte exécute le programme** en temps réel, en interagissant avec les composants.

---

## 🛠️ Exemple simple : Allumer une LED

- **Composants** : une LED, une résistance, des fils.
- **Code** :
```cpp
void setup() {
  pinMode(13, OUTPUT); // La broche 13 est une sortie
}

void loop() {
  digitalWrite(13, HIGH); // Allume la LED
  delay(1000);            // Attend 1 seconde
  digitalWrite(13, LOW);  // Éteint la LED
  delay(1000);            // Attend 1 seconde
}
```

---

## 🎓 Pourquoi c’est génial ?

- **Accessible** : pas besoin d’être expert en électronique ou en code.
- **Concret** : on voit immédiatement le résultat de ce qu’on programme.
- **Créatif** : on peut inventer des jeux, des objets utiles, des expériences scientifiques…
- **Interdisciplinaire** : lien avec la physique, la technologie, les mathématiques, l’informatique.

