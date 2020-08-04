<template>
    <form @submit.prevent="send">
        <h3>Register</h3>
        <input v-model.trim="firstnameCom" type="text" placeholder="First Name" required />
        <input v-model.trim="user.lastname" type="text" placeholder="Last Name" required />
        <input type="submit" value="Create" />


        <fieldset>
            <legend>Props:</legend>
            <p>id: {{id}}</p>
            <p>firstname: {{firstname}}</p>
            <p>lastname: {{lastname}}</p>
        </fieldset>
        <fieldset>
            <legend>Data:</legend>
            <p>id: {{user.id}}</p>
            <p>firstname: {{user.firstname}}</p>
            <p>lastname: {{user.lastname}}</p>
        </fieldset>
        <fieldset>
            <legend>Computed:</legend>
            <p>firstname:</p>
        </fieldset>

    </form>
</template>

<script>
    export default {
        name: "MyForm",

        data() {
            return {
              user: {
                id: this.id,
                firstname: this.firstname,
                lastname: this.lastname,
              }
            }
        },

        computed: {
            firstnameCom: {
                get() {
                    return this.firstname ? this.firstname : this.user.firstname;
                },
                set(value) {
                    this.user.firstname = value
                }
            }
        },

        props: {
          id: {
            required: false,
            type: Number,
          },
          firstname: {
            required: false,
            type: String,
          },
          lastname: {
            required: false,
            type: String,
          },
        },

        methods: {
            send() {

                const user = {
                    id: this.user.id ? this.user.id : new Date().getTime().toString().slice(9),
                    firstname: this.user.firstname,
                    lastname: this.user.lastname,
                };

                this.$emit('add', user);
            },
        },
    }
</script>

<style scoped>
    form{
        border: 1px solid cornflowerblue;
        margin: 10px 0;
    }

    form input{
        margin: 5px;
    }

    h3{
        font-family: Tahoma, fantasy;
        margin: 10px;
    }
</style>
