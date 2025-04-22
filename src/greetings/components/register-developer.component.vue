<script>
  export default {
    name: 'register-developer',
    emits: ['developer-registered'],
    data() {
      return {
        firstName: '',
        lastName: '',
        errorMessage: ''
      }
    },
    methods: {
      onRegister() {
        if (this.firstName.trim() || this.lastName.trim()) {
          console.log("Registering developer");
          this.$emit('developer-registered', {
            firstName: this.firstName,
            lastName: this.lastName,
          });
          this.clearForm();
        } else {
          console.log("Cannot register");
          this.errorMessage = 'Please provide at least first name or last name.';
        }
      },
      clearForm() {
        this.firstName = '';
        this.lastName = '';
        this.errorMessage = '';
      }
    }
  }
</script>

<template>
  <div>
    <h2>New Developer</h2>
    <div>
      <form v-on:submit.prevent="onRegister">
        <div>
          <label>First Name</label>
          <input id="firstName" type="text" v-model="firstName" />
        </div>
        <div>
          <label>Last Name</label>
          <input id="lastName" type="text" v-model="lastName" />
        </div>
        <div class="actions">
          <button type="submit">Register</button>
          <button type="button" v-on:click="clearForm">Clear</button>
        </div>
      </form>
      <p v-if="errorMessage">{{ errorMessage }}</p>
    </div>
  </div>
</template>

<style scoped>

</style>