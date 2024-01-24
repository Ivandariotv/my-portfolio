<script setup lang="ts">
import githubIcon from "../assets/icons/github.vue";
import linkedinIcon from "../assets/icons/linkedin.vue";
import mailIcon from "../assets/icons/mail.vue";
import menuIcon from "../assets/icons/menu.vue";
import closeIcon from "../assets/icons/close.vue";
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

  // Llamar a la función cuando cambie el tamaño de la ventana
  window.addEventListener('resize', checkScreenSize);
});

function checkScreenSize() {
  // Obtener el ancho de la pantalla
  const screenWidth = window.innerWidth;

  // Verificar si el ancho de la pantalla es "md" (768px) o superior
  if (screenWidth >= 768) {
    hideMenu();
  }
}

function showMenu() {
  const body = document.querySelector("#body") as HTMLElement;

  body.style.transform = "scale(0.9)";
  body.style.left = "calc(95% - 60px)";
  body.style.borderRadius = "8px";
}

function hideMenu() {
  const body = document.querySelector("#body") as HTMLElement;

  body.style.transform = "scale(1)";
  body.style.left = "0px";
  body.style.borderRadius = "0px";
}
</script>

<template>
  <header style="width: calc(100% - 100px);"
    class="absolute px-6 py-[5vh] h-full transition-all duration-500 text-white md:hidden">
    <a @click="hideMenu()" class="flex items-center gap-2 py-2 cursor-pointer">
      <closeIcon class="w-6 h-6 fill-white" />
      <span class="text-xl">
        <span class="font-bold">Ivan</span><span class="text-gray-300">Via</span>
      </span>
    </a>
    <nav class="py-4">
      <ul class="grid gap-2 ">
        <li><a href="#">Servicios</a></li>
        <li><a href="#">Trabajos</a></li>
        <li><a href="#">Notas</a></li>
        <li><a href="#">Contacto</a></li>
      </ul>
    </nav>
    <nav class="py-4">
      <ul class="grid gap-2 ">
        <li>
          <a href="#" class="flex items-center gap-2">
            <linkedinIcon class="w-5 h-5 fill-white" />
            <span>Linkedin</span>
          </a>
        </li>
        <li>
          <a href="#" class="flex items-center gap-2">
            <githubIcon class="w-5 h-5 fill-white" />
            <span>Github</span>
          </a>
        </li>
        <li>
          <a href="#" class="flex items-center gap-2">
            <mailIcon class="w-5 h-5" />
            <span>Email</span>
          </a>
        </li>
      </ul>
    </nav>
  </header>

  <div id="body" class="h-full w-full fixed overflow-auto bg-[#2d2e31] transition-all duration-500 left-0 rounded-none">
    <header id="landing-header"
      class="flex gap-6 xl:gap-12 py-4 md:py-8 px-6 md:px-12 lg:px-24 top-0 w-full items-center text-white z-40 transition-all duration-500">
      <menuIcon class="w-6 h-6 fill-white md:hidden cursor-pointer" @click="showMenu()" />
      <div>
        <h1 class="text-xl md:text-2xl">
          <span class="font-bold">Ivan</span><span class="text-gray-300">Via</span>
        </h1>
      </div>
      <nav class="grow lg:px-4 xl:px-12 transition-all duration-500 hidden md:flex">
        <ul
          class="flex text-sm [&>li>a]:px-4 [&>li>a]:py-2 [&>li>a]:font-semibold [&>li>a]:transition-colors [&>li>a]:duration-500">
          <li><a href="#">Servicios</a></li>
          <li><a href="#">Trabajos</a></li>
          <li><a href="#">Notas</a></li>
          <li><a href="#">Contacto</a></li>
        </ul>
      </nav>
      <nav class="hidden md:flex">
        <ul
          class="flex text-sm [&>li>a]:px-4 [&>li>a]:py-2 [&>li>a]:font-semibold [&>li>a]:transition-colors [&>li>a]:duration-500">
          <li>
            <a href="https://www.linkedin.com/in/ivanviia/" target="_blank" rel="noopener noreferrer"
              class="flex items-center gap-2">
              <linkedinIcon class="w-5 h-5 fill-white" />
              <span class="hidden lg:block">Linkedin</span>
            </a>
          </li>
          <li>
            <a href="https://github.com/Ivandariotv" target="_blank" rel="noopener noreferrer"
              class="flex items-center gap-2">
              <githubIcon class="w-5 h-5 fill-white" />
              <span class="hidden lg:block">Github</span>
            </a>
          </li>
        </ul>
      </nav>
      <a href="#" type="button" class="text-white bg-gray-100/5 fill-gray-100/5 rounded-full text-sm p-4 hidden md:flex">
        <mailIcon class="w-5 h-5" />
      </a>

      <div id="menu-backdrop"
        class="absolute bg-white/5 backdrop-blur-lg rounded-[var(--rounded)] translate-x-[var(--left)] translate-y-[var(--top)] left-0 top-0 w-[var(--width)] h-[var(--height)] transition-all duration-500 ease-in-out opacity-0 -z-10">
      </div>
    </header>
    <slot></slot>
  </div>
</template>