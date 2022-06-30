<template lang="">
    <div>
        <div>     
            <div class="form-group">
                <label for="">Username</label>
                <input type="text"
                class="form-control" name="" id="" v-model="username" aria-describedby="helpId" placeholder="">
            </div>
            <div class="form-group">
                <label for="">Password</label>
                <input type="text"
                class="form-control" name="" id="" v-model="password" aria-describedby="helpId" placeholder="">
            </div>
            <div>
                <button type="submit" @click="submitLogin">Login</button>
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
        submiLogin(){
            axios.post('http://94.74.86.174:8080/api/',{
                username: this.username,
                password: this.password
            })
            .then((res)=>{
                console.log(res)
            }).catch((err)=>{
                console.log(err)
            })
        }
    }
}
</script>
<style lang="">
    
</style>