#Docker 

### FROM
`FROM <image>[:<tag>] [AS name] `

- используя AS можно задать имя, которое после можно использовать в Dockerfile как ссылку на версию(позволяет модифицировать образ поэтапно)
```Docker
FROM httpd:alpine AS base
COPY ./html/ /usr/local/apache2/htdocs/

FROM base AS publish
````

### ARG
```Docker
ARG VERSION=latest
FROM busybox:$VERSION
ARG VERSION
RUN echo $VERSION > image_version
````

Переменная объявленная до FROM может быть использована только вместе с FROM, но не после него. 
Чтобы достать значение из переменной вне FROM, можно объявить ее еще раз и присвоить ей значение

### COPY
`COPY <src directory> <dest directory>`
*Скопировать все из src в dest

В документации есть разные способы использования COPY. Пример:
 `COPY hom* /mydir/` - скопировать все файлы начинающиеся на `hom`

Атрибут --from:
```Docker
FROM httpd:alpine AS base
COPY ./html/ /usr/local/apache2/htdocs/

FROM base AS final
COPY --from=base  /usr/local/apache2/htdocs/ /app/
````
*Скопировать из base [путь до файлов] в /app/

### WORKDIR

Задает рабочую диреткторию внутри контейнера(ту с которой стартуем контейнер)
```Docker
FROM httpd:alpine AS base
WORKDIR /usr/local/apache2/htdocs/
COPY ./html/ .
````

WORKDIR будет самостоятельно создавать директории, которых не хватает

### EXPOSE
`EXPOSE <port>`

```Docker
FROM httpd:alpine AS base
WORKDIR /usr/local/apache2/htdocs/
EXPOSE 80
EXPOSE 443
COPY ./html/ .
````

Контейнер слушает на портах 80 и 443 (-p 8080:80 - мапит порты)

### RUN

Позволяет делать вызов Shell команды внутри image 
Чаще всего используется для установки нужных пакетов внутрь контейнера.
`RUN` создаёт слой во время запуска. Docker фиксирует состояние образа после каждой инструкции `RUN`

```Docker
FROM httpd:alpine AS base
WORKDIR /usr/local/apache2/htdocs/
EXPOSE 80
EXPOSE 443
COPY ./html/ .
RUN dotnet build "csproj file"
````
*Соберет проект сразу после инициализации контейнера

### CMD

`CMD` — инструкция для запуска чего-либо во время запуска самого контейнера. По ходу сборки она не фиксирует никакого результата. Может быть только одна
Например запустим скрипт `my_script.py`.
```Docker
FROM python:3.7.2-alpine3.8
LABEL maintainer="jeffmshale@gmail.com"
ENV ADMIN="jeff"

RUN apk update && apk upgrade && apk add bash

COPY . ./app

ADD https://raw.githubusercontent.com/discdiver/pachy-vid/master/sample_vids/vid1.mp4 \
/my_app_directory

RUN ["mkdir", "/a_directory"]

CMD ["python", "./my_script.py"]
```
### VOLUME
`VOLUME ["/data"]`

Указывается путь куда контейнер будет сохранять данные. Эти данные будут храниться вне контейнера, чтобы в случае прекращения его работы, дата не была потеряна

```Docker
FROM httpd:alpine AS base
WORKDIR /usr/local/apache2/htdocs/
EXPOSE 80
EXPOSE 443
COPY ./html/ .
VOLUME /usr/local/apache2/htdocs/
RUN dotnet build "csproj file"
````

Работа с VOLUME отличается для Windows и Linux!