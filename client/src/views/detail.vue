<script setup lang="ts">
import { ref } from 'vue'
import { useRoute } from 'vue-router'
import { useBlogStore } from '@/store/blog'
import { getBlogById } from '@/service/api'
defineProps([])

const blogStore = useBlogStore()

const route = useRoute()

const blog = ref({})

const getBlog = async () => {
  const id = route.params.id
  const res = await getBlogById(Number(id))
  blog.value = res.result
}

getBlog()
</script>

<template>
  <div>detail page：{{ route.params.id }}</div>
  <div>Pinia getters：{{ blogStore.getName }}</div>
  <div>Pinia state：{{ blogStore.list }}</div>
  <div>{{ blog }}</div>
  <router-link to="/">返回首页</router-link>
</template>

<style lang="scss" scoped>
// div {
//   font-size: 14px;
// }
</style>
