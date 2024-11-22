<template>
  <div class="dashboard">
    <h1>Tableau de Bord</h1>

    <div class="filter">
      <label for="period">Sélectionner une période :</label>
      <select id="period" v-model="selectedPeriod" @change="fetchData">
        <option value="7">7 derniers jours</option>
        <option value="30">30 derniers jours</option>
        <option value="365">12 derniers mois</option>
      </select>
    </div>

    <div class="stats">
      <p><strong>Total des ventes :</strong> {{ totalSales }} €</p>
      <p><strong>Top 5 Produits :</strong></p>
      <ul>
        <li v-for="product in topProducts" :key="product.name">
          {{ product.name }} ({{ product.sales }} ventes)
        </li>
      </ul>
    </div>

    <sales-charts :sales-data="salesData" />
    <product-table :products="products" />
  </div>
</template>

<script>
import SalesCharts from "./SalesCharts.vue";
import ProductTable from "./ProductTable.vue";

export default {
  name: "Dashboard",
  components: {
    SalesCharts,
    ProductTable,
  },
  data() {
    return {
      selectedPeriod: 7,
      totalSales: 0,
      topProducts: [],
      salesData: [],
      products: [],
    };
  },
  methods: {
    fetchData() {
      // Simuler les données
      this.totalSales = 12000;
      this.topProducts = [
        { name: "Produit A", sales: 150 },
        { name: "Produit B", sales: 120 },
      ];
      this.salesData = [
        { category: "Électronique", sales: 40 },
        { category: "Mode", sales: 30 },
        { category: "Maison", sales: 30 },
      ];
      this.products = [
        {
          name: "Produit A",
          addedDate: "2023-01-01",
          price: 29.99,
          totalSales: 150,
        },
        {
          name: "Produit B",
          addedDate: "2023-02-01",
          price: 19.99,
          totalSales: 120,
        },
      ];
    },
  },
  created() {
    this.fetchData();
  },
};
</script>

<style scoped>
.dashboard {
  padding: 20px;
}

.filter {
  margin-bottom: 20px;
}

.stats {
  margin: 20px 0;
}

ul {
  list-style: none;
  padding: 0;
}

ul li {
  margin: 5px 0;
}
</style>
