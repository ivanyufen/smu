<template>
  <div class="about">
    <h1>This is an about page</h1>
    <div class="md-layout md-gutter">
    <div class="md-layout-item">1</div>
    <div class="md-layout-item">2</div>
    <div class="md-layout-item">3</div>
    </div>
  </div>
</template>

<script>
import URL from "./../endpoint.js"
export default{
  name: 'about',
  mounted(){
  }
}
</script>

<style scoped>
.md-layout-item{
  background: lightpink;
}
</style>
