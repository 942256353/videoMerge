<script setup lang="ts">
import NavBar from './components/NavBar.vue'
import VideoList from './components/VideoList.vue';
import VideoSelect from './components/VideoSelect.vue'
import useConfigStore from './store/useConfigStore';

const {config} = useConfigStore()
</script>

<template>
  <main class="">
    <NavBar />
    <section class="grid grid-cols-2 gap-3 p-3 bg-white">
      <VideoSelect v-model="config.preVideo">
         <template #tip>
            片头
         </template>
      </VideoSelect>
      <VideoSelect v-model="config.endVideo">
         <template #tip>
            片尾
         </template>
      </VideoSelect>
    </section>
    <section class="">
      <VideoList />
    </section>
  </main>
</template>

<style lang="less">
</style>
