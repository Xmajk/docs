# SSH_port
Popis pro otevření ssh na portu.

## Pokus jedna
>[!IMPORTANT]
>Toto řešení mi nefunguje!!!
1. Upravte konfigurační soubor SSH:
Otevřete konfigurační soubor SSH na vašem serveru. Většinou se nachází v /etc/ssh/sshd_config. Můžete ho otevřít pomocí textového editoru jako je nano nebo vim. Například:
```
sudo nano /etc/ssh/sshd_config
```

2. Nastavte porty SSH:
V konfiguračním souboru naleznete řádek, který obsahuje nastavení portu SSH. Výchozí port je 22. Chcete-li přidat další port (například port 6969), přidejte novou řádku s nastavením portu. Například:
```
Port 22
Port 6969
```
Ujistěte se, že máte povolené potřebné porty ve firewallu (například UFW) a v případě, že používáte cloudový poskytovatel, povolte tyto porty i v jeho konzoli nebo panelu.

3. Restartujte SSH službu:
Po provedení změn v konfiguračním souboru je třeba restartovat SSH službu, aby se změny projevily. Použijte následující příkaz:
```
sudo service ssh restart
```

4. Ověřte, že SSH poslouchá na obou portech:
Můžete ověřit, zda SSH poslouchá na obou portech, pomocí následujícího příkazu:
```
sudo ss -tuln
```
Měli byste vidět výstup s dvěma řádky, které ukazují, že SSH poslouchá na portech 22 a 6969.

## Pokus dva
>[!IMPORTANT]
>Toto řešení už funguje!!!
>Jelikož do SSH zasahuje i socket, tak musíme přizpůsobit socket

1. Pro jistotu napsat port do sshd config (první pokus)

2. Do souboru na cestě "/etc/systemd/system/ssh.socket.d" vložit:
ListenStream, který je prázdný je myšlen 22
```
cat >/etc/systemd/system/ssh.socket.d/listen.conf <<EOF
[Socket]
ListenStream=
ListenStream=[port]
EOF
```

3. Reload démona
```
sudo systemctl daemon-reload
```

4. Restartovat službu
```
sudo systemctl restart ssh.socket
```

5. Potom je potřeba na PC (win) restarovat ssh-key 
[adresa rpi] = adresa vašeho rpi 
[port] = port ssh 
```
ssh-keygen -R [[adresa rpi]]:[port]
```