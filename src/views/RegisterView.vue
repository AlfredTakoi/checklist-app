<template lang="">
    <div>
        <div>
            <div class="form-group">
                <label for="">Email</label>
                <input type="email"
                class="form-control" name="email" id="email" v-model="email" aria-describedby="helpId" placeholder="">
            </div>
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
                <button type="submit" @click="submitLogin">Register</button>
            </div>
            <a href="/">Login</a>
        </div>
    </div>
</template>
<script>
import axios from 'axios'

export default {
    name: 'LoginView',
    data(){
        return {
            email: '',
            username: '',
            password: ''
        }
    },
    methods: {
        submitLogin(){
            axios.post('http://94.74.86.174:8080/api/register',{
                username: this.username,
                password: this.password,
                email: this.email
            })
            .then((res)=>{
                console.log(res)
                this.$router.push({name: "login"})
            }).catch((err)=>{
                console.log(err)
            })
        }
    }
}
</script>
<style lang="">
    
</style>