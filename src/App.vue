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
import TodoEmpty from './components/TodoEmpty.vue';
import TodoFormAdd from './components/TodoFormAdd.vue';
import TodoItems from './components/TodoItems.vue';
import TodoSpinner from './components/TodoSpinner.vue';




export default {
  name: 'App',
  components: {
    TodoSpinner,
    TodoFormAdd,
    TodoItems,
    TodoEmpty
  },
  data() {
    return {
      loading: true
    }
  },


  created() {
    this.$store.dispatch('getTodos').finally(() => {
      this.loading = false
    })
  }
}
</script>
