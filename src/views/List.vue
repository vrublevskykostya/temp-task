<template>
  <div>
  <h1>List</h1>
    <div class="row">
      <div class="input-field s6">
        <select ref="select" v-model="filter">
          <option value="" disabled selected>Choose your filter</option>
          <option value="active">Active</option>
          <option value="outdate">Outdated</option>
          <option value="completed">Completed</option>
        </select>
        <label>Status filter</label>
        <button v-if="filter" class="btn" @click="filter = null">clear filter</button>
      </div>
    </div>

  <table v-if="tasks.length">
    <thead>
    <tr>
      <th>#</th>
      <th>Title</th>
      <th>Date</th>
      <th>Description</th>
      <th>Status</th>
      <th>Open</th>
    </tr>
    </thead>
    <tbody>
      <tr
          v-for="(task, idx) in displayTasks"
          :key="task.id"
      >
        <td> {{ idx + 1 }} </td>
        <td> {{task.title}} </td>
        <td> {{ new Date(task.date).toLocaleDateString() }} </td>
        <td><div class="text"> {{task.description}} </div></td>
        <td> {{ task.status }} </td>
        <td>
          <router-link
              tag="button"
              class="btn btn-small"
              :to="'/task/' + task.id"
        >OPEN</router-link>
        </td>
      </tr>
    </tbody>
  </table>

  <p v-else>No tasks</p>
  </div>
</template>

<script>
export default {
  name: "List",
  data: () => ({
    filter: null
  }),
  computed: {
    tasks() {
      return this.$store.getters.tasks
    },
    displayTasks() {
      return this.tasks.filter(t => {
        if (!this.filter) {
          return true
        } return t.status === this.filter
      })
    }
  },
  mounted() {
    M.FormSelect.init(this.$refs.select, {});
  },

}
</script>

<style scoped>
.text {
  width: 400px;
  white-space: nowrap;
  text-overflow: ellipsis;
  overflow: hidden;
}
</style>