<template>
  <div>
    <header>
      <h1>{{ title }}</h1>
      <Button
          @toggle-add-task="$emit('toggle-add-task')"
          :text="showAddTask ? 'Close Note' : 'Open Add Note'" color="blue"
      />
    </header>
  </div>
</template>

<script>
import Button from "./Button";
export default {
  name: 'Header',
  components: {Button},
  props: {
    title: String,
    showAddTask: Boolean
  },
  data() {
    return{

    }
  }
}
</script>

<style scoped>
  header{
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 20px;
  }
</style>