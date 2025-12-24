# AWS S3 + KMS 

## Amazon S3 
- S3 è uno storage a oggetti usato per file, backup e log.
- Non è un filesystem e si accede ai dati tramite API.

## Storage class
- Standard: accesso frequente.
- Standard-IA: accesso raro.
- Glacier / Deep archive: accesso molto raro, costi bassi.

## LifeCycle 
- Le regole di lifecycle permettono di spostare automaticamente i dati tra le classi per ridurre i costi e gestire la retention.

## Crittografia 
- SSE-S3: chiavi gestite da aws.
- SSE-KMS: chiavi gestite da kms, più controllo e audit.

## KMS 
- KMS gestisce le chiavi di cifratura usate da S3 e atri servizi.
- Se un ruolo IAM non ha permessi sulla chiave KMS, non può leggere i dati cifrati.
