# Проект второго семестра

Деплой в кластер Kubernetes приложения интернет-магазина «Сосисочная». 

## Описание

* В backend добавлены flyway-миграции БД
* Выполнена сборка Docker-образов приложений backend, frontend, backend-report с применением multi-stage
* Описан манифест для развертывания персистивной PostgreSQL в кластере
* Описаны манифесты для развертывания приложений frontend, backend-report, backend
* Описаны стратегии деплоя для бэкенда — RollingUpdate — и для backend-report — Recreate
* Реализованы VPA для backend и HPA для backend-report
* Добавлены liveness probe для бэкенда
* Автоматизировано создание БД и пользователя для отчетов в MongoDB

## Deploy

Отредактировать параметры в sausage-store-chart/values.yaml и выполнить:

`helm upgrade --install sausage sausage-store-chart/ --debug`

## Demo

Приложение доступно по адресу https://front-dedushkinv.2sem.students-projects.ru

# Sausage Store

![image](https://user-images.githubusercontent.com/9394918/121517767-69db8a80-c9f8-11eb-835a-e98ca07fd995.png)


## Technologies used

* Frontend – TypeScript, Angular.
* Backend  – Java 16, Spring Boot, Spring Data.
* Database – H2.

## Installation guide
### Backend

Install Java 16 and maven and run:

```bash
cd backend
mvn package
cd target
java -jar sausage-store-0.0.1-SNAPSHOT.jar
```

### Frontend

Install NodeJS and npm on your computer and run:

```bash
cd frontend
npm install
npm run build
npm install -g http-server
sudo http-server ./dist/frontend/ -p 80 --proxy http://localhost:8080
```

Then open your browser and go to [http://localhost](http://localhost)
