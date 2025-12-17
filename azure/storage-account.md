# Storage account
Uno storage account è il contenuto di base di azure per salvare dati(blob,file, code, tabelle).

# Tipi di dati 
Blob storage --> file, backup, log, media
File Storage --> file share (tipo NAS)

# Replication
## Tipo               Significato                         Quando usarlo
  LRS        3 copie dello stesso datacenter            test/non critico
  ZRS        3 copie in zone diverse                    produzione standard
  GRS        replica anche in un'altra regione          disaster recovery
  GZRS       zone + regione secondaria                  sistemi critici

# Access tiers (costo vs accesso)
- hot --> accesso frequente (costa di più)
- cool --> accesso raro
- archive --> quadi mai (recupero lento)

i dati possono cambiare tier (lifecycle)

# Sicurezza (solo le basi giuste)
- Accesso con Azure AD / RBAC
- Shared Access Signature (SAS) per accessi remporanei
- Encryption sempre attiva (default azure)

Uno storage account è progettato bilanciando costo, disponibilità e sicurezza dei dati. 
