# Dashboard de vendas Porsche

Dashboard interativa, em arquivo HTML único, sobre 100 vendas da Porsche. Responde três perguntas de negócio com filtros, indicadores e gráficos.

**Endereço publicado:** [Acessar a dashboard](https://vitorpires-codes.github.io/dashboard-porsche-sales/)

## Perguntas de negócio escolhidas

1. **Quais modelos geram mais receita?** Mostra os dez modelos com maior receita no recorte. Responde onde está o dinheiro e se ele se concentra em poucos modelos. Na base completa, o 911 Dakar lidera, com cerca de 6,3% da receita.

2. **Como os clientes pagam?** Mostra a receita e o número de vendas por método de pagamento. O método define o fluxo de caixa e a forma de conciliar cada venda. Na base completa, a transferência bancária (Wire Transfer) concentra cerca de 31% da receita, com 26 vendas.

3. **Quanto da receita já foi entregue?** Mostra a distribuição da receita por situação de entrega. Na base completa, só cerca de 40% da receita está entregue. Cerca de 55,5% está pendente ou em trânsito, e 5% das vendas foram canceladas. Esse é o valor que ainda pode dar problema.

Escolhi essas três perguntas porque formam uma sequência: onde está a receita, como ela entra e quanto dela já virou entrega de fato.

## O que a dashboard tem

- **Filtros:** modelo, ano do modelo, cidade e método de pagamento. Cada um tem a opção "Todos" e um botão para limpar todos de uma vez.
- **Indicadores:** total de vendas, receita total, ticket médio e percentual da receita já entregue. Todos recalculam com os filtros.
- **Gráficos:** barras horizontais com os dez maiores modelos, barras por método de pagamento e rosca por situação de entrega. Os três recalculam juntos.
- **Recorte vazio:** quando um filtro não retorna vendas, a mensagem aparece no lugar dos gráficos.

## Prompt e evolução

Anexei uma base com 100 vendas de veículos Porsche (base_limpa_porsche.csv). Use o Canvas para criar uma dashboard em HTML de arquivo único, pronta para publicar no GitHub Pages. Entregue o código completo.

DADOS
Colunas: id_venda, data_venda (AAAA-MM-DD; 24 linhas estão vazias, pois as datas originais eram inválidas), modelo, ano_modelo, preco (em dólares, US$), quilometragem, metodo_pagamento, cidade, estado, status_entrega, grupo_entrega (Entregue, Em trânsito, Pendente, Cancelado).
Incorpore os dados diretamente no JavaScript do HTML. Não leia arquivo externo.

FILTROS (barra no topo, com a opção "Todos" em cada um)
- Modelo Porsche
- Ano do modelo
- Cidade
- Método de pagamento
Um botão discreto "Limpar filtros". Ao mudar qualquer filtro, todos os indicadores e gráficos recalculam.

INDICADORES (quatro cartões no topo)
- Total de vendas
- Receita total (US$)
- Ticket médio (US$)
- Percentual da receita já entregue
Cada cartão tem um rótulo pequeno em caixa alta, o valor em destaque e uma linha de apoio com contexto (por exemplo, "de 100 vendas no total").

PERGUNTAS DE NEGÓCIO (três blocos, cada um com um gráfico)
1. Quais modelos geram mais receita?
2. Como os clientes pagam?
3. Quanto da receita já foi entregue?
Cada bloco tem: título em forma de pergunta, uma frase curta explicando o que o gráfico mostra, o gráfico, e uma linha final com a principal conclusão calculada a partir dos dados filtrados. Calcule tudo a partir dos dados. Não escreva valores fixos no texto.

DIREÇÃO VISUAL
Inspire-se no site oficial da Porsche Brasil (https://www.porsche.com/brazil/pt/). O resultado deve parecer uma peça de marca, não um painel técnico.
- Fundo escuro sóbrio, com cor próxima de #0E1418. Texto em branco ou cinza muito claro.
- Uma única cor de destaque, discreta, aplicada apenas em pequenos detalhes (uma linha fina sob títulos, o segmento principal de um gráfico). Evite cores fortes em áreas grandes.
- Tipografia sem serifa, limpa, com hierarquia clara: título grande e leve, rótulos pequenos em caixa alta com espaçamento entre letras, valores de destaque em peso maior.
- Muito espaço em branco. Margens generosas, grade de largura máxima de 1200px centralizada, cartões com bordas finas em tom ligeiramente mais claro que o fundo, sem sombras pesadas.
- Sem ícones decorativos, emojis ou gradientes chamativos.

GRÁFICOS (use Chart.js via CDN do cdnjs)
- Gráfico 1: barras horizontais com os 10 modelos de maior receita. Rótulos de valor no fim de cada barra, em US$ abreviado (ex.: US$ 0,81 mi). Linhas de grade quase invisíveis.
- Gráfico 2: barras verticais por método de pagamento. Tooltip mostrando receita e número de vendas.
- Gráfico 3: rosca (doughnut) por grupo de entrega, com o percentual entregue no centro. Legenda à direita. Cores: verde-discreto para Entregue, cinza-claro para Em trânsito, dourado-discreto para Pendente, cinza-escuro para Cancelado.
- Todos os gráficos sem legenda redundante, com fontes do mesmo estilo do resto da página.

FORMATAÇÃO
- Valores em dólar com símbolo US e separadores do padrão brasileiro (ex.: US$ 12.827.800).
- Percentuais com uma casa decimal e vírgula (ex.: 39,6%).
- Quando um filtro não retornar vendas, mostre uma mensagem elegante no lugar dos gráficos, em vez de deixá-los vazios.

RESPONSIVIDADE
- Em desktop, os gráficos 1 e 2 ficam lado a lado e o gráfico 3 ocupa a largura total.
- Em celular, tudo vira uma coluna, com os filtros empilhados.

TÉCNICA
- Arquivo único, com HTML, CSS e JavaScript.
- Não use localStorage nem sessionStorage.
- Código comentado nas partes principais, para eu entender depois.

Ao final, liste em uma frase o que você decidiu de visual e de cálculo, para eu registrar no README.

Como a dashboard foi gerada:

- A dashboard foi gerada em uma única versão, a partir do prompt acima, sem ajustes posteriores.

## Tratamento da base

Antes de enviar a base para a IA, fiz estes passos:

1. Mantive só as colunas sanitizadas e descartei as versões cruas.
2. Converti preço, ano do modelo e quilometragem para número.
3. Converti as datas para o formato AAAA-MM-DD. As 24 datas inválidas, como 30 de fevereiro de 2024 e 31 de abril de 2024, ficaram vazias e marcadas como inválidas. Essas vendas entram nos indicadores de receita e modelo, mas não entram em análises por período.
4. Agrupei os 10 status de entrega em quatro grupos: Entregue; Em trânsito (Shipped e In Transit); Pendente (status de espera, aprovação e revisão); e Cancelado.
5. A coluna `vendedor` foi removida da base e da dashboard. Ela contém nomes de pessoas e não é necessária para as perguntas de negócio.

A base limpa está no arquivo `base_limpa_porsche.csv`.

**Limitações conhecidas**

- Vinte vendas têm data posterior a 23 de outubro de 2026, chegando a 1º de outubro de 2027. Mantive as datas como vieram da planilha. Como a dashboard não filtra por data, isso não altera os números exibidos, mas os dados devem ser confirmados com a fonte.

## Decisões de filtro

Usei cidade no filtro porque foi o que pedi no prompt. A base tem 79 cidades para 100 vendas, então a maioria dos recortes por cidade tem uma ou duas vendas. Se fosse refazer, usaria estado, que agrupa melhor os dados.

## Ferramenta usada

ChatGPT com Canvas.

## Arquivos

- `index.html`: a dashboard completa, com os dados embutidos.
- `base_limpa_porsche.csv`: a base tratada.
- `README.md`: este arquivo.
- `print-da-tela.png`: captura da dashboard com um filtro aplicado.
