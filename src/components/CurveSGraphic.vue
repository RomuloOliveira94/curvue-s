<script setup lang="ts">
  //curve S
  import { ref, onMounted } from "vue";

  const canvas = ref<HTMLCanvasElement | null>(null);
  const planned = [0, 5, 10, 15, 25, 35, 45, 55, 65, 75, 85, 95, 100];
  const actual = [0, 2, 5, 10, 20, 25, 30, 35, 45, 65, ];

  const month = [
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

  const percentage = [
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
  ];

  onMounted(() => {
    const ctx = canvas.value?.getContext("2d");
    if (!canvas.value || !ctx) return;

    canvas.value.width = 1250;
    canvas.value.height = 650;
    ctx.translate(30, 30);

    const plannedPoints = planned.map((andamento, index) => {
      return {
        month: index * 100,
        andamento: 600 - andamento * 6,
      };
    });

    const actualPoints = actual.map((andamento, index) => {
      return {
        month: index * 100,
        andamento: 600 - andamento * 6,
      };
    });

    ctx.beginPath();
    plannedPoints.forEach((point, index) => {
      if (index === 0) {
        ctx.moveTo(point.month, point.andamento);
      } else {
        ctx.lineTo(point.month, point.andamento);
        ctx.lineWidth = 2;
        ctx.strokeStyle = "#0000D3";
        ctx.lineCap = "round";
        ctx.lineJoin = "round";
        ctx.stroke();

        ctx.beginPath();
        ctx.fillStyle = "#0000D3";
        ctx.arc(point.month, point.andamento, 8, 0, Math.PI * 2);
        ctx.fill();

        ctx.font = "18px sans serif";
        ctx.textAlign = "end";
        ctx.textBaseline = "bottom";
        ctx.fillText(
          planned[index] + "%",
          point.month,
          point.andamento - 10
        );

        ctx.font = "18px sans serif";
        ctx.fillStyle = "black";
        ctx.textAlign = "end";
        ctx.textBaseline = "bottom";
        ctx.fillText(month[index - 1], point.month, 620);
      }
    });
    ctx.closePath();

    ctx.beginPath();
    actualPoints.forEach((point, index) => {
      if (index === 0) {
        ctx.moveTo(point.month, point.andamento);
      } else {
        ctx.lineTo(point.month, point.andamento);
        ctx.strokeStyle = "#D3003D";
        ctx.lineWidth = 2;
        ctx.lineCap = "round";
        ctx.lineJoin = "round";
        ctx.stroke();

        ctx.beginPath();
        ctx.fillStyle = "#D3003D";
        ctx.fillText(
          actual[index] + "%",
          point.month,
          point.andamento - 10
        );
        ctx.arc(point.month, point.andamento, 8, 0, Math.PI * 2);
        ctx.fill();
      }
    });
    ctx.closePath();

    ctx.beginPath();

    ctx.moveTo(0, 600);
    ctx.lineTo(1200, 600);
    ctx.strokeStyle = "black";
    ctx.lineWidth = 2;
    ctx.stroke();

    ctx.moveTo(0, 600);
    ctx.lineTo(0, 0);
    ctx.strokeStyle = "black";
    ctx.lineWidth = 2;
    ctx.stroke();

    ctx.save();
    ctx.translate(0, 300);
    ctx.rotate(-Math.PI / 2);
    ctx.fillStyle = "black";
    ctx.font = "20px sans serif";
    ctx.textAlign = "center";
    ctx.fillText("Progresso", 0, 0);
    ctx.restore();

    ctx.moveTo(0, 600);
    percentage.forEach((percentage, index) => {
      ctx.fillStyle = "black";
      ctx.font = "18px sans serif";
      ctx.textAlign = "end";
      ctx.textBaseline = "bottom";
      ctx.fillText(percentage, 50, 600 - index * 60);
    });

    ctx.closePath();
  });
</script>

<template>
  <canvas ref="canvas" />
  <small
    >Este gráfico foi desenvolvido utilizando HTML, Vue.JS, e Canvas API
  </small>
</template>

<style>
  canvas {
    display: block;
    margin: 0 auto;
    border: 1px solid #000;
    padding: 12px;
    background-color: white;
    border: 2px solid black;
    border-radius: 10px;
  }

  small {
    display: block;
    text-align: center;
    margin-top: 1rem;
    font-weight: bold;
  }
</style>
