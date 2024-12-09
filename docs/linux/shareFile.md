
1. Nainstalujte Samba na Ubuntu:
Otevřete terminál na vašem počítači s Ubuntu a spusťte následující příkaz k instalaci Samba:
```
sudo apt-get install samba
```

2. Nastavte sdílenou složku na Ubuntu:
Poté vytvořte složku, kterou chcete sdílet, a nastavte ji jako sdílenou složku Samba.
Například:
```
mkdir ~/sdilenaslozka
sudo nano /etc/samba/smb.conf
```

V souboru smb.conf přidejte následující konfigurační blok na konec souboru:
```
[SdilenaSlozka]
comment = Sdílená složka pro Windows
path = /home/tvoje-uzivatelske-jmeno/sdilenaslozka
browseable = yes
read only = no
guest ok = yes
```
Ujistěte se, že path odkazuje na cestu k vaší složce. Poté uložte a zavřete soubor.

3. Nastavte heslo pro uživatele Samba:
Nastavte heslo pro uživatele Samba (může být odlišné od vašeho uživatelského hesla). 
Spusťte tento příkaz:
```
sudo smbpasswd -a tvoje-uzivatelske-jmeno
```
Následně vám bude představeno nastavení hesla pro uživatele Samba.

4. Restartujte službu Samba:
Spusťte tento příkaz pro restartování Samba serveru:
```
sudo service smbd restart
```

5. Nastavení na Windows 11:
Na počítači s Windows 11 otevřete Průzkumník souborů. Poté klepněte na "Síť" v levém panelu. Měli byste vidět sdílenou složku z Ubuntu. Pokud ne, zkuste zadat \\ip-adresa-ubuntu do adresního řádku Průzkumníka souborů a stiskněte Enter. Zadáte-li heslo, které jste nastavili pro uživatele Samba, měli byste mít přístup k sdíleným souborům.

Nyní byste měli mít sdílenou složku mezi svými dvěma počítači, která umožňuje přístup a sdílení souborů v reálném čase.