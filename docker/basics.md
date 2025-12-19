# Docker file 

# Scrivo il Dockerfile, costruisco l’immagine, Kubernetes crea e gestisce i container.
#Dockerfile
- file di testo con le istruzioni per costruire un’immagine
#Immagine Docker
- risultato del Dockerfile, immutabile e versionata
#Container
- istanza in esecuzione dell’immagine
- gestita da Kubernetes, volatile (può morire e rinascere)

# FROM
From permette di utilizzare ambienti standard e già pronti, riducendo il tempo, errori e problemi di compatibilità

# COPY (build time) 
- file dentro l'immagine
- durante la build i file ./html finiscono nell'immagine
- ogni container avrà sempre quegli stessi file
- COPY = build time -> immagine immutabile
## ottimo per:
- produzione
- app stabili
- immagini versionate
## ES:
FROM nginx:latest
COPY ./html /usr/share/nginx/html <-- build time
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]

# VOLUME (run time)
- file fuori dall'immagine
- l'immagine non contine i file
- i file arrivanno quando il container parte
- se cambi html/ -> cambia subito il sito
- Volume = run time -> file esterni e modificabili
## Tipico di:
- sviluppo
- test
- debug
# ES:
#dockerfile
FROM nginx:latest
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
#avvio container
docker run -p 8080:80 \
  -v $(pwd)/html:/usr/share/nginx/html \ <- run time
  nginx


