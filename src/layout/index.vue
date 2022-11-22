<template>
  <div class="container">
    <base-count></base-count><br>
    <div>
      <el-button plain type="success" @click="open2">success</el-button>
      <el-button plain type="warning" @click="open3">warning</el-button>
      <el-button plain type="info" @click="open1">message</el-button>
      <el-button plain type="danger" @click="open4">error</el-button>
    </div><br>
    <div>
      <el-button @click="toggleDark()">
        <el-icon>
          <component :is="icon"></component>
        </el-icon>
        <span>{{ isDark ? 'Dark' : 'Light' }}</span>
      </el-button>
    </div>
  </div>

</template>

<script setup lang="ts">
const isDark = useDark({
  // storageKey: 'vitepress-theme-appearance',
})

const toggleDark = useToggle(isDark)

const icon = computed(() => isDark.value ? 'moon' : 'sunny')

onMounted(() => {
  sayHello()
})

const open1 = () => {
  ElMessage('this is a message.')
}
const open2 = () => {
  ElMessage({
    message: 'Congrats, this is a success message.',
    type: 'success',
  })
}
const open3 = () => {
  ElMessage({
    message: 'Warning, this is a warning message.',
    type: 'warning',
  })
}
const open4 = () => {
  ElMessage.error('Oops, this is a error message.')
}
</script>

<style scoped lang="scss">
.container {
  height: 100%;
  width: 100%;
  // background-color: $theme-color;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;

  h1 {
    font-size: 2rem;
  }
}
</style>
