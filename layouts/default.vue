<template>
  <el-container class="layout-default">
    <el-header height="auto">
      <my-header />
    </el-header>
    <el-main>
      <nuxt />
    </el-main>
    <el-footer height="100%">
      <my-footer />
    </el-footer>
  </el-container>
</template>

<script>
import MyHeader from '@/components/public/header/'
import MyFooter from '@/components/public/footer/'
export default {
  components: {
    MyHeader,
    MyFooter
  }
}
</script>
