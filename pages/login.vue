<template>
  <div class="bg-gradient-to-t from-gray-800 to-white-900 min-h-screen flex justify-center">
      <div class="mt-10">
      <h1 class="text-2xl font-semibold mb-4">Login</h1>
      <form @submit.prevent="login">
          <div class="mb-4">
          <label for="username" class="block text-sm font-medium text-gray-600">Username:</label>
          <input v-model="username" type="text" id="username" class="mt-1 p-2 w-full border rounded-md" required />
          </div>
          <div class="mb-4">
          <label for="password" class="block text-sm font-medium text-gray-600">Password:</label>
          <input v-model="password" type="password" id="password" class="mt-1 p-2 w-full border rounded-md" required />
          </div>
          <button @click="log(username, password)" type="submit" class="w-full bg-blue-500 text-white p-2 rounded-md">Login</button>
      </form>
      </div>
  </div>
</template>

<script setup>
import { useSSRContext } from 'vue';

const {login}=useNuxtApp()
const users=usersList()
const username=ref('')
const password=ref('')
const loginStatus=isLoggedIn()
function log(username,password){
  let a=login(username,password)
  console.log(a)
  loginStatus.value=true
  if(loginStatus){
      navigateTo('/')
  }
}
definePageMeta({
  middleware:["auth"]
})
</script>