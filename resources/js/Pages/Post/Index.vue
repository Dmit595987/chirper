<template>

        <h1 class="text-lg mb-6">Posts</h1>
        <div class="mb-4">
            <Link :href="route('post.create')" class="block p-1 rounded-full text-center text-white bg-red-500 hover:text-gray-500  ">Add Post</Link>
            <div v-if="posts">
                <div class="w-48 mt-6 pt-6 border-t border-gray-300" v-for="post in posts">
                    <div>id: {{ post.id}}</div>
                    <div>title: {{ post.title}}</div>
                    <div>content: {{ post.content}}</div>
                    <div class="text-sm text-right">created: {{ post.date }}</div>
                    <Link class="mb-4 block p-1 rounded-full text-center text-white bg-red-500 hover:text-gray-500" :href="route('post.show', post.id)">Show Post</Link>
                    <Link class="mb-4 block p-1 rounded-full text-center text-white bg-gray-800 hover:text-gray-500" :href="route('post.edit', post.id)">Edit Post</Link>
                    <Link @click.prevent="deletePost(post.id)" class="block p-1 rounded-full text-center text-red-600 bg-gray-500 hover:text-gray-900" >Delete Post</Link>
                </div>
            </div>

        </div>

</template>

<script>
import {defineComponent} from 'vue'
import {Link} from "@inertiajs/vue3"
import MainLayout from "@/Layouts/MainLayout.vue";

export default defineComponent({
    name: "Index",
    layout: MainLayout,
    components: {
      Link
    },

    props: [
        'posts'
    ],

    methods: {
        deletePost(id){
            this.$inertia.delete(`/posts/${id}`)
        }
    },
})
</script>


