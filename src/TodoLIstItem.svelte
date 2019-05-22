<li
  class="{ todo.done ? 'todo-li--done': '' }"
  on:click="fire('toggle-todo', { todo, index })"
>
  { todo.title }
</li>

<style>
    .todo-li--done {
      text-decoration: line-through;
    }
</style>