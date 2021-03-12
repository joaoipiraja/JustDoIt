# JustDoIt
1st Ignite React Challenge

- [x] Add a new task  ✏️
- [x] Remove a task 🗑
- [x] Mark and unmark a task as completed ✅

### Tests specification
* Should be able to add a task
* Should not be able to add a task with an empty title
* Should be able to remove a task
* Should be able to check a task

### Resolution

```tsx
function searchId(id: number) {
    let resultId = tasks.findIndex(task => {
      return task.id == id;
    });
    return resultId;
  }

  function generateId() {
    let id = 0;
    const tasksLengh = tasks.length;

    if (tasksLengh > 0) {
      id = tasks[tasksLengh - 1].id + 1;
    }
    return id;
  }

  function handleCreateNewTask() {

    if (newTaskTitle) {
      const dado = { id: generateId(), title: newTaskTitle, isComplete: false };
      setTasks([...tasks, dado]);
      setNewTaskTitle("");
    }
  }

  function handleToggleTaskCompletion(id: number) {
    // Altere entre `true` ou `false` o campo `isComplete` de uma task com dado ID
    let updatedTasks = [...tasks];
    const index = searchId(id);
    updatedTasks[index].isComplete = !updatedTasks[index].isComplete;
    setTasks(updatedTasks);

  }

  function handleRemoveTask(id: number) {
    // Remova uma task da listagem pelo ID
    let updatedTasks = [...tasks];
    const index = searchId(id);
    updatedTasks.splice(index, index + 1);
    setTasks(updatedTasks);
  }
```