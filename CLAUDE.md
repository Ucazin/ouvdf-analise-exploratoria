# Projeto Final — Introdução à Ciência de Dados (CEUB)

> Análise exploratória (EDA) das **manifestações da Ouvidoria do DF (OUV-DF, 2016–2025)**: entender → limpar → analisar → concluir → comunicar. Trabalho em trio, com notebook + slides entregues no GitHub e apresentação em sala.

## Status atual

**Fase: ENTREGA PUBLICADA no GitHub + site no ar, DENTRO DA REGRA.** Tema: **Ouvidoria do DF (OUV-DF)** — dataset do **Portal de Dados Abertos do DF**, ✅ atende à regra eliminatória de fonte. `notebook/analise.ipynb` (4 etapas, **8 gráficos**, 4 conclusões) roda sem erros; `apresentacao/slides.pdf` **redesenhado** (14 slides, identidade editorial); `README.md` + dados em `data/`.
**✅ GitHub:** https://github.com/Ucazin/ouvdf-analise-exploratoria (repo renomeado de "motogp"; histórico limpo, contributor = só Ucazin).
**🌐 GitHub Pages (site de data storytelling):** https://ucazin.github.io/ouvdf-analise-exploratoria/ (no ar, build ok).
**Pendente:** ensaiar apresentação. (Opcional: unificar a paleta dos gráficos do notebook com a do site/slides — hoje o notebook usa paleta levemente diferente.)

## Contexto do trabalho (enunciado oficial)

- **Disciplina:** Introdução à Ciência de Dados — Prof. MsC Pedro H. Mello (CEUB).
- **Formato:** trios. Tema livre, **mas os dados têm que vir exclusivamente do Portal de Dados Abertos do DF** → https://www.dados.df.gov.br/dataset ✅ (agora atendido — OUV-DF é do portal).
- **Regra de reserva:** cada dataset só pode ser usado por um trio — vale quem validar primeiro.
- **E-mail de validação:** pedro.mpereira@ceub.edu.br
- **Apresentação:** 10 min por trio (+3 de perguntas), **todos os 3 integrantes falam**.
- **Fonte do enunciado:** `projeto_final_ics.html` (documento Quarto do professor) e `template_validacao.md` (formulário de validação a preencher).

### As 4 etapas obrigatórias (vão no notebook)

1. **Entendimento e descrição** — carregar com pandas, `head()`, descrever cada coluna, tipo de cada coluna, nº de linhas/colunas, estatísticas básicas (média, mediana, moda, mín, máx).
2. **Completude e limpeza** — nulos por coluna (e proporção); o que foi feito com nulos/duplicatas/valores estranhos **e por quê**; correção de tipagem.
3. **Análise e visualização** — **mínimo 6 gráficos em Python** (matplotlib/seaborn/pandas), tipos variados (barra, linha, histograma, dispersão, boxplot), todos com título/eixos/legenda, **cada um com texto de interpretação logo abaixo** (gráfico sem interpretação é desconsiderado).
4. **Conclusões** — **mínimo 3**, cada uma respondendo à pergunta, sustentada por evidência (gráfico/tabela/estatística) e escrita de forma honesta.

### Entregáveis (no GitHub)

```
.
├── README.md          # tema, pergunta, link do dado, integrantes, como rodar
├── notebook/
│   └── analise.ipynb  # análise completa, roda do início ao fim SEM erros, organizada em markdown
└── apresentacao/
    └── slides.pdf     # PowerPoint/Google Slides exportado em PDF
```

- **Notebook `.ipynb`:** trabalho completo, rodando sem erro, dividido em células markdown.
- **Slides `.pdf`:** capa (tema+nomes) → contracapa (pergunta) → descrição do dataset → completude/limpeza → gráficos com interpretação → conclusões. **Os gráficos dos slides têm que ser os mesmos do notebook, feitos em Python.**

### Critérios de avaliação

Escolha/descrição do dado · limpeza justificada · qualidade da pergunta · os 6+ gráficos · interpretação dos gráficos · as 3+ conclusões · organização do notebook · apresentação (tempo, todos falando) · organização do repositório/README.

## Prazos

| Item | Prazo |
|------|-------|
| Validação do dataset (e-mail `.md` ao professor) | até o fim da **Aula 1** |
| **Entrega final no GitHub** (notebook + slides.pdf + README) | **23h59 de 24/06/2026** |
| **Apresentações em sala** (ordem alfabética) | **25/06/2026** |

## Stack

- Linguagem: **Python 3.13** (kernel jupyter usa 3.12 — ambos com pandas/matplotlib/seaborn ok)
- Análise: **pandas 3.0** · Visualização: **matplotlib / seaborn**
- Ambiente: **Jupyter Notebook (`.ipynb`)** · Slides: gerados via **matplotlib `PdfPages`** → `.pdf`
- Versionamento: **GitHub**

> Os defaults globais (Next.js/Tailwind/shadcn) NÃO se aplicam — este é um projeto de data science em Python.

## Dataset (OUV-DF)

- **Fonte:** Portal de Dados Abertos do GDF — *“Dados Estatísticos do Sistema de Ouvidoria / OUV-DF”*.
  🔗 https://www.dados.df.gov.br/dataset/dados-abertos-do-sistema-de-ouvidoria-ouv-df
- **Tabela central:** `TB_MANIFESTACAO` — **2.153.285 linhas × 17 colunas**, período jul/2016–fev/2025.
- **Encoding:** ISO-8859-1, separador `;`. Modelo relacional: fato (manifestação) + dimensões (Tema, Assunto, Classificação, Situação, Sexo, Região Administrativa…).
- **Pergunta:** *O que a população do DF mais demanda da OUV-DF, quem se manifesta e qual o desfecho?*

## Roadmap / próximos passos

1. **Ensaiar a apresentação** (10 min, os 3 falam) — dividir: descrição+limpeza / gráficos / conclusões. O site Pages e os slides servem de apoio visual.
2. **Deletar o repo `motogp-analise-exploratoria-old`** no GitHub (sobra antiga; Claude não tem scope `delete_repo`).
3. **(Opcional) unificar a paleta** dos gráficos do notebook (`apresentacao/figuras/fig*.png`) com a do site/slides (azul/laranja) — hoje o notebook usa paleta crest/mista; site e slides usam `docs/img/g_*.png` (azul/laranja).
4. **(Opcional) validar o dataset com o professor** por e-mail (regra de reserva: 1 dataset por trio).

## Decisões técnicas

- **2026-06-24 — Site GitHub Pages + slides redesenhados (design-start/frontend-design).** A pedido do usuário, criada uma camada de apresentação visual: site editorial institucional em `docs/` (HTML/CSS + **Chart.js** para 4 gráficos interativos + 4 imagens), servido via **Pages de `/docs`**; slides.pdf refeitos em **HTML→PDF via Chrome headless** (`--print-to-pdf`), mesma identidade. **Stack:** sem build, Fraunces+IBM Plex Sans, paleta azul/laranja. `design-brief.md` registra a direção. **QA:** screenshots via Chrome headless (desktop+mobile) — responsivo, sem overflow. Gráficos do site/slides re-renderizados em `docs/img/g_*.png` (paleta unificada).
- **2026-06-24 — PIVÔ para OUV-DF (dentro da regra do portal do DF).** Abandonado o MotoGP (fonte Kaggle, fora da regra eliminatória). O trio decidiu usar **qualquer dataset bom do portal do DF**; Claude curou candidatos e o trio escolheu **Ouvidoria OUV-DF**. **Resolve a não-conformidade** que existia com o MotoGP.
- **2026-06-24 — Acesso ao portal:** o portal tem **WAF anti-bot (challenge JS)** — `curl`/script não baixam (retornam a home). Download feito **manualmente pelo usuário** no navegador (passa pelo WAF); Claude processou de `~/Downloads`.
- **2026-06-24 — Dados:** `OUV-DF - Manifestação.csv` e `Resposta.csv` na verdade eram **ZIPs** (TB_MANIFESTACAO 279 MB / TB_RESPOSTA 238 MB descompactados). Análise usa só **TB_MANIFESTACAO** + dimensões. Localização (114 MB) e Resposta **não** versionados (estouram limite GitHub e não usados).
- **2026-06-24 — Repo:** `data/manifestacao.csv.gz` (44 MB, todas as colunas, cabe no GitHub) + `data/dim_*.csv` + `Dicionario_OUV-DF.pdf`. `.gitignore` bloqueia os brutos na raiz e tabelas pesadas. Limpei 12 arquivos crus que estavam staged na raiz (incl. Localização 114 MB).
- **2026-06-24 — Limpeza:** nulos 26–31% nos campos opcionais (idade/sexo/bairro/RA) **mantidos e filtrados por gráfico** (dropar perderia ~600k linhas); 1 duplicata removida; IDADE fora de [1,110] (de −7967 a 266) → NaN; `Data Abertura` (texto SQL "Oct 18 2016 6:00PM") → datetime; FKs decodificadas via dimensões.
- **2026-06-24 — Slides via matplotlib (`PdfPages`):** `slides.pdf` (14 slides) reusa os PNGs do notebook. Bug corrigido: `ax.axis("off")` escondia a faixa de título (texto branco sobre branco) → trocado por desligar ticks/spines mantendo facecolor.
- **2026-06-24 — (HISTÓRICO, descartado) Tema MotoGP** (Kaggle, CC0) — era fora da regra; substituído pelo OUV-DF.

## Bugs conhecidos / pendências

- [x] Integrantes do trio: **Lucca Mariz, Vitor Pupe, Lucas Cerqueira**.
- [x] **Dentro da regra:** dados do Portal do DF (OUV-DF). Não-conformidade do MotoGP resolvida.
- [x] Notebook roda sem erro (0 erros, 8 gráficos) — verificado via nbconvert.
- [ ] **Commit + push** para o GitHub (repo precisa renomear de "motogp" ou criar novo).
- [ ] **Deletar repo `motogp-analise-exploratoria-old`** (Claude não tem scope `delete_repo`).
- [ ] 🔐 **Revogar o token Kaggle** (`KGAT_…`) exposto em sessão anterior — kaggle.com/settings (não é mais usado, mas revogar por segurança).
- [ ] Faltam e-mails `@sempre.ceub.edu.br` dos integrantes (se o professor exigir validação formal).

## Ideias / parking lot

- Tabelas não usadas (Resposta, Localização, Unidade, Assunto detalhado) rendem mais análises: tempo de resposta (Resposta), mapa de pontos (Localização X/Y), órgão acionado (Unidade).
- Dados brutos completos em `~/Downloads/` (zip do pacote + CSVs soltos) e `~/Downloads/ouvdf_x/` (TB_MANIFESTACAO extraído).

## Histórico de sessões

### 2026-06-24 (sessão 3 — apresentação visual: site + slides)
- Publicado no GitHub (repo renomeado `motogp...` → `ouvdf-analise-exploratoria`, histórico limpo via branch órfão + force-push, contributor só Ucazin).
- Criado **site GitHub Pages** (`docs/index.html`) editorial institucional, responsivo, 4 gráficos interativos (Chart.js) + 4 imagens, no ar em https://ucazin.github.io/ouvdf-analise-exploratoria/.
- **Slides.pdf redesenhados** via HTML→PDF (Chrome headless), mesma identidade. `data.json`/`data.js` com agregações; `docs/img/g_*.png` na paleta do site; `design-brief.md`.
- QA visual via Chrome headless (desktop + mobile). Habilitado Pages via `gh api`.

### 2026-06-24 (sessão 2 — pivô para OUV-DF)
- **Pivô de tema:** abandonado MotoGP (fora da regra) → **Ouvidoria OUV-DF** (portal do DF, dentro da regra). Usuário baixou o pacote completo manualmente (WAF bloqueia script).
- EDA real de 2,15 mi de manifestações (nulos, datas, idade, joins com dimensões); definida pergunta + 8 gráficos + 4 conclusões.
- Construído **tudo do zero para OUV-DF**: `notebook/analise.ipynb` (4 etapas, 8 gráficos, 4 conclusões, executado 0 erros), `apresentacao/slides.pdf` (14 slides), `apresentacao/figuras/` (8 PNGs), `README.md` reescrito, `data/` reorganizada (gzip + dimensões + dicionário), `.gitignore` blindado, `CLAUDE.md` atualizado.
- QA visual de todos os gráficos e slides (corrigida inconsistência de % no gráfico de regiões e bug da faixa de título nos slides).
- Arquivos principais: `notebook/analise.ipynb`, `apresentacao/slides.pdf`, `README.md`, `data/manifestacao.csv.gz`, `CLAUDE.md`.

### 2026-06-24 (sessão 1 — MotoGP, descartada)
- Tema MotoGP (Kaggle, CC0): notebook (7 gráficos) + slides + README publicados no GitHub. Auditoria apontou **não-conformidade eliminatória** (fonte fora do portal do DF) → motivou o pivô da sessão 2.

### 2026-06-22
- Lido o enunciado e o `template_validacao.md`; mapeados requisitos, entregáveis, prazos e critérios. Pesquisados datasets do Portal do DF. Criado este `CLAUDE.md`.

---

## Como rodar

```bash
pip install pandas numpy matplotlib seaborn jupyter
jupyter notebook notebook/analise.ipynb
# ou executar tudo do zero, sem abrir:
jupyter nbconvert --to notebook --execute --inplace notebook/analise.ipynb
```

O notebook acha a pasta `data/` automaticamente (sobe diretórios até encontrá-la), então roda da raiz ou de dentro de `notebook/`.
