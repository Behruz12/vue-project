<template>
  <div @dblclick="$emit('toggle-reminder', task.id)" :class="[task.reminder ? 'reminder' : 'remind', 'task']">
    <h3>
      {{ task.text }}
      <i @click="$emit('delete-task', task.id)" class="fas fa-times"></i>
    </h3>
    <p>{{ task.day }}</p>
  </div>
</template>

<script>

export default {
  name: 'Task',
  props: {
    task: Object
  },
  data(){
    return {

    }
  }
}
</script>

<style scoped>
  .task{
    background: #f4f4f4;
    margin: 5px;
    padding: 10px 20px;
    cursor: pointer;
  }
  .task.reminder{
    border-left: 5px solid green;
  }
  .task.remind {
    border-left: 10px solid red;
  }
  .task h3{
    display: flex;
    align-items: center;
    justify-content: space-between;
  }
  .fas {
    color: red;
  }
</style>