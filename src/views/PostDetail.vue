<script setup>
import {computed, ref } from 'vue';
import Footer from '../components/Footer.vue';

function getPostsFromLocalStorage() {
    const storedPosts = localStorage.getItem('posts');
    return storedPosts ? JSON.parse(storedPosts) : [];
}

const { index } = defineProps(['index']);

const posts = ref(getPostsFromLocalStorage());

const selectedPost = computed(() => {
    return posts.value[index];
});

console.log(index);
</script>

<style scoped>

    p {
        font-size: 16px;
    }

</style>

<template>
    <div>
        <h1 v-if="selectedPost">{{ selectedPost.title }}</h1>
        <p v-if="selectedPost">{{ selectedPost.body }}</p>
        <p v-else>No post found (Index: {{ index }})</p>
  
        <Footer />
    </div>
</template>
