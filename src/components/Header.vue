<script setup>
import { onMounted, onUnmounted, ref } from "vue";

const headerRef = ref(null);
const ELE = document.documentElement;
const mobileNav = ref(null);
const menuBarIcon = ref(null);
const backDrop = ref(null);

const menuIconClass = ref("fa-solid fa-bars");

// Toggle Mobile Navigation
const toggleMobileNav = () => {
  mobileNav.value.classList.toggle("h-0");
  mobileNav.value.classList.toggle("h-96");
  menuIconClass.value = menuIconClass.value === "fa-solid fa-bars" ? "fa-solid fa-xmark" : "fa-solid fa-bars";
  ELE.classList.toggle("overflow-hidden");
  backDrop.value.classList.toggle("hidden");
};

// Toggle Theme
const toggleTheme = () => {
  ELE.classList.toggle("dark");
  const theme = ELE.classList.contains("dark") ? "dark" : "light";
  localStorage.setItem("theme", theme);
};

// Initialize theme from localStorage
const initTheme = () => {
  const storedTheme = localStorage.getItem("theme");
  if (storedTheme) {
    ELE.classList.add(storedTheme);
  }
};

// sticky nav script
const toggleClasses = (element, classes, condition) => {
  classes.forEach((className) => {
    element.classList.toggle(className, condition);
  });
};

const handleScroll = () => {
  if (headerRef.value) {
    toggleClasses(headerRef.value, ["bg-white", "dark:text-white", "dark:bg-slate-800", "shadow-lg", "dark:sm:bg-slate-900"], window.scrollY > 0);
  }
};

onMounted(() => {
  window.addEventListener("scroll", handleScroll);
  mobileNav.value = document.getElementById("mobile-nav");
  menuBarIcon.value = document.querySelector("#menubar i");
  backDrop.value = document.getElementById("backdrop");
  initTheme();
});

onUnmounted(() => {
  window.removeEventListener("scroll", handleScroll);
});
</script>

<template>
  <header ref="headerRef" class="fixed w-full py-4 lg:px-0 px-5 z-[999] duration-300">
    <nav class="flex justify-between items-center max-w-6xl mx-auto px-2">
      <div class="flex gap-4 items-center">
        <div class="bg-primary text-white rounded-full size-10 text-xl flex-center">Y</div>
        <div>
          <h4 class="font-bold text-lg uppercase">Yogi</h4>
          <p class="text-xs">Profile</p>
        </div>
      </div>

      <ul class="md:flex hidden gap-10 hover:*:text-primary *:duration-200">
        <li>
          <a href="#home">Home</a>
        </li>
        <li>
          <a href="#about">About Us</a>
        </li>
        <li>
          <a href="#projects">Projects</a>
        </li>
        <li>
          <a href="#contact">Contact Us</a>
        </li>
        <span @click="toggleTheme" class="theme-switch md:block hidden">
          <i class="fa-solid fa-circle-half-stroke cursor-pointer"></i>
        </span>
      </ul>

      <div class="flex items-center gap-6">
        <a href="#contact">
          <button class="btn btn-outline md:!flex !hidden"><i class="fa-regular fa-paper-plane"></i> Let's Talk</button>
        </a>
        <span @click="toggleTheme" class="theme-switch md:hidden">
          <i class="fa-solid fa-circle-half-stroke cursor-pointer"></i>
        </span>
        <span id="menubar" @click="toggleMobileNav" class="cursor-pointer md:hidden text-xl">
          <i :class="menuIconClass"></i>
        </span>
      </div>
    </nav>
  </header>

  <!-- backdrop -->
  <span id="backdrop" @click="toggleMobileNav" class="fixed h-screen bg-black/10 inset-0 backdrop-blur-sm z-[997] hidden"></span>

  <!-- Mobile Nav -->
  <ul id="mobile-nav" class="flex-center flex-col gap-10 fixed w-full bottom-0 duration-200 left-0 z-[998] text-xl md:hidden dark:bg-slate-800 bg-primary text-white rounded-t-3xl h-0 overflow-hidden">
    <li>
      <a href="#home" @click="toggleMobileNav">Home</a>
    </li>
    <li>
      <a href="#about" @click="toggleMobileNav">About Us</a>
    </li>
    <li>
      <a href="#projects" @click="toggleMobileNav">Projects</a>
    </li>
    <li>
      <a href="#contact" @click="toggleMobileNav">Contact Us</a>
    </li>
  </ul>
</template>
