<script>
  import Todo from '../Todo.svelte'
  import Card from '../Card.svelte'
  import { fade, fly } from 'svelte/transition';

</script>
<div in:fade>
  <Card title="Todos">
    <Todo ></Todo>
  </Card>
</div>
