<script setup lang="ts">
import githubIcon from "../assets/icons/github.vue";
import linkedinIcon from "../assets/icons/linkedin.vue";
import mailIcon from "../assets/icons/mail.vue";
import { onMounted } from "vue";

onMounted(() => {
  const listItem = document.querySelectorAll("#landing-header a");
  const menuBackDrop = document.querySelector("#menu-backdrop") as HTMLElement;

  listItem.forEach((item, index) => {
    item.addEventListener("mouseenter", () => {
      const { left, top, width, height } = item.getBoundingClientRect();
      const rounded = index === listItem.length - 1 ? 2 : 0.25;

      menuBackDrop.style.setProperty("--left", `${left}px`);
      menuBackDrop.style.setProperty("--top", `${top}px`);
      menuBackDrop.style.setProperty("--width", `${width}px`);
      menuBackDrop.style.setProperty("--height", `${height}px`);
      menuBackDrop.style.setProperty("--rounded", `${rounded}rem`);

      menuBackDrop.style.opacity = "1";
      menuBackDrop.style.visibility = "visible";
    });

    item.addEventListener("mouseleave", () => {
      menuBackDrop.style.opacity = "0";
      menuBackDrop.style.visibility = "hidden";
    });
  });
});
</script>

<template>
  <header
    id="landing-header"
    class="flex gap-12 py-8 px-24 fixed top-0 w-full items-center text-white z-40"
  >
    <div>
      <h1 class="text-2xl">
        <span class="font-bold">Ivan</span
        ><span class="text-gray-300">Via</span>
      </h1>
    </div>
    <nav class="grow px-12">
      <ul
        class="flex text-sm [&>li>a]:px-4 [&>li>a]:py-2 [&>li>a]:font-semibold [&>li>a]:transition-colors [&>li>a]:duration-500"
      >
        <li><a href="#">Servicios</a></li>
        <li><a href="#">Trabajos</a></li>
        <li><a href="#">Notas</a></li>
        <li><a href="#">Contacto</a></li>
      </ul>
    </nav>
    <nav>
      <ul
        class="flex text-sm [&>li>a]:px-4 [&>li>a]:py-2 [&>li>a]:font-semibold [&>li>a]:transition-colors [&>li>a]:duration-500"
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
    <a
      href="#"
      type="button"
      class="text-white bg-gray-100/5 fill-gray-100/5 rounded-full text-sm p-4"
    >
      <mailIcon class="w-5 h-5" />
    </a>

    <div
      id="menu-backdrop"
      class="absolute bg-white/5 backdrop-blur-lg rounded-[var(--rounded)] translate-x-[var(--left)] translate-y-[var(--top)] left-0 top-0 w-[var(--width)] h-[var(--height)] transition-all duration-500 ease-in-out opacity-0 -z-10"
    ></div>
  </header>
</template>
