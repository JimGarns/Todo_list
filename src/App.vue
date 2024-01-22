<template>
  <main>

    <div class="todo">

     <div class="todo__header">
       <div class="todo__title">
         <h1>To Do List</h1>
       </div>

       <div class="todo__field">
         <input v-model="inputData" @keyup.enter=addTask type="text">
         <button class = "todo__submit" @click = addTask>Go</button>
       </div>
     </div>

      <div class="todo__body">

        <ul>
          <li class = "liItem" v-for="item in inputArray">{{item}} <button @click = removeTask>X</button></li>
        </ul>

      </div>

    </div>

  </main>
</template>

<script setup>

import {ref} from "vue";

const inputData = ref('')
const inputArray = ref([])

const addTask = () => {

  if(inputData.value !== '') {
    inputArray.value.push(inputData.value)
  }
  else alert('Field cannot be empty.')

  inputData.value = ''
}

const removeTask = (event) => {
  event.target.closest("li").remove()
}


</script>

<style scoped lang="scss">

.todo {
  padding: 300px 0 0 0;

  &__field {
    padding-top: 50px;

    input {
      height: 30px;
      padding: 0 5px;
    }

    button {
      height: 30px;
    }

  }

  &__body {
    padding-left: 10px;
    margin-top: 10px;
    min-height: 300px;
    width: 100%;
    background: #222222;
  }

  li {
    display: flex;
    justify-content: space-between;
    margin-bottom: 10px;
  }

  ul {
    list-style: none;
    padding: 0;
  }
}


</style>
