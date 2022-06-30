<template lang="">
    <div>
        <div>     
            <div class="form-group">
                <label for="">Username</label>
                <input type="text"
                class="form-control" name="username" id="username" v-model="username" aria-describedby="helpId" placeholder="">
            </div>
            <div class="form-group">
                <label for="">Password</label>
                <input type="password"
                class="form-control" name="passowrd" id="password" v-model="password" aria-describedby="helpId" placeholder="">
            </div>
            <div>
                <button type="submit" @click="submitLogin">Login</button>
            </div>
            <a href="/register">Register</a>
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
        submitLogin(){
            axios.post('http://94.74.86.174:8080/api/login',{
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