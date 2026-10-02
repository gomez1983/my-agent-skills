---
name: processar-nf
description: Executa a triagem e reconciliação contábil automatizada de notas fiscais e comprovantes em /Inbox/ via script python, lançando no Notion e arquivando no Drive. Use quando o usuário solicitar processar notas fiscais ou digitar 'processar_nf'.
---

# Prompt — Processamento de Notas Fiscais e Comprovantes

Instruções operacionais para a triagem autônoma, leitura multimodal e reconciliação contábil de documentos financeiros depositados em `/Inbox/`.

---

## 🎯 Objetivo
Automatizar a extração de dados contábeis de faturas, recibos e notas fiscais sem necessidade de renomeação manual prévia, efetuando o lançamento no banco de dados do Notion (`Finanças André - 2026`) e arquivando os arquivos na pasta física correta no Google Drive.

---

## ⚙️ Regras de Execução

1. **Leitura e Extração Multimodal:**
   - Varredura de arquivos nas extensões `.pdf`, `.png`, `.jpg`, `.jpeg` no diretório `/Inbox/`.
   - Extração via motor Google Gemini (`gemini-3.5-flash-lite`):
     - Razão Social / Nome Fantasia / Emissor.
     - Valor monetário nominal em centavos.
     - Data de vencimento ou emissão no padrão `YYYY-MM-DD`.
     - Identificação de fluxo: `entrada` (recebimento de salário da Prytter) ou `saida` (despesas e contas).

2. **Reconciliação De-Para:**
   - Consultar as regras da matriz [[Integrações Antigravity/Matriz de Reconciliação Contábil — De-Para.md]].
   - Para concessionárias e despesas recorrentes (Vivo Fibra, DAS MEI, Nubank, FAL, etc.), utilizar o nome padronizado e a respectiva categoria do Notion.

3. **Arquivamento Definitivo no Google Drive:**
   - Despesas: `d:\Google Drive\Meu Drive\Pessoal\Finanças\Contas\YYYY\NomeDoMes\`
   - Recebimentos Prytter: `d:\Google Drive\Meu Drive\Pessoal\Finanças\Salário\Notas Fiscais\YYYY\`
   - Renomeação padronizada no formato camelCase `nomeDoEstabelecimento_mesAno.ext`.

4. **Captura Automática do Link do Google Drive:**
   - O motor consulta a base local do Google Drive para Desktop (`%LOCALAPPDATA%\Google\DriveFS\*\mirror_metadata_sqlite.db`) para obter o `cloud_id` atribuído ao arquivo.
   - Gera o link canônico do Drive: `https://drive.google.com/open?id=<FILE_ID>&usp=drive_fs`.

5. **Alimentação do Notion via API:**
   - Conexão via `Scripts/.env` (`NOTION_API_KEY`).
   - Criação da página na base de **`Entrada`** (ID: `335f6d15-a91a-801d-9d29-c6ba086da0f1`) com link na propriedade `Arquivos e mídia`.
   - Criação da página na base de **`Saídas`** (ID: `335f6d15-a91a-80d8-9b50-ceb72c7ba398`) com link na propriedade `Comprovantes`.

6. **Sincronização Dupla com o Excel (Soberania de Dados):**
   - Ao concluir os lançamentos no Notion, o script aciona automaticamente `export_notion_finances_to_excel.py`.
   - A planilha `Pessoal\Finanças\Finanças André - 2026.xlsx` é imediatamente atualizada com as novas linhas, vínculos de comprovantes, cálculos e gráficos atualizados em todas as abas.

---

## 🚀 Como Executar

Para acionar a rotina diretamente:
```powershell
python Scripts/process_inbox_finances.py
```

Para simulação sem mover arquivos:
```powershell
python Scripts/process_inbox_finances.py --dry-run
```
