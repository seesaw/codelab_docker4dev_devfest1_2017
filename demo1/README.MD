Iniziamo dai comandi base:

`docker pull` scaricherà sulla vostra macchina un immagine presente sul repository comune di docker.

Potente consultare il repository da [hub.docker.com](http://hub.docker.com)

Per prima cosa inziamo a scaricare [alpine](https://it.wikipedia.org/wiki/Alpine_Linux) con il comando `docker pull alpine`

Lanciamo il comando `docker run alpine echo "hello from alpine"`

Cosa è successo ? 

1.	Il Docker client contatta il Docker daemon
2.	Il Docker daemon controlla in locale se l'immagine `alpine` esiste, e in caso la scarica.
3. Il Docker daemon crea un container con quella immagine .
4. Il Docker daemon manda lo stream al Docker client