<template>
  <div id='app'>
    <router-view/>

  </div>
</template>

<script>
const API_URL = "https://travel-bug-backend.herokuapp.com/profiles";

export default {
    name: "Register",
    data() {
        return {
            // registerURL: "https://travel-bug-backend.herokuapp.com/profiles",
            // form: {
            //   username: "",
            //   password: ""
            // },
            show: true
            // users: [],
        };
    }
    // mounted() {
    //   fetch(this.registerURL, {
    //     method: "get",
    //     mode: "cors",
    //     credentials: "same-origin",
    //     headers: new Headers({ "Content-Type": "application/json" })
    //   }).then(resp => {
    //     return resp.json().then(resp => {
    //       console.log(resp);
    //     });
    //   });
    // }
};
</script>

<style>
html {
    background-image: "https://blenderartists.org/uploads/default/original/4X/9/d/d/9dd7ee0b61133075aaf60207c9c05ebc1ac23cad.jpg";
}
</style>