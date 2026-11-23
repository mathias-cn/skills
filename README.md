# skills

Coleção pessoal de [Agent Skills](https://agentskills.io/specification): pastas com um `SKILL.md` (e arquivos de apoio) que ensinam um agente de IA a executar uma tarefa específica. O formato é um padrão aberto, então as mesmas skills funcionam em Claude (claude.ai e Claude Code), Cursor, Codex e outras ferramentas compatíveis.

## Skills disponíveis

| Skill | O que faz |
|---|---|
| [`prospeccao-vendas-sites`](skills/prospeccao-vendas-sites/SKILL.md) | Playbook de prospecção e venda de sites e landing pages para pequenos negócios: garimpo de leads, abordagem fria (método GIC), follow-up, prévia, reunião, objeções, preço, nichos e pós-venda. |

## Estrutura do repositório

```
skills/
├── README.md
└── skills/
    └── <nome-da-skill>/
        ├── SKILL.md          # obrigatório: frontmatter (name, description) + instruções
        ├── references/       # opcional: documentos lidos sob demanda
        ├── scripts/          # opcional: código executável
        └── assets/           # opcional: modelos, imagens, fontes
```

## Como instalar

### Opção 1: CLI `skills` (mais simples)

```bash
# listar as skills do repositório
npx skills add mathias-cn/skills --list

# instalar tudo, ou escolher uma skill e as ferramentas de destino
npx skills add mathias-cn/skills --skill prospeccao-vendas-sites
npx skills add mathias-cn/skills --skill prospeccao-vendas-sites -a claude-code -a cursor -a codex
```

Use `-g` para instalar no diretório do usuário (global) em vez do projeto atual.

### Opção 2: copiar a pasta manualmente

Copie `skills/<nome-da-skill>/` para o diretório de skills da ferramenta. Os caminhos mais comuns são:

| Ferramenta | No projeto | Global |
|---|---|---|
| Claude Code | `.claude/skills/` | `~/.claude/skills/` |
| Cursor | `.cursor/skills/` | `~/.cursor/skills/` |
| Codex | `.agents/skills/` | `~/.codex/skills/` |

Esses caminhos podem mudar com as versões; confirme na documentação de cada ferramenta.

### Claude.ai

Compacte a pasta da skill em `.zip` (com a pasta `prospeccao-vendas-sites/` na raiz do arquivo) e envie pelo upload de skills nas configurações do Claude.

## Convenções para novas skills

- Uma pasta por skill, com o nome em minúsculas, números e hífens (sem acentos, sem `--`, até 64 caracteres). O `name` no frontmatter **precisa ser igual ao nome da pasta**.
- `description` com até 1024 caracteres: diga **o que a skill faz e quando usar**. É o que o agente lê para decidir se carrega a skill, então inclua os termos que o usuário provavelmente usaria.
- Mantenha o `SKILL.md` abaixo de ~500 linhas e mova o detalhe para `references/`, apontando no `SKILL.md` quando cada arquivo deve ser lido.
- Use só os campos padrão do frontmatter (`name`, `description`, opcionalmente `license`, `compatibility`, `metadata`) para garantir compatibilidade entre ferramentas.
- Não coloque segredos, tokens ou dados pessoais na skill.

## Créditos

A skill `prospeccao-vendas-sites` foi escrita a partir da transcrição e dos slides de uma live sobre prospecção e venda de sites (novembro de 2026), reorganizada e reescrita em formato de skill, sem os trechos de divulgação de cursos e produtos. Os méritos das ideias são dos palestrantes.

## Licença

[MIT](LICENSE).
