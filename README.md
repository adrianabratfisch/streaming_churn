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

   
_Etapas do Pré-processamento no Pipeline:_
1. [Primeira etapa, por exemplo, "Normalização dos Dados"]
2. [Segunda etapa, por exemplo, "Tratamento de Valores Ausentes"]
3. [Terceira etapa, por exemplo, "Codificação de Variáveis Categóricas"]

## 🤖 Modelagem e Avaliação

Utilizamos [insira as ferramentas ou métodos de modelagem usados, por exemplo, "algoritmos de machine learning como XGBoost e RandomForest"] para construir nosso modelo. As métricas de avaliação incluem [insira as métricas usadas, por exemplo, "precisão, recall e a área sob a curva ROC"].


## 📈 Insights e Conclusões

[Resuma os principais insights obtidos e as conclusões do seu projeto. Por exemplo, "Nossa análise revelou que... Isso sugere que..."]

## 📜 Estrutura do Projeto

A estrutura de diretórios do projeto foi organizada da seguinte forma:
```
├── README.md 
├── data
│ ├── processed
│ └── raw
├── models
├── notebooks 
├── reports
│ └── figures 
├── requirements.txt
├── src
│ ├── __init__.py 
│ ├── data
│ │ └── [NomeDoScriptDeDados].py 
│ ├── features
│ │ └── [NomeDoScriptDeFeatures].py 
│ ├── models
│ │ ├── predict_model.py 
│ │ └── train_model.py 

```

## 🚧 Próximos Passos

[Descreva os próximos passos para o seu projeto, por exemplo, "O próximo passo é implementar o modelo em um ambiente de produção para testar sua eficácia em tempo real."]


