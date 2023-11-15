<template>
  <div class="project">
    <div class="actions">
      <h3 @click="showDetails = !showDetails">{{ project.title }}</h3>
    </div>
    <div v-if="showDetails" class="details">
      <p>{{ project.details }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "SingleProject",
  props: ["project"],
  data() {
    return {
      showDetails: false,
    };
  },
};
</script>

<style scoped>
.project {
  background: white;
  margin: 20px auto;
  padding: 10px 20px;
  border-radius: 4px;
  box-shadow: 1px 2px 3px rgba(0, 0, 0, 0.12);
  /* Default color is not complete */
  border-left: 4px solid rgb(240, 20, 64);
}
h3 {
  cursor: pointer;
}
</style>
