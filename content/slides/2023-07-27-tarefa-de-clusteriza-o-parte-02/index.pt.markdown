---
title: Tarefa de clusterização - parte 02
author: Tiago Pereira
date: '2023-07-27'
slug: tarefa-de-clusteriza-o-parte-02
categories:
  - Agrupamento
  - Clusterização
  - Densidade
  - Mean Shift
  - Modelos
  - Redes SOM
tags:
  - Cluster
summary: 'Algoritmo Mean Shift, Métodos baseados em modelos: Redes SOM'
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

## Método Mean Shift

---

O método **Mean Shift** é um algoritmo baseado em **janela deslizante** que tenta encontrar áreas densas no conjunto de dados.

---

A ideia desse algoritmo é criar uma **região circular**, obtida através da **média ponderada** dos elementos presentes dentro dessa área, considerando a **distância** de cada ponto em relação ao ponto atual.

---


A região de maior concentração em de objetos determina a **direção de deslocamento** deste círculo na base de dados.

---

Quando o círculo **não se movimentar** mais na base de dados a iteração termina e o algoritmo é encerrado.

---

<img src="gif02.gif" width="700">

---

### Compreendendo o algoritmo

<img src="fig01.png" width="700">

---

A ideia do algoritmo é calcular a **função densidade de probabilidade** para um conjunto de dados. Isso é feito através do conceito de **kernel density estimation (KDE)**

---

A **média ponderada** é calculada utilizando o kernel, que atribui pesos aos pontos de dados com base em sua proximidade ao ponto central.

---

<img src="fig02.png" width="700">

---

<img src="fig03.png" width="700">

---

A **largura de banda (bandwidth)** define o raio da **vizinhança** que é considerado para calcular a média ponderada.

---

<img src="gif01.gif" width="700">

---

Se o valor do bandwidth for **muito grande**, os pontos de dados de diferentes clusters podem ser misturados, levando a um agrupamento **menos discriminativo**.

---

Se o valor do bandwidth for **muito pequeno**, podem surgir **clusters pequenos e insignificantes** ou até mesmo apenas um **único cluster** que englobe todos os pontos.

---

A **escolha** adequada do valor do bandwidth é **crucial** para obter resultados significativos com o algoritmo Mean Shift. 

---

Geralmente, esse valor é **ajustado empiricamente** ou através de **métodos de validação cruzada** para encontrar o valor que melhor se adapte aos dados específicos em questão. 

---

Uma abordagem comum é **experimentar** diferentes valores e selecionar aquele que produzir os **clusters mais relevantes** e bem definidos para a tarefa em questão.

---

{{<slide background-color="#54787d">}}

## Métodos baseados em modelos

---

### Redes de Kohonen

**Redes de Kohonen**, também conhecidas como **Mapas Auto-Organizáveis (SOM - Self-Organizing Maps)**, são uma classe especial de algoritmos de aprendizado de máquina **não supervisionado**, desenvolvidas por Teuvo Kohonen em 1982.

---

Essas redes têm como objetivo **organizar** e **visualizar** dados complexos em um **espaço bidimensional** ou tridimensional, de forma que **padrões** e **estruturas ocultas** possam ser facilmente **identificados**.

---

O funcionamento das redes de Kohonen é inspirado na forma como o **cérebro humano** organiza informações e aprende a partir do **ambiente**.

---

### Cérebro respondendo a estímulos

<img src="cerebro2.gif" width="700">

---

A rede é composta por um **conjunto de neurônios** artificialmente conectados em uma estrutura **bidimensional**, que representa o mapa. Cada neurônio é associado a um **vetor de pesos**, que inicialmente é **aleatório**.

---

O treinamento das redes de Kohonen ocorre em **duas etapas:** Competição e Cooperação

&nbsp;

Princípio fundamental: **Aprendizagem competitiva**

---

### Competição

Durante essa fase, um dado de entrada é apresentado à rede, e cada neurônio calcula a sua **distância** em relação ao dado.

&nbsp;

O neurônio que possui os pesos mais próximos do dado de entrada é o **vencedor (BMU: Best Matching Unit)**, ou seja, o neurônio com menor distância euclidiana.

---

### Cooperação

O neurônio vencedor, juntamente com seus neurônios vizinhos próximos, **atualiza seus pesos** para ficarem mais **similares** ao dado de entrada.

&nbsp;

Essa **atualização** ajuda a agrupar os dados de entrada **similares** em **regiões próximas** do mapa.

---

Essas duas etapas de competição e cooperação são repetidas várias vezes durante o treinamento, e gradualmente, os neurônios se **organizam** em regiões distintas, formando agrupamentos e **revelando padrões** presentes nos dados.

---

<table>
<tr>
<th>Competição</th>
<th>Cooperação</th>
</tr>
<tr>
<td>
<img src="kohonen.jpeg" width="420">
</td>
<td>
<img src="SOM.gif" width="420">
</td>
</tr>
</table>

---

A **vizinhança** de cada neurônio pode ser definida de acordo com a **forma geométrica** utilizada para representar os neurônios da rede

---

<img src="topologia.png" width="700">

---

- **Hexagonal:** cada neurônio possui 6 vizinhos diretos

&nbsp;

- **Retangular:** cada neurônio possui 4 vizinhos diretos

---

### Atualização dos pesos

&nbsp;

Os pesos são **atualizados** segundo a **distância** ao neurônio **ganhador**

<img src="eq.jpg" width="700">

<img src="eq2.jpg" width="700">

---

### Considerações finais

&nbsp;

- É uma rede de **aprendizado não supervisionado**

- Os exemplos de entrada são comparados a **todos** os neurônios e o **mais próximo** é considerado o neurônio **vencedor (BMU)**

---

- Os pesos do nerônio vencedor são **atualizados** para **aproximar-se** mais do padrão de dados que representa

- É uma rede ideal para **detecção de agrupamentos**

---

- O **vetor de pesos** para um cluster serve como um **exemplar dos padrões** de entrada associados com esse cluster.

