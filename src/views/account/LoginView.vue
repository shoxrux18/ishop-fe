<template>
  <el-row>
    <el-col :lg="{span:8,offset:8}">
      <el-card>
        <template #header>
          Tizimga kirish
        </template>
        <template #default>
          <el-form :model="form" label-position="top" @submit.stop.prevent="onSubmit">
            <el-form-item label="Login">
              <el-input v-model='form.username'/>
            </el-form-item>
            <el-form-item label="Parol">
              <el-input v-model='form.password' type="password" show-password />
            </el-form-item>
            <el-form-item>
              <el-button native-type="submit" type="primary" :loading="loading">Login</el-button>
            </el-form-item>
          </el-form>
        </template>
      </el-card>
    </el-col>
    {{ form }}
  </el-row>
</template>
<script setup>


import {reactive, ref} from "vue";
import {$axios} from "@/plugins/axios";
import {ElMessage} from "element-plus";
import {useRouter} from "vue-router";
const router = useRouter()
const loading = ref(false)
const form = reactive({username: "",password: ""})
const onSubmit = async () =>{
  loading.value=true
  let resp = await $axios.post('/account/auth/',form)
  if (resp.error){
    ElMessage({
      message: "Login va/yoki parol noto'g'ri",
      type: 'error'
    })


  } else {
    localStorage.setItem("token",resp.data.token)
    ElMessage({
      message: "Xush kelibsiz",
      type: 'success'
    })
    router.push({name:'homepage'})
  }
  loading.value=false


  //     .then(r=> {
  //
  //   loading.value=false
  // }).catch(r=>{
  //
  //
  // })
}

</script>