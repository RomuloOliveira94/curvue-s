<script setup lang="ts">
  import ExplainSectionContainer from "./ExplainSectionContainer.vue";
</script>

<template>
  <ExplainSectionContainer>
    <h1>O que é curva em S?</h1>

    <p>
      A curva em S é uma representação gráfica que relaciona a quantidade de
      trabalho investida ao longo do tempo. Assim, nesse gráfico, o eixo
      vertical (y) corresponde à baseline de custos e trabalho, enquanto o eixo
      horizontal (x) corresponde ao tempo de andamento do projeto.
    </p>
  </ExplainSectionContainer>
  <ExplainSectionContainer>
    <h1>Por que é importante utilizar a curva em S?</h1>

    <p>
      A curva em S apresenta a quantidade de trabalho investida e o tempo de
      duas maneiras: o que foi estimado no planejamento e o que foi realizado, o
      que permite comparar e analisar o projeto. Com isso, ela evidencia os
      desvios, sendo uma importante aliada para:
    </p>

    <ul>
      <li>Identificar a saúde do projeto;</li>
      <li>Evitar riscos negativos;</li>
      <li>Tomar decisões mais assertivas;</li>
      <li>Melhor utilização dos recursos;</li>
      <li>Implementar melhorias durante o andamento;</li>
      <li>Garantir o sucesso do projeto.</li>
    </ul>
  </ExplainSectionContainer>

  <ExplainSectionContainer>
    <h1>Como funciona a curva em S do projeto?</h1>

    <p>
      Como funciona a curva em S do projeto? Como a curva em S leva em
      consideração as estimativas de custo e esforço, o primeiro passo para
      construí-la é justamente estabelecer a linha de base do projeto.
    </p>

    <p>
      Com a linha de base estruturada, o gráfico pode ser montado conforme as
      atividades forem avançando. Normalmente, esses dados são atualizados mês a
      mês, mas nada impede que eles sejam acumulados por trimestre, semestre ou
      por ano, dependendo da necessidade do projeto.
    </p>
  </ExplainSectionContainer>
</template>

<style scoped>
  h1 {
    font-size: 2rem;
    margin-bottom: 1rem;
    font-weight: 900;
  }

  p {
    font-size: 1.5rem;
    font-weight: 500;
  }

  li {
    font-size: 1.5rem;
    font-weight: 500;
  }

  ul {
    display: flex;
    width: 100%;
    flex-direction: column;
    align-items: start;
    list-style-type: disc;
    margin-left: 2rem;
  }
</style>
