<template>
  <div id="itemListWrapper">
    <h2>{{ label }}</h2> 
      <ol>
        <item v-for="(item, index) in items" :data="items" @change="selectItem" :key="item.itemDescription">
          {{item.itemDescription}} 
          <md-checkbox class="md-primary" type="checkbox" id="checkbox" @change="filteredItems(index)" v-model="item.isSelected"></md-checkbox>
        </item>
      </ol>
  </div>
</template>

<script>
export default {
  name: 'ItemsList',

  data () {
    return { 
    }
  },

  props: {
    label: { type: String, required: true },
    items: { type: Array, required: true },
  },

  methods: {
    selectItem() {
      const selected = this.items.isSelected
      console.log(selected);
    }
   },
  
  computed: {
    selectedItems () {
      let isSelected = this.items.isSelected
      console.log(isSelected);
      return isSelected

    },  

    filteredItems () {
      let fItems = this.items.filter(item => item.isSelected);
      console.log(fItems);
      return fItems
    }
  },
}


</script>

<style scoped>

ul {
    margin: 0 auto;
    text-align: center;
}

li {
    color: green;
    display: inline-block;
    vertical-align: top;
}

#itemListWrapper {
  width: 100%;
  height: auto;
  border: 3px solid green;
  padding: 10px;
  margin: auto;
  margin-top: 20px;
}

</style>