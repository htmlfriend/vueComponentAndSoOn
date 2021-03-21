<template>
  <div class="container pt-1">
    <div class="card">
      <h2>Slots</h2>
    </div>
    <app-block>
      <p>Text for new blocks</p>

      <template v-slot:header>
        <h3>This is title</h3>
      </template>
      <template v-slot:footer>
        <h5>This is footer of the page</h5>
      </template>
    </app-block>
    <div>
      <app-list>
        <template #default="{iter, id}">
          <span style="color: #c25205">item of iter{{iter}} id --- {{id}}</span>
        </template>
      </app-list>
    </div>
  </div>

</template>

<script>
import AppBlock from './components/AppBlock.vue'
import AppList from './components/AppList'
export default {
  components: { AppBlock, AppList }
}
</script>

<style scoped lang="scss">

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
