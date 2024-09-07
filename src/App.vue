<!-- js -->
<script setup>
import { ref } from 'vue';

const inputValue = ref('');
const todoList = ref([
  { text: 'vue', done: false },
  { text: 'react', done: false },
  { text: 'vercel', done: false }
]);

const handleClickButton = () => {  
  if (inputValue.value.trim() !== '') {   
    todoList.value.push({ text: inputValue.value, done: false });
    inputValue.value = '';  
  }
};

const handleclickDeleteButton = (index) => {
  todoList.value.splice(index, 1);
};
</script>

<!-- html -->
<template>
  <h4>TODO LIST</h4>

  <input v-model="inputValue" placeholder="할 일을 입력하세요" /> 
  <p>{{ inputValue }}</p>

  <button @click="handleClickButton">확인</button> 

  <div v-for="(todo, index) in todoList" :key="index" class="todo-item">  
    <input type="checkbox" v-model="todo.done" />  
    <span :class="{ 'done-item': todo.done }">{{ todo.text }}</span>

    <button >수정</button>
    <button @click="handleclickDeleteButton(index)">삭제</button> 
  
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
  margin-top: 10px;  
  padding: 10px;
  font-size: 12px;
}

input {
  width: 100%;
  padding: 10px;
  font-size: 16px;
  border: 1px solid #ccc;
  border-radius: 4px;
  box-sizing: border-box;
}

button {
  padding: 6px 10px;
  font-size: 12px;
  border-radius: 2px;
  writing-mode: vertical-lr;
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