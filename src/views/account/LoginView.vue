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
              <el-button native-type="submit" type="primary">Login</el-button>
            </el-form-item>
          </el-form>
        </template>
      </el-card>
    </el-col>
    {{ form }}
  </el-row>
</template>
<script setup>


import {reactive} from "vue";

const form = reactive({username:"",password:""})
const onSubmit = () =>{
  alert(1)
}

</script>