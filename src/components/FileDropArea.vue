<template>
  <div
    @dragover.prevent="drag = true"
    @dragleave.prevent="drag = false"
    @drop.prevent="onDrop"
  >
    <slot />
  </div>
</template>

<script lang="ts">
import { Component, Vue, Watch } from "vue-property-decorator"

@Component
export default class FileDropArea extends Vue {
  drag = false

  @Watch("drag")
  syncOnDragChanged(): void {
    this.$emit("update:drag", this.drag)
  }

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

    this.$emit("drop", event.dataTransfer.files[0])
  }
}
</script>
