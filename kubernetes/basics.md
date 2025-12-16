# node 
node: Macchina del cluster (fornisce CPU/RAM).
Quando viene aggiornato un deployment il node non decide nulla replica e basta.

# pod 
Pod: Unita' base in kubernetes, ha un ip proprio e contiene uno o piu' containers.
Kubernetes non usa i pod da soli perche' i pod muoiono facilmente.
Pod crash --> replicaset lo ricrea il deployment non interviene e il node esegue.

# replicaset
Il replicaset garantisce che ci sia sempre il numero desiderato di pod.
Il replicaset ricrea i pod che muoiono.


# deployment
Il deployment garantisce versioni e aggiornamenti, non i pod . 
Aggiornare un deployment crea un nuovo replicaset.
Il deployment controlla quanti pod devono stare nel vecchio e nel nuovo replicaset durante un aggiornamento.
- Il deploiment è l'oggetto che descrive come deve girare un'applicazione in kubernetes.
- Definisce immagine, numero di repliche e strategie di aggiornamento.
- Gestisce il ciclo di vita dell'app usando replicaset e pod.
- Permette aggiornamenti senza downtime e rollback.
## Deployment yamal campi minimi
- image: immagine del container da eseguire.
- replicas: numero di pod desiderati.
- selector + labels: servono a collegare Deployment/replicaSet ai pod corretti.
- Template: definisce il pod (container, porte, env, ecc.)

# ConfigMap e Secret
## ConfigMap 
- Contiene configurazioni non sensibili.
- Usata per variabili d'ambiente, file config, impostazioni dell'app.
- non e' cifrata.
## Secret
- Contiene dati sensibili come password, token e certificati.
- I valori sono codificati in base64 (non super sicuri).
- Piu' sicura per informazioni delicate rispetto alla configmap.

### Come vengono usati nei pod
- Possono essere montati come variabili d'ambiente.
- Possono essere montati come file dentro il container.
### Differenza chiave 
- ConfigMap = configurazione normale.
- Secret = configurazione sensibile.


