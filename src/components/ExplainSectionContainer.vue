<template>
  <section class="section-container">
    <slot />
  </section>
</template>

<style>
  .section-container {
    display: flex;
    align-items: start;
    flex-direction: column;
    margin-top: 1rem;
  }
</style>
