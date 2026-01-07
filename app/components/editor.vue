<script setup lang="ts">
import { useEditor, EditorContent } from "@tiptap/vue-3";
import Text from "@tiptap/extension-text";
import Document from "@tiptap/extension-document";
import Paragraph from "@tiptap/extension-paragraph";

const props = defineProps<{
  modelValue: string;
}>();
const modelValue = ref(props.modelValue);

const emits = defineEmits<{
  "update:modelValue": [value: string | undefined];
}>();

const editor = useEditor({
  content: modelValue.value,
  extensions: [Document, Paragraph, Text],
  onUpdate: () => {
    emits("update:modelValue", editor.value?.getText());
  },
  editorProps: {
    attributes: {
      class: "h-dvh p-2",
    },
  },
});

watch(modelValue, (value) => {
  const isSame = editor.value?.getText() === value;

  if (isSame || !value) {
    return;
  }

  editor.value?.commands.setContent(value);
});
</script>

<template>
  <EditorContent :editor="editor" />
</template>
