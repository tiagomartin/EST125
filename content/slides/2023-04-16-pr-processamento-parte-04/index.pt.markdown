---
title: Pré-processamento - parte 04
author: Tiago Pereira
date: '2023-04-16'
slug: pr-processamento-parte-04
categories:
  - Pré-processamento
tags:
  - Pre
summary: 'Transformação de dados, discretização, binarização, one-hot encoding'
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
  
## Transformação de dados
  
---
  
- As bases de dados brutas e integradas a partir de bases distintas podem sofrer, além de valores ausentes, ruídos e inconsistências, de dados não ou pouco padronizados.

  - Por exemplo, pode haver valores de um mesmo atributo escritos em maiúsculo e outros em minúsculo, e os formatos e as unidades podem ser diferentes.

---
  
- Outro tipo de problema encontrado é a não uniformidade dos atributos, ou seja, alguns atributos podem ser numéricos, outros categóricos, e os domínios de cada atributo podem ser muito diferentes.

- Como podemos resolver esses problemas?
  
---



<a href="http://gph.is/1Vp16TL" target="_blank" rel="noopener noreferrer"><img src="https://media3.giphy.com/media/P4TqKx6NHyLnO/giphy.gif"  width="800" height="500"></a>

---
  
- **Padronização:** Resolver as diferenças de unidades e escalas dos dados.

  - **Capitalização:** é usual padronizar as fontes,	normalmente para maiúsculo.
  - **Padronização de formatos:** observar e padronizar o formato de cada atributo da base, principalmente quando diferentes bases precisam ser integradas.

---
  
  - **Conversão de unidades:** todos os dados devem ser convertidos e padronizados em uma mesma unidade de medida.

  - **Normalização:** tornar os dados mais apropriados à aplicação de algum algoritmo de mineração.

---
  
#### Tipos de normalização
  
  - **Normalização Max-Min:** Realiza uma transformação linear nos dados originais


`$$X' = \dfrac{X - \min(X)}{\max(X) - \min(X)}$$`


---

  - **Normalização pelo escore-z:** Útil quando os valores máximo e mínimo de um atributo forem desconhecidos ou quando existe outliers.
      
`$$X' = \dfrac{X - \bar{X}}{s_X}$$` 
  
---
  
  - **Normalização pelo escalonamento decimal:** Move a casa decimal de um atributo `\(X\)`.

`$$X' = \dfrac{X}{10^j}$$`
			
  em que `\(j\)` é o menor inteiro tal que `\(\max(|X'|)< 1\)`.

---
  
  - **Normalização pela distância interquartilica:** Toma o valor do atributo, subtrai a mediana e divide pela distância interquartílica ($DIQ = Q_3 - Q_1$)	

`$$X' =  \dfrac{X - Q_2}{DIQ}$$`

---

#### Exemplo de uso das diferentes normalizações

<style type="text/css">
.tg  {border-collapse:collapse;border-spacing:0;}
.tg td{border-color:black;border-style:solid;border-width:1px;font-family:Arial, sans-serif;font-size:14px;
  overflow:hidden;padding:10px 5px;word-break:normal;}
.tg th{border-color:black;border-style:solid;border-width:1px;font-family:Arial, sans-serif;font-size:14px;
  font-weight:normal;overflow:hidden;padding:10px 5px;word-break:normal;}
.tg .tg-34fe{background-color:#c0c0c0;border-color:inherit;text-align:center;vertical-align:top}
.tg .tg-c3ow{border-color:inherit;text-align:center;vertical-align:top}
</style>
<table class="tg">
<thead>
  <tr>
    <th class="tg-34fe">ID</th>
    <th class="tg-34fe">Valor original</th>
    <th class="tg-34fe">Max-Min</th>
    <th class="tg-34fe">Escore-z</th>
    <th class="tg-34fe">Escalonamento decimal</th>
    <th class="tg-34fe">Distância interquartílica</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td class="tg-c3ow">1</td>
    <td class="tg-c3ow">67</td>
    <td class="tg-c3ow">0,85</td>
    <td class="tg-c3ow">0,73</td>
    <td class="tg-c3ow">0,67</td>
    <td class="tg-c3ow">0,40</td>
  </tr>
  <tr>
    <td class="tg-c3ow">2</td>
    <td class="tg-c3ow">43</td>
    <td class="tg-c3ow">0,33</td>
    <td class="tg-c3ow">-0,92</td>
    <td class="tg-c3ow">0,43</td>
    <td class="tg-c3ow">-0,80</td>
  </tr>
  <tr>
    <td class="tg-c3ow">3</td>
    <td class="tg-c3ow">58</td>
    <td class="tg-c3ow">0,65</td>
    <td class="tg-c3ow">0,11</td>
    <td class="tg-c3ow">0,58</td>
    <td class="tg-c3ow">-0,05</td>
  </tr>
  <tr>
    <td class="tg-c3ow">4</td>
    <td class="tg-c3ow">28</td>
    <td class="tg-c3ow">0,00</td>
    <td class="tg-c3ow">-1,96</td>
    <td class="tg-c3ow">0,28</td>
    <td class="tg-c3ow">-1,55</td>
  </tr>
  <tr>
    <td class="tg-c3ow">5</td>
    <td class="tg-c3ow">74</td>
    <td class="tg-c3ow">1,00</td>
    <td class="tg-c3ow">1,21</td>
    <td class="tg-c3ow">0,74</td>
    <td class="tg-c3ow">0,75</td>
  </tr>
  <tr>
    <td class="tg-c3ow">6</td>
    <td class="tg-c3ow">65</td>
    <td class="tg-c3ow">0,80</td>
    <td class="tg-c3ow">0,59</td>
    <td class="tg-c3ow">0,65</td>
    <td class="tg-c3ow">0,30</td>
  </tr>
  <tr>
    <td class="tg-c3ow">7</td>
    <td class="tg-c3ow">70</td>
    <td class="tg-c3ow">0,91</td>
    <td class="tg-c3ow">0,94</td>
    <td class="tg-c3ow">0,70</td>
    <td class="tg-c3ow">0,55</td>
  </tr>
  <tr>
    <td class="tg-c3ow">8</td>
    <td class="tg-c3ow">42</td>
    <td class="tg-c3ow">0,30</td>
    <td class="tg-c3ow">-0,99</td>
    <td class="tg-c3ow">0,42</td>
    <td class="tg-c3ow">-0,85</td>
  </tr>
  <tr>
    <td class="tg-c3ow">9</td>
    <td class="tg-c3ow">57</td>
    <td class="tg-c3ow">0,63</td>
    <td class="tg-c3ow">0,04</td>
    <td class="tg-c3ow">0,57</td>
    <td class="tg-c3ow">-0,10</td>
  </tr>
  <tr>
    <td class="tg-c3ow">10</td>
    <td class="tg-c3ow">60</td>
    <td class="tg-c3ow">0,70</td>
    <td class="tg-c3ow">0,25</td>
    <td class="tg-c3ow">0,60</td>
    <td class="tg-c3ow">0,05</td>
  </tr>
</tbody>
</table>

---

  - **Transformação logarítmica:** Usada para reduzir a assimetria e a variância dos dados. É especialmente útil quando os dados estão distribuídos de forma exponencial ou quando há um grande intervalo de valores entre as observações.

---

  - **Transformação de raiz quadrada:** Similar à transformação logarítmica, com o benefício de manter a escala original dos dados, facilitando a interpretação.

---

- A transformação logarítmica é mais adequada para dados com caudas longas e uma grande variação, enquanto a transformação da raiz quadrada é mais adequada para dados com uma variação moderada. Além disso, a o uso de logarítmos tem o efeito de estabilizar a variância dos dados, enquanto a o uso da raiz quadrada tem o efeito de reduzir a variância dos dados.

---

{{<slide background-color="#54787d">}} 

## Discretização de dados

---

- **Discretização** é o processo de transformar uma variável contínua em uma variável categórica ou discreta. 

- É útil quando se deseja agrupar valores contínuos em categorias ou intervalos para simplificar a análise ou reduzir o efeito de valores extremos. 
---

- Algumas das técnicas comuns de discretização incluem:

  - **Discretização equi-probabilística:** Essa técnica envolve a divisão dos dados em intervalos de tamanho igual, de modo que cada intervalo contenha aproximadamente a mesma quantidade de observações.

---

  - **Discretização equi-distante:** Nessa técnica, os dados são divididos em intervalos de tamanho igual, com base em uma distância predefinida.

---

  - **Discretização por quartis:** Os dados são divididos em quartis, com base nos valores de corte que dividem os dados em quatro partes iguais.
  
---

  - **Discretização por frequência:** Os dados são divididos em intervalos com base na frequência de observações em cada intervalo.

---

  - **Binarização:** A binarização é uma técnica de transformação de dados que converte valores quantitativos em valores binários (0 ou 1) com base em um valor de corte.
  
---

#### Exemplo de binarização

![Binarização](fig05.png)

---

  - **One-Hot Encoding:** O One-Hot Encoding é uma técnica de transformação de dados que converte variáveis categóricas em vetores binários para permitir a análise em modelos de machine learning.
  
---

#### Exemplo de one-hot enconding

![OHE](fig08.png)



