# 📣 Ouvidoria do Distrito Federal (OUV-DF) — Análise Exploratória de Dados

Projeto final da disciplina **Introdução à Ciência de Dados** (CEUB) — Prof. MsC Pedro H. Mello.

Análise exploratória de **2,15 milhões de manifestações** registradas no Sistema de Ouvidoria do
Governo do DF entre **julho/2016 e fevereiro/2025**.

> 🌐 **Apresentação online (GitHub Pages):** https://ucazin.github.io/ouvdf-analise-exploratoria/
> 🖥️ **Slides (PDF):** [`apresentacao/slides.pdf`](apresentacao/slides.pdf) · 📓 **Notebook:** [`notebook/analise.ipynb`](notebook/analise.ipynb)

## 👥 Integrantes (trio)

- Lucca Mariz
- Vitor Pupe
- Lucas Cerqueira

## ❓ Pergunta orientadora

> **O que a população do DF mais demanda da Ouvidoria-Geral (OUV-DF), quem se manifesta e qual é o desfecho dessas manifestações?**

Desdobramentos: que tipos de manifestação predominam? Em quais temas se concentram? Como o volume
evoluiu no tempo? Qual o perfil de quem se manifesta? O poder público resolve o que é demandado?

## 📊 Fonte dos dados

Conjunto **“Dados Estatísticos do Sistema de Ouvidoria / OUV-DF”** — **Portal de Dados Abertos do
Governo do DF** (dados.df.gov.br), licença de dados abertos.
🔗 https://www.dados.df.gov.br/dataset/dados-abertos-do-sistema-de-ouvidoria-ouv-df

- **Tabela central:** `TB_MANIFESTACAO` — **2.153.285 linhas × 17 colunas** (uma linha por manifestação).
- **Tabelas de domínio** (traduzem os códigos `*_id`): Tema, Assunto, Classificação, Situação, Sexo, Região Administrativa, Tipo, Unidade.
- **Formato original:** `ISO-8859-1`, separador `;`. A tabela de manifestações é versionada **compactada**
  (`data/manifestacao.csv.gz`, ~44 MB) para caber no GitHub — o `pandas` lê o `.gz` diretamente.

> As tabelas brutas pesadas do conjunto (Localização ~114 MB, Resposta ~36 MB) **não são versionadas**
> (excedem o limite de 100 MB do GitHub e não são usadas nesta análise). Estão disponíveis no link acima.

## 🗂️ Estrutura do repositório

```
.
├── README.md                  # este arquivo
├── data/
│   ├── manifestacao.csv.gz    # tabela central compactada (2,15 mi de linhas)
│   ├── dim_*.csv              # tabelas de domínio (tema, classificação, situação, sexo, RA…)
│   └── Dicionario_OUV-DF.pdf  # dicionário de dados oficial
├── notebook/
│   └── analise.ipynb          # análise completa (4 etapas), roda do início ao fim sem erros
└── apresentacao/
    ├── slides.pdf             # 14 slides (gráficos = os mesmos do notebook)
    └── figuras/               # os 8 gráficos em PNG
```

## 🔎 O que o notebook faz (4 etapas)

1. **Entendimento e descrição** — carga com pandas, `head()`, significado e tipo de cada coluna, dimensões e estatísticas básicas.
2. **Completude e limpeza** — nulos por coluna (~26–31% nos campos opcionais), 1 duplicata removida, idades impossíveis (de −7967 a 266) tratadas, conversão de tipos e decodificação dos códigos via tabelas de domínio — tudo justificado.
3. **Análise e visualização** — **8 gráficos** (barra, barra horizontal, linha, histograma, boxplot, dispersão), cada um com interpretação logo abaixo.
4. **Conclusões** — 4 conclusões sustentadas por evidência, com discussão honesta das limitações.

## ▶️ Como rodar

Requer Python 3.10+.

```bash
# 1. instalar dependências
pip install pandas numpy matplotlib seaborn jupyter

# 2. abrir o notebook
jupyter notebook notebook/analise.ipynb

# (opcional) executar tudo do zero pela linha de comando:
jupyter nbconvert --to notebook --execute --inplace notebook/analise.ipynb
```

O notebook localiza a pasta `data/` automaticamente, então roda tanto a partir da raiz do projeto quanto de dentro de `notebook/`.

## ✅ Principais conclusões

1. **A OUV-DF é, na prática, um grande canal de reclamação** — ~67% das manifestações são reclamações e apenas ~5% são elogios. Um termômetro direto da insatisfação com o serviço público.
2. **A demanda é dominada por serviços essenciais e zeladoria urbana** — Saúde, Transporte/Mobilidade, Zeladoria e Habitação somam ~65% dos temas (consultas, passe estudantil, tapa-buraco, iluminação).
3. **Responder não é resolver** — 76% das manifestações ficam como “Respondida”, mas só ~9% como “Resolvida” (vs ~14% “Não resolvida”). O *gap* é sistêmico e não varia entre regiões.
4. **O acesso é desigual** — o Plano Piloto concentra ~31% das manifestações que informam a região (~21% do total); o público é predominantemente adulto (idade mediana 45) e mais feminino.
