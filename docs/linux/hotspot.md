# Nastavení hotspotu

1. Zkontrolujte, zda máte nainstalovaný balíček hostapd. Pokud jej nemáte nainstalovaný, můžete ho nainstalovat pomocí následujícího příkazu:
```
sudo apt-get install hostapd
```

2. Nyní vytvořte konfigurační soubor pro hotspot. Můžete to udělat v terminálu, například takto:
```
sudo nano /etc/hostapd/hostapd.conf
```

3. V editoru nano můžete zadat následující konfiguraci pro váš hotspot:
```
interface=wlan0
driver=nl80211
ssid=NÁZEV_HOTSPOTU
hw_mode=g
channel=CHISLO
wmm_enabled=0
macaddr_acl=0
auth_algs=1
ignore_broadcast_ssid=0
wpa=2
wpa_passphrase=HESLO_PRO_HOTSPOT
wpa_key_mgmt=WPA-PSK
wpa_pairwise=TKIP
rsn_pairwise=CCMP
```
__interface__ - Určuje jméno vašeho bezdrátového adaptéru. Můžete zjistit jméno vašeho adaptéru pomocí příkazu ifconfig.

__ssid__ - Zde zadejte název vašeho hotspotu.

__channel__ - Určuje kanál, na kterém bude hotspot vysílat.

__wpa_passphrase__ - Zadejte heslo, které budou uživatelé potřebovat k připojení k hotspotu.

4. Uložte soubor a zavřete editor.

5. Nyní spusťte hotspot pomocí příkazu:
```
sudo hostapd /etc/hostapd/hostapd.conf
```

6. Hotspot by měl být nyní aktivní, a uživatelé by se měli moci k němu připojit se zadaným heslem.

7. Když budete chtít hotspot vypnout, stačí zavřít terminál, ve kterém je spuštěný proces hostapd.

## Nastavení aby se spouštěl po bootu

1. Vytvořte systemd službu pro váš hotspot. Otevřete terminál a použijte editor, například nano, k vytvoření nového souboru pro službu:
```
sudo nano /etc/systemd/system/hotspot.service
```

2. Do souboru hotspot.service vložte následující obsah:
```
[Unit]
Description=Hotspot Service
After=network.target

[Service]
ExecStart=/usr/sbin/hostapd /etc/hostapd/hostapd.conf
Restart=on-failure
RestartSec=5

[Install]
WantedBy=multi-user.target
```
Tento konfigurační soubor říká systemd, jak spustit a spravovat vaši službu hotspotu.

3. Uložte soubor a zavřete editor.

4. Aktivujte službu, aby se spouštěla při startu systému:
```
sudo systemctl enable hotspot.service
```

5. Spusťte službu:
```
sudo systemctl start hotspot.service
```