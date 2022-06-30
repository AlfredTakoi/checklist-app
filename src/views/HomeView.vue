<template>
  <div class="home">
    <h1>Welcome</h1>

    <a href="#">Create</a>
    <table>
      <thead>
        <tr>
          <th>No</th>
          <th>Name</th>
          <th>Action</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td></td>
          <td></td>
          <td></td>
        </tr>
      </tbody>
    </table>
  </div>
</template>
<script>
import axios from 'axios'

export default {
  data(){
    return {
      checklist: []
    }
  },
  mounted(){
    this.getChecklist()
  },
  methods:{
    getChecklist(){
      axios.get('http://94.74.86.174:8080/api/checklist',{
        headers: {
          Authorization: "Bearer " + localStorage.getItem('token'), 
        }
      })
      .then((res)=>{
        console.log(res)
        this.checklist = res.data.data
      }).catch((err)=>{
        console.log(err)
      })
    }
  }
}
</script>
