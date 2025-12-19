# ConfigMap
- La ConfigMap viene usata quando il Pod parte.
- L’immagine Docker è già pronta e non cambia.
- Se la ConfigMap cambia, i Pod devono essere ricreati per usare i nuovi valori.
(L'immagine si costruisce una volta, la configMap può cambiare.)
#perchè esiste:
- L'immagine docker è immutabile
- La configurazione può cambiare
#ConfigMap permette di:
- cambiare comportamento senza rebuil dell'immagine

# Nota
ConfigMap viene usata a runtime, mentre il Dockerfile opera a build time.
Questo permette di mantenere l’immagine immutabile e gestire la configurazione separatamente.
