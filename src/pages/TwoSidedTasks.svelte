<script>
  import Card from "../Card.svelte"
  import TaskList from '../tasks/TaskList.svelte'

  let tasks =[
    {title: "Work to do", value: 1},
    {title: "Steady as she goes", value: 2},
    {title: "Super hard task!", value: 3}
  ]
  let trashTasks =[{title: "Weekend at bernies", value: 3}]

  function addTask(task, value) { 
    tasks.push({title: task, value: value})
    tasks = tasks
  }

  function completeTask(i) { 
    let result = tasks.splice(i, 1)[0]
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
        addTask={(task, value) => addTask(task, value) } 
        completeTask={(v) => completeTask(v)}
        deleteTask={(v) => deleteTask(v)}>
      </TaskList>
    </div>
    <div class="w-1/2">
      <TaskList tasks={trashTasks} completedMode={true}></TaskList>
    </div>
  </div>  

</Card>