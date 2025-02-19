<template>
  <div
    class="f-center"
    :style="{
      backgroundColor: bgColor,
      fontSize: `${fontSize}px`,
      color: fontColor,
      height: `${height}px`
    }"
  >
    {{ title }}
  </div>
</template>

<script lang="ts" setup>
interface Props {
  title?: string
  bgColor?: string
  fontSize?: number
  fontColor?: string
  height?: number
}

withDefaults(defineProps<Props>(), {
  title: '文章',
  bgColor: '#000000',
  fontSize: 16,
  fontColor: '#ffffff',
  height: 70,
})
</script>

<style scoped lang="scss"></style>
