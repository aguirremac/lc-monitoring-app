<template>
    <div class="flex flex-col items-center justify-items-center">
        <span class="font-bold my-0">{{ label }}</span>
        <a-input-number v-model:value="customModel" :min="0" class="">
            <template #addonBefore>
                <a-button type="text" size="small" @click="customModel !== 0 && customModel--"
                    class="cursor-pointer">-</a-button>
            </template>
            <template #addonAfter>
                <a-button type="text" size="small" @click="customModel++" class="cursor-pointer w-full">+</a-button>
            </template>
        </a-input-number>
    </div>
</template>

<script setup lang="ts">

defineProps({
    label: {
        required: false,
        type: String
    }
})

const customModel = defineModel<number>({ required: true });

</script>

<style scoped></style>