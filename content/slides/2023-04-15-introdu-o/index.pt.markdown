---
title: Pré-processamento - parte 01
author: Tiago Pereira
date: '2023-04-15'
slug: introdu-o
categories:
  - Pré-processamento
tags:
  - Pre
summary: 'Pré-processamento, importância, problemas reais, tipos de dados e preparação da base de dados'
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

## Pré-processamento de dados


---

**Pré-processamento** de dados se define como um conjunto de técnicas e procedimentos aplicados aos dados **antes** de sua utilização em um modelo ou algoritmo de análise. 

É uma etapa fundamental na análise de dados, pois visa garantir que os dados estejam **corretos**, **completos**, **coerentes** e em um **formato** apropriado para serem analisados. 

---

O pré-processamento de dados inclui diversas atividades, como limpeza de dados, transformação de dados, redução de dimensão, seleção de recursos, normalização e amostragem. 

O objetivo geral do pré-processamento de dados é aumentar a qualidade e a precisão da análise de dados, minimizando a influência de ruídos e inconsistências nos resultados finais.

---

{{<slide background-color="#54787d">}} 

## Importância do pré-processamento

---

O pré-processamento de dados é uma etapa importante e crítica no processo de análise de dados. Algumas razões pelas quais é importante realizar o pré-processamento são...

---

  1. **Melhoria da qualidade dos dados:** O pré-processamento de dados pode ajudar a melhorar a qualidade dos dados, eliminando dados duplicados, ausentes ou inconsistentes. Isso resulta em dados mais precisos e confiáveis para análise.

---

  2. **Ajuste dos dados para a análise:** Muitos modelos e algoritmos de análise de dados requerem que os dados estejam em um formato específico. Na etapa do pré-processamento de dados ajusta-se os dados para que estejam em um formato adequado para a análise.
  
---

  3. **Eliminação de ruídos:** Os dados geralmente contêm ruídos, como outliers e valores extremos, que podem afetar negativamente a precisão dos resultados finais. Nesta etapa, elimina-se esses ruídos, tornando os resultados mais precisos.
  
---

  4. **Redução da complexidade dos dados:** Podemos reduzir a complexidade dos dados, eliminando variáveis desnecessárias e reduzindo o número de dimensões do conjunto de dados. Isso torna mais fácil a análise e interpretação dos dados.

---

  5. **Melhoria do desempenho do modelo:** O pré-processamento de dados pode ajudar a melhorar o desempenho do modelo, ao remover dados redundantes, normalizar os dados e selecionar os recursos mais importantes. Isso resulta em modelos mais precisos e confiáveis.
  
---

<a href="https://www.forbes.com/sites/gilpress/2016/03/23/data-preparation-most-time-consuming-least-enjoyable-data-science-task-survey-says/?sh=34ce9abe6f63" target="_blank" rel="noopener noreferrer"><img src="time.jpg"  width="1000" height="400"></a>

---

<a href="https://gph.is/g/Eq2rpxa" target="_blank" rel="noopener noreferrer"><img src="https://media3.giphy.com/media/9u514UZd57mRhnBCEk/giphy.gif"  width="800" height="500"></a>

---

#### O que há de errado nessa base?

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
    <th class="tg-34fe">Usuário</th>
    <th class="tg-34fe">Idade</th>
    <th class="tg-34fe">Cidade</th>
    <th class="tg-34fe">Data</th>
    <th class="tg-34fe">Salário</th>
    <th class="tg-34fe">Npáginas</th>
    <th class="tg-34fe">Nsessões</th>
    <th class="tg-34fe">Nprodutos</th>
    <th class="tg-34fe">Clique</th>
    <th class="tg-34fe">Comprou</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td class="tg-c3ow">user1</td>
    <td class="tg-c3ow">22</td>
    <td class="tg-c3ow">Belo Horizonte</td>
    <td class="tg-c3ow">22/10/21</td>
    <td class="tg-c3ow">1200</td>
    <td class="tg-c3ow">5</td>
    <td class="tg-c3ow">2</td>
    <td class="tg-c3ow">5</td>
    <td class="tg-c3ow">no</td>
    <td class="tg-c3ow">no</td>
  </tr>
  <tr>
    <td class="tg-c3ow">user2</td>
    <td class="tg-c3ow">1</td>
    <td class="tg-c3ow">São paulo</td>
    <td class="tg-c3ow">20/09/22</td>
    <td class="tg-c3ow">5000</td>
    <td class="tg-c3ow">21</td>
    <td class="tg-c3ow">4</td>
    <td class="tg-c3ow">11</td>
    <td class="tg-c3ow">yes</td>
    <td class="tg-c3ow">yes</td>
  </tr>
  <tr>
    <td class="tg-c3ow">user 3</td>
    <td class="tg-c3ow">41</td>
    <td class="tg-c3ow">BH</td>
    <td class="tg-c3ow">23 de dezembro 2022</td>
    <td class="tg-c3ow">12000</td>
    <td class="tg-c3ow">2</td>
    <td class="tg-c3ow">1</td>
    <td class="tg-c3ow">3</td>
    <td class="tg-c3ow">NA</td>
    <td class="tg-c3ow">yes</td>
  </tr>
  <tr>
    <td class="tg-c3ow">user 4</td>
    <td class="tg-c3ow">32</td>
    <td class="tg-c3ow">Miami</td>
    <td class="tg-c3ow">22/10/01</td>
    <td class="tg-c3ow">50000</td>
    <td class="tg-c3ow">NA</td>
    <td class="tg-c3ow">5</td>
    <td class="tg-c3ow">2</td>
    <td class="tg-c3ow">yes</td>
    <td class="tg-c3ow">no</td>
  </tr>
  <tr>
    <td class="tg-c3ow">user5</td>
    <td class="tg-c3ow">20</td>
    <td class="tg-c3ow">Tokyo</td>
    <td class="tg-c3ow">23/01/25</td>
    <td class="tg-c3ow">12220</td>
    <td class="tg-c3ow">5</td>
    <td class="tg-c3ow">5</td>
    <td class="tg-c3ow">8</td>
    <td class="tg-c3ow">no</td>
    <td class="tg-c3ow">yes</td>
  </tr>
  <tr>
    <td class="tg-c3ow">user6</td>
    <td class="tg-c3ow">28</td>
    <td class="tg-c3ow">NY</td>
    <td class="tg-c3ow">March 14, 2018</td>
    <td class="tg-c3ow">250000</td>
    <td class="tg-c3ow">8</td>
    <td class="tg-c3ow">NA</td>
    <td class="tg-c3ow">NA</td>
    <td class="tg-c3ow">no</td>
    <td class="tg-c3ow">yes</td>
  </tr>
</tbody>
</table>

---

#### Principais problemas com dados reais

![Principais problemas](tipos.png)

---

#### Tipos de dados

Os dados podem ser classificados em três tipos principais: estruturados, semiestruturados e não estruturados

---

#### Estruturados

São dados organizados em uma estrutura definida, como tabelas, colunas e linhas em um banco de dados. 

- **Exemplos:** informações de vendas, cadastros de clientes, registros de transações financeiras, entre outros.

---

Para dados estruturados, a técnica de pré-processamento mais comum é a **limpeza de dados**, além da **seleção de atributos relevantes**, **normalização** e **transformação** de dados.

---

#### Semiestruturados

São dados que não possuem uma estrutura rígida como os dados estruturados, mas possuem algumas formas de organização, como marcadores, tags ou atributos. 

- **Exemplos:** arquivos XML, JSON, HTML, entre outros.

---

Para dados semiestruturados, a técnica de pré-processamento mais comum é a **extração de informações relevantes**, que envolve a identificação de padrões e estruturas em dados como XML, JSON ou HTML, além da **extração de dados** a partir dessas estruturas. 

---

#### Não estruturados

São dados que não possuem uma estrutura definida e estão em formato livre, como texto, imagens, vídeos, áudios, e-mails, redes sociais, entre outros. Exigem o uso de técnicas mais avançadas de **processamento de linguagem natural**, **reconhecimento de padrões** e **aprendizado de máquina**. 

---

Com o aumento da quantidade de dados gerados diariamente, a análise de **dados semiestruturados** e **não estruturados** tem se tornado cada vez mais importante para empresas que desejam obter insights valiosos sobre seus clientes, mercado e tendências. 

---

### Processo de preparação da base de dados

![Preparação da base de dados](pre.png)

