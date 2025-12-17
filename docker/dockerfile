# Docher file base (nginx esempio)

FROM nginx:latest # immagine di partenza(non parto da zero, uso nginx già pronto)
COPY ./html /usr/share/nginx/html # Copia file dall'host all'immagine(es: sito statico, config, app)
EXPOSE 80 # documenta quale porta usa il container(non apre la porta lo dice soltanto)
CMD ["nginx", "-g", "deamon off;"] # comando che parte quando il container si avvia(senza questo --> container morto subito)

