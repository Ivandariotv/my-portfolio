<script setup lang="ts">
import githubIcon from "../assets/icons/github.vue";
import linkedinIcon from "../assets/icons/linkedin.vue";
import mailIcon from "../assets/icons/mail.vue";
</script>

<template>
  <header class="flex gap-12 py-8 px-24 items-center text-white">
    <div>
      <h1 class="text-2xl">
        <span class="font-bold">Ivan</span
        ><span class="text-gray-300">Via</span>
      </h1>
    </div>
    <nav class="grow px-12">
      <ul
        class="flex text-sm [&>li>a]:px-4 [&>li>a]:py-2 [&>li>a]:font-semibold"
      >
        <li><a href="#">Servicios</a></li>
        <li><a href="#">Trabajos</a></li>
        <li><a href="#">Notas</a></li>
        <li><a href="#">Contacto</a></li>
      </ul>
    </nav>
    <nav>
      <ul
        class="flex text-sm [&>li>a]:px-4 [&>li>a]:py-2 [&>li>a]:font-semibold"
      >
        <li>
          <a
            href="https://www.linkedin.com/in/ivanviia/"
            target="_blank"
            rel="noopener noreferrer"
            class="flex items-center"
            ><linkedinIcon class="w-5 h-5 mr-2 fill-white" />Linkedin</a
          >
        </li>
        <li>
          <a
            href="https://github.com/Ivandariotv"
            target="_blank"
            rel="noopener noreferrer"
            class="flex items-center"
            ><githubIcon class="w-5 h-5 mr-2 fill-white" />Github</a
          >
        </li>
      </ul>
    </nav>
    <button
      type="button"
      class="text-white bg-gray-100/5 fill-gray-100/5 rounded-full text-sm p-4"
    >
      <mailIcon class="w-5 h-5" />
    </button>
  </header>
</template>
