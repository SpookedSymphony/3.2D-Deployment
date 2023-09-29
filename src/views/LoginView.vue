<script setup>
    import login from '../components/AdminLogin.vue'
    import Footer from '../components/Footer.vue'
    import { RouterLink } from 'vue-router'
</script>

<style scoped>

    h2,
    a {
        display: flex;
        justify-content: center;
        margin: auto !important;
        float: center;
        width: 250px;
    }

</style>

<template>
    <main>
        <login/>

        <h2>Not registered?</h2>
        <RouterLink to="/register">Register</RouterLink> 

        <Footer/>
    </main>
</template>