<template>
  <div class="common-layout">
    <el-container class="lay-container">
     <common-aside/>
      <el-container class="r-container">
        <common-header/>
        <el-main>
          <router-view />
        </el-main>
      </el-container>
    </el-container>
  </div>
</template>

<script>
    import {defineComponent} from 'vue'
    import CommonHeader from '../components/CommonHeader.vue'
    import CommonAside from '../components/CommonAside.vue'
    export default defineComponent({
        components:{
            CommonHeader,CommonAside
        }
    })
</script>

<style lang="scss" scoped>
.r-container{
  flex-wrap: wrap;
}
</style>