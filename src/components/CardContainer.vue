<script>
export default {
  name: 'CardContainer',
  props: {
    title: String
  }
}
</script>


<template>
    <div class="card">
        <div class="container">
        <h2><b>{{ title }}</b></h2>
        </div>
    </div>
</template>

<style>
    h4 {
        color: #333;
    }
</style>