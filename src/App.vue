<script setup lang="ts">
  import CurveSGraphic from "./components/CurveSGraphic.vue";
  import ExplainSection from "./components/ExplainSection.vue";
  import Footer from "./components/Footer.vue";
  import Header from "./components/Header.vue";
</script>

<template>
  <main id="main-content">
    <Header />
    <div>
      <h1>Gráfico de progresso em curva S</h1>
      <p>
        Este gráfico mostra o progresso previsto e o progresso real de um
        projeto de sistema no período de um ano.
      </p>
      <div class="obs-section">
        <div class="blue-section">
          <span class="line-blue"></span>
          <p>Progresso previsto do Projeto</p>
        </div>
        <div class="red-section">
          <span class="line-red"></span>
          <p>Progresso Real do Projeto</p>
        </div>
      </div>
    </div>
    <CurveSGraphic />
    <br />
    <br />
    <ExplainSection />
    <Footer />
  </main>
</template>

<style scoped>
  header {
    line-height: 1.5;
    display: flex;
    flex-direction: column;
    align-items: center;
    padding: 2rem 0;
  }

  p {
    text-align: center;
    font-size: 1.5rem;
    margin-bottom: 1rem;
  }

  h1 {
    text-align: center;
    font-size: 2rem;
    margin-bottom: 2rem;
  }

  .logo {
    display: block;
    margin: 0 auto 2rem;
  }
  .obs-section {
    display: flex;
    justify-content: center;
    align-items: center;
    margin-top: 1rem;
  }

  .blue-section {
    display: flex;
    align-items: center;
    margin-right: 2rem;
    margin-bottom: 2rem;
    gap: 12px;
  }

  .red-section {
    display: flex;
    align-items: center;
    margin-bottom: 2rem;
    gap: 12px;
  }

  .line-blue {
    display: inline-block;
    width: 20px;
    height: 20px;
    background-color: #0000d3;
  }

  .line-red {
    display: inline-block;
    width: 20px;
    height: 20px;
    background-color: #d3003d;
    margin-right: 10px;
  }
</style>
