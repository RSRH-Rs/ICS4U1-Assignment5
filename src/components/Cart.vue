<script setup>
import { useCart, useStore } from "../store/index.js"
const cart = useCart();
const store = useStore();
</script>

<template>

    <div class="cartlist" v-for="item in new Set(cart.purchase)" v-if="cart.purchase">
        <div class="display">
            <div class="name">
                {{ store.movies.filter(x => x.id == item)[0].title }}
            </div>
            
        </div>

    </div>

    <button class="purchase_btn" @click="cart.clear()" >Clear Items </button>

</template>

<style scoped>
.cartlist {
    height: 100%;
    background: url("https://cdn.wallpapersafari.com/51/70/ZfwI49.jpg") no-repeat center;
    background-size: cover;

}

.display {
    color: black;
    font-weight: 300;
    width: 97%;
    margin: 10px;
    border: 3px solid darkred;
    padding: 10px;
    display: list-item;
}

.name {
    float: left;
    font-family: Impact, Haettenschweiler, 'Arial Narrow Bold', sans-serif;
}



.purchase_btn {
    width: 150px;
    height: 40px;
    margin-top: 20px;
    background: linear-gradient(to right, red, darkred);
    border: 1px solid red;
    border-radius: 5px;
    font-family: Georgia, 'Times New Roman', Times, serif;
    font-weight: 600;
    font-size: 20px;
    margin-left: 1%;
}



.purchase_btn:hover{
    color: white;
}
</style>