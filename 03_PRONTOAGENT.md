# ProntoAgent — Piattaforma B2B Front Office Automation

## Cos'è

ProntoAgent è una piattaforma B2B per l'automazione del front office multicanale.

**Posizionamento:** "Un solo cervello per tutte le tue comunicazioni."

Non vende tecnologia — vende il front office sempre attivo per PMI italiane su più verticali.

## Dominio

**prontoagent.it** — intestato a Grazia Petrini

## Tassonomia Agenti

| Tipo | Descrizione | Canali |
|------|-------------|--------|
| **Talker** | Agenti vocali | Telefono (voce) |
| **Writer** | Agenti che scrivono | Email, WhatsApp, Telegram |
| **Doer** | Agenti che eseguono | Workflow, automazioni, integrazioni |

**ProntoAgent** è l'orchestratore che coordina i tre tipi e gestisce il cross-channel.

**Esempio cross-channel:** arriva una telefonata → parte automaticamente un WhatsApp al fornitore.

## Modello di Business

**Crediti ricorrenti mensili** su tre livelli:

```
Pavaleggio Digital Services OÜ (Paolo/Grazia)
    ↓ wholesale credits
Reseller (es. società dei 1000 clienti)
    ↓ retail credits con markup
Cliente finale (PMI)
    ↓ consuma crediti per ogni azione
```

- Il reseller compra pacchetti di crediti mensili
- Rivende con il suo markup ai clienti finali
- Il reseller si assume il rischio del sottoutilizzo

## Roadmap

### Fase 1 — Talker (PRIORITÀ)
- Clone di CallAgent riscritto nativamente white label
- Architettura sottodomini automatici con SSL
- Primo reseller: società dei 1000 clienti
- Stack: Supabase + Netlify + Cloudflare for SaaS

### Fase 2 — Writer
- Aggiunta canale email e WhatsApp
- Cross-channel attivo
- Stessa architettura, nuovi moduli

### Fase 3 — Doer
- Agenti che eseguono azioni
- Integrazioni CRM e gestionali esterni

### Fase 4 — Marketplace
- API aperte per agenti esterni (es. chi ha già CallAgent o DeepAgent)
- MCP server nativi per integrazione con Claude e altri LLM

## Architettura Tecnica

### Stack

| Layer | Tecnologia |
|-------|-----------|
| Frontend | React su Netlify |
| Backend | Supabase Edge Functions |
| Database | Supabase Postgres |
| Auth | Supabase Auth |
| DNS/SSL | Cloudflare for SaaS (wildcard SSL) |
| Sottodomini | Cloudflare Workers (generazione automatica) |
| Pagamenti | Stripe |
| LLM | Anthropic API (Claude) |

### Integrazioni

- **ElevenLabs** — sintesi vocale
- **Twilio** — telefonia
- **Unipile** — WhatsApp Business
- **PHPMailer** — email

### White Label — Architettura Sottodomini

Ogni cliente/reseller ha il suo sottodominio dedicato:
```
cliente1.prontoagent.it
cliente2.prontoagent.it
```

Cloudflare for SaaS gestisce:
- Creazione automatica sottodominio via API
- SSL wildcard automatico
- White label completo: il cliente porta il suo dominio, punta CNAME su Cloudflare

**Isolamento dati:** ogni cliente ha il suo schema Supabase isolato, generato automaticamente alla creazione nel pannello reseller.

### Modelli di Reseller

**Fase 1 — Reseller senza rebrand**
Il reseller vende con il brand ProntoAgent visibile. Più semplice tecnicamente.

**Fase 2 — White label completo**
Il reseller vende con il suo brand. ProntoAgent è invisibile.

### Integrazione Agenti Esterni

Chi ha già CallAgent, DeepAgent o altro:
- Si connette via API token
- ProntoAgent orchestra sopra quello che esiste
- Non buttano il vecchio sistema — lo integrano

## Primo Partner

Una società italiana con ~1000 clienti PMI ha contattato Paolo per erogare servizi di front office automatizzato.

La struttura commerciale:
- La società ha i clienti finali
- Pavaleggio Digital Services OÜ eroga il servizio in white label
- Paolo fornisce la tecnologia/metodologia come fornitore esterno

## Origine Tecnologica

ProntoAgent nasce da CallAgent (ceduto a OPS ECOM). Il codice sorgente NON è stato ceduto formalmente (atto notarile in corso). La nuova versione è una riscrittura completa su stack moderno.

**Differenza chiave:**
- CallAgent = prodotto verticale (solo voce)
- ProntoAgent = hub orchestratore multicanale

