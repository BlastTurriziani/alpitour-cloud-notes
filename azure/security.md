# Identity vs RBAC
## Identity (Azure AD)
- Definisce *chi* sei: utente, gruppo, servizio, VM.
- Serve per autenticarsi alle risorse azure.
- Include anche le managed identity per le VM e i servizi

## RBCA (Role-Based Access Control)
- Definisce *cosa puoi fare* sulle risorse azure.
- Assegna permessi a identita' (lettura, scrittura, gestione).
- Ruoli tipici: reader, Contributor, owner.

### Differenza chiave
- Identity = autenticazione (chi entra).
- RBCA = autorizzazione (cosa puo' fare chi entra).
