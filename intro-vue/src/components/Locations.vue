<template>
    <div class="destination">
        <h2 class="location-header">Your Destinations:</h2>
        <ul class="destination-ul">
            <li  v-for="post in locationData" :key="post.id" class="destination-li">
                <div class="moveX">
                    <h2 class="destination-h3"> {{ post.country_name }}</h2>
                    <button v-bind='post' @click='deletePost(post)' class="delete-button" name='button'>X</button>
                </div>
                <h4 class="destination-goalDate">Date: {{ post.goal_date | moment('dddd, MMMM Do YYYY')}}</h4>
                <h4 class="destination-activities">Activities: {{ post.activities }}</h4>
            </li>
        </ul>
    </div>
</template>

<script>
    export default {
        data() {
            return {
                name: "Locations",
                msg: "Welcome to Your Vue.js App",
                locationUrl: "https://travel-bug-backend.herokuapp.com/posts/profile/" +
                    this.$route.query.user,
                locationData: null,
                deleteURL: "https://travel-bug-backend.herokuapp.com/posts/",
                
            };
        },
        created() {
            this.fetchCountries()
        },
    
        methods: {
            fetchCountries(){
                fetch(this.locationUrl, {
                        method: "get",
                        mode: "cors",
                        headers: new Headers({
                            "Content-Type": "application/json"
                        })
                    })
                    .then(resp => resp.json())
                    .then(resp => {
                        this.locationData = resp.posts;
                    });
                },  
            deletePost(post) {
                {
                    fetch(this.deleteURL + post.location_post_id, {
                            method: "DELETE",
                        })
                        .then(resp => resp.json())
                        .then(json => {return json;})
                        .then(this.locationData = this.locationData.filter((element)  => {
                            return element.location_post_id !== post.location_post_id
                        }))
                }
            }
        }
    }

</script>

<style>
    .destination {
        display: flex;
        flex-flow: column;
        margin-left: 5vw;
    }

    .moveX{
        display: flex;
        justify-content: space-between
    }
    
    .location-header {
        font-size: 1.2em;
        color: #086788;
        text-shadow: -1px -1px 1px white, 1px 1px 1px white, -1px 1px 1px white, 1px -1px 1px white;
        font-family: "Slackey";
    }
    
    .destination-ul {
        list-style: none;
        padding: 0px;
        width: 60vw;
    }
    
    .destination-li {
        background-color: #9fb1bca8;
        border-radius: 15px;
        box-shadow: 8px 8px 8px #444545;
        color: #086788;
        border: 0px;
        font-family: "Simonetta";
    }
    
    .destination-activities,
    .destination-goalDate,
    .destination-h3 {
        margin-left: 1vw;
    }
    
    .destination-h3 {
        color: #086788;
        text-shadow: -1px -1px 1px white, 1px 1px 1px white, -1px 1px 1px white, 1px -1px 1px white;
        font-family: "Slackey";
    }
    
    .delete-button {
        display:flex;
        font-size: 1em;
        background-color: red;
        height: 5vh;
        margin-right: 1vw;
        margin-top: 1vw;
        color: #086788;
        border: solid #086788;
    }
</style>
 
