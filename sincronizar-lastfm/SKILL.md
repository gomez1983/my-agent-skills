---
name: sincronizar-lastfm
description: Executa a sincronização delta e consolidação de scrobbles da API do Last.fm via script python e atualiza telemetria no vault. Use sob 'sincronizar_lastfm' ou 'sync_lastfm'.
---

# Prompt — Sincronização e Telemetria Musical (Last.fm)

Instruções operacionais para execução sob demanda ou periódica da sincronização incremental de scrobbles e atualização do painel de hábitos musicais no vault.

---

## 🎯 Objetivo
Buscar novos scrobbles registrados no perfil `SirPulga` na API do Last.fm desde o último timestamp registrado em `Fontes/lastfmstats-SirPulga.json`, incorporar as novas faixas à base estruturada, recalcular as métricas globais e atualizar o painel de telemetria em [[André/Música e Hábitos de Audição.md]].

---

## ⚙️ Regras de Execução

1. **Gatilhos no Chat (Qualquer IDE / Antigravity / Codex / Claude):**
   - `sincronizar_lastfm`
   - `sync_lastfm`
   - `atualizar músicas`
   - `atualizar lastfm`

2. **Comando de Execução Direta:**
   ```powershell
   python Scripts/sync_lastfm.py
   ```

3. **Fluxo do Script:**
   - Carrega credenciais de `Scripts/.env` (`LASTFM_API_KEY`, `LASTFM_SHARED_SECRET`, `LASTFM_USER`).
   - Consulta o último timestamp (UTS) em `Fontes/lastfmstats-SirPulga.json`.
   - Faz a requisição paginada do delta para a API (`user.getRecentTracks` com `from=<UTS>`).
   - Grava de forma atômica o novo JSON atualizado.
   - Consulta o Top 10 de artistas e faixas dos últimos 7 dias (`period=7day`).
   - Atualiza a tabela consolidada e a seção semanal em [[André/Música e Hábitos de Audição.md]].

---

## 📋 Formato de Resposta Obrigatório no Chat
Após a execução de cada sincronização, a resposta ao usuário DEVE conter impreterivelmente:
1. **Resumo da Execução:** novos scrobbles, total consolidado e status do tracker da meta anual.
2. **Músicas Ouvidas no Dia:** listagem de todas as faixas reproduzidas na data corrente (00h00 até o momento atual).
3. **Músicas Ouvidas Desde a Última Sincronização:** listagem das faixas capturadas especificamente no delta desta execução.

