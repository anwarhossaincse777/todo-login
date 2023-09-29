<script setup>
import Todo from "./Todo.vue";
import {reactive, ref} from "vue";
import {useAuth} from "@/stores/auth";
import router from "@/router";

const loginForm=reactive({
  username:'' ,
  password :'',
})




const auth=useAuth();

function submitFrom() {
  const success= auth.login(loginForm);
  if (success){
        if (success.newUsername===loginForm.username && success.newPassword===loginForm.password){
          alert("login");
          router.push({ name: 'dashboard'});
          auth.isLoggedIn=true;
        }else {
          alert("No record match");
        }
  }else {
    alert("not success")
  }


}

</script>


<template>
  <section class="bg-[#00DCBD]" id="app">
    <!-- Show login and registration forms if the user is not logged in -->
    <div  class="container h-screen flex justify-center items-center">
      <div class="flex flex-col justify-center items-center">
        <!-- Login form -->
        <form
            class="bg-white shadow-md rounded px-8 pt-6 pb-8 mb-4"
            @submit.prevent="submitFrom"
        >
          <div class="mb-4 w-80">
            <label
                class="block text-gray-700 text-sm font-bold mb-2"
                required
                for="username"
            >
              Username
            </label>
            <input
                v-model="loginForm.username"
                required
                class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
                id="username"
                type="text"
                placeholder="Username"
            />
          </div>
          <div class="mb-6 w-80">
            <label
                class="block text-gray-700 text-sm font-bold mb-2"
                for="password"
                required
            >
              Password
            </label>
            <input
                v-model="loginForm.password"
                class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 mb-3 leading-tight focus:outline-none focus:shadow-outline"
                required
                id="password"
                type="password"
                placeholder="******************"
            />
          </div>
          <div class="flex items-center justify-between">
            <button
                class="bg-[#00DCBD] hover:bg-[#20665d] text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline"
                type="submit"
            >
              Sign In
            </button>
            <RouterLink :to="{name:'register'}"
                class="inline-block align-baseline font-bold text-sm text-[#00DCBD] hover:text-[#20665d]"

            >
              Or Register
            </RouterLink>
          </div>
        </form>
      </div>
      </div>
  </section>
</template>


<style scoped>

</style>