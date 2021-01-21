<template>
  <div class="container pt-1">
   <div class="card">Slots</div>
    <app-block>
      <template #content>
        <p>Lorem ipsum dolor sit amet.</p>
      </template>
      <template v-slot:header>
        <h3>голова</h3>
      </template>

    </app-block>
  </div>
</template>

<script>
import AppBlock from '@/AppBlock'
export default {
  components: {
    AppBlock
  },
  data () {
    return {

    }
  },
  methods: {

  }

}
</script>

<style>

</style>
