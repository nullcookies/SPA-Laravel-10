<script setup>

</script>

<template>
    <h2 class="text-lg mb-6">Create</h2>
    <Link :href="route('post.index')" class="text-sm mb-6">Back</Link>
    <form @submit.prevent="store">
        <div class="mb-4">
            <input v-model="title" class="w-full rounded-full border-gray-300" type="text" placeholder="title">
            <div v-if="errors.title" class="text-red-500 test-sm">{{ errors.title }}</div>
        </div>
        <div class="mb-4">
            <textarea v-model="content" class="w-full rounded-full border-gray-300" placeholder="content"></textarea>
            <div v-if="errors.content" class="text-red-500 test-sm">{{ errors.content }}</div>
        </div>
        <div>
            <button
                class="ml-auto hover:bg-white hover:text-sky-500 block p-2 w-32 border border-sky-500 bg-sky-500 rounded-full text-center text-white"
                type="submit">Store
            </button>
        </div>
    </form>
</template>
<script>
import {Link} from "@inertiajs/vue3";
import MainLayout from "@/Layouts/MainLayout.vue";

export default {
    name: "Index",
    components: {
        Link
    },
    layout: MainLayout,

    data() {
        return {
            title: '',
            content: '',
        }
    },

    props: [
        'errors'
    ],

    methods: {
        store() {
            this.$inertia.post('/post', {title: this.title, content: this.content})
        }
    }
}
</script>

<style scoped>

</style>
