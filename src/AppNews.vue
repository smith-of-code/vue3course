<template>
  <div class="card">
    <h3>{{ title }}</h3>
    <app-button @action="open">
      {{isNewsOpen?'закрыть':'открыть'}}
    </app-button>
    <div v-show="isNewsOpen">
      <hr>
      <p>{{text}}</p>
      <app-button @action="read"
                  :color="isNewsRead?'danger':'primary'"
      >
        {{isNewsRead?'не прочитанно':'прочитанно'}}
      </app-button>
    </div>
  </div>
</template>

<script>
import AppButton from '@/AppButton'

export default {
  name: 'AppNews',
  components: { AppButton },
  props: {
    id: {
      type: Number,
      required: true,
      validator (value) {
        return !!value
      }
    },
    title: {
      type: String,
      required: true
    },
    text: {
      type: String,
      required: true
    },
    isOpen: {
      type: Boolean,
      required: false,
      default: false
    },
    wasRead: {
      type: Boolean,
      required: true
    }
  },
  emits: {
    'open-news': null,
    'read-news' (id) {
      if (id) {
        return true
      }
      console.warn('нет параметра для emit read-news')
      return false
    }
  },
  data () {
    return {
      isNewsOpen: this.isOpen,
      isNewsRead: this.wasRead
    }
  },
  methods: {
    open () {
      this.isNewsOpen = !this.isNewsOpen
      if (this.isNewsOpen) {
        this.$emit('open-news')
      }
    },
    read () {
      this.isNewsRead = !this.isNewsRead
      this.$emit('read-news', this.id)
      if (this.isNewsRead) {
        this.isNewsOpen = false
      }
    }
  }
}
</script>

<style scoped>

</style>
