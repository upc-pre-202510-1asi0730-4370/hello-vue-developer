<script>
import {defineComponent} from "vue";
import GreetDeveloper from "@/greetings/components/greet-developer.component.vue";

export default defineComponent({
  components: {GreetDeveloper}
})
</script>

<template>
  <h1>Hello Vue Developer Application</h1>

  <greet-developer first-name="Alberto" last-name="Perez"></greet-developer>
</template>

<style>
</style>