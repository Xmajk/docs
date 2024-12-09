# Použití argumentů při spuštění a kontrola procesu
Můžeš spustit každý Node.js proces s vlastním argumentem, který bude specifický pro každý bot, a pak můžeš tento argument vyhledat pomocí příkazu ps.

```bash
nohup node bot1/index.js --name=bot1 &
nohup node bot2/index.js --name=bot2 &
```

Pak můžeš zjistit, který proces patří ke kterému botovi pomocí příkazu:

```bash
ps aux | grep node
```

Tímto způsobem uvidíš něco jako:
```bash
user   1234  1.0  1.0 123456 23456 pts/0    S    13:37   0:00 node bot1/index.js --name=bot1
user   1235  1.0  1.0 123456 23456 pts/0    S    13:37   0:00 node bot2/index.js --name=bot2
```
Zde vidíš PID (process ID) každého procesu a můžeš podle argumentu zjistit, který patří kterému botovi.