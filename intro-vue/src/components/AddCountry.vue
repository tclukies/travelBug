<template>
<div id='country'>
    <form @submit='onSubmit' class="country-form">
        <label for='addToList' class="add-to">Add to Your Bucket List!</label>
        <div>
            <input  v-model='form.country_name' placeholder=' Country Name' type='text' name='country_name' id='country_name' value=''>
        </div>
        <div>
            <input v-model='form.goal_date' placeholder=' Goal Date' type='text' name='goal_date' id='goal_date' value=''>
        </div>
        <div>
            <textarea  v-model='form.activities' placeholder=' Activities you want to do!' type='text' name='activities' id='activities' value=''>Add activities here!</textarea>
        </div>
        <div>
            <input  v-model='form.visited' placeholder=' True or False' type='text' name='visited' id='visited' value=''>
        </div>
            <button type='submit' name='button'  class="country-form-button" >Add Now!</button>
            
    </form>
    </div>
</template>

<script>
export default {
    name: "AddCountry",
    data() {
        return {
            // location: "",
            // activities: "",
            postsURL: "https://travel-bug-backend.herokuapp.com/posts",
            form: {
                profile_id: "",
                country_name: "",
                goal_date: "",
                activities: "",
                visited: ""
            }
        };
    },
    methods: {
        onSubmit(evt) {
            this.form.profile_id = this.$route.query.user;
            evt.preventDefault();
            return fetch(this.postsURL, {
                method: "post",
                headers: new Headers({ "Content-Type": "application/json" }),
                body: JSON.stringify(this.form)
            })
                .then(console.log(this.form))
                .then(resp => {
                    console.log(resp);
                    if (!resp.ok) {
                        if (resp.status >= 400 || resp.status < 500) {
                            return resp.json().then(data => {
                                const err = { errorMessage: data.message };
                                throw err;
                            });
                        }
                        const err = { errorMessage: "Blah" };
                        throw err;
                    }
                    return resp.json();
                })
                .then(setTimeout(function() {
                            location.reload();
                        }, 1000))
        }
    }
};
</script>

<style>
.country-form {
    display: flex;
    flex-flow: column;
    /* height: 60vh; */
    flex-wrap: column;
    justify-content: center;
    align-items: center;
    margin-bottom: 5vh;
    background-color: #9fb1bca8;
    border-radius: 15px;
    box-shadow: 8px 8px 8px #444545;
    padding: 1vh;
    width: 24vw;
}
#country_name,
#goal_date,
#activities,
#visited {
    background-color: white;
    width: 15vw;
    border: 1px solid black;
    margin-bottom: 1vh;
    color: #086788;
    box-shadow: 3px 3px 3px #444545;
    border-radius: 10px;
}
#activities {
    margin: 0;
}
textarea:focus,
input:focus {
    outline: none;
}
.add-to {
    font-size: 1.2em;
    color: #086788;
    text-shadow: -1px -1px 1px white, 1px 1px 1px white, -1px 1px 1px white,
        1px -1px 1px white;
    font-family: "Slackey";
}
.country-form-button {
    background-color: white;
    color: #086788;
    height: 5vh;
    border-radius: 10px;
    box-shadow: 3px 3px 3px #444545;
    border: 0px;
}
</style>
