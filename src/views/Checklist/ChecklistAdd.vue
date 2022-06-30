<template lang="">
    <div>
        <div>     
            <div class="form-group">
                <label for="">Name</label>
                <input type="text"
                class="form-control" name="passowrd" id="password" v-model="name" aria-describedby="helpId" placeholder="">
            </div>
            <div>
                <button type="submit" @click="createChecklist">Create Checklist</button>
            </div>
        </div>
    </div>
</template>
<script>
import axios from 'axios'

export default {
    name: 'LoginView',
    data(){
        return {
            username: '',
            password: ''
        }
    },
    methods: {
        createChecklist(){
            axios.post('http://94.74.86.174:8080/api/checklist',{
                username: this.username,
                password: this.password
            })
            .then((res)=>{
                console.log(res)
                let token = res.data.data.token
                localStorage.setItem('token', token)
                this.$router.push({name: "home"})
            }).catch((err)=>{
                console.log(err)
            })
        }
    }
}
</script>
<style lang="">
    
</style>