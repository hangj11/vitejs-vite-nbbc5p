<!-- js  -->
<script setup>
import { ref } from 'vue';
/**
  todo item
  key: text, done
  item.text or item['text']
  {
    text: string
    done: boolean(true/false)
  }
*/
const inputValue = ref('');
const todoList = ref([
  { text: 'vue', done: false },
  { text: 'react', done: false },
  { text: 'vercel', done: false },
]);

const handleClickButton = () => {
  todoList.value.push(inputValue.value);
};

const handleChange = (event) => {
  const nextValue = event.target.value;
  inputValue.value = nextValue;
};

const handleClickDeleteButton = (index) => {
  todoList.value.splice(index, 1);
};
</script>

<!-- html -->
<template>
  <p>{{ todoList }}</p>
  <h4>TODO LIST</h4>

  <input v-model="inputValue" />
  <!-- <input :value="inputValue" @change="handleChange" /> -->

  <button @click="handleClickButton">확인</button>

  <div class="todo-item" v-for="(item, index) in todoList">
    <input type="checkbox" v-model="item.done" />
    <span :class="{ 'done-item': item.done }">{{ item.text }}</span>
    <!-- item.done ? <span class="done-item"... : 
                      <span class="" ...
    -->
    <div>
      <!-- <button>수정</button> -->
      <button @click="handleClickDeleteButton(index)">삭제</button>
    </div>
  </div>
</template>

<!-- css -->
<style scoped>
.todo-item {
  width: 100%;
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
  border: 1px solid gray;
}

.done-item {
  text-decoration: line-through;
}
</style>


<!-- <style scoped>
.todo-item {
  width: 100%;
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
  border: 1px solid gray;
  margin-top: 10px;  
  padding: 5px;  
}
</style> -->

<!-- js 동적으로 제어하는 부분  -->
<!-- <script setup>
import {ref} from 'vue'; 

const inputValue = ref("");
const todoList= ref([])

console.log(inputValue.value);

const handleclickValue =() => {
  todoList.value.push(inputValue.value);
  console.log()
};

const handleChange = (event) => {
  const nextValue =event.target.value;
  inputValue.value = nextValue
};


</script>

--html 영역--
<template>
<h1>TODOLIST </h1>

<input v-model="inputValue"/>

<p>{{ inputValue }}</p>

<button @click="hanleclickValue">확인</button>
<div class="todo-item">
  <div>코드짜기</div>
  <button>삭제</button>
</div>
</template>

-- css영역 -->
<!-- <style scoped>
.todo-item {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: conter;
  border:1px solid gray;
}

</style>  -->

<!-- <div> count : {{ count }}</div>
<button @click="증가">+</button>
<button @click="감소">-</button> -->


<!-- const count = ref (0);
const 증가 = () => {
count.value = count.value+1
}  
const 감소 = () => {
count.value = count.value-1
} -->

<!-- <input:value="inputValue"
@change="handleChange"/> -->