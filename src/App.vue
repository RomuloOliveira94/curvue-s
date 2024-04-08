<script setup lang="ts">
  import Canva from "./components/Canva.vue";
</script>

<template>
  <main>
    <header>
      <div>
        <h1>Gráfico de andamento</h1>
        <p>
          Este gráfico mostra o andamento previsto e o andamento real do projeto
          ao longo dos meses.
        </p>
        <div class="obs-section">
          <div class="blue-section">
            <span class="line-blue"></span>
            <p>Previsão de Andamento do Projeto</p>
          </div>
          <div class="red-section">
            <span class="line-red"></span>
            <p>Andamento Real do Projeto</p>
          </div>
        </div>
      </div>
    </header>
    <Canva />
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

  h1 {
    font-size: 2rem;
    text-align: center;
    margin-bottom: 1rem;
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
    gap: 12px;
  }

  .red-section {
    display: flex;
    align-items: center;
    gap: 12px;
  }

  .line-blue {
    display: inline-block;
    width: 20px;
    height: 20px;
    background-color: blue;
  }

  .line-red {
    display: inline-block;
    width: 20px;
    height: 20px;
    background-color: red;
    margin-right: 10px;
  }
</style>
