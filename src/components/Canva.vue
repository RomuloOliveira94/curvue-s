<script setup lang="ts">
  //curve S
  import { ref, onMounted } from "vue";

  const canvas = ref<HTMLCanvasElement | null>(null);
  const andamentoPrevisto = [0, 5, 10, 15, 25, 35, 45, 55, 65, 75, 85, 95, 100];
  const andamentoReal = [0, 2, 5, 10, 20, 25, 30, 35, 45, 65, 75, 85, 90];
  const meses = [
    "Jan",
    "Fev",
    "Mar",
    "Abr",
    "Mai",
    "Jun",
    "Jul",
    "Ago",
    "Set",
    "Out",
    "Nov",
    "Dez",
  ];

  const porcentagem = [
    "0%",
    "10%",
    "20%",
    "30%",
    "40%",
    "50%",
    "60%",
    "70%",
    "80%",
    "90%",
    "100%",
  ]

  onMounted(() => {
    const ctx = canvas.value?.getContext("2d");
    if (!canvas.value || !ctx) return;
    
    canvas.value.width = 1250;
    canvas.value.height = 650;
    ctx.translate(0, 30)
    const pontosPrevistos = andamentoPrevisto.map((andamento, index) => {
      return {
        meses: index * 100,
        andamento: 600 - andamento * 6,
      };
    });

    const pontosReais = andamentoReal.map((andamento, index) => {
      return {
        meses: index * 100,
        andamento: 600 - andamento * 6,
      };
    });

    console.log(pontosPrevistos);

    ctx.beginPath();
    pontosPrevistos.forEach((ponto, index) => {
      if (index === 0) {
        ctx.moveTo(ponto.meses, ponto.andamento);
      } else {
        ctx.lineTo(ponto.meses, ponto.andamento);
        ctx.lineWidth = 2;
        ctx.strokeStyle = "blue";
        ctx.lineCap = "round";
        ctx.lineJoin = "round";
        ctx.stroke();
        ctx.beginPath();
        ctx.fillStyle = "blue";
        ctx.fillText(andamentoPrevisto[index] + "%", ponto.meses, ponto.andamento - 10);
        ctx.arc(ponto.meses, ponto.andamento, 8, 0, Math.PI * 2);
        ctx.fill();
        ctx.font = "18px sans serif";
        ctx.textAlign = "end";
        ctx.textBaseline = "bottom";
        
      }
    });
    ctx.closePath();

    ctx.beginPath();
    pontosReais.forEach((ponto, index) => {
      if (index === 0) {
        ctx.moveTo(ponto.meses, ponto.andamento);
      } else {
        ctx.lineTo(ponto.meses, ponto.andamento);
        ctx.strokeStyle = "red";
        ctx.lineWidth = 2;
        ctx.lineCap = "round";
        ctx.lineJoin = "round";
        ctx.stroke();
        ctx.beginPath();
        ctx.fillStyle = "red";
        ctx.fillText(andamentoReal[index] + "%", ponto.meses, ponto.andamento - 10);
        ctx.arc(ponto.meses, ponto.andamento, 8, 0, Math.PI * 2);
        ctx.fill();

        ctx.font = "18px sans serif";
        ctx.fillStyle = "green";
        ctx.textAlign = "end";
        ctx.textBaseline = "bottom";
        ctx.fillText(meses[index - 1], ponto.meses, 620);
      }
    });
    ctx.closePath();

    ctx.beginPath();
    ctx.moveTo(0, 600);
    ctx.lineTo(1200, 600);
    ctx.strokeStyle = "black";
    ctx.lineWidth = 2;
    ctx.stroke();
    ctx.closePath();

    ctx.beginPath();
    ctx.moveTo(0, 600);
    ctx.lineTo(0, 0);
    ctx.strokeStyle = "black";
    ctx.lineWidth = 2;
    ctx.stroke();
    ctx.closePath();

    ctx.beginPath();
    ctx.moveTo(0, 600);
    porcentagem.forEach((porcentagem, index) => {
      ctx.fillStyle = "black";
      ctx.font = "18px sans serif";
      ctx.textAlign = "end";
      ctx.textBaseline = "bottom";
      ctx.fillText(porcentagem, 50, 600 - index * 60);
    });

    ctx.closePath();

  });
</script>

<template>
  <canvas ref="canvas" />
</template>

<style>
  canvas {
    display: block;
    margin: 0 auto;
    border: 1px solid #000;
    padding: 12px;
    background-color: azure;
    border: 2px solid black;
    border-radius: 10px;
  }
</style>
