<script setup>
import { ref } from "vue";
import { useRouter } from "vue-router";
import { isLoggedIn } from "../store/index";

const data = ref(false);
const submitted = ref(false);
const username = ref("");
const password = ref("");
const router = useRouter();

const isSuccessful = () => {
    submitted.value = true;
    if (username.value == "tmdb" && password.value == "movies") {
        data.value = true;
        router.push('/Purchase');
        isLoggedIn.value = true;
    }
}

</script>

<template>
    <div class='login'>
        <h1 class="title">Use your username and password to Login! </h1>
        <form class='form-1' action="#" method="GET">
            <table>
                <tr>
                    <td class="td_left"><label for="username">Username</label></td>
                    <td class="td_right"><input type="text" name="username" id="username"
                            placeholder="username" v-model="username">
                    </td>
                </tr>

                <tr>
                    <td class="td_left"><label for="password">Password</label></td>
                    <td class="td_right"><input type="password" name="password" id="password"
                            placeholder="password" v-model="password"></td>
                </tr>

                

                <tr>
                    <td colspan="2" align="center">

                        <input type="button" id="btn_sub" value="Login" @click="isSuccessful()">
                    </td>
                </tr>
            </table>
        </form>

        <div v-if="submitted" class="submitted">
            <p v-if="!data" class="Deny">Invalid input. Incorrect username or password.</p>
        </div>
    </div>
</template>
    
<style scoped>
.title {
    text-align: center;
    font-family: Impact, Haettenschweiler, 'Arial Narrow Bold', sans-serif;
    font-weight: 800;
}

.Deny {
    border: 3px solid darkred;
    background-color: pink;
    font-size: 2vw;
    font-family: 'Times New Roman', Times, serif;
    font-weight: 900;
    margin-left: auto;
    margin-right: 15%;
    text-align: center;
    padding: 1vw;
    width: 50%;
    color: darkred;
}

.Welcome {
    border: 3px solid darkgreen;
    background-color: lightgreen;
    font-size: 2vw;
    font-family: 'Times New Roman', Times, serif;
    font-weight: 900;
    margin-left: auto;
    margin-right: 15%;
    text-align: center;
    padding: 1vw;
    width: 50%;
    color: darkgreen;
}

.login {
    margin-top: 5%;
    padding: 30px;
}

.form-1 {
    width: 50%;
    margin: 15px;
    margin-left: auto;
    margin-right: 15%;
}

.td_left {
    width: 100px;
    text-align: right;
    height: 45px;
    font-family: Georgia, 'Times New Roman', Times, serif;
}

.td_right {
    padding-left: 50px;
}

#username,
#password,
#email,
#name,
#tel {
    width: 251px;
    height: 32px;
    border: 1px solid #A6A6A6;
    border-radius: 5px;
    padding-left: 10px;
    font-family: Georgia, 'Times New Roman', Times, serif;
}

#img_check {
    height: 32px;
    vertical-align: middle;
}

#btn_sub {
    width: 150px;
    height: 40px;
    margin-top: 20px;
    background: linear-gradient(to right, red, darkred);
    border: 1px solid red;
    border-radius: 5px;
    font-family: Georgia, 'Times New Roman', Times, serif;
    font-weight: 600;
    font-size: 20px;
    margin-left: 20%;
}

#btn_sub:hover {
    color: white;
}
</style>