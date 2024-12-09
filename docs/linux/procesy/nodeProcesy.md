# Použití pm2 pro správu procesů
Můžeš také použít nástroj jako je pm2, který je specificky navržen pro správu Node.js aplikací. pm2 ti umožní jednoduše spravovat a monitorovat Node.js aplikace, a automaticky jim přiřazuje jména, která si můžeš určit.

Instalace pm2:
```bash
npm install -g pm2
```

Spuštění botů s pm2:
```bash
pm2 start bot1/index.js --name "bot1"
pm2 start bot2/index.js --name "bot2"
```

Tímto způsobem můžeš pomocí příkazu pm2 status snadno zjistit, který proces patří ke kterému botovi:
```bash
pm2 status
```

Výstup bude něco jako:
```bash
┌──────┬─────┬──────┬──────┬────────┬─────────┬──────┬───────────┬────────┬──────────┐
│ Name │ id  │ mode │ status│ cpu    │ mem     │ user │ watching  │ uptime │ restarted│
├──────┼─────┼──────┼──────┼────────┼─────────┼──────┼───────────┼────────┼──────────┤
│ bot1 │ 0   │ fork │ online│ 0.1%   │ 25.2MB  │ user │ disabled  │ 3m     │ 0        │
│ bot2 │ 1   │ fork │ online│ 0.1%   │ 25.3MB  │ user │ disabled  │ 3m     │ 0        │
└──────┴─────┴──────┴──────┴────────┴─────────┴──────┴───────────┴────────┴──────────┘
```