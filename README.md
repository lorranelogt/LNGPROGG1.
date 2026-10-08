# Indicadores Econômicos do Brasil

Projeto G1 — Tema 17. Análise de 40 observações trimestrais simuladas, de 2015 a 2024. A fonte foi fornecida pelo professor. O documento do tema contém o título G2, mas o nome da entrega segue G1 conforme a atividade.

## Executar no computador

Utilize Python 3.11 ou 3.12. Abra o terminal na pasta que contém `app.py`.

```bash
python -m venv .venv
```

No Windows:

```powershell
.venv\Scripts\activate
```

No macOS/Linux:

```bash
source .venv/bin/activate
```

Depois:

```bash
python -m pip install -r requirements.txt
python -m streamlit run app.py
```

Abra `index.html` no navegador para visualizar a página de apresentação. Ela é estática; o dashboard Python é executado separadamente pelo Streamlit.

Para usar o notebook no VS Code, instale as extensões Python e Jupyter, abra o arquivo em `notebooks/`, escolha o ambiente `.venv` como kernel e clique em Executar Tudo. O notebook já inclui os resultados da execução de entrega. Execute a partir da raiz do projeto ou da pasta `notebooks`.

## Organização

```text
projeto-g1/
├── app.py
├── analise.py
├── requirements.txt
├── README.md
├── PUBLICACAO.md
├── index.html
├── .nojekyll
├── .gitignore
├── .streamlit/config.toml
├── dados/simulacao_indicadores_economicos_brasil.csv
├── database/indicadores.db
├── notebooks/analise_indicadores_economicos.ipynb
└── imagens/
    ├── evolucao.png
    ├── comparacao.png
    ├── relacoes.png
    └── radar.png
```

`analise.py` centraliza preparação, cálculos, conclusão e banco para manter dashboard e notebook consistentes. O CSV original é preservado. O banco é reconstruível e contém somente os dados simulados da atividade.

## Perguntas da análise

- Como o PIB e a renda evoluem?
- Quais trimestres têm maiores variações do PIB?
- Inflação e desemprego estão associados?
- Juros e consumo estão associados?
- Quais indicadores têm maior dispersão relativa?
- Quais períodos estão rotulados como Crise?

## Tratamento e metodologia

Datas e colunas numéricas são convertidas explicitamente. Duplicatas exatas são removidas, linhas inválidas são excluídas com contagem no relatório e conflitos de trimestre geram erro. São verificados ano/trimestre contra a data, categorias válidas, positividade de indicadores de nível e intervalo do desemprego. Inflação negativa é permitida. Não há imputação nem retirada arbitrária de outliers.

Na fonte entregue: 40 registros válidos, nenhuma duplicata, ausência ou lacuna trimestral. As ausências nas colunas derivadas são esperadas: a primeira variação trimestral e as três primeiras médias móveis não têm histórico suficiente.

- **KPIs:** médias aritméticas de PIB, inflação, desemprego, juros, câmbio e variação trimestral do PIB.
- **Variação do PIB:** `(pib_t / pib_t-1 - 1) * 100`, calculada na série completa e somente entre trimestres consecutivos. Filtros não redefinem o trimestre anterior.
- **Média móvel:** quatro trimestres consecutivos, calculada antes dos filtros.
- **Correlação:** Pearson contemporâneo, com aviso para recortes insuficientes; não demonstra causalidade.
- **Instabilidade:** coeficiente de variação amostral dos níveis, não volatilidade de retornos.
- **Radar:** média normalizada de 0 a 100 pelos extremos da base completa. Valores maiores não são necessariamente melhores.
- **Barras anuais:** médias dos trimestres selecionados, não totais anuais.
- **Crise:** classificação original da fonte, sem atribuição a acontecimentos reais.

A unidade de PIB e volumes de comércio exterior não está detalhada. Não se assume PIB em milhões ou bilhões. Renda usa a escala monetária do tema e não foi deflacionada. A periodicidade de acumulação da inflação não foi especificada, portanto não há cálculo de inflação anual composta.

## Atendimento aos requisitos

| Requisito | Implementação |
|---|---|
| Python e Pandas | Preparação, atributos, agregações e KPIs |
| Matplotlib e Seaborn | Heatmaps no dashboard e gráficos no notebook |
| Streamlit | Aplicação com filtros, abas, tabelas, textos e exportação |
| Filtros múltiplos | Ano, trimestre, nível econômico e indicador |
| KPIs dinâmicos | Seis médias conforme o recorte |
| Gráficos obrigatórios | Linha, barras, dispersão, heatmap, radar e tabela dinâmica |
| Funcionalidade avançada 1 | Persistência SQLite com SQLAlchemy e consulta SQL |
| Funcionalidade avançada 2 | Correlação estatística Pandas/NumPy |
| Recurso temporal adicional | Média móvel de quatro trimestres |
| Notebook | Introdução, fonte, limpeza, atributos, EDA, KPIs, gráficos, interpretação e conclusão |
| HTML | Página responsiva com resultados e arquivos para download |
| Publicação | Instruções em PUBLICACAO.md; depende de publicação na conta do aluno |

Os filtros de ano, trimestre e nível afetam os KPIs, análises e conclusão. A escolha de indicadores altera gráficos comparativos; os dois pares de dispersão pedidos no tema continuam visíveis. Seleção vazia é tratada. A gravação SQLite usa sempre a base completa, evitando substituir os dados por um recorte.

## Limites

A análise é acadêmica e a base é simulada. Não representa séries oficiais ou efeitos causais. O SQLite é persistência local; no Streamlit Community Cloud o arquivo pode ser perdido/recriado em reinícios. O CSV versionado permanece como fonte para reconstrução. O projeto não consome API nem se apresenta como multipágina: utiliza abas, correlação e SQLite para atender aos recursos exigidos.

## Links da entrega

- Repositório GitHub: pendente de publicação.
- GitHub Pages: pendente de publicação.
- Streamlit Community Cloud: pendente de publicação.

Preencha esses campos e o objeto `links` ao final de `index.html` com os endereços reais após publicar.
