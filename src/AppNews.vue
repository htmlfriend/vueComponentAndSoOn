<template>
  <div class="card">
    <h3>{{title}}</h3>
    <app-button-vue @action='open' >{{isNewsOpen ? 'Close' : 'Open'}}
    </app-button-vue>
    <app-button-vue v-if='!unmarked' @action="$emit('unmark',id)" color="danger">Mark unreadable
    </app-button-vue>
    <div v-if='isNewsOpen'>
      <hr />
<p >Lorem, ipsum dolor sit amet consectetur adipisicing elit. Veritatis in modi enim quisquam cum illo vero fugit quia laborum suscipit omnis nobis excepturi, perferendis incidunt dicta maxime. Nam, aut molestiae natus amet labore eveniet soluta at neque tempore eos. Pariatur numquam sunt ab voluptate esse?</p>
<app-button-vue v-if='!wasRead' color="primary" @action="mark" >Read news</app-button-vue>
    <app-news-list></app-news-list>
    </div>
  </div>
</template>

<script>
import AppButtonVue from './components/AppButton.vue'
import AppNewsList from './components/AppNewsList'
export default {
  props: {
    title: {
      type: String,
      required: true
    },
    id: {
      type: Number,
      required: true
    },
    isOpen: {
      type: Boolean,
      required: false,
      default: false
    },
    wasRead: {
      type: Boolean,
      required: true,
      default: false
    },
    unmarked: {
      type: Boolean,
      default: true
    }
  },
  // emits: ['open-news'],
  emits: {
    'open-news': null,
    'read-news' (id) {
      if (id) {
        return true
      }
      console.warn('there is not id for emit read-news')
    },
    unmarked: null
  },
  data () {
    return {
      isNewsOpen: this.isOpen

    }
  },
  methods: {
    open () {
      this.isNewsOpen = !this.isNewsOpen
      if (this.isNewsOpen) {
        // pass emit to parents
        this.$emit('open-news')
      }
    },
    mark () {
      this.isNewsOpen = false
      this.$emit('read-news', this.id)
    }
    // unmarkedPost () {
    //   if (this.unmarked) {
    //     this.$emit('unmark', this.id)
    //   }
    // }
  },
  components: { AppButtonVue, AppNewsList }
}
</script>
