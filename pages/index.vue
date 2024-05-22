<template>
    <div class="h-screen mx-auto flex flex-col items-center justify-center">
        <a-form v-model="formState" name="basic" :label-col="{ span: 8 }" :wrapper-col="{ span: 16 }" autocomplete="off"
            @finish="onFinish" @finishFailed="onFinishFailed"
            class="border border-gray-200 p-5 rounded-md shadow-xl w-full max-w-[500px] h-full m-5 flex flex-col gap-2">
            <a-select v-model:value="formState.networkLeader" show-search placeholder="Select a Network Leader"
                :options="options" :filter-option="filterOption" style="min-width: 300px;"></a-select>

            <div class="px-5 border border
            
            p-2 rounded-md">
                <p class="my-0 pb-2 text-lg font-bold">10AM SERVICE</p>
                <div class="flex gap-2 items-center">
                    <CustomInputNumber v-model="formState.AM.adult" label="ADULT" />
                    <CustomInputNumber v-model="formState.AM.youth" label="YOUTH" />
                    <CustomInputNumber v-model="formState.AM.online" label="ONLINE" />
                </div>
            </div>

        </a-form>
        <pre>{{ formState }}</pre>
    </div>
</template>

<script setup lang="ts">
import type { SelectProps } from 'ant-design-vue';
import { ref } from 'vue';
const options = ref<SelectProps['options']>([
    { value: 'M1-Magbanua', label: 'M1-Magbanua' },
    { value: 'M2-Quirante', label: 'M2-Quirante' },
    { value: 'M3-Argonia', label: 'M3-Argonia' },
]);


const filterOption = (input: string, option: any) => {
    return option.label.toLowerCase().indexOf(input.toLowerCase()) >= 0;
};


const formState = reactive({
    networkLeader: null,
    AM: {
        adult: 0,
        youth: 0,
        online: 0,
    }
});
const onFinish = (values: any) => {
    console.log('Success:', values);
};

const onFinishFailed = (errorInfo: any) => {
    console.log('Failed:', errorInfo);
};

</script>

<style scoped></style>