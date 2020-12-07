<template>
  <div
    class="file-upload-card"
    @dragover.prevent="drag = true"
    @dragleave.prevent="drag = false"
    @drop.prevent="onDrop"
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
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator"

@Component
export default class FileUploadCard extends Vue {
  drag = false

  file: File | null = null

  onDrop(event: DragEvent): void {
    this.drag = false

    if (!event) {
      return
    }

    if (!event.dataTransfer) {
      return
    }

    if (event.dataTransfer.files.length === 0) {
      return
    }

    this.file = event.dataTransfer.files[0]
  }
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
