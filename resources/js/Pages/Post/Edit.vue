<template>

        <h1 class="text-lg mb-6">Edit</h1>
        <Link :href="route('post.index')" class="mb-4 block p-1 rounded-full text-center text-white bg-red-500 hover:text-gray-500  ">Main Page</Link>
        <form @submit.prevent="update">
            <div class="mb-4">
                <input v-model="title" class="border-gray-300 rounded-full w-full " type="text" placeholder="title">
            </div>
            <div class="mb-4">
                <textarea v-model="content" class="border-gray-300 rounded-full w-full " placeholder="content"></textarea>
            </div>
            <div>
                <button class="w-3/4  rounded-full text-center text-white bg-red-500 hover:text-gray-500" type="submit">Update</button>
            </div>
        </form>

</template>

<script>
import {defineComponent} from 'vue'
import {Link} from "@inertiajs/vue3"
import ForgotPassword from "@/Pages/Auth/ForgotPassword.vue";
import MainLayout from "@/Layouts/MainLayout.vue";

export default defineComponent({
    name: "Index",
    layout: MainLayout,
    components: {
        ForgotPassword,
      Link
    },

    props: [
      'post',
    ],

    data() {
      return {
          id: this.post.id,
          title: this.post.title,
          content: this.post.content,
      }
    },

    methods: {
      update(){
           this.$inertia.patch(`/posts/${this.id}`, {title: this.title, content: this.content})
      }
    },
})
</script>


