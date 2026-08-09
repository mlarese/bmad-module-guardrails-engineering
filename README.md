# Guardrails Engineering (`gre`)

Quattro figure di presidio su disciplina architetturale del codice, sicurezza applicativa, infrastruttura e operatività, impianto delle applicazioni che usano modelli linguistici. Ogni raccomandazione porta il costo di non seguirla.

Modulo BMad. È una porzione del bundle [Guardrails](https://github.com/mlarese/bmad-module-guardrails):
stesse figure, stesso comportamento, solo l'area engineering.

> **Generato.** Questo repository è prodotto da `tools/build_modules.py` nel
> repository [bmad-module-guardrails](https://github.com/mlarese/bmad-module-guardrails).
> Le modifiche si fanno lì e poi si rigenera: qui vengono sovrascritte.

## Figure

| Figura | Ruolo | Skill | Cosa presidia |
| ------ | ----- | ----- | ------------- |
| 🔐 Kai | Application Security Engineer | `grl-agent-security` | Pensa come chi attacca e ordina i rischi per probabilità reale, non per gravità teorica; ogni difesa la pesa per quanto costa contro quanto danno evita. |
| 🧱 Otto | Code Architect | `grl-agent-architecture` | Usa SOLID, KISS, DRY, separazione delle responsabilità, vertical slice e architettura esagonale come attrezzi e mai come dogmi: guarda confini fra moduli, direzione delle… |
| 🖥️ Bruno | Infrastructure & Ops Engineer | `grl-agent-ops` | Sistemista veterano: prima di aggiungere un pezzo di infrastruttura chiede quante persone la manterranno alle tre di notte, e il suo mestiere è toglierne, non aggiungerne — «ti… |
| 🧠 Enzo | AI Engineer | `grl-agent-ai` | Costruisce applicazioni che usano modelli linguistici e sa soprattutto quando non servono: metà delle funzioni per cui viene chiamato si risolvono con una query, una regola o un… |

## Skill e workflow

| Skill | Comando | Cosa fa |
| ----- | ------- | ------- |
| `gre-profile` | Profila il progetto | Raccoglie in pochi minuti gli otto campi che danno contesto a tutte e quattro le figure, criticità inclusa. |
| `gre-profile` | Aggiorna il profilo | Riallinea il profilo quando il progetto cambia, e dice se il cambiamento invalida rischi già accettati. |
| `gre-board` | Convoca il collegio | Fa leggere lo stesso artefatto alle sole figure pertinenti e restituisce un riepilogo unico, conflitti compresi. |
| `gre-board` | Rischi già accettati | Mostra, raggruppato per figura, quello che il progetto ha consapevolmente scelto di accettare. |
| `gre-board` | Gate di rilascio | Verifica una release identificata e restituisce GO, GO_CON_CONDIZIONI, NO_GO o EVIDENZA_INSUFFICIENTE. |
| `grl-automation` | Instrada un'automazione | Classifica lo scenario, sceglie agenti e workflow BMad e dichiara capability mancanti, scope e approvazioni. |
| `grl-automation` | Prepara un piano eseguibile | Costruisce passi idempotenti con input, output, precondizioni, rischio, approvazione e rollback. |
| `grl-automation` | Esegui controlli read-only | Raccoglie evidenze e confronti riproducibili senza modificare sistemi esterni. |
| `grl-automation` | Prepara un dry-run | Genera e valida diff o payload senza spendere, pubblicare o applicare side effect. |
| `grl-automation` | Esegui dopo approvazione | Applica solo lo scope approvato, registra prima/dopo e osserva il risultato; in caso di errore attiva il rollback. |
| `grl-automation` | Riprendi un'automazione | Riprende un run esistente dal primo passo non concluso senza duplicare scritture o side effect. |

## Installazione

```
bmad install gre
```

Poi, come primo passo, `gre-profile`: raccoglie il profilo di progetto — settore,
dati trattati, mercato, stack, criticità — e da lì ogni figura deriva quanto essere
severa. Senza profilo il default resta `normal` e le figure partono senza contesto.

## Memoria condivisa

Il profilo vive in `{project-root}/_bmad/memory/grl-shared/project-profile.md`, insieme
a `decisions.md` e `accepted-risks.md`. Il percorso è lo stesso per tutti i moduli
Guardrails: installandone due, il profilo resta uno solo e si compila una volta.

## Convivenza con il bundle

Questo modulo installa skill con **lo stesso nome** del bundle `grl` — `grl-agent-security`
sta identica in entrambi. Bundle e moduli tematici non vanno installati insieme nello
stesso progetto: si sceglie il bundle completo, oppure i moduli delle aree che servono.

## Licenza

MIT.
