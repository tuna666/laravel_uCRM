<script setup>
import { Inertia } from "@inertiajs/inertia";
defineProps({
    id: String,
    blog: Object,
});

const deletePost = (id) => {
    Inertia.delete(`/inertia/${id}`, {
        onBefore: () => confirm("本当に削除しますか？"),
    });
};
</script>

<template>
    <p>test show page</p>
    <p>id: {{ id }}</p>
    <button @click="deletePost(blog.id)">削除する</button>
</template>
