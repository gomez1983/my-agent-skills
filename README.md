# 🧠 My Agent Skills (`my-agent-skills`)

Repositório central de **Skills para Agentes de IA** (compatível com Cursor, Antigravity, Claude Code e runtime de agentes em IDEs).

Este repositório reúne tanto as **skills multi-stack e autônomas do Second Brain** quanto as skills especializadas extraídas de projetos reais (Java/Spring Boot, Flutter/Dart/IoT, etc.).

---

## 📂 Catálogo de Skills Disponíveis

| Skill | Escopo / Finalidade | Stack Principal |
| :--- | :--- | :--- |
| [`auditoria-codigo`](./auditoria-codigo) | **Skill Mestre Multi-Stack** para auditoria de segurança, detecção de segredos no Git, integridade de DTOs, WebSockets, permissões e geração de patches em diff. | Java/Spring Boot, Flutter, React, APIs |
| [`security-audit-spring`](./security-audit-spring) | Auditoria defensiva especializada para APIs corporativas em Java 21 e Spring Boot 3 (JPA, Mass Assignment, RFC 7807, BigDecimal). | Spring Boot 3, Java 21, MySQL |
| [`security-audit-flutter`](./security-audit-flutter) | Auditoria defensiva para Smart Remote e IoT (WebSockets LG/Samsung, SSDP/WoL, AndroidManifest, secure storage). | Flutter, Dart, Android, Windows |
| [`grill-me`](./grill-me) | Protocolo de entrevista implacável e alinhamento prévio antes de codificar, gerando especificação técnica formal. | Agnóstico / Engenharia de Software |
| [`processar-inbox`](./processar-inbox) | Triagem polimórfica autônoma de arquivos (separação fiscal Notion/Drive e notas atômicas no Obsidian). | Python, Notion API, Multimodal |
| [`processar-nf`](./processar-nf) | Reconciliação contábil automatizada de notas fiscais com categorização De-Para e lançamento em planilhas. | Python, OCR/Multimodal, Excel |
| [`auditoria-vault`](./auditoria-vault) | Rotina de vigilância, saúde do grafo e integridade de links no Obsidian. | Obsidian, Dataview, Python |
| [`buscar-semantica`](./buscar-semantica) | Recuperação de notas por afinidade conceitual e embeddings no cofre. | Python, Embeddings, Vetorial |
| [`sincronizar-lastfm`](./sincronizar-lastfm) | Sincronização delta e consolidação semanal de telemetria musical via API. | Python, Last.fm API |
| [`baixar-video`](./baixar-video) | Download de vídeos em alta resolução e extração de áudio MP3 de múltiplas plataformas. | Python, yt-dlp, ffmpeg |
| [`aprimorar-imagem`](./aprimorar-imagem) | Síntese e restauração com pós-processamento local. | Python, API de Imagens |
| [`aprimorar-flux`](./aprimorar-flux) | Restauração fotográfica com reconstrução dérmica e microporos via Fal.ai FLUX.1 [dev]. | Python, Fal.ai FLUX.1 |
| [`aprimorar-gemini`](./aprimorar-gemini) | Realce cromático e reconstituição multimodal via Google Gemini Images API. | Python, Gemini API |

---

## 🚀 Como Usar em Novos Projetos

Ao iniciar qualquer projeto em qualquer IDE (Cursor, Antigravity ou IntelliJ), você pode simplesmente instruir o seu assistente:

```text
Baixe e configure a skill 'auditoria-codigo' deste repositório para a pasta .agents/skills/ deste projeto:
https://github.com/gomez1983/my-agent-skills/tree/main/auditoria-codigo
```

Ou clonar diretamente o repositório como submódulo / referência de consulta:

```bash
git clone https://github.com/gomez1983/my-agent-skills.git
```

---

## 🛡️ Padrão de Estrutura de Cada Skill

Cada pasta de skill segue rigorosamente a especificação de agentes:
- `SKILL.md`: Instruções centrais com frontmatter YAML (`name`, `description`) e regras de ativação.
- `refs/` ou scripts de apoio: Manuais detalhados, checklists por stack e templates de relatórios.
- **Princípio Fundamental:** Nenhuma modificação automática em código de produção sem aprovação humana expressa (propostas sempre em diff `before/after`).
