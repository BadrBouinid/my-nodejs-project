<template>
  <div>
    <h2>Graphiques de ventes</h2>
    <Bar :data="chartData" />
  </div>
</template>

<script>
import { Bar } from "vue-chartjs";
import { defineComponent } from "vue";
import {
  Chart as ChartJS,
  Title,
  Tooltip,
  Legend,
  BarElement,
  CategoryScale,
  LinearScale,
} from "chart.js";

ChartJS.register(
  Title,
  Tooltip,
  Legend,
  BarElement,
  CategoryScale,
  LinearScale
);

export default defineComponent({
  components: {
    Bar,
  },
  props: {
    salesData: Array,
  },
  computed: {
    chartData() {
      return {
        labels: this.salesData.map((data) => data.category),
        datasets: [
          {
            label: "Ventes par catégorie",
            data: this.salesData.map((data) => data.sales),
            backgroundColor: "rgba(75, 192, 192, 0.2)",
            borderColor: "rgba(75, 192, 192, 1)",
            borderWidth: 1,
          },
        ],
      };
    },
  },
});
</script>
