<template>
  <hr />
  <h2>{{title}}</h2>
  <ul>
    <li :key='item.id' v-for='item in news'>{{item.title}} <span v-if="item.wasRead">!!!</span>
    </li>
  </ul>
</template>

<script>
export default {
  inject: ['title', 'news']
}
</script>

<style lang="scss" scoped>

</style>
