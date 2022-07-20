<template>
  <div id="app">
    <app-number @itemAdded="logItem"></app-number>
    <p class="result">Kết quả: {{arr}}</p>
  </div>
</template>

<script>
import createNumber from './components/createNumber.vue';
export default {

  data: function() {
    return {
      arr: '',
    }
  },

  components: {
    appNumber : createNumber
  },

  methods: {
    logItem(item) {
      if(typeof item == 'object') {
        this.arr = `${item}`
      }else {
        this.arr = item
      }
    }
  }
}
</script>

<style>
  .result {
    border: 1px dashed blue;
    width: 450px;
    padding: 20px;
    margin: auto;
  }
</style>
