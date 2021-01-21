<template>
  <div class="container pt-1">
    <div class="card">
      <h2>Актуальные Новости за {{ now }}</h2>
      <span>открыто: {{ openRate }} | прочитанно: {{ readRate }}</span>
    </div>
    <app-news
      v-for="item in news"
      :news="item"
      :key="item.id"
      :id="item.id"
      :title="item.title"
      :text="item.text"
      :is-open="item.isOpen"
      :wasRead="item.wasRead"
      @open-news="openRate++"
      @read-news="readNews"
    ></app-news>
  </div>
</template>

<script>
import AppNews from '@/AppNews'
export default {
  components: {
    AppNews
  },
  data () {
    return {
      openRate: 0,
      readRate: 0,
      now: new Date().toLocaleDateString(),
      news: [
        {
          id: 1,
          title: 'новость 1',
          text: 'Lorem ipsum dolor sit amet, consectetur adipisicing elit. Accusantium eveniet minus sapiente. Ad dicta explicabo omnis perferendis? Cupiditate, magni, odit?',
          isOpen: true,
          wasRead: false
        },
        {
          id: 2,
          title: 'новость 2',
          text: 'Lorem ipsum dolor sit amet, consectetur adipisicing elit. Accusantium eveniet minus sapiente. Ad dicta explicabo omnis perferendis? Cupiditate, magni, odit?',
          isOpen: false,
          wasRead: false
        }
      ]
    }
  },
  methods: {
    readNews (id) {
      const idx = this.news.findIndex(news => news.id === id)
      this.news[idx].wasRead = !this.news[idx].wasRead
      if (this.news[idx].wasRead) {
        this.readRate++
      } else {
        this.readRate--
      }
    }
  }

}
</script>

<style>

</style>
