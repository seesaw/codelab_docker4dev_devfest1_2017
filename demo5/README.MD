Ora abbiamo un app rails, facciamola partire.

Modifichiamo il file docker-compose aggiungerndo una folder per la cache, in modo tale da non dover più fare il download delle gemme.

Il file diventa
```
version: '3'
services:
  web:
    build: ./application
    ports:
      - "3000:3000"
    command: bash -c "bundle install --path=/cache && rails s -p 3000 -b '0.0.0.0'"
    volumes:
      - ./application:/my_app
      - ./application/gem_cache:/cache

```

Ora, rilanciando docker-compose up, verranno scaricate e salvate le gemme dentro la folder di cache, e verrà avviato il servizio.

Capite quanto potente è avere il codice che gira in un ambiente isolato, e avere il codice accessibile... Provate ad aggiungere un file index.html in /application/my_rails_app/public con all'interno 

```
Hi devfest1 !
```

e ricaricare la pagina. 