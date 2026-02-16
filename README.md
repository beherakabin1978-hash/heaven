<!DOCTYPE html>
<html>
<head>
    <title>Heaven - Family App</title>
    <style>
        body {
            font-family: Arial;
            text-align: center;
            background: linear-gradient(to right, #4e73df, #1cc88a);
            color: white;
        }
        .card {
            background: rgba(255,255,255,0.2);
            padding: 20px;
            margin: 20px;
            border-radius: 12px;
        }
        input {
            padding: 8px;
            border-radius: 5px;
            border: none;
        }
        button {
            padding: 8px 15px;
            border: none;
            border-radius: 8px;
            cursor: pointer;
            font-weight: bold;
        }
        ul {
            list-style: none;
            padding: 0;
        }
        li {
            margin: 10px 0;
        }
    </style>
</head>
<body>

<h1>🌤 Welcome to Heaven</h1>
<p>Your Private Family Interaction App</p>

<div class="card">
    <h2>📅 Family Tasks</h2>
    <input type="text" id="taskInput" placeholder="Enter task">
    <button onclick="addTask()">Add</button>
    <ul id="taskList"></ul>
</div>

<script>
let tasks = JSON.parse(localStorage.getItem("tasks")) || [];
let taskList = document.getElementById("taskList");

function displayTasks() {
    taskList.innerHTML = "";
    tasks.forEach((task, index) => {
        let li = document.createElement("li");
        li.textContent = task + " ";

        let deleteBtn = document.createElement("button");
        deleteBtn.textContent = "❌";
        deleteBtn.onclick = function() {
            deleteTask(index);
        };

        li.appendChild(deleteBtn);
        taskList.appendChild(li);
    });
}

function addTask() {
    let taskInput = document.getElementById("taskInput");
    let task = taskInput.value;
    if (task === "") return;

    tasks.push(task);
    localStorage.setItem("tasks", JSON.stringify(tasks));
    taskInput.value = "";
    displayTasks();
}

function deleteTask(index) {
    tasks.splice(index, 1);
    localStorage.setItem("tasks", JSON.stringify(tasks));
    displayTasks();
}

displayTasks();
</script>

</body>
</html>
