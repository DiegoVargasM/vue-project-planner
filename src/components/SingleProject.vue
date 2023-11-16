<template>
  <div class="project" :class="{ complete: project.complete }">
    <div class="actions">
      <h3 @click="showDetails = !showDetails">{{ project.title }}</h3>
      <div class="icons">
        <router-link :to="{ name: 'EditProject', params: { id: project.jd } }">
          <span class="material-icons"> edit </span>
        </router-link>
        <span @click="deleteProject" class="material-icons"> delete </span>
        <span @click="toggleComplete" class="material-icons tick"> done </span>
      </div>
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
      uri: "http://localhost:3000/projects/" + this.project.id,
    };
  },
  methods: {
    deleteProject() {
      fetch(this.uri, { method: "DELETE" })
        .then(() => this.$emit("delete", this.project.id))
        .catch((err) => console.log(err));
    },
    toggleComplete() {
      fetch(this.uri, {
        method: "PATCH",
        headers: { "Content-Type": "application/json" },
        body: JSON.stringify({ complete: !this.project.complete }),
      })
        .then(() => {
          this.$emit("complete", this.project.id);
        })
        .catch((err) => console.log(err));
    },
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
  border-left: 4px solid rgb(240, 20, 64);
}

h3 {
  cursor: pointer;
}
.material-icons {
  cursor: pointer;
  font-size: 24px;
  color: #bbb;
  margin-left: 10px;
}
.material-icons:hover {
  color: rgb(102, 100, 100);
}

.actions {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.project.complete {
  border-left: 4px solid rgb(8, 180, 8);
}

.project.complete .tick {
  color: rgb(8, 180, 8);
}
</style>
