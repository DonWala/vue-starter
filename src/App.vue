<template>
    <div>
        <h1>Witaj w systemie do zapisów na zajęcia</h1>

        <div v-if="authenticatedUsername">
            <logged-in-page :username="authenticatedUsername" :meetings="meetings" @logout="logMeOut($event)"></logged-in-page>
        </div>

        <div v-else>
            <login-form @login="logMeIn($event)"></login-form>
        </div>

    </div>
</template>

<script>
    import "milligram";
    import LoginForm from "./LoginForm";
    import UserPanel from "./UserPanel";
    

    export default {
        components: {LoginForm, UserPanel},
        data() {
            return {
                authenticatedUsername: '',
                meetings: [],
            }
        },
        methods: {
            logMeIn(username) {
                this.authenticatedUsername = username;
            },
            logMeOut() {
                this.authenticatedUsername = '';
                this.meetings = meetings;
            }
        }
    }
</script>
