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

Dica prática: o campo "escala tonal" do ACE-Step aceita tônica + maior/menor (ex. `C major`, `A minor`). Para sugerir um modo (Dorian, Lydian etc.) sem widget dedicado de modo, escolha a tônica/maior-menor mais próxima e reforce o caráter modal na descrição em prosa do "Prompt da música" (ex. citar "a floating, major-but-unresolved quality" para Lydian, ou "a cool, static minor color" para Dorian) — o texto da letra é o que carrega a nuance modal real, o widget só define a tônica/modo-base.

## Groove e dinâmica

- Pulso mínimo ou ausente; quando houver, mantenha constante, sem variações bruscas, sem fills.
- Dinâmica deve ficar numa faixa estreita do início ao fim — mudanças de seção são **texturais** (camada entra/sai), não **energéticas** (sem "explosões"/drops).
- Seção mais "fria" de uma faixa (equivalente a uma ponte) deve tirar camadas, não baixar e depois disparar de volta com força.

## Arco de forma recomendado (para o "Prompt da música")

Use tags de seção reais que o ACE-Step reconhece — `[Intro]`, `[Verse]`, `[Chorus]`, `[Bridge]`, `[Breakdown]`, `[Outro]` — nunca contagem de compassos ("4 bars" etc.), que o modelo não executa literalmente. Dentro de cada seção, descreva em prosa:

1. **Intro**: textura mínima, só 1-2 elementos entrando devagar.
2. **Verse/seção principal**: camada principal estabelecida (pad/synth), movimento bem sutil.
3. **Chorus/seção de destaque**: adiciona 1 camada melódica/motívica discreta — **varie qual** (synth lead, corda com arco longo, piano felt, pad de sopro, textura granular) **a cada faixa do mesmo vídeo**. Nunca repita a mesma escolha (ex. sino/mallet/glockenspiel) em várias das 8 faixas — ver "Erro recorrente" abaixo.
4. **Bridge/seção de respiro**: tira camadas, deixa mais vazio.
5. **Retorno**: traz de volta a textura principal, eventualmente reintroduzindo a camada melódica.
6. **Outro**: volta ao mínimo, final limpo (bom para loop/corte).

Dimensione a duração aparente de cada seção pela duração real da faixa (uma faixa de 5 min sustenta seções mais longas/repetidas que uma de 2 min).

## Erro recorrente observado em testes reais — timbre "sino/shimmer" grudado a faixa inteira

Testado com o usuário: um lote de 8 faixas que usava palavras como "shimmer", "chime", "bell-like", "metallic resonance" (mesmo como "acento ocasional") saiu com esse timbre **tocando o tempo inteiro**, em quase todas as faixas, soando repetitivo e nada "inspirador". Causas identificadas (cruzadas com relatos públicos de prompting do ACE-Step):

- **Tags cheias de adjetivo/clima e pobres em instrumento concreto** ("calm, contemplative, slow-evolving, vast reverb...") fazem o modelo cair no "preenchimento genérico" do gênero — e esse preenchimento padrão de ambient/cinematic lento tende a ser exatamente um ornamento tipo sino/music-box/glockenspiel. Nomear poucos instrumentos concretos evita isso.
- **Uma palavra como "shimmer"/"chime"/"bell" no Tags ou repetida na Letra é tratada como característica da faixa inteira**, não como um acento pontual de uma seção — o modelo não tem como saber que era pra ser "só no chorus, de vez em quando". Se quiser um acento assim, ele deve aparecer **só na seção do Chorus em prosa**, nunca no campo Tags.
- **Tags de seção ([Verse]/[Chorus]/[Bridge]) sem instrumento nomeado** tendem a não mudar muito o timbre sozinhas — elas funcionam melhor quando a prosa de cada seção nomeia o que entra/sai (instrumento concreto), não só o clima.

**Regras daqui pra frente**:
1. No Tags, liste **4-6 instrumentos/fontes sonoras concretas** (ex. "analog synth pad, bowed cello drone, felt piano, tape texture") + BPM/gênero — minimize adjetivos soltos de clima/produção ("calm", "cinematic", "atmospheric" são aceitáveis em pequena dose, mas nunca a maioria das palavras do Tags).
2. Não repita a mesma palavra de "ornamento" (sino/chime/shimmer/glockenspiel/bell/music-box) em mais de **uma** das 8 faixas de um vídeo. Prefira variar entre: synth lead, corda, piano, sopro, textura granular/ruído, arpejo de synth modular — cada faixa com um "instrumento-âncora" diferente das outras.
3. Na Letra, prefira nomear instrumentos concretos entrando/saindo por seção ("piano enters alone", "cello drone joins underneath", "piano drops out") a parágrafos descritivos de clima/sensação sem instrumento nomeado.
4. Se usar uma palavra de textura como "shimmer"/"bell"/"chime" nesta faixa, ela só pode aparecer **uma vez**, dentro da seção específica onde deve soar (ex. só no Chorus), nunca no Tags e nunca repetida em Verse+Chorus+Bridge.

## Regras ACE-Step específicas (recap)

- **Tags** = legenda curta (gênero, instrumentos, clima). Nunca bpm/escala/tempo aqui — isso vai nos widgets dedicados do node.
- **Letra** = `[instrumental]` + tags de seção + instrumentação em prosa. É aqui que a estrutura e o caráter modal/dinâmico da faixa são descritos.
- Não prometa precisão de compasso — o vocabulário de estrutura do ACE-Step é por seção, não por contagem de bars.
- `duration`/`seconds` é um alvo real que o modelo tenta cumprir (diferente do YuE2, que usava um teto de `max_duration`).

## Cross-reference

Para harmonia funcional, jazz, reharmonização, outros gêneros fora de ambient, ou crítica detalhada de uma composição existente, use a skill completa `music-composition` (ver link no topo deste arquivo) em vez de expandir este resumo.
