# Avahi
Avahi je implementace tzv. zeroconf, což je podle Wikipedie technika, díky které se počítače na lokální síti sami domluví tak, aby mezi sebou mohli komunikovat. 

## Princip
Ve světě Applu a Linuxu, resp. Avahi, se o tu nejdůležitější část fungování zeroconf stará mDNS (Multicast DNS) a DNS-SD (DNS Service Discovery). Protokol mDNS se od DNS moc neliší, používá také A/AAAA/SRV záznamy a největším rozdílem je způsob komunikace, která probíhá přes multicast. Když chce nějaký počítač zjistit IP na doméně „foo.local“, pošle na adresu 224.0.0.251 nebo FF02::FB v případě IPv6, dotaz, který přijde všem počítačům na lokální podsíti. Když toto jméno patří některému z nich, odpoví a adresa je na světě. Multicast dotazy lze rozesílat i mezi více podsítěmi, takže můžete mít třeba jinou podsíť na WiFi a jinou na kabel a pořád vám bude Avahi fungovat. Podmínkou je podpora na routeru.

## Instalace a konfigurace

1. Nainstalovat pomocí příkazu:
```
sudo apt install avahi-daemon
```

2. Konfigurace: 
```
sudo nano /etc/avahi/avahi-daemon.conf
```

Na nastavení domény na server.local
```
[server]
host-name=server
domain-name=local
```

>[!IMPORTANT]
>musím nastavit i inteface, na kterém je server napojen

3. Restartování avahi:
```
sudo systemctl restart avahi-daemon
```

4. Testování:
Nyní můžete otestovat, zda funguje doména "server.local". 
Použijte nástroj avahi-resolve-host-name k tomu:
```
avahi-resolve-host-name server.local
```