<template>
  <form
  class="add-form"
  @submit="onSubmit"
  >
     <div class="form-control">
       <label>Note</label>
       <input
          type="text"
          name="text"
          placeholder="Add note"
          v-model="text"
       >
     </div>
    <div class="form-control" >
      <label>Date and Time</label>
      <input
          type="datetime-local"
          name="day"
          placeholder="Add date and time"
          v-model="day"

      >
    </div>
    <div class="form-control form-control-check">
      <label>Mark</label>
      <input
          type="checkbox"
          value="reminder"
          v-model="reminder"
      >
    </div>
    <input
        type="submit"
        value="Save Task"
        class="btn btn-block">
  </form>
</template>

<script>
export default {
  name: "AddTask",
  data() {
    return {
      text: '',
      day: '',
      reminder: false
    }
  },
  methods: {
    onSubmit(e) {
      e.preventDefault()
      if(!this.text && !this.day) {
        alert("You must add all thing")
        this.text = ''
        this.day = ''
        this.reminder = false
        return
      }
      if(!this.text) {
        alert("Please add note!")
        this.text = ''
        this.day = ''
        this.reminder = false
        return
      }
      if(!this.day) {
        alert("Please add day!")
        this.text = ''
        this.day = ''
        this.reminder = false
        return;
      }
      // eslint-disable-next-line no-unused-vars
      const AddTask = {
        id: Math.floor(Math.random() * 1000),
        text: this.text,
        day: this.day,
        reminder: this.reminder
      }
      this.$emit('Add-task', AddTask)
      this.text = ''
      this.day = ''
      this.reminder = false
    }
  }
}
</script>

<style scoped>
  .form-control-check input{
    flex: 2;
    height: 20px;
  }
  .form-control-check label {
    flex: 1;
  }
  .form-control-check {
    display: flex;
    align-items: center;
    justify-content: space-between;
  }
  .add-form {
    margin-bottom: 40px;
  }
  .form-control{
    margin: 20px 0;
  }
  .form-control label {
    display: block;
  }
  .form-control input {
    width: 100%;
    height: 40px;
    margin: 5px;
    padding: 3px 7px;
    font-size: 17px;
  }
</style>