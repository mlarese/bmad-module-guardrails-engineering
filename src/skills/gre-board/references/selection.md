# Roster e confini del collegio

Chi entra e su quale segnale. Una figura entra solo se nell'artefatto — o nel profilo di progetto — c'è un aggancio concreto; il tipo di documento non basta.

| Figura | Skill | Entra quando compare |
| ------ | ----- | -------------------- |
| Kai 🔐 | `grl-agent-security` | autenticazione e autorizzazione, segreti e chiavi, superfici esposte (API, upload, webhook), dipendenze, integrazioni LLM |
| Otto 🧱 | `grl-agent-architecture` | struttura delle cartelle, confini fra moduli, strati di astrazione, direzione delle dipendenze, impatto strutturale di una feature |
| Dario 🗄️ | `grl-agent-database` | schema e modello dati, migrazioni, query e indici, scelta del motore, transazioni e consistenza, backup/restore e RPO/RTO del datastore, vector store e ricerca ibrida |
| Bruno 🖥️ | `grl-agent-ops` | Dockerfile e compose, manifest Kubernetes, configurazione di server e reverse proxy, accessi SSH, pipeline di deploy, dove sono conservati i segreti, backup, log e monitoraggio |
| Enzo 🧠 | `grl-agent-ai` | chiamate a un modello linguistico, prompt, RAG o ricerca su documenti, embedding e vector store, catene o agenti, tool calling, automazioni che passano da un modello, valutazione della qualità di un output generato |

Oltre alle figure, una rotta: su una landing o una pagina di prodotto convoca anche `grl-web` in diagnosi, per l'asse che nessuna figura copre — cosa la pagina dice, in che ordine, e se chiede l'azione prima di aver smontato l'obiezione. Quando la pagina arriva dal gate di `grl-web`, la lettura non ripete l'asse ma lo **verifica**: si ricostruisce il brief dalla pagina a freddo e si dice dove diverge da quello scritto. Se non diverge, è una riga sola. Conta come rotta, non come figura del collegio.

## Confini

Chi ha la competenza decisiva parla, gli altri tacciono anche quando il tema li sfiora.

| Questione | Parla | Tace |
| --------- | ----- | ---- |
| Dato personale nei log | Vera | Kai — a meno che il log sia esposto: allora Kai sulla superficie, Vera sul dato |
| Cifratura dei dati a riposo | Kai (come si fa) | Vera dice solo *che* serve |
| Vulnerabilità nota in una dipendenza | Kai | Aldo, anche se la licenza è nello stesso manifest |
| Il prodotto usa un LLM | assi distinti: Enzo sull'impianto (RAG, orchestrazione, eval, costi), Aldo sull'AI Act generale — classificazione, obblighi, dati di training, IP degli output — Vera sull'intersezione AI Act-GDPR (FRIA, bias, basi giuridiche, retention, spiegazione) e Kai sui rischi dell'integrazione | Nils, salvo che il progetto tocchi anche una norma diversa dall'AI Act |
| Core Web Vitals | Nora (l'effetto in Search e la soglia) | Bruno se la causa è server, cache o CDN; Iris se è un'immagine o un font della pagina |
| Crawler di modelli linguistici, llms.txt, citazioni in AI Overviews | Nora | Enzo, che resta sull'impianto delle applicazioni AI |
| Tracking Ads, consenso, Customer Match e remarketing | Vera (dati e consenso), Dalia (mappatura tecnica Ads) | Kai se la superficie è esposta; Aldo/Nils se la base giuridica o il settore regolamentato sono in discussione |
| Troppi strati di astrazione | Otto | tutti gli altri |
| Schema, migrazione, query, indici, scelta del motore, recuperabilità del dato | Dario | Otto resta sui confini fra moduli; Bruno sulle macchine e sui backup eseguiti; Kai su privilegi ed esposizione |
| Tariffa, KPI alberghiero, forecast, inventario, canale, invio a PMS o Channel Manager | Rhea | Marta se il tema diventa fiscale; Dario se la domanda è sullo schema che conserva i dati; Vera sui dati dell'ospite |
| Come si configura un server, un container, un cluster, un deploy | Bruno | tutti gli altri |
| Hardening di SSH, del cluster, dei container | Bruno (come si configura) | Kai dice *quale* rischio va chiuso e con che priorità |
| Segreti in produzione | Bruno (dove si conservano e come si iniettano) | Kai sul rischio dell'esposizione |
| Dove vivono fisicamente i dati (regione, provider, backup) | Bruno (configurazione) | Vera sul vincolo di trasferimento, Nils se il settore lo impone |
| «Ci serve Kubernetes?» | Bruno | Otto solo se la scelta cambia i confini del codice |

Una figura del roster che non è installata nel progetto non si convoca: applica il suo mandato da questa tabella e dillo in una riga.

**Marta non registra rischi accettati.** È l'unica figura del collegio che non scrive in
`accepted-risks.md`: un rischio fiscale accettato non è quindi in memoria, e il filtro che zittisce
le segnalazioni non lo copre. Se in una convocazione precedente l'utente ha accettato un rischio
fiscale, chiediglielo invece di darlo per registrato — o per non accettato.

## Figure fuori da questo modulo

Le tabelle qui sopra citano anche figure Guardrails che questo modulo non installa.
Qui sono installate: Kai (grl-agent-security), Otto (grl-agent-architecture), Dario (grl-agent-database), Bruno (grl-agent-ops), Enzo (grl-agent-ai).

Quando il tema appartiene a una figura assente, il confine resta valido: **dichiara che
il tema esce dal perimetro, nomina la competenza che servirebbe e prosegui solo su ciò che
resta autorizzato.** Registra `missing_capability` e `handoff_status: pending`; non
improvvisare il parere mancante, non dichiarare completato il passaggio e non superare un
gate che dipende da quella capacità. Il lavoro indipendente può continuare, il gate dipendente
resta `blocked` o `EVIDENZA_INSUFFICIENTE`. Il modulo che la contiene si installa a parte; il
bundle completo `grl` le contiene tutte.
