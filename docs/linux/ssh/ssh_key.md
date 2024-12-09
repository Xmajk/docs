# SSH_key

1. KLíč na klientovi
Nejdříve si vytvořte na PC ze kterého se chcete připojit na ssh klíč pomocí příkazu:
```
ssh-keygen
```

>[!IMPORTANT]
>Tento klíč najdete na cestě:
>[cesta ke složce uživatele]/.ssh/id_rsa.pub

2. Soubor s klíči na SSH serveru:

>[!IMPORTANT]
>Vytvořte složku .ssh ve složce uživatele

Ve složce .ssh vytvořte soubor authorized_keys a do něj vložit klíč z počítače