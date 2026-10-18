# Cálculos e atualização

## Origem e organização

Base!A6:M6 preserva os cabeçalhos em inglês da fonte. Os 295 registros ocupam A7:M301. O cálculo cobre as linhas 7 a 1006. A coluna D contém datas numéricas do Excel, com exibição dia/mês/ano.

Calculos possui um registro correspondente a cada linha da Base. As colunas A:E identificam o registro. F normaliza o preço EA, G calcula o bruto, H traz o cupom, I calcula o total, J traz o total informado, K indica a inclusão no recorte, L calcula a diferença e M identifica IDs repetidos. N identifica divergência monetária superior a meio centavo.

## Filtros do painel

| Célula | Controle | Valores |
|---|---|---|
| Painel!B8 | Data inicial inclusiva | Data válida |
| Painel!G8 | Data final inclusiva | Data válida, igual ou posterior ao início |
| Painel!L8 | Plano | Todos, Core, Standard, Ultimate |
| Painel!Q8 | Tipo | Todos, Monthly, Quarterly, Annual |
| Painel!V8 | Renovação | Todas, Yes, No |

Calculos!P3 valida as opções e as datas. K usa o identificador preenchido e todas as condições do filtro para retornar 1 ou 0. As opções inglesas são mantidas para corresponder exatamente à fonte: Monthly = mensal, Quarterly = trimestral e Annual = anual.

## Agregados

| Intervalo/célula | Cálculo |
|---|---|
| P6 | Soma das flags K, quantidade incluída |
| P7 | SOMASES do total J com K = 1 |
| P8 | P7/P6; n.a. quando quantidade = 0 |
| P9 | CONT.SES K = 1 e renovação Yes / P6 |
| P10 | Bruto selecionado |
| P11:P13 | Planos, EA e Minecraft selecionados |
| P14 | Cupons selecionados |
| P15 | EA + Minecraft |
| P16 | Adicionais / bruto |
| P17 | Quantidade com cupom positivo / quantidade selecionada |
| O21:R33 | Calendário de 2024 e agregação mensal |
| T21:V24 | Total por plano e ordem com desempate estável |
| X21:Y24 | Ranking ordenado usado pelo gráfico |
| T28:U31 | Composição do bruto para o gráfico de composição |
| O38:Q44 | Conciliação terminal, não usada como origem dos resultados |

Os meses são exibidos em ordem cronológica. O limite inferior é o primeiro dia de cada mês e o superior é o primeiro dia do mês seguinte, exclusivo. Isso evita misturar meses com números semelhantes ou excluir o último dia.

Os gráficos são ligados a células, não a imagens. A seleção do painel recalcula os totais por fórmulas. Não foram criadas tabelas dinâmicas ou segmentações nativas, e as listas suspensas não são descritas como esses recursos.

## Cuidados de interpretação

Um registro da base é uma assinatura listada, não uma sequência de pagamentos. O total do tipo Annual é a soma dos valores informados nas linhas anuais, sem multiplicação. A renovação automática não mede retenção. Os preços EA e Minecraft são brutos, pois não há alocação dos cupons por produto.

O período atual começa em janeiro e termina em dezembro de 2024. Janeiro e fevereiro têm apenas dois registros cada, e dezembro termina no dia 16. Não há garantia de cobertura uniforme ou comparação entre meses completos.

## Adicionar registros

1. Insira uma nova linha abaixo dos registros atuais da Base, com os 13 campos originais na mesma ordem. Mantenha ID único e campos monetários numéricos.
2. Use datas numéricas, não textos. Mantenha as categorias escritas exatamente como a fonte.
3. A tabela do Excel pode ser expandida para incluir a nova linha. Os cálculos já cobrem até a linha 1006, independentemente da expansão do filtro da tabela.
4. Ajuste o período no painel e confira os totais e a conciliação.
5. Para outro ano, substitua as datas de R22:R33 e os rótulos de O22:O33 da aba Calculos, ajustando também o título do gráfico no Painel.
6. Acima de 1.000 registros, estenda as fórmulas por linha e todos os intervalos limitados à linha 1006. Não use o resultado antes de reconciliar a nova base.

Os valores esperados de Q39:Q44 documentam a base original. Após uma atualização, revise esses controles de referência. Eles não bloqueiam nem alteram os indicadores.
