# Static-jinja-plus

Образ генератора статических сайтов на основе [StaticJingaPlus](https://github.com/MrDave/StaticJinjaPlus)

## Запуск контейнера

1.В репозитории доступны несколько образов на базе Ubuntu и на базе python:3.12-slim. Можно скачать релизнутую сборку или самую свежую сборку не попавшую в релиз. Выбирите наиболее подходящий docker-образ и скачайте его, предварительно установив тэг `$TAG`:

```
docker pull juneshone/static-jinja-plus:$TAG
```

2.Убедитесь, что образ докер-контейнера скачан:

```
docker images juneshone/static-jinja-plus:$TAG
```

3.На локальной машине создайте два каталога: первый `<./PATH/TO/TEMPLATES/FOLDER>` с набором шаблонов для StaticJinjaPlus, а второй `<./PATH/TO/BUILD/FOLDER>` для размещения результатов сборки. Чтобы использовать ресурсы, такие как .css и .js, создайте дополнительный подкаталог assets внутри каталога с набором ваших шаблонов (./templates/assets по умолчанию). В этом случае StaticJinjaPlus скопирует ресурсы в выходную папку, сохраняя те же относительные пути. Вы можете ознакомиться с примерами шаблонов в репозитории [StaticJingaPlus](https://github.com/MrDave/StaticJinjaPlus).

Для рендеринга файлов выполните следующую команду:

```
docker run --rm -v <./PATH/TO/TEMPLATES/FOLDER>:/opt/StaticJinjaPlus/templates/ -v <./PATH/TO/BUILD/FOLDER>:/opt/StaticJinjaPlus/build/ juneshone/static-jinja-plus:$TAG
```
  
Пример команды:

```
docker run --rm -v ./templates:/opt/StaticJinjaPlus/templates/ -v ./build/site:/opt/StaticJinjaPlus/build/ juneshone/static-jinja-plus:latest
```

После успешного запуска контейнера файлы сборки появятся в указанной папке, а в консоли вы увидите сообщение о каждом шаблоне:

```
Rendering about.html...
Rendering assets/app.js...
Rendering assets/style.css...
Rendering faq.html...
Rendering index.html...
```

## Создание докер-образ на основе докер-контейнера:

Для создания докер-образа перейдите в каталог с нужной версией.
Получите хеш-сумму файлов репозитория [StaticJingaPlus](https://github.com/MrDave/StaticJinjaPlus) в командной оболочке, выполнив следующее:

- _версия 0.1.0_

```
curl -sL https://github.com/MrDave/StaticJinjaPlus/archive/refs/tags/0.1.0.tar.gz | sha256sum
```

- _версия 0.1.1(latest)_
```
curl -sL https://github.com/MrDave/StaticJinjaPlus/archive/refs/tags/0.1.1.tar.gz | sha256sum
```

### Создание докер-образ на базе Ubuntu:

- _версия latest_

```
docker build -t juneshone/static-jinja-plus:latest --build-arg HASH=30d9424df1eddb73912b0e2ad5375fa2c876c8e30906bec91952dfb75dcf220b --build-arg TAG=0.1.1 -f Dockerfile .
```

- _версия 0.1.1_

```
docker build -t juneshone/static-jinja-plus:0.1.1 --build-arg HASH=30d9424df1eddb73912b0e2ad5375fa2c876c8e30906bec91952dfb75dcf220b --build-arg TAG=0.1.1 -f Dockerfile .
```

- _версия 0.1.0_

```
docker build -t juneshone/static-jinja-plus:0.1.0 --build-arg HASH=3555bcfd670e134e8360ad934cb5bad1bbe2a7dad24ba7cafa0a3bb8b23c6444 --build-arg TAG=0.1.0 -f Dockerfile .
```

- _версия develop_

```
docker build -t juneshone/static-jinja-plus:develop -f Dockerfile .
```

### Создание докер-образ на базе Python-slim:

- _версия slim_

```
docker build -t juneshone/static-jinja-plus:slim --build-arg HASH=30d9424df1eddb73912b0e2ad5375fa2c876c8e30906bec91952dfb75dcf220b --build-arg TAG=0.1.1 -f Dockerfile .
```

- _версия 0.1.1_

```
docker build -t juneshone/static-jinja-plus:0.1.1-slim --build-arg HASH=30d9424df1eddb73912b0e2ad5375fa2c876c8e30906bec91952dfb75dcf220b --build-arg TAG=0.1.1 -f Dockerfile .
```

- _версия 0.1.0-slim_

```
docker build -t juneshone/static-jinja-plus:0.1.0-slim --build-arg HASH=3555bcfd670e134e8360ad934cb5bad1bbe2a7dad24ba7cafa0a3bb8b23c6444 --build-arg TAG=0.1.0 -f Dockerfile .
```

- _версия develop-slim_

```
docker build -t juneshone/static-jinja-plus:develop-slim -f Dockerfile .
```

## Цель проекта

Код написан в учебных целях — это урок в курсе по Python и веб-разработке на сайте [Devman](https://dvmn.org).