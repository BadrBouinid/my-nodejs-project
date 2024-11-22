<template>
  <div>
    <h2>Tableau des produits</h2>
    <table>
      <thead>
        <tr>
          <th>Nom</th>
          <th>Date d'ajout</th>
          <th>Prix</th>
          <th>Total des ventes</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="product in products" :key="product.name">
          <td>{{ product.name }}</td>
          <td>{{ product.addedDate }}</td>
          <td>{{ product.price }} €</td>
          <td>{{ product.totalSales }} ventes</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  props: {
    products: Array,
  },
};
</script>

<style scoped>
table {
  width: 100%;
  border-collapse: collapse;
}

th,
td {
  padding: 8px;
  border: 1px solid #ddd;
}

th {
  text-align: left;
}
</style>
