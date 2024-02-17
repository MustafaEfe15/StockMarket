<script setup>
    defineProps({
        firmName: String,
        firmValue: String
    })

    function drag(event) {
          var target = event.target;
          console.log(parseFloat(target.getAttribute('data-x') || 0));
          console.log(parseFloat(target.getAttribute('data-y') || 0));
        }
</script>
 
<template>

    <v-card 
    width="100%"
    variant="elevated"
    color="primary"
    class="ma-4 cursor-pointer"
    >
        <v-card-title> {{ firmName }} </v-card-title>
        <v-card-subtitle>  </v-card-subtitle>

        <v-card-text> $ {{ firmValue }} </v-card-text>
    </v-card>


</template>