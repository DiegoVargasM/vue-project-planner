<template>
  <nav class="filter-nav">
    <button @click="updateFilter('all')" :class="{ active: currentFilter === 'all' }">
      View All
    </button>
    <button
      @click="updateFilter('completed')"
      :class="{ active: currentFilter === 'completed' }"
    >
      Completed
    </button>
    <button
      @click="updateFilter('ongoing')"
      :class="{ active: currentFilter === 'ongoing' }"
    >
      Ongoing
    </button>
  </nav>
</template>

<script>
export default {
  props: ["currentFilter"],
  name: "FilterNav",
  methods: {
    updateFilter(filter) {
      this.$emit("filterChange", filter);
    },
  },
};
</script>

<style>
.filter-nav button {
  background: none;
  border: none;
  color: #9e9d9d;
  outline: none;
  font-size: 0.8rem;
  text-transform: uppercase;
  margin-right: 10px;
  letter-spacing: 1px;
  font-weight: bold;
  cursor: pointer;
}
.filter-nav button.active {
  color: #424242;
}
</style>
