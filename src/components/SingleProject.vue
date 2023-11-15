<template>
  <div class="project">
    <div class="actions">
      <h3>{{ project.title }}</h3>
    </div>
    <div class="details">
      <p>{{ project.details }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "SingleProject",
  props: ["project"],
};
</script>

<style scoped></style>
