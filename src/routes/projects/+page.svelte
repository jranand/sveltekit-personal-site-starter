<script>
  import ProjectCard from '$lib/components/ProjectCard.svelte'
</script>

<svelte:head>
  <title>Anand JR | Projects</title>
  <meta
    name="description"
    content="List of various products and projects I worked on as an entrepreneur and front-end web developer"
  />
</svelte:head>

<section class="w-full mt-12 mb-12">
  <div class="flex items-center justify-between gap-4 mb-8">
    <h2 class="text-2xl font-medium sm:text-3xl mb-5 text-zinc-800 dark:text-zinc-400">
      UI/UX consultant for <a
        href={"#"}
        class="border-b-2 border-zinc-400 pb-1 hover:border-indigo-500 transition-all ease-in-out hover:translate-y-1 hover:scale-110 duration-300"
        target="_blank"
        rel="noreferrer">some company</a
      >
    </h2>
  </div>
  <ProjectCard />
</section>
