1. Připojte se ke svému serveru přes SSH a otevřete soubor /etc/ssh/sshd_config ve vašem oblíbeném textovém editoru s administrátorskými právy. Například můžete použít příkaz sudo nano /etc/ssh/sshd_config.

2. V souboru sshd_config hledejte nebo přidejte následující řádek:
```
Banner /cesta/k/vasi/zprave
```
Místo /cesta/k/vasi/zprave nahraďte skutečnou cestou k souboru, který obsahuje vaši zprávu. Tento soubor může obsahovat textovou zprávu, kterou chcete zobrazit před zadáním hesla.

3. Uložte změny a zavřete editor.

4. Restartujte SSH službu, aby se změny projevily. Použijte následující příkaz:
```
sudo systemctl restart ssh
```
nebo
```
sudo service ssh restart
```
Nyní, když se připojíte k serveru pomocí SSH, uvidíte vaši zprávu před tím, než budete požádáni o zadání hesla. Tato zpráva může sloužit k různým účelům, například k informování uživatelů o pravidlech a pokynech pro připojení.