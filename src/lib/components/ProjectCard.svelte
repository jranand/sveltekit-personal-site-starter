<script>
  import { myProjects } from '$lib/info'
</script>

<ul class="grid grid-cols-1 gap-x-12 gap-y-16 sm:grid-cols-2 lg:grid-cols-3 mb-12">
  {#each myProjects as project}
    <li class="group relative flex flex-col items-start">
      <div
        class="relative z-10 flex h-auto w-full items-center justify-center bg-white shadow-md shadow-zinc-800/5 ring-1 ring-zinc-900/5 dark:border dark:border-zinc-700/50 dark:bg-zinc-800 dark:ring-0"
      >
        <img
          alt=""
          loading="lazy"
          width="600"
          height="1200"
          decoding="async"
          data-nimg="1"
          class="h-auto w-full"
          style="color:transparent"
          src="/media/{project.image}"
        />
      </div>
      <h2 class="mt-6 text-base font-semibold text-zinc-800 dark:text-zinc-100">
        <div
          class="absolute -inset-x-4 -inset-y-6 z-0 scale-95 bg-zinc-50 opacity-0 transition group-hover:scale-100 group-hover:opacity-100 dark:bg-zinc-800/50 sm:-inset-x-6 sm:rounded-2xl"
        />
        <a href={project.link} target="_blank" rel="noreferrer"
          ><span class="absolute -inset-x-4 -inset-y-6 z-20 sm:-inset-x-6 sm:rounded-2xl" /><span
            class="relative z-10">{project.title}</span
          ></a
        >
      </h2>
      <p class="relative z-10 mt-2 text-sm text-zinc-600 dark:text-zinc-400">
        {project.desc}
      </p>
      <div class="relative mt-4 flex flex-wrap gap-1">
        {#each project.stack as stack}
          <span
            class="whitespace-nowrap rounded-full bg-indigo-50 px-2.5 py-0.5 text-xs text-indigo-500"
          >
            {stack}
          </span>
        {/each}
      </div>
    </li>
  {/each}
</ul>
