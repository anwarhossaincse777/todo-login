<script setup>

import {useAuth} from "@/stores/auth";

const auth=useAuth();

</script>

<template>

  <div class="p-4 sm:ml-64">
    <div class="p-4 border-2 border-gray-200 border-dashed rounded-lg dark:border-gray-700">
      <h1 class="text-center text-blue-700 font-extrabold">Welcome To Admin Panel</h1>
      <br>
      <br>
      <h1 class="text-center">Your Email is : <span class="font-extrabold">{{auth.user.newUserEmail}}</span></h1>
    </div>
  </div>



</template>

<style scoped>
.m_top{

  margin-top: 69px;

}
</style>