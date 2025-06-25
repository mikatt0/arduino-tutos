---
sidebar_position: 3
---

# 🧊 DHT 22

### C'est chaud, c'est chaud !

## 🧪 **Mesurer la température et l’humidité avec un capteur DHT22**

### 🎯 Objectif
- Comprendre le fonctionnement d’un capteur numérique.
- Lire des données de température et d’humidité.
- Afficher les données dans le moniteur série de l’IDE Arduino.

---

### 🧰 Matériel nécessaire
| Composant | Quantité |
|----------|----------|
| Carte Arduino UNO | 1 |
| Capteur DHT22 | 1 |
| Résistance 10 kΩ | 1 |
| Câbles Dupont | Quelques-uns |
| Breadboard | 1 |

---

### 🔌 Câblage

| Broche DHT22 | Arduino UNO |
|--------------|-------------|
| VCC          | 5V          |
| DATA         | Pin 2       |
| GND          | GND         |

> 🔧 Utiliser une version du capteur qui comporte une **résistance de 10 kΩ** placée entre **VCC et DATA** (pull-up).

---

### 💻 Code Arduino

Avant de commencer, installe les bibliothèques nécessaires :
1. Ouvre l’IDE Arduino.
2. Va dans **Croquis > Inclure une bibliothèque > Gérer les bibliothèques**.
3. Recherche et installe :
   - **DHT sensor library** (par Adafruit)
   - **Adafruit Unified Sensor**

```cpp
#include "DHT.h"

#define DHTPIN 2       // Broche de données connectée au DHT22
#define DHTTYPE DHT22  // Type de capteur

DHT dht(DHTPIN, DHTTYPE);

void setup() {
  Serial.begin(9600);
  dht.begin();
  Serial.println("Capteur DHT22 prêt !");
}

void loop() {
  float temperature = dht.readTemperature();
  float humidite = dht.readHumidity();

  if (isnan(temperature) || isnan(humidite)) {
    Serial.println("Erreur de lecture du capteur !");
    return;
  }

  Serial.print("Température : ");
  Serial.print(temperature);
  Serial.println(" °C");

  Serial.print("Humidité : ");
  Serial.print(humidite);
  Serial.println(" %");

  delay(2000); // Attendre 2 secondes entre chaque mesure
}
```

---

### 🧠 Explication du code
- `dht.readTemperature()` : lit la température en degrés Celsius.
- `dht.readHumidity()` : lit le pourcentage d’humidité relative.
- Les données sont affichées dans le **moniteur série** toutes les 2 secondes.

---

### ✅ Vérification
- Ouvre le **moniteur série** dans l’IDE Arduino (Ctrl + Maj + M).
- Tu devrais voir les valeurs de température et d’humidité s’afficher régulièrement.

---

### 💻 Version alternative améliorée (sans `delay()`)

```cpp
#include "DHT.h"

#define DHTPIN 2       // Broche de données connectée au DHT22
#define DHTTYPE DHT22  // Type de capteur

DHT dht(DHTPIN, DHTTYPE);

unsigned long previousMillis = 0;      // Temps de la dernière lecture
const long interval = 2000;            // Intervalle entre les lectures (en ms)

void setup() {
  Serial.begin(9600);
  dht.begin();
  Serial.println("Capteur DHT22 prêt !");
}

void loop() {
  unsigned long currentMillis = millis();

  if (currentMillis - previousMillis >= interval) {
    previousMillis = currentMillis;

    float temperature = dht.readTemperature();
    float humidite = dht.readHumidity();

    if (isnan(temperature) || isnan(humidite)) {
      Serial.println("Erreur de lecture du capteur !");
      return;
    }

    Serial.print("Température : ");
    Serial.print(temperature);
    Serial.println(" °C");

    Serial.print("Humidité : ");
    Serial.print(humidite);
    Serial.println(" %");
  }

  // Ici, on peut ajouter d'autres actions sans être bloqué par delay()
}
```

---

### ✅ Avantages de cette version
- **Non bloquante** : le programme peut faire autre chose pendant l’attente.
- **Évolutive** : on peut facilement ajouter des capteurs, des animations LED, ou des interactions utilisateur.
- **Bonne pratique** : `millis()` est la méthode recommandée pour les projets complexes.

Souhaites-tu que je t’aide à intégrer un **affichage LCD** ou une **alerte visuelle** (LED, buzzer) en fonction des valeurs mesurées ?


### 🧩 Extensions possibles
- Afficher les données sur un écran LCD.
- Allumer une LED si la température dépasse un seuil.

### 🏷️ Todo
 - [Préparer une PCB avec la resistance et le condensateur pour faciliter le montage](https://passionelectronique.fr/tutorial-dht22/)


