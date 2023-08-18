<template>
    <div class="w-48 mx-auto pt-6">
        <h1 class="mb-6 text-xl">My Posts Site</h1>
        <slot />
    </div>
</template>
<script>
import {defineComponent} from 'vue'

export default defineComponent({
    name: "MainLayout"
})
</script>


