MyDialog.vue
<template>
  <v-dialog v-model="dialogVisible" width="500">
    <v-card>
      <v-card-title class="headline">
        {{ title }}
      </v-card-title>
      <v-card-text>
        {{ message }}
        <slot></slot>
      </v-card-text>
      <v-card-actions class="justify-end">
        <v-btn color="grey darken-1" @click="closeDialog">
          Cancel
        </v-btn>
        <v-btn color="primary" @click="handleConfirm">
          {{ confirmText }}
        </v-btn>
      </v-card-actions>
    </v-card>
  </v-dialog>
</template>

<script lang="ts" setup>
import { ref } from 'vue';

const dialogVisible = ref(false);
const title = ref('Confirm Action'); // Default title
const message = ref('Are you sure you want to perform this action?'); // Default message
const confirmText = ref('Yes, Proceed'); // Default confirm text

const emit = defineEmits(['confirm', 'close']);

const openDialog = (options?: { title?: string; message?: string; confirmText?: string }) => {
  title.value = options?.title ?? 'Confirm Action'; // Use provided title or default
  message.value = options?.message ?? 'Are you sure you want to perform this action?'; // Use provided message or default
  confirmText.value = options?.confirmText ?? 'Yes, Proceed'; // Use provided confirmText or default
  dialogVisible.value = true;
};

const closeDialog = () => {
  dialogVisible.value = false;
  emit('close');
};

const handleConfirm = () => {
  emit('confirm');
  closeDialog();
};

defineExpose({
  openDialog,
  closeDialog,
});
</script>