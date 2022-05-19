<template>
  <div class="container">
    <nuxt keep-alive :keep-alive-props="{ max: 10 }" />
    <h1 class="text-center fill-red border-2">This is nuxt js sample.</h1>

    <nav class="bg-purple-800 text-white">
      <ul class="px-28 py-4 flex space-x-11 justify-end">
        <li class="cursor-pointer"><a href="/home">Home</a></li>
        <li class="cursor-pointer">About</li>
        <li class="cursor-pointer">Contact</li>
        <li class="cursor-pointer">
          <button @click="$fetch" class="rounded">Refresh</button>
        </li>
      </ul>
    </nav>

    <p v-if="$fetchState.pending">Fetching mountains...</p>
    <p v-else-if="$fetchState.error">An error occurred :(</p>
    <div v-else>
      <h1>Nuxt Mountains</h1>

      <div class="flex" v-for="item of mountains">
        <div class="basis-1/2">{{ item.title }}</div>
        <div class="basis-1/2">
          <img :src="`${item.image}`" :alt="`${item.src}`" />
        </div>
      </div>
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
img {
  max-width: 100%;
  height: auto;
}
.item {
  width: 120px;
  height: 120px;
  height: auto;
  float: left;
  margin: 3px;
  padding: 3px;
}
</style>