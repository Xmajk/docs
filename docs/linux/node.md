# Instalace Node a NMP

1. Příkaz na instalaci Node.js:
```
sudo apt install nodejs
```

2. Příkaz pro instalaci NPM:
```
sudo apt install npm
```

Získání informací o verzích:
```
michal@michal-desktop:~/share$ node -v
v18.13.0
michal@michal-desktop:~/share$ npm -v
9.2.0
```

# Nová instalace
Zjistil jsem že předešlí způsob neinstaluje aktuální verzi, tutdíž ji musíme nainstalovat ručně přes bin soubor

1. Stáhneme binárku podle architekry [zde](https://nodejs.org/en/download/prebuilt-binaries)

2. vytvořím dir /usr/local/lib/nodejs

3. rozbalím do directory stáhnutý soubor pomocí příkazu

```bash
sudo tar -xJvf <název souboru> -C /usr/local/lib/nodejs
```

4. do souboru .profile (v adresáři usera) vložím toto

```bash
nano ~/.profile
```

```bash
#Nodejs
export PATH=/usr/local/lib/nodejs/<název souboru>/bin:$PATH
```

>[!important]
>node nastavuji pro konkréítního uživatele, pro ostatní si to musí dát do svých .profile souborů

5. restartovat .profil soubor 

```bash
. ~/.profile
```

6. můžeme zkusit node a npm
```bash
node -v
npm -v
```

# Nová instalace (funguje)

Steps to download and install node in ubuntu

1. Step 1: Download latest or recommended node .tar.xz file from https://nodejs.org/en/

or you can download node version 14.15.5 (.tar.xz file) directly from here ->

https://nodejs.org/dist/v14.15.5/node-v14.15.5-linux-x64.tar.xz

2. Step 2: Go to the directory in which (.tar.xz file) is downloaded.

In my case --> /Download directory

3. Step 3: Update System Repositories

sudo apt update

4. Step 4: Install the package xz-utils

sudo apt install xz-utils

5. Step 5: To Extract the .tar.xz file

sudo tar -xvf name_of_file

In my case --> sudo tar -xvf node-v14.15.5-linux-x64.tar.xz

6. Step 6: sudo cp -r directory_name/{bin,include,lib,share} /usr/

In my case --> sudo cp -r node-v14.15.5-linux-x64/{bin,include,lib,share} /usr/

7. Step 7: Check the node version

node --version

Result In my case -> v14.15.5