<script setup>
import {reactive} from "vue";
import {useAuth} from "@/stores/auth";
import router from "@/router";


const registerForm=reactive({
  newUsername:'' ,
  newPassword :'',
  conformPassword:''
})


// Register

const auth=useAuth();


function submitRegisterFrom() {
  // Perform password matching validation
  if (registerForm.newPassword !== registerForm.conformPassword) {
    alert("Passwords do not match. Please try again.");
  } else {
    const success=auth.register(registerForm);
    if (success){
      alert("Register Complete Successfully");
      router.push({ name: 'dashboard'});
    }else {
      alert("Something Went wrong");
    }
  }

}

</script>

<template>
  <section class="bg-[#00DCBD]" id="app">

    <!-- Show login and registration forms if the user is not logged in -->
    <div  class="container h-screen flex justify-center items-center">
      <div class="flex flex-col justify-center items-center">
        <form
            class="bg-white shadow-md rounded px-8 pt-6 pb-8 mb-4"
            @submit.prevent="submitRegisterFrom"
        >
          <div class="mb-4 w-80">
            <label
                class="block text-gray-700 text-sm font-bold mb-2"
                for="Username"
                required
            >
              Username
            </label>
            <input
                v-model="registerForm.newUsername"
                class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
                id="Username"
                type="text"
                placeholder="Username"
                required
            />
          </div>
          <div class="mb-4 w-80">
            <label
                class="block text-gray-700 text-sm font-bold mb-2"
                for="newPassword"
                required
            >
              New Password
            </label>
            <input
                v-model="registerForm.newPassword"
                class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 mb-3 leading-tight focus:outline-none focus:shadow-outline"
                required
                id="newPassword"
                type="password"
                placeholder="******************"
            />
          </div>
          <div class="mb-6 w-80">
            <label
                class="block text-gray-700 text-sm font-bold mb-2"
                for="conformPassword"
                required
            >
              Conform Password
            </label>
            <input
                v-model="registerForm.conformPassword"
                class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 mb-3 leading-tight focus:outline-none focus:shadow-outline"
                required
                id="conformPassword"
                type="password"
                placeholder="******************"
            />
          </div>
          <div class="flex items-center justify-between">
            <button
                class="bg-[#00DCBD] hover:bg-[#00DCBD] text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline"
                type="submit"
            >
              Register
            </button>
            <RouterLink
                :to="{name:'login'}"
                class="inline-block align-baseline font-bold text-sm text-[#00DCBD] hover:text-[#00DCBD]"

            >
              Back to Login
            </RouterLink>
          </div>
        </form>
      </div>
    </div>
    </section>
</template>

<style scoped>

</style>