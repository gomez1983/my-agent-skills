---
name: baixar-video
description: Baixa vídeos em alta resolução ou extrai áudios em MP3 do YouTube, TikTok, Instagram, Twitter/X e plataformas web usando script python, salvando em Downloads/Saída de Mídia/. Use sob 'baixar_video' ou 'baixar_audio'.
---

# Prompt — Download Universal de Vídeos e Mídias

Habilidade oficial para baixar vídeos, reels, tiktoks, documentários, aulas, trilhas e referências do **YouTube, TikTok, Instagram, Twitter/X, Facebook, Twitch, Reddit, Vimeo** e mais de 1.000 sites compatíveis diretamente para o seu repositório local.

---

## 1. Como Usar no Chat

Basta enviar o comando acompanhado de qualquer URL:

1. **Download do Vídeo em MP4 (qualidade máxima disponível):**
   ```text
   baixar_video https://www.youtube.com/watch?v=EXEMPLO
   baixar_video https://www.tiktok.com/@usuario/video/123456789
   baixar_video https://www.instagram.com/reel/EXEMPLO/
   baixar_video https://x.com/usuario/status/123456789
   ```

2. **Download em Resolução Específica (ex.: 1080p, 720p):**
   ```text
   baixar_video https://www.youtube.com/watch?v=EXEMPLO qualidade:1080p
   ```

3. **Extrair Apenas o Áudio (MP3):**
   ```text
   baixar_audio https://www.youtube.com/watch?v=EXEMPLO
   ```

---

## 2. Destino e Organização dos Arquivos

- **Vídeos:** Salvos em `C:\Users\andre\Downloads\Saída de Mídia\Vídeos\`
- **Áudios:** Salvos em `C:\Users\andre\Downloads\Saída de Mídia\Áudios\`
- **Execução Automática da IA:**
  O assistente aciona internamente:
  ```powershell
  python Scripts/download_video.py "<URL>"
  ```

---

## 3. Conexões com o Vault
- Referência canônica: [[Prompts/Automação e Operações/Prompt - Download de Vídeos.md]]
- Diretório de saída: `Downloads/Saída de Mídia/`

