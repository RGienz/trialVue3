myPrimary.vue
<template>
  <div>
    <h1>{{ count }}</h1>
    <button @click="increment">Increment</button>
    <v-btn @click="decre">decrement</v-btn>
    <v-btn color="primary" @click="openConfirmationDialog">Show Confirmation</v-btn>

    <my-dialog ref="confirmationDialog" @confirm="handleConfirmation"></my-dialog>
  </div>
</template>

<script lang="ts" setup>
import { ref } from 'vue';
import MyDialog from '../components/icons/MyDialog.vue';

const count = ref(0);
const confirmationDialog = ref<InstanceType<typeof MyDialog> | null>(null);

function increment() {
  count.value++;
}

const decre = () => {
  count.value--;
};

const openConfirmationDialog = () => {
  confirmationDialog.value?.openDialog();
};

const handleConfirmation = () => {
  console.log('User confirmed the action!');
};
</script>