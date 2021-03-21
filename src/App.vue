<template>
  <div class="container pt-1">
    <div class="card">
    <app-async-component></app-async-component>
      <h2>Dinamic and async components</h2>
      <app-button ref="myBtn" :color="oneColor" @action='active = "one"'>One</app-button>
      <app-button @action='active = "two"' :color="twoColor" >Two</app-button>
    </div>
    <keep-alive>
      <component :is="componentName"></component>
    </keep-alive>
  </div>

</template>

<script>
import AppButton from './components/AppButton.vue'
import AppTextOne from './components/AppTextOne'
import AppTextTwo from './components/AppTextTwo.vue'
export default {
  data () {
    return {
      active: 'one'
    }
  },
  mounted () {
    // setTimeout(() => {
    //   this.componentName = 'new comp name'
    // }, 2000)
    this.$refs.myBtn.btnLog()
  },
  computed: {
    // componentName () {
    // if (this.active === 'one') {
    //   return 'app-text-one'
    // } else {
    //   return 'app-text-two'
    // }

    // return 'app-text-' + this.active
    componentName: {
      get () {
        return 'app-text-' + this.active
      },
      set (value) {
        console.log('value', value)
      }
    },
    oneColor () {
      return this.active === 'one' ? 'primary' : ''
    },
    twoColor () {
      return this.active === 'two' ? 'primary' : ''
    }
  },
  components: { AppButton, AppTextOne, AppTextTwo }
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
