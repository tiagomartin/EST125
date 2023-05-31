---
title: Tarefa de classificação - parte 03
author: Tiago Pereira
date: '2023-05-30'
slug: tarefa-de-classifica-o-parte-03
categories:
  - Classificação
tags:
  - Classificação
summary: 'Random Forests e SVM'
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

## Random Forests

---

**Random Forests** é um algoritmo de aprendizado de máquina que combina várias **árvores de decisão** independentes para realizar tarefas de classificação ou regressão. 

---

Ele pertence à categoria de **métodos ensemble**, que buscam melhorar a precisão e robustez das predições combinando diferentes modelos para se obter um único resultado.

---

{{<slide background-color="#54787d">}} 

## Construção de um Random Forests

---

### Etapas

&nbsp;

- Amostragem aleatória com reposição (bootstrap) dos dados de treinamento
- Construção de uma árvore de decisão para cada amostra bootstrap
- Votação (classificação) ou média (regressão) dos resultados das árvores

---

![random](random.jpeg)

---

### Amostragem Bootstrap

&nbsp;

- Seleciona-se aleatoriamente uma amostra dos dados de treinamento com reposição 
- Diferentes amostras podem conter itens duplicados ou omitir outros
- Garante diversidade nas árvores construídas

---

Para cada amostra _bootstrap_ gerada, os dados são divididos utilizando os atributos que maximizem a **pureza dos nós**

---

- **Critérios de divisão:** Gini Index, Entropia, Ganho de Informação, etc.

- Construção recursiva até atingir **critérios de parada** (profundidade máxima, pureza mínima)

---

### Como realizar a classificação?

&nbsp;

- A classificação é obtida por **votação majoritária** dos resultados de cada árvore
- Cada árvore possui um peso igual na votação final
- **Resultado:** classe mais frequente entre todas as árvores

---

![random](rf_class.jpg)

{{< spoiler text= "Qual a classe predita?" >}}
<p style="color: green"> Pela regra da maioria: classe 1 </p>
{{< /spoiler >}}

---

### Vantagens do Random Forests

&nbsp;

- Trata efetivamente problemas de **overfitting**
- Lida bem com **dados ausentes** e **valores discrepantes**

---

- Capaz de lidar com **atributos de diferentes tipos** (numéricos, categóricos)
- Reduz a **variância** e melhora a **precisão** em comparação com uma única árvore

---


{{<slide background-color="#54787d">}} 

## Support Vector Machine (SVM)

---

O **SVM** (Support Vector Machine) é um algoritmo de aprendizado de máquina amplamente utilizado em problemas de classificação.

&nbsp;

Ele é especialmente útil quando os dados são **não linearmente separáveis** ou quando se deseja encontrar um **hiperplano ótimo** para separação das classes.

---

### Princípio básico

&nbsp;

O objetivo do SVM é encontrar um **hiperplano de separação ótimo** que maximize a **margem** entre as classes.

---

### Hiperplano de Separação

&nbsp;


Para problemas de classificação binária, um **hiperplano de separação** é uma superfície que divide o espaço de características em duas regiões, uma para cada classe. Neste caso, esse hiperplano é uma **reta**!

&nbsp;

Em problemas **multiclasse**, pode ser um plano ou uma superfície mais complexa.

---

![hiper](hiper.jpg)

Temos aqui 4 hiperplanos (A, B, C e D). Qual o melhor?

---

### Vetores de Suporte

&nbsp;

Os **vetores de suporte** são os pontos de dados mais próximos ao hiperplano de separação. Eles são fundamentais para o SVM, pois definem a posição do hiperplano e a **margem**.

---

### Margem

&nbsp;

A **margem** é a distância entre o hiperplano de separação e os vetores de suporte mais próximos. O objetivo do SVM é **maximizar a margem**, pois isso aumenta a capacidade de **generalização** do modelo.

---

![SVM](svm.jpeg)

---

Para encontrar o **hiperplano ótimo**, caímos em um problema de otimização com restrição, que pode ser resolvido utilizando a técnica dos **Multiplicadores de Lagrange**!

---

Mas e se tivermos problemas **não linearmente separáveis**?

![svm](svm01.jpg)

---

O SVM é um algoritmo que inicialmente trabalha com dados **linearmente separáveis**. No entanto, muitas vezes encontramos conjuntos de dados que não podem ser separados por um **hiperplano linear**. É aí que entra o **Kernel Trick**.

---


{{<slide background-color="#54787d">}} 

## Kernel Trick

---

O **Kernel Trick** (Truque do Kernel) nos permite **mapear os dados** para um espaço de características de **dimensão superior**, onde se tornam linearmente separáveis. 

---

Isso é feito através de uma **função** chamada **kernel**, que calcula o produto interno entre dois vetores nesse espaço de características.

---

![svm](svm02.jpg)

---

Existem diferentes **tipos de kernels** que podem ser utilizados, como o **linear**, **polinomial**, **RBF (radial basis function)** e **sigmoide**. Cada um desses kernels possui suas características e é escolhido com base nas características do conjunto de dados e no tipo de separação não linear esperada

---

![svm](kernel.jpg)

---

### Escolha do kernel

&nbsp;

A escolha do kernel adequado é importante para obter um bom desempenho do SVM. É necessário analisar as características dos dados e testar diferentes kernels para encontrar o que **melhor se adapta** ao problema em questão

---

O uso do **Kernel Trick** pode melhorar o desempenho do SVM ao permitir que ele modele relações não lineares nos dados. No entanto, é preciso ter cuidado para evitar o **overfitting**, garantindo que o modelo generalize bem para dados não vistos.

---


{{<slide background-color="#54787d">}} 

## SVM para problemas multiclasse

---

O SVM como definido funciona para **duas classes**. O que fazemos então se tivermos **mais de duas** classes?

---

### One-vs-One (OVO)

&nbsp;

Nessa abordagem, é criado um **classificador SVM** para cada **par de classes** possível. Cada classificador é usado para classificar uma instância de entrada e a **classe com mais votos** é selecionada como a **classe final**.

---

<img src="OVO.png" width="700">

---

Essa abordagem pode ser **computacionalmente mais intensiva** em problemas com um grande número de classes, pois requer treinar um número maior de classificadores

---

### One-vs-All (OVA)

&nbsp;

Essa abordagem consiste em treinar **um classificador SVM para cada classe**, onde cada classificador é treinado para distinguir uma classe específica das demais classes combinadas.

---

Durante a fase de teste, cada classificador é usado para classificar uma instância de entrada e a classe com a **maior probabilidade** é selecionada como a classe final.

---

<img src="OVA.png" width="700">
