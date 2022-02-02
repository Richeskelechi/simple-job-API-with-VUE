<template>
  <h1>Job Details Page</h1>
  <div v-if="job">
    <p>The Job ID is {{ id }}</p>
    <p>The Job Title is {{ job.title }}</p>
    <p>The Job Detail is {{ job.details }}</p>
  </div>
  <div v-else>Loading</div>
</template>

<script>
export default {
  props: ["id"],
  data() {
    return {
      job: null,
    };
  },
  mounted() {
    fetch("http://localhost:3000/jobs/" + this.id)
      .then((res) => res.json())
      .then((data) => (this.job = data))
      .catch((err) => console.log(err.message));
  },
};
</script>

<style></style>
