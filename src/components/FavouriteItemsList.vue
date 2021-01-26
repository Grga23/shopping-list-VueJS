<template>
  <div>
    <h2>{{ label }}</h2> 
    <ol v-for="item in items" :key="item">
      <br />
      <li id="regularItemsList">{{item.itemDescription}} X {{item.quantity}}; 
        <input type="checkbox" id="checkbox" v-model="checked">
        <label for="checkbox">{{ checked }}</label>
      </li>
    </ol>

    <ul v-for="item in items" :key="item">
      <li v-show="item.isSelected">
      {{item.itemDescription}} IS 
      {{item.isSelected}}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'ItemsList',

  props: {
    label: { type: String, required: true },
    items: { type: Array, required: true },
  },
  
  computed: {
    filteredItems () {
      let fItems = this.items.filter(item => item.isSelected);
      return fItems
    }
  },
}


</script>

<style scoped>

li {
  color: green
}
</style>