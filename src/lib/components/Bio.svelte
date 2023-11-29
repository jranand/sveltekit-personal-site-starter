<script>
  import SocialLinks from '$lib/components/SocialLinks.svelte'
  import { bio, name } from '$lib/info.js'
</script>

 <!-- bio -->
 <section class="flex justify-start items-center gap-16 pt-8 pb-16">
     <div class="bio">
       <img
       src='https://randomuser.me/api/portraits/lego/2.jpg'
       alt={name}
       class="block h-24 w-24 mb-5 origin-left pointer-events-auto rounded-full ring-zinc-200 dark:ring-zinc-700"
     />
     <div class="mx-auto max-w-2xl lg:max-w-5xl">
       <div class="max-w-2xl">
         <h1
           class="text-2xl font-bold tracking-tight text-zinc-800 dark:text-zinc-100 sm:text-3xl"
         >
          Hi, I am [your name] - with your skill set and experience
         </h1>
         <p class="mt-6 text-base text-zinc-600 dark:text-zinc-400">
             {bio}
         </p>
         <div class="mt-6 flex items-center gap-6">
             <SocialLinks />
         </div>
       </div>
     </div>
     
     </div>
      
   </section>