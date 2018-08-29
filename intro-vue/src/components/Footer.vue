<template>
<div class='footer'>
    <router-link to='/about' class='anchor'>About</router-link>
    <router-link to='/faq' class='anchor'>FAQ</router-link>
    <router-link to='/contactus' class='anchor'>Contact Us</router-link>
    </div>
</template>

<script>
export default {
    name: "Footer",
    data() {
        return {
            msg: "Welcome to Your Vue.js App"
        };
    }
};
</script>

<style>
.footer {
    margin-left: 35%;
    margin-right: 35%;
    position: center;
    bottom: 0;
    position: fixed;
    width: 30%;
    text-align: center;
    background-color: rgba(255, 255, 255, 0.418);
    border-radius: 15px;
}
.first {
    display: flex;
    height: 90vh;
}
</style>