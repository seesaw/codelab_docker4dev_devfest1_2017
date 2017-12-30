Iniziamo ora a creare un app su più container.

Per prima cosa creiamo una nostra immagine con ruby.

```

FROM ruby:2.3.3

RUN apt-get update -qq && apt-get install -y build-essential libpq-dev nodejs

RUN mkdir /my_app

WORKDIR /my_app

RUN gem install rails

```

e ne facciamo la build.

Creo anche il file docker-compose.yml

```
version: '3'
services:
  web:
    build: ./application
    ports:
      - "3000:3000"
```

Usando il comando `docker-compose run --service-port rails web new my_rails_ap¡` verrà creato un progetto rails nuovo all'interno del container, che morirà.

Aggiungiamo la riga `command: rails new my_rails_app` all'interno dei docker-file, e vediamo come adesso, facendo `docker up`, si ottenga la stessa cosa.

Questo comando serve per caricare tutto il docker-compose file, ovvero tutta la rete di container.

Come ultimo passaggio, rifacciamo la stessa cosa abilitando il volume aggiungendo 

```
    #volumes:
    #  - ./application:/my_app
```

Il volume creerà un collegamento tra host e container.
