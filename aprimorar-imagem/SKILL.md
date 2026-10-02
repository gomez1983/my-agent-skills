---
name: aprimorar-imagem
description: Executa restauração e aprimoramento de imagem via API de geração de imagem com pós-processamento local, salvando em Saída de Mídia. Use sob o gatilho 'aprimorar'.
---

# Prompt — Aprimoramento e Reconstrução de Imagem

Prompt parametrizado para restauração, recuperação de micro-detalhes e síntese de textura fotorrealista a partir de imagens de baixa resolução ou comprimidas.

---

## Conteúdo do Prompt

```text
Ultra-premium optical image restoration and true-to-source enhancement. Professional studio photograph with clean optical clarity. Recover authentic fine details: sharp facial features, smooth natural skin texture with subtle fine pores and soft specular highlights, crisp individual hair strands, and precise edges. Strictly maintain original fabric and materials: preserve the exact original smooth swimwear fabric, zero woven patterns, zero waffle or mesh texture, zero added fabric relief. Strictly maintain 100% geometric and spatial pose lock: identical posture, hand positions, fingers, anatomy, and composition without deviation. Absolute true-to-source fidelity: zero redesign of clothing, accessories, or background. Balanced natural contrast, zero plastic smoothing, zero artificial noise, zero coarse grain. Keep the subject and materials completely identical to the reference image.
```

---

## Formas de Execução Automática

1. **Invocação Direta pelo Assistente:**
   - Anexe a imagem neste chat e instrua: `Aplique o [[Prompt - Aprimoramento de Imagem]] nesta imagem`. O assistente lê a nota diretamente no vault e executa o processamento sem necessidade de colar o texto.

2. **Inserção via Plugin Core Templates (Modelos) do Obsidian:**
   - Configure a pasta `Prompts` como repositório de templates nas preferências do Obsidian (*Configurações > Modelos / Templates*).
   - Use o comando `Inserir Modelo` (`Ctrl/Cmd + P` ou atalho dedicado) para injetar o texto no cursor.

3. **Transclusão em Notas:**
   - Em qualquer nota de documentação ou registro, utilize `![[Prompt - Aprimoramento de Imagem#Conteúdo do Prompt]]` para embutir o bloco de texto sem duplicar conteúdo.
