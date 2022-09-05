---
layout: page
title: Todo
permalink: /todo/
---

# Todo List

<form id="todo-form">
<input type="text" placeholder="Todo Name" id="todo-name">
<input type="submit" value="Submit">
</form>

<ul id="todo-list-ul">
</ul>

<script>
document.getElementById("todo-form").onsubmit = function (event) {
  event.preventDefault();
  const name = document.getElementById("todo-name").value;
  document.getElementById("todo-name").value = "";
  const todoItem = document.createElement("li");
  const todoText = document.createTextNode(name);
  todoItem.appendChild(todoText);
  todoItem.classList.add("todo-item");
  todoItem.onclick = function () {
    document.getElementById("todo-list-ul").removeChild(todoItem);
  }
  document.getElementById("todo-list-ul").appendChild(todoItem);
}
</script>

<style>
.todo-item:hover {
  text-decoration: line-through;
  cursor: pointer;
}
</style>