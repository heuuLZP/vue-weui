<template>
  <h2>this is button page</h2>
  <child :title="title"></child>
</template>
<script>
import child from './child.vue';
export default {
  data(){
      return {
        title: '这是从父组件来的'
        }
  },
  components: { child }
}
</script>
<style>
</style>
