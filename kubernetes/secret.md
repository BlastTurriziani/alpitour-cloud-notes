# Secret 
- Un secret seve a fornire dati sensibili (password, token, certificati) ai pod.
- I secret non fanno parte dell'imagine Docker.
- I valori sono in base64 (encoding, non cifratura).

#Perchè esiste 
- L'immagine docker è immutabile.
- Le credenziali non devono stare nel codice o nell'immagine.

#Quando viene usato 
- Il secret viene letto quando il Pod viene creato.
- Se il secret cambia, i Pod devono essere ricreati per usare i nuovi valori.

#Differenza con ConfigMap
- ConfigMap = configurazione normale
- Secret = configurazione sensibile  
