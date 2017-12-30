Immaginiamo ora ci serva un database.

Decidiamo di usare postgres.

Per farlo aggiungiamo come ai services un servizio database chiamato 'db' con l'immagine `postgres`.

Facendo docker-compose up, verrà scaricata l'immagine del database e verrà avviata l'app rails.

Per dare priorità al database inseriamo sul docker-compose file la seguente dipendenza

```
depends_on:
      - db

```

Siamo così sicuri che l'app verrà avviata dopo il container del db.

Aggiungiamo delegated e cached rispettivamente sul volume dell'app e della cache, per vitare colli di bottiglia.

Creiamo ora un model e una tabella su db.

Dobbiamo interagire con rails, dentro il container. Per farlo usiamo il comando `docker exec -i -t demo6_db_1 /bin/bash`

Creiamo qualcosa con `rails generate scaffold HighScore game:string score:integer`

Vediamo che l'app ora è interfacciata con il db.
