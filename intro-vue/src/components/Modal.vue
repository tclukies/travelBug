<template>
    <div class='content'>
        <div class="title">
            <h1>Welcome to Travel Bug!</h1>
            <div class="bug-div">
                <img id="travel-bug" src="../assets/TravelBug.png" class="dion">
           </div>
        </div>
        <div>
            <div class='modal-container'>
                <div class='modal-header'>
                    <slot name='login'>
                        <div v-if='logseen' id='signin'>
                            <form>
                                <h3>Come Explore!</h3>
                                <div class="login">
                                    <input placeholder='Username' type='text' name='username' id='username' value=''>
                                    <input placeholder='Password' type='password' name='password' id='password' value=''>
                                    <input @click.prevent='bool' type='submit' value='Sign In' class='signButton'>
                                </div>
                                <div class="new-to">
                                    <label for='login'>New to Travel Bug?</label>
                                </div>
                                <div>
                                    <!-- <b-button class='danger' v-on:click='seen ==! seen, logseen ==! logseen' type='submit' name='button'>Sign up now!</b-button> -->
                                    <button v-on:click='seen ==! seen, logseen ==! logseen' type='submit' class="signButton" name='button'>Sign up now!</button>
                                </div>
                                <div id="alertMessage">
                                    <p></p>
                                </div>
                            </form>
                        </div>
                    </slot>
                    <slot name='register'>
                        <div v-if='seen' id='registrationForm'>
                            <form @submit.prevent='sendCredentials()'>
                                <h3>We are excited for your new ventures!</h3>
                                <div>
                                    <input placeholder='First Name' type='text' name='firstName' id='firstName' value=''>
                                </div>
                                <div>
                                    <input placeholder='Last Name' type='text' name='lastName' id='lastName' value=''>
                                </div>
                                <div>
                                    <input placeholder='Email' type='text' name='email' id='email' value=''>
                                </div>
                                <div>
                                    <input placeholder='Username' type='text' name='username' id='username' value=''>
                                </div>
                                <div>
                                    <input placeholder='Password' type='text' name='passWord' id='passWord' value=''>
                                </div>
                                <div>
                                    <input placeholder='Confirm Password' type='text' name='confirmPassword' id='confirmPassword' value=''>
                                </div>
                                <div>
                                    <router-link to='/main' tag='button'>Create Profile</router-link>
                                </div>
                            </form>
                        </div>
                    </slot>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: "Modal",
    data() {
        return {
            seen: false,
            logseen: true,
            name: "modal",
            signinUrl: "https://travel-bug-backend.herokuapp.com/profiles",
            form: {
                username: "",
                password: ""
            },
            profileData: null
        };
    },
    mounted() {
        fetch(this.signinUrl, {
            method: "get",
            mode: "cors",
            credentials: "same-origin",
            headers: new Headers({
                "Content-Type": "application/json"
            })
        })
            .then(resp => resp.json())
            .then(resp => {
                this.profileData = resp;
            });
    },

    methods: {
        verified(userid) {
            this.$router.push({
                path: "main",
                query: {
                    user: userid
                }
            });
        },
        notVerified() {
            document.querySelector("#alertMessage").textContent =
                "Incorrect username or password. Please try again!";
        },
        bool() {
            for (let i = 0; i < this.profileData.profile.length; i++) {
                if (
                    document.querySelector("#username").value ===
                        this.profileData.profile[i].username &&
                    document.querySelector("#password").value ===
                        this.profileData.profile[i].password
                ) {
                    this.verified(this.profileData.profile[i].id);
                } else {
                    this.notVerified();
                }
            }
        }
    }
};
</script>

<style scoped>
.content {
    display: flex;
    flex-flow: column;
    justify-content: center;
    align-items: center;
    color: #086788;
    /* text-shadow: 2px 2px 2px #9fb1bc; */
    text-shadow: -2px -2px 2px white, 2px 2px 2px white, -2px 2px 2px white,
        2px -2px 2px white;
    font-family: "Slackey";
}
.title {
    display: flex;
    flex-flow: column;
    justify-content: center;
    align-items: center;
    margin-top: 6vh;
    margin-bottom: 3vh;
}

.new-to {
    text-shadow: none;
}
#alertMessage {
    text-shadow: none;
}

@keyframes flip-bug {
    0% {
        transform: scaleX(-1);
        margin-left: 0px;
    }
    5% {
        transform: scaleX(1);
    }
    47% {
        transform: scaleX(1);
    }
    50% {
        margin-left: 350px;
    }
    53% {
        transform: scaleX(-1);
    }
    95% {
        transform: scaleX(-1);
    }
    100% {
        transform: scaleX(-1);
        margin-left: 0px;
    }
}
@keyframes bounce-bug-div {
    0% {
        transform: translateY(0);
    }
    10% {
        transform: translateY(15px);
    }
    20% {
        transform: translateY(0);
    }
    30% {
        transform: translateY(15px);
    }
    40% {
        transform: translateY(0);
    }
    50% {
        transform: translateY(15px);
    }
    60% {
        transform: translateY(0);
    }
    70% {
        transform: translateY(15px);
    }
    80% {
        transform: translateY(0);
    }
    90% {
        transform: translateY(15px);
    }
    100% {
        transform: translateY(0);
    }
}
#travel-bug {
    animation: flip-bug 5s infinite;
    animation-timing-function: linear;
}
.bug-div {
    width: 500px;
    animation: bounce-bug-div 5s infinite;
}

.login {
    margin-top: 5vh;
    margin-bottom: 5vh;
    font-family: "Simonetta";
}
.modal-header {
    display: flex;
    justify-content: center;
    background-color: #9fb1bca8;
    border-radius: 15px;
    box-shadow: 8px 8px 8px #444545;
}
/* #username {
    background-color: #9fb1bc;
    color: #086788;
}

#password {
    background-color: #9fb1bc;
    color: #086788;
} */

#signin {
    display: flex;
    flex-wrap: column;
    justify-content: center;
    align-items: center;
}
.signButton {
    background-color: #9fb1bc;
    color: #086788;
}
form {
    display: flex;
    flex-flow: column;
    justify-content: center;
    align-items: center;
}
</style>