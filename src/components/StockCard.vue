<script setup>
    defineProps({
        firmName: String,
        firmValue: String
    })
</script>
 
<template>

    <v-card 
    width="100%"
    variant="elevated"
    color="primary"
    class="my-4 cursor-pointer">

        <v-card-title> {{ firmName }} </v-card-title>
        <v-card-subtitle>  </v-card-subtitle>

        <v-card-text> $ {{ firmValue }} </v-card-text>
    
    </v-card>


</template>