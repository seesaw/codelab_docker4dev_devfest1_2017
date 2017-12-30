Inziamo ora a vedere qualcosa di più interessante.

Iniziamo ora ad usare un website statico.
Scarichiamo e lanciamo l'immagine `dockersamples/static-site` con `$ docker run -d dockersamples/static-site`


Vediamo con `docker ps` che l'immagine è running, ma... come ci accedamo? Come possiamo usarla?

Dobbiamo lanciare il comando di prima con qualche altro paramentro `docker run --name static-site -e AUTHOR="Thomas" -d -P dockersamples/static-site
`

*	--name specifica il nome del container
*	-e passa i successivi valori come variabili d'ambiente
* -d crea un container detached, ovvero non "attaccato" alla console corrente
* -P mappa le porte interne con quelle esterne (in questo caso random) 

Fermiamo il precendente container con `docker stop` e avviamo quello nuovo.

Facciamo una prova senza -d
`docker run --name static-site-2 -e AUTHOR="Thomas" -P dockersamples/static-site
` vedere che rimane collegato alla console in uso.



Guardiamo quali sono le porte esposte per poterci interfacciare con il container con il comando `docker port static-site`

Fermiamo il container.

