<script setup>
import router from "@/router";
import {useAuth} from "@/stores/auth.js";
import {ElMessage, ElNotification} from "element-plus";

const auth=useAuth();
function logOut(){
 const success= auth.logout();
 if (success){
   router.push({name:'login'})
   ElNotification({
     title: 'Success',
     message: 'You have Successfully Logged Out',
     type: 'success',
     position: 'top-right',
     duration:2000,
   })
 }else {
   ElMessage({
     type: 'error',
     message: "Something went wrong" ,
   })
 }
}
</script>

<template>
  <nav class="bg-white-700 border-gray-200 dark:bg-gray-900">
    <div class="flex flex-wrap justify-between items-center mx-auto max-w-screen-xl p-4">
      <RouterLink :to="{name:'dashboard'}" class="flex items-center">
        <span class="self-center text-2xl font-semibold whitespace-nowrap text-white">Dashboard</span>
      </RouterLink>
      <div class="flex items-center">
        <button @click.prevent="logOut()" class="text-lg font-bold  text-black">Log Out</button>
      </div>
    </div>
  </nav>
</template>

<style scoped>

</style>