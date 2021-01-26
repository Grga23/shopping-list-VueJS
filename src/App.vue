<template>
  <div md-layout small id="app">
    <!-- <favourite-items-list label="Favourite Items" :items="favouriteItems"> --> 
    <stepper md-layout-item
          label="Stepper"/>  
          
    <items-list md-layout-item 
          label="REGULAR ITEMS" 
          :items="regularItems"/>  

    <monthly-items-list md-layout-item 
          label="Monthly Items" 
          :items="monthlyItems" />

    <add-item md-layout-item 
          label="Add Items" 
          @inputItem="addItem"/>  

    <shopping-list md-layout-item 
          label="Shopping List" 
          :items="addedItems" 
          :isRegularItem="isRegularItem" 
          @removeAddedItem="removeAddedItem"
          @removeRegularItem="removeRegularItem"/>
  </div>
</template>

<script>
//import FavouriteItemsList from './components/FavouriteItemsList.vue'
import Vue from 'vue'
import VueMaterial from 'vue-material'
import 'vue-material/dist/vue-material.min.css'
import Stepper from './components/Stepper.vue'
import AddItem from './components/AddItem.vue'
import ItemsList from './components/ItemsList.vue'
import MonthlyItemsList from './components/MonthlyItemsList.vue'
import ShoppingList from './components/ShoppingList.vue'

Vue.use(VueMaterial)


export default {
  name: 'App',
  components: {
    //FavouriteItemsList,
    Stepper,
    AddItem,
    ItemsList,
    MonthlyItemsList,
    ShoppingList
  },
  data () {
    return { 
      regularItems: [
        {
          itemDescription: 'Palčke z arašidi',
          category: 'Snacks',
          quantity: 1,
          isSelected: false
        },
        {
          itemDescription: 'Bobi Palcke',
          category: 'Snacks',
          quantity: 1,
          isSelected: false

        },        
        {
          itemDescription: 'Piškoti za zajtrk',
          category: 'Snacks',
          quantity: 1,
          isSelected: false

        },        
        {
          itemDescription: 'Limone',
          category: 'Fruits & Vegetables',
          quantity: 2,
          isSelected: false

        },        
        {
          itemDescription: 'Pomaranče',
          category: 'Fruits & Vegetables',
          quantity: 2,
          isSelected: false

        }, 
        {
          itemDescription: 'Banane',
          category: 'Fruits & Vegetables',
          quantity: 1,
          isSelected: false

        },             
        {
          itemDescription: 'Riževo mleko',
          category: 'Dairy products',
          quantity: 2,
          isSelected: false

        },        
        {
          itemDescription: 'Avokado',
          category: 'Fruits & Vegetables',
          quantity: 1,
          isSelected: false

        },       
        {
          itemDescription: 'Mango',
          category: 'Fruits & Vegetables',
          quantity: 1,
          isSelected: false
        },
        {
          itemDescription: 'WC Papir',
          category: 'Hygiene',
          quantity: 1,
          isSelected: false
        },
        {
          itemDescription: 'Plenice',
          category: 'Hygiene',
          quantity: 1,
          isSelected: false
        },
        {
          itemDescription: 'Puranja prsa, salama',
          category: 'Meat & Deli',
          quantity: 2,
          isSelected: false
        },
        {
          itemDescription: 'Suha salama',
          category: 'Meat & Deli',
          quantity: 1,
          isSelected: false
        },
        {
          itemDescription: 'Humus',
          category: 'Meat & Deli',
          quantity: 2,
          isSelected: false
        },
        {
          itemDescription: 'Zdenka sir',
          category: 'Meat & Deli',
          quantity: 1,
          isSelected: false
        },
        {
          itemDescription: 'Sir',
          category: 'Dairy products',
          quantity: 1,
          isSelected: false
        },
        {
          itemDescription: 'Pašteta',
          category: 'Meat & Deli',
          quantity: 1,
          isSelected: false
        },
        {
          itemDescription: 'Puding',
          category: 'Dairy products',
          quantity: 2,
          isSelected: false
        }
      ],
      monthlyItems: [
        {
          itemDescription: 'Kochschkolade',
          category: 'Dairy products',
          quantity: 1,
          isSelected: true
        },
        {
          itemDescription: 'Kava',
          category: 'Beverages',
          quantity: 1,
          isSelected: true
        },
        {
          itemDescription: 'Kakav',
          category: 'Dry foods',
          quantity: 1,
          isSelected: false
        },
        {
          itemDescription: 'Cet',
          category: 'Hygiene',
          quantity: 1,
          isSelected: false
        },
        {
          itemDescription: 'Pivo',
          category: 'Beverages',
          quantity: 1,
          isSelected: false
        },
        {
          itemDescription: 'Makaroni',
          category: 'Dry foods',
          quantity: 1,
          isSelected: false
        },
        {
          itemDescription: 'Maslo',
          category: 'Dairy products',
          quantity: 1,
          isSelected: false
        },
        {
          itemDescription: 'Gres',
          category: 'Dry foods',
          quantity: 1,
          isSelected: false
        },
        {
          itemDescription: 'Šumečke',
          category: 'Beverages',
          quantity: 1,
          isSelected: false
        },
        {
          itemDescription: 'Bonboni za v avto',
          category: 'Snacks',
          quantity: 1,
          isSelected: false
        },
        {
          itemDescription: 'Krompir',
          category: 'Fruits & Vegetables',
          quantity: 1,
          isSelected: false
        },
        {
          itemDescription: 'Koruza v konzervi',
          category: 'Fruits & Vegetables',
          quantity: 1,
          isSelected: false
        },
        {
          itemDescription: 'Robčki',
          category: 'Hygiene',
          quantity: 1,
          isSelected: false
        },
        {
          itemDescription: '',
          category: '',
          quantity: 1,
          isSelected: false
        },



      ],
      addedItems: [],
      selectedRegularItems: [],
      selectedMonthlyItems: [],
      inputItem: '',
      inputItemQ: '',
    }
  },
    // WHEN YOU NEED TO CHANGE DATA USE  METHODS ! When you need to change PRESENTATION OF THE DATA, USE COMPUTED
  methods: {
    addItem (item) {
      this.addedItems.push(item);
      console.log('Added ' + item.itemDescription + item.quantity);
      console.log(this.addedItems)
    },

    removeAddedItem(index) {
      console.log(index);
      this.addedItems.splice(index, 1);
    },

    removeRegularItem(index) {
      console.log(index);
      this.isRegularItem.splice(index, 1);
    },

    selectRegularItem () {
      // select it 
      // add it to seelecterRegularItems array
      // make a computed data point

    },

    selectedMonthlyItem () {
      // select it 
      // add it to seelecterRegularItems array
      // make a computed data point

    },
  },


  computed: {
/*     isSelectedRegularItem () {
      let selectedItems = this.selectedRegularItems.filter (item => item.isSelected);
      return selectedItems;
    }, */

    isRegularItem () {
      let isRegularItem = this.regularItems.filter (item => item.isSelected);
      console.log(isRegularItem);
      return isRegularItem;

    }
    // totalIncome () {
    //   let totalIncome = 0; 
    //   this.incomes.forEach(obj => totalIncome += obj.value); // Za vsak obj v arrayu 'costs' ==> naredi totalCosts += obj.value
    //   return totalIncome;
    //  }
  },
}


</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: left;
  color: #2c3e50;
  margin: 8px;
  border: 3px solid green;
  padding: 20px;
}

</style>


<!-- 
1. ShoppingList ==> final list component
sem not bos feedal vse isSelected 

1. List itemov ki jih kupujes 
2. Na select - ti ga remova / + doda na novo komponento
> 1 Array ==> gre v dva computed propa (na App nivoju)
> 1 od teh filtrira po is Selected / drug pa po false. 
> in pol posljes vsakega v svojo komponento 


--> 