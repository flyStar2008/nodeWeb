<template>
  <el-row>
    <el-col :span="4">
      <el-menu
        active-text-color="#ffd04b"
        background-color="#545c64"
        class="el-menu-vertical"
        default-active="home"
        text-color="#fff"
        @open="handleOpen"
        @close="handleClose"
      >
        <div class="logo-box">
          <img src="../assets/img/logo.svg" alt="">
        </div>
        <el-menu-item @click="openRouter" index="/home">
          <template #title>
            <el-icon><HomeFilled /></el-icon>
            <span>Info</span>
          </template>
        </el-menu-item>
        <el-sub-menu index="files">
          <template #title>
            <el-icon><Files /></el-icon>
            <span>Files</span>
          </template>
            <el-menu-item @click="openRouter" index="/files/upload">upload</el-menu-item>
            <el-menu-item @click="openRouter" index="/files/download">download</el-menu-item>
        </el-sub-menu>
        <el-sub-menu index="Assets">
          <template #title>
            <el-icon><CreditCard /></el-icon>
            <span>Assets</span>
          </template>
            <el-menu-item @click="openRouter" index="/assets/chequebock">Chequebock</el-menu-item>
            <el-menu-item @click="openRouter" index="/assets/vouchers">Vouchers</el-menu-item>
            <el-menu-item @click="openRouter" index="/assets/rewards">Rewards</el-menu-item>
            <el-menu-item @click="openRouter" index="/assets/pledges">Pledges</el-menu-item>
        </el-sub-menu>
        <el-sub-menu index="Settings">
          <template #title>
            <el-icon><Setting /></el-icon>
            <span>Settings</span>
          </template>
            <el-menu-item @click="openRouter" index="/setting/api">Api</el-menu-item>
            <el-menu-item @click="openRouter" index="/setting/node">Node</el-menu-item>
        </el-sub-menu>
        
      </el-menu>
      
    </el-col>
    <el-col :span="20" class="page-content">
      <div class="content-bar"> </div>
      <router-view></router-view>
    </el-col>
  </el-row>
</template>

<script setup>
import {
  CreditCard,
  Files,
  HomeFilled,
  Setting,
} from '@element-plus/icons-vue'
import { useRouter } from 'vue-router'
const router = useRouter()

const handleOpen = (key, keyPath) => {
  console.log(key, keyPath)
}
const handleClose = (key, keyPath) => {
  console.log(key, keyPath)
}

const openRouter = (item) => {
  console.log(item)
  router.push({
    path: item.index
  })
}
</script>
<style scoped lang="scss">
.el-menu-vertical {
  height: 100%;
}
.logo-box {
  padding-left: calc(var(--el-menu-base-level-padding) + var(--el-menu-level) * var(--el-menu-level-padding));
  padding-top: 30px;
}
.page-content {
  height: 100vh;
  background-color: rgba(239, 239, 239, 1);
  overflow-y: scroll;
}
.content-bar {
  height: 65px;
}
</style>
