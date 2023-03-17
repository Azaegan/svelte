<script>
  let counter = 0;
  let message = 'Hello Svelte';
  let items = [
    {name:'piim', done:false} 
    {name:'sai', done:true}
    {name:'viin', done:false}
    {name: 'õlu', done:true}
    ];
    $: doneItems =  items.filter(item => item.done);
    $: toDoItems =  items.filter(item => item.done);
  function add(){
    items.push({name:message, done: false});
    items = items;
    message = '';
  }
</script>
<div class="content">
  <input type="text" class="input" bind:value={message}>
  <button class="button is-primary" on:click={add}>Add</button>
  <ItemList bind:items={items} title="All Items"></ItemList>
  <ItemList bind:items={doneItems} title="Done Items"></ItemList>
  <ItemList bind:items={toDoItems} title="To Do Items"></ItemList>
</div>
  <h1>All Items</h1>
  <ul>
    {#each items as item}
    <li>
      {item.name}
    <input type="checkbox" bind:checked={item.done}>
  </li>
    {/each}
  </ul>
  <h1>Done Items</h1>
  <ul>
    {#each doneItems as item}
    <li>
      {item.name}
    <input type="checkbox" bind:checked={item.done}>
  </li>
    {/each}
  </ul>
  <h1>Todo Items</h1>
  <ul>
    {#each toDoItems as item}
    <li>
      {item.name}
    <input type="checkbox" bind:checked={item.done}>
  </li>
    {/each}

