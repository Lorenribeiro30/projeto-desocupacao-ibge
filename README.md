# Desocupação no Brasil: comparação entre 2024 e 2025

## Problema e objetivo

A desocupação afeta a renda das famílias e pode aumentar a vulnerabilidade social. Como o mercado de trabalho varia entre os estados, observar apenas um número nacional pode esconder diferenças locais. Este projeto compara taxas anuais de desocupação em 12 unidades da Federação (UFs) em 2024 e 2025, para identificar diferenças e apoiar a definição de prioridades para políticas de emprego. A taxa corresponde à parcela das pessoas na força de trabalho que estavam desocupadas; não é a parcela de toda a população.

## Coleta de dados

Fonte pública: IBGE, Pesquisa Nacional por Amostra de Domicílios Contínua (PNAD Contínua). Os indicadores anuais foram transcritos manualmente das divulgações oficiais abaixo, em 06/11/2026:

- [Divulgação de 2024](https://agenciadenoticias.ibge.gov.br/agencia-sala-de-imprensa/2013-agencia-de-noticias/releases/42703-pnad-continua-taxas-medias-anuais-de-desocupacao-sao-as-menores-da-serie-em-14-unidades-da-federacao).
- [Divulgação de 2025](https://agenciadenoticias.ibge.gov.br/agencia-sala-de-imprensa/2013-agencia-de-noticias/releases/45920-pnad-continua-taxas-anuais-de-desocupacao-sao-as-menores-da-serie-em-20-unidades-da-federacao).

Os textos são páginas públicas; os dados foram extraídos dos textos, sem API ou scraping, e organizados manualmente em CSV estruturado. A seleção inclui as 12 UFs citadas nominalmente em ambas as divulgações como tendo atingido os menores valores anuais da série. É uma amostra intencional, não aleatória: **não representa todas as 27 UFs, nem permite generalizar para o Brasil**. Valores sujeitos a eventual revisão do IBGE.

## Modelagem e análise exploratória

A base `dados/desocupacao_ibge_2024_2025.csv` contém uma linha por UF e ano: `uf`, `regiao`, `ano` e `taxa_desocupacao_pct` (número em pontos percentuais, ex.: 5.0 significa 5%). São 24 linhas. A análise em Python confere tipos, nulos, duplicatas, valores possíveis e presença dos dois anos; padroniza espaços, calcula estatísticas descritivas e compara taxas por UF. Como cada linha possui apenas um indicador numérico, a correlação de Pearson é calculada entre as taxas de 2024 e 2025 das mesmas 12 UFs. Não indica causa nem prova estabilidade estatística. O notebook está em `notebook/analise.ipynb`.

## Resultados e conclusões

- Onze das 12 UFs selecionadas registraram taxas numéricas menores em 2025; no Amazonas, os valores arredondados permaneceram em 8,4%. Não foi feito teste de significância estatística.
- São Paulo teve a maior redução nominal do recorte: de 6,2% para 5,0%, uma diferença de **−1,2 ponto percentual**.
- Em 2025, Amazonas (8,4%) e Rio Grande do Norte (8,1%) registraram as maiores taxas do recorte; Mato Grosso (2,2%) e Santa Catarina (2,3%), as menores.
- A correlação de Pearson entre as taxas dos dois anos foi aproximadamente 0,992, mas mede associação entre valores das mesmas UFs e não demonstra causalidade.

A diferença entre as taxas sugere investigar as condições locais e priorizar a avaliação de ações de qualificação, intermediação de emprego e apoio à contratação nas áreas de maior desocupação. Antes de implementar medidas, seria necessário examinar todas as UFs, perfil dos trabalhadores, oferta de vagas, sazonalidade e incerteza amostral. Os dados não explicam por si só o motivo das diferenças nem demonstram a eficácia das ações.

## Visualização

A imagem `visualizacoes/comparacao_ufs.png` apresenta as taxas por UF e ano. Painel interativo no Looker Studio: ****https://datastudio.google.com/reporting/80a866d3-d5fb-40b7-bbc8-861ed3c17208****. O gráfico inclui somente as 12 UFs selecionadas; percentuais não devem ser somados nem tratados como número de pessoas.

## Reprodução

No Google Colab, abra `notebook/analise.ipynb`, clique em **Ambiente de execução > Executar tudo** e selecione o arquivo CSV quando solicitado. Para abrir no computador, mantenha a estrutura de pastas e execute o notebook a partir da pasta `notebook`.
