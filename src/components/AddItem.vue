<template>
  <div id="additemwrapper">
    <h2>{{ label }}</h2>
    <div class="">
      <md-field>
        <md-input class="input" v-model="inputItem" type="text" placeholder="Which item to buy?" ref="itemDescription"></md-input>
      </md-field>  
    </div>
      <md-field>
        <md-input class="input" v-model.number="inputItemQ" type="number" placeholder="How many/much?" ></md-input>
      </md-field>
      <div class="md-layout md-gutter">
        <div class="md-layout-item">
          <md-field>
            <label> Choose category</label>
            <md-select v-model="inputCategory" id="category" @keypress.enter="addItem">
              <md-option value="Snacks">Snacks</md-option>
              <md-option value="Fruits & Vegetables">Fruits & Vegetables</md-option>
              <md-option value="Dairy products">Dairy products</md-option>
              <md-option value="Hygiene">Hygiene</md-option>
              <md-option value="Meat & Deli">Meat & Deli</md-option>
              <md-option value="Beverages">Beverages</md-option>
              <md-option value="Dry foods">Dry foods</md-option>
            </md-select>
          </md-field> 
        </div>
      </div>
      <div id="additembutton">
          <md-button class="additem md-primary" @click="addItem">Add item</md-button>
      </div>
      <div>
        <img id="addtocart" :src="image" @click="addItem" >
      </div>

  </div>
</template>

<script>
export default {
  name: 'AddItem',

    data () {
    return { 
      addedItems: [],
      inputItem: '',
      inputCategory: '',
      inputItemQ: '',
      image: '/assets/addtocart.png',
    }
  },

  props: {
    label: { type: String, required: true },
    items: { type: Array, required: true },
  },

  methods: {
    addItem() {
      const itemObject = { itemDescription: this.inputItem, category: this.inputCategory, quantity: this.inputItemQ }
      this.$emit("inputItem", itemObject)
      this.inputItem = '';
      this.inputItemQ = ''
      this.inputCategory = null;
      this.$refs.itemDescription.focus();
    },
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

#additemwrapper {
  width: 100%;
  height: auto%;
  border: 3px solid green;
  padding: 10px;
  margin: 0px;
}

#additembutton {
  width: 100%;
  height: 100%;
  display: inline-grid;

}

#addtocart {
  display: block;
  width: 50px;
  height: 50px;
  margin: auto;
  padding: 8px;
  text-align: center;

}

.additem {

}

.input {
  color: lightseagreen;
}

.md-button {
  height: 100%
}

@media only screen and (min-width: 768px) {
  #additembutton {
    height: 100px;
    border: 2px solid green;
  }

  .md-button {
    font-size: large;
  }
}

</style>