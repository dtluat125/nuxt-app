<script setup>
const data = await useFetch("/api/tickers?limit=10");
const currencyList = data.data?.value?.data;
</script>

<template>
  <main>
    <h1>Index Page</h1>
    {{data.pending}}
    <div v-if="!data.pending">Loading...</div>

    <table border="1 px solid" v-if="data.data">
      <thead>
        <tr>
          <th>Name</th>
          <th>Symbol</th>
          <th>Price</th>
          <th>Details</th>
        </tr>
      </thead>
      <tr v-for="currency in currencyList" :key="currency.id">
        <td>{{ currency?.name }}</td>
        <td>{{ currency?.symbol }}</td>
        <td>{{ currency?.price_usd }}</td>
        <td>
          <NuxtLink :to="'/currency/' + currency?.id">{{
            currency?.id
          }}</NuxtLink>
        </td>
      </tr>
    </table>
  </main>
</template>
