# Security Group 
Firewall a livello di istanza, stateful, regole inbound decidono chi puo' entrare. Migliore della subnet per sicurezza perche' basato su ruoli non ip

# Comunicazione Front --> Back
Apro nel security group del backend (sg-back) la porta 8080 solo dal security group frontend (sg-front)
cosi' 
- Front --> back = si
- Back --> front = no

