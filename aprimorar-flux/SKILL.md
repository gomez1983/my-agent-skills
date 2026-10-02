---
name: aprimorar-flux
description: Executa restauração fotográfica e síntese de micro-textura dérmica e têxtil via API FLUX.1 [dev] no Fal.ai via script python. Use sob o gatilho 'aprimorar_flux'.
---

# Prompt — Aprimoramento e Reconstrução FLUX.1 [dev]

Prompt parametrizado para o modelo FLUX.1 [dev] via Fal.ai focado em máxima preservação de identidade fisionômica, anatomia e trajes, combinada com reconstrução fotorrealista de microtexturas de pele e tecido em alta definição.

---

## Conteúdo do Prompt

```text
RAW authentic 35mm master photograph, hyper-realistic human skin texture with razor-sharp epidermal pores, organic micro-dermal relief, natural subtle blemishes, and fine freckles. Realistic beach photoshoot specular sheen: authentic tanning oil highlights on collarbones, shoulders, and cleavage, zero plastic, zero waxy flat skin. Intense expressive eyes with crisp dark eyeliner, separated sharp eyelashes, and glassy specular reflections in the iris. Dynamic hair rendering with crisp individual flyaway strands catching natural warm sunlight. Sharp metallic specular gleam on jewelry, rings, chains, and accessories. Crisp tactile textile weave faithful to original fabric. Balanced warm golden hour contrast, clean optical focus.
```

---

## Parâmetros Padrão de Execução (Clarity Diffusion Upscaler)

- **Script:** `Scripts/flux_enhance.py`
- **Resolução Mínima:** `>= 2000px` na menor dimensão (fator de escala automático)
- **Creativity (Denoising):** `0.60` (síntese profunda de microporos, sardas e textura orgânica)
- **Resemblance (ControlNet):** `0.50` (preservação de fisionomia e proporções originais)
- **Guidance Scale:** `6.0`
- **Negative Prompt:** `plastic skin, smooth skin, airbrushed, porcelain skin, waxy skin, doll skin, filtered, beauty filter, soft focus, blur, digital painting, cgi, 3d render, cartoon, oversmoothed, flat texture`
- **Safety Checker:** `False`
- **Output Format:** `jpeg`

---

## Conexões
- Central de Prompts: [[Prompts/Índice de Prompts]]
- Documentação da API: [[Integrações Antigravity/Integração FLUX via Fal.ai]]
- Regras Operacionais do Assistente: [[AGENTS.md]]
