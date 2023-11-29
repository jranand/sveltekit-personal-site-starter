<script>
  import '../app.css'
  import '../prism.css'
  import Nav from '$lib/components/Nav.svelte'
  import Footer from '$lib/components/Footer.svelte';
</script>
<div class="flex w-full">
  <div class="container inset-0 max-h-full py-5 px-10 bg-white dark:bg-black rounded max-w-screen-lg mx-auto">
    <Nav />
    <main class="flex  mt-5 flex-col flex-grow w-full mx-auto">
      <slot />
    </main>
  </div>  
</div>
<Footer />

