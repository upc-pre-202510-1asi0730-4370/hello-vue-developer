<script>
import {defineComponent} from "vue";
import GreetDeveloper from "@/greetings/components/greet-developer.component.vue";
import RegisterDeveloper from "@/greetings/components/register-developer.component.vue";
import {Developer} from "@/greetings/model/developer.entity.js";
import ShowDeveloperCount from "@/greetings/components/show-developer-count.component.vue";

export default defineComponent({
  components: {ShowDeveloperCount, RegisterDeveloper, GreetDeveloper},
  data() {
    return {
      firstName: "",
      lastName: "",
      developerCount: 0,
      hasRegistered: false,
    }
  },
  methods: {
    onDeveloperRegistered(developer) {
      this.firstName = developer.firstName;
      this.lastName = developer.lastName;
      this.hasRegistered = true;
      console.log("Developer registered: ", developer);
      this.updateDeveloperCount(developer);
    },
    updateDeveloperCount(developer) {
      const dev = new Developer(developer.firstName, developer.lastName);
      if (dev.fullName !== "Unknown") {
        this.developerCount++;
      }
    }
  }
})
</script>

<template>
  <h1>Hello Vue Developer Application</h1>

  <register-developer v-on:developer-registered="onDeveloperRegistered"></register-developer>
  <greet-developer v-if="hasRegistered" :first-name="firstName" :last-name="lastName"></greet-developer>

  <show-developer-count :developer-count="developerCount"></show-developer-count>
</template>

<style>
</style>