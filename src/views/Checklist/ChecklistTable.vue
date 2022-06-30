<template lang="">
  <div>
    <button :to="{name: 'checklist.add'}">Create</button>
    <table>
      <thead>
        <tr>
          <th>No</th>
          <th>Name</th>
          <th>Action</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(checklist, index) in checklists" :key="index++">
          <td>{{index}}</td>
          <td>{{checklist.name}}</td>
          <td>
            <button>Edit</button> <button>Delete</button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>
<script>
import axios from 'axios'

export default {
  data() {
    return {
      checklists: [],
    };
  },
  mounted() {
    this.getChecklist();
  },
  methods: {
    getChecklist() {
      axios
        .get("http://94.74.86.174:8080/api/checklist", {
          headers: {
            Authorization: "Bearer " + localStorage.getItem("token"),
          },
        })
        .then((res) => {
          console.log(res);
          this.checklists = res.data.data;
        })
        .catch((err) => {
          console.log(err);
        });
    },
  },
};
</script>
<style lang=""></style>
