<script setup>
import { reactive, ref } from "vue";
import { Inertia } from "@inertiajs/inertia";

defineProps({
    errors: Object,
});

// const formData = reactive({
//     title: "",
//     content: "",
// });

const formData = ref({
    title: "",
    content: "",
});

const submitFunction = () => {
    // reactiveバージョン
    // Inertia.post("/inertia", formData);

    // refバージョン（valueプロパティを使う）
    Inertia.post("/inertia", formData.value);
};
</script>

<template>
    <form @submit.prevent="submitFunction">
        <input
            type="text"
            v-model="formData.title"
            placeholder="Title"
            class="form-control"
        />
        <div v-if="errors?.title">{{ errors.title }}</div>
        <input
            type="text"
            v-model="formData.content"
            placeholder="Content"
            class="form-control"
        />
        <div v-if="errors?.content">{{ errors.content }}</div>

        <button type="submit" class="btn btn-primary">Submit</button>
    </form>
</template>
