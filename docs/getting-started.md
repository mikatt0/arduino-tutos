---
sidebar_position: 2
---

# Bien débuter

<!-- ## Démarrer l'IDE Arduino  -->

## 🖥️ L'IDE __(Environnement de Développement Intégré)__ 

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