---
name: buscar-semantica
description: Executa a busca vetorial por afinidade conceitual e embeddings no cofre via script python, recuperando notas relevantes sem exigir termos exatos. Use sob o gatilho 'buscar_semantica' ou 'busca_vetorial'.
---

# Prompt — Busca Semântica no Vault (`buscar_semantica`)

Diretriz operacional e procedimento de recuperação de conhecimento por similaridade vetorial (Nível 3 do Second Brain) através do script `Scripts/vault_semantic_search.py`.

---

## 1. Propósito e Casos de Uso

A busca tradicional por texto exato ou grep falha quando o usuário não se lembra do título da nota, do nome exato de uma pessoa ou dos termos literais utilizados.

Este gatilho permite:
- **Resgatar Notas por Memória Vaga:** Ex.: *"onde anotei sobre finitude da vida e passagem do tempo"*.
- **Localizar Decisões Arquiteturais e Post-Mortems:** Ex.: *"qual foi o problema de arredondamento de dinheiro na concessionária"*.
- **Cruzar Conhecimentos:** Ex.: *"quais exercícios faço para membros superiores na academia"*.

---

## 2. Como a IA Executa a Busca

Ao receber o comando ou identificar a necessidade de busca por conceito:
1. Executa no terminal:
   ```powershell
   python "Scripts/vault_semantic_search.py" "<termo ou pergunta conceitual>"
   ```
2. O script consulta o índice em cache (`Scripts/.cache/semantic_index.json`), calcula a similaridade cosseno (0 a 100%) contra os embeddings gerados via `models/gemini-embedding-001` (3072 dimensões) e retorna as 5 notas mais próximas com trechos contextuais.
3. A IA lê os resultados, abre a nota relevante se necessário via wikilink e responde diretamente ao usuário.

---

## 3. Manutenção e Reindexação Incremental

- O script opera com **idempotência baseada em SHA-256**: notas inalteradas não consomem chamadas de API de embedding.
- Para forçar reindexação completa de todo o cofre:
  ```powershell
  python "Scripts/vault_semantic_search.py" --reindex
  ```

---

## 4. Referências e Conexões
- [[ROADMAP.md]] — Matriz Estratégica: Nível 3 (Busca Semântica).
- [[AGENTS.md]] — Seção 10 (Gatilhos Rápidos de Automação).
- [[Prompts/Índice de Prompts.md]] — Central de Skills.
