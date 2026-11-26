---
name: canal-musica-ambiente-prompts-ace-step
description: Use quando o usuário quiser gerar os prompts de música (tags, letra/prompt estruturado, bpm, escala tonal, compasso, duração) para as 8 músicas-base do workflow ACE-Step 1.5 (ComfyUI) do canal de YouTube de música ambiente/foco. Pergunta se já existe um estilo definido e a duração do vídeo antes de gerar.
metadata:
  language: pt-BR
  version: "1.0"
---

# Gerador de prompts ACE-Step para o canal de música ambiente

Esta skill gera, pronto para colar no ComfyUI, o conteúdo das 8 músicas-base do workflow **"Canal YouTube Musica Ambiente - 5 Musicas (ACE-Step).json"**: a tag (estilo), o prompt estruturado (letra), e os parâmetros bpm/escala tonal/compasso/duração de cada uma.

Ela é complementar à skill `canal-youtube-musica-ambiente` (que define a identidade do canal e sugere vídeos inteiros) — esta skill foca só na etapa de **escrever as 8 músicas de um vídeo específico**, já com conhecimento de teoria musical aplicada ao ACE-Step.

## Arquitetura do workflow (contexto necessário antes de gerar qualquer coisa)

O workflow tem **8 nós "ACE-Step Generate Music - musica N de 8"** independentes. Cada um:
- recebe tags de uma caixa **"Tags (estilo) - musica N de 8"** (texto curto: gênero/instrumentos/clima — nunca bpm/escala/tempo aqui);
- recebe a letra de uma caixa **"Prompt da musica - musica N de 8"** (o prompt estruturado por seções);
- tem seus próprios widgets **bpm, duração, compasso (timesignature), idioma, escala tonal (keyscale)**.

Um loop aninhado roda cada uma das 8 músicas **3 vezes** (seeds diferentes a cada repetição) = **24 faixas por vídeo**. Isso é fixo na estrutura do workflow — não dá para gerar mais ou menos de 8 músicas-base sem editar o workflow em si (avise o usuário se ele quiser isso).

**Limitação técnica importante**: o nó que define o tamanho do áudio gerado ("Empty ACE-Step 1.5 Latent Audio") é único e compartilhado pelas 24 faixas. Por isso, **a duração (`duration`) precisa ser a MESMA nas 8 músicas** — não dá pra variar de verdade entre 4 e 5 minutos por faixa hoje. Sempre calcule UM valor de duração e use nas 8. (Se o usuário quiser duração realmente diferente por música, isso exigiria uma extensão do workflow — avise e pergunte antes de prosseguir, não implemente por conta própria.)

## Fluxo da conversa

Siga esta ordem, uma pergunta de cada vez:

1. **Estilo**: pergunte se o usuário já tem um estilo definido para este vídeo/canal, ou se quer criar um novo agora. Se o canal já tem identidade estabelecida (ambient minimalista/drone, synth pads com melodias "inspiradoras", estética brutalista, instrumental, sem vocais/bateria), use isso como base por padrão e pergunte só se este vídeo específico quer uma variação de tema (ex.: "sono profundo" vs "foco intenso" vs "relaxamento").
2. **Duração do vídeo**: pergunte quantas horas/minutos o vídeo deve ter.
3. **Calcule a duração por faixa**:
   ```
   segundos_por_faixa = (duração_do_vídeo_em_minutos * 60) / 24
   ```
   Informe o resultado ao usuário antes de gerar os prompts (ex.: vídeo de 2h → 7200s / 24 = 300s = 5 min por faixa). Esse valor vai para a `Duracao` das 8 músicas.
4. **Gere as 8 músicas**, uma de cada vez ou todas juntas (pergunte a preferência se não ficar claro), seguindo a seção "Como escrever cada música" abaixo.
5. Devolva no formato exato da seção "Formato de saída".

## Como escrever cada música

Para cada uma das 8 músicas, consulte `references/teoria-musical-ambiente.md` (teoria musical aplicada a ambient/foco, com matriz de bpm/escala/modo) antes de decidir bpm, escala tonal e o arco de seções. Varie levemente bpm e escala/modo entre as 8 músicas (dentro da identidade do canal) para o vídeo não soar repetitivo, mas mantenha a mesma "família sonora".

**Tags (estilo)**: uma frase curta com gênero + instrumentos + clima + palavras-chave de "sem vocal/bateria" (ex.: `minimalist ambient drone, warm analog synth pads, slow evolving texture, calm, focused, instrumental, no vocals, no drums, no percussion`). Nunca inclua bpm, escala ou compasso aqui — isso vai nos campos dedicados.

**Prompt da musica (letra)**: comece com `[instrumental]`. Depois, estruture por seções usando as tags reais que o ACE-Step reconhece (`[Intro]`, `[Verse]`, `[Chorus]`, `[Bridge]`, `[Breakdown]`, `[Outro]` — não use contagem de compassos tipo "4 bars", o modelo não executa isso literalmente). Dentro de cada seção, descreva em prosa a instrumentação e o que entra/sai, seguindo a filosofia: introduzir elementos aos poucos, dinâmica estável/sem picos, tirar camadas na seção mais "fria" em vez de dar uma guinada dramática, final limpo. Dimensione o número e duração aparente das seções para a duração real da faixa (uma faixa de 5 min pede seções mais longas/mais repetidas que uma de 2 min).

**Bpm / Escala Tonal / Compasso**: escolha com base em `references/teoria-musical-ambiente.md`. Compasso quase sempre `4` para este gênero, a menos que o usuário peça algo incomum.

**Duracao**: sempre o valor calculado no passo 3 (igual nas 8 músicas).

## Consultando teoria musical mais a fundo

`references/teoria-musical-ambiente.md` cobre o que basta para 95% dos casos deste canal (ambient/drone, modos, bpm, arco de dinâmica). Se o usuário pedir algo fora disso (ex.: harmonia jazz, um gênero bem diferente, reharmonização, crítica detalhada de uma composição), existe a skill completa de composição musical em `github.com/SJY051/music-composition` (licença CC BY 4.0 para o conteúdo) — clone-a (`git clone https://github.com/SJY051/music-composition`) e leia `references/00-navigation.md` dela para achar o arquivo certo, carregando só 1-3 arquivos relevantes, nunca o repositório inteiro.

## Formato de saída

Depois de calcular tudo, devolva exatamente neste formato, uma vez por música (substitua N de 1 a 8):

```
MÚSICA N:

Prompt da música:
[PROMPT AJUSTADO AQUI]

Tags + Style:
Tags (estilo) - [tags curtas: gênero/instrumentos/clima]
Bpm - [BPM]
Escala Tonal - [Escala Tonal]
Compasso - [Formula de Compasso]
Duracao - [Duracao em segundos, igual nas 8]
```

Ao final das 8, lembre o usuário de colar cada bloco no node correspondente ("Tags (estilo) - musica N de 8", "Prompt da musica - musica N de 8", e os widgets do node "ACE-Step Generate Music - musica N de 8") e que a `Duracao` também precisa bater com o `seconds` do node "Empty ACE-Step 1.5 Latent Audio" (compartilhado pelas 24 faixas).
