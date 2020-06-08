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

database_host (localhost): mariadb
database_port (3306): 3306
database_name (shp_dmo61): database
database_user (shp_dmo61): user
database_password (insert-password): pass
```

5. Open  your Chameleon via http://localhost in your browser
```bash
enjoy
```
