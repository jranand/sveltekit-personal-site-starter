<script>
  import { navMenu } from '$lib/info'
  import MoonIcon from 'heroicons-svelte/solid/MoonIcon.svelte'
  import SunIcon from 'heroicons-svelte/solid/SunIcon.svelte'
  import { browser } from '$app/environment'
  import { page } from '$app/stores';
  import { name } from '$lib/info'
  let toggleMenu = false;
  let isDarkMode = browser ? Boolean(document.documentElement.classList.contains('dark')) : true

  function disableTransitionsTemporarily() {
    document.documentElement.classList.add('[&_*]:!transition-none')
    window.setTimeout(() => {
      document.documentElement.classList.remove('[&_*]:!transition-none')
    }, 0)
  }
</script>

<header class="flex items-center justify-between w-full py-4 mx-auto lg:pb-8 gap-16">
  <a
    class="text-lg font-bold sm:text-2xl dark:text-indigo-500 text-indigo-700"
    href="/"
  >
    {name} <sup>💻🎼😎</sup>
  </a>

  <div class="flex justify-around gap-2 items-center">
   
    <div
      class="sm:flex hidden justify-center p-1 relative sm:w-auto sm:-space-x-px overflow-hidden sm:rounded-xl"
    >
      <nav aria-label="Global">
        <ul class="flex items-center gap-2 text-sm">
          {#each navMenu as item}
            <li>
              <a
                href={item.link}
                class={`${$page.url.pathname === item.link ? 'bg-indigo-800 text-white': 'bg-transparent text-zinc-900 dark:text-white dark:text-zinc-50'} inline-block px-4 py-2 text-sm rounded-full font-medium  hover:bg-indigo-800 hover:text-white focus:relative` }
              >
                {item.title}
              </a>
            </li>
          {/each}
          <li>
            <a href="mailto:jranand.py@gmail.com" class="inline-block px-4 py-2 border-2 text-sm rounded-full border-indigo-500  font-medium text-zinc-900 dark:text-zinc-50 hover:bg-indigo-800 hover:text-white focus:relative">Say Hello</a>
          </li>
        </ul>
      </nav>
    </div>
    <div   class="dropdown flex mr-2 sm:hidden gap-2">
      <!-- svelte-ignore a11y-label-has-associated-control -->
      <button  on:click={()=>{toggleMenu = !toggleMenu}} class="bg-transparent">
        {#if toggleMenu}
        <svg
                  xmlns="http://www.w3.org/2000/svg"
                  fill="none"
                  viewBox="0 0 24 24"
                  class="inline-block h-6 w-6 stroke-current">
                  <title>Close Dropdown</title>
                  <path
                    stroke-linecap="round"
                    stroke-linejoin="round"
                    stroke-width="2"
                    d="M6 18L18 6M6 6l12 12" />
                </svg>
        {:else}
        <svg
                  xmlns="http://www.w3.org/2000/svg"
                  fill="none"
                  viewBox="0 0 24 24"
                  class="inline-block h-6 w-6 stroke-current">
                  <title>Open Dropdown</title>
                  <path
                    stroke-linecap="round"
                    stroke-linejoin="round"
                    stroke-width="2"
                    d="M4 6h16M4 12h16M4 18h16" />
                </svg>
        {/if}
      </button>
      <ul  class={`${toggleMenu ? 'block': 'hidden'} w-52  absolute right-8 z-50 top-16  py-2 mt-2 mr-10 bg-white rounded-lg shadow-xl dark:bg-zinc-700 light:bg-white`}>
        {#each navMenu as item}
        <li class="mb-2">
          <a
            on:blur={()=>{ toggleMenu = false }}
            href={item.link}
            class="inline-block px-4 py-2 text-sm rounded font-medium text-zinc-900 dark:text-zinc-50 w-full hover:bg-indigo-800 hover:text-white focus:relative"
          >
            {item.title}
          </a>
        </li>
      {/each}
      <li>
        <a href="mailto:jranand.py@gmail.com" class="inline-block px-4 py-2  text-sm rounded w-full border-indigo-500  font-medium text-zinc-900 dark:text-zinc-50 hover:bg-indigo-800 hover:text-white focus:relative">Say Hello</a>
      </li>
      </ul>
    </div>
    <button
      type="button"
      role="switch"
      aria-label="Toggle Dark Mode"
      aria-checked={isDarkMode}
      class="w-5 h-5 sm:h-8 sm:w-8 sm:p-1"
      on:click={() => {
        isDarkMode = !isDarkMode
        localStorage.setItem('isDarkMode', isDarkMode.toString())

        disableTransitionsTemporarily()

        if (isDarkMode) {
          document.querySelector('html').classList.add('dark')
        } else {
          document.querySelector('html').classList.remove('dark')
        }
      }}
    >
      <MoonIcon class="hidden text-zinc-500 dark:block" />
      <SunIcon class="block text-zinc-400 dark:hidden" />
    </button>
  </div>
</header>
