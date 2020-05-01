<template>
  <div>
    <home></home>
  </div>
</template>


<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import Home from './Home.vue'
@Component({
  components: {
     Home
  }
})
export default class App extends Vue {}
</script>


<style lang="stylus" scope>

</style>