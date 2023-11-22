<template>
  <div class="about">
        <Form :on-submit="onSubmitHandler" :validation-schema="validationSchema" 
        :initial-values="initialValues" class="w-[90%] mt-12 md:w-1/2  mx-auto flex py-24 flex-col px-10 bg-gray-200 rounded-md">
          <h1 class="text-center font-semibold text-5xl f-1">Đăng Ký </h1>
          <div class="mb-3 w-full">
            <label class="text-start">Tên <span class="text-red-500">*</span></label>
            <Field name="name"  type="text" placeholder="Tên Đăng Ký" class="outline-none border-none w-full text-xl rounded-md shadow-md py-3 px-4 font-serif placeholder:font-normal"/>
            <p class="text-red-500">
              <ErrorMessage name="name"/>
            </p>
          </div>
          <div class="mb-3 w-full">
            <label class="text-start">Email <span class="text-red-500">*</span></label>
            <Field name="email" type="text" placeholder="Địa chỉ email" class="outline-none border-none w-full text-xl rounded-md shadow-md py-3 px-4 font-serif placeholder:font-normal"/>
            <p class="text-red-500">
              <ErrorMessage name="email"/>
            </p>
          </div>
          <div class="mb-3 w-full">
            <label class="text-start"> Mật Khẩu <span class="text-red-500">*</span></label>
            <Field name="password" type="password" placeholder="Mật khẩu" class="outline-none border-none w-full text-xl rounded-md shadow-md py-3 px-4 font-serif placeholder:font-normal"/>
            <p class="text-red-500">
              <ErrorMessage name="password"/>
            </p>
          </div>
          <div class="mb-3 w-full flex justify-center">
            <button class="bg-indigo-500 hover:bg-indigo-600 cursor-pointer px-12 py-3 rounded-md text-white text-2xl f-1">Đăng Ký</button>
          </div>
          <div class="mb-3">
            <p class="text-center text-lg">Bạn đã có tài khoản <span class="text-indigo-500"><router-link to="/login">Đăng Nhập ?</router-link></span></p>
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
const router = useRouter()

const validationSchema = yup.object({
  name:yup.string().required("Nhập Tên"),
  email:yup.string().email("vui lòng nhập địa chỉ email").required("Không kiếm thấy email"),
  password:yup.string().min(5,"Mật phải lớn hơn năm ký tự").required("Không kiếm mật khẩu"),
})

const initialValues ={
  name:"",
  email:'',
  password:""
}

const onSubmitHandler =async(e,{resetForm})=>{
  try{
        const res = await axios.post(`http://localhost:8000/api/v1/register`,e);
        const data = await res.data;
        toast.success(data?.msg);
        resetForm();
        router.push('/login')
  }catch(e){
    toast.error(e?.response?.data?.message);
  }
}

</script>
