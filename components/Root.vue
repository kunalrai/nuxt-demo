<template>
    <div class="container">
    <h1 class="text-center fill-red border-2"> This is nuxt js tutorial.</h1>
    
    <nav class="mx-4">
        <ul class="flex gap-x-2">
            <li class="cursor-pointer"><a href="/home">Home</a> </li>
            <li class="cursor-pointer">About</li>
            <li class="cursor-pointer">Contact</li>
        </ul>
    </nav>
  <div class="border-2"/>
    <Home/>


    </div>
</template>

<script>
import Home from '../pages/home.vue';
export default {
    components: { Home }
}
</script>

<style>
 
</style>