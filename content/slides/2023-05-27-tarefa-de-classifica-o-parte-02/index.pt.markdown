---
title: Tarefa de classificação - parte 02
author: Tiago Pereira
date: '2023-05-27'
slug: tarefa-de-classifica-o-parte-02
categories:
  - Classificação
tags:
  - Classificação
summary: 'Árvores de decisão: principais algoritmos, critérios de divisão'
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

## Árvores de decisão

---

Uma **árvore de decisão** é um modelo de aprendizado de máquina que utiliza uma estrutura de árvore para tomar decisões com base em condições nos dados de entrada. 

---

Essa estrutura hierárquica consiste em nós que representam **testes** sobre atributos e arestas que conectam os nós, indicando os resultados desses testes.

---

Cada **nó interno** da árvore representa um teste em um atributo específico, enquanto as **folhas** representam as classes ou valores de saída. 

---

Ao percorrer a árvore da raiz até uma folha, os dados de entrada são avaliados de acordo com os testes em cada nó, seguindo o caminho apropriado até alcançar uma folha, onde é tomada a decisão final.

---

![decisionTree](decisionTree.jpeg)

---

{{<slide background-color="#54787d">}} 

## Principais Algoritmos

---

**ID3 (Iterative Dichotomiser 3)** 

&nbsp;
&nbsp;

É um dos primeiros algoritmos de árvore de decisão e utiliza o **ganho de informação** como critério para selecionar a melhor divisão em cada nó. No entanto, o ID3 não lida diretamente com **atributos numéricos**.

---

**C4.5**

&nbsp;
&nbsp;

É uma extensão do ID3 e possui melhorias, incluindo a capacidade de lidar com **atributos numéricos** e **valores ausentes**. Além disso, o C4.5 utiliza a **razão de ganho** como métrica de seleção de atributos, em vez do ganho de informação utilizado pelo ID3.

---

**CART (Classification and Regression Trees)**

&nbsp;
&nbsp;

É um algoritmo que pode ser usado tanto para problemas de **classificação** quanto de **regressão**. O CART constrói árvores binárias e utiliza o **índice de Gini** como critério de divisão. Ele busca minimizar a **impureza** nos nós da árvore.

---

![processo](processo.jpg)

---

{{<slide background-color="#54787d">}} 

## Critérios de divisão

---

### Entropia

A **entropia** é uma **medida de impureza** ou desordem nos dados em um algoritmo de árvore de decisão. Ela é utilizada para avaliar o quão homogêneos ou heterogêneos são os exemplos de uma determinada classe em um conjunto de dados.

---

É calculada a partir da distribuição das classes no conjunto de dados. Quanto **maior** a entropia, **maior a incerteza** sobre a classe de um exemplo. Quanto **menor** a entropia, mais **homogêneos** são os exemplos em relação à classe.

---

### Cálculo da entropia (E)

{{< math >}} 
$$ \text{E(S)} = \sum_{i=1}^c -p_i\log_2 p_i$$
{{< /math >}}

em que {{< math >}} `\(p_i\)`{{< /math >}} é a proporção de exemplos na classe {{< math >}} `\(i\)`{{< /math >}} da amostra de treinamento S.

&nbsp;
&nbsp;

A **entropia** mede a **"impureza"** de S!

---

No contexto das árvores de decisão a **entropia** é usada para estimar a **aleatoriedade** da variável a prever a classe.

---

### Ganho de Informação (G)

O **ganho de informação** é uma métrica utilizada para medir a relevância de um atributo na divisão dos dados. Ele indica a **quantidade de informação** que um atributo fornece sobre a **classe** ou **variável** de saída.

---

### Cálculo do ganho de informação

{{< math >}} 

$$ \text{G}(S, A) = \text{E}(S) - \text{E}(S,A)$$

{{< /math >}}

em que {{< math >}} `$$E(S,A) = \sum_{v\in \text{valores de } A} \dfrac{|S_v|}{|S|} \times \text{E}(S_v)$$`{{< /math >}} é a entropia do atributo A.


---

### Razão de ganho

Também conhecida como **gain ratio**, é uma métrica utilizada para selecionar os melhores atributos de divisão, levando em consideração o viés por atributos com muitos valores possíveis.

---

Enquanto o **ganho de informação** mede a redução da entropia dos dados após a divisão com base em um atributo, a **razão de ganho** ajusta esse valor, levando em consideração o número de valores distintos do atributo. 

Essa correção é importante para evitar que atributos com **muitos valores** possíveis tenham vantagem sobre atributos com **menos valores**.

---

### Cálculo da razão de ganho

{{< math >}} 

$$ \text{Gain ratio}(S, A) = \dfrac{G(S, A)}{E(S, A)}$$

{{< /math >}}

---

### Índice de Gini

O índice de Gini é outra medida de **impureza** utilizada para avaliar a heterogeneidade dos dados em relação à classe ou variável de saída. 

Mede a probabilidade de dois exemplos escolhidos aleatoriamente pertencerem a diferentes classes.

---

### Cálculo do índice de Gini

{{< math >}} 

$$ \text{Gini}(S) = 1 - \sum_{i=1}^c p_i^2$$

{{< /math >}}

em que {{< math >}} `\(p_i\)`{{< /math >}} é a proporção de exemplos na classe {{< math >}} `\(i\)`{{< /math >}} da amostra de treinamento S.

---

O índice de Gini varia de 0 a 1, sendo 0 quando todos os exemplos pertencem à mesma classe (alta pureza) e 1 quando os exemplos estão igualmente distribuídos entre as classes (alta impureza).

---

{{<slide background-color="#54787d">}} 

## Exemplo

---

### Compra de um computador

![exemplo](tabela.jpg)

---

#### Cálculo da entropia

&nbsp;
&nbsp;

{{< math >}} 
$$ \text{E(S)} = -\dfrac{9}{14}\log_2 (\dfrac{9}{14}) - \dfrac{5}{14}\log_2 (\dfrac{5}{14}) = 0,940$$
{{< /math >}}

---

#### Ganho de informação para o atributo idade

&nbsp;

{{< math >}} 
$$ \text{E(S, Idade)} = \dfrac{|\leq 30|}{|S|}\times \text{E}(\leq 30)\\
+ \dfrac{|31...40|}{|S|}\times \text{E}(31...40) \\ +  \dfrac{|>40|}{|S|}\times \text{E}(>40)$$`
{{< /math >}}

---

<style type="text/css">
.tg  {border-collapse:collapse;border-color:#93a1a1;border-spacing:0;}
.tg td{background-color:#fdf6e3;border-color:#93a1a1;border-style:solid;border-width:0px;color:#002b36;
  font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:10px 5px;word-break:normal;}
.tg th{background-color:#657b83;border-color:#93a1a1;border-style:solid;border-width:0px;color:#fdf6e3;
  font-family:Arial, sans-serif;font-size:14px;font-weight:normal;overflow:hidden;padding:10px 5px;word-break:normal;}
.tg .tg-oao4{background-color:#fdf6e3;border-color:#002b36;text-align:center;vertical-align:top}
.tg .tg-c3ow{border-color:inherit;text-align:center;vertical-align:top}
.tg .tg-cw6g{background-color:#657b83;border-color:inherit;text-align:center;vertical-align:top}
.tg .tg-itrc{background-color:#657b83;border-color:inherit;color:#fdf6e3;text-align:center;vertical-align:middle}
</style>
<table class="tg">
<thead>
  <tr>
    <th class="tg-cw6g"></th>
    <th class="tg-cw6g"></th>
    <th class="tg-c3ow" colspan="2">Classe</th>
    <th class="tg-c3ow"></th>
  </tr>
</thead>
<tbody>
  <tr>
    <td class="tg-cw6g"></td>
    <td class="tg-oao4"></td>
    <td class="tg-c3ow">Sim</td>
    <td class="tg-c3ow">Não</td>
    <td class="tg-c3ow"></td>
  </tr>
  <tr>
    <td class="tg-itrc" rowspan="3">Idade<br></td>
    <td class="tg-oao4">=&lt; 30</td>
    <td class="tg-c3ow">2</td>
    <td class="tg-c3ow">3</td>
    <td class="tg-c3ow">5</td>
  </tr>
  <tr>
    <td class="tg-oao4">31...40</td>
    <td class="tg-c3ow">4</td>
    <td class="tg-c3ow">0</td>
    <td class="tg-c3ow">4</td>
  </tr>
  <tr>
    <td class="tg-oao4">&gt;40</td>
    <td class="tg-c3ow">3</td>
    <td class="tg-c3ow">2</td>
    <td class="tg-c3ow">5</td>
  </tr>
  <tr>
    <td class="tg-cw6g"></td>
    <td class="tg-oao4"></td>
    <td class="tg-c3ow"></td>
    <td class="tg-c3ow"></td>
    <td class="tg-c3ow">14</td>
  </tr>
</tbody>
</table>

&nbsp;

{{< math >}} 
$$ \text{E(S, Idade)} = \dfrac{5}{|14|}\times \text{E}(\leq 30)+ \dfrac{4}{|14|}\times \text{E}(31...40) \\ +  \dfrac{5}{14}\times \text{E}(>40)$$
{{< /math >}}

---

<style type="text/css">
.tg  {border-collapse:collapse;border-color:#93a1a1;border-spacing:0;}
.tg td{background-color:#fdf6e3;border-color:#93a1a1;border-style:solid;border-width:0px;color:#002b36;
  font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:10px 5px;word-break:normal;}
.tg th{background-color:#657b83;border-color:#93a1a1;border-style:solid;border-width:0px;color:#fdf6e3;
  font-family:Arial, sans-serif;font-size:14px;font-weight:normal;overflow:hidden;padding:10px 5px;word-break:normal;}
.tg .tg-oao4{background-color:#fdf6e3;border-color:#002b36;text-align:center;vertical-align:top}
.tg .tg-c3ow{border-color:inherit;text-align:center;vertical-align:top}
.tg .tg-cw6g{background-color:#657b83;border-color:inherit;text-align:center;vertical-align:top}
.tg .tg-itrc{background-color:#657b83;border-color:inherit;color:#fdf6e3;text-align:center;vertical-align:middle}
</style>
<table class="tg">
<thead>
  <tr>
    <th class="tg-cw6g"></th>
    <th class="tg-cw6g"></th>
    <th class="tg-c3ow" colspan="2">Classe</th>
    <th class="tg-c3ow"></th>
  </tr>
</thead>
<tbody>
  <tr>
    <td class="tg-cw6g"></td>
    <td class="tg-oao4"></td>
    <td class="tg-c3ow">Sim</td>
    <td class="tg-c3ow">Não</td>
    <td class="tg-c3ow"></td>
  </tr>
  <tr>
    <td class="tg-itrc" rowspan="3">Idade<br></td>
    <td class="tg-oao4">=&lt; 30</td>
    <td class="tg-c3ow">2</td>
    <td class="tg-c3ow">3</td>
    <td class="tg-c3ow">5</td>
  </tr>
  <tr>
    <td class="tg-oao4">31...40</td>
    <td class="tg-c3ow">4</td>
    <td class="tg-c3ow">0</td>
    <td class="tg-c3ow">4</td>
  </tr>
  <tr>
    <td class="tg-oao4">&gt;40</td>
    <td class="tg-c3ow">3</td>
    <td class="tg-c3ow">2</td>
    <td class="tg-c3ow">5</td>
  </tr>
  <tr>
    <td class="tg-cw6g"></td>
    <td class="tg-oao4"></td>
    <td class="tg-c3ow"></td>
    <td class="tg-c3ow"></td>
    <td class="tg-c3ow">14</td>
  </tr>
</tbody>
</table>

&nbsp;

{{< math >}} 
$$ \text{E}(\leq 30) = -\dfrac{2}{5}\log_2 (\dfrac{2}{5}) - \dfrac{3}{5}\log_2 (\dfrac{3}{5}) = 0,971$$
{{< /math >}}

&nbsp;

{{< math >}} 
$$ \text{E}(31...40) = 0\,\,\,\,\,\,\,\, \text{e} \,\,\,\,\,\,\,\, \text{E}(>40) = 0,971$$
{{< /math >}}

---

{{< math >}} 
$$ \text{E(S, Idade)} = \dfrac{5}{|14|}\times 0,971 + \dfrac{4}{|14|}\times 0 \\ +  \dfrac{5}{14}\times 0,971 = 0,693$$
{{< /math >}}

&nbsp;


{{< math >}} 

$$ \text{G}(S, \text{Idade}) = \text{E}(S) - \text{E}(S,\text{Idade})\\ = 0,940 - 0,693 = 0,247$$

{{< /math >}}

---

![ganhos](ganhos.jpg)

---

Escolhemos o atributo com maior ganho de informação como nó de decisão. No nosso caso, o atributo **Idade**. A partir daí, dividimos o conjunto de dados a partir das categorias da variável idade e repetimos o mesmo processo em todos os ramos. 

Um ramo com entropia de 0 é um **nó folha**. Um ramo com entropia maior que 0 precisa de mais divisão.

---

### Árvore estimada


[![](https://mermaid.ink/img/pako:eNptkMFuwjAMhl8l8qlIpUJip2pDWmkZHLYLO7HsYDXuqNQkKCTaJsLT7FH2YriFSUzCF1v-v9-yfYDaKoIcms5-1lt0XryW0giOx7eVQkXvYjyexfuH6SSKIqn2Pig0nkY3oOkky7I75ubJutW3iFmvlsnckWq9vRBFL4n48vtjo6iSPv9XeFgUi6uZ5blffdXUES8TxdO17SIXlm3LwQYpaHIaW8WnHnpKgt-SJgk5l4oaDJ2XIM2RUQzerr9NDbl3gVIIO4WeyhY_HGrIG-z23B1OcM_n9w1fTGGHZmPtH3M8AeDBbHA?type=png)](https://mermaid.live/edit#pako:eNptkMFuwjAMhl8l8qlIpUJip2pDWmkZHLYLO7HsYDXuqNQkKCTaJsLT7FH2YriFSUzCF1v-v9-yfYDaKoIcms5-1lt0XryW0giOx7eVQkXvYjyexfuH6SSKIqn2Pig0nkY3oOkky7I75ubJutW3iFmvlsnckWq9vRBFL4n48vtjo6iSPv9XeFgUi6uZ5blffdXUES8TxdO17SIXlm3LwQYpaHIaW8WnHnpKgt-SJgk5l4oaDJ2XIM2RUQzerr9NDbl3gVIIO4WeyhY_HGrIG-z23B1OcM_n9w1fTGGHZmPtH3M8AeDBbHA)

---

João possui as seguintes características

- menos de 30 anos
- renda média
- é estudante
- possuí um bom crédito na praça!

---

### De volta ao Joãozinho...

[![](https://mermaid.ink/img/pako:eNptkcFOwzAMhl8lyi5FyqqJIiQCTFrXDjjAZZwgHKLGWSPSpEpTbWjd0_AovBjpWqQhzRdb_r_fiew9LqwATLHUdluU3Hn0mjGDQizenwQX8IGm03l3d5_MOpRGeeNbwY2HizNQMovj-Cpwy2itqnPEvFezaOlAKG9HIu0l1L38fNsO5VGf_ythWIdWJzOzoZ_vCtAQPtOhh1PbKKc22B5HGzOF5k2TgUQbB2CQVFrTyY28Jo139hPoJEmSsZ5ulfAlvax3t6MPpWRBVoMVE1yBq7gSYW_7_kmGfQkVMExDKUDyVnuGmTkElLferr9Mgal3LRDc1oJ7yBTfOF5hKrluQve4D_c83OJ4EoJrbt6s_WMOv9VMhv8?type=png)](https://mermaid.live/edit#pako:eNptkcFOwzAMhl8lyi5FyqqJIiQCTFrXDjjAZZwgHKLGWSPSpEpTbWjd0_AovBjpWqQhzRdb_r_fiew9LqwATLHUdluU3Hn0mjGDQizenwQX8IGm03l3d5_MOpRGeeNbwY2HizNQMovj-Cpwy2itqnPEvFezaOlAKG9HIu0l1L38fNsO5VGf_ythWIdWJzOzoZ_vCtAQPtOhh1PbKKc22B5HGzOF5k2TgUQbB2CQVFrTyY28Jo139hPoJEmSsZ5ulfAlvax3t6MPpWRBVoMVE1yBq7gSYW_7_kmGfQkVMExDKUDyVnuGmTkElLferr9Mgal3LRDc1oJ7yBTfOF5hKrluQve4D_c83OJ4EoJrbt6s_WMOv9VMhv8)

{{< spoiler text= "João comprará o computador?" >}}
<p style="color: green"> De acordo com árvores de decisão: SIM! </p>
{{< /spoiler >}}
