<script setup>
import { reactive, watch } from "vue";
const form = reactive({
  email: "",
  password: "",
  message: "",
});

const emit = defineEmits(["login"]);
const handleLogin = () => {
  emit("login", form.email, form.password); // Emit only when the form is submitted
};

// watchers example
watch(form, (newForm) => {
  if (newForm.password.length < 6) {
    form.message = "Password must be at least 6 characters long";
  } else {
    form.message = "Password is valid";
  }
});

// Option API example
// export default {
//   data() {
//     return {
//       email: "",
//       password: "",
//       message: "",
//     };
//   },
//   methods: {
//     login() {
//       this.$emit("login", this.email, this.password);
//     },
//   },
//   emits: ["login"],
//   watch: {
//     password(newPass, oldPass) {
//       if (newPass.length < 6) {
//         this.message = "Password must be at least 6 characters long";
//       } else {
//         this.message = "Password is valid";
//       }
//     },
//   },
// };
</script>

<template>
  <!-- login -->
  <div class="min-h-screen flex items-center justify-center w-full">
    <div class="px-8 py-6 w-1/3 bg-blue-400 border-2 border-black rounded-2xl shadow-[2px_2px_0px_rgba(0,0,0,1)]">
      <h1 class="text-2xl font-bold text-center mb-4">Login</h1>
      <form @submit.prevent="handleLogin">
        <div class="mb-4">
          <label for="email" class="block text-sm font-medium">Email Address</label>
          <input type="email" id="email"
            class="bg-white w-full px-3 py-2 border-2 border-black rounded-2xl shadow-[2px_2px_0px_rgba(0,0,0,1)]"
            placeholder="your@email.com" v-model="form.email" />
        </div>
        <div class="mb-4">
          <label for="password" class="block text-sm font-medium">Password</label>
          <input type="password" id="password"
            class="bg-white w-full px-3 py-2 border-2 border-black rounded-2xl shadow-[2px_2px_0px_rgba(0,0,0,1)]"
            placeholder="Enter your password" v-model="form.password" />
          <b class="text-white" v-if="form.message">{{ form.message }}</b>
        </div>
        <button
          class="w-full mt-5 justify-center py-2 px-4 border-2 border-black rounded-2xl text-sm font-medium text-white bg-gray-700 hover:bg-black shadow-[2px_2px_0px_rgba(0,0,0,1)]">
          Login
        </button>
      </form>
    </div>
  </div>
</template>
