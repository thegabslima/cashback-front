<script>
import CardContainer from './components/CardContainer.vue'
import ListTransactionCard from './components/ListTransactionsCard.vue'

export default {
  name: 'App',
  components: {
    CardContainer,
    ListTransactionCard,
  }
}
</script>

<template>
  <div>
    <CardContainer title="Transações"/>
    <ListTransactionCard />
  </div>
</template>

<style>
  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
  }
    h4 {
          color: #333;
      }
    .card {
        margin: 20px;
        box-shadow: 2px 3px 4px 2px rgb(0 0 0 / 18%);
        border-radius: 10px;
        transition: 0.3s;
    }
    .container {
        padding: 2px 16px;
    }
</style>
