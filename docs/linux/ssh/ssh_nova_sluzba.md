# Vytvoření nové služby
[Výce na stackoverflow fóru](https://stackoverflow.com/questions/61443935/ssh-service-running-on-multiple-ports-with-custom-rules-in-linux)

1. Vytvořte kopii ssh konfigurace služby a pojmenujte si ji podle potřeby
```
cp /etc/ssh/sshd_config /etc/ssh/sshd_config_custom
```

2. Vytvořte kopii služby a pojmenujte ji podle potřeby
```
cp /lib/systemd/system/ssh.service /lib/systemd/system/sshd-custom.service
```

3. Otevřete "/lib/systemd/system/sshd-custom.service" a změňte
```
ExecStart=/usr/sbin/sshd -D $SSHD_OPTS
```
na
```
ExecStart=/usr/sbin/sshd -D $SSHD_OPTS -f /etc/ssh/sshd_config_custom
```

A ještě změnte
```
Alias=sshd.service
```
na
```
Alias=sshd-custom.service
```

4. Nyní můžete povolit a spustit alužbu
```
systemctl enable sshd-custom.service
systemctl start sshd-custom.service
```