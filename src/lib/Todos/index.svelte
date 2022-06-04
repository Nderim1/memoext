<script>
  import { onMount } from "svelte";

  import AddTodo from "./AddTodo/index.svelte";
  import ShowTodos from "./ShowTodos/index.svelte";

  let todoToEdit = "";
  let todoToEditIndex = "";

  let allTodos = [];

  const updateLSTodos = (todos) => {
    localStorage.setItem("memo.todos", JSON.stringify(todos));
  };

  const addTodo = (todo) => {
    allTodos = [].concat(todo, allTodos);
    updateLSTodos(allTodos);
  };

  const editTodo = (newText) => {
    allTodos[todoToEditIndex].title = newText;
    allTodos[todoToEditIndex].status = "todo";
    todoToEdit = "";
    todoToEditIndex = "";
  };

  const handleEditTodoClick = (index) => {
    todoToEdit = allTodos[index].title;
    todoToEditIndex = index;
  };

  const handleOnCheckboxCheck = (index, status) => {
    allTodos[index].status = status;
    updateLSTodos(allTodos);
  };

  const removeTodo = (index) => {
    const confirmPopup = window.confirm(
      "Are you sure you want to delete your TODO?"
    );
    if (confirmPopup) {
      allTodos.splice(index, 1);
      // mutate the array so it triggers a rerender
      allTodos = [].concat(allTodos);
      updateLSTodos(allTodos);
    }
  };

  onMount(() => {
    const LSTodos = localStorage.getItem("memo.todos");
    if (!LSTodos) {
      updateLSTodos(allTodos);
    } else {
      allTodos = JSON.parse(LSTodos);
    }
  });
</script>

<div>
  <AddTodo {addTodo} {todoToEdit} {editTodo} />
  <ShowTodos
    {allTodos}
    {handleOnCheckboxCheck}
    {removeTodo}
    editTodo={handleEditTodoClick}
  />
</div>
