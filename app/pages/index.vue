<script setup lang="ts">
import { useStorage } from "@vueuse/core";
import Editor from "~/components/editor.vue";

const note = useStorage("note", "");
</script>

<template>
  <Editor v-model:model-value="note" />
</template>
