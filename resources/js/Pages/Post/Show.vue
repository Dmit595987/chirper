<template>

        <h1 class="text-lg mb-6">Post</h1>
        <div class="mb-4">
            <Link :href="route('post.index')" class="mb-4 block p-1 rounded-full text-center text-white bg-red-500 hover:text-gray-500  ">Main Page</Link>
            <div v-if="post">
                <div class="w-48 mt-6 pt-6 border-t border-gray-300" >
                    <div>id: {{ post.id}}</div>
                    <div>title: {{ post.title}}</div>
                    <div>content: {{ post.content}}</div>
                    <div class="text-sm text-right">created: {{ post.date }}</div>

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
        'post'
    ],
})
</script>


