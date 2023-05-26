---
title: Tarefa de classificação - parte 01
author: Tiago Pereira
date: '2023-05-01'
slug: tarefa-de-classifica-o-parte-01
categories:
  - Classificação
tags:
  - Classificação
summary: 'Tarefa de classificação, KNN e Naive Bayes'
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

## Tarefa de Classificação

---

### O que são problemas de classificação?

Os problemas de **classificação** são aqueles que envolvem a classificação de objetos ou instâncias em uma ou mais categorias pré-definidas.

---

- Em problemas de classificação, o objetivo é **"aprender"** um modelo que possa **mapear** as características de um objeto para uma categoria correspondente.


- O modelo é treinado com **dados rotulados**, ou seja, dados onde a categoria ou classe de cada objeto é **conhecida**.

---

- O modelo é então usado para classificar **novos objetos** com base em suas características.

- Exemplos de problemas de classificação incluem:

  - Classificar e-mails como **spam** ou **não spam**.
  - Classificar transações de cartão de crédito como **fraudulentas** ou **legítimas**.
  - Classificar imagens de objetos como **carros**, **animais**, **plantas**, etc.
  
---

#### Problema de classificação

![class](class.png)

---

- Podem ser divididos em **classificação binária** e **classificação multiclasse**

- Em problemas de classificação binária, existem apenas **duas classes** possíveis (por exemplo, sim ou não).

- Para os multiclasse, existem **três** ou **mais classes** possíveis (por exemplo, vermelho, azul ou verde).

---

{{<slide background-color="#54787d">}} 

## Algoritmos de classificação

---

- Algoritmos mais comuns usados para problemas de classificação:

  - K-Nearest Neighbors (KNN)
  - Naive Bayes
  - Árvores de decisão
  - Random Forests
  - Máquinas de Vetores de Suporte (SVM)
  - Redes Neurais Artificiais (ANN)

---

{{<slide background-color="#54787d">}} 

## K-Nearest Neighbors (KNN)

---

O KNN é um algoritmo de aprendizado supervisionado de classificação e regressão, que usa a proximidade dos objetos para classificar novas instâncias.

---

É um dos algoritmos mais simples e intuitivos de aprendizado de máquina. Utiliza a ideia do "vizinho mais próximo", o que significa que ele determina a classe de uma instância com base nas classes de seus vizinhos mais próximos.

---

Em outras palavras, se a maioria dos vizinhos mais próximos de uma instância pertence a uma classe específica, então a instância também é classificada como pertencente a essa classe.

--- 

### Algoritmo KNN

![knn](knn.jpg)

---

O valor de K é um **parâmetro** importante em KNN. Ele determina o número de vizinhos mais próximos que são usados para classificar uma nova instância.

---

Um valor de K pequeno pode levar a um modelo muito **sensível** ao **ruído** nos dados, enquanto um valor grande de K pode levar a uma **perda** de detalhes importantes nos dados.

---

A escolha do valor K ideal é frequentemente realizada por meio de técnicas de **validação cruzada**.

---

- KNN é usado para problemas de classificação e regressão.

  - Em problemas de **classificação**, a classe mais comum entre os K vizinhos mais próximos é escolhida como a classe da nova instância.

  - Em problemas de **regressão**, a média ou mediana dos valores alvo dos K vizinhos mais próximos é escolhida como o valor alvo da nova instância.

---

É **computacionalmente caro** para grandes conjuntos de dados, pois ele precisa calcular a distância entre a nova instância e todos os pontos de dados no conjunto de treinamento.

---

Além disso, o KNN é **sensível à escala** dos dados, portanto, a **normalização dos dados** é importante antes de aplicar o algoritmo.


Finalmente, o KNN pode ser usado como um modelo de referência para problemas de classificação e regressão antes de explorar modelos mais complexos.

---

{{<slide background-color="#54787d">}} 

## Exemplo

---

### Compra de um computador

![exemplo](tabela.jpg)

---
João possui as seguintes características

- menos de 30 anos
- renda média
- é estudante
- possuí um bom crédito na praça!

---

João **compraria** ou **não compraria** o computador?

![duvida](https://media2.giphy.com/media/XeH1MFu4x3etVsllUN/giphy.gif)  


---

<p style="font-size: 56px">Quem é o João?</p>

&nbsp;
&nbsp;

{{% fragment %}}
<p style="color: blue">{{< math >}}$x_0 = \{\leq 30, \text{ Média}, \text{ Sim}, \text{ Bom}\}${{< /math >}}</p>
{{% /fragment %}}

---

Usando o classificador KNN com k = 5

![tab_dis](tab_dist.jpg)


---

Temos então que os **5 vizinhos** mais próximos a João são


- <p style="color: red">{{< math >}} $ x_2 = \{\leq 30, \text{ Alta}, \text{ Sim}, \text{ Bom}\}${{< /math >}}</p>
- <p style="color: red">{{< math >}} $ x_8 = \{\leq 30, \text{Média}, \text{ Não}, \text{ Bom}\}${{< /math >}}</p>


---

- <p style="color: green">{{< math >}} $ x_9 = \{\leq 30, \text{ Baixa}, \text{ Sim}, \text{ Bom}\}${{< /math >}}</p>
- <p style="color: green">{{< math >}} $ x_{10} = \{> 40, \text{ Média}, \text{ Sim}, \text{ Excelente}\}${{< /math >}}</p>
- <p style="color: green">{{< math >}} $ x_{11} = \{\leq 30, \text{ Média}, \text{ Sim}, \text{ Excelente}\}${{< /math >}}</p>

---

{{< spoiler text= "João comprará o computador?" >}}
&nbsp;
<p style="color: green"> De acordo com o KNN: SIM! </p>
{{< /spoiler >}}

---

{{<slide background-color="#54787d">}} 

## Classificador Naïve Bayes

---

Baseia-se no **Teorema de Bayes**, que afirma que a probabilidade de um evento ocorrer dado que outro evento já ocorreu é proporcional à probabilidade deste último evento ocorrer dado o primeiro.

---

- Este método estima a probabilidade de cada classe (categoria) dada as **características** dos dados.

- Ele assume que as características são **independentes entre si**, ou seja, não há interdependência entre elas.

- Com base nessa **probabilidade**, ele classifica novos dados em uma das categorias pré-definidas.


---

### Vantagens

- O Classificador Naïve Bayes é um algoritmo simples e rápido.

- Ele funciona bem em conjuntos de dados com muitas características e com pouco dados.

- É um algoritmo eficiente em tarefas de classificação de texto.

---

### Desvantagens

- O Classificador Naïve Bayes assume que as características são independentes entre si, o que nem sempre é verdade.

- Ele pode ser afetado por dados faltantes ou incorretos.

- Não é um bom algoritmo para tarefas que envolvem classes dependentes.

---

{{<slide background-color="#54787d">}} 

## Exemplo

---

### Compra de um computador

![exemplo](tabela.jpg)

---

Voltando ao Joãozinho...

&nbsp;
&nbsp;

{{% fragment %}}
<p style="color: blue">{{< math >}}$x_0 = \{\leq 30, \text{ Média}, \text{ Sim}, \text{ Bom}\}${{< /math >}}</p>
{{% /fragment %}}

---

{{< math >}} 
$$ P(\text{classe = Sim}) = \dfrac{9}{14} \,\,\,\,\,\,\, \text{e}\,\,\,\,\,\,\, P(\text{classe = Não}) = \dfrac{5}{14}$$
{{< /math >}}

---

Para o atributo **Idade**

{{< math >}} 
$$ P(\text{Idade} \leq 30 | \text{classe = Sim}) = \dfrac{2}{9} \\ P(\text{Idade} \leq 30 | \text{classe = Não}) = \dfrac{3}{5}$$
{{< /math >}}

---


Para o atributo **Renda**

{{< math >}} 
$$ P(\text{Renda = Média} | \text{classe = Sim}) = \dfrac{4}{9} \\ P(\text{Renda = Média} | \text{classe = Não}) = \dfrac{2}{5}$$
{{< /math >}}

---


Para o atributo **Estudante**

{{< math >}} 
$$ P(\text{Estudante = Sim} | \text{classe = Sim}) = \dfrac{6}{9} \\ P(\text{Estudante = Sim} | \text{classe = Não}) = \dfrac{1}{5}$$
{{< /math >}}

---


Para o atributo **Crédito**

{{< math >}} 
$$ P(\text{Crédito = Bom} | \text{classe = Sim}) = \dfrac{6}{9} \\ P(\text{Crédito = Bom} | \text{classe = Não}) = \dfrac{2}{5}$$

{{< /math >}}

---

Temos então, sob independência...

{{< math >}} 
`$$P(x_0|\text{Sim}) = P(\leq 30 \cap \text{Média} \cap \text{Sim} \cap \text{Bom}|\text{Sim} ) \\ = \dfrac{2}{9} \times \dfrac{4}{9}\times \dfrac{6}{9}\times \dfrac{6}{9} = \dfrac{32}{729} = 0,044$$`
{{< /math >}}

---

Temos então, sob independência...

{{< math >}} 
`$$P(x_0|\text{Não}) = P(\leq 30 \cap \text{Média} \cap \text{Sim} \cap \text{Bom}|\text{Não} ) \\ = \dfrac{3}{5} \times \dfrac{2}{5}\times \dfrac{1}{5}\times \dfrac{2}{5} = \dfrac{12}{625} = 0,019$$`
{{< /math >}}

---

Pelo Teorema da Probabilidade Total:

{{< math >}} 
`$$P(x_0) = P(x_0|\text{classe = Sim}) \times P(\text{classe = Sim}) + \\ P(x_0|\text{classe = Não}) \times P(\text{classe = Não}) \\ 0,044 \times 0,643 + 0,019 \times 0,357 = 0,035$$`
{{< /math >}}

---

Assim, pelo Teorema de Bayes:

{{< math >}} 
$$P(\text{Sim}|x_0) = \dfrac{P(x_0|\text{classe = Sim}) \times P(\text{classe = Sim})}{P(x_0)} \\ = \dfrac{0,044) \times 0,643}{0,035} = 0,80 \\ $$
{{< /math >}}

---

Assim, pelo Teorema de Bayes:

{{< math >}} 
$$P(\text{Não}|x_0) = \dfrac{P(x_0|\text{classe = Não}) \times P(\text{classe = Não})}{P(x_0)} \\ = \dfrac{0,019) \times 0,357}{0,035} = 0,20 \\ $$
{{< /math >}}


---

{{< spoiler text= "João comprará o computador?" >}}
&nbsp;
<p style="color: green"> De acordo com o Naïve Bayes: SIM! </p>
{{< /spoiler >}}
