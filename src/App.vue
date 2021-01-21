<template>
  <div class="container pt-1">
   <div class="card">
    <h2>асинхронщина</h2>
     <app-button
       :color="active === 'one' ?'danger':'primary'"
       @action="active= 'one'"
     >one</app-button>
     <app-button
       :color="active === 'two' ?'danger':'primary'"
       @action="active= 'two'"
     >two</app-button>
   </div>
    <keep-alive>
      <component :is="componentName"></component>
    </keep-alive>
  </div>
</template>

<script>
import AppButton from '@/AppButton'
import AppTextOne from '@/AppTextOne'
import AppTextTwo from '@/AppTextTwo'
export default {
  components: {
    AppButton,
    AppTextOne,
    AppTextTwo
  },
  data () {
    return {
      active: 'one'
    }
  },
  methods: {

  },
  computed: {
    componentName () {
      return `app-text-${this.active}`
    }
  }

}
</script>

<style>

</style>
