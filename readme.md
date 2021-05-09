# Requirements

+ PHP 7.4 with following extensions: tidy, curl
+ composer

# How to Install

1. Clone the Project

```bash
git clone https://github.com/kzorluoglu/chameleon-docker.git
```

2. Clone the Chameleon Project under *chameleon-docker*

```bash
 cd chameleon-docker
 git clone https://github.com/chameleon-system/chameleon-system.git
```

3. Run docker-compose

```bash
docker-compose up -d #-d run in to the background
```

4. Run composer install in Chameleon Project

```bash
cd chameleon-system
composer install
```

5. Open your Chameleon via http://localhost in your browser

```bash
enjoy
```

# phpMyAdmin

via `http://localhost:8080` , Username: **`root`**, Password : **`root`**

# Debug

## Xdebug

1. Change the **YOURDOCKERIPADRESSE** and **YOURIDEKEY** placeholders with yours in **/docker/php/php.ini**

```bash
xdebug...
xdebug.remote_host=YOURDOCKERIPADRESSE
xdebug.idekey=YOURIDEKEY
xdebug...
```

2. And Configure your IDE with idekey and remote_host configurations.
3. Enjoj

## Xdebug with VSCode

1. Install [PHP Debug](https://marketplace.visualstudio.com/items?itemName=felixfbecker.php-debug) Extension
2. Replace your **YOURIDEKEY** with **VSCODE** in **/docker/phpphp.ini**

```
xdebug.remote_host=YOURDOCKERIPADRESS
xdebug.idekey=VSCODE
```

3. Create .vscode/launch.json manually or Create over Run Panel
4. Replace your launch.json

```json
{
  "version": "0.2.0",
  "configurations": [
    {
      "name": "Listen for XDebug",
      "type": "php",
      "request": "launch",
      "port": 9000,
      "pathMappings": {
        "/var/www/html": "${workspaceFolder}/chameleon-system"
      }
    }
  ]
}
```

5. Enjoj