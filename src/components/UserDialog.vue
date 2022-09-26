<template>
  <div>
    <button type="button" @click="handleClick">Show Dialog</button>
  </div>
</template>

<script>
  export default {
    name: 'UserDialog',
    emits: ['dialogUpdated'],
    methods: {
      handleClick() {
        this.$emit('dialogUpdated', true);
      }
    }
  }
</script>
