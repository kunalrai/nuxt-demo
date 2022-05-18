<template>
  <div class="container">
    <h1 class="text-center fill-red border-2">This is nuxt js tutorial.</h1>

    <nav class="mx-4">
      <ul class="flex gap-x-2">
        <li class="cursor-pointer"><a href="/home">Home</a></li>
        <li class="cursor-pointer">About</li>
        <li class="cursor-pointer">Contact</li>
      </ul>
    </nav>
    <div class="border-2" />
    <button @click="$fetch" class="rounded-tl-lg">Refresh</button>
    <p v-if="$fetchState.pending">Fetching mountains...</p>
    <p v-else-if="$fetchState.error">An error occurred :(</p>
    <div v-else>
      <h1>Nuxt Mountains</h1>
      <ul class="">
        <div v-for="item of mountains">
          <div>
            {{ item.title }}
          </div>
          <img class="" :src="`${item.image}`" :alt="item.src" />
        </div>
      </ul>
    </div>
  </div>
</template>

<script>
import Home from "../pages/home.vue";
export default {
  components: { Home },
  data: () => ({
    posts: [],
    mountains: [],
  }),
  async fetch() {
    this.mountains = await fetch("https://api.nuxtjs.dev/mountains").then(
      (res) => {
        var s = res.json();
        console.log(s);
        return s;
      }
    );
  },

  fetchOnServer: false,
  fetchKey: "site-sidebar",
  fetchKey(getCounter) {
    // getCounter is a method that can be called to get the next number in a sequence
    // as part of generating a unique fetchKey.
    return this.someOtherData + getCounter("sidebar");
  },
};
</script>

<style>
</style>