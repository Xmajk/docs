# Záloha 

Záloha se vytváři pomocí mysqldump

Tento příkaz požádá o heslo.
```
mysqldump -u root -p nazev_databaze > backup.sql
```

## Skript pro automatizování záloh

```
#!/bin/bash

# Nastavte proměnné pro přihlášení k databázi
DB_USER="your_db_user"
DB_PASS="your_db_password"
DB_NAME="your_db_name"

# Název souboru pro zálohu dat
BACKUP_FILE="data_backup_$(date +\%Y\%m\%d\%H\%M\%S).sql"

# Cesta k adresáři, kde budou uloženy zálohy
BACKUP_DIR="/path/to/backup/directory"

# Vytvořte zálohu dat bez struktury tabulek
mysqldump -u $DB_USER -p$DB_PASS --no-create-info $DB_NAME > $BACKUP_DIR/$BACKUP_FILE

# Zpracujte chyby, pokud mysqldump selže
if [ $? -eq 0 ]; then
  echo "Záloha byla úspěšně vytvořena v $BACKUP_DIR/$BACKUP_FILE"
else
  echo "Chyba při vytváření zálohy"
fi
```

Po vytvoření automatizované zálohy musím nastavit práva: 
```
chmod +x backup_database.sh
```

Spuštění:
```
./backup_database.sh
```
