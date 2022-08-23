<script>
  export default {
    data(){
      return{
        booksLoading: false,
      }
    },
    props: ['booksResult']
  }
</script>
<template>
<div class="text-center mt-8 max-w-screen-md m-auto gap-4 grid md:grid-cols-3">

  <div v-for="book in booksResult.docs" :key="book.author_key" class="max-w-sm bg-white rounded-lg border border-gray-200 shadow-md dark:bg-gray-800 dark:border-gray-700">
      <a href="#">
          <img class="rounded-t-lg" :src="`https://covers.openlibrary.org/b/olid/${book.edition_key}-L.jpg`" alt="" />
      </a>
      <div class="p-5">
          <a href="#">
              <h5 class="mb-2 text-2xl font-bold tracking-tight text-gray-900 dark:text-white">{{book.title}}</h5>
          </a>
          <p class="mb-3 font-normal text-gray-700 dark:text-gray-400">{{book.subtitle}}</p>
      </div>
  </div>
</div>
</template>
<style>
</style>
