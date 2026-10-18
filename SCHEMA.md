# Xbox Sales — schema do projeto

Autor: Samuel B. Lira. Planejamento escrito antes da implementação.

## Objetivo e público
Dashboard educacional no Excel para analisar vendas de assinaturas e adicionais. Destinado ao avaliador da DIO e a leitores de portfólio. Construção autoral com assistência de IA, usando a base didática fornecida pela DIO.

## Perguntas de negócio
1. Qual é o total registrado e o ticket médio no recorte escolhido?
2. Como o valor se distribui ao longo dos meses e entre os planos?
3. Quanto EA Play e Minecraft acrescentam ao valor dos planos?
4. Qual parcela das assinaturas tem renovação automática habilitada?
5. Qual é a incidência de cupons e seu valor no recorte?

## Dados e significado
- Fonte: https://hermes.dio.me/files/assets/805d54f9-6d53-4246-bed7-4aa2da615923.xlsx
- 295 registros, 295 IDs únicos, datas de início entre 01/01/2024 e 16/12/2024.
- Preservar os 13 campos originais em Base. Não copiar os ativos ou o layout do dashboard finalizado.
- Valores monetários apresentados em reais, conforme a formatação da fonte.
- O hífen no preço de EA Play significa ausência do adicional e será convertido em zero somente nos cálculos.
- Data de início representa a data do registro analisado. Não há histórico de cobrança recorrente, cancelamentos, custos ou metas.
- Total registrado não será multiplicado pela duração do plano nem apresentado como receita contábil reconhecida ou MRR.
- A renovação automática é uma configuração, não uma taxa de retenção ou uma renovação efetivamente realizada.

## Arquitetura
1. Painel: único dashboard, filtros editáveis e gráficos nativos.
2. Calculos: elegibilidade por registro, normalização do adicional, agregações e conciliação independente ao final.
3. Base: tabela original, filtros nativos, cabeçalho congelado e referência da fonte.

Fluxo: Base e filtros do Painel alimentam Calculos; Painel lê agregados. Os controles de auditoria não alimentam os resultados.

## Interações
- Data inicial e final inclusivas.
- Plano: Todos, Core, Standard, Ultimate.
- Tipo: Todos, Monthly, Quarterly, Annual.
- Renovação: Todas, Yes, No.
- Os indicadores, os três gráficos e o resumo de adicionais obedecem ao mesmo recorte.
- Sem registros: total e quantidade zero; ticket e proporções exibem n.a.
- Datas ausentes, não numéricas ou invertidas: aviso explícito, resultados indisponíveis.
- Listas suspensas e validação de datas. Não apresentar listas como segmentações de dados nativas.
- Links de navegação entre as três abas.

## Cálculos
- Total: soma de Total Value dos registros elegíveis.
- Quantidade: contagem de registros elegíveis, com IDs únicos na base fornecida.
- Ticket: total / quantidade, com guarda para zero.
- Renovação automática: quantidade elegível com Yes / quantidade elegível.
- Bruto: preço do plano + preço EA normalizado + preço Minecraft.
- Cupons: soma de Coupon Value. Incidência: registros com cupom positivo / quantidade.
- Adicionais: EA + Minecraft. Participação: adicionais / bruto, antes dos cupons.
- Evolução: soma por mês da data de início, respeitando todos os filtros.
- Ranking: planos ordenados pelo total filtrado, com desempate estável.
- Conciliação: soma de Total Value versus bruto menos cupons, além de diferenças por linha e duplicidade de ID.

## Direção visual
Redesign solicitado: tema dark inspirado na interface de um console, com composição assimétrica. Fundo preto azulado, cartões em grafite, verde elétrico, ciano e violeta. Logo Xbox real, botões A/B/X/Y e ícones vetoriais próprios de controle, renovação, comprovantes e desempenho. Identidade Xbox reconhecível, sem transformar gráficos ou números em imagens.

O total ganha um painel vertical de destaque, com quantidade e ticket integrados. A evolução ocupa a área central, o ranking fica à esquerda e os adicionais têm um painel independente. Os cinco filtros continuam nas células originais para preservar todas as dependências. Os links de navegação e a aba Base serão revisados para contraste no modo escuro.

Logo e ícones são imagens incorporadas, disponíveis offline. A fonte do logo e a autoria dos ícones serão documentadas. As imagens não funcionarão como botões falsos: ações reais usam hiperlinks ou validações de dados do Excel.

## Atualização
Capacidade de cálculo: 1.000 registros nas linhas 7 a 1006 da Base. A tabela original tem apenas as linhas fornecidas. Novos registros podem ser adicionados na sequência, mantendo a estrutura, até o limite informado. Fórmulas auxiliares pré-preparadas não são dados de demonstração. Acima desse limite, ampliar os intervalos e as fórmulas conforme documentação.

## Critérios de aceite
- Reconciliar R$ 7.633,00, 295 registros, R$ 2.935,00 em planos, R$ 2.940,00 EA, R$ 3.880,00 Minecraft e R$ 2.122,00 cupons.
- Testar filtros individualmente, combinação de filtros, período sem registros e datas inválidas.
- Testar uma linha adicional temporária e restaurar o arquivo final.
- Confirmar três gráficos nativos conectados a células e tabela de dados com filtros.
- Verificar visualmente todas as abas e ausência de erros de fórmula nos resultados.
- Informar explicitamente o aplicativo usado na verificação e eventuais limites.

## Entrega
Xbox_Sales.xlsx, README.md, este schema, docs com cálculos e testes, base original atribuída e capturas reais da planilha em images. Nomes sem número de versão. Repositório sugerido: xbox-sales-excel. A publicação será feita quando houver repositório de destino informado pelo usuário.

## Aperfeiçoamento com a referência enviada
Logo Xbox incorporado nas três abas, preservação dos filtros, indicadores e dados, remoção de bordas residuais do painel e revisão do texto de contexto dos cupons. Conferir se imagens deixam livres os links e as entradas. O símbolo será mantido em verde nas três abas, a partir do mesmo desenho vetorial da referência enviada. As capturas devem vir do arquivo recalculado.
