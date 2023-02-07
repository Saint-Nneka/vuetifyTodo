<template>
  <v-container class="d-flex justify-center align-center">
    <v-card width="300" max-width="100%" flat>
      <v-card-title class="text-center">Add Todo</v-card-title>
      <v-toolbar class= "rounded-lg px-2" color="pink">
        <v-text-field 
        label="Add Todo" 
        density="compact"
        variant="underlined"
         prepend-inner-icon="mdi-plus-circle"
         clearable
         hide-details
         v-model="newTodo"
         @keypress.enter="addTodo"
         />
         <v-btn class="text-capitalize bg-pink-lighten-3 ml-2 text-body-2" 
         height="44" 
         flatgg
         @click="addTodo">
         Add Todo
         </v-btn>
      </v-toolbar>

  <v-card-text class="px-1">
    <v-slide-y-transition group tag="v-list">
      <v-card 
      v-for= "(todo, i) in todos"
      :key = "i"
      elevation="2"
      class="rounded-lg mb-4"
      >
        <v-card-title
        class="d-flex
        justify-space-between
        align-center"
        >
        {{todo}}
          <v-btn 
          @click= "deleteTodo(i)"
          icon
          size="small"
          flat
          >
            <v-icon color="red">
              mdi-trash-can-outline
            </v-icon>
          </v-btn>
        </v-card-title>
      </v-card>
    </v-slide-y-transition>
    
  </v-card-text>
    </v-card>
  </v-container>
</template>

<script setup>
import { ref } from "vue";

const todos = ref([]);
const newTodo = ref("");

const addTodo = () => {
  if(newTodo.value=='') return
  todos.value.push(newTodo.value);
  newTodo.value = "";
};

const deleteTodo = (i) => {
  todos.value.splice(i, 1);
};
</script>

<style>

</style>