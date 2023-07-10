<script setup>

</script>

<template>
    <h2 class="text-lg mb-6">Posts</h2>
    <div>
        <Link :href="route('post.create')"
              class="hover:bg-white hover:text-sky-500 block p-2 w-32 border border-sky-500 bg-sky-500 rounded-full text-center text-white">
            Add post
        </Link>
    </div>
    <div v-if="posts">
        <div class="mt-6 pt-6 border-t border-gray-300" v-for="post in posts">
            <div>id: {{ post.id }}</div>
            <div>title: {{ post.title }}</div>
            <div>content: {{ post.content }}</div>
            <div>created_at: {{ post.created_at }}</div>
            <div> {{ post.date }}</div>
            <div class="text-sm text-right">
                <Link class="text-sky-400" :href="route('post.show', post.id)">Show</Link>
            </div>
            <div class="text-sm text-right">
                <Link class="text-sky-400" :href="route('post.edit', post.id)">Edit</Link>
            </div>
            <div class="text-sm text-right">
                <p @click="deletePost(post.id)" class="cursor-point text-red-400">Delete</p>
            </div>
        </div>
    </div>
</template>
<script>
import {Link} from "@inertiajs/vue3";
import MainLayout from "@/Layouts/MainLayout.vue";

export default {
    name: "Index",

    layout: MainLayout,
    props: [
        'posts'
    ],
    components: {
        Link
    },
    methods: {
        deletePost(id) {
            this.$inertia.delete(`/posts/${id}`)
        }
    }
}
</script>

<style scoped>

</style>
