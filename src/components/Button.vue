<template>
  <div>
    <button @click="onClick()" :style="{ background: color }" class="btn">{{ text }}</button>

  </div>
</template>

<script>
export default {
  name: 'Button',
  props: {
    text: String,
    color: String
  },
  data(){
    return{

    }
  },
  methods: {
    onClick() {
      this.$emit('toggle-add-task')
    }
  }
};
</script>

<style>

</style>