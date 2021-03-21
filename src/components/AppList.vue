<template>
  <div class="card">
    <ul>
      <li :key="item" v-for="(item, idx) in 5">
        <slot :iter='item' :id='idx'></slot>
      </li>
    </ul>

  </div>
</template>

<script>
export default {

}
</script>

<style lang="scss" scoped>

</style>
