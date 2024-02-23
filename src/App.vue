<script>
import StockCard from "./components/StockCard.vue"
import SearchBar from "./components/SearchBar.vue"
import StockBasket from "./components/StockBasket.vue";
import HeaderBar from "./components/headercomponents/HeaderBar.vue";

export default {
    components: { 
      StockBasket,
      StockCard,
      HeaderBar,
      SearchBar
    },
    
    data() {
        return {
            stockList: [
                { "name": "Koç Holding", "value": "3.738.150" },
                { "name": "Sabancı Holding", "value": "934.333" },
                { "name": "Eczacıbaşı Holding", "value": "1.524.120" },
                { "name": "Ağaoğlu Holding", "value": "3.234.567" }
            ],
            filteredList: [
                { "name": "Koç Holding", "value": "3.738.150" },
                { "name": "Sabancı Holding", "value": "934.333" },
                { "name": "Eczacıbaşı Holding", "value": "1.524.120" },
                { "name": "Ağaoğlu Holding", "value": "3.234.567" }
            ]
        };
    },
    methods: {
        filterCards(value) {
            if (value.length > 2)
                this.filteredList = this.stockList.filter(stock => stock.name.toLowerCase().includes(value.toLowerCase()));
            else
                this.filteredList = this.stockList;
        },
        allowDrop(ev) {
          if(ev && ev.preventDefault) ev.preventDefault();
        },
        drag(ev) {
          console.log(JSON.stringify(ev.target.id));
          ev.dataTransfer.setData("stockId", ev.target.id);
        },
        drop(ev) {
          if(ev.preventDefault) ev.preventDefault();
          console.log(ev);
          var data = ev.dataTransfer.getData("stockId");to
          //ev.target.appendChild(document.getElementById(data));
          this.filteredList = this.filteredList.filter(stock => stock.name != data);
        }
    }
}
</script>

<template>

<v-container class="ma-0 pa-0 mx-auto" style="background:white">
  <v-row>
    <v-col cols="12">
      <v-container>
        <HeaderBar></HeaderBar>
      </v-container>
    </v-col>
  </v-row>
  
  <v-row>
    <v-col cols="6">
      <v-container class="d-flex flex-row flex-wrap">

      <SearchBar
      @keyTyped="filterCards"
      />

      <StockCard
      v-for="stock in filteredList"
      :key="stock.name"
      :id="stock.name"
      :firmName="stock.name"
      :firmValue="stock.value"
      draggable="true"
      v-on:dragstart="drag($event)"
      />
        
      </v-container>
    </v-col>
    <v-col cols="6">
      <v-container>
        <StockBasket v-on:drop="drop($event)" v-on:dragover="allowDrop($event)"></StockBasket>
      </v-container>
    </v-col>
  </v-row>
</v-container>
     

</template>