<template>
  <div id="App" class="grid">
    <header class="bg-red-600 col-span-12">header</header>

    <nav class="bg-yellow-200 col-span-4">nav</nav>

    <main class="bg-blue-400 col-span-8">main</main>
  </div>
</template>

<script>
export default {
  name: 'App',
}
</script>

<style>
nav {
  height: calc(100vh - 24px);
}
</style>
