<template>
  <div class="flex flex-col space-y-5 p-5">
    <FileUploadCard />
  </div>
</template>

<script lang="ts">
import FileUploadCard from "@/components/FileUploadCard.vue"
import { Component, Vue } from "vue-property-decorator"

@Component({
  components: {
    FileUploadCard,
  },
})
export default class DemoPage extends Vue {}
</script>

<style scoped lang="scss" ></style>