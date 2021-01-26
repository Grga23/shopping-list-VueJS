<template>
  <div id="monthlyitemslistwrapper">
    <h2>{{ label }}</h2> 
    <md-list>
      <ul v-for="item in items" :key="item">
        <md-list-item v-show="item.isSelected">
        {{item.itemDescription}} IS 
        {{item.isSelected}}
        </md-list-item>
      </ul>
    </md-list>

  </div>
</template>

<script>
export default {
  name: 'MonthlyItemsList',
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

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
li {
  color: green;
}

#monthlyitemslistwrapper {
  width: 100%;
  height: auto;
  border: 3px solid green;
  padding: 10px;
  margin: auto;
  margin-top: 20px;
}

</style>
