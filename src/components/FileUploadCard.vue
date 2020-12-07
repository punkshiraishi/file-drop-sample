<template>
  <FileDropArea
    class="file-upload-card"
    :drag.sync="drag"
    @drop="file = $event"
  >
    <div v-if="!drag">
      ドラッグアンドドロップでファイルを追加
    </div>
    <div v-else>
      ドラッグ中
    </div>

    <div v-if="file">
      ファイル名： {{ file.name }}
      <button @click="file = null">
        クリア
      </button>
    </div>
  </FileDropArea>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator"
import FileDropArea from "./FileDropArea.vue"

@Component({
  components: {
    FileDropArea,
  },
})
export default class FileUploadCard extends Vue {
  drag = false

  file: File | null = null
}
</script>
<style lang="scss" scoped>
.file-upload-card {
  display: flex;
  flex-direction: column;
  border: solid 1px;
  padding: 1rem;
  width: 20rem;
}
button {
  color: white;
  background: gray;
  padding: 0.2rem;
}
</style>
