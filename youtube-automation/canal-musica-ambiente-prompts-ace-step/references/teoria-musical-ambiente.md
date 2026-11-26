# Teoria musical aplicada a ambient/foco (ACE-Step)

> Conteúdo adaptado e sintetizado a partir da skill de composição musical [`SJY051/music-composition`](https://github.com/SJY051/music-composition) (documentação sob licença CC BY 4.0), com foco específico no nicho deste canal: música ambiente instrumental para foco/relaxamento/sono, gerada com ACE-Step. Para teoria fora deste recorte, clone o repositório original e use `references/00-navigation.md` dele.

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
3. **Chorus/seção de destaque**: adiciona 1 camada melódica ou motívica discreta (sino, mallet, lead suave) — sem crescer em volume, só em interesse.
4. **Bridge/seção de respiro**: tira camadas, deixa mais vazio.
5. **Retorno**: traz de volta a textura principal, eventualmente reintroduzindo a camada melódica.
6. **Outro**: volta ao mínimo, final limpo (bom para loop/corte).

Dimensione a duração aparente de cada seção pela duração real da faixa (uma faixa de 5 min sustenta seções mais longas/repetidas que uma de 2 min).

## Regras ACE-Step específicas (recap)

- **Tags** = legenda curta (gênero, instrumentos, clima). Nunca bpm/escala/tempo aqui — isso vai nos widgets dedicados do node.
- **Letra** = `[instrumental]` + tags de seção + instrumentação em prosa. É aqui que a estrutura e o caráter modal/dinâmico da faixa são descritos.
- Não prometa precisão de compasso — o vocabulário de estrutura do ACE-Step é por seção, não por contagem de bars.
- `duration`/`seconds` é um alvo real que o modelo tenta cumprir (diferente do YuE2, que usava um teto de `max_duration`).

## Cross-reference

Para harmonia funcional, jazz, reharmonização, outros gêneros fora de ambient, ou crítica detalhada de uma composição existente, use a skill completa `music-composition` (ver link no topo deste arquivo) em vez de expandir este resumo.
