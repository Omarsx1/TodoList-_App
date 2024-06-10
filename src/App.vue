<script setup>
import { ref, onMounted, computed, watch } from "vue";

const todos = ref([]);
const name = ref("");

const input_content = ref("");
const input_category = ref(null);

const todos_asc = computed(() =>
  todos.value.sort((a, b) => {
    return b.createdAt - a.createdAt;
  })
);

const addTodo = () => {
  if (input_content.value.trim() === "" || input_category.value === null) {
    return;
  }
  todos.value.push({
    content: input_content.value,
    category: input_category.value,
    done: false,
    createdAt: new Date().getTime(),
  });
 
  input_content.value = ""
  input_category.value = null
};

const removeTodo = todo => {
  todos.value = todos.value.filter(t => t !== todo)
}

watch(
  todos,
  (newVal) => {
    localStorage.setItem("todos", JSON.stringify(newVal));
  },
  { deep: true }
);

watch(name, (newVal) => {
  localStorage.setItem("name", newVal);
});

onMounted(() => {
  name.value = localStorage.getItem("name") || "";
  todos.value = JSON.parse(localStorage.getItem("todos")) || [];
});
</script>

<template>
  <main class="app">
    <section class="greeting">
      <h2 class="title">
        Que pasa,
        <input type="text" placeholder="Tu nombre aquí" v-model="name" />
      </h2>
    </section>

    <section class="create-todo">
      <h3 class="font-semibold">Crear una tarea pendiente</h3>

      <form @submit.prevent="addTodo">
        <h4>¿Qué hay en tu lista de tareas pendientes?</h4>
        <input
          type="text"
          placeholder="p.ej. Revisar el informe general"
          v-model="input_content"
        />
        <h4 class="text-gray-700">Elige una categoría</h4>

        <div class="options">
          <label>
            <input
              type="radio"
              name="category"
              id="personal"
              value="personal"
              v-model="input_category"
            />
            <span class="bubble personal"></span>
            <div class="font-bold">Personal</div>
          </label>

          <label>
            <input
              type="radio"
              name="category"
              value="business"
              v-model="input_category"
            />
            <span class="bubble business"></span>
            <div class="font-bold">Trabajo</div>
          </label>
        </div>

        <input type="submit" value="Agregar a la lista" />
      </form>
    </section>

    <section class="todo-list">
      <h3>Lista de pendientes</h3>
      <div class="list">
        <div v-for="todo in todos_asc" :class="`todo-item ${todo.done && 'done'}`">
          <label>
            <input type="checkbox" v-model="todo.done"/>
            <span :class="`bubble ${todo.category}`">
              </span>
          </label>

          <div class="todo-content">
            <input type="text" v-model="todo.content" disabled/>
          </div>

          <div class="actions">
            <button class="delete rounded-2xl" @click="removeTodo(todo)">Eliminar</button>
          </div>
        </div>
      </div>
    </section>
  </main>
</template>
