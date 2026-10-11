# [Churn Streaming]

![image](https://github.com/danielesantiago/TemplatePED/assets/64613885/cc24a702-46b8-4263-a764-8c65c56f02ac)


## 📌 Visão Geral
Este projeto analisa a base de clientes de um um "serviço de streaming por assinatura", para entender "quem cancela, por quê e em que momento da vida do cliente", o cancelamento (churn) acontece. Utilizamos "análse exploratória de dados (limpeza, análise univariada e análise bivariada) e frameworks de negócio (cohort, RFM e Pareto)** para transformar um extrato bruto de clientes em hipóteses acionáveis sobre retenção.

📄 [Veja o template da apresentação](https://github.com/profrenatabiaggi/template/blob/master/reports/figures/Template_Case.pptx)

📄 [Veja o template do notebook][(https://github.com/profrenatabiaggi/template/blob/master/notebooks/Case_Fraude.ipynb)](https://github.com/adrianabratfisch/streaming_churn/tree/master/notebooks)

## 💼 Entendimento do Negócio

Em um serviço de assinatura, reter um cliente custa muito menos do que adquirir um novo - por isso, entender o churn é uma das análises de maior impacto financeiro. A empresa desse caso, desconfia que vem perdendo assinantes, mas não sabe quem cancela, por que cancela, nem em que momento da relação isso acontece. Este projeto explora os dados para responder a estas perguntas, antes de qualquer modelo preditivo.

**Tipos de Análise Realizados:**
- Anãlise Univariada com Limpeza e TRatamento de dados
- Anãlise Bivariada (relação de cada variável com o Churn)
- Anãlise de Retenção por Cohort
- Segmentação de clientes com RFM adaptado para assinatura
- Anãlise de Pareto dos motivos do cancelamento.

**Principais Indicadores Chave de Desempenho:**
- Taxa de Churn (geral e por segmento)
- Retenção por safra de assinatura (Cohort)
- NPS por grupo de Churn
- Tempo de vida do cliente (meses por assinatura)

## 📊 Análise do Modelo Atual

A base bruta chegou com diversos problemas de qualidade típicos de um extrato exportado ás pressas de múltiplos sistemas: valores em escalas misturadas, categorias escritas de várias formas, ausências disfarçadas e datas armazenadas como textos. A primeira etapa do projeto foi diagnosticar e tratar esses problemas - porque nenhuma conclusão é confiável sobre um dado sujo.
Um cuidado central da anãlise foi o viés de maturação: clientes muito recentes aparecem como "não churn" apenas porque ainda não tiveram tempo de cancelar. Para comprarar os grupos de forma justa, a anãlise de churn considerou apenas clientes com pelo menos 220 dias de assinatura - uma premissa assumida e registrada explicitamente.

## 🛠 Pré-processamento 
O pré-processamento foi conduzdo com Python, tratando cada problema de qualidade de forma justificasa (corrigir, remover, manter ou imputar), e criando as variáveis necessárias para os frameworks.

_Considerações Importantes:_
1. Variáveis de engajamento (dias ativos, recencia, horas assistidas) são contaminadas pelo próprio Churn. (vazamento de target) - quem cancelou, parou de usar porque saiu.= não o contrário - e por isso não foram usadas para explicar o Churn.

   
_Etapas do Pré-processamento:
1. Remoção de clientes duplicados (cliente_id repetido
2. Conversão das colunas de data para o tipo Datetime
3. Padronização de categorias (plano, canal_aquisicao) e tratamento de ausências disfarçadas ("?" na região
4. Correlação de escala em valor_mensal (valores em centavos divididos por 100)
5. Tratamentos de valores impossíveis em idade
6. Feature Engineering recencia, meses assinatura e receita acumulada.

## 🤖 Frameworks e Avaliação

Esse projeto aplica frameworks de análise de negócio para extrair valor dos dados de forma estatística.
* Cohort: matriz de retenção por safra de assinatura, lida por linha, coluna e diagonal.
* RFM adaptado: como não há compra repetida, adaptamos as três dimensões - Recência (dias desde o último acesso), Frequência (uso no último mês) e MOnetário (Valor do plano) - validando a segmentação pela taxa de churn de cada grupo.
* Pareto: concentração dos motivos de cancelamento, para identificar os poucos motivos que respondem pela maioria das saídas.


## 📈 Insights e Conclusões

As principais descobertas da análise:
* O NPS é o sinal mais forte de churn: clientes que cancelaram tinham NPS médio de 4,1 contra 7,4 dos que permaneceram.
* A retenção piorou nas safras mais recentes: comparando o mesmo mês de vida entre coortes, as safras de 2023 retém menos que as de 2022 - um alerta sobre a qualidade da aquisição ou da experiência ao longo do tempo.
* O plano básico tem a maior taxa de cancelamento, emquanto idade, região e ciclo (mensal, anual) praticamente não separarm os grupos.
* Poucos motivos concentram a mairia dos cancelamentos (Pareto), indicando que os esforços devem se concentrar em Preço ou Conteúdos Novos ( a verificar com análise de custos, benchmarking com concorrentes , etc)

  Nota importante: Todas as conclusões são hipóteses embasadas, não relações causais provadas. Confirmar causa exigiria experimentação (ex: testes A/B)

## 📜 Estrutura do Projeto

A estrutura de diretórios do projeto foi organizada da seguinte forma:
```
├── README.md 
├── notebooks 
├── Estatístca.ipynb
 


## 🚧 Próximos Passos

* Investigar a causa da piora da retenção nas safras recentes ( o que mudou na aquisição ou no produto ao longo de 2023)
* Validar as hipóteses de churn com um teste A/B - por exemplo uma ação de retenção direcionada aos clientes nos primeiros meses de vida.
* Construir um modelo preditivo de churn usando apenas as variáveis limpas(não contaminadas) , com o NPS como o principal preditor.
* Aprofundar a análise de funil de onboarding para reduzor o gargalo de conversão inicial.


