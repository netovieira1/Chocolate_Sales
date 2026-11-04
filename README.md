# Análise das Exportações Brasileiras para a França (2016–2020)

Análise exploratória em Python (pandas) de exportações do Brasil para a França, com 71 mil registros de exportação, para entender **o que o Brasil vende, de onde vende e como isso evoluiu ao longo do tempo**, com foco em apoiar a decisão de uma empresa de chocolate interessada no mercado francês.

> [CONFIRMAR: ajuste a frase acima para o que realmente motivou o projeto: cenário fictício de curso, trabalho para uma empresa real, etc.]

## Problema de negócio

Uma empresa de chocolate quer avaliar a exportação para a França. Antes de decidir, é preciso responder:

1. Como as exportações para o país evoluíram nos últimos anos?
2. Quais categorias de produto dominam essa pauta?
3. Quais cidades brasileiras mais exportam e o que cada uma vende?
4. Qual é o peso do cacau e do chocolate nessa pauta?

## Dados

- **Arquivo:** `chocolate_sales.csv`
- **Fonte:** arquivo [`chocolate_sales.zip`](dados/chocolate_sales.zip), incluído neste repositório (contém `chocolate_sales.csv`). Fonte original não registrada.
- **País de destino:** França
- **Período:** 2016 a 2020
- **Tamanho:** 142.360 linhas e 11 colunas, sem valores nulos (71.180 registros únicos, ver "Tratamento dos dados")

| Coluna | Descrição |
|---|---|
| `Year`, `Month` | Ano e mês da exportação |
| `Country` | País de destino |
| `City` | Cidade brasileira de origem (648 cidades em 2020) |
| `SH4 Code` / `SH4 Description` | Produto no Sistema Harmonizado, nível de 4 dígitos |
| `SH2 Code` / `SH2 Description` | Categoria do produto, nível de 2 dígitos (97 categorias) |
| `Economic Block` | Bloco econômico do país de destino |
| `US$ FOB` | Valor exportado em dólares (preço FOB) |
| `Net Weight` | Peso líquido |

### Tratamento dos dados

Cada registro de exportação aparece **duas vezes** na base, uma com o bloco econômico `Europe` e outra com `European Union (EU)`. Somar a base inteira dobraria todos os valores em dólar. Por isso o notebook mantém apenas uma cópia de cada registro (a do bloco `European Union (EU)`), o que reduz a base de 142.360 para 71.180 linhas.

## O que foi feito

1. Leitura e inspeção da base (`info()`), conferindo tipos e valores nulos.
2. Verificação e tratamento da duplicidade entre blocos econômicos.
3. Evolução anual do valor exportado e variação em relação ao ano anterior.
4. Ranking das categorias de produto mais exportadas (por `SH2 Description`).
5. Ranking das cidades que mais exportaram em 2020 e perfil de produtos das 2 primeiras.
6. Recorte de cacau e preparações (SH2 18), com detalhe por produto, ano e cidade.

## Principais descobertas

- **As exportações somam cerca de US$ 11,7 bilhões em 2016–2020.** O pico foi em 2018 (US$ 2,62 bi), com alta de cerca de 18% sobre 2017.
- **2020 teve queda de aproximadamente 24%** em relação a 2019 (de US$ 2,61 bi para US$ 1,98 bi), coincidindo com o início da pandemia.
- **A pauta é concentrada em poucas categorias:** resíduos e farelos da indústria alimentar (cerca de 24% do total), minérios, escórias e cinzas (cerca de 14,5%), máquinas e equipamentos (cerca de 8%), celulose (cerca de 8%) e aeronaves (cerca de 5%).
- **Cidades líderes em 2020:** Duque de Caxias (RJ), com US$ 140 mi, Luís Eduardo Magalhães (BA), com US$ 133 mi, e Ponta Grossa (PR), com US$ 94 mi.
- **Duque de Caxias depende de poucos itens:** máquinas e equipamentos respondem por cerca de 66% do que a cidade exporta, e combustíveis minerais por cerca de 24%. Já Luís Eduardo Magalhães exporta praticamente só resíduos da indústria alimentar.
- **Cacau e preparações pesam muito pouco:** US$ 10,6 milhões em cinco anos, cerca de 0,09% do total exportado para a França. Dentro disso, a manteiga, gordura e óleo de cacau respondem por cerca de 76% e o cacau em grão (inteiro ou partido, cru ou torrado) por cerca de 24%. **O chocolate propriamente dito (SH4 1806) soma apenas cerca de US$ 10,6 mil no período.**
- **O cacau exportado vem da Bahia:** Itabuna (cerca de 70%), Gandu (cerca de 21%) e Ilhéus (cerca de 8%). Os valores subiram de US$ 0,75 mi em 2016 para US$ 3,55 mi em 2018 e ficaram em US$ 2,98 mi em 2020.

A base mostra que o chocolate brasileiro quase não aparece na pauta de exportação para a França. Ela não permite concluir se isso indica uma oportunidade ou uma barreira de mercado.

## Como reproduzir

```bash
git clone https://github.com/netovieira1/chocolate_sales.git
cd NOME-DO-REPOSITORIO
pip install pandas matplotlib jupyter jinja2
jupyter notebook chocolate_sales.ipynb
```

## Ferramentas

Python, pandas, matplotlib, Jupyter Notebook

## Contato

[Neto Vieira] | [www.linkedin.com/in/neto-vieira94] | [f.vieiraneto1@gmail.com]
