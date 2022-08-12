Traefik и локальная разработка
======

Контейнер с Traefik для запуска http реверс-прокси с локальной машины в docker контейнер.

Заменить паттерн ##yourcompany## на ваш домен

#### Настройка DnsMasq

Для того что бы весь трафик на поддомены *.lc с локальной машины направлялись на 127.0.0.1 нужно на локальную машину установить Dnsmasq и настроить.

* Для MacOS:

Инструкция: https://gist.github.com/ogrrd/5831371
Инструкция2: https://medium.com/@kharysharpe/automatic-local-domains-setting-up-dnsmasq-for-macos-high-sierra-using-homebrew-caf767157e43

```bash

./build/dnsmasq-macos

```

* Для Linux:

```bash

./build/dnsmasq-linux

```


#### Запуск Traefik

```bash

./build/run-dev

```

После запуска - Traefik будет всегда запущенным в docker.

Будет доступно:

http://traefik.##yourcompany##.lc:8080 - Дашборд Traefik'а

http://adminer.##yourcompany##.lc - Adminer это веб-интерфейс для работы с БД в docker

http://api-editor.##yourcompany##.lc - Swagger Api editor Интерфейс для редактирования api схем


#### Остальные сервисы

Пример описания сервиса можно посмотреть в файле `docker-compose.dev.example.yml`

  

Все сервисы должны быть в docker сети `##yourcompany##` и иметь network aliace:

```bash
networks:
  default:
   aliases:
    - test.##yourcompany##.lc
```
