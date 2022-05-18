<template>
  <el-container class="layout-container-demo">
    <el-header> <h3>微前端</h3> </el-header>
    <el-container style="flex: 1">
      <el-aside width="200px">
        <el-menu :router="true" @select="handleSelect" :default-active="activeIndex">
          <el-menu-item :key="item.path" v-for="item in system" :index="item.path">
            {{ item.name }}
          </el-menu-item>
        </el-menu>
      </el-aside>
      <el-main class="main-container">
        <!-- 应用系统挂载的节点 -->
        <div id="micro-app"></div>
        <router-view />
      </el-main>
    </el-container>
  </el-container>
</template>
<script lang="ts" setup>
// 各个应用系统
const system = [
  { name: '首页', path: '/' },
  { name: '关于', path: '/about' },
  { name: '系统管理', path: '/app-vue2' },
  { name: '用户管理', path: '/app-vue3' },
  { name: '点餐管理', path: '/app-react' },
];
const activeIndex = '';
const handleSelect = (key: string, keyPath: string[]) => {
  console.log(key, keyPath);
};
</script>
<style lang="scss">
.layout-container-demo {
  height: 100vh;
}
.layout-container-demo .el-header {
  position: relative;
  background-color: var(--el-color-primary-light-7);
  color: var(--el-text-color-primary);
  display: flex;
  // justify-content: center;
  align-items: center;
}
.layout-container-demo .el-aside {
  height: 100%;
  color: var(--el-text-color-primary);
  background: var(--el-color-primary-light-8);
}
.layout-container-demo .el-menu {
  border-right: none;
  background: transparent;
}
.layout-container-demo .el-main {
  padding: 0;
  background-color: var(--el-color-primary-light-9);
}
.layout-container-demo .toolbar {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  height: 100%;
  right: 20px;
}
</style>
