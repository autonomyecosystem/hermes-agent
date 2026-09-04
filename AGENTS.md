# Hermes — contratto operativo locale

Hermes è un progetto upstream adattato all'ecosistema. La guida upstream completa
è in `docs/UPSTREAM_AGENT_GUIDE.md`; leggerne solo le sezioni pertinenti.

## Orientamento

- Core Python: `hermes/`, `tools/`, `run_agent.py`, `cli.py`.
- Gateway/API e piattaforme: `gateway/` e configurazione in `~/.hermes/`.
- Desktop Electron/React: `apps/desktop/` (ha regole proprie).
- Test Python: `tests/`; test e workspace JS: `tests-js/`, `ui-tui/`, `web/`.
- Avvio locale governato: `../AutonomyControlCenter/autonomy/scripts/hermes-local.sh`.

## Invarianti

- Conservare prompt caching e ordine dei messaggi/tool; evitare refactor larghi.
- Il core deve restare stretto; capacità opzionali vanno in toolset/skills.
- Non inserire credenziali in `config.yaml`, log, fixture o commit. Usare env.
- Non usare `--network host` né ampliare mount/permessi dei container.
- Non cambiare provider/modello, inviare messaggi reali o riavviare il servizio
  operativo senza considerare l'impatto ACC.
- Il repository segue upstream: non mescolare fix locali con aggiornamenti massivi.

## Verifica

- Python mirato: `pytest tests/<file>.py -q`.
- Suite Python: `./scripts/run_tests.sh`.
- Workspace JS: `npm run check` (può essere lunga; prima usare il workspace mirato).
- Prima del handoff: `git diff --check` e `git status --short`.

Per convenzioni architetturali, tool loop e release usare la guida di riferimento,
non copiarla nel prompt.
