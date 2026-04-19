# Processo Trainee PotiCode

Portal de capacitações do Processo Trainee da PotiCode. Construído com Jekyll e hospedado via GitHub Pages.

---

## Como o Jekyll funciona

Jekyll é um gerador de sites estáticos. Ele lê seus arquivos fonte (Markdown, SCSS, templates) e gera uma pasta `_site/` com HTML, CSS e JS prontos para serem servidos — sem banco de dados, sem servidor.

O fluxo é simples:

```
Arquivos fonte → Jekyll processa → _site/ → GitHub Pages serve
```

Toda vez que você faz um `push` para a branch `main`, o GitHub Actions executa o build automaticamente e publica o site.

---

## Estrutura do projeto

```
prosel-poticode/
├── _data/
│   └── capacitacoes.yml     ← lista de sessões e datas de liberação
├── capacitacoes/            ← conteúdo de cada sessão (um .md por aula)
├── assets/
│   ├── css/main.scss        ← estilos do site
│   └── files/               ← arquivos para download (PDF, ZIP, etc.)
├── _layouts/                ← templates de página
├── _includes/               ← componentes reutilizáveis (header, etc.)
├── index.md                 ← página inicial
├── capacitacoes.md          ← índice de capacitações
├── sobre.md                 ← página sobre
└── _config.yml              ← configurações gerais do site
```

---

## Adicionando uma nova sessão de capacitação

### Passo 1 — Criar o arquivo de conteúdo

Crie um arquivo `.md` dentro da pasta `capacitacoes/`. Use o slug da sessão como nome do arquivo (ex: `git-basico.md`).

**Estrutura obrigatória do arquivo:**

```markdown
---
layout: training
title: "Título da Sessão"
permalink: /capacitacoes/slug-da-sessao/
---

## Primeiro tópico

Conteúdo aqui...

## Segundo tópico

Mais conteúdo...
```

> O `permalink` define a URL da página. Use sempre o mesmo slug que você vai registrar no `_data/capacitacoes.yml`.

Opcionalmente, você pode adicionar materiais para download diretamente no frontmatter:

```markdown
---
layout: training
title: "Título da Sessão"
permalink: /capacitacoes/slug-da-sessao/
materiais:
  - titulo: "Slides da aula"
    arquivo: "nome-do-arquivo.pdf"
    tipo: PDF
    descricao: "Descrição opcional"
---
```

Coloque o arquivo correspondente em `assets/files/`.

### Passo 2 — Registrar no índice de capacitações

Abra `_data/capacitacoes.yml` e adicione a sessão na semana correta:

```yaml
semanas:
  - label: "Semana 1"
    sessoes:
      - titulo: "Título da Sessão"
        slug: "slug-da-sessao"
        unlock: "2026-06-10"
```

O campo `slug` deve ser idêntico ao usado no `permalink` do arquivo `.md`.

---

## Alterando a data de liberação de uma sessão

Abra `_data/capacitacoes.yml` e edite o campo `unlock` da sessão desejada:

```yaml
- titulo: "HTML"
  slug: "html"
  unlock: "2026-06-06"   ← altere esta data
```

O formato é `AAAA-MM-DD`. A sessão fica bloqueada (acinzentada e sem link) até essa data, verificada automaticamente no navegador do usuário a cada acesso.

---

## Adicionando arquivos para download

1. Copie o arquivo (PDF, DOCX, ZIP, etc.) para `assets/files/`
2. Referencie-o no frontmatter da sessão correspondente:

```yaml
materiais:
  - titulo: "Nome exibido"
    arquivo: "nome-exato-do-arquivo.pdf"
    tipo: PDF
```

Os valores aceitos para `tipo` são: `PDF`, `DOC`, `SLIDES`, `ZIP`.

---

## Configurações gerais

As configurações principais ficam em `_config.yml`:

| Campo | O que faz |
|-------|-----------|
| `title` | Nome do site exibido no navbar |
| `description` | Descrição usada nas meta tags de SEO |
| `baseurl` | Prefixo da URL — deve ser igual ao nome do repositório no GitHub |
| `url` | Domínio base — troque pelo seu usuário do GitHub |

Para alterar o `url`, edite a linha:
```yaml
url: "https://SEU-USUARIO.github.io"
```

---

## Rodando localmente

```bash
# Instalar dependências (apenas na primeira vez ou após mudar o Gemfile)
bundle install

# Iniciar servidor de desenvolvimento
bundle exec jekyll serve
```

Acesse em: `http://localhost:4000/prosel-poticode/`

Para validar erros de frontmatter:

```bash
bundle exec jekyll build --strict_front_matter
```

---

## Deploy

O site é publicado automaticamente via GitHub Actions a cada `push` na branch `main`. Não é necessário nenhum comando manual.

Para que o deploy funcione, o repositório precisa estar configurado em:  
**Settings → Pages → Source → GitHub Actions**
