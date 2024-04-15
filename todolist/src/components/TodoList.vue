<script setup>
import { ref } from 'vue'
//string 
const newTask = ref('')
//array
const tasks = ref([])
//trim() để loại bỏ các khoảng trắng ở đầu và cuối chuỗi
// ở đây biến newtask sẽ lưu giá trị tạm thời , rồi sau đó push lên cho thằng tasks để lưu , khi push xong thì sẽ refresh lại thành string rỗng ''
const addTask =()=>{
	 if( newTask.value.trim()!== '' ){
		tasks.value.push(newTask.value)
		newTask.value = ''
	 } 
}
//slice(index,1) sẽ xóa đi ( 1 ) phần từ ở vị trí ( index ) ở trong mảng 
const removeTask =(index)=>{
	tasks.value.splice(index,1)
} 
</script>
<template>
	<div class="todo-app">
		<div class="task-input">
			<input v-model="newTask" @keyup.enter="addTask" placeholder="Add new task">
			<button @click="addTask"> Add</button>
		</div>
		<ul class="task-list">
			<li v-for="(task,index) in tasks" :key="index" class ="task-item">
				{{ task }}
			</li>
			<button @click="removeTask(index)" class="remove-button"> Remove </button>
		</ul>
	</div> 
</template>
<style scoped>
.todo-app {
	max-width: 400px;
	margin: 50px auto;
	padding: 20px;
	border: 1px solid #ccc;
	border-radius: 8px;
	box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  }
  
  .app-title {
	font-size: 24px;
	margin-bottom: 20px;
	text-align: center;
	color: #333;
  }
  
  .task-input {
	display: flex;
	gap: 10px;
  }
  
  input {
	flex: 1;
	padding: 8px;
	font-size: 14px;
  }
  
  button {
	padding: 8px 12px;
	font-size: 14px;
	background-color: #4caf50;
	color: #fff;
	border: none;
	border-radius: 4px;
	cursor: pointer;
  }
  
  button:hover {
	background-color: #45a049;
  }
  
  .task-list {
	list-style: none;
	padding: 0;
  }
  
  .task-item {
	display: flex;
	justify-content: space-between;
	align-items: center;
	padding: 10px;
	margin: 8px 0;
	background-color: #ece4e4;
	border: 1px solid #ddd;
	border-radius: 4px;
  }
  
  .remove-button {
	padding: 6px 10px;
	font-size: 12px;
	background-color: #e74c3c;
	color: #fff;
	border: none;
	border-radius: 3px;
	cursor: pointer;
  }
  
  .remove-button:hover {
	background-color: #c0392b;
  }
</style>