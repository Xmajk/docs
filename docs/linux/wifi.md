# Wifi

1. Připojení Wi-Fi adaptéru: 
Ujisti se, že máš k dispozici Wi-Fi adaptér, který je kompatibilní s Raspberry Pi a Ubuntu Server. Pokud používáš Raspberry Pi 3 nebo novější, měl by mít vestavěnou Wi-Fi, ale u starších modelů budeš potřebovat externí adaptér.

2. Nastavení Wi-Fi sítě: 
Otevři terminál na Raspberry Pi a uprav konfigurační soubor pro Wi-Fi. Nejběžnější způsob, jak to udělat, je pomocí nástroje netplan. Použij následující příkaz pro úpravu konfiguračního souboru:
```
sudo nano /etc/netplan/50-cloud-init.yaml
```
Tento příkaz otevře textový editor nano a zobrazí konfigurační soubor. Přidej následující blok do konfigurace:
```
network:
  version: 2
  ethernets:
    eth0:
      dhcp4: true
      optional: true
  wifis:
    wlan0:
      dhcp4: true
      optional: true
      access-points:
        "NÁZEV_SÍTĚ":
          password: "HESLO"
```

Nahraď "NÁZEV_SÍTĚ" názvem Wi-Fi sítě, ke které se chceš připojit, a "HESLO" heslem této sítě.

4. Uložení a ukončení editoru: Po úpravě konfiguračního souboru stiskni Ctrl+O pro uložení změn a poté Ctrl+X pro ukončení editoru.

5. Aplikace konfigurace: Aktualizuj konfiguraci sítě pomocí následujícího příkazu:
```
sudo netplan apply
```

5. Restart Raspberry Pi: Než se změny projeví, může být nutné restartovat Raspberry Pi:
```
sudo reboot
```

6. Jestli to nebude fungovat, může pomoct:
```
chmod 600 /etc/netplan/your_config_file.yaml
```

## Nastavení statické ip

1. Přejdete do stejného souboru a vložte konfiguraci
```
network:
    ethernets:
        eth0:
            dhcp4: true
            optional: true
    version: 2
    wifis:
      wlan0:
        dhcp4: no
        addresses:
         - ADRESA_SÍTĚ/MASKA_SÍTĚ
        gateway4: ADRESA_DG
        nameservers:
         addresses: [DNS1, DNS2]
        access-points:
          "NÁZEV_SÍTĚ":
            password: "HESLO"
``` 

2. Zrestartujte netplan
```
sudo netplan apply
```