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

**Histórico rápido**: duas iterações anteriores foram testadas e **reprovadas pelo usuário em geração real**: (1) um lote com Tags cheia de adjetivo de clima + Letra em prosa estruturada por seção saiu repetitivo, com um ornamento (sino/shimmer) grudado na faixa inteira; (2) mesmo depois de trocar os instrumentos e manter a Letra em prosa por seção, o resultado ainda não ficou bom. O usuário então forneceu a fórmula abaixo (baseada em prática real com IAs generativas de música) como o formato a seguir **a partir de agora por padrão**. Não volte à prosa estruturada por seção a menos que o usuário peça explicitamente para testar isso de novo.

**A partir de agora, o padrão é**:
- **Letra ("Prompt da música") = apenas `[instrumental]`.** Nada de tags de seção, nada de prosa de instrumentação. Simples assim.
- **Tags (estilo) = uma única lista densa, separada por vírgula**, construída nesta ordem (4 blocos, sem rotular os blocos no texto final — é só a ordem de composição):
  1. **Estilo + Função**: ex. `deep space ambient`, `minimalist cinematic ambient`, `dark ambient cinematic underscore`, `atmospheric cinematic instrumental`, `deep focus`.
  2. **Elementos + Textura**: 3-5 instrumentos/fontes sonoras **concretas** (não adjetivos soltos) — ex. `warm evolving synth pads`, `deep sub drone`, `soft felt piano notes`, `subtle granular texture`, `bowed cello`, `sparse plucked guitar`, `distant synth swells`, `vast hall/cathedral reverb`.
  3. **Ritmo + Energia**: `slow tempo`/`slow pacing`, `beatless`, `low energy`, `meditative`, `hypnotic` ou `calm`/`peaceful`/`moody` (escolha 1-2, não os três).
  4. **Restrição** (sempre as mesmas, em todas as 8 faixas do vídeo): `no drums`, `no percussion`, `no vocals`, `no sudden drops`, `no energetic build-up`, `instrumental only`.

**Evite nas Tags**: `epic`, `driving`, `cinematic trailer`, `energetic` — e qualquer palavra que sugira clímax/ação (puxa o modelo para fora do foco calmo). Se mesmo assim a IA acelerar ou meter batida, reforce ainda mais `beatless`, `no drums`, `slow movement`.

**O que varia entre as 8 faixas do mesmo vídeo**: só o bloco 2 (Elementos + Textura) — cada faixa com um par/trio de instrumentos-âncora diferente (ex. synth pad + cello numa, felt piano + brass pad noutra, drone + synth sequencer noutra) — e o bloco 1 (Estilo + Função) pode variar entre as 3 sub-variações do gênero (deep space ambient / cinematic introspective minimal / dark & moody focus). Os blocos 3 e 4 (ritmo/restrição) ficam praticamente **idênticos** nas 8 — isso é intencional, é o que mantém a identidade sonora do vídeo e trava o modelo fora de bateria/vocais/drops.

**Exemplos de referência (fornecidos pelo usuário, usar como modelo literal de tom/vocabulário)**:
- `Deep space ambient, dark atmospheric pads, slow evolving drones, subtle granular textures, vast hall reverb, beatless, no drums, no percussion, no vocals, calm, hypnotic, deep focus, instrumental`
- `Minimalist cinematic ambient, soft felt piano, warm sustained strings, gentle tape texture, spacious reverb, slow pacing, no drums, no sudden changes, introspective, peaceful, instrumental only`
- `Dark ambient cinematic underscore, deep low-end drone, eerie distant synth swells, sparse atmospheric plucks, heavy reverb, no beat, no percussion, no vocals, moody, focused, instrumental`

## Regras ACE-Step específicas (recap)

- **Tags** = a lista densa de 4 blocos descrita acima (estilo+função, elementos+textura, ritmo+energia, restrição). Nunca bpm/escala/tempo numérico aqui — isso vai nos widgets dedicados do node.
- **Letra** = `[instrumental]`, só isso, no formato padrão atual (ver acima). Só use tags de seção (`[Intro]`/`[Verse]`/`[Chorus]`/`[Bridge]`/`[Outro]`) + prosa se o usuário pedir explicitamente para testar essa variação de novo.
- Não prometa precisão de compasso — o vocabulário de estrutura do ACE-Step (quando usado) é por seção, não por contagem de bars.
- `duration`/`seconds` é um alvo real que o modelo tenta cumprir (diferente do YuE2, que usava um teto de `max_duration`).

## Cross-reference

Para harmonia funcional, jazz, reharmonização, outros gêneros fora de ambient, ou crítica detalhada de uma composição existente, use a skill completa `music-composition` (ver link no topo deste arquivo) em vez de expandir este resumo.
