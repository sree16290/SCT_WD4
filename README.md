# SCT_WD4
To do web App
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>To-Do List App</title>

<style>

body{
font-family: Arial;
background: linear-gradient(135deg,#74ebd5,#ACB6E5);
display:flex;
justify-content:center;
align-items:center;
height:100vh;
}

.container{
background:white;
padding:25px;
border-radius:10px;
width:350px;
box-shadow:0 10px 20px rgba(0,0,0,0.2);
}

h2{
text-align:center;
}

input,button{
padding:8px;
margin:5px;
}

button{
cursor:pointer;
background:#4CAF50;
color:white;
border:none;
border-radius:5px;
}

ul{
list-style:none;
padding:0;
}

li{
background:#f2f2f2;
margin:8px 0;
padding:10px;
border-radius:5px;
display:flex;
flex-direction:column;
}

.completed{
text-decoration: line-through;
color:gray;
}

.task-actions button{
margin-right:5px;
background:#2196F3;
}

.delete{
background:#f44336;
}

</style>
</head>

<body>

<div class="container">

<h2>To-Do List</h2>

<input type="text" id="taskInput" placeholder="Enter task">
<input type="datetime-local" id="taskTime">
<button onclick="addTask()">Add</button>

<ul id="taskList"></ul>

</div>

<script>

function addTask(){

let taskText = document.getElementById("taskInput").value;
let taskTime = document.getElementById("taskTime").value;

if(taskText === ""){
alert("Enter a task");
return;
}

let li = document.createElement("li");

let taskContent = document.createElement("span");
taskContent.innerText = taskText + " (" + taskTime + ")";

li.appendChild(taskContent);

let actions = document.createElement("div");
actions.className = "task-actions";

let completeBtn = document.createElement("button");
completeBtn.innerText = "Complete";
completeBtn.onclick = function(){
li.classList.toggle("completed");
};

let editBtn = document.createElement("button");
editBtn.innerText = "Edit";
editBtn.onclick = function(){
let newTask = prompt("Edit task:", taskText);
if(newTask){
taskContent.innerText = newTask + " (" + taskTime + ")";
}
};

let deleteBtn = document.createElement("button");
deleteBtn.innerText = "Delete";
deleteBtn.className="delete";
deleteBtn.onclick = function(){
li.remove();
};

actions.appendChild(completeBtn);
actions.appendChild(editBtn);
actions.appendChild(deleteBtn);

li.appendChild(actions);

document.getElementById("taskList").appendChild(li);

document.getElementById("taskInput").value="";
document.getElementById("taskTime").value="";

}

