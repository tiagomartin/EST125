---
title: Avaliação de modelos - parte 02
author: Tiago Pereira
date: '2023-06-15'
slug: avalia-o-de-modelos-parte-02
categories:
  - Classificação
  - Predição
  - Machine Learning
tags:
  - Classificação
  - Predição
summary: 'Função custo para predição, validação holdout, validação cruzada, trade-off bias-variância'
authors: []
slides:
  theme: white
  highlight_style: dracula
  diagram: yes
  diagram_options:
    theme: base
  reveal_options:
    controls: yes
    progress: yes
    slide_number: c/t
    center: yes
    rtl: no
    mouse_wheel: yes
    transition: fade
    transitionSpeed: default
    background_transition: slide
    touch: yes
    loop: no
    menu_enabled: yes
---

{{<slide background-color="#54787d">}} 

## Avaliação de modelos de predição

---

Seja `\(d_j\)`, `\(j = 1,\cdots, n\)`, a resposta desejada para o objeto `\(j\)` e `\(y_j\)` a resposta estimada (predita) do algoritmo, obtida a partir de uma entrada `\(\mathbf{x_j}\)` apresentada ao algoritmo.

---

Podemos definir então, `\(e_j = d_j - y_j\)` como sendo a diferença entre o valor observado e o valor predito para o objeto `\(j\)`.

---

<table>
<tr>
<th>Erro quadrático médio</th>
<th>Raiz do erro quadrático médio</th>
</tr>
<tr>
<td>
{{< math >}}$$MSE =\dfrac{1}{n} \displaystyle{\sum_{j=1}^n e_j^2}$${{< /math >}}
</td>
<td>
{{< math >}}$$RMSE =\sqrt{\dfrac{1}{n} \displaystyle{\sum_{j=1}^n e_j^2}}$${{< /math >}}
</td>
</tr>
</table>

---

<table>
<tr>
<th>Erro absoluto médio</th>
<th>Média percentual absoluta do erro</th>
</tr>
<tr>
<td>
{{< math >}}$$MAE = \dfrac{1}{n} \displaystyle{\sum_{j=1}^n |e_j|}$${{< /math >}}
</td>
<td>
{{< math >}}$$MAPE = \dfrac{1}{n} \displaystyle{\sum_{j=1}^n |e_j/d_j|}\times 100$${{< /math >}}
</td>
</tr>
</table>

---


<table>
<tr>
<th>Qual o melhor modelo?</th>
<th></th>
</tr>
<tr>
<td>
Suponha que tenhamos dados simulados utilizando o seguinte modelo:
<img src="fig01.png" width="4200">
</td>
<td>
<img src="fig02.png" width="8200">
</td>
</tr>
</table>

---

Podemos estimar diversos modelos `\(y\)` que predizem o verdadeiro valor de `\(d\)`

<img src="fig03.png" width="500">

---

Nosso interesse está em treinar o modelo e avaliar a sua capacidade de generalização

<img src="fig04.png" width="500">

---

{{<slide background-color="#54787d">}} 

## Validação holdout

---

<table>
<tr>
<th>Validação holdout</th>
<th></th>
</tr>
<tr>
<td>
<span style="font-weight: bold; color: #54787d">Dados originais:</span> treinamento e teste

<span style="font-weight: bold; color: #54787d">Dados de treinamento:</span> treinamento e validação
</td>
<td>
<img src="houlout.png" width="1500">
</td>
</tr>
</table>

---


<table>
<tr>
<th>Exemplo</th>
<th></th>
</tr>
<tr>
<td>
Vamos avaliar a relação entre Frequência Cardíaca e Idade de 270 pacientes
</td>
<td>
<img src="fig05.png" width="1500">
</td>
</tr>
</table>

---

70% da base para treino e 30% para validação

<table>
<tr>
<th></th>
<th></th>
</tr>
<tr>
<td>
<img src="fig06.png" width="1500">
</td>
<td>
<img src="fig07.png" width="1500">
</td>
</tr>
</table>

---

{{<slide background-color="#54787d">}} 

## Validação cruzada k-fold

---

**Dados de treinamento:** `\(k\)` partes iguais. 

**Treina** com `\(k-1\)` partes, e **valida** com uma

<img src="cross_validation.png" width="1500">

---

<table>
<tr>
<th>Exemplo</th>
<th></th>
</tr>
<tr>
<td>
<img src="fig08.png" width="1500">
</td>
<td>
<img src="fig09.png" width="2300">
</td>
</tr>
</table>

---

{{<slide background-color="#54787d">}} 

## Trade-off bias-variância

---

Imagine que você está tentando **acertar** um alvo com dardos. Seus arremessos podem ser agrupados de três maneiras diferentes:

---

**Grupo de alto viés (bias)**

&nbsp;

Seus arremessos são **consistentemente agrupados longe do alvo**, mas **próximos uns dos outros**. 

&nbsp;

Isso indica um **alto viés**, pois você está fazendo arremessos incorretos, mas de forma **consistente**.

---

**Grupo de alta variância**

&nbsp;

Seus arremessos estão **espalhados por toda a área**, **longe do alvo e uns dos outros**. 

&nbsp;

Isso indica **alta variância**, pois seus arremessos são **inconsistentes e imprevisíveis**. 

---

**Grupo equilibrado**

&nbsp;

Seus arremessos estão **agrupados próximo ao alvo** e também estão **próximos uns dos outros**. 

&nbsp;

Isso é o **equilíbrio** entre **viés** e **variância**, onde você está acertando o alvo de forma **consistente** e **precisa**. 

---

<img src="bias_variance.png" width="800">

---

### Bias - o erro sistemático

&nbsp;

O **bias**, também chamado de víes, representa o **erro sistemático** do modelo, ou seja, a diferença entre as **previsões** do modelo e os **valores reais**. 

---

O **bias** está relacionado à habilidade do modelo em se ajustar aos dados, ou seja, se o seu problema é um **underfitting**, o seu modelo tem um **alto bias**. 

&nbsp;

O erro no treinamento é **alto** e **igual** ao erro na validação

---

### Variância - a instabilidade

&nbsp;

A **variância** representa a **instabilidade** do modelo, ou seja, como as previsões variam para diferentes conjuntos de treinamento. 

---

A **variância** está relacionada a habilidade do modelo se **ajustar** a novos dados, ou seja, se o seu problema é um **overfitting**, o seu modelo tem uma **alta variância**.

&nbsp;

O erro no treinamento é **baixo** e **menor** que o erro na validação

---

<table>
<tr>
<th>Bias vs. Variância</th>
<th></th>
</tr>
<tr>
<td>
Voltemos ao nosso modelo simulado:
<img src="fig01.png" width="4200">
</td>
<td>
<img src="fig02.png" width="8200">
</td>
</tr>
</table>

---

Vamos ajustar um modelo polinomial de **grau 2**

<img src="fig12.png" width="500">

---

<table>
<tr>
<th>Bias vs. Variância</th>
<th></th>
</tr>
<tr>
<td>
<img src="fig13.png" width="5200">
</td>
<td>
<img src="fig14.png" width="8200">
</td>
</tr>
</table>

---

Vamos ajustar um modelo polinomial de **grau 10**

<img src="fig15.png" width="500">

---

<table>
<tr>
<th>Bias vs. Variância</th>
<th></th>
</tr>
<tr>
<td>
<img src="fig16.png" width="5200">
</td>
<td>
<img src="fig17.png" width="8200">
</td>
</tr>
</table>

---

 O nosso objetivo é reduzir o bias e a variância o máximo que pudermos, entretanto, nos deparamos com um **trade-off** entre **under** e **overfitting**.
 
---

Quanto **maior a complexidade** do modelo, **maior a variância** e **menor o bias**

<img src="bias-variance_tradeOff.png" width="1500">

---

Algumas medidas podem ajudar a encontrar o nível de complexidade ideal:

  - **Alto Bias:** Adicionar mais variáveis e/ou adicionar novas variáveis a partir de combinações das variáveis existentes
  
  - **Alta Variância:** Selecionar um conjunto menor de variáveis
  
---

<table>
<tr>
<th>Bias vs. Variância:</th>
<th>Tamanho da amostra</th>
</tr>
<tr>
<td>
<img src="alto_bias2.png" width="1500">
</td>
<td>
<img src="alta_variancia2.png" width="1500">
</td>
</tr>
</table>
