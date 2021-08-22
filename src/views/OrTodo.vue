<template>
  <div class="TodoB">
    <Todo />
  </div>
</template>

<script>
// @ is an alias to /src
import Todo from '@/components/Todo.vue'

export default {
  name: 'Todo',
  components: {
    Todo
  }
}
</script>
