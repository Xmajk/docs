# Instalace MySQL
1. nainstalujte __MySQL__
```
sudo apt install mysql-server
```

2. startněte MySQL
Po dokončení instalace MySQL serveru spusťte službu a povolte jej automatické spuštění po startu systému:
```
sudo systemctl start mysql
```

3. enable MySQL
```
sudo systemctl enable mysql
```

na roota se pze přihlásit pomocí:
```
mysql -u root -p
```

4. Pokud jste při instalaci nezadali heslo na roota, tak je stejné jako uživatele, který instaloval MySQL

5. Přes SSH tunnel se nejde připojit na roota, tak standartně vytvořte nového uživatele
```
CREATE USER 'nový_uživatel'@'localhost' IDENTIFIED BY 'nové_heslo';
GRANT ALL PRIVILEGES ON *.* TO 'nový_uživatel'@'localhost' WITH GRANT OPTION;
FLUSH PRIVILEGES;
```