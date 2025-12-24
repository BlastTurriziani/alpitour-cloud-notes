# Ingress
- Ingress serve a esporre servizi HTTP/HTTPS dall’esterno del cluster.

## Come funziona
- Il traffico entra tramite Ingress e viene instradato verso i Service (ClusterIP),
che a loro volta inoltrano ai Pod.

## Perché usarlo
- Routing per host e path
- Supporto TLS/HTTPS
- Un solo entry-point per più servizi

## Nota
Ingress funziona solo con un Ingress Controller (es. NGINX).
