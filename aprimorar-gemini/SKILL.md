---
name: aprimorar-gemini
description: Executa realce cromático vívido e restauração multimodal via Google Gemini Images API via script python. Use sob o gatilho 'aprimorar_gemini'.
---

# Prompt — Aprimoramento e Reconstrução Gemini Images

Prompt parametrizado para o motor multimodal de geração e aprimoramento de imagem do Google Gemini (Gemini Images), focado em restauração de alta fidelidade óptica, reconstituição biológica de microporos dérmicos, equilíbrio cromático vibrante e preservação estrita de identidade facial, anatomia e trajes.

---

## Conteúdo do Prompt

```text
High-fidelity optical image restoration and photographic enhancement. Preserve 100% strict identity, facial geometry, eye expression, gaze, posture, body anatomy, clothing structure, and composition from the reference image. Reconstruct authentic biological human skin texture with razor-sharp micro-pores, natural epidermal relief, subtle freckles, and organic imperfections, avoiding any plastic, waxy, or airbrushed smoothing. Dynamic lighting with warm golden tones, natural specular highlights on collarbones, shoulders, and décolletage resembling authentic photoshoot sheen. Crisp, vibrant color fidelity: rich saturated textile tones, accurate fabric ribbing and weave, sharp metallic reflections on jewelry, accessories, and clean specular glass reflection in the irises. Ultra-clean optical sharpness with zero digital artifacts, zero noise distortion, and pristine studio clarity.
```

---

## Parâmetros Padrão de Execução

- **Script de Orquestração:** `Scripts/gemini_enhance.py`
- **Chave de API:** `Scripts/.env` (`GEMINI_API_KEY`)
- **Modelos Primários:** `gemini-3.1-flash-image` (Nano Banana 2) / `gemini-2.5-flash-image` (Nano Banana)
- **Modalidade de Resposta:** `responseModalities: ["IMAGE"]`
- **Preservação de Fisionomia:** 100% de correspondência fisionômica e geométrica
- **Diretório de Saída:** `Downloads\Imagens Aprimoradas\` (resolvido automaticamente para o usuário atual)
- **Formato de Saída:** `JPEG` de alta qualidade

---

## Formas de Execução Automática

1. **Gatilho Rápido no Chat:**
   - Anexe a imagem e envie a palavra-chave: `aprimorar_gemini`.
   - O assistente executa o script autônomo com as diretrizes desta nota e salva a imagem gerada na pasta de destino.

2. **Linha de Comando (Manual):**
   ```powershell
   python Scripts/gemini_enhance.py "caminho_da_imagem.jpg" "texto_do_prompt"
   ```

---

## Conexões
- Central de Prompts: [[Prompts/Índice de Prompts]]
- Documentação Técnica: [[Integrações Antigravity/Integração Gemini Images API]]
- Regras Operacionais do Assistente: [[AGENTS.md]]
