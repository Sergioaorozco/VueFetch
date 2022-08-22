<script>
const baseUrl = 'http://openlibrary.org/search.json'
import BookResult from './BookResult.vue'
export default {
    data() {
        return {
            vueLibrary: {}
        };
    },
    methods: {
        async getData(e) {
            e.preventDefault();
            const inputValue = document.getElementById("book-search").value;
            try {
              await fetch(`${baseUrl}?q=${inputValue}`)
                  .then(res => res.json())
                  .then(data => this.vueLibrary = data)
            } catch(err) {
              err => console.log(err)
            }
        }
    },
    components: { BookResult }
}
</script>

<template>
<div>
  <main class="flex flex-col items-center max-w-screen-md	m-auto mt-6">
    <h1 class="text-5xl	font-bold mb-6 text-cyan-600">Books Fetch</h1>
    <form @submit="getData" class="flex items-center w-full">   
        <label for="book-search" class="sr-only">Search</label>
        <div class="relative w-full">
            <div class="flex absolute inset-y-0 left-0 items-center pl-3 pointer-events-none">
                <svg aria-hidden="true" class="w-5 h-5 text-gray-500 dark:text-gray-400" fill="currentColor" viewBox="0 0 20 20" xmlns="http://www.w3.org/2000/svg"><path fill-rule="evenodd" d="M8 4a4 4 0 100 8 4 4 0 000-8zM2 8a6 6 0 1110.89 3.476l4.817 4.817a1 1 0 01-1.414 1.414l-4.816-4.816A6 6 0 012 8z" clip-rule="evenodd"></path></svg>
            </div>
            <input type="text" id="book-search" class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full pl-10 p-2.5  dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500" placeholder="Search Mockups, Logos, Design Templates..." required>
        </div>
        <button type="submit" class="inline-flex items-center py-2.5 px-3 ml-2 text-sm font-medium hover:text-white text-cyan-600 rounded-lg border border-cyan-700 hover:bg-cyan-800 focus:ring-4 focus:outline-none focus:ring-blue-300 dark:bg-blue-600 dark:hover:text-cyan-50 dark:focus:ring-blue-800">
            <svg aria-hidden="true" class="mr-2 -ml-1 w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M21 21l-6-6m2-5a7 7 0 11-14 0 7 7 0 0114 0z"></path></svg>Search
        </button>
    </form>
  </main>
  <section>
    <BookResult :booksResult="vueLibrary"></BookResult>
  </section>
</div>
</template>
<style scoped>
</style>
