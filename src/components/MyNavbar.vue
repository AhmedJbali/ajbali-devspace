<template>
  <nav class="fixed top-0 left-0 right-0 bg-white shadow-md z-50">
    <div class="max-w-7xl mx-auto px-6 py-4 flex justify-between items-center">
      <div class="text-2xl font-bold text-indigo-600">
        Ahmed Jbali
      </div>

      <ul class="menu scroll-nav hidden md:flex space-x-8 text-gray-700 font-semibold">
        <li>
          <a class="scroll-to flex items-center gap-1 hover:text-indigo-600 transition" href="#home">
            <span>Home</span> <i class="las la-home text-lg"></i>
          </a>
        </li>
        <li>
          <a class="scroll-to flex items-center gap-1 hover:text-indigo-600 transition" href="#about">
            <span>About</span> <i class="lar la-user text-lg"></i>
          </a>
        </li>
        <li>
          <a class="scroll-to flex items-center gap-1 hover:text-indigo-600 transition" href="#resume">
            <span>Resume</span> <i class="las la-briefcase text-lg"></i>
          </a>
        </li>
        <li>
          <a class="scroll-to flex items-center gap-1 hover:text-indigo-600 transition" href="#services">
            <span>Services</span> <i class="las la-stream text-lg"></i>
          </a>
        </li>
        <li>
          <a class="scroll-to flex items-center gap-1 hover:text-indigo-600 transition" href="#skills">
            <span>Skills</span> <i class="las la-shapes text-lg"></i>
          </a>
        </li>
        <li>
          <a class="scroll-to flex items-center gap-1 hover:text-indigo-600 transition" href="#testimonial">
            <span>Portfolios</span> <i class="las la-grip-vertical text-lg"></i>
          </a>
        </li>
      </ul>

      <!-- Menu burger mobile -->
      <button @click="toggleMenu" class="md:hidden focus:outline-none text-gray-700">
        <svg v-if="!menuOpen" xmlns="http://www.w3.org/2000/svg" class="h-8 w-8" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
          <path stroke-linecap="round" stroke-linejoin="round" d="M4 6h16M4 12h16M4 18h16" />
        </svg>
        <svg v-else xmlns="http://www.w3.org/2000/svg" class="h-8 w-8" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
          <path stroke-linecap="round" stroke-linejoin="round" d="M6 18L18 6M6 6l12 12" />
        </svg>
      </button>
    </div>

    <transition name="fade">
      <ul v-if="menuOpen" class="md:hidden bg-white shadow-md px-6 py-4 space-y-4 text-gray-700 font-semibold">
        <li>
          <a @click="closeMenu" class="scroll-to flex items-center gap-1 hover:text-indigo-600 transition" href="#home">
            <span>Home</span> <i class="las la-home text-lg"></i>
          </a>
        </li>
        <li>
          <a @click="closeMenu" class="scroll-to flex items-center gap-1 hover:text-indigo-600 transition" href="#about">
            <span>About</span> <i class="lar la-user text-lg"></i>
          </a>
        </li>
        <li>
          <a @click="closeMenu" class="scroll-to flex items-center gap-1 hover:text-indigo-600 transition" href="#resume">
            <span>Resume</span> <i class="las la-briefcase text-lg"></i>
          </a>
        </li>
        <li>
          <a @click="closeMenu" class="scroll-to flex items-center gap-1 hover:text-indigo-600 transition" href="#services">
            <span>Services</span> <i class="las la-stream text-lg"></i>
          </a>
        </li>
        <li>
          <a @click="closeMenu" class="scroll-to flex items-center gap-1 hover:text-indigo-600 transition" href="#skills">
            <span>Skills</span> <i class="las la-shapes text-lg"></i>
          </a>
        </li>
        <li>
          <a @click="closeMenu" class="scroll-to flex items-center gap-1 hover:text-indigo-600 transition" href="#testimonial">
            <span>Portfolios</span> <i class="las la-grip-vertical text-lg"></i>
          </a>
        </li>
      </ul>
    </transition>
  </nav>
</template>

<script>
export default {
  name: "MyNavbar",
  data() {
    return {
      menuOpen: false,
    };
  },
  methods: {
    toggleMenu() {
      this.menuOpen = !this.menuOpen;
    },
    closeMenu() {
      this.menuOpen = false;
    },
  },
};
</script>

<style scoped>
.fade-enter-active, .fade-leave-active {
  transition: opacity 0.3s ease;
}
.fade-enter-from, .fade-leave-to {
  opacity: 0;
}
.menu li a {
  display: flex;
  align-items: center;
}
</style>
