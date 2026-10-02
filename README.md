# 🛡️ My Agent Skills (`my-agent-skills`)

Repositório central de **Skills Autônomas de Auditoria de Código e Segurança** para Agentes de IA (compatível com Cursor, Antigravity, Claude Code e IDEs de desenvolvimento).

Diferente de scripts locais que dependem de bancos de dados ou chaves de terceiros, estas skills são **100% autônomas (standalone)**: fornecem heurísticas, roteiros de *taint analysis*, checklists arquiteturais e filtros anti-falso-positivo diretamente para a cognição da IA.

---

## 📂 Catálogo de Skills Portáteis

| Skill | Descrição e Escopo | Tecnologias Cobertas |
| :--- | :--- | :--- |
| [`auditoria-codigo`](./auditoria-codigo) | **Skill Mestre Consolidada (Multi-Stack):** Fluxo unificado em 8 passos, análise de dependências reais via lockfiles, rastreamento de fluxo de dados, busca de segredos no Git, validação de permissões de plataforma e propostas de correção estritamente em formato diff (`before/after`). | Java/Spring Boot, Flutter/Dart, React/TypeScript, APIs REST |
| [`security-audit-spring`](./security-audit-spring) | **Auditoria para APIs Spring Boot 3 & Java 21:** Foco em Spring Data JPA, prevenção de Mass Assignment em `@RequestBody`, Bean Validation (`@Valid`), RFC 7807 (*Problem Details*), integridade monetária com `BigDecimal` e persistência mandatória de relatórios em `docs/security/audits/`. | Java 21, Spring Boot 3, Hibernate, MySQL |
| [`security-audit-flutter`](./security-audit-flutter) | **Auditoria para Mobile & IoT (Smart Remote):** Foco em aplicações cliente para Smart TVs (LG webOS e Samsung Tizen), conexões WebSocket locais, broadcast SSDP/UDP, pacotes mágicos Wake-on-LAN, permissões no `AndroidManifest.xml` e armazenamento seguro (`flutter_secure_storage`). | Flutter, Dart, Android, Windows |

---

## 🚀 Como Usar em Qualquer Projeto

Ao abrir um projeto novo em qualquer IDE (Cursor, Antigravity ou IntelliJ), você pode instruir o assistente no chat:

### Opção 1: Utilizando a Skill Mestre Unificada (Recomendado)
```text
Baixe e configure a skill 'auditoria-codigo' deste repositório para a pasta .agents/skills/ deste projeto:
https://github.com/gomez1983/my-agent-skills/tree/main/auditoria-codigo
```

### Opção 2: Utilizando a Skill Específica da Stack
- **Para projetos Spring Boot / Java:**
  ```text
  Baixe e configure a skill da pasta security-audit-spring de:
  https://github.com/gomez1983/my-agent-skills/tree/main/security-audit-spring
  ```
- **Para projetos Flutter / IoT:**
  ```text
  Baixe e configure a skill da pasta security-audit-flutter de:
  https://github.com/gomez1983/my-agent-skills/tree/main/security-audit-flutter
  ```

---

## 🛡️ Princípios Invioláveis das Skills

1. **Versão Instalada > Última Lançada:** Inspeciona os arquivos de bloqueio reais (`pom.xml`, `pubspec.lock`, `package-lock.json`). Versão defasada sem CVE/Advisory explorável é tratada apenas como `INFO`.
2. **Evidência Real e Contexto de Hardware:** Reconhece restrições de ambiente (como certificados autoassinados da LG na porta 3001 ou tráfego HTTP local da Samsung na porta 8001) para eliminar falsos positivos.
3. **Nenhuma Alteração Automática:** O código de produção nunca é alterado sem autorização. Todas as correções para itens críticos ou de alta gravidade são apresentadas como sugestões em diff (`before/after`).
