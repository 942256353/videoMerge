<script lang='ts' setup>
import { Plus, UpdateRotation, CloseOne } from '@icon-park/vue-next'
import { UploadRequestOptions } from 'element-plus'
import { ref } from 'vue'

const files = ref<string[]>(['asda', 'asdsads'])
const httpRequest = (options: UploadRequestOptions) => {
  const file = options.file.path.split('\\').pop()!
  files.value?.push(file)
}
</script>
<template>
  <main class="">
    <section class="flex justify-center gap-6 mt-5">
      <el-upload
        action="#"
        ref="upload"
        multiple
        drag
        :show-file-list="false"
        :http-request="httpRequest"
      >
        <Plus theme="outline" size="48" class="text-gray-600" />
      </el-upload>
      <div
        class="w-20 h-20 boder border-gray-20 cursor-pointer bg-white flex justify-center items-center rounded-md"
      >
        <UpdateRotation theme="outline" size="48" fill="#333" />
      </div>
    </section>
    <section class="text-center text-white my-3 text-xs opacity-40 font-light">
      准备转换<span class="px-1 text-yellow-300 font-bold"> {{ files.length }}</span
      >个视频
    </section>
    <!-- 视频列表 -->
    <section class="scrollbar-hide rounded-lg p-3 overflow-y-auto h-80">
      <div
        v-for="(file, index) of files"
        :key="index"
        class="group bg-[#34495e] text-gray-300 opacity-80 flex justify-between items-center py-1 px-3 my-2 rounded-md hover:bg-white hover:text-[#2c3e50] hover:opacity-90 duration-300"
      >
        <div class="text-xs opacity-70">{{ file }}</div>
        <CloseOne
          theme="outline"
          size="20"
          fill="#333"
          class="opacity-20 cursor-pointer group-hover:opacity-100 duration-300"
        />
      </div>
    </section>
    <section class="text-gray-400 text-xs text-center opacity-80">
      @小谢作品<span class="ml-2 text-yellow-500">众乐乐不如独乐乐</span>
    </section>
  </main>
</template>
<style lang='scss' scoped>
:deep(.el-upload-dragger) {
  @apply w-20 h-20 flex justify-center items-center;
}
.scrollbar-hide::-webkit-scrollbar {
  display: none; /*Chrome Safari*/
}
.scrollbar-hide {
  scrollbar-width: none; /*Firefox*/
  -ms-overflow-style: none; /*IE 10+*/
}
</style>