---
name: netcore-design-system-3-0-skill-lovable
description: Use when the user wants to use, integrate, configure, or build with Netcore-Design-System-3.0 — Agent skill for Claude, Cursor, and Lovable that enforces the Netcore product design system on every AI-generated UI — Manrope font, brand blue #2F68E5, white inputs, 8px radius, Untitled UI component anatomy with Netcore token overrides. Activate when the conversation mentions Netcore-Design-System-3.0.
---

# Netcore-Design-System-3.0

> Agent skill for Claude, Cursor, and Lovable that enforces the Netcore product design system on every AI-generated UI — Manrope font, brand blue #2F68E5, white inputs, 8px radius, Untitled UI component anatomy with Netcore token overrides.

**Repository:** https://github.com/designedbytaiyab/Netcore-Design-System-3.0
**Language:** —  ·  **Stars:** 0  ·  **License:** —


## When to use this skill

Use when the user wants to use, integrate, configure, or build with Netcore-Design-System-3.0 — Agent skill for Claude, Cursor, and Lovable that enforces the Netcore product design system on every AI-generated UI — Manrope font, brand blue #2F68E5, white inputs, 8px radius, Untitled UI component anatomy with Netcore token overrides. Activate when the conversation mentions Netcore-Design-System-3.0.

## Capabilities (from README)

- PMs — prototype any Netcore screen without explaining the design system every time
- Designers — stop correcting AI output before it can go into a review
- Engineers — get CSS that actually matches the product when you use AI codegen

## Workflow

1. **Orient** — Confirm what the user wants to do with Netcore-Design-System-3.0.
2. **Recall** — Abra `REFERENCES.md` e localize a seção do doc relevante (mirror dos paths originais).
3. **Configure** — Walk through installation/setup; ask for missing env vars or credentials.
4. **Build** — Generate code/config that matches the conventions in the docs.
5. **Validate** — Run the project's own checks (tests, lints, smoke calls) before declaring done.
6. **Cite** — Quando responder, mencione qual seção de `REFERENCES.md` você usou.

## Conventions

- Prefer official APIs/CLI documented in the repo over third-party wrappers.
- Surface required env vars and secrets explicitly; never inline real values.
- If the repo ships a CLI, prefer its commands over re-implementing logic.

## Sanitização de Dados (DLP — obrigatório)

Esta skill opera sob política **Zero Trust**. Antes de qualquer resposta, log ou
artefato gerado:

- **Nunca** exponha em logs, UI pública ou commits: chaves de API, tokens, senhas,
  strings de conexão, JWTs, dados de PII (CPF, CNPJ, e-mail real, telefone) ou
  conteúdo de arquivos `.env` reais.
- Ao citar valores sensíveis, substitua por placeholder: `ENV_VAR_PLACEHOLDER`,
  `*****` ou `<REDACTED>`.
- Toda credencial deve ser lida via `process.env.NOME_DA_VAR` — nunca hard-coded.
- Arquivos de configuração entregues ao usuário devem ser **templates** sem valores
  reais (ex.: `.env.example` com `API_KEY=ENV_VAR_PLACEHOLDER`).
- Antes de enviar dados do usuário a APIs terceiras, valide o destino e mascare
  PII que não seja estritamente necessária à chamada.

## Mitigar Riscos de Dados (mecanismo de ação)

Quando o usuário pedir **"mitigar riscos"**, **"sanitizar"** ou for solicitar
deploy/publicação, execute este protocolo antes de qualquer outra coisa:

1. **Validar** — varra o contexto atual e os arquivos gerados procurando:
   `sk_live_*`, `sk_test_*`, `pk_live_*`, `whsec_*`, `AIzaSy*`, `ghp_*`,
   `AKIA*`, `xox[baprs]-*`, `SG.*`, JWTs (`eyJ...`), connection strings
   (`postgres://user:pass@...`), CPF/CNPJ, e arquivos `.env` com valores reais.
2. **Interromper** — se algum padrão for encontrado, **pare o fluxo** e reporte
   o achado ao usuário antes de prosseguir. Não gere, não envie, não comite.
3. **Mascarar** — substitua o valor sensível por `ENV_VAR_PLACEHOLDER` (ou
   `*****` para PII) tanto no código quanto em logs/respostas.
4. **Corrigir o código** — converta chamadas inseguras (`fetch("https://api/?key=ABC123")`,
   credenciais inline em headers/SDK) para usar `process.env.X` e instrua o
   usuário a configurar a variável no ambiente.
5. **Substituir `.env` por `.env.example`** — se um `.env` real for detectado,
   gere um `.env.example` com placeholders e remova o arquivo original.
6. **Reportar** — ao final, devolva um sumário: o que foi mascarado, o que foi
   substituído, e quais ações o usuário ainda precisa executar (rotacionar
   chaves vazadas, configurar variáveis de ambiente, revisar diffs).

Se algum risco crítico não puder ser mitigado automaticamente, **recomende não
publicar** o artefato e oriente revisão manual.

## Reference index (consolidado em REFERENCES.md)

- `README.md` (consultar seção em `REFERENCES.md`)
- `CHANGELOG.md` (consultar seção em `REFERENCES.md`)
- `SKILL.md` (consultar seção em `REFERENCES.md`)
- `design-system.md` (consultar seção em `REFERENCES.md`)
- `.github/PULL_REQUEST_TEMPLATE.md` (consultar seção em `REFERENCES.md`)
- `references/components.md` (consultar seção em `REFERENCES.md`)
- `references/extended.md` (consultar seção em `REFERENCES.md`)
- `references/tokens.md` (consultar seção em `REFERENCES.md`)
- `flows/campaign-creation/figma-nodes.md` (consultar seção em `REFERENCES.md`)
- `flows/campaign-creation/specs.md` (consultar seção em `REFERENCES.md`)
- `_metadata.json` — Repo metadata snapshot.


## Complete repository map

```
- .github/
  - PULL_REQUEST_TEMPLATE.md
- assets/
  - components/
    - side-nav.png
    - text-fields.png
    - top-navigation.png
  - screens/
    - campaign-creation/
      - 01-home.png
      - 02-type-selection.png
      - 03-channel-selection.png
      - 04-setup.png
      - 05-audience.png
      - 06-audience-filters.png
      - 07-content.png
      - 08-content-selected.png
      - 09-schedule.png
      - 10-preview.png
- CHANGELOG.md
- design-system.md
- flows/
  - campaign-creation/
    - figma-nodes.md
    - specs.md
- README.md
- references/
  - components.md
  - extended.md
  - tokens.md
- SKILL.md
```
