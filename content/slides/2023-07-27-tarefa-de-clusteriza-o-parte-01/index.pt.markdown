---
title: Tarefa de clusterização - parte 01
author: Tiago Pereira
date: '2023-07-27'
slug: indexTC01
categories:
  - Clusterização
  - Agrupamento
  - DBSCAN
  - Densidade
tags:
  - Cluster
summary: 'Tarefa de clusterização, métodos baseados em densidade: DBSCAN'
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

## Clusterização

---

Uma das habilidades mais básicas dos organismos vivos é a capacidade de agrupar objetos similares para produzir uma **taxonomia**, uma **classificação**, ou um **agrupamento**.

---

**Humanos** se interessam por **categorizações**...

---

<table>
<tr>
<th>Música</th>
<th></th>
</tr>
<tr>
<td>
<img src="music.jpg" width="2000">
</td>
<td>
<ul>
  <li>Rock</li>
  <li>Erudita</li>
  <li>Popular</li>
  <li>Jazz</li>
  <li>etc...</li>
</ul>
</td>
</tr>
</table>

---

<table>
<tr>
<th>Filmes</th>
<th></th>
</tr>
<tr>
<td>
<img src="movies.jpg" width="2000">
</td>
<td>
<ul>
  <li>Animação</li>
  <li>Aventura</li>
  <li>Comédia</li>
  <li>Drama</li>
  <li>etc...</li>
</ul>
</td>
</tr>
</table>

---

Diversas **ciências** se baseiam na organização de objetos de acordo com suas similaridades

---

<table>
<tr>
<th>Biologia</th>
<th></th>
</tr>
<tr>
<td>
<img src="macaco_homem.jpg" width="420">
</td>
<td>
<dl>
  <dt>Reino: Animalia</dt>
  <dt>Ramo: Chordata</dt>
  <dt>Classe: Mammalia</dt>
  <dt>Ordem: Primatas</dt>
  <dt>Família: <em>Hominidae</em></dt>
  <dt>Gênero: <em>Homo</em></dt>
  <dt>Espécie: <em>Homo sapiens</em></dt>
</dl>
</td>
</tr>
</table>

---

Existem muitas situações nas quais não sabemos de **antemão** uma maneira **apropriada** de agrupar uma coleção de objetos de acordo com suas **similaridades**

---

Imagine que você tem uma cesta cheia de frutas diferentes. Como você poderia agrupá-las?

---

<table>
<tr>
<th>Como agrupá-las?</th>
<th></th>
</tr>
<tr>
<td>
<img src="cesta.jpg" width="420">
</td>
<td>
<ul>
  <li>Pela cor?</li>
  <li>Pelo tamanho?</li>
  <li>Pelo sabor?</li>
  <li>Ou algum outro critério?</li>
</ul>
</td>
</tr>
</table>

---

A **clusterização** é uma técnica de mineração de dados que nos permite descobrir **padrões** e estruturas ocultas em conjuntos de dados. Ela agrupa objetos **similares** e os **separa** dos demais, formando clusters.

---

Os grupos são formados de maneira a **maximizar** a similaridade entre os elementos de um grupo (**similaridade intra-grupo**) e **minimizar** a similaridade entre elementos de grupos diferentes (**similaridade inter-grupos**)

---

<img src="relacoes.png" width="700">

---

{{<slide background-color="#54787d">}} 

## Métodos de clusterização

---

Já conhecemos...

&nbsp;

- Métodos hierárquicos
- Métodos não-hierárquicos

---

{{<slide background-color="#54787d">}} 

## Métodos baseados em densidade

---

São técnicas utilizadas na mineração de dados para identificar agrupamentos ou padrões em conjuntos de dados com base na **densidade dos elementos amostrais**.

---

Esses métodos levam em consideração a **proximidade** entre os indivíduos, agrupando aqueles que estão próximos uns dos outros em **regiões densas**.

---

Uma **região densa** é uma região onde cada ponto tem **muitos pontos** em sua **vizinhança**.

---

<img src="dens.jpg" width="700">

---

{{<slide background-color="#54787d">}} 

## Método DBSCAN

---

O método **DBSCAN** (Density-Based Spatial Clustering of Applications with Noise) é um dos algoritmos baseados em **densidade** mais conhecidos.

---

Vamos definir **densidade** como sendo o número de pontos dentro de um **raio específico** (Eps)

---

Um ponto é um **ponto de núcleo** (core point) se ele tem mais que um número especificado de pontos (MinPts) dentro de Eps

&nbsp;

Estes são os pontos que estão no **interior** de um grupo

---

Um **ponto de fronteira** (border point) tem menos que MinPts dentro de Eps mas está na vizinhança de um ponto núcleo

---

Um **ponto de ruído** (noise point) é um ponto que não é nem um ponto núcleo nem um ponto de fronteira.

---

<img src="points2.png" width="700">

---

Para encontrar os agrupamentos, o algoritmo DBSCAN faz uma **varredura** nas observações determinando **todos os pontos núcleo**. 

---

Faz-se a seguir uma varredura dos pontos núcleo fazendo as conexões a todos os pontos que estejam a uma distância menor do que (Eps).

---

Cada subconjunto de pontos conectados entre si (conectividade), forma um cluster.

---

<img src="DBSCAN_tutorial.gif" width="700">

---

### Vantagens do DBSCAN

&nbsp;

- Eficiente em tratar grandes bases de dados
- Menos sensível a ruídos
- Forma clusters de formato arbitrário
- Usuário não precisa determinar a quantidade de clusters

---

### Desvantagem do DBSCAN

&nbsp;

Sensível aos parâmetros de entrada (Eps e MinPts)

<img src="tab_par_dbscan.png" width="1000">

---

### Determinação dos valores de Eps e MinPts

&nbsp;

- Verificar a distância ao _k_-ésimo vizinho mais próximo: _k_-dist

- Para objetos que estão dentro de um cluster: se _k_ for menor ou igual ao tamanho do cluster então _k_-dist é **pequeno**.

---

- Para objetos que não estão dentro de um cluster: _k_-dist é **grande**
- Seleciona-se os _k_-dist para cada objeto, para um determinado valor de _k_.
- Ordena-se os objetos pelos valores de _k_-dist

---

- No ponto onde houver uma grande variação do número _k_-dist, significa que foi atingido um valor adequado para Eps.
- Valor de Eps depende do número _k_ escolhido.
- Na prática, o valor _k_ = 4 é utilizado para a maioria dos banco de dados, com bons resultados

---

<img src="minpts_eps.jpg" width="1000">

---

### Problema: Clusters com densidades diferentes

<img src="problema_dbscan.jpg" width="1000">

---

Se Eps é **alto suficiente** para que C e D sejam detectados como clusters então A e B e a região a sua volta se tornarão um **único cluster**

---

Se Eps é **baixo suficiente** para que A e B sejam detectados como clusters separados então C e D (e os objetos a seu redor) serão considerados **outliers**!
