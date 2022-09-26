<template>
  <div>
    <h1>NAME: {{ user.name }}, AGE: {{ user.age }}</h1>
  </div>
</template>

<script>
  export default {
    name: 'UserDisplay',
    props: {
      user: {
        name: String,
        age: Number,
      }
    }
  }
</script>
