---
sidebar_position: 2
---

# Bien débuter

<!-- ## Démarrer l'IDE Arduino  -->

## 🖥️ __L'IDE__ (Environnement de Développement Intégré)

C'est le logiciel qui sert à écrire les programmes pour les carte Arduino, il permet également de téléverser le programme sur la carte et de suivre l'exécution du programme pour dépanner.

### Lancer l'application

![Open arduino IDE](/img/getting-started/open-ide.png "Open arduino IDE")

### Configurer la communication avec la carte

#### Ouvrir le configurateur de carte

![Card configuration](/img/getting-started/open-card-configuration.png "Card configuration")

#### Vérifier la configuration de la carte

![Configure card](/img/getting-started/configure-card.png "Configure card")


## 🧰 Premier programme

Ce premier programme va nous servir à valider que l'application et la carte fonctionne. Il est extrênement simple, il s'agit de faire clignoter la DEL intégrée à la carte.

Pour cela il nous faut saisir le programme suivant :

```cpp
// La fonction setup n'est applelée qu'une seule fois quand on allumer la carte ou que l'on appuoe sur reset
void setup() {
    // Initialiser la sortie digital LED_BUILTIN comme sortie.
    pinMode(LED_BUILTIN, OUTPUT);
}

// La function loop recommence indéfiniment
void loop() {
     digitalWrite(LED_BUILTIN, HIGH);   // Allumer la DEL (HIGH tension de la sortie)
     delay(1000);                       // Attendre 1 seconde
     digitalWrite(LED_BUILTIN, LOW);    // Eteindre la DEL
     delay(1000);                       // Attendre 1 seconde
 }

```

### Utilisation du moniteur série

Le moniteur série permet de faire communique la carte avec l'ordinateur pour afficher des textes.
Nous allons modifier le programme précédent pour ajouter cette fonction.

```cpp
// La fonction setup n'est applelée qu'une seule fois quand on allumer la carte ou que l'on appuoe sur reset
void setup() {
    // Initialisation du moniteur
    Serial.begin(9600);
    // Initialiser la sortie digital LED_BUILTIN comme sortie.
    pinMode(LED_BUILTIN, OUTPUT);
}

// La function loop recommence indéfiniment
void loop() {
    Serial.println("Jour");            // Envoi du message
    digitalWrite(LED_BUILTIN, HIGH);   // Allumer la DEL (HIGH tension de la sortie)
    delay(1000);                       // Attendre 1 seconde
    Serial.println("Nuit");            // Envoi du message
    digitalWrite(LED_BUILTIN, LOW);    // Eteindre la DEL
    delay(1000);                       // Attendre 1 seconde
 }

```

## 📚 Qu’est-ce qu’une bibliothèque Arduino ?

Une **bibliothèque Arduino** est un ensemble de **fichiers de code pré-écrits** qui permettent de **simplifier l’utilisation de composants ou de fonctions complexes**. Elle contient :
- Des **fonctions prêtes à l’emploi** (ex. : lire un capteur, afficher sur un écran),
- Des **définitions de variables et de constantes**,
- Et parfois des **exemples de code**.

---

### 🧠 Pourquoi utiliser des bibliothèques ?

#### ✅ **Faciliter la programmation**
Au lieu d’écrire tout le code soi-même, on utilise des fonctions déjà créées :
```cpp
// Sans bibliothèque
digitalWrite(pin, HIGH);

// Avec bibliothèque DHT
float temperature = dht.readTemperature();
```

#### ✅ **Gagner du temps**
Les bibliothèques sont **testées et fiables**, ce qui évite de réinventer la roue.

#### ✅ **Accéder à des composants avancés**
Certaines bibliothèques permettent de gérer :
- Des **capteurs complexes** (DHT22, MPU6050…),
- Des **écrans** (LCD, OLED, TFT…),
- Des **moteurs**, **cartes SD**, **modules Wi-Fi**, etc.

---

### 🛠️ Comment ajouter une bibliothèque dans l’IDE Arduino ?

<!-- 1. **Ouvrir l’IDE Arduino**
2. Aller dans **Croquis > Inclure une bibliothèque > Gérer les bibliothèques**
3. Rechercher le nom de la bibliothèque (ex. : `DHT`, `FastLED`)
4. Cliquer sur **Installer**

> 📦 Les bibliothèques sont téléchargées depuis le **gestionnaire de bibliothèques Arduino**, qui contient des milliers de ressources gratuites. -->


#### 📌 Étape 1 : Ouvrir l’IDE Arduino
Lance l’**IDE Arduino 2.3** sur ton ordinateur. Tu arrives sur l’interface principale avec un nouvel onglet de code.

---

#### 📌 Étape 2 : Ouvrir le gestionnaire de bibliothèques
1. Clique sur l’icône **"Bibliothèques"** dans la barre latérale gauche (📚).
2. Ou bien, va dans le menu **"Sketch" > "Include Library" > "Manage Libraries…"**.

---

#### 📌 Étape 3 : Rechercher une bibliothèque
Dans la fenêtre du **Library Manager** :
- Utilise la **barre de recherche** en haut à droite.
- Tape le nom de la bibliothèque que tu veux installer (ex. : `DHT`, `FastLED`, `LiquidCrystal_I2C`…).

---

#### 📌 Étape 4 : Installer la bibliothèque
- Une fois la bibliothèque trouvée, clique sur le bouton **"Install"** à droite.
- Attends quelques secondes que l’installation se termine.

> ✅ Une coche verte s’affiche une fois la bibliothèque installée.

---

#### 📌 Étape 5 : L’utiliser dans ton code
Tu peux maintenant inclure la bibliothèque dans ton programme avec :
```cpp
#include <NomDeLaBibliotheque.h>
```

Par exemple :
```cpp
#include <DHT.h>
```

---

#### 🧠 Astuce
Les bibliothèques sont téléchargées avec des exemples d'utilisation, il ne faut hésiter à les consulter pour voir l'ensemble des possibilités.

---

### 🧩 Exemple concret

#### 🔹 Sans bibliothèque
Lire un capteur DHT22 demanderait de gérer le protocole de communication soi-même (très complexe).

#### 🔹 Avec bibliothèque
```cpp
#include "DHT.h"
DHT dht(2, DHT22);
float t = dht.readTemperature();
```
➡️ En **une ligne**, on obtient la température !

---

### 🎓 En résumé

| Avantage | Description |
|---------|-------------|
| 🧠 Simplicité | Moins de code à écrire |
| ⏱️ Rapidité | Gain de temps pour les projets |
| 📦 Richesse | Accès à des composants avancés |
| 🧪 Fiabilité | Code testé par la communauté |

---
