<template>
  <el-menu
      :default-active="route.name"
      class="el-menu-demo"
      mode="horizontal"
      router="true"
  >
    <el-menu-item index="homepage" :route="{name: 'homepage'}">Home</el-menu-item>

    <el-menu-item index="account.login" :route="{name: 'account.login'}">Login</el-menu-item>

  </el-menu>


</template>

<script setup>
import {useRoute} from "vue-router";

const route = useRoute()
</script>