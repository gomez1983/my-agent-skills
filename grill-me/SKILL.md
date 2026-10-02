---
name: grill-me
description: Conduz uma entrevista crítica implacável e alinhamento prévio antes de qualquer código ou implementação, gerando especificação técnica formal para a IDE Antigravity. Use sob os gatilhos 'grill_me' ou 'entrevistar'.
---

# Prompt — Alinhamento e Interrogatório Arquitetural (`grill_me` / `entrevistar`)

Diretriz operacional e protocolo de estresse prévio de requisitos, arquitetura e decisões de design inspirado na skill `grill-me` (Matt Pocock).

---

## 1. Propósito e Filosofia

O objetivo deste gatilho é **proibir a implementação prematura** (*vibe coding*). Antes de criar código, alterar esquemas de banco ou desenhar soluções complexas:
- A IA assume a postura de um arquiteto e revisor crítico.
- Conduz uma entrevista metódica percorrendo cada galho da árvore de decisões do projeto.
- Produz como artefato final uma especificação arquitetural executável (PRD / Especificação Técnica) salva em `/Projetos/<Nome_do_Projeto>/` para guiar a execução autônoma na IDE Antigravity ou em qualquer agente.

---

## 2. Regras de Conduta Durante a Entrevista

1. **Uma Pergunta por Vez:**
   - Nunca disparar questionários longos em bloco. Fazer uma (ou no máximo duas) perguntas encadeadas por rodada, explicando brevemente o trade-off técnico daquela escolha.
2. **Opções Pré-Formatadas com Recomendação:**
   - Sempre fornecer opções de escolha claras, apontando uma `(Recomendada)` com base nas boas práticas do projeto e na infraestrutura existente no vault.
   - Permitir que o usuário escolha uma opção ou responda livremente.
3. **Mapeamento de Pontas Soltas:**
   - Questionar critérios de sucesso, persistência de dados, dependências externas, tratamento de falhas e casos extremos (*edge cases*).
4. **Travamento de Código:**
   - Nenhuma linha de código ou arquivo final é gerado enquanto a entrevista não for dada como concluída pelo usuário.

---

## 3. Artefato Final Gerado: `Especificação Arquitetural e Plano de Execução`

Ao concluir o alinhamento, a IA gera autonomamente o arquivo:
`d:\Google Drive\Meu Drive\Pessoal\My Second Brain\Projetos\<Nome_do_Projeto>\Especificação — <Nome_do_Projeto>.md`

O documento segue o formato padronizado com:
1. **Visão Geral e Contexto:** O problema a ser resolvido e premissas validadas.
2. **Decisões Arquiteturais Fechadas:** Lista de escolhas feitas durante o `grill-me` (linguagens, bibliotecas, bancos, APIs).
3. **Casos Extremos & Segurança:** O que pode dar errado e como contornar.
4. **Plano de Execução Passo a Passo:** Checklist sequencial com arquivos a criar/modificar e comandos a rodar.

### Como a IDE Antigravity Executa o Plano:
Na IDE Antigravity (interface escura), basta abrir o workspace do projeto ou iniciar uma sessão dizendo:
> "Leia a especificação em `Projetos/<Nome_do_Projeto>/Especificação — <Nome_do_Projeto>.md` e execute a Fase 1."

A IDE lerá o plano estruturado e executará o código com precisão milimétrica, sem necessidade de reexplicar o contexto.

---

## 4. Referências e Conexões
- [[Prompts/Índice de Prompts.md]] — Catálogo de skills e comandos rápidos.
- [[AGENTS.md]] — Seção 8 (Sínteses e BPM) e Seção 10 (Gatilhos Rápidos).
- [[Integrações Antigravity/Segundo Cérebro para Agentes e IAs.md]] — Princípios de desacoplamento entre planejar e executar.
