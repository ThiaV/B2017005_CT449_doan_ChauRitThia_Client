<template>
  <div class="about">
        <Form :on-submit="onSubmitHandler" :validation-schema="validationSchema" 
        :initial-values="initialValues" class="w-[90%] mt-12 md:w-1/2  mx-auto flex py-24 flex-col px-10 bg-gray-200 rounded-md">
          <h1 class="text-center font-semibold text-5xl placeholder:font-normal f-1">Đăng Nhập </h1>
         
          <div class="mb-3 w-full">
            <label class="text-start">Email <span class="text-red-500">*</span></label>
            <Field name="email" type="text" placeholder="Nhập Email" class="outline-none border-none w-full text-xl rounded-md shadow-md py-3 px-4 font-serif"/>
            <p class="text-red-500">
              <ErrorMessage name="email"/>
            </p>
          </div>
          <div class="mb-3 w-full">
            <label class="text-start"> Mật Khẩu <span class="text-red-500">*</span></label>
            <Field name="password" type="password" placeholder="Nhập mật khẩu" class="outline-none border-none w-full text-xl rounded-md shadow-md py-3 px-4 font-serif placeholder:font-normal"/>
            <p class="text-red-500">
              <ErrorMessage name="password"/>
            </p>
          </div>
          <div class="mb-3 w-full flex justify-center">
            <button class="bg-indigo-500 hover:bg-indigo-600 cursor-pointer px-12 py-3 rounded-md text-white text-2xl f-1">Đăng Nhập</button>
          </div>
          <div class="mb-3">
            <p class="text-center text-lg">Bạn chưa có tài khoản <span class="text-indigo-500"><router-link to="/register">Đăng Ký ?</router-link></span></p>
          </div>
        </Form>
  </div>
</template>
<script setup>
import { RouterLink } from 'vue-router';
import {Form,Field,ErrorMessage} from 'vee-validate';
import * as yup from 'yup';
import {toast} from 'vue3-toastify'
import axios from 'axios'
import {useRouter} from 'vue-router'
import {userStore} from '../stores/userStore';
const router = useRouter()
const validationSchema = yup.object({
  email:yup.string().email("vui lòng nhập email").required("tài khoản email không hợp lệ "),
  password:yup.string().min(5,"Nhật mật khẩu có ít nhất 5 ký tự").required("mật khẩu không hợp lệ"),
})

const initialValues ={
  email:'',
  password:""
}

const store = userStore();


const fetchUser = async(token)=>{
  try{
        const res =  await axios.get(`http://localhost:8000/api/v1/profile`,{
          headers:{
            'Authorization':`Bearer ${token}`
          }
        });
        const data = await res.data;
        console.log(data);
        store.setUser(data);
  }catch(e){
    console.log(e)
  }
}


const onSubmitHandler =async(e,{resetForm})=>{
  try{
        const res = await axios.post(`http://localhost:8000/api/v1/login`,e);
        const data = await res.data;
        toast.success(data?.msg);
        store.setToken(data.token);
        fetchUser(data?.token)
        resetForm();
        router.push('/')
  }catch(e){
    toast.error(e?.response?.data?.message);
  }
}

</script>
