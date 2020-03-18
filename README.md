# LAM Docker Environment
This is a simple Laravel + Angular + MySQL environment based on [Docker](https://www.docker.com/).

## How to use
### Laravel
Put your Laravel Application inside the `LaraDock` folder, without the `/vendor/` folder.

### Angular
Put your Angular Application inside the `AnguDock` folder, withouth the `/node_modules/` folder.

### MySQL
Not so much to be done! Your DB data will be located at `MysqDock/db/` folder.

## Building
On the root folder, run:
```
docker-compose up --build -d
```

Three images will be created: LaraDock, AnguDock and MysqDock. 

MysqDock by default creates a database named `app`, with username `application` and password `devel`. Port `3306` is exposed. 

LaraDock will automaticaly be connected to this database and running on port `8000`, also exposed.

AnguDock will be running at the exposed port `4200`.