# Verificações realizadas

Data: 17/10/2026.

Foram testados controles e resultados no motor de criação. O XLSX final foi reaberto e recalculado no LibreOffice. O Microsoft Excel não foi utilizado nesta verificação.

| Teste | Obtido | Esperado |
|---|---|---|
| Total integral | 7633 | 7633 |
| Quantidade integral | 295 | 295 |
| Plano bruto | 2935 | 2935 |
| EA Play bruto | 2940 | 2940 |
| Minecraft bruto | 3880 | 3880 |
| Cupons | 2122 | 2122 |
| Conciliação por linha | 0 | 0 |
| IDs repetidos | 0 | 0 |
| L8 Ultimate quantidade | 98 | 98 |
| L8 Ultimate total | 5388 | 5388 |
| Q8 Annual quantidade | 71 | 71 |
| Q8 Annual total | 1754 | 1754 |
| V8 Yes quantidade | 148 | 148 |
| V8 Yes total | 3786 | 3786 |
| Filtros combinados | 1064 | 1064 |
| Sem registros | 0 | 0 |
| Ticket sem registros | n.a. | n.a. |
| Datas invertidas | 0 | 0 |
| Total indisponível | n.a. | n.a. |
| Inclusão próxima linha | 7638 | 7638 |
| Restauração final | 7633 | 7633 |
| LibreOffice Painel B14 | 7633.0 | 7633 |
| LibreOffice Painel J14 | 295.0 | 295 |
| LibreOffice Painel P14 | 25.8745762711864 | 25.87457627118644 |
| LibreOffice Painel V14 | 0.501694915254237 | 0.5016949152542373 |
| LibreOffice Painel S5 | Cálculos | Cálculos |
| LibreOffice Painel W5 | Ver base | Ver base |
| LibreOffice Calculos P3 | 1.0 | 1 |
| LibreOffice Calculos P6 | 295.0 | 295 |
| LibreOffice Calculos P7 | 7633.0 | 7633 |
| LibreOffice Calculos P11 | 2935.0 | 2935 |
| LibreOffice Calculos P12 | 2940.0 | 2940 |
| LibreOffice Calculos P13 | 3880.0 | 3880 |
| LibreOffice Calculos P14 | 2122.0 | 2122 |
| LibreOffice Calculos P42 | 0.0 | 0 |
| LibreOffice Calculos P43 | 0.0 | 0 |
| LibreOffice Calculos P44 | 0.0 | 0 |
| Células originais preservadas | 3835 | 3835 |
| Células de erro no arquivo final | 0 | 0 |
| Validações de dados | 5 | 5 |
| Links internos | 4 | 4 |
| Gráficos nativos | 3 | 3 |
| Gráficos ligados a Calculos | 3 | 3 |
| Tabela nativa | 1 | 1 |
| Filtro nativo na tabela | 1 | 1 |

Total: 45 verificações concluídas com os resultados esperados.

## Revisão visual
As três abas foram renderizadas e revisadas. Na conferência do arquivo reaberto, o gráfico de composição foi convertido para colunas, pois a rosca não preservou a distinção visual desejada. Os rótulos mensais foram encurtados. As capturas finais vêm do PDF gerado pelo LibreOffice a partir do arquivo entregue; as capturas de apoio são recortes dos dados e dos cálculos, não a totalidade das linhas.

## Cobertura e limites
Os testes de mudança de filtro, datas invertidas, ausência de resultados e inclusão temporária de nova linha ocorreram no motor de criação. No LibreOffice foram conferidos o estado final restaurado, os resultados, as fórmulas, os links, as validações, os gráficos e a tabela. Não foi simulada interação por clique no Microsoft Excel. A revisão dos links confirmou seus destinos e textos, sem teste de cliques no Excel.

Os 3.835 valores da Base foram comparados com a fonte. A base original está preservada em data/base.xlsx. As três séries gráficas permanecem conectadas às células da aba Calculos.

A fonte cobre apenas 2024 e tem cobertura parcial em alguns meses. Não foram calculados retenção, churn, margem, MRR ou cobrança recorrente por falta dos dados necessários.
