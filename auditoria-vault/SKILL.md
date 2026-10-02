---
name: auditoria-vault
description: Executa a rotina unificada de vigilância diária e saúde do vault (auditoria de links, notas órfãs, inbox pendente, sincronização Last.fm e sincronização de cores). Use quando o usuário pedir 'auditoria', 'heartbeat', 'lint' ou 'verificação de saúde'.
---

# Prompt — Auditoria Diária de Saúde do Vault (`auditoria`)

Instruções operacionais para a execução unificada e periódica (diária) de manutenção, checagem de saúde e sincronização do ecossistema do vault.

---

## 🎯 Objetivo
Concentrar em um único comando diário (`auditoria`, `heartbeat` ou `lint`) a verificação de integridade física e conceitual do vault, atualizando telemetrias externas periódicas (Last.fm), limpando a entrada de dados (Inbox), corrigindo links no grafo, auditando estilos cromáticos e registrando o estado operacional no Daily Log do dia.

---

## ⚙️ Checklist Operacional de Execução

Ao receber o comando **`auditoria`** (ou seus sinônimos `heartbeat`, `lint` ou `verificação de saúde`), a IA executa sequencialmente:

### 1. Sincronização de Telemetria Periódica (Last.fm & Dota 2)
- Executar a sincronização delta do Last.fm:
  ```powershell
  python Scripts/sync_lastfm.py
  ```
- Executar a sincronização de partidas do Dota 2 (Modo Turbo):
  ```powershell
  python Scripts/sync_dota.py
  ```
- Incorporar novos scrobbles em `Fontes/lastfmstats-SirPulga.json` e partidas em `Fontes/dota2-matches.json`.
- Atualizar métricas consolidadas em [[André/Música e Hábitos de Audição.md]] e [[André/Jogos/Dota 2/Dota 2.md]].

### 2. Varredura do Inbox (`/Inbox/`)
- Mapear a pasta `Inbox/`.
- Verificar se existem arquivos brutos aguardando processamento (áudios, PDFs, notas soltas, comprovantes).
- Se houver apenas `README.md`, classificar o Inbox como limpo.

### 3. Auditoria de Integridade do Grafo (Vault Lint)
- Mapear todos os links bidirecionais (`[[...]]`) e identificar links quebrados (apontando para arquivos inexistentes).
- Identificar notas órfãs (arquivos Markdown sem conexões de entrada ou saída no grafo).
- Aplicar correções automáticas imediatas em links quebrados ou placeholders.

### 4. Sincronização Cromática e Visual
- Conferir se os 10 pares de regras cromáticas de pastas em `.obsidian/snippets/note-distinction.css` correspondem com exatidão aos valores inteiros decimais e hexadecimais no `.obsidian/graph.json`.

### 5. Continuidade de Memória e Registro Operacional
- Verificar a existência ou criar o log operacional do dia em `Daily Logs/YYYY-MM/YYYY-MM-DD-log.md` (ou `Daily Logs/YYYY-MM-DD-log.md`).
- Adicionar uma entrada formal detalhando:
  - Horário de início e término.
  - Resultados da sincronização Last.fm (scrobbles novos, total acumulado).
  - Status do Inbox.
  - Relatório de links e nós órfãos.
  - Status da validação cromática.
  - Arquivos modificados ou corrigidos.

---

## 🚀 Gatilhos Reconhecidos no Chat
- `auditoria` (gatilho mestre diário)
- `heartbeat`
- `lint`
- `auditoria do vault`
- `verificação de saúde`
