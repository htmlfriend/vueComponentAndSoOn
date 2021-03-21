<template>
  <div>
    <div class="card">
      <slot name="header"></slot>
      <slot name="default"> Not comments</slot>
      <div v-if="$slots.footer">
        <slot name="footer"></slot>
     </div>
    </div>
  </div>
</template>

<script>
export default {
  mounted () {
    console.log('mounted', this.$slots)
  }
}
</script>

<style lang="scss" scoped>

</style>
