<script>
  import Card from "../Card.svelte"
  import TaskList from '../tasks/TaskList.svelte'

  let tasks =["Work to do", "more work to do", "Other Stuff you don't want"]
  let trashTasks =["Working for the weekend"]

  function addTask(task) { 
    tasks.push(task)
    tasks = tasks
  }

  function completeTask(i) { 
    let result = tasks.splice(i, 1)
    trashTasks.push(result)
    trashTasks = trashTasks
    tasks = tasks
  }

  function deleteTask(i) { 
    tasks.splice(i, 1)
    tasks = tasks
  }

</script>

<Card title="Two sided lists">
  <div class="flex">
    <div class="w-1/2">
      <TaskList 
        tasks={tasks} 
        addTask={(v) => addTask(v) } 
        completeTask={(v) => completeTask(v)}
        deleteTask={(v) => deleteTask(v)}>
      </TaskList>
    </div>
    <div class="w-1/2">
      <TaskList tasks={trashTasks} completedMode={true}></TaskList>
    </div>
  </div>  

</Card>