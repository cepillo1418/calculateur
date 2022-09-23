<template>
  <div id="user__card">
    <p>Nom: {{ name }}</p>
    <p>Score: {{ score }}</p>
  </div>
</template>

<script>
export default {
  name: "UserCard.vue",
  props: {
    name: String,
    score: Number
  }
}
</script>

<style scoped lang="scss">
#user__card {
  border: 1px solid black;
  border-radius: 5px;

  p:first-child {
    color: red;
  }
}
</style>