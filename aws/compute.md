# EC2 Concetti base
## cos'e una EC2:
- Una macchina virtuale nel ccloud.
- Lavora come una normale VM (windows o linux).
- puo' essere pubblica (IP pubblico) o privata (solo rete interna).
## AMI
- Immagine di avvio (amazon machine image).
- Contiene il sistema operativo + software iniziale.
- Esempi: amazon linux, ubuntu, windows server.
## Istance type 
- Determina CPU, RAM, rete.
- Famiglie: t2/t3 (general), m5 (balanced), c5 (compute), r5 (memory).

# Sicurezza EC2 (SG + IAM Role).
## Security group
- firewall per la EC2.
- Controlla chi puo' entrare (inbound).
- Regole stateful.
## IAM role 
- Mai usare chiavi nella EC2.
- Usare IAM role per dare permessi temporanei (es: accesso a S3).

# Storage e Dischi (EBS)
## EBS
- Disco persistente collegato alla macchina.
- Tipi principali:
 - gp3 (generale, consigliato).
 - io1/io2 (alta IOPS, database).
 - st1/sc1 (magnetic, per stroughput).
## Caratteristiche 
- Persistente: non sparisce se spegni la EC2.
- Puo' essere aumentato in qualsiasi momento.

# Elastic IP, Auto Scaling e Load Balancing (Funzioni avanzate).
## Elastic IP 
- IP pubblico statico associabile ad una EC2.
- Utile per server che devono avere sempre lo stesso IP.
## Auto scaling group (ASG)
- Gruppo di EC2 che cresce o diminuisce in base al carico.
- Usato con il load balancer.
## Load balancer 
- Distribuisce traffico verso piu' EC2.
- Puo' essere pubblico o privato.

