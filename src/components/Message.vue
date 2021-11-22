<template>
  <div class="message_container">
    <p>{{ msg }}</p>
  </div>
</template>

<script>
export default {
  name: "Message",
  props: {
    msg: String
  }
}
</script>

<style scoped>
  .message_container {
    color: #004085;
    background-color: #cce5ff;

    border: 2px solid #B8DAFF;
    border-radius: 5px;

    padding: 10px;
    max-width: 400px;
    margin: 30px auto;

    transition: ease .5s;
  }
</style>