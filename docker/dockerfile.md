# Docher file base (nginx esempio)
# immagine di partenza(non parto da zero, uso nginx già pronto)
* FROM nginx:latest
# Copia file dall'host all'immagine(es: sito statico, config, app)
* COPY ./html /usr/share/nginx/html
# documenta quale porta usa il container(non apre la porta lo dice soltanto)
* EXPOSE 80
# comando che parte quando il container si avvia(senza questo --> container morto subito)
* CMD ["nginx", "-g", "deamon off;"]
## concetto chiave
Dockerfile → ricetta
Image → risultato
Container → istanza in esecuzione


