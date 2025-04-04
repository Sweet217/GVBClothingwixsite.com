<template>
  <header
    :class="[
      'py-4 fixed top-0 left-0 w-full z-50',
      isScrolled ? 'bg-transparent text-white shadow-lg' : 'bg-black text-white',
    ]"
  >
    <div class="container mx-auto flex justify-between items-center px-6">
      <!-- Logo and Title -->
      <div class="flex items-center">
        <a
          :class="[
            'font-new-rocker transition-[font-size,margin] duration-250 ease-in-out text-3xl',
            isScrolled ? 'text-6xl mt-10' : 'text-3xl',
          ]"
          >GVB</a
        >
        <a
          :class="[
            'ml-1 font-new-rocker text-1xl',
            isScrolled ? 'opacity-0' : 'opacity-100',
          ]"
        >
          Clothing</a
        >
      </div>

      <!-- Hamburger Menu for Mobile -->
      <button
        @click="toggleMenu"
        class="lg:hidden text-white"
        :class="{ 'opacity-0': isScrollingDown }"
      >
        <span class="material-icons">menu</span>
      </button>

      <!-- Navigation Links -->
      <nav
        :class="[
          'lg:flex items-center w-full justify-between ml-4',
          isMenuOpen ? 'block' : 'hidden',
          'absolute top-full left-0 w-full bg-black lg:relative lg:bg-transparent',
        ]"
      >
        <!-- Centered Links -->
        <div
          class="flex flex-col lg:flex-row justify-center flex-1 space-y-4 lg:space-y-0 lg:space-x-10 mr-20 text-center lg:text-left"
        >
          <router-link
            to="/"
            class="font-super-funky hover:text-purple-100"
            :class="{ 'opacity-0': isScrollingDown }"
          >
            Home
          </router-link>
          <router-link
            to="/contact"
            class="font-super-funky hover:text-purple-100"
            :class="{ 'opacity-0': isScrollingDown }"
          >
            Contact
          </router-link>
        </div>

        <!-- Cart Icon -->
        <router-link
          to="/cart"
          :class="[
            'font-super-funky hover:text-purple-100 flex items-center mr-20',
            isScrolled ? 'opacity-0' : 'opacity-100',
          ]"
        >
          <span class="material-icons">shopping_cart</span>
        </router-link>
      </nav>

      <!-- Social Media Icons -->
      <div :class="['flex space-x-4', isScrolled ? 'opacity-0' : 'opacity-100']">
        <a
          href="https://www.facebook.com/profile.php?id=61574341145991"
          target="_blank"
          rel="noopener noreferrer"
          class="text-white hover:text-blue-500"
        >
          <i class="bi bi-facebook"></i>
        </a>
        <a
          href="https://wa.me/523125953394"
          target="_blank"
          rel="noopener noreferrer"
          class="text-white hover:text-green-500"
        >
          <i class="bi bi-whatsapp"></i>
        </a>
        <a
          href="https://www.instagram.com/gvb_clothing/"
          target="_blank"
          rel="noopener noreferrer"
          class="text-white hover:text-pink-500"
        >
          <i class="bi bi-instagram"></i>
        </a>
      </div>
    </div>
  </header>
</template>

<script>
export default {
  data() {
    return {
      lastScrollY: 0,
      isScrollingDown: false,
      isScrolled: false,
      isMenuOpen: false,
    };
  },
  mounted() {
    window.addEventListener("scroll", this.handleScroll);
  },
  beforeUnmount() {
    window.removeEventListener("scroll", this.handleScroll);
  },
  methods: {
    handleScroll() {
      const currentScrollY = window.scrollY;
      this.isScrollingDown = currentScrollY > this.lastScrollY;
      this.lastScrollY = currentScrollY;
      this.isScrolled = currentScrollY > 50;

      if (this.isScrollingDown) {
        this.isMenuOpen = false;
      }
    },
    toggleMenu() {
      this.isMenuOpen = !this.isMenuOpen;
    },
  },
};
</script>

<style scoped>
header {
  z-index: 50;
  transition: color 0.3s ease, box-shadow 0.3s ease;
}

header.bg-transparent {
  box-shadow: none;
  -webkit-text-stroke: 2px rgb(0, 0, 0); /* Adjust thickness and color */
  margin-top: -20px;
}

body {
  margin-top: 80px;
}

img {
  transition: opacity 0.3s ease;
}
</style>
