<template>
  <form>
    <input v-model.trim="user.firstname" type="text" placeholder="First Name" required />
    <input v-model.trim="user.lastname" type="text" placeholder="Last Name" required />
    <input type="submit" value="Create" />
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
}
</script>
