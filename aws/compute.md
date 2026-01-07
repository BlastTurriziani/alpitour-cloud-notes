# EC2 Concetti base
## cos'e una EC2:
- Una macchina virtuale nel cloud.
- Lavora come una normale VM (windows o linux).
- puo' essere pubblica (IP pubblico) o privata (solo rete interna).
## AMI
- Immagine di avvio (amazon machine image).
- Contiene il sistema operativo + software iniziale.
- Esempi: amazon linux, ubuntu, windows server.
## Instance type 
- Determina CPU, RAM, rete.
- Famiglie principali:
  - t2/t3: generiche, economiche
  - m5: bilanciate
  - c5: compute-intensive
  - r5: memory-intensive
  - I database SQL preferiscono istanze memory-optimized (es. r5) perche' sfruttano molta ram per caching e query   

# Sicurezza EC2 (SG + IAM Role).
## Security group
- firewall per la EC2.
- Controlla chi puo' entrare (inbound).
- Regole stateful.
- Best practice:permettere traffico solo da altri Security Group, non da 0.0.0.0/0 quando possibile.
## IAM role 
- Mai usare chiavi statiche nella EC2.
- Dare permessi tramite IAM Role (accesso a S3, DynamoDB, ecc).
- Le credenziali generate dal ruolo sono temporanee e sicure.

# Storage e Dischi (EBS)
## EBS
- Disco persistente collegato alla macchina.
- Tipi principali:
 - gp3 (generale, consigliato).
 - io1/io2 (alta IOPS, database).
 - st1/sc1 (magnetic, per throughput).
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
## Load balancer *
- Distribuisce traffico verso piu' EC2, quindi gestisce il sovraccarico delle macchine in modo da non avere down 
## ALB (Application Load Balancer) --> Layer 7, HTTP/HTTPS. 
- Possiamo bilanciare il carico su più applicazioni sulla stessa macchina(container).
- Per applicazioni basate su container i load balan
- ELB ( EC2 Load Balancer) spesso si usa un load balancer predefinito come ELB di amazon per velocità e configurazione 
  - NLB (Network Load Balancer) --> Layer 4, TCP/UDP.

- Nel complesso possiamo impostare un load balancer interno o esterno, a seconda di dove vogliamo esporre l'applicazione se esterna o interna.
- Ha la funzionalità di separare il traffico pubblico da quello privato. 
- Fa dei controlli di integrità delle nostre instanze per assicurasi che funzionino tutte correttamente (siamo noi che configuriamo quello che poi lui andrà a controllare)
- Se ci fosse un'istanza che non funziona correttamente il traffico verrà indirizzato verso una macchina funzionante.
- Può anche imporre la persistenza con i cookies quindi l'utente parlerà con la stessa instanza nel tempo.

# S3 - EBS - VM - Container
- S3 = file via API
- EBS = disco per VM
- VM = server completo
- Container = applicazione







