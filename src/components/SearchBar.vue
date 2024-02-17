<script setup>
let searchValue = ""
const emit = defineEmits(['keyTyped'])

function onchange() {
    console.log(searchValue);
    if(searchValue.length > 1) emit("keyTyped", searchValue);
}
</script>

<template>
    <v-container>
        <v-text-field
        v-model="searchValue"
        label="Search"
        prepend-inner-icon="mdi-magnify"
        single-line
        variant="outlined"
        v-on:update:model-value="onchange"
        hide-details
      ></v-text-field>
    </v-container>
</template>