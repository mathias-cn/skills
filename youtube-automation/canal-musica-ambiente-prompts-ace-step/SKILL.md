---
name: canal-musica-ambiente-prompts-ace-step
description: Use quando o usuário quiser gerar os prompts de música (tags, letra/prompt estruturado, bpm, escala tonal, compasso, duração) para as 8 músicas-base do workflow ACE-Step 1.5 (ComfyUI) do canal de YouTube de música ambiente/foco — em qualquer gênero musical, não só ambient. Pergunta estilo/gênero, se já existe um definido, e a duração do vídeo antes de gerar.
metadata:
  language: pt-BR
  version: "1.1"
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

1. **Estilo/gênero**: pergunte se o usuário já tem um estilo definido para este vídeo, ou se quer criar um novo agora. Se nada for dito, assuma a identidade já estabelecida do canal (ambient minimalista/drone, synth pads com melodias "inspiradoras", estética brutalista, instrumental, sem vocais/bateria) e pergunte só se este vídeo específico quer uma variação de tema (ex.: "sono profundo" vs "foco intenso" vs "relaxamento"). Mas esta skill **não está limitada a ambient** — se o usuário pedir um gênero diferente (lo-fi, piano clássico, synthwave, jazz instrumental, música regional etc.), siga normalmente usando a seção "Qual referência de teoria musical usar" abaixo para decidir a fonte certa.
2. **Duração do vídeo**: pergunte quantas horas/minutos o vídeo deve ter.
3. **Calcule a duração por faixa**:
   ```
   segundos_por_faixa = (duração_do_vídeo_em_minutos * 60) / 24
   ```
   Informe o resultado ao usuário antes de gerar os prompts (ex.: vídeo de 2h → 7200s / 24 = 300s = 5 min por faixa). Esse valor vai para a `Duracao` das 8 músicas.
4. **Gere as 8 músicas**, uma de cada vez ou todas juntas (pergunte a preferência se não ficar claro), seguindo as seções "Qual referência de teoria musical usar" e "Regras ACE-Step específicas" abaixo.
5. Devolva no formato exato da seção "Formato de saída".

## Qual referência de teoria musical usar

Esta skill não escreve teoria musical do zero — ela **adapta e formata** o que uma referência de teoria diz para os campos do ACE-Step. Escolha a fonte pelo gênero/estilo definido no passo 1:

- **Ambient/drone/foco (identidade padrão do canal, ou qualquer variação próxima dela)**: use `references/teoria-musical-ambiente.md` deste diretório — já é o recorte certo (bpm, modos, arco de dinâmica) para este caso, carregue só ele.
- **Qualquer outro gênero/estilo** (lo-fi, piano clássico, synthwave, jazz, música regional, trilha de cena, etc.): use a skill completa `music-composition`, vendorizada em `../../musica/music-composition/` deste mesmo repositório (fork verbatim de `SJY051/music-composition`, CC BY 4.0 — ver `VENDORED-FROM.md` lá dentro). Siga o processo dela:
  1. Leia `../../musica/music-composition/SKILL.md` e depois `references/00-navigation.md` para achar os arquivos certos (ela mesma indica, pela pergunta do usuário e pelo gênero, quais 1-3 arquivos carregar — não carregue mais que isso).
  2. Carregue também o arquivo de gênero correspondente em `references/genres/` (ex. `jazz-styles.md`, `pop-rock.md`, `electronic-edm.md`) — a própria skill reforça isso.
  3. Extraia dali decisões concretas: tonalidade/modo, faixa de bpm, instrumentação idiomática do gênero, e um arco de forma/dinâmica (ex. `form/popular-song-forms.md`, `form/narrative-and-transitions.md`, `production-aware/energy-and-dynamics.md`).
  4. **Adapte essas decisões para o ACE-Step** usando as regras da seção "Regras ACE-Step específicas" abaixo — isso é o que esta skill faz que a `music-composition` sozinha não faz (ela não conhece o ACE-Step nem os campos tags/letra/bpm/escala/compasso/duração do nosso workflow).

Para as 8 músicas de um mesmo vídeo, varie levemente bpm e escala/modo entre elas (dentro do estilo escolhido) para não soar repetitivo, mantendo a mesma "família sonora" ao longo do vídeo.

## Regras ACE-Step específicas (aplicam-se a qualquer gênero)

- **Tags** = legenda curta (gênero, instrumentos, clima). Nunca escala/tempo-texto aqui, **mas o BPM numérico pode e deve ir no final das Tags também** (ex. `..., 58 bpm`), além do widget `Bpm` — reforça a aderência de tempo no ACE-Step (ver "Formato padrão atual" em `references/teoria-musical-ambiente.md`).
- **Letra**: para gêneros **calmos/ambient/foco/cinematic underscore** (a maioria dos pedidos deste canal), o padrão validado é **marcadores minúsculos colados sem espaço**: `[intro][inst][inst][outro]` (2-3× `[inst]` para ~5 min, menos para faixas curtas) — nada de tags de seção maiúsculas nem prosa. Três iterações anteriores (Tags com adjetivo de clima + prosa por seção; troca de instrumentos mantendo a prosa) foram testadas e reprovadas pelo usuário em geração real; não volte a isso sem pedido explícito. Para outros gêneros com progressão real (ex. jazz com forma, pop/rock, trilha com builds), tags de seção (`[Intro]`, `[Verse]`, `[Chorus]`, `[Bridge]`, `[Outro]`) + prosa continuam sendo o caminho, seguindo a referência de gênero escolhida. Nunca prometa precisão de compasso (ex. "4 bars") — o ACE-Step não executa isso literalmente.
- `duration`/`seconds` é um alvo real que o modelo tenta cumprir (diferente do YuE2, que usava um teto de `max_duration`).
- **Evite timbre repetitivo/"mush" genérico** (testado em produção, 3 iterações, confirmado por relatos públicos de prompting do ACE-Step): a Tags precisa ter **5-12 tags no total** (nem menos nem mais — dilui), cada uma concreta e qualificada (`soft felt piano`, não só `piano`) — nunca só adjetivo de clima solto. Varie os instrumentos/texturas entre as 8 músicas de um vídeo; nunca repita a mesma palavra de ornamento (sino/chime/shimmer/glockenspiel) em mais de uma faixa; evite `epic`/`driving`/`cinematic trailer`/`energetic` e qualquer par de tags contraditório (`lo-fi`+`hi-fi`, `energetic`+`meditative`).

Resumo de onde cada coisa vai (combinando a referência escolhida acima com as regras ACE-Step):

- **Tags (estilo)**: para ambient/foco/cinematic calmo, a lista densa de 5-12 tags descrita em `teoria-musical-ambiente.md`, terminando no BPM numérico (ex. `space ambient, deep focus, deep sub drone, bowed double bass, vast reverb, beatless, no drums, no vocals, 58 bpm`); para outros gêneros, frase curta com gênero + instrumentos + clima no vocabulário que a referência escolhida sugerir (ex. jazz instrumental: `smooth modal jazz, upright bass, brushed drums, Rhodes piano, late-night lounge, instrumental`).
- **Prompt da musica (letra)**: para ambient/foco/cinematic calmo, **apenas `[intro][inst][inst][outro]`** (padrão validado — ver acima); para outros gêneros, seções reais + instrumentação em prosa, seguindo o arco de forma/dinâmica que a referência indicou (builds/drops, refrões mais fortes etc. onde for idiomático — não force a filosofia "ambient" em um gênero que pede contraste).
- **Bpm / Escala Tonal**: dentro da faixa e tonalidade/modo que a referência escolhida sugeriu para o gênero.
- **Compasso**: `4` na grande maioria dos casos; só fuja disso se o gênero/pedido do usuário pedir explicitamente um compasso incomum (valsa, odd meter etc.) e o combo do node suportar.
- **Duracao**: sempre o valor calculado no passo 3 do fluxo (igual nas 8 músicas, pela limitação técnica já descrita).

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
