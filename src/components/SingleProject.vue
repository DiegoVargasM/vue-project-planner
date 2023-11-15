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

<style scoped>
.project {
  background: white;
  margin: 20px auto;
  padding: 10px 20px;
  border-radius: 4px;
  box-shadow: 1px 2px 3px rgba(0, 0, 0, 0.12);
  border-left: 4px solid rgb(240, 20, 64);
}
h3 {
  cursor: pointer;
}
</style>
