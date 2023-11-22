<script setup>
import { RouterLink } from 'vue-router'
import {computed} from 'vue';
import {userStore} from '../stores/userStore'
import {toast} from 'vue3-toastify'
import {useRouter} from 'vue-router'
const store = userStore();
const route = useRouter()
const token = computed(()=>store.token);
const logout =()=>{
  try{
    store.logoutButton();
  toast.success("Đăng xuất thành công")
  route.replace("/")
  }catch(e){
    toast.error(e.message)
  }
}
</script>

<template>
        <header class="shadow">
          <nav class="w-full md:w-[80%] mx-auto flex flex-col text-center  md:flex-row  justify-center  items-center md:justify-between py-4 px-2 f-1">
            <router-link to="/" class="text-3xl md:text-4xl">Crt-Shop</router-link>
            <ul class="flex space-x-4 text-2xl items-center">
              <li>
                <router-link to="/">Trang Chủ</router-link>
              </li>
              <li>
                <router-link to="/about">Giới Thiệu</router-link>
              </li>
              <li>
                <router-link :to="{name:'Contact'}">Liên Hệ</router-link>
              </li>
              <li v-if="!token" >
                <router-link to="/login" class="bg-indigo-500 inline-block hover:bg-indigo-600 cursor-pointer px-5 py-2 md:px-12 md:py-3 rounded-md text-white">Đăng Nhập</router-link>
              </li>
            
              <li v-if="token" >
                <button @click="logout" class="bg-indigo-500 inline-block hover:bg-indigo-600 cursor-pointer px-5 py-2 md:px-12 md:py-3 rounded-md text-white">Đăng Xuất</button>
              </li>
            </ul>
          </nav>
        </header>
</template>