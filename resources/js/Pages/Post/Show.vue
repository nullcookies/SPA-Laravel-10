<script setup>

</script>

<template>
    <h2 class="text-lg mb-2">Post</h2>
    <div class="mb-6">
        <Link :href="route('post.index')" class="text-sm mb-6">Back</Link>
    </div>

    <div v-if="post">
        <div class="mt-6 pt-6 border-t border-gray-300">
            <div>id: {{ post.id }}</div>
            <div>title: {{ post.title }}</div>
            <div>content: {{ post.content }}</div>
            <div>created_at: {{ post.created_at }}</div>
            <div> {{ post.date }}</div>
        </div>
    </div>
</template>
<script>
import {Link} from "@inertiajs/vue3";
import MainLayout from "@/Layouts/MainLayout.vue";

export default {
    name: "Index",

    props: [
        'post'
    ],

    layout: MainLayout,
    components: {
        Link
    }
}
</script>

<style scoped>

</style>
