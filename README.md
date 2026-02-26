# ESP32-C6 WiFi Router (NAT)

Configuration d’un **ESP32-C6** pour le transformer en **routeur WiFi avec NAT**.

Ce projet permet d’utiliser l’ESP32-C6 comme point d’accès WiFi capable de partager une connexion réseau.

---

## 📋 Table des matières

* [Présentation](#présentation)
* [Matériel requis](#matériel-requis)
* [Prérequis logiciel](#prérequis-logiciel)
* [Identification du port série](#identification-du-port-série)
* [Test de communication](#test-de-communication)
* [Installation du firmware](#installation-du-firmware)
* [Flash du firmware](#flash-du-firmware)
* [Résultat attendu](#résultat-attendu)
* [Dépannage](#dépannage)
* [Licence](#licence)

---

## 📖 Présentation

Ce projet utilise le firmware **esp32_nat_router_extended** pour transformer un ESP32-C6 en :

* Point d'accès WiFi
* Routeur NAT
* Extenseur de réseau léger
* Solution embarquée basse consommation

Firmware utilisé :
https://github.com/dchristl/esp32_nat_router_extended

---

## 🧰 Matériel requis

* ESP32-C6
* Câble USB-C compatible données
* Alimentation 5V – 2A
* Ordinateur sous Linux (ou compatible esptool)

---

## 💻 Prérequis logiciel

* Python 3
* esptool

Installation d’esptool si nécessaire :

```bash
pip install esptool
```

---

## 🔎 Identification du port série

### 1. Lister les ports disponibles (ESP débranché)

```bash
ls /dev/ttyACM*
```

### 2. Brancher l’ESP32-C6

Relancer la commande :

```bash
ls /dev/ttyACM*
```

👉 Le nouveau port détecté correspond à l’ESP32
Exemple : `/dev/ttyACM0`

---

## 🚀 Test de communication

```bash
esptool.py --port /dev/ttyACM0 chip_id
```

Remplacer le port par le vôtre.

Si un **Chip ID** est retourné, la communication fonctionne correctement.

---

## 📦 Installation du firmware

Télécharger la dernière version :

https://github.com/dchristl/esp32_nat_router_extended/releases/latest

### Choisir le bon fichier :

* `esp32nat_extended_full_vX.X.X.zip` → Installation complète
* `esp32nat_extended_update_vX.X.X.zip` → Mise à jour

Extraire le fichier `.bin` avant le flash.

---

## 🔥 Flash du firmware

```bash
esptool --chip esp32c6 --port /dev/ttyACM0 write_flash 0x0 esp32nat_extended_full_vX.X.X.bin
```

Adapter :

* Le port série
* Le nom exact du fichier `.bin`

---

## ✅ Résultat attendu

Après redémarrage :

* L’ESP32-C6 crée un point d’accès WiFi
* Connexion possible au réseau généré
* Interface d’administration accessible selon la configuration du firmware

---

## 🛠 Dépannage

### Permission refusée sur le port série

```bash
sudo usermod -a -G dialout $USER
```

Puis redémarrer la session.

### Aucun port détecté

* Vérifier que le câble USB supporte les données
* Tester un autre port USB
* Vérifier l’alimentation

---

## 📜 Licence

Ce projet repose sur le firmware développé par dchristl.
Merci de consulter le dépôt officiel pour les conditions de licence.

---

## 🤝 Contribution

Les contributions sont les bienvenues :

* Issues
* Pull requests
* Suggestions d’amélioration

---
