#Docker 

Сайт на котором в открытом доступе вымещают образы для докера. Так же там можно найти документацию и тэги.

На сайте Docker Hub в описании образа можно найти в описании версию образа *docker-alpine*. Такая версия представляет собой линукс, из которого выпилили все, что не нужно (как правило размер такий образов сокращается процентов на 90%)

Чтобы установить нужную версию нужно указать в поле `FROM` в файле *Dockerfile* указать точную версию образа, который мы хотим собирать. После чего остановить *docker-compose* и снова выполнить `docker-compose build`