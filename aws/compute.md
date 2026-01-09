# EC2 Concetti base
## cos'e una EC2:
- Una macchina virtuale nel cloud.
- Lavora come una normale VM (windows o linux).
- puo' essere pubblica (IP pubblico) o privata (solo rete interna).
## Client e Application
- Errori come 4xx sono errori del client
- Errori come 5xx sono errori dell'application(es. 503 il LB non ha più capacità o non è momentaneamente in grado di gestire la richiesta)
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

## Auto scaling group (ASG) *
- Le funzionalità dell'auto scaling group sono quelli di scalare e incrementare le instanze EC2 in base al carico delle richieste e di rimuoverle in caso di cali
- Possiamo definire un massimo e un minimo di macchine attive.
- Usato con il load balancer().
- 

## Load balancer *
- Distribuisce traffico verso piu' EC2, quindi gestisce il sovraccarico delle macchine in modo da non avere down 
- Nel complesso possiamo impostare un load balancer interno o esterno, a seconda di dove vogliamo esporre l'applicazione se esterna o interna.
- Se ci fosse un'istanza che non funziona correttamente il traffico verrà indirizzato verso una macchina funzionante.
- Ha la funzionalità di separare il traffico pubblico da quello privato.
- Fa dei controlli di integrità delle nostre instanze per assicurasi che funzionino tutte correttamente (siamo noi che configuriamo quello che poi lui andrà a controllare)
- ELB ( EC2 Load Balancer) spesso si usa un load balancer predefinito come ELB di amazon per velocità e configurazione
- I load balancer classici sono deprecati.
- I load balancer possono essere scalabili ma non instantaneamente(per esempio se sappiamo che per un determinato giorno ci sarà un evento particolare si quello che viene chiamato Pre-warming)
## ALB (Application Load Balancer) --> Layer 7, HTTP/HTTPS. 
- Con ALB i server delle applicazioni non vedono direttamente l'IP del client(viene inserito in una intestazione denominata X-forwarded-for)
- Possiamo avere load balancer su più applicazioni sulla stessa macchina(container).
- Può anche imporre la persistenza con i cookies quindi l'utente parlerà con la stessa instanza nel tempo questa funzionalità sarà gestita fondamentalmente da ALB.
- Per applicazioni basate su container e microservizi i load balancer sono la scelta migliore.
- C'è una funzionalità di mappature delle porte, fondamentalmente il load balancer può rendirizzare a qualsiasi porta dinamica nel backend(si potrebbe usare un ALB con 10 applicazioni e funzionerebbe benissimo)
- ALB può effettuare il routing con hostname e path
- ALB è perfetto per ECS o docker
## NLB (Network Load Balancer) --> Layer 4, TCP/UDP.
- Il load balancer del carico di rete ha prestazioni molto più elevate rispetto a quello delle applicazioni
- Vede direttamente l'IP del client sul lato applcazione(vale solo per i LB di rete).

# S3 - EBS - VM - Container
- S3 = file via API
- EBS = disco per VM
- VM = server completo
- Container = applicazione

# Glue *
- è un processo ETL (Extract, Transform, Load) gestito da aws.
- aws gestisce tutto il backend del server e tutto il provisioning del software. 
- Aiuta a capire i dati, suggerisce trasformazioni e genera codice ETL in modo da dedicare meno tempo per la codifica manuale.
- Esegue processi ETL in modo flessibile in una piattaforma spark scalabile assegnando automaticamente le risorse necessarie per completarli.
## Catalogo
- Include un catalogo dati, un repository di metadati centrale.
- possiamo avere i nostri dati in qualunque database dentro aws, i nostri metadati ovunque essi siano possono essere archiviati dentro un catalogo in aws glue.
- metadati informazioni correlate allo schema e alla fonte dei dati dove vengono correlati.
- Il catalogo dati può essere utilizzato per: Ottenere i metadati informativi sui tuoi dati, avere il monitoraggio degli accessi ecc(da approfondire)
- Un motore ETL in grado di generare automaticamente codice python.
- Un motore flessibile che gestisce la risoluzione delle dipendense il monitoraggio dei processi e i nuovi tentativi.
- Insieme questi elementi facilitano una parte di lavoro pesante come individuazione, categorizzazione, pulizia, arricchimento e spostamento dei dati.
- Rileva automaticamente i dati determina lo schema e crea il nostro catalogo dati.
- Offre un'ntegrazione immediata con amazon athena, amazon EMR e amazon redshift spectrum
- Il codice ETL creato da glue è semplicemente codice python modificabile, riutilizzabile e portatile.
- è serverless quindi non ci sono risorse da gestire e paghi solo per quello che i nostri lavori consumano per l'esecuzione.
- Lavora molto con spark
# Lambda *
- è un servizio serverless quando il nostro codice non è in esecuzione non ci sono costi.
- Viene invocata da un servizio AWS quando accade un'evento. 
- ES. carichiamo un file su S3 --> S3 rileva l'evento --> S3 chiama lambda --> lambda esegue il codice.
- Serve per automatizzare piccole azioni ripetitive che altrimenti dovresti fare a mano o con una vm sempre accesa.
- non

# step function

# event bridge










