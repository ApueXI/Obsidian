---
Created: 2025-07-11T08:53
---
```JavaScript
import React, { use, useState } from "react";

function TodoList() {
  const [tasks, setTasks] = useState(["Eat", "Sleep", "Game"]);
  const [newTasks, setNewTasks] = useState("");

  function handleInputChange(params) {
    setNewTasks(params.target.value);
  }
  function addTask() {
    if (newTasks.trim() !== "") {
      setTasks((prevTasks) => [...prevTasks, newTasks]);
      setNewTasks("");
    }
  }
  function deleteTask(index) {
    const updatedTask = tasks.filter((_, i) => {
      return i !== index;
    });

    setTasks(updatedTask);
  }

  function moveTaskUp(index) {
    if (index > 0) {
      const updatedTask = [...tasks];
      [updatedTask[index], updatedTask[index - 1]] = [
        updatedTask[index - 1],
        updatedTask[index],
      ];
      setTasks(updatedTask);
    }
  }

  function moveTaskDown(index) {
    if (index < tasks.length - 1) {
      const updatedTask = [...tasks];
      [updatedTask[index], updatedTask[index + 1]] = [
        updatedTask[index + 1],
        updatedTask[index],
      ];
      setTasks(updatedTask);
    }
  }

  return (
    <>
      <div className="to-do-list">
        <h1>To-Do List</h1>
        <div>
          <input
            type="text"
            placeholder="Enter a Task"
            value={newTasks}
            onChange={handleInputChange}
          />
          <button className="add-button" onClick={addTask}>
            Add
          </button>
        </div>
        <div>
          <ol>
            {tasks.map((task, index) => {
              return (
                <li key={index}>
                  <span className="text">{task}</span>
                  <button
                    className="delete-task"
                    onClick={() => deleteTask(index)}
                  >
                    Delete
                  </button>
                  <button
                    className="move-task"
                    onClick={() => moveTaskUp(index)}
                  >
                    Up
                  </button>
                  <button
                    className="move-task"
                    onClick={() => moveTaskDown(index)}
                  >
                    Down
                  </button>
                </li>
              );
            })}
          </ol>
        </div>
      </div>
    </>
  );
}

export default TodoList;
```

```CSS
body {
  background-color: hsl(0, 0%, 10%);
}
.to-do-list {
  font-family: Arial, Helvetica, sans-serif;
  text-align: center;
  margin-top: 100px;
}
h1 {
  font-size: 4rem;
  color: white;
}
button {
  font-size: 1.7rem;
  font-weight: bold;
  padding: 10px 20px;
  color: white;
  border: none;
  border-radius: 15px;
  cursor: pointer;
  transition: background-color 0.5s ease;
}
.add-button {
  background-color: hsl(125, 47%, 54%);
}
.add-button:hover {
  background-color: hsl(125, 47%, 44%);
}
.delete-task {
  background-color: hsl(10, 90%, 54%);
}
.delete-task:hover {
  background-color: hsl(10, 90%, 44%);
}
.move-task {
  background-color: blue;
}
.move-task:hover {
  background-color: hsl(240, 100%, 40%);
}
.down-task {
  background-color: hsl(207, 90%, 64%);
}
.down-task:hover {
  background-color: hsl(207, 90%, 54%);
}
input[type="text"] {
  font-size: 1.6rem;
  padding: 10px;
  border: 2px solid hsl(0, 0%, 80%, 0.5);
  color: hsl(0, 0%, 0%, 0.5);
}
ol {
  padding: 0;
}
li {
  font-size: 2rem;
  font-weight: bold;
  padding: 15px;
  background-color: hsl(0, 0%, 90%);
  margin-bottom: 10px;
  border: 3px solid hsl(0, 0%, 85%, 0.75);
  border-radius: 15px;
  display: flex;
  align-items: center;
}
.text {
  flex: 1;
}
.delete-task,
.move-task {
  padding: 8px 12px;
  font-size: 1.4rem;
  margin-left: 10px;
}
```