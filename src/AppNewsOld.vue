<template>
  <div class="container pt-1">
    <div class="card">
      <h2>Main news</h2>
      <h3>{{ now }}</h3>
      <h4>Opened {{openRate}} || Read {{readRate}}  || UnmarkRate {{ unmarkRate}}</h4>
    </div>
  <app-news v-for='item in news' :key='item.id' :title='item.title' :id='item.id' :is-open='item.isOpen' :was-read='item.wasRead' :unmarked='item.unmarked' @unmark='unreadNews' @open-news='openNews' @read-news='readNews' ></app-news>
  </div>
</template>

<script>
import AppNews from './AppNews'
export default {
  data () {
    return {
      title: 'The header from data',
      now: new Date().toLocaleString(),
      openRate: 0,
      readRate: 0,
      unmarkRate: 0,
      news: [{ title: 'John Baden won election', id: 1, isOpen: false, wasRead: false, unmarked: true }, { title: 'Vue works well', id: 2, isOpen: false, wasRead: false, unmarked: true }]
    }
  },
  provide () {
    return {
      title: 'List of news',
      news: this.news
    }
  },
  methods: {
    openNews (data, data2) {
      console.log('data', data)
      console.log('data2', data2)
      this.openRate++
    },
    readNews (id) {
      this.readRate++
      // find componet to change
      console.log('id of an element', id)
      const idx = this.news.findIndex(news => news.id === id)
      this.news[idx].wasRead = true
      this.news[idx].unmarked = false
      console.log('idx', this.news[idx].id)
    },
    unreadNews (id) {
      console.log('id of an element', id)
      const newPost = this.news.find(news => news.id === id)
      newPost.wasRead = false
      newPost.unmarked = true
      this.unmarkRate++
      this.readRate--
      console.log('idx', newPost.title)
    }
  },
  components: {
    'app-news': AppNews
  }
}
</script>

<style scoped lang="scss">
h2 {
  color: red
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
