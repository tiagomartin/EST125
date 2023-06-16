---
title: Avaliação de modelos
author: Tiago Pereira
date: '2023-06-07'
slug: index.pt-br
categories:
  - Classificação
  - Predição
  - Machine Learning
tags:
  - Classificação
  - Predição
summary: 'Avaliação de Modelos, matriz de confusão, métricas, curva ROC'
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

## Avaliação de modelos

---

Você já se perguntou como saber se um modelo de machine learning está **realmente funcionando**? É aí que entra a **avaliação** de modelos!

---

<table>
<tr>
<th>Avaliação de Modelos</th>
<th></th>
</tr>
<tr>
<td>
<img src="detetive.jpg" width="2000">
</td>
<td>
A <span style="font-weight: bold; color: #54787d">avaliação de modelos</span> de machine learning é como um <span style="font-weight: bold; color: #54787d">detetive</span> investigando um caso
</td>
</tr>
</table>

---

O nosso modelo é um **herói** ou um **impostor**?

![hero](https://media4.giphy.com/media/ek4CUx2FONgHaMz9V5/giphy-downsized-medium.gif)  

---

{{<slide background-color="#54787d">}} 

## Matriz de confusão

---


Permite a visualização do **desempenho** do algoritmo

&nbsp;

<img src="mc.png" width="700">

---



- <span style="font-weight: bold; color: #54787d">VP (Verdadeiro Positivo):</span> objeto da classe positiva classificado como positivo 

&nbsp;

- <span style="font-weight: bold; color: #54787d">VN (Verdadeiro Negativo):</span> objeto da classe negativa classificado como negativo

---

- <span style="font-weight: bold; color: #54787d">FP (Falso Positivo):</span> objeto da classe negativa classificado como positivo. Também conhecido como **alarme falso** ou **Erro tipo 1**

&nbsp;

- **FN (Falso Negativo):** objeto da classe positiva classificado como negativo. É também conhecido como **Erro Tipo 2**	

---

<table>
<tr>
<th>Exemplos</th>
<th></th>
</tr>
<tr>
<td>
<img src="mc_cliente.png" width="2610">
</td>
<td>
<img src="mc_paciente.png" width="4000">
</td>
</tr>
</table>


---

<table>
<tr>
<th>Acurácia</th>
<th></th>
</tr>
<tr>
<td>
<img src="acc.jpg" width="2610">
</td>
<td>
Mede a <span style="font-weight: bold; color: #54787d">proporção de previsões corretas</span> do modelo em relação ao total de previsões feitas. 
</td>
</tr>
</table>

É como sua nota em uma prova!

---

<table>
<tr>
<th>Acurácia</th>
<th></th>
</tr>
<tr>
<td>
<img src="mc.png" width="1000">
</td>
<td>
<img src="acc_form.jpg" width="2200"> 
</td>
</tr>
</table>

A **Taxa de Erro Aparente** do classificador é dada por

{{< math >}}$$TEA = 1 - ACC$${{< /math >}}

---

<table>
<tr>
<th>Exemplos</th>
<th></th>
</tr>
<tr>
<td>
<img src="mc_cliente_acc.png" width="1500">
</td>
<td>
<img src="acc_form_clientes.jpg" width="2000">
</td>
</tr>
<tr>
<td>
<img src="mc_paciente_acc.png" width="1500">
</td>
<td>
<img src="acc_form_pacientes.jpg" width="2000">
</td>
</tr>
</table>

---

Mas será que a **acurácia** é suficiente para avaliar nossos modelos de forma **precisa**? 

&nbsp;

Às vezes, uma **única métrica** não é capaz de nos contar toda a história.

---

<table>
<tr>
<th>Precisão</th>
<th></th>
</tr>
<tr>
<td>
<img src="precision.jpg" width="1000">
</td>
<td>
Ela nos diz quantas das <span style="font-weight: bold; color: #54787d">previsões positivas</span> foram realmente corretas. 
</td>
</tr>
</table>

---

<table>
<tr>
<th>Precisão</th>
<th></th>
</tr>
<tr>
<td>
<img src="mc.png" width="1800">
</td>
<td>
<img src="precision_form.jpg" width="2200"> 
</td>
</tr>
</table>

Porcentagem de verdadeiros positivos dentre todos os objetos classificados como positivos

---

<table>
<tr>
<th>Exemplos</th>
<th></th>
</tr>
<tr>
<td>
<img src="mc_cliente_prec.png" width="1500">
</td>
<td>
<img src="prec_form_clientes.jpg" width="2000">
</td>
</tr>
<tr>
<td>
<img src="mc_paciente_prec.png" width="1500">
</td>
<td>
<img src="prec_form_pacientes.jpg" width="2000">
</td>
</tr>
</table>

---

<table>
<tr>
<th>Sensibilidade</th>
<th></th>
</tr>
<tr>
<td>
<img src="recall.jpg" width="1200">
</td>
<td>
Mede a <span style="font-weight: bold; color: #54787d">proporção de casos positivos reais</span> que foram encontrados pelo modelo 
</td>
</tr>
</table>


---


<table>
<tr>
<th>Sensibilidade</th>
<th></th>
</tr>
<tr>
<td>
<img src="mc.png" width="1800">
</td>
<td>
<img src="sens_form.jpg" width="2200"> 
</td>
</tr>
</table>

Também conhecida por **Recall** ou **Taxa de Verdadeiros Positivos (TVP)**

---

<table>
<tr>
<th>Exemplos</th>
<th></th>
</tr>
<tr>
<td>
<img src="mc_cliente_sens.png" width="1500">
</td>
<td>
<img src="sens_form_clientes.jpg" width="2000">
</td>
</tr>
<tr>
<td>
<img src="mc_paciente_sens.png" width="1500">
</td>
<td>
<img src="sens_form_pacientes.jpg" width="2400">
</td>
</tr>
</table>

---


<table>
<tr>
<th>Especificidade
</th>
<th></th>
</tr>
<tr>
<td>
<img src="espec.jpg" width="1200">
</td>
<td>
 Ajuda a identificar a capacidade do modelo em reconhecer <span style="font-weight: bold; color: #54787d">corretamente as amostras negativas</span>   
</td>
</tr>
</table>

---

<table>
<tr>
<th>Especificidade</th>
<th></th>
</tr>
<tr>
<td>
<img src="mc.png" width="1800">
</td>
<td>
<img src="espec_form.jpg" width="2200"> 
</td>
</tr>
</table>

Também conhecida por **Taxa de Verdadeiros Negativos (TVN)**

---

<table>
<tr>
<th>Exemplos</th>
<th></th>
</tr>
<tr>
<td>
<img src="mc_cliente_espec.png" width="1500">
</td>
<td>
<img src="espec_form_clientes.jpg" width="2000">
</td>
</tr>
<tr>
<td>
<img src="mc_paciente_espec.png" width="1500">
</td>
<td>
<img src="espec_form_pacientes.jpg" width="2400">
</td>
</tr>
</table>

---



<table>
<tr>
<th>Taxa de Falso Positivo
</th>
<th></th>
</tr>
<tr>
<td>
<img src="fpr.jpg" width="2200">
</td>
<td>
 Ela mede a <span style="font-weight: bold; color: #54787d">proporção de amostras negativas</span> classificadas como positivas pelo modelo
</td>
</tr>
</table>

---

<table>
<tr>
<th>Especificidade</th>
<th></th>
</tr>
<tr>
<td>
<img src="mc.png" width="1800">
</td>
<td>
<img src="fpr_form.jpg" width="2200"> 
</td>
</tr>
</table>



---

<table>
<tr>
<th>Exemplos</th>
<th></th>
</tr>
<tr>
<td>
<img src="mc_cliente_espec.png" width="1500">
</td>
<td>
<img src="fpr_form_clientes.jpg" width="2000">
</td>
</tr>
<tr>
<td>
<img src="mc_paciente_espec.png" width="1500">
</td>
<td>
<img src="fpr_form_pacientes.jpg" width="2400">
</td>
</tr>
</table>

---

<table>
<tr>
<th>F<sub>1</sub> - Score
</th>
<th></th>
</tr>
<tr>
<td>
<img src="f1.jpg" width="2200">
</td>
<td>
 Ele leva em consideração tanto <span style="font-weight: bold; color: #54787d">precisão</span> quanto a  <span style="font-weight: bold; color: #54787d">sensibilidade</span>, dando uma medida balanceada do desempenho do modelo.
</td>
</tr>
</table>

---

{{< math >}}$$F_1 \text{-score} = 2 \times \dfrac{\text{Precisão} \times \text{Sensibilidade}}{\text{Precisão} + \text{Sensibilidade}}$${{< /math >}}

&nbsp;

O F<sub>1</sub>-score é como um **equilibrista** em uma corda bamba. 

---

{{<slide background-color="#54787d">}} 

## Curva ROC

---

A **Curva ROC** é como um mapa que nos guia pela **sensibilidade** e pelos **falsos positivos** do modelo em diferentes configurações. 

&nbsp;

Ela nos mostra o quão bem nosso modelo pode **distinguir** entre as classes.

---

<img src="roc.jpg" width="1000">

---

Representa o número de vezes que o classificador **acertou a predição** contra o número de vezes que o classificador **errou a predição**

---

A área sob a curva ROC, conhecida como **AUC-ROC**, é uma métrica comumente utilizada para avaliar o desempenho global do modelo. 

&nbsp;

Quanto **maior a AUC-ROC**, **melhor** é o desempenho do modelo em discriminar corretamente as classes.

---

<img src="auc.jpg" width="1000">
