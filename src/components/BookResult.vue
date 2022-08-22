<script>
  export default {
    data(){
      return{
      }
    },
    props: ['booksResult']
  }
</script>
<template>
  <div>
      <ul>
        <li v-for="book in booksResult.docs" :key="book.author_key">{{book.title}}</li>
      </ul>
  </div>
</template>
<style>
</style>
