<script lang='ts' setup>
import { UploadRequestOptions } from 'element-plus';
import { ref } from 'vue';

const props = defineProps<{
  modelValue: string
}>()
const emit = defineEmits<{
  'update:modelValue': [file:string]
}>()
const file = ref<string>(props.modelValue.split('\\').pop()!)
const httpRequest = (options: UploadRequestOptions) => {
    file.value = options.file.path.split('\\').pop()!;
    emit('update:modelValue',options.file.path)
}
</script>
<template>
  <main class="">
    <el-upload action="#" :show-file-list="false" ref="upload" :limit="1" drag :http-request="httpRequest">
        <div class="">
           <div class="text-xs opacity-80 font-bold text-gray-700 truncate"> {{file}}</div>
            <el-tag type="warning" size="small"  effect="dark"><slot name="tip" /></el-tag>
        </div>
     </el-upload>
  </main>
</template>
<style lang='scss' scoped>
:deep(.el-upload-dragger){
    @apply p-3 m-0 border border-gray-200;
    &.is-dragover{
      @apply p-3 m-0 border;
    }
}
</style>