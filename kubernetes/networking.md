# IGW
IGW = Internet gateway --> subnet pubblica (perche' accetta traffico da internet)

# Nat
Nat gateway --> subnet privata (perche' permette solo l'uscita)

# DB
DB sempre in subnet privata(NAT)
niente IGW nessuna connessione in ingresso da internet

# Load balancer
Un load balancer pubblico deve stare in subnet pubbliche perche' ha bisogno dell'internet gateway 


