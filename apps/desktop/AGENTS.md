# Hermes Desktop — regole rapide

Valgono anche le regole del repo Hermes. La guida di giudizio completa è in
`ENGINEERING_GUIDE.md`; il contratto visuale è `DESIGN.md`.

- Stack: Electron + React/TypeScript; renderer in `src/`, main/preload in `electron/`.
- Riutilizzare componenti e token esistenti; niente stili globali ad hoc.
- Mantenere i confini main/preload/renderer e validare ogni payload IPC.
- Non esporre Node, shell, filesystem o segreti direttamente al renderer.
- Preservare accessibilità, tastiera, focus e comportamento cross-platform.
- Una modifica funzionale richiede test vicino al codice; evitare snapshot fragili.

Verifiche dalla directory `apps/desktop`:

- `npm run typecheck`
- `npm run lint`
- `npm run test:ui` oppure il test Vitest mirato
- test piattaforma desktop solo se la modifica tocca Electron/IPC

Non eseguire packaging, firma o publish salvo richiesta esplicita.
