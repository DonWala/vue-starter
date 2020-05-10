<template>
    <div>
        <h1>System do zapisów na zajêcia</h1>

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
            logMeOut(meetings) {
                this.authenticatedUsername = '';
				this.meetings = meetings;
            }
        }
    }
</script>
