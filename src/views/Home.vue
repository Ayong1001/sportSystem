<script setup>
import Left from '../components/home/Left.vue'
import Right from '../components/home/Right.vue'
</script>

<template>
  <div class="home">
    <Left></Left>
    <Right></Right>
  </div>
</template>

<style lang="less" scoped>
.home {
  width: 100%;
  height: 100%;
  padding: 0 34px 50px 34px;
  display: flex;
}
</style>
