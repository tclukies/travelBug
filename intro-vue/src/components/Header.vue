<template>
  <div class="header-1">
    <img src="../assets/TravelBug.png" class="dion1">
    <h1 class="travel-bug">Travel Bug</h1>
    <router-link to='/' tag='button' class="header-1-logout">Logout</router-link>
  </div>
</template>

<script>
export default {
    name: "Header",
    data() {
        return {
            msg: "Welcome to Your Vue.js App"
        };
    }
};
</script>
 
<style>
.header-1 {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-top: 1vh;
    margin-left: 10vh;
    margin-right: 10vh;
}
.dion1 {
    height: 12vh;
}
.travel-bug {
    color: #086788;
    text-shadow: -2px -2px 2px white, 2px 2px 2px white, -2px 2px 2px white,
        2px -2px 2px white;
    font-family: "Slackey";
}
.header-1-logout {
    background-color: white;
    color: #086788;
    height: 5vh;
    border-radius: 10px;
    box-shadow: 3px 3px 3px #444545;
}
</style>