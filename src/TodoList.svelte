<input type="text" value="{value}">
<button on:click="{addTodo(title)}">追加</button>
<ul>
    { #each filteredTodos as todo, index }
      <TodoListItem {todo} {index} on:toggle-todo="{toggleTodo(event)}"/>
    { /each }
</ul>

<button on:click="{set({ condition: null })}">すべて</button>
<button on:click="{set({ condition: true })}">完了のみ</button>
<button on:click="{set({ condition: false })}">未完了のみ</button>


<script>
    import { push, splice } from 'svelte-extras';
    import TodoListItem from './TodoListItem'
    // export default 'TodoListItem.svelte';

    let value = "";
    const data = () => {
      return {
        title: "",
        todos: [],
        condition: null
      }
    };

    const filteredTodos = (todos, condition) => {
      return condition !== null ? todos.filter(x => x.done === condition) : todos;
    }

    const addTodo = (title) => {
      this.todos.push({title, done: false})
    }
    // data() {
    //     return {
    //       title: '',
    //       todos: [],
    //       condition: null,
    //     };
    //   };
    //   computed: {
    //     filteredTodos({ todos, condition }) {
    //       return condition !== null ? todos.filter(todo => todo.done === condition) : todos;
    //     },
    //   },
    //   methods: {
    //     push,
    //     splice,
    //     addTodo(title) {
    //       this.push('todos', { title, done: false });
    //       this.set({ title: '' }); 
    //     },
    //     toggleTodo({ todo, index }) {
    //       this.splice('todos', index, 1, { ...todo, done: !todo.done });
    //     },
    //   },
    // };
</script>