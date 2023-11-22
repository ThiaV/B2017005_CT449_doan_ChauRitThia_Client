<script setup>

import {Form,Field,ErrorMessage} from 'vee-validate';
import * as yup from 'yup';
import {toast} from 'vue3-toastify'
import axios from 'axios'
const validationSchema = yup.object({
  email:yup.string().email("vui lòng nhập email hợp lệ").required("Email không hợp lệ"),
  message:yup.string().min(5,"phải lớn hơn 5 ký tự").required("Mật không hợp lệ"),
  name:yup.string().required("Không thấy tên")
})

const initialValues ={
  email:'',
  message:"",
  name:""
}


const onSubmitHandler =async(e,{resetForm})=>{
  try{
        const res = await axios.post(`http://localhost:8000/api/v1/contact`,e);
        const data = await res.data;
        toast.success(data?.msg);
        resetForm();
  }catch(e){
    toast.error(e?.response?.data?.message);
  }
}

</script>
<template>
   <section class="text-gray-600 body-font relative">
  <div class="container px-5 py-24 mx-auto flex sm:flex-nowrap flex-wrap">
    <div class="lg:w-2/3 md:w-1/2 bg-gray-300 rounded-lg overflow-hidden sm:mr-10 p-10 flex items-end justify-start relative">
      <iframe width="100%" height="100%" class="absolute inset-0" frameborder="0" title="map" marginheight="0" marginwidth="0" scrolling="no" src="" ></iframe>
      <div class="bg-white relative flex flex-wrap py-6 rounded shadow-md">
        <div class="lg:w-1/2 px-6">
          <h2 class="title-font font-semibold text-gray-900 tracking-widest text-xs">Địa Chỉ</h2>
          <p class="mt-1">Quê quán,...</p>
        </div>
        <div class="lg:w-1/2 px-6 mt-4 lg:mt-0">
          <h2 class="title-font font-semibold text-gray-900 tracking-widest text-xs">Email</h2>
          <a class="text-indigo-500 leading-relaxed">abc@email.com</a>
          <h2 class="title-font font-semibold text-gray-900 tracking-widest text-xs mt-4">Số Điện Thoại</h2>
          <p class="leading-relaxed">123-456-7890</p>
        </div>
      </div>
    </div>
    <Form   :on-submit="onSubmitHandler" :validation-schema="validationSchema" 
        :initial-values="initialValues" class="lg:w-1/3 md:w-1/2 bg-white flex flex-col md:ml-auto w-full md:py-8 mt-8 md:mt-0">
      <h2 class="text-gray-900 text-lg mb-1 font-medium title-font">Đánh giá</h2>
      <p class="leading-relaxed mb-5 text-gray-600">Cảm ơn đã liên hệ</p>
      <div class="relative mb-4">
        <label for="name" class="leading-7 text-sm text-gray-600">Tên</label>
        <Field  type="text" id="name" name="name" class="w-full bg-white rounded border border-gray-300 focus:border-indigo-500 focus:ring-2 focus:ring-indigo-200 text-base outline-none text-gray-700 py-1 px-3 leading-8 transition-colors duration-200 ease-in-out"/>
        <p class="text-red-500">
              <ErrorMessage name="name"/>
            </p>
      </div>
      <div class="relative mb-4">
        <label for="email" class="leading-7 text-sm text-gray-600">Email</label>
        <Field  type="email" id="email" name="email" class="w-full bg-white rounded border border-gray-300 focus:border-indigo-500 focus:ring-2 focus:ring-indigo-200 text-base outline-none text-gray-700 py-1 px-3 leading-8 transition-colors duration-200 ease-in-out"/>
        <p class="text-red-500">
              <ErrorMessage name="email"/>
            </p>
      </div>
      <div class="relative mb-4">
        <label for="message" class="leading-7 text-sm text-gray-600">Tin Nhắn</label>
        <Field as="textarea" id="message" name="message" class="w-full bg-white rounded border border-gray-300 focus:border-indigo-500 focus:ring-2 focus:ring-indigo-200 h-32 text-base outline-none text-gray-700 py-1 px-3 resize-none leading-6 transition-colors duration-200 ease-in-out"></Field>
        <p class="text-red-500">
              <ErrorMessage name="message"/>
            </p>
      </div>
      <button type="submit" class="text-white bg-indigo-500 border-0 py-2 px-6 focus:outline-none hover:bg-indigo-600 rounded text-lg">Gửi</button>

    </Form>
  </div>
</section>
</template>



<style lang="scss" scoped>

</style>