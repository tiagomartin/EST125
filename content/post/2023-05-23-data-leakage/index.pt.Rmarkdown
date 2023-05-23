---
title: 'Data Leakage: um problema invisível que pode comprometer seu projeto de machine
  learning'
author: Tiago Pereira
date: '2023-05-23'
slug: data-leakage
categories:
  - Conceitos
  - Pré-processamento
  - Data Leakage
tags:
  - Conceitos
  - EDA
subtitle: 'O vazamento de dados é uma vulnerabilidade que compromete a confiabilidade das métricas de avaliação do modelo, levando a resultados questionáveis e imprecisos.'
summary: 'O vazamento de dados é uma vulnerabilidade que compromete a confiabilidade das métricas de avaliação do modelo, levando a resultados questionáveis e imprecisos.'
authors: []
lastmod: '2023-05-23T14:27:04-03:00'
featured: no
draft: no
image:
  caption: ''
  focal_point: ''
  preview_only: no
projects: []
---

Olá pessoal, beleza?

Hoje vamos falar sobre um problema muitas vezes não detectado, mas que pode comprometer, e muito, os resultados de seu modelo preditivo: o vazamento de dados!

Analisar dados tornou-se uma peça fundamental para o sucesso das empresas em um mundo cada vez mais orientado por dados. A capacidade de extrair insights valiosos a partir de dados tem impulsionado a tomada de decisões e melhorado os resultados em várias organizações. No entanto, um desafio crítico enfrentado nesses projetos é o vazamento de dados, conhecido como _"data leakage"_. 

Neste post, exploraremos como realizar uma análise de dados de forma a evitar o data leakage, garantindo a integridade e a confiabilidade dos modelos de machine learning.

## O que é Data Leakage?

Antes de mais nada, é fundamental compreendermos o conceito de "vazamento de dados". O _data leakage_ ocorre quando informações que não estariam disponíveis durante o uso prático do modelo são acidentalmente incluídas no processo de treinamento ou validação. Isso pode levar a resultados ilusoriamente bons durante a fase de desenvolvimento, mas que se mostram ineficazes quando o modelo é aplicado a novos dados. O vazamento de dados é um desafio complexo, pois muitas vezes é sutil e difícil de detectar. Compreender suas formas e causas é essencial para evitar resultados distorcidos.


## O que pode causar Data Leakage?

Existem várias causas comuns de data leakage, e é essencial identificá-las para evitar sua ocorrência. Vamos listar as mais comuns...

#### Data Leakage Temporal: Quando o tempo é um fator crítico

Em muitos casos, os dados estão organizados em ordem cronológica, e é importante respeitar essa estrutura durante a divisão dos conjuntos de treinamento, validação e teste. Vazar dados futuros para o conjunto de treinamento pode levar a um modelo enviesado, uma vez que ele terá acesso a informações que não estariam disponíveis no mundo real.
  
#### Data Leakage de Fonte: Quando a fonte dos dados é comprometida 

Ocorre quando as informações provenientes de fontes não disponíveis no momento da previsão são incluídas no conjunto de treinamento. O conjunto de teste deve ser usado apenas para avaliar o desempenho final do modelo, e não para tomar decisões no processo de desenvolvimento. Utilizar informações do conjunto de teste, como estatísticas descritivas ou variáveis criadas a partir desses dados, pode levar a um modelo superestimado. 

#### Data Leakage de Alvo: Quando o próprio alvo está vazando informações

Esse tipo de vazamento ocorre quando o próprio alvo (variável a ser prevista) contém informações que não devem estar disponíveis no momento da previsão. Isso pode acontecer quando a variável alvo é alterada antes da previsão ser realizada, introduzindo assim um viés nos resultados. Por exemplo, considere um modelo de classificação de spam em e-mails. Suponha que o objetivo seja prever se um e-mail é spam ou não com base no conteúdo e nos atributos do e-mail. No entanto, durante o treinamento do modelo, a variável alvo (indicando se o e-mail é spam ou não) é atualizada após a análise do conteúdo do e-mail, e o modelo então, terá acesso a informações futuras que não estariam disponíveis no momento real da classificação. Isso pode levar a uma avaliação enganosa do modelo, pois ele estará utilizando informações que não seriam conhecidas no momento em que a classificação real seria realizada. Quando o modelo for aplicado em tempo real para classificar novos e-mails, ele não terá acesso a essas informações futuras e sua capacidade de previsão será comprometida, resultando em uma menor eficácia na detecção de spam. 


![over](over.jpeg)

## Overfitting: Quando o modelo se ajusta demais aos dados de treinamento

Independente de sua causa, o vazamento de dados pode levar a um superajuste do modelo aos dados de treinamento, fenômeno conhecido como _overfitting_, resultando em um desempenho fraco em dados não vistos. O modelo pode memorizar os padrões de vazamento e não conseguir generalizar corretamente para novos dados. Além disso, pode causar resultados inconsistentes e imprecisos, uma vez que informações irrelevantes ou incorretas são utilizadas no processo de treinamento. Isso pode levar a decisões errôneas e impactar negativamente os resultados esperados.

## Como evitar o vazamento de dados nos modelos de machine learning?

Prevenir o vazamento de dados é essencial para garantir a qualidade e a confiabilidade dos modelos de machine learning. Antes de começar qualquer projeto de machine learning, é fundamental ter um conhecimento profundo dos dados. Isso envolve entender a estrutura dos dados, sua qualidade, possíveis vieses e a relação entre as variáveis. Ao conhecer os dados de forma abrangente, é possível identificar potenciais fontes de _data leakage_.


![train+test+samples](https://media4.giphy.com/media/zIOdLMZDcBDc2gk6vV/giphy.gif)  


#### Divisão adequada dos conjuntos de dados

Outro ponto que se deve levar em consideração é a correta divisão dos conjuntos de treinamento, validação e teste. Essa prática é essencial para evitar o vazamento de dados. A técnica mais comum é usar uma divisão temporal, se for o caso, garantindo que os dados futuros não sejam incluídos no conjunto de treinamento. Além disso, é importante ter um conjunto de validação para ajustar os hiperparâmetros do modelo e um conjunto de teste para avaliar seu desempenho final. Lembre-se que todas imputações de _missing values_ devem ser realizadas a partir de informações do **conjunto de treinamento**.

#### Feature engineering cuidadosa

A engenharia de recursos desempenha um papel crítico na criação de variáveis úteis para o modelo. No entanto, é necessário ter cuidado ao criar variáveis que não estariam disponíveis durante a aplicação prática. É importante garantir que todas as variáveis criadas sejam baseadas apenas em informações disponíveis até o momento em que a previsão é feita. 

#### Validação cruzada apropriada

A validação cruzada é uma técnica útil para avaliar o desempenho do modelo. No entanto, é importante aplicá-la corretamente, garantindo que os passos de pré-processamento, engenharia de recursos e modelagem sejam realizados separadamente para cada dobra da validação cruzada. Isso evita o vazamento de informações entre as dobras e produz resultados mais realistas.

## Em resumo...

O vazamento de dados representa um desafio oculto na análise de dados e pode comprometer a precisão e a confiabilidade dos modelos de machine learning. No entanto, adotar estratégias adequadas de prevenção de vazamentos pode ajudar a mitigar esses problemas e garantir a integridade dos modelos.

Ao compreender as causas do data leakage e adotar práticas adequadas de análise de dados, as organizações podem obter resultados mais confiáveis e maximizar o valor de seus projetos de machine learning.

A conscientização sobre o data leakage é essencial para os profissionais de análise de dados e cientistas de dados. Ao adotar medidas proativas para prevenir o vazamento de dados, podemos construir modelos confiáveis e tomar decisões mais informadas, impulsionando o sucesso das empresas e maximizando o valor dos dados.


Até breve! 👋


