# IGW
IGW = Internet gateway --> subnet pubblica (perche' accetta traffico da internet)

# Nat
Nat gateway --> subnet privata (perche' permette solo l'uscita)

# DB
DB sempre in subnet privata(NAT)
niente IGW nessuna connessione in ingresso da internet

# Load balancer
Un load balancer pubblico deve stare in subnet pubbliche perche' ha bisogno dell'internet gateway 

# Servicea
## Cluster IP e Accesso esterno
- E il tipo di service di default.
- Serve per comunicazioni interne al cluster.
- Espone i pod all'interno del cluster con un IP stabile.
- Usato tra i microservizi (es: frontend --> backend).
- Un service clusterIP e' raggiungibile solo dall'interno del cluster.
- Non puo' essere chiamato da internet o da macchine esterne.
- Per accesso esterno servono altri tipi di Service (Nodeport, Loadbalancer) o un ingress
## NodePort
- Espone l'applicazione Kubernetes all'esterno del cluster.
- Usa una porta del Node (range 30000–32767) accessibile da fuori.
- Qualsiasi Node può inoltrare il traffico ai Pod corretti.
- Usato per test e sviluppo, non consigliato in produzione.
## Perche' esistono i service
- I pod cambiano ip spesso perche vengono ricreati
- Il service offre un endpoint stabile (IP + DNS) verso un gruppo di pod.
- Usa i label selector per decidere quali pod far vedere.





