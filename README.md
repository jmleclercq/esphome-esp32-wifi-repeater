# Esp32_Wifi_Router
Paramétrage d'un ESP32-C6 pour en faire un point d'accès Wifi


Matériel nécessaire
    - Un ESP32 C6 
    - Un cable USBC qui permet le transport de données
    - Une alimentation 5V - 2A

Mise en place
     🚀 Identification du port série utilisé par le module ESP

    Il faut identifier sur quel port l'ESP se connecte. Pour cela lancer la commande (SANS BRANCHER l'ESP)
    ls /dev/ttyACM*
    Vous devriez voir les ports série présents. 
    Ensuite vous branchez l'ESP et retapez la commande
    ls /dev/ttyACM*
    👉 Le nouveau port apparu = ton ESP32.


    🚀 Test de la communication

    esptool.py --port /dev/ttyACM0 chip_id (remplace par le bon port)

    Si ça répond avec un Chip ID → tout est parfait côté système.

 🚀 Installer le bin
    Il ne reste plus qu'à flasher la carte avec le bon binaire. Tu le trouve ici :

    ## Flashing the prebuild binaries
- Download [latest release](https://github.com/dchristl/esp32_nat_router_extended/releases/latest)
  * Download esp32nat_extended_full_vX.X.X.zip for fresh install
  * Download esp32nat_extended_update_vX.X.X.zip for update

et le code pour flasher, en remplaçant par le bon numéro de port

    esptool --chip esp32c6 --port /dev/ttyACM7 write_flash 0x0 esp32nat_extended_full_vX.X.X.bin