<template>
  <div class="root">
    <router-view></router-view>
  </div>
</template>

<script>
export default {
  data () {
    return {
    }
  }
}
</script>

<style scoped lang='scss'>
  .root{
    flex: 1;
    background-color: blueviolet;
    background-image: linear-gradient(to right, #202020, #292929);
    height: 100%;
    padding: 20px 30px;
  }
</style>
