# Hostname

1. Nejprve změňte hostname na "mojerpi" pomocí následujícího příkazu:
```
sudo hostnamectl set-hostname mojerpi
```

2. Upravte soubor __/etc/hosts__ s oprávněním administrátora:
```
sudo nano /etc/hosts
```

3. Přidejte následující řádek na konec souboru:
```
127.0.0.1       mojerpi.local
```
Uložte soubor a rebootujte.
