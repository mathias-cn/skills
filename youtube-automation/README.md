# youtube-automation

Skills para planejar e automatizar canais de YouTube (identidade de canal, ideias de vídeo, prompts para geração de música/imagem/animação por IA).

## Skills disponíveis

| Skill | O que faz |
|---|---|
| [`canal-youtube-musica-ambiente`](canal-youtube-musica-ambiente/SKILL.md) | Cria a identidade visual e musical de um canal de música ambiente (foco, relax, estudo, flowstate, sono) e gera sugestões completas de vídeo: thumbnail/imagem (estática ou com prompt de animação em loop), título, descrição, character sheet do personagem principal e prompts de música para o YuE2 (ComfyUI). |
| [`canal-musica-ambiente-prompts-ace-step`](canal-musica-ambiente-prompts-ace-step/SKILL.md) | Gera, música por música, o prompt estruturado (tags + letra), bpm, escala tonal, compasso e duração para as 8 músicas-base do workflow ACE-Step 1.5 (ComfyUI) do canal de música ambiente, com base em teoria musical aplicada a ambient/foco. |

## Instalar só este segmento

```bash
npx skills add mathias-cn/skills/youtube-automation/canal-youtube-musica-ambiente
npx skills add mathias-cn/skills/youtube-automation/canal-musica-ambiente-prompts-ace-step
```

Veja o [README principal](../README.md) para as outras formas de instalação.
