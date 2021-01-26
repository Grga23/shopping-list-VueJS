<template>
  <div id="shoppinglistwrapper">
    <h1>{{ label }}</h1> 
    <div>
      <h2> Added Items </h2> 
      <ul v-for="(item, index) in items" :key="index">
        <div>
          <li class="addeditems">
          {{item.itemDescription}} X
          {{item.quantity}} AT 
          {{item.category}}
          <br>
          <md-button class="md-accent" ref="removeButton" @click="removeAddedItem(index)">Remove item</md-button>
          </li>
        </div>
      </ul>
    </div>
    <div>
      <h2> Selected Regular Items </h2>
        <ul v-for="(regItem, index) in isRegularItem" :key="index">
          <li>
            {{regItem.itemDescription}} X
            {{regItem.quantity}} 
            <br>
            <md-button class="md-accent" ref="removeRegularButton" @click="removeRegularItem(index)">Remove item</md-button>
            <md-button class="md-accent" @click="removeRegularItem1()">Remove item</md-button>
            <md-checkbox class="md-primary" type="checkbox" id="checkbox" @change="filteredItems(index)" v-model="regItem.isSelected"></md-checkbox>
          </li>
        </ul>
    </div>
      <div>
      <h2> V-IF Regular items test </h2>
      <p v-if="inStock">In Stock</p>
      <p v-else>Out of Stock</p>

      <md-button class="md-accent" @click="changeState()">Change STATE</md-button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ShoppingList',
  props: {
    label: { type: String, required: true },
    items: { type: Array, required: true },
    isRegularItem: { type: Array, required: true},
  },

    data () {
    return { 
      inStock: false
    }
  },

  methods: {
    changeState() {
      console.log("Change state clicked")
      this.inStock = !this.inStock;

    },
    removeAddedItem (index) {
      this.$emit("removeAddedItem", index)
      console.log('removeAddedItem emitted')
    },

    removeRegularItem (index) {
      this.$emit("removeRegularItem", index)
      console.log('removeRegularItem emitted')    
      },
    removeRegularItem1 () {
      this.isRegularItem.isSelected = !this.isRegularItem.isSelected 

    },  
   },
}


</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->

<style scoped>

ul {}

li {
    color: green;
}

.removeItem {
  background-color: red;
  color: white;
  display: inline-grid;

}

.addeditems {
  border-radius: 5%;
  border: 1px, solid, blue;
  background-color: lightskyblue;
  padding: 5px;
  margin: auto;
  display: -moz-inline-grid;

}

#shoppinglistwrapper {
  width: 100%;
  height: auto%;
  border: 3px solid green;
  padding: 10px;
  margin: auto;
  margin-top: 20px;
}

</style>