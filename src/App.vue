<template>
  <div class="px-3 py-10 md:px-10">
    <div class="w-full sm:w-1/2 lg:w-1/3 mx-auto">

      <TodoSpinner v-if="loading" />

      <TodoFormAdd />

      <TodoItems v-if="$store.state.todos.length" />

      <TodoEmpty v-else />
    </div>
  </div>
</template>

<script>
import { ref } from 'vue';
import TodoEmpty from './components/TodoEmpty.vue';
import TodoFormAdd from './components/TodoFormAdd.vue';
import TodoItems from './components/TodoItems.vue';
import TodoSpinner from './components/TodoSpinner.vue';
import { useStore } from 'vuex';




export default {
  name: 'App',
  components: {
    TodoSpinner,
    TodoFormAdd,
    TodoItems,
    TodoEmpty
  },

  setup() {
    const loading = ref(false);
    const store = useStore()


    loading.value = true
    store.dispatch('getTodos').finally(() => {
      loading.value = false
    })

    return {
      loading
    }
  },






}
</script>
