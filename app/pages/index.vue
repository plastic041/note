<script setup lang="ts">
import { useStorage } from "@vueuse/core";
import Editor from "~/components/editor.vue";

const note = useStorage("note", "");
</script>

<template>
  <textarea
    v-model="note"
    class="h-dvh w-screen border-none outline-none m-0 fixed p-2 resize-none"
  />
</template>
