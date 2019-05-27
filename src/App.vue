<template>
  <div id="app">
  	<Deposits />
  	<br>
  	<br>
    <AddDeposits/>

  </div>
</template>

<script>
import AddDeposits from './components/AddDeposits.vue'
import Deposits from './components/Deposits.vue'

export default {
  name: 'app',
  components: {
    AddDeposits,
    Deposits
  }
}
</script>

<style>

</style>
