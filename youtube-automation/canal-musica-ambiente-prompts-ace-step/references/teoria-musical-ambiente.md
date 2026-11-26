# Teoria musical aplicada a ambient/foco (ACE-Step)

> Conteúdo adaptado e sintetizado a partir da skill de composição musical [`SJY051/music-composition`](https://github.com/SJY051/music-composition) (documentação sob licença CC BY 4.0), com foco específico no nicho deste canal: música ambiente instrumental para foco/relaxamento/sono, gerada com ACE-Step. Para qualquer outro gênero, use a skill completa vendorizada em `../../../musica/music-composition/` (ver `SKILL.md` do pacote de prompts ACE-Step, seção "Qual referência de teoria musical usar").

## O gênero: ambient / drone contemplativo

Ambient é música pensada para ser ouvida de forma periférica — atmosfera antes de ritmo. Características centrais: sem batida marcada (ou muito lenta/quase ausente), pads e drones sustentados, texturas que evoluem devagar, peças longas, e o desenho espacial (reverb, delay, panning) como parte do conteúdo musical, não só "produção". Variações relevantes para o canal:
- **Drone**: sustentado, evolução muito lenta — ótimo para "sono"/"deep focus".
- **New age**: mais melódico, levemente mais "guiado" — ótimo para "foco produtivo".
- **Ambient técnico**: elementos rítmicos discretos e repetitivos (sem virar dança) — ótimo para "flowstate".

**Erro comum a evitar**: aplicar estrutura de música pop ou EDM (build→drop, grandes contrastes dinâmicos) a uma peça ambient. Uma faixa de 5 minutos pode sustentar uma única ideia por muito tempo — isso é intencional, não um defeito.

## BPM — faixa de referência

BPM em ambient é mais "pulso sentido" do que andamento dançável:

| Intenção da faixa | BPM sugerido |
|---|---|
| Drone muito profundo / sono | 40-55 |
| Foco contemplativo (padrão do canal) | 55-70 |
| Foco mais "ativo"/produtivo, flowstate | 68-82 |

Varie o BPM entre as 8 músicas de um mesmo vídeo dentro de uma faixa estreita (ex.: 58-72) para dar variedade sem quebrar a coerência sonora do vídeo.

## Escala/modo — qual usar e por quê

Harmonia modal (centro tonal por repetição/drone, não por cadência V→I) é a base natural de ambient. Não é preciso nomear acordes no prompt — basta escolher o modo certo para a "escala tonal" do node e deixar a cor dele guiar a descrição em prosa.

| Modo | Caráter | Quando usar no canal |
|---|---|---|
| **Lydian** (ex. `C Lydian` / `F Lydian`) | Flutuante, expansivo, "admiração" | Faixas de "pensamento profundo"/inspiração — combina com o conceito visual de "O Pensador" |
| **Dorian** (ex. `D Dorian`) | Frio, ambíguo, maduro, estável | Opção "padrão" segura para a maioria das faixas de foco |
| **Aeolian / natural minor** (ex. `A minor`) | Reflexivo, introspectivo | Faixas mais "quietas"/noturnas, sono |
| **Mixolydian** | Levemente mais quente/aberto, sem tensão de dominante | Variação sutil para não repetir sempre Dorian/Aeolian |
| Evitar: Phrygian, Locrian | Tensos, instáveis, "sombrios" | Só se o usuário pedir deliberadamente uma faixa mais inquietante (incomum neste canal) |

Dica prática: o campo "escala tonal" do ACE-Step aceita tônica + maior/menor (ex. `C major`, `A minor`). Para sugerir um modo (Dorian, Lydian etc.) sem widget dedicado de modo, escolha a tônica/maior-menor mais próxima; o caráter modal (ex. "floating" para Lydian, "cool/static" para Dorian) pode aparecer como 1 palavra isolada no Tags (ver fórmula abaixo), mas não é mais descrito em prosa — ver "Formato padrão atual" abaixo.

## Groove e dinâmica

- Pulso mínimo ou ausente; quando houver, mantenha constante, sem variações bruscas, sem fills.
- Dinâmica deve ficar numa faixa estreita do início ao fim — sem "explosões"/drops, sem builds de energia.

## Formato padrão atual (validado com o usuário, 2ª iteração) — Tags densa + Letra mínima

**Histórico rápido**: três iterações foram testadas em geração real. (1) Tags cheia de adjetivo de clima + Letra em prosa por seção → saiu repetitivo, com um ornamento (sino/shimmer) grudado na faixa inteira. (2) Trocar os instrumentos mas manter a Letra em prosa por seção → ainda não ficou bom. (3) O usuário então forneceu a fórmula abaixo (baseada em prática real com ACE-Step/ACE Studio) como o formato definitivo a partir de agora. Não volte às versões (1)/(2) a menos que o usuário peça explicitamente para testar de novo.

**A partir de agora, o padrão é**:
- **Letra ("Prompt da música") = só marcadores de estrutura em minúsculo, colados sem espaço**: `[intro][inst][inst][outro]` (2-3× `[inst]` para uma faixa de ~5 min; menos `[inst]` para faixas mais curtas). Nada de `[Verse]`/`[Chorus]`/prosa — essa é a sintaxe específica do ACE-Step/ACE Studio para instrumental puro.
- **Tags (estilo) = uma única lista densa, separada por vírgula**, com **5 a 12 tags no total** (nem menos nem mais — tags demais diluem umas às outras), construída nesta ordem (4 blocos + BPM, sem rotular os blocos no texto final):
  1. **Estilo + Função**: ex. `space ambient`, `dark ambient`, `cinematic ambient`, `minimalist`, `deep focus`.
  2. **Elementos + Textura**: 2-4 instrumentos/fontes sonoras **concretas e qualificadas** (não genéricas) — ex. `soft felt piano` (não só `piano`), `deep sub drone`, `bowed cello drone`, `subtle granular texture`, `warm sustained strings`, `distant synth swells`, `evolving synth pads`, `vast/wide reverb`.
  3. **Ritmo + Energia/Restrição**: `beatless`, `slow pacing`, `no drums`, `no percussion`, `no vocals` — só o essencial (2-4 tags, não precisa repetir sinônimos de restrição).
  4. **BPM numérico ao final**, ex. `58 bpm` — **além** do widget `Bpm` do node (reforça a aderência de tempo), sempre igual ao valor do widget.

**Evite nas Tags**: `epic`, `driving`, `cinematic trailer`, `energetic`, e **qualquer par de tags contraditório** (ex. `lo-fi` + `hi-fi`, `energetic` + `meditative`). Se mesmo assim a IA acelerar ou meter batida, reforce `beatless`/`no drums`.

**O que varia entre as 8 faixas do mesmo vídeo**: o bloco 2 (Elementos + Textura) — cada faixa com um par de instrumentos-âncora diferente — e o bloco 1 (Estilo + Função) pode alternar entre as 3 sub-variações do gênero (space ambient / cinematic minimalist / dark ambient underscore). O BPM varia faixa a faixa (dentro de 55-70, ver tabela acima) e precisa bater com o widget. O bloco 3 (ritmo/restrição) fica praticamente idêntico nas 8 — intencional, mantém a identidade sonora do vídeo.

**Exemplos de referência (fornecidos pelo usuário, usar como modelo literal de tom/vocabulário e de estrutura)**:
- Tags: `space ambient, dark ambient, evolving synth pads, deep sub drone, subtle granular texture, vast reverb, beatless, no drums, no percussion, no vocals, 60 bpm` · Letra: `[intro][inst][outro]`
- Tags: `cinematic ambient, minimalist, soft felt piano, warm sustained strings, subtle tape texture, wide stereo, slow pacing, no drums, no vocals, 65 bpm` · Letra: `[intro][inst][inst][outro]`

## Regras ACE-Step específicas (recap)

- **Tags** = a lista densa de 5-12 tags descrita acima (estilo+função, elementos+textura qualificada, ritmo/restrição, BPM numérico ao final). O BPM aqui é além do widget, não em vez dele.
- **Letra** = marcadores minúsculos colados `[intro][inst][inst][outro]` (ajustar nº de `[inst]` à duração), no formato padrão atual (ver acima). Só use tags de seção (`[Intro]`/`[Verse]`/`[Chorus]`/`[Bridge]`/`[Outro]`) + prosa se o usuário pedir explicitamente para testar essa variação de novo.
- Não prometa precisão de compasso — o ACE-Step não executa contagem de bars.
- `duration`/`seconds` é um alvo real que o modelo tenta cumprir (diferente do YuE2, que usava um teto de `max_duration`).

## Cross-reference

Para harmonia funcional, jazz, reharmonização, outros gêneros fora de ambient, ou crítica detalhada de uma composição existente, use a skill completa `music-composition` (ver link no topo deste arquivo) em vez de expandir este resumo.
