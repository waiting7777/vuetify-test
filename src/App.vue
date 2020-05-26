<template>
  <div class="container">
    <div>Time diff: {{ diff }} ms</div>
    <div v-for="t in test" :key="t.id">
      <!-- <v-checkbox v-model="t.value"></v-checkbox> -->
      <!-- <v-simple-checkbox v-model="t.value" :ripple="false"></v-simple-checkbox> -->
      <input type="checkbox" v-model="t.value" />
    </div>
  </div>
</template>

<script>
import { range } from 'lodash'
export default {
  name: 'App',
  data() {
    return {
      test: range(10).map(v => { return { id: v, value: false }}),
      create: 0,
      mount: 0,
      diff: 0
    }
  },
  created() {
    this.create = new Date().getTime()
  },
  mounted() {
    this.mount = new Date().getTime()
    this.diff = this.mount - this.create
  }
};
</script>
