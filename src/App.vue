<script setup>
import StockCard from "./components/StockCard.vue"
import SearchBar from "./components/SearchBar.vue"

function efe(value) {
  alert(value);
}
</script>

<template>

<v-container class="ma-0 pa-0">
  <v-row>
    <v-col cols="6">
      <v-container class="d-flex flex-row flex-wrap">
        <SearchBar @keyTyped="efe"/>

        <StockCard firmName="Koç Holding" firmValue="3.738.150"/>
        <StockCard firmName="Sabancı Holding" firmValue="934.333"/>
        <StockCard firmName="Eczacıbaşı Holding" firmValue="1.524.120"/>
        <StockCard firmName="Ağaoğlu Holding" firmValue="3.234.567"/>
      </v-container>
    </v-col>
    <v-col>
      <v-container class="d-flex flex-row flex-wrap">
        SEPET BURADA OLACAK
      </v-container>
    </v-col>
  </v-row>
</v-container>
     

</template>