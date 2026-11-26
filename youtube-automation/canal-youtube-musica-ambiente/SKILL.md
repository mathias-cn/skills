---
name: canal-youtube-musica-ambiente
description: Use quando o usuário quiser criar identidade e gerar ideias de vídeo (thumbnail, título, descrição, prompts de música para YuE2/ComfyUI, prompts de imagem/animação, e character sheet do personagem principal) para um canal de YouTube de música ambiente (foco, relax, estudo, flowstate, sono).
metadata:
  language: pt-BR
  version: "1.0"
---

# Gerador de identidade e vídeos para canal de música ambiente no YouTube

Esta skill ajuda o usuário a planejar um canal de YouTube do nicho "horas de música" (foco, relaxamento, estudo, flowstate, sono etc.), produzido com ComfyUI + YuE2 para a música. O fluxo tem duas fases: (1) definir a identidade do canal, (2) gerar 5 sugestões de vídeo completas.

## Arquétipos de referência (calibração, não copiar)

Estes 7 canais reais foram analisados diretamente (perfil, about, últimos vídeos, thumbnails e descrições completas). Use-os como régua de qualidade e para inspirar perguntas/sugestões. **Nunca reproduza um design ou personagem protegido exato** — dois dos exemplos abaixo usam mascotes/personagens de altíssimo reconhecimento (um gato em estilo visual inspirado em Tom & Jerry; a própria "Lofi Girl", um dos personagens mais reconhecíveis do YouTube). Ao sugerir algo parecido para o usuário, crie sempre um personagem/mascote **original**, nunca o personagem protegido em si.

1. **Minimalismo estoico/foco** (ex. canal "Stoic State") — avatar: busto/estátua de mármore clássica. Thumbnails **estáticas**: fundo preto, uma única cena de mármore/escultura por vídeo (mãos estilo "Criação de Adão" segurando fone de ouvido, busto usando fone, mãos segurando uma ampulheta), tipografia bold sem serifa em minúsculas, frase curta terminada em ponto final ("godlike focus.", "flowstate.", "lock in."). Títulos: "[N hour] playlist to [verbo] [benefício]" ou "music to [enter/get] [estado mental]" ("2 hour playlist to unlock godlike focus."). Duração ~2h. Descrição: citação filosófica + ensaio de 4-5 parágrafos + CTA de inscrição.
2. **Jazz noir com mascote** (ex. canal "Tom's Jazz Lounge") — avatar: mascote detetive em círculo vermelho/preto. Thumbnails **estáticas**: fundo vermelho sólido, mesmo mascote em poses diferentes, texto "JAZZ NOIR" grande em serifa. Títulos: "[Frase de efeito] -- [descritor de gênero]" ("A Beautiful Kind of Trouble -- Dark Jazz | Late Night Noir"). Duração ~2h. Descrição: narrativa curta com emojis + link Spotify + CTA.
3. **Lofi medieval** (ex. canal "Quest & Rest") — avatar: lua crescente. Thumbnails **com leve animação/loop** (chuva, fogueira tremulando) e texto animado sobreposto na própria tela: pixel art em alta resolução, cavaleiro **deitado/descansando** em cenários variados. Títulos com reticências, 2ª pessoa ("The castle is calling... but the rain says stay"). Duração longa: **~8 horas**. Descrição: boas-vindas calorosa em 2ª pessoa + crédito de autoria + copyright.
4. **Pós-apocalíptico atmosférico** (ex. canal "Lemuria") — avatar: soldado com máscara de gás em P&B. Thumbnails **estáticas**: pintura/aquarela em duotone (cinza, verde tóxico, vermelho+ciano), figuras isoladas. Títulos: "[Frase de impacto completa]｜[Gênero]" com barra vertical fullwidth "｜" ("Until the last breath.｜Dark Military Atmosphere"). Duração ~1h-1h30. Descrição: citação itálico-unicode + links + **tracklist com timestamps e nomes individuais de faixa** + crédito da arte + 15-18 hashtags.
5. **Clássico sombrio/orquestral** (ex. canal "Villain's Symphony") — avatar: violino com asas de morcego. Thumbnails **estáticas**, cinematic/pintura realista: retrato solítário de um único músico (esqueleto tocando violoncelo, violinista encapuzado, rei decadente tocando alaude) em ambiente gótico à luz de velas, tons quentes contra fundo escuro. Títulos: "Dark Classical Music for [personagem/arquétipo] | [subtítulo evocativo]" ("Dark Classical Music for the Grim Reaper | When Death Plays the Cello"). Duração ~2h. Descrição: estilo "manifesto" longo — parágrafos poeticos, lista de frases imperativas curtas ("Write the story no one else could finish."), uso declarado (writing/studying/RPG), menciona **"coleções" temáticas nomeadas** (sub-séries dentro do canal, ex. "Fallen Crowns", "The Gothic Court"), bloco grande de keywords soltas separadas por vírgula, hashtags no início e no fim.
6. **Multi-“rádio” por humor/sub-gênero** (ex. canal "Lofi Girl" — **personagem protegida, nunca copiar**; use só a estrutura) — em vez de um único estilo, o canal mantém várias transmissões/uploads paralelos, cada um com seu próprio nicho dentro do mesmo guarda-chuva visual (lofi hip hop, lofi jazz, lofi medieval, lofi sintetizado para dormir etc.). Fórmula de título repetível: "[gênero/mood] radio [emoji] [beats/music] to [verbo]/[verbo] to" ("lofi hip hop radio 📚 beats to relax/study to", "medieval lofi radio 🏰 beats to scribe manuscripts to"). Útil como inspiração para o usuário criar **várias vertentes/títulos dentro do mesmo canal**, cada uma mirando um sub-nicho.
7. **Cyberpunk urbano chuvoso, animado em loop** (ex. canal "Shibuya After Rain") — avatar: letreiro de neon. Thumbnails **claramente animadas/loop**: render 3D cinematográfico de uma vista de sacada/varanda sobre uma cidade neon (estilo Tokyo/Shibuya) à noite, chuva caindo (linhas de movimento visíveis), luzes de neon roxas/violeta refletidas nas ruas molhadas, câmera estática mas cena viva (chuva, luzes piscando, vapor). Títulos seguem um **template fixo com slots variáveis**: "Shibuya After Dark – Lofi Rain & [variação de cenário/vista] for [benefício/mood] | 4K" publicado quase diariamente trocando só a parte variável ("...& Amber Balcony Views for Study, Focus and Slow Nights | 4K", "...& Midnight Railways for Dreams and Gentle Inspiration | 4K"). Duração ~3h. Descrição: bloco com emojis em lista ("This video is perfect for: ☕ Studying... 🌙 Late-night work..."), CTA explícito de like/subscribe/comentário, hashtags, e um grande despejo de keywords SEO separadas por vírgula no final (sem frases, só termos de busca repetidos com variações).

Padrão comum a todos: identidade visual muito consistente vídeo a vídeo, títulos seguindo sempre a mesma fórmula/template, vídeos de "horas de música", e no YouTube Studio esses vídeos aparecem rotulados "Criado com IA" (conteúdo sintético/alterado) — ao publicar, o usuário deve ativar essa divulgação no YouTube Studio. **A duração-alvo varia MUITO entre canais (de ~1h a ~8h)** — nunca assuma "1 hora" como padrão fixo; pergunte ao usuário qual duração ele quer mirar. **Alguns canais usam imagem 100% estática (arquétipos 1, 2, 4, 5), outros usam loop animado (arquétipos 3 e 7 claramente; QuestNRest também tem texto animado sobreposto)** — pergunte ao usuário qual dos dois formatos ele quer antes da Fase 2, pois isso muda os prompts que a skill precisa entregar.

## Fase 1 — Definir a identidade do canal

Primeiro, pergunte ao usuário (uma pergunta objetiva):

> "Você já tem a identidade visual e o gênero musical do seu canal definidos, ou quer montar isso agora comigo?"

### Caminho A — já tem identidade pronta

Peça que ele descreva o canal cobrindo os mesmos elementos analisados nos arquétipos acima:
- Tema/conceito central do canal
- Gênero e subgênero musical (para o prompt do YuE2)
- Instrumentação típica
- Mood/atmosfera
- Paleta de cores e estilo visual (fundo, ilustração, fotografia, pixel art, 3D, etc.)
- Presença ou não de um personagem/mascote recorrente (sempre original) — se sim, ver seção "Personagem principal e Character Sheet" abaixo
- **Imagem estática ou loop animado?** (se animado: que tipo de movimento — chuva, fogo, fumaça, luzes piscando, parallax sutil, etc.)
- Padrão de título (estrutura, tom, se tem sufixo de gênero, se usa um template fixo com slots variáveis como o arquétipo 7)
- Idioma dos títulos/descrições
- Duração-alvo por vídeo (1h? 2h? 3h? um mix de 8h+?)
- Formato de descrição desejado (tracklist com timestamps, narrativa curta, texto reflexivo, manifesto/coleções temáticas, checklist de emojis + SEO dump, ou mensagem fixa de boas-vindas)

Se o usuário deixar qualquer um desses pontos vago, pergunte especificamente por ele antes de seguir — não preencha lacunas com suposições, pois isso gera sugestões genéricas demais.

### Caminho B — construir junto

Faça **uma pergunta por vez**, sempre oferecendo 3-4 sugestões concretas baseadas na resposta anterior (pode usar AskUserQuestion quando disponível). Ordem sugerida:

1. **Propósito/vibe**: para que uso o ouvinte vai usar o canal? (foco/trabalho, estudar, relaxar, dormir, flowstate/produtividade, gaming ambiente, etc.)
2. **Gênero musical**: com base na resposta 1, sugira 3-4 gêneros/subgêneros coerentes.
3. **Tema/universo visual**: sugira temas que combinem com o gênero escolhido (estoicismo/filosofia, fantasia medieval, cyberpunk chuvoso, pós-apocalíptico, noir/detetive, clássico sombrio/gótico, natureza/floresta, espaço, etc.)
4. **Estilo de arte**: pixel art, pintura digital/aquarela, render 3D cinematográfico, minimalismo fotográfico, ilustração vetorial flat, anime/mangá etc. — sugerido conforme o tema.
5. **Estático ou animado em loop?**: perguntar diretamente. Cenários com elementos naturais em movimento (chuva, fogo, fumaça, neon piscando, folhas caindo) combinam melhor com loop animado (como os arquétipos 3 e 7); retratos/composições simétricas de impacto combinam melhor com estático (como os arquétipos 1, 2, 4, 5).
6. **Paleta de cores**: 2-3 opções coerentes com tema+estilo.
7. **Mascote/personagem (opcional)**: perguntar se querem uma figura recorrente (original, nunca uma IP de terceiros) ou só cenários/objetos. Se sim, seguir a seção "Personagem principal e Character Sheet" abaixo para gerar o prompt da folha de referência.
8. **Padrão de título**: mostrar 2-3 exemplos de estrutura coerentes com tudo que foi definido (inspirados nos 7 arquétipos acima) e deixar o usuário escolher ou ajustar. Perguntar se ele quer um template fixo com slot variável (estilo arquétipo 7, útil para publicar com frequência) ou títulos mais únicos por vídeo. Perguntar também se o canal vai ter **texto embutido na própria imagem** (thumbnail e/ou imagem de fundo do vídeo) — como nos arquétipos 1 (frase curta em minúsculas, bold sem serifa, ex. "flowstate.") e 2 ("JAZZ NOIR" em serifa grande); os arquétipos 4, 5, 6 e 7 **não** usam texto na imagem, só no título do vídeo, então isso não é obrigatório. Se sim, definir junto: a frase/palavra exata (geralmente a mesma do final do título, ou uma citação curta), o estilo de fonte (bold sans-serif minúsculo, serifa de impacto, manuscrita etc.), a posição (centralizado, rodapé, topo) e a cor/contraste — ver seção "Texto na imagem" abaixo.
9. **Idioma**: inglês (mercado maior) ou português/outro.
10. **Duração-alvo por vídeo**: pergunte diretamente (1h, 2h, 3h ou um mix longo de 8h+).
11. **Formato da descrição**: sugerir com base nos 7 estilos observados (tracklist nomeada, narrativa curta, texto reflexivo, manifesto com coleções, checklist+SEO dump, ou boas-vindas fixa). Se optar por tracklist, cada faixa da Fase 2 precisa de nome próprio.
12. **Nome do canal**: só depois de tudo acima definido (tema, gênero, mascote, idioma), sugira 5-8 opções de nome coerentes com a identidade montada, no mesmo espírito curto/evocativo dos arquétipos de referência (ex. "Stoic State", "Quest & Rest", "Lemuria", "Villain's Symphony", "Shibuya After Rain") — nunca nomes genéricos tipo "Lofi Music Channel". Deixe o usuário escolher um, pedir mais opções, ou informar que já tem nome definido.

Ao fim, resuma a identidade consolidada (incluindo o nome escolhido) em um bloco curto antes de passar para a Fase 2, e confirme com o usuário.

## Personagem principal e Character Sheet (se houver mascote)

Se o canal tem (ou vai ter) um personagem/mascote recorrente, pergunte:

> "Você já tem esse personagem definido/desenhado, ou quer que eu monte a descrição dele com você agora?"

- **Se já tem**: peça para descrever (espécie/forma, roupa/acessórios fixos, paleta de cores, expressão/personalidade visual, qualquer traço distintivo). Se o usuário já tiver imagens dele, avise que pode carregá-las direto nos nodes "Imagem de referência 1/2/3" do grupo Character Sheet no ComfyUI.
- **Se não tem**: construa a descrição junto, uma pergunta por vez, coerente com o tema/estilo visual já definidos na Fase 1 (espécie/forma do personagem, roupa/acessórios, paleta, expressão).

Com a descrição fechada, monte um **prompt de character sheet** pronto para colar no node "Character Sheet - Prompt" do workflow do ComfyUI, seguindo sempre esta estrutura (fundo branco, múltiplos ângulos, igual a uma folha de referência de personagem/lookbook):

> `character reference sheet, turnaround sheet, consistent character design, same outfit and facial features in every view, clean pure white background, studio lighting, fashion lookbook photography style, large full body front view, full body side profile view, full body back view, two close-up face portrait crops, [descrição específica do personagem: espécie/forma, roupa, cores, acessórios, expressão], high detail, no text, no watermark`

Explique ao usuário que, no ComfyUI, esse grupo "Character Sheet": (1) roda só com esse prompt se ele não tiver imagens de referência, ou (2) usa imagens de referência (se ele carregar 1-3 fotos/desenhos do personagem e marcar o checkbox "Usar imagem de referência?") para manter a aparência consistente. A imagem final dessa folha alimenta automaticamente os checkboxes "Usar imagem de referência?" dos grupos de Thumbnail e de Foto de Perfil do YouTube no mesmo workflow — assim o personagem aparece consistente em thumbnails e na foto de perfil do canal.

Se o usuário não tiver personagem recorrente, pule esta seção normalmente (nem toda identidade de canal precisa de mascote — ver arquétipos 1, 4 e 5).

## Texto na imagem (thumbnail e imagem do vídeo), se o canal usar

Quando a Fase 1 definir que o canal usa texto embutido na imagem (arquétipos 1 e 2 são a referência — ex. "flowstate." em bold minúsculo sobre o busto de mármore, ou "JAZZ NOIR" em serifa grande sobre fundo vermelho), esse texto **aparece na imagem gerada em si**, tanto na thumbnail quanto na imagem de fundo usada durante o vídeo (normalmente é o mesmo prompt/imagem para os dois — ver Fase 2). Não é um overlay separado feito depois: o texto entra diretamente no prompt de imagem do Krea-2.

O Krea-2 usado no workflow é baseado em Qwen-Image, um modelo bem acima da média em renderizar texto legível dentro da imagem — mas a precisão cai conforme a frase cresce. Ao escrever qualquer prompt de imagem para um canal que usa texto:
- Escreva a frase exata entre aspas dentro do próprio prompt, nunca deixe implícito. Ex.: `..., bold lowercase sans-serif text "flowstate." centered near the bottom of the frame, clean minimal typography, high contrast against the dark background, no watermark`.
- Prefira frases de 1 a 5 palavras — acima disso o modelo erra grafia com mais frequência.
- Descreva o estilo tipográfico explicitamente (serifa/sem serifa, caixa alta/baixa, peso da fonte, posição no quadro) e repita essa descrição em todos os prompts de imagem do canal, para manter consistência visual vídeo a vídeo.
- Se o canal for animado em loop (arquétipo 3, por exemplo), o texto deve estar no prompt da **imagem estática/frame-base**, não no prompt de animação — a animação só move elementos do cenário, o texto deve ficar fixo e legível.

## Fase 2 — Gerar 5 sugestões de vídeo

Com a identidade definida (via A ou B), gere **5 sugestões de vídeo**, cada uma com:

1. **Imagem/visual** — depende do que foi definido na Fase 1:
   - **Se estático**: um único prompt bem detalhado para IA generativa de imagem (sujeito, pose, cenário, iluminação, paleta, estilo/técnica, enquadramento, resolução/aspect ratio). Esse mesmo prompt serve para thumbnail e para o fundo do vídeo. Se o canal usa texto na imagem (ver seção "Texto na imagem" acima), inclua a frase exata entre aspas e o estilo tipográfico diretamente neste prompt.
   - **Se animado em loop**: entregar **dois prompts separados e bem detalhados**:
     1. Um prompt de **imagem estática** (para gerar o frame-base/thumbnail) — mesma especificação detalhada do caso estático acima, incluindo o texto na imagem (frase exata + tipografia) se o canal usar.
     2. Um prompt de **animação/vídeo em loop** para uma IA de vídeo (ex. Runway, Kling, Luma, AnimateDiff/ComfyUI video nodes), descrevendo: quais elementos se movem (chuva caindo, fumaça subindo, luzes de neon piscando, folhas balançando, fogo tremulando), a câmera (geralmente estática/sem corte, ou um pan/zoom muito sutil), a duração do clipe-base (ex. 4-10s, que depois será posto em loop contínuo no ComfyUI), e a instrução explícita de que o **início e o fim do clipe devem casar perfeitamente (seamless loop)**, sem saltos visíveis de luz, posição ou movimento.
2. **Título**: seguindo o padrão definido na Fase 1 (template fixo com slot variável, ou título único por vídeo).
3. **Descrição**: seguindo o formato escolhido na Fase 1 — com palavras-chave do nicho e, se fizer sentido para o gênero, bloco de hashtags e/ou lista de keywords soltas (estilo Shibuya After Rain) ao final. Sem inventar afirmações sobre o canal que o usuário não confirmou. Lembrar o usuário de marcar o vídeo como conteúdo alterado/sintetizado por IA no YouTube Studio ao publicar.
4. **Prompts de música para o YuE2**: ver seção abaixo — múltiplos prompts da mesma linha estética para render um vídeo com a duração-alvo definida na Fase 1.

Se o canal tiver personagem principal definido (seção acima), ofereça também gerar um **prompt para a foto de perfil do canal no YouTube** (formato 1:1, composição centralizada e reconhecível mesmo cortada em círculo), para usar no grupo "Foto de Perfil" do workflow do ComfyUI — com a mesma opção de referência pela Character Sheet.

## Como montar os prompts de música (guia YuE2)

O prompt de estilo do YuE2 usa tags separadas por vírgula, cobrindo 5 ingredientes, nesta ordem de prioridade (a ordem pesa — o que vier primeiro tem mais peso):

| Ingrediente | Exemplos |
|---|---|
| Idioma | English, Portuguese (sempre a primeira tag, mesmo quando o resultado é instrumental) |
| Gênero | city pop, dark jazz noir, medieval lofi, post-apocalyptic dark ambient, dark classical orchestral, cyberpunk lofi |
| Instrumentos | acoustic guitar, Rhodes piano, pulsing bass, analog synths, brushed drums, lute, soft flute, cello, strings |
| Mood | dreamy, uplifting, melancholic, intimate, bleak, nostalgic, sinister |
| Vocal | female vocal / male vocal + tom (airy, warm, deep, smoky) — ou **"instrumental, no vocals"** quando o gênero do canal normalmente não tem voz (caso comum neste nicho) |
| Tempo (opcional) | BPM numérico (ex. 72 BPM) ou descritivo (slow, unhurried phrasing, upbeat) |

Regras:
- Sempre começar pelo idioma, mesmo em faixas instrumentais.
- Colocar o BPM dentro do próprio prompt de estilo (YuE2 não tem campo de BPM separado); tratar como direção, não garantia exata.
- Excluir um instrumento indesejado com tag negativa (ex. "no guitar").
- Nunca empilhar gêneros conflitantes — ou escolher um híbrido já estabelecido, ou liderar decisivamente com um gênero.
- Nunca descrever a história/tema da música no prompt de estilo — isso é para a letra (lyrics), não para o estilo. Se o canal for instrumental, nem se aplica.
- Sempre incluir a tag vocal (gênero + tom) quando houver voz; quando for instrumental, deixar isso explícito ("instrumental, no vocals") em vez de omitir.

### Gerando a duração-alvo com faixas coerentes

Uma faixa do YuE2 costuma durar poucos minutos, então para fechar a duração-alvo definida na Fase 1 (1h, 2h, 3h, 8h etc.) o usuário precisa gerar várias faixas da mesma linha estética. Para cada sugestão de vídeo, entregue **de 6 a 10 variações de prompt** dentro do mesmo gênero/mood geral, variando sutilmente instrumentação, tempo ou intensidade — isso evita repetição perceptível ao longo do vídeo, mas mantém a coesão estilística. Se a duração-alvo for muito maior que o número de prompts entregues (ex. 8h), avise o usuário que ele provavelmente vai repetir/alternar os mesmos prompts várias vezes ou pedir mais variações, e ofereça gerar mais. Se o formato de descrição escolhido usa tracklist nomeada (estilo Lemuria), dê um nome curto e evocativo para cada faixa/prompt (ex. "The Invisible Wall", "Alone Together") em vez de "Faixa 1".

No workflow do ComfyUI, o Grupo 3 (loop de músicas) tem **uma caixa de texto por prompt** ("Prompt de música 1 de 8" até "8 de 8") — cole cada uma das 6-10 variações numa caixa diferente (de cima para baixo) e o loop gera **uma música por prompt preenchido**, não N cópias do mesmo prompt. Avise o usuário disso ao entregar as variações, para ele saber onde colar cada uma.

## Checklist antes de entregar as 5 sugestões

- Identidade visual e musical está consolidada e confirmada pelo usuário (incluindo estático vs. animado, duração-alvo e formato de descrição)?
- Cada sugestão é diferente o bastante das outras 4 (evitar repetir a mesma composição de thumbnail ou o mesmo ângulo de título)?
- Se o formato é animado em loop, cada sugestão tem os **dois** prompts (imagem + animação/loop), e o prompt de animação especifica claramente o que se move e exige loop sem emendas visíveis?
- Nenhum personagem ou design protegido (ex. Lofi Girl, gatos estilo Tom & Jerry) foi reproduzido — só estrutura/fórmula, sempre com personagens originais?
- Todos os prompts do YuE2 começam com idioma, têm tag de vocal/instrumental, e não misturam gêneros conflitantes?
- As variações de prompt por vídeo somam material suficiente para a duração-alvo (ou foi avisado que não somam)?
- Se o formato usa tracklist, cada faixa tem nome próprio?
- Se há personagem principal, o prompt de character sheet foi entregue (e o de foto de perfil, se aplicável)?
- Se o canal usa texto na imagem, cada prompt de imagem (estática e, se animado, o frame-base) inclui a frase exata entre aspas e o estilo tipográfico (fonte, posição, cor)?