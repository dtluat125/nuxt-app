<script setup>
// import { ref } from "vue";
const route = useRoute();
const { data: coins, pending } = await useFetch(
  "/api/ticker?id=" + route.params.id
);
// const coin = ref(coins.value[0]);
const coin = computed(() => coins.value[0])
</script>
<template>
  <div v-if="coin">
    <h2>{{ coin?.name }} Detail page</h2>
    <table border="1 px solid">
      <thead>
        <th>Symbol</th>
        <th>Rank</th>
        <th>Price - US $</th>
        <th>Market Cap - US $</th>
      </thead>
      <tbody>
        <tr>
          <td>{{ coin?.symbol }}</td>
          <td>{{ coin?.rank }}</td>
          <td>{{ coin?.price_usd }}</td>
          <td>{{ coin?.market_cap_usd }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>
