---
name: processar-inbox
description: Executa a triagem polimórfica de arquivos depositados em /Inbox/ (separando documentos fiscais para Notion/Drive e materiais de áudio/texto para síntese no Obsidian com wikilinks). Use quando o usuário digitar 'processar_inbox', 'triagem' ou solicitar organização da caixa de entrada.
---

# Prompt — Processamento e Triagem de Inbox (`processar_inbox`)

Diretriz operacional e técnica para varredura, transcrição multimodal, síntese de conhecimento e arquivamento autônomo de arquivos brutos depositados na pasta `/Inbox/`.

---

## 1. Visão Geral e Propósito

O gatilho `processar_inbox` (ou `triagem`) implementa a função de **"Bibliotecário Autônomo"** do Segundo Cérebro. 

Ele permite que o usuário deposite qualquer material bruto (anotações rápidas em texto, áudios de reuniões, ligações gravadas, links soltos ou rascunhos) dentro de `/Inbox/` sem se preocupar com categorização, tags ou wikilinks. Ao acionar o comando, a IA assume a curadoria completa da informação.

---

## 2. Tipos de Mídia Aceitos e Roteamento

| Tipo de Arquivo | Extensões | Pipeline de Execução | Destino Final |
| :--- | :--- | :--- | :--- |
| **Documentos Contábeis / Fiscais** | `.pdf`, `.png`, `.jpg`, `.jpeg` (comprovantes, faturas, guias, notas) | Pipeline Contábil (`process_inbox_finances.py`) + API Notion + Matriz De-Para + Sincronização Excel | Notion (`Entrada`/`Saídas`), Google Drive (`Pessoal\Finanças\Contas\` ou `Pessoal\Finanças\Salário\`) e Planilha Excel (`Pessoal\Finanças\Finanças André - 2026.xlsx`) |
| **Áudio** | `.m4a`, `.mp3`, `.wav`, `.ogg`, `.3gp` | Conversão via FFmpeg (quando necessário) + Transcrição multimodal Gemini | Obsidian (`/André/`, `/Projetos/`, etc.) |
| **Texto / Rascunho** | `.txt`, `.md` | Leitura direta do sistema de arquivos e síntese de tópicos | Obsidian (`/André/`, `/Projetos/`, etc.) |
| **Links / Referências** | URLs em arquivos `.txt` ou `.md` | Extração de conteúdo via navegação web e síntese de conceitos | Obsidian (`/Fontes/` ou notas de tema) |

---

## 3. Passo a Passo do Algoritmo de Execução

Ao receber o comando `processar_inbox` no chat:

### Passo 1: Varredura e Classificação Polimórfica da Caixa de Entrada
1. Inspecionar o diretório `d:\Google Drive\Meu Drive\Pessoal\My Second Brain\Inbox\`.
2. Ignorar o arquivo de sistema `README.md`.
3. Se a pasta estiver vazia (apenas o README), reportar imediatamente que a caixa de entrada está limpa.
4. Mapear e segregar os arquivos presentes entre:
   - **Lote Contábil/Financeiro:** Arquivos `.pdf`, `.png`, `.jpg`, `.jpeg` que representem faturas, recibos, cupons, boletos ou notas fiscais.
   - **Lote de Conhecimento/Segundo Cérebro:** Arquivos de áudio, textos brutos, notas e links soltos.

### Passo 2: Processamento do Lote Contábil/Financeiro
Caso existam documentos contábeis no Inbox:
1. Disparar autonomamente o motor de reconciliação financeira:
   ```powershell
   python Scripts/process_inbox_finances.py
   ```
2. O script analisa o documento com o Gemini, consulta a matriz De-Para, efetua o lançamento oficial no banco de dados do Notion (`Finanças André - 2026`), renomeia o arquivo físico transferindo-o para a pasta correta no Google Drive (`Pessoal\Finanças\Contas\` ou `Pessoal\Finanças\Salário\Notas Fiscais\`) e aciona automaticamente a atualização da planilha soberana em `Pessoal\Finanças\Finanças André - 2026.xlsx`.
3. O arquivo contábil é retirado do `/Inbox/` sem poluir as notas do Obsidian.

### Passo 3: Processamento do Lote de Conhecimento (Obsidian)
- **Se for arquivo de áudio:**
  1. Verificar se o formato necessita de normalização (ex.: contêineres 3GP de gravação telefônica são convertidos para MP3 mono 16kHz via FFmpeg).
  2. Fazer upload do arquivo de áudio para a API do Google Gemini via `google.genai`.
  3. Aguardar o status `ACTIVE` do arquivo.
  4. Disparar a extração com o prompt mestre:
     - Identificação de participantes e interlocutores.
     - Resumo executivo dos objetivos e acordos.
     - Tópicos detalhados (valores, datas, pendências, requisitos burocráticos).
     - Transcrição literal integral dos diálogos.
- **Se for arquivo de texto/rascunho:**
  1. Ler o conteúdo textual bruto.
  2. Identificar o tema principal e os conceitos-chave.

### Passo 4: Identificação da Pasta de Destino no Grafo (Sem notas soltas)
A IA determina autonomamente a pasta correta para as notas de conhecimento, evitando notas soltas em pastas-raiz:
- **Reuniões e Alinhamentos Corporativos da Prytter:** `/André/Carreira/Prytter/Reuniões/`.
- **Conversas Informais e Diálogos com Amigos:** `/André/Conversas entre Amigos/` ou subpastas temáticas dedicadas.
- **Pessoal / Saúde / Carreira Geral:** `/André/<Subpasta_Temática>/`.
- **Projetos Específicos / Negócios:** `/Projetos/<Nome_do_Projeto>/`.
- **Ferramentas de Desenvolvimento e Editores:** `/IDE's/<Nome_da_Ferramenta>/`.
- **Documentos Imutáveis / Referências Externas:** `/Fontes/`.

### Passo 5: Formatação e Conexões do Grafo (Wikilinks)
Criar a nota permanente no destino com:
- Frontmatter padronizado contendo obrigatoriamente:
  - `tags`, `cssclass: ai-note`, `status: ativo`, `tipo: sintese`, `contexto`.
  - `horario_reuniao` ou `horario_gravacao` no formato `HH:MM` (além de `created` e `updated`).
- Cabeçalho de Metadados logo abaixo do título:
  - `> **Origem:** Gravação de Áudio (<nome_arquivo>).`
  - `> **Data:** DD/MM/AAAA às HH:MM.`
  - `> **Duração:** X min Y s.`
  - `> **Participantes:** Interlocutores da conversa com wikilinks.`
  - `> **Pessoas Mencionadas:** Pessoas citadas com wikilinks.`
  - `> **Conexões do Grafo:** Wikilinks bidirecionais relevantes.`
- Síntese estruturada em tom direto e coloquial (sem formalismos excessivos em conversas de amigos/trabalho), tópicos práticos e transcrição integral literal recolhível em Callout Nativo do Obsidian (`> [!NOTE]-`).

### Passo 6: Limpeza do Inbox e Registro Operacional
1. Excluir os arquivos brutos de conhecimento já processados de `/Inbox/`, mantendo a caixa de entrada 100% limpa.
2. Registrar a operação completa no `Daily Logs/YYYY-MM-DD-log.md` com os metadados de conclusão e arquivos afetados.

---

## 4. Prompt Mestre Utilizado para Transcrição e Síntese Multimodal

```markdown
Você é um assistente de transcrição e síntese documental de alta precisão.
Analise o material fornecido na íntegra.

Entregue:
1. Resumo executivo claro dos principais pontos tratados (participantes identificáveis, contexto, objetivo, decisões e desfechos).
2. Tópicos detalhados enumerando fatos, valores, protocolos, prazos, solicitações ou dados acordados.
3. Transcrição integral e literal fiel das falas dos interlocutores.

Estruture em formato Markdown claro e profissional, em Português do Brasil.
```

---

## 5. Referências e Conexões
- [[Prompts/Índice de Prompts.md]] — Catálogo central de prompts e gatilhos.
- [[AGENTS.md]] — Seção 1 (Governança do Inbox) e Seção 10 (Gatilhos Rápidos).
- [[Integrações Antigravity/Protocolo de Heartbeat e Vigilância.md]] — Rotina de vigilância automática do Inbox.
