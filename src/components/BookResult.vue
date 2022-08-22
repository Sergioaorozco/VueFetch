<script>
  export default {
    data(){
      return{
        booksLoading: false
      }
    },
    props: ['booksResult']
  }
</script>
<template>
<div>
      <ul class="text-center mt-8 max-w-screen-md m-auto gap-4 grid sm:grid-cols-2 md:grid-cols-3">
        <li class="font-bold text-slate-400 block p-6 max-w-full md:max-w-sm bg-white rounded-lg border border-gray-200 shadow-md hover:bg-gray-100 dark:bg-gray-800 dark:border-gray-700 dark:hover:bg-gray-700" v-for="book in booksResult.docs" :key="book.author_key">{{book.title}}</li>
      </ul>
</div>
</template>
<style>
</style>
