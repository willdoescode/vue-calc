<template>
  <div class="head">
    {{ headText }}
  </div>
</template>

<script>
export default {
  name: 'Header',
  props: {
    headText: String
  }
}
</script>

<style scoped>
.head {
  font-size: 50px;
  padding-bottom: 20px;
  font-weight: bold;
  background: -webkit-linear-gradient(lightgreen, lightblue);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  -webkit-text-stroke: 1px black;
}
</style>
